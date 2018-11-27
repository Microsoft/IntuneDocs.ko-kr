---
title: Microsoft Intune - Azure를 사용한 비준수 메시지와 작업 | Microsoft Docs
description: 비준수 장치에 보낼 알림 이메일을 만듭니다. 장치가 비준수로 표시된 후 준수하기 위한 유예 기간을 추가하거나 장치가 준수하기까지 액세스를 차단하는 일정을 만드는 등의 작업을 추가합니다. Azure에서 Microsoft Intune을 사용하여 이를 수행합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5bd8bfe0230e4d49ce5ae4372e0f373a014c00ce
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187775"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>이메일 자동화 및 비준수 장치 - Intune에 대한 작업 추가

작업을 시간 순으로 구성하는 **비준수에 대한 작업** 기능이 있습니다. 이러한 작업은 준수 정책에 맞지 않는 장치에 적용됩니다. 

## <a name="overview"></a>개요
기본적으로 Intune에서 준수하지 않는 장치를 검색한 경우 Intune은 즉시 장치를 비준수로 표시합니다. Azure AD(Active Directory) [조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)는 장치를 차단합니다. 장치가 비준수 상태일 경우 **비준수에 대한 작업**은 수행할 작업을 결정하는 데 유연성을 제공합니다. 예를 들어 장치를 즉시 차단하지 않고 사용자에게 준수하도록 유예 기간을 부여합니다.

몇 가지 유형의 작업이 있습니다.

- **최종 사용자에게 메일 보내기**: 최종 사용자에게 보내기 전에 메일 알림을 사용자 지정합니다. 회사 로고, 연락처 정보를 비롯하여 받는 사람, 제목, 메시지 본문을 사용자 지정할 수 있습니다.

    또한 Intune은 비준수 장치에 대한 세부 정보를 이메일 알림에 포함합니다.

- **원격으로 비규격 장치 잠금**: 비규격 장치의 경우 원격 잠금을 실행할 수 있습니다. 그러면 장치 잠금을 해제하기 위해 PIN 또는 암호를 입력하라는 메시지가 표시됩니다. [원격 잠금](device-remote-lock.md) 기능에 대해 자세히 알아봅니다. 

- **장치를 비준수로 표시**: 장치를 비준수로 표시한 후 일정을(일 수로) 만듭니다. 작업이 즉시 적용되도록 구성하거나 사용자에게 준수할 유예 기간을 제공할 수 있습니다.

이 문서에서는 다음 방법을 보여 줍니다.

- 메시지 알림 템플릿 만들기
- 비준수 장치에 대해 메일 보내기 또는 장치 원격 잠금과 같은 작업을 만듭니다.


## <a name="before-you-begin"></a>시작하기 전에

- 비준수에 대한 작업을 설정하려면 하나 이상의 장치 준수 정책이 있어야 합니다. 장치 준수 정책을 만들려면 다음 플랫폼을 참조하세요.

  - [OWA(Outlook Web Access)](compliance-policy-create-android.md)
  - [Android 회사 프로필](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- 장치 준수 정책을 사용하여 장치가 회사 리소스를 사용하지 못하도록 차단하려면 Azure AD 조건부 액세스가 설정돼야 합니다. 지침에 대해서는 [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) 또는 [Intune에서 조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)을 참조하세요.

## <a name="create-a-notification-message-template"></a>알림 메시지 템플릿 만들기

사용자에게 메일을 보내려면 알림 메시지 템플릿을 만듭니다. 장치가 비준수 상태이면 템플릿에 입력한 세부 사항이 사용자에게 보낸 메일에 표시됩니다.

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **장치 준수** > **알림**을 선택합니다.
3. **알림 만들기**를 선택합니다. 다음 정보를 입력합니다.

   - **Name**
   - **제목**
   - **Message**
   - **메일 머리글 – 회사 로고 포함**
   - **메일 바닥글 – 회사 이름 포함**
   - **메일 바닥글 – 연락처 정보 포함**

   ![Intune에서 준수 알림 메시지의 예](./media/actionsfornoncompliance-1.PNG)

4. 정보 추가를 완료하면 **만들기**를 선택합니다. 알림 메시지 템플릿을 사용할 준비가 됐습니다. 회사 포털 브랜딩의 일부로 업로드하는 로고는 이메일 템플릿에 사용됩니다. 회사 포털 브랜딩에 대한 자세한 내용은 [회사 ID 브랜딩 사용자 지정](company-portal-app.md#company-identity-branding-customization)을 참조하세요.  

> [!NOTE]
> 이전에 만든 알림 템플릿을 편집할 수도 있습니다.

## <a name="add-actions-for-noncompliance"></a>비준수에 대한 작업 추가

장치 준수 정책을 만들면 Intune은 비준수 장치인 경우에 수행할 작업을 자동으로 만듭니다. 장치가 준수 정책을 충족하지 않는 경우 이 작업은 해당 장치를 비준수로 표시합니다. 장치가 비준수로 표시되는 기간을 사용자 지정할 수 있습니다. 이 작업은 제거할 수 없습니다.

준수 정책을 만들 때 다른 작업을 추가하거나 기존 정책을 업데이트할 수도 있습니다. 

1. [Azure Portal](https://portal.azure.com)에서 **Microsoft Intune** > **장치 준수**를 엽니다.
2. **정책**을 선택하고 사용자 정책 중 하나를 선택한 다음, **속성**을 선택합니다. 

    정책이 아직 없습니까? [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) 또는 다른 플랫폼 정책을 만듭니다.
  
    > [!NOTE]
    > JAMF 장치 및 장치 그룹을 사용하여 대상으로 지정된 장치는 현재 준수 작업을 받을 수 없습니다.

3. **비준수에 대한 작업** > **추가**를 선택합니다.
4. **작업**을 선택합니다. 

    - **최종 사용자에게 메일 보내기**: 장치가 비준수 상태이면 사용자에게 메일을 보내도록 선택합니다. 또한 다음 작업도 수행합니다. 
    
         - 이전에 만든 **메시지 템플릿**을 선택합니다.
         - 그룹을 선택하여 **추가 받는 사람**를 입력합니다.
    
    - **원격으로 비규격 장치 잠금**: 장치가 비준수 상태이면 장치를 잠급니다. 이렇게 하면 사용자는 장치 잠금을 해제하기 위해 PIN 또는 암호를 반드시 입력해야 합니다. 
    
    - **스케줄**: 사용자 장치에 대해 작업을 트리거할 비준수 이후의 일 수(0-365)를 입력합니다. 이 유예 기간이 지나면 조건부 액세스 정책을 적용할 수 있습니다. **0**일을 입력하면 조건부 액세스가 **즉시** 적용됩니다. 예를 들어, 장치가 비준수 상태이면 회사 리소스에 대한 액세스를 즉시 차단할 수 있습니다.

5. 완료되면 **추가** > **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="next-steps"></a>다음 단계
[장치 준수 활동을 모니터링합니다](device-compliance-monitor.md).
