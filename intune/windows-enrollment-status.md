---
title: 등록 상태 페이지 설정
titleSuffix: Microsoft Intune
description: Windows 10 장치를 등록하는 사용자에게 인사하세요.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 08d76d6b76ee7838633435ae095c171e0a3cdf8e
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236495"
---
# <a name="set-up-an-enrollment-status-page"></a>등록 상태 페이지 설정
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
장치 설정 중에는 등록 상태 페이지에 장치에 관한 설치 정보가 표시됩니다. 사용자가 기본 등록을 완료하고 장치에 로그인할 때 일부 응용 프로그램, 프로필 및 인증서가 설치되지 않을 수 있습니다. 등록 상태 페이지는 사용자가 장치 설정 중에 장치 상태를 이해하는 데 도움이 됩니다. 여러 등록 상태 페이지 프로필을 만들고 여러 그룹에 적용할 수 있습니다. 프로필은 다음과 같이 설정할 수 있습니다.
- 설치 진행률 표시.
- 설치가 완료될 때까지 사용 차단.
- 장치 설정에 실패한 경우 사용자가 수행할 수 있는 작업 지정.

또한 동일한 사용자나 장치의 충돌하는 프로필 할당을 고려하기 위해 각 프로필의 우선순위를 설정할 수도 있습니다.

 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>모든 사용자의 기본 등록 상태 페이지 켜기

등록 상태 페이지를 사용하려면 아래 단계에 따릅니다.
 
1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **등록 상태 페이지(미리 보기)** 를 선택합니다.
2. **등록 상태 페이지** 블레이드에서 **기본값** > **설정**을 선택합니다.
3. **프로필 및 앱 설치 진행률 표시**에서 **예**를 선택합니다.
4. 사용하려는 다른 설정을 선택한 다음, **저장**을 선택합니다.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>등록 상태 페이지 프로필을 만들고 그룹에 할당

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **등록 상태 페이지(미리 보기)** > **프로필 만들기**를 선택합니다.
2. **이름** 및 **설명**을 제공합니다.
3. **만들기**를 선택합니다.
4. **등록 상태 페이지** 목록에서 새 프로필을 선택합니다.
5. **할당** > **그룹 선택**을 선택하고 이 프로필을 채택하려는 그룹을 선택한 후 **선택** > **저장**을 선택합니다.
6. **설정** > 이 프로필에 적용할 설정 선택 > **저장**을 선택합니다.

## <a name="set-the-enrollment-status-page-priority"></a>등록 상태 페이지 우선순위 설정

장치 또는 사용자는 여러 그룹에 있을 수 있으며, 여러 등록 상태 페이지 프로필을 보유할 수 있습니다. 이러한 충돌을 해결하려면 각 프로필의 우선 순위를 설정하면 됩니다. 누군가 등록 상태 페이지 프로필을 두 개 이상 보유하고 있다면 우선 순위가 가장 높은 프로필만 적용됩니다.

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **등록 상태 페이지(미리 보기)** 를 선택합니다.
2. 목록의 프로필을 마우스로 가리키세요.
3. 세로 점 세 개를 사용하여 목록의 원하는 위치로 프로필을 끕니다.


## <a name="enrollment-status-page-tracking-information"></a>등록 상태 페이지 추적 정보

상태 페이지는 장치 준비, 장치 설정 및 계정 설정에 대한 정보를 추적합니다.

### <a name="device-preparation"></a>장치 준비

장치 준비를 위해 등록 상태 페이지는 TPM(신뢰할 수 있는 플랫폼 모듈)키 증명(해당하는 경우), Azure Active Directory 조인 진행 상황 및 Intune 등록을 추적합니다.

### <a name="device-setup"></a>장치 설정

장치 설정을 위해 등록 상태 페이지는 모든 장치에 할당된 경우 다음 항목을 추적합니다.
- 보안 정책
    - 모든 등록에 대한 하나의 구성 서비스 공급자(CSP)입니다.
    - Intune에서 구성된 실제 CSP는 여기서 추적하지 않습니다.
- 응용 프로그램
    - 컴퓨터별 LoB(기간 업무) MSI 앱입니다.
    - 설치 컨텍스트 = 장치인 LoB 저장소 앱입니다.
    - 설치 컨텍스트 = 장치인 오프라인 저장소 및 LoB 저장소 앱입니다.
- 연결 프로필
    - **모든 장치** 또는 등록 장치가 멤버로 속한 Autopilot 장치의 장치 그룹에 할당된 VPN 또는 Wi-Fi 프로필
- **모든 장치** 또는 등록 장치가 멤버로 속한 Autopilot 장치의 장치 그룹에 할당된 인증서

### <a name="account-setup"></a>계정 설정
계정 설정을 위해 등록 상태 페이지는 다음 항목을 추적합니다.
- 보안 정책
    - 모든 등록에 대해 하나의 CSP입니다.
    - Intune에서 구성된 실제 CSP는 여기서 추적하지 않습니다.
- 응용 프로그램
    - 모든 장치, 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 사용자별 LoB MSI 앱입니다.
    - 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 컴퓨터별 LoB MSI 앱입니다.
    - 다음 중 하나에 할당된 LoB 스토어 앱, 온라인 스토어 앱 및 오프라인 스토어 앱입니다.
        - 모든 장치
        - 모든 사용자
        - 장치를 등록하는 사용자가 사용자로 설정된 설치 컨텍스트의 멤버인 사용자 그룹입니다.
- 연결 프로필
    - 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 VPN 또는 Wi-Fi 프로필입니다.
- 인증서
    - 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 인증서 프로필입니다.

## <a name="next-steps"></a>다음 단계
Windows 등록 페이지를 설정한 후 Windows 장치를 관리하는 방법을 알아봅니다. 자세한 내용은 [Microsoft Intune 장치 관리란?](https://docs.microsoft.com/intune/device-management)을 참조하세요.
