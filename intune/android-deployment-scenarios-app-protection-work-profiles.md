---
title: Microsoft Intune의 앱 보호 정책 및 회사 프로필 - Azure | Microsoft Docs
description: Microsoft Intune에서 개인 또는 BYOD Android Enterprise 디바이스에 앱 보호 정책이나 회사 프로필을 사용하기로 결정한 경우, 차이점과 장단점을 확인합니다. APP-WE(등록이 없는 앱 보호 정책) 및 Android Enterprise 회사 프로필이 제공하는 차이점과 기능을 비교합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/13/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fbdd89e6d26042258cd4c5a3d93cfdb68d73756d
ms.sourcegitcommit: 5708ec1d7ae50494be44ed5064f150b636188c84
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56240103"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Intune의 Android Enterprise 디바이스에 대한 애플리케이션 보호 정책 및 회사 프로필

대부분의 조직에서 관리자는 다양한 디바이스에서 리소스 및 데이터를 보호해야 하는 과제가 있습니다. 한 가지 과제는 개인 Android Enterprise 디바이스에서 사용자의 리소스를 보호하는 것으로, 이를 BYOD(Bring Your Own Device)라고도 합니다. Microsoft Intune에서는 BYOD(Bring Your Own Device)를 위한 두 가지 Android 배포 시나리오를 지원합니다.

- APP-WE(등록이 없는 앱 보호 정책)
- Android Enterprise 회사 프로필

APP-WE 및 Android 회사 프로필 배포 시나리오에는 BYOD 환경에 중요한 다음 주요 기능이 포함됩니다.

1. **조직에서 관리되는 데이터의 보호 및 분리**: 두 솔루션은 모두 조직에서 관리되는 데이터에 대한 DLP(데이터 손실 방지) 제어를 적용하여 조직 데이터를 보호합니다. 이 보호는 최종 사용자가 실수로 보호된 데이터를 개인 앱 또는 계정에 공유하는 것과 같은 보호된 데이터의 우발적인 누수를 방지합니다. 데이터에 액세스하는 디바이스가 정상 상태이고 손상되지 않았는지 확인하는 역할도 합니다.

2. **최종 사용자 개인 정보**: APP-WE 및 Android Enterprise 회사 프로필은 디바이스에 있는 최종 사용자 콘텐츠와 MDM(모바일 디바이스 관리) 관리자가 관리하는 데이터를 분리합니다. 두 시나리오에서 모두 IT 관리자는 조직에서 관리되는 앱 또는 ID에 대해 PIN 전용 인증과 같은 정책을 적용합니다. IT 관리자는 최종 사용자가 소유하거나 제어하는 데이터를 읽거나, 액세스하거나, 지울 수 없습니다.

BYOD 배포를 위해 APP-WE 또는 Android Enterprise 회사 프로필을 선택하는지 여부는 요구 사항과 비즈니스 필요에 따라 달라집니다. 이 문서의 목적은 결정에 도움이 되도록 지침을 제공하는 것입니다.

## <a name="about-intune-app-protection-policies"></a>Intune 앱 보호 정책 정보

Intune APP(앱 보호 정책)는 사용자를 대상으로 하는 데이터 보호 정책입니다. 이 정책은 애플리케이션 수준에서 데이터 손실 방지를 적용합니다. Intune APP를 사용하려면 앱 개발자가 자신이 만든 앱에서 APP 기능을 사용하도록 설정해야 합니다.

개별 Android 앱에서 APP를 사용하도록 설정하는 몇 가지 방법은 다음과 같습니다.

1. **기본적으로 Microsoft 자사 앱에 통합됨**: Android용 Microsoft Office 앱과 선택적 기타 Microsoft 앱에 Intune APP가 기본 제공됩니다. Word, OneDrive, Outlook 등의 해당 Office 앱에는 정책을 적용하기 위한 추가적인 사용자 지정이 필요하지 않습니다. 이 앱은 Google Play 스토어에서 직접 최종 사용자가 설치할 수 있습니다.

2. **Intune SDK를 사용하여 개발자가 앱 빌드에 통합함**: 앱 개발자는 원본 코드에 Intune SDK를 통합하고 Intune APP 정책 기능을 지원하도록 앱을 다시 컴파일할 수 있습니다.

3. **Intune 앱 래핑 도구를 사용하여 래핑됨**: 일부 고객은 원본 코드에 대한 액세스 권한 없이 Android 앱(.APK 파일)을 컴파일합니다. 원본 코드가 없으면, 개발자가 Intune SDK와 통합할 수 없습니다. SDK가 없으면, 앱에서 APP 정책을 사용하도록 설정할 수 없습니다. 개발자는 APP 정책을 지원하도록 앱을 수정하거나 기록해야 합니다.

    도움이 되도록 Intune에서는 기존 Android 앱(APK)용 **앱 래핑 도구** 도구를 제공하고 APP 정책을 인식하는 앱을 만듭니다.

    이 도구에 대한 자세한 내용은 [앱 보호 정책에 대해 기간 업무 앱 준비](apps-prepare-mobile-application-management.md)를 참조하세요.

