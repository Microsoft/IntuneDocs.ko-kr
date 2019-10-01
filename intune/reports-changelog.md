---
title: Intune 데이터 웨어하우스 변경 로그
titleSuffix: Microsoft Intune
description: 이 항목에서는 Microsoft Intune 데이터 웨어하우스 API에 대한 변경 내용 목록을 제공합니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0aaa305ac216e0f80f82116e626b21f3ae7a8510
ms.sourcegitcommit: c8cb314256c4896e838918f015ffaefb8f00ace5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2019
ms.locfileid: "71303307"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 데이터 웨어하우스 API에 대한 변경 로그

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 데이터 웨어하우스에 대한 업데이트를 최신 상태로 유지합니다.

## <a name="1903-part-2"></a>1903(2부)
_릴리스 날짜: 2019년 4월_

### <a name="beta-changes"></a>베타 변경

다음 표에서 최근 제거 컬렉션 및 Intune Data Warehouse의 대체 컬렉션이 나열되어 있습니다.

|    수집                          |    Change(영문)     |    추가 정보                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    mobileAppDeviceUserInstallStatus    |    제거됨    |    대신 [mobileAppInstallStatusCounts](intune-data-warehouse-collections.md#mobileappinstallstatuscounts)를 사용합니다.                                                                                                                                                                                                                                                                     |
|    enrollmentTypes                     |    제거됨    |    대신 [deviceEnrollmentTypes](intune-data-warehouse-collections.md#deviceenrollmenttypes)를 사용합니다.                                                                                                                                                                                                                                                                                      |
|    mdmStatuses                         |    제거됨    |    대신 [complianceStates](intune-data-warehouse-collections.md#compliancestates)를 사용합니다.                                                                                                                                                                                                                                                                                               |
|    workPlaceJoinStateTypes             |    제거됨    |    대신 [디바이스](intune-data-warehouse-collections.md#devices) 및 [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) 컬렉션의 `azureAdRegistered` 속성을 사용합니다.                                                                                                                                                                                                             |
|    clientRegistrationStateTypes        |    제거됨    |    대신 [deviceRegistrationStates](intune-data-warehouse-collections.md#deviceregistrationstates)를 사용합니다.                                                                                                                                                                                                                                                                             |
|    currentUser                         |    제거됨    |    대신 [사용자](intune-data-warehouse-collections.md#users) 컬렉션을 사용합니다.                                                                                                                                                                                                                                                                                                      |
|    mdmDeviceInventoryHistories         |    제거됨    |    속성의 대부분이 중복되었거나 이제 [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) 또는 [디바이스](intune-data-warehouse-collections.md#devices) 컬렉션에서 찾을 수 있습니다. 이 두 컬렉션에 아직 나열되지 않은 모든 **mdmDeviceInventoryHistories** 속성은 더 이상 사용할 수 없습니다. 아래 세부 정보를 참조하세요.    |

다음 표에는 **mdmDeviceInventoryHistories** 컬렉션에서 발견된 이전 속성과 변경/대체가 나열되어 있습니다. **mdmDeviceInventoryHistories**에 있지만 아래에 나열되지 않은 모든 속성은 제거되었습니다.

|    이전 속성                |    변경/대체                                                           |
|--------------------------------|---------------------------------------------------------------------------------|
|    cellularTechnology          |    디바이스 컬렉션의 cellularTechnology                                     |
|    deviceClientId              |    디바이스 컬렉션의 deviceId                                               |
|    deviceManufacturer          |    디바이스 컬렉션의 제조업체                                           |
|    deviceModel                 |    디바이스 컬렉션의 모델                                                  |
|    deviceName                  |    디바이스 컬렉션의 deviceName                                             |
|    deviceOsPlatform            |    디바이스 컬렉션의 deviceTypeKey                                          |
|    deviceOsVersion             |    devicePropertyHistories 컬렉션의 osVersion                              |
|    deviceType                  |    디바이스 컬렉션의 deviceTypeKey, deviceTypes 컬렉션 참조    |
|    encryptionState             |    디바이스 컬렉션의 encryptionState 속성                           |
|    exchangeActiveSyncId        |    디바이스 컬렉션의 easDeviceId 속성                               |
|    exchangeDeviceId            |    디바이스 컬렉션의 easDeviceId                                            |
|    imei                        |    디바이스 컬렉션의 imei                                                   |
|    isSupervised                |    디바이스 컬렉션의 isSupervised 속성                              |
|    무단 해제                  |    devicePropertyHistories 컬렉션의 무단 해제                             |
|    meid                        |    디바이스 컬렉션의 meid 속성                                      |
|    oem                         |    디바이스 컬렉션의 제조업체                                           |
|    osName                      |    디바이스 컬렉션의 deviceTypeKey, deviceTypes 컬렉션 참조    |
|    phoneNumber                 |    디바이스 컬렉션의 phoneNumber                                            |
|    platformType                |    디바이스 컬렉션의 모델                                                  |
|    product                     |    디바이스 컬렉션의 deviceTypeKey                                          |
|    productVersion              |    devicePropertyHistories 컬렉션의 osVersion                              |
|    serialNumber                |    디바이스 컬렉션의 serialNumber                                           |
|    storageFree                 |    디바이스 컬렉션의 freeStorageSpaceInBytes 속성                   |
|    storageTotal                |    디바이스 컬렉션의 totalStorageSpaceInBytes 속성                |
|    subscriberCarrierNetwork    |    디바이스 컬렉션의 subscriberCarrier 속성                         |
|    wifimac                     |    디바이스 컬렉션의 wiFiMacAddress                                         |

다음 표에는 [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) 컬렉션에 있는 속성의 변경 내용이 나열되어 있습니다. 

|    이전 속성                  |    변경/대체                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, deviceCategories 컬렉션 참조       |
|    certExpirationDate            |    제거됨                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    디바이스 컬렉션의 enrolledDateTime                           |
|    deviceTypeKey                 |    디바이스 컬렉션의 deviceTypeKey                              |
|    easID                         |    디바이스 컬렉션의 easDeviceId                                |
|    enrolledByUser                |    디바이스 컬렉션의 userId                                     |
|    enrollmentTypeKey             |    디바이스 컬렉션의 deviceEnrollmentTypeKey                    |
|    graphDeviceIsCompliant        |    제거됨                                                          |
|    graphDeviceIsManaged          |    제거됨                                                          |
|    lastContact                   |    디바이스 컬렉션의 lastSyncDateTime                           |
|    lastContactNotification       |    제거됨                                                          |
|    lastContactWorkplaceJoin      |    제거됨                                                          |
|    lastExchangeStatusUtc         |    제거됨                                                          |
|    lastModifiedDateTimeUTC       |    제거됨                                                          |
|    lastPolicyUpdateUtc           |    제거됨                                                          |
|    managementAgentKey            |    managementStateKey                                               |
|    제조업체                  |    디바이스 컬렉션의 제조업체                               |
|    mdmStatusKey                  |    complianceStateKey, complianceStates 컬렉션 참조    |
|    model                         |    디바이스 컬렉션의 모델                                      |
|    osFamily                      |    디바이스 컬렉션의 operatingSystem                            |
|    osRevisionNumber              |    디바이스 컬렉션의 osVersion                                  |
|    processorArchitecture         |    제거됨                                                          |
|    referenceId                   |    디바이스 컬렉션의 azureAdDeviceId                            |
|    serialNumber                  |    디바이스 컬렉션의 serialNumber                               |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

다음 표에는 [디바이스](intune-data-warehouse-collections.md#devices) 컬렉션에 있는 속성의 변경 내용이 나열되어 있습니다. 

|    이전 속성                  |    변경/대체                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, deviceCategories 컬렉션 참조       |
|    certExpirationDate            |    제거됨                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime                                                 |
|    easId                         |    easDeviceId                                                      |
|    enrolledByUser                |    userId                                                           |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey                                          |
|    graphDeviceIsCompliant        |    제거됨                                                          |
|    graphDeviceIsManaged          |    제거됨                                                          |
|    lastContact                   |    lastSyncDateTime                                                 |
|    lastContactNotification       |    제거됨                                                          |
|    lastContactWorkplaceJoin      |    제거됨                                                          |
|    lastExchangeStatusUtc         |    제거됨                                                          |
|    lastPolicyUpdateUtc           |    제거됨                                                          |
|    mdmStatusKey                  |    complianceStateKey, complianceStates 컬렉션 참조    |
|    osFamily                      |    operatingSystem                                                  |
|    processorArchitecture         |    제거됨                                                          |
|    referenceId                   |    azureAdDeviceId                                                  |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

다음 표에는 [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities) 컬렉션에 있는 속성의 변경 내용이 나열되어 있습니다. 

|    이전 속성         |    변경/대체         |
|-------------------------|-------------------------------|
|    enrollmentTypeKey    |    deviceEnrollmentTypeKey    |

다음 표에는 [mamApplications](intune-data-warehouse-collections.md#mamapplications) 컬렉션에 있는 속성의 변경 내용이 나열되어 있습니다. 

|    이전 속성       |    변경/대체    |
|-----------------------|--------------------------|
|    applicationKey     |    mamApplicationKey     |
|    applicationName    |    mamApplicationName    |
|    applicationId      |    mamApplicationId      |

다음 표에는 [mamApplicationInstances](intune-data-warehouse-collections.md#mamapplicationinstances) 컬렉션에 있는 속성의 변경 내용이 나열되어 있습니다. 

|    이전 속성     |    변경/대체    |
|---------------------|--------------------------|
|    applicationId    |    mamApplicationId      |
|    deviceId         |    mamDeviceId           |
|    deviceType       |    mamDeviceType         |
|    deviceName       |    mamDeviceName         |

다음 표에는 [mamCheckins](intune-data-warehouse-collections.md#mamcheckins) 컬렉션에 있는 속성의 변경 내용이 나열되어 있습니다. 

|    이전 속성      |    변경/대체    |
|----------------------|--------------------------|
|    applicationKey    |    mamApplicationKey     |

다음 표에는 [사용자](intune-data-warehouse-collections.md#users) 컬렉션에 있는 속성의 변경 내용이 나열되어 있습니다. 

|    이전 속성             |    변경/대체    |
|-----------------------------|--------------------------|
|    startDateInclusiveUtc    |    제거됨               |
|    endDateInclusiveUtc      |    제거됨               |
|    isCurrent                |    제거됨               |

## <a name="1903"></a>1903
_릴리스 날짜: 2019년 3월_

### <a name="v10-changes-reflecting-back-to-beta"></a>베타 버전을 다시 반영하는 V1.0 변경 내용
V1.0은 1808에 처음 도입되었을 때 베타 API와 상당한 차이가 있었습니다. 이러한 변경 내용은 1903에서 베타 API 버전으로 다시 반영됩니다. 베타 API 버전을 사용하는 중요한 보고서가 있으면 변경 내용을 위반하지 않도록 해당 보고서를 V1.0으로 전환하는 것이 좋습니다. Data Warehouse API 버전 및 이번 버전과의 호환성에 대한 자세한 내용은 [API 버전 정보](reports-api-url.md)를 참조하세요. 

## <a name="1902"></a>1902 
_릴리스 날짜: 2019년 2월_

### <a name="power-bi-compliance-app"></a>Power BI 준수 앱 

[Intune 준수(데이터 웨어하우스)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 앱을 사용하여 Power BI Online에서 Intune 데이터 웨어하우스에 액세스합니다. 이제 이 Power BI 앱을 사용하면 설정할 필요 없이 웹 브라우저를 떠나지 않고도 미리 만들어진 보고서에 액세스하고 공유할 수 있습니다. 

> [!NOTE]
> Intune Compliance 앱에 적용할 수 있는 두 가지 추가 필터가 있습니다.

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Intune Compliance 앱에 추가 필터 추가
1. 웹 브라우저에서 [Intune Compliance(Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 앱을 엽니다.
2. **비규격 디바이스**를 클릭하고 **complianceStatus** 필터에서 **비 규격**을 선택합니다. 
3. **알 수 없는 디바이스**를 클릭하고 **complianceStatus** 필터에서 **아직 사용할 수 없음**을 선택합니다. 

## <a name="1812"></a>1812 
_릴리스 날짜: 2018년 12월_

### <a name="enrollment-activities-collection-released-to-v10"></a>등록 작업 컬렉션이 v1.0으로 릴리스됨 

이제 등록 작업 컬렉션을 v1.0에서 사용할 수 있습니다. 이 컬렉션을 사용하여 사용자 환경에서 등록 실패 볼륨 및 추세를 파악할 수 있습니다. 자세한 내용은 [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities), [enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses), [enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories) 및 [enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons)를 참조하세요.

## <a name="1808"></a>1808
_릴리스 날짜: 2018년 8월_

### <a name="v10-collections"></a>v1.0 컬렉션  

이제 쿼리 매개 변수 `api-version=v1.0`을(를) 설정하여 Intune 데이터 웨어하우스의 v1.0 버전을 사용할 수 있습니다. 데이터 웨어하우스의 컬렉션 업데이트는 가산적이므로 기존 시나리오가 중단되지 않습니다.

### <a name="enrollment-activities-collection-released-to-beta"></a>등록 작업 컬렉션이 베타로 릴리스됨

새 `Enrollment Activities` 컬렉션이 베타로 릴리스됩니다. 이 컬렉션을 사용하여 가장 일반적인 실패를 보면서 등록 진행 방법을 파악할 수 있습니다. 


## <a name="1805"></a>1805
_릴리스 날짜: 2018년 5월_

### <a name="correction-to-device-count-in-devices-collection"></a>**디바이스** 컬렉션의 디바이스 수 수정 

**디바이스** 컬렉션이 수정되어 `isDeleted` 특성을 기준으로 필터링되는 총 디바이스 수가 감소할 수 있습니다. 이 감소는 수정 결과이며 오류가 아닙니다. **디바이스** 컬렉션에 대한 자세한 내용은 [디바이스 엔티티 참조](reports-ref-devices.md)를 참조하세요. 


## <a name="1801"></a>1801
_2018년 1월 출시_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Intune 데이터 웨어하우스 애플리케이션 전용 인증 <!-- 1867540 -->

Azure AD(Azure Active Directory)를 사용하여 애플리케이션을 설정하고 Intune 데이터 웨어하우스에 인증할 수 있습니다. 자세한 내용은 [Intune 데이터 웨어하우스 애플리케이션 전용 인증](data-warehouse-app-only-auth.md)을 참조하세요.

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Azure AD 및 Intune 자격 증명 요구 사항 <!-- 2077525 -->

- Intune 라이선스는 Intune 데이터 웨어하우스(API 포함)에 액세스할 때 더 이상 사용자에게 할당될 필요가 없습니다.
- Intune 역할 이름을 **보고서**에서 **Intune 데이터 웨어하우스**로 변경했습니다. 

    자세한 내용은 [Azure AD 및 Intune 자격 증명 요구 사항](reports-api-url.md#azure-ad-and-intune-credential-requirements)을 참조하세요.

### <a name="odata-query-options----2077711---"></a>OData 쿼리 옵션 <!-- 2077711 -->

<code>$select</code>을 OData 쿼리 매개 변수로 사용할 수 있습니다. 최신 버전에서는 <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> 및 <code>$top</code> OData 쿼리 매개 변수를 지원합니다. 자세한 내용은 [OData 쿼리 옵션](reports-api-url.md#odata-query-options)을 참조하세요.

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Data Warehouse 데이터 모델의 새 엔터티 <!-- 2077804 -->

- [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md) 엔터티가 추가되었습니다. **MobileAppDeviceUserInstallStatus**는 지정된 디바이스 및 사용자의 모바일 앱 설치 상태를 나타냅니다.
- [**MobileAppInstallStates**](reports-ref-application.md#mobileappinstallstates) 엔터티가 추가되었습니다. **MobileAppInstallState** 엔터티는 디바이스, 사용자 또는 둘 다를 포함하는 그룹에 할당된 후 모바일 애플리케이션의 설치 상태를 나타냅니다. 

## <a name="1710"></a>1710
_2017년 11월 출시됨_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>현재 사용자라는 새 엔터티 컬렉션은 현재 활성 사용자 데이터로 제한됨 <!-- 1544273 -->

**사용자** 엔터티 컬렉션에는 엔터프라이즈에서 할당된 라이선스를 가진 모든 Azure AD(Azure Active Directory) 사용자가 포함됩니다. 이러한 레코드에는 사용자가 제거된 경우에도 데이터 컬렉션 기간의 사용자 상태가 포함됩니다. 예를 들어, 사용자가 Intune에 추가된 다음 지난달 중에 제거되었을 수 있습니다. 보고 시점에는 이 사용자가 없지만 데이터에는 사용자와 상태가 있습니다. 데이터에 있는 사용자의 현재 상태 기록에 대한 기간을 보여 주는 보고서를 만들 수 있습니다.

이와 달리 새 **현재 사용자** 엔터티 컬렉션에는 제거되지 않은 사용자만 포함됩니다. **현재 사용자** 엔터티 컬렉션에는 현재 활성 사용자만 포함됩니다. **현재 사용자** 엔터티 컬렉션에 대한 자세한 내용은 [현재 사용자 엔터티에 대한 참조](reports-ref-current-user.md)를 참조하세요.

## <a name="1709"></a>1709
_2017년 10월 출시됨_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Intune Data Warehouse 데이터 모델에 추가된 사용자 디바이스 연결 엔터티 컬렉션 <!-- 1187917 -->

이제 사용자와 디바이스 엔터티 컬렉션을 연결하는 사용자 디바이스 연결 정보를 사용하여 보고서 및 데이터 시각화를 작성할 수 있습니다. 데이터 모델은 데이터 웨어하우스 Intune 페이지에서 검색한 Power BI 파일(PBIX)이나 OData 엔드포인트를 통해 액세스하거나 사용자 지정 클라이언트를 개발하여 액세스할 수 있습니다. 자세한 내용은 [사용자 디바이스 연결](reports-ref-user-device.md)을 참조하세요.

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Data Warehouse 데이터 모델의 새 엔터티 <!-- 1479526 --><!-- -->

- 엔터티 [**UserDeviceAssociation**](reports-ref-user-device.md)이 추가되었습니다. **UserDeviceAssociation**에는 조직의 사용자 디바이스 연결이 포함되어 있습니다. 이제 사용자와 디바이스 엔터티 컬렉션을 연결하는 사용자 디바이스 연결 정보를 사용하여 보고서 및 데이터 시각화를 작성할 수 있습니다.  
- 엔터티 [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md)이 추가되었습니다. **IntuneManagementExtension**은 버전 및 설치 상태와 같은 정보를 추적하는 모바일 디바이스에 대한 엔터티를 포함합니다.

## <a name="next-steps"></a>다음 단계
- [매주 Intune에 추가되는 새로운 기능](whats-new.md)에 대해 알아봅니다. 예정된 변경, 서비스 관련 중요 공지 및 이전 릴리스 관련 정보에 대해서도 알아볼 수 있습니다.
- [Microsoft Intune 블로그](https://go.microsoft.com/fwlink/?LinkID=273882)를 읽어 보세요.
