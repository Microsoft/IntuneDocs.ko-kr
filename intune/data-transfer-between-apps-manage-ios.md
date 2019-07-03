---
title: iOS 앱 간의 데이터 전송 관리
titleSuffix: Microsoft Intune
description: 앱 간 데이터 전송을 관리하려면 Microsoft Intune에서 모바일 앱 관리를 사용하는 법을 이해합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f97b3365036271a7f41e7c3274e8a3bd966407f3
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512146"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Microsoft Intune에서 iOS 앱 간의 데이터 전송 관리 방법

회사 데이터를 보호하려면 관리하는 앱으로만 파일 전송을 제한합니다. 다음과 같은 방법으로 iOS 앱을 관리할 수 있습니다.

-   **정책 관리** 앱이라고 하는 앱에 대한 앱 보호 정책을 구성하여 회사 데이터 손실을 방지합니다. [앱 보호 정책을 사용하여 관리할 수 있는 모든 Intune 관리 앱](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)을 참조하세요.

-   **MDM 채널**을 통해 앱을 배포 및 관리합니다. 이 경우 MDM(모바일 디바이스 관리) 솔루션에 디바이스를 등록해야 합니다. 배포하는 앱은 **정책 관리** 앱 또는 다른 관리되는 앱일 수 있습니다.

iOS 디바이스의 **관리에서 열기** 기능은 **MDM 채널**을 통해 디바이스에 배포된 앱 간에만 파일 전송이 발생하도록 제한할 수 있습니다. 구성 설정에서 *관리에서 열기* 제한 사항을 설정한 다음, MDM 솔루션을 사용하여 배포합니다.  사용자가 배포된 앱을 설치하면 설정한 제한 사항이 적용됩니다.

## <a name="use-app-protection-with-ios-apps"></a>iOS 앱에서 앱 보호 사용
iOS **관리에서 열기** 기능과 함께 앱 보호 정책을 사용하여 다음과 같은 방법으로 회사 데이터를 보호할 수 있습니다.

-   **직원 소유 디바이스는 MDM 솔루션에서 관리되지 않음:** 앱 보호 정책 설정을 **앱이 정책 관리 앱에만 데이터를 전송하도록 허용**으로 설정할 수 있습니다. 정책 관리 앱의 *여는 위치* 동작에서는 다른 정책 관리 앱만 공유 옵션으로 표시됩니다. 사용자가 기본 메일 앱의 OneDrive에서 첨부 파일로 정책 보호 파일을 보내려고 하는 경우 해당 파일을 읽을 수 없습니다.

