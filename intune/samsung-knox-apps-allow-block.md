---
title: Samsung Knox에 대한 앱 허용/차단 Microsoft IntuneIntune 정책
titleSuffix: ''
description: Samsung Knox Standard 디바이스에 대해 앱을 허용 및 차단하는 사용자 지정 프로필을 만듭니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4efa2a813dda16805effe55ff3d1b967ef5d6c88
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798230"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Microsoft Intune에서 사용자 지정 정책을 사용하여 Samsung Knox Standard 디바이스에 대해 앱 허용 및 차단 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클의 절차를 사용하여 다음 중 하나를 만들 수 있는 Microsoft Intune 사용자 지정 정책을 만듭니다.

- 디바이스에서 실행되지 않도록 차단할 앱 목록. 이 목록에 있는 앱은 정책을 적용했을 때 이미 설치되어 있었더라도 실행이 차단됩니다.
- 디바이스의 사용자가 Google Play 스토어에서 설치할 수 있는 앱 목록입니다. 나열된 앱만 설치할 수 있습니다. 다른 앱은 스토어에서 설치할 수 없습니다.

이러한 설정은 Samsung Knox Standard를 실행하는 디바이스에서만 사용할 수 있습니다.

## <a name="create-an-allowed-or-blocked-app-list"></a>허용되거나 차단된 앱 목록 만들기

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **디바이스 구성**을 선택합니다.
2. **디바이스 구성** 창에서 **관리** > **프로필**을 선택합니다.
2. 프로필 목록 창에서 **프로필 만들기**를 선택합니다.
3. **프로필 만들기** 창에서 이 디바이스 프로필에 대한 **이름** 및 선택적 **설명**을 입력합니다.
2. **Android**의 **플랫폼**과 **사용자 지정**의 **프로필 유형**을 선택합니다.
3. **설정**을 클릭합니다.
3. **사용자 지정 OMA-URI 설정** 창에서 **추가**를 선택합니다.
4. **OMA URI 설정 추가 또는 편집** 대화 상자에서 다음 설정을 지정합니다.

   디바이스에서 실행이 차단된 앱 목록의 경우

   - **이름** - **PreventStartPackages**를 입력합니다.
   - **설명** - ‘실행이 차단된 앱 목록’과 같이 설명을 선택적으로 입력합니다.
   -    **데이터 형식** - 드롭다운 목록에서 **문자열**을 선택합니다.
   -    **OMA-URI** - **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**를 입력합니다.
   -    **값** - 허용할 앱 패키지 이름 목록을 입력합니다. 구분 기호로 **;:,** 또는 **|** 를 사용할 수 있습니다. (예: package1, package2;)

   사용자가 다른 앱을 모두 제외하는 반면 Google Play 스토어에서 설치할 수 있도록 허용된 앱 목록의 경우
   - **이름** - **AllowInstallPackages**를 입력합니다.
   - **설명** - ‘사용자가 Google Play 스토어에서 설치할 수 있는 앱 목록’과 같이 설명을 선택적으로 입력합니다.
   - **데이터 형식** - 드롭다운 목록에서 **문자열**을 선택합니다.
   - **OMA-URI** - **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**를 입력합니다.
   - **값** - 허용할 앱 패키지 이름 목록을 입력합니다. 구분 기호로 **;:,** 또는 **|** 를 사용할 수 있습니다. (예: package1, package2;)

4. **확인**을 클릭한 다음, **프로필 만들기** 창에서 **만들기**를 선택합니다.

>[!TIP]
> Google Play 스토어에서 앱을 탐색하여 앱의 패키지 ID를 찾을 수 있습니다. 패키지 ID는 앱 페이지의 URL에 포함되어 있습니다. 예를 들어 Microsoft Word 앱의 패키지 ID는 **com.microsoft.office.word**입니다.

다음에 대상이 지정된 각 디바이스가 체크인되면 앱 설정이 적용됩니다.


<!---## Assign the custom profile--->
