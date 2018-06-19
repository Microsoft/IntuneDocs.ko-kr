---
title: Microsoft Intune에서 Exchange 조건부 액세스 모니터링
titlesuffix: ''
description: Intune Azure Portal을 사용하여 온-프레미스 Exchange 및 Exchange Online에 대한 조건부 액세스 준수를 모니터링합니다.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 932dfe32c6df5741615d9db9f303aaee7785d3a3
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2018
ms.locfileid: "29775361"
---
# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune"></a>Intune에서 온-프레미스 Exchange 및 Exchange Online에 대한 조건부 액세스 준수 모니터링

Intune 1704 릴리스부터는 관리자가 온-프레미스 Exchange Connector 또는 Intune 서비스 간 커넥터(Exchange Online 커넥터)를 통해 Intune과 동기화되는 Exchange ActiveSync 장치 레코드 관련 보고 정보를 확인할 수 있습니다. 조건부 액세스 준수 보고 기능은 다음과 같은 여러 동기화 상태가 설정된 장치의 요약 정보를 제공합니다.

-   **허용**

-   **차단**

-   **격리**

## <a name="to-monitor-conditional-access-compliance"></a>조건부 액세스 준수를 모니터링하려면

1.  [Azure Portal](https://portal.azure.com/)로 이동한 다음 Intune 자격 증명을 사용하여 로그인합니다.

2.  정상적으로 로그인되면 **Azure 대시보드**가 표시됩니다.

3.  왼쪽 메뉴에서 **모든 서비스**를 선택한 다음, 텍스트 상자 필터에 **Intune**을 입력합니다.

4.  **Intune**을 선택하면 **Intune 대시보드**가 표시됩니다.

5.  **조건부 액세스**와 **개요**를 차례로 선택합니다.

6.  차트에서 **허용**, **차단** 또는 **격리**의 세 영역 중 하나를 선택하면 조건부 액세스 준수 보고 내용을 확인할 수 있습니다.

    ![조건부 액세스 대시보드의 이미지](./media/CA-reporting-intune-1.png)

세 영역 중 하나를 선택하면 허용, 차단 또는 격리 중인 장치에 대한 추가 세부 정보를 확인할 수 있습니다.

특정 장치로 드릴다운하여 더 자세한 정보를 확인할 수도 있습니다. 예를 들어 다음의 이미지에서 선택된 장치는 차단된 상태입니다. Intune에서는 조건부 액세스 준수 보고서 창에서 회사 데이터를 제거할 수 있는 옵션을 제공합니다.

![조건부 액세스 장치 세부 보고 이미지](./media/CA-reporting-intune-3.png)

장치 세부 정보 창에서 다음과 같은 추가 정보를 확인할 수 있습니다.

-   **개요:** OS 버전, 장치 모델, 소유권, 일련 번호, 장치 제조업체, 전화번호, 마지막 장치 체크 인 시간 등의 장치 속성을 확인할 수 있습니다.

-   **속성:** 장치 소유권(개인 또는 회사)을 설정할 수 있습니다.

-   **하드웨어:** 개요에 표시되는 정보와 함께 저장소 세부 정보(총 공간 및 사용 가능한 공간), 시스템 엔클로저, 네트워크 세부 정보, 네트워크 서비스 및 추가 조건부 액세스 차단 세부 정보도 제공됩니다.

-   **검색된 앱:** 장치에 설치된 모든 응용 프로그램이 표시됩니다. 설치된 앱의 목록을 .CSV 형식으로 내보낼 수도 있습니다.

-   **준수:** 모든 장치 준수 정책 세부 정보가 표시됩니다.

-   **장치 구성:** 모든 장치 구성 세부 정보가 표시됩니다.

-   **Exchange 액세스:** 여기서는 조건부 액세스 정책을 적용한 후의 장치 상태에 대해 자세히 확인할 수 있습니다.
