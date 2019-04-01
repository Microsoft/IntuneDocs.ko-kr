---
title: Android용 Microsoft Intune 앱 SDK 개발자 테스트 가이드
description: Android 테스트 가이드에 대 한 Microsoft Intune 앱 SDK를 사용 하면 Intune 관리 Android 앱을 테스트할 수 있습니다.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4203f424c395399cb0ed1e7472b006602aa0b210
ms.sourcegitcommit: db7a6b8fc9e82dae4f2111ca0b2d3c14e33658f9
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072473"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Android용 Microsoft Intune 앱 SDK 개발자 테스트 가이드

Android 테스트 가이드에 대 한 Microsoft Intune 앱 SDK는 Intune 관리 Android 앱을 테스트할 수 있도록 설계 되었습니다.  

## <a name="prerequisite-test-accounts"></a>필수 구성 요소 테스트 계정
새 계정 및 미리 생성 된 데이터 없이 만들 수 있습니다. 새 계정을 만들려면 다음 단계를 수행합니다.
1. 로 이동 합니다 [Microsoft 데모](https://demos.microsoft.com/environments/create/tenant) 사이트입니다. 
2. [Intune 설정](https://docs.microsoft.com/intune/setup-steps) 모바일 장치 관리 (MDM)를 사용 하도록 설정 합니다.
3. [사용자를 만들](https://docs.microsoft.com/intune/users-add)합니다.
4. [그룹을 만듭니다](https://docs.microsoft.com/intune/groups-add).
5. [라이선스 할당](https://docs.microsoft.com/intune/licenses-assign) 테스트에 적합 하 게 합니다.


## <a name="azure-portal-policy-configuration"></a>Azure portal 정책 구성
[앱 보호 정책 만들기 및 할당](https://docs.microsoft.com/intune/app-protection-policies) 에 [Azure portal의 Intune 블레이드에서](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview)합니다. 프로그램 [앱 구성 정책](https://docs.microsoft.com/intune/app-configuration-policies-overview) 수 생성 되어 Intune 블레이드에서 할당 합니다.

> [!NOTE]
> Azure portal에서 앱 없으면 해당 정책을 사용 하 여 하 여 대상를 선택 하는 **더 많은 앱** 옵션 및 텍스트 상자에 패키지 이름을 제공 합니다.

> [!IMPORTANT]
> 적용할 앱 구성 정책에 대 한 등록 사용자 수 대상으로 지정 합니다는 [Intune 앱 보호 정책](https://docs.microsoft.com/intune/app-protection-policy)합니다.

## <a name="test-cases"></a>테스트 사례

다음 테스트 사례 구성 및 확인 단계를 제공 합니다. Intune 관리 Android 앱 문제를 해결 하려면이 지침을 따르세요.

### <a name="required-pin-and-corporate-credentials"></a>PIN 필요 하 고 회사 자격 증명

회사 리소스에 액세스 하려면 pin을 요구할 수 있습니다. 또한 사용자는 관리 되는 앱을 사용 하려면 먼저 회사 인증을 적용할 수 있습니다. 이러한 요구 사항을 설정 하려면 다음 단계를 사용 합니다.

1. 구성 **액세스용 PIN 필요** 하 고 **액세스용 회사 자격 증명** 하 **예**합니다. 자세한 내용은 [Microsoft Intune의 Android 앱 보호 정책 설정](app-protection-policy-settings-android.md#access-requirements)을 참조하세요.
2. 다음 조건을 확인합니다.
    - 앱 시작 PIN 입력/설정 및/또는 회사 포털을 사용 하 여 등록 중 사용 된 프로덕션 사용자에 대 한 프롬프트를 제공 해야 합니다.
    - 유효한 로그인 프롬프트를 표시 하는 오류는 잘못 구성 된 android 매니페스트를 특별히 ADAL 통합 (SkipBroker, ClientID, 및 인증 기관)에 대 한 값 때문일 수 있습니다.
    - 모든 프롬프트를 표시 하는 잘못 통합 원인일 수 있습니다 `MAMActivity` 값입니다. 에 대 한 자세한 내용은 `MAMActivity`를 참조 하세요 [Android 개발자 가이드에 대 한 Microsoft Intune 앱 SDK](app-sdk-android.md)합니다.

> [!NOTE] 
> 위의 테스트가 작동 하지 않는 경우 아래 테스트 가능성이 실패할 수도 있습니다. 검토 [SDK](app-sdk-android.md##sdk-integration) 하 고 [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) 통합 합니다.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>다른 앱과 데이터를 받고 전송 제한
다음과 같이 회사 관리 되는 응용 프로그램 간의 데이터 전송을 제어할 수 있습니다.

1. 설정할 **앱 다른 앱으로 데이터를 전송할 수 있도록 허용** 하 **정책 관리 앱**합니다.
2. **앱이 다른 앱의 데이터를 받도록 허용**에서 **모든 앱**으로 설정합니다. 사용 의도 및 콘텐츠 공급자는 이러한 정책에 의해 영향을 미칩니다.
3. 다음 조건을 확인합니다.
    - 관리 되지 않는 앱에서 앱 함수를 제대로 열리지 합니다.
    - 관리 되는 앱 사이의 콘텐츠 공유가 허용 됩니다.
    - 관리 되지 않는 앱 (예: Chrome)에 관리 되는 앱에서 공유는 차단 됩니다.

### <a name="restrict-cut-copy-and-paste"></a>잘라내기, 복사 및 붙여넣기 제한
관리 되는 응용 프로그램에 다음과 같은 시스템 클립보드를 제한할 수 있습니다.

1. 설정할 **잘라내기, 복사 및 붙여넣기 제한 다른 앱과** 하 **붙여넣기에 정책 관리**합니다.
2. 다음 조건을 확인합니다.
    - 에 관리 되는 앱에서 텍스트를 복사는 관리 되지 않는 앱 (예: 메시지)이 차단 됩니다.

### <a name="prevent-save-as"></a>**다른 이름으로 저장** 차단
제어할 수 있습니다 **다른 이름으로 저장** 다음과 같은 기능:

1. 앱에 필요한 경우 [통합으로 저장 컨트롤](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)설정 **' 다른 이름으로 저장 ' 사용 안 함** 하 **예**합니다.
2. 다음 조건을 확인합니다.
    - 저장 위치로 적절 한 관리 되는 제한 됩니다.

### <a name="file-encryption"></a>파일 암호화
다음과 같이 장치에서 데이터를 암호화할 수 있습니다.

1. 설정할 **앱 데이터 암호화** 하 **예**합니다.
2. 다음 조건을 확인합니다.
    - 일반적인 응용 프로그램 동작을 받지 않습니다.

### <a name="prevent-android-backups"></a>Android 백업 차단
다음과 같이 앱 백업을 제어할 수 있습니다.

1. 설정한 경우 [백업 제한 사항 통합](app-sdk-android.md#protecting-backup-data), 구성 **Android 백업 금지** 하 **예**합니다.
2. 다음 조건을 확인합니다.
    - 백업은 제한 됩니다.

### <a name="unenrollment"></a>등록 취소
회사 메일 및 문서를 포함 하는 관리 되는 앱을 원격으로 초기화할 수 없습니다 하 고 개인 데이터에는 더 이상 관리 다음과 같은 경우 암호가 해독 됩니다.

1. Azure portal에서 [초기화를 실행할](https://docs.microsoft.com/intune/apps-selective-wipe)합니다.
2. 된 초기화 처리기에 다음 조건 확인에 대 한 앱 등록 하지 않습니다.
    - 앱의 전체 초기화를 발생합니다.
3. 앱에 대 한 등록 된 경우 `WIPE_USER_DATA` 또는 `WIPE_USER_AUXILARY_DATA`, 다음 조건을 확인 합니다.
    - 관리 되는 콘텐츠는 앱에서 제거 됩니다. 자세한 내용은 [Android 개발자 가이드-선택적 초기화에 대 한 Intune 앱 SDK](app-sdk-android.md#selective-wipe)합니다.

### <a name="multi-identity"></a>다중 ID
통합 [다중 id 지원](app-sdk-android.md#multi-identity-optional) 철저히 테스트 해야 하는 위험 수준이 높은 변경 합니다. 가장 일반적인 문제 (위협 수준 및 컨텍스트) id의 잘못 된 설정 및 파일에도 추적으로 인해 됩니다 (`MAMFileProtectionManager`).

최소한 다음 다중 id 시나리오는 유효성을 재검사:

- **다른 이름으로 저장** 정책이 관리 되는 id에 대 한 제대로 작동 합니다.
- 복사/붙여넣기 제한에서 제대로 적용 개인을 관리 합니다.
- 관리 서비스 id에 속하는 데이터만 암호화 됩니다 하 고 개인 파일은 수정 되지 않습니다.
- 등록 취소 하는 동안 선택적 초기화만 관리 되는 id 데이터를 제거합니다.
- 관리 되지 않는 관리 되는 계정 (첫 번째 시간에만 해당)로 변경할 때 최종 사용자는 조건부 시작에 대 한 라는 메시지가 표시 됩니다.

### <a name="app-configuration-optional"></a>(선택 사항) 앱 구성
다음과 같이 관리 되는 앱의 동작을 구성할 수 있습니다.

1. 앱 구성 설정을 사용 하는 앱을 하는 경우 앱 (관리자로) 설정할 수 있는 모든 값을 올바르게 처리를 테스트 해야 합니다. [앱 구성 정책을](https://docs.microsoft.com/intune/app-configuration-policies-overview) 만들고 Intune을 사용 하 여 할당할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune에 Android 기간 업무 앱을 추가합니다](lob-apps-android.md).
