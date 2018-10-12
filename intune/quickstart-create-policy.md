---
title: '빠른 시작: Windows 10 장치에 대한 장치 준수 정책 추가'
description: 이 빠른 시작을 사용하여 회사 데이터를 보호하고 회사 리소스에 액세스하기 위해 최종 사용자가 사용하는 장치를 관리하는 정책을 만듭니다. 그런 다음, 그룹에 정책을 할당합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73e1e0a27d128d567a924e6f2b343026b11f1a44
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581654"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>빠른 시작: Windows 10 장치에 대한 장치 준수 정책 추가
Windows에 대한 Intune 장치 준수 정책은 Windows 장치가 준수하는 것으로 간주되려면 충족해야 하는 규칙과 설정을 지정합니다. 이러한 정책을 [조건부 액세스](https://docs.microsoft.com/intune/conditional-access)와 함께 사용하여 회사 리소스에 대한 액세스를 허용하거나 차단할 수 있습니다. 장치 보고서를 가져오 고 비준수에 대해 조치를 할 수 있습니다.

이 빠른 시작에서는 Windows 10 장치에 대한 장치 준수 정책을 만든 다음, 장치 그룹을 정책에 할당합니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건
- 이 빠른 시작을 완료하려면 [사용자를 만들고](quickstart-create-user.md) [그룹을 만들어야 합니다](quickstart-create-group.md).


## <a name="sign-in-to-intune"></a>Intune에 로그인
[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다.

## <a name="create-a-device-compliance-policy"></a>장치 준수 정책 만들기
1. **장치 준수** > **정책** > **정책 만들기**를 선택합니다.
2. **이름**에 **Windows 10 규정 준수**를 입력하고 **설명**에 **Windows 10에 대한 준수 정책 샘플**을 입력합니다.
3. **플랫폼**에서 **Windows 10 이상**을 선택합니다.
4. **설정**에서 **시스템 보안**을 선택한 다음, **모바일 장치의 잠금을 해제하는 데 암호 필요**를 **필요**로 설정합니다. 정책 설정이 완료되면 **확인**을 선택합니다.
   ![준수 정책](/intune/media/quickstart-create-policy/compliance-policy.png)
5. **Windows 10 준수 정책** 창을 닫습니다. 
6. **정책 만들기** 창에서 **만들기**를 선택합니다. 이 단계에서는 정책을 만들고 **장치 준수** > **정책**에 정책을 나열합니다.
7. 새 정책을 선택하고 **할당**을 선택합니다. Azure AD(Active Directory) 보안 그룹을 포함하거나 제외할 수 있습니다.
8. **선택된 그룹**을 선택하면 기존 Azure AD 보안 그룹이 표시됩니다. **Contoso 테스터**를 선택하고, **저장**을 선택하여 그룹의 사용자에게 정책을 배포합니다. [그룹 만들기](quickstart-create-group.md)에서 이 그룹을 만들지 않은 경우 원하는 그룹을 사용할 수 있습니다. 

## <a name="clean-up-resources"></a>리소스 정리
정책이 더 이상 필요 없으면 정책을 삭제합니다. 삭제하려면 **Windows 10 준수** 정책을 선택하고 **삭제**를 클릭합니다. 

## <a name="next-steps"></a>다음 단계
이 빠른 시작에서는 간단한 장치 준수 정책을 만들고 할당했습니다. 정책을 수신할 Windows 10 장치를 등록하려면 자동 등록을 설정하는 방법에 대한 빠른 시작을 계속 진행하세요. 
 
> [!div class="nextstepaction"]
> [자동 등록 설정](quickstart-setup-auto-enrollment.md)