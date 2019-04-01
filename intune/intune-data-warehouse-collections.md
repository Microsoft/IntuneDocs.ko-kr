---
title: Intune 데이터 웨어하우스 컬렉션
titlesuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 컬렉션은 데이터 웨어하우스 API와 관련된 세부 정보를 제공합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/11/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2cdf7ea715a13809c860e77412914e3fd2b45a28
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57400486"
---
#  <a name="intune-data-warehouse-collections"></a>Intune 데이터 웨어하우스 컬렉션

다음 Intune 데이터 웨어하우스 컬렉션은 데이터 웨어하우스 API 엔터티의 v1.0 컬렉션에 대한 속성, 설명 및 예제를 제공합니다. 

## <a name="apprevisions"></a>appRevisions
**appRevision** 엔터티는 앱의 모든 버전을 나열합니다.

|          속성          |                                      설명                                      |                예제               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | 앱에 대한 고유 식별자                                                         | 123                                  |
| ApplicationId              | 앱의 고유 식별자 - AppKey와 유사하지만 이 키는 자연어입니다.        | b66bc706-ffff-7437-0340-032819502773 |
| 수정                   | 이진 파일을 업로드하는 동안 관리자가 설명한 버전입니다.                   | 2                                    |
| 제목                      | 앱의 제목                                                                     | Excel                                |
| 게시자                  | 앱의 게시자                                                                 | Microsoft                            |
| UploadState                | 앱의 업로드 상태                                                              | 1                                    |
| AppTypeKey                 | 다음 섹션에 설명된 AppType의 참조입니다.                            | 1                                    |
| VppProgramTypeKey          | 아래에 설명된 VppProgramType의 참조입니다.                                        | 30876                                |
| CreationTime               | 해당 수정 버전을 만든 시간                                            | 2016/11/23 0:00                      |
| ModifiedTime               | 해당 수정 버전과 관련된 항목을 마지막으로 변경한 시간                            | 2016/11/23 0:00                      |
| Size                       | 이진 크기(바이트)                                                          | 120,392,000                          |
| StartDateInclusiveUTC      | 데이터 웨어하우스에서 해당 앱의 수정 버전을 만든 UTC 날짜 및 시간      | 2016/11/23 0:00                      |
| EndDateExclusiveUTC        | 해당 앱의 수정 버전이 더 이상 사용되지 않는 UTC 날짜 및 시간                        | 2016/11/23 0:00                      |
| IsCurrent                  | 해당 앱의 수정 버전이 데이터 웨어하우스에 있는지 여부를 나타냅니다.         | True/False                           |
| RowLastModifiedDateTimeUTC | 데이터 웨어하우스에서 해당 앱의 버전을 마지막으로 수정한 UTC 날짜 및 시간 | 2016/11/23 0:00                      |

## <a name="apptypes"></a>appTypes
**appType** 엔터티는 앱의 설치 원본을 나열합니다.

|   속성  |        설명        |
|:-----------:|:-------------------------:|
| AppTypeID   | 형식에 대한 ID           |
| AppTypeKey  | 키에 대한 대리 키 |
| AppTypeName | 앱 유형                  |

### <a name="example"></a>예제

| AppTypeID |                이름               |                     설명                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | Android 스토어 앱               | Android 스토어 앱                             |
| 1         | Android LOB 앱                 | Android 기간 업무 앱                  |
| 2         | 관리되는 Android 스토어 앱(MAM) | 관리를 사용하도록 설정된 Android 스토어 앱 |
| 3         | iOS 스토어 앱                   | iOS 스토어 앱                                 |
| 4         | iOS LOB 앱                     | iOS 기간 업무 앱                      |
| 5         | 관리되는 iOS 스토어 앱(MAM)     | 관리를 사용하도록 설정된 iOS 스토어 앱       |
| 6         | O365 Pro Plus 제품군             | Windows 10용 Office 365 Pro Plus 제품군     |
| 7         | 웹앱                         | 웹앱                                        |
| 8         | Windows Phone 8.1 스토어 앱     | Windows Phone 8.1 스토어 앱                    |
| 9         | Windows 스토어 앱               | Windows 스토어 앱                              |
| 10        | Windows LOB 앱                | Windows AppX 기간 업무 앱              |
| 11        | Windows Mobile MSI              | MSI 기간 업무 앱                      |
| 12        | Windows Phone LOB 앱           | Windows Phone 기간 업무 앱             |

## <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities
다음 표는 디바이스에 준수 정책 할당 상태를 요약하여 보여줍니다. 각 준수 상태에서 찾을 수 있는 디바이스 수를 표시합니다.

|    속성   |                                                                                      설명                                                                                     |  예제 |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | 규정 준수 정책에 대한 요약을 만들 때의 날짜 키                                                                                                                   | 20161204 |
| Unknown       | 오프라인이거나 다른 이유로 인해 Intune 또는 Azure AD와 통신하지 못한 디바이스 수                                                                           | 5        |
| NotApplicable | 관리자가 대상으로 지정한 디바이스 규정 준수 정책을 적용할 수 없는 디바이스 수                                                                                     | 201      |
| 규정     | 관리자가 대상으로 지정한 하나 이상의 디바이스 준수 정책 설정이 성공적으로 적용된 디바이스 수                                                                        | 4083     |
| InGracePeriod | 관리자가 정의한 유예 기간에 있지만, 해당 규정을 준수하지 않은 디바이스 수                                                                                  | 57       |
| NonCompliant  | 관리자가 대상으로 지정한 하나 이상의 디바이스 준수 정책이 디바이스에서 적용되지 않았거나, 관리자가 대상으로 지정한 정책을 사용자가 준수하지 않는 디바이스 수 | 43       |
|    오류      |    Intune 또는 Azure AD와 통신하지 못하고 오류 메시지를 반환한 디바이스 수                                                                          |    3     |

