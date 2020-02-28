---
title: Microsoft Intune에서 Windows 디바이스 등록 문제 해결
titleSuffix: Microsoft Intune
description: Intune에서 Windows 디바이스를 등록할 때 가장 일반적인 문제 중 일부에 대한 문제를 해결하기 위한 제안입니다.
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
ms.openlocfilehash: dae8e92209a8640ab3254e073d3043d390c3791b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514254"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune에서 iOS 디바이스 등록 문제 해결

이 문서는 Intune 관리자가 Intune에서 Windows 디바이스를 등록할 때 나타나는 문제들을 이해하고 해결하는 데 도움이 됩니다.

## <a name="prerequisites"></a>전제 조건
문제 해결을 시작하기 전에 몇 가지 기본적인 정보를 수집하는 것이 중요합니다. 이 정보를 통해 문제를 보다 잘 이해하고 해결 시간을 단축하는데 도움을 얻을 수 있습니다.

문제에 대한 다음 정보를 수집합니다.
- 사용자에게 유효한 Intune 라이선스가 할당되어 있나요? 사용자가 디바이스를 등록하려면 먼저 필요한 라이선스를 할당받아야 합니다.
- Windows 디바이스에 최신 업데이트가 설치되어 있습니까? Intune의 일부 기능은 최신 버전의 Windows에서만 작동합니다. Windows 업데이트를 통해 제공되는 알려진 문제에 대한 수정 사항이 많이 있습니다. 모든 최신 업데이트를 적용하면 Windows 디바이스 등록 문제를 해결하는 경우가 많습니다. 
- 정확한 오류 메시지가 무엇입니까?
- 어디서 오류 메시지가 표시됩니까?
- 문제가 언제 시작되었습니까? 등록이 실행되었습니까? 
- 어떤 플랫폼(Android, iOS/iPadOS, Windows)에 문제가 있습니까?
- 얼마나 많은 사용자가 영향을 받습니까? 영향을 받는 사용자는 전체입니까, 아니면 일부입니까?
- 영향을 받은 디바이스는 얼마나 됩니까? 영향을 받는 디바이스는 전체입니까, 아니면 일부입니까?
- MDM 기관이란 무엇입니까?
- 등록은 어떻게 진행됩니까? BYOD(Bring Your Own Device)와 등록 프로필이 포함된 Apple DEP(디바이스 등록 프로그램) 중 무엇을 사용합니까?

## <a name="error-messages"></a>오류 메시지

### <a name="this-user-is-not-authorized-to-enroll"></a>이 사용자에게 등록할 수 있는 권한이 없습니다.

오류 0x801c003: "이 사용자에게 등록할 수 있는 권한이 없습니다. 이 작업을 다시 시도하거나 시스템 관리자에게 오류 코드(0x801c0003)를 알리고 문의하세요."
오류 80180003: "오류가 발생했습니다. 이 사용자에게 등록할 수 있는 권한이 없습니다. 이 작업을 다시 시도하거나 시스템 관리자에게 오류 코드(80180003)를 알리고 문의하세요."

**원인:** 다음 조건이 발생한 경우: 

- 사용자가 Intune에서 허용된 최대 디바이스 수를 이미 등록했습니다.    
- 디바이스가 디바이스 유형 제한에 의해 차단되었습니다.    
- 컴퓨터에서 Windows 10 Home을 실행 중입니다. 그러나 Intune에 등록하거나 Azure AD에 가입하는 것은 Windows 10 Pro 및 이후 버전에서만 지원됩니다.

#### <a name="resolution"></a>해결 방법
이 문제에 대한 몇 가지 가능한 해결 방법은 다음과 같습니다.

##### <a name="remove-devices-that-were-enrolled"></a>등록된 디바이스 제거
1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.    
2. **사용자** > **모든 사용자**로 이동합니다.    
3. 영향을 받는 사용자 계정을 선택한 후 **디바이스**를 클릭합니다.    
4. 사용하지 않거나 원치 않는 디바이스를 선택한 후 **삭제**를 클릭합니다. 

