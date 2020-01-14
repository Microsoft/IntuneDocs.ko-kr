---
title: Intune과 Wandera Mobile Threat Protection 통합 설정
titleSuffix: Intune on Azure
description: 회사 리소스의 모바일 디바이스 액세스를 제어하기 위해 Microsoft Intune을 사용하여 Wandera Mobile Threat Protection 솔루션을 설정하는 방법입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e565f40aac2a2b97f547a5b68a70a887d9e820ae
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207471"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Intune과 Wandera Mobile Threat Protection 통합  

Intune과 Wandera Mobile Threat Defense 솔루션을 통합하려면 다음 단계를 완료하세요.  

> [!NOTE]
> 이 Mobile Threat Defense 공급업체는 등록되지 않은 디바이스에서 지원되지 않습니다.

## <a name="before-you-begin"></a>시작하기 전에  

Wandera를 Intune과 통합하는 프로세스를 시작하기 전에 다음 필수 조건이 충족되는지 확인하세요.
- Microsoft Intune 구독  
- 다음 권한을 부여할 Azure Active Directory 관리자 자격 증명  
  - 로그인 및 사용자 프로필 읽기  
  - 로그인한 사용자로 디렉터리에 액세스  
  - 디렉터리 데이터 읽기  
  - Intune에 디바이스 정보 보내기  

- Wandera 구독:
  - EMM Connect에 대한 사용권이 있는 Wandera 계정 하나 이상  
  - Wandera에서 슈퍼 관리자 권한이 있는 계정  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Wandera Mobile Threat Defense 앱 권한 부여  

Wandera Mobile Threat Defense 앱 권한 부여 프로세스:  
- Wandera Mobile Threat Defense 서비스에서 디바이스 상태와 관련된 정보를 Intune으로 다시 전달하도록 허용합니다.  
- Wandera는 Azure AD 등록 그룹 멤버 자격과 동기화하여 해당 디바이스의 데이터베이스를 채웁니다.  
- Wandera RADAR 관리 포털에서 Azure AD SSO(Single Sign ON)를 사용하도록 허용합니다.  
- Wandera Mobile Threat Defense 앱에서 Azure AD SSO를 사용하여 로그인하도록 허용합니다.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Wandera Mobile Threat Defense 통합 설정  
Wandera용 ‘EMM Connect’를 설정하려면 1회성 구성 프로세스를 Intune 및 Wandera 콘솔 모두에서 완료해야 합니다.  이 구성 프로세스는 15분 정도 걸립니다. Wandera 기술 계정 또는 지원 담당자와 협력하지 않고 구성을 완료할 수 있습니다.  

