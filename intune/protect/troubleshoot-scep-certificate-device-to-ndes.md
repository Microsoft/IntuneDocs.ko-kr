---
title: Microsoft Intune에서 관리되는 디바이스와 NDES의 통신 문제 해결 | Microsoft Docs
description: SCEP 인증서 프로필을 사용하여 Intune으로 인증서를 배포하는 경우 관리되는 디바이스와 NDES 서버의 통신 문제를 해결합니다.
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
ms.openlocfilehash: 7945f1df3ddf1a6ff2c42a537e1071d1b5acff24
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514271"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>Microsoft Intune에서 SCEP 인증서 프로필의 디바이스와 NDES 서버의 통신 문제 해결

다음 정보를 사용하여 Intune SCEP(단순 인증서 등록 프로토콜) 인증서 프로필을 수신하고 처리한 디바이스가 NDES(네트워크 장치 등록 서비스)에 연결하여 챌린지를 제공할 수 있는지 확인합니다. 디바이스에서 프라이빗 키가 생성되고 인증서 서명 요청(CSR) 및 챌린지가 디바이스에서 NDES 서버로 전달됩니다. 디바이스는 NDES 서버에 연결하기 위해 SCEP 인증서 프로필의 URI를 사용합니다.

이 문서에서는 [SCEP 통신 흐름 개요](troubleshoot-scep-certificate-profiles.md)의 2단계를 참조합니다.

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>디바이스에서 연결에 대한 IIS 로그 검토

IIS 로그에는 모든 플랫폼에 동일한 유형의 항목이 포함되어 있습니다.


1. NDES 서버에서 다음 폴더에 있는 가장 최근 IIS 로그 파일을 엽니다.   *%SystemDrive%\inetpub\logs\logfiles\w3svc1*

