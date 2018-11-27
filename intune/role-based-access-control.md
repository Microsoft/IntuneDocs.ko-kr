---
title: Microsoft Intune에서 RBAC
description: RBAC(역할 기반 액세스 제어)를 통해 Microsoft Intune에서 작업을 수행하고 변경할 수 있는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 07a1c0a0825faafa85b3fb2904dcb517268617bf
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180054"
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>Microsoft Intune에서 RBAC(역할 기반 관리 제어)

RBAC를 사용하면 조직 내에서 다양한 Intune 작업을 수행할 수 있는 사용자와 해당 작업이 적용되는 사용자를 제어할 수 있습니다. 몇 가지 일반적인 Intune 시나리오에 적용되는 기본 제공 역할을 사용하거나, 사용자 고유의 역할을 만들 수 있습니다. 역할은 다음으로 정의됩니다.

- **역할 정의**: 역할의 이름, 역할이 관리하는 리소스 및 각 리소스에 대해 부여되는 권한입니다.
- **구성원**: 권한을 부여받은 사용자 그룹입니다.
- **범위**: 구성원이 관리할 수 있는 사용자 또는 장치 그룹입니다.
- **할당** - 정의, 구성원 및 범위가 구성된 경우 역할이 할당됩니다.

![Intune RBAC 예제](./media/intune-rbac-1.PNG)

새로운 Azure Portal부터는 **Azure AD(Azure Active Directory)** 에서 Intune에 사용할 수 있는 두 가지 디렉터리 역할을 제공합니다. 이러한 역할에는 Intune에서 모든 활동을 수행할 수 있는 모든 권한이 부여됩니다.

- **전역 관리자:** 이 역할의 사용자는 Azure AD의 모든 관리 기능뿐 아니라 Exchange Online, SharePoint Online, 비즈니스용 Skype Online 등 Azure AD에 페더레이션되는 서비스에도 액세스할 수 있습니다. Azure AD 테넌트에 등록하는 사람이 전역 관리자가 됩니다. 전역 관리자만이 다른 Azure AD 관리자 역할을 할당할 수 있습니다. 조직에 전역 관리자가 두 명 이상 있을 수도 있습니다. 전역 관리자는 모든 사용자 및 다른 모든 관리자의 암호를 다시 설정할 수 있습니다.

- **Intune 서비스 관리자:** 이 역할의 사용자는 서비스 제공 시 Intune 내에서 전역 권한을 소유합니다. 또한 대체하는 Azure 제한 사항 외에도 이 역할은 사용자 및 장치를 관리하고 Intune 그룹을 만들고 관리하는 기능을 제공합니다.

- **조건부 액세스 관리자:** 이 역할의 사용자는 조건부 액세스 정책을 확인, 생성, 수정, 삭제할 수만 있습니다.

    > [!IMPORTANT]
    > Intune 서비스 관리자 역할은 Azure AD의 조건부 액세스 설정을 관리하는 기능은 제공하지 않습니다.
    > Intune 역할의 멤버에는 Intune 라이선스가 필요합니다.

    > [!TIP]
    > Intune에는 **사용자**, **그룹** 및 **조건부 액세스**의 3개 Azure AD 확장도 표시됩니다. Azure AD RBAC를 사용하여 이러한 확장을 제어합니다. 또한 **사용자 계정 관리자**는 AAD 사용자/그룹 활동만 수행하며, Intune에서 모든 활동을 수행하기 위한 모든 권한은 없습니다. 자세한 내용은 [Azure AD를 통한 RBAC](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles)를 참조하세요.

## <a name="roles-created-in-the-intune-classic-portal"></a>Intune 클래식 포털에서 만든 역할

“모든” 권한을 소유한 Intune **서비스 관리자** 사용자만이 Intune 클래식 포털에서 Azure Portal의 Intune으로 마이그레이션됩니다. 따라서 "읽기 전용" 또는 "기술 지원팀" 액세스 권한이 있는 Intune **서비스 관리자** 사용자는 Azure Portal의 Intune 역할로 다시 할당한 다음 클래식 포털에서 제거해야 합니다.

> [!IMPORTANT]
> 관리자가 Intune을 사용한 PC 관리 기능에 계속 액세스해야 하는 경우에는 클래식 포털에서 Intune 서비스 관리자 액세스 권한을 유지해야 할 수도 있습니다.

## <a name="built-in-roles"></a>기본 제공 역할

다음 역할은 Intune에서 기본 제공되며 추가 구성 없이 그룹에 할당할 수 있습니다.

- **기술 지원팀 운영자**: 사용자와 장치에 대해 원격 작업을 수행하며, 사용자 또는 장치에 응용 프로그램이나 정책을 할당할 수 있습니다.
- **정책 및 프로필 관리자**: 준수 정책, 구성 프로필, Apple 등록 및 회사 장치 식별자를 관리합니다.
- **읽기 전용 운영자**: 사용자, 장치, 등록, 구성 및 응용 프로그램 정보를 확인할 수 있습니다. Intune을 변경할 수 없습니다.
- **응용 프로그램 관리자**: 모바일 및 관리되는 응용 프로그램을 관리하며, 장치 정보를 읽고, 장치 구성 프로필을 볼 수 있습니다.
- **Intune 역할 관리자**: 사용자 지정 Intune 역할을 관리하고 기본 제공 Intune 역할에 대한 할당을 추가합니다. 관리자에게 사용 권한을 할당할 수 있는 유일한 Intune 역할입니다.
- **학교 관리자**: [Intune for Education](introduction-intune-education.md)에서 Window 10 장치를 관리하고 다음 작업을 수행할 수 있습니다: 

