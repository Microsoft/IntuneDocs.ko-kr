---
title: Android 앱 보호 정책 설정
titlesuffix: Microsoft Intune
description: 이 항목에서는 Android 장치에 대한 앱 보호 정책 설정을 설명합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9e9ef9f5-1215-4df1-b690-6b21a5a631f8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae031f601792251f1dcf7b93fb914a740bc36300
ms.sourcegitcommit: 46f6f3d4e1c7c0a5a716503f759ea5cf03c1a02b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136984"
---
# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Microsoft Intune의 Android 앱 보호 정책 설정
이 문서에서는 Android 장치에 대한 앱 보호 정책 설정을 설명합니다. 설명하는 정책 설정은 Azure Portal의 **설정** 블레이드에서 앱 보호 정책에 대해 [구성](app-protection-policies.md)될 수 있습니다.
데이터 재배치 설정 및 액세스 설정의 두 가지 정책 설정 범주가 있습니다. 이 문서에서 *정책 관리 앱*이라는 용어는 앱 보호 정책으로 구성된 앱을 나타냅니다.

##  <a name="data-relocation-settings"></a>데이터 재배치 설정

| Setting | 사용 방법 | 기본값 |
|------|------|------|
| **Android 백업 차단** | 이 앱에서 회사 또는 학교 데이터를 [Android 백업 서비스](https://developer.android.com/google/backup/index.html)로 백업하지 않도록 하려면 **예**를 선택하고 이 앱에서 회사 또는 학교 데이터를 백업할 수 있도록 하려면 **아니요**를 선택합니다.| 예 |
| **앱이 다른 앱으로 데이터를 전송하도록 허용** | 이 앱에서 데이터를 받을 수 있는 앱을 지정합니다. <ul><li> **정책 관리 앱**: 다른 정책 관리 앱으로만 데이터를 전송하도록 허용합니다.</li> <li>**모든 앱**: 모든 앱으로의 전송을 허용합니다. </li> <li>**없음**: 다른 정책 관리 앱을 포함한 모든 앱에 대한 데이터 전송을 허용하지 않습니다.</li></ul> <p>Intune에서 기본적으로 데이터를 전송할 수 있는 몇 가지 예외적인 앱 및 서비스가 있습니다. 또한, Intune APP을 지원하지 않는 앱에 전송될 데이터를 허용해야 하는 경우 사용자만의 예외를 만들 수 있습니다. 자세한 내용은 [데이터 전송 예외](#Data-transfer-exemptions)를 참조합니다.<p>이 정책은 웹 콘텐츠의 동작에도 영향을 줍니다. 이 정책이 **차단됨**으로 설정되면 Managed Browser를 포함하여 모든 브라우저에 대한 http 링크를 열 수 없습니다. 또한 이 정책이 **정책 관리 전용**으로 설정되면 Managed Browser에서만 http 링크를 열 수 있습니다.<p>**참고:** Intune은 Android 인스턴트 앱 기능을 현재 지원하지 않습니다. Intune은 앱 간에 모든 데이터 연결을 차단합니다.  [Android 인스턴트 앱](https://developer.android.com/topic/instant-apps/index.html)에 대한 자세한 내용은 Android 개발자 설명서를 참조하세요.</p>| 모든 앱 |
| **앱이 다른 앱의 데이터를 받도록 허용** | 이 앱에 데이터를 전송할 수 있는 앱을 지정합니다. <ul><li>**정책 관리 앱**: 다른 정책으로 관리된 앱에서만 데이터를 전송하도록 허용합니다.</li><li>**모든 앱**: 모든 앱의 데이터 전송을 허용합니다.</li><li>**없음**: 다른 정책 관리 앱을 포함한 모든 앱에서의 데이터 전송을 허용하지 않습니다. </li></ul> <p>예외적으로 intune이 데이터를 전송받을 수 있는 몇 가지 앱 및 서비스가 있습니다. 전체 앱 및 서비스 목록은 [데이터 전송 예외](#Data-transfer-exemptions)를 참조하세요. | 모든 앱 |
| **"다른 이름으로 저장" 차단** | 이 앱에서 다른 이름으로 저장 옵션을 사용할 수 없도록 설정하려면 **예**를 선택합니다. 다른 이름으로 저장을 사용할 수 있도록 설정하려면 **아니요**를 선택합니다. **참고:** 이 설정은 Microsoft Excel, OneNote, PowerPoint 및 Word에 지원됩니다. 또한 타사 및 LOB 앱에서도 지원될 수 있습니다. <p>**회사 데이터를 저장할 저장소 서비스 선택** <br>사용자가 선택한 서비스(비즈니스용 OneDrive, SharePoint 및 로컬 저장소)에 저장할 수 있습니다. 기타 서비스는 모두 차단됩니다.</p> | 아니요<p>&nbsp;</p><p>&nbsp;</p>0개 선택됨 |
| **다른 앱에서 잘라내기, 복사 및 붙여넣기 제한** | 이 앱에서 잘라내기, 복사 및 붙여넣기 동작을 사용할 수 있는 경우를 지정합니다. 다음 중에서 선택합니다. <ul><li>**차단됨**: 이 앱과 다른 앱 간에 잘라내기, 복사 및 붙여넣기 작업을 허용하지 않습니다.</li><li>**정책 관리 앱**: 이 앱과 다른 정책 관리 앱 간에만 잘라내기, 복사 및 붙여넣기 작업을 허용합니다.</li><li>**정책 관리 앱에 붙여넣기**: 이 앱과 다른 정책 관리 앱 간에 잘라내기 또는 복사를 허용합니다. 모든 앱의 데이터를 이 앱에 붙여넣을 수 있습니다.</li><li>**모든 앱**: 이 앱과 다른 앱 간의 잘라내기, 복사 및 붙여넣기에 대한 제한이 없습니다. | 모든 앱 |
|**Managed Browser에서 표시할 수 있는 웹 콘텐츠 제한** | 앱의 웹 링크를 Managed Browser 앱에서 열 수 있도록 적용하려면 **예**를 선택합니다. <br><br> Intune에 등록되지 않은 장치의 경우 Managed Browser 앱에서만 정책 관리 앱의 웹 링크를 열 수 있습니다. <br><br> Intune을 사용하여 장치를 관리하는 경우 [Microsoft Intune에서 Managed Browser 정책을 사용하여 인터넷 액세스 관리](app-configuration-managed-browser.md)를 참조하세요.<br><br> 모바일 장치(iOS 및 Android)용 Microsoft Edge 브라우저는 Intune 앱 보호 정책을 지원합니다. Edge 브라우저 응용 프로그램에서 회사 Azure AD 계정으로 로그인하는 사용자는 Intune에서 보호됩니다. Edge 브라우저는 MAM SDK를 통합하고, 다음과 같은 방지를 제외하고는 모든 데이터 보호 정책을 지원합니다.<ul><li>**다른 이름으로 저장**: Microsoft Edge 브라우저에서 사용자가 클라우드 저장소 공급자(예: OneDrive)에 직접 앱 내 연결을 추가할 수 없습니다.</li><li>**연락처 동기화**: Microsoft Edge 브라우저는 기본 연락처 목록에 저장하지 않습니다.</li></ul> | 아니요 |
| **앱 데이터 암호화** | 이 앱에서 회사 또는 학교 데이터의 암호화를 적용하려면 **예**를 선택합니다. Intune에서는 Android 키 저장소 시스템과 함께 OpenSSL, 128비트 AES 암호화 체계를 사용하여 앱 데이터를 안전하게 암호화합니다. 데이터는 파일 I/O 작업 동안 동기적으로 암호화됩니다. 장치 저장소의 콘텐츠는 항상 암호화됩니다. <br><br> 이 암호화 방법은 FIPS 140-2의 인증을 받지 **않았습니다**.  | 예 |
| **장치 암호화를 사용하는 경우 앱 암호화를 사용하지 않음** | 장치 암호화가 등록된 장치에서 검색되는 경우 **예**를 선택하여 내부 앱 저장소에 앱 암호화를 사용하지 않도록 합니다. <br><br>**참고:** Intune은 Intune MDM을 사용하여 장치 등록을 검색할 수 있습니다. 관리되지 않는 응용 프로그램이 데이터에 액세스할 수 없도록 외부 앱 저장소가 계속 암호화됩니다. | 예 |
| **연락처 동기화 사용 안 함** | 앱에서 장치의 네이티브 연락처 앱에 데이터를 저장하는 것을 방지하려면 **예**를 선택합니다. **아니요**를 선택하면 앱에서 장치의 네이티브 연락처 앱에 데이터를 저장할 수 있습니다. <br><br>선택적 초기화를 수행하여 앱에서 회사 또는 학교 데이터를 제거할 경우 앱에서 네이티브 연락처 앱으로 직접 동기화된 연락처가 제거됩니다. 기본 주소록에서 다른 외부 소스에 동기화된 연락처는 초기화할 수 없습니다. 현재 Microsoft Outlook 앱에만 적용됩니다. | 아니요 |
| **인쇄를 사용하지 않도록 설정** | 앱에서 회사 또는 학교 데이터를 인쇄하는 것을 방지하려면 **예**를 선택합니다. | 아니요 |

  >[!NOTE]
  >**앱 데이터 암호화** 설정의 암호화 방법은 FIPS 140-2의 인증을 받지**않았습니다**.

  ## <a name="data-transfer-exemptions"></a>데이터 전송 예외

  Intune 앱 보호 정책에서 데이터 송수신을 허용할 수 있는 예외적인 앱 및 플랫폼 서비스가 일부 있습니다. 예를 들어 Android의 모든 Intune 관리 앱이 Google 텍스트 음성 변환 서비스로 데이터를 전송하고 이 서비스에서 데이터를 전송받을 수 있어야 모바일 장치 화면의 텍스트를 소리 내어 읽어주는 기능을 사용할 수 있습니다. 이 목록은 변경될 수 있으며 생산성 보장에 유용한 서비스 및 앱을 나타냅니다.

  ### <a name="full-exemptions"></a>완전 예외

  다음 앱 및 서비스에서는 Intune 관리 앱으로 데이터를 전송하거나 이 앱에서 데이터 전송받는 것이 완전히 허용됩니다.

  |앱/서비스 이름 | 설명 |
  | ------ | ---- |
  | com.android.phone | 네이티브 휴대폰 앱
  | com.android.vending | Google Play 스토어 |
  | com.android.documentsui | Android 문서 선택기|
  | com.google.android.webview | [WebView](https://developer.android.com/reference/android/webkit/WebView.html) - Outlook을 비롯한 여러 앱에 필요합니다. |
  | com.android.webview |[Webview](https://developer.android.com/reference/android/webkit/WebView.html) - Outlook을 비롯한 여러 앱에 필요합니다.|
  | com.google.android.tts | Google 텍스트 음성 변환 |
  | com.android.providers.settings | Android 시스템 설정 |
  | com.android.settings | Android 시스템 설정 |
  | com.azure.authenticator | Azure Authenticator 앱 - 여러 시나리오에서 성공적인 인증을 위해 필요합니다. |
  | com.microsoft.windowsintune.companyportal | Intune 회사 포털|

  ### <a name="conditional-exemptions"></a>조건부 예외
  다음 앱 및 서비스에서는 Intune 관리 앱으로 데이터를 전송하거나 이 앱에서 데이터를 전송받는 것이 특정 조건에서만 허용됩니다.

  |앱/서비스 이름 | 설명 | 예외 조건|
  | ------ | ---- | --- |
  | com.android.chrome | Google Chrome 브라우저 | Chrome은 Android 7.0 이상에서 일부 WebView 구성 요소에 사용되며 보기에서 숨겨지지 않습니다. 그러나 앱으로 들어오거나 앱에서 나가는 데이터 흐름은 항상 제한됩니다.  |
  | com.skype.raider | Skype | Skype 앱은 전화를 걸게 되는 특정 작업에 대해서만 허용됩니다. |
  | com.android.providers.media | Android 미디어 콘텐츠 공급자 | 미디어 콘텐츠 공급자는 벨소리 선택 작업에 대해서만 허용됩니다. |
  | com.google.android.gms; com.google.android.gsf | Google Play 서비스 패키지 | 이러한 패키지는 푸시 알림 등의 Google Cloud Messaging 작업에 대해서 허용됩니다. |

자세한 내용은 [앱에 대한 데이터 전송 정책 예외](app-protection-policies-exception.md)를 참조합니다.

##  <a name="access-settings"></a>액세스 설정

| Setting | 사용 방법 |  
|------|------| 
| **액세스하려면 PIN 필요** | 이 앱을 사용하는 데 PIN을 요구하려면 **예**를 선택합니다. 회사 또는 학교 컨텍스트에서 앱을 처음으로 실행할 때 이 PIN을 설정하라는 메시지가 표시됩니다. <br><br> 기본값은 **예**입니다.<br><br> PIN 강도에 대한 다음 설정을 구성합니다. <br> <ul><li>**유형 선택**: 앱 보호 정책이 적용된 앱에 액세스하기 전에 숫자 또는 암호 유형 PIN의 요구 사항을 설정합니다. 숫자 요구 사항에는 숫자만 포함되고, 암호는 1자 이상의 알파벳 문자 **또는** 1자 이상의 특수 문자로 정의할 수 있습니다. <br><br> 기본값 = **숫자**<br><br> **참고:** 허용되는 특수 문자에는 Android 영어 키보드의 기호 및 특수 문자가 포함됩니다.</li></ul>  <ul><li>**PIN 초기화 전 시도 횟수**: 초기화하기 전까지 PIN을 성공적으로 입력하기 위해 시도할 수 있는 횟수를 지정합니다. <br><br> 기본값 = **5** </li> <br> <li> **단순한 PIN 허용**: 사용자가 *1234*, *1111*, *abcd* 또는 *aaaa*와 같은 단순한 PIN 시퀀스를 사용할 수 있도록 허용하려면 **예**를 선택합니다. 단순한 순서를 사용하는 것을 방지하려면 **아니요**를 선택합니다. <br><br>기본값은 **예**입니다. <br><br>**참고**: 암호 형식 PIN을 구성하고, 단순 PIN 허용을 예로 설정한 경우 사용자 PIN에 1자 이상의 문자 **또는** 1자 이상의 특수 문자가 포함되어야 합니다. 암호 형식 PIN을 구성하고, 단순 PIN 허용을 아니요로 설정한 경우 사용자 PIN에 1개 이상의 숫자 **및** 1자 이상의 문자**와** 1자 이상의 특수 문자가 포함되어야 합니다.* </li> <br> <li>  **PIN 길이**: PIN 시퀀스의 최소 자릿수를 지정합니다. <br><br>기본값 = **4** </li> <br> <li> **PIN 대신 지문 허용(Android 6.0 이상)**: 앱 액세스에 PIN 대신 [지문 인증](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)을 사용하도록 허용하려면 **예**를 선택합니다. <br><br>기본값 = **예** <br><br>***참고**: 이 기능은 Android 장치에서 생체 인식을 위한 일반 컨트롤을 지원합니다. * Samsung Pass와 같은 OEM 특정 생체 인식 설정은 ‘지원되지 않습니다.’ <br><br>Android에서 PIN 대신 [Android 지문 인증](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)을 사용하여 ID를 증명하도록 허용할 수 있습니다. 회사 또는 학교 계정으로 이 앱을 열려고 하면 PIN을 입력하는 대신 해당 지문 ID를 제공하라는 메시지가 표시됩니다. <br><br> Android 회사 프로필은 **PIN 대신 지문 허용** 정책을 적용하려면 별도의 지문을 등록해야 합니다. 이 정책은 Android 회사 프로필에 설치된 정책 관리 앱에만 적용됩니다. 회사 포털에서 등록하여 Android 회사 프로필을 만든 후 별도의 지문을 장치에 등록해야 합니다. Android 회사 프로필을 사용하는 회사 프로필 지문에 대한 자세한 내용은 [회사 프로필 잠금](https://support.google.com/work/android/answer/7029958)을 참조하세요.| 
| **액세스 시 회사 자격 증명 필요** | 앱 액세스에 PIN을 입력하는 대신 해당 회사 또는 학교 계정으로 로그인하도록 요구하려면 **예**를 선택합니다. **예**로 설정하고 PIN 또는 생체 인식 프롬프트를 사용하는 경우 회사 자격 증명과, PIN 또는 생체 인식 프롬프트가 표시됩니다. <br><br>기본값은 **아니요**입니다. |
| **관리되는 앱이 무단 해제 또는 루팅된 장치를 실행할 수 없도록 차단** |이 앱이 무단 해제 또는 루팅된 장치에서 실행되는 것을 차단하려면 **예**를 선택합니다. 개인적인 작업에 이 앱을 계속 사용할 수 있지만 이 앱의 회사 또는 학교 데이터에 액세스하려면 다른 장치를 사용해야 합니다. <br><br>기본값은 **예**입니다. |
| **액세스 요구 사항을 다시 확인할 시간(분)** | 다음 설정을 구성합니다. <ul><li>**제한 시간**: 이전에 정책에서 정의된 액세스 요구 사항이 다시 확인되기까지 걸리는 시간(분)입니다. 예를 들어 관리자가 정책에서 장치에 루팅된 PIN 및 블록을 설정하고, 사용자가 Intune 관리 앱을 열 때, PIN을 입력해야 하고 루팅되지 않은 장치에서 앱을 사용해야 합니다. 이 설정을 사용하는 경우 사용자가 구성된 값과 같은 기간에 Intune 관리 앱에서 PIN을 다시 입력하거나 또 다른 root-detection 확인을 할 필요가 없습니다.  <br><br>이 정책 설정 형식은 양의 정수를 지원합니다. <br><br> 기본값 = **30분** <br><br> **참고:** Android에서는 PIN이 모든 Intune 관리 앱 간에 공유됩니다. 앱이 장치에서 포그라운드를 나가면 PIN 타이머가 재설정됩니다. 사용자는 이 설정에서 정의한 제한 시간 동안 PIN을 공유하는 Intune 관리 앱에 PIN을 입력할 필요가 없습니다.* <br><br></li><li>**오프라인 유예 기간**: MAM 앱이 오프라인으로 실행할 수 있는 시간(분)입니다. 앱에 대한 액세스 요구 사항을 다시 확인하기 전의 시간(분)을 지정합니다. 이 기간이 만료된 후에 앱을 계속 실행하려면 Azure AD(Azure Active Directory)에 대한 사용자 인증이 필요합니다. <br><br>이 정책 설정 형식은 양의 정수를 지원합니다. <br><br>기본값 = **720**분(12시간)</li></ul>|
| **앱 데이터를 초기화하기 전의 오프라인 간격(일)** | 이 오랜 기간(관리자가 정의) 앱이 오프라인으로 실행된 후에 사용자가 네트워크에 연결하고 다시 인증해야 합니다. 성공적으로 인증하고 나면 데이터에 계속 액세스할 수 있으며 오프라인 간격이 재설정됩니다. 사용자가 인증에 실패하면 앱에서 사용자 계정과 데이터를 선택적으로 초기화합니다. 선택적 초기화로 제거되는 데이터에 대한 자세한 내용은 [Intune-관리 앱에서 회사 데이터만 초기화하는 방법](https://docs.microsoft.com/intune/apps-selective-wipe)을 참조하세요. <br><br>이 정책 설정 형식은 양의 정수를 지원합니다. <br><br>기본값 = **90일** |
| **화면 캡처 및 Android Assistant 차단(Android 6.0 이상)** | 이 앱을 사용할 때 장치의 화면 캡처 및 **Android Assistant** 기능을 차단하려면 **예**를 선택합니다. **예**를 선택하면 회사 또는 학교 계정으로 이 앱을 사용할 때 최근 사용 앱 미리 보기 이미지도 흐리게 표시됩니다. <br><br>기본값은 **아니요**입니다. |
| **장치 PIN을 관리하는 경우 앱 PIN 사용 안 함** | 등록된 장치에서 장치 잠금이 검색되는 경우 앱 PIN을 사용하지 않도록 설정하려면 **예**를 선택합니다. <br><br>**참고:** Intune은 Android에서 타사 EMM 솔루션을 사용한 장치 등록을 검색할 수 없습니다. <br><br>기본값은 **아니요**입니다. |
| **최소 Android 운영 체제 필요** | 이 앱을 사용하기 위한 최소 Android 운영 체제를 요구하려면 **예**를 선택합니다. 장치의 Android 버전이 요구 사항을 충족하지 않으면 사용자 액세스가 차단됩니다. <br><br>이 정책 설정 형식은 major.minor, major.minor.build, major.minor.build.revision을 지원합니다. <br><br>기본값은 **아니요**입니다. |
| **최소 Android 운영 체제 필요(경고)** | 이 앱을 사용하기 위한 최소 Android 운영 체제를 요구하려면 **예**를 선택합니다. 장치의 Android 버전이 요구 사항을 충족하지 않으면 사용자에게 알림이 표시됩니다. 이 알림은 무시할 수 있습니다.<br><br> 이 정책 설정 형식은 major.minor, major.minor.build, major.minor.build.revision을 지원합니다. <br><br>기본값은 **아니요**입니다. |
| **Require minimum app version**(최소 앱 버전 필요) | 앱을 사용할 최소 앱 버전을 요구하려면 **예**를 선택합니다. 장치의 앱 버전이 요구 사항을 충족하지 않으면 사용자 액세스가 차단됩니다.<br><br>응용 프로그램 간에 서로 다른 버전 지정 체계를 종종 있는 하나의 앱을 대상으로 하는 하나의 최소 응용 프로그램 버전으로는 정책(예를 들어 ‘Outlook 버전 정책’)을 만듭니다. <br><br> 이 정책 설정 형식은 major.minor, major.minor.build, major.minor.build.revision을 지원합니다. <br><br>기본값은 **아니요**입니다. |
| **Require minimum app version (Warning only)**(최소 앱 버전 필요(경고)) | 이 앱을 사용하기 위한 최소 앱 버전을 권장하려면 **예**를 선택합니다. 장치의 앱 버전이 요구 사항을 충족하지 않으면 사용자에게 알림이 표시됩니다. 이 알림은 무시할 수 있습니다.<br><br>응용 프로그램 간에 서로 다른 버전 지정 체계를 종종 있는 하나의 앱을 대상으로 하는 하나의 최소 응용 프로그램 버전으로는 정책(예를 들어 ‘Outlook 버전 정책’)을 만듭니다. <br><br> 이 정책 설정 형식은 major.minor, major.minor.build, major.minor.build.revision을 지원합니다. <br><br>기본값은 **아니요**입니다. |
| **최소 Android 패치 버전 필요** | Google이 출시한 최소 Android 보안 패치를 요구하려면 **예**를 선택합니다. 장치의 Android 보안 패치가 요구 사항을 충족하지 않으면 사용자 액세스가 차단됩니다.<br><br> 이 정책 설정 형식은 *YYYY-MM-DD* 날짜 형식을 지원합니다.  <br><br>기본값은 **아니요**입니다. |
| **최소 Android 패치 버전 필요(경고)** | Google이 출시한 최소 Android 보안 패치를 요구하려면 **예**를 선택합니다. 장치의 Android 보안 패치가 요구 사항을 충족하지 않으면 사용자에게 알림이 표시됩니다. 이 알림은 무시할 수 있습니다.<br><br> 이 정책 설정 형식은 *YYYY-MM-DD* 날짜 형식을 지원합니다.  <br><br>기본값은 **아니요**입니다.|

> [!NOTE]
> 동일한 앱과 사용자 집합에 대한 액세스 섹션에서 구성된 여러 Intune 앱 보호 설정이 Android에서 작동하는 방법에 대해 자세히 알아보려면 [Intune MAM 질문과 대답](mam-faq.md) 및 [Intune에서 앱 보호 정책 액세스 작업을 사용하여 선택적으로 데이터 초기화](app-protection-policies-access-actions.md)를 참조하세요.
