---
title: 빠른 시작 - 비규격 디바이스로 알림 보내기
titleSuffix: Microsoft Intune
description: 이 빠른 시작에서는 Microsoft Intune을 사용하여 비규격 디바이스에 이메일 알림을 보냅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/27/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb175d2133cf2a7bc5b064c13afb7e252147c729
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044242"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>빠른 시작: 비규격 디바이스로 알림 보내기

이 빠른 시작에서는 Microsoft Intune을 사용하여 비규격 디바이스가 있는 직원의 구성원에게 이메일 알림을 보냅니다.

기본적으로 Intune에서 준수하지 않는 디바이스를 검색한 경우 Intune은 즉시 디바이스를 비준수로 표시합니다. AAD(Azure Active Directory) [조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)는 디바이스를 차단합니다. 디바이스가 비준수 상태일 경우 Intune을 사용하면 비준수 작업을 추가할 수 있으며, 이를 통해 수행할 작업을 유연하게 결정할 수 있습니다. 예를 들어 비규격 디바이스를 차단하기 전에 사용자에게 준수 유예 기간을 지정할 수 있습니다.

디바이스가 규정을 준수하지 않을 때 수행할 수 있는 작업 중 하나는 해당 최종 사용자에게 이메일을 보내는 것입니다. 이메일 알림을 최종 사용자에게 보내기 전에 사용자 정의할 수도 있습니다. 특히 회사 로고, 연락처 정보를 비롯하여 받는 사람, 제목 및 메시지 본문을 사용자 지정할 수 있습니다. Intune은 비규격 디바이스에 대한 세부 정보도 이메일 알림에 포함합니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건
- 디바이스 준수 정책을 사용하여 디바이스가 회사 리소스를 사용하지 못하도록 차단하려면 AAD 조건부 액세스가 설정돼야 합니다. [디바이스 준수 정책 만들기](quickstart-set-password-length-android.md) 빠른 시작을 완료한 경우 Azure Active Directory를 사용하고 있는 것입니다. AAD에 대한 자세한 내용은 [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) 또는 [Intune에서 조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)을 참조하세요.

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal) 포털에 [글로벌 관리자](users-add.md#types-of-administrators) 또는 Intune [서비스 관리자](users-add.md#types-of-administrators)로 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="create-a-notification-message-template"></a>알림 메시지 템플릿 만들기

사용자에게 메일을 보내려면 알림 메시지 템플릿을 만듭니다. 디바이스가 비준수 상태이면 템플릿에 입력한 세부 사항이 사용자에게 보낸 메일에 표시됩니다.

1. Intune에서 **디바이스 준수** > **알림** > **알림 만들기**를 선택합니다. 
2. 다음 정보를 입력합니다.

   - **이름**: *Contoso 관리자*
   - **제목**: *디바이스 정책 준수*
   - **메시지**: *현재 디바이스가 조직의 규정 준수 요구 사항을 충족하지 않습니다.*
   - **이메일 헤더 – 회사 로고 포함**: **사용**으로 설정하여 조직 로고를 표시합니다.
   - **이메일 바닥글 – 회사 이름 포함**: **사용**으로 설정하여 조직 이름을 표시합니다.
   - **이메일 바닥글 – 연락처 정보 포함**: **사용**으로 설정하여 조직의 연락처 정보를 표시합니다.

   ![Intune에서 준수 알림 메시지의 예](./media/quickstart-send-notification-01.png)

3. 정보 추가를 완료하면 **만들기**를 선택합니다. 알림 메시지 템플릿을 사용할 준비가 됐습니다.

    > [!NOTE]
    > 이전에 만든 알림 템플릿을 편집할 수도 있습니다.

회사 이름, 회사 연락처 정보 및 회사 로고 설정에 대한 자세한 내용은 [회사 정보 및 개인정보처리방침](company-portal-app.md#company-information-and-privacy-statement), [지원팀 정보](company-portal-app.md#support-information) 및 [회사 ID 브랜딩 사용자 지정](company-portal-app.md#company-identity-branding-customization)을 참조하세요. 

## <a name="add-a-noncompliance-policy"></a>비준수 정책 추가

디바이스 준수 정책을 만들면 Intune은 비준수 디바이스인 경우에 수행할 작업을 자동으로 만듭니다. 디바이스가 준수 정책을 충족하지 않는 경우 Intune이 자동으로 디바이스를 비준수로 표시합니다. 디바이스가 비준수로 표시되는 기간을 사용자 지정할 수 있습니다. 준수 정책을 만들 때 다른 작업을 추가하거나 기존 준수 정책을 업데이트할 수도 있습니다. 

다음 단계에서는 Windows 10 디바이스에 대한 준수 정책을 만듭니다.

1. Intune에서 **디바이스 준수**를 선택합니다.
2. **정책** > **정책 만들기**를 선택합니다.
3. 다음 정보를 입력합니다.

   - **이름**: *Windows 10 규정 준수*
   - **설명**: *Windows 10 규정 준수 정책*
   - **플랫폼**: Windows 10 이상

4. **설정** > **시스템 보안**을 선택하여 디바이스 보안 관련 설정을 표시합니다.
5. **모바일 디바이스의 잠금을 해제하는 데 암호 요구**를 **필요**로 설정합니다. 이 설정은 사용자의 모바일 장치에 있는 정보에 액세스하기 위해 암호를 입력해야 하는지 여부를 지정합니다. 
6. **최소 암호 길이**를 **6**으로 설정합니다. 이 설정은 최소 암호 자릿수 또는 문자 수를 지정합니다.

    <img alt="System Security settings for a new compliance policy" src="./media/quickstart-send-notification-02.png" width="600">

7. **확인** > **확인** > **만들기**를 선택하여 준수 정책을 만듭니다.
8. **속성** > **비준수에 대한 작업** > **추가**를 선택합니다.
9. **작업** 드롭다운 목록 상자에서 **최종 사용자에게 이메일 보내기**가 선택되었는지 확인합니다.
10. **메시지 템플릿** > **Contoso 관리자** > **선택**을 선택하여 이 항목의 앞부분에서 만든 메시지 템플릿을 선택합니다.
11. **추가** > **확인** > **저장**을 선택하여 변경 내용을 저장합니다.

## <a name="assign-the-policy"></a>정책 할당

준수 정책은 특정 사용자의 그룹 또는 모든 사용자에게 할당할 수 있습니다. Intune에서 디바이스가 비준수임을 인식하면 사용자에게 준수 정책을 충족하도록 디바이스를 업데이트해야 한다는 알림이 표시됩니다. 다음 단계를 통해 정책을 할당할 수 있습니다.

1. 이전에 만든 **Windows 10 준수** 정책을 선택합니다.
2. **할당**을 선택합니다.
3. **할당 대상** 드롭다운 목록 상자에서 **모든 사용자**를 선택합니다. 그러면 모든 사용자가 선택됩니다. 이 준수 정책을 충족하지 않는 **Windows 10 이상** 디바이스가 있는 모든 사용자에게 알림이 표시됩니다.

    > [!NOTE]
    > 준수 정책을 할당할 때 그룹을 포함하거나 제외할 수 있습니다.

4. **저장**을 클릭합니다.

정책을 성공적으로 만들고 저장하면 **디바이스 준수 - 정책** 목록에 표시됩니다. 목록에서 **할당됨**이 **예**로 설정되어 있음을 확인합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Intune을 사용하여 직원의 Windows 10 디바이스에 최소 6자 길이의 암호를 요구하는 준수 정책을 만들고 할당했습니다. Windows 디바이스에 대한 준수 정책 만들기에 대한 자세한 내용은 [Intune에서 Windows 디바이스에 대한 디바이스 준수 정책 추가](compliance-policy-create-windows.md)를 참조하세요.

다음 Intune 빠른 시작을 진행하기 위해서는 아래 빠른 시작 링크를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: 클라이언트 앱 추가 및 할당](quickstart-add-assign-app.md)
