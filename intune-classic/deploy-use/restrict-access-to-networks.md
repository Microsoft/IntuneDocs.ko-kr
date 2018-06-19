---
title: Cisco ISE를 통해 네트워크에 대한 액세스 보호
description: Cisco ISE에 의해 제어되는 WiFi 및 VPN에 액세스하기 전에 장치가 Intune에 등록되고 정책을 준수하도록 Intune에서 Cisco ISE를 사용합니다.
keywords: ''
author: dougeby
ms.author: angrobe
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1893410f4993d6feaa218d251dd7e2561286f5a3
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025215"
---
# <a name="using-cisco-ise-with-microsoft-intune"></a>Microsoft intune에서 Cisco ISE 사용

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Cisco ISE(ID 서비스 엔진)와 Intune을 통합하면 Intune 장치 등록 및 규정 준수 상태를 사용하여 ISE 환경에서 네트워크 정책을 작성할 수 있습니다. 이러한 정책을 사용하여 회사 네트워크에 대한 액세스가 Intune에서 관리되고 Intune 정책을 준수하는 장치로 제한되도록 할 수 있습니다.

## <a name="configuration-steps"></a>구성 단계

이 통합을 사용하려는 경우 Intune 테넌트에서는 어떤 설정 작업도 필요하지 않습니다. Intune 테넌트에 액세스하려면 Cisco ISE 서버에 대한 권한을 제공해야 합니다. 이 작업이 완료되면 Cisco ISE 서버에서 나머지 설정 작업이 진행됩니다. 이 문서에서는 ISE 서버에 Intune 테넌트 액세스 권한을 제공하는 방법에 대해 설명합니다.

### <a name="step-1-manage-the-certificates"></a>1단계: 인증서 관리
Azure AD(Azure Active Directory) 콘솔에서 인증서를 내보낸 다음, ISE 콘솔의 신뢰할 수 있는 인증서 저장소로 가져옵니다.

#### <a name="internet-explorer-11"></a>Internet Explorer 11


   a. 관리자 권한으로 Internet Explorer를 실행하고 Azure AD 콘솔에 로그인합니다.

   b. 주소 표시줄에서 자물쇠 아이콘을 선택하고 **인증서 보기**를 선택합니다.

   c. 인증서 속성의 **세부 정보** 탭에서 **파일에 복사**를 선택합니다.

   d. **인증서 내보내기 마법사** 시작 페이지에서 **다음**을 선택합니다.

   e. **내보내기 파일 형식** 페이지에서 기본값인 **DER로 인코딩된 바이너리 X.509(.CER)** 를 선택하고 **다음**을 선택합니다.  

   f. **내보낼 파일** 페이지에서 **찾아보기**를 선택하여 파일을 저장할 위치를 선택하고 파일 이름을 제공합니다. 내보낼 파일을 선택한 것 같지만 실제로는 내보낸 인증서가 저장될 파일에 이름을 지정하게 되는 것입니다. **다음** &gt; **마침**을 선택합니다.

   g. ISE 콘솔 내에서 Intune 인증서(내보낸 파일)를 **신뢰할 수 있는 인증서** 저장소로 가져옵니다.

#### <a name="safari"></a>Safari

 a. Azure AD 콘솔에 로그인합니다.

b. 잠금 아이콘 &gt; **추가 정보**를 선택합니다.

   c. **인증서 보기** &gt; **세부 정보**를 선택합니다.

   d. 인증서를 선택하고 **내보내기**를 선택합니다. 

   e. ISE 콘솔 내에서 Intune 인증서(내보낸 파일)를 **신뢰할 수 있는 인증서** 저장소로 가져옵니다.

> [!IMPORTANT]
>
> 인증서 만료 날짜를 확인합니다. 이 날짜가 완료되면 인증서를 내보내고 새 인증서를 가져와야 하기 때문입니다.


### <a name="obtain-a-self-signed-cert-from-ise"></a>ISE에서 자체 서명된 인증서 가져오기 

1. ISE 콘솔에서 **관리** > **인증서** > **시스템 인증서** > **자체 서명된 인증서 생성**로 이동합니다.  
2. 자체 서명된 인증서를 내보냅니다.
3. 텍스트 편집기에서 내보낸 인증서를 편집합니다.

   - Delete **-----BEGIN CERTIFICATE-----**
   - Delete **-----END CERTIFICATE-----**

모든 텍스트를 한 줄에 입력해야 합니다.


