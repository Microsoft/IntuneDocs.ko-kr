---
title: 확장에 대한 앱 보호 정책
titleSuffix: Microsoft Intune
description: 이 항목에서는 확장에 대한 APP(앱 보호 정책)에 대해 설명합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f38f22d7aaf03f278fad86061aa8198c8e37f31f
ms.sourcegitcommit: b1ddc7f4a3d520b7d6755c7a423a46d1e2548592
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69655195"
---
# <a name="protecting-application-extensions"></a>애플리케이션 확장 보호

이 문서에서는 Microsoft Intune의 확장에 대한 앱 보호 정책에 대해 설명합니다.

## <a name="add-ins-for-outlook-app"></a>Outlook 앱용 추가 기능

Outlook 추가 기능을 사용하면 인기 있는 앱을 메일 클라이언트와 통합할 수 있습니다. Outlook용 추가 기능은 웹, Windows, Mac, Android 및 iOS용 Outlook에서 사용할 수 있습니다. Intune APP SDK 및 Intune 앱 보호 정책에는 Outlook용 추가 기능 관리를 위한 지원이 포함되어 있지 않으나 사용을 제한하는 다른 방법이 있습니다. 추가 기능은 Microsoft Exchange를 통해 관리되기 때문에 사용자는 Outlook 및 관리되지 않는 추가 기능 애플리케이션에서 데이터와 메시지를 공유할 수 있습니다(Exchange에서 사용자에 대해 추가 기능을 해제하지 않은 경우).

최종 사용자가 Outlook 추가 기능에 액세스하고 설치하는 것을 중지하려면(이는 모든 Outlook 클라이언트에 영향을 줌) Exchange 관리 센터에서 역할을 다음과 같이 변경해야 합니다.

- 사용자가 Office 스토어 추가 기능을 설치하지 못하도록 하려면 내 마켓플레이스 역할을 제거합니다.
- 사용자가 추가 기능을 테스트용으로 로드하지 못하도록 하려면 내 사용자 지정 앱 역할을 제거합니다.
- 사용자가 모든 추가 기능을 설치하지 못하도록 하려면 내 사용자 지정 앱 및 내 마켓플레이스 역할을 둘 다 제거합니다.

이러한 지침은 웹, Windows, Mac 및 모바일의 Outlook에서 Office 365, Exchange 2016 및 Exchange 2013에 적용됩니다.

- [Outlook용 추가 기능](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx)에 대해 자세히 알아보세요.
- [Outlook 앱용 추가 기능을 설치하고 관리할 수 있는 관리자 및 사용자를 지정하는 방법](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx)에 대해 자세히 알아보세요.

## <a name="linkedin-account-connections-for-microsoft-apps"></a>Microsoft 앱에 대한 LinkedIn 계정 연결

LinkedIn 계정 연결을 사용하면 특정 Microsoft 앱 내에서 LinkedIn 공개 프로필 정보를 볼 수 있습니다. 기본적으로 사용자는 LinkedIn과 Microsoft 직장 또는 학교 계정을 연결하여 추가적인 LinkedIn 프로필 정보를 보도록 선택할 수 있습니다. 

> [!NOTE]
> 미국 정부 고객과, 오스트레일리아, 캐나다, 중국, 프랑스, 독일, 인도, 대한민국, 영국, 일본, 남아공에서 호스팅되는 Exchange Online 메일박스를 사용하는 조직에서는 현재 LinkedIn 통합을 사용할 수 없습니다.

Intune SDK 및 Intune 앱 보호 정책에는 LinkedIn 계정 연결 관리 지원이 포함되어 있지 않지만 이 연결을 관리할 수 있는 다른 방법이 있습니다. 전체 조직에 대해 LinkedIn 계정 연결을 사용하지 않게 설정하거나, 조직 내 선별된 사용자 그룹에 대해 LinkedIn 계정 연결을 사용하도록 설정할 수 있습니다. 이 설정은 모든 플랫폼(웹, 모바일, 데스크톱)의 Office 365 앱 전체에서 LinkedIn 연결에 영향을 미칩니다. 다음과 같습니다.