|권한|작업|
|---|---|
|감사 데이터|읽기|
|DeviceConfigurations|할당, 만들기, 삭제, 읽기, 업데이트|
|장치 등록 관리자|읽기, 업데이트|
|관리 장치|읽기, 업데이트<!--, Delete [To be added in 1803]-->|
|모바일 앱|할당, 만들기, 삭제, 읽기, 업데이트|
|보고서|읽기|
|원격 작업|PC 정리, 재부팅, 원격 잠금, 사용 중지, 장치 동기화, 초기화|
|조직|읽기|

### <a name="to-assign-a-built-in-role"></a>기본 제공 역할을 할당하려면

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **역할** > **모든 역할**을 선택합니다.
1. **Intune 역할 - 모든 역할** 창에서 할당할 기본 제공 역할을 선택합니다.

2. <*역할 이름*> - **개요** 창에서 **관리**, **할당**을 차례로 선택합니다.

    > [!NOTE]
    > 기본 제공 역할은 편집하거나 삭제할 수 없습니다.

3. 사용자 지정 역할 창에서 **할당**을 선택합니다.

4. **역할 할당** 창에서 할당에 대한 **이름** 및 선택적 **설명**을 입력하고 다음을 선택합니다.
    - **구성원** - 사용 권한을 부여하려면 사용자가 포함된 그룹을 선택합니다.
    - **범위** - 위 구성원이 관리하도록 허용할 사용자가 포함된 그룹을 선택합니다.
<br></br>
5. 작업이 끝나면 **확인**을 클릭합니다. 새 할당이 할당 목록에 표시됩니다.

### <a name="intune-rbac-table"></a>Intune RBAC 테이블

- 각 역할이 수행할 수 있는 작업을 자세히 확인하려면 [Intune RBAC 테이블](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)을 다운로드하세요.

## <a name="custom-roles"></a>사용자 지정 역할

특정 작업 기능에 필요한 모든 권한을 포함하는 사용자 지정 역할을 만들 수 있습니다. 예를 들어 IT 부서 그룹에서 응용 프로그램, 정책 및 구성 프로필을 관리하는 경우 이러한 모든 권한을 사용자 지정 역할 하나에 추가할 수 있습니다.

> [!IMPORTANT]
> 역할을 만들거나 편집하거나 할당하려면 계정에 Azure AD의 다음 사용 권한 중 하나가 있어야 합니다.
> - **전역 관리자**
> - **Intune 서비스 관리자**

### <a name="to-create-a-custom-role"></a>사용자 지정 역할을 만들려면

1. Intune 자격 증명을 사용하여 [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. 왼쪽 메뉴에서 **모든 서비스**를 선택한 다음, 텍스트 상자 필터에 **Intune**을 입력합니다.

3. **Intune** > **역할** > **모든 역할** > **사용자 지정 추가**를 선택합니다.

4. **사용자 지정 역할 추가** 창에서 새 역할의 이름 및 설명을 입력하고 **권한**을 클릭합니다.

5. **사용 권한** 창에서 이 역할에 사용할 사용 권한을 선택합니다. [Intune RBAC 테이블](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)을 활용하여 적용할 권한을 결정할 수 있습니다.

6. 작업이 끝나면 **확인**을 선택합니다.

7. **사용자 지정 역할 추가** 창에서 **만들기**를 클릭합니다. **Intune 역할 - 모든 역할** 창의 목록에 새 역할이 표시됩니다.

### <a name="to-assign-a-custom-role"></a>사용자 지정 역할을 할당하려면

1. **Intune 역할 - 모든 역할** 창에서 할당할 사용자 지정 역할을 선택합니다.

2. <*역할 이름*> - **개요** 창에서 **관리**, **할당**을 차례로 선택합니다. 이 창에서 기존 역할을 편집하거나 삭제할 수도 있습니다.

3. 사용자 지정 역할 창에서 **할당**을 선택합니다.

4. **역할 할당** 창에서 할당에 대한 **이름** 및 선택적 **설명**을 입력하고 다음을 선택합니다.
    - **구성원** - 사용 권한을 부여하려면 사용자가 포함된 그룹을 선택합니다.
    - **범위** - 위 구성원이 관리하도록 허용할 사용자가 포함된 그룹을 선택합니다.
<br></br>
5. 작업이 끝나면 **확인**을 클릭합니다. 새 할당이 할당 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

[문제 해결 포털에서 Intune 기술 지원팀 운영자 역할 사용](help-desk-operators.md)

## <a name="see-also"></a>참고 항목

[Azure AD를 사용하여 역할 할당](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
