---
title: Microsoft Intune으로 모바일 응용 프로그램 관리용 앱을 준비하는 방법 결정
description: 이 항목의 정보는 LOB(기간 업무) 앱이 모바일 앱 관리 정책을 사용하도록 하기 위해 앱 줄 바꿈 도구 및 앱 SDK를 사용해야 하는 경우를 결정하는 데 도움이 됩니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 8841354b268f70634a61040fb06ed857120e9cfc
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181975"
---
# <a name="prepare-line-of-business-apps-for-app-protection-policies"></a>앱 보호 정책에 대해 LOB(기간 업무) 앱 준비

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Intune 앱 래핑 도구 또는 Intune 앱 SDK를 사용하여 앱에서 앱 보호 정책을 사용할 수 있게 할 수 있습니다. 이 정보를 사용하여 이러한 두 가지 방법 및 사용 시기에 대해 알아보세요.

## <a name="intune-app-wrapping-tool"></a>Intune 앱 래핑 도구
앱 래핑 도구는 **내부** LOB(기간 업무) 앱에 주로 사용됩니다. 이 도구는 앱을 둘러싸는 래퍼를 만들어 앱이 Intune 앱 보호 정책에 의해 관리될 수 있게 하는 명령줄 응용 프로그램입니다. ISV(Independent Software Vendor)가 제공하는 앱을 보호할 때는 ISV가 래핑된 앱을 계속해서 지원할지 여부를 명시하는 것이 중요합니다.

도구를 사용하기 위해 소스 코드가 필요하지는 않지만 서명 자격 증명이 필요합니다. 서명 자격 증명에 대한 자세한 내용은 [Intune 블로그](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)를 참조하세요. 앱 래핑 도구 설명서는 [Android App Wrapping Tool](app-wrapper-prepare-android.md)(앱 래핑 도구) 및 [iOS App Wrapping Tool](app-wrapper-prepare-ios.md)(iOS 앱 래핑 도구) 항목을 참조하세요.

앱 래핑 도구는 Apple 앱 스토어 또는 Google Play 스토어에서 앱을 지원하지 **않습니다**. 개발자 통합이 필요한 특정 기능을 지원하지도 않습니다(다음 기능 비교 표 참조).

Intune에 등록되지 않은 장치의 앱 보호 정책에 대한 앱 래핑 도구에 대한 자세한 내용은 [Microsoft Intune에 등록되지 않은 장치의 기간 업무 앱 및 데이터 보호](/intune-classic/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune)를 참조하세요.

### <a name="reasons-to-use-the-app-wrapping-tool"></a>앱 래핑 도구를 사용하는 이유
* 앱에 기본 제공 데이터 보호 기능이 없습니다.
* 앱이 간단합니다.
* 앱이 내부적으로 배포됩니다.
* 앱의 소스 코드에 액세스할 수 없습니다.
* 앱 개발자가 아닙니다.
* 앱에 최소한의 사용자 인증 환경이 있습니다.

### <a name="supported-app-development-platforms"></a>지원되는 앱 개발 플랫폼

|**앱 래핑 도구** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |예|예|
|**OWA(Outlook Web Access)**|아니요 – [Intune 앱 SDK Xamarin 바인딩](app-sdk-xamarin.md)을 사용합니다.|예|

## <a name="intune-app-sdk"></a>Intune 앱 SDK
앱 SDK는 주로 Apple 앱 스토어 및/또는 Google Play 스토어에 앱이 있으며 Intune으로 앱을 관리할 수 있기를 원하는 고객을 위해 설계되었습니다. 그러나 기간 업무 앱을 비롯한 모든 앱은 SDK 통합을 활용할 수 있습니다.

SDK에 대해 자세히 알아보려면 [개요](app-sdk.md) 항목을 참조하세요. SDK 사용을 시작하려면 [Microsoft Intune 앱 SDK 시작](app-sdk-get-started.md) 항목을 참조하세요.

