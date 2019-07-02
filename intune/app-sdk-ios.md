---
title: iOS용 Microsoft Intune 앱 SDK 개발자 가이드
description: iOS용 Microsoft Intune 앱 SDK를 사용하면 네이티브 iOS 앱에 Intune 앱 보호 정책(APP 또는 MAM 정책이라고도 함)을 통합할 수 있습니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4877920821b2471f752f9fdb8941e87576d937ba
ms.sourcegitcommit: 9c06d8071b9affeda32e367bfe85d89bc524ed0b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413854"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>iOS용 Microsoft Intune 앱 SDK 개발자 가이드

> [!NOTE]
> 지원되는 각 플랫폼에서 통합을 준비하는 방법을 설명하는 [Intune 앱 SDK 시작 가이드](app-sdk-get-started.md) 문서를 읽어보는 것이 좋습니다.

iOS용 Microsoft Intune 앱 SDK를 사용하면 네이티브 iOS 앱에 Intune 앱 보호 정책(APP 또는 MAM 정책이라고도 함)을 통합할 수 있습니다. MAM 지원 애플리케이션은 Intune 앱 SDK와 통합된 애플리케이션입니다. IT 관리자는 Intune에서 앱을 적극적으로 관리할 때 모바일 앱에 앱 보호 정책을 배포할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

* Xcode 9 이상이 설치된 OS X 10.8.5 이상의 Mac OS 컴퓨터에서 실행해야 합니다.

* 앱은 iOS 10 이상을 대상으로 해야 합니다.

* [iOS용 Intune 앱 SDK 사용 조건](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf)을 확인하세요. 기록을 위해 사용 조건의 사본을 인쇄하여 보관하세요. iOS용 Intune 앱 SDK를 다운로드하여 이러한 사용 조건에 동의합니다.  동의하지 않는 경우 소프트웨어를 사용하지 마세요.

* [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)에서 iOS용 Intune 앱 SDK 파일을 다운로드합니다.

## <a name="whats-in-the-sdk-repository"></a>SDK 저장소의 새로운 기능

관련 없는 Swift 코드를 포함 하거나 10.2 이전 버전의 Xcode 사용 하 여 컴파일되는 앱/extensions에는 다음 파일이 같습니다.

* **IntuneMAM.framework**: Intune 앱 SDK 프레임워크입니다. Intune 클라이언트 응용 프로그램 관리를 사용 하도록 설정 하려면 앱/확장에는이 프레임 워크를 연결 하는 것이 좋습니다. 그러나 일부 개발자는 정적 라이브러리의 성능 이점을 원할 수 있습니다. 다음을 참조하세요.

* **libIntuneMAM.a**: Intune 앱 SDK 정적 라이브러리입니다. 개발자는 연결 프레임 워크는 대신 정적 라이브러리를 선택할 수 있습니다. 정적 라이브러리는 앱/확장 빌드 시 이진에 직접 포함 하기 때문에 정적 라이브러리를 사용 하 여 시작 시간이 성능상의 이점이 있습니다. 그러나 앱에 통합 하는 것 보다 복잡 한 프로세스입니다. 앱에 정적 라이브러리를 앱에 연결 하는 모든 확장을 포함 하는 경우 더 큰 앱 번들 크기를 확장 하면 정적 라이브러리에 포함 될 각 앱/확장 이진. 프레임 워크를 사용 하 여, 앱 및 확장 작은 앱 크기가 동일한 Intune SDK 이진을 공유할 수 있습니다.

* **IntuneMAMResources.bundle**: SDK에서 사용하는 리소스가 포함된 리소스 번들입니다. 리소스 번들은 정적 라이브러리 (libIntuneMAM.a)를 통합 하는 앱에만 필요 합니다.

다음 파일은 Swift 코드를 포함 하 고 Xcode 10.2 +를 사용 하 여 컴파일되는 앱/extensions에 관련:

* **IntuneMAMSwift.framework**: The Intune App SDK Swift 프레임 워크입니다. 이 프레임 워크 api 앱을 호출 하는 모든 헤더를 포함 합니다. Intune 클라이언트 응용 프로그램 관리를 사용 하 여 app/extensions에이 프레임 워크를 연결 합니다.

* **IntuneMAMSwiftStub.framework**: Intune 앱 SDK Swift 스텁 프레임 워크입니다. 앱/extensions에 연결 해야 하는 IntuneMAMSwift.framework의 필수 종속성입니다.


다음 파일은 모든 앱/확장 관련:

* **IntuneMAMConfigurator**: Intune 관리에 대 한 최소 필요한 변경 작업을 사용 하 여 앱 또는 확장의 Info.plist를 구성 하는 데 사용 합니다. 앱 또는 확장 기능에 따라 Info.plist를 추가 수동 변경 하는 것이 해야 합니다.

* **헤더**: 공용 Intune 앱 SDK API를 표시합니다. 이러한 헤더는 IntuneMAM/IntuneMAMSwift 프레임 워크 내에 포함 되므로 프레임 워크 중 하나를 사용 하는 개발자가 프로젝트에 헤더를 수동으로 추가할 필요가 없습니다. 정적 라이브러리 (libIntuneMAM.a)에 대해 연결을 선택 하는 개발자가 수동으로 해당 프로젝트에서 이러한 헤더를 포함 해야 합니다.

다음 헤더 파일에는 Intune 앱 SDK에서 개발자에게 제공하는 API, 데이터 형식 및 프로토콜이 포함되어 있습니다.

    * IntuneMAMAppConfig.h
    * IntuneMAMAppConfigManager.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMDefs.h
    * IntuneMAMEnrollmentDelegate.h
    * IntuneMAMEnrollmentManager.h
    * IntuneMAMEnrollmentStatus.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMLogger.h
    * IntuneMAMPolicy.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMPolicyManager.h
    * IntuneMAMVersionInfo.h

개발자는 IntuneMAM.h만 가져오면 이전 헤더 전체 콘텐츠를 사용할 수 있습니다.


## <a name="how-the-intune-app-sdk-works"></a>Intune 앱 SDK의 작동 방식

iOS용 Intune 앱 SDK의 목적은 최소한의 코드 변경으로 iOS 애플리케이션에 관리 기능을 추가하는 것입니다. 모바일 애플리케이션의 일관성과 안정성에 영향을 주지 않으면서 코드 변경을 적게 하고, 출시에 필요한 시간을 단축할 수 있습니다.


## <a name="build-the-sdk-into-your-mobile-app"></a>모바일 앱으로 SDK 빌드

Intune 앱 SDK를 사용하려면 다음 단계를 따르세요.

