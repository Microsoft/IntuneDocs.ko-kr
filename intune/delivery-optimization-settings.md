---
title: Intune에 대 한 Windows 10 배달 최적화 설정을 | Microsoft Docs
description: Intune을 사용 하 여 배포할 수 있는 Windows 10 장치에 대 한 배달 최적화 설정입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6e90828da8c209b534b830af7fe522b254374bf
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57695282"
---
# <a name="delivery-optimization-settings-for-intune"></a>Intune에 대 한 배달 최적화 설정

이 문서에서는 Intune에서 지 원하는 10 이상 Windows를 실행 하는 장치에 대 한 배달 최적화 설정을 나열 합니다.  

Intune 콘솔에서 대부분의 옵션은 직접 관련 콘텐츠에 대 한 링크가 제공 되는 Windows 설명서에서 자세히 설명 되어 있는 배달 최적화 설정에 매핑됩니다.  설정 또는 Intune에 관련 된 옵션은 추가 콘텐츠 링크를 포함 하지 않습니다.  

다음 표에 다음과 같습니다.  

- **설정**: Intune에 표시 되는 설정입니다. 링크 설정에 관련 항목을 엽니다 [Windows 10에 대 한 배달 최적화 구성 업데이트](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) Windows 설명서를 설정 하는 방법에 대 한 자세히 알아볼 수 있습니다.

- **Windows 버전**:이 설정에 대 한 지원이 포함 된 Windows 10의 최소 버전입니다.  

- **세부 정보**: Intune에 Intune의 기본을 포함 하 여 설정을 구현 하는 방법의 간략 한 설명입니다. 사용 가능한 경우 연결이 있는지 [배달 최적화 정책 구성 서비스 제공자](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization) (CSP) 항목입니다.  

이러한 설정을 사용 하려면 Intune에서 구성 참조 [업데이트를 제공](delivery-optimization-windows.md)합니다.  

## <a name="delivery-optimization"></a>배달 최적화  

