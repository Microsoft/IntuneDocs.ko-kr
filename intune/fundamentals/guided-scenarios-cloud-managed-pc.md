---
title: 단계별 시나리오 - 클라우드 관리 Modern Desktop
titleSuffix: Microsoft Intune
description: Microsoft 365 장치 관리 포털에서 기본 Modern Desktop을 설정 및 구성하는 단계별 시나리오에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f78f3696827ebd50084f0e4b012c5f94427eeb35
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164572"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>단계별 시나리오 - 클라우드 관리 Modern Desktop

Modern Desktop은 정보 근로자를 위한 최신 생산성 플랫폼입니다. Office 365 ProPlus 및 Windows 10은 Windows 10 및 Microsoft Defender Advanced Threat Protection의 최신 보안 기준과 함께 Modern Desktop의 핵심 구성 요소입니다. 

클라우드에서 Modern Desktop을 관리하면 인터넷 전체 원격 작업을 추가로 활용할 수 있습니다. 클라우드 관리는 기본 제공 Windows 모바일 장치 관리 정책을 활용하고 로컬 Active Directory 그룹 정책에 대한 종속성을 제거합니다. 

자체 조직에서 클라우드 관리 Modern Desktop을 평가하려는 경우 이 단계별 시나리오는 기본 배포에 필요한 모든 구성을 미리 정의합니다. 이 단계별 시나리오에서는 Intune 장치 관리 기능을 사용해 볼 수 있는 보안 환경을 만듭니다. 

## <a name="prerequisites"></a>전제 조건
- [MDM 기관을 Intune으로 설정](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) - MDM(모바일 장치 관리) 기관 설정에 따라 디바이스를 관리하는 방법이 결정됩니다. IT 관리자가 MDM 기관을 설정해야 사용자가 관리를 위해 디바이스를 등록할 수 있습니다.
- M365 E3 이상(또는 최상의 보안을 위해 M365 E5)
- Windows 10 1903 디바이스(최상의 최종 사용자 환경을 위해 Windows Autopilot에 등록됨)
- 이 단계별 시나리오를 완료하는 데 필요한 Intune 관리자 권한:
  - 디바이스 구성 읽기, 만들기, 삭제, 할당 및 업데이트
  - 등록 프로그램 디바이스 읽기, 프로필 읽기, 프로필 만들기, 프로필 할당, 프로필 삭제
  - 모바일 앱 읽기, 만들기, 삭제, 할당 및 업데이트
  - 조직 읽기 및 업데이트
  - 보안 기준 읽기, 만들기, 삭제, 할당 및 업데이트
  - 정책 집합 읽기, 만들기, 삭제, 할당 및 업데이트

## <a name="step-1---introduction"></a>1단계 - 소개

이 단계별 시나리오를 사용하여 테스트 사용자를 설정하고, Intune에 디바이스를 등록하고, Windows 10 및 Office ProPlus뿐만 아니라 Intune 권장 설정으로 디바이스를 배포합니다. [Intune에서 이 보호를 사용하도록 설정](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune)을 선택하면 Microsoft Defender Advanced Threat Protection을 사용하도록 디바이스가 구성됩니다. 설정하는 사용자와 등록하는 디바이스는 새 보안 그룹에 추가되고 보안 및 생산성에 대한 권장 설정으로 구성됩니다. 

### <a name="what-you-will-need-to-continue"></a>계속해야 하는 작업

