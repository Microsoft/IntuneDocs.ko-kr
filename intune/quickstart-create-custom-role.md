---
title: 빠른 시작 - Intune에서 사용자 지정 역할 만들기 및 할당
description: 빠른 시작 - 원격 디바이스 관리자에 대한 사용자 지정 역할을 만들고 할당합니다.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: be3ef61d3bdce2f1ad74a388a2ec50691313a1d1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57400291"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>빠른 시작: 사용자 지정 역할 만들기 및 할당

이 Intune 빠른 시작에서는 보안 작업 부서에 대해 특정 사용 권한을 가진 사용자 지정 역할을 만듭니다. 그 후 해당 역할을 이러한 운영자 그룹에 할당합니다. 즉시 사용할 수 있는 여러 기본 역할이 있습니다. 하지만 이와 같은 사용자 지정 역할을 만들면 모바일 디바이스 관리 시스템의 모든 부분에 대한 액세스를 정밀하게 제어할 수 있습니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건

- 이 빠른 시작을 완료하려면 [그룹을 만들어야 합니다](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다.

## <a name="create-a-custom-role"></a>사용자 지정 역할 만들기

사용자 지정 역할을 만들 때 다양한 작업에 대한 권한을 설정할 수 있습니다. 보안 작업 역할의 경우 운영자가 디바이스의 구성 및 정책을 검토할 수 있도록 읽기 권한을 설정하겠습니다.

1. Intune에서 **역할** > **모든 역할** > **추가**를 선택합니다.
![브라우저](media/quickstart-create-custom-role/add-custom-role.png)
2. **사용자 지정 역할 추가**에서 **이름** 상자에 입력 *보안 작업*을 입력합니다.
3. **설명** 상자에 *보안 운영자가 디바이스 구성 및 규정 준수 정보를 모니터링할 수 있게 해주는 역할*을 입력합니다.
4. **읽기** > **확인** 옆에서 **구성** > **회사 디바이스 식별자** > **예**를 선택합니다.
![브라우저](media/quickstart-create-custom-role/corp-device-id-read.png)
5. **읽기** > **확인** 옆에서 **디바이스 준수 정책** > **예**를 선택합니다.
6. **읽기** > **확인** 옆에서 **디바이스 구성** > **예**를 선택합니다.
7. **읽기** > **확인** 옆에서 **조직** > **예**를 선택합니다.
8. **확인** > **만들기**를 선택합니다.

## <a name="assign-the-role-to-a-group"></a>그룹에 역할 할당

보안 운영자가 새 권한을 사용하려면, 먼저 보안 사용자가 포함된 그룹에 역할을 할당해야 합니다.

1. Intune에서 **역할** > **모든 역할** > **보안 작업**을 선택합니다.
2. **Intune 역할** 아래에서 **할당** > **할당**을 선택합니다.
3. **할당 이름** 상자에 *보안 작업*을 입력합니다.
4. **멤버(그룹)** > **추가**를 선택합니다.
5. **Contoso 테스터** 그룹을 선택합니다.
6. **선택** > **확인**을 선택합니다.
7. **범위(그룹)** > **포함할 그룹 선택** > **Contoso 테스터**를 선택합니다.
8. **선택** > **확인** > **확인**을 선택합니다.

이제 그룹의 모든 구성원은 *보안 작업* 역할의 구성원이며 회사 장치 식별자, 장치 준수 정책, 장치 구성 및 조직 정보와 같은 장치에 대한 정보를 검토할 수 있습니다.

## <a name="clean-up-resources"></a>리소스 정리

새 사용자 지정 역할이 더 이상 필요 없으면 삭제할 수 있습니다. **역할** > **모든 역할**에서 역할 옆에 있는 줄임표(...)를 선택하고 **삭제**를 선택합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 사용자 지정 보안 작업 역할을 만들고 그룹에 할당했습니다. Intune의 역할에 대한 자세한 내용은 [Microsoft Intune을 통한 RBAC(역할 기반 관리 제어)](role-based-access-control.md)를 참조하세요.

다음 Intune 빠른 시작을 진행하기 위해서는 아래 빠른 시작 링크를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: iOS용 이메일 디바이스 프로필 만들기](quickstart-email-profile.md)
