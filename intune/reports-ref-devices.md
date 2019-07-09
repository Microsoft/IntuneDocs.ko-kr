---
title: 디바이스 - Intune 데이터 웨어하우스
titleSuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 디바이스 범주에 대한 항목을 참조하세요.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b1fe488ed7d295a40b42c1fb17a76693004be4d
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67547927"
---
# <a name="reference-for-devices-entities"></a>디바이스 엔터티에 대한 참조

**디바이스** 범주는 다음과 같은 정보를 추적하는 모바일 디바이스에 대한 엔터티를 포함합니다.

  - 디바이스 유형
  - 디바이스 등록 및 등록 상태
  - 디바이스 소유권
  - 디바이스 관리 상태
  - Azure AD 상태에 대한 디바이스 멤버 자격
  - 등록 상태
  - 디바이스에 대한 과거 정보
  - 디바이스에서 앱의 인벤토리

## <a name="devicetypes"></a>DeviceTypes

**DeviceTypes** 엔터티는 다른 데이터 웨어하우스 엔터티에서 참조하는 디바이스 유형을 나타냅니다. 디바이스 유형은 일반적으로 디바이스 모델, 제조업체 또는 두 가지의 조합을 설명합니다.

| 속성  | 설명 |
|---------|------------|
| DeviceTypeID |디바이스 유형의 고유 식별자 |
| DeviceTypeKey |데이터 웨어하우스의 디바이스 유형에 대한 고유 식별자 - 대리 키 |
| DeviceTypeName |디바이스 유형 |

### <a name="example"></a>예제

| deviceTypeID  | 이름 | 설명 |
|---------|------------|--------|
| 0 |데스크톱 |Windows 데스크톱 디바이스 |
| 1 |WindowsRT |WindowsRT 디바이스 |
| 2 |WinMO6 |Windows Mobile 6.0 디바이스 |
| 3 |Nokia |Nokia 디바이스 |
| 4 |WindowsPhone |Windows Phone 디바이스 |
| 5 |Mac |Mac 디바이스 |
| 6 |WinCE |Windows CE 디바이스 |
| 7 |WinEmbedded |Windows Embedded 디바이스 |
| 8 |iPhone |iPhone 디바이스 |
| 9 |iPad |iPad 디바이스 |
| 10 |IPod |iPod 디바이스 |
| 11 |Android |Android 디바이스 - 디바이스 관리자로 관리 |
| 12 |ISocConsumer |iSoc 소비자 디바이스 |
| 14 |MacMDM |기본 MDM 에이전트로 관리되는 Mac OS X 디바이스 |
| 15 |HoloLens |HoloLens 디바이스 |
| 16 |SurfaceHub |Surface Hub 디바이스 |
| 17 |AndroidForWork |Android Profile Owner로 관리되는 Android 디바이스 |
| 100 |Blackberry |Blackberry 디바이스 |
| 101 |Palm |Palm 디바이스 |
| 255 |Unknown |알 수 없는 디바이스 유형 |

## <a name="enrollmentactivities"></a>enrollmentActivities 
**EnrollmentActivity** 엔터티는 디바이스 등록의 작업을 나타냅니다.

| 속성                      | 설명                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | 이 등록 작업이 기록된 때의 날짜 키입니다.               |
| deviceEnrollmentTypeKey       | 등록 형식의 키입니다.                                        |
| deviceTypeKey                 | 디바이스 유형의 키입니다.                                                |
| enrollmentEventStatusKey      | 등록의 성공 여부를 나타내는 상태 키입니다.    |
| enrollmentFailureCategoryKey  | 등록 실패 범주의 키입니다(등록에 실패하는 경우).        |
| enrollmentFailureReasonKey    | 등록 실패 이유의 키입니다(등록에 실패하는 경우).          |
| osVersion                     | 디바이스의 운영 체제 버전입니다.                               |
| 개수                         | 위의 분류와 일치하는 등록 작업의 총 수입니다.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
**EnrollmentEventStatus** 엔터티는 디바이스 등록의 결과를 나타냅니다.

