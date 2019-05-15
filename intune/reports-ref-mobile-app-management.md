---
title: MAM(모바일 앱 관리)
titleSuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 모바일 앱 관리 범주에 대한 항목을 참조하세요.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 456abbf849120675b6a7c108ca65c6f9967ae64a
ms.sourcegitcommit: 601327125ac8ae912d8159422de8aac7dbdc25f6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59429202"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>모바일 앱 관리(MAM) 엔터티에 대한 참조

**모바일 앱 관리** 범주에는 다음과 같은 모바일 앱에 대한 엔터티가 포함됩니다.

  -  앱
  -  Instances
  -  체크인 상태
  -  상태
  -  정책 상태
  -  등록 상태
  -  플랫폼 형식

## <a name="mamapplication"></a>MamApplication

**MamApplication** 엔터티는 회사에 등록하지 않고 모바일 앱 관리(MAM)를 통해 관리되는 LOB(기간 업무) 앱을 나열합니다.

| 속성 | 설명 | 예제 |
|---------|------------|--------|
| mamApplicationKey |MAM 애플리케이션의 고유 식별자입니다. | 432 |
| mamApplicationName |MAM 애플리케이션의 이름입니다. |MAM 애플리케이션 예제 이름 |
| mamApplicationId |MAM 애플리케이션의 애플리케이션 ID입니다. | 123 |
| IsDeleted |이 MAM 앱 레코드가 업데이트되었는지 나타냅니다. <br>True-MAM 앱이 이 테이블에서 필드가 업데이트된 새 레코드를 가집니다. <br>False-이 MAM 앱의 최신 레코드입니다. |True/False |
| StartDateInclusiveUTC |데이터 웨어하우스에서 해당 MAM 앱을 만든 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| DeletedDateUTC |IsDeleted를 True로 변경한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |데이터 웨어하우스에서 해당 MAM 앱을 마지막으로 수정한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |


## <a name="mamapplicationinstance"></a>MamApplicationInstance

**MamApplicationInstance** 엔터티는 디바이스별 사용자당 단일 인스턴스로서 관리되는 모바일 앱 관리(MAM) 앱을 나열합니다. 엔터티 내 모든 사용자 및 디바이스에 MAM 정책이 하나 이상 할당되어 있으므로 모두 보호됩니다.


|          속성          |                                                                                                  설명                                                                                                  |               예제                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               데이터 웨어하우스의 MAM 앱 인스턴스에 대한 고유 식별자 - 서로게이트 키                                                                |                 123                  |
|           UserId           |                                                                              해당 MAM 앱을 설치한 사용자의 사용자 ID                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              MAM 앱 인스턴스에 대한 고유 식별자 - ApplicationInstanceKey와 비슷하지만 자연 키입니다.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | 이 Mam 애플리케이션 인스턴스가 생성된 Mam 애플리케이션의 애플리케이션 ID입니다.   | 11/23/2016 12:00:00 AM   |
|     ApplicationVersion     |                                                                                     해당 MAM 앱의 애플리케이션 버전                                                                                      |                  2                   |
|        CreatedDate         |                                                                 MAM 앱 인스턴스의 이 레코드를 만든 날짜입니다. 값은 null일 수 있습니다.                                                                 |        11/23/2016 12:00:00 AM        |
|          플랫폼          |                                                                          해당 MAM 앱이 설치된 디바이스 플랫폼                                                                           |                  2                   |
|      PlatformVersion       |                                                                      해당 MAM 앱이 설치된 디바이스의 플랫폼 버전                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            해당 MAM 앱을 래핑한 MAM SDK 버전                                                                            |                 3.2                  |
| mamDeviceId | MAM 애플리케이션 인스턴스가 연결된 디바이스의 디바이스 ID입니다.   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | MAM 애플리케이션 인스턴스가 연결된 디바이스의 디바이스 유형입니다.   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | MAM 애플리케이션 인스턴스가 연결된 디바이스의 디바이스 이름입니다.   | 11/23/2016 12:00:00 AM   |
|         IsDeleted          | 이 MAM 앱 인스턴스 레코드가 업데이트되었는지 나타냅니다. <br>True-이 MAM 앱 인스턴스는 이 테이블에서 필드가 업데이트된 새 레코드를 가집니다. <br>False-이 MAM 앱 인스턴스의 최신 레코드입니다. |              True/False              |
|   StartDateInclusiveUtc    |                                                              데이터웨어 하우스에서 해당 MAM 앱 인스턴스를 만든 UTC 날짜 및 시간                                                               |        11/23/2016 12:00:00 AM        |
|       DeletedDateUtc       |                                                                             IsDeleted를 True로 변경한 UTC 날짜 및 시간                                                                              |        11/23/2016 12:00:00 AM        |
| RowLastModifiedDateTimeUtc |                                                           데이터웨어 하우스에서 해당 MAM 앱 인스턴스를 마지막으로 수정한 UTC 날짜 및 시간                                                            |        11/23/2016 12:00:00 AM        |


## <a name="mamcheckin"></a>MamCheckin

**MamCheckin** 엔터티는 Intune 서비스를 사용하여 모바일 앱 관리(MAM) 앱 인스턴스가 체크인되었을 때 수집된 데이터를 나타냅니다. 

