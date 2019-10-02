---
title: Microsoft Intune에서 SCEP 인증서 프로필 사용 - Azure | Microsoft Docs
description: Microsoft Intune을 사용하여 SCEP(단순 인증서 등록 프로토콜) 인증서 프로필을 만들고 할당합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
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
ms.openlocfilehash: 8e6b9f7d6aeda219af0f0cf3d0f5c34a3f03d258
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722893"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>Intune에서 SCEP 인증서 프로필 만들기 및 할당

SCEP(단순 인증서 등록 프로토콜) 인증서를 지원하도록 [인프라를 구성](certificates-scep-configure.md)한 후에는 Intune에서 SCEP 인증서 프로필을 만들고 사용자 및 디바이스에 할당할 수 있습니다.

> [!IMPORTANT]  
> SCEP 인증서 프로필을 만들기 전에 SCEP 인증서 프로필을 사용하는 디바이스가 신뢰할 수 있는 루트 CA(인증 기관)를 신뢰해야 합니다. Intune에서 *신뢰할 수 있는 인증서 프로필*을 사용하여 사용자 및 디바이스에 신뢰할 수 있는 루트 CA 인증서를 프로비저닝합니다. 신뢰할 수 있는 인증서 프로필에 대한 내용은 *Intune에서 인증을 위해 인증서 사용*의 [신뢰할 수 있는 루트 CA 인증서 내보내기](certificates-configure.md#export-the-trusted-root-ca-certificate) 및 [신뢰할 수 있는 인증서 프로필 만들기](certificates-configure.md#create-trusted-certificate-profiles)를 참조하세요.


## <a name="create-a-scep-certificate-profile"></a>SCEP 인증서 프로필 만들기

1. [Intune 포털](https://aka.ms/intuneportal)에 로그인합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. SCEP 인증서 프로필에 대한 **이름** 및 **설명**을 입력합니다.
4. **플랫폼** 드롭다운 목록에서 이 SCEP 인증서에 대한 [지원되는 디바이스 플랫폼](certificates-configure.md#supported-platforms-and-certificate-profiles)을 선택합니다. 
5. **프로필** 유형 드롭다운 목록에서 **SCEP 인증서**를 선택합니다.  
   
   **Android Enterprise** 플랫폼의 경우 *프로필 유형*이 두 가지 범주인 *디바이스 소유자만* 및 *회사 프로필만*으로 구분됩니다. 관리하는 디바이스에 대해 올바른 SCEP 인증서 프로필을 선택해야 합니다.  

   *디바이스 소유자만* 프로필에 대한 SCEP 인증서 프로필에는 다음과 같은 제한 사항이 있습니다.  

   1. 다음 변수가 지원됩니다.  

      - CN={{OnPrem_Distinguished_Name}}  
      - CN={{onPremisesSamAccountName}}  

   2. 모니터링에서는 디바이스 소유자 SCEP 인증서 프로필에 대해 인증서 보고를 사용할 수 없습니다.
   
   3. 디바이스 소유자용 SCEP 인증서 프로필로 프로비저닝되는 인증서의 해지는 Intune을 통해 지원되지 않지만, 외부 프로세스를 통하거나 인증 기관에서 직접 관리할 수 있습니다.

6. **설정**을 선택하고 다음 구성을 완료합니다.

   - **인증서 유형**:   
     *(적용 대상:  Android, Android Enterprise, iOS, macOS, Windows 8.1 이상 및 Windows 10 이상)*  

      인증서 프로필을 사용하는 방법에 따라 유형을 선택합니다.
      - **사용자**: *사용자* 인증서는 인증서의 주체와 SAN에 사용자 및 디바이스 특성을 모두 포함할 수 있습니다.  
      - **디바이스**:  *디바이스* 인증서는 인증서의 주체와 SAN에 있는 디바이스 특성만 포함할 수 있습니다.  
      
        키오스크와 같은 사용자가 없는 디바이스 또는 Windows 디바이스에 대해 **디바이스**를 사용합니다. Windows 디바이스에서 인증서는 로컬 컴퓨터 인증서 저장소에 배치됩니다.  

   - **주체 이름 형식**:  
     인증서 요청 시 Intune에서 자동으로 주체 이름을 만드는 방식을 선택합니다. 주체 이름 형식에 대한 옵션은 **사용자** 또는 **디바이스** 중에서 선택하는 인증서 유형에 따라 달라집니다.  

     > [!NOTE]  
     > 결과 CSR(인증서 서명 요청)의 주체 이름에 다음 문자 중 하나가 이스케이프 문자로 포함되면(앞에 백슬래시 \\ 포함) SCEP를 사용하여 인증서를 가져오는 [알려진 문제](#avoid-certificate-signing-requests-with-escaped-special-characters)가 있습니다.
     > - \+
     > - ;
     > - ,
     > - =

     - **사용자 인증서 유형**  
       *주체 이름 형식*에 대한 형식 옵션은 다음과 같습니다.  
       - **구성되지 않음**
       - **일반 이름**
       - **메일이 포함된 일반 이름**
       - **메일인 일반 이름**
       - **IMEI(International Mobile Equipment Identity)**
       - **일련 번호**
       - **사용자 지정**: 이 옵션을 선택하면 **사용자 지정** 텍스트 상자도 표시됩니다. 이 필드를 사용하여 변수를 포함한 사용자 지정 주체 이름 형식을 입력합니다. 사용자 지정 형식은 두 개의 변수 **CN(일반 이름)** 및 **E(메일)** 을 지원합니다. **CN(일반 이름)** 은 다음 변수 중 하나로 설정할 수 있습니다.

         - **CN={{UserName}}** : 사용자의 사용자 계정 이름입니다(예: janedoe@contoso.com).
         - **CN={{AAD_Device_ID}}** : Azure AD(Active Directory)에서 디바이스를 등록하는 경우 할당된 ID입니다. 이 ID는 일반적으로 Azure AD로 인증하는 데 사용됩니다.
         - **CN={{SERIALNUMBER}}** : 일반적으로 디바이스를 식별하는 제조업체에서 사용되는 고유한 SN(일련 번호)입니다.
         - **CN={{IMEINumber}}** : 휴대폰을 식별하는 데 사용되는 IMEI(International Mobile Equipment Identity) 고유 번호입니다.
         - **CN={{OnPrem_Distinguished_Name}}** : 쉼표로 구분된 상대 고유 이름 순서(예: *CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com*)입니다.

           *{{OnPrem_Distinguished_Name}}* 변수를 사용하려면 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)를 사용하여 *onpremisesdistinguishedname* 사용자 특성을 Azure AD와 동기화해야 합니다.

         - **CN={{onPremisesSamAccountName}}** : 관리자는 Azure AD Connect를 사용하여 Azure AD에 대한 Active Directory의 samAccountName 특성을 *onPremisesSamAccountName* 특성으로 동기화할 수 있습니다. Intune에서는 해당 변수를 인증서의 제목에 있는 인증 발급 요청의 일부로 대체할 수 있습니다. samAccountName 특성은 이전 버전의 Windows(Windows 2000 이전)에서 클라이언트 및 서버를 지원하는 데 사용되는 사용자 로그인 이름입니다. 사용자 로그인 이름 형식은 다음과 같습니다. *DomainName\testUser* 또는 *testUser*만

            *{{onPremisesSamAccountName}}* 변수를 사용하려면 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)를 사용하여 *onPremisesSamAccountName* 사용자 특성을 Azure AD와 동기화해야 합니다.

         이러한 변수 및 정적 문자열을 한 개 이상 조합하여 다음과 같은 사용자 지정 주체 이름 형식을 만들 수 있습니다.  
         - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
            
        이 예제에는 CN 및 E 변수를 사용하는 주체 이름 형식과 조직 구성 단위, 조직, 위치, 상태 및 국가 값에 해당하는 문자열이 포함됩니다. [CertStrToName 함수](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)에서는 이 함수와 지원되는 문자열을 보여 줍니다.

      - **디바이스 인증서 유형**  
        주체 이름 형식에 대한 형식 옵션은 다음 변수를 포함합니다. 
        - **{{AAD_Device_ID}}**
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{AzureADDeviceId}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}** *(Windows 및 도메인 가입 디바이스에만 적용됨)*
        - **{{MEID}}**
        
        텍스트 상자에서 이러한 변수와 변수 텍스트를 차례로 지정할 수 있습니다. 예를 들어, *Device1*이라는 디바이스의 일반 이름을 **CN={{DeviceName}}Device1**으로 추가할 수 있습니다.

        > [!IMPORTANT]  
        > - 변수를 지정하는 경우 오류를 방지하기 위해 예제에 표시된 대로 변수 이름을 중괄호 { }로 묶습니다.  
        > - **IMEI**, **SerialNumber** 및 **FullyQualifiedDomainName**과 같이 디바이스 인증서의 *주체* 또는 *SAN*에 사용되는 디바이스 속성은 디바이스에 대해 액세스 권한이 있는 사람이 스푸핑할 수 있는 속성입니다.
        > - 디바이스는 해당 디바이스에 설치할 해당 프로필의 인증서 프로필에 지정된 모든 변수를 지원해야 합니다.  예를 들어, SCEP 프로필의 주체 이름에 **{{IMEI}}** 가 사용되며 IMEI 번호가 없는 디바이스에 할당된 경우 프로필을 설치하지 못합니다.  
 


   - **주체 대체 이름**:  
     인증서 요청 시 Intune에서 SAN(주체 대체 이름)을 자동으로 만드는 방식을 선택합니다. SAN에 대한 옵션은 **사용자** 또는 **디바이스** 중에서 선택하는 인증서 유형에 따라 달라집니다.  

      - **사용자 인증서 유형**  
        사용 가능한 특성 중에서 선택합니다.  
        - **메일 주소**
        - **UPN(사용자 계정 이름)** 

        예를 들어 사용자 인증서 유형에는 주체 대체 이름에 UPN(사용자 계정 이름)이 포함될 수 있습니다. 클라이언트 인증서가 네트워크 정책 서버에 대한 인증에 사용되는 경우 주체 대체 이름을 UPN으로 설정합니다.

      - **디바이스 인증서 유형**  
        **특성** 드롭다운을 사용하고 특성을 선택한 후 해당 인증서 프로필에 **값** 및 **추가**를 할당합니다. 추가 특성을 선택하여 여러 값을 추가할 수 있습니다.  

        사용 가능한 특성은 다음과 같습니다.
        - **메일 주소**
        - **UPN(사용자 계정 이름)**
        - **DNS**

        *디바이스* 인증서 유형을 사용하면 값에 다음 디바이스 인증서 변수를 사용할 수 있습니다.  

        - **{{AAD_Device_ID}}**
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{AzureADDeviceId}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        특성 값을 지정하려면 변수 이름을 중괄호로 묶고 해당 변수에 대한 텍스트를 입력합니다. 예를 들어, DNS 특성 값 **{{AzureADDeviceId}}.domain.com**을 추가할 수 있습니다. 여기서 *.domain.com*은 텍스트입니다. 사용자 *User1*의 경우 메일 주소가 {{FullyQualifiedDomainName}}User1@Contoso.com으로 표시될 수 있습니다.  

        > [!IMPORTANT]  
        > - 디바이스 인증서 변수를 사용할 때 변수 이름을 중괄호 { }로 묶습니다.  
        > - 변수 뒤에 오는 텍스트에는 중괄호 **{ }** , 파이프 기호 **|** 및 세미콜론 **;** 을 사용하지 마세요.  
        > - **IMEI**, **SerialNumber** 및 **FullyQualifiedDomainName**과 같이 디바이스 인증서의 *주체* 또는 *SAN*에 사용되는 디바이스 속성은 디바이스에 대해 액세스 권한이 있는 사람이 스푸핑할 수 있는 속성입니다.  
        > - 디바이스는 해당 디바이스에 설치할 해당 프로필의 인증서 프로필에 지정된 모든 변수를 지원해야 합니다.  예를 들어, SCEP 프로필의 SAN에 **{{IMEI}}** 가 사용되며 IMEI 번호가 없는 디바이스에 할당된 경우 프로필을 설치하지 못합니다.

   - **인증서 유효 기간**:  
     인증서 템플릿에서 유효 기간보다 작은 값은 입력할 수 있지만 높은 값은 입력할 수 없습니다. [Intune 콘솔 내에서 설정할 수 있는 사용자 지정 값을 지원](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template)하도록 인증서 템플릿을 구성한 경우 이 설정을 사용하여 인증서가 만료되기 전까지 남은 시간을 지정합니다.  

     예를 들어 인증서 템플릿의 인증서 유효 기간이 2년이면 값을 1년으로 입력할 수는 있어도 5년으로는 입력할 수 없습니다. 또한 이 값은 발급 CA 인증서의 남은 유효 기간보다 작아야 합니다.

   - **KSP(키 스토리지 공급자)** :  
     *(적용 대상:  Windows 8.1 이상 및 Windows 10 이상)*  
     
     인증서에 대한 키를 저장할 위치를 지정합니다. 다음 값 중에서 선택합니다.  
     - **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈) KSP에 등록, 그렇지 않으면 소프트웨어 KSP에 등록**
     - **TPM(신뢰할 수 있는 플랫폼 모듈) KSP에 등록, 그러지 않으면 실패**
     - **Passport에 등록, 그러지 않으면 실패(Windows 10 이상)**
     - **소프트웨어 KSP에 등록**

   - **키 사용**:  
     다음과 같이 인증서에 대한 키 사용 옵션을 선택합니다.

     - **디지털 서명**: 디지털 서명으로 키를 보호하는 경우에만 키 교환을 허용합니다.
     - **키 암호화**: 키가 암호화된 경우에만 키 교환을 허용합니다.  

   - **키 크기(비트)** :  
     키에 포함된 비트 수를 선택합니다.  

   - **해시 알고리즘**:  
     *(Android, Android Enterprise, Windows Phone 8.1, Windows 8.1 이상 및 Windows 10 이상에 적용됨)*  

     이 인증서와 함께 사용할 수 있는 해시 알고리즘 유형 중 하나를 선택합니다. 연결 디바이스에서 지원되는 가장 강력한 보안 수준을 선택합니다.

   - **루트 인증서**:  
     이전에 구성한 후 이 SCEP 인증서 프로필의 해당 사용자 및 디바이스에 할당한 *신뢰할 수 있는 인증서 프로필*을 선택합니다. 신뢰할 수 있는 인증서 프로필은 신뢰할 수 있는 루트 CA 인증서를 사용하여 사용자 및 디바이스를 프로비저닝하는 데 사용됩니다. 신뢰할 수 있는 인증서 프로필에 대한 내용은 *Intune에서 인증을 위해 인증서 사용*의 [신뢰할 수 있는 루트 CA 인증서 내보내기](certificates-configure.md#export-the-trusted-root-ca-certificate) 및 [신뢰할 수 있는 인증서 프로필 만들기](certificates-configure.md#create-trusted-certificate-profiles)를 참조하세요. 루트 인증 기관과 발급 인증 기관이 있는 경우 발급 인증 기관과 연결된 신뢰할 수 있는 루트 인증서 프로필을 선택합니다.

   - **확장 키 사용**:  
     인증서의 용도에 대한 값을 추가합니다. 대부분의 경우 인증서는 사용자 또는 디바이스가 서버에 인증할 수 있도록 *클라이언트 인증*이 필요합니다. 필요에 따라 다른 키 사용을 추가할 수 있습니다.

   - **갱신 임계값(%)** :  
     디바이스에서 인증서 갱신을 요청하기 전까지 남은 인증서 수명을 백분율로 입력합니다. 예를 들어, 20을 입력하면 인증서 갱신은 인증서가 80% 만료될 때 시도되며 갱신에 성공할 때까지 계속 시도됩니다. 갱신되면 새 인증서가 생성되어 새 퍼블릭/프라이빗 키 쌍이 생성됩니다.

   - **SCEP 서버 URL**:  
     SCEP를 통해 인증서를 발급하는 NDES 서버의 URL을 하나 이상 입력합니다. 예를 들어 *https://ndes.contoso.com/certsrv/mscep/mscep.dll* 과 같이 입력합니다. URL이 이 프로필을 사용하여 디바이스에 무작위로 푸시되는 경우 필요에 따라 부하 분산을 위해 다른 SCEP URL을 추가할 수 있습니다. SCEP 서버 중 하나를 사용할 수 없는 경우 SCEP 요청은 실패하며 후속 디바이스 체크 인에서 가동 중지된 동일한 서버에 대해 인증서 요청이 수행될 수 있습니다.

7. **확인**을 선택하고 **만들기**를 선택합니다. 프로필이 만들어지고 *디바이스 구성 - 프로필* 목록에 나타납니다.

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>이스케이프된 특수 문자를 사용하여 인증서 서명 요청 방지
다음 특수 문자 중 하나 이상이 이스케이프 문자로 들어 있는 CN(주체 이름)이 포함된 SCEP 인증서 요청에 대해 알려진 문제가 있습니다. 주체 이름에 특수 문자 중 하나를 이스케이프 문자로 포함하면 CSR의 주체 이름이 올바르지 않게 되며, 이로 인해 Intune SCEP 챌린지 유효성 검사가 실패하고 인증서가 발급되지 않습니다.  

특수 문자는 다음과 같습니다.
- \+
- ,
- ;
- =

주체 이름에 특수 문자 중 하나가 포함된 경우 다음 옵션 중 하나를 사용하여 이 제한 사항을 해결합니다.  
- 특수 문자를 포함하는 CN 값을 따옴표로 캡슐화합니다.  
- CN 값에서 특수 문자를 제거합니다.  

**예를 들어**, *테스트 사용자(TestCompany, LLC)* 로 표시되는 주체 이름이 있습니다.  CN에서 *TestCompany*와 *LLC* 사이에 쉼표가 포함되면 문제가 발생합니다.  전체 CN을 따옴표로 묶거나 하거나 *TestCompany*와 *LLC* 사이에서 쉼표를 제거하여 이러한 문제를 방지할 수 있습니다.
- **따옴표 추가**: *CN=* ”Test User (TestCompany, LLC)”,OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **쉼표 제거**: *CN=Test User (TestCompany LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 그러나 백슬래시 문자를 사용하여 쉼표를 이스케이프하려고 하면 CRP 로그에 오류가 발생하면서 실패합니다.  
- **이스케이프된 쉼표**: *CN=Test User (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

이 오류는 다음 오류와 유사합니다. 

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>인증서 프로필 할당
다른 용도로 [디바이스 프로필을 배포](../configuration/device-profile-assign.md)하는 것과 동일한 방식으로 SCEP 인증서 프로필을 할당합니다. 그러나 계속하기 전에 다음 사항을 고려하세요.

- SCEP 인증서 프로필을 그룹에 할당하면 신뢰할 수 있는 루트 CA 인증서 파일(*신뢰할 수 있는 인증서 프로필*에 지정)이 디바이스에 설치됩니다. 디바이스는 SCEP 인증서 프로필을 사용하여 해당 신뢰할 수 있는 루트 CA 인증서의 인증서 요청을 만듭니다.  

- SCEP 인증서 프로필은 인증서 프로필을 만들 때 지정한 플랫폼을 실행하는 디바이스에만 설치됩니다.

- 사용자 컬렉션 또는 디바이스 컬렉션에 인증서 프로필을 할당할 수 있습니다.

- 디바이스를 등록한 후 인증서를 디바이스에 빠르게 게시하려면 인증서 프로필을 디바이스 그룹이 아닌 사용자 그룹에 할당합니다. 디바이스 그룹에 프로필을 할당하는 경우에는 디바이스에서 정책을 수신하기 전에 전체 디바이스 등록을 수행해야 합니다.  

- Intune 및 Configuration Manager의 공동 관리를 사용하는 경우 Configuration Manager에서 리소스 액세스 정책의 [워크로드 슬라이더](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)를 **Intune** 또는 **파일럿 Intune**으로 설정합니다. 이렇게 설정하면 Windows 10 클라이언트가 인증서 요청 프로세스를 시작할 수 있습니다.

- 신뢰할 수 있는 인증서 프로필 및 SCEP 인증서 프로필을 따로 만들어 할당하는 경우에도 둘 다 할당해야 합니다. 디바이스에 설치하지 않은 경우 SCEP 인증서 정책이 실패합니다. 신뢰할 수 있는 루트 인증서 프로필이 SCEP 프로필과 동일한 그룹에도 배포되어 있는지 확인합니다.


> [!NOTE]
> iOS 디바이스에서 SCEP 인증서 프로필이 Wi-Fi 또는 VPN 프로필과 같은 추가 프로필과 연결되면, 디바이스는 각각의 추가 프로필에 대한 인증서를 받습니다. 이로 인해 iOS 디바이스는 SCEP 인증서 요청에 의해 전달된 여러 인증서를 갖게 됩니다.  단일 인증서가 필요한 경우 SCEP 인증서 대신 PKCS 인증서를 사용해야 합니다.  이는 SCEP 및 PKCS 인증서를 디바이스에 전달하는 방법이 다르기 때문입니다.


## <a name="next-steps"></a>다음 단계  

[프로필 할당](../configuration/device-profile-assign.md)  
