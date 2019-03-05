---
title: Microsoft Intune에 iOS 기간 업무 앱 추가
titlesuffix: ''
description: Microsoft Intune에 iOS LOB(기간 업무) 앱을 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7206a29bea5a53bf13b43a9881c629f27e949dbb
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230007"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Microsoft Intune에 iOS 기간 업무 앱 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 문서의 정보를 사용하여 Microsoft Intune에 iOS LOB(기간 업무) 앱을 추가할 수 있습니다.

>[!NOTE]
>iOS 디바이스 사용자는 주식, 지도 같은 기본 제공 iOS 앱 중 일부를 제거할 수 있습니다. Intune를 사용하여 해당 앱을 다시 배포할 수는 없습니다. 사용자가 이러한 앱을 삭제하는 경우 앱 스토어로 이동해서 수동으로 다시 설치해야 합니다.

## <a name="step-1-specify-the-software-setup-file"></a>1단계: 소프트웨어 설치 파일 지정

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드에서 **관리** > **앱**을 차례로 선택합니다.
5. 앱 목록 위에서 **추가**를 선택합니다.
6. **앱 추가** 창에서 **기간 업무 앱**을 선택합니다.

## <a name="step-2-configure-the-app-package-file"></a>2단계: 앱 패키지 파일 구성

1. **앱 추가** 창에서 **앱 패키지 파일**을 선택합니다.
2. **앱 패키지 파일** 창에서 찾아보기 단추를 선택합니다. 그런 다음, 확장명이 **.ipa**인 iOS 설치 파일을 선택합니다.
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

> [!NOTE]
> iOS LOB 앱의 프로비전 프로필은 만료되기 30일 전에 만료 사실이 안내됩니다.

## <a name="step-5-update-a-line-of-business-app"></a>5단계: 기간 업무 앱 업데이트

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Intune 서비스에서 새 IPA 파일을 디바이스에 성공적으로 배포하려면 IPA 패키지의 Info.plist 파일에 있는 `CFBundleVersion` 문자열을 증분해야 합니다.

## <a name="next-steps"></a>다음 단계

- 만든 앱이 앱 목록에 나타납니다. 이제 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

- 앱의 속성 및 할당을 모니터링할 수 있는 방법에 대해 자세히 알아봅니다. [앱 정보 및 할당을 모니터링하는 방법](apps-monitor.md)을 참조하세요.

- Intune에서 앱의 컨텍스트에 대해 자세히 알아봅니다. [디바이스 및 앱 수명 주기에 대한 개요](introduction-device-app-lifecycles.md)를 참조하세요.
