---
title: Android용 사용자 지정 앱별 VPN 프로필
titleSuffix: Microsoft Intune
description: Microsoft Intune으로 관리되는 Android 디바이스용 앱별 VPN 프로필을 만드는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62f418e396c5030a47ea0bcb31914cd4e1069c40
ms.sourcegitcommit: eb2e420b304c7da9d3be5ef49a676cba66766d2b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74319852"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Microsoft Intune 사용자 지정 프로필을 사용하여 Android 디바이스에 대한 앱별 VPN 프로필 만들기

Intune으로 관리되는 Android 5.0 이상 디바이스용 앱별 VPN 프로필을 만들 수 있습니다. 먼저 Pulse Secure 또는 Citrix 연결 형식을 사용하는 VPN 프로필을 만듭니다. 그런 다음 VPN 프로필을 특정 앱과 연결하는 사용자 지정 구성 정책을 만듭니다.

> [!NOTE]
> Android 엔터프라이즈 디바이스에서 앱별 VPN을 사용하려면 다음 단계를 사용할 수도 있습니다. 그러나 VPN 클라이언트 앱에 대해 [앱 구성 정책](../apps/app-configuration-policies-use-android.md)를 사용하는 것이 좋습니다.

Android 디바이스 또는 사용자 그룹에 정책을 할당한 후에 사용자가 PulseSecure 또는 Citrix VPN 클라이언트를 시작해야 합니다. 그러면 VPN 클라이언트는 지정한 앱에서 생성되는 트래픽만 열린 VPN 연결을 사용하도록 허용합니다.

> [!NOTE]
>
> 이 프로필에서는 Pulse Secure 및 Citrix 연결 형식만 지원됩니다.

## <a name="step-1-create-a-vpn-profile"></a>1단계: VPN 프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **전체 회사에 대한 Android 앱별 VPN 프로필**이 적절한 프로필 이름일 수 있습니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Android**를 선택합니다.
    - **프로필 유형**: **VPN**을 선택합니다.

4. **설정** > **구성**을 선택합니다. 그런 다음, VPN 프로필을 구성합니다. 자세한 내용은 [VPN 설정 구성 방법](vpn-settings-configure.md) 및 [Android 디바이스에 대한 Intune VPN 설정](vpn-settings-android.md)을 참조하세요.

VPN 프로필을 만들 때 지정하는 **연결 이름** 값을 적어 두세요. 다음 단계에서 이 이름이 필요합니다. 예를 들면 **MyAppVpnProfile**입니다.

## <a name="step-2-create-a-custom-configuration-policy"></a>2단계: 사용자 지정 구성 정책 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 사용자 지정 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **전체 회사에 대한 사용자 지정 OMA-URI Android VPN 프로필**이 적절한 프로필 이름일 수 있습니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Android**를 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택합니다.

4. **설정** > **구성**을 선택합니다.
5. **사용자 지정 OMA-URI 설정** 창에서 **추가**를 선택합니다.
    - **이름**: 설정의 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **OMA URI** `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`를 입력합니다. 여기서 *Name*은 1단계에서 적어 둔 연결 이름입니다. 이 예제에서 문자열은 `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`입니다.
    - **데이터 형식**: **문자열**을 입력합니다.
    - **값**: 프로필에 연결할 패키지가 세미콜론으로 구분된 목록을 입력합니다. 예를 들어 Excel 및 Google Chrome 브라우저에서 VPN 연결을 사용하려면 `com.microsoft.office.excel;com.android.chrome`과 같이 입력합니다.

![Android 앱별 VPN 사용자 지정 정책의 예](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>앱 목록을 블랙리스트 또는 허용 목록으로 설정(옵션)

*블랙리스트* 값을 사용하여 VPN 연결을 사용**할 수 없는** 앱 목록을 입력할 수 있습니다. 다른 모든 앱은 VPN을 통해 연결됩니다. 또는 **허용 목록** 값을 사용하여 VPN 연결을 사용*할 수 있는* 앱 목록을 입력합니다. 목록에 없는 앱은 VPN을 통해 연결되지 않습니다.

1. **사용자 지정 OMA-URI 설정** 창에서 **추가**를 선택합니다.
2. 설정 이름을 입력합니다.
3. **OMA-URI**에서 `./Vendor/MSFT/VPN/Profile/*Name*/Mode`를 입력합니다. 여기서 *Name*은 1단계에서 적어 둔 VPN 프로필 이름입니다. 이 예제에서 문자열은 `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`입니다.
4. **데이터 형식**에 **문자열**을 입력합니다.
5. **값**에 **블랙리스트** 또는 **허용 목록**을 입력합니다.

## <a name="step-3-assign-both-policies"></a>3단계: 두 정책 모두 할당

필요한 사용자 또는 디바이스에 [두 디바이스 프로필을 모두 할당](device-profile-assign.md)합니다.
