---
title: Microsoft Intune에서 Android 디바이스에 사용자 지정 설정 추가- Azure | Microsoft Docs
description: 미리 공유한 키로 WiFi 프로필을 만들려면 Android 디바이스에 대해 사용자 지정 프로필을 추가 또는 만들기, 앱당 VPN 프로필 만들기 또는 Microsoft Intune에서 Samsung Knox Standard 디바이스에 대한 앱 허용/차단
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 74d23c8433c741927f28bb1d6b9f55393e38f7db
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182978"
---
# <a name="use-custom-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune의 Android 디바이스에 대한 사용자 지정 설정 사용

Microsoft Intune을 사용하면 "사용자 지정 프로필"을 사용하여 Android 디바이스에 대한 사용자 지정 설정을 추가하거나 만들 수 있습니다. 사용자 지정 프로필은 Intune의 기능입니다. Intune에 기본 제공되지 않은 디바이스 설정 및 기능을 추가하도록 설계되었습니다.

Android 사용자 지정 프로필은 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 사용하여 Android 디바이스에서 다른 기능을 구성합니다. 이러한 설정은 일반적으로 모바일 디바이스 제조업체에서 이러한 기능을 제어하기 위해 사용합니다.

사용자 지정 프로필을 사용하여 다음 Android 설정을 구성하고 할당할 수 있습니다. 다음 설정은 intune에 기본 제공되지 않습니다.

- [미리 공유한 키를 사용하여 Wi-Fi 프로필 만들기](/intune/wi-fi-profile-shared-key)
- [앱당 VPN 프로필 만들기](/intune/android-pulse-secure-per-app-vpn)
- [Samsung KNOX Standard 장치에 대해 앱 허용 및 차단](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> 나열된 설정만이 사용자 지정 프로필에 의해 구성될 수 있습니다. Android 디바이스는 구성할 수 있는 OMA-URI 설정의 전체 목록을 노출하지 않습니다. 더 많은 설정을 참조하려는 경우 [Intune Uservoice 사이트](https://microsoftintune.uservoice.com/forums/291681-ideas)에서 더 많은 설정에 투표하십시오.

이 문서는 Android 디바이스의 사용자 지정 프로필을 만드는 방법을 보여줍니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: `android custom profile` 등의 프로필의 이름을 입력합니다.
    - **설명**: 설정에 대한 설명을 입력합니다.
    - **플랫폼**: **Android**를 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택합니다.

4. **사용자 지정 OMA-URI 설정**에서 **추가**를 선택합니다. 다음 설정을 입력합니다.

    - **이름**: 쉽게 찾을 수 있도록 OMA-URI 설정에 대한 고유 이름을 입력합니다.
    - **설명**: 설정에 대한 개요와 기타 중요한 모든 세부 정보를 제공하는 설명을 입력합니다.
    - **OMA-URI**: 설정으로 사용하려는 OMA-URI를 입력합니다.
    - **데이터 형식**: 이 OMA URI 설정에 사용할 데이터 형식을 선택합니다. 옵션은 다음과 같습니다.

      - 문자열
      - 문자열(XML 파일)
      - 날짜 및 시간
      - 정수
      - 부동 소수점
      - 부울
      - Base64(파일)

    - **값**: 입력한 OMA-URI와 연결할 데이터를 입력합니다. 값은 선택한 데이터 형식에 따라 달라집니다. 예를 들어 **날짜 및 시간**을 선택한 경우 날짜 선택에서 값을 선택합니다.

    일부 설정을 추가한 후 **내보내기**를 선택할 수 있습니다. **내보내기**는 쉼표로 구분된 값(.csv) 파일에서 추가한 모든 값의 목록을 만듭니다.

5. **확인**을 선택하여 변경 내용을 저장합니다. 필요에 따라 더 많은 설정을 계속 추가합니다. 
6. 끝나면 **확인** > **만들기**를 선택하여 Intune 프로필을 만듭니다. 완료되면 프로필이 **디바이스 구성 - 프로필** 목록에 나타납니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 그런 다음, [프로필을 할당합니다](device-profile-assign.md).

[Android 엔터프라이즈 장치에서 프로필을 만드는](custom-settings-android-for-work.md) 방법을 참조하세요.
