---
title: Microsoft Intune 앱 SDK Xamarin 바인딩
description: Intune 앱 SDK Xamarin 바인딩은 Xamarin에 내장된 iOS 및 Android 앱의 Intune 앱 보호 정책을 사용하도록 설정합니다.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19202d4387635b7cd1f7e4604d755fb8a213d327
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503445"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune 앱 SDK Xamarin 바인딩

> [!NOTE]
> 먼저 지원되는 각 플랫폼에서 통합을 준비하는 방법을 설명하는 [Intune 앱 SDK 시작](app-sdk-get-started.md) 문서를 읽어보는 것이 좋습니다.

## <a name="overview"></a>개요
[Intune 앱 SDK Xamarin 바인딩](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)은 Xamarin에 내장된 iOS 및 Android 앱의 [Intune 앱 보호 정책](../apps/app-protection-policy.md)을 사용하도록 설정합니다. 개발자는 바인딩을 사용하여 Intune 앱 보호 기능을 Xamarin 기반 앱에 손쉽게 빌드할 수 있습니다.

Microsoft Intune 앱 SDK Xamarin 바인딩을 사용하면 Xamarin으로 개발한 앱에 Intune 앱 보호 정책(APP 또는 MAM 정책이라고도 함)을 통합할 수 있습니다. MAM 지원 애플리케이션은 Intune 앱 SDK와 통합된 애플리케이션입니다. IT 관리자는 Intune에서 앱을 적극적으로 관리할 때 모바일 앱에 앱 보호 정책을 배포할 수 있습니다.

## <a name="whats-supported"></a>지원되는 기능

### <a name="developer-machines"></a>개발자 컴퓨터
* Windows(Visual Studio 버전 15.7+)
* macOS

### <a name="mobile-app-platforms"></a>모바일 앱 플랫폼
* Android
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Intune 모바일 애플리케이션 관리 시나리오

* Intune APP-WE(디바이스 등록을 사용하지 않는)
* Intune MAM 등록 디바이스
* 타사 EMM 등록 디바이스

이제 Intune 앱 SDK Xamarin 바인딩이 내장된 Xamarin 앱에서는 Intune 모바일 디바이스 관리(MDM)가 등록된 디바이스 및 등록되지 않은 디바이스 모두에서 Intune 앱 보호 정책을 받을 수 있습니다.

## <a name="prerequisites"></a>전제 조건

[사용 약관](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf)을 검토합니다. 기록을 위해 사용 조건의 사본을 인쇄하여 보관하세요. Intune 앱 SDK Xamarin 바인딩을 다운로드하여 이러한 사용 조건에 동의합니다. 동의하지 않는 경우 소프트웨어를 사용하지 마세요.

Intune SDK가 작동하려면 [인증](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) 및 조건부 시작 시나리오를 위한 [ADAL(Active Directory 인증 라이브러리)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)이 필요하며, 이 경우 앱에 [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/)를 구성해야 합니다. 

애플리케이션이 ADAL 또는 MSAL을 사용하도록 이미 구성되어 있고, Azure Active Directory를 사용하여 인증하는 데 사용되는 고유한 사용자 지정 클라이언트 ID가 있는 경우 Intune MAM(모바일 애플리케이션 관리) 서비스에 대한 Xamarin 앱 사용 권한을 부여하는 단계를 따릅니다. [Intune SDK 시작 가이드](app-sdk-get-started.md)의 "[앱에 Intune 앱 보호 서비스에 대한 액세스 권한 부여](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)" 섹션의 지침을 사용합니다.



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>iOS 모바일 앱에서 Intune 앱 보호 정책을 사용하도록 설정
1. [Microsoft.Intune.MAM.Xamarin.iOS NuGet 패키지](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)를 Xamarin.iOS 프로젝트에 추가합니다.
2. Intune 앱 SDK를 iOS 모바일 앱에 통합하는 데 필요한 일반적인 단계를 따르세요. [iOS용 Intune 앱 SDK 개발자 가이드](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)의 통합 지침 3단계에서 시작할 수 있습니다. 이 도구가 Microsoft.Intune.MAM.Xamarin.iOS 패키지에 포함되어 있고 빌드 시 자동으로 실행되므로 IntuneMAMConfigurator를 실행하는 해당 섹션의 마지막 단계를 건너뛸 수 있습니다.
    **중요**: 앱에 키 집합 공유를 사용하도록 설정하는 작업이 Visual Studio와 Xcode에서 약간 다릅니다. 앱의 Entitlements plist를 열고 "키 집합 사용" 옵션이 설정되었으며 해당 섹션에 적절한 키 집합 공유 그룹이 추가되어 있는지 확인합니다. 그런 다음 적절한 모든 구성/플랫폼 조합에 대해 프로젝트 "iOS 번들 서명" 옵션의 "사용자 지정 자격" 필드에 Entitlements plist가 지정되어 있는지 확인합니다.
