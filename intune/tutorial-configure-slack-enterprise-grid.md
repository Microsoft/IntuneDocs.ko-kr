---
title: 자습서 - EMM 및 앱 구성에 Intune을 사용하도록 Slack 구성
titleSuffix: Microsoft Intune
description: 이 자습서에서는 EMM 및 앱 구성에 Intune을 사용하도록 Slack을 구성합니다.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 06/11/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7ff4e1fd9f055268a461d1a81b8a2e31fe3d32b
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67548987"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>자습서: EMM 및 앱 구성에 Intune을 사용하도록 Slack 구성

Slack은 Microsoft Intune에서 사용할 수 있는 협업 앱입니다.   

이 자습서에서는 다음 작업을 수행하게 됩니다.
> [!div class="checklist"]
> - Slack Enterprise Grid에서 Intune을 EMM(Enterprise Mobility Management) 공급자로 설정합니다. Grid 플랜 작업 영역의 액세스를 Intune 관리형 디바이스로 제한할 수 있습니다.
> - 앱 구성 정책을 만들어 iOS의 EMM용 Slack 앱 및 Android 회사 프로필 디바이스용 Slack 앱을 관리합니다.
> - Intune 디바이스 준수 정책을 만들어 Android 및 iOS 디바이스가 규격 디바이스로 간주되기 위해 충족해야 하는 조건을 설정합니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건
이 자습서를 사용하려면 다음 구독이 있는 테스트 테넌트가 필요합니다.
- Azure Active Directory Premium([평가판](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Intune 구독([평가판](free-trial-sign-up.md))

[Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-) 플랜도 필요합니다.

## <a name="configure-your-slack-enterprise-grid-plan"></a>Slack Enterprise Grid 플랜 구성
[Slack의 지침](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm)에 따라 Slack Enterprise Grid 플랜에 대해 EMM을 켜고 Grid 플랜의 IDP(ID 공급자)로 [Azure Active Directory를 연결](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial)합니다.

## <a name="sign-in-to-intune"></a>Intune에 로그인
[Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>iOS 디바이스에서 EMM용 Slack 설정
iOS 앱 EMM용 Slack을 Intune 테넌트에 추가하고 앱 구성 정책을 만들어 조직의 iOS 사용자가 Intune을 EMM 공급자로 사용하여 Slack에 액세스할 수 있도록 합니다.

### <a name="add-slack-for-emm-to-intune"></a>Intune에 EMM용 Slack 추가
Intune에서 EMM용 Slack을 관리 iOS 앱으로 추가하고 Slack 사용자를 할당합니다. 앱은 플랫폼별로 다르므로 Android 디바이스의 Slack 사용자를 위한 Intune 앱을 따로 추가해야 합니다.
1. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다.
2. 앱 유형에서  **- iOS**를 선택합니다.
3. **앱 스토어 검색**을 선택합니다. 검색어 “EMM용 Slack”을 입력하고 앱을 선택합니다.
4. **앱 정보**를 필요에 따라 변경 내용을 구성합니다.
5. **추가**를 선택합니다.
6. 검색 창에 “EMM용 Slack”을 입력하고 방금 추가한 앱을 선택합니다.
7. 관리에서 **할당**을 선택합니다.
8. **그룹 추가**를 선택합니다. Slack에 대해 EMM을 켤 때 영향을 받도록 선택한 사용자에 따라 **할당 유형**에서 다음을 선택할 수 있습니다.
    - **등록된 디바이스에 사용 가능** - “All members (including guests)”(모든 구성원(게스트 포함)를 선택한 경우
    - **등록 유무에 상관없이 사용 가능** - “All members (excluding guests)”(모든 구성원(게스트 제외)) 또는 “선택 사항”을 선택한 경우
9. **포함된 그룹**을 선택하고 이 앱을 모든 사용자가 사용할 수 있도록 설정에서 **예**를 선택합니다.
10. **확인**을 클릭한 다음 **확인**을 다시 클릭합니다.
11. **저장**을 클릭합니다.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>EMM용 Slack을 위한 앱 구성 정책 추가
EMM iOS용 Slack을 위한 앱 구성 정책을 추가합니다. 관리 디바이스의 앱 구성 정책은 플랫폼별로 다르므로 Android 디바이스의 Slack 사용자를 위한 정책을 따로 추가해야 합니다.
1. Intune에서 **클라이언트 앱** > **앱 구성 정책** > **추가**를 선택합니다.
2. 이름에 Slack 앱 구성 정책 테스트를 입력합니다.
3. 디바이스 등록 유형에서 **관리 디바이스**를 선택합니다.
4. 플랫폼에서 **iOS**를 선택합니다.
5. **연결된 앱**을 선택합니다.
6. 검색 창에 “EMM용 Slack”을 입력하고 앱을 선택합니다.
7. **확인**을 클릭한 다음 **구성 설정**을 선택합니다. 
    - 구성 키와 키의 값에 대한 자세한 내용은 [Slack의 AppConfig 웹 페이지](https://www.appconfig.org/company/slack/)의 "기술" 탭에 있는 문서를 참조하세요.
8. **확인**을 선택하고 **추가**를 선택합니다.
9. 검색 창에 “Slack 앱 구성 정책 테스트”를 입력하고 방금 추가한 정책을 선택합니다.
10. 관리에서 **할당**을 선택합니다.
11. 할당 대상에서 **모든 사용자 + 모든 디바이스**를 선택합니다.
12. **저장**을 클릭합니다.

### <a name="optional-create-an-ios-device-compliance-policy"></a>(선택 사항) iOS 디바이스 준수 정책 만들기
Intune 디바이스 준수 정책을 설정하여 디바이스가 준수 상태로 간주하기 위해 충족해야 하는 조건을 설정합니다. 이 자습서에서는 iOS 디바이스의 디바이스 준수 정책을 만듭니다. 준수 정책은 플랫폼별로 다르므로 Android 디바이스의 Slack 사용자를 위한 정책을 따로 만들어야 합니다.
1. Intune에서 **디바이스 준수** > **정책** > **정책 만들기**를 선택합니다.
2. 이름에 “iOS 준수 정책 테스트”를 입력합니다.
3. 설명에 “iOS 준수 정책 테스트”를 입력합니다.
4. 플랫폼에서 **iOS**를 선택합니다.
5. **디바이스 상태**를 선택합니다. 탈옥 디바이스 옆에 있는 **차단**을 선택한 후 **확인**을 선택합니다.
6. **시스템 보안**을 선택하고 암호 설정을 입력합니다. 이 자습서에서는 다음 권장 설정을 선택합니다.
    - 모바일 디바이스의 잠금을 해제하는 데 암호 필요에서 **필요**를 선택합니다.
    - 단순 암호에서 **차단**을 선택합니다.
    - 최소 암호 길이에 4를 입력합니다.
    - 필수 암호 유형에서 **영숫자**를 선택합니다.
    - 화면 잠금 후 암호를 요구하기 전까지 최대 시간(분)에서 **즉시**를 선택합니다.
    - 암호 만료(일)에 41을 입력합니다.
    - 재사용을 방지하기 위한 이전 암호 수에 5를 입력합니다.
7. **확인**을 클릭한 후 **확인**을 다시 선택합니다.
8. **만들기**를 클릭합니다.

## <a name="set-up-slack-on-android-work-profile-devices"></a>Android 회사 프로필 디바이스에서 Slack 설정
Slack 관리형 Google Play 앱을 Intune 테넌트에 추가하고 앱 구성 정책을 만들어 조직의 Android 사용자가 Intune을 EMM 공급자로 사용하여 Slack에 액세스할 수 있도록 합니다.

### <a name="add-slack-to-intune"></a>Intune에 Slack 추가
Intune에서 Slack을 관리형 Google Play 앱으로 추가하고 Slack 사용자를 할당합니다. 앱은 플랫폼별로 다르므로 iOS 디바이스의 Slack 사용자를 위한 Intune 앱을 따로 추가해야 합니다.
1. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다.
2. 앱 유형에서 **스토어 앱 - 관리형 Google Play**를 선택합니다.
3. **관리형 Google Play - 승인**을 선택합니다. 검색어 “EMM용 Slack”을 입력하고 앱을 선택합니다.
4. **승인**을 선택합니다.
5. 검색 창에 “Slack”을 입력하고 방금 추가한 앱을 선택합니다.
6. 관리에서 **할당**을 선택합니다.
7. **그룹 추가**를 선택합니다. Slack에 대해 EMM을 켤 때 영향을 받도록 선택한 사용자에 따라 **할당 유형**에서 다음을 선택할 수 있습니다.
    - **등록된 디바이스에 사용 가능** - “All members (including guests)”(모든 구성원(게스트 포함)를 선택한 경우
    - **등록 유무에 상관없이 사용 가능** - “All members (excluding guests)”(모든 구성원(게스트 제외)) 또는 “선택 사항”을 선택한 경우
8. 포함된 그룹을 선택하고 이 앱을 모든 사용자가 사용할 수 있도록 설정에서 **예**를 선택합니다.
9. **확인**을 클릭한 다음 **확인**을 다시 클릭합니다.
10. **저장**을 클릭합니다.

### <a name="add-an-app-configuration-policy-for-slack"></a>Slack을 위한 앱 구성 정책 추가
Slack을 위한 앱 구성 정책을 추가합니다. 관리 디바이스의 앱 구성 정책은 플랫폼별로 다르므로 iOS 디바이스의 Slack 사용자를 위한 정책을 따로 추가해야 합니다.
1. Intune에서 **클라이언트 앱** > **앱 구성 정책** > **추가**를 선택합니다.
2. 이름에 Slack 앱 구성 정책 테스트를 입력합니다.
3. 디바이스 등록 유형에서 **관리 디바이스**를 선택합니다.
4. 플랫폼에서 **Android**를 선택합니다.
5. **연결된 앱**을 선택합니다.
6. 검색 창에 “Slack”을 입력하고 앱을 선택합니다.
7. **확인**을 선택한 다음 **구성 설정**을 선택합니다.
    - 구성 키와 키의 값에 대한 자세한 내용은 [Slack의 AppConfig 웹 페이지](https://www.appconfig.org/company/slack/)의 "기술" 탭에 있는 문서를 참조하세요.
8. **확인**을 클릭하고 **추가**를 선택합니다.
9. 검색 창에 “Slack 앱 구성 정책 테스트”를 입력하고 방금 추가한 정책을 선택합니다.
10. 관리에서 **할당**을 선택합니다.
11. 할당 대상에서 **모든 사용자 + 모든 디바이스**를 선택합니다.
12. **저장**을 클릭합니다.

### <a name="optional-create-an-android-device-compliance-policy"></a>(선택 사항) Android 디바이스 준수 정책 만들기
Intune 디바이스 준수 정책을 설정하여 디바이스가 준수 상태로 간주하기 위해 충족해야 하는 조건을 설정합니다. 이 자습서에서는 Android 디바이스의 디바이스 준수 정책을 만듭니다. 준수 정책은 플랫폼별로 다르므로 iOS 디바이스의 Slack 사용자를 위한 정책을 따로 만들어야 합니다.
1. Intune에서 **디바이스 준수** > **정책** > **정책 만들기**를 선택합니다.
2. 이름에 “Android 준수 정책 테스트”를 입력합니다.
3. 설명에 “Android 준수 정책 테스트”를 입력합니다.
4. 플랫폼에서 **Android Enterprise**를 선택합니다.
5. 프로필 유형에서 **회사 프로필**을 선택합니다.
6. **디바이스 상태**를 선택합니다. 루팅된 디바이스 옆에 있는 **차단**을 선택한 후 **확인**을 선택합니다.
7. **시스템 보안**을 선택하고 **암호 설정**을 입력합니다. 이 자습서에서는 다음 권장 설정을 선택합니다.
    - 모바일 디바이스의 잠금을 해제하는 데 암호 필요에서 **필요**를 선택합니다.
    - 필수 암호 유형에서 **최소 영숫자**를 선택합니다.
    - 최소 암호 길이에 4를 입력합니다.
    - 화면 잠금 후 암호를 요구하기 전까지 최대 시간(분)에서 **15분**을 선택합니다.
    - 암호 만료(일)에 41을 입력합니다.
    - 재사용을 방지하기 위한 이전 암호 수에 5를 입력합니다.
8. **확인**을 클릭한 다음 **확인**을 다시 클릭합니다.
9. **만들기**를 클릭합니다.

## <a name="launch-slack"></a>Slack 시작

방금 만든 정책에 따라 작업 영역 중 하나에 로그인하려고 하는 모든 iOS 또는 Android 회사 프로필 디바이스는 Intune에 등록해야 합니다. 이 시나리오를 테스트하려면 Intune에 등록된 iOS 디바이스에서 EMM용 Slack을 시작해 보거나 Intune에 등록된 Android 회사 프로필 디바이스에서 Slack을 시작해 봅니다. 

## <a name="next-steps"></a>다음 단계

이 자습서의 내용
- Slack Enterprise Grid에서 Intune을 EMM(Enterprise Mobility Management) 공급자로 설정했습니다. 
- 앱 구성 정책을 만들어 iOS의 EMM용 Slack 앱 및 Android 회사 프로필 디바이스용 Slack 앱을 관리했습니다.
- Intune 디바이스 준수 정책을 만들어 Android 및 iOS 디바이스가 규격 디바이스로 간주되기 위해 충족해야 하는 조건을 설정했습니다.

앱 구성 정책에 대한 자세한 내용은 [Microsoft Intune용 앱 구성 정책](app-configuration-policies-overview.md)을 참조하세요. 디바이스 준수 정책에 대해 자세히 알아보려면 [Intune을 사용하여 조직의 리소스 액세스를 허용하도록 디바이스에서 규칙 설정](device-compliance-get-started.md)을 참조하세요.