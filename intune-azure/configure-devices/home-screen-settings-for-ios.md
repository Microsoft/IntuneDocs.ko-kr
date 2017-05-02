---
title: "iOS 장치용 Intune 홈 화면 레이아웃 설정"
titleSuffix: Intune Azure preview
description: "Intune Azure 미리 보기: iOS 장치에서 홈 화면과 도킹을 사용자 지정하는 데 사용할 수 있는 설정을 알아봅니다."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 4/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6aba4491-afb9-43cd-9ccc-14e6a2a5a3b1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 72bfde93389a060ed52062be0f2692b8bc35543a
ms.lasthandoff: 04/19/2017


---

# <a name="intune-home-screen-layout-settings-for-ios-devices"></a>iOS 장치용 Intune 홈 화면 레이아웃 설정

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

이 설정을 사용하여 정책을 할당할 모든 iOS 장치에 대해 도킹 및 홈 화면에서 앱, 폴더 및 웹 클립의 레이아웃을 구성합니다.

프로필을 할당하는 iOS 장치는 감독 모드여야 하며, iOS 9.3 이상을 실행 중이어야 합니다.

1. **장치 기능** 블레이드에서 **홈 화면 레이아웃(감독 모드인 경우에만)**을 선택합니다.
2. **홈 화면 레이아웃(감독 모드인 경우에만)** 블레이드에서 **도킹** 또는 **페이지** 레이아웃을 구성할지 여부를 선택합니다.

## <a name="add-items-to-the-dock"></a>도킹에 항목 추가

**도킹** 블레이드에서 iOS 화면 아래쪽에 있는 도킹에 최대 6개의 항목 또는 폴더를 추가할 수 있습니다. 그러나 여러 장치에서 이보다 적은 항목을 지원합니다. 예를 들어 iPhone 장치는 최대 4개까지 지원합니다. 이 경우 구성한 처음 4개 항목만 장치에 표시됩니다.

1. **추가**를 선택하여 도킹에 항목을 추가합니다.
2. **행 추가** 블레이드에서 **앱**을 추가할지, **폴더**를 추가할지 선택합니다.
3. 이 항목의 **목록에 앱을 추가하는 방법** 및 **목록에 폴더를 추가하는 방법** 섹션을 사용하여 도킹에 표시할 앱과 폴더를 구성합니다.
4. 항목을 계속 추가합니다. 작업이 완료되면 각 블레이드에서 **확인**을 클릭하여 **프로필 만들기** 블레이드로 돌아갑니다. **만들기**를 선택합니다.

>[!TIP]
> 항목을 홈 화면과 페이지 목록에 끌어서 놓고, 항목을 다시 정렬할 수도 있습니다. 

### <a name="example"></a>예

이 예제에서는 Safari, Mail 및 Stocks 앱만 표시되도록 도킹 화면을 구성했습니다. 다음 이미지에서 속성을 설명하기 위해 Mail 앱이 선택되었습니다.

