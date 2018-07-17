---
title: Microsoft Intune에 대한 네트워크 요구 사항 및 대역폭 세부 정보
titlesuffix: ''
description: Intune에 대한 네트워크 구성 요구 사항 및 대역폭 세부 정보를 검토합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c161d1ca120d5a0210cffca01e781f1ae9206fe4
ms.sourcegitcommit: 2198a39ae48beca5fc74316976bc3fc9db363659
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38225360"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune 네트워크 구성 요구 사항 및 대역폭

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Intune 관리자는 이 문서의 지침을 참조하여 Intune 서비스의 네트워크 요구 사항을 파악할 수 있습니다. 이 문서의 정보를 참조하여 프록시 설정에 필요한 IP 주소 및 포트 설정과 대역폭 요구 사항을 파악할 수 있습니다.

## <a name="average-network-traffic"></a>평균 네트워크 트래픽
이 표에는 각 클라이언트의 네트워크를 통해 전송되는 공통 콘텐츠의 대략적인 크기 및 주기가 정리되어 있습니다.

> [!NOTE]
> 장치가 Intune에서 업데이트 및 콘텐츠를 받을 수 있도록 하려면 해당 장치를 인터넷에 주기적으로 연결해야 합니다. 업데이트나 콘텐츠를 받는 데 필요한 시간은 경우에 따라 다르지만 매일 1시간 이상 인터넷에 계속 연결된 상태를 유지해야 합니다.

|콘텐츠 유형|대략적인 크기|주기 및 세부 정보|
|----------------|--------------------|-------------------------|
|Intune 클라이언트 설치<br /><br />**Intune 클라이언트 설치 외에도 다음 요구 사항을 충족해야 합니다.**|125 MB|**한 번**<br /><br />클라이언트 다운로드 크기는 클라이언트 컴퓨터의 운영 체제에 따라 다릅니다.|
|클라이언트 등록 패키지|15 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|Endpoint Protection 에이전트|65 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|Operations Manager 에이전트|11 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|정책 에이전트|3 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|Microsoft Easy Assist 에이전트를 통한 원격 지원|6 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|클라이언트의 일별 작업|6 MB|**매일**<br /><br />Intune 클라이언트는 Intune 서비스와 정기적으로 통신하여 업데이트 및 정책을 확인하고 클라이언트의 상태를 서비스에 보고합니다.|
|Endpoint Protection 맬웨어 정의 업데이트|상황에 따라 다름<br /><br />일반적으로 40KB -2MB|**매일**<br /><br />하루에 최대 3번|
|Endpoint Protection 엔진 업데이트|5 MB|**매월**|
|소프트웨어 업데이트|상황에 따라 다름<br /><br />크기는 배포하는 업데이트에 따라 달라집니다.|**매월**<br /><br />일반적으로 소프트웨어 업데이트는 매월 두 번째 화요일에 배포됩니다.<br /><br />새로 등록되거나 배포된 컴퓨터는 이전에 배포된 업데이트의 전체 집합을 다운로드하는 동안 네트워크 대역폭을 추가로 사용할 수 있습니다.|
|서비스 팩|상황에 따라 다름<br /><br />크기는 배포하는 각 서비스 팩에 따라 달라집니다.|**상황에 따라 다름**<br /><br />서비스 팩을 배포하는 시기에 따라 달라집니다.|
|소프트웨어 배포|상황에 따라 다름<br /><br />크기는 배포하는 소프트웨어에 따라 달라집니다.|**상황에 따라 다름**<br /><br />소프트웨어를 배포하는 시기에 따라 달라집니다.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>네트워크 대역폭 사용량을 줄이는 방법
다음 방법 중 하나 이상을 사용하여 Intune 클라이언트의 네트워크 대역폭 사용을 줄일 수 있습니다.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>프록시 서버를 사용하여 콘텐츠 요청 캐시
프록시 서버는 콘텐츠를 캐시하여 중복 다운로드를 줄이고 인터넷에서 콘텐츠의 네트워크 대역폭을 줄일 수 있습니다.

