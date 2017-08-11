---
title: "응용 프로그램 | Microsoft 문서"
description: "Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 응용 프로그램 범주에 대한 항목을 참조하세요."
keywords: "Intune 데이터 웨어하우스"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2e12792445b36ba6657cbe6b2f6c924f6d97fe3c
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-application-entities"></a>응용 프로그램 엔터티에 대한 참조

**응용 프로그램** 범주는 다음과 같은 정보를 추적하는 모바일 장치에 대한 엔터티를 포함합니다.

  -  앱 버전
  -  앱의 설치 원본
  -  앱을 만든 개발자의 유형
  -  앱에 대한 관리되는 소프트웨어 유형. 예: **사이드카** 또는 **데스크톱**
  -  앱의 VPP(Volume Purchasing Program) 상태

## <a name="apprevision"></a>AppRevision

**AppRevision** 엔터티는 앱의 모든 버전을 나열합니다.

| 속성  | 설명 | 예 |
|---------|------------|--------|
| AppKey |앱의 고유 식별자 |123 |
| ApplicationId |앱의 고유 식별자 - AppKey와 유사하지만 이 키는 자연어입니다. |b66bc706-ffff-7437-0340-032819502773 |
| 수정 |관리자가 이진 파일을 업로드할 때 언급한 버전 |2 |
| 제목 |앱의 이름 |Excel |
| 게시자 |앱의 게시자 |Microsoft |
| UploadState |앱의 업로드 상태 |1 |
| AppTypeKey |다음 섹션에 설명된 AppType에 대한 참조입니다. | |
| VppProgramTypeKey |아래에 설명된 VppProgramType에 대한 참조 | |
| CreationTime |이 수정 버전을 만든 시간 |11/23/2016 12:00:00 AM |
| ModifiedTime |이 수정 버전과 관련된 항목이 마지막으로 변경된 시간 |11/23/2016 12:00:00 AM |
| Size |이진 파일의 크기 | |
| StartDateInclusiveUTC |이 앱 수정 버전이 데이터 웨어하우스에서 생성된 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |이 앱 수정 버전이 중단되는 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |
| IsCurrent |이 앱 버전이 최신인지 또는 데이터 웨어하우스에 없는지 표시 |True/False |
| RowLastModifiedDateTimeUTC |데이터 웨어하우스에서 이 앱 버전을 마지막으로 수정한 UTC 날짜 및 시간 |11/23/2016 12:00:00 AM |

## <a name="appinstallertypes"></a>AppInstallerTypes

**AppInstallerTypes** 엔터티는 앱의 설치 원본을 나열합니다.

| 속성  | 설명 |
|---------|------------|
| AppTypeID |형식에 대한 ID |
| AppTypeKey |키에 대한 대리 키 |
| AppTypeName |앱 유형 |

## <a name="example"></a>예

| AppTypeID  | Name | 설명 |
|---------|------------|--------|
| 0 |Android 스토어 앱 |Android 스토어 앱 |
| 1 |Android LOB 앱 |Android 기간 업무 앱 |
| 2 |관리되는 Android 스토어 앱(MAM) |관리를 사용하도록 설정한 Android 스토어 앱 |
| 3 |iOS 스토어 앱 |iOS 스토어 앱 |
| 4 |iOS LOB 앱 |iOS 기간 업무 앱 |
| 5 |관리되는 iOS 스토어 앱(MAM?) |관리를 사용하도록 설정한 iOS 스토어 앱 |
| 6 |O365 Pro Plus 도구 모음 |Windows 10용 Office 365 Pro Plus 제품군 |
| 7 |웹앱 |웹앱 |
| 8 |Windows Phone 8.1 스토어 앱 |Windows Phone 8.1 스토어 앱 |
| 9 |Windows 스토어 앱 |Windows 스토어 앱 |
| 10 |Windows LOB 앱 |Windows AppX 기간 업무 앱 |
| 11 |Windows Mobile MSI |MSI 기간 업무 앱 |
| 12 |Windows Phone LOB 앱 |Windows Phone LOB(기간 업무) 앱 |

## <a name="applicationtypes"></a>ApplicationTypes

**ApplicationTypes** 엔터티는 앱에 대해 가능한 유형을 나열합니다.

| 속성  | 설명 |
|---------|------------|
| ApplicationTypeID |형식에 대한 ID |
| ApplicationTypeKey |키에 대한 대리 키 |
| ApplicationTypeName |앱 유형 |

## <a name="example"></a>예

| ApplicationTypeID  | Name | 설명 |
|---------|------------|--------|
| 0 |InHouse |사내에서 개발한 앱 |
| 1 |DeepLink |앱 스토어 앱에 대한 링크 |
| 2 |WebLink |웹앱에 대한 링크 |

## <a name="managedsoftwaretypes"></a>ManagedSoftwareTypes

**ManagedSoftwareTypes** 엔터티는 앱에 대해 가능한 관리 소프트웨어 유형을 나열합니다.

| 속성  | 설명 |
|---------|------------|
| SoftwareTypeID |형식에 대한 ID |
| SoftwareTypeKey |키에 대한 대리 키 |
| SoftwareTypeName |소프트웨어 종류 |

## <a name="example"></a>예

| SoftwareTypeID  | Name | 설명 |
|---------|------------|--------|
| 0 |데스크톱 |데스크톱 앱 |
| 2 |업데이트 |Window 업데이트 |
| 5 |SideCarAgent | |
| 1 |휴대폰 |모바일 앱 |
| 3 |WebLink |웹 링크 |
| 4 |VppDeepLink |VPP(Volume Purchase Program)의 일부인 앱 스토어에서 앱의 링크 |

## <a name="vppprogramtypes"></a>VppProgramTypes

**VppProgramTypes** 엔터티는 앱에 대해 가능한 VPP 프로그램 유형을 나열합니다.

| 속성  | 설명 |
|---------|------------|
| VppProgramTypeID |형식에 대한 ID |
| VppProgramTypeKey |키에 대한 대리 키 |
| VppProgramTypeName |Vpp 프로그램 유형 |

## <a name="example"></a>예

| VppProgramID  | Name | 설명 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 |Microsoft |Microsoft의 VPP 프로그램 |
| 00000000-0000-0000-0000-000000000000 |아직 사용할 수 없음 |기본값, VPP 아님 |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B |Apple |Apple VPP 프로그램 |