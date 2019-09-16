---
title: Android용 Microsoft Intune 앱 SDK 개발자 가이드
description: Android용 Microsoft Intune 앱 SDK를 사용하면 Android 앱에 Intune MAM(모바일 앱 관리)을 통합할 수 있습니다.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 527d71f0e48627498b05af8ee497579c648d3156
ms.sourcegitcommit: ec22a186a9cfa489a8490698e387624e480892d8
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68960544"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Android용 Microsoft Intune 앱 SDK 개발자 가이드

> [!NOTE]
> 먼저 SDK의 현재 기능 및 지원되는 각 플랫폼에서 통합을 준비하는 방법을 설명하는 [Intune 앱 SDK 개요](app-sdk.md) 항목을 읽어보는 것이 좋습니다.

Android용 Microsoft Intune 앱 SDK를 사용하면 네이티브 Android 앱에 Intune 앱 보호 정책(**APP** 또는 MAM 정책이라고도 함)을 통합할 수 있습니다. Intune 관리 애플리케이션은 Intune 앱 SDK와 통합된 애플리케이션입니다. Intune 관리자는 Intune으로 앱을 직접 관리할 때 Intune 관리 앱에 앱 보호 정책을 쉽게 배포할 수 있습니다.


## <a name="whats-in-the-sdk"></a>SDK에 포함된 내용

Intune 앱 SDK는 다음 파일로 구성됩니다.