| 속성                   | 설명                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | 데이터 웨어하우스의 등록 상태의 고유 식별자(서로게이트 키)  |
| enrollmentEventStatusName  | 등록 상태의 이름입니다. 아래 예제를 참조하세요.                            |

### <a name="example"></a>예제

| enrollmentEventStatusName  | 설명                            |
|----------------------------|----------------------------------------|
| 성공                    | 디바이스 등록 성공         |
| Failed                     | 디바이스 등록 실패             |
| 사용할 수 없음              | 등록 상태를 사용할 수 없습니다.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
**EnrollmentFailureCategory** 엔터티는 디바이스 등록에 실패한 이유를 나타냅니다. 

| 속성                       | 설명                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | 데이터 웨어하우스의 등록 실패 범주의 고유 식별자(서로게이트 키)  |
| enrollmentFailureCategoryName  | 등록 실패 범주의 이름입니다. 아래 예제를 참조하세요.                            |

### <a name="example"></a>예제

| enrollmentFailureCategoryName   | 설명                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| 해당 없음                  | 등록 실패 범주를 적용할 수 없습니다.                                                            |
| 사용할 수 없음                   | 등록 실패 범주를 사용할 수 없습니다.                                                             |
| Unknown                         | 알 수 없는 오류입니다.                                                                                                |
| 인증                  | 인증에 실패했습니다.                                                                                        |
| 권한 부여                   | 호출이 인증되었지만 등록할 수 있는 권한이 없습니다.                                                         |
| AccountValidation               | 등록에 대한 계정의 유효성을 검사하지 못했습니다. (계정 차단됨, 등록 사용 안 함)                      |
| UserValidation                  | 사용자의 유효성을 검사할 수 없습니다. (사용자가 없음, 라이선스 누락)                                           |
| DeviceNotSupported              | 디바이스가 모바일 디바이스 관리에서 지원되지 않습니다.                                                         |
| InMaintenance                   | 계정이 유지 관리 모드에 있습니다.                                                                                    |
| BadRequest                      | 클라이언트에서 서비스에서 인식/지원되지 않는 요청을 보냈습니다.                                        |
| FeatureNotSupported             | 이 등록에서 사용되는 기능은 이 계정에서 지원되지 않습니다.                                        |
| EnrollmentRestrictionsEnforced  | 관리자가 구성한 등록 제한 사항이 이 등록을 차단합니다.                                          |
| ClientDisconnected              | 최종 사용자에 의해 클라이언트 시간 초과 또는 등록이 중단되었습니다.                                                        |
| UserAbandonment                 | 최종 사용자에 의해 등록이 중단되었습니다. (최종 사용자가 온보딩을 시작했지만 적시에 완료하지 못함)  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
**EnrollmentFailureReason** 엔터티는 지정된 실패 범주 내에서 디바이스 등록 실패에 대한 자세한 이유를 나타냅니다.  

| 속성                     | 설명                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | 데이터 웨어하우스의 등록 실패 이유의 고유 식별자(서로게이트 키)  |
| enrollmentFailureReasonName  | 등록 실패 이유의 이름입니다. 아래 예제를 참조하세요.                            |

### <a name="example"></a>예제

