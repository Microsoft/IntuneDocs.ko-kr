---
title: Microsoft Intune 앱으로 회사 디바이스 등록| Microsoft Docs
description: Intune에서 회사 Android 디바이스를 등록하는 방법을 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/07/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ef7ec650c65206eeab69d8f666dc4fb39052bbdb
ms.sourcegitcommit: 549352bdea93cc2809e3e0010bfcc10bd44dc728
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68862311"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Microsoft Intune 앱으로 회사 디바이스 등록

회사 소유의 Android 디바이스를 등록하면 회사 이메일, 앱 및 조직에서 사용할 수 있는 기타 데이터에 안전하게 액세스 할 수 있습니다. Microsoft Intune 앱은 Android 6.0 이상을 실행하는 회사 소유의 디바이스를 지원합니다. 등록하는 동안 새 디바이스와 초기화된 디바이스에 자동으로 설치됩니다. 

등록하는 방법은 네 가지입니다. 어떤 옵션을 사용할지는 회사가 알려줘야 합니다.
 
* NFC(근거리 통신)  
* 토큰  
* QR 코드   
* Google Zero Touch  

## <a name="enroll-device"></a>디바이스 등록 
디바이스를 설정하고 등록하려면 다음 단계를 완료하세요.  

> [!NOTE]
> Android 버전 또는 디바이스 제조업체에서 여기 절차에 포함되지 않은 추가 단계를 완료하도록 요구할 수도 있습니다. 스크린샷에 보이는 색상과 텍스트가 디바이스에 다르게 나타날 수도 있습니다.  

