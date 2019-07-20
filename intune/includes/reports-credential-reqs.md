---
ms.openlocfilehash: 6ec8f8a613d3b0a0b17f2615de634e70fa282fd7
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68229285"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Azure AD 및 Intune 자격 증명 요구 사항

인증 및 권한 부여는 Azure AD 자격 증명 및 Intune 역할 기반 액세스 제어(RBAC) 기반입니다. 테넌트에 대한 모든 전역 관리자와 Intune 서비스 관리자는 기본적으로 데이터 웨어하우스에 액세스할 수 있습니다. **Intune 데이터 웨어하우스** 리소스에 대한 액세스 권한을 부여하여 더 많은 사용자에게 액세스를 제공하기 위해 Intune 역할을 사용합니다.

Intune 데이터 웨어하우스(API 포함)에 액세스하기 위한 요구 사항은 다음과 같습니다.

- 사용자가 다음 중 하나여야 합니다.
  - Azure AD 전역 관리자
  - Intune 서비스 관리자
  - **Intune 데이터 웨어하우스** 리소스에 역할 기반 액세스 권한이 있는 사용자
  - [애플리케이션 전용 인증](../data-warehouse-app-only-auth.md)을 사용한 사용자 없는 인증 
