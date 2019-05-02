---
title: Microsoft Intune 앱 SDK Xamarin 바인딩
description: Intune 앱 SDK Xamarin 바인딩은 Xamarin에 내장된 iOS 및 Android 앱의 Intune 앱 보호 정책을 사용하도록 설정합니다.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: d42fab929d6fa3e7fbaed8e9557573ebbaa1f3ad
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292353"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune 앱 SDK Xamarin 바인딩

> [!NOTE]
> 먼저 지원되는 각 플랫폼에서 통합을 준비하는 방법을 설명하는 [Intune 앱 SDK 시작](app-sdk-get-started.md) 문서를 읽어보는 것이 좋습니다.

## <a name="overview"></a>개요
[Intune 앱 SDK Xamarin 바인딩](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)은 Xamarin에 내장된 iOS 및 Android 앱의 [Intune 앱 보호 정책](app-protection-policy.md)을 사용하도록 설정합니다. 개발자는 바인딩을 사용하여 Intune 앱 보호 기능을 Xamarin 기반 앱에 손쉽게 빌드할 수 있습니다.

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

SDK가 작동하려면 [인증](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) 및 조건부 시작 시나리오를 위한 [ADAL(Active Directory 인증 라이브러리)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)이 필요하며, 이 경우 앱에 [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/)를 구성해야 합니다. 

애플리케이션이 ADAL 또는 MSAL을 사용하도록 이미 구성되어 있고, Azure Active Directory를 사용하여 인증하는 데 사용되는 고유한 사용자 지정 클라이언트 ID가 있는 경우 Intune MAM(모바일 애플리케이션 관리) 서비스에 대한 Xamarin 앱 사용 권한을 부여하는 단계를 따릅니다. [Intune SDK 시작 가이드](app-sdk-get-started.md)의 "[앱에 Intune 앱 보호 서비스에 대한 액세스 권한 부여](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)" 섹션의 지침을 사용합니다.

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>iOS 모바일 앱에서 Intune 앱 보호 정책을 사용하도록 설정
1. [Microsoft.Intune.MAM.Xamarin.iOS NuGet 패키지](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)를 Xamarin.iOS 프로젝트에 추가합니다.
2.  Intune 앱 SDK를 iOS 모바일 앱에 통합하는 데 필요한 일반적인 단계를 따르세요. [iOS용 Intune 앱 SDK 개발자 가이드](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)의 통합 지침 3단계에서 시작할 수 있습니다. 이 도구가 Microsoft.Intune.MAM.Xamarin.iOS 패키지에 포함되어 있고 빌드 시 자동으로 실행되므로 IntuneMAMConfigurator를 실행하는 해당 섹션의 마지막 단계를 건너뛸 수 있습니다.
    **중요**: 앱에 키 집합 공유를 사용하도록 설정하는 작업이 Visual Studio와 Xcode에서 약간 다릅니다. 앱의 Entitlements plist를 열고 "키 집합 사용" 옵션이 설정되었으며 해당 섹션에 적절한 키 집합 공유 그룹이 추가되어 있는지 확인합니다. 그런 다음 적절한 모든 구성/플랫폼 조합에 대해 프로젝트 "iOS 번들 서명" 옵션의 "사용자 지정 자격" 필드에 Entitlements plist가 지정되어 있는지 확인합니다.
