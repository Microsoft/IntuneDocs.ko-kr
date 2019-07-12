---
title: Microsoft Intune용 앱 구성 정책
titleSuffix: ''
description: Microsoft Intune에서 iOS 또는 Android 디바이스에 앱 구성 정책을 사용하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10dad24ee41f63dcc304d95e9b733f7de3f1b71a
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/08/2019
ms.locfileid: "67649035"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Microsoft Intune용 앱 구성 정책

Microsoft Intune에서 앱 구성 정책을 사용하여 iOS 또는 Android 앱용 구성 설정을 제공합니다. 이러한 구성 설정을 사용하면 앱 구성 및 관리의 업계 표준 방법을 사용하여 앱을 사용자 지정할 수 있습니다. 구성 정책 설정은 앱에서 해당 설정을 확인할 때(일반적으로는 앱을 처음 실행할 때) 사용됩니다.

포함 및 제외 할당의 조합을 사용하여 사용자 및 디바이스 그룹에 앱 구성 정책을 할당할 수 있습니다. 앱 구성 정책을 추가하면 앱 구성 정책에 대한 할당을 설정할 수 있습니다. 정책에 대한 할당을 설정할 때 정책이 적용될 사용자 그룹을 포함할지 제외할지 선택할 수 있습니다. 하나 이상의 그룹을 포함하도록 선택하면 기본 제공 그룹을 포함하거나 선택하기 위해 특정 그룹을 선택할 수 있습니다. 기본 제공 그룹에는 **모든 사용자**, **모든 디바이스** 및 **모든 사용자 + 모든 디바이스**가 포함됩니다.

예를 들어 앱 구성 설정에서 다음 세부 정보 중 하나를 지정해야 할 수도 있습니다.

- 사용자 지정 포트 번호
- 언어 설정
- 보안 설정
- 회사 로고와 같은 브랜딩 설정

사용자가 이러한 설정을 대신 입력하면 작업이 잘못 수행되어 기술 지원팀의 부담이 증가하며 새 앱 도입이 지연될 수 있습니다.

앱 구성 정책을 사용하면 앱을 실행하기 전에 사용자에게 할당된 정책에 구성 설정을 할당할 수 있으므로 앱 설정 문제를 방지할 수 있습니다. 배포한 설정은 자동으로 제공되므로 사용자가 아무런 작업을 수행하지 않아도 됩니다.

구성 설정은 앱에서 확인할 때마다 사용됩니다. 일반적으로 앱은 사용자가 앱을 처음 실행할 때 구성 설정을 확인합니다.

Intune을 사용한 앱 구성을 사용하는 방법에는 두 가지 옵션이 있습니다.
 - **관리 디바이스** - 디바이스는 MDM(모바일 디바이스 관리) 공급자로 Intune에서 관리됩니다.
 - **관리되는 앱** - 앱이 디바이스 등록 없이 관리됩니다.

> [!NOTE]
> Microsoft Intune 관리자는 관리되는 장치에서 Microsoft Office 애플리케이션에 추가할 사용자 계정을 제어할 수 있습니다. 허용되는 조직 사용자 계정만 액세스하도록 제한하고 등록된 디바이스에서 개인 계정을 차단할 수 있습니다. 지원 애플리케이션이 앱 구성을 처리하고 승인되지 않은 계정을 제거 및 차단합니다.

## <a name="apps-that-support-app-configuration"></a>앱 구성을 지원하는 앱

### <a name="managed-devices"></a>관리되는 디바이스
앱 구성 정책을 지원하는 앱에서 해당 정책을 사용할 수 있습니다. Intune에서 앱 구성을 지원하려면 [Appconfig 커뮤니티](https://www.appconfig.org/members)에 정의된 대로 앱 구성 사용을 지원하도록 앱을 작성해야 합니다. 자세한 내용은 앱 공급업체에 문의하세요.

### <a name="managed-apps"></a>관리되는 앱
Intune 앱 SDK를 앱에 통합하거나 앱이 개발된 후 앱을 래핑하여 기간 업무 앱을 준비할 수 있습니다. iOS와 Android 둘 다에 사용할 수 있는 Intune 앱 SDK를 통해 앱을 Intune 앱 보호 구성 정책에 사용할 수 있도록 설정할 수 있습니다. Intune 앱 SDK는 앱 개발자에게서 필요한 코드 변경의 양을 최소화하려고 합니다. 자세한 내용은 [Intune 앱 SDK 개요](app-sdk.md)를 참조하세요.

## <a name="graph-api-support-for-app-configuration"></a>앱 구성에 대한 Graph API 지원

또한 Graph API를 사용하여 앱 구성 작업을 수행할 수 있습니다. 자세한 내용은 [Graph API Reference MAM Targeted Config](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create)(Graph API 참조 MAM 대상 구성)를 참조하세요.

## <a name="next-steps"></a>다음 단계

### <a name="managed-devices"></a>관리되는 디바이스

 - iOS 디바이스로 앱 구성을 사용하는 방법을 알아봅니다.  [관리형 iOS 디바이스용 앱 구성 정책 추가](app-configuration-policies-use-ios.md)를 참조하세요.
 - Android 디바이스로 앱 구성을 사용하는 방법을 알아봅니다.  [관리되는 Android 디바이스용 앱 구성 정책 추가](app-configuration-policies-use-android.md)를 참조하세요.

### <a name="managed-apps"></a>관리되는 앱

 - 관리되는 앱으로 앱 구성을 사용하는 방법을 알아봅니다. [디바이스 등록 없이 관리되는 앱용 앱 구성 정책 추가](app-configuration-policies-managed-app.md)를 참조하세요.
