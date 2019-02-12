---
title: Intune 디바이스 등록에 대한 다단계 인증 요구
titlesuffix: Microsoft Intune
description: Azure AD에서 Intune 디바이스를 등록하기 위해 다단계 인증을 요구하는 방법입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 71d551ca64f85c3ba6a807fac70e3b0662e1b89a
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834095"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Intune 디바이스 등록에 대한 다단계 인증 요구

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune은 장치 등록 시 Azure AD(Active Directory) MFA(다단계 인증)를 사용하여 회사 리소스를 보호하는 데 도움을 줄 수 있습니다.

MFA는 다음과 같은 검증 방법 중 두 가지 이상을 요구하는 방식으로 작동합니다.

- 사용자가 알고 있는 항목(대개 암호 또는 PIN)
- 사용자가 가지고 있는 항목(휴대폰처럼 쉽게 복제할 수 없으며 신뢰할 수 있는 디바이스)
- 사용자의 특징을 나타내는 항목(지문과 같은 생체 인식)

MFA는 iOS, Android, Windows 8.1 이상, Windows Phone 8.1 또는 Windows 10 Mobile 이상의 디바이스에서 지원됩니다.

MFA를 사용하도록 설정하면 최종 사용자가 디바이스를 등록하기 위해 두 가지 형식의 자격 증명을 제공해야 합니다.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>디바이스 등록 단계에서 다단계 인증을 요구하도록 Intune 구성

장치 등록시 MFA를 요구하려면 다음 단계를 진행합니다.

>[!Important]
>이 정책을 구현하려면 사용자에게 Azure Active Directory Premium P1 이상이 할당되어 있어야 합니다.

>[!Important]
>Microsoft Intune 등록에 대한 **디바이스 기반 액세스 규칙**을 구성하지 마세요.

1. 자격 증명으로 [Microsoft Azure Portal](https://portal.azure.com)에 로그인합니다.
2. 포털에서 **[Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)** 로 이동합니다.
3. 보안 아래의 **Azure Active Directory**에서 **[조건부 액세스](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)** 를 선택합니다.
4. **새 정책**을 선택합니다.
5. **새 정책**에서 정책에 대한 설명이 포함된 이름을 입력합니다.
6. **할당** 섹션에서 **사용자 및 그룹**을 선택합니다.
7. **사용자 및 그룹**에서 **사용자 또는 그룹 선택**을 선택하고 **사용자 및 그룹**을 확인합니다. 그런 다음, 이 정책을 수신할 사용자 및/또는 그룹을 선택한 다음, **완료**를 선택합니다.
8. **할당** 섹션에서 **클라우드 앱**을 선택합니다.
9. **클라우드 앱**의 **포함** 탭에서 **앱 선택**을 선택한 다음 **선택** > **Microsoft Intune 등록**을 선택하고 **완료**를 선택합니다.
10. **할당** 섹션에서 **조건**에 대해 MFA에 대한 설정을 구성할 필요가 없습니다.
11. **액세스 제어** 섹션에서 **허용**을 선택합니다.
12. **허용**에서 **액세스 권한 부여**를 선택한 다음 **다단계 인증 기능 필요**를 선택합니다. 디바이스가 등록될 때까지는 준수 여부를 평가할 수 없으므로 **준수 상태로 표시된 디바이스 필요**를 선택하지 마세요. 그런 다음, **선택**을 선택합니다.
13. **새 정책**에서 **정책 사용** > **켬**을 선택한 다음 **만들기**를 선택합니다.



## <a name="next-steps"></a>다음 단계

최종 사용자가 디바이스를 등록할 때 이제는 PIN, 전화 또는 생체 인식과 같은 두 번째 식별 형식으로 인증해야 합니다.
