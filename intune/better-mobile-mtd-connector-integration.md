---
title: Intune과 Better Mobile 통합 설정
titleSuffix: Intune on Azure
description: Intune과 Better Mobile 커넥터 통합
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 7/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.openlocfilehash: 5aad0e4aa0f3377c0d46f241d92712d81e4cfbd6
ms.sourcegitcommit: 973a06f4a35b74314fece2bae17dd6885b4211c3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42823211"
---
# <a name="integrate-better-mobile-with-intune"></a>Intune과 Better Mobile 통합

Intune과 Better Mobile Threat Defense 솔루션을 통합하려면 다음 단계를 완료하세요.

## <a name="before-you-begin"></a>시작하기 전에

> [!NOTE]
> 다음 단계는 [Better Mobile 관리 콘솔](https://aad.bmobi.net)에서 수행해야 합니다.

Intune과 Better Mobile을 통합하는 과정을 시작하기 전에 다음 항목이 있는지 확인합니다.

-   Microsoft Intune 구독

-   다음 권한을 부여할 Azure Active Directory 관리자 자격 증명

    -   로그인 및 사용자 프로필 읽기

    -   로그인한 사용자로 디렉터리에 액세스

    -   디렉터리 데이터 읽기

    -   Intune에 장치 정보 보내기

-   Better Mobile 관리 콘솔에 액세스하기 위한 관리자 자격 증명

### <a name="better-mobile-app-authorization"></a>Better Mobile 앱 권한 부여

Better Mobile 앱 권한 부여 프로세스는 다음과 같습니다.

-   Better Mobile 서비스에서 장치 상태와 관련된 정보를 Intune으로 다시 전달하도록 허용합니다.

-   Better Mobile은 Azure Active Directory 등록 그룹 멤버 자격과 동기화하여 해당 장치의 데이터베이스를 채웁니다.

-   Better Mobile 관리 콘솔에서 Azure Active Directory SSO(Single Sign On)를 사용하도록 허용합니다.

-   Better Mobile 앱에서 Azure Active Directory SSO를 사용하여 로그인하도록 허용합니다.

## <a name="to-set-up-better-mobile-integration"></a>Better Mobile 통합을 설정하려면

1. [Better Mobile 관리 콘솔](https://aad.bmobi.net)로 이동하여 자격 증명으로 로그인합니다.
2. **통합** > **EMM/MDM** > **계정 추가**를 선택합니다.

     ![Better Mobile 관리 콘솔](media/better_mobile_console.png)
 
3. **Intune**을 선택합니다.
4. **계정 이름** 옆에 설명자를 입력합니다. 
5. **Microsoft 로그인** 창에 Intune 자격 증명을 입력합니다.
6. **요청된 권한** 창에서 **수락**을 선택합니다.
7. Better Mobile이 장치를 동기화할 Azure Active Directory 보안 그룹을 검색하고 목록에서 선택합니다. 그런 다음 **계속**을 선택합니다.
8. **완료**를 선택합니다.
9. **계정 추가** 페이지가 다시 나타납니다. 페이지를 닫습니다. 

## <a name="next-steps"></a>다음 단계

-   [Better Mobile 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)