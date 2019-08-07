---
title: Microsoft Intune에 대한 네트워크 엔드포인트
titleSuffix: ''
description: Intune에 대한 엔드포인트를 검토합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1dd836d8bbc4d6f32081c74fb6f9edc42aff2cac
ms.sourcegitcommit: d2ac912b834c4840de9cc92ba1815b6ecfbfb52b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68482968"
---
# <a name="network-endpoints-for-microsoft-intune"></a>Microsoft Intune에 대한 네트워크 엔드포인트  

이 페이지에는 Intune 배포 시 프록시 설정에 필요한 IP 주소 및 포트 설정이 나열되어 있습니다.

클라우드 전용 서비스인 Intune에는 서버 또는 게이트웨이와 같은 온-프레미스 인프라가 필요하지 않습니다.

## <a name="access-for-managed-devices"></a>관리형 디바이스의 액세스  

방화벽 및 프록시 서버로 보호되는 디바이스를 관리하려면 Intune에 대한 통신을 사용하도록 설정해야 합니다.

- 프록시 서버는 **HTTP(80)** 와 **HTTPS(443)** 를 모두 지원해야 합니다. Intune 클라이언트에서 두 프로토콜을 모두 사용하기 때문입니다. Windows Information Protection은 포트 444를 사용합니다.
- 일부 작업(예: 클래식 pc 에이전트의 소프트웨어 업데이트 다운로드)의 경우 Intune에는 manage.microsoft.com에 대한 인증되지 않은 프록시 서버 액세스가 필요합니다.

개별 클라이언트 컴퓨터에서 프록시 서버 설정을 수정할 수 있습니다. 그룹 정책을 사용하여 지정된 프록시 서버로 보호되는 모든 클라이언트 컴퓨터의 설정을 변경할 수도 있습니다.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

관리되는 디바이스를 사용하려면 **모든 사용자**가 방화벽을 통해 서비스에 액세스할 수 있도록 구성해야 합니다.

다음 표에는 Intune 클라이언트에서 액세스하는 포트 및 서비스가 정리되어 있습니다.

