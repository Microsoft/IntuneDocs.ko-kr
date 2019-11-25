---
title: Microsoft Intune에서 iOS 디바이스용 앱당 VPN 설정 - Azure | Microsoft Docs
description: 필수 조건을 참조하고 VPN(가상 프라이빗 네트워크) 사용자에 대한 그룹을 만들고 SCEP 인증서 프로필을 추가하고 앱당 VPN 프로필을 구성하고 일부 앱을 iOS 디바이스의 Microsoft Intune에서 VPN 프로필을 할당합니다. 또한 디바이스에서 VPN 연결을 확인하기 위한 단계를 나열합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36039334f7e93b66735e10d0ac2c5d80602e2b83
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059867"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-ios-devices-in-intune"></a>Intune에서 iOS 디바이스용 앱당 VPN(가상 프라이빗 네트워크) 설정

Microsoft Intune에서 앱에 할당된 VPN(가상 프라이빗 네트워크)을 만들고 사용할 수 있습니다. 이 기능은 "앱당 VPN" 이라고 합니다. Intune에서 관리되는 디바이스에서 VPN을 사용할 수 있는 관리 앱을 선택합니다. 앱당 VPN을 사용하는 경우 최종 사용자는 VPN을 통해 자동으로 연결하고 문서 등의 조직 리소스에 액세스합니다.

이 기능은 다음에 적용됩니다.

- iOS 9 이상

VPN이 앱당 VPN을 지원하는지 확인하려면 VPN 공급 기업의 설명서를 확인합니다.

이 문서에서는 앱당 VPN 프로필을 만들고 앱에 이 프로필을 할당하는 방법을 보여 줍니다. 이러한 단계를 사용하여 최종 사용자에 대한 원활한 앱당 VPN 환경을 만들 수 있습니다. 앱당 VPN을 지원하는 대부분의 VPN의 경우 사용자는 앱을 열면 자동으로 VPN에 연결됩니다.

일부 VPN은 앱당 VPN을 통해 사용자 이름 및 암호 인증을 허용합니다. 즉, 사용자는 VPN에 연결하려면 사용자 이름 및 암호를 입력해야 합니다.

## <a name="per-app-vpn-with-zscaler"></a>Zscaler를 사용한 앱당 VPN

