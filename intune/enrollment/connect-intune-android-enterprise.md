---
title: Intune 계정을 관리형 Google Play 계정에 연결합니다.
titleSuffix: Microsoft Intune
description: Intune 계정을 관리형 Google Play 계정에 연결하는 방법을 알아봅니다.
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
ms.openlocfilehash: a89b94f098292bf44122d6d2d144c7f35967cd32
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709445"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Intune 계정을 관리형 Google Play 계정에 연결

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

[Android 엔터프라이즈 회사 프로필](android-work-profile-enroll.md), [Android 엔터프라이즈 완전 관리형](android-fully-managed-enroll.md) 및 [Android 엔터프라이즈 전용 디바이스](android-kiosk-enroll.md)를 지원하려면 Intune 테넌트 계정을 관리형 Google Play 계정에 연결해야 합니다.  

Android 엔터프라이즈 관리를 더 쉽게 구성하고 사용할 수 있도록 Intune에서는, Google Play에 연결한 후, Android 엔터프라이즈와 관련된 일반적인 앱 4개를 Intune 관리자 콘솔에 자동으로 추가합니다. 다음과 같은 4개의 Android Enterprise 앱이 있습니다.

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise완전 관리형 시나리오에 사용합니다.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 2단계 인증을 사용하는 경우 계정에 로그인할 수 있도록 지원합니다.
- **[Intune 회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - APP(앱 보호 정책) 및 Android Enterprise 작업 프로필 시나리오에 사용합니다.
- [관리형 홈 화면](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) -Android Enterprise 전용/키오스크 시나리오에 사용합니다.

> [!NOTE]
> Google과 Microsoft 도메인 간 상호 작용으로 인해, 이 단계에서는 브라우저 설정을 조정해야 할 수 있습니다.  "portal.azure.com"과 "play.google.com"이 브라우저의 동일한 보안 영역에 있는지 확인하세요.

1. 모바일 디바이스 관리를 아직 준비하지 않은 경우  [모바일 디바이스 관리 기관](../fundamentals/mdm-authority-set.md) 을 **Microsoft Intune**.
2. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하여 **디바이스 등록** > **Android 등록** > **관리되는 Google Play**를 선택합니다.  사용자 지정 Intune 관리자 역할을 사용할 경우 여기에 액세스하려면 조직 읽기 및 업데이트 권한이 필요합니다.
   
   ![Android 엔터프라이즈 등록 화면](./media/connect-intune-android-enterprise/android-work-bind.png)

3. **동의**를 선택하여 Microsoft에서 [Google에 사용자 및 디바이스 정보를 보낼 수 있도록](../protect/data-intune-sends-to-google.md) 권한을 부여합니다. 
   
4. **Google을 시작하여 지금 연결**을 선택하여 관리되는 Google Play 웹 사이트를 엽니다. 웹 사이트가 브라우저의 새 탭에 열립니다.
  
5. Google의 로그인 페이지에서 이 테넌트에 대한 모든 Android 엔터프라이즈 관리 작업과 연결할 Google 계정을 입력합니다. Google Play 콘솔에서 앱을 관리 및 게시하기 위해 귀사의 IT 관리자가 공유하는 Google 계정입니다. 기존 Google 계정을 사용하거나 새 계정을 만들 수 있습니다. 선택한 계정이 G-Suite 도메인과 연결되어서는 안 됩니다.
    
    > [!Note]
    > Microsoft Edge 브라우저를 사용하는 경우 오른쪽 위 모서리에 있는 **로그인**을 클릭하여 Google 계정에 로그인합니다.

6. **조직 이름**에 회사 이름을 제공합니다. **EMM(엔터프라이즈 이동성 관리) 공급자**의 경우 **Microsoft Intune**이 나타나야 합니다.

7. Android 계약에 동의한 다음, **확인**을 선택합니다. 요청이 처리됩니다.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Android 엔터프라이즈 관리 계정 연결 끊기

Android 엔터프라이즈 등록 및 관리를 끌 수 있습니다. 이렇게 하려면 먼저 회사 프로필 디바이스, 전용 디바이스 및 완전히 관리되는 디바이스 등 등록된 Android 엔터프라이즈 디바이스를 사용 중지해야 합니다. 그런 다음, Intune 관리 콘솔에서 **연결 끊기**를 선택하여 등록된 모든 Android 엔터프라이즈 회사 프로필 디바이스, 전용 디바이스 및 완전 관리형 디바이스를 등록에서 제거합니다. 관리형 Google Play 계정과 Intune의 관계도 제거됩니다.

1. Intune 관리자는 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 등록** > **Android 등록** > **관리되는 Google Play** > **연결 끊기**를 선택합니다.
3. Intune에서 모든 Android 엔터프라이즈 디바이스의 연결을 끊고 등록을 취소하려면 **예**를 선택합니다.

## <a name="next-steps"></a>다음 단계

관리형 Google Play 계정에 연결한 후 [Android 엔터프라이즈 회사 프로필 디바이스를 설정](android-work-profile-enroll.md)하고 [Android 엔터프라이즈 전용 디바이스를 설정](android-kiosk-enroll.md)하고 [Android 엔터프라이즈 완전 관리형 디바이스를 설정](android-kiosk-enroll.md)할 수 있습니다.
