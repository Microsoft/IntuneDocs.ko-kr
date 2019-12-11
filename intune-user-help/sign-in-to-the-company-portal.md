---
title: 회사 포털 앱에 로그인하는 방법 | Microsoft Docs
description: 여러 플랫폼에서 회사 포털 앱에 로그인하는 방법을 알아보세요.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68a44027c14e0a52d72fc032a6ab42413fa8df96
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508292"
---
# <a name="sign-in-to-company-portal"></a>회사 포털에 로그인  

회사 포털 앱에 로그인 하는 방법에는 다음 세 가지가 있습니다.

* 업무용 메일 주소 및 암호에 로그인합니다.  
* 인증서 기반 인증으로 로그인합니다.  
* 다른 디바이스에서 로그인합니다.    


## <a name="sign-in-with-your-email-address-and-password"></a>메일 주소 및 암호를 사용하여 로그인합니다.
다음 단계는 iOS에 대 한 회사 포털의 스크린샷을 보여 줍니다.  

1. 장치에서 앱을 열고 **로그인**을 탭 합니다.  

   [![회사 포털 로그인 페이지의 예제 스크린샷](/intune-user-help/media/intune-ios-cp-signin-1908.png)](/intune-user-help/media/intune-ios-cp-signin-lightbox-1908.png#lightbox)  


2. **회사 또는 학교 계정**을 입력하고 **다음**을 탭합니다.

   ![사용자는 같은 화면에서 전자 메일 및 암호 대신 전자 메일 주소만 입력하라는 메시지를 받습니다.](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. 암호를 입력하고 **로그인**을 탭합니다.

   ![전자 메일 주소가 승인된 후에 암호를 입력하라는 메시지가 표시됩니다.](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. 앱에서 자격 증명을 확인 합니다. 완료 되 면 조직의 리소스에 액세스 하 여 사용 가능한 앱을 설치할 수 있습니다.  

   ![인증 프로세스를 진행하고 나면 회사 포털 앱에 로그인되며 이 상태는 로드 중 막대로 표현됩니다.](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="sign-in-with-certificate-based-authentication"></a>인증서 기반 인증으로 로그인

1. 디바이스에서 회사 포털 앱을 엽니다.  

2. **회사 또는 학교 계정**을 입력합니다.  

3. **인증서로 로그인** 링크를 탭합니다.  

4. 인증서를 사용하려면 **계속**을 탭합니다.  

## <a name="sign-in-from-another-device"></a>다른 디바이스에서 로그인

회사에서 스마트 카드를 사용 하 여 컴퓨터에 액세스 하는 경우 다른 장치에서 로그인 하 여 인증 해야 할 가능성이 높습니다.  

1. 디바이스에서 회사 포털 앱을 엽니다. 회사 리소스에 액세스 하는 데 사용 하는 장치 인지 확인 합니다.       

1. **다른 디바이스에서 로그인**을 선택합니다.  

   ![회사 포털 로그인 페이지는 사용자에게 이메일 주소에 대한 메시지를 표시합니다.  "다음" 단추 및 "다른 디바이스에서 로그인"에 대한 링크를 표시합니다. 또한 "계정에 액세스할 수 없습니까?"에 대한 링크를 포함합니다. Microsoft 개인정보처리방침 정보로 이동하게 하는 하단의 링크](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. 회사 포털에 로그인하기 위한 고유한 일회성 코드를 받게 됩니다. 코드를 복사 합니다.

   ![회사 컴퓨터의 고유 암호를 사용하여 https://microsoft.com/devicelogin 페이지로 이동하여 로그인 시 해당 코드를 사용하라는 지침이 제공됩니다.](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. 인증을 위해 사용 중인 다른 장치에서 브라우저를 열고 [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin)으로 이동 합니다. 코드를 입력 하거나 붙여 넣습니다.  

   ![회사 포털 앱이 아닌 작업 컴퓨터에서 사용자 브라우저 이미지 표시되는 "디바이스 로그인" 페이지에서 사용자에게 회사 포털 앱에서 받은 코드를 입력하라는 메시지가 나타납니다.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. __계속__ 을 선택 하 여 회사 포털에서 작업 장치에 로그인 할 수 있도록 허용 합니다.   

   ![사용자는 필드에 고유한 코드를 입력하고 "디바이스 로그인" 사이트에서 Intune 회사 포털이 로그인에 필요한 인증을 수신하는 올바른 앱인지 확인을 요구합니다.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. 코드가 확인되고 나면 창을 닫아도 됩니다.  

   ![사용자가 디바이스에서 회사 포털 앱에 로그인했으며 이 페이지를 닫을 수 있음을 언급하는 확인 페이지](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. 회사 포털 앱이 회사 장치에서 로그인 합니다.  

   ![인증 프로세스를 진행하고 나면 회사 포털 앱에 로그인되며 해당 프로세스는 로드 중 막대로 표시됩니다.](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.  