| enrollmentFailureReasonName      | 설명                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 해당 없음                   | 등록 실패 이유를 적용할 수 없습니다.                                                                                                                                                       |
| 사용할 수 없음                    | 등록 실패 이유를 사용할 수 없습니다.                                                                                                                                                        |
| Unknown                          | 알 수 없는 오류입니다.                                                                                                                                                                                         |
| UserNotLicensed                  | 사용자를 Intune에서 찾을 수 없거나 유효한 라이선스가 없습니다.                                                                                                                                     |
| UserUnknown                      | 사용자를 Intune에서 알 수 없습니다.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | 한 명의 사용자만 디바이스를 등록할 수 있습니다. 이 디바이스는 이전에 다른 사용자에 의해 등록되었습니다.                                                                                                                |
| EnrollmentOnboardingIssue        | Intune MDM(모바일 디바이스 관리) 기관이 아직 구성되지 않았습니다.                                                                                                                                 |
| AppleChallengeIssue              | iOS 관리 프로필 설치가 지연되었거나 실패했습니다.                                                                                                                                         |
| AppleOnboardingIssue             | Apple MDM 푸시 인증서를 Intune에 등록해야 합니다.                                                                                                                                       |
| DeviceCap                        | 사용자가 허용된 최댓값보다 많은 디바이스를 등록하려고 시도했습니다.                                                                                                                                        |
| AuthenticationRequirementNotMet  | Intune 등록 서비스가 이 요청을 인증하지 못했습니다.                                                                                                                                            |
| UnsupportedDeviceType            | 이 디바이스가 Intune 등록에 대한 최소 요구 사항을 충족하지 않습니다.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | 이 디바이스는 구성된 등록 제한 사항 규칙으로 인해 등록에 실패했습니다.                                                                                                                          |
| BulkDeviceNotPreregistered       | 이 디바이스의 IMEI(국제 모바일 장비 식별자) 또는 일련 번호를 찾을 수 없습니다.  이 식별자가 없는 디바이스는 현재 차단된 개인 소유 디바이스로 인식됩니다.  |
| FeatureNotSupported              | 사용자가 모든 고객에 대해 아직 해제되지 않거나 Intune 구성과 호환되지 않는 기능에 액세스하려고 시도했습니다.                                                            |
| UserAbandonment                  | 최종 사용자에 의해 등록이 중단되었습니다. (최종 사용자가 온보딩을 시작했지만 적시에 완료하지 못함)                                                                                           |
| APNSCertificateExpired           | 만료된 Apple MDM 푸시 인증서를 사용하여 Apple 디바이스를 관리할 수 없습니다.                                                                                                                            |
## <a name="ownertypes"></a>OwnerTypes

**EnrollmentTypes** 엔터티는 디바이스가 회사 디바이스인지 개인 소유인지 알 수 없는지 나타냅니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| ownerTypeID |소유자 유형에 대한 고유 식별자 | |
| ownerTypeKey |데이터 웨어하우스의 소유자 유형에 대한 고유 식별자 - 서로게이트 키 | |
| ownerTypeName |디바이스의 소유자 유형을 나타냅니다.  <br>회사 - 회사 소유 디바이스입니다. <br>개인 - 개인 소유 디바이스입니다(BYOD).  <br>알 수 없음 - 이 디바이스에 대한 정보가 없습니다. |회사 개인 알 수 없음 |

> [!Note]  
> 디바이스용 동적 그룹을 만들 때 AzureAD의 `ownerTypeName`에 대해 필터 값 `deviceOwnership`을 `Company`로 설정해야 합니다. 자세한 내용은 [디바이스 규칙](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices)을 참조하세요. 

## <a name="managementstates"></a>ManagementStates

**ManagementStates** 엔터티는 디바이스의 상태에 대한 세부 정보를 제공합니다. 세부 정보는 원격 작업을 적용할 때, 디바이스를 탈옥 또는 루팅한 경우 유용합니다.

| 속성  | 설명 |
|---------|------------|
| managementStateID | 관리 상태의 고유 식별자입니다. |
| managementStateKey | 데이터 웨어하우스에서 관리 상태의 고유 식별자 - 대리 키 |
| managementStateName | 이 디바이스에 적용된 원격 작업의 상태를 나타냅니다. |

### <a name="example"></a>예제

| managementStateID  | 이름 | 설명 |
|---------|------------|--------|
| 0 |관리 대상 | 보류 중인 원격 작업 없이 관리됨 |
| 1 |RetirePending | 디바이스에 대한 보류 중인 사용 중지 명령이 없습니다. |
| 2 |RetireFailed | 디바이스에서 사용 중지 명령이 실패했습니다. |
| 3 |WipePending | 디바이스에 대한 보류 중인 초기화 명령이 있습니다. |
| 4 |WipeFailed | 디바이스에서 초기화 명령이 실패했습니다. |
| 5 |Unhealthy | 비정상 상태 |
| 6 |DeletePending | 디바이스에 대한 보류 중인 삭제 명령이 있습니다. |
| 7 |RetireIssued | 디바이스로 사용 중지 명령이 실행되었습니다. |
| 8 |WipeIssued | 초기화 명령이 실행되었습니다. |
| 9 |WipeCanceled | 초기화 명령이 취소되었습니다. |
| 10 |RetireCanceled | 사용 중지 명령이 취소되었습니다. |
| 11 |Discovered | Intune에서 디바이스를 새로 검색하고 해당 디바이스를 처음으로 체크 인하면 '관리됨' 상태가 됩니다. |

