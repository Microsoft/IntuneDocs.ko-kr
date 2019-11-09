---
title: Microsoft Intune에서 Windows 디바이스 등록 문제 해결
titleSuffix: Microsoft Intune
description: Intune에서 Windows 장치를 등록할 때 가장 일반적인 문제 중 일부에 대 한 문제 해결에 대 한 제안입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 348768be4a42667f579df0ccb500434425258db0
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712852"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune에서 iOS 디바이스 등록 문제 해결

이 문서는 intune 관리자가 Intune에서 Windows 장치를 등록할 때의 문제를 이해 하 고 해결 하는 데 도움이 됩니다

## <a name="prerequisites"></a>전제 조건
문제 해결을 시작 하기 전에 몇 가지 기본적인 정보를 수집 하는 것이 중요 합니다. 이 정보를 통해 문제를 보다 잘 이해 하 고 해결 시간을 단축할 수 있습니다.

문제에 대 한 다음 정보를 수집 합니다.
- 사용자에 게 유효한 Intune 라이선스가 할당 되어 있나요? 사용자가 디바이스를 등록하려면 먼저 필요한 라이선스를 할당받아야 합니다.
- Windows 장치에 최신 업데이트가 설치 되어 있습니까? Intune의 일부 기능은 최신 버전의 Windows 에서만 작동 합니다. Windows 업데이트를 통해 제공 되는 알려진 문제에 대 한 수정 사항이 많이 있습니다. 모든 최신 업데이트를 적용 하면 Windows 장치 등록 문제를 해결 하는 경우가 많습니다. 
- 정확한 오류 메시지가 무엇입니까?
- 어디서 오류 메시지가 표시됩니까?
- 문제가 언제 시작되었습니까? 등록이 작동 했습니까? 
- 어떤 플랫폼 (Android, iOS, Windows)에 문제가 있나요?
- 영향을 받는 사용자는 몇 개입니까? 모든 사용자에 게 영향을 미치는지 아니면 일부에만 적용 되나요?
- 영향을 받는 장치는 몇 개입니까? 모든 장치가 영향을 받는지 아니면 일부 입니까?
- MDM 기관 이란? System Center Configuration Manager 경우 사용 중인 Configuration Manager 버전은 무엇 인가요?
- 등록을 수행 하는 방법 등록 프로필을 사용 하 여 BYOD (사용자 소유의 장치) 또는 DEP (Apple 장비 등록 프로그램)를 사용 하나요?

## <a name="error-messages"></a>오류 메시지

### <a name="this-user-is-not-authorized-to-enroll"></a>이 사용자는 등록할 수 있는 권한이 없습니다.

오류 0x801c003: "이 사용자는 등록할 수 있는 권한이 없습니다. 이 작업을 다시 시도 하거나 시스템 관리자에 게 오류 코드 (0x801c0003)를 요청할 수 있습니다.
오류 80180003: "오류가 발생했습니다. 이 사용자는 등록할 수 있는 권한이 없습니다. 이 작업을 다시 시도 하거나 시스템 관리자에 게 오류 코드 80180003을 요청할 수 있습니다. "

**원인:** 다음 조건 중 하나입니다. 

- 사용자가 Intune에서 허용 된 최대 장치 수를 이미 등록 했습니다.    
- 장치가 장치 유형 제한에 의해 차단 되었습니다.    
- 컴퓨터에서 Windows 10 Home을 실행 하 고 있습니다. 그러나 Intune에 등록 하거나 Azure AD에 가입 하는 것은 Windows 10 Pro 이상 버전 에서만 지원 됩니다.

#### <a name="resolution"></a>해결 방법
이 문제에 대 한 몇 가지 가능한 해결 방법은 다음과 같습니다.

##### <a name="remove-devices-that-were-enrolled"></a>등록 된 장치 제거
1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인 합니다.    
2. **사용자**  > **모든 사용자**로 이동 합니다.    
3. 영향을 받는 사용자 계정을 선택 하 고 **장치**를 클릭 합니다.    
4. 사용 하지 않거나 원치 않는 장치를 선택 하 고 **삭제**를 클릭 합니다. 

