---
title: 디바이스 - Intune 데이터 웨어하우스
titlesuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 디바이스 범주에 대한 항목을 참조하세요.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 69c8b4a5b786768d315bfe6ec707b8c4b915c93a
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112938"
---
# <a name="reference-for-devices-entities"></a>디바이스 엔터티에 대한 참조

**장치** 범주는 다음과 같은 정보를 추적하는 모바일 장치에 대한 엔터티를 포함합니다.

  -  디바이스 유형
  -  디바이스 등록 및 등록 상태
  -  디바이스 소유권
  -  디바이스 관리 상태
  -  Azure AD 상태에 대한 디바이스 멤버 자격
  -  등록 상태
  -  디바이스에 대한 과거 정보
  -  디바이스에서 앱의 인벤토리

## <a name="devicetypes"></a>DeviceTypes

**DeviceTypes** 엔터티는 다른 데이터 웨어하우스 엔터티에서 참조하는 장치 유형을 나타냅니다. 디바이스 유형은 일반적으로 디바이스 모델, 제조업체 또는 두 가지의 조합을 설명합니다.

| 속성  | 설명 |
|---------|------------|
| DeviceTypeID |디바이스 유형의 고유 식별자 |
| DeviceTypeKey |데이터 웨어하우스의 디바이스 유형에 대한 고유 식별자 - 대리 키 |
| DeviceTypeName |디바이스 유형 |

## <a name="example"></a>예제

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
| 15 |HoloLens |Holo Lens 디바이스 |
| 16 |SurfaceHub |Surface Hub 디바이스 |
| 17 |AndroidForWork |Android Profile Owner로 관리되는 Android 디바이스 |
| 100 |Blackberry |Blackberry 디바이스 |
| 101 |Palm |Palm 디바이스 |
| 255 |Unknown |알 수 없는 디바이스 유형 |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

**ClientRegistrationStateTypes** 엔터티는 다른 데이터 웨어하우스 테이블에서 참조하는 등록 형식을 나타냅니다.

| 속성  | 설명 |
|---------|------------|
| clientRegisterationStateID |등록 상태에 대한 고유 식별자 |
| clientRegisterationStateKey |데이터 웨어하우스의 등록 상태에 대한 고유 식별자 - 대리 키 |
| clientRegisterationStateName |등록 상태 |

## <a name="example"></a>예제

| ClientRegisterationStateID  | 이름 | 설명 |
|---------|------------|--------|
| 0 |NotRegistered |등록 안 됨 |
| 1 |SMSIDConflict |SMS ID 충돌 |
| 2 |등록됨 |등록됨 |
| 3 |Revoked |IT 관리자가 클라이언트를 차단했고 클라이언트가 차단될 수 있음을 나타내는 상태입니다. 디바이스는 초기화 또는 사용 중지 후 취소 상태가 될 수 있습니다. |
| 4 |KeyConflict |키 충돌 |
| 5 |ApprovalPending |승인 보류 중 |
| 6 |ResetCert |인증서 재설정 |
| 7 |NotRegisteredPendingEnrollment |등록 안 됨 등록 보류 중 |
| 8 |Unknown |알 수 없는 상태 |

## <a name="enrollmenttypes"></a>EnrollmentTypes

**EnrollmentTypes** 엔터티는 장치를 등록하는 방식을 나타냅니다. 등록 형식은 등록 메서드를 캡처합니다. 예시는 서로 다른 등록 형식 및 그 의미를 표시합니다.

| 속성  | 설명 |
|---------|------------|
| managementStateID |관리 상태의 고유 식별자입니다. |
| managementStateKey |데이터 웨어하우스에서 관리 상태의 고유 식별자 - 대리 키 |
| managementStateName |이 디바이스에 적용된 원격 작업의 상태를 나타냅니다. |

## <a name="example"></a>예제

| enrollmentTypeID  | 이름 | 설명 |
|---------|------------|--------|
| 0 |Unknown |등록 형식이 수집되지 않았습니다. |
| 1 |UserEnrollment |사용자가 시작한 등록 |
| 2 |DeviceEnrollment |사용자 없는 프로필로 디바이스 등록 |
| 3 |DeviceEnrollmentWithUDA |UDA 프로필로 디바이스 등록 |
| 4 |AzureDomainJoined |사용자가 Azure Active Directory를 통해 시작한 디바이스 등록 |
| 5 |UserEnrollmentWithServiceAccount |사용자가 서비스 계정을 통해 시작한 등록 |
| 6 |DepDeviceEnrollment |사용자 없는 프로필로 DEP 디바이스 등록 |
| 7 |DepDeviceEnrollmentWithUDA |UDA 프로필로 DEP 디바이스 등록 |
| 8 |AutoEnrollment |BYOD 시나리오를 위한 결합된 DRS 및 MDM 등록 |