## <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities
다음 표는 정책별 및 정책 유형별 기반 위에 디바이스에 준수 정책 할당 상태를 요약하여 보여줍니다. 각 할당된 준수 정책에 대한 각 준수 상태에서 찾을 수 있는 디바이스 수를 표시합니다.

|      속성     |                                                                                      설명                                                                                     |  예제 |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | 규정 준수 정책에 대한 요약을 만들 때의 날짜 키                                                                                                                   | 20161219 |
| PolicyKey         | 요약이 생성된 규정 준수 정책의 키                                                                                                                   | 10178    |
| PolicyPlatformKey | 요약이 생성된 규정 준수 정책의 플랫폼 형식의 키                                                                                            | 5        |
| Unknown           | 오프라인이거나 다른 이유로 인해 Intune 또는 Azure AD와 통신하지 못한 디바이스 수                                                                           | 13       |
| NotApplicable     | 관리자가 대상으로 지정한 디바이스 규정 준수 정책을 적용할 수 없는 디바이스 수                                                                                     | 3        |
| 규정         | 관리자가 대상으로 지정한 하나 이상의 디바이스 준수 정책 설정이 성공적으로 적용된 디바이스 수                                                                        | 45       |
| InGracePeriod     | 관리자가 정의한 유예 기간에 있지만, 해당 규정을 준수하지 않은 디바이스 수                                                                                  | 3        |
| NonCompliant      | 관리자가 대상으로 지정한 하나 이상의 디바이스 준수 정책이 디바이스에서 적용되지 않았거나, 관리자가 대상으로 지정한 정책을 사용자가 준수하지 않는 디바이스 수 | 7        |
| 오류             | Intune 또는 Azure AD와 통신하지 못하고 오류 메시지를 반환한 디바이스 수                                                                             | 3        |
## <a name="compliancestates"></a>complianceStates

|      속성      |                       설명                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | mdmStatusKey가 있는 디바이스의 준수 상태       |
| complianceStateKey | 디바이스 및 준수 상태와 일치하는 준수 키 |
| complianceStateID  | 이 준수 상태와 일치하는 ID                |

### <a name="example"></a>예제

|  complianceStatus  |                       설명                      |
|:------------------:|:------------------------------------------------------:|
|    Unknown         |    알 수 없습니다.                                                                        |
|    규정       |    준수                                                                      |
|    정책 위반    |       디바이스가 호환되지 않으며 회사 리소스에서 차단되었습니다.             |
|    충돌        |    다른 규칙과 충돌합니다.                                                      |
|    오류           |       오류.                                                                       |
|    ConfigManager   |    Config Manager가 관리합니다.                                                      |
|    InGracePeriod   |       디바이스가 호환되지 않지만 계속해서 회사 리소스에 액세스할 수 있습니다.          |

## <a name="dates"></a>날짜
**날짜** 엔터티는 여러 데이터 웨어하우스 엔터티에 걸쳐 참조되는 날짜를 나타냅니다.

|     속성    |                       설명                      |    예제    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | 데이터 웨어하우스의 해당 날짜에 대한 고유 식별자 | 20160703      |
| FullDate        | 해당 날짜가 전체 날짜/시간 형식으로 표시됩니다.        | 2016/7/3 0:00 |
| DayOfWeek       | 주중 일수                                            | 1             |
| DayOfMonth      | 달중 일수                                           | 3             |
| DayOfYear       | 연중 일수                                            | 185           |
| WeekOfYear      | 연중 주                                           | 28            |
| MonthOfYear     | 연중 월                                      | 7             |
| CalendarQuarter | 달력 분기                                       | 3             |
| CalendarYear    | 달력 연도                                          | 2016          |
| DateKey         | 데이터 웨어하우스의 해당 날짜에 대한 고유 식별자 | 20160703      |
| FullDate        | 해당 날짜가 전체 날짜/시간 형식으로 표시됩니다.        | 2016/7/3 0:00 |
| DayOfWeek       | 주중 일수                                            | 1             |
| DayOfMonth      | 달중 일수                                           | 3             |
| DayOfYear       | 연중 일수                                            | 185           |
| WeekOfYear      | 연중 주                                           | 28            |
| MonthOfYear     | 연중 월                                      | 7             |
| CalendarQuarter | 달력 분기                                       | 3             |
| CalendarYear    | 달력 연도                                          | 2016          |

## <a name="devicecategories"></a>deviceCategories

|      속성      |                                    설명                                   |                예제               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | 디바이스 범주의 고유 식별자입니다.                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | 데이터 웨어하우스에서 디바이스 범주의 고유 식별자 - 서로게이트 키 | 1                                    |
| deviceCategoryName | 디바이스 범주의 표시 이름                                            | Smartphones                          |

