---
title: Microsoft Intune에서 정책 시작 - Azure | Microsoft Docs
description: 회사 데이터를 보호하고 회사 리소스에 액세스하기 위해 최종 사용자가 사용하는 장치를 관리하는 정책을 만듭니다. 그런 다음, 그룹에 정책을 할당합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7fa1b596a1800971919cfc0ab3e94d2d16ec328
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271527"
---
# <a name="get-started-with-creating-policies"></a>정책 만들기 시작

Intune 정책은 장치를 등록하고 회사 정책을 준수하도록 하는 데 좋은 방법입니다. 준수 정책은 회사 소유 키오스크와 같은 특수 장치 유형과 개인(Bring Your Own) 장치, 태블릿 및 사용자가 지정되지 않은 장치를 관리하는 데 도움이 됩니다.

![데이터가 적은 준수 대시보드](/intune/media/generic-compliance-dashboard.png)

모바일 장치는 다음과 같은 준수 정책을 사용하여 관리할 수 있습니다.

* Intune에 사용자가 등록하는 장치 수 조정
* 장치 수준 암호화, 암호 길이 및 카메라 사용과 같은 장치 설정 관리
* 앱, 이메일 프로필, VPN 프로필 등을 제공
* 보안 준수 정책에 대한 장치 수준 기준 평가

준수 정책은 iOS, Android, Windows 등과 같은 각 플랫폼에 대해 생성됩니다. 이 연습에서는 iOS를 사용합니다. iOS 장치에 사용할 수 있는 정책은 다음과 같습니다.

* PIN 또는 암호 구성
* 장치 암호화
* 탈옥 장치
* 전자 메일 프로필
* 최소 OS 버전
* 최대 OS 버전

## <a name="create-a-policy"></a>정책 만들기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치 준수** > **정책** > **정책 만들기**를 선택합니다.
4. 정책 **이름** 및 **설명**을 입력합니다. 
5. **플랫폼**에서 **iOS**를 선택합니다.
6. **설정**에서 **시스템 보안**을 선택한 다음, **모바일 장치의 잠금을 해제하는 데 암호 필요**를 **필요**로 설정합니다. 

    다음과 같은 다른 규칙도 설정할 수 있습니다. 
    - **최소 암호 길이**
    - **필수 암호 유형**
    - **암호의 영숫자가 아닌 문자 수**
    
    정책 설정이 완료되면 **확인**을 선택합니다.
  
7. **정책 만들기**로 돌아가서 **만들기**를 선택합니다. 이 단계에서는 정책을 만들고 **장치 준수** > **정책**에 정책을 나열합니다.
8. 새 정책을 선택하고 **할당**을 선택합니다. Azure AD(Active Directory) 보안 그룹을 포함하거나 제외할 수 있습니다.
선택된 그룹을 선택하면 기존 Azure AD 보안 그룹이 표시됩니다. 이 정책을 적용할 사용자 그룹을 선택한 다음 **저장**을 선택하여 정책을 사용자에게 배포합니다.

새 회사 정책을 준수하기 위해 몇 분 후에, 등록된 장치에서 업데이트된 암호를 묻는 메시지가 표시됩니다. **iOS용 회사 포털 앱**에서 업데이트를 수동으로 확인할 수 있습니다. 회사 포털 앱을 열고 장치 이름을 선택한 다음, **동기화**를 선택합니다.

> [!NOTE]
> 동적 장치 그룹에 적용되는 새 정책은 그룹의 모든 장치에 적용하는 데 최대 8시간이 걸릴 수 있습니다.

## <a name="next-steps"></a>다음 단계

[장치 등록 시작](get-started-enroll.md) - iOS 장치의 전체 등록 과정을 안내하여 등록 과정을 알아봅니다.

## <a name="learn-more"></a>자세한 정보

* [Intune 장치 준수 정책 모니터링](compliance-policy-monitor.md)
* [Intune에서 조건부 액세스 정책을 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)
