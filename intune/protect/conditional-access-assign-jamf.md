---
title: Jamf 디바이스에 대한 디바이스 준수 정책
titleSuffix: Microsoft Intune
description: 보안 Jamf 관리 디바이스를 도우려면 Azure Active Directory의 조건부 액세스와 함께 Microsoft Intune 준수 정책을 사용합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b09b30fd32caace9ed3259350c01548d5e5fae15
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74161597"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Jamf Pro로 관리되는 Mac에서 준수 적용

[Jamf Pro를 Intune과 통합](conditional-access-integrate-jamf.md)할 때 조건부 액세스 정책을 사용하여 조직 요구 사항이 있는 Mac 디바이스에 규정 준수를 적용할 수 있습니다.  이 문서는 다음 작업에 도움이 됩니다.  

- 조건부 액세스 정책 만들기
- Jamf를 사용하여 관리하는 디바이스에 Intune 회사 포털 앱을 배포하도록 Jamf Pro 구성
- 디바이스 사용자가 Jamf 셀프 서비스 앱 내에서 시작하는 회사 포털 앱에 로그인할 때 Azure AD에 등록할 디바이스 구성 디바이스를 등록하면 회사 리소스 액세스를 위한 조건부 액세스 정책이 디바이스를 평가할 수 있게 해주는 Azure AD의 ID가 설정됩니다.  
 
이 문서의 절차를 수행하려면 Intune 및 Jamf Pro 콘솔에 대한 액세스 권한이 필요합니다.

## <a name="set-up-device-compliance-policies-in-intune"></a>Intune에서 디바이스 준수 정책 설정

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스** > **준수 정책**을 선택합니다. 이전에 만든 정책을 사용 중인 경우 콘솔에서 해당 정책을 선택하고 이 절차의 다음 단계로 이동합니다. 새 정책을 만들려면 **정책 만들기**를 선택하고 **macOS**의 *플랫폼*을 사용하여 정책에 세부 정보를 지정합니다. 조직의 요구 사항을 충족하도록 *설정* 및 *비준수에 대한 작업*을 구성하고 **만들기**를 선택하여 정책을 저장합니다.

3. 정책 *개요* 창에서 **할당**을 선택합니다. 제공된 옵션을 사용하여 이 정책을 수신하는 Azure Active Directory(Azure AD) 사용자 및 보안 그룹을 구성합니다. Jamf를 Intune과 통합해도 장치 그룹을 대상으로 하는 규정 준수 정책은 지원되지 않습니다.

4. **저장**을 선택하면 정책이 사용자에게 배포됩니다.  

배포하는 정책은 할당된 사용자가 사용하는 디바이스를 대상으로 합니다. 이러한 디바이스에 대해 준수 여부를 평가합니다. 준수 디바이스는 Azure AD에서 "*준수 상태로 표시된 장치 필요*" 설정에 준수 상태로 표시됩니다.  

> [!NOTE]
> Intune에서 정책을 준수하려면 전체 디스크 암호화가 필요합니다.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Jamf Pro에서 macOS용 회사 포털 앱 배포

Jamf Pro에서 Intune 회사 포털을 배포할 정책을 만듭니다. 이 정책은 회사 포털 앱을 배포하여 Jamf 셀프 서비스에서 사용할 수 있게 합니다. 사용자가 Azure AD에 디바이스를 등록할 수 있도록 Jamf Pro에서 정책을 만들기 전에 이 정책을 만듭니다.  

다음 절차를 완료하려면 macOS 디바이스 및 Jamf Pro 포털에 대한 액세스 권한이 필요합니다. 

### <a name="to-deploy-the-company-portal-app"></a>회사 포털 앱을 배포하려면  

