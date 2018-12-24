---
title: 디바이스 등록 관리자 계정을 사용하여 디바이스 등록
titlesuffix: Microsoft Intune
description: 디바이스 등록 관리자 계정을 사용하여 Intune에 디바이스를 등록합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: eb369d8e89ff41e75d5bd669819afbe98b6d1ba7
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53031843"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>디바이스 등록 관리자 계정을 사용하여 Intune에서 디바이스 등록

DEM(디바이스 등록 관리자) 계정을 사용하여 단일 Azure Active Directory 계정에서 최대 1,000개의 모바일 디바이스를 등록할 수 있습니다. DEM은 AAD 사용자 계정에 적용될 수 있는 Intune 사용 권한이며 이를 통해 사용자가 최대 1,000개의 디바이스를 등록할 수 있습니다. DEM 계정은 디바이스를 등록하고 디바이스의 사용자에게 전달하기 전에 준비하는 시나리오에 유용합니다.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>DEM 계정을 사용하여 등록된 디바이스의 제한 사항

DEM 사용자 계정 및 DEM 사용자 계정을 사용하여 등록된 디바이스에는 다음과 같은 제한 사항이 있습니다.

  - 회사 포털에서 초기화를 수행할 수 없습니다. Azure Portal의 Intune에서 DEM 사용자 계정으로 등록된 디바이스를 초기화할 수 있습니다.
  - 회사 포털 앱 또는 웹 사이트에 로컬 디바이스만 표시됩니다.
  - DEM 사용자 계정은 앱 관리에 대한 사용자별 Apple ID 요구 사항으로 인해 Apple VPP 사용자 라이선스를 사용하여 Apple VPP(Volume Purchase Program) 앱을 사용할 수 없습니다.
  - Apple VPP 디바이스 라이선스가 있는 경우 디바이스는 VPP 앱을 설치할 수 있습니다.
  - Windows 10 1803+를 제외하고 디바이스에 대한 조건부 액세스가 차단됨


## <a name="add-a-device-enrollment-manager"></a>디바이스 등록 관리자 추가

1.  [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **장치 등록 관리자**를 선택합니다.

2.  **추가**를 선택합니다.

3.  **사용자 추가** 블레이드에서 DEM 사용자의 사용자 계정 이름을 입력하고 **추가**를 선택합니다. DEM 사용자가 DEM 사용자 목록에 추가됩니다.

## <a name="permissions-for-dem"></a>DEM에 대한 권한

다음 작업에는 글로벌 관리자 또는 Intune 서비스 관리자 Azure AD 역할이 필요합니다.
- Azure AD 사용자 계정에 DEM 권한 할당
- 모든 DEM 사용자 참조

글로벌 관리자 또는 Intune 서비스 관리자 역할은 할당되지 않고 디바이스 등록 관리자 역할용으로 사용하도록 설정된 읽기 권한은 할당된 사용자의 경우 자신이 만든 DEM 사용자만 볼 수 있습니다.


## <a name="remove-device-enrollment-manager-permissions"></a>디바이스 등록 관리자 제거 권한

디바이스 등록 관리자를 제거해도 등록된 디바이스에는 영향을 주지 않습니다.

**장치 등록 관리자를 제거하려면**

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록**을 선택한 다음, **장치 등록 관리자**를 선택합니다.
2. **장치 등록 관리자** 블레이드에서 DEM 사용자를 선택하고 **삭제**를 선택합니다.

