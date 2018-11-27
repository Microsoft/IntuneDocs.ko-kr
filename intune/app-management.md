---
title: Microsoft Intune의 앱 관리란?
titlesuffix: ''
description: Microsoft Intune을 사용한 앱 관리의 기본 사항을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 366fab51d88587233f945fe7d880e3b6881bef45
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179187"
---
# <a name="what-is-microsoft-intune-app-management"></a>Microsoft Intune 앱 관리란?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

IT 관리자는 Microsoft Intune을 사용하여 회사의 직원이 사용하는 클라이언트 앱을 관리할 수 있습니다. 이 기능은 장치 관리 및 데이터 보호 외에 추가적인 것입니다. 관리자의 우선 순위 중 하나는 최종 사용자가 업무 수행에 필요한 앱을 액세스할 수 있게 하는 것입니다. 이 목표는 다음과 같은 이유로 쉽지 않을 수 있습니다.
- 장치 플랫폼 및 앱 유형이 광범위합니다.
- 회사 장치와 사용자 개인 장치 둘 다에서 앱을 관리해야 할 수 있습니다.
- 네트워크와 데이터가 안전하게 유지되는지 확인해야 합니다.

또한 Intune에 등록되지 않은 장치에서 앱을 할당하고 관리할 수 있습니다.

Intune은 앱을 실행하려는 장치에서 필요한 앱을 얻도록 도와주는 다양한 기능을 제공합니다. 다음 표에는 앱 관리 기능이 요약되어 있습니다. 

## <a name="app-management-capabilities-by-platform"></a>플랫폼별 앱 관리 기능

|  | Android | iOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| 장치 및 사용자에게 앱 추가 및 할당 | 예 | 예 | 예 | 예 | 예 |
| Intune에 등록되지 않은 장치에 앱 할당 | 예 | 예 | 아니요 | 아니요 | 아니요 |
| 앱 구성 정책을 사용하여 앱의 시작 동작 제어 | 아니요 | 예 | 아니요 | 아니요 | 아니요 |
| 모바일 앱 프로비전 정책을 사용하여 만료된 앱 갱신 | 아니요 | 예 | 아니요 | 아니요 | 아니요 |
| 앱 보호 정책이 적용되는 앱에서 회사 데이터 보호 | 예 | 예 | 아니요 | 아니요1 | 아니요 |
| 설치된 앱에서 회사 데이터만 제거(앱 선택적 초기화) | 예 | 예 | 아니요 | 예 | 예 |
| 앱 할당 모니터링 | 예 | 예 | 예 | 예 | 예 |
| 앱 스토어에서 대량 구매 앱 할당 및 추적 | 아니요 | 아니요 | 아니요 | 예 | 아니요 |
| 장치에 앱 필수 설치(필수)2 | 예 | 예 | 예 | 예 | 예 |
| 회사 포털에서 장치에 선택적 설치(사용 가능한 설치) | 예 | 예 | 예 | 예 | 예 |
| 웹에서 앱에 바로 가기 설치(웹 링크) | 예 | 예 | 예 | 예 | 예 |
| 사내(기간 업무) 앱 | 예 | 예 | 예 | 예 | 아니요 |
| 스토어의 앱 | 예 | 예 | 아니요 | 예 | 예 |
| 앱 업데이트 | 예 | 예 | 아니요 | 예 | 예 |

<sup>1</sup> Windows 10을 실행하는 장치에서 앱을 보호하려면 [Windows Information Protection](windows-information-protection-configure.md)을 사용하는 것이 좋습니다.

<sup>2</sup> Intune에서 관리하는 장치에만 적용됩니다.

## <a name="get-started"></a>시작

대부분의 앱 관련 정보는 다음과 같이 수행하여 액세스할 수 있는 **클라이언트 앱** 워크로드에서 확인할 수 있습니다.

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다.  
    Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Microsoft Intune** 창에서 **클라이언트 앱**을 선택합니다.

    !["클라이언트 앱" 워크로드 창](./media/apps-workload.png)

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
- **앱 선택적 초기화**: 선택한 사용자의 장치에서 회사 데이터만 제거하려면 이 옵션을 선택합니다. 자세한 내용은 다음을 참조하십시오.
    - [앱 선택적 초기화](apps-selective-wipe.md)