## <a name="deviceconfigurationprofiledeviceactivities"></a>deviceConfigurationProfileDeviceActivities
**DeviceConfigurationProfileDeviceActivity** 엔터티는 하루에 성공, 보류, 실패 또는 오류 상태에 있는 디바이스의 수를 나열합니다. 숫자는 엔터티에 할당된 디바이스 구성 프로필을 반영합니다. 예를 들어 디바이스가 모든 할당된 정책에 대해 성공 상태에 있으면 그 날에 대해 성공 카운터를 1만큼 높입니다. 디바이스에 두 프로필이 할당된 경우(성공 상태에 하나, 오류 상태에 하나) 엔터티는 성공 카운터를 하나 늘리고 디바이스를 오류 상태에 놓습니다. 엔터티는 지난 30일 동안 특정 날짜에 해당 상태에 있는 디바이스가 몇 개인지 표시합니다.

|  속성 |                                          설명                                          |  예제 |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | 데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키 | 20160703 |
| Pending   | 보류 중 상태에 있는 고유 디바이스의 수                                                    | 123      |
| 성공 | 성공 상태에 있는 고유 디바이스의 수                                                    | 12       |
| 오류     | 오류 상태에 있는 고유 디바이스의 수                                                      | 10       |
| Failed    | 실패 상태에 있는 고유 디바이스의 수                                                     | 2        |

## <a name="deviceconfigurationprofileuseractivities"></a>deviceConfigurationProfileUserActivities 
**DeviceConfigurationProfileUserActivity** 엔터티는 하루에 성공, 보류, 실패, 오류 상태에 있는 사용자 수를 표시합니다. 숫자는 엔터티에 할당된 디바이스 구성 프로필을 반영합니다. 예를 들어 사용자가 모든 할당된 정책에 대해 성공 상태에 있으면 해당 날짜에 대한 성공 카운터를 1만큼 높입니다. 사용자에게 두 프로필이 할당된 경우(하나는 성공 상태, 하나는 오류 상태) 오류 상태의 사용자를 카운트합니다. **DeviceConfigurationProfileUserActivity** 엔터티는 지난 30일 동안 특정 날짜에 해당 상태에 있는 사용자 수를 표시합니다. 

| 속성  | 설명  | 예제  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | 데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키  | 20160703  |
| Pending  | 보류 중 상태에 있는 고유 사용자 수  | 123  |
| 성공  | 성공 상태에 있는 고유 사용자 수  | 12  |
| 오류  | 오류 상태에 있는 고유 사용자 수  | 10  |
| Failed  | 실패 상태에 있는 고유 사용자 수  | 2  |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

|          속성          |                                                                                      설명                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | 날짜를 나타내는 날짜 테이블에 대한 참조                                                                                                                                          |
| DeviceKey                  | 데이터 웨어하우스에서 디바이스의 고유 식별자는 서로게이트 키입니다. Intune 디바이스 ID가 포함된 디바이스 테이블의 참조입니다.                               |
| DeviceName                 | 디바이스 이름 지정을 허용하는 플랫폼에서 디바이스의 이름입니다. 다른 플랫폼에서 Intune은 다른 속성으로부터 이름을 만듭니다. 이 특성은 모든 디바이스에 대해 사용할 수 없습니다. |
| DeviceRegistrationStateKey | 이 디바이스에 대한 디바이스 등록 상태 특성의 키입니다.                                                                                                                    |
| OwnerTypeKey               | 이 디바이스의 소유자 유형 특성 키는 회사, 개인 또는 알 수 없음입니다.                                                                                                  |
| ManagementStateKey         | 이 디바이스와 연결된 관리 상태의 키로 원격 작업의 마지막 상태나 탈옥/루팅 여부를 나타냅니다.                                                |
| AzureADRegistered          | 디바이스가 Azure Active Directory에 등록되었는지 여부를 나타냅니다.                                                                                                                             |
| ComplianceStateKey         | ComplianceState에 대한 키입니다.                                                                                                                                                            |
| OSVersion                  | OS 버전                                                                                                                                                                          |
| 탈옥                 | 디바이스의 탈옥 또는 루팅 여부를 나타냅니다.                                                                                                                                         |
| DeviceCategoryKey          | 이 디바이스의 디바이스 범주 특성 키입니다.                                                                                                                                    |
## <a name="deviceregistrationstates"></a>deviceRegistrationStates
**DeviceRegistrationState** 엔터티는 다른 데이터 웨어하우스 컬렉션에서 참조하는 등록 형식을 나타냅니다. 

|           속성          |                                     설명                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | 등록 상태에 대한 고유 식별자                                            |
| deviceRegistrationStateKey  | 데이터 웨어하우스의 등록 상태의 고유 식별자 - 서로게이트 키 |
| deviceRegistrationStateName | 등록 상태                                                                  |
|    NotRegistered                     |    등록 안 됨                                                                                                                                                                  |
|    등록됨                        |       등록됨                                                                                                                                                                   |
|    Revoked                           |       IT 관리자가 클라이언트를 차단했고 클라이언트가 차단 해제될 수 있음을 나타내는 상태입니다. 디바이스는 초기화 또는 사용 중지 후 취소 상태가 될 수 있습니다.        |
|    KeyConflict                       |    키 충돌                                                                                                                                                                    |
|    ApprovalPending                   |    승인 보류 중                                                                                                                                                                |
|    CertificateReset                  |    인증서 재설정                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    등록 안 됨 등록 보류 중                                                                                                                                               |
|    Unknown                           |    알 수 없는 상태                                                                                                                                                                   |

