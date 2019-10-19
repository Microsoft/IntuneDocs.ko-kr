---
title: MAM(모바일 앱 관리)
titleSuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 모바일 앱 관리 범주에 대한 항목을 참조하세요.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb1833a6a54fe0a7f78958e653468921df952b4d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505703"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>모바일 앱 관리(MAM) 엔터티에 대한 참조

**모바일 앱 관리** 범주에는 다음과 같은 모바일 앱에 대한 엔터티가 포함됩니다.

- 앱
- Instances
- 체크인 상태
- 상태
- 정책 상태
- 등록 상태
- 플랫폼 형식

## <a name="mamapplications"></a>mamApplications

**mamApplication** 엔터티는 회사에 등록하지 않고 MAM(모바일 앱 관리)을 통해 관리되는 LOB(기간 업무) 앱을 나열합니다.

| 속성 | 설명 | 예제 |
|---------|------------|--------|
| mamApplicationKey |MAM 애플리케이션의 고유 식별자입니다. | 432 |
| mamApplicationName |MAM 애플리케이션의 이름입니다. |MAM 애플리케이션 예제 이름 |
| mamApplicationId |MAM 애플리케이션의 애플리케이션 ID입니다. | 123 |
| isDeleted |이 MAM 앱 레코드가 업데이트되었는지 나타냅니다. <br>True-MAM 앱이 이 테이블에서 필드가 업데이트된 새 레코드를 가집니다. <br>False-이 MAM 앱의 최신 레코드입니다. |True/False |
| startDateInclusiveUTC |데이터 웨어하우스에서 해당 MAM 앱을 만든 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| deletedDateUTC |IsDeleted를 True로 변경한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC |데이터 웨어하우스에서 해당 MAM 앱을 마지막으로 수정한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |


## <a name="mamapplicationinstances"></a>mamApplicationInstances

**mamApplicationInstance** 엔터티는 디바이스별 사용자당 단일 인스턴스로서 관리되는 MAM(모바일 앱 관리)을 나열합니다. 엔터티 내 모든 사용자 및 디바이스에 MAM 정책이 하나 이상 할당되어 있으므로 모두 보호됩니다.


|          속성          |                                                                                                  설명                                                                                                  |               예제                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               데이터 웨어하우스의 MAM 앱 인스턴스에 대한 고유 식별자 - 서로게이트 키                                                                |                 123                  |
|           userId           |                                                                              해당 MAM 앱을 설치한 사용자의 사용자 ID                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              MAM 앱 인스턴스에 대한 고유 식별자 - ApplicationInstanceKey와 비슷하지만 자연 키입니다.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | 이 Mam 애플리케이션 인스턴스가 생성된 Mam 애플리케이션의 애플리케이션 ID입니다.   | 11/23/2016 12:00:00 AM   |
|     applicationVersion     |                                                                                     해당 MAM 앱의 애플리케이션 버전                                                                                      |                  2                   |
|        createdDate         |                                                                 MAM 앱 인스턴스의 이 레코드를 만든 날짜입니다. 값은 null일 수 있습니다.                                                                 |        11/23/2016 12:00:00 AM        |
|          플랫폼          |                                                                          해당 MAM 앱이 설치된 디바이스 플랫폼                                                                           |                  2                   |
|      platformVersion       |                                                                      해당 MAM 앱이 설치된 디바이스의 플랫폼 버전                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            해당 MAM 앱을 래핑한 MAM SDK 버전                                                                            |                 3.2                  |
| mamDeviceId | MAM 애플리케이션 인스턴스가 연결된 디바이스의 디바이스 ID입니다.   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | MAM 애플리케이션 인스턴스가 연결된 디바이스의 디바이스 유형입니다.   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | MAM 애플리케이션 인스턴스가 연결된 디바이스의 디바이스 이름입니다.   | 11/23/2016 12:00:00 AM   |
|         isDeleted          | 이 MAM 앱 인스턴스 레코드가 업데이트되었는지 나타냅니다. <br>True-이 MAM 앱 인스턴스는 이 테이블에서 필드가 업데이트된 새 레코드를 가집니다. <br>False-이 MAM 앱 인스턴스의 최신 레코드입니다. |              True/False              |
|   startDateInclusiveUtc    |                                                              데이터웨어 하우스에서 해당 MAM 앱 인스턴스를 만든 UTC 날짜 및 시간                                                               |        11/23/2016 12:00:00 AM        |
|       deletedDateUtc       |                                                                             IsDeleted를 True로 변경한 UTC 날짜 및 시간                                                                              |        11/23/2016 12:00:00 AM        |
| RowLastModifiedDateTimeUtc |                                                           데이터웨어 하우스에서 해당 MAM 앱 인스턴스를 마지막으로 수정한 UTC 날짜 및 시간                                                            |        11/23/2016 12:00:00 AM        |