- **iOS 앱 프로비전 프로필**: iOS 앱에는 인증서로 서명된 프로비전 프로필 및 코드가 포함됩니다. 인증서가 만료되면 앱을 더 이상 실행할 수 없습니다. Intune은 만료가 임박한 앱이 있는 장치에 새 프로비전 프로필 정책을 미리 할당하기 위한 도구를 제공합니다. 자세한 내용은 다음을 참조하십시오.
    - [iOS 앱 프로비전 프로필](app-provisioning-profile-ios.md)

이 섹션에 대한 자세한 내용은 [앱 관리](app-management.md)를 참조하세요.

### <a name="monitor"></a>모니터
- **앱 라이선스**: 앱 스토어에서 대량 구매 앱을 보고, 할당하고, 모니터링할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
    - [iOS VPP(대량 구매 프로그램) 앱](vpp-apps-ios.md)
    - [비즈니스용 Microsoft Store 대량 구매 앱](windows-store-for-business.md)
- **검색된 앱**: Intune에서 할당되었거나 장치에 설치된 앱을 표시합니다. 자세한 내용은 [Microsoft Intune을 사용하여 장치 세부 정보 보기](device-inventory.md)를 참조하세요.
- **앱 설치 상태**: 만든 앱 할당의 상태를 표시합니다. 자세한 내용은 [Microsoft Intune으로 앱 정보 및 할당을 모니터링 하는 방법](apps-monitor.md#device-and-user-status-graphs)을 참조하세요.
- **앱 보호 상태**: 선택한 사용자에 대한 앱 보호 정책의 상태를 표시합니다.
- **감사 로그**: 모든 IT 관리자의 Intune 앱 관련 활동을 표시합니다.

이 섹션에 대한 자세한 내용은 [앱 모니터링](apps-monitor.md)을 참조하세요.

### <a name="set-up"></a>설정
- **iOS VPP 토큰**: iOS VPP(대량 구매 프로그램) 라이선스를 적용하고 볼 수 있습니다. 자세한 내용은 다음을 참조하십시오.
    - [iOS 대량 구매 앱](vpp-apps-ios.md)
- **Windows 엔터프라이즈 인증서**: 관리되는 Windows 장치에 기간 업무 앱을 배포하는 데 사용되는 코드 서명 인증서의 상태를 적용하거나 볼 수 있습니다.
- **Windows Symantec 인증서**: Windows 10 Mobile 장치에 XAP 및 WP8.x appx 파일을 배포하는 데 필요한 Symantec 코드 서명 인증서의 상태를 적용하거나 볼 수 있습니다.
- **비즈니스용 Microsoft Store**: 비즈니스용 Microsoft Store에 대한 통합을 설정합니다. 그런 다음, 구매한 응용 프로그램을 Intune에 동기화하고 할당한 후 라이선스 사용 현황을 추적할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
    - [비즈니스용 Microsoft Store 대량 구매 앱](windows-store-for-business.md)
- **Windows 테스트용 로드 키**: Windows 스토어에서 앱을 게시 및 다운로드하는 대신 장치에 직접 설치하는 데 사용할 수 있는 Windows 테스트용 로드 키를 추가할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
    - [Windows 앱 테스트용 로드](app-sideload-windows.md)
- **회사 포털 브랜딩**: 회사 포털을 사용자 지정하여 회사 브랜딩을 제공할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
    - [회사 포털 구성](company-portal-app.md)
- **앱 범주**: 앱 범주 이름을 추가, 고정 및 삭제할 수 있습니다.
- **Android 회사 프로필**: 엔터프라이즈용으로 승인한 앱을 승인하고 동기화할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
    - [Android 회사 프로필 앱](apps-add-android-for-work.md).

### <a name="help-and-support"></a>도움말 및 지원
- **도움말 및 지원**: 문제를 해결하거나, 지원을 요청하거나, Intune 상태를 볼 수 있습니다. 자세한 내용은 다음을 참조하십시오.
    - [문제 해결](help-desk-operators.md)

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune에 앱 추가](apps-add.md)