### <a name="enable-support-for-wandera-in-intune"></a>Intune에서 Wandera를 지원하도록 설정

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **테넌트 관리** > **커넥터 및 토큰** > **Mobile Threat Defense** > **추가**를 선택합니다.
3. **커넥터 추가** 페이지에서 드롭다운을 사용하여 **Wandera**를 선택합니다. 그런 다음, **만들기**를 선택합니다.  
4. Mobile Threat Defense 창의 커넥터 목록에서 **Wandera** MTD 커넥터를 선택하여 *커넥터 편집* 창을 엽니다. **Wandera 관리 콘솔 열기**를 선택하여 Wandera 관리 콘솔인 [RADAR](https://radar.wandera.com/login)을 열고 로그인합니다. 
5. Wandera 콘솔에서 **설정** > **EMM 통합**으로 이동하고 **EMM Connect** 탭을 선택합니다. ‘EMM Vendor’(EMM 공급업체) 드롭다운을 사용하여 ‘Microsoft Intune’을 선택합니다.  

   ![Intune 선택](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

6. **권한 부여**를 선택하여 Intune 포털과 연결합니다. Intune 관리자 자격 증명을 사용하여 로그인하고 확인란을 선택한 다음 권한 요청을 **수락**합니다.  

   ![권한 허용](./media/wandera-mtd-connector-integration/permissions.png) 

7. Wandera에서 연결을 완료하고 RADAR 관리 콘솔로 돌아옵니다. 필요한 경우 추가 구성에 대한 액세스 권한을 **부여**하는 프로세스를 반복합니다.  

   ![통합 및 사용 권한](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

8. RADAR 콘솔을 사용할 때 **EMM Label**(EMM 레이블) 아래에 표시되는 **SyncOnly** 그룹의 이름을 복사합니다. 이 이름은 Intune에서 Wandera와의 동기화를 위해 그룹을 구성할 때 사용합니다.

   ![동기화 그룹](./media/wandera-mtd-connector-integration/sync-group-name.png) 

9. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 콘솔로 돌아가 Wandera MTD 커넥터를 편집합니다. 사용 가능한 토글을 **켜기**로 설정하고 구성을 **저장**합니다.  

   ![Wandera 사용](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Intune과 Wandera가 이제 연결되었습니다.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Wandera 애플리케이션 및 동기화 그룹 구성  
Wandera를 배포하려면 사용하는 플랫폼(iOS 및 Android)용 Wandera 모바일 앱을 Intune에 추가하고 동기화를 위한 특정 그룹인 ‘SyncOnly’ 그룹에 할당합니다.  

다음 섹션과 절차에서는 이 프로세스를 안내합니다.

Wandera의 이 프로세스에 관해 자세히 알아보려면 Wandera [RADAR](https://radar.wandera.com/login)에 로그인하세요. **설정** > **EMM Integration**(EMM 통합)으로 이동하고 **앱 푸시** 탭을 선택한 다음 **Microsoft Intune**을 선택합니다. 앱 푸시 탭이 Intune 관련 지침으로 업데이트됩니다.  

### <a name="add-the-wandera-apps"></a>Wandera 앱 추가  
Android 및 iOS 디바이스에 Wandera 앱을 배포하기 위한 클라이언트 앱을 Intune에서 만듭니다. Wandera 앱과 관련된 절차와 맞춤형 세부 정보는 [Add MTD apps](mtd-apps-ios-app-configuration-policy-add-assign.md)(MTD 앱 추가)를 참조하세요.  

앱을 만든 후 여기로 돌아와 동기화 그룹을 만들어 앱을 할당합니다.

### <a name="create-the-synchronization-group-and-assign-the-apps"></a>동기화 그룹 만들기 및 앱 할당

1. Wandera RADAR 콘솔 내의 **EMM Label** 아래에 표시되는 **SyncOnly** 그룹의 이름을 확인합니다. 이 이름은 7단계에 [Intune에서 Wandera 지원을 설정](#enable-support-for-wandera-in-intune)할 때 저장했을 수 있습니다. 이 이름은 Intune에서 Wandera 동기화를 위한 그룹 이름으로 사용합니다.  

2. Endpoint Manager 관리 센터에서 **그룹**으로 이동하고 **새 그룹**을 선택합니다. 다음을 지정하여 Wandera에서 사용할 동기화 그룹을 구성합니다.
   - **그룹 유형**: **Security**
   - **그룹 이름**: Wandera RADAR 관리 콘솔에서 받은 **SyncOnly** 이름을 지정합니다.

   ![동기화 그룹 구성](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. **구성원**을 선택하고 Wandera에서 사용할 Android 및 iOS 디바이스를 포함하는 그룹을 할당합니다.

4. **만들기**를 선택하여 그룹을 저장합니다.

자세한 내용은 [앱 배포](../apps/apps-deploy.md)를 참조하세요.

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>동기화 그룹에 Wandera 앱 할당  
iOS 및 Android용으로 만든 Wandera 앱에 대해 다음 절차를 반복합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱**을 선택하고 Wandera 앱을 선택합니다.
3. **할당** 및 **그룹 추가**를 차례로 선택합니다.  
4. ‘그룹 추가’ 창에서 ‘할당 유형’으로 **필수**를 선택합니다.  
5. **포함된 그룹**을 선택한 다음 **포함할 그룹 선택**을 선택합니다. Wandera 동기화를 위해 만든 그룹을 지정한 다음 **선택** > **확인** > **확인**을 클릭합니다. **저장**을 선택하여 그룹 할당을 완료합니다. 

## <a name="next-steps"></a>다음 단계  
통합을 구성했으므로 Wandera 관리 콘솔에서 정책 구성을 시작하고, 고급 조건부 액세스를 설정하고, 보고서를 볼 수 있습니다. Wandera 관리 및 구성에 대해 자세히 알아보려면 Wandera 설명서에서 [Support Center Getting Started Guide](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started)(지원 센터 시작 가이드)를 참조하세요. 
