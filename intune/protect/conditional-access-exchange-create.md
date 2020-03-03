---
title: Exchange 조건부 액세스 정책 만들기
titleSuffix: Microsoft Intune
description: Intune에서 Exchange 온-프레미스 및 레거시 Exchange Online Dedicated의 조건부 액세스를 구성합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4962b4c75460b129f9df7729b5a34485d8ee0760
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576062"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Exchange 온-프레미스 및 레거시 Exchange Online Dedicated에 대한 조건부 액세스 정책 만들기

이 문서에서는 디바이스 준수를 기반으로 Exchange 온-프레미스에 대한 조건부 액세스를 구성하는 방법을 설명합니다.

Exchange Online Dedicated 환경이 있고 신규 또는 기존 구성 상태인지를 확인해야 하는 경우 계정 관리자에게 문의하세요. Exchange 온-프레미스 또는 레거시 Exchange Online Dedicated 환경에 대한 메일 액세스를 제어하려면 Intune에서 Exchange 온-프레미스에 대한 조건부 액세스를 구성합니다.

## <a name="before-you-begin"></a>시작하기 전에

조건부 액세스를 구성하기 전에 다음 구성이 있는지 확인합니다.

- Exchange 버전이 **Exchange 2010 SP1 이상**입니다. Exchange Server CAS(클라이언트 액세스 서버) 배열이 지원됩니다.

- Intune을 온-프레미스 Exchange에 연결하는 [Exchange Active Sync 온-프레미스 Exchange 커넥터](exchange-connector-install.md)를 설치했고 사용합니다.

    >[!IMPORTANT]  
    >Intune은 구독당 여러 개의 온-프레미스 Exchange Connector를 지원합니다.  그러나 각 온-프레미스 Exchange 커넥터는 단일 Intune 테넌트별로 다르며 다른 테넌트에서는 사용할 수 없습니다.  둘 이상의 온-프레미스 Exchange 조직이 있는 경우 각 Exchange 조직에 대해 별도의 커넥터를 설정할 수 있습니다.

- 컴퓨터에서 Exchange Server와 통신할 수 있는 한 해당되는 모든 컴퓨터에 온-프레미스 Exchange 조직에 대한 커넥터를 설치할 수 있습니다.

- 이 커넥터는 **Exchange CAS 환경**을 지원합니다. Intune은 Exchange CAS 서버에 직접 커넥터를 설치하는 것을 지원합니다. 커넥터 때문에 서버에서 추가 로드가 발생하므로 별도의 컴퓨터에 설치하는 것이 좋습니다. 커넥터를 구성할 때는 커넥터가 Exchange CAS 서버 중 하나와 통신하도록 설정해야 합니다.

- **Exchange ActiveSync**는 인증서 기반 인증 또는 사용자 자격 증명 항목으로 구성되어야 합니다.

- 조건부 액세스 정책이 구성되고 사용자를 대상으로 지정한 경우 사용자가 자신의 이메일에 연결하기 전에 사용하는 **디바이스**는 다음과 같아야 합니다.
  - Intune에 **등록**되어 있거나 도메인에 가입된 PC여야 합니다.
  - **Azure Active Directory에 등록**되어야 합니다. 또한 클라이언트 Exchange ActiveSync ID가 Azure Active Directory에 등록되어 있어야 합니다.

- Azure AD DRS(Device Registration Service)는 Intune 및 Office 365 고객에 대해 자동으로 활성화됩니다. ADFS 디바이스 등록 서비스를 이미 배포한 고객의 온-프레미스 Active Directory에는 등록된 디바이스가 표시되지 않습니다. **Windows PC 및 Windows Phone 디바이스에는 적용되지 않습니다**.

- 해당 디바이스에 배포된 디바이스 준수 정책을 **준수**해야 합니다.

