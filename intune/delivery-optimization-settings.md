---
title: Intune에 대한 Windows 10 전송 최적화 설정 | Microsoft Docs
description: Intune을 사용하여 배포할 수 있는 Windows 10 디바이스의 전송 최적화 설정입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ab4871da52f5df0aec0a698f31daa5608a57c1c3
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67493898"
---
# <a name="delivery-optimization-settings-for-intune"></a>Intune의 전송 최적화 설정

이 문서에서는 Intune에서 지원하는 Windows 10 이상을 실행하는 디바이스의 전송 최적화 설정을 나열합니다.  

대부분의 Intune 콘솔 옵션은 직접 매핑하여 최적화 설정을 제공합니다. 최적화 설정에 대한 자세한 내용은 Windows 설명서에 나와 있으며, 관련 콘텐츠에 대한 링크가 제공됩니다.  Intune과 관련된 설정 또는 옵션에는 추가 콘텐츠 링크가 없습니다.  

아래 표에는 다음 항목이 포함되어 있습니다.  

- **설정**: Intune에 표시되는 설정입니다. 링크인 설정은 설정에 대해 자세히 알아볼 수 있는 Windows 설명서의 [Windows 10 업데이트에 대한 전송 최적화 구성](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) 관련 항목을 엽니다.

- **Windows 버전**: 이 설정을 지원하는 Windows 10 최소 버전입니다.  

- **세부 정보**: Intune 기본값을 포함하여 Intune이 설정을 구현하는 방법에 대한 간략한 설명입니다. 세부 정보가 있는 경우 [전송 최적화 정책 CSP(구성 서비스 공급자)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization) 항목의 링크가 제공됩니다.  

이러한 설정을 사용하도록 Intune을 구성하려면 [업데이트 전송](delivery-optimization-windows.md)을 참조하세요.  

## <a name="delivery-optimization"></a>배달 최적화  

