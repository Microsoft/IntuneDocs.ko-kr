---
title: 장치 로그 수집
description: 관리되는 장치에서 로그를 수집하는 방법을 알아봅니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f07947a4064cbd6852edb93ea8d6d17e2c6d9101
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025572"
---
# <a name="device-logs"></a>장치 로그

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

문제 해결 과정의 일환으로 사용자 장치에서 로그를 수집할 수 있습니다. 이러한 로그를 수집하기 위한 지침은 여기에 설명되어 있습니다. 일반적으로 장치에 액세스하여 이러한 로그를 가져오거나, 사용자에게 로그를 수집하여 보내달라고 요청할 수 있습니다.

### <a name="android-logs"></a>Android 로그
Android 로그는 *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*에 있습니다.

경우에 따라 특히, 최신 Android 장치에서는 파일이 표시되지 않습니다. 이 경우 사용자는 Android용 회사 포털 앱을 열어야 합니다. 그런 다음 **설정**>**로그 복사**를 선택하고 장치를 다시 부팅해야 합니다.

사용자가 데이터 로그를 보내는 방법에 대한 자세한 내용은 다음 문서를 참조하세요.

- [자세한 정보 로깅을 사용하여 IT 관리자가 장치 문제를 해결하도록 돕기](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android): 사용자가 자세한 정보 로깅을 켜고 모든 데이터 로그를 자동으로 보내는 방법을 설명합니다. 기본적으로 자세한 정보 로깅은 켜져 있습니다.

- [메일을 사용하여 IT 관리자에게 Android 진단 데이터 로그 보내기](/intune-user-help/send-logs-to-your-it-admin-by-email-android)

- [USB 케이블을 사용하여 IT 관리자에게 진단 데이터 로그 보내기](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS 로그

[IT 관리자에게 iOS 등록 오류 보내기](/intune-user-help/send-errors-to-your-it-admin-ios)에 설명된 대로 사용자가 등록 오류를 보낼 수 있습니다.

[iOS 장치 로그 보내기](/intune-user-help/send-logs-to-microsoft-ios)에 설명된 대로 사용자가 장치 로그를 보낼 수 있습니다.

### <a name="mac-os-x-logs"></a>Mac OS X 로그

1. **Console(콘솔)** 앱을 엽니다.
2. **FILES(파일)** 에서 **system.log**를 선택합니다.
3. 맨 위의 메뉴 모음에서 **File(파일)** > **Save a Copy As…(다른 이름으로 복사본 저장…)** 를 선택하고 파일을 저장합니다.

### <a name="windows-phone"></a>Windows Phone

Windows Phone 회사 포털 앱에서는 사용자는 줄임표(**...**)를 선택하여 메뉴에 액세스한 다음 **로그 보내기**를 선택합니다. 이 옵션은 회사 포털 앱에 로그인하기 전과 후에 모두 사용할 수 있습니다.

### <a name="windows"></a>Windows

Windows 회사 포털의 경우 로그는 *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*에 있습니다.