## <a name="devices"></a>장치
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
| OperatingSystem            | 디바이스 운영 체제는  Windows, iOS 등입니다.                                                                                                                                   |
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


## <a name="devicetypes"></a>deviceTypes
**deviceType**엔터티는 다른 데이터 웨어하우스 엔터티에서 참조하는 디바이스 유형을 나타냅니다. 디바이스 유형은 일반적으로 디바이스 모델, 제조업체 또는 두 가지의 조합을 설명합니다.

|    속성    |                                  설명                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | 디바이스 유형의 고유 식별자                                       |
| DeviceTypeKey  | 데이터 웨어하우스의 디바이스 유형의 고유 식별자 - 서로게이트 키 |
| DeviceTypeName | 디바이스 유형                                                                |

### <a name="example"></a>예제

| deviceTypeID |        이름       |                      설명                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | 사용할 수 없음   | 이 디바이스 유형을 사용할 수 없습니다.                     |
| 0            | 데스크톱           | Windows 데스크톱 디바이스                              |
| 1            | Windows           | Windows 디바이스                                      |
| 2            | WinMO6            | Windows Mobile 6.0 디바이스                           |
| 3            | Nokia             | Nokia 디바이스                                        |
| 4            | WindowsPhone      | Windows Phone 디바이스                                |
| 5            | Mac               | Mac 디바이스                                          |
| 6            | WinCE             | Windows CE 디바이스                                   |
| 7            | WinEmbedded       | Windows Embedded 디바이스                             |
| 8            | iPhone            | iPhone 디바이스                                       |
| 9            | iPad              | iPad 디바이스                                         |
| 10           | IPod              | iPod 디바이스                                         |
| 11           | Android           | Android 디바이스 - 디바이스 관리자로 관리   |
| 12           | ISocConsumer      | iSoc 소비자 디바이스                                |
| 13           | Unix              | Unix 디바이스                                         |
| 14           | MacMDM            | 기본 MDM 에이전트로 관리되는 Mac OS X 디바이스 |
| 15           | HoloLens          | Holo Lens 디바이스                                    |
| 16           | SurfaceHub        | Surface Hub 디바이스                                  |
| 17           | AndroidForWork    | Android Profile Owner로 관리되는 Android 디바이스  |
| 18           | AndroidEnterprise | Android 엔터프라이즈 디바이스                          |
| 100          | Blackberry        | Blackberry 디바이스                                   |
| 101          | Palm              | Palm 디바이스                                         |
| 255          | Unknown           | 알 수 없는 디바이스 유형                                 |

## <a name="deviceenrollmenttypes"></a>deviceEnrollmentTypes
**deviceEnrollmentType** 엔터티는 디바이스를 등록하는 방식을 나타냅니다. 등록 형식은 등록 메서드를 캡처합니다. 예시는 서로 다른 등록 형식 및 그 의미를 표시합니다.

|         속성         |                                    설명                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | 등록 유형의 고유 식별자입니다.                                       |
| deviceEnrollmentTypeKey  | 데이터 웨어하우스의 등록 유형의 고유 식별자 - 서로게이트 키 |
| deviceEnrollmentTypeName | 등록 유형 이름                                                           |

### <a name="example"></a>예제

| enrollmentTypeID |                이름                |                                        설명                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Unknown                            | 등록 형식이 수집되지 않았습니다.                                                      |
| 1                | UserEnrollment                     | BYOD 채널을 통한 사용자 구동 등록입니다.                                           |
| 2                | DeviceEnrollmentManager            | 디바이스 등록 관리자 계정을 사용하여 사용자 등록                              |
| 3                | AppleBulkWithUser                  | 사용자 챌린지를 사용한 Apple 대량 등록 (DEP, Apple Configurator)                   |
| 4                | AppleBulkWithoutUser               | 사용자 챌린지를 사용하지 않은 Apple 대량 등록   (DEP, Apple Configurator, 모바일 구성) |
| 5                | WindowsAzureADJoin                 | Windows 10 Azure AD 조인                                                                |
| 6                | WindowsBulkUserless                | 인증서를 사용하여 ICD를 통해 Windows 10 대량 등록                               |
| 7                | WindowsAutoEnrollment              | Windows 10 자동 등록   (회사 계정 추가)                                    |
| 8                | WindowsBulkAzureDomainJoin         | Windows 10 대량 Azure AD 조인                                                           |
| 9                | WindowsCoManagement                | AutoPilot 또는 그룹 정책에 의해 트리거되는 Windows 10 공동 관리                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | 디바이스 인증을 사용하는 Windows 10 Azure AD 조인                                            |

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
| count                         | 위의 분류와 일치하는 등록 작업의 총 수입니다.  |

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

## <a name="intunemanagementextensions"></a>intuneManagementExtensions
**intuneManagementExtension**은 각 Windows 10 디바이스의 **intuneManagementExtension** 상태를 일별로 나열합니다. 데이터는 최근 60일 동안 보존됩니다.

