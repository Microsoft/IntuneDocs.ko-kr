---
title: Microsoft Intune의 앱 관리란?
titleSuffix: ''
description: Microsoft Intune의 플랫폼별 클라이언트 앱 관리 기능에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b630709646b2f4489cbfea6284689c9436798ca
ms.sourcegitcommit: 78f9750712c254d8b123ef15b74f30ca999aa128
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71916357"
---
# <a name="what-is-microsoft-intune-app-management"></a>Microsoft Intune 앱 관리란?


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

IT 관리자는 Microsoft Intune을 사용하여 회사의 직원이 사용하는 클라이언트 앱을 관리할 수 있습니다. 이 기능은 디바이스 관리 및 데이터 보호 외에 추가적인 것입니다. 관리자의 우선 순위 중 하나는 최종 사용자가 업무 수행에 필요한 앱을 액세스할 수 있게 하는 것입니다. 이 목표는 다음과 같은 이유로 쉽지 않을 수 있습니다.
- 디바이스 플랫폼 및 앱 유형이 광범위합니다.
- 회사 디바이스와 사용자 개인 디바이스 둘 다에서 앱을 관리해야 할 수 있습니다.
- 네트워크와 데이터가 안전하게 유지되는지 확인해야 합니다.

또한 Intune에 등록되지 않은 디바이스에서 앱을 할당하고 관리할 수 있습니다.

## <a name="mobile-application-management-mam-basics"></a>MAM(모바일 애플리케이션 관리) 기본 사항

[Intune MAM(모바일 애플리케이션 관리)](app-lifecycle.md)은 사용자를 위해 모바일 앱을 게시, 푸시, 구성, 보호, 모니터링 및 업데이트할 수 있는 Intune 관리 기능 제품군을 나타냅니다.

