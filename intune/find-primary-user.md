---
title: Microsoft Intune 디바이스의 기본 사용자를 찾습니다.
titleSuffix: ''
description: Intune 디바이스의 기본 사용자(또는 사용자 디바이스 선호도)을 찾습니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7c0947438b42f4a2fa5ccae8e9cab07a60167ae
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071693"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Intune 디바이스의 기본 사용자 찾기

사용자 디바이스 선호도라고도 하는 기본 사용자는 각 Intune 디바이스의 속성입니다. Intune 디바이스에는 기본 사용자를 0개나 1개 할당할 수 있습니다. 할당된 기본 사용자가 없는 디바이스는 "공유 디바이스"라고 합니다.

## <a name="how-to-find-a-devices-primary-user"></a>디바이스의 기본 사용자를 찾는 방법

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스** 메뉴를 선택하고 디바이스를 선택합니다.
3. **개요** 페이지에서 **자세히 보기**를 선택하여 기본 사용자를 나열합니다.

## <a name="what-is-the-primary-user"></a>기본 사용자란?
기본 사용자 속성은 다음에서 허가받은 Intune 사용자를 다바이스에 매핑하는 데 사용됩니다.
- 회사 포털 앱
- 최종 사용자 웹 사이트
- Azure Portal의 문제 해결 페이지와 같은 IT 전문가 환경 이러한 페이지에서는 기본 사용자를 사용하여 사용자 계정을 디바이스에 매핑합니다.    

### <a name="company-portal-app"></a>회사 포털 앱
회사 포털 앱에서는 회사 포털에 로그인한 사용자 계정이 해당 디바이스의 기본 사용자라고 예상합니다. 다른 사용자가 기본 사용자로 할당된 경우 회사 포털에서는 경고를 표시합니다.

“이 디바이스가 이미 조직의 다른 사용자에게 할당되었습니다. 회사 지원팀에 기본 디바이스 사용자가 되는 방법을 문의하세요. 회사 포털을 계속 사용할 수는 있지만 기능이 제한됩니다."

Intune 디바이스에 할당된 기본 사용자가 없으면 회사 포털 앱에서 이 디바이스를 공유 디바이스로 감지합니다. 공유 디바이스는 디바이스 제목에 “공유” 레이블이 표시되므로 시각적으로 식별할 수 있습니다. 이 모드에서도 회사 포털을 사용하여 사용 가능한 앱을 요청하고 설치할 수는 있습니다. 그러나 셀프 서비스 작업(재설정/이름 바꾸기/사용 중지)은 사용할 수 없습니다.  

공유 디바이스의 회사 포털에 표시하려면 사용 가능한 앱을 사용자 그룹에 할당해야 합니다. 이러한 앱은 IT 관리자가 구성한 방법에 따라 시스템 컨텍스트나 사용자 컨텍스트에 설치됩니다. 앱 컨텍스트에 대한 자세한 내용은 [Windows 10 디바이스에서 앱 설치](apps-windows-10-app-deploy.md#installing-apps-on-windows-10-devices)를 참조하세요. 이 기능을 사용하려면 회사 포털 10.3.4651.0 이상 버전이 필요합니다.


## <a name="who-is-assigned-as-the-primary-user"></a>누가 기본 사용자로 할당되나요?
Intune에서는 등록하는 중이나 끝나고 바로 디바이스에 기본 사용자를 자동으로 추가합니다. 등록 방법에 따라 기본 사용자가 디바이스에 추가되는 시기가 결정됩니다.

| 플랫폼 | 등록 메서드 | 할당되는 기본 사용자 | 기본 사용자가 할당되는 시기 |
| ---- | ---- | ---- | ---- |
| Windows | 회사 또는 학교 추가(사용자 주도) | 등록하는 사용자 | 등록 중 |   
| Windows | 최신 앱 로그인(사용자 주도) | 등록하는 사용자 | 등록 중 | 
| Windows | MDM에만 등록(사용자 주도) | 등록하는 사용자 | 등록 중 | 
| Windows | Azure AD 조인(기본 제공 환경) | 등록하는 사용자 | 등록 중 | 
| Windows | Azure AD 조인(Autopilot 기본 제공 환경) | 등록하는 사용자 | 등록 중 | 
| Windows | MDM에만 등록 | 등록하는 사용자 | 등록 중 | 
| Windows | 하이브리드 AADJ + 자동 등록 GPO | Windows에 처음 로그인하는 사용자 | Windows에 처음 로그인하는 사용자인 경우| 
| Windows | 공동 관리 | Windows에 처음 로그인하는 사용자 | Windows에 처음 로그인하는 사용자인 경우 | 
| Windows | Azure AD 조인(대량 등록 토큰) | 없음 | 해당 없음 | 
| Windows | Azure AD 조인(Autopilot 자체 배포 모드) | 없음 | 해당 없음 | 
| 플랫폼 간 사용 가능 | 회사 포털 앱을 사용한 사용자 주도 등록 | 등록하는 사용자 | 등록 중 |
| 플랫폼 간 사용 가능 | DEM(디바이스 등록 관리자) | 등록하는 DEM 사용자 | 등록 중 |
| iOS, macOS | 사용자 선호도를 사용한 Apple DEP(자동 디바이스 등록) | 등록하는 사용자 | 등록 중 |
| iOS, macOS | 사용자 선호도를 사용하지 않는 Apple DEP(자동 디바이스 등록) | 없음 | 해당 없음 |
| Android | Android 회사 소유 전용 디바이스 | 없음 | 해당 없음 |

## <a name="primary-user-and-azure-ad-device-owner"></a>기본 사용자 및 Azure AD 디바이스 소유자
경우에 따라 Intune 기본 사용자가 Azure AD 디바이스의 **소유자** 속성(**디바이스** > **Azure AD 디바이스**에서 확인 가능)과 다를 수 있습니다. Azure AD 디바이스 소유자는 Azure Active Directory에 디바이스를 등록할 때 추가됩니다.

## <a name="next-steps"></a>다음 단계
[Intune 디바이스를 관리합니다.](device-management.md)
