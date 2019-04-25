---
title: 개인 데이터 보기 및 수정
description: 개인 데이터를 보고 수정하는 방법에 대해 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1ba77bc7-505e-4eca-a49e-dcdaa75d0043
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d0567d605afeb37812d495cc6192100ab76444f
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511630"
---
# <a name="view-and-correct-personal-data"></a>개인 데이터 보기 및 수정

Intune 관리자는 액세스 권한을 기반으로 일부 개인 데이터를 볼 수 있지만 최종 사용자만 디바이스의 개인 데이터를 변경할 수 있습니다.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-dsr-and-stp-note.md)]


## <a name="view-personal-data"></a>개인 데이터 보기

관리자는 Intune UI의 다양한 블레이드에서 최종 사용자의 개인 정보를 볼 수 있습니다. 다음 문서에서는 관리자가 액세스할 수 있는 정보와 액세스할 수 없는 정보에 대해 설명합니다.
- Intune의 [디바이스 세부 정보 보기](device-inventory.md)는 최종 사용자의 디바이스에 대한 세부 정보를 검토하는 방법을 설명합니다.
- [앱 정보 및 할당 모니터링](apps-monitor.md)은 최종 사용자의 디바이스에 설치된 앱에 대한 세부 정보를 확인하는 방법을 설명합니다.
- [디바이스를 등록하면 회사에 어떤 정보가 표시되나요? 문서](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)는 최종 사용자에게 회사에서 볼 수 있거나 없는 데이터 목록을 제공합니다. 수집하는 데이터의 종류와 수집 이유를 사용자에게 명확하게 알리는 것이 가장 좋습니다. 이 문서는 투명성의 첫 번째 단계가 될 수 있습니다.

### <a name="who-can-view-the-data"></a>누가 데이터를 볼 수 있습니까?

Microsoft는 엄격한 제어를 통해 고객 데이터에 대한 액세스를 제어하여 주요 작업을 완료하는 데 필요한 최소한의 액세스 권한을 제공하고 더 이상 필요하지 않을 때 액세스 권한을 취소합니다. 

RBAC(역할 기반 관리 제어)를 사용하여 최종 사용자 개인 데이터에 대한 액세스를 보호하고 제어할 수 있습니다. 자세한 내용은 [Microsoft Intune과 RBAC](role-based-access-control.md)를 참조하세요.

온라인 서비스 사용 약관 및 [Microsoft Online Services 개인정보처리방침](http://go.microsoft.com/fwlink/p/?linkid=131004&clcid=0x409)을 읽으면 Microsoft 데이터 방침에 대해 자세히 알아볼 수 있습니다. 

## <a name="correct-end-user-personal-data"></a>최종 사용자 개인 데이터 수정

관리자는 디바이스 또는 앱 관련 정보를 업데이트할 수 없습니다. 최종 사용자가 디바이스 이름과 같은 개인 데이터를 수정하려면 해당 디바이스에서 직접 수정해야 합니다. 이러한 변경 내용은 다음에 Intune에 연결할 때 동기화됩니다.


## <a name="next-steps"></a>다음 단계

Intune의 개인 데이터 [감사, 내보내기 또는 삭제](privacy-data-audit-export-delete.md) 방법에 대해 알아봅니다.
