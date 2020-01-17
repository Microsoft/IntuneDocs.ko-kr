---
title: Samsung Knox에 대한 앱 허용/차단 Microsoft IntuneIntune 정책
titleSuffix: ''
description: Samsung Knox Standard 디바이스에 대해 앱을 허용 및 차단하는 사용자 지정 프로필을 만듭니다.
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
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207080"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Microsoft Intune에서 사용자 지정 정책을 사용하여 Samsung Knox Standard 디바이스에 대해 앱 허용 및 차단 

이 아티클의 절차를 사용하여 다음 중 하나를 만들 수 있는 Microsoft Intune 사용자 지정 정책을 만듭니다.

- 디바이스에서 실행되지 않도록 차단할 앱 목록. 이 목록에 있는 앱은 정책을 적용했을 때 이미 설치되어 있었더라도 실행이 차단됩니다.
- 디바이스의 사용자가 Google Play 스토어에서 설치할 수 있는 앱 목록입니다. 나열된 앱만 설치할 수 있습니다. 다른 앱은 스토어에서 설치할 수 없습니다.

이러한 설정은 Samsung Knox Standard를 실행하는 디바이스에서만 사용할 수 있습니다.

## <a name="create-an-allowed-or-blocked-app-list"></a>허용되거나 차단된 앱 목록 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 좋은 프로필 이름은 **Windows phone 사용자 지정 프로필**입니다.
    - **설명**: 설정에 대한 개요와 기타 중요한 모든 세부 정보를 제공하는 설명을 입력합니다.
    - **플랫폼**: **Android**를 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택 합니다.

4. **사용자 지정 OMA-URI 설정**에서 **추가**를 선택합니다. 다음 설정을 입력합니다.

    디바이스에서 실행이 차단된 앱 목록의 경우

    - **이름**: **PreventStartPackages**를 입력합니다.
    - **설명**: 설정 개요를 제공하는 설명과 프로필을 찾는 데 도움이 되는 기타 관련 정보를 입력합니다. 예를 들어 **실행이 차단 된 앱 목록을**입력 합니다.
    - **OMA-URI**(대/소문자 구분): **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**를 입력합니다.
    - **데이터 형식**: **문자열**을 선택 합니다.
    - **값**: 허용할 앱 패키지 이름 목록을 입력합니다. 구분 기호로 `;`, `:` 또는 `|`를 사용할 수 있습니다. 예를 들어 다음과 같이 입력합니다. `package1;package2;`

   사용자가 다른 앱을 모두 제외하는 반면 Google Play 스토어에서 설치할 수 있도록 허용된 앱 목록의 경우

    - **이름**: **AllowInstallPackages**를 입력합니다.
    - **설명**: 설정 개요를 제공하는 설명과 프로필을 찾는 데 도움이 되는 기타 관련 정보를 입력합니다. 예를 들어 **사용자가 Google Play에서 설치할 수 있는 앱 목록을**입력 합니다.
    - **OMA-URI**(대/소문자 구분): **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**를 입력합니다.
    - **데이터 형식**: **문자열**을 선택 합니다.
    - **값**: 허용할 앱 패키지 이름 목록을 입력합니다. 구분 기호로 `;`, `:` 또는 `|`를 사용할 수 있습니다. 예를 들어 다음과 같이 입력합니다. `package1;package2;`

5. **확인**을 선택하여 변경 내용을 저장합니다.
6. 완료되면 **확인** > **만들기**를 선택하여 Intune 프로필을 만듭니다. 완료되면 프로필이 **디바이스 - 구성 프로필** 목록에 표시됩니다.

>[!TIP]
> Google Play 스토어에서 앱을 탐색하여 앱의 패키지 ID를 찾을 수 있습니다. 패키지 ID는 앱 페이지의 URL에 포함되어 있습니다. 예를 들어 Microsoft Word 앱의 패키지 ID는 **com.microsoft.office.word**입니다.

다음에 대상이 지정된 각 디바이스가 체크인되면 앱 설정이 적용됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](../device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.
