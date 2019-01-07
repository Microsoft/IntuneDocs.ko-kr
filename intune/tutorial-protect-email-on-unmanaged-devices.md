---
title: 자습서 - 관리되지 않는 디바이스에서 Exchange Online 메일 보호
titlesuffix: Microsoft Intune
description: Intune 앱 보호 정책 및 Azure AD 조건부 액세스를 사용하여 Office 365 Exchange Online을 보호하는 방법을 알아봅니다.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/11/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bcf66037995c6b5cb2b0c5b3f090d3af2e42cd6a
ms.sourcegitcommit: 8019bdd8117806c6a3a73a8c6d40af1a3def6d90
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53262886"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>자습서: 관리되지 않는 디바이스에서 Exchange Online 메일 보호

디바이스가 Intune과 같은 디바이스 관리 솔루션에 등록되지 않았더라도 조건부 액세스와 함께 앱 보호 정책을 사용하여 Exchange Online을 보호하는 방법을 알아봅니다. 이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다. 

> [!div class="checklist"]
> * Outlook 앱용 Intune 앱 보호 정책을 만듭니다. “다른 이름으로 저장”을 차단하여 사용자가 앱 데이터로 수행할 수 있는 작업과 잘라내기, 복사 및 붙여넣기 작업을 제한합니다. 
> * Outlook 앱이 Exchange Online에서 회사 메일에만 액세스하도록 허용하는 Azure AD(Azure Active Directory) 조건부 액세스 정책을 만듭니다. iOS 및 Android용 Outlook과 같은 최신 인증 클라이언트에는 MFA(다단계 인증)도 필요합니다.