- 디바이스가 조건부 액세스 설정을 충족하지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.
  - 디바이스를 Intune에 등록하지 않았거나 Azure Active Directory에 등록하지 않은 경우, 회사 포털 앱을 설치하고 디바이스를 등록하며 이메일을 활성화하는 방법에 대한 지침이 포함된 메시지가 표시됩니다. 이 프로세스는 또한 디바이스의 Exchange ActiveSync ID를 Azure Active Directory의 디바이스 레코드와 연결합니다.
  - 디바이스가 규정을 준수하지 않으면 사용자를 Intune 회사 포털 웹 사이트 또는 회사 포털 앱으로 디렉션한다는 메시지가 표시됩니다. 회사 포털에서 문제에 대한 정보와 이를 해결하는 방법을 찾을 수 있습니다.

### <a name="support-for-mobile-devices"></a>모바일 디바이스에 대한 지원

- Windows Phone 8.1 이상
- iOS/iPadOS의 기본 메일 앱
- EAS 메일 클라이언트(예: Android 4 이상의 Gmail).
- EAS 메일 클라이언트 **Android 회사 프로필 디바이스:** **회사 프로필**의 **Gmail** 및 **Nine Work for Android Enterprise**만 Android 회사 프로필에 대해 지원됩니다. 조건부 액세스가 Android 회사 프로필에서 작동하려면 Gmail 또는 Nine Work for Android 엔터프라이즈 앱에 대한 이메일 프로필을 배포해야 하며, 이러한 앱을 필수 설치로 배포해야 합니다.

> [!NOTE]
> Android 및 iOS/iPadOS용 Microsoft Outlook은 Exchange 온-프레미스 커넥터를 통해 사용할 수 없습니다. 온-프레미스 사서함에 대해 iOS/iPadOS 및 Android용 Outlook에서 Azure Active Directory 조건부 액세스 정책 및 Intune 앱 보호 정책을 활용하려는 경우 [iOS/iPadOS 및 Android용 Outlook에서 하이브리드 최신 인증 사용](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)을 참조하세요.

### <a name="support-for-pcs"></a>PC 지원

Windows 8.1 이상에 설치된 기본 **메일** 애플리케이션(Intune을 사용하여 MDM에 등록된 경우)

## <a name="configure-exchange-on-premises-access"></a>Exchange 온-프레미스 액세스 구성

Exchange 온-프레미스 액세스 제어를 설정하려면 다음 절차를 사용하기 전에 Exchange 온-프레미스에 대한 [Intune 온-프레미스 Exchange Connector](exchange-connector-install.md)를 하나 이상 설치하고 구성해야 합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **테넌트 관리** > **Exchange 액세스**로 이동한 다음 **Exchange 온-프레미스 액세스**를 선택합니다.

3. **Exchange 온-프레미스 액세스** 창에서 *Exchange 온-프레미스 액세스 제어 사용*에 대해 **예**를 선택합니다.

   > [!div class="mx-imgBorder"]
   > ![Exchange 온-프레미스 액세스의 예시 스크린샷](./media/conditional-access-exchange-create/exchange-on-premises-access.png)

4. **할당**에서 **포함할 그룹 선택**을 선택한 다음 액세스를 구성할 하나 이상의 그룹을 선택합니다.

   선택한 그룹의 구성원에게는 그러한 구성원에게 적용되는 Exchange 온-프레미스 액세스용 조건부 액세스 정책이 있습니다. 이 정책을 받는 사용자는 Intune에 디바이스를 등록하고 준수 프로필을 준수해야 Exchange 온-프레미스에 액세스할 수 있습니다.

   > [!div class="mx-imgBorder"]
   > ![포함할 그룹 선택](./media/conditional-access-exchange-create/select-groups.png)

5. 그룹을 제외하려면 **제외할 그룹 선택**을 선택한 다음 디바이스 등록 요구 사항에서 제외되는 하나 이상의 그룹을 선택하고 Exchange 온-프레미스에 액세스하기 전에 준수 프로필을 준수합니다.

   **저장**을 선택하여 구성을 저장하고 **Exchange 액세스** 창으로 돌아갑니다.

