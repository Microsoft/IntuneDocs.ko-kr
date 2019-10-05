---
title: Microsoft Intune에서 Windows 10 디바이스에 대한 사용자 지정 설정 추가 - Azure | Microsoft Docs
description: Microsoft Intune에서 Windows 10을 실행하는 디바이스에 OMA-URI 설정을 사용하려면 사용자 지정 프로필을 추가하거나 만듭니다. 사용자 지정 프로필을 사용하여 사용자 지정 설정을 추가합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51ee389351dd0ccccf69f01e932f7374ca38b03b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735066"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>Intune에서 Windows 10 디바이스에 대한 사용자 지정 사용

Microsoft Intune을 사용하면 "사용자 지정 프로필"을 사용하여 Windows 10 디바이스에 대한 사용자 지정 설정을 추가하거나 만들 수 있습니다. 사용자 지정 프로필은 Intune의 기능입니다. Intune에 기본 제공되지 않은 디바이스 설정 및 기능을 추가하도록 설계되었습니다.

Windows 10 사용자 지정 프로필은 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 사용하여 다른 기능을 구성합니다. 이러한 설정은 일반적으로 모바일 디바이스 제조업체에서 디바이스에서 기능을 제어하기 위해 사용합니다. 

Windows 10에서는 [정책 CSP(구성 서비스 공급자)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)와 같은 다양한 CSP(구성 서비스 공급자) 설정을 사용할 수 있습니다.

특정 설정을 찾을 경우 [Windows 10 디바이스 제한 프로필 ](device-restrictions-windows-10.md)에 많은 기본 제공 설정이 있습니다. 따라서 사용자 지정 값을 입력할 필요가 없습니다.

이 문서에서는 다음을 보여줍니다.

- Windows 10 디바이스에 대한 사용자 지정 프로필을 만드는 방법
- 권장된 OMA-URI 설정 목록을 포함합니다.
- VPN 연결을 여는 사용자 지정 프로필의 예를 제공합니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: `windows 10 custom profile` 등의 프로필의 이름을 입력합니다.
    - **설명**: 설정에 대한 설명을 입력합니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택합니다.

4. **사용자 지정 OMA-URI 설정**에서 **추가**를 선택합니다. 다음 설정을 입력합니다.

    - **이름**: 설정 목록에서 쉽게 식별할 수 있도록 OMA-URI 설정에 대한 고유한 이름을 입력합니다.
    - **설명**: 설정에 대한 개요와 기타 중요한 모든 세부 정보를 제공하는 설명을 입력합니다.
    - **OMA-URI**(대/소문자 구분): 설정으로 사용할 OMA-URI를 입력합니다.
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

## <a name="example"></a>예제

다음 예제에서는 **Connectivity/AllowVPNOverCellular** 설정이 사용됩니다. 이 설정을 사용하면 Windows 10 디바이스는 셀룰러 네트워크에서 VPN 연결을 열 수 있습니다.

![VPN 설정을 포함하는 사용자 지정 정책의 예](./media/custom-settings-windows-10/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>구성할 수 있는 정책 찾기

[구성 서비스 공급자 참조](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)에서 Windows 10이 지원하는 모든 CSP(구성 서비스 공급자)의 전체 목록이 있습니다.

일부 Windows 10 버전과 호환되지 않는 설정도 있습니다. [구성 서비스 공급자 참조](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)는 각 CSP에 지원되는 버전을 알려 줍니다.

또한 Intune은 [구성 서비스 공급자 참조](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)에 나열된 모든 설정을 지원하지 않습니다. 원하는 설정을 Intune에서 지원하는지 확인하려면 해당 설정에 대한 아티클을 엽니다. 각 설정 페이지는 지원되는 작업이 표시됩니다. Intune으로 작업하려면 설정에서 **추가**, **대체** 및 **가져오기** 작업을 지원해야 합니다. **Get** 작업에서 반환된 값이 **추가** 또는 **교체** 작업에서 제공한 값과 일치하지 않으면 Intune에서 규정 준수 오류를 보고합니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 그런 다음, [프로필을 할당합니다](device-profile-assign.md).
