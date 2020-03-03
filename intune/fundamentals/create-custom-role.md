---
title: Intune에서 사용자 지정 역할 만들기
description: Microsoft Intune에서 사용자 지정 역할을 만드는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569186"
---
# <a name="create-a-custom-role-in-intune"></a>Intune에서 사용자 지정 역할 만들기

특정 작업 기능에 필요한 모든 권한을 포함하는 사용자 지정 Intune 역할을 만들 수 있습니다. 예를 들어 IT 부서 그룹에서 애플리케이션, 정책 및 구성 프로필을 관리하는 경우 이러한 모든 권한을 사용자 지정 역할 하나에 추가할 수 있습니다. 사용자 지정 역할을 만든 후 해당 권한이 필요한 모든 사용자에게 [할당](assign-role.md)할 수 있습니다.

역할을 만들거나 편집하거나 할당하려면 계정에 Azure AD의 다음 사용 권한 중 하나가 있어야 합니다.
- **전역 관리자**
- **Intune 서비스 관리자**

## <a name="to-create-a-custom-role"></a>사용자 지정 역할을 만들려면

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **테넌트 관리** > **역할** > **모든 역할** > **만들기**를 선택합니다.

2. **기본 사항** 페이지에서 새 역할의 이름과 설명을 입력한 후 **다음**을 선택합니다.

3. **권한** 창에서 이 역할에 사용할 권한을 선택합니다.

4. **범위(태그)** 페이지에서 이 역할의 태그를 선택합니다. 이 역할은 이러한 태그가 있는 리소스에 액세스할 수도 있습니다. **다음**을 선택합니다.

5. **검토 + 만들기** 페이지에서 완료되면 **만들기**를 선택합니다. **Intune 역할 - 모든 역할** 블레이드의 목록에 새 역할이 표시됩니다.

## <a name="copy-a-role"></a>역할 복사

기존 역할을 복사할 수도 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **테넌트 관리** > **역할** > **모든 역할** > 목록에서 역할의 확인란 선택 > **복제**를 선택합니다.

2. **기본 사항** 페이지에서 이름을 입력합니다. 고유한 이름을 사용해야 합니다.

3. 원본 역할의 모든 권한 및 범위 태그는 이미 선택되어 있습니다. 나중에 중복 역할의 **이름**, **설명**, **권한**및 **범위(태그)** 를 변경할 수 있습니다.

4. 원하는 모든 변경 작업을 수행한 후 **다음**을 선택하여 **검토 + 만들기** 페이지로 이동합니다. **만들기**를 선택합니다. 

## <a name="next-steps"></a>다음 단계
- [사용자에게 역할 할당](assign-role.md)
- [Intune에서 역할 기반 액세스 제어에 대해 자세히 알아보기](role-based-access-control.md)


