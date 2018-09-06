---
title: Microsoft Intune에서 iOS 장치용 앱당 VPN 설정 - Azure | Microsoft Docs
description: 필수 조건을 참조하고 VPN(가상 사설망) 사용자에 대한 그룹을 만들고 SCEP 인증서 프로필을 추가하고 앱당 VPN 프로필을 구성하고 일부 앱을 iOS 장치의 Microsoft Intune에서 VPN 프로필을 할당합니다. 또한 장치에서 VPN 연결을 확인하기 위한 단계를 나열합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f4746e2f20926c102717214304711cc9883597b8
ms.sourcegitcommit: 1e349bcfd562f34866108e566e5b5062717e0112
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2018
ms.locfileid: "40252453"
---
# <a name="set-up-per-app-virtual-private-network-vpn-in-intune-for-ios-devices"></a>iOS 장치용 Intune에서 앱당 VPN 설정

Intune이 관리하는 iOS 장치에서 관리되는 앱이 VPN을 사용할 수 있도록 지정합니다. Intune에서 앱당 VPN을 만들면 최종 사용자가 회사 문서에 액세스할 때 VPN을 통해 자동으로 연결합니다.

현재 앱당 VPN을 사용할 수 있는 공급자는 다음과 같습니다.

 - Check Point Remote Access VPN
 - Cisco AnyConnect
 - Citrix
 - F5
 - Pulse Connect Secure
 - SonicWall
 - Palo Alto Networks GlobalProtect

## <a name="prerequisites-for-per-app-vpn"></a>앱당 VPN의 필수 조건

> [!IMPORTANT]
> VPN 공급업체에는 특정 하드웨어 또는 라이선스와 같이 앱별 VPN에 대한 다른 특정 요구 사항이 있을 수 있습니다. Intune에서 앱별 VPN을 설정하기 전에 먼저 관련 설명서를 확인하고 해당 필수 구성 요소를 충족해야 합니다.

해당 ID를 증명하기 위해 장치의 프롬프트 없이 동의해야 하는 인증서가 VPN 서버에 표시됩니다. 인증서의 자동 승인을 보장하려면 CA(인증 기관)에서 발급한 VPN 서버의 루트 인증서가 포함된 신뢰할 수 있는 인증서 프로필을 만듭니다. 

인증서를 내보내고 CA를 추가합니다.

1. VPN 서버에서 관리 콘솔을 엽니다.
2. VPN 서버에서 인증서 기반 인증을 사용하는지 확인합니다. 
3. 신뢰할 수 있는 루트 인증서 파일을 내보냅니다. 해당 파일은 .cer 확장명이며 신뢰할 수 있는 인증서 프로필을 만들 때 추가됩니다.
4. 인증을 위해 인증서를 발급한 CA의 이름을 VPN 서버에 추가합니다.
    해당 장치에서 제공한 CA가 VPN 서버의 신뢰할 수 있는 CA 목록에 있는 CA와 일치하는 경우 VPN 서버는 성공적으로 장치를 인증합니다.

## <a name="create-a-group-for-your-vpn-users"></a>VPN 사용자 그룹 만들기

Azure AD(Azure Active Directory)에서 기존 그룹을 만들거나 선택하여 앱당 VPN에 액세스할 수 있는 멤버를 포함합니다.

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
2. **그룹**을 선택하고 **새 그룹**을 클릭합니다.
3. 그룹에 대한 **그룹 형식**을 선택합니다. 
3. 그룹의 **그룹 이름**을 입력합니다. 
4. 그룹의 **그룹 설명**을 입력합니다. 
5. **멤버 자격 유형**에 **할당됨**을 선택합니다.
7. **멤버** 창에서 이름 또는 이메일 주소로 VPN 사용자를 검색합니다.
8. 각 사용자를 선택하고 **선택**을 클릭합니다.
9. **만들기**를 클릭합니다.

## <a name="create-a-trusted-certificate-profile"></a>신뢰할 수 있는 인증서 프로필 만들기

