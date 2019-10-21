---
title: Microsoft Intune에서 Microsoft Defender ATP 사용 - Azure | Microsoft Docs
description: Intune에서 Microsoft Defender ATP(Advanced Threat Protection)를 사용하여 Intune 디바이스 설정, 구성, 온보딩 등을 마친 다음, Intune 디바이스 규정 준수 및 조건부 액세스 정책과 함께 디바이스 ATP 위험 평가를 사용하여 네트워크 리소스를 보호합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1e72e16eba8bb29adc7360db9e923a15d144b6e
ms.sourcegitcommit: b8127c7a62d9ac4d0f768980fa1424567bb58733
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72350038"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Intune에서 조건부 액세스로 Microsoft Defender ATP에 대한 규정 준수 적용  

Microsoft Defender ATP(Microsoft Defender Advanced Threat Protection)를 Mobile Threat Defense 솔루션으로 Microsoft Intune에 통합하여 보안 위반을 방지하고 조직 내에서 위반이 미치는 영향을 제한할 수 있습니다. Microsoft Defender ATP는 Windows 10 이상을 실행하는 디바이스에서 작동합니다.

성공하려면 다음 구성을 함께 사용합니다.
- **Intune과 Microsoft Defender ATP 간에 서비스간 연결을 설정합니다.** . 이 연결을 통해 Microsoft Defender ATP는 Intune으로 관리하는 Windows 10 디바이스에서 컴퓨터 위험에 대한 데이터를 수집할 수 있습니다.  
- **디바이스 구성 프로필을 사용하여 Microsoft Defender ATP에 디바이스를 온보딩합니다**. 디바이스를 온보딩하여 Microsoft Defender ATP와 통신하도록 구성하고 위험 수준을 평가하는 데 유용한 데이터를 제공합니다.  
 - **디바이스 규정 준수 정책을 사용하여 허용하려는 위험 수준을 설정합니다**. 위험 수준은 Microsoft Defender ATP에서 보고됩니다.  허용되는 위험 수준을 초과하는 디바이스는 비규격으로 식별됩니다.  
- **조건부 액세스 정책을 사용**하여 사용자가 비규격 디바이스에서 회사 리소스에 액세스하지 못하도록 차단합니다.  

또한 Intune을 Microsoft Defender ATP에 통합하면 ATP의 TVM(위협 및 취약성 관리)을 활용하고 [Intune을 사용하여 TVM이 식별한 엔드포인트 약점을 수정](atp-manage-vulnerabilities.md)할 수 있습니다.

## <a name="example-of-using-microsoft-defender-atp-with-intune"></a>Intune에서 Microsoft Defender ATP를 사용하는 예제  

다음 예제는 이러한 솔루션이 함께 작동하여 조직을 보호하는 방법을 설명합니다. 이 예제에서는 Microsoft Defender ATP 및 Intune이 이미 통합되어 있습니다.  

누군가가 포함된 악성 코드가 있는 Word 첨부 파일을 조직 내의 사용자에게 전송하는 경우를 고려합니다.  
- 사용자가 첨부 파일을 열고 콘텐츠를 활성화합니다.  
- 상승된 권한 공격이 시작되고, 원격 컴퓨터의 공격자가 공격 대상 디바이스에 대한 관리자 권한을 갖게 됩니다.  
- 그런 다음, 공격자가 사용자의 다른 디바이스에 원격으로 액세스합니다. 이 보안 위반은 전체 조직에 영향을 미칠 수 있습니다.  

Microsoft Defender ATP를 사용하면 이 시나리오와 같은 보안 이벤트를 편리하게 해결할 수 있습니다.  
- 이 예제에서 Microsoft Defender ATP는 디바이스에서 비정상적인 코드가 실행되었으며, 프로세스 권한 에스컬레이션이 발생하고 악성 코드가 삽입되고 의심스러운 원격 셸이 실행되었음을 감지합니다.  
- 디바이스의 이러한 작업을 기준으로, Microsoft Defender ATP는 [해당 디바이스를 고위험으로 분류하고](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity) Microsoft Defender Security Center 포털에 의심스러운 활동에 대한 자세한 보고서를 포함합니다.  

