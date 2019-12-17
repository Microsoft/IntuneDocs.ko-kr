---
title: 자습서 - Microsoft 엔드포인트 관리자에서 Intune 연습
titleSuffix: Microsoft Intune
description: 이 자습서에서는 작업 수행 방법을 더 잘 이해하기 위해 Microsoft 엔드포인트 관리자 관리 센터에서의 Microsoft Intune을 살펴봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 267f09c3dc16aab10fbe64f0e8662ee6f7c7ffa0
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907994"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>자습서: Microsoft Endpoint Manager에서 Intune 연습

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure)에는 100개 이상의 서비스가 포함되어 다양한 클라우드 컴퓨팅 시나리오 및 가능성을 지원합니다. Microsoft Intune은 Azure에서 사용할 수 있는 여러 서비스 중 하나입니다. Intune를 사용하면 회사의 디바이스, 앱 및 데이터가 회사의 보안 요구 사항을 충족하는지 확인할 수 있습니다. 확인해야 할 요구 사항 및 이러한 요구 사항이 충족되지 않을 경우 발생하는 문제를 설정할 수 있는 제어 권한이 있습니다. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 Microsoft Intune 서비스와 기타 디바이스 관리 관련 설정을 찾을 수 있습니다. Intune에서 사용할 수 있는 기능을 이해하면 다양한 MDM(모바일 디바이스 관리) 및 MAM(모바일 앱 관리) 작업을 수행하는 데 도움이 됩니다.

> [!NOTE]
> Microsoft Endpoint Manager는 모든 엔드포인트를 관리하기 위한 단일 통합형 엔드포인트 관리 플랫폼입니다. 이 Microsoft Endpoint Manager 관리 센터는 ConfigMgr와 Microsoft Intune에 연결됩니다.

이 자습서에서는 다음 작업을 수행하게 됩니다.
> [!div class="checklist"]
> * Microsoft 엔드포인트 관리자 관리 센터 살펴보기
> * Microsoft 엔드포인트 관리자 관리 센터의 보기 사용자 지정

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건
Microsoft Intune을 설정하기 전에, 다음 요구 사항을 검토하세요.

