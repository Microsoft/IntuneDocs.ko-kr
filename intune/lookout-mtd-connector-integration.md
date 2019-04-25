---
title: Microsoft Intune과 Lookout 통합 설정
titleSuffix: Microsoft Intune
description: 회사 리소스에 대한 모바일 디바이스 액세스를 제어하기 위해 Lookout MTD(Mobile Threat Defense)와 Intune을 통합하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3644ebaa0582cea5e79c5123ac89b97bc6f97f29
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61507528"
---
# <a name="set-up-your-lookout-mobile-threat-defense-integration-with-intune"></a>Intune과 Lookout Mobile Threat Defense 통합 설정

Lookout Mobile Threat Defense 구독을 설정하려면 다음 단계를 수행해야 합니다.

| #        |단계  |
| ------------- |:-------------|
| 1 | [Azure AD 정보 수집](#collect-azure-ad-information) |
| 2 | [구독 구성](#configure-your-subscription) |
| 3 | [등록 그룹 구성](#configure-enrollment-groups) |
| 4 | [상태 동기화 구성](#configure-state-sync) |
| 5 | [오류 보고서를 메일로 받는 사람의 정보 구성](#configure-error-report-email-recipient-information) |
| 6 | [등록 설정 구성](#configure-enrollment-settings) |
| 7 | [메일 알림 구성](#configure-email-notifications) |
| 8 | [위협 분류 구성](#configure-threat-classification) |
| 9 | [등록 점검](#watching-enrollment) |

> [!IMPORTANT]
> 아직 Azure AD 테넌트와 연결되지 않은 기존 Lookout Mobile Endpoint Security 테넌트는 Azure AD와 Intune을 통합하는 데 사용할 수 없습니다. 새 Lookout Mobile Endpoint Security 테넌트를 만들려면 Lookout 지원 센터로 문의하세요. 새 테넌트를 사용하여 Azure AD 사용자를 등록할 수 있습니다.

## <a name="collect-azure-ad-information"></a>Azure AD 정보 수집
Lookout Mobility Endpoint Security 테넌트가 Azure AD 구독과 연결되어 Lookout을 Intune과 통합합니다. Lookout Mobile Threat Defense 서비스 구독을 사용하도록 설정하려면 Lookout 지원(enterprisesupport@lookout.com)에 다음 정보가 필요합니다.

* **Azure AD 테넌트 ID**
* **전체** Lookout 콘솔 액세스를 위한 **Azure AD 그룹 개체 ID**
* Lookout 콘솔에 **제한된** 액세스를 하기 위한 **Azure AD 그룹 개체 ID**(선택 사항)

다음 단계에 따라 Lookout 지원 팀에 제공해야 하는 정보를 수집합니다.

1. [Azure Portal](https://portal.azure.com)에 로그인한 후 구독을 선택합니다. 

2. 구독 이름을 선택하면 결과 URL은 구독 ID를 포함합니다.  구독 ID를 찾는 데 문제가 있으면 [Microsoft 지원 문서](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b)ID를 찾는 방법에 대한 팁을 확인하세요.

3. Azure AD 그룹 ID를 찾습니다. Lookout 콘솔은 두 가지 수준의 액세스를 지원합니다.  
   * **모든 권한:** Azure AD 관리자는 모든 권한이 있는 사용자 그룹을 만들고, 선택적으로 제한된 권한이 있는 사용자 그룹을 만들 수 있습니다.  이러한 그룹의 사용자만 **Lookout 콘솔**에 로그인할 수 있습니다.
   * **제한된 권한:** 이 그룹의 사용자는 Lookout 콘솔의 여러 구성 및 등록 관련 모듈에 대한 액세스 권한이 없으며, Lookout 콘솔의 **보안 정책** 모듈에 대한 읽기 전용 액세스 권한을 갖습니다.  

     > [!TIP] 
     > 사용 권한에 대한 자세한 내용은 Lookout 웹 사이트에서 [이 문서](https://personal.support.lookout.com/hc/articles/114094105653)를 참조하세요.

     > [!NOTE] 
     > **그룹 개체 ID**는 **Azure AD 관리 포털**의 그룹 **속성** 페이지에 있습니다.

4. 이 정보를 수집한 후 Lookout 지원 센터로 문의하세요(메일: enterprisesupport@lookout.com). Lookout 지원 팀은 주요 담당자와 함께 수집한 정보를 사용하여 구독을 등록하고 Lookout 엔터프라이즈 계정을 만듭니다.

## <a name="configure-your-subscription"></a>구독 구성

1. Lookout 지원 팀이 Lookout 엔터프라이즈 계정을 만들면 Lookout에서 사용자 회사의 주요 담당자에게 로그인 URL에 대한 링크(<https://aad.lookout.com/les?action=consent>)가 포함된 이메일을 전송합니다.

2. Azure AD 테넌트를 등록하려면 Lookout 콘솔에 처음 로그인할 때 Azure AD 역할이 전역 관리자인 사용자 계정을 사용해야 합니다. 이후에는 로그인에 이 수준의 Azure AD 권한이 필요하지 않습니다. 동의 페이지가 표시됩니다. **동의**를 선택하여 등록을 완료합니다. 동의하고 승인하면 Lookout 콘솔로 리디렉션됩니다.

   ![Lookout 콘솔의 첫 번째 로그인 페이지 스크린샷](./media/lookout_mtp_initial_login.png)

3. [Lookout 콘솔](https://aad.lookout.com)의 **시스템** 모듈에서 **커넥터** 탭과 **Intune**을 차례로 선택합니다.

   ![커넥터 탭의 Intune 옵션이 포함된 Lookout 콘솔의 이미지](./media/lookout_mtp_setup-intune-connector.png)

4. **커넥터** > **연결 설정**으로 이동하여 **하트비트 빈도**(단위: 분)를 지정합니다.

   ![하트비트 주기가 구성된 연결 설정 탭의 이미지](./media/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>등록 그룹 구성
1. [Azure AD 관리 포털](https://manage.windowsazure.com)에서 Lookout 통합을 테스트할 적은 수의 사용자를 포함하는 Azure AD 보안 그룹을 만드는 것이 좋습니다.

    > [!NOTE] 
    > 식별되고 지원되는 Azure AD 내 등록 그룹 사용자의 모든 Lookout 지원, Intune 등록 디바이스가 Lookout MTD 콘솔에 등록되며 활성화할 수 있습니다.

2. [Lookout 콘솔](https://aad.lookout.com)의 **시스템** 모듈에서 **커넥터** 탭, **등록 관리**를 차례로 선택하여 Lookout에서 해당 디바이스를 등록해야 하는 사용자 집합을 정의합니다. 등록할 Azure AD 보안 그룹 **표시 이름**을 추가합니다.

    ![Intune Connector 등록 페이지의 스크린샷](./media/lookout-mtp-enrollment.png)

    >[!IMPORTANT]
    > **표시 이름**은 Azure Portal에서 보안 그룹의 **속성**에 표시된 것처럼 대/소문자를 구분합니다. 아래 그림에 표시된 것처럼 보안 그룹의 **표시 이름**은 카멜식 대/소문자입니다. 반면 제목은 모두 소문자입니다. Lookout 콘솔에서 보안 그룹에 대한 **표시 이름**의 대/소문자를 일치시키세요.
    >![Azure Portal, Azure Active Directory 서비스, 속성 페이지의 이미지](./media/aad-group-display-name.png)

    >[!NOTE] 
    >가장 좋은 방법은 새 디바이스의 확인 간격을 기본값(5분)으로 하는 것입니다. 현재 제한 사항, **Lookout에서는 그룹 표시 이름의 유효성을 검사할 수 없습니다.** Azure Portal의 **표시 이름** 필드가 Azure AD 보안 그룹과 정확히 일치하도록 하세요. **중첩 그룹 만들기는 지원되지 않습니다.**  Lookout에 사용된 Azure AD 보안 그룹에는 사용자만 포함해야 하며, 다른 그룹은 포함할 수 없습니다.

3.  그룹이 추가된 후 다음번에 사용자가 지원되는 해당 디바이스에서 Lookout for Work 앱을 열면 디바이스가 Lookout에서 활성화됩니다.

4.  결과에 만족한 경우 추가 사용자 그룹까지 등록을 확장합니다.

## <a name="configure-state-sync"></a>상태 동기화 구성
**상태 동기화** 옵션에서 Intune에 전송해야 할 데이터 유형을 지정합니다.  Lookout Intune 통합이 제대로 작동하려면 디바이스 상태와 위협 상태가 둘 다 필요합니다. 이러한 설정은 기본적으로 사용됩니다.

## <a name="configure-error-report-email-recipient-information"></a>오류 보고서를 메일로 받는 사람의 정보 구성
**오류 관리** 옵션에서 오류 보고서를 받아야 하는 메일 주소를 입력합니다.

![Intune Connector 오류 관리 페이지의 스크린샷](./media/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>등록 설정 구성
**커넥터** 페이지의 **시스템** 모듈에서 디바이스 연결이 끊긴 것으로 간주되는 일 수를 지정합니다.  연결이 끊긴 장치는 Intune 조건부 액세스 정책을 기반으로 규정 비준수로 간주되어 회사 애플리케이션 액세스가 차단됩니다. 1일에서 90일 사이의 값을 지정할 수 있습니다.

![시스템 모듈의 Lookout 등록 설정](./media/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>메일 알림 구성
위협 경고를 메일로 받으려면 알림을 받아야 하는 사용자 계정으로 [Lookout 콘솔](https://aad.lookout.com)에 로그인합니다. **시스템** 모듈의 **기본 설정** 탭에서 알림의 위협 수준을 선택한 후 **켬**으로 설정합니다. 변경 내용을 저장합니다.

![사용자 계정이 표시된 기본 설정 페이지의 스크린샷](./media/lookout-mtp-email-notifications.png) 이제 메일 알림을 받지 않으려면 알림을 **끔**으로 설정하고 변경 내용을 저장합니다.

### <a name="configure-threat-classification"></a>위협 분류 구성
Lookout Mobile Threat Defense는 다양한 종류의 모바일 위협을 분류합니다. [Lookout 위협 분류](https://personal.support.lookout.com/hc/articles/114094130693)에는 기본 위험 수준이 지정되어 있습니다. 이 수준은 언제든지 회사 요구 사항에 맞게 변경할 수 있습니다.

![위협 및 분류를 보여 주는 정책 페이지의 스크린샷](./media/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> 위험 수준은 Mobile Threat Defense의 중요한 측면으로, 런타임 시 이러한 위험 수준에 따라 Intune 통합에서 디바이스 규정 준수를 측정하기 때문입니다. Intune 관리자가 디바이스에 최소 수준의 활성 위협(**높음**, **중간** 또는 **낮음**)이 있다면 디바이스가 규정을 준수하지 않는 것으로 식별하도록 정책 규칙을 설정할 수 있습니다. Lookout Mobile Threat Defense의 위협 분류 정책을 통해 디바이스의 규정 준수 여부가 Intune에서 바로 측정됩니다.

## <a name="watching-enrollment"></a>등록 감시
설치가 완료되면 Lookout Mobile Threat Defense에서 지정한 등록 그룹에 해당하는 디바이스를 Azure AD에 폴링하기 시작합니다.  등록된 디바이스에 대한 정보는 디바이스 모듈에서 찾을 수 있습니다.  디바이스의 초기 상태는 보류 중으로 표시됩니다.  디바이스에서 Lookout for Work 앱을 설치하고 열고 활성화하면 디바이스 상태가 변경됩니다.  Lookout for Work 앱을 디바이스에 푸시하는 방법에 대한 자세한 내용은 [Intune을 사용하여 Lookout for Work 앱 추가](mtd-apps-ios-app-configuration-policy-add-assign.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

[Lookout 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)
