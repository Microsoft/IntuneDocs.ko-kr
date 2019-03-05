---
title: 모바일 디바이스 관리 기관을 설정합니다.
titlesuffix: Microsoft Intune
description: Intune으로 모바일 디바이스 관리 기관을 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99b913b23638a507ed9b0a5cb32afff66679a164
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231913"
---
# <a name="set-the-mobile-device-management-authority"></a>모바일 디바이스 관리 기관을 설정합니다.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

MDM(모바일 디바이스 관리) 기관 설정에 따라 디바이스를 관리하는 방법이 결정됩니다. IT 관리자가 MDM 기관을 설정해야 사용자가 관리를 위해 디바이스를 등록할 수 있습니다.

가능한 구성은 다음과 같습니다.

- **Intune 독립 실행형** - Azure Portal을 사용하여 구성하는 클라우드 전용 관리입니다. Intune에서 제공하는 모든 기능 집합을 포함합니다. [Intune 콘솔에서 MDM 기관을 설정합니다](#set-mdm-authority-to-intune).

- **Intune 하이브리드** - Intune 클라우드 솔루션과 System Center Configuration Manager의 통합입니다. Configuration Manager 콘솔을 사용하여 Intune을 구성합니다. [Configuration Manager에서 MDM 기관을 설정합니다](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription). 

    > [!Important]
    >향후 릴리스에서는 새 하이브리드 MDM 고객의 온보딩이 꺼집니다. 자세한 내용은 [하이브리드 모바일 디바이스 관리에서 Azure의 Intune으로 이동](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) 블로그 게시물을 참조하세요.

- **Office 365용 모바일 디바이스 관리**  - Office 365와 Intune 클라우드 솔루션의 통합입니다. Office 365 관리 센터에서 Intune을 구성합니다. Intune 독립 실행형에서 제공되는 기능 중 일부를 포함합니다. Office 365 관리 센터에서 MDM 기관을 설정합니다.

> [!IMPORTANT]
> Configuration Manager 버전 1610 이상과 Microsoft Intune 버전 1705에서는 Microsoft 지원에 문의하여 기존의 관리 디바이스를 등록 취소했다가 다시 등록할 필요 없이 MDM 기관을 변경할 수 있습니다. 자세한 내용은 [MDM 기관을 Configuration Manager로 변경 준비](mdm-authority-set.md#prepare-to-change-the-mdm-authority-to-configuration-manager)를 참조하세요.

## <a name="set-mdm-authority-to-intune"></a>MDM 기관을 Intune으로 설정

MDM 기관을 아직 설정하지 않은 경우 다음 단계를 수행합니다. MDM 기관을 변경하려면 아래의 [MDM 기관 변경](#prepare-to-change-the-mdm-authority-to-configuration-manager) 섹션을 참조합니다.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. 주황색 배너를 선택하여 **모바일 디바이스 관리 기관** 설정을 엽니다. 주황색 배너는 MDM 기관을 아직 설정하지 않은 경우만 표시됩니다.
4. **모바일 디바이스 관리 기관** 아래에서, 다음 옵션 중에서 MDM 기관을 선택합니다.
   - **Intune MDM 기관**
   - **Configuration Manager MDM 기관**
   - **없음**

   ![Intune의 모바일 디바이스 관리 기관 설정 화면 스크린샷](media/set-mdm-auth.png)

   MDM 기관을 Intune으로 설정했음을 나타내는 메시지가 표시됩니다.

### <a name="workflow-of-intune-administration-ui"></a>Intune 관리 UI의 워크플로
Android 또는 Apple 디바이스 관리를 사용하는 경우 Intune은 이러한 타사 서비스와 통합하는 디바이스 및 사용자 정보를 보내 해당 디바이스를 관리합니다.

데이터 공유 동의를 추가하는 시나리오는 다음과 같습니다.
- Android 회사 프로필을 사용합니다.
- Apple MDM 푸시 인증서를 사용하고 업로드.
- DEP(장비 등록 프로그램), School Manager, Volume Purchasing Program 등의 Apple 서비스 중 하나를 사용.

각 경우에 동의는 모바일 디바이스 관리 서비스의 실행과 관련하여 엄격히 적용됩니다. 예를 들어 IT 관리자는 등록을 위해 Google 또는 Apple 디바이스를 인증했는지 확인합니다. 새 워크플로가 가동될 때 어떤 정보가 공유되는지 알려주는 설명서는 다음 위치에 있습니다.
- [Intune이 Google에 보내는 데이터](https://aka.ms/Data-intune-sends-to-google)
- [Intune이 Apple에 보내는 데이터](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>핵심 고려 사항
새 MDM 기관으로 변경하면 디바이스가 서비스에 체크 인되어 동기화되기 전에 전환 시간(최대 8시간)이 필요할 수 있습니다. 등록된 디바이스가 변경 후에도 계속 관리되고 보호되도록 하려면 새 MDM 기관(하이브리드)에서 설정을 구성해야 합니다. 
- 디바이스는 새 MDM 기관(Intune 독립 실행형)의 설정이 디바이스의 기존 설정을 대체하도록 변경 후에도 서비스에 연결되어야 합니다.
- MDM 기관을 변경한 후 이전 MDM 기관(Intune 독립 실행형)의 일부 기본 설정(예: 프로필)이 최대 7일 동안 또는 디바이스가 서비스에 처음 연결될 때까지 디바이스에 남아 있습니다. 새 MDM 기관(하이브리드)에서 최대한 신속하게 앱 및 설정(정책, 프로필, 앱 등)을 구성하고, 기존의 등록된 디바이스를 가진 사용자가 포함된 사용자 그룹에 해당 설정을 배포하는 것이 좋습니다. MDM 기관에서 변경이 수행되고 디바이스가 서비스에 연결되는 즉시, 새 MDM 기관에서 새 설정을 수신되므로 관리 및 보호의 부재가 나타나지 않습니다.
- 동일한 디바이스 범주가 Intune 및 Configuration Manager에 있는 경우 디바이스에 대한 디바이스 범주 할당은 새 MDM 기관으로 전환한 후로 미뤄지지 않습니다. 디바이스 범주를 계속 사용하려면 MDM 기관을 변경하고 디바이스를 Configuration Manager 콘솔에 표시한 후에 마이그레이션된 디바이스가 적절한 컬렉션에 수동으로 추가되어야 합니다.
- 연결된 사용자가 없는 디바이스(일반적으로 iOS 디바이스 등록 프로그램 또는 대량 등록 시나리오가 있는 경우)는 새 MDM 기관으로 마이그레이션되지 않습니다. 이러한 디바이스의 경우 새 MDM 기관으로 이동하려면 지원 서비스에 문의해야 합니다.

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>MDM 기관을 Configuration Manager로 변경 준비

다음 정보를 검토하여 MDM 기관 변경을 준비하세요.
- MDM 기관을 변경하는 옵션을 사용하려면 Configuration Manager 버전 1610 이상이 있어야 합니다.
- 새 MDM 기관으로 변경한 후에 디바이스가 서비스에 연결되는 데 최대 8시간이 걸릴 수 있습니다.
- Configuration Manager 콘솔에서 Intune 구독을 설정할 때 사용할 Intune 독립 실행형에서 현재 관리되는 모든 사용자가 포함된 Configuration Manager 사용자 컬렉션을 만듭니다. 이 컬렉션은 사용자 및 해당 디바이스에 Configuration Manager 라이선스가 할당되고 MDM 기관 변경 후에 하이브리드 환경에서 관리되도록 하는 데 도움이 됩니다.
- IT 관리 사용자도 이 사용자 컬렉션에 포함되어야 합니다.  
- 변경 전에 MDM 기관은 Intune 관리 콘솔에서 **Microsoft Intune으로 설정**(독립 실행형)으로 표시됩니다.
- MDM 기관 변경 전에 Microsoft Intune 관리 콘솔에서 MDM 기관에는 **Microsoft Intune으로 설정**(독립 실행형 테넌트)이 표시되어야 합니다.
    > [!NOTE]    
    > MDM 기관에 **Intune 및 Office 365에서 관리**가 표시되면 Office 365 관리 MDM 디바이스는 MDM 기관을 **Configuration Manager**(하이브리드)로 변경하면 더 이상 관리되지 않습니다. MDM 기관을 변경하기 전에 해당 사용자에게 Intune 또는 Enterprise Mobility Suite에 대한 라이선스를 부여하는 것이 좋습니다.   

- [Microsoft Intune 관리 콘솔](http://manage.microsoft.com)에서 디바이스 등록 관리자 역할을 제거합니다. 자세한 내용은 [Intune에서 디바이스 등록 관리자 삭제](device-enrollment-manager-enroll.md#remove-device-enrollment-manager-permissions)를 참조하세요.
- 구성된 모든 디바이스 그룹 매핑을 해제합니다. 자세한 내용은 [Microsoft Intune에서 디바이스 그룹 매핑을 사용하여 디바이스 분류](device-group-mapping.md)를 참조하세요.
- MDM 기관을 변경하는 동안 최종 사용자에게 거의 영향을 주지 않아야 합니다. 그러나 사용자가 디바이스를 켜고 변경 즉시 서비스에 연결하도록 이러한 변경 사항을 사용자에게 알릴 수 있습니다. 이 예방 조치를 통해 최대한 많은 디바이스가 가능한 한 빨리 새 기관을 통해 서비스에 연결되고 등록됩니다.
- MDM 기관 변경 전에 Intune 독립 실행형을 사용하여 iOS 디바이스를 관리하는 경우 이전에 Intune에서 사용했던 동일한 APNs(Apple Push Notification Service) 인증서가 갱신되고 Configuration Manager(하이브리드)에서 테넌트를 다시 설정하는 데 사용되도록 해야 합니다.    

    > [!IMPORTANT]  
    > 하이브리드에 다른 APNs 인증서가 사용되면 이전에 등록한 모든 iOS 디바이스가 등록 취소되고 다시 등록하는 프로세스를 진행해야 합니다. MDM 기관 변경 전에 Intune에서 iOS 디바이스를 관리하는 데 사용된 APNs 인증서를 정확히 알고 있어야 합니다. Apple Push Certificates 포털(https://identity.apple.com))에 나열된 동일한 인증서를 찾고, 해당 Apple ID가 원래 APNs 인증서를 만드는 데 사용된 사용자를 식별한 후 새 MDM 기관 변경의 일부로 동일한 APNs 인증서를 갱신하는 데 이 인증서를 사용할 수 있도록 합니다.

## <a name="change-the-mdm-authority-to-configuration-manager"></a>MDM 기관을 Configuration Manager로 변경

1. Configuration Manager 콘솔에서 **관리** &gt; **개요** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 Intune 구독을 추가하도록 선택합니다.
2. Intune에서 MDM 기관을 설정할 때 사용했던 Intune 테넌트에 로그인하고 **다음**을 클릭합니다.
3. **내 MDM 기관을 Configuration Manager로 변경**을 선택하고 **다음**을 클릭합니다.
4. 새 하이브리드 MDM 기관에서 계속 관리할 모든 사용자를 포함하는 사용자 컬렉션을 선택합니다.
5. **다음** 을 클릭하여 마법사를 완료합니다. 이제 MDM 기관이 **Configuration Manager**로 변경됩니다.
6. 동일한 Intune 테넌트를 사용하여 [Microsoft Intune 관리 콘솔](http://manage.microsoft.com)에 로그인하고 MDM 기관이 **Configuration Manager로 설정**으로 변경되었는지 확인합니다.
7. MDM 기관을 구성 관리자로 변경한 후 [iOS 등록](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac) 및 [Android 등록](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-android)을 설정할 수 있습니다.
8. Configuration Manager 콘솔에서 새 MDM 기관(하이브리드)의 새로운 설정 및 앱을 구성하고 배포합니다.

다음 번에 디바이스가 서비스에 연결되면 새 MDM 기관과 동기화하여 새 설정을 받습니다.

## <a name="change-mdm-authority-to-office-365"></a>MDM 기관을 Office 365로 변경

기존 Intune 서비스 외에 Office 365 MDM을 활성화하려면 [https://protection.office.com](https://protection.office.com)으로 이동하여 **데이터 손실 방지** > **디바이스 보안 정책** > **관리되는 디바이스 목록 보기** > **시작하기**를 선택합니다.

자세한 내용은 [Office 365에서 MDM(모바일 디바이스 관리) 설정](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)을 참조하세요.

Office 365 MDM에서만 최종 사용자를 관리하려면 Office 365 MDM을 활성화한 후 할당된 Intune 및/또는 EMS 라이선스를 모두 제거합니다.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 인증서 만료 후 모바일 디바이스 정리

MDM 인증서는 모바일 디바이스가 Intune 서비스와 통신할 때 자동으로 갱신됩니다. 모바일 디바이스가 초기화되거나 일정 기간에 Intune 서비스와 통신하지 못한 경우에는 MDM 인증서가 갱신되지 않습니다. MDM 인증서가 만료되고 180일 후 Azure Portal에서 디바이스가 제거됩니다.

## <a name="remove-mdm-authority"></a>MDM 기관 제거

MDM 기관을 Unknown으로 다시 변경할 수 없습니다. MDM 기관은 Microsoft 서버에서 등록된 디바이스가 보고하는 포털(ConfigMGR, Azure Intune, Office 365 MDM)을 확인하는 데 사용됩니다.

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>MDM 기관 변경 후 예상되는 상황

- Intune 서비스에서 테넌트의 MDM 기관이 변경되었음을 감지하면 서비스에 체크 인하고 동기화하기 위해 등록된 모든 디바이스에 알림 메시지를 보냅니다(이 알림은 정기적으로 예약된 체크 인을 벗어남). 따라서 테넌트의 MDM 기관이 Intune 독립 실행형에서 하이브리드로 변경된 후에 전원이 켜져 있고 온라인 상태인 모든 디바이스는 서비스에 연결되고, 새 MDM 기관을 수신하고, 하이브리드에서 관리되게 됩니다. 이러한 서비스의 관리 및 보호가 중단되는 일은 없습니다.
- MDM 기관을 변경하는 동안(또는 직후에) 전원이 켜져 있고 온라인 상태인 디바이스의 경우에도 디바이스가 새 MDM 기관의 서비스에 등록되기까지 최대 8시간의 지연이 있습니다(예약된 다음 정기 체크 인 타이밍에 따라).    

  > [!IMPORTANT]    
  > MDM 기관을 변경하는 시간과 갱신된 APNs 인증서를 새 기관으로 업로드하는 시간 사이의 iOS 디바이스에 대한 새 디바이스 등록 및 디바이스 체크 인에 실패합니다. 따라서 MDM 기관을 변경한 후 가능한 한 빨리 APNs 인증서를 갱신하고 새 인증 기관에 업로드하는 것이 중요합니다.

- 사용자는 디바이스에서 서비스로의 체크 인을 수동으로 시작하여 새 MDM 기관을 빠르게 변경할 수 있습니다. 사용자는 회사 포털 앱을 사용하고 디바이스 준수 검사를 시작하여 이 변경을 쉽게 수행할 수 있습니다.
- MDM 기관이 변경되고, 디바이스가 체크 인되고 서비스와 동기화된 후 작업이 제대로 진행되는지 확인하려면 Configuration Manager 콘솔에서 디바이스를 찾아보세요. 이전에 Intune에서 관리되던 디바이스는 이제 Configuration Manager 콘솔에서 관리되는 디바이스로 표시됩니다.    
- MDM 기관 변경 동안 디바이스가 오프라인 상태일 때와 디바이스가 서비스로 체크 인될 때까지의 중간 기간이 있습니다. 이 중간 기간 동안 디바이스가 보호되고 제대로 작동되도록 하기 위해 최대 7일 동안(또는 디바이스가 새 MDM 기관에 연결되고 기존 설정을 덮어쓰는 새 설정을 받을 때까지) 디바이스에서 다음 프로필이 그대로 유지됩니다.
    - 전자 메일 프로필
    - VPN 프로필
    - 인증서 프로필
    - Wi-Fi 프로필
    - 구성 프로필
- 새 MDM 기관으로 변경한 후 Microsoft Intune 관리 콘솔의 준수 데이터가 정확히 보고될 때가지 최대 1주가 걸릴 수 있습니다. 그러나 Azure Active Directory 및 디바이스의 준수 상태는 정확하게 유지되므로 디바이스는 계속 보호됩니다.
- 기존 설정을 덮어쓰고 새로 사용하려는 설정은 이전 이름과 같은 이름이어야 합니다. 그렇지 않으면 디바이스에서 프로필 및 정책이 중복될 수 있습니다.    

  > [!TIP]    
  > 모범 사례는 MDM 기관 변경이 완료된 즉시, 모든 배포 뿐만 아니라 모든 관리 설정과 구성을 만드는 것입니다. 이렇게 하면 중간 기간 동안에도 디바이스가 보호되고 능동적으로 관리될 수 있습니다.

-  MDM 기관을 변경한 후 다음 단계를 수행하여 새 디바이스가 새 기관에 성공적으로 등록되었는지 확인합니다.   
    - 새 디바이스 등록
    - 새로 등록된 디바이스가 Configuration Manager 콘솔에 표시되어야 합니다.
    - 디바이스의 관리 콘솔에서 원격 잠금 등의 작업을 수행합니다. 성공한 경우 디바이스가 새 MDM 기관에서 관리되는 것입니다.
- 특정 디바이스에 문제가 있는 경우 등록을 취소했다가 다시 등록하여 가능한 한 빠른 시일 내에 디바이스가 새 기관에 연결되고 관리될 수 있도록 합니다.

## <a name="next-steps"></a>다음 단계

MDM 기관을 설정하면 [디바이스 등록](device-enrollment.md)을 시작할 수 있습니다.
