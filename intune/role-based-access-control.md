---
title: Microsoft Intune을 사용하는 RBAC(역할 기반 액세스 제어)
description: Microsoft Intune에서 RBAC를 사용하여 작업을 수행하고 변경할 수 있는 사용자를 제어하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 895b358760775b1021e545b271acb7ced7fa7b1d
ms.sourcegitcommit: ac3fe7504e58c74495a560a68eae2b784a4f7d46
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942078"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>Microsoft Intune을 사용하는 RBAC(역할 기반 액세스 제어)

RBAC(역할 기반 액세스 제어)를 사용하여 조직의 리소스에 액세스할 수 있는 사람과 그 사람이 해당 리소스로 할 수 있는 일을 관리할 수 있습니다.  Intune 사용자에게 [역할을 할당](assign-role.md)하여 해당 사용자가 보고 변경할 수 있는 범위를 제한할 수 있습니다. 각 역할에는 해당 역할이 할당된 사용자가 조직 내에서 액세스하여 변경할 수 있는 항목을 결정하는 권한 세트가 있습니다.

역할을 만들거나 편집하거나 할당하려면 계정에 Azure AD의 다음 사용 권한 중 하나가 있어야 합니다.
- **전역 관리자**
- **Intune 서비스 관리자**(**Intune 관리자**라고도 함)

## <a name="roles"></a>역할
역할은 해당 역할이 할당된 사용자에게 부여되는 권한 세트를 정의합니다.
기본 제공 역할과 사용자 지정 역할을 모두 사용할 수 있습니다. 기본 제공 역할은 몇 가지 일반적인 Intune 시나리오를 다룹니다. 꼭 필요한 권한 세트만 있는 [사용자 고유의 사용자 지정 역할 만들기](create-custom-role.md)가 가능합니다. Intune에 대한 권한을 갖고 있는 여러 Azure Active Directory 역할이 있습니다.
역할을 보려면 **Intune** > **역할** > **모든 역할**을 선택한 다음, 역할을 선택합니다. 다음과 같은 페이지가 표시됩니다.

-   **속성**: 역할의 이름, 설명, 형식, 할당 및 범위 태그입니다. 
-   **사용 권한**: 역할이 갖는 권한을 정의하는 긴 토글 세트를 나열합니다.
-   **할당**: 어떤 사용자가 어떤 사용자/디바이스에 액세스할 수 있는지 정의하는 [역할 할당]( assign-role.md) 목록입니다. 한 역할에 여러 권한을 할당할 수 있으며, 한 사용자를 여러 할당에 포함할 수 있습니다.

### <a name="built-in-roles"></a>기본 제공 역할
추가 구성 없이 그룹에 기본 제공 역할을 할당할 수 있습니다. 기본 제공 역할의 이름, 설명, 형식 또는 권한을 삭제하거나 편집할 수 없습니다. 각 기본 제공 역할에 대한 사용 권한의 전체 목록은 [Intune RBAC 테이블](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)을 참조하세요.

- **기술 지원팀 운영자**: 사용자와 디바이스에 대해 원격 작업을 수행하며, 사용자 또는 디바이스에 애플리케이션이나 정책을 할당할 수 있습니다.
- **정책 및 프로필 관리자**: 규정 준수 정책, 구성 프로필, Apple 등록, 회사 디바이스 식별자 및 보안 기준을 관리합니다.
- **읽기 전용 운영자**: 사용자, 디바이스, 등록, 구성 및 애플리케이션 정보를 확인할 수 있습니다. Intune을 변경할 수 없습니다.
- **애플리케이션 관리자**: 모바일 및 관리되는 애플리케이션을 관리하며, 디바이스 정보를 읽고, 디바이스 구성 프로필을 볼 수 있습니다.
- **Intune 역할 관리자**: 사용자 지정 Intune 역할을 관리하고 기본 제공 Intune 역할에 대한 할당을 추가합니다. 관리자에게 사용 권한을 할당할 수 있는 유일한 Intune 역할입니다.
- **학교 관리자**: [Intune for Education](introduction-intune-education.md)으로 Windows 10 디바이스를 관리합니다.

### <a name="custom-roles"></a>사용자 지정 역할
사용자 지정 권한을 사용하여 사용자 고유의 역할을 만들 수 있습니다. 사용자 지정 역할에 대한 자세한 내용은 [사용자 지정 역할 만들기](create-custom-role.md)를 참조하세요.

