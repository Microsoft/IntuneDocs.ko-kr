---
title: 개인 데이터 감사, 내보내기 또는 삭제
description: 개인 데이터를 감사, 내보내기 또는 삭제하는 방법에 대해 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 659fdb9b67b941a27cef5a3680537f3eeb3bbbeb
ms.sourcegitcommit: 119962948045079022aa48f968dde3e961d7cd0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031692"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Intune에서 개인 데이터 감사, 내보내기 또는 삭제

Intune 관리자는 감사 로그를 사용하여 개인 데이터와 관련된 활동을 추적할 수 있습니다. 관리자는 개인 데이터를 내보내고 삭제할 수도 있습니다.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>개인 데이터 감사

감사 로그는 Microsoft Intune에서 변경 내용을 생성하는 활동 레코드를 테넌트 관리자에게 제공합니다. 감사 로그는 여러 관리 작업에 사용할 수 있으며, 일반적으로 생성, 업데이트(편집), 삭제 및 할당 작업에 사용할 수 있습니다. 감사 이벤트를 생성하는 원격 작업도 검토할 수 있습니다. 이러한 감사 로그에는 Intune에 디바이스가 등록된 사용자의 개인 데이터가 포함될 수 있습니다.  

보안상의 이유로 Intune은 사용자 및 디바이스 작업에 대한 감사 로그를 1년간 유지할 수 있습니다. 이러한 로그는 1년의 보존 기간이 지나면 자동으로 삭제됩니다.

감사 로그를 검토하려면 [Intune 활동에 대한 감사 로그](monitor-audit-logs.md)를 참조하세요. 

관리자는 감사 로그를 삭제할 수 없습니다.

