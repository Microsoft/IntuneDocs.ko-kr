---
title: 단계별 시나리오 - 모바일용 Microsoft Edge 배포
titleSuffix: Microsoft Intune
description: Microsoft 365 장치 관리 포털에서 보안 모바일용 Microsoft Edge를 배포하는 단계별 시나리오에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e86f3a469169e7a805cb3f56e570ba4d3a90e925
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585698"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>단계별 시나리오 - 모바일용 Microsoft Edge 배포 

이 [단계별 시나리오](~/fundamentals/guided-scenarios-overview.md)에 따라 조직의 iOS 또는 Android 디바이스에서 사용자에게 Microsoft Edge 앱을 할당할 수 있습니다. 이 앱을 할당하면 사용자가 회사 디바이스를 사용하여 콘텐츠를 원활하게 찾아볼 수 있습니다. 

Microsoft Edge를 사용하면 사용자가 작업 콘텐츠를 통합, 정렬 및 관리하는 데 도움이 되는 기본 제공 기능으로 웹의 혼란을 줄일 수 있습니다. Microsoft Edge 애플리케이션에서 회사 Azure AD 계정으로 로그인하는 iOS 및 Android 디바이스 사용자는 정의되는 작업 공간 **즐겨찾기** 및 웹 사이트 필터를 사용하여 미리 로드된 브라우저를 찾습니다.

> [!NOTE]
> 사용자가 iOS 또는 Android 디바이스를 등록하는 것을 차단한 경우 이 시나리오에서는 등록을 사용할 수 없으며 사용자는 직접 Edge를 설치해야 합니다.
Intune 정책을 통해 사용할 수 있는 Microsoft Edge 엔터프라이즈 기능은 다음과 같습니다. 

- **이중 ID** - 사용자는 검색을 위해 회사 계정뿐 아니라 개인 계정을 추가할 수 있습니다. Office 365 및 Outlook의 아키텍처 및 환경과 비슷한 두 ID는 완전히 분리됩니다. Intune 관리자는 회사 계정 내에서 보호된 검색 환경에 대해 원하는 정책을 설정할 수 있습니다. 
- **Intune 앱 보호 정책 통합** - 관리자는 이제 잘라내기, 복사 및 붙여넣기 제어, 화면 캡처 방지, 사용자가 선택한 링크가 다른 관리형 앱에서만 열리도록 하는 기능을 포함하여 앱 보호 정책의 대상을 Microsoft Edge로 지정할 수 있습니다.
- **Azure 애플리케이션 프록시 통합** - 관리자는 SaaS 앱 및 웹앱에 대한 액세스를 제어할 수 있으므로, 최종 사용자가 회사 네트워크에서 연결하든지, 인터넷에서 연결하든지 관계없이 브라우저 기반 앱이 Microsoft Edge 브라우저에서만 실행되도록 할 수 있습니다. 
- **즐겨찾기 및 홈페이지 바로 가기 관리** - 간편한 액세스를 위해 관리자는 최종 사용자가 회사 컨텍스트에 있을 경우 즐겨찾기 아래에 URL이 표시되도록 설정할 수 있습니다. 관리자는 회사 사용자가 Microsoft Edge에서 새 페이지 또는 새 탭을 열 때 기본 바로 가기로 표시될 홈페이지 바로 가기를 설정할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

