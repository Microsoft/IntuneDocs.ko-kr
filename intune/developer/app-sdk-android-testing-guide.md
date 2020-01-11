---
title: Android용 Microsoft Intune 앱 SDK 테스트 가이드
description: Android용 Microsoft Intune 앱 SDK 테스트 가이드는 Intune 관리 Android 앱을 테스트하는 데 참고할 수 있습니다.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d473d29536b4ffdcc221c8cf61c63725bae0fa2
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75653906"
---
# <a name="microsoft-intune-app-sdk-for-android-testing-guide"></a>Android용 Microsoft Intune 앱 SDK 테스트 가이드

이 가이드는 개발자가 Intune에서 관리 하는 Android 앱을 테스트 하는 데 도움이 됩니다.  

## <a name="prerequisite-test-accounts"></a>필수 테스트 계정
미리 생성 된 데이터를 사용 하거나 사용 하지 않고 새 계정을 만들 수 있습니다. 새 계정을 만들려면 다음 단계를 수행합니다.
1. [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant) 사이트로 이동합니다. 
2. MDM(모바일 디바이스 관리)을 사용할 수 있도록 [Intune을 설정](../fundamentals/setup-steps.md)합니다.
3. [사용자를 만듭니다](../fundamentals/users-add.md).
4. [그룹을 만듭니다](../fundamentals/groups-add.md).
5. 테스트에 적합한 [라이선스를 할당](../fundamentals/licenses-assign.md)합니다.


## <a name="azure-portal-policy-configuration"></a>Azure Portal 정책 구성
[Azure Portal의 Intune 블레이드](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview)에서 [앱 보호 정책을 만들고 할당](../apps/app-protection-policies.md)합니다. Intune 블레이드에서 [앱 구성 정책을](../apps/app-configuration-policies-overview.md) 만들고 할당할 수도 있습니다.

> [!NOTE]
> 앱이 Azure Portal에 나열되지 않으면 **더 많은 앱** 옵션을 선택하고 텍스트 상자에 패키지 이름을 제공하여 정책의 대상으로 지정할 수 있습니다.

## <a name="test-cases"></a>테스트 사례

다음 테스트 사례는 구성 및 확인 단계를 제공합니다. 이 가이드는 Intune에서 관리되는 Android 앱 문제를 해결하는 데 참고할 수 있습니다.

### <a name="required-pin-and-corporate-credentials"></a>필수 PIN 및 회사 자격 증명

회사 리소스에 액세스하기 위한 PIN을 요구할 수 있습니다. 관리형 앱을 사용하려는 사용자에게 회사 인증을 적용할 수도 있습니다. 방법은 다음과 같습니다.

