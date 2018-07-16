---
title: 앱 보호 정책 액세스 작업을 사용하여 선택적으로 데이터 초기화
titleSuffix: Microsoft Intune
description: Microsoft Intune에서 앱 보호 정책 액세스 작업을 사용하여 선택적으로 데이터를 초기화하는 방법에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2cfd426a0ae7165a7aae60a90d104852fd834db6
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909119"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>Intune에서 앱 보호 정책 액세스 작업을 사용하여 선택적으로 데이터 초기화

Intune 앱 보호 정책을 사용하면 최종 사용자가 회사 앱 또는 계정에 액세스하지 못하게 차단하는 설정을 구성할 수 있습니다. 이러한 설정은 무단 해제 장치 및 최소 OS 버전과 같은 사항에 대해 조직에서 설정한 데이터 재배치 및 액세스 요구 사항을 대상으로 합니다.
 
이러한 설정을 사용하여 비준수에 대해 수행할 작업으로 최종 사용자 장치에서 회사의 회사 데이터를 초기화하도록 명시적으로 선택할 수 있습니다. 일부 설정의 경우 액세스 차단 및 다른 지정된 값에 따라 데이터 초기화와 같은 여러 작업을 구성할 수 있습니다.

## <a name="create-an-app-protection-policy-using-access-actions"></a>액세스 작업을 사용하여 앱 보호 정책 만들기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다.  
    Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **모바일 앱** > **앱 보호 정책**을 선택합니다.
4. **정책 추가**(기존 정책을 편집할 수도 있음)를 클릭합니다. 
5. **필요한 설정 구성**을 클릭하여 정책에 대해 구성할 수 있는 설정 목록을 볼 수 있습니다. 
6. **설정** 창에서 아래로 스크롤하면 편집 가능한 테이블이 있는 **액세스 작업**이라는 섹션이 표시됩니다.

    ![Intune 앱 보호 액세스 작업의 스크린샷](./media/apps-selective-wipe-access-actions01.png)

7. **설정**을 선택하고 사용자가 회사 앱에 로그인하기 위해 충족해야 하는 **값**을 입력합니다. 
8. 사용자가 요구 사항을 충족하지 않을 경우 **작업**을 선택합니다. 경우에 따라 단일 설정에 대해 여러 작업을 구성할 수 있습니다. 자세한 내용은 [앱 보호 정책을 만들고 할당하는 방법](app-protection-policies.md)을 참조하세요.

>[!NOTE]
> **장치 모델** 설정을 사용하려면 세미콜론으로 구분된 모델 식별자 목록을 입력합니다. 

## <a name="policy-settings"></a>정책 설정 

앱 보호 정책 설정 테이블에는 **설정**, **값** 및 **작업**에 대한 열이 있습니다.

iOS의 경우 **설정** 드롭다운을 사용하여 다음 설정에 대한 작업을 구성할 수 있습니다.
-  최대 PIN 시도 횟수
-  오프라인 유예 기간
-  무단 해제/루팅된 장치
-  최소 OS 버전
-  최소 앱 버전
-  최소 SDK 버전
-  장치 모델

Android의 경우 **설정** 드롭다운을 사용하여 다음 설정에 대한 작업을 구성할 수 있습니다.
-  최대 PIN 시도 횟수
-  오프라인 유예 기간
-  무단 해제/루팅된 장치
-  최소 OS 버전
-  최소 앱 버전
-  최소 패치 버전
-  장치 제조업체

기본적으로 **액세스용 PIN 필요** 설정이 **예**로 설정된 경우, 테이블에는 **오프라인 유예 기간** 및 **최대 PIN 입력 시도**로 구성된 설정으로 채워진 행이 있습니다.
 
설정을 구성하려면 **설정** 열의 드롭다운에서 설정을 선택합니다. 값을 설정해야 하는 경우 설정을 선택하면 동일한 행의 **값** 열 아래에서 편집 가능한 텍스트 상자가 활성화됩니다. 또한 드롭다운은 설정에 적용할 수 있는 조건부 실행 작업 집합과 함께 **작업** 열 아래에서 활성화됩니다. 

다음 목록은 일반적인 작업 목록을 제공합니다.
-  **액세스 차단** – 최종 사용자가 회사 앱에 액세스하는 것을 차단합니다.
-  **데이터 초기화** – 최종 사용자의 장치에서 회사 데이터를 초기화합니다.
-  **경고** – 최종 사용자에게 경고 메시지로 대화 상자를 제공합니다.

### <a name="additional-settings-and-actions"></a>추가 설정 및 작업 

**최소 OS 버전** 설정과 같은 일부의 경우에는 다른 버전 번호에 따라 적용 가능한 모든 작업을 수행하도록 설정을 구성할 수 있습니다. 

![Intune 앱 보호 액세스 작업의 스크린샷 - 최소 OS 버전](./media/apps-selective-wipe-access-actions05.png)

설정이 완전히 구성되면 행은 읽기 전용 보기에 표시되며 언제든지 편집할 수 있습니다. 또한 행에 **설정** 열의 드롭다운을 사용하여 선택할 수 있습니다. 이미 구성되어 있고 여러 작업을 허용하지 않는 설정은 드롭다운에서 선택할 수 없습니다.

## <a name="next-steps"></a>다음 단계

Intune 앱 보호 정책에 대한 자세한 내용은 다음을 참조하세요.
- [앱 보호 정책을 만들고 할당하는 방법](app-protection-policies.md)
- [iOS 앱 보호 정책 설정](app-protection-policy-settings-ios.md)
- [Microsoft Intune의 Android 앱 보호 정책 설정](app-protection-policy-settings-android.md) 