##### <a name="increase-the-device-enrollment-limit"></a>디바이스 등록 제한 늘리기

> [!NOTE]
> 이 메서드는 영향을 받는 사용자 뿐 아니라 모든 사용자에 대한 디바이스 등록 한도를 늘립니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **장치** > **등록 제한** > **기본** **>** **속성** >  **(장치** 제한 **)** > (**장치 제한** >) **검토 + 저장으로 이동 합니다**.    
 

##### <a name="check-device-type-restrictions"></a>디바이스 유형 제한 확인
1. 전역 관리자 계정을 사용하여 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **등록 제한**으로 이동한 다음, **디바이스 유형 제한**에서 **기본** 제한을 선택합니다.    
3. **플랫폼**을 선택한 다음, **Windows(MDM)** 에 대해 **허용**을 선택합니다.

    > [!IMPORTANT]
    > 현재 설정이 이미 **허용**으로 되어 있다면 **차단**으로 변경하고 설정을 저장한 다음, 다시 **허용**으로 변경하고 설정을 다시 저장합니다. 이렇게 하면 등록 설정이 다시 설정됩니다.

4. 약 15분 정도 기다린 후 영향을 받는 디바이스를 다시 등록합니다.    

##### <a name="upgrade-windows-10-home"></a>Windows 10 Home 업그레이드
[Windows 10 Home을 Windows 10 Pro로 업그레이드](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro)하거나 이후 버전으로 업그레이드합니다. 



### <a name="this-user-is-not-allowed-to-enroll"></a>이 사용자는 등록할 수 없습니다.

오류 0x801c0003: "이 사용자는 등록할 수 없습니다. 다시 시도하거나 시스템 관리자에게 오류 코드(801c0003)를 알리고 문의하세요."

**원인:** **사용자가 Azure AD에 디바이스를 조인할 수 있습니다** 설정이 **없음**으로 설정됩니다. 이렇게 하면 새 사용자가 디바이스를 Azure AD에 조인할 수 없습니다. 따라서 Intune 등록이 실패합니다.

