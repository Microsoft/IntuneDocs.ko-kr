---
title: Intune에서 Android 장치를 제거하는 방법 | Microsoft Docs
description: Intune에서 Android 장치 등록을 취소하는 방법을 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
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
ms.openlocfilehash: ec3c0a1c8ce4e04f4d23fb01e7c2525d8f2eed5b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018365"
---
# <a name="how-to-remove-your-android-device-from-intune"></a>Intune에서 Android 장치를 제거하는 방법

Intune에서 Android 장치를 제거하면 장치에서 회사 리소스에 더 이상 액세스할 수 없습니다.  관리에서 장치를 제거할 때 발생하는 상황에 대한 자세한 내용은 [Intune에서 장치 등록을 취소하면 어떻게 되나요?](what-happens-if-you-unenroll-your-device-from-intune-android.md)를 참조하세요.

## <a name="removing-the-device-from-the-company-portal-app"></a>회사 포털 앱에서 장치 제거하기

Intune에서 장치 및 회사 포털 앱을 제거하려면 다음 단계를 따르세요.

1. 회사 포털 앱 오른쪽 위의 세로 점 세 개를 탭하여 **작업 메뉴**를 엽니다.

   ![오른쪽 위에 작업 메뉴가 열려 있는 Android 회사 포털 앱의 이미지 새로운 "회사 포털 제거" 옵션은 "내 프로필"과 "설정" 아래, 그리고 "사용 약관", "도움말 및 의견", "정보" 위에 있는 세 번째 옵션으로 제공됩니다.](./media/android_remove_cp_menu_action_after_1705.png)

2. **회사 포털 제거**를 탭합니다.

3. 회사 포털을 제거할지를 묻는 확인 팝업 메시지가 표시됩니다. 이 메시지는 장치를 등록 취소하는 경우의 결과에 대한 일부 정보를 제공합니다. 이 메시지를 읽은 후 **확인**을 탭하여 앱을 제거합니다.

   ![작업 메뉴에서 새로운 "회사 포털 제거" 옵션을 선택하면 제공되는 확인 대화 상자 이미지 이 대화 상자는 "회사 포털을 제거하면 회사 지원팀이 장치를 더 이상 관리하지 않게 되며 회사 데이터, 회사 앱 및 회사 메일에 대한 액세스 권한이 제거될 수 있습니다."라는 알림을 사용자에게 표시합니다. 그런 다음 "예"를 선택하여 회사 포털 앱을 제거할 것인지를 확인하라는 메시지가 표시됩니다.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>회사 포털 앱에서 수집한 데이터 제거하기

Android용 회사 포털 앱이 장치에 저장하는 모든 데이터를 제거하려면:

-   응용 프로그램에서 앱 데이터 지우기 -> 앱 클릭 -> "데이터 지우기" 단추 클릭
-   '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' 폴더 삭제

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com#HelpDeskDialog)를 참조하세요.