이러한 감사 이벤트는 1년 동안 보존됩니다. 테넌트 관리자는 [지원 요청 양식](https://privacy.microsoft.com/en-US/privacy-questions?)을 사용하여 감사 로그를 요청할 수 있습니다.

## <a name="export-personal-data"></a>개인 데이터 내보내기

관리자는 계정, 서비스 데이터 및 관련 로그를 포함한 최종 사용자 개인 데이터를 내보냄으로써 데이터 주체 권한 요청을 준수할 수 있습니다. 데이터 주체에게 개인 데이터의 복사본을 제공할지 여부 또는 보류해야 할 합법적인 업무상 이유가 있는지 여부는 사용자와 사용자의 조직이 결정해야 합니다. 제공하기로 결정한 경우 실제 문서의 복사본, 적절하게 교정된 버전 또는 공유하기에 적합하다고 생각되는 부분의 스크린샷을 제공할 수 있습니다.

사용자의 개인 데이터를 내보내려면 다음을 사용할 수 있습니다. 
- Intune MDM 디바이스 블레이드를 사용하여 디바이스 목록을 내보냅니다. 디바이스 데이터를 직접 복사할 수도 있습니다.
- [Export-IntuneData.ps1 스크립트](https://aka.ms/intunedataexport).

## <a name="delete-end-user-personal-data"></a>최종 사용자 개인 데이터 삭제

개인 데이터를 Intune 관리 대상에서 제외하는 방법은 세 가지가 있습니다.
- Azure Active Directory에서 사용자 삭제
- 디바이스를 초기 설정으로 다시 설정
- 사용자 자체 제거

### <a name="delete-a-user-from-intune"></a>Intune에서 사용자 삭제

Intune에서 최종 사용자의 개인 데이터를 삭제하려면 관리자가 [AAD(Azure Active Directory)에서 사용자를 삭제](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user)해야 합니다. 사용자가 AAD에서 삭제되면(하드 삭제) Intune은 AAD에서 삭제 신호를 수신한 다음, Intune 서비스에서 해당 사용자의 모든 개인 데이터를 자동으로 삭제하기 시작합니다. 사용자의 정보는 제거 작업 후 30일 내에 Intune 서비스에서 삭제됩니다.

### <a name="reset-device-to-factory-settings"></a>디바이스를 초기 설정으로 다시 설정
초기 설정으로 다시 설정하면 모든 회사 및 개인 데이터와 설정이 원래 초기 설정으로 복원됩니다. 다음 직원에게 디바이스를 제공하는 데 유용합니다. 사용자 파일, 사용자 설치 애플리케이션 및 기본값이 아닌 설정이 제거되고, 이 데이터는 제거 작업 후 30일 내에 Intune 서비스에서 삭제됩니다.

### <a name="user-self-removal-from-intune-management"></a>Intune 관리 대상에서 사용자 자체 제외
사용자는 관리자의 도움 없이 [Android, Apple 또는 Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android) 개인 디바이스를 Intune 관리 대상에서 제외할 수 있습니다.   

### <a name="retire"></a>사용 중지
**사용 중지** 작업은 회사 애플리케이션과 같은 Intune 제공 데이터, Intune이 관리하는 앱 관련 데이터, 정책 설정 및 Intune을 통해 프로비전되는 이메일 프로필을 제거합니다. 이 작업은 디바이스에 사용자의 개인 데이터를 남깁니다.

### <a name="delete-a-tenant-from-microsoft-intune"></a>Microsoft Intune에서 테넌트 삭제

Intune 테넌트 고객이 Intune 계정을 취소하면 고객이 Intune 계정을 폐쇄한 후 180일 내에 모든 테넌트 데이터가 삭제됩니다. AAD 테넌트가 다른 Microsoft 엔터프라이즈 구독(Azure, Office 365)과 연결되어 있으면, Intune 고객 데이터만 삭제됩니다. AAD 테넌트 리소스는 다른 구독에서 사용할 수 있도록 유지됩니다. Intune 계정이 AAD 테넌트와 연결된 유일한 구독인 경우 테넌트가 삭제되고 모든 리소스와 고객 데이터도 삭제됩니다.

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>하이브리드 MDM(모바일 디바이스 관리) 환경에서 사용자 삭제
하이브리드 MDM(Configuration Manager와 통합된 Intune)이 있는 경우 사용자를 완전히 삭제하고 로컬 Active Directory, Configuration Manager 및 Intune에서 완전히 제거하려면 다음 작업을 순서대로 완료해야 합니다.

1. 로컬 AD(Active Directory)에서 사용자를 삭제합니다. 이렇게 하면 사용자가 Azure AD로 동기화되지 않고 Configuration Manager 검색으로 검색되지도 않습니다. 
2. Configuration Manager 콘솔에서 사용자를 삭제하여 Configuration Manager에서 사용자 및 관련 데이터를 제거합니다. 콘솔에서 **자산 및 준수** > **사용자**로 이동하여 삭제할 사용자를 마우스 오른쪽 단추로 클릭한 다음, **삭제**를 클릭합니다.
3. [AAD에서 사용자를 삭제](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user)하면 Azure Active Directory와 Intune 모두에서 사용자 및 관련 데이터가 동시에 제거됩니다. 사용자가 AAD에서 삭제되면(하드 삭제) Intune은 AAD에서 삭제 신호를 수신한 다음, Intune 서비스에서 해당 사용자의 모든 개인 데이터를 자동으로 삭제하기 시작합니다. 사용자의 정보는 제거 작업 후 30일 내에 Intune 서비스에서 삭제됩니다.

> [!Important]
>새 하이브리드 MDM 고객의 온보딩은 더 이상 사용되지 않습니다. 자세한 내용은 [하이브리드 모바일 디바이스 관리에서 Azure의 Intune으로 이동](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) 블로그 게시물을 참조하세요.

## <a name="next-steps"></a>다음 단계

Intune의 개인 데이터 [감사, 내보내기 또는 삭제](privacy-data-audit-export-delete.md) 방법에 대해 알아봅니다.
