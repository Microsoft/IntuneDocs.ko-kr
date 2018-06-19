---
title: Intune 장치 등록에 대한 다단계 인증
description: Azure AD에서 장치를 등록하기 위해 다단계 인증을 요구하는 방법입니다.
keywords: ''
author: dougeby
ms.author: angrobe
manager: angerobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: 62568a307b5e28c9543a8bb73271da2f55c44ae4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31014132"
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Intune 장치 등록에 대한 다단계 인증

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune은 장치 등록을 위해 Azure AD MFA(다단계 인증)을 통합하여 회사 리소스를 보호할 수 있게 합니다.

MFA는 다음과 같은 확인 방법을 두 가지 이상 요구하는 방식으로 작동합니다. 

- 사용자가 알고 있는 항목(대개 암호 또는 PIN)
- 사용자가 가지고 있는 항목(휴대폰처럼 쉽게 복제할 수 없으며 신뢰할 수 있는 장치)
- 사용자의 특징(생체 인식)

MFA는 iOS, Android, Windows 8.1 이상 또는 Windows Phone 8.1 이상의 장치에서 지원됩니다.

> [!NOTE]
> Configuration Manager의 이전 버전(릴리스 1610 이전)에서는 Configuration Manager 관리자 콘솔에서 MFA 설정을 계속 볼 수 있습니다. Configuration Manager 관리자 콘솔은 더 이상 작동하지 않으므로 MFA를 구성하려 하지 마세요. 이 항목에 설명된 대로 MFA를 구성합니다.

### <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>장치 등록 단계에서 다단계 인증을 요구하도록 Intune 구성
장치를 등록하라 때 MFA를 요구하려면 다음 단계를 따르세요.

1. 관리자 자격 증명으로 [Microsoft Azure 포털](https://manage.windowsazure.com)에 로그인합니다.
2. 테넌트를 선택합니다.
2. **응용 프로그램** 탭을 선택합니다. Azure AD 보안 기능을 구성할 수 있는 서비스 목록이 표시됩니다.
3. **Microsoft Intune 등록**을 선택합니다.
4. **구성**을 선택합니다. 
5. **다단계 인증 및 위치 기반 액세스 규칙** 아래에서 다음을 수행할 수 있습니다.
    
    -  액세스 규칙 사용
    -  모든 사용자에게 규칙을 적용할지 특정 Azure AD 보안 그룹에 적용할지를 선택합니다.
    -  모든 장치 등록에 다단계 인증이 필요합니다.
    -  장치가 회사에 없는 경우 등록 시 다단계 인증이 필요합니다.
    -  **회사 리소스에 대한 액세스 차단**을 선택하여 장치가 회사 네트워크에 등록되지 않은 경우 장치 등록을 차단합니다. 
4. 또한 **회사 네트워크 위치 정의/편집** 링크를 클릭하여 장치 등록에 대한 네트워크 연결 요구 사항을 구성할 수도 있습니다.

> [!IMPORTANT]
> 
> Microsoft Intune 등록에 대한 **장치 기반 액세스 규칙**을 구성하지 마세요.
