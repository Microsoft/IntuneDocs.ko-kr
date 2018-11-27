---
title: API를 사용하여 타사 인증 기관 등록 - Microsoft Intune - Azure | Microsoft Docs
description: 타사 CA(인증 기관)용 SCEP GitHub 솔루션을 추가하거나 통합하여 Microsoft Intune의 장치에 SCEP 인증서를 발급합니다. 이 솔루션에는 유효성을 검사하고, 성공 및 실패 알림을 Intune에 보내고, Intune과 통신할 때 SSL 소켓 팩터리를 사용하는 Java 및 C# API가 포함됩니다. SCEP CA 구성을 테스트하는 단계에 대한 개요를 볼 수도 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 054342994a75965b3e1bcb13884af07131ab0122
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181924"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>API를 사용하여 SCEP에 대한 타사 CA를 Intune에 추가

Microsoft Intune에서 타사 CA(인증 기관)를 추가하고 SCEP(단순 인증서 등록 프로토콜)를 사용하여 이러한 CA가 인증서를 발급하고 인증서의 유효성을 검사하도록 할 수 있습니다. [타사 인증 기관 추가](certificate-authority-add-scep-overview.md)에서는 이 기능에 대한 개요를 제공하고 Intune의 관리자 작업을 설명합니다.

Microsoft가 GitHub.com에 게시하는 오픈 소스 라이브러리를 사용하는 일부 개발자 작업도 있습니다. 라이브러리에는 다음과 같은 API가 포함되어 있습니다.

- Intune에서 동적으로 생성된 SCEP 암호의 유효성 검사
- SCEP 요청을 제출하는 장치에 생성된 인증서를 Intune에 알림

이 API를 사용하면 타사 SCEP 서버가 MDM 장치용 Intune SCEP 관리 솔루션과 통합됩니다. 라이브러리는 해당 사용자의 인증, 서비스 위치 및 ODATA Intune Service API와 같은 측면을 추상화합니다.

## <a name="scep-management-solution"></a>SCEP 관리 솔루션

![타사 인증 기관 SCEP를 Microsoft Intune과 통합하는 방법](./media/scep-certificate-vendor-integration.png)

관리자는 Intune을 사용하여 SCEP 프로필을 만든 다음, 이 프로필을 MDM 장치에 할당합니다. SCEP 프로필에는 다음과 같은 매개 변수가 포함됩니다.

- SCEP 서버의 URL
- 인증 기관의 신뢰할 수 있는 루트 인증서
- 인증서 특성 등

Intune으로 체크 인하는 장치는 SCEP 프로필을 할당받고, 이러한 매개 변수로 구성됩니다. 동적으로 생성되는 SCEP 챌린지 암호는 Intune에서 만들어진 다음, 장치에 할당됩니다.

이 챌린지에 포함되는 항목은 다음과 같습니다.

- 동적으로 생성된 챌린지 암호
- 장치에서 SCEP 서버에 발급하는 CSR(인증서 서명 요청)에 필요한 매개 변수에 대한 세부 정보
- 챌린지 만료 시간

Intune은 이 정보를 암호화하고, 암호화된 Blob에 서명한 다음, 이러한 세부 정보를 SCEP 챌린지 암호로 패키지합니다.

그러면 SCEP 서버에 연결하여 인증서를 요청한 장치에서 이 SCEP 챌린지 암호를 제공합니다. SCEP 서버는 유효성 검사를 위해 CSR 및 암호화된 SCEP 챌린지 암호를 Intune으로 보냅니다.  이 챌린지 암호 및 CSR은 인증서를 장치에 발급하는 SCEP 서버에 대한 유효성 검사를 통과해야 합니다. SCEP 챌린지의 유효성을 검사하는 경우 수행되는 검사는 다음과 같습니다.


- 암호화된 BLOB의 서명 유효성 검사
- 인증 질문이 만료되지 않았는지 검사
- 프로필이 여전히 장치를 대상으로 하는지 검사
- CSR에 있는 장치에서 요청한 인증서 속성이 예상 값과 일치하는지 검사

SCEP 관리 솔루션에는 보고 기능도 포함되어 있습니다. 관리자는 SCEP 프로필의 배포 상태 및 장치에 발급된 인증서에 대한 정보를 가져올 수 있습니다.

## <a name="integrate-with-intune"></a>Intune과 통합

라이브러리를 Intune SCEP와 통합하는 코드는 [Microsoft/Intune-Resource-Access GitHub 리포지토리](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)에서 다운로드할 수 있습니다.

