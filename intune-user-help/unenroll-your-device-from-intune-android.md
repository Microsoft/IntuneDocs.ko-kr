---
title: Intune에서 Android 디바이스를 제거하는 방법 | Microsoft Docs
description: Intune 회사 포털에서 Android 디바이스 제거
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91aefbc8c3960100ce5e9164ce48a2b9d33c3f3e
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238956"
---
# <a name="unenroll-your-android-device-from-management"></a>관리에서 Android 디바이스 등록 취소  

더 이상 조직에서 관리하지 않도록 등록된 Android 디바이스를 제거합니다. 이 문서에서는 회사 포털 앱에서 디바이스를 제거하는 방법을 설명합니다. 디바이스를 제거하면 다음과 같이 됩니다.  

* 디바이스가 조직이 보호하는 데이터 및 리소스에 액세스하지 못합니다.
* 디바이스는 더 이상 회사 포털에 나타나지 않습니다.
* 회사 포털에서 앱을 설치할 수 없습니다.
* 디바이스를 추가할 때 디바이스에서 변경된 모든 설정(예: 카메라 사용 안 함 또는 특정 암호 길이 요구)이 더 이상 적용되지 않습니다.  

> [!NOTE]
> Microsoft Intune 앱에서 회사 소유의 장치를 등록 취소 하거나 제거할 수 없습니다. 장치는 초기 장치를 설치 하는 동안 등록 되었으며 조직의 리소스에 액세스 하려면 등록 해야 합니다.  

1. 회사 포털에서 오른쪽 위 모서리로 이동하여 세 개의 수직 점을 탭합니다. 작업 메뉴가 열립니다.

   ![오른쪽 위에 작업 메뉴가 열려 있는 Android 회사 포털 앱의 스크린샷입니다. 새로운 "회사 포털 제거" 옵션은 "내 프로필"과 "설정" 아래, 그리고 "사용 약관", "도움말 및 의견", "정보" 위에 있는 세 번째 옵션으로 제공됩니다.](./media/android_remove_cp_menu_action_after_1705.png)

2. **회사 포털 제거**를 탭합니다.  

3. 디바이스를 등록 취소한 후 발생하는 상황에 대한 정보가 포함된 메시지가 표시됩니다. **확인**을 탭하여 회사 포털에서 디바이스를 제거할 것임을 확인합니다.

   ![작업 메뉴에서 새로운 "회사 포털 제거" 옵션을 선택하면 표시되는 확인의 스크린샷입니다.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>회사 포털 앱에서 수집한 데이터 제거  

Android용 회사 포털 앱이 디바이스에 저장하는 모든 데이터를 제거하려면:

- **애플리케이션** > **[*name of app*]**  > **데이터 지우기**를 눌러서 앱 데이터를 지웁니다.
- 다음 폴더 삭제: \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal.

## <a name="uninstall-the-company-portal-app"></a>회사 포털 앱 제거

회사 포털은 디바이스 관리 앱입니다. 관리에서 디바이스 등록을 취소해야만 제거가 가능합니다. 완료되면 **제거**가 표시될 때까지 회사 포털 앱 아이콘을 탭하고 있습니다. **제거**를 탭하여 디바이스에서 앱을 제거합니다.  

또는 **설정** > **앱** > **회사 포털** > **제거**를 탭합니다.  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>디바이스 관리자로 회사 포털 앱 제거

마지막 수단으로 디바이스 관리자로 앱을 디바이스에서 제거할 수 있습니다.  

회사 소유 디바이스가 있는 경우 조직에서는 회사 포털을 항상 디바이스에 설치해야 할 수 있습니다. 제거하는 경우 앱을 다시 설치할 때까지 이메일, 앱, WiFi 또는 VPN과 같은 보호된 회사 리소스에 액세스하지 못할 수 있습니다. 필수 앱을 설치, 업데이트 또는 제거하는 방법에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune)를 참조하세요.  

디바이스 관리자로 회사 포털을 비활성화하는 방법은 다음과 같습니다. 각 설정의 실제 이름은 Android 디바이스에 따라 다를 수 있습니다.  

**옵션 1**:  

1. **설정** > **보안** > **추가 보안 설정** > **디바이스 관리자**를 선택합니다.  
2. **회사 포털** 선택을 취소합니다.  

**옵션 2**:

1. **설정** > **잠금 화면 및 보안** > **기타 보안 설정** > **디바이스 관리 앱**을 선택합니다.
2. **회사 포털** 선택을 취소합니다.

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
