---
title: Microsoft Intune에서 SCEP와 함께 타사 CA 사용 - Azure | Microsoft Docs
description: Microsoft Intune에서 공급업체 또는 타사 CA(인증 기관)를 추가하여 SCEP 프로토콜을 통해 모바일 디바이스에 인증서를 발급할 수 있습니다. 이 개요에서 Azure AD(Active Directory) 애플리케이션은 Microsoft Intune에 인증서 유효성 검사 권한을 부여합니다. 그런 다음, SCEP 서버 설정에서 AAD 애플리케이션의 애플리케이션 ID, 인증 키 및 테넌트 ID를 사용하여 인증서를 발급합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d042a160d016343c6e8374dff8f74560b9806014
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508487"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>SCEP를 사용하여 Intune에 파트너 인증 기관 추가

Microsoft Intune에서 타사 CA(인증 기관)를 추가할 수 있습니다. 이러한 CA는 SCEP(단순 인증서 등록 프로토콜)를 사용하여 모바일 디바이스에 인증서를 제공할 수 있습니다. 이 기능은 Windows, iOS, Android 및 macOS 디바이스에서 새 인증서를 발급하고 갱신할 수 있습니다.

이 기능의 사용법은 오픈 소스 API와 Intune 관리자 작업이라는 두 가지 부분으로 나뉘어 있습니다.

**1부 - 오픈 소스 API 사용**  
Microsoft는 Intune과 통합되어 인증서의 유효성을 검사하고, 성공 또는 실패 알림을 전송하며, SSL(특히 SSL 소켓 팩터리)을 사용하여 Intune과 통신하는 API를 만들었습니다.

API는 [Intune SCEP API 공개 GitHub 리포지토리](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)에서 다운로드하여 솔루션에서 사용할 수 있습니다. 타사 SCEP 서버에서 이 API를 사용하여 인증서를 디바이스에 전송하기 전에 Intune에 사용자 지정 인증 질문 유효성 검사를 실행합니다.

[Intune SCEP 관리 솔루션과 통합](scep-libraries-apis.md)에서는 API 사용, 메서드 및 빌드한 솔루션 테스트에 대한 자세한 정보를 제공합니다.

**2부 - 애플리케이션 및 프로필 만들기**  
Azure AD(Active Directory) 애플리케이션을 사용하면 Intune에 권한을 위임하여 장치에서 발생하는 SCEP 요청을 처리할 수 있습니다. Azure AD 애플리케이션은 개발자가 만든 API 솔루션 내에서 사용되는 애플리케이션 ID 및 인증 키 값을 포함합니다. 그런 다음, 관리자는 Intune을 사용하여 SCEP 인증서 프로필을 만들고 배포할 수 있습니다. 디바이스의 배포 상태에 대한 보고서를 볼 수도 있습니다.

이 문서에서는 관리자 관점에서 Azure AD 애플리케이션 생성 등을 살펴보며 이 기능에 대한 개요를 제공합니다.

## <a name="overview"></a>개요

다음 단계는 Intune에서 SCEP 인증서를 발급하는 방법에 대한 개요를 제공합니다.

1. Intune에서 관리자는 SCEP 인증서 프로필을 만든 다음, 프로필 대상을 사용자 또는 디바이스로 지정합니다.
2. 디바이스가 Intune에 체크 인합니다.
3. Intune은 고유한 SCEP 인증 질문을 만듭니다. 또한 올바른 주체 및 SAN과 같은 추가 무결성 검사 정보를 추가합니다.
4. Intune은 인증 질문 및 무결성 검사 정보를 암호화하고 서명한 다음, SCEP 요청을 통해 디바이스에 이 정보를 보냅니다.
5. 디바이스는 Intune에서 푸시되는 SCEP 인증서 프로필을 기반으로 디바이스에 CSR(인증서 서명 요청) 및 공용/개인 키 쌍을 생성합니다.
6. CSR 및 암호화/서명된 인증 질문이 타사 SCEP 서버 엔드포인트로 전송됩니다.
7. SCEP 서버는 CSR과 인증 질문을 Intune에 보냅니다. 그런 다음, Intune은 서명의 유효성을 검사하고 페이로드의 암호를 해독하며 CSR을 무결성 검사 정보와 비교합니다.
8. Intune은 SCEP 서버에 응답을 보내고 인증 질문 유효성 검사가 성공했는지 여부를 명시합니다.  
9. 인증 질문이 성공적으로 확인되면 SCEP 서버는 디바이스에 인증서를 발급합니다.

다음 다이어그램에서는 Intune과 타사 SCEP 통합의 자세한 흐름을 보여 줍니다.

