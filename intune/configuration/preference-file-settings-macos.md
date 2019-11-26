---
title: Microsoft Intune에서 macOS 디바이스에 기본 설정 파일 설정 추가 - Azure | Microsoft Docs
titleSuffix: ''
description: 앱에 대 한 주요 정보를 포함 하는 xml 또는 info.plist 파일을 추가 합니다. 기본 설정 파일 장치 구성 프로필을 사용 하 여 속성 목록 파일에서 키 정보를 변경 하 고 macOS 장치에 할당 합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9acad2e8539da7210c349ffb254af62f370af5f6
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391500"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Microsoft Intune를 사용 하 여 macOS 장치에 속성 목록 파일 추가

Microsoft Intune를 사용 하 여 macOS 장치에 대 한 속성 목록 파일 (. info.plist) 또는 macOS 장치에 앱을 추가할 수 있습니다.

이 기능은 다음에 적용됩니다.

- 10.7 이상 버전을 실행 하는 macOS 장치

일반적으로 속성 목록 파일에는 macOS 응용 프로그램에 대 한 정보가 포함 됩니다. 자세한 내용은 [정보 속성 목록 파일](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) (Apple 웹 사이트) 및 [사용자 지정 페이로드 설정](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1)정보를 참조 하세요.

이 문서에서는 macOS 장치에 추가할 수 있는 다양 한 속성 목록 파일 설정을 나열 하 고 설명 합니다. MDM (모바일 장치 관리) 솔루션의 일부로 이러한 설정을 사용 하 여 앱 번들 ID (`com.company.application`)를 추가 하 고 info.plist 파일을 추가 합니다.

이러한 설정은 Intune에서 디바이스 구성 프로필에 추가된 다음, macOS 디바이스에 할당되거나 배포됩니다.

## <a name="before-you-begin"></a>시작하기 전에

[프로필을 만듭니다](device-profile-create.md).

## <a name="what-you-need-to-know"></a>기억해야 하는 사항

- 이러한 설정은 유효성이 검사 되지 않습니다. 장치에 프로필을 할당 하기 전에 변경 내용을 테스트 해야 합니다.
- 앱 키를 입력 하는 방법을 잘 모르겠으면 앱 내에서 설정을 변경 합니다. 그런 다음 [Xcode](https://developer.apple.com/xcode/) 를 사용 하 여 앱의 기본 설정 파일을 검토 하 여 설정이 어떻게 구성 되었는지 확인 합니다. Apple은 파일을 가져오기 전에 Xcode를 사용 하 여 관리할 관리 되지 않는 설정을 제거 하는 것이 좋습니다.
- 일부 앱은 관리 되는 기본 설정에서 작동 하며 모든 설정을 관리할 수 없습니다.
- 사용자 채널 설정이 아니라 장치 채널 설정을 대상으로 하는 속성 목록 파일을 업로드 해야 합니다. 속성 목록 파일은 전체 장치를 대상으로 합니다.

## <a name="preference-file"></a>기본 설정 파일

- **기본 설정 도메인 이름**: 속성 목록 파일은 일반적으로 웹 브라우저 (microsoft Edge), [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)및 사용자 지정 앱에 사용 됩니다. 기본 설정 도메인을 만들면 번들 ID도 만들어집니다. `com.company.application`와 같은 번들 ID를 입력 합니다. 예를 들어 `com.Contoso.applicationName`, `com.Microsoft.Edge` 또는 `com.microsoft.wdav`를 입력합니다.
- **속성 목록 파일**: 앱과 연결 된 속성 목록 파일을 선택 합니다. `.plist` 또는 `.xml` 파일 이어야 합니다. 예를 들어 `YourApp-Manifest.plist` 또는 `YourApp-Manifest.xml` 파일을 업로드 합니다.
- **파일 내용**: 속성 목록 파일의 키 정보가 표시 됩니다. 키 정보를 변경 해야 하는 경우에는 다른 편집기에서 목록 파일을 열고 Intune에서 해당 파일을 다시 업로드 합니다.

**확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.
