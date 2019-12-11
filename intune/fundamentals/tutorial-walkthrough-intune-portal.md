---
title: 자습서 - Azure Portal에서 Intune 연습
titleSuffix: Microsoft Intune
description: 이 자습서에서는 작업 수행 방법을 더 잘 이해하기 위해 Microsoft Intune을 살펴봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9197d4f96eae1041b00b07110ef421a12a4fe338
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712988"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>자습서: Azure Portal에서 Microsoft Intune 연습

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure)에는 100개 이상의 서비스가 포함되어 다양한 클라우드 컴퓨팅 시나리오 및 가능성을 지원합니다. Microsoft Intune은 Azure에서 사용할 수 있는 여러 서비스 중 하나입니다. Intune를 사용하면 회사의 디바이스, 앱 및 데이터가 회사의 보안 요구 사항을 충족하는지 확인할 수 있습니다. 확인해야 할 요구 사항 및 이러한 요구 사항이 충족되지 않을 경우 발생하는 문제를 설정할 수 있는 제어 권한이 있습니다. [Azure portal](https://portal.azure.com)은 Microsoft Intune 서비스를 찾을 수 있는 곳입니다. Intune에서 사용할 수 있는 기능을 이해하면 다양한 MDM(모바일 디바이스 관리) 및 MAM(모바일 앱 관리) 작업을 수행하는 데 도움이 됩니다.

이 자습서에서는 다음 작업을 수행하게 됩니다.
> [!div class="checklist"]
> * Microsoft Intune 살펴보기
> * Azure Portal 구성

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건
Microsoft Intune을 설정하기 전에, 다음 요구 사항을 검토하세요.

- [지원되는 운영 체제 및 브라우저](../supported-devices-browsers.md) 
- [네트워크 구성 요구 사항 및 대역폭](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Microsoft Intune 무료 평가판 등록

Intune 평가판은 30일 동안 무료로 사용할 수 있습니다. 회사 또는 학교 계정이 이미 있는 경우 해당 계정으로 **로그인**하고 구독에 Intune을 추가합니다. 그렇지 않은 경우 조직에서 Intune을 사용하려면 [평가판 계정을 등록](free-trial-sign-up.md)할 수 있습니다.

> [!IMPORTANT]
> 새 계정을 등록한 후에는 기존 회사 또는 학교 계정을 결합할 수 없습니다.

## <a name="tour-microsoft-intune"></a>Microsoft Intune 살펴보기

Azure Portal에서 Intune을 더 잘 이해하려면 다음 단계를 따릅니다. 살펴보기를 완료하면 Intune의 주요 사항 중 일부를 더 잘 이해할 수 있습니다.

1. 브라우저를 열고 [Intune 포털](https://aka.ms/intuneportal)에 로그인합니다. Intune을 처음 사용하는 경우 평가판 구독을 사용합니다.

    ![Microsoft Intune 포털 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Azure에서 Intune 또는 다른 서비스를 열 때 서비스가 창에 표시됩니다. Intune에서 사용할 수 있는 첫 번째 워크로드 중 일부에는 **디바이스**, **클라이언트 앱**, **사용자** 및 **그룹**이 포함됩니다. 워크로드는 서비스의 하위 영역일 뿐입니다. 워크로드를 선택하면 해당 창이 전체 페이지로 열립니다. 기타 창이 열고 닫혀 이전 창을 표시하는 경우 해당 창의 오른쪽에서 슬라이드 아웃됩니다. 창을 블레이드라고도 합니다. 

    기본적으로 Intune을 여는 경우 **개요** 창이 표시됩니다. 이 창에서는 앱 설치 상태뿐만 아니라 디바이스 할당 및 규정 준수 상태의 전체적인 시각적 스냅샷을 제공합니다.

2. [Intune](https://aka.ms/intuneportal)에서 **디바이스 등록**을 선택하여 Intune 테넌트에 등록된 디바이스의 세부 정보를 표시합니다. 새 Intune 테넌트로 시작하는 경우 아직 등록된 디바이스가 없습니다. 

    ![디바이스 등록 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Intune을 사용하면 회사 데이터에 액세스하는 방법을 포함하여 직원의 디바이스 및 앱을 관리할 수 있습니다. 이 MDM(모바일 디바이스 관리) 서비스를 사용하려면 먼저 디바이스를 Intune에 등록해야 합니다. 디바이스가 등록되면 MDM 인증서가 발급됩니다. 이 인증서는 Intune 서비스와 통신하는 데 사용됩니다. 

    Intune에 직원의 디바이스를 등록하는 몇 가지 방법이 있습니다. 각 방법은 디바이스의 소유권(개인 또는 회사), 기기 유형(iOS, Windows, Android) 및 관리 요구 사항(재설정, 선호도, 잠금)에 따라 다릅니다. 그러나 디바이스 등록을 활성화하기 전에 Intune 인프라를 설정해야 합니다. 특히 디바이스를 등록하려면 [MDM 기관을 설정](mdm-authority-set.md)해야 합니다. Intune 환경(테넌트)을 준비하는 방법에 대한 자세한 내용은 [Intune 설정](setup-steps.md)을 참조하세요. Intune 테넌트가 준비되면 디바이스를 등록할 수 있습니다. 디바이스 등록에 대한 자세한 내용은 [디바이스 등록이란?](../enrollment/device-enrollment.md)을 참조하세요.

3. [Intune](https://aka.ms/intuneportal)에서 **디바이스 준수**를 선택하여 Intune에서 관리되는 디바이스의 규정 준수에 대한 세부 정보를 표시합니다. 다음 이미지와 비슷하게 세부 정보가 표시됩니다.

    ![디바이스 준수 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    규정 준수 요구 사항은 기본적으로 디바이스 PIN 또는 디바이스 암호화를 요구하는 등의 규칙입니다. 디바이스 준수 정책은 준수하는 것으로 간주되려면 디바이스가 따라야 하는 규칙 및 설정을 정의합니다. 디바이스 준수를 사용하려면 다음이 있어야 합니다.
    - Intune 및 Azure AD(Azure Active Directory) 프리미엄 구독
    - 지원되는 플랫폼을 실행하는 디바이스
    - Intune에 등록되어야 하는 디바이스
    - 한 명의 사용자 또는 기본 사용자 중 하나에 등록된 디바이스입니다.
    
    자세한 내용은 [Intune에서 디바이스 준수 정책 시작](../protect/device-compliance-get-started.md)을 참조하세요.

4. [Intune](https://aka.ms/intuneportal)에서 **디바이스 구성**을 선택하여 Intune의 디바이스 프로필에 대한 세부 정보를 표시합니다.

    ![디바이스 구성 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Intune은 조직 내의 다른 디바이스에서 사용하거나 사용하지 않게 할 수 있는 설정 및 기능을 포함합니다. 이러한 설정 및 기능을 "구성 프로필"에 추가합니다. iOS, Android 및 Windows를 포함하여 다양한 디바이스 및 플랫폼에 대한 프로필을 만들 수 있습니다. 그런 다음, Intune을 사용하여 조직의 디바이스에 프로필을 적용할 수 있습니다.   

    디바이스 구성에 대한 자세한 내용은 [Microsoft Intune에서 디바이스 프로필을 사용하여 디바이스에서 기능 설정 적용](../configuration/device-profiles.md)을 참조하세요.

5. [Intune](https://aka.ms/intuneportal)에서 **디바이스**를 선택하여 Intune 테넌트의 등록된 디바이스에 대한 세부 정보를 표시합니다. 새 Intune 등록으로 시작하는 경우 아직 등록된 디바이스가 없습니다.

    ![디바이스 등록 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)

    **디바이스** 창에서는 테넌트의 등록된 디바이스에 대한 세부 정보를 제공합니다. **모든 디바이스**를 클릭하여 Intune 테넌트에 대한 디바이스 목록을 표시할 수 있습니다.

6. [Intune](https://aka.ms/intuneportal)에서 **클라이언트 앱**을 선택하여 앱 설치 상태를 표시합니다.

    ![클라이언트 앱 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)

    IT 관리자는 Microsoft Intune을 사용하여 회사의 직원이 사용하는 클라이언트 앱을 관리할 수 있습니다. 이 기능은 디바이스 관리 및 데이터 보호 외에 추가적인 것입니다. 관리자의 우선 순위 중 하나는 최종 사용자가 업무 수행에 필요한 앱을 액세스할 수 있게 하는 것입니다. 또한 Intune에 등록되지 않은 디바이스에서 앱을 할당하고 관리할 수 있습니다. Intune은 원하는 디바이스에서 필요한 앱을 얻도록 도와주는 다양한 기능을 제공합니다. 앱을 추가하고 할당하는 방법에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](../apps/apps-add.md) 및 [Microsoft Intune을 사용하여 그룹에 앱 할당](../apps/apps-deploy.md)을 참조하세요.

7. [Intune](https://aka.ms/intuneportal)에서 **조건부 액세스**를 선택하여 액세스 정책에 대한 세부 정보를 표시합니다.

    ![조건부 액세스 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    조건부 액세스는 메일 및 회사 리소스에 연결할 수 있는 앱과 디바이스를 제어할 수 있는 방법을 말합니다. 디바이스 기반 및 앱 기반 조건부 액세스에 대해 알아보고 Intune을 사용한 조건부 액세스를 사용하는 일반적인 시나리오를 찾아보려면 [조건부 액세스란?](../protect/conditional-access.md)을 참조하세요.

8. [Intune](https://aka.ms/intuneportal)에서 **사용자**를 선택하여 Intune에 포함된 사용자에 대한 세부 정보를 표시합니다. 이러한 사용자는 회사의 직원입니다.

    ![사용자 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    사용자를 직접 Intune에 추가하거나 온-프레미스 Active Directory에서 사용자를 동기화할 수 있습니다. 추가된 사용자는 디바이스를 등록하고 회사 리소스에 액세스할 수 있습니다. 또한 사용자에게 Intune에 액세스하는 추가적인 사용 권한을 제공할 수 있습니다. 자세한 내용은 [사용자 추가 및 Intune에 관리 권한 부여](users-add.md)를 참조하세요.

9. [Intune](https://aka.ms/intuneportal)에서 **그룹**을 선택하여 Intune에 포함된 Azure AD(Azure Active Directory) 그룹에 대한 세부 정보를 표시합니다. Intune 관리자는 그룹을 사용하여 디바이스 및 사용자를 관리할 수 있습니다.

    ![그룹 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    조직의 요구에 맞도록 그룹을 설정할 수 있습니다. 그룹을 만들어 지리적 위치, 부서 또는 하드웨어 특성별로 사용자 또는 디바이스를 구성합니다. 그룹을 사용하여 대규모 작업을 관리합니다. 예를 들어 많은 사용자에 대해 정책을 설정하거나 디바이스 세트에 앱을 배포할 수 있습니다. 그룹에 대한 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](../groups-add.md)을 참조하세요.

10. [Intune](https://aka.ms/intuneportal)에서 **도움말 및 지원**을 선택하여 도움을 요청합니다. IT 관리자 권한으로 **도움말 및 지원** 옵션을 사용하여 Intune에 대한 온라인 지원 티켓을 저장할 뿐만 아니라 솔루션을 검색하고 확인할 수 있습니다. 

    ![도움말 및 지원 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    지원 티켓을 만들려면 Azure Active Directory의 관리자 역할로 계정이 할당되어야 합니다. 관리자 역할에는 **Intune 관리자**, **글로벌 관리자** 및 **서비스 관리자**가 포함됩니다. 자세한 내용은 [Microsoft Intune에 대한 지원을 받는 방법](../get-support.md)을 참조하세요.

11. [Intune](https://aka.ms/intuneportal)에서 **테넌트 상태**를 선택하여 Intune 테넌트에 대한 세부 정보를 표시합니다.

    ![테넌트 상태 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    테넌트 상태 세부 정보에는 커넥터 상태, Intune 서비스 상태 및 Intune 뉴스가 포함됩니다. 테넌트 또는 Intune 자체가 포함된 문제가 있는 경우 **테넌트 상태** 창에서 세부 정보를 찾을 수 있습니다. 자세한 내용은 [Intune 테넌트 상태](../tenant-status.md)를 참조하세요.

12. [Intune](https://aka.ms/intuneportal)에서 **문제 해결**을 선택하면 문제 해결 팁, 지원 요청 또는 Intune 상태 확인에 대한 바로 가기로 이동합니다. 이 정보는 선택한 Intune 사용자에 따라 다릅니다.

    ![문제 해결 창 스크린샷](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Intune 내 문제 해결에 대한 자세한 내용은 [문제 해결 포털을 사용하여 회사 내 사용자 지원](../help-desk-operators.md)을 참조하세요.

## <a name="configure-the-azure-portal"></a>Azure Portal 구성

Azure를 사용하면 포털의 보기를 사용자 지정하고 구성할 수 있습니다.

### <a name="change-the-sidebar"></a>사이트바 변경

Azure Portal의 왼쪽에 있는 **사이드바**에는 사용 가능한 모든 Azure 서비스 목록이 표시됩니다. 가장 중요한 서비스의 영구적 보기를 유지할 수 있도록 이 포괄적인 목록을 기본 보기에서 수정할 수 있습니다. 아래 정보는 목록의 맨 위에 추가할 서비스의 예로 Intune을 사용합니다.

![사용자가 ‘추가 서비스’ 목록에서 Microsoft Intune을 검색 중입니다.](./media/tutorial-walkthrough-intune-portal/azure-add-intune1.png)

1. 페이지 왼쪽에 있는 사이드바에서 **모든 서비스**를 선택합니다.
2. 필터 상자에서 **Intune**을 검색합니다.
3. **별**을 선택하여 Intune을 즐겨찾기 서비스 목록 아래쪽에 추가합니다.
4. Intune 서비스를 마우스로 가리킵니다. 서비스 이름 오른쪽에 있는 **세로 점 세 개**를 사용하여 Intune을 선택하고 끕니다.

### <a name="change-the-dashboard"></a>대시보드 변경

기본 방문 페이지는 **대시보드**입니다. 이 페이지에서는 가장 관련성이 높은 정보를 표시하도록 타일을 사용자 지정합니다.

![일반적인 새 대시보드의 이미지입니다. 모든 서비스가 왼쪽에 있고 기본 대시보드가 가운데에 있는 사이드바를 보여 줍니다. 대시보드 수정 단추는 상단을 따라 있으며, 대시보드에는 모든 리소스, 빠른 시작 자습서, 서비스 상태 및 Azure Marketplace에 액세스할 수 있는 타일이 있습니다.](./media/tutorial-walkthrough-intune-portal/azure-default-dashboard.png)

현재 대시보드를 수정하려면 **대시보드 편집** 단추를 선택합니다. 기본 대시보드를 변경하지 않으려는 경우 **새 대시보드**를 만들 수도 있습니다. 새 대시보드를 만들면 타일을 추가하거나 재배열할 수 있는 **타일 갤러리**가 포함된 빈 프라이빗 대시보드가 제공됩니다. 타일은 **일반** 범주인 **유형**별로 찾거나 **검색** 및 **리소스 그룹** 또는 **태그**를 통해 찾을 수 있습니다.

어떤 **줄임표** 단추에서든 **대시보드에 고정**을 선택하여 대시보드에 직접 타일을 추가할 수도 있습니다.

![Intune의 [사용자 및 그룹 > 모든 그룹] 위치의 확대 사진으로, 그룹의 오른쪽 끝에 “대시보드에 고정” 옵션이 표시되어 있습니다.](./media/tutorial-walkthrough-intune-portal/azure-pin-to-dashboard.png)

이 기능은 Intune에 그룹 및 사용자와 같은 콘텐츠를 더 추가하고 나면 관련성이 더 높아집니다.

## <a name="next-steps"></a>다음 단계

Microsoft Intune에서 신속하게 실행하려면 먼저 Intune 체험 계정을 설정하여 Intune 빠른 시작을 단계별로 진행합니다.

> [!div class="nextstepaction"]
> [빠른 시작: Microsoft Intune 평가판 체험](free-trial-sign-up.md)