### <a name="azure-active-directory-roles-with-intune-access"></a>Intune 액세스 권한이 있는 Azure Active Directory 역할
| Azure Active Directory 역할 | 모든 Intune 데이터 | Intune 감사 데이터 |
| --- | :---: | :---: |
| 전역 관리자 | 읽기/쓰기 | 읽기/쓰기 |
| Intune 서비스 관리자 | 읽기/쓰기 | 읽기/쓰기 |
| 조건부 액세스 관리자 | 없음 | 없음 |
| 보안 관리자 | 읽기 전용 | 읽기 전용 |
| 보안 운영자 | 읽기 전용 | 읽기 전용 |
| 보안 Reader | 읽기 전용 | 읽기 전용 |
| 규정 준수 관리자 | 없음 | 읽기 전용 |
| 규정 준수 데이터 관리자 | 없음 | 읽기 전용 |

> [!TIP]
> Intune에는 세 개의 Azure AD 확장도 표시됩니다. Azure AD RBAC를 사용하여 제어되는 **사용자**, **그룹** 및 **조건부 액세스**. 또한 **사용자 계정 관리자**는 AAD 사용자/그룹 활동만 수행하며, Intune에서 모든 활동을 수행하기 위한 모든 권한은 없습니다. 자세한 내용은 [Azure AD가 포함된 RBAC](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles)를 참조하세요.
### <a name="roles-created-in-the-intune-classic-portal"></a>Intune 클래식 포털에서 만든 역할
“모든” 권한을 소유한 Intune **서비스 관리자** 사용자만이 Intune 클래식 포털에서 Azure Portal의 Intune으로 마이그레이션됩니다. 따라서 "읽기 전용" 또는 "기술 지원팀" 액세스 권한이 있는 Intune **서비스 관리자** 사용자는 Azure Portal의 Intune 역할로 다시 할당한 다음, 클래식 포털에서 제거해야 합니다.
> [!IMPORTANT]
> 관리자가 Intune을 사용하여 PC 관리 기능에 계속 액세스해야 하는 경우에는 클래식 포털에서 Intune 서비스 관리자 액세스 권한을 유지해야 할 수도 있습니다.

## <a name="role-assignments"></a>역할 할당
역할 할당은 다음을 정의합니다.

- 역할에 할당되는 사용자
- 역할에 할당되는 사용자가 볼 수 있는 리소스
- 역할에 할당되는 사용자가 변경할 수 있는 리소스

사용자에게 사용자 지정 역할과 기본 제공 역할을 모두 할당할 수 있습니다. Intune 역할을 할당받으려면 사용자에게 Intune 라이선스가 있어야 합니다.
역할을 보려면 **Intune** > **역할** > **모든 역할**을 선택한 다음, 역할을 선택하고 할당을 선택합니다. 다음과 같은 페이지가 표시됩니다.

-   **속성**: 할당의 이름, 설명, 역할, 멤버, 범위 및 태그입니다.
-   **멤버**: 나열된 그룹의 모든 사용자는 범위(그룹)에 나와 있는 사용자/디바이스를 관리할 수 있는 권한이 있습니다.
-   **범위(그룹)**: 이 그룹에 속한 모든 사용자/디바이스는 멤버의 사용자가 관리할 수 있습니다.
-   **[범위(태그)](scope-tags.md)**: 멤버의 사용자는 범위 태그가 동일한 리소스를 볼 수 있습니다.

### <a name="multiple-role-assignments"></a>여러 역할 할당
사용자에게 여러 역할을 할당하면 다음과 같이 해당 역할 할당의 권한이 다른 개체로 확장됩니다.

- 권한 할당은 해당 역할의 할당 범위(그룹) 내에 있는 개체(예: 정책 또는 앱)에만 적용됩니다. 다른 할당에서 권한을 특별히 부여하지 않는 한 권한 할당은 다른 역할 할당의 개체에 적용되지 않습니다.
- 다른 권한(예: 만들기 및 읽기)은 사용자 할당에서 유형이 같은 모든 개체(예: 모든 정책 또는 모든 앱)에 적용됩니다.
- 유형이 다른 개체(예: 정책 또는 앱)의 권한은 서로에게 적용되지 않습니다. 예를 들어 정책 읽기 권한은 사용자 할당의 앱을 읽을 수 있는 권한을 제공하지 않습니다.

## <a name="next-steps"></a>다음 단계
- [사용자에게 역할 할당](assign-role.md)
- [사용자 지정 역할 만들기](create-custom-role.md)
