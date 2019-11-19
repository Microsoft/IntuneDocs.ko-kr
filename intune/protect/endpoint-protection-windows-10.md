---
title: Microsoft Intune에서 Windows 10 디바이스 보호 설정 - Azure | Microsoft Docs
description: Windows 10 디바이스에서 엔드포인트 보호 설정을 사용하거나 추가하여 Microsoft Defender 기능을 사용하도록 설정합니다. 여기에는 Application Guard, 방화벽, SmartScreen, 암호화 및 BitLocker, Exploit Guard, Application Control, Security Center 및 Microsoft Intune의 로컬 디바이스에 대한 보안이 포함됩니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: karthig
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e2909e7ad1ced9483a6cec58f1f3009f56946f5f
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74058420"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Intune을 사용하여 디바이스를 보호하기 위한 Windows 10( 이상) 설정

Microsoft Intune에는 디바이스를 보호할 수 있는 많은 설정이 포함되어 있습니다. 이 문서에서는 Windows 10 이상 디바이스에서 사용하도록 설정하고 구성할 수 있는 모든 설정에 대해 설명합니다. 이러한 설정은 BitLocker 및 Microsoft Defender를 포함한 보안을 제어하기 위해 Intune의 엔드포인트 보호 구성 프로필에 만들어집니다.  

Microsoft Defender 바이러스 백신을 구성하려면 [Windows 10 디바이스 차단](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)을 참조하세요.  

## <a name="before-you-begin"></a>시작하기 전에  

[엔드포인트 보호 디바이스 구성 프로필을 만듭니다](endpoint-protection-configure.md).  

Csp (구성 서비스 공급자)에 대 한 자세한 내용은 [구성 서비스 공급자 참조](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)를 참조 하세요.  

## <a name="microsoft-defender-application-guard"></a>Microsoft Defender Application Guard  

Microsoft Edge를 사용하는 동안 Microsoft Defender Application Guard는 조직에서 신뢰하지 않는 사이트로부터 환경을 보호합니다. 사용자가 격리된 네트워크 경계에 나열되지 않은 사이트를 방문하면 해당 사이트가 Hyper-V 가상화된 브라우징 세션에서 열립니다. 신뢰할 수 있는 사이트는 디바이스 구성에 구성되는 네트워크 경계로 정의됩니다.  

Application Guard는 Windows 10(64비트) 디바이스에서만 사용할 수 있습니다. 이 프로필을 사용하면 Win32 구성 요소가 설치되어 Application Guard를 활성화할 수 있습니다.  

