---
title: Microsoft Intune의 Android용 키오스크 설정 - Azure | Microsoft Docs
description: Android 키오스 장치를 단일 앱 및 다중 앱 키오스크로 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cef98527ee2c281547f8046f3c6f08275d8f0807
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329386"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Intune에서 Android 장치에 대한 키오스크 설정

장치 구성 설정을 사용하여 장치를 단일 또는 다중 앱 키오스크 모드로 구성할 수 있습니다. 장치가 키오스크 모드에 있는 경우 장치의 사용은 제한 프로필에 정의된 앱 또는 웹 링크로 제한됩니다. 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>Android 키오스크 장치를 단일 앱으로 제한

키오스크 장치의 제한 프로필이 **키오스크 모드** = **단일 앱 키오스크**로 설정된 경우 사용자는 단일 앱에만 액세스할 수 있습니다. 이 모드로 구성된 장치가 시작되면 특정 앱이 시작됩니다. 사용자가 새 앱을 열거나 실행 중인 앱을 변경하는 것을 제한합니다.

1. 키오스크 장치에서 사용할 앱이 [장치에 배포](apps-deploy.md)되어 있고 키오스크 장치용으로 만든 장치 그룹에 앱을 할당했는지 확인합니다.
2. [Intune 포털](https://portal.azure.com)로 이동하여 **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. **프로필 만들기** 블레이드에서 다음 필드를 설정합니다.
     - **Name**
     - **플랫폼**: Android 엔터프라이즈
     - **프로필 유형**: 장치 소유자만 > 장치 제한 사항
4. **설정** > **키오스크**를 선택합니다.
5. **키오스크 모드**의 경우 **단일 앱 키오스크**를 선택합니다.
6. **관리되는 앱 선택**을 선택한 다음, 이 프로필을 사용하는 장치에서만 사용할 수 있는 관리되는 Google Play 앱을 선택합니다.
7. **확인** > **확인** > **확인** > **만들기**를 선택합니다.
8. 방금 만든 프로필 > **할당**을 선택합니다.
9. **할당할** 아래에서 **선택된 그룹**을 선택합니다.
10. **포함할 그룹 선택** > 키오스크 장치용으로 만든 장치 그룹 선택 > **선택**을 선택합니다.

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>키오스크 장치 앱 또는 웹 링크 집합으로 제한

키오스크 장치의 제한 프로필이 **키오스크 모드** = **다중 앱 키오스크**로 설정된 경우 사용자는 구성하는 앱의 제한된 수에만 액세스할 수 있습니다. 사용자가 방문할 수 있는 웹 링크의 집합을 정의할 수도 있습니다. 정책이 적용되면 사용자는 홈 화면에서 허용되는 앱의 아이콘을 볼 수 있습니다.

여러 앱용 Android 키오스크 장치를 설정하려면 다음의 기본 단계를 따릅니다.

1. [관리되는 Google Play에서 관리되는 홈 화면 앱 가져오기 및 배포](#import-and -deploy-the-managed-home-screen-app)
2. [키오스크 모드에서 사용할 수 있는 앱 추가 및 할당](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. (선택 사항) [키오스크 모드에서 사용할 수 있는 웹 링크 추가](#add-web-links-that-can-be-used-in-kiosk-mode)

### <a name="import-and-deply-the-managed-home-screen-app"></a>관리되는 홈 화면 앱을 가져오기 및 배포

1. [Google Play에서 관리되는 홈 화면 페이지](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise)로 이동하여 다른 관리되는 Google Play 앱에 사용하는 동일한 계정으로 로그인합니다.
2. **승인**을 선택합니다.
3. [Intune 포털](https://portal.azure.com)로 이동하여 **클라이언트 앱** > **관리되는 Google Play** > **동기화**를 선택합니다.
4. **앱** > **관리되는 홈 화면** > **할당** > **그룹 추가**를 선택합니다.
5. **할당 유형** 아래에서 **필수**를 선택합니다.
6. **그룹 포함** > **포함할 그룹 선택** > 키오스크 장치용으로 만든 장치 그룹 선택 > **선택** > **확인** > **확인** > **저장**을 선택합니다.

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>키오스크 모드에서 사용할 수 있는 앱 추가 및 할당

키오스크 장치에서 사용하려는 각 앱에 대해 다음 단계를 따릅니다.

1. [Intune에 앱 추가](store-apps-android.md).
2. **클라이언트 앱** > **앱** > 앱 선택 > **할당** > **그룹 추가**를 선택합니다.
3. **할당 유형** 아래에서 **필수**를 선택합니다.
4. **그룹 포함** > **포함할 그룹 선택** > 키오스크 장치용으로 만든 장치 그룹 선택 > **선택** > **확인** > **확인** > **저장**을 선택합니다.

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>키오스크 모드에서 사용할 수 있는 웹 링크 추가

1. [Intune 포털](https://portal.azure.com)로 이동하여 **클라이언트 앱** > **앱** > **추가**를 선택합니다.
2. **앱 유형** 아래에서 **웹 링크**를 선택합니다.
3. **구성**을 선택하고 필요한 정보를 제공합니다. 로고 이미지는 웹 사이트의 favicon.ico에서 자동으로 검색되므로 추가할 필요가 없습니다.
4. **확인** > **추가**를 선택합니다.

[모바일 앱](apps-add.md)을 사용하여 키오스크 장치에 웹 브라우저 앱을 배포했는지 확인합니다.

### <a name="create-a-multi-app-kiosk-profile"></a>다중 앱 키오스크 프로필 만들기

1. [Intune 포털](https://portal.azure.com)로 이동하여 **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. **프로필 만들기** 블레이드에서 다음 필드를 설정합니다.
     - **이름**: 직관적인 이름 입력
     - **플랫폼**: Android 엔터프라이즈
     - **프로필 유형**: 장치 소유자만 > 장치 제한 사항
4. **설정** > **키오스크**를 선택합니다.
5. **키오스크 모드**의 경우 **다중 앱 키오스크**를 선택합니다.
6. **추가**를 선택한 다음, 이 프로필을 사용하는 장치에 사용할 수 있는 앱 또는 링크를 선택합니다.
7. **확인** > **확인** > **확인** > **만들기**를 선택합니다.
8. 방금 만든 프로필 > **할당**을 선택합니다.
9. **할당할** 아래에서 **선택된 그룹**을 선택합니다.
10. **포함할 그룹 선택** > 키오스크 장치용으로 만든 장치 그룹 선택 > **선택** > **저장**을 선택합니다.

## <a name="next-steps"></a>다음 단계
[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
