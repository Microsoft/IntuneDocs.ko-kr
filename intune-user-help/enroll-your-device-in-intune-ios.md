---
title: 회사 리소스에 대한 iOS 장치 액세스 설정 | Microsoft Docs
description: iOS 장치를 Intune에서 관리하게 하는 방법을 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 50fc19410b280e984c8dc3abe620baad7c3267de
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959539"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>회사 리소스에 대한 iOS 장치 액세스 설정

Intune 회사 포털 앱으로 iOS 장치를 등록하여 조직의 이메일, 파일 및 앱에 대한 보안 액세스 권한을 얻습니다.

회사 또는 개인 장치에서 독점 데이터에 액세스하려면 먼저 장치가 관리되도록 해야 합니다. 장치가 관리된 후 조직은 MDM(모바일 장치 관리) 공급자를 통해 장치에 정책 및 앱을 할당합니다. 

장치에서 회사 또는 학교 정보에 대한 액세스를 유지 관리하려면 조직의 기본 설정과 일치하도록 장치를 구성해야 합니다. 이 문서에서는 회사 포털에서 이러한 요구 사항에 맞게 장치를 등록, 구성 및 유지 관리할 수 있는 방법을 설명합니다.

> [!NOTE]
> Mail 앱에서 회사 메일에 액세스하려고 하는데 장치를 관리할지 묻는 메시지가 표시되면 적절한 위치에 있는 것입니다. 아래 지침에 따라 iOS 장치에서 메일 및 기타 회사 리소스에 대한 액세스 권한을 얻습니다.

## <a name="what-to-expect-from-the-company-portal-app"></a>회사 포털 앱에서 예상되는 상황

### <a name="security"></a>보안
초기 설정 중 앱에서는 조직에 사용자를 인증하도록 요구합니다. 그런 다음, 업데이트해야 하는 장치 설정을 알려줍니다. 예를 들어 조직은 종종 사용자가 충족해야 하는 최소 또는 최대 문자 암호 요구 사항을 설정합니다.    

### <a name="protection"></a>보호
장치가 등록된 후 회사 포털 앱은 장치가 보호되는지 계속해서 확인합니다. 예를 들어 신뢰할 수 없는 소스에서 앱을 설치하는 경우 앱은 사용자에게 경고하고 경우에 따라 회사 데이터에 대한 액세스를 취소합니다. 이와 같은 앱 보호 정책은 조직에서 흔하게 사용됩니다. 종종 사용자가 액세스 권한을 다시 얻기 위해 먼저 신뢰할 수 없는 앱을 제거해야 합니다.

### <a name="setting-notifications"></a>알림 설정
등록 후 조직이 다단계 인증과 같은 새 보안 요구 사항을 적용하는 경우 회사 포털 앱은 이를 알려줍니다. 장치에서 작업을 계속할 수 있도록 설정을 조정할 수 있습니다.  

등록에 대해 자세히 알아보려면 [회사 포털 앱을 설치하고 장치를 등록하면 어떤 일이 생기나요?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)를 참조하세요. 

## <a name="before-you-start"></a>시작하기 전에

- 등록을 시작하면 전체 프로세스가 완료되었는지 확인합니다. 몇 분 동안 일시 중지하면 설치가 종료되고 다시 시작해야 할 수 있습니다.  
- 이 프로세스가 실패하면 회사 포털 앱으로 돌아가서 다시 시도합니다.  
- Wi-Fi가 작동 중이고 Safari가 장치에서 작동하는지 확인합니다.
- [Intune 회사 포털 앱](install-and-sign-in-to-the-intune-company-portal-app-ios.md)을 다운로드고 설치합니다.  


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>회사 포털 앱을 사용하여 회사 리소스에 대한 액세스 권한 설정

