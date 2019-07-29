---
title: 플랫폼에서 지원되는 암호화 방법을 사용하여 Microsoft Intune에서 디바이스 암호화
titleSuffix: Microsoft Intune
description: BitLocker 또는 FileVault와 같은 기본 제공 암호화 방법을 사용하여 디바이스를 암호화하고 Intune 포털 내에서 암호화된 디바이스의 복구 키를 관리하세요.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 57b459efa5b423f1c73a0d6b7b9172f71f4c86d3
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375166"
---
# <a name="use-device-encryption-with-intune"></a>Intune에서 디바이스 암호화 사용  

Intune을 통해 디바이스 기본 제공 디스크 또는 드라이브 암호화를 관리하여 디바이스의 데이터를 보호하세요.  

엔드포인트 보호를 위해 디스크 암호화를 디바이스 구성 프로필의 일부로 구성할 수 있습니다. Intune에서 지원하는 플랫폼 및 암호화 기술은 다음과 같습니다.  
- macOS: FileVault   
- Windows 10 이상: BitLocker  

또한 Intune은 모든 관리형 디바이스에서 디바이스의 암호화 상태에 관한 세부 정보를 제시하는 기본 제공 [암호화 보고서](encryption-monitor.md)도 제공합니다.  

## <a name="filevault-encryption-for-macos"></a>macOS를 위한 FileVault 암호화  

Intune을 사용하여 macOS를 실행하는 디바이스에서 FileVault 디스크 암호화를 구성할 수 있습니다. 그런 다음 Intune 암호화 보고서를 사용하여 해당 디바이스의 암호화 세부 정보를 확인하고 FileVault로 암호화된 디바이스의 복구 키를 관리할 수 있습니다.  

FileVault는 macOS에 포함된 전체 디스크 암호화 프로그램입니다. Intune을 사용하여 **macOS 10.13 이상**을 실행하는 디바이스에서 FileVault를 구성할 수 있습니다.  

FileVault를 구성하려면 macOS 플랫폼의 엔드포인트 보호를 위한 [디바이스 구성 프로필](device-profile-create.md)을 만듭니다. FileVault 설정은 macOS 엔드포인트 보호를 위해 사용할 수 있는 설정 범주 중 하나입니다.  

FileVault를 사용하여 디바이스를 암호화하는 정책을 만든 후 2단계로 디바이스에 정책이 적용됩니다. 먼저 Intune에서 복구 키를 검색하고 백업할 수 있도록 디바이스를 준비합니다. 이를 에스크로라고 합니다. 키를 에스크로했으면 디스크 암호화를 시작할 수 있습니다.

![FileVault 설정](./media/encrypt-devices/filevault-settings.png)

Intune에서 관리할 수 있는 FileVault 설정에 대한 자세한 내용은 macOS 엔드포인트 보호 설정에 관한 Intune 문서에서 [FileVault](endpoint-protection-macos.md#filevault)를 참조하세요.  

### <a name="how-to-configure-macos-filevault"></a>MacOS FileVault를 구성하는 방법 

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스 구성** > **프로필** > **프로필 만들기**로 이동합니다.  

2. 다음 옵션을 설정합니다.  

   - 플랫폼: macOS  
   - 프로필 유형: Endpoint Protection  

3. **설정** > **FileVault**를 선택합니다.  

4. ‘FileVault’에 대해 **사용**을 선택합니다.   

5. ‘복구 키 유형’은 **개인 키**만 지원됩니다.   

   최종 사용자에게 디바이스의 복구 키를 검색하는 방법을 안내할 수 있는 메시지를 추가하는 것이 좋습니다. 정기적으로 디바이스의 새 복구 키를 자동으로 생성할 수 있는 개인 복구 키 회전을 위한 설정을 사용하는 경우 이 정보는 최종 사용자에게 유용할 수 있습니다.  

   예를 들면 다음과 같습니다. 손실되거나 최근 회전된 복구 키를 검색하려면 원하는 디바이스에서 Intune 회사 포털 웹 사이트에 로그인합니다. 포털에서 ‘디바이스’로 이동하고 FileVault를 사용하도록 설정한 디바이스를 선택한 다음 ‘복구 키 가져오기’를 선택합니다.   현재 복구 키가 표시됩니다.  

6. 비즈니스 요구에 맞게 나머지 설정을 구성한 다음 **확인**을 선택합니다.  

   > [!NOTE]
   > 7월 릴리스 출시가 며칠 내에 완료될 때까지 FileVault의 지원이 제한됩니다. 출시가 완료될 때까지는 FileVault를 구성하는 경우 ‘로그아웃할 때까지 FileVault 연기’를 **사용**으로 설정해야 합니다.   

7. 추가 설정 구성을 완료한 다음 프로필을 저장합니다.  

### <a name="manage-filevault"></a>FileVault 관리  

Intune이 FileVault를 사용하여 macOS 디바이스를 암호화한 후에는 intune [암호화 보고서](encryption-monitor.md)를 볼 때 FileVault 복구 키를 보고 관리할 수 있습니다.  

## <a name="bitlocker-encryption-for-windows-10"></a>Windows 10용 BitLocker 암호화  

Intune을 사용하여 Windows 10을 실행하는 디바이스에서 BitLocker 드라이브 암호화를 구성할 수 있습니다. 그런 다음 Intune 암호화 보고서를 사용하여 해당 디바이스의 암호화 정보를 확할 수 있습니다. 또한 Azure AD(Azure Active Directory)에 있는 디바이스의 BitLocker에 대한 중요한 정보에 액세스할 수 있습니다.  

BitLocker는 **Windows 10 이상**을 실행하는 디바이스에서 사용할 수 있습니다.  

Windows 10 이상 플랫폼의 엔드포인트 보호를 위한 [디바이스 구성 프로필](device-profile-create.md)을 만들 때 BitLocker를 구성할 수 있습니다. BitLocker 설정은 Windows 10 엔드포인트 보호를 위한 Windows 암호화 설정 범주에 있습니다.    

![BitLocker 설정](./media/encrypt-devices/bitlocker-settings.png) 

### <a name="how-to-configure-windows-10-bitlocker"></a>Windows 10 BitLocker를 구성하는 방법  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 디바이스 구성 > 프로필 > 프로필 만들기로 이동합니다.  

2. 다음 옵션을 설정합니다.  
   - 플랫폼: Windows 10 이상  
   - 프로필 유형: Endpoint Protection  

3. **설정** > **Windows 암호화**를 선택합니다.

4. 비즈니스 요구에 맞게 BitLocker의 설정을 구성한 다음 **확인**을 선택합니다.  

5. 추가 설정 구성을 완료한 다음 프로필을 저장합니다.  

### <a name="manage-bitlocker"></a>BitLocker 관리  

Intune이 BitLocker를 사용하여 Windows 10 디바이스를 암호화한 후에는 intune [암호화 보고서](encryption-monitor.md)를 볼 때 BitLocker 복구 키를 보고 관리할 수 있습니다.  

## <a name="next-steps"></a>다음 단계  

[디바이스 준수](compliance-policy-create-windows.md) 정책 만들기  

암호화 보고서를 사용하여 다음 관리  
- [BitLocker 복구 키](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault 복구 키](encryption-monitor.md#filevault-recovery-keys)

Intune으로 구성하는 암호화 설정 검토  
- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)  
- [FileVault](endpoint-protection-macos.md#filevault)  
 
 
