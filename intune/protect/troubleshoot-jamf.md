---
title: Microsoft Intune와 Jamf Pro 통합 문제 해결
titleSuffix: Microsoft Intune
description: Mac 용 Jamf Pro 장치를 통합할 때 가장 일반적인 몇 가지 문제를 해결 하기 위한 제안 사항을 Microsoft Intune 합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e92e3442e1347cb1a2cd1c737078912b74f075c9
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817640"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>Jamf Pro와 Microsoft Intune의 통합 문제 해결

이 문서는 Intune 관리자가 Jamf Pro for macOS와 Intune의 통합 관련 문제를 이해 하 고 해결 하는 데 도움이 됩니다.

> [!TIP]  
> 이 문서에 포함 된 대부분의 정보는 support.microsoft.com의 [Microsoft Intune와 Jamf를 통합할 때 발생 하는 문제 해결](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune) 에 처음 나타났습니다.

## <a name="prerequisites"></a>전제 조건

문제 해결을 시작 하기 전에 몇 가지 기본적인 정보를 수집 하 여 문제를 명확 하 게 파악 하 고 해결 시간을 단축 합니다. 예를 들어 Jamf 통합 관련 문제가 발생 하는 경우 항상 전제 조건이 충족 되었는지 확인 합니다. 문제 해결을 시작 하기 전에 다음 고려 사항을 검토 하세요.

