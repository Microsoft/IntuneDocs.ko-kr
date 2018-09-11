---
title: Microsoft Intune의 30일 무료 평가판 등록
titleSuffix: Microsoft Intune
description: Microsoft Intune의 30일 무료 평가판에 등록하는 방법에 대해 알아봅니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: get-started
ms.openlocfilehash: 6492b757376c95c366d45a63b05f2ec60bdd791b
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44254125"
---
# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Microsoft Intune 무료 평가판 등록


이 문서에서는 Azure Portal용 Intune 독립 실행형 평가판에 등록하는 과정을 안내합니다.

1. [Intune 등록](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) 페이지를 방문하여 평가판 구독에 등록하는 양식을 작성합니다.
2. 회사 또는 학교 계정이 있고 Intune 평가판에 이 계정을 사용하려면 대신 [이 로그인 지침](/intune/account-sign-up)을 따르세요.

* 대부분의 IT 작업자 및 사용자가 여러분과 다른 로캘에 있는 경우 **회사 위치는 어디입니까?** 아래에서 로캘을 선택할 수 있습니다.

2. 등록 프로세스가 끝나면 새 계정 정보가 포함된 메시지가 제공됩니다. <br/> 

![계정 정보 이미지](./media/2-end-of-sign-up-process.png) <br/>

이제 **준비가 되었습니다.** 를 클릭하면 테스트 환경에 사용자를 추가할 수 있는 Office 365 관리 센터로 이동합니다. <br/><br/>그러나 Intune Azure Portal로 직접 이동하려면 새 브라우저 창을 열고 주소 표시줄에 **https://portal.azure.com** 을 입력합니다. 그러면 제공된 자격 증명을 사용하여 로그인할 수 있는 Azure 로그인 페이지로 이동합니다. Intune 평가판에 로그인할 때마다 이 주소를 사용합니다. <br/> ![Azure Portal 로그인 페이지 이미지](./media/azure-portal-signin.png)

Intune [Azure portal](https://portal.azure.com)에 처음으로 로그온한 경우 Azure 대시보드에 Intune이 표시되지 않을 수 있습니다. Azure 대시보드에 Intune 서비스를 추가하려면 다음을 수행합니다.
1. 대시보드의 왼쪽에 있는 Azure 서비스 목록에서 **모든 서비스 >** 를 선택하고 검색 상자에 **Intune**을 입력합니다.
2. 목록에서 **Intune**을 선택하고, 별표를 선택하여 서비스 목록에 서비스를 추가합니다.<br/> ![Azure Portal 내에서 Microsoft Intune 선택 이미지](./media/azure-add-intune1.png)
3. 그런 다음 서비스 목록에서 **Intune**을 선택하면 Intune 대시보드가 열립니다.

평가판에 등록하는 경우 등록 과정 중에 제공한 메일 주소로 계정 정보가 포함된 메일 메시지도 제공됩니다. 이 전자 메일을 통해 평가판이 활성화된 것을 확인합니다.

## <a name="keeping-the-admin-experiences-straight"></a>관리자 환경 계속 유지

사용할 수 있는 포털이 두 개 있습니다.
- [Intune의 기능](what-is-intune.md)을 탐색할 수 있는 Azure의 Intune 대시보드([portal.azure.com](https://portal.azure.com))입니다. 일반적으로 Intune 대시보드에서 작업을 수행합니다.
- Azure Active Directory를 사용하지 않는 경우 사용자를 추가 및 관리할 수 있는Office 365 관리 센터([portal.office.com](https://portal.office.com))입니다. 또한 대금 청구 및 지원을 포함하여 계정의 다른 측면을 관리할 수 있습니다.

## <a name="next-steps"></a>다음 단계

### <a name="integration-with-other-products"></a>다른 제품과의 통합
Intune에서 Azure Active Directory 사용자 계정을 사용하는 방법을 자세히 알아봅니다.
- [ID 요구 사항](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [디렉터리 동기화 요구 사항](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [다단계 인증 요구 사항](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

[System Center Configuration Manager와 함께 Intune](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)를 사용하는 방법에 대해 자세히 알아보기
