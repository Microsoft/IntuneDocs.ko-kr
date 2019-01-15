---
title: 앱 보호 정책이란?
titleSuffix: Microsoft Intune
description: Microsoft Intune 앱 보호 정책이 어떻게 회사 데이터를 보호하고 데이터 손실을 방지하는지 알아봅시다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: b6ebc3db81b969d83bc22034057ab4217e90931f
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297284"
---
# <a name="what-are-app-protection-policies"></a>앱 보호 정책이란?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune 앱 보호 정책은 회사 데이터를 보호하고 데이터 손실을 방지하도록 도와줍니다.

## <a name="how-you-can-protect-app-data"></a>앱 데이터를 보호하는 방법
직원은 개인 및 회사 작업 둘 다에 모바일 디바이스를 사용합니다. 직원의 생산성을 유지하는 동시에 의도했거나 의도하지 않은 데이터 손실을 방지하려고 합니다. 또한 사용자가 관리하지 않는 디바이스에서 액세스하는 회사 데이터를 보호하려고 합니다.

**MDM(모바일 장치 관리) 솔루션에 관계없이** Intune 앱 보호 정책을 사용할 수 있습니다. 이러한 독립성은 디바이스 관리 솔루션에 디바이스를 등록하거나 등록하지 않고 회사의 데이터를 보호하는 데 도움이 됩니다. **앱 수준 정책**을 구현하면 회사 리소스에 대한 액세스를 제한하고 IT 부서의 범위 내에 데이터를 유지할 수 있습니다.

앱 보호 정책은 다음 디바이스에서 실행되는 앱에 대해 구성할 수 있습니다.

- **Microsoft Intune에 등록:** 이러한 디바이스는 일반적으로 회사 소유입니다.

- **타사 MDM(모바일 디바이스 관리) 솔루션에 등록:** 이러한 디바이스는 일반적으로 회사 소유입니다.

  > [!NOTE]
  > 타사 모바일 앱 관리 또는 보안 컨테이너 솔루션에는 모바일 앱 관리 정책을 사용하면 안 됩니다.

- **모바일 디바이스 관리 솔루션에 등록되지 않음:** 이 디바이스는 일반적으로 직원이 소유한 디바이스로 Intune 또는 기타 MDM 솔루션에서 관리 또는 등록되지 않습니다.

> [!IMPORTANT]
> Office 365 서비스에 연결되는 Office 모바일 앱에 대한 모바일 앱 관리 정책을 만들 수 있습니다. 하이브리드 모던 인증이 활성화된 iOS 및 Android용 Outlook의 Intune 앱 보호 정책을 생성하여 Exchange 온-프레미스 사서함에 대한 액세스를 보호할 수도 있습니다. 이 기능을 사용하기 전에 [iOS 및 Android 요구 사항에 대한 Outlook](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)을 충족하는지 확인합니다. 온-프레미스 Exchange 또는 SharePoint 서비스에 연결하는 다른 앱에는 앱 보호 정책이 지원되지 않습니다.

**앱 보호 정책을 사용할 경우의 중요한 혜택은 다음과 같습니다.**

-   앱 수준에서 회사 데이터 보호. 모바일 앱 관리에는 디바이스 관리가 필요하지 않으므로 관리되는 디바이스와 관리되지 않는 디바이스 둘 다에서 회사 데이터를 보호할 수 있습니다. 관리는 사용자 ID를 중심으로 하며 디바이스 관리에 대한 요구 사항이 제거됩니다.

-   최종 사용자 생산성은 영향을 받지 않으며, 개인 컨텍스트에서 앱을 사용하는 경우 정책이 적용되지 않습니다. 회사 컨텍스트에서만 정책이 적용되므로 개인 데이터를 변경하지 않고도 회사 데이터를 보호할 수 있습니다.

앱 보호 정책과 함께 MDM을 사용할 경우 추가적인 혜택이 있으며, 회사에서 앱 보호 정책을 MDM과 함께 사용하거나 MDM을 제외하고 사용할 수 있습니다. 예를 들어, 회사에서 지급한 휴대폰과 개인 태블릿을 모두 사용하는 직원을 생각해 보세요. 회사 휴대폰은 MDM에 등록되고 앱 보호 정책으로 보호되고 개인 태블릿은 앱 보호 정책으로만 보호됩니다.

