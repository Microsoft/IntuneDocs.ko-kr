---
title: 회사 리소스에 대한 액세스 설정 | Microsoft Docs
description: iOS 장치를 Intune에서 관리하게 하는 방법을 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
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
ms.openlocfilehash: c29c01169483b408528db71b1e9bb2b718220ddc
ms.sourcegitcommit: 7f46e9990797bdfa669ccba2077721f1bc70c07e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/04/2018
ms.locfileid: "30755252"
---
# <a name="set-up-access-to-your-company-resources"></a>회사 리소스에 대한 액세스 설정

회사에는 메일부터 파일, 네트워크 등에 이르는 많은 기밀 정보가 있습니다. 회사에서는 iOS 장치에서 해당 정보에 액세스할 때 정보를 보호할 수 있도록 Microsoft Intune을 사용하고 있습니다. 이렇게 하면 회사에서 리소스를 관리하고, 보안을 강화하고, 선호하는 장치를 자유롭게 사용하여 작업을 완료할 수 있습니다.

> [!NOTE]
> 메일 앱에서 회사 메일에 액세스하려는 경우 장치를 관리하여 안전하게 유지하라는 메시지가 표시될 수 있습니다. 아래 지침에 따라 iOS 장치에서 메일 및 기타 회사 리소스에 대한 액세스 권한을 얻습니다.

## <a name="before-you-start"></a>시작하기 전에

- 시작한 후 전체 프로세스가 완료되었는지 확인합니다. 몇 분 이상 일시 중지되면 일반적으로 진행이 중지되며 다시 시작해야 합니다.
- 이 프로세스가 실패하면 회사 포털 앱으로 돌아가 다시 시도해야 합니다.
- Wi-Fi가 작동 중이고 Safari가 장치에서 작동하는지 확인합니다.
- [Intune 회사 포털 앱](install-and-sign-in-to-the-intune-company-portal-app-ios.md)을 다운로드고 설치합니다.


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>회사 포털 앱을 사용하여 회사 리소스에 대한 액세스 권한 설정