## <a name="ownertypes"></a>OwnerTypes

**EnrollmentTypes** 엔터티는 장치가 회사 장치인지 개인 소유인지 알 수 없는지 나타냅니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| ownerTypeID |소유자 유형에 대한 고유 식별자 | |
| ownerTypeKey |데이터 웨어하우스의 소유자 유형에 대한 고유 식별자 - 서로게이트 키 | |
| ownerTypeName |디바이스의 소유자 유형을 나타냅니다.  <br>회사 - 회사 소유 디바이스입니다. <br>개인 - 개인 소유 디바이스입니다(BYOD).  <br>알 수 없음 - 이 디바이스에 대한 정보가 없습니다. |회사 개인 알 수 없음 |

## <a name="mdmstatuses"></a>MdmStatuses

**MdmStatuses** 엔터티는 장치의 준수 상태를 나타냅니다.

| 속성  | 설명 |
|---------|------------|
| MdmStatusID |준수 상태의 고유 식별자 |
| MdmStatusKey |데이터 웨어하우스에서 규정 준수 상태의 고유 식별자 - 대리 키 | 
| ComplianceStatus |디바이스의 준수 상태, 아래 표의 값 중 하나가 있어야 함 | 


## <a name="example"></a>예제

| MdmStatusID  | ComplianceStatus | 설명 |
|---------|------------|--------|
| 0 |Unknown |디바이스의 준수 상태를 알 수 없습니다. |
| 1 |규정 |디바이스가 준수 상태입니다. |
| 2 |정책 위반 |디바이스가 준수 상태가 아닙니다. |
| 3 |Conflict |디바이스의 준수로 인해 충돌이 발생했습니다. |
| 4 |오류 |디바이스의 준수 상태를 읽는 동안 오류가 발생했습니다. |


## <a name="managementstates"></a>ManagementStates

**ManagementStates** 엔터티는 장치의 상태에 대한 세부 정보를 제공합니다. 세부 정보는 원격 작업을 적용할 때, 디바이스를 탈옥 또는 루팅한 경우 유용합니다.

| 속성  | 설명 |
|---------|------------|
| managementStateID | 관리 상태의 고유 식별자입니다. |
| managementStateKey | 데이터 웨어하우스에서 관리 상태의 고유 식별자 - 대리 키 |
| managementStateName | 이 디바이스에 적용된 원격 작업의 상태를 나타냅니다. |

## <a name="example"></a>예제

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

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

**WorkPlaceJoinStateTypes** 엔터티는 장치의 Azure Active Directory Workplace Join 상태를 나타냅니다.  등록 워크플로는 하나 이상의 인증서를 사용하여 인증할 수 있습니다. 디바이스 WorkPlace가 등록되면 이 인증서가 디바이스와 사용자를 인증하는 데 사용됩니다. 인증서 발급은 SCEP(단순 인증서 등록 지점) 서버를 통해 제공됩니다. 엔터티 내의 값은 이 프로세스를 거치는 동안 디바이스의 다양한 상태를 나타냅니다. 여기에는 필수 인증서(SCEP 서버에서) 발행 실패로 인한 WorkPlace 참여 실패가 포함됩니다. 디바이스가 이 워크플로를 통과하지 않으면 값이 알 수 없음으로 설정됩니다.

| 속성  | 설명 |
|---------|------------|
| WorkPlaceJoinStateID | 작업 공간 참여 상태의 고유 식별자 |
| WorkPlaceJoinStateKey | 데이터 웨어하우스에서 작업 공간 참여 상태에 대한 고유 식별자 - 대리 키 |
| WorkPlaceJoinStateName | 작업 공간 참여 상태 |

## <a name="example"></a>예제

