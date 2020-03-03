---
title: 플랫폼에서 지원되는 암호화 방법으로 디바이스 암호화
titleSuffix: Microsoft Intune
description: BitLocker 또는 FileVault와 같은 기본 제공 암호화 방법을 사용하여 디바이스를 암호화하고 Intune 포털 내에서 암호화된 디바이스의 복구 키를 관리하세요.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a5c844377dcd69b6caf5ef9f72fcb8dbb4ef8bd0
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609305"
---
# <a name="use-device-encryption-with-intune"></a>Intune에서 디바이스 암호화 사용

Intune을 통해 디바이스 기본 제공 디스크 또는 드라이브 암호화를 관리하여 디바이스의 데이터를 보호하세요.

엔드포인트 보호를 위해 디스크 암호화를 디바이스 구성 프로필의 일부로 구성할 수 있습니다. Intune에서 지원하는 플랫폼 및 암호화 기술은 다음과 같습니다.

- macOS: FileVault
- Windows 10 이상: BitLocker

또한 Intune은 모든 관리형 디바이스에서 디바이스의 암호화 상태에 관한 세부 정보를 제시하는 기본 제공 [암호화 보고서](encryption-monitor.md)도 제공합니다.

## <a name="filevault-encryption-for-macos"></a>macOS를 위한 FileVault 암호화

Intune을 사용하여 macOS를 실행하는 디바이스에서 FileVault 디스크 암호화를 구성할 수 있습니다. 그런 다음 Intune 암호화 보고서를 사용하여 해당 디바이스의 암호화 세부 정보를 확인하고 FileVault로 암호화된 디바이스의 복구 키를 관리할 수 있습니다.

FileVault가 디바이스에서 작동하려면 사용자 승인 디바이스 등록이 필요합니다. 사용자는 등록이 사용자의 승인을 받은 것으로 간주되도록 시스템 기본 설정에서 관리 프로필을 수동으로 승인해야 합니다.

FileVault는 macOS에 포함된 전체 디스크 암호화 프로그램입니다. Intune을 사용하여 **macOS 10.13 이상**을 실행하는 디바이스에서 FileVault를 구성할 수 있습니다.

FileVault를 구성하려면 macOS 플랫폼의 엔드포인트 보호를 위한 [디바이스 구성 프로필](../configuration/device-profile-create.md)을 만듭니다. FileVault 설정은 macOS 엔드포인트 보호를 위해 사용할 수 있는 설정 범주 중 하나입니다.

FileVault를 사용하여 디바이스를 암호화하는 정책을 만든 후 2단계로 디바이스에 정책이 적용됩니다. 먼저 Intune에서 복구 키를 검색하고 백업할 수 있도록 디바이스를 준비합니다. 이 작업을 에스크로라고 합니다. 키를 에스크로했으면 디스크 암호화를 시작할 수 있습니다.

![FileVault 설정](./media/encrypt-devices/filevault-settings.png)