|Setting  |Windows 버전  |세부 정보  |
|---------|-----------------|---------|
| [다운로드 모드](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode)     | 1511         | 다운로드 방법을 지정 콘텐츠를 다운로드 하도록 배달 최적화를 사용 합니다.<br><ul><li>**구성되지 않음**: 최종 사용자는 운영 체제에서 제공되는 *Windows 업데이트 또는 제공 최적화* 설정을 사용할 수 있는 고유한 방법으로 해당 디바이스를 업데이트합니다. </li> <li> **HTTP만, 피어링 없음(0)**: 인터넷에서만 업데이트를 가져옵니다. (피어-투-피어) 네트워크에 있는 다른 컴퓨터에서 업데이트를 가져오지 마십시오. </li> <li> **(1)에서 동일한 NAT 뒤의 피어 링과 혼합 된 HTTP**: 네트워크의 다른 컴퓨터에서 인터넷에서 업데이트를 가져옵니다. </li> <li> **전용 그룹 (2) 간 피어 링과 혼합 된 HTTP**: Active Directory 사이트 (있는 경우) 또는 동일한 도메인에 동일한 장치에서 발생 피어 링 합니다. 이 옵션을 선택하면 피어링이 NAT(Network Address Translation) IP 주소를 교차합니다. </li> <li> **인터넷 피어링과 혼합된 HTTP(3)**: 인터넷 및 네트워크의 다른 컴퓨터에서 업데이트를 가져옵니다. </li> <li> **피어링이 없는 단순 다운로드 모드(99)**: Microsoft와 같은 업데이트 소유자로부터 직접 인터넷에서 업데이트를 가져옵니다. 배달 최적화 클라우드 서비스에는 연결하지 않습니다. </li> <li> **바이패스 모드(100)**: BITS(Background Intelligent Transfer Service)를 사용하여 업데이트를 가져옵니다. 배달 최적화를 사용하지 마세요. </li></ul> **기본**: 구성 되지 않음  <br><br> 정책 CSP: [DODownloadMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodownloadmode)  <br><br>  |
| [피어 선택 제한](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#select-a-method-to-restrict-peer-selection)          | 1803        | 필요 **다운로드 모드** 로 설정 *(1)에서 동일한 NAT 뒤의 피어 링과 혼합 된 HTTP* 하거나 *사설 그룹 (2) 간 피어 링과 혼합 된 HTTP*합니다.<br/><br/>장치의 특정 그룹에 피어 선택 영역을 제한합니다.<br/><br/>**기본**: 구성 되지 않음 <br/><br/>정책 CSP: [DORestrictPeerSelectionBy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dorestrictpeerselectionby)<br><br>      |
| [그룹 ID 원본](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#select-the-source-of-group-ids)     | 1803        | 필요 **다운로드 모드** 로 설정할 *비공개 그룹 간 피어 링과 혼합 된 HTTP*합니다.<br><br>원본에서 장치의 특정 그룹에 피어 선택 영역을 제한합니다.<br><br>선택 하는 경우 **사용자 지정**, 한 다음 구성한 **그룹 ID (GUID)** 합니다. 서로 다른 도메인에 추가 되거나 동일한 LAN에 없는 분기에 대 한 로컬 네트워크 피어 링에 대 한 단일 그룹을 만들어야 하는 경우에 그룹 ID로 GUID를 사용 합니다.<br><br>**기본**: 구성 되지 않음 <br><br>정책 CSP: [DOGroupId](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dogroupid)     |

## <a name="bandwidth"></a>대역폭  

|Setting  |Windows 버전  |세부 정보  |
|---------|---------|---------|
|대역폭 최적화 형식     | *세부 정보 참조*        | Intune에서 최대값을 결정 하는 방법 선택 대역폭 모든 동시 다운로드 활동에서 해당 배달 최적화를 사용할 수 있습니다.<br><br>다음 옵션을 사용할 수 있습니다.<br><ul><li>**구성되지 않음**</li><br><li>**절대**– 지정 된 [최대 다운로드 대역폭 (KB/s)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-download-bandwidth) 하며 [최대 업로드 대역폭 (KB/s)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-upload-bandwidth) 장치는 모든 동시 배달 최적화 다운로드에서 사용할 수 있는 작업을 합니다.<br><br>Windows 1607 필요<br><br>정책 CSP: [DOMaxDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxdownloadbandwidth) 고 [DOMaxUploadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxuploadbandwidth)</li><br><li>**%** – 지정 된 [최대 전경 다운로드 대역폭 (%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-foreground-download-bandwidth) 및 [최대 백그라운드 다운로드 대역폭 (%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-foreground-download-bandwidth) 모든 동시 배달에서 장치를 사용할 수 있는 최적화 작업을 다운로드합니다.<br><br>Windows 1803 필요<br><br>정책 CSP: [DOPercentageMaxForegroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxforegroundbandwidth) 고 [DOPercentageMaxBackgroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxbackgroundbandwidth)    <br><br><li>**업무 시간을 사용 하 여 백분율** – 최대 [전경](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#set-business-hours-to-limit-foreground-download-bandwidth) 대역폭 및 최대 다운로드 [백그라운드](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#set-business-hours-to-limit-background-download-bandwidth) 다운로드 대역폭, 구성 업무 시간 시작 및 종료 시간을 다음의 사용 중 및 업무 시간 외에 대역폭의 비율입니다. <br><br>Windows 1803 필요 <br><br>정책 CSP: [DOSetHoursToLimitBackgroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitbackgrounddownloadbandwidth) 고 [DOSetHoursToLimitForegroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitforegrounddownloadbandwidth)<br><br>   |
|[초 단위로 지연 백그라운드 HTTP 다운로드](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#delay-background-download-from-http-in-secs) | 1803        | HTTP를 통해 콘텐츠의 백그라운드 다운로드를 지연 시키는 최대 시간을 구성 하려면이 설정을 사용 합니다. 이 다운로드를 지 원하는 피어-투-피어 다운로드 원본에만 적용 됩니다. 이 지연 하는 동안 장치가 사용 가능한 콘텐츠를 포함 하 여 피어를 검색합니다. 피어 원본을 기다리는 동안 다운로드를 최종 사용자에 게 표시 됩니다.   <br><br>**기본**: *없는 값을 구성*  <br><br>**권장**: 60 초   <br><br>정책 CSP: [DODelayBackgroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaybackgrounddownloadfromhttp) <br><br>    |
| [초 단위로 지연 전경 HTTP 다운로드](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#delay-foreground-download-from-http-in-secs)      | 1803       | HTTP를 통해 콘텐츠의 전경 (대화형) 다운로드를 지연 하는 최대 시간을 구성 합니다. 이 다운로드를 지 원하는 피어-투-피어 다운로드 원본에만 적용 됩니다. 이 지연 하는 동안 장치가 사용 가능한 콘텐츠를 포함 하 여 피어를 검색합니다. 피어 원본을 기다리는 동안 다운로드를 최종 사용자에 게 표시 됩니다.   <br><br>**기본**: *없는 값을 구성*  <br><br>**권장**: 60 초   <br><br>정책 CSP: [DODelayForegroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelayforegrounddownloadfromhttp) <br><br>         |


## <a name="caching"></a>캐싱  

|Setting  |Windows 버전  |세부 정보  |
|---------|---------|---------|
|[피어 캐싱 (GB)에 필요한 최소 RAM](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-ram-allowed-to-use-peer-caching)      | 1703        | 피어 캐시를 사용 하도록 장치를 포함 해야 하는 gb 최소 RAM 크기를 지정 합니다. <br><br>**기본**: *없는 값을 구성*  <br><br>**권장**: 4GB <br><br>정책 CSP: [DOMinRAMAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominramallowedtopeer) <br><br>        |
|[피어 캐싱 (GB)에 필요한 최소 디스크 크기](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-disk-size-allowed-to-use-peer-caching)      | 1703        | 피어 캐시를 사용 하도록 장치를 포함 해야 하는 Gb에서 최소 디스크 크기를 지정 합니다. <br><br>**기본**: *없는 값을 구성*  <br><br>**권장**: 32GB   <br><br>정책 CSP: [DOMinDiskSizeAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domindisksizeallowedtopeer) <br><br>    |
|[피어 캐싱 (MB)에 대 한 최소 콘텐츠 파일 크기](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-peer-caching-content-file-size)      | 1703        | 파일을 충족 해야 합니다 또는 피어 캐싱을 사용 하 여 초과 (mb)의 최소 크기를 지정 합니다.  <br><br>**기본**: *없는 값을 구성*  <br><br>**권장**: 10MB   <br><br>정책 CSP: [DOMinFileSizeToCache](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominfilesizetocache)  <br><br>      |
|[(%)에 업로드 하는 데 필요한 최소 배터리 수준](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#allow-uploads-while-the-device-is-on-battery-while-under-set-battery-level)      | 1709        | 장치 동료에 게 데이터를 업로드 해야 하는 최소 배터리 수준 백분율을 지정 합니다. 배터리 수준으로 지정된 된 값으로 떨어지면 모든 활성 업로드 자동으로 일시 중지 합니다.   <br><br>**기본**: *없는 값을 구성*  <br><br>**권장**: 40%   <br><br>정책 CSP: [DOMinBatteryPercentageAllowedToUpload](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominbatterypercentageallowedtoupload) <br><br>        |
|[캐시 드라이브를 수정 합니다.](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#modify-cache-drive)        | 1607        | 드라이브를 지정 합니다. 해당 캐시에 대 한 배달 최적화를 사용 합니다. 환경 변수, 드라이브 문자 또는 전체 경로 사용할 수 있습니다.  <br><br>**기본**: % SystemDrive % <br><br>정책 CSP: [DOModifyCacheDrive](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domodifycachedrive) <br><br>        |
| [최대 캐시 기간 (일)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-cache-age)    | 1511         | 파일을 장치에 배달 최적화 캐시에 저장 된는 각 파일이 성공적으로 다운로드 한 후에 시간이 방법을 지정 합니다.   <br><br>Intune을 사용 하 여 일 동안에서 캐시 보존 기간을 구성 합니다. 정의한 일 수가 정의 하는 방법 Windows이이 설정 되는 시간 (초), 해당 번호로 변환 됩니다. 예를 들어 3 일의 Intune 구성 259200 초 (3 일) 장치의 변환 됩니다.  <br><br>**기본**: *없는 값을 구성*     <br><br>**권장**: 7   <br><br>정책 CSP: [DOMaxCacheAge](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)  <br><br>          |
| 최대 캐시 크기 형식  | *세부 정보 참조*    | 배달 최적화에서 사용 되는 장치에서 디스크 공간의 크기를 관리 하는 방법을 선택 합니다. 구성 되지 않은 경우 사용할 수 있는 사용 가능한 디스크 공간의 20% 캐시 크기 기본값은입니다.  <br><ul><li>**구성되지 않음**(기본값)</li><br><li>**절대** – 지정 된 [절대 최대 캐시 크기 (GB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#absolute-max-cache-size) 배달 최적화에 대 한 장치를 사용할 수 드라이브 공간의 최대 크기를 구성 하려면. 0 (영)로 설정 하면 캐시 크기가 제한 있지만 장치 디스크 공간이 부족할 때 배달 최적화 캐시가 지워집니다. <br><br>Windows 1607 필요<br><br> 정책 CSP: [DOAbsoluteMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-doabsolutemaxcachesize) </li><br><li>**백분율** – 지정 된 [최대 캐시 크기 (%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-cache-size) 배달 최적화에 대 한 장치를 사용할 수 드라이브 공간의 최대 크기를 구성 하려면. 사용 가능한 드라이브 공간의 비율이 및 배달 최적화에서 지속적으로 사용 가능한 드라이브 공간을 평가 하 고 최대 캐시 크기 집합 비율을 유지 하려면 캐시가 지워집니다. <br><br>Windows 1511 필요<br><br>정책 CSP: [DOMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcachesize)  |
| [VPN 피어 캐싱](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#enable-peer-caching-while-the-device-connects-via-vpn)  | 1709  | 선택 **사용** 피어 캐싱 도메인 네트워크에 VPN을 통해 연결 되어 있는 동안에 참여 하도록 장치를 구성 합니다. 사용할 수 있는 장치에서 다운로드 하거나 다른 도메인 네트워크 장치에 VPN 또는 회사 도메인 네트워크에 업로드할 수 있습니다.  <br><br>**기본**: 구성 되지 않음  <br><br>정책 CSP: [DOAllowVPNPeerCaching](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)    |

## <a name="next-steps"></a>다음 단계

[Intune에서 배달 최적화 구성](delivery-optimization-windows.md)