인증을 위해 ZPA(Zscaler Private Access)는 Azure AD(Azure Active Directory)와 통합됩니다. ZPA를 사용하는 경우 [신뢰할 수 있는 인증서](#create-a-trusted-certificate-profile) 또는 [SCEP 또는 PKCS 인증서](#create-a-scep-or-pkcs-certificate-profile) 프로필(이 문서에서 설명됨)이 필요하지 않습니다. Zscaler에 대해 앱당 VPN 프로필을 설정한 경우 연결된 앱 중 하나를 열면 ZPA에 자동으로 연결되지 않습니다. 대신, 사용자는 먼저 Zscaler 앱에 로그인해야 합니다. 그러면 원격 액세스가 연결된 앱으로 제한됩니다.

## <a name="prerequisites-for-per-app-vpn"></a>앱당 VPN의 필수 조건

> [!IMPORTANT]
> VPN 공급업체에는 특정 하드웨어 또는 라이선스와 같이 앱당 VPN에 대한 다른 요구 사항이 있을 수 있습니다. Intune에서 앱별 VPN을 설정하기 전에 먼저 관련 설명서를 확인하고 해당 필수 구성 요소를 충족해야 합니다.

해당 ID를 증명하기 위해 디바이스의 프롬프트 없이 동의해야 하는 인증서가 VPN 서버에 표시됩니다. 인증서의 자동 승인을 확인하려면 CA(인증 기관)에서 발급된 VPN 서버의 루트 인증서가 포함된 신뢰할 수 있는 인증서 프로필을 만듭니다. 

### <a name="export-the-certificate-and-add-the-ca"></a>인증서 내보내기 및 CA 추가

1. VPN 서버에서 관리 콘솔을 엽니다.
2. VPN 서버에서 인증서 기반 인증을 사용하는지 확인합니다. 
3. 신뢰할 수 있는 루트 인증서 파일을 내보냅니다. 해당 파일은 .cer 확장명이며 신뢰할 수 있는 인증서 프로필을 만들 때 추가됩니다.
4. 인증을 위해 인증서를 발급한 CA의 이름을 VPN 서버에 추가합니다.

    해당 디바이스에서 제공된 CA가 VPN 서버의 신뢰할 수 있는 CA 목록에 있는 CA와 일치하는 경우 VPN 서버는 성공적으로 디바이스를 인증합니다.

## <a name="create-a-group-for-your-vpn-users"></a>VPN 사용자 그룹 만들기

앱당 VPN을 사용하는 사용자나 디바이스의 경우 Azure AD(Azure Active Directory)에서 기존 그룹을 만들거나 선택합니다. 새 그룹을 만들려면 [사용자 및 디바이스를 구성하기 위한 그룹 추가](../fundamentals/groups-add.md)를 참조하세요.

## <a name="create-a-trusted-certificate-profile"></a>신뢰할 수 있는 인증서 프로필 만들기

Intune에서 만든 프로필에 CA에서 발급한 VPN 서버의 루트 인증서를 가져옵니다. 신뢰할 수 있는 인증서 프로필은 iOS 디바이스가 VPN 서버에서 제공한 CA를 자동으로 신뢰하도록 합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.
    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **전체 회사에 대한 iOS 신뢰할 수 있는 인증서 VPN 프로필**이 적절한 프로필 이름일 수 있습니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **iOS**를 선택합니다.
    - **프로필 유형**: **신뢰할 수 있는 인증서**를 선택합니다.
4. 폴더 아이콘을 선택하고 VPN 관리 콘솔에서 내보낸 VPN 인증서(.cer 파일)로 이동합니다. 
5. **확인** > **만들기**를 선택합니다.

    ![Microsoft Intune에서 iOS 디바이스에 대한 신뢰할 수 있는 인증서 프로필 만들기](./media/vpn-setting-configure-per-app/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>SCEP 또는 PKCS 인증서 프로필 만들기

신뢰할 수 있는 루트 인증서 프로필을 사용하면 디바이스가 자동으로 VPN 서버를 신뢰할 수 있습니다. SCEP 또는 PKCS 인증서를 사용하면 iOS VPN 클라이언트에서 VPN 서버에 자격 증명을 제공합니다. 인증서를 사용하면 디바이스에서 사용자 이름 및 암호를 확인하는 메시지 없이 자동으로 인증할 수 있습니다. 

클라이언트 인증 인증서를 구성하고 할당하려면 다음 문서 중 하나를 참조하세요.

- [Intune을 사용하여 SCEP를 지원하도록 인프라 구성](../protect/certificates-scep-configure.md)
- [Intune을 사용하여 PKCS 인증서 구성 및 관리](../protect/certficates-pfx-configure.md)

클라이언트 인증용 인증서를 구성해야 합니다. SCEP 인증서 프로필에서 이 인증서를 직접 설정할 수 있습니다(**확장 키 사용** 목록 > **클라이언트 인증**). PKCS의 경우 CA(인증 기관)의 인증서 템플릿에서 클라이언트 인증을 설정합니다.

![주체 이름 형식, 키 사용, 확장 키 사용 등을 포함한 Microsoft Intune에서 SCEP 인증서 프로필 만들기](./media/vpn-setting-configure-per-app/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>앱당 VPN 프로필 만들기

VPN 프로필에서는 클라이언트 자격 증명이 포함된 SCEP 또는 PKCS 인증서, VPN에 대한 연결 정보 및 앱당 VPN 플래그를 포함하여 iOS 애플리케이션에서 사용될 앱당 VPN 기능을 사용하도록 설정합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **구성 프로필** > **프로필 만들기**를 선택합니다.
2. 다음 속성을 입력합니다.
    - **이름**: 사용자 지정 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **전체 회사에 대한 iOS 앱별 VPN 프로필**이 적절한 프로필 이름일 수 있습니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **iOS**를 선택합니다.
    - **프로필 유형**: **VPN**을 선택합니다.
3. **연결 형식**에서 VPN 클라이언트 앱을 선택합니다.
4. **기본 VPN**을 선택합니다. [iOS VPN 설정](vpn-settings-ios.md)에서 모든 설정을 나열하고 설명합니다. 앱당 VPN을 사용하는 경우 다음 속성이 나열된 것처럼 설정해야 합니다.

    - **인증 방법**: **인증서**를 선택합니다. 
    - **인증 인증서**: 기존 SCEP 또는 PKCS 인증서 > **확인**을 선택합니다.      
    - **분할 터널링**: **사용 안 함**을 선택하여 VPN 연결이 활성 상태일 때 모든 트래픽이 VPN 터널을 사용하도록 강제합니다. 

      ![Microsoft Intune에서 앱별 VPN 프로필에 연결, IP 주소 또는 FQDN, 인증 방법 및 분할 터널링 입력](./media/vpn-setting-configure-per-app/vpn-per-app-create-vpn-profile.png)

    기타 설정에 대한 자세한 내용은 [iOS VPN 설정](vpn-settings-ios.md)을 참조하세요.

5. **자동 VPN** > **자동 VPN 유형** > **앱 별 VPN** 선택

    ![Intune의 iOS 디바이스에서 자동 VPN을 앱당 VPN으로 설정](./media/vpn-setting-configure-per-app/vpn-per-app-automatic.png)

6. **확인** > **확인** > **만들기**를 선택합니다.

## <a name="associate-an-app-with-the-vpn-profile"></a>VPN 프로필과 앱 연결

VPN 프로필을 추가한 후에 앱 및 Azure AD 그룹을 프로필에 연결합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **앱** > **모든 앱**을 선택합니다.
2. 목록 > **할당** > **추가 그룹**에서 앱을 선택합니다.
3. **할당 유형**에서 **필수** 또는 **등록된 디바이스에 사용 가능**을 선택합니다.
4. **포함된 그룹** > **포함할 그룹 선택** > 이 문서에서 [사용자가 만든 그룹](#create-a-group-for-your-vpn-users)> **선택**을 선택합니다.
5. **VPN**의 이 문서에서 [사용자가 만든](#create-a-per-app-vpn-profile) 앱당 VPN 프로필을 선택합니다.

    ![Microsoft Intune에서 앱당 VPN 프로필에 앱 할당](./media/vpn-setting-configure-per-app/vpn-per-app-app-to-vpn.png)

6. **확인** > **저장**을 선택합니다.

다음과 같은 모든 조건에서는 다음번 디바이스 체크인 시에 앱과 프로필 사이의 연결이 제거됩니다.

- 앱이 필수 설치 의도와 함께 대상으로 지정되었습니다.
- 프로필과 앱이 모두 동일한 그룹으로 대상 지정되었습니다.
- 사용자가 앱 할당에서 앱당 VPN 구성을 제거했습니다.

다음과 같은 모든 조건에서는 사용자가 회사 포털에서 재설치를 요청하기 전까지 앱과 프로필 사이의 연결이 유지됩니다.

- 앱이 사용 가능한 설치 의도와 함께 대상으로 지정되었습니다.
- 프로필과 앱이 모두 동일한 그룹으로 대상 지정되었습니다.
- 최종 사용자가 회사 포털에서 앱 설치를 요청한 결과로 앱과 프로필이 디바이스에 설치되었습니다.
- 사용자가 앱 할당에서 앱당 VPN 구성을 제거하거나 변경했습니다.

## <a name="verify-the-connection-on-the-ios-device"></a>iOS 디바이스에 대한 연결 확인

앱당 VPN을 설정하고 디바이스와 연결한 경우 디바이스에서 연결이 작동하는지 확인합니다.

### <a name="before-you-attempt-to-connect"></a>연결하려고 하기 전에

- 위에 언급한 모든 정책이 동일한 그룹에 배포되는지 확인합니다. 그렇지 않는 경우 앱당 VPN 환경이 작동하지 않습니다.
- Pulse Secure VPN 앱 또는 사용자 지정 VPN 클라이언트 앱을 사용하는 경우 앱 계층 또는 패킷 계층 터널링을 사용하도록 선택할 수 있습니다. **ProviderType** 값은 앱 계층 터널링의 경우 **app-proxy**로 설정하고, 패킷 계층 터널링의 경우 **packet-tunnel**로 설정합니다. 올바른 값을 사용하고 있는지 확인하려면 VPN 공급 기업의 설명서를 확인합니다.

### <a name="connect-using-the-per-app-vpn"></a>앱당 VPN을 사용하여 연결

VPN을 선택하거나 자격 증명을 입력하지 않고 연결하여 제로 터치 환경을 확인합니다. 제로 터치 환경은 다음을 의미합니다.

- 디바이스에는 VPN 서버를 신뢰하라는 메시지가 표시되지 않습니다. 즉, 사용자에게는 **동적 신뢰** 대화 상자가 표시되지 않습니다.
- 사용자는 자격 증명을 입력할 필요가 없습니다.
- 사용자가 연결된 앱 중 하나를 열면 사용자의 디바이스가 VPN에 연결됩니다.

## <a name="next-steps"></a>다음 단계

- iOS 설정을 검토하려면 [Microsoft Intune의 iOS 디바이스에 대한 VPN 설정](vpn-settings-ios.md)을 참조하세요.
- VPN 설정과 Intune에 대해 자세히 알아보려면 [Microsoft Intune에서 VPN 설정 구성](vpn-settings-configure.md)을 참조하세요.
