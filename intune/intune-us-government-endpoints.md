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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4712c2958e2beee8853ad0d2620414d823da327
ms.sourcegitcommit: 6e07c35145f70b008cf170bae57143248a275b67
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804504"
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
- Azure Portal: https://portal.azure.us/ 
- Office 365: https://portal.office365.us/ 
- Intune 회사 포털: https://portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Intune이 의존하는 파트너 서비스 엔드포인트:
- AAD 동기화 서비스: https://syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https://login.microsoftonline.us
- 디렉터리 프록시: https://directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph: https://directory.microsoftazure.us 및 https://graph.microsoftazure.us
- MS Graph: https://graph.microsoft.us
- ADRS: https://enterpriseregistration.microsoftonline.us
