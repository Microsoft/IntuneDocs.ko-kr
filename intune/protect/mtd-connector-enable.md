---
title: Microsoft Intune에서 Mobile Threat Defense 커넥터 사용하도록 설정
titleSuffix: Microsoft Intune
description: Mobile Threat Defense(MTD) 파트너와 Microsoft Intune 간에 커넥터를 사용하도록 설정합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ac49edcd4ea71bdbc83cfa093f2bb5e42aefd54
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722074"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Intune에서 Mobile Threat Defense 커넥터를 사용하도록 설정

> [!NOTE] 
> 이 항목은 모든 Mobile Threat Defense 파트너에게 적용됩니다.

Mobile Threat Defense(MTD)를 설치하는 동안 MTD 파트너 콘솔에서 위협을 분류하기 위한 정책을 구성하고 Intune에서 디바이스 준수 정책을 만들었습니다. MTD 파트너 콘솔에서 Intune 커넥터를 이미 구성했다면 이제 Intune에서 MTD 파트너 애플리케이션의 MTD 연결을 사용할 수 있습니다.

Intune Mobile Threat Defense에 새 애플리케이션을 통합하고 Intune에 대한 연결을 사용하도록 설정하면 Intune은 Azure Active Directory에 클래식 조건부 액세스 정책을 만듭니다. [Defender ATP](advanced-threat-protection.md)나 추가 [MTD 파트너](mobile-threat-defense.md#mobile-threat-defense-partners)를 포함하여 통합되는 각 MTD 앱은 새 클래식 조건부 액세스 정책을 만듭니다. 이러한 정책은 무시할 수 있지만 편집 또는 삭제하거나 사용하지 않도록 설정할 수는 없습니다.

MTD 앱의 클래식 조건부 액세스 정책: 

- MTD 파트너와 통신하기 전에 Intune MTD에서 디바이스가 Azure AD에 등록되어 디바이스 ID를 받도록 요구하는 데 사용됩니다. ID가 있어야만 디바이스에서 Intune에 상태를 보고할 수 있습니다.  
- 다른 클라우드 앱 또는 리소스에는 영향을 주지 않습니다.  
- MTD 관리를 돕기 위해 만들 수 있는 조건부 액세스 정책과는 다릅니다.
- 기본적으로 평가에 사용하는 다른 조건부 액세스 정책은 조작하지 마세요.  

클래스 조건부 액세스 정책을 보려면 [Azure](https://portal.azure.com/#home)에서 **Azure Active Directory** > **조건부 정책** > **클래식 정책**으로 이동합니다.


## <a name="to-enable-the-mtd-connector"></a>MTD 커넥터를 사용하도록 설정하려면

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.

4. **Intune 대시보드**에서 **디바이스 준수**를 선택하고 **설치** 섹션 아래에서 **Mobile Threat Defense**를 선택합니다.

5. **Mobile Threat Defense** 창에서 **추가**를 선택합니다.

6. 드롭다운 목록에서 **설치할 Mobile Threat Defense 커넥터**로 MTD 솔루션을 선택합니다.

    ![Intune Azure Portal의 MTD 설치](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. 조직의 요구 사항에 따라 전환 옵션을 사용하도록 설정합니다. 표시되는 설정/해제 옵션은 MTD 파트너에 따라 다릅니다.

## <a name="mtd-toggle-options"></a>MTD 설정/해제 옵션

조직의 요구 사항에 따라 사용 하도록 설정해야 하는 MTD 설정/해제 옵션을 결정할 수 있습니다. 아래에 자세한 내용이 나와 있습니다.

- **Android 4.1+ 디바이스를 [MTD 파트너 이름] for Work MTD에 연결**: 이 옵션을 사용하도록 설정하는 경우 Android 4.1 이상 디바이스가 보안 위험을 Intune에 다시 보고하도록 지정할 수 있습니다.
  - **수신된 데이터가 없는 경우 비규격으로 표시**: Intune이 MTD 파트너로부터 이 플랫폼에 대한 데이터를 받지 못한 경우 해당 디바이스를 비규격으로 간주합니다.
<br></br>
- **iOS 8.0+ 디바이스를 [MTD 파트너 이름] for Work MTD에 연결**: 이 옵션을 사용하도록 설정하면 iOS 8.0+ 디바이스가 보안 위험을 Intune에 보고하게 할 수 있습니다.
  - **수신된 데이터가 없는 경우 비규격으로 표시**: Intune이 MTD 파트너로부터 이 플랫폼에 대한 데이터를 받지 못한 경우 해당 디바이스를 비규격으로 간주합니다.
<br></br>
- **iOS 디바이스에 대해 앱 동기화 사용**: 이 Mobile Threat Defense 파트너가 위협 분석 목적으로 사용할 iOS 애플리케이션의 메타데이터를 Intune에서 요청하도록 합니다.

- **지원되지 않은 OS 버전 차단**: 디바이스가 지원되는 최소 버전보다 낮은 운영 체제를 실행 중인 경우 차단합니다.

- **파트너가 응답하지 않을 때까지 기간(일)** : 연결이 끊어져서 Intune에서 파트너가 응답하지 않는 것으로 간주할 때까지의 비활성 상태 기간(일)입니다. Intune은 응답하지 않는 MTD 파트너에 대한 준수 상태를 무시합니다.

> [!IMPORTANT] 
> 가능하다면 디바이스 규정 준수 및 조건부 액세스 정책 규칙을 만들기 전에 MTD 앱을 추가하고 할당하는 것이 좋습니다. 이렇게 하면 MTD 앱이 최종 사용자가 설치할 수 있는 상태로 준비되어 최종 사용자가 이메일과 기타 회사 리소스에 액세스할 수 있습니다.

> [!TIP]
> Mobile Threat Defense 창서 Intune과 MTD 파트너 간의 **연결 상태** 및 **마지막 동기화** 시간을 확인할 수 있습니다.