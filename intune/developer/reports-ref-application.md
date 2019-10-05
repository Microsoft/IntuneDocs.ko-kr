---
title: 애플리케이션 엔터티에 대한 참조
titleSuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 애플리케이션 범주에 대한 항목을 참조하세요.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e737f1cce594b5dd40b2f43048ba37578f5d7c9
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940432"
---
# <a name="reference-for-application-entities"></a>애플리케이션 엔터티에 대한 참조

**애플리케이션** 범주는 다음과 같은 정보를 추적하는 모바일 디바이스에 대한 엔터티를 포함합니다.

- 앱 버전
- 앱의 설치 원본
- 앱을 만든 개발자의 유형
- 앱에 대한 관리되는 소프트웨어 유형. 예: **사이드카** 또는 **데스크톱**
- 앱의 VPP(Volume Purchasing Program) 상태

## <a name="apprevisions"></a>appRevisions

**appRevision** 엔터티는 앱의 모든 버전을 나열합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| appKey |앱에 대한 고유 식별자 |123 |
| applicationId |앱의 고유 식별자 - AppKey와 유사하지만 이 키는 자연어입니다. |b66bc706-ffff-7437-0340-032819502773 |
| 수정 |이진 파일을 업로드하는 동안 관리자가 설명한 버전 |2 |
| title |앱의 제목 |Excel |
| 게시자 |앱의 게시자 |Microsoft |
| uploadState |앱의 업로드 상태 |1 |
| appTypeKey |다음 섹션에 설명된 AppType에 대한 참조입니다. | |
| vppProgramTypeKey |아래에 설명된 VppProgramType에 대한 참조 | |
| creationTime |해당 수정 버전을 만든 시간 |11/23/2016 12:00:00 AM |
| modifiedTime |해당 수정 버전과 관련된 항목을 마지막으로 변경한 시간 |11/23/2016 12:00:00 AM |
| 크기 |이진 파일의 크기 | |
| startDateInclusiveUTC |데이터 웨어하우스에서 해당 앱의 수정 버전을 만든 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| endDateExclusiveUTC |해당 앱의 수정 버전이 더 이상 사용되지 않는 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| isCurrent |해당 앱의 수정 버전이 데이터 웨어하우스에 있는지 여부를 나타냅니다. |True/False |
| rowLastModifiedDateTimeUTC |데이터 웨어하우스에서 해당 앱의 버전을 마지막으로 수정한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>appTypes

**appType** 엔터티는 앱의 설치 원본을 나열합니다.

| 속성  | 설명 |
|---------|------------|
| appTypeID |형식에 대한 ID |
| appTypeKey |키에 대한 대리 키 |
| appTypeName |앱 유형 |

### <a name="example"></a>예제

| AppTypeID  | 이름 | 설명 |
|---------|------------|--------|
| 0 |Android 스토어 앱 | Android 스토어 앱 |
| 1 |Android LOB 앱 | Android 기간 업무 앱 |
| 2 |관리되는 Android 스토어 앱(MAM) | 관리를 사용하도록 설정된 Android 스토어 앱 |
| 3 |iOS 스토어 앱 | iOS 스토어 앱 |
| 4 |iOS LOB 앱 | iOS 기간 업무 앱 |
| 5 |관리되는 iOS 스토어 앱(MAM?) | 관리를 사용하도록 설정된 iOS 스토어 앱 |
| 6 |O365 Pro Plus 도구 모음 | Windows 10용 Office 365 Pro Plus 제품군 |
| 7 |웹앱 | 웹앱 |
| 8 |Windows Phone 8.1 스토어 앱 | Windows Phone 8.1 스토어 앱 |
| 9 |Windows 스토어 앱 | Windows 스토어 앱 |
| 10 |Windows LOB 앱 | Windows AppX 기간 업무 앱 |
| 11 |Windows Mobile MSI | MSI 기간 업무 앱 |
| 12 |Windows Phone LOB 앱 | Windows Phone 기간 업무 앱 |


## <a name="vppprogramtypes"></a>vppProgramTypes

**vppProgramType** 엔터티는 앱에 대해 가능한 VPP 프로그램 유형을 나열합니다.

| 속성  | 설명 |
|---------|------------|
| VppProgramTypeID | 형식에 대한 ID |
| vppProgramTypeKey | 키에 대한 서로게이트 키 |
| vppProgramTypeName | VPP 프로그램 유형 |

### <a name="example"></a>예제

| VppProgramID  | 이름 | 설명 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsoft의 VPP 프로그램 |
| 00000000-0000-0000-0000-000000000000 | 아직 사용할 수 없음 | 기본값, VPP 없음 |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apple의 VPP 프로그램 |



## <a name="applicationinventories"></a>applicationInventories

**applicationInventory** 엔터티는 인벤토리 수집 시점에 디바이스에서 발견된 애플리케이션을 나열합니다.

| 속성  | 설명 |
|---------|------------|
| deviceKey | Intune 디바이스 ID가 포함된 디바이스 테이블에 대한 참조 |
| dateKey | 인벤토리의 날짜를 가리키는 날짜 테이블에 대한 참조 |
| applicationName | 애플리케이션 이름입니다. |
| applicationVersion | 애플리케이션의 버전 |
| bundleSize | 응용 프로그램의 크기(바이트) |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

**mobileAppInstallState** 엔터티는 디바이스, 사용자 또는 둘 다를 포함하는 그룹에 할당된 후 모바일 애플리케이션의 설치 상태를 나타냅니다.

| 속성 | 설명 |
|---|---|
| appInstallStateKey | 계정에 대한 앱 설치 상태의 고유 ID입니다. |
| appInstallState | 앱 설치 상태의 열거형 값입니다. |
| appInstallStateName | 앱 설치 상태의 이름입니다. |



