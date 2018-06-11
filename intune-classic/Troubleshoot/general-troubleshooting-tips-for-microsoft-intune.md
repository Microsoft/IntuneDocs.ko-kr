---
title: 일반 문제 해결 팁
description: Intune 문제를 해결하는 데 도움이 되는 일반 리소스입니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/08/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bbcfa2de4b2d6ef7bff481817a289f56e746ee7f
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34718032"
---
# <a name="general-troubleshooting-tips-for-microsoft-intune"></a>Microsoft Intune에 대한 일반적인 문제 해결 팁

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune을 배포한 후에 구성이나 클라이언트 장치에서 문제가 발생할 수 있습니다. 다음 리소스를 사용하면 문제를 해결하기 위해 문제의 원인을 파악할 수 있습니다.

> [!NOTE]
> 지원 요청을 만들거나 기존 요청을 보려면 [Azure 도움말 + 지원](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) 페이지를 방문하세요. 지원 옵션에 대한 자세한 내용은 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)을 참조하세요.

## <a name="define-the-problem"></a>문제 정의

-   동작은 무엇인가요?

-   누구에게 이 동작이 발생하며 어떤 플랫폼과 장치에서 발생하나요?

-   이전에 장치가 제대로 작동하지 않았나요?

-   Intune 또는 장치 구성을 어떻게 변경했나요?

-   구성 변경 이외에 작업 환경에 대한 다른 변경을 수행했나요?

-   이 문제가 얼마나 자주 발생하나요? 산발적인가요, 아니면 일관성 있게 발생하나요?

-   사용자에게 인증 문제가 발생할 수 있나요? 가능성이 있는 경우 사용자가 Azure Active Directory를 사용하는 다른 서비스에 로그인할 수 있는지 확인합니다. 또한 사용자가 다른 장치에서 로그인할 수 있는지 확인합니다.

-   서비스 상태를 확인했나요? 또한 [Office 365 관리 포털](https://portal.office.com/Admin/Default.aspx)에서 Intune 서비스 상태를 모니터링할 수 있습니다. 왼쪽 창에서 **서비스 상태**를 선택합니다.

## <a name="collect-available-data"></a>사용 가능한 데이터 수집

- 다음 리소스를 통해 장치 로그를 수집하는 방법을 파악할 수 있습니다.
  - [USB 케이블을 사용하여 IT 관리자에게 Android 진단 데이터 로그 보내기](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [메일을 사용하여 IT 관리자에게 Android 진단 데이터 로그 보내기](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [IT 관리자에게 Android 등록 오류 보내기](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)
  - [IT 관리자에게 iOS 등록 오류 보내기](/intune-user-help/send-errors-to-your-it-admin-ios)

- 관리 콘솔 데이터. 예를 들어 정책 구현 문제의 경우 [Microsoft Intune에서 그룹을 사용하여 사용자 및 장치 관리](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)에 설명된 대로 의도한 정책 및 해당 정책의 상태를 검사합니다.

## <a name="research-the-solution"></a>솔루션 연구

-   웹에서 해결 방법 검색. 예를 들어 0x80073CF0 오류가 발생하는 경우 웹에서 **technet intune 0x80073cf0**을 검색하면 [Microsoft Intune에서 앱 배포 문제 해결](troubleshoot-app-deployment-problems-in-microsoft-intune.md) 문서를 찾을 수 있습니다. 이 문서에서는 해당 오류를 해결하기 위한 제안 사항을 제공합니다.

-   [Intune TechNet 포럼](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)에서 답변 검색.  이 문제가 이전에 해결되지 않은 경우 질문을 게시하여 커뮤니티의 제안 사항을 확인합니다.

-   지원 요청 시작. 문제를 정의하고 사용할 수 있는 데이터를 수집하고 나면 Intune 지원에서 더욱 효율적으로 문제 해결을 지원할 수 있습니다.

    지원 요청을 만들려면 [Office 365 관리 센터를 방문](https://portal.office.com/admin/default.aspx)합니다. 지원 옵션에 대한 자세한 내용은 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)을 참조하세요.

## <a name="find-community-resources"></a>커뮤니티 리소스 찾기
이러한 커뮤니티 리소스에서 기타 유용한 정보를 찾을 수 있습니다.

-   [Microsoft Intune 활용 안내서](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx)에는 Intune 구성, 유지 관리 및 문제 해결에 도움이 되는 다양한 리소스의 링크가 포함되어 있습니다.

-   [Intune 블로그](http://blogs.technet.com/b/windowsintune/)

-   [Twitter에서 Intune 팔로우](https://twitter.com/MSIntune)

-   [Intune 포럼](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### <a name="next-steps"></a>다음 단계
아래 항목에는 특정 문제에 대한 문제 해결 도움말이 있습니다. 정보가 도움이 되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)에 설명된 대로 Microsoft 지원에 문의하세요.

[Microsoft Intune에서 Endpoint Protection 문제 해결](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Microsoft Intune 관련 회사 리소스 액세스 문제 해결](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Microsoft Intune에서 앱 배포 문제 해결](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Intune에서 장치 등록 문제 해결](troubleshoot-device-enrollment-in-intune.md)

[Microsoft Intune의 정책 문제 해결](troubleshoot-policies-in-microsoft-intune.md)

[Microsoft Intune에서 클라이언트 설정 문제 해결](troubleshoot-client-setup-in-microsoft-intune.md)

[Microsoft Intune에서 소프트웨어 업데이트 문제 해결](troubleshoot-software-updates-in-microsoft-intune.md)
