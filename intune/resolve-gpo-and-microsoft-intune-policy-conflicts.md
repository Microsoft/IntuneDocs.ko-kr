---
title: GPO 및 Intune 정책 충돌 해결
titlesuffix: Microsoft Intune
description: 그룹 정책 및 Intune 구성 정책 간의 충돌을 해결하는 방법을 알아봅니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: c36585b8482cc679de6b86f933abed4411c2dc4a
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837359"
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>GPO(그룹 정책 개체) 및 Microsoft Intune 정책 충돌 해결

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Intune은 Windows PC에서 설정 관리를 도와주는 정책을 사용합니다. 예를 들어 정책을 사용하여 PC의 Windows 방화벽에 대한 설정을 제어할 수 있습니다. 많은 Intune 설정이 Windows 그룹 정책으로 구성할 수 있는 설정과 비슷합니다. 그러나 경우에 따라 두 가지 방법이 서로 충돌할 수 있습니다.

충돌이 발생하는 경우 PC에서 도메인에 로그인할 수 있는 한 도메인 수준 그룹 정책이 Intune 정책보다 우선합니다. 이런 경우 Intune 정책이 클라이언트 PC에 적용됩니다.

## <a name="what-to-do-if-you-are-using-group-policy"></a>그룹 정책을 사용하는 경우 수행해야 하는 작업
적용하는 정책이 그룹 정책으로 관리되고 있지 않은지 확인합니다. 충돌을 방지하기 위해 다음 방법 중 하나 이상을 사용할 수 있습니다.

-   Intune 클라이언트를 설치하기 전에 그룹 정책 설정이 적용되지 않은 Active Directory OU(조직 구성 단위)로 PC를 이동합니다. 또한 Intune에 등록되어 있으며 그룹 정책 설정을 적용하지 않을 PC가 포함된 OU에서 그룹 정책 상속을 차단할 수 있습니다.

-   보안 그룹 필터를 사용하여 Intune을 통해 관리되지 않는 PC에만 GPO를 적용하도록 제한할 수 있습니다.

-   Intune 정책과 충돌하는 그룹 정책 개체를 사용하지 않거나 제거합니다.

Active Directory 및 Windows 그룹 정책에 대해서는 Windows Server 문서를 참조하십시오.

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>Intune 정책과 충돌을 피하기 위해 기존 GPO를 필터링하는 방법
설정이 Intune 정책과 충돌하는 GPO를 식별한 경우, 보안 그룹 필터를 사용하여 Intune을 통해 관리되지 않는 PC에만 해당 GPO가 적용되도록 제한할 수 있습니다.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


선택한 GPO에 대한 그룹 정책 관리 콘솔의 **보안 필터링** 영역에 지정된 보안 그룹에만 GPO를 적용할 수 있습니다. 기본적으로 GPO는 *인증된 사용자*에 적용됩니다.

-   **Active Directory 사용자 및 컴퓨터** 스냅인에서 Intune으로 관리하지 않으려는 컴퓨터 및 사용자 계정을 포함하는 새 보안 그룹을 만듭니다. 예를 들어 이 그룹의 이름을 *Microsoft Intune에 포함되지 않음*으로 지정할 수 있습니다.

-   그룹 정책 관리 콘솔에서 선택한 GPO에 해당하는 **위임** 탭에서 새 보안 그룹을 마우스 오른쪽 단추로 클릭하여 보안 그룹의 사용자 및 컴퓨터 모두에 적절한 **읽기** 및 **그룹 정책 적용** 권한을 위임합니다. **그룹 정책 적용** 권한은 **고급** 대화 상자에서 지정할 수 있습니다.

-   그런 다음 새 보안 그룹 필터를 선택한 GPO에 적용하고 **인증된 사용자** 기본 필터를 제거합니다.

새 보안 그룹은 Intune 서비스 변경 내용에서 등록 항목으로 유지되어야 합니다.

### <a name="see-also"></a>참고 항목
[Microsoft Intune을 사용하여 Windows PC 관리](manage-windows-pcs-with-microsoft-intune.md)
