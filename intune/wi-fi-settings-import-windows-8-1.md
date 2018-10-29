---
title: Microsoft Intune에서 Windows 장치에 대한 Wi-Fi 설정 가져오기 - Azure | Microsoft Docs
description: netsh wlan을 사용하여 Windows 장치에서 Wi-Fi 설정을 XML 파일로 내보냅니다. 그런 다음, Intune에서 이 파일을 가져와 Windows 8.1, Windows 10 및 Windows Holographic for Business를 실행하는 장치에 대한 Wi-Fi 프로필을 만듭니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e32749225af3f19ab07decbcf1488595b7d946fd
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49424869"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Intune에서 Windows 장치에 대한 Wi-Fi 설정 가져오기

Windows를 실행하는 장치의 경우 이전에 파일로 내보낸 Wi-Fi 구성 프로필을 가져올 수도 있습니다. **Windows 10 이상 장치의 경우 Intune에서 직접 [Wi-Fi 프로필을 만들](wi-fi-settings-windows.md) 수도 있습니다**.

적용 대상:  
- Windows 8.1 이상
- Windows 10 이상
- Windows 10 데스크톱 또는 모바일
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Windows 장치에서 Wi-Fi 설정 내보내기

Windows에서 `netsh wlan`을 사용하여 기존 Wi-Fi 프로필을 Intune에서 읽을 수 있는 XML 파일로 내보냅니다. 프로필을 사용하기 위해 일반 텍스트로 키를 내보내야 합니다.

필수 WiFi 프로필이 이미 설치되어 있는 Windows 컴퓨터에서 다음 단계를 사용합니다.

1. 내보낸 Wi-Fi 프로필에 대한 로컬 폴더를 만듭니다(예: **c:\WiFi**).
2. 관리자 권한으로 명령 프롬프트를 엽니다.
3. `netsh wlan show profiles` 명령을 실행하고 내보내려는 프로필의 이름을 적어둡니다. 이 예제에서 프로필 이름은 **WiFiName**입니다.
4. `netsh wlan export profile name="ProfileName" folder=c:\Wifi` 명령을 실행합니다. 이 명령은 **Wi-Fi-WiFiName.xml**이라는 Wi-Fi 프로필 파일을 대상 폴더에 만듭니다.

## <a name="import-the-wi-fi-settings-into-intune"></a>Intune으로 Wi-Fi 설정 가져오기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 장치 제한 프로필의 **이름** 및 **설명**을 입력합니다.

    > [!IMPORTANT]
    > - 이름은 Wi-Fi 프로필 xml의 이름 속성과 동일**해야** 합니다. 그렇지 않으면 실패합니다.
    > - 미리 공유한 키를 포함하는 Wi-Fi 프로필을 내보내는 경우 명령에 `key=clear`를 추가**해야** 합니다. 예를 들어 다음과 같이 입력합니다. `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - Windows 10에서 미리 공유한 키를 사용하면 Intune에서 나타나는 업데이트 관리 오류가 발생합니다. 이런 경우 Wi-Fi 프로필은 장치에 제대로 할당되고 프로필은 예상대로 작동합니다.
    > - 미리 공유한 키를 포함하는 Wi-Fi 프로필을 내보내는 경우 파일이 보호되도록 합니다. 키가 일반 텍스트인 경우 키를 보호하는 것은 사용자의 책임입니다.

4. **플랫폼**에서 **Windows 8.1 이상**을 선택합니다.
5. **프로필 형식**에서 **Wi-Fi 가져오기**를 선택합니다.
6. 다음 설정을 구성합니다.
    - **연결 이름**: Wi-Fi 연결에 대한 이름을 입력합니다. 이 이름은 최종 사용자가 사용 가능한 Wi-Fi 네트워크를 찾아볼 때 표시됩니다.
    - **프로필 XML**: [찾아보기] 단추를 선택하고 가져오려는 Wi-Fi 프로필 설정이 포함된 XML 파일을 선택합니다.
    - **파일 콘텐츠**: 선택한 구성 프로필에 대한 XML 코드를 보여줍니다.
7. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아무것도 하지 않습니다. 그런 다음, [이 프로필을 할당](device-profile-assign.md)합니다.

## <a name="more-resources"></a>기타 참고 자료

사용 가능한 다른 플랫폼을 포함한 [Wi-Fi 설정 개요](wi-fi-settings-configure.md).