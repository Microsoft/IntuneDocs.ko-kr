---
title: Microsoft Intune에서 Windows Defender ATP 사용 - Azure | Microsoft Docs
description: Intune 및 Windows Defender 보안 센터(ATP 포털)에서 ATP 켜기 등 엔드투엔드 시나리오에서 Windows Defender Security Center (ATP portal)를 사용하도록 설정하고, ATP 구성 프로필을 사용하여 디바이스를 등록하고, Intune 디바이스 준수 정책을 만들고, Azure AD 조건부 액세스 정책을 만들고, 디바이스 준수를 모니터링하는 방법을 확인합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 186ba1a8813e84b89a23c8aabb3a4ef0bd392da4
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67045913"
---
# <a name="enforce-compliance-for-windows-defender-atp-with-conditional-access-in-intune"></a>Intune에서 조건부 액세스로 Windows Defender ATP에 대한 규정 준수 적용

Windows Defender ATP(Advanced Threat Protection) 및 Microsoft Intune은 함께 작동하여 보안 위반을 방지하고 조직 내에서 위반 영향을 제한합니다.

이 기능은 다음에 적용됩니다. Windows 10 디바이스

예를 들어 누군가가 포함된 악성 코드가 있는 Word 첨부 파일을 조직 내의 사용자에게 전송합니다. 사용자가 첨부 파일을 열고 콘텐츠를 활성화합니다. 상승된 권한 공격이 시작되고, 원격 컴퓨터의 공격자가 공격 대상 디바이스에 대한 관리자 권한을 갖게 됩니다. 그런 다음, 공격자가 사용자의 다른 디바이스에 원격으로 액세스합니다.

이 보안 위반은 전체 조직에 영향을 미칠 수 있습니다.

Windows Defender ATP는 이 시나리오와 같은 보안 이벤트를 해결할 수 있습니다. Windows Defender 보안 센터(ATP 콘솔)는 디바이스를 “높은 위험”으로 보고하고 의심스러운 활동의 자세한 보고서를 포함합니다. 이 예제에서 Windows Defender ATP는 디바이스에서 비정상적인 코드가 실행되었으며, 프로세스 권한 에스컬레이션이 발생하고 악성 코드가 삽입되고 의심스러운 원격 셸이 실행되었음을 감지합니다. 그런 다음, Windows Defender ATP는 위협을 완화하는 옵션을 제공합니다.

Intune을 사용하여 허용되는 위험 수준을 결정하는 준수 정책을 만들 수 있습니다. 디바이스가 이 위험을 초과하면 비규격 상태가 됩니다. Azure AD(Active Directory) 조건부 액세스와 결합할 경우 회사 리소스에 대한 사용자 액세스가 차단됩니다.

이 문서에서는 다음 방법을 보여 줍니다.

- ATP에서 Intune을 사용하도록 설정하고, Intune에서 ATP를 사용하도록 설정합니다. 이러한 작업은 Intune과 Windows Defender ATP 간에 서비스-서비스 연결을 만듭니다. 이 연결을 통해 Windows Defender ATP에서 Intune 디바이스에 대한 컴퓨터 위험을 작성할 수 있습니다.
- Intune에서 준수 정책을 만듭니다.
- 위협 수준에 따라 디바이스의 Azure AD(Active Directory)에서 조건부 액세스를 사용하도록 설정합니다.

## <a name="prerequisites"></a>전제 조건

Intune에서 ATP를 사용하려면 다음을 구성했으며 사용할 준비가 되었는지 확인합니다.

- Enterprise Mobility + Security E3 및 Windows E5(또는 Microsoft 365 Enterprise E5)에 대한 라이선스가 부여된 테넌트
- Azure AD에 연결된 [Intune 관리](windows-enroll.md) Windows 10 디바이스가 포함된 Microsoft Intune 환경
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) 및 Windows Defender 보안 센터(ATP 포털)에 대한 액세스 권한

## <a name="enable-windows-defender-atp-in-intune"></a>Intune에서 Windows Defender ATP 사용

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **디바이스 준수** > **Windows Defender ATP** > **Windows Defender 보안 센터 열기**를 차례로 선택합니다.

    ![Windows Defender 보안 센터 열기 선택](./media/atp-device-compliance-open-windows-defender.png)

4. **Windows Defender 보안 센터**에서 다음을 수행합니다.
    1. **설정** > **고급 기능**을 선택합니다.
    2. **Microsoft Intune 연결**에서 **켜기**를 선택합니다.

        ![Intune에 대한 연결을 사용하도록 설정](./media/atp-security-center-intune-toggle.png)

    3. **기본 설정 저장**을 선택합니다.

5. Intune, **디바이스 준수** > **Windows Defender ATP**로 돌아갑니다. **Windows 디바이스 버전 10.0.15063 이상을 Windows Defender ATP에 연결**을 **켜기**로 설정합니다.
6. **저장**을 선택합니다.

일반적으로 이 작업은 한 번 수행합니다. 따라서 Intune 리소스에서 이미 ATP를 사용하도록 설정한 경우에는 다시 이 작업을 수행하지 않아도 됩니다.

## <a name="onboard-devices-using-a-configuration-profile"></a>구성 프로필을 사용하여 디바이스 등록

최종 사용자가 Intune에 등록하면 구성 프로필을 사용하여 다른 설정을 디바이스에 푸시할 수 있습니다. 이는 Windows Defender ATP에도 적용됩니다.

Windows Defender에는 [Windows Defender ATP 서비스](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)와 통신하여 파일을 검색하고, 위협을 탐지하며, Windows Defender ATP에 위험을 보고하는 등록 구성 패키지가 포함되어 있습니다.

