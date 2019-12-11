---
title: 등록되지 않은 디바이스에 Mobile Threat Defense 앱 추가
titleSuffix: Microsoft Intune
description: 디바이스 사용자가 등록 취소한 디바이스에 Mobile Threat Defense 앱 추가
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72794461"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>등록되지 않은 디바이스에 Mobile Threat Defense 앱 추가

기본적으로 Mobile Threat Defense와 함께 Intune 앱 보호 정책을 사용하는 경우 Intune은 최종 사용자가 디바이스에서 필요한 모든 앱을 설치하고 앱에 로그인하여 관련 서비스에 연결할 수 있도록 안내합니다.

최종 사용자는 디바이스를 등록하려면 Microsoft Authenticator(iOS)가 필요하며, 모바일 디바이스에서 위협이 식별될 때 알림을 받고 위협을 해결하기 위한 지침을 받으려면 Mobile Threat Defense(Android 및 iOS 모두)가 필요합니다.

필요에 따라 Intune을 사용하여 Microsoft Authenticator 및 MTD(Mobile Threat Defense) 앱도 추가하고 배포할 수 있습니다.

> [!NOTE] 
> 이 문서는 앱 보호 정책을 지원하는 모든 Mobile Threat Defense 파트너에게 적용됩니다. Better Mobile(Android), Zimperium(iOS), Lookout for Work(Android/iOS).
> 
> 등록되지 않은 디바이스의 경우 Intune과 함께 사용하는 iOS용 Mobile Threat Defense 앱을 설정하는 **iOS 앱 구성 정책이 필요하지 않습니다**. 이것이 Intune 등록된 디바이스에 대한 주요 차이점입니다. 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>Intune을 통해 iOS용 Microsoft Authenticator 구성(선택 사항)
Mobile Threat Defense와 함께 Intune 앱 보호 정책을 사용하는 경우 Intune은 최종 사용자가 디바이스를 설치하고, 로그인하고, Microsoft Authenticator(iOS)에 등록하는 방법을 안내합니다.

그러나 Intune 회사 포털을 통해 최종 사용자가 앱을 사용할 수 있도록 하려면 [Microsoft Intune에 iOS 스토어 앱 추가](../apps/store-apps-ios.md)에 대한 지침을 참조하세요. **앱 정보 구성** 섹션을 완료하면 이 [Microsoft Authenticator - iOS App Store URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)을 사용합니다. 마지막 단계로 [Intune을 사용하여 그룹에 앱을 할당](../apps/apps-deploy.md)해야 합니다.

> [!NOTE] 
> iOS 디바이스의 경우 사용자의 ID가 Azure AD에서 확인될 수 있도록 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)가 필요합니다. Intune 회사 포털은 사용자의 ID가 Azure AD에서 확인될 수 있도록 Android 디바이스에서 브로커로 작동합니다.

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>Intune을 통해 Mobile Threat Defense 앱을 사용할 수 있도록 설정(선택 사항)
Mobile Threat Defense와 함께 Intune 앱 보호 정책을 사용하는 경우 Intune은 최종 사용자가 필요한 Mobile Threat Defense 클라이언트 앱을 설치하고 로그인하도록 안내합니다. 

그러나 Intune 회사 포털을 통해 최종 사용자가 앱을 사용할 수 있도록 하려면 [Azure Portal](https://portal.azure.com/)에서 아래 단계를 수행하면 됩니다. 다음 프로세스에 대해 잘 알고 있어야 합니다.

- [Intune에 앱 추가](../apps/apps-add.md)
- [Intune을 사용하여 앱 할당](../apps/apps-deploy.md)

### <a name="making-lookout-for-work-available-to-end-users"></a>최종 사용자가 Lookout for Work를 사용할 수 있도록 설정
- **OWA(Outlook Web Access)**  
  - [Microsoft Intune에 Android 스토어 앱 추가](../apps/store-apps-android.md) 지침을 참조하세요. **앱 정보 구성** 섹션을 완료하면 이 [Lookout for Work - Play 스토어 URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise)을 사용합니다.

- **iOS**
  - [Microsoft Intune에 iOS 스토어 앱 추가](../apps/store-apps-ios.md) 지침을 참조하세요. **앱 정보 구성** 섹션을 완료하면 이 [Lookout for Work - iOS App Store URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8)을 사용합니다.

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>최종 사용자가 Zimperium을 사용할 수 있도록 설정
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS**
  - [Microsoft Intune에 iOS 스토어 앱 추가](../apps/store-apps-ios.md) 지침을 참조하세요. **앱 정보 구성** 섹션을 완료하면 이 [Zimperium - App Store URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8)을 사용합니다.
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>최종 사용자가 Better Mobile을 사용할 수 있도록 설정 
- **OWA(Outlook Web Access)**
  - [Microsoft Intune에 Android 스토어 앱 추가](../apps/store-apps-android.md) 지침을 참조하세요. **앱 정보 구성** 섹션을 완료하면 이 [Active Shield - Play 스토어 URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise)을 사용합니다.
<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>다음 단계  

- [Intune에서 등록되지 않은 디바이스에 Mobile Threat Defense 커넥터를 사용하도록 설정](~/protect/mtd-enable-unenrolled-devices.md)

