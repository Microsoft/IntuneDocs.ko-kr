---
title: 하이브리드 Azure AD 조인 디바이스 등록 - Windows Autopilot
titleSuffix: ''
description: Windows Autopilot을 사용하여 하이브리드 Azure AD 조인 디바이스를 Microsoft Intune에 등록합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ac370ffe297cb62af6ed55cfd5c4c41cf8452d3
ms.sourcegitcommit: dfcf80a91792715404dc021c8684866c8b0a27e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65816299"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Intune 및 Windows Autopilot을 사용하여 하이브리드 Azure AD 조인 디바이스 배포
Intune 및 Windows Autopilot을 사용하여 하이브리드 Azure AD(Azure Active Directory) 조인 디바이스를 설정할 수 있습니다. 이렇게 하려면 이 문서의 단계를 수행합니다.

## <a name="prerequisites"></a>전제 조건

[하이브리드 Azure AD 조인 디바이스](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)를 성공적으로 구성합니다. Get-MsolDevice cmdlet을 사용하여 [등록을 확인]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration)해야 합니다.

등록할 디바이스도 다음과 같아야 합니다.
- [2018년 10월 업데이트](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/)가 있는 Windows 10을 실행합니다.
- 인터넷에 대한 액세스 권한이 있어야 합니다.
- Active Directory에 대한 액세스 권한이 있어야 합니다(현재 VPN 연결은 지원되지 않음).
- OOBE(첫 실행 경험)를 거칩니다.
- 조인하려는 도메인의 도메인 컨트롤러를 ping할 수 있습니다.

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10 자동 등록 설정

