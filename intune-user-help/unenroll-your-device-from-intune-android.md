---
title: Intune에서 Android 디바이스를 제거하는 방법 | Microsoft Docs
description: Intune에서 Android 디바이스 등록을 취소하는 방법을 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/23/2018
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
ms.openlocfilehash: d932005c955afed7f16e9766b559b77b2cd43182
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959488"
---
# <a name="unenroll-your-android-device-from-management"></a>관리에서 Android 디바이스 등록 취소  

더 이상 조직에서 관리하지 않도록 등록된 Android 디바이스를 제거합니다. 이 문서에서는 회사 포털 앱에서 디바이스를 제거하는 방법을 설명합니다. 디바이스를 제거하면 다음과 같이 됩니다.  

* 디바이스가 조직이 보호하는 데이터 및 리소스에 액세스하지 못합니다.
* 디바이스는 더 이상 회사 포털에 나타나지 않습니다.
* 회사 포털에서 앱을 설치할 수 없습니다.
* 디바이스를 추가할 때 디바이스에서 변경된 모든 설정(예: 카메라 사용 안 함 또는 특정 암호 길이 요구)이 더 이상 적용되지 않습니다.  

1. 회사 포털에서 오른쪽 위 모서리로 이동하여 세 개의 수직 점을 탭합니다. 작업 메뉴가 열립니다.

   ![오른쪽 위에 작업 메뉴가 열려 있는 Android 회사 포털 앱의 이미지 새로운 "회사 포털 제거" 옵션은 "내 프로필"과 "설정" 아래, 그리고 "사용 약관", "도움말 및 의견", "정보" 위에 있는 세 번째 옵션으로 제공됩니다.](./media/android_remove_cp_menu_action_after_1705.png)

2. **회사 포털 제거**를 탭합니다.  

3. 디바이스를 등록 취소한 후 발생하는 상황에 대한 정보가 포함된 메시지가 표시됩니다. **확인**을 탭하여 회사 포털에서 장치를 제거할 것임을 확인합니다.

   ![작업 메뉴에서 새로운 "회사 포털 제거" 옵션을 선택하면 제공되는 확인 대화 상자 이미지 이 대화 상자는 "회사 포털을 제거하면 회사 지원팀이 디바이스를 더 이상 관리하지 않게 되며 회사 데이터, 회사 앱 및 회사 메일에 대한 액세스 권한이 제거될 수 있습니다."라는 알림을 사용자에게 표시합니다. 그런 다음 "예"를 선택하여 회사 포털 앱을 제거할 것인지를 확인하라는 메시지가 표시됩니다.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>회사 포털 앱에서 수집한 데이터 제거하기  

Android용 회사 포털 앱이 디바이스에 저장하는 모든 데이터를 제거하려면:

-   응용 프로그램에서 앱 데이터 지우기 -> 앱 클릭 -> "데이터 지우기" 단추 클릭
-   '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' 폴더 삭제

## <a name="uninstall-the-company-portal-app"></a>회사 포털 앱 제거  
회사 포털은 디바이스 관리 앱이므로 [관리에서 디바이스 등록 취소](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management)할 때까지 이를 제거할 수 있습니다. 완료되면 **제거**가 표시될 때까지 회사 포털 앱 아이콘을 탭하고 있습니다. **제거**를 탭하여 장치에서 앱을 제거합니다.  

또는 **설정** > **앱** > **회사 포털** > **제거**를 탭합니다.  

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