- **Application Guard**  
  **기본값**: 구성되지 않음  
   Application Guard CSP: [Settings/AllowWindowsDefenderApplicationGuard](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **Edge에 대해 설정됨** - 이 기능을 켜면 Hyper-V 가상화된 브라우징 컨테이너에서 신뢰할 수 없는 사이트가 열립니다.  
  - **구성 되지 않음** -장치에서 신뢰할 수 있고 신뢰할 수 없는 모든 사이트를 열 수 있습니다.  

- **클립보드 동작**  
  **기본값**: 구성되지 않음  
   Application Guard CSP: [Settings/ClipboardSettings](https://go.microsoft.com/fwlink/?linkid=872351)  

  로컬 PC와 Application Guard 가상 브라우저 간에 허용되는 복사 및 붙여넣기 작업을 선택합니다.  
  - **구성되지 않음**  
  - **PC에서 브라우저만 복사 하 여 붙여넣기 허용**  
  - **브라우저에서 PC로만 복사 및 붙여넣기 허용**  
  - **PC와 브라우저 간 복사 및 붙여넣기 허용**  
  - **PC와 브라우저 간 복사 및 붙여넣기 차단**  

- **클립보드 내용**  
  이 설정은 *클립보드 동작이* *허용* 설정 중 하나로 설정 된 경우에만 사용할 수 있습니다.  
  **기본값**: 구성되지 않음  
  Application Guard CSP: [Settings/ClipboardFileType](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  허용 된 클립보드 콘텐츠를 선택 합니다.  
  - **구성되지 않음**  
  - **Text**  
  - **이미지**  
  - **텍스트 및 이미지**  

- **엔터프라이즈 사이트의 외부 콘텐츠**  
  **기본값**: 구성되지 않음  
  Application Guard CSP: [Settings/BlockNonEnterpriseContent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - **차단** - 승인되지 않은 웹 사이트의 콘텐츠가 로드되지 않습니다.  
  - **구성되지 않음** - 엔터프라이즈가 아닌 사이트가 디바이스에서 열릴 수 있습니다.  
 
- **가상 브라우저에서 인쇄**  
  **기본값**: 구성되지 않음  
  Application Guard CSP: [Settings/PrintingSettings](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **허용** -가상 브라우저에서 선택한 콘텐츠를 인쇄할 수 있습니다.  
  - **구성 되지 않음** 모든 인쇄 기능을 사용 하지 않습니다.  

  인쇄를 *허용* 하면 다음 설정을 구성할 수 있습니다.
  - **인쇄 형식** 다음 옵션 중 하나 이상을 선택 합니다.  
    - PDF  
    - XPS  
    - 로컬 프린터
    - 네트워크 프린터  

- **로그 수집**  
  **기본값**: 구성되지 않음  
  Application Guard CSP: [Audit/AuditApplicationGuard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **허용** - Application Guard 브라우징 세션 내에서 발생하는 이벤트에 대한 로그를 수집합니다.  
  - **구성되지 않음** - 검색 세션 내에서 로그를 수집하지 않습니다.  

- **사용자 생성 브라우저 데이터 보존**  
  **기본값**: 구성되지 않음  
  Application Guard CSP: [Settings/AllowPersistence 속성](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **허용** Application Guard 가상 브라우징 세션 중에 만들어진 사용자 데이터(예: 암호, 즐겨찾기 및 쿠키)를 저장합니다.  
  - **구성되지 않음** 디바이스가 다시 시작되거나 사용자가 로그아웃할 때 사용자가 다운로드한 파일과 데이터를 삭제합니다.  

- **그래픽 가속**  
 **기본값**: 구성되지 않음  
  Application Guard CSP: [Settings/AllowVirtualGPU](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - **사용** - 가상 그래픽 처리 장치에 액세스하여 그래픽 집약적 웹 사이트 및 비디오를 더 빠르게 로드합니다.  
  - **구성 되지 않음** 그래픽에 장치 CPU 사용 가상 그래픽 처리 단위를 사용 하지 마세요.  

- **호스트 파일 시스템에 파일 다운로드**  
  **기본값**: 구성되지 않음  
  Application Guard CSP: [Settings/SaveFilesToHost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **사용** - 사용자가 가상화된 브라우저에서 호스트 운영 체제로 파일을 다운로드할 수 있습니다.  
  - **구성되지 않음** - 파일을 디바이스에서 로컬로 유지하고, 호스트 파일 시스템에 파일을 다운로드하지 않습니다.  

## <a name="microsoft-defender-firewall"></a>Microsoft Defender 방화벽  
 
### <a name="global-settings"></a>전역 설정  

다음 설정은 모든 네트워크 형식에 적용할 수 있습니다.  

- **파일 전송 프로토콜**  
  **기본값**: 구성되지 않음  
   방화벽 CSP: [MdmStore/Global/DisableStatefulFtp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - **차단** - 상태 저장 FTP를 사용하지 않도록 설정합니다.  
  - **구성되지 않음** - 방화벽에서 보조 연결을 허용하는 상태 저장 FTP 필터링을 수행합니다.  

- **삭제 전 보안 연결 유휴 시간**  
  **기본값**: *구성되지 않음*  
   방화벽 CSP: [MdmStore/Global/SaIdleTime](https://go.microsoft.com/fwlink/?linkid=872539)  

   보안 연결을 삭제 한 후 유휴 시간을 초 단위로 지정 합니다.   

- **미리 공유한 키 인코딩**  
  **기본값**: 구성되지 않음  
   방화벽 CSP: [MdmStore/Global/PresharedKeyEncoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - U t f-8을 사용 하 여 presheared **키를 인코딩합니다** .  
   - **구성 되지 않음** -로컬 저장소 값을 사용 하 여 presheared 키를 인코딩합니다.  

- **IPsec 예외**  
  **기본값**: *0 선택 됨*  
   방화벽 CSP: [MdmStore/Global/제외](https://go.microsoft.com/fwlink/?linkid=872547)

   IPsec에서 제외할 다음 유형의 트래픽을 하나 이상 선택 합니다.  
   - **IPv6 ICMP 종류 코드 네트워크 환경 검색**  
   - **ICMP**  
   - **IPv6 ICMP 종류 코드 라우터 검색**  
   - **IPv4 및 IPv6 DHCP 네트워크 트래픽 모두**  

- **인증서 해지 목록 확인**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [MdmStore/Global/CRLcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  디바이스에서 인증서 해지 목록을 확인하는 방법을 선택합니다. 다음 옵션을 사용할 수 있습니다.  
  - **CRL 확인 사용 안 함**  
  - **해지 된 인증서에 대해서만 CRL 확인 실패**  
  - 발생 한 **오류에 대 한 CRL 확인에 실패**합니다.  
 

- **키 지정 모듈에 대해 선택적으로 인증 집합 일치**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [MdmStore/Global/OpportunisticallyMatchAuthSetPerKM](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **사용** 키 지정 모듈에서 지원하지 않는 인증 모음만 무시해야 합니다.  
  - **구성되지 않음** 키 지정 모듈에서 집합에 지정된 모든 인증 모음을 지원하지 않으면 전체 인증 집합을 무시합니다.  


- **패킷 큐**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [MdmStore/Global/EnablePacketQueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  IPsec 터널 게이트웨이 시나리오의 암호화된 수신 및 일반 텍스트 전달에 대해 수신 쪽 소프트웨어의 크기 조정을 사용하도록 설정되는 방법을 지정합니다. 이 설정은 패킷 순서가 유지되는지 확인합니다. 다음 옵션을 사용할 수 있습니다.  
  - **구성되지 않음**  
  - **모든 패킷 큐 사용 안 함**  
  - **인바운드 암호화 된 패킷만 큐에 대기**  
  - **해독 후에 큐 패킷을 전달만 수행 합니다.**  
  - **인바운드 및 아웃 바운드 패킷 모두 구성**  

### <a name="network-settings"></a>네트워크 설정  

다음 설정은이 문서에 한 번만 표시 되지만 모두 세 가지 특정 네트워크 형식에 적용 됩니다.  
- **도메인 (작업 공간) 네트워크**  
- **개인 (검색 가능) 네트워크**  
- **공용 (검색 불가능) 네트워크**  

#### <a name="general-settings"></a>일반 설정  

- **Microsoft Defender 방화벽**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [Enablefirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **사용** - 방화벽 및 고급 보안을 설정할 수 있습니다. 
  - **구성되지 않음** 다른 정책 설정에 관계없이 모든 네트워크 트래픽을 허용합니다.  

- **은폐 모드**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [DisableStealthMode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - **구성되지 않음**  
  - **차단** -방화벽이 스텔스 모드에서 작동 하지 못하도록 차단 됩니다. 은폐 모드를 차단하면 **IPsec 보안 패킷 예외**도 차단할 수 있습니다.  
  - **허용** -방화벽은 스텔스 모드에서 작동 하므로 응답을 검색 하는 요청을 방지할 수 있습니다.  

- **스텔스 모드로 IPsec 보안 패킷 예외**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [DisableStealthModeIpsecSecuredPacketExemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  *스텔스 모드가* *Block*으로 설정 된 경우이 옵션은 무시 됩니다.  

  - **구성되지 않음**  
  - **차단** -IPSec 보안 패킷은 예외를 수신 하지 않습니다.  
  - **허용** -예외를 사용 합니다. 방화벽의 스텔스 모드는 호스트 컴퓨터가 IPsec으로 보안이 유지 되는 원치 않는 네트워크 트래픽에 응답 하지 않도록 방지 해서는 안 됩니다.  

- **보호됨**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [차폐](https://go.microsoft.com/fwlink/?linkid=872561)  
    - **구성되지 않음**  
    - **차단** -Microsoft Defender 방화벽을 설정 하 고이 설정을 *차단*으로 설정 하면 다른 정책 설정에 관계 없이 들어오는 모든 트래픽이 차단 됩니다. 
    - **허용** - *허용*으로 설정 하면이 설정이 해제 되 고 다른 정책 설정에 따라 들어오는 트래픽이 허용 됩니다.

- **멀티캐스트 브로드캐스트에 대한 유니캐스트 응답**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [DisableUnicastResponsesToMulticastBroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  일반적으로 멀티캐스트 또는 브로드캐스트 메시지에 대한 유니캐스트 응답을 수신하려 하지 않습니다. 이러한 응답은 서비스 거부(DOS) 공격 또는 알려진 라이브 컴퓨터를 검색하려고 시도하는 공격자를 나타낼 수 있습니다.  
  - **구성되지 않음**  
  - **블록** - 멀티캐스트 브로드캐스트에 대한 유니캐스트 응답 비활성화  
  - **허용** - 멀티캐스트 브로드캐스트에 대한 유니캐스트 응답 허용  

- **인바운드 알림**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [DisableInboundNotifications](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - **구성되지 않음**  
  - **블록** -앱이 포트에서 수신 대기 하지 못하도록 차단 될 때 사용할 알림을 숨깁니다.  
  - **허용** - 이 설정을 사용하도록 지정하여 앱이 포트에서 수신 대기하지 않도록 차단될 때 사용자에게 알림을 표시할 수 있습니다.  

- **아웃바운드 연결에 대한 기본 작업**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [DefaultOutboundAction](https://aka.ms/intune-firewall-outboundaction)  
  
  방화벽에서 아웃 바운드 연결에 대해 수행 하는 기본 작업을 구성 합니다. 이 설정은 Windows 버전 1809 이상에 적용 됩니다.  

  - **구성되지 않음**  
  - **Block** -차단 하지 않도록 명시적으로 지정 되지 않은 경우 기본 방화벽 작업은 아웃 바운드 트래픽에 대해 실행 되지 않습니다.  
  - **허용** -기본 방화벽 작업이 아웃 바운드 연결에 대해 실행 됩니다.  

- **인바운드 연결에 대한 기본 작업**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [DefaultInboundAction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - **구성되지 않음**  
  - **차단** - 인바운드 연결에서 기본 방화벽 작업이 실행되지 않습니다.  
  - **허용** -기본 방화벽 작업이 인바운드 연결에 대해 실행 됩니다.  

#### <a name="rule-merging"></a>규칙 병합  

- **로컬 스토리지의 권한 있는 애플리케이션 Microsoft Defender 방화벽 규칙**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [AuthAppsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - **구성되지 않음**  
  - **차단** - 로컬 저장소에서 권한 있는 애플리케이션 방화벽 규칙이 무시되고 적용되지 않습니다.  
  - **허용** -
   **사용**을 선택하면 방화벽 규칙을 로컬 저장소에 적용하여 해당 규칙이 인식 및 적용됩니다.  

- **로컬 저장소의 전역 포트 Microsoft Defender 방화벽 규칙**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [GlobalPortsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - **구성되지 않음**  
  - **Block** -로컬 저장소의 전역 포트 방화벽 규칙은 무시 되 고 적용 되지 않습니다.  
  - **허용** - 인식 및 적용할 글로벌 포트 방화벽 규칙을 로컬 저장소에 적용합니다.  

- **로컬 저장소의 Microsoft Defender 방화벽 규칙**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [Allowlocalpolicymerge](https://go.microsoft.com/fwlink/?linkid=872567)  

  - **구성되지 않음**  
  - **차단** -로컬 저장소의 방화벽 규칙은 무시 되 고 적용 되지 않습니다.
  - **허용** - 인식 및 적용할 방화벽 규칙을 로컬 저장소에 적용합니다.  

- **로컬 저장소의 IPsec 규칙**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [Allowlocaldependency Policymerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - **구성되지 않음**  
  - **차단** -  스키마 버전 및 연결 보안 규칙 버전에 관계없이 로컬 저장소에서 연결 보안 규칙이 무시되고 적용되지 않습니다.  
  - **허용** - 스키마 또는 연결 보안 규칙 버전과 관계없이 로컬 저장소에서 연결 보안 규칙이 적용됩니다.  

### <a name="firewall-rules"></a>방화벽 규칙  

하나 이상의 사용자 지정 방화벽 규칙을 **추가할** 수 있습니다. 자세한 내용은 [Windows 10 장치에 대 한 사용자 지정 방화벽 규칙 추가](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)를 참조 하세요.  

사용자 지정 방화벽 규칙은 다음 옵션을 지원 합니다.  

#### <a name="general-settings"></a>일반 설정:  

- **이름**  
  **기본값**: *이름 없음*  

  규칙에 대 한 친숙 한 이름을 지정 합니다. 이 이름은 규칙을 식별 하는 데 도움이 되는 규칙 목록에 표시 됩니다.  

- **설명**  
  **기본값**: *설명 없음*  

  규칙에 대 한 설명을 제공 합니다.  

- **방향**   
  **기본값**: 구성되지 않음  
  방화벽 CSP: [FirewallRules/*FirewallRuleName*/Direction](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  이 규칙이 **인바운드**또는 **아웃 바운드** 트래픽에 적용 되는지 여부를 지정 합니다. **구성 되지 않음**으로 설정 하면 규칙이 아웃 바운드 트래픽에 자동으로 적용 됩니다.  

- **작업**  
  **기본값**: 구성되지 않음  
  방화벽 CSP: [FirewallRules/*FirewallRuleName*/Action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action)및 [FirewallRules/*FirewallRuleName*/action/type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  **허용** 또는 **차단**을 선택 합니다. **구성 되지 않음**으로 설정 하는 경우 규칙은 기본적으로 트래픽을 허용 합니다.  

- **네트워크 유형**  
  **기본값**: 0 선택 됨  
  방화벽 CSP: [FirewallRules/*FirewallRuleName*/Profiles](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  이 규칙이 속한 최대 세 가지 유형의 네트워크 유형을 선택 합니다. 옵션에는 **도메인**, **개인**및 **공용**이 포함 됩니다.  네트워크 유형을 선택 하지 않은 경우이 규칙은 세 가지 네트워크 유형 모두에 적용 됩니다.  

#### <a name="application-settings"></a>애플리케이션 설정  

- **애플리케이션**  
  **기본값**: 모두  

  앱 또는 프로그램에 대 한 연결을 제어 합니다. 다음 옵션 중 하나를 선택 하 고 추가 구성을 완료 합니다.  
  - **패키지 제품군 이름** – 패키지 제품군 이름을 지정 합니다. 패키지 제품군 이름을 찾으려면 PowerShell 명령 **add-appxpackage**를 사용 합니다.   
    방화벽 CSP: [FirewallRules/*FirewallRuleName*/App/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - **파일 경로** – 절대 경로 또는 상대 경로일 수 있는 클라이언트 장치에서 앱의 파일 경로를 지정 해야 합니다. 예: C:\Windows\System\Notepad.exe 또는%WINDIR%\Notepad.exe.  
    방화벽 CSP: [FirewallRules/*FirewallRuleName*/app/files](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Windows 서비스** – 트래픽을 보내거나 받는 응용 프로그램이 아닌 서비스인 windows 서비스 짧은 이름을 지정 합니다. 서비스 짧은 이름을 찾으려면 PowerShell 명령 **get-help**를 사용 합니다.  
    방화벽 CSP: [FirewallRules/*FirewallRuleName*/app/servicename](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **모두**– *추가 구성을 사용할 수 없습니다*.  

#### <a name="ip-address-settings"></a>IP 주소 설정  

이 규칙이 적용 되는 로컬 및 원격 주소를 지정 합니다.  

- **로컬 주소**    
  **기본값**: 모든 주소  
  방화벽 CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  **주소** 또는 **지정 된 주소**를 선택 합니다.  

  *지정 된 주소*를 사용 하는 경우 하나 이상의 주소를 규칙에 적용 되는 로컬 주소의 쉼표로 구분 된 목록으로 추가 합니다. 유효한 토큰은 다음과 같습니다.  
  - *모든* 로컬 주소에 대해 별표 "*"를 사용 합니다. 별표를 사용 하는 경우 사용 하는 유일한 토큰 이어야 합니다.  
  - 서브넷을 지정 하려면 서브넷 마스크 또는 네트워크 접두사 표기법을 사용 합니다. 서브넷 마스크와 네트워크 접두사를 모두 지정 하지 않으면 서브넷 마스크의 기본값은 255.255.255.255입니다.  
  - 올바른 IPv6 주소입니다.  
  - 공백이 포함 되지 않은 "시작 주소-끝 주소" 형식의 IPv4 주소 범위입니다.  
  - 공백이 포함 되지 않은 "시작 주소-끝 주소" 형식의 IPv6 주소 범위입니다.  

- **원격 주소**  
  **기본값**: 모든 주소  
  방화벽 CSP: [FirewallRules/*FirewallRuleName*/dvaddressvvvvaddress](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  **주소** 또는 **지정 된 주소**를 선택 합니다.  

  *지정 된 주소*를 사용 하는 경우 하나 이상의 주소를 규칙에 적용 되는 원격 주소를 쉼표로 구분 된 목록으로 추가 합니다. 토큰은 대/소문자를 구분 하지 않습니다. 유효한 토큰은 다음과 같습니다.  
  - *모든* 원격 주소에 별표 "*"를 사용 합니다. 별표를 사용 하는 경우 사용 하는 유일한 토큰 이어야 합니다.  
  - "Defaultgateway"  
  - "DHCP"  
  - "DNS"  
  - "WINS"  
  - "인트라넷" (Windows 버전 1809 이상에서 지원 됨)  
  - "RmtIntranet" (Windows 버전 1809 이상에서 지원 됨)  
  - "Internet" (Windows 버전 1809 이상에서 지원 됨)  
  - "Ply2Renders" (Windows 버전 1809 이상에서 지원 됨)  
  - "LocalSubnet"는 로컬 서브넷의 로컬 주소를 나타냅니다.  
  - 서브넷을 지정 하려면 서브넷 마스크 또는 네트워크 접두사 표기법을 사용 합니다. 서브넷 마스크와 네트워크 접두사를 모두 지정 하지 않으면 서브넷 마스크의 기본값은 255.255.255.255입니다.  
  - 올바른 IPv6 주소입니다.  
  - 공백이 포함 되지 않은 "시작 주소-끝 주소" 형식의 IPv4 주소 범위입니다.  
  - 공백이 포함 되지 않은 "시작 주소-끝 주소" 형식의 IPv6 주소 범위입니다.  

#### <a name="port-and-protocol-settings"></a>포트 및 프로토콜 설정  
이 규칙이 적용 되는 로컬 및 원격 포트를 지정 하십시오.  

- **프로토콜**  
  **기본값**: Any  
  방화벽 CSP: [FirewallRules/*FirewallRuleName*/protocol](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  다음 중 하나를 선택 하 고 필요한 모든 구성을 완료 합니다.  
  - **모두** – 추가 구성을 사용할 수 없습니다.  
  - **TCP** – 로컬 및 원격 포트를 구성 합니다. 두 옵션 모두 모든 포트나 지정 된 포트를 지원 합니다. 쉼표로 구분 된 목록을 사용 하 여 지정 된 포트를 입력 합니다.  
    - **로컬 포트** -방화벽 CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **원격 포트** -방화벽 CSP: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** – 로컬 및 원격 포트를 구성 합니다. 두 옵션 모두 모든 포트나 지정 된 포트를 지원 합니다. 쉼표로 구분 된 목록을 사용 하 여 지정 된 포트를 입력 합니다.  
    - **로컬 포트** -방화벽 CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **원격 포트** -방화벽 CSP: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **사용자 지정** -0에서 255 사이의 사용자 지정 **프로토콜** 번호를 지정 합니다.  

#### <a name="advanced-configuration"></a>고급 구성  
- **인터페이스 유형**  
  **기본값**: 0 선택 됨  
  방화벽 CSP: [FirewallRules/*FirewallRuleName*/InterfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  다음 옵션 중에서 선택합니다.  
  - **원격 액세스**  
  - **무선**  
  - **	LAN(Local Area Network)**  

- **이러한 사용자 로부터의 연결만 허용**  
  **기본값**: 모든 사용자 *(목록이 지정 되지 않은 경우 기본적으로 모두 사용 됨)*  
  방화벽 CSP: [FirewallRules/*FirewallRuleName*/LocalUserAuthorizationList](https://aka.ms/intunefirewallauthorizedusers)  

  이 규칙에 대 한 권한이 있는 로컬 사용자 목록을 지정 합니다. 이 규칙이 Windows 서비스에 적용 되는 경우 권한 있는 사용자 목록을 지정할 수 없습니다.  


## <a name="microsoft-defender-smartscreen-settings"></a>Microsoft Defender SmartScreen 설정  
 
장치에 Microsoft Edge가 설치 되어 있어야 합니다.  

- **앱 및 파일용 SmartScreen**  
  **기본값**: 구성되지 않음  
   SmartScreen CSP: [smartscreen/EnableSmartScreenInShell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **구성 되지 않음** -SmartScreen 사용을 사용 하지 않도록 설정 합니다.  
  - **사용** - 파일 실행 및 앱 실행용 Windows SmartScreen이 활성화됩니다. SmartScreen은 클라우드 기반 피싱 방지 및 맬웨어 방지 구성 요소입니다.  

- **확인되지 않은 파일 실행**  
  **기본값**: 구성되지 않음  
   SmartScreen CSP: [smartscreen/PreventOverrideForFilesInShell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **구성되지 않음** - 이 기능을 비활성화하여 최종 사용자가 확인되지 않은 파일을 실행할 수 있도록 합니다.  
  - **차단** - 최종 사용자가 Windows SmartScreen에서 확인되지 않은 파일을 실행할 수 없습니다.  

## <a name="windows-encryption"></a>Windows 암호화  
 
### <a name="windows-settings"></a>Windows 설정  

- **디바이스 암호화**  
  **기본값**: 구성되지 않음  
  BitLocker CSP: [Requiredeviceencryption](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **필수** - 디바이스 암호화를 사용하도록 사용자에게 요청합니다. Windows 버전 및 시스템 구성에 따라 사용자에게 다음과 같이 요청할 수 있습니다.  
    - 다른 공급자의 암호화를 사용하도록 설정되지 않았는지 확인합니다.  
    - BitLocker 드라이브 암호화를 해제한 다음, BitLocker를 다시 설정해야 합니다.  
  - **구성되지 않음**  
  
  다른 암호화 방법이 활성화된 상태에서 Windows 암호화를 켜면 디바이스가 불안정해질 수 있습니다.  

- **스토리지 카드 암호화(모바일만 해당)**  
  *이 설정은 Windows 10 모바일에만 적용됩니다.*  
  **기본값**: 구성되지 않음  
  BitLocker CSP: [RequireStorageCardEncryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - **필수**로 설정하면 디바이스에서 사용하는 이동식 스토리지 카드를 암호화합니다.  
  - **구성되지 않음** - 스토리지 카드 암호화가 필요하지 않으며 사용자에게 이 암호화를 설정하도록 요구하지 않습니다.  

### <a name="bitlocker-base-settings"></a>BitLocker 기본 설정  

기본 설정은 모든 종류의 데이터 드라이브에 대한 범용 BitLocker 설정입니다. 최종 사용자가 모든 종류의 데이터 드라이브에서 수정할 수 있는 드라이브 암호화 작업 또는 구성 옵션을 관리하는 설정은 다음과 같습니다.  

- **다른 디스크 암호화에 대한 경고**  
  **기본값**: 구성되지 않음  
  BitLocker CSP: [AllowWarningForOtherDiskEncryption](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **차단** - 다른 디스크 암호화 서비스가 디바이스에 있는 경우 경고 메시지를 표시하지 않도록 설정합니다.  
  - **구성 되지 않음** -다른 디스크 암호화가 표시 되도록 경고를 허용 합니다.  

  *차단*으로 설정 하면 다음 설정을 구성할 수 있습니다.  

  - **Azure AD 조인 중에 표준 사용자가 암호화를 활성화하도록 허용**  
    *이 설정은 Azure Active Directory 조인 된 (Azure ADJ) 장치에만 적용 되며, `Warning for other disk encryption`이전 설정에 따라 달라 집니다.*  
    **기본값**: 구성되지 않음  
    BitLocker CSP: [Allowstandarduserencryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **허용** -표준 사용자 (비관리자)가 로그인 할 때 BitLocker 암호화를 사용 하도록 설정할 수 있습니다.  
     - **구성되지 않음** 관리자만 디바이스에서 BitLocker 암호화를 사용하도록 설정할 수 있습니다.  

- **암호화 방법 구성**  
  **기본값**: 구성되지 않음  
  BitLocker [CSP:](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **사용** - 운영 체제, 데이터 및 이동식 드라이브에 대한 암호화 알고리즘을 구성합니다.  
  - **구성되지 않음** - BitLocker에서 XTS-AES 128 비트를 기본 암호화 방법으로 사용하거나 설치 스크립트에서 지정된 암호화 방법을 사용합니다.  

  ‘사용’으로 설정하면 다음 설정을 구성할 수 있습니다.   

  - **운영 체제 드라이브에 대한 암호화**  
    **기본값**: XTS-AES 128 비트  
   
    운영 체제 드라이브에 대한 암호화 방법을 선택합니다. XTS-AES 알고리즘을 사용하는 것이 좋습니다.  
    - **AES-CBC 128 비트**  
    - **AES-CBC 256 비트**  
    - **XTS-AES 128 비트**  
    - **XTS-AES 256 비트**  

  - **고정 데이터 드라이브에 대한 암호화**  
    **기본값**: AES-CBC 128 비트  
   
    고정(기본 제공) 데이터 드라이브에 대한 암호화 방법을 선택합니다. XTS-AES 알고리즘을 사용하는 것이 좋습니다.  
    - **AES-CBC 128 비트**  
    - **AES-CBC 256 비트**  
    - **XTS-AES 128 비트**  
    - **XTS-AES 256 비트**  

  - **이동식 데이터 드라이브에 대한 암호화**  
    **기본값**: AES-CBC 128 비트  

    이동식 데이터 드라이브에 대한 암호화 방법을 선택합니다. Windows 10을 실행하지 않는 디바이스에서 이동식 드라이브를 사용하는 경우 AES-CBC 알고리즘을 사용하는 것이 좋습니다.  
    - **AES-CBC 128 비트**  
    - **AES-CBC 256 비트**  
    - **XTS-AES 128 비트**  
    - **XTS-AES 256 비트**  

### <a name="bitlocker-os-drive-settings"></a>BitLocker OS 드라이브 설정  

다음 설정은 특히 운영 체제 데이터 드라이브에 적용됩니다.  

- **시작 시 추가 인증**  
  **기본값**: 구성되지 않음  
  BitLocker CSP: [Systemdrivesrequirestartupauthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **필요** - TPM(신뢰할 수 있는 플랫폼 모듈) 사용을 포함하여 컴퓨터 시작에 필요한 인증 요구 사항을 구성할 수 있습니다.  
  - **구성 되지 않음** -TPM을 사용 하는 장치에 대 한 기본 옵션만 구성 합니다.  

  ‘필요’로 설정하면 다음 설정을 구성할 수 있습니다.   

  - **호환되지 않는 TPM 칩과 BitLocker**  
    **기본값**: 구성되지 않음  

    - **차단** - 호환되는 TPM 칩이 디바이스에 없을 때 BitLocker를 사용하지 못합니다.  
    - **구성되지 않음** - 사용자가 호환되는 TPM 칩 없이 BitLocker를 사용할 수 있습니다. BitLocker에는 암호 또는 시작 키가 필요할 수 있습니다.  

  - **호환되는 TPM 시작**  
    **기본값**: TPM 허용  

    TPM 허용, 필수 또는 허용 안 함을 구성 합니다.  

    - **TPM 허용**  
    - **TPM 허용 안 함**  
    - **TPM 필요**  

  - **호환되는 TPM 시작 PIN**  
    **기본값**: TPM을 사용 하 여 시작 PIN 허용  

    TPM 칩과 함께 시작 PIN 사용을 허용하거나, 허용하지 않거나, 요구하도록 선택합니다. 시작 PIN을 사용하려면 최종 사용자와의 상호 작용이 필요합니다.  

    - **TPM을 사용한 시작 PIN 허용**  
    - **TPM을 사용한 시작 PIN 허용 안 함**  
    - **TPM을 사용한 시작 PIN 필요**

  - **호환되는 TPM 시작 키**  
    **기본값**: TPM을 사용 하 여 시작 키 허용  

    TPM 칩과 함께 시작 키 사용을 허용하거나, 허용하지 않거나, 요구하도록 선택합니다. 시작 키를 사용하려면 최종 사용자와의 상호 작용이 필요합니다.  

    - **TPM을 사용 하 여 시작 키 허용**  
    - **TPM을 사용 하 여 시작 키 허용 안 함**  
    - **TPM이 있는 시작 키 필요**  

  - **호환되는 TPM 시작 키 및 PIN**  
    **기본값**: TPM을 사용 하 여 시작 키 및 PIN 허용  

    TPM 칩과 함께 시작 키 및 PIN 사용을 허용하거나, 허용하지 않거나, 요구하도록 선택합니다. 시작 키와 PIN을 사용하려면 최종 사용자와의 상호 작용이 필요합니다.  
    - **TPM을 사용 하 여 시작 키 및 PIN 허용**  
    - **TPM을 사용 하 여 시작 키 및 PIN 허용 안 함**  
    - **TPM을 사용 하 여 시작 키 및 PIN 필요**   

- **최소 PIN 길이**  
    **기본값**: 구성되지 않음  
    BitLocker CSP: [Systemnees% Pinlength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **사용** TPM 시작 PIN의 최소 길이를 구성 합니다.  
    - **구성되지 않음** - 사용자가 6-20 자릿수의 시작 PIN을 구성할 수 있습니다.  

  ‘사용’으로 설정하면 다음 설정을 구성할 수 있습니다.   

  - **최소 문자 수**  
    **기본값**: *구성 되지 않은* BitLocker CSP: [Systemnees이상 pinlength](https://go.microsoft.com/fwlink/?linkid=872528)  

    시작 PIN에 필요한 문자 수를 **4**-**20**에서 입력합니다.  

- **OS 드라이브 복구**  
  **기본값**: 구성되지 않음   
  BitLocker CSP: [Systemdrivesrecoveryoptions](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **사용** - 필요한 시작 정보를 사용할 수 없을 때 BitLocker로 보호된 운영 체제 드라이브를 복구하는 방법을 제어합니다.  
  - **구성되지 않음** - BitLocker 복구에 대한 기본 복구 옵션이 지원됩니다. 기본적으로 DRA가 허용되며, 사용자가 복구 암호와 복구 키를 포함한 복구 옵션을 선택하고, 복구 정보는 AD DS에 백업되지 않습니다.  

  ‘사용’으로 설정하면 다음 설정을 구성할 수 있습니다.   

  - **인증서 기반 데이터 복구 에이전트**  
    **기본값**: 구성되지 않음  
     
    - **차단** -BitLocker로 보호 되는 OS 드라이브에서 데이터 복구 에이전트 사용을 방지 합니다.  
    - **구성 되지 않음** -데이터 복구 에이전트를 BitLocker로 보호 된 운영 체제 드라이브와 함께 사용할 수 있습니다.  

  - **사용자의 복구 암호 생성**  
    **기본값**: 48 자리 복구 암호 허용  

    사용자가 48자리 복구 암호를 생성하도록 허용하는지, 허용하지 않는지 또는 요구하는지를 선택합니다.  
    - **48 자리 복구 암호 허용**  
    - **48 자리 복구 암호 허용 안 함**  
    - **48 자리 복구 암호 필요**  

  - **사용자의 복구 키 생성**  
    **기본값**: 256 비트 복구 키 허용  

    사용자가 256비트 복구 키를 생성하도록 허용하는지, 허용하지 않는지 또는 요구하는지를 선택합니다.  
    - **256 비트 복구 키 허용**  
    - **256 비트 복구 키 허용 안 함**  
    - **256 비트 복구 키 필요**  

  - **BitLocker 설치 마법사의 복구 옵션**  
    **기본값**: 구성되지 않음  

    - **차단** - 사용자가 복구 옵션을 보고 변경할 수 없습니다. 로 설정 되 면 
    - **구성되지 않음** - 사용자가 BitLocker를 설정할 때 복구 옵션을 표시하거나 변경할 수 있습니다. 
 
  - **Azure Active Directory에 BitLocker 복구 정보 저장**  
    **기본값**: 구성되지 않음  

    - **사용** - BitLocker 복구 정보를 Azure AD(Azure Active Directory)에 저장합니다.  
    - **구성 되지 않음** -BitLocker 복구 정보가 AAD에 저장 되지 않습니다.  

  - **Azure Active Directory에 저장 된 BitLocker 복구 정보**  
    **기본값**: 백업 복구 암호 및 키 패키지  

    Azure AD에 저장되는 BitLocker 복구 정보 부분을 구성합니다. 다음 중에서 선택합니다.  
    - **백업 복구 암호 및 키 패키지**  
    - **백업 복구 암호만**  

  - **클라이언트 기반 복구 암호 순환**  
    **기본값**: Azure AD 조인 장치에 대해 키 회전이 사용 됩니다.  
    BitLocker CSP: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    이 설정은 OS 드라이브 복구 후 (bootmgr 또는 WinRE를 사용 하 여) 클라이언트 기반 복구 암호 순환을 시작 합니다.  

    - 구성되지 않음  
    - 키 회전 사용 안 함  
    - Azure AD 조인 장치에 대해 키 회전이 사용 됩니다.  
    - Azure AD 및 하이브리드 조인 장치에 대해 키 회전이 사용 됩니다.  

  - **BitLocker를 사용 하도록 설정 하기 전에 Azure Active Directory에 복구 정보 저장**  
    **기본값**: 구성되지 않음  
 
     컴퓨터에서 Azure Active Directory에 BitLocker 복구 정보를 성공적으로 백업 하지 않으면 사용자가 BitLocker를 사용 하지 못하도록 합니다.  

    - **필요** - BitLocker 복구 정보가 Azure AD에 성공적으로 저장되지 않으면 사용자가 BitLocker를 설정할 수 없습니다.  
    - **구성되지 않음** - 복구 정보가 Azure AD에 성공적으로 저장되지 않는 경우에도 사용자가 BitLocker를 설정할 수 있습니다.  

- **부팅 전 복구 메시지 및 URL**  
  **기본값**: 구성되지 않음  
  BitLocker CSP: [Systemdrivesrecoverymessage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **사용** -부팅 전 키 복구 화면에 표시 되는 메시지와 URL을 구성 합니다.  
  - **구성되지 않음** - 이 기능이 사용되지 않습니다.  
  
  ‘사용’으로 설정하면 다음 설정을 구성할 수 있습니다.   
  - **부팅 전 복구 메시지**  
    **기본값**: 기본 복구 메시지 및 URL 사용   
 
    부팅 전 복구 메시지가 사용자에게 표시되는 방법을 구성합니다. 다음 중에서 선택합니다.  
    - **기본 복구 메시지 및 URL 사용**  
    - **빈 복구 메시지 및 URL 사용**  
    - **사용자 지정 복구 메시지 사용**  
    - **사용자 지정 복구 URL 사용**  

### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 고정 데이터 드라이브 설정  

이러한 설정은 고정 데이터 드라이브에만 적용 됩니다.  

- **BitLocker로 보호되지 않는 고정식 데이터 드라이브에 대한 쓰기 액세스**  
  **기본값**: 구성되지 않음  
  BitLocker CSP: [Fixed드라이브 Esrequireencryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **차단** - BitLocker로 보호되지 않는 데이터 드라이브에 대한 읽기 전용 액세스 권한을 부여합니다.  
  - **구성 되지 않음** -기본적으로 암호화 되지 않은 데이터 드라이브에 대 한 읽기 및 쓰기 액세스입니다.  

- **고정식 드라이브 복구**  
  **기본값**: 구성되지 않음  
  BitLocker CSP: [Fixed드라이브 Esrecoveryoptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **사용** - 필요한 시작 정보를 사용할 수 없을 때 BitLocker로 보호된 고정식 드라이브를 복구하는 방법을 제어할 수 있습니다.  
  - **구성되지 않음** - 이 기능이 사용되지 않습니다.  

  ‘사용’으로 설정하면 다음 설정을 구성할 수 있습니다.   

  - **데이터 복구 에이전트**  
    **기본값**: 구성되지 않음  
 
    - **차단** - BitLocker로 보호된 고정식 드라이브 정책 편집기에서 데이터 복구 에이전트를 사용할 수 없습니다. 
    - **구성되지 않음** - BitLocker로 보호된 고정식 드라이브에서 데이터 복구 에이전트를 사용할 수 있도록 합니다.  

  - **사용자의 복구 암호 생성**  
    **기본값**: 48 자리 복구 암호 허용  

    사용자가 48자리 복구 암호를 생성하도록 허용하는지, 허용하지 않는지 또는 요구하는지를 선택합니다.  
    - **48 자리 복구 암호 허용**  
    - **48 자리 복구 암호 허용 안 함**  
    - **48 자리 복구 암호 필요**  

  - **사용자의 복구 키 생성**  
    **기본값**: 256 비트 복구 키 허용

    사용자가 256비트 복구 키를 생성하도록 허용하는지, 허용하지 않는지 또는 요구하는지를 선택합니다.
    - **256 비트 복구 키 허용**  
    - **256 비트 복구 키 허용 안 함**  
    - **256 비트 복구 키 필요**  

  - **BitLocker 설치 마법사의 복구 옵션**  
    **기본값**: 구성되지 않음  

    - **차단** - 사용자가 복구 옵션을 보고 변경할 수 없습니다. 로 설정 되 면 
    - **구성되지 않음** - 사용자가 BitLocker를 설정할 때 복구 옵션을 표시하거나 변경할 수 있습니다.
 
  - **Azure Active Directory에 BitLocker 복구 정보 저장**  
    **기본값**: 구성되지 않음  

    - **사용** - BitLocker 복구 정보를 Azure AD(Azure Active Directory)에 저장합니다.  
    - **구성 되지 않음** -BitLocker 복구 정보가 AAD에 저장 되지 않습니다.

  - **Azure Active Directory에 저장 된 BitLocker 복구 정보**  
    **기본값**: 백업 복구 암호 및 키 패키지  

    Azure AD에 저장되는 BitLocker 복구 정보 부분을 구성합니다. 다음 중에서 선택합니다.  
    - **백업 복구 암호 및 키 패키지**  
    - **백업 복구 암호만**  

  - **클라이언트 기반 복구 암호 순환**  
    **기본값**: Azure AD 조인 장치에 대해 키 회전이 사용 됩니다.  
    BitLocker CSP: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    이 설정은 OS 드라이브 복구 후 (bootmgr 또는 WinRE를 사용 하 여) 클라이언트 기반 복구 암호 순환을 시작 합니다.  

    - 구성되지 않음  
    - 키 회전 사용 안 함  
    - Azure AD 조인 장치에 대해 키 회전이 사용 됩니다.  
    - Azure AD 및 하이브리드 조인 장치에 대해 키 회전이 사용 됩니다.  

  - **BitLocker를 사용 하도록 설정 하기 전에 Azure Active Directory에 복구 정보 저장**  
    **기본값**: 구성되지 않음  
 
    컴퓨터에서 Azure Active Directory에 BitLocker 복구 정보를 성공적으로 백업 하지 않으면 사용자가 BitLocker를 사용 하지 못하도록 합니다.  

    - **필요** - BitLocker 복구 정보가 Azure AD에 성공적으로 저장되지 않으면 사용자가 BitLocker를 설정할 수 없습니다.  
    - **구성되지 않음** - 복구 정보가 Azure AD에 성공적으로 저장되지 않는 경우에도 사용자가 BitLocker를 설정할 수 있습니다.  

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 이동식 데이터 드라이브 설정  

이러한 설정은 이동식 데이터 드라이브에만 적용 됩니다.  

- **BitLocker로 보호되지 않는 이동식 데이터 드라이브에 대한 쓰기 액세스**  
  **기본값**: 구성되지 않음  
  BitLocker CSP: [Removable드라이브 Esrequireencryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **차단** - BitLocker로 보호되지 않는 데이터 드라이브에 대한 읽기 전용 액세스 권한을 부여합니다.  
  - **구성 되지 않음** -기본적으로 암호화 되지 않은 데이터 드라이브에 대 한 읽기 및 쓰기 액세스입니다.  

  ‘사용’으로 설정하면 다음 설정을 구성할 수 있습니다.   

  - **다른 조직에서 구성된 디바이스에 대한 쓰기 액세스**  
    **기본값**: 구성되지 않음  

    - **차단** - 다른 조직에서 구성된 디바이스에 대한 쓰기 액세스를 허용합니다.  
    - **구성 되지 않음** -쓰기 액세스를 거부 합니다.  
 
## <a name="microsoft-defender-exploit-guard"></a>Microsoft Defender Exploit Guard  

[악용 방지](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) 를 사용 하 여 직원이 사용 하는 앱의 공격 노출 영역을 관리 하 고 줄일 수 있습니다.  

### <a name="attack-surface-reduction"></a>공격 노출 영역 축소  

공격 노출 영역 축소 규칙은 맬웨어가 악성 코드를 사용 하 여 컴퓨터를 감염 시키는 데 자주 사용 하는 행위를 방지 합니다.  

#### <a name="attack-surface-reduction-rules"></a>공격 노출 영역 축소 규칙  

- **Windows 로컬 보안 기관 하위 시스템에서 도용하는 자격 증명에 플래그 지정**  
  **기본값**: 구성되지 않음  
  규칙: [Windows 로컬 보안 기관 하위 시스템(lsass.exe)에서 도용하는 자격 증명에 플래그를 지정합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe)

  악용 검색 맬웨어가 컴퓨터를 감염시키는 데 일반적으로 사용되는 작업과 앱을 방지합니다.  

  - **구성되지 않음**  
  - **사용** - Windows 로컬 보안 기관 하위 시스템(lsass.exe)에서 도용하는 자격 증명에 플래그를 지정합니다.  
  - **감사만**  

- **Adobe Reader에서 프로세스 만들기 (베타)**  
  **기본값**: 구성되지 않음  
  규칙: [Adobe Reader에서 자식 프로세스를 만들지 못하도록 차단](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)  

  - **구성되지 않음**  
  - **사용** -Adobe Reader에서 만든 자식 프로세스를 차단 합니다.  
  - **감사만**  

#### <a name="rules-to-prevent-office-macro-threats"></a>Office 매크로 위협을 방지하는 규칙  

Office 앱에서 다음 작업을 수행하지 못하도록 차단합니다.  

- **다른 프로세스에 삽입되는 Office 앱(예외 없음)**  
  **기본값**: 구성되지 않음  
  규칙: [Office 애플리케이션이 다른 프로세스에 코드를 삽입하지 못하도록 차단합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes)  

  - **구성되지 않음**  
  - **블록** Office 앱이 다른 프로세스에 삽입 하지 못하도록 차단 합니다.  
  - **감사만**  

- **실행 가능 콘텐츠를 만드는 Office 앱/매크로**  
  **기본값**: 구성되지 않음  
  규칙: [Office 애플리케이션이 실행 가능한 콘텐츠를 생성하지 못하도록 차단합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content)  

  - **구성되지 않음**  
  - **블록** -Office 앱 및 매크로가 실행 가능 콘텐츠를 만들지 못하도록 차단 합니다.  
  - **감사만**  

- **자식 프로세스를 실행하는 Office 앱**  
  **기본값**: 구성되지 않음  
  규칙: [모든 Office 애플리케이션에서 하위 프로세스 생성 차단](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)  

  - **구성되지 않음**  
  - **블록** -Office 앱이 자식 프로세스를 시작 하지 못하도록 차단 합니다.  
  - **감사만**  
  
- **Office 매크로 코드에서 Win32 가져오기**  
  **기본값**: 구성되지 않음  
  규칙: [Office 매크로에서 Win32 API 호출을 차단합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros)  

  - **구성되지 않음**  
  - **블록** -Office의 매크로 코드에서 Win32 가져오기를 차단 합니다.  
  - **감사만**  
  
- **Office 통신 제품에서 프로세스 만들기**  
  **기본값**: 구성되지 않음  
  규칙: [Office 통신 응용 프로그램이 자식 프로세스를 만들지 못하도록 차단](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)  

  - **구성되지 않음**  
  - **사용** -Office 통신 앱에서 자식 프로세스 만들기를 차단 합니다.  
  - **감사만**  

#### <a name="rules-to-prevent-script-threats"></a>스크립트 위협을 방지하는 규칙  

스크립트 위협을 방지하기 위해 다음 항목을 차단합니다.  

- **난독 처리된 js/vbs/ps/매크로 코드**  
  **기본값**: 구성되지 않음  
  규칙: [잠재적으로 난독 처리된 스크립트가 실행되지 못하도록 차단합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts)    

  - **구성되지 않음**  
  - **Block** -난독 처리 된 js/vbs/ps/매크로 코드를 차단 합니다.  
  - **감사만**  

- **인터넷에서 다운로드된 페이로드를 실행하는 js/vbs(예외 없음)**  
  **기본값**: 구성되지 않음  
  규칙: [JavaScript 또는 VBScript가 다운로드된 실행 가능한 콘텐츠를 시작하지 못하도록 차단합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content)  

  - **구성되지 않음**  
  - **블록** -인터넷에서 다운로드 된 페이로드를 실행 하는 것을 차단 합니다.  
  - **감사만**  

- **PSExec 및 WMI 명령에서 프로세스 만들기**  
  **기본값**: 구성되지 않음  
  규칙: [PSExec 및 WMI 명령에서 발생하는 프로세스 만들기를 차단합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)  

  - **구성되지 않음**  
  - **차단** - PSExec 및 WMI 명령에서 발생하는 프로세스 만들기를 차단합니다.  
  
  - **감사만**  

- **USB에서 실행되는 신뢰할 수 없고 서명되지 않은 프로세스**  
  **기본값**: 구성되지 않음  
  규칙: [USB에서 실행되는 신뢰할 수 없고 서명되지 않은 프로세스를 차단합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb)    

  - **구성되지 않음**  
  - **차단** - USB에서 실행되는 신뢰할 수 없고 서명되지 않은 프로세스를 차단합니다.  
  - **감사만**  
  
- **전파, 처리 기간 또는 신뢰할 수 있는 목록 조건을 충족하지 않는 실행 파일**  
  **기본값**: 구성되지 않음  
  규칙: [실행 파일이 출현율, 나이 또는 신뢰할 수 있는 목록 기준을 충족하지 않으면 실행을 차단합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)    

  - **구성되지 않음**  
  - **차단** - 실행 파일이 출현율, 나이 또는 신뢰할 수 있는 목록 기준을 충족하지 않으면 실행을 차단합니다.  
  - **감사만**  

#### <a name="rules-to-prevent-email-threats"></a>이메일 위협을 방지하는 규칙  

이메일 위협을 방지하기 위해 다음 항목을 차단합니다.  

- **이메일(웹 메일/메일 클라이언트)에서 삭제된 실행 파일 콘텐츠(exe, dll, ps, js, vbs 등)의 실행(예외 없음)**  
  **기본값**: 구성되지 않음  
  규칙: [이메일 클라이언트 및 웹 메일에서 실행 가능한 콘텐츠를 차단합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail)  

  - **구성되지 않음**  
  - **차단** - 메일(웹 메일/메일 클라이언트)에서 삭제된 실행 파일 콘텐츠(exe, dll, ps, js, vbs 등)의 실행을 차단합니다.  
  - **감사만**  

#### <a name="rules-to-protect-against-ransomware"></a>랜섬웨어로부터 보호하기 위한 규칙  

- **고급 랜섬웨어 보호**  
  기본값: 구성되지 않음  
  규칙: [랜섬웨어로부터 고급 보호 기능을 사용합니다](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware)  

  - **구성되지 않음**  
  - **사용** - 적극적인 랜섬웨어 보호를 사용합니다.  
  - **감사만**  

#### <a name="attack-surface-reduction-exceptions"></a>공격 노출 영역 축소 예외

- **공격 노출 영역 축소 규칙에서 제외할 파일 및 폴더**  
  Defender CSP: [AttackSurfaceReductionOnlyExclusions](https://go.microsoft.com/fwlink/?linkid=872981)  

  - 공격 노출 영역 축소 규칙에서 제외할 파일 및 폴더를 포함 하는 .csv 파일을 **가져옵니다** .  
  - 로컬 파일 또는 폴더를 수동으로 **추가** 합니다.  

> [!IMPORTANT]  
> LOB Win32 앱을 올바르게 설치하고 실행하도록 허용하려면 다음 디렉터리를 검사 대상에서 제외해야 합니다.  
> **X64 클라이언트 머신**:  
> *C:\Program Files(x86)\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  
>  
> **X86 클라이언트 머신**:  
> *C:\Program Files\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  

### <a name="controlled-folder-access"></a>폴더 액세스 제어  

랜섬웨어와 같은 악성 앱과 위협으로부터 [중요한 데이터를 보호](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/controlled-folders)합니다.  

- **폴더 보호**  
  **기본값**: 구성되지 않음  
  Defender CSP: [EnableControlledFolderAccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  인증되지 않은 앱이 파일 및 폴더를 무단으로 변경할 수 없도록 보호합니다.  

  - **구성되지 않음**  
  - **사용**  
  - **감사만**  
  - **디스크 수정 차단**  
  - **디스크 수정 감사**  

  구성 *되지 않은*구성을 선택 하면 다음을 구성할 수 있습니다.  
  - **보호 된 폴더에 대 한 액세스 권한이 있는 앱 목록**  
    Defender CSP: [ControlledFolderAccessAllowedApplications](https://go.microsoft.com/fwlink/?linkid=872616)  

    - 앱 목록이 포함 된 .csv 파일을 **가져옵니다** .  
    - 이 목록에 앱을 수동으로 **추가** 합니다.  

  - **보호 해야 하는 추가 폴더의 목록**  
    Defender CSP: [ControlledFolderAccessProtectedFolders](https://go.microsoft.com/fwlink/?linkid=872617)  

    - 폴더 목록이 포함 된 .csv 파일을 **가져옵니다** .  
    - 이 목록에 폴더를 수동으로 **추가** 합니다.  

### <a name="network-filtering"></a>네트워크 필터링  

모든 앱에서 IP 주소 또는 도메인에서 낮은 평판이로의 아웃 바운드 연결을 차단 합니다. 네트워크 필터링은 감사 및 차단 모드 모두에서 지원 됩니다.  

- **네트워크 보호**  
  **기본값**: 구성되지 않음  
  Defender CSP: [EnableNetworkProtection](https://go.microsoft.com/fwlink/?linkid=872618)  

  이 설정은 인터넷의 피싱 사기, 익스플로잇 호스팅 사이트 및 악성 콘텐츠에 대 한 액세스 권한이 있는 앱에서 최종 사용자를 보호 하는 데 목적이 있습니다. 또한 타사 브라우저에서 위험한 사이트에 연결할 수 없습니다.  

  - **구성되지 않음** - 이 기능이 사용되지 않습니다. 사용자와 앱이 위험한 도메인에 연결 하는 것을 차단 하지 않습니다. 관리자는 Microsoft Defender 보안 센터에서 이 작업을 확인할 수 없습니다.  
  - **사용** -네트워크 보호를 켜고 사용자 및 앱이 위험한 도메인에 연결 하지 못하도록 합니다. 관리자는 Microsoft Defender 보안 센터에서 이 작업을 확인할 수 있습니다.  
  - **감사만**:-사용자와 앱이 위험한 도메인에 연결 하지 못하도록 차단 되지 않습니다. 관리자는 Microsoft Defender 보안 센터에서 이 작업을 확인할 수 있습니다.  

### <a name="exploit-protection"></a>악용 방지  

- **XML 업로드**  
  **기본값**: *구성되지 않음*  

  악용 방지를 사용 하 여 [장치를 악용 하지 못하도록 보호](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)하려면 원하는 시스템 및 응용 프로그램 완화 설정이 포함 된 XML 파일을 만듭니다. XML 파일을 만드는 방법에는 다음 두 가지가 있습니다.  

  - *PowerShell* - *Get-ProcessMitigation*, *Set-ProcessMitigation* 및 *ConvertTo-ProcessMitigationPolicy* PowerShell cmdlet 중 하나 이상을 사용합니다. cmdlet은 완화 설정을 구성하고 이들의 XML 표현을 내보냅니다.  

  - *Microsoft Defender 보안 센터 UI* - Microsoft Defender 보안 센터에서 앱 및 브라우저 컨트롤을 클릭한 다음, 결과 화면의 아래쪽으로 스크롤하여 Exploit Protection을 찾습니다. 먼저 시스템 설정 및 프로그램 설정 탭을 사용하여 완화 설정을 구성합니다. 그런 다음 화면 아래쪽의 설정 내보내기 링크를 찾아서 해당 XML 표현을 내보냅니다.  

- **악용 방지 인터페이스의 사용자 편집**  
  **기본값**: 구성되지 않음  
  ExploitGuard CSP: [ExploitProtectionSettings](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **블록** -메모리, 제어 흐름 및 정책 제한을 구성할 수 있는 XML 파일을 업로드 합니다. XML 파일의 설정을 사용하여 애플리케이션의 악용을 방지할 수 있습니다.  
  - **구성 되지 않음** -사용자 지정 구성을 사용 하지 않습니다.  

## <a name="microsoft-defender-application-control"></a>Microsoft Defender 애플리케이션 제어  

에서 감사 해야 하거나 Microsoft Defender 응용 프로그램 제어에서 실행할 수 있도록 신뢰할 수 있는 추가 앱을 선택 합니다. Windows 구성 요소 및 모든 Windows 저장소 앱의 실행은 자동으로 신뢰할 수 있습니다.  


- **응용 프로그램 제어 코드 무결성 정책**  
  **기본값**: 구성되지 않음  
   CSP: [APPLOCKER csp](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **적용** -사용자의 장치에 대 한 응용 프로그램 제어 코드 무결성 정책을 선택 합니다.  
  
    디바이스에서 사용하도록 설정되면 애플리케이션 제어는 *적용*에서 *감사만*으로 모드를 변경할 때에만 해제될 수 있습니다. 모드를 *적용*에서 *구성하지 않음*으로 변경하면 애플리케이션 제어가 할당된 디바이스에 계속 적용됩니다.  

  - **구성 되지 않음** -장치에 응용 프로그램 제어가 추가 되지 않습니다. 그러나 이전에 추가 된 설정은 할당 된 장치에 계속 적용 됩니다. 
 
  - **감사 전용** -응용 프로그램이 차단 되지 않습니다. 모든 이벤트는 로컬 클라이언트의 로그에 기록 됩니다.  

## <a name="microsoft-defender-credential-guard"></a>Microsoft Defender Credential Guard  

Microsoft Defender Credential Guard는 자격 증명 도난 공격을 방어합니다. 권한 있는 시스템 소프트웨어만 액세스할 수 있도록 비밀을 격리합니다.  

- **Credential Guard**  
  **기본값**: 사용 안 함  
  [DeviceGuard CSP](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **사용 안 함** - 이전에 **UEFI 잠금 없이 사용** 옵션을 사용하여 설정한 경우 Credential Guard를 원격으로 해제합니다.  

  - **UEFI 잠금과 함께 사용** - 레지스트리 키 또는 그룹 정책을 사용하여 Credential Guard를 원격으로 사용할 수 있도록 합니다.  

    > [!NOTE]
    > 이 설정을 사용하고 나중에 Credential Guard를 사용하지 않으려는 경우 그룹 정책을 **사용 안 함**으로 설정해야 합니다. 그리고 각 컴퓨터에서 UEFI 구성 정보를 물리적으로 지웁니다. UEFI 구성이 지속되는 한, Credential Guard는 사용하도록 설정됩니다.  

  - **UEFI 잠금 없이 사용** - 그룹 정책을 사용하여 Credential Guard를 원격으로 사용할 수 없도록 합니다. 이 설정을 사용하는 디바이스에서는 Windows 10 버전 1511 이상을 실행 중이어야 합니다.  

  Credential Guard를 *사용하도록 설정*할 경우 다음 필수 기능도 사용하도록 설정됩니다.  
  
  - VBS(**가상화 기반 보안**)  
    다음에 다시 부팅하는 중에 켜집니다. 가상화 기반 보안은 Windows 하이퍼바이저를 사용하여 보안 서비스에 대한 지원을 제공합니다.  
  - **보안 부팅 및 직접 메모리 액세스**  
    VBS가 보안 부팅 및 DMA(직접 메모리 액세스) 보호를 통해 켜집니다. DMA 보호는 하드웨어 지원이 필요하며 올바르게 구성된 디바이스에서만 작동합니다.  

## <a name="microsoft-defender-security-center"></a>Microsoft Defender 보안 센터  

Microsoft Defender 보안 센터는 각각의 개별 기능에서 별도의 응용 프로그램 또는 프로세스로 작동합니다. 또한 알림 센터를 통해 알림을 표시합니다. 수집기 또는 단일 위치로 작동하여 상태를 확인하고 각 기능에 대한 일부 구성을 실행합니다. [Microsoft Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) 문서에서 자세히 알아보세요.  

### <a name="microsoft-defender-security-center-app-and-notifications"></a>Microsoft Defender 보안 센터 앱 및 알림  

Microsoft Defender 보안 센터 앱의 다양한 영역에 대한 최종 사용자 액세스를 차단합니다. 또한 섹션을 숨기면 관련 알림도 차단됩니다.  

- **바이러스 및 위협 방지**  
  **기본값**: 구성되지 않음  
  WindowsDefenderSecurityCenter CSP: [DisableVirusUI](https://go.microsoft.com/fwlink/?linkid=873662)  

  최종 사용자가 Microsoft Defender Security Center에서 바이러스 및 위협 방지 영역을 볼 수 있는지 여부를 구성 합니다. 이 섹션을 숨기면 바이러스 및 위협 방지와 관련 된 모든 알림도 차단 됩니다.  

  - **구성되지 않음**  
  - **숨기기**  

- **랜 섬 웨어 보호**  
  **기본값**: 구성되지 않음  
  WindowsDefenderSecurityCenter CSP: [HideRansomwareDataRecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  최종 사용자가 Microsoft Defender Security Center에서 랜 섬 웨어 보호 영역을 볼 수 있는지 여부를 구성 합니다. 이 섹션을 숨기면 랜 섬 웨어 보호와 관련 된 모든 알림도 차단 됩니다.  

  - **구성되지 않음**  
  - **숨기기**  

- **계정 보호**  
  **기본값**: 구성되지 않음  
  WindowsDefenderSecurityCenter CSP: [DisableAccountProtectionUI](https://go.microsoft.com/fwlink/?linkid=873666)  

  최종 사용자가 Microsoft Defender Security Center의 계정 보호 영역을 볼 수 있는지 여부를 구성 합니다. 이 섹션을 숨기면 계정 보호와 관련 된 모든 알림도 차단 됩니다.  

  - **구성되지 않음**  
  - **숨기기**  

- **방화벽 및 네트워크 보호**  
  **기본값**: 구성되지 않음  
  WindowsDefenderSecurityCenter CSP: [DisableNetworkUI](https://go.microsoft.com/fwlink/?linkid=873668)  

  최종 사용자가 Microsoft Defender 보안 센터에서 방화벽 및 네트워크 보호 영역을 볼 수 있는지 여부를 구성 합니다. 이 섹션을 숨기면 방화벽 및 네트워크 보호와 관련 된 모든 알림도 차단 됩니다.  

  - **구성되지 않음**  
  - **숨기기**  

- **앱 및 브라우저 제어**  
  **기본값**: 구성되지 않음  
  WindowsDefenderSecurityCenter CSP: [Disableappbrowserui](https://go.microsoft.com/fwlink/?linkid=873669)  

  최종 사용자가 Microsoft Defender 보안 센터에서 앱 및 브라우저 제어 영역을 볼 수 있는지 여부를 구성 합니다. 이 섹션을 숨기면 앱 및 브라우저 컨트롤과 관련 된 모든 알림도 차단 됩니다.  

  - **구성되지 않음**  
  - **숨기기**  

- **하드웨어 보호**  
  **기본값**: 구성되지 않음  
  WindowsDefenderSecurityCenter CSP: [DisableDeviceSecurityUI](https://go.microsoft.com/fwlink/?linkid=873670)  

  최종 사용자가 Microsoft Defender Security Center의 하드웨어 보호 영역을 볼 수 있는지 여부를 구성 합니다. 이 섹션을 숨기면 하드웨어 보호와 관련 된 모든 알림도 차단 됩니다.  

  - **구성되지 않음**  
  - **숨기기**  

- **디바이스 성능 및 상태**  
  **기본값**: 구성되지 않음  
  WindowsDefenderSecurityCenter CSP: [DisableHealthUI](https://go.microsoft.com/fwlink/?linkid=873671)  

  최종 사용자가 Microsoft Defender 보안 센터에서 장치 성능 및 상태 영역을 볼 수 있는지 여부를 구성 합니다. 이 섹션을 숨기면 장치 성능 및 상태와 관련 된 모든 알림도 차단 됩니다.  
  
  - **구성되지 않음**  
  - **숨기기**  

- **제품군 옵션**  
  **기본값**: 구성되지 않음  
  WindowsDefenderSecurityCenter CSP: [DisableFamilyUI](https://go.microsoft.com/fwlink/?linkid=873673)  

  최종 사용자가 Microsoft Defender 보안 센터에서 제품군 옵션 영역을 볼 수 있는지 여부를 구성 합니다. 이 섹션을 숨기면 제품군 옵션과 관련 된 모든 알림도 차단 됩니다.  
  
  - **구성되지 않음**  
  - **숨기기**  

- **앱 표시 영역의 알림**  
  **기본값**: 구성되지 않음  
  WindowsDefenderSecurityCenter CSP: [DisableNotifications](https://go.microsoft.com/fwlink/?linkid=873675)  

  최종 사용자에게 표시할 알림을 선택합니다. 중요하지 않은 알림에는 검색 완료 시 알림을 포함한 Microsoft Defender 바이러스 백신 활동의 요약이 포함됩니다. 다른 모든 알림은 중요 알림으로 간주합니다.  

  - **구성되지 않음**  
  - **중요 하지 않은 알림 차단**  
  - **모든 알림 차단**  

- **시스템 트레이의 Windows Security Center 아이콘**  
  **기본값**: 구성되지 않음  

  알림 영역 컨트롤의 표시를 구성 합니다. 사용자가 로그 아웃 하 고 로그인 하거나 컴퓨터를 다시 부팅 해야이 설정이 적용 됩니다.  
  
  - **구성되지 않음**  
  - **숨기기**  

- **TPM 지우기 단추**  
  **기본값**: 구성되지 않음  

  TPM 지우기 단추의 표시를 구성 합니다.  
  
  - **구성되지 않음**  
  - **사용 안 함**  

- **TPM 펌웨어 업데이트 경고**  
  **기본값**: 구성되지 않음  
  
  취약 한 펌웨어가 검색 되 면 업데이트 TPM 펌웨어 표시를 구성 합니다.  

  - **구성되지 않음**  
  - **숨기기**  

- **변조 방지**  
  **기본값**: 구성되지 않음

  장치에서 변조 방지 기능을 설정 하거나 해제 합니다. 변조 방지를 사용 하려면 [Microsoft Defender Advanced Threat Protection을 Intune과 통합](advanced-threat-protection.md)하 고 [Enterprise Mobility + Security E5 라이선스](../fundamentals/licenses.md)를 사용 해야 합니다.  
  - **구성 되지 않음** -장치 설정이 변경 되지 않습니다.
  - **사용** -변조 방지 기능이 설정 되 고 장치에 제한이 적용 됩니다.
  - **사용 안 함** -변조 방지 기능이 해제 되어 있으므로 제한이 적용 되지 않습니다.

### <a name="it-contact-information"></a>IT 연락처 정보  

Microsoft Defender 보안 센터 앱 및 앱 알림에 표시할 IT 연락처 정보를 제공합니다.  

**앱 및 알림에 표시**, **앱에만 표시**, **알림에만 표시** 또는 **표시 안 함**을 선택할 수 있습니다. **IT 조직 이름**과 다음 연락처 옵션 중 하나 이상을 입력합니다.  


- **IT 연락처 정보**  
  **기본값**: 표시 안 함  
  WindowsDefenderSecurityCenter CSP: [EnableCustomizedToasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  최종 사용자에 게 IT 연락처 정보를 표시할 위치를 구성 합니다.  
  
  - **앱 및 알림에 표시**  
  - **앱에만 표시**  
  - **알림에만 표시**  
  - **표시 안 함**  

  표시 하도록 구성 된 경우 다음 설정을 구성할 수 있습니다.  

  - **IT 조직 이름**  
    **기본값**: *구성되지 않음*  
    WindowsDefenderSecurityCenter CSP: [CompanyName](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **IT 부서 전화 번호 또는 Skype ID**  
    **기본값**: *구성되지 않음*  
    WindowsDefenderSecurityCenter CSP: [휴대폰](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **IT 부서 이메일 주소**  
    **기본값**: *구성되지 않음*  
    WindowsDefenderSecurityCenter CSP: [전자 메일](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **IT 지원 웹 사이트 URL**  
    **기본값**: *구성되지 않음*  
    WindowsDefenderSecurityCenter CSP: [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>로컬 디바이스 보안 옵션  

이러한 옵션을 사용하여 Windows 10 디바이스에서 로컬 보안 설정을 구성합니다.  

### <a name="accounts"></a>계정  

- **새 Microsoft 계정 추가**:  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **차단** 사용자가 새 Microsoft 계정을 디바이스에 추가할 수 없습니다.  
  - **구성 되지 않음** -사용자가 장치에서 Microsoft 계정을 사용할 수 있습니다.  

- **암호 없이 원격 로그온**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **차단** - 암호가 비어 있는 로컬 계정에서만 디바이스의 키보드를 사용하여 로그인할 수 있습니다.  
   - **구성되지 않음** - 암호가 비어 있는 로컬 계정에서 물리적 디바이스가 아닌 위치에서 로그인할 수 있습니다.  

#### <a name="admin"></a>관리자  

- **로컬 관리자 계정**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **블록** 로컬 관리자 계정을 사용 하지 않습니다.  
  - **구성되지 않음**  

- **관리자 계정 이름 바꾸기**  
  **기본값**: *구성되지 않음*  
  LocalPoliciesSecurityOptions CSP: [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  “Administrator” 계정의 SID(보안 ID)와 연결할 다른 계정 이름을 정의합니다.  

 #### <a name="guest"></a>게스트  

- **게스트 계정**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [LocalPoliciesSecurityOptions](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **차단** -게스트 계정의 사용을 금지 합니다.  
  - **구성되지 않음**  

- **게스트 계정 이름 바꾸기**  
  **기본값**: *구성되지 않음*  
  LocalPoliciesSecurityOptions CSP: [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  “Guest” 계정의 SID(보안 ID)와 연결할 다른 계정 이름을 정의합니다.  

### <a name="devices"></a>디바이스  

- **로그온 없이 디바이스 도킹 해제**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **차단** - 사용자가 도킹된 휴대용 디바이스의 물리적 꺼내기 단추를 눌러 디바이스를 안전하게 도킹 해제할 수 있습니다.  
  - **구성 되지 않음** -사용자가 장치에 로그인 하 고 장치를 도킹 해제할 수 있는 권한을 받아야 합니다.  

- **공유 프린터에 대한 프린터 드라이버 설치**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **사용** - 모든 사용자가 공유 프린터에 연결하는 일환으로 프린터 드라이버를 설치할 수 있습니다.  
  - **구성되지 않음** - 관리자만 공유 프린터에 연결하는 일환으로 프린터 드라이버를 설치할 수 있습니다.  

- **CD-ROM 액세스를 로컬 활성 사용자로 제한**  
  **기본값**: 구성되지 않음  
  CSP: [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **사용** - 대화형으로 로그온한 사용자만 CD-ROM 미디어를 사용할 수 있습니다. 이 정책을 사용하도록 설정하고 대화형으로 로그온하는 사용자가 없으면 네트워크를 통해 CD-ROM에 액세스할 수 있습니다.  
  - **구성 되지 않음** -누구나 cd-rom에 액세스할 수 있습니다.  

- **이동식 미디어 포맷 및 꺼내기**  
  **기본값**: 관리자  
  CSP: [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  이동식 NTFS 미디어를 포맷하고 꺼낼 수 있는 사용자를 정의합니다.  
  - **구성되지 않음**  
  - **관리자**  
  - **관리자 및 고급 사용자**  
  - **관리자 및 대화형 사용자**  

### <a name="interactive-logon"></a>대화형 로그온  

- **화면 보호기가 활성화될 때까지 잠금 화면 비활성 시간(분)**  
  **기본값**: *구성되지 않음*  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  대화형 데스크톱의 로그인 화면에서 화면 보호기가 시작될 때까지의 최대 비활성 시간(분)을 입력합니다. (**0** - **99999**)  

- **로그온하려면 Ctrl+Alt+Del을 눌러야 함**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **사용** - 사용자가 로그인할 때 Ctrl+Alt+Del을 누를 필요가 없습니다.  
  - **구성되지 않음** - 사용자가 먼저 Ctrl+Alt+Del을 눌러야 Windows에 로그온할 수 있습니다.  

- **스마트 카드 제거 동작**  
  **기본값**: 워크스테이션 잠금   
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  스마트 카드 판독기에서 로그온한 사용자의 스마트 카드를 제거할 때 수행되는 동작을 결정합니다. 옵션은 다음과 같습니다.  

  - **워크스테이션 잠금** - 스마트 카드를 제거하면 워크스테이션이 잠깁니다. 이 옵션을 사용하면 사용자가 해당 영역을 그대로 두고, 스마트 카드를 사용하고, 보호된 세션을 계속 유지할 수 있습니다.  
  - **작업 없음**  
  - **강제 로그오프** - 스마트 카드를 제거하면 사용자가 자동으로 로그오프됩니다.  
  - **원격 데스크톱 서비스 세션인 경우 연결 끊기** - 스마트 카드를 제거하면 사용자를 로그오프하지 않고 세션의 연결이 끊어집니다. 이 옵션을 사용하면 사용자가 다시 로그인하지 않고도 스마트 카드를 삽입하고, 나중에 세션을 다시 시작하거나 다른 스마트 카드 판독기가 장착된 컴퓨터에서 다시 시작할 수 있습니다. 세션이 로컬이면 이 정책은 워크스테이션 잠금과 동일하게 작동합니다.  

#### <a name="display"></a>표시  

- **잠금 화면의 사용자 정보**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  세션이 잠겨 있을 때 표시되는 사용자 정보를 구성합니다. 구성하지 않으면 사용자 표시 이름, 도메인 및 사용자 이름이 표시됩니다.  

  - **구성되지 않음**  
  - **사용자 표시 이름, 도메인 및 사용자 이름**  
  - **사용자 표시 이름만**  
  - **사용자 정보 표시 안 함**  

- **마지막으로 로그인한 사용자 숨기기**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **사용** -사용자 이름을 숨깁니다.  
  - **구성 되지 않음** -마지막 사용자 이름을 표시 합니다.  

- **로그인 시 사용자 이름 숨기기** 
  **기본값**: 구성 되지 않음  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **사용** -사용자 이름을 숨깁니다.  
  - **구성 되지 않음** -마지막 사용자 이름을 표시 합니다.  

- **로그온 메시지 제목**  
  **기본값**: *구성되지 않음*  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  로그인하는 사용자에 대한 메시지 제목을 설정합니다.  

- **로그온 메시지 텍스트**  
  **기본값**: *구성되지 않음*  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  로그인하는 사용자에 대한 메시지 텍스트를 설정합니다.  
  
### <a name="network-access-and-security"></a>네트워크 액세스 및 보안

- **명명된 파이프 및 공유에 대한 익명 액세스**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **구성되지 않음** - 공유 및 명명된 파이프 설정에 대한 익명 액세스를 제한합니다. 익명으로 액세스할 수 있는 설정에 적용됩니다.  
  - **차단** -이 정책을 사용 하지 않도록 설정 하 여 익명 액세스를 사용할 수 있도록 합니다.  

- **SAM 계정의 익명 열거**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **구성 되지 않음** -익명 사용자가 SAM 계정을 열거할 수 있습니다.  
  - **차단** - SAM 계정의 익명 열거를 방지합니다.  

- **SAM 계정 및 공유의 익명 열거**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **구성되지 않음** - 익명 사용자가 도메인 계정 및 네트워크 공유의 이름을 열거할 수 있음을 의미합니다.  
  - **차단** - SAM 계정 및 공유의 익명 열거를 차단합니다. 

- **암호 변경 시 LAN Manager 해시 값 저장됨**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  암호의 해시 값이 다음에 암호를 변경할 때 저장 되는지 여부를 결정 합니다. 
  - **구성 되지 않음** -해시 값이 저장 되지 않습니다.  
  - **블록** -LM (LAN Manager)은 새 암호에 대 한 해시 값을 저장 합니다.  

- **PKU2U 인증 요청**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **구성 되지 않음**-PU2U 요청을 허용 합니다.  
  - **블록** -장치에 대 한 PKU2U 인증 요청을 차단 합니다.  

- **원격 RPC 연결을 SAM으로 제한**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **구성 되지 않음** -사용자 및 그룹이 SAM에 대 한 원격 RPC 호출을 수행할 수 있는 기본 보안 설명자를 사용 합니다.
  - **허용** -사용자 및 그룹이 사용자 계정 및 암호를 저장 하는 SAM (보안 계정 관리자)에 대 한 원격 RPC 호출을 수행 하지 못하도록 합니다. 또한 **허용** 을 지정 하면 기본 SDDL (Security Descriptor Definition Language) 문자열을 변경 하 여 사용자와 그룹이 이러한 원격 호출을 수행 하도록 명시적으로 허용 하거나 거부할 수 있습니다.  

    - **보안 설명자**  
      **기본값**: *구성되지 않음*  
    
- **NTLM SSP 기반 클라이언트에 대한 최소 세션 보안**  
  **기본값**: 없음  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  이 보안 설정을 사용하면 서버에서는 128비트 암호화 및/또는 NTLMv2 세션 보안의 협상을 요구할 수 있습니다.  

  - **없음**  
  - **NTLMv2 세션 보안 필요**  
  - **128비트 암호화 필요**  
  - **NTLMv2 및 128비트 암호화 필요**.  
 
- **NTLM SSP 기반 서버에 대한 최소 세션 보안**  
  **기본값**: 없음  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  이 보안 설정은 네트워크 로그온에 사용되는 시도/응답 인증 프로토콜을 결정합니다.  

  - **없음**  
  - **NTLMv2 세션 보안 필요**  
  - **128비트 암호화 필요**  
  - **NTLMv2 및 128비트 암호화 필요**.  

- **LAN Manager 인증 수준**  
  **기본값**: LM 및 NTLM  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM 및 NTLM**  
  - **LM, NTLM 및 NTLMv2**  
  - **NTLM**  
  - **Nt**  
  - **LM이 아닌 NTLMv2**  
  - **LM 또는 NTLM이 아닌 NTLMv2**  
  
- **안전 하지 않은 게스트 로그온**  
  **기본값**: 구성되지 않음  
  LanmanWorkstation CSP: [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  이 설정을 사용 하도록 설정 하면 SMB 클라이언트는 보안 되지 않은 게스트 로그온을 거부 합니다.  

  - **구성되지 않음**  
  - **Block** -SMB 클라이언트는 안전 하지 않은 게스트 로그온을 거부 합니다.  

### <a name="recovery-console-and-shutdown"></a>복구 콘솔 및 종료  

- **종료할 때 가상 메모리 페이지 파일 지우기**  
  **기본값**: 구성되지 않음  
   LocalPoliciesSecurityOptions CSP: [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **사용** - 디바이스의 전원이 꺼질 때 가상 메모리 페이지 파일을 지웁니다.  
  - **구성되지 않음** - 가상 메모리를 지우지 않습니다.  

- **로그온 없이 종료**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **차단** - Windows 로그인 화면에서 종료 옵션을 숨깁니다. 사용자가 디바이스에 로그인한 후에 종료해야 합니다.  
  - **구성되지 않음** - 사용자가 Windows 로그인 화면에서 디바이스를 종료할 수 있습니다.  

### <a name="user-account-control"></a>사용자 계정 컨트롤  

- **안전한 위치 없는 UIA 무결성**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - **블록** -파일 시스템의 안전한 위치에 있는 앱은 UIAccess 무결성 으로만 실행 됩니다.  
  - **구성되지 않음** - 애플리케이션이 파일 시스템의 안전한 위치에 있지 않는 경우에도 UIAccess 무결성을 사용하여 실행될 수 있습니다.  

- **사용자별 위치로 파일 및 레지스트리 쓰기 오류 가상화**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **사용** - 데이터를 보호된 위치에 쓰는 애플리케이션이 실패합니다.  
  - **구성 안 함** - 애플리케이션 쓰기 오류는 런타임에 파일 시스템 및 레지스트리에 대해 정의된 사용자 위치로 리디렉션됩니다.  

- **서명되고 유효성이 검사된 실행 파일만 권한 상승**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **사용** - 실행 파일이 실행되기 전에 해당 파일에 대한 PKI 인증서 경로의 유효성 검사를 적용합니다.  
  - **구성되지 않음** - 실행 파일이 실행되기 전에 PKI 인증 경로 유효성 검사를 적용하지 않습니다.  

#### <a name="uia-elevation-prompt-behavior"></a>UIA 권한 상승 프롬프트 동작  

- **관리자에 대한 권한 상승 프롬프트**  
  **기본값**: 비 Windows 바이너리에 대한 동의 확인  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  관리자 승인 모드에서 관리자에 대한 권한 상승 프롬프트의 동작을 정의합니다.  

  - **구성되지 않음**  
  - **권한 상승 전에 확인 안 함**  
  - **보안된 데스크톱에서 자격 증명 확인**  
  - **자격 증명 확인**  
  - **동의 확인**  
  - **Windows 이외의 바이너리에 대한 동의 요청**  


- **표준 사용자에 대한 권한 상승 프롬프트**  
  **기본값**: 자격 증명 요청  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  표준 사용자에 대한 권한 상승 프롬프트의 동작을 정의합니다.  

  - **구성되지 않음**  
  - **권한 상승 요청 자동으로 거부**  
  - **보안된 데스크톱에서 자격 증명 확인**  
  - **자격 증명 확인**  

- **사용자의 대화형 데스크톱으로 권한 상승 프롬프트 라우팅**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - **사용** -보안 된 데스크톱이 아닌 대화형 사용자의 데스크톱으로 이동 하는 모든 권한 상승 요청 관리자 및 표준 사용자에 대한 모든 프롬프트 동작 정책 설정이 사용됩니다.  
  - **구성되지 않음** - 관리자 및 표준 사용자에 대한 프롬프트 동작 정책 설정에 관계없이 모든 권한 상승 요청이 보안된 데스크톱으로 이동하도록 합니다.

- **앱 설치에 대한 관리자 권한 프롬프트**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **사용** - 애플리케이션 설치 패키지가 검색되지 않거나 권한 상승을 묻는 메시지가 표시됩니다.
   - **구성되지 않음** - 애플리케이션 설치 패키지에 상승된 권한이 필요할 때 관리 사용자 이름과 암호를 요구하는 메시지가 사용자에게 표시됩니다.

- **보안된 데스크톱 없는 UIA 권한 상승 프롬프트**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **사용** - UIAccess 애플리케이션에서 보안 데스크톱을 사용하지 않고도 권한 상승을 요구하는 메시지를 표시할 수 있습니다.  
- **구성 되지 않음** -권한 상승 프롬프트는 보안 된 데스크톱을 사용 합니다.  

#### <a name="admin-approval-mode"></a>관리자 승인 모드  

- **기본 제공 관리자에 대한 관리자 승인 모드**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **사용** - 기본 제공 관리자 계정에서 관리자 승인 모드를 사용할 수 있습니다. 권한 상승이 필요한 작업에서는 사용자에게 작업을 승인하도록 요구하는 메시지가 표시됩니다.  
  - **구성되지 않음** - 모든 앱이 모든 관리자 권한으로 실행됩니다.  

- **관리자 승인 모드에서 모든 관리자 실행**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - **사용**-관리자 승인 모드를 사용 하도록 설정 합니다.  
  - **구성되지 않음** - 관리자 승인 모드와 모든 관련 UAC 정책 설정을 사용하지 않도록 설정합니다.  

### <a name="microsoft-network-client"></a>Microsoft 네트워크 클라이언트  

- **통신에 디지털 서명(서버가 동의한 경우)**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  SMB 클라이언트에서 SMB 패킷 서명을 협상하는지 여부를 결정합니다.  
  - **Block** -smb 클라이언트는 smb 패킷 서명을 협상 하지 않습니다.
  - **구성되지 않음** - Microsoft 네트워크 클라이언트에서 세션 설정 시 SMB 패킷 서명을 실행하도록 서버에 요청합니다. 서버에서 패킷 서명을 사용하도록 설정되면 패킷 서명이 협상됩니다.  

- **암호화되지 않은 암호를 타사 SMB 서버로 보내기**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **차단** - SMB(서버 메시지 블록) 리디렉터에서 인증 중에 암호 암호화를 지원하지 않는 타사 SMB 서버에 일반 텍스트 암호를 보낼 수 있습니다.  
  - **구성 되지 않음** -일반 텍스트 암호 보내기를 차단 합니다. 암호는 암호화 됩니다.  

- **통신에 디지털 서명(항상)**  
  **기본값**: 구성되지 않음  
  LocalPoliciesSecurityOptions CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **사용** - Microsoft 네트워크 서버에서 SMB 패킷 서명에 동의하지 않는 한, Microsoft 네트워크 클라이언트에서 서버와 통신하지 않습니다.  
  - **구성 되지 않음** -클라이언트와 서버 간에 SMB 패킷 서명이 협상 됩니다.  

### <a name="microsoft-network-server"></a>Microsoft 네트워크 서버  
  
- **통신에 디지털 서명(클라이언트가 동의한 경우)**  
  **기본값**: 구성되지 않음  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **사용** - Microsoft 네트워크 서버는 클라이언트가 요청한 대로 SMB 패킷 서명을 협상합니다. 즉, 클라이언트에서 패킷 서명이 사용 가능한 경우, 패킷 서명이 협상됩니다.  
  - **구성 되지 않음** -smb 클라이언트는 smb 패킷 서명을 협상 하지 않습니다.  

- **통신에 디지털 서명(항상)**  
  **기본값**: 구성되지 않음  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **사용** - Microsoft 네트워크 클라이언트에서 SMB 패킷 서명에 동의하지 않는 한 Microsoft 네트워크 서버에서 해당 클라이언트와 통신하지 않습니다.  
  - **구성 되지 않음** -클라이언트와 서버 간에 SMB 패킷 서명이 협상 됩니다.  

## <a name="xbox-services"></a>Xbox 서비스

- **Xbox 게임 저장 작업**  
  **기본값**: 구성되지 않음  
  CSP: [TaskScheduler/EnableXboxGameSaveTask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  이 설정은 Xbox 게임 저장 작업을 사용 하거나 사용 하지 않도록 설정할지 여부를 결정 합니다.  
  - **Enabled**
  - **구성되지 않음**

- **Xbox 액세서리 관리 서비스**  
  **기본값**: 수동  
  CSP: [Systemservices/ConfigureXboxAccessoryManagementServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875481)  

  이 설정은 보조 관리 서비스의 시작 유형을 결정 합니다.  
  - **수동**
  - **자동**
  - **사용 안 함**

- **Xbox Live Auth Manager 서비스**  
  **기본값**: 수동  
  CSP: [Systemservices/ConfigureXboxLiveAuthManagerServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  이 설정은 라이브 Auth Manager 서비스의 시작 유형을 결정 합니다.  
  - **수동**
  - **자동**
  - **사용 안 함**
 
- **Xbox Live 게임 저장 서비스**  
  **기본값**: 수동  
  CSP: [Systemservices/ConfigureXboxLiveGameSaveServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875483)  

  이 설정은 Live Game 저장 서비스의 시작 유형을 결정 합니다.  
  - **수동**
  - **자동**
  - **사용 안 함**

- **Xbox Live 네트워킹 서비스**  
  **기본값**: 수동  
  CSP: [Systemservices/ConfigureXboxLiveNetworkingServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875484)  

  이 설정은 네트워킹 서비스의 시작 유형을 결정 합니다.  
  - **수동**
  - **자동**
  - **사용 안 함**

## <a name="user-rights"></a>사용자 권한

- **신뢰할 수 있는 호출자로 액세스 자격 증명 관리자**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/AccessCredentialManagerAsTrustedCaller](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-accesscredentialmanagerastrustedcaller)

  이 사용자 권한은 백업 및 복원 작업 중에 자격 증명 관리자에서 사용 됩니다. 이 권한이 다른 엔터티에 부여 되 면 사용자가 저장 한 자격 증명이 손상 될 수 있습니다.
  - **구성되지 않음**
  - **허용**

- **로컬 로그온 허용**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/AllowLocalLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-allowlocallogon)

  이 사용자 권한은 컴퓨터에 로그온 할 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **네트워크에서 액세스 허용**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/AccessFromNetwork](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-accessfromnetwork)

  이 사용자 권한은 네트워크를 통해 컴퓨터에 연결할 수 있는 사용자 및 그룹을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **운영 체제의 일부로 작동**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/ActAsPartOfTheOperatingSystem](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-actaspartoftheoperatingsystem)

  운영 체제의 일부로 작동
  - **구성되지 않음**
  - **허용**  

- **파일 및 디렉터리 백업**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/BackupFilesAndDirectories](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-backupfilesanddirectories)

  이 사용자 권한은 파일 및 디렉터리를 백업할 때 파일, 디렉터리, 레지스트리 및 기타 영구 개체 사용 권한을 무시할 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **시스템 시간 변경**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/ChangeSystemTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-changesystemtime)

  이 사용자 권한은 컴퓨터의 내부 클록에서 시간 및 날짜를 변경할 수 있는 사용자 및 그룹을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **전역 개체 만들기**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/CreateGlobalObjects](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createglobalobjects)

  이 보안 설정은 사용자가 모든 세션에서 사용할 수 있는 전역 개체를 만들 수 있는지 여부를 결정 합니다. 전역 개체를 만들 수 있는 사용자는 다른 사용자의 세션에서 실행 되는 프로세스에 영향을 줄 수 있으므로 응용 프로그램 오류나 데이터 손상을 초래할 수 있습니다.
  - **구성되지 않음**
  - **허용**

- **페이지 파일 만들기**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/CreatePageFile](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createpagefile)

  이 사용자 권한은 내부 API를 호출 하 여 페이지 파일의 크기를 만들고 변경할 수 있는 사용자 및 그룹을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **영구 공유 개체 만들기**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/CreatePermanentSharedObjects](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createpermanentsharedobjects)

  이 사용자 권한은 프로세스에서 개체 관리자를 사용 하 여 디렉터리 개체를 만드는 데 사용할 수 있는 계정을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **기호 링크 만들기**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/CreateSymbolicLinks](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createsymboliclinks)

  이 사용자 권한은 사용자가 로그온 한 컴퓨터에서 바로 가기 링크를 만들 수 있는지 여부를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **토큰 만들기**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/메서드인 appserviceloginhandler.createtoken](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createtoken)

  이 사용자 권한은 프로세스에서 내부 API를 사용 하 여 액세스 토큰을 만들 때 모든 로컬 리소스에 대 한 액세스 권한을 얻는 데 사용할 수 있는 토큰을 만드는 프로세스에서 사용할 수 있는 사용자/그룹을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **프로그램 디버그**  
  **기본값**: 구성되지 않음  
    CSP: [Userrights/DebugPrograms](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-debugprograms)

  이 사용자 권한은 디버거를 프로세스나 커널에 연결할 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **네트워크에서 액세스 거부**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/DenyAccessFromNetwork](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denyaccessfromnetwork)

  이 사용자 권한은 네트워크를 통해 컴퓨터에 액세스할 수 없는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **서비스로 로그온 거부**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/DenyLocalLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denylocallogon)

  이 보안 설정은 프로세스를 서비스로 등록할 수 없도록 하는 서비스 계정을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **원격 데스크톱 서비스를 통한 로그온 거부**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/DenyRemoteDesktopServicesLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denyremotedesktopserviceslogon)

  이 사용자 권한은 원격 데스크톱 서비스 클라이언트로 로그온 할 수 없는 사용자 및 그룹을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **위임 사용**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/EnableDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-enabledelegation)

 이 사용자 권한은 사용자 또는 컴퓨터 개체에서 위임용으로 트러스트 된 사용자를 설정할 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **보안 감사 생성**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/GenerateSecurityAudits](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-generatesecurityaudits)

  이 사용자 권한은 프로세스에서 보안 로그에 항목을 추가 하는 데 사용할 수 있는 계정을 결정 합니다. 보안 로그는 권한이 없는 시스템 액세스를 추적 하는 데 사용 됩니다.
  - **구성되지 않음**
  - **허용**

- **클라이언트 가장**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/ImpersonateClient](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-impersonateclient)

  사용자에 게이 사용자 권한을 할당 하면 해당 사용자 대신 실행 되는 프로그램에서 클라이언트를 가장할 수 있습니다. 이러한 종류의 가장에 대해이 사용자 권한을 요구 하면 권한이 없는 사용자가 클라이언트를 속여 사용자가 만든 서비스에 연결 하 여 해당 클라이언트를 가장 하는 것을 방지할 수 있습니다. 이렇게 하면 권한이 없는 사용자의 권한을 상승 시킬 수 있습니다. 관리 또는 시스템 수준
  - **구성되지 않음**
  - **허용**

- **예약 우선 순위 증가**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/IncreaseSchedulingPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-increaseschedulingpriority)

  이 사용자 권한은 다른 프로세스에 할당 된 실행 우선 순위를 높이기 위해 다른 프로세스에 대 한 쓰기 속성 액세스 권한이 있는 프로세스를 사용할 수 있는 계정을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **디바이스 드라이버 로드 및 언로드**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/LoadUnloadDeviceDrivers](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-loadunloaddevicedrivers)

  이 사용자 권한은에서 커널 모드로 장치 드라이버 또는 기타 코드를 동적으로 로드 하 고 언로드할 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **메모리의 페이지 잠금**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/LockMemory](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-lockmemory)

  이 사용자 권한 데이터를 실제 메모리에 유지하는 프로세스를 사용하여 시스템이 디스크의 가상 메모리로 데이터를 페이징하지 않도록 방지할 수 있는 계정을 결정합니다.
  - **구성되지 않음**
  - **허용**

- **감사 및 보안 로그 관리**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/ManageAuditingAndSecurityLog](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-manageauditingandsecuritylog)

  이 사용자 권한은 파일, Active Directory 개체 및 레지스트리 키와 같은 개별 리소스에 대 한 개체 액세스 감사 옵션을 지정할 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **볼륨 유지 관리 작업 수행**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/ManageVolume](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-managevolume)

  이 사용자 권한은 볼륨에서 유지 관리 작업을 실행할 수 있는 사용자 및 그룹 (예: 원격 조각 모음)을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **펌웨어 환경 값 수정**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/ModifyFirmwareEnvironment](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-modifyfirmwareenvironment)

  이 사용자 권한은 펌웨어 환경 값을 수정할 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **개체 레이블 수정**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/ModifyObjectLabel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-modifyobjectlabel)

  이 사용자 권한은 파일, 레지스트리 키 또는 다른 사용자가 소유한 프로세스와 같은 개체의 무결성 레이블을 수정할 수 있는 사용자 계정을 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **단일 프로세스 프로파일링**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/프로필 Ingleprocess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-profilesingleprocess)

  이 사용자 권한은 성능 모니터링 도구를 사용 하 여 시스템 프로세스의 성능을 모니터링할 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

- **원격 종료**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/RemoteShutdown](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-remoteshutdown)

  이 사용자 권한은 네트워크의 원격 위치에서 컴퓨터를 종료할 수 있는 사용자를 결정 합니다. 이 사용자 권한을 잘못 사용 하면 서비스 거부가 발생할 수 있습니다.
  - **구성되지 않음**
  - **허용**
  
- **파일 및 디렉터리 복원**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/RestoreFilesAndDirectories](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-restorefilesanddirectories)
  
  이 사용자 권한은 백업 된 파일 및 디렉터리를 복원할 때 파일, 디렉터리, 레지스트리 및 기타 영구 개체 권한을 무시할 수 있는 사용자를 결정 하 고 유효한 보안 주체를 개체의 소유자로 설정할 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**
  
- **파일 또는 개체의 소유권 가져오기**  
  **기본값**: 구성되지 않음  
  CSP: [Userrights/TakeOwnership](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-takeownership)

  이 사용자 권한은 Active Directory 개체, 파일 및 폴더, 프린터, 레지스트리 키, 프로세스 및 스레드를 포함 하 여 시스템에서 보안 개체의 소유권을 가져올 수 있는 사용자를 결정 합니다.
  - **구성되지 않음**
  - **허용**

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](../configuration/device-profile-assign.md)하고, [해당 상태를 모니터링](../configuration/device-profile-monitor.md)합니다.  

[macOS](endpoint-protection-macos.md) 디바이스에 대한 엔드포인트 보호 설정을 구성합니다.  
