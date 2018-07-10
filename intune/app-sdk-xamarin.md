---
title: Microsoft Intune 앱 SDK Xamarin 바인딩
description: Intune 앱 SDK Xamarin 바인딩은 Xamarin에 내장된 iOS 및 Android 앱의 Intune 앱 보호 정책을 사용하도록 설정합니다.
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 06/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f8f5e397c314088c7b26edba486f9cbaf9718096
ms.sourcegitcommit: 1eddded65ae9e442dd3bebd16b9428af76a67f34
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2018
ms.locfileid: "35250947"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune 앱 SDK Xamarin 바인딩

> [!NOTE]
> 먼저 지원되는 각 플랫폼에서 통합을 준비하는 방법을 설명하는 [Intune 앱 SDK 시작](app-sdk-get-started.md) 문서를 읽어보는 것이 좋습니다.

## <a name="overview"></a>개요
[Intune 앱 SDK Xamarin 바인딩](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)은 Xamarin에 내장된 iOS 및 Android 앱의 [Intune 앱 보호 정책](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)을 사용하도록 설정합니다. 개발자는 바인딩을 사용하여 Intune 앱 보호 기능을 Xamarin 기반 앱에 손쉽게 빌드할 수 있습니다.

Microsoft Intune 앱 SDK Xamarin 바인딩을 사용하면 Xamarin으로 개발한 앱에 Intune 앱 보호 정책(APP 또는 MAM 정책이라고도 함)을 통합할 수 있습니다. MAM 지원 응용 프로그램은 Intune 앱 SDK와 통합된 응용 프로그램입니다. IT 관리자는 Intune에서 앱을 적극적으로 관리할 때 모바일 앱에 앱 보호 정책을 배포할 수 있습니다.

## <a name="whats-supported"></a>지원되는 기능

### <a name="developer-machines"></a>개발자 컴퓨터
* Windows
* macOS


### <a name="mobile-app-platforms"></a>모바일 앱 플랫폼
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Intune 모바일 응용 프로그램 관리 시나리오

* Intune APP-WE(장치 등록을 사용하지 않는)
* Intune MAM 등록 장치
* 타사 EMM 등록 장치

이제 Intune 앱 SDK Xamarin 바인딩이 내장된 Xamarin 앱에서는 Intune 모바일 장치 관리(MDM)가 등록된 장치 및 등록되지 않은 장치 모두에서 Intune 앱 보호 정책을 받을 수 있습니다.

## <a name="prerequisites"></a>전제 조건

[사용 약관](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf)을 검토합니다. 기록을 위해 사용 조건의 사본을 인쇄하여 보관하세요. Intune 앱 SDK Xamarin 바인딩을 다운로드하여 이러한 사용 조건에 동의합니다. 동의하지 않는 경우 소프트웨어를 사용하지 마세요.

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>iOS 모바일 앱에서 Intune 앱 보호 정책을 사용하도록 설정
1. [Microsoft.Intune.MAM.Xamarin.iOS NuGet 패키지](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)를 Xamarin.iOS 프로젝트에 추가합니다.
2.  Intune 앱 SDK를 iOS 모바일 앱에 통합하는 데 필요한 일반적인 단계를 따르세요. [iOS용 Intune 앱 SDK 개발자 가이드](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)의 통합 지침 3단계에서 시작할 수 있습니다. 이 도구가 Microsoft.Intune.MAM.Xamarin.iOS 패키지에 포함되어 있고 빌드 시 자동으로 실행되므로 IntuneMAMConfigurator를 실행하는 해당 섹션의 마지막 단계를 건너뛸 수 있습니다.
    **중요**: 앱에 키 집합 공유를 사용하도록 설정하는 작업이 Visual Studio와 Xcode에서 약간 다릅니다. 앱의 Entitlements plist를 열고 "키 집합 사용" 옵션이 설정되었으며 해당 섹션에 적절한 키 집합 공유 그룹이 추가되어 있는지 확인합니다. 그런 다음 적절한 모든 구성/플랫폼 조합에 대해 프로젝트 "iOS 번들 서명" 옵션의 "사용자 지정 자격" 필드에 Entitlements plist가 지정되어 있는지 확인합니다.