|표시되는 내용|설명|
|---|---|
|![아래쪽에 “로그인” 단추가 있는 회사 포털 로그인 화면](./media/ios-01-cp-enroll-1802.PNG)|회사 포털 앱을 열고 **로그인**을 탭합니다.|
|![Azure AD 로그인 프롬프트](./media/ios-02-cp-enroll-1802.PNG)|회사 메일 주소를 입력하고 **다음**을 탭합니다.|
|![Azure AD 암호 프롬프트.](./media/ios-03-cp-enroll-1802.PNG)|암호를 입력하고 **로그인**을 탭합니다.|
|![회사 리소스 스플래시 로드 중 화면.](./media/ios-04-cp-enroll-1802.PNG)|이 화면이 로드될 때까지 기다립니다.|
|![사용 약관 페이지.](./media/ios-05-cp-enroll-1802.PNG)|사용 약관을 읽고 **모두 동의**합니다.|
|![회사 액세스 설정 화면. 관리 및 설정이 모두 해결되어야 함.](./media/ios-06-cp-enroll-1802.PNG)|**시작**을 탭하여 장치에서 회사 리소스에 액세스할 수 있게 설정하는 프로세스를 시작합니다. 지금 이 작업을 할 수 없는 경우에는 프로세스를 **연기**할 수 있지만 메일, 문서 등을 가져올 수 없게 됩니다.|
|![회사에서 볼 수 있는 정보 화면.](./media/ios-07-cp-enroll-1802.PNG)|아래쪽에서 링크를 탭하면 회사에서 볼 수 있는 정보에 대해 **자세히 알아볼 수 있습니다**. 그렇지 않은 경우에는 **계속**을 탭 합니다.|
|![다음 단계 화면.](./media/ios-08-cp-enroll-1802.PNG)|이 화면에서는 설정 시 수행되는 작업을 살펴봅니다. Safari, 설정 앱 및 회사 포털 앱에서 작업하는 데 시간이 걸립니다. **계속**을 탭합니다.|
|![다음 단계에서 [다음]을 탭한 후 로딩 화면.](./media/ios-09-cp-enroll-1802.PNG)|이 화면이 로드될 때까지 기다립니다.|
|![등록을 위해 Safari로 전환됨.](./media/ios-cp-sent-to-safari-1808.png)|장치에 대한 관리 정보를 확인하도록 Safari로 이동됩니다.|
|![설정 앱을 열도록 요청하는 시스템 프롬프트.](./media/ios-8-cp-enroll-1711.PNG)|**허용**을 탭하여 설정 앱을 열고 구성 프로필을 다운로드합니다. 이 프로필을 설치하면 회사에서 장치에 대한 회사 정보를 관리할 수 있습니다.|
|![장치 설정에 있는 프로필 설치 화면의 스크린샷입니다.](./media/ios-9-cp-enroll-1711.PNG)|**설치**를 탭합니다.|
|![화면 아래쪽에서 프로필 모달 대화 상자 설치.](./media/ios-10-cp-enroll-1711.PNG)|**설치**를 탭합니다.|
|![프로필 설치 중 로딩 화면.](./media/ios-11-cp-enroll-1711.PNG)|이 화면이 로드될 때까지 기다립니다.|
|![프로필 관리 경고 화면.](./media/ios-12-cp-enroll-1711.PNG)|Apple에서 작성한 이 경고를 통해 관리 중인 장치에서 수행할 수 있는 작업 유형에 대해 자세히 알 수 있습니다. [회사에서 볼 수 있는 정보](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)에 대해 자세히 알아봅니다.|
|![원격 관리의 신뢰 정보를 요청하는 시스템 프롬프트.](./media/ios-13-cp-enroll-1711.PNG)|**신뢰**를 탭하여 장치에서 회사 정보 및 설정을 관리할 수 있습니다.|
|![프로필 설치 완료 로드 화면.](./media/ios-14-cp-enroll-1711.PNG)|이 화면이 로드될 때까지 기다립니다.|
|![프로필 설치됨 화면.](./media/ios-15-cp-enroll-1711.PNG)|프로필이 설치되고 장치의 회사 정보와 설정이 훨씬 더 관리되는 상태에 가까워집니다.|
|![등록을 위해 Safari로 전환됨.](./media/ios-16-cp-enroll-1711.PNG)|장치에 대한 관리 정보 확인을 완료하도록 Safari로 이동됩니다. |
|![회사 포털을 열기 위한 시스템 프롬프트.](./media/ios-17-cp-enroll-1711.PNG)|**열기**를 탭합니다.|
|![회사 리소스 로드 중 화면.](./media/ios-21-cp-enroll-1802.PNG)|이 화면이 로드될 때까지 기다립니다.|
|![회사 포털 앱에서 장치 범주를 선택합니다.](./media/ios-22-cp-enroll-1802.PNG)|장치에 가장 적합한 범주를 선택합니다. 이는 일반적으로 장치를 소유한 사람과 함께 또는 장치가 대부분 사용되는 위치에서 작업해야 합니다.|
|![범주 선택됨.](./media/ios-23-cp-enroll-1802.PNG)||
|![장치 관리 성공, 이제 설정을 업데이트해야 함.](./media/ios-24-cp-enroll-1802.PNG)|장치가 성공적으로 관리됩니다. 회사에서 업데이트 시 요구할 수 있는 암호 길이 등의 다른 설정이 있을 수 있습니다. 계속하려면 **계속**을 탭합니다.|
|![장치 설정 확인.](./media/ios-25-cp-enroll-1802.PNG)|회사 포털에서 설정을 업데이트해야 하는지 여부를 확인합니다.|
|![설정 확인 완료됨, 잘못된 OS 버전 포함](./media/ios-26-cp-enroll-1802.PNG)|회사 포털에서 설정 문제를 해결하는 방법에 대한 지침을 제공합니다. 문제 해결을 완료하면 **설정 확인**을 탭합니다.|
|![장치 설정 확인 로딩 화면](./media/ios-27-cp-enroll-1802.PNG)|장치에서 설정이 회사 리소스에 액세스할 만큼 안전한지 확인합니다.|
|![설정을 성공적으로 등록 및 업데이트함](./media/ios-28-cp-enroll-1802.PNG)|축하합니다. 이제 장치가 Intune에 등록됩니다.|

> [!Note]
> 장치가 완전히 관리되기까지 몇 단계가 더 남아 있을 수 있습니다. [Telecom Expense Management를 사용하는 장치 등록](enroll-your-device-with-telecom-expense-management-ios.md)에 대해 자세히 알아보세요. 조직에서 Apple의 장비 등록 프로그램을 사용하는 경우 [여기](enroll-your-device-dep-ios.md)를 참조하세요.

여전히 도움이 필요하세요? 회사 지원팀과 확인하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에서 찾을 수 있습니다.  
