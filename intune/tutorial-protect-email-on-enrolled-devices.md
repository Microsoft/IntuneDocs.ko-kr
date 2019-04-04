---
title: 자습서 - Intune 관리 디바이스에서 Exchange Online 메일 보호
titleSuffix: Microsoft Intune
description: 관리 디바이스 및 Outlook 앱을 사용하도록 요구하는 Azure AD 조건부 액세스 및 iOS Intune 준수 정책을 통해 Exchange Online을 보호하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4a8e873c48ceb59bfb8ac98fec9a29fa51d6cd3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799771"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>자습서: 관리 디바이스에서 Exchange Online 이메일 보호
디바이스 준수 정책을 조건부 액세스와 함께 사용하여 iOS 디바이스가 Intune에서 관리되고 승인된 메일 앱을 사용하는 경우에만 Exchange Online 메일에 액세스할 수 있도록 하는 방법을 알아봅니다. 

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다. 
> [!div class="checklist"]
> * Intune iOS 장치 준수 정책을 만들어 장치가 준수해야 하는 충족 조건을 설정합니다.
> * iOS 디바이스가 Intune에 등록하고, Intune 정책을 준수하고, 승인된 Outlook 모바일 앱을 사용하여 Exchange Online 메일에 액세스하도록 요구하는 Azure AD(Azure Active Directory) 조건부 액세스 정책을 만듭니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건
  - 이 자습서를 사용하려면 다음 구독이 있는 테스트 테넌트가 필요합니다.
    - Azure Active Directory Premium([평가판](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Exchange([평가판](https://go.microsoft.com/fwlink/p/?LinkID=510938))를 포함하는 Office 365 Business 구독
  - 시작하기 전에 [빠른 시작: iOS용 이메일 디바이스 프로필 만들기](quickstart-email-profile.md)의 단계에 따라 iOS 디바이스의 테스트 디바이스 프로필을 만듭니다.

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="create-the-ios-device-compliance-policy"></a>iOS 디바이스 준수 정책 만들기
Intune 디바이스 준수 정책을 설정하여 디바이스가 준수 상태로 간주하기 위해 충족해야 하는 조건을 설정합니다. 이 자습서에서는 iOS 디바이스의 디바이스 준수 정책을 만듭니다. 준수 정책은 플랫폼에 특정하므로 평가하려는 각 디바이스 플랫폼의 개별 규정 준수 정책이 필요합니다.

1.  Intune에서 **디바이스 준수** > **정책** > **정책 만들기**를 선택합니다.
2.  **이름**에 **iOS 준수 정책 테스트**를 입력합니다. 
3.  **설명**에 **iOS 준수 정책 테스트**를 입력합니다.
4.  **플랫폼**에서 **iOS**를 선택합니다. 
5.  **설정** > **메일**을 선택합니다. 
     
    1.  **모바일 디바이스에 관리되는 메일 프로필이 있어야 함** 옆에 있는 **필요**를 선택합니다.
    2. **확인**을 선택합니다.

    ![관리되는 메일 프로필을 요구하도록 메일 준수 정책을 설정합니다.](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)
    
6.  **디바이스 상태**를 선택합니다. **탈옥 디바이스** 옆에 있는 **차단**을 선택한 후 **확인**을 선택합니다.
7.  **시스템 보안**을 선택하고 **암호** 설정을 입력합니다. 이 자습서에서는 다음 권장 설정을 선택합니다.
     
    - **모바일 디바이스의 잠금을 해제하는 데 암호 필요**에서 **필요**를 선택합니다.
    - **단순 암호**에서 **차단**을 선택합니다.
    - **최소 암호 길이**에 **4**를 입력합니다.
    - **필수 암호 유형**에서 **영숫자**를 선택합니다.
    - **화면 잠금 후 암호를 요구하기 전까지 최대 시간(분)** 에서 **즉시**를 선택합니다.
    - **암호 만료(일)** 에 **41**을 입력합니다.
    - **재사용을 방지하기 위한 이전 암호 수**에 **5**를 입력합니다.
 
    ![메일 준수 정책의 암호 설정 구성](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8.  **확인**을 선택한 후 **만들기**를 선택합니다.
9.  **만들기**를 선택합니다.

## <a name="create-the-conditional-access-policy"></a>조건부 액세스 정책 만들기
이제 모든 디바이스가 Intune에 등록하고 Exchange Online에 액세스하기 전에 Intune 준수 정책을 준수하도록 요구하는 조건부 액세스 정책을 만들겠습니다. 메일 액세스를 위해 Outlook 앱도 필요합니다. 조건부 액세스 정책은 Azure AD 포털 또는 Intune 포털에서 구성할 수 있습니다. 현재 Intune 포털에 있으므로 여기에서 정책을 만들겠습니다.
1.  Intune에서 **조건부 액세스** > **정책** > **새 정책**을 선택합니다.
1.  **이름**에 **Office 365 메일 정책 테스트**를 입력합니다. 
3.  **할당**에서 **사용자 및 그룹**을 선택합니다. **포함** 탭에서 **모든 사용자**를 선택한 후 **완료**를 선택합니다.

4.  **할당**에서 **클라우드 앱**을 선택합니다. Office 365 Exchange Online 메일을 보호해야 하므로 다음 단계에 따라 선택합니다.
     
    1. **포함** 탭에서 **앱 선택**을 선택합니다.
    2. **선택**을 선택합니다. 
    3. 애플리케이션 목록에서 **Office 365 Exchange Online**을 선택한 후 **선택**을 선택합니다. 
    4. **완료**를 선택합니다.
  
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5.  **할당**에서 **조건** > **장치 플랫폼**을 선택합니다.
     
    1. **구성**에서 **예**를 선택합니다.
    2. **포함** 탭에서 **모든 디바이스**를 선택한 후 **완료**를 선택합니다. 
    3. **완료**를 다시 선택합니다.
   
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6.  **할당** 섹션에서 **조건** > **클라이언트 앱**을 선택합니다.
     
    1. **구성**에서 **예**를 선택합니다.
    2. 이 자습서에서는 **모바일 앱 및 데스크톱 클라이언트** 및 **최신 인증 클라이언트**(iOS용 Outlook 및 Android 용 Outlook 같은 앱을 참조함)를 선택합니다. 다른 확인란을 모두 선택 취소합니다.
    3. **완료**를 선택한 후 **완료**를 다시 선택합니다.
    
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7.  **액세스 제어**에서 **권한 부여**를 선택합니다. 
     
    1. **권한 부여** 창에서 **액세스 허용**을 선택합니다.
    2. **준수 상태로 표시된 디바이스 필요**를 선택합니다. 
    3. **승인된 클라이언트 앱 필요**를 선택합니다.
    4. **여러 컨트롤의 경우**에서 **선택된 컨트롤이 모두 필요함**을 선택합니다. 이렇게 설정하면 디바이스가 메일에 액세스를 시도할 때 선택한 요구 사항이 둘 다 적용됩니다.
    5. **선택**을 선택합니다.
     
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8.  **정책 사용**에서 **켜기**를 선택합니다.
     
    ![Office 365 Exchange Online 앱 선택](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9.  **만들기**를 선택합니다.

## <a name="try-it-out"></a>기능 직접 사용해 보기
직접 만든 정책을 사용하면 Office 365에 로그인을 시도하는 모든 iOS 디바이스가 Intune에 등록하고 iOS용 Outlook 모바일 앱을 사용해야 합니다. iOS 디바이스에서 이 시나리오를 테스트하려면 테스트 테넌트에서 사용자의 자격 증명을 사용하여 Exchange Online에 로그인을 시도합니다. 디바이스를 등록하고 Outlook 모바일 앱을 설치하라는 메시지가 표시됩니다.
1. iPhone에서 테스트하려면 **설정** > **암호 및 계정** > **계정 추가** > **Exchange**로 이동합니다.
2. 테스트 테넌트에 있는 사용자의 메일 주소를 입력하고 **다음**을 누릅니다.
3. **로그인**을 누릅니다.
4. 테스트 사용자의 암호를 입력하고 **로그인**을 누릅니다.
5. 등록 옵션과 함께 리소스에 액세스하려면 디바이스를 관리해야 한다는 메시지가 표시됩니다. 

## <a name="clean-up-resources"></a>리소스 정리
더 이상 필요하지 않은 테스트 정책을 제거할 수 있습니다.
1. [Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다.
2. **디바이스 준수** > **정책**을 선택합니다.
3. **정책 이름** 목록에서 테스트 정책의 상황에 맞는 메뉴(**...**)를 선택한 후 **삭제**를 선택합니다. **확인**을 선택하여 확인합니다.
4. **조건부 액세스** > **정책**을 선택합니다.
5. **정책 이름** 목록에서 테스트 정책의 상황에 맞는 메뉴(**...**)를 선택한 후 **삭제**를 선택합니다. **예**를 선택하여 확인합니다.

 ## <a name="next-steps"></a>다음 단계 
이 자습서에서는 iOS 디바이스가 Intune에 등록하고 Outlook 앱을 사용하여 Exchange Online 메일에 액세스하도록 요구하는 정책을 만들었습니다. Intune과 함께 조건부 액세스를 사용하여 Office 365 Exchange Online용 Exchange ActiveSync 클라이언트를 비롯한 다른 앱 및 서비스를 보호하는 방법에 대한 자세한 내용은 [조건부 액세스 설정](conditional-access.md)을 참조하세요.
