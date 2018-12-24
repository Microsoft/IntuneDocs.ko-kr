---
title: iOS를 실행하는 디바이스에 대해 Microsoft Intune 홈 화면 레이아웃 설정
titleSuffix: ''
description: iOS를 실행하는 디바이스에서 홈 화면과 Dock를 사용자 지정하는 데 사용할 수 있는 Microsoft Intune의 설정에 대해 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 65ecff2a21fa814c3b3518eb92e0378301dbd606
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189323"
---
# <a name="microsoft-intune-home-screen-layout-settings-for-devices-running-ios"></a>iOS를 실행하는 디바이스에 대해 Microsoft Intune 홈 화면 레이아웃 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이러한 설정을 사용하여 iOS를 실행하는 디바이스의 도킹 및 홈 화면에서 폴더의 레이아웃을 구성합니다.

할당된 프로필을 사용해 iOS를 실행하는 디바이스는 감독 모드여야 하며, iOS 9.3 이상을 실행해야 합니다.

1. [Azure Portal의 Intune](https://portal.azure.com)에서 [**장치 구성 영역의 장치 기능**으로 이동합니다](device-features-configure.md).
2. **장치 기능** 창에서 **홈 화면 레이아웃(감독 모드인 경우에만)** 을 선택합니다.
3. **홈 화면 레이아웃(감독 모드인 경우에만)** 창에서 **Dock** 또는 **페이지** 레이아웃을 구성할지 여부를 선택합니다.

## <a name="add-items-to-the-dock"></a>Dock에 항목 추가

**Dock** 창에서 iOS 화면 Dock에 최대 6개의 항목 또는 폴더를 추가할 수 있습니다. 그러나 이보다 적은 항목을 지원하는 디바이스가 많습니다. 예를 들어 iPhone 디바이스는 최대 4개의 항목을 지원합니다. 이 경우 구성한 처음 4개 항목만 디바이스에 표시됩니다.

1. **추가**를 선택하여 Dock에 항목을 추가합니다.
2. **행 추가** 창에서 **앱**을 추가할지, **폴더**를 추가할지 선택합니다.
3. 이 항목의 정보를 참조하여 Dock에 표시할 앱 및 폴더를 구성합니다.
4. 항목을 계속 추가합니다. 작업이 완료되면 각 창에서 **확인**을 클릭하여 **프로필 만들기** 창으로 돌아갑니다. **만들기**를 선택합니다.

>[!TIP]
> 항목을 홈 화면과 페이지 목록에 끌어서 놓고, 항목을 다시 정렬할 수도 있습니다.

### <a name="example"></a>예제

이 예제에서는 Safari, Mail 및 Stocks 앱만 표시되도록 Dock 화면을 구성했습니다. 다음 이미지에서 속성을 설명하기 위해 Mail 앱이 선택되었습니다.

![샘플 iOS Dock 설정](./media/FfFiUcP.png)

iPhone에 정책을 할당할 때 결과는 다음 스크린샷과 유사한 Dock이 됩니다.

![iPhone의 샘플 iOS 레이아웃 Dock](./media/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>홈 화면 페이지 추가

홈 화면에 표시할 페이지와 각 페이지에 표시할 앱을 추가합니다. 페이지에 추가되는 앱은 목록에 지정되는 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 한 페이지에 들어가는 개수보다 많은 앱을 추가할 경우 앱이 후속 페이지로 이동합니다.

1. **페이지** 창에서 **추가**를 선택합니다.
2. **행 추가** 창에서 **페이지 이름**을 입력합니다. 이 이름은 Azure Portal에서 참조용으로 사용되며, iOS 디바이스에는 *표시되지 않습니다*.
3. **추가**를 선택한 다음 페이지에 **앱**을 추가할지, **폴더**를 추가할지 선택합니다.
4. 이 항목의 정보를 참조하여 페이지에 표시할 앱 및 폴더를 구성합니다.

### <a name="example"></a>예제

이 예제에서는 **Contoso**라는 새 페이지를 구성했습니다. 페이지에는 친구 찾기와 설정 앱만 표시됩니다. 다음 이미지에서 속성을 설명하기 위해 설정 앱이 선택되었습니다.

![iOS 홈 화면 설정 예제](./media/Jc2OxyX.png)

iPhone에 정책을 할당할 때 결과는 다음 스크린샷과 유사한 페이지가 됩니다.

![수정된 홈 화면을 사용하는 iOS 디바이스](./media/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>목록에 앱을 추가하는 방법

1. **앱 이름**을 입력합니다. 이 이름은 Azure Portal에서 참조용으로 사용되며, iOS 디바이스에는 *표시되지 않습니다*.
2. 표시할 앱의 **앱 번들 ID**를 입력합니다. 도움말은 이 항목의 **기본 제공 iOS 앱에 대한 번들 ID 참조**를 참조하세요.
3. **확인**을 클릭하고, 항목을 계속 추가합니다. 장치 Dock의 경우는 최대 **6**개, 디바이스 페이지의 경우는 최대 **60**개입니다.
4. 작업을 마쳤으면 **확인**을 클릭합니다.

## <a name="how-to-add-a-folder-to-the-list"></a>목록에 폴더를 추가하는 방법

폴더에서 페이지에 추가되는 앱은 목록에 지정되는 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 한 페이지에 들어가는 개수보다 많은 앱을 추가할 경우 앱이 후속 페이지로 이동합니다.

1. **폴더 이름**을 입력합니다. 이 이름은 해당 디바이스에서 사용자에게 표시됩니다.
2. **추가**를 선택하여 폴더 페이지를 만듭니다. 최대 20개의 페이지를 추가할 수 있습니다.
3. **행 추가** 창에서 페이지에 대한 이름을 입력합니다. 이 이름은 Azure Portal에서 참조용으로 사용되며, iOS 디바이스에는 *표시되지 않습니다*.
3. **앱 이름**을 입력합니다. 이 이름은 Azure Portal에서 참조용으로 사용되며, iOS 디바이스에는 *표시되지 않습니다*.
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


## <a name="next-steps"></a>다음 단계

이제 선택한 그룹에 디바이스 프로필을 할당할 수 있습니다. 자세한 내용은 [디바이스 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.
