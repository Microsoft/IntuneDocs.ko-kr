---
title: Windows PC에 대한 방화벽 정책
titlesuffix: Microsoft Intune
description: Intune에서는 Intune 클라이언트로 관리하는 PC를 다양한 방법으로 보호할 수 있습니다. 그중 하나는 Windows 방화벽 설정을 구성하는 것입니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic-keep
ms.openlocfilehash: a38ff69b878880ffa16e327eace0afe64d336f43
ms.sourcegitcommit: 116be0eaa44fd5518ff34780d39569224ef4746b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36310575"
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>Microsoft Intune에서 Windows 방화벽 정책을 사용하여 Windows PC 보호

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Microsoft Intune에서는 Intune 클라이언트로 관리하는 Windows PC를 다양한 방법으로 보호할 수 있습니다. 그중 한 가지 방법은 PC에서 Windows 방화벽 설정을 구성할 수 있도록 하는 정책을 제공하는 것입니다.

컴퓨터에 Intune Windows PC 클라이언트를 아직 설치하지 않은 경우 [Microsoft Intune을 사용하여 Windows PC 클라이언트 설치](install-the-windows-pc-client-with-microsoft-intune.md)를 참조하세요.

다음 섹션의 정보를 참조하여 Windows PC에 대한 Windows 방화벽 정책을 쉽게 구성, 배포 및 모니터링할 수 있습니다.

## <a name="use-intune-policies-to-manage-windows-firewall"></a>Intune 정책을 사용하여 Windows 방화벽 관리
Windows 방화벽 정책을 통해 관리 PC의 Windows 방화벽을 제어하는 설정을 만들고 배포할 수 있습니다. Windows 방화벽에 대한 사용자 지정 예외는 관리할 수 없으며 이러한 설정은 타사 방화벽에 영향을 주지 않습니다.

