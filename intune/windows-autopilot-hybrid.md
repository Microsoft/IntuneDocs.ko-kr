---
title: Windows Autopilot을 사용하여 하이브리드 Active Directory 조인 장치에 대한 Intune 등록 설정
titleSuffix: Microsoft Intune
description: Windows Autopilot를 사용하여 하이브리드 Active Directory 조인 장치를 Intune에 등록합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 77a0c3f3a2e1ed0ee2dbc652049bb7057c736010
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189965"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>Intune 및 Windows Autopilot을 사용하여 하이브리드 Azure AD 조인 장치 배포(미리 보기)
Intune 및 Windows Autopilot를 사용하여 하이브리드 Azure Active Directory 조인 장치를 설정할 수 있습니다. 이렇게 하려면 다음 단계를 수행합니다.

> [!NOTE]
> 이 기능은 앞으로 며칠 동안 사용자 기반 전체에 롤아웃됩니다. 따라서 계정에 롤아웃될 때까지 다음 단계를 수행하지 못할 수도 있습니다.

## <a name="prerequisites"></a>전제 조건

- [하이브리드 Azure Active Directory 조인 장치](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)를 성공적으로 구성합니다.
    - [Get-MsolDevice cmdlet을 사용하여 등록을 확인]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration)합니다.

등록할 장치도 다음과 같아야 합니다.
- [2018년 10월 업데이트](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/)가 있는 Windows 10을 실행합니다.
- 인터넷에 대한 액세스 권한이 있어야 합니다.
- Active Directory에 대한 액세스 권한이 있어야 합니다(VPN 연결은 지원되지 않음).
- OOBE(첫 실행 경험)를 통해 이동합니다.

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10 자동 등록 설정

