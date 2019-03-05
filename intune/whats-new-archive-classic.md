---
title: Microsoft Intune 클래식 포털 아카이브의 새로운 기능
description: Microsoft Intune에 대한 새로운 기능 공지
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/08/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a56dcf0bb9c35bb12198537e6fdd1d2f72e3cfbb
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238866"
---
# <a name="whats-new-in-the-intune-classic-portal---previous-months"></a>Intune 클래식 포털의 새로운 기능 - 지난 달

[!INCLUDE [classic-portal](./includes/classic-portal.md)]

이 페이지에는 Intune 클래식 포털에 대해 [새로운 기능 페이지](whats-new.md)에서 이전에 발표되었던 새로운 기능과 공지가 나와 있습니다.

## <a name="april-2017"></a>2017년 4월

### <a name="new-capabilities"></a>새로운 기능

#### <a name="myapps-available-for-managed-browser---822308-822303--"></a>Managed Browser에 사용할 수 있는 MyApps <!--822308, 822303-->

Microsoft MyApps는 이제 Managed Browser 내에서 더 나은 지원을 제공합니다. 관리 대상으로 지정되지 않은 Managed Browser 사용자는 MyApps 서비스로 직접 연결되므로 관리자가 프로비전한 SaaS 앱에 액세스할 수 있습니다. Intune 관리 대상으로 지정된 사용자는 계속 기본 제공 Managed Browser 책갈피에서 MyApps에 액세스할 수 있습니다.

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Managed Browser 및 회사 포털에 대한 새 아이콘 <!--918433, 918431, 971473-->

Managed Browser 앱의 Android 및 iOS 버전 모두에서 아이콘이 업데이트됩니다. 새 아이콘은 업데이트된 Intune 배지를 포함하므로 EM+S(Enterprise Mobility + Security)의 다른 앱과 더 일관된 환경을 제공합니다. [Intune 앱 UI 페이지의 새로운 기능](whats-new-app-ui.md)에서 Managed Browser의 새 아이콘을 볼 수 있습니다.

회사 포털에서는 EM + S에 있는 다른 앱과의 일관성을 향상시키기 위해 Android, iOS 및 Windows 버전의 앱에 대한 업데이트된 아이콘도 받습니다. 이러한 아이콘은 4월부터 5월 말까지 여러 플랫폼에서 점진적으로 출시됩니다.

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 회사 포털의 로그인 진행률 표시기 <!--953374-->

Android 회사 포털 앱의 업데이트에는 사용자가 앱을 시작하거나 다시 시작할 때 로그인 진행률 표시기가 표시됩니다. 표시기에서는 "연결 중..."에서부터 "로그인 중...", "보안 요구 사항을 확인하는 중..."까지 새로운 상태를 진행한 후 사용자가 앱에 액세스할 수 있도록 허용합니다. [Intune 앱 UI 페이지의 새로운 기능](whats-new-app-ui.md)에서 Android용 회사 포털 앱의 새 화면을 볼 수 있습니다.

#### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>앱의 SharePoint Online 액세스 차단 <!-- 679339 -->

이제 앱 보호 정책이 적용되지 않은 앱이 [SharePoint Online](app-based-conditional-access-intune-create.md)에 액세스하지 않도록 차단하는 앱 기반 조건부 액세스 정책을 만들 수 있습니다. 앱 기반 조건부 액세스 시나리오에서는 Azure Portal을 사용하여 SharePoint Online에 액세스할 앱을 지정할 수 있습니다.

#### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>iOS용 회사 포털에서 iOS용 Outlook으로의 Single Sign-On 지원 <!--834012-->
사용자는 같은 디바이스에서 같은 계정으로 iOS용 회사 포털 앱에 로그인되어 있는 경우 더 이상 Outlook 앱에 로그인할 필요가 없습니다. 사용자는 Outlook 앱을 시작할 때 계정을 선택하여 자동으로 로그인할 수 있습니다. 이 기능을 다른 Microsoft 앱에 추가하는 작업도 진행하는 중입니다.

#### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>iOS용 회사 포털 앱에서 상태 메시지 개선 <!--744866-->
이제 iOS용 회사 포털 앱 내에서 더 구체적인 새 오류 메시지가 표시되므로 디바이스에서 진행되는 상황에 대한 정보에 더 쉽게 액세스할 수 있습니다. 기존에 이러한 오류 사례는 "회사 포털을 일시적으로 사용할 수 없음"이라는 일반 오류 메시지에 포함되었습니다. 또한 사용자가 인터넷에 연결되어 있지 않을 때 iOS에서 회사 포털을 시작하는 경우 이제 "인터넷 연결 없음"이라는 상태 표시줄이 홈페이지에 지속적으로 표시됩니다.

#### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Windows 10 회사 포털 앱에 대해 앱 설치 상태 개선 <!--676495-->

Windows 10 회사 포털 앱에서 시작되는 앱 설치에 대한 새로운 향상된 기능은 다음과 같습니다.
-   MSI 패키지에 대한 더 빠른 설치 진행 보고
-   Windows 10 1주년 업데이트 이상을 실행하는 디바이스의 최신 앱에 대한 더 빠른 설치 진행 보고
-   Windows 10 1주년 업데이트 이상을 실행하는 디바이스의 최신 앱 설치에 대한 새로운 진행률 표시줄

[Intune 앱 UI 페이지의 새로운 기능](whats-new-app-ui.md)에서 새로운 진행률 표시줄을 확인할 수 있습니다.

#### <a name="bulk-enroll-windows-10-devices----747607---"></a>Windows 10 디바이스 대량 등록 <!-- 747607 -->

