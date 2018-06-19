---
title: Exchange에서 관리하는 모바일 장치 초기화
description: Microsoft Intune을 사용하면 Intune Exchange Connector를 통해 EAS(Exchange ActiveSync)를 사용하여 관리되는 모바일 장치를 초기화하거나 재설정할 수 있습니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 753e5e9dac7199dff18d110808524f05aa669036
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31016087"
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Wipe for Exchange-managed mobile devices

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune을 사용하면 Intune Exchange Connector를 통해 EAS(Exchange ActiveSync)를 사용하여 관리되는 모바일 장치를 초기화하거나 재설정할 수 있습니다. 다음 표에서는 Exchange ActiveSync를 통해 사용할 수 있는 초기화 기능을 설명합니다.


|      초기화 유형       |              Windows 8.1 및 Windows RT 8.1              |                            iOS                             |                          Android                          |
|-------------------------|----------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|        전체 초기화        |          메일 계정 및 캐시된 메일 제거           |                      공장 기본 설정                       |                      출하 시 설정으로 초기화                       |
|  선택적 초기화/메일   |                  메일 계정을 제거합니다.                  |                       지원 안 됨                       |                      지원 안 됨                       |
| 선택적 초기화/정책 | 정책 적용이 제거되지만 설정은 변경되지 않음 | 정책 적용이 제거되지만 설정은 변경되지 않음 | 정책 적용이 제거되지만 설정은 변경되지 않습니다. |

