---
title: Intune에서 iOS 장치 제거 | Microsoft Docs
description: Intune에서 iOS 장치 제거 방법 설명
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 0a90cace32edb33293ba0b0b89d272465ea32418
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34547491"
---
# <a name="remove-your-ios-device-from-intune"></a>Intune에서 iOS 장치 제거

Intune에서 iOS 장치를 제거하면 장치가 더 이상 회사 리소스에 액세스할 수 없으며 Intune을 통해 관리되지 않습니다.


## <a name="removing-the-device-from-my-devices"></a>내 장치에서 장치 제거하기

Intune에서 장치를 제거하려면 다음 단계를 따르거나 이 비디오를 시청하세요.


1.  회사 포털 앱에서 **장치**를 탭합니다. 등록을 취소하려는 장치를 선택합니다. **장치**를 탭할 때 하나의 장치만 있는 경우 장치 세부 정보 화면으로 직접 이동합니다.

2.  **이름 바꾸기** 옆의 줄임표 단추 > **장치 제거** > **제거**를 차례로 탭합니다.  

    |![사용자가 제거를 클릭한 후 옵션을 표시하는 회사 포털 앱 장치 화면의 스크린샷입니다. "장치 제거", "출하 시 설정으로 리셋" 및 "취소" 단추를 표시합니다.](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![사용자가 장치 제거 단추를 클릭한 후 옵션을 표시하는 회사 포털 앱 장치 화면의 스크린샷입니다. 빨간색으로 강조 표시된 "제거" 단추, 파란색으로 강조 표시된 "자세히 알아보기" 단추 및 "취소" 단추를 표시합니다.](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


  Intune에서 장치를 등록 취소하면 다음과 같은 일이 발생합니다.

  -   장치가 더 이상 회사 포털에 나타나지 않습니다.

  -   더 이상 회사 포털에서 앱을 설치할 수 없습니다.

  -   장치를 추가할 때 장치에서 변경된 모든 설정(예: 카메라 사용 안 함 또는 특정 암호 길이 요구)이 더 이상 적용되지 않습니다.

  -   장치에서 더 이상 일부 회사 리소스(예: 파일 공유 또는 내부 웹 사이트)에 액세스하지 못할 수 있습니다.

  -   장치에서 더 이상 회사 앱 및 회사 데이터를 사용할 수 없습니다.

  -   더 이상 Wi-Fi 또는 VPN(가상 사설망)을 사용하여 회사 네트워크에 연결할 수 없습니다.

  -   장치에서 회사 전자 메일 프로필이 제거됩니다.

  -   메일용으로만 구성된 장치는 회사 포털 앱이나 웹 사이트에 더 이상 나타나지 않습니다.
  
  -   앱이 제거됩니다. 회사 앱 데이터가 제거됩니다.

## <a name="removing-data-collected-by-the-company-portal-app"></a>회사 포털 앱에서 수집한 데이터 제거하기

회사 포털이 장치에 로컬 데이터를 저장하는 세 장소가 있습니다.

-   **정보 로그**: 회사 포털에서 장치를 제거하는 경우 앱이 얼마나 오래 열려 있었는지 또는 크래시되었는지 등 Microsoft에서 수집하는 표준 앱 활동 데이터가 자동으로 지워집니다.

-   **Apple 분석**: Apple에서 수집하는 표준 앱 크래시 활동 데이터입니다. 이 정보는 장치를 출하 시 설정으로 다시 설정해야만 제거할 수 있습니다. 이렇게 하면 장치에서 모든 개인 정보를 지웁니다. 이를 수행하려면 **설정** > **일반** > **다시 설정** > **모든 콘텐츠 및 설정 지우기**를 차례로 엽니다.

-   **키 집합**: 사용자 장치는 키 집합에 로그인을 위해 사용된 암호 및 기타 정보를 저장합니다. Microsoft 앱은 Microsoft Outlook 및 Microsoft Authenticator를 포함해 장치에 있는 모든 Microsoft 개발 앱에서 로그인 정보를 공유합니다. Apple 분석처럼 이 정보는 장치를 출하 시 설정으로 다시 설정해야만 제거할 수 있습니다. 이렇게 하면 장치에서 모든 개인 정보를 지웁니다. 이를 수행하려면 **설정** > **일반** > **다시 설정** > **모든 콘텐츠 및 설정 지우기**를 차례로 엽니다.


여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com#HelpDeskDialog)를 참조하세요.
