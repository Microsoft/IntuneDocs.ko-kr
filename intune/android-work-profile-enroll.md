---
title: Intune에서 Android 엔터프라이즈 회사 프로필 디바이스 등록
titleSuffix: Microsoft Intune
description: Intune에서 Android 엔터프라이즈 회사 프로필 디바이스를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66574fe66f90b73d8ebf5835c5b16e93276579e4
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568221"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Android 엔터프라이즈 회사 프로필 디바이스 등록 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune을 통해 Android 엔터프라이즈 회사 프로필 디바이스에 앱과 설정을 배포하여 업무 및 개인 정보가 구분되도록 할 수 있습니다. Android 엔터프라이즈에 대한 자세한 내용은 [Android 엔터프라이즈 요구 사항](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)을 참조하세요.

Android 엔터프라이즈 회사 프로필 관리를 설정하려면 다음 단계를 따릅니다.

1. [Intune 테넌트 계정을 Android 엔터프라이즈 계정에 연결](connect-intune-android-enterprise.md)합니다.
2. Android 엔터프라이즈 회사 프로필 등록 설정을 지정합니다. Android 엔터프라이즈 회사 프로필은 [특정 Android 디바이스에서만 지원](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22)됩니다. Android 엔터프라이즈 회사 프로필을 지원하는 디바이스는 기본 Android 관리도 지원합니다. Intune에서는 Android 엔터프라이즈 회사 프로필을 지원하는 디바이스를 [등록 제한](enrollment-restrictions-set.md) 내에서 관리하는 방법을 지정할 수 있습니다.
    - **차단(기본적으로 설정됨)**:  Android 엔터프라이즈 회사 프로필을 지원하는 디바이스를 비롯한 모든 Android 디바이스가 기존 Android 디바이스로 등록됩니다.
    - **허용**: Android 엔터프라이즈 회사 프로필을 지원하는 모든 디바이스가 Android 회사 프로필 디바이스로 등록됩니다. Android 엔터프라이즈 회사 프로필을 지원하지 않는 Android 디바이스는 기본 Android 디바이스로 등록됩니다.
3. [사용자에게 디바이스를 등록하는 방법을 알려 줍니다](/intune-user-help/enroll-your-device-in-intune-android).


Android 엔터프라이즈 회사 프로필을 사용하여 디바이스를 등록하려고 하지만 해당 디바이스가 이미 정규 Android 디바이스로 등록된 경우 먼저 해당 디바이스 등록을 취소한 다음, 다시 등록해야 합니다.

[디바이스 등록 관리자](device-enrollment-manager-enroll.md) 계정을 사용하여 Android 엔터프라이즈 회사 프로필 디바이스를 등록하는 경우 계정당 등록할 수 있는 디바이스 수는 최대 10개입니다.

자세한 내용은 [Google에 보내는 데이터 Intune](data-intune-sends-to-google.md)을 참조하세요.

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>관리형 Google Play 스토어에서 회사 포털 앱 승인

사용자가 항상 최신 버전의 회사 포털 앱에 액세스할 수 있도록 하려면 관리형 Google Play 스토어에서 Android용 회사 포털 앱을 승인해야 합니다. 이를 승인하면 각 사용자가 자동 업데이트를 받을 수 있습니다. 승인하지 않으면 회사 포털이 결국 최신 상태가 아니게 되며, Microsoft에서 릴리스하는 중요한 버그 수정이나 새로운 기능을 받지 못할 수 있습니다.

Intune 회사 포털을 승인하려면 다음 단계를 따르세요.

1.  [관리형 Google Play 스토어](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal)에서 회사 포털 앱으로 이동합니다.
2.  Android 엔터프라이즈에 대한 바인딩을 구성하는 데 사용한 것과 동일한 Google 계정으로 관리형 Google Play 스토어에 로그인합니다.
3.  **승인**을 클릭하면 새 대화 상자가 열립니다.
4.  이 대화 상자에서 권한을 검토하고 **승인**을 클릭합니다. 회사 포털 앱이 디바이스의 회사 프로필을 관리할 수 있게 하려면 이러한 권한을 허용해야 합니다.
5.  **앱이 새 권한을 요청할 때 승인 유지**를 선택하고 **저장**을 클릭합니다.

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Android 엔터프라이즈 회사 프로필의 다음 단계
- [Android 엔터프라이즈 회사 프로필 앱 배포](apps-add-android-for-work.md)
- [Android 엔터프라이즈 회사 프로필 구성 정책 추가](device-profiles.md)
