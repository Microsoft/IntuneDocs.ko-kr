---
title: Microsoft Intune의 디바이스 관리 기능
description: 등록된 디바이스를 관리하는 데 Microsoft Intune이 도움을 주는 방법을 확인하려면 이 항목을 읽어보세요.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c2c50909b701ee5418ea69d73e67518de1c5bce
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67045728"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Microsoft Intune의 등록된 디바이스 관리 기능

Microsoft Intune에서 다양한 디바이스를 서비스에 *등록*하여 관리할 수 있습니다. 일부 디바이스 유형은 사용자가 직접 등록하거나, *회사 포털* 앱을 사용하여 등록할 수 있습니다. 등록하면 앱을 찾아 설치하고, 해당 디바이스가 회사 정책을 준수하는지 확인하고, IT 지원 팀에 문의할 수 있습니다.

이 문서에서는 디바이스를 등록한 후 제공되는 기능의 전체 목록이 나와 있습니다.

관리, 인벤토리, 앱 배포, 프로비저닝 및 만료는 모두 Azure Portal의 Intune을 통해 처리됩니다.

사용자가 앱을 설치하고, 디바이스를 등록 및 제거하고, 해당 IT 부서 또는 기술 지원팀에 문의할 수 있는 회사 포털에 액세스할 수 있습니다.



## <a name="device-security-and-configuration"></a>디바이스 보안 및 구성

|기능|세부 정보|추가 정보|
|--------------|-----------|--------------------|
|구성 정책<br><br>사용자 지정 정책| 조직의 모바일 디바이스에서 많은 설정과 기능을 관리할 수 있습니다. 예를 들어 암호를 요구하고, 실패한 시도 횟수를 제한하고, 화면 잠금 전 시간을 제한하고, 암호 만료 시간을 설정하고, 이전에 사용한 암호의 사용을 금지할 수 있습니다. 디바이스 카메라 또는 웹 브라우저와 같은 하드웨어 및 소프트웨어 기능의 사용을 제어할 수도 있습니다.<br><br>구성 정책에 필요한 설정이 포함되어 있지 않은 경우 사용자 지정 정책을 사용합니다. iOS 디바이스의 경우 Apple 구성기 도구에서 내보낸 설정을 가져올 수 있습니다. 다른 디바이스의 경우 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 사용하여 디바이스에서 설정 및 기능을 구성할 수 있습니다.|[Microsoft Intune 정책을 사용하여 디바이스의 설정 및 기능 관리](device-compliance-get-started.md)|
|원격 초기화, 원격 잠금 및 암호 재설정|디바이스를 분실하거나 도난당하는 경우 중요한 데이터를 지웁니다. 예를 들어, 원격으로 디바이스를 잠그거나, 공장 설정으로 복원하거나, 회사 데이터만 삭제할 수 있습니다.<br><br>디바이스에 액세스하는 방법을 잊어버리거나 분실 또는 도난당한 디바이스를 잠그거나 분실 또는 도난당한 디바이스의 데이터를 초기화할 경우 암호를 재설정할 수 있습니다.|[원격 잠금](device-remote-lock.md) 또는 [암호 재설정](device-passcode-reset.md)으로 디바이스 보호 지원|
|키오스크 모드|화면 캡처 및 전원 스위치와 같은 모바일 디바이스의 특정 기능을 잠글 수 있습니다. 또한 지정한 단일 앱을 실행하도록 디바이스를 제한할 수 있습니다. |[Microsoft Intune의 iOS 구성 정책 설정](device-restrictions-ios.md)|

## <a name="app-management"></a>앱 관리

