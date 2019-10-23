---
title: Microsoft Intune-Azure를 사용해 Windows 디바이스에서 암호 재설정 | Microsoft Docs
description: Windows 디바이스에서 암호를 재설정하려면 Microsoft Pin 재설정 서비스 및 Microsoft Pin 재설정 클라이언트를 설치하고 Azure AD 디렉토리 ID를 사용하여 디바이스 정책을 만든 다음, Microsoft Intune을 사용하여 Azure Portal에서 암호를 재설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 445737a1b0a72e380844af6225cdb735cd3ec02c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509360"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>Intune을 사용하여 Windows 디바이스의 암호 재설정

Windows 디바이스에 대한 암호를 재설정할 수 있습니다. 암호 재설정 기능은 Microsoft PIN 재설정 서비스를 사용하여 Windows 10 Mobile을 실행하는 디바이스에 대한 새 암호를 생성할 수 있습니다. 

## <a name="supported-platforms"></a>지원되는 플랫폼

- 크리에이터스 업데이트 이상을 실행하는 Windows 10 Mobile(Azure AD 조인)

지원되는 **않는** 플랫폼은 다음과 같습니다.
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>PIN 재설정 서비스 권한 부여

Windows 디바이스에서 암호를 재설정하려면 PIN 재설정 서비스를 Intune 테넌트에 등록합니다.

1. [Microsoft PIN 재설정 서비스 프로덕션](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent)으로 이동해 테넌트 관리자 계정에 로그인합니다.
2. PIN 재설정 서비스의 사용자 계정 액세스에 대한 동의를 **수락**합니다. ![사용 권한에 대한 PIN 재설정 서버 요청 수락](./media/device-windows-pin-reset/pin-reset-service-home-screen.png)
3. [Microsoft PIN 재설정 클라이언트 프로덕션](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent)으로 이동해 테넌트 관리자 계정에 로그인합니다. PIN 재설정 클라이언트의 사용자 계정 액세스에 대한 동의를 **수락**합니다.
4. [Azure Portal](https://portal.azure.com)에서 PIN 재설정 서비스가 엔터프라이즈 애플리케이션(모든 애플리케이션)에 나열되어 있는지 확인합니다. ![PIN 재설정 서비스 사용 권한 페이지](./media/device-windows-pin-reset/pin-reset-service-application.png)

> [!NOTE]
> PIN 재설정 요청을 수락한 후 `Page not found` 메시지를 가져오거나 아무 일도 일어나지 않은 것처럼 나타날 수 있습니다. 이 동작은 정상입니다. 해당 테넌트에 대해 두 개의 PIN 재설정 애플리케이션이 표시되어 있는지 확인해야 합니다.

## <a name="configure-windows-devices-to-use-pin-reset"></a>PIN 재설정을 사용하도록 Windows 디바이스 구성

관리하는 Windows 디바이스에서 PIN 재설정을 구성하려면 [Intune Windows 10 사용자 지정 디바이스 정책](../configuration/custom-settings-windows-10.md)을 사용합니다. 다음 Windows 정책 CSP(구성 서비스 공급자)를 사용하여 정책을 구성합니다.

**디바이스 정책 사용** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

*테넌트 ID*를 [Azure Portal](https://portal.azure.com)에서 Azure Active Directory의 **속성**에 표시되어 있는 Azure AD 디렉터리 ID로 교체합니다.

이 CSP의 값을 **True**로 설정합니다.

> [!TIP]
> 정책을 만든 후 그룹에 할당(또는 배포)합니다. 해당 정책을 사용자 그룹 또는 디바이스 그룹에 할당할 수 있습니다. 사용자 그룹에 할당하는 경우 해당 그룹에 IOS 같은 다른 디바이스를 소유한 사용자가 포함될 수 있습니다. 기술적으로 해당 정책은 적용되지 않지만 이러한 디바이스는 상태 세부 정보에 포함됩니다.

## <a name="reset-the-passcode"></a>암호 재설정

1. [Azure 포털](https://portal.azure.com)에 로그인합니다. 
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **디바이스**를 선택한 다음, **모든 디바이스**를 선택합니다.
4. 암호를 재설정하려는 디바이스를 선택합니다. 디바이스 속성에서 **새 암호**를 선택합니다.
5. **예**를 선택하여 확인합니다. 암호가 생성되고 다음 7일 동안 포털에 표시됩니다.

## <a name="next-step"></a>다음 단계

암호 재설정에 실패하면 자세한 정보를 제공하는 포털에 링크가 제공됩니다.