2. 로그에서 다음 예와 유사한 항목을 검색합니다. 두 예 모두 끝 근처에 표시되는 상태 **200**을 포함합니다.

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   And

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. 디바이스에서 IIS에 연결하면 mscep.dll에 대한 HTTP GET 요청이 기록됩니다.

   이 요청의 끝 근처에 있는 상태 코드를 검토합니다.
   - **상태 코드 200**: 이 상태는 NDES 서버와의 연결이 성공했음을 나타냅니다.
   - **상태 코드 500**: IIS_IURS 그룹에 올바른 권한이 없을 수 있습니다. 이 문서 뒷부분의 [상태 코드 500](#status-code-500)을 참조하세요.
   - 상태 코드가 200 또는 500이 아닌 경우:

     - 구성의 유효성을 검사하려면 이 문서 뒷부분의 [SCEP 서버 URL 테스트](#test-the-scep-server-url)를 참조하세요.

     - 자주 발생하지 않는 오류 코드에 대한 자세한 내용은 [IIS 7 이상 버전의 HTTP 상태 코드](https://support.microsoft.com/help/943891)를 참조하세요.

   연결 요청이 전혀 기록되지 않으면 디바이스와 NDES 서버 간 네트워크에서 디바이스로부터의 연결이 차단된 것일 수 있습니다.

## <a name="review-device-logs-for-connections-to-ndes"></a>NDES와의 연결에 대한 디바이스 로그 검토

### <a name="android-devices"></a>Android 디바이스

[디바이스 OMADM 로그](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)를 검토합니다. 디바이스가 NDES에 연결될 때 기록되는 다음과 유사한 항목을 찾습니다.

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

주요 항목에는 다음 샘플 텍스트 문자열이 포함됩니다.

- There are 1 requests
- Received '200 OK' when sending GetCACaps(ca) to https://\<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
- Signing pkiMessage using key belonging to [dn=CN=\<username>; serial=1]


연결은 NDES 서버의 %SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ 폴더에 IIS에 의해서도 기록됩니다. 다음은 예입니다.

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="iosipados-devices"></a>iOS/iPadOS 디바이스

[디바이스 디버그 로그](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)를 검토합니다. 디바이스가 NDES에 연결될 때 기록되는 다음과 유사한 항목을 찾습니다.

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

주요 항목에는 다음 샘플 텍스트 문자열이 포함됩니다.

- operation=GetCACert
- Attempting to retrieve issued certificate
- Sending CSR via GET
- operation=PKIOperation

### <a name="windows-devices"></a>Windows 디바이스

NDES에 연결하는 Windows 디바이스에서 디바이스 Windows 이벤트 뷰어를 확인하고 성공적 연결의 표시를 찾을 수 있습니다. 연결은 디바이스 *DeviceManagement-Enterprise-Diagnostics-Provide* > **관리자** 로그에 이벤트 ID **36**으로 기록됩니다.

로그를 열려면

1. 디바이스에서 **eventvwr.msc**를 실행하여 Windows 이벤트 뷰어를 엽니다.

2. **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**을 확장합니다.

3. 다음 예와 비슷하고 다음과 같은 주요 줄이 있는 이벤트 **36**을 찾습니다. **SCEP: Certificate request generated successfully**:

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>일반 오류 문제 해결

다음 섹션은 모든 디바이스 플랫폼과 NDES의 일반적 연결 문제에 도움이 됩니다.

### <a name="status-code-500"></a>상태 코드 500

다음 예와 비슷하고 상태 코드가 500인 연결은 *인증 후 클라이언트 가장* 사용자 권한이 NDES 서버의 IIS_IURS 그룹에 할당되지 않았음을 나타냅니다. 상태 값 **500**은 끝부분에 나타납니다.

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**이 문제를 해결하려면**

1. NDES 서버에서 **secpol.msc**를 실행하여 로컬 보안 정책을 엽니다.

2. **로컬 정책**을 확장한 다음 **사용자 권한 할당**을 클릭합니다.

3. 오른쪽 창에서 **인증 후 클라이언트 가장**을 두 번 클릭합니다.

4. **사용자 또는 그룹 추가…** 를 클릭하고, **선택할 개체 이름을 입력하십시오** 상자에 **IIS_IURS**를 입력한 다음 **확인**을 클릭합니다.

5. **확인**을 클릭합니다.

6. 컴퓨터를 다시 시작한 다음 디바이스에서 다시 연결을 시도합니다.

### <a name="test-the-scep-server-url"></a>SCEP 서버 URL 테스트

다음 단계를 사용하여 SCEP 인증서 프로필에 지정된 URL을 테스트합니다.

1. Intune에서 SCEP 인증서 프로필을 편집하고 서버 URL을 복사합니다. URL은 *https://contoso.com/certsrv/mscep/msecp.dll* 과 비슷해야 합니다.

2. 웹 브라우저를 연 다음 해당 SCEP 서버 URL로 이동합니다. 결과는 **HTTP Error 403.0 – Forbidden**이어야 합니다. 이 결과는 URL이 올바로 작동하고 있음을 나타냅니다.

   이 오류 메시지가 표시되지 않으면 아래 나온 오류와 비슷한 링크를 선택하여 문제별 지침을 확인합니다.
   - [일반적인 네트워크 장치 등록 서비스 메시지가 표시됩니다.](#general-ndes-message)
   - ["HTTP 오류 503. 서비스를 사용할 수 없음"이 표시됩니다.](#http-error-503)
   - ["GatewayTimeout" 오류가 표시됩니다.](#gatewaytimeout)
   - ["HTTP 414 요청 URI가 너무 긺"이 표시됩니다.](#http-414-request-uri-too-long)
   - ["이 페이지를 표시할 수 없습니다"가 표시됩니다.](#this-page-cant-be-displayed)
   - ["500 - 내부 서버 오류"가 표시됩니다.](#internal-server-error)

#### <a name="general-ndes-message"></a>일반 NDES 메시지

SCEP 서버 URL로 이동하면 다음 네트워크 장치 등록 서비스 메시지가 표시됩니다.

![SCEP 서버 URL](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **원인**: 이 문제는 일반적으로 Microsoft Intune Connector 설치 문제입니다.

  mscep.dll은 올바르게 설치된 경우, 들어오는 요청을 가로채고 HTTP 403 오류를 표시하는 ISAPI 확장입니다.
  
  **해결 방법**: *SetupMsi.log* 파일을 검토하여 Microsoft Intune Connector가 성공적으로 설치되었는지 확인합니다. 다음 예에서 *설치가 완료되었습니다*와 *설치 성공 또는 오류 상태: 0*은 설치가 성공했음을 나타냅니다.

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  설치에 실패하면 Microsoft Intune Connector를 제거한 후 다시 설치합니다.

#### <a name="http-error-503"></a>HTTP 오류 503

SCEP 서버 URL로 이동하면 다음과 같은 오류가 표시됩니다.

![HTTP 오류 503. 서비스를 사용할 수 없음](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

이 문제는 일반적으로 IIS의 **SCEP** 애플리케이션 풀이 시작되지 않았기 때문에 발생합니다. NDES 서버에서 **IIS 관리자**를 열고 **애플리케이션 풀**로 이동합니다. **SCEP** 애플리케이션 풀을 찾아 시작되었는지 확인합니다.

SCEP 애플리케이션 풀이 시작되지 않은 경우 서버에서 애플리케이션 이벤트 로그를 확인합니다.

1. 디바이스에서 **eventvwr.msc**를 실행하여 **이벤트 뷰어**를 열고 **Windows 로그** > **애플리케이션**으로 이동합니다.

2. 다음 예와 비슷한 이벤트를 찾습니다. 이는 요청이 수신될 때 애플리케이션 풀이 충돌함을 뜻합니다.

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**애플리케이션 풀 충돌의 일반적 원인**:

- **원인 1**: NDES 서버의 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 중간 CA 인증서(자체 서명되지 않음)가 있습니다.

  **해결 방법**: 신뢰할 수 있는 루트 인증 기관 인증서 저장소에서 중간 인증서를 제거한 후 NDES 서버를 다시 시작합니다.
  
  신뢰할 수 있는 루트 인증 기관 인증서 저장소에 있는 모든 중간 인증서를 식별하려면 다음 PowerShell cmdlet을 실행합니다. `Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  **발급 대상** 값과 **발급자** 값이 동일한 인증서가 루트 인증서입니다. 그렇지 않으면 중간 인증서입니다.

  인증서를 제거하고 서버를 다시 시작한 후 PowerShell cmdlet을 다시 실행하여 중간 인증서가 없는지 확인합니다. 중간 인증서가 있다면 그룹 정책이 중간 인증서를 NDES 서버로 푸시하는지 확인합니다. 푸시한다면 그룹 정책에서 NDES 서버를 제외하고 중간 인증서를 다시 제거합니다.

- **원인 2**: Intune Certificate Connector에서 사용되는 인증서 CRL(인증서 해지 목록)의 URL이 차단되거나 연결할 수 없습니다.

  **해결 방법**: 추가 로깅을 사용하여 자세한 정보를 수집합니다.
  1. 이벤트 뷰어를 열고 **보기**를 클릭하여 **분석 및 디버그 로그 표시** 옵션이 선택되어 있는지 확인합니다.
  2. **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **CAPI2** > **작동**으로 이동하고 **작동**을 오른쪽 단추로 클릭한 다음 **로그 사용**을 클릭합니다.
  3. CAPI2 로깅을 사용하도록 설정한 후 문제를 재현하고 이벤트 로그를 검사하여 문제를 해결합니다.

- **원인 3**: **CertificateRegistrationSvc**에 대한 IIS 권한이 **Windows 인증**을 사용하도록 설정되어 있습니다.

  **해결 방법**: **익명 인증**을 사용하도록 설정하고 **Windows 인증**을 사용하지 않도록 설정한 다음 NDES 서버를 다시 시작합니다.

  ![IIS 권한](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

SCEP 서버 URL로 이동하면 다음과 같은 오류가 표시됩니다.

![GatewayTimeout 오류](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **원인**: **Microsoft AAD Application Proxy Connector** 서비스가 시작되지 않았습니다.

  **해결 방법**:  **services.msc**를 실행한 다음 **Microsoft AAD Application Proxy Connector** 서비스가 실행 중이고 **시작 유형**이 **자동**으로 설정되어 있는지 확인합니다.

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 요청 URI가 너무 긺

SCEP 서버 URL로 이동하면 다음과 같은 오류가 표시됩니다. `HTTP 414 Request-URI Too Long`

- **원인**: NDES 서비스가 수신하는 긴 URL(쿼리)을 지원하도록 IIS 요청 필터링이 구성되지 않았습니다. 이 지원은 SCEP용 인프라에 사용할 [NDES 서비스를 구성](certificates-scep-configure.md#configure-the-ndes-service)할 때 구성됩니다.

- **해결 방법**: 긴 URL에 대한 지원을 구성합니다.

  1. NDES 서버에서 **기본 웹 사이트** > **요청 필터링** > **기능 설정 편집**을 선택하여 **요청 필터링 설정 편집** 페이지를 엽니다.

  2. 다음 설정을 구성합니다.
     - **최대 URL 길이(바이트)** = 65534
     - **최대 쿼리 문자열(바이트)** = 65534

  3. **확인**을 선택하여 이 구성을 저장하고 IIS 관리자를 닫습니다.

  4. 다음 레지스트리 키를 찾아 표시된 값이 있는지 확인하여 이 구성의 유효성을 검사합니다.

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     다음 값은 DWORD 항목으로 설정됩니다.
     - 이름: **MaxFieldLength**, 10진수 값 **65534**
     - 이름: **MaxRequestBytes**, 10진수 값 **65534**

  5. NDES 서버를 다시 시작합니다.

#### <a name="this-page-cant-be-displayed"></a>이 페이지를 표시할 수 없습니다

Azure AD 애플리케이션 프록시가 구성되었습니다. SCEP 서버 URL로 이동하면 다음과 같은 오류가 표시됩니다.

`This page can't be displayed`

- **원인**: 이 문제는 애플리케이션 프록시 구성에서 SCEP 외부 URL이 잘못된 경우 발생합니다. 이 URL의 예는 https://contoso.com/certsrv/mscep/mscep.dll 입니다.

  **해결 방법**: 애플리케이션 프록시 구성에서 SCEP 외부 URL에 *yourtenant.msappproxy.net*의 기본 도메인을 사용합니다.

#### <a name="internal-server-error"></a>500 - 내부 서버 오류

SCEP 서버 URL로 이동하면 다음과 같은 오류가 표시됩니다.

![500 - 내부 서버 오류](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **원인 1**: NDES 서비스 계정이 잠겨 있거나 암호가 만료되었습니다.

  **해결 방법**: 계정 잠금을 해제하거나 암호를 다시 설정합니다.

- **원인 2**: MSCEP RA 인증서가 만료되었습니다.

  **해결 방법**: MSCEP RA 인증서가 만료된 경우 NDES 역할을 다시 설치하거나 새 CEP 암호화 및 Exchange 등록 에이전트(오프라인 요청) 인증서를 요청합니다.

  새 인증서를 요청하려면 다음 단계를 수행합니다.

  1. CA(인증 기관) 또는 발급 CA에서 인증서 템플릿 MMC를 엽니다. 로그인한 사용자와 NDES 서버에 CEP 암호화 및 Exchange 등록 에이전트(오프라인 요청) 인증서 템플릿에 대한 **읽기** 및 **등록** 권한이 있어야 합니다.

  2. NDES 서버에서 만료된 인증서를 확인하고 인증서에서 **주체** 정보를 복사합니다.

  3. **컴퓨터 계정**에 대한 인증서 MMC를 엽니다.

  4. **개인**을 확장하고 **인증서**를 마우스 오른쪽 단추로 클릭한 다음 **모든 작업** > **새 인증서 요청**을 선택합니다.

  5. **인증서 요청** 페이지에서 **CEP 암호화**를 선택한 다음 **이 인증서를 등록하려면 추가 정보가 필요합니다. 설정을 구성하려면 여기를 클릭 하십시오**를 클릭합니다.

     ![CEP 암호화 선택](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. **인증서 속성**에서 **주체** 탭을 클릭하고 2단계에서 수집한 정보로 **주체 이름**을 입력하고 **추가**를 클릭한 다음 **확인**을 클릭합니다.

  7. 인증서 등록을 완료합니다.

  8. **내 사용자 계정**에 대한 인증서 MMC를 엽니다.

     Exchange 등록 에이전트(오프라인 요청) 인증서는 사용자 컨텍스트에서 등록해야 합니다. 이 인증서 템플릿의 **주체 유형**이 **사용자**로 설정되어 있기 때문입니다.

  9. **개인**을 확장하고 **인증서**를 마우스 오른쪽 단추로 클릭한 다음 **모든 작업** > **새 인증서 요청**을 선택합니다.

  10. **인증서 요청** 페이지에서 **Exchange 등록 에이전트(오프라인 요청)** 를 선택한 다음 **이 인증서를 등록하려면 추가 정보가 필요합니다. 설정을 구성하려면 여기를 클릭 하십시오**를 클릭합니다.

      ![Exchange 등록 에이전트 선택](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. **인증서 속성**에서 **주체** 탭을 클릭하고 2단계에서 수집한 정보로 **주체 이름**을 입력하고 **추가**를 클릭합니다.

      ![인증서 속성](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      **프라이빗 키** 탭을 선택하고 **프라이빗 키를 내보낼 수 있게 설정**을 선택한 다음 **확인**을 클릭합니다.

      ![프라이빗 키](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. 인증서 등록을 완료합니다.

  13. 현재 사용자 인증서 저장소에서 Exchange 등록 에이전트(오프라인 요청) 인증서를 내보냅니다. 인증서 내보내기 마법사 페이지에서 **예, 프라이빗 키를 내보냅니다**를 클릭합니다.

  14. 로컬 컴퓨터 인증서 저장소로 인증서를 가져옵니다.

  15. 인증서 MMC에서 각 새 인증서에 대해 다음 작업을 수행합니다.

      인증서를 마우스 오른쪽 단추로 클릭하고 **모든 작업** > **프라이빗 키 관리**를 클릭하고, NDES 서비스 계정에 **읽기** 권한을 추가합니다.

  16. **iisreset** 명령을 실행하여 IIS를 다시 시작합니다.

## <a name="next-steps"></a>다음 단계

디바이스가 인증서 요청을 위해 NDES 서버에 성공적으로 연결하는 경우, 다음 단계는 [Intune Certificate Connector 정책 모듈](troubleshoot-scep-certificate-ndes-policy-module.md)을 검토하는 것입니다.
