---
title: 미국 정부 배포용 네트워크 엔드포인트 - Microsoft Intune
titleSuffix: ''
description: Intune에 대한 미국 정부 엔드포인트를 검토합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d876c0268f38a09ea3729a7e19ee00b321ae897a
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000400"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Microsoft Intune에 대한 미국 정부 엔드포인트

이 페이지에는 Intune 배포 시 프록시 설정에 필요한 미국 정부 엔드포인트가 나열되어 있습니다.

방화벽 및 프록시 서버로 보호되는 디바이스를 관리하려면 Intune에 대한 통신을 사용하도록 설정해야 합니다.

- 프록시 서버는 **HTTP(80)** 와 **HTTPS(443)** 를 모두 지원해야 합니다. Intune 클라이언트에서 두 프로토콜을 모두 사용하기 때문입니다.
- 소프트웨어 업데이트 다운로드 등의 일부 작업을 위해 Intune에는 manage.microsoft.com에 대한 인증되지 않은 프록시 서버 액세스가 필요합니다.

개별 클라이언트 컴퓨터에서 프록시 서버 설정을 수정할 수 있습니다. 그룹 정책을 사용하여 지정된 프록시 서버로 보호되는 모든 클라이언트 컴퓨터의 설정을 변경할 수도 있습니다.

관리되는 디바이스를 사용하려면 **모든 사용자**가 방화벽을 통해 서비스에 액세스할 수 있도록 구성해야 합니다.

다음 표에는 Intune 클라이언트에서 액세스하는 포트 및 서비스가 정리되어 있습니다.

|**엔드포인트**|**IP 주소**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>미국 정부 고객 지정 엔드포인트:
- Azure Portal: https:\//portal.azure.us/ 
- Office 365: https:\//portal.office365.us/ 
- Intune 회사 포털: https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Intune이 의존하는 파트너 서비스 엔드포인트:
- AAD Sync 서비스: https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https:\//login.microsoftonline.us
- Directory Proxy: https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph: https:\//directory.microsoftazure.us 및 https:\//graph.microsoftazure.us
- MS Graph: https:\//graph.microsoft.us
- ADRS: https:\//enterpriseregistration.microsoftonline.us

## <a name="windows-push-notification-services"></a>Windows Push Notification Services
MDM(모바일 디바이스 관리)을 사용하여 관리되는 Intune 관리 디바이스에서 디바이스 작업 및 기타 작업을 즉시 수행하려면 Windows PUsh Notification Services(WNS)가 필요합니다. 자세한 내용은 [WNS 트래픽을 지원하기 위한 엔터프라이즈 방화벽 및 프록시 구성](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)을 참조하세요.

## <a name="apple-device-network-information"></a>Apple 디바이스 네트워크 정보

|**사용 목적**|**호스트 이름(IP 주소/서브넷)**|**프로토콜**|**포트**|
|------------|-----------|------------|-----------|
|Apple 서버에서 콘텐츠 받기 및 표시|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|APNS 서버와 통신|#-courier.push.apple.com<br>‘#’은 0~50 사이 임의 숫자입니다.|TCP|5223 및 443|
|인터넷, iTunes Store, macOS 앱 스토어, iCloud, 메시지 등 액세스를 포함한 다양한 기능|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 또는 443|

자세한 내용은 다음을 참조하십시오.

- [Apple 소프트웨어 제품에서 사용하는 TCP 및 UDP 포트](https://support.apple.com/HT202944)
- [macOS, iOS 및 iTunes 서버 호스트 연결 및 iTunes 백그라운드 프로세스 정보](https://support.apple.com/HT201999)
- [macOS 및 iOS 클라이언트가 Apple 푸시 알림을 받지 못하는 경우](https://support.apple.com/HT203609)

## <a name="next-steps"></a>다음 단계
[Microsoft Intune에 대한 네트워크 엔드포인트](intune-endpoints.md)

[Windows 10 자동 등록 및 디바이스 등록](../enrollment/windows-enroll.md#registration-and-enrollment-cnames)