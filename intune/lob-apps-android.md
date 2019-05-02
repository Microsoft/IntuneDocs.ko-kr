---
title: Microsoft Intune에 Android 기간 업무 앱 추가
description: Microsoft Intune에 Android LOB(기간 업무) 앱을 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5be123dc918785c1c60ec08e5815d642a3f13f72
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587470"
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>Microsoft Intune에 Android 기간 업무 앱 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

LOB(기간 업무) 앱은 앱 설치 파일에서 추가하는 앱입니다. 이러한 종류의 앱은 일반적으로 사내에서 작성됩니다. Intune이 사용자 디바이스에 LOB 앱을 설치합니다. 

> [!Note]
> 관리되는 Google Play 스토어의 LOB 앱에 대한 자세한 내용은 [관리되는 Google Play 스토어의 기간 업무 앱 사용](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-managed-google-play-store)을 참조하세요. 

> [!Note]
> Android for Work 디바이스의 경우 [이 문서](https://docs.microsoft.com/intune/apps-add-android-for-work)를 따릅니다. 

## <a name="step-1-specify-the-software-setup-file"></a>1단계: 소프트웨어 설치 파일 지정

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드에서 **관리** > **앱**을 차례로 선택합니다.
5. 앱 목록 위에서 **추가**를 선택합니다.
6. **앱 추가** 창에서 **기간 업무 앱**을 선택합니다.

## <a name="step-2-configure-the-app-package-file"></a>2단계: 앱 패키지 파일 구성

1. **앱 추가** 창에서 **앱 패키지 파일**을 선택합니다.
2. **앱 패키지 파일** 창에서 찾아보기 단추를 선택합니다. 그런 다음, 확장명이 **.apk**인 Android 설치 파일을 선택합니다.
3. 작업을 마쳤으면 **확인**을 선택합니다.


## <a name="step-3-configure-app-information"></a>3단계: 앱 정보 구성

1. **앱 추가** 창에서 **앱 정보**를 선택합니다.
2. **앱 정보** 창에서 앱의 세부 정보를 추가합니다. 선택한 앱에 따라 이 창의 일부 값이 자동으로 채워질 수 있습니다.
    - **이름**: 회사 포털에 표시되는 앱 이름을 입력합니다. 사용하는 모든 앱 이름이 고유한지 확인합니다. 동일한 앱 이름을 두 번 사용하는 경우 앱 중 하나만 회사 포털에 표시됩니다.
    - **설명**: 앱에 대한 설명을 입력합니다. 설명은 회사 포털에 표시됩니다.
    - **게시자**: 앱 게시자의 이름을 입력합니다.
    - **최소 운영 체제**: 목록에서 앱을 설치할 수 있는 최소 운영 체제 버전을 선택합니다. 이전 버전의 운영 체제를 사용하는 디바이스에 앱을 할당할 경우 앱이 설치되지 않습니다.
    - **범주**: 기본 제공 앱 범주를 하나 이상 선택하거나 직접 만든 범주를 선택합니다. 범주를 사용하면 사용자가 회사 포털을 탐색할 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱을 쉽게 확인할 수 있도록 표시합니다.
    - **정보 URL**: 필요에 따라 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 이 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에 표시됩니다.
    - **개발자**: 선택적으로, 앱 개발자의 이름을 입력합니다.
    - **소유자**: 선택적으로, 이 앱의 소유자 이름을 입력합니다. 예를 들어 **HR 부서** 등을 입력합니다.
    - **메모**: 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고**: 앱과 연결된 아이콘을 업로드합니다. 사용자가 회사 포털을 탐색할 때 이 아이콘이 앱과 함께 표시됩니다.
3. 작업을 마쳤으면 **확인**을 선택합니다.

## <a name="step-4-finish-up"></a>4단계: 끝내기

1. **앱 추가** 창에서 앱의 세부 정보가 올바른지 확인합니다.
2. **추가**를 선택하여 Intune에 앱을 업로드합니다.

이제 만든 앱이 앱 목록에 나타납니다. 목록에서 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

## <a name="step-5-update-a-line-of-business-app"></a>5단계: 기간 업무 앱 업데이트

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> Intune 서비스에서 새 APK 파일을 디바이스에 성공적으로 배포하려면 APK 패키지의 AndroidManifest.xml 파일에 있는 `android:versionCode` 문자열을 증분해야 합니다.

## <a name="next-steps"></a>다음 단계

- 만든 앱이 앱 목록에 나타납니다. 이제 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

- 앱의 속성 및 할당을 모니터링할 수 있는 방법에 대해 자세히 알아봅니다. [앱 정보 및 할당을 모니터링하는 방법](apps-monitor.md)을 참조하세요.

- Intune에서 앱의 컨텍스트에 대해 자세히 알아봅니다. [디바이스 및 앱 수명 주기에 대한 개요](introduction-device-app-lifecycles.md)를 참조하세요.