이제 WCD(Windows 구성 디자이너)를 사용하여 Azure Active Directory 및 Intune에 대한 Windows 10 크리에이터스 업데이트를 실행하는 많은 디바이스를 연결할 수 있습니다. Azure AD 테넌트에 대한 [대량 MDM 등록](windows-bulk-enroll.md)을 사용하도록 설정하려면 Windows 구성 디자이너를 사용하여 Azure AD 테넌트에 디바이스를 연결하는 프로비전 패키지를 만들고, 이 패키지를 대량으로 등록 및 관리할 회사 소유 디바이스에 적용합니다. 패키지가 디바이스에 적용되면, 디바이스가 Azure AD에 연결되고 Intune에 등록되며 Azure AD 사용자가 로그온할 수 있는 준비를 갖추게 됩니다.  Azure AD 사용자는 이러한 디바이스에서 표준 사용자이며 할당된 정책 및 필수 앱을 수신합니다. 셀프 서비스 및 회사 포털 시나리오의 경우 이번에는 지원되지 않습니다.

### <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal--736542--"></a>Azure Portal의 Intune 공개 미리 보기의 새로운 기능<!--736542-->

2017년 초에 Microsoft에서는 전체 관리 환경을 Azure로 마이그레이션합니다. 이를 통해 Graph API를 사용하여 확장 가능한 최신 서비스 플랫폼에서 핵심 EMS 워크플로에 대한 강력한 통합 관리를 지원합니다.

새 평가판 테넌트에서는 이번 달에 Azure Portal에서 새 관리 환경의 공개 미리 보기를 표시하기 시작합니다. 미리 보기 상태에서는 기존 Intune 콘솔의 기능과 패리티가 반복적으로 제공됩니다.

Azure Portal의 관리 환경에서는 이미 발표된 새 그룹화 및 대상 지정 기능을 사용합니다. 따라서 기존 테넌트가 새 그룹화 환경으로 마이그레이션될 때 사용자도 마이그레이션되어 테넌트에 새 관리 환경의 미리 보기가 표시됩니다. 그 동안 테넌트가 마이그레이션될 때까지 새 기능을 테스트하거나 살펴보려는 경우 새 Intune 평가판 계정에 등록하거나 [새 설명서](whats-new.md)를 살펴보세요.

Azure의 Intune 미리 보기에 대한 새로운 기능은 [여기](whats-new.md)에서 찾을 수 있습니다.

### <a name="notices"></a>알림

#### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 등록 시나리오에 대한 직접 액세스 <!--951869-->

2017년 1월 이후에 만든 Intune 계정은 Azure Preview 포털에서 디바이스 등록 워크로드를 사용하여 Apple 등록 시나리오에 직접 액세스할 수 있습니다. 이전에는 Azure Portal의 링크를 통해서만 Apple 등록 미리 보기에 액세스할 수 있었습니다. 2017년 1월 이전에 만든 Intune 계정은 일회성 마이그레이션을 수행해야 Azure에서 이러한 기능을 사용할 수 있습니다. 마이그레이션 일정은 아직 공지되지 않았지만 가능한 한 빠른 시일 내에 세부 정보가 제공될 예정입니다. 기존 계정에서 미리 보기에 액세스할 수 없는 경우 평가판 계정을 만들어 새로운 경험을 테스트해 보는 것이 좋습니다.

#### <a name="whats-coming-for-appx-in-intune-in-the-azure-portal----1000270---"></a>Azure Portal의 Intune에서 Appx에 대한 향후 변경 사항 <!-- 1000270 -->

Azure Portal의 Intune으로 마이그레이션하는 과정의 일환으로 appx의 다음 세 가지 사항을 변경합니다.

1. MDM에 등록된 디바이스에만 배포할 수 있는 새 appx 앱 유형을 Intune 콘솔에 추가합니다.
2. Intune PC 에이전트를 통해 관리되는 PC만 대상으로 할 수 있도록 기존 appx 앱 유형의 용도를 변경합니다.
3. 마이그레이션과 함께 기존 appx를 모두 MDM appx로 변환합니다.

##### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?

Intune PC 에이전트를 통해 관리되는 디바이스의 기존 배포에는 아무런 영향을 주지 않습니다. 그러나 마이그레이션 후에는 이전에 대상으로 하지 않았던 Intune PC 에이전트를 통해 관리되는 새 디바이스에 마이그레이션된 appx를 배포할 수 없습니다.

##### <a name="what-action-do-i-need-to-take"></a>수행해야 하는 작업

