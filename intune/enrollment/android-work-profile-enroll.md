---
title: Intune에서 Android 엔터프라이즈 회사 프로필 디바이스 등록
titleSuffix: Microsoft Intune
description: Intune에서 Android 엔터프라이즈 회사 프로필 디바이스를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4339f98ed133c3426faee8bd4b18024fd2648606
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503359"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Android 엔터프라이즈 회사 프로필 디바이스 등록 설정

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune을 통해 Android 엔터프라이즈 회사 프로필 디바이스에 앱과 설정을 배포하여 업무 정보와 개인 정보가 구분되도록 할 수 있습니다. Android 엔터프라이즈에 대한 자세한 내용은 [Android 엔터프라이즈 요구 사항](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)을 참조하세요.

Android 엔터프라이즈 회사 프로필 관리를 설정하려면 다음 단계를 따릅니다.

1. [Intune 테넌트 계정을 Android 엔터프라이즈 계정에 연결](connect-intune-android-enterprise.md)합니다.
2. Android 엔터프라이즈 회사 프로필 등록 설정을 지정합니다. Android 엔터프라이즈 회사 프로필은 [특정 Android 디바이스에서만 지원](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22)됩니다. Android Enterprise 회사 프로필을 지원하는 디바이스에서는 Android 디바이스 관리자 관리도 지원합니다. Intune에서는 Android 엔터프라이즈 회사 프로필을 지원하는 디바이스를 [등록 제한](enrollment-restrictions-set.md) 내에서 관리하는 방법을 지정할 수 있습니다.
    - **차단**:  Android Enterprise 회사 프로필을 지원하는 디바이스를 포함한 모든 Android 디바이스는 Android 디바이스 관리자 등록 역시 차단되지 않는 한 Android 디바이스 관리자 디바이스로 등록됩니다. 
    - **허용(기본적으로 설정됨)** : Android 엔터프라이즈 회사 프로필을 지원하는 모든 디바이스가 Android 회사 프로필 디바이스로 등록됩니다. Android Enterprise 회사 프로필을 지원하지 않는 Android 디바이스는 Android 디바이스 관리자 등록이 차단되지 않는 한 Android 디바이스 관리자 디바이스로 등록됩니다. 
> [!NOTE]
> 2019년 7월 기준으로 새로운 테넌트의 경우 **허용**에 설정된 기본값은 true입니다. 모든 이전 테넌트는 등록 제한 사항이 변경되는 일을 겪지 않으며 자신이 등록 제한 사항에 설정한 모든 정책을 볼 수 있습니다. 등록 제한 사항이 변경되지 않은 이전 테넌트의 경우 **차단**이 여전히 Android Enterprise 회사 프로필의 기본값입니다.

3. [사용자에게 디바이스를 등록하는 방법을 알려 줍니다](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android).  

Android Enterprise 회사 프로필을 사용하여 디바이스를 등록하고 싶지만 해당 디바이스가 이미 Android 디바이스 관리자에 등록된 경우 먼저 해당 디바이스 등록을 취소한 다음 다시 등록해야 합니다.
> [!NOTE]
> 관리자는 **사용 중지** 기능을 사용하여 원격으로 이를 수행할 수 있습니다. 이 기능은 **모든 디바이스** 블레이드에서 디바이스를 선택한 후 작업 메뉴에서 찾을 수 있습니다.

[디바이스 등록 관리자](device-enrollment-manager-enroll.md) 계정을 사용하여 Android 엔터프라이즈 회사 프로필 디바이스를 등록하는 경우 계정당 등록할 수 있는 디바이스 수는 최대 10개입니다.

자세한 내용은 [Google에 보내는 데이터 Intune](../protect/data-intune-sends-to-google.md)을 참조하세요.

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Android 엔터프라이즈 회사 프로필의 다음 단계
- [Android 엔터프라이즈 회사 프로필 앱 배포](../apps/apps-add-android-for-work.md)
- [Android 엔터프라이즈 회사 프로필 구성 정책 추가](../configuration/device-profiles.md)

## <a name="see-also"></a>참고 항목

[Microsoft Intune에서 Android Enterprise 디바이스 구성 및 문제 해결](https://support.microsoft.com/help/4476974)
