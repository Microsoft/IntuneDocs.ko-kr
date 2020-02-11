---
title: Microsoft Intune Certificate Connector 정책 모듈 문제 해결 | Microsoft Docs
description: SCEP 인증서 프로필을 사용하여 Intune을 통해 인증서를 배포할 때 NDES 정책 모듈이 인증서 요청을 처리하는 경우의 정책 모듈 작업 문제를 해결합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915839"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>Microsoft Intune에서 NDES 정책 모듈 문제 해결

이 문서의 정보는 Microsoft Intune Certificate Connector와 함께 설치되는 NDES(네트워크 장치 등록 서비스) 정책 모듈 작업의 유효성을 검사하는 데 도움이 됩니다. NDES가 인증서에 대한 요청을 받아 정책 모듈에 전달하면 정책 모듈은 요청의 유효성을 검사하여 디바이스에 유효한 것으로 확인합니다. 유효성 검사 후 NDES는 CA(인증 기관)에 연결하여 디바이스를 대신해 인증서를 요청합니다.

이 문서는 [SCEP 통신 워크플로](troubleshoot-scep-certificate-profiles.md)의 3단계 및 4단계에 적용됩니다.

## <a name="ndes-communication-to-the-policy-module"></a>정책 모듈에 대한 NDES 통신

디바이스에서 인증서 요청을 받은 후 NDES는 Microsoft Intune Certificate Connector와 함께 설치되는 정책 모듈을 통해 Intune을 사용하여 요청의 유효성을 검사합니다. 이러한 항목은 *인증서 등록 지점*을 참조합니다.

**성공을 나타내는 로그 항목**:

모듈에 유효성 검사 요청이 제출되었는지 확인하려면 NDES 서버의 로그에서 다음 예와 유사한 항목을 찾습니다.

- **IIS 로그**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **NDESPlugin 로그**:

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  다음 예는 디바이스 챌린지 요청의 유효성 검사에 성공하고 NDES가 이제 CA에 연결할 수 있음을 나타냅니다.

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**성공 표시기가 없는 경우**:

이러한 항목을 찾을 수 없는 경우 먼저 [디바이스와 NDES 서버 통신](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors)의 문제 해결 가이드를 검토합니다.

해당 문서의 정보를 통해 문제를 해결할 수 없는 경우 문제를 나타낼 수 있는 추가 항목은 다음과 같습니다.

### <a name="ndespluginlog-contains-an-error-12175"></a>NDESPlugin.log에 오류 12175가 포함됨

로그에 다음과 유사한 오류 12175이 포함되어 있다면 SSL 인증서에 문제가 있을 수 있습니다.

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

최신 브라우저 및 모바일 디바이스의 브라우저는*주체 대체 이름*이 있는 경우 SSL 인증서에서 *일반 이름*을 무시합니다.

**해결 방법**:  *일반 이름* 및 *주체 대체 이름*에 대해 다음 특성을 사용하여 웹 서버 SSL 인증서를 발급한 다음 IIS에서 443 포트에 바인딩합니다.

  - **주체 이름**  
    CN = 외부 서버 이름
  - **주체 대체 이름**  
     Name = 외부 서버 이름  
     DNS Name = 내부 서버 이름

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>NDESPlugin.log에 오류 403 - 사용할 수 없음: 액세스가 거부되었습니다"가 포함됨

다음 로그에 다음과 유사한 오류 403이 포함되어 있는 경우 클라이언트 인증서가 신뢰되지 않거나 잘못된 것일 수 있습니다.

**NDESPlugin.log**:

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**IIS 로그**:

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

이 문제는 NDES 서버의 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 중간 CA 인증서가 있는 경우에 발생합니다.

인증서의 *발급 대상* 값과 *발급자* 값이 동일하다면 루트 인증서입니다. 그렇지 않으면 중간 인증서입니다.

**해결 방법**: 이 문제를 해결하려면 신뢰할 수 있는 루트 인증 기관 인증서 저장소에서 중간 CA 인증서를 식별하고 제거합니다.

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>NDESPlugin.log에 챌린지가 false를 반환한다고 표시됩니다

챌린지의 결과가 **false**를 반환하면 *CertificateRegistrationPoint.svclog*에서 오류를 확인합니다. 예를 들어 다음 항목과 유사한 "서명 인증서를 검색할 수 없습니다" 오류가 표시될 수 있습니다.

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**해결 방법**: 커넥터가 설치된 서버에서 레지스트리 편집기를 열고 `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector` 레지스트리 키를 찾은 다음 SigningCertificate 값이 있는지 확인합니다.

이 값이 없으면 services.msc에서 Intune Connector Service를 다시 시작한 다음 값이 레지스트리에 표시되는지 확인합니다. 그래도 값이 없는 경우 NDES 서버와 Intune 서비스 간의 네트워크 연결 문제가 원인인 경우가 많습니다.

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES는 인증서 발급 요청을 전달합니다.

인증서 등록 지점(정책 모듈)에 의한 유효성 검사가 성공한 후 NDES는 디바이스를 대신하여 CA에 인증서 요청을 전달합니다.

**성공을 나타내는 로그 항목**:

- **NDESPlugin 로그**:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **IIS 로그**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**성공 표시기가 없는 경우**:

성공을 나타내는 항목이 표시되지 않으면 다음 단계를 따릅니다.

1. 인증서 등록 지점에서 챌린지를 확인할 때 *CertificateRegistrationPoint.svclog*에 기록된 문제를 찾습니다. 다음 줄 사이에 있는 항목을 찾습니다.

   - VerifyRequest Started.
   - VerifyRequest Finished with status False

2. CA에서 인증 기관 MMC를 열고 **실패한 요청**을 선택하여 문제를 식별하는 데 도움이 되는 오류를 찾습니다. 다음 이미지는 예입니다.

   ![실패한 요청의 예](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. CA의 애플리케이션 이벤트 로그에서 오류를 검토합니다. 일반적으로 이전 단계에서 **실패한 요청**에 표시되는 것과 일치하는 오류를 볼 수 있습니다. 다음 이미지는 예입니다.

   ![애플리케이션 로그 검토](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>다음 단계

NDES 정책 모듈이 요청의 유효성을 검사하고 요청이 인증 기관에 전달되면 다음 단계는 [디바이스에 대한 인증서 배달](troubleshoot-scep-certificate-delivery.md)을 검토하는 것입니다.
