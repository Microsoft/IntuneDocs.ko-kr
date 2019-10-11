---
ms.openlocfilehash: 3aadafbcf9c9208e7c87504c5459731de1e402b5
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2019
ms.locfileid: "71302620"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Windows 10 자동 등록 사용

자동 등록을 통해 사용자가 Intune에 Windows 10 디바이스를 등록할 수 있습니다. 등록하려면 사용자가 회사 계정을 개인적으로 소유한 디바이스에 추가하거나 회사 소유 디바이스를 Azure Active Directory에 연결합니다. 디바이스는 백그라운드에서 등록되어 Azure Active Directory에 연결됩니다. 등록된 디바이스는 Intune을 통해 관리됩니다.

**필수 구성 요소**
- Azure Active Directory Premium 구독([평가판 구독](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune 구독


### <a name="configure-automatic-mdm-enrollment"></a>자동 MDM 등록 구성

1. [Azure Portal](https://portal.azure.com)에 로그인하고 **Azure Active Directory**를 선택합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-azure-main.png)

2. **이동성(MDM 및 MAM)** 을 선택합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-mdm.png)

3. **Microsoft Intune**을 선택합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-intune.png)

4. **MDM 사용자 범위**를 구성합니다. Microsoft Intune에서 관리해야 하는 사용자의 디바이스를 지정합니다. 이러한 Windows 10 디바이스는 Microsoft Intune을 사용한 관리에 자동으로 등록됩니다.

   - **없음** - MDM 자동 등록 사용 안 함
   - **일부** - Windows 10 디바이스를 자동으로 등록할 수 있는 **그룹** 선택
   - **모두** -모든 사용자가 Windows 10 디바이스를 자동으로 등록할 수 있음

      > [!IMPORTANT]
      > BYOD 디바이스의 경우, 모든 사용자(또는 동일한 사용자 그룹)에 대해 MAM 사용자 범위와 MDM 사용자 범위(자동 MDM 등록)가 모두 사용되는 경우 MAM 사용자 범위가 우선 적용됩니다. 디바이스는 MDM에 등록되기 보다는 WIP(Windows Information Protection) 정책(구성한 경우)을 사용합니다.
      >
      > 회사 디바이스의 경우 두 가지 범위가 모두 사용되면, MDM 사용자 범위가 우선 적용됩니다. 디바이스가 MDM에 등록됩니다.

   > [!NOTE]
   > MDM 사용자 범위는 사용자 개체를 포함하는 Azure AD 그룹으로 설정해야 합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-scope.png)

5. 다음 URL의 기본값을 사용합니다.
    - **MDM 사용 약관 URL**
    - **MDM 검색 URL**
    - **MDM 규정 준수 URL**

6. **저장**을 선택합니다.

기본적으로 2단계 인증이 서비스에 대해 활성화되어 있지 않습니다. 그러나 디바이스를 등록할 때 2단계 인증이 권장됩니다. 2단계 인증을 요구하려면 Azure AD에서 2단계 인증 공급자를 구성하고 다단계 인증에 대한 사용자 계정을 구성합니다. [Azure Multi-Factor Authentication Server 시작](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)을 참조하세요.