![샘플 iOS 도킹 설정](http://i.imgur.com/FfFiUcP.png)

IPhone에 정책을 할당할 때 결과는 다음과 유사한 도킹이 됩니다.

![iPhone의 샘플 iOS 레이아웃 도킹](http://i.imgur.com/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>홈 화면 페이지 추가

홈 화면에 표시할 페이지와 각 페이지에 표시할 앱을 추가합니다. 페이지에 추가되는 앱은 목록에 지정되는 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 페이지에 맞출 수 있는 수보다 많은 앱을 추가할 경우 앱은 후속 페이지로 이동합니다.


1. **페이지** 블레이드에서 **추가**를 선택합니다.
2. **행 추가** 블레이드에서 **페이지 이름**을 입력합니다. 이 이름은 Intune 포털에서 참조용으로 사용되며, iOS 장치에서는 *표시되지 않습니다*.
3. **추가**를 선택한 다음 페이지에 **앱**을 추가할지, **폴더**를 추가할지 선택합니다.
4. 이 항목의 **목록에 앱을 추가하는 방법** 및 **목록에 폴더를 추가하는 방법** 섹션을 사용하여 페이지에 표시할 앱과 폴더를 구성합니다.

### <a name="example"></a>예

이 예제에서는 **Contoso**라는 새 페이지를 구성했습니다. 페이지에는 친구 찾기와 설정 앱만 표시됩니다. 다음 이미지에서 속성을 설명하기 위해 설정 앱이 선택되었습니다.

![iOS 홈 화면 설정 예제](http://i.imgur.com/Jc2OxyX.png)

IPhone에 정책을 할당할 때 결과는 다음과 유사한 페이지가 됩니다.

![수정된 홈 화면을 사용하는 iOS 장치](http://i.imgur.com/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>목록에 앱을 추가하는 방법

1. **앱 이름**을 입력합니다. 이 이름은 Intune 포털에서 참조용으로 사용되며, iOS 장치에서는 *표시되지 않습니다*.
2. 표시할 앱의 **앱 번들 ID**를 입력합니다. 도움말은 이 항목의 **기본 제공 iOS 앱에 대한 번들 ID 참조**를 참조하세요.
3. **확인**을 클릭하고, 항목을 계속 추가합니다. 장치 도킹의 경우는 최대 **6**개, 디바이스 페이지의 경우는 최대 **60**개입니다.
4. 작업을 마쳤으면 **확인**을 클릭합니다.

## <a name="how-to-add-a-folder-to-the-list"></a>목록에 폴더를 추가하는 방법

폴더에서 페이지에 추가되는 앱은 목록에 지정되는 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 페이지에 맞출 수 있는 수보다 많은 앱을 추가할 경우 앱은 후속 페이지로 이동합니다.

1. **폴더 이름**을 입력합니다. 이 이름은 해당 장치 사용자에게 표시됩니다.
2. **추가**를 선택하여 폴더 페이지를 만듭니다. 최대 20개의 페이지를 추가할 수 있습니다.
3. **행 추가** 블레이드에서 페이지에 대한 이름을 입력합니다. 이 이름은 Intune 포털에서 참조용으로 사용되며, iOS 장치에서는 *표시되지 않습니다*.
3. **앱 이름**을 입력합니다. 이 이름은 Intune 포털에서 참조용으로 사용되며, iOS 장치에서는 *표시되지 않습니다*.
2. 표시할 앱의 **앱 번들 ID**를 입력합니다. 도움말은 **목록에 앱을 추가하는 방법**을 참조하세요.
3. **추가**를 선택합니다. 최대 60개 항목을 추가할 수 있습니다.
4. 작업을 마쳤으면 **확인**을 클릭합니다.


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>기본 제공 iOS 앱에 대한 번들 ID 참조

이 목록에서는 몇 가지 일반적인 기본 제공 iOS 앱의 번들 ID를 보여줍니다. 다른 앱의 번들 ID를 찾으려면 소프트웨어 공급업체에 문의하세요. 

|||
|-|-|
|앱 이름|BundleID|
|앱 스토어|com.apple.AppStore|
|계산기|com.apple.calculator|
|일정|com.apple.mobilecal|
|카메라|com.apple.camera|
|시계|com.apple.mobiletimer|
|나침반|com.apple.compass|
|연락처|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|친구 찾기|com.apple.mobileme.fmf1|
|나의 iPhone 찾기|com.apple.mobileme.fmip1|
|게임 센터|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|상태|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|키노트|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|맵|com.apple.Maps|
|메시지|com.apple.MobileSMS|
|음악|com.apple.Music|
|뉴스|com.apple.news|
|참고|com.apple.mobilenotes|
|숫자|com.apple.Numbers|
|페이지|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|사진|com.apple.mobileslideshow|
|Podcasts|com.apple.podcasts|
|미리 알림|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|설정|com.apple.Preferences|
|주식|com.apple.stocks|
|팁|com.apple.tips|
|동영상|com.apple.videos|
|음성 메모|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|보기|com.apple.Bridge|
|날씨|com.apple.weather|

