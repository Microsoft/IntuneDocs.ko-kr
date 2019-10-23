---
title: Intune에 Android 디바이스 등록
titleSuffix: Microsoft Intune
description: Intune에 Android 디바이스를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff005ddded4178801e7e334f604280ef4408aaff
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505671"
---
# <a name="enroll-android-devices"></a>Android 디바이스 등록

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 관리자는 다음과 같은 방법으로 Android 디바이스를 등록할 수 있습니다.
- Android 엔터프라이즈(사용자에게 안전한 최신 기능을 제공하는 등록 옵션 세트 제품):
    - [**Android 엔터프라이즈 회사 프로필**](android-work-profile-enroll.md): 개인 디바이스에 회사 데이터에 액세스할 수 있는 권한을 부여합니다. 관리자는 회사 계정, 앱 및 데이터를 관리할 수 있습니다. 디바이스에 있는 개인 데이터는 회사 데이터와 분리되며, 관리자는 개인 설정이나 데이터를 제어하지 않습니다. 
    - [**Android 엔터프라이즈 전용**](android-kiosk-enroll.md): 디지털 신호, 티켓 인쇄 또는 재고 관리와 같은 회사 소유의 단일 사용 디바이스입니다. 관리자는 제한된 앱 및 웹 링크 집합에 대한 디바이스 사용을 잠급니다. 또한 사용자가 다른 앱을 추가하거나 디바이스에서 다른 작업을 수행하는 것을 방지합니다.
    - [**Android 엔터프라이즈 완전 관리형**](android-fully-managed-enroll.md): 회사 소유의 단일 사용자 디바이스로 개인 용도가 아닌 업무용으로만 사용됩니다. 관리자는 전체 디바이스를 관리하고 회사 프로필에 사용할 수 없는 정책 제어를 적용할 수 있습니다. 
- [**Android 디바이스 관리자**](android-enroll-device-administrator.md)(삼성 Knox Standard 디바이스 및 [Zebra 디바이스](../configuration/android-zebra-mx-overview.md) 포함). 

## <a name="prerequisites"></a>전제 조건

모바일 디바이스 관리를 준비하려면 MDM 기관을 **Microsoft Intune**으로 설정해야 합니다. 지침은 [MDM 기관 설정](../fundamentals/mdm-authority-set.md)을 참조하세요. 이 항목은 모바일 디바이스 관리에 대해 Intune을 처음 설정할 때 한 번만 설정하면 됩니다.

Zebra Technologies에서 만든 디바이스의 경우 특정 디바이스 기능에 따라 회사 포털 추가 권한을 부여해야 할 수 있습니다. [Zebra 디바이스의 이동성 확장](../configuration/android-zebra-mx-overview.md)에 자세한 내용이 있습니다.

삼성 Knox Standard 디바이스의 경우 [추가 필수 구성 요소](android-samsung-knox-mobile-enroll.md)가 있습니다.

## <a name="next-steps"></a>다음 단계

- [Android 엔터프라이즈 회사 프로필 등록 설정](android-work-profile-enroll.md)
- [Android 엔터프라이즈 전용 디바이스 등록 설정](android-kiosk-enroll.md)
- [Android 엔터프라이즈 완전 관리형 등록 설정](android-fully-managed-enroll.md)
- [Android 디바이스 관리자 등록 설정](android-enroll-device-administrator.md)

