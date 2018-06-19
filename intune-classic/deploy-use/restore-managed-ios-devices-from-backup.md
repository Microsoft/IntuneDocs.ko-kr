---
title: Intune 관리 iOS 장치를 백업에서 복원
description: 백업에서 복원한 후 해당 장치를 다시 등록하는 방법에 대한 지침을 최종 사용자에게 제공합니다.
keywords: 복원, 관리되는, iOS
author: lenewsad
ms.author: lanewsad
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2c2a35a7faa022ab2b9b095d4a08075e1c338c70
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022682"
---
# <a name="restore-intune-managed-ios-devices-from-backup"></a>Intune 관리 iOS 장치를 백업에서 복원

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

새 장치를 가져오는 경우와 같이 사용자가 iOS 장치를 백업에서 복원해야 할 경우가 있습니다. 이 항목에서는 장치를 복원한 후 Intune 관리 설정을 위해 수행해야 할 추가 단계를 설명합니다.

## <a name="restoring-backups-onto-the-same-device"></a>동일한 장치에 백업 복원

동일한 장치에서 백업을 복원 중인 경우 해당 장치에서 등록 상태도 복원됩니다. 추가 작업이 필요하지 않습니다.

## <a name="restoring-backups-onto-different-devices"></a>다른 장치에 백업 복원

동일한 장치에서 백업을 복원 중인 경우 등록 상태는 새 장치에 자동으로 복원됩니다. [Intune으로 iOS 장치를 등록](/intune-user-help/enroll-your-device-in-intune-ios)하려면 사용자가 앱 버전 2.1.22 이상의 회사 포털 앱에서 표준 등록 단계를 수행해야 합니다.

> [!NOTE]
> 조건부 액세스 정책을 사용하여 최종 사용자를 대상으로 지정하는 경우 다시 등록될 때까지 회사 메일에 액세스할 수 없게 됩니다.

> [!TIP]
> 사용자에 대한 통신 예제로는 새 장치 등록을 위해 회사 포털 앱이 버전 2.1.22 이상인지 확인해야 하는 경우가 있습니다. 버전을 확인하려면 회사 포털 앱을 열고, 오른쪽 위에 있는 메뉴 단추를 탭한 다음 정보를 탭합니다. 이전 버전인 경우 회사 포털 앱을 종료하고 앱 스토어를 엽니다. 오른쪽 아래 모서리에서 업데이트 단추를 탭한 다음 목록에서 회사 포털 항목 옆에 있는 업데이트 단추를 탭합니다. 업데이트가 완료되면 회사 포털 앱을 시작하고 [Intune에 iOS 장치를 등록](/intune-user-help/enroll-your-device-in-intune-ios)합니다.

## <a name="resolving-known-issues-with-restores"></a>복원 시 알려진 문제 해결

아직도 회사 포털 버전 2.1.21 이전 버전을 사용하고 있는 경우 장치를 복원하고 회사 포털 앱을 시작할 때 문제가 발생할 수 있습니다. 사용자의 상황에 맞는 단계를 수행하여 이러한 문제를 해결할 수 있습니다.

### <a name="for-users-who-will-only-use-their-new-device"></a>새 장치만 사용하는 사용자
회사 포털 앱을 시작하고 현재 장치 타일을 선택한 후 __제거__ 단추를 탭하여 등록을 취소합니다. 제거한 후에는 표준 등록 단계에 따라 [Intune에 iOS 장치를 등록](/intune-user-help/enroll-your-device-in-intune-ios)합니다.

### <a name="for-users-who-will-use-both-their-old-and-new-devices"></a>이전 장치와 새 장치를 모두 사용하는 사용자
Safari에서 쿠키를 기반으로 선택 취소 __설정__ > __Safari__ > __Clear History and Website Data__(기록 및 웹 사이트 데이터 지우기)를 탭하여 Safari에서 쿠키를 지웁니다. 지운 후에는 회사 포털 앱을 제거했다가 다시 설치하고 표준 등록 단계에 따라 [Intune에 iOS 장치를 등록](/intune-user-help/enroll-your-device-in-intune-ios)합니다.