- [Jamf Pro를 Intune과 통합](conditional-access-integrate-jamf.md#prerequisites)에서 필수 구성 요소를 검토 합니다.
- 모든 사용자에 게 Microsoft Intune 및 Microsoft AAD Premium P1 라이선스가 있어야 합니다. 
- Jamf Pro 콘솔에서 Microsoft Intune 통합 권한이 있는 사용자 계정이 있어야 합니다.
- Azure에서 전역 관리자 권한을 가진 사용자 계정이 있어야 합니다.


Intune과 Jamf Pro 통합을 조사할 때 다음 정보를 고려 하세요. 
- 정확한 오류 메시지가 무엇입니까?
- 오류 메시지는 어디에 있나요?
- 문제가 언제 시작되었습니까?  Intune과 Jamf Pro 통합이 작동 했습니까?
- 영향을 받는 사용자는 몇 개입니까? 모든 사용자에 게 영향을 미치는지 아니면 일부에만 적용 되나요?
- 영향을 받는 장치는 몇 개입니까? 모든 장치가 영향을 받는지 아니면 일부 입니까?
 

## <a name="common-problems"></a>일반적인 문제 

다음 정보는 Intune 및 Jamf Pro 통합을 설정한 후 장치에 대 한 일반적인 문제를 식별 하 고 해결 하는 데 도움이 될 수 있습니다.  

| 문제   | 추가 정보                  |
|-----------------|--------------------------|
| **Jamf Pro에서 장치가 응답 하지 않는 것으로 표시 됨**  | [장치가 Jamf Pro 또는 Azure AD를 사용 하 여 체크 인 되지 못함](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **앱 장치를 열 때 Mac 장치에서 키 집합 로그인을 요청 하면 등록에 실패 함**  | [앱이 AZURE AD에 등록할 수 있도록 사용자에 게 암호를 입력 하 라는 메시지가 표시 됩니다](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app). |
| **장치 등록 실패**  | 다음과 같은 원인이 적용 될 수 있습니다. <br> **-** [ ***원인 1*** -Azure의 Jamf Pro 앱에 잘못 된 사용 권한이 있습니다.](#cause-1) <br> **-** [ ***원인 2*** -Azure AD의 *Jamf 기본 macos 커넥터* 에 문제가 있습니다.](#cause-2) <br> **-** [ ***원인 3*** -사용자에 게 유효한 Intune 또는 Jamf 라이선스가 없습니다.](#cause-3) <br> **-** [ ***원인 4*** -사용자가 Jamf 셀프 서비스를 사용 하 여 회사 포털 앱을 시작 하지 않았습니다.](#cause-4) <br> **-** [ ***원인 5*** -Intune 통합이 해제 됨](#cause-5) <br> **-** [ ***원인 6*** -장치가 Intune에 이미 등록 되었거나 사용자가 장치를 여러 번 등록 하려고 시도 했습니다.](#cause-6) <br> **-** [ ***원인 7*** -JamfAAD 사용자의 키 집합에서 "Microsoft Workplace Join 키"에 대 한 액세스를 요청 합니다.](#cause-7) |
|  **Mac 장치가 Intune에서 호환 되지만 Azure에서 비준수를 표시 함** | [장치 등록 문제](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **Jamf를 사용 하 여 등록 된 Mac 장치용 Intune 콘솔에 중복 된 항목이 표시 됩니다.** | [동일한 장치를 가져오면 하는 여러 등록](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **준수 정책에서 장치를 평가 하지 못함** | [정책 대상 장치 그룹](#compliance-policy-fails-to-evaluate-the-device) |
| **Microsoft Graph API에 대 한 액세스 토큰을 검색할 수 없습니다.** | 다음과 같은 원인이 적용 될 수 있습니다. <br> [Azure에서 Jamf Pro 앱에 대 한](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure) - 권한 <br> [Jamf 또는 Intune에 대 한](#a-license-required-for-jamf-intune-integration-has-expired) -  만료 라이선스 <br> **-** [포트가 열려 있지 않음](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>Jamf Pro에서 장치가 응답 하지 않는 것으로 표시 됨  

**원인**: Jamf Pro에서 *응답 하지 않는* 것으로 표시 되는 장치의 일반적인 원인은 다음과 같습니다.

- 장치에서 Jamf Pro를 사용 하 여 체크 인 하지 못했습니다.  
  Jamf Pro에서는 15 분 마다 장치를 체크 인할 것으로 예상 합니다. 24 시간 동안 체크 인 하지 못할 경우 Jamf에서 장치를 응답 하지 않는 것으로 표시 합니다.  

- 장치가 Azure AD에 체크 인 되지 않습니다.  
  Azure AD에 성공적으로 등록 되 면 macOS 장치에서 Azure 토큰을 수신 합니다.
  - 이 토큰은 12 시간 마다 새로 고쳐집니다.   
  - 24 시간 이상 토큰 새로 고침이 실패 하면 Jamf Pro는 장치를 응답 하지 않는 것으로 표시 합니다.  
  - Azure 토큰이 만료 되 면 사용자에 게 Azure에 로그인 하 여 새 토큰을 가져와야 한다는 메시지가 표시 됩니다. Azure 액세스를 위한 새로 고침 토큰은 7 일 마다 생성 됩니다.

**해결 방법**  
Jamf Pro에서 장치가 응답 하지 *않는* 것으로 표시 되 면 장치의 등록 된 사용자가 응답 하지 않는 상태를 수정 하기 위해 로그인 해야 합니다. 로그인 키 집합에서 Intune의 id가 있기 때문에 작업을 수행 하는 사용자 여야 합니다.



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>앱을 열 때 Mac 장치에서 키 집합 로그인을 묻는 메시지가 표시 됩니다.  

Intune 및 Jamf Pro 통합을 구성 하 고 조건부 액세스 정책을 배포한 후에는 Jamf Pro를 사용 하 여 관리 되는 장치 사용자는 팀, Outlook 및 Azure가 필요한 기타 앱과 같은 Microsoft Office 365 응용 프로그램을 열 때 암호를 묻는 메시지를 표시 합니다. AD 인증. 

예를 들어 Microsoft 팀을 열 때 다음 예제와 유사한 텍스트가 있는 프롬프트가 표시 됩니다.

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**원인**: 이러한 메시지는 Azure AD 등록이 필요한 적용 가능한 각 앱에 대해 Jamf Pro에 의해 생성 됩니다. 

**해결 방법**   
프롬프트에서 사용자는 Azure AD에 로그인 하기 위해 장치 암호를 제공 해야 합니다. 다음 옵션을 사용할 수 있습니다.
- **거부** -로그인 하지 않고 앱을 사용 하지 않습니다.
- **허용** -일회성 로그인. 다음에 앱을 열 때 로그인 하 라는 메시지가 다시 표시 됩니다.
- **항상 허용** -로그인 자격 증명은 응용 프로그램에 대해 캐시 됩니다. 다음에 앱을 열 때 로그인 하 라는 메시지가 표시 되지 않습니다.  

한 앱에 대해 *항상 허용* 을 선택 하면 이후 로그인에 대해서만 해당 앱이 승인 됩니다. 추가 앱은 *항상 허용*으로 설정 될 때까지 인증에 대 한 메시지를 표시 합니다. 한 앱에 대 한 캐시 된 자격 증명은 다른 앱에서 사용할 수 없습니다.  

### <a name="devices-fail-to-register"></a>장치 등록 실패  

Mac 장치를 등록 하는 데 실패 하는 몇 가지 일반적인 원인은 다음과 같습니다.  

#### <a name="cause-1"></a>원인 1  

**Azure의 Jamf Pro enterprise 응용 프로그램에 잘못 된 권한이 있거나 둘 이상의 사용 권한이 있습니다.**  

  Azure에서 앱을 만들 때 모든 기본 API 권한을 제거한 후 Intune에 *update_device_attributes*의 단일 사용 권한을 할당 해야 합니다. 

  **해결 방법**  
  검토 하 고 필요한 경우 Azure AD에서 만든 Jamf 앱에 대 한 사용 권한을 수정 합니다. [AZURE AD에서 Jamf에 대 한 응용 프로그램을 만들려면](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory)절차를 참조 하세요. 

#### <a name="cause-2"></a>원인 2  

**Azure AD 테 넌 트에서 **Jamf Native macOS 커넥터** 앱이 생성 되지 않았거나 커넥터에 대 한 동의가 전역 관리자 권한이 없는 계정으로 서명 되었습니다.**  

  **해결 방법**  
  Docs.jamf.com의 [Microsoft Intune와 통합](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html) 에서 *Macos Intune 통합 구성* 섹션을 참조 하세요. 

#### <a name="cause-3"></a>원인 3

**사용자에 게 유효한 Intune 또는 Jamf 라이선스가 없습니다.**  

  유효한 라이선스가 없으면 Jamf 라이선스가 만료 되었음을 나타내는 다음과 같은 오류가 발생할 수 있습니다.  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **해결 방법**
  - Jamf license: Jamf에 대 한 새 라이선스를 얻으려면 Jamf에 문의 하세요.  
  - Intune 라이선스: 사용자에 게 유효한 라이선스를 할당 하거나 Microsoft 또는 파트너에 게 문의 하 여 현재 라이선스를 얻는 방법에 대 한 정보를 확인 합니다.

#### <a name="cause-4"></a>원인 4  

**사용자가 *Jamf 셀프 서비스* 를 사용 하 여 회사 포털 앱을 시작 하지 않았습니다.**

장치를 성공적으로 등록 하 고 Jamf을 통해 Intune에 등록 하려면 사용자가 Jamf Self Service를 사용 하 여 Intune 회사 포털를 열어야 합니다. 사용자가 회사 포털을 수동으로 여는 경우 Jamf에 연결 하지 않고 장치를 등록 하 고 등록 합니다.  

장치에서 등록 하 고 등록 하는 데 사용 하는 서비스를 확인 하려면 장치에서 회사 포털 앱을 확인 합니다. Jamf를 통해 등록 하는 경우 셀프 서비스 앱을 열어 변경 하는 알림을 받게 됩니다.

회사 포털 앱에서 사용자는 **`Not registered`** 를 볼 수 있으며 다음 예와 유사한 항목이 회사 포털 로그에 나타날 수 있습니다.  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**해결 방법**  
Intune에서 Jamf로 등록 원본을 변경 하려면 다음을 수행 합니다.
1. [Intune에서 macOS 디바이스 등록을 취소합니다](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos). Intune에서 완전히 제거 되지 않는 장치에 대 한 더 많은 문제를 방지 하려면이 목록에서 [*원인 6*](#cause-6) 을 참조 하세요.  

2. 장치에서 Jamf 셀프 서비스를 사용 하 여 회사 포털 앱을 열고 Intune에 장치를 등록 합니다. 이 작업을 수행 하려면 Jamf을 사용 하 여 [macOS 용 회사 포털 앱을 배포](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)하 고 [Jamf Pro에서 사용자 장치를 Azure AD에 등록 하는 정책을 만들어야](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory)합니다.  

3. 포털이 열리면 첫 번째 화면에 로그인 하 라는 메시지가 표시 됩니다. 회사 또는 학교 계정을 사용합니다.  

4. 회사 포털에서 사용자의 계정 정보를 확인하고, 디바이스 등록 및 디바이스 준수 상태를 표시합니다. 노란색 삼각형은 학교 또는 회사의 macOS 디바이스를 보호하기 위해 수행해야 하는 작업을 강조 표시합니다. 시작을 클릭하여 등록을 시작합니다.  

5. 메시지가 표시되면 컴퓨터의 로그인 정보를 입력합니다.  
     
관리에서 디바이스를 등록하는 데 몇 분 정도 걸릴 수 있습니다. 그 동안 디바이스에서 다른 작업을 수행할 수 있습니다. 회사 액세스 설정이 완료되면 알려드리겠다는 메시지를 받게 됩니다.

#### <a name="cause-5"></a>원인 5  

**Intune 통합이 꺼져 있습니다.**

Intune 통합이 꺼져 있으면 사용자가 장치를 등록 하려고 할 때 다음 메시지와 함께 회사 포털 팝업 창이 표시 됩니다.  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

Jamf Pro 서버는 통합이 꺼져 있는 경우 intune에서 통합을 사용 하지 않도록 설정 하 여 Intune 서버에 펄스를 보냅니다. 

**해결 방법**  
Jamf Pro 내에서 Intune 통합을 다시 사용 하도록 설정 합니다. [Jamf Pro에서 Microsoft Intune 통합 구성](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro)을 참조하세요.


#### <a name="cause-6"></a>원인 6  

**장치가 이전에 Intune에 등록 되었거나, 사용자가 장치를 여러 번 등록 하려고 했습니다.**

장치가 Jamf에서 등록 취소, Intune에서 올바르게 제거 되지 않았거나, 몇 가지 등록이 시도 되 면 포털에서 동일한 장치의 여러 인스턴스가 표시 될 수 있습니다. 이로 인해 Jamf 등록이 실패 합니다.

**해결 방법**  
1. Mac에서 **터미널**을 시작 합니다.
2. **SUDO JAMF removemdmprofile**을 실행 합니다.
3. **SUDO JAMF removeFramework**를 실행 합니다.
4. JAMF Pro 서버에서 컴퓨터의 인벤토리 레코드를 삭제 합니다.
5. AzureAD에서 장치를 삭제 합니다.
6. 장치가 있는 경우 장치에서 다음 파일을 삭제 합니다.
   - /Library/application support Support/Companyportal.appx. info
   - /Library/application support 지원/Companyportal.appx
   - /Library/application support Support/jamfsoftware. selfservice
   - /라이브러리/저장 된 응용 프로그램
   - State/jamfsoftware. selfservice. savedState
   - /Dev/ss 응용 프로그램 상태/m s. Companyportal.appx. savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Oom/<username>/Library/Cookies/Companyportal.appx
   - /Oom/<username>/Library/Cookies/jamfAAD
   - Companyportal.appx
   - Companyportal.appx. HockeySDK
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Microsoft 세션 전송 키 (공개 및 개인 키)
   - Microsoft Workplace Join 키 (공개 및 개인 키)
7. DeviceLogin.microsoft.com 인증서를 포함 하 여 *Microsoft*, *Intune*또는 *회사 포털*를 참조 하는 장치의 키 집합에서 모든 항목을 제거 합니다. JAMF 공개 키와 개인 키를 제외 하 고 *JAMF* 참조를 제거 합니다. 
   > [!IMPORTANT]  
   > 공개 키와 개인 키를 제거 하면 장치 등록이 중단 됩니다.

8. 찾은 다음 항목을 삭제 합니다.  
   - Kind: 응용 프로그램 암호; 계정: workplacejoin
   - Kind: 응용 프로그램 암호; 계정: workplacejoin. registeredUserPrincipalName
   - Kind: Certificate; 발급자: MS-조직 액세스
   - Kind: Identity 기본 설정 이름 (ADFS STS URL이 있는 경우): https://adfs\<DNSName>.com/adfs/ls
   - Kind: Identity 기본 설정 이름: https://enterpriseregistration.windows.net
   - Kind: Identity 기본 설정 이름: https://enterpriseregistration.windows.net/  
9. Mac 장치를 다시 시작 합니다.
10. 장치에서 회사 포털를 제거 합니다.
11. Portal.manage.microsoft.com으로 이동 하 여 Mac 장치의 모든 인스턴스를 삭제 합니다. 다음 단계로 이동 하기 전에 30 분 이상 기다립니다.
12. JAMF Pro에서 장치를 다시 등록 합니다.
13. 셀프 서비스를 다시 열고 등록 정책을 시작 합니다.


#### <a name="cause-7"></a>원인 7  

**JamfAAD 사용자의 키 집합에서 "Microsoft Workplace Join 키"에 대 한 액세스를 요청 합니다.**

등록 하는 동안 macOS 장치의 사용자는 키 집합에서 키에 대 한 JamfAAD 액세스를 허용 하도록 다음 프롬프트를 받습니다. 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**해결 방법**  
Azure AD에 장치를 성공적으로 등록 하려면 Jamf에서 사용자에 게 계정 암호를 입력 하 고 **허용**을 선택 해야 합니다.

이 요청은이 문서의 앞부분에서 [앱을 열 때 키 집합 로그인에 대 한 Mac 장치 요청 프롬프트](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app)와 비슷합니다.  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>Mac 장치가 Intune에서 호환 되지만 Azure에서 비준수를 표시 함  

**원인**: 다음 조건에 따라 장치가 Intune에서 준수 상태로 표시 될 수 있지만 Azure에서는 호환 되지 않습니다.  
- 장치가 올바르게 등록 되지 않았습니다.  
- 장치가 필요한 정리 없이 여러 번 등록 되었습니다.

**해결 방법**  
이 문제를 해결 하려면이 문서의 앞부분에 나오는 장치에서 *등록에 실패*하는 [*원인 6*](#cause-6) 의 해결 방법에 대해 설명 합니다. 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>Jamf를 사용 하 여 등록 된 Mac 장치용 Intune 콘솔에 중복 된 항목이 표시 됩니다.  
 
**원인**: 장치가 intune에 여러 번 등록 되어, 일반적으로 intune에서 제거 된 후 다시 등록 됩니다.  

Intune 및 Jamf Pro 통합에서 장치를 제거 하는 경우 일부 데이터는 남아 있을 수 있으며이로 인해 연속 등록이 중복 된 항목을 만들 수 있습니다.  

**해결 방법**  
이 문제를 해결 하려면이 문서의 앞부분에 나오는 장치에서 *등록에 실패*하는 [*원인 6*](#cause-6) 의 해결 방법에 대해 설명 합니다. 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>준수 정책에서 장치를 평가 하지 못함  

**원인**: Intune과 Jamf 통합은 장치 그룹을 대상으로 하는 규정 준수 정책을 지원 하지 않습니다. 

**해결 방법**  
사용자 그룹에 할당할 macOS 장치에 대 한 준수 정책을 수정 합니다. 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>Microsoft Graph API에 대 한 액세스 토큰을 검색할 수 없습니다.

이 경우 다음과 같은 오류가 발생합니다.

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

이 오류의 원인은 다음 중 하나일 수 있습니다. 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Azure에서 Jamf Pro 응용 프로그램에 대 한 사용 권한 문제가 있습니다.

Azure에서 Jamf Pro 앱을 등록 하는 동안 다음 조건 중 하나가 발생 했습니다.  
- 앱에서 두 개 이상의 사용 권한을 받았습니다.
- ***\< 회사 >* 에 대 한 관리자 동의 부여** 옵션이 선택 되지 않았습니다.  

**해결 방법**  
이 문서의 앞부분에 나오는 장치에 대 한 [등록 실패](#devices-fail-to-register)문제 해결을 참조 하세요.

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>Jamf에 대 한 라이선스가 필요 합니다.-Intune 통합이 만료 되었습니다.

**해결**방법: [장치 등록이 실패 하](#devices-fail-to-register)는 원인 3에 대 한 해결 방법을 참조 하세요. 

#### <a name="the-required-ports-arent-open-on-your-network"></a>필요한 포트가 네트워크에서 열려 있지 않습니다.

**해결**방법: Jamf Pro와 Intune을 통합 하기 위한 [필수 구성 요소](conditional-access-integrate-jamf.md#prerequisites) 에서 네트워크 포트에 대 한 정보를 검토 합니다.


## <a name="next-steps"></a>다음 단계
[Jamf Pro를 Intune과 통합 하는](conditional-access-integrate-jamf.md) 방법에 대 한 자세한 정보