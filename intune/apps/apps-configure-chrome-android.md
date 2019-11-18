---
title: Intune을 사용하여 Android 장치용 Google Chrome 구성
titleSuffix: Microsoft Intune
description: Android 장치용 Google Chrome에서 Intune 구성 정책을 사용합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14e9aa6e82d7b3e24350de8770f02b0a08695e1a
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801658"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Intune을 사용하여 Android 장치용 Google Chrome 구성 

Intune 앱 구성 정책을 사용하여 Android 장치용 Google Chrome을 구성할 수 있습니다. 앱 설정을 자동으로 적용할 수 있습니다. 예를 들어 차단하거나 허용하려는 책갈피와 URL을 구체적으로 설정할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

- 사용자의 Android 엔터프라이즈 디바이스를 Intune에 등록해야 합니다. 자세한 내용은 [Android 엔터프라이즈 회사 프로필 디바이스 등록 설정](~/enrollment/android-work-profile-enroll.md)을 참조하세요.
- Google Chrome은 관리되는 Google Play 앱으로 추가됩니다. 관리되는 Google Play에 대한 자세한 내용은 [Intune 계정을 관리되는 Google Play 계정에 연결](~/enrollment/connect-intune-android-enterprise.md)을 참조하세요.

## <a name="add-the-google-chrome-app-to-intune"></a>Intune에 Google Chrome 앱 추가

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **Intune** 창에서 **클라이언트 앱** > **앱** > **추가**를 선택한 다음 **관리되는 Google Play** 앱을 추가합니다.
3. 관리되는 Google Play로 이동하여 **Google Chrome**을 검색하고 승인합니다.

    ![Google Chrome 검색 및 승인](~/apps/media/apps-configure-chrome-android/search.png)

4. Google Chrome을 필수 앱 유형으로 사용자 그룹에 할당합니다. Intune에 디바이스를 등록하면 Google Chrome이 자동으로 배포됩니다.

Intune에 관리되는 Google Play 앱을 추가하는 방법에 대한 자세한 내용은 [관리되는 Google Play 스토어 앱](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps)을 참조하세요.

## <a name="add-app-configuration-for-managed-ae-devices"></a>관리되는 AE 디바이스에 대한 앱 구성 추가

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 창에서 **앱 구성 정책** > **추가**를 선택합니다.
2. 정책 이름을 추가한 다음 디바이스 등록 유형에서 **관리 디바이스**를 선택하고 플랫폼에서 **Android**를 선택합니다.

    ![Google Chrome 구성 정책 추가](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. **연결된 앱**을 클릭하고 **Google Chrome**을 선택합니다.

    ![연결된 앱에서 Google Chrome 선택](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. **구성 설정**을 클릭하고, **구성 디자이너 사용**을 선택한 다음, **추가**를 클릭하여 구성 키를 선택합니다.

    ![구성 디자이너 사용](~/apps/media/apps-configure-chrome-android/configuration.png)

    다음은 일반 설정의 예입니다.
    - **URL 목록에 대한 액세스 차단**: `["*"]`
    - **URL 목록에 대한 액세스 허용**: `["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
    - **관리되는 책갈피**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Incognito 모드 가용성**: `Incognito mode disabled`

    구성 디자이너를 사용하여 추가된 구성 설정은 표에 나열됩니다. 

    ![일반 설정](~/apps/media/apps-configure-chrome-android/common-settings.png)

    위 설정은 책갈피를 만들고 `baidu.com`, `yahoo.com`, `chromium.org` 및 `chrome://`을 제외한 모든 URL에 대한 액세스를 차단합니다.

5. **확인**과 **추가**를 클릭하여 구성 정책을 Intune에 추가합니다.
6. 이 구성 정책을 사용자 그룹에 할당합니다. 자세한 내용은 [Microsoft Intune을 사용하여 그룹에 앱 할당](~/apps/apps-deploy.md)을 참조하세요. 

## <a name="verify-the-device-settings"></a>디바이스 설정 확인

Android 엔터프라이즈에 Android 장치를 등록하면 포트폴리오 아이콘이 포함된 관리되는 Google Chrome 앱이 자동으로 배포됩니다.
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Google Chrome을 시작하면 적용되는 설정을 찾을 수 있습니다.

   책갈피:<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   차단된 URL:<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   URL 허용:<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   Incognito 탭:<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>문제 해결

1. Intune 포털을 확인하여 정책 배포 상태를 모니터링합니다.

    ![정책 배포 상태 모니터링](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Google Chrome을 시작하고 **chrome://policy**를 방문합니다. 설정이 성공적으로 적용되었는지 확인할 수 있습니다.

    ![설정이 성공적으로 적용되었는지 확인](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>추가 정보

- [관리되는 Android 엔터프라이즈 디바이스용 앱 구성 정책 추가](~/app-configuration-policies-use-android.md)
- [Chrome Enterprise 정책 목록](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>다음 단계

- Android Enterprise 완전 관리형 디바이스에 대한 자세한 정보는 [Android Enterprise 완전 관리형 디바이스의 Intune 등록 설정](~/enrollment/android-fully-managed-enroll.md)을 참조하세요.
