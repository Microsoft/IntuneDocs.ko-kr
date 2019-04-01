---
title: 개발-Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 기능 개발
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c377a8558b1f318b4ddad735b6368a291e34516
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756822"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>Microsoft intune-개발에서 2019 년 3 월

준비 및 계획,이 페이지를 지원 하기 위해 목록 Intune UI 업데이트 및 기능을 개발은 있지만 아직 릴리스되지 않은 경우. 또한,

- 변경 하기 전에 작업을 수행 해야 하는 것이 예정, 경우 무료 Office 메시지 센터 게시물을 게시 하겠습니다.
- 경우 기능을 프로덕션 환경에서 미리 보기로 하거나 시작 일반 공급 기능 설명 됩니다 및 또는 이동이 페이지에 [새로운 기능 페이지](whats-new.md)합니다.
- 이 페이지와 [새로운 기능 페이지](whats-new.md) 정기적으로 업데이트 됩니다. 추가 업데이트가 있는지 다시 확인하세요.
- 참조 된 [M365 로드맵](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) 전략적 결과물 및 타임 라인에 대 한 합니다.

> [!Note]
> 이러한 항목에는 이후 릴리스에서 제공 하는 Intune 기능에 대 한 Microsoft의 현재 예상 반영 합니다. 날짜 및 개별 기능이 변경 될 수 있습니다. 개발의 모든 항목 경우 기능 설명 페이지

**RSS 피드**: 다음(`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`) URL을 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알림을 받을 수 있습니다.


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal의 Intune


<!-- 1903 start-->

### <a name="encryption-report-----2351538---"></a>암호화 보고서  <!-- 2351538 -->
새 암호화 보고서를 사용 하 여 장치 암호화 상태에 대 한 세부 정보를 볼 수 있습니다. 사용 가능한 세부 정보는 장치 TPM 버전, 암호화 준비 상태 및 상태, 오류 보고 등 포함 됩니다.  

### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-----2351547----"></a>Intune 포털에서 BitLocker 복구 키에 액세스  <!-- 2351547  -->
새로운 진입점에서 Active Directory (AAD (Azure) BitLocker 키 ID 및 BitLocker 복구 키에 대 한 세부 정보를 볼 수 있는 장치에 추가 될 예정입니다.

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>앱 구성 정책에 대 한 범위 태그 <!--2371891 -->
또한 해당 범위 태그를 할당 하는 역할이 있는 사용자만 앱 구성 정책에 액세스할 수 있도록 앱 구성 정책을 범위 태그를 추가할 수 있습니다. 앱 구성 정책 대상으로 하거나만 같은 범위 태그를 할당 하는 앱과 연결 된 수 있습니다.

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Autopilot 프로필을 모든 디바이스 가상 그룹에 할당 <!--2715522 -->
Autopilot 프로필을 모든 디바이스 가상 그룹에 할당할 수 있습니다. 그렇게 하려면 **디바이스 등록** > **Windows 등록** > **배포 프로필** &gt; 프로필 선택 &gt; **할당**을 선택하고 **할당 대상**에서 **모든 디바이스**를 선택합니다. Autopilot 프로필에 대한 자세한 내용은 [Windows Autopilot을 사용하여 Windows 디바이스 등록](enrollment-autopilot.md)을 참조하세요.

### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523----"></a>Windows 대량 등록 후 회사 포털 앱을 사용 하 여 사용 가능한 앱 설치 <!-- 2751523  -->
사용 하 여 Intune에 등록 된 Windows 장치의 [Windows 대량 등록](windows-bulk-enroll.md) (패키지를 프로 비전 중) 회사 포털 앱을 사용 하 여 사용 가능한 앱 설치 수 있게 됩니다. 회사 포털 앱에 대 한 자세한 내용은 참조 하세요. [Windows 10 회사 포털에 수동으로 추가](store-apps-company-portal-app.md) 하 고 [Microsoft Intune 회사 포털 앱을 구성 하는 방법](company-portal-app.md)합니다.

### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430---"></a>IOS 앱 프로비저닝 프로필에 대 한 범위 태그 <!--2934430 -->
또한 해당 범위 태그를 할당 하는 역할이 있는 사용자만에 iOS 앱 프로비저닝 프로필에 액세스할 수 있도록 범위 태그는 iOS 앱 프로 비전 프로필에 추가할 수 있습니다. 

### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477----"></a>Office 배포 도구 (ODT) Office ProPlus 배포에 대 한 XML <!-- 3192477  -->
Intune 관리 콘솔에서 Office Pro Plus의 인스턴스를 만들 때 Office 배포 도구 (ODT) XML을 제공할 수 있습니다. 이렇게 하면 큰 사용자 지정 가능성 기존 Intune UI 옵션에서 사용자의 요구를 충족 하지 않는 경우. 

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>사용자의 Windows 업데이트에 대 한 검사 차단    <!-- 3316758    -->
새 Windows 업데이트 링을 사용할 수 있는 설정 Windows 업데이트에 대 한 검색에서 사용자를 차단 하는 추가 될 예정입니다. 이 설정은 포털 내에서 사용할 수 없지만 Intune Graph API를 사용 하 여 구성할 수 있습니다.

### <a name="windows-update-notifications-----3316782---"></a>Windows 업데이트 알림  <!-- 3316782 -->
사용자에 게 표시 되는 Windows 업데이트 알림을 구성 하는 일을 할 수 있도록 지원 Windows 업데이트 링 구성에 추가 될 예정입니다. 이 설정은 포털 내에서 사용할 수 없지만 Intune Graph API를 사용 하 여 구성할 수 있습니다.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>IOS 용 회사 포털 등록 12 장치 사용자 변경 <!--3448635 -->  
IOS 용 회사 포털 앱의 등록 화면 및 Apple iOS 12.2에에서 릴리스된 MDM 등록 변경 내용에 맞게 단계를 업데이트할 예정입니다. 업데이트 된 워크플로를 사용자에 게 이제 됩니다.

- Safari (Safari)를 통해 회사 포털 웹 사이트를 열고 회사 포털 앱에 반환 하기 전에 관리 프로필을 다운로드할 수 있습니다. 
- 장치에서 관리 프로필을 설치 하려면 설정 앱을 엽니다.
- 등록을 완료 하려면 회사 포털 앱에 반환 합니다.  

이러한 변경 내용을 준비 하는 방법에 대 한 자세한 내용은 참조는 [Microsoft 기술 커뮤니티 게시물](https://techcommunity.microsoft.com/)합니다. 한편, 회사 포털에서 새 iOS 등록을 지원 하려면 업데이트 했습니다의 단계 [Intune에서 iOS 장치 등록](https://docs.microsoft.com/en-us/intune/ios-enroll)합니다. 이러한 문서 변경 내용을 Apple iOS 버전 12.2 출시 후 라이브 상태가 됩니다. 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>테 넌 트 상태 페이지에서 추가 커넥터에 대 한 지원 <!-- 3617202     -->
테 넌 트 상태 페이지에는 포함 하 여 추가 커넥터에 대 한 상태 정보가 표시 됩니다 *Windows Defender Advanced Threat Protection* (ATP) 및 기타 Mobile Threat Defense 커넥터.

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>Intune 권한 부여 읽기 전용 액세스를 일부 Azure Active Directory 역할 <!-- 3637917 -->
에서는 Intune 읽기 전용 액세스는 다음 Azure AD 역할에 부여 될 됩니다. Azure AD 역할을 사용 하 여 부여 된 사용 권한을 Intune 역할 기반 액세스 제어 (RBAC)를 사용 하 여 부여 된 권한 보다 우선 합니다.

읽기 전용 Intune 감사 데이터에 액세스 합니다.

- 규정 준수 관리자
- 준수 데이터 관리자

Intune는 모든 데이터를 읽기 전용 액세스를 지원 합니다.

- 보안 관리자
- 보안 연산자
- 보안 Reader
- 전역 판독기

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>진단 설정에 쉽게 액세스할 수 있도록   <!-- 3804627   -->
하는 새로운 옵션이 추가 될 예정를 **감사 로그** 블레이드에서 직접 열을 사용할 수 있는 Intune 콘솔에서 모든 감사 로그 작업에서 모든 합니다 *진단 설정* 페이지입니다.

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>만들기 및 장치 구성 프로필을 사용 하 여 Intune에서 Android 얼룩말 장치의 <!-- 3895244  -->
Intune은 구성 얼룩말 Android 장치를 지원 합니다. 특히를 수 있습니다. 

- 장치 구성 프로필을 만들고 StageNow에서 생성 하는 모바일 확장 (MX) 프로필을 사용 하 여 Android 얼룩말 장치에 설정 적용 (**장치 구성** > **프로필**  >  **프로필 만들기** > **Android** 플랫폼에 대 한).

적용 대상:  
- Android

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱 배포 <!-- 1672660  -->
디바이스 컨텍스트에서 필요로 하는 온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱을 할당할 수 있습니다. 이 방식으로 비즈니스용 Microsoft Store 앱을 배포하면 디바이스의 모든 사용자에 대해 앱을 설치할 수 있습니다. 이 기능은 Windows 10 RS4 이상 데스크톱 디바이스에만 적용됩니다. 디바이스 컨텍스트에 설치하는 옵션은 MSFB 온라인 라이선스가 부여된 앱에 대한 클라이언트 앱 할당 페이지에서 사용할 수 있습니다.

## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.
