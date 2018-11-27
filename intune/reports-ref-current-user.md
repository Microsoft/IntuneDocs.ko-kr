---
title: 현재 사용자 - Intune 데이터 웨어하우스
titlesuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 사용자 범주에 대한 항목을 참조하세요.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: b58f6f360cf034be11153a57227da42ed1e29388
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189778"
---
# <a name="reference-for-current-user-entity"></a>현재 사용자 엔터티에 대한 참조

**현재 사용자** 범주에는 데이터 모델의 사용자 속성이 포함됩니다. **현재 사용자** 엔터티 컬렉션은 현재 활성 사용자로 제한됩니다. 엔터티에는 라이선스가 현재 할당된 모든 Azure Active Directory 사용자가 포함됩니다. 라이선스는 Intune 라이선스, 하이브리드 라이선스 또는 Microsoft Office 365 라이선스 일 수 있습니다. 제거된 사용자는 현재 사용자 컬렉션에 표시되지 않습니다. 사용자 상태의 변경 기록이 포함된 컬렉션의 경우 [사용자 엔터티에 대한 참조](reports-ref-user.md)를 참조하세요.


## <a name="current-user"></a>현재 사용자

**현재 사용자** 엔터티는 엔터프라이즈에서 할당된 라이선스를 가진 모든 Azure AD(Azure Active Directory) 사용자를 나열합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| UserKey |데이터 웨어하우스의 사용자에 대한 고유 식별자 - 서로게이트 키 |123 |
| UserId |사용자에 대한 고유 식별자 - UserKey와 비슷하지만 자연 키입니다. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |사용자의 이메일 주소 |John@constoso.com |
| UPN | 사용자의 사용자 계정 이름입니다. | John@constoso.com |
| DisplayName |사용자의 표시 이름 |John |
| IntuneLicensed |이 사용자의 Intune 라이선스 여부를 나타냅니다. |True/False |
| StartDateInclusiveUTC |데이터 웨어하우스에서 해당 사용자를 만든 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |데이터 웨어하우스에서 해당 사용자를 마지막으로 수정한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>다음 단계
 - **사용자** 엔터티 컬렉션을 사용하여 사용자 데이터를 현재 활성 상태가 아닌 사용자까지 확장할 수 있습니다. 자세한 내용은 [사용자 엔터티에 대한 참조](reports-ref-user.md)를 참조하세요.
 - 데이터 웨어하우스가 Intune에서 사용자의 수명을 추적하는 방법에 대한 자세한 내용은 [Intune 데이터 웨어하우스의 사용자 수명 표시](reports-ref-user-timeline.md)를 참조하세요.
