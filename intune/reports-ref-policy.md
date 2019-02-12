---
title: 정책 엔터티에 대한 참조
titlesuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 정책 범주에 대한 항목을 참조하세요.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08724e6e73d277a0d68155fb255a11ba68207b41
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842034"
---
# <a name="reference-for-policy-entities"></a>정책 엔터티에 대한 참조

**정책** 범주는 다음과 같은 정보를 추적하는 모바일 디바이스에 대한 엔터티를 포함합니다.

  -  디바이스 구성 프로필, 앱 구성 프로필 및 규정 준수 정책의 인벤토리  
  -  하루에 성공, 보류, 실패, 또는 오류 상태에 있는 디바이스의 수  
  -  하루에 성공, 보류, 실패, 또는 오류 상태에 있는 사용자의 수  
  -  성공, 보류, 실패, 또는 오류 상태에 있는 디바이스의 누적 수  

## <a name="policy"></a>정책

**정책** 엔터티는 디바이스 구성 프로필, 앱 구성 프로필 및 규정 준수 정책을 나열합니다. 정책을 MDM(Mobile Device Management)을 통해 기업 내 그룹에 할당할 수 있습니다.

| 속성  | 설명 | 예 |
|---------|------------|--------|
| PolicyKey |데이터 웨어하우스에서 정책을 나타내는 고유 키 |123 |
| PolicyId |데이터 웨어하우스의 정책에 대한 고유 식별자 |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |정책 이름 |"Windows 10 Baseline" |
| PolicyVersion |정책 버전 정책이 편집, 변경되었거나 새 버전이 만들어진 날짜입니다. |1, 2, 3 |
| IsDeleted |정책 레코드가 업데이트되었는지 나타냅니다.  <br>True - 정책에 업데이트된 필드를 포함한 새 레코드가 있습니다. <br>False- 정책에 대한 최신 레코드입니다. |True/False |
| StartDateInclusiveUTC |데이터 웨어하우스에서 정책을 만든 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| DeletedDateUTC |IsDeleted를 True로 변경한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |데이터 웨어하우스에서 정책을 마지막으로 수정한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |

## <a name="policytype"></a>PolicyType

**PolicyType** 엔터티는 디바이스 구성 프로필, 앱 구성 프로필 및 규정 준수 정책 유형을 나열합니다. 정책을 MDM(Mobile Device Management)을 통해 기업 내 그룹에 할당할 수 있습니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| PolicyTypeId |원본 시스템의 정책에 대한 고유 식별자 |123 |
| PolicyTypeKey |데이터 웨어하우스의 정책에 대한 고유 식별자 |1 |
| PolicyTypeName |정책 형식의 이름입니다. |Windows 10 준수 정책 |

## <a name="deviceconfiguration"></a>DeviceConfiguration

**DeviceConfigurationProfileDeviceActivity** 엔터티는 하루에 성공, 보류, 실패 또는 오류 상태에 있는 디바이스의 수를 나열합니다. 숫자는 엔터티에 할당된 디바이스 구성 프로필을 반영합니다. 예를 들어 디바이스가 모든 할당된 정책에 대해 성공 상태에 있으면 그 날에 대해 성공 카운터를 1만큼 높입니다. 디바이스에 두 프로필이 할당된 경우(성공 상태에 하나, 오류 상태에 하나) 엔터티는 성공 카운터를 하나 늘리고 디바이스를 오류 상태에 놓습니다. 엔터티는 지난 30일 동안 특정 날짜에 해당 상태에 있는 디바이스가 몇 개인지 표시합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| DateKey |데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키 |20160703 |
| Pending |보류 중 상태에 있는 고유 디바이스의 수 |123 |
| 성공 |성공 상태에 있는 고유 디바이스의 수 |12 |
| 오류 |오류 상태에 있는 고유 디바이스의 수 |10 |
| Failed |실패 상태에 있는 고유 디바이스의 수 |2 |