| workPlaceJoinStateID  | 이름 | 설명 |
|---------|------------|--------|
| 0 |Unknown |디바이스가 작업 공간 참여 상태가 아니면 알 수 없는 상태임 |
| 1 |성공 |작업 공간 참여 성공 |
| 2 |FailureToGetScepMetadata |SCEP 메타데이터 가져오기 실패 |
| 3 |FailureToGetScepChallenge |SCEP 챌린지를 가져오기 실패 |
| 4 |DeviceFailureToInstallScepCommand |디바이스에서 SCEP 명령 설치 실패 |
| 5 |DeviceFailureToGetCertificate |디바이스에서 SCEP를 통한 인증서 가져오기 실패 |
| 6 |DeviceScepPending |보류 중인 상태. 디바이스가 아직 SCEP 수행 중 |
| 7 |DeviceScepFailed |디바이스가 SCEP를 통해 인증서를 설치하지 못함 |
| 8 |AADValidationFailed |디바이스가 AAD에 존재함을 확인하지 못함 |

## <a name="managementagenttypes"></a>ManagementAgentTypes

**ManagementAgentTypes** 엔터티는 장치 관리에 사용되는 에이전트를 나타냅니다.

| 속성  | 설명 |
|---------|------------|
| ManagementAgentTypeID | 관리 에이전트 유형에 대한 고유 식별자 |
| ManagementAgentTypeKey | 데이터 웨어하우스의 관리 에이전트 유형에 대한 고유 식별자 - 서로게이트 키 |
| ManagementAgentTypeName |디바이스 관리에 사용되는 에이전트의 종류를 나타냅니다. |

## <a name="example"></a>예제

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

**장치** 엔터티는 관리 대상인 모든 등록된 장치와 그에 해당하는 속성을 나열합니다.

| 속성  | 설명 |
|---------|------------|
| DeviceKey | 데이터 웨어하우스에서 디바이스의 고유 식별자 - 대리 키 |
| DeviceId | 디바이스에 대한 고유 식별자 |
| DeviceName | 디바이스 이름 지정을 허용하는 플랫폼에서 디바이스의 이름입니다. 다른 플랫폼에서 Intune은 다른 속성으로부터 이름을 만듭니다. 이 특성은 모든 디바이스에 대해 사용할 수 없습니다. |
| DeviceTypeKey | 이 디바이스에 대한 디바이스 유형 특성의 키 |
| ClientRegisterationStateKey | 이 디바이스에 대한 클라이언트 등록 상태 특성의 키 |
| OwnerTypeKey | 이 디바이스에 대한 소유자 유형 특성의 키: 회사, 개인 또는 알 수 없음. |
| objectSourceKey | 이 열을 무시합니다. |
| CreatedDate | 디바이스를 등록한 날짜 |
| LastContact | Intune에서 마지막으로 인식된 디바이스 체크 인 |
| LastContactNotification | Intune에서 디바이스를 체크 인하도록 마지막으로 알린 시간 |
| LastContactWorkplaceJoin | 이 디바이스에 대한 마지막으로 알려진 작업 공간 참여 상태를 나타내는 타임스탬프입니다. |
| ManagementAgentKey | 이 디바이스와 연결된 관리 에이전트의 키입니다. |
| ManagementStateKey | 이 디바이스와 연결된 관리 상태의 키로 원격 작업의 마지막 상태를 나타내거나 탈옥/루팅 여부를 나타냅니다. |
| 참조 | Azure Active Directory의 디바이스 ID |
| WorkPlaceJoinStateKey | 이 디바이스와 연결된 작업 공간 참여 상태의 키입니다. |
| CategoryId | 이 열을 무시합니다. |
| EnrollmentTypeKey | 이 디바이스와 연결된 등록 유형 키로 등록 메서드를 나타냅니다. |
| CertExpirationDate | MDM 관리 인증서의 만료 날짜입니다. |
| MdmStatusKey | MdmStatus에 대한 키 |
| OSFamily | OS 제품군(Windows, iOS, Android 등) |
| OSVersion | OS 버전 |
| OSMajorVersion | OS 버전의 주 버전 구성 요소(major.minor.build.revision) |
| OSMinorVersion | OS 버전의 부 버전 구성 요소(major.minor.build.revision) |
| OSBuildNumber | OS 버전의 빌드 버전 구성 요소(major.minor.build.revision) |
| OSRevisionNumber | OS 버전의 수정 버전 구성 요소(major.minor.build.revision) |
| EasID | Exchange Active Sync에서 관리하는 디바이스의 경우 이 디바이스의 EAS ID입니다. |
| GraphDeviceIsManaged | Intune이 Azure AD에서 마지막으로 설정한 관리 상태 |
| GraphDeviceIsCompliant | Intune이 Azure AD에서 마지막으로 설정한 준수 상태 |
| SerialNumber | 디바이스의 일련 번호(사용 가능한 경우) |
| EnrolledByUser | 사용자 테이블의 사용자 ID 열을 참조하는 이 디바이스를 등록한 사용자의 ID입니다. |
| RowLastModifiedDateTimeUTC | 이 레코드를 마지막으로 수정한 시간입니다. |
| ProcessorArchitecture | 프로세서 아키텍처 |
| DeviceAction | 마지막으로 실행된 디바이스 작업. 지금은 무시합니다. |
| 제조업체 | 디바이스 제조업체 |
| 모델 | 디바이스 모델 |
| LastPolicyUpdateUtc | 디바이스에서 정책을 마지막으로 업데이트한 시간 |
| LastExchangeStatusUtc | 디바이스를 exchange와 마지막으로 동기화한 시간입니다. |
| IsDeleted | 더 이상 Intune에서 디바이스를 관리하지 않는 경우 True로 설정합니다. 마지막으로 알려진 상태를 유지합니다. |
| AndroidSecurityPatchLevel |디바이스의 가장 최근 보안 패치 날짜입니다. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