-   **Intune에서 관리되는 디바이스:** Intune에 등록된 디바이스의 경우 앱 보호 정책이 있는 앱과 Intune을 통해 배포된 다른 관리되는 iOS 앱 간의 데이터 전송은 자동으로 허용됩니다. 다른 앱으로 데이터 전송을 허용하는 방법을 지정하려면 **앱이 데이터를 다른 앱에 전송하도록 허용**을 사용하도록 설정한 다음, 원하는 공유 수준을 선택합니다. 앱이 다른 앱에서 데이터를 수신할 수 있도록 허용하는 방법을 지정하려면 **앱이 다른 앱에서 데이터를 수신할 수 있도록 허용**을 사용하도록 설정한 다음, 원하는 데이터 수신 수준을 선택합니다. **관리에서 열기** 기능을 사용하여 Intune을 통해 배포된 앱 간의 데이터 전송을 제어할 수 있습니다. 앱 데이터를 수신하고 공유하는 방법에 대한 자세한 내용은 [데이터 재배치 설정](app-protection-policy-settings-ios.md#data-protection)을 참조하세요.   

-   **타사 MDM 솔루션에서 관리되는 디바이스:** iOS **관리에서 열기** 기능을 사용하여 관리되는 앱으로만 데이터 전송을 제한할 수 있습니다.
타사 MDM 솔루션을 사용하여 배포하는 앱도 Intune 앱 보호 정책과 연결되도록 하려면 [사용자 UPN 설정 구성](#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm) 섹션에서 설명된 대로 사용자 UPN 설정을 구성합니다. 사용자 UPN 설정으로 앱을 배포하면 사용자가 회사 계정을 사용하여 로그인할 때 앱 보호 정책이 앱에 적용됩니다.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Microsoft Intune 또는 타사 EMM에 대한 사용자 UPN 설정 구성
사용자 UPN 설정 구성은 Intune 또는 타사 EMM 솔루션으로 관리되는 디바이스에 **필요**합니다. UPN 구성은 Intune에서 배포하는 앱 보호 정책과 함께 작동합니다. 다음 프로시저는 UPN 설정 방법을 구성하는 방법과 그에 따른 사용자 환경에 대한 일반적인 흐름입니다.

1.  [Azure Portal](https://portal.azure.com)에서 iOS에 대한 [앱 보호 정책을 만들고 할당](app-protection-policies.md)합니다. 회사 요구 사항에 따라 정책 설정을 구성하고 이 정책이 있어야 하는 iOS 앱을 선택합니다.

2.  다음 일반화된 단계를 사용하여 Intune 또는 타사 MDM 솔루션을 통해 관리할 앱과 이메일 프로필을 배포합니다. 이 환경은 *예제 1*에서도 설명합니다.

3.  다음 앱 구성 설정을 사용하여 앱을 관리 디바이스에 배포합니다.

      **키** = IntuneMAMUPN, **값** = <username@company.com>

      예: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]
      
       > [!NOTE]
       > Intune에서 앱 구성 정책은 등록 유형 "관리 디바이스"에 대한 정책이어야 합니다.
       > 또한 앱은 사용 가능한 것으로 설정된 경우 Intune Company Portal에서 설치하거나 필요한 경우 디바이스에 푸시해야 합니다. 

4.  등록된 디바이스에 Intune 또는 타사 MDM 공급자를 사용하여 다음에서 **열기 관리** 정책을 배포합니다.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>예제 1: Intune 또는 타사 MDM 콘솔의 관리 환경

1. Intune 또는 타사 MDM 공급자의 관리 콘솔로 이동합니다. 등록된 iOS 장치에 애플리케이션 구성 설정을 배포하는 콘솔 섹션으로 이동합니다.

2. [애플리케이션 구성] 섹션에서 다음 설정을 입력합니다.

   **키** = IntuneMAMUPN, **값** = <username@company.com>

   키/값 쌍의 정확한 구문은 타사 MDM 공급자에 따라 달라질 수 있습니다. 다음 표에서는 타사 MDM 공급자 및 키/값 쌍에 입력해야 하는 정확한 값의 예를 보여줍니다.

   |타사 MDM 공급자| 구성 키 | 값 형식 | 구성 값|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | 문자열 | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | 문자열 | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | 문자열 | ${userUPN} **또는** ${userEmailAddress} |
   |Citrix 엔드포인트 관리 | IntuneMAMUPN | 문자열 | ${user.userprincipalname} |
   |ManageEngine 모바일 디바이스 관리자 | IntuneMAMUPN | 문자열 | %upn% |


### <a name="example-2-end-user-experience"></a>예제 2: 최종 사용자 환경

1.  사용자가 디바이스에 Microsoft Word 앱을 설치합니다.

2.  사용자가 관리되는 기본 이메일 앱을 시작하여 이메일에 액세스합니다.

3.  사용자가 Microsoft Word에서 기본 메일의 문서를 열려고 합니다.

4.  Word 앱이 시작되면 회사 계정을 사용하여 로그인하라는 메시지가 사용자에게 표시됩니다. 사용자가 입력하는 계정은 Microsoft Word 앱에 대한 앱 구성 설정에서 지정한 계정과 일치해야 합니다.

    > [!NOTE]
    > 사용자는 Word를 사용하여 개인 계정을 추가하고 사용할 수 있습니다. 사용자가 회사 컨텍스트 외부에서 Word를 사용하는 경우에는 앱 보호 정책이 적용되지 않습니다. 

5.  로그인 후에는 앱 보호 정책 설정이 Word 앱에 적용됩니다.

6.  이제 데이터 전송이 성공하고 앱의 문서에 회사 ID로 태그가 지정됩니다.  데이터는 회사 컨텍스트에서 처리되고 정책 설정이 적용됩니다. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>타사 EMM에 대한 사용자 UPN 설정 확인

사용자 UPN 설정을 구성한 후 iOS 앱이 Intune 앱 보호 정책을 수신하고 준수하는지 확인합니다.

예를 들어 **앱 PIN 필요** 정책 설정은 쉽게 테스트할 수 있습니다. 정책 설정이 **예**이면 회사 데이터에 액세스하기 전에 PIN을 설정하거나 입력하라는 메시지가 사용자에게 표시되어야 합니다.

먼저 iOS 앱에 대한 [앱 보호 정책을 만들고 할당](app-protection-policies.md)합니다. 앱 보호 정책을 테스트하는 방법에 대한 자세한 내용은 [앱 보호 정책 유효성 검사](app-protection-policies-validate.md)를 참조하세요.


### <a name="see-also"></a>참고 항목
[Intune 앱 보호 정책이란?](app-protection-policy.md)