**DeviceConfigurationProfileUserActivity** 엔터티는 하루에 성공, 보류, 실패, 오류 상태에 있는 사용자 수를 표시합니다. 숫자는 엔터티에 할당된 디바이스 구성 프로필을 반영합니다. 예를 들어 사용자가 모든 할당된 정책에 대해 성공 상태에 있으면 해당 날짜에 대한 성공 카운터를 1만큼 높입니다. 사용자에게 두 프로필이 할당된 경우(하나는 성공 상태, 하나는 오류 상태) 오류 상태의 사용자를 카운트합니다.  **DeviceConfigurationProfileUserActivity** 엔터티는 지난 30일 동안 특정 날짜에 해당 상태에 있는 사용자 수를 표시합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| DateKey |데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키 |20160703 |
| Pending |보류 중 상태에 있는 고유 사용자 수 |123 |
| 성공 |성공 상태에 있는 고유 사용자 수 |12 |
| 오류 |오류 상태에 있는 고유 사용자 수 |10 |
| Failed |실패 상태에 있는 고유 사용자 수 |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

**PolicyTypeActivity** 엔터티는 성공, 보류, 실패 또는 오류 상태에 있는 디바이스의 누적 수를 표시합니다. 하루의 디바이스 구성 프로필, 앱 구성 프로필, 규정 준수 정책에 대한 상태를 표시합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| DateKey |데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키 |20160703 |
| PolicyKey |정책 키 - Policy와 조인하여 policyName을 가져올 수 있습니다. |Windows 10 기준 |
| PolicyTypeKey |정책 키 유형 - PolicyType과 조인하여 정책 유형 이름을 가져올 수 있습니다. |Windows10 준수 정책 |
| Pending |보류 중 상태에 있는 고유 디바이스의 수 |123 |
| 성공 |성공 상태에 있는 고유 디바이스의 수 |12 |
| 오류 |오류 상태에 있는 고유 디바이스의 수 |10 |
| Failed |실패 상태에 있는 고유 디바이스의 수 |2 |

## <a name="compliance-policy"></a>준수 정책

규정 준수 정책 API 참조에는 디바이스에 할당된 규정 준수 정책에 대한 상태 정보를 제공하는 엔터티가 포함됩니다.

### <a name="compliancepolicystatusdeviceactivities"></a>CompliancePolicyStatusDeviceActivities

다음 표는 디바이스에 준수 정책 할당 상태를 요약하여 보여줍니다. 각 준수 상태에서 찾을 수 있는 디바이스 수를 표시합니다.


|속성     |설명  |예제  |
|---------|---------|---------|
|DateKey  |규정 준수 정책에 대한 요약을 만들 때의 Datekey.|20161204 |
|Unknown  |오프라인이거나 다른 이유로 인해 Intune 또는 Azure AD와 통신하지 못한 디바이스의 수. |5|
|NotApplicable      |관리자가 대상으로 지정한 디바이스 규정 준수 정책을 적용할 수 없는 디바이스 수.|201 |
|규정      |관리자가 대상으로 지정한 하나 이상의 디바이스 준수 정책 설정이 성공적으로 적용된 디바이스 수. |4083 |
|InGracePeriod      |관리자가 정의한 유예 기간에 있지만 해당 규정을 준수하지 않은 디바이스 수. |57|
|NonCompliant      |관리자가 대상으로 지정한 하나 이상의 디바이스 준수 정책이 디바이스에서 적용되지 않았거나, 관리자가 대상으로 지정한 정책을 사용자가 준수하지 않는 디바이스 수.|43 |
|오류      |Intune 또는 Azure AD와 통신하지 못하고 오류 메시지가 반환한 디바이스 수. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>CompliancePolicyStatusDevicePerPolicyActivities 

다음 표는 정책별 및 정책 유형별 기반 위에 디바이스에 준수 정책 할당 상태를 요약하여 보여줍니다. 각 할당된 준수 정책에 대한 각 준수 상태에서 찾을 수 있는 디바이스 수를 표시합니다.