|       속성      |                          설명                          | 예제 |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | 날짜의 고유 식별자입니다.                                | 123     |
| TenantKey           | 테넌트의 고유 식별자입니다.                              | 456     |
| DeviceKey           | 디바이스의 고유 식별자입니다.                              | 789     |
| ExtensionVersionKey | IntuneManagementExtension 버전의 고유 식별자입니다. | 1       |
| ExtensionStateKey   | 상태의 고유 식별자입니다.                            | 2       |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates
**IntuneManagementExtensionHealthState**는 **IntuneManagementExtension**의 가능한 상태를 모두 나열합니다.

|      속성     |                   설명                  | 예제 |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | 상태의 고유 식별자입니다.           | 2       |
| ExtensionState    | IntuneManagementExtension의 상태입니다. | 정상 |

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions
**IntuneManagementExtensionVersion** 엔터티는 **IntuneManagementExtension**에서 사용하는 모든 버전을 나열합니다.

|       속성      |                          설명                          | 예제 |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | IntuneManagementExtension 버전의 고유 식별자입니다. | 1       |
| ExtensionVersion    | 4 자리 버전 번호입니다.                                   | 1.0.2.0 |

## <a name="managementagenttypes"></a>managementAgentTypes
**managementAgentType** 엔터티는 디바이스 관리에 사용되는 에이전트를 나타냅니다.

|         속성        |                                       설명                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | 관리 에이전트 유형에 대한 고유 식별자                                         |
| ManagementAgentTypeKey  | 데이터 웨어하우스의 관리 에이전트 유형의 고유 식별자 - 서로게이트 키 |
| ManagementAgentTypeName | 디바이스 관리에 사용되는 에이전트의 종류를 나타냅니다.                              |

### <a name="example"></a>예제

| ManagementAgentTypeID |                이름               |                                  설명                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | 디바이스가 Exchange Active Sync를 통해 관리됨                         |
| 2                     | MDM                               | 디바이스가 MDM 에이전트를 사용하여 관리됨                                   |
| 3                     | EasMdm                            | 디바이스가 Exchange Active Sync와 MDM 에이전트를 둘 다 사용하여 관리됨        |
| 4                     | IntuneClient                      | 디바이스가 Intune PC 에이전트로 관리됨                               |
| 5                     | EasIntuneClient                   | 디바이스가 Exchange Active Sync와 Intune PC 에이전트를 둘 다 사용하여 관리됨 |
| 8                     | ConfigManagerClient               | 디바이스가 System Center Configuration Manager 에이전트를 사용하여 관리됨     |
| 10                    | ConfigurationManagerClientMdm     | 디바이스가 Configuration Manager 및 MDM에서 관리됩니다.                    |
| 11                    | ConfigurationManagerCLientMdmEas  | 디바이스가 Configuration Manager, MDM 및 Eas에서 관리됩니다.               |
| 16                    | Unknown                           | 알 수 없는 관리 에이전트 유형                                              |
| 32                    | Jamf                              | 디바이스 특성은 Jamf에서 가져옵니다.                               |
| 64                    | GoogleCloudDevicePolicyController |  디바이스가 Google의 CloudDPC에서 관리됩니다.                                 |

## <a name="managementstates"></a>managementStates
**ManagementState** 엔터티는 디바이스의 상태의 세부 정보를 제공합니다. 세부 정보는 원격 작업을 적용할 때, 디바이스를 탈옥 또는 루팅한 경우 유용합니다.

|       속성      |                                     설명                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | 관리 상태의 고유 식별자입니다.                                       |
| managementStateKey  | 데이터 웨어하우스에서 관리 상태의 고유 식별자 - 서로게이트 키 |
| managementStateName | 이 디바이스에 적용된 원격 작업의 상태를 나타냅니다.                 |

### <a name="example"></a>예제

| managementStateID |      이름      |                                                   설명                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | 관리 대상        | 보류 중인 원격 작업 없이 관리됩니다.                                                                       |
| 1                 | RetirePending  | 디바이스에 대해 보류 중인 사용 중지 명령이 있습니다.                                                             |
| 2                 | RetireFailed   | 디바이스에서 사용 중지 명령에 실패했습니다.                                                                      |
| 3                 | WipePending    | 디바이스에 대해 보류 중인 초기화 명령이 있습니다.                                                               |
| 4                 | WipeFailed     | 디바이스에서 초기화 명령에 실패했습니다.                                                                        |
| 5                 | Unhealthy      | 비정상 상태입니다.                                                                                              |
| 6                 | DeletePending  | 디바이스에 대한 보류 중인 삭제 명령이 있습니다.                                                             |
| 7                 | RetireIssued   | 디바이스에 대한 사용 중지 명령이 실행되었습니다.                                                               |
| 8                 | WipeIssued     | 초기화 명령이 실행되었습니다.                                                                               |
| 9                 | WipeCanceled   | 초기화 명령이 취소되었습니다.                                                                               |
| 10                | RetireCanceled | 사용 중지 명령이 취소되었습니다.                                                                             |
| 11                | Discovered     | Intune에서 디바이스를 새로 검색하고 해당 디바이스를 처음으로 체크 인하면 '관리됨' 상태가 됩니다. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates
MobileAppInstallState 엔터티는 장치, 사용자 또는 둘 다를 포함하는 그룹에 할당된 후 모바일 애플리케이션의 설치 상태를 나타냅니다.

