---
title: 회사 포털을 사용하여 Intune에 macOS 장치 등록 | Microsoft Docs
description: 회사 포털 앱을 사용하여 Intune에 macOS 장치를 등록하는 방법을 설명합니다.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 3dac9446d7a1097f5be4d0851cd78e8cbb86cc4e
ms.sourcegitcommit: 2198a39ae48beca5fc74316976bc3fc9db363659
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38224764"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>회사 포털 앱을 사용하여 Intune에 macOS 장치 등록

조직의 앱, 데이터 및 리소스에 액세스할 수 있으면 업무를 더 쉽게 수행할 수 있습니다. 조직에서 Intune을 사용하여 [리소스에 대한 액세스를 관리하려면](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md) macOS용 회사 포털 앱을 다운로드해야 합니다. 이 지침은 OS X El Capitan 10.11+의 macOS 장치에 해당됩니다.


1. __Dock__에서 __Safari__를 찾고 새 창을 연 다음 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)를 엽니다.

2. 회사 또는 학교 계정으로 회사 포털 웹 사이트에 로그인합니다.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. 로그인 한 후에 페이지의 왼쪽 위 모퉁이에서 **메뉴**를 클릭하고 **내 장치**를 선택합니다.

   ![웹 포털에 앱을 설치할 수 없다고 표시되고 그 아래에 내 장치 단추가 있는 웹 포털 방문 페이지의 스크린샷](./media/macOS_enroll_001_landing_page.png)

4. __내 장치__ 페이지에 등록된 장치 목록이나 단순히 배너가 표시됩니다. 장치가 이미 등록되어 있는지 또는 macOS가 있는지 여부에 따라 달라집니다. 나열되지 않는 장치를 등록하려면 __장치가 나열되면 여기를 탭하여 식별합니다. 여기를 탭하여 나열되지 않는 장치를 등록할 수도 있습니다.__ 라는 배너를 선택합니다. 등록된 장치가 없으면 배너가 다음 메시지를 표시합니다. **등록된 장치가 없습니다. 여기를 탭하여 이 장치를 등록하세요.**

    ![목록에 없는 장치를 등록하거나 식별되지 않은 장치를 식별하라는 배너 프롬프트 위에 몇 개의 식별되지 않은 장치가 표시된 내 장치 페이지의 스크린샷](./media/macOS_enroll_002_tap_here_banner.png)

5. 회사 포털 앱을 macOS 장치에 다운로드하여 등록을 계속합니다.

    ![사용자에게 macOS 회사 포털 앱을 다운로드하라는 알림입니다. 이 알림에는 단계에 나열된 텍스트가 오른쪽 아래 모서리의 "다운로드"라는 단추 위에 표시됩니다.](./media/macOS_enroll_IWP_CP_app_notice.png)

6. Mac에서 다운로드한 **CompanyPortal.pkg**가 열기에 안전한지 검사합니다. 설치 관리자를 열고 설치 프로세스를 진행합니다.

7. 설치 관리자를 마치면 **응용 프로그램** 폴더 또는 **실행 패드**를 연 다음 **회사 포털**을 엽니다.

8. Mac에서 **"CompanyPortal"은 인터넷에서 다운로드한 응용 프로그램입니다. 여시겠습니까?** 라는 메시지를 표시합니다. **열기**를 클릭합니다.

   > [!NOTE]
   > 장치가 조직의 리소스에 액세스해도 안전한지 확인하기 위해 Intune에서 컴퓨터에 액세스해야 합니다. 컴퓨터에서 회사 포털 앱이 열리지 않는 경우 [Gatekeeper를 사용하지 않도록 설정](https://support.apple.com/HT202491)한 다음 앱을 열어 보세요.

9. 회사 포털 앱의 첫 화면에는 회사 포털 웹 사이트에 로그인할 때 사용하는 것과 동일한 회사 또는 학교 계정으로 **로그인**하라는 메시지가 표시됩니다.

10. 회사 포털에서 사용자의 계정 정보를 확인한 다음 **장치 등록** 및 **장치 준수** 상태를 표시합니다. 회사에서 Mac을 사용해도 안전한지 확인하기 위해 수행하는 작업이 있음을 알리는 노란색 삼각형이 나타납니다. **시작**을 클릭하여 [장치를 관리에 등록합니다](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).

11. Mac에서 관리에 등록을 시작합니다. 그 동안 컴퓨터의 로그인 정보를 제공하라는 메시지가 표시될 수 있습니다. 등록하는 데는 몇 분 정도 걸릴 수 있습니다. 그 동안 컴퓨터에 다른 작업을 수행할 수 있습니다. 회사 액세스 설정이 완료되면 알려드리겠다는 메시지가 표시됩니다.

여전히 도움이 필요하세요? 회사 지원팀과 확인하세요. 연락처 정보는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com#HelpDeskDialog)에서 찾을 수 있습니다.
