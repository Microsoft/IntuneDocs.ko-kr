---
title: Microsoft Intune-Azure에서 디바이스 암호 다시 설정 | Micrososft Docs
description: Intune에서 관리하거나 모니터링하는 디바이스에서 암호 제거 작업을 사용하여 암호를 제거하거나 다시 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34aea5256ebb7d6577b4e77054dcca63d47bf317
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728587"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Intune에서 디바이스 암호 다시 설정 또는 제거

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

이 문서에서는 Android 엔터프라이즈(이전에는 Android for Work 또는 AfW라고 함) 디바이스에서의 디바이스 수준 암호 재설정과 회사 프로필 암호 재설정에 대해 설명합니다. 이러한 차이가 각 디바이스에 대한 요구 사항으로서 디바이스별로 다를 수 있다는 점을 인식하는 것이 중요합니다. 디바이스 수준 암호 재설정은 전체 디바이스에 대한 암호를 다시 설정합니다. 회사 프로필 암호 재설정은 Android 엔터프라이즈 디바이스에서 사용자의 회사 프로필에 대한 암호만 다시 설정합니다.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>디바이스 수준 암호 재설정을 위해 지원되는 플랫폼

| 플랫폼 | 지원 여부 |
| ---- | ---- |
| 버전 6.x 이하의 Android 디바이스 | 예 |
| 키오스크 모드의 Android 엔터프라이즈 디바이스 | 예 |
| iOS 디바이스 | 예 |
| 사용자 등록에 등록된 iOS 디바이스 | 아니요 |
| 작업 프로필에 등록된 Android 디바이스 | 아니요 |
| 버전 7.0 이상의 Android 디바이스 | 아니요 |
| macOS | 아니요 |
| Windows | 아니요 |

즉, Android 디바이스의 경우 해당 디바이스 수준 암호 재설정은 6.x 이하를 실행하는 디바이스 또는 키오스크 모드에서 실행되는 Android 엔터프라이즈 디바이스에서만 지원됩니다. Google이 디바이스 관리자가 부여한 앱 내에서 Android 7 디바이스의 암호 재설정에 대한 지원을 제거했으며, 모든 MDM 공급 업체에 적용되었기 때문입니다.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Android 엔터프라이즈 회사 프로필 암호 재설정에 대해 지원되는 플랫폼

| 플랫폼 | 지원 여부 |
| ---- | ---- |
| 회사 프로필에 등록되고 8.0 이상 버전을 실행 중인 Android 엔터프라이즈 디바이스 | 예 |
| 회사 프로필에 등록되고 7.x 이하 버전을 실행 중인 Android 엔터프라이즈 디바이스 | 아니요 |
| 7\.x 이하 버전을 실행 중인 Android 디바이스 | 아니요 |

새 회사 프로필 암호를 만들려면 암호 재설정 작업을 사용합니다. 이 작업은 암호 재설정 메시지를 표시하고 회사 프로필에만 사용할 새로운 임시 암호를 만듭니다. 

## <a name="reset-a-passcode"></a>암호 재설정


1. 다음 역할 중 하나를 사용하여 [Azure Portal](https://portal.azure.com)에 로그인합니다. Azure Active Directory 글로벌 관리자, Azure Active Directory Intune 서비스 관리자, 기술 지원팀 운영자 또는 역할 관리자.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링한 다음, **Microsoft Intune**을 선택합니다.
3. **디바이스**를 선택한 다음, **모든 디바이스**를 선택합니다.
4. 관리하는 디바이스 목록에서 디바이스를 선택하고 **자세히...** 를 선택합니다. 그런 다음, **암호 제거** 디바이스 원격 작업을 선택합니다.

## <a name="reset-android-work-profile-passcodes"></a>Android 회사 프로필 암호 다시 설정

회사 프로필에 등록된 지원되는 Android 엔터프라이즈 디바이스는 최종 사용자에 대한 관리되는 새 프로필 잠금 해제 암호 또는 관리되는 프로필 질문을 수신합니다.

8\.x 이상 버전을 실행 중이고 회사 프로필에 등록된 Android 엔터프라이즈 디바이스의 경우 등록이 완료된 직후에 재설정된 암호를 활성화한다는 알림이 최종 사용자에게 표시됩니다. 회사 프로필 암호가 필요하고 설정된 경우 알림이 표시됩니다. 암호를 입력하면 알림은 해제됩니다.


## <a name="remove-ios-passcodes"></a>iOS 암호 제거

다시 설정하는 대신 iOS 디바이스에서 암호가 제거됩니다. 암호 준수 정책이 설정되어 있는 경우 디바이스는 설정에서 새 암호를 설정하라는 메시지를 사용자에게 표시합니다.

## <a name="next-steps"></a>다음 단계

방금 수행한 작업의 상태를 확인하려면 **디바이스**에서 **디바이스 작업**을 선택합니다.
