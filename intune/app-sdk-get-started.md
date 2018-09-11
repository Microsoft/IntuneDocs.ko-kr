---
title: Microsoft Intune 앱 SDK 시작
description: Microsoft Intune을 통해 모바일 앱을 MAM(모바일 응용 프로그램 관리)에 사용할 수 있도록 빠르게 설정할 수 있습니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8e22c0caf7b99bcb7a81259829369b7671056abe
ms.sourcegitcommit: d047a692c798e1fb61ee43a487d6332bce344610
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44058951"
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Microsoft Intune 앱 SDK 시작

이 가이드에서는 Microsoft Intune을 통해 모바일 앱을 앱 보호 정책에 사용할 수 있도록 빠르게 설정하는 방법을 안내합니다. 먼저 [Intune 앱 SDK 개요](app-sdk.md) 항목에 설명되어 있는 Intune 앱 SDK의 이점을 이해하는 것이 좋습니다.

Intune 앱 SDK는 iOS 및 Android에서 유사한 시나리오를 지원하며 다양한 플랫폼에서 IT 관리자를 위한 일관된 환경을 만들기 위한 것입니다. 하지만 플랫폼의 제한으로 인해 특정 기능 지원에는 약간씩 차이가 있습니다.

## <a name="register-your-store-app-with-microsoft"></a>Microsoft에 스토어 앱 등록

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>앱이 조직 내부용이며 공개적으로 사용할 수 없는 경우:

