---
title: macOS에 대한 Microsoft Intune 장치 제한 설정
titlesuffix: ''
description: macOS를 실행하는 장치에서 장치 설정 및 기능을 제어하는 데 사용할 수 있는 Intune 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 51b1df246c23f2e1571b3bccc3f4f26ae91e26dd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52178355"
---
# <a name="microsoft-intune-macos-device-restriction-settings"></a>Microsoft Intune macOS 장치 제한 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 macOS를 실행하는 장치에 대해 구성할 수 있는 Microsoft Intune 장치 제한 설정을 보여줍니다.

## <a name="password"></a>암호
-   **암호** - 최종 사용자에게 장치에 액세스하려면 암호를 입력하도록 요구합니다.
    -   **필수 암호 유형** - 암호를 숫자만으로 구성할 수 있는지 아니면 영숫자(문자와 숫자 포함)로 구성해야 하는지 지정합니다. 이 설정은 Mac OS X 버전 10.10.3 이상에서만 지원됩니다.
    -   **암호에 포함해야 하는 영숫자가 아닌 문자 수** - 암호에 필요한 복잡한 문자 수(**0**~**4**)를 지정합니다.<br>복합 문자는 "**?**" 등의 기호입니다.
    -   **최소 암호 길이** - 사용자가 구성해야 하는 암호의 최소 길이(**4**~**16**자)를 입력합니다.
    -   **단순 암호** - **0000** 또는 **1234**와 같은 단순 암호 사용을 허용합니다.
    -   **화면 잠금 후 암호를 요구하기 전까지 최대 시간(분)** - 컴퓨터 잠금을 해제하려면 암호를 입력해야 할 때까지 컴퓨터가 비활성 상태로 유지되는 시간을 지정합니다.
    -   **화면이 잠기기 전까지 최대 비활성 시간(분)** - 화면이 잠기기 전까지 컴퓨터를 유휴 상태로 유지해야 하는 기간을 지정합니다.
    -   **암호 만료(일)** - 사용자가 암호를 변경해야 할 때까지의 기간을 **1**~**255**일 사이로 지정합니다.
    -   **이전 암호 다시 사용 안 함** - 이전에 사용했으며 다시 사용할 수 없는 암호의 수를 **1**~**24**개 사이로 지정합니다.

## <a name="restricted-apps"></a>제한된 앱

제한된 앱 목록에서 다음 목록 중 하나를 구성할 수 있습니다.

- **금지된 앱** 목록 - 사용자가 설치하거나 실행할 수 없고 Intune에서 관리되지 않는 앱을 나열합니다. 사용자는 금지된 앱을 설치할 수 있지만, 그렇게 하는 경우 해당 사용자에게 이를 보고합니다.
- **승인된 앱** 목록 - 사용자가 설치할 수 있는 앱을 나열합니다. 사용자는 나열되지 않은 앱을 설치하지 않아야 합니다. Intune에서 관리되는 앱은 자동으로 허용됩니다. 사용자가 승인 목록에 없는 앱을 설치할 수 있지만 설치하는 경우 관리자에게 보고됩니다.

목록을 구성하려면 **추가**를 클릭한 다음 선택한 이름, 앱 게시자(선택 사항) 및 앱의 번들 ID를 지정합니다(예: *com.apple.calculator*).

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>표시되지 않은 전자 메일 도메인

**전자 메일 도메인 URL** 필드에서 하나 이상의 URL을 목록에 추가합니다. 사용자가 구성한 도메인이 아닌 다른 도메인에서 받은 이메일은 MacOS 메일 앱에서 신뢰할 수 없는 이메일로 표시됩니다.