3.  바인딩을 추가하고 앱을 제대로 구성하면 앱에서 Intune SDK API를 사용할 수 있습니다. 이렇게 하려면 다음 네임스페이스를 포함해야 합니다.

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. 앱 보호 정책을 받기 시작하려면 앱이 Intune MAM 서비스에 등록되어 있어야 합니다. 앱이 사용자 인증을 위해 [Azure Active Directory 인증 라이브러리](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory)(ADAL) 또는 [Microsoft 인증 라이브러리](https://www.nuget.org/packages/Microsoft.Identity.Client)(MSAL)를 사용하지 않고 Intune SDK에서 인증을 처리하도록 하려는 경우, 앱은 사용자의 UPN을 IntuneMAMEnrollmentManager의 LoginAndEnrollAccount 메서드에 제공해야 합니다.
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      호출 시 사용자의 UPN을 알 수 없는 경우 앱이 null에 전달할 수 있습니다. 이 경우 사용자에게 이메일 주소와 암호를 모두 입력하라는 메시지가 표시됩니다.
      
      앱이 이미 ADAL 또는 MSAL을 사용하여 사용자를 인증하는 경우 앱과 Intune SDK 간에 SSO(single sign-on) 환경을 구성할 수 있습니다. 먼저 iOS용 Intune Xamarin Bindings(com.microsoft.adalcache)에서 사용하는 것과 동일한 키체인 액세스 그룹에 토큰을 저장하도록 ADAL/MSAL을 구성해야 합니다. ADAL의 경우 [AuthenticationContext의 KeychainSecurityGroup 속성을 설정](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Token-cache-serialization#enable-token-cache-sharing-across-ios-applications)하여 이 작업을 수행할 수 있습니다. MSAL의 경우 [PublicClientApplication의 KeychainSecurityGroup 속성을 설정](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/msal-net-2-released#you-can-now-enable-sso-between-adal-and-msal-apps-on-xamarinios)해야 합니다. 그런 다음, 앱과 함께 Intune SDK에서 사용하는 기본 AAD 설정을 재정의해야 합니다. [iOS용 Intune 앱 SDK 개발자 가이드](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)에 설명된 대로 앱의 Info.plist에 있는 IntuneMAMSettings 사전을 통해 재정의하거나, IntuneMAMPolicyManager 인스턴스의 AAD 재정의 속성을 사용할 수 있습니다. Info.plist 접근 방법은 ADAL 설정이 정적인 애플리케이션에 권장되고, 재정의 속성은 런타임에 이러한 값을 확인하는 애플리케이션에 권장됩니다. 모든 SSO 설정이 구성되면 앱은 성공적으로 인증된 후 사용자의 UPN을 IntuneMAMEnrollmentManager의 RegisterAndEnrollAccount 메서드에 제공해야 합니다.
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      앱은 IntuneMAMEnrollmentDelegate의 하위 클래스에서 EnrollmentRequestWithStatus 메서드를 구현하고 IntuneMAMEnrollmentManager의 대리자 속성을 해당 클래스의 인스턴스로 설정하여 등록 시도의 결과를 확인할 수 있습니다. 예를 들어 [샘플 Xamarin.iOS 애플리케이션](https://github.com/msintuneappsdk/sample-intune-xamarin-ios)을 참조하세요.

      등록이 성공하면 앱은 다음 속성을 쿼리하여 등록된 계정의 UPN(이전에 알 수 없는 경우)을 확인할 수 있습니다. 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> iOS용 리매퍼가 없습니다. Xamarin.Forms 앱에 통합하는 것은 일반 Xamarin.iOS 프로젝트와 동일합니다. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Android 모바일 앱에서 Intune 앱 보호 정책을 사용하도록 설정

1. [Microsoft.Intune.MAM.Xamarin.Android NuGet 패키지](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)를 Xamarin.Android 프로젝트에 추가합니다.
    1. Xamarin.Forms 앱을 추가 합니다 [Microsoft.Intune.MAM.Remapper.Tasks NuGet 패키지](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) 를 Xamarin.Android 프로젝트도 합니다. 
2. 에 대 한 필요한 일반적인 단계를 따릅니다 [Intune 앱 SDK를 통합](app-sdk-android.md) 에 대 한 자세한 내용은이 문서를 참조 하는 동안 Android 모바일 앱입니다.

### <a name="xamarinandroid-integration"></a>Xamarin.Android 통합

Intune 앱 SDK를 통합 하는 것에 대 한 전체 개요에서 찾을 수 있습니다 합니다 [Android 개발자 가이드에 대 한 Microsoft Intune 앱 SDK](app-sdk-android.md)합니다. 다음 섹션에서는 Java에서 네이티브 Android 앱을 개발 하 고 Xamarin 앱 개발에 대 한 구현 간의 차이점을 강조 표시 하는 가이드를 통해 읽고 Intune 앱 SDK Xamarin 앱과 통합 하는 대로 C#입니다. 이 섹션에서는 추가으로 처리할지 및 전체에서 설명서를 읽고의 대 안으로 작동할 수 없습니다.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[이름이 변경된 메서드](app-sdk-android.md#renamed-methods)
대부분의 경우, Android 클래스에서 사용할 수 있는 메서드가 MAM 대체 클래스에서 최종본으로 표시되어 있습니다. 이 경우 MAM 대체 클래스는 대신 재정의할 유사한 이름의 메서드(접미사 `MAM`이 붙음)를 제공합니다. 예를 들어 `OnCreate()`를 재정의하고 `base.OnCreate()`를 호출하는 대신 `MAMActivity`에서 파생하는 경우 `Activity`는 `OnMAMCreate()`를 재정의하고 `base.OnMAMCreate()`를 호출해야 합니다.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[MAM 애플리케이션](app-sdk-android.md#mamapplication)
앱을 정의 해야 합니다는 `Android.App.Application` 클래스에서 상속 되는 `MAMApplication`합니다. 서브 클래스가 `[Application]` 특성으로 올바르게 데코레이팅되고 `(IntPtr, JniHandleOwnership)` 생성자를 재정의하는지 확인입니다.
```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```
> [!NOTE]
> MAM Xamarin 바인딩 사용 하 여 문제에는 응용 프로그램 디버그 모드에서 배포 하는 경우 충돌을 발생할 수 있습니다. 이 문제를 해결 합니다 `Debuggable=false` 특성에 추가 되어야 합니다는 `Application` 클래스 및 `android:debuggable="true"` 수동으로 설정 된 경우 매니페스트에서 플래그를 제거 해야 합니다.

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
예: 장치 또는 클라우드 스토리지에 저장이 허용되는지 확인
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

에 대 한 `Xamarin.Forms` 제공 하는 응용 프로그램을 `Microsoft.Intune.MAM.Remapper` 삽입 하 여 MAM 클래스 대체를 자동으로 수행 하는 패키지 `MAM` 의 자주 사용 되는 클래스 계층 구조에 클래스 `Xamarin.Forms` 클래스입니다. 

> [!NOTE]
> Xamarin.Forms 통합 또한 위에서 설명한 Xamarin.Android 통합을 수행 됩니다.

프로젝트에는 Remapper 추가 되 면 MAM 해당 하는 대체를 수행 해야 합니다. 예를 들어 `FormsAppCompatActivity` 하 고 `FormsApplicationActivity` 계속 하려면 재정의 제공 하는 응용 프로그램에서 사용할 수 있습니다 `OnCreate` 및 `OnResume` MAM 클래스로 바뀝니다 `OnMAMCreate` 및 `OnMAMResume` 각각.

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
대체 되지 경우 대체를 변경할 때까지 다음 컴파일 오류가 발생할 수 있습니다.
* [컴파일러 오류 CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). 이 오류는 일반적으로 이 양식 ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``에 표시됩니다.
이는 Remapper가 Xamarin 클래스의 상속을 수정할 때 특정 함수가 `sealed`로 만들어지고 대신 새 MAM 변형이 추가되어 재정의되기 때문에 예상됩니다.
* [컴파일러 오류 CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507):이 오류는 일반적으로이 폼에 표시 됩니다 ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``합니다. Remapper가 일부 Xamarin 클래스의 상속을 변경하면 특정 멤버 함수가 `public`으로 변경됩니다. 이러한 함수를 재정의 하는 경우 이러한 액세스 한정자 재정의를 변경 해야 합니다 `public` 도 합니다.

> [!NOTE]
> Remapper IntelliSense 자동 완성을 위해 Visual Studio를 사용 하는 종속성을 다시 작성 합니다. 따라서 다시 로드 하 고 변경 내용을 제대로 인식 하는 IntelliSense에는 Remapper 추가 되 면 프로젝트를 다시 작성 해야 합니다.

## <a name="support"></a>Support
조직이 기존 Intune 고객인 경우 Microsoft 지원 담당자에게 문의해 지원 티켓을 열고 [Github 문제 페이지에서](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) 문제를 만들면 가능한 한 빨리 도움을 제공할 수 있습니다. 
