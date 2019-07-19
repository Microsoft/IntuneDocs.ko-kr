---
title: Microsoft Intune에서 보안 기준선 사용 - Azure | Microsoft Docs
description: 모바일 디바이스 관리용 Microsoft Intune을 사용하여 디바이스에서 사용자 및 데이터를 보호하기 위해 권장 Windows 보안 설정을 추가하거나 구성합니다. BitLocker 사용, Microsoft Defender Advanced Threat Protection 구성, Internet Explorer 제어, Smart Screen 사용, 로컬 보안 정책 설정, 암호 요구, 인터넷 다운로드 차단 등
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 16586ece687b5d50ea89b28bfd524f50e65ceb46
ms.sourcegitcommit: 5ce8726278004bbf072149a9c924091bb0654b7c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67851474"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>Intune에서 보안 기준을 사용하여 Windows 10 디바이스 구성

Intune의 보안 기준을 사용하면 사용자와 디바이스를 안전하게 보호할 수 있습니다. 보안 기준은 미리 구성된 Windows 설정 그룹으로, 관련 보안 팀에서 권장하는 알려진 그룹의 설정 및 기본값을 적용하는 데 도움이 됩니다. Intune에서 보안 기준 프로필을 만들 때는 ‘디바이스 구성’ 프로필을 만듭니다. 

이 기능은 다음에 적용됩니다.

- Windows 10 버전 1809 이상​

Intune에서 보안 기준을 사용자 또는 디바이스의 그룹에 배포하면 설정이 Windows 10 이상을 실행하는 디바이스에 적용됩니다. 예를 들어 ‘MDM 보안 기준’은 휴대용 디바이스에 대해 자동으로 BitLocker를 사용하도록 설정하고, 디바이스를 잠금 해제하는 데 자동으로 암호를 요구하며, 기본 인증을 자동으로 사용하지 않도록 설정하는 등의 기능을 제공합니다.  기본값이 환경에 맞지 않으면 기준을 사용자 지정하여 필요한 설정을 적용합니다.  

다른 기준 형식에서 같은 설정을 포함할 수 있지만 해당 설정에 다른 기본값을 사용합니다. 사용하도록 선택한 기준의 기본값을 이해하고 조직의 요구 사항에 맞게 각 기준을 수정하는 것이 중요합니다.  

> [!NOTE]
> 보안 기준의 미리 보기 버전을 프로덕션 환경에서 사용하지 않는 것이 좋습니다. 미리 보기 기준의 설정은 미리 보기 과정에서 변경될 수 있습니다. 

보안 기준을 사용하는 목적은 Microsoft 365로 작업할 때 엔드투엔드 보안 워크플로를 제공하는 것입니다. 몇 가지 이점은 다음과 같습니다.

- 보안 기준선에는 보안에 영향을 주는 설정에 대한 모범 사례와 권장 사항이 포함됩니다. Intune은 그룹 정책 보안 기준선을 만드는 동일한 Windows 보안 팀과 협력하고 있습니다. 이러한 권장 사항은 지침 및 광범위한 경험을 토대로 작성된 것입니다.
- Intune을 처음 사용하고 어디서부터 시작해야 할지 모르는 경우, 보안 기준이 도움이 됩니다. 조직의 리소스와 데이터를 보호하는 데 도움이 된다는 것을 알고 있으면 보안 프로필을 빠르게 만들고 배포할 수 있습니다.
- 현재 그룹 정책을 사용하는 경우 이러한 기준선을 사용하면 관리를 위해 Intune으로 마이그레이션하는 것이 훨씬 쉽습니다. 이러한 기준선은 Intune에 기본적으로 제공되며 최신 관리 환경을 포함합니다.