* **Microsoft.Intune.MAM.SDK.aar**: 지원 라이브러리 JAR 파일을 제외한 SDK 구성 요소입니다.
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: Android v4 지원 라이브러리를 사용하는 앱 내에서 MAM을 사용하도록 설정하는 데 필요한 클래스입니다.
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: Android v7 지원 라이브러리를 사용하는 앱 내에서 MAM을 사용하도록 설정하는 데 필요한 클래스입니다.
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**: Android v17 지원 라이브러리를 사용하는 앱 내에서 MAM을 사용하도록 설정하는 데 필요한 클래스입니다. 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**: `android.support.text` 패키지에서 Android 지원 라이브러리 클래스를 사용하는 앱 내에서 MAM을 사용하도록 설정하는 데 필요한 클래스입니다.
* **Microsoft.Intune.MDM.SDK.DownlevelStubs.jar**: 이 jar 파일에는 최신 디바이스에만 있지만 MAMActivity의 메서드에 의해 참조되는 Android 시스템 클래스용 스텁이 포함됩니다. 새로운 디바이스는 이 스텁 클래스를 무시합니다. 이 jar 파일은 앱이 MAMActivity에서 파생되는 클래스에 리플렉션을 수행하는 경우에만 필요하며 대부분의 앱에는 포함할 필요가 없습니다. 이 jar 파일을 사용하는 경우 모든 클래스를 ProGuard에서 제외시키는 데 주의해야 합니다. 모두 "android" 루트 패키지 안에 있습니다.
* **com.microsoft.intune.mam.build.jar**: [SDK 통합에 도움이 되는](#build-tooling) 도움이 되는 Gradle 플러그 인입니다.
* **CHANGELOG.txt**: 각 SDK 버전에서 변경된 내용의 레코드를 제공합니다.
* **THIRDPARTYNOTICES.TXT**: 앱에 컴파일될 타사 및/또는 OSS 코드를 확인하는 특성 알림입니다.

## <a name="requirements"></a>요구 사항

### <a name="android-versions"></a>Android 버전
이 SDK는 Android API 19(Android 4.4+)부터 Android API 28(Android 9.0)까지 지원합니다.

### <a name="company-portal-app"></a>회사 포털 앱
Android용 Intune 앱 SDK가 작동하려면 디바이스에 앱 보호 정책을 사용하기 위한 [회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) 앱이 있어야 합니다. 회사 포털이 Intune 서비스에서 앱 보호 정책을 검색합니다. 앱을 초기화할 때 정책과 회사 포털에서 해당 정책을 적용하는 코드를 로드합니다.

> [!NOTE]
> 회사 포털 앱이 디바이스에 없으면 Intune 관리 앱은 Intune 앱 보호 정책을 지원하지 않는 일반 앱처럼 작동합니다.

디바이스 등록 없이 앱 보호를 사용하기 위해 사용자가 회사 포털 앱을 통해 디바이스를 등록할 필요가 _**없습니다**_ .

## <a name="sdk-integration"></a>SDK 통합

### <a name="sample-app"></a>샘플 앱
Intune 앱 SDK와 올바르게 통합하는 방법에 대한 예제는 [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App)에 제공됩니다. 이 예제에서는 [Gradle 빌드 플러그 인](#gradle-build-plugin)을 사용합니다.

### <a name="referencing-intune-app-libraries"></a>Intune 앱 라이브러리 참조

Intune 앱 SDK는 외부 종속성이 없는 표준 Android 라이브러리입니다. **Microsoft.Intune.MAM.SDK.aar**에는 앱 보호 정책 사용에 필요한 인터페이스와 Microsoft Intune Company Portal 앱과의 상호 운용에 필요한 코드가 모두 포함되어 있습니다.

**Microsoft.Intune.MAM.SDK.aar**은 Android 라이브러리 참조로 지정해야 합니다. 이렇게 하려면 Android Studio에서 앱 프로젝트를 열고 **파일 > 새로 만들기 > 새 모듈**로 이동하고 **.JAR/.AAR 패키지 가져오기**를 선택합니다. 그런 다음, .AAR에 대한 모듈을 만들기 위해 Android 아카이브 패키지 Microsoft.Intune.MAM.SDK.aar을 선택합니다. 앱 코드가 포함된 하나 이상의 모듈을 마우스 오른쪽 단추로 클릭하고 **모듈 설정** > **종속성 탭** >  **+ 아이콘**  >  **모듈 종속성**으로 이동한 다음, 방금 만든 MAM SDK AAR 모듈 > **확인**을 선택합니다. 이렇게 하면 프로젝트를 빌드할 때 모듈이 MAM SDK와 함께 컴파일됩니다.

또한 **Microsoft.Intune.MAM.SDK.Support.XXX .jar** 라이브러리는 해당 `android.support.XXX` 라이브러리의 Intune 변형을 포함합니다. 앱이 지원 라이브러리에 종속될 필요가 없는 경우를 대비하여 Microsoft.Intune.MAM.SDK.aar에 빌드되지 않습니다.

#### <a name="proguard"></a>ProGuard

[ProGuard](http://proguard.sourceforge.net/)(또는 다른 shrinking/obfuscation 메커니즘)를 빌드 단계로 사용하면 SDK는 포함해야 하는 추가 구성 규칙을 포함합니다. 빌드에 .AAR을 포함할 때는 규칙이 proguard 단계에 자동으로 통합되고 필요한 클래스 파일이 유지됩니다.

Azure ADAL(Active Directory Authentication Libraries)에는 고유 ProGuard 제한 사항이 있습니다. 앱에서 ADAL을 통합하는 경우 이러한 제한 사항에 대한 ADAL 문서를 따라야 합니다.

### <a name="build-tooling"></a>빌드 도구
Intune 앱 SDK는 앱에서 Intune 정책 적용을 지원하고 참여할 수 있도록 하는 Android 라이브러리입니다. 일부 정책에서는 [앱의 명시적 참여](#enable-features-that-require-app-participation)를 요구하지만 대부분은 반자동으로 적용됩니다. 이 자동 적용을 수행하려면 앱이 여러 Android 기본 클래스에서의 상속을 MAM에서의 상속으로 하는 바꾸고, 이와 유사하게 특정 Android 시스템 서비스 클래스로의 호출을 MAM 동급 클래스로의 호출로 바꾸어야 합니다. 필요한 구체적인 대체는 [아래에](#class-and-method-replacements) 자세히 설명되어 있습니다.

이러한 대체를 수동으로 수행하는 것은 귀찮은 프로세스일 것입니다. 대신, 이 SDK는 대체를 자동으로 수행하는 빌드 도구(Gradle 빌드를 위한 플러그 인 및 비 Gradle 빌드용 명령줄 도구)를 제공합니다. 이러한 도구는 Java 컴파일에 의해 생성된 클래스 파일을 변환하고 원래 소스 코드는 수정하지 않습니다.

이 도구는 [직접 대체](#class-and-method-replacements)만 수행합니다. [Save-As 정책](#enable-features-that-require-app-participation), [Multi-Identity](#multi-identity-optional), [App-WE 등록](#app-protection-policy-without-device-enrollment), [AndroidManifest 수정](#manifest-replacements) 또는 [ADAL 구성](#configure-azure-active-directory-authentication-library-adal)과 같은 좀 더 복잡한 SDK 통합을 수행하지 않습니다. 이러한 작업은 앱이 Intune을 완전히 지원하기 전에 완료되어야 하기 때문입니다. 앱과 관련된 통합 지점에 대해서는 이 설명서의 나머지 부분을 자세히 검토하세요.

> [!NOTE]
> 수동 대체를 통해 MAM SDK의 부분 또는 전체 원본 통합을 이미 수행한 프로젝트에 대해 이러한 도구를 실행하는 것이 좋습니다. 프로젝트는 여전히 MAM SDK를 종속성으로 표시합니다.

### <a name="gradle-build-plugin"></a>Gradle Build 플러그 인
앱이 gradle로 빌드되지 않은 경우 [명령줄 도구와 통합](#command-line-build-tool)으로 건너뜁니다. 

앱 SDK 플러그 인은 SDK의 일부로 **GradlePlugin/com.microsoft.intune.mam.build.jar**로 배포됩니다. Gradle이 이 플러그 인을 찾을 수 있으려면 buildscript 클래스 경로에 추가해야 합니다. 이 플러그 인은 [Javassist](https://jboss-javassist.github.io/javassist/)에 의존하므로 이 기능도 함께 추가해야 합니다. 이러한 기능을 클래스 경로에 추가하려면 루트 `build.gradle`에 다음을 추가합니다.

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

그런 다음, APK 프로젝트의 `build.gradle` 파일에서 플러그 인을 다음과 같이 적용하세요.

```groovy
apply plugin: 'com.microsoft.intune.mam'
```

기본적으로 이 플러그 인은 `project` 종속성**에만** 작동합니다.
테스트 컴파일은 영향을 받지 않습니다. 구성을 목록에 제공할 수 있습니다.
* 제외할 프로젝트
* [포함할 외부 종속성](#usage-of-includeexternallibraries) 
* 처리에서 제외할 특정 클래스
* 처리에서 제외할 변형입니다. 이러한 변형은 전체 변형 이름 또는 단일 버전을 나타낼 수 있습니다. 예
  * 앱의 빌드 형식이 {`savory`, `sweet`} 및 {`vanilla`, `chocolate`}를 갖는 `debug` 및 `release`인 경우
  * `savory`를 지정하여 savory 버전의 모든 변형을 제외하거나 `savoryVanillaRelease`를 사용하여 해당 변형만 정확히 제외할 수 있습니다.

#### <a name="example-partial-buildgradle"></a>예제 부분 build.gradle

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*", "!com.microsoft.qux*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}
```

다음과 같은 결과가 나타납니다.
* `:product:FooLib`는 `excludeProjects`에 포함되므로 다시 작성되지 않습니다.
* `:product:foo-project`는 `excludeClasses`에 있으므로 건너뛴 `com.contoso.SplashActivity`를 제외하고 다시 작성됩니다.
* `bar.jar`은 `includeExternalLibraries`에 포함되므로 다시 작성됩니다.
* `zap.jar`은 프로젝트가 아니고 `includeExternalLibraries`에 있지 않으므로 다시 작성되지 **않습니다**.
* `com.contoso.foo:zap-artifact:1.0.0`은 `includeExternalLibraries`에 있으므로 다시 작성됩니다.
* `com.microsoft.bar:baz:1.0.0`은 와일드카드(`com.microsoft.*`)를 통해 `includeExternalLibraries`에 포함되어 있으므로 다시 작성됩니다.
* `com.microsoft.qux:foo:2.0`은 부정 패턴을 통해 명시적으로 제외되었으므로 이전 항목과 똑같은 와일드카드와 일치하더라도 다시 작성되지 않습니다.

#### <a name="usage-of-includeexternallibraries"></a>includeExternalLibraries의 사용

이 플러그 인은 기본적으로 프로젝트 종속성(일반적으로 `project()` 함수에서 제공)에서만 작동하므로, 아래에 설명된 기준에 따라 MAM 처리가 필요한 경우 `fileTree(...)`으로 지정되거나 maven 또는 기타 패키지 원본(예: “`com.contoso.bar:baz:1.2.0`”)에서 얻은 모든 종속성이 `includeExternalLibraries` 속성에 제공되어야 합니다. 와일드카드(“*”)가 지원됩니다. `!`로 시작하는 항목은 부정이며 라이브러리를 제외하는 데 사용할 수 있습니다. 그렇지 않은 항목은 와일드카드에 의해 포함됩니다.

아티팩트 표기법으로 외부 종속성을 지정할 때 `includeExternalLibraries` 값에서 버전 구성 요소를 생략하는 것이 좋습니다. 버전을 포함하는 경우 정확한 버전이어야 합니다. 동적 버전 사양(예: `1.+`)은 지원되지 않습니다.

`includeExternalLibraries`에 라이브러리를 포함해야 하는지 여부를 판별하는 데 사용해야 하는 일반 규칙은 다음 두 가지 질문을 기준으로 합니다.
1. 라이브러리에 MAM 동급에 해당하는 클래스가 있나요? 예: `Activity` , `Fragment` , `ContentProvider` , `Service` 등
2. 있는 경우 앱에서 이러한 클래스를 사용하나요?

이러한 질문의 답이 모두 ‘예’이면 해당 라이브러리를 `includeExternalLibraries`에 포함해야 합니다. 

| 시나리오 | 포함 여부 |
|--|--|
| PDF 뷰어 라이브러리를 앱에 포함하고 사용자가 PDF를 보려고 할 때 애플리케이션에서 `Activity` 뷰어를 사용합니다. | 예 |
| 웹 성능 향상을 위해 앱에 HTTP 라이브러리를 포함합니다. | 아니요 |
| `Activity` , `Application` 및 `Fragment`에서 파생된 클래스를 포함하는 React Native와 같은 라이브러리를 포함하고 앱에서 해당 클래스를 사용하거나 추가로 파생시킵니다. | 예 |
| `Activity` , `Application` 및 `Fragment`에서 파생된 클래스를 포함하는 React Native와 같은 라이브러리를 포함하지만 정적 도우미 또는 유틸리티 클래스만 사용합니다. | 아니요 |
| `TextView`에서 파생된 뷰 클래스를 포함하는 라이브러리를 포함하고 앱에서 해당 클래스를 사용하거나 추가로 파생시킵니다. | 예 |

#### <a name="reporting"></a>보고
빌드 플러그 인은 변경 내용에 대한 html 보고서를 생성할 수 있습니다. 이 보고서를 생성하라고 요청하려면 `intunemam` 구성 블록에서 `report = true`를 지정합니다. 생성된 보고서는 빌드 디렉터리의 `outputs/logs`에 작성됩니다.

```groovy
intunemam {
    report = true
}
```

#### <a name="dependencies"></a>종속성

gradle 플러그 인은 [Javassist](https://jboss-javassist.github.io/javassist/)에 대한 종속성이 있으므로 위에서 설명한 것처럼 Gradle 종속성 해결에서 사용해야 합니다. Javassist는 이 플러그 인을 실행하는 빌드 타임에만 사용됩니다. Javassist 코드는 앱에 추가되지 않습니다.

> [!NOTE] 
> 버전 3.0 이상의 Android Gradle 플러그 인 및 Gradle 4.1 이상을 사용해야 합니다.

### <a name="command-line-build-tool"></a>명령줄 빌드 도구
빌드 시 Gradle을 사용하는 경우 [다음 섹션](#class-and-method-replacements)으로 건너뜁니다.

명령줄 빌드 도구는 SDK 드롭의 `BuildTool` 폴더에서 사용할 수 있습니다. 위에서 자세히 설명한 것과 같이 이 도구는 Gradle 플러그 인과 동일한 기능을 수행하지만 사용자 지정 또는 비 Gradle 빌드 시스템에 통합될 수 있습니다. 또한 좀 더 일반적이고 호출이 좀 더 복잡하므로 Gradle 플러그 인은 가능할 때만 사용해야 합니다.

#### <a name="using-the-command-line-tool"></a>명령줄 도구 사용

`BuildTool\bin` 디렉터리에 있는 제공된 도우미 스크립트를 사용하여 명령줄 도구를 호출할 수 있습니다.

이 도구에는 다음 매개 변수가 필요합니다.

| 매개 변수 | 설명 |
| -- | -- |
| `--input` | 수정할 클래스 파일의 세미콜론으로 구분된 jar 파일 및 디렉터리 목록입니다. 여기에는 다시 쓰려는 모든 jar/디렉터리가 포함되어야 합니다. |
| `--output` | 수정한 클래스를 저장할 세미콜론으로 구분된 jar 파일 및 디렉터리 목록입니다. 입력 항목당 하나의 출력 항목이 있으며 순서대로 나열되어야 합니다. |
| `--classpath` | 빌드 클래스 경로입니다. 여기에는 jar 및 클래스 디렉터리가 둘 다 포함됩니다. |
| `--excludeClasses`| 재작성에서 제외해야 하는 클래스의 이름을 포함하는 세미콜론으로 구분된 목록입니다. |

선택적인 `--excludeClasses`를 제외한 모든 매개 변수가 필수입니다.

> [!NOTE] 
> Unix와 비슷한 시스템에서 세미콜론은 명령 구분 기호입니다. 셸이 명령을 분할하지 못하게 하려면 각 세미콜론을 '\'로 이스케이프하거나 전체 매개 변수를 느낌표로 래핑합니다.

#### <a name="example-command-line-tool-invocation"></a>명령줄 도구 호출 예제

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

다음과 같은 결과가 나타납니다.

* `product-foo-project` 디렉터리는 `mam-build\product-foo-project`로 다시 작성됩니다.
* `bar.jar`는 `mam-build\libs\bar.jar`로 다시 작성됩니다.
* `zap.jar`는 `--classpath`에만 나열되므로 다시 작성되지 **않습니다**.
* `com.contoso.SplashActivity` 클래스는 `--input`에 있더라도 다시 작성되지 **않습니다**.

> [!NOTE] 
> 빌드 도구는 현재 aar 파일을 지원하지 않습니다. 빌드 시스템이 aar 파일을 처리할 때 `classes.jar`을 아직 추출하지 않은 경우 빌드 도구를 호출하기 전에 이 작업을 수행해야 합니다.


## <a name="class-and-method-replacements"></a>클래스 및 메서드 대체

Intune 관리를 사용하도록 설정하려면 Android 기본 클래스를 동등한 개별 MAM 클래스로 바꿔야 합니다. SDK 클래스는 Android 기본 클래스와 앱에서 파생된 고유 버전의 Android 기본 클래스 사이에 존재합니다. 예를 들어 앱 활동은 `Activity` > `MAMActivity` >
`AppSpecificActivity`와 같은 상속 계층을 생성할 수 있습니다. MAM 계층은 앱에 관리되는 보기를 원활하게 제공하기 위해 시스템 작업에 대한 호출을 필터링합니다.

기본 클래스 외에도, 앱이 파생 없이 사용할 수 있는 일부 클래스(예: `MediaPlayer`)에 필수 MAM 동급 클래스도 있으며 [일부 메서드 호출도 대체](#wrapped-system-services)해야 합니다. 정확한 세부 사항은 아래와 같습니다.

이 섹션에서 설명하는 모든 대체는 SDK [빌드 도구](#build-tooling)에서 자동으로 수행할 수 있습니다. 



| Android 기본 클래스 | Intune 앱 SDK 대체 항목 |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.Dialog | MAMDialog |
| android.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent([Pending Intent](#pendingintent) 참조) |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder(Binder가 AIDL(Android Interface Definition Language) 인터페이스에서 생성되지 않은 경우에만 필요함) |
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.CheckedTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> 애플리케이션에 자체 파생된 `Application` 클래스가 필요하지 않은 경우에도 [아래 `MAMApplication`을 참조하십시오.](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar:

| Android 클래스 | Intune 앱 SDK 대체 항목 |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar:

|Android 클래스 | Intune 앱 SDK 대체 항목 |
|--|--|
| android.support.v7.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Android 클래스 | Intune 앱 SDK 대체 항목 |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Android 클래스 | Intune 앱 SDK 대체 항목 |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>이름이 바뀐 메서드
대부분의 경우, Android 클래스에서 사용할 수 있는 메서드가 MAM 대체 클래스에서 최종본으로 표시되어 있습니다. 이 경우 MAM 대체 클래스는 대신 재정의할 유사한 이름의 메서드(일반적으로 접미사 `MAM`이 붙음)를 제공합니다. 예를 들어 `onCreate()`를 재정의하고 `super.onCreate()`를 호출하는 대신 `MAMActivity`에서 파생하는 경우 `Activity`는 `onMAMCreate()`를 재정의하고 `super.onMAMCreate()`를 호출해야 합니다. Java 컴파일러는 동등한 MAM 메서드 대신 원래 메서드가 실수로 재정의되는 것을 방지하기 위해 최종 제한을 적용해야 합니다.

### <a name="mamapplication"></a>MAMApplication
앱이 `android.app.Application` 서브클래스를 만드는 경우 대신 `com.microsoft.intune.mam.client.app.MAMApplication`의 서브클래스를 **만들어야** 합니다. 앱이 `android.app.Application` 서브클래스를 만들지 않는 경우 AndroidManifest.xml의 `<application>` 태그에서 `"com.microsoft.intune.mam.client.app.MAMApplication"`을 `"android:name"` 특성으로 설정해야 **합니다**.

### <a name="pendingintent"></a>PendingIntent
`PendingIntent.get*` 대신 `MAMPendingIntent.get*` 메서드를 사용해야 합니다. 그런 다음 결과로 생성된 `PendingIntent`를 일반적인 방식으로 사용할 수 있습니다.

### <a name="wrapped-system-services"></a>래핑된 시스템 서비스
일부 시스템 서비스 클래스의 경우, 서비스 인스턴스에서 원하는 메서드를 직접 호출하지 않고 MAM 래퍼 클래스에서 정적 메서드를 호출해야 합니다. 예를 들어, `getSystemService(ClipboardManager.class).getPrimaryClip()`에 대한 호출은 `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)`에 대한 호출이어야 합니다. 이러한 호출을 수동으로 대체하지 않는 것이 좋습니다. 대신 BuildPlugin을 통해 수행합니다.

| Android 클래스 | Intune 앱 SDK 대체 항목 |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.ContentProviderClient | MAMContentProviderClientManagement |
| android.content.ContentResolver | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| android.print.PrintManager | MAMPrintManagement |
| android.support.v4.print.PrintHelper | MAMPrintHelperManagement |
| android.view.View | MAMViewManagement |
| android.view.DragEvent | MAMDragEventManagement |

`ClipboardManager`, `ContentProviderClient`, `ContentResolver`, `PackageManager` 같은 클래스는 대부분의 메서드가 래핑되고 `DownloadManager`, `PrintManager`, `PrintHelper`, `View`, `DragEvent` 같은 클래스는 한두 개 메서드만 래핑됩니다. BuildPlugin을 사용하고 있지 않은지 잘 모르겠으면 MAM에 해당하는 클래스가 노출하는 API를 참조하세요. 

### <a name="manifest-replacements"></a>매니페스트 대체
Java 코드 외에도 매니페스트에서 위의 클래스 대체를 수행해야 할 수도 있습니다. 특별 참고 사항:
* `android.support.v4.content.FileProvider`에 대한 매니페스트 참조는 `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`로 대체해야 합니다.

## <a name="androidx-libraries"></a>AndroidX 라이브러리
Android P를 사용하면서 Google은 AndroidX라는 새로운 이름의 지원 라이브러리를 발표했으며 버전 28은 기존 android.support 라이브러리의 최신 주 릴리스입니다.

Android 지원 라이브러리와 달리, AndroidX 라이브러리의 MAM 변형은 제공하지 않습니다. 대신, AndroidX는 다른 외부 라이브러리로 취급되며 빌드 플러그 인/도구로 다시 작성되도록 구성되어야 합니다. Gradle 빌드의 경우 플러그 인 구성의 `includeExternalLibraries` 필드에 `androidx.*`를 포함하여 이처럼 구성할 수 있습니다. 명령줄 도구의 호출은 모든 jar 파일을 명시적으로 나열해야 합니다.
## <a name="sdk-permissions"></a>SDK 권한

Intune 앱 SDK에는 SDK를 통합하는 앱에 대한 세 가지 [Android 시스템 권한](https://developer.android.com/guide/topics/security/permissions.html)이 있어야 합니다.

* `android.permission.GET_ACCOUNTS`(필요한 경우 런타임 시 요청됨)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

조정된 인증을 수행하려면 Azure [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)(Active Directory Authentication Library)에 이러한 권한이 필요합니다. 이러한 사용 권한이 앱에 부여되지 않거나 사용자에 의해 취소될 경우 브로커(회사 포털 앱)가 필요한 인증 흐름을 사용할 수 없습니다.

## <a name="logging"></a>로깅

로깅된 데이터를 최대한 활용하려면 초기에 로깅을 초기화해야 합니다. 일반적으로 `Application.onMAMCreate()`는 로깅을 초기화하는 가장 좋은 위치입니다.

앱에서 MAM 로그를 받으려면 [Java Handler](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html)를 만들어 `MAMLogHandlerWrapper`에 추가합니다. 그러면 애플리케이션 핸들러에서 모든 로그 메시지에 대해 `publish()`를 호출합니다.

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```



## <a name="enable-features-that-require-app-participation"></a>앱 참여를 요구하는 기능 사용

SDK가 자체적으로 구현할 수 없는 몇 가지 앱 보호 정책이 있습니다. 앱은 다음의 `AppPolicy` 인터페이스에서 찾을 수 있는 여러 가지 API를 사용하여 이러한 기능을 수행하기 위한 동작을 제어할 수 있습니다. `AppPolicy` 인스턴스를 검색하려면 `MAMPolicyManager.getPolicy`를 사용합니다.

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * This function is now deprecated. Please use getIsSaveToLocationAllowed(SaveLocation, String) instead
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 *
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Checks whether any activities which could handle the given intent are allowed by policy. Returns false only if all
 * activities which could otherwise handle the intent are blocked. If there are no activities which could handle the intent
 * regardless of policy, returns true. If some activities are allowed and others blocked, returns true. Note that it is not
 * necessary to use this method for policy enforcement. If your app attempts to launch an intent for which there are no
 * allowed activities, MAM will display a dialog explaining the situation to the user.
 *
 * @param intent
 *         intent to check
 *
 * @return whether any activities which could handle this intent are allowed.
*/
boolean areIntentActivitiesAllowed(Intent intent);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 *
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether
 * file encryption is in use. File encryption is transparent to the app, and the app should not need
 * to make any business logic decisions based on this.
 * 
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}
```

> [!NOTE]
> `MAMPolicyManager.getPolicy`은 디바이스 또는 앱에 Intune 관리 정책이 적용되지 않더라도 항상 Null이 아닌 앱 정책을 반환합니다.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>예: 앱에 PIN이 필요한지 확인

앱에 고유 PIN 사용자 환경이 있는 경우 IT 관리자가 앱 PIN을 묻도록 SDK를 구성했으면 이를 사용하지 않게 설정할 수 있습니다. IT 관리자가 이 앱에 앱 PIN 정책을 배포했는지 확인하려면 현재 최종 사용자에 대해 다음 메소드를 호출하세요.

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>예: 기본 Intune 사용자 확인

AppPolicy에 노출된 API 외에도, `MAMUserInfo` 인터페이스에 정의된 `getPrimaryUser()` API를 통해 사용자 계정 이름(**UPN**)도 노출됩니다. UPN을 가져오려면 다음을 호출합니다.

```java
MAMUserInfo info = MAMComponents.get(MAMUserInfo.class);
if (info != null) return info.getPrimaryUser();
```

MAMUserInfo 인터페이스의 전체 정의는 다음과 같습니다.

```java
/**
 * External facing user informations.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if the device is not enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>예: 디바이스 또는 클라우드 스토리지에 저장이 허용되는지 확인

다수의 앱에서는 최종 사용자가 로컬에서나 클라우드 스토리지 서비스에 파일을 저장할 수 있게 하는 기능을 구현합니다. Intune 앱 SDK에서는 IT 관리자가 조직에 적합하다고 판단하는 대로 정책 제한을 적용하여 데이터 누출을 방지할 수 있습니다.  IT 부서가 제어할 수 있는 정책 중 하나는 최종 사용자에게 관리되지 않는 “개인” 데이터 저장소에 저장하도록 허용하는지 여부입니다. 개인 데이터 저장소에는 로컬 위치, SD 카드, 타사 백업 서비스 등이 포함됩니다.

**이 기능을 사용하려면 앱 참여가 필요합니다.** 앱에서 직접 개인 저장소나 클라우드 위치에 저장하는 것이 허용되는 경우에는 이 기능을 구현해야만 IT 관리자가 특정 위치에 저장하는 작업을 허용할지 여부를 제어할 수 있습니다. 아래 API는 현재 Intune 관리자의 정책에 따라 개인 저장소에 저장하는 작업이 허용되는지 여부를 앱에 알립니다. 그러면 앱에서는 최종 사용자가 앱을 통해 사용할 수 있는 개인 데이터 저장소를 인식하므로 정책을 적용할 수 있습니다.  

정책이 적용되는지 여부를 확인하기 위해 다음을 호출합니다.

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

`service` 매개 변수는 다음 `SaveLocation` 값 중 하나여야 합니다.


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

`username`은 저장되는 클라우드 서비스와 연결된 UPN/사용자 이름/이메일이어야 합니다(저장되는 문서를 소유한 사용자와 반드시 같아야 하는 것은 *아님*). AAD UPN와 클라우드 서비스 사용자 이름 간에 매핑이 없거나 사용자 이름을 알 수 없으면 null을 사용합니다.

사용자 정책에서 다양한 위치에 데이터를 저장하도록 허용하는지를 결정하는 이전 메소드는 동일한 **AppPolicy** 클래스에 있는 `getIsSaveToPersonalAllowed()`입니다. 이 함수는 이제 **더 이상 사용되지 않음**이므로 사용하지 않아야 합니다. 다음 호출은 `getIsSaveToPersonalAllowed()`에 해당합니다.

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> 문제의 위치가 **SaveLocations** 열거형에 나열되지 않은 경우 `SaveLocation.OTHER`를 사용합니다.


## <a name="register-for-notifications-from-the-sdk"></a>SDK에서 알림 등록

### <a name="overview"></a>개요
Intune 앱 SDK를 사용하면 IT 관리자가 배포하는 선택적 초기화와 같은 특정 정책의 동작을 앱에서 제어할 수 있습니다. IT 관리자가 해당 정책을 배포하면 Intune 서비스가 알림을 SDK에 보냅니다.

앱은 `MAMNotificationReceiver`를 만든 다음 `MAMNotificationReceiverRegistry`에 등록하여 SDK에서 알림을 등록해야 합니다. 다음 예제에 나온 대로 `App.onCreate`에서 원하는 수신기 및 알림 유형을 제공하면 됩니다.

```java
@Override
public void onCreate() {
  super.onCreate();
  MAMComponents.get(MAMNotificationReceiverRegistry.class)
    .registerReceiver(
      new ToastNotificationReceiver(),
      MAMNotificationType.WIPE_USER_DATA);
  }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

`MAMNotificationReceiver` 인터페이스는 Intune 서비스에서 보내는 알림을 수신합니다. 일부 알림은 SDK에서 직접 처리되지만, 일부 알림의 경우 앱 참여가 필요합니다. 앱은 알림에서 true 또는 false를 반환**해야** 합니다. 알림의 결과로 시도한 일부 작업에서 오류가 발생하지 않는 한 앱은 항상 true를 반환해야 합니다.

* 이 오류는 Intune 서비스에 보고될 수 있습니다. 예를 들어 IT 관리자가 초기화를 시작한 후 앱에서 사용자 데이터를 초기화하지 못한 경우 보고될 수 있습니다.

>[!NOTE]
> 해당 콜백이 UI 스레드에서 실행되고 있지 않기 때문에 `MAMNotificationReceiver.onReceive`에서 차단해도 안전합니다.

SDK에 정의된 `MAMNotificationReceiver` 인터페이스는 아래 포함되어 있습니다.

```java
/**
 * The SDK is signaling that a MAM event has occurred.
 *
 */
public interface MAMNotificationReceiver {

    /**
     * A notification was received.
     *
     * @param notification
     *            The notification that was received.
     * @return The receiver should return true if it handled the
     *   notification without error (or if it decided to ignore the
     *   notification). If the receiver tried to take some action in
     *   response to the notification but failed to complete that
     *   action it should return false.
     */
    boolean onReceive(MAMNotification notification);
}
```

### <a name="types-of-notifications"></a>알림 유형

다음과 같은 알림이 앱에 전송되고, 일부 알림의 경우 앱 참여가 필요할 수 있습니다.

* **WIPE_USER_DATA**: 이 알림은 `MAMUserNotification` 클래스를 통해 전송됩니다. 이 알림이 수신되면 앱에서는 `MAMUserNotification`을 통해 전달된 "회사" ID와 연결된 모든 데이터를 삭제해야 합니다. 이 알림은 현재 APP-WE 서비스 등록 취소 과정에 전송됩니다. 사용자의 기본 이름은 일반적으로 등록 프로세스 동안 지정됩니다. 이 알림에 등록하는 경우 앱에서 모든 사용자 데이터가 삭제되었는지 확인해야 합니다. 이 알림에 등록하지 않는 경우는 기본 선별적 초기화 동작이 수행됩니다.

* **WIPE_USER_AUXILIARY_DATA**: Intune 앱 SDK에서 기본 선택적 초기화 동작을 수행하며 초기화 발생 시 일부 보조 데이터도 제거되도록 하려면 앱에서 이 알림을 등록할 수 있습니다. 이 알림은 단일 ID 앱에는 사용할 수 없습니다. 다중 ID 앱에만 보내집니다.

* **REFRESH_POLICY**: 이 알림은 `MAMUserNotification`을 통해 전송됩니다. 이 알림이 수신되면 앱에서 캐싱한 Intune 정책 결정 사항을 무효화하고 업데이트해야 합니다. 앱에서 정책 가정을 저장하지 않는 경우 이 알림에 등록할 필요가 없습니다.

* **REFRESH_APP_CONFIG**: 이 알림은 `MAMUserNotification`을 통해 전송됩니다. 이 알림이 수신되면 캐싱된 애플리케이션 구성 데이터를 무효화하고 업데이트해야 합니다.

* **MANAGEMENT_REMOVED**: 이 알림은 `MAMUserNotification`을 통해 전송되며 앱이 비관리 상태가 될 것임을 알립니다. 비관리 상태가 되면 더 이상 암호화된 파일을 읽거나, MAMDataProtectionManager로 암호화된 데이터를 읽거나, 암호화된 클립보드와 상호 작용하거나, 관리 앱 에코시스템에 참여할 수 없습니다. 자세한 내용은 아래를 참조하세요.

* **MAM_ENROLLMENT_RESULT**: 이 알림은 APP-WE 등록 시도가 완료되었으니 해당 시도의 상태를 입력하라고 앱에 알리기 위해 `MAMEnrollmentNotification`을 통해 전송됩니다.

* **COMPLIANCE_STATUS**: 이 알림은 규정 준수 수정 시도의 결과를 앱에 알리기 위해 `MAMComplianceNotification`을 통해 전송됩니다.

> [!NOTE]
> 앱에서 `WIPE_USER_DATA`와 `WIPE_USER_AUXILIARY_DATA` 알림 모두를 둘 다 등록할 수 없습니다.

### <a name="management_removed"></a>MANAGEMENT_REMOVED

`MANAGEMENT_REMOVED` 알림은 이전의 정책 관리형 사용자가 더 이상 Intune MAM 정책을 통해 관리되지 않는다는 것을 나타냅니다. 이로 인해 사용자 데이터를 지우거나 사용자를 로그아웃할 필요는 없습니다(데이터를 지워야 하는 경우 `WIPE_USER_DATA` 알림이 전송됨). 대부분의 앱은 이 알림을 처리할 필요가 전혀 없지만, `MAMDataProtectionManager`를 사용하는 앱은 [이 알림에 특별히 주의](#data-protection)해야 합니다.

MAM이 앱의 `MANAGEMENT_REMOVED` 수신기를 호출하면 다음 사항이 적용됩니다.
* MAM은 앱에 속한 이전에 암호화된 파일(하지만 보호되지 않는 데이터 버퍼)을 이미 해독했습니다. 앱에 직접 속하지 않은 sd 카드의 공개 위치(예: Documents 또는 Download 폴더)에 있는 파일은 해독되지 않습니다.
* 수신기 메서드(또는 수신기가 시작된 후 실행되는 다른 코드)가 만든 새 파일 또는 보호되는 데이터 버퍼는 암호화되지 않습니다.
* 앱은 여전히 암호화 키에 액세스할 수 있으므로 암호 해독 데이터 버퍼 같은 작업은 성공합니다.

앱의 수신기가 반환되면 앱은 더 이상 암호화 키에 액세스할 수 없습니다.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Azure ADAL(Active Directory 인증 라이브러리) 구성

먼저 [GitHub의 ADAL 리포지토리](https://github.com/AzureAD/azure-activedirectory-library-for-android)에 있는 ADAL 통합 지침을 읽어 보세요.

SDK가 작동하려면 [인증](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) 및 조건부 시작 시나리오를 위한 [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)이 필요하며, 이 경우 앱에 [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/)를 구성해야 합니다. 구성 값은 AndroidManifest 메타데이터를 통해 SDK에 전달됩니다.

앱을 구성하고 적절한 인증을 사용하려면 다음을 AndroidManifest.xml의 앱 노드에 추가합니다. 이러한 일부 구성은 앱에서 일반적으로 인증에 ADAL을 사용하는 경우에만 필요합니다. 이 경우 앱이 AAD를 사용하여 자체를 등록하는 데 사용하는 특정 값이 필요합니다. 이것은 AAD에서 별개의 두 등록 값(앱의 값 및 SDK의 값)을 인식하기 때문에 최종 사용자에게 인증을 요구하는 메시지가 두 번 나타나는 일이 없도록 하려는 것입니다.

```xml
<meta-data
    android:name="com.microsoft.intune.mam.aad.Authority"
    android:value="https://AAD authority/" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.ClientID"
    android:value="your-client-ID-GUID" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
    android:value="your-redirect-URI" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.SkipBroker"
    android:value="[true | false]" />
```

### <a name="adal-metadata"></a>ADAL 메타데이터

* **Authority**는 사용 중인 AAD 권한입니다. 이 값이 없으면 AAD 공용 환경이 사용됩니다.
    > [!NOTE]
    > 애플리케이션이 소버린 클라우드를 인식하는 경우 이 필드를 설정하지 않습니다.

* **ClientID**는 사용할 AAD ClientID(애플리케이션 ID라고도 함)입니다. Azure AD로 등록된 경우 고유 앱의 ClientID를 사용해야 합니다. 이 값이 없는 경우 Intune 기본값이 사용됩니다.

* **NonBrokerRedirectURI**는 브로커가 없는 경우에 사용할 AAD 리디렉션 URI입니다. 지정된 값이 없으면 기본값인 `urn:ietf:wg:oauth:2.0:oob`가 사용됩니다. 이 기본값은 대부분의 앱에 적합합니다.

  * NonBrokerRedirectURI는 SkipBroker가 "true"인 경우에 사용됩니다.

* **SkipBroker**는 기본 ADAL SSO 참여 동작을 재정의하는 데 사용됩니다. SkipBroker는 ClientID를 지정하는 앱에 대해서만 지정해야 **하며**, 조정된 인증/디바이스 수준 SSO를 지원하지 않습니다. 이 경우 "true"로 설정해야 합니다. 대부분의 앱은 SkipBroker 매개 변수를 설정하면 안 됩니다.

  * ClientID는 **반드시** 매니페스트에서 지정하여 SkipBroker 값을 지정해야 합니다.

  * ClientID가 지정되면 기본값은 "false"입니다.

  * SkipBroker가 "true"이면 NonBrokerRedirectURI가 사용됩니다. ADAL을 통합하지 않는(따라서 ClientID가 없는) 앱도 기본적으로 "true"로 설정합니다.

### <a name="common-adal-configurations"></a>일반적인 ADAL 구성

앱에서 ADAL을 구성할 수 있는 일반적인 방법은 다음과 같습니다. 앱의 구성을 찾아 ADAL 메타데이터 매개변수(위에 설명됨)를 필요한 값으로 설정해야 합니다. 모든 경우에 기본이 아닌 환경에 필요한 경우 Authority를 지정할 수 있습니다. 지정하지 않으면 공개 프로덕션 AAD 기관이 사용됩니다.

#### <a name="1-app-does-not-integrate-adal"></a>1. 앱이 ADAL을 통합하지 않는 경우
ADAL 메타데이터가 매니페스트에 있으면 **안 됩니다**.

#### <a name="2-app-integrates-adal"></a>2. 앱이 ADAL을 통합하는 경우

|필수 ADAL 매개 변수| 값 |
|--|--|
| ClientID | 앱의 ClientID(앱을 등록할 때 Azure AD에서 생성함) |

필요한 경우 기관을 지정할 수 있습니다.

다음과 같이 앱을 Azure AD에 등록하고 앱 보호 정책 서비스에 대한 액세스 권한을 앱에 제공해야 합니다.
* Azure AD에 애플리케이션을 등록하는 방법에 대한 정보는 [여기](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)를 참조하세요.
* APP(앱 보호 정책) 서비스에 대한 Android 앱 권한을 부여하는 단계를 따라야 합니다. 앱에 Intune 앱 보호 서비스에 대한 액세스 권한 부여(선택 사항)에서 [Intune SDK 시작 가이드](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration)의 지침을 따릅니다. 

[조건부 액세스](#conditional-access)를 위한 요구 사항도 참조하세요.


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. 앱이 ADAL을 통합하지만 조정된 인증/디바이스 수준 SSO를 지원하지 않습니다.

|필수 ADAL 매개 변수| 값 |
|--|--|
| ClientID | 앱의 ClientID(앱을 등록할 때 Azure AD에서 생성함) |
| SkipBroker | **True** |

필요한 경우 Authority와 NonBrokerRedirectURI를 지정할 수 있습니다.

### <a name="conditional-access"></a>조건부 액세스

조건부 액세스(CA)는 AAD 리소스에 대한 액세스 제어에 사용할 수 있는 Azure Active Directory [기능](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer)입니다. [Intune 관리자는](https://docs.microsoft.com/intune/conditional-access) Intune에서 관리하는 디바이스 또는 앱으로부터의 리소스 액세스만 허용하는 CA 규칙을 정의할 수 있습니다. 앱이 적절한 때 리소스에 액세스할 수 있게 하려면 아래 단계를 따라야 합니다. 앱이 AAD 액세스 토큰을 획득하지 않아도 되거나, CA로 보호할 수 없는 리소스에만 액세스하는 경우 이 단계를 생략할 수 있습니다.

1. [ADAL 통합 지침](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library)을 따릅니다. 
   특히 11단계에서 브로커 사용을 참조하세요.
2. [Azure Active Directory 테넌트에 애플리케이션 등록](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). 
   리디렉션 URI는 위의 ADAL 통합 지침에서 찾을 수 있습니다.
3. 위의 [공통 ADAL 구성](#common-adal-configurations), 항목 2에 따라 매니페스트 메타데이터 매개 변수를 설정합니다.
4. [Azure Portal](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2)에서 [디바이스 기반 CA](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use)를 사용하도록 설정하고 확인하여 모든 항목이 제대로 구성되었는지 테스트
    - 앱에 로그인하면 Intune Company Portal 설치 및 등록을 위한 프롬프트 표시
    - 등록 후 앱 로그인이 완료됩니다.
5. 앱이 Intune APP SDK 통합을 탑재한 후에는 msintuneappsdk@microsoft.com에 문의하여 [앱 기반 조건부 액세스](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access) 승인 앱 목록에 추가되게 합니다.
6. 앱이 승인 목록에 추가되면 [앱 기반 CA를 구성하고](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create) 앱 로그인이 제대로 완료되는지 확인하여 유효성을 검사합니다.

## <a name="app-protection-policy-without-device-enrollment"></a>디바이스 등록이 없는 앱 보호 정책

### <a name="overview"></a>개요
디바이스 등록이 없는 Intune 앱 보호 정책(APP-WE 또는 MAM-WE라고도 함)은 Intune MDM에 디바이스를 등록하지 않고도 Intune에서 앱을 관리할 수 있도록 허용합니다. APP-WE는 디바이스 등록 유무에 상관없이 작동합니다. 디바이스에 여전히 회사 포털을 설치해야 하지만, 사용자가 회사 포털에 로그인하여 디바이스를 등록하지 않아도 됩니다.

> [!NOTE]
> 모든 앱에서 디바이스 등록이 없는 앱 보호 정책을 지원해야 합니다.

### <a name="workflow"></a>워크플로

앱에서 새 사용자 계정을 만들 때 Intune 앱 SDK에 관리할 계정을 등록해야 합니다. SDK에서 APP-WE 서비스에 앱을 등록하는 세부 정보를 처리합니다. 실패가 발생하면 필요한 경우 적절한 간격으로 등록을 재시도해야 합니다.

사용자가 회사 콘텐츠에 액세스하지 못하게 차단해야 하는지 확인하기 위해 앱이 Intune 앱 SDK에서 등록된 사용자의 상태도 쿼리할 수 있습니다. 관리를 위해 여러 계정을 등록할 수 있지만, 현재로서는 APP-WE 서비스를 통해 한 번에 한 계정만 등록할 수 있습니다. 즉, 앱에서 한 번에 한 계정만 앱 보호 정책을 받을 수 있습니다.

앱은 SDK 대신 ADAL(Azure Active Directory Authentication Library)에서 적절한 액세스 토큰을 획득하는 콜백을 제공해야 합니다. 앱에서 고유 액세스 토큰을 획득하고 사용자 인증을 위해 이미 ADAL을 사용하고 있다고 가정합니다.

앱에서 계정을 완전히 제거하면 앱이 더 이상 해당 사용자에 대해 정책을 적용하지 않아야 함을 표시하도록 해당 계정을 등록 취소해야 합니다. 사용자가 MAM 서비스에 등록된 경우 사용자의 등록이 취소되고 앱이 초기화됩니다.


### <a name="overview-of-app-requirements"></a>앱 요구 사항 개요

APP-WE 통합을 구현하려면 앱에서 MAM SDK에 사용자 계정을 등록해야 합니다.

1. 앱에서 `MAMServiceAuthenticationCallback` 인터페이스의 인스턴스를 구현하고 등록_해야_ 합니다. 콜백 인스턴스는 앱의 수명 주기에서 최대한 빨리 등록해야 합니다(일반적으로 애플리케이션 클래스의 `onMAMCreate()` 메서드 사용).

2. 사용자 계정을 만들고 사용자가 ADAL로 로그인하고 나면 앱이 `registerAccountForMAM()`을 호출_해야_ 합니다.

3. 사용자 계정이 제거되면 앱에서 `unregisterAccountForMAM()`을 호출하여 Intune 관리에서 계정을 제거해야 합니다.

    > [!NOTE]
    > 사용자가 임시로 앱에서 로그아웃하면 앱에서 `unregisterAccountForMAM()`을 호출하지 않아도 됩니다. 이 호출에서 초기화를 시작하여 사용자의 회사 데이터를 완전히 제거할 수 있습니다.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

필수 인증과 등록 API는 모두 `MAMEnrollmentManager` 인터페이스에 있습니다. `MAMEnrollmentManager`에 대한 참조는 다음과 같이 얻을 수 있습니다.

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

반환된 `MAMEnrollmentManager` 인스턴스는 null이 되지 않습니다. API 메서드는 두 가지 범주, 즉 **인증**과 **계정 등록**으로 나뉩니다.

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>계정 인증

이 섹션에서는 `MAMEnrollmentManager`의 인증 API 메서드와 해당 사용 방법에 대해 설명합니다.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. SDK가 지정된 사용자와 리소스 ID에 대한 ADAL 토큰을 요청할 수 있도록 앱에서 `MAMServiceAuthenticationCallback` 인터페이스를 구현해야 합니다. `registerAuthenticationCallback()` 메소드를 호출하여 `MAMEnrollmentManager`에 콜백 인스턴스를 제공해야 합니다. 앱 수명 주기 중 초기에 등록 재시도 또는 앱 보호 정책 새로 고침 체크인을 위해 토큰이 필요할 수 있으므로 콜백을 등록하는 데 이상적인 위치는 앱 `MAMApplication` 하위 클래스의 `onMAMCreate()` 메서드에 있습니다.

2. `acquireToken()` 메서드에서 지정된 사용자에 대해 요청된 리소스 ID의 액세스 토큰을 획득해야 합니다. 요청된 토큰을 획득할 수 없으면 null을 반환해야 합니다.

    > [!NOTE]
    > 올바른 토큰을 획득할 수 있도록 앱이 `acquireToken()`에 전달된 `resourceId` 및 `aadId` 매개 변수를 사용해야 합니다.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. SDK가 `acquireToken()`을 호출할 때 앱에서 토큰을 제공할 수 없으면, 예를 들어 자동 인증에 실패하고 UI를 표시하기에 적절하지 않은 경우 앱에서 `updateToken()` 메서드를 호출하여 나중에 토큰을 제공할 수 있습니다. 이전 `acquireToken()` 호출을 통해 요청한 동일한 UPN, AAD ID 및 리소스 ID를 마지막으로 획득한 토큰과 함께 `updateToken()`에 전달해야 합니다. 제공된 콜백에서 null을 반환한 다음 앱에서 최대한 빨리 이 메서드를 호출해야 합니다.

    > [!NOTE]
    > SDK에서 토큰을 가져오기 위해 주기적으로 `acquireToken()`을 호출하므로 `updateToken()`을 반드시 호출할 필요가 없습니다. 그러나 등록과 앱 보호 정책 체크 인이 적시에 완료될 수 있으므로 호출하는 것이 매우 좋습니다.


### <a name="account-registration"></a>계정 등록

이 섹션에서는 `MAMEnrollmentManager`의 계정 등록 API 메서드와 해당 사용 방법에 대해 설명합니다.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. 관리 계정을 등록하려면 앱에서 `registerAccountForMAM()`을 호출해야 합니다. 사용자 계정은 UPN과 AAD 사용자 ID 모두를 사용하여 식별합니다. 등록 데이터를 사용자의 AAD 테넌트와 연결하려면 테넌트 ID도 필요합니다. 사용자 권한을 제공하여 특정 소버린 클라우드의 등록을 허용할 수도 있습니다. 자세한 내용은 [소버린 클라우드 등록](#sovereign-cloud-registration)을 참조하세요.  SDK가 MAM 서비스에서 지정된 사용자의 앱을 등록하려고 시도할 수 있습니다. 등록에 실패하면 계정을 등록 취소할 때까지 주기적으로 등록을 시도합니다. 재시도 기간은 일반적으로 12~24시간입니다. SDK에서는 알림을 통해 비동기적으로 등록 시도 상태를 제공합니다.

2. AAD 인증이 필요하므로 사용자가 앱에 로그인한 후 ADAL을 사용하여 성공적으로 인증되고 나면 사용자 계정을 등록하는 것이 좋습니다. 사용자의 AAD ID와 테넌트 ID가 [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android) 개체의 일부로 ADAL 인증 호출에서 반환됩니다.
    * 테넌트 ID는 `AuthenticationResult.getTenantID()` 메서드를 통해 제공됩니다.
    * 사용자에 대한 정보는 `AuthenticationResult.getUserInfo()`에서 제공되는 `UserInfo` 유형의 하위 개체에 있으며, AAD 사용자 ID는 `UserInfo.getUserId()`를 호출하여 해당 개체에서 검색합니다.

3. Intune 관리에서 계정을 등록 취소하려면 앱에서 `unregisterAccountForMAM()`을 호출해야 합니다. 계정이 성공적으로 등록되어 관리되면 SDK에서 계정의 등록을 취소하고 데이터를 초기화합니다. 계정을 주기적으로 등록하려는 시도도 중지됩니다. SDK에서는 알림을 통해 비동기적으로 등록 취소 요청 상태를 제공합니다.

### <a name="sovereign-cloud-registration"></a>소버린 클라우드 등록

[소버린 클라우드 인식](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) 애플리케이션은 `authority`를 `registerAccountForMAM()`에 제공해야 **합니다**.  이 정보는 AuthenticationCallback AuthenticationResult에서 `getAuthority()` 호출 앞에 오는 ADAL의 [1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) acquireToken extraQueryParameters에서 `instance_aware=true`를 제공하여 구할 수 있습니다.

```java
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> AndroidManifest.xml에서 `com.microsoft.intune.mam.aad.Authority` 메타데이터 항목을 설정하지 않습니다.

> [!NOTE]
> `MAMServiceAuthenticationCallback::acquireToken()` 메서드에서 권한이 올바르게 설정되었는지 확인합니다.

#### <a name="currently-supported-sovereign-clouds"></a>현재 지원되는 소버린 클라우드

1. Arlington

### <a name="important-implementation-notes"></a>중요한 구현 참고 사항

#### <a name="authentication"></a>인증

* 앱에서 `registerAccountForMAM()`을 호출할 때 다른 스레드에서 잠시 후에 해당 `MAMServiceAuthenticationCallback` 인터페이스에 대한 콜백을 받을 수 있습니다. 이상적으로, 앱은 요청된 토큰의 획득을 신속하게 하기 위해 계정을 등록하기 전 ADAL에서 자체 토큰을 획득하는 것이 좋습니다. 앱이 콜백에서 유효한 토큰을 반환하면 등록이 진행되고 앱이 알림을 통해 최종 결과를 받습니다.

* 엡에서 유효한 AAD 토큰을 반환하지 않으면 등록을 시도한 후의 최종 결과는 `AUTHENTICATION_NEEDED`입니다. 앱이 알림을 통해 이 결과를 받으면 이전에 `acquireToken()`에서 요청한 사용자 및 리소스의 토큰을 획득하고 등록 프로세스를 다시 시작하기 위해 `updateToken()` 메서드를 호출하여 등록 프로세스를 단축할 것을 강력하게 권장합니다.

* 주기적 앱 보호 정책 새로 고침 체크인을 위한 토큰을 획득하기 위해 앱의 등록된 `MAMServiceAuthenticationCallback`도 호출됩니다. 요청 시 앱에서 토큰을 제공할 수 없으면 알림을 받지 못하지만, 체크인 프로세스를 빠르게 수행하도록 다음 번 적절한 시기에 토큰을 획득하고 `updateToken()`을 호출하도록 시도해야 합니다. 토큰을 제공하지 않으면 다음 번 체크인 시에도 여전히 콜백이 호출됩니다.

* 소버린 클라우드 지원을 위해서는 권한을 제공해야 합니다.

#### <a name="registration"></a>등록

* 사용자의 편의를 위해 등록 메서드는 idempotent입니다. 예를 들어, 계정이 아직 등록되지 않은 경우 `registerAccountForMAM()`에서는 계정을 등록하고 앱을 등록만 하려고 하며, 현재 등록된 경우 `unregisterAccountForMAM()`에서는 계정을 등록 취소만 합니다. 그 이후의 호출은 작동하지 않으므로 이 메서드를 두 번 이상 호출해도 문제가 되지 않습니다. 또한 이러한 메서드의 호출과 결과 알림이 서로 대응하지 않을 수 있습니다. 즉, 이미 등록된 ID에 대해 `registerAccountForMAM`이 호출되면 해당 ID에 대해 알림이 다시 전송되지 않을 수 있습니다. SDK가 백그라운드에서 주기적으로 등록을 시도하고 Intune 서비스에서 받은 초기화 요청을 통해 등록 취소가 트리거될 수 있으므로, 이러한 메서드 호출에 해당하지 않는 알림이 전송될 수 있습니다.

* 여러 다른 ID에 대해 등록 메서드를 호출할 수 있지만, 현재로서는 하나의 사용자 계정만 등록될 수 있습니다. Intune에 대한 사용권이 있으며 앱 보호 정책을 통해 대상으로 지정된 여러 사용자 계정이 동시 또는 거의 동시에 등록되는 경우 어떤 계정이 등록될지 모릅니다.

* 마지막으로 `MAMEnrollmentManager`를 쿼리하여 특정 계정이 등록되었는지 확인하고 `getRegisteredAccountStatus` 메서드를 사용하여 현재 상태를 가져올 수 있습니다. 제공된 계정이 등록되지 않은 경우 이 메서드에서 **null**을 반환합니다. 계정이 등록되면 이 메서드에서 `MAMEnrollmentManager.Result` 열거형의 멤버 중 하나로 계정의 상태를 반환합니다.

### <a name="result-and-status-codes"></a>결과 및 상태 코드

계정을 처음 등록하면 `PENDING` 상태로 시작하여, 초기 MAM 서비스 등록 시도가 완료되지 않았음을 나타냅니다. 등록 시도가 완료되면 아래 테이블의 결과 코드 중 하나를 포함한 알림이 전송됩니다. 또한 `getRegisteredAccountStatus()` 메서드에서 계정의 상태를 반환하므로, 해당 사용자가 회사 콘텐츠에 액세스하지 못하게 차단되었는지 앱에서 항상 확인할 수 있습니다. SDK가 백그라운드에서 등록을 재시도하므로 등록에 실패해도 시간이 경과함에 따라 계정의 상태가 변경될 수 있습니다.

|결과 코드 | 설명 |
| -- | -- |
|AUTHORIZATION_NEEDED | 이 결과는 앱의 등록된 `MAMServiceAuthenticationCallback` 인스턴스에서 토큰을 제공하지 않거나 제공된 토큰이 유효하지 않음을 나타냅니다.  가능하면 앱에서 유효한 토큰을 획득하고 `updateToken()`을 호출해야 합니다. |
| NOT_LICENSED | 사용자에게 Intune에 대한 사용권이 없거나 Intune MAM 서비스에 연결하려 했지만 실패했습니다.  앱은 비관리(정상) 상태로 지속되어야 하며 사용자를 차단하지 않아야 합니다.  사용자에게 나중에 사용권이 부여되는 경우를 대비하여 주기적으로 등록을 시도합니다. |
| ENROLLMENT_SUCCEEDED | 등록에 성공하거나 사용자가 이미 등록되었습니다.  등록에 성공하면 이 알림 전에 정책 새로 고침 알림이 전송됩니다.  회사 데이터에 액세스하도록 허용해야 합니다. |
| ENROLLMENT_FAILED | 등록에 실패했습니다.  자세한 내용은 디바이스 로그에 있습니다.  사용자에게 Intune에 대한 사용권이 있음이 이미 확인되었으므로 앱에서는 이 상태로 회사에 액세스하게 허용하지 않아야 합니다.|
| WRONG_USER | MAM 서비스를 통해 디바이스당 한 명의 사용자만 앱을 등록할 수 있습니다.  다른 사용자로 등록하려면 등록된 모든 앱을 먼저 등록 취소해야 합니다.  그렇지 않으면 이 앱을 기본 사용자로 등록해야 합니다.  사용권을 확인한 다음 이 검사가 수행되므로, 앱을 성공적으로 등록할 때까지 사용자가 회사 데이터에 액세스하지 못하게 차단해야 합니다.|
| UNENROLLMENT_SUCCEEDED | 등록이 취소되었습니다.|
| UNENROLLMENT_FAILED | 등록 취소 요청이 실패했습니다.  자세한 내용은 디바이스 로그에 있습니다. |
| PENDING | 사용자의 초기 등록을 진행 중입니다.  등록 결과를 알 때까지 앱에서 회사 데이터에 대한 액세스를 차단할 수 있지만, 필수는 아닙니다. |
| COMPANY_PORTAL_REQUIRED | Intune에 대한 사용권이 부여되지만, 디바이스에 회사 포털 앱을 설치해야 앱을 등록할 수 있습니다. Intune 앱 SDK에서 지정된 사용자가 앱에 액세스하지 못하게 차단하고 회사 포털 앱을 설치하도록 지시합니다(자세한 내용은 아래 참조). |


### <a name="company-portal-requirement-prompt-override-optional"></a>회사 포털 요구 사항 프롬프트 재정의(선택사항)

`COMPANY_PORTAL_REQUIRED` 결과를 받으면 SDK에서 등록이 요청된 ID를 사용하는 활동의 사용을 차단합니다. 대신 SDK에서는 해당 활동이 회사 포털을 다운로드하도록 프롬프트를 표시합니다. 앱에서 이 동작을 방지하려면 활동을 통해 `MAMActivity.onMAMCompanyPortalRequired`를 구현할 수 있습니다.

이 메서드는 SDK에서 기본 차단 UI를 표시하기 전에 호출됩니다. 앱에서 활동 ID를 변경하거나 등록을 시도한 사용자의 등록을 취소하면 SDK가 활동을 차단하지 않습니다. 이 경우 앱에서 회사 데이터가 누수되지 않게 합니다. 다중 ID 앱(뒷부분에서 설명)만 작업 ID를 변경할 수 있습니다.

`MAMActivity`를 명시적으로 상속하지 않지만(빌드 도구를 통해 변경) 이 알림을 처리해야 하는 경우, `MAMActivityBlockingListener`를 대신 구현할 수 있습니다.

### <a name="notifications"></a>알림

앱이 **MAM_ENROLLMENT_RESULT** 형식의 알림을 등록하면 등록 요청이 완료되었음을 앱에 알리기 위해 `MAMEnrollmentNotification`이 전송됩니다. `MAMEnrollmentNotification`은 [SDK에서 알림 등록](#register-for-notifications-from-the-sdk) 섹션에 설명된 대로 `MAMNotificationReceiver` 인터페이스를 통해 받습니다.

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

`getEnrollmentResult()` 메서드에서 등록 요청의 결과를 반환합니다.  `MAMEnrollmentNotification`에서 `MAMUserNotification`을 확장하므로 등록을 시도하는 사용자의 ID도 사용 가능합니다. [SDK에서 알림 등록](#register-for-notifications-from-the-sdk) 섹션에 자세히 설명된 대로 앱에서 이러한 알림을 받도록 `MAMNotificationReceiver` 인터페이스를 구현해야 합니다.

등록 알림을 받을 때 등록된 사용자 계정의 상태가 변경될 수 있지만, 모든 경우에 변경되지는 않습니다(예: `WRONG_USER`와 같은 자세한 정보를 포함하는 결과 다음에 `AUTHORIZATION_NEEDED` 알림을 받으면, 자세한 정보를 포함하는 결과가 계정의 상태로 유지 관리됨).  계정이 성공적으로 등록되면 계정이 등록 취소되거나 초기화될 때까지 `ENROLLMENT_SUCCEEDED` 상태로 유지됩니다.

등록 알림을 받을 때 등록된 사용자 계정의 상태가 변경될 수 있지만, 모든 경우에 변경되지는 않습니다(예: `WRONG_USER`와 같은 자세한 정보를 포함하는 결과 다음에 `AUTHORIZATION_NEEDED` 알림을 받으면, 자세한 정보를 포함하는 결과가 계정의 상태로 유지 관리됨).  계정이 성공적으로 등록되면 계정이 등록 취소되거나 초기화될 때까지 `ENROLLMENT_SUCCEEDED` 상태로 유지됩니다.

## <a name="app-ca-with-policy-assurance"></a>APP CA with Policy Assurance

### <a name="overview"></a>개요
APP CA(Conditional Access) with Policy Assurance를 사용하면 Intune 앱 보호 정책 애플리케이션에서 리소스 액세스가 조건부로 허용됩니다.  AAD는 APP CA with Policy Assurance 보호된 리소스에 대한 액세스 권한을 액세스 토큰에 부여하기 전에 앱을 등록하고 APP을 통해 관리할 것을 요구하여 조건부 액세스를 적용합니다.  앱은 토큰 획득에 ADAL 브로커를 사용해야 하고, 설정은 위의 [조건부 액세스](#conditional-access)에 설명한 것과 동일합니다.

### <a name="adal-changes"></a>ADAL 변경
ADAL 라이브러리에는 앱에 APP 관리 규정을 준수하지 않아 토큰 획득에 실패했다고 알려주는 새로운 오류 코드가 있습니다.  앱이 이 오류 코드를 수신하는 경우 앱을 등록하고 정책을 적용하여 규정 준수 문제를 해결하도록 SDK를 호출해야 합니다. ADAL `AuthenticationCallback`의 `onError()` 메서드에서 예외를 수신하고 `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED` 오류 코드를 받게 됩니다.  이 경우 예외를 `IntuneAppProtectionPolicyRequiredException`에 캐스팅하고, 규정 준수 문제 해결에 사용할 추가 매개 변수를 추출할 수 있습니다(아래 코드 샘플 참조). 문제 해결에 성공하면 앱이 ADAL을 통해 토큰 획득을 다시 시도할 수 있습니다.

> [!NOTE]
> 새 오류 코드 및 APP CA with Policy Assurance에 대 한 지원에는 ADAL 라이브러리 버전 1.15.0 이상이 필요합니다.

### <a name="mamcompliancemanager"></a>MAMComplianceManager

ADAL에서 정책 필요 오류가 수신되면 `MAMComplianceManager` 인터페이스가 사용됩니다.  이 인터페이스에는 앱을 규정 준수 상태로 만들기 위해 호출해야 하는 `remediateCompliance()` 메서드가 포함되어 있습니다. `MAMComplianceManager`에 대한 참조는 다음과 같이 얻을 수 있습니다.

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

반환된 `MAMComplianceManager` 인스턴스는 null이 되지 않습니다.

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

AAD가 요청된 토큰을 제공하기 위한 조건을 충족할 수 있도록, 앱을 관리 대상에 넣으려고 시도하는 `remediateCompliance()` 메서드가 호출됩니다.  처음 네 개 매개 변수는 ADAL `AuthenticationCallback.onError()` 메서드가 수신한 예외에서 추출할 수 있습니다(아래 코드 샘플 참조).  마지막 매개 변수는 규정 준수를 시도하는 동안 UX 표시 여부를 제어하는 부울입니다.  다음은 이 작업이 진행되는 동안 사용자 지정된 UX를 표시할 필요가 없는 앱의 기본값으로 제공되는 간단한 차단 진행률 스타일 인터페이스입니다.  규정 준수 문제 해결이 진행되는 동안에만 차단하며 최종 결과를 표시하지 않습니다.  앱은 규정 준수 문제 해결 시도의 성공 또는 실패를 처리하는 알림 수신기를 등록해야 합니다(아래 참조).

`remediateCompliance()` 메서드는 규정 준수 설정의 일부로 MAM 등록을 수행할 수 있습니다.  앱이 등록 알림을 위한 알림 수신기를 등록한 경우 등록 알림을 받게 될 수 있습니다.  앱의 등록된 `MAMServiceAuthenticationCallback`은 MAM 등록을 위한 토큰을 얻기 위해 `acquireToken()` 메서드를 호출할 것입니다. `acquireToken()`은 앱이 자체 토큰을 획득하기 전에 호출되므로, 앱이 토큰 획득 이후에 수행하는 기록 또는 계정 만들기 작업이 아직 완료되지 않았을 수 있습니다.  이 경우 콜백이 토큰을 획득할 수 있어야 합니다.  `acquireToken()`에서 토큰을 반환할 수 없는 경우 규정 준수 문제 해결 시도가 실패합니다.  나중에 요청된 리소스에 대한 유효한 토큰을 사용하여 `updateToken()`을 호출하면 제공된 토큰을 사용하여 규정 준수 문제 해결이 즉시 다시 시도됩니다.

> [!NOTE]
> 사용자는 `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED` 오류가 발생하기 전에 이미 broker를 설치하고 디바이스를 등록하는 방법을 배웠을 것이므로 여전히 `acquireToken()`에서 자동 토큰 획득이 가능합니다.  이로 인해 broker의 캐시에 유효한 새로 고침 토큰이 있으므로 요청된 토큰의 자동 획득이 성공할 수 있습니다.

다음은 `AuthenticationCallback.onError()` 메서드에서 정책 필요 오류를 수신한 다음, `MAMComplianceManager`를 호출하여 오류를 처리하는 샘플입니다.

```java
public void onError(@Nullable Exception exc) {
    if (exc instanceof AuthenticationException && 
        ((AuthenticationException) exc).getCode() == ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED) {

        final IntuneAppProtectionPolicyRequiredException policyRequiredException = 
            (IntuneAppProtectionPolicyRequiredException) ex;

        final String upn = policyRequiredException.getAccountUpn();
        final String aadId = policyRequiredException.getAccountUserId();
        final String tenantId = policyRequiredException.getTenantId();
        final String authority = policyRequiredException.getAuthorityURL();

        MAMComplianceManager complianceManager = MAMComponents.get(MAMComplianceManager.class);
        complianceManager.remediateCompliance(upn, aadId, tenantId, authority, showUX);
    }
}
```

### <a name="status-notifications"></a>상태 알림

앱이 **COMPLIANCE_STATUS** 형식의 알림에 등록하면 앱에 규정 준수 문제 해결 시도의 최종 상태를 알리기 위해 `MAMComplianceNotification`이 전송됩니다. `MAMComplianceNotification`은 [SDK에서 알림 등록](#register-for-notifications-from-the-sdk) 섹션에 설명된 대로 `MAMNotificationReceiver` 인터페이스를 통해 받습니다.

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

`getComplianceStatus()` 메서드는 규정 준수 문제 해결 시도의 결과를 `MAMCAComplianceStatus` 열거형의 값으로 반환합니다.

|상태 코드 | 설명 |
| -- | -- |
| 알 수 없음 | 상태를 알 수 없습니다. 예기치 않은 실패 이유를 나타내는 것일 수 있습니다. 회사 포털 로그에서 추가 정보를 찾을 수 있습니다. |
| 규정 준수 | 규정 준수 문제 해결이 성공하여 앱이 이제 정책을 준수합니다. ADAL 토큰 획득을 다시 시도해야 합니다. |
| NOT_COMPLIANT | 규정 준수 문제를 해결하기 위한 시도가 실패했습니다.  앱이 규정을 준수하지 않으므로 오류 조건을 해결하기 전에는 ADAL 토큰 획득을 다시 시도하면 안 됩니다.  추가 오류 정보가 MAMComplianceNotification과 함께 전송됩니다. |
| SERVICE_FAILURE | Intune 서비스에서 규정 준수 데이터를 검색하는 동안 오류가 발생했습니다. 회사 포털 로그에서 추가 정보를 찾을 수 있습니다. |
| NETWORK_FAILURE | Intune 서비스에 연결할 때 오류가 발생했습니다. 네트워크 연결이 복원되면 앱에서 토큰 획득을 다시 시도해야 합니다. |
| CLIENT_ERROR | 클라이언트와 관련된 어떤 이유로 규정 준수 문제 해결 시도가 실패했습니다.  예를 들어 토큰이 없거나 잘못된 사용자가 원인일 수 있습니다. 추가 오류 정보가 MAMComplianceNotification과 함께 전송됩니다. |
| PENDING | 시간 제한을 초과했을 때 서비스에서 상태 응답이 도착하지 않아 규정 준수 문제 해결 시도가 실패했습니다. 앱이 나중에 토큰 획득을 다시 시도해야 합니다. |
| COMPANY_PORTAL_REQUIRED | 규정 준수 문제 해결을 성공하려면 디바이스에 회사 포털을 설치해야 합니다.  디바이스에 회사 포털이 이미 설치된 경우 앱을 다시 시작해야 합니다.  이 경우 사용자에게 앱을 다시 시작할 것을 요청하는 대화 상자가 표시됩니다. |

규정 준수 상태가 `MAMCAComplianceStatus.COMPLIANT`인 경우 앱은 자체 리소스에 대한 원래 토큰 획득을 다시 시작해야 합니다. 규정 준수 수정 문제 해결 시도가 실패한 경우 `getComplianceErrorTitle()` 및 `getComplianceErrorMessage()` 메서드는 앱이 최종 사용자에게 표시할 수 있는(표시하도록 선택하는 경우) 지역화된 문자열을 반환합니다.  대부분의 오류는 앱에서 해결할 수 없으므로 일반적인 오류인 경우 계정 만들기 또는 로그인을 실패로 처리하고 사용자가 나중에 다시 시도할 수 있게 하는 것이 가장 좋습니다.  오류가 계속되면 MAM 로그를 검토하여 원인을 파악할 수 있습니다.  최종 사용자는 [여기](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "회사 지원팀에 이메일로 로그 보내기")의 지침에 따라 로그를 제출할 수 있습니다.

`MAMComplianceNotification`에서 `MAMUserNotification`을 확장하므로 복원을 시도한 사용자의 ID도 사용 가능합니다.

다음은 MAMNotificationReceiver 인터페이스를 구현하기 위해 익명 클래스를 사용하여 수신기를 등록하는 예제입니다.

```java
final MAMNotificationReceiverRegistry notificationRegistry = MAMComponents.get(MAMNotificationReceiverRegistry.class);
// create a receiver
final MAMNotificationReceiver receiver = new MAMNotificationReceiver() {
    public boolean onReceive(MAMNotification notification) {
        if (notification.getType() == MAMNotificationType.COMPLIANCE_STATUS) {
            MAMComplianceNotification complianceNotification = (MAMComplianceNotification) notification;
            
            // take appropriate action based on complianceNotification.getComplianceStatus()
            
            // unregister this receiver if no longer needed
            notificationRegistry.unregisterReceiver(this, MAMNotificationType.COMPLIANCE_STATUS);
        }
        return true;
    }
};
// register the receiver
notificationRegistry.registerReceiver(receiver, MAMNotificationType.COMPLIANCE_STATUS);
```

> [!NOTE]
> 알림이 누락될 수 있는 경합 상태를 피하려면 `remediateCompliance()`를 호출하기 전에 알림 수신기를 등록해야 합니다.

### <a name="implementation-notes"></a>구현 노트

> [!NOTE]
> 앱의 `MAMServiceAuthenticationCallback.acquireToken()` 메서드는 broker를 강제로 새로 고칠 수 있도록 `acquireTokenSilentSync()`의 새 `forceRefresh` 플래그에 대한 값으로 *true*를 전달해야 합니다.  이는 MAM 서비스 토큰에 영향을 줄 수 있는 ADAL 토큰의 캐싱 이슈를 해결하기 위한 조치입니다. 일반적으로 다음과 비슷한 형태입니다.
>
> ```java
> AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ true);
> ```

> [!NOTE]
> 문제 해결을 시도하는 동안 사용자 지정 차단 UX를 표시하려면 `remediateCompliance()`의 showUX 매개 변수에 대한 값으로 *false*를 전달해야 합니다. UX를 표시하고 알림 수신기를 등록한 후 `remediateCompliance()`를 호출해야 합니다.  이렇게 하면 `remediateCompliance()`가 매우 빠르게 실패할 경우 알림이 누락될 수 있는 경합 상태를 방지할 수 있습니다.  예를 들어 Activity 서브클래스의 `onCreate()` 또는 `onMAMCreate()` 메서드는 알림 수신기를 등록한 후 `remediateCompliance()`를 호출하는 가장 이상적인 장소입니다.  `remediateCompliance()`의 매개 변수는 UX에 의도 추가 기능으로 전달할 수 있습니다.  규정 준수 상태 알림이 수신되면 결과를 표시할 수도 있고, 작업을 그냥 완료할 수도 있습니다.

> [!NOTE]
> `remediateCompliance()`는 계정을 등록하고 등록을 시도합니다.  주 토큰을 획득하면 `registerAccountForMAM()`을 호출할 필요가 없지만, 호출해도 아무 문제 없습니다. 반면, 앱이 토큰 획득에 실패하여 사용자 계정을 제거하려는 경우 `unregisterAccountForMAM()`을 호출하여 계정을 제거하고 백그라운드 등록 재시도를 차단해야 합니다.

## <a name="protecting-backup-data"></a>백업 데이터 보호

Android Marshmallow(API 23) 현재, Android에는 앱이 데이터를 백업하는 두 가지 방법이 있습니다. 각 옵션을 앱에서 사용할 수 있으며 여러 단계를 거쳐 Intune 데이터 보호가 적절하게 구현되도록 해야 합니다. 아래 표를 검토하면 올바른 데이터 보호 동작에 필요한 적절한 작업에 대해 살펴볼 수 있습니다.  [Android API 가이드](https://developer.android.com/guide/topics/data/backup.html)에서 백업 방법에 대해 알아볼 수 있습니다.

### <a name="auto-backup-for-apps"></a>앱에 대한 자동 백업

Android는 앱의 대상 API에 관계없이 Android Marshmallow 디바이스에서 앱의 Google Drive에 [자동 전체 백업](https://developer.android.com/guide/topics/data/autobackup.html) 기능을 제공하기 시작했습니다. AndroidManifest.xml에서 `android:allowBackup`을 **false**로 명시적으로 설정하면 앱은 Android에서 수행하는 백업용 큐에 추가되지 않고 “회사” 데이터가 앱 내에서 유지됩니다. 이 경우 추가 작업이 필요하지 않습니다.

그러나 매니페스트 파일에서 `android:allowBackup`을 지정하지 않더라도 기본적으로 `android:allowBackup` 특성은 true로 설정됩니다. 즉, 모든 앱 데이터가 사용자의 Google Drive 계정에 자동으로 백업되는, 이 동작은 **데이터 누출의 위험**이 있습니다. 따라서 데이터 보호가 적용되도록 아래 개략적인 설명대로 SDK를 변경해야 합니다.  Android Marshmallow 디바이스에서 앱을 실행하려면 아래의 지침에 따라 고객 데이터를 제대로 보호해야 합니다.  

Intune을 통해 XML에서 사용자 지정 규칙을 정의하는 기능을 비롯하여 Android에서 제공하는 모든 [자동 백업 기능](https://developer.android.com/guide/topics/data/autobackup.html)을 이용할 수 있지만 아래 단계에 따라 데이터를 보호해야 합니다.

1. 앱에서 고유 사용자 지정 BackupAgent를 사용하지 **않으면** Intune 정책을 준수하는 자동 전체 백업을 허용하려면 기본 MAMBackupAgent를 사용합니다. 앱 매니페스트에 다음을 둡니다.

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```


2. **[선택사항]** 선택적 사용자 지정 BackupAgent를 구현한 경우 MAMBackupAgent 또는 MAMBackupAgentHelper를 사용해야 합니다. 다음 섹션을 참조하세요. Android M 이상에서 쉬운 백업을 제공하는 Intune의 **MAMDefaultFullBackupAgent**(1단계에 설명됨)로 전환하는 것이 좋습니다.

3. 앱이 받아야 하는 전체 백업 유형을 결정할 경우(필터링되지 않음, 필터링됨 또는 없음) 앱에서 `android:fullBackupContent` 특성을 true, false 또는 XML 리소스로 설정해야 합니다.

4. 그런 다음 `android:fullBackupContent`에 넣은 내용이 무엇이든 매니페스트에서 `com.microsoft.intune.mam.FullBackupContent`라는 메타데이터 태그에 복사 _**해야**_ 합니다.

    **예제 1**: 앱에 예외 없이 전체가 백업되도록 하려면 `android:fullBackupContent` 특성과 `com.microsoft.intune.mam.FullBackupContent` 메타데이터 태그를 모두 **true**로 설정합니다.

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **예제 2**: 앱에서 사용자 지정 BackupAgent를 사용하고 Intune 정책을 준수하는 전체 자동 백업에서 옵트아웃하려면 특성과 메타데이터 태그를 **false**로 설정해야 합니다.

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **예제 3**: XML 파일에 정의된 사용자 지정 규칙에 따라 앱에 전체 백업이 있도록 특성과 메타데이터 태그를 동일한 XML 리소스로 설정합니다.

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```


### <a name="keyvalue-backup"></a>Key/Value Backup

[키/값 백업](https://developer.android.com/guide/topics/data/keyvaluebackup.html) 옵션이 모든 API 8+에서 사용 가능하며, 앱 데이터를 [Android 백업 서비스](https://developer.android.com/google/backup/index.html)에 업로드합니다. 앱의 사용자당 데이터 크기는 5MB로 제한됩니다. 키/값 백업을 사용하는 경우 **BackupAgentHelper** 또는 **BackupAgent**를 사용해야 합니다.

### <a name="backupagenthelper"></a>BackupAgentHelper

BackupAgentHelper는 기본 Android 기능 및 Intune MAM 통합 면에서 BackupAgent에 비해 훨씬 더 간단하게 구현할 수 있습니다. BackupAgentHelper의 경우 개발자는 전체 파일 및 공유 기본 설정을 **FileBackupHelper** 및 **SharedPreferencesBackupHelper**에 각각 등록할 수 있으며 이들 항목은 생성된 BackupAgentHelper에 추가됩니다. 아래 단계를 따라 Intune MAM과 함께 BackupAgentHelper를 사용합니다.

1. BackupAgentHelper를 사용하여 다중 ID 백업을 활용하려면 Android 가이드를 따라 [BackupAgentHelper 확장](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper)을 수행합니다.

2. 클래스에서 BackupAgentHelper, FileBackupHelper 및 SharedPreferencesBackupHelper에 해당하는 MAM의 항목을 확장하게 합니다.

|Android 클래스 | MAM 해당 항목 |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

다음 지침을 따르면 다중 ID 백업 및 복원에 성공합니다.

### <a name="backupagent"></a>BackupAgent

BackupAgent를 사용하면 백업되는 데이터에 대해 훨씬 더 명확히 지정할 수 있습니다. 개발자가 구현을 수행해야 하므로 Intune에서 데이터를 적절하게 보호하기 위해 필요한 추가 단계가 있습니다. 대부분의 작업을 개발자가 담당하게 되므로, Intune 통합이 약간 더 개입됩니다.

**MAM 통합:**

1. BackupAgent 구현에서 Android 지침을 따르도록 [키/값 백업](https://developer.android.com/guide/topics/data/keyvaluebackup.html) 및 특히 [BackupAgent 확장](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent)에 대한 Android 설명서를 자세히 읽어 보세요.

2. 클래스에서 `MAMBackupAgent` 확장하게 합니다.

**다중 ID 백업:**

1. 백업을 시작하기 전에 다중 ID 시나리오에서 백업하려는 파일 또는 데이터 버퍼를 **IT 관리자가 백업하도록 허용**되는지 확인합니다. 이를 확인하도록 `MAMFileProtectionManager` 및 `MAMDataProtectionManager`에서 `isBackupAllowed` 함수를 제공합니다. 파일 또는 데이터 버퍼를 백업하도록 허용하지 않는 경우에는 백업에 계속 포함하지 않아야 합니다.

2. 1단계에 확인한 파일의 ID를 백업하려는 경우에는 백업 도중 특정 시점에 데이터를 추출할 파일에 대해 `backupMAMFileIdentity(BackupDataOutput data, File … files)`를 호출해야 합니다. 그러면 자동으로 새 백업 엔터티가 생성되고 이 엔터티가 `BackupDataOutput` 에 작성됩니다. 이러한 엔터티는 복원 시 자동으로 사용됩니다.

**다중 ID 복원:**

데이터 백업 안내서에서는 애플리케이션의 데이터를 복원하는 일반 알고리즘을 지정하고 [BackupAgent 확장](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) 섹션에서 코드 샘플을 제공합니다. 다중 ID 복원에 성공하려면 이 코드 샘플에 제공된 일반 구조를 따르고 다음에 특히 주의해야 합니다.

1. `while(data.readNextHeader())`* 루프를 활용하여 백업 엔티티를 조사해야 합니다.

2. `data.getKey()`*가 `onBackup`에서 작성한 키와 일치하지 않으면 `data.skipEntityData()`*를 호출해야 합니다. 이 단계를 수행하지 않으면 복원에 성공하지 못할 수 있습니다.

3. 자동으로 작성하는 엔티티가 유실되므로, `while(data.readNextHeader())`* 구성에서 백업 엔티티를 사용하는 동안 반환하지 마세요.

* 여기서 `data`는 복원 시 앱에 전달되는 **MAMBackupDataInput**의 지역 변수 이름입니다.

## <a name="multi-identity-optional"></a>다중 ID(선택사항)

### <a name="overview"></a>개요
기본적으로 Intune 앱 SDK는 앱에 전체적으로 정책을 적용합니다. 다중 ID는 정책을 ID 수준별로 적용하기 위해 설정할 수 있는 선택적 Intune 앱 보호 기능입니다. 이 기능을 사용하려면 다른 앱 보호 기능보다 훨씬 더 많은 앱 참여가 필요합니다.

> [!NOTE]
> 올바른 앱 참여가 없으면 데이터가 누수되고 다른 보안 문제가 발생할 수 있습니다.

사용자가 디바이스 또는 앱을 등록하고 나면 SDK에서 이 ID를 등록하고 이를 기본 Intune 관리 ID로 간주합니다. 앱의 다른 사용자는 무제한 정책 설정이 적용되는 관리되지 않는 항목으로 처리됩니다.

> [!NOTE]
> 현재 Intune 관리 ID는 디바이스당 하나만 지원됩니다.

ID는 문자열로 정의됩니다. ID는 **대/소문자를 구분하지 않음**이며, ID와 관련한 SDK에 대한 요청은 ID를 설정할 때 원래 사용된 것과 같은 대/소문자를 반환하지 않을 수도 있습니다.

앱은 활성 ID를 변경하려는 경우 SDK에 *알려야 합니다*. 경우에 따라 SDK는 ID 변경이 필요한 경우 앱에도 알립니다. 그러나 대부분의 경우 MAM은 어떤 데이터가 UI에 표시되거나 특정 시점에 스레드에서 사용되고 있고 데이터 누수를 피하기 위해 올바른 ID를 설정하는 데 앱을 사용하는지 알 수 없습니다. 다음에 나오는 섹션에서는 앱 작업이 필요한 일부 특정 시나리오가 설명됩니다.

### <a name="enabling-multi-identity"></a>다중 ID 사용

기본적으로 모든 앱은 단일 ID 앱으로 간주합니다. AndroidManifest.xml에 다음 메타데이터를 두어 앱에서 다중 ID를 인식할 수 있음을 선언할 수 있습니다.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>ID 설정

개발자는 다음 수준에서 앱 사용자의 ID를 우선순위에 따라 내림차순으로 설정할 수 있습니다.

  1. 스레드 수준
  2. `Context`(일반적으로 `Activity`) 수준
  3. 프로세스 수준

스레드 수준에서 설정된 ID는 `Context` 수준에서 설정된 ID를 대체하고 프로세스 수준에서 설정된 ID를 대체합니다. `Context`에서 설정된 ID는 해당하는 관련 시나리오에만 사용됩니다. 예를 들어 파일 IO 작업에는 연결된 `Context`가 없습니다. 일반적으로 앱은 `Activity`에 대한 `Context` ID를 설정합니다. `Activity` ID가 동일한 ID로 설정되지 않는 한 앱은 관리되는 ID에 대한 데이터를 표시하면 *안 됩니다*. 일반적으로 프로세스 수준 ID는 모든 스레드에서 한 번에 한 명의 사용자만 앱을 사용하는 경우에만 유용합니다. 대부분의 앱은 해당 ID를 사용할 필요가 없을 수 있습니다.

앱에서 `Application` 컨텍스트를 사용하여 시스템 서비스를 획득하는 경우 스레드 또는 프로세스 ID가 설정되었는지, 또는 앱의 `Application` 컨텍스트에서 UI ID를 설정했는지 확인해야 합니다.

`setUIPolicyIdentity` 또는 `switchMAMIdentity`를 사용하여 UI ID를 업데이트하는 특수 사례를 처리하려면 두 메서드를 `IdentitySwitchOption` 값 세트로 전달하면 됩니다.

* `IGNORE_INTENT`: 현재 작업과 연결된 의도를 무시해야 하는 ID 전환을 요청하는 경우에 사용합니다.
  예를 들면 다음과 같습니다.

  1. 관리형 문서를 포함하고 있는 관리 ID에서 의도를 수신하는 앱이 문서를 표시합니다.
  2. 사용자가 자신의 개인 ID로 전환하고, 앱은 UI ID 전환을 요청합니다. 개인 ID에서는 앱이 더 이상 문서를 표시하지 않으므로 ID 전환을 요청할 때 `IGNORE_INTENT`를 사용합니다.

  사용자가 설정하지 않으면 SDK는 가장 최근 의도가 여전히 앱에서 사용되고 있다고 가정합니다. 그러면 의도를 수신 데이터로 처리하고 새 ID를 사용하도록 새 ID에 대한 정책이 수신됩니다.

>[!NOTE]
> `CLIPBOARD_SERVICE`는 UI 작업에 사용되므로, SDK는 포그라운드 작업의 UI ID를 `ClipboardManager` 작업에 사용합니다.
> `MAMPolicyManager`에서 다음 메서드를 사용하여 ID를 설정하고 이전에 설정한 ID 값을 검색할 수 있습니다.

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);
  ```

>[!NOTE]
> 앱의 ID를 Null로 설정하여 ID를 지울 수 있습니다.
>
> 빈 문자열을 앱 보호 정책이 없는 ID로 사용할 수 있습니다.

#### <a name="results"></a>결과
ID를 설정하는 데 사용된 모든 메서드는 `MAMIdentitySwitchResult`를 통해 결과 값을 다시 보고합니다. 반환될 수 있는 네 개의 값은 다음과 같습니다.

| 반환 값 | 시나리오 |
|--|--|
| SUCCEEDED | ID가 변경되었습니다. |
| NOT_ALLOWED  | ID 변경이 허용되지 않습니다. 현재 스레드에 다른 ID가 설정되어 있을 때 UI(컨텍스트) ID를 설정하려고 할 경우 이 작업이 수행됩니다. |
| CANCELLED | 사용자가 보통 PIN 또는 인증 프롬프트에서 뒤로 단추를 눌러 ID 변경을 취소했습니다. |
| FAILED | 알 수 없는 이유로 ID 변경에 실패했습니다.|

앱에서 회사 데이터를 표시하거나 사용하기 전에 ID 전환이 성공적인지 확인해야 합니다. 현재는 다중 ID 사용 앱에 대한 프로세스 및 스레드 ID 전환이 항상 성공하지만, 실패 조건을 추가할 권한은 Microsoft가 보유합니다. UI ID가 스레드 ID와 충돌하거나 사용자가 조건부 시작 요구 사항을 취소하는 경우 잘못된 인수로 인해 UI ID 전환이 실패할 수 있습니다(예: PIN 화면에서 [뒤로] 단추를 누름).


컨텍스트 ID를 설정할 경우 결과는 비동기적으로 보고됩니다. 컨텍스트가 작업인 경우에는 SDK가 PIN이나 전체 회사 자격 증명을 입력해야 할 수 있는 조건부 시작이 수행된 후까지 ID 변경에 성공했는지 알 수 없게 됩니다. 앱은 이 매개 변수에 Null을 전달할 수 있더라도 이 결과를 수신하도록 `MAMSetUIIdentityCallback`을 구현해야 합니다.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

`MAMPolicyManager.setUIPolicyIdentity`를 호출하는 대신 `MAMActivity`의 메서드를 통해 직접 활동 ID를 설정할 수도 있습니다. 이렇게 하려면 다음 메서드를 사용하세요.

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

해당 활동의 ID를 변경하려는 시도의 결과를 앱에 알리려는 경우 `MAMActivity`의 메서드를 재정의할 수도 있습니다.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

`onSwitchMAMIdentityComplete`를 재정의하지 않으면(또는 `super` 메서드를 호출하면) 작업에 대한 ID 전환 실패 시 작업이 완료됩니다. 메서드를 재정의하는 경우 ID 전환이 실패한 후 회사 데이터가 표시되지 않도록 주의해야 합니다.

>[!NOTE]
> ID를 전환하려면 작업을 다시 만들어야 할 수 있습니다. 이 경우 `onSwitchMAMIdentityComplete` 콜백이 작업의 새 인스턴스에 전달됩니다.


### <a name="implicit-identity-changes"></a>명시적 ID 변경

앱의 ID 설정 기능 이외에도, 앱 보호 정책이 적용된 다른 Intune 관리 앱의 데이터 수신에 따라 스레드 또는 컨텍스트의 ID가 변경될 수 있습니다.

#### <a name="examples"></a>예

1. 다른 MAM 앱에서 보낸 `Intent`에서 작업이 시작된 경우에는 `Intent`가 전송된 시점의 다른 앱에서 유효한 ID에 따라 작업 ID가 설정됩니다.

2. 서비스의 경우 `onStart` 또는 `onBind` 호출 기간 동안 스레드 ID가 비슷하게 설정됩니다. `onBind`에서 반환된 `Binder` 호출도 일시적으로 스레드 ID를 설정합니다.

3. 마찬가지로 `ContentProvider` 호출은 해당 기간에 대한 스레드 ID를 설정합니다.


    또한 사용자가 작업을 조작하면 암시적 ID 전환이 수행될 수 있습니다.

    **예:** 사용자가 `Resume` 중에 인증 프롬프트에서 취소하면 암시적으로 빈 ID로 전환됩니다.

    앱은 이러한 변경 내용을 인식하고 필요한 경우 앱에서 변경을 금지할 수 있습니다. `MAMService` 및 `MAMContentProvider`는 하위 클래스가 재정의할 수 있는 다음 메서드를 공개합니다.

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchResultCallback callback);
    ```

    `MAMActivity` 클래스에서 메서드에 다음과 같은 추가 매개 변수가 있습니다.

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchReason reason,
      final AppIdentitySwitchResultCallback callback);
    ```

    * `AppIdentitySwitchReason`은 암시적 전환의 원인을 캡처하며 `CREATE`, `RESUME_CANCELLED` 및 `NEW_INTENT` 값을 사용할 수 있습니다.  `RESUME_CANCELLED` 이유는 작업이 다시 시작되어 PIN,인증 또는 기타 준수 UI가 표시되고 사용자가 일반적으로 뒤로 단추를 사용하여 해당 UI를 취소하려고 할 때 사용됩니다.


    * `AppIdentitySwitchResultCallback`은 다음과 같습니다.

      ```java
      public interface AppIdentitySwitchResultCallback {
          /**
            * @param result
            *            whether the identity switch can proceed.
            */
          void reportIdentitySwitchResult(AppIdentitySwitchResult result);
        }
        ```

      ```AppIdentitySwitchResult```는 `SUCCESS` 또는 `FAILURE`입니다.

`MAMService.onMAMBind`에서 반환된 Binder 를 통해 적용된 변경을 제외하고 모든 암시적 ID 변경에 대해 `onMAMIdentitySwitchRequired` 메서드가 호출됩니다. 기본 `onMAMIdentitySwitchRequired` 구현에서 즉시 다음을 호출합니다.

* 이유가 `RESUME_CANCELLED`이면 `reportIdentitySwitchResult(FAILURE)`.

* 다른 모든 경우에는 `reportIdentitySwitchResult(SUCCESS)`.

  대부분 앱은 ID 전환을 다른 방식으로 차단하거나 연기할 필요가 없지만, 앱이 이렇게 해야 할 경우에는 다음 사항을 고려해야 합니다.

  * ID 전환을 차단하는 경우의 결과는 `Receive` 공유 설정이 데이터 수신을 금지한 경우와 동일합니다.

  * 서비스가 주 스레드에서 실행 중이면 `reportIdentitySwitchResult`을(를) **반드시** 동기적으로 호출해야 합니다. 그렇지 않으면 UI 스레드가 응답하지 않습니다.

  * **`Activity`** 만들기의 경우 `onMAMCreate` 전에 `onMAMIdentitySwitchRequired`가 호출됩니다. 앱이 ID 전환 허용 여부를 결정하기 위해 UI를 표시해야 할 경우 해당 UI는 *다른* 작업을 통해 표시되어야 합니다.

  * **`Activity`** 에서 `RESUME_CANCELLED`와 같은 이유로 빈 ID로 전환해야 할 경우 앱은 데이터를 해당 ID 전환과 일관되게 표시하도록 다시 시작된 작업을 수정해야 합니다.  이 작업을 수행할 수 없으면 앱은 전환을 거부하고 사용자에게는 ID를 다시 시작하기 위해 정책을 준수할지 묻는 메시지가 다시 표시됩니다(예: 앱 PIN 입력 화면 표시).

    > [!NOTE]
    > 다중 ID 앱은 항상 관리되는 앱과 관리되지 않는 앱에서 들어오는 데이터를 둘 다 수신합니다. 앱은 관리되는 ID의 데이터를 관리되는 방식으로 처리해야 합니다.

  요청된 ID가 관리되지만(`MAMPolicyManager.getIsIdentityManaged`를 사용하여 확인) 앱이 메일 계정 등의 계정을 먼저 설정해야 하기 때문에 해당 계정을 사용할 수 없다면 ID 전환이 거부됩니다.

#### <a name="build-plugin--tool-considerations"></a>빌드 플러그 인/도구 고려 사항
`MAMActivity`, `MAMService` 또는 `MAMContentProvider`에서 명시적으로 상속하지 않지만(빌드 도구를 통해 해당 변경을 했기 때문에) ID 스위치를 여전히 처리해야 하는 경우 `MAMActivityIdentityRequirementListener`(`Activity`의 경우) 또는 `MAMIdentityRequirementListener`(`Service`또는 `ContentProviders`의 경우)를 대신 구현할 수 있습니다.
정적 메서드 `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)`를 호출하여 `MAMActivity.onMAMIdentitySwitchRequired`의 기본 동작에 액세스할 수 있습니다.

마찬가지로 `MAMActivity.onSwitchMAMIdentityComplete`을 재정의해야 하는 경우 `MAMActivity`에서 명시적으로 상속하지 않고 `MAMActivityIdentitySwitchListener`를 구현할 수 있습니다.

### <a name="preserving-identity-in-async-operations"></a>비동기 작업에서 ID 유지
UI 스레드의 작업에서 백그라운드 작업을 다른 스레드에 발송하는 것은 일반적입니다. 다중 ID 앱은 이러한 백그라운드 작업이 적절한 ID로 작동하는지 확인하려고 합니다. 적절한 ID는 ID를 발송한 작업에 사용되는 ID와 동일한 경우가 많습니다. MAM SDK는 ID 보존에 도움이 되도록 편의를 위해 `MAMAsyncTask`와 `MAMIdentityExecutors`를 제공합니다.
비동기 작업에서 회사 데이터를 파일에 쓸 수 있거나 다른 앱과 통신할 수 있을 때 사용해야 합니다.

#### <a name="mamasynctask"></a>MAMAsyncTask

`MAMAsyncTask`를 사용하려면 `AsyncTask` 대신 해당 함수를 상속 받고 `doInBackground` 및 `onPreExecute`의 재정의를 각각 `doInBackgroundMAM` 및 `onPreExecuteMAM`으로 바꿉니다. `MAMAsyncTask` 생성자는 작업 컨텍스트를 사용합니다. 예를 들면 다음과 같습니다.

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
`MAMIdentityExecutors`를 사용하면 `wrapExecutor` 및 `wrapExecutorService` 메서드를 통해 기존의 `Executor` 또는 `ExecutorService` 인스턴스를 ID를 유지하는 `Executor`/`ExecutorService`로 래핑할 수 있습니다. 예

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```

### <a name="file-protection"></a>파일 보호

모든 파일은 만들어질 때 스레드 및 프로세스 ID를 기준으로 하는 ID에 연결됩니다. 이 ID는 파일 암호화 및 선택적 초기화에 둘 다 사용됩니다. ID가 관리되고 암호화를 요구하는 정책이 있는 파일만 암호화됩니다. SDK의 기본 선택적 기능 초기화는 초기화가 요청된 관리 ID와 연결된 파일만 초기화합니다. 앱은 `MAMFileProtectionManager` 클래스를 사용하여 파일 ID를 쿼리하거나 변경할 수 있습니다.

```java
public final class MAMFileProtectionManager {

   /**
    * Protect a file or directory. This will synchronously trigger whatever protection is required for the file, and will tag the
    * file for future protection changes. If an identity is set on a directory, it is set recursively on all files and
    * subdirectories. New files or directories will inherit their parent directory's identity. If MAM is operating in offline mode,
    * this method will silently do nothing.
    *
    * @param identity
    *        Identity to set.
    * @param file
    *        File to protect.
    *
    * @throws IOException
    *         If the file cannot be protected.
    */
   public static void protect(final File file, final String identity) throws IOException;

   /**
     * Protect a file obtained from a content provider. This is intended to be used for
     * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
     * It may also be used with descriptors referring to private files owned by this app.
     * It is not intended to be used for files owned by other apps and such usage will fail. If
     * creating a new file via a content provider exposed by another MAM-integrated app, the new
     * file identity will automatically be set correctly if the ContentResolver in use was
     * obtained via a Context with an identity or if the thread identity is set.
     *
     * This will synchronously trigger whatever protection is required for the file, and will tag
     * the file for future protection changes. If an identity is set on a directory, it is set
     * recursively on all files and subdirectories. If MAM is operating in offline mode, this
     * method will silently do nothing.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     *
     * @throws IOException
     *             If the file cannot be protected.
     */
    public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

}

public interface MAMFileProtectionInfo {
    String getIdentity();
}
 ```

#### <a name="app-responsibility"></a>앱 책임
MAM은 읽고 있는 파일과 `Activity`에 표시되는 데이터 간 관계를 자동으로 유추할 수 없습니다. 앱은 회사 데이터를 표시하기 전에 UI ID를 적절하게 *설정해야 합니다*. 여기에는 파일에서 읽은 데이터가 포함됩니다. 파일이 앱 외부에서 제공된 경우(`ContentProvider`에서 제공되거나 공개적으로 쓰기 가능한 위치에서 읽은 경우) 앱은 파일에서 읽은 정보를 표시하기 전에 파일 ID를 확인하려고 *시도해야 합니다*(`MAMFileProtectionManager.getProtectionInfo` 사용). `getProtectionInfo`가 null이 아니고 비어 있지 않은 ID를 보고할 경우 UI ID는 이 ID와 일치하도록 *설정되어야 합니다*(`MAMActivity.switchMAMIdentity` 또는 `MAMPolicyManager.setUIPolicyIdentity` 사용). ID 전환에 실패하는 경우 파일의 데이터가 표시되지 *않아야 합니다*.

예제 흐름은 다음과 같이 표시될 수 있습니다.
* 사용자가 앱에서 열 문서를 선택합니다.
* 열기 흐름 중에 디스크에서 데이터를 읽기 전에 앱이 콘텐츠를 표시하는 데 사용되어야 하는 ID를 확인합니다.
  * MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
  * if(info)   MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback)
  * 앱이 결과가 콜백에 보고될 때까지 기다립니다.
  * 보고된 결과가 실패인 경우 앱이 문서를 표시하지 않습니다.
* 앱이 파일을 열고 렌더링합니다.
  
#### <a name="single-identity-to-multi-identity-transition"></a>단일 ID에서 다중 ID로 전환
이전에 단일 ID Intune을 통합하여 출시된 앱이 이후에 다중 ID를 통합하면 이전에 설치된 앱이 전환됩니다(사용자에게는 보이지 않으며 연결된 UX는 없음). 앱이 이 전환을 처리하기 위해 명시적으로 *해야 하는* 것은 없습니다. 전환 이전에 생성된 모든 파일은 계속해서 관리형 파일로 간주됩니다. 따라서 암호화 정책이 켜져 있으면 암호화 상태를 유지합니다. 원한다면 업그레이드를 검색하고 `MAMFileProtectionManager.protect`를 사용하여 특정 파일 또는 디렉터리에 빈 ID를 태그로 지정할 수 있습니다. 이렇게 하면 암호화된 파일 또는 디렉터리의 암호화가 제거됩니다.

#### <a name="offline-scenarios"></a>오프라인 시나리오

오프라인 모드에서 파일 ID 태그를 지정할 경우 주의하세요. 다음 사항을 고려해야 합니다.

* 회사 포털이 설치되지 않으면 파일에 ID 태그를 지정할 수 없습니다.

* 회사 포털이 설치되어 있지만 앱에 Intune MAM 정책이 없으면 파일에 안정적으로 ID 태그를 지정할 수 없습니다.

* 파일 ID 태그 지정을 사용할 수 있으면 이전에 만든 모든 파일이 빈 문자열 ID에 속한 개인용/비관리로 처리됩니다. 단, 앱이 이전에 파일이 등록된 사용자에게 속하는 것으로 처리되는 경우의 단일 ID 관리 앱으로 설치된 경우는 개인용으로 처리되지 않습니다.

### <a name="directory-protection"></a>디렉터리 보호

파일을 보호하는 데 사용하는 `protect` 메서드와 동일한 메서드로 디렉터리를 보호할 수 있습니다. 디렉터리 보호는 디렉터리에 포함된 모든 파일과 하위 디렉터리 및 해당 디렉터리에서 만들 새 파일에 반복적으로 적용됩니다. 디렉터리 보호는 반복적으로 적용되므로 `protect` 호출에서 매우 큰 디렉토리를 완료하는 데 시간이 오래 걸릴 수 있습니다. 이런 이유로 인해 다수의 파일을 포함하는 디렉터리에 보호를 적용하는 앱이 백그라운드 스레드에서 비동기적으로 `protect`를 실행할 수 있습니다.

### <a name="data-protection"></a>데이터 보호

여러 ID에 속하는 것으로 파일에 태그를 지정할 수는 없습니다. 여러 사용자에게 속한 데이터를 같은 파일에 저장해야 하는 앱은 `MAMDataProtectionManager`에서 제공한 기능을 사용하여 이 작업을 수행할 수 있습니다. 이렇게 하면 앱이 데이터를 암호화하고 특정 사용자에게 연결할 수 있습니다. 암호화된 데이터는 파일로 디스크에 저장하는 데 적합합니다. ID와 연결된 데이터를 쿼리하고 나중에 데이터를 암호 해제할 수 있습니다.

`MAMDataProtectionManager`를 활용하는 앱에서는 `MANAGEMENT_REMOVED` 알림의 수신기를 구현해야 합니다. 이 알림이 완료되고 나면, 버퍼를 보호할 때 파일 암호화가 사용된 경우 이 클래스를 통해 보호된 버퍼를 더 이상 읽을 수 없게 됩니다. 앱에서 이 알림 중에 모든 버퍼에서 `MAMDataProtectionManager.unprotect`를 호출하여 이 상황을 해결할 수 있습니다. 또한 ID 정보를 유지하려는 경우 이 알림 중에 보호를 호출하는 것이 안전합니다. 알림 중에는 암호화가 사용되지 않습니다.


```java

public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected
     * input.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function
     *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The
     *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original
     *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method.
     *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the
     * unprotected input.
     *
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     *
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input stream to get information on. Either this input
     *            stream must have been returned by a previous call to
     *            protect OR input.markSupported() must return true.
     *            Otherwise it will be impossible to get protection info
     *            without advancing the stream position. The stream must be
     *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input bytes to get information on. These must be bytes
     *            returned by a previous call to protect() or a copy of
     *            such bytes.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```

### <a name="content-providers"></a>콘텐츠 공급자

앱에서 `ContentProvider`를 통해 `ParcelFileDescriptor` 이외의 회사 데이터를 제공하는 경우 앱에서 `MAMContentProvider`의 `isProvideContentAllowed(String)` 메서드를 호출하여 콘텐츠에 대한 소유자 ID의 UPN(사용자 계정 이름)을 전달해야 합니다. 이 함수가 false를 반환하면 콘텐츠가 호출자에게 반환*하지 말아야* 합니다. 콘텐츠 공급자를 통해 반환된 파일 설명자는 파일 ID에 따라 자동으로 처리됩니다.

`MAMContentProvider`를 명시적으로 상속하는 대신 빌드 도구가 변경 작업을 처리하도록 허용하는 경우 동일한 `MAMContentProvider.isProvideContentAllowed(provider, contentIdentity)` 메서드의 정적 버전을 호출할 수 있습니다.

### <a name="selective-wipe"></a>선택적 초기화

`WIPE_USER_DATA` 알림에 대해 다중 ID 앱을 등록할 경우, 해당 사용자에게 속한 것으로 ID 태그된 모든 파일을 포함하여 초기화된 사용자의 모든 데이터를 제거할 책임이 앱에 있습니다. 앱이 파일에서 사용자 데이터를 제거하지만 다른 데이터는 파일에 남겨둘 경우 파일의 ID를 변경*해야 합니다*(`MAMFileProtectionManager.protect`를 통해, 개인 데이터 또는 빈 ID로 변경). 암호화 정책을 사용할 경우 정리되는 사용자에 속한 모든 나머지 파일은 암호 해독되지 않으며 초기화 후에 앱에 액세스할 수 없게 됩니다.

`WIPE_USER_DATA`에 등록한 앱에는 SDK 기본 선택적 초기화 동작이 적용되지 않습니다. 다중 ID 인식 앱의 경우 MAM 기본 선택적 초기화는 초기화의 대상이 되는 ID가 있는 파일만 초기화하므로 더 많이 유실될 수 있습니다. 다중 ID 인식 애플리케이션에서 MAM 기본 선택 초기화를 수행하고 _**및**_ 에서 초기화 시 고유 작업을 수행하려는 경우 `WIPE_USER_AUXILIARY_DATA` 알림을 등록해야 합니다. 이 알림은 MAM 기본 선택적 초기화를 수행하기 직전에 SDK에서 즉시 전송합니다. 앱에서 `WIPE_USER_DATA` 및 `WIPE_USER_AUXILIARY_DATA`를 둘 다 등록할 수는 없습니다.

기본 선택적 초기화는 앱을 정상적으로 종료하여 작업을 완료하고 앱 프로세스를 종료합니다. 앱이 기본 선택적 초기화를 재정의하는 경우 초기화 후 사용자가 메모리 내 데이터에 액세스할 수 없도록 앱을 수동으로 종료하는 것이 좋습니다.


## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Android 애플리케이션에 대해 MAM 대상 구성 사용(선택 사항)
[MAM-WE](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) 및 [Android 작업 프로필 앱](https://docs.microsoft.com/intune/app-configuration-policies-use-android)에 대한 Intune 콘솔에서 애플리케이션별 키-값 쌍을 구성할 수 있습니다.
이러한 키-값 쌍은 Intune에서 전혀 해석되지 않고 앱에 전달됩니다. 해당 구성을 수신하려고 하는 애플리케이션은 `MAMAppConfigManager` 및 `MAMAppConfig` 클래스를 사용하여 구성을 수신할 수 있습니다. 동일한 앱에서 여러 정책을 대상으로 지정하면 동일한 키에 사용할 수 있는 여러 개의 충돌 값이 발생할 수 있습니다.

> [!NOTE] 
> MAM-WE를 통한 전송 설정 구성은 `offline`을 통해 전송할 수 없습니다.  오직 Android Enterprise AppRestrictions만이 이 예의 빈 ID에 대한 `MAMUserNotification`을 통해 전송됩니다.

### <a name="example"></a>예제

```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
LOGGER.info("App Config Data = " + appConfig.getFullData());
String valueToUse = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    for (String value : values) {
        if (isCorrectValue(value)) {
            valueToUse = value;
        }
    }
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
LOGGER.info("Found value " + valueToUse);
```

### <a name="notification"></a>알림
앱 구성이 다음과 같은 새 알림 형식을 추가합니다.
* **REFRESH_APP_CONFIG**: 이 알림은 `MAMUserNotification`을 통해 전송되며 새 앱 구성 데이터가 사용 가능함을 앱에 알립니다.

### <a name="further-reading"></a>추가 참고 자료
Graph API의 기능에 대한 자세한 내용은 [Graph API 참조](https://developer.microsoft.com/graph/docs/concepts/overview)를 참조하세요. <br>

Android에서 MAM 대상 앱 구성 정책을 만드는 방법에 대한 자세한 내용은 [Android for Work용 Microsoft Intune 앱 구성 정책을 사용하는 방법](https://docs.microsoft.com/intune/app-configuration-policies-use-android)에서 MAM 대상 앱 구성 섹션을 참조하세요.

## <a name="style-customization-optional"></a>스타일 사용자 지정(선택사항)

통합된 앱과 더 정확하게 일치하도록 MAM SDK에서 생성한 보기를 시각적으로 사용자 지정할 수 있습니다. 앱 로고의 크기 외에도 기본, 보조 및 배경 색상을 사용자 지정할 수 있습니다. 이 스타일 사용자 지정은 선택사항이며 사용자 지정 스타일을 구성하지 않은 경우 기본값을 사용합니다.


### <a name="how-to-customize"></a>사용자 지정 방법
Intune MAM 보기에 스타일 변경을 적용하려면 먼저 스타일 재정의 XML 파일을 만들어야 합니다. 이 파일은 앱의 “/res/xml” 디렉터리에 두어야 하며 원하는 대로 이름을 지정할 수 있습니다. 다음은 이 파일이 따라야 하는 형식의 예입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>
```

앱에 이미 있는 리소스를 다시 사용해야 합니다. 예를 들어, colors.xml 파일에 녹색을 정의한 다음 여기에서 참조해야 합니다. 16진 색상 코드인 “#0000ff”를 사용할 수 없습니다. 앱 로고의 최대 크기는 110dip(dp)입니다. 작은 로고 이미지를 사용해야 하지만, 이 최대 크기를 사용하면 가장 우수한 결과를 얻을 수 있습니다. 110dip 제한을 초과하면 이미지가 축소되며 흐릿하게 표시될 수 있습니다.

다음은 허용된 스타일 특성, 해당 특성이 제어하는 UI 요소, 해당 XML 특성 항목 이름 및 각각에 필요한 리소스 유형이 나열된 전체 목록입니다.

|스타일 특성 | 영향을 받는 UI 요소 | 특성 항목 이름 | 예상 리소스 유형 |
| -- | -- | -- | -- |
| 배경색 | PIN 화면 배경색 <Br>PIN 상자 채우기 색 | background_color | 색상 |
| 전경색 | 전경 텍스트 색 <br> 기본 상태의 PIN 상자 테두리 <br> 사용자가 PIN을 입력할 때 PIN 상자의 문자(난독 처리된 문자 포함)| foreground_color | 색상|
| 강조 색 | 강조 표시할 때 PIN 상자 테두리 <br> 하이퍼링크 |accent_color | 색상 |
| 앱 로고 | Intune 앱 PIN 화면에 표시되는 큰 아이콘 | logo_image | 그리기 가능 |

## <a name="default-enrollment-optional"></a>기본 등록(선택 사항)

다음은 자동 APP-WE 서비스 등록(이 섹션에서는 **기본값 등록**이라고 함)을 위해 앱 시작 시 사용자 프롬프트를 요구하는 것에 관한 지침으로, Intune 보호 사용자만 SDK 통합 Android LOB 앱을 사용할 수 있도록 허용하는 Intune 앱 보호 정책을 요구합니다. 또한 SDK 통합 Android LOB 앱에 SSO를 사용하는 방법에 관해서도 설명합니다. 이것은 Intune 이외의 사용자가 사용할 수 있는 스토어 앱에서는 **지원되지 않습니다**.

> [!NOTE] 
> **기본값 등록**의 이점에는 디바이스의 앱에 관한 APP-WE 서비스에서 정책을 얻는 단순화된 방법이 포함됩니다.

> [!NOTE] 
> **기본 등록**은 소버린 클라우드를 인식합니다.

다음 단계에 따라 기본 등록을 사용합니다.

1. 앱이 ADAL을 통합하거나 SSO를 설정해야 하는 경우 [일반적인 ADAL 구성](#common-adal-configurations) #2에 따라 [ADAL을 구성](#configure-azure-active-directory-authentication-library-adal)합니다. 그렇지 않은 경우 이 단계를 건너뛰어도 됩니다.
   
2. 매니페스트에서 태그 아래에 다음 값을 추가 하 여 기본 등록을 `<application>` 사용 하도록 설정 합니다.

   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```

   > [!NOTE] 
   > 이것은 앱에서 유일한 MAM-WE 통합이어야 합니다. MAMEnrollmentManager API를 호출하려는 다른 시도가 있으면 충돌이 발생합니다.

3. 매니페스트에서 `<application>` 태그 아래에 다음 값을 추가 하 여 필요한 MAM 정책을 사용 하도록 설정 합니다.

   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```

   > [!NOTE] 
   > 이렇게 하면 사용자는 디바이스에 회사 포털을 다운로드하고 사용하기 전에 기본 등록 절차를 완료해야 합니다.


## <a name="limitations"></a>제한 사항

### <a name="file-size-limitations"></a>파일 크기 제한

[ProGuard](http://proguard.sourceforge.net/) 없이 실행되는 대규모 코드 기반의 경우 ,Dalvik 실행 파일 형식의 제한 사항이 문제가 될 수 있습니다. 특히 다음과 같은 제한 사항이 발생할 수 있습니다.

1. 필드에 대한 65-K 제한입니다.
2. 메소드에 대한 65-K 제한입니다.

### <a name="policy-enforcement-limitations"></a>정책 적용 제한 사항

* **콘텐츠 확인자 사용**: “전송 또는 수신” Intune 정책이 다른 앱에서 콘텐츠 확인자를 사용하여 콘텐츠 공급자에 액세스하는 것을 차단하거나 부분적으로 차단할 수 있습니다. 이로 인해 `ContentResolver` 메서드에서 null이 반환되거나 오류 값이 발생합니다(예: 차단된 경우 `openOutputStream`에서 `FileNotFoundException`이 throw됨). 앱에서는 콘텐츠 확인자를 통한 데이터 쓰기가 정책으로 인해 실패했거나 정책으로 인해 실패할 것인지 여부를 다음을 호출하여 확인할 수 있습니다.

    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```

    또는 연결된 활동이 없는 경우

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    이 두 번째 사례에서 다중 ID 앱은 스레드 ID를 적절하게 설정하도록 주의해야 합니다(또는 `getPolicy` 호출에 명시적 ID 전달).

### <a name="exported-services"></a>내보낸 서비스

 Intune 앱 SDK에 포함된 AndroidManifest.xml 파일에는 **MAMNotificationReceiverService**가 포함되어 있으며, 이것은 회사 포털이 관리하는 앱에 알림을 보낼 수 있도록 하는 내보낸 서비스여야 합니다. 이 서비스는 호출자를 검사하여 회사 포털만 알림을 보낼 수 있는지 확인합니다.

### <a name="reflection-limitations"></a>리플렉션 제한 사항
일부 MAM 기본 클래스(예: MAMActivity, MAMDocumentsProvider)는 특정 API 수준 위에만 존재하는 반환 형식 또는 매개 변수를 사용하는 메서드(원래 Android 기본 클래스를 기반으로)를 포함합니다. 이런 이유 때문에 리플렉션을 사용하여 앱 구성 요소의 모든 메서드를 열거하는 것이 항상 가능하지는 않습니다. 이 제한 사항은 MAM에 국한되지 않으며 앱 자체가 Android 기본 클래스에서 이러한 메서드를 구현하는 경우 적용되는 것과 동일한 제한 사항입니다.

### <a name="robolectric"></a>Robolectric
Robolectric에서는 MAM SDK 동작 테스트가 지원되지 않습니다. Robelectric에서는 실제 디바이스나 에뮬레이터에서 동작을 정확하게 재현하지는 못하기 때문에 Robolectric에서의 MAM SDK 실행에는 알려진 문제가 있습니다.

Roboelectric에서 애플리케이션을 테스트해야 할 경우 권장되는 해결 방법은 애플리케이션 클래스 논리를 도우미로 이동하고 MAMApplication에서 상속하지 않는 애플리케이션 클래스로 단위 테스트 apk를 생성하는 것입니다.
## <a name="expectations-of-the-sdk-consumer"></a>SDK 소비자의 기대

Intune SDK는 Android API에서 제공되는 계약을 유지하지만, 정책 적용의 결과로 오류 상태가 더 빈번하게 트리거될 수 있습니다. 다음 Android 모범 사례는 오류 가능성을 줄입니다.

* null을 반환할 수 있는 Android SDK 함수가 null일 가능성이 높아졌습니다.  문제를 최소화하려면 올바른 위치에서 null 검사가 이루어지도록 합니다.

* 확인할 수 있는 기능은 MAM 대체 API를 통해 확인해야 합니다.

* 파생된 함수는 상위 클래스 버전을 통해 호출해야 합니다.

* API를 모호한 방식으로 사용해서는 안 됩니다. 예를 들어 requestCode 확인 없이 `Activity.startActivityForResult`를 사용하면 이상한 동작이 발생합니다.

## <a name="telemetry"></a>원격 분석

Android 용 Intune 앱 SDK는 앱에서 데이터 수집을 제어하지 않습니다. 기본적으로 회사 포털 애플리케이션은 시스템 생성 데이터를 기록합니다. 이 데이터는 Microsoft Intune로 전송됩니다. Microsoft 정책에 따라 Microsoft는 개인 데이터를 수집하지 않습니다.

> [!NOTE]
> 최종 사용자가 이 데이터를 보내지 않도록 선택하는 경우 회사 포털 앱의 [설정]에서 원격 분석을 해제해야 합니다. 자세한 내용은 [Microsoft 사용량 현황 데이터 수집 해제](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android)를 참조하세요. 

## <a name="recommended-android-best-practices"></a>권장되는 Android 모범 사례

* 가능한 경우 모든 라이브러리 프로젝트에서 동일한 android:package를 공유해야 합니다. 이 문제는 전적으로 빌드 시에 발생하므로, 런타임 시에는 산발적으로 장애가 발생하지 않습니다. Intune 앱 SDK의 최신 버전에서는 중복성이 제거됩니다.

* 최신 Android SDK 빌드 도구를 사용합니다.

* 불필요한 라이브러리 및 사용하지 않는 라이브러리(예: android.support.v4)를 모두 제거합니다.