앱을 등록할 *필요가 없습니다*. 내부 기간 업무 앱의 경우 IT 관리자는 내부적으로 앱을 배포합니다. Intune에서는 SDK로 빌드된 앱을 감지하여 IT 관리자가 해당 앱에 앱 보호 정책을 적용할 수 있도록 합니다. [iOS 또는 Android 앱을 앱 보호 정책에 사용할 수 있도록 설정](#enable-your-iOS-or-Android-app-for-app-protection-policy) 섹션으로 건너뛸 수 있습니다.

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>앱이 Apple App Store 또는 Google Play와 같은 공개 앱 스토어에 출시되는 경우:

_**반드시**_ 먼저 Microsoft Intune에 앱을 등록하고 등록 조건에 동의해야 합니다. 그런 다음, IT 관리자는 Intune 앱 파트너로 나열될 관리되는 앱에 앱 보호 정책을 적용할 수 있습니다.

Microsoft Intune 팀에서 등록을 완료하고 확인할 때까지 Intune 관리자는 앱의 딥 링크에 앱 보호 정책을 적용할 수 없습니다. Microsoft는 앱을 [Microsoft Intune 파트너 페이지](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)에도 추가할 예정입니다. 그 페이지에는 Intune 앱 보호 정책을 지원하는 앱임을 나타내는 앱 아이콘이 표시됩니다.

등록 프로세스를 시작하려면 [Microsoft Intune 앱 파트너 설문지](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u)를 작성하세요.

Microsoft에서는 사용자의 설문지 응답에 명시된 메일 주소를 사용하여 연락한 후 등록 프로세스를 진행합니다. 또한 연락해야 할 사항이 있는 경우 등록 메일 주소를 사용하여 연락합니다.

> [!NOTE]
> Microsoft Intune 팀에서 설문지나 메일 서신을 통해 수집한 모든 정보에 [Microsoft 개인정보취급방침](https://www.microsoft.com/privacystatement/default.aspx)이 적용됩니다.

**등록 프로세스 진행 사항**:

1. 설문지를 제출하고 나면 Microsoft에서 등록 메일 주소를 통해 연락을 드려 성공적인 수신을 확인하거나 등록을 완료하기 위해 필요한 추가 정보를 요청합니다.

2. Microsoft는 사용자로부터 필요한 모든 정보를 받은 후 서명할 수 있는 Microsoft Intune 앱 파트너 계약서를 보냅니다. 이 계약에서는 Microsoft Intune 앱 파트너가 되려는 회사가 동의해야 하는 조건을 설명합니다.

3. 또한 앱이 Microsoft Intune 서비스를 사용해 등록 완료되는 경우 및 앱이 [Microsoft Intune 파트너](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) 사이트에서 추천 목록에 뜨는 경우에도 알려드립니다.

4. 마지막으로 다음 월별 Intune 서비스 업데이트에 앱의 딥 링크가 추가됩니다. 예를 들어 등록 정보가 7월에 완료되는 경우 딥 링크는 8월 중순에 지원됩니다.

앱의 딥 링크가 향후에 변경되면 앱을 다시 등록해야 합니다.

> [!NOTE]
> 새 버전의 Intune 앱 SDK를 사용하여 앱을 업데이트하는 경우에도 Microsoft에 알려 주세요.

## <a name="download-the-sdk-files"></a>SDK 파일 다운로드

네이티브 iOS 및 Android용 Intune 앱 SDK는 Microsoft GitHub 계정에서 호스트됩니다. 다음 공용 리포지토리에는 기본 iOS 및 Android용 SDK 파일이 각각 포함되어 있습니다.

* [iOS용 Intune 앱 SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Android용 Intune 앱 SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

앱이 Xamarin 앱인 경우 이 SDK 변형을 사용하세요.

* [Intune 앱 SDK Xamarin 바인딩](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)

Microsoft 리포지토리에서 분기하고 끌어오는 데 사용할 수 있는 GitHub 계정을 등록하는 것이 좋습니다. GitHub에서는 개발자가 Microsoft 제품 팀과 커뮤니케이션하고, 문제를 개설하고 빠른 응답을 받으며, 릴리스 정보를 확인하고, Microsoft에 피드백을 제공할 수 있도록 하고 있습니다. Intune 앱 SDK GitHub에 대해 궁금한 사항은 msintuneappsdk@microsoft.com으로 문의해 주세요.

## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>iOS 또는 Android 앱을 앱 보호 정책에 사용할 수 있도록 설정

앱에 Intune 앱 SDK를 통합하려면 다음 개발자 가이드 중 하나가 필요합니다.

* **[iOS용 Intune 앱 SDK 개발자 가이드](app-sdk-ios.md)**: 이 문서에서는 Intune 앱 SDK를 사용하여 기본 iOS 앱을 사용하도록 설정하는 과정을 단계별로 안내합니다.

* **[Android용 Intune 앱 SDK 개발자 가이드](app-sdk-android.md)**: 이 문서에서는 Intune 앱 SDK를 사용하여 기본 Android 앱을 사용하도록 설정하는 과정을 단계별로 안내합니다.

* **[Intune 앱 SDK Xamarin 바인딩 가이드](app-sdk-xamarin.md)**: 이 문서를 사용하면 Intune 앱 보호 정책용 Xamarin을 사용하여 iOS 및 Android 앱을 쉽게 빌드할 수 있습니다.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>iOS 또는 Android 앱에서 앱 기반 조건부 액세스를 사용하도록 설정
 
 앱에서 앱 보호 정책을 사용하도록 설정하는 것 외에도 다음 사항이 충족되어야 앱에서 AAD(Azure Active Directory) 앱 기반 조건부 액세스가 제대로 작동합니다.
 
 * 앱은 [Azure Active Directory 인증 라이브러리](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)를 통해 빌드되고 AAD broker 인증을 사용하도록 설정되어 있어야 합니다.
 
 * 앱의 [AAD 클라이언트 ID](https://docs.microsoft.com/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application)는 iOS 및 Android 플랫폼에서 고유해야 합니다.
 
## <a name="configure-telemetry-for-your-app"></a>앱에 대한 원격 분석 구성

Microsoft Intune은 앱의 사용 통계에 대한 데이터를 수집합니다.

* **iOS용 Intune 앱 SDK**: SDK는 기본적으로 사용 이벤트에 대한 SDK 원격 분석 데이터를 기록합니다. 이 데이터는 Microsoft Intune로 전송됩니다.

    * 앱에서 Microsoft Intune으로 SDK 원격 분석 데이터를 보내지 않으려면 IntuneMAMSettings 사전에서 `MAMTelemetryDisabled` 속성을 "YES"로 설정하여 원격 분석 전송을 사용하지 않도록 설정해야 합니다.

* **Android용 Intune 앱 SDK**: Android용 Intune 앱 SDK는 앱에서 데이터 수집을 제어하지 않습니다. 기본적으로 회사 포털 응용 프로그램은 원격 분석 데이터를 기록합니다. 이 데이터는 Microsoft Intune로 전송됩니다. Microsoft 정책에 따라 Microsoft는 PII(개인 식별 정보)를 수집하지 않습니다. 

    * 최종 사용자가 이 데이터를 보내지 않도록 선택하는 경우 회사 포털 앱의 [설정]에서 원격 분석을 해제해야 합니다. 자세한 내용은 [Microsoft 사용 현황 데이터 수집 해제](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android)를 참조하세요. 


 iOS 및 Android 기간 업무 앱 버전 번호가 표시됩니다.<!-- 1380712 -->

## <a name="line-of-business-app-version-numbers"></a>기간 업무 앱 버전 번호

Intune의 기간 업무 앱은 이제 iOS 및 Android 앱의 버전 번호를 표시합니다. 번호는 Azure Portal, 앱 목록 및 앱 개요 블레이드에 표시됩니다. 최종 사용자는 회사 포털 앱 및 웹 포털에서 앱 번호를 확인할 수 있습니다.

### <a name="full-version-number"></a>전체 버전 번호

전체 버전 번호는 앱의 특정 릴리스를 식별합니다. 번호는 _버전_(_빌드_)으로 표시됩니다. 예를 들어 2.2(2.2.17560800). 

전체 버전 번호는 다음과 같은 두 구성 요소로 이루어져 있습니다.

 - **버전**  
   버전 번호는 사람이 읽을 수 있는 앱의 릴리스 번호입니다. 이는 최종 사용자가 앱의 다양한 릴리스를 식별하는 데 사용합니다.

 - **빌드 번호**  
    빌드 번호는 앱 검색에 사용하고 프로그래밍 방식으로 앱을 관리하기 위한 내부 번호입니다. 빌드 번호는 코드에서 변경 내용을 참조하는 앱의 반복을 가리킵니다.

### <a name="version-and-build-number-in-android-and-ios"></a>Android 및 iOS의 버전 및 빌드 번호

Android 및 iOS는 모두 앱과 관련하여 버전 및 빌드 번호를 사용합니다. 그러나 두 운영 체제는 모두 OS 특정적인 의미가 있습니다. 다음 표에 이러한 용어 간의 관계가 설명되어 있습니다.

Intune에서 사용하기 위해 기간 업무 응용 프로그램을 개발 중인 경우 버전 및 빌드 번호를 모두 사용해야 합니다. Intune 앱 관리 기능은 의미 있는 **CFBundleVersion**(iOS의 경우) 및 **PackageVersionCode**(Android의 경우)를 사용합니다. 이러한 번호는 앱 매니페스트에서 포함됩니다. 

Intune|iOS|Android|설명|
|---|---|---|---|
버전 번호|CFBundleShortVersionString|PackageVersionName |이 번호는 최종 사용자를 위한 앱의 특정 릴리스를 나타냅니다.|
빌드 번호|CFBundleVersion|PackageVersionCode |이 번호는 앱 코드에서 반복을 나타내는 데 사용됩니다.|

#### <a name="ios"></a>iOS

- **CFBundleShortVersionString**  
    번들의 릴리스 버전 번호를 지정합니다. 이 번호는 앱의 릴리스된 버전을 식별합니다. 최종 사용자가 앱을 참조하는 데 사용되는 번호입니다.
  - **CFBundleVersion**  
    번들의 빌드 버전으로, 번들의 반복을 식별합니다. 번호는 릴리스 또는 릴리스되지 않은 번들을 식별할 수도 있습니다. 번호는 앱 검색에 사용됩니다.

#### <a name="android"></a>Android

 - **PackageVersionName**  
    사용자에게 표시되는 버전 번호입니다. 이 특성은 원시 문자열 또는 문자열 리소스에 대한 참조로 설정할 수 있습니다. 문자열은 사용자에게 표시하기 위한 것입니다.
 - **PackageVersionCode**  
    내부 버전 번호입니다. 이 번호는 해당 버전이 더 최신 버전임을 나타내는 더 높은 숫자가 있는 다른 버전에 비해 더 최신인지 여부를 판명하는 데만 사용됩니다. 이는 버전이 아닙니다. 

## <a name="next-steps-after-integration"></a>통합 후 다음 단계

### <a name="test-your-app"></a>앱 테스트
iOS 또는 Android 앱을 Intune 앱 SDK와 통합하는 데 필요한 단계를 완료한 후에는 모든 앱 보호 정책이 사용하도록 설정되어 사용자 및 IT 관리자에 대해 작동하는지 확인해야 합니다. 통합된 앱을 테스트하려면 다음이 필요합니다.

* **Microsoft Intune 테스트 계정**: Intune 앱 보호 기능에 대해 Intune 관리 앱을 테스트하려면 Microsoft Intune 계정이 필요합니다.

    * Intune 앱 보호 정책에 대해 iOS 또는 Android 스토어 앱을 사용하도록 설정하는 ISV인 경우 등록 단계에 설명된 대로 Microsoft Intune을 사용하여 등록을 완료하면 프로모션 코드를 받게 됩니다. 이 프로모션 코드를 사용하여 1년 연장하여 사용할 수 있는 Microsoft Intune 평가판을 신청할 수 있습니다.

    * 스토어에 게시하지 않을 LOB(기간 업무) 앱을 개발 중인 경우에는 조직을 통해 Microsoft Intune에 대한 액세스 권한을 가져야 합니다. [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0)에서 한 달 무료 평가판도 신청할 수 있습니다.

* **Intune 앱 보호 정책**: 모든 Intune 앱 보호 정책에 대해 앱을 테스트하려면 각 정책 설정에 대해 예상되는 동작이 무엇인지 알고 있어야 합니다. [iOS 앱 보호 정책](/intune-classic/deploy-use/ios-mam-policy-settings) 및 [Android 앱 보호 정책](/intune-classic/deploy-use/android-mam-policy-settings)에 대한 설명을 참조하세요.

* **문제 해결**: 앱의 사용자 환경을 수동으로 테스트하는 동안 문제가 발생하면 [Troubleshooting MAM](/intune-classic/troubleshoot/troubleshoot-mam)(MAM 문제 해결)을 확인하세요. 이 문서에서는 Intune 관리 앱에서 발생할 수 있는 일반적인 문제, 대화 및 오류 메시지에 관한 도움말을 제공합니다. 

### <a name="badge-your-app-optional"></a>앱에 배지 지정(선택 사항)

Intune 앱 보호 정책이 앱에서 작동하는지 확인한 후 Intune 앱 보호 로고와 함께 앱 아이콘에 배지를 지정할 수 있습니다.

이 배지는 IT 관리자, 최종 사용자 및 잠재적인 Intune 고객에게 앱이 Intune 앱 보호 정책을 준수한다는 것을 나타냅니다. 또한 Intune 고객에게 해당 앱의 사용 및 채택을 권장합니다.

배지는 서류 가방 아이콘이며 아래의 샘플에서 볼 수 있습니다.

![배지 예 1](./media/badge-example-1.png) ![배지 예 2](./media/badge-example-2.png)

**앱에 배지를 지정하는 데 필요한 항목**:

* **.eps** 파일을 읽을 수 있는 이미지 조작 응용 프로그램 또는 **.ai** 파일을 읽을 수 있는 Adobe 응용 프로그램

* Microsoft Intune GitHub에서 [Intune 앱 배지 자산 및 지침](https://github.com/msintuneappsdk/intune-app-partner-badge)을 찾을 수 있습니다.
