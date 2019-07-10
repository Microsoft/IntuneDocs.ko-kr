---
title: Microsoft Intune과 Symantec 통합 설정
titleSuffix: Microsoft Intune
description: 회사 리소스에 대한 모바일 디바이스 액세스를 제어하기 위해 Microsoft Intune을 사용하여 Symantec Endpoint Protection Mobile 솔루션을 설정하는 방법입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/21/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd185a42d36de6aaf1e6d0ff0b8e34619b02c093
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572430"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>Intune과 Symantec Endpoint Protection Mobile 통합 설정

Intune과 SEP Mobile(Symantec Endpoint Protection Mobile) 솔루션을 통합하려면 다음 단계를 완료하세요. Single Sign-On 기능을 보유하려면 Azure AD에 SEP Mobile 앱을 추가해야 합니다.

## <a name="before-you-begin"></a>시작하기 전에

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>Intune과 SEP Mobile을 통합하는 데 사용되는 Azure AD 계정

- SEP Mobile 기본 설정 프로세스를 시작하려면 [Symantec Endpoint Protection Mobile 관리 콘솔](https://aad.skycure.com)에 Azure AD 계정이 제대로 구성되어 있어야 합니다.
- 통합을 수행하려면 Azure AD 계정이 전역 관리자 계정이어야 합니다.
### <a name="network-setup"></a>네트워크 설정

Symantec 문서 [Setting up your network configuration](https://portal.skycure.com/articles/Documentation/Setting-up-your-network-configuration-26-8-2016)(네트워크 구성 설정)을 참조하여 SEP Mobile 설정과 통합을 적용하도록 네트워크가 제대로 구성되어 있는지 확인할 수 있습니다.

### <a name="full-integration-vs-read-only"></a>전체 통합 및 읽기 전용

SEP Mobile은 Intune과의 통합을 두 가지 모드로 지원합니다.

- **읽기 전용 통합(기본 설정):** Azure Active Directory에서 디바이스를 인벤토리에 포함하고 Symantec Endpoint Protection Mobile 관리 콘솔에서 해당 정보를 채우기만 합니다.
<br>
    - Symantec Endpoint Protection Mobile 관리 콘솔에서 **Intune에 디바이스 상태 및 위험 보고** 및 **Intune에 보안 문제도 보고** 상자가 선택되지 않은 경우 통합은 읽기 전용이므로 Intune에서 디바이스 상태(준수 또는 미준수)가 변경되지 않습니다.
<br></br>
- **전체 통합:** 디바이스의 위험 및 보안 문제 세부 정보에 대해 SEP Mobile에서 보고하도록 허용합니다. 이렇게 하면 두 클라우드 서비스 간 양방향 통신이 이루어집니다.

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>SEP Mobile 앱을 Azure AD 및 Intune과 함께 사용하는 방법은 무엇인가요?

- **iOS 앱:** 최종 사용자가 iOS 앱을 사용하여 Azure AD에 로그인할 수 있습니다.

- **Android 앱:** 최종 사용자가 Android 앱을 사용하여 Azure AD에 로그인할 수 있습니다.

- **관리 앱:** Intune과의 서비스 간 통신을 사용하도록 설정하는 SEP Mobile Azure AD 다중 테넌트 앱입니다.

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>Intune과 SEP Mobile 간의 읽기 전용 통합을 설정하려면

> [!IMPORTANT]
> SEP Mobile 관리자 자격 증명은 Azure Active Directory에서 유효한 사용자에 속해 있는 메일 계정으로 구성됩니다. 이에 속해 있지 않으면 로그인에 실패합니다. SEP Mobile은 SSO(Single Sign-On)로 해당 관리자를 인증하는 데 Azure Active Directory를 사용합니다.

1. [Symantec Endpoint Protection Mobile 관리 콘솔](https://aad.skycure.com)로 이동합니다.

2. **SEP Mobile 관리자 자격 증명**을 입력한 다음, **계속**을 선택합니다.

3. **설정**으로 이동하고 **Intune 통합**에서 **기본 설정**을 선택합니다.

4. **iOS 앱** 옆에 있는 **Active Directory에 추가**를 선택합니다.

    ![Symantec Endpoint Protection Mobile 관리 콘솔의 이미지](./media/symantec-portal-basic-add.png)

5. 로그인 페이지가 열리면 Intune 자격 증명을 입력한 다음, **동의**를 선택합니다.

    ![iOS 앱 Intune 로그인 프롬프트 이미지](./media/symantec-portal-basic-accept.png)

6. Azure AD에 앱을 추가한 후, 앱이 성공적으로 추가되었다는 표시가 나타납니다.

    ![iOS 앱 완료 화면 이미지](./media/symantec-portal-basic-added.png)

7. **SEP Mobile Android** 및 **관리** 앱에 대해 이러한 단계를 반복합니다.

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>SEP Mobile에 Azure AD 보안 그룹 추가

SEP Mobile을 실행하는 모든 디바이스가 포함된 Azure AD 보안 그룹을 추가해야 합니다.

- SEP Mobile을 실행하는 디바이스의 보안 그룹을 모두 입력하여 선택한 다음, 변경 내용을 저장합니다.

    ![SEP Mobile 앱에 대한 사용자 그룹을 보여주는 이미지](./media/symantec-portal-basic-groups.png)

SEP Mobile은 Mobile Threat Defense 서비스를 실행하는 디바이스를 Azure AD 보안 그룹과 동기화합니다.

![SEP Mobile 관리 콘솔의 보안 그룹 구성 이미지](./media/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>Intune과 SEP Mobile 간의 전체 통합을 설정하려면

### <a name="retrieve-the-directory-id-in-azure-ad"></a>Azure AD에서 디렉터리 ID 검색

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.

2. 검색 상자에 “Active Directory”를 입력한 다음, **Azure Active Directory**를 선택합니다.

3. **속성**을 선택합니다.

4. **디렉터리 ID** 옆에 있는 복사 아이콘을 선택한 다음, 안전한 위치에 붙여넣습니다. 나중 단계에서 이 식별자가 필요합니다.

    ![Azure Portal에서 디렉터리 ID를 보여주는 이미지](./media/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>(선택 사항) SEP Mobile 앱을 실행해야 하는 디바이스의 전용 보안 그룹을 만듭니다.
1. [Azure Portal](https://portal.azure.com)의 **관리**에서 **사용자 및 그룹**을 선택한 다음, **모든 그룹**을 선택합니다.

2. **추가** 단추를 선택합니다. 그룹 **이름**을 입력합니다. **멤버 자격 유형**에서 **할당됨**을 선택합니다.

3. **멤버** 블레이드에서 그룹 멤버를 선택한 다음, **선택** 단추를 선택합니다.

4. **그룹** 블레이드에서 **만들기**를 선택합니다.

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>Symantec Endpoint Protection Mobile과 Intune 간에 통합 설정

1. [Symantec Endpoint Protection Mobile 관리 콘솔](https://aad.skycure.com)로 이동합니다.

2. **SEP Mobile 관리자 자격 증명**을 입력한 다음, **계속**을 선택합니다.

3. **설정** > **통합** > **Intune** > **EMM 통합 선택** 섹션으로 이동합니다.

4. **디렉터리 ID** 상자에 이전 섹션의 Azure Active Directory에서 복사한 디렉터리 ID를 붙여넣고 설정을 저장합니다.

    ![SEP Mobile 포털에서 디렉터리 ID를 보여주는 이미지](./media/symantec-portal-directory-ID.png)

5. **설정** > **통합** > **Intune** > **기본 설정** 섹션으로 이동합니다.

6. **iOS 앱** 옆에 있는 **Active Directory에 추가** 단추를 선택합니다.

    ![Active Directory에 iOS 앱을 추가하는 작업을 보여주는 이미지](./media/symantec-portal-basic-add.png)

7. 디렉터리를 관리하는 Office 365 계정용 Azure Active Directory 자격 증명을 사용하여 로그인합니다.

8. **동의** 단추를 선택하여 SEP Mobile iOS 앱을 Azure Active Directory에 추가합니다.

    ![동의 단추를 보여주는 이미지](./media/symantec-portal-basic-accept.png)

9. **Android 앱** 및 **관리 앱**에 대해 동일한 프로세스를 반복합니다.

10. SEP Mobile 앱(예: 이전에 만든 보안 그룹)을 실행해야 하는 모든 사용자 그룹을 선택합니다.

    ![SEP Mobile 앱에 대한 사용자 그룹을 보여주는 이미지](./media/symantec-portal-basic-groups.png)

11. SEP Mobile은 선택된 그룹의 디바이스를 동기화하고 Intune에 정보를 보고하기 시작합니다. 전체 통합 섹션에서 이 데이터를 볼 수 있습니다. **설정** > **통합** > **Intune** > **전체 통합** 섹션으로 이동합니다.

     ![SEP Mobile 전체 통합 완료를 보여주는 이미지](media/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>다음 단계

[SEP Mobile 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)