6. 그런 다음 Intune 온-프레미스 Exchange Connector 구성을 구성합니다. 콘솔에서 **테넌트 관리** > **Exchange 액세스**> **Exchange ActiveSync 온-프레미스 커넥터**를 선택한 다음 구성하려는 Exchange 조직의 커넥터를 선택합니다.

7. **사용자 알림**에서 **편집**을 선택하여 *사용자 알림* 메시지를 수정할 수 있는 **조직 편집** 워크플로를 엽니다.

   > [!div class="mx-imgBorder"]
   > ![알림을 위한 조직 편집 워크플로의 예시 스크린샷](./media/conditional-access-exchange-create/edit-organization-user-notification.png)

   디바이스가 비규격이고 Exchange 온-프레미스에 액세스하려는 사용자에게 전송되는 기본 전자 메일 메시지를 수정합니다. 메시지 템플릿에는 마크업 언어가 사용됩니다. 입력할 때 메시지의 미리 보기도 볼 수 있습니다.

   **검토 + 저장**을 선택한 다음 **저장**을 선택하여 편집 내용을 저장하면 Exchange 온-프레미스 액세스의 구성이 완료됩니다.

   > [!TIP]
   > 마크업 언어에 대한 자세한 내용은 이 Wikipedia [문서](https://en.wikipedia.org/wiki/Markup_language)를 참조하세요.

8. 그런 다음 **Advanced Exchange ActiveSync 액세스 설정**을 선택하여 디바이스 액세스 규칙을 구성하는 *고급 Exchange ActiveSync 액세스 설정* 워크플로를 엽니다.

   > [!div class="mx-imgBorder"]
   > ![고급 설정을 위한 조직 편집 워크플로의 예시 스크린샷](./media/conditional-access-exchange-create/edit-organization-advanced-settings.png)

   - **관리되지 않는 디바이스 액세스**의 경우는 다음과 같이 조건부 액세스의 영향을 받지 않는 디바이스에서 액세스하는 전역 기본값 규칙 또는 기타 규칙을 설정합니다.

     - **액세스 허용** - 모든 디바이스에서 Exchange 온-프레미스에 즉시 액세스할 수 있습니다. 이전 절차에 포함된 것으로 구성한 그룹의 사용자에게 속한 디바이스는 이후에 준수 정책을 준수하지 않거나 Intune에 등록되지 않은 것으로 평가되는 경우 차단됩니다.

     - **액세스 차단** 및 **격리** – 모든 디바이스가 Exchange 온-프레미스에 초기 액세스하지 못하도록 즉시 차단합니다. 이전 절차에 포함된 것으로 구성한 그룹의 사용자에게 속한 디바이스는 Intune에서 디바이스를 등록한 후에 액세스를 받고 준수 상태로 평가됩니다.

       삼성 Knox Standard를 실행하지 *않는* Android 디바이스는 이 설정을 지원하지 않으므로 항상 차단됩니다.

   - **디바이스 플랫폼 예외**에서 **추가**를 선택한 다음 사용자 환경의 필요에 따라 세부 정보를 지정합니다.

      **관리되지 않는 디바이스 액세스** 설정이 **차단됨**으로 설정된 경우 등록되고 준수 상태에 있는 디바이스는 차단에 대한 플랫폼 예외가 있는 경우에도 허용됩니다.  

9. **확인**을 선택하여 편집 내용을 저장합니다.

10. **검토 + 저장**을 선택한 다음 **저장**을 선택하여 Exchange 조건부 액세스 정책을 저장합니다.

## <a name="next-steps"></a>다음 단계

그런 다음 규정 준수 정책을 만들고 사용자에게 할당하여 Intune에서 모바일 디바이스를 평가하게 합니다. [디바이스 규정 준수 시작](device-compliance-get-started.md)을 참조하세요.

[Microsoft Intune에서 Intune 온-프레미스 Exchange 커넥터 문제 해결](https://support.microsoft.com/help/4471887)
