---
title: Microsoft Intune - Azure에서 엔드포인트 보호 설정 구성 | Microsoft Docs
description: Microsoft Intune에서 macOS 또는 Windows 10 디바이스 프로필을 만들 경우 엔드포인트 보호 설정을 만듭니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1c7702c8079405664dd3fd34a9282531f88d7d0
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848911"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Intune에서 엔드포인트 보호 설정 추가

엔드포인트 보호를 사용하면 방화벽, bitlocker, 앱 허용 및 차단, Windows Defender 및 암호화 등을 포함하여 사용자 디바이스에서 다양한 보안 기능을 제어할 수 있습니다. 디바이스 프로필을 사용하여 Microsoft Intune에서 이러한 설정을 구성할 수 있습니다.

예를 들어 Mac 앱 스토어에서 macOS 사용자만 앱을 설치할 수 있는 엔드포인트 보호 프로필을 만들 수 있습니다. 또는 Windows 10 디바이스에서 앱을 실행하는 경우 Windows SmartScreen을 사용하도록 설정합니다.

이 문서는 프로필을 만드는 방법을 보여줍니다. 그런 다음, 사용 가능한 설정에 대한 자세한 내용은 디바이스 플랫폼을 선택합니다.

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>엔드포인트 보호 설정을 포함하는 디바이스 프로필 만들기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
4. 엔드포인트 보호 프로필의 **이름** 및 **설명**을 입력합니다.
5. **플랫폼** 드롭다운 목록에서 사용자 지정 설정을 적용할 디바이스 플랫폼을 선택합니다. 현재 디바이스 제한 설정에 대해 다음 플랫폼 중 하나를 선택할 수 있습니다.
   - **macOS**
   - **Windows 10 이상**
6. **프로필 유형** 드롭다운 목록에서 **Endpoint Protection**을 선택합니다. 
7. 선택한 플랫폼에 따라 구성할 수 있는 설정이 다릅니다. 각 플랫폼에 대한 자세한 설정을 보려면 다음 항목 중 하나로 이동하세요.
   - [macOS 설정](endpoint-protection-macos.md)
   - [Windows 10 설정](endpoint-protection-windows-10.md)
8. 완료되면 **프로필 만들기** 페이지로 돌아와서 **만들기**를 클릭합니다.

프로필이 만들어지고 프로필 목록 페이지에 표시됩니다. 이 프로필을 그룹에 할당하려면 [디바이스 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계
프로필을 그룹에 할당하려면 [디바이스 프로필 할당](device-profile-assign.md)을 참조하세요.
