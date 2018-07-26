---
title: 앱 설치 문제 해결
titlesuffix: Microsoft Intune
description: Microsoft Intune 문제 해결 창을 사용하면 앱 설치 문제 해결에 도움이 될 수 있습니다.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: c1c2a37103f8fedc09a70b4387aae3f472dfb636
ms.sourcegitcommit: dc8b6f802cca7895a19ec38bec283d4b3150d213
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39138682"
---
# <a name="troubleshoot-app-installation-issues"></a>앱 설치 문제 해결

Microsoft Intune MDM 관리 장치에서 앱 설치에 실패하는 경우도 있습니다. 이러한 앱 설치에 실패할 경우, 실패 이유를 파악하거나 문제를 해결하기 어려울 수 있습니다. Microsoft Intune은 지원 센터 운영자 및 Intune 관리자가 사용자 도움 요청을 해결하기 위해 앱 정보를 볼 수 있는 앱 설치 실패 세부 정보를 제공합니다. Intune 내의 문제 해결 창에서는 사용자 장치의 관리되는 앱에 대한 세부 정보를 비롯하여 실패 세부 정보를 제공합니다. **관리되는 앱** 창에서 개별 장치 아래에는 앱의 종단 간 수명 주기에 대한 세부 정보가 제공됩니다. 앱이 만들어지거나 수정되거나 대상이 지정되거나 장치에 제공되는 경우 등에 설치 문제를 볼 수 있습니다. 

## <a name="to-review-app-troubleshooting-details"></a>앱 문제 해결 세부 정보를 검토하려면

Intune은 특정 사용자 장치에 설치된 앱을 기반으로 앱 문제 해결 세부 정보를 제공합니다.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **문제 해결**을 선택합니다.
4. **사용자 선택**을 클릭하여 문제를 해결할 사용자를 선택합니다. **사용자 선택** 창이 표시됩니다.
5. 이름 또는 이메일 주소를 입력하여 사용자를 선택합니다. 창 아래쪽에서 **선택**을 클릭합니다. **문제 해결** 창에 사용자에 대한 문제 해결 정보가 표시됩니다. 
6. **장치** 목록에서 문제를 해결할 장치를 선택합니다.
    ![Intune 문제 해결 창.](media/troubleshoot-app-install-01.png)
7. 선택한 장치 창에서 **관리되는 앱**을 선택합니다. 관리되는 앱 목록이 표시됩니다.
    ![Intune에서 관리되는 특정 장치의 세부 정보.](media/troubleshoot-app-install-02.png)
8. 목록에서 **설치 상태**에 실패가 표시된 앱을 선택합니다.
    ![설치 실패 세부 정보를 표시하는 선택된 앱.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > 같은 앱을 여러 그룹에 할당하되, 앱에 대해 의도한 동작(의도)을 각각 다르게 할 수 있습니다. 예를 들어 앱 할당 중에 사용자에 대해 앱이 제외된 경우 앱에 대해 확인된 의도에 **제외**가 표시됩니다. 자세한 내용은 [앱 의도 간의 충돌을 해결하는 방법](apps-deploy.md#how-conflicts-between-app-intents-are-resolved)을 참조하세요.<br><br>
    > 현재 Intune은 OS 플랫폼을 기반으로 앱을 필터링하지 않습니다.

앱 설치 오류 세부 정보에 문제가 표시됩니다. 이러한 세부 정보를 사용하여 문제를 해결하기 위해 수행할 최상의 조치를 결정할 수 있습니다. 앱 설치 문제 해결에 대한 자세한 내용은 [Error Codes For Troubleshooting App Installation Issues](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues)(앱 설치 문제 해결을 위한 오류 코드)를 참조하세요.

> [!Note]  
> 브라우저를 [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting)으로 전환하여 **문제 해결** 창에 액세스할 수도 있습니다.

## <a name="next-steps"></a>다음 단계

- 추가 Intune 문제 해결 정보는 [문제 해결 포털을 사용하여 회사 내 사용자 지원](help-desk-operators.md)을 참조하세요. 
- 알려진 Microsoft Intune 문제를 알아봅니다. 자세한 내용은 [알려진 Microsoft Intune 문제](known-issues.md)를 참조하세요.
- 추가 도움이 필요하십니까? [Microsoft Intune에 대한 지원을 받는 방법](get-support.md)을 참조하십시오.
