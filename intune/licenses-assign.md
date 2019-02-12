---
title: Microsoft Intune 라이선스 할당
description: Intune에 등록할 수 있도록 사용자에게 라이선스 할당
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 797ea27103144423d1b43434612999631a4a243d
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834495"
---
# <a name="assign-licenses-to-users-so-they-can-enroll-devices-in-intune"></a>Intune에 디바이스를 등록할 수 있도록 사용자에게 라이선스 할당

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

수동으로 사용자를 추가하든 아니면 온-프레미스 Active Directory에서 동기화하든 상관없이 먼저 각 사용자에게 Intune 라이선스를 할당해야 사용자가 Intune에 디바이스를 등록할 수 있습니다. 라이선스 목록은 [Intune을 포함하는 라이선스](licenses.md)를 참조하세요.

## <a name="assign-an-intune-license-in-the-office-365-admin-center"></a>Office 365 관리 센터에서 Intune 라이선스 할당

[Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)을 사용하여 클라우드 기반 사용자를 수동으로 추가하고, 클라우드 기반 사용자 계정 및 온-프레미스 Active Directory에서 Azure AD로 동기화한 계정에 라이선스를 할당할 수 있습니다.

1. 테넌트 관리자 자격 증명을 사용하여 [Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)에 로그인한 후 **사용자** > **활성 사용자**를 선택합니다.

2. Intune 사용자 라이선스를 할당할 사용자 계정을 선택한 후 **제품 라이선스** > **편집**을 선택합니다.

3. **Intune** 또는 **Enterprise Mobility + Security**를 **켬**으로 전환하고 **저장**을 선택합니다.

   ![Office 365 포털 제품 라이선스 섹션의 스크린 샷입니다.](./media/office-assign-license.png)

4. 이제 사용자 계정은 서비스를 사용하고 장치를 관리하고 등록하는 데 필요한 권한이 생겼습니다.

> [!NOTE]
> 사용자는 디바이스를 등록한 후에만 관리 콘솔에 표시됩니다. 또한 사용자 그룹을 선택하여 동시에 편집할 수 있습니다. 즉, 선택한 모든 사용자에 대한 라이선스를 추가하거나 바꾸도록 선택할 수 있습니다.

## <a name="assign-an-intune-license-by-using-azure-active-directory"></a>Azure Active Directory를 사용하여 Intune 라이선스 할당

Azure Active Directory를 사용하여 Intune 라이선스를 사용자에게 할당할 수도 있습니다. 자세한 내용은 [Azure Active Directory 문서에서 사용자에게 라이선스 할당](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal)을 참조하세요. 

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>학교 데이터 동기화를 사용하여 Intune for Education에서 사용자에게 라이선스 할당
교육 기관일 경우 SDS(학교 데이터 동기화)를 사용하여 Intune for Education 라이선스를 동기화된 사용자에게 할당할 수 있습니다. SDS 프로필을 설정할 때 [Intune for Education] 확인란을 선택하면 됩니다.  

![SDS 프로필 설정 스크린샷](./media/i4e-sds-profile-setup-setting.png)

Intune for Education 라이선스를 할당할 경우 Intune A Direct 라이선스도 할당되는지 확인합니다.

![제품 라이선스 설정 스크린샷](./media/i4e-set-licenses.png)

SDS에 대한 자세한 내용은 이 [학교 데이터 동기화 및 강의실 개요](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91)를 참조하세요.

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>사용자 및 디바이스 라이선스가 서비스 액세스에 영향을 주는 방식
* 사용자 소프트웨어 라이선스를 할당하는 각 **사용자**는 온라인 서비스 및 관련 소프트웨어(System Center 소프트웨어 포함)에 액세스하여 최대 15대의 장치와 애플리케이션을 관리하는 데 해당 서비스와 소프트웨어를 사용할 수 있습니다.
* 사용자 라이선스와 별도로 모든 디바이스에 대해 라이선스를 구입할 수 있습니다. 디바이스에는 디바이스 라이선스를 할당할 필요가 없습니다. 온라인 서비스 및 관련 소프트웨어(System Center 소프트웨어 포함)를 액세스하고 사용하는 각 디바이스에는 디바이스 라이선스가 할당되어야 합니다.
* 여러 사용자가 디바이스를 사용하는 경우 각 사용자에게 디바이스 소프트웨어 라이선스가 있어야 하거나, 모든 사용자에게 사용자 소프트웨어 라이선스가 있어야 합니다.

## <a name="understanding-the-type-of-licenses-you-have-purchased"></a>구입한 라이선스 형식 이해

Intune을 구입한 방법에 따라 구독 정보를 확인하는 방법은 다음과 같습니다.

- 기업계약을 통해 Intune을 구입한 경우 **구독**의 볼륨 라이선스 포털에서 구독 정보를 찾을 수 있습니다.
- 클라우드 솔루션 공급자를 통해 Intune을 구입한 경우 재판매인으로부터 확인합니다.
- CC# 또는 송장을 포함한 Intune을 구입한 경우 라이선스는 사용자 기반입니다.




## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>PowerShell을 사용하여 EMS 사용자 라이선스를 선택적으로 관리
Microsoft Enterprise Mobility + Security(이전 명칭 Enterprise Mobility Suite)를 사용하는 조직에는 EMS 패키지의 Intune 서비스 또는 Azure Active Directory Premium만 필요한 사용자가 있을 수 있습니다. [Azure Active Directory PowerShell cmdlet](https://msdn.microsoft.com/library/jj151815.aspx)을 사용하여 한 가지 서비스 또는 서비스 하위 집합을 할당할 수 있습니다.

EMS 서비스에 대해 사용자 라이선스를 선택적으로 할당하려면, [Windows PowerShell용 Azure Active Directory 모듈](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule)이 설치된 컴퓨터에서 관리자로 PowerShell을 엽니다. PowerShell은 로컬 컴퓨터 또는 ADFS 서버에 설치할 수 있습니다.

원하는 서비스 계획에만 적용되는 새로운 라이선스 SKU 정의를 만들어야 합니다. 이렇게 하려면, 적용하지 않을 계획은 비활성화합니다. 예를 들면, Intune 라이선스를 할당하지 않는 라이선스 SKU 정의를 만들 수 있습니다. 사용 가능한 서비스 목록을 보려면 다음을 입력합니다.

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

다음 명령을 실행하여 Intune 서비스 계획을 제외할 수 있습니다. 같은 방법을 사용하여 전체 보안 그룹으로 확장하거나 보다 세분화된 필터를 사용할 수 있습니다.

**예제 1**<br>
명령줄에서 새로운 사용자를 만들고 라이선스의 Intune 부분을 비활성화한 상태로 EMS 라이선스를 할당합니다.

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


다음을 통해 검증합니다.

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**예제 2:**<br>
이미 라이선스가 할당된 사용자에 대해 EMS 라이선스의 Intune 부분을 비활성화합니다.

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

다음을 통해 검증합니다.

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)
