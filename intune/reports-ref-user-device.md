---
title: 사용자 장치 연결 - Intune 데이터 웨어하우스
titlesuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API의 변경 사항 목록입니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bd06c4d42de0c4f64ec0c0cfa61d8aa44af7ab95
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34224078"
---
# <a name="user-device-association"></a>사용자 장치 연결

**UserDeviceAssociation** 엔터티에는 조직의 사용자 장치 연결이 포함되어 있습니다.


|        이름        |                                           설명                                            |        예제         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              데이터 웨어하우스에서 사용자의 고유 식별자입니다. (서로게이트 키입니다.)               |          123           |
|     DeviceKey      |                      데이터 웨어하우스의 장치에 대한 고유 식별자                      |          123           |
| CreatedDateTimeUTC |           사용자 장치 연결을 만든 날짜 및 시간. UTC 형식을 사용합니다.           | 11/23/2016 12:00:00 AM |
|     IsDeleted      | 사용자가 해당 장치를 등록 취소했으며 연결이 현재 더 이상 존재하지 않음을 나타냅니다. |       True/False       |
|  EndedDateTimeUTC  |              IsDeleted를 <strong>True</strong>로 변경한 UTC 날짜 및 시간               | 06/23/2017 12:00:00 AM |

