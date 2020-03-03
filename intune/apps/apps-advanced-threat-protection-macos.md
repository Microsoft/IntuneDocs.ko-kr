---
title: Microsoft Intune을 사용하여 macOS 디바이스에 Microsoft Defender ATP 추가
titleSuffix: ''
description: Microsoft Intune을 사용하여 macOS 디바이스에 Microsoft Defender ATP를 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
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
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569562"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>Microsoft Intune을 사용하여 macOS 디바이스에 Microsoft Defender ATP 추가

앱을 배포, 구성, 모니터링 또는 보호하려면 앱을 Intune에 추가해야 합니다. 사용할 수 있는 [앱 유형](~/apps/apps-add.md#app-types-in-microsoft-intune) 중 하나는 Microsoft Defender ATP(Advanced Threat Protection)입니다. Intune에서 이 앱 유형을 선택하면 macOS를 실행하고 직접 관리하는 디바이스에 Microsoft Defender ATP를 할당하고 설치할 수 있습니다. 이 앱 유형을 사용하면 macOS 앱 래핑 도구를 사용하지 않고도 macOS 디바이스에 Microsoft Defender ATP를 쉽게 할당할 수 있습니다. 앱을 더 안전하게 최신 상태로 유지하기 위해 앱과 함께 MAU(Microsoft 자동 업데이트)가 제공됩니다.

## <a name="prerequisites"></a>전제 조건
- macOS 디바이스는 macOS 10.13 이상을 실행해야 합니다.
- macOS 디바이스에는 650MB 이상의 디스크 공간이 있어야 합니다.
- Intune에서 커널 확장을 배포합니다. 자세한 내용은 [Intune에서 macOS 커널 확장 추가](~/configuration/kernel-extensions-overview-macos.md)를 참조하세요.

> [!IMPORTANT]
> 커널 확장은 Microsoft Defender ATP 앱이 설치되기 전에 디바이스에 있는 경우에만 자동으로 승인될 수 있습니다. 또는 Mac의 경우 사용자에게 “시스템 확장이 차단되었습니다.” 메시지가 표시되고 **보안 기본 설정** 또는 **시스템 기본 설정** > **보안 및 개인 정보**로 이동한 다음, **허용**을 선택하여 확장을 승인해야 합니다. 자세한 내용은 [Mac용 Microsoft Defender ATP의 커널 확장 문제 해결](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext)을 참조하세요.

## <a name="add-microsoft-defender-atp-to-intune"></a>Intune에 Microsoft Defender ATP 추가
다음 단계를 사용하여 Intune에 Microsoft Defender ATP를 추가할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **Microsoft Defender ATP** 아래 **앱 유형** 목록에서 **macOS**를 선택합니다.

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
> 현재, Apple은 Intune이 macOS 디바이스에서 Microsoft Defender ATP를 제거하는 방법을 제공하지 않습니다.

## <a name="next-steps"></a>다음 단계
- macOS 디바이스에서 Microsoft Defender ATP를 구성하는 방법에 대한 자세한 내용은 [macOS 디바이스에서 Microsoft Defender ATP 구성](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences)을 참조하세요.
- 사용자 그룹에 앱 할당을 포함하고 제외하는 방법에 대한 자세한 내용은 [앱 할당 포함 및 제외](~/apps/apps-inc-exl-assignments.md)를 참조하세요.
- [그룹에 앱 할당](~/apps/apps-deploy.md)

