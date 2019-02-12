---
title: Intune 마이그레이션 중 앱 보호 정책 구성
titlesuffix: Microsoft Intune
description: 이 아티클에서는 Microsoft Intune 마이그레이션 중 앱 보호 정책을 설정하는 데 필요한 단계를 제공합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa9df81c363099cc487497fdd4503df8c91ea4a5
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837037"
---
# <a name="configure-app-protection-policies-optional"></a>앱 보호 정책 구성(선택 사항)


앱 보호 정책을 사용하면 다음을 수행할 수 있습니다.
* 앱 암호화
* 앱 액세스 시 PIN 정의
* 앱이 무단 해제 또는 루팅된 디바이스에서 실행되지 않도록 차단하고 다른 많은 보호 조치 수행

사용자의 휴대폰을 잃어버리거나 도난당한 경우 개인 데이터는 그대로 유지하면서 선택적으로 회사 데이터를 원격으로 초기화할 수 있습니다.

앱 보호 정책은 앱 수준에서 보안을 적용하며 디바이스 등록이 필요하지 않습니다. 이 정책은 Intune에 등록된 디바이스와 등록되지 않은 디바이스에서 모두 사용할 수 있습니다. 또한 타사 MDM 공급자에 등록된 디바이스에도 적용할 수 있습니다.

## <a name="app-protection-policies-with-lob-apps"></a>LOB 앱의 앱 보호 정책

또한 [Microsoft Intune 앱 SDK](app-sdk-get-started.md) 또는 iOS 및 Android 플랫폼용 Microsoft Intune 앱 래핑 도구를 사용하여 LOB(기간 업무) 앱으로 모바일 앱 보호 정책을 확장할 수도 있습니다. 자세한 내용은 [iOS용 앱 래핑 도구](app-wrapper-prepare-ios.md) 및 [Android용 앱 래핑 도구](app-wrapper-prepare-android.md)를 참조하세요. 또한 [앱 보호에 대한 LOB 앱 준비](apps-prepare-mobile-application-management.md)를 참조하세요.

## <a name="how-do-app-protection-policies-help-during-migration"></a>앱 보호 정책이 마이그레이션하는 동안 어떻게 도움이 되나요?

마이그레이션에서는 디바이스를 이전 MDM 공급자에서 제거하고 Intune에 등록해야 합니다. 이런 과정을 계획하고, 최종 사용자가 이전 MDM 공급자에서 등록 취소하는 즉시 Intune에 등록하도록 권장해야 합니다. 그러나 마이그레이션하는 동안 등록 프로세스 완료를 미루는 사용자가 있을 수 있으며, 이런 경우 해당 디바이스가 MDM 공급자 중 하나에서 관리되지 않습니다.

이 기간에 회사 리소스 액세스가 계속 허용되는 경우 조직이 디바이스 도난 및 회사 데이터 손실에 더 취약해질 수 있습니다. 회사 리소스 액세스가 차단된 경우 사용자 생산성이 떨어질 수도 있습니다.

Intune에서는 디바이스 수준 관리 방법이 없는 경우 회사 데이터 보안 기능을 계속 사용할 수 있도록 마이그레이션하는 동안에도 회사 데이터 보호 기능을 제공할 수 있습니다.

이전 MDM 공급자에서 조건부 액세스를 비활성화하므로, Intune에 등록하는 동안에도 사용자는 계속 생산성을 유지할 수 있습니다.

## <a name="task-list-for-app-protection-policies"></a>앱 보호 정책에 대한 작업 목록

1. [앱 보호 정책 만들기](app-protection-policies.md#create-an-app-protection-policy)
2. [정책 배포](app-protection-policies.md#deploy-a-policy-to-users)


## <a name="next-steps"></a>다음 단계

[특별 마이그레이션 고려 사항](migration-guide-considerations.md)