> [!Note]  
> 앱 인스턴스가 하루에 여러 번 체크인할 경우 데이터 웨어하우스는 이를 단일 체크인으로 저장합니다.

| 속성 | 설명 | 예제 |
|---------|------------|--------|
| DateKey |데이터 웨어하우스에서 MAM 앱 체크 인을 기록한 날짜 키 | 20160703 |
| ApplicationInstanceKey |해당 MAM 앱 체크 인에 연결된 앱 인스턴스의 키 | 123 |
| UserKey |해당 MAM 앱 체크 인에 연결된 사용자의 키 | 4323 |
| mamApplicationKey |MAM 애플리케이션과 관련된 애플리케이션의 애플리케이션 키를 체크 인합니다. | 432 |
| DeviceHealthKey |해당 MAM 앱 체크 인에 연결된 DeviceHealth의 키 | 321 |
| PlatformKey |해당 MAM 앱 체크 인에 연결된 디바이스의 플랫폼을 나타냅니다. |123 |
| EffectiveAppliedPolicyKey |체크인된 MAM 앱과 연결된 발효된 적용 정책을 나타냅니다. 특정 앱 및 사용자와 관련된 모든 정책을 병합하여 얻은 발효된 적용 정책 결과입니다. | 322 |
| LastCheckInDate |이 MAM 앱이 마지막으로 체크인한 날짜와 시간입니다. 값은 null일 수 있습니다. |11/23/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>MamDeviceHealth

**MamDeviceHealth** 엔터티는 탈옥 디바이스라고 해도 모바일 앱 관리(MAM) 정책이 배포된 디바이스를 나타냅니다.

| 속성 | 설명 | 예제 |
|---------|------------|--------|
| DeviceHealthKey |데이터 웨어하우스의 디바이스 및 관련 상태에 대한 고유 식별자 - 서로게이트 키 |123 |
| DeviceHealth |디바이스 및 관련 상태에 대한 고유 식별자 - DeviceHealthKey와 비슷하지만 자연 키입니다 |b66bc706-ffff-7777-0340-032819502773 |
| DeviceHealthName |디바이스 상태를 나타냅니다. <br>사용할 수 없음 - 이 디바이스에 대한 정보가 없습니다. <br>정상 - 디바이스가 탈옥되지 않았습니다. <br>비정상 - 디바이스가 탈옥되었습니다. |사용할 수 없음 정상 비정상 |
| RowLastModifiedDateTimeUtc |데이터 웨어하우스에서 해당 특정 MAM 디바이스 상태를 마지막으로 수정한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

**MamEffectivePolicy** 엔터티는 조직에 적용되는 모든 모바일 앱 관리(MAM) 실효 정책을 나열합니다. 특정 앱 및 사용자와 관련된 모든 정책을 병합하여 얻은 발효된 적용 정책 결과입니다.

| 속성 | 설명 | 예제 |
|---------|------------|--------|
| EffectivePolicyKey |데이터 웨어하우스의 효과적인 MAM 정책에 대한 고유 식별자 |2 |
| RealPolicyKey |IT Pro가 작성하는 MAM 정책의 고유 식별자입니다. |1 |
| RowCreatedDateTimeUtc |데이터 웨어하우스에서 MAM 실효 정책이 만들어진 UTC 날짜 및 시간입니다. |11/23/2016 12:00:00 AM |

## <a name="mamglobalapplication"></a>MamGlobalApplication

**MamGlobalApplication** 엔터티는 회사에 등록하지 않고 모바일 앱 관리(MAM)를 통해 관리되는 스토어 앱을 나열합니다.


|          속성          |                                               설명                                               |           예제            |
|----------------------------|---------------------------------------------------------------------------------------------------------|------------------------------|
|       ApplicationKey       |          대리 키로 알려진 데이터 웨어하우스의 스토어 앱의 고유 식별자입니다.          |             123              |
|       ApplicationId        | 스토어 앱의 고유 식별자입니다. ApplicationKey와 비슷하지만 자연 키 식별자입니다.  | com.microsoft.skydrive.<ios> |
|      ApplicationName       |                                      MAM 전역 애플리케이션 이름입니다.                                       |           Skydrive           |
| RowLastModifiedDateTimeUtc | 데이터 웨어하우스에서 이 특정 MAM 글로벌 애플리케이션을 마지막으로 수정한 UTC 날짜 및 시간입니다. |    11/23/2016 12:00:00 AM    |

## <a name="mamplatform"></a>MamPlatform

**MamPlatform** 엔터티는 모바일 앱 관리(MAM) 앱이 설치된 플랫폼 이름과 유형을 나열합니다.


|          속성          |                                    설명                                    |                         예제                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     데이터 웨어하우스의 플랫폼에 대한 고유 식별자 - 서로게이트 키      |                           123                           |
|          플랫폼          | 플랫폼에 대한 고유 식별자 - PlatformKey와 비슷하지만 자연 키입니다. |                           123                           |
|        PlatformName        |                                   플랫폼 이름                                   | 사용할 수 없음 <br>없음 <br>Windows <br>iOS <br>Android: |
| RowLastModifiedDateTimeUtc | 데이터 웨어하우스에서 해당 플랫폼을 마지막으로 수정한 UTC 날짜 및 시간  |                 11/23/2016 12:00:00 AM                  |

