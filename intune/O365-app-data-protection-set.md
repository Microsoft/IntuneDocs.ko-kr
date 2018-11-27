---
title: Microsoft Intune에서 Office 365 앱의 데이터 관리
titlesuffix: ''
description: Microsoft Intune에서 Office 365 앱의 데이터 관리에 대해 자세히 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a3eed03deb3f619f75502e8a9d1d66fefc38a081
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180074"
---
# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps-in-microsoft-intune"></a>Microsoft Intune에서 사용자가 관리되는 Office 365 앱에 대한 기본 보호 환경을 사용하는 방법

**Office 365 관리 앱** 마법사는 각 장치 플랫폼에 대한 앱 보호 정책을 만듭니다.

이 마법사는 다음 정책을 설정합니다.

**iOS**
* 앱 데이터 암호화

**OWA(Outlook Web Access)**
* 앱 데이터 암호화
* 액세스용 단순 PIN 필요

이러한 정책은 필요할 때 Office 앱에서 작업 데이터를 초기화할 수 있는 기능을 제공하여 Office 365 앱을 관리할 수 있도록 해줍니다. 또한 작업 데이터를 암호화하고 PIN을 입력해야 Office 365 앱에서 데이터를 볼 수 있도록 함으로써 장치가 분실되거나 도난된 경우 기본 보호를 보장합니다.


이 문서에서는 비즈니스용 OneDrive를 예제로 사용하여 Intune에서 관리되는 응용 프로그램의 사용자 환경을 보여 줍니다.


>[!NOTE]
>개인 장치에서는 일반적으로 최종 사용자가 앱을 다운로드합니다. 장치가 MDM(모바일 장치 관리) 솔루션에서 관리되는 경우 장치에 앱을 배포할 수 있습니다.

## <a name="user-experience-on-an-ios-device"></a>iOS 장치의 사용자 환경

1. 비즈니스용 OneDrive 앱을 시작하여 로그인 페이지를 엽니다.  
2. 회사 계정 사용자 이름을 입력합니다. 회사 자격 증명을 입력할 수 있도록 Office 365 인증 페이지로 리디렉션됩니다. 
3. Azure Active Directory에서 자격 증명이 인증되면 앱 보호 정책이 적용되며, 비즈니스용 OneDrive 앱을 다시 시작하라는 메시지가 표시됩니다. 

   > [!NOTE]
   > Intune에서 등록되지 않은 장치에서만 다시 시작 필요 메시지가 표시됩니다.

4. 비즈니스용 OneDrive 앱을 다시 시작합니다. 설정된 앱 보호 정책으로 앱이 시작되고 장치의 PIN을 설정하라는 메시지가 표시됩니다(장치의 PIN을 아직 구성하지 않은 경우).  

   > [!NOTE]
   > 대부분의 사용자에게는 이 메시지가 표시되지 않습니다. iOS 장치에서 PIN을 사용하도록 설정하지 않은 사용자에게만 이 메시지가 표시됩니다.

5. PIN을 설정하고 확인했으면 비즈니스용 OneDrive 앱으로 돌아갑니다. 이제 IT 관리자가 OneDrive에서 작업 데이터를 보호함을 알리는 일회성 알림이 표시됩니다. 
6. 이 알림을 클릭하면 비즈니스용 OneDrive에서 파일에 액세스할 수 있습니다. 

>[!NOTE]
>배포된 정책을 변경하는 경우 다음에 앱을 열 때 변경 내용이 적용됩니다.

## <a name="user-experience-on-an-android-device"></a>Android 장치의 사용자 환경

1. 비즈니스용 OneDrive 앱을 시작하여 로그인 페이지를 엽니다.  <br/> ![OneDrive 앱 시작 화면 이미지](./media/onedrive-android-welcome.png)
2. 회사 계정 사용자 이름을 입력합니다. 회사 자격 증명을 입력할 수 있도록 Office 365 인증 페이지로 리디렉션됩니다. <br/> ![Android의 O365 로그인 이미지](./media/o365-sign-in-android.png)
3. Azure Active Directory에서 자격 증명이 인증되면 회사 포털 앱을 설치하는 지침이 포함된 메시지가 표시됩니다(아직 장치에 설치되지 않은 경우). **스토어로 이동**을 탭하여 계속 진행합니다. <br/> ![회사 포털 앱을 가져오는 메시지의 이미지](./media/get-company-portal-android.png) <br/>회사 포털 앱이 휴대폰에 이미 설치된 경우 비즈니스용 OneDrive 앱이 자동으로 시작되며 마지막 메모로 건너뛸 수 있습니다.   

   > [!IMPORTANT]
   > Android에서 앱 보호 정책을 통해 관리할 Office 앱을 설정한 후 장치 사용자는 실제로 메일이나 문서를 읽기 위해 앱을 열거나 로그인할 필요가 없지만 회사 포털 앱을 설치**해야** 회사 메일 및 문서에 액세스할 수 있습니다.

