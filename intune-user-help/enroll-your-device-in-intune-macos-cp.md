---
title: 회사 포털을 사용하여 Intune에 macOS 디바이스 등록 | Microsoft Docs
description: 회사 포털 앱을 사용하여 Intune에 macOS 디바이스를 등록하는 방법을 설명합니다.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee725d118353e18924858569ac861992d19f839a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506192"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>회사 포털 앱을 사용하여 Intune에 macOS 디바이스 등록

Intune 회사 포털 앱으로 macOS 디바이스를 등록하여 조직의 이메일, 파일 및 앱에 대한 보안 액세스 권한을 얻습니다.

조직에서 소유하는 데이터에 액세스하려면 먼저 디바이스 관리를 받아야 합니다. 디바이스가 관리된 후 조직은 모바일 디바이스 관리 공급자를 통해 디바이스에 정책 및 앱을 푸시할 수 있습니다. 디바이스에서 회사 또는 학교 정보에 대한 지속적인 액세스를 얻으려면 정책 설정과 일치하도록 디바이스를 구성해야 합니다.  

이 문서에서는 macOS용 Intune 회사 포털 앱에서 조직의 요구 사항에 맞게 디바이스를 등록, 구성 및 유지 관리할 수 있는 방법을 설명합니다.  
</br>
> [!VIDEO https://www.youtube.com/embed/Pa2pfhwq_yk?rel=0]

## <a name="what-to-expect-from-the-company-portal-app"></a>회사 포털 앱에서 예상되는 상황

초기 설정 중 앱에서는 조직에 사용자를 인증하도록 요구합니다. 그런 다음, 수행해야 하는 디바이스 설정을 알려줍니다. 예를 들어 조직은 종종 사용자가 충족해야 하는 최소 또는 최대 문자 암호 요구 사항을 설정합니다.    

디바이스가 등록된 후 회사 포털 앱은 디바이스가 보호되는지 계속해서 확인합니다. 예를 들어 신뢰할 수 없는 소스에서 앱을 설치하는 경우 앱은 사용자에게 경고하고 경우에 따라 회사 데이터에 대한 액세스를 취소합니다. 이와 같은 앱 보호 정책은 조직에서 일반적이며 사용자는 종종 액세스 권한을 다시 얻기 위해 먼저 신뢰할 수 없는 앱을 제거해야 합니다.

등록 후 조직이 다단계 인증과 같은 새 보안 요구 사항을 적용하는 경우 회사 포털 앱은 이를 알려줍니다. 디바이스에서 작업을 계속할 수 있도록 설정을 조정할 수 있습니다.  

등록에 대해 자세히 알아보려면 [회사 포털 앱을 설치하고 디바이스를 등록하면 어떤 일이 생기나요?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)를 참조하세요.  

## <a name="get-your-device-managed"></a>디바이스를 관리하도록 설정  
MacOS 10.12 이상을 실행 하는 macOS 장치를 등록 하려면 다음 단계를 사용 합니다.   


1. 회사 포털 웹 사이트에 액세스하려면 __Safari__에서 새 창을 열고, https://portal.manage.microsoft.com 으로 이동합니다.  

2. 회사 또는 학교 계정을 사용하여 회사 포털 웹 사이트에 로그인합니다.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. 페이지의 왼쪽 위 모서리로 이동하고 **메뉴** > **디바이스**를 클릭합니다.  

4. __디바이스__ 페이지에 관리되는 디바이스 목록 또는 배너가 표시됩니다. 표시되는 내용은 관리되는 디바이스가 있는지에 따라 달라집니다. 
    * 나열되지 않은 디바이스를 추가하려면 **여기를 탭하여 사용 중인 디바이스를 알려주거나 새 디바이스를 추가하세요.** 를 읽는 배너를 선택합니다.
    * 디바이스가 없는 경우 배너는 **관리되는 디바이스가 없습니다. 여기를 탭하여 이 장치를 추가하세요.** 를 읽습니다. 배너를 클릭하여 디바이스를 추가합니다.  

     ![클릭할 위치를 강조 표시하는 배너 옵션 주위에 빨간색 사각형이 있는 디바이스 페이지의 스크린샷](./media/CP-enroll-MACOS-1808.png)  
5. 회사 포털에 현재 표시된 메시지와 일치하는 다음 단계를 완료합니다.  
    * 처음으로 디바이스를 추가하는 경우 디바이스에 회사 포털 앱을 다운로드할지 묻는 메시지가 나타납니다. **다운로드**를 클릭하여 계속합니다.  

         ![macOS 회사 포털 앱을 다운로드하는 프롬프트 화면의 예제 스크린샷 사용자는 프롬프트의 왼쪽 아래에 파란색 다운로드 단추 또는 오른쪽 아래에 회색 취소 단추를 클릭하여 선택할 수 있는 옵션이 있습니다.](./media/CP-enroll-download-macOS-1808.png)  

    * 관리되는 macOS 디바이스가 이미 있는 경우 현재 관리되는 macOS 디바이스 목록이 있는 프롬프트를 받게 됩니다. **내 디바이스가 여기에 나열되지 않습니다** > **다운로드**를 선택하여 추가하는 디바이스에서 회사 포털 앱을 다운로드합니다.  

         ![macOS 회사 포털 앱을 다운로드하는 프롬프트 화면의 예제 스크린샷 사용자는 *내 디바이스가 여기에 나열되지 않습니다* 또는 페이지 중 특정 디바이스를 선택하는 옵션이 있습니다. 파란색 다운로드 단추가 프롬프트의 왼쪽 아래에 표시되고, 회색 취소 단추가 오른쪽 아래에 표시됩니다.](./media/cp-mac-os-device-isnt-here-1808.png)  

6. 디바이스에서 설치 파일 **CompanyPortal.pkg**가 열기에 안전한지 검사합니다. 완료되면 설치 관리자를 열고 설치를 완료합니다.  

7. 설치 관리자가 완료되면 **실행 패드**로 이동하고 **회사 포털**을 엽니다.  

8. macOS 디바이스는 회사 포털 앱을 열 것인지 확인하라는 메시지를 표시합니다. **열기**를 클릭합니다.  

   > [!TIP]
   > 디바이스가 조직의 리소스에 액세스해도 안전한지 확인하기 위해 Intune에서 컴퓨터에 액세스해야 합니다. 컴퓨터에서 회사 포털 앱이 열리지 않는 경우 [Gatekeeper를 사용하지 않도록 설정](https://support.apple.com/HT202491)합니다. 그런 다음, 앱을 엽니다.

9. 회사 포털 앱에 표시되는 첫 번째 화면은 **로그인**을 묻는 메시지를 표시합니다. 회사 포털 웹 사이트에 로그인하는 데 사용한 동일한 회사 또는 학교 계정을 사용합니다.

10. 회사 포털에서 사용자의 계정 정보를 확인하고, **디바이스 등록** 및 **디바이스 준수** 상태를 표시합니다. 노란색 삼각형은 학교 또는 회사의 macOS 디바이스를 보호하기 위해 수행해야 하는 작업을 강조 표시합니다. **시작**을 클릭하여 등록을 시작합니다. 

11. 메시지가 표시되면 컴퓨터의 로그인 정보를 입력합니다.  

관리에서 디바이스를 등록하는 데 몇 분 정도 걸릴 수 있습니다. 그 동안 디바이스에서 다른 작업을 수행할 수 있습니다. 회사 액세스 설정이 완료되면 알려드리겠다는 메시지를 받게 됩니다.  

## <a name="unverified-profiles"></a>확인되지 않은 프로필
macOS 디바이스에 설치된 MDM(모바일 디바이스 관리) 프로필을 보면 일부 프로필의 상태가 **확인되지 않음**으로 표시될 수 있습니다. **관리 프로필**에 **확인됨** 상태가 표시되는 한, 염려할 필요가 없습니다.  

관리 프로필은 MDM 채널 연결을 정의합니다. 관리 프로필이 확인되는 한, 채널을 통해 머신에 전달되는 다른 프로필은 관리 프로필의 보안 특성을 상속합니다.

또한 다른 프로필은 개별 확인이 필요하지 않기 때문에 더 빠르게 생성되어 디바이스에 전달됩니다. 

## <a name="updating-the-company-portal-app"></a>회사 포털 앱 사용

회사 포털 앱 업데이트는 Mac 용 Microsoft 자동 업데이트를 통해 다른 Office 앱과 동일한 방식으로 수행됩니다. [MacOS용 Microsoft 앱 업데이트에 대한 자세한 내용은 여기](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1)를 참조하세요.  

## <a name="next-steps"></a>다음 단계  
추가 도움이 필요하세요? 회사 지원팀과 확인하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에서 찾을 수 있습니다.  