- [지원되는 운영 체제 및 브라우저](../supported-devices-browsers.md) 
- [네트워크 구성 요구 사항 및 대역폭](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Microsoft Intune 무료 평가판 등록

Intune 평가판은 30일 동안 무료로 사용할 수 있습니다. 회사 또는 학교 계정이 이미 있는 경우 해당 계정으로 **로그인**하고 구독에 Intune을 추가합니다. 그렇지 않은 경우 조직에서 Intune을 사용하려면 [평가판 계정을 등록](free-trial-sign-up.md)할 수 있습니다.

> [!IMPORTANT]
> 새 계정을 등록한 후에는 기존 회사 또는 학교 계정을 결합할 수 없습니다.

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Microsoft 엔드포인트 관리자 관리 센터의 Microsoft Intune 살펴보기

Microsoft 엔드포인트 관리자 관리 센터의 Intune을 더 잘 이해하려면 아래 단계를 따릅니다. 살펴보기를 완료하면 Intune의 주요 사항 중 일부를 더 잘 이해할 수 있습니다.

1. 브라우저를 열고 [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다. Intune을 처음 사용하는 경우 평가판 구독을 사용합니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 홈 페이지의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    Azure에서 Microsoft 엔드포인트 관리자 또는 다른 서비스를 열 때 서비스가 창에 표시됩니다. Intune에서 사용할 수 있는 첫 번째 워크로드 중 일부에는 **디바이스**, **앱**, **사용자** 및 **그룹**이 포함됩니다. 워크로드는 서비스의 하위 영역일 뿐입니다. 워크로드를 선택하면 해당 창이 전체 페이지로 열립니다. 기타 창이 열고 닫혀 이전 창을 표시하는 경우 해당 창의 오른쪽에서 슬라이드 아웃됩니다. 

    기본적으로 Microsoft 엔드포인트 관리자를 열면 **홈 페이지** 창이 표시됩니다. 이 창에서는 기타 유용한 관련 링크뿐만 아니라 테넌트 상태 및 규정 준수 상태의 전체적인 시각적 스냅샷을 제공합니다.

2. 탐색 창에서 **대시보드**를 선택하여 Intune 테넌트의 디바이스 및 클라이언트 앱에 대한 전체 세부 정보를 표시합니다. 새 Intune 테넌트로 시작하는 경우 아직 등록된 디바이스가 없습니다. 

    ![Microsoft 엔드포인트 관리자 관리 센터 - 대시보드의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Intune을 사용하면 회사 데이터에 액세스하는 방법을 포함하여 직원의 디바이스 및 앱을 관리할 수 있습니다. 이 MDM(모바일 디바이스 관리) 서비스를 사용하려면 먼저 디바이스를 Intune에 등록해야 합니다. 디바이스가 등록되면 MDM 인증서가 발급됩니다. 이 인증서는 Intune 서비스와 통신하는 데 사용됩니다. 

    Intune에 직원의 디바이스를 등록하는 몇 가지 방법이 있습니다. 각 방법은 디바이스의 소유권(개인 또는 회사), 기기 유형(iOS, Windows, Android) 및 관리 요구 사항(재설정, 선호도, 잠금)에 따라 다릅니다. 그러나 디바이스 등록을 활성화하기 전에 Intune 인프라를 설정해야 합니다. 특히 디바이스를 등록하려면 [MDM 기관을 설정](mdm-authority-set.md)해야 합니다. Intune 환경(테넌트)을 준비하는 방법에 대한 자세한 내용은 [Intune 설정](setup-steps.md)을 참조하세요. Intune 테넌트가 준비되면 디바이스를 등록할 수 있습니다. 디바이스 등록에 대한 자세한 내용은 [디바이스 등록이란?](../enrollment/device-enrollment.md)을 참조하세요.

3. 탐색 창에서 **디바이스**를 선택하여 Intune 테넌트에 등록된 디바이스의 세부 정보를 표시합니다. 

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스**를 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    **디바이스 - 개요** 창에는 다음 상태 및 경고에 대한 요약을 볼 수 있는 여러 탭이 있습니다.
    - **등록 상태** - 플랫폼 및 등록 오류별로 Intune 등록 디바이스에 대한 세부 정보를 검토합니다.
    - **등록 경고** - 플랫폼별로 할당되지 않은 디바이스에 대한 자세한 내용을 확인합니다. 
    - **준수 상태** - 디바이스, 정책, 설정, 위협 및 보호에 따라 준수 상태를 검토합니다. 또한 이 창에서는 준수 정책을 사용하지 않는 디바이스 목록을 제공합니다.
    - **구성 상태** - 프로필 배포뿐만 아니라 디바이스 프로필의 구성 상태를 검토합니다. 
    - **소프트웨어 업데이트 상태** - 모든 디바이스 및 모든 사용자에 대한 배포 상태를 시각적으로 표시합니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 디바이스의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. **디바이스 - 개요** 창에서 **준수 정책**을 선택하여 Intune에서 관리되는 디바이스의 규정 준수에 대한 세부 정보를 표시합니다. 다음 이미지와 비슷하게 세부 정보가 표시됩니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 준수 정책의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스 규정 준수**를 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    규정 준수 요구 사항은 기본적으로 디바이스 PIN 또는 디바이스 암호화를 요구하는 등의 규칙입니다. 디바이스 준수 정책은 준수하는 것으로 간주되려면 디바이스가 따라야 하는 규칙 및 설정을 정의합니다. 디바이스 준수를 사용하려면 다음이 있어야 합니다.
    - Intune 및 Azure AD(Azure Active Directory) 프리미엄 구독
    - 지원되는 플랫폼을 실행하는 디바이스
    - Intune에 등록되어야 하는 디바이스
    - 한 명의 사용자 또는 기본 사용자 중 하나에 등록된 디바이스입니다.
    
    자세한 내용은 [Intune에서 디바이스 준수 정책 시작](../protect/device-compliance-get-started.md)을 참조하세요.

5. **디바이스 - 개요** 창에서 **조건부 액세스**를 선택하여 액세스 정책에 대한 세부 정보를 표시합니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 조건부 액세스의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **조건부 액세스**를 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    조건부 액세스는 메일 및 회사 리소스에 연결할 수 있는 앱과 디바이스를 제어할 수 있는 방법을 말합니다. 디바이스 기반 및 앱 기반 조건부 액세스에 대해 알아보고 Intune을 사용한 조건부 액세스를 사용하는 일반적인 시나리오를 찾아보려면 [조건부 액세스란?](../protect/conditional-access.md)을 참조하세요.

6. 탐색 창에서 **디바이스** > **구성 프로필**을 선택하여 Intune의 디바이스 프로필에 대한 세부 정보를 표시합니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 구성 프로필의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스 구성**을 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    Intune은 조직 내의 다른 디바이스에서 사용하거나 사용하지 않게 할 수 있는 설정 및 기능을 포함합니다. 이러한 설정 및 기능을 "구성 프로필"에 추가합니다. iOS, Android, macOS 및 Windows를 포함하여 다양한 디바이스 및 플랫폼에 대한 프로필을 만들 수 있습니다. 그런 다음, Intune을 사용하여 조직의 디바이스에 프로필을 적용할 수 있습니다.   

    디바이스 구성에 대한 자세한 내용은 [Microsoft Intune에서 디바이스 프로필을 사용하여 디바이스에서 기능 설정 적용](../configuration/device-profiles.md)을 참조하세요.

7. 탐색 창에서 **디바이스** > **모든 디바이스**를 선택하여 Intune 테넌트의 등록된 디바이스에 대한 세부 정보를 표시합니다. 새 Intune 등록으로 시작하는 경우 아직 등록된 디바이스가 없습니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 모든 디바이스의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    이 디바이스 목록에는 규정 준수, OS 버전 및 마지막 체크 인 날짜에 대한 주요 정보가 표시됩니다.

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스** > **모든 디바이스**를 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.
 
8. 탐색 창에서 **앱**을 선택하여 앱 상태 개요를 표시합니다. 이 창에서는 다음 탭을 기반으로 앱 설치 상태를 제공합니다.

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **클라이언트 앱**을 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    **앱 - 개요** 창에는 다음 상태에 대한 요약을 볼 수 있는 두 개의 탭이 있습니다.
    - **설치 상태** - 디바이스의 상위 설치 오류뿐만 아니라 설치 오류가 있는 앱을 표시합니다.  
    - **앱 보호 정책 상태** - 플래그가 지정된 사용자뿐만 아니라 앱 보호 정책에 할당된 사용자에 대한 세부 정보를 찾습니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 앱의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    IT 관리자는 Microsoft Intune을 사용하여 회사의 직원이 사용하는 클라이언트 앱을 관리할 수 있습니다. 이 기능은 디바이스 관리 및 데이터 보호 외에 추가적인 것입니다. 관리자의 우선 순위 중 하나는 최종 사용자가 업무 수행에 필요한 앱을 액세스할 수 있게 하는 것입니다. 또한 Intune에 등록되지 않은 디바이스에서 앱을 할당하고 관리할 수 있습니다. Intune은 원하는 디바이스에서 필요한 앱을 얻도록 도와주는 다양한 기능을 제공합니다. 

    > [!NOTE]
    > **앱 - 개요** 창에는 테넌트 상태 및 계정 정보도 제공됩니다.

    앱을 추가하고 할당하는 방법에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](../apps/apps-add.md) 및 [Microsoft Intune을 사용하여 그룹에 앱 할당](../apps/apps-deploy.md)을 참조하세요.

9. **앱 - 개요** 창에서 **모든 앱**을 선택하여 Intune에 추가된 앱 목록을 확인합니다.

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **클라이언트 앱** > **앱**을 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    플랫폼에 따라 다양한 앱 유형을 Intune에 추가할 수 있습니다. 앱을 추가한 후에는 사용자 그룹에 할당할 수 있습니다. 

    ![Microsoft 엔드포인트 관리자 관리 센터 - 모든 앱의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    자세한 내용은 [Microsoft Intune에 앱 추가](~/apps/apps-add.md)를 참조하세요. 

10. 탐색 창에서 **사용자**를 선택하여 Intune에 포함된 사용자에 대한 세부 정보를 표시합니다. 이러한 사용자는 회사의 직원입니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 사용자의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **사용자**를 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    사용자를 직접 Intune에 추가하거나 온-프레미스 Active Directory에서 사용자를 동기화할 수 있습니다. 추가된 사용자는 디바이스를 등록하고 회사 리소스에 액세스할 수 있습니다. 또한 사용자에게 Intune에 액세스하는 추가적인 사용 권한을 제공할 수 있습니다. 자세한 내용은 [사용자 추가 및 Intune에 관리 권한 부여](users-add.md)를 참조하세요.

11. 탐색 창에서 **그룹**을 선택하여 Intune에 포함된 Azure AD(Azure Active Directory) 그룹에 대한 세부 정보를 표시합니다. Intune 관리자는 그룹을 사용하여 디바이스 및 사용자를 관리할 수 있습니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 그룹의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **그룹**을 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    조직의 요구에 맞도록 그룹을 설정할 수 있습니다. 그룹을 만들어 지리적 위치, 부서 또는 하드웨어 특성별로 사용자 또는 디바이스를 구성합니다. 그룹을 사용하여 대규모 작업을 관리합니다. 예를 들어 많은 사용자에 대해 정책을 설정하거나 디바이스 세트에 앱을 배포할 수 있습니다. 그룹에 대한 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](../groups-add.md)을 참조하세요.

12. 탐색 창에서 **테넌트 관리**를 선택하여 Intune 테넌트에 대한 세부 정보를 표시합니다.

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **테넌트 상태**를 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    **테넌트 관리자 - 테넌트 상태** 창에는 **테넌트 세부 정보**, **커넥터 상태**및 **서비스 상태 대시보드**에 대한 탭이 제공됩니다. 테넌트 또는 Intune 자체가 포함된 문제가 있는 경우 이 창에서 세부 정보를 찾을 수 있습니다. 

    ![Microsoft 엔드포인트 관리자 관리 센터 - 테넌트 상태의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    자세한 내용은 [Intune 테넌트 상태](../tenant-status.md)를 참조하세요.

13. 탐색 창에서 **문제 해결 + 지원** > **문제 해결**을 선택하여 특정 사용자에 대한 상태 정보를 확인합니다. 

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **문제 해결**을 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    **할당** 드롭다운 목록에서 클라이언트 앱, 정책, 업데이트 링 및 등록 제한의 대상 할당을 보도록 선택할 수 있습니다. 또한 이 창에서는 특정 사용자에 대한 디바이스 세부 정보, 앱 보호 상태 및 등록 오류를 제공합니다.

    ![Microsoft 엔드포인트 관리자 관리 센터 - 문제 해결의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    Intune 내 문제 해결에 대한 자세한 내용은 [문제 해결 포털을 사용하여 회사 내 사용자 지원](../help-desk-operators.md)을 참조하세요.

14. 탐색 창에서 **문제 해결 + 지원** > **도움말 및 지원**을 선택하여 도움을 요청합니다. 

    > [!TIP]
    > 이전에 Azure Portal에서 Intune을 사용한 경우에는 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **도움말 및 지원**을 선택하여 Azure Portal에서 위의 세부 정보를 찾을 수 있었습니다.

    IT 관리자 권한으로 **도움말 및 지원** 옵션을 사용하여 Intune에 대한 온라인 지원 티켓을 저장할 뿐만 아니라 솔루션을 검색하고 확인할 수 있습니다. 

    ![Microsoft 엔드포인트 관리자 관리 센터 - 도움말 및 지원의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    지원 티켓을 만들려면 Azure Active Directory의 관리자 역할로 계정이 할당되어야 합니다. 관리자 역할에는 **Intune 관리자**, **글로벌 관리자** 및 **서비스 관리자**가 포함됩니다. 

    자세한 내용은 [Microsoft Intune에 대한 지원을 받는 방법](../get-support.md)을 참조하세요.

15. 탐색 창에서 **문제 해결 + 지원** > **단계별 시나리오**를 선택하여 사용 가능한 Intune 단계별 시나리오를 표시합니다. 

    단계별 시나리오는 하나의 포괄적인 사용 사례를 중심으로 하는 일련의 사용자 지정된 단계입니다. 일반적인 시나리오는 조직에서 관리자, 사용자 또는 디바이스가 수행하는 역할을 기반으로 합니다. 일반적으로 이 역할에는 최상의 사용자 환경 및 보안을 제공하기 위해 신중하게 오케스트레이션된 프로필, 설정, 애플리케이션 및 보안 컨트롤 컬렉션이 필요합니다.

    특정 Intune 시나리오를 구현하는 데 필요한 모든 단계와 리소스에 대해 잘 모르는 경우 단계별 시나리오를 시작점으로 사용할 수 있습니다. 

    ![Microsoft 엔드포인트 관리자 관리 센터 - 단계별 시나리오의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    단계별 시나리오에 대한 자세한 내용은 [단계별 시나리오 개요](~/fundamentals/guided-scenarios-overview.md)를 참조하세요.

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>Microsoft 엔드포인트 관리자 관리 센터 구성

Azure를 사용하면 포털의 보기를 사용자 지정하고 구성할 수 있습니다.

### <a name="change-the-dashboard"></a>대시보드 변경

**대시보드**는 Intune 테넌트의 디바이스 및 클라이언트 앱에 대한 전체 세부 정보를 표시합니다. 대시보드를 통해 Microsoft 엔드포인트 관리자 관리 센터에서 집중적으로 정렬된 보기를 만들 수 있습니다. 일상 작업을 신속하게 시작하고 리소스를 모니터링할 수 있는 작업 영역으로 대시보드를 사용합니다. 예를 들어 프로젝트, 작업 또는 사용자 역할을 기반으로 사용자 지정 대시보드를 빌드합니다. Microsoft 엔드포인트 관리자 관리 센터는 기본 대시보드를 시작점으로 제공합니다. 기본 대시보드를 편집하고, 추가 대시보드를 만들고 사용자 지정하고, 대시보드를 게시 및 공유하여 다른 사용자에게 제공할 수 있습니다. 

   ![Microsoft 엔드포인트 관리자 관리 센터 - 대시보드의 스크린샷](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

현재 대시보드를 수정하려면 **편집**을 선택합니다. 기본 대시보드를 변경하지 않으려는 경우 **새 대시보드**를 만들 수도 있습니다. 새 대시보드를 만들면 타일을 추가하거나 재배열할 수 있는 **타일 갤러리**가 포함된 빈 프라이빗 대시보드가 제공됩니다. 범주 또는 리소스 유형별로 타일을 찾을 수 있습니다. 특정 타일을 검색할 수도 있습니다. **내 대시보드**를 선택하여 기존 사용자 지정 대시보드를 선택합니다.

### <a name="change-the-portal-settings"></a>포털 설정 변경

기본 보기, 테마, 자격 증명 제한 시간 및 언어 및 지역 설정을 선택하여 Microsoft 엔드포인트 관리자 관리 센터를 사용자 지정할 수 있습니다.

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>다음 단계

Microsoft Intune에서 신속하게 실행하려면 먼저 Intune 체험 계정을 설정하여 Intune 빠른 시작을 단계별로 진행합니다.

> [!div class="nextstepaction"]
> [빠른 시작: Microsoft Intune 평가판 체험](free-trial-sign-up.md)
