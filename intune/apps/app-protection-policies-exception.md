---
title: 응용 프로그램을 위한 데이터 전송 정책 예외
titleSuffix: Microsoft Intune
description: Intune APP(앱 보호 정책) 데이터 전송 정책에 대한 예외를 만듭니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09c8a8819c288663936174e9317267c39eac63bc
ms.sourcegitcommit: ecaff388038fb800f2e646f8efcf8f3b1e2fd1b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/18/2020
ms.locfileid: "77437854"
---
# <a name="how-to-create-exceptions-to-the-intune-app-protection-policy-app-data-transfer-policy"></a>Intune APP(앱 보호 정책) 데이터 전송 정책에 대한 예외를 만드는 방법

관리자는 Intune APP(앱 보호 정책) 데이터 전송 정책에 대한 예외를 만들 수 있습니다. 예외를 통해 관리되지 않는 응용 프로그램과 관리되는 응용 프로그램 간에 데이터를 전송할 수 있도록 구체적으로 선택할 수 있습니다. IT는 예외 목록에 포함된 관리되지 않는 앱을 신뢰해야 합니다. 

>[!WARNING] 
> 데이터 전송 예외 정책의 변경에 책임이 있습니다. 이 정책에 대한 추가는 관리되지 않는 응용프로그램(Intune에서 관리되지 않는 응용프로그램)이 관리되는 응용프로그램의 보호를 받는 데이터에 액세스할 수 있게 합니다. 보호된 데이터에 대한 액세스는 데이터 보안이 유출될 수 있습니다. 조직이 사용해야 하는 애플리케이션에 대한 데이터 전송 예외만 추가하지만 Intune APP(애플리케이션 보호 정책)을 지원하지는 않습니다. 또한 데이터 유출 위험으로 간주되지 않는 응용 프로그램에 대한 예외만 추가합니다.

Intune Application Protection Policy 내에서 **앱이 다른 앱으로 데이터를 전송하도록 허용**을 **정책 관리 앱**으로 설정하면 앱이 Intune에서 관리하는 앱으로만 데이터를 전송할 수 있음을 의미합니다. Intune 앱을 지원하지 않는 특정 앱으로 데이터 전송을 허용해야 하는 경우에는 **제외할 앱 선택**을 사용하여 이 정책에 대한 예외를 만들 수 있습니다. 제외를 통해 Intune에서 관리하는 애플리케이션이 URL 프로토콜(iOS) 또는 패키지 이름(Android)을 기반으로 관리되지 않는 애플리케이션을 호출하게 할 수 있습니다. 기본적으로 Intune은 중요한 네이티브 애플리케이션을 이 예외 목록에 추가합니다. 

> [!NOTE]
> 데이터 전송 정책 예외의 수정이나 추가는 제한 자르기, 복사 및 붙여넣기 같은 다른 앱 보호 정책에 영향을 미치지 않습니다. 

## <a name="ios-data-transfer-exceptions"></a>iOS 데이터 전송 예외
iOS/iPadOS를 대상으로 하는 정책의 경우 URL 프로토콜에서 데이터 전송 예외를 구성할 수 있습니다. 예외를 추가하려면 지원되는 URL 프로토콜 정보 찾기 응용 프로그램의 개발자가 제공한 설명서를 확인합니다. iOS/iPadOS 데이터 전송 예외에 대한 자세한 내용은 [iOS 앱 보호 정책 설정 - 데이터 전송 예외](app-protection-policy-settings-ios.md#data-transfer-exemptions)를 참조하세요.

> [!NOTE]
> Microsoft는 타사 애플리케이션에 대한 앱 예외를 만들기 위한 URL 프로토콜을 수동으로 찾을 수 있는 방법이 없습니다. 

## <a name="android-data-transfer-exceptions"></a>Android 데이터 전송 예외
Android 대상으로 하는 정책의 경우 응용 프로그램 패키지 이름으로 데이터 전송 예외를 구성할 수 있습니다. 예외를 추가하고자 하는 응용 프로그램에 대해 **Google Play** 스토어 페이지를 확인해 응용 프로그램 패키지 이름을 찾을 수 있습니다. Android 데이터 전송 예외에 대한 자세한 내용은 [Android 앱 보호 정책 설정 - 데이터 전송 예외](app-protection-policy-settings-android.md#data-transfer-exemptions)를 참조하세요.


>[!TIP]
> Google Play 스토어에서 앱을 탐색하여 앱의 패키지 ID를 찾을 수 있습니다. 패키지 ID는 앱 페이지의 URL에 포함되어 있습니다. 예를 들어 Microsoft Word 앱의 패키지 ID는 **com.microsoft.office.word**입니다.

### <a name="example"></a>예제
**Webex** 패키지를 예외로 MAM 데이터 전송 정책에 추가함으로써 관리되는 Outlook 이메일 메시지 내의 Webex 링크는 Webex 애플리케이션에서 직접 열 수 있습니다. 데이터 전송은 관리되지 않는 다른 응용 프로그램에서 계속 제한됩니다.

- iOS/iPadOS **Webex** 예제:   Intune 관리 앱이 호출할 수 있도록 **Webex** 앱을 제외하려면 다음 문자열에 대한 데이터 전송 예외를 추가해야 합니다. <code>wbx</code>
    
- iOS/iPadOS **Maps** 예제:   Intune 관리 앱이 호출할 수 있도록 네이티브 **Maps** 앱을 제외하려면 다음 문자열에 대한 데이터 전송 예외를 추가해야 합니다. <code>maps</code>

- Android **Webex** 예제:   Intune 관리 앱이 호출할 수 있도록 **Webex** 앱을 제외하려면 다음 문자열에 대한 데이터 전송 예외를 추가해야 합니다. <code>com.cisco.webex.meetings</code>
    
- Android **SMS** 예제:   다양한 메시징 앱과 Android 디바이스에서 Intune 관리 앱이 호출할 수 있도록 네이티브 **SMS** 앱을 제외하려면 다음 문자열에 대한 데이터 전송 예외를 추가해야 합니다. 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

- Android **인증서 설치 관리자** 예: Android용 Outlook에서 S/MIME 인증서(메일 첨부 파일로 제공)를 Android 키 저장소에 설치할 수 있도록 네이티브 **인증서 설치 관리자** 앱을 제외하려면 문자열 <code>com.android.certinstaller</code>에 대한 데이터 전송 예외를 추가해야 합니다. 자세한 내용은 [iOS/iPadOS 및 Android용 Outlook의 민감도 레이블 지정 및 보호](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/sensitive-labeling-and-protection-outlook-for-ios-android)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [앱 보호 정책 만들기 및 배포](app-protection-policies.md)
- [iOS 앱 보호 정책 설정 - 데이터 전송 예외](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Android 앱 보호 정책 설정 - 데이터 전송 예외](app-protection-policy-settings-android.md#data-transfer-exemptions)
