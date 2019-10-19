---
title: Windows Defender 켜기 | Microsoft Docs
description: Windows Defender를 켜서 회사 리소스에 액세스하는 방법을 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/08/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e8fd6941a94a24dd3b6bf98daf6adc9a47f9fa7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72501947"
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>Windows Defender를 켜서 회사 리소스에 액세스

직장이나 학교에서는 자체 리소스에 액세스하는 디바이스가 안전한지 확인해야 합니다. 악성 소프트웨어에 대한 Windows의 기본 보호 기능인 [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx)를 사용하는 방법은 여러 가지가 있습니다.

액세스 문제가 있는 경우 해결하기 위해 Windows Defender에서 변경할 필요가 있는 설정이 몇 가지 있습니다. 이 단계를 수행하려면 컴퓨터의 여러 위치로 이동이 필요할 수 있습니다.

## <a name="turn-on-windows-defender"></a>Windows Defender 켜기

1. **시작**에서 **제어판**을 엽니다.
2. **관리 도구** > **그룹 정책 편집**을 엽니다. 새 창에 **로컬 그룹 정책 편집기**가 열립니다.
3. **컴퓨터 구성** > **관리 템플릿** > **Windows 구성 요소** > **Windows Defender 바이러스 백신**을 엽니다. **Windows Defender 바이러스 백신 사용 안 함** 설정은 다른 설정의 폴더 아래 있습니다. 
4. **Windows Defender 바이러스 백신 사용 안 함**을 열고 **사용 안 함** 또는 **구성되지 않음**으로 설정되어 있는지 확인합니다.

## <a name="turn-on-real-time-protection"></a>실시간 보호 켜기

**시작**으로 이동하고 **Windows Defender 보안 센터**를 검색하여 실시간 보호가 켜져 있는지 확인합니다. **바이러스 및 위협 방지 설정**을 선택하고 **실시간 보호**와 **클라우드 제공 보호**가 모두 **사용**으로 설정되어 있는지 확인합니다. 이 옵션이 표시지 않으면 다음을 수행하여 옵션을 활성화합니다.

1. **시작**에서 **제어판**을 엽니다.
2. **관리 도구** > **그룹 정책 편집**을 엽니다. 새 창에 **로컬 그룹 정책 편집기**가 열립니다.
3. **컴퓨터 구성** > **관리 템플릿** > **Windows 구성 요소** > **Windows Defender 바이러스 백신** > **바이러스 및 위협 방지**를 엽니다.
4. **Virus and threat protection area**(바이러스 및 위협 방지 영역) 설정을 열고 **사용 안 함**으로 설정합니다.

## <a name="update-your-antivirus-definitions"></a>바이러스 백신 정의 업데이트

**시작**으로 이동하고 **Windows Defender 보안 센터**를 검색하여 바이러스 백신 정의가 최신인지 확인합니다. **보호 업데이트**와 **업데이트 확인**을 선택하여 디바이스가 최신 바이러스로부터 보호되도록 하십시오. 이 옵션이 표시되지 않으면 [실시간 보호 켜기](turn-on-defender-windows.md#turn-on-real-time-protection)의 단계를 수행하십시오.

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. IT 관리자의 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
