---
title: Microsoft Intune에서 Android 디바이스의 Wi-Fi 설정 구성 - Azure | Microsoft Docs
titleSuffix: ''
description: Android의 WiFi 디바이스 구성 프로필을 만들거나 추가합니다. Microsoft Intune에서 인증서 추가, EAP 유형 선택 및 인증 방법 선택을 포함하여 다양한 설정을 확인합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/26/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 955d9931779752e8736435555db7f7aba777b430
ms.sourcegitcommit: 8b716db3c0fdbb7dff62497ec283902a5069a343
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652405"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Microsoft Intune에서 Android를 실행하는 디바이스의 Wi-Fi 설정 추가

특정 WiFi 설정을 사용하여 프로필을 만든 후 Android 디바이스에 이 프로필을 배포할 수 있습니다. Microsoft Intune은 네트워크에 인증, PKS 또는 SCEP 인증서 사용 등을 포함한 많은 기능을 제공합니다.

Wi-Fi 설정은 기본 설정 및 엔터프라이즈 수준 설정이라는 두 가지 범주로 구분됩니다.

이 문서에서는 이러한 설정을 설명합니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 프로필 만들기](device-profile-create.md).

## <a name="basic"></a>기본

- **Wi-Fi 유형**: **기본**을 선택합니다.
- **SSID**: 디바이스에 연결할 무선 네트워크의 실제 이름인 **서비스 집합 ID**를 입력합니다. 그러나 사용자에게는 연결을 선택할 때 구성한 **네트워크 이름**만 표시됩니다.
- **숨겨진 네트워크**: **사용**을 선택하면 이 네트워크가 디바이스의 사용 가능한 네트워크 목록에 숨겨집니다. SSID는 브로드캐스트되지 않습니다. **사용 안 함**을 선택하면 이 네트워크가 디바이스의 사용 가능한 네트워크 목록에 표시됩니다.

## <a name="enterprise"></a>Enterprise