|       속성      |                        설명                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | 계정에 대한 앱 설치 상태의 고유 ID입니다. |
| AppInstallState     | 앱 설치 상태의 열거형 값입니다.                     |
| AppInstallStateName | 앱 설치 상태의 이름입니다.                           |

## <a name="mobileappinstallstatuscounts"></a>mobileAppInstallStatusCounts
Microsoft Intune을 통해 모바일 애플리케이션 관리를 사용하여 지정된 대상 장치 유형의 모바일 앱 설치 상태를 나타냅니다.

|      속성      |                                                          설명                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | 앱 설치 상태가 기록된 날짜의 키입니다.                                                                     |
| AppKey             | AppRevision 인스턴스를 식별하는 데 사용되는 모바일 앱의 키입니다.                                                          |
| DeviceTypeKey      | 모바일 애플리케이션과 연관된 장치 유형의 키입니다.                                                              |
| AppInstallStateKey | MobileAppInstallState 인스턴스를 식별하는 데 사용되는 앱 설치 상태의 키입니다.                                         |
| 오류 코드          | 앱 설치 프로그램, 모바일 플랫폼 또는 서비스에서 반환된 앱 설치와 관련된 오류 코드입니다. |
| 개수              | 총 개수입니다.                                                                                                                  |

## <a name="ownertypes"></a>ownerTypes
**ownerType** 엔터티는 디바이스가 회사 디바이스인지 개인 소유인지 알 수 없는지 나타냅니다.

|    속성   |                                                                                     설명                                                                                    |           예제          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | 소유자 유형에 대한 고유 식별자                                                                                                                                               |                            |
| ownerTypeKey  | 데이터 웨어하우스의 소유자 유형의 고유 식별자 - 서로게이트 키                                                                                                       |                            |
| ownerTypeName | 디바이스 소유자 유형을 나타냅니다. 회사 - 엔터프라이즈 소유 디바이스입니다.  개인 - 개인 소유 디바이스입니다(BYOD).   알 수 없음 - 이 디바이스에 대한 정보가 없습니다. | 회사 개인 알 수 없음 |

> [!Note]  
> 에 대 한 합니다 `ownerTypeName` 필터에서 장치에 대 한 동적 그룹을 만들 때 azure Ad에서 값을 설정 해야 `deviceOwnership` 으로 `Company`입니다. 자세한 내용은 [장치에 대 한 규칙](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices)합니다. 

## <a name="policies"></a>정책
**정책** 엔터티는 디바이스 구성 프로필, 앱 구성 프로필 및 규정 준수 정책을 나열합니다. 정책을 MDM(Mobile Device Management)을 통해 기업 내 그룹에 할당할 수 있습니다.

|          속성          |                                                                       설명                                                                      |                예               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | 데이터 웨어하우스에서 정책을 나타내는 고유 키                                                                                              | 123                                  |
| PolicyId                   | 데이터 웨어하우스의 정책에 대한 고유 식별자                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | 정책 이름                                                                                                                                    | "Windows 10 Baseline"                |
| PolicyVersion              | 정책 버전 정책이 편집, 변경되었거나 새 버전이 만들어진 날짜입니다.                                                             | 1, 2, 3                              |
| IsDeleted                  | 정책 레코드가 업데이트되었는지 나타냅니다.  True - 정책에 업데이트된 필드를 포함한 새 레코드가 있습니다.  False- 정책의 최신 레코드입니다. | True/False                           |
| StartDateInclusiveUTC      | 데이터 웨어하우스에서 정책을 만든 UTC 날짜 및 시간입니다.                                                                              | 2016/11/23 0:00                      |
| DeletedDateUTC             | IsDeleted를 True로 변경한 UTC 날짜 및 시간                                                                                                   | 2016/11/23 0:00                      |
| RowLastModifiedDateTimeUTC | 데이터 웨어하우스에서 정책을 마지막으로 수정한 UTC 날짜 및 시간입니다.                                                                        | 2016/11/23 0:00                      |

## <a name="policydeviceactivities"></a>policyDeviceActivities
다음 표는 하루에 성공, 보류, 실패 또는 오류 상태에 있는 디바이스의 수를 나열합니다. 수는 데이터별 정책 유형 프로필을 반영합니다. 예를 들어 디바이스가 모든 할당된 정책에 대해 성공 상태에 있으면 그 날에 대해 성공 카운터를 1만큼 높입니다. 디바이스에 두 프로필이 할당된 경우(성공 상태에 하나, 오류 상태에 하나) 엔터티는 성공 카운터를 하나 늘리고 디바이스를 오류 상태에 놓습니다. **policyDeviceActivity** 엔터티는 지난 30일 동안 특정 날짜에 해당 상태에 있는 디바이스가 몇 개인지 표시합니다.

|  속성 |                                           설명                                           |        예제        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | 데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키 | 20160703              |
| Pending   | 보류 중 상태에 있는 고유 디바이스의 수                                                    | 123                   |
| 성공 | 성공 상태에 있는 고유 디바이스의 수                                                    | 12                    |
| PolicyKey | 정책 키 - Policy와 조인하여 policyName을 가져올 수 있습니다.                                  | Windows 10 기준 |
| 오류     | 오류 상태에 있는 고유 디바이스의 수                                                      | 10                    |
| Failed    | 실패 상태에 있는 고유 디바이스의 수                                                     | 2                     |