### <a name="step-2-create-an-app-for-ise-in-your-azure-ad-tenant"></a>2단계: Azure AD 테넌트에서 ISE용 앱 만들기
1. Azure AD 콘솔에서 **응용 프로그램** > **응용 프로그램 추가** > **조직에서 개발 중인 응용 프로그램 추가**를 선택합니다.
2. 앱의 이름 및 URL을 제공합니다. URL은 회사 웹 사이트일 수 있습니다.
3. 앱 매니페스트(JSON 파일)를 다운로드합니다.
4. 매니페스트 JSON 파일을 편집합니다. 1단계에서 편집한 인증서 텍스트를 **keyCredentials** 설정 값으로 제공합니다.
5. 해당 이름을 변경하지 않고 파일을 저장합니다.
6. Microsoft Graph 및 Microsoft Intune API에 대한 사용 권한이 있는 앱을 제공합니다.

   a. Microsoft Graph에 대해 다음을 선택합니다.
    - **응용 프로그램 사용 권한**: 디렉터리 데이터 읽기
    - **위임된 권한**:
        - 항상 사용자 데이터에 액세스
        - 사용자 로그인

   b. Microsoft Intune API의 **응용 프로그램 사용 권한**에서 **Intune에서 장치 상태 및 규정 준수 가져오기**를 선택합니다.

7. **끝점 보기**를 선택하고 ISE 설정 구성에 사용하기 위해 다음 값을 복사합니다.

|Azure AD 포털의 값|ISE 포털의 해당 필드|
|-------------------|---------------------------------|
|Microsoft Azure AD Graph API 끝점|자동 검색 URL|
|OAuth 2.0 토큰 끝점|토큰 발급 URL|
|클라이언트 ID로 코드 업데이트|클라이언트 ID|

### <a name="step-4-upload-the-self-signed-certificate-from-ise-into-the-ise-app-you-created-in-azure-ad"></a>4단계: ISE의 자체 서명된 인증서를 Azure AD에서 만든 ISE 앱으로 업로드
1. Base64로 인코딩된 인증서 값과 지문을 .cer X509 공용 인증서 파일에서 가져옵니다. 이 예제에서는 PowerShell을 사용합니다.


~~~
  $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
  $cer.Import(“mycer.cer”)
  $bin = $cer.GetRawCertData()
  $base64Value = [System.Convert]::ToBase64String($bin)
  $bin = $cer.GetCertHash()
  $base64Thumbprint = [System.Convert]::ToBase64String($bin)
  $keyid = [System.Guid]::NewGuid().ToString()

