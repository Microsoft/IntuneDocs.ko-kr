---
title: Microsoft Intune에서 Windows 10 장치에 대한 사용자 지정 설정 - Azure | Microsoft Docs
description: Microsoft Intune의 사용자 지정 프로필을 사용하여 Windows 10을 실행하는 장치에서 OMA-URI 사용자 지정 설정을 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdbb6643a4ee8aace0db22cd7f9189f7ac6445f0
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232829"
---
# <a name="custom-oma-uri-settings-for-windows-10-devices---intune"></a>Windows 10 장치에 대한 사용자 지정 OMA-URI 설정 - Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 10 및 Windows 10 Mobile용 Microsoft Intune **사용자 지정** 프로필을 사용하여 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 배포합니다. 이러한 설정은 장치의 기능을 제어하는 데 사용됩니다. Windows 10에서는 [정책 CSP(구성 서비스 공급자)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)와 같은 다양한 CSP(구성 서비스 공급자) 설정을 사용할 수 있습니다.

특정 설정을 찾고 있는 경우 Intune에서 기본 제공되며 사용자 지정 값이 필요가 없는 여러 설정이 [Windows 10 장치 제한 프로필](device-restrictions-windows-10.md)에 있습니다.

## <a name="configure-custom-settings"></a>사용자 지정 설정 구성

1. **사용자 지정** 프로필 유형을 사용하여 새 구성 프로필을 생성합니다. [사용자 지정 장치 설정을 구성하는 방법](custom-settings-configure.md)에 단계가 나열됩니다.
2. **사용자 지정 OMA-URI 설정**에서 **추가**를 선택하여 새 설정을 만듭니다. **내보내기**를 클릭하여 쉼표로 구분된 값(.csv) 파일로 구성한 모든 값의 목록을 만들 수도 있습니다.
3. 추가하려는 각 OMA-URI 설정에 대해 다음 정보를 입력합니다.

- **이름**: 설정 목록에서 쉽게 식별할 수 있도록 OMA-URI 설정에 대한 고유한 이름을 입력합니다.
- **설명** : 필요에 따라 설정에 대한 설명을 입력합니다.
- **OMA-URI(대/소문자 구분)**: 설정을 제공할 OMA-URI를 입력합니다.
- **데이터 형식**: 다음 중에서 선택합니다.
  - **문자열**
  - **문자열(XML)**
  - **날짜 및 시간**
  - **정수**
  - **부동 소수점**
  - **부울**
  - **Base64**
- **값**: 입력한 OMA-URI와 연결할 값 또는 파일을 입력합니다.

4. 작업이 완료되면 **확인**을 선택합니다. **프로필 만들기**에서 **만들기**를 선택합니다. 프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="example"></a>예제
다음 예제에서는 **Connectivity/AllowVPNOverCellular** 설정이 사용됩니다. 이 설정을 사용하면 Windows 10 장치는 셀룰러 네트워크에서 VPN 연결을 열 수 있습니다.

![VPN 설정을 포함하는 사용자 지정 정책의 예](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>구성할 수 있는 정책 찾기

Windows 10에서 지원하는 모든 CSP(구성 서비스 공급자)의 전체 목록은 [구성 서비스 공급자 참조](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)에서 확인할 수 있습니다.

일부 Windows 10 버전과 호환되지 않는 설정도 있습니다. [구성 서비스 공급자 참조](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)는 각 CSP에 지원되는 버전을 알려 줍니다.

또한 Intune은 나열된 설정을 모두 지원하지는 않습니다. 원하는 설정을 Intune에서 지원하는지 확인하려면 해당 설정에 대한 아티클을 엽니다. 각 설정 페이지에 지원되는 작업이 표시되어 있습니다. Intune으로 작업하려면 설정에서 **추가** 또는 **대체** 작업을 지원해야 합니다.