1. [Azure Portal](https://portal.azure.com)에 로그인하고 왼쪽 창에서 **Azure Active Directory**를 선택합니다.

   ![Azure Portal](./media/auto-enroll-azure-main.png)

1. **이동성(MDM 및 MAM)** 을 선택합니다.

   ![Azure Active Directory 창](./media/auto-enroll-mdm.png)

1. **Microsoft Intune**을 선택합니다.

   ![이동성(MDM 및 MAM) 창](./media/auto-enroll-intune.png)

1. Intune 및 Windows를 사용하여 Azure AD 조인 디바이스를 배포하는 사용자가 **MDM 사용자 범위**에 포함된 그룹의 멤버인지 확인합니다.

   ![이동성(MDM 및 MAM) 구성 창](./media/auto-enroll-scope.png)

1. **MDM 사용 약관 URL**, **MDM 검색 URL** 및 **MDM 규정 준수 URL** 상자에 기본값을 사용한 다음, **저장**을 선택합니다.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>조직 구성 단위에서 컴퓨터 계정 제한 증가

Active Directory용 Intune Connector는 온-프레미스 Active Directory 도메인에 Autopilot에 등록된 컴퓨터를 만듭니다. Intune Connector를 호스팅하는 컴퓨터에는 도메인 내에 컴퓨터 개체를 만들 수 있는 권한이 있어야 합니다. 

일부 도메인에서는 컴퓨터를 만들 수 있는 권한이 컴퓨터에 부여되지 않습니다. 또한 도메인에서는 컴퓨터 개체를 만들 수 있는 권한이 위임되지 않은 모든 사용자 및 컴퓨터에 기본 제공 제한(기본값 10)이 적용됩니다. 따라서 하이브리드 Azure AD 조인 디바이스가 만들어진 조직 단위의 Intune Connector를 호스트하는 컴퓨터에 권한이 위임되어야 합니다.

컴퓨터를 만들 수 있는 권한이 부여된 조직 구성 단위는 다음과 일치해야 합니다.
- 도메인 조인 프로필에 입력된 조직 구성 단위
- 선택한 프로필이 없는 경우 도메인에 대한 컴퓨터의 도메인 이름

1. **Active Directory 사용자 및 컴퓨터(DSA.msc)** 를 엽니다.

1. 하이브리드 Azure AD 조인 컴퓨터를 만드는 데 사용할 조직 구성 단위를 마우스 오른쪽 단추로 클릭한 다음, **제어 위임**을 선택합니다.

    ![제어 위임 명령](media/windows-autopilot-hybrid/delegate-control.png)

1. **제어 위임** 마법사에서 **다음** > **추가** > **개체 형식**을 선택합니다.

1. **개체 형식** 창에서 **컴퓨터** 확인란을 선택한 다음, **확인**을 클릭합니다.

    ![개체 형식 창](media/windows-autopilot-hybrid/object-types-computers.png)

1. **사용자, 컴퓨터 또는 그룹 선택** 창의 **선택할 개체 이름 입력** 상자에 Connector가 설치된 컴퓨터의 이름을 입력합니다.

    ![사용자, 컴퓨터 또는 그룹 선택 창](media/windows-autopilot-hybrid/enter-object-names.png)

1. **이름 확인**을 선택하여 항목의 유효성을 검사하고, **확인**과 **다음**을 차례로 선택합니다.

1. **위임할 사용자 지정 작업 만들기** > **다음**을 차례로 선택합니다.

1. **폴더에 있는 다음 개체만** 확인란을 선택한 다음, **컴퓨터 개체**, **이 폴더에서 선택한 개체 만들기** 및 **이 폴더에서 선택한 개체 삭제** 확인란을 선택합니다.

    ![Active Directory 개체 형식 창](media/windows-autopilot-hybrid/only-following-objects.png)
    
1. **다음**을 선택합니다.

1. **사용 권한**에서 **모든 권한** 확인란을 선택합니다.  
    다른 모든 옵션이 선택됩니다.

    ![사용 권한 창](media/windows-autopilot-hybrid/full-control.png)

1. **다음**과 **마침**을 차례로 선택합니다.

## <a name="install-the-intune-connector"></a>Intune Connector 설치

Active Directory용 Intune Connector는 Windows Server 2016 이상을 실행하는 컴퓨터에 설치해야 합니다. 컴퓨터가 인터넷과 Active Directory에 액세스할 수 있어야 합니다. 규모와 및 가용성을 늘리거나 여러 Active Directory 도메인을 지원하기 위해 환경에 여러 개의 커넥터를 설치할 수 있습니다. 다른 Intune 커넥터를 실행하지 않는 서버에 커넥터를 설치하는 것이 좋습니다.

1. [Intune Connector(미리 보기) 언어 요구 사항](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector)에 설명된 대로 언어 팩을 설치 및 구성했는지 확인합니다.
2. [Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Windows 등록** > **Active Directory용 Intune Connector(미리 보기)** > **커넥터 추가**를 차례로 선택합니다. 
3. 지침에 따라 커넥터를 다운로드합니다.
4. 다운로드한 커넥터 설치 파일, *ODJConnectorBootstrapper.exe*를 열어서 커넥터를 설치합니다.
5. 설치가 끝나면 **구성**을 선택합니다.
6. **로그인**을 선택합니다.
7. 사용자 글로벌 관리자 또는 Intune 관리자 역할 자격 증명을 입력합니다.  
   사용자 계정에는 할당된 Intune 라이선스가 있어야 합니다.
8. **디바이스 등록** > **Windows 등록** > **Active Directory용 Intune Connector(미리 보기)** 로 차례로 이동한 다음, 연결 상태가 **활성**인지 확인합니다.

> [!NOTE]
> 커넥터에서 로그인한 후 [Intune](https://aka.ms/intuneportal)에 표시되는 데 몇 분 정도 걸릴 수 있습니다. Intune 서비스와 통신할 수 있는 경우에만 표시됩니다.

### <a name="turn-off-ie-enhanced-security-configuration"></a>IE 보안 강화 구성 끄기
기본적으로 Windows Server에는 Internet Explorer 보안 강화 구성이 켜져 있습니다. Active Directory용 Intune Connector에 로그인할 수 없는 경우 관리자용 IE 보안 강화 구성을 끕니다. [Internet Explorer 보안 강화 구성을 끄는 방법](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration)

### <a name="configure-web-proxy-settings"></a>웹 프록시 설정 구성

네트워킹 환경에 웹 프록시가 있는 경우 [기존 온-프레미스 프록시 서버 작업](autopilot-hybrid-connector-proxy.md)을 참조하여 Active Directory용 Intune Connector가 제대로 작동하는지 확인합니다.


## <a name="create-a-device-group"></a>디바이스 그룹 만들기
1. [Intune](https://aka.ms/intuneportal)에서 **그룹** > **새 그룹**을 선택합니다.

1. **그룹** 창에서 다음을 수행합니다.

    a. **그룹 유형**에서 **보안**을 선택합니다.

    b. **그룹 이름** 및 **그룹 설명**을 입력합니다.

    c. **멤버 자격 유형**을 선택합니다.

1. 멤버 자격 유형에 **동적 디바이스**를 선택한 경우 **그룹** 창에서 **동적 디바이스 멤버**를 선택한 다음, **고급 규칙** 상자에서 다음 중 하나를 수행합니다.
    - Autopilot 디바이스를 모두 포함하는 그룹을 만들려면 `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`를 입력합니다.
    - 특정 주문 ID로 Autopilot 디바이스가 모두 포함된 그룹을 만들려면 `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`을 입력합니다.
    - 특정 구매 주문 ID로 Autopilot 디바이스가 모두 포함된 그룹을 만들려면 `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`를 입력합니다.
    
1. **저장**을 선택합니다.

1. **만들기**를 선택합니다.  

## <a name="register-your-autopilot-devices"></a>Autopilot 등록

다음 방법 중 하나를 선택하여 Autopilot 디바이스를 등록합니다.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>이미 등록된 Autopilot 등록

1. **대상이 지정된 모든 디바이스를 Autopilot으로 변환**이 **예**로 설정된 Autopilot 배포 프로필을 만듭니다. 
2. Autopilot에 자동으로 등록하려는 멤버가 포함되는 그룹에 프로필을 할당합니다.

자세한 내용은 [Autopilot 배포 프로필 만들기](enrollment-autopilot.md#create-an-autopilot-deployment-profile)를 참조하세요.

### <a name="register-autopilot-devices-that-arent-enrolled"></a>등록되지 않은 Autopilot 등록

디바이스가 아직 등록되지 않은 경우 직접 등록할 수 있습니다. 자세한 내용은 [디바이스 추가](enrollment-autopilot.md#add-devices)를 참조하세요.

### <a name="register-devices-from-an-oem"></a>OEM에서 디바이스 등록

새 디바이스를 구입하는 경우 일부 OEM에서 디바이스를 등록할 수 있습니다. 자세한 내용은 [Windows Autopilot 페이지](http://aka.ms/WindowsAutopilot)를 참조하세요.

Autopilot 디바이스가 *등록되면* Intune에 등록되기 전에, 다음 세 곳에 표시됩니다(일련 번호로 이름이 설정됨).
- Azure Portal의 Intune에 있는 **Autopilot 디바이스** 창. **디바이스 등록** > **Windows 등록** > **디바이스**를 선택합니다.
- Azure Portal의 Intune에 있는 **Azure AD 디바이스** 창. **디바이스** > **Azure AD 디바이스**를 선택합니다.
- Azure Portal의 Azure Active Directory에 있는 **Azure AD 모든 디바이스** 창. **디바이스** > **모든 디바이스**를 선택합니다.

Autopilot 디바이스가 *등록되면*, 네 곳에 표시됩니다.
- Azure Portal의 Intune에 있는 **Autopilot 디바이스** 창. **디바이스 등록** > **Windows 등록** > **디바이스**를 선택합니다.
- Azure Portal의 Intune에 있는 **Azure AD 디바이스** 창. **디바이스** > **Azure AD 디바이스**를 선택합니다.
- Azure Portal의 Azure Active Directory에 있는 **Azure AD 모든 디바이스** 창. **디바이스** > **모든 디바이스**를 선택합니다.
- Azure Portal의 Intune에 있는 **모든 디바이스** 창. **디바이스** > **모든 디바이스**를 선택합니다.

Autopilot 디바이스가 등록되면, 해당 이름이 디바이스의 호스트 이름이 됩니다. 기본적으로 호스트 이름은 *DESKTOP-* 으로 시작됩니다.


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Autopilot 배포 프로필 만들기 및 할당
Autopilot 배포 프로필은 Autopilot 디바이스를 구성하는 데 사용됩니다.

1. [Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기**를 선택합니다.
1. **이름**을 입력하고 **설명**(선택 사항)을 입력합니다.
1. **배포 모드**에서 **사용자 기반**을 선택합니다.
1. **Azure AD 조인 유형** 상자에서 **하이브리드 Azure AD 조인됨(미리 보기)** 을 선택합니다.
1. **OOBE(첫 실행 경험)** 를 선택하고, 필요에 따라 옵션을 구성한 다음, **저장**을 선택합니다.
1. **만들기**를 선택하여 프로필을 만듭니다. 
1. 프로필 창에서 **할당**을 선택합니다.
1. **그룹 선택**을 선택합니다.
1. **그룹 선택** 창에서 디바이스 그룹을 선택한 다음, **선택**을 클릭합니다.

디바이스 프로필 상태가 *할당되지 않음*에서 *할당 중*으로 그리고, 마지막으로 *할당됨*으로 변경되는 데 약 15분이 걸립니다.

## <a name="optional-turn-on-the-enrollment-status-page"></a>(선택 사항) 등록 상태 페이지 설정

1. [Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Windows 등록** > **등록 상태 페이지**를 선택합니다.
1. **등록 상태 페이지** 창에서 **기본값** > **설정**을 선택합니다.
1. **프로필 및 앱 설치 진행률 표시** 상장에서 **예**를 선택합니다.
1. 필요에 따라 다른 옵션을 구성합니다.
1. **저장**을 선택합니다.

## <a name="create-and-assign-a-domain-join-profile"></a>도메인 조인 프로필 만들기 및 할당

1. [Intune](https://aka.ms/intuneportal)에서 **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
1. 다음 속성을 입력합니다.
   - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
   - **설명**: 프로필에 대한 설명을 입력합니다.
   - **플랫폼**: **Windows 10 이상**을 선택합니다.
   - **프로필 유형**: **도메인 가입(미리 보기)** 을 선택합니다.
1. **설정**을 선택하고 **컴퓨터 이름 접두사**, **도메인 이름** 및 [DN 형식](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name)의 **조직 구성 단위**(선택 사항)를 제공합니다. 
1. **확인** > **만들기**를 선택합니다.  
    프로필이 만들어지고 목록에 표시됩니다.
1. 프로필을 할당하려면 [디바이스 프로필 할당](device-profile-assign.md#assign-a-device-profile)의 단계에 따라 프로필을 [디바이스 그룹](windows-autopilot-hybrid.md#create-a-device-group) 단계에서 사용한 것과 같은 그룹에 할당합니다.
   - 여러 도메인 가입 프로필 배포
   
     a. 특정 Autopilot 배포 프로필을 통해 모든 Autopilot 디바이스를 포함하는 동적 그룹을 만들고 (device.enrollmentProfileName -eq "Autopilot 프로필 이름")을 입력합니다. 
     
     b. 'Autopilot 프로필 이름'은 [Autopilot 배포 프로필 만들기 및 할당](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile)에서 만든 프로필의 표시 이름으로 바꿉니다. 
     
     c. 여러 Autopilot 배포 프로필을 만들고 해당 디바이스를 동적 그룹에서 지정한 프로필에 할당합니다.

> [!NOTE]
> 하이브리드 Azure AD 조인을 위한 Windows Autopilot의 명명 기능은 %SERIAL%과 같은 변수를 지원하지 않으며 컴퓨터 이름에 대한 접두사만 지원합니다.

## <a name="next-steps"></a>다음 단계

Windows Autopilot이 구성되었으면 이러한 디바이스를 관리하는 방법을 알아봅니다. 자세한 내용은 [Microsoft Intune 디바이스 관리란?](device-management.md)을 참조하세요.