### <a name="reasons-to-use-the-sdk"></a>SDK를 사용하는 이유
* 앱에 기본 제공 데이터 보호 기능이 없습니다.
* 앱이 복잡하며 다양한 환경을 포함하고 있습니다.
* 앱이 Google Play 또는 Apple의 앱 스토어와 같은 공개 앱 스토어에 배포됩니다.
* 앱 개발자이며 SDK를 사용할 수 있는 기술적 배경을 가지고 있습니다.
* 앱에 다른 SDK 통합이 있습니다.
* 앱이 자주 업데이트됩니다.

### <a name="supported-app-development-platforms"></a>지원되는 앱 개발 플랫폼

|**Intune 앱 SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|예 – [Intune 앱 SDK Xamarin 바인딩](app-sdk-xamarin.md)을 사용합니다.|아니요|
|**OWA(Outlook Web Access)**| 예 – [Intune 앱 SDK Xamarin 바인딩](app-sdk-xamarin.md)을 사용합니다.|아니요|

## <a name="feature-comparison"></a>기능 비교
이 표에는 앱 SDK 및 앱 래핑 도구에 사용할 수 있는 설정이 나와 있습니다.

> [!NOTE]
> 앱 래핑 도구는 Intune 독립 실행형 또는 Configuration Manager가 포함된 Intune과 함께 사용할 수 있습니다.

|기능|앱 SDK|앱 래핑 도구|
|-----------|---------------------|-----------|
|웹 콘텐츠가 회사에서 관리되는 브라우저에 표시되도록 제한|X|X|
|Android, iTunes 또는 iCloud 백업 차단|X|X|
|앱이 다른 앱으로 데이터를 전송하도록 허용|X|X|
|앱이 다른 앱의 데이터를 받도록 허용|X|X|
|다른 앱에서 잘라내기, 복사 및 붙여넣기 제한|X|X|
|액세스용 단순 PIN 필요|X|X|
|기본 제공 앱 PIN을 Intune PIN으로 바꾸기|X||
|PIN을 다시 설정하기 전 시도 횟수 지정|X|X|
|PIN 대신 지문 허용|X|X|
|PIN 대신 안면 인식 허용(iOS에만 해당)|X|X|
|액세스 시 회사 자격 증명 필요|X|X|
|관리되는 앱이 무단 해제 또는 루팅된 장치를 실행하지 못하도록 차단|X|X|
|앱 데이터 암호화|X|X|
|지정된 시간(분) 후에 액세스 요구 사항 다시 확인|X|X|
|오프라인 유예 기간 지정|X|X|
|화면 캡처 차단(Android에만 해당)|X|X|
|장치 등록이 제외된 MAM에 대한 지원|X|X|
|전체 초기화|X|X|
|선택적 초기화 <br></br>**참고:** iOS의 경우 관리 프로필을 제거하면 앱도 제거됩니다.|X||
|"다른 이름으로 저장" 차단|X||
|대상 응용 프로그램 구성|X||
|다중 ID 지원|X||
|사용자 지정 가능한 스타일 |X|||
|Citrix mVPN을 통한 주문형 응용 프로그램 VPN|X|X| 
|연락처 동기화 사용 안 함|X|X|
|인쇄 사용 안 함|X|X|
|최소 앱 버전 필요|X|X|
|최소 운영 체제 필요(iOS 및 Android)|X|X|
|최소 Android 보안 패치 버전 필요(Android에만 해당)|X|X|
|iOS용 최소 Intune SDK 필요(iOS에만 해당)|X|X|

## <a name="next-steps"></a>다음 단계

앱 보호 정책 및 Intune에 대한 자세한 내용은 다음 항목을 참조하세요.

  - [Android 앱 래핑 도구](app-wrapper-prepare-android.md)</br>
  - [iOS 앱 래핑 도구](app-wrapper-prepare-ios.md)</br>
  - [SDK를 사용하여 모바일 응용 프로그램 관리에 앱을 사용하도록 설정](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
