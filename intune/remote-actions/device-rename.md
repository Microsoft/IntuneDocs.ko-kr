---
title: Microsoft Intune을 사용하여 디바이스 이름 바꾸기 - Azure | Microsoft Docs
description: Microsoft Intune을 사용하여 디바이스 이름을 바꿉니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11b339a3e94e60db43e8237d9f3d2c729b48a57d
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413604"
---
# <a name="rename-a-device-in-intune"></a>Intune에서 디바이스 이름 바꾸기

**디바이스 이름 바꾸기** 작업을 통해 Intune에 등록된 디바이스의 이름을 바꿀 수 있습니다. 디바이스 이름은 Intune 및 디바이스에서 변경됩니다.

다음 유형의 디바이스 이름을 바꿀 수 있습니다.
- 회사 소유 Windows 
- iOS/iPadOS 감독
- 회사 소유 MacOS 10

이 기능은 현재 하이브리드 Azure AD Windows 디바이스의 이름 바꾸기를 지원하지 않습니다.

## <a name="rename-a-device"></a>디바이스 이름 바꾸기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
3. **디바이스** > **모든 디바이스**를 선택한 후 디바이스 > **기타** > **디바이스 이름 바꾸기**를 선택합니다.
4. **디바이스 이름 바꾸기** 블레이드에서 텍스트 상자에 새 이름을 입력합니다. 문자, 숫자 및 하이픈을 사용할 수 있습니다. 이름은 하나 이상의 문자 또는 하이픈을 포함해야 합니다.
5. 이름을 바꾼 후 디바이스를 다시 시작하려면 **이름을 바꾼 후 다시 시작** 옆에 있는 **예**를 선택합니다.
6. **이름 바꾸기**를 선택합니다.

## <a name="windows-device-rename-rules"></a>Windows 디바이스 이름 바꾸기 규칙
Windows 디바이스의 이름을 바꿀 때 새 이름은 다음 규칙을 따라야 합니다.
- 15자 이하(63바이트보다 작거나 같아야 함, 후행 NULL을 포함하지 않음)
- null 또는 빈 문자열이 아님
- 허용된 ASCII: 문자(a-z, A-Z), 숫자(0-9) 및 하이픈
- 허용된 유니코드: 문자 >= 0x80, 유효한 UTF8이어야 함, IDN 매핑 가능해야 함(RtlIdnToNameprepUnicode가 성공함, RFC 3492 참조)
- 이름에 숫자만 포함할 수는 없음
- 이름에 공백이 없음
- 허용되지 않는 문자: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>다음 단계

디바이스 **이름 바꾸기** 작업의 상태를 확인하려면 디바이스의 **개요** 페이지를 확인합니다.