APP를 사용하도록 설정된 앱 목록을 보려면, [다양한 모바일 애플리케이션 보호 정책을 사용하는 관리형 앱](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)을 참조하세요.

## <a name="deployment-scenarios"></a>배포 시나리오

이 섹션에서는 APP-WE 및 Android Enterprise 회사 프로필 배포 시나리오의 중요한 특징을 설명합니다.

#### <a name="app-we"></a>APP-WE

APP-WE(등록이 없는 앱 보호 정책) 배포는 디바이스가 아닌 앱에 대한 정책을 정의합니다. 이 시나리오에서 디바이스는 일반적으로 Intune과 같은 MDM 기관에서 등록 또는 관리되지 않습니다. 앱 및 조직 데이터 액세스를 보호하기 위해 관리자는 APP로 관리 가능한 앱을 사용하고 해당 앱에 데이터 보호 정책을 적용합니다.

이 기능은 다음에 적용됩니다.

- Android 4.4 이상

> [!TIP]
> 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

APP-WE 시나리오는 디바이스에서 조직을 위한 공간을 적게 사용하고 MDM에 등록하지 않으려는 최종 사용자에게 적합합니다. 그래도 관리자는 데이터를 보호해야 합니다. 이와 같은 디바이스는 관리되지 않습니다. WiFi, 디바이스 VPN 및 인증서 관리와 같은 매우 일반적인 MDM 작업과 기능이 이 배포 시나리오에 포함되지 않습니다.

#### <a name="android-enterprise-work-profiles"></a>Android Enterprise 회사 프로필

회사 프로필은 핵심 Android Enterprise 배포 시나리오이고 BYOD 사용 사례를 대상으로 하는 유일한 시나리오입니다. 회사 프로필은 Intune에서 관리할 수 있는 Android OS 수준에서 만들어진 별도 파티션입니다.

이 기능은 다음에 적용됩니다.

- Google Mobile Services를 사용하는 Android 5.0 이상 디바이스

회사 프로필에는 다음 기능이 포함됩니다.

- **기존 MDM 기능**: 관리되는 Google Play를 사용하는 앱 수명 주기 관리와 같은 주요 MDM 기능은 모든 Android Enterprise 시나리오에서 사용할 수 있습니다. 관리되는 Google Play는 사용자 개입 없이 앱을 설치 및 업데이트하는 강력한 환경을 제공합니다. IT 부서에서는 앱 구성 설정을 조직용 앱에 푸시할 수도 있습니다. 최종 사용자가 알 수 없는 출처에서 설치를 허용하도록 요구할 필요도 없습니다. 인증서 배포, WiFi/VPN 구성 및 디바이스 암호 설정과 같은 일반적인 기타 MDM 작업은 회사 프로필을 통해 사용할 수 있습니다.

- **회사 프로필 경계의 DLP**: IT 부서에서는 APP-WE처럼 데이터 보호 정책을 적용할 수 있습니다. 회사 프로필을 사용하면, 앱 수준이 아닌 회사 프로필 수준에서 DLP 정책이 적용됩니다. 예를 들어 복사/붙여넣기 보호는 앱에 적용되는 APP 설정을 통해 적용되거나 회사 프로필을 통해 적용됩니다. 앱이 회사 프로필에 배포되면, 관리자는 APP 수준에서 이 정책을 해제하여 회사 프로필에 대한 복사/붙여넣기 보호를 일시 중지할 수 있습니다.

## <a name="tips-to-optimize-the-work-profile-experience"></a>회사 프로필 환경을 최적화하기 위한 팁

### <a name="when-to-use-app-within-work-profiles"></a>회사 프로필 내에서 APP를 사용하는 경우

Intune APP 및 회사 프로필은 함께 또는 별도로 사용할 수 있는 상호 보완적인 기술입니다. 아키텍처 측면에서 두 솔루션은 모두 다양한 계층에서(APP는 개별 앱 계층에서, 회사 프로필은 프로필 계정에서) 정책을 적용합니다. APP 정책으로 관리되는 앱을 회사 프로필의 앱에 배포하는 시나리오는 유효하며 지원됩니다. APP, 회사 프로필 또는 특정 조합을 사용하는 것은 DLP 요구 사항에 따라 결정됩니다.

회사 프로필과 APP는 한 프로필이 조직의 데이터 보호 요구 사항을 충족하지 않는 경우, 추가적인 적용 범위를 제공함으로써 서로의 설정을 보완합니다. 예를 들어 회사 프로필은 신뢰할 수 없는 클라우드 스토리지 위치에 저장하지 못하도록 앱을 제한하는 제어를 기본적으로 제공하지 않습니다. APP에는 이 기능이 포함됩니다. 회사 프로필에서 제공하는 DLP만으로 충분하다고 결정하고 APP를 사용하지 않도록 선택할 수 있습니다. 또는 두 가지 정책의 조합으로 보호해야 할 수 있습니다.