## <a name="managementagenttypes"></a>ManagementAgentTypes

**ManagementAgentTypes** 엔터티는 디바이스 관리에 사용되는 에이전트를 나타냅니다.

| 속성  | 설명 |
|---------|------------|
| ManagementAgentTypeID | 관리 에이전트 유형에 대한 고유 식별자 |
| ManagementAgentTypeKey | 데이터 웨어하우스의 관리 에이전트 유형에 대한 고유 식별자 - 서로게이트 키 |
| ManagementAgentTypeName |디바이스 관리에 사용되는 에이전트의 종류를 나타냅니다. |

### <a name="example"></a>예제

| ManagementAgentTypeID  | 이름 | 설명 |
|---------|------------|--------|
| 1 |EAS | Exchange Active Sync를 통해 디바이스를 관리 |
| 2 |MDM | 디바이스가 MDM 에이전트를 사용하여 관리됨 |
| 3 |EasMdm | 디바이스가 Exchange Activesync와 MDM 에이전트를 둘 다 사용하여 관리됨 |
| 4 |IntuneClient | 디바이스가 Intune PC 에이전트를 사용하여 관리됨 |
| 5 |EasIntuneClient | 디바이스가 Exchange Active Sync와 Intune PC 에이전트를 둘 다 사용하여 관리됨 |
| 8 |ConfigManagerClient | 디바이스가 System Center Configuration Manager 에이전트를 사용하여 관리됨 |
| 16 |Unknown | 알 수 없는 관리 에이전트 유형 |

## <a name="devices"></a>디바이스

**디바이스** 엔터티는 관리 대상인 모든 등록된 디바이스와 그에 해당하는 속성을 나열합니다.

|          속성          |                                                                                       설명                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | 데이터 웨어하우스에서 디바이스의 고유 식별자 - 서로게이트 키                                                                                                               |
| DeviceId                   | 디바이스의 고유 식별자입니다.                                                                                                                                                     |
| DeviceName                 | 디바이스 이름 지정을 허용하는 플랫폼에서 디바이스의 이름입니다. 다른 플랫폼에서 Intune은 다른 속성으로부터 이름을 만듭니다. 이 특성은 모든 디바이스에 대해 사용할 수 없습니다. |
| DeviceTypeKey              | 이 디바이스의 디바이스 유형 특성의 키                                                                                                                                    |
| DeviceRegistrationState    | 이 디바이스의 클라이언트 등록 상태 특성의 키                                                                                                                      |
| OwnerTypeKey               | 이 디바이스의 소유자 유형 특성 키는 회사, 개인 또는 알 수 없음입니다.                                                                                                    |
| EnrolledDateTime           | 이 디바이스가 등록된 날짜 및 시간                                                                                                                                         |
| LastSyncDateTime           | Intune에서 마지막으로 인식된 디바이스 체크 인                                                                                                                                              |
| ManagementAgentKey         | 이 디바이스와 연결된 관리 에이전트의 키                                                                                                                             |
| ManagementStateKey         | 이 디바이스와 연결된 관리 상태의 키로 원격 작업의 마지막 상태를 나타내거나 탈옥/루팅 여부를 나타냅니다.                                                |
| AzureADDeviceId            | 이 디바이스의 Azure deviceID                                                                                                                                                  |
| AzureADRegistered          | 디바이스가 Azure Active Directory에 등록되었는지 여부를 나타냅니다.                                                                                                                             |
| DeviceCategoryKey          | 이 디바이스와 연결된 범주의 키                                                                                                                                     |
| DeviceEnrollmentType       | 이 디바이스와 연결된 등록 유형 키로 등록 방법을 나타냅니다.                                                                                             |
| ComplianceStateKey         | 이 디바이스와 연결된 준수 상태의 키입니다.                                                                                                                             |
| OSVersion                  | 디바이스의 운영 체제 버전입니다.                                                                                                                                                |
| EasDeviceId                | 디바이스의 Exchange ActiveSync ID입니다.                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | 디바이스와 연결된 사용자의 고유 ID입니다.                                                                                                                           |
| RowLastModifiedDateTimeUTC | 데이터 웨어하우스에서 디바이스를 마지막으로 수정한 UTC 날짜 및 시간                                                                                                       |
| 제조업체               | 디바이스 제조업체                                                                                                                                                             |
| 모델                      | 디바이스의 모델                                                                                                                                                                    |
| OperatingSystem            | 디바이스 운영 체제는 Windows, iOS 등입니다.                                                                                                                                   |
| IsDeleted                  | 디바이스가 삭제되었는지 여부를 표시하는 이진입니다.                                                                                                                                 |
| AndroidSecurityPatchLevel  | Android 보안 패치 수준                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | 디바이스가 감독되고 있습니다.                                                                                                                                                               |
| FreeStorageSpaceInBytes    | 사용 가능한 스토리지 공간(바이트)입니다.                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | 총 스토리지 공간(바이트)입니다.                                                                                                                                                                |
| EncryptionState            | 디바이스의 암호화 상태입니다.                                                                                                                                                      |
| SubscriberCarrier          | 디바이스의 구독자 통신 회사입니다.                                                                                                                                                       |
| PhoneNumber                | 디바이스의 전화 번호                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | 디바이스의 셀룰러 기술입니다.                                                                                                                                                    |
| WiFiMacAddress             | Wi-Fi MAC                                                                                                                                                                              |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

