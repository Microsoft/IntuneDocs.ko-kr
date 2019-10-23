---
title: Microsoft Managed Home Screen 앱 구성
titleSuffix: Microsoft Intune
description: Microsoft Managed Home Screen 앱을 구성하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d47cee2c26960775d268b317845c118e99b85fe9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507585"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Android Enterprise용 Microsoft Managed Home Screen 앱 구성

Managed Home Screen은 Intune을 통해 등록되어 다중 앱 키오스크 모드에서 실행되는 기업 소유의 Android Enterprise 전용 디바이스에 사용되는 애플리케이션입니다. Managed Home Screen은 이러한 디바이스를 바탕으로 실행되는 다른 승인된 앱의 시작 관리자로 작동합니다. Managed Home Screen을 통해 IT 관리자는 디바이스를 사용자 지정하고 최종 사용자가 액세스할 수 있는 기능을 제한할 수 있습니다. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Microsoft Managed Home Screen 앱 구성 시기

일반적으로 디바이스 구성을 통해 설정을 사용할 수 있는 경우 여기서 설정을 구성합니다. 이렇게 하면 시간을 절약하고 오류를 최소화하며 더 나은 Intune 지원 환경을 제공합니다. 그러나 일부 Managed Home Screen 설정은 현재 Intune 콘솔의 **앱 구성 정책** 블레이드를 통해서만 사용할 수 있습니다. 이 문서를 통해 구성 디자이너 또는 JSON 스크립트를 사용하여 다양한 설정을 구성하는 방법을 알아봅니다. 

> [!NOTE]
> 현재 **클라이언트 앱**과 **디바이스 구성**을 통한 허용 목록의 애플리케이션 및 고정 웹 링크 설정이 가능하며 사용할 수 있습니다. Managed Home Screen에 영향을 미치는 **디바이스 구성**에서 사용 가능한 전체 설정 목록은 [전용 디바이스 설정](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)을 참조하세요.  

먼저 Azure Portal의 Intune 콘솔로 이동하여 **클라이언트 앱** > **앱 구성 정책**으로 이동합니다. **Android**를 실행하는 **관리 디바이스**에 대한 구성 정책을 추가하고 연결된 앱으로 **Managed Home Screen**을 선택합니다. **구성 설정**을 클릭하여 사용 가능한 여러 Managed Home Screen 설정을 구성할 수 있습니다. 

## <a name="choosing-a-configuration-settings-format"></a>구성 설정 형식 선택

Managed Home Screen의 구성 설정을 정의할 때 선택할 수 있는 방법은 두 가지가 있습니다.

- **구성 디자이너**를 사용하면 기능을 끄거나 켜게 토글하고 값을 설정할 수 있는 간편한 UI를 통해 설정을 구성할 수 있습니다. 이 방법에서는 값 형식이 `BundleArray`인 몇 가지 구성 키를 사용할 수 없습니다. 이러한 구성 키는 JSON 데이터 입력으로만 구성할 수 있습니다. 
- **JSON 데이터**를 사용하면 JSON 스크립트를 사용하여 가능한 모든 구성 키를 정의할 수 있습니다. 

구성 디자이너를 통해 속성을 추가하는 경우 **구성 설정 형식** 드롭다운에서 **JSON 입력 데이터**를 선택하여 이 속성을 자동으로 JSON으로 변환할 수 있습니다.

