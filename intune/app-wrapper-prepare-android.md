---
title: Intune 앱 래핑 도구를 사용하여 Android 앱 래핑
description: 앱 자체의 코드를 수정하지 않고 Android 앱을 래핑하는 방법에 대해 알아봅니다. 모바일 앱 관리 정책을 적용할 수 있도록 앱을 준비합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 74ef09c8979e6867d49c119668ad329570cee424
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189829"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Intune 앱 래핑 도구를 사용하여 앱 보호 정책에 대해 Android 앱 준비

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Android용 Microsoft Intune 앱 래핑 도구를 사용하여 해당 앱 코드를 변경하지 않고도 앱 기능을 제한하여 사내 Android 앱의 동작을 변경합니다.

이 도구는 PowerShell에서 실행되고 Android 앱 주위에 래퍼를 생성하는 Windows 명령줄 응용 프로그램입니다. 앱을 래핑한 후에는 Intune에서 [모바일 응용 프로그램 관리 정책](/intune-classic/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)을 구성하여 앱의 기능을 변경할 수 있습니다.


도구를 실행하기 전에 [앱 래핑 도구를 실행하기 위한 보안 고려 사항](#security-considerations-for-running-the-app-wrapping-tool)을 검토하세요. 이 도구를 다운로드하려면 GitHub의 [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)(Android용 Microsoft Intune 앱 래핑 도구)로 이동하세요.

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>앱 래핑 도구의 필수 구성 요소 준비

-   앱 래핑 도구는 Windows 7 이상을 실행하는 Windows 컴퓨터에서 실행해야 합니다.

-   입력하는 앱은 파일 확장명이 .apk인 유효한 Android 응용 프로그램 패키지여야 합니다. 그리고

    -   암호화할 수 없습니다.
    -   Intune 앱 래핑 도구로 이미 래핑되지 않아야 합니다.
    -   Android 4.0 이상에서 작성해야 합니다.

-   앱이 회사에 의해 또는 회사를 위해 개발되어야 합니다. Google Play 스토어에서 다운로드한 앱에서 이 도구를 사용할 수 없습니다.

-   앱 래핑 도구를 실행하려면 최신 버전의 [Java 런타임 환경](http://java.com/download/)을 설치한 다음 Windows 환경 변수에 Java path 변수를 C:\ProgramData\Oracle\Java\javapath로 설정해야 합니다. 도움이 더 필요하면 [Java 설명서](http://java.com/download/help/)를 참조하세요.

    > [!NOTE]
    > 일부 경우에 32비트 버전의 Java에서 메모리 문제가 발생할 수 있습니다. 64비트 버전을 설치하는 것이 좋습니다.

- Android는 모든 앱 패키지(.apk)를 서명해야 합니다. 기존 인증서와 전체 서명 인증서 **재사용** 지침은 [서명 인증서 재사용 및 앱 래핑](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps)을 참조하세요. Java 실행 파일 keytool.exe를 사용하여 래핑된 출력 앱에 서명하는 데 필요한 **새** 자격 증명을 생성합니다. 설정된 모든 암호에는 보안이 적용되어야 하지만, 나중에 앱 래핑 도구를 실행하는 데 필요하므로 암호를 적어 두세요.

> [!NOTE]
> Intune 앱 래핑 도구는 앱 서명 시 Google의 v2 서명 방식과 향후 예정된 v3 서명 방식을 지원하지 않습니다. Intune 앱 래핑 도구를 사용하여 .apk 파일을 래핑한 경우, [Google에서 제공하는 Apksigner 도구]( https://developer.android.com/studio/command-line/apksigner)를 사용하는 것을 추천합니다. 이렇게 하면 앱이 최종 사용자 장치에서 Android 표준에 의해 올바르게 실행됩니다. 

- (선택 사항) 입력 앱 내에서 Multidex를 사용합니다. 경우에 따라 앱은 래핑 중에 추가된 Intune MAM SDK 클래스로 인해 DEX(Dalvik 실행 파일) 크기 제한에 도달할 수 있습니다. DEX 파일은 Android 앱 컴파일의 일부입니다. 이 시나리오에서 모범 사례는 앱 자체 내에서 Multidex를 사용하도록 설정하는 것입니다. 특정 조직에서는 앱을 컴파일하는 사용자(예: 앱 빌드 팀)와 함께 작업해야 할 수 있습니다. 

## <a name="install-the-app-wrapping-tool"></a>앱 래핑 도구 설치

1.  [GitHub 리포지토리](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)에서 Android용 Intune 앱 래핑 도구에 대한 InstallAWT.exe 설치 파일을 Windows 컴퓨터에 다운로드합니다. 설치 파일을 엽니다.

2.  사용권 계약에 동의한 다음 설치를 완료합니다.

이 도구를 설치한 폴더를 메모해 둡니다. 기본 위치는 C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool입니다.

## <a name="run-the-app-wrapping-tool"></a>앱 래핑 도구 실행

1. 앱 래핑 도구를 설치한 Windows 컴퓨터에서 PowerShell 창을 엽니다.

2. 도구를 설치한 폴더에서 앱 래핑 도구 PowerShell 모듈을 가져옵니다.

   ```
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. **invoke-AppWrappingTool** 명령을 사용하여 도구를 실행합니다. 사용 구문은 다음과 같습니다.
   ```
   Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
   -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
   ```

   다음 표에 **invoke-AppWrappingTool** 명령의 속성이 자세히 나와 있습니다.

|속성|정보 산업|예제|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|원본 Android 앱(.apk)의 경로입니다.| |
 |**-OutputPath**&lt;String&gt;|출력 Android 앱의 경로입니다. InputPath와 동일한 디렉터리 경로일 경우 패키징이 실패합니다.| |
|**-KeyStorePath**&lt;String&gt;|서명을 위한 공개/개인 키 쌍이 포함된 키 저장소 파일의 경로입니다.|기본적으로 키 저장소 파일은 "C:\Program Files (x86)\Java\jreX.X.X_XX\bin"에 저장됩니다. |
|**-KeyStorePassword**&lt;SecureString&gt;|키 저장소를 해독하는 데 사용되는 암호입니다. Android에서는 모든 응용 프로그램 패키지(.apk)가 서명되어야 합니다. Java keytool을 사용하여 KeyStorePassword를 생성합니다. 여기에서 Java [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html)(키 저장소)에 대해 자세히 읽으세요.| |
|**-KeyAlias**&lt;String&gt;|서명에 사용할 키의 이름입니다.| |
|**-KeyPassword**&lt;SecureString&gt;|서명에 사용될 개인 키의 암호를 해독하는 데 사용되는 암호입니다.| |
|**-SigAlg**&lt;SecureString&gt;| (선택 사항) 서명에 사용할 서명 알고리즘의 이름입니다. 이 알고리즘은 개인 키와 호환해야 합니다.|예: SHA256withRSA, SHA1withRSA|
| **&lt;CommonParameters&gt;** | (선택 사항) 명령은 verbose, debug와 같은 일반적인 PowerShell 매개 변수를 지원합니다. |


- 일반적인 매개 변수의 목록은 [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx)를 참조하세요.

- 도구에 대한 자세한 사용 정보를 보려면 명령을 입력합니다.

    ```
    Help Invoke-AppWrappingTool
    ```

**예:**

PowerShell 모듈을 가져옵니다.
```
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```
네이티브 앱 HelloWorld.apk에서 앱 래핑 도구를 실행합니다.
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

**KeyStorePassword** 및 **KeyPassword**에 대한 메시지가 표시됩니다. 키 저장소 파일을 만드는 데 사용한 자격 증명을 입력합니다.

래핑된 앱과 로그 파일이 생성되고 지정한 출력 경로에 저장됩니다.

## <a name="how-often-should-i-rewrap-my-android-application-with-the-intune-app-wrapping-tool"></a>Intune 앱 줄 바꿈 도구를 사용하여 Android 응용 프로그램을 얼마나 자주 다시 줄 바꿈해야 합니까?
응용 프로그램을 다시 줄 바꿈해야 하는 주요 시나리오는 다음과 같습니다.
* 응용 프로그램 자체가 새 버전을 릴리스했습니다. 이전 버전의 앱이 래핑되어 Intune 콘솔에 업로드되었습니다.
* Android용 Intune 앱 줄 바꿈 도구는 주요 버그 수정 또는 새로운 특정 Intune 응용 프로그램 보호 정책 기능을 사용할 수 있는 새 버전을 릴리스했습니다. 이는 [Android용 Microsoft Intune 앱 줄 바꿈 도구](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)에 대한 GitHub 리포지토리를 통해 6-8주마다 발생합니다.

다시 줄 바꿈하기 위한 몇 가지 모범 사례는 다음과 같습니다. 
* 빌드 프로세스 중에 사용된 서명 인증서를 유지 관리하려면 [서명 인증서 재사용 및 앱 래핑](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps)을 참조하세요.

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>서명 인증서 재사용 및 앱 래핑
Android의 경우 Android 장치에 설치하려면 유효한 인증서로 모든 앱에 서명해야 합니다.

래핑된 앱은 래핑 프로세스 중에 또는 기존 서명 도구를 사용하여 래핑한 *후에* 서명될 수 있습니다(래핑 전에 앱에 있는 모든 서명 정보는 무시됨). 가능하면 빌드 프로세스에서 이미 사용된 서명 정보를 래핑 중에 사용해야 합니다. 특정 조직에서는 이를 위해 키 저장소 정보를 소유한 사용자(앱 빌드 팀)와 함께 작업해야 할 수 있습니다. 

이전 서명 인증서를 사용할 수 없거나 앱이 이전에 배포되지 않은 경우 [Android Developer Guide](https://developer.android.com/studio/publish/app-signing.html#signing-manually)(Android 개발자 가이드)의 지침에 따라 새 서명 인증서를 만들 수 있습니다.

앱이 이전에 다른 서명 인증서를 사용하여 배포되었던 경우 업그레이드 후에 해당 앱을 Intune에 업로드할 수 없습니다. 앱 빌드 시 사용한 것과 다른 인증서를 사용하여 앱에 서명한 경우 앱 업그레이드 시나리오가 중단됩니다. 마찬가지로 앱 업그레이드를 위해 새로운 서명 인증서를 모두 유지해야 합니다. 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>앱 래핑 도구를 실행하기 위한 보안 고려 사항
잠재적인 스푸핑, 정보 공개 및 권한 상승 공격을 방지하려면:

-   입력 LOB(기간 업무) 응용 프로그램, 출력 응용 프로그램 및 Java KeyStore가 앱 래핑 도구를 실행한 것과 같은 Windows 컴퓨터에 있는지 확인합니다.

-   출력 응용 프로그램을 도구가 실행 중인 것과 같은 컴퓨터의 Intune에 가져옵니다. Java keytool에 대한 자세한 내용은 [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html)을 참조하세요.

-   출력 응용 프로그램 및 도구가 UNC(Universal Naming Convention) 경로에 있는데 도구와 입력 파일을 동일한 컴퓨터에서 실행하지 않는 경우, [IPsec(Internet Protocol Security)](http://wikipedia.org/wiki/IPsec) 또는 [SMB(Server Message Block) 서명](https://support.microsoft.com/kb/887429)을 사용하여 환경을 안전하게 설정합니다.

-   응용 프로그램이 신뢰할 수 있는 소스에서 오는지 확인합니다.

-   래핑된 앱을 포함하고 있는 출력 디렉터리를 보호합니다. 출력에 대한 사용자 수준 디렉터리를 사용하는 것이 좋습니다.

## <a name="requiring-user-login-prompt-for-an-automatic-app-we-service-enrollment-requiring-intune-app-protection-policies-in-order-to-use-your-wrapped-android-lob-app-and-enabling-adal-sso-optional"></a>자동 APP-WE 서비스 등록을 위한 사용자 로그인 프롬프트 필요, 래핑된 Android LOB 앱을 사용하기 위한 Intune 앱 보호 정책 필요, ADAL SSO을 사용하도록 설정(선택 사항)

다음은 자동 APP-WE 서비스 등록(이 섹션에서는 **기본값 등록**이라고 함)을 위해 앱 시작 시 사용자 프롬프트를 요구하는 것에 관한 지침으로, Intune 보호 사용자만 래핑된 Android LOB 앱을 사용할 수 있도록 허용하는 Intune 앱 보호 정책을 요구합니다. 또한 래핑된 Android LOB 앱에 SSO를 사용하는 방법에 관해서도 설명합니다. 

> [!NOTE] 
> **기본값 등록**의 이점에는 장치의 앱에 관한 APP-WE 서비스에서 정책을 얻는 단순화된 방법이 포함됩니다.

### <a name="general-requirements"></a>일반 요구 사항
* Intune SDK 팀은 앱의 응용 프로그램 ID를 필요로 합니다. ID는 [Azure Portal](https://portal.azure.com/)을 통해 확인할 수 있으며 **모든 응용 프로그램** 아래 **응용 프로그램 ID** 열에 나와 있습니다. Intune SDK 팀에는 이메일(msintuneappsdk@microsoft.com)을 통해 연락하는 것이 좋습니다.
     
### <a name="working-with-the-intune-sdk"></a>Intune SDK 사용
이러한 지침은 최종 사용자 장치에서 사용하기 위해 Intune 앱 보호 정책을 요구하려는 모든 Android 및 Xamarin 앱에만 적용됩니다.

1. [Android 가이드용 Intune SDK](https://docs.microsoft.com/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal)에 정의된 단계에 따라 ADAL을 구성합니다.

> [!NOTE]
> 앱에 연결된 “클라이언트 ID”라는 용어는 앱에 연결된 Azure Portal의 “응용 프로그램 ID”라는 용어와 같습니다. 
> * SSO를 사용하려면 “일반적인 ADAL 구성” #2가 필요합니다.

2. 매니페스트에 다음 값을 입력하여 기본 등록을 사용합니다. ```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
   > [!NOTE] 
   > 이것은 앱에서 유일한 MAM-WE 통합이어야 합니다. MAMEnrollmentManager API를 호출하려는 다른 시도가 있으면 충돌이 발생할 수 있습니다.

3. 매니페스트에 다음 값을 입력하여 필요한 MAM 정책을 설정합니다. ```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
   > [!NOTE] 
   > 이렇게 하면 사용자는 장치에 회사 포털을 다운로드하고 사용하기 전에 기본 등록 절차를 완료해야 합니다.

### <a name="see-also"></a>참고 항목
- [Microsoft Intune으로 모바일 응용 프로그램 관리용 앱을 준비하는 방법 결정](apps-prepare-mobile-application-management.md)

- [Android용 Microsoft Intune 앱 SDK 개발자 가이드](app-sdk-android.md)
