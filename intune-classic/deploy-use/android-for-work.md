---
title: Android for Work 정보
description: Intune에서는 사용자가 업무용 Android 장치를 사용할 때 추가 관리 기능과 개인 정보를 제공하기 위해 Android for Work을 관리합니다.
keywords: ''
author: nathbarn
manager: dougeby
ms.date: 03/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: ac83eb71b04e034023d008fa4cdbb960f2c4bedb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020965"
---
# <a name="manage-android-for-work-devices-with-intune"></a>Intune에서 Android for Work 장치 관리

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Android for Work는 개인 앱 및 데이터를 회사 앱 및 데이트가 포함된 회사 프로필과 구분하는 Android 장치 기능 및 서비스의 집합니다. Android for Work에서는 사용자가 업무용 Android 장치를 사용할 때 추가 관리 기능을 제공하고 개인 정보를 보호합니다. Intune을 통해 앱과 회사 리소스를 Android for Work 장치에 배포하여 회사 및 개인 정보가 구분되도록 할 수 있습니다. 성공적으로 배포된 경우 앱과 앱이 액세스하는 데이터는 장치의 Android for Work 환경 내에서만 유지됩니다.

## <a name="supported-devices"></a>지원되는 장치

Android for Work 관리 기능에서는 최신 Android 운영 체제에 포함된 기능을 사용합니다. 현재 Android for Work는 회사 프로필을 지원하는 Android 5.0 Lollipop 이상을 실행하는 장치에서 지원됩니다. Android for Work을 지원하지 않는 장치의 경우 기존 Android 관리를 계속 사용할 수 있습니다. [Android for Work 요구 사항](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)에 대해 자세히 알아보세요.

## <a name="onboarding"></a>온보딩

Android for Work 장치를 등록하기 전에 일부 온보딩 단계를 완료해야 합니다. 이러한 단계는 Android for Work 앱 배포 및 관리 프로세스의 필수적인 부분인 Google의 Play for Work 서비스와 Intune 테넌트 간에 연결을 설정합니다. [Android for Work 등록 사용](/intune-classic/deploy-use/set-up-android-for-work)에 대해 자세히 알아보세요.

## <a name="work-profile-management"></a>회사 프로필 관리

Intune에서 Android for Work 장치를 관리할 경우 전체 장치를 관리하는 것이 아닙니다. 관리 기능은 등록하는 동안 만든 회사 프로필에만 영향을 줍니다. Intune을 통해 장치에 배포되는 앱은 회사 프로필에 설치됩니다. 업무용 앱을 장치의 개인 앱과 구분하기 위해 회사 프로필의 앱 아이콘에는 주황색 서류 가방이 표시됩니다. 장치의 Android for Work 부분에 포함되지 않은 모든 Android 앱과 데이터는 개인용으로 유지되고 최종 사용자가 관리합니다. 사용자는 선택한 앱을 장치에 개인용으로 설치할 수 있지만, 관리자는 회사 프로필로 범위가 지정된 앱 및 작업을 관리하고 모니터링할 수 있습니다.

Intune은 Android for Work 장치에서 구성할 수 있는 기본 제공 일반 설정의 범위를 제공합니다. [Android for Work 정책 설정](android-for-work-policy-settings-in-microsoft-intune.md)에 대해 자세히 알아보세요.

## <a name="app-publishing-and-distribution"></a>앱 게시 및 배포

Google Play for Work 서비스는 Android for Work 앱 배포 및 관리의 필수적인 부분입니다. 회사 프로필로 Android for Work 장치에 배포된 모든 앱은 Play for Work 서비스에서 제공됩니다. Play 스토어에서 앱을 관리하고 배포하려면 회사의 Google 관리용 관리자 자격 증명을 사용하여 Google Play 웹 사이트에 로그인합니다. Android for Work 배포용 앱이 장치의 회사 프로필에 표시되도록 승인할 수 있습니다. 이러한 앱은 Intune 콘솔에 동기화되고, 나중에 이 콘솔에서 Intune을 통해 앱을 배포하고 관리할 수 있습니다. 조직에서 개발한 LOB(기간 업무) 앱은 Google의 Android 앱 게시 콘솔을 사용하여 Play for Work에 게시해야 합니다. 조직에 대한 액세스를 제한하려면 Android 앱 게시 콘솔에서 기간 업무 앱을 구성해야 합니다.

앱은 사용자 조작 없이, 사용자가 **알 수 없는 소스에서의 설치**를 허용할 필요 없이 설치할 수 있습니다. 선택적 앱이나 사용 가능한 앱을 찾아보고 설치하려는 경우, 사용자는 장치에서 Play for Work 스토어를 탐색할 수 있습니다. [Android for Work용 앱 배포](/intune-classic/deploy-use/android-for-work-apps)에 대해 자세히 알아보세요.

## <a name="app-configuration"></a>앱 구성

