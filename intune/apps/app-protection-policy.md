---
title: 앱 보호 정책 개요
titleSuffix: Microsoft Intune
description: Microsoft Intune 앱 보호 정책이 어떻게 회사 데이터를 보호하고 데이터 손실을 방지하는지 알아봅시다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c340ffaacad303c4ff395c84d92e3907e42a521
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036636"
---
# <a name="app-protection-policies-overview"></a>앱 보호 정책 개요

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

앱 보호 정책(APP)은 관리되는 앱에서 조직의 데이터를 안전하게 보호하거나 유지되도록 하는 규칙입니다. 정책은 사용자가 "회사" 데이터를 액세스하거나 이동하려고 할 때 적용되는 규칙이거나, 사용자가 앱 내에 있을 때 금지되거나 모니터링되는 일련의 작업일 수 있습니다. 관리되는 앱은 앱 보호 정책이 적용되어 있으며 Intune을 통해 관리할 수 있는 앱입니다.

MAM(모바일 애플리케이션 관리) 앱 보호 정책을 사용하면 애플리케이션 내에서 조직의 데이터를 관리하고 보호할 수 있습니다. 중요한 데이터를 포함하는 회사 또는 학교 관련 앱인 **등록 없는 MAM**(MAM-WE)는 **Bring-your-own-device**(BYOD) 시나리오의 개인 디바이스를 비롯한 거의 모든 [디바이스](app-management.md#app-management-capabilities-by-platform)에서 관리할 수 있습니다. Microsoft Office 앱과 같은 많은 생산성 앱은 Intune MAM에서 관리할 수 있습니다. 공개적으로 사용 가능한 공식적인 [Microsoft Intune 보호 앱](apps-supported-intune-apps.md) 목록을 참조하세요.

## <a name="how-you-can-protect-app-data"></a>앱 데이터를 보호하는 방법
직원은 개인 및 회사 작업 둘 다에 모바일 디바이스를 사용합니다. 직원의 생산성을 유지하는 동시에 의도했거나 의도하지 않은 데이터 손실을 방지하려고 합니다. 또한 사용자가 관리하지 않는 디바이스에서 액세스하는 회사 데이터를 보호하려고 합니다.

**MDM(모바일 디바이스 관리) 솔루션에 관계없이** Intune 앱 보호 정책을 사용할 수 있습니다. 이러한 독립성은 디바이스 관리 솔루션에 디바이스를 등록하거나 등록하지 않고 회사의 데이터를 보호하는 데 도움이 됩니다. **앱 수준 정책**을 구현하면 회사 리소스에 대한 액세스를 제한하고 IT 부서의 범위 내에 데이터를 유지할 수 있습니다.

### <a name="app-protection-policies-on-devices"></a>디바이스의 앱 보호 정책

앱 보호 정책은 다음 디바이스에서 실행되는 앱에 대해 구성할 수 있습니다.

- **Microsoft Intune에 등록:** 이러한 디바이스는 일반적으로 회사 소유입니다.

- **타사 MDM(모바일 디바이스 관리) 솔루션에 등록:** 이러한 디바이스는 일반적으로 회사 소유입니다.

  > [!NOTE]
  > 타사 모바일 앱 관리 또는 보안 컨테이너 솔루션에는 모바일 앱 관리 정책을 사용하면 안 됩니다.

- **모바일 디바이스 관리 솔루션에 등록되지 않음:** 이 디바이스는 일반적으로 직원이 소유한 디바이스로서 Intune 또는 기타 MDM 솔루션에서 관리 또는 등록되지 않습니다.

> [!IMPORTANT]
> Office 365 서비스에 연결되는 Office 모바일 앱에 대한 모바일 앱 관리 정책을 만들 수 있습니다. 하이브리드 모던 인증이 활성화된 iOS 및 Android용 Outlook의 Intune 앱 보호 정책을 생성하여 Exchange 온-프레미스 사서함에 대한 액세스를 보호할 수도 있습니다. 이 기능을 사용하기 전에 [iOS 및 Android 요구 사항에 대한 Outlook](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)을 충족하는지 확인합니다. 온-프레미스 Exchange 또는 SharePoint 서비스에 연결하는 다른 앱에는 앱 보호 정책이 지원되지 않습니다.

## <a name="benefits-of-using-app-protection-policies"></a>앱 보호 정책을 사용할 경우의 이점

앱 보호 정책을 사용할 경우의 중요한 이점은 다음과 같습니다.

- **앱 수준에서 회사 데이터 보호.** 모바일 앱 관리에는 디바이스 관리가 필요하지 않으므로 관리되는 디바이스와 관리되지 않는 디바이스 둘 다에서 회사 데이터를 보호할 수 있습니다. 관리는 사용자 ID를 중심으로 하며 디바이스 관리에 대한 요구 사항이 제거됩니다.

- **최종 사용자 생산성은 영향을 받지 않으며, 개인 컨텍스트에서 앱을 사용하는 경우 정책이 적용되지 않습니다.** 회사 컨텍스트에서만 정책이 적용되므로 개인 데이터를 변경하지 않고도 회사 데이터를 보호할 수 있습니다.

- **앱 보호 정책은 앱 계층 보호가 구현되었는지 확인합니다**. 예를 들어, 다음을 수행할 수 있습니다.
  - 업무용으로 앱을 열려면 PIN이 필요합니다. 
  - 앱 간의 데이터 공유를 제어합니다. 
  - 업무용 앱 데이터를 개인 스토리지 위치에 저장하지 못하게 합니다.

- **MDM은 MAM과 함께 디바이스가 보호되도록 합니다**. 예를 들어 디바이스 액세스 시 PIN을 요구하거나, 관리되는 앱을 디바이스에 배포할 수 있습니다. 앱 관리를 보다 강력하게 제어하기 위해 MDM 솔루션을 통해 디바이스에 앱을 배포할 수도 있습니다.

앱 보호 정책과 함께 MDM을 사용할 경우 추가적인 혜택이 있으며, 회사에서 앱 보호 정책을 MDM과 함께 사용하거나 MDM을 제외하고 사용할 수 있습니다. 예를 들어, 회사에서 지급한 휴대폰과 개인 태블릿을 모두 사용하는 직원을 생각해 보세요. 회사 휴대폰은 MDM에 등록되고 앱 보호 정책으로 보호되고 개인 태블릿은 앱 보호 정책으로만 보호됩니다.

디바이스 상태를 설정하지 않고 사용자에게 MAM 정책을 적용하면 BYOD 디바이스 및 Intune 관리형 디바이스에서 모두 사용자에게 MAM 정책이 적용됩니다. 관리 상태에 따라 MAM 정책을 적용할 수도 있습니다. 따라서 앱 보호 정책을 만들 때 **모든 앱 유형을 대상으로 함** 옆에서 **아니요**를 선택합니다. 그러고 나서, 다음 작업을 수행합니다.
- Intune 관리형 디바이스에 덜 엄격한 MAM 정책을 적용하고 MDM에 등록되지 않은 디바이스에 더 엄격한 MAM 정책을 적용합니다.
- 등록되지 않은 디바이스에만 MAM 정책을 적용합니다.

## <a name="supported-platforms-for-app-protection-policies"></a>앱 보호 정책을 지원하는 플랫폼

Intune은 앱을 실행하려는 디바이스에서 필요한 앱을 얻도록 도와주는 다양한 기능을 제공합니다. 자세한 내용은 [플랫폼별 앱 관리 기능](app-management.md#app-management-capabilities-by-platform)을 참조하십시오.

Intune 앱 보호 정책 플랫폼 지원은 Android 및 iOS 디바이스용 Office 모바일 애플리케이션 플랫폼 지원에 맞춰 조정됩니다. 자세한 내용은 [Office 시스템 요구 사항](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg)의 **모바일 앱** 섹션을 참조하세요.

> [!IMPORTANT]
> Android에서 앱 보호 정책을 받으려면 디바이스에 Intune 회사 포털이 필요합니다. 자세한 내용은 [Intune 회사 포털 액세스 앱 요구 사항](../fundamentals/end-user-mam-apps-android.md#access-apps)을 참조하세요.

## <a name="how-app-protection-policies-protect-app-data"></a>앱 보호 정책으로 앱 데이터를 보호하는 방법

### <a name="apps-without-app-protection-policies"></a>앱 보호 정책을 사용하지 않는 앱

앱을 제한 없이 사용하는 경우 회사 및 개인 데이터가 혼합될 수 있습니다. 업무용 데이터가 개인 스토리지와 같은 곳에 저장되거나 관리 범위를 벗어난 앱에 전송되어 손실될 수 있습니다. 다음 다이어그램에 있는 화살표는 회사와 및 개인 앱 간 및 스토리지 위치로의 무제한 데이터 이동을 표시합니다.

![배치된 정책이 없는 앱 간의 데이터 이동에 대한 개념 이미지](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>앱 보호 정책(APP)을 사용하여 데이터 보호

앱 보호 정책을 사용하여 회사 데이터가 디바이스의 로컬 스토리지에 저장되지 않도록 할 수 있습니다(아래 그림 참조). 앱 보호 정책으로 보호되지 않는 다른 앱으로 데이터 이동을 제한할 수도 있습니다. 앱 보호 정책 설정은 다음과 같습니다.
- **조직 데이터 복사본 저장**, **잘라내기, 복사, 붙여넣기 제한**과 같은 데이터 재배치 정책
- **액세스용 단순 PIN 필요** 및 **관리되는 앱이 탈옥 또는 루팅 상태의 디바이스에서 실행되지 않도록 차단**과 같은 액세스 정책 설정

![정책에 의해 보호되는 회사 데이터를 보여주는 개념 이미지](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>MDM 솔루션에서 관리되는 디바이스에서 APP로 데이터 보호

아래 그림은 MDM 및 앱 보호 정책이 함께 제공하는 보호 계층을 보여 줍니다.

![앱 보호 정책이 BYOD 디바이스에서 작동하는 방식을 보여 주는 이미지](./media/app-protection-policy/app-protection-policies-with-mdm.png)

MDM 솔루션은 다음을 제공하여 가치를 추가합니다.

- 디바이스 등록
- 디바이스에 앱 배포
- 지속적인 디바이스 규정 준수 및 관리 제공

앱 보호 정책은 다음을 제공하여 가치를 추가합니다.

- 회사 데이터가 소비자 앱과 서비스에 누출되지 않도록 보호
- *다른 이름으로 저장*, *클립보드* 또는 *PIN*과 같은 제한 사항을 클라이언트 앱에 적용
- 디바이스에서 해당 앱을 제거하지 않고 필요할 때 앱에서 회사 데이터 초기화

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>등록되지 않은 디바이스에 대해 APP으로 데이터 보호

다음 다이어그램은 MDM 없이 앱 수준에서 데이터 보호 정책이 작동하는 방식을 보여 줍니다.

![앱 보호 정책이 등록 없이 디바이스에서 작동하는 방식을 보여 주는 이미지(비관리형 디바이스)](./media/app-protection-policy/app-protection-policies-without-mdm.png)

MDM 솔루션에 등록되지 않은 BYOD 디바이스의 경우 앱 보호 정책을 통해 앱 수준에서 회사 데이터를 보호할 수 있습니다.
그러나 다음과 같은 몇 가지 제한 사항에 유의해야 합니다.

- 디바이스에 앱을 배포할 수 없습니다. 최종 사용자가 스토어에서 앱을 구입해야 합니다.
- 해당 디바이스에서 인증서 프로필을 프로비전할 수 없습니다.
- 이러한 디바이스에서 회사 Wi-Fi 및 VPN 설정을 프로비전할 수 없습니다.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>앱 보호 정책으로 관리할 수 있는 앱

[Intune SDK](../developer/app-sdk.md)와 통합되었거나 [Intune 앱 래핑 도구](../developer/apps-prepare-mobile-application-management.md)로 래핑된 모든 앱은 Intune 앱 보호 정책을 사용하여 관리할 수 있습니다. 이러한 도구를 사용하여 작성되었으며 공용으로 사용할 수 있는 [Microsoft Intune 보호 앱](apps-supported-intune-apps.md)의 공식 목록을 참조하세요.

Intune SDK 개발 팀에서는 네이티브 Android, iOS(Obj-C, Swift), Xamarin, Xamarin.Forms 및 Cordova 플랫폼으로 빌드된 앱을 적극적으로 테스트하고 해당 앱에 대한 지원을 유지합니다. 일부 고객은 React Native와 NativeScript 같은 다른 플랫폼과 Intune SDK 통합에 성공했지만, Microsoft는 지원되는 플랫폼 외에 다른 플랫폼을 사용하는 앱 개발자를 위한 명확한 지침이나 플러그 인을 제공하지 않습니다.

[Intune SDK](../developer/app-sdk.md)는 자사와 타사 버전 SDK 모두에 대해 [ADAL(Azure Active Directory Authentication Library)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)의 일부 고급 인증 기능을 사용합니다. 따라서 [MSAL(Microsoft Authenticiation Library)](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries)은 Intune 앱 보호 서비스 인증 및 조건부 실행과 같은 여러 핵심 시나리오에서 잘 작동하지 않습니다. Microsoft의 Identity 팀에서 제공하는 전반적인 지침이 모든 Microsoft Office 앱의 경우 MSAL로 전환하는 것임을 고려하면, [Intune SDK](../developer/app-sdk.md)는 결국 MSAL을 지원해야 하겠지만 현재로서는 계획이 없습니다.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>앱 보호 정책을 사용하기 위한 최종 사용자 요구 사항

다음 목록은 Intune 관리 앱에 대해 앱 보호 정책을 사용하기 위한 최종 사용자 요구 사항입니다.

- 최종 사용자에게 AAD(Azure Active Directory) 계정이 있어야 합니다. Azure Active Directory에서 Intune 사용자를 만드는 방법을 알아보려면 [Intune에 사용자 추가 및 관리 권한 부여](../fundamentals/users-add.md)를 참조하세요.

- 최종 사용자의 Azure Active Directory 계정에 Microsoft Intune 라이선스가 할당되어 있어야 합니다. 최종 사용자에게 Intune 라이선스를 할당하는 방법을 알아보려면 [Intune 라이선스 관리](../fundamentals/licenses-assign.md)를 참조하세요.

- 최종 사용자가 앱 보호 정책의 대상으로 지정된 보안 그룹에 속해야 합니다. 동일한 앱 보호 정책은 사용 중인 특정 앱을 대상으로 해야 합니다. [Azure Portal](https://portal.azure.com)의 Intune 콘솔에서 앱 보호 정책을 만들고 배포할 수 있습니다. 보안 그룹은 현재 [Microsoft 365 관리 센터](https://admin.microsoft.com)에서 만들 수 있습니다.

- 최종 사용자가 자신의 AAD 계정을 사용하여 앱에 로그인해야 합니다.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Microsoft Office 앱에 대한 앱 보호 정책

Microsoft Office 앱에서 앱 보호 정책을 사용하는 경우 알아야 할 몇 가지 추가 요구 사항이 있습니다.

### <a name="outlook-mobile-app"></a>Outlook 모바일 앱
[Outlook 모바일 앱](https://products.office.com/outlook) 사용에 대한 추가 요구 사항은 다음과 같습니다.

- 최종 사용자의 디바이스에 Outlook 모바일 앱이 설치되어 있어야 합니다.
- 최종 사용자의 Azure Active Directory 계정에 [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) 사서함 및 라이선스가 연결되어 있어야 합니다.

  >[!NOTE]
  > Outlook 모바일 앱은 현재 Microsoft Exchange Online용 만 Intune App Protection 및 [하이브리드 최신 인증을 사용하는 Exchange Server](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)만 지원하며 Office 365 전용 Exchange는 지원하지 않습니다.

### <a name="word-excel-and-powerpoint"></a>Word, Excel 및 PowerPoint
[Word, Excel 및 PowerPoint](https://products.office.com/business/office) 앱 사용을 위한 추가 요구 사항은 다음과 같습니다.

- 최종 사용자의 Azure Active Directory 계정에 [Office 365 Business 또는 Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) 라이선스가 연결되어 있어야 합니다. 구독에는 모바일 디바이스의 Office 앱이 포함되어야 하며 [비즈니스용 OneDrive](https://onedrive.live.com/about/business/)의 클라우드 스토리지 계정이 포함될 수 있습니다. 다음 [지침](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)에 따라 [Microsoft 365 관리 센터](https://admin.microsoft.com)에서 Office 365 라이선스를 할당받을 수 있습니다.

- 최종 사용자는 “조직 데이터 복사본 저장” 애플리케이션 보호 정책 설정에서 세분화된 저장을 기능으로 사용하여 구성된 관리 위치가 있어야 합니다. 예를 들어 관리 위치가 OneDrive인 경우 최종 사용자의 Word, Excel 또는 PowerPoint 앱에 [OneDrive](https://onedrive.live.com/about/) 앱이 구성되어 있어야 합니다.

- 관리 위치가 OneDrive인 경우 해당 앱이 최종 사용자에게 배포된 앱 보호 정책의 대상으로 지정되어야 합니다.

  >[!NOTE]
  > Office 모바일 앱은 현재 SharePoint Online만 지원하고 SharePoint 온-프레미스는 지원하지 않습니다.

### <a name="managed-location-needed-for-office"></a>Office에 필요한 관리되는 위치
Office에 관리되는 위치(예: OneDrive)가 필요합니다. Intune에서는 앱의 모든 데이터를 "회사" 또는 "개인"으로 표시합니다. 데이터는 비즈니스 위치에서 시작될 경우 "회사" 데이터로 간주됩니다. Office 앱의 경우 Intune은 전자 메일(Exchange) 또는 클라우드 스토리지(비즈니스용 OneDrive 계정이 있는 OneDrive 앱)를 비즈니스 위치로 간주합니다.

### <a name="skype-for-business"></a>비즈니스용 Skype
비즈니스용 Skype 사용에 대한 추가 요구 사항이 있습니다. [비즈니스용 Skype](https://products.office.com/skype-for-business/it-pros) 라이선스 요구 사항을 참조하세요. SfB(비즈니스용 Skype) 하이브리드 및 온-프레미스 구성에 대해서는 [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756)(SfB 및 Exchange의 하이브리드 최신 인증이 GA(일반 공급) 상태가 됨) 및 [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910)(AAD를 사용한 SfB 온-프레미스의 최신 인증)를 각각 참조하세요.

## <a name="app-protection-global-policy"></a>앱 보호 글로벌 정책

OneDrive 관리자가 **admin.onedrive.com**을 탐색하고 **디바이스 액세스**를 선택하는 경우 OneDrive 및 SharePoint 클라이언트 앱에 **모바일 애플리케이션 관리** 제어를 설정할 수 있습니다. 

OneDrive 관리자 콘솔에 사용 가능하게 만든 설정은 **글로벌** 정책이라는 특별한 Intune 앱 보호 정책을 구성합니다. 이 글로벌 정책은 테넌트의 모든 사용자에게 적용할 수 있으므로 정책 대상을 제어할 방법이 없습니다. 

사용하도록 설정되면 iOS 및 Android용 OneDrive 및 SharePoint 앱은 기본적으로 선택한 설정을 통해 보호됩니다. IT Pro는 대상 앱을 더 많이 추가하고, 모든 정책 설정을 수정할 수 있도록 Intune 콘솔에서 이 정책을 편집할 수 있습니다. 

기본적으로 테넌트당 한 개의 **글로벌** 정책만 있을 수 있습니다. 그러나 [Intune Graph API](../developer/intune-graph-apis.md)를 사용하여 테넌트당 추가 글로벌 정책을 만들 수 있지만 권장되지는 않습니다. 이러한 정책 구현의 문제 해결이 복잡해질 수 있으므로 추가 글로벌 정책 만들기는 권장되지 않습니다.

**글로벌** 정책이 테넌트의 모든 사용자에게 적용되는 반면, 모든 표준 Intune 앱 보호 정책은 이러한 설정을 재정의합니다.

## <a name="app-protection-features"></a>앱 보호 기능

### <a name="multi-identity"></a>다중 ID

다중 ID 지원을 사용하면 앱에서 여러 대상을 지원할 수 있습니다. 이러한 대상은 "회사" 사용자 및 "개인" 사용자입니다. 회사 및 학교 계정은 "회사" 대상에서 사용되는 반면 개인 계정은 Microsoft Office 사용자와 같은 소비자 대상에 사용됩니다. 다중 ID를 지원하는 앱은 공개적으로 해제할 수 있으며 앱 보호 정책은 앱이 회사 및 학교("회사") 컨텍스트에서 사용되는 경우에만 적용됩니다. 다중 ID 지원은 [Intune SDK](../developer/app-sdk.md)를 사용하여 앱에 로그인한 회사 또는 학교 계정에만 앱 보호 정책을 적용합니다. 개인 계정으로 앱에 로그인하면 이 데이터는 그대로 유지됩니다.

“개인” 컨텍스트의 예로 Word에서 새 문서를 시작하는 사용자를 고려합니다. 이는 개인 컨텍스트로 간주되므로 Intune 앱 보호 정책이 적용되지 않습니다. “회사” OneDrive 계정에 문서가 저장되면 이는 “회사” 컨텍스트로 간주되므로 Intune 앱 보호 정책이 적용됩니다.

“회사” 컨텍스트에 대한 예로써, 회사 계정을 사용하여 OneDrive 앱을 시작하는 사용자를 고려합니다. 업무용에서는 파일을 개인 스토리지 위치로 이동할 수 없습니다. 나중에 사용자가 개인 계정으로 OneDrive를 사용하는 경우 개인 OneDrive에서 제한 없이 데이터를 복사 및 이동할 수 있습니다.

Outlook에는 "개인" 및 "회사" 이메일 모두의 이메일 보기가 결합되어 있습니다. 이 경우 Outlook 앱은 시작 시 Intune PIN을 묻는 메시지를 표시합니다.

Intune의 다중 ID에 대한 자세한 내용은 [MAM 및 다중 ID](apps-supported-intune-apps.md)를 참조하세요.

### <a name="intune-app-pin"></a>Intune 앱 PIN

PIN(개인 식별 번호)은 올바른 사용자가 애플리케이션에서 조직의 데이터에 액세스하는지 확인하는 데 사용하는 암호입니다.

**PIN 프롬프트**<br>
사용자가 “회사” 데이터에 액세스하려고 하면 Intune에서 사용자의 앱 PIN을 묻는 메시지가 표시됩니다. Word, Excel 또는 PowerPoint와 같은 다중 ID 앱에서는 사용자가 "회사" 문서나 파일을 열려고 할 때 PIN을 묻는 메시지가 표시됩니다. [Intune 앱 래핑 도구](../developer/apps-prepare-mobile-application-management.md)를 사용하여 관리되는 기간 업무 앱 등의 단일 ID 앱에서는 [Intune SDK](../developer/app-sdk.md)에서 앱의 사용자 환경이 항상 "회사"라는 사실을 알고 있기 때문에 시작 시 PIN을 묻는 메시지가 표시됩니다.

**PIN 프롬프트 또는 회사 자격 증명 프롬프트, 빈도**<br>
IT 관리자는 Intune 관리 콘솔에서 Intune 앱 보호 정책 설정인 **다음 시간(분) 후에 액세스 요구 사항 다시 확인**을 정의할 수 있습니다. 이 설정은 디바이스에서 액세스 요구 사항을 확인하고 애플리케이션 PIN 화면 또는 회사 자격 증명 프롬프트가 다시 표시되기까지의 시간을 지정합니다. 그러나 사용자에게 표시되는 빈도에 영향을 미치는 PIN에 대한 중요한 세부 정보는 다음과 같습니다.

- **The PIN is shared among apps of the same publisher to improve usability**(유용성 향상을 위해 동일한 게시자의 앱 간에 PIN 공유):<br> iOS에서 **동일한 앱 게시자**의 모든 앱에서 하나의 앱 PIN을 공유합니다. 예를 들어 모든 Microsoft 앱은 동일한 PIN을 공유합니다. Android의 경우 하나의 앱 PIN이 모든 앱 간에서 공유됩니다.
- **디바이스 재부팅 후에 *다음 시간(분) 후에 액세스 요구 사항 다시 확인* 동작:**<br> 타이머는 다음번에 Intune 앱 PIN 또는 회사 자격 증명 프롬프트를 표시할 시기를 결정하는 비활성 시간(분)을 추적합니다. iOS에서 타이머는 디바이스 재부팅에 영향을 받지 않습니다. 따라서 디바이스 재부팅은 Intune PIN(또는 대상 회사 자격 증명) 정책을 사용하는 iOS 앱에서 사용자가 비활성화된 시간(분)에 영향을 주지 않습니다. Android에서는 타이머가 디바이스 재부팅 시 다시 설정됩니다. 따라서 Intune PIN(또는 회사 자격 증명) 정책을 사용하는 Android 앱은 **디바이스 재부팅 후** ‘다음 시간(분) 후에 액세스 요구 사항 다시 확인’ 설정 값에 상관없이 앱 PIN 또는 회사 자격 증명 프롬프트를 묻는 메시지를 표시합니다.  
- **PIN과 관련된 타이머의 롤링 특성:**<br> 앱(앱 A)에 액세스하기 위해 PIN을 입력하고 앱이 디바이스에서 전경(기본 입력 포커스)을 나가면, 타이머가 해당 PIN을 재설정합니다. 이 PIN을 공유하는 어떠한 앱(앱 B)도 타이머가 재설정되었기 때문에 사용자에게 PIN 입력을 요구하지는 않습니다. '다음 시간(분) 후에 액세스 요구 사항 다시 확인' 값이 다시 충족되면 메시지가 다시 나타납니다.

iOS 디바이스의 경우 PIN이 다른 게시자의 앱 간에 공유되는 경우에도 **다음 시간(분) 후에 액세스 요구 사항 다시 확인** 값이 주 입력 포커스가 아닌 앱에 다시 충족할 때 프롬프트가 다시 표시됩니다. 따라서 예를 들어 사용자에게 게시자 _X_의 앱 _A_와 게시자 _Y_의 앱 _B_가 있는 경우 이러한 두 앱은 동일한 PIN을 공유합니다. 사용자는 앱 _A_(전경)에 중점을 두고, 앱 _B_는 최소화됩니다. **다음 시간(분) 후에 액세스 요구 사항 다시 확인** 값이 충족되고 사용자가 앱 _B_로 전환한 후 PIN이 필요합니다.

  >[!NOTE]
  > 특히 자주 사용하는 앱의 경우 사용자의 액세스 요구 사항을 보다 자주 확인하려면(즉, PIN 프롬프트) ‘다음 시간(분) 후에 액세스 요구 사항 다시 확인’ 설정 값을 줄이는 것이 좋습니다.

**Outlook 및 OneDrive의 기본 제공 앱 PIN**<br>
Intune PIN은 비활성 타이머(**다음 시간(분) 후에 액세스 요구 사항 다시 확인** 값)를 기반으로 작동합니다. 따라서 Intune PIN 프롬프트는 기본적으로 앱 실행과 연결된 경우가 많은 Outlook 및 OneDrive용 기본 제공 앱 PIN 프롬프트와 별도로 표시됩니다. 사용자가 두 PIN 프롬프트를 동시에 받는 경우 Intune PIN이 우선적으로 표시되어야 합니다.

**Intune PIN 보안**<br>
PIN을 사용하면 올바른 사용자만 앱에서 조직의 데이터에 액세스할 수 있습니다. 따라서 최종 사용자는 해당 Intune 앱 PIN을 설정하거나 다시 설정하기 전에 회사 또는 학교 계정으로 로그인해야 합니다. 이 인증은 보안 토큰 교환을 통해 Azure Active Directory에 의해 처리되며 [Intune SDK](../developer/app-sdk.md)에 투명하게 공개되지 않습니다. 보안의 관점에서 회사 또는 학교 데이터를 보호하는 가장 좋은 방법은 암호화하는 것입니다. 암호화는 앱 PIN과 관련이 없으며 고유한 앱 보호 정책입니다.

**무차별 암호 대입 공격으로부터의 보호 및 Intune PIN**<br>
앱 PIN 정책의 일환으로, IT 관리자는 앱을 잠그기 전에 사용자가 PIN 인증을 시도할 수 있는 최대 횟수를 설정할 수 있습니다. 이 시도 횟수가 충족되면 [Intune SDK](../developer/app-sdk.md)는 앱에서 "회사" 데이터를 초기화할 수 있습니다.

**Intune PIN 및 선택적 초기화**<br>
iOS에서 앱 수준의 PIN 정보는 앱과 동일 게시자 간에 공유되는 키 집합에 저장됩니다(예: 모든 제1 당사자 Microsoft 앱). 이 PIN 정보는 최종 사용자 계정에도 연결됩니다. 한 앱의 선택적 초기화는 다른 앱에 영향을 주지 않아야 합니다. 

예를 들어 로그인한 사용자의 Outlook 설정 PIN은 공유된 키 집합에 저장됩니다. 사용자가 OneDrive에 로그인할 때는(Microsoft에서도 게시) 동일한 공유 키 집합을 사용하기 때문에 Outlook과 동일한 PIN이 표시됩니다. Outlook에서 로그아웃하거나 사용자 데이터를 초기화하는 경우 Intune SDK는 OneDrive에서 그 PIN을 계속 사용할 수 있으므로 해당 키 집합을 지우지 않습니다. 그와 같은 이유로 선택적 초기화에서는 공유된 키 집합(PIN 포함)이 지워지지 않습니다. 이러한 동작은 디바이스에 게시자의 앱이 하나만 존재할 때라도 동일하게 유지됩니다. 

PIN은 동일한 게시자의 앱 간에 공유되므로 단일 앱이 초기화되는 경우 Intune SDK는 동일 게시자의 디바이스에 다른 앱이 또 있는지의 여부를 알지 못합니다. 따라서 Intune SDK는 다른 앱에도 사용될 수 있다는 판단 하에 PIN을 지우지 않습니다. 일부 OS 정리 작업의 일환으로서 해당 게시자의 마지막 앱이 결국 제거될 때면 앱 PIN의 초기화가 필요할 것으로 예상됩니다.
 
일부 디바이스에서 PIN이 초기화되는 것으로 보일 경우엔 다음과 같은 상황이 발생할 수 있습니다. PIN이 ID와 연결되어 있으므로 초기화 이후 다른 계정에 사용자가 로그인되어 있다면 새 PIN을 입력하라는 메시지가 표시됩니다. 그러나 이전에 있던 계정으로 로그인하는 경우에는 키 집합에 이미 저장되어 있는 PIN을 사용하여 로그인할 수 있습니다.

**동일한 게시자의 앱에서 PIN을 두 번 설정하시겠습니까?**<br>
MAM(iOS)은 현재 영숫자 및 특수 문자를 사용하는 애플리케이션 수준 PIN('암호'라 함)을 허용합니다. 이 경우 [iOS용 Intune SDK](../developer/app-sdk-ios.md)를 통합하려면 애플리케이션(예: WXP, Outlook, Managed Browser, Yammer)이 참가해야 합니다. 이렇게 하지 않으면 대상 애플리케이션에 암호 설정이 제대로 적용되지 않습니다. 이는 iOS용 Intune SDK 버전 7.1.12에서 출시된 기능입니다.

이 기능을 지원하고 이전 버전의 iOS용 Intune SDK와 호환성을 보장하기 위해 7.1.12 이상의 모든 PIN(숫자 또는 암호)은 이전 SDK 버전의 숫자 PIN과 별도로 처리됩니다. 따라서 동일한 게시자의 iOS용 Intune SDK 7.1.12 이전 버전과 7.1.12 이상 버전을 사용하는 애플리케이션이 디바이스에 있는 경우 두 개의 PIN을 설정해야 합니다. 두 개의 PIN(각 앱용)은 어떤 방식으로든 서로 관련이 없습니다(즉, 앱에 적용되는 앱 보호 정책을 준수해야 합니다). 따라서 PIN과 관련하여 앱 A와 B에 동일한 정책이 적용되는 *경우에만* 사용자가 동일한 PIN을 두 번 설정할 수 있습니다. 

이 동작은 Intune 모바일 앱 관리에서 사용하도록 설정된 iOS 애플리케이션의 PIN과 관련이 있습니다. 시간이 지나 애플리케이션이 최신 버전의 iOS용 Intune SDK를 채택하면서 동일한 게시자의 앱에서 PIN을 두 번 설정해야 하는 문제는 완화됩니다. 예를 보려면 아래 참고를 참조하세요.

  >[!NOTE]
  > 예를 들어 앱 A는 7.1.12 이전 버전으로 빌드되고 앱 B는 동일한 게시자의 7.1.12 이상 버전으로 빌드된 경우, iOS 디바이스에 두 앱이 모두 설치되어 있으면 최종 사용자가 A와 B에 대해 별도로 PIN을 설정해야 합니다.
  > SDK 버전 7.1.9를 사용하는 앱 C가 디바이스에 설치되면 앱 A와 동일한 PIN을 공유합니다. 7.1.14를 사용하는 앱 D는 앱 B와 동일한 PIN을 공유하게 됩니다.  
  > 앱 A와 C만 디바이스에 설치된 경우 하나의 PIN만 설정하면 됩니다. 앱 B와 D만 디바이스에 설치된 경우에도 마찬가지입니다.

### <a name="app-data-encryption"></a>앱 데이터 암호화
IT 관리자는 앱 데이터 암호화를 요구하는 앱 보호 정책을 배포할 수 있습니다. 이러한 정책의 일환으로, IT 관리자는 콘텐츠가 암호화되는 경우를 지정할 수도 있습니다.

**Intune 데이터 암호화가 처리되는 방식**<br> 암호화 앱 보호 정책 설정에 대한 자세한 내용은 [Android 앱 보호 정책 설정](app-protection-policy-settings-android.md) 및 [iOS 앱 보호 정책 설정](app-protection-policy-settings-ios.md)을 참조하세요.

**암호화되는 데이터**<br>
IT 관리자의 앱 보호 정책에 따라 "회사"로 표시된 데이터만 암호화됩니다. 데이터는 비즈니스 위치에서 시작될 경우 "회사" 데이터로 간주됩니다. Office 앱의 경우 Intune은 다음을 비즈니스 위치로 간주합니다.

- 이메일(Exchange) 
- 클라우드 스토리지(비즈니스용 OneDrive 계정을 사용하는 OneDrive 앱)

[Intune 앱 래핑 도구](../developer/apps-prepare-mobile-application-management.md)에서 관리되는 기간 업무 앱의 경우 모든 앱 데이터가 “회사” 데이터로 간주됩니다.

### <a name="selective-wipe"></a>선택적 초기화

**원격으로 데이터 초기화**<br>
Intune은 다음 세 가지 방법으로 앱 데이터를 초기화할 수 있습니다. 
- 전체 디바이스 초기화
- MDM에 대한 선택적 초기화 
- MAM 선택적 초기화

MDM의 원격 초기화에 대한 자세한 내용은 [초기화 또는 사용 중지를 사용하여 디바이스 제거](../remote-actions/devices-wipe.md)를 참조하세요. MAM을 사용하는 선택적 초기화에 대한 자세한 내용은 [사용 중지 작업](../remote-actions/devices-wipe.md#retire) 및 [앱에서 회사 데이터만 초기화하는 방법](apps-selective-wipe.md)을 참조하세요.

[전체 디바이스 초기화](../remote-actions/devices-wipe.md)는 디바이스를 출하 시 기본 설정으로 복원하여 **디바이스**에서 모든 사용자 데이터 및 설정을 제거합니다. 그리고 디바이스가 Intune에서 제거됩니다.

  >[!NOTE]
  > 전체 디바이스 초기화, 그리고 MDM에 대한 선택적 초기화는 Intune MDM(모바일 디바이스 관리)에 등록된 디바이스에서만 수행할 수 있습니다.

**MDM에 대한 선택적 초기화**<br>
회사 데이터를 제거하는 방법에 대한 자세한 내용은 [디바이스 제거 -사용 중지](../remote-actions/devices-wipe.md#retire)를 참조하세요.

**MAM에 대한 선택적 초기화**<br>
MAM에 대한 선택적 초기화는 단순히 앱에서 업무용 앱 데이터를 제거합니다. 이 요청은 Intune Azure Portal 포털에서 시작됩니다. 초기화 요청을 시작하는 방법을 알아보려면 [앱에서 회사 데이터만 초기화하는 방법](apps-selective-wipe.md)을 참조하세요.

선택적 초기화가 시작된 상태로 앱을 사용하면 [Intune SDK](../developer/app-sdk.md)는 Intune MAM 서비스에서 선택적 초기화 요청을 30분 간격으로 확인합니다. 또한 사용자가 앱을 처음 시작하고 회사 또는 학교 계정으로 로그인할 때에도 선택적 초기화를 확인합니다.

**온-프레미스 서비스가 Intune 보호 앱에 작동하지 않을 때**<br>
Intune 앱 보호 기능은 애플리케이션과 [Intune SDK](../developer/app-sdk.md) 사이에서 일관되게 작동하기 위해 사용자의 ID에 의존합니다. 이를 보장하는 유일한 방법은 최신 인증뿐입니다. 앱이 온-프레미스 구성에 작동하는데도 일관되거나 보장되지 않는 시나리오가 있습니다.

**관리되는 앱에서 웹 링크를 안전하게 여는 방법**<br>
IT 관리자는 Intune을 사용하여 쉽게 관리할 수 있는 Microsoft Intune에서 개발된 웹 브라우저인 [Intune Managed Browser 앱](app-configuration-managed-browser.md)에 대한 앱 보호 정책을 배포 및 설정할 수 있습니다. IT 관리자는 Intune 관리 앱의 모든 웹 링크가 Managed Browser 앱을 사용하여 열리도록 지정할 수 있습니다.

## <a name="app-protection-experience-for-ios-devices"></a>iOS 디바이스에 대한 앱 보호 환경

### <a name="device-fingerprint-or-face-ids"></a>디바이스 지문 또는 얼굴 ID 
Intune 앱 보호 정책을 사용하면 Intune의 사용이 허가된 사용자에 대해서만 앱 액세스를 제어할 수 있습니다. 앱에 대한 액세스를 제어하는 한 가지 방법으로, 지원되는 디바이스에서 Apple의 Touch ID 또는 Face ID를 요구하는 방법이 있습니다. Intune은 디바이스의 생체 인식 데이터베이스에 변경 사항이 있는 경우 동작을 구현하며, Intune은 다음 비활성 시간 제한 값이 충족될 때 사용자에게 PIN을 요구하는 메시지를 표시합니다. 생체 인식 데이터의 변경 사항에는 지문 또는 얼굴의 추가나 제거가 포함됩니다. Intune 사용자에게 설정한 PIN이 없는 경우 Intune PIN 설정으로 안내됩니다.
 
이 프로세스의 목적은 앱 내의 조직 데이터를 앱 수준에서 보호하고 계속 안전하게 유지하기 위한 것입니다. 이 기능은 iOS에만 제공되고 iOS용 Intune SDK, 버전 9.0.1 이상을 통합하는 애플리케이션의 참여가 필요합니다. 대상 애플리케이션에 동작이 적용될 수 있도록 SDK의 통합이 필요합니다. 이 통합은 롤링 기반으로 특정 애플리케이션 팀에서 수행합니다. 참여하는 일부 앱에는 WXP, Outlook, Managed Browser 및 Yammer가 포함됩니다.
  
### <a name="ios-share-extension"></a>iOS 공유 확장
데이터 전송 정책이 **관리되는 앱만** 또는 **앱 없음**으로 설정된 경우에도 사용자가 iOS 공유 확장을 사용하여 관리되지 않는 앱에서 회사 또는 학교 데이터를 열 수 있습니다. Intune 앱 보호 정책은 디바이스를 관리하지 않고는 iOS 공유 확장을 제어할 수 없습니다. 따라서 Intune은 _**"회사" 데이터를 앱 외부에서 공유하기 전에 먼저 암호화합니다**_ . 관리되는 앱 외부에서 "회사" 파일 열기를 시도하여 이 암호화 동작의 유효성을 검사할 수 있습니다. 파일이 암호화되어야 하며, 관리되는 앱 외부에서 파일을 열 수 없어야 합니다.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>동일한 앱 및 사용자 집합에 대한 여러 Intune 앱 보호 액세스 설정
액세스에 대한 Intune 앱 보호 정책은 최종 사용자 디바이스가 회사 계정에서 대상 앱에 액세스하려 하기 때문에 지정된 순서에 따라 적용됩니다. 일반적으로 초기화가 우선 적용되고, 차단이 적용된 다음, 무시할 수 있는 경고가 적용됩니다. 예를 들어 특정 사용자/앱에 적용되는 경우 사용자의 액세스를 차단하는 최소 iOS 운영 체제 설정 적용 후 iOS 버전을 업그레이드하도록 사용자에게 경고하는 최소 iOS 운영 체제 설정이 적용됩니다. 따라서 IT 관리자가 최소 iOS 운영 체제를 11.0.0.0으로, 최소 iOS 운영 체제(경고에서만 해당)를 11.1.0.0으로 구성하는 반면 앱에 액세스하려는 디바이스는 iOS 10인 시나리오에서 최종 사용자는 결국 액세스 차단을 야기하는 최소 iOS 운영 체제에 대한 더 제한적인 설정을 기반으로 차단되게 됩니다.

다른 유형의 설정을 처리할 경우 Intune SDK 버전 요구 사항이 우선하고 이어 앱 버전 요구 사항, iOS 운영 체제 버전 요구 사항이 처리됩니다. 그런 다음, 동일한 순서로 설정의 모든 형식에 대한 모든 경고를 확인합니다. Intune SDK 버전 요구 사항은 필수 차단 시나리오의 경우 Intune 제품 팀의 안내에 따라 구성하는 것이 좋습니다.

## <a name="app-protection-experience-for-android-devices"></a>Android 디바이스에 대한 앱 보호 환경

### <a name="company-portal-app-and-intune-app-protection"></a>회사 포털 앱 및 Intune 앱 보호
많은 앱 보호 기능이 회사 포털 앱에 기본 제공됩니다. 회사 포털 앱이 항상 필요한 경우에도 디바이스 등록은 _필요하지 않습니다_. 등록 없는 모바일 앱 관리(MAM-WE)의 경우 최종 사용자가 회사 포털 앱을 디바이스에 설치해야 합니다.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>동일한 앱 및 사용자 집합에 대한 여러 Intune 앱 보호 액세스 설정
액세스에 대한 Intune 앱 보호 정책은 최종 사용자 디바이스가 회사 계정에서 대상 앱에 액세스하려 하기 때문에 지정된 순서에 따라 적용됩니다. 일반적으로 차단이 우선 적용된 다음, 무시할 수 있는 경고가 적용됩니다. 예를 들어 특정 사용자/앱에 적용되는 경우 사용자의 액세스를 차단하는 최소 Android 패치 버전 설정 적용 후 패치 업그레이드를 적용하도록 사용자에게 경고하는 최소 Android 패치 버전 설정이 적용됩니다. 따라서 IT 관리자가 최소 Android 패치 버전을 2018-03-01로, 최소 Android 패치 버전(경고에서만 해당)을 2018-02-01로 구성하는 반면 앱에 액세스하려는 디바이스의 패치 버전은 2018-01-01인 시나리오에서 최종 사용자는 결국 액세스 차단을 야기하는 최소 Android 패치 버전에 대한 더 제한적인 설정을 기반으로 차단되게 됩니다. 

다른 두 유형의 설정을 처리할 경우 앱 버전 요구 사항이 우선하고 이어 Android 운영 체제 버전 요구 사항 및 Android 패치 버전 요구 사항이 차례로 처리됩니다. 그런 다음, 동일한 순서로 설정의 모든 형식에 대한 모든 경고를 확인합니다.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Android 디바이스에 대한 Intune 앱 보호 정책 및 Google의 SafetyNet 증명 
Intune 앱 보호 정책은 최종 사용자 디바이스에 Android 디바이스의 Google SafetyNet 증명을 전달하도록 요구하는 기능을 관리자에게 제공합니다. 새 Google Play 서비스 결정 사항은 Intune 서비스에서 결정한 간격으로 IT 관리자에게 보고됩니다. 부하 때문에 서비스 호출 빈도가 제한되므로 이 값은 내부적으로 유지되며 구성할 수 없습니다. IT 관리자가 Google SafetyNet 증명 설정을 위해 구성한 작업은 조건부 시작 시 Intune 서비스에 마지막으로 보고된 결과에 따라 수행됩니다. 데이터가 없는 경우 다른 조건부 시작 검사가 실패하지 않으면 액세스가 허용되며, 증명 결과를 확인하기 위한 Google Play 서비스 "왕복"은 백 엔드에서 시작되고 디바이스가 실패하면 사용자에게 비동기적으로 메시지를 표시합니다. 부실 데이터가 있는 경우 마지막으로 보고된 결과에 따라 액세스가 차단 또는 허용되며, 마찬가지로 증명 결과를 확인하기 위한 Google Play 서비스 "왕복"은 백 엔드에서 시작되고 디바이스가 실패하면 사용자에게 비동기적으로 메시지를 표시합니다.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Android 디바이스에 대한 Intune 앱 보호 정책 및 Google의 앱 API 확인
Intune 앱 보호 정책은 최종 사용자 디바이스에 Android 디바이스의 Google 앱 확인 API를 통해 신호를 보내도록 요구하는 기능을 관리자에게 제공합니다. 이 작업을 수행하는 방법은 디바이스에 따라 조금씩 다릅니다. 일반적으로 Google Play 스토어로 이동하여 **내 앱 및 게임**을 클릭하고, 마지막 앱 검색 결과를 클릭하면 Play Protect로 이동됩니다. **디바이스의 보안 위협 검색**을 켭니다.

### <a name="googles-safetynet-attestation-api"></a>Google의 SafetyNet 증명 API 
Intune은 Google Play Protect SafetyNet API를 활용하여 등록되지 않은 디바이스에 대한 기존 루트 검색 검사를 추가합니다. Google은 루팅된 디바이스에서 앱을 실행하고 싶지 않은 개발자를 위해 Android 앱에 도입할 수 있는 이 API 세트를 개발하여 유지해 왔습니다. 예를 들어 Android Pay 앱에는 이 API가 통합되어 있습니다. Google이 발생하는 루트 검색 검사 전체를 공개적으로 공유하지는 않지만, 이 API가 디바이스를 루팅한 사용자를 찾아낼 수 있을 것으로 예상됩니다. 이렇게 찾아낸 사용자의 액세스를 차단하거나, 정책이 적용되는 앱에서 이러한 사용자의 회사 계정을 초기화할 수 있습니다. **기본 무결성 검사**는 디바이스의 일반 무결성에 대해 알려줍니다. 변조 흔적이 있는 루팅된 디바이스, 에뮬레이터, 가상 디바이스 및 디바이스는 기본 무결성을 실패합니다. **기본 무결성 및 인증된 디바이스 검사**는 Google 서비스를 사용하는 디바이스의 호환성을 알려줍니다. Google의 인증을 받은 수정되지 않은 디바이스만이 이 검사를 통과할 수 있습니다. 실패하는 디바이스는 다음과 같습니다.

- 기본 무결성에 실패하는 디바이스
- 부팅 로더의 잠금이 해제된 디바이스
- 사용자 지정 시스템 이미지/ROM을 사용하는 디바이스
- 제조업체가 Google 인증을 적용하지 않았거나 인증을 통과하지 못한 디바이스
- Android 오픈 소스 프로그램 원본 파일로 직접 빌드한 시스템 이미지를 사용하는 디바이스
- 베타/개발자 미리 보기 시스템 이미지를 사용하는 디바이스

기술 정보는 [SafetyNet 증명에 대한 Google 설명서](https://developer.android.com/training/safetynet/attestation)를 참조하세요.

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>SafetyNet 디바이스 증명 설정 및 ‘무단 해제된/루팅된 디바이스’ 설정
Google Play Protect의 SafetyNet API 검사를 수행하려면 적어도 증명 결과를 확인하기 위한 "왕복" 실행 시간 동안 최종 사용자가 온라인 상태여야 합니다. 최종 사용자가 오프라인 상태여도 IT 관리자는 여전히 **무단 해제된/루팅된 디바이스** 설정에서 결과를 얻을 것으로 예상할 수 있습니다. 즉, 최종 사용자가 너무 오래 오프라인 상태이면 **오프라인 유예 기간** 값이 작동하기 시작하고, 해당 타이머 값에 도달하면 네트워크를 사용할 수 있을 때까지 회사 또는 학교 데이터에 대한 모든 액세스가 차단됩니다. 두 설정을 모두 켜면 계층식 방법을 사용하여 최종 사용자 디바이스를 정상 상태로 유지할 수 있으며, 이는 최종 사용자가 모바일 디바이스로 회사 또는 학교 데이터에 액세스할 때 중요합니다.

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play 보호 API 및 Google Play 서비스
Google Play 보호 API를 활용하는 앱 보호 정책 설정을 적용하려면 Google Play 서비스가 작동해야 합니다. **SafetyNet 디바이스 증명**과 **앱에서 위협 검색** 설정 둘 다 정상적으로 작동하려면 Google에서 확인한 Google Play 서비스 버전이 필요합니다. 보안 영역에 속하는 이러한 설정 때문에 최종 사용자는 이러한 설정의 대상으로 지정되었는데 Google Play 서비스 버전 요구 사항을 충족하지 않거나 Google Play 서비스에 대한 액세스 권한이 없으면 차단됩니다.

## <a name="next-steps"></a>다음 단계

[Microsoft Intune으로 앱 보호 정책을 만들고 배포하는 방법](app-protection-policies.md)

[Microsoft Intune에서 사용 가능한 Android 앱 보호 정책 설정](app-protection-policy-settings-android.md)

[Microsoft Intune에서 사용 가능한 iOS 앱 보호 정책 설정](app-protection-policy-settings-ios.md)

## <a name="see-also"></a>참고 항목
Salesforce 모바일 앱과 같은 타사 앱은 Intune을 특정 방식으로 사용하여 회사 데이터를 보호합니다. 특히 Salesforce 앱이 Intune에서 작동하는 방식(MDM 앱 구성 설정 포함)에 대한 자세한 내용은 [Salesforce 앱 및 Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf)을 참조하세요.
