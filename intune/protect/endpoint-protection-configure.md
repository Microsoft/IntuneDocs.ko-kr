---
title: Microsoft Intune - Azure에서 엔드포인트 보호 설정 구성 | Microsoft Docs
description: Microsoft Intune에서 macOS 또는 Windows 10 디바이스 프로필을 만들 경우 엔드포인트 보호 설정을 만듭니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 884e4211a880feb3eb533238a5e7246b2738ce46
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502312"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Intune에서 엔드포인트 보호 설정 추가  

Intune에서 디바이스 구성 프로필을 사용하여 디바이스에서 다음을 포함한 일반적인 엔드포인트 보호 보안 기능을 관리할 수 있습니다.  
- 방화벽   
- BitLocker  
- 앱 허용 및 차단  
- Windows Defender 및 암호화  

예를 들어 Mac 앱 스토어에서 macOS 사용자만 앱을 설치할 수 있는 엔드포인트 보호 프로필을 만들 수 있습니다. 또는 Windows 10 디바이스에서 앱을 실행하는 경우 Windows SmartScreen을 사용하도록 설정합니다.  

프로필을 만들기 전에 Intune에서 관리할 수 있는 각 지원되는 플랫폼의 엔드포인트 보호 설정을 자세히 설명하는 다음 문서를 참조하세요.  
   - [macOS 설정](endpoint-protection-macos.md)  
   - [Windows 10 설정](endpoint-protection-windows-10.md)  

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>엔드포인트 보호 설정을 포함하는 디바이스 프로필 만들기  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.  
3. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.  
4. 엔드포인트 보호 프로필의 **이름** 및 **설명**을 입력합니다.  
5. **플랫폼** 드롭다운 목록에서 사용자 지정 설정을 적용할 디바이스 플랫폼을 선택합니다. 현재 디바이스 제한 설정에 대해 다음 플랫폼 중 하나를 선택할 수 있습니다.  
   - **macOS**  
   - **Windows 10 이상**  
6. **프로필 유형** 드롭다운 목록에서 **Endpoint Protection**을 선택합니다.  
7. 선택한 플랫폼에 따라 구성할 수 있는 설정이 다릅니다. 참조:  
   - [macOS 설정](endpoint-protection-macos.md)  
   - [Windows 10 설정](endpoint-protection-windows-10.md)  

8. 적용 가능한 설정을 구성한 후 **프로필 만들기** 페이지에서 **만들기**를 선택합니다.  

   프로필이 만들어지고 프로필 목록 페이지에 표시됩니다. 이 프로필을 그룹에 할당하려면 [디바이스 프로필 할당](../configuration/device-profile-assign.md)을 참조하세요.  

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Windows 10 디바이스의 사용자 지정 방화벽 규칙 추가  

Windows 10의 엔드포인트 보호 규칙을 포함하는 프로필의 일부로 Windows Defender 방화벽을 구성하는 경우 방화벽의 사용자 지정 규칙을 구성할 수 있습니다. 사용자 지정 규칙을 사용하면 Windows 10에서 지원되는 미리 정의된 방화벽 규칙 세트를 확장할 수 있습니다.  

사용자 지정 방화벽 규칙을 사용하여 프로필을 계획하는 경우 프로필의 방화벽 규칙을 그룹화하는 방법에 영향을 줄 수 있는 다음 정보를 고려하세요.  
- 각 프로필은 최대 150개의 방화벽 규칙을 지원합니다. 150개 이상의 규칙을 사용하는 경우 각각 150개 규칙으로 제한되는 추가 프로필을 만듭니다.  
- 각 프로필에서 규칙이 하나라도 적용되지 않는 경우 해당 프로필의 모든 규칙이 실패하고 규칙 중 아무것도 디바이스에 적용되지 않습니다.  
- 하나의 규칙이 적용되지 않으면 프로필의 모든 규칙이 실패로 보고됩니다. Intune에서는 실패한 개별 규칙을 식별할 수 없습니다.  

Intune에서 관리할 수 있는 방화벽 규칙은 Windows [방화벽 CSP(구성 서비스 공급자)]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)에 자세히 설명되어 있습니다. Intune에서 지원하는 Windows 10 디바이스의 사용자 지정 방화벽 설정 목록을 검토하려면 [사용자 지정 방화벽 규칙](endpoint-protection-windows-10.md#firewall-rules)을 참조하세요.  

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>엔드포인프 보호 프로필에 사용자 지정 방화벽 규칙을 추가하려면  

1. Intune에서 **디바이스 구성** > **프로필** > **프로필 만들기**로 이동합니다.  

2. ‘플랫폼’에서 **Windows 10 이상**을 선택한 다음 ‘프로필 유형’에서 **엔드포인트 보호**를 선택합니다.    

3. **Windows Defender 방화벽**을 선택하고 구성 페이지를 열고 ‘방화벽 규칙’에서 **추가**를 선택하여 **규칙 만들기** 페이지를 엽니다.   

4. 방화벽 규칙의 설정을 지정한 다음 **확인**을 선택하여 저장합니다. 설명서에서 사용 가능한 사용자 지정 방화벽 규칙 옵션을 검토하려면 [사용자 지정 방화벽 규칙](endpoint-protection-windows-10.md#firewall-rules)을 참조하세요.  

5. 규칙을 저장하면 ‘Windows Defender 방화벽’ 페이지의 규칙 목록에 표시됩니다.   

6. 규칙을 수정하려면 목록에서 규칙을 선택하여 **규칙 편집** 페이지를 엽니다.  

7. 프로필에서 규칙을 삭제하려면 규칙의 줄임표 **(…)** 를 선택한 다음 **삭제**를 선택합니다.  

8. 규칙이 표시되는 순서를 변경하려면 규칙 목록 맨 위의 ‘위쪽 화살표, 아래쪽 화살표’ 아이콘을 선택합니다.   


## <a name="next-steps"></a>다음 단계  

프로필을 그룹에 할당하려면 [디바이스 프로필 할당](../configuration/device-profile-assign.md)을 참조하세요.  
