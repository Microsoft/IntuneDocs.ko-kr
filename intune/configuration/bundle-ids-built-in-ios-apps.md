---
title: Microsoft Intune의 기본 제공 앱용 iOS/iPadOS 번들 ID - Azure | Microsoft Docs
titleSuffix: ''
description: 기본 제공 iOS 및 iPadOS 앱의 번들 ID 목록을 참조하세요. 이러한 번들 ID를 사용하여 Microsoft Intune의 디바이스 구성 프로필 및 정책에서 앱을 명시적으로 허용합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10c6ea8e3afd7bb1f5a583c0088c72fc155cb0f9
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513302"
---
# <a name="bundle-ids-for-built-in-ios-and-ipados-apps-you-can-use-in-intune"></a>Intune에서 사용할 수 있는 기본 제공 iOS 및 iPadOS 앱의 번들 ID

iOS/iPadOS 디바이스에서 기능을 구성할 때 iOS/iPadOS 디바이스에서 기본 제공 앱을 추가할 수도 있습니다. 이 문서는 몇 가지 일반적인 기본 제공 iOS/iPadOS 앱의 번들 ID를 나열합니다. 다른 앱의 번들 ID를 찾으려면 소프트웨어 공급업체에 문의하세요. Apple의 [iOS/iPadOS 번들 ID](https://support.apple.com/guide/mdm/ios-bundle-ids-mdm90f60c1ce/web)(Apple의 웹 사이트가 열림) 목록을 참조하세요.

## <a name="bundle-ids"></a>번들 ID

| 번들 ID                   | 앱 이름     | 게시자 |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | 앱 스토어    | Apple     |
| com.apple.calculator        | 계산기   | Apple     |
| com.apple.mobilecal         | 일정     | Apple     |
| com.apple.camera            | 카메라       | Apple     |
| com.apple.mobiletimer       | 시계        | Apple     |
| com.apple.clips             | Clips        | Apple     |
| com.apple.compass           | 나침반      | Apple     |
| com.apple.MobileAddressBook | 연락처     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | 파일        | Apple     |
| com.apple.mobileme.fmf1     | 친구 찾기 | Apple     |
| com.apple.mobileme.fmip1    | 나의 iPhone 찾기  | Apple     |
| com.apple.gamecenter        | 게임 센터  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | 상태       | Apple     |
| com.apple.Home              | 홈         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | 키노트      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | 맵         | Apple     |
| com.apple.measure           | 측정 항목      | Apple     |
| com.apple.MobileSMS         | 메시지     | Apple     |
| com.apple.Music             | 음악        | Apple     |
| com.apple.news              | 뉴스         | Apple     |
| com.apple.mobilenotes       | 참고        | Apple     |
| com.apple.Numbers           | 숫자      | Apple     |
| com.apple.Pages             | 페이지        | Apple     |
| com.apple.mobilephone       | 전화        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | 사진       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | 미리 알림    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | 설정     | Apple     |
| com.apple.shortcuts         | 바로 가기    | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | 주식       | Apple     |
| com.apple.tips              | 팁         | Apple     |
| com.apple.tv                | TV           | Apple     |
| com.apple.videos            | 동영상       | Apple     |
| com.apple.VoiceMemos        | 음성 메모   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | 보기        | Apple     |
| com.apple.weather           | 날씨      | Apple     |

## <a name="next-steps"></a>다음 단계

이러한 번들 ID를 사용하여 [디바이스 기능](ios-device-features-settings.md)을 구성하고 iOS/iPadOS 디바이스에서 [일부 설정을 허용하거나 제한](device-restrictions-ios.md)합니다.
