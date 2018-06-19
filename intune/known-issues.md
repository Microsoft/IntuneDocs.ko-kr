---
title: Microsoft Intune - Azure의 알려진 문제 | Microsoft Docs
description: Microsoft Intune의 알려진 문제에 대해 알아봅니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f49b5050f4ce182699f0955bed6224309a4d7c7c
ms.sourcegitcommit: c1631ad8feba6c6fd03698ab20836b2e5d8a78d2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/12/2018
ms.locfileid: "34073838"
---
# <a name="known-issues-in-microsoft-intune"></a>Microsoft Intune의 알려진 문제


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클을 사용하여 Microsoft Intune의 알려진 문제를 파악할 수 있습니다.

여기에 나열되지 않은 버그를 보고하려면 [지원 요청을 시작](get-support.md)하세요.

Intune의 새로운 기능을 요청하려면 [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) 사이트에서 보고서를 제출하는 것이 좋습니다.

## <a name="migration"></a>마이그레이션

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Intune 레거시 PC 클라이언트 기능은 Silverlight 콘솔에서만 사용 가능합니다.

Azure Portal의 Intune에서 Windows 10을 관리하는 기능은 Windows MDM 등록을 통해 사용할 수 있습니다. 자세한 내용은 [Azure용 Intune 콘솔 및 레거시 Intune PC 클라이언트](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure)을 참조하세요.

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>마이그레이션 도중 Intune이 만든 그룹은 다른 Microsoft 제품의 기능에 영향을 줄 수 있습니다.

Intune에서 Azure Portal로 마이그레이션할 때 **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421**이라는 이름의 새 그룹이 보일 수 있습니다. 이 그룹에는 Intune의 사용이 허가된 사용자뿐만 아니라 Azure Active Directory의 모든 사용자도 포함됩니다. 이러한 사용 방식으로 인해 일부 기존 또는 새로운 사용자가 어떤 그룹의 멤버도 아니라면 다른 Microsoft 제품에서 문제가 발생할 수 있습니다.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>마이그레이션한 정책에 대한 상태 블레이드가 작동하지 않음

Azure 클래식 포털에서 마이그레이션한 정책의 상태 정보는 Azure Portal에서 확인할 수 없습니다. 그러나 클래식 포털에서는 이러한 정책에 대한 보고서를 계속 확인할 수 있습니다. 마이그레이션한 구성 정책에 대한 상태 정보를 확인하려면 Azure Portal에서 정책을 다시 만드세요.

## <a name="apps"></a>앱


### <a name="multiple-app-install-prompts-for-certain-vpp-apps"></a>특정 VPP 앱에 대한 여러 앱 설치 프롬프트
최종 사용자 장치에 이미 설치된 특정 VPP 앱에 대한 여러 앱 설치 프롬프트를 볼 수 있습니다. 이 문제는 **자동 앱 업데이트** 옵션이 Intune Azure Portal에 업로드한 VPP 토큰에 대해 **켜짐**으로 설정된 경우 발생합니다.    

이 문제를 해결하려면 VPP 토큰에 대해 **자동 앱 업데이트** 옵션을 사용하지 못하게 설정할 수 있습니다. 이렇게 하려면 Azure Portal에서 Microsoft Intune을 엽니다. Intune에서 **모바일 앱** > **iOS VPP 토큰**을 선택합니다. 다음으로 영향을 받는 앱을 배포한 VPP 토큰을 선택하고 **편집** > **자동 앱 업데이트** > **꺼짐** > **저장**을 선택합니다. 또는 영향을 받는 앱을 VPP 앱으로 배포하는 것을 중지할 수 있습니다. 그러면 프롬프트도 중지됩니다.    

현재 릴리스에서 알려진 문제입니다. 이 문제를 해결하게 될 예정된 수정 내용이 있습니다. 수정이 구현되면 사용자에게 더 이상 여러 앱 설치 프롬프트가 표시되지 않습니다.

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>기본 Intune 테넌트 언어에서만 iOS 대량 구매 앱을 사용할 수 있음
iOS 대량 구매 앱은 Intune 계정과 동일한 국가 코드에 대해서만 표시되며 할당할 수 있습니다. Intune은 Intune 테넌트 계정 국가 코드와 동일한 iTunes 로캘의 앱만 동기화합니다. 예를 들어 미국 스토어에서만 사용할 수 있는 앱을 구매했는데 Intune 계정이 독일어라면 Intune에 해당 앱이 표시되지 않습니다.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>동일한 iOS 대량 구매 프로그램의 여러 복사본이 업로드됨
동일한 VPP 토큰에 대해 **업로드** 단추를 여러 번 클릭하지 마세요. 여러 번 클릭하면 중복 VPP 토큰이 업로드되고, 동일한 VPP 토큰에 대해 앱이 여러 번 동기화됩니다.