MAM을 사용하면 애플리케이션 내에서 조직의 데이터를 관리하고 보호할 수 있습니다. 중요한 데이터를 포함하는 회사 또는 학교 관련 앱인 **등록 없는 MAM**(MAM-WE)는 **Bring-your-own-device**(BYOD) 시나리오의 개인 디바이스를 비롯한 거의 모든 [디바이스](app-management.md#app-management-capabilities-by-platform)에서 관리할 수 있습니다. Microsoft Office 앱과 같은 많은 생산성 앱은 Intune MAM에서 관리할 수 있습니다. 공개적으로 사용 가능한 공식적인 [Microsoft Intune 보호 앱](apps-supported-intune-apps.md) 목록을 참조하세요.

Intune MAM은 다음과 같은 두 가지 구성을 지원합니다.
- **Intune MDM + MAM**: IT 관리자는 Intune MDM(모바일 디바이스 관리)에 등록된 디바이스에서 MAM 및 앱 보호 정책을 사용하여 앱을 관리할 수만 있습니다. MDM + MAM을 사용하여 앱을 관리하려면 Azure Portal(https://portal.azure.com )에서 Intune 콘솔을 사용해야 합니다.
- **디바이스를 등록하지 않은 MAM**: 디바이스를 등록하지 않은 MAM 또는 MAM-WE를 통해 IT 관리자는 Intune MDM에 등록되지 않은 디바이스에서 MAM 및 앱 보호 정책을 사용하여 앱을 관리할 수 있습니다. 즉, 타사 EMM 공급자에 등록된 디바이스의 Intune으로 앱을 관리할 수 있습니다. MAM-WE를 사용하여 앱을 관리하려면 Azure Portal(https://portal.azure.com )에서 Intune 콘솔을 사용해야 합니다. 또한 타사 EMM(Enterprise Mobility Management) 공급자에 등록되었거나 MDM에 등록되지 않은 디바이스에서 Intune를 통해 앱을 관리할 수 있습니다. BYOD 및 Microsoft의 EMS에 대한 자세한 내용은 [Microsoft EMS(Enterprise Mobility + Security)를 사용하여 BYOD를 활성화하기 위한 기술 결정](../fundamentals/byod-technology-decisions.md)을 참조하세요.

## <a name="app-management-capabilities-by-platform"></a>플랫폼별 앱 관리 기능

Intune은 앱을 실행하려는 디바이스에서 필요한 앱을 얻도록 도와주는 다양한 기능을 제공합니다. 다음 표에서 앱 관리 기능의 요약을 제공합니다.

|  | Android/Android Enterprise | iOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| 디바이스 및 사용자에게 앱 추가 및 할당 | 예 | 예 | 예 | 예 | 예 |
| Intune에 등록되지 않은 디바이스에 앱 할당 | 예 | 예 | 아니요 | 아니요 | 아니요 |
| 앱 구성 정책을 사용하여 앱의 시작 동작 제어 | 예 | 예 | 아니요 | 아니요 | 아니요 |
| 모바일 앱 프로비전 정책을 사용하여 만료된 앱 갱신 | 아니요 | 예 | 아니요 | 아니요 | 아니요 |
| 앱 보호 정책이 적용되는 앱에서 회사 데이터 보호 | 예 | 예 | 아니요 | 아니요 <sup>1</sup> | 아니요 |
| 설치된 앱에서 회사 데이터만 제거(앱 선택적 초기화) | 예 | 예 | 아니요 | 예 | 예 |
| 앱 할당 모니터링 | 예 | 예 | 예 | 예 | 예 |
| 앱 스토어에서 대량 구매 앱 할당 및 추적 | 아니요 | 아니요 | 아니요 | 예 | 아니요 |
| 디바이스에 앱 필수 설치(필수) <sup>2</sup> | 예 | 예 | 예 | 예 | 예 |
| 회사 포털에서 디바이스에 선택적 설치(사용 가능한 설치) | 예 <sup>3</sup> | 예 | 예 | 예 | 예 |
| 웹에서 앱에 바로 가기 설치(웹 링크) | 예 <sup>4</sup> | 예 | 예 | 예 | 예 |
| 사내(기간 업무) 앱 | 예 | 예 | 예 | 예 | 아니요 |
| 스토어의 앱 | 예 | 예 | 아니요 | 예 | 예 |
| 앱 업데이트 | 예 | 예 | 아니요 | 예 | 예 |

<sup>1</sup> Windows 10을 실행하는 디바이스에서 앱을 보호하려면 [Windows Information Protection](../protect/windows-information-protection-configure.md)을 사용하는 것이 좋습니다.<br>
<sup>2</sup> Intune에서 관리하는 디바이스에만 적용됩니다.<br>
<sup>3</sup> Intune은 Android Enterprise 디바이스의 관리되는 Google Play 저장소에서 사용 가능한 앱을 지원합니다.<br>
<sup>4</sup> Intune은 표준 Android Enterprise 디바이스에서 웹 링크로 앱에 바로 가기를 설치하는 것을 제공하지 않습니다. 그러나 [다중 앱 전용 Android Enterprise 디바이스](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)에 대한 웹 링크 지원은 제공됩니다. 


## <a name="get-started"></a>시작

대부분의 앱 관련 정보는 다음과 같이 수행하여 액세스할 수 있는 **클라이언트 앱** 워크로드에서 확인할 수 있습니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Microsoft Intune** 창에서 **클라이언트 앱**을 선택합니다.

    !["클라이언트 앱" 워크로드 창](./media/app-management/apps-workload.png)

다음 네 개의 섹션에서는 **클라이언트 앱** 창에서 사용할 수 있는 옵션에 대해 설명합니다.

### <a name="manage"></a>관리
- **앱**: 직원이 사용하는 앱을 추가하고, 보고, 할당하고, 모니터링하려면 이 옵션을 선택합니다. 자세한 내용은 다음을 참조하십시오.
  - [앱 추가](apps-add.md).
  - [앱 할당](apps-deploy.md)
  - [앱 모니터링](apps-monitor.md)
- **앱 구성 정책**: 사용자가 앱을 실행할 때 필요할 수 있는 설정을 제공하려면 이 옵션을 선택합니다. 자세한 내용은 다음을 참조하십시오.
  - [Intune용 앱 구성 정책](app-configuration-policies-overview.md)
    - [iOS 앱 구성 정책](app-configuration-policies-use-ios.md)
    - [Android 앱 구성 정책](app-configuration-policies-use-android.md)
- **앱 보호 정책**: 설정을 앱에 연결하고 앱에서 사용하는 회사 데이터를 보호하려면 이 옵션을 선택합니다. 예를 들어 다른 앱과 통신하는 앱의 기능을 제한하거나, 사용자에게 회사 앱에 액세스하려면 PIN을 입력하도록 요구할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
  - [앱 보호 정책](app-protection-policies.md)
- **앱 선택적 초기화**: 선택한 사용자의 디바이스에서 회사 데이터만 제거하려면 이 옵션을 선택합니다. 자세한 내용은 다음을 참조하십시오.
  - [앱 선택적 초기화](apps-selective-wipe.md)
- **iOS 앱 프로비전 프로필**: iOS 앱에는 인증서로 서명된 프로비전 프로필 및 코드가 포함됩니다. 인증서가 만료되면 앱을 더 이상 실행할 수 없습니다. Intune은 만료가 임박한 앱이 있는 디바이스에 새 프로비전 프로필 정책을 미리 할당하기 위한 도구를 제공합니다. 자세한 내용은 다음을 참조하십시오.
  - [iOS 앱 프로비전 프로필](app-provisioning-profile-ios.md)

이 섹션에 대한 자세한 내용은 [앱 관리](app-management.md)를 참조하세요.

### <a name="monitor"></a>모니터
- **앱 라이선스**: 앱 스토어에서 대량 구매 앱을 보고, 할당하고, 모니터링할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
  - [iOS VPP(대량 구매 프로그램) 앱](vpp-apps-ios.md)
  - [비즈니스용 Microsoft Store 대량 구매 앱](windows-store-for-business.md)
- **검색된 앱**: Intune에서 할당되었거나 디바이스에 설치된 앱을 표시합니다. 자세한 내용은 [Intune에서 검색된 앱](app-discovered-apps.md)을 참조하세요.
- **앱 설치 상태**: 만든 앱 할당의 상태를 표시합니다. 자세한 내용은 [Microsoft Intune으로 앱 정보 및 할당을 모니터링 하는 방법](apps-monitor.md#device-and-user-status-graphs)을 참조하세요.
- **앱 보호 상태**: 선택한 사용자에 대한 앱 보호 정책의 상태를 표시합니다.
- **감사 로그**: 모든 IT 관리자의 Intune 앱 관련 활동을 표시합니다.

이 섹션에 대한 자세한 내용은 [앱 모니터링](apps-monitor.md)을 참조하세요.

### <a name="set-up"></a>설정
- **iOS VPP 토큰**: iOS VPP(대량 구매 프로그램) 라이선스를 적용하고 볼 수 있습니다. 자세한 내용은 다음을 참조하십시오.
  - [iOS 대량 구매 앱](vpp-apps-ios.md)
- **Windows 엔터프라이즈 인증서**: 관리되는 Windows 디바이스에 기간 업무 앱을 배포하는 데 사용되는 코드 서명 인증서의 상태를 적용하거나 볼 수 있습니다.
- **Windows Symantec 인증서**: Windows 10 Mobile 디바이스에 XAP 및 WP8.x appx 파일을 배포하는 데 필요한 Symantec 코드 서명 인증서의 상태를 적용하거나 볼 수 있습니다.
- **비즈니스용 Microsoft Store**: 비즈니스용 Microsoft Store에 대한 통합을 설정합니다. 그런 다음, 구매한 애플리케이션을 Intune에 동기화하고 할당한 후 라이선스 사용 현황을 추적할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
  - [비즈니스용 Microsoft Store 대량 구매 앱](windows-store-for-business.md)
- **Windows 테스트용 로드 키**: Windows 스토어에서 앱을 게시 및 다운로드하는 대신 디바이스에 직접 설치하는 데 사용할 수 있는 Windows 테스트용 로드 키를 추가할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
  - [Windows 앱 테스트용 로드](app-sideload-windows.md)
- **회사 포털 브랜딩**: 회사 포털을 사용자 지정하여 회사 브랜딩을 제공할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
  - [회사 포털 구성](company-portal-app.md)
- **앱 범주**: 앱 범주 이름을 추가, 고정 및 삭제할 수 있습니다.
- **Android 회사 프로필**: 앱을 승인하고, 승인한 앱을 엔터프라이즈에 대해 동기화할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
  - [Android 회사 프로필 앱](apps-add-android-for-work.md).

### <a name="help-and-support"></a>도움말 및 지원
- **도움말 및 지원**: 문제를 해결하거나, 지원을 요청하거나, Intune 상태를 볼 수 있습니다. 자세한 내용은 다음을 참조하십시오.
  - [문제 해결](../fundamentals/help-desk-operators.md)

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune에 앱 추가](apps-add.md)