---
title: Microsoft Intune용 앱 구성 정책
titlesuffix: ''
description: Microsoft Intune에서 iOS 또는 Android 장치에 앱 구성 정책을 사용하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bfde1e935c782643e06030659082907365b1903e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179995"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Microsoft Intune용 앱 구성 정책

Microsoft Intune에서 앱 구성 정책을 사용하여 iOS 또는 Android 앱용 구성 설정을 제공합니다. 이러한 구성 설정을 사용하면 앱을 사용자 지정할 수 있습니다. 사용자 및 장치에 이러한 구성 정책을 직접 할당하지는 않으며, 대신 앱에 구성 정책을 연결한 다음, 앱을 할당합니다. 구성 정책 설정은 앱에서 해당 설정을 확인할 때(일반적으로는 앱을 처음 실행할 때) 사용됩니다.

포함 및 제외 할당의 조합을 사용하여 사용자 및 장치 그룹에 앱 구성 정책을 할당할 수 있습니다. 앱 구성 정책을 추가하면 앱 구성 정책에 대한 할당을 설정할 수 있습니다. 정책에 대한 할당을 설정할 때 정책이 적용될 사용자 그룹을 포함할지 제외할지 선택할 수 있습니다. 하나 이상의 그룹을 포함하도록 선택하면 기본 제공 그룹을 포함하거나 선택하기 위해 특정 그룹을 선택할 수 있습니다. 기본 제공 그룹에는 **모든 사용자**, **모든 장치** 및 **모든 사용자 + 모든 장치**가 포함됩니다.

예를 들어 앱에서 다음 세부 정보 중 하나를 지정하도록 요구할 수 있습니다.

- 사용자 지정 포트 번호
- 언어 설정
- 보안 설정
- 회사 로고와 같은 브랜딩 설정

사용자가 이러한 설정을 잘못 입력하면 기술 지원팀의 부담이 증가하며 새 앱 도입이 지연될 수 있습니다.

앱 구성 정책을 사용하는 경우 사용자가 앱을 실행하기 전에 정책에서 이러한 설정을 사용자에게 할당할 수 있으므로 이러한 문제를 방지할 수 있습니다. 배포한 설정은 자동으로 제공되므로 사용자가 아무런 작업을 수행하지 않아도 됩니다.

구성 설정은 앱에서 확인할 때마다 사용됩니다. 일반적으로 앱은 사용자가 앱을 처음 실행할 때 구성 설정을 확인합니다.

Intune을 사용한 앱 구성을 사용하는 방법에는 두 가지 옵션이 있습니다.
 - **관리 장치** - 장치는 MDM(모바일 장치 관리) 공급자로 Intune에서 관리됩니다.
 - **관리되는 앱** - 앱이 장치 등록 없이 관리됩니다.

> [!NOTE]
> Microsoft Intune 관리자는 관리되는 장치에서 Microsoft Office 응용 프로그램에 추가할 사용자 계정을 제어할 수 있습니다. 허용되는 조직 사용자 계정만 액세스하도록 제한하고 등록된 장치에서 개인 계정을 차단할 수 있습니다. 지원 응용 프로그램이 앱 구성을 처리하고 승인되지 않은 계정을 제거 및 차단합니다.

## <a name="apps-that-support-app-configuration"></a>앱 구성을 지원하는 앱

앱 구성 정책을 지원하는 앱에서 해당 정책을 사용할 수 있습니다. Intune에서 앱 구성을 지원하려면 앱 구성 사용을 지원하도록 앱을 작성해야 합니다. 자세한 내용은 앱 공급업체에 문의하세요.

Intune 앱 SDK를 앱에 통합하거나 앱이 개발된 후 앱을 래핑하여 기간 업무 앱을 준비할 수 있습니다. iOS와 Android 둘 다에 사용할 수 있는 Intune 앱 SDK를 통해 앱을 앱 구성 정책에 사용할 수 있도록 설정할 수 있습니다. Intune 앱 SDK는 앱 개발자에게서 필요한 코드 변경의 양을 최소화하려고 합니다. 자세한 내용은 [Intune 앱 SDK 개요](app-sdk.md)를 참조하세요.

## <a name="graph-api-support-for-app-configuration"></a>앱 구성에 대한 Graph API 지원

또한 Graph API를 사용하여 앱 구성 작업을 수행할 수 있습니다. 자세한 내용은 [Graph API Reference MAM Targeted Config](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create)(Graph API 참조 MAM 대상 구성)를 참조하세요.

## <a name="next-steps"></a>다음 단계

### <a name="managed-devices"></a>관리되는 장치

 - iOS 장치로 앱 구성을 사용하는 방법을 알아봅니다.  [관리되는 iOS 장치용 앱 구성 정책 추가](app-configuration-policies-use-ios.md)를 참조하세요.
 - Android 장치로 앱 구성을 사용하는 방법을 알아봅니다.  [관리되는 Android 장치용 앱 구성 정책 추가](app-configuration-policies-use-android.md)를 참조하세요.

### <a name="managed-apps"></a>관리되는 앱

 - 관리되는 앱으로 앱 구성을 사용하는 방법을 알아봅니다. [장치 등록 없이 관리되는 앱용 앱 구성 정책 추가](app-configuration-policies-managed-app.md)를 참조하세요.
