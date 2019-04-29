---
title: Microsoft Intune에서 보안 기준선 사용 - Azure | Microsoft Docs
description: 모바일 디바이스 관리용 Microsoft Intune을 사용하여 디바이스에서 사용자 및 데이터를 보호하기 위해 권장 그룹 보안 설정을 추가하거나 구성합니다. BitLocker 사용, Windows Defender Advanced Threat Protection 구성, Internet Explorer 제어, Smart Screen 사용, 로컬 보안 정책 설정, 암호 요구, 인터넷 다운로드 차단 등
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b2a5e2bbd6d06cc4ec0cf71ee815229b01040a8
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61490690"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Intune에서 Windows 10 보안 기준선 만들기

보안 기준선은 Windows 10 이상을 실행하는 디바이스에서 사용할 수 있는 미리 보기 기능입니다. 이 기능에는 사용자 및 디바이스를 보호하는 데 도움을 줄 수 있는 Intune에서 지원되는 여러 설정이 포함되어 있습니다. 또한 이러한 설정을 보안 팀에서 권장하는 값으로 자동 설정합니다. 예를 들어, 기준선은 자동으로 BitLocker를 설정하고, 디바이스를 잠금 해제하는 데 자동으로 암호를 요구하며, 기본 인증을 자동으로 비활성화하는 등의 기능을 제공합니다.

이 기능은 다음에 적용됩니다.

- Windows 10 버전 1809 이상​

> [!NOTE]
> 보안 기준선은 미리 보기 상태이지만 기준선이 미리 보기 과정에서 변경될 수 있으므로 프로덕션 환경에서는 프로필을 사용하지 않는 것이 좋습니다. 일반적으로 보안 기준선을 사용할 수 있는 경우 기존 프로필은 최신 지원 프로필로 변환되지 않습니다.

보안 기준선을 사용하는 목적은 Microsoft 365로 작업할 때 엔드투엔드 보안 워크플로를 제공하는 것입니다. 몇 가지 이점은 다음과 같습니다.

- 보안 기준선에는 보안에 영향을 주는 설정에 대한 모범 사례와 권장 사항이 포함됩니다. Intune은 그룹 정책 보안 기준선을 만드는 동일한 Windows 보안 팀과 협력하고 있습니다. 이러한 권장 사항은 지침 및 광범위한 경험을 토대로 작성된 것입니다.
- Intune을 처음 접했고 어디서부터 시작해야 할지 모르겠다면 보안 기준선이 도움이 됩니다. 조직의 리소스와 데이터를 보호하는 데 도움이 된다는 것을 알고 있으면 보안 프로필을 빠르게 만들고 배포할 수 있습니다.
- 현재 그룹 정책을 사용하는 경우 이러한 기준선을 사용하면 관리를 위해 Intune으로 마이그레이션하는 것이 훨씬 쉽습니다. 이러한 기준선은 Intune에 기본적으로 제공되며 최신 관리 환경을 포함합니다.

보안 기준선은 Intune에서 "구성 프로필"을 만듭니다. 이 프로필에는 기준선의 모든 설정이 포함됩니다. 그런 다음, 이 프로필을 사용자, 그룹 및 디바이스에 적용하거나 할당합니다.

프로필이 할당되면 프로필을 모니터링하고 기준선을 모니터링할 수 있습니다. 예를 들어, 어떤 디바이스가 기준선과 일치하는지 또는 기준선과 일치하지 않는지를 알 수 있습니다.

이 문서에서는 보안 기준선을 사용하여 프로필을 만들고, 프로필을 할당하며, 프로필을 모니터링하는 방법을 보여 줍니다.