이 단계별 시나리오에서 테스트 디바이스 및 테스트 사용자를 제공해야 합니다. 다음 작업을 완료해야 합니다.
- Azure Active Directory에서 테스트 사용자 계정을 설정합니다.
- Windows 10 버전 1903 이상을 실행하는 테스트 디바이스를 만듭니다.
- (선택 사항) [Windows Autopilot을 사용하여 테스트 디바이스를 등록합니다](~/enrollment/enrollment-autopilot.md#add-devices).
- (선택 사항) [조직의 Azure Active Directory 로그인 페이지에 브랜딩](https://go.microsoft.com/fwlink/?linkid=2102455)을 사용하도록 설정합니다.

## <a name="step-2---user"></a>2단계 - 사용자

디바이스에서 설정할 사용자를 선택합니다. 이 사용자는 디바이스의 기본 사용자가 됩니다.

이 구성에 사용자 또는 디바이스를 더 추가하려면 마법사에서 생성된 AAD 보안 그룹에 사용자 및 디바이스를 추가하면 됩니다. 다른 단계별 시나리오와 달리, 구성을 사용자 지정할 수 없으므로 마법사를 두 번 이상 실행할 필요가 없습니다. 생성된 AAD 그룹에 사용자 및 디바이스를 더 추가하면 됩니다. 마법사를 완료한 후에는 권장되는 정책을 배포하여 생성된 그룹을 볼 수 있습니다. 

## <a name="step-3---device"></a>3단계 - 디바이스

디바이스에서 Windows 10 버전 1903 이상을 실행하고 있는지 확인합니다.  기본 사용자가 디바이스를 받을 때 디바이스를 설정해야 합니다. 사용자가 사용할 수 있는 두 가지 설정 옵션이 있습니다. 

### <a name="option-a--windows-autopilot"></a>옵션 A – Windows Autopilot
Windows Autopilot은 사용자가 IT 지원 없이 기본적으로 사용할 수 있도록 새 디바이스의 구성을 자동화합니다. 디바이스가 Windows Autopilot에 이미 등록된 경우 일련 번호로 디바이스를 선택합니다. Windows Autopilot 사용에 대한 자세한 내용은 [Windows Autopilot에 디바이스 등록(선택 사항)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional)을 참조하세요.

### <a name="option-b--manual-device-enrollment"></a>옵션 B - 수동 디바이스 등록
사용자가 모바일 장치 관리에서 수동으로 새 디바이스를 설정하고 등록합니다. 이 시나리오를 완료한 후 디바이스를 다시 설정하고 기본 사용자에게 Windows 디바이스의 등록 지침을 제공합니다. 자세한 내용은 [첫 번째 실행 경험에서 Azure AD에 Windows 10 디바이스 조인](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device)을 참조하세요.

## <a name="step-4---review--create"></a>4단계 - 검토 + 만들기

마지막 단계에서는 구성한 설정의 요약을 검토할 수 있습니다. 선택 항목을 검토한 후에는 **배포**를 클릭하여 단계별 시나리오를 완료합니다. 단계별 시나리오를 완료한 후에는 리소스 테이블이 표시됩니다. 나중에 이 리소스를 편집할 수 있지만 요약 보기를 종료하면 테이블이 저장되지 않습니다.

> [!IMPORTANT]
> 단계별 시나리오가 완료되면 요약이 표시됩니다. 나중에 요약에 나열된 리소스를 수정할 수 있지만 이 리소스를 표시하는 테이블은 저장되지 않습니다.

### <a name="verification"></a>확인
1. 선택된 항목에 MDM 사용자 범위가 할당되었는지 확인합니다.
    - [MDM 사용자 범위](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment)가 다음과 같은지 확인합니다.
        - **Microsoft Intune** 앱의 경우 **모두**로 설정하거나,
        - **일부**로 설정합니다. 또한 이 단계별 시나리오에서 생성된 사용자 그룹을 추가합니다.
2. 선택한 사용자가 Azure Active Directory에 디바이스를 조인할 수 있는지 확인합니다.
    - AAD 조인이 다음과 같은지 확인합니다.
        - **모두**로 설정하거나,
        - **일부**로 설정합니다. 또한 이 단계별 시나리오에서 생성된 사용자 그룹을 추가합니다.
3. 디바이스에서 해당하는 단계에 따라 다음을 기준으로 디바이스를 Azure AD에 조인합니다.
    - Autopilot 사용: 자세한 내용은 [Windows Autopilot 사용자 기반 모드](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)를 참조하세요.
    - Autopilot 사용 안 함: 자세한 내용은 [첫 번째 실행 경험에서 Azure AD에 Windows 10 디바이스 조인](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device)을 참조하세요.

### <a name="what-happens-when-i-click-deploy"></a>[배포]를 클릭하면 어떻게 되나요?
사용자 및 디바이스가 새 보안 그룹에 추가됩니다. 또한 회사 또는 학교에서 보안 및 생산성을 위해 Intune 권장 설정으로 구성됩니다. 사용자가 디바이스를 Azure AD에 조인한 후 추가 앱 및 설정이 디바이스에 추가됩니다. 이 추가 구성에 대한 자세한 내용은 [빠른 시작: Windows 10 디바이스 등록](~/enrollment/quickstart-enroll-windows-device.md)을 참조하세요.

## <a name="additional-information"></a>추가 정보

### <a name="register-device-with-windows-autopilot-optional"></a>Windows Autopilot에 디바이스 등록(선택 사항)

필요에 따라 등록된 Autopilot 디바이스를 사용하도록 선택할 수 있습니다. Autopilot의 경우 이 단계별 시나리오는 Autopilot 배포 프로필 및 등록 상태 페이지 프로필을 할당합니다. Autopilot 배포 프로필은 다음과 같이 구성됩니다.
- 사용자 기반 모드 - 즉, Windows 설치 중에 최종 사용자가 사용자 이름 및 암호를 입력해야 합니다.
- Azure AD 조인.
- Windows 설치 사용자 지정:
  - Microsoft 소프트웨어 사용 조건 화면 숨기기
  - 개인 정보 설정 숨기기 
  - 로컬 관리자 권한 없이 사용자의 로컬 프로필 만들기
  - 회사 로그인 페이지에서 계정 변경 옵션 숨기기

등록 상태 페이지는 Autopilot 디바이스에만 사용할 수 있도록 구성되며 모든 앱이 설치될 때까지 기다리도록 허용합니다.

또한 단계별 시나리오는 맞춤형 설정 환경에 대해 선택된 Autopilot 디바이스에 사용자를 할당합니다.

#### <a name="post-requisites"></a>사후 필수 조건
사용자가 디바이스를 Azure Active Directory에 조인하면 다음 구성이 디바이스에 적용됩니다.
1. Office 365 ProPlus는 클라우드 관리 PC에 자동으로 설치됩니다. 여기에는 Access, Excel, OneNote, Outlook, PowerPoint, Publisher, 비즈니스용 Skype 및 Word를 비롯하여 친숙한 애플리케이션이 포함됩니다. 이 애플리케이션을 사용하여 SharePoint Online, Exchange Online 및 비즈니스용 Skype Online과 같은 Office 365 서비스와 연결할 수 있습니다. Office 365 ProPlus는 Office의 비구독 버전과 달리 새로운 기능으로 정기적으로 업데이트됩니다. 새로운 기능 목록을 보려면 Office 365의 새로운 기능을 참조하세요.
2. Windows 보안 기준은 클라우드 관리 PC에 설치됩니다. Microsoft Defender Advanced Threat Protection을 설정한 경우 단계별 시나리오는 Defender의 기준 설정도 구성합니다. Defender Advanced Threat Protection은 Windows 10 보안 스택에 대한 보호의 새로운 위반 후 계층을 제공합니다. Windows 10에 기본 제공되는 클라이언트 기술과 강력한 클라우드 서비스의 조합을 사용하여 다른 방어를 통과하는 위협을 탐지할 수 있습니다. 

## <a name="next-steps"></a>다음 단계

- Microsoft Defender Advanced Threat Detection을 사용하는 경우 규정을 준수하기 위해 Defender 위협 분석을 요구하는 [Intune 준수 정책](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy)을 만듭니다.
- 디바이스가 Intune 준수를 충족하지 않는 경우 액세스를 차단하는 [디바이스 기반 조건부 액세스 정책](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy)을 만듭니다.
