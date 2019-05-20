---
title: Windows 10용 앱 보호 정책 구성
titleSuffix: Microsoft Intune
description: 이 항목에서는 Windows 10 디바이스의 APP(앱 보호 정책)를 구성하는 방법을 설명합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f7bff9fa319f8df1abc4622237d1f9b98b9a685
ms.sourcegitcommit: 617bd653c34c1e6a4e2ad61811c5912f8dab775c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/10/2019
ms.locfileid: "59570717"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Windows 10용 앱 보호 정책 구성 준비 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Azure AD에서 MAM 공급자를 설정하여 Windows 10용 MAM(모바일 애플리케이션 관리)을 사용하도록 설정합니다. Azure AD에서 MAM 공급자를 설정하면 Intune을 사용하여 새 WIP(Windows Information Protection) 정책을 만들 때 등록 상태를 정의할 수 있습니다. 등록 상태는 MAM 또는 MDM(모바일 디바이스 관리)일 수 있습니다.

## <a name="to-configure-the-mam-provider"></a>MAM 공급자를 구성하려면

1. Azure Portal에 로그인하고 **Azure Active Directory**를 선택합니다.

2. **관리** 그룹에서 **이동성(MDM 및 MAM)** 을 선택합니다.

3. **Microsoft Intune**을 클릭합니다.

4. **구성** 블레이드의 **기본 MAM URL 복원** 그룹에서 설정을 구성합니다.

   **MAM 사용자 범위**  
   MAM 자동 등록을 사용하여 직원의 Windows 디바이스에서 엔터프라이즈 데이터를 관리합니다. MAM 자동 등록은 Bring Your Own Device 시나리오용으로 구성됩니다.<ul><li>**없음**<br>사용자가 MAM에 등록될 수 없는 경우 선택합니다.</li><li>**일부**<br>MAM에 등록될 사용자가 포함된 Azure AD 그룹을 선택합니다.</li><li>**모두**<br>모든 사용자가 MAM에 등록될 수 있는 경우 선택합니다.</li></ul>

   **MAM 사용 약관 URL**  
   MAM 사용 약관 URL은 Microsoft Intune에서 지원되지 않습니다. 이 입력 상자는 보호 정책을 적용하도록 비워 두어야 합니다.

   **MAM 검색 URL**  
   MAM 서비스 등록 엔드포인트의 URL입니다. 등록 엔드포인트는 MAM 서비스에서 관리할 디바이스를 등록하는 데 사용됩니다.

   **MAM 준수 URL**  
   MAM 준수 URL은 Microsoft Intune에서 지원되지 않습니다. 이 입력 상자는 보호 정책을 적용하도록 비워 두어야 합니다. 

5.  **저장**을 클릭합니다.

## <a name="next-steps"></a>다음 단계

[WIP 앱 보호 정책 만들기](windows-information-protection-policy-create.md)
