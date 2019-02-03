---
title: Microsoft Intune에서 교육 설정 추가 또는 구성 - Azure | Microsoft Docs
description: Microsoft Intune의 Windows 10 이상 디바이스에 있는 디바이스 구성 프로필에서 테스트 실행 앱을 사용합니다. 교육 설정을 사용하여 구성 프로필을 만들고, 테스트 앱 URL을 입력하고, 어떻게 사용자 로그인하는 방법을 선택하고, 테스트 중에 화면을 모니터링하고, 테스트 중에 텍스트 제안을 허용 또는 방지합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 1e49e1673e0bebdcdafb8ad7792051c76b80f696
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831465"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune의 Windows 10 디바이스에서 테스트 실행 앱 사용

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune의 교육 프로필은 학생이 디바이스에서 시험에 응시할 수 있도록 설계되었습니다. 이 기능에는 **테스트 실행** 앱과 테스트 URL을 추가하는 설정, 최종 사용자가 테스트에 로그인하는 방법 등이 포함됩니다. 이 기능은 다음 플랫폼을 지원합니다.

- Windows 10 이상

사용자가 로그인하면 테스트 실행 앱이 사용자가 입력한 테스트가 함께 자동으로 열립니다. 테스트가 진행되는 동안에는 다른 앱을 디바이스에서 실행할 수 없습니다. [Windows 10에서 테스트 수행](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)에서는 테스트 실행 앱에 대한 자세한 정보를 제공합니다.

이 문서에서는 Microsoft Intune에서 디바이스 구성 프로필을 만드는 단계가 나열되어 있습니다. Windows 10 디바이스에 사용할 수 있는 교육에 대해 읽고 배울 수 있는 정보도 포함되어 있습니다.

## <a name="create-a-device-profile"></a>디바이스 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고, **Intune**을 기준으로 필터링한 다음, **Microsoft Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필**: **교육 프로필**을 선택합니다.

4. 구성할 설정을 입력합니다.

    - [Windows 10 이상](education-settings-windows.md)

5. **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

설정을 입력하고 프로필을 만들면 프로필 목록에 프로필이 표시됩니다. 그런 다음, [이 프로필을 그룹에 할당](device-profile-assign.md)합니다.

## <a name="next-steps"></a>다음 단계

[Windows 10 교육 설정](education-settings-windows.md) 및 해당 설명을 참조하세요.

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.