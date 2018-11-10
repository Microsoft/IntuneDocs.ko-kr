---
title: iOS 앱 간의 데이터 전송 관리
titlesuffix: Microsoft Intune
description: 앱 간 데이터 전송을 관리하려면 Microsoft Intune에서 모바일 앱 관리를 사용하는 법을 이해합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 491d2884f73d9178f54b6b2861bfe6f248c41c63
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236563"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Microsoft Intune에서 iOS 앱 간의 데이터 전송 관리 방법
## <a name="manage-ios-apps"></a>IOS 앱 관리
회사 데이터 보호는 파일 전송이 관리하는 앱으로만 제한되도록 하는 작업을 포함합니다.  다음과 같은 방법으로 iOS 앱을 관리할 수 있습니다.

-   앱에 대해 앱 보호 정책을 구성하여 회사 데이터 손실을 방지할 수 있습니다. 이러한 앱을 **정책 관리** 앱이라고 합니다. [앱 보호 정책을 사용하여 관리할 수 있는 모든 Intune 관리 앱](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)을 참조하세요.

-   **MDM 채널**을 사용하여 앱을 배포하고 관리할 수도 있습니다.  이렇게 하려면 MDM 솔루션에 장치를 등록해야 합니다. **정책 관리된** 앱 또는 다른 관리되는 앱일 수 있습니다.

iOS 장치의 **관리에서 열기** 기능은 **MDM 채널**을 통해 장치에 배포된 앱 간에만 파일 전송이 발생하도록 제한할 수 있습니다. 관리에서 열기 제한 사항은 구성 설정에서 설정되며 MDM 소프트웨어를 사용하여 배포됩니다.  사용자가 배포된 앱을 설치하면 설정한 제한 사항이 적용됩니다.

##  <a name="using-app-protection-with-ios-apps"></a>iOS 앱에서 앱 보호 사용
앱 보호 정책을 **관리에서 열기** 기능과 함께 사용하여 회사 데이터를 다음과 같은 방법으로 보호할 수 있습니다.

-   **직원 소유 장치는 MDM 솔루션에서 관리되지 않음:** 앱 보호 정책 설정을 **앱이 데이터를 전송하도록 허용: 정책 관리된 앱**으로 설정할 수 있습니다. 정책 관리된 앱의 다음에서 열기 동작에서는 다른 정책 관리된 앱만 공유 옵션으로 표시됩니다. 사용자가 정책으로 보호된 파일을 기본 메일에서 OneDrive의 첨부 파일로 보내려고 하는 경우 해당 파일을 읽을 수 없습니다.