## <a name="policyplatformtypes"></a>policyPlatformTypes

|        속성        |                      설명                      |     예제    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | 정책 플랫폼 유형에 대한 고유 키입니다.        | 20170519       |
| PolicyPlatformTypeId   | 정책 플랫폼 유형의 고유 식별자입니다. | 1              |
| PolicyPlatformTypeName | 정책 플랫폼 유형의 이름입니다.              | AndroidForWork |

## <a name="policytypeactivities"></a>policyTypeActivities
**PolicyTypeActivity** 엔터티는 성공, 보류, 실패 또는 오류 상태에 있는 디바이스의 누적 수를 표시합니다. 하루의 디바이스 구성 프로필, 앱 구성 프로필, 규정 준수 정책에 대한 상태를 표시합니다.

|    속성   |                                          설명                                          |           예제           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | 데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키 | 20160703                    |
| PolicyKey     | 정책 키 - Policy와 조인하여 policyName을 가져올 수 있습니다.                                | Windows 10 기준         |
| PolicyTypeKey | 정책 키 유형 - Policy Type과 조인하여 정책 유형 이름을 가져올 수 있습니다.             | Windows10 준수 정책 |
| Pending       | 보류 중 상태에 있는 고유 디바이스의 수                                                    | 123                         |
| 성공     | 성공 상태에 있는 고유 디바이스의 수                                                    | 12                          |
| 오류         | 오류 상태에 있는 고유 디바이스의 수                                                      | 10                          |
| Failed        | 실패 상태에 있는 고유 디바이스의 수                                                     | 2                           |

## <a name="policytypes"></a>policyTypes
**PolicyType** 엔터티는 디바이스 구성 프로필, 앱 구성 프로필 및 규정 준수 정책 유형을 나열합니다. 정책을 MDM(Mobile Device Management)을 통해 기업 내 그룹에 할당할 수 있습니다.

|    속성    |                       설명                      |            예제            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | 원본 시스템의 정책에 대한 고유 식별자  | 123                           |
| PolicyTypeKey  | 데이터 웨어하우스의 정책에 대한 고유 식별자 | 1                             |
| PolicyTypeName | 정책 형식의 이름입니다.                               | Windows 10 준수 정책 |

## <a name="policyuseractivities"></a>policyUserActivities
다음 표는 하루에 성공, 보류, 실패 또는 오류 상태에 있는 사용자 수를 나열합니다. 수는 데이터별 정책 유형 프로필을 반영합니다. 예를 들어 사용자가 모든 할당된 정책에 대해 성공 상태에 있으면 해당 날짜에 대한 성공 카운터를 1만큼 높입니다. 사용자에게 두 프로필이 할당된 경우(하나는 성공 상태, 하나는 오류 상태) 오류 상태의 사용자를 카운트합니다. **PolicyUserActivity** 엔터티는 지난 30일 동안 특정 날짜에 몇 명의 사용자가 어떤 상태에 있었는지 표시합니다.

|  속성 |                                          설명                                          |       예제       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | 데이터 웨어하우스에서 디바이스 구성 프로필 체크 인을 기록했을 때의 날짜 키 | 20160703            |
| Pending   | 보류 중 상태에 있는 고유 디바이스의 수                                                    | 123                 |
| 성공 | 성공 상태에 있는 고유 디바이스의 수                                                    | 12                  |
| PolicyKey | 정책 키 - Policy와 조인하여 policyName을 가져올 수 있습니다.                                | Windows 10 기준 |
| 오류     | 오류 상태에 있는 고유 디바이스의 수                                                      | 10                  |

## <a name="termsandconditions"></a>termsAndConditions
**termsAndConditions** 엔터티는 지정된 사용 약관(T&C) 정책의 메타데이터와 내용을 나타냅니다. T&C 정책의 내용은 사용자가 Intune에 처음으로 등록 시도를 한 경우와 이후에 관리자의 재수락이 필요한 내용을 편집한 경우 표시됩니다. 이를 통해 관리자는 Intune에 디바이스를 등록하기 위해 사용자가 동의해야 하는 조항을 전달할 수 있습니다.

|    속성        |    설명    |    예제        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    'userTermsAndConditionsAcceptances' 컬렉션의 항목에 해당하는 키입니다.    |    123    |
|    termsAndCondidionsId    |    termsAndConditions 항목의 ID입니다.    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    이 사용 약관 항목의 버전입니다.    |    1    |
|    (이름)    |    이 termsAndConditions 항목의 이름입니다.        |    Intune 사용 약관     |
|    description    |    이러한 사용 약관의 설명입니다.     |         |
|    title    |    이러한 사용 약관의 제목입니다.     |    디바이스 관리 회사 정책        |
|    summaryOfTerms    |    사용자에게 제공된 조건의 요약입니다.     |    사용 약관에 동의함    |
|    termsAndConditionsBodyText    |    사용 약관의 텍스트 본문입니다.       |    *디바이스 암호화* - 6자리 PIN 적용    |
|    isDeleted    |    이 값이 삭제되었는지 여부에 대한 참 또는 거짓 값입니다.     |    False    |
|    startDateInclusiveUTC    |    사용 약관이 적용되는 시작 날짜입니다.     |    2018/8/23 4:01:34 AM    |
|    endDateEclusiveUTC    |    사용 약관의 종료 날짜입니다.     |    9999/12/31 12:00:00 AM    |