- **Wi-Fi 유형**: **엔터프라이즈**를 선택합니다.
- **SSID**: 디바이스에 연결할 무선 네트워크의 실제 이름인 **서비스 집합 ID**를 입력합니다. 그러나 사용자에게는 연결을 선택할 때 구성한 **네트워크 이름**만 표시됩니다.
- **숨겨진 네트워크**: **사용**을 선택하면 이 네트워크가 디바이스의 사용 가능한 네트워크 목록에 숨겨집니다. SSID는 브로드캐스트되지 않습니다. **사용 안 함**을 선택하면 이 네트워크가 디바이스의 사용 가능한 네트워크 목록에 표시됩니다.
- **EAP 유형**: 보안 무선 연결을 인증하는 데 사용되는 EAP(확장할 수 있는 인증 프로토콜) 유형을 선택합니다. 옵션은 다음과 같습니다.

  - **EAP-TLS**: 또한 다음을 입력합니다.

    - **서버 신뢰** - **서버 유효성 검사에 대한 루트 인증서**: 기존의 신뢰할 수 있는 루트 인증서 프로필을 선택합니다. 이 인증서는 클라이언트가 네트워크에 연결될 때 서버에 제공되며 연결을 인증합니다.

    - **클라이언트 인증** - **클라이언트 인증에 사용할 클라이언트 인증서(ID 인증서)** : 디바이스에도 배포되는 SCEP 또는 PKCS 클라이언트 인증서 프로필을 선택합니다. 이 인증서는 연결을 인증하기 위해 디바이스가 서버에 제공하는 ID입니다.

    - **ID 개인 정보 사용(외부 ID)** : EAP ID 요청에 대한 응답으로 전송되는 텍스트를 입력합니다. 이 텍스트에는 `anonymous`와 같은 값을 사용할 수 있습니다. 인증하는 동안 이 익명 ID가 먼저 전송된 다음 실제 ID가 보안 채널을 통해 전송됩니다.

  - **EAP-TTLS**: 또한 다음을 입력합니다.

    - **서버 신뢰** - **서버 유효성 검사에 대한 루트 인증서**: 기존의 신뢰할 수 있는 루트 인증서 프로필을 선택합니다. 이 인증서는 클라이언트가 네트워크에 연결될 때 서버에 제공되며 연결을 인증합니다.

    - **클라이언트 인증**: **인증 방법**을 선택합니다. 옵션은 다음과 같습니다.

      - **사용자 이름 및 암호**: 연결을 인증하기 위해 사용자 이름 및 암호를 입력하라는 메시지가 사용자에게 표시됩니다. 또한 다음을 입력합니다.
        - **EAP 이외의 방법(내부 ID)** : 연결을 인증하는 방법을 선택합니다. Wi-Fi 네트워크에 구성된 동일한 프로토콜을 선택해야 합니다. 옵션은 다음과 같습니다.

          - **암호화되지 않은 암호(PAP)**
          - **CHAP(Challenge Handshake 인증 프로토콜)**
          - **MS-CHAP(Microsoft CHAP)**
          - **MS-CHAP v2(Microsoft CHAP 버전 2)**

      - **인증서**: 디바이스에도 배포되는 SCEP 또는 PKCS 클라이언트 인증서 프로필을 선택합니다. 이 인증서는 연결을 인증하기 위해 디바이스가 서버에 제공하는 ID입니다.

      - **ID 개인 정보 사용(외부 ID)** : EAP ID 요청에 대한 응답으로 전송되는 텍스트를 입력합니다. 이 텍스트에는 `anonymous`와 같은 값을 사용할 수 있습니다. 인증하는 동안 이 익명 ID가 먼저 전송된 다음 실제 ID가 보안 채널을 통해 전송됩니다.

  - **PEAP**: 또한 다음을 입력합니다.

    - **서버 신뢰** - **서버 유효성 검사에 대한 루트 인증서**: 기존의 신뢰할 수 있는 루트 인증서 프로필을 선택합니다. 이 인증서는 클라이언트가 네트워크에 연결될 때 서버에 제공되며 연결을 인증합니다.

    - **클라이언트 인증**: **인증 방법**을 선택합니다. 옵션은 다음과 같습니다.

      - **사용자 이름 및 암호**: 연결을 인증하기 위해 사용자 이름 및 암호를 입력하라는 메시지가 사용자에게 표시됩니다. 또한 다음을 입력합니다.
        - **인증을 위한 EAP 이외의 방법(내부 ID)** : 연결을 인증하는 방법을 선택합니다. Wi-Fi 네트워크에 구성된 동일한 프로토콜을 선택해야 합니다. 옵션은 다음과 같습니다.

          - **없음**
          - **MS-CHAP v2(Microsoft CHAP 버전 2)**

      - **인증서**: 디바이스에도 배포되는 SCEP 또는 PKCS 클라이언트 인증서 프로필을 선택합니다. 이 인증서는 연결을 인증하기 위해 디바이스가 서버에 제공하는 ID입니다.

      - **ID 개인 정보 사용(외부 ID)** : EAP ID 요청에 대한 응답으로 전송되는 텍스트를 입력합니다. 이 텍스트에는 `anonymous`와 같은 값을 사용할 수 있습니다. 인증하는 동안 이 익명 ID가 먼저 전송된 다음 실제 ID가 보안 채널을 통해 전송됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아무것도 하지 않습니다. 그런 다음, [이 프로필을 할당](device-profile-assign.md)합니다.

## <a name="more-resources"></a>기타 참고 자료

- 다른 플랫폼을 포함한 [Wi-Fi 설정 개요](wi-fi-settings-configure.md).

- Android 엔터프라이즈 또는 Android 키오스크 디바이스를 사용 중인가요? 그렇다면 [Android 엔터프라이즈 및 전용 디바이스를 실행하는 디바이스의 Wi-Fi 설정](wi-fi-settings-android-enterprise.md)을 확인하세요.
