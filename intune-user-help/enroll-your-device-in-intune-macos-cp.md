---
title: Intune 회사 포털를 사용 하 여 Mac 등록 | Microsoft Docs
description: 회사 포털 앱을 사용 하 여 Intune에서 Mac을 등록 하는 방법에 대해 알아봅니다.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: e04950a67938d883b0762c03efa371fcb74d0731
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75855479"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>회사 포털 앱을 사용 하 여 macOS 장치 등록  

Intune 회사 포털 앱으로 macOS 디바이스를 등록하여 회사 또는 학교 전자 메일, 파일 및 앱에 대한 보안 액세스 권한을 얻습니다.

조직에서는 일반적으로 사용자가 장치를 등록 해야 소유 데이터에 액세스할 수 있습니다. 디바이스가 등록되면 *관리*됩니다. 조직은 Intune과 같은 MDM(모바일 디바이스 관리) 공급자를 통해 디바이스에 정책과 앱을 할당할 수 있습니다. 디바이스에서 회사 또는 학교 정보에 대한 지속적인 액세스를 얻으려면 조직의 정책 설정과 일치하도록 디바이스를 구성해야 합니다.  

이 문서에서는 조직의 요구 사항을 충족하도록 macOS용 회사 포털 앱을 사용하여 디바이스를 등록, 구성 및 유지 관리하는 방법을 설명합니다.  


## <a name="what-to-expect-from-the-company-portal-app"></a>회사 포털 앱에서 예상되는 상황

초기 설치 중에 회사 포털 앱을 사용 하려면 사용자가 로그인 하 여 조직에 인증 해야 합니다. 그런 다음 조직의 요구 사항에 맞게 구성 해야 하는 장치 설정을 사용자에 게 알려 줍니다. 회사 포털 예를 들어 조직은 종종 사용자가 충족해야 하는 최소 또는 최대 문자 암호 요구 사항을 설정합니다.    

장치를 등록 한 후에는 항상 조직의 요구 사항에 따라 장치를 보호 하도록 회사 포털 합니다. 예를 들어 신뢰할 수 없는 소스에서 앱을 설치 하는 경우 회사 포털에서 사용자에 게 경고 하 고 조직의 리소스에 대 한 액세스를 제한할 수 있습니다. 이와 같은 앱 보호 정책은 일반적입니다. 액세스 권한을 다시 얻으려면 신뢰할 수 없는 앱을 제거 해야 할 가능성이 높습니다. 

등록 후 조직이 다단계 인증과 같은 새 보안 요구 사항을 적용하는 경우 회사 포털은 이를 알려줍니다. 디바이스에서 작업을 계속할 수 있도록 설정을 조정할 수 있습니다.  

등록에 대해 자세히 알아보려면 [회사 포털 앱을 설치하고 디바이스를 등록하면 어떤 일이 생기나요?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)를 참조하세요.  

## <a name="get-your-macos-device-managed"></a>MacOS 장치 관리 받기  
다음 단계를 사용 하 여 macOS 장치를 조직에 등록 합니다. 장치에서 macOS 10.12 이상을 실행 해야 합니다.   

> [!NOTE]
> 이 프로세스 전체에서 키 집합에 저장 된 기밀 정보를 사용 하 회사 포털를 허용 하 라는 메시지가 표시 될 수 있습니다. 이러한 프롬프트는 Apple 보안의 일부입니다. 프롬프트가 표시 되 면 로그인 키 집합 암호를 입력 하 고 **항상 허용**을 선택 합니다. **Enter** 키를 누르거나 키보드에서 **반환** 하는 경우 프롬프트에서 **허용**을 대신 선택 하면 추가 프롬프트가 표시 될 수 있습니다.  