> [!NOTE]
> Microsoft Intune 정책 및 그룹 정책이 PC의 동일한 설정을 관리하도록 구성된 경우 그룹 정책 설정이 Microsoft Intune 정책을 재정의합니다. Intune 정책과 그룹 정책 간의 충돌을 방지하는 방법에 대한 정보는 [GPO 및 Microsoft Intune 정책 충돌 해결](resolve-gpo-and-microsoft-intune-policy-conflicts.md)을 참조하세요.
>
> Windows Vista를 실행하는 컴퓨터에 Windows 방화벽 설정을 배포하려는 경우에는 먼저 컴퓨터에 [핫픽스 KB971800](http://support2.microsoft.com/kb/971800)을 설치해야 합니다.

> [!IMPORTANT]
> Intune을 사용하여 Windows 방화벽을 관리하려면 다음 두 서비스가 관리할 컴퓨터에서 설정되어 있는지 확인하세요.
>
> -   Windows 방화벽
> -   IPsec 정책 에이전트

## <a name="configure-a-windows-firewall-policy"></a>Windows 방화벽 정책 구성

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **정책** &gt; **정책 추가**를 선택합니다.

2.  **Windows 방화벽 설정** 정책을 구성하고 배포합니다. 권장 설정을 사용하거나 설정을 사용자 지정할 수 있습니다. 정책을 만들고 배포하는 방법에 대한 자세한 정보가 필요한 경우 [Microsoft Intune 컴퓨터 클라이언트를 사용한 일반 Windows PC 관리 작업](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)을 참조하세요.

    다음 섹션에서는 정책에서 구성할 수 있는 값과 정책을 사용자 지정하지 않은 경우에 사용되는 기본값을 나열합니다.

Windows 방화벽 정책을 배포한 후 **정책** 작업 영역의 **모든 정책** 페이지에서 해당 상태를 볼 수 있습니다.

## <a name="specify-policy-settings-for-windows-firewall"></a>Windows 방화벽에 대한 정책 설정 지정

### <a name="turn-on-windows-firewall"></a>Windows 방화벽 사용

이 정책 설정은 관리 컴퓨터가 다음 상태일 경우 Windows 방화벽을 사용하도록 설정합니다.
- 도메인에 연결됨(예: 작업 공간)
- 신뢰할 수 있는 개인 네트워크에 연결됨(예: 홈 네트워크)
- 신뢰할 수 없는 공용 네트워크에 연결됨(예: 커피숍)

이러한 각 설정의 기본값은 가장 안전한 값인 **예**입니다.



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>허용되는 프로그램 목록에 있는 연결을 포함하여 들어오는 모든 연결 차단

이 정책 설정은 관리 컴퓨터가 다음 상태일 경우 들어오는 네트워크 트래픽을 차단하도록 Windows 방화벽을 구성합니다.
- 도메인에 연결됨(예: 작업 공간)
- 신뢰할 수 있는 개인 네트워크에 연결됨(예: 홈 네트워크)
- 신뢰할 수 없는 공용 네트워크에 연결됨(예: 커피숍)

이러한 각 설정의 기본값은 가장 안전한 값인 **예**입니다.

> [!IMPORTANT]
> 서비스 팩이 설치되지 않은 Windows Vista를 실행 중인 관리 컴퓨터가 환경에 포함되어 있는 경우에는 Microsoft 기술 자료의 [문서 971800](http://go.microsoft.com/fwlink/?LinkId=188405) 과 관련된 업데이트를 설치하거나 해당 컴퓨터에 배포된 정책에서 **들어오는 모든 연결 차단** 정책 설정을 사용하지 않도록 설정해야 합니다.

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>Windows 방화벽이 새 프로그램을 차단할 때 사용자에게 알림

이러한 정책 설정은 관리 컴퓨터가 다음 상태일 경우에 Windows 방화벽에서 들어오는 네트워크 트래픽을 차단할 때 PC 사용자에게 알릴지 여부를 결정합니다.
- 도메인에 연결됨(예: 작업 공간)
- 신뢰할 수 있는 개인 네트워크에 연결됨(예: 홈 네트워크)
- 신뢰할 수 없는 공용 네트워크에 연결됨(예: 커피숍)

이러한 각 설정의 기본값은 **예**입니다.


### <a name="configure-predefined-exceptions"></a>미리 정의된 예외 구성

이전에 구성된 값에 관계없이 방화벽을 통해 특정 네트워크 트래픽 유형을 허용하는 예외를 구성할 수 있습니다. 기본적으로 이러한 설정은 구성되어 있지 않습니다.

|설정 이름|세부 정보|
|------------------|--------------------|
|**BranchCache - 콘텐츠 검색**<br>(Windows 7 이상)|BranchCache 클라이언트에서 HTTP를 사용하여 분산 모드에서는 다른 BranchCache 클라이언트의 콘텐츠를 검색하고, 호스트 캐시 모드에서는 호스트 캐시에서 콘텐츠를 검색할 수 있습니다. 이 설정에서는 HTTP를 사용합니다.|
|**BranchCache - 호스트 캐시 클라이언트**<br>(Windows 7 이상)|BranchCache 클라이언트에서 호스트 캐시를 사용할 수 있습니다. 이 설정에서는 HTTPS를 사용합니다.|
|**BranchCache - 호스트 캐시 서버**|BranchCache 클라이언트에서 호스트 캐시를 사용하여 다른 클라이언트와 통신할 수 있습니다. 이 설정에서는 HTTPS를 사용합니다.|
|**BranchCache - 피어 검색**<br>(Windows 7 이상)|BranchCache 클라이언트에서 WS 검색(웹 서비스 동적 검색) 프로토콜을 사용하여 로컬 서브넷에서 콘텐츠 가용성을 검색할 수 있습니다.|
|**BITS 피어 캐싱**|클라이언트에서 BITS(Background Intelligent Transfer Service)를 사용하고 동일한 서브넷의 클라이언트에 있는 BITS 캐시에 저장된 파일을 공유할 수 있습니다. 이 설정에서는 장치 WSDAPI(Web Services on Devices) 및 RPC(원격 프로시저 호출)를 사용합니다.|
|**네트워크 프로젝터에 연결**|사용자가 유선 또는 무선 네트워크를 통해 프로젝터에 연결하여 프레젠테이션을 표시할 수 있습니다. 이 설정에서는 WSDAPI를 사용합니다.|
|**핵심 네트워킹**|클라이언트에서 IPv4 및 IPv6을 사용하여 네트워크 리소스에 연결할 수 있습니다.|
|**DTC(Distributed Transaction Coordinator)**|관리 컴퓨터에서 트랜잭션으로 보호되는 리소스(예: 데이터베이스, 메시지 큐, 파일 시스템)를 업데이트하는 트랜잭션을 조정할 수 있습니다.|
|**파일 및 프린터 공유**|사용자가 네트워크의 다른 사용자와 로컬 파일 및 프린터를 공유할 수 있습니다. 이 설정에서는 NetBIOS, LLMNR(링크 로컬 멀티캐스트 이름 확인), SMB(서버 메시지 블록) 프로토콜 및 RPC를 사용합니다.|
|**홈 그룹**<br>(Windows 7 이상)|관리 컴퓨터가 홈 그룹 네트워크에 참여할 수 있습니다.|
|**iSCSI 서비스**|관리 컴퓨터에서 iSCSI 서버 및 장치에 연결할 수 있습니다.|
|**키 관리 서비스**|컴퓨터에서 기업 환경의 라이선스 준수 현황을 파악할 수 있습니다.|
|**Media Center Extender**|Media Center Extender가 Windows Media Center를 실행하는 컴퓨터와 통신할 수 있습니다. 이 설정에서는 SSDP(Simple Service Discovery Protocol) 및qWave를 사용합니다.|
|**Netlogon 서비스**|사용자 및 서비스 인증을 위해 도메인 클라이언트와 도메인 컨트롤러 간 보안 채널을 구성합니다. 이 설정에서는 RPC를 사용합니다.|
|**네트워크 검색**|컴퓨터가 네트워크의 다른 장치를 검색하거나 다른 장치에서 검색될 수 있습니다. 이 설정에서는 기능 검색 호스트 및 게시 서비스, SSDP, NetBIOS, LLMNR 및 UPnP 네트워크 프로토콜을 사용합니다.|
|**성능 로그 및 경고**|성능 로그 및 경고 서비스가 원격으로 관리될 수 있습니다. 이 설정에서는 RPC를 사용합니다.|
|**원격 관리**|컴퓨터를 원격으로 관리할 수 있습니다.|
|**원격 지원**|관리 컴퓨터의 사용자가 네트워크의 다른 사용자에게 원격 지원을 요청할 수 있습니다. 이 설정에서는 SSDP, PNRP(피어 이름 확인 프로토콜), Teredo 및 UPnP 네트워크 프로토콜을 사용합니다.|
|**원격 데스크톱**|컴퓨터에서 원격 데스크톱을 사용하여 다른 컴퓨터에 액세스할 수 있습니다.|
|**원격 이벤트 로그 관리**|클라이언트 이벤트 로그를 원격으로 보고 관리할 수 있습니다. 이 설정에서는 명명된 파이프 및 RPC를 사용합니다.|
|**원격 예약된 작업 관리**|작업 예약 서비스를 원격으로 관리할 수 있습니다. 이 설정에서는 RPC를 사용합니다.|
|**원격 서비스 관리**|클라이언트에서 로컬 서비스를 원격으로 관리할 수 있습니다. 이 설정에서는 명명된 파이프 및 RPC를 사용합니다.|
|**원격 볼륨 관리**|소프트웨어 및 하드웨어 디스크 볼륨을 원격으로 관리할 수 있습니다. 이 설정에서는 RPC를 사용합니다.|
|**라우팅 및 원격 액세스**|컴퓨터로 들어오는 VPN 및 원격 액세스 연결을 설정합니다.|
|**SSTP(Secure Socket Tunneling Protocol)**|SSTP(Secure Socket Tunneling Protocol)를 통해 관리 컴퓨터에 들어오는 VPN 연결을 설정합니다. 이 설정에서는 HTTPS를 사용합니다.|
|**SNMP 트랩**|관리 컴퓨터에서 SNMP(Simple Network Management Protocol) 트랩 서비스 트래픽을 받을 수 있습니다.|
|**UPnP 프레임워크**|컴퓨터에서 UPnP 인증 장치를 검색 및 사용하도록 컴퓨터의 UPnP 프레임워크 서비스를 구성합니다.|
|**Windows 공동 작업 컴퓨터 이름 등록 서비스**|컴퓨터에서 SSDP와 PNRP를 사용하여 다른 컴퓨터를 찾아 통신할 수 있습니다.|
|**Windows Media Player**|UDP(User Datagram Protocol)를 통해 스트리밍 미디어를 수신할 수 있습니다.|
|**Windows Media Player 네트워크 공유 서비스**|네트워크를 통해 미디어를 공유할 수 있습니다. 이 설정에서는 SSDP, qWave 및 UPnP 네트워크 프로토콜을 사용합니다.|
|**Windows Media Player 네트워크 공유 서비스(인터넷)**<br>(Windows 7 이상)|사용자가 네트워크를 통해 홈 미디어를 공유할 수 있습니다.|
|**Windows Meeting Space**|사용자가 네트워크를 통해 협력하여 문서, 프로그램 및 데스크톱을 공유할 수 있습니다. 이 설정에서는 DFSR(분산 파일 시스템 복제) 및 P2P를 사용합니다.|
|**Windows Peer to Peer Collaboration Foundation**|다양한 피어 투 피어 프로그램 및 기술에서 연결할 수 있도록 해당 프로그램 및 기술을 구성합니다. 이 설정에서는 SSDP 및 PNRP를 사용합니다.|
|**Windows 원격 관리(호환성)**|운영 체제 및 장치의 원격 관리를 위해 WS-Management, 웹 서비스 기반 프로토콜을 사용하여 관리 컴퓨터를 원격으로 관리할 수 있습니다.|
|**Windows 원격 관리**<br>(Windows 8 이상)|운영 체제 및 장치의 원격 관리를 위해 WS-Management, 웹 서비스 기반 프로토콜을 사용하여 관리 컴퓨터를 원격으로 관리할 수 있습니다.|
|**Windows Virtual PC**<br>(Windows 7 이상)|가상 컴퓨터가 다른 컴퓨터와 통신할 수 있습니다.|
|**무선 휴대용 장치**|MTP(미디어 전송 프로토콜)를 통해 네트워크 사용 카메라 또는 미디어 장치에서 관리 컴퓨터로 미디어를 전송할 수 있습니다. 이 설정에서는 SSDP 및 UPnP 네트워크 프로토콜을 사용합니다.|

### <a name="see-also"></a>참고 항목
[Windows PC를 보호하는 정책](policies-to-protect-windows-pcs-in-microsoft-intune.md)
