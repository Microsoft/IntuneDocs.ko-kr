---
title: 사용자 추가 및 권한 부여
titlesuffix: Microsoft Intune
description: Azure AD와 온-프레미스 사용자를 동기화하고 Intune 구독에 대한 관리자 권한을 부여합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.openlocfilehash: 76721710f266ff5f25dca763d7b6cca561050610
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184576"
---
# <a name="add-users-and-grant-administrative-permission-to-intune"></a>Intune에 사용자 추가 및 관리 권한 부여

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

관리자는 사용자를 직접 추가할 수도 있고 온-프레미스 Active Directory에서 사용자를 동기화할 수도 있습니다. 추가된 사용자는 장치를 등록하고 회사 리소스에 액세스할 수 있습니다. *전역 관리자*, *서비스 관리자* 등의 추가 권한을 사용자에게 제공할 수도 있습니다.

## <a name="add-users-to-intune"></a>Intune에 사용자 추가
[Office 365 포털](https://www.office.com/signin) 또는 [Azure Portal](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)을 통해 Intune 구독에 사용자를 수동으로 추가할 수 있습니다. 관리자는 사용자 계정을 편집하여 Intune 라이선스를 할당할 수 있습니다. Office 365 포털 또는 Intune Azure Portal에서 라이선스를 할당할 수 있습니다. Office 365 포털 사용에 대한 자세한 내용은 [Office 365 포털에 개별적으로 또는 대량으로 사용자 추가](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)를 참조하세요.

### <a name="add-intune-users-in-the-office-365-admin-center"></a>Office 365 관리 센터에서 Intune 사용자 추가
1. 전역 관리자 또는 사용자 관리 관리자 계정으로 [Office 365 포털](https://www.office.com/signin)에 로그인하세요.
2. Office 365 메뉴에서 **관리**를 선택합니다.
3. 관리 센터에서 **사용자 추가**를 선택합니다.

   ![사용자 추가 섹션의 스크린 샷](media/office-add-user.png)

4. 다음 사용자 정보를 지정합니다.
   - **이름**
   - **성**
   - **표시 이름**
   - **사용자 이름** - 서비스 액세스에 사용되는 Azure Active Directory에 저장된 유니버설 원칙 이름(UPN)입니다.
   - **위치**
   - **연락처 정보**(선택 사항)
   - **암호** - 자동으로 생성하거나 지정

     ![새 사용자 섹션의 스크린 샷](media/office-add-user-details.png)

5. Intune 라이선스를 할당합니다. **제품 라이선스**를 선택하고 제품 라이선스를 선택합니다. Intune을 비롯한 라이선스가 필요합니다.
6. **추가**를 선택하여 새 사용자를 만듭니다.

### <a name="add-intune-users-in-the-azure-portal"></a>Azure Portal에서 Intune 사용자 추가
1. [Azure Portal](https://portal.azure.com)에 로그인하고 **모든 서비스** > **모니터링 + 관리** > **Intune**으로 이동합니다. **Intune**에 대한 *리소스를 검색*할 수도 있습니다.
2. **사용자** > **모든 사용자**를 선택합니다.
3. 관리 센터에서 **새로운 사용자**를 선택합니다.
   ![새 사용자 스크린샷](media/intune-add-user.png)
4. 다음 사용자 정보를 지정합니다.
   - **이름**
   - **사용자 이름** - Azure Active Directory 포털의 새 이름 ![이름 및 사용자 이름 추가하는 스크린샷](media/intune-add-user-info.png) **확인**을 선택하여 계속합니다.
5. 필요에 따라 다음과 같은 사용자 속성을 지정할 수 있습니다.
   - **프로필** - **직위** 및 **부서**를 비롯한 작업 정보
   -  **그룹** - 사용자에 대해 추가할 그룹 선택
   - **디렉터리 역할** -사용자에게 Intune 서비스 관리자 역할을 포함한 관리 권한을 부여합니다.

   **만들기**를 선택하여 Intune에 새 사용자를 추가합니다.
6. **프로필**을 선택한 다음 새 사용자의 **사용 위치**를 선택합니다. 새 사용자에게 Intune 라이선스를 할당하려면 사용 위치가 필요합니다. **저장**을 선택하여 계속합니다.
    ![사용 위치의 스크린샷](media/intune-add-user-loc.png)
7. **라이선스**를 선택한 다음 **할당**을 선택하여 이 사용자에게 Intune 라이선스를 할당합니다. 장치를 등록하거나 회사 리소스에 액세스하려면 Intune 라이선스가 필요합니다. **제품**을 선택하고 라이선스 형식을 선택한 다음 **선택**, **할당**을 차례로 선택합니다.

## <a name="grant-admin-permissions"></a>관리자 권한 부여

Intune 구독에 사용자를 추가한 후에는 몇 가지 사용자 관리 권한을 부여하는 것이 좋습니다.  관리 권한을 부여하려면 다음 단계를 따르세요.

### <a name="give-admin-permissions-in-office-365"></a>Office 365에서 관리 권한 부여
1. [Office 365 포털](https://www.office.com/signin)에 전역 관리자 계정으로 로그인합니다.
2. Office 365 메뉴에서 **관리**를 선택합니다.
3. 관리 센터에서 **활성 사용자**를 선택하고 사용자를 선택하여 관리 권한을 부여합니다.

4. **역할** 열에서 **편집**을 선택합니다.

    ![관리 사용자의 스크린샷](./media/office-assign-roles-open.png)

5. 사용 가능한 역할 목록에서 부여할 관리 권한을 선택합니다.
![역할 할당의 스크린샷](./media/office-assign-roles.png)
6. **저장**을 선택합니다.

### <a name="give-admin-permissions-in-the-azure-portal"></a>Azure Portal에서 관리자 권한 부여
1. [Azure Portal](https://www.office.com/signin)에 전역 관리자 계정으로 로그인합니다.
2. Azure Portal에서 **사용자**를 선택한 후 관리 권한을 부여할 사용자를 선택합니다.
3. **디렉터리 역할**을 선택한 다음 권한을 선택합니다.
  ![디렉터리 역할의 스크린샷](./media/add-intune-directory-role.png)
4. **저장**을 선택합니다.

### <a name="types-of-administrators"></a>관리자 유형

사용자에게 하나 이상의 관리자 권한을 할당합니다. 이러한 권한은 사용자 및 사용자가 관리할 수 있는 작업에 대한 관리 범위를 정의합니다. 관리자 권한은 여러 Microsoft 클라우드 서비스 간에 공통적입니다. 일부 서비스에서 일부 사용 권한을 지원하지 않을 수 있습니다. Azure Portal 및 Office 365 포털 모두 Intune에서 사용하지 않는 제한된 관리자 역할을 나열합니다. Intune 관리자 권한은 다음 옵션을 포함합니다.

- **전역 관리자** - (Office 365 및 Intune) Intune의 모든 관리 기능에 액세스할 수 있습니다. 기본적으로는 Intune을 등록하는 사람이 전역 관리자가 됩니다. 다른 관리 역할을 할당할 수 있는 관리자는 전역 관리자뿐입니다. 조직에 전역 관리자가 여러 명 있을 수 있습니다. 하지만 업무상의 위험을 줄이려면 회사에서 이 역할을 소수의 인원에게만 제공하는 것이 좋습니다.
- **암호 관리자** - (Office 365 및 Intune) 암호를 재설정하고, 서비스 요청을 관리하고, 서비스 상태를 모니터링합니다. 암호 관리자는 사용자의 암호 재설정만 수행할 수 있습니다.
- **서비스 관리자** - (Office 365 및 Intune) Microsoft에 대한 지원 요청을 열고 서비스 대시보드와 메시지 센터를 확인합니다. 이 관리자는 지원 티켓을 열고 읽는 권한 외에는 "보기 전용" 권한을 소유합니다.
- **대금 청구 관리자** - (Office 365 및 Intune) 구매를 진행하고, 구독 및 지원 티켓을 관리하고, 서비스 상태를 모니터링합니다.
- **사용자 관리자** - (Office 365 및 Intune) 암호를 재설정하고, 서비스 상태를 모니터링하고, 사용자 계정을 추가/삭제하고, 서비스 요청을 관리합니다. 사용자 관리 관리자는 전역 관리자를 삭제하거나, 다른 관리 역할을 만들거나, 다른 관리자의 암호를 재설정할 수 없습니다.
- **Intune 서비스 관리자** -**디렉터리 역할** 옵션을 포함한 관리자를 만들 수 있는 권한을 제외한 모든 Intune 전역 관리자 권한입니다.

Microsoft Intune 구독을 만드는 데 사용하는 계정은 전역 관리자입니다. 일상적인 관리 작업에는 전역 관리자를 사용하지 않는 것이 가장 좋습니다. 관리자는 Intune 라이선스를 사용하여 Azure Portal에서 Intune에 액세스하지 않아도 되지만 Exchange 서비스 커넥터 설정과 같은 어떤 관리 작업을 수행하려면 Intune 라이선스가 필요합니다.

Office 365 포털에 액세스하려면 계정에 **로그인 허용**이 설정되어 있어야 합니다. Azure Portal의 **프로필**에서 **로그인 차단**을 **아니요**로 설정하여 액세스를 허용합니다. 이 상태는 구독에 대한 라이선스 보유와는 다른 문제입니다. 기본적으로 모든 사용자 계정은 **허용**됩니다. 관리자 권한이 없는 사용자는 Office 365 포털을 사용하여 Intune 암호를 재설정할 수 있습니다.

## <a name="sync-active-directory-and-add-users-to-intune"></a>Active Directory를 동기화하고 Intune에 사용자 추가
온-프레미스 Active Directory에서 Microsoft Azure AD(Azure Active Directory)로 Intune 사용자를 포함한 사용자 계정을 가져오도록 디렉터리 동기화를 구성할 수 있습니다. 온-프레미스 Active Directory 서비스를 모든 Azure Active Directory 기반 서비스와 연결하면 사용자 ID를 훨씬 간편하게 관리할 수 있습니다. 사용자에게 친숙하고 간편한 인증 환경을 제공하도록 Single Sign-On 기능을 구성할 수도 있습니다. 같은 [Azure AD 테넌트](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)를 여러 서비스와 연결하면 이전에 동기화했던 사용자 계정을 모든 클라우드 기반 서비스에 사용할 수 있습니다.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Azure AD와 온-프레미스 사용자를 동기화하는 방법
Azure AD와 사용자 계정을 동기화하기 위해 필요한 유일한 도구는 [Azure AD Connect 마법사](https://www.microsoft.com/download/details.aspx?id=47594)입니다. Azure AD Connect 마법사는 온-프레미스 ID 인프라를 클라우드에 연결하도록 안내하는 간단한 환경을 제공합니다. 토폴로지 및 요구 사항(단일 디렉터리 또는 여러 디렉터리, 암호 해시 동기화, 통과 인증 또는 페더레이션)을 선택합니다. 마법사는 연결이 작동되도록 하는 데 필요한 모든 구성 요소를 배포하고 구성합니다. 여기에는 동기화 서비스, AD FS(Active Directory Federation Services) 및 Azure AD PowerShell 모듈이 포함됩니다.

> [!TIP]
> Azure AD Connect에는 이전에 Dirsync 및 Azure AD Sync로 출시된 기능이 포함됩니다. [디렉터리 통합](http://technet.microsoft.com/library/jj573653.aspx)에 대해 자세히 알아봅니다. 로컬 디렉터리에서 Azure AD로 사용자 계정을 동기화하는 방법에 대해 자세히 알아보려면 [Active Directory와 Azure AD의 유사성](http://technet.microsoft.com/library/dn518177.aspx)을 참조하세요.