![구성 집합 형식 옵션 스크린샷](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>구성 디자이너 사용

구성 디자이너를 사용하면 미리 채워진 설정과 연결된 값을 선택할 수 있습니다. 

![추가된 구성 집합 스크린샷](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

다음 표는 Managed Home Screen의 사용 가능한 구성 키, 값 형식, 기본값 및 설명을 나열합니다. 설명은 선택한 값에서 예상되는 디바이스 작동을 제공합니다. 구성 디자이너에서 사용할 수 없는 구성 키는 이 표에 나열되지 않았습니다.

| 구성 키 | 값 형식 | 기본값 | 설명 |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 그리드 크기 설정 | 문자열 | 자동 | Managed Home Screen에 배치할 앱의 그리드 크기를 설정할 수 있습니다. 앱 행과 열 수를 설정하여 형식 `columns;rows`를 사용하여 그리드 크기를 정의할 수 있습니다. 그리드 크기를 정의할 경우 홈 화면의 행에 표시되는 최대 앱 수는 설정한 행 수가 되고, 홈 화면의 열에 표시되는 최대 앱 수는 설정한 열 수가 됩니다. |
| 화면 헤더 사용 | 부울 | TRUE | 피드, 피드 카드 등, 관리형 홈 화면이 제공하는 여러 보기에 대한 위 헤더를 사용합니다. 이 설정을 사용할 경우 디바이스 사용자에게 헤더가 표시됩니다. |
| 디바이스 상태 표시줄 사용 | 부울 | TRUE | 홈 화면에서 상태 표시줄을 사용합니다(WiFi 등, 현재 연결을 표시하는 위쪽 막대). 이 구성 키를 사용할 경우 최종 사용자는 연결 및 활성 앱을 나타내는 상태 표시줄에 아이콘이 표시되는 것을 볼 수 있습니다. |
| 알림 배지 사용 | 부울 | FALSE | 앱의 새 알림 수를 표시하는 앱 아이콘의 알림 배지를 사용합니다. 이 설정을 사용할 경우 최종 사용자에게 읽지 않은 알림이 있는 앱에 대한 알림 배지가 표시됩니다. 이 구성 키를 사용하지 않는 경우 최종 사용자에게 읽지 않은 알림이 있더라도 앱에 알림 배지가 표시되지 않습니다. |
| 홈 화면 잠금 | 부울 | TRUE | 최종 사용자가 홈 화면에서 앱 아이콘을 움직일 수 있는 기능을 제거합니다. 이 구성 키를 사용할 경우 홈 화면의 앱 아이콘이 잠기며 최종 사용자가 홈 화면의 다른 그리드 위치에 끌어서 놓을 수 없습니다. `false`로 하면 최종 사용자가 Managed Home Screen에서 애플리케이션과 웹 링크 아이콘을 이동할 수 있습니다.  |
| 디바이스 배경 무늬 설정 | 문자열 | Default | 배경 무늬로 설정하려는 이미지의 URL을 입력하여 원하는 배경 무늬를 설정할 수 있습니다. |
| 앱 아이콘 크기 설정 | integer | 2 | 홈 화면에 표시되는 앱의 아이콘 크기를 설정할 수 있습니다. 이 구성을 0(가장 작음), 1(작음), 2(보통), 3(큼) 및 4(가장 큼) 등의 값을 사용하여 다른 크기로 선택할 수 있습니다. |
| 앱 폴더 아이콘 설정 | integer | 0 | 홈 화면의 앱 폴더 표시를 정의할 수 있습니다. 다음 값 중에서 모양을 선택할 수 있습니다. 짙은 정사각(0), 짙은 원(1), 얇은 정사각(2), 얇은 원(3) |
| 제스처 사용 | 부울 | FALSE | 최종 사용자가 위로 살짝 밀기, 아래로 살짝 밀기 등, 여러 제스처에 동작을 할당할 수 있습니다. 이 구성 키를 사용하지 않도록 설정하면 최종 사용자가 다음 페이지가 있는 경우 오른쪽으로 밀었다가 홈 페이지로 돌아오는 작업만 가능합니다. |
| 세로 스크롤 사용 | 부울 | FALSE | Managed Home Screen의 세로 스크롤을 사용합니다. 이 구성 키를 사용할 경우 최종 사용자는 가로로 미는 것이 아니라 세로 동작을 통해서만 다른 페이지로 이동할 수 있습니다. |
| 홈 화면 테마 설정 | 문자열 | Theme.Light.Blue | 여러 색상으로 미리 정의된 테마 집합 중에서 홈 화면 테마를 선택할 수 있습니다. 다음 형식으로 문자열 값을 입력하여 다음 테마를 선택할 수 있습니다.   Theme.Light.Green. Light를 Dark로 바꾸면 더 어두운 테마가 되고 Green은 Blue, Yellow, Pink, Red, Orange 및 Purple로 바꿀 수 있습니다. |
| 고정 사용 | 부울 | FALSE | 영구 앱을 표시하고 설치된 모든 앱의 시작 지점이 되는 홈 화면 맨 아래의 앱 고정 섹션을 사용합니다. 이 구성 키를 사용할 경우 최종 사용자가 고정에서 앱에 액세스하고, 모든 앱 섹션을 통해 허용 목록에 있는지 여부에 관계없이 디바이스에 설치된 모든 앱 목록으로 이동할 수 있습니다. |
| 화면 방향 설정 | integer | 1 | 홈 화면의 방향을 가로 모드나 세로 모드로 설정하거나, 자동 회전을 허용할 수 있습니다. 값 1(세로 모드), 2(가로 모드), 3(자동 회전)을 입력하여 방향을 설정할 수 있습니다. |
| 홈 화면 피드 사용 | 부울 | FALSE | 홈 화면의 왼쪽을 살짝 밀면 표시되는 홈 화면 피드를 사용합니다. 이 피드는 뉴스, 캘린더, 자주 사용하는 앱, Cortana 음성 도우미 카드 등, 다양한 콘텐츠 형식을 표시합니다. 이 항목을 활성화하면 최종 사용자가 홈 화면을 왼쪽으로 살짝 밀어 피드로 이동할 수 있습니다. |
| 개요 모드 사용 | 부울 | FALSE | 최종 사용자가 기본 화면에서 오른쪽으로 살짝 밀어 액세스하는 홈 화면에서 다른 페이지를 추가하거나 제거할 수 있습니다. 이 항목을 사용할 경우 최종 사용자는 홈 화면 기본 페이지의 오른쪽에 페이지를 추가하고, 기본 페이지를 변경하며, Managed Home Screen의 설정에 액세스할 수 있습니다. |
| 디바이스 원격 분석 사용 | 부울 | FALSE | Managed Home Screen에 대해 수집되는 모든 원격 분석을 사용합니다. 이 항목을 사용하면 Microsoft가 특정 앱이 해당 디바이스에서 실행된 횟수 등과 같은 디바이스 사용 원격 분석을 수집할 수 있습니다. |
| 허용 목록에 있는 애플리케이션 설정 | bundleArray | FALSE | 디바이스에 설치된 앱 중에서 홈 화면에 표시할 앱 세트를 정의할 수 있습니다. 표시하려는 앱의 앱 패키지 이름을 입력해 정의할 수 있습니다. 예를 들어, com.microsoft.emmx는 홈 화면에서 설정에 액세스할 수 있게 지정합니다. 이 섹션에서 허용 목록에 넣은 앱은 기존에 디바이스에 설치되어 있어야 홈 화면에 표시될 수 있습니다. |
| 고정된 웹 링크 설정 | bundleArray | FALSE | 홈 화면에서 웹 사이트를 빠른 시작 아이콘으로 고정할 수 있습니다. 이 구성을 통해 URL을 정의하고 홈 화면에 등록하여 최종 사용자가 한 번의 탭으로 브라우저 안에서 실행할 수 있게 합니다. |
| 검색 창 사용 | 부울 | FALSE | 홈 화면에 검색 창을 사용하도록 설정합니다. 이 항목을 사용하면 디바이스 사용자가 홈 화면에 표시되는 검색 창에서 웹에 검색하려는 항목을 무엇이든 입력할 수 있습니다. |
| 설정 앱 사용 안 함 | 부울 | FALSE | Managed Home Screen의 설정 페이지를 사용하지 않습니다. 이 항목을 사용하지 않게 설정하면 디바이스의 최종 사용자가 Managed Home Screen의 설정으로 이동할 수 없습니다. |
| 화면 보호기 사용 | 부울 | FALSE | 화면 보호기 모드를 사용하거나 사용하지 않도록 지정합니다. true로 설정할 경우 **screen_saver_image**, **screen_saver_show_time**, **inactive_time_to_show_screen_saver** 및 **media_detect_screen_saver**를 구성합니다. |
| 화면 보호기 이미지 | 문자열 |   | 화면 보호기 이미지의 URL을 설정합니다. URL을 설정하지 않은 경우 디바이스는 화면 보호기가 활성화될 때 기본 화면 보호기를 표시합니다. 기본 이미지에는 Managed Home Screen 앱 아이콘이 표시됩니다.  |
| 화면 보호기 표시 시간 | integer | 0 | 디바이스가 화면 보호기 모드 중에 화면 보호기를 표시하는 시간을 초 단위로 설정하는 옵션을 제공합니다. 0으로 설정하면 디바이스가 활성 상태가 될 때까지 화면 보호기 모드로 화면 보호기가 계속 표시됩니다.  |
| 화면 보호기를 사용하도록 설정하는 비활성 시간 | integer | 30 | 화면 보호기를 실행하기 전까지 디바이스가 비활성 상태인 시간(초)입니다. 0으로 설정할 경우 디바이스가 화면 보호기 모드를 시작하지 않습니다. |
| 화면 보호기를 표시하기 전에 미디어 검색 | 부울 | TRUE | 오디오/비디오가 디바이스에서 재생 중일 때 디바이스 화면에 화면 보호기를 표시할지 여부를 선택합니다. true로 설정할 경우 디바이스는 **inactive_time_to_show_scree_saver**의 값과 관계없이 오디오/비디오를 재생하지 않습니다. false로 설정할 경우 **inactive_time_to_show_screen_saver**에서 설정한 값에 따라 디바이스 화면에 화면 보호기를 표시합니다.   |
| 가상 홈 단추 사용 | 부울 | FALSE | 이 설정을 `True`로 하면 최종 사용자가 Managed Home Screen 홈 단추에 액세스하여 현재 작업 중인 위치에서 Managed Home Screen으로 돌아갈 수 있습니다.  |
| 가상 홈 단추 형식 | 문자열 | swipe_up | **swipe_up**을 사용하면 살짝 밀기 제스처로 홈 단추에 액세스합니다. **float**를 사용하면 최종 사용자가 화면 주변으로 이동할 수 있는 고정 영구 홈 단추에 액세스합니다. |
| 배터리 및 신호 강도 표시줄 | 부울 | True  | 이 설정을 `True`로 하면 배터리 및 신호 강도 표시줄을 표시합니다. |
| 잠금 작업 모드 종료 암호 | 문자열 |   | 문제 해결을 위해 4-6자리 암호 코드를 입력하여 일시적으로 작업 잠금 모드를 중단합니다. |
| Wi-Fi 설정 표시 | 부울 | FALSE | 이 설정을 `True`로 하면 최종 사용자가 Wi-Fi를 끄거나 켤 수 있고, 다른 Wi-Fi 네트워크에 연결할 수 있습니다.  |
| Bluetooth 설정 표시 | 부울 | FALSE | 이 설정을 `True`로 하면 최종 사용자가 Bluetooth를 끄거나 켤 수 있고, 다른 Bluetooth 지원 디바이스에 연결할 수 있습니다.   |
| 폴더의 애플리케이션을 이름별로 정렬 | 부울 | TRUE | 이 설정을 `False`로 설정하면 폴더의 항목을 지정된 순서대로 표시할 수 있습니다. 그러지 않으면 폴더에 사전 순으로 표시됩니다.   |
| 애플리케이션 순서 사용 | 부울 | FALSE | 이 설정을 `True`로 설정하면 Managed Home Screen에서 애플리케이션, 웹 링크 및 폴더의 순서를 설정하는 기능을 사용하도록 설정할 수 있습니다. 사용하도록 설정하면 **app_order**로 순서를 설정합니다. 최종 사용자는 Bluetooth를 켜거나 끄고 다른 Bluetooth 지원 디바이스에 연결할 수 있습니다.   |
| 애플리케이션 순서 | bundleArray | FALSE | Managed Home Screen에서 애플리케이션, 웹 링크 및 폴더의 순서를 지정할 수 있습니다. 이 설정을 사용하려면 **Lock Home Screen**(홈 화면 잠금)을 사용하도록 설정해야 하고, **눈금 크기 설정**을 정의해야 하며, **애플리케이션 순서 사용**을 `True`로 설정해야 합니다.   |

## <a name="enter-json-data"></a>JSON 데이터 입력

JSON 데이터를 입력하여 Managed Home Screen에 사용 가능한 모든 설정과 **구성 디자이너**에서 사용하지 않게 지정된 설정을 구성합니다.

![추가된 JSON 데이터 스크린샷](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

위의 **구성 디자이너** 표에 나열된 목록 외에도 다음 표는 JSON 데이터를 통해서만 구성할 수 있는 구성 키를 제공합니다.

|    구성 키    |    값 형식    |    기본값    |    설명    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    허용 목록에 있는 애플리케이션 설정    |    bundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    디바이스에 설치된 앱 중에서 홈 화면에 표시할 앱 집합을 정의할 수 있습니다. 표시하려는 앱의 앱 패키지 이름을 입력할 수 있습니다. 예를 들어, com.android.settings는 홈 화면에서 설정을 액세스할 수 있게 지정합니다. 이 섹션에서 허용 목록에 넣은 앱은 기존에 디바이스에 설치되어 있어야 홈 화면에 표시될 수 있습니다.    |
|    고정된 웹 링크 설정    |    bundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    홈 화면에서 웹 사이트를 빠른 시작 아이콘으로 고정할 수 있습니다. 이 구성을 통해 URL을 정의하고 홈 화면에 등록하여 최종 사용자가 한 번의 탭으로 브라우저 안에서 실행할 수 있게 합니다.    |
|    앱 그룹화를 위한 관리형 폴더 만들기    |    bundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    폴더 안에서 폴더 및 그룹 앱을 만들고 명명할 수 있습니다. 최종 사용자는 폴더를 이동하거나, 폴더 이름을 바꾸거나, 폴더 안에서 앱을 이동할 수 없습니다.   폴더는 만든 순서대로 표시되며 폴더 안의 앱은 사전순으로 표시됩니다.         참고: 폴더로 그룹화하려는 모든 앱은 필요에 맞게 디바이스에 할당되고 Managed Home Screen에 추가되어 있어야 합니다.     |

다음은 모든 사용 가능한 구성 키를 포함한 JSON 스크립트 예제입니다.

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "grid_size",
            "valueString": "4;5"
        },
        {
            "key": "app_order_enabled",
            "valueBool": true
        },
        {
            "key": "apps_in_folder_ordered_by_name",
            "valueBool": true
        },
        {
            "key": "app_orders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.Microsoft.emmx"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 1
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Work"
                        },
                        {
                            "key": "type",
                            "valueString": "managed_folder"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 2
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.microsoft.launcher.enterprise"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "class",
                            "valueString": "com.microsoft.launcher.launcher"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 3
                        }
                    ]
                }
            ]
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="googles-android-device-policy-app"></a>Google의 Android 디바이스 정책 앱
이제 Managed Home Screen 앱에서 Google의 Android 디바이스 정책 앱에 액세스할 수 있습니다. Managed Home Screen 앱은 Intune에 다중 앱 키오스크 모드를 사용하는 AE(Android 엔터프라이즈) 전용 디바이스로 등록된 디바이스에 사용되는 사용자 지정 시작 관리자입니다. Android 디바이스 정책 앱에서 액세스하거나 지원 및 디버깅을 위해 사용자를 Android 디바이스 정책 앱으로 안내할 수 있습니다. 이 시작 기능은 디바이스가 등록되고 Managed Home Screen으로 잠길 때 사용할 수 있습니다. 이 기능을 사용하기 위해 추가 설치가 필요하지 않습니다.

## <a name="managed-home-screen-debug-screen"></a>Managed Home Screen 디버그 화면
디버그 화면이 표시될 때까지 **뒤로** 단추를 클릭하여 Managed Home Screen의 디버그 화면에 액세스할 수 있습니다(**뒤로** 단추를 15번 이상 클릭). 이 디버그 화면에서 Android 디바이스 정책 애플리케이션을 시작하거나, 로그를 확인 및 업로드하거나, 키오스크 모드를 일시적으로 중지하여 디바이스를 업데이트할 수 있습니다. 키오스크 모드를 일시 중지하는 방법에 대한 자세한 내용은 Android Enterprise [전용 디바이스 설정](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)에서 **키오스크 모드 유지** 항목을 참조하세요.

## <a name="next-steps"></a>다음 단계

- Android Enterprise 전용 디바이스에 대한 자세한 정보는 [Android Enterprise 전용 디바이스의 Intune 등록 설정](../enrollment/android-kiosk-enroll.md)을 참조하세요.
