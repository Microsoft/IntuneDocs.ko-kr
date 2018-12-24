---
title: Microsoft Intune에서 SCEP 또는 PKCS 인증 제거 - Azure | Microsoft Docs
titleSuffix: ''
description: 관리자는 초기화 또는 사용 중지 조치를 사용하여 Microsoft Intune에서 인증서를 제거할 수 있습니다 디바이스 등록 취소 또는 준수 정책 제거 등 인증서가 자동으로 제거되는 시나리오가 있습니다. Intune 라이선스를 분실하거나 제거한 경우와 같이 인증서가 디바이스에 자동으로 남아 있는 시나리오도 있습니다. Android, Android 엔터프라이즈, iOS, macOS 및 Windows 디바이스에 대한 다양한 방법을 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 06b568ee7cc2dc55a8d44cf04b96078b47d8c4b3
ms.sourcegitcommit: 77a1047f5d93c1924e5c9ea243454532881be031
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52579169"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Microsoft Intune에서 SCEP 및 PKCS 인증서 제거

Microsoft Intune에서 디바이스에 SCEP 및 PKCS 인증서를 추가할 수 있습니다. 이 인증서는 디바이스를 [초기화](devices-wipe.md#wipe)하거나 [사용 중지](devices-wipe.md#retire)할 때도 제거할 수 있습니다. 인증서가 자동으로 제거되는 또 다른 시나리오와 인증서가 디바이스에 남아있는 일부 시나리오가 있습니다.

이 문서에서는 몇 가지 일반적인 시나리오와 PKCS 및 SCEP 인증서에 미치는 영향을 나열합니다.

> [!NOTE]
> Active Directory(AD) 또는 Azure AD에서 제거되는 사용자의 인증서를 제거하고 해지하려면 다음 단계를 순서대로 따르십시오.
>
>    1. 사용자의 디바이스 초기화 또는 사용 중지
>    2. AD 또는 Azure AD에서 사용자 제거

## <a name="windows-devices"></a>Windows 디바이스

#### <a name="scep-certificates"></a>SCEP 인증서

- 다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.

  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우
  - 디바이스는 Azure Active Directory(AD) 그룹에서 제거됩니다.
  - 인증서 프로필은 그룹 할당에서 제거됩니다.

- 다음과 같은 경우 SCEP 인증서가 해지됩니다.
  - 관리자가 SCEP 프로필을 변경하거나 업데이트하는 경우

- 다음과 같은 경우 루트 인증서가 제거됩니다.
  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우

- 다음과 같은 경우 SCEP 인증서가 디바이스에 **남아 있습니다**(인증서는 해지되거나 제거되지 않음).
  - 최종 사용자가 Intune 라이선스를 상실하는 경우
  - 관리자가 Intune 라이선스를 철회하는 경우
  - 관리자가 Azure AD에서 사용자 또는 그룹을 제거하는 경우

#### <a name="pkcs-certificates"></a>PKCS 인증서

- 다음과 같은 경우 PKCS 인증서가 해지 *및* 제거됩니다.

  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우

- 다음과 같은 경우 루트 인증서가 제거됩니다.
  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우

- 다음과 같은 경우 PKCS 인증서가 디바이스에 **남아 있습니다**(인증서는 해지되거나 제거되지 않음).
  - 최종 사용자가 Intune 라이선스를 상실하는 경우
  - 관리자가 Intune 라이선스를 철회하는 경우
  - 관리자가 Azure AD에서 사용자 또는 그룹을 제거하는 경우
  - 관리자가 PKCS 프로필을 변경하거나 업데이트하는 경우
  - 인증서 프로필은 그룹 할당에서 제거됩니다.


## <a name="ios-devices"></a>iOS 장치

#### <a name="scep-certificates"></a>SCEP 인증서

- 다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.

  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우
  - 디바이스는 Azure Active Directory(AD) 그룹에서 제거됩니다.
  - 인증서 프로필은 그룹 할당에서 제거됩니다.

- 다음과 같은 경우 SCEP 인증서가 해지됩니다.
  - 관리자가 SCEP 프로필을 변경하거나 업데이트하는 경우

- 다음과 같은 경우 루트 인증서가 제거됩니다.
  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우

- 다음과 같은 경우 SCEP 인증서가 디바이스에 **남아 있습니다**(인증서는 해지되거나 제거되지 않음).
  - 최종 사용자가 Intune 라이선스를 상실하는 경우
  - 관리자가 Intune 라이선스를 철회하는 경우
  - 관리자가 Azure AD에서 사용자 또는 그룹을 제거하는 경우

#### <a name="pkcs-certificates"></a>PKCS 인증서

- 다음과 같은 경우 PKCS 인증서가 해지 *및* 제거됩니다.

  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우

- 다음과 같은 경우 PKCS 인증서가 제거됩니다.
  - 인증서 프로필은 그룹 할당에서 제거됩니다.
  
- 다음과 같은 경우 루트 인증서가 제거됩니다.
  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우

- 다음과 같은 경우 PKCS 인증서가 디바이스에 **남아 있습니다**(인증서는 해지되거나 제거되지 않음).
  - 최종 사용자가 Intune 라이선스를 상실하는 경우
  - 관리자가 Intune 라이선스를 철회하는 경우
  - 관리자가 Azure AD에서 사용자 또는 그룹을 제거하는 경우
  - 관리자가 PKCS 프로필을 변경하거나 업데이트하는 경우

## <a name="android-knox-devices"></a>Android KNOX 디바이스

#### <a name="scep-certificates"></a>SCEP 인증서

- 다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.
  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우

- 다음과 같은 경우 SCEP 인증서가 해지됩니다.
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우
  - 디바이스는 Azure Active Directory(AD) 그룹에서 제거됩니다.
  - 인증서 프로필은 그룹 할당에서 제거됩니다.
  - 관리자가 Azure Active Directory(AD)에서 사용자 또는 그룹을 제거하는 경우
  - 관리자가 SCEP 프로필을 변경하거나 업데이트하는 경우

- 다음과 같은 경우 루트 인증서가 제거됩니다.
  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우

- 다음과 같은 경우 SCEP 인증서가 디바이스에 **남아 있습니다**(인증서는 해지되거나 제거되지 않음).
  - 최종 사용자가 Intune 라이선스를 상실하는 경우
  - 관리자가 Intune 라이선스를 철회하는 경우
  - 관리자가 Azure AD에서 사용자 또는 그룹을 제거하는 경우

#### <a name="pkcs-certificates"></a>PKCS 인증서

- 다음과 같은 경우 PKCS 인증서가 해지 *및* 제거됩니다.

  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우

- 다음과 같은 경우 루트 인증서가 제거됩니다.
  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [초기화](devices-wipe.md#wipe) 작업을 실행하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우

- 다음과 같은 경우 PKCS 인증서가 디바이스에 **남아 있습니다**(인증서는 해지되거나 제거되지 않음).
  - 최종 사용자가 Intune 라이선스를 상실하는 경우
  - 관리자가 Intune 라이선스를 철회하는 경우
  - 관리자가 Azure AD에서 사용자 또는 그룹을 제거하는 경우
  - 관리자가 PKCS 프로필을 변경하거나 업데이트하는 경우
  - 인증서 프로필은 그룹 할당에서 제거됩니다.
  
  
> [!NOTE]
> Android for work 디바이스는 위의 시나리오에 대해 유효성이 검사되지 않았습니다. Android 레거시 디바이스(삼성이 아닌 모든 비작업 프로필 디바이스)는 인증서를 제거할 수 없습니다. 

## <a name="macos-certificates"></a>macOS 인증서

#### <a name="scep-certificates"></a>SCEP 인증서

- 다음과 같은 경우 SCEP 인증서가 해지 *및* 제거됩니다.
  - 최종 사용자가 등록 취소하는 경우
  - 관리자가 [사용 중지](devices-wipe.md#retire) 작업을 실행하는 경우
  - 디바이스는 Azure Active Directory(AD) 그룹에서 제거됩니다.
  - 인증서 프로필은 그룹 할당에서 제거됩니다.

- 다음과 같은 경우 SCEP 인증서가 해지됩니다.
  - 관리자가 SCEP 프로필을 변경하거나 업데이트하는 경우

- 다음과 같은 경우 SCEP 인증서가 디바이스에 **남아 있습니다**(인증서는 해지되거나 제거되지 않음).
  - 최종 사용자가 Intune 라이선스를 상실하는 경우
  - 관리자가 Intune 라이선스를 철회하는 경우
  - 관리자가 Azure AD에서 사용자 또는 그룹을 제거하는 경우

> [!NOTE]
> [초기화](devices-wipe.md#wipe) 작업을 사용하여 macOS 장치를 초기화하는 기능은 지원되지 않습니다.

#### <a name="pkcs-certificates"></a>PKCS 인증서

PKCS 인증서는 macOS에서 지원되지 않습니다.