Android for Work은 앱 구성 값을 지원되는 앱에 배포하기 위한 인프라를 제공합니다. 업무용 앱의 구성 값을 지정하면 사용자가 앱을 처음 시작할 때 구성 값이 제대로 설정됩니다. 앱 구성을 지원하려면 앱 개발자가 특별히 관리되는 구성 값을 지원하도록 Android 앱을 만들어야 합니다. 이렇게 되면 Intune을 사용하여 이러한 구성 설정을 지정하고 적용할 수 있습니다. [Android for Work 앱 구성 설정](afw-app-configuration-policy.md)에 대해 자세히 알아보세요.

## <a name="email-configuration"></a>메일 구성

Android for Work는 iOS에서 제공되는 것과 같은 기본 전자 메일 앱이나 네이티브 전자 메일 프로필 개체를 제공하지 않습니다. 대신, 앱 구성 설정을 지원하는 앱에 해당 설정을 적용하여 메일 구성을 설정할 수 있습니다. Gmail 및 Nine Work은 Android for Work 앱 구성이 포함된 구성을 지원하는 Play 스토어의 두 가지 EAS(Exchange ActiveSync) 클라이언트 앱입니다.

Intune은 작업용 앱으로 관리되는 경우 Gmail 및 Nine Work 앱에 대한 구성 템플릿을 제공합니다. 앱 구성 프로필을 지원하는 기타 메일 앱은 모바일 앱 구성 정책을 통해 구성할 수 있습니다.

Android for Work 장치에 Exchange ActiveSync 조건부 액세스를 사용 중이면 Gmail 또는 Nine Work 메일 앱을 사용해야 합니다. Android용 Microsoft Outlook 앱이나 ADAL을 통해 최신 인증을 사용하는 기타 메일 앱도 지원됩니다. [회사 메일에 대한 메일 프로필](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)에 대해 자세히 알아보세요.

## <a name="app-protection-policies"></a>앱 보호 정책

앱 보호 정책은 회사 프로필 및 개인 프로필에서 완전히 지원됩니다. Android 앱 게시 콘솔(https://play.google.com/apps/publish)에 기간 업무 앱을 게시할 수 있습니다. 이 콘솔에는 앱을 조직에 비공개로 설정하는 옵션이 포함됩니다. [Android for Work 준수 정책 설정](afw-compliance-policy-settings-in-microsoft-intune.md)에 대해 자세히 알아보세요. 앱 보호 정책에 대한 일반적인 내용은 [앱 정책](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)을 참조하세요.

## <a name="vpn-profiles"></a>VPN 프로필

VPN 지원은 Android VPN 프로필과 비슷합니다. Android for Work 관리를 위해 동일한 VPN 공급자 및 기본 구성 옵션을 다음과 같은 두 가지 방식으로 사용할 수 있습니다.

-  **회사 프로필 범위 VPN** – VPN 연결이 회사 프로필에 배포된 앱으로 제한됩니다. Android for Work로 관리되는 앱만 VPN 연결을 사용할 수 있습니다. 장치의 개인 앱은 관리되는 VPN 연결을 사용할 수 없습니다.

-  **앱별 VPN** – VPN 공급자가 앱별 VPN에 대한 구성을 지원하고 Android for Work 앱 구성 프로필을 통해 앱별 VPN을 구성하는 기능을 제공할 경우 Intune에서 앱별 VPN을 구성할 수 있습니다. VPN 공급자에게 문의하여 이 기능을 지원하는지 확인하세요. [VPN 연결 프로필](vpn-connections-in-microsoft-intune.md)에 대해 자세히 알아보세요.

## <a name="certificate-profiles"></a>인증서 프로필

Android 관리에 사용할 수 있는 인증서 프로필 구성 옵션을 Android for Work 장치에서 동일하게 사용할 수 있습니다. Android for Work에서는 고급 인증서 관리 API를 제공합니다. 고급 인증서 관리는 다음 기능을 제공합니다.

- 인증서 배포가 자동으로 매끄럽게 수행되도록 합니다.
-  Intune에서 장치가 사용 중지되고 회사 프로필이 제거될 경우 배포된 인증서가 완전히 제거되도록 합니다.
-  관리 서비스를 통해 IT 부서에서 인증서를 배포 및 구성했음을 사용자에게 알리는 향상된 메시지를 제공합니다.

[인증서 프로필](secure-resource-access-with-certificate-profiles.md)에 대해 자세히 알아보세요.

## <a name="wi-fi-profiles"></a>Wi-Fi 프로필

Intune에서 장치가 사용 중지되고 회사 프로필이 삭제될 경우 Android for Work에서 관리하는 Wi-Fi 프로필도 제거됩니다. [Wi-Fi 프로필](wi-fi-connections-in-microsoft-intune.md)에 대해 자세히 알아보세요.

## <a name="next-steps"></a>다음 단계
[Android for Work 등록 사용](/intune-classic/deploy-use/set-up-android-for-work)

[Android for Work용 앱 배포](/intune-classic/deploy-use/android-for-work-apps)
