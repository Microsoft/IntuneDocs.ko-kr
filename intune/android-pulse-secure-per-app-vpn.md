---
title: Android용 사용자 지정 앱별 VPN 프로필
titlesuffix: Microsoft Intune
description: Microsoft Intune으로 관리되는 Android 장치용 앱별 VPN 프로필을 만드는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 48f1227da6260217105120d31301f60b6e06110c
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186021"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Microsoft Intune 사용자 지정 프로필을 사용하여 Android 장치에 대한 앱별 VPN 프로필 만들기

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune으로 관리되는 Android 5.0 이상 장치용 앱별 VPN 프로필을 만들 수 있습니다. 먼저 Pulse Secure 또는 Citrix 연결 형식을 사용하는 VPN 프로필을 만듭니다. 그런 다음 VPN 프로필을 특정 앱과 연결하는 사용자 지정 구성 정책을 만듭니다.

Android 장치 또는 사용자 그룹에 정책을 할당한 후에 사용자가 PulseSecure 또는 Citrix VPN 클라이언트를 시작해야 합니다. 그러면 VPN 클라이언트는 지정한 앱에서 생성되는 트래픽만 열린 VPN 연결을 사용하도록 허용합니다.

> [!NOTE]
>
> 이 프로필에서는 Pulse Secure 및 Citrix 연결 형식만 지원됩니다.


## <a name="step-1-create-a-vpn-profile"></a>1단계: VPN 프로필 만들기


1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **장치 구성**을 선택합니다.
2. **관리** 섹션 아래의 **장치 구성** 창에서 **프로필**을 선택합니다.
2. 프로필 목록 창에서 **프로필 만들기**를 선택합니다.
3. **프로필 만들기** 창에서 VPN 프로필에 대한 **이름** 및 선택적 **설명**을 입력합니다.
4. **플랫폼** 드롭다운 목록에서 **Android**를 선택합니다.
5. **프로필** 유형 드롭다운 목록에서 선택 **VPN**을 선택합니다.
3. **설정** > **구성**을 선택한 다음 [VPN 설정을 구성하는 방법](vpn-settings-configure.md) 및 [Android 장치에 대한 Intune VPN 설정](vpn-settings-android.md)의 설정에 따라 VPN 프로필을 구성합니다.

VPN 프로필을 만들 때 지정하는 **연결 이름** 값을 적어 두세요. 다음 단계에서 이 이름이 필요합니다. 예를 들면 **MyAppVpnProfile**입니다.

## <a name="step-2-create-a-custom-configuration-policy"></a>2단계: 사용자 지정 구성 정책 만들기

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **장치 구성**을 선택합니다.
2. **관리** 섹션 아래의 **장치 구성** 창에서 **프로필**을 선택합니다.
3. 프로필 창에서 **프로필 만들기**를 클릭합니다.
4. **프로필 만들기** 창에서 사용자 지정 프로필에 대한 **이름** 및 **설명**을 입력합니다.
5. **플랫폼** 드롭다운 목록에서 **Android**를 선택합니다.
6. **프로필** 유형 드롭다운 목록에서 선택 **사용자 지정**을 선택합니다.
7. **설정** > **구성**을 선택합니다.
3. **사용자 지정 OMA-URI 설정** 창에서 **추가**를 선택합니다.
    - 설정 이름을 입력합니다.
    - **OMA-URI**로 **./Vendor/MSFT/VPN/Profile/*Name*/PackageList** 문자열을 지정합니다. 여기서 *Name*은 1단계에서 적어둔 연결 이름입니다. 이 예제에서 문자열은 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**입니다.
    - **데이터 형식**으로 **문자열**을 지정합니다.
    - **값**으로 프로필에 연결할 패키지가 세미콜론으로 구분된 목록을 만듭니다. 예를 들어 Excel 및 Google Chrome 브라우저에서 VPN 연결을 사용하려면 **com.microsoft.office.excel;com.android.chrome**과 같이 입력합니다.

![Android 앱별 VPN 사용자 지정 정책의 예](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>앱 목록을 블랙리스트 또는 허용 목록으로 설정(옵션)
  **블랙리스트** 값을 사용하여 VPN 연결을 사용*할 수 없는* 앱 목록을 지정할 수 있습니다. 다른 모든 앱은 VPN을 통해 연결됩니다.
또는 **허용 목록** 값을 사용하여 VPN 연결을 사용*할 수 있는* 앱 목록을 지정할 수 있습니다. 목록에 없는 앱은 VPN을 통해 연결되지 않습니다.
  1.    **사용자 지정 OMA-URI 설정** 창에서 **추가**를 선택합니다.
  2.    설정 이름을 입력합니다.
  3.    **OMA-URI**로 **./Vendor/MSFT/VPN/Profile/*Name*/Mode** 문자열을 사용합니다. 여기서 *Name*은 1단계에서 적어둔 VPN 프로필 이름입니다. 이 예제에서 문자열은 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**입니다.
  4.    **데이터 형식**으로 **문자열**을 지정합니다.
  5.    **값**에 **블랙리스트** 또는 **허용 목록**을 입력합니다.



## <a name="step-3-assign-both-policies"></a>3단계: 두 정책 모두 할당

[장치 프로필을 할당하는 방법](device-profile-assign.md)의 지침을 사용하여 필요한 사용자 또는 장치에 두 프로필을 모두 할당합니다.