Intune에서 만든 프로필에 CA에서 발급한 VPN 서버의 루트 인증서를 가져옵니다. 신뢰할 수 있는 인증서 프로필은 iOS 장치가 VPN 서버에서 제공한 CA를 자동으로 신뢰하도록 합니다.

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
2. **장치 구성**을 선택하고 **프로필**을 클릭합니다.
3. **프로필 만들기**를 클릭합니다. **프로필 만들기**에서:
    1. **이름**을 입력합니다.
    2. **설명**을 입력합니다.
    3. **플랫폼**으로 **iOS**를 선택합니다.
    4. **프로필 형식**으로 **신뢰할 수 있는 인증서**를 선택합니다.
4. 폴더 아이콘을 클릭하고 VPN 관리 콘솔에서 내보낸 VPN 인증서(.cer 파일)로 이동합니다. **확인**을 클릭합니다.
5. **만들기**를 클릭합니다.

    ![신뢰할 수 있는 인증서 프로필 만들기](./media/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-certificate-profile"></a>SCEP 인증서 프로필 만들기

신뢰할 수 있는 루트 인증서 프로필을 사용하면 iOS가 자동으로 VPN 서버를 신뢰할 수 있습니다. SCEP 인증서를 사용하면 iOS VPN 클라이언트에서 VPN 서버에 자격 증명을 제공합니다. 인증서를 사용하면 장치에서 사용자 이름 및 암호의 iOS 장치 사용자를 확인하는 메시지 없이 자동으로 인증할 수 있습니다. 

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
2. **장치 구성**을 선택하고 **프로필**을 클릭합니다.
3. **프로필 만들기**를 클릭합니다. **프로필 만들기**에서:
    1. **이름**을 입력합니다.
    2. **설명**을 입력합니다.
    3. **플랫폼**으로 **iOS**를 선택합니다.
    4. **프로필 형식**으로 **SCEP 인증서**를 선택합니다.
4. **연도**를 선택하고 **인증서 유효 기간이**으로 `2`를 입력합니다.
5. **주체 이름 형식**으로 **공통 이름**을 선택합니다.
6. **주체 대체 이름**으로 **UPN(사용자 계정 이름)** 을 선택합니다.
7. **키 사용**에서 **디지털 서명** 및 **키 암호화**를 선택합니다.
8. **키 크기(비트)** 에서 **2048**을 선택합니다.
9. 루트 인증서를 클릭하고 SCEP 인증서를 선택합니다. **확인**을 클릭합니다.
10. **확장된 키 사용**의 **이름**에 `Client Authentication`을 입력합니다.
11. **개체 식별자**에 `1.3.6.1.5.5.7.3.2`를 입력합니다.
12. **추가**를 클릭합니다.
13. ***서버 URL***을 입력하고 **추가**를 클릭합니다.
14. **확인**을 클릭합니다.
15. **만들기**를 클릭합니다.

    ![SCEP 인증서 프로필 만들기](./media/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>앱당 VPN 프로필 만들기

VPN 프로필에는 클라이언트 자격 증명을 포함한 SCEP 인증서, VPN에 대한 연결 정보 및 앱당 VPN 플래그를 포함하여 iOS 응용 프로그램에서 사용할 앱당 VPN 기능을 사용하도록 설정합니다.

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
2. **장치 구성**을 선택하고 **프로필**을 클릭합니다.
3. **프로필 만들기**를 클릭합니다. **프로필 만들기**에서:
    1. **이름**을 입력합니다.
    2. **설명**을 입력합니다.
    3. **플랫폼**으로 **iOS**를 선택합니다.
    4. **프로필 형식**에서 **VPN**을 선택합니다.
4. **기본 VPN**을 선택합니다. **기본 VPN**에서:
    1. **연결 이름**을 입력합니다.
    2. **서버 IP 주소 또는 FQDN**을 입력합니다.
    3. **인증 방법**으로 **인증서**를 선택합니다.
    4. **인증 인증서** 아래에서 SCEP 인증서를 선택하고 **확인**을 클릭합니다.
    5. **연결 형식**으로 VPN을 선택합니다.
    6. 필요한 경우 VPN의 특성을 구성합니다.
    7. **분할 터널링 사용 안 함**에 선택합니다.
5. **자동 VPN**을 클릭합니다. **자동 VPN**에서:
    1. **자동 VPN의 유형**에서 **앱당 VPN**을 선택합니다.
    2. VPN의 URL을 입력하고 **추가**를 클릭합니다.
    3. **확인**을 클릭합니다.
6. **확인**을 클릭합니다.
7. **만들기**를 클릭합니다.

    ![앱당 VPN 프로필 만들기](./media/vpn-per-app-create-vpn-profile.png)


## <a name="associate-an-app-with-the-vpn-profile"></a>VPN 프로필과 앱 연결

VPN 프로필을 추가한 후에 앱 및 Azure AD 그룹을 프로필에 연결합니다.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **모바일 앱**을 선택합니다.
4. **앱**을 클릭합니다.
5. 앱 목록에서 앱을 선택합니다.
6. **할당**을 클릭합니다.
7. **작업 추가**를 클릭합니다.
8. **그룹 추가** 창에서 **할당 형식**으로 **필수**를 선택합니다.
9. 앞에서 정의한 그룹을 선택하고 **이 앱을 필수로 설정**을 선택합니다.
10. **VPN**에서 VPN 정의를 선택합니다.
 
    > [!NOTE]  
    > 경우에 따라 VPN 정의가 값을 검색하는 데 최대 1분이 걸립니다. **저장**을 클릭하기 전에 3~5분을 기다립니다.

11. **확인**을 클릭하고 **저장**을 클릭합니다.

    ![VPN과 앱 연결](./media/vpn-per-app-app-to-vpn.png)

다음과 같은 조건에서는 다음번 장치 체크인 시에 앱과 프로필 사이의 연결이 제거됩니다.
- 앱이 필수 설치 의도와 함께 대상으로 지정되었습니다.
- 프로필과 앱이 모두 동일한 그룹으로 대상 지정되었습니다.
- 사용자가 앱 할당에서 앱당 VPN 구성을 제거했습니다.

다음과 같은 조건에서는 최종 사용자가 회사 포털에서 재설치를 요청하기 전까지 앱과 프로필 사이의 연결이 계속 유지됩니다.
- 앱이 사용 가능한 설치 의도와 함께 대상으로 지정되었습니다.
- 프로필과 앱이 모두 동일한 그룹으로 대상 지정되었습니다.
- 최종 사용자가 회사 포털에서 앱 설치를 요청한 결과, 앱과 프로필이 장치에 설치되었습니다.
- 사용자가 앱 할당에서 앱당 VPN 구성을 제거했습니다.

## <a name="verify-the-connection-on-the-ios-device"></a>iOS 장치에 대한 연결 확인

앱당 VPN을 설정하고 장치와 연결한 경우 장치에서 연결이 작동하는지 확인합니다.

### <a name="before-you-attempt-to-connect"></a>연결하려고 하기 전에

 - iOS 9 이상을 실행하고 있는지 확인합니다.
 - 위에 언급한 *모든* 정책이 동일한 사용자 그룹에 배포되도록 합니다. 실패하는 경우 앱당 VPN 환경이 가장 확실하게 중단됩니다.  
 - 지원되는 타사 VPN 앱이 설치되었는지 확인합니다. 지원되는 VPN 앱은 다음과 같습니다.
    - Check Point Capsule Connect
    - Cisco AnyConnect
    - Citrix VPN
    - F5 Access
    - Pulse Secure
    - SonicWall Mobile Connect

### <a name="connect-using-the-per-app-vpn"></a>앱당 VPN을 사용하여 연결

VPN을 선택하거나 자격 증명을 입력하지 않고 연결하여 제로 터치 환경을 확인합니다. 제로 터치 환경은 다음을 의미합니다.

 - 장치에서는 VPN 서버를 신뢰하라는 메시지를 표시하지 않습니다. 즉, **동적 신뢰** 대화 상자가 표시됩니다.
 - 자격 증명을 입력할 필요는 없습니다.
 - 연결 단추를 누른 후에 VPN에 연결됩니다.

iOS 장치에 대한 연결을 확인합니다.

1. VPN 앱을 누릅니다.
2. **연결**을 누릅니다.  
VPN은 추가 프롬프트 없이 성공적으로 연결합니다.

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>다음 단계

- iOS 설정을 검토하려면 [Microsoft Intune의 iOS 장치에 대한 VPN 설정](vpn-settings-ios.md)을 참조하세요.
-  VPN 설정과 Intune에 대해 자세히 알아보려면 [Microsoft Intune에서 VPN 설정을 구성하는 방법](vpn-settings-configure.md)을 참조하세요.