등록하면 Intune에서 Windows Defender ATP를 통해 자동 생성된 구성 패키지를 가져옵니다. 프로필이 디바이스에 푸시되거나 배포되면 이 구성 패키지도 디바이스에 푸시됩니다. 이렇게 하면 Windows Defender ATP에서 디바이스에 대한 위협을 모니터링할 수 있습니다.

구성 패키지를 사용하여 디바이스를 등록하고 나면 다시 등록할 필요가 없습니다. [그룹 정책 또는 SCCM(System Center Configuration Manager)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection)을 사용하여 디바이스를 등록할 수도 있습니다.

### <a name="create-the-configuration-profile"></a>구성 프로필 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. **이름**과 **설명**을 입력합니다.
4. **플랫폼**에서 **Windows 10 이상**을 선택합니다.
5. **프로필 유형**에서 **Windows Defender ATP(Windows 10 Desktop)** 를 선택합니다.
6. 설정을 구성합니다.

  - **Windows Defender ATP 클라이언트 구성 패키지 유형**: 프로필에 구성 패키지를 추가하려면 **온보드**를 선택합니다. **등록 취소**를 선택하여 프로필에서 구성 패키지를 제거합니다.
  
    > [!NOTE] 
    > Windows Defender ATP와 적절히 연결한 경우 Intune은 구성 프로필을 자동으로 **온보드**하며, **Windows Defender ATP 클라이언트 구성 패키지 유형** 설정을 사용할 수 없게 됩니다.
  
  - **모든 파일에 대해 샘플 공유**: **사용**을 사용하면 샘플을 수집하고 Windows Defender ATP와 공유할 수 있습니다. 예를 들어 의심스러운 파일을 발견할 경우 심층 분석을 위해 Windows Defender ATP에 제출할 수 있습니다. **구성되지 않음**은 Windows Defender ATP에 샘플을 공유하지 않습니다.
  - **원격 분석 보고 주기 단축**: 위험이 큰 디바이스의 경우 이 설정을 **사용**하여 원격 분석을 Windows Defender ATP 서비스에 더 자주 보고합니다.

    [System Center Configuration Manager를 사용하여 Windows 10 컴퓨터 등록](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection)에는 Windows Defender ATP 설정에 대한 자세한 정보가 포함되어 있습니다.

7. **확인**, **만들기**를 차례로 선택하여 변경 내용을 저장하면 프로필이 생성됩니다.

## <a name="create-the-compliance-policy"></a>준수 정책 만들기
준수 정책은 디바이스에서 허용되는 위험 수준을 결정합니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 준수** > **정책** > **정책 만들기**를 선택합니다.
3. **이름**과 **설명**을 입력합니다.
4. **플랫폼**에서 **Windows 10 이상**을 선택합니다.
5. **Windows Defender ATP** 설정에서 **디바이스가 머신 위험 점수나 그 아래에 있어야 함**을 기본 설정 수준으로 설정합니다. 위협 수준 분류는 [Windows Defender ATP에 의해 결정](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/alerts-queue-windows-defender-advanced-threat-protection)됩니다.

   - **지우기**: 이 수준이 가장 안전합니다. 디바이스가 어떠한 위협에도 노출되지 않았으며 회사 리소스에 계속 액세스할 수 있습니다. 어떠한 위협이든 확인되는 디바이스는 비규격으로 평가됩니다. (Windows Defender ATP 사용자 값 *Secure*.)
   - **낮음**: 낮은 수준의 위협만 있는 디바이스는 규격 디바이스입니다. 보통 또는 높은 위협 수준의 디바이스는 비규격 디바이스입니다.
   - **보통**: 낮음 또는 보통 수준의 위협이 있는 디바이스는 규격 디바이스입니다. 높은 수준의 위협이 검색되는 경우 해당 디바이스는 비규격으로 간주됩니다.
   - **높음**: 이 수준은 최소 보안이며 모든 위협 수준을 허용합니다. 따라서 높음, 보통 또는 낮은 위협 수준의 디바이스가 규격으로 간주됩니다.

6. **확인**, **만들기**를 차례로 선택하여 변경 내용을 저장하고 정책을 만듭니다.

## <a name="assign-the-policy"></a>정책 할당

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 준수** > **정책** &gt; Windows Defender ATP 준수 정책을 선택합니다.
3. **할당**을 선택합니다.
4. Azure AD 그룹을 포함하거나 제외하여 정책을 할당합니다.
5. 그룹에 정책을 배포하려면 **저장**을 선택합니다. 정책의 대상이 되는 사용자 디바이스의 준수 여부가 평가됩니다.

## <a name="create-a-conditional-access-policy"></a>조건부 액세스 정책 만들기
비규격 디바이스인 ‘경우’ 조건부 액세스 정책에 따라 리소스 액세스가 차단됩니다.  따라서 디바이스가 위협 수준을 초과하는 경우 SharePoint 또는 Exchange Online과 같은 회사 리소스에 대한 액세스를 차단할 수 있습니다.  

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

[조건부 액세스란?](conditional-access.md)은 좋은 리소스입니다.

## <a name="monitor-device-compliance"></a>디바이스 준수 모니터링
다음으로, Windows Defender ATP 준수 정책이 있는 디바이스의 상태를 모니터링합니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 준수** > **정책 준수**를 선택합니다.
3. 목록에서 Windows Defender ATP 정책을 찾아 어떤 디바이스가 규격 또는 비규격인지 확인합니다.

## <a name="more-good-stuff"></a>기타 유용한 자료
[Windows Defender ATP 조건부 액세스](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Windows Defender ATP 위험 대시보드](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[디바이스 준수 정책 시작](device-compliance-get-started.md)  
[Azure AD의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