#### <a name="resolution"></a>해결 방법
1. [Azure Portal](https://portal.azure.com/)에 관리자로 로그인합니다.    
2. **Azure Active Directory** > **디바이스** > **디바이스 설정**으로 이동합니다.    
3. **사용자가 디바이스를 Azure AD에 조인할 수 있음**을 **모두**로 설정하세요.    
4. 디바이스를 다시 등록합니다.   

### <a name="the-device-is-already-enrolled"></a>디바이스가 이미 등록되어 있습니다.

오류 8018000a: "오류가 발생했습니다. 디바이스가 이미 등록되어 있습니다.  시스템 관리자에게 오류 코드(8018000a)를 알리고 문의하세요."

**원인:** 다음 조건 중 하나 이상이 true일 경우:
- 다른 사용자가 이미 Intune에 디바이스를 등록했거나 Azure AD에 디바이스를 조인했습니다. 이 경우에 해당되는지 여부를 확인하려면 **설정** > **계정** > **회사 액세스**로 이동합니다. 다음과 유사한 메시지를 찾습니다. "시스템의 다른 사용자가 이미 회사 또는 학교에 연결되어 있습니다. 해당 회사 또는 학교 연결을 제거하고 다시 시도하세요."    

#### <a name="resolution"></a>해결 방법

다음 방법 중 하나를 사용하여 이 문제를 해결할 수 있습니다.

##### <a name="remove-the-other-work-or-school-account"></a>다른 회사 또는 학교 계정 제거
1. Windows에서 로그아웃한 다음, 디바이스를 등록했거나 조인한 다른 계정을 사용하여 로그인합니다.    
2. **설정** > **계정** > **회사 액세스**로 이동한 다음 회사 또는 학교 계정을 제거합니다.
3. Windows에서 로그아웃한 다음, 계정을 사용하여 로그인합니다.    
4. Intune에 디바이스를 등록하거나 디바이스를 Azure AD에 조인합니다. 



### <a name="this-account-is-not-allowed-on-this-phone"></a>이 전화에는 이러한 계정이 허용되지 않습니다.

오류: "이 전화에는 이러한 계정이 허용되지 않습니다. 입력한 정보가 올바른지 확인한 후 다시 시도하거나 회사에 지원을 요청하십시오."

**원인:** 디바이스를 등록하려는 사용자에게 유효한 Intune 라이선스가 없습니다.

#### <a name="resolution"></a>해결 방법
사용자에게 유효한 Intune 라이선스를 할당한 후 디바이스를 등록합니다.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>MDM 사용 약관 엔드포인트가 올바르게 구성되지 않은 것 같습니다.

**원인:** 다음 조건 중 하나 이상이 true일 경우: 
 - Office 365 및 Intune용 MDM(Mobile Device Management)을 테넌트에서 모두 사용합니다. 디바이스를 등록하려는 사용자에게 유효한 Intune 라이선스 또는 Office 365 라이선스가 없습니다.     
- Azure AD의 MDM 사용 약관이 비어 있거나 올바른 URL을 포함하고 있지 않습니다.    

#### <a name="resolution"></a>해결 방법

이 문제를 해결하려면 다음 방법 중 하나를 사용하세요. 
 
##### <a name="assign-a-valid-license-to-the-user"></a>사용자에게 유효한 라이선스 할당
[Microsoft 365 관리 센터](https://portal.office.com/adminportal/home)로 이동한 다음, Intune 또는 Office 365 라이선스를 사용자에게 할당합니다.

##### <a name="correct-the-mdm-terms-of-use-url"></a>MDM 사용 약관 URL 수정
  1. [Azure Portal](https://portal.azure.com/)에 로그인한 다음 **Azure Active Directory**를 선택합니다.    
  2. **모바일(MDM 및 MAM)** 을 선택한 다음, **Microsoft Intune**을 클릭합니다.    
  3. **기본 MDM URL 복원**을 선택하고 **MDM 사용 약관 URL**이 **https://portal.manage.microsoft.com/TermsofUse.aspx** 로 설정되어 있는지 확인합니다.    
  4. **저장**을 선택합니다.    


### <a name="something-went-wrong"></a>오류가 발생했습니다.

오류 80180026: "오류가 발생했습니다. 올바른 로그인 정보를 사용하고 있으며 소속 조직에서 이 기능을 사용하는지 확인합니다. 이 작업을 다시 시도하거나 시스템 관리자에게 오류 코드(80180026)를 알리고 문의하세요."

**원인:** 이 오류는 Windows 10 컴퓨터를 Azure AD에 조인하려고 시도할 때 그리고 다음의 두 조건에 모두 해당될 때 발생할 수 있습니다. 
- Azure에서 MDM 자동 등록을 사용하도록 설정합니다.    
- Intune PC 클라이언트(Intune PC 에이전트)는 Windows 10 컴퓨터에 설치됩니다.

#### <a name="resolution"></a>해결 방법
다음 방법 중 하나를 사용하여 이 문제를 해결할 수 있습니다.

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Azure에서 MDM 자동 등록을 사용하지 않도록 설정합니다.
1. [Azure Portal](https://portal.azure.com/)에 로그인합니다.    
2. **Azure Active Directory** > **모바일(MDM 및 MAM)**  > **Microsoft Intune**으로 이동합니다.    
3. **MDM 사용자 범위**를 **없음**으로 설정한 후 **저장**을 클릭합니다.    
     
##### <a name="uninstall"></a>제거
컴퓨터에서 Intune PC 클라이언트 에이전트를 제거합니다.    

### <a name="the-software-cannot-be-installed"></a>소프트웨어를 설치할 수 없습니다.

오류: "소프트웨어를 설치할 수 없습니다. 0x80cf4017."

**원인:** 클라이언트 소프트웨어가 최신 버전이 아닙니다.

#### <a name="resolution"></a>해결 방법
1. [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)에 로그인하세요.    
2. **관리** > **클라이언트 소프트웨어 다운로드**로 이동한 후 **클라이언트 소프트웨어 다운로드**를 클릭합니다.    
3. 설치 패키지를 저장한 후 클라이언트 소프트웨어를 설치합니다. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>계정 인증서가 잘못되었으며 만료되었을 수 있습니다.

오류: "계정 인증서가 유효하지 않으며 만료되었을 수 있습니다. 0x80cf4017."

**원인:** 클라이언트 소프트웨어가 최신 버전이 아닙니다.

#### <a name="resolution"></a>해결 방법
1. [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)에 로그인하세요.    
2. **관리** > **클라이언트 소프트웨어 다운로드**로 이동한 후 **클라이언트 소프트웨어 다운로드**를 클릭합니다.    
3. 설치 패키지를 저장한 후 클라이언트 소프트웨어를 설치합니다.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>조직에서 이 버전의 Windows를 지원하지 않습니다. 

오류: "문제가 발생했습니다. 조직에서 이 버전의 Windows를 지원하지 않습니다.  (0x80180014)"

**원인:** Windows MDM 등록은 Intune 테넌트에서 사용하지 않도록 설정되어 있습니다.

#### <a name="resolution"></a>해결 방법
독립 실행형 Intune 환경에서 이 문제를 해결하려면 다음 단계를 수행합니다. 
 
1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **등록 제한** > 디바이스 유형 제한을 선택합니다.    
2. **속성** > **편집**(**플랫폼 설정** 옆) > **Windows(MDM)** 에 대해 **허용**을 선택합니다.    
3. **검토 + 저장**을 클릭합니다.    

### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>대량 등록 중에 설치 실패가 발생했습니다.

**원인:** 각 프로비전 패키지의 계정 패키지(Package_GUID)에 있는 Azure AD 사용자 계정이 디바이스를 Azure AD에 조인할 수 없습니다. 이러한 Azure AD 계정은 WCD(Windows 구성 디자이너) 또는 School PC 설정 앱을 사용하여 프로비전 패키지를 설정할 때 자동으로 생성되며, 이러한 계정은 디바이스를 Azure AD에 조인하는 데 사용됩니다.

#### <a name="resolution"></a>해결 방법
1. [Azure Portal](https://portal.azure.com/)에 관리자로 로그인합니다.    
2. **Azure Active Directory > 디바이스 > 디바이스 설정**으로 이동합니다.    
3. **사용자가 디바이스를 Azure AD에 조인할 수 있음**을 **모두** 또는 **선택됨**으로 설정하세요.

   **선택됨**을 선택할 경우, **선택됨**을 클릭한 후 **구성원 추가**를 클릭하여 Azure AD에 디바이스를 조인할 수 있는 모든 사용자를 추가합니다. 프로비전 패키지에 대한 모든 Azure AD 계정이 추가되었는지 확인합니다.
 
Windows 구성 디자이너의 프로비전 패키지를 만드는 방법에 대한 자세한 내용은 [Windows 10용 프로비전 패키지 만들기](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)를 참조하세요.

School PC 설정 앱에 대한 자세한 내용은 [School PC 설정 앱 사용](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app)을 참조하세요.


### <a name="auto-mdm-enroll-failed"></a>자동 MDM 등록: 실패 

그룹 정책을 사용하여 Windows 10 디바이스를 자동으로 등록하려고 할 경우, 다음과 같은 문제들이 발생합니다. 
- 작업 스케줄러의 **Microsoft** > **Windows** > **enterprisemgmt**에서, **AAD 작업에서 MDM에 자동으로 등록 하기 위해 등록 클라이언트에서 만든 일정**의 마지막 실행 결과는 다음과 같습니다. **이벤트 76 자동 MDM 등록: 실패(알 수 없는 Win32 오류 코드: 0x8018002b)**       
- 이벤트 뷰어에서 다음과 같은 이벤트가 **애플리케이션 및 서비스 로그/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/Admin**에 기록됩니다.   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**원인:** 다음 조건 중 하나 이상이 true일 경우: 
- UPN에는 .local(예: joe@contoso.local)과 같이 확인되지 않거나 라우팅이 불가능한 도메인이 포함되어 있습니다.    
- **MDM 사용자 범위**는 **없음**으로 설정됩니다. 

#### <a name="resolution"></a>해결 방법
UPN에 확인되지 않거나 라우팅이 불가능한 도메인이 포함되어 있다면 다음 단계를 수행합니다. 

1. Active Directory Domain Services(AD DS)가 실행되는 서버에서 **실행** 대화 상자에 **dsa.msc**를 입력하여 **Active Directory 사용자 및 컴퓨터**를 연 다음, **확인**을 클릭합니다.    
2. 도메인에서 **사용자**를 클릭한 후 다음을 수행합니다.  
    - 영향을 받는 사용자가 하나뿐인 경우, 사용자를 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다. **계정** 탭의 **사용자 로그온 이름** 아래에 있는 UPN 접미사 드롭다운 목록에서 contoso.com과 같은 올바른 UPN 접미사를 선택한 후 **확인**을 클릭합니다.    
    - 영향을 받는 사용자가 여럿일 경우, 해당 사용자들을 선택하고 **작업** 메뉴에서 **속성**을 클릭합니다. **계정** 탭에서 **UPN 접미사** 확인란을 선택하고 드롭다운 목록에서 contoso.com과 같은 올바른 UPN 접미사를 선택한 후 **확인**을 클릭합니다.
3. 다음 동기화를 기다리거나 관리자 권한 PowerShell 프롬프트에서 다음 명령을 실행하여 동기화 서버에서 델타 동기화를 강제로 적용합니다.
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

**MDM 사용자 범위**를 **없음**으로 설정한 경우, 다음 단계를 수행합니다. 
 
1. [Azure Portal](https://portal.azure.com/)에 로그인한 다음 **Azure Active Directory**를 선택합니다.
2. **모바일(MDM 및 MAM)** 을 선택한 후 **Microsoft Intune**을 선택합니다.    
3. **MDM 사용자 범위**를 **모두**로 설정합니다. 또는 **MDM 사용자 범위**를 **일부**로 설정하고 Windows 10 디바이스를 자동으로 등록할 수 있는 그룹을 선택합니다.    
4. **MAM 사용자 범위**를 **없음**으로 설정합니다.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Autopilot 프로필을 만드는 동안 오류가 발생했습니다.

**원인:** 디바이스 이름 템플릿의 지정된 명명 형식이 요구 사항에 맞지 않습니다. 예를 들어 직렬 매크로에 대해서는 %SERIAL% 대신 %serial%과 같이 소문자를 사용합니다.

#### <a name="resolution"></a>해결 방법

명명 형식이 다음 요구 사항을 충족하는지 확인합니다.

- 디바이스에 대한 고유한 이름을 만듭니다. 이름은 15자 이하여야 하고, 문자(a-z, A-Z), 숫자(0-9) 및 하이픈(‐)만 포함할 수 있습니다.
- 이름이 모두 숫자일 수는 없습니다.
- 이름에는 공백이 포함될 수 없습니다.
- %SERIAL% 매크로를 사용하여 하드웨어별 일련 번호를 추가합니다. 또는 %RAND:<# of digits>% 매크로를 사용하여 숫자의 임의 문자열을 추가합니다. 문자열에는 <# of digits> 숫자가 포함됩니다. 예를 들어, MYPC-% RAND:6%는 MYPC-123456과 같은 이름을 생성합니다.

### <a name="something-went-wrong-oobeidps"></a>오류가 발생했습니다. OOBEIDPS.

**원인:** 이 문제는 ID 공급자(IdP)에 대한 액세스를 차단하는 프록시, 방화벽 또는 그 외 네트워크 디바이스가 있는 경우에 발생합니다.

#### <a name="resolution"></a>해결 방법
Autopilot에 대한 인터넷 기반 서비스에 필요한 액세스가 차단되지는 않았는지 확인합니다. 자세한 내용은 [Windows Autopilot 네트워킹 요구 사항](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network)을 참조하세요.


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>모바일 관리를 위해 디바이스를 등록하는 중입니다(실패: 3, 0x801C03EA).

**원인:** 디바이스에 버전 2.0을 지원하는 TPM 칩이 있지만 아직 버전 2.0으로 업그레이드되지 않았습니다.

#### <a name="resolution"></a>해결 방법
TPM 칩을 버전 2.0으로 업그레이드합니다.

문제가 계속될 경우, 동일한 디바이스가 2개의 할당된 그룹에 있으며 그룹마다 다른 Autopilot 프로필이 할당되어 있는지 확인합니다. 디바이스가 두 그룹에 있는 경우, 해당 디바이스에 적용할 Autopilot 프로필을 결정한 후 다른 프로필의 할당을 제거합니다.

Autopilot을 사용하여 키오스크 모드에서 Windows 디바이스를 배포하는 방법에 대한 자세한 내용은 [Windows Autopilot을 사용하여 키오스크 배포](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)를 참조하세요.


### <a name="securing-your-hardware-failed-0x800705b4"></a>하드웨어 보안 설정(실패: 0x800705b4).

오류 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**원인:** 대상 Windows 디바이스가 다음 요구 사항 중 한 가지를 충족하지 않습니다.

- 디바이스에는 물리적 TPM 2.0 칩이 있어야 합니다. 가상 TPM(예: Hyper-V VM) 또는 TPM 1.2 칩을 사용하는 디바이스는 자체 배포 모드에서 작동하지 않습니다.
- 디바이스에서 다음 Windows 버전 중 하나를 실행해야 합니다.
    - Windows 10 빌드 1703 버전 이상
    - 하이브리드 Azure AD 조인이 사용되는 경우 Windows 10 빌드 1809 버전 이상


#### <a name="resolution"></a>해결 방법
대상 디바이스가 **원인** 섹션에 설명된 두 가지 요구 사항을 모두 충족하는지 확인합니다.

Autopilot을 사용하여 키오스크 모드에서 Windows 디바이스를 배포하는 방법에 대한 자세한 내용은 [Windows Autopilot을 사용하여 키오스크 배포](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)를 참조하세요.


### <a name="something-went-wrong-error-code-80070774"></a>오류가 발생했습니다. 오류 코드 80070774.

오류 0x80070774: 오류가 발생 했습니다. 올바른 로그인 정보를 사용하고 있으며 소속 조직에서 이 기능을 사용하는지 확인합니다. 이 작업을 다시 시도하거나 시스템 관리자에게 오류 코드(80070774)를 알리고 문의하세요."

이 문제는 대체로 첫 로그인 화면에서 디바이스가 시간이 초과될 때 하이브리드 Azure AD Autopilot 시나리오에서 디바이스를 다시 시작하기 전에 발생합니다. 이는 연결 문제로 인해 도메인 컨트롤러를 찾을 수 없거나 성공적으로 연결할 수 없음을 의미합니다. 또는 디바이스가 도메인에 조인할 수 없는 상태를 입력했습니다.

**원인:** 가장 일반적인 원인은 하이브리드 Azure AD 조인이 사용되고 있으며 사용자 할당 기능이 Autopilot 프로필에 구성되어 있다는 점 때문입니다. 사용자 할당 기능을 사용하여 초기 로그인 화면에서 디바이스에 대한 Azure AD 조인을 수행하면 디바이스는 온-프레미스 도메인에 조인할 수 없는 상태로 전환됩니다. 따라서 사용자 할당 기능은 표준 Azure AD 조인 Autopilot 시나리오에서만 사용해야 합니다.  하이브리드 Azure AD 조인 시나리오에서는 이 기능을 사용하면 안 됩니다.

#### <a name="resolution"></a>해결 방법

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **Windows** > **Windows 디바이스**를 차례대로 선택합니다.
2. 문제가 발생하는 디바이스를 선택한 후 가장 오른쪽에 있는 줄임표(...)를 클릭합니다.
3. **사용자 할당 취소**를 선택한 후 프로세스가 완료될 때까지 기다립니다.
4. OOBE를 다시 시도하기 전에 하이브리드 Azure AD Autopilot 프로필이 할당되었는지 확인합니다.

#### <a name="second-resolution"></a>두 번째 해결 방법
문제가 계속될 경우, 오프라인 도메인 가입 Intune 커넥터를 호스트하는 서버에서 ODJ Connector 서비스 로그 내에 이벤트 ID 30312가 기록되어 있는지 확인합니다. 이벤트 30312는 다음과 같습니다.

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

이 문제는 대체로 Windows Autopilot 디바이스를 만든 조직 구성 단위에 사용 권한을 잘못 위임했기 때문에 발생합니다. 자세한 내용은 [조직 구성 단위에서 컴퓨터 계정 한도 늘리기](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit)를 참조하세요.

1. **Active Directory 사용자 및 컴퓨터(DSA.msc)** 를 엽니다.
2. 하이브리드 Azure AD 조인 컴퓨터를 만드는 데 사용할 조직 구성 단위를 마우스 오른쪽 단추로 클릭한 다음, **제어 위임**을 선택합니다.
3. **제어 위임** 마법사에서 **다음** > **추가** > **개체 형식**을 선택합니다.
4. **개체 형식** 창에서 **컴퓨터** 확인란을 선택한 다음, **확인**을 선택합니다.
5. **사용자**, **컴퓨터** 또는 **그룹** 창의 **선택할 개체 이름 입력** 상자에 Connector가 설치된 컴퓨터의 이름을 입력합니다.
6. **이름 확인**을 선택하여 입력 항목의 유효성을 검사한 다음, **확인** > **다음**을 선택합니다.
7. **위임할 사용자 지정 작업 만들기** > **다음**을 차례로 선택합니다.
8. **폴더에 있는 다음 개체만** 확인란을 선택한 다음, **컴퓨터 개체**, **이 폴더에서 선택한 개체 만들기** 및 **이 폴더에서 선택한 개체 삭제** 확인란을 선택합니다.
9. **다음**을 선택합니다.
10. **사용 권한**에서 **모든 권한** 확인란을 선택합니다. 다른 모든 옵션이 선택됩니다.
11. **다음** > **마침**을 선택합니다.

### <a name="the-enrollment-status-page-times-out-before-the-sign-in-screen"></a>등록 상태 페이지가 로그인 화면 이전에 시간 초과됨

**원인:** 다음과 같은 조건들이 모두 충족될 경우, 이러한 문제가 발생할 수 있습니다.
- 등록 상태 페이지를 사용하여 비즈니스 앱에 대한 Microsoft Store를 추적합니다.
- 규정 준수 컨트롤로 표시되는 필수 디바이스를 사용하는 Azure AD 조건부 액세스 정책이 있습니다.
- 정책은 모든 클라우드 앱 및 Windows에 적용됩니다.

#### <a name="resolution"></a>해결 방법:
다음 중 하나를 시도합니다.
- 디바이스에 대한 Intune 규정 준수 정책을 대상으로 합니다. 사용자가 로그온하기 전에 규정 준수를 판정할 수 있는지 확인합니다.
- 스토어 앱에 대한 오프라인 라이선스를 사용합니다. 이와 같이 Windows 클라이언트는 디바이스 규정 준수를 판정하기 전에 Microsoft Store로 확인할 필요가 없습니다.



## <a name="next-steps"></a>다음 단계

- [Intune에서 디바이스 등록 문제 해결](../troubleshoot-device-enrollment-in-intune.md)
- [Intune 포럼에서 질문하기](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Microsoft Intune 지원 팀 블로그 보기](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Microsoft Enterprise Mobility + Security 블로그 보기](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Microsoft Intune에 대한 지원 받기](../fundamentals/get-support.md)
- [공동 관리 등록 오류 찾기](https://docs.microsoft.com/configmgr/comanage/how-to-monitor#enrollment-errors)