|표시되는 내용|설명|
|---|---|
|![아래쪽에 “로그인” 단추가 있는 회사 포털 로그인 화면.](./media/ios-01-cp-enroll-1802.png)|회사 포털 앱을 열고 **로그인**을 탭합니다.|
|![Azure AD 로그인 프롬프트.](./media/ios-02-cp-enroll-1802.png)|회사 메일 주소를 입력하고 **다음**을 탭합니다.|
|![Azure AD 암호 프롬프트.](./media/ios-03-cp-enroll-1802.png)|암호를 입력하고 **로그인**을 탭합니다.|
|![회사 리소스 스플래시 로드 중 화면.](./media/ios-04-cp-enroll-1802.png)|로드될 때까지 기다립니다.|
|![사용 약관 페이지.](./media/ios-05-cp-enroll-1802.png)|사용 약관을 읽고 **모두 동의**합니다.|
|![회사 액세스 설정 화면. 관리 및 설정이 모두 해결되어야 함.](./media/ios-06-cp-enroll-1802.png)|**시작**을 탭하여 장치에서 회사 리소스에 액세스할 수 있게 설정하는 프로세스를 시작합니다. 지금 이 작업을 할 수 없는 경우에는 프로세스를 **연기**할 수 있지만 메일, 문서 등을 가져올 수 없게 됩니다.|
|![회사에서 볼 수 있는 정보 화면.](./media/ios-07-cp-enroll-1802.png)|아래쪽에서 링크를 탭하면 회사에서 볼 수 있는 정보에 대해 **자세히 알아볼 수 있습니다**. 그렇지 않은 경우에는 **계속**을 탭 합니다.|
|![다음 단계 화면.](./media/ios-08-cp-enroll-1802.png)|이 화면에서는 설정 시 수행되는 작업을 살펴봅니다. Safari, 설정 앱 및 회사 포털 앱에서 이 프로세스를 완료하는 데는 시간이 걸립니다. **계속**을 탭합니다.|
|![다음 단계에서 [다음]을 탭한 후 로딩 화면.](./media/ios-09-cp-enroll-1802.png)|로드될 때까지 기다립니다.|
|![등록을 위해 Safari로 전환됨.](./media/ios-7-cp-enroll-1711.png)|장치에 대한 관리 정보를 확인하도록 Safari로 이동됩니다.|
|![설정 앱을 열도록 요청하는 시스템 프롬프트.](./media/ios-8-cp-enroll-1711.png)|**허용**을 탭하여 설정 앱을 열고 구성 프로필을 다운로드합니다. 이 프로필을 설치하면 회사에서 장치에 대한 회사 정보를 관리할 수 있습니다.|
|![설정에서 열린 프로필.](./media/ios-9-cp-enroll-1711.png)|**설치**를 탭합니다.|
|![화면 아래쪽에서 프로필 모달 대화 상자 설치.](./media/ios-10-cp-enroll-1711.png)|**설치**를 탭합니다.|
|![프로필 설치 중 로딩 화면.](./media/ios-11-cp-enroll-1711.png)|로드될 때까지 기다립니다.|
|![프로필 관리 경고 화면.](./media/ios-12-cp-enroll-1711.png)|Apple에서 작성한 이 경고를 통해 관리 중인 장치에서 수행할 수 있는 작업 유형에 대해 자세히 알 수 있습니다. [회사에서 볼 수 있는 정보](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)에 대해 자세히 알아봅니다.|
|![원격 관리의 신뢰 정보를 요청하는 시스템 프롬프트.](./media/ios-13-cp-enroll-1711.png)|**신뢰**를 탭하여 장치에서 회사 정보 및 설정을 관리할 수 있습니다.|
|![프로필 설치 완료 로드 화면.](./media/ios-14-cp-enroll-1711.png)|로드될 때까지 기다립니다.|
|![프로필 설치됨 화면.](./media/ios-15-cp-enroll-1711.png)|프로필이 설치되고 장치의 회사 정보와 설정이 훨씬 더 관리되는 상태에 가까워집니다.|
|![등록을 위해 Safari로 전환됨.](./media/ios-16-cp-enroll-1711.png)|장치에 대한 관리 정보 확인을 완료하도록 Safari로 이동됩니다. |
|![회사 포털을 열기 위한 시스템 프롬프트.](./media/ios-17-cp-enroll-1711.png)|**열기**를 탭합니다.|
|![회사 리소스 로드 중 화면.](./media/ios-21-cp-enroll-1802.png)|로드될 때까지 기다립니다.|
|![회사 포털 앱에서 장치 범주를 선택합니다.](./media/ios-22-cp-enroll-1802.png)|장치에 가장 적합한 범주를 선택합니다. 이는 일반적으로 장치를 소유한 사람과 함께 또는 장치가 대부분 사용되는 위치에서 작업해야 합니다.|
|![범주 선택됨.](./media/ios-23-cp-enroll-1802.png)||
|![장치 관리 성공, 이제 설정을 업데이트해야 함.](./media/ios-24-cp-enroll-1802.png)|장치가 성공적으로 관리됩니다. 회사에서 업데이트 시 요구할 수 있는 암호 길이 등의 다른 설정이 있을 수 있습니다. 계속하려면 **계속**을 탭합니다.|
|![장치 설정 확인.](./media/ios-25-cp-enroll-1802.png)|회사 포털에서 설정을 업데이트해야 하는지 여부를 확인합니다.|
|![설정 확인 완료됨, 잘못된 OS 버전 포함](./media/ios-26-cp-enroll-1802.png)|회사 포털에서 설정 문제를 해결하는 방법에 대한 지침을 제공합니다. 문제 해결을 완료하면 **설정 확인**을 탭합니다.|
|![장치 설정 확인 로딩 화면](./media/ios-27-cp-enroll-1802.png)|장치에서 설정이 회사 리소스에 액세스할 만큼 안전한지 확인합니다.|
|![설정을 성공적으로 등록 및 업데이트함](./media/ios-28-cp-enroll-1802.png)|축하합니다. 이제 장치가 Intune에 등록됩니다.|

> [!Note]
> 장치가 완전히 관리되기까지 몇 단계가 더 남아 있을 수 있습니다. [Telecom Expense Management를 사용하는 장치 등록](enroll-your-device-with-telecom-expense-management-ios.md)에 대해 자세히 알아보세요. 조직에서 Apple의 장비 등록 프로그램을 사용하는 경우 [여기](enroll-your-device-dep-ios.md)를 참조하세요.

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com#HelpDeskDialog)를 참조하세요.
