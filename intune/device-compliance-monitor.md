---
title: 디바이스 준수 모니터링
titlesuffix: Microsoft Intune
description: 디바이스 준수를 모니터링하는 방법을 알아봅니다."
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b6c86b8f365f5ac3e65e91725e9fcd29ccd9ef58
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187026"
---
# <a name="monitor-device-compliance-in-intune"></a>Intune에서 디바이스 준수 모니터

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**개요** 블레이드에서 **준수 프로필**의 상태 요약을 볼 수 있습니다.
대화형으로 방식으로 차트를 클릭하여 세부 정보로 드릴다운할 수 있습니다. 여러 준수 프로 파일을 구성한 경우 **관리** > **보고서** 아래 정책 블레이드에서 정책 상태를 볼 수 있습니다.

##  <a name="device-compliance"></a>디바이스 정책 준수

디바이스 준수 보고서의 요약 보기에는 다음 중 하나로 보고되는 디바이스 수에 대한 집계된 정보가 표시됩니다.

- **규격**: 장치는 최근에 평가됐으며 지정한 준수 프로필 설정을 준수합니다.
- **비규격**: 장치가 평가되고 비규격으로 확인되었습니다.  프로필에 지정된 유예 기간이 있는 경우 유예 기간이 만료되어 디바이스가 비규격 상태가 되었습니다.
- **유예 기간**: 장치가 평가되고 비규격으로 확인되었습니다. 그러나 디바이스가 비규격으로 표시되기 전까지 유예 기간이 계속 적용됩니다.

각 섹션을 드릴다운하여 개별 디바이스 및 사용자에 대한 세부 정보를 확인할 수 있습니다.

## <a name="setting-compliance"></a>설정 준수

설정 준수 보고서에서는 다음과 같은 각 준수 설정에 대한 세부 정보를 제공합니다.

- 설정을 준수하지 않는 디바이스 수
- 설정이 적용되는 플랫폼

각 설정을 드릴다운하여 이러한 설정이 사용된 프로필 및 설정의 값에 대한 세부 정보를 확인할 수 있습니다.
