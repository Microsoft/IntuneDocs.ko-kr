---
title: Intune을 사용하여 Microsoft Defender ATP가 발견한 취약성 수정 -Azure | Microsoft Docs
description: Intune 콘솔에서 보안 작업 및 Microsoft Defender ATP(Advanced Threat Protection)의 일부인 위협 및 취약성 관리를 관리하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 987e3171c4e5c5ba3f15097837e2c018ddc7a4b6
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049207"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>Intune을 사용하여 Microsoft Defender ATP가 식별한 취약성 수정  

Intune을 Microsoft Defender ATP(Advanced Threat Protection)와 통합하면 ATP의 TVM(위협 및 취약성 관리)을 활용하고 Intune을 사용하여 TVM이 식별한 엔드포인트 약점을 수정할 수 있습니다. 이렇게 통합하면 사용자 환경에서 수정 응답 시간을 개선할 수 있는 위험 기반 접근 방식을 통해 취약성을 검색하고 우선 순위를 지정할 수 있습니다.  

[위협 및 취약성 관리](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt)는 [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)의 일부입니다.  

## <a name="how-integration-works"></a>통합의 작동 방식  

Intune을 Microsoft Defender Advanced Threat Protection에 연결한 후 ATP는 관리형 디바이스에서 위협 및 취약성 정보를 수신합니다.  

Windows Defender Security Center 콘솔에서 ATP 보안 관리자는 엔드포인트 취약성에 대한 데이터를 검토합니다. 그런 다음, 관리자는 한 번 클릭을 사용하여 수정을 위해 취약한 디바이스에 플래그를 지정하는 보안 작업을 만듭니다. 보안 작업은 Intune 관리자가 볼 수 있는 Intune 콘솔에 즉시 전달됩니다. 보안 작업은 취약성 유형, 우선 순위, 상태 및 취약성을 수정하기 위해 수행할 단계를 나타냅니다. Intune 관리자는 작업을 허용 또는 거부하도록 선택합니다.  

작업을 수락되면 Intune 관리자는 보안 작업의 일부로 제공되는 지침에 따라 Intune을 통해 취약성을 수정합니다.  

일반적인 수정 작업은 다음과 같습니다.  
- 애플리케이션이 실행되지 못하도록 **차단**  
- 취약성을 완화하기 위해 운영 체제 업데이트 **배포**  
- 레지스트리 값 **수정**  
- 취약성에 영향을 미치는 구성을 **사용 안 함** 또는 **사용**으로 설정  
- **주의 필요**는 제공할 적합한 권장 사항이 없는 경우 관리자에게 위협을 경고하는 작업입니다.  

예제 워크플로:  
- Microsoft Defender ATP 내에서 Contoso Media Player v4라는 앱의 취약성이 발견되었고 관리자가 해당 앱을 업데이트하기 위한 보안 작업을 만듭니다. Contoso Media Player는 Intune을 사용하여 배포된 비관리형 앱입니다.  

  이 보안 작업은 보류 중 상태로 Intune 콘솔에 표시됩니다.  
  ![Intune 콘솔에서 보안 작업 목록 보기](./media/atp-manage-vulnerabilities/temp-security-tasks.png)
 
- Intune 관리자는 보안 작업을 선택하여 작업에 대한 세부 정보를 봅니다.  그런 다음, 관리자는 **수락**을 선택합니다. 그러면 Intune 및 ATP에서 상태가 ‘수락됨’으로 업데이트됩니다.  
  ![보안 작업 수락 또는 거부](./media/atp-manage-vulnerabilities/temp-accept-task.png) 
 
- 그런 다음, 관리자는 제공된 지침에 따라 작업을 수정합니다.  지침은 필요한 수정 유형에 따라 달라집니다. 사용 가능한 경우 수정 지침에는 Intune에서 구성 관련 창을 여는 링크가 포함됩니다. 

  이 예제에서 Media Player는 관리형 앱이 아니므로 Intune은 텍스트 지침만 제공할 수 있습니다. 관리형 앱인 경우 Intune은 업데이트된 버전을 다운로드하는 지침을 제공하고 업데이트된 파일을 배포에 추가할 수 있도록 앱에 대한 배포를 여는 링크를 제공할 수 있습니다. 

- 수정을 완료한 후 Intune 관리자는 보안 작업을 열고 **작업 완료**를 선택합니다.  수정 상태가 Intune 및 ATP에서 업데이트되고, 여기서 보안 관리자가 수정된 취약성 상태를 확인합니다.  

## <a name="prerequisites"></a>전제 조건  

**구독**:  
- Microsoft Intune  
- Microsoft Defender Advanced Threat Protection([평가판에 가입](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink))  

**ATP에 대한 Intune 구성**:  
- Microsoft Defender ATP를 사용하여 서비스 간 연결을 구성합니다.  
- ATP를 통해 위험을 평가할 디바이스에 **Microsoft Defender ATP(Windows 10 데스크톱)** 의 프로필 유형을 사용하는 디바이스 준수 정책을 배포합니다.
  ATP를 사용하도록 Intune을 설정하는 방법에 대한 자세한 내용은 [Intune에서 조건부 액세스로 Microsoft Defender ATP에 대한 규정 준수 적용](https://docs.microsoft.com/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune)을 참조하세요.  

## <a name="work-with-security-tasks"></a>보안 작업 사용  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스 보안** > **보안 작업**으로 이동합니다.  
2. 목록에서 작업을 선택하여 해당 보안 작업의 추가 세부 정보를 표시하는 리소스 창을 엽니다.  
3. 보안 작업 리소스 창을 보면서 추가 링크를 선택할 수 있습니다.  
   - 관리형 앱 - 취약한 앱을 봅니다. 취약성이 여러 앱에 적용되는 경우 필터링된 앱 목록이 표시됩니다.  
   - 디바이스 - 해당 디바이스에 있는 취약성의 추가적인 세부 정보가 포함된 항목에 연결할 수 있는 ‘취약한 디바이스 목록’을 봅니다.  
   - 요청자 - 링크를 사용하여 이 보안 작업을 제출한 관리자에게 메일을 보냅니다.  
   - 메모 - 보안 작업을 열 때 요청자가 제출한 사용자 지정 메시지를 읽습니다.  
4. **수락** 또는 **거부**를 선택하여 계획된 작업에 대한 알림을 ATP에 보냅니다. 작업을 수락하거나 거부할 때 ATP에 전송되는 메모를 제출할 수 있습니다.  

5. 작업을 수락한 후 보안 작업을 다시 열고(닫힌 경우) 수정 세부 정보에 따라 취약성을 수정합니다.  보안 작업 정보에서 ATP가 제공하는 지침은 관련된 취약성에 따라 달라집니다.  

   수정 지침에는 Intune 콘솔에서 관련 구성 개체를 여는 링크가 포함됩니다(열 수 있는 경우).  

6. 수정 단계를 완료한 후 보안 작업을 열고 **작업 완료**를 선택합니다.  이 작업은 Intune 및 ATP에서 보안 작업 상태를 업데이트합니다.  

수정에 성공한 후 수정된 디바이스의 새로운 정보를 기반으로 ATP의 위험 노출 점수가 떨어질 수 있습니다. 

## <a name="next-steps"></a>다음 단계
Intune 및 [Microsoft Defender ATP](https://docs.microsoft.com/intune/advanced-threat-protection)에 대한 자세한 정보  
Intune [Mobile Threat Defense](https://docs.microsoft.com/intune/mobile-threat-defense) 검토  
Microsoft Defender ATP의 [위협 및 취약성 관리 대시보드](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights) 검토
