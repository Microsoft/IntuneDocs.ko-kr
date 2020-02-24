---
title: Intune에 회사 식별자 추가
titleSuffix: ''
description: Microsoft Intune에 회사 식별자(등록 방법, IMEI 및 일련 번호)를 추가하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51538f8994557bba718f0e8344b1da8d3c7193fa
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414416"
---
# <a name="identify-devices-as-corporate-owned"></a>회사 소유의 디바이스 식별

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 관리자로서 사용자는 디바이스를 회사 소유로 식별하여 관리 및 식별을 구체화할 수 있습니다. Intune은 추가 관리 작업을 수행하고 회사 소유 디바이스에서 전체 전화 번호와 앱의 인벤토리와 같은 추가 정보를 수집할 수 있습니다. 회사 소유가 아닌 디바이스에서 등록하지 못하도록 차단하는 디바이스 제한을 설정할 수도 있습니다.

등록 시 Intune은 다음과 같은 디바이스에 회사 소유 상태를 자동으로 할당합니다.

- [디바이스 등록 관리자](device-enrollment-manager-enroll.md) 계정을 사용하여 등록됨(모든 플랫폼)
- Apple [장비 등록 프로그램](device-enrollment-program-enroll-ios.md), [Apple School Manager](apple-school-manager-set-up-ios.md) 또는 [Apple Configurator](apple-configurator-enroll-ios.md)를 사용하여 등록됨(iOS만 해당)
- IMEI(International Mobile Equipment Identifier) 번호(IMEI 번호가 있는 모든 플랫폼) 또는 일련 번호(iOS 및 Android)를 사용하여 [등록 전에 회사 소유로 식별됨](#identify-corporate-owned-devices-with-imei-or-serial-number)
- 회사 또는 학교 자격 증명으로 Azure Active Directory에 조인됨 [Azure Active Directory 등록 디바이스](https://docs.microsoft.com/azure/active-directory/devices/overview)는 개인용으로 표시됩니다.
- [디바이스 속성 목록](#change-device-ownership)에서 회사로 설정

등록 후 **개인**과 **회사** 사이에서 [소유권 설정을 변경](#change-device-ownership)할 수 있습니다.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>IMEI 또는 일련 번호로 회사 소유 디바이스 식별

Intune 관리자는 14자리 IMEI 번호 또는 일련 번호가 나열된 쉼표로 구분된 값(.csv) 파일을 만들고 가져올 수 있습니다. Intune에서는 디바이스 등록 중에 이러한 식별자를 사용하여 디바이스 소유권을 회사로 지정합니다. 각 IMEI 또는 일련 번호에는 관리 용도로 목록에 지정된 세부 정보를 포함할 수 있습니다.

이 기능이 지원되는 플랫폼은 다음과 같습니다.

| 플랫폼 | IMEI 번호 | 일련 번호 |
|---|---|---|
| Windows | 지원됨(Windows Phone) | 지원되지 않음 |
| iOS/macOS | 지원되지 않음 | 지원됨 |
| 디바이스 관리자 관리 Android OS v10 | 지원되지 않음 | 지원되지 않음 |
| 기타 Android | 지원되지 않음 | 지원됨 |

<!-- When you upload serial numbers for corporate-owned iOS/iPadOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Apple 디바이스 일련 번호를 확인하는 방법을 알아봅니다](https://support.apple.com/HT204308).<br>
[Android 디바이스 일련 번호를 확인하는 방법을 알아봅니다](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>.csv 파일을 사용하여 회사 식별자 추가
목록을 만들려면 헤더 없이 2열로 구성된 쉼표로 구분된 값(.csv) 목록을 만듭니다. 왼쪽 열에 14자리 IMEI 또는 일련 번호를 추가하고, 오른쪽 열에 세부 정보를 추가합니다. ID, IMEI 또는 일련 번호 중 한 가지 유형만 단일 .csv 파일로 가져올 수 있습니다. 세부 정보는 128자로 제한되며 관리 용도로만 사용됩니다. 세부 정보는 디바이스에 표시되지 않습니다. 현재는 .csv 파일당 5,000개 행으로 제한됩니다.

**일련 번호가 포함된 .csv 파일 업로드** – 머리글 없이 두 열로 이루어진 쉼표로 구분된 값(.csv) 목록을 만들고 목록을 .csv 파일당 디바이스 5,000대 또는 용량 5MB로 제한합니다.

|||
|-|-|
|&lt;ID #1&gt;|&lt;디바이스 #1 세부 정보&gt;|
|&lt;ID #2&gt;|&lt;디바이스 #2 세부 정보&gt;|

이.csv 파일을 텍스트 편집기에서 보면 다음과 같이 표시됩니다.

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> 일부 Android 및 iOS/iPadOS 디바이스에는 IMEI 번호가 여러 개 있습니다. Intune은 등록된 디바이스당 하나의 IMEI 번호만 읽습니다. IMEI 번호를 가져오지만 Intune에서 인벤토리에 배정한 IMEI가 아닌 경우 디바이스는 회사 소유 디바이스가 아니라 개인 디바이스로 분류됩니다. 한 디바이스에 대해 여러 IMEI 번호를 가져오면 인벤토리에 배정되지 않은 번호는 등록 상태가 **알 수 없음**으로 표시됩니다.<br>
>다음 항목도 참고하세요. 일련 번호는 iOS/iPadOS 디바이스에 권장되는 식별 형식입니다.
>Android 일련 번호는 고유함이나 존재가 보장되지 않습니다. 일련 번호가 신뢰할 수 있는 디바이스 ID인지는 해당 디바이스 공급자에게 확인하세요.
>디바이스에서 Intune으로 보고된 일련 번호는 디바이스의 Android 설정/정보 메뉴에 표시되는 ID와 일치하지 않을 수 있습니다. 디바이스 제조업체에 보고된 일련 번호 형식을 확인하세요.
>점(.)을 포함하는 일련 번호를 사용하여 파일 업로드를 시도하면 업로드가 실패합니다. 점이 있는 일련 번호는 지원되지 않습니다.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>회사 식별자의 .csv 목록 업로드

1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하여 **디바이스** > **디바이스 등록** > **회사 디바이스 식별자** > **추가** > **CSV 파일 업로드**를 선택합니다.

2. **식별자 추가** 블레이드에서 **IMEI** 또는 **일련 번호** 중 식별자 형식을 지정합니다.

3. 폴더 아이콘을 클릭하고 가져오려는 목록의 경로를 지정하세요. .csv 파일로 이동하여 **추가**를 선택합니다. 

4. .csv 파일이 이미 Intune에 있지만 다른 세부 정보가 있는 회사 식별자를 포함하는 경우 **중복 식별자 검토** 팝업이 표시됩니다. Intune에 덮어쓰려는 식별자를 선택하고 **확인** 선택하여 식별자를 추가합니다. 각 식별자의 경우 첫 번째 중복만 비교됩니다.

## <a name="manually-enter-corporate-identifiers"></a>회사 식별자를 수동으로 입력

1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하여 **디바이스** > **디바이스 등록** > **회사 디바이스 식별자** > **추가** > **수동으로 입력**을 선택합니다.

2. **식별자 추가** 블레이드에서 **IMEI** 또는 **일련 번호** 중 식별자 형식을 지정합니다.

3. **식별자**와 추가하려는 각 식별자의 **세부 정보**를 입력합니다. 식별자 입력을 완료한 경우 **추가**를 선택합니다.

5. 이미 Intune에 있지만 다른 세부 정보가 있는 회사 식별자를 입력한 경우 **중복 식별자 검토** 팝업이 표시됩니다. Intune에 덮어쓰려는 식별자를 선택하고 **확인** 선택하여 식별자를 추가합니다. 각 식별자의 경우 첫 번째 중복만 비교됩니다.

**새로 고침**을 클릭하면 새로운 디바이스 식별자를 확인할 수 있습니다.

가져온 디바이스가 반드시 등록되지는 않습니다. 디바이스는 **등록됨** 또는 **연결되지 않음** 중 하나의 상태일 수 있습니다. **연결되지 않음**은 디바이스가 Intune 서비스와 통신된 적이 없음을 의미합니다.

## <a name="delete-corporate-identifiers"></a>회사 식별자 삭제

1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하여 **디바이스** > **디바이스 등록** > **회사 디바이스 식별자**를 선택합니다.
2. 삭제할 디바이스 식별자를 선택하고 **삭제**를 선택합니다.
3. 삭제를 확인합니다.

등록된 디바이스의 회사 식별자를 삭제해도 디바이스의 소유권이 변경되지는 않습니다. 디바이스의 소유권을 변경하려면 **디바이스**로 이동하고 디바이스를 선택하고 **속성**을 선택하고 **디바이스 소유권**을 변경합니다.

## <a name="imei-specifications"></a>IMEI 사양
International Mobile Equipment Identifiers에 대한 자세한 사양은 [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)을 참조하세요.

## <a name="change-device-ownership"></a>디바이스 소유권 변경

디바이스 속성은 Intune의 각 디바이스 레코드에 대한 **소유권**을 표시합니다. 관리자는 디바이스를 **개인** 또는 **회사**로 지정할 수 있습니다. 디바이스의 소유권 유형이 회사에서 개인으로 변경되면 Intune은 7일 내에 해당 디바이스에서 이전에 수집된 모든 앱 정보를 삭제합니다. 해당하는 경우 Intune은 레코드에서 전화 번호도 삭제합니다. 

**디바이스 소유권을 변경하려면 다음과 같이 합니다.**
1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하고 **디바이스** > **모든 디바이스** > 해당 디바이스를 선택합니다.
2. **속성**을 선택합니다.
3. **디바이스 소유권**을 **개인** 또는 **회사**로 지정합니다.

   ![디바이스 범주 및 디바이스 소유권 옵션을 보여 주는 디바이스 속성](./media/corporate-identifiers-add/device-properties.png)