[Windows 보안 기준선](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)은 이 기능에 대해 자세히 알아볼 수 있는 훌륭한 리소스입니다. [MDM(모바일 디바이스 관리)](https://docs.microsoft.com/windows/client-management/mdm/)은 MDM에 대한 정보 및 Windows 디바이스에서 수행할 수 있는 작업에 대해 알아볼 수 있는 훌륭한 리소스입니다.

## <a name="security-baseline-versions-and-instances"></a>보안 기준 버전 및 인스턴스
때때로 기준의 새 업데이트가 제공될 수 있습니다. 기준의 새 버전 인스턴스 각각에서는 설정을 추가 또는 제거하거나 다른 변경 내용을 도입할 수 있습니다. 예를 들어 새 버전의 Windows 10에서 새 Windows 10 설정이 제공되는 것처럼 MDM 보안 기준에서는 최신 설정을 포함하는 새 버전 인스턴스를 받을 수 있습니다.  

Intune 콘솔에서 사용할 수 있는 보안 기준과 관련 정보를 확인할 수 있습니다. 사용 가능한 정보는 해당 기준 유형을 사용하는 프로필 수, 사용 가능한 기준 유형의 다른 인스턴스 수, 최신 인스턴스가 제공되거나 게시된 시기 등입니다.  다음 예제에서는 널리 사용 되는 MDM 보안 기준의 타일을 보여 줍니다.  

![기준 타일](./media/security-baselines/baseline-tile.png)

사용하는 기준 버전 정보를 보려면 기준을 선택한 다음 **버전**을 선택합니다. Intune에 프로필에서 사용 중인 버전에 대한 정보가 표시됩니다. 버전 창에서 단일 버전을 선택하여 해당 버전을 사용하는 프로필에 대해 자세히 확인할 수 있습니다. 또한 두 가지 버전을 선택하고 **기준 비교**를 선택하여 차이점을 자세히 설명하는 CSV 파일을 다운로드할 수도 있습니다.  

![기준 비교](./media/security-baselines/compare-baselines.png)

보안 기준 ‘프로필’을 만들면 프로필에서 최근에 릴리스된 보안 기준 인스턴스를 자동으로 사용합니다.   미리 보기 버전을 사용하여 만든 기준을 포함하여 이전 기준 버전 인스턴스를 사용하여 이전에 만든 프로필을 계속 사용하거나 편집할 수 있습니다. 

보안 기준 프로필은 사용 중인 기준의 [버전 변경](#change-the-baseline-instance-for-a-profile)을 지원합니다. 즉, 새 버전이 출시되는 경우 활용하기 위해 새 기준 프로필을 만들 필요가 없습니다. 대신 준비되면 기준 프로필을 선택한 다음 기본 제공 옵션을 사용하여 해당 프로필의 인스턴스 버전을 변경하면 됩니다.  

## <a name="available-security-baselines"></a>사용 가능한 보안 기준선 

다음 보안 기준 인스턴스는 Intune에서 사용할 수 있습니다. 링크를 사용하여 각 기준의 최근 인스턴스에 대한 설정을 확인하세요. 

- **MDM 보안 기준**
  - [2019년 봄(19H1) MDM 보안 기준](security-baseline-settings-mdm.md)
  - [미리 보기: 2018년 10월 MDM 보안 기준](security-baseline-settings-mdm-archive.md)

- **Microsoft Defender ATP 기준**  
  ‘(이 기준을 사용하려면 환경이 [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) 사용에 대한 필수 조건을 충족해야 합니다.)’ 
  - [미리 보기: Microsoft Defender ATP 기준](security-baseline-settings-defender-atp.md)  

이전에 미리 보기 템플릿을 기반으로 만든 프로필은 새 프로필을 만드는 데 해당 미리 보기 템플릿을 사용할 수 없더라도 계속 사용하거나 편집할 수 있습니다. 

## <a name="prerequisites"></a>전제 조건
- Intune에서 기준선을 관리하려면 계정에 [정책 및 프로필 관리자](role-based-access-control.md#built-in-roles) 기본 제공 역할이 있어야 합니다.

- 일부 기준을 사용하려면 Microsoft Defender ATP와 같은 추가 서비스에 대한 활성 구독이 있어야 할 수 있습니다.  

## <a name="co-managed-devices"></a>공동 관리형 디바이스

Intune 관리 디바이스의 보안 기준선은 Configuration Manager를 사용하는 공동 관리 디바이스와 유사합니다. 공동 관리 디바이스는 System Center Configuration Manager 및 Microsoft Intune을 사용하여 Windows 10 디바이스를 동시에 관리합니다. 이를 통해 Configuration Manager에 대한 기존 투자를 Intune을 활용하도록 클라우드 연결할 수 있습니다. Configuration Manager를 사용하고 클라우드의 이점도 누리고 싶은 경우 [공동 관리 개요](https://docs.microsoft.com/sccm/comanage/overview)는 훌륭한 리소스입니다.

공동 관리 디바이스를 사용할 때는 **디바이스 구성** 워크로드(해당 설정)를 Intune으로 전환해야 합니다. [디바이스 구성 워크로드](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration)는 자세한 정보를 제공합니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스 보안** > **보안 기준**을 선택하여 사용 가능한 기준 목록을 표시합니다.


    ![구성할 보안 기준을 선택](./media/security-baselines/available-baselines.png)

2. 사용하려는 기준을 선택한 후 **프로필 만들기**를 선택합니다.  

3. **기본 사항** 탭에서 다음 속성을 지정합니다.

    - **이름**: 보안 기준선 프로필의 이름을 입력합니다. 예를 들어 ‘Defender ATP용 표준 프로필’을 입력합니다. 

    - **설명**: 이 기준선이 하는 일을 설명하는 텍스트를 입력합니다. 설명은 원하는 텍스트를 입력하면 됩니다. 선택 사항이지만 사용하는 것이 좋습니다.  

   **다음**을 선택하여 다음 탭으로 이동합니다. 새 탭으로 이동한 후 탭 이름을 선택하여 이전에 보던 탭으로 돌아갈 수 있습니다.  

4. 구성 설정 탭에서 선택한 기준에서 사용할 수 있는 **설정**의 그룹을 확인합니다. 그룹을 확장하여 해당 그룹의 설정 및 기준의 설정에 대한 기본값을 확인할 수 있습니다. 특정 설정을 찾으려면
   - 그룹을 선택하여 확장하고 사용 가능한 설정을 검토합니다.  
   - ‘검색’ 창에 키워드를 지정하여 검색 기준을 포함하는 그룹만 표시하도록 보기를 필터링합니다.   
 
   기준에서 각 설정에는 해당 기준 버전의 기본값 구성이 있습니다. 비즈니스 요구 사항에 맞게 기본값 설정을 다시 구성합니다. 다른 기준에 같은 설정이 포함될 수 있으며 기준의 의도에 따라 설정의 기본값이 다릅니다. 

    ![그룹을 확장하여 해당 그룹에 대한 설정 보기](./media/security-baselines/sample-list-of-settings.png)

5. **범위 태그** 탭에서 **범위 태그 선택**을 선택하여 *태그 선택* 창을 열고 프로필에 범위 태그를 할당합니다. 

6. **할당** 탭에서 **포함할 그룹 선택**을 선택한 다음 하나 이상의 그룹에 기준을 할당합니다. **제외할 그룹 선택**을 사용하여 할당을 미세 조정합니다.  

   ![프로필 할당](./media/security-baselines/assignments.png)
  
7. 기준을 배포할 준비가 된 경우 **검토 + 만들기** 탭으로 이동하여 기준에 대한 세부 정보를 검토합니다. **만들기**를 선택하여 프로필을 저장하고 배포합니다.  

   프로필을 만들면 프로필은 바로 할당된 그룹에 푸시되고 즉시 적용할 수 없습니다.

   > [!TIP]  
   > 처음에 프로필을 그룹에 할당하지 않고 저장하는 경우 나중에 프로필을 편집하여 할당할 수 있습니다.  

   ![기준 검토](./media/security-baselines/review.png) 

  
8. 프로필을 만든 후 **디바이스 보안** > **보안 기준**으로 이동하여 편집하고, 구성한 기준 유형을 선택한 다음 **프로필**을 선택합니다.  사용 가능한 프로필 목록에서 프로필을 선택한 다음 **속성**을 선택합니다. 모든 사용 가능한 구성 탭의 설정을 편집하고 **검토 + 저장**을 선택하여 변경 내용을 커밋할 수 있습니다.  

## <a name="change-the-baseline-instance-for-a-profile"></a>프로필의 기준 인스턴스 변경
기준 프로필은 프로필에서 사용하는 기준 인스턴스 변경을 지원합니다. 이전 인스턴스 또는 더 일반적으로 동일한 기준의 새 인스턴스를 선택할 수 있습니다.  Defender ATP용 기준 사용에서 MDM 보안 기준 사용으로 프로필을 변경하는 것과 같은 다른 두 기준 간에 변경할 수는 없습니다. 

기준 버전 변경을 구성할 때 관련된 두 기준 버전 간의 변경 사항을 나열하는 CSV 파일을 다운로드할 수 있습니다. 원래 기준 버전의 모든 사용자 지정을 유지하고 새 버전에 적용할 수도 있고 선택한 새 기준 버전에 있는 모든 기본값을 구현할 수도 있습니다. 

저장 시 변환이 완료되면 기준이 할당된 그룹에 즉시 다시 배포됩니다.  

**변환 중**:
- 사용 중이던 원래 버전에 없는 새 설정은 추가되고 기본값을 사용하도록 설정됩니다.  

- 선택하는 새 기준 버전에 없는 설정은 제거되고 이 보안 기준 프로필에서 더 이상 적용되지 않습니다.  

  설정이 기준 프로필에서 더 이상 관리되지 않은 경우 해당 설정은 디바이스에서 다시 설정되지 않습니다. 대신, 디바이스의 설정은 다른 프로세스에서 설정을 관리하여 변경할 때까지 마지막 구성으로 유지됩니다. 설정 관리를 중지한 후 설정을 변경할 수 있는 예에는 디바이스에서 만든 다른 기준 프로필, 그룹 정책 설정 또는 수동 구성을 포함하는 것이 포함됩니다. 

### <a name="to-change-the-instance-for-a-baseline"></a>기준의 인스턴스를 변경하려면  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인한 다음 **디바이스 보안** > **보안 기준**을 선택하고 변경할 프로필이 있는 기준 유형의 제목을 선택합니다.  

2. 다음으로 **프로필**을 선택한 다음 편집할 프로필의 확인란을 선택하고 **버전 변경**을 선택합니다.  

   ![기준 선택](./media/security-baselines/select-baseline.png)  

3. **버전 변경** 창에서 **Select a security baseline to update to**(업데이트할 보안 기준 선택) 드롭다운을 사용하여 사용할 버전 인스턴스를 선택합니다.  

   ![버전 선택](./media/security-baselines/select-instance.png)  
   
4. **업데이트 검토**를 선택하여 프로필 현재 인스턴스 버전과 선택한 새 버전 간의 차이를 표시하는 CSV 파일을 다운로드합니다. 이 파일을 검토하여 추가 또는 제거된 설정과 업데이트된 프로필에서 이러한 설정의 기본값이 무엇인지 파악합니다.  

   준비가 되면 다음 단계를 계속합니다.  

5. **Select a method to update the profile**(프로필을 업데이트할 방법 선택)에서 다음 두 가지 옵션 중 하나를 선택합니다. 
   - **Accept baseline changes but keep my existing setting customizations**(기준 변경 사항을 적용하지만 기존 설정 사용자 지정 유지) - 이 옵션은 기준 프로필의 사용자 지정 내용을 유지하고 사용하도록 선택한 새 버전에 적용합니다.
   - **Accept baseline changes and discard existing setting customizations**(기준 변경 사항을 적용하고 기존 설정 사용자 지정 삭제) - 이 옵션은 원래 프로필을 완전히 덮어씁니다. 업데이트된 프로필에서는 모든 설정에 기본값을 사용합니다.  

6. **제출**을 선택합니다. 프로필이 선택한 기준 버전으로 업데이트되고 변환이 완료된 후 기준이 할당된 그룹에 즉시 다시 배포됩니다.

## <a name="remove-a-security-baseline-assignment"></a>보안 기준 할당 제거
보안 기준 설정이 디바이스에 더 이상 적용되지 않거나 기준의 설정이 ‘구성되지 않음’으로 설정되는 경우 디바이스에서 이러한 설정은 관리 전 구성으로 되돌려집니다.  대신 디바이스에서 이전에 관리되는 설정이 다른 프로세스에서 디바이스의 해당 설정을 업데이트하기 전에 받은 마지막 구성을 유지합니다.  

디바이스에서 나중에 설정을 변경할 수 있는 다른 프로세스에는 다르거나 새로운 보안 기준, 디바이스 구성 프로필, 그룹 정책 구성 또는 디바이스 설정 수동 편집 등이 있습니다.  





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

- Microsoft Intune에서 Azure AD(Active Directory)를 사용하여 온-프레미스 Active Directory 그룹 정책을 순수 클라우드 솔루션으로 마이그레이션할 계획입니다. 도움을 주기 위해 [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10)(보안 준수 툴킷)에는 하이브리드 AD 및 Azure AD 조인 디바이스를 관리하는 데 도움이 되는 그룹 정책 템플릿이 포함되어 있습니다. 이러한 디바이스는 필요에 따라 클라우드(Intune)의 MDM 설정과 온-프레미스 도메인 컨트롤러의 그룹 정책 설정을 가져올 수 있습니다.

## <a name="next-steps"></a>다음 단계
- 사용할 수 있는 기준의 최신 버전에서 설정을 확인합니다.  
  - [MDM 보안 기준](security-baseline-settings-mdm.md)  
  - [Microsoft Defender ATP 기준](security-baseline-settings-defender-atp.md)  

- 상태를 확인하고 [기준선 및 프로필](security-baselines-monitor.md)을 모니터링합니다.
