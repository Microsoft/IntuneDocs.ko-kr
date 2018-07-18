---
title: 응용 프로그램을 위한 데이터 전송 정책 예외
titleSuffix: Microsoft Intune
description: Intune 모바일 응용 프로그램 관리(MAM) 데이터 전송 정책에 대한 예외를 만듭니다.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 34174568570700e0b15d5bce1bb0bf239251b577
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039157"
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Intune 모바일 응용 프로그램 관리(MAM) 데이터 전송 정책에 대한 예외를 만드는 방법

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

관리자로서 Intune 모바일 응용 프로그램 관리(MAM) 데이터 전송 정책에 대한 예외를 만들 수 있습니다. 예외를 통해 관리되지 않는 응용 프로그램과 관리되는 응용 프로그램 간에 데이터를 전송할 수 있도록 구체적으로 선택할 수 있습니다. 예외 목록에 포함된 관리되지 않는 앱은 IT의 신뢰를 받아야 합니다. 

>[!WARNING] 
> 데이터 전송 예외 정책의 변경에 책임이 있습니다. 이 정책에 대한 추가는 관리되지 않는 응용프로그램(Intune에서 관리되지 않는 응용프로그램)이 관리되는 응용프로그램의 보호를 받는 데이터에 액세스할 수 있게 합니다. 보호된 데이터에 대한 액세스는 데이터 보안이 유출될 수 있습니다. 조직이 사용해야 하는 응용 프로그램에 대한 데이터 전송 예외만 추가하지만 Intune APP(응용 프로그램 보호 정책)을 지원하지는 않습니다. 또한 데이터 유출 위험으로 간주되지 않는 응용 프로그램에 대한 예외만 추가합니다.

Intune Application Protection Policy 내에서 **앱이 다른 앱으로 데이터를 전송하도록 허용**을 **정책 관리 앱**으로 설정하면 앱이 Intune에서 관리하는 앱으로만 데이터를 전송할 수 있음을 의미합니다. Intune 앱을 지원하지 않는 특정 앱으로 데이터 전송을 허용해야 하는 경우에는 **제외할 앱 선택**을 사용하여 정책에 대한 예외를 만들 수 있습니다. 제외를 통해 Intune에서 관리하는 응용 프로그램이 URL 프로토콜(iOS) 또는 패키지 이름(Android)을 기반으로 관리되지 않는 응용 프로그램을 호출하게 할 수 있습니다. 기본적으로 Intune은 중요한 네이티브 응용 프로그램을 이 예외 목록에 추가합니다. 

> [!NOTE]
> 데이터 전송 정책 예외의 수정이나 추가는 제한 자르기, 복사 및 붙여넣기 같은 다른 앱 보호 정책에 영향을 미치지 않습니다. 

## <a name="ios-data-transfer-exceptions"></a>iOS 데이터 전송 예외
IOS를 대상으로 하는 정책의 경우 URL 프로토콜에서 데이터 전송 예외를 구성할 수 있습니다. 예외를 추가하려면 지원되는 URL 프로토콜 정보 찾기 응용 프로그램의 개발자가 제공한 설명서를 확인합니다. IOS 데이터 전송 예외에 대한 자세한 내용은 [iOS 응용 프로그램 보호 정책 설정 - 데이터 전송 예외](app-protection-policy-settings-ios.md#data-transfer-exemptions)를 참조합니다.

> [!NOTE]
> Microsoft는 타사 응용 프로그램에 대한 앱 예외를 만들기 위한 URL 프로토콜을 수동으로 찾을 수 있는 방법이 없습니다. 

## <a name="android-data-transfer-exceptions"></a>Android 데이터 전송 예외
Android 대상으로 하는 정책의 경우 응용 프로그램 패키지 이름으로 데이터 전송 예외를 구성할 수 있습니다. 예외를 추가하고자 하는 응용 프로그램에 대해 **Google Play** 스토어 페이지를 확인해 응용 프로그램 패키지 이름을 찾을 수 있습니다. Android 데이터 전송 예외에 대한 자세한 내용은 [Android 응용 프로그램 보호 정책 설정 - 데이터 전송 예외](app-protection-policy-settings-android.md#data-transfer-exemptions)를 참조합니다.


>[!TIP]
> Google Play 스토어에서 앱을 탐색하여 앱의 패키지 ID를 찾을 수 있습니다. 패키지 ID는 앱 페이지의 URL에 포함되어 있습니다. 예를 들어 Microsoft Word 앱의 패키지 ID는 **com.microsoft.office.word**입니다.

### <a name="example"></a>예제
**Webex** 패키지를 예외로 MAM 데이터 전송 정책에 추가함으로써 관리되는 Outlook 이메일 메시지 내의 Webex 링크는 Webex 응용 프로그램에서 직접 열 수 있습니다. 데이터 전송은 관리되지 않는 다른 응용 프로그램에서 계속 제한됩니다.

- iOS **Webex** 예: Intune 관리 앱이 호출할 수 있도록 **Webex** 앱을 제외하려면 다음 문자열에 대한 데이터 전송 예외를 추가해야 합니다. <code>wbx</code>
    
 - iOS **Maps** 예: Intune 관리 앱이 호출할 수 있도록 네이티브 **Maps** 앱을 제외하려면 다음 문자열에 대한 데이터 전송 예외를 추가해야 합니다. <code>maps</code>

- Android **Webex** 예: Intune 관리 앱이 호출할 수 있도록 **Webex** 앱을 제외하려면 다음 문자열에 대한 데이터 전송 예외를 추가해야 합니다. <code>com.cisco.webex.meetings</code>
    
- Android **SMS** 예: 다양한 메시징 앱과 Android 장치에서 Intune 관리 앱이 호출할 수 있도록 네이티브 **SMS** 앱을 제외하려면 다음 문자열에 대한 데이터 전송 예외를 추가해야 합니다. 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>다음 단계

- [앱 보호 정책 만들기 및 배포](app-protection-policies.md)
- [iOS 앱 보호 정책 설정 - 데이터 전송 예외](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Android 앱 보호 정책 설정 - 데이터 전송 예외](app-protection-policy-settings-android.md#data-transfer-exemptions)