1. [Azure Portal](https://portal.azure.com)에 로그인하고 **Azure Active Directory**를 선택합니다.

   ![Azure Portal의 스크린샷](./media/auto-enroll-azure-main.png)

2. **이동성(MDM 및 MAM)** 을 선택합니다.

   ![Azure Portal의 스크린샷](./media/auto-enroll-mdm.png)

3. **Microsoft Intune**을 선택합니다.

   ![Azure Portal의 스크린샷](./media/auto-enroll-intune.png)

4. Intune 및 Windows를 사용하여 Azure Active Directory에 조인된 장치를 배포하는 사용자가 **MDM 사용자 범위**에 속한 그룹의 멤버인지 확인합니다.

   ![Azure Portal의 스크린샷](./media/auto-enroll-scope.png)

5. 다음 URL의 기본값을 사용합니다.
    - **MDM 사용 약관 URL**
    - **MDM 검색 URL**
    - **MDM 규정 준수 URL**
6. **저장**을 선택합니다.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>조직 구성 단위에서 컴퓨터 계정 제한 증가

Active Directory용 Intune Connector는 온-프레미스 Active Directory 도메인에 Autopilot 등록 컴퓨터를 만듭니다. Intune Connector를 호스팅하는 컴퓨터에는 도메인 내에 컴퓨터 개체를 만들 수 있는 권한이 있어야 합니다. 

일부 도메인에서는 컴퓨터를 만들 수 있는 권한이 컴퓨터에 부여되지 않습니다. 또는 관리자가 도메인 전체의 컴퓨터 계정 제한을 늘리지 않으려고 할 수 있습니다. 이러한 상황에서는 하이브리드 Azure AD 조인 장치가 만들어지는 조직 구성 단위에 권한을 위임할 수 있습니다.

컴퓨터를 만들 수 있는 권한이 부여된 조직 구성 단위는 다음과 일치해야 합니다.
- 도메인 조인 프로필에 입력된 조직 구성 단위
- 또는 선택한 프로필이 없는 경우 도메인에 대한 컴퓨터의 도메인 이름

1. **Active Directory 사용자 및 컴퓨터**(DSA.msc)를 엽니다.

2. 하이브리드 Azure AD 조인 컴퓨터를 만드는 데 사용할 조직 구성 단위를 마우스 오른쪽 단추로 클릭한 다음, **제어 위임**은 선택합니다.

    ![제어 위임의 스크린샷](media/windows-autopilot-hybrid/delegate-control.png)

3. **제어 위임** 마법사에서 **다음** > **추가...** > **개체 형식**을 차례로 선택합니다.

4. **개체 형식** 대화 상자에서 **컴퓨터**, **확인**을 차례로 선택합니다.

    ![제어 위임의 스크린샷](media/windows-autopilot-hybrid/object-types-computers.png)

5. **사용자, 컴퓨터 또는 그룹 선택** 대화 상자의 **선택할 개체 이름 입력** 상자에서 Connector가 설치된 컴퓨터의 이름을 입력합니다.

    ![제어 위임의 스크린샷](media/windows-autopilot-hybrid/enter-object-names.png)

6. **이름 확인**을 선택하여 항목의 유효성을 검사한 다음, **확인** > **다음**을 차례로 선택합니다.

7. **위임할 사용자 지정 작업 만들기** > **다음**을 차례로 선택합니다.

8. **폴더에 있는 다음 개체만** 선택하고, 다음 옵션을 선택합니다.
    - **컴퓨터 개체**
    - **이 폴더에서 선택한 개체 만들기**
    - **이 폴더에서 선택한 개체 삭제**

    ![제어 위임의 스크린샷](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. **다음**을 선택합니다.

10. **권한** 아래에서 **모든 권한**(다른 모든 옵션이 선택됨) > **다음** > **마침**을 차례로 선택합니다.

    ![제어 위임의 스크린샷](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>Intune Connector 설치

Active Directory용 Intune Connector는 인터넷 및 Active Directory에 액세스할 수 있는 Windows Server 2016을 실행하는 컴퓨터에 설치해야 합니다. 규모와 및 가용성을 늘리거나 여러 Active Directory 도메인을 지원하기 위해 환경에 여러 개의 커넥터를 설치할 수 있습니다. 다른 Intune 커넥터를 실행하지 않는 서버에 커넥터를 설치하는 것이 좋습니다.

1. [Intune Connector(미리 보기) 언어 요구 사항](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector)에 설명된 대로 언어 팩을 설치 및 구성했는지 확인합니다.
2. [Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Windows 등록** > **Active Directory용 Intune Connector(미리 보기)** > **커넥터 추가**를 차례로 선택합니다. 
3. 지침에 따라 커넥터를 다운로드합니다.
4. 다운로드한 커넥터 설치 파일(ODJConnectorBootstrapper.exe)을 열어 커넥터를 설치합니다.
5. 설치가 완료되면 **구성**을 선택합니다.
6. **로그인**을 선택합니다.
7. 사용자 글로벌 관리자 또는 Intune 관리자 역할 자격 증명을 입력합니다.
8. **장치 등록** > **Windows 등록** > **Active Directory용 Intune Connector(미리 보기)** 로 차례로 이동하여 연결 상태가 **활성**인지 확인합니다.

### <a name="configure-web-proxy-settings"></a>웹 프록시 설정 구성

네트워킹 환경에 웹 프록시가 있는 경우 Active Directory용 Intune Connector가 제대로 작동할 수 있도록 [기존 온-프레미스 프록시 서버 작업](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)의 지침을 따릅니다.


## <a name="create-a-device-group"></a>장치 그룹 만들기
1. [Intune](https://aka.ms/intuneportal)에서 **그룹** > **새 그룹**을 선택합니다.
2. **그룹** 블레이드에서:
    1. **그룹 형식**에서 **보안**을 선택합니다.
    2. **그룹 이름** 및 **그룹 설명**을 입력합니다.
    3. **멤버 자격 유형**을 선택합니다.
3. 위의 **멤버 자격 형식**에 대해 **동적 장치**를 선택했다면 **그룹** 블레이드에서 **동적 장치 멤버**를 선택하고 **고급 규칙** 상자에서 다음 코드를 입력합니다.
    - Autopilot 장치를 모두 포함한 그룹을 만들려는 경우 `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`를 입력합니다.
    - 특별 주문 ID를 사용하여 Autopilot 장치를 모두 포함한 그룹을 만들려는 경우 `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `를 입력합니다.
    - 특별 구매 주문 ID를 사용하여 Autopilot 장치를 모두 포함한 그룹을 만들려는 경우 `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`를 입력합니다.
    
    **고급 규칙** 코드를 추가한 후에 **저장**을 선택합니다.
5. **만들기**를 선택합니다.  

## <a name="register-your-autopilot-devices"></a>Autopilot 등록

다음 방법 중 하나를 선택하여 Autopilot 장치를 등록합니다.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>이미 등록된 Autopilot 등록

1. **대상이 지정된 모든 장치를 Autopilot으로 변환**이 **예**로 설정된 Autopilot 배포 프로필을 만듭니다. 
2. Autopilot에 자동으로 등록하려는 멤버가 포함되는 그룹에 프로필을 할당합니다.

자세한 내용은 [Autopilot 배포 프로필 만들기](enrollment-autopilot.md#create-an-autopilot-deployment-profile)를 참조하세요.

### <a name="register-autopilot-devices-that-arent-enrolled"></a>등록되지 않은 Autopilot 등록

장치가 아직 등록되지 않은 경우 직접 등록할 수 있습니다. 자세한 내용은 [장치 추가](enrollment-autopilot.md#add-devices)를 참조하세요.

### <a name="register-devices-from-an-oem"></a>OEM에서 장치 등록

새 장치를 구입하는 경우 일부 OEM에서 장치를 등록할 수 있습니다. 자세한 내용은 [Windows Autopilot 페이지](http://aka.ms/WindowsAutopilot)를 참조하세요.

Autopilot 장치가 등록되면(그리고 Intune에 등록되기 전에) 이름이 해당 일련 번호로 설정된 장치가 다음 세 위치에 표시됩니다.
- Azure Portal의 Intune에 있는 Autopilot 장치 블레이드(**장치 등록** > **Windows 등록** > **장치**)
- Azure Portal의 Intune에 있는 Azure AD 장치 블레이드(**장치** > **Azure AD 장치**)
- Azure Portal의 Azure Active Directory에 있는 Azure Active Directory의 AAD 모든 장치 블레이드(**장치** > **모든 장치**)

Autopilot 장치가 등록되면 다음 네 위치에 표시됩니다.
- Azure Portal의 Intune에 있는 Autopilot 장치 블레이드(**장치 등록** > **Windows 등록** > **장치**)
- Azure Portal의 Intune에 있는 Azure AD 장치 블레이드(**장치** > **Azure AD 장치**)
- Azure Portal의 Azure Active Directory에 있는 Azure Active Directory의 AAD 모든 장치 블레이드(**장치** > **모든 장치**)
- Azure Portal의 Intune에 있는 모든 장치 블레이드(**장치** > **모든 장치**)

Autopilot 장치가 등록되면 장치 이름이 장치의 호스트 이름으로 변경됩니다. 기본적으로 "DESKTOP-"로 시작합니다.




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Autopilot 배포 프로필 만들기 및 할당
Autopilot 배포 프로필은 Autopilot 장치를 구성하는 데 사용됩니다.

1. [Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기**를 선택합니다.
2. **이름** 및 선택적 **설명**을 입력합니다.
3. **배포 모드**에서 **사용자 기반**을 선택합니다.
4. **Azure AD 조인 유형** 상자에서 **하이브리드 Azure AD 조인됨(미리 보기)** 을 선택합니다.
5. **OOBE(첫 실행 경험)** 를 선택하고, 필요에 따라 옵션을 구성한 다음, **저장**을 선택합니다.
6. **만들기**를 선택하여 프로필을 만듭니다. 
7. 프로필 블레이드에서 **할당**을 선택합니다.
8. **그룹 선택** 블레이드에서 **그룹 선택**을 선택하고, 장치 그룹 > **선택**을 차례로 선택합니다.

장치 프로필 상태가 **할당되지 않음**, **할당 중**, 마지막으로 **할당됨**으로 차례로 변경되는 데 약 15분이 걸립니다.

## <a name="turn-on-the-enrollment-status-page-optional"></a>등록 상태 페이지 설정(선택 사항)

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **등록 상태 페이지(미리 보기)** 를 선택합니다.
2. **등록 상태 페이지** 블레이드에서 **기본값** > **설정**을 선택합니다.
3. **프로필 및 앱 설치 진행률 표시**에서 **예**를 선택합니다.
4. 필요에 따라 다른 옵션을 구성합니다.
5. **저장**을 선택합니다.

## <a name="create-and-assign-a-domain-join-profile"></a>도메인 조인 프로필 만들기 및 할당

1. [Intune](https://aka.ms/intuneportal)에서 **디바이스 구성** > **프로필** > **프로필 만들기**를 차례로 선택합니다.
2. 다음 속성을 입력합니다.
   - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
   - **설명**: 설정에 대한 설명을 입력합니다.
   - **플랫폼**: **Windows 10 이상**을 선택합니다.
   - **프로필 유형**: **도메인 조인(미리 보기)** 을 선택합니다.
3. **설정**을 선택하고, **컴퓨터 이름 접두사**, **도메인 이름** 및 **조직 구성 단위**(선택 사항)를 제공합니다. 
4. **확인** > **만들기**를 선택합니다. 프로필이 만들어지고 목록에 표시됩니다.
5. 프로필을 할당하려면 [장치 프로필 할당](device-profile-assign.md#assign-a-device-profile) 아래의 단계를 수행합니다. 

## <a name="next-steps"></a>다음 단계

Windows Autopilot이 구성되었으면 이러한 장치를 관리하는 방법을 알아봅니다. 자세한 내용은 [Microsoft Intune 장치 관리란?](device-management.md)을 참조하세요.