1. 새 디바이스나 초기화된 디바이스를 켭니다.  
2. **시작** 화면에서 언어를 선택합니다.   QR 코드 또는 NFC를 통해 등록해야 하는 경우, 해당 메서드와 일치하는 아래 단계를 수행합니다.  
     * NFC: NFC 지원 디바이스를 프로그래머 디바이스에 맞대고 탭하여 조직의 네트워크에 연결합니다. 화면의 지시를 따릅니다. Chrome 서비스 약관 화면이 표시되면 5단계를 진행합니다.  

     * QR 코드: [QR 코드 등록](#qr-code-enrollment)의 단계를 완료합니다.  

     다른 메서드를 사용해야 하는 경우 3단계를 진행합니다.    

3. Wi-Fi에 연결하고 **다음**을 탭합니다. 등록 메서드와 일치하는 단계를 따릅니다. 

    * 토큰: Google 로그인 화면이 표시되면 [토큰 등록](#token-enrollment) 단계를 완료합니다.  
    * Google Zero Touch: Wi-Fi에 연결하면 조직에서 디바이스가 인식됩니다. 4단계를 진행하고 설치가 완료될 때까지 화면의 지시를 따릅니다.    
 
       ![Google Zero Touch를 사용하는 경우 표시되는 Google 사용 약관 화면의 예제 이미지이며, Accept & Continue(동의 및 계속) 단추가 강조 표시되어 있습니다.](./media/google-zero-touch-intune-app-01.png)   
   
4. Google의 사용 약관을 검토합니다. 그런 다음, **ACCEPT & CONTINUE**(동의 및 계속)을 탭합니다.  

      ![Google 약관 화면의 예제 이미지이며, Accept & Continue(동의 및 계속) 단추가 강조 표시되어 있습니다.](./media/fully-managed-intune-app-04.png)   

6. Chrome의 서비스 약관을 검토합니다. 그런 다음, **ACCEPT & CONTINUE**(동의 및 계속)을 탭합니다.  

   ![Chrome 서비스 약관 화면의 예제 이미지이며, Accept & Continue(동의 및 계속) 단추가 강조 표시되어 있습니다.](./media/fully-managed-intune-app-06.png)   

7. 로그인 화면에서 회사 또는 학교 계정으로 로그인합니다.   

    a. 이메일을 입력하고 **다음**을 탭합니다.      
    b. 암호를 입력하고 **로그인**을 탭합니다.  

8. 조직의 요구 사항에 따라, 화면 잠금 또는 암호화와 같은 설정을 업데이트하라는 메시지가 표시될 수 있습니다. 이런 메시지가 표시되면 **설정**을 탭하고 화면의 지시를 따릅니다.  

   ![회사 전화 설정 화면의 예제 이미지이며 설정 단추가 강조 표시되어 있습니다.](./media/fully-managed-intune-app-10.png)   

9. 디바이스에 회사 앱을 설치하려면 **설치**를 탭합니다. 설치가 완료되면 **다음**을 탭합니다.  

   ![회사 전화 설정 화면의 예제 이미지이며 설치 단추가 강조 표시되어 있습니다.](./media/fully-managed-intune-app-11.png)   

10. **시작** 을 탭 하 여 Microsoft Intune 앱을 열고 장치를 등록 합니다. 

    ![회사 전화 설정 화면의 예제 이미지이며 시작 단추가 강조 표시되어 있습니다.](./media/fully-managed-intune-app-17.png)   

11. 로그인을 탭 **하 **고 다음** 을 탭 하 여 등록을 시작 합니다.** 등록이 **완료** 되었다는 메시지가 표시 되 면 완료 를 탭 합니다.  

    ![액세스 설정, 장치 등록 화면, 완료 단추 강조 표시의 예제 이미지](./media/fully-managed-intune-app-19.png)   

10. 디바이스가 준비되었다는 메시지가 표시되면, **완료**를 탭합니다.  

    ![회사 전화 설정 화면의 예제 이미지이며 완료 단추가 강조 표시되어 있습니다.](./media/fully-managed-intune-app-18.png)   

조직의 리소스에 액세스 하는 데 문제가 있는 경우 장치에서 추가 설정을 업데이트 해야 할 수 있습니다. Microsoft Intune 앱에 로그인 하 여 필수 업데이트를 확인 합니다.   


## <a name="qr-code-enrollment"></a>QR 코드 등록  
이 섹션에서는 회사에서 제공한 QR 코드를 스캔합니다.  완료되면 디바이스 등록 단계로 리디렉션됩니다.     
  
1. **시작** 화면에서 화면을 다섯 번 탭하여 QR 코드 설정을 시작합니다.  

   ![디바이스 설정 시작 화면의 예제 이미지이며 화면을 탭하라는 지침이 강조 표시되어 있습니다.](./media/qr-code-intune-app-01.png)  

2. 화면의 지시에 따라 Wi-Fi에 연결합니다.  
3. 디바이스에 QR 코드 스캐너가 없으면 스캐너가 설치되는 진행률이 설정 화면에 표시됩니다. 설치가 완료될 때까지 기다립니다.  
4. 메시지가 표시되면 조직에서 제공한 등록 프로필 QR 코드를 스캔합니다.  
5. [디바이스 등록](#enroll-device), 4단계로 돌아가서 설정을 계속합니다.  

## <a name="token-enrollment"></a>토큰 등록  
이 섹션에서는 회사에서 제공한 토큰을 입력합니다. 완료되면 디바이스 등록 단계로 리디렉션됩니다.  

1. Google 로그인 화면의 **Email or phone**(이메일 또는 전화) 상자에 **afw#setup**을 입력합니다. **다음**을 탭합니다. 

   ![Google 로그인 화면의 예제 이미지이며, "afw#setup"이 필드에 입력된 것을 보여줍니다.](./media/token-intune-app-01.png)   

2. **Android 디바이스 정책** 앱에 대해 **설치**를 선택합니다. 설치를 계속합니다. 디바이스에 따라, 추가 사용 약관을 검토하고 승인해야 할 수도 있습니다.    

3. **이 디바이스 등록** 화면에서 **다음**을 선택합니다.  

4. **코드 입력**을 선택합니다.  

5. **Scan or enter code**(스캔 또는 코드 입력) 화면에 조직에서 제공한 코드를 입력합니다.  **다음**을 클릭합니다.  

   ![Scan or enter code(스캔 또는 코드 입력) 화면의 예제 이미지이며 [다음] 단추가 강조 표시되어 있습니다.](./media/token-intune-app-04.png)  

6. [디바이스 등록](#enroll-device), 4단계로 돌아가서 설정을 계속합니다.  



## <a name="next-steps"></a>다음 단계   
여전히 도움이 필요하세요? 회사 지원팀에 문의하거나(연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 확인) <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 팀</a>으로 메일을 보내세요.  
