---
title: Microsoft Intune Certificate Connector 및 이벤트 ID 문제 해결 | Microsoft Docs
description: 이벤트 ID 및 설명을 검토하여 Microsoft Intune Certificate Connector 문제를 해결하고 Intune 커넥터 서비스의 진단 코드를 검토합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a282662032fe77cbf39da279c587bff31ad9e24
ms.sourcegitcommit: cf40f641af4746a1e34edd980dc6ec96fd040126
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70123226"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Intune Certificate Connector 이벤트 및 진단 코드

6\.1806.x.x 버전부터 Intune Connector 서비스는 **이벤트 뷰어**(**애플리케이션 및 서비스 로그** > **Microsoft Intune Connector**)에 이벤트를 기록합니다. 이러한 이벤트를 사용하여 Intune Connector 구성의 잠재적 문제를 해결할 수 있습니다. 이러한 이벤트는 작업의 성공과 실패를 기록하고, IT 관리자가 문제를 해결하는 데 도움이 되는 메시지와 함께 진단 코드를 포함합니다.

> [!TIP]  
> 이슈를 해결하고 Intune Connector 설정을 확인하려면 [인증 기관 스크립트 샘플](https://aka.ms/intuneconnectorverificationscript)을 참조하세요.

## <a name="event-ids-and-descriptions"></a>이벤트 ID 및 설명

| 이벤트 ID      | 이벤트 이름    | 이벤트 설명 | 관련 진단 코드 |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | 커넥터 서비스를 시작했습니다. | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | 커넥터 서비스를 중지했습니다. | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | 커넥터 등록 인증서를 갱신했습니다. | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | 커넥터 등록 인증서를 갱신하지 못했습니다. 커넥터를 다시 설치하세요. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | 레지스트리에서 커넥터 등록 인증서를 검색하지 못했습니다. 이 이벤트와 관련된 인증서 지문에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | 이벤트 세부 정보에서 진단 정보를 확인합니다. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | PKCS 인증서를 발급했습니다. 이 이벤트와 관련된 디바이스 ID, 사용자 ID, CA 이름, 인증서 템플릿 이름 및 인증서 지문에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | PKCS 인증서를 발급하지 못했습니다. 이 이벤트와 관련된 디바이스 ID, 사용자 ID, CA 이름, 인증서 템플릿 이름 및 인증서 지문에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | 인증서를 해지했습니다. 이 이벤트와 관련된 디바이스 ID, 사용자 ID, CA 이름 및 인증서 일련 번호에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | 인증서를 해지하지 못했습니다. 이 이벤트와 관련된 디바이스 ID, 사용자 ID, CA 이름 및 인증서 일련 번호에 대한 이벤트 세부 정보를 검토하세요. 자세한 내용은 NDES SVC 로그를 참조하세요.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | 인증서의 요청 또는 해지 데이터를 업로드했습니다. 업로드 세부 정보에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | 인증서의 요청 또는 해지 데이터를 업로드하지 못했습니다. 이벤트 세부 정보 > 업로드 상태를 차례로 검토하여 실패 지점을 확인하세요.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | 인증서 서명, 클라이언트 인증서 다운로드 또는 인증서 해지에 대한 요청을 다운로드했습니다. 다운로드 세부 정보에 대한 이벤트 세부 정보를 검토하세요.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | 인증서 서명, 클라이언트 인증서 다운로드 또는 인증서 해지에 대한 요청을 다운로드하지 못했습니다. 다운로드 세부 정보에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | 인증서 등록 지점에서 클라이언트 요청을 확인했습니다. | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | 인증서 등록 지점에서 완료했지만 요청을 거부했습니다. 자세한 내용은 진단 코드 및 메시지를 참조하세요. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | 인증서 등록 지점에서 클라이언트 챌린지를 확인하지 못했습니다. 자세한 내용은 진단 코드 및 메시지를 참조하세요. 챌린지에 해당하는 디바이스 ID에 대한 이벤트 메시지 세부 정보를 참조하세요. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | 인증서 등록 지점에서 알림 프로세스를 완료했고 인증서를 클라이언트 디바이스로 보냈습니다. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | 인증서 등록 지점에서 알림 프로세스를 완료하지 못했습니다. 요청에 대한 내용은 이벤트 메시지 세부 정보를 참조하세요. NDES 서버와 CA 간의 연결을 확인하세요. | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>진단 코드

| 진단 코드 | 진단 이름 | 진단 메시지 |
| -------------   | -------------   | -------------      |
| 0x00000000 | 성공  | 성공 |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | 인증 기관이 유효하지 않거나 연결할 수 없습니다. 인증 기관을 사용할 수 있고 서버에서 이 인증 기관과 통신할 수 있는지 확인하세요. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | 로컬 인증서 저장소에 Symantec 클라이언트 인증 인증서가 없습니다. 자세한 내용은 [Symantec Registration Authorization 인증서 설치](https://docs.microsoft.com/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate) 문서를 참조하세요.  |
| 0x00000402 | RevokeCert_AccessDenied  | 지정한 계정에 CA에서 인증서를 해지할 수 있는 권한이 없습니다. 이벤트 메시지 세부 정보의 CA 이름 필드를 참조하여 발급하는 CA를 확인하세요.  |
| 0x00000403 | CertThumbprint_NotFound  | 사용자 입력과 일치하는 인증서를 찾을 수 없습니다. 인증서 커넥터를 등록하고 다시 시도하세요. |
| 0x00000404 | Certificate_NotFound  | 제공된 입력과 일치하는 인증서를 찾을 수 없습니다. 인증서 커넥터를 다시 등록하고 다시 시도하세요. |
| 0x00000405 | Certificate_Expired  | 인증서가 만료되었습니다. 인증서 커넥터를 다시 등록하여 인증서를 갱신하고 다시 시도하세요. |
| 0x00000408 | CRPSCEPCert_NotFound  | CRP 암호화 인증서를 찾을 수 없습니다. NDES 및 Intune Connector가 올바르게 설정되어 있는지 확인하세요. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | 서명 인증서를 검색할 수 없습니다. Intune Connector 서비스가 올바르게 구성되어 있고 Intune Connector 서비스가 실행되고 있는지 확인하세요. 또한 인증서 다운로드 이벤트가 성공했는지도 확인하세요. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | SCEP 챌린지 요청을 역직렬화하지 못했습니다. NDES 및 Intune Connector가 올바르게 설정되어 있는지 확인하세요. |
| 0x00000411 | CRPSCEPChallenge_Expired  | 만료된 인증서 챌린지로 인해 요청이 거부되었습니다. 관리 서버에서 새 챌린지를 얻은 후에 클라이언트 디바이스에서 다시 시도할 수 있습니다. |
| 0x0FFFFFFFF | Unknown_Error  | 서버 쪽 오류가 발생하여 요청을 완료할 수 없습니다. 다시 시도하세요. |


## <a name="next-steps"></a>다음 단계
추가 지원이 필요하면 [Microsoft Intune에서 SCEP 인증서 프로필 배포 문제 해결](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune) 가이드를 참조하세요.
