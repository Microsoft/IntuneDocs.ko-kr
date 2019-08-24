---
title: Jamf 디바이스에 대한 디바이스 준수 정책
titleSuffix: Microsoft Intune
description: 보안 Jamf 관리 디바이스를 도우려면 Azure Active Directory의 조건부 액세스와 함께 Microsoft Intune 준수 정책을 사용합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d23e725db965a249522f7f8fa89f8bb27bc24fd8
ms.sourcegitcommit: 864fdf995c2b41f104a98a7e2665088c2864774f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68680002"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Jamf Pro로 관리되는 Mac에서 준수 적용

적용 대상: Azure Portal의 Intune

Azure Active Directory 및 Microsoft Intune의 조건부 액세스 정책을 사용하여 최종 사용자가 조직 요구 사항을 준수하도록 할 수 있습니다. 이 정책을 [Jamf Pro로 관리되는](conditional-access-integrate-jamf.md) Mac에 적용할 수 있습니다. Intune 및 Jamf Pro 콘솔에 둘 다 액세스할 수 있어야 합니다.

## <a name="set-up-device-compliance-policies-in-intune"></a>Intune에서 디바이스 준수 정책 설정

1. Microsoft Azure를 열고 **Intune** > **디바이스 준수** > **정책**으로 이동합니다. 비준수 사용자 및 그룹에 대한 일련의 작업(예: 경고 이메일 보내기) 선택을 포함하여 macOS에 대한 정책을 만들 수 있습니다.
2. [정책] > [할당]을 선택합니다. Azure AD(Active Directory) 보안 그룹을 포함하거나 제외할 수 있습니다.
3. [선택된 그룹]을 선택하면 Azure AD 보안 그룹이 표시됩니다. 이 정책을 적용할 사용자 그룹을 선택한 후 [저장]을 선택하여 정책을 사용자에게 배포합니다.

사용자에게 정책을 적용했습니다. 정책의 대상이 되는 사용자가 사용하는 디바이스의 준수 여부가 평가되고 Azure Active Directory에서 “준수 상태로 표시된 디바이스 필요” 설정에 대해 준수 상태로 표시됩니다.

> [!Note]
> Intune에서 정책을 준수하려면 전체 디스크 암호화가 필요합니다.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Jamf Pro에서 macOS용 회사 포털 앱 배포

아래 절차에 따라 Jamf Pro에서 macOS용 회사 포털 앱을 백그라운드 설치로 배포해야 합니다.

1. macOS 디바이스에서 [macOS용 회사 포털 앱](https://go.microsoft.com/fwlink/?linkid=862280)의 현재 버전을 다운로드합니다. 설치하지는 않습니다. Jamf Pro에 업로드할 앱 복사본이 필요합니다.
2. Jamf Pro를 열고 **컴퓨터 관리** > **패키지**로 이동합니다.
3. macOS용 회사 포털 앱이 포함된 새 패키지를 만든 다음 **저장**을 클릭합니다.
4. **컴퓨터** > **정책**을 열고 **새로 만들기**를 선택합니다.
5. **일반** 페이로드를 사용하여 정책에 대한 설정을 구성합니다. 이 설정은 다음과 같아야 합니다.
   - 트리거: **등록 완료** 및 **Recurring Check-in**(되풀이 체크 인)을 선택합니다.
   - 실행 빈도: **Once per computer**(컴퓨터당 한 번)를 선택합니다.
6. **패키지** 페이로드를 선택하고 **구성**을 클릭합니다.
7. **추가**를 클릭하여 회사 포털 앱이 포함된 패키지를 선택합니다.
8. **작업** 팝업 메뉴에서 **설치**를 선택합니다.
9. 패키지의 설정을 구성합니다.
10. **범위** 탭을 클릭하여 회사 포털 앱을 설치할 컴퓨터를 지정합니다. **저장**을 클릭합니다. 다음 번에 컴퓨터에서 선택한 트리거가 발생하고 **일반** 페이로드의 기준을 충족하면 정책에 따라 범위가 지정된 디바이스가 실행됩니다.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Jamf Pro에서 사용자가 자신의 디바이스를 Azure Active Directory에 등록하도록 하는 정책 만들기

> [!NOTE]
> 다음 단계를 진행하기 전에 macOS용 [회사 포털을 배포](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)해야 합니다.  

최종 사용자는 Jamf Self 서비스를 통해 회사 포털 앱을 시작하여 Azure AD가 포함된 디바이스를 Jamf Pro에서 관리되는 디바이스로 등록해야 합니다. 이를 위해서는 최종 사용자가 조치를 취해야 합니다. 전자 메일, Jamf Pro 알림 또는 Jamf Self Service의 단추를 클릭하도록 최종 사용자에게 알리는 다른 방법을 통해 [최종 사용자에게 연락](end-user-educate.md)하는 것이 좋습니다.

> [!WARNING]
> 디바이스 등록을 시작하려면 회사 포털 앱을 Jamf Self Service에서 시작해야 합니다. <br><br>회사 포털 앱을 수동으로 시작하는 경우(예: 애플리케이션 또는 다운로드 폴더에서) 디바이스가 등록되지 않습니다. 최종 사용자가 회사 포털 앱을 수동으로 시작하면 'AccountNotOnboarded' 경고가 표시됩니다.

1. Jamf Pro에서 **컴퓨터** > **정책**으로 이동하고 디바이스 등록을 위한 새 정책을 만듭니다.
2. 트리거 및 실행 빈도를 포함하여 **Microsoft Intune 통합** 페이로드를 구성합니다.
3. **범위** 탭을 클릭하고 정책 범위를 모든 대상 디바이스로 지정합니다.
4. **Self Service** 탭을 클릭하여 정책을 Jamf Self Service에서 사용 가능하게 설정합니다. **디바이스 준수** 범주에 정책을 포함합니다. **저장**을 클릭합니다.

## <a name="removing-a-jamf-managed-device-from-intune"></a>Intune에서 Jamf 관리 디바이스를 제거합니다.

**모든 디바이스** 보기에서 **삭제**를 선택하여 Intune 콘솔에서 Jamf 관리 디바이스를 제거할 수 있습니다. 여러 디바이스를 선택하고 **삭제**를 클릭하여 대량 디바이스 삭제를 사용하도록 설정할 수 있습니다.

[Jamf 관리 디바이스를 Jamf Pro 문서에서 제거](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)하는 방법에 대해 알아봅니다. 또한 추가 도움을 위해 지원 티켓을 [Jamf 지원](https://www.jamf.com/support/)와 함께 제출할 수 있습니다. 

## <a name="next-steps"></a>다음 단계

- [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Azure Active Directory에서 조건부 액세스 시작](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