**DevicePropertyHistory** 엔터티는 지난 90일 동안 하루에 각 장치 레코드의 장치 테이블 및 일일 스냅숏과 동일한 속성을 지닙니다. DateKey 열은 각 행에 대한 날짜를 나타냅니다.

| 속성  | 설명 |
|---------|------------|
| DateKey |날짜를 나타내는 날짜 테이블에 대한 참조 |
| DeviceKey |데이터 웨어하우스에서 디바이스의 고유 식별자 - 대리 키 Intune 디바이스 ID가 포함된 디바이스 테이블에 대한 참조입니다. |
| DeviceName |디바이스 이름 지정을 허용하는 플랫폼에서 디바이스의 이름입니다. 다른 플랫폼에서 Intune은 다른 속성으로부터 이름을 만듭니다. 이 특성은 모든 디바이스에 대해 사용할 수 없습니다. |
| DeviceTypeKey |이 디바이스에 대한 디바이스 유형 특성의 키 |
| ClientRegisterationStateKey |이 디바이스에 대한 클라이언트 등록 상태 특성의 키 |
| OwnerTypeKey |이 디바이스에 대한 소유자 유형 특성의 키: 회사, 개인 또는 알 수 없음. |
| objectSourceKey |이 열을 무시합니다. |
| CreatedDate |디바이스를 등록한 날짜 |
| LastContact |Intune에서 마지막으로 인식된 디바이스 체크 인 |
| LastContactNotification |Intune에서 디바이스를 체크 인하도록 마지막으로 알린 시간 |
| LastContactWorkplaceJoin |이 디바이스에 대한 마지막으로 알려진 작업 공간 참여 상태를 나타내는 타임스탬프입니다. |
| ManagementAgentKey |이 디바이스와 연결된 관리 에이전트의 키입니다. |
| ManagementStateKey |이 디바이스와 연결된 관리 상태의 키로 원격 작업의 마지막 상태를 나타내거나 탈옥/루팅 여부를 나타냅니다. |
| 참조 |Azure Active Directory의 디바이스 ID |
| WorkPlaceJoinStateKey |이 디바이스와 연결된 작업 공간 참여 상태의 키입니다. |
| CategoryId |이 열을 무시합니다. |
| EnrollmentTypeKey |이 디바이스와 연결된 등록 유형 키로 등록 메서드를 나타냅니다. |
| CertExpirationDate |MDM 관리 인증서의 만료 날짜입니다. |
| MdmStatusKey |MdmStatus에 대한 키 |
| OSFamily |OS 제품군(Windows, iOS, Android 등) |
| OSVersion |OS 버전 |
| OSMajorVersion |OS 버전의 주 버전 구성 요소(major.minor.build.revision) |
| OSMinorVersion |OS 버전의 부 버전 구성 요소(major.minor.build.revision) |
| OSBuildNumber |OS 버전의 빌드 버전 구성 요소(major.minor.build.revision) |
| OSRevisionNumber |OS 버전의 수정 버전 구성 요소(major.minor.build.revision) |
| EasID |Exchange Active Sync에서 관리하는 디바이스의 경우 이 디바이스의 EAS ID입니다. |
| GraphDeviceIsManaged |Intune이 Azure AD에서 마지막으로 설정한 관리 상태 |
| GraphDeviceIsCompliant |Intune이 Azure AD에서 마지막으로 설정한 준수 상태 |
| SerialNumber |디바이스의 일련 번호(사용 가능한 경우) |
| EnrolledByUser |사용자 테이블의 사용자 ID 열을 참조하는 이 디바이스를 등록한 사용자의 ID입니다. |
| RowLastModifiedDateTimeUTC |이 레코드를 마지막으로 수정한 시간입니다. |
| ProcessorArchitecture |프로세서 아키텍처 |
| DeviceAction |마지막으로 실행된 디바이스 작업. 지금은 무시합니다. |
| 제조업체 |디바이스 제조업체 |
| 모델 |디바이스 모델 |
| LastPolicyUpdateUtc |디바이스에서 정책을 마지막으로 업데이트한 시간 |
| LastExchangeStatusUtc |디바이스를 exchange와 마지막으로 동기화한 시간입니다. |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