- [MDM 기관을 Intune으로 설정](mdm-authority-set.md#set-mdm-authority-to-intune) - MDM(모바일 장치 관리) 기관 설정에 따라 디바이스를 관리하는 방법이 결정됩니다. IT 관리자가 MDM 기관을 설정해야 사용자가 관리를 위해 디바이스를 등록할 수 있습니다.
- 필요한 Intune 관리자 권한:
    - 관리형 앱 읽기, 만들기, 삭제 및 할당 권한
    - 모바일 앱 읽기, 만들기 및 할당 권한
    - 정책 세트 읽기, 만들기 및 할당 권한
    - 조직 읽기, 업데이트 권한

## <a name="step-1---introduction"></a>1단계 - 소개

**모바일용 Microsoft Edge 배포** 단계별 시나리오에 따라 선택된 iOS 및 Android 사용자 그룹을 위해 기본 Microsoft Edge 배포를 설정합니다. 이 배포에서는 **이중 ID** 및 **관리형 즐겨찾기 및 홈페이지 바로 가기**를 구현합니다. 또한 선택된 사용자가 등록한 디바이스에는 Intune을 통해 Microsoft Edge 앱이 자동으로 설치됩니다. 이 자동 설치는 다음을 포함한 모든 사용자 기반 등록 유형에서 수행됩니다. 
- 회사 포털 앱을 통한 iOS 등록 
- Apple Business Manager를 통한 iOS 사용자 선호도 등록 
- 회사 포털 앱을 통한 레거시 Android 등록 

이 단계별 시나리오에서는 Microsoft Edge 즐겨찾기에 표시되는 **MyApps**를 자동으로 사용하도록 설정하고 Intune 회사 포털 앱에 대해 설정한 것과 동일한 브랜딩을 사용하여 브라우저를 구성합니다. 

### <a name="what-you-will-need-to-continue"></a>계속해야 하는 작업
사용자에게 필요한 작업 공간 즐겨찾기 및 웹 브라우징에 필요한 필터에 대해 질문합니다. 계속하기 전에 다음 작업을 완료했는지 확인합니다.

- Azure AD 그룹에 사용자를 추가합니다. 자세한 내용은 [Create a basic group and add members using Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2102458)(Azure Active Directory를 사용하여 기본 그룹 만들기 및 멤버 추가)를 참조하세요.
- Intune에서 iOS 또는 Android 디바이스를 등록합니다. 자세한 내용은 [디바이스 등록](https://go.microsoft.com/fwlink/?linkid=2102547)을 참조하세요.
- Microsoft Edge에서 추가할 작업 공간 즐겨찾기 목록을 수집합니다.
- Microsoft Edge에서 적용할 웹 사이트 필터 목록을 수집합니다.

## <a name="step-2---basics"></a>2단계 - 기본 사항

이 단계에서는 새 Microsoft Edge 정책의 이름 및 설명을 입력해야 합니다. 할당 및 구성을 변경해야 하는 경우 나중에 이 정책을 참조할 수 있습니다. 이 단계별 시나리오에서는 iOS 디바이스용 Microsoft Edge iOS 앱과 Android 디바이스용 Microsoft Edge Android 앱을 둘 다 추가하고 할당합니다. 또한 이 단계에서는 이 앱에 대한 구성 정책을 만듭니다.

## <a name="step-3---configuration"></a>3단계 - 구성

이 단계에서 단계별 시나리오는 Intune을 통해 사용자에게 할당된 다른 모든 앱을 표시하며 Microsoft Intune 회사 포털 앱과 동일한 브랜딩을 공유하도록 Microsoft Edge를 구성합니다. **홈페이지 바로 가기 URL**, **관리형 책갈피** 목록 및 **차단된 URL** 목록을 사용하여 Microsoft Edge를 추가로 구성할 수 있습니다. 디바이스의 Microsoft Edge에서 새 탭을 열면 **홈페이지 바로 가기 URL**이 검색 창 아래에 첫 번째 아이콘으로 사용자에게 표시됩니다. **관리형 책갈피**는 사용자가 업무용으로 Microsoft Edge를 사용할 때 사용 가능한 즐겨찾기 URL 목록입니다. **차단된 URL**은 업무용인 경우 사용자에게 차단되는 사이트를 지정합니다. 다른 모든 사이트를 사용할 수 있습니다. 

## <a name="step-4---assignments"></a>4단계 - 할당

이 단계에서는 Microsoft Edge 모바일을 작업용으로 구성하도록 포함하려는 사용자 그룹을 선택할 수 있습니다. 또한 Microsoft Edge는 이 사용자가 등록한 모든 iOS 및 Android 디바이스에 설치됩니다.

## <a name="step-5---review--create"></a>5단계 - 검토 + 만들기

마지막 단계에서는 구성한 설정의 요약을 검토할 수 있습니다. 선택 항목을 검토한 후에는 **만들기**를 클릭하여 단계별 시나리오를 완료합니다. 

> [!NOTE]
> Edge는 구성을 수신하는 데 최대 12시간이 걸릴 수 있습니다. 자세한 내용은 [Microsoft Intune용 앱 구성 정책](~/apps/app-configuration-policies-overview.md)을 참조하세요.

> [!IMPORTANT]
> 단계별 시나리오가 완료되면 요약이 표시됩니다. 나중에 요약에 나열된 리소스를 수정할 수 있지만 이 리소스를 표시하는 테이블은 저장되지 않습니다.

## <a name="next-steps"></a>다음 단계

- Intune 앱 보호 정책 통합을 설정하여 Microsoft Edge 사용에 대한 보안을 강화합니다. 자세한 내용은 [Microsoft Edge에 대한 애플리케이션 보호 정책](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge)을 참조하세요.
- 포함할 인트라넷 사이트가 있는 경우 Azure 애플리케이션 프록시 통합을 사용하여 액세스를 보호하는 방법을 살펴봅니다. 자세한 내용은 [Microsoft Edge의 애플리케이션 프록시 설정 구성](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge)을 참조하세요.

