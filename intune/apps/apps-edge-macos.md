---
title: Microsoft Intune을 사용하여 macOS 디바이스에 Microsoft Edge 추가
titleSuffix: ''
description: Microsoft Intune을 사용하여 macOS 디바이스에 Microsoft Edge를 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c31dd652022ae0d394ab2229a0c25b362ad8574d
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563577"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Microsoft Intune을 사용하여 macOS 디바이스에 Microsoft Edge 추가

앱을 배포, 구성, 모니터링 또는 보호하려면 앱을 Intune에 추가해야 합니다. 사용 가능한 [앱 유형](~/apps/apps-add.md#app-types-in-microsoft-intune) 중 하나는 Microsoft Edge ‘버전 77 이상’입니다.  Intune에서 이 앱 유형을 선택하면 macOS를 실행하고 직접 관리하는 디바이스에 Microsoft Edge ‘버전 77 이상’을 할당하고 설치할 수 있습니다.  이 앱 유형을 사용하면 macOS 앱 래핑 도구를 사용하지 않고도 macOS 디바이스에 Microsoft Edge를 쉽게 할당할 수 있습니다. 앱을 더 안전하게 최신 상태로 유지하기 위해 앱과 함께 MAU(Microsoft 자동 업데이트)가 제공됩니다.

> [!IMPORTANT]
> 이 앱 유형은 **공개 미리 보기**로 제공되며 macOS용 개발자 및 베타 채널을 제공합니다. 배포는 영어(EN)로만 가능하지만 최종 사용자가 브라우저의 **설정** > **언어**에서 표시 언어를 변경할 수 있습니다. 

> [!NOTE]
> Microsoft Edge ‘버전 77 이상’은 Windows 10에서도 사용할 수 있습니다. 

## <a name="prerequisites"></a>전제 조건
- Microsoft Edge를 설치하기 전에 macOS 디바이스에서 macOS 10.12 이상을 실행하고 있어야 합니다.

## <a name="add-microsoft-edge-to-intune"></a>Intune에 Microsoft Edge 추가
다음 단계를 사용하여 Microsoft Edge 버전 77 이상을 Intune에 추가할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **Microsoft Edge 버전 77 이상** 아래 **앱 유형**에서 **macOS**를 선택합니다.

## <a name="configure-app-information"></a>앱 정보 구성
이 단계에서는 이 앱 배포에 대한 정보를 제공합니다. 이 정보를 통해 Intune에서 앱을 식별하며 사용자가 회사 포털에서 앱을 찾을 수 있습니다.

1. **앱 정보**를 클릭하여 **앱 정보** 창을 표시합니다.
2. **앱 정보** 창에서 이 앱 배포에 대한 정보를 제공합니다. 이 정보를 통해 Intune에서 앱을 식별하며 사용자가 회사 포털에서 앱을 찾을 수 있습니다.
    - **이름**: 회사 포털에 표시되는 앱의 이름을 입력합니다. 모든 이름이 고유한지 확인합니다. 동일한 앱 이름을 두 번 사용하는 경우에는 회사 포털에서 앱 중 하나만 사용자에게 표시됩니다.
    - **설명**: 앱에 대한 설명을 입력합니다. 예를 들어 설명에 대상 사용자를 나열할 수 있습니다.
    - **게시자**: Microsoft가 게시자로 표시됩니다.
    - **범주**: 필요한 경우, 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이 설정을 통해 사용자가 회사 포털을 찾아볼 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱을 눈에 띄게 표시하려면 이 옵션을 선택합니다.
    - **정보 URL**: 필요에 따라 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 이 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자**: Microsoft가 개발자로 표시됩니다.
    - **소유자**: Microsoft가 소유자로 표시됩니다.
    - **메모**: 선택 사항으로, 이 앱과 연결할 모든 메모를 입력합니다.
3. **확인**을 선택합니다.

## <a name="configure-microsoft-edge-settings"></a>Microsoft Edge 설정 구성
이 단계에서는 앱에 대한 설치 옵션을 구성합니다.

1. **앱 추가** 창에서 **앱 설정**을 선택합니다.
2. **앱 설정** 창에서 **베타** 채널이 자동으로 선택되며 변경할 수 없습니다.
    - **베타** 채널은 가장 안정적인 Microsoft Edge 미리 보기 환경이며 조직 내에서 전체 파일럿에 대한 가장 적합한 선택입니다. 6주마다 주요 업데이트를 포함합니다.

    > [!NOTE]
    > 사용자가 회사 포털을 찾아볼 때 Microsoft Edge 브라우저 로고가 앱과 함께 표시됩니다.
3.  **확인**을 선택합니다.

## <a name="select-scope-tags-optional"></a>범위 태그 선택(선택 사항)
범위 태그를 사용하여 Intune에서 클라이언트 앱 정보를 볼 수 있는 사용자를 결정할 수 있습니다. 범위 태그에 대한 자세한 내용은 분산형 IT에 역할 기반 액세스 제어 및 범위 태그 사용을 참조하세요.
1.  **범위(태그)**  > **추가**를 선택합니다.
2.  **선택** 상자를 사용하여 범위 태그를 검색합니다.
3.  이 앱에 할당하려는 범위 태그 옆의 확인란을 선택합니다.
4.  **선택** > **확인**을 클릭합니다.

## <a name="add-the-app"></a>앱 추가
구성을 완료한 후 **App 앱** 창에서 **추가**를 선택합니다. 

만든 앱이 앱 목록에 표시되며, 여기서 이 앱을 선택한 그룹에 할당할 수 있습니다. 

> [!NOTE]
> 현재, Apple은 Intune이 macOS 디바이스에서 Microsoft Edge를 제거하는 방법을 제공하지 않습니다.

## <a name="next-steps"></a>다음 단계
- macOS 디바이스에서 Microsoft Edge를 구성하는 방법에 대한 자세한 내용은 [macOS 디바이스에서 Microsoft Edge 구성](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac)을 참조하세요.
- 사용자 그룹에 앱 할당을 포함하고 제외하는 방법에 대한 자세한 내용은 [앱 할당 포함 및 제외](~/apps/apps-inc-exl-assignments.md)를 참조하세요.
- [그룹에 앱 할당](~/apps/apps-deploy.md)

