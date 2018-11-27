---
title: Intune 최종 사용자 앱 UI 업데이트
titlesuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 최종 사용자 장치에서 작동하는 앱의 UI가 어떻게 변경되었는지 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0d6a798f9f16f4eaa0e882fb7d90203be912051f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190033"
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune 최종 사용자 앱 UI 업데이트
최종 사용자가 이번 Microsoft Intune 릴리스에서 보게 될 앱의 UI가 어떻게 업데이트되었는지 알아봅니다. 이러한 업데이트를 이해하면 사용자 커뮤니케이션 및 배포를 지원하기 위해 만든 사용자 지정 설명서 업데이트에 도움이 될 것입니다. 사용자가 회사 포털을 사용하여 지원 센터에 전화해 지원을 요청하는 경우 사용자에게 발생하는 문제를 더 잘 해결하는 방법을 이해하는 데에도 도움이 될 수 있습니다.

<!---End-user messaging for accounts 1573558, 1712; changes to be made for other platforms for 1801 Users of the Company Portal website, will be blocked from taking actions that require write access to your tenant. They will see appropriate error messaging explaining that their account is under maintenance. Similar changes are coming to the Company Portal apps for Android, iOS, macOS, and Windows soon. ![Error message that occurs during account move](./media/account-move-rom-iwp-user-1712.png)--->

## <a name="week-of-november-12-2018"></a>2018년 11월 12일 주

### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows 회사 포털 바로 가기 키 <!-- 2771518 -->
최종 사용자는 바로 가기 키(액셀러레이터 키)를 사용하여 Windows 회사 포털에서 앱 및 장치 작업을 트리거할 수 있습니다.

## <a name="week-of-october-22-2018"></a>2018년 10월 22일이 있는 주

### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>회사 포털 앱에 대한 사용자 지정 브랜드 이미지 추가 <!-- 1916266 -->
Microsoft Intune 관리자는 iOS 회사 포털 앱의 사용자 프로필 페이지에 배경 이미지로 표시될 사용자 지정 브랜드 이미지를 업로드할 수 있습니다. 회사 포털 앱 구성에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요.



## <a name="week-of-august-27-2018"></a>2018년 8월 27일 주  

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>회사 포털 웹 사이트의 새로운 사용자 환경 업데이트<!--2000968 -->  
고객으로부터의 피드백에 기반한 새 기능을 회사 포털 웹 사이트에 추가했습니다. 장치의 기존 기능과 유용성이 크게 향상됩니다. 사이트 영역&ndash;예: 장치 세부 정보, 피드백, 지원 및 장치 개요&ndash;은 응답성이 높은 최신의 새로운 디자인을 제공합니다. [Intune 회사 포털 웹 사이트 설명서](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website)는 이러한 변경 내용을 반영하도록 업데이트되었습니다.   

표시되는 업데이트는 다음을 포함합니다.  

- 모든 장치 플랫폼에서 간소화된 워크플로
- 향상된 장치 식별 및 등록 흐름
- 더 유용한 오류 메시지
- 전문 기술 용어는 줄이고 친근한 언어 사용
- 앱에 대한 직접 링크를 공유하는 기능
- 대규모 앱 카탈로그의 성능 개선
- 향상된 모든 사용자에 대한 접근성  

|업데이트됨|이전|
|---|---|
|![업데이트된 장치 페이지는 더 이상 전체 목록 위에 팝업으로 표시하지 않고 장치 정보 위에 바르게 정렬된 장치를 표시합니다.](./media/iwp-device-after-1803.png)|![이전 버전의 장치 페이지입니다.](./media/iwp-device-before-1803.png)|
|![업데이트된 앱 설치 페이지는 게시 날짜, 버전 및 앱 형식 등 설명 및 다양한 설치 정보 위에 앱을 바르게 보여줍니다.](./media/iwp-app-install-after-1803.png)|![이전 버전의 앱 설치 페이지입니다.](./media/iwp-app-install-before-1803.png)|  

## <a name="week-of-july-16-2018"></a>2018년 7월 16일 주  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱에서 동기화할 수 있는 더 많은 기회   
이제 Windows용 회사 포털 앱을 사용하여 Windows 작업 표시줄 및 시작 메뉴에서 직접 동기화를 시작할 수 있습니다. 이 기능은 장치를 동기화하고 회사 리소스에 액세스하는 작업만 수행하는 경우에 특히 유용합니다. 새 기능에 액세스하려면 작업 표시줄 또는 시작 메뉴에 고정되어 있는 회사 포털 아이콘을 마우스 오른쪽 단추로 클릭합니다. 메뉴 옵션(점프 목록이라고도 함)에서 **이 장치 동기화**를 선택합니다. 회사 포털에 **설정** 페이지가 열리고 동기화가 시작됩니다.  

![장치의 바탕 화면에 있는 Windows 작업 표시줄의 스크린샷 회사 포털 앱 프로그램 아이콘을 클릭하여 "작업 표시줄에 고정", "창 닫기" 및 "이 장치 동기화" 작업 옵션이 있는 메뉴를 표시합니다.](./media/sync-device-from-start-menu-1807.png)  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱의 새 검색 환경  

이제 Windows용 회사 포털 앱에서 앱을 탐색하거나 검색하면 기존 **타일** 보기와 새로 추가된 **세부 정보** 보기 간에 전환할 수 있습니다. 새 보기에는 이름, 게시자, 게시 날짜 및 설치 상태와 같은 응용 프로그램 세부 정보가 나열됩니다.  