### <a name="install-company-portal-app"></a>회사 포털 앱 설치  
1. [내 Mac 등록](https://go.microsoft.com/fwlink/?linkid=853070)으로 이동 합니다.  
2. 회사 포털 pkg 파일이 다운로드 됩니다. 설치 관리자를 열고 단계를 계속 진행 합니다. 
3. 소프트웨어 사용권 계약에 동의합니다. 
4. 소프트웨어를 설치 하려면 장치 암호 또는 등록 된 지문을 입력 하세요.  
5. 회사 포털을 엽니다. 

> [!IMPORTANT]
> Microsoft 자동 업데이트가 열리고 Microsoft 소프트웨어를 업데이트할 수 있습니다. 모든 업데이트를 설치한 후 회사 포털 앱을 엽니다. 최상의 설치 환경을 위해 최신 버전의 Microsoft 자동 업데이트 및 회사 포털를 설치 합니다.  


### <a name="enroll-your-mac"></a>Mac 등록  


1. 회사 또는 학교 계정을 사용하여 회사 포털에 로그인합니다.  
2. 앱이 열리면 **시작**을 선택 합니다.  
3. 조직에서 등록 된 장치에서 볼 수 있는 사항과 볼 수 없는 내용을 검토 합니다. 그런 다음 **계속**을 선택합니다.
4.  메시지가 표시 되 면 **관리 프로필 설치** 화면에서 장치 암호를 입력 합니다.

    ![회사 포털의 예제 스크린샷, 관리 프로필 설치 화면, 암호 프롬프트 강조 표시](./media/install-management-profile-macos-1912.PNG)   
5. **장치 관리 확인** 화면에서 **시스템 기본 설정 열기**를 선택 합니다.  

    !["시스템 기본 설정 열기" 단추를 강조 표시 하는 장치 관리 확인 화면의 예제 스크린샷](./media/confirm-device-management-macos-1912.PNG)  
6. 장치의 시스템 기본 설정이 열립니다. 장치 프로필 목록에서 **관리 프로필** **을 선택 하 고 승인 > ** **승인**을 선택 합니다.  
    ![시스템 기본 설정의 스크린샷 스크린샷, 관리 프로필 화면, "승인" 단추를 강조 표시 합니다.](./media/management-profile-approve-macos-1912.PNG)   
1. 회사 포털로 돌아가서 **계속**을 선택 합니다.    
2. 조직에서 장치 설정을 업데이트 해야 할 수 있습니다. 설정 업데이트가 완료 되 면 **설정 확인**을 선택 합니다.  

    ![회사 포털, 장치 설정 업데이트 화면의 예제 스크린샷, "설정 확인" 단추가 강조 표시 됩니다.](./media/update-settings-mac-1911.PNG)  
9. 설치가 완료 되 면 **완료**를 선택 합니다.  


 ## <a name="troubleshooting-and-feedback"></a>문제 해결 및 피드백   

등록 하는 동안 문제가 발생 하는 경우 **도움말** > **진단 보고서 보내기** 로 이동 하 여 Microsoft 앱 개발자에 게 문제를 보고 합니다. 이 정보는 앱을 개선 하는 데 사용 됩니다. 또한 IT 지원 담당자가 도움을 받을 수 있는 경우이 정보를 사용 하 여 문제를 해결 합니다.  

Microsoft에 문제를 보고 한 후 사용자 환경의 세부 정보를 IT 지원 담당자에 게 보낼 수 있습니다. **전자 메일 세부 정보**를 선택 합니다. 전자 메일의 본문에서 경험을 입력 합니다. 지원 담당자의 전자 메일 주소를 찾으려면 회사 포털 앱 > **연락처**로 이동 합니다. 또는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 확인합니다.  
 

또한 Microsoft Intune 회사 포털 팀은 여러분의 의견을 듣고 싶습니다. **도움말** > **사용자 의견 보내기** 로 이동 하 여 생각과 아이디어를 공유 합니다.  

## <a name="unverified-profiles"></a>확인되지 않은 프로필  
**시스템 기본 설정** > **프로필**에서 설치된 MDM(모바일 디바이스 관리) 프로필을 보면 일부 프로필의 상태가 확인되지 않음으로 표시될 수 있습니다. 관리 프로필에 확인됨 상태가 표시되는 한, 염려할 필요가 없습니다.  

관리 프로필은 MDM 채널 연결을 정의합니다. 관리 프로필이 확인되는 한, 채널을 통해 머신에 전달되는 다른 프로필은 관리 프로필의 보안 특성을 상속합니다.  

## <a name="updating-the-company-portal-app"></a>회사 포털 앱 사용

회사 포털 앱 업데이트는 macOS용 Microsoft 자동 업데이트를 통해 다른 Office 앱과 동일한 방식으로 수행됩니다. [macOS용 Microsoft 앱 업데이트](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1)에 대해 자세히 알아보세요.  

## <a name="next-steps"></a>다음 단계  
여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.  