- Azure Portal에서 테넌트에 대해 LinkedIn 계정 연결을 사용하거나 사용하지 않게 설정합니다. 
- 그룹 정책을 사용하여 조직의 Office 2016 앱에 대해 LinkedIn 계정 연결을 사용하거나 사용하지 않게 설정합니다.

LinkedIn 통합이 테넌트에 대해 사용하도록 설정된 경우 조직의 사용자가 LinkedIn과 Microsoft 직장 또는 학교 계정에 연결하면 다음과 같은 두 옵션이 제공됩니다. 

- 두 계정 간에 데이터를 공유하는 권한을 제공할 수 있습니다. 즉 LinkedIn 계정에게 Microsoft 직장 또는 학교 계정과 데이터를 공유하는 권한을 부여하고 Microsoft 직장 또는 학교 계정에도 LinkedIn 계정과 데이터를 공유하도록 하는 것입니다. LinkedIn과 공유하는 데이터는 온라인 서비스로 유지됩니다. 
- LinkedIn 계정에서만 Microsoft 직장 및 학교 계정에 대해 데이터를 공유하는 권한을 부여할 수 있습니다.

사용자가 Office 추가 기능을 통한 계정 간 데이터 공유에 동의한 경우 LinkedIn 통합에서는 기존 Microsoft Graph API를 사용합니다. LinkedIn 통합에서는 Office 추가 기능에 제공되는 API의 하위 집합만 사용하며 여러 제외를 지원합니다.


|Microsoft Graph 권한  |설명  |
|---------|---------|
|[사람](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)에 대한 읽기 권한     |앱이 로그인한 사용자와 관련한 사람의 점수 지정 목록을 읽을 수 있게 합니다. 이 목록은 로컬 연락처, 소셜 네트워크의 연락처 또는 조직의 디렉터리, 최근 연락이 있었던 사람(예: 이메일, Skype 등)을 포함할 수 있습니다.         |
|[일정](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)에 대한 읽기 권한     |앱이 사용자 일정의 이벤트를 읽을 수 있습니다. 회의에 대해 로그인한 사용자 일정, 일정의 시간, 위치, 참석자를 포함합니다.         |
|[사용자 프로필](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)에 대한 읽기 권한     |사용자가 응용 프로그램에 로그인할 수 있도록 하고, 앱에서 로그인한 사용자의 프로필을 읽을 수 있도록 합니다. 또한 앱이 로그인한 사용자에 대한 기본 회사 정보를 읽을 수 있습니다.         |
|Subscriptions     |이 범위는 사용할 수 없으며 아직 사용되지 않습니다. 여기에는 사용자의 조직이 Microsoft 앱 및 Office 365 등의 서비스에 제공하는 구독이 포함됩니다.         |
|Insights     |이 범위는 사용할 수 없으며 아직 사용되지 않습니다. Microsoft 서비스의 용도에 따라 로그인한 사용자의 계정에 연결된 관심 사항이 포함됩니다.         |

### <a name="learn-more"></a>자세한 정보

- [Microsoft 앱의 LinkedIn 정보 및기능](https://go.microsoft.com/fwlink/?linkid=850740)에 대해 알아봅니다.
- [Office 365 로드맵 페이지](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc)에서 LinkedIn 계정 연결 릴리스에 대해 알아봅니다. 
- [LinkedIn 계정 연결 구성](https://docs.microsoft.com/azure/active-directory/linkedin-integration)에 대해 알아봅니다.
- 사용자의 LinkedIn와 Microsoft 간에 공유되는 데이터에 대한 자세한 내용은 [회사 또는 학교의 Microsoft 애플리케이션에서의 LinkedIn](https://www.linkedin.com/help/linkedin/answer/84077)을 참조하세요.