4. 이제 Google Play 스토어에 있으며, 회사 포털 앱을 다운로드하고 설치할 수 있습니다. 이 앱은 데이터를 안전하게 보호하는 데 도움이 됩니다. <br/> ![Google Play 스토어의 앱 이미지](./media/google-play-get-app-android.png)
5. 앱 설치를 완료한 후 **동의함**을 선택하여 약관에 동의합니다. 비즈니스용 OneDrive 앱이 자동으로 시작됩니다.


>[!NOTE]
>다음에 비즈니스용 OneDrive를 열면 PIN을 설정하라는 메시지가 나타날 수 있습니다(IT 관리자가 요구하는 경우). PIN을 설정하고 확인한 후 비즈니스용 OneDrive를 계속 사용할 수 있습니다.

![PIN에 대한 메시지의 이미지](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>이 마법사에서 설정하는 정책은 무엇입니까?

|     |       | |
|----|--------|-|
|**Name**|Office 365 앱 관리| |
| **설명**|Office 365 앱 관리 마법사에서 생성| |
| |  | |
| **설정 이름** |**iOS 정책 값** | **Android 정책 값** |
|iTunes 및 iCloud 백업 차단| 아니요 | 해당 없음 |
|Android 백업 차단 |해당 없음 | 아니요|
|앱이 다른 앱으로 데이터를 전송하도록 허용 | 모든 앱 | 모든 앱|
|앱이 다른 앱의 데이터를 받도록 허용| 모든 앱 | 모든 앱|
|"다른 이름으로 저장" 차단 | 아니요 | 아니요|
|다른 앱에서 잘라내기, 복사 및 붙여넣기 제한 | 모든 앱 | 모든 앱 |
|웹 콘텐츠가 회사에서 관리되는 브라우저에 표시되도록 제한 | 아니요| 아니요|
|앱 데이터 암호화 | 장치가 잠길 때 | 예|
|연락처 동기화 사용 안 함 | 아니요| 아니요|
|인쇄 사용 안 함 | 아니요 | 아니요|
|액세스 시 PIN 필요 | 아니요 | 예|
|PIN 다시 설정까지의 입력 시도 횟수 | 해당 없음 |5|
|단순한 PIN 허용 | 해당 없음 |예|
|PIN 길이 | 해당 없음 | 4|
|PIN 대신 지문 허용 | 해당 없음 | 예 |
|액세스 시 회사 자격 증명 필요 | 아니요 | 아니요|
|관리되는 앱이 무단 해제 또는 루팅된 장치를 실행하지 못하도록 차단 | 아니요 | 아니요|
|다음 시간(분) 후에 액세스 요구 사항 다시 확인 - 제한 시간 | 30 | 30|
|다음 시간(분) 후에 액세스 요구 사항 다시 확인 - 오프라인 유예 기간 | 720 |720|
|앱 데이터가 초기화되기 전의 오프라인 간격(일) | 90 | 90|
|화면 캡처 차단(Android 장치에만 해당) | 해당 없음 | 아니요 |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>앱 PIN 정책이 Android 장치에 대해서만 구성되는 이유는 무엇입니까?
암호화는 iOS와 Android에서 다르게 작동합니다.

iOS에서 Intune 앱 보호 정책과 연결된 앱의 경우 데이터는 운영 체제에서 제공하는 장치 수준 암호화를 통해 암호화된 상태로 보관됩니다. 따라서 앱 암호화 정책을 설정하는 경우 자동으로 사용자에게 작업 데이터에 액세스하려면 장치 PIN을 입력하도록 요구합니다. 장치에서 장치 PIN을 아직 구성하지 않은 사용자에게는 장치 PIN을 만들라는 메시지가 표시됩니다.

Android에서 Intune 앱 보호 정책과 연결된 앱의 경우 데이터는 파일 I/O 작업 동안 동기적으로 암호화됩니다. 장치 저장소의 콘텐츠는 항상 암호화됩니다. MDM에서 관리되지 않는 장치에서는 앱 보호 정책을 통해 장치 PIN 요구 사항을 강제할 수 없습니다. 사용자가 일부 PIN을 사용하여 회사 데이터에 액세스할 수 있도록 하기 위해 마법사에서는 앱 PIN 정책을 지원합니다.

언제든지 조직의 요구 사항에 맞게 이러한 정책 설정을 편집할 수 있습니다.

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>마법사에서 만든 정책을 보고 편집하려면 어떻게 해야 합니까?
이러한 정책 또는 Intune Azure Portal에서 만든 모든 정책을 보거나 업데이트하려면 대시보드에서 **앱 관리** > **앱 보호 정책**을 선택합니다. 정책 목록이 오른쪽에 열립니다. 설정을 보고 편집하기 위해 표시할 정책을 선택합니다. <br/>
![정책을 표시하는 사용자 인터페이스 경로 이미지](./media/image-for-faq.png)

## <a name="next-steps"></a>다음 단계
- [앱 보호 정책](app-protection-policy.md)에 대해 자세히 알아봅니다.
