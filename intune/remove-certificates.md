---
title: Microsoft Intune에서 SCEP 또는 PKCS 인증 제거 - Azure | Microsoft Docs
titleSuffix: ''
description: 관리자는 초기화 또는 사용 중지 조치를 사용하여 Microsoft Intune에서 인증서를 제거할 수 있습니다 디바이스 등록 취소 또는 준수 정책 제거 등 인증서가 자동으로 제거되는 시나리오가 있습니다. Intune 라이선스를 분실하거나 제거한 경우와 같이 인증서가 디바이스에 자동으로 남아 있는 시나리오도 있습니다. Android, Android 엔터프라이즈, iOS, macOS 및 Windows 디바이스에 대한 다양한 방법을 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 977e7006d39ae76516d5b06019e463d1018aaa79
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229261"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Microsoft Intune에서 SCEP 및 PKCS 인증서 제거

Microsoft Intune에서 디바이스에 SCEP(단순 인증서 등록 프로토콜) 및 PKCS(공개 키 암호화 표준) 인증서를 추가할 수 있습니다. 이 인증서는 디바이스를 [초기화](devices-wipe.md#wipe)하거나 [사용 중지](devices-wipe.md#retire)할 때도 제거할 수 있습니다. 

인증서가 자동으로 제거되는 또 다른 시나리오와 인증서가 디바이스에 남아있는 일부 시나리오가 있습니다. 이 문서에서는 몇 가지 일반적인 시나리오와 PKCS 및 SCEP 인증서에 미치는 영향을 나열합니다.

> [!NOTE]
> 온-프레미스 Active Directory 또는 Azure AD(Active Directory)에서 제거되는 사용자의 인증서를 제거하고 해지하려면 다음 단계를 순서대로 따릅니다.
>
> 1. 사용자의 디바이스 초기화하거나 사용 중지합니다.
> 2. 온-프레미스 Active Directory 또는 Azure AD에서 사용자를 제거합니다.

## <a name="windows-devices"></a>Windows 디바이스

#### <a name="scep-certificates"></a>SCEP 인증서

다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.
- 디바이스가 Azure AD 그룹에서 제거됩니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.

다음과 같은 경우 SCEP 인증서가 해지됩니다.
- 관리자가 SCEP 프로필을 변경하거나 업데이트합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.
- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 SCEP 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).
- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.

#### <a name="pkcs-certificates"></a>PKCS 인증서

다음과 같은 경우 PKCS 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.
- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 PKCS 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).
- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.
- 관리자가 PKCS 프로필을 변경하거나 업데이트합니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.


## <a name="ios-devices"></a>iOS 장치

#### <a name="scep-certificates"></a>SCEP 인증서

다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.
- 디바이스가 Azure AD 그룹에서 제거됩니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.

다음과 같은 경우 SCEP 인증서가 해지됩니다.
- 관리자가 SCEP 프로필을 변경하거나 업데이트합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.
- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 SCEP 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).
- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.

#### <a name="pkcs-certificates"></a>PKCS 인증서

다음과 같은 경우 PKCS 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 PKCS 인증서가 제거됩니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.
  
다음과 같은 경우 루트 인증서가 제거됩니다.
- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 PKCS 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).
- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.
- 관리자가 PKCS 프로필을 변경하거나 업데이트합니다.

## <a name="android-knox-devices"></a>Android KNOX 디바이스

#### <a name="scep-certificates"></a>SCEP 인증서

다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.
- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.

다음과 같은 경우 SCEP 인증서가 해지됩니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.
- 디바이스가 Azure AD 그룹에서 제거됩니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.
- 관리자가 SCEP 프로필을 변경하거나 업데이트합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.
- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 SCEP 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).
- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.

#### <a name="pkcs-certificates"></a>PKCS 인증서

다음과 같은 경우 PKCS 인증서가 해지 *및* 제거됩니다.

- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 루트 인증서가 제거됩니다.
- 사용자가 등록을 취소합니다.
- 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.

다음과 같은 경우 PKCS 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).
- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.
- 관리자가 PKCS 프로필을 변경하거나 업데이트합니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.
  
  
> [!NOTE]
> Android for Work 디바이스는 이전 시나리오에 대해 유효성이 검사되지 않습니다. Android 레거시 디바이스(삼성이 아닌 모든 비작업 프로필 디바이스)는 인증서를 제거할 수 없습니다. 

## <a name="macos-certificates"></a>macOS 인증서

#### <a name="scep-certificates"></a>SCEP 인증서

다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.
- 사용자가 등록을 취소합니다.
- 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행합니다.
- 디바이스가 Azure AD 그룹에서 제거됩니다.
- 인증서 프로필이 그룹 할당에서 제거됩니다.

다음과 같은 경우 SCEP 인증서가 해지됩니다.
- 관리자가 SCEP 프로필을 변경하거나 업데이트합니다.

다음과 같은 경우 SCEP 인증서가 디바이스에 *남아 있습니다*(인증서는 해지되거나 제거되지 않음).
- 사용자가 Intune 라이선스를 상실합니다.
- 관리자가 Intune 라이선스를 철회합니다.
- 관리자가 Azure AD에서 사용자 또는 그룹을 제거합니다.

> [!NOTE]
> [초기화](devices-wipe.md#wipe) 작업을 사용하여 macOS 디바이스를 초기화하는 기능은 지원되지 않습니다.

#### <a name="pkcs-certificates"></a>PKCS 인증서

PKCS 인증서는 macOS에서 지원되지 않습니다.

