---
title: 사용 약관을 거부한 경우 관리에서 디바이스 제거 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 12e3b111572758ca8d77406287134df8cdf7e027
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883958"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>“사용 약관”을 거부한 경우 관리에서 디바이스 제거

회사 포털 앱에 로그인을 시도하는 동안 사용 약관을 거부하면, 다음 시도 시 회사 포털 앱에 로그인이 금지되므로, 이 "해결 방법" 지침을 사용하여 Intune에서 디바이스를 제거합니다.

회사 포털 앱을 제거하면 Intune에서도 디바이스가 제거됩니다. 디바이스는 더 이상 회사 리소스에 액세스할 수 없습니다. 관리에서 디바이스를 제거할 때 발생하는 상황에 대한 자세한 내용은 [Intune에서 디바이스 등록을 취소하면 어떻게 되나요?](what-happens-if-you-unenroll-your-device-from-intune-android.md)를 참조하세요.

회사 포털 앱을 제거하려면 먼저 **디바이스 관리자** 설정으로 이동한 다음 **회사 포털**을 해제해야 합니다. 보유한 Android 디바이스에 따라 단계는 약간 다를 수도 있습니다.

## <a name="removing-the-device-from-the-company-portal-app"></a>회사 포털 앱에서 디바이스 제거하기

Intune에서 디바이스를 제거하고 회사 포털 앱을 제거하려면:

1. **설정**&gt;**보안 및 화면 잠금**&gt;**디바이스 관리자**로 이동합니다.

    이 단계를 완료하면 디바이스 등록이 즉시 취소됩니다.

2. 옆에 있는 상자를 선택 취소하거나 **회사 포털**을 해제합니다.

    이제 회사 포털 앱을 제거할 수 있습니다.

## <a name="removing-data-collected-by-the-company-portal-app"></a>회사 포털 앱에서 수집한 데이터 제거하기

Android용 회사 포털 앱이 디바이스에 저장하는 모든 데이터를 제거하려면:

- 애플리케이션에서 앱 데이터 지우기 -&gt; 앱 클릭 -&gt; "데이터 지우기" 단추 클릭
- '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' 폴더 삭제


여전히 도움이 필요하세요? 회사 지원팀에 문의하거나(연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 확인) <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 팀</a>으로 메일을 보내세요.
