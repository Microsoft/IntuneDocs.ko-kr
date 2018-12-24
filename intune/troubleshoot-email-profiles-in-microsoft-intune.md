---
title: Microsoft Intune의 이메일 프로필 문제 해결 - Azure | Microsoft Docs
description: 전자 메일 프로필 문제와 이 문제를 해결하는 방법입니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 480b453aa4f08f8d2a2460e26bfdb5f05466df6e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190101"
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Microsoft Intune에서 전자 메일 프로필 문제 해결

몇 가지 일반적인 이메일 프로필 문제와 이 문제를 해결하는 방법을 검토합니다.

이 정보가 도움이 되지 않으면 [Microsoft Intune에 대한 지원을 받을](get-support.md) 수도 있습니다.

## <a name="unable-to-send-images-from--email-account"></a>전자 메일 계정에서 이미지를 보낼 수 없습니다.
Azure 클래식 포털의 Intune에 적용됩니다.

자동으로 구성된 전자 메일 계정의 사용자는 자신의 디바이스에서 그림이나 이미지를 보낼 수 없습니다. 이 시나리오는 **타사 애플리케이션에서 이메일을 보내도록 허용** 옵션이 활성화되지 않은 경우에 발생할 수 있습니다.

### <a name="intune-solution"></a>Intune 솔루션

1. Microsoft Intune 관리 콘솔을 열고 **정책** 워크로드 > **구성 정책**을 선택합니다.

2. 메일 프로필을 선택하고 **편집**을 선택합니다.

3. **Allow e-mail to be sent from third-party applications**(타사 응용 프로그램에서 전자 메일을 보내도록 허용)을 선택합니다.

### <a name="configuration-manager-integrated-with-intune-solution"></a>Intune 솔루션과 통합된 Configuration Manager

1. Configuration Manager 콘솔 > **자산 및 호환성**을 엽니다.

2. **개요** > **호환성 설정** > **회사 리소스 액세스**를 확장하고 **이메일 프로필**을 선택합니다.

3. 전자 메일 프로필을 마우스 오른쪽 단추로 클릭하고 **속성**을 엽니다.

4. **동기화 설정** 탭에서 **타사 응용 프로그램에서 전자 메일을 보내도록 허용**을 선택합니다.

## <a name="device-already-has-an-email-profile-installed"></a>디바이스에 메일 프로필이 이미 설치되어 있음

Intune 프로필을 프로비저닝하기 전에 사용자가 이메일 프로필을 설치한 경우 Intune 이메일 프로필 배포 결과는 디바이스 플랫폼에 따라 달라집니다.

- **iOS**: Intune에서는 호스트 이름 및 메일 주소를 기반으로 기존에 중복된 메일 프로필을 검색합니다. 사용자가 만든 중복 전자 메일 프로필에서는 Intune 관리자가 만든 프로필 배포가 차단됩니다. iOS 사용자는 일반적으로 이메일 프로필을 만든 후에 등록을 하므로 이것은 일반적인 문제입니다. 회사 포털에서는 수동으로 구성된 이메일 프로필로 인해 준수되지 않는 사용자를 업데이트하고 사용자에게 해당 프로필을 제거하라는 메시지를 표시합니다. 사용자는 Intune 프로필을 배포할 수 있도록 이메일 프로필을 제거해야 합니다. 이 문제를 방지하려면 사용자에게 등록하도록 지시하고 Intune에서 프로필을 배포하도록 허용합니다. 그런 다음, 사용자가 만든 이메일 프로필을 설치합니다.

- **Windows**: Intune에서는 호스트 이름 및 메일 주소를 기반으로 기존에 중복된 메일 프로필을 검색합니다. Intune은 사용자가 만든 기존 전자 메일 프로필을 덮어씁니다.

- **Samsung KNOX Standard**: Intune에서는 이메일 주소를 기반으로 중복된 이메일 계정을 식별하고 Intune 프로필로 덮어씁니다. 사용자가 해당 계정을 구성하는 경우 Intune 프로필에 의해 다시 덮어쓰게 됩니다. 이로 인해 계정 구성을 덮어쓰는 사용자에게 혼동이 발생할 수 있습니다.

삼성 KNOX는 호스트 이름을 사용하여 프로필을 식별하지 않습니다. 서로 다른 호스트의 동일한 이메일 주소로 배포할 여러 이메일 프로필을 만들지 말고 서로 덮어쓰는 것이 좋습니다.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>KNOX Standard 디바이스에 대한 오류 0x87D1FDE8
**문제**: 다양한 Android 디바이스에 대한 삼성 KNOX Standard용 Exchange Active Sync 이메일 프로필을 만들고 배포한 후 디바이스의 속성 > 정책 탭에 **0x87D1FDE8** 또는 **조정 실패**라는 오류가 보고됩니다.

삼성 KNOX 및 소스 정책에 대한 EAS 프로필 구성을 확인하세요. Samsung KNOX 동기화 옵션은 더 이상 지원되지 않으며, 해당 옵션은 프로필에서 선택하면 안 됩니다. 디바이스가 최대 24시간까지 정책을 처리하기에 충분한 시간을 갖도록 합니다.

## <a name="next-steps"></a>다음 단계
이 정보가 도움이 되지 않으면 [Microsoft Intune에 대한 지원을 받을](get-support.md) 수도 있습니다.