Intune 디바이스 규정 준수 정책에 따라 디바이스가 *중간* 또는 *높음* 위험 수준으로 분류되므로 손상된 디바이스는 비규격으로 분류됩니다. 이 분류를 통해 조건부 액세스 정책이 시작되고 해당 디바이스에서 회사 리소스에 대한 액세스를 차단할 수 있습니다.  

## <a name="prerequisites"></a>전제 조건

Intune에서 Microsoft Defender ATP를 사용하려면 다음을 구성했으며 사용할 준비가 되었는지 확인합니다.

- Enterprise Mobility + Security E3 및 Windows E5(또는 Microsoft 365 Enterprise E5)에 대한 라이선스가 부여된 테넌트
- Azure AD에 연결된 [Intune 관리](../enrollment/windows-enroll.md) Windows 10 디바이스가 포함된 Microsoft Intune 환경
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) 및 Microsoft Defender Security Center(ATP 포털)에 대한 액세스 권한

## <a name="enable-microsoft-defender-atp-in-intune"></a>Intune에서 Microsoft Defender ATP 사용

첫 번째 단계는 Intune과 Microsoft Defender ATP 간에 서비스간 연결을 설정하는 것입니다. 이를 위해 Microsoft Defender Security Center 및 Intune 둘 다에 대한 관리 권한이 필요합니다.  

