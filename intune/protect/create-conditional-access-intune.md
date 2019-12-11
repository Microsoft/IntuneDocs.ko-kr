---
title: Intune을 사용하여 디바이스 기반 조건부 액세스 설정
titleSuffix: Microsoft Intune
description: Microsoft Intune 디바이스 준수 및 모바일 앱 관리를 기준으로 디바이스 기반 조건부 액세스 정책을 만드는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fde15da898a70e9557aabb9ed7a7ae8324cfb304
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188337"
---
# <a name="create-a-device-based-conditional-access-policy"></a>디바이스 기반 조건부 액세스 정책 만들기

Intune을 통해 액세스 제어에 모바일 디바이스 규정 준수를 추가하여 Azure Active Directory의 조건부 액세스를 강화합니다. 디바이스 준수에 대한 요구 사항을 정의하는 Intune 규정 준수 정책을 통해 디바이스의 규정 준수 상태를 사용하여 앱 및 서비스에 대한 액세스를 허용하거나 차단할 수 있습니다. **디바이스가 규격으로 표시되어야 함** 설정을 사용하는 조건부 액세스 정책을 만들어 이 작업을 수행할 수 있습니다.

조건부 액세스 정책은 보호하려는 앱 또는 서비스, 앱 또는 서비스에 액세스할 수 있는 조건 및 정책이 적용되는 사용자를 지정합니다. 조건부 액세스는 Azure AD premium 기능이지만 *Intune*에서 액세스하는 조건부 액세스 노드는 *Azure AD*에서 액세스하는 것과 동일한 노드입니다.

> [!IMPORTANT]
> 조건부 액세스를 설정하기 전에 특정 요구 사항에 맞는지 여부에 따라 디바이스를 평가하도록 Intune 디바이스 준수 정책을 설정해야 합니다. [Intune에서 디바이스 준수 정책 시작](device-compliance-get-started.md)을 참조하세요.

## <a name="create-conditional-access-policy"></a>조건부 액세스 정책 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스** > **조건부 액세스** > **정책** > **새 정책**을 선택합니다.
  ![새 조건부 액세스 정책 만들기](./media/create-conditional-access-intune/create-ca.png)

3. **할당**에서 **사용자 및 그룹**을 선택합니다.

4. **포함** 탭에서 이 조건부 액세스 정책이 적용되는 사용자 또는 그룹을 식별합니다. 포함할 그룹 또는 사용자를 선택한 후에 이 정책에서 제외할 사용자, 역할 또는 그룹이 있으면 **제외** 탭을 사용합니다.

   - **모든 사용자**: 내부 및 게스트 사용자를 포함하여 모든 사용자 및 그룹에 정책을 적용하려면 이 옵션을 선택합니다.

   - **사용자 및 그룹 선택**: 이 옵션을 선택하고 다음 옵션 중 하나 이상을 지정합니다.
  
     1. **모든 게스트 사용자**: 외부 게스트 사용자(예: 파트너, 외부 협력자)를 포함하거나 제외하려면 이 옵션을 선택합니다.

     2. **디렉터리 역할**: 이러한 역할이 할당된 사용자를 포함하거나 제외할 하나 이상의 Azure AD 역할을 선택합니다.

     3. **사용자 및 그룹**: 포함하거나 제외할 개별 사용자 또는 그룹을 검색하고 선택하려면 이 옵션을 선택합니다.

        > [!TIP]
        > 소규모 사용자를 대상으로 정책을 테스트하여 예상대로 작동하는지 확인합니다.

5. **완료**를 선택합니다.

6. **할당**에서 **클라우드 앱 및 작업**을 선택합니다.

7. **포함 탭**에서 사용 가능한 옵션을 사용하여 이 조건부 액세스 정책을 사용하여 보호하려는 앱 및 서비스를 식별합니다. 그런 후 이 정책에서 제외하려는 앱 또는 서비스가 있는 경우 **제외** 탭을 사용할 수 있습니다.

   - **모든 클라우드 앱**: 모든 앱에 정책을 적용하려면 이 옵션을 선택합니다.
     > [!IMPORTANT]
     > Azure Portal 액세스를 위한 Microsoft Azure 관리 앱은 이 목록에 포함됩니다. 여기 또는 **사용자 및 그룹** 옵션에서 **제외** 탭을 사용하여 사용자 자신(또는 지정한 사용자나 그룹)가 Azure Portal에 로그인할 수 있는지 확인해야 합니다. 

   - **앱 선택**: 이 옵션을 선택하고 **선택**을 선택한 후 애플리케이션 목록을 사용하여 보호하려는 앱 또는 서비스를 검색하고 선택합니다.

   준비가 되면 **완료**를 선택합니다.