클라이언트 컴퓨터에서 콘텐츠를 받는 캐싱 프록시 서버는 해당 콘텐츠를 검색하고 웹 응답 및 다운로드를 모두 캐시할 수 있습니다. 서버는 캐시된 데이터를 사용하여 클라이언트의 후속 요청에 응답합니다.

다음은 Intune 클라이언트의 콘텐츠를 캐시할 프록시 서버에 사용하는 일반적인 설정입니다.


|          Setting           |           권장 값           |                                                                                                  세부 정보                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         캐시 크기         |             5GB - 30GB             | 값은 사용하는 구성 및 네트워크의 클라이언트 컴퓨터의 수에 따라 달라집니다. 파일이 너무 빠르게 삭제되지 않도록 하려면 환경에 맞게 캐시 크기를 조정하세요. |
| 개별 캐시 파일 크기 |                950 MB                 |                                                                     이 설정은 모든 캐싱 프록시 서버에서 사용할 수 없습니다.                                                                     |
|   캐시할 개체 유형    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Intune 패키지는 HTTP를 통한 BITS(Background Intelligent Transfer Service) 다운로드로 검색되는 CAB 파일입니다.                                               |

프록시 서버를 사용하여 콘텐츠를 캐시하는 방법에 대해서는 사용 중인 프록시 서버 솔루션의 설명서를 참조하세요.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>컴퓨터에서 BITS(Background Intelligent Transfer Service) 사용
Intune은 Windows 컴퓨터에서 BITS(Background Intelligent Transfer Service)를 사용할 수 있도록 지원하여 구성한 시간 동안 컴퓨터에서 사용하는 네트워크 대역폭을 줄여 줍니다. Intune 에이전트 정책의 **네트워크 대역폭** 페이지에서 BITS에 대한 정책을 구성할 수 있습니다.

