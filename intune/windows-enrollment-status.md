---
title: 등록 상태 페이지 설정
titleSuffix: Microsoft Intune
description: Windows 10 장치를 등록하는 사용자에게 인사하세요.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/17/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6604c35cebdad4341f27a51db1a4c735f9a9818
ms.sourcegitcommit: 6bd5867c41fb5288fde114dbfcc127dd206f7148
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235623"
---
# <a name="set-up-an-enrollment-status-page"></a>등록 상태 페이지 설정
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
장치 설정 중에는 등록 상태 페이지에 최종 사용자 장치에 관한 설치 상태 정보가 표시됩니다. 일부 응용 프로그램, 프로필 및 인증서는 사용자가 등록되는 시점에 완전히 설치되지 않을 수 있습니다. 상태 페이지는 사용자가 등록 중과 이후에 장치 상태를 이해하는 데 도움이 됩니다. 모든 사용자에 대해 상태 페이지를 사용하고, 할당된 모든 응용 프로그램과 프로필이 설치되기 전까지 사용자를 장치에서 차단할 수 있습니다.
 
모든 최종 사용자에 대해 등록 상태 페이지를 사용하려면 아래 단계에 따릅니다.
 
1.  [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **등록 상태 페이지(미리 보기)** 를 선택합니다.
2.  **등록 상태 페이지** 블레이드에서 **기본값** > **설정**을 선택합니다.
3.  **프로필 및 앱 설치 진행률 표시**에서 **예**를 선택합니다.
4.  사용하려는 다른 설정을 선택한 다음, **저장**을 선택합니다.
 
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
- 연결 프로필(VPN 및 Wi-Fi)은 아직 추적되지 않으므로 항상 "0 of 0"으로 표시됩니다.
- 인증서는 아직 추적되지 않으므로 항상 "0 of 0"으로 표시됩니다.

### <a name="account-setup"></a>계정 설정
계정 설정을 위해 등록 상태 페이지는 다음 항목을 추적합니다.
- 보안 정책
    - 모든 등록에 대해 하나의 CSP입니다.
    - Intune에서 구성된 실제 CSP는 여기서 추적하지 않습니다.
- 응용 프로그램
    - 모든 장치, 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 사용자별 LoB MSI 앱입니다.
    - 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 컴퓨터별 LoB MSI 앱입니다.
    - 설치 컨텍스트 = 사용자인 모든 장치, 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 LoB 저장소 앱입니다.
    - 설치 컨텍스트 = 사용자인 모든 장치, 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 온라인 저장소 앱입니다.
    - 설치 컨텍스트 = 사용자인 모든 장치, 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 오프라인 저장소 앱입니다.
- 연결 프로필
    - 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 VPN 또는 Wi-Fi 프로필입니다.
- 인증서
    - 모든 사용자 또는 장치를 등록하는 사용자가 구성원인 사용자 그룹에 할당된 인증서 프로필입니다.

## <a name="next-steps"></a>다음 단계
Windows 등록 페이지를 설정한 후 Windows 장치를 관리하는 방법을 알아봅니다. 자세한 내용은 [Microsoft Intune 장치 관리란?](https://docs.microsoft.com/intune/device-management)을 참조하세요.