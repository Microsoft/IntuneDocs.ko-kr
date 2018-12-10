---
title: 빠른 시작 - 앱 보호 정책 만들기 및 할당
titlesuffix: Microsoft Intune
description: 이 빠른 시작에서는 Microsoft Intune을 사용하여 앱 보호 정책을 만들고 할당 및 지정합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2ae378550a75f756390053e44eb4fbd04f665612
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179089"
---
# <a name="quickstart-create-and-assign-an-app-protection-policy"></a>빠른 시작: 앱 보호 정책 만들기 및 할당

이 빠른 시작에서는 Intune을 사용하여 최종 사용자 디바이스의 클라이언트 앱에 앱 보호 정책을 만들고 할당합니다. Intune은 앱 보호 정책을 사용하여 앱이 조직의 데이터 보호 요구 사항을 충족하는지 확인합니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건

- 이 빠른 시작을 완료하려면 [사용자 만들기](quickstart-create-user.md), [그룹 만들기](quickstart-create-group.md), [디바이스 등록](quickstart-setup-auto-enrollment.md) 및 [앱 추가 및 할당](quickstart-add-assign-app.md)을 해야 합니다.

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 [글로벌 관리자 또는 Intune 서비스 관리자](users-add.md#types-of-administrators)로 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="create-an-app-protection-policy"></a>앱 보호 정책 만들기

다음 단계에 따라 앱 보호 정책을 만듭니다.

1. [Intune](https://aka.ms/intuneportal)에서 **클라이언트 앱** > **앱 보호 정책** > **정책 만들기**를 선택합니다. 
2. 다음 세부 정보를 입력하세요. 

    - **이름**: *Windows 10 콘텐츠 보호*
    - **설명**: *이 정책과 연결된 사용자는 할당된 앱과 디바이스의 다른 비관리 앱 간의 콘텐츠를 잘라내거나 복사 또는 붙여넣을 수 없습니다.*
    - **플랫폼**: *Windows 10*
    - **등록 상태**: *등록*

3. **보호되는 앱**을 선택하여 이 정책을 준수해야 하는 앱을 선택합니다.
4. **앱 추가**를 클릭합니다.
5. **권장 앱** 아래에서 **Word Mobile**을 선택합니다.
5. **확인** > **확인**을 클릭합니다. 
6. **필요한 설정**을 선택하여 앱을 구성합니다.
7. **재정의 허용**을 클릭하여 Windows Information Protection 모드를 설정합니다. 이 옵션을 선택하면 엔터프라이즈 데이터가 보호된 앱에서 벗어나는 것을 차단합니다.
8. **확인** > **만들기**를 클릭합니다.

이제 Intune에서 앱 보호 정책이 표시됩니다.

### <a name="assign-the-app-protection-policy"></a>앱 보호 정책 할당

Intune에서 앱 보호 정책을 만든 후에는 그룹에 할당할 수 있습니다. 

다음 단계에 따라 앱 보호 정책을 할당합니다.

1.  [Intune](https://aka.ms/intuneportal)에서 **Intune** > **클라이언트 앱** > **보호 정책**을 선택합니다. 
2.  이전에 만든 앱 보호 정책을 선택합니다. 이 빠른 시작에서 정책은 **Windows 10 콘텐츠 보호**입니다.
3.  **할당**을 선택합니다.
4.  **포함** 탭에서 **포함할 그룹 선택**을 클릭합니다.
5.  포함할 그룹으로 **Contoso 테스터**를 선택합니다.
6.  **선택**을 클릭합니다. 

이제 앱 보호 정책을 할당했습니다.

> [!NOTE]
> 앱 보호 정책은 디바이스가 포함된 그룹이 아닌 사용자가 포함된 그룹에만 적용될 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 앱 보호 정책을 만들고 할당했습니다. 이 정책이 할당된 앱의 사용자는 할당된 앱과 디바이스의 다른 비관리 앱 간의 콘텐츠를 잘라내거나 복사 또는 붙여넣을 수 없습니다. 이 유형의 보호는 조직의 데이터를 보호하는 데 도움이 됩니다. Intune의 앱 보호 정책에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

다음 Intune 빠른 시작을 진행하기 위해서는 아래 빠른 시작 링크를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: 사용자 지정 역할 만들기 및 할당](quickstart-create-custom-role.md)
