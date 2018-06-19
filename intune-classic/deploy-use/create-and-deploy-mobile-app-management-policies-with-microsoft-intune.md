---
title: MAM 정책 만들기 및 배포
description: 이 항목의 단계별 지침에 따라 모바일 앱 관리 정책을 만들고 배포합니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cc133071f4d6c0d1a3bbb3acc7c0bd5cb45b6cef
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31026417"
---
# <a name="create-and-deploy-app-protection-policies-with-microsoft-intune"></a>Microsoft Intune으로 앱 보호 정책 만들기 및 배포

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

이 항목에서는 **Azure Portal**에서 앱 보호 정책을 만드는 과정을 설명합니다. Azure Portal은 앱 보호 정책을 만들기 위한 새로운 관리 콘솔이며, 이 포털을 사용하여 앱 보호 정책을 만드는 것이 좋습니다. Azure Portal에서는 다음 MAM 시나리오를 지원합니다.

- Intune에 등록된 장치
- 타사 MDM 솔루션에서 관리되는 장치
- MDM 솔루션(BYOD)에서 관리되지 않는 장치

> [!IMPORTANT]
> **Intune 관리 콘솔**을 사용하여 장치를 관리하는 경우 다음 몇 가지 사항을 고려합니다.
> 
> * [Intune 관리 콘솔](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)을 사용하여 Intune에 등록된 장치의 앱을 지원하는 앱 보호 정책을 만들 수 있습니다.
> * Intune 관리 콘솔에서 만든 앱 보호 정책은 Azure Portal에 가져올 수 없습니다.  Azure Portal에서 앱 보호 정책을 다시 만들어야 합니다.
> 
> * Intune 관리 콘솔에는 일부 앱 보호 정책 설정이 나타나지 않을 수 있습니다. Azure Portal은 앱 보호 정책을 만들기 위한 새 관리 콘솔입니다.
> 
> * 관리되는 앱을 배포하려면 Intune 관리 콘솔에서 앱 보호 정책을 만들어야 합니다. 이 경우 Intune 관리 포털과 Azure Portal 모두에서 앱 보호 정책을 만들 수 있습니다. Intune 관리 콘솔을 사용하면 관리되는 앱을 배포할 수 있고 새로운 관리 콘솔 Azure Portal에서는 모든 앱 보호 정책 설정을 사용할 수 있습니다.
> 
> * Intune 관리 콘솔과 Azure Portal 둘 다에서 앱 보호 정책을 만들 경우 Azure Portal에서 만든 정책이 앱에 적용됩니다.

Android 및 iOS 플랫폼에 지원되는 정책 설정의 목록을 보려면 다음 중 하나를 선택합니다.

> [!div class="op_single_selector"]
> - [iOS 정책](ios-mam-policy-settings.md)
> - [Android 정책](android-mam-policy-settings.md)

- 앱 보호 정책의 작동 방식 및 Intune 앱 보호 정책으로 지원되는 시나리오에 대한 자세한 설명은 [앱 보호 정책을 사용하여 앱 데이터 보호](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)를 참조하세요.

##  <a name="create-an-app-protection-policy"></a>앱 보호 정책 만들기
앱 보호 정책은 Azure Portal에서 만듭니다. 처음으로 Azure Portal을 사용하는 경우 [Microsoft Intune 앱 보호 정책용 Azure Portal](azure-portal-for-microsoft-intune-mam-policies.md)을 읽어 Azure Portal에 대해 자세히 알아보세요. 앱 보호 정책을 만들기 전에 [필수 조건 및 지원](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md) 정보를 검토하세요.

앱 보호 정책을 만들려면 다음 단계를 따르세요.