**DevicePropertyHistory** 엔터티는 지난 90일 동안 하루에 각 디바이스 레코드의 디바이스 테이블 및 일일 스냅샷과 동일한 속성을 지닙니다. DateKey 열은 각 행에 대한 날짜를 나타냅니다.

|          속성          |                                                                                      설명                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | 날짜를 나타내는 날짜 테이블에 대한 참조                                                                                                                                          |
| DeviceKey                  | 데이터 웨어하우스에서 디바이스의 고유 식별자 - 서로게이트 키 Intune 디바이스 ID가 포함된 디바이스 테이블의 참조입니다.                               |
| DeviceName                 | 디바이스 이름 지정을 허용하는 플랫폼에서 디바이스의 이름입니다. 다른 플랫폼에서 Intune은 다른 속성으로부터 이름을 만듭니다. 이 특성은 모든 디바이스에 대해 사용할 수 없습니다. |
| DeviceRegistrationStateKey | 이 디바이스에 대한 디바이스 등록 상태 특성의 키입니다.                                                                                                                    |
| OwnerTypeKey               | 이 디바이스의 소유자 유형 특성 키는 회사, 개인 또는 알 수 없음입니다.                                                                                                  |
| ManagementStateKey         | 이 디바이스와 연결된 관리 상태의 키로 원격 작업의 마지막 상태나 탈옥/루팅 여부를 나타냅니다.                                                |
| AzureADRegistered          | 디바이스가 Azure Active Directory에 등록되었는지 여부를 나타냅니다.                                                                                                                             |
| ComplianceStateKey         | ComplianceState에 대한 키입니다.                                                                                                                                                            |
| OSVersion                  | OS 버전                                                                                                                                                                          |
| 탈옥                 | 디바이스의 탈옥 또는 루팅 여부를 나타냅니다.                                                                                                                                         |
| DeviceCategoryKey          | 이 디바이스의 디바이스 범주 특성 키입니다. 

## <a name="applicationinventory"></a>ApplicationInventory

**ApplicationInventory** 엔터티는 인벤터리 수집 시점에 디바이스에서 발견된 앱을 나열합니다.


|      속성      |                       설명                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              디바이스 테이블에 대한 참조               |
|   ApplicationKey   | ? (ExchangeDeviceService\DeviceApplication에서 복사) |
|  ApplicationName   | ? (ExchangeDeviceService\DeviceApplication에서 복사) |
| ApplicationVersion | ? (ExchangeDeviceService\DeviceApplication에서 복사) |
|     BundleSize     | ? (ExchangeDeviceService\DeviceApplication에서 복사) |