### <a name="suppress-app-policy-for-work-profiles"></a>회사 프로필을 위해 APP 정책 차단

APP-WE 시나리오의 관리되지 않는 디바이스 및 회사 프로필을 사용하는 관리형 디바이스와 같은 여러 디바이스를 보유한 개별 사용자를 지원해야 할 수 있습니다. 

예를 들어 최종 사용자가 회사 앱을 열 때 PIN을 입력하도록 요구합니다. 디바이스에 따라 PIN 기능은 APP 또는 회사 프로필에서 처리됩니다. APP-WE 디바이스의 경우, PIN으로 시작 동작은 APP에서 적용됩니다. 회사 프로필 디바이스의 경우, OS에서 적용하는 디바이스 또는 회사 프로필 PIN을 사용할 수 있습니다. 이 시나리오를 적용하려면, 앱이 회사 프로필에 배포될 때 APP 설정이 적용되지 않도록 구성해야 합니다. 이렇게 구성하지 않으면, 디바이스뿐 아니라 APP 계층에서도 PIN을 묻는 메시지를 최종 사용자에게 표시합니다.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>회사 프로필에서 다중 ID 동작 제어

Outlook 및 OneDrive와 같은 Office 애플리케이션에는 "다중 ID" 동작이 있습니다. 애플리케이션의 한 인스턴스 내에서 최종 사용자는 여러 개별 계정 또는 클라우드 스토리지 위치에 연결을 추가할 수 있습니다. 애플리케이션 내에서 해당 위치에서 검색된 데이터를 분리하거나 병합할 수 있습니다. 또한 사용자는 개인 ID(user@outlook.com)와 조직 ID(user@contoso.com) 간에 컨텍스트를 전환할 수 있습니다.

회사 프로필을 사용하는 경우, 이 다중 ID 동작을 사용하지 않도록 설정할 수 있습니다. 이를 사용하지 않도록 설정하면, 회사 프로필에서 배지가 달린 앱 인스턴스의 경우, 조직 ID를 사용하여 구성해야 합니다. Office Android 앱을 지원하기 위한 허용된 계정 앱 구성 설정을 사용합니다.

자세한 내용은 [iOS 및 Android용 Outlook 앱 구성 설정 배포](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)를 참조하세요.

## <a name="when-to-use-intune-app"></a>Intune APP를 사용하는 경우

Intune APP를 사용하는 것이 가장 추천되는 여러 엔터프라이즈 이동성 시나리오가 있습니다.

#### <a name="older-devices-running-android-44-51-are-being-used"></a>Android 4.4~5.1을 실행하는 오래된 디바이스를 사용 중인 경우

공식적으로 Google Mobile Services를 사용하는 Android 디바이스 5.0 이상은 회사 프로필을 지원하고 이 방법으로 관리할 수 있습니다. 그러나 몇몇 OEM이 제공하는 일부 Android 5.0 및 5.1 디바이스는 회사 프로필을 지원하지 않습니다.

회사 프로필을 지원하지 않는 버전을 사용하는 경우, 디바이스에서 조직 데이터에 대한 DLP를 보장하려면 Intune APP 기능을 사용해야 합니다.

#### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>MDM이 없고, 등록이 없고, Google Services를 사용할 수 없는 경우

일부 고객은 다양한 이유로 회사 프로필 관리를 포함한 어떤 형태의 디바이스 관리도 원하지 않습니다.

- 법적 및 책임상 이유
- 일관된 사용자 경험을 제공하기 위해
- Android 디바이스 환경이 매우 다양한 종류로 구성된 경우
- 회사 프로필 관리에 필요한 Google Services에 연결할 수 없는 경우.

예를 들어 고객이 중국에 있거나 사용자가 중국에 있는 경우에는 Google Services가 차단되므로 Android 디바이스 관리를 사용할 수 없습니다. 이 경우, DLP를 위해 Intune APP를 사용합니다.

## <a name="summary"></a>요약

Intune을 사용하면, APP-WE 및 Android Enterprise 회사 프로필을 둘 다 Android BYOD 프로그램에 사용할 수 있습니다. APP-WE 또는 회사 프로필을 선택하는 것은 비즈니스 및 사용 요구 사항에 따라 결정됩니다. 요약하면, 관리형 디바이스에서 인증서 배포, 앱 푸시 등의 MDM 작업이 필요한 경우에는 회사 프로필을 사용합니다. 디바이스를 관리하지 않으려 하거나 관리할 수 없고, Intune APP 사용 가능 앱만 사용 중인 경우에는 APP-WE를 사용합니다.

## <a name="next-steps"></a>다음 단계
[앱 보호 정책 사용](app-protection-policy.md) 또는 [디바이스 등록](android-enroll.md)을 시작합니다.