제품에 라이브러리를 통합하는 작업에는 다음 단계가 포함됩니다. 이러한 단계를 수행하려면 GitHub 리포지토리로 작업하고, Visual Studio에서 솔루션 및 프로젝트를 만드는 방법에 대한 지식이 필요합니다.

1. 리포지토리에서 알림을 수신하도록 등록
2. 리포지토리 복제 또는 다운로드
3. `\src\CsrValidation` 폴더(https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) 아래에서 필요한 라이브러리 구현으로 이동합니다.
4. README 파일의 지침에 따라 라이브러리 빌드
5. SCEP 서버를 빌드하는 프로젝트에 라이브러리 포함
6. SCEP 서버에서 다음 작업을 완료합니다.

    - (이 문서에서) 관리자가 라이브러리에서 인증에 사용하는 [Azure 응용 프로그램 식별자, Azure 응용 프로그램 키 및 테넌트 ID](#onboard-scep-server-in-azure)를 구성하도록 허용합니다. 관리자는 Azure 응용 프로그램 키를 업데이트할 수 있어야 합니다.
    - Intune에서 생성된 SCEP 암호를 포함하는 SCEP 요청을 식별합니다.
    - **요청 유효성 검사 API** 라이브러리를 사용하여 Intune에서 생성된 SCEP 암호의 유효성을 검사합니다.
    - 라이브러리 알림 API를 사용하여 Intune에서 생성된 SCEP 암호가 있는 SCEP 요청에 대해 발급된 인증서를 Intune에 알립니다. 또한 이러한 SCEP 요청을 처리할 때 발생할 수 있는 오류에 대해 Intune에 알립니다.
    - 관리자가 문제를 해결하는 데 도움이 되는 충분한 정보가 서버에 기록되는지 확인합니다.

7. (이 문서에서) [통합 테스트](#integration-testing)를 완료하고 모든 문제를 해결합니다.
8. 고객에게 다음을 설명하는 서면 지침을 제공합니다.

    - Azure Portal에서 SCEP 서버를 등록하는 방법
    - 라이브러리를 구성하는 데 필요한 Azure 응용 프로그램 식별자 및 Azure 응용 프로그램 키를 가져오는 방법

### <a name="onboard-scep-server-in-azure"></a>Azure에서 SCEP 서버 등록

Intune에 인증하려면 SCEP 서버에서 Azure 응용 프로그램 ID, Azure 응용 프로그램 키 및 테넌트 ID를 알아야 합니다. SCEP 서버에 Intune API 액세스 권한도 있어야 합니다.

이 데이터를 가져오려면 SCEP 서버 관리자가 Azure Portal에 로그인하고, 응용 프로그램을 등록하고, 응용 프로그램에 **Microsoft Intune API\SCEP challenge validation** 권한을 부여하고, 응용 프로그램 키를 만든 다음, 응용 프로그램 ID, 해당 키 및 테넌트 ID를 다운로드합니다.

응용 프로그램을 등록하고 ID 및 키를 가져오는 방법에 대한 지침은 [포털을 사용하여 리소스에 액세스할 때 사용할 AAD 응용 프로그램 및 서비스 주체 만들기](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)를 참조하세요.

### <a name="java-library-api"></a>Java 라이브러리 API

Java 라이브러리는 빌드 시 종속성을 가져오는 Maven 프로젝트로 구현됩니다. API는 `IntuneScepServiceClient` 클래스에 의해 `com.microsoft.intune.scepvalidation` 네임스페이스 아래에 구현됩니다.

#### <a name="intunescepserviceclient-class"></a>IntuneScepServiceClient 클래스

`IntuneScepServiceClient` 클래스에는 SCEP 서비스에서 SCEP 암호의 유효성을 검사하고, 생성된 인증서를 Intune에 알리고, 오류를 나열하는 데 사용되는 메서드가 포함됩니다.

##### <a name="intunescepserviceclient-constructor"></a>IntuneScepServiceClient 생성자

서명:

```java
IntuneScepServiceClient(
    Properties configProperties)
```

설명:

`IntuneScepServiceClient` 개체를 인스턴스화하고 구성합니다.

매개 변수:

    - configProperties  클라이언트 구성 정보를 포함하는 속성 개체

구성에는 다음 속성이 포함되어야 합니다.

    - AAD_APP_ID="등록 프로세스 중에 얻은 Azure 응용 프로그램 ID"
    - AAD_APP_KEY="등록 프로세스 중에 얻은 Azure 응용 프로그램 키"
    - TENANT="등록 프로세스 중에 얻은 테넌트 ID"
    - PROVIDER_NAME_AND_VERSION="제품 및 해당 버전을 식별하는 데 사용되는 정보"
    
솔루션에 인증을 사용하거나 사용하지 않는 프록시가 필요한 경우 다음 속성을 추가할 수 있습니다.

    - PROXY_HOST="프록시가 호스팅되는 호스트입니다."
    - PROXY_PORT="프록시에서 수신 대기 중인 포트입니다."
    - PROXY_USER="프록시에서 기본 인증을 사용하는 경우 사용할 사용자 이름입니다."
    - PROXY_PASS="프록시에서 기본 인증을 사용하는 경우 사용할 암호입니다."

Throws:

    - IllegalArgumentException  생성자가 적절한 속성 개체 없이 실행되는 경우 throw됩니다.

> [!IMPORTANT]
> 이 클래스의 인스턴스를 인스턴스화하고 여러 SCEP 요청을 처리하는 데 사용하는 것이 가장 좋습니다. 이렇게 하면 인증 토큰 및 서비스 위치 정보가 캐시되므로 오버헤드가 줄어듭니다.

**보안 메모**  
SCEP 서버 구현자는 구성 속성에 입력된 데이터가 변조 및 공개되지 않고 계속 저장되도록 보호해야 합니다. 적절한 ACL 및 암호화를 사용하여 정보를 보호하는 것이 좋습니다.

##### <a name="validaterequest-method"></a>ValidateRequest 메서드

서명:

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

설명:

SCEP 인증서 요청의 유효성을 검사합니다.

매개 변수:

    - transactionId     SCEP 트랜잭션 ID
    - certificateRequest   DER로 인코딩된 PKCS #10 인증서 요청 문자열로 인코딩된 Base64

Throws:

    - IllegalArgumentException   잘못된 매개 변수를 사용하여 호출하는 경우 throw됩니다.
    - IntuneScepServiceException   인증서 요청이 올바르지 않는 것이 발견되었을 경우 throw됩니다.
    - Exception            예상치 못한 오류가 발생한 경우 throw됩니다.

> [!IMPORTANT]
> 이 메서드에 의해 throw된 예외는 서버에서 기록해야 합니다. `IntuneScepServiceException` 속성에는 인증서 요청 유효성 검사가 실패한 이유에 대한 자세한 정보가 있습니다.

**보안 메모**  

  - 이 메서드에서 예외를 throw하는 경우 SCEP 서버는 클라이언트에 인증서를 발급해서는 **안 됩니다**.
  - SCEP 인증서 요청 유효성 검사 실패는 Intune 인프라에 문제가 있음을 나타낼 수 있습니다. 또는 공격자가 인증서를 얻으려고 한다는 것을 나타낼 수 있습니다.

##### <a name="sendsuccessnotification-method"></a>SendSuccessNotification 메서드

서명:

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

설명:

SCEP 요청을 처리하는 도중에 인증서가 생성되었음을 Intune에 알립니다.

매개 변수:

    - transactionId      SCEP 트랜잭션 ID
    - certificateRequest    DER로 인코딩된 PKCS #10 인증서 요청 문자열로 인코딩된 Base64
    - certThumprint      프로비전된 인증서의 지문
    - certSerialNumber    프로비전된 인증서의 일련 번호
    - certExpirationDate    프로비전된 인증서의 만료 날짜. 날짜 시간 문자열은 웹 UTC 시간(YYYY-MM-DDThh:mm:ss.sssTZD) ISO 8601 형식이어야 합니다.
    - certIssuingAuthority   인증서를 발급한 기관의 이름

Throws:

    - IllegalArgumentException   잘못된 매개 변수를 사용하여 호출하는 경우 throw됩니다.
    - IntuneScepServiceException   인증서 요청이 올바르지 않는 것이 발견되었을 경우 throw됩니다.
    - Exception            예상치 못한 오류가 발생한 경우 throw됩니다.

> [!IMPORTANT]
> 이 메서드에 의해 throw된 예외는 서버에서 기록해야 합니다. `IntuneScepServiceException` 속성에는 인증서 요청 유효성 검사가 실패한 이유에 대한 자세한 정보가 있습니다.

**보안 메모**

  - 이 메서드에서 예외를 throw하는 경우 SCEP 서버는 클라이언트에 인증서를 발급해서는 **안 됩니다**.
  - SCEP 인증서 요청 유효성 검사 실패는 Intune 인프라에 문제가 있음을 나타낼 수 있습니다. 또는 공격자가 인증서를 얻으려고 한다는 것을 나타낼 수 있습니다.

##### <a name="sendfailurenotification-method"></a>SendFailureNotification 메서드

서명:

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

설명:

SCEP 요청을 처리하는 동안 오류가 발생했음을 Intune에 알립니다. 이 클래스의 메서드에 의해 throw된 예외에 대해서는 이 메서드를 호출하면 안 됩니다.

매개 변수:

    - transactionId     SCEP 트랜잭션 ID
    - certificateRequest   DER로 인코딩된 PKCS #10 인증서 요청 문자열로 인코딩된 Base64
    - hResult        발생한 오류를 가장 잘 나타내는 Win32 오류 코드. [Win32 오류 코드](https://msdn.microsoft.com/library/cc231199.aspx) 참조
    - errorDescription    발생한 오류에 대한 설명

Throws:

    - IllegalArgumentException   잘못된 매개 변수를 사용하여 호출하는 경우 throw됩니다.
    - IntuneScepServiceException   인증서 요청이 올바르지 않는 것이 발견되었을 경우 throw됩니다.
    - Exception            예상치 못한 오류가 발생한 경우 throw됩니다.

> [!IMPORTANT]
> 이 메서드에 의해 throw된 예외는 서버에서 기록해야 합니다. `IntuneScepServiceException` 속성에는 인증서 요청 유효성 검사가 실패한 이유에 대한 자세한 정보가 있습니다.

**보안 메모**

  - 이 메서드에서 예외를 throw하는 경우 SCEP 서버는 클라이언트에 인증서를 발급해서는 **안 됩니다**.
  - SCEP 인증서 요청 유효성 검사 실패는 Intune 인프라에 문제가 있음을 나타낼 수 있습니다. 또는 공격자가 인증서를 얻으려고 한다는 것을 나타낼 수 있습니다.

##### <a name="setsslsocketfactory-method"></a>SetSslSocketFactory 메서드

서명:

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

설명:

이 메서드를 사용하여 Intune과 통신할 때 지정된 SSL 소켓 팩터리(기본값 대신)를 사용해야 함을 클라이언트에 알립니다.

매개 변수:

    - factory   클라이언트가 HTTPS 요청에 사용해야 하는 SSL 소켓 팩터리

Throws:

    - IllegalArgumentException    잘못된 매개 변수를 사용하여 호출하는 경우 throw됩니다.

> [!NOTE]
> 이 클래스의 다른 메서드를 실행하기 전에 필요한 경우 SSL 소켓 팩터리를 설정해야 합니다.

## <a name="integration-testing"></a>통합 테스트

솔루션이 Intune과 적절하게 통합되었는지 확인하고 테스트해야 합니다. 다음은 이 작업의 단계를 간략히 정리한 것입니다.

1. [Intune 평가판 계정](account-sign-up.md)을 설정합니다.
2. (이 문서에서) [Azure Portal의 SCEP 서버](#onboard-scep-server-in-azure)를 등록합니다.
3. SCEP 서버를 등록할 때 생성된 ID와 키를 사용하여 [SCEP 서버를 구성](certificates-scep-configure.md)합니다.
4. [시나리오 테스트 매트릭스](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv)에서 시나리오를 테스트하려면 [장치를 등록](device-enrollment.md)합니다.
5. 테스트 인증 기관에 대한 [신뢰할 수 있는 루트 인증서 프로필을 생성](certificates-scep-configure.md)합니다.
6. SCEP 프로필을 생성하여 [시나리오 테스트 매트릭스](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv)에 나열된 시나리오를 테스트합니다.
7. 해당 장치를 등록한 사용자에게 [프로필을 할당](device-profile-assign.md)합니다.
8. 장치가 Intune과 동기화될 때까지 기다립니다. 또는 수동으로 [장치를 동기화](device-sync.md)합니다.
9. 신뢰할 수 있는 루트 인증서 및 SCEP [프로필이 장치에 배포되었는지](device-profile-monitor.md) 확인합니다.
10. 모든 장치에 신뢰할 수 있는 루트 인증서가 설치되어 있는지 확인합니다.
11. 할당된 프로필의 SCEP 인증서가 모든 장치에 설치되어 있는지 확인합니다.
12. 설치된 인증서의 속성이 SCEP 프로필에 설정된 속성과 일치하는지 확인합니다.
13. 발급된 인증서가 Intune 콘솔에 올바르게 나열되어 있는지 확인합니다.

## <a name="see-also"></a>참고 항목

- [타사 CA 추가 개요](certificate-authority-add-scep-overview.md)
- [Intune 설정](setup-steps.md)
- [장치 등록](device-enrollment.md)
- [SCEP 인증서 프로필 구성](certificates-scep-configure.md#create-a-scep-certificate-profile)(이 시나리오에서는 Microsoft NDES Server\Connector 설치가 사용되지 않음)
