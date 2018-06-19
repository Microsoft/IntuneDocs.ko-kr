---
title: Intune 마이그레이션 중 장치 준수 및 앱 관리 정책 구성
titlesuffix: Microsoft Intune
description: 이 아티클의 목적은 Microsoft Intune 마이그레이션 중 장치 준수 및 앱 관리 정책을 구성하는 데 필요한 단계를 제공하는 것입니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 13a9c0a036eb6ce6ea7e984419c9598194b35b68
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2018
ms.locfileid: "29926357"
---
# <a name="configure-device-compliance-and-app-management-policies-when-migrating-to-microsoft-intune"></a>Microsoft Intune에 마이그레이션할 때 장치 준수 및 앱 관리 정책 구성

Intune으로 마이그레이션할 때 주요 목표는 모든 장치를 Intune에 등록하고 해당 정책을 준수하도록 하는 것입니다. 장치 정책을 통해 회사 소유의 단일 사용자 장치를 관리할 수 있을 뿐만 아니라 키오스크, POS(Point of Sale) 컴퓨터, 강의실에서 여러 학생이 공유하는 태블릿, 사용자가 지정되지 않은 장치(iOS에만 해당) 등 공유 장치 및 개인 장치(BYOD)를 관리할 수 있습니다.

각 장치 플랫폼이 다양한 설정을 제공할 수 있지만, 다음 모바일 장치 관리 기능을 제공하여 Intune 장치 정책을 각 장치 플랫폼에 적용할 수 있습니다.

-   각 사용자가 등록하는 장치의 수를 규정합니다.

-   장치 설정(예: 장치 수준 암호화, 암호 길이, 카메라 사용)을 관리합니다.

-   앱, 메일 프로필, VPN 프로필 등을 제공합니다.

-   보안 준수 정책에 대한 장치 수준 기준을 평가합니다.

> [!IMPORTANT]
> 장치 관리 정책은 개별 장치 또는 사용자에게 직접 할당되지 않으며, 대신 사용자 그룹에 할당됩니다. 정책을 사용자 그룹에 직접 적용함으로써 사용자 장치에 적용하거나, 정책을 장치 그룹에 적용함으로써 그룹 구성원에게 적용할 수 있습니다.

## <a name="task-list-for-device-compliance-policies"></a>장치 준수 정책에 대한 작업 목록

### <a name="task-1-add-device-groups-optional"></a>작업 1: 장치 그룹 추가(선택 사항)

사용자 ID 대신 장치 ID에 따라 관리 작업을 수행해야 할 때 장치 그룹을 만들 수 있습니다.

장치 그룹은 키오스크 장치와 같이 전용 사용자가 없는 장치, 교대 근무자가 공유하는 장치 또는 특정 위치에 할당된 장치를 관리하는 데 유용합니다.

장치 등록 전에 미리 장치 그룹을 구성하면 등록 시 장치 범주를 사용하여 장치를 자동으로 그룹에 결합시킬 수 있습니다. 그러면 그룹의 장치 정책을 자동으로 받게 됩니다. [그룹 시작](groups-get-started.md).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>작업 2: 리소스 액세스 프로필(Wi-Fi, VPN 및 메일 인증서) 사용

리소스 액세스 프로필은 인증서 및 등록된 장치에 대한 액세스 구성을 제공합니다. 인증서 기반 인증을 사용하는 경우 [인증서 구성](certificates-configure.md)을 수행합니다.

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>작업 3: 장치 구성 프로필 만들기 및 배포

장치 수준 설정을 적용할 장치 구성 프로필(예: 카메라 사용 안 함, 앱 스토어, 단일 앱 모드 구성, 홈 화면 등)을 만들어야 합니다. [장치 프로필](device-profiles.md)에 대해 자세히 알아보세요.

####  <a name="directly-import-ios-configuration-profiles-optional"></a>iOS 구성 프로필 직접 가져오기(선택 사항)

-   **Apple Configurator iOS 프로필(iOS 7.1 이상):** 기존 MDM 솔루션에서 Apple Configurator 프로필(.mobileconfig 파일)을 사용하는 경우 Intune에서 해당 프로필을 사용자 지정 구성 정책으로 직접 가져올 수 있습니다.

-   **iOS 모바일 응용 프로그램 구성 정책:** 기존 MDM 솔루션에서 iOS 모바일 응용 프로그램 구성 정책을 사용하는 경우 해당 정책이 Apple에서 속성 목록에 대해 지정한 XML 형식을 충족하는 한 Intune에서 이 정책을 직접 가져올 수 있습니다.

- [iOS](custom-settings-ios.md) 사용자 지정 정책을 추가하는 방법에 대해 알아보세요.

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>작업 4: 장치 준수 정책 만들기 및 배포(선택 사항)

장치 준수 정책은 보안 지향 설정을 평가하고 장치가 회사 표준을 준수하는지 여부를 보여 주는 보고를 제공합니다. 이러한 설정은 다음과 같습니다.

-   PIN 길이

-   탈옥 상태

-   OS 버전

장치 준수 설정에 대한 추가 리소스를 참조하세요.

-   [장치 준수 정책](device-compliance.md)에 대해 알아보세요.

-   [장치 준수 정책을 만드는 방법](device-compliance-get-started.md)에 대해 알아보세요.

### <a name="task-5-publish-and-deploy-apps"></a>작업 5: 앱 게시 및 배포

Intune MDM을 사용하는 경우 앱 자동 설치를 요구하거나 회사 포털에서 앱을 사용할 수 있도록 하여 앱을 제공할 수 있습니다.

-   [앱 추가 방법](apps-add.md).

-   [앱 배포 방법](apps-deploy.md).

### <a name="task-6-enable-device-enrollment"></a>작업 6: 장치 등록 사용

장치 등록은 장치를 관리하는 데 필요합니다. [회사 소유 장치 및 사용자의 개인 장치를 등록하는 방법](device-enrollment.md)에 대해 알아보세요.

## <a name="next-steps"></a>다음 단계

[앱 보호 정책 구성(선택 사항)](migration-guide-app-protection-policies.md).