##### <a name="increase-the-device-enrollment-limit"></a>디바이스 등록 제한 늘리기

> [!NOTE]
> 이 메서드는 영향을 받는 사용자 뿐 아니라 모든 사용자에 대 한 장치 등록 제한을 늘립니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인 합니다.
2. **장치 등록**  > **등록 제한**으로 이동한 다음 **장치 제한 제한**을 선택 합니다.    
3. **장치 제한**값을 늘립니다. 

##### <a name="check-device-type-restrictions"></a>디바이스 유형 제한 확인
1. 전역 관리자 계정을 사용 하 여 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431) 에 로그인 합니다.
2. **장치 등록**  > **등록 제한**으로 이동한 후 **장치 유형 제한**에서 **기본** 제한을 선택 합니다.    
3. **플랫폼**을 선택 하 고 Windows **허용** **(MDM)** 을 선택 합니다.

    > [!IMPORTANT]
    > 현재 설정이 이미 **허용**되는 경우 **차단**으로 변경 하 고 설정을 저장 한 다음 다시 **허용** 으로 변경 하 고 설정을 다시 저장 합니다. 이렇게 하면 등록 설정이 다시 설정 됩니다.

4. 약 15 분 정도 기다린 후 영향을 받는 장치를 다시 등록 합니다.    

##### <a name="upgrade-windows-10-home"></a>Windows 10 Home 업그레이드
[Windows 10 Home을 windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) 또는 더 높은 버전으로 업그레이드 합니다. 



### <a name="this-user-is-not-allowed-to-enroll"></a>이 사용자는 등록할 수 없습니다.

오류 0x801c0003: "이 사용자는 등록할 수 없습니다. 다시 시도 하거나 시스템 관리자에 게 801c0003 오류 코드를 문의할 수 있습니다.

**원인:** **사용자가 AZURE AD에 장치를 조인할 수 있습니다** . 설정이 **없음**으로 설정 됩니다. 이렇게 하면 새 사용자가 장치를 Azure AD에 조인할 수 없습니다. 따라서 Intune 등록이 실패 합니다.

