---
title: 앱 보호 정책 만들기 및 배포
titleSuffix: Microsoft Intune
description: 이 항목에서는 Microsoft Intune APP(앱 보호 정책)를 만들고 사용자에게 할당하는 방법을 설명합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b5f973e5ce169edcf6149b0588c905d8497cca2
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885753"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>앱 보호 정책을 만들고 할당하는 방법

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

조직의 사용자를 위해 Microsoft Intune APP(앱 보호 정책)를 만들고 할당하는 방법을 알아봅니다. 이 항목에서는 기존 정책을 수정하는 방법을 설명합니다.

## <a name="before-you-begin"></a>시작하기 전에

앱 보호 정책은 Intune에서 관리되거나 관리되지 않을 수 있는 디바이스에서 실행되는 앱에 적용할 수 있습니다. 앱 보호 정책의 작동 방식 및 Intune 앱 보호 정책에서 지원되는 시나리오에 대한 자세한 설명은 [Microsoft Intune 앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

MAM을 지원하는 앱 목록을 확인하려면 [MAM 앱 목록](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)을 참조하세요.

앱 보호 정책을 준비하기 위해 Microsoft Intune에 조직의 LOB(기간 업무) 앱을 추가하는 방법은 [Microsoft Intune에 앱 추가](apps-add.md)를 참조하세요.

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>iOS/iPadOS 및 Android 앱용 앱 보호 정책

iOS/iPadOS 및 Android 앱용 앱 보호 정책을 만드는 경우 최신 Intune 프로세스 흐름에 따라 새 앱 보호 정책을 만듭니다.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>iOS/iPadOS 또는 Android 앱 보호 정책 만들기
1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. Intune 포털에서 **앱** > **앱 보호 정책**을 선택합니다. **앱 보호 정책** 세부내용이 열리고, 여기서 새 정책을 만들고 기존 정책을 편집할 수 있습니다.
3. **정책 만들기**를 선택하고 **iOS/iPadOS** 또는 **Android**를 선택합니다. **정책 만들기** 창이 표시됩니다.
4. **기본 사항** 페이지에서 다음 값을 추가합니다.

    | 값 | 설명 |
    |--------------|------------------------------------------------|
    | Name | 이 앱 보호 정책의 이름입니다. |
    | 설명 | [선택 사항]이 앱 보호 정책의 설명입니다. |


    **플랫폼** 값은 위의 선택에 따라 설정됩니다.

    ![정책 만들기 창의 기본 사항 페이지 스크린샷](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. **다음**을 클릭하여 **앱** 페이지를 표시합니다.<br>
    **앱** 페이지에서는 다양한 디바이스의 앱에 이 정책을 적용하는 방법을 선택할 수 있습니다. 앱을 하나 이상 추가해야 합니다.<p>
    
    | 값/옵션 | 설명 |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | 모든 디바이스 유형에 있는 앱 대상 | 관리 상태의 디바이스에 있는 앱을 정책 대상으로 지정하려면 이 옵션을 사용합니다. 특정 디바이스 유형에 있는 앱을 대상으로 지정하려면 **아니요**를 선택합니다. 자세한 내용은 [디바이스 관리 상태에 따른 대상 앱 보호 정책](#target-app-protection-policies-based-on-device-management-state)을 참조하세요. |
    |     디바이스 유형 | 이 정책이 MDM 관리형 디바이스 또는 비관리형 디바이스에 적용되는지 여부를 지정하려면 이 옵션을 사용합니다. iOS 앱 정책의 경우 **관리되지 않음** 및 **관리** 디바이스 중에서 선택합니다. Android 앱 정책의 경우 **관리되지 않음**, **Android 디바이스 관리자** 및 **Android Enterprise** 중에서 선택합니다.  |
    | 공개 앱 | **공개 앱 선택**을 클릭하여 대상으로 지정할 앱을 선택합니다. |
    | 사용자 지정 앱 | **사용자 지정 앱 선택**을 클릭하여 번들 ID에 따라 대상으로 지정할 사용자 지정 앱을 선택합니다. |
    
    선택한 앱이 공개 및 사용자 지정 앱 목록에 표시됩니다. 
6. **다음**을 클릭하여 **데이터 보호** 페이지를 표시합니다.<br>
    이 페이지에서는 잘라내기, 복사, 붙여넣기 및 다른 이름으로 저장 제한을 포함한 DLP(데이터 손실 방지) 컨트롤의 설정을 제공합니다. 이 설정은 사용자가 이 앱 보호 정책이 적용되는 앱의 데이터와 상호 작용하는 방법을 결정합니다.

    **데이터 보호 설정**:<br>
    - **iOS/iPadOS 데이터 보호** - 자세한 내용은 [iOS 앱 보호 정책 설정 - 데이터 보호](~/apps/app-protection-policy-settings-ios.md#data-protection)를 참조하세요.
    - **Android 데이터 보호** - 자세한 내용은 [Android 앱 보호 정책 설정 - 데이터 보호](~/apps/app-protection-policy-settings-android.md#data-protection)를 참조하세요.

7. **다음**을 클릭하여 **액세스 요구 사항** 페이지를 표시합니다.<br>
    이 페이지에서는 사용자가 업무용으로 앱에 액세스하기 위해 충족해야 하는 PIN 및 자격 증명 요구 사항을 구성할 수 있는 설정을 제공합니다. 
 
    **액세스 요구 사항 설정**:<br>
    - **iOS/iPadOS 액세스 요구 사항** - 자세한 내용은 [iOS 앱 보호 정책 설정 - 액세스 요구 사항](~/apps/app-protection-policy-settings-ios.md#access-requirements)을 참조하세요.
    - **Android 액세스 요구 사항** - 자세한 내용은 [Android 앱 보호 정책 설정 - 액세스 요구 사항](~/apps/app-protection-policy-settings-android.md#access-requirements)을 참조하세요.

8. **다음**을 클릭하여 **조건부 시작** 페이지를 표시합니다.<br>
    이 페이지에서는 앱 보호 정책에 대한 로그인 보안 요구 사항을 설정하는 설정을 제공합니다. **설정**을 선택하고 사용자가 회사 앱에 로그인하기 위해 충족해야 하는 **값**을 입력합니다. 그런 다음, 사용자가 요구 사항을 충족하지 않을 경우 **작업**을 선택합니다. 경우에 따라 단일 설정에 대해 여러 작업을 구성할 수 있습니다.

    **조건부 시작 설정**:<br>
    - **iOS/iPadOS 조건부 시작** - 자세한 내용은 [iOS 앱 보호 정책 설정 - 조건부 시작](~/apps/app-protection-policy-settings-ios.md#conditional-launch)을 참조하세요.
    - **Android 조건부 시작** - 자세한 내용은 [Android 앱 보호 정책 설정 - 조건부 시작](~/apps/app-protection-policy-settings-android.md#conditional-launch)을 참조하세요.

9. **다음**을 클릭하여 **할당** 페이지를 표시합니다.<br>
   **할당** 페이지에서는 사용자 그룹에 앱 보호 정책을 할당할 수 있습니다.

10. **다음: 검토 + 만들기**를 클릭하여 이 앱 보호 정책에 대해 입력한 값과 설정을 검토합니다.

11. 작업이 완료되면 **만들기**를 클릭하여 Intune에서 앱 보호 정책을 만듭니다. 

    > [!TIP]
    > 이러한 정책 설정은 회사 컨텍스트에서 앱을 사용하는 경우에만 적용됩니다. 최종 사용자가 앱을 사용하여 개인 작업을 수행하는 경우에는 이러한 정책의 영향을 받지 않습니다. 새 파일을 만들면 해당 파일은 개인 파일로 간주됩니다. 

최종 사용자는 앱 스토어 또는 Google Play에서 앱을 다운로드할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
* [Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](../fundamentals/end-user-mam-apps-android.md)
* [iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>기존 정책 변경
기존 정책을 편집할 수 있으며 대상으로 지정된 사용자에게 적용할 수 있습니다. 그러나 기존 정책을 변경하는 경우 앱에 이미 로그인한 사용자에게는 8시간 동안 변경 내용이 표시되지 않습니다.

변경 사항의 결과를 즉시 확인하려면 최종 사용자가 앱에서 로그아웃한 다음, 다시 로그인해야 합니다.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>정책과 연결된 앱 목록을 변경하려면

1. **앱 보호 정책** 창에서 변경하려는 정책을 선택합니다.

2. *Intune 앱 보호* 창에서 **속성**을 선택합니다.

3. *앱* 섹션 옆에 있는 **편집**을 선택합니다.

4. **앱** 페이지에서는 다양한 디바이스의 앱에 이 정책을 적용하는 방법을 선택할 수 있습니다. 앱을 하나 이상 추가해야 합니다.<p>
    
    | 값/옵션 | 설명 |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | 모든 디바이스 유형에 있는 앱 대상 | 관리 상태의 디바이스에 있는 앱을 정책 대상으로 지정하려면 이 옵션을 사용합니다. 특정 디바이스 유형에 있는 앱을 대상으로 지정하려면 **아니요**를 선택합니다. 자세한 내용은 [디바이스 관리 상태에 따른 대상 앱 보호 정책](#target-app-protection-policies-based-on-device-management-state)을 참조하세요. |
    |     디바이스 유형 | 이 정책이 MDM 관리형 디바이스 또는 비관리형 디바이스에 적용되는지 여부를 지정하려면 이 옵션을 사용합니다. iOS 앱 정책의 경우 **관리되지 않음** 및 **관리** 디바이스 중에서 선택합니다. Android 앱 정책의 경우 **관리되지 않음**, **Android 디바이스 관리자** 및 **Android Enterprise** 중에서 선택합니다.  |
    | 공개 앱 | **공개 앱 선택**을 클릭하여 대상으로 지정할 앱을 선택합니다. |
    | 사용자 지정 앱 | **사용자 지정 앱 선택**을 클릭하여 번들 ID에 따라 대상으로 지정할 사용자 지정 앱을 선택합니다. |

    선택한 앱이 공개 및 사용자 지정 앱 목록에 표시됩니다. 

5. **검토 + 만들기**를 클릭하여 이 정책에 대해 선택한 앱을 검토합니다.

6. 작업이 완료되면 **저장**을 클릭하여 앱 보호 정책을 업데이트합니다.
 
#### <a name="to-change-the-list-of-user-groups"></a>사용자 그룹 목록을 변경하려면

1. **앱 보호 정책** 창에서 변경하려는 정책을 선택합니다.

2. *Intune 앱 보호* 창에서 **속성**을 선택합니다.

3. *할당* 섹션 옆에 있는 **편집**을 선택합니다.

4. 새 사용자 그룹을 정책에 추가하려면 *포함* 탭에서 **포함할 그룹 선택**을 선택한 다음, 사용자 그룹을 선택합니다. **선택**을 선택하여 그룹을 추가합니다. 

5. 사용자 그룹을 제외하려면 *제외* 탭에서 **제외할 그룹 선택**을 선택하고 사용자 그룹을 선택합니다. **선택**을 선택하여 사용자 그룹을 제거합니다.  

6. 이전에 추가된 그룹을 삭제하려면 *포함* 또는 *제외* 탭에서 줄임표(...)를 선택하고 **삭제**를 선택합니다.

7. **검토 + 만들기**를 클릭하여 이 정책에 대해 선택한 사용자 그룹을 검토합니다.

8. 할당 변경이 완료되면 **저장**을 선택하여 구성을 저장하고 새 사용자 세트에 정책을 배포합니다. 구성을 저장하기 전에 **취소**를 선택하면 *포함* 및 *제외* 탭에서 변경한 모든 내용이 삭제됩니다.

### <a name="to-change-policy-settings"></a>정책 설정을 변경하려면

1. **앱 보호 정책** 창에서 변경하려는 정책을 선택합니다.

2. *Intune 앱 보호* 창에서 **속성**을 선택합니다.

3. 변경할 설정에 해당하는 섹션 옆의 **편집**을 선택합니다. 그런 다음, 설정을 새 값으로 변경합니다.

7. **검토 + 만들기**를 클릭하여 이 정책에 대해 업데이트된 설정을 검토합니다.

4. **저장**을 선택하여 변경 내용을 저장합니다. 모든 변경 내용이 완료될 때까지 설정 영역을 선택하고 수정한 다음, 변경 내용을 저장하는 프로세스를 반복합니다. 그런 다음, *Intune 앱 보호 - 속성* 창을 닫을 수 있습니다. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>디바이스 관리 상태에 따른 대상 응용 프로그램 보호 정책
대부분 조직에서는 최종 사용자가 Intune 앱 보호 정책을 사용하여 보호되는 관리되지 않는 디바이스 및 회사 소유 디바이스와 같은 Intune MDM(모바일 디바이스 관리) 모두를 사용할 수 있게 하는 것이 일반적입니다. 관리되지 않는 디바이스는 BYOD(Bring Your Own Devices)라고도 알려져 있습니다.

Intune 앱 보호 정책이 사용자의 ID를 대상으로 지정하기 때문에 사용자에 대한 보호 설정은 등록된 디바이스(관리된 MDM) 및 미등록된 디바이스(관리되지 않는 MDM) 모두에 적용될 수 있습니다. 따라서 Intune 등록 또는 미등록 iOS 및 Android 디바이스에 Intune 앱 보호 정책을 대상으로 지정할 수 있습니다. 엄격한 DLP(데이터 손실 방지) 컨트롤이 적절히 마련되어 있는 관리되지 않는 디바이스에 대해 하나의 보호 정책이 있을 수 있고, DLP 컨트롤이 조금 더 느슨할 수 있는 MDM 관리 디바이스에 대해 별도의 보호 정책이 있을 수 있습니다. 이것이 개인 Android 엔터프라이즈 디바이스에서 작동하는 방식에 대한 자세한 내용은 [앱 보호 정책 및 회사 프로필](android-deployment-scenarios-app-protection-work-profiles.md)을 참조하세요.

이러한 정책을 만들려면 Intune 콘솔에서 **앱** > **앱 보호 정책**으로 이동한 다음, **정책 만들기**를 선택합니다. 기존 앱 보호 정책을 편집할 수도 있습니다. 앱 보호 정책을 관리형 디바이스 및 비관리형 디바이스 모두에 적용하려면 **앱** 페이지로 이동하여 **모든 디바이스 유형에 있는 앱 대상**이 기본값인 **예**로 설정되어 있는지 확인합니다. 관리 상태에 따라 할당을 세부적으로 할당하려면 **모든 디바이스 유형에 있는 앱 대상**을 **아니요**로 설정합니다. 

### <a name="device-types"></a>디바이스 유형

- **관리되지 않음**: 관리되지 않는 디바이스는 Intune MDM 관리가 검색되지 않은 디바이스입니다. 여기에는 타사 MDM 공급업체에서 관리하는 디바이스가 포함됩니다.
- **Intune 관리 디바이스**: 관리 디바이스는 Intune MDM에서 관리합니다.
- **Android 디바이스 관리자**: Android 디바이스 관리 API를 사용하는 Intune 관리 디바이스입니다.
- **Android 엔터프라이즈**: Android 엔터프라이즈 회사 프로필 또는 Android 엔터프라이즈 전체 디바이스 관리를 사용하는 Intune 관리 디바이스입니다.

> [!NOTE]
> Android 디바이스에는 선택한 디바이스 유형에 관계없이 Intune 회사 포털 앱을 설치하라는 메시지가 표시됩니다. 예를 들어 'Android 엔터프라이즈'를 선택하면 관리되지 않는 Android 디바이스 사용자에게는 계속 메시지가 표시됩니다.

iOS의 경우 Intune에 등록된 디바이스의 앱에 APP(앱 보호 정책) 설정을 지정하려면 추가 앱 구성 설정이 필요합니다.

- 모든 MDM 관리되는 애플리케이션에 대해 **IntuneMAMUPN**을 구성해야 합니다. 자세한 내용은 [Microsoft Intune에서 iOS 앱 간의 데이터 전송 관리 방법](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm)을 참조하세요.
- 모든 타사 및 LOB MDM 관리 애플리케이션에 대해 **IntuneMAMDeviceID**를 구성해야 합니다. **IntuneMAMDeviceID**는 디바이스 ID 토큰으로 구성되어야 합니다. 예: `key=IntuneMAMDeviceID, value={{deviceID}}` 자세한 내용은 [관리되는 iOS 디바이스용 앱 구성 정책 추가](app-configuration-policies-use-ios.md)를 참조하세요.
- **IntuneMAMDeviceID**만 구성된 경우 Intune 앱은 디바이스를 관리되지 않는 것으로 간주합니다.

> [!NOTE]
> 디바이스 관리 상태에 따른 앱 보호 정책에 대한 특정 iOS 지원 내용은 [관리 상태에 따라 대상으로 지정된 MAM 보호 정책](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state)을 참조합니다.

## <a name="policy-settings"></a>정책 설정
iOS 및 Android에 대한 정책 설정의 전체 목록을 보려면 다음 링크 중 하나를 선택합니다.

- [iOS 정책](app-protection-policy-settings-ios.md)
- [Android 정책](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>다음 단계
[규정 준수 및 사용자 상태 모니터링](app-protection-policies-monitor.md)

## <a name="see-also"></a>참고 항목
* [Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](../fundamentals/end-user-mam-apps-android.md)
* [iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](../fundamentals/end-user-mam-apps-ios.md)