|Setting  |Windows 버전  |세부 정보  |
|---------|-----------------|---------|
| [다운로드 모드](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#download-mode)     | 1511         | 전송 최적화에서 콘텐츠 다운로드에 사용할 방법을 지정합니다.<br><ul><li>**구성되지 않음**: 최종 사용자는 운영 체제에서 제공되는 *Windows 업데이트 또는 제공 최적화* 설정을 사용할 수 있는 고유한 방법으로 해당 디바이스를 업데이트합니다. </li> <li> **HTTP만, 피어링 없음(0)** : 인터넷에서만 업데이트를 가져옵니다. 네트워크의 다른 컴퓨터(피어 투 피어)에서 업데이트를 가져오지 마세요. </li> <li> **동일한 NAT 뒤의 피어링과 혼합된 HTTP(1)** : 인터넷 및 네트워크의 다른 컴퓨터에서 업데이트를 가져옵니다. </li> <li> **프라이빗 그룹에서 피어링과 혼합된 HTTP(2)** : 동일한 Active Directory 사이트(있는 경우) 또는 동일한 도메인의 디바이스에서 피어링이 발생합니다. 이 옵션을 선택하면 피어링이 NAT(Network Address Translation) IP 주소를 교차합니다. </li> <li> **인터넷 피어링과 혼합된 HTTP(3)** : 인터넷 및 네트워크의 다른 컴퓨터에서 업데이트를 가져옵니다. </li> <li> **피어링이 없는 단순 다운로드 모드(99)** : Microsoft와 같은 업데이트 소유자로부터 직접 인터넷에서 업데이트를 가져옵니다. 배달 최적화 클라우드 서비스에는 연결하지 않습니다. </li> <li> **바이패스 모드(100)** : BITS(Background Intelligent Transfer Service)를 사용하여 업데이트를 가져옵니다. 배달 최적화를 사용하지 마세요. </li></ul> **기본값**: 구성되지 않음  <br><br> 정책 CSP: [DODownloadMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodownloadmode)  <br><br>  |
| [피어 선택 제한](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#select-a-method-to-restrict-peer-selection)          | 1803        | **다운로드 모드**를 *동일한 NAT 뒤의 피어링과 혼합된 HTTP(1)* 또는 *프라이빗 그룹에서 피어링과 혼합된 HTTP(2)* 로 설정해야 합니다.<br/><br/>피어 선택을 디바이스의 특정 그룹으로 제한합니다.<br/><br/>**기본값**: 구성되지 않음 <br/><br/>정책 CSP: [DORestrictPeerSelectionBy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dorestrictpeerselectionby)<br><br>      |
| [그룹 ID 원본](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#select-the-source-of-group-ids)     | 1803        | **다운로드 모드**를 *프라이빗 그룹에서 피어링과 혼합된 HTTP*로 설정해야 합니다.<br><br>피어 선택을 원본별 디바이스의 특정 그룹으로 제한합니다.<br><br>**사용자 지정**을 선택하는 경우 **그룹 ID(GUID)** 를 구성합니다. 다른 도메인에 있거나 동일한 LAN에 있지 않은 분기의 로컬 네트워크 피어링을 위한 단일 그룹을 만들어야 하는 경우 그룹 ID로 GUID를 사용합니다.<br><br>**기본값**: 구성되지 않음 <br><br>정책 CSP: [DOGroupId](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dogroupid)     |

## <a name="bandwidth"></a>대역폭  

|Setting  |Windows 버전  |세부 정보  |
|---------|---------|---------|
|대역폭 최적화 형식     | *세부 정보 참조*        | 전송 최적화가 모든 동시 다운로드 작업에 사용할 수 있는 최대 대역폭을 Intune이 어떻게 결정하게 할 것인지 선택합니다.<br><br>다음 옵션을 사용할 수 있습니다.<br><ul><li>**구성되지 않음**</li><br><li>**절대** – 디바이스가 모든 동시 전송 최적화 다운로드 작업에 사용할 수 있는 [최대 다운로드 대역폭(KB/s)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-download-bandwidth) 및 [최대 업로드 대역폭(KB/s)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-upload-bandwidth)을 지정합니다.<br><br>Windows 1607 필요<br><br>정책 CSP: [DOMaxDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxdownloadbandwidth) 및 [DOMaxUploadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxuploadbandwidth)</li><br><li>**백분율** – 디바이스가 모든 동시 전송 최적화 다운로드 작업에 사용할 수 있는 [최대 포그라운드 다운로드 대역폭(%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth) 및 [최대 백그라운드 다운로드 대역폭(%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth)을 지정합니다.<br><br>Windows 1803 필요<br><br>정책 CSP: [DOPercentageMaxForegroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxforegroundbandwidth) 및 [DOPercentageMaxBackgroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxbackgroundbandwidth)    <br><br><li>**업무 시간을 사용하는 백분율** – 최대 [포그라운드](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-foreground-download-bandwidth) 다운로드 대역폭 및 최대 [백그라운드](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-background-download-bandwidth) 다운로드 대역폭의 경우 업무 시간 시작 및 종료 시간을 구성한 다음, 업무 시간과 업무 외 시간에 사용할 대역폭 백분율을 구성합니다. <br><br>Windows 1803 필요 <br><br>정책 CSP: [DOSetHoursToLimitBackgroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitbackgrounddownloadbandwidth) 및 [DOSetHoursToLimitForegroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitforegrounddownloadbandwidth)<br><br>   |
|[백그라운드 HTTP 다운로드 지연(초)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-background-download-from-http-in-secs) | 1803        | HTTP를 통한 콘텐츠의 백그라운드 다운로드를 지연하는 최대 시간을 구성하려면 이 설정을 사용합니다. 이 설정은 피어-투-피어 다운로드 원본을 지원하는 다운로드에만 적용됩니다. 이 지연 시간 동안 디바이스는 콘텐츠를 사용할 수 있는 피어를 검색합니다. 피어 원본을 기다리는 동안 최종 사용자에게는 다운로드가 중단된 것처럼 보입니다.   <br><br>**기본값**: *값을 구성하지 않음*  <br><br>**권장**: 60초   <br><br>정책 CSP: [DODelayBackgroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaybackgrounddownloadfromhttp) <br><br>    |
| [포그라운드 HTTP 다운로드 지연(초)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-foreground-download-from-http-in-secs)      | 1803       | HTTP를 통한 콘텐츠의 포그라운드(대화형) 다운로드를 지연하는 최대 시간을 구성합니다. 이 설정은 피어-투-피어 다운로드 원본을 지원하는 다운로드에만 적용됩니다. 이 지연 시간 동안 디바이스는 콘텐츠를 사용할 수 있는 피어를 검색합니다. 피어 원본을 기다리는 동안 최종 사용자에게는 다운로드가 중단된 것처럼 보입니다.   <br><br>**기본값**: *값을 구성하지 않음*  <br><br>**권장**: 60초   <br><br>정책 CSP:  [DODelayForegroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelayforegrounddownloadfromhttp) <br><br>         |


## <a name="caching"></a>캐싱  

|Setting  |Windows 버전  |세부 정보  |
|---------|---------|---------|
|[피어 캐싱에 필요한 최소 RAM(GB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-ram-inclusive-allowed-to-use-peer-caching)      | 1703        | 디바이스가 피어 캐시를 사용하기 위해 필요한 최소 RAM 크기를 GB 단위로 지정합니다. <br><br>**기본값**: *값을 구성하지 않음*  <br><br>**권장**: 4GB <br><br>정책 CSP: [DOMinRAMAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominramallowedtopeer) <br><br>        |
|[피어 캐싱에 필요한 최소 디스크 크기(GB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-disk-size-allowed-to-use-peer-caching)      | 1703        | 디바이스가 피어 캐시를 사용하기 위해 필요한 최소 디스크 크기를 GB 단위로 지정합니다. <br><br>**기본값**: *값을 구성하지 않음*  <br><br>**권장**: 32GB   <br><br>정책 CSP: [DOMinDiskSizeAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domindisksizeallowedtopeer) <br><br>    |
|[피어 캐싱에 필요한 최소 콘텐츠 파일 크기(MB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-peer-caching-content-file-size)      | 1703        | 피어 캐싱을 사용하기 위해 파일이 충족 또는 초과해야 하는 최소 크기를 MB 단위로 지정합니다.  <br><br>**기본값**: *값을 구성하지 않음*  <br><br>**권장**: 10MB   <br><br>정책 CSP: [DOMinFileSizeToCache](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominfilesizetocache)  <br><br>      |
|[업로드에 필요한 최소 배터리 수준(%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#allow-uploads-while-the-device-is-on-battery-while-under-set-battery-level)      | 1709        | 디바이스가 피어에 데이터를 업로드하기 위해 필요한 최소 배터리 수준을 백분율로 지정합니다. 배터리 잔량이 지정된 값 아래로 떨어지면 진행 중인 업로드가 자동으로 일시 중지됩니다.   <br><br>**기본값**: *값을 구성하지 않음*  <br><br>**권장**: 40%   <br><br>정책 CSP: [DOMinBatteryPercentageAllowedToUpload](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominbatterypercentageallowedtoupload) <br><br>        |
|[캐시 드라이브 수정](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#modify-cache-drive)        | 1607        | 전송 최적화에서 캐시에 사용되는 드라이브를 지정합니다. 환경 변수, 드라이브 문자 또는 전체 경로를 사용할 수 있습니다.  <br><br>**기본값**:  %SystemDrive% <br><br>정책 CSP: [DOModifyCacheDrive](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domodifycachedrive) <br><br>        |
| [최대 캐시 기간(일)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-cache-age)    | 1511         | 각 파일이 성공적으로 다운로드된 후 디바이스의 전송 최적화 캐시에 파일을 보관하는 기간을 지정합니다.   <br><br>Intune에서는 캐시 기간을 일 단위로 구성합니다. 사용자가 정의하는 일 수는 해당 시간(초)으로 변환되며, Windows는 이 방식으로 이 설정을 정의합니다. 예를 들어 Intune 구성 3일은 디바이스에서 259200초(3일)로 변환됩니다.  <br><br>**기본값**: *값을 구성하지 않음*     <br><br>**권장**: 7   <br><br>정책 CSP: [DOMaxCacheAge](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)  <br><br>          |
| 최대 캐시 크기 형식  | *세부 정보 참조*    | 전송 최적화에 사용되는 디바이스의 디스크 공간 크기를 관리하는 방법을 선택합니다. 구성하지 않을 경우 캐시 크기는 기본적으로 사용 가능한 디스크 공간의 20%로 설정됩니다.  <br><ul><li>**구성되지 않음**(기본값)</li><br><li>**절대** – 디바이스가 전송 최적화에 사용할 수 있는 최대 드라이브 공간 크기를 구성하는 [절대 최대 캐시 크기(GB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#absolute-max-cache-size)를 지정합니다. 0으로 설정하면 캐시 크기 제한이 사라집니다. 단, 디바이스의 디스크 공간이 얼마 남지 않으면 전송 최적화에서 캐시를 지웁니다. <br><br>Windows 1607 필요<br><br> 정책 CSP: [DOAbsoluteMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-doabsolutemaxcachesize) </li><br><li>**백분율** – 디바이스가 전송 최적화에 사용할 수 있는 최대 드라이브 공간 크기를 구성하는 [최대 캐시 크기(%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-cache-size)를 지정합니다. 백분율은 사용 가능한 드라이브 공간을 의미하며, 전송 최적화에서는 사용 가능한 드라이브 공간을 지속적으로 평가하여 최대 캐시 크기가 설정된 백분율을 넘지 않도록 캐시를 지웁니다. <br><br>Windows 1511 필요<br><br>정책 CSP: [DOMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcachesize)  |
| [VPN 피어 캐싱](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#enable-peer-caching-while-the-device-connects-via-vpn)  | 1709  | **사용**을 선택하여 VPN을 통해 도메인 네트워크에 연결되어 있는 동안 피어 캐싱에 참여하도록 디바이스를 구성합니다. 사용하도록 설정된 디바이스는 VPN 또는 회사 도메인 네트워크의 다른 도메인 네트워크에(서) 업로드 또는 다운로드할 수 있습니다.  <br><br>**기본값**: 구성되지 않음  <br><br>정책 CSP: [DOAllowVPNPeerCaching](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)    |

## <a name="next-steps"></a>다음 단계

[Intune에서 전송 최적화 구성](delivery-optimization-windows.md)
