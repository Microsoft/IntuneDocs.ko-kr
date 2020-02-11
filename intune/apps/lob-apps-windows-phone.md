---
title: Microsoft Intune에 Windows Phone 기간 업무 앱 추가
titleSuffix: ''
description: Microsoft Intune을 사용하여 Windows Phone LOB(기간 업무) 앱을 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 328bafc2a55191c203263911ceaac9b520eb07f5
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755156"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>Microsoft Intune에 Windows Phone 기간 업무 앱 추가

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

이 문서의 정보를 사용하여 Microsoft Intune에 Windows Phone LOB(기간 업무) 앱을 추가할 수 있습니다. LOB 앱은 앱 설치 파일에서 Intune에 추가하는 앱입니다. 이러한 종류의 앱은 일반적으로 사내에서 작성됩니다. Intune이 사용자 디바이스에 LOB 앱을 설치합니다. 

## <a name="select-the-app-type"></a>앱 유형 선택

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **앱 유형 선택** 창의 **기타** 앱 유형에서 **LOB(기간 업무) 앱**을 선택합니다.
4. **선택**을 클릭합니다. **앱 추가** 단계가 표시됩니다.

## <a name="step-1---app-information"></a>1단계 - 앱 정보

### <a name="select-the-app-package-file"></a>앱 패키지 파일 선택

1. **앱 추가** 창에서 **앱 패키지 파일 선택**을 클릭합니다. 
2. **앱 패키지 파일** 창에서 찾아보기 단추를 선택합니다. 그런 다음 확장명이 **.xap**인 Windows Phone 설치 파일을 선택합니다.
   앱 세부 정보가 표시됩니다.
3. 완료되면 **앱 패키지 파일** 창에서 **확인**을 선택하여 앱을 추가합니다.

### <a name="set-app-information"></a>앱 정보 설정

1. **앱 정보** 페이지에서 앱의 세부 정보를 추가합니다. 선택한 앱에 따라 이 창의 일부 값이 자동으로 채워질 수 있습니다.
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
2. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.

## <a name="step-2---select-scope-tags-optional"></a>2단계 - 범위 태그 선택(선택 사항)
범위 태그를 사용하여 Intune에서 클라이언트 앱 정보를 볼 수 있는 사용자를 결정할 수 있습니다. 범위 태그에 대한 자세한 내용은 [분산형 IT에 역할 기반 액세스 제어 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.

1. **범위 태그 선택**을 클릭하여 앱의 범위 태그를 선택적으로 추가합니다. 
2. **다음**을 클릭하여 **할당** 페이지를 표시합니다.

## <a name="step-3---assignments"></a>3단계 - 할당

1. 앱에 대해 **필수**, **등록된 디바이스에 사용 가능** 또는 **제거** 그룹 할당을 선택합니다. 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](~/fundamentals/groups-add.md) 및 [Microsoft Intune을 사용하여 그룹에 앱 할당](apps-deploy.md)을 참조하세요.
2. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다. 

## <a name="step-4---review--create"></a>4단계 - 검토 + 만들기

1. 앱에 대해 입력한 값과 설정을 검토합니다.
2. 완료되면 **만들기**를 클릭하여 Intune에 앱을 추가합니다.

    LOB(기간 업무) 앱의 **개요** 블레이드가 표시됩니다.

이제 만든 앱이 앱 목록에 나타납니다. 목록에서 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

- 만든 앱이 앱 목록에 나타납니다. 이제 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

- 앱의 속성 및 할당을 모니터링할 수 있는 방법에 대해 자세히 알아봅니다. [앱 정보 및 할당을 모니터링하는 방법](apps-monitor.md)을 참조하세요.

- Intune에서 앱의 컨텍스트에 대해 자세히 알아봅니다. [디바이스 및 앱 수명 주기에 대한 개요](../fundamentals/device-lifecycle.md)를 참조하세요.