**앱** 페이지의 **설치됨** 보기를 통해 완료 및 진행 중인 앱 설치에 대한 세부 정보를 볼 수 있습니다.  

타일 보기를 보여 주는 예제 스크린샷:  
 
![설치된 앱을 타일 보기로 보여주는 Windows용 Intune 회사 포털 앱의 스크린샷](/intune/media/tiles-installed-view-cpapp-1807.png)  

세부 정보 보기를 보여 주는 예제 스크린샷:  

![설치된 앱을 세부 정보 보기에 보여주는 Windows용 Intune 회사 포털 앱의 스크린샷.](/intune/media/details-installed-view-cpapp-1807.png) 

## <a name="week-of-april-23-2018"></a>2018년 4월 23일 주간
### <a name="updated-navigation-view-in-the-company-portal-app-for-windows-10----1195010---"></a>Windows 10 <!-- 1195010 -->용 회사 포털 앱의 탐색 보기 업데이트됨
Windows 10용 Intune 회사 포털 앱이 [Fluent Design System의 탐색 보기](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics)로 업데이트되었습니다. 앱의 옆쪽에 모든 최상위 페이지의 정적 세로 목록이 표시됩니다. 링크를 클릭하여 빠르게 페이지를 보고 페이지 간에 전환할 수 있습니다. 이 업데이트는 Intune에서 더욱 공감할 수 있고 친숙한 적응형 환경을 만들려는 Microsoft의 지속적인 노력의 일부로 여러 업데이트 중 첫 번째로 선보이는 것입니다. 

![Fluent Design 탐색 보기를 보여주는 회사 포털 앱 대시보드의 스크린샷](./media/1804_WindowsCP_Fluent_01.png)


## <a name="week-of-april-2-2018"></a>2018년 4월 2일의 주간

### <a name="user-experience-update-for-the-company-portal-app-for-ios----1412866---"></a>iOS용 회사 포털 앱의 사용자 환경 업데이트 <!-- 1412866 -->
iOS용 회사 포털 앱에 대한 주요 사용자 환경 업데이트가 릴리스되었습니다. 이 업데이트는 현대적인 모양과 느낌을 포함하여 시각적으로 완전히 새롭게 설계했습니다. 앱의 기능은 유지하면서도 유용성과 접근성을 향상시켰습니다.  

또한 다음을 확인할 수 있습니다.
- iPhone X 지원
- 더 빨라진 앱 시작과 응답 로드로 사용자 시간 단축
- 사용자에게 최신 상태 정보를 제공하는 추가 진행률 표시줄
- 문제 발생 시 이를 보고하기 쉽도록 사용자가 로그를 업로드하는 방식 개선 사항  

|이전|이러한|
|---|---|
|![01](/intune/media/cp_iosRedesign_before_1803_01.png)|![01](/intune/media/cp_iosRedesign_after_1803_01.png)|
|*이전 단계와 결합*|![02](/intune/media/cp_iosRedesign_after_1803_02.png)|
|![03](/intune/media/cp_iosRedesign_before_1803_02.png)|![03](/intune/media/cp_iosRedesign_after_1803_03.png)|

### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Windows용 회사 포털 앱의 언어 개선 사항 <!-- 1683758 -->
귀사에 더욱 친숙하고 구체적이 되도록 Windows 10용 회사 포털에서 언어를 개선하였습니다.

|이전|이러한|
|---|---|
|![01](./media/windows_enroll_before_1803.png)|![01](./media/windows_enroll_after_1803.png)|
|![02](./media/windows_view_policy_issues_before_1803.png)|![02](./media/windows_view_policy_issues_after_1803.png)

## <a name="week-of-march-12-2018"></a>2018년 3월 12일 주

### <a name="company-portal-for-android-visual-updates----976944---"></a>Android용 회사 포털 시각적 업데이트 <!-- 976944 -->