|Domains    |IP 주소      |
|-----------|----------------|
|login.microsoftonline.com | 추가 정보: [Office 365 URL 및 IP 주소 범위](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|

## <a name="network-requirements-for-powershell-scripts-and-win32-apps"></a>PowerShell 스크립트 및 Win32 앱의 네트워크 요구 사항  

Intune을 사용하여 Powershell 스크립트 또는 Win32 앱을 배포하는 경우 테넌트가 현재 상주하는 엔드포인트에 대한 액세스 권한도 부여해야 합니다.

|ASU | 스토리지 이름 | CDN |
| --- | --- |--- |
| AMSUA0601 | prodmsua06data | https:\//prodmsua06data.azureedge.net |
| AMSUA0602 | prodamsua0602data | https:\//prodamsua0602data.azureedge.net |
| AMSUA0101 | prodmsua01data | https:\//prodmsua01data.azureedge.net |
| AMSUA0201 | prodmsua02data | https:\//prodmsua02data.azureedge.net |
| AMSUA0202 | Prodmsua0202rcdata | https:\//prodamsua0202data.azureedge.net/ |
| AMSUA0401 | prodmsua04data | https:\//prodmsua04data.azureedge.net |
| AMSUA0402 | Prodmsua0402rcdata | https:\//prodamsua0402data.azureedge.net/ |
| AMSUA0501 | prodmsua05data | https:\//prodmsua05data.azureedge.net |
| AMSUA0502 | prodmsua0502data | https:\//prodmsua0502data.azureedge.net |
| AMSUB0101 | prodmsub01data | https:\//prodmsub01data.azureedge.net |
| AMSUB0102 | prodamsub0102data | https:\//prodamsub0102data.azureedge.net |
| AMSUB0201 | prodmsub02data | https:\//prodmsub02data.azureedge.net |
| AMSUB0202 | Prodmsub0202rcdata | https:\//prodamsub0202data.azureedge.net |
| AMSUB0301 | Prodmsub03data2 | https:\//prodmsub03data2.azureedge.net |
| AMSUB0302 | Prodmsub0302rcdata | https:\//prodamsub0302data.azureedge.net |
| AMSUB0501 | prodmsub05data | https:\//prodmsub05data.azureedge.net |
| AMSUC0101 | prodmsuc01data | https:\//prodmsuc01data.azureedge.net |
| AMSUC0201 | prodmsuc02data | https:\//prodmsuc02data.azureedge.net |
| AMSUC0301 | prodmsuc03data | https:\//prodmsuc03data.azureedge.net |
| AMSUC0501 | prodmsuc05data | https:\//prodmsuc05data.azureedge.net |
| AMSUA0701 | pemsua07rcdata | https:\//pemsua07data.azureedge.net |

## <a name="windows-push-notification-services-wns"></a>Windows Push Notification Services(WNS)  

MDM(모바일 디바이스 관리)을 사용하여 관리되는 Intune 관리 Windows 디바이스의 경우, 디바이스 작업 및 기타 작업을 즉시 수행하려면 Windows Push Notification Services(WNS)를 사용해야 합니다. 자세한 내용은 [엔터프라이즈 방화벽을 통한 Windows 알림 트래픽 허용](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)을 참조하세요.  

## <a name="delivery-optimization-port-requirements"></a>Delivery Optimization 포트 요구 사항  

### <a name="port-requirements"></a>포트 요구 사항  

피어 투 피어 트래픽의 경우 Delivery Optimization은 TCP/IP용 7680 또는 NAT 통과용 3544(필요에 따라 Teredo)를 사용합니다. 클라이언트-서비스 통신의 경우 포트 80/443을 통해 HTTP 또는 HTTPS를 사용합니다.

### <a name="proxy-requirements"></a>프록시 요구 사항  

Delivery Optimization을 사용하려면 바이트 범위 요청을 허용해야 합니다. 자세한 내용은 [Windows 업데이트에 대한 프록시 요구 사항](https://docs.microsoft.com/windows/deployment/update/windows-update-troubleshooting)을 참조하세요.

### <a name="firewall-requirements"></a>방화벽 요구 사항  

방화벽을 통해 다음 호스트 이름이 Delivery Optimization을 지원하도록 허용합니다.
클라이언트와 Delivery Optimization 클라우드 서비스 간의 통신:
- \*.do.dsp.mp.microsoft.com

Delivery Optimization 메타데이터의 경우:
- \*.dl.delivery.mp.microsoft.com
- \*.emdl.ws.microsoft.com

## <a name="apple-device-network-information"></a>Apple 디바이스 네트워크 정보  

|사용 목적|호스트 이름(IP 주소/서브넷)|프로토콜|포트|
|-----|--------|------|-------|
|Apple 서버에서 콘텐츠 받기 및 표시|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|APNS 서버와 통신|#-courier.push.apple.com<br>‘#’은 0~50 사이 임의 숫자입니다.|    TCP     |  5223 및 443  |
|World Wide Web, iTunes Store, macOS 앱 스토어, iCloud, 메시징 등 액세스를 포함한 다양한 기능 |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 또는 443   |

자세한 내용은 Apple의 [TCP and UDP ports used by Apple software products](https://support.apple.com/en-us/HT202944)(Apple 소프트웨어 제품에 사용되는 TCP 및 UDP 포트), [About macOS, iOS, and iTunes server host connections and iTunes background processes](https://support.apple.com/en-us/HT201999)(macOS, iOS 및 iTunes 서버 호스트 연결과 iTunes 백그라운드 프로세스 정보) 및 [If your macOS and iOS clients aren't getting Apple push notifications](https://support.apple.com/en-us/HT203609)(macOS 및 iOS 클라이언트가 Apple 푸시 알림을 받지 못하는 경우)를 참조하세요.  

## <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune 인증서 커넥터  

Microsoft Intune Certificate Connector를 호스트하는 서버는 다음 표에 나열된 공용 IP 위치에 **TCP** 포트 **443**을 사용하여 액세스할 수 있어야 합니다. 인증서에 대한 자세한 내용은 [Intune을 사용하여 PKCS 인증서 구성 및 사용](certficates-pfx-configure.md) 및 [Intune을 사용하여 SCEP 인증서 구성 및 사용](certificates-scep-configure.md)을 참조하세요.

|Domains                             |IP 주소       |
|---------------|--------------------------------------|
|Manage.microsoft.com <br> i.manage.microsoft.com <br> r.manage.microsoft.com <br> a.manage.microsoft.com <br> p.manage.microsoft.com <br> EnterpriseEnrollment.manage.microsoft.com <br> EnterpriseEnrollment-s.manage.microsoft.com|13.76.177.110  |
|fef.msua06.manage.microsoft.com  |13.78.185.97  |
|Manage.microsoft.com <br> i.manage.microsoft.com <br> r.manage.microsoft.com <br> a.manage.microsoft.com <br> p.manage.microsoft.com <br> EnterpriseEnrollment.manage.microsoft.com <br> EnterpriseEnrollment-s.manage.microsoft.com |13.82.96.212  |
|fef.amsua0502.manage.microsoft.com |13.85.68.142   |
| portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msuc01.manage.microsoft.com <br> m.fei.msuc01.manage.microsoft.com <br> portal.fei.msuc02.manage.microsoft.com <br> m.fei.msuc02.manage.microsoft.com <br> portal.fei.msuc03.manage.microsoft.com <br> m.fei.msuc03.manage.microsoft.com <br> portal.fei.msuc05.manage.microsoft.com <br> m.fei.msuc05.manage.microsoft.com |20.188.107.228|
|fef.msua04.manage.microsoft.com  |23.96.112.28  |
|fef.amsua0402.manage.microsoft.com|40.69.157.122    |
|Manage.microsoft.com <br> i.manage.microsoft.com <br> r.manage.microsoft.com <br> a.manage.microsoft.com <br> p.manage.microsoft.com <br> EnterpriseEnrollment.manage.microsoft.com <br> EnterpriseEnrollment-s.manage.microsoft.com |40.83.123.72    |
|portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msub01.manage.microsoft.com <br> m.fei.msub01.manage.microsoft.com <br> portal.fei.amsub0102.manage.microsoft.com <br> m.fei.amsub0102.manage.microsoft.com <br> fei.msub02.manage.microsoft.com <br> portal.fei.msub02.manage.microsoft.com <br> m.fei.msub02.manage.microsoft.com <br> portal.fei.msub03.manage.microsoft.com <br> m.fei.msub03.manage.microsoft.com <br> portal.fei.msub05.manage.microsoft.com <br> m.fei.msub05.manage.microsoft.com <br> portal.fei.amsub0202.manage.microsoft.com <br> m.fei.amsub0202.manage.microsoft.com <br> portal.fei.amsub0302.manage.microsoft.com <br> m.fei.amsub0302.manage.microsoft.com |51.144.161.187 |
|portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msub01.manage.microsoft.com <br> m.fei.msub01.manage.microsoft.com <br> portal.fei.amsub0102.manage.microsoft.com <br> m.fei.amsub0102.manage.microsoft.com <br> fei.msub02.manage.microsoft.com <br> portal.fei.msub02.manage.microsoft.com <br> m.fei.msub02.manage.microsoft.com <br> portal.fei.msub03.manage.microsoft.com <br> m.fei.msub03.manage.microsoft.com <br> portal.fei.msub05.manage.microsoft.com <br> m.fei.msub05.manage.microsoft.com <br> portal.fei.amsub0202.manage.microsoft.com <br> m.fei.amsub0202.manage.microsoft.com <br> portal.fei.amsub0302.manage.microsoft.com <br> m.fei.amsub0302.manage.microsoft.com  |52.138.193.149  |
|portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msua01.manage.microsoft.com <br> m.fei.msua01.manage.microsoft.com <br> portal.fei.msua02.manage.microsoft.com <br> m.fei.msua02.manage.microsoft.com <br> portal.fei.msua04.manage.microsoft.com <br> m.fei.msua04.manage.microsoft.com <br> portal.fei.msua05.manage.microsoft.com <br> m.fei.msua05.manage.microsoft.com <br> portal.fei.amsua0502.manage.microsoft.com <br> m.fei.amsua0502.manage.microsoft.com <br> portal.fei.msua06.manage.microsoft.com <br> m.fei.msua06.manage.microsoft.com <br> portal.fei.amsua0602.manage.microsoft.com <br> m.fei.amsua0602.manage.microsoft.com <br> fei.amsua0202.manage.microsoft.com <br> portal.fei.amsua0202.manage.microsoft.com <br> m.fei.amsua0202.manage.microsoft.com <br> portal.fei.amsua0402.manage.microsoft.com <br> m.fei.amsua0402.manage.microsoft.com |52.160.70.20  |
|fef.amsua0602.manage.microsoft.com |52.161.28.64   |
|fef.amsua0202.manage.microsoft.com |52.165.165.17   |
|portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msua01.manage.microsoft.com <br> m.fei.msua01.manage.microsoft.com <br> portal.fei.msua02.manage.microsoft.com <br> m.fei.msua02.manage.microsoft.com <br> portal.fei.msua04.manage.microsoft.com <br> m.fei.msua04.manage.microsoft.com <br> portal.fei.msua05.manage.microsoft.com <br> m.fei.msua05.manage.microsoft.com <br> portal.fei.amsua0502.manage.microsoft.com <br> m.fei.amsua0502.manage.microsoft.com <br> portal.fei.msua06.manage.microsoft.com <br> m.fei.msua06.manage.microsoft.com <br> portal.fei.amsua0602.manage.microsoft.com <br> m.fei.amsua0602.manage.microsoft.com <br> fei.amsua0202.manage.microsoft.com <br> portal.fei.amsua0202.manage.microsoft.com <br> m.fei.amsua0202.manage.microsoft.com <br> portal.fei.amsua0402.manage.microsoft.com <br> m.fei.amsua0402.manage.microsoft.com |52.168.54.64   |
|r.manage.microsoft.com |52.169.9.87    |
|.manage.microsoft.com  |52.174.26.23   |
|portal.fei.msuc01.manage.microsoft.com <br> m.fei.msuc01.manage.microsoft.com <br> portal.fei.msuc02.manage.microsoft.com <br> m.fei.msuc02.manage.microsoft.com <br> portal.fei.msuc03.manage.microsoft.com <br> m.fei.msuc03.manage.microsoft.com <br> portal.fei.msuc05.manage.microsoft.com <br> m.fei.msuc05.manage.microsoft.com |52.175.12.209  |
|fef.msua07.manage.microsoft.com |52.175.208.218     |
|fef.msua02.manage.microsoft.com |52.177.194.236    |
|sts.manage.microsoft.com        |104.40.82.191    |
|fef.msua01.manage.microsoft.com |138.91.243.97     |
|fef.msua05.manage.microsoft.com |138.91.244.151     |





