---
title: Windows Phone 8.1을 실행하는 장치에 대한 Microsoft Intune 사용자 지정 설정
titleSuffix: ''
description: Windows Phone 8.1 사용자 지정 프로필에서 사용할 수 있는 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b21464016dff3396b25861af568fa90d8b7a260f
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31834756"
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-phone-81"></a>Windows Phone 8.1을 실행하는 장치에 대한 Microsoft Intune 사용자 지정 장치 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune Windows Phone 8.1 **사용자 지정** 프로필을 사용하여 Windows Phone 8.1 장치에서 기능을 제어하는 데 사용할 수 있는 OMA-URI 설정을 할당할 수 있습니다. 이는 많은 모바일 장치 제조업체가 장치 기능을 제어하는 데 사용하는 표준 설정입니다.

이 기능은 다른 Intune 정책을 사용하여 구성할 수 없는 설정을 할당할 수 있도록 하기 위한 것입니다.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Windows Phone 8.1 장치에 대한 사용자 지정 정책 설정

1. [Microsoft Intune에서 사용자 지정 장치 설정을 구성하는 방법](custom-settings-configure.md)의 지침을 사용하여 시작합니다.
2. **사용자 지정 OMA-URI 설정** 창서 **추가**를 선택하여 하나 이상의 OMA-URI 설정을 추가합니다.
3. **행 추가** 창에서 각 설정에 대해 다음 값을 구성합니다.
    - **이름** - 설정 목록에서 쉽게 식별할 수 있도록 OMA-URI 설정에 대한 고유한 이름을 입력합니다.
    - **설명** - 설정의 개요에 대한 설명과 찾을 때 도움이 되는 기타 관련 정보를 제공합니다.
    - **OMA-URI** - 설정을 제공하려는 OMA-URI를 지정합니다.
    - **데이터 형식** - 이 OMA-URI 설정을 지정할 데이터 형식을 선택합니다. **문자열**, **문자열(XML)**, **날짜 및 시간**, **정수**, **부동 소수점**, **부울** 또는 **Base64** 중에서 선택합니다.
    - **값** - 입력한 OMA-URI와 연결할 값 또는 파일을 입력합니다.

4. 완료되면 **확인**을 클릭한 다음 필요에 따라 설정을 계속 추가합니다.
