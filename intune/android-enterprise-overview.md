---
title: Microsoft Intune에서 Android 회사 프로필 디바이스 관리
titlesuffix: ''
description: Microsoft Intune에서는 사용자가 업무용 Android 디바이스를 사용할 때 추가 관리 기능과 개인 정보를 제공하기 위해 Android 회사 프로필 디바이스를 관리합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4082b845643aae47464e4df14ac6621fcf8f39cf
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180254"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Intune으로 Android 회사 프로필 디바이스 관리

Android 엔터프라이즈는 개인 앱 및 데이터를 회사 앱 및 데이터와 구분하는 기능 및 서비스의 집합입니다. Android 엔터프라이즈는 사용자가 업무용 Android 디바이스를 사용할 때 추가 관리 기능과 개인 정보를 제공합니다. 

## <a name="supported-devices"></a>지원되는 디바이스

Android 엔터프라이즈 관리 기능은 최신 Android 운영 체제의 일부인 기능에 따라 달라집니다. Android 엔터프라이즈를 지원하지 않는 디바이스의 경우 기존 Android 관리를 계속 사용할 수 있습니다. 자세한 내용은 [Android 엔터프라이즈 요구 사항](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)을 참조하세요.

## <a name="onboarding"></a>온보딩

Android 회사 프로필 디바이스를 등록하기 전에 일부 온보딩 단계를 완료해야 합니다. 이러한 단계를 통해 Intune 테넌트와 Google Play for Work 서비스 간 연결을 설정합니다. 자세한 내용은 [Android 회사 프로필 디바이스 등록 사용](android-work-profile-enroll.md)을 참조하세요.

## <a name="work-profile-management"></a>회사 프로필 관리

Intune을 사용하여 Android 회사 프로필 디바이스를 관리하는 경우 전체 디바이스를 관리하는 것이 아닙니다. 관리 기능은 등록하는 동안 만든 회사 프로필에만 영향을 줍니다. Intune을 통해 디바이스에 배포되는 앱은 회사 프로필에 설치됩니다. 회사 프로필의 앱 아이콘은 디바이스의 개인 앱에서 식별됩니다. 디바이스의 엔터프라이즈 부분에 포함되지 않은 모든 Android 앱과 데이터는 개인용으로 유지되고 최종 사용자가 관리합니다. 사용자는 디바이스의 개인 측에 선택한 앱을 설치할 수 있습니다. 관리자는 회사 프로필로 범위가 지정된 앱 및 작업을 관리하고 모니터링할 수 있습니다.

Intune은 Android 회사 프로필 디바이스에서 구성할 수 있는 기본 제공 일반 설정의 범위를 제공합니다. 자세한 내용은 [Android 회사 프로필 디바이스 정책 설정](compliance-policy-create-android-for-work.md)을 참조하세요.

## <a name="app-publishing-and-distribution"></a>앱 게시 및 배포

Google Play for Work 서비스는 Android 엔터프라이즈 앱 배포 및 관리의 필수적인 부분입니다. 회사 프로필로 Android 회사 프로필 디바이스에 배포된 모든 앱은 관리되는 Google Play 서비스에서 제공됩니다. Play 스토어에서 앱을 관리하고 배포하려면 회사의 Google 관리용 관리자 자격 증명을 사용하여 Google Play 웹 사이트에 로그인합니다. Android 엔터프라이즈 배포용 앱이 디바이스의 회사 프로필에 표시되도록 승인할 수 있습니다. 이러한 앱은 Intune 콘솔에 동기화되고, 나중에 이 콘솔에서 Intune을 통해 앱을 배포하고 관리할 수 있습니다. 조직에서 개발한 LOB(기간 업무) 앱은 Google의 Android 앱 게시 콘솔을 사용하여 관리되는 Google Play에 게시해야 합니다. 조직에 대한 액세스를 제한하려면 Android 앱 게시 콘솔에서 기간 업무 앱을 구성해야 합니다.

앱은 사용자 조작 없이, 사용자가 **알 수 없는 소스에서의 설치**를 허용할 필요 없이 설치할 수 있습니다. 선택적 앱이나 사용 가능한 앱을 찾아보고 설치하려는 경우, 사용자는 디바이스에서 Play for Work 스토어를 탐색할 수 있습니다. 자세한 내용은 [Intune을 사용하여 Android 회사 프로필 디바이스에 앱 할당](apps-add-android-for-work.md)을 참조하세요.

## <a name="app-configuration"></a>앱 구성

Android 엔터프라이즈는 앱 구성 값을 지원하는 앱에 배포하기 위한 인프라를 제공합니다. 업무용 앱의 구성 값을 지정하면 사용자가 앱을 처음 시작할 때 구성 값이 제대로 설정됩니다. 앱 구성을 지원하려면 앱 개발자가 특별히 관리되는 구성 값을 지원하도록 Android 앱을 만들어야 합니다. 이렇게 되면 Intune을 사용하여 이러한 구성 설정을 지정하고 적용할 수 있습니다. 자세한 내용은 [관리되는 Android 디바이스용 앱 구성 정책 추가](app-configuration-policies-use-android.md)를 참조하세요.