[Windows 보안 기준선](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)은 이 기능에 대해 자세히 알아볼 수 있는 훌륭한 리소스입니다. [MDM(모바일 디바이스 관리)](https://docs.microsoft.com/windows/client-management/mdm/)은 MDM에 대한 정보 및 Windows 디바이스에서 수행할 수 있는 작업에 대해 알아볼 수 있는 훌륭한 리소스입니다.

## <a name="prerequisites"></a>전제 조건
Intune에서 기준선을 관리하려면 계정에 [정책 및 프로필 관리자](role-based-access-control.md#built-in-roles) 기본 제공 역할이 있어야 합니다.


## <a name="co-managed-devices"></a>공동 관리형 디바이스

Intune 관리 디바이스의 보안 기준선은 Configuration Manager를 사용하는 공동 관리 디바이스와 유사합니다. 공동 관리 디바이스는 System Center Configuration Manager 및 Microsoft Intune을 사용하여 Windows 10 디바이스를 동시에 관리합니다. 이를 통해 Configuration Manager에 대한 기존 투자를 Intune을 활용하도록 클라우드 연결할 수 있습니다. Configuration Manager를 사용하고 클라우드의 이점도 누리고 싶은 경우 [공동 관리 개요](https://docs.microsoft.com/sccm/comanage/overview)는 훌륭한 리소스입니다.

공동 관리 디바이스를 사용할 때는 **디바이스 구성** 워크로드(해당 설정)를 Intune으로 전환해야 합니다. [디바이스 구성 워크로드](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration)는 자세한 정보를 제공합니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com/)에서 **모든 서비스**를 선택하고 > **Intune**을 기준으로 필터링하고 > **Intune**을 선택합니다.
2. **보안 기준선(미리 보기)** 를 선택합니다. 사용 가능한 기준선 목록이 제공됩니다. 더 많은 기준선이 추가되면 여기에 표시됩니다.

    ![Intune에서 현재 사용 가능한 보안 기준선 목록 보기](./media/security-baselines/available-baselines.png)

3. 사용하려는 기준선을 선택하고 > **프로필 만들기**를 선택합니다.
4. **기본**에서 다음 속성을 입력합니다.

    - **이름**: 보안 기준선 프로필의 이름을 입력합니다. 예를 들어 다음과 같이 입력합니다. `pilot Windows 10 MDM baseline - Oct 2018`
    - **설명**: 이 기준선이 하는 일을 설명하는 텍스트를 입력합니다. 설명은 원하는 텍스트를 입력하면 됩니다. 선택 사항이지만 꼭 사용하는 것이 좋습니다.

5. **설정**을 확장합니다. 목록에서 이 보안 기준선의 모든 설정과 설정이 자동으로 어떻게 설정되는지 볼 수 있습니다. 설정 및 해당 값은 권장 사항이며 사용자가 변경할 수 있습니다.

    ![설정을 확장하여 Intune에서 이 보안 기준선의 모든 설정 표시](./media/security-baselines/sample-list-of-settings.png)

    일부 설정을 확장하여 해당 값을 확인합니다. 예를 들어, **Windows Defender**를 확장합니다. 몇 가지 설정과 설정이 어떻게 설정되는지 확인합니다.

    ![Intune에서 Windows Defender 설정 중 일부가 자동으로 설정되는지 확인합니다.](./media/security-baselines/expand-windows-defender.png)

6. 프로필을 **만듭니다**. 
7. **프로필**을 선택합니다. 프로필이 만들어지고 목록에 표시됩니다. 그러나 아직 아무 것도 하지 않습니다. 그런 다음, 프로필을 할당합니다.

## <a name="assign-the-profile"></a>프로필 할당

프로필이 생성되었으면 사용자, 디바이스 및 그룹에 할당할 준비가 된 것입니다. 할당되면 프로필과 해당 설정이 선택한 사용자, 디바이스 및 그룹에 적용됩니다.

1. Intune에서 **보안 기준선** > 기준선 선택 > **프로필**을 선택합니다.
2. 프로필 > **할당**을 선택합니다.

    ![Intune에서 보안 기준선 프로필을 선택하고 할당을 클릭하여 프로필 배포](./media/security-baselines/assignments.png)

3. **포함** 탭에서 이 정책을 적용할 그룹, 사용자 또는 디바이스를 추가합니다.

    > [!TIP]
    > 그룹을 **제외**할 수도 있습니다. 정책을 **모든 사용자**에게 적용하는 경우 관리자 그룹을 제외하는 것이 좋습니다. 어떤 일이 발생하면 사용자와 관리자는 잠금 상태를 원하지 않습니다.

4. 변경 내용을 **저장**합니다.

저장하는 즉시 Intune으로 체크 인될 때 프로필이 디바이스에 푸시됩니다. 따라서 즉시 발생할 수 있습니다.

## <a name="available-security-baselines"></a>사용 가능한 보안 기준선  

다음 보안 기준선은 Intune에서 사용할 수 있습니다.
- **미리 보기: MDM 보안 기준선**
  - 버전: [2018년 10월](security-baseline-settings-windows.md)

## <a name="q--a"></a>Q & A

#### <a name="why-these-settings"></a>이러한 설정은 왜 필요한가요?

Microsoft 보안 팀은 지난 수년 동안 Windows 개발자 및 보안 커뮤니티와 직접 협력하여 이러한 권장 사항을 작성했습니다. 이 기준선의 설정은 가장 관련성 높은 보안 관련 구성 옵션으로 간주됩니다. 새로운 Windows 빌드마다 팀은 새로 릴리스된 기능을 기반으로 해당 권장 사항을 조정합니다.

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>그룹 정책 및 Intune에 대한 Windows 보안 기준선의 권장 사항에 차이점이 있나요? Intune?

동일한 Microsoft 보안 팀이 각 기준선에 대한 설정을 선택하고 구성했습니다. Intune은 Intune 보안 기준선의 모든 관련 설정을 포함합니다. 그룹 정책 기준선에는 온-프레미스 도메인 컨트롤러에만 적용되는 몇 가지 설정이 있습니다. 이러한 설정은 Intune의 권장 사항에서 제외됩니다. 다른 모든 설정은 동일합니다.

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Intune 보안 기준선이 CIS 또는 NSIT를 준수하나요?

엄밀히 말하면, 그렇지 않습니다. Microsoft 보안 팀은 해당 권장 사항을 작성하기 위해 CIS와 같은 조직과 논의합니다. 그러나 “CIS 규격” 및 Microsoft 기준선 간에 일대일 매핑은 없습니다.

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Microsoft의 보안 기준선은 어떤 인증을 포함하나요? 

- Microsoft는 수년 동안 그랬듯이 GPO(그룹 정책) 및 [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10)에 대한 보안 기준선을 지속적으로 게시하고 있습니다. 이러한 기준선은 대부분의 조직에서 사용됩니다. 이러한 기준선의 권장 사항은 Microsoft 보안 팀이 DoD(국방부), NIST(국가 표준 기술 연구소) 등을 비롯한 기업 고객 및 외부 기관과 협력한 결과입니다. Microsoft는 당사의 권장 사항과 기준선을 이러한 조직과 공유합니다. 이러한 조직은 Microsoft의 권장 사항을 충실하게 반영하는 자체적인 권장 사항도 보유하고 있습니다. MDM(모바일 디바이스 관리)이 클라우드 환경으로 지속적으로 성장함에 따라 Microsoft는 이러한 그룹 정책 기준선에 대한 동일한 MDM 권장 사항을 작성했습니다. 이러한 추가 기준선은 Microsoft Intune에 기본 제공되며 기준선을 따르거나 따르지 않는 사용자, 그룹 및 디바이스에 대한 규정 준수 보고서를 포함합니다.

- 많은 고객이 Intune 기준선 권장 사항을 시작점으로 사용하여 IT 및 보안 요구 사항에 맞게 사용자 지정합니다. Microsoft의 Windows 10 RS5 **MDM 보안 기준선**은 릴리스할 첫 번째 기준선입니다. 이 기준선은 고객이 CIS, NIST 및 기타 표준을 기반으로 하고 궁극적으로는 다른 보안 기준선을 가져올 수 있도록 해주는 범용 인프라로 작성되었습니다. 현재 Windows용으로 제공되며 나중에는 iOS 및 Android를 포함할 예정입니다.

- Microsoft Intune에서 Azure AD(Active Directory)를 사용하여 온-프레미스 Active Directory 그룹 정책을 순수 클라우드 솔루션으로 마이그레이션할 계획입니다. 이를 지원하기 위해 하이브리드 AD 및 Azure AD 조인 디바이스용으로 게시된 보조 GPO가 있습니다. 이러한 디바이스는 필요에 따라 클라우드(Intune)의 MDM 설정과 온-프레미스 도메인 컨트롤러의 그룹 정책 설정을 가져올 수 있습니다.

## <a name="next-steps"></a>다음 단계
- Intune에서 지원되는 [Windows 보안 기준선 설정](security-baseline-settings-windows.md)을 확인합니다.  
- 상태를 확인하고 [기준선 및 프로필](security-baselines-monitor.md)을 모니터링합니다.