#### <a name="resolution"></a>해결 방법
1. [Azure Portal](https://portal.azure.com/)에 관리자로 로그인합니다.    
2. **장치 설정** >  **Azure Active Directory**  > **장치** 로 이동 합니다.    
3. **사용자가 디바이스를 Azure AD에 조인할 수 있음**을 **모두**로 설정하세요.    
4. 디바이스를 다시 등록합니다.   

### <a name="the-device-is-already-enrolled"></a>디바이스가 이미 등록되어 있습니다.

오류 8018000a: "오류가 발생 했습니다. 디바이스가 이미 등록되어 있습니다.  시스템 관리자에 게는 오류 코드 8018000a를 사용 하 여 문의할 수 있습니다.

**원인:** 다음 조건 중 하나 이상이 true일 경우:
- 다른 사용자가 이미 Intune에 장치를 등록 했거나 Azure AD에 장치를 조인 했습니다. 이 경우에 해당 하는지 확인 하려면 **설정**  > **계정**  > **회사 액세스**로 이동 합니다. 다음과 유사한 메시지를 찾습니다. "시스템의 다른 사용자가 이미 회사 또는 학교에 연결 되어 있습니다. 해당 회사 또는 학교 연결을 제거 하 고 다시 시도 하세요. "    
- 컴퓨터에 구성 관리자 클라이언트 에이전트가 설치되어 있습니다.    

#### <a name="resolution"></a>해결 방법

다음 방법 중 하나를 사용하여 이 문제를 해결할 수 있습니다.

##### <a name="remove-the-other-work-or-school-account"></a>다른 회사 또는 학교 계정 제거
1. Windows에서 로그 아웃 한 다음 장치를 등록 하거나 가입한 다른 계정을 사용 하 여 로그인 합니다.    
2. **설정** > **계정** > **회사 액세스**로 이동한 다음 회사 또는 학교 계정을 제거합니다.
3. Windows에서 로그 아웃 한 다음 계정을 사용 하 여 로그인 합니다.    
4. Intune에 장치를 등록 하거나 장치를 Azure AD에 가입 시킵니다. 

##### <a name="remove-the-configuration-manager-client"></a>구성 관리자 클라이언트 제거
Configuration Manager 클라이언트를 제거한 후 장치를 다시 등록 합니다.



### <a name="this-account-is-not-allowed-on-this-phone"></a>이 전화에는이 계정이 허용 되지 않습니다.

오류: "이 계정은이 휴대폰에서 허용 되지 않습니다. 입력 한 정보가 올바른지 확인 한 후 다시 시도 하거나 회사에서 지원을 요청 하십시오. "

**원인:** 장치를 등록 하려는 사용자에 게 유효한 Intune 라이선스가 없습니다.

#### <a name="resolution"></a>해결 방법
사용자에 게 유효한 Intune 라이선스를 할당 하 고 장치를 등록 합니다.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>MDM 사용 약관 끝점이 올바르게 구성 되지 않은 것 같습니다.

**원인:** 다음 조건 중 하나 이상이 true일 경우: 
 - Office 365 및 Intune 용 MDM (모바일 장치 관리)을 테 넌 트에서 모두 사용 하 고, 장치를 등록 하려고 하는 사용자에 게 유효한 Intune 라이선스 또는 Office 365 라이선스가 없습니다.     
- Azure AD의 MDM 사용 약관은 비어 있거나 올바른 URL을 포함 하지 않습니다.    

#### <a name="resolution"></a>해결 방법

이 문제를 해결 하려면 다음 방법 중 하나를 사용 합니다. 
 
##### <a name="assign-a-valid-license-to-the-user"></a>사용자에 게 유효한 라이선스 할당
[Microsoft 365 관리 센터](https://portal.office.com/adminportal/home)로 이동한 다음 Intune 또는 Office 365 라이선스를 사용자에 게 할당 합니다.

##### <a name="correct-the-mdm-terms-of-use-url"></a>MDM 사용 약관 URL 수정
  1. [Azure Portal](https://portal.azure.com/)에 로그인한 다음 **Azure Active Directory**를 선택합니다.    
  2. **모바일 (MDM 및 MAM)** 을 선택 하 고 **Microsoft Intune**을 클릭 합니다.    
  3. **기본 Mdm Url 복원**을 선택 하 고 **MDM 사용 약관 url** 이 **https://portal.manage.microsoft.com/TermsofUse.aspx** 로 설정 되어 있는지 확인 합니다.    
  4. **저장**을 선택합니다.    


### <a name="something-went-wrong"></a>오류가 발생했습니다.

오류 80180026: "오류가 발생했습니다. 올바른 로그인 정보를 사용 하 고 있으며 조직에서이 기능을 사용 하는지 확인 합니다. 이 작업을 다시 시도 하거나 시스템 관리자에 게 오류 코드 80180026을 요청할 수 있습니다. "

**원인:** 이 오류는 Windows 10 컴퓨터를 Azure AD에 가입 하려고 시도 하 고 다음 두 조건에 모두 해당 하는 경우에 발생할 수 있습니다. 
- Azure에서 MDM 자동 등록을 사용 하도록 설정 합니다.    
- Intune PC 클라이언트 (Intune PC 에이전트) 또는 Configuration Manager 클라이언트 에이전트가 Windows 10 컴퓨터에 설치 되어 있어야 합니다.

#### <a name="resolution"></a>해결 방법
다음 방법 중 하나를 사용하여 이 문제를 해결할 수 있습니다.

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Azure에서 MDM 자동 등록을 사용 하지 않도록 설정 합니다.
1. [Azure 포털](https://portal.azure.com/)에 로그인합니다.    
2. **Azure Active Directory**  > **Mobility (MDM 및 MAM)**  > **Microsoft Intune**로 이동 합니다.    
3. **MDM 사용자 범위** 를 **없음**으로 설정 하 고 **저장**을 클릭 합니다.    
     
##### <a name="uninstall"></a>제거
컴퓨터에서 Intune PC 클라이언트 또는 Configuration Manager 클라이언트 에이전트를 제거 합니다.    

### <a name="the-software-cannot-be-installed"></a>소프트웨어를 설치할 수 없습니다.

오류: "소프트웨어를 설치할 수 없습니다, 0x80cf4017."

**원인:** 클라이언트 소프트웨어가 최신 버전이 아닙니다.

#### <a name="resolution"></a>해결 방법
1. [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)에 로그인하세요.    
2. **관리**  > **클라이언트 소프트웨어 다운로드**로 이동한 후 **클라이언트 소프트웨어 다운로드**를 클릭 합니다.    
3. 설치 패키지를 저장 한 후 클라이언트 소프트웨어를 설치 합니다. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>계정 인증서가 잘못되었으며 만료되었을 수 있습니다.

오류: "계정 인증서가 유효하지 않으며 만료되었을 수 있습니다. 0x80cf4017."

**원인:** 클라이언트 소프트웨어가 최신 버전이 아닙니다.

#### <a name="resolution"></a>해결 방법
1. [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)에 로그인하세요.    
2. **관리**  > **클라이언트 소프트웨어 다운로드**로 이동한 후 **클라이언트 소프트웨어 다운로드**를 클릭 합니다.    
3. 설치 패키지를 저장 한 후 클라이언트 소프트웨어를 설치 합니다.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>조직에서이 버전의 Windows를 지원 하지 않습니다. 

오류: "문제가 발생 했습니다. 조직에서이 버전의 Windows를 지원 하지 않습니다.  (0x80180014) "

**원인:** Windows MDM 등록은 Intune 테 넌 트에서 사용 하지 않도록 설정 됩니다.

#### <a name="resolution"></a>해결 방법
독립 실행형 Intune 환경에서이 문제를 해결 하려면 다음 단계를 수행 합니다. 
 
1. [Azure Portal](https://portal.azure.com/)에 관리자로 로그인합니다.    
2. 왼쪽에서 **Intune** 을 선택 하 고 **장치 등록**  > **등록 제한**으로 이동 합니다.    
3. **장치 유형 제한**에서 **플랫폼**을 클릭 한 다음 WINDOWS에 **허용** **(MDM)** 을 선택 합니다.    
4. **저장**을 클릭합니다.    
 
하이브리드 MDM에서 Intune 및 Configuration Manager로이 문제를 해결 하려면 다음 단계를 수행 합니다. 
1. Configuration Manager 콘솔을 엽니다.    
2. **관리**를 선택한 다음 **Cloud Services**를 선택 합니다.    
3. **Microsoft Intune 구독**을 마우스 오른쪽 단추로 클릭 한 다음 **플랫폼 구성 > Windows**를 선택 합니다.    
4. **Windows 등록** > **사용** > 확인란**을**선택 합니다.  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>대량 등록 중에 설치 오류가 발생 했습니다.

**원인:** 각 프로 비전 패키지의 계정 패키지 (Package_GUID)에 있는 Azure AD 사용자 계정은 장치를 Azure AD에 조인할 수 없습니다. 이러한 Azure AD 계정은 WCD (Windows 구성 디자이너) 또는 School Pc 설정 앱을 사용 하 여 프로 비전 패키지를 설정할 때 자동으로 생성 되며, 이러한 계정은 장치를 Azure AD에 조인 하는 데 사용 됩니다.

#### <a name="resolution"></a>해결 방법
1. [Azure Portal](https://portal.azure.com/)에 관리자로 로그인합니다.    
2. **장치 설정 > Azure Active Directory > 장치**로 이동 합니다.    
3. **사용자가 디바이스를 Azure AD에 조인할 수 있음**을 **모두** 또는 **선택됨**으로 설정하세요.

   **선택한**경우 선택 **됨**을 클릭 한 다음 **구성원 추가** 를 클릭 하 여 Azure AD에 장치를 조인할 수 있는 모든 사용자를 추가 합니다. 프로 비전 패키지에 대 한 모든 Azure AD 계정이 추가 되었는지 확인 합니다.
 
Windows 구성 디자이너의 프로 비전 패키지를 만드는 방법에 대 한 자세한 내용은 [windows 10 용 프로 비전 패키지 만들기](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)를 참조 하세요.

School Pc 설정 앱에 대 한 자세한 내용은 [School Pc 설정 앱 사용](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app)을 참조 하세요.


### <a name="auto-mdm-enroll-failed"></a>자동 MDM 등록: 실패 

그룹 정책를 사용 하 여 Windows 10 장치를 자동으로 등록 하려고 하면 다음과 같은 문제가 발생 합니다. 
- 작업 스케줄러의 **Microsoft** >  **Windows** > **enterprisemgmt**에서, **AAD 작업에서 MDM에 자동으로 등록 하기 위해 등록 클라이언트에서 만든 일정** 의 마지막 실행 결과는 다음과 같습니다. **이벤트 76 자동 MDM 등록: 실패 (알 수 없는 Win32 오류 코드: 0x8018002b)**       
- 이벤트 뷰어에서 다음 이벤트는 **응용 프로그램 및 서비스 Logs/Microsoft/Windows/DeviceManagement/Admin**에 기록 됩니다.   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**원인:** 다음 조건 중 하나 이상이 true일 경우: 
- UPN에는 로컬 (예: joe@contoso.local)과 같이 확인 되지 않거나 라우팅할 때 있지 않은 도메인이 포함 되어 있습니다.    
- **MDM 사용자 범위** 는 **없음**으로 설정 됩니다. 

#### <a name="resolution"></a>해결 방법
UPN에 확인 되지 않은 도메인 또는 라우팅 불가능 도메인이 포함 되어 있는 경우 다음 단계를 수행 합니다. 

1. Active Directory Domain Services (AD DS)이 실행 되는 서버에서 **실행** 대화 상자에 **dsa.msc** 를 입력 하 여 **Active Directory 사용자 및 컴퓨터** 를 연 다음 **확인**을 클릭 합니다.    
2. 도메인에서 **사용자** 를 클릭 하 고 다음을 수행 합니다.  
    - 영향을 받는 사용자가 하나뿐인 경우 사용자를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. **계정** 탭의 **사용자 로그온 이름**아래에 있는 upn 접미사 드롭다운 목록에서 CONTOSO.COM와 같은 올바른 upn 접미사를 선택 하 고 **확인**을 클릭 합니다.    
    - 영향을 받는 사용자가 여러 개인 경우 사용자를 선택 하 고 **작업** 메뉴에서 **속성**을 클릭 합니다. **계정** 탭에서 **upn 접미사** 확인란을 선택 하 고, 드롭다운 목록에서 CONTOSO.COM와 같은 올바른 upn 접미사를 선택한 다음 **확인**을 클릭 합니다.
3. 다음 동기화를 기다리거나, 관리자 권한 PowerShell 프롬프트에서 다음 명령을 실행 하 여 동기화 서버에서 델타 동기화를 강제로 적용 합니다.
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

**MDM 사용자 범위** 를 **없음**으로 설정한 경우 다음 단계를 수행 합니다. 
 
1. [Azure Portal](https://portal.azure.com/)에 로그인한 다음 **Azure Active Directory**를 선택합니다.
2. **모바일 (MDM 및 MAM)** 을 선택 하 고 **Microsoft Intune**를 선택 합니다.    
3. **MDM 사용자 범위** 를 **모두**로 설정 합니다. 또는 **MDM 사용자 범위** 를 **일부**로 설정 하 고 Windows 10 장치를 자동으로 등록할 수 있는 그룹을 선택 합니다.    
4. **MAM 사용자 범위** 를 **없음**으로 설정 합니다.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Autopilot 프로필을 만드는 동안 오류가 발생 했습니다.

**원인:** 장치 이름 템플릿의 지정 된 명명 형식이 요구 사항에 맞지 않습니다. 예를 들어,% 직렬% 대신% 직렬%와 같이 직렬 매크로에 대해 소문자를 사용 합니다.

#### <a name="resolution"></a>해결 방법

명명 형식이 다음 요구 사항을 충족 하는지 확인 합니다.

- 디바이스에 대한 고유한 이름을 만듭니다. 이름은 15자 이하여야 하고, 문자(a-z, A-Z), 숫자(0-9) 및 하이픈(‐)만 포함할 수 있습니다.
- 이름이 모두 숫자일 수는 없습니다.
- 이름에 공백을 포함할 수 없습니다.
- %SERIAL% 매크로를 사용하여 하드웨어별 일련 번호를 추가합니다. 또는% RAND: < # of digits >% 매크로를 사용 하 여 임의의 숫자 문자열을 추가 합니다. 문자열에는 숫자 < # > 숫자가 포함 됩니다. 예를 들어 MYPC-% RAND: 6%는 MYPC-123456와 같은 이름을 생성 합니다.

### <a name="something-went-wrong-oobeidps"></a>오류가 발생했습니다. OOBEIDPS.

**원인:** 이 문제는 IdP (Id 공급자)에 대 한 액세스를 차단 하는 프록시, 방화벽 또는 다른 네트워크 장치가 있는 경우에 발생 합니다.

#### <a name="resolution"></a>해결 방법
Autopilot에 대 한 인터넷 기반 서비스에 필요한 액세스가 차단 되지 않았는지 확인 합니다. 자세한 내용은 [Windows Autopilot 네트워킹 요구 사항](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network)을 참조 하세요.


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>모바일 관리를 위해 장치를 등록 하 고 있습니다 (실패: 3, 0x801C03EA).

**원인:** 장치에 버전 2.0을 지 원하는 TPM 칩이 있지만 아직 버전 2.0로 업그레이드 되지 않았습니다.

#### <a name="resolution"></a>해결 방법
TPM 칩을 버전 2.0으로 업그레이드 합니다.

문제가 지속 되 면 동일한 장치가 두 개의 할당 된 그룹에 있는지 확인 하 고 각 그룹이 다른 Autopilot 프로필을 할당 하 고 있는지 확인 합니다. 두 그룹에 있는 경우 장치에 적용할 Autopilot 프로필을 결정 한 다음 다른 프로필의 할당을 제거 합니다.

Autopilot를 사용 하 여 키오스크 모드에서 Windows 장치를 배포 하는 방법에 대 한 자세한 내용은 [Windows Autopilot를 사용 하 여 키오스크 배포](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)를 참조 하세요.


### <a name="securing-your-hardware-failed-0x800705b4"></a>하드웨어 보안 설정 (실패: 0x800705b4).

오류 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**원인:** 대상 Windows 장치가 다음 요구 사항 중 하나를 충족 하지 않습니다.

- 장치에는 물리적 TPM 2.0 칩이 있어야 합니다. 가상 Tpm (예: Hyper-v Vm) 또는 TPM 1.2 칩을 사용 하는 장치는 자체 배포 모드에서 작동 하지 않습니다.
- 장치에서 다음 Windows 버전 중 하나를 실행 해야 합니다.
    - Windows 10 빌드 1703 이상 버전
    - 하이브리드 Azure AD 조인이 사용 되는 경우 Windows 10 빌드 1809 이상 버전입니다.


#### <a name="resolution"></a>해결 방법
대상 장치가 **원인** 섹션에 설명 된 요구 사항을 모두 충족 하는지 확인 합니다.

Autopilot를 사용 하 여 키오스크 모드에서 Windows 장치를 배포 하는 방법에 대 한 자세한 내용은 [Windows Autopilot를 사용 하 여 키오스크 배포](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)를 참조 하세요.


### <a name="something-went-wrong-error-code-80070774"></a>오류가 발생했습니다. 오류 코드 80070774.

오류 0x80070774: 문제가 발생 했습니다. 올바른 로그인 정보를 사용 하 고 있으며 조직에서이 기능을 사용 하는지 확인 합니다. 이 작업을 다시 시도 하거나 오류 코드 80070774를 사용 하 여 시스템 관리자에 게 문의할 수 있습니다.

이 문제는 일반적으로 초기 로그인 화면에서 장치가 시간 초과 될 때 하이브리드 Azure AD Autopilot 시나리오에서 장치를 다시 시작 하기 전에 발생 합니다. 연결 문제로 인해 도메인 컨트롤러를 찾을 수 없거나 성공적으로 연결할 수 없음을 의미 합니다. 또는 장치가 도메인에 가입할 수 없는 상태를 입력 했습니다.

**원인:** 가장 일반적인 원인은 하이브리드 Azure AD 조인이 사용 되 고 있으며 사용자 할당 기능이 Autopilot 프로필에 구성 되어 있기 때문입니다. 사용자 할당 기능을 사용 하 여 초기 로그인 화면에서 장치에 대 한 Azure AD 조인을 수행 하면 장치는 온-프레미스 도메인에 가입할 수 없는 상태로 전환 됩니다. 따라서 사용자 할당 기능은 표준 Azure AD 조인 Autopilot 시나리오 에서만 사용 해야 합니다.  하이브리드 Azure AD 조인 시나리오에서는이 기능을 사용 하지 않아야 합니다.

#### <a name="resolution"></a>해결 방법

1. **Intune** >  **장치등록** > **Windows 등록** > **장치**로 이동 합니다.
2. 문제가 발생 하는 장치를 선택 > 가장 오른쪽에 있는 줄임표 (...)를 클릭 합니다.
3. **사용자 할당** 해제를 선택 하 고 프로세스가 완료 될 때까지 기다립니다.
4. OOBE를 다시 시도 하기 전에 하이브리드 Azure AD Autopilot 프로필이 할당 되었는지 확인 합니다.

#### <a name="second-resolution"></a>두 번째 해결 방법
문제가 지속 되 면 오프 라인 도메인 가입 Intune 커넥터를 호스트 하는 서버에서 ODJ Connector 서비스 로그 내에 이벤트 ID 30312이 기록 되어 있는지 확인 합니다. 이벤트 30312는 다음과 유사 합니다.

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

이 문제는 일반적으로 Windows Autopilot 장치를 만든 조직 구성 단위에 대 한 사용 권한을 잘못 위임 했기 때문에 발생 합니다. 자세한 내용은 [조직 구성 단위에서 컴퓨터 계정 제한 늘리기](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit)를 참조 하세요.

1. **Active Directory 사용자 및 컴퓨터(DSA.msc)** 를 엽니다.
2. 하이브리드 Azure AD 조인 컴퓨터를 만드는 데 사용할 조직 구성 단위를 마우스 오른쪽 단추로 클릭한 다음, **제어 위임**을 선택합니다.
3. **제어 위임** 마법사에서 **다음** > **추가** > **개체 형식**을 선택합니다.
4. **개체 형식** 창에서 **컴퓨터** 확인란을 선택한 다음, **확인**을 선택합니다.
5. **사용자**, **컴퓨터** 또는 **그룹** 창의 **선택할 개체 이름 입력** 상자에 Connector가 설치된 컴퓨터의 이름을 입력합니다.
6. **이름 확인** 을 선택 하 여 입력 > **확인**  > **다음**을 선택 합니다.
7. **위임할 사용자 지정 작업 만들기** > **다음**을 차례로 선택합니다.
8. **폴더에 있는 다음 개체만** 확인란을 선택한 다음, **컴퓨터 개체**, **이 폴더에서 선택한 개체 만들기** 및 **이 폴더에서 선택한 개체 삭제** 확인란을 선택합니다.
9. **다음**을 선택합니다.
10. **사용 권한**에서 **모든 권한** 확인란을 선택합니다. 다른 모든 옵션이 선택됩니다.
11. **다음**  > **마침**을 선택 합니다.

## <a name="next-steps"></a>다음 단계

- [Intune에서 디바이스 등록 문제 해결](../troubleshoot-device-enrollment-in-intune.md)
- [Intune 포럼에서 질문하기](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Microsoft Intune 지원 팀 블로그를 확인 하세요.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Microsoft Enterprise Mobility 및 보안 블로그 확인](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Microsoft Intune에 대한 지원 받기](../fundamentals/get-support.md)
- [공동 관리 등록 오류 찾기](https://docs.microsoft.com/sccm/comanage/how-to-monitor#enrollment-errors)