**MdmDeviceInventoryHistories** 엔터티 지난 90일 동안 MDM 관리 장치에 대한 인벤토리 데이터의 일일 스냅숏을 포함합니다. DateKey 열은 행에 대한 날짜를 나타냅니다. 일부 속성은 모든 디바이스에 대해 적용되지 않거나 입력되지 않을 수 있으므로 이 페이지에서 자세한 내용을 참조하세요. 자세한 내용은 [Microsoft Intune에서 인벤토리를 사용하는 디바이스 이해](device-inventory.md)를 참조하세요.

| 속성  | 설명 |
|---------|------------|
| DateKey | 날짜를 나타내는 날짜 테이블에 대한 참조 |
| DeviceKey |데이터 웨어하우스에서 디바이스의 고유 식별자 - 대리 키 Intune 디바이스 ID가 포함된 디바이스 테이블에 대한 참조입니다. |
| DeviceModel |디바이스 모델 |
| OS |디바이스의 OS |
| DeviceName |디바이스 이름 지정을 허용하는 플랫폼에서 디바이스의 이름입니다. 다른 플랫폼에서 Intune은 다른 속성으로부터 이름을 만듭니다. 이 특성은 모든 디바이스에 대해 사용할 수 없습니다. |
| SoftwareVersion |대부분의 경우 OS 버전이지만 Apple 플랫폼의 경우 예외적으로 OS 버전과 다릅니다. |
| Imei |IMEI 번호 |
| HardwareInventoryTimeUtc |이 디바이스에 대해 처음 인벤토리가 보고된 시간입니다. |
| InventoryModifiedTimeUtc |이 스냅숏을 만들 때 인벤토리를 마지막으로 저장한 시간 |
| InventoryReportingTimeUtc |이 디바이스에 대해 마지막 시간 인벤토리가 수집된 시간입니다. |
| ExchangeActiveSyncId |Exchange ActiveSync 디바이스 ID |
| ComputerSystemDescription |시스템 설명 |
| ComputerSystemName |시스템 이름 |
| ComputerSystemManufacturer |시스템 제조업체 |
| ComputerSystemModel |시스템 모델 |
| UserName |사용자 이름 |
| OSType |OS 유형 |
| OSCaption |OS 캡션 |
| OSName |OS 이름 |
| OSManufacturer |OS 제조업체 |
| OSProductSuite |OS 제품군 |
| OSProductType |OS 제품 종류 |
| 로캘 |OS 로캘 |
| PhysicalMemoryCapacity |실제 메모리 용량(바이트) |
| PhysicalMemoryRemovable |이동식 실제 메모리(바이트) |
| SystemEnclosureChassisTypesInnerText |이 디바이스에 대한 시스템 섀시 종류를 정의합니다. 숫자는 다음 값을 나타냅니다.  <br>0 또는 비어 있음 = 알 수 없음   <br>1 = 데스크톱   <br>2 = 랩톱  <br>3 = 워크스테이션  <br>4 = 엔터프라이즈 서버  <br>100 = 전화기  <br>101 = 태블릿  <br>102/103 = 알 수 없는 다른 유형의 모바일 디바이스 |
| SystemEnclosureModel |시스템 엔클로저 모델 |
| SystemEnclosureSerialNumber |시스템 엔클로저 일련 번호 |
| NetworkAdapterConfigurationText |네트워크 어댑터의 구성 텍스트 |
| MacAddress |MAC 주소 |
| SmsID |Intune 디바이스 ID |
| CertExpiry |MDM 관리 인증서의 만료 날짜입니다. |
| DeviceClientAgentVersion |클라이언트 에이전트 버전 |
| DeviceClientID |디바이스 클라이언트 ID |
| SerialNumber |일련 번호 |
| DeviceManufacturer |디바이스 제조업체 |
| DMVersion |DM 버전 |
| 펌웨어 버전 |펌웨어 버전 |
| HardwareVersion |하드웨어 버전 |
| PlatformType |플랫폼 유형 |
| ProcessorLevel |프로세서 수준 |
| ProcessorRevision |프로세서 수정 버전 |
| 제품 |제품 |
| ProductVersion |제품 버전 |
| OEM |OEM(주문자 상표 부착 제조업체) |
| DeviceBuildVersion |디바이스 빌드 버전 |
| Meid |Mobile Equipment Identifier |
| PhoneNumber |전화 번호 |
| SubscriberCarrierNetwork |전화 통신 회사의 네트워크 이름 |
| CellularTechnology |전화 통신 회사의 네트워크 형식(CDMA/GSM) |
| Imsi |IMSI 번호 |
| 탈옥 |탈옥 또는 루팅 디바이스의 경우 true입니다. |
| IsActivationLockEnabled |True이면 활성화 잠금 사용 |
| DeviceType |디바이스 유형 |
| IsSupervised |감독됨 |
| DeviceDisplayNumberOfColors |디바이스 디스플레이의 색 수 |
| HorizontalResolution |디바이스 가로 화면 해상도 |
| VerticalResolution |디바이스 세로 화면 해상도 |
| StorageFree |사용 가능한 저장소 공간(바이트) |
| StorageTotal |총 저장소 공간(바이트) |
| ProgramFree |사용 가능한 프로그램 메모리(바이트) |
| ProgramTotal |전체 프로그램 메모리(바이트) |
| RemovableStorageFree |사용 가능한 이동식 저장소(바이트) |
| RemovableStorageTotal |총 이동식 저장소(바이트) |
| DeviceMemoryDeviceCapacity |디바이스 메모리 용량 |
| DeviceMemoryAvailableDeviceCapacity |사용 가능한 디바이스 메모리 용량 |
| DeviceOSVersion |OS 버전 |
| DeviceOSPlatform |OS 플랫폼 |
| DeviceOSLanguage |OS 언어 |
| PasswordMaxAttemptsBeforeWipe |디바이스 초기화에 앞서 허용되는 최대 암호 입력 시도 횟수 |
| PasswordMinComplexChars |암호에 필요한 최소 복합 문자 수 |
| PasswordMinLength |필요한 최소 암호 길이 |
| PasswordHistory |암호 - 사용할 수 없는 최소 과거 암호 |
| PasswordEnabled |암호 - 사용할 수 있나요? |
| PasswordExpiration |암호 - 만료 날짜 |
| AllowRecoveryPassword |암호 복구 허용 |
| PasswordAutoLockTimeout |암호 - 자동 잠금 시간 제한 |
| PasswordType |암호 형식 |
| BacklightACTimeout |전원 연결 시 후광 시간 제한 |
| BacklightBatTimeout |배터리 사용 시 후광 시간 제한 |
| PowerBackupPercent |예비 전력 백분율(%) |
| BatteryPercent |남은 배터리 백분율입니다. |
| PlatformID |플랫폼 ID |
| ExchangeDeviceID |Exchange 디바이스 ID |
| SmsProcessorDescription |프로세서 설명 |
| OwnerEmailAddress |소유자의 이메일 주소 |
| DeviceOSName |OS 이름 |
| WifiMac |WIFI Mac 주소 |
| EthernetMac |이더넷 MAC 주소 |
| RequireEncryption |디바이스의 암호화 여부를 나타냅니다. |
| ActivationLockBypassCode |활성화 잠금 무시 코드 |

## <a name="applicationinventory"></a>ApplicationInventory

**ApplicationInventory** 엔터티는 인벤터리 수집 시점에 장치에서 발견된 앱을 나열합니다.


|      속성      |                       설명                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              디바이스 테이블에 대한 참조               |
|   ApplicationKey   | ? (ExchangeDeviceService\DeviceApplication에서 복사) |
|  ApplicationName   | ? (ExchangeDeviceService\DeviceApplication에서 복사) |
| ApplicationVersion | ? (ExchangeDeviceService\DeviceApplication에서 복사) |
|     BundleSize     | ? (ExchangeDeviceService\DeviceApplication에서 복사) |