|속성  |설명  |예제  |
|---------|---------|---------|
|DateKey  |규정 준수 정책에 대한 요약을 만들 때의 Datekey.|20161219|
|PolicyKey     |요약이 생성된 규정 준수 정책에 대한 키. |10178 |
|PolicyPlatformKey      |요약이 생성된 규정 준수 정책의 플랫폼 형식에 대한 키.|5|
|Unknown     |오프라인이거나 다른 이유로 인해 Intune 또는 Azure AD와 통신하지 못한 디바이스의 수.|13|
|NotApplicable     |관리자가 대상으로 지정한 디바이스 규정 준수 정책을 적용할 수 없는 디바이스 수.|3|
|규정      |관리자가 대상으로 지정한 하나 이상의 디바이스 준수 정책 설정이 성공적으로 적용된 디바이스 수. |45|
|InGracePeriod      |관리자가 정의한 유예 기간에 있지만 해당 규정을 준수하지 않은 디바이스 수. |3|
|NonCompliant      |관리자가 대상으로 지정한 하나 이상의 디바이스 준수 정책이 디바이스에서 적용되지 않았거나, 관리자가 대상으로 지정한 정책을 사용자가 준수하지 않는 디바이스 수.|7|
|오류      |Intune 또는 Azure AD와 통신하지 못하고 오류 메시지가 반환한 디바이스 수. |3|

### <a name="policyplatformtypes"></a>PolicyPlatformTypes

다음 표에는 모든 할당된 정책의 플랫폼 형식이 들어 있습니다. 어떤 디바이스에도 할당되지 않은 정책 플랫폼 형식은 이 표에 들어 있지 않습니다.


|속성  |설명  |예제  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |정책 플랫폼 형식에 대한 고유 키입니다. |20170519 |
|PolicyPlatformTypeId      |정책 플랫폼 형식에 대한 고유 식별자입니다.|1|
|PolicyPlatformTypeName      |정책 플랫폼 형식에 대한 이름입니다.|AndroidForWork |

### <a name="policydeviceactivity"></a>PolicyDeviceActivity

다음 표는 하루에 성공, 보류, 실패 또는 오류 상태에 있는 디바이스의 수를 나열합니다. 수는 데이터별 정책 유형 프로필을 반영합니다. 예를 들어 디바이스가 모든 할당된 정책에 대해 성공 상태에 있으면 그 날에 대해 성공 카운터를 1만큼 높입니다. 디바이스에 두 프로필이 할당된 경우(성공 상태에 하나, 오류 상태에 하나) 엔터티는 성공 카운터를 하나 늘리고 디바이스를 오류 상태에 놓습니다. PolicyDeviceActivity 엔터티는 지난 30일 동안 특정 날짜에 해당 상태에 있는 디바이스가 몇 개인지 표시합니다.

|속성  |설명  |예제  |
|---------|---------|---------|
|DateKey|데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키|20160703|
|Pending|보류 중 상태에 있는 고유 디바이스의 수|123|
|성공|성공 상태에 있는 고유 디바이스의 수|12|
PolicyKey|정책 키 - Policy와 조인하여 policyName을 가져올 수 있습니다.|Windows 10 기준|
|오류|오류 상태에 있는 고유 디바이스의 수|10|
|Failed|실패 상태에 있는 고유 디바이스의 수|2|

### <a name="policyuseractivity"></a>PolicyUserActivity 

다음 표는 하루에 성공, 보류, 실패 또는 오류 상태에 있는 사용자 수를 나열합니다. 수는 데이터별 정책 유형 프로필을 반영합니다. 예를 들어 사용자가 모든 할당된 정책에 대해 성공 상태에 있으면 해당 날짜에 대한 성공 카운터를 1만큼 높입니다. 사용자에게 두 프로필이 할당된 경우(하나는 성공 상태, 하나는 오류 상태) 오류 상태의 사용자를 카운트합니다. PolicyUserActivity 엔터티는 지난 30일 동안 특정 날짜에 해당 상태에 있는 장치가 몇 개인지 표시합니다.


| 속성  |                                         설명                                         |       예제       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  DateKey  | 데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키 |      20160703       |
|  Pending  |                         보류 중 상태에 있는 고유 디바이스의 수                          |         123         |
| 성공 |                         성공 상태에 있는 고유 디바이스의 수                          |         12          |
| PolicyKey |                정책 키 - Policy와 조인하여 policyName을 가져올 수 있습니다.                 | Windows 10 기준 |
|   오류   |                          오류 상태에 있는 고유 디바이스의 수                           |         10          |