Android의 [자료 디자인](https://material.io/) 지침에 따르도록 Android용 회사 포털 앱을 업데이트했습니다.

|이전|이러한|
|---|---|
|![01](./media/android_about_before_1803.png)|![01](./media/androidCP_about_after_1803.png)|
|![02](./media/android_contact_it_before_1803.png)|![02](./media/android_contact_it_after_1803.png)|
|![03](./media/android_devices_before_1803.png)|![03](./media/androidCP_devicelist_after_1803.png)|
|![04](./media/android_device_details_before_1803.png)|![05](./media/androidCP_devicedetails_1_after1803.png)|
|![05](./media/android_device_details_update_settings_before_1803.png)|![05](./media/androidCP_devicedetails_red_box_2_after1803.png)|
|![06](./media/android_profile_before_1803.png)|![06](./media/android_profile_after_1803.png)|
|![07](./media/androidCP_Setup01_before_1803.png)|![07](./media/androidCP_Setup01_after_1803.png)|


## <a name="week-of-november-27-2017"></a>2017년 11월 27일 주

### <a name="new-device-categories-step-in-guided-setup-for-the-company-portal-app-for-windows-10----1335292---"></a>Windows 10용 회사 포털 앱에 대한 설정 가이드의 새로운 "장치 범주" 단계 <!-- 1335292 -->

[장치 그룹 매핑](device-group-mapping.md)을 사용하도록 설정한 경우 이제 Windows 10용 회사 포털 앱에서 사용자가 장치를 등록한 후 장치 범주를 선택하는 과정을 안내합니다.

![장치 그룹 매핑 범주](./media/w10_cp_category_device_setup_after_1711.png)

## <a name="week-of-november-13-2017"></a>2017년 11월 13일 주

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>버전 2.9.0에 대한 iOS 회사 포털의 향상된 장치 설정 워크플로 기능<!-- 1417174 -->

iOS용 회사 포털 앱에서 장치 설정 워크플로를 개선했습니다. 언어는 더욱 친숙하게 변경되었으며, 최대한 화면을 결합했습니다. 또한 전체 설정 텍스트에서 회사 이름을 사용하여 언어가 회사에 더욱 구체적으로 변경되었습니다.

> [!NOTE]
> **Microsoft Intune** > **클라이언트 앱** > **회사 포털 브랜딩** > **회사 이름**에는 Azure Portal에서 설정한 회사 이름이 사용됩니다. 이 값을 설정하지 않으면 **Azure Active Directory** > **속성** > **이름**에 설정된 테넌트 이름이 사용됩니다. 회사 포털 브랜딩에서 회사 이름을 설정하지 않았고 테넌트 이름을 표시하지 않으려면 [회사 포털 브랜딩] 탭에서 회사 이름을 설정하는 것이 좋습니다. 이 문자열을 회사 포털의 헤더에 표시하지 않으려면 “로고 옆에 회사 이름 표시” 확인란을 선택 취소하면 됩니다.

|이전|이러한|
|---|---|
|![01](./media/ios_cp_enroll_01_before_1711.png)|![01](./media/ios_cp_enroll_01_after_1711.png)|
|![02](./media/ios_cp_enroll_02_before_1711.png)|*이전 단계와 결합*|
|![03](./media/ios_cp_enroll_03_before_1711.png)|![03](./media/ios_cp_enroll_03_after_1711.png)|
|![04](./media/ios_cp_enroll_04_before_1711.png)|![04](./media/ios_cp_enroll_04_after_1711.png)|
|![05](./media/ios_cp_enroll_05_before_1711.png)|![05](./media/ios_cp_enroll_05_after_1711.png)|
|![06](./media/ios_cp_enroll_06_before_1711.png)|![06](./media/ios_cp_enroll_06_after_1711.png)|
|![07](./media/ios_cp_enroll_07_before_1711.png)|![07](./media/ios_cp_enroll_07_after_1711.png)|


## <a name="week-of-november-6-2017"></a>2017년 11월 6일 주

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Windows 10용 회사 포털 앱에 대한 업데이트 <!--1299474-->
설정과 의도된 사용자 작업이 모든 설정에서 더욱 일관되도록 Windows 10용 회사 포털 앱의 설정 페이지가 업데이트되었습니다. 또한 다른 Windows 앱의 레이아웃과 일치하도록 업데이트되었습니다.

|이전|이러한|
|---|---|
|![01](./media/w10-share-logs.png)|![02](./media/w10-share-logs-after-1711.png)|


### <a name="search-improvements-to-the-company-portal-apps-and-website----1418189---"></a>회사 포털 앱 및 웹 사이트의 향상된 검색 기능<!-- 1418189 -->
이제 회사 포털 앱에서 앱 범주, 이름 및 설명 전체에 검색이 사용됩니다. 결과는 관련성이 낮은 순서로 정렬됩니다. 이 업데이트는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)에도 제공됩니다.

관련성을 추적하는 방법은 여전히 미세 조정 중이므로 회사 포털 웹 사이트의 맨 아래에서 "피드백" 링크를 사용하여 작동 방식에 대해 알려주세요.

## <a name="week-of-october-16-2017"></a>2017년 10월 16일의 주

