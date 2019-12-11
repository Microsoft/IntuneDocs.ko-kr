---
title: 특별 마이그레이션 고려 사항
titleSuffix: Microsoft Intune
description: 이 문서는 Microsoft Intune에 대한 마이그레이션 캠페인을 시작하기 전에 특별 마이그레이션 고려 사항을 제공합니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86cef30c31b53c6bfd1873390fb7546cbeab2a53
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72510029"
---
# <a name="special-migration-considerations"></a>특별 마이그레이션 고려 사항

기존 MDM 공급자 환경에 따라 적용될 수 있는 특별 마이그레이션 고려 사항이 있습니다.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Apple의 DEP(장비 등록 프로그램)에 대한 초기화

Apple DEP(디바이스 등록 프로그램)는 최종 사용자가 제거할 수 없는 디바이스 구성을 설정합니다. DEP의 고급 관리 기능을 유지하려면 초기화를 통해 디바이스를 기본(신규) 상태로 되돌리고 Intune에 등록해야 합니다.

계속해서 DEP를 사용하여 Intune에서 디바이스를 관리하려면 [디바이스 등록 프로그램을 사용하여 iOS 디바이스 등록을 설정](../enrollment/device-enrollment-program-enroll-ios.md)합니다.


## <a name="next-steps"></a>다음 단계

[2단계: 마이그레이션 캠페인](../migration-guide-campaign.md)