3.  바인딩을 추가하고 앱을 제대로 구성하면 앱에서 Intune SDK API를 사용할 수 있습니다. 이렇게 하려면 다음 네임스페이스를 포함해야 합니다.

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. 앱 보호 정책을 받기 시작하려면 앱이 Intune MAM 서비스에 등록되어 있어야 합니다. 앱이 이미 Azure ADAL(Active Directory Authentication Library)을 사용하여 사용자를 인증하는 경우 앱에서 성공적으로 인증한 후 IntuneMAMEnrollmentManager의 registerAndEnrollAccount 메서드에 사용자 UPN을 제공해야 합니다.
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **중요**: Intune 앱 SDK의 기본 ADAL 설정을 앱 설정으로 재정의해야 합니다. [iOS용 Intune 앱 SDK 개발자 가이드](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)에 설명된 대로 앱의 Info.plist에 있는 IntuneMAMSettings 사전을 통해 재정의하거나, IntuneMAMPolicyManager 인스턴스의 AAD 재정의 속성을 사용할 수 있습니다. Info.plist 접근 방법은 ADAL 설정이 정적인 응용 프로그램에 권장되고, 재정의 속성은 런타임에 이러한 값을 확인하는 응용 프로그램에 권장됩니다. 
      
      앱이 ADAL을 사용하지 않고 Intune SDK를 사용하여 인증을 처리하려는 경우에는 앱에서 IntuneMAMEnrollmentManager의 loginAndEnrollAccount 메서드를 호출해야 합니다.
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      
> [!NOTE] 
> iOS용 리매퍼가 없습니다. Xamarin.Forms 앱에 통합하는 것은 일반 Xamarin.iOS 프로젝트와 동일합니다. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Android 모바일 앱에서 Intune 앱 보호 정책을 사용하도록 설정

### <a name="xamarinandroid-integration"></a>Xamarin.Android 통합

1. [Microsoft.Intune.MAM.Xamarin.Android NuGet 패키지](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)의 최신 버전을 Xamarin.Android 프로젝트에 추가합니다. 이렇게 하면 Intune이 응용 프로그램을 사용하기에 필요한 참조를 제공합니다.

2. [Android용 Intune 앱 SDK 개발자 가이드](app-sdk-android.md)를 특별한 관심을 갖고 충분히 읽고 따르십시오.
    1. [전체 클래스 및 메서드 바꾸기 섹션](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)입니다. 
    2. [MAMApplication 섹션](app-sdk-android.md#mamapplication)입니다. 서브 클래스가 `[Application]` 특성으로 올바르게 데코레이팅되고 `(IntPtr, JniHandleOwnership)` 생성자를 재정의하는지 확인입니다.
    3. 앱이 AAD에 대한 인증을 수행하는 경우의 [ADAL 통합 섹션](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)입니다.
    4. 응용 프로그램의 MAM 서비스에서 정책을 가져오려고 계획한 경우의 [MAM-WE 등록 섹션](app-sdk-android.md#app-protection-policy-without-device-enrollment)입니다.

> [!NOTE]
> 가이드에서 코드 조각을 변환하는 경우 또는 `Microsoft.Intune.MAM.Xamarin.Android` 바인딩의 [Android용 Intune 앱 SDK 개발자 가이드](app-sdk-android.md)에서 동등한 API를 찾으려 시도하는 경우 Xamarin 바인딩 생성기가 다음과 같은 주목할 만한 방식으로 Android API를 수정할 수 있음을 알아야 합니다.
> * 모든 식별자는 파스칼식 대/소문자로 변환(com.foo.bar ->Com.Foo.Bar)
> * 모든 가져오기/설정하기 작업이 속성 작업으로 변환(예: Foo.getBar() -> Foo.Bar, Foo.setBar("zap") -> Foo.Bar = "zap")
> * 모든 인터페이스가 'I' 문자를 이름에 추가(FooInterface -> IFooInterface)

### <a name="xamarinforms-integration"></a>Xamarin.Forms 통합

**위의 단계를 모두 수행하는 것 외에도** `Xamarin.Forms` 응용 프로그램의 경우 `Microsoft.Intune.MAM.Remapper` 패키지를 제공합니다. 이 패키지는 `FormsAppCompatActivity` 및 `FormsApplicationActivity`처럼 일반적으로 사용된 `Xamarin.Forms` 클래스의 클래스 계층 구조에 `MAM` 클래스를 삽입하여 사용자를 위해 클래스 바꾸기를 수행하므로 `OnMAMCreate` 및 `OnMAMResume`처럼 MAM 동등한 함수에 대한 재정의를 제공하여 이러한 클래스를 계속 사용할 수 있습니다. 이 도구를 사용하려면 다음을 수행하십시오.

1.  프로젝트에 [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) NuGet 패키지를 추가합니다. 이렇게 하면 아직 Intune 앱 SDK Xamarin 바인딩이 포함되지 않은 경우 자동으로 추가됩니다.

2.  위의 2.2 단계에서 만든 `MAMApplication` 클래스의 `OnMAMCreate` 함수에서 `Xamarin.Forms.Forms.Init(Context, Bundle)`에 호출을 추가합니다. Intune 관리를 통해 응용 프로그램이 백그라운드에서도 시작할 수 있기 때문에 필요합니다.

> [!NOTE]
> 이 작업은 Visual Studio가 Intellisense 자동 완성을 위해 사용하는 종속성을 다시 작성하기 때문에 Intellisense가 변경 내용을 올바로 인식하도록 처음 Remapper를 실행한 후 Visual Studio를 다시 시작해야 할 수 있습니다. 


## <a name="support"></a>Support

조직이 기존 Intune 고객인 경우 Microsoft 지원 담당자에게 문의해 지원 티켓을 열고 [Github 문제 페이지에서](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) 문제를 만들면 가능한 한 빨리 도움을 제공할 수 있습니다. 