## <a name="mamcheckins"></a>mamCheckins

**mamCheckin** 엔터티는 Intune 서비스를 사용하여 MAM(모바일 앱 관리) 앱 인스턴스가 체크인되었을 때 수집된 데이터를 나타냅니다. 

> [!Note]  
> 앱 인스턴스가 하루에 여러 번 체크인할 경우 데이터 웨어하우스는 이를 단일 체크인으로 저장합니다.

| 속성 | 설명 | 예제 |
|---------|------------|--------|
| dateKey |데이터 웨어하우스에서 MAM 앱 체크 인을 기록한 날짜 키 | 20160703 |
| applicationInstanceKey |해당 MAM 앱 체크 인에 연결된 앱 인스턴스의 키 | 123 |
| userKey |해당 MAM 앱 체크 인에 연결된 사용자의 키 | 4323 |
| mamApplicationKey |MAM 애플리케이션과 관련된 애플리케이션의 애플리케이션 키를 체크 인합니다. | 432 |
| deviceHealthKey |해당 MAM 앱 체크 인에 연결된 DeviceHealth의 키 | 321 |
| platformKey |해당 MAM 앱 체크 인에 연결된 디바이스의 플랫폼을 나타냅니다. |123 |
| effectiveAppliedPolicyKey |체크인된 MAM 앱과 연결된 발효된 적용 정책을 나타냅니다. 특정 앱 및 사용자와 관련된 모든 정책을 병합하여 얻은 발효된 적용 정책 결과입니다. | 322 |
| pastCheckInDate |이 MAM 앱이 마지막으로 체크인한 날짜와 시간입니다. 값은 null일 수 있습니다. |11/23/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>mamDeviceHealth

**mamDeviceHealth** 엔터티는 탈옥 디바이스라고 해도 MAM(모바일 앱 관리) 정책이 배포된 디바이스를 나타냅니다.

| 속성 | 설명 | 예제 |
|---------|------------|--------|
| deviceHealthKey |데이터 웨어하우스의 디바이스 및 관련 상태에 대한 고유 식별자 - 서로게이트 키 |123 |
| deviceHealth |디바이스 및 관련 상태에 대한 고유 식별자 - DeviceHealthKey와 비슷하지만 자연 키입니다 |b66bc706-ffff-7777-0340-032819502773 |
| deviceHealthName |디바이스 상태를 나타냅니다. <br>사용할 수 없음 - 이 디바이스에 대한 정보가 없습니다. <br>정상 - 디바이스가 탈옥되지 않았습니다. <br>비정상 - 디바이스가 탈옥되었습니다. |사용할 수 없음 정상 비정상 |
| RowLastModifiedDateTimeUtc |데이터 웨어하우스에서 해당 특정 MAM 디바이스 상태를 마지막으로 수정한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

**mamEffectivePolicy** 엔터티는 조직에 적용되는 모든 MAM(모바일 앱 관리) 실효 정책을 나열합니다. 특정 앱 및 사용자와 관련된 모든 정책을 병합하여 얻은 발효된 적용 정책 결과입니다.

| 속성 | 설명 | 예제 |
|---------|------------|--------|
| effectivePolicyKey |데이터 웨어하우스의 효과적인 MAM 정책에 대한 고유 식별자 |2 |
| realPolicyKey |IT Pro가 작성하는 MAM 정책의 고유 식별자입니다. |1 |
| rowCreatedDateTimeUtc |데이터 웨어하우스에서 MAM 실효 정책이 만들어진 UTC 날짜 및 시간입니다. |11/23/2016 12:00:00 AM |

## <a name="mamplatforms"></a>mamPlatforms

**mamPlatform** 엔터티는 MAM(모바일 앱 관리) 앱이 설치된 플랫폼 이름과 유형을 나열합니다.


|          속성          |                                    설명                                    |                         예제                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     데이터 웨어하우스의 플랫폼에 대한 고유 식별자 - 서로게이트 키      |                           123                           |
|          플랫폼          | 플랫폼에 대한 고유 식별자 - PlatformKey와 비슷하지만 자연 키입니다. |                           123                           |
|        platformName        |                                   플랫폼 이름                                   | 사용할 수 없음 <br>없음 <br>Windows <br>iOS <br>Android: |
| RowLastModifiedDateTimeUtc | 데이터 웨어하우스에서 해당 플랫폼을 마지막으로 수정한 UTC 날짜 및 시간  |                 11/23/2016 12:00:00 AM                  |