### <a name="some-managed-browser-traffic-not-routed-through-azure-app-proxy----2463492---"></a>일부 Managed Browser 트래픽이 Azure App Proxy를 통해 라우팅되지 않음 <!-- 2463492 -->
특정 3차 트래픽(예: Javascript 또는 AJAX 호출)이 Azure App Proxy를 통해 라우팅되지 않는 Managed Browser 및 앱 프록시 통합에 관련된다고 알려진 문제가 있습니다. 현재 릴리스에서 알려진 문제입니다.  

<!-- ## Groups -->

## <a name="device-configuration"></a>장치 구성

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>일부 장치에 대해 Windows Information Protection 정책을 저장할 수 없음

Intune에 등록되지 않은 장치의 경우 Windows Information Protection 정책에 대한 설정의 **회사 ID** 필드에서 주 도메인만 지정할 수 있습니다.
**고급 설정** > **네트워크 경계** > **보호된 도메인 추가**를 사용하여 도메인을 더 추가하는 경우 정책을 저장할 수 없습니다. 표시되는 오류 메시지는 조만간 보다 정확하게 변경될 예정입니다.

### <a name="cisco-anyconnect-and-cisco-legacy-anyconnect-vpn-client-support---ios"></a>Cisco AnyConnect 및 Cisco Legacy AnyConnect VPN 클라이언트 지원 - iOS

iOS 장치의 경우 새로운 Cisco AnyConnect 클라이언트에서 NAC(네트워크 액세스 제어) 통합이 작동하지 않습니다. Microsoft는 NAC 통합 기능을 제공하기 위해 Cisco와 협력하고 있습니다.

[Intune에서 VPN 프로필 만들기](vpn-settings-ios.md)에서는 Cisco AnyConnect 및 Cisco Legacy AnyConnect 클라이언트에 대한 자세한 정보를 제공합니다.

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>macOS Sierra 장치에서 숫자 암호 유형 사용

현재는 macOS Sierra 장치에 대한 장치 제한 프로필에서 **숫자** **필수 암호 유형**을 선택하면 암호가 **영숫자**로 적용됩니다. 이러한 장치에 숫자 암호를 사용하려는 경우 이 설정을 구성하지 마세요.
이 문제는 향후 macOS 버전에서 해결될 수도 있습니다.

이러한 설정에 대한 자세한 내용은 [Microsoft Intune의 macOS 장치 제한 설정](device-restrictions-macos.md)을 참조하세요.

## <a name="compliance"></a>준수

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Intune의 준수 정책이 새 콘솔에 표시되지 않음

클래식 포털에서 만든 준수 정책은 마이그레이션되기는 하지만 Azure Portal의 디자인 변경으로 인해 Azure Portal에 표시되지는 않습니다. Intune 클래식 포털에서 만든 규정 준수 정책이 계속 적용되지만 클래식 포털에서 보고 편집해야 합니다.

또한 Azure Portal에서 만든 새 준수 정책은 클래식 포털에서는 보이지 않습니다.

자세한 내용은 [장치 준수](device-compliance.md)를 참조하세요.

<!-- ## Enrollment -->


## <a name="data-protection"></a>데이터 보호

### <a name="ios-app-protection-policies"></a>iOS 앱 보호 정책

등록 없이 MAM(모바일 앱 관리)을 통해 관리되는 장치에서 사용자에게 제공되는 [iOS 앱 보호 정책](app-protection-policy-settings-ios.md)을 정의할 수 있습니다. 일시적인 오류로 인해 여러 개의 소수 자릿수가 아닌 단일 소수 자릿수를 가진 iOS 버전인 경우에만 이러한 정책을 정의할 수 있습니다. 최소 버전을 iOS 10.3.1로 설정하는 것이 아니라 iOS 10.3으로 설정합니다. 이 문제는 iOS SDK의 예정된 업데이트를 통해 해결될 것입니다.


## <a name="administration-and-accounts"></a>관리 및 계정

전역 관리자(테넌트 관리자라고도 함)는 별도의 Intune 또는 EMS(Enterprise Mobility Suite) 라이선스 없이 일상적인 관리 작업을 계속 수행할 수 있습니다. 그러나 자신의 장치나 회사 장치 등록 또는 Intune 회사 포털 사용 등의 서비스를 사용하려는 전역 관리자에게는 Intune 또는 EMS 라이선스가 필요합니다.

<!-- ## Additional items -->