1. [Azure Portal](https://portal.azure.com)로 이동한 다음 자격 증명을 입력합니다.

2. **추가 서비스**를 선택하고, "Intune"을 입력합니다.

3. **Intune 앱 보호**를 선택합니다.

4. **Intune 모바일 응용 프로그램 관리 &gt; 설정**을 선택하여 **모든 설정** 블레이드를 엽니다.

    ![Intune 모바일 응용 프로그램 관리 블레이드의 스크린 샷](../media/AppManagement/AzurePortal_MAM_Mainblade-2.png)

2.  **모든 설정** 블레이드에서 **앱 정책**을 선택합니다. **앱 정책** 블레이드가 열리며, 여기서 새 정책을 만들고 기존 정책을 편집합니다. **정책 추가**를 선택합니다.

    ![정책 메뉴 추가 옵션을 강조 표시한 앱 정책 블레이드의 스크린 샷 ](../media/AppManagement/AzurePortal_MAM_AddPolicy.png)

3.  정책의 이름을 입력하고, 간략한 설명을 추가한 다음 플랫폼 형식을 선택하여 iOS 또는 Android에 대한 정책을 만듭니다. 각 플랫폼에 대해 여러 개의 정책을 만들 수 있습니다.

    ![정책 추가 블레이드의 스크린 샷](../media/AppManagement/AzurePortal_MAM_AddPolicy_only.png)

4.  **앱**을 선택하여 **앱 블레이드**를 열면 사용할 수 있는 앱 목록이 표시됩니다. 만들고 있는 정책과 연결할 앱을 목록에서 하나 이상 선택합니다. 앱을 선택한 후 **앱** 블레이드 맨 아래에 있는 **선택** 단추를 선택하여 선택 내용을 저장합니다.

    > [!IMPORTANT]
    > 정책을 만들려면 앱을 하나 이상 선택해야 합니다.

5.  **정책 추가 블레이드**에서 **필요한 설정 구성** 을 선택하여 정책 설정 블레이드를 엽니다.

    **데이터 재배치** 및 **액세스**라는 두 범주의 정책 설정이 있습니다.  데이터 재배치 정책은 앱 내부 및 외부로 데이터 이동에 적용할 수 있는 반면, 액세스 정책은 최종 사용자가 회사 컨텍스트에서 앱에 액세스하는 방법을 결정합니다.
    정책 설정에는 기본값이 있습니다. 이 기본값이 요구 사항을 충족하는 경우에는 변경할 필요가 없습니다.

    > [!TIP]
    > 이러한 정책 설정은 회사 컨텍스트에서 앱을 사용하는 경우에만 적용됩니다.  최종 사용자가 앱을 사용하여 개인 작업을 수행하는 경우에는 이러한 정책의 영향을 받지 않습니다.

    ![정책 추가 블레이드와 설정 블레이드의 스크린 샷](../media/AppManagement/AzurePortal_MAM_PolicySettings.png)

6.  **확인**을 선택하여 이 구성을 저장합니다. 이제 **정책 추가** 블레이드로 돌아왔습니다. **만들기**를 클릭하여 정책을 만들고 설정을 저장합니다.

    ![앱 및 설정이 구성되었음을 보여 주는 정책 추가 블레이드의 스크린 샷](../media/AppManagement/AzurePortal_MAM_CreatePolicy.png)

이전 절차에서 설명한 대로 정책 만들기를 완료하면 사용자에게 배포되지 않습니다. 정책을 배포하려면 "사용자에게 정책 배포" 섹션을 참조하세요.

> [!IMPORTANT]
> Intune 관리 콘솔을 사용하여 앱에 대한 앱 보호 정책을 만들고 Azure Portal을 사용하여 앱 보호 정책을 만드는 경우 Azure Portal을 사용하여 만든 정책이 우선적으로 적용됩니다. 그러나 Intune 또는 Configuration Manager 콘솔의 보고 기능이 Intune 관리 콘솔에서 만든 정책 설정을 보고합니다. 예를 들면 다음과 같습니다.
>
> -   Intune 관리 콘솔에서는 앱에서 복사를 차단하는 앱 보호 정책을 만들고,
> -   Azure 콘솔에서는 앱에서 복사를 허용하는 앱 보호 정책을 만들었습니다.
> -   두 정책을 모두 동일한 앱에 연결합니다.
> -   Azure 콘솔에서 만든 정책이 우선 적용되어 복사가 허용됩니다.
> -   그러나 Intune 콘솔의 상태 및 보고서에 복사가 차단되었다고 잘못 표시됩니다.

## <a name="line-of-business-lob-apps-optional"></a>LOB(기간 업무) 앱(선택 사항)

Intune 1703 버전부터 새 앱 보호 정책을 만들 때 LOB 앱을 Intune에 일반적으로 추가할 수 있습니다. 따라서 완전한 앱 배포 권한 없이도 MAM SDK를 사용하여 LOB 앱에 대한 앱 보호 정책을 정의할 수 있습니다.
/intune/app-sdk-get-started
> [!TIP]
> [Intune 앱 SDK](/intune/app-sdk-get-started) 워크플로를 진행할 때에도 LOB 앱을 Intune에 추가할 수 있습니다.

> [!IMPORTANT]
> 사용자가 MAM 앱 배포 관련 권한만 있고 Intune에서 모든 앱을 배포할 수 있도록 하는 완전한 앱 배포 권한은 없는 경우, 사용자는 Intune SDK 워크플로를 진행할 수 없지만 MAM 앱 보호 정책 만들기 워크플로를 통해 LOB 앱을 추가할 수는 있습니다.

### <a name="to-add-lob-apps-ios-and-android"></a>LOB 앱을 추가하려면(iOS 및 Android)

1.  [정책 추가] 블레이드에서 **앱**을 선택하여 [앱] 블레이드를 엽니다.

    ![MAM 정책 추가 블레이드](../media/AppManagement/mam-lob-apps-1.png)

2.  **앱 더 보기**를 클릭하고 **번들 ID**(iOS)나 **패키지 ID**(Android)를 입력한 다음 [선택]을 클릭하여 LOB 앱을 추가합니다.

    ![MAM 앱 더 보기 블레이드](../media/AppManagement/mam-lob-apps-2.png)

### <a name="to-add-lob-apps-windows"></a>LOB 앱을 추가하려면(Windows)

> [!IMPORTANT]
> 새 앱 보호 정책을 만들 때 플랫폼 드롭다운 목록에서 Windows 10을 선택해야 합니다.

1. [정책 추가] 블레이드에서 **허용되는 앱** 또는 **제외 앱**을 선택하여 [허용되는 앱] 또는 [제외 앱] 블레이드를 엽니다.

   > [!NOTE]
   > 
   > - **허용되는 앱**: 이 정책을 준수해야 하는 앱입니다.
   > - **제외 앱**: 이 정책에서 제외되며 회사 데이터에 제한 없이 액세스할 수 있습니다.
   > <br></br>
2. [허용되는 앱] 또는 [제외 앱] 블레이드에서 **앱 추가**를 클릭합니다. 권장 Microsoft 앱, 스토어 또는 데스크톱 앱을 추가할 수 있습니다.

    a.  **권장 앱:** 관리자가 정책으로 쉽게 가져올 수 있도록 미리 채워진 앱(대부분 Office 앱) 목록입니다.

    b.  **스토어 앱:** 관리자가 Windows 스토어의 모든 앱을 정책에 추가할 수 있습니다.

    c.  **Windows 데스크톱 앱:** 관리자가 기존 Windows 데스크톱 앱을 정책에 추가할 수 있습니다(예: exe, dll 등).

## <a name="deploy-a-policy-to-users"></a>사용자에게 정책 배포

1.  **정책** 블레이드에서  **사용자 그룹**을 선택하면 **사용자 그룹** 블레이드가 열립니다. **사용자 그룹** 블레이드에서 **사용자 그룹 추가**를 선택하여 **사용자 그룹 추가** 블레이드를 엽니다.

    ![사용자 그룹 추가 옵션을 강조 표시한 사용자 그룹 블레이드의 스크린 샷](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  사용자 그룹 목록이 **사용자 그룹 추가** 블레이드에 표시됩니다. 이는 **Azure Active Directory**에 있는 모든 보안 그룹의 목록입니다. 이 정책을 적용할 사용자 그룹을 선택하고 **선택**을 선택합니다. **선택**을 선택하면 정책이 사용자에게 배포됩니다.

    ![Azure Active Directory 사용자 목록을 보여 주는 사용자 그룹 추가 블레이드의 스크린 샷](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    이제 정책을 만들고 사용자에게 배포했습니다.

Intune 라이선스가 할당된 사용자만 정책에 의해 영향을 받습니다. 선택한 보안 그룹에서 Intune 라이선스가 할당되지 않은 사용자는 영향을 받지 않습니다.

>[!IMPORTANT]
> Configuration Manager와 함께 Intune을 사용하여 iOS 및 Android 장치를 관리하는 경우 선택한 그룹에 바로 포함된 사용자에만 정책이 적용됩니다. 선택한 그룹 내에 중첩된 자식 그룹의 멤버는 영향을 받지 않습니다.

최종 사용자는 앱 스토어 또는 Google Play에서 앱을 다운로드할 수 있습니다. 자세한 내용은 다음을 참조하십시오.
* [Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](/intune/end-user-mam-apps-android)
* [iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](/intune/end-user-mam-apps-ios)

##  <a name="change-existing-policies"></a>기존 정책 변경
기존 정책을 편집할 수 있으며 대상으로 지정된 사용자에게 적용할 수 있습니다. 그러나 기존 정책을 변경하는 경우 앱에 이미 로그인한 사용자에게는 8시간 동안 변경 내용이 표시되지 않습니다.

변경 사항의 결과를 즉시 확인하려면 최종 사용자가 앱에서 로그아웃하고 다시 로그인해야 합니다.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>정책과 연결된 앱 목록을 변경하려면

1.  **앱 정책** 블레이드에서 변경할 정책을 선택합니다. 방금 선택한 정책과 관련된 블레이드가 열립니다.

    ![별도 블레이드에서 열린 기존 정책의 스크린 샷](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  정책 블레이드에서 **대상 앱**을 선택하여 앱 목록을 엽니다.

3.  목록에서 앱을 제거하거나 추가하고 **저장** 아이콘을 선택하여 변경 내용을 저장합니다.

### <a name="to-change-the-list-of-user-groups"></a>사용자 그룹 목록을 변경하려면

1.  **앱 정책** 블레이드에서 변경할 정책을 선택합니다. 선택한 정책과 관련된 블레이드가 열립니다.

2.  정책 블레이드에서 **사용자 그룹**을 선택하여 이 정책이 있는 현재 사용자 그룹 목록을 보여 주는 **사용자 그룹** 블레이드를 엽니다.

3.  정책에 새 사용자 그룹을 추가하려면 **사용자 그룹 추가**를 선택하고 사용자 그룹을 선택합니다. **선택**을 선택하여 선택한 그룹에 정책을 배포합니다.

    ![두 명의 사용자를 선택한 사용자 그룹 추가 블레이드의 스크린샷](../media/AppManagement/AzurePortal_MAM_ChangePolicy_SelectUser.png)

4.  사용자 그룹을 삭제하려면 제거하려는 사용자 그룹을 강조 표시합니다. 그런 다음 줄임표(…)를 선택하고 **삭제**를 선택하여 사용자 그룹을 제거합니다.

    ![삭제 옵션을 보여 주는 스크린샷 ](../media/AppManagement/AzurePortal_MAM_ChangePolicy_DeleteUser.png)

### <a name="to-change-policy-settings"></a>정책 설정을 변경하려면

1.  **앱 정책** 블레이드에서 변경할 정책을 선택합니다. 방금 선택한 정책과 관련된 블레이드가 열립니다.

    ![별도 블레이드에서 열린 기존 정책의 스크린 샷 ](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  **정책 설정**을 선택하여 **정책 설정** 블레이드를 엽니다.

3.  설정을 변경하고 **저장** 아이콘을 선택하여 변경 내용을 저장합니다.

    ![맨 위에서 저장 메뉴 옵션을 보여 주는 정책 설정 블레이드의 스크린 샷](../media/AppManagement/AzurePortal_MAM_ChangePolicy_ChangeSettings.png)

## <a name="policy-settings"></a>정책 설정
iOS 및 Android에 대한 정책 설정의 전체 목록을 보려면 다음 중 하나를 선택합니다.

> [!div class="op_single_selector"]
> - [iOS 정책](ios-mam-policy-settings.md)
> - [Android 정책](android-mam-policy-settings.md)

## <a name="next-steps"></a>다음 단계
[규정 준수 및 사용자 상태 모니터링](monitor-mobile-app-management-policies-with-microsoft-intune.md)

### <a name="see-also"></a>참고 항목
* [Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](/intune/end-user-mam-apps-android)
* [iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](/intune/end-user-mam-apps-ios)