|기능|세부 정보|추가 정보|
|--------------|-----------|--------------------|
|앱 배포 및 관리|설치 파일 및 앱 스토어를 통한 앱 배포, 자세한 앱 상태 모니터링, 앱 제거 등 수명 주기 동안 모바일 앱을 관리할 수 있는 다양한 도구를 제공합니다.|[Microsoft Intune에서 앱 배포](apps-deploy.md)|
|규격 및 비규격 앱|규격 앱(사용자가 설치 가능) 및 비규격 앱(사용자가 설치 불가능) 목록을 지정할 수 있습니다.|[Microsoft Intune의 iOS 정책 설정](device-restrictions-ios.md)|
|모바일 애플리케이션 관리|Intune을 사용하여 관리되거나, Intune으로 관리되지 않는 디바이스 모두에 대해 모바일 애플리케이션 관리를 사용하여 앱에 대한 제한을 구성합니다. 복사 및 붙여넣기, 데이터의 외부 백업, 앱 간 데이터 전송과 같은 작업을 제한하여 회사 데이터의 보안을 강화할 수 있습니다.|[Microsoft Intune 콘솔에서 모바일 애플리케이션 관리 정책 구성 및 배포](app-wrapper-prepare-android.md)|
|iOS 모바일 앱 구성|모바일 앱 구성 정책을 사용하여 사용자가 앱을 실행할 때 필요할 수 있는 iOS 앱에 대한 설정을 제공할 수 있습니다. 예를 들어 앱에서 사용자가 포트 번호 또는 로그온 정보를 지정하도록 요구할 수 있습니다. 앱 구성을 간소화하고 지원 요청 횟수를 줄일 수 있습니다.|[Microsoft Intune에서 모바일 앱 구성 정책을 사용하여 iOS 앱 구성](app-configuration-policies-use-ios.md)|
|iOS 모바일 앱 프로비전 프로필|곧 만료되는 iOS 앱에 프로비전 프로필을 배포하는 데 도움이 됩니다. |[iOS 모바일 프로비전 프로필 정책을 사용하여 모바일 앱이 만료되지 않도록 방지](app-provisioning-profile-ios.md)|
|관리되는 브라우저|디바이스 사용자가 방문할 수 있는 웹 사이트를 제어하도록 관리되는 브라우저 정책을 구성합니다. 또한 관리되는 브라우저에 모바일 애플리케이션 관리 정책을 적용할 수도 있습니다.|[Microsoft Intune에서 Managed Browser 정책을 사용하여 인터넷 액세스 관리](app-configuration-managed-browser.md)|
|비즈니스용 Windows Hello|온-프레미스 Active Directory를 사용하는 Windows 10 또는 Azure Active Directory에서 암호, 스마트 카드 또는 가상 스마트 카드를 대신하는 로그인 방법인 비즈니스용 Windows Hello를 통합할 수 있습니다.|[Microsoft Intune을 사용하는 디바이스에서 비즈니스용 Windows Hello 설정 제어](windows-hello.md)|
|대량 구매 앱|앱 스토어에서 라이선스 정보를 가져오고, 사용한 라이선스 수를 추적하고, 소유한 라이선스보다 많은 앱을 설치하지 못하도록 차단하는 방식으로 대량 구매 프로그램을 통해 구매한 앱을 관리할 수 있습니다.|[Microsoft Intune을 사용하여 대량 구매 앱 관리](vpp-apps.md)|

## <a name="company-resource-access"></a>회사 리소스 액세스

|기능|세부 정보|추가 정보|
|--------------|-----------|--------------------|
|인증서 프로필|Wi-Fi, VPN 및 전자 메일 프로필을 보호하고 인증하는 데 사용할 수 있는 SCEP(단순 인증서 등록 프로토콜) 인증서와 신뢰할 수 있는 인증서 프로필을 만들고 배포합니다.|[Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](certificates-configure.md)|
|Wi-Fi 프로필|사용자에게 무선 네트워크 설정을 배포합니다. 이러한 설정을 배포하여 사용자가 기업 네트워크에 연결하는 데 필요한 노력을 최소화할 수 있습니다.|[Microsoft Intune에서 Wi-Fi 연결](wi-fi-settings-configure.md)|
|전자 메일 프로필|이메일 설정을 만들고 디바이스에 배포하므로 사용자가 설정할 필요 없이 개인 디바이스에서 회사 이메일에 액세스할 수 있습니다.|[Microsoft Intune에서 메일 프로필을 사용하여 회사 메일에 대한 액세스 구성](email-settings-configure.md)|
|VPN 프로필|사용자와 조직의 디바이스에 VPN 설정을 배포합니다. 이러한 설정을 배포하여 사용자가 회사 네트워크에 있는 리소스에 연결하는 데 필요한 노력을 최소화할 수 있습니다.|[Microsoft Intune에서 VPN 연결](device-profiles.md#vpn)|
|조건부 액세스 정책|Intune에서 관리하지 않는 디바이스의 Microsoft Exchange 전자 메일 및 SharePoint Online에 대한 액세스를 관리합니다.|[Microsoft Intune을 사용한 메일 및 SharePoint 액세스 제한](app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>다음 단계

[관리할 수 있는 디바이스 목록을 참조하세요](device-management.md).
