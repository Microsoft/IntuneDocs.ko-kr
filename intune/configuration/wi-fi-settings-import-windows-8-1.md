---
title: Microsoft Intune에서 Windows 디바이스에 대한 Wi-Fi 설정 가져오기 - Azure | Microsoft Docs
description: netsh wlan을 사용하여 Windows 디바이스에서 Wi-Fi 설정을 XML 파일로 내보냅니다. 그런 다음, Intune에서 이 파일을 가져와 Windows 8.1, Windows 10 및 Windows Holographic for Business를 실행하는 디바이스에 대한 Wi-Fi 프로필을 만듭니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207012"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Intune에서 Windows 디바이스에 대한 Wi-Fi 설정 가져오기

Windows를 실행하는 디바이스의 경우 이전에 파일로 내보낸 Wi-Fi 구성 프로필을 가져올 수도 있습니다. **Windows 10 이상 디바이스의 경우 Intune에서 직접 [Wi-Fi 프로필을 만들](wi-fi-settings-windows.md) 수도 있습니다**.

적용 대상:  
- Windows 8.1 이상
- Windows 10 이상
- Windows 10 데스크톱 또는 모바일
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Windows 디바이스에서 Wi-Fi 설정 내보내기

Windows에서 `netsh wlan`을 사용하여 기존 Wi-Fi 프로필을 Intune에서 읽을 수 있는 XML 파일로 내보냅니다. 프로필을 사용하기 위해 일반 텍스트로 키를 내보내야 합니다.

필수 WiFi 프로필이 이미 설치되어 있는 Windows 컴퓨터에서 다음 단계를 사용합니다.

1. 내보낸 Wi-Fi 프로필에 대한 로컬 폴더를 만듭니다(예: **c:\WiFi**).
2. 관리자 권한으로 명령 프롬프트를 엽니다.
3. `netsh wlan show profiles` 명령을 실행합니다. 내보내려는 프로필의 이름을 적어둡니다. 이 예제에서 프로필 이름은 **WiFiName**입니다.
4. `netsh wlan export profile name="ProfileName" folder=c:\Wifi` 명령을 실행합니다. 이 명령은 **Wi-Fi-WiFiName.xml**이라는 Wi-Fi 프로필 파일을 대상 폴더에 만듭니다.

## <a name="import-the-wi-fi-settings-into-intune"></a>Intune으로 Wi-Fi 설정 가져오기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 이름은 Wi-Fi 프로필 xml의 이름 속성과 동일**해야** 합니다. 그렇지 않으면 실패합니다.
    - **설명**: 설정에 대한 개요와 기타 중요한 모든 세부 정보를 제공하는 설명을 입력합니다.
    - **플랫폼**: **Windows 8.1 이상**을 선택합니다.
    - **프로필 유형**: **Wi-Fi 가져오기**를 선택합니다.

    > [!IMPORTANT]
    > - 미리 공유한 키를 포함하는 Wi-Fi 프로필을 내보내는 경우 명령에 `key=clear`를 추가**해야** 합니다. 예를 들어 다음과 같이 입력합니다. `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - Windows 10에서 미리 공유한 키를 사용하면 Intune에서 나타나는 업데이트 관리 오류가 발생합니다. 이런 경우 Wi-Fi 프로필은 디바이스에 제대로 할당되고 프로필은 예상대로 작동합니다.
    > - 미리 공유한 키를 포함하는 Wi-Fi 프로필을 내보내는 경우 파일이 보호되도록 합니다. 키가 일반 텍스트인 경우 키를 보호하는 것은 사용자의 책임입니다.

4. 다음 설정을 입력합니다.

    - **연결 이름**: Wi-Fi 연결의 이름을 입력합니다. 이 이름은 사용자가 사용 가능한 Wi-fi 네트워크를 찾아볼 때 표시 됩니다.
    - **프로필 XML**: 찾아보기 단추를 선택하고 가져오려는 Wi-Fi 프로필 설정이 포함된 XML 파일을 선택합니다.
    - **파일 내용**: 선택한 구성 프로필에 대한 XML 코드를 표시합니다.

5. **확인**을 선택하여 변경 내용을 저장합니다.
6. 완료되면 **확인** > **만들기**를 선택하여 Intune 프로필을 만듭니다. 완료되면 프로필이 **디바이스 - 구성 프로필** 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아무것도 하지 않습니다. 다음으로, [프로필을 할당](../device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

사용 가능한 다른 플랫폼을 포함한 [Wi-Fi 설정 개요](wi-fi-settings-configure.md)를 참조하세요.
