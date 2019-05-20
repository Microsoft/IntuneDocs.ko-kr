---
title: 앱에서 회사 데이터만 초기화하는 방법
titleSuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 Intune 관리 앱에서 회사 데이터만 선택적으로 초기화하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/24/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83cc1f43faba1ee98bde680b1ff2b74c78ff65e4
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389498"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Intune 관리 앱에서 회사 데이터만 초기화하는 방법

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

디바이스를 분실하거나 도난당한 경우, 또는 직원이 퇴사하는 경우, 디바이스에서 업무용 앱 데이터가 확실히 제거되도록 해야 합니다. 하지만 디바이스에서 개인 데이터(특히, 직원 소유의 디바이스인 경우)를 제거하지 말아야 하는 경우가 있습니다.

>[!NOTE]
> 현재 Intune 관리 앱에서 회사 데이터 초기화가 지원되는 플랫폼은 iOS, Android 및 Windows 10 플랫폼뿐입니다. Intune 관리 앱은 Intune APP SDK를 포함하는 애플리케이션이며 조직에 대한 사용이 허가된 사용자 계정이 있습니다. 애플리케이션 보호 정책의 배포는 앱 선택적 초기화를 활성화하는 데 필요하지 않습니다.

회사 앱 데이터를 선택적으로 제거하려면 이 항목의 단계를 사용하여 초기화 요청을 만듭니다. 요청이 완료되고 나면, 다음 번에 디바이스에서 앱을 실행할 때 회사 데이터가 앱에서 제거됩니다. 삭제 요청을 만드는 것 외에도 APP(애플리케이션 보호 정책) 액세스 설정 조건이 충족되지 않으면 조직의 데이터를 선택적으로 지우는 작업을 새 작업으로 구성할 수 있습니다. 이 기능을 사용하면 미리 구성된 기준에 따라 애플리케이션에서 중요한 조직 데이터를 자동으로 보호하고 제거할 수 있습니다.

>[!IMPORTANT]
> 앱에서 기본 주소록에 직접 동기화된 연락처가 제거됩니다. 기본 주소록에서 다른 외부 소스에 동기화된 연락처는 초기화할 수 없습니다. 현재 Microsoft Outlook 앱에만 적용됩니다.

## <a name="deployed-wip-policies-without-user-enrollment"></a>사용자 등록 없이 배포된 WIP 정책
WIP(Windows Information Protection) 정책은 MDM 사용자가 Windows 10 디바이스를 등록하지 않고 배포할 수 있습니다. 이 구성을 사용하면 회사는 WIP 구성을 기반으로 회사 문서를 보호할 수 있는 한편 사용자는 자신의 Windows 디바이스를 관리할 수 있습니다. 문서가 WIP 정책으로 보호되면 Intune 관리자는 보호되는 데이터를 선택적으로 초기화할 수 있습니다. 사용자 및 디바이스를 선택하고 초기화 요청을 보내면 WIP 정책을 통해 보호된 모든 데이터를 사용할 수 없게 됩니다. Azure Portal의 Intune에서 **클라이언트 앱** > **앱 선택적 초기화**를 선택합니다. 자세한 내용은 [Intune을 사용하여 WIP(Windows Information Protection) 앱 보호 정책 만들기 및 배포](windows-information-protection-policy-create.md)를 참조하세요.

## <a name="create-a-wipe-request"></a>초기화 요청 만들기

1.  [Azure 포털](https://portal.azure.com)에 로그인합니다.

2.  **모든 서비스**를 선택하고 필터 텍스트 상자에 **Intune**을 입력하고 **Intune**을 선택합니다. Intune 창이 열리면 **클라이언트 앱** 창을 선택합니다.

    ![Microsoft Intune 창 스크린샷](./media/apps-selective-wipe01.png)

3.  **클라이언트 앱 창**에서 **앱 선택적 초기화**를 선택합니다.

4.  **새 초기화 요청**을 선택합니다. **새 초기화 요청** 창이 열립니다.

    ![새 초기화 요청 창의 스크린샷](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  사용자를 선택한 다음, **선택**을 선택하여 초기화할 앱 데이터의 사용자를 선택합니다.

6.  다음으로 **새 초기화 요청** 창에서 **디바이스**를 선택합니다. 선택한 사용자와 연결된 모든 디바이스를 나열하고 디바이스 이름(사용자가 정의한 이름) 및 디바이스 유형, 디바이스 플랫폼의 두 열도 제공하는 **디바이스 선택** 창이 열립니다. 초기화하려는 디바이스를 선택합니다.

7.  이제 **새 초기화 요청** 창으로 다시 전환됩니다. 초기화 요청을 수행하려면 **확인**을 클릭합니다.

서비스에서 디바이스의 각 보호된 앱 및 초기화 요청과 연결된 사용자에 대해 별도의 초기화 요청을 만들고 추적합니다.

## <a name="monitor-your-wipe-requests"></a>초기화 요청 모니터링

초기화 요청의 전반적인 상태를 표시하고, 보류 중인 요청 및 오류의 수가 포함된 요약된 보고서를 생성할 수 있습니다. 세부 정보를 확인하려면 다음 단계를 따릅니다.

1.  **클라이언트 앱 - 앱 선택적 초기화** 창에서 사용자별로 그룹화된 요청 목록을 확인할 수 있습니다. 시스템에서는 디바이스에서 실행 중인 각각의 보호된 앱에 대해 초기화 요청을 생성하므로 한 사용자에 대해 여러 요청이 표시될 수 있습니다. 상태를 통해 초기화 요청이 **보류 중**인지, **실패**했는지 아니면 **성공**했는지 확인할 수 있습니다.

    ![앱 선택적 초기화 창의 초기화 요청 상태 스크린샷](./media/wipe-request-status-1.png)

또한 디바이스 이름과 디바이스 유형을 볼 수 있습니다. 이는 보고서를 읽을 때 유용합니다.

>[!IMPORTANT]
> 초기화하려면 사용자가 앱을 열어야 하며 초기화에는 요청 후 최대 30분 걸릴 수 있습니다.

## <a name="delete-a-wipe-request"></a>초기화 요청 삭제

보류 중 상태의 초기화는 수동으로 삭제할 때까지 표시됩니다. 초기화 요청을 수동으로 삭제하려면

1.  **클라이언트 앱 - 앱 선택적 초기화** 창에서 다음을 수행합니다.

2.  목록에서 삭제하려는 초기화 요청을 마우스 오른쪽 단추로 클릭하고 **초기화 요청 삭제**를 선택합니다.

    ![앱 선택적 초기화 창의 초기화 요청 목록 스크린샷](./media/delete-wipe-request.png)

3.  삭제를 확인하라는 메시지가 표시되면 **예** 또는 **아니요**를 선택하고 **확인**을 클릭합니다.

### <a name="see-also"></a>참고 항목
[앱 보호 정책이란?](app-protection-policy.md)

[앱 관리란?](app-management.md)
