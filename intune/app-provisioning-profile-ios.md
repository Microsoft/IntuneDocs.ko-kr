---
title: Microsoft Intune에서 iOS 앱 프로비전 프로필
titlesuffix: ''
description: Intune은 만료일이 다가오는 앱이 있는 디바이스에 새 프로비전 프로필을 미리 할당하기 위한 도구를 제공합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d58c7e0dcb02ec553d1d1cb43b44ecf3258810a8
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838320"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>iOS 앱 프로비전 프로필을 사용하여 모바일 앱이 만료되지 않도록 방지

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>소개

iPhone 및 iPad에 할당된 Apple iOS LOB(기간 업무) 앱은 포함된 프로비전 프로필과 인증서로 서명된 코드로 빌드됩니다. 앱이 실행되면 iOS는 iOS 앱의 무결성을 확인하고 프로비전 프로필에 정의된 정책을 적용합니다. 다음 유효성 검사가 수행됩니다.

- **설치 파일 무결성** - iOS는 엔터프라이즈 서명 인증서의 공개 키와 앱 세부 정보를 비교합니다. 두 내용이 다르면 앱 콘텐츠가 변경되었을 수 있으므로 앱 실행이 허용되지 않습니다.
- **기능 적용** - iOS는 앱 설치(.ipa) 파일에 포함된 엔터프라이즈 프로비전 프로필(개별 개발자 프로비전 프로필이 아님)에서 앱 기능을 적용하려고 합니다.


일반적으로 앱에 서명하기 위해 사용하는 엔터프라이즈 서명 인증서는 3년 동안 유지됩니다. 그러나 프로비전 프로필은 1년 후에 만료됩니다. Intune은 인증서가 여전히 유효한 동안 만료일이 다가오는 앱이 있는 디바이스에 새 프로비전 프로필을 미리 할당하기 위한 도구를 제공합니다.
인증서가 만료되면 새 인증서로 앱을 다시 서명하고 새 인증서의 키에 새 프로비전 프로필을 포함해야 합니다.

관리자의 경우 iOS 앱 프로비전 구성을 할당하려면 보안 그룹을 제외 및 포함할 수 있습니다. 예를 들어 iOS 앱 프로비전 구성을 모든 사용자에게 할당할 수 있지만 임원 그룹은 제외합니다.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>iOS 모바일 앱 프로비전 프로필을 만드는 방법

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
1.  **클라이언트 앱** 워크로드에서 **관리** > **iOS 앱 프로비전 프로필**을 선택합니다.
2.  프로필 목록 창에서 **프로필 만들기**를 선택합니다.
3. **프로필 만들기** 창에서 다음 값을 구성합니다.
    - **이름** - 이 모바일 프로비전 프로필의 이름을 제공합니다.
    - **설명** - 필요에 따라 정책에 대한 설명을 제공합니다.
    - **프로필 파일 업로드** - **가져오기**를 선택하고 Apple 개발자 웹 사이트에서 다운로드한 Apple 모바일 구성 프로필 파일(확장명 `.mobileprovision`)을 선택합니다.
4. 작업이 끝나면 **만들기**를 선택합니다.

## <a name="next-steps"></a>다음 단계

필요한 iOS 디바이스에 프로필을 할당합니다. 자세한 내용은 [디바이스 프로필을 할당하는 방법](device-profile-assign.md)의 단계를 참조하세요.
