---
title: Intune에서 Android 디바이스를 제거하는 방법 | Microsoft Docs
description: Intune 회사 포털에서 Android 디바이스 제거
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2019
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
ms.openlocfilehash: 75b26e178badbaa7905199eb91490134d2b72ba9
ms.sourcegitcommit: 61ed365f7f8826451c41bcab5e19bef97b5a3c72
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2019
ms.locfileid: "54057341"
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

-   애플리케이션에서 앱 데이터 지우기 -&gt; 앱 클릭 -&gt; "데이터 지우기" 단추 클릭
-   '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' 폴더 삭제

## <a name="uninstall-the-company-portal-app"></a>회사 포털 앱 제거  
회사 포털은 디바이스 관리 앱입니다. [관리에서 디바이스 등록을 취소](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management)해야만 제거할 수 있습니다. 완료되면 **제거**가 표시될 때까지 회사 포털 앱 아이콘을 탭하고 있습니다. **제거**를 탭하여 디바이스에서 앱을 제거합니다.  

또는 **설정** > **앱** > **회사 포털** > **제거**를 탭합니다.  

### <a name="remove-company-portal-app-as-device-administrator"></a>회사 포털 앱을 디바이스 관리자로 제거  
마지막 수단으로 디바이스 관리자로 삭제하여 디바이스에서 앱을 제거할 수 있습니다.  

회사 소유 디바이스가 있는 경우 조직에서는 회사 포털을 항상 디바이스에 설치해야 할 수 있습니다. 제거하는 경우 앱을 다시 설치할 때까지 이메일, 앱, WiFi 또는 VPN과 같은 보호된 회사 리소스에 대한 액세스 권한이 손실될 수 있습니다. 필수 앱을 설치, 업데이트 또는 제거하는 방법에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune)를 참조하세요.  

회사 포털을 디바이스 관리자로 사용하지 않으려면 아래 단계를 완료합니다. 각 설정의 실제 이름은 Android 디바이스에 따라 다를 수 있습니다.  

**Android 단계, 옵션 1**:  
1. **설정** > **보안** > **추가 보안 설정** > **디바이스 관리자**를 선택합니다.  
2. **회사 포털** 선택을 취소합니다.  

**Android 단계, 옵션 2**:  
1. **설정** > **잠금 화면 및 보안** > **기타 보안 설정** > **디바이스 관리 앱**을 선택합니다.  
2. **회사 포털** 선택을 취소합니다.    

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
