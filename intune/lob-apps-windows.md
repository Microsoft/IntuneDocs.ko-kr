---
title: Microsoft Intune에 Windows 기간 업무 앱 추가
titleSuffix: ''
description: Microsoft Intune을 사용하여 Windows LOB(기간 업무) 앱을 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca41e12136911cc0aecb6968a949fb738e2e2d77
ms.sourcegitcommit: d1116c70bd0f2382d590091e0e66095de3925324
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59570769"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Microsoft Intune에 Windows 기간 업무 앱 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

LOB(기간 업무) 앱은 앱 설치 파일로 추가합니다. 이러한 종류의 앱은 일반적으로 사내에서 작성됩니다. 다음 단계는 Windows LOB 앱을 Microsoft Intune에 추가할 수 있도록 지침을 제공합니다.

## <a name="step-1-specify-the-software-setup-file"></a>1단계: 소프트웨어 설치 파일 지정

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드에서 **관리** > **앱**을 차례로 선택합니다.
5. 앱 목록 위에서 **추가**를 선택합니다.
6. **앱 추가** 창에서 **기간 업무 앱**을 선택합니다.

## <a name="step-2-configure-the-app-package-file"></a>2단계: 앱 패키지 파일 구성

1. **앱 추가** 창에서 **앱 패키지 파일**을 선택합니다.
2. **앱 패키지 파일** 창에서 찾아보기 단추를 선택합니다. 그런 다음, 확장명이 **.msi**, **.appx** 또는 **.appxbundle**인 Windows 설치 파일을 선택합니다.

    > [!NOTE]
    > Windows 앱의 파일 확장명에는 **.msi**, **.appx**, **.appxbundle**, **.msix** 및 **.msixbundle**이 포함됩니다.  

1. 작업을 마쳤으면 **확인**을 선택합니다.


## <a name="step-3-configure-app-information"></a>3단계: 앱 정보 구성

1. **앱 추가** 창에서 **앱 정보**를 선택합니다.
2. **앱 정보** 창에서 다음 정보를 구성합니다. 이 창의 일부 값은 자동으로 채워질 수 있습니다.
    - **이름**: 회사 포털에 표시되는 앱 이름을 입력합니다. 사용하는 모든 앱 이름이 고유한지 확인합니다. 동일한 앱 이름을 두 번 사용하는 경우 앱 중 하나만 회사 포털에 표시됩니다.
    - **설명**: 앱에 대한 설명을 입력합니다. 설명은 회사 포털에 표시됩니다.
    - **게시자**: 앱 게시자의 이름을 입력합니다.
    - **앱 버전 무시**: 앱 개발자가 앱을 자동으로 업데이트하는 경우 **예**로 설정합니다. 이 옵션은 모바일 .msi 앱에만 적용됩니다.
    - **범주**: 기본 제공 앱 범주를 하나 이상 선택하거나 직접 만든 범주를 선택합니다. 범주를 사용하면 사용자가 회사 포털을 탐색할 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱을 쉽게 확인할 수 있도록 표시합니다.
    - **정보 URL**: 필요에 따라 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에 표시됩니다.
    - **명령줄 인수**: 선택적으로, 실행 시 .msi 파일에 적용할 명령줄 인수를 입력합니다. 예를 들어 **/q** 등을 입력합니다.
    - **개발자**: 선택적으로, 앱 개발자의 이름을 입력합니다.
    - **소유자**: 선택적으로, 이 앱의 소유자 이름을 입력합니다. 예를 들어 **HR 부서** 등을 입력합니다.
    - **메모**: 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고**: 앱과 연결된 아이콘을 업로드합니다. 사용자가 회사 포털을 탐색할 때 이 아이콘이 앱과 함께 표시됩니다.
3. 작업을 마쳤으면 **확인**을 선택합니다.

## <a name="step-4-finish-up"></a>4단계: 끝내기

1. **앱 추가** 창에서 앱 정보를 올바르게 구성했는지 확인합니다.
2. **추가**를 선택하여 Intune에 앱을 업로드합니다.

## <a name="step-5-update-a-line-of-business-app"></a>5단계: 기간 업무 앱 업데이트

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>버전 확인 프로세스를 무시하도록 자체 업데이트 모바일 MSI 앱 구성

버전 확인 프로세스를 무시하도록 알려진 자체 업데이트 모바일 MSI 앱을 구성할 수 있습니다. 

MSI 설치 관리자 기반의 일부 앱은 앱 개발자가 자동으로 업데이트합니다. 자동으로 업데이트되는 이러한 MSI 앱의 경우 **앱 정보** 창에서 **앱 버전 무시** 설정을 구성할 수 있습니다. 이 설정을 **예**로 전환하면 Microsoft Intune에서 Windows 클라이언트에 설치된 앱 버전을 적용하지 않습니다. 

이 기능은 경합 상태를 방지하는 데 유용합니다. 예를 들어 앱 개발자가 앱을 자동으로 업데이트하는데 Intune에서 앱을 업데이트할 경우 경합 상태가 발생할 수 있습니다. 둘 다 Windows 클라이언트에서 앱 버전을 적용하려 시도할 수 있으며, 이로 인해 충돌이 발생합니다.

## <a name="next-steps"></a>다음 단계

- 만든 앱이 앱 목록에 나타납니다. 이제 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

- 앱의 속성 및 할당을 모니터링할 수 있는 방법에 대해 자세히 알아봅니다. [앱 정보 및 할당을 모니터링하는 방법](apps-monitor.md)을 참조하세요.

- Intune에서 앱의 컨텍스트에 대해 자세히 알아봅니다. [Microsoft Intune에 대한 앱 수명 주기 개요](app-lifecycle.md)를 참조하세요.