- **MDM은 디바이스가 보호되도록 합니다**. 예를 들어 디바이스 액세스 시 PIN을 요구하거나, 관리되는 앱을 디바이스에 배포할 수 있습니다. 앱 관리를 보다 강력하게 제어하기 위해 MDM 솔루션을 통해 디바이스에 앱을 배포할 수도 있습니다.

- **앱 보호 정책은 앱 계층 보호가 구현되었는지 확인합니다**. 예를 들어, 다음을 수행할 수 있습니다.
  - 업무용으로 앱을 열려면 PIN이 필요합니다. 
  - 앱 간의 데이터 공유를 제어합니다. 
  - 업무용 앱 데이터를 개인 스토리지 위치에 저장하지 못하게 합니다.


### <a name="supported-platforms-for-app-protection-policies"></a>앱 보호 정책을 지원하는 플랫폼
Intune 앱 보호 정책 플랫폼 지원은 Android 및 iOS 디바이스용 Office 모바일 애플리케이션 플랫폼 지원에 맞춰 조정됩니다. 자세한 내용은 [Office 시스템 요구 사항](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg)의 **모바일 앱** 섹션을 참조하세요.

Windows 디바이스는 현재 지원되지 않습니다. 그러나 유사한 기능을 제공하는 Windows Information Protection을 사용할 수 있습니다. 자세한 내용은 [WIP(Windows Information Protection)를 사용하여 엔터프라이즈 데이터 보호](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)를 참조하세요.


## <a name="how-app-protection-policies-protect-app-data"></a>앱 보호 정책으로 앱 데이터를 보호하는 방법

#### <a name="apps-without-app-protection-policies"></a>앱 보호 정책을 사용하지 않는 앱

![배치된 정책이 없는 앱 간의 데이터 이동에 대한 개념 이미지](./media/apps-without-protection-policies.png)

앱을 제한 없이 사용하는 경우 회사 및 개인 데이터가 혼합될 수 있습니다. 업무용 데이터가 개인 스토리지와 같은 곳에 저장되거나 관리 범위를 벗어난 앱에 전송되어 손실될 수 있습니다. 이전 다이어그램에 있는 화살표는 회사와 및 개인 앱 간 및 스토리지 위치로의 무제한 데이터 이동을 표시합니다.


### <a name="data-protection-with-app-protection-policies"></a>앱 보호 정책을 사용하여 앱 보호

![정책에 의해 보호되는 회사 데이터를 보여주는 개념 이미지](./media/apps-with-protection-policies.png)


앱 보호 정책을 사용하여 회사 데이터가 장치의 로컬 스토리지에 저장되지 않도록 할 수 있습니다. 앱 보호 정책으로 보호되지 않는 다른 앱으로 데이터 이동을 제한할 수도 있습니다. 앱 보호 정책 설정은 다음과 같습니다.
- **다른 이름으로 저장 차단** 및 **잘라내기, 복사 및 붙여넣기 제한**과 같은 데이터 재배치 정책
- **액세스용 단순 PIN 필요** 및 **관리되는 앱이 탈옥 또는 루팅 상태의 디바이스에서 실행되지 않도록 차단**과 같은 액세스 정책 설정

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mobile-device-management-solution"></a>모바일 디바이스 관리 솔루션에서 관리하는 디바이스에서 앱 보호 정책으로 데이터 보호

![앱 보호 정책이 BYOD 디바이스에서 작동하는 방식을 보여 주는 이미지](./media/app-protection-policies-with-mdm.png)

**MDM 솔루션에 등록된 디바이스의 경우**-

이전 그림은 MDM 및 앱 보호 정책이 함께 제공하는 보호 계층을 보여 줍니다.

MDM 솔루션에서 다음을 수행합니다.

-   디바이스 등록

-   디바이스에 앱 배포

-   지속적인 디바이스 규정 준수 및 관리 제공

**앱 보호 정책의 이점:**

-   회사 데이터가 소비자 앱과 서비스에 누출되지 않도록 보호

-   ‘다른 이름으로 저장’, ‘클립보드’ 또는 *PIN*과 같은 제한 사항을 클라이언트 앱에 적용

-   디바이스에서 해당 앱을 제거하지 않고 앱에서 회사 데이터 초기화


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>등록되지 않은 디바이스에 대해 앱 보호 정책으로 데이터 보호