1. **옵션 1-(권장) 프레임 워크**: Xcode 10.2 +를 사용 하는 앱/확장 Swift 코드를 포함 하는 경우 연결할 `IntuneMAMSwift.framework` 및 `IntuneMAMSwiftStub.framework` 대상: 끌어서 `IntuneMAMSwift.framework` 및 `IntuneMAMSwiftStub.framework` 에 **포함 이진 파일** 프로젝트 대상의 목록입니다.

    링크이 고, 그렇지 `IntuneMAM.framework` 대상: 끌어서 `IntuneMAM.framework` 에 **포함 된 이진 파일** 프로젝트 대상의 목록입니다.

   > [!NOTE]
   > 프레임워크를 사용하는 경우 앱을 앱 스토어에 제출하기 전에 수동으로 범용 프레임워크에서 시뮬레이터 아키텍처를 제거해야 합니다. 자세한 내용은 [앱 스토어에 앱 제출](#submit-your-app-to-the-app-store)을 참조하세요.

   **옵션 2-정적 라이브러리**:이 옵션은만 사용할 수 없는 Swift 코드를 포함 하거나 Xcode를 사용 하 여 빌드한 앱/확장에 대 한 < 10.2 합니다. `libIntuneMAM.a` 라이브러리에 연결합니다. 프로젝트 대상의 **연결된 프레임워크 및 라이브러리** 목록으로 `libIntuneMAM.a` 라이브러리를 끌어옵니다.

    ![Intune 앱 SDK iOS - 연결된 프레임워크 및 라이브러리](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    `{PATH_TO_LIB}`를 Intune 앱 SDK 위치로 대체하여 `-force_load {PATH_TO_LIB}/libIntuneMAM.a`를 다음 중 하나에 추가합니다.
   * 프로젝트의 `OTHER_LDFLAGS` 빌드 구성 설정
   * Xcode UI의 **기타 링커 플래그**

     > [!NOTE]
     > `PATH_TO_LIB`를 찾으려면 `libIntuneMAM.a` 파일을 선택하고 **파일** 메뉴에서 **정보 가져오기**를 선택합니다. **정보** 창의 **일반** 섹션에서 **위치** 정보(경로)를 복사하여 붙여넣습니다.

     **빌드 단계** 내의 **번들 리소스 복사** 아래로 리소스 번들을 끌어 프로젝트에 `IntuneMAMResources.bundle` 리소스 번들을 추가합니다.

     ![Intune 앱 SDK iOS - 번들 리소스 복사](./media/intune-app-sdk-ios-copy-bundle-resources.png)
     
2. Swift에서 Intune api를 호출 하는 경우에 Objective-c 브리징 헤더를 통해 필수 Intune SDK 헤더 앱/확장을 가져와야 합니다. 앱/확장 Objective-c 브리징 헤더를 이미 포함 되어 있지 않으면를 통해 하나를 지정할 수 있습니다 합니다 `SWIFT_OBJC_BRIDGING_HEADER` 빌드 구성 설정이 나 Xcode UI **Objective-c 브리징 헤더** 필드입니다. 브리징 헤더에는 코드는 다음과 같아야 합니다.

   ```objc
      #import <IntuneMAMSwift/IntuneMAM.h>
   ```
   
   이렇게 하면 모든 Intune SDK Api 사용 가능한 모든 Swift 소스 파일에서 앱/확장 합니다. 
   
    > [!NOTE]
    > * 브리지 특정 Intune SDK 헤더만 포괄적인 IntuneMAM.h 보다는 Swift 하도록 선택할 수 있습니다.
    > * 헤더 파일의 경로 통합 하는 프레임 워크/정적 라이브러리에 따라 달라질 수 있습니다.
    > * Intune SDK Api를 모듈 가져오기 문을 통해 Swift에서 사용할 수 있도록 (예: IntuneMAMSwift 가져오기) 현재 지원 되지 않습니다. Objective-c 브리징 헤더를 사용 하는 것이 좋습니다.
    
3. 프로젝트에 다음 iOS 프레임워크를 추가합니다.  
    * MessageUI.framework  
    * Security.framework  
    * MobileCoreServices.framework  
    * SystemConfiguration.framework  
    * libsqlite3.tbd  
    * libc++.tbd  
    * ImageIO.framework  
    * LocalAuthentication.framework  
    * AudioToolbox.framework  
    * QuartzCore.framework  
    * WebKit.framework

4. 각 프로젝트 대상에서 **기능**을 클릭하고 **키 집합 공유** 스위치를 사용하도록 설정하여 키 집합 공유를 사용하도록 설정합니다(아직 설정되지 않은 경우). 다음 단계를 진행하려면 키 집합 공유가 필요합니다.

   > [!NOTE]
   > 프로비전 프로필이 새로운 키 집합 공유 값을 지원해야 합니다. 키 집합 액세스 그룹이 와일드카드 문자를 지원해야 합니다. 이를 확인하려면 텍스트 편집기에서 .mobileprovision 파일을 열고 **keychain-access-groups**를 검색한 다음 와일드카드 문자가 있는지 확인합니다. 예를 들면 다음과 같습니다.
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

5. 키 집합 공유를 사용하도록 설정한 후 단계에 따라 Intune 앱 SDK에서 데이터를 저장할 별도의 액세스 그룹을 만듭니다. UI를 사용하거나 자격 파일을 사용하여 키 집합 액세스 그룹을 만들 수 있습니다. UI를 사용하여 키 집합 액세스 그룹을 만드는 경우 다음 단계를 수행해야 합니다.

     a. 모바일 앱에 키 집합 액세스 그룹이 정의되어 있지 않으면 앱의 번들 ID를 **첫 번째** 그룹으로 추가합니다.
    
    b. 공유 키 집합 그룹 `com.microsoft.intune.mam`을 기존 액세스 그룹에 추가합니다. Intune 앱 SDK에서 이 액세스 그룹을 사용하여 데이터를 저장합니다.
    
    c. 기존 액세스 그룹에 `com.microsoft.adalcache`를 추가합니다.
    
        ![Intune App SDK iOS: keychain sharing](./media/intune-app-sdk-ios-keychain-sharing.png)
    
    d. 위에 표시된 Xcode UI를 사용하지 않고 직접 자격 파일을 편집하여 키 집합 액세스 그룹을 만드는 경우 키 집합 액세스 그룹 앞에 `$(AppIdentifierPrefix)`를 추가합니다(Xcode는 이를 자동으로 처리함). 예를 들면 다음과 같습니다.
    
        - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
        - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
        > [!NOTE]
        > An entitlements file is an XML file that is unique to your mobile application. It is used to specify special permissions and capabilities in your iOS app. If your app did not previously have an entitlements file, enabling keychain sharing (step 3) should have caused Xcode to generate one for your app. Ensure the app's bundle ID is the first entry in the list.

6. 앱이 `UIApplication canOpenURL`에 전달하는 각 프로토콜을 앱 Info.plist 파일의 `LSApplicationQueriesSchemes` 배열에 포함합니다. 다음 단계로 진행하기 전에 변경 내용을 저장해야 합니다.

7. 앱에서 FaceID를 아직 사용하지 않는 경우 [NSFaceIDUsageDescription Info.plist 키](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75)가 기본 메시지로 구성되었는지 확인합니다. 이는 iOS가 앱이 FaceID를 어떻게 사용하려고 하는지 사용자에게 알려주기 위해 필요합니다. Intune 앱 보호 정책 설정을 사용하면 IT 관리자가 구성할 때 FaceID를 앱 액세스 방법으로 사용할 수 있습니다.

8. [SDK 리포지토리](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)에 포함된 IntuneMAMConfigurator 도구를 사용하여 앱의 Info.plist 구성을 완료합니다. 도구에는 다음과 같은 세 개의 매개 변수가 있습니다.

   |속성|사용 방법|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (선택 사항) `<Path to the output plist>` |

'-o' 매개 변수를 지정하지 않으면 입력 파일이 현재 위치에서 수정됩니다. 이 도구는 멱등적이며 앱의 Info.plist 또는 자격을 변경할 때마다 다시 실행해야 합니다. 또한 Info.plist 구성 요구 사항이 최신 릴리스에서 변경된 경우 Intune SDK를 업데이트할 때 최신 버전의 도구를 다운로드하여 실행해야 합니다.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Azure ADAL(Active Directory 인증 라이브러리) 구성

Intune 앱 SDK는 해당 인증 및 조건부 시작 시나리오에 [Azure Active Directory 인증 라이브러리](https://github.com/AzureAD/azure-activedirectory-library-for-objc)를 사용합니다. 또한 ADAL을 사용하여 디바이스 등록 시나리오가 없는 관리를 위해 MAM 서비스에 사용자 ID를 등록합니다.

일반적으로 ADAL에서는 앱이 AAD(Azure Active Directory)에 등록하고 고유 ID(클라이언트 ID) 및 기타 ID을 받아야 앱에 부여된 토큰의 보안이 보장됩니다. 따로 지정한 경우가 아니면, Intune 앱 SDK는 Azure AD에 연결할 때 기본 등록 값을 사용합니다.  

앱에서 이미 ADAL을 사용하여 사용자를 인증하는 경우 기존 등록 값을 사용하고 Intune 앱 SDK 기본값을 재정의해야 합니다. 이렇게 하면 사용자에게 인증 메시지가 두 번(Intune 앱 SDK를 통해 한 번, 앱에서 한 번) 나타나지 않습니다.

앱이 마스터 분기에 있는 [ADAL의 최신 버전](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases)에 연결하는 것이 좋습니다. 현재 Intune 앱 SDK에서는 조건부 액세스가 필요한 앱을 지원하기 위해 ADAL 브로커 분기를 사용합니다. 따라서 이러한 앱은 Microsoft Authenticator 앱에 종속됩니다. 그러나 SDK는 ADAL의 마스터 분기와 계속 호환됩니다. 앱에 적합한 분기를 사용합니다.

### <a name="link-to-adal-binaries"></a>ADAL 바이너리에 연결

ADAL 바이너리에 앱을 연결하려면 다음 단계를 수행합니다.

1. GitHub에서 [Objective-C용 Azure ADAL(Active Directory 인증 라이브러리)](https://github.com/AzureAD/azure-activedirectory-library-for-objc)을 다운로드한 다음 Git 하위 모듈 또는 CocoaPods를 사용하여 ADAL을 다운로드하는 방법에 관한 [지침](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download)을 따릅니다.

2. ADAL 프레임워크(옵션 1) 또는 정적 라이브러리(옵션 2)를 프로젝트에 추가합니다.

3. 앱에 키 집합 액세스 그룹이 정의되어 있지 않으면 앱의 번들 ID를 첫 번째 그룹으로 추가합니다.

4. 키 집합 액세스 그룹에 `com.microsoft.adalcache`를 추가하여 ADAL SSO(Single Sign-On)를 사용하도록 설정합니다.

5. ADAL 공유 캐시 키 집합 그룹을 명시적으로 설정하는 경우 이를 `<appidprefix>.com.microsoft.adalcache`로 설정해야 합니다. 이를 재정의하지 않으면 ADAL에서 자동으로 설정합니다. 사용자 지정 키 집합 그룹을 지정하여 `com.microsoft.adalcache`를 바꾸려면 IntuneMAMSettings 아래의 Info.plist 파일에 `ADALCacheKeychainGroupOverride` 키를 사용하여 지정하세요.

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Intune 앱 SDK에 대한 ADAL 설정 구성

앱에서 이미 인증에 대해 ADAL을 사용하고 고유한 ADAL 설정이 있는 경우 Intune 앱 SDK에서 Azure Active Directory에 대한 인증 중 동일한 설정을 사용하도록 할 수 있습니다. 이렇게 하면 앱에서 사용자에게 인증 메시지를 두 번 표시하지 않습니다. 다음 설정을 입력하는 방법은 [Intune 앱 SDK에 대한 설정 구성](#configure-settings-for-the-intune-app-sdk)을 참조하세요.  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

앱에서 이미 ADAL를 사용하는 경우 다음 구성이 필요합니다.

1. 프로젝트 Info.plist 파일의 **IntuneMAMSettings** 사전에서 `ADALClientId` 키 이름으로 ADAL 호출에 사용할 클라이언트 ID를 지정합니다.

2. 또한 **IntuneMAMSettings** 사전에서 `ADALAuthority` 키 이름으로 Azure AD 기관을 지정합니다.

3. 또한 **IntuneMAMSettings** 사전에서 `ADALRedirectUri` 키 이름으로 ADAL 호출에 사용할 리디렉션 URI를 지정합니다. 또는 애플리케이션의 리디렉션 URI가 `scheme://bundle_id` 형식인 경우 `ADALRedirectScheme`을 대신 지정할 수 있습니다.

앱에서 런타임 시 이러한 Azure AD 설정을 재정의할 수도 있습니다. 이 작업을 수행하려면 `IntuneMAMPolicyManager` 인스턴스의 `aadAuthorityUriOverride`, `aadClientIdOverride`, `aadRedirectUriOverride` 속성을 설정하면 됩니다.

4. APP(앱 보호 정책) 서비스의 iOS 앱 권한을 부여하는 단계를 따라야 합니다. 앱에 Intune 앱 보호 서비스에 대한 액세스 권한 부여(선택 사항)에서 [Intune SDK 시작 가이드](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration)의 지침을 따릅니다.  

> [!NOTE]
> Info.plist 접근 방법은 정적이며 런타임에 확인할 필요가 없는 모든 설정에 권장됩니다. `IntuneMAMPolicyManager` 속성에 할당된 값이 Info.plist에 지정된 해당 값보다 우선하며, 앱을 다시 시작한 후에도 유지됩니다. 사용자가 등록 취소되거나 값이 지워지거나 변경될 때까지 SDK는 계속 이 값을 정책 체크인에 사용합니다.

### <a name="if-your-app-does-not-use-adal"></a>앱에서 ADAL을 사용하지 않는 경우

위에서 언급했듯이 Intune 앱 SDK는 해당 인증 및 조건부 시작 시나리오에 [Azure Active Directory 인증 라이브러리](https://github.com/AzureAD/azure-activedirectory-library-for-objc)를 사용합니다. 또한 ADAL을 사용하여 디바이스 등록 시나리오가 없는 관리를 위해 MAM 서비스에 사용자 ID를 등록합니다. **앱에서 고유한 인증 메커니즘에 ADAL을 사용하지 않는 경우** Intune 앱 SDK는 ADAL 매개 변수에 대한 기본값을 제공하며, Azure AD에 대한 인증을 처리합니다. 위에 나열된 ADAL 설정에 대한 값을 지정할 필요가 없습니다. 앱에서 사용하는 인증 메커니즘이 있는 경우 ADAL 프롬프트의 맨 위에 표시됩니다. 

## <a name="configure-settings-for-the-intune-app-sdk"></a>Intune 앱 SDK에 대한 설정 구성

애플리케이션의 Info.plist 파일에 포함된 **IntuneMAMSettings** 사전을 사용하여 Intune 앱 SDK를 설정 및 구성할 수 있습니다. IntuneMAMSettings 사전이 Info.plist 파일에 표시되지 않으면, 사전을 만들어야 합니다.

IntuneMAMSettings 사전에서 다음과 같이 지원되는 설정을 사용하여 Intune 앱 SDK를 구성할 수 있습니다.

이러한 설정 중 일부는 이전 섹션에서 설명되었을 수도 있으며 일부 앱에 적용되지 않는 설정도 있습니다.

Setting  | 유형  | 정의 | 필수 여부
--       |  --   |   --       |  --
ADALClientId  | 문자열  | 앱의 Azure AD 클라이언트 식별자입니다. | 앱에서 ADAL을 사용하는 경우 필수입니다. |
ADALAuthority | 문자열 | 사용 중인 앱의 Azure AD 기관입니다. AAD 계정이 구성된 사용자 고유의 환경을 사용해야 합니다. | 앱에서 ADAL을 사용하는 경우 필수입니다. 이 값이 없는 경우 Intune 기본값이 사용됩니다.|
ADALRedirectUri  | 문자열  | 앱의 Azure AD 리디렉션 URI입니다. | 앱에서 ADAL을 사용하는 경우 ADALRedirectUri 또는 ADALRedirectScheme은 필수입니다.  |
ADALRedirectScheme  | 문자열  | 앱의 Azure AD 리디렉션 스키마입니다. 애플리케이션의 리디렉션 URI가 `scheme://bundle_id` 형식인 경우 ADALRedirectUri 대신 이 설정을 사용할 수 있습니다. | 앱에서 ADAL을 사용하는 경우 ADALRedirectUri 또는 ADALRedirectScheme은 필수입니다. |
ADALLogOverrideDisabled | 부울  | SDK에서 모든 ADAL 로그(있는 경우 앱에서의 ADAL 호출 포함)를 해당 로그 파일로 라우팅할지 여부를 지정합니다. 기본값은 NO입니다. 앱이 해당 ADAL 로그 콜백을 설정하려는 경우 YES로 설정합니다. | 선택 사항입니다. |
ADALCacheKeychainGroupOverride | 문자열  | "com.microsoft.adalcache" 대신 ADAL 캐시에 사용할 키 집합 그룹을 지정합니다. 이 설정에는 app-id 접두사가 없습니다. 이 접두사는 런타임에 제공된 문자열에 추가됩니다. | 선택 사항입니다. |
AppGroupIdentifiers | 문자열 배열  | 앱 자격 com.apple.security.application-groups 섹션의 앱 그룹 배열입니다. | 앱이 애플리케이션 그룹을 사용하는 경우에 필요합니다. |
ContainingAppBundleId | 문자열 | 확장의 포함 애플리케이션 번들 ID를 지정합니다. | iOS 확장에 필요합니다. |
DebugSettingsEnabled| 부울 | YES로 설정할 경우 설정 번들 내의 테스트 정책을 적용할 수 있습니다. 애플리케이션은 이 설정이 사용하도록 설정된 상태로 제공되어서는 *안 됩니다*. | 선택 사항입니다. 기본값은 no입니다.|
MainNibFile <br> MainNibFile~ipad  | 문자열  | 이 설정에는 애플리케이션의 주 nib 파일 이름이 있어야 합니다.  | 애플리케이션이 해당 Info.plist에서 MainNibFile을 정의하는 경우에 필수입니다. |
MainStoryboardFile <br> MainStoryboardFile~ipad  | 문자열  | 이 설정에는 애플리케이션의 주 스토리보드 파일 이름이 있어야 합니다. | 애플리케이션이 해당 Info.plist에서 UIMainStoryboardFile을 정의하는 경우에 필수입니다. |
MAMPolicyRequired| 부울| 앱에 Intune APP 정책이 없는 경우 앱이 시작되지 않도록 할지를 지정합니다. 기본값은 NO. <br><br> 참고: MAMPolicyRequired가 YES로 설정된 앱 스토어에는 앱을 제출할 수 없습니다. | 선택 사항입니다. 기본값은 no입니다.|
MAMPolicyWarnAbsent | 부울| 앱에 Intune APP 정책이 없는 경우 앱이 시작 시 사용자에게 경고할지를 지정합니다. <br><br> 참고: 그래도 사용자는 경고를 해제한 후 정책 없이 앱을 사용할 수 있습니다. | 선택 사항입니다. 기본값은 no입니다. |
MultiIdentity | 부울| 앱이 다중 ID를 인식하는지를 지정합니다. | 선택 사항입니다. 기본값은 no입니다. |
SplashIconFile <br> SplashIconFile~ipad | 문자열  | Intune 시작 아이콘 파일을 지정합니다. | 선택 사항입니다. |
SplashDuration | 숫자 | 애플리케이션 시작 시 Intune 시작 화면이 표시되는 최소 시간(초)입니다. 기본값은 1.5입니다. | 선택 사항입니다. |
BackgroundColor| 문자열| 시작 및 PIN 화면의 배경색을 지정합니다. '#XXXXXX' 형식의 16진수 RGB 문자열을 허용합니다. 여기서 X는 0-9 또는 A-F 범위의 값일 수 있습니다. 파운드 기호는 생략할 수 있습니다.   | 선택 사항입니다. 기본값은 연한 회색입니다. |
ForegroundColor| 문자열| 시작 및 PIN 화면의 전경색(텍스트 색 등)을 지정합니다. '#XXXXXX' 형식의 16진수 RGB 문자열을 허용합니다. 여기서 X는 0-9 또는 A-F 범위의 값일 수 있습니다. 파운드 기호는 생략할 수 있습니다.  | 선택 사항입니다. 기본값은 검정입니다. |
AccentColor | 문자열| PIN 화면의 테마 컬러(예: 단추 텍스트 색 및 상자 강조 색)를 지정합니다. '#XXXXXX' 형식의 16진수 RGB 문자열을 허용합니다. 여기서 X는 0-9 또는 A-F 범위의 값일 수 있습니다. 파운드 기호는 생략할 수 있습니다.| 선택 사항입니다. 기본값은 시스템 파란색입니다. |
MAMTelemetryDisabled| 부울| SDK가 원격 분석 데이터를 해당 백 엔드로 보내는지를 지정합니다.| 선택 사항입니다. 기본값은 no입니다. |
MAMTelemetryUsePPE | 부울 | MAM SDK가 PPE 원격 분석 백 엔드에 데이터를 전송할지 여부를 지정합니다. 테스트 원격 분석 데이터가 고객 데이터와 혼합되지 않도록 Intune 정책을 사용하여 앱을 테스트하는 경우 이 설정을 사용합니다. | 선택 사항입니다. 기본값은 no입니다. |
MaxFileProtectionLevel | 문자열 | 선택 사항입니다. 앱에서 지원할 수 있는 최대 `NSFileProtectionType`을 지정할 수 있습니다. 이 값은 서비스에서 보낸 정책이 애플리케이션에서 지원할 수 있는 수준보다 높은 경우 해당 정책을 재정의합니다. 가능한 값은 `NSFileProtectionComplete`, `NSFileProtectionCompleteUnlessOpen`, `NSFileProtectionCompleteUntilFirstUserAuthentication`, `NSFileProtectionNone`입니다.|
OpenInActionExtension | 부울 | Open in Action 확장은 YES로 설정합니다. 자세한 내용은 UIActivityViewController를 통한 데이터 공유 섹션을 참조하세요. |
WebViewHandledURLSchemes | 문자열 배열 | 앱의 WebView에서 처리하는 URL 스키마를 지정합니다. | 앱에서 링크 및/또는 javascript를 통해 URL을 처리하는 WebView를 사용하는 경우 필요합니다. |

## <a name="receive-app-protection-policy"></a>앱 보호 정책 받기

### <a name="overview"></a>개요

Intune 앱 보호 정책을 받으려면 앱에서 Intune MAM 서비스를 사용하여 등록 요청을 시작해야 합니다. 디바이스 등록 여부에 관계없이 Intune 콘솔에서 앱 보호 정책을 받도록 앱을 구성할 수 있습니다. 등록이 없는 앱 보호 정책(**APP-WE** 또는 MAM-WE라고도 함)을 사용하면 Intune MDM(모바일 디바이스 관리)에 디바이스를 등록할 필요 없이 Intune에서 앱을 관리할 수 있습니다. 두 경우 모두 정책을 받으려면 Intune MAM 서비스에 등록해야 합니다.

### <a name="apps-that-use-adal"></a>ADAL을 사용하는 앱

이미 ADAL을 사용하는 앱은 사용자가 성공적으로 인증된 후 `IntuneMAMEnrollmentManager` 인스턴스에서 `registerAndEnrollAccount` 메서드를 호출해야 합니다.

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

`registerAndEnrollAccount` 메서드를 호출하여 SDK는 사용자 계정을 등록하고 이 계정을 대신하여 앱을 등록하려고 시도합니다. 어떤 이유로든 등록에 실패하면 SDK는 자동으로 24시간 후에 등록을 다시 시도합니다. 앱은 디버깅 목적으로 대리자를 통해 모든 등록 요청의 결과에 대한 [알림](#status-result-and-debug-notifications)을 받을 수 있습니다.

이 API가 호출되고 나면 앱이 정상적으로 계속 작동할 수 있습니다. 등록에 성공하면 SDK가 사용자에게 앱을 다시 시작해야 한다고 알립니다. 이때 사용자는 앱을 즉시 다시 시작할 수 있습니다.

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal"></a>ADAL을 사용하지 않는 앱

ADAL을 사용하여 사용자를 로그인하지 않는 앱은 API를 호출하여 SDK에서 해당 인증을 처리하도록 하여 Intune MAM 서비스에서 앱 보호 정책을 계속 수신할 수 있습니다. 앱에 Azure AD로 인증된 사용자가 없지만 데이터를 보호하기 위해 앱 보호 정책을 계속 수신해야 하는 경우 이 기술을 사용해야 합니다. 예를 들어 다른 인증 서비스가 앱 로그인에 사용되거나 앱에서 서명을 지원하지 않는 경우가 여기에 해당됩니다. 이를 위해 애플리케이션이 `IntuneMAMEnrollmentManager` 인스턴스에서 `loginAndEnrollAccount` 메서드를 호출할 수 있습니다.

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

이 메서드를 호출하면 기존 토큰을 찾을 수 없는 경우 SDK에서 사용자에게 자격 증명을 묻는 메시지를 표시합니다. 그러면 SDK에서 제공된 사용자 계정을 대신하여 Intune MAM 서비스에 앱 등록을 시도합니다. "nil"을 ID로 사용하여 메서드를 호출할 수 있습니다. 이 경우 SDK는 디바이스의 기존 관리되는 사용자로 등록하거나(MDM), 기존 사용자가 없는 경우 사용자 이름을 입력하라는 메시지를 표시합니다.

등록에 실패하는 경우 앱은 실패의 세부 정보에 따라 나중에 다시 이 API 호출을 고려해야 합니다. 앱은 대리자를 통해 모든 등록 요청의 결과에 대한 [알림](#status-result-and-debug-notifications)을 수신할 수 있습니다.

이 API가 호출되고 나면 앱이 정상적으로 계속 작동할 수 있습니다. 등록에 성공하면 SDK가 사용자에게 앱을 다시 시작해야 한다고 알립니다.

예:
```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>Intune이 시작 시 인증 및 등록을 처리하도록 허용

앱이 시작되기 전에 Intune SDK에서 ADAL 및 등록을 통해 모든 인증을 처리하도록 하고, 앱에 항상 APP 정책이 필요한 경우 `loginAndEnrollAccount` API를 사용할 필요가 없습니다. 앱의 Info.plist에 있는 IntuneMAMSettings 사전에서 아래 두 설정을 YES로 간단하게 설정할 수 있습니다.

Setting  | 유형  | 정의 |
--       |  --   |   --       |  
AutoEnrollOnLaunch| 부울| 기존의 관리되는 ID가 감지되면 아직 등록되지 않은 경우 앱을 실행할 때 자동으로 등록을 시도할지 지정합니다. 기본값은 NO. <br><br> 참고: 관리되는 ID가 없거나 ID에 대한 유효한 토큰이 ADAL 캐시에 없는 경우 앱에서 MAMPolicyRequired가 YES로 설정되어 있지 않다면 자격 증명을 묻지 않고 자동으로 등록 시도가 실패합니다. |
MAMPolicyRequired| 부울| 앱에 Intune 앱 보호 정책이 없는 경우 앱이 시작되지 않도록 할지를 지정합니다. 기본값은 NO. <br><br> 참고: MAMPolicyRequired가 YES로 설정된 앱 스토어에는 앱을 제출할 수 없습니다. MAMPolicyRequired를 YES로 설정할 경우 AutoEnrollOnLaunch도 YES로 설정해야 합니다. |

앱에 이 옵션을 선택하면 등록 후 앱 다시 시작을 처리할 필요가 없습니다.

### <a name="deregister-user-accounts"></a>사용자 계정 등록 취소

사용자가 앱에서 로그아웃하기 전에 앱이 SDK에서 사용자를 등록 취소해야 합니다. 그러면 다음 사항이 보장됩니다.

1. 사용자 계정에 대해 더 이상 등록이 다시 시도되지 않습니다.

2. 앱 보호 정책이 제거됩니다.

3. 필요에 따라 앱에서 선택적 초기화를 시작한 경우 모든 회사 데이터가 삭제됩니다.

사용자가 로그아웃되기 전에 앱이 `IntuneMAMEnrollmentManager` 인스턴스에서 다음 메서드를 호출해야 합니다.

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

이 메서드는 사용자 계정의 Azure AD 토큰이 삭제되기 전에 호출해야 합니다. SDK에서 사용자를 대신하여 Intune MAM 서비스에 대해 특정 요청을 하려면 사용자 계정의 AAD 토큰이 필요합니다.

앱이 자체적으로 사용자의 회사 데이터를 삭제하는 경우 `doWipe` 플래그를 false로 설정할 수 있습니다. 그렇지 않으면 앱은 SDK에서 선택적 초기화를 시작하도록 할 수 있습니다. 그러면 앱의 선택적 초기화 대리자가 호출됩니다.

예:
```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>상태, 결과 및 디버그 알림

앱은 Intune MAM 서비스에 대한 다음 요청과 관련한 상태, 결과 및 디버그 알림을 수신할 수 있습니다.

* 등록 요청
* 정책 업데이트 요청
* 등록 취소 요청

알림은 `IntuneMAMEnrollmentDelegate.h`의 대리자 메서드를 통해 제공됩니다.

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;
```

이러한 대리자 메서드는 다음 정보가 있는 `IntuneMAMEnrollmentStatus` 개체를 반환합니다.

* 요청과 연결된 계정의 ID
* 요청의 결과를 나타내는 상태 코드
* 상태 코드에 대한 설명이 포함된 오류 문자열
* `NSError` 개체입니다. 이 개체는 반환될 수 있는 특정 상태 코드와 함께 `IntuneMAMEnrollmentStatus.h`에 정의됩니다.

> [!NOTE]
> 이 정보는 디버그 전용입니다. 앱의 비즈니스 논리는 이러한 알림을 기반으로 해서는 안 됩니다. 이 정보는 디버깅 또는 모니터링 목적으로 원격 분석 서비스로 전송할 수 있습니다.

### <a name="sample-code"></a>예제 코드

다음은 대리자 메서드의 예제 구현입니다.

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>애플리케이션 다시 시작

앱이 처음으로 MAM 정책을 수신하면 필요한 후크를 적용하기 위해 다시 시작되어야 합니다. 다시 시작되어야 한다는 사실을 앱에 알리기 위해 SDK는 `IntuneMAMPolicyDelegate.h`의 대리자 메서드를 제공합니다.

```objc
 - (BOOL) restartApplication
```

이 메서드의 반환 값은 SDK에 애플리케이션에서 필요한 다시 시작을 처리해야 함을 알립니다.

* true가 반환되는 경우 애플리케이션이 다시 시작을 처리해야 합니다.

* false가 반환되는 경우 SDK는 이 메서드가 반환된 후 애플리케이션을 다시 시작합니다. SDK는 사용자에게 애플리케이션을 다시 시작하도록 알리는 대화 상자를 즉시 표시합니다.

## <a name="customize-your-apps-behavior-with-apis"></a>API를 사용하여 앱 동작 사용자 지정

Intune 앱 SDK에는 앱에 배포한 Intune APP 보호 정책에 관한 정보를 가져오기 위해 호출할 수 있는 여러 가지 API가 있습니다. 이 데이터를 사용하여 앱 동작을 사용자 지정할 수 있습니다. 다음 표에서는 사용자가 사용할 수 있는 몇 가지 필수 Intune 클래스에 대한 정보를 제공합니다.

인스턴스 | 설명
----- | -----------
IntuneMAMPolicyManager.h | IntuneMAMPolicyManager 클래스는 애플리케이션에 배포된 Intune APP 정책을 표시합니다. 특히 [다중 ID 사용](app-sdk-ios.md#enable-multi-identity-optional)에 유용한 API를 표시합니다. |
IntuneMAMPolicy.h | IntuneMAMPolicy 클래스는 앱에 적용되는 일부 MAM 정책 설정을 제공합니다. 이러한 정책 설정은 앱이 UI를 사용자 지정할 수 있도록 노출됩니다. 대부분의 정책 설정은 앱이 아닌 SDK에 의해 적용됩니다. 앱이 구현해야 하는 유일한 방법은 Save-as 컨트롤입니다. 이 클래스는 Save-as를 구현하는 데 필요한 일부 API를 제공합니다. |
IntuneMAMFileProtectionManager.h | IntuneMAMFileProtectionManager 클래스는 앱이 제공된 ID를 기반으로 파일 및 디렉터리를 명시적으로 보호하는 데 사용할 수 있는 API를 제공합니다. ID는 Intune으로 관리하거나 관리하지 않을 수 있으며 SDK는 적절한 MAM 정책을 적용합니다. 이 클래스를 사용하는 것은 선택 사항입니다. |
IntuneMAMDataProtectionManager.h | IntuneMAMDataProtectionManager 클래스는 앱이 제공된 ID를 통해 데이터 버퍼를 보호하는 데 사용할 수 있는 API를 제공합니다. ID는 Intune으로 관리하거나 관리하지 않을 수 있으며 SDK는 적절한 암호화를 적용합니다. |

## <a name="implement-save-as-controls"></a>다른 이름으로 저장 컨트롤 구현

Intune을 사용하여 IT 관리자는 관리되는 앱이 데이터를 저장할 수 있는 스토리지 위치를 선택할 수 있습니다. 앱은 `IntuneMAMPolicy.h`에 정의된 `isSaveToAllowedForLocation` API를 사용하여 Intune 앱 SDK에서 허용된 스토리지 위치를 쿼리할 수 있습니다.

클라우드 저장소 또는 로컬 위치에 관리되는 데이터를 저장하려면 먼저 앱에서 `isSaveToAllowedForLocation` API를 사용하여 IT 관리자가 해당 위치로의 데이터 저장을 허용했는지 확인해야 합니다.

`isSaveToAllowedForLocation` API를 사용하는 경우 앱은 스토리지 위치에 UPN(사용 가능한 경우)을 전달해야 합니다.

### <a name="supported-save-locations"></a>지원되는 저장 위치

`isSaveToAllowedForLocation` API는 IT 관리자가 `IntuneMAMPolicy.h`에 정의된 다음 위치에 데이터를 저장하는 것을 허용하는지 여부를 확인하기 위한 상수를 제공합니다.

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

앱은 `isSaveToAllowedForLocation`의 상수를 사용하여 데이터를 "관리되는" 위치(예: 비즈니스용 OneDrive 또는 "개인")로 저장할 수 있는지 확인해야 합니다. 또한 앱에서 위치가 "관리되는" 위치인지 “개인” 위치인지 확인할 수 없을 때 이 API를 사용해야 합니다.

"개인"으로 알려진 위치는 `IntuneMAMSaveLocationOther` 상수로 표시됩니다.

앱이 로컬 디바이스의 위치로 데이터를 저장할 때는 `IntuneMAMSaveLocationLocalDrive` 상수를 사용해야 합니다.

## <a name="share-data-via-uiactivityviewcontroller"></a>UIActivityViewController를 통해 데이터 공유

Intune 앱 SDK는 릴리스 8.0.2부터 `UIActivityViewController` 작업을 필터링하여 Intune 관리 공유 위치만 선택할 수 있도록 합니다. 이 동작은 애플리케이션 데이터 전송 정책에 의해 제어됩니다.

### <a name="copy-to-actions"></a>‘복사’ 작업

`UIActivityViewController` 및 `UIDocumentInteractionController`를 통해 문서를 공유하는 경우 iOS에서 공유되는 문서의 열기를 지원하는 각 애플리케이션에 대해 ‘복사’ 작업이 표시됩니다. 애플리케이션은 Info.plist에 있는 `CFBundleDocumentTypes` 설정을 통해 지원하는 문서 종류를 선언합니다. 정책에서 관리되지 않는 애플리케이션에 공유를 금지하는 경우에는 이 유형의 공유를 더 이상 사용할 수 없습니다. 대신, 사용자는 UI가 아닌 작업 확장을 해당 애플리케이션에 추가하고 Intune 앱 SDK에 연결해야 합니다. 작업 확장은 스텁에 불과합니다. SDK는 파일 공유 동작을 구현합니다. 아래 단계를 따릅니다.

1. 애플리케이션의 Info.plist `CFBundleURLTypes` 아래에 schemeURL이 하나 이상 정의되어 있어야 합니다.

2. 애플리케이션과 작업 확장이 하나 이상의 앱 그룹을 공유해야 하며, 해당 앱 그룹이 앱 및 확장 IntuneMAMSettings 사전의 `AppGroupIdentifiers` 배열 아래에 나열되어야 합니다.

3. 작업 확장의 이름을 “Open in”과 애플리케이션 이름으로 지정합니다. 필요에 따라 Info.plist를 지역화합니다.

4. [Apple 개발자 설명서](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/)에 설명된 대로 확장에 대한 템플릿 아이콘을 제공합니다. 또는 IntuneMAMConfigurator 도구를 사용하여 애플리케이션 .app 디렉터리에서 이러한 이미지를 생성할 수 있습니다. 이렇게 하려면 다음을 실행합니다.

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. 확장의 Info.plist에 있는 IntuneMAMSettings 아래에 이름이 `OpenInActionExtension`이고 값이 YES인 부울 설정을 추가합니다.

6. 단일 파일과 `com.microsoft.intune.mam` 접두사가 붙은 애플리케이션 `CFBundleDocumentTypes`의 모든 유형을 지원하도록 `NSExtensionActivationRule`을 구성합니다. 예를 들어 애플리케이션이 public.text 및 public.image를 지원하는 경우 활성화 규칙은 다음과 같습니다.

    ```objc
    SUBQUERY (
        extensionItems,
        $extensionItem,
        SUBQUERY (
            $extensionItem.attachments,
            $attachment,
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” ||
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1
    ).@count == 1
    ```

### <a name="update-existing-share-and-action-extensions"></a>기존 공유 및 작업 확장 업데이트

앱에 이미 공유 또는 작업 확장이 포함되어 있는 경우 Intune 형식을 허용하도록 해당 `NSExtensionActivationRule`을 수정해야 합니다. 확장에서 지원하는 각 형식마다 `com.microsoft.intune.mam` 접두사가 붙은 추가 형식을 추가합니다. 예를 들어 기존 활성화 규칙이 다음과 같다고 가정합니다.  

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data"
    ).@count > 0
).@count > 0
```

이 경우 다음과 같이 변경해야 합니다.

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data
    ).@count > 0
).@count > 0
```

> [!NOTE]
> IntuneMAMConfigurator 도구를 사용하여 Intune 형식을 활성화 규칙에 추가할 수 있습니다. 기존 활성화 규칙이 미리 정의된 문자열 상수(예: NSExtensionActivationSupportsFileWithMaxCount, NSExtensionActivationSupportsText 등)를 사용하는 경우 조건자 구문이 복잡해질 수 있습니다. Intune 형식을 추가하는 동안 IntuneMAMConfigurator 도구를 사용하여 활성화 규칙을 문자열 상수에서 조건자 문자열로 변환할 수도 있습니다.

### <a name="what-the-ui-should-look-like"></a>UI의 모양

이전 UI:

![데이터 공유 - iOS 이전 공유 UI](./media/sharing-UI-old.png)

새 UI:

![데이터 공유 - iOS 새 공유 UI](./media/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>iOS 애플리케이션에 대상 구성(APP/MAM 앱 구성)을 사용하도록 설정

MAM 대상 구성(MAM 앱 구성이라고도 함)을 사용하면 앱이 Intune SDK를 통해 구성 데이터를 받을 수 있습니다. 이 데이터의 형식 및 변형을 정의하고 앱 소유자/개발자가 Intune 고객에게 전달해야 합니다.

Intune 관리자는 Intune Azure Portal 및 Intune Graph API를 통해 구성 데이터를 대상으로 지정하고 배포할 수 있습니다. iOS용 Intune 앱 SDK 버전 7.0.1를 기준으로, MAM 서비스를 통해 MAM 대상 구성에 참여하는 앱에 MAM 대상 구성 데이터를 제공할 수 있습니다. 애플리케이션 구성 데이터는 MDM 채널을 통해 제공되는 것이 아니라 MAM 서비스를 통해 앱에 직접 푸시됩니다. Intune 앱 SDK는 이러한 콘솔에서 검색된 데이터에 액세스하기 위한 클래스를 제공합니다. 다음 항목은 필수 구성 요소입니다.

* MAM 대상 구성 UI에 액세스하려면 먼저 앱을 Intune MAM 서비스에 등록해야 합니다. 자세한 내용은 [앱 보호 정책 받기](#receive-app-protection-policy)를 참조하세요.

* 앱의 원본 파일에 `IntuneMAMAppConfigManager.h`를 포함합니다.

* `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]`를 호출하여 앱 구성 개체를 가져옵니다.

* `IntuneMAMAppConfig` 개체에 대해 적절한 선택기를 호출합니다. 예를 들어 애플리케이션 키가 문자열인 경우 `stringValueForKey` 또는 `allStringsForKey`를 사용하는 것이 좋습니다. 반환 값 및 오류 조건에 대한 자세한 설명은 `IntuneMAMAppConfig.h`를 참조하세요.

Graph API의 기능에 대한 자세한 내용은 [Graph API 참조](https://developer.microsoft.com/graph/docs/concepts/overview)를 참조하세요.

iOS에서 MAM 대상 앱 구성 정책을 만드는 방법에 대한 자세한 내용은 [iOS용 Microsoft Intune 앱 구성 정책을 사용하는 방법](https://docs.microsoft.com/intune/app-configuration-policies-use-ios)에서 MAM 대상 앱 구성 섹션을 참조하세요.

## <a name="telemetry"></a>원격 분석

기본적으로 iOS용 Intune 앱 SDK는 다음과 같은 유형의 이벤트에 대한 원격 분석을 수집합니다.

* **앱 시작**: Microsoft Intune이 관리 유형별로 MAM 지원 앱 사용에 대해 알아보는 데 도움이 됩니다(MDM이 있는 MAM, MDM 등록이 없는 MAM 등).

* **등록 호출**: Microsoft Intune이 클라이언트 쪽에서 시작된 등록 호출의 성공률 및 기타 성능 메트릭에 대해 알아보는 데 도움이 됩니다.

* **Intune 작업**: 문제를 진단하고 Intune의 기능을 보장하기 위해 Intune SDK 작업에 대한 정보를 수집합니다.

> [!NOTE]
> 모바일 애플리케이션에서 Microsoft Intune에 Intune 앱 SDK 원격 분석 데이터를 보내지 않도록 선택하는 경우 Intune 앱 SDK 원격 분석 캡처를 사용하지 않도록 설정해야 합니다. IntuneMAMSettings 사전에서 `MAMTelemetryDisabled` 속성을 YES로 설정합니다.

## <a name="enable-multi-identity-optional"></a>(선택 사항) 다중 ID 사용 설정

기본적으로 SDK는 앱에 전체적으로 정책을 적용합니다. 다중 ID는 ID 단위 수준에서 정책을 적용하기 위해 사용할 수 있는 MAM 기능입니다. 이 기능을 사용하려면 다른 MAM 기능보다 더 많은 앱 참여가 필요합니다.

앱은 활성 ID를 변경하려는 경우 앱 SDK에 알려야 합니다. SDK는 ID 변경이 필요한 경우 앱에도 알립니다. 현재 관리 ID는 하나만 지원됩니다. 사용자가 디바이스 또는 앱을 등록하고 나면 SDK에서 이 ID를 사용하고 이를 기본 관리 ID로 간주합니다. 앱의 다른 사용자는 무제한 정책 설정이 적용되는 관리되지 않는 항목으로 처리됩니다.

ID는 단순히 문자열로 정의됩니다. ID는 대/소문자를 구분하지 않습니다. ID와 관련한 SDK에 대한 요청은 ID를 설정할 때 원래 사용된 것과 같은 대/소문자를 반환하지 않을 수도 있습니다.

### <a name="identity-overview"></a>ID 개요

ID는 계정의 사용자 이름입니다(예: user@contoso.com). 개발자는 다음 수준에서 앱의 ID를 설정할 수 있습니다.

* **프로세스 ID**: 프로세스 전반 ID를 설정하고 주로 단일 ID 애플리케이션에 사용됩니다. 이 ID는 모든 작업, 파일 및 UI에 영향을 줍니다.

* **UI ID**: 잘라내기/복사/붙여넣기, PIN, 인증, 데이터 공유 등 주 스레드에서 UI 작업에 적용되는 정책을 결정합니다. UI ID는 파일 작업(암호화, 백업 등)에 영향을 주지 않습니다.

* **스레드 ID**: 현재 스레드에 적용되는 정책에 영향을 줍니다. 이 ID는 모든 작업, 파일 및 UI에 영향을 줍니다.

사용자가 관리되는지와 관계없이 ID를 적절하게 설정하는 것은 앱의 책임입니다.

어느 시점에서든 모든 스레드에는 UI 작업 및 파일 작업에 대한 유효한 ID가 있습니다. 이 ID는 적용되어야 하는 정책(있는 경우)을 확인하는 데 사용됩니다. ID가 'ID 없음'이거나 사용자가 관리되지 않는 경우 정책이 적용되지 않습니다. 아래 다이어그램은 효과적인 ID를 결정하는 방법을 보여 줍니다.

  ![Intune App SDK iOS: ID 확인 프로세스](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>스레드 큐

앱은 흔히 비동기 및 동기 작업을 스레드 큐로 디스패치합니다. SDK는 GCD(Grand Central Dispatch) 호출을 가로채고 현재 스레드 ID를 디스패치된 작업과 연결합니다. 작업이 종료되면 SDK는 일시적으로 스레드 ID를 작업과 연결된 ID로 변경하고 작업을 종료한 다음 원래 스레드 ID를 복원합니다.


`NSOperationQueue`는 GCD를 기반으로 구축되므로 `NSOperations`는 `NSOperationQueue`에 작업이 추가될 때 스레드의 ID에서 실행됩니다. GCD를 통해 직접 디스패치된 `NSOperations` 또는 함수는 실행되고 있을 때 현재 스레드 ID를 변경할 수도 있습니다. 이 ID는 디스패치하는 스레드에서 상속된 ID를 재정의합니다.

### <a name="file-owner"></a>파일 소유자

SDK는 로컬 파일 소유자 ID를 추적하여 적절하게 정책을 적용합니다. 파일이 만들어지거나 파일이 잘라내기 모드에서 열리면 파일 소유자가 설정됩니다. 소유자는 작업을 수행하는 스레드의 유효 파일 작업 ID로 설정됩니다.

또는 앱은 `IntuneMAMFilePolicyManager`를 사용하여 명시적으로 파일 소유자 ID를 설정할 수 있습니다. 앱은 파일 내용을 표시하기 전에 `IntuneMAMFilePolicyManager`를 사용하여 파일 소유자를 검색하고 UI ID를 설정합니다.

### <a name="shared-data"></a>공유 데이터

앱이 관리되는 사용자와 관리되지 않는 사용자 둘 다의 데이터를 포함하는 파일을 만드는 경우 관리되는 사용자의 데이터를 암호화하는 것은 앱의 책임입니다. `IntuneMAMDataProtectionManager`에서 `protect` 및 `unprotect` API를 사용하여 데이터를 암호화할 수 있습니다.

`protect` 메서드는 관리되는 사용자 또는 관리되지 않는 사용자일 수 있는 ID를 허용합니다. 사용자가 관리되는 경우 데이터가 암호화됩니다. 사용자가 관리되지 않는 경우 ID를 인코딩하는 데이터에 헤더가 추가되지만 데이터는 암호화되지 않습니다. `protectionInfo` 메서드를 사용하여 데이터의 소유자를 검색할 수 있습니다.

### <a name="share-extensions"></a>공유 확장

앱에 공유 확장이 있는 경우 `IntuneMAMDataProtectionManager`의 `protectionInfoForItemProvider` 메서드를 통해 공유되는 항목의 소유자를 검색할 수 있습니다. 공유 항목이 파일인 경우 SDK에서 파일 소유자 설정을 처리합니다. 공유 항목이 데이터인 경우 파일 소유자를 설정하고(이 데이터가 파일에 유지되는 경우) 이 데이터를 UI에 표시하기 전에 `setUIPolicyIdentity` API를 호출하는 것은 앱의 책임입니다.

### <a name="turn-on-multi-identity"></a>다중 ID 설정

기본적으로 앱은 단일 ID로 간주됩니다. SDK는 등록된 사용자의 프로세스 ID를 설정합니다. 다중 ID 지원을 사용하려면 앱의 Info.plis 파일에 있는 IntuneMAMSettings 사전에 이름이 `MultiIdentity`이고 값이 YES인 부울 설정을 추가합니다.

> [!NOTE]
> 다중 ID를 사용하도록 설정한 경우 프로세스 ID, UI ID 및 스레드 ID는 nil로 설정됩니다. 이를 적절하게 설정하는 것은 앱은 책임입니다.

### <a name="switch-identities"></a>ID 전환

* **앱에서 시작된 ID 전환**:

    다중 ID 앱은 시작될 때 알 수 없는, 관리되지 않는 계정으로 실행된다고 간주됩니다. 조건부 시작 UI는 실행되지 않으며 앱에서 정책이 적용되지 않습니다. ID를 변경해야 할 때마다 SDK에 알리는 것은 앱의 책임입니다. 일반적으로 이러한 상황은 앱이 특정 사용자 계정에 대한 데이터를 표시하려고 할 때마다 발생합니다.

    사용자가 문서, 사서함 또는 전자 필기장의 탭을 열려고 하는 경우를 예로 들 수 있습니다. 앱은 파일, 사서함 또는 탭이 실제로 열리기 전에 SDK에 알려야 합니다. 이 작업은 `IntuneMAMPolicyManager`의 `setUIPolicyIdentity` API를 통해 수행됩니다. 이 API는 사용자가 관리되는지와 관계없이 호출되어야 합니다. 사용자가 관리되는 경우 SDK는 조건부 시작 검사(탈옥 검색, PIN, 인증 등)를 수행합니다.

    ID 전환 결과는 완료 처리기를 통해 비동기적으로 앱에 반환됩니다. 성공 결과 코드가 반환될 때까지 앱은 문서, 사서함 또는 탭을 여는 작업을 연기해야 합니다. ID 전환에 실패하는 경우 앱은 작업을 취소해야 합니다.

* **SDK에서 시작된 ID 전환**:

    SDK가 앱에 특정 ID로의 전환을 요청해야 하는 경우가 있습니다. 다중 ID 앱은 `IntuneMAMPolicyDelegate`에 이 요청을 처리하기 위한 `identitySwitchRequired` 메서드를 구현해야 합니다.

    이 메서드가 호출되면 앱은 지정된 ID로의 전환 요청을 처리할 수 있는 경우 `IntuneMAMAddIdentityResultSuccess`를 완료 처리기에 전달해야 합니다. 앱이 ID 전환을 처리할 수 없는 경우 `IntuneMAMAddIdentityResultFailed`를 완료 처리기에 전달해야 합니다.

    앱은 이 호출에 대한 응답으로 `setUIPolicyIdentity`를 호출할 필요는 없습니다. SDK가 앱이 관리되지 않는 사용자 계정으로 전환하도록 요구하는 경우 빈 문자열이 `identitySwitchRequired` 호출에 전달됩니다.

* **선택적 초기화**:

    앱이 선택적으로 초기화된 경우 SDK는 `IntuneMAMPolicyDelegate`의 `wipeDataForAccount` 메서드를 호출합니다. 지정된 사용자의 계정 및 해당 계정과 연결된 모든 데이터를 제거하는 것은 앱의 책임입니다. SDK는 사용자가 소유한 모든 파일을 제거할 수 있으며, 앱이 `wipeDataForAccount` 호출에서 FALSE를 반환하는 경우 이렇게 합니다.

    이 메서드는 백그라운드 스레드에서 호출됩니다. 사용자에 대한 모든 데이터(앱에서 FALSE를 반환하는 경우에는 파일 제외)가 제거될 때까지 앱에서 값을 반환해서는 안 됩니다.

## <a name="ios-best-practices"></a>iOS 모범 사례

다음은 iOS용으로 개발할 때 권장되는 모범 사례입니다.

* iOS 파일 시스템은 대/소문자를 구분합니다. `libIntuneMAM.a` 및 `IntuneMAMResources.bundle`과 같이 파일 이름의 대/소문자가 올바른지 확인합니다.

* Xcode에서 `libIntuneMAM.a`를 찾는 데 문제가 있는 경우 링커 검색 경로에 이 라이브러리 경로를 추가하면 문제를 해결할 수 있습니다.

## <a name="faqs"></a>FAQ(질문과 대답)

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>네이티브 Swift 또는 Objective-C와 Swift의 상호 운용성을 통해 모든 API의 주소를 지정할 수 있나요?

Intune 앱 SDK API는 Objective-C 전용이며 **네이티브** Swift를 지원하지 않습니다. Swift의 Objective-C와 상호 운용성이 필요합니다.

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>내 애플리케이션의 모든 사용자를 APP-WE 서비스에 등록해야 하나요?

아니요. 실제로 회사 또는 학교 계정만 Intune 앱 SDK에 등록하면 됩니다. 계정이 회사 또는 학교 컨텍스트에서 사용되는지를 결정하는 것은 앱의 책임입니다.

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>애플리케이션에 이미 로그인한 사용자의 경우는 어떤가요? 등록해야 하나요?

성공적으로 인증된 후 사용자를 등록하는 것은 애플리케이션의 책임입니다. 또한 애플리케이션이 MDM 없는 MAM 기능을 가지기 전에 존재했을 수 있는 기존 계정을 등록하는 것도 애플리케이션의 책임입니다.

이렇게 하려면 애플리케이션이 `registeredAccounts:` 메서드를 사용해야 합니다. 이 메서드는 등록된 모든 계정이 있는 NSDictionary를 Intune MAM 서비스에 반환합니다. 애플리케이션의 모든 기존 계정이 목록에 없는 경우 애플리케이션은 `registerAndEnrollAccount:`을 통해 해당 계정을 등록해야 합니다.

### <a name="how-often-does-the-sdk-retry-enrollments"></a>SDK가 등록을 다시 시도하는 빈도는 어느 정도인가요?

SDK는 이전에 실패한 모든 등록을 24시간 간격으로 자동으로 다시 시도합니다. SDK는 사용자의 조직에서 사용자가 애플리케이션에 로그인한 후 MAM을 사용하도록 설정한 경우 사용자가 등록되고 정책을 수신하도록 하기 위해 이렇게 합니다.

SDK는 사용자가 애플리케이션을 등록했음을 감지하면 다시 시도를 중지합니다. 특정 시점에 1명의 사용자만 애플리케이션을 등록할 수 있기 때문입니다. 사용자가 등록 취소된 경우 다시 시도는 같은 24시간 간격으로 다시 시작됩니다.

### <a name="why-does-the-user-need-to-be-deregistered"></a>사용자를 등록 취소해야 하는 이유는 무엇인가요?

SDK는 백그라운드에서 주기적으로 다음 작업을 수행합니다.

* 애플리케이션이 아직 등록되지 않은 경우 SDK는 24시간마다 모든 등록된 계정을 등록하려고 시도합니다.
* 애플리케이션이 등록된 경우 SDK는 8시간마다 MAM 정책 업데이트를 확인합니다.

사용자를 등록 취소하면 사용자가 더 이상 애플리케이션을 사용하지 않으며 해당 사용자 계정에 대한 주기적 이벤트를 중지할 수 있음이 SDK에 통지됩니다. 또한 등록 취소하고 필요한 경우 선택적 초기화를 수행하라고 앱을 트리거합니다.

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>등록 취소 메서드에서 doWipe 플래그를 true로 설정해야 하나요?

사용자가 애플리케이션에서 로그아웃하기 전에 이 메서드를 호출해야 합니다.  로그아웃 진행 과정의 일부로 사용자의 데이터가 애플리케이션에서 삭제되면 `doWipe`를 false로 설정할 수 있습니다. 그러나 애플리케이션이 사용자의 데이터를 제거하지 않는 경우 SDK가 데이터를 삭제할 수 있도록 `doWipe`를 true로 설정해야 합니다.

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>애플리케이션을 등록 취소할 수 있는 다른 방법이 있나요?

예, IT 관리자는 애플리케이션에는 선택적 초기화 명령을 보낼 수 있습니다. 그러면 사용자가 등록 취소되고 사용자의 데이터가 초기화됩니다. SDK는 이 시나리오를 자동으로 처리하고 등록 취소 대리자 메서드를 통해 알림을 보냅니다.

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>SDK를 통합하는 방법을 보여 주는 샘플 앱이 있습니까?

예. 최근에 오픈 소스 샘플 앱 [iOS용 Wagr](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App)을 개선했습니다. Wagr은 이제 Intune 앱 SDK를 통해 앱 보호 정책을 사용하도록 설정됩니다.

## <a name="submit-your-app-to-the-app-store"></a>앱 스토어에 앱 제출

Intune 앱 SDK의 정적 라이브러리 빌드와 프레임워크 빌드는 둘 다 범용 이진 파일입니다. 따라서 모든 디바이스와 시뮬레이터 아키텍처에 대한 코드가 있습니다. Apple은 앱에 시뮬레이터 코드가 있는 경우 앱 스토어에 제출된 앱을 거부합니다. 디바이스 전용 빌드의 정적 라이브러리에 대해 컴파일할 때 링커에서 시뮬레이터 코드를 자동으로 제거합니다. 앱 스토어에 앱을 업로드하기 전에 모든 시뮬레이터 코드를 제거하려면 다음 단계를 수행합니다.

1. 데스크톱에 `IntuneMAM.framework`가 있는지 확인합니다.

2. 다음 명령을 실행하세요.

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    첫 번째 명령은 프레임워크의 DYLIB 파일에서 시뮬레이터 아키텍처를 제거합니다. 두 번째 명령은 디바이스 전용 DYLIB 파일을 프레임워크 디렉터리에 다시 복사합니다.
