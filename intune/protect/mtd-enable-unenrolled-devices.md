---
title: 등록되지 않은 디바이스에 Mobile Threat Defense 커넥터를 사용하도록 설정
titleSuffix: Microsoft Intune
description: Microsoft Intune에서 등록되지 않은 디바이스에 Mobile Threat Defense 커넥터를 사용하도록 설정
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2744a27a733824bab9d920f4de0b49e951c1c34
ms.sourcegitcommit: a4c7339ec9ff5b1b846cb3cca887cf91b5cd4baa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627634"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Intune에서 등록되지 않은 디바이스에 Mobile Threat Defense 커넥터를 사용하도록 설정

MTD(Mobile Threat Defense)를 설치하는 동안 Mobile Threat Defense 파트너 콘솔에서 위협을 분류하기 위한 정책을 구성하고 Intune에서 앱 보호 정책을 만들었습니다. MTD 파트너 콘솔에서 Intune 커넥터를 이미 구성했다면 이제 Intune에서 MTD 파트너 애플리케이션의 MTD 연결을 사용할 수 있습니다.

> [!NOTE] 
> 이 문서는 앱 보호 정책을 지원하는 모든 Mobile Threat Defense 파트너에게 적용됩니다. Better Mobile(Android), Zimperium(iOS), Lookout for Work(Android/iOS).

## <a name="to-enable-the-mtd-connector"></a>MTD 커넥터를 사용하도록 설정하려면

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.

2. **Intune 대시보드**에서 **디바이스 준수**를 선택하고 **설치** 섹션 아래에서 **Mobile Threat Defense**를 선택합니다.

3. **Mobile Threat Defense** 창에서 **추가**를 선택합니다.

4. 드롭다운 목록에서 **설치할 Mobile Threat Defense 커넥터**로 MTD 솔루션을 선택합니다.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. 조직의 요구 사항에 따라 전환 옵션을 사용하도록 설정합니다. 표시되는 설정/해제 옵션은 MTD 파트너에 따라 다릅니다.

## <a name="mtd-toggle-options"></a>MTD 설정/해제 옵션

조직의 요구 사항에 따라 사용 하도록 설정해야 하는 MTD 설정/해제 옵션을 결정할 수 있습니다. 아래에 자세한 내용이 나와 있습니다.

**앱 보호 정책 설정**
- **앱 보호 정책 평가를 위해 *\<MTD 파트너 이름>* 에 Android 디바이스 버전 4.4 이상 연결**: 이 옵션을 사용하도록 설정하면 디바이스 위협 수준 규칙을 사용하는 앱 보호 정책이 이 커넥터의 데이터를 포함하여 디바이스를 평가합니다.
- **앱 보호 정책 평가를 위해 *\<MTD 파트너 이름>* 에 iOS 디바이스 버전 11 이상 연결**: 이 옵션을 사용하도록 설정하면 디바이스 위협 수준 규칙을 사용하는 앱 보호 정책이 이 커넥터의 데이터를 포함하여 디바이스를 평가합니다.

**일반 공유 설정**
- **파트너가 응답하지 않을 때까지 기간(일)** : 연결이 끊어져서 Intune에서 파트너가 응답하지 않는 것으로 간주할 때까지의 비활성 상태 기간(일)입니다. Intune은 응답하지 않는 MTD 파트너에 대한 준수 상태를 무시합니다.

> [!TIP]
> Mobile Threat Defense 창서 Intune과 MTD 파트너 간의 **연결 상태** 및 **마지막 동기화** 시간을 확인할 수 있습니다.

> [!NOTE] 
> Intune에 대한 Mobile Threat Defense 연결을 사용하도록 설정하면 Intune은 Azure Active Directory에서 클래식 조건부 액세스 정책을 만듭니다. [Defender ATP](advanced-threat-protection.md)나 추가 [MTD 파트너](mobile-threat-defense.md#mobile-threat-defense-partners)를 포함하여 통합되는 각 MTD 앱은 새 클래식 조건부 액세스 정책을 만듭니다. **이 정책은 무시할 수 있지만 편집 또는 삭제하거나 사용 안 함으로 설정할 수 없습니다.**
> 
> MTD 앱의 클래식 조건부 액세스 정책: 
> - MTD 파트너와 통신하기 전에 Intune MTD에서 디바이스가 Azure AD에 등록되어 디바이스 ID를 받도록 요구하는 데 사용됩니다. ID가 있어야만 디바이스에서 Intune에 상태를 보고할 수 있습니다.  
> - 다른 클라우드 앱 또는 리소스에는 영향을 주지 않습니다.  
> - MTD 관리를 돕기 위해 또는 앱 보호 CA 필요에 대해 만들 수 있는 조건부 액세스 정책과는 다릅니다.
> - 기본적으로 평가에 사용하는 다른 조건부 액세스 정책은 조작하지 마세요.  
>
> 클래스 조건부 액세스 정책을 보려면 [Azure](https://portal.azure.com/#home)에서 **Azure Active Directory** > **조건부 정책** > **클래식 정책**으로 이동합니다.

## <a name="next-steps"></a>다음 단계

- [Intune을 사용하여 MTD(Mobile Threat Defense) 앱 보호 정책을 만듭니다](~/protect/mtd-app-protection-policy.md).