![앱 보호 정책이 관리되는 디바이스에서 작동하는 방식을 보여 주는 이미지](./media/app-protection-policies-without-mdm.png)

이전 다이어그램은 MDM 없이 앱 수준에서 데이터 보호 정책이 작동하는 방식을 보여 줍니다.

MDM 솔루션에 등록되지 않은 BYOD 디바이스의 경우 앱 보호 정책을 통해 앱 수준에서 회사 데이터를 보호할 수 있습니다.
그러나 다음과 같은 몇 가지 제한 사항에 유의해야 합니다.

-   디바이스에 앱을 배포할 수 없습니다. 최종 사용자가 스토어에서 앱을 구입해야 합니다.

-   해당 디바이스에서 인증서 프로필을 프로비전할 수 없습니다.

-   이러한 디바이스에서 회사 Wi-Fi 및 VPN 설정을 프로비전할 수 없습니다.

## <a name="app-protection-global-policy"></a>앱 보호 글로벌 정책

OneDrive 관리자가 **admin.office.com**을 탐색하고 **장치** 액세스를 선택하는 경우 OneDrive 및 SharePoint 클라이언트 앱에 **모바일 애플리케이션 관리** 제어를 설정할 수 있습니다. 

OneDrive 관리자 콘솔에 사용 가능하게 만든 설정은 **글로벌** 정책이라는 특별한 Intune 앱 보호 정책을 구성합니다. 이 글로벌 정책은 테넌트의 모든 사용자에게 적용할 수 있으므로 정책 대상을 제어할 방법이 없습니다. 

사용하도록 설정되면 iOS 및 Android용 OneDrive 및 SharePoint 앱은 기본적으로 선택한 설정을 통해 보호됩니다. IT Pro는 대상 앱을 더 많이 추가하고, 모든 정책 설정을 수정할 수 있도록 Intune 콘솔에서 이 정책을 편집할 수 있습니다. 

기본적으로 테넌트당 한 개의 **글로벌** 정책만 있을 수 있습니다. 그러나 [Intune Graph API](intune-graph-apis.md)를 사용하여 테넌트당 추가 글로벌 정책을 만들 수 있지만 권장되지는 않습니다. 이러한 정책 구현의 문제 해결이 복잡해질 수 있으므로 추가 글로벌 정책 만들기는 권장되지 않습니다.

**글로벌** 정책이 테넌트의 모든 사용자에게 적용되는 반면, 모든 표준 Intune 앱 보호 정책은 이러한 설정을 재정의합니다.


## <a name="multi-identity"></a>다중 ID

다중 ID를 지원하는 앱을 사용하면 앱이 업무용으로 사용되는 경우 앱 보호 정책이 적용되는 동안 다른 계정(회사 및 개인)을 사용하여 동일한 앱에 액세스할 수 있습니다.

개인 컨텍스트의 예로 Word에서 새 문서를 시작하는 사용자를 고려합니다. 이는 개인 컨텍스트로 간주되므로 Intune 앱 보호 정책이 적용되지 않습니다. 회사 OneDrive 계정에 문서가 저장되면 이는 회사 컨텍스트로 간주되므로 Intune 앱 보호 정책이 적용됩니다.

회사 컨텍스트는 예로 회사 계정을 사용하여 OneDrive 앱을 시작하는 사용자를 고려합니다. 업무용에서는 파일을 개인 스토리지 위치로 이동할 수 없습니다. 나중에 사용자가 개인 계정으로 OneDrive를 사용하는 경우 개인 OneDrive에서 제한 없이 데이터를 복사 및 이동할 수 있습니다.

- Intune을 통해 [MAM 및 다중 ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)를 지원하는 앱에 대해 자세히 알아봅니다.

## <a name="next-steps"></a>다음 단계

[Microsoft Intune으로 앱 보호 정책을 만들고 배포하는 방법](app-protection-policies.md)

## <a name="see-also"></a>참고 항목
Salesforce 모바일 앱과 같은 타사 앱은 Intune을 특정 방식으로 사용하여 회사 데이터를 보호합니다. 특히 Salesforce 앱이 Intune에서 작동하는 방식(MDM 앱 구성 설정 포함)에 대한 자세한 내용은 [Salesforce 앱 및 Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf)을 참조하세요.