3. 바인딩을 추가하고 앱을 제대로 구성하면 앱에서 Intune SDK API를 사용할 수 있습니다. 이렇게 하려면 다음 네임스페이스를 포함해야 합니다.

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. 앱 보호 정책을 받기 시작하려면 앱이 Intune MAM 서비스에 등록되어 있어야 합니다. 앱이 사용자 인증을 위해 [Azure Active Directory 인증 라이브러리](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory)(ADAL) 또는 [Microsoft 인증 라이브러리](https://www.nuget.org/packages/Microsoft.Identity.Client)(MSAL)를 사용하지 않고 Intune SDK에서 인증을 처리하도록 하려는 경우, 앱은 사용자의 UPN을 IntuneMAMEnrollmentManager의 LoginAndEnrollAccount 메서드에 제공해야 합니다.

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      호출 시 사용자의 UPN을 알 수 없는 경우 앱이 null에 전달할 수 있습니다. 이 경우 사용자에게 이메일 주소와 암호를 모두 입력하라는 메시지가 표시됩니다.
      
      앱이 이미 ADAL 또는 MSAL을 사용하여 사용자를 인증하는 경우 앱과 Intune SDK 간에 SSO(single sign-on) 환경을 구성할 수 있습니다. 먼저 iOS용 Intune Xamarin Bindings(com.microsoft.adalcache)에서 사용하는 것과 동일한 키체인 액세스 그룹에 토큰을 저장하도록 ADAL/MSAL을 구성해야 합니다. ADAL의 경우 [AuthenticationContext의 iOSKeychainSecurityGroup 속성을 설정](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/iOS-Keychain-Access)하여 이 작업을 수행할 수 있습니다. MSAL의 경우 [PublicClientApplication의 iOSKeychainSecurityGroup 속성을 설정](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Xamarin-iOS-specifics#enable-keychain-access)해야 합니다. 그런 다음, 앱과 함께 Intune SDK에서 사용하는 기본 AAD 설정을 재정의해야 합니다. [iOS용 Intune 앱 SDK 개발자 가이드](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)에 설명된 대로 앱의 Info.plist에 있는 IntuneMAMSettings 사전을 통해 재정의하거나, IntuneMAMPolicyManager 인스턴스의 AAD 재정의 속성을 사용할 수 있습니다. Info.plist 접근 방법은 ADAL 설정이 정적인 애플리케이션에 권장되고, 재정의 속성은 런타임에 이러한 값을 확인하는 애플리케이션에 권장됩니다. 모든 SSO 설정이 구성되면 앱은 성공적으로 인증된 후 사용자의 UPN을 IntuneMAMEnrollmentManager의 RegisterAndEnrollAccount 메서드에 제공해야 합니다.

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      앱은 IntuneMAMEnrollmentDelegate의 하위 클래스에서 EnrollmentRequestWithStatus 메서드를 구현하고 IntuneMAMEnrollmentManager의 대리자 속성을 해당 클래스의 인스턴스로 설정하여 등록 시도의 결과를 확인할 수 있습니다. 

      등록이 성공하면 앱은 다음 속성을 쿼리하여 등록된 계정의 UPN(이전에 알 수 없는 경우)을 확인할 수 있습니다. 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>샘플 애플리케이션
Xamarin.ios 앱에서 MAM 기능을 강조 표시 하는 샘플 응용 프로그램은 [GitHub](https://github.com/msintuneappsdk/sample-intune-xamarin-ios)에서 사용할 수 있습니다.

> [!NOTE] 
> iOS용 리매퍼가 없습니다. Xamarin.Forms 앱에 통합하는 것은 일반 Xamarin.iOS 프로젝트와 동일합니다. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Android 모바일 앱에서 Intune 앱 보호 정책을 사용하도록 설정
1. [Microsoft.Intune.MAM.Xamarin.Android NuGet 패키지](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)를 Xamarin.Android 프로젝트에 추가합니다.
    1. Xamarin.Forms 앱의 경우 [Microsoft.Intune.MAM.Remapper.Tasks NuGet 패키지](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks)를 Xamarin.Android 프로젝트에도 추가합니다. 
2. 추가 세부 정보는 이 문서를 참조하여 Android 모바일 앱에 [Intune App SDK 통합](app-sdk-android.md)에 필요한 일반 단계를 따릅니다.

### <a name="xamarinandroid-integration"></a>Xamarin.Android 통합

Intune App SDK 통합에 대한 전체 개요는 [Android용 Microsoft Intune App SDK 개발자 가이드](app-sdk-android.md)에서 확인할 수 있습니다. 이 가이드를 읽고 Intune App SDK를 Xamarin 앱과 통합할 때, 다음 섹션에서는 Java에서 개발된 네이티브 Android 앱과 C#에서 개발된 Xamarin 앱의 구현 간의 차이점을 집중 조명합니다. 이 섹션은 보충으로 취급되어야 하며 가이드 전체를 읽는 것으로 대신할 수는 없습니다.

#### <a name="remapper"></a>Remapper
1\.4428.1 릴리스부터는 MAM 클래스, 메서드 및 시스템 서비스 교체를 수행 하는 [빌드](app-sdk-android.md#build-tooling) 도구로 xamarin.ios 응용 프로그램에 `Microsoft.Intune.MAM.Remapper` 패키지를 추가할 수 있습니다. Remapper를 포함 하는 경우 응용 프로그램을 빌드할 때 이름이 바뀐 메서드 및 MAM 응용 프로그램 섹션의 MAM 해당 교체 부분이 자동으로 수행 됩니다.

Remapper에서 ification의 클래스를 제외 하려면 프로젝트 `.csproj` 파일에 다음 속성을 추가 합니다.

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> 이번에는 Remapper와 관련 된 문제로 인해 Xamarin.ios 앱에서 디버그할 수 없습니다. 이 문제가 해결 될 때까지 응용 프로그램을 디버그 하는 데 수동 통합이 권장 됩니다.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[이름이 변경된 메서드](app-sdk-android.md#renamed-methods)
대부분의 경우, Android 클래스에서 사용할 수 있는 메서드가 MAM 대체 클래스에서 최종본으로 표시되어 있습니다. 이 경우 MAM 대체 클래스는 대신 재정의할 유사한 이름의 메서드(접미사 `MAM`이 붙음)를 제공합니다. 예를 들어 `OnCreate()`를 재정의하고 `base.OnCreate()`를 호출하는 대신 `MAMActivity`에서 파생하는 경우 `Activity`는 `OnMAMCreate()`를 재정의하고 `base.OnMAMCreate()`를 호출해야 합니다.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[MAM 애플리케이션](app-sdk-android.md#mamapplication)
앱은 `Android.App.Application` 클래스를 정의 해야 합니다. MAM을 수동으로 통합 하는 경우 `MAMApplication`에서 상속 해야 합니다. 서브 클래스가 `[Application]` 특성으로 올바르게 데코레이팅되고 `(IntPtr, JniHandleOwnership)` 생성자를 재정의하는지 확인입니다.

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> MAM Xamarin 바인딩 문제로 인해 디버그 모드로 배포할 때 애플리케이션이 충돌할 수 있습니다. 이 문제를 해결하려면 `Debuggable=false` 특성을 `Application` 클래스에 추가해야 하며 수동으로 설정한 경우 `android:debuggable="true"` 플래그를 매니페스트에서 제거해야 합니다.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[앱 참여를 요구하는 기능 사용](app-sdk-android.md#enable-features-that-require-app-participation)
예: 앱에 PIN이 필요한지 확인

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

예: 기본 Intune 사용자 확인

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

예: 디바이스 또는 클라우드 스토리지에 저장이 허용되는지 확인

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[SDK에서 알림 등록](app-sdk-android.md#register-for-notifications-from-the-sdk)
앱은 `MAMNotificationReceiver`를 만들고 `MAMNotificationReceiverRegistry`에 등록하여 SDK에서 알림을 등록해야 합니다. 아래 예제와 같이 `App.OnMAMCreate`에서 원하는 수신기 및 알림 유형을 제공하면 됩니다.

```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
        registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[MAM 등록 관리자](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms 통합

`Xamarin.Forms` 애플리케이션의 경우 일반적으로 사용되는 `Xamarin.Forms` 클래스의 클래스 계층에 `MAM` 클래스를 주입하여 MAM 클래스 교체를 자동으로 수행하는 `Microsoft.Intune.MAM.Remapper` 패키지를 제공했습니다. 

> [!NOTE]
> 위에 자세히 설명된 Xamarin.Android 통합 외에도 Xamarin.Forms 통합이 수행됩니다. Remapper는 Xamarin.ios 앱에서 다르게 동작 하므로 수동 MAM 대체를 계속 수행 해야 합니다.

Remapper가 프로젝트에 추가되면 MAM에 해당하는 대체를 수행해야 합니다. 예를 들어 `FormsAppCompatActivity` 및 `FormsApplicationActivity`는 `OnCreate`에 대한 재정의를 제공하고 `OnResume`이 MAM의 해당하는 `OnMAMCreate` 및 `OnMAMResume`으로 각각 대체된 애플리케이션에서 계속 사용할 수 있습니다.

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```

대체 작업을 하지 않은 경우 대체 작업을 수행할 때까지 다음과 같은 컴파일 오류가 발생할 수 있습니다.
* [컴파일러 오류 CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). 이 오류는 일반적으로 이 양식 ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``에 표시됩니다.
이는 Remapper가 Xamarin 클래스의 상속을 수정할 때 특정 함수가 `sealed`로 만들어지고 대신 새 MAM 변형이 추가되어 재정의되기 때문에 예상됩니다.
* [컴파일러 오류 CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): 이 오류는 일반적으로 이 양식 ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``에 표시됩니다. Remapper가 일부 Xamarin 클래스의 상속을 변경하면 특정 멤버 함수가 `public`으로 변경됩니다. 이러한 함수 중 하나를 재정의하는 경우 해당 재정의에 대한 액세스 한정자도 `public`으로 변경해야 합니다.

> [!NOTE]
> Remapper는 Visual Studio에서 IntelliSense 자동 완성을 위해 사용하는 종속성을 다시 작성합니다. 따라서 IntelliSense에 대해 Remapper가 추가되면 프로젝트를 다시 로드하고 다시 빌드해야 변경 내용을 올바르게 인식할 수 있습니다.

#### <a name="troubleshooting"></a>문제 해결
* 응용 프로그램을 시작할 때 빈 화면이 표시 되 면 주 스레드에서 탐색 호출을 강제로 실행 해야 할 수 있습니다.
* Intune SDK Xamarin 바인딩은 MvvmCross와 Intune MAM 클래스 간의 충돌로 인해 MvvmCross과 같은 플랫폼 간 프레임 워크를 사용 하는 앱을 지원 하지 않습니다. 앱을 일반 Xamarin.ios로 이동한 후 일부 고객은 통합에 성공 했을 수 있지만 MvvmCross를 사용 하는 앱 개발자를 위한 명시적 지침 또는 플러그 인은 제공 하지 않습니다.

### <a name="company-portal-app"></a>회사 포털 앱
Intune SDK Xamarin 바인딩은 장치에 [회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android 앱이 있는지를 사용 하 여 앱 보호 정책을 사용 하도록 설정 합니다. 회사 포털이 Intune 서비스에서 앱 보호 정책을 검색합니다. 앱을 초기화할 때 정책과 회사 포털에서 해당 정책을 적용하는 코드를 로드합니다. 사용자에 게 로그인 할 필요가 없습니다.

> [!NOTE]
> 회사 포털 앱이 **Android** 디바이스에 없으면 Intune 관리 앱은 Intune 앱 보호 정책을 지원하지 않는 일반 앱처럼 작동합니다.

디바이스 등록 없이 앱 보호를 사용하기 위해 사용자가 회사 포털 앱을 통해 디바이스를 등록할 필요가 _**없습니다**_ .

### <a name="sample-applications"></a>샘플 애플리케이션
Xamarin.ios 및 Xamarin.ios 앱에서 MAM 기능을 강조 표시 하는 샘플 응용 프로그램은 [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps)에서 사용할 수 있습니다.

## <a name="support"></a>Support
anization is an existing Intune customer, please work with your Microsoft support repr조직이 기존 Intune 고객인 경우 Microsoft 지원 담당자에게 문의해 지원 티켓을 열고 [GitHub 문제 페이지](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)에서 문제를 만듭니다. 가능 하면 즉시 도와 드리겠습니다. 