1. **액세스용 PIN 필요**와 **액세스용 회사 자격 증명 필요**를 **예**로 설정합니다. 자세한 내용은 [Microsoft Intune의 Android 앱 보호 정책 설정](../apps/app-protection-policy-settings-android.md#access-requirements)을 참조하세요.
2. 다음 조건을 확인합니다.
    - 앱을 시작하면 회사 포털에 등록하는 동안 사용한 PIN 입력 또는 프로덕션 사용자를 묻는 프롬프트가 표시됩니다.
    - 잘못 구성 된 Android 매니페스트, 특히 ADAL (Azure Active Directory Authentication Library) 통합 (SkipBroker, ClientID 및 Authority)의 값으로 인해 유효한 로그인 프롬프트를 표시 하지 못할 수 있습니다.
    - 프롬프트가 표시되지 않으면 잘못 통합된 `MAMActivity` 값이 원인일 수 있습니다. `MAMActivity`에 대한 자세한 내용은 [Android 용 Microsoft Intune 앱 SDK 개발자 가이드](app-sdk-android.md)를 참조하세요.

> [!NOTE] 
> 이전 테스트가 작동 하지 않을 경우 다음 테스트도 실패할 수 있습니다. [SDK](app-sdk-android.md##sdk-integration) 및 [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) 통합을 검토하세요.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>다른 앱으로 데이터 전송 및 수신 제한
회사에서 관리되는 애플리케이션 간의 데이터 전송은 다음과 같이 제어할 수 있습니다.

1. **앱에서 다른 앱으로 데이터를 전송할 수 있도록 허용**을 **정책 관리 앱**으로 설정합니다.
2. **앱이 다른 앱의 데이터를 받도록 허용**에서 **모든 앱**으로 설정합니다. 이러한 정책은 의도 및 콘텐츠 공급자 사용에 영향을 미칩니다.
3. 다음 조건을 확인합니다.
    - 비관리형 앱에서 앱으로 여는 기능이 올바르게 작동합니다.
    - 관리형 앱 간에 콘텐츠를 공유할 수 있습니다.
    - 관리형 앱에서 비관리형 앱(예: Chrome)으로 공유가 차단됩니다.

### <a name="restrict-cut-copy-and-paste"></a>잘라내기, 복사 및 붙여넣기 제한
관리형 애플리케이션에 대한 시스템 클립보드가 다음과 같이 제한됩니다.

1. **다른 앱에서 잘라내기, 복사 및 붙여넣기 제한**을 **붙여넣기에 정책 관리된 앱**으로 설정합니다.
2. 다음 조건을 확인합니다.
    - 앱에서 비관리형 앱(예: 메시지)으로 텍스트 복사하기가 차단됩니다.

### <a name="prevent-save"></a>저장 차단
**다른 이름으로 저장** 기능을 다음과 같이 제어할 수 있습니다.

1. 앱에 [통합된 다른 이름으로 저장 컨트롤](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)이 필요한 경우 **'다른 이름으로 저장' 금지**를 **예**로 설정합니다.
2. 다음 조건을 확인합니다.
    - 저장이 적절한 관리형 위치로만 제한됩니다.

### <a name="file-encryption"></a>파일 암호화
디바이스의 데이터를 다음과 같이 암호화할 수 있습니다.

1. **앱 데이터 암호화**를 **예**로 설정합니다.
2. 다음 조건을 확인합니다.
    - 정상적인 응용 프로그램 동작은 영향을 받지 않습니다.

### <a name="prevent-android-backups"></a>Android 백업 차단
앱 백업을 다음과 같이 제어할 수 있습니다.

1. [통합 백업 제한](app-sdk-android.md#protecting-backup-data)을 설정한 경우 **Android 백업 차단**을 **예**로 설정합니다.
2. 다음 조건을 확인합니다.
    - 백업이 제한됩니다.

### <a name="unenrollment"></a>등록 취소
회사 이메일 및 문서를 포함하는 관리형 앱을 원격으로 지울 수 있고, 개인 데이터가 더 이상 관리되지 않으면 암호 해독됩니다. 방법은 다음과 같습니다.

1. Azure Portal에서 [초기화 명령을 실행](../apps/apps-selective-wipe.md)합니다.
2. 앱이 초기화 처리기에 대해 등록되지 않은 경우 다음 조건을 확인합니다.
    - 앱의 전체 초기화가 발생합니다.
3. 앱이 `WIPE_USER_DATA` 또는 `WIPE_USER_AUXILARY_DATA`에 대해 등록된 경우 다음 조건을 확인합니다.
    - 관리형 콘텐츠가 앱에서 제거됩니다. 자세한 내용은 [Android용 Intune 앱 SDK 개발자 가이드 - 선택적 초기화](app-sdk-android.md#selective-wipe)를 참조하세요.

### <a name="multi-identity-support"></a>다중 ID 지원
[다중 ID 지원](app-sdk-android.md#multi-identity-optional) 통합은 위험 수준이 높은 변화이기 때문에 철저한 테스트가 필요합니다. 가장 일반적인 문제는 id (컨텍스트 및 위협 수준)를 부적절 하 게 설정 하 고 파일 (`MAMFileProtectionManager`)을 추적 하는 경우에 발생 합니다.

최소한 다음을 확인 합니다.

- **다른 이름으로 저장** 정책이 관리형 ID에 대해 제대로 작동하지 않습니다.
- 복사 및 붙여넣기 제한이 관리형에서 개인으로 올바르게 적용됩니다.
- 관리 ID에 속하는 데이터만 암호화되고 개인 파일은 수정되지 않습니다.
- 등록 취소 중 선택적 초기화가 관리 ID 데이터만 제거합니다.
- 비관리형 계정에서 관리형 계정으로 변경하면 조건부 시작을 묻는 메시지가 사용자에게 표시됩니다(처음에만).

### <a name="app-configuration-optional"></a>앱 구성(선택 사항)
관리형 앱의 동작을 구성할 수 있습니다. 앱 구성 설정이 앱에 사용되는 경우 관리자가 설정할 수 있는 모든 값이 앱에서 제대로 처리되는지 테스트해야 합니다. Intune에서 [앱 구성 정책을](../apps/app-configuration-policies-overview.md) 만들고 할당할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune에 Android 기간 업무 앱 추가](../apps/lob-apps-android.md)