### <a name="to-enable-defender-atp"></a>Defender ATP를 사용하도록 설정하려면  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 준수** > **Microsoft Defender ATP**를 선택한 후 *커넥터 설정* 아래에서 **Microsoft Defender Security Center 열기**를 선택합니다.

    ![Microsoft Defender Security Center를 열려면 선택](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. **Microsoft Defender Security Center**에서 다음을 수행합니다.
    1. **설정** > **고급 기능**을 선택합니다.
    2. **Microsoft Intune 연결**에서 **켜기**를 선택합니다.

        ![Intune에 대한 연결을 사용하도록 설정](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. **기본 설정 저장**을 선택합니다.

4. Intune, **디바이스 준수** > **Microsoft Defender ATP**로 돌아갑니다. **Windows 디바이스 버전 10.0.15063 이상을 Microsoft Defender ATP에 연결**을 **켜기**로 설정합니다.
5. **저장**을 선택합니다.

일반적으로 이 작업은 한 번 수행합니다. Intune 테넌트에 대해 Microsoft Defender ATP를 사용하도록 설정한 후에는 이 작업을 다시 수행할 필요가 없습니다.

> [!TIP]  
> Intune Mobile Threat Defense에 새 애플리케이션을 통합하고 Intune에 대한 연결을 사용하도록 설정하면 Intune은 Azure Active Directory에 클래식 조건부 액세스 정책을 만듭니다. [Defender ATP](advanced-threat-protection.md)나 추가 [MTD 파트너](mobile-threat-defense.md#mobile-threat-defense-partners)를 포함하여 통합되는 각 MTD 앱은 새 클래식 조건부 액세스 정책을 만듭니다. 이러한 정책은 무시할 수 있지만 편집 또는 삭제하거나 사용하지 않도록 설정할 수는 없습니다.
> 
> MTD 앱의 클래식 조건부 액세스 정책: 
> 
> - MTD 파트너와 통신하기 전에 Intune MTD에서 디바이스가 Azure AD에 등록되어 디바이스 ID를 받도록 요구하는 데 사용됩니다. ID가 있어야만 디바이스에서 Intune에 상태를 보고할 수 있습니다.  
> - 다른 클라우드 앱 또는 리소스에는 영향을 주지 않습니다.  
> - MTD 관리를 돕기 위해 만들 수 있는 조건부 액세스 정책과는 다릅니다.
> - 기본적으로 평가에 사용하는 다른 조건부 액세스 정책은 조작하지 마세요.  
> 
> 클래스 조건부 액세스 정책을 보려면 [Azure](https://portal.azure.com/#home)에서 **Azure Active Directory** > **조건부 정책** > **클래식 정책**으로 이동합니다.

## <a name="onboard-devices-by-using-a-configuration-profile"></a>구성 프로필을 사용하여 디바이스 온보딩

Intune과 Microsoft Defender ATP 간에 서비스간 연결을 설정한 후에는 해당 위험 수준에 대한 데이터를 수집하고 사용할 수 있도록 Intune 관리형 디바이스를 ATP에 온보딩합니다. 디바이스를 온보딩하려면 Microsoft Defender ATP용 디바이스 구성 프로필을 사용합니다.  

Microsoft Defender ATP에 대한 연결을 설정하면 Intune은 Microsoft Defender ATP에서 Microsoft Defender ATP 온보딩 구성 패키지를 받습니다. 이 패키지는 디바이스 구성 프로필을 사용하여 디바이스에 배포됩니다. 이 구성 패키지는 [Microsoft Defender ATP 서비스 ](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)와 통신하면서 파일을 검색하고, 위협을 감지하고, Microsoft Defender ATP에 위험을 보고하도록 디바이스를 구성합니다.  

구성 패키지를 사용하여 디바이스를 등록하고 나면 다시 등록할 필요가 없습니다. [그룹 정책 또는 SCCM(System Center Configuration Manager)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)을 사용하여 디바이스를 등록할 수도 있습니다.


### <a name="create-the-device-configuration-profile"></a>디바이스 구성 프로필 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. **이름**과 **설명**을 입력합니다.
4. **플랫폼**에서 **Windows 10 이상**을 선택합니다.
5. **프로필 유형**에서 **Microsoft Defender ATP(Windows 10 Desktop)** 를 선택합니다.
6. 설정을 구성합니다.

   - **Microsoft Defender ATP 클라이언트 구성 패키지 유형**: 프로필에 구성 패키지를 추가하려면 **온보드**를 선택합니다. **등록 취소**를 선택하여 프로필에서 구성 패키지를 제거합니다.
  
     > [!NOTE]  
     > Microsoft Defender ATP와 적절히 연결한 경우 Intune은 구성 프로필을 자동으로 **온보딩**하며, **Microsoft Defender ATP 클라이언트 구성 패키지 유형** 설정을 사용할 수 없게 됩니다.
  
    - **모든 파일에 대해 샘플 공유**: **사용**을 사용하면 샘플을 수집하고 Microsoft Defender ATP와 공유할 수 있습니다. 예를 들어 의심스러운 파일을 발견할 경우 심층 분석을 위해 Microsoft Defender ATP에 제출할 수 있습니다. **구성되지 않음**은 Microsoft Defender ATP에 샘플을 공유하지 않습니다.
    - **원격 분석 보고 주기 단축**: 위험이 큰 디바이스의 경우 이 설정을 **사용**하여 원격 분석을 Microsoft Defender ATP 서비스에 더 자주 보고합니다.

    [System Center Configuration Manager를 사용하여 Windows 10 컴퓨터 온보딩](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm)에는 Microsoft Defender ATP 설정에 대한 자세한 정보가 포함되어 있습니다.

7. **확인**, **만들기**를 차례로 선택하여 변경 내용을 저장하면 프로필이 생성됩니다.
8. Microsoft Defender ATP를 사용하여 평가하려는 디바이스에 [디바이스 구성 프로필을 할당](../configuration/device-profile-assign.md)합니다.  


## <a name="create-and-assign-the-compliance-policy"></a>규정 준수 정책 만들기 및 할당  

규정 준수 정책은 디바이스에 대해 허용되는 것으로 간주되는 위험 수준을 결정합니다.

### <a name="create-the-compliance-policy"></a>준수 정책 만들기  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 준수** > **정책** > **정책 만들기**를 선택합니다.
3. **이름**과 **설명**을 입력합니다.
4. **플랫폼**에서 **Windows 10 이상**을 선택합니다.
5. **설정**에서 **Microsoft Defender ATP**를 선택합니다.
6. **디바이스가 머신 위험 점수나 그 아래에 있어야 함**을 원하는 수준으로 설정합니다. 
   
   위협 수준 분류는 [Microsoft Defender ATP에 의해 결정](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue)됩니다.

   - **지우기**: 이 수준이 가장 안전합니다. 디바이스가 어떠한 위협에도 노출되지 않았으며 회사 리소스에 계속 액세스할 수 있습니다. 어떠한 위협이든 확인되는 디바이스는 비규격으로 평가됩니다. (Microsoft Defender ATP 사용자 값 *Secure*)
   - **낮음**: 낮은 수준의 위협만 있는 디바이스는 규격 디바이스입니다. 보통 또는 높은 위협 수준의 디바이스는 비규격 디바이스입니다.
   - **보통**: 낮음 또는 보통 수준의 위협이 있는 디바이스는 규격 디바이스입니다. 높은 수준의 위협이 검색되는 경우 해당 디바이스는 비규격으로 간주됩니다.
   - **높음**: 이 수준은 최소 보안이며 모든 위협 수준을 허용합니다. 따라서 높음, 보통 또는 낮은 위협 수준의 디바이스가 규격으로 간주됩니다.

6. **확인**, **만들기**를 차례로 선택하여 변경 내용을 저장하고 정책을 만듭니다.  
7. 해당하는 그룹에 [디바이스 준수 정책을 할당](create-compliance-policy.md#assign-the-policy)합니다.



## <a name="create-a-conditional-access-policy"></a>조건부 액세스 정책 만들기  

조건부 액세스 정책은 규정 준수 정책에서 설정한 위협 수준을 초과하는 디바이스에 대해 리소스 액세스를 차단합니다. SharePoint 또는 Exchange Online과 같은 회사 리소스에 대한 디바이스 액세스를 차단할 수 있습니다.  

> [!TIP]  
> 조건부 액세스는 Azure AD(Azure Active Directory) 기술입니다. *Intune*에서 액세스되는 조건부 액세스 노드는 *Azure AD*에서 액세스한 것과 동일한 노드입니다.  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **조건부 액세스** > **새 정책**을 선택합니다.
2. 정책 **이름**을 입력하고 **사용자 및 그룹**을 선택합니다. 포함 또는 제외 옵션을 사용하여 정책에 대한 그룹을 추가하고 **완료**를 선택합니다.
3. **클라우드 앱**을 선택한 다음 보호할 앱을 선택합니다. 예를 들어 **앱 선택**을 선택한 다음 **Office 365 SharePoint Online** 및 **Office 365 Exchange Online**을 선택합니다.

    **완료**를 선택하여 변경 내용을 저장합니다.

4. **조건** > **클라이언트 앱**을 선택하여 앱과 브라우저에 정책을 적용합니다. 예를 들어 **예**를 선택한 다음 **브라우저**와 **모바일 앱 및 데스크톱 클라이언트**를 사용하도록 설정합니다.

    **완료**를 선택하여 변경 내용을 저장합니다.

5. **권한 부여**를 선택하여 디바이스 준수에 따라 조건부 액세스를 적용합니다. 예를 들어 **액세스 권한 부여** > **디바이스가 규격으로 표시되어야 함**을 선택합니다.

    **선택**을 선택하여 변경 내용을 저장합니다.

6. **정책 사용**, **만들기**를 차례로 선택하여 변경 내용을 저장합니다.



## <a name="monitor-device-compliance"></a>디바이스 준수 모니터링  

다음으로, Microsoft Defender ATP 준수 정책이 있는 디바이스의 상태를 모니터링합니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 준수** > **정책 준수**를 선택합니다.
3. 목록에서 Microsoft Defender ATP 정책을 찾아 어떤 디바이스가 규격 또는 비규격인지 확인합니다.

## <a name="view-onboarding-status"></a>온보딩 상태 보기
모든 Intune 관리 Windows 10 디바이스의 온보딩 상태를 보려면 **디바이스 준수** > **Microsoft Defender ATP**로 이동할 수 있습니다. 또한 이 페이지에서 Microsoft Defender ATP에 추가 장치를 온보딩하기 위한 디바이스 구성 프로필 만들기를 시작할 수도 있습니다.

## <a name="next-steps"></a>다음 단계  

[Microsoft Defender ATP 조건부 액세스](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)   
[Microsoft Defender ATP 위험 대시보드](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  
[ATP 취약성 관리에서 보안 작업을 사용하여 디바이스의 문제 해결](atp-manage-vulnerabilities.md)  
[디바이스 준수 정책 시작](device-compliance-get-started.md)  
 