### <a name="search-improvements-to-the-company-portal-website----1331697---"></a>회사 포털 웹 사이트의 향상된 검색 기능<!-- 1331697 -->
[회사 포털 웹 사이트](https://portal.manage.microsoft.com)부터는 앱 검색 기능을 개선했습니다. 이제 검색은 이름 및 설명 필드 외에도 앱 범주에서 수행됩니다. 결과는 기본적으로 정렬 관련도의 내림차순으로 정렬됩니다. 

회사 포털 웹 사이트가 iOS용 회사 포털 앱의 일부로 사용되므로 iOS 사용자는 이 변경 내용을 수용합니다. Android 및 Windows용 회사 포털 앱은 향후 몇 개월 내에 유사한 업데이트를 수용하게 됩니다.

관련성을 추적하는 방법은 여전히 미세 조정 중이므로 회사 포털 웹 사이트의 맨 아래에서 "피드백" 링크를 사용하여 작동 방식에 대해 알려주세요.


### <a name="ios-company-portal-displays-large-icons----1454593---"></a>iOS 회사 포털의 큰 아이콘 표시 <!-- 1454593 -->
이 릴리스에서는 iOS 회사 포털의 앱 타일에서 아이콘을 표시하는 방법과 관련된 알려진 문제를 해결했습니다. 120x120 픽셀 이상의 앱 아이콘을 업로드하면 이제 [회사 포털 웹 사이트](https://portal.manage.microsoft.com) 및 iOS 회사 포털의 앱 페이지가 앱 타일의 전체 크기로 표시됩니다.


## <a name="week-of-october-2-2017"></a>2017년 10월 2일이 있는 주

### <a name="improvements-to-device-setup-workflow-in-company-portal----1490692---"></a>회사 포털의 향상된 장치 설정 워크플로 기능<!-- 1490692 -->
Android용 회사 포털 앱에서 장치 설치 워크플로를 개선했습니다. 언어는 귀사를 위해 더욱 친숙하고 구체적으로 변경되었으며, 최대한 화면을 결합했습니다. 

|이전|이러한|
|---|---|
|![01](./media/android_cp_enroll_01_post_1709.png)|![01](./media/android_cp_enroll_01_1709_new.png)|
|![01a](./media/android_cp_enroll_01_before_1710.png)| *이전 단계와 결합* |
|![02](./media/android_cp_enroll_02_before_1710.png)|![02](./media/android_cp_enroll_02_after_1710.png)|
|![03](./media/android_cp_enroll_03_before_1710.png)|![03](./media/android_cp_enroll_03_after_1710.png)|

Android 회사 프로필 장치에서 추가 단계가 개선되었습니다.

|이전|이러한|
|---|---|
|![04](./media/android_work_cp_enroll_01_before_1710.png)|![04](./media/android_work_cp_enroll_01_after_1710.png)|
|![05](./media/android_work_cp_enroll_02_before_1710.png)| *이전 단계와 결합* |
|![06](./media/android_work_cp_enroll_03_before_1710.png)|![06](./media/android_work_cp_enroll_03_after_1710.png)|
|![07](./media/android_work_cp_enroll_04_before_1710.png)|![07](./media/android_work_cp_enroll_04_after_1710.png)|
|![08](./media/android_work_cp_enroll_05_before_1710.png)| *이전 단계와 결합* |


조건부 액세스 전자 메일 활성화 화면도 업데이트했습니다.

|이전|이러한|
|---|---|
|![06](./media/android_conditional_access_email_before_1710.png)|![06](./media/android_conditional_access_email_after_1710.png)

## <a name="week-of-september-11-2017"></a>2017년 9월 11일이 있는 주

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android용 회사 포털 앱의 구문을 쉽게 이해 <!-- 1396349 -->  

최종 사용자가 쉽게 등록할 수 있도록 새로운 텍스트가 포함되어 Android용 회사 포털 앱의 등록 프로세스가 간소화되었습니다. 사용자 지정 등록 설명서가 있는 경우 새 화면을 반영하도록 업데이트하려고 합니다. 아래에서 샘플 이미지를 찾을 수 있습니다.

|이전|이러한|
|---|---|
|![01](./media/android_cp_enroll_01_before_1709.png)|![01](./media/android_cp_enroll_01_post_1709.png)|
|![02](./media/android_cp_enroll_02_before_1709.png)|![02](./media/android_cp_enroll_02_post_1709.png)|
|![03](./media/android_cp_enroll_03_before_1709.png)|![03](./media/android_cp_enroll_03_post_1709.png)|
|![04](./media/android_cp_enroll_04_before_1709.png)|![04](./media/android_cp_enroll_04_post_1709.png)|
|![05](./media/android_cp_enroll_05_before_1709.png)|![05](./media/android_cp_enroll_05_post_1709.png)|


## <a name="august-2017"></a>2017년 8월

### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>iOS 11 메일 앱의 OAuth 지원 <!-- 1196951 -->

Intune을 사용하는 조건부 액세스는 OAuth를 통해 iOS 장치에서 더욱 안전한 인증을 지원합니다. 이를 지원하기 위해 iOS용 회사 포털 앱에 더욱 안전한 인증을 허용하는 다른 흐름이 생겼습니다. 최종 사용자가 메일 앱에서 새 Exchange 계정에 로그인하려고 할 때 웹 보기 메시지가 표시됩니다. Intune에 등록되면 기본 메일 앱이 인증서에 액세스하도록 허용할지를 묻는 메시지가 표시됩니다. 대부분의 최종 사용자에게 격리된 메일이 더 이상 표시되지 않습니다. 기존 메일 계정에서는 기본 인증 프로토콜을 계속 사용하므로 이러한 사용자에게는 격리 메일이 계속 배달됩니다. 최종 사용자에 대한 이 로그인 환경은 Office 모바일 앱의 로그인 환경과 비슷합니다.

![기본 메일 앱의 계정 유형을 선택합니다.](./media/ios-11-ca-email-after-1708-01.png)

![Exchange를 선택하면 iOS 장치에서 메일 주소 및 계정 이름을 묻습니다.](./media/ios-11-ca-email-after-1708-02.png)

![메일 주소 및 계정 이름을 제공합니다.](./media/ios-11-ca-email-after-1708-03.png)

![외부 Microsoft 로그인 페이지로 전송됩니다.](./media/ios-11-ca-email-after-1708-04.png)

![Microsoft 페이지에 암호를 제공합니다.](./media/ios-11-ca-email-after-1708-05.png)

![Microsoft에서 장치를 관리에 등록할지 묻습니다.](./media/ios-11-ca-email-after-1708-06.png)

![회사 포털 웹 사이트에서 등록하라는 메시지가 사용자에게 표시됩니다.](./media/ios-11-ca-email-after-1708-07.png)



### <a name="intune-mobile-application-management-mam-dialog-boxes-will-have-a-modern-interface----1199015---"></a>Intune MAM(모바일 응용 프로그램 관리) 대화 상자에는 최신 인터페이스가 포함됨 <!-- 1199015 -->

Intune MAM(모바일 응용 프로그램 관리) 대화 상자가 최신 모양과 느낌으로 업데이트됩니다. 대화 상자는 이전 스타일과 동일한 방식으로 작동합니다.

**이전 환경**

![이전 인터페이스](./media/NewUI_Old_AttachFileHandler.jpg)

**최신 환경**

![최신 인터페이스](./media/NewUI_Modern_AttachFileHandler.jpg)


### <a name="updates-to-the-device-details-page-on-the-company-portal-app-for-windows-10----1287448---"></a>Windows 10용 회사 포털 앱의 “장치 세부 정보” 페이지에 대한 업데이트 <!-- 1287448 -->

Windows 10용 회사 포털 앱이 __장치 세부 정보__ 페이지의 제목 아래에서 속성으로 __범주__ 태그가 이동됩니다.

![Windows용 회사 포털 앱의 “장치 세부 정보” 화면으로, 이제 해당 화면의 제목 바로 아래가 아니라 속성으로 “범주” 필드가 표시됩니다.](./media/cp_win10_category_tag_move_after_1708.png)

## <a name="july-2017"></a>2017년 7월

### <a name="apps-details-pages-will-display-new-information-for-android-devices---1287476--"></a>앱 세부 정보 페이지에 Android 장치의 새 정보가 표시됨 <!--1287476-->

Android용 회사 포털 앱의 앱 세부 정보 페이지에는 이제 IT 관리자가 해당 앱에 대해 정의한 앱 범주가 표시됩니다.

![새 앱 세부 정보 페이지](./media/cp_android_appdetails_after_1708.png)

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>모든 플랫폼에 대해 회사 포털 앱 전체에서 로그인 환경 개선됨 <!--User Story 1132123-->

Android, iOS 및 Windows용 Intune 회사 포털 앱에 대한 로그인 환경을 개선하게 될 향후 몇 개월 내에 제공될 변경이 있음을 알려드립니다. Azure AD에서 이 변경 내용을 적용할 경우 회사 포털 앱에 대한 모든 플랫폼에서 새로운 사용자 환경이 자동으로 나타나게 됩니다. 또한 사용자가 이제 생성된 일회용 코드를 사용하여 다른 장치에서 회사 포털에 로그인할 수도 있습니다. 이 기능은 사용자가 자격 증명 없이 로그인해야 할 경우에 특히 유용합니다.  

아래에서 이전 로그인 환경, 자격 증명을 사용하는 새 로그인 환경, 그리고 다른 장치로부터의 새 로그인 환경을 볼 수 있습니다.

__이전 로그인 환경__

![웹 사이트가 그림으로 표시되면서 그 앞에 사람 아이콘이 포함된 회사 포털 로그인 페이지 아래에 "로그인" 단추가 있습니다. Microsoft 개인 정보 및 쿠키 정보로 이동하게 하는 하단의 링크](./media/cp_ios_aad_signin_before_1704_001.png)

![사용자는 로그인을 탭한 후 전자 메일 및 암호를 요구하는 이 페이지에서 암호 오류를 해결하는 방법을 제공하고 자격 증명을 입력합니다.](./media/cp_ios_aad_signin_before_1704_002.png)

![암호를 입력한 후 회사 포털 앱에 로그인되며 이 상태는 로드 중 막대로 표현됩니다.](./media/cp_ios_aad_signin_before_1704_003.png)

__새 로그인 환경__

![웹 사이트가 그림으로 표시되면서 그 앞에 사람 아이콘이 포함된 회사 포털 로그인 페이지 그 아래 “로그인” 단추가 있습니다. Microsoft 개인 정보 및 쿠키 정보로 이동하게 하는 하단의 링크](./media/cp_ios_aad_signin_after_1704_001.png)

![사용자는 같은 화면에서 전자 메일 및 암호 대신 전자 메일 주소만 입력하라는 메시지를 받습니다.](./media/cp_ios_aad_signin_after_1704_002.png)

![전자 메일 주소가 승인된 후에 암호를 입력하라는 메시지가 표시됩니다.](./media/cp_ios_aad_signin_after_1704_003.png)

![인증 프로세스를 진행하고 나면 회사 포털 앱에 로그인되며 이 상태는 로드 중 막대로 표현됩니다.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__다른 장치에서 로그인 시 새 로그인 환경__

![웹 사이트가 그림으로 표시되면서 그 앞에 사람 아이콘이 포함된 회사 포털 로그인 페이지 그 아래 “로그인” 단추가 있습니다. Microsoft 개인 정보 및 쿠키 정보로 이동하게 하는 하단의 링크](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

__다른 장치에서 로그인__ 링크를 누릅니다.

![회사 컴퓨터의 고유 암호를 사용하여 aka.ms/devicelogin 페이지로 이동하여 로그인 시 해당 코드를 사용하라는 지침이 제공됩니다.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

브라우저를 시작하고 [https://aka.ms/devicelogin](https://aka.ms/devicelogin)으로 이동합니다.

![회사 포털 앱이 아닌 작업 컴퓨터에서 사용자 브라우저 이미지 표시되는 "장치 로그인" 페이지에서 사용자에게 회사 포털 앱에서 받은 코드를 입력하라는 메시지가 나타납니다.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

회사 포털 앱에서 확인한 코드를 입력합니다. __계속__을 선택하면 스마트 카드와 같이 회사에서 지원되는 방법을 사용하여 인증할 수 있습니다.

![사용자는 필드에 고유한 코드를 입력하고 "장치 로그인" 사이트에서 Intune 회사 포털이 로그인에 필요한 인증을 수신하는 올바른 앱인지 확인을 요구합니다.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![사용자가 장치에서 회사 포털 앱에 로그인했으며 이 페이지를 닫을 수 있음을 언급하는 확인 페이지](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

회사 포털 앱에서 로그인이 시작됩니다.

![인증 프로세스를 진행하고 나면 회사 포털 앱에 로그인되며 이 상태는 로드 중 막대로 표현됩니다.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="june-2017"></a>2017년 6월

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies"></a>이제 Android용 회사 포털 앱에는 앱 보호 정책에 대한 새로운 최종 사용자 환경이 있습니다.
고객 의견에 따라 Android용 회사 포털 앱에 **회사 콘텐츠 액세스** 단추가 표시됩니다. 이는 Intune 모바일 응용 프로그램 관리의 기능인 앱 보호 정책을 지원하는 앱만 액세스하면 되는 경우 최종 사용자가 불필요하게 등록 프로세스를 수행하지 않도록 하기 위한 것입니다.

사용자는 장치 등록을 시작하는 대신 **회사 콘텐츠 액세스** 단추를 탭합니다.

![표준 사례처럼 즉각적인 등록 옵션을 제공하는 대신 중간에 큰 텍스트 "회사 콘텐츠 액세스"가 표시된 Android 회사 포털 앱 이미지](./media/and_access_company_content_after_1706.png)

그러면 사용자가 장치에서 사용하기 위해 앱에 권한을 부여하도록 회사 포털 웹 사이트로 이동됩니다. 회사 포털 웹 사이트에서 사용자 자격 증명을 확인합니다.

![로그인을 확인하는 회사 포털 웹 사이트 이미지](./media/and_iwp_sign_in_auth_page_after_1706.png)

**동작** 메뉴를 탭하면 전체 관리에 앱을 등록할 수 있습니다.

![장치 등록 옵션이 있는 화면 오른쪽 위의 메뉴가 표시된 Android용 회사 포털 앱 이미지](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Windows 10 크리에이터스 업데이트와 동기화하는 앱 개선 사항 <!--676505-->

Windows 10용 회사 포털 앱은 이제 Windows 10 크리에이터스 업데이트(버전 1703)가 설치되어 있는 장치의 앱 설치 요청 동기화를 자동으로 시작합니다. 이렇게 하면 "동기화 보류 중" 상태에 있는 동안의 앱 설치 지연 문제를 줄일 수 있습니다. 사용자가 수동으로 앱 내에서 동기화를 시작할 수도 있습니다.

![Microsoft Word 다운로드가 회사 포털 앱 스토어에서 보류 중 상태인 Windows 10 회사 포털 앱 이미지](./media/w10_download_pending_after_1706.png)

![장치가 동기화 중이며 앱 다운로드를 시도하고 있음을 나타내는 상태 메시지와 함께 새 자동 동기화 상태가 표시된 Windows 10 회사 포털 앱 이미지](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 회사 포털에 대한 새로운 단계별 환경 <!---1058938--->
Windows 10용 회사 포털 앱에 식별되거나 등록되지 않은 장치에 대한 단계별 Intune 연습 환경이 포함될 예정입니다. 새 환경에서는 Azure Active Directory 등록(조건부 액세스 기능에 필요) 및 MDM 등록(장치 관리 기능에 필요) 과정을 사용자에게 안내하는 단계별 지침을 제공합니다. 회사 포털 홈 페이지에서 안내 방식 환경에 액세스할 수 있습니다. 사용자는 이러한 등록을 완료하지 않아도 앱을 계속 사용할 수 있지만 제한된 기능만 사용할 수 있습니다.

이 업데이트는 Windows 10 1주년 업데이트(빌드 1607) 이상을 실행하는 장치에서만 표시됩니다.

![사용 중인 장치가 회사에서 사용하도록 아직 설정되지 않았으며 사용자가 설정을 시작하려면 메시지를 선택해야 한다고 사용자에게 알리는 상태 메시지가 "장치" 목록의 중간에 표시된 Windows 10 회사 포털 앱 방문 페이지 이미지](./media/win10_guided_enroll_select_setup_after_1706.png)

![이 장치에 회사 계정을 추가해야 관리에 등록할 수 있다고 사용자에게 경고하는 Windows 10 회사 포털 앱 설정 페이지 이미지](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![등록을 완료하려면 설정 앱으로 이동한 다음, "연결"을 선택해야 한다고 사용자에게 알리는 이 장치 페이지에 회사 계정을 추가하는 Windows 10 회사 포털 앱의 이미지 이렇게 하면 화면에서 회사 포털 앱으로 돌아가 등록을 완료해야 한다고 알립니다.](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![이제 사용자 장치가 등록되었으며 계속하려면 '다음' 단추를 탭해야 한다고 알리는 완료 상태 메시지가 표시된 Windows 10 회사 포털 앱의 관리에 등록 화면 이미지](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![사용자에게 모든 설정이 완료되었으며 회사 계정을 제대로 추가하여 장치가 등록되었음을 알리는 Windows 10 회사 포털 앱 완료 화면 이미지](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>회사 포털을 쉽게 제거할 수 있는 새로운 메뉴 작업 <!--1164569-->
사용자 여러분의 의견에 따라 장치에서 회사 포털 제거를 시작할 수 있는 새로운 메뉴 작업이 Android용 회사 포털 앱에 추가되었습니다. 이 작업을 수행하면 Intune 관리에서 장치가 제거되므로 사용자가 장치에서 앱을 제거할 수 있습니다.

![오른쪽 위에 작업 메뉴가 열려 있는 Android 회사 포털 앱의 이미지 새로운 "회사 포털 제거" 옵션은 "내 프로필"과 "설정" 아래, 그리고 "사용 약관", "도움말 및 의견", "정보" 위에 있는 세 번째 옵션으로 제공됩니다.](./media/android_remove_cp_menu_action_after_1705.png)

![작업 메뉴에서 새로운 "회사 포털 제거" 옵션을 선택하면 제공되는 확인 대화 상자 이미지 이 대화 상자에는 "회사 포털을 제거하면 장치를 더 이상 IT 관리자가 관리하지 않게 되며 회사 데이터, 회사 앱 및 회사 메일에 대한 액세스 권한이 제거될 수 있습니다."라는 알림이 표시됩니다. 그런 다음 "예"를 선택하여 회사 포털 앱을 제거할 것인지를 확인하라는 메시지가 표시됩니다.](./media/android_remove_cp_menu_confirmation_after_1705.png)

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios---1230777--"></a>iOS용 회사 포털 앱의 앱 타일 개선 사항 <!--1230777-->
사용자가 회사 포털에 대해 설정하는 브랜딩 색을 반영하도록 홈 페이지의 앱 타일 디자인이 업데이트되었습니다.

**업데이트 전**

!["모든 앱", "추천 앱" 및 "범주"의 미리 설정된 채우기 이미지가 표시되어 있는 업데이트 전의 iOS용 회사 포털 앱 이미지](./media/cp_ios_homepage_before_1705.png)

**업데이트 후**

![조직에 맞는 색을 선택하는 기능이 반영된 업데이트 후의 iOS용 회사 포털 앱 이미지](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>이제 iOS용 회사 포털 앱에서 계정 선택기 사용 가능
사용자가 회사 또는 학교 계정을 사용하여 iOS 장치에서 다른 Microsoft 앱에 로그인한 경우 처음으로 회사 포털에 로그인할 때 새로운 계정 선택기가 나타날 수 있습니다.

![테스트 사용자 "Robin Swanson"이 두 전자 메일 주소 중 하나를 선택하는 방법을 보여 주는 계정 선택기 이미지 위 그림에 나와 있는 것처럼, 두 주소 아래에는 사용자가 다른 계정으로 로그인하는 데 사용할 수 있는 단추가 있습니다.](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>2017년 4월

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser 및 회사 포털의 새 아이콘 <!--918433, 918431-->

Managed Browser 앱의 Android 및 iOS 버전 모두에서 아이콘이 업데이트됩니다. 새 아이콘은 업데이트된 Intune 배지를 포함하므로 EM+S(Enterprise Mobility + Security)의 다른 앱과 더 일관된 환경을 제공합니다.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width="200" height="366" align="center">
           </td>
      </tr>
   </table>
</body>
</html>

회사 포털도 앱의 Android, iOS 및 Windows 버전에 대해 업데이트된 아이콘을 수신하므로 EM+S의 다른 앱과의 일관성을 개선합니다. 이러한 아이콘은 4월부터 5월 말까지 여러 플랫폼에서 점진적으로 출시됩니다.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 회사 포털의 로그인 진행률 표시기 <!--953374-->

Android 회사 포털 앱의 업데이트에는 사용자가 앱을 시작하거나 다시 시작할 때 로그인 진행률 표시기가 표시됩니다. 표시기에서는 "연결 중..."에서부터 "로그인 중...", "보안 요구 사항을 확인하는 중..."까지 새로운 상태를 진행한 후 사용자가 앱에 액세스할 수 있도록 허용합니다.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width="200" height="366" align="center">
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width="200" height="366" align="center">
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Windows 10 회사 포털 앱에 대해 앱 설치 상태 개선 <!--676495-->
이제 Windows 10 회사 포털 앱에서는 앱 세부 정보 페이지에 설치 진행률 표시줄을 제공합니다. 이 진행률 표시줄은 Windows 10 1주년 업데이트 이상을 실행하는 장치의 최신 앱에서 지원됩니다.

__이전__ ![상태가 ‘설치 중’으로 표시되는 이전 버전의 로딩 화면 이미지](./media/cp_win10_install_status_before_1704.png)

__이후__ ![이제 설치 진행률 표시줄이 표시되는 업데이트된 버전의 로딩 화면 이미지](./media/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>2017 년 2월

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Android용 회사 포털 앱의 새 사용자 환경 <!--621622, announced 1702-->
3월부터, Android용 회사 포털 앱이 [material design guidelines](https://material.io/guidelines/material-design/introduction.html)(재료 디자인 지침)에 따라 모양과 느낌이 더욱 세련되어집니다. 이러한 향상된 사용자 환경에는 다음이 포함됩니다.

* __색__: 탭 헤더에 사용자 지정 색상표에 따라 색을 표시할 수 있습니다.

![왼쪽은 업데이트 전의 Android용 회사 포털 앱 이미지입니다. 오른쪽은 업데이트 후의 Android용 회사 포털 앱 이미지입니다. 두 이미지 모두에서 사용 가능한 세 탭인 앱, 장치 및 IT 담당자 중에 장치 탭이 선택된 탭으로 표시되어 있습니다.](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __인터페이스__: __앱__ 탭에서 __추천 앱__ 및 __모든 앱__ 단추가 업데이트되었습니다. __검색__ 단추는 이제 부동 작업 단추입니다.

![왼쪽은 업데이트 전의 Android용 회사 포털 앱 이미지입니다. 오른쪽은 업데이트 후의 Android용 회사 포털 앱 이미지입니다. 두 이미지 모두에서 사용 가능한 세 탭인 앱, 장치, IT 담당자 중에서 앱 탭이 선택된 탭으로 표시되어 있습니다.](./media/CP_Android_AppsTab_BeforeAfter.png)

* __탐색__: 모든 앱은 쉽게 탐색할 수 있도록 __추천__, __전체__ 및 __범주__ 탭으로 구분된 뷰를 표시합니다. __IT 담당자__는 가독성 향상을 위해 간소화 되었습니다.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width="200" height="366" align="center">
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>2017년 1월

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>회사 포털 웹 사이트 현대화 <!--753980, announced 1701-->
2월부터 회사 포털 웹 사이트는 관리 장치가 없는 사용자를 대상으로 하는 앱을 지원합니다. 웹 사이트는 다른 Microsoft 제품과 마찬가지로 새로운 고대비 색 구성표, 동적 그림 및 "햄버거 메뉴"를 사용합니다. ![이제 회사 포털 웹 사이트 왼쪽 상단에 추가된 햄버거 메뉴의 작은 이미지에는](./media/CP_hamburger_menu.png) 기술 지원팀 연락처 세부 정보와 기존 관리되는 장치에 관한 정보가 포함됩니다. 방문 페이지는 추천 및 최근에 업데이트된 앱에 대한 슬라이드를 포함하여 사용자가 사용할 수 있는 앱을 강조하도록 재조정됩니다.

![왼쪽은 이전 버전의 [앱], [내 장치] 및 [Featured and Categories]\(추천 및 범주) 보기를 포함하는 회사 포털 웹 사이트의 현재 버전 이미지입니다. 오른쪽은 새로 고쳐진 앱 슬라이드, [Recently Published]\(최근 게시) 앱 목록 및 업데이트된 [Categories]\(범주) 보기가 포함된 회사 포털 웹 사이트의 업데이트된 버전 이미지입니다.](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>UI에서 곧 공개 예정
이는 사용자 인터페이스를 업데이트하여 사용자 환경을 개선할 방법에 대한 계획입니다.

> [!Note]
> 아래 이미지는 미리 보기일 수 있으며 발표된 제품은 제공된 버전과 다를 수 있음에 유의하세요.

### <a name="ui-iwp"></a>회사 포털 웹 사이트의 새로운 사용자 환경 업데이트<!--2000968-->

UI 업데이트, 간소화된 워크플로 및 향상된 접근성 기능을 통해 8월부터 새로운 회사 포털 웹 사이트 환경을 도입할 예정입니다. 여기에는 앱 공유 및 전반적인 성능 향상과 같은 고객 기반 고급 기능이 포함되어 보다 편리한 사용자 환경을 제공합니다.

고객의 의견에 따라 몇 가지 새로운 기능을 추가했습니다. 그러면 다음과 같은 기존 기능과 유용성을 크게 향상시킵니다.

-   웹 사이트 전체 UI 개선 사항
-   앱에 대한 직접 링크를 공유하는 기능
- 대규모 앱 카탈로그의 성능 향상

이 변경 내용을 준비하기 위해 조치를 취할 필요가 없습니다. 업데이트된 회사 포털 웹 사이트가 제공될 때 알려드리겠습니다. 그러나 결국 업데이트된 스크린샷을 포함한 최종 사용자 문서를 업데이트해야 할 수 있습니다. 웹 사이트에서 iOS 앱의 **앱** 섹션을 제공하므로 iOS에서 회사 포털 앱에 대한 설명서를 업데이트해야 할 수도 있습니다.  

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>회사 포털 웹 사이트의 UI 업데이트 <!--1313244 part 2-->

__추천 앱 업데이트__ 사용자가 추천하기 위해 선택한 앱을 찾아볼 수 있는 사이트에 전용 페이지를 추가하고 홈페이지의 추천 섹션에서 UI를 일부 조정했습니다.

![앱을 표시하는 다양한 색상의 타일입니다. 각 앱 아래에는 큰 사각형의 색상이 있습니다. 여기서 이 색상은 앱 로고의 기본 색상에서 가져옵니다. “추천 앱” 섹션은 회사 포털 앱의 맨 위에 표시됩니다.](./media/cp_win10_colorful_tiles_after_1708.png)



### <a name="see-also"></a>참고 항목
* [Microsoft Intune 블로그](http://go.microsoft.com/fwlink/?LinkID=273882)
* [클라우드 플랫폼 로드맵](https://www.microsoft.com/cloud-platform/roadmap)
* [Intune의 새로운 기능](https://docs.microsoft.com/intune/whats-new)
