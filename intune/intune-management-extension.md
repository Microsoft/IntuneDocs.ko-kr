---
title: Windows 10 장치용 Microsoft Intune에서 PowerShell 스크립트 추가 - Azure | Microsoft Docs
description: PowerShell 스크립트를 추가하고, Azure Active Directory 그룹에 스크립트 정책을 할당하고, 보고서를 사용하여 스크립트를 모니터링하고, Microsoft Intune에서 Windows 10 장치에 추가한 스크립트를 삭제하는 단계를 참조합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2046a928525e974eee5f63d772d46864b21f0267
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34583675"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Windows 10 장치를 위한 Intune에서의 PowerShell 스크립트 관리
Intune 관리 확장을 사용하면 Windows 10 장치에서 실행되도록 Intune에서 PowerShell 스크립트를 업로드할 수 있습니다. 관리 확장은 Windows 10 MDM(모바일 장치 관리) 기능을 보완하며 사용자가 최신 관리로 더 손쉽게 이행할 수 있도록 합니다.

## <a name="moving-to-modern-management"></a>최신 관리로 이동
최종 사용자 컴퓨팅은 디지털 변형을 거치는 중입니다. 기존의 클래식 IT는 단일 장치 플랫폼, 회사 소유 장치, 사무실에서 일하는 사용자, 다양한 수동적인 IT 프로세스에 초점을 맞추고 있습니다. 반면 최신 작업 공간에서는 사용자와 회사가 모두 소유하는 여러 장치 플랫폼이 가능하므로 사용자는 장소에 구애 받지 않고 일할 수 있으며 자동화된 능동적 IT 프로세스를 제공합니다. 

Microsoft Intune과 같은 MDM 서비스는 MDM 프로토콜을 사용하여 Windows 10 장치를 관리할 수 있습니다. 기본 제공되는 Windows 10 관리 클라이언트는 엔터프라이즈 관리 작업을 수행하는 Intune과 통신할 수 있습니다. 이를 통해 Windows 10 장치에서 최신 관리로 이행할 수 있습니다. 단, 고급 장치 구성, 문제 해결 및 현재 Windows 10 MDM에서 사용할 수 없는 레거시 Win32 앱 관리와 같은 특정 기능이 필요할 수도 있습니다. 이러한 기능의 경우 Windows 10 장치에서 Intune 소프트웨어 클라이언트를 실행할 수도 있습니다. 결과적으로, Windows 10 MDM이 제공하는 새 기능을 사용할 수 없습니다. [Intune 소프트웨어 클라이언트와 Windows 10 MDM 간의 차이점을 비교해 보세요](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison).

Intune 관리 확장은 Windows 10 MDM의 기본 기능을 보완합니다. 필요한 기능을 제공하는 Windows 10 장치에서 실행하도록 PowerShell 스크립트를 만들 수 있습니다. 예를 들어 Windows 10 장치에서 레거시 Win32 앱을 설치하는 PowerShell 스크립트를 만들고, Intune에 스크립트를 업로드하고, 스크립트를 Azure AD(Active Directory) 그룹에 할당하고, Windows 10 장치에서 스크립트를 실행할 수 있습니다. 그런 다음 Windows 10 장치에서 스크립트의 실행 상태를 처음부터 끝까지 모니터링할 수 있습니다.

## <a name="prerequisites"></a>전제 조건
Intune 관리 확장에는 다음과 같은 필수 구성 요소가 있습니다.
- 장치가 Azure AD에 연결되어야 합니다. 하이브리드 AD 연결 장치는 여기에 포함되지 않습니다.
- 장치에서 Windows 10 버전 1607 이상을 실행해야 합니다.
- [Azure AD에서 자동 MDM 등록을 사용](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)하도록 설정해야 하며, 장치가 Intune에 자동으로 등록되어야 합니다.

## <a name="create-a-powershell-script-policy"></a>PowerShell 스크립트 정책 만들기 
1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치 구성** > **PowerShell 스크립트** > **추가**를 차례로 선택합니다.
4. PowerShell 스크립트에 대한 **이름** 및 **설명**을 입력합니다. **스크립트 위치**에 대한 PowerShell 스크립트를 찾습니다. 스크립트는 200KB(ASCII) 또는 100KB(유니코드)보다 작아야 합니다.
5. **구성**을 선택합니다. 그런 다음, 장치(**예**) 또는 시스템 컨텍스트(**아니요**)에서 사용자의 자격 증명을 사용하여 스크립트를 실행하도록 선택합니다. 기본적으로 스크립트는 시스템 컨텍스트에서 실행됩니다. 스크립트를 시스템 컨텍스트에서 실행해야 하는 경우 외에는 **예**를 선택합니다. 
  ![PowerShell 스크립트 추가 창](./media/mgmt-extension-add-script.png)
6. 신뢰할 수 있는 게시자가 스크립트를 서명해야 하는지 여부를 선택합니다(**예**). 기본적으로 서명할 스크립트에 대한 요구 사항은 없습니다. 
7. **확인**, **만들기**를 차례로 클릭하여 스크립트를 저장합니다.

## <a name="assign-a-powershell-script-policy"></a>PowerShell 스크립트 정책 할당
1. **PowerShell 스크립트**에서 할당할 스크립트를 선택한 다음, **관리** > **할당**을 차례로 선택합니다.
  ![PowerShell 스크립트 추가 창](./media/mgmt-extension-assignments.png)
 
2. **그룹 선택**을 선택하여 사용할 수 있는 Azure AD 그룹을 나열합니다. 
3. 장치에서 스크립트를 받는 사용자가 포함된 그룹을 하나 이상 선택합니다. 선택한 그룹에 정책을 할당하도록 **선택**합니다.

Intune 관리 확장은 1시간마다 Intune으로 동기화합니다. Azure AD 그룹에 정책이 지정되면 PowerShell 스크립트가 실행되고 실행 결과가 보고됩니다. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>PowerShell 스크립트에 대한 실행 상태 모니터
Azure Portal에서 사용자 및 장치에 대한 PowerShell 스크립트의 실행 상태를 모니터링할 수 있습니다.

**PowerShell 스크립트**에서 모니터링할 스크립트를 선택하고, **모니터**를 선택한 다음, 다음 보고서 중 하나를 선택합니다.
   - **장치 상태**
   - **사용자 상태**

## <a name="delete-a-powershell-script"></a>PowerShell 스크립트 삭제
**PowerShell 스크립트**에서 스크립트를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.
