---
title: Microsoft Intune - Azure를 사용한 비준수 메시지와 작업 | Microsoft Docs
description: 비준수 장치에 보낼 알림 이메일을 만듭니다. 장치가 비준수로 표시된 후 준수하기 위한 유예 기간을 추가하거나 장치가 준수하기까지 액세스를 차단하는 일정을 만드는 등의 작업을 추가합니다. Azure에서 Microsoft Intune을 사용하여 이를 수행합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8e8603ca59b46937b1529e710a8bc83aec5dd4d6
ms.sourcegitcommit: 4c18352d5b3b30080f7c7257fa63d852b1894850
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32017960"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>이메일 자동화 및 비준수 장치 - Intune에 대한 작업 추가

작업을 시간 순으로 구성하는 **비준수에 대한 작업** 기능이 있습니다. 이러한 작업은 준수 정책에 맞지 않는 장치에 적용됩니다. 

## <a name="overview"></a>개요
기본적으로 Intune에서 준수하지 않는 장치를 검색한 경우 Intune은 즉시 장치를 비준수로 표시합니다. Azure AD(Active Directory) [조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)는 장치를 차단합니다. 장치가 비준수 상태일 경우 **비준수에 대한 작업**은 수행할 작업을 결정하는 데 유연성을 제공합니다. 예를 들어 장치를 즉시 차단하지 않고 사용자에게 준수하도록 유예 기간을 부여합니다.

2가지 유형의 작업이 있습니다.

- **이메일을 통해 최종 사용자에게 알림**: 최종 사용자에게 보내기 전에 이메일 알림을 사용자 지정합니다. 회사 로고, 연락처 정보를 비롯하여 받는 사람, 제목, 메시지 본문을 사용자 지정할 수 있습니다.

    또한 Intune은 비준수 장치에 대한 세부 정보를 이메일 알림에 포함합니다.

- **장치를 비준수로 표시**: 장치를 비준수로 표시한 후 일정을(일 수로) 만듭니다. 작업이 즉시 적용되도록 구성하거나 사용자에게 준수할 유예 기간을 제공할 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

- 비준수에 대한 작업을 설정하려면 하나 이상의 장치 준수 정책이 있어야 합니다. 장치 준수 정책을 만들려면 다음 플랫폼을 참조하세요.

  - [OWA(Outlook Web Access)](compliance-policy-create-android.md)
  - [Android for Work](compliance-policy-create-android-for-work.md)
  - [Android](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- 장치 준수 정책을 사용하여 장치가 회사 리소스를 사용하지 못하도록 차단하려면 Azure AD 조건부 액세스가 설정돼야 합니다. [Azure Active Directory에서 조건부 액세스 구성](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)을 참조하여 안내를 받으십시오.

- 알림 메시지 템플릿을 반드시 만들어야 합니다. 사용자에게 이메일을 보내려면 이 템플릿이 비준수에 대해 작업을 만드는 데 사용됩니다.

## <a name="create-a-notification-message-template"></a>알림 메시지 템플릿 만들기

1. Intune 자격 증명을 사용하여 [Azure Portal](https://portal.azure.com)에 로그인합니다. 
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치 준수**를 선택한 다음, **알림**을 선택합니다. 
4. **알림 만들기**를 선택하고 다음 정보를 입력합니다.

   - 이름
   - 주체
   - 메시지
   - 이메일 머리글 – 회사 로고 포함
   - 이메일 바닥글 – 회사 이름 포함
   - 이메일 바닥글 – 연락처 정보 포함

   ![Intune에서 준수 알림 메시지의 예](./media/actionsfornoncompliance-1.PNG)

정보 추가를 완료하면 **만들기**를 선택합니다. 알림 메시지 템플릿을 사용할 준비가 됐습니다.

> [!NOTE]
> 이전에 만든 알림 템플릿을 편집할 수도 있습니다.

## <a name="add-actions-for-noncompliance"></a>비준수에 대한 작업 추가

기본적으로 Intune은 비준수에 대해 작업을 자동으로 만듭니다. 장치가 준수 정책을 충족하지 않는 경우 이 작업은 해당 장치를 비준수로 표시합니다. 장치가 비준수로 표시되는 기간을 사용자 지정할 수 있습니다. 이 작업은 제거할 수 없습니다.

새 장치 준수 정책을 만들 때 또는 기존 준수 정책을 업데이트할 때 작업을 추가할 수 있습니다. 

1. [Azure Portal](https://portal.azure.com)에서 **Microsoft Intune**을 열고 **장치 준수**를 선택합니다.
2. **정책**을 선택하고 사용자 정책 중 하나를 선택한 다음, **속성**을 선택합니다. 

  정책이 아직 없습니까? [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) 또는 다른 플랫폼 정책을 만듭니다.
  
  > [!NOTE]
  > JAMF 장치 및 장치 그룹을 사용하여 대상으로 지정된 장치는 현재 준수 작업을 받을 수 없습니다.

3. **비준수에 대한 작업**을 선택한 다음, **추가**를 선택하여 작업 매개 변수를 입력합니다. 이전에 만든 메시지 템플릿을 선택하고 추가 수신자를 추가하고 유예 기간 일정을 업데이트할 수 있습니다. 일정에서 일 수(0 - 365)를 입력할 수 있습니다. 그런 다음, 조건부 액세스 정책을 적용할 수 있습니다. 일 수를 **0**으로 입력하는 경우 조건부 액세스는 **즉시** 회사 리소스에 대한 액세스를 차단 합니다.

4. 완료되면 **추가** > **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="next-steps"></a>다음 단계
보고서를 실행하여 장치 준수 활동을 모니터링합니다. [Intune에서 장치 준수를 모니터링하는 방법](device-compliance-monitor.md)에서 몇 가지 지침을 제공합니다.
