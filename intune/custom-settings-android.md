---
title: Microsoft Intune - Azure에서 Android 장치에 대한 사용자 지정 설정 추가 | Microsoft Docs
description: 미리 공유한 키로 WiFi 프로필을 만들려면 Android 장치에 대해 사용자 지정 프로필을 추가 또는 만들기, 앱당 VPN 프로필 만들기 또는 Microsoft Intune에서 Samsung Knox Standard 장치에 대한 앱 허용/차단
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0195e138b59fae019fa2bc02aadf211257a65cac
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022053"
---
# <a name="custom-settings-for-android-devices---intune"></a>Android 장치 - Intune에 대한 사용자 지정 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

사용자 지정 설정은 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 사용하여 Android 장치에서 다른 기능을 구성합니다. 이러한 설정은 일반적으로 모바일 장치 제조업체에서 장치에서 기능을 제어하기 위해 사용합니다.

사용자 지정 프로필을 사용하여 다음 Android 설정을 구성하고 할당할 수 있습니다. 이러한 설정은 Intune 정책에 기본 제공되지 않습니다.

- [미리 공유한 키를 사용하여 Wi-Fi 프로필 만들기](/intune/wi-fi-profile-shared-key)
- [앱당 VPN 프로필 만들기](/intune/android-pulse-secure-per-app-vpn)
- [Samsung KNOX Standard 장치에 대해 앱 허용 및 차단](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> 나열된 설정만이 이 프로필 형식에 의해 구성될 수 있습니다. Android 장치는 구성할 수 있는 OMA-URI 설정의 전체 목록을 노출하지 않습니다. 더 많은 설정을 참조하려는 경우 [Intune Uservoice 사이트](https://microsoftintune.uservoice.com/forums/291681-ideas)에서 더 많은 설정에 투표하십시오.

## <a name="custom-profile-settings-for-android-devices"></a>Android 장치에 대한 사용자 지정 프로필 설정

1. [Azure 포털](https://portal.azure.com)에 로그인합니다. 
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. Android 플랫폼을 사용하여 사용자 지정 프로필을 만듭니다. [Microsoft Intune에서 사용자 지정 장치 설정 구성](custom-settings-configure.md)에서 단계를 나열합니다.
4. **사용자 지정 OMA-URI 설정**에서 **추가**를 선택한 다음, **행 추가**를 선택합니다.
5. 다음 속성을 입력합니다.

   - **이름** - 쉽게 찾을 수 있도록 OMA-URI 설정에 대한 고유 이름을 입력합니다.
   - **설명** - 설정에 대한 개요와 기타 중요한 모든 세부 정보를 제공하는 설명을 입력합니다.
   - **데이터 형식** - 이 OMA URI 설정에 사용하는 데이터 형식을 입력합니다. **문자열**, **문자열(XML)**, **날짜 및 시간**, **정수**, **부동 소수점** 또는 **부울** 중에서 선택합니다.
   - **OMA URI** - 원하는 OMA URI를 입력합니다.
   - **값** - 입력한 OMA-URI와 연결할 값을 입력합니다.

6. **확인**을 선택하여 변경 내용을 저장합니다. 필요에 따라 더 많은 설정을 계속 추가합니다.

## <a name="next-steps"></a>다음 단계

설정을 완료하면 프로필이 생성되어 목록에 표시됩니다. 이 프로필을 그룹에 할당하려면 [장치 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.
