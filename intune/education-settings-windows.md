---
title: Microsoft Intune의 Windows 10 교육 설정 - Azure | Microsoft Docs
description: Windows 10 디바이스에 대한 모든 교육 설정 목록을 참조하세요. 테스트 실행 앱이 있는 디바이스 구성 프로필에서 이 설정을 사용하고, 사용자 또는 학생이 로그인하는 방법을 선택하고, 테스트 중에 화면을 모니터링하는 등의 작업을 Intune에서 수행할 수 있습니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 32c15037bad21ca90f81ed239ac24a9bac8d7499
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228326"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Intune을 사용하여 Windows 10 디바이스에서 테스트 실행 앱 구성

이 문서에서는 Windows 10 이상을 실행하는 디바이스에서 구성할 수 있는 모든 Microsoft Intune 교육 테스트 실행 앱을 보여줍니다. 이 앱을 사용하여 학생은 디바이스에 로그인하고 테스트를 받을 수 있습니다.

이러한 설정은 디바이스 구성 프로필에 추가된 후 Microsoft Intune을 사용하여 디바이스에 할당 또는 배포됩니다.

[Intune의 테스트 실행 앱](education-settings-configure.md)은 이 기능에 대한 자세한 정보를 제공합니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>테스트 설정 가져오기

- **계정 유형**: 사용자가 테스트에 로그인하는 방법을 선택합니다. 옵션은 다음과 같습니다.
  - Azure AD 계정
  - 도메인 계정
  - 로컬 계정
- **계정 사용자 이름**: 테스트 실행 앱에 사용되는 계정의 사용자 이름을 입력합니다. 다음 형식으로 계정을 입력할 수 있습니다.
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **평가 URL**: 사용자가 수행할 테스트의 URL을 입력합니다. URL을 가져오는 방법에 대한 자세한 내용은 [시험 응시 설명서](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)를 참조하세요.
- **화면 모니터링**: 사용자가 테스트를 수행하는 동안 화면 작업을 모니터링하도록 **허용**을 선택합니다. **구성되지 않음** 테스트 중에 화면을 모니터링하지 못하도록 합니다.
- **텍스트 제안**: 시험 응시자가 텍스트 제안을 볼 수 있도록 **허용**을 선택합니다. **구성되지 않음** 사용자가 테스트를 수행하는 동안 텍스트 제안을 차단합니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어졌지만 아직 아무것도 하지 않습니다. [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.
