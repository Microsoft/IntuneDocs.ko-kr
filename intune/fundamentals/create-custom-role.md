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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b7e8f5077f2052a11c980ae3f5629af810a8a0b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726117"
---
# <a name="create-a-custom-role-in-intune"></a>Intune에서 사용자 지정 역할 만들기

특정 작업 기능에 필요한 모든 권한을 포함하는 사용자 지정 Intune 역할을 만들 수 있습니다. 예를 들어 IT 부서 그룹에서 애플리케이션, 정책 및 구성 프로필을 관리하는 경우 이러한 모든 권한을 사용자 지정 역할 하나에 추가할 수 있습니다. 사용자 지정 역할을 만든 후 해당 권한이 필요한 모든 사용자에게 [할당](assign-role.md)할 수 있습니다.

역할을 만들거나 편집하거나 할당하려면 계정에 Azure AD의 다음 사용 권한 중 하나가 있어야 합니다.
- **전역 관리자**
- **Intune 서비스 관리자**

## <a name="to-create-a-custom-role"></a>사용자 지정 역할을 만들려면

1. Intune 자격 증명을 사용하여 [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. 왼쪽 메뉴에서 **모든 서비스**를 선택한 다음, 텍스트 상자 필터에 **Intune**을 입력합니다.

3. **Intune** > **역할** > **모든 역할** > **추가**를 선택합니다.

4. **사용자 지정 역할 추가** 블레이드에서 새 역할의 이름 및 설명을 입력하고 **권한**을 클릭합니다.

5. **사용 권한** 블레이드에서 이 역할에 사용할 사용 권한을 선택합니다.

6. **범위(태그)** 블레이드에서 이 역할에 대한 태그를 선택합니다. 이 역할은 이러한 태그가 있는 리소스에 액세스할 수도 있습니다.

7. 작업이 완료되면 **확인**을 선택합니다.

8. **사용자 지정 역할 추가** 블레이드에서 **만들기**를 클릭합니다. **Intune 역할 - 모든 역할** 블레이드의 목록에 새 역할이 표시됩니다.

## <a name="next-steps"></a>다음 단계
- [사용자에게 역할 할당](assign-role.md)
- [Intune에서 역할 기반 액세스 제어에 대해 자세히 알아보기](role-based-access-control.md)