8. **할당** 섹션에서 **조건**을 선택합니다.

   - **로그인 위험**: 이 정책에서 Azure AD ID 보호 로그인 위험 탐지를 사용하려면 *예*를 선택한 후에 정책을 적용할 로그인 위험 수준을 선택합니다.

   - **디바이스 플랫폼**: **포함** 탭에서 이 조건부 액세스 정책을 적용할 디바이스 플랫폼을 식별합니다. **제외** 탭을 사용하여 이 정책에서 플랫폼을 제외합니다.

   - **위치**: **포함** 탭에서 정책이 적용되는지 여부를 지정합니다.
     - 모든 위치
     - IT 부서에서 제어하는 신뢰할 수 있는 네트워크 위치
     - 특정 네트워크 위치.

     이 정책에서 네트워크 위치를 제외하려면 **제외** 탭을 사용합니다.

   - **클라이언트 앱**: 정책을 브라우저 앱, 모바일 앱 및 데스크톱 클라이언트에 적용해야 하는 경우 *예*를 선택합니다.

   - **디바이스 상태**: 예를 선택하고 디바이스가 하이브리드 Azure AD에 조인된 상태 또는 디바이스가 규격으로 표시된 상태(또는 두 상태를 모두 갖는 경우)를 특별히 제외하도록 선택하지 않으면 조건부 액세스 정책이 모든 디바이스 상태에 적용됩니다.

     > [!TIP]
     > **최신 인증** 클라이언트와 **Exchange ActiveSync 클라이언트**를 둘 다 보호하려는 경우 각 클라이언트 유형에 대해 하나씩 두 개의 조건부 액세스 정책을 따로 만듭니다. Exchange ActiveSync가 최신 인증을 지원하지만 Exchange ActiveSync에서 지원하는 유일한 조건은 플랫폼입니다. 다단계 인증을 포함하는 기타 조건은 지원되지 않습니다. Exchange ActiveSync에서 Exchange Online에 대한 액세스를 효과적으로 보호하려면 지원되는 플랫폼에만 적용 정책을 선택하고 클라우드 앱 Office 365 Exchange Online 및 클라이언트 앱 Exchange ActiveSync를 지정하는 조건부 액세스 정책을 만듭니다.

9. **완료**를 선택합니다.

10. **액세스 제어**에서 **권한 부여**를 선택합니다. 설정한 조건에 따라 진행되는 작업을 구성합니다.  다음 옵션에서 선택할 수 있습니다.

    - **액세스 차단**: 이 정책에 지정된 사용자는 지정한 조건에 따라 앱 액세스가 거부됩니다.
    - **액세스 허용**: 이 정책에 지정된 사용자에게 액세스 권한이 부여되지만 다음 추가 작업을 요구할 수 있습니다.
      - **다단계 인증 필요**: 사용자는 전화 통화 또는 문자 등의 추가 보안 요구 사항을 완료해야 합니다.
      - **디바이스가 규격으로 표시되어야 함**: 디바이스가 Intune 규격이어야 합니다. 디바이스가 비규격이면 Intune에서 디바이스를 등록하는 옵션이 제공됩니다.
      - **하이브리드 Azure AD 조인된 디바이스 필요**: 디바이스는 하이브리드 Azure AD와 조인되어야 합니다.
      - **승인된 클라이언트 앱 필요**: 디바이스는 승인된 클라이언트 앱을 사용해야 합니다. 
      - **여러 컨트롤의 경우**: 디바이스가 앱에 액세스하려고 할 때 모든 요구 사항이 적용되도록 **선택된 컨트롤이 모두 필요함**을 선택합니다.

      ![액세스 제어 권한 부여 설정](./media/create-conditional-access-intune/create-ca-grant-access-settings.png)

11. **정책 사용**에서 **켜기**를 선택합니다.

12. **만들기**를 선택합니다.

## <a name="next-steps"></a>다음 단계

[Intune을 사용하는 앱 기반 조건부 액세스](app-based-conditional-access-intune.md)

[Troubleshooting Intune conditional access](https://support.microsoft.com/help/4456106)(Intune 조건부 액세스 문제 해결)
