---
title: Microsoft Intune-Azure를 사용해 Windows Holographic 디바이스 사용 | Microsoft Docs
description: Microsoft Intune을 사용하여 회사 포털 구성, 준수 정책 만들기, OMA-URI 설정 사용자 지정, 앱 배포, 디바이스를 그룹으로 분류, 프로필 만들기, 디바이스 제한, 소프트웨어 업데이트 사용하도록 설정, 사용 약관 설정, VPN 및 Wi-Fi 설정 구성 및 Hello for Business 사용을 포함하여 Windows Holographic for Business 및 HoloLens를 실행하는 디바이스에서 다른 작업을 관리 및 완료할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e50784529bb3128b08aa36859ca003f7c6f7691
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727794"
---
# <a name="manage-and-use-different-device-management-features-on-windows-holographic-and-hololens-devices-with-intune"></a>Intune을 사용하여 Windows Holographic 및 HoloLens 디바이스의 다양한 디바이스 관리 기능 관리 및 사용

Microsoft Intune에는 [Microsoft HoloLens](https://docs.microsoft.com/hololens/) 같은 Windows Holographic for Business를 실행하는 디바이스를 관리하는 데 도움이 되는 여러 기능이 포함되어 있습니다. Intune을 사용하여 디바이스가 조직의 규칙을 준수하는지 확인하고 VPN 또는 WiFi 프로필을 추가하여 디바이스를 사용자 지정할 수 있습니다. 다른 주요 기능은 디바이스를 키오스크로 사용하고 특정 앱 또는 특정 앱 집합을 실행하는 것입니다.

이 문서의 작업은 Windows Holographic for Business(소프트웨어 업데이트 포함)를 실행하고 비즈니스용 Windows Hello를 사용하는 디바이스를 관리, 사용자 지정 및 보호하는 데 도움이 됩니다.

Intune에서 Windows Holographic 디바이스를 사용하려면 버전 업그레이드 프로필을 만드세요. 이 업그레이트 프로필은 Windows Holographic 디바이스를 Windows Holographic for Business로 업그레이드합니다. Microsoft HoloLens의 경우 Commercial Suite를 구입하여 업그레이드에 필요한 라이선스를 얻을 수 있습니다. 자세한 내용은 [Windows Holographic을 실행하는 디바이스를 Windows Holographic for Business로 업그레이드](../configuration/holographic-upgrade.md)를 참조하세요.

## <a name="azure-active-directory"></a>Azure Active Directory

Azure AD(Active Directory)는 Windows Holographic for Business를 실행하는 디바이스의 관리 및 제어를 도와주는 유용한 리소스입니다. Intune 및 Azure AD를 사용하여 다음을 수행할 수 있습니다. 

- **[Azure Active Directory에 디바이스 조인](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)** : Azure AD(Active Directory)에서 Windows Holographic for Business를 실행하는 디바이스를 포함하여 회사 소유의 Windows 10 디바이스를 추가할 수 있습니다. 이 기능은 Azure AD가 디바이스를 제어하도록 허용합니다. 이렇게 하면 사용자는 보안 및 규정 표준을 충족하는 디바이스에서 회사 리소스에 액세스할 수 있습니다.

  자세한 내용은 [Azure AD의 디바이스 관리](https://docs.microsoft.com/azure/active-directory/devices/overview)에 설명되어 있습니다.

- **[Windows 디바이스에 대한 대량 등록](../enrollment/windows-bulk-enroll.md)** : 여러 새로운 Windows 디바이스를 Azure AD(Active Directory) 및 Intune에 조인할 수 있습니다. 이 기능을 대량 등록이라고 하며, 프로비전 패키지를 사용합니다. 이러한 패키지는 Windows Holographic for Business를 실행하는 디바이스를 Azure AD 테넌트에 조인하고, Intune에 등록합니다.

## <a name="company-portal"></a>회사 포털
**[회사 포털 앱 구성](../apps/company-portal-app.md)**

Intune은 사용자가 회사 데이터에 액세스하고, 디바이스를 등록하고, 앱을 설치하고, IT 부서에 문의하는 회사 포털 앱을 제공합니다. Windows Holographic for Business를 실행하는 디바이스에 대한 회사 포털 앱을 사용자 지정할 수 있습니다.

회사 포털 앱을 사용하여 다음 작업을 수행할 수도 있습니다.

- 설정 앱 또는 회사 포털 앱을 사용하여 [Intune에서 디바이스 제거](/intune-user-help/unenroll-your-device-from-intune-windows)
- [디바이스 이름 바꾸기](/intune-user-help/rename-your-device-cpapp)
- 디바이스에 [앱 설치](/intune-user-help/install-apps-cpapp-windows)
- 설정 앱 또는 회사 포털 앱에서 [수동으로 디바이스 동기화](/intune-user-help/sync-your-device-manually-windows)

## <a name="compliance-policy"></a>준수 정책
**[디바이스 준수 정책 만들기](../protect/compliance-policy-create-windows.md)**

준수 정책은 디바이스가 준수하려면 반드시 충족해야 할 규칙과 설정입니다. 비준수 디바이스용 회사 리소스에 대한 액세스를 차단하려면 조건부 액세스를 통해 이러한 정책을 사용합니다. Intune에서 Windows Holographic for Business을 실행하는 디바이스에 대한 액세스를 허용하거나 차단하기 위한 준수 정책을 만듭니다. 예를 들어 Bitlocker를 사용하도록 설정할 것을 요구하는 정책을 만들 수 있습니다.

**[준수 정책 시작](../protect/device-compliance-get-started.md)** 을 참조합니다.

## <a name="deploy-and-manage-apps"></a>앱 배포 및 관리
**[Intune에 앱 추가](../apps/apps-add.md)**

Intune을 사용하여 Windows Holographic for Business를 실행하는 디바이스에 앱을 추가할 수 있습니다. 다음을 포함하여 앱을 배포하는 방법은 많습니다.

- [Microsoft Store 앱 추가](../apps/store-apps-windows.md)
- [만든 앱 추가](../apps/lob-apps-windows.md)
- [그룹에 앱 할당](../apps/apps-deploy.md)

Microsoft Intune은 Windows Holographic for Business를 실행하는 Microsoft HoloLens 디바이스에 유니버설 Windows 앱을 배포할 수 있습니다. Intune Azure Portal에서 앱 패키지를 직접 업로드하거나, 비즈니스용 Microsoft Store에서 배포할 수 있습니다. 관련 영역에 대한 자세한 내용은 다음 문서를 참조하세요.
- Intune Azure Portal을 사용하여 LOB(기간 업무) 앱을 배포하려면 [Microsoft Intune에 Windows 기간 업무 앱을 추가하는 방법](../apps/lob-apps-windows.md)을 참조하세요.

    > [!NOTE]
    > Intune은 최대 패키지 크기 8GB를 허용합니다. 이 패키지 크기는 Intune에 업로드된 LOB 앱에만 사용 가능합니다.

- 비즈니스용 Microsoft Store를 사용하여 앱을 배포하려면 [Microsoft Intune을 사용하여 비즈니스용 Microsoft Store에서 구입한 앱을 관리하는 방법](../apps/windows-store-for-business.md)을 참조하세요. 
- Microsoft Intune을 사용하는 앱 관리에 대한 자세한 내용은 [Microsoft Intune의 앱 관리란?](../apps/app-management.md)을 참조하세요.
- Microsoft HoloLens용 앱 개발에 대한 자세한 내용은 [Microsoft HoloLens용 혼합 현실 앱](https://www.microsoft.com/hololens/apps)을 참조하세요. 

> [!NOTE]
> Windows 10 Holographic for Business 1607을 실행하는 HoloLens 디바이스는 비즈니스용 Microsoft Store에서 구입한, 온라인 사용이 허가된 앱을 지원하지 않습니다. 자세한 내용은 [HoloLens에 앱 설치](https://docs.microsoft.com/hololens/hololens-install-apps)를 참조하세요.

## <a name="device-actions"></a>디바이스 작업
Intune에는 IT 관리자가 디바이스에서 로컬로 또는 Azure Portal에서 Intune을 사용하여 원격으로 다른 작업을 수행할 수 있는 몇 가지 기본 제공 작업이 있습니다. 또한 사용자가 Intune 회사 포털에서 Intune에 등록된 개인적으로 소유한 디바이스로 원격 명령을 실행할 수 있습니다.

Windows Holographic for Business를 실행하는 디바이스를 사용할 때 다음 작업을 사용할 수 있습니다. 

- **[초기화](../remote-actions/devices-wipe.md#wipe)** : **초기화** 작업은 Intune에서 디바이스를 제거하고 공장 기본값으로 복원합니다. 이 작업은 새 사용자에게 디바이스를 제공하기 전에 또는 디바이스를 분실하거나 도난당했을 때 사용합니다.

- **[사용 중지](../remote-actions/devices-wipe.md#retire)** : **사용 중지** 작업은 Intune에서 디바이스를 제거합니다. 관리되는 앱 데이터, 설정 및 Intune에서 할당된 이메일 프로필도 제거합니다. 사용자의 개인 데이터는 디바이스에 유지됩니다.

- **[디바이스를 동기화하여 최신 정책과 작업 가져오기](../remote-actions/device-sync.md)** : **동기화** 작업은 강제로 디바이스가 Intune을 사용하여 즉시 체크 인하도록 합니다. 디바이스가 체크 인하면 디바이스에 할당된 보류 중인 작업 또는 정책을 즉시 받게 됩니다. 이 기능을 통해 예약된 다음 체크 인을 기다리지 않고 할당한 정책의 유효성을 검사하고 문제를 해결할 수 있습니다.

**[Microsoft Intune 디바이스 관리란?](../remote-actions/device-management.md)** 은 Azure Portal을 사용하여 디바이스를 관리하는 방법에 대한 유용한 리소스입니다. 

## <a name="device-categories-and-groups"></a>디바이스 범주 및 그룹
**[디바이스를 그룹으로 분류](../enrollment/device-group-mapping.md)**

판매, 회계, 인사 등의 만든 범주 기반 그룹에 디바이스를 자동으로 추가하려면 Intune을 사용하여 디바이스 범주를 만들 수 있습니다. 이를 통해 Windows Holographic for Business를 실행 중인 디바이스 관리를 더 쉽게 할 수 있습니다.

## <a name="device-configuration-profiles"></a>디바이스 구성 프로필 
**[구성 프로필 시작](../configuration/device-profiles.md) 및 [자신의 프로필 만들기](../configuration/device-profile-create.md)**

Intune은 조직 내의 다른 디바이스에서 사용하거나 사용하지 않게 할 수 있는 설정 및 기능을 포함합니다. 이러한 설정 및 기능은 프로필을 사용하여 관리됩니다. 예를 들어 Cortana를 사용하도록 설정하거나 Windows Holographic for Business를 실행하는 디바이스에서 Windows Defender Smart Screen을 사용하는 프로필을 만들 수 있습니다.

프로필에서 OMA URI를 사용하여 일부 설정을 사용자 지정하고 디바이스 제한을 만들고 VPN(가상 프라이빗 네트워크) 및 Wi-Fi를 구성할 수 있습니다.

### <a name="custom-device-settingsconfigurationcustom-settings-windows-holographicmd"></a>[사용자 지정 디바이스 설정](../configuration/custom-settings-windows-holographic.md)

OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 구성하려면 Intune에서 사용자 지정 프로필을 만들 수 있습니다. OMA-URI 설정을 사용하여 VPN을 사용하도록 설정하거나 Microsoft 업데이트에서 업데이트를 검사하는 등 Windows Holographic for Business의 다양한 기능을 제어합니다.

### <a name="configure-kiosk-modeconfigurationkiosk-settings-holographicmd"></a>[키오스크 모드 구성](../configuration/kiosk-settings-holographic.md)

Intune에서 사용할 수 있는 공유 또는 게스트 PC 기능을 사용하여 키오스크로 실행하도록 Windows Holographic for Business 디바이스를 구성할 수 있습니다. 이러한 디바이스는 하나의 앱(단일 앱 키오스크 모드)을 실행하거나 여러 앱(다중 앱 키오스크 모드)을 실행할 수 있습니다.

### <a name="device-restrictionsconfigurationdevice-restrictions-windows-holographicmd"></a>[디바이스 제한 사항](../configuration/device-restrictions-windows-holographic.md)

디바이스 제한을 사용하면 암호를 요구하고 [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps)에서 앱을 설치하고 Bluetooth를 사용하도록 설정하는 등 디바이스에서 다양한 설정과 기능을 제어할 수 있습니다. 이러한 제한 사항은 Intune 프로필에서 만듭니다. 이 프로필은 Windows Holographic for Business를 실행하는 여러 디바이스에 적용할 수 있습니다.

### <a name="configure-vpnconfigurationvpn-settings-configuremd"></a>[VPN 구성](../configuration/vpn-settings-configure.md)

VPN(가상 프라이빗 네트워크)을 사용하면 사용자가 회사 네트워크에 안전하게 원격으로 액세스할 수 있습니다. Intune에서 Windows Holographic for Business를 실행하는 디바이스에 대한 특정 설정을 포함하는 VPN 프로필을 만들 수 있습니다. 예를 들어 VPN 프로필을 만듦으로써 모든 Windows Holographic for Business 디바이스는 연결 유형으로 Citrix VPN를 사용할 수 있습니다.

### <a name="configure-wi-ficonfigurationwi-fi-settings-configuremd"></a>[Wi-Fi 구성](../configuration/wi-fi-settings-configure.md)

또한 Windows Holographic for Business 디바이스에 무선 네트워크 설정을 할당하는 Intune에서 Wi-Fi 프로필을 만들 수 있습니다. Wi-Fi 프로필을 할당하면 최종 사용자는 네트워크 구성 없이도 회사 네트워크 액세스 권한을 가져옵니다. 예를 들어 Windows Holographic for Business 디바이스 전용 Wi-Fi 네트워크를 만들 수 있습니다.

## <a name="shared-multi-user-devices"></a>다중 사용자 디바이스 공유
[공유 디바이스](../configuration/shared-user-device-settings-windows-holographic.md)

Microsoft HoloLens와 같이 Windows Holographic for Business를 실행하는 디바이스에는 여러 사용자가 있을 수 있습니다. Intune에는 이러한 공유 디바이스에서 로컬 스토리지 및 계정 관리를 사용하여 전원 관리와 같은 다양한 기능을 제어할 수 있는 설정이 포함됩니다. 또한 서로 다른 운영 체제를 사용하여 디바이스에 구성 프로필을 적용할 수 있습니다. 예를 들어 디바이스 그룹에는 동일한 그룹에서 RS2 및 RS3를 실행하는 디바이스가 있을 수 있습니다.

## <a name="software-updates"></a>소프트웨어 업데이트
**[소프트웨어 업데이트 관리](../protect/windows-update-for-business-configure.md)**

Intune에는 Windows 10 디바이스용 업데이트 링이라는 기능이 포함되어 있습니다. 이러한 업데이트 링은 업데이트를 설치하는 방법을 결정하는 설정 그룹을 포함합니다. 예를 들어 업데이트를 설치하기 위한 유지 관리 기간을 만들거나 업데이트가 설치된 후 다시 시작을 선택할 수 있습니다. 업데이트 링은 Windows Holographic for Business를 실행하는 여러 디바이스에 적용할 수 있습니다.

## <a name="terms-and-conditions"></a>사용 약관
**[사용자 액세스에 대한 회사의 사용 약관 설정](../enrollment/terms-and-conditions-create.md)**

사용자가 디바이스를 등록하고 이메일을 포함한 회사 앱에 액세스하기 전에 사용자가 회사의 사용 약관에 동의할 것을 요구할 수 있습니다. Intune에서 사용 약관이 회사 포털에 표시되는 방식을 정의하고 또한 이러한 약관을 Windows Holographic for Business를 실행하는 디바이스에 할당합니다.

## <a name="windows-hello-for-business"></a>비즈니스용 Windows Hello
**[비즈니스용 Windows Hello 사용](../protect/windows-hello.md)**

비즈니스용 Hello는 Azure Active Directory 계정을 사용하여 암호, 스마트 카드 또는 가상 스마트 카드를 대신하는 대체 로그인 방법입니다. 비즈니스용 Hello를 사용하면 Windows Holographic for Business 디바이스는 설정한 최소 길이의 PIN으로 로그인할 수 있습니다.