## <a name="email-configuration"></a>메일 구성

Android 엔터프라이즈는 iOS에서 제공되는 것과 같은 네이티브 이메일 앱이나 기본 이메일 프로필을 제공하지 않습니다. 대신, 앱 구성 설정을 지원하는 앱에 해당 설정을 적용하여 메일 구성을 설정할 수 있습니다. Gmail 및 Nine Work는 Android 엔터프라이즈 앱 구성이 포함된 구성을 지원하는 Play 스토어의 두 가지 EAS(Exchange ActiveSync) 클라이언트 앱입니다.

Intune은 작업용 앱으로 관리되는 경우 Gmail 및 Nine Work 앱에 대한 구성 템플릿을 제공합니다. 앱 구성 프로필을 지원하는 기타 이메일 앱은 모바일 앱 구성 정책을 통해 구성할 수 있습니다.

Android 회사 프로필 디바이스에 Exchange ActiveSync 조건부 액세스를 사용하는 경우 Gmail 또는 Nine Work 이메일 앱을 사용하는 것이 좋습니다. Android용 Microsoft Outlook 앱이나 ADAL을 통해 최신 인증을 사용하는 기타 메일 앱도 지원됩니다. 자세한 내용은 [Microsoft Intune에서 이메일 설정을 구성하는 방법](email-settings-configure.md)을 참조하세요.

## <a name="app-protection-policies"></a>앱 보호 정책

앱 보호 정책은 회사 프로필 및 개인 프로필에서 완전히 지원됩니다. Android 앱 게시 콘솔(https://play.google.com/apps/publish)에 기간 업무 앱을 게시할 수 있습니다. 이 콘솔에는 앱을 조직에 비공개로 설정하는 옵션이 포함됩니다. 자세한 내용은 [Intune에서 Android 회사 프로필 디바이스에 대한 디바이스 준수 정책 추가](compliance-policy-create-android-for-work.md)를 참조하세요. 앱 보호 정책에 대한 일반적인 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

## <a name="vpn-profiles"></a>VPN 프로필

VPN 지원은 Android VPN 프로필과 비슷합니다. Android 엔터프라이즈 관리를 위해 동일한 VPN 공급자 및 기본 구성 옵션을 다음과 같은 두 가지 방식으로 사용할 수 있습니다.

-  **회사 프로필 범위 VPN** – VPN 연결이 회사 프로필에 배포된 앱으로 제한됩니다. Android 엔터프라이즈로 관리되는 앱만 VPN 연결을 사용할 수 있습니다. 디바이스의 개인 앱은 관리되는 VPN 연결을 사용할 수 없습니다. 자세한 내용은 [Android 엔터프라이즈 VPN 설정](vpn-settings-android.md#android-for-work-vpn-settings)을 참조하세요.

-  **앱별 VPN** – VPN 공급자가 지원하는 경우 Intune에서 앱별 VPN을 구성할 수 있습니다.
    - 앱별 VPN에 대한 구성
    - Android 엔터프라이즈 앱 구성 프로필을 통해 앱별 VPN을 구성하는 기능입니다.
    자세한 내용은 [Microsoft Intune 사용자 지정 프로필을 사용하여 Android 디바이스에 대한 앱별 VPN 프로필 만들기](android-pulse-secure-per-app-vpn.md)를 참조하세요.

## <a name="certificate-profiles"></a>인증서 프로필

Android 관리에 사용할 수 있는 인증서 프로필 구성 옵션을 Android 회사 프로필 디바이스에서 동일하게 사용할 수 있습니다. Android 엔터프라이즈에서는 고급 인증서 관리 API를 제공합니다. 고급 인증서 관리는 다음 기능을 제공합니다.

-  인증서 배포가 자동으로 매끄럽게 수행되도록 합니다.
-  Intune에서 디바이스가 사용 중지되고 회사 프로필이 제거될 경우 배포된 인증서가 제거되도록 합니다.
-  관리 서비스를 통해 IT 부서에서 인증서를 배포 및 구성했음을 사용자에게 알리는 향상된 메시지를 제공합니다.

자세한 내용은 [Microsoft Intune에서 디바이스에 대한 인증서 프로필 구성](certificates-configure.md)을 참조하세요.

## <a name="wi-fi-profiles"></a>Wi-Fi 프로필

Intune에서 디바이스가 사용 중지되고 회사 프로필이 삭제될 경우 Android 엔터프라이즈에서 관리하는 Wi-Fi 프로필도 제거됩니다. 자세한 내용은 [Microsoft Intune에서 Wi-Fi 설정을 구성하는 방법](wi-fi-settings-configure.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계
- [Android 장치 등록](android-enroll.md)
- [Intune을 사용하여 Android 회사 프로필 장치에 앱 할당](apps-add-android-for-work.md)