1. macOS 디바이스에서 [macOS용 회사 포털 앱](https://go.microsoft.com/fwlink/?linkid=862280)의 현재 버전을 다운로드하되 설치는 하지 않습니다. 앱의 복사본만 있으면 Jamf Pro에 앱을 업로드할 수 있습니다.  

2. Jamf Pro를 열고 **컴퓨터 관리** > **패키지**로 이동합니다.

3. macOS용 회사 포털 앱이 포함된 새 패키지를 만든 다음 **저장**을 선택합니다.

4. **컴퓨터** > **정책**을 열고 **새로 만들기**를 선택합니다.

5. **일반** 페이로드를 사용하여 정책에 대한 설정을 구성합니다. 이 설정은 다음과 같아야 합니다.
   - 트리거: **등록 완료** 및 **Recurring Check-in**(되풀이 체크 인)을 선택합니다.
   - 실행 빈도: **Once per computer**(컴퓨터당 한 번)를 선택합니다.

6. **패키지** 페이로드를 선택하고 **구성**을 클릭합니다.

7. **추가**를 클릭하여 회사 포털 앱이 포함된 패키지를 선택합니다.

8. **작업** 팝업 메뉴에서 **설치**를 선택합니다.
9. 패키지의 설정을 구성합니다.

10. **범위** 탭을 선택하여 회사 포털 앱을 설치할 컴퓨터를 지정합니다. **저장**을 선택합니다. 다음 번에 컴퓨터에서 선택한 트리거가 발생하고 **일반** 페이로드의 기준을 충족하면 범위가 지정된 디바이스에서 정책이 실행됩니다.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Jamf Pro에서 사용자가 자신의 디바이스를 Azure Active Directory에 등록하도록 하는 정책 만들기  

Jamf Pro 셀프 서비스를 통해 macOS용 [회사 포털을 배포](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)하고 나면 Azure AD에 사용자의 디바이스를 등록하는 Jamf Pro 정책을 만들 수 있습니다. 

디바이스를 등록하려면 디바이스 사용자가 Jamf 셀프 서비스 내에서 Intune 회사 포털 앱을 수동으로 선택해야 합니다. 이메일, Jamf Pro 알림 또는 조직에서 이 작업을 수행하여 디바이스를 등록하도록 지시할 때 사용하는 다른 방법을 통해 [최종 사용자에게 문의](../fundamentals/end-user-educate.md)하는 것이 좋습니다. 

> [!WARNING]
> 회사 포털 앱을 수동으로 시작하는 경우(예: 애플리케이션 또는 다운로드 폴더에서) 디바이스가 등록되지 않습니다. 최종 사용자가 회사 포털 앱을 수동으로 시작하면 **'AccountNotOnboarded'** 경고가 표시됩니다.

### <a name="to-create-the-registration-policy"></a>등록 정책을 만들려면  

1. Jamf Pro에서 **컴퓨터** > **정책**으로 이동하여 디바이스 등록을 위한 새 정책을 만듭니다.

2. 트리거 및 실행 빈도를 포함하여 **Microsoft Intune 통합** 페이로드를 구성합니다.

3. **범위** 탭을 선택하고 정책 범위를 모든 대상 디바이스로 지정합니다.

4. **셀프 서비스** 탭을 선택하여 정책을 Jamf 셀프 서비스에서 사용할 수 있게 설정합니다. **디바이스 준수** 범주에 정책을 포함합니다. **저장**을 클릭합니다.

## <a name="validate-intune-and-jamf-integration"></a>Intune 및 Jamf 통합 유효성 검사  

Jamf Pro 콘솔을 사용하여 Jamf Pro와 Microsoft Intune 간 통신이 잘 되는지 확인합니다. 

- Jamf Pro에서 **설정** > **전역 관리** > **Microsoft Intune 통합**으로 이동한 후 **테스트**를 선택합니다.

    콘솔에 연결 성공 또는 실패를 알리는 메시지가 표시됩니다.  

Jamf Pro 콘솔에서 수행하는 연결 테스트가 실패하면 Jamf 구성을 검토합니다. 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Intune에서 Jamf 관리 디바이스를 제거합니다.

Jamf 관리 디바이스를 제거하려면 Microsoft Endpoint Manager 관리 센터를 열고 **디바이스** > **모든 디바이스**를 선택한 다음 **삭제**를 선택합니다.  여러 디바이스를 선택하고 **삭제**를 클릭하여 대량 디바이스 삭제를 사용하도록 설정할 수 있습니다.

[Jamf 관리 디바이스를 Jamf Pro 문서에서 제거](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)하는 방법에 대해 알아봅니다. 또한 추가 도움을 위해 지원 티켓을 [Jamf 지원](https://www.jamf.com/support/)와 함께 제출할 수 있습니다. 

## <a name="next-steps"></a>다음 단계

- [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Azure Active Directory에서 조건부 액세스 시작](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
