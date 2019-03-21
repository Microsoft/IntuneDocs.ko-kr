---
title: 기술 지원팀의 문제 해결 포털
titlesuffix: Microsoft Intune
description: 기술 지원팀 직원은 문제 해결 포털을 사용하여 사용자의 기술 문제를 해결합니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 135e93bf3cfb93b5299dfd005a3ca70bbba84d77
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57787137"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>문제 해결 포털을 사용하여 회사 내 사용자 지원

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

문제 해결 포털에서는 지원 센터 운영자 및 Intune 관리자가 사용자 정보를 보고 사용자 도움 요청을 해결할 수 있습니다. 지원 센터를 포함하는 조직은 **지원 센터 운영자**를 사용자 그룹에 할당할 수 있습니다. 지원 센터 운영자 역할은 **문제 해결** 창을 사용할 수 있습니다.

**문제 해결** 창에도 사용자 등록 문제가 표시됩니다. 문제 및 제안된 수정 단계에 대한 세부 정보를 통해 관리자 및 도움말 지원 센터 운영자가 문제를 해결할 수 있습니다. 특정 등록 문제는 캡처되지 않고 일부 오류에는 수정 제안이 없을 수 있습니다.

지원 센터 운영자 역할을 추가하는 단계는 [Intune을 통한 RBAC(역할 기반 관리 제어)](/intune/role-based-access-control)를 참조하세요.

사용자가 Intune 관련 기술 문제를 지원 센터에 문의하면 지원 센터 운영자가 사용자 이름을 입력합니다. Intune에서는 다음을 포함하여 계층 1의 많은 문제를 해결하는 데 도움이 되는 유용한 데이터를 보여 줍니다.

- 사용자 상태
- 할당
- 규정 준수 문제
- 디바이스가 응답하지 않음
- 디바이스가 Wi-Fi 또는 VPN 설정을 가져오지 않음
- 앱 설치 실패

## <a name="to-review-troubleshooting-details"></a>문제 해결 세부 정보 검토

문제 해결 창에서 **사용자 선택**을 선택하여 사용자 정보를 봅니다. 사용자 정보는 사용자와 디바이스의 현재 상태를 이해하는 데 유용합니다.  

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **문제 해결**을 선택합니다.
4. **선택**을 클릭하여 문제를 해결할 사용자를 선택합니다.
5. 이름 또는 이메일 주소를 입력하여 사용자를 선택합니다. **선택**을 클릭합니다. 문제 해결 창에서 사용자에 대한 문제 해결 정보가 표시됩니다. 다음 표에서는 이러한 정보에 대해 설명합니다.

> [!Note]  
> 브라우저를 [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting)으로 전환하여 **문제 해결** 창에 액세스할 수도 있습니다.

## <a name="areas-of-troubleshooting-dashboard"></a>문제 해결 대시보드의 영역

**문제 해결** 창을 사용하여 사용자 정보를 검토할 수 있습니다.

![](/intune/media/troubleshooting-dash.png)

| 영역 | 이름 | 설명 |
| ---  | ---  | ---         |
| 1.   | 계정 상태  | 현재 Intune 테넌트의 상태가 **활성** 또는 **비활성**으로 표시됩니다.       |
| 2.   | 사용자를 선택합니다.  | 현재 선택된 사용자의 이름입니다. **사용자 변경**을 클릭하여 새 사용자를 선택합니다.       |
| 3.   | 사용자 상태  | 사용자의 Intune 라이선스, 디바이스 수, 각 디바이스의 준수, 앱 수 및 앱의 준수에 대한 상태가 표시됩니다.       |
| 4.   | 사용자 정보  | 이 목록을 사용하여 창에서 검토할 세부 정보를 선택합니다. <br>선택할 수 있는 항목은 다음과 같습니다. <ul><li>클라이언트 앱<li>규정 준수 정책<li> 구성 정책<li>앱 보호 정책 <li>등록 제한 사항</ul>      |
| 5.   | 그룹 구성원 자격  | 선택한 사용자가 구성원인 현재 그룹을 보여 줍니다.       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

## <a name="enrollment-failure-reference"></a>등록 오류 참조

등록 오류 표에서는 등록 시도가 실패했음을 나타냅니다. 아래 표에 나열된 디바이스는 또 다른 시도 중에 성공적으로 등록되었습니다. 실패한 시도 중 일부는 나열될 수 없습니다. 마이그레이션 정보는 일부 오류에 사용할 수 없습니다.

| 테이블 열 | 설명 |
|-------------|----------|
| 등록 시작 | 사용자가 먼저 등록을 시작한 시작 시간입니다. |
| OS | 디바이스 운영 체제 |
| OS 버전 | 디바이스 운영 체제 버전입니다. |
| 실패 | 오류의 원인입니다. |

### <a name="failure-details"></a>오류 세부 정보

오류 행을 선택하면 자세한 세부 정보가 제공됩니다.