BITS 및 Windows 컴퓨터에 대한 자세한 내용은 TechNet 라이브러리의 [Background Intelligent Transfer Service](http://technet.microsoft.com/library/bb968799.aspx)를 참조하세요.

### <a name="use-branchcache-on-computers"></a>컴퓨터에서 BranchCache 사용
Intune 클라이언트는 BranchCache를 사용하여 WAN(광역 네트워크) 트래픽을 줄일 수 있습니다. 다음 운영 체제에서 BranchCache를 지원합니다.

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

BranchCache를 사용하려면 클라이언트 컴퓨터에서 BranchCache를 사용하도록 설정한 후 **분산 캐시 모드**에 대해 구성해야 합니다.

기본적으로 BranchCache 및 분산 캐시 모드는 Intune 클라이언트를 설치할 때 컴퓨터에서 사용되도록 설정됩니다. 그러나 그룹 정책에서 BranchCache를 사용하지 않도록 설정한 경우 Intune에서 해당 정책을 재정의하지 않으므로 BranchCache는 계속 사용되지 않도록 설정됩니다.

BranchCache를 사용하는 경우 조직의 다른 관리자와 함께 그룹 정책 및 Intune 방화벽 정책을 관리합니다. BranchCache 또는 방화벽 예외를 사용하지 않도록 설정하는 정책을 배포하지 않아야 합니다. BranchCache에 대한 자세한 내용은 [BranchCache 개요](http://technet.microsoft.com/library/hh831696.aspx)를 참조하세요.

## <a name="network-communication-requirements"></a>네트워크 통신 요구 사항

관리하는 장치와 클라우드 기반 서비스에 필요한 웹 사이트 간에 네트워크 통신을 사용하도록 설정합니다.

Intune은 Intune 소프트웨어를 실행하는 서버와 같은 온-프레미스 인프라를 사용하지 않지만 Exchange 및 Active Directory 동기화 도구를 비롯하여 온-프레미스 인프라를 사용할 수 있는 옵션은 있습니다.

방화벽 및 프록시 서버로 보호되는 컴퓨터를 관리하려면 Intune에 대한 통신을 사용하도록 설정해야 합니다.

-   프록시 서버는 **HTTP(80)** 와 **HTTPS(443)** 를 모두 지원해야 합니다. Intune 클라이언트에서 두 프로토콜을 모두 사용하기 때문입니다.
-   Intune에서 소프트웨어 및 업데이트 다운로드 등의 일부 작업을 수행하려면 manage.microsoft.com에 대한 인증되지 않은 프록시 서버 액세스가 필요합니다.

개별 클라이언트 컴퓨터에서 프록시 서버 설정을 수정할 수도 있고, 그룹 정책을 사용하여 지정된 프록시 서버로 보호되는 모든 클라이언트 컴퓨터의 설정을 변경할 수도 있습니다.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

관리되는 장치를 사용하려면 **모든 사용자**가 방화벽을 통해 서비스에 액세스할 수 있도록 구성해야 합니다.

다음 표에는 Intune 클라이언트에서 액세스하는 포트 및 서비스가 정리되어 있습니다.

|**도메인**|**IP 주소**|
|---------------------|-----------|
|login.microsoftonline.com | 추가 정보: [Office 365 URL 및 IP 주소 범위](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |  13.64.198.190|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |13.64.188.173|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |40.71.32.174|
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |13.64.197.181 |
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |40.71.38.205|
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |13.64.191.182 |
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |40.71.37.51 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |40.118.250.246 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |13.90.142.194 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.64.250.226 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.90.151.142 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.169.155.165 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.174.188.97 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.178.190.24 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.174.16.215 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |40.69.69.27 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |52.166.196.199 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |40.69.71.164 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |52.174.182.102 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |40.69.78.145 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |52.174.192.105 |
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |13.94.46.250|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |52.163.119.15 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |13.75.124.145 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |52.163.119.5|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.175.35.226|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.163.119.6|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.175.38.24|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.163.119.3|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|23.97.165.17|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|

### <a name="apple-device-network-information"></a>Apple 장치 네트워크 정보

|         호스트 이름         |                                        URL(IP 주소/서브넷)                                        |  프로토콜  |     포트     |                          장치                           |
|--------------------------|-------------------------------------------------------------------------------------------------------|------------|--------------|-----------------------------------------------------------|
|      관리 사용자       |                                  gateway.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2195     |                    Apple iOS 및 macOS                    |
|      관리 사용자       |                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |                    Apple iOS 및 macOS                    |
|      관리 사용자       | Apple iTunesitunes.apple.com, \*.mzstatic.com, \*.phobos.apple.com, \*.phobos.apple.com.edgesuite.net |    HTTP    |      80      |                    Apple iOS 및 macOS                    |
|        PI Server         |                gateway.push.apple.com(17.0.0.0/8) feedback.push.apple.com(17.0.0.0/8)                 |    TCP     |  2195, 2196  |         Apple iOS와 macOS 클라우드 메시징의 경우입니다.          |
|     장치 서비스      |                                        gateway.push.apple.com                                         |    TCP     |     2195     |                           Apple                           |
|     장치 서비스      |                                        feedback.push.apple.com                                        |    TCP     |     2196     |                           Apple                           |
|     장치 서비스      |   Apple iTunesitunes.apple.com \*.mzstatic.com\*.phobos.apple.com \*.phobos.apple.com.edgesuite.net   |    HTTP    |      80      |                           Apple                           |
| 장치(인터넷/Wi-Fi) |                                 #-courier.push.apple.com(17.0.0.0/8)                                  |    TCP     | 5223 및 443 | Apple에만 해당합니다. &#39;#&#39;는 0~200 사이의 임의 숫자입니다. |
| 장치(인터넷/Wi-Fi) |                           phobos.apple.comocsp.apple.comax.itunes.apple.com                           | HTTP/HTTPS |  80 또는 443   |                        Apple에만 해당합니다.                         |

