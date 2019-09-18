---
title: Microsoft Intune의 Windows 10 교육 설정 - Azure | Microsoft Docs
description: Windows 10 디바이스에 대한 모든 교육 설정 목록을 참조하세요. 테스트 실행 앱이 있는 디바이스 구성 프로필에서 이 설정을 사용하고, 사용자 또는 학생이 로그인하는 방법을 선택하고, 테스트 중에 화면을 모니터링하는 등의 작업을 Intune에서 수행할 수 있습니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07d3488d509339fc48eb8449b12725b757775eb5
ms.sourcegitcommit: 98f2597eec28c6096985d5a1acae72430c2afb1a
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877979"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Intune을 사용하여 Windows 10 디바이스에서 테스트 실행 앱 구성

테스트 하기 앱을 사용 하 여 교실의 Windows 10 장치에서 온라인 테스트를 안전 하 게 관리할 수 있습니다. 테스트 수행 앱을 설정 하려면 Intune에서 장치 구성 프로필을 만들고 보안 평가 설정을 구성 해야 합니다. 이 문서에서는 테스트 수행 앱에 대해 찾을 수 있는 설정을 설명 합니다. 

프로필을 구성한 후 학생에 게 할당 하 고 배포 합니다. 

[Intune의 테스트 실행 앱](education-settings-configure.md)은 이 기능에 대한 자세한 정보를 제공합니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>테스트 설정 가져오기
장치 구성 프로필을 만든 후 **프로필 유형** 으로 이동 하 여 **보안 평가 (교육)** 를 선택 합니다. 다음은 테스트 앱 설정 사용을 확인할 수 있습니다. 


- **계정 형식**: 사용자가 테스트에 로그인하는 방법을 선택합니다. 옵션은 다음과 같습니다.
  - Azure AD 계정
  - 도메인 계정
  - 로컬 계정
  - 로컬 게스트 계정: Windows 10 버전 1903 이상을 실행 하는 장치 에서만 사용할 수 있습니다.    
- **계정 사용자 이름**: Take a Test 앱에 사용되는 계정의 사용자 이름을 입력합니다. 다음 형식으로 계정을 입력할 수 있습니다.
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **계정 이름**: 로컬 게스트 계정 유형을 설정 하려면 테스트 수행 앱에 사용 되는 계정의 이름을 입력 합니다. 계정 이름은 로그인 화면에 타일로 표시 됩니다. 학생 들이 타일을 클릭 하 여 테스트를 시작 합니다.  
- **평가 URL**: 사용자가 수행할 테스트의 URL을 입력합니다. URL을 가져오는 방법에 대한 자세한 내용은 [시험 응시 설명서](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)를 참조하세요.
- **프린터 연결**: 프린터에 연결 된 장치 에서만 테스트 앱 사용에 대 한 액세스를 허용 하려면 **필요** 를 선택 합니다. 이 설정은 푸는 사람은에서 앱의 인쇄 단추를 사용할 수 있도록 합니다. **구성 되지 않음** 학생은 프린터에 연결 되지 않은 장치에서 앱에 액세스할 수 있습니다.  
- **화면 모니터링**: 사용자가 테스트를 수행하는 동안 화면 작업을 모니터링하도록 **허용**을 선택합니다. **구성되지 않음** 테스트 중에 화면을 모니터링하지 못하도록 합니다.
- **텍스트 제안**: 시험 응시자가 텍스트 제안을 볼 수 있도록 **허용**을 선택합니다. **구성되지 않음** 사용자가 테스트를 수행하는 동안 텍스트 제안을 차단합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.