Intune에서 관리할 수 있는 FileVault 설정에 대한 자세한 내용은 macOS 엔드포인트 보호 설정에 관한 Intune 문서에서 [FileVault](endpoint-protection-macos.md#filevault)를 참조하세요.

### <a name="permissions-to-manage-filevault"></a>FileVault를 관리할 권한

Intune에서 FileVault를 관리하려면 계정에 적용 가능한 Intune RBAC([역할 기반 액세스 제어](../fundamentals/role-based-access-control.md)) 권한이 있어야 합니다.

**원격 작업** 범주의 일부인 FileVault 권한 및 권한을 부여하는 기본 제공 RBAC 역할은 다음과 같습니다.
 
- **FileVault 키 가져오기**:
  - 기술 지원팀 운영자
  - 엔드포인트 보안 관리자

- **FileVault 키 회전**
  - 기술 지원팀 운영자

### <a name="how-to-configure-macos-filevault"></a>MacOS FileVault를 구성하는 방법

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.

3. 다음 옵션을 설정합니다.

   - 플랫폼: macOS
   - 프로필 유형: 엔드포인트 보호

4. **설정** > **FileVault**를 선택합니다.

5. ‘FileVault’에 대해 **사용**을 선택합니다. 

6. ‘복구 키 유형’은 **개인 키**만 지원됩니다. 

   최종 사용자에게 디바이스의 복구 키를 검색하는 방법을 안내할 수 있는 메시지를 추가하는 것이 좋습니다. 정기적으로 디바이스의 새 복구 키를 자동으로 생성할 수 있는 개인 복구 키 회전을 위한 설정을 사용하는 경우 이 정보는 최종 사용자에게 유용할 수 있습니다.

   예를 들면 다음과 같습니다. 손실되거나 최근 회전된 복구 키를 검색하려면 원하는 디바이스에서 Intune 회사 포털 웹 사이트에 로그인합니다. 포털에서 ‘디바이스’로 이동하고 FileVault를 사용하도록 설정한 디바이스를 선택한 다음 ‘복구 키 가져오기’를 선택합니다.   현재 복구 키가 표시됩니다.

7. 비즈니스 요구에 맞게 나머지 [FileVault 설정](endpoint-protection-macos.md#filevault)을 구성한 다음, **확인**을 선택합니다.

  8. 추가 설정 구성을 완료한 다음 프로필을 저장합니다.  

### <a name="manage-filevault"></a>FileVault 관리

Intune이 FileVault를 사용하여 macOS 디바이스를 암호화한 후에는 intune [암호화 보고서](encryption-monitor.md)를 볼 때 FileVault 복구 키를 보고 관리할 수 있습니다.

Intune이 FileVault로 macOS 디바이스를 암호화한 후에는 모든 디바이스의 웹 회사 포털에서 해당 디바이스의 개인 복구 키를 볼 수 있습니다. 웹 회사 포털에서 암호화된 macOS 디바이스를 선택하고 원격 디바이스 작업으로 "복구 키 가져오기"를 선택합니다.

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices"></a>MEM 암호화된 macOS 디바이스에서 개인 복구 키 검색

최종 사용자는 iOS 회사 포털 앱을 사용하여 개인 복구 키(FileVault 키)를 검색합니다. 개인 복구 키를 포함한 디바이스는 Intune에 등록하고 Intune을 통한 FileVault로 암호화해야 합니다. iOS 회사 포털 앱을 사용하면 최종 사용자는 FileVault 개인 복구 키가 포함된 웹 페이지를 열 수 있습니다. Intune에서 **디바이스** > *암호화되어 등록된 macOS 디바이스* > **복구 키 가져오기**를 선택하여 복구 키를 검색할 수도 있습니다. 

## <a name="bitlocker-encryption-for-windows-10"></a>Windows 10용 BitLocker 암호화

Intune을 사용하여 Windows 10을 실행하는 디바이스에서 BitLocker 드라이브 암호화를 구성할 수 있습니다. 그런 다음 Intune 암호화 보고서를 사용하여 해당 디바이스의 암호화 정보를 확할 수 있습니다. 또한 Azure AD(Azure Active Directory)에 있는 디바이스의 BitLocker에 대한 중요한 정보에 액세스할 수 있습니다.

BitLocker는 **Windows 10 이상**을 실행하는 디바이스에서 사용할 수 있습니다.

Windows 10 이상 플랫폼의 엔드포인트 보호를 위한 [디바이스 구성 프로필](../configuration/device-profile-create.md)을 만들 때 BitLocker를 구성할 수 있습니다. BitLocker 설정은 Windows 10 엔드포인트 보호를 위한 Windows 암호화 설정 범주에 있습니다.

![BitLocker 설정](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>Windows 10 BitLocker를 구성하는 방법

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.

3. 다음 옵션을 설정합니다.

   - 플랫폼: Windows 10 이상
   - 프로필 유형: 엔드포인트 보호

4. **설정** > **Windows 암호화**를 선택합니다.

5. 비즈니스 요구에 맞게 BitLocker의 설정을 구성한 다음 **확인**을 선택합니다.

6. 추가 설정 구성을 완료한 다음 프로필을 저장합니다.

### <a name="manage-bitlocker"></a>BitLocker 관리

Intune이 BitLocker를 사용하여 Windows 10 디바이스를 암호화한 후에는 intune [암호화 보고서](encryption-monitor.md)를 볼 때 BitLocker 복구 키를 보고 관리할 수 있습니다.

### <a name="rotate-bitlocker-recovery-keys"></a>BitLocker 복구 키 순환

Intune 디바이스 작업을 사용하여 Windows 10 버전 1909 이상을 실행하는 디바이스의 BitLocker 복구 키를 원격으로 순환할 수 있습니다.

#### <a name="prerequisites"></a>전제 조건

BitLocker 복구 키의 순환을 지원하려면 디바이스가 다음 필수 구성 요소를 충족해야 합니다.

- 디바이스에서 Windows 10 버전 1909 이상을 실행해야 합니다.

- Azure AD 조인 및 하이브리드 조인 디바이스는 키 순환을 지원해야 합니다.

  - **클라이언트 기반 복구 암호 순환**

  이 설정은 Windows 10 Endpoint Protection에 대한 디바이스 구성 정책의 일부로 *Windows 암호* 아래에 있습니다.
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>BitLocker 복구 키를 순환하려면

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스** > **모든 디바이스**를 선택합니다.

3. 관리하는 디바이스 목록에서 디바이스를 선택하고 **자세히**를 선택한 다음, **BitLocker 키 순환** 디바이스 원격 작업을 선택합니다.

## <a name="next-steps"></a>다음 단계

[디바이스 준수](compliance-policy-create-windows.md) 정책 만들기

암호화 보고서를 사용하여 다음 관리

- [BitLocker 복구 키](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault 복구 키](encryption-monitor.md#filevault-recovery-keys)

Intune으로 구성하는 암호화 설정 검토

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
