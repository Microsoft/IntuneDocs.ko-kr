---
title: Microsoft Intune을 사용하여 macOS 디바이스에 Office 365 설치
titlesuffix: ''
description: Microsoft Intune을 사용하여 macOS 디바이스에 Office 365 앱을 설치하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4aa5cb24bc153839c6aac193f074128dd46a2e5f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185409"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Microsoft Intune을 사용하여 macOS 디바이스에 Office 365 할당

이 앱 유형을 사용하면 macOS 디바이스에 Office 365 2016 앱을 쉽게 할당할 수 있습니다. 이 앱 유형을 사용하면 Word, Excel, PowerPoint, Outlook 및 OneNote를 설치할 수 있습니다. 앱을 더 안전하게 최신 상태로 유지하기 위해 앱과 함께 MAU(Microsoft 자동 업데이트)가 제공됩니다. 원하는 앱이 Intune 콘솔의 앱 목록에 하나의 앱으로 표시됩니다.


## <a name="before-you-start"></a>시작하기 전에

macOS 디바이스에 Office 365를 추가하기 전에 다음 세부 정보를 파악합니다.

- 이 앱을 배포할 디바이스에서 macOS 10.10 이상을 실행하고 있어야 합니다.
- Intune은 Mac용 Office 2016 제품군에 포함된 Office 앱 추가만 지원합니다.
- Intune에서 앱 패키지를 설치할 때 Office 앱이 열리면 저장되지 않은 파일에서 사용자 데이터가 손실될 수 있습니다.

## <a name="create-and-configure-the-app-suite"></a>앱 패키지 만들기 및 구성

**앱** 창에서 Office 365를 추가합니다.
1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **모니터링 + 관리** > **Intune**을 선택합니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드 창의 **관리** 아래에서 **앱**을 선택합니다. 
5. **추가**를 선택합니다.
6. **앱 유형** 목록의 **Office 365 제품군** 그룹에서 **macOS**를 선택합니다.
7. 앱 제품군에 대한 정보를 가져오려면 **앱 제품군 정보**를 선택합니다.  
    이 정보를 사용하여 Intune에서 앱 제품군을 식별할 수 있으며, 사용자가 회사 포털에서 앱 제품군을 찾을 수도 있습니다.
8. 다음 정보를 입력합니다.
    - **제품군 이름**: 회사 포털에 표시되는 앱 제품군의 이름을 입력합니다. 사용하는 모든 제품군 이름이 고유한지 확인합니다. 같은 앱 패키지 이름이 두 번 나타나는 경우 앱 중 하나만 회사 포털에서 사용자에게 표시됩니다.
    - **제품군 설명**: 앱 제품군에 대한 설명을 입력합니다.
    - **게시자**: Microsoft가 게시자로 표시됩니다.
    - **범주**: 기본 제공 앱 범주 중 하나 이상이나 직접 만든 범주를 선택합니다. 이 설정을 통해 사용자가 회사 포털을 찾아볼 때 앱 패키지를 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 이 옵션을 선택하면 사용자가 앱을 찾을 때 회사 포털의 기본 페이지에 앱 제품군이 눈에 띄게 표시됩니다.
    - **정보 URL**: 선택적으로, 이 앱에 대한 정보가 포함된 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인 정보 URL**: 선택적으로, 이 앱에 대한 개인 정보 관련 정보가 포함된 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자**: Microsoft가 개발자로 표시됩니다.
    - **소유자**: Microsoft가 소유자로 표시됩니다.
    - **메모**: 선택 사항으로, 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고**: Office 365 로고는 사용자가 회사 포털을 찾을 때 앱과 함께 표시되는 로고입니다.
9. **확인**을 선택합니다.
10. **앱 추가** 창에서 **추가**를 선택합니다.  
    패키지가 앱 목록에 단일 항목으로 표시됩니다.

## <a name="configure-app-assignments"></a>앱 할당 구성

이 단계에서는 앱 패키지에 대한 할당을 구성합니다. 

1. 앱 목록에서 **Office 365** 앱 제품군을 선택하여 **Office 365** 개요 창을 표시합니다.
2. **Office 365** 창에서 **할당**을 선택합니다.
3. 앱 제품군을 사용할 그룹을 추가하려면 **그룹 추가**를 선택합니다.  
    **그룹 추가** 창이 표시됩니다.
4. **할당 유형**을 **필수** 또는 **사용 가능**으로 설정합니다.
5. 선택한 그룹에 제품군을 할당합니다. 자세한 내용은 [Microsoft Intune을 사용하여 그룹에 앱 할당](apps-deploy.md)을 참조하세요.

    >[!Note]
    > Intune를 통해 Office 365 앱 제품군을 제거할 수는 없습니다.

5. **할당** 창에서 **확인**을 선택합니다.
6. **그룹 추가** 창에서 **확인**을 선택합니다.
7. 할당을 커밋하려면 **저장**을 선택합니다.

## <a name="next-steps"></a>다음 단계

- Windows 10 디바이스에 Office 365 앱을 추가하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 Windows 10 디바이스에 Office 365 ProPlus 2016 앱 할당](apps-add-office365.md)을 참조하세요.
- 사용자 그룹에 앱 할당을 포함하고 제외하는 방법에 대한 자세한 내용은 [앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요.
