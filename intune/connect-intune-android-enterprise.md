---
title: Intune 계정을 Android 엔터프라이즈 계정에 연결
titlesuffix: Microsoft Intune
description: Intune 계정을 Android 엔터프라이즈 계정에 연결하는 방법에 대해 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c32effb645b329c8095ec8757a980b1f3d80a4d7
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184289"
---
# <a name="connect-your-intune-account-to-your-android-enterprise-account"></a>Intune 계정을 Android 엔터프라이즈 계정에 연결

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android 회사 프로필 장치 및 Android 키오스크 장치를 지원하려면 Intune 테넌트 계정을 Android 엔터프라이즈 계정에 연결해야 합니다. 

> [!NOTE]
> Google과 Microsoft 도메인 간 상호 작용으로 인해, 이 단계에서는 브라우저 설정을 조정해야 할 수 있습니다.  "portal.azure.com"과 "play.google.com"이 브라우저의 동일한 보안 영역에 있는지 확인하세요.

1. 아직 설정하지 않은 경우 **Microsoft Intune**으로 [모바일 장치 관리 기관을 설정](mdm-authority-set.md)하여 모바일 장치 관리를 준비합니다.
2. [Azure Portal의 Intune](https://aka.ms/intuneportal)에 로그인하고, **장치 등록** > **Android 등록** > **관리되는 Google Play**를 선택합니다.  사용자 지정 Intune 관리자 역할을 사용할 경우 여기에 액세스하려면 조직 읽기 및 업데이트 권한이 필요합니다.
   
   ![Android 엔터프라이즈 등록 화면](./media/android-work-bind.png)

3. **동의**를 선택하여 Microsoft에서 [Google에 사용자 및 장치 정보를 보낼 수 있도록](data-intune-sends-to-google.md) 권한을 부여합니다. 
   
4. **Google을 시작하여 지금 연결**을 선택하여 관리되는 Google Play 웹 사이트를 엽니다. 웹 사이트가 브라우저의 새 탭에 열립니다.
  
5. Google의 로그인 페이지에서 이 테넌트에 대한 모든 Android 엔터프라이즈 관리 작업과 연결할 Google 계정을 입력합니다. Google Play 콘솔에서 앱을 관리 및 게시하기 위해 귀사의 IT 관리자가 공유하는 Google 계정입니다. 기존 Google 계정을 사용하거나 새 계정을 만들 수 있습니다. 선택한 계정이 G-Suite 도메인과 연결되어서는 안 됩니다.
    
    > [!Note]
    > Microsoft Edge 브라우저를 사용하는 경우 오른쪽 위 모서리에 있는 **로그인**을 클릭하여 Google 계정에 로그인합니다.

6. **조직 이름**에 회사 이름을 제공합니다. **EMM(엔터프라이즈 이동성 관리) 공급자**의 경우 **Microsoft Intune**이 나타나야 합니다.

7. Android 계약에 동의한 다음, **확인**을 선택합니다. 요청이 처리됩니다.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Android 엔터프라이즈 관리 계정 연결 끊기

Android 엔터프라이즈 등록 및 관리를 해제할 수 있습니다. 이렇게 하려면 먼저 등록된 Android 회사 프로필 장치를 모두 사용 중지해야 합니다. 그런 다음, Intune 관리 콘솔에서 **연결 끊기**를 선택하여 등록된 모든 Android 회사 프로필 장치 및 키오스크 장치를 등록에서 제거합니다. Android 엔터프라이즈 계정과 Intune 사이의 관계도 제거됩니다.

1. [Azure Portal](https://portal.azure.com)에서 Intune 관리자로 **모든 서비스** > **모니터링 + 관리** > **Intune**을 선택합니다.
2. **장치 등록** > **Android 등록** > **관리되는 Google Play** > **연결 끊기**를 선택합니다.
3. Intune에서 모든 Android 엔터프라이즈 장치의 연결을 끊고 등록을 취소하려면 **예**를 선택합니다.

## <a name="next-steps"></a>다음 단계

Android 엔터프라이즈 계정에 연결한 후 [Android 회사 프로필 장치를 설정](android-work-profile-enroll.md)하고 [Android 키오스크 장치를 설정](android-kiosk-enroll.md)할 수 있습니다.