마이그레이션 후 새 PC 배포를 수행하려면 appx를 PC appx로 다시 업로드해야 합니다. 자세한 내용은 Intune 지원 팀 블로그에서 [Appx changes in Intune in the Azure portal](https://aka.ms/appxchange)(Azure Portal의 Intune에서 Appx 변경 사항)을 참조하세요.  

#### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure Portal에서 대체되는 관리 역할

Intune 클래식 포털(Silverlight)에서 사용된 기존 MAM(모바일 애플리케이션 관리) 관리 역할(기여자, 소유자 및 읽기 전용)은 Intune Azure Portal에서 새로운 RBAC(역할 기반 관리 제어)의 전체 집합으로 대체됩니다. Azure Portal로 마이그레이션한 후에 이러한 새 관리 역할에 관리자를 다시 할당해야 합니다. RBAC 및 새 역할에 대한 자세한 내용은 [Microsoft Intune에 대한 역할 기반 액세스 제어](role-based-access-control.md)를 참조하세요.

### <a name="whats-coming"></a>향후 예정 사항

#### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>모든 플랫폼에 대해 회사 포털 앱 전체에서 로그인 환경 개선됨 <!--User Story 1132123-->

Android, iOS 및 Windows용 Intune 회사 포털 앱에 대한 로그인 환경을 개선하게 될 향후 몇 개월 내에 제공될 변경이 있음을 알려드립니다. Azure AD에서 이 변경 내용을 적용할 경우 회사 포털 앱에 대한 모든 플랫폼에서 새로운 사용자 환경이 자동으로 나타나게 됩니다. 또한 사용자가 이제 생성된 일회용 코드를 사용하여 다른 디바이스에서 회사 포털에 로그인할 수도 있습니다. 이 기능은 사용자가 자격 증명 없이 로그인해야 할 경우에 특히 유용합니다.

이전 로그인 환경, 자격 증명을 사용하는 새 로그인 환경, 그리고 다른 디바이스로부터의 새 로그인 환경에 대한 스크린샷은 [앱 UI의 새로운 기능](whats-new-app-ui.md) 페이지에서 볼 수 있습니다.

#### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>변경 계획: Intune의 Intune 파트너 포털 환경 변화 <!-- 1050016 -->

2017년 5월 중순의 서비스 업데이트부터 manage.microsoft.com에서 Intune 파트너 페이지가 제거됩니다.  

파트너 관리자인 경우 더 이상 Intune 파트너 페이지에서 고객을 대신하여 작업을 보고 수행할 수 없지만, 대신 Microsoft의 다른 두 파트너 포털 중 하나에서 로그인해야 합니다.

[Microsoft 파트너 센터](https://partnercenter.microsoft.com/) 및 [Microsoft Office 365 파트너 관리 센터](https://portal.office.com/)를 통해, 관리하는 고객 계정에 로그인할 수 있습니다. 파트너로서 앞으로는 이러한 사이트 중 하나를 사용하여 고객을 관리하세요.


#### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple의 Application Transport Security 업데이트 요구 <!--748318-->

Apple에서는 ATS(Application Transport Security)에 대한 특정 요구 사항을 적용할 것이라고 발표했습니다. ATS는 HTTPS를 통한 모든 앱 통신에서 보다 엄격한 보안을 적용하는 데 사용됩니다. 이 변경 사항은 iOS 회사 포털 앱을 사용하는 Intune 고객에게 영향을 줍니다.

새로운 ATS 요구 사항을 적용하는 Apple TestFlight 프로그램을 통해 iOS용 회사 포털 앱 버전을 제공했습니다. ATS 준수를 테스트하는 데 이 버전을 사용해 보려면 이름, 성, 메일 주소, 회사 이름을 포함하여 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>에 메일을 보내 주세요. 자세한 내용은 [Intune 지원 블로그](https://aka.ms/compportalats)를 참조하세요.

## <a name="march-2017"></a>2017년 3월

### <a name="new-capabilities"></a>새로운 기능

#### <a name="support-for-skycure"></a>Skycure에 대한 지원

이제 Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Skycure에서 수행한 위험 평가에 따라 조건부 액세스를 사용하여 회사 리소스에 대한 모바일 디바이스의 액세스를 제어할 수 있습니다. 위험은 다음을 비롯하여 Skycure를 실행하는 디바이스에서 수집된 원격 분석에 따라 평가됩니다.

- 물리적 방어
- 네트워크 방어
- 애플리케이션 방어
- 취약성 방어

Intune 디바이스 준수 정책을 통해 사용하도록 설정된 Skycure(Symantec Endpoint Protection Mobile) 위험 평가에 따라 EMS 조건부 액세스 정책을 구성할 수 있습니다. 이러한 정책을 사용하여 검색된 위협에 따라 회사 리소스에 대한 비규격 디바이스 액세스를 허용하거나 차단할 수 있습니다. 자세한 내용은 [Symantec Endpoint Protection Mobile Connector](skycure-mobile-threat-defense-connector.md)를 참조하세요.

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android용 회사 포털 앱의 새 사용자 환경 <!--621622-->

Android용 회사 포털 앱이 최신 모양과 느낌 및 더 나은 사용자 경험을 위해 사용자 인터페이스를 업데이트할 예정입니다. 중요한 업데이트는 다음과 같습니다.

- 색: 회사 포털 탭 머리글이 IT 관리자가 정의한 브랜드 색으로 지정됩니다.
- 앱: **앱** 탭에서 **추천 앱** 및 **모든 앱** 단추가 업데이트됩니다.
- Search: **앱** 탭에서 **검색** 단추가 부동 작업 단추입니다.
- 앱 탐색: 보다 쉽게 탐색할 수 있도록 **모든 앱** 보기에 탭으로 구분된 **추천**, **전체** 및 **범주** 보기가 표시됩니다.
- 지원: 가독성 향상을 위해 **내 디바이스** 및 **IT 담당자** 탭이 업데이트됩니다.

이러한 변경에 대한 자세한 내용은 [Intune 최종 사용자 앱 UI 업데이트](whats-new-app-ui.md)를 참조하세요.

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>관리되지 않은 디바이스에서 할당된 앱에 액세스 가능 <!--664691-->

회사 포털 웹 사이트 디자인 변경의 일환으로, iOS 및 Android 사용자가 자기에게 할당된 앱을 관리되지 않는 디바이스에 "등록 없이 사용 가능"으로 설치할 수 있습니다. 사용자는 Intune 자격 증명을 사용하여 회사 포털 웹 사이트에 로그인하고 자기에게 할당된 앱의 목록을 볼 수 있습니다. "등록 없이 사용 가능" 앱의 앱 패키지는 회사 포털 웹 사이트를 통해 다운로드할 수 있습니다. 설치하려면 등록이 필요한 앱은 사용자가 앱을 설치하려 할 때 등록하라는 메시지가 표시되므로 이 변경의 영향을 받지 않습니다.

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Windows 10 회사 포털용 서명 스크립트 <!--941642-->

Windows 10 회사 포털 앱을 다운로드하거나 사이드로드해야 하는 경우 스크립트를 사용하여 조직의 앱 서명 프로세스를 단순화하고 간소화할 수 있습니다.   스크립트 및 사용 지침을 다운로드하려면 TechNet 갤러리에서 [ Microsoft Intune Signing Script for Windows 10 Company Portal(Windows 10 회사 포털용 Microsoft Intune 서명 스크립트)](https://aka.ms/win10cpscript)을 참조하세요. 이 알림에 대한 자세한 내용은 Intune 지원 팀 블로그에서 [Updating your Windows 10 Company Portal app(Windows 10 회사 포털 앱 업데이트)](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/)을 참조하세요.


### <a name="notices"></a>알림

#### <a name="support-for-ios-103"></a>iOS 10.3에 대한 지원

iOS 10.3 릴리스가 2017년 3월 27일에 iOS 사용자에게 배포되기 시작했습니다. 기존의 모든 Intune MDM 및 MAM 시나리오는 최신 버전의 Apple OS와 호환됩니다. 현재 iOS 디바이스 관리에 사용할 수 있는 기존의 모든 Intune 기능은 사용자가 디바이스 및 앱을 iOS 10.3으로 업그레이드할 때도 계속 작동할 것으로 예상합니다.

현재 공유할 만한 알려진 문제는 없습니다. iOS 10.3 관련 문제가 발생하는 경우 [Intune 지원 팀](get-support.md)에 연락해 주시기 바랍니다.

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>중국에 거주하는 Android 사용자에 대한 지원 향상 <!--720444-->

중국에는 Google Play 스토어를 사용할 수 없으므로 Android 디바이스 사용자는 중국 마켓플레이스에서 앱을 다운로드해야 합니다. 회사 포털은 중국의 Android 사용자가 현지 앱 스토어에서 회사 포털 및 Outlook 앱을 다운로드하도록 리디렉션하여 이 워크플로를 지원합니다. 이는 모바일 장치 관리 및 모바일 애플리케이션 관리에 대한 조건부 액세스 정책이 설정된 경우 사용자 환경을 개선합니다. Android용 회사 포털 및 Outlook 앱은 다음과 같은 중국 앱 스토어에서 사용할 수 있습니다.

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>모범 사례: 회사 포털 앱을 최신으로 유지하기<!--879465-->

2016년 12월 Microsoft는 iOS, Android, Windows 8.1 이상 또는 Windows Phone 8.1 이상 디바이스를 등록할 때 사용자 그룹에 대한 MFA(다단계 인증) 적용을 사용하도록 설정한 업데이트를 릴리스했습니다. 이 기능은 Android(v5.0.3419.0 이상) 및 iOS(v2.1.17 이상)에 대한 특정 기준 버전의 회사 포털 앱 없이는 작동할 수 없습니다.

Microsoft는 지원되는 모든 플랫폼에서 콘솔 및 회사 포털 앱에 새로운 기능을 추가함으로써 지속적으로 Intune을 개선하고 있습니다. 결과적으로, Microsoft는 현재 버전의 회사 포털 앱에서 발견되는 문제에 대해서만 수정 사항을 릴리스합니다. 따라서 최상의 사용자 환경을 위해 최신 버전의 회사 포털 앱을 사용하는 것이 좋습니다.

>[!Tip]
> 사용자에게 해당 앱 스토어에서 자동으로 앱을 업데이트하도록 디바이스를 설정하게 요청하세요. Android 회사 포털 앱을 네트워크 공유에서 사용 가능하도록 한 경우에는 [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=49140)에서 최신 버전을 다운로드할 수 있습니다.

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>iOS 및 Android에서 Microsoft Teams의 MAM 활성화

Microsoft는 Microsoft Teams의 일반적인 가용성을 발표했습니다. iOS 및 Android용 업데이트된 Microsoft Teams 앱은 이제 Intune MAM(모바일 앱 관리) 기능이 활성화되었습니다. 따라서 대화 및 회사 데이터를 보호하면서도 팀원들이 여러 디바이스에서 자유롭게 작업하도록 할 수 있습니다. 자세한 내용은 Enterprise Mobility + Security 블로그에서 [Microsoft Teams 알림](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/)을 참조하세요.


## <a name="february-2017"></a>2017 년 2월

### <a name="new-capabilities"></a>새로운 기능

### <a name="modernizing-the-company-portal-website---753980--"></a>회사 포털 웹 사이트 현대화 <!--753980-->
회사 포털 웹 사이트는 관리 디바이스가 없는 사용자를 대상으로 하는 앱을 지원합니다. 웹 사이트는 다른 Microsoft 제품과 마찬가지로 새로운 고대비 색 구성표, 동적 그림 및 "햄버거 메뉴"를 사용합니다. ![이제 회사 포털 웹 사이트 왼쪽 상단에 추가된 햄버거 메뉴의 작은 이미지에는](./media/CP_hamburger_menu.png).

### <a name="notices"></a>알림

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>iOS 디바이스의 그룹 또는 정책에 대한 업데이트에는 그룹 마이그레이션이 필요 없음 <!--898837-->
회사 디바이스 등록 프로필에서 미리 할당된 모든 Intune 디바이스 그룹마다, Azure Active Directory 디바이스 그룹으로 마이그레이션하는 동안 회사 디바이스 등록 프로필 이름을 기반으로 AAD에 동적인 디바이스 그룹이 생성됩니다. 그러면 디바이스가 등록될 때 자동으로 그룹화되어 원래 Intune 그룹과 동일한 정책 및 앱을 받습니다.

테넌트가 그룹화 및 타기팅을 위한 마이그레이션 프로세스에 들어가고 나면, Intune은 회사 디바이스 등록 프로필을 통해 타기팅된 Intune 그룹에 맞는 동적 AAD 그룹을 자동으로 생성합니다. Intune 관리자가 타기팅된 Intune 그룹을 삭제해도 해당되는 동적 AAD 그룹은 삭제되지 않습니다. 그룹의 구성원과 동적 쿼리는 지워지지만, 그룹 자체는 IT 관리자가 AAD 포털을 통해 제거할 때까지 남습니다.

마찬가지로 IT 관리자가 회사 디바이스 등록 프로필을 통해 타기팅되는 Intune 그룹이 무엇인지 변경할 경우, Intune에서는 새 프로필 할당을 반영한 새 동적 그룹을 생성하지만 이전 할당에 대해 생성된 동적 그룹을 제거하지는 않습니다t.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Windows 설정을 통해 Windows 데스크톱 디바이스 관리를 기본값으로 설정<!--663050-->
Windows 10 데스크톱을 등록하는 기본 동작이 바뀌고 있습니다. 새 등록은 PC 에이전트를 통해서가 아니라 일반적인 MDM 에이전트 등록 흐름을 따릅니다. 회사 포털 웹 사이트는 Windows 10 데스크톱 사용자에게 모바일 디바이스로 Windows 10 데스크톱 컴퓨터를 추가하는 과정을 안내하는 등록 지침을 제공합니다. 현재 등록된 PC에는 영향을 주지 않으며, [원하는 경우](manage-windows-pcs-with-microsoft-intune.md) 조직에서 PC 에이전트를 사용하여 Windows 10 데스크톱을 계속 관리할 수 합니다.

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>선택적 초기화에 대한 모바일 앱 관리 지원 향상 <!--581242-->
"앱 데이터를 초기화하기 전의 오프라인 간격" 정책으로 인해 데이터가 자동으로 제거되는 경우 회사 또는 학교 데이터에 다시 액세스하는 방법에 대한 추가 지침이 최종 사용자에게 제공됩니다.<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS용 회사 포털 링크가 앱 내에서 열림<!--665954-->
설명서 및 앱에 대한 링크를 포함하여 iOS용 회사 포털 앱 내의 링크는 Safari의 앱 내 보기를 사용하여 회사 포털 앱에서 직접 열립니다. 이 업데이트는 1월에 서비스 업데이트에서 별도로 제공됩니다.

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows 디바이스의 새 MDM 서버 주소 <!--893007-->
Windows 및 Windows Phone 사용자가 MDM 서버 주소 입력 메시지가 표시되었을 때 __manage.microsoft.com__을 입력할 경우 디바이스 등록이 실패합니다. MDM 서버 주소가 __manage.microsoft.com__에서 __enrollment.manage.microsoft.com__으로 변경됩니다. 사용자에게 Windows 또는 Windows Phone 디바이스를 등록하는 동안 MDM 서버 주소를 입력하라는 메시지가 표시되면 __enrollment.manage.microsoft.com__을 사용하라고 알리세요. CNAME 설정을 변경할 필요는 없습니다. 이 변경에 대한 자세한 내용을 보려면 [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange)를 방문하세요.

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android용 회사 포털 앱의 새 사용자 환경 <!--621622-->
3월부터, Android용 회사 포털 앱이 [material design guidelines](https://material.io/guidelines/material-design/introduction.html)(재료 디자인 지침)에 따라 모양과 느낌이 더욱 세련되어집니다. 이러한 향상된 사용자 환경에는 다음이 포함됩니다.

* __색__: 탭 헤더에 사용자 지정 색상표에 따라 색을 표시할 수 있습니다.
* __인터페이스__: 앱 탭에서 추천 앱 및 모든 앱 단추가 업데이트되었습니다. 검색 단추는 이제 부동 작업 단추입니다.
* __탐색__: 모든 앱은 쉽게 탐색할 수 있도록 추천, 전체 및 범주 탭으로 구분된 뷰를 표시합니다.
* __서비스__: 내 디바이스 및 IT 담당자 탭 가독성을 개선했습니다.

[UI 업데이트 페이지](whats-new-app-ui.md)에서 이전 및 이후 이미지를 찾을 수 있습니다.

### <a name="associate-multiple-management-tools-with-the-microsoft-store-for-business---926135--"></a>비즈니스용 Microsoft 스토어와 여러 관리 도구 연결<!--926135-->
둘 이상의 관리 도구를 사용하여 비즈니스용 Microsoft 스토어 앱을 배포하는 경우, 이전에는 그 중에 하나만 비즈니스용 Microsoft 스토어에 연결할 수 있었습니다. 이제 Intune 및 Configuration Manager와 같은 여러 관리 도구를 스토어에 연결할 수 있습니다. 자세한 내용은 [Microsoft Intune을 사용하여 비즈니스용 Microsoft 스토어에서 구입한 앱 관리](windows-store-for-business.md)를 참조하세요.

## <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal---736542--"></a>Azure Portal의 Intune 공개 미리 보기의 새로운 기능 <!--736542-->

2017년 초에 Microsoft에서는 전체 관리 환경을 Azure로 마이그레이션합니다. 이를 통해 Graph API를 사용하여 확장 가능한 최신 서비스 플랫폼에서 핵심 EMS 워크플로에 대한 강력한 통합 관리를 지원합니다.

새 평가판 테넌트에서는 이번 달에 Azure Portal에서 새 관리 환경의 공개 미리 보기를 표시하기 시작합니다. 미리 보기 상태에서는 기존 Intune 콘솔의 기능과 패리티가 반복적으로 제공됩니다.

Azure Portal의 관리 환경에서는 이미 발표된 새 그룹화 및 대상 지정 기능을 사용합니다. 따라서 기존 테넌트가 새 그룹화 환경으로 마이그레이션될 때 사용자도 마이그레이션되어 테넌트에 새 관리 환경의 미리 보기가 표시됩니다. 그 동안 테넌트가 마이그레이션될 때까지 새 기능을 테스트하거나 살펴보려는 경우 새 Intune 평가판 계정에 등록하거나 [새 설명서](whats-new.md)를 살펴보세요.

Azure의 Intune 미리 보기에 대한 새로운 기능은 [여기](whats-new.md)에서 찾을 수 있습니다.

## <a name="january-2017"></a>2017년 1월

### <a name="new-capabilities"></a>새로운 기능

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>등록과 상관없는 MAM에 대한 콘솔 내 보고서<!--677961-->
등록된 디바이스 및 등록되지 않은 디바이스 모두에 대한 새 앱 보호 보고서가 추가되었습니다. [intune을 사용하여 모바일 앱 관리 정책을 모니터링](app-protection-policies-monitor.md)할 수 있는 방법을 자세히 알아보세요.

#### <a name="android-711-support---694397--"></a>Android 7.1.1 지원<!--694397-->
Intune은 이제 Android 7.1.1을 완벽하게 지원하고 관리합니다.

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>iOS 디바이스가 비활성 상태이거나, 관리 콘솔에서 통신할 수 없는 경우 문제 해결 <!--unknown-->
사용자 디바이스에서 Intune과의 연결이 끊기는 경우 회사 리소스에 대한 액세스 권한을 다시 얻도록 새로운 문제 해결 단계를 제공할 수 있습니다. [디바이스가 비활성 상태이거나 관리 콘솔이 디바이스와 통신할 수 없음](troubleshoot-device-enrollment-in-intune.md#devices-are-inactive-or-the-admin-console-cant-communicate-with-them)을 참조하세요.

### <a name="notices"></a>알림

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Windows 설정을 통해 Windows 데스크톱 디바이스 관리를 기본값으로 설정<!--663050-->
Windows 10 데스크톱을 등록하는 기본 동작이 바뀌고 있습니다. 새 등록은 PC 에이전트를 통해서가 아니라 일반적인 MDM 에이전트 등록 흐름을 따릅니다.

회사 포털 웹 사이트는 Windows 10 데스크톱 사용자에게 모바일 디바이스로 Windows 10 데스크톱 컴퓨터를 추가하는 과정을 안내하는 등록 지침을 제공합니다. 현재 등록된 PC에는 영향을 주지 않으며, [원하는 경우](manage-windows-pcs-with-microsoft-intune.md) 조직에서 PC 에이전트를 사용하여 Windows 10 데스크톱을 계속 관리할 수 합니다.

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>선택적 초기화에 대한 모바일 앱 관리 지원 향상 <!--581242-->
"앱 데이터를 초기화하기 전의 오프라인 간격" 정책으로 인해 데이터가 자동으로 제거되는 경우 회사 또는 학교 데이터에 다시 액세스하는 방법에 대한 추가 지침이 최종 사용자에게 제공됩니다.<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS용 회사 포털 링크가 앱 내에서 열림<!--665954-->
설명서 및 앱에 대한 링크를 포함하여 iOS용 회사 포털 앱 내의 링크는 Safari의 앱 내 보기를 사용하여 회사 포털 앱에서 직접 열립니다. 이 업데이트는 1월에 서비스 업데이트에서 별도로 제공됩니다.

#### <a name="modernizing-the-company-portal-website---753980--"></a>회사 포털 웹 사이트 현대화 <!--753980-->
2월부터 회사 포털 웹 사이트는 관리 디바이스가 없는 사용자를 대상으로 하는 앱을 지원합니다. 웹 사이트는 다른 Microsoft 제품과 마찬가지로 새로운 고대비 색 구성표, 동적 그림 및 "햄버거 메뉴"를 사용합니다. ![회사 포털 웹 사이트 햄버거 메뉴](./media/CP_hamburger_menu.png).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>앱 보호 정책에 대한 새 설명서<!--583398-->
iOS 및 Android 앱에서 Intune 앱 래핑 도구 또는 Intune 앱 SDK를 사용하여 앱 보호 정책(MAM 정책이라고도 함)을 사용하도록 설정하려는 관리자 및 앱 개발자를 위한 설명서를 업데이트했습니다.

다음 문서가 업데이트되었습니다.

* [Microsoft Intune으로 모바일 애플리케이션 관리용 앱을 준비하는 방법 결정](apps-prepare-mobile-application-management.md)
* [Intune 앱 래핑 도구를 사용하여 모바일 애플리케이션 관리를 위해 iOS 앱 준비](app-wrapper-prepare-ios.md)
* [Microsoft Intune 앱 SDK 시작](app-sdk-get-started.md)
* [iOS용 Intune 앱 SDK 개발자 가이드](app-sdk-ios.md)

다음 문서가 문서 라이브러리에 새로 추가되었습니다.

* [Intune 앱 SDK Cordova 플러그 인](app-sdk-cordova.md)
* [Intune 앱 SDK Xamarin 구성 요소](app-sdk-xamarin.md)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>iOS에서 회사 포털을 시작할 경우의 진행률 표시줄 <!--665978-->
iOS용 회사 포털은 수행되는 로드 프로세스에 대한 정보를 사용자에게 제공하는 시작 화면의 진행률 표시줄을 도입하기로 했습니다. 진행률 표시줄이 단계적으로 회전자를 바꿀 예정입니다. 즉, 일부 사용자에게는 새로운 진행률 표시줄이 표시되지만 다른 사용자에게는 계속 회전자가 표시됩니다.

## <a name="december-2016"></a>2016년 12월

### <a name="public-preview-of-intune-in-the-azure-portal--736542--"></a>Azure Portal의 Intune 공개 미리 보기<!--736542-->
2017년 초에 Microsoft에서는 전체 관리 환경을 Azure로 마이그레이션합니다. 이를 통해 Graph API를 사용하여 확장 가능한 최신 서비스 플랫폼에서 핵심 EMS 워크플로에 대한 강력한 통합 관리를 지원합니다. 모든 Intune 테넌트에 대해 이 포털을 일반 공급하기 전에, 이번 달 후반부터 일부 테넌트에게 이 새로운 관리 환경의 미리 보기 제공을 개시할 것임을 알려 드립니다.

Azure Portal의 관리 환경에서는 이미 발표된 새 그룹화 및 대상 지정 기능을 사용합니다. 따라서 기존 테넌트가 새 그룹화 환경으로 마이그레이션될 때 사용자도 마이그레이션되어 테넌트에 새 관리 환경의 미리 보기가 표시됩니다. Azure Portal에서 Microsoft Intune용으로 제공되는 기능에 대한 자세한 내용을 [새로운 설명서](/intune/what-is-intune)에서 확인해 보시기 바랍니다.

__Azure Portal의 공개 미리 보기에 통신 지출 관리 통합__ <!--747605--> 이제 Azure Portal 내에서 타사 TEM(통신 지출 관리) 서비스와의 통합 미리 보기를 시작합니다. Intune을 사용하여 국내 및 로밍 데이터 사용량을 제한할 수 있습니다. 우선 [Saaswedo](http://www.saaswedo.com/)와의 통합으로 시작합니다. 평가판 테넌트에 이 기능을 사용하려면 [Microsoft 지원에 문의](get-support.md)하세요.

### <a name="new-capabilities"></a>새로운 기능

__모든 플랫폼에서 다단계 인증__<!--747590--> 이제 선택한 사용자 그룹이 Azure 관리 포털에서 iOS, Android, Windows 8.1+ 또는 Windows Phone 8.1+ 장치를 등록할 때 Azure Active Directory의 Microsoft Intune 등록 애플리케이션에서 MFA(Multi-Factor Authentication)를 구성하여 해당 사용자 그룹에 MFA를 적용할 수 있습니다.

__모바일 디바이스 등록을 제한하는 기능__<!--747596--> Intune은 등록할 수 있는 모바일 디바이스 플랫폼을 제어하는 새로운 등록 제한을 추가합니다. Intune은 모바일 디바이스 플랫폼을 iOS, macOS, Android, Windows 및 Windows Mobile로 구분합니다.
* 모바일 디바이스 등록을 제한해도 PC 클라이언트 등록은 제한되지 않습니다.
* iOS에 한해, 개인 소유 디바이스의 등록을 차단하는 한 가지 추가 옵션이 있습니다.

Intune은 [이 문서](device-enrollment.md)에 설명된 대로 IT 관리자가 회사 소유로 표시하기 위한 조치를 취하지 않은 한 모든 새 디바이스를 개인 소유 디바이스로 표시합니다.

### <a name="notices"></a>알림

__Azure Portal로 등록 시 Multi-Factor Authentication 이동__ <!--VSO 750545--> 이전에는 관리자가 Intune 콘솔 또는 Configuration Manager(2016년 10월 이전 릴리스) 콘솔로 이동하여 Intune 등록에 대한 MFA를 설정했습니다. 이 업데이트된 기능을 사용하면 이제 [Microsoft Azure Portal](https://manage.windowsazure.com)에 Intune 자격 증명으로 로그인하고 Azure AD를 통해 MFA 설정을 구성합니다. 이 기능에 대한 자세한 내용은 [여기](https://aka.ms/mfa_ad)를 참조하세요.

__이제 중국에서 Android용 회사 포털 앱 사용 가능__ <!--VSO 658093--> 중국에서 Android용 회사 포털 앱을 다운로드할 수 있도록 게시합니다. 중국에는 Google Play 스토어가 없으므로 Android 디바이스는 중국 앱 마켓플레이스에서 앱을 구입해야 합니다. Android용 회사 포털 앱은 다음 스토어에서 다운로드할 수 있습니다.
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

Android 용 회사 포털 앱은 Google Play 서비스를 사용하여 Microsoft Intune 서비스와 통신합니다. 중국에서는 Google Play 서비스가 아직 제공되지 않으므로 다음 작업을 수행하면 완료까지 최대 8시간 걸릴 수 있습니다. 

|Intune 관리 콘솔| Android용 Intune 회사 포털 앱 |Intune 회사 포털 웹 사이트|   
|---|---|---|
|전체 초기화| 원격 디바이스 제거| 디바이스(로컬 및 원격) 제거|
|선택적 초기화| 디바이스 다시 설정| 디바이스 다시 설정|
|신규 또는 업데이트된 앱 배포| 사용 가능한 LOB(기간 업무) 앱 설치| 디바이스 암호 재설정|
|원격 잠금|||
|암호 재설정|||

### <a name="deprecations"></a>지원 중단

__Firefox에서 더 이상 Silverlight를 지원하지 않음__ <!--VSO TBA--> Mozilla는 2017년 3월부터 [Firefox 브라우저](https://www.mozilla.org/firefox) 버전 52에서 Silverlight를 지원하지 않을 예정입니다. 따라서 51 이후의 Firefox 버전을 사용하여 기존 Intune 콘솔에 더 이상 로그인할 수 없게 됩니다. Internet Explorer 10/11 또는 [버전 52 이전의 Firefox](https://ftp.mozilla.org/pub/firefox/releases/)를 사용하여 관리 콘솔에 액세스하는 것이 좋습니다. Intune이 Azure Portal로 전환되면 Silverlight를 사용하지 않고도 다수의 [최신 브라우저](/azure/azure-preview-portal-supported-browsers-devices)가 지원될 예정입니다.

__Exchange Online 모바일 사서함 정책 제거__ <!--770687--> 12월부터 관리자는 더 이상 Intune 콘솔 내에서 Exchange Online(EAS) 모바일 사서함 정책을 보거나 구성할 수 없습니다. 12월과 1월 동안에 이 변경 내용이 모든 Intune 테넌트로 롤아웃됩니다. 모든 기존 정책은 구성된 상태로 유지됩니다. 새 정책을 구성하려면 Exchange 관리 셸을 사용하세요. 자세한 내용은 [여기](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx)를 참조하세요.

__Intune AV Player, 이미지 뷰어 및 PDF 뷰어 앱이 Android에서 더 이상 지원되지 않음__ <!--747553--> 2016년 12월 중순부터 사용자는 더 이상 Intune AV Player, 이미지 뷰어 및 PDF 뷰어 앱을 사용할 수 없습니다. 이러한 앱은 Azure Information Protection 앱으로 대체되었습니다. Azure Information Protection 앱에 대한 자세한 내용은 [여기](/information-protection/rms-client/mobile-app-faq)를 참조하세요.

## <a name="november-2016"></a>2016년 11월

### <a name="new-capabilities"></a>새로운 기능

__Windows 10 디바이스에 사용할 수 있는 새로운 Microsoft Intune 회사 포털__ Microsoft는 새로운 [Windows 10 디바이스용 Microsoft Intune 회사 포털 앱](https://www.microsoft.com/store/apps/9wzdncrfj3pz)을 출시했습니다. 이 앱은 새로운 Windows 10 유니버셜 형식을 활용하고 있으며, 현재 사용 중인 모든 기능을 계속 사용할 수 있게 하면서 사용자에게 앱의 업데이트된 사용자 환경과 모든 Windows 10 디바이스, PC 및 모바일 유사 디바이스에 걸쳐 동일한 환경을 제공합니다.

새 앱을 사용하면 사용자가 Windows 10 디바이스에서 SSO(Single Sign-On) 및 인증서 기반 인증과 같은 추가적인 플랫폼 기능도 활용할 수 있습니다. 이 앱은 기존 Windows 8.1 회사 포털과 Windows Phone 8.1 회사 포털에 대한 업그레이드로서 Microsoft 스토어에서 설치해 사용할 수 있습니다. 자세한 내용은 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)를 참조하세요.

> [!IMPORTANT]
> __Intune 및 Android for Work에 대한 업데이트__ __필수__ 작업을 통해 Android for Work 앱을 배포할 수 있는 반면, Intune 그룹이 새 Azure AD 그룹 환경으로 마이그레이션된 경우에는 앱을 __사용 가능__으로만 배포할 수 있습니다.

__Intune 앱 SDK Cordova 플러그 인을 통해 별도의 등록 없이 MAM 사용__ 앱 개발자는 Cordova용 Intune 앱 SDK 플러그 인을 사용하여 Cordova 기반 Android 및 iOS용 앱에 디바이스를 등록하지 않고도 MAM 기능을 설정할 수 있습니다. Cordova용 Intune 앱 SDK 플러그 인은 [여기](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)에서 제공됩니다.

__Intune 앱 SDK Xamarin 구성 요소를 통해 별도의 등록 없이 MAM 사용__ 앱 개발자는 Intune 앱 SDK Xamarin 구성 요소를 사용하여 Xamarin 기반 Android 및 iOS용 앱에 디바이스를 등록하지 않고도 MAM 기능을 설정할 수 있습니다. Intune 앱 SDK Xamarin 구성 요소는 [여기](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)에서 제공됩니다.

### <a name="notices"></a>알림

__이제 Symantec 서명 인증서를 업로드할 때 서명된 Windows Phone 8 회사 포털이 필요하지 않음__ Symantec 서명 인증서를 업로드할 때 서명된 Windows Phone 8 회사 포털 앱이 더 이상 필요하지 않습니다. 인증서는 개별적으로 업로드할 수 있습니다.

### <a name="deprecations"></a>지원 중단

__Windows Phone 8 회사 포털에 대한 지원__ 이제 Windows Phone 8 회사 포털은 지원되지 않습니다. Windows Phone 8 및 WinRT 플랫폼 지원이 2016년 10월에 중단되었습니다. Windows 8 회사 포털 지원도 2016년 10월에 중단되었습니다.


### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.
