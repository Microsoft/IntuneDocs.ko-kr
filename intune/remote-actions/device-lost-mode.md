---
title: Microsoft Intune-Azure를 사용하여 iOS 분실 모드 활성화 | Microsoft Docs
description: Microsoft Intune을 사용하여 분실되거나 도난당한 iOS 디바이스의 잠금 화면에서 표시하는 메시지를 사용자 지정하기 위해 분실 모드를 켜거나 시작합니다. 그리고 분실 모드 작업을 사용하는 경우 보안 및 개인 정보 취급 방침에 대한 세부 정보를 가져옵니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2956be9e32587c3bf86ce009a6927269c11ffced
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712228"
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Intune을 사용하여 iOS 디바이스에서 분실 모드 설정

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

**분실 모드** 디바이스 작업을 수행하면 분실했거나 도난당한 iOS 디바이스에 대해 분실 모드를 사용하도록 설정할 수 있습니다. 이 모드를 통해 디바이스의 잠금 화면에 표시되는 메시지 및 전화 번호를 입력할 수 있습니다. 디바이스에서 분실 모드를 사용하려면 감독 모드인 회사 소유 iOS 디바이스여야 합니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

- iOS 9.3 이상

다음에서는 이 기능이 지원되지 않습니다. 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>분실 모드 설정

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
3. **디바이스**를 선택한 다음, **모든 디바이스**를 선택합니다.
4. 관리하는 디바이스 목록에서 iOS 디바이스를 선택한 다음 **분실 모드(감독 모드만)** 를 선택합니다.
5. **분실 모드**에서 **사용**을 선택합니다.
6. **잠금 화면에서 표시할 메시지**에서 디바이스의 잠금 화면에 표시할 메시지를 입력합니다.
7. 필요에 따라 **표시할 전화 번호** 상자에 전화 번호를 입력합니다.
6. **확인**을 선택하여 변경 내용을 저장합니다.

분실 모드를 사용하도록 설정하면 모든 디바이스 사용이 차단됩니다. 분실 모드를 사용하지 않도록 설정할 때까지 최종 사용자는 디바이스에 액세스할 수 없습니다. 분실 모드가 설정된 동안 [디바이스 찾기](device-locate.md) 작업을 사용하여 디바이스를 찾을 수 있습니다.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>분실 모드의 보안 및 개인 정보와 디바이스 찾기 작업
- 이 작업을 켤 때까지 디바이스 위치 정보는 Intune에 전송되지 않습니다.
- 디바이스 찾기 작업을 사용하면 디바이스의 위도/경도 좌표가 Intune으로 전송되고 Azure Portal에 표시됩니다.
- 데이터는 24시간 동안 저장되었다가 제거됩니다. 위치 데이터를 수동으로 제거할 수 없습니다.
- 위치 데이터는 저장된 동안 및 전송되는 동안 모두 암호화됩니다.
- 잠금 화면에 표시하기 위해 입력한 메시지에서 분실 디바이스를 반환할 특정 세부 정보를 포함해야 합니다.

## <a name="next-steps"></a>다음 단계

분실 모드를 설정한 상태를 보려면 **디바이스**를 열고 **디바이스 작업**을 선택합니다.