Store the values for $base64Thumbprint, $base64Value and $keyid, to be used in the next step.
~~~
2. 매니페스트 파일을 통해 인증서를 업로드합니다. [Azure 관리 포털](https://manage.windowsazure.com)에 로그인합니다.
3. Azure AD 스냅인에서 X.509 인증서로 구성할 응용 프로그램을 찾습니다.
4. 응용 프로그램 매니페스트 파일을 다운로드합니다. 
5. 빈 “KeyCredentials”: [], 속성을 다음 JSON으로 바꿉니다.  KeyCredential 복합 형식은 [Entity and complex type reference](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType)(엔터티 및 복합 형식 참조)에 나와 있습니다.


~~~
“keyCredentials“: [
{
 “customKeyIdentifier“: “$base64Thumbprint_from_above”,
 “keyId“: “$keyid_from_above“,
 “type”: “AsymmetricX509Cert”,
 “usage”: “Verify”,
 “value”:  “$base64Value_from_above”
 }2. 
 ], 
~~~

예를 들면 다음과 같습니다.

    “keyCredentials“: [
    {
    “customKeyIdentifier“: “ieF43L8nkyw/PEHjWvj+PkWebXk=”,
    “keyId“: “2d6d849e-3e9e-46cd-b5ed-0f9e30d078cc”,
    “type”: “AsymmetricX509Cert”,
    “usage”: “Verify”,
    “value”: “MIICWjCCAgSgAwIBA***omitted for brevity***qoD4dmgJqZmXDfFyQ”
    }
    ],

6. 변경 내용을 응용 프로그램 매니페스트 파일에 저장합니다.
7. 편집한 응용 프로그램 매니페스트 파일을 Azure 관리 포털을 통해 업로드합니다.
8. 선택 사항: X.509 인증서가 응용 프로그램에 있는지 확인하려면 다시 매니페스트를 다운로드하세요.

>[!NOTE]
>
> KeyCredentials는 컬렉션이므로 롤오버 시나리오에서는 여러 X.509 인증서를 업로드하고 손상 시나리오에서는 인증서를 삭제할 수 있습니다.


### <a name="step-4-configure-ise-settings"></a>4단계: ISE 설정 구성
ISE 관리 콘솔에서 다음 설정 값을 제공합니다.
  - **서버 유형**: 모바일 장치 관리자
  - **인증 유형**: OAuth - 클라이언트 자격 증명
  - **자동 검색**: 예
  - **자동 검색 URL**: *1단계의 값 입력*
  - **클라이언트 ID**: *1단계의 값 입력*
  - **토큰 발급 URL**: *1단계의 값 입력*



## <a name="information-shared-between-your-intune-tenant-and-your-cisco-ise-server"></a>Intune 테넌트와 Cisco ISE 서버 간에 공유되는 정보
이 표에서는 Intune 테넌트와 Intune에서 관리되는 장치용 Cisco ISE 서버 간에 공유되는 정보를 보여 줍니다.

|속성|  설명|
|---------------|------------------------------------------------------------|
|complianceState|장치가 규정을 준수하는지 준수하지 않는지 여부를 나타내는 True 또는 false 문자열입니다.|
|isManaged|클라이언트가 Intune에 의해 관리되는지 여부를 나타내는 True 또는 false 문자열입니다.|
|macAddress|장치의 Mac 주소입니다.|
|serialNumber|장치의 일련 번호입니다. iOS 장치에만 적용됩니다.|
|imei|IMEI(15자리 10진수: 14자리 + 확인 번호) 또는 IMEISV(16자리) 숫자에는 장치의 원본, 모델 및 일련 번호에 대한 정보를 포함되어 있습니다. 이 번호 구조는 3GPP TS 23.003에 지정되어 있습니다. SIM 카드가 있는 장치에만 적용됩니다.|
|udid|고유한 장치 식별자로 40개 문자 및 숫자 시퀀스입니다. iOS 장치에 해당됩니다.|
|meid|모바일 장치 식별자로, CDMA 모바일 스테이션 장비의 물리적 부분을 식별하는 전역적으로 고유한 번호입니다. 숫자 형식은 3GPP2 보고서 S. R0048로 정의되지만 실질적으로는 16진수를 포함하는 IMEI로 표시될 수 있습니다. MEID는 56비트 길이(14자리 16진수)입니다. 8비트 지역 코드(RR), 24비트 제조업체 코드 및 24비트 제조업체 할당 일련 번호를 포함하는 3개의 필드로 구성됩니다.|
|osVersion|장치의 운영 체제 버전입니다.
|model|장치 모델입니다.
|제조업체|장치 제조업체입니다.
|azureDeviceId|작업 공간이 Azure AD에 가입된 이후의 장치 ID입니다. 가입되지 않은 장치의 경우 빈 GUID로 표시됩니다.|
|lastContactTimeUtc|Intune 관리 서비스를 사용하여 장치를 마지막으로 체크 인한 날짜 및 시간입니다.


## <a name="user-experience"></a>사용자 환경

사용자가 등록 해제된 장치를 사용하여 리소스에 액세스하려고 할 경우 여기에 표시된 것과 같은 등록 메시지가 수신됩니다.

![등록 프롬프트 예제](../media/cisco-ise-user-iphone.png)

등록할 것을 선택하면 Intune 등록 프로세스 페이지로 리디렉션됩니다. Intune에 대한 사용자 등록 환경은 다음 항목에 설명되어 있습니다.

- [Intune에서 Android 장치 등록](/intune-user-help/enroll-your-device-in-Intune-android)</br>
- [Intune에서 iOS 장치 등록](/intune-user-help/enroll-your-device-in-intune-ios)</br>
- [Intune에서 Mac OS X 장치 등록](/intune-user-help/enroll-your-device-in-intune-mac-os-x)</br>
- [Intune에서 Windows 장치 등록](/intune-user-help/enroll-your-device-in-intune-windows)</br>

또한 사용자 환경에 대한 사용자 지정된 지침을 만드는 데 사용할 수 있는 [다운로드 가능한 등록 지침 집합](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)도 있습니다.


### <a name="see-also"></a>참고 항목

[Cisco ID 서비스 엔진 관리자 가이드, 릴리스 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)