## <a name="prerequisites"></a>전제 조건
  - 이 자습서를 사용하려면 다음 구독이 있는 테스트 테넌트가 필요합니다.
    - Azure Active Directory Premium([평가판](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Intune 구독([평가판](free-trial-sign-up.md))
    - Exchange([평가판](https://go.microsoft.com/fwlink/p/?LinkID=510938))를 포함하는 Office 365 Business 구독

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다. Azure Portal에서 **모든 서비스** > **Intune**을 선택하여 Intune을 찾습니다.

## <a name="create-the-app-protection-policy"></a>앱 보호 정책 만들기
이 자습서에서는 앱 수준에서 보호를 설정하도록 Outlook 앱에 대한 Intune 앱 보호 정책을 설정합니다. 업무용으로 앱을 열려면 PIN이 필요합니다. 또한 앱 간의 데이터 공유를 제한하고 회사 데이터가 개인 위치에 저장되지 않도록 합니다.

1.  Intune에서 **클라이언트 앱** > **앱 보호 정책** > **정책 추가**를 차례로 선택합니다.
2.  **이름**에 **Outlook 앱 정책 테스트**를 입력합니다.
3.  **설명**에 **Outlook 앱 정책 테스트**를 입력합니다.
4.  **앱**을 선택합니다. 앱 목록에서 **Outlook**을 선택한 후 **선택**을 선택합니다.
5.  **설정**을 선택합니다. 
6.  **데이터 재배치**에서 이 자습서에 맞게 다음 설정을 선택합니다.

    - **앱이 다른 앱으로 데이터를 전송하도록 허용**에서 **없음**을 선택합니다.
    - **앱이 다른 앱의 데이터를 받도록 허용**에서 **없음**을 선택합니다.
    - **“다른 이름으로 저장” 차단**에서 **예**를 선택합니다.
    - **다른 앱에서 잘라내기, 복사 및 붙여넣기 제한**에서 **차단됨**을 선택합니다.
   
     ![Outlook 앱 보호 정책 데이터 재배치 설정 선택](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-data-relocation.png)
    
7.  **액세스 작업**에서 이 자습서에 맞게 다음 설정을 선택합니다.

    - **액세스 시 PIN 필요**에서 **예**를 선택합니다.
    - **액세스하려면 회사 자격 증명 필요**에서 **예**를 선택합니다.
    - 다른 모든 설정은 기본값으로 유지합니다.
 
     ![Outlook 앱 보호 정책 액세스 작업 선택](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-access-actions.png)

9.  **확인**을 선택합니다.
10. **만들기**를 선택합니다.

Outlook용 앱 보호 정책이 만들어집니다. 이제 디바이스에서 Outlook 앱을 사용하도록 조건부 액세스를 설정할 수 있습니다.

## <a name="create-conditional-access-policies"></a>조건부 액세스 정책 만들기
이제 모든 디바이스 플랫폼에 적용되는 두 가지 조건부 액세스 정책을 만들어보겠습니다. 첫 번째 정책은 iOS용 Outlook 및 Android용 Outlook과 같은 최신 인증 클라이언트가 승인된 Outlook 앱 및 MFA를 사용하도록 요구합니다. 두 번째 정책은 Exchange ActiveSync 클라이언트가 승인된 Outlook 앱을 사용하도록 요구합니다. (현재 Exchange Active Sync는 디바이스 플랫폼 이외의 조건을 지원하지 않습니다.) Azure AD 포털 또는 Intune 포털에서 조건부 액세스 정책을 구성할 수 있습니다. 현재 Intune 포털에 있으므로 여기에서 정책을 만들겠습니다.
### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>최신 인증 클라이언트에 대한 MFA 정책 만들기
1.  Intune에서 **조건부 액세스** > **정책** > **새 정책**을 선택합니다.
1.  **이름**에 **최신 인증 클라이언트용 테스트 정책**을 입력합니다. 
3.  **할당**에서 **사용자 및 그룹**을 선택합니다. **포함** 탭에서 **모든 사용자**를 선택한 후 **완료**를 선택합니다.

4.  **할당**에서 **클라우드 앱**을 선택합니다. Office 365 Exchange Online 메일을 보호해야 하므로 다음 단계에 따라 선택합니다.
     
    1. **포함** 탭에서 **앱 선택**을 선택합니다.
    2. **선택**을 선택합니다. 
    3. 애플리케이션 목록에서 **Office 365 Exchange Online**을 선택한 후 **선택**을 선택합니다. 
    4. **완료**를 선택합니다.
  
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5.  **할당**에서 **조건** > **장치 플랫폼**을 선택합니다.
     
    1. **구성**에서 **예**를 선택합니다.
    2. **포함** 탭에서 **모든 플랫폼(지원되지 않는 플랫폼 포함)** 을 선택합니다. 
    3. **완료**를 선택합니다.
   
6.  **조건** 창에서 **클라이언트 앱**을 선택합니다.
     
    1. **구성**에서 **예**를 선택합니다.
    2. **모바일 앱 및 데스크톱 클라이언트** 및 **최신 인증 클라이언트**를 선택합니다.
    3. 다른 확인란을 선택 취소합니다.
    4. **완료**를 선택한 후 **완료**를 다시 선택합니다.
    
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7.  **액세스 제어**에서 **권한 부여**를 선택합니다. 
     
    1. **권한 부여** 창에서 **액세스 허용**을 선택합니다.
    2. **다단계 인증 필요**를 선택합니다.
    4. **승인된 클라이언트 앱 필요**를 선택합니다.
    5. **여러 컨트롤의 경우**에서 **선택된 컨트롤이 모두 필요함**을 선택합니다. 이렇게 설정하면 디바이스가 메일에 액세스를 시도할 때 선택한 요구 사항이 둘 다 적용됩니다.
    6. **선택**을 선택합니다.
     
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

8.  **정책 사용**에서 **켜기**를 선택합니다.
     
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)

9.  **만들기**를 선택합니다.

최신 인증 클라이언트에 대한 조건부 액세스 정책이 만들어집니다. 이제 Exchange Active Sync 클라이언트에 대한 정책을 만들 수 있습니다.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Exchange Active Sync 클라이언트에 대한 정책 만들기
1.  Intune에서 **조건부 액세스** > **정책** > **새 정책**을 선택합니다.
2.  **이름**에 **EAS 클라이언트용 테스트 정책**을 입력합니다. 
3.  **할당**에서 **사용자 및 그룹**을 선택합니다. **포함** 탭에서 **모든 사용자**를 선택한 후 **완료**를 선택합니다.

4.  **할당**에서 **클라우드 앱**을 선택합니다. 다음 단계를 사용하여 Office 365 Exchange Online 메일을 선택합니다.
     
    1. **포함** 탭에서 **앱 선택**을 선택합니다.
    2. **선택**을 선택합니다. 
    3. 애플리케이션 목록에서 **Office 365 Exchange Online**을 선택한 후 **선택**을 선택합니다. 
    4. **완료**를 선택합니다.

5.  **할당**에서 **조건** > **장치 플랫폼**을 선택합니다.
     
    1. **구성**에서 **예**를 선택합니다.
    2. **포함** 탭에서 **모든 플랫폼(지원되지 않는 플랫폼 포함)** 을 선택한 후 **완료**를 선택합니다. 
    3. **완료**를 다시 선택합니다.

6.  **조건** 창에서 **클라이언트 앱**을 선택합니다.
     
    1. **구성**에서 **예**를 선택합니다.
    2. **모바일 앱 및 데스크톱 클라이언트**를 선택합니다.
    3. **Exchange ActiveSync 클라이언트** 및 **지원되는 플랫폼에만 정책 적용**을 선택합니다. 
    4. 다른 확인란을 모두 선택 취소합니다.
    5. **완료**를 선택한 후 **완료**를 다시 선택합니다.
    
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)

7.  **액세스 제어**에서 **권한 부여**를 선택합니다. 
     
    1. **권한 부여** 창에서 **액세스 허용**을 선택합니다.
    4. **승인된 클라이언트 앱 필요**를 선택합니다. 다른 확인란을 모두 선택 취소합니다.
    6. **선택**을 선택합니다.
     
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

8.  **정책 사용**에서 **켜기**를 선택합니다.

9.  **만들기**를 선택합니다.

앱 보호 정책 및 조건부 액세스가 이제 설정되었으며 테스트할 준비가 되었습니다. 

## <a name="try-it-out"></a>기능 직접 사용해 보기
직접 만든 정책을 사용할 경우 디바이스가 Intune에 등록되고 Outlook 모바일 앱을 사용하여 Office 365 메일에 액세스해야 합니다. iOS 디바이스에서 이 시나리오를 테스트하려면 테스트 테넌트에서 사용자의 자격 증명을 사용하여 Exchange Online에 로그인을 시도합니다.
1. iPhone에서 테스트하려면 **설정** > **암호 및 계정** > **계정 추가** > **Exchange**로 이동합니다.
2. 테스트 테넌트에 있는 사용자의 메일 주소를 입력하고 **다음**을 누릅니다.
3. **로그인**을 누릅니다.
4. 테스트 사용자의 암호를 입력하고 **로그인**을 누릅니다.
5. MFA를 설정해야 함을 나타내는 **추가 정보 필요** 메시지가 표시됩니다. 계속해서 추가 확인 방법을 설정합니다.
6. 그러면 IT 부서에서 승인하지 않은 앱을 사용하여 이 리소스를 열려고 한다는 메시지가 표시됩니다. 이것은 기본 메일 앱 사용이 차단됨을 의미합니다. 로그인을 취소합니다.
7.  Outlook 앱을 열고 **설정** > **계정 추가** > **메일 계정 추가**를 선택합니다.
8. 테스트 테넌트에 있는 사용자의 메일 주소를 입력하고 **다음**을 누릅니다.
9. **Office 365로 로그인**을 누릅니다. 추가 인증 및 등록을 요구하는 메시지가 표시됩니다. 로그인한 후 잘라내기, 복사, 붙여넣기 및 “다른 이름으로 저장” 등의 작업을 테스트할 수 있습니다.

## <a name="clean-up-resources"></a>리소스 정리
더 이상 필요하지 않은 테스트 정책을 제거할 수 있습니다.
1. [Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다.
2. **디바이스 준수** > **정책**을 선택합니다.
3. **정책 이름** 목록에서 테스트 정책의 상황에 맞는 메뉴(**...**)를 선택한 후 **삭제**를 선택합니다. **확인**을 선택하여 확인합니다.
4. **조건부 액세스** > **정책**을 선택합니다.
5. **정책 이름** 목록에서 각 테스트 정책의 상황에 맞는 메뉴(**...**)를 선택한 후 **삭제**를 선택합니다. **예**를 선택하여 확인합니다.

 ## <a name="next-steps"></a>다음 단계 
이 자습서에서는 Outlook 앱으로 수행할 수 있는 작업을 제한하는 앱 보호 정책을 만들고, 최신 인증 클라이언트를 위한 MFA와 Outlook 앱과 요구하는 조건부 액세스 정책을 만들었습니다. Intune과 함께 조건부 액세스를 사용하여 다른 앱 및 서비스를 보호하는 방법에 대한 자세한 내용은 [조건부 액세스 설정](conditional-access.md)을 참조하세요.