| 섹션 | 설명 |
|-------------|----------|
| 오류 세부 정보 | 오류의 자세한 설명입니다. |
| 잠재적 수정 | 오류를 해결하기 위해 제안된 단계입니다. 일부 오류는 수정될 수 없습니다. |
| 리소스(선택 사항) | 조치를 취하기 위해 포털에 있는 추가 정보 또는 영역에 대한 링크입니다. |

### <a name="enrollment-errors"></a>등록 오류

| 오류 | 세부 정보 |
|-------------|----------|
| iOS 시간 제한 또는 오류 | 사용자 등록이 완료되는 데 너무 오래 걸렸기 때문에 발생한 디바이스와 Intune 간의 시간 제한입니다. |
| 사용자를 찾을 수 없음 또는 사용이 허가되지 않은 사용자 | 사용자에게 라이선스가 없거나 사용자가 서비스에서 제거되었습니다. |
| 이미 등록된 디바이스 | 사용자가 다른 사용자에 의해 등록된 디바이스에서 회사 포털을 사용하여 디바이스를 등록하려고 했습니다. |
| Intune에 온보딩되지 않음 | Intune MDM(모바일 디바이스 관리) 기관이 구성되지 않았을 때 등록이 시도되었습니다. |
| 등록 권한 부여 실패 | 이전 버전의 회사 포털을 사용하여 등록이 시도되었습니다. |
| 디바이스가 지원되지 않음 | 디바이스는 Intune 등록에 대한 최소 요구 사항을 충족하지 않습니다. |
| 등록 제한 사항을 충족하지 못함 | 이 등록은 관리자 구성 등록 제한 사항으로 인해 차단되었습니다. |
| 디바이스 버전이 너무 낮음 | 관리자가 더 높은 디바이스 버전을 요구하는 등록 제한을 구성했습니다. |
| 디바이스 버전이 너무 높음 | 관리자가 더 낮은 디바이스 버전을 요구하는 등록 제한을 구성했습니다. |
| 디바이스를 개인으로 등록할 수 없음 | 관리자가 개인 등록을 차단하는 등록 제한을 구성했으며, 실패한 디바이스가 회사로 미리 정의되지 않았습니다. |
| 디바이스 플랫폼이 차단됨 | 관리자가 이 디바이스의 플랫폼을 차단하는 등록 제한을 구성했습니다. |
| 대량 토큰이 만료되었음 | 프로비전 패키지의 대량 토큰이 만료되었습니다. |
| Autopilot 디바이스 또는 세부 정보를 찾지 못함 | 등록하려고 할 때 Autopilot 디바이스를 찾을 수 없습니다. |
| Autopilot 프로필을 찾지 못했거나 할당하지 않음 | 디바이스에 활성 Autopilot 프로필이 없습니다. |
| 예기치 않은 Autopilot 등록 방법 | 디바이스에서 허용되지 않는 방법을 사용하여 등록하려고 했습니다. |
| Autopilot 디바이스가 제거됨 | 등록하려고 하는 디바이스가 이 계정에 대한 Autopilot에서 제거되었습니다. |
| 디바이스 최대값 도달 | 이 등록은 관리자 구성 디바이스 제한 사항으로 인해 차단되었습니다. |
| Apple 온보딩 | 모든 iOS 디바이스는 Intune 내에서 누락되거나 만료된 Apple MDM 푸시 인증서로 인해 현재 등록에서 차단되었습니다. |
| 디바이스가 미리 등록되지 않음 | 회사 및 모든 개인 등록이 관리자에 의해 차단되므로 디바이스는 미리 등록되지 않았습니다. |
| 기능이 지원되지 않음 | 사용자가 Intune 구성과 호환되지 않는 메서드를 통해 등록하려고 시도했었을 수 있습니다. |

## <a name="collect-available-data-from-mobile-device"></a>모바일 디바이스에서 사용 가능한 데이터 수집

사용자의 디바이스 문제를 해결할 때 다음 리소스를 사용하여 디바이스 데이터를 수집할 수 있습니다.
  - [IT 관리자에게 iOS 등록 오류 보내기](/intune-user-help/send-errors-to-your-it-admin-ios)
  - [자세한 정보 로깅으로 회사 지원팀의 디바이스 문제 해결 돕기](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
  - [USB 케이블을 사용하여 회사 지원팀에 Android 로그 보내기](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [메일을 사용하여 IT 관리자에게 Android 진단 데이터 로그 보내기](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
  - [IT 관리자에게 Android 등록 오류 보내기](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>다음 단계

조직 디바이스의 역할, 모바일 앱 관리, 데이터 보호 작업을 정의하는 RBAC(역할 기반 관리 제어)에 대해 자세히 알아봅니다. 자세한 내용은 [Intune을 통한 RBAC(역할 기반 관리 제어)](/intune/role-based-access-control)를 참조하세요.

알려진 Microsoft Intune 문제를 알아봅니다. 자세한 내용은 [알려진 Microsoft Intune 문제](/intune/known-issues)를 참조하세요.

필요한 경우 도움을 받기 위해 지원 티켓을 만드는 방법을 알아봅니다. [지원 받기](/intune/get-support)