-   **Intune에서 관리되는 장치:** Intune에 등록된 장치의 경우 앱 보호 정책이 있는 앱과 Intune을 통해 배포된 다른 관리되는 iOS 앱 간의 데이터 전송은 자동으로 허용됩니다. 데이터가 다른 앱으로 전송할 수 있도록 허용하는 방법을 지정하려면 **앱이 다른 앱으로 데이터를 전송할 수 있도록 허용** 설정을 사용하고 기본 설정 수준의 공유를 선택합니다. 앱이 다른 앱에서 데이터를 수신할 수 있도록 허용하는 방법을 지정하려면 **앱이 다른 앱에서 데이터를 수신할 수 있도록 허용** 설정을 사용하고 기본 설정 수준의 데이터 수신을 선택합니다. **관리에서 열기** 기능을 사용하여 Intune을 통해 배포된 앱 간의 데이터 전송을 제어할 수 있습니다. 앱 데이터를 수신하고 공유하는 방법에 대한 자세한 내용은 [데이터 재배치 설정](app-protection-policy-settings-ios.md#data-relocation-settings)을 참조하세요.   

-   **타사 MDM 솔루션으로 관리되는 장치:** iOS **관리에서 열기** 기능을 사용하여 관리되는 앱으로만 데이터 전송을 제한할 수 있습니다.
타사 MDM 솔루션을 사용하여 배포하는 앱도 Intune에서 구성한 앱 보호 정책과 연결되도록 하려면 [사용자 UPN 설정 구성](#configure-user-upn-setting-for-third-party-emm) 연습에서 설명한 대로 사용자 UPN 설정을 구성해야 합니다.  사용자 UPN 설정으로 앱을 배포하면 최종 사용자가 회사 계정을 사용하여 로그인할 때 앱 보호 정책이 앱에 적용됩니다.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Microsoft Intune 또는 타사 EMM에 대한 사용자 UPN 설정 구성
사용자 UPN 설정 구성은 Intune 또는 타사 EMM 솔루션으로 관리되는 장치에 **필요**합니다. 아래에 설명된 절차는 UPN을 구성하는 방법과 결과로 생성되는 최종 사용자 환경에 대한 일반적인 설명입니다.

1.  [Azure Portal](https://portal.azure.com)에서 iOS에 대한 [앱 보호 정책을 만들고 할당](app-protection-policies.md)합니다. 회사 요구 사항에 따라 정책 설정을 구성하고 이 정책이 있어야 하는 iOS 앱을 선택합니다.

2.  아래 일반적인 단계를 사용하여 Intune 또는 타사 MDM 솔루션을 통해 관리할 앱 및 전자 메일 프로필을 배포합니다. 이 환경은 예제 1에서도 설명합니다.

3.  다음 앱 구성 설정을 사용하여 앱을 배포합니다.

      **키** = IntuneMAMUPN,  **값** = <username@company.com>

      예: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  등록된 장치에 Intune 또는 타사 MDM 공급자를 사용하여 다음에서 **열기 관리** 정책을 배포합니다.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>예제 1: Intune 또는 타사 MDM 콘솔의 관리 환경

1. Intune 또는 타사 MDM 공급자의 관리 콘솔로 이동합니다. 등록된 iOS 장치에 응용 프로그램 구성 설정을 배포하는 콘솔 섹션으로 이동합니다.

2. [응용 프로그램 구성] 섹션에서 다음 설정을 입력합니다.

   **키** = IntuneMAMUPN,  **값** = <username@company.com>

   키/값 쌍의 정확한 구문은 타사 MDM 공급자에 따라 달라질 수 있습니다. 아래 표에서는 타사 MDM 공급자 및 키/값 쌍에 입력해야 하는 정확한 값의 예를 보여 줍니다.

|타사 MDM 공급자| 구성 키 | 값 형식 | 구성 값|
| ------- | ---- | ---- | ---- |
|Microsoft Intune| IntuneMAMUPN | 문자열 | {{UserPrincipalName}}|
|VMware AirWatch| IntuneMAMUPN | 문자열 | {UserPrincipalName}|
|MobileIron | IntuneMAMUPN | 문자열 | ${userUPN} **또는** ${userEmailAddress} |
|ManageEngine 모바일 장치 관리자 | IntuneMAMUPN | 문자열 | %upn% |


### <a name="example-2-end-user-experience"></a>예제 2: 최종 사용자 환경

1.  최종 사용자가 장치에 Microsoft Word 앱을 설치합니다.

2.  최종 사용자가 관리되는 기본 메일 앱을 시작하여 메일에 액세스합니다.

3.  최종 사용자가 Microsoft Word에서 기본 메일의 문서를 열려고 합니다.

4.  Word 앱이 시작되면 회사 계정을 사용하여 로그인하라는 메시지가 최종 사용자에게 표시됩니다.  메시지가 표시될 때 최종 사용자가 입력하는 계정이 Microsoft Word 앱에 대한 앱 구성 설정에서 지정한 계정과 일치해야 이와 같이 진행됩니다.

    > [!NOTE]
    > 최종 사용자는 개인적인 작업을 수행하기 위해 Word에 다른 개인 계정을 추가할 수 있으며 개인 컨텍스트에서 Word 앱을 사용하는 경우 이러한 개인 계정에는 앱 보호 정책이 적용되지 않습니다.

5.  로그인하면 앱 보호 정책 설정이 Word 앱에 적용됩니다.

6.  이제 데이터 전송이 성공하고 앱의 문서에 회사 ID로 태그가 지정됩니다. 또한 데이터가 회사 컨텍스트에서 처리되고 정책 설정이 그에 따라 적용됩니다.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>타사 EMM에 대한 사용자 UPN 설정 확인

사용자 UPN 설정을 구성한 후 iOS 앱이 Intune 앱 보호 정책을 받고 준수할 수 있는지 확인해야 합니다.

예를 들어 **Require app PIN**(앱 PIN 필요) 정책 설정은 장치에서 육안으로 쉽게 테스트할 수 있습니다. 이 정책이 **예**로 설정된 경우 최종 사용자가 회사 데이터에 액세스하려고 할 때 PIN을 설정하거나 입력하라는 메시지가 표시됩니다.

먼저 iOS 앱에 대한 [앱 보호 정책을 만들고 할당](app-protection-policies.md)합니다. 앱 보호 정책을 테스트하는 방법에 대한 자세한 내용은 [앱 보호 정책 유효성 검사](app-protection-policies-validate.md)를 참조하세요.


### <a name="see-also"></a>참고 항목
[Intune 앱 보호 정책이란?](app-protection-policy.md)