## <a name="userdeviceassociations"></a>userDeviceAssociations
**UserDeviceAssociation** 엔터티에는 조직의 사용자 디바이스 연결이 포함되어 있습니다.

|        이름        |                                             설명                                            |     예제     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | 데이터 웨어하우스에서 사용자의 고유 식별자입니다.   (서로게이트 키입니다.)                            | 123             |
| DeviceKey          | 데이터 웨어하우스의 디바이스에 대한 고유 식별자                                             | 123             |
| CreatedDateTimeUTC | 사용자 디바이스 연결을 만든 날짜 및 시간입니다. UTC 형식을 사용합니다.                     | 2016/11/23 0:00 |
| IsDeleted          | 사용자가 해당 디바이스를 등록 취소했으며 연결이 현재 더 이상 존재하지 않음을 나타냅니다. | True/False      |
| EndedDateTimeUTC   | IsDeleted를 True로 변경한 UTC 날짜 및 시간                                               | 2017/6/23 0:00  |

## <a name="users"></a>사용자
**사용자** 엔터티는 회사 내 할당된 라이선스가 있는 모든 Azure Active Directory(Azure AD) 사용자를 나열합니다.

**사용자** 엔터티 컬렉션에는 사용자 데이터가 포함됩니다. 이러한 레코드에는 사용자가 제거된 경우에도 데이터 컬렉션 기간의 사용자 상태가 포함됩니다. 예를 들어, 사용자가 Intune에 추가된 다음 지난달 중에 제거되었을 수 있습니다. 보고 시점에는 이 사용자가 없지만 이전 달의 데이터에는 사용자와 상태가 있습니다. 데이터에 있는 사용자의 현재 상태 기록에 대한 기간을 보여 주는 보고서를 만들 수 있습니다.

|          속성          |                                                                                                           설명                                                                                                          |                예제               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | 데이터 웨어하우스의 사용자의 고유 식별자 - 서로게이트 키                                                                                                                                                         | 123                                  |
| UserId                     | 사용자의 고유 식별자는 UserKey와 비슷하지만 자연 키입니다.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | 사용자의 이메일 주소                                                                                                                                                                                                     | John@constoso.com                    |
| UPN                        | 사용자의 사용자 계정 이름입니다.                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | 사용자의 표시 이름                                                                                                                                                                                                      | John                                 |
| IntuneLicensed             | 이 사용자의 Intune 라이선스 여부를 나타냅니다.                                                                                                                                                                              | True/False                           |
| IsDeleted                  | 사용자의 모든 라이선스가 만료되었는지 여부와 이에 따라 사용자가 Intune에서 제거되었는지 여부를 나타냅니다. 단일 레코드의 경우 이 플래그는 변경되지 않습니다. 대신 새 사용자 상태의 새 레코드가 만들어집니다. | True/False                           |
| RowLastModifiedDateTimeUTC | 데이터 웨어하우스에서 레코드를 마지막으로 수정한 UTC 날짜 및 시간                                                                                                                                                 | 2016/11/23 0:00                      |

## <a name="usertermsandconditionsacceptances"></a>userTermsAndConditionsAcceptances
**userTermsAndConditionsAcceptance** 엔터티는 지정된 사용자의 T&C(사용 약관) 정책 수락 상태를 나타냅니다. 사용자가 회사 포털에 계속 액세스하려면 최신 버전의 약관에 동의해야 합니다.

|    속성    |    설명    |    예제    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    '날짜' 컬렉션에 있는 날짜 값에 해당하는 키입니다.     |    20180823    |
|    userKey    |    '사용자' 컬렉션에 있는 사용자의 사용자 키 매핑입니다.     |    20000    |
|    termsAndConditionsKey    |    'termsAndConditions' 컬렉션의 항목에 해당하는 키입니다.    |    1    |
|    acceptedDateTimeUTC    |    사용자가 사용 약관을 수락한 시간입니다.    |    2018/8/23 4:01:34 AM    |
|    lastModifiedDateTimeUTC    |    이 항목이 마지막으로 수정된 시간입니다.     |    2018/8/23 4:01:34 AM    |

## <a name="vppprogramtypes"></a>vppProgramTypes 
**vppProgramType** 엔터티는 앱에 대해 가능한 VPP 프로그램 유형을 나열합니다.

|      속성      |          설명         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | 형식에 대한 ID           |
| VppProgramTypeKey  | 키에 대한 서로게이트 키 |
| VppProgramTypeName | VPP 프로그램 유형          |

### <a name="example"></a>예제

|             VppProgramID             |         이름        | 설명                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | Microsoft의 VPP 프로그램 |
| 00000000-0000-0000-0000-000000000000 | 아직 사용할 수 없음 | 기본값, VPP 없음   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | Apple의 VPP 프로그램     |

## <a name="next-steps"></a>다음 단계

Intune 데이터 웨어하우스의 자세한 내용은 [데이터 웨어하우스 데이터 모델](https://docs.microsoft.com/intune/reports-ref-data-model)을 참조하세요.

