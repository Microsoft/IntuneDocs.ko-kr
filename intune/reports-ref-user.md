---
title: 사용자 - Intune 데이터 웨어하우스
titlesuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 사용자 범주에 대한 항목을 참조하세요.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11c3cc35408b2d50e781c50cd1821b8cead19ad7
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57232389"
---
# <a name="reference-for-user-entity"></a>사용자 엔터티 참조

**사용자** 범주에는 데이터 모델의 사용자 속성을 정의하는 **사용자** 엔터티가 포함됩니다.

## <a name="user"></a>사용자

**사용자** 엔터티는 회사 내 할당된 라이선스가 있는 모든 Azure Active Directory(Azure AD) 사용자를 나열합니다.

**사용자** 엔터티 컬렉션에는 사용자 데이터가 포함됩니다. 이러한 레코드에는 사용자가 제거된 경우에도 데이터 컬렉션 기간의 사용자 상태가 포함됩니다. 예를 들어, 사용자가 Intune에 추가된 다음 지난달 중에 제거되었을 수 있습니다. 보고 시점에는 이 사용자가 없지만 이전 달의 데이터에는 사용자와 상태가 있습니다. 데이터에 있는 사용자의 현재 상태 기록에 대한 기간을 보여 주는 보고서를 만들 수 있습니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| UserKey |데이터 웨어하우스의 사용자에 대한 고유 식별자 - 서로게이트 키 |123 |
| UserId |사용자에 대한 고유 식별자 - UserKey와 비슷하지만 자연 키입니다. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |사용자의 이메일 주소 |John@constoso.com |
| UPN | 사용자의 사용자 계정 이름입니다. | John@constoso.com |
| DisplayName |사용자의 표시 이름 |John |
| IntuneLicensed |이 사용자의 Intune 라이선스 여부를 나타냅니다. |True/False |
| IsDeleted | 사용자의 모든 라이선스가 만료되었는지 여부와 이에 따라 사용자가 Intune에서 제거되었는지 여부를 나타냅니다. 단일 레코드의 경우 이 플래그는 변경되지 않습니다. 대신 새 사용자 상태에 대한 새 레코드가 만들어집니다. |True/False |
| StartDateInclusiveUTC |IsDeleted = FALSE인 경우 사용자에게 라이선스가 할당되고 Intune에 현재 상태를 포함하기 시작한 날짜/시간(UTC)입니다. IsDeleted = TRUE인 경우 사용자의 라이선스가 만료되었고 사용자가 Intune에서 제거된 날짜/시간(UTC)입니다. |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |IsDeleted = FALSE인 경우 사용자의 라이선스가 만료되었고 사용자가 Intune에서 제거된 날짜/시간(UTC)입니다. 라이선스가 전날 만료되었습니다. IsDeleted = TRUE인 경우 사용자가 새 라이선스를 다시 얻었고 Intune에서 다시 만들어진 날짜/시간(UTC)입니다.  |11/23/2016 12:00:00 AM |
| IsCurrent |이 레코드가 사용자의 최신 상태를 나타내는지 여부를 나타냅니다. 단일 사용자에 대해 여러 레코드가 존재할 수 있지만 이 중 하나만 현재 상태를 나타냅니다.  |True/False |
| RowLastModifiedDateTimeUTC |데이터 웨어하우스에서 레코드를 마지막으로 수정한 날짜 및 시간(UTC)  |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>다음 단계
 - **현재 사용자** 엔터티 컬렉션을 사용하여 사용자 데이터를 현재 활성 상태인 사용자로 제한할 수 있습니다. 자세한 내용은 [현재 사용자 엔터티에 대한 참조](reports-ref-current-user.md)를 참조하세요.
 - 데이터 웨어하우스가 Intune에서 사용자의 수명을 추적하는 방법에 대한 자세한 내용은 [Intune 데이터 웨어하우스의 사용자 수명 표시](reports-ref-user-timeline.md)를 참조하세요.