![타사 인증 기관 SCEP를 Microsoft Intune과 통합하는 방법](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>타사 CA 통합 설정

### <a name="validate-third-party-certification-authority"></a>타사 인증 기관 유효성 검사

타사 인증 기관을 Intune과 통합하기 전에 사용 중인 CA가 Intune을 지원하는지 확인합니다. (이 문서에서) [타사 CA 파트너](#third-party-certification-authority-partners)는 목록을 포함합니다. 인증 기관의 지침에서 자세한 내용을 확인할 수도 있습니다. CA는 해당 구현과 관련된 설치 지침을 포함할 수 있습니다.

### <a name="authorize-communication-between-ca-and-intune"></a>CA와 Intune 간의 통신 승인

Intune을 사용하여 타사 SCEP 서버가 사용자 지정 인증 질문 유효성 검사를 실행할 수 있도록 Azure AD에 앱을 만듭니다. 이 앱은 Intune에 위임된 권한을 부여하여 SCEP 요청의 유효성을 검사합니다.

Azure AD 앱을 등록하는 데 필요한 권한이 있는지 확인합니다. [필요한 권한](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions)에 단계가 나열되어 있습니다.

**1단계: Azure AD 애플리케이션 만들기**

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **Azure Active Directory** > **앱 등록** > **새 애플리케이션 등록**을 선택합니다.
3. 이름과 로그온 URL을 입력합니다. 애플리케이션 유형에 **웹앱/API**를 선택합니다.
4. **만들기**를 선택합니다.

[Azure Active Directory와 애플리케이션 통합](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)에는 URL 및 이름에 대한 팁을 포함하여 앱을 만드는 방법에 대한 몇 가지 지침이 포함되어 있습니다.

**2단계: 사용 권한 부여**

애플리케이션을 만든 후 Microsoft Intune API에 필요한 권한을 부여합니다.

1. Azure AD 앱에서 **설정** > **필수 권한**을 엽니다.  
2. **추가** > **API 선택**을 선택 > **Microsoft Intune API** > **선택**을 선택합니다.
3. **권한 선택**에서 **SCEP 인증 질문 유효성 검사** > **선택**을 선택합니다.
4. **완료**를 선택하여 변경 내용을 저장합니다.

**3단계: 애플리케이션 ID 및 인증 키 가져오기**

그런 다음, Azure AD 애플리케이션의 ID와 키 값을 가져옵니다. 다음 값이 필요합니다.

- 애플리케이션 ID
- 인증 키
- 테넌트 ID

**애플리케이션 ID 및 인증 키를 가져오려면**:

1. Azure AD에서 새 애플리케이션을 선택합니다(**앱 등록**).
2. **애플리케이션 ID**를 복사하여 애플리케이션 코드에 저장합니다.
3. 그런 다음, 인증 키를 생성합니다. Azure AD 앱에서 **설정** > **키**를 엽니다.
4. **암호**에서 설명을 입력하고 키의 기간을 선택합니다. 변경 내용을 **저장**합니다. 표시된 값을 복사하고 저장합니다.

    > [!IMPORTANT]
    > 이 키는 다시 표시되지 않으므로 즉시 복사하고 저장합니다. 이 키 값은 타사 CA 구현에 필요합니다. 애플리케이션 ID, 인증 키 및 테넌트 ID를 구성하는 방법에 대한 해당 지침을 검토합니다.

**테넌트 ID**는 계정의 @ 기호 다음에 오는 도메인 텍스트입니다. 예를 들어 계정이 `admin@name.onmicrosoft.com`이면 테넌트 ID는 **name.onmicrosoft.com**입니다.

[애플리케이션 ID 및 인증 키 가져오기](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key)에는 이러한 값을 가져오는 단계가 나열되어 있고 Azure AD 앱에 대한 자세한 정보가 제공됩니다.

### <a name="configure-and-deploy-a-scep-certificate-profile"></a>SCEP 인증서 프로필 구성 및 배포
관리자는 사용자 또는 디바이스를 대상으로 SCEP 인증서 프로필을 만듭니다. 그런 다음, 프로필을 할당합니다.

- [SCEP 인증서 프로필 만들기](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [인증서 프로필 할당](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>인증서 제거

디바이스의 등록을 취소하거나 초기화할 때 인증서가 제거됩니다. 인증서는 해지되지 않습니다.

## <a name="third-party-certification-authority-partners"></a>타사 인증 기관 파트너
다음 타사 인증 기관은 Intune을 지원합니다.

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)
- [EJBCA GitHub 오픈 소스 버전](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)

Intune과 제품을 통합하는 데 관심이 있는 타사 CA인 경우 API 지침을 검토합니다.

- [Intune SCEP API GitHub 리포지토리](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [타사 CA에 대한 Intune SCEP API 지침](scep-libraries-apis.md)

## <a name="see-also"></a>참고 항목

- [인증서 프로필 구성](certificates-scep-configure.md)
- [Intune SCEP API GitHub 리포지토리](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [타사 CA에 대한 Intune SCEP API 지침](scep-libraries-apis.md)
