---
title: 초기 버전 | Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 초기 버전
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: d1b553d262200e58a4c06dd0f4bcb72ca1398080
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54386983"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Microsoft Intune 초기 버전 - 2019년 1월

> [!Note]
> NDA 알림: Intune에 대해 다음 변경 사항을 개발 중입니다. 이 정보는 매우 제한된 기준에 따라 NDA에서 공유됩니다. Twitter, UserVoice, Reddit 등과 같은 소셜 미디어 또는 공개 웹 사이트에 이 정보를 게시하지 마세요. 

**초기 버전**에서는 Microsoft Intune의 향후 릴리스에서 도입될 기능(NDA로 공유됨) 목록을 제공합니다. 이 정보는 제한적으로 제공되며 변경될 수 있습니다. Twitter, UserVoice에 게시 또는 다른 방법으로 이 정보를 회사 외부에서 공유하지 마세요. 여기 나열된 일부 기능은 마감일을 맞추지 못할 위험이 있으며 다음 릴리스까지 지연될 수 있습니다. 다른 기능은 고객용 준비 상태를 확인하기 위해, 파일럿(플라이팅) 테스트 중 입니다. 질문이나 궁금한 내용이 있으면 Microsoft 제품 그룹 담당자에게 연락하세요.

이 페이지는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal의 Intune

<!-- 1901 start -->

### <a name="android-enterprise-apps----1352553----"></a>Android Enterprise 앱 <!-- 1352553  -->
Microsoft Intune에서 관리되는 Google Play 앱을 삭제할 수 있습니다. 관리되는 Google Play 앱을 삭제하려면 Azure Portal에서 Microsoft Intune을 열고 **클라이언트 앱** > **앱**을 선택합니다. 앱 목록에서 관리되는 Google Play 앱의 오른쪽에 있는 줄임표(...)를 선택한 다음, 표시된 목록에서 **삭제**를 선택합니다. 앱 목록에서 관리되는 Google Play 앱을 삭제하면 관리되는 Google Play 앱이 자동으로 승인되지 않습니다.

### <a name="managed-google-play-app-type----1352580---"></a>관리되는 Google Play 앱 유형 <!-- 1352580 -->
**관리되는 Google Play** 앱 형식을 사용하면 [관리되는 Google Play 앱](https://play.google.com/work/search?q=microsoft&c=apps)을 Intune에 추가할 수 있습니다. Intune 관리자는 이제 Intune 내에서 승인된 관리되는 Google Play 앱을 찾기, 검색, 승인, 동기화 및 할당할 수 있습니다. 더 이상 관리되는 Google Play 콘솔에 별도로 이동할 필요가 없으며, 더 이상 재인증할 필요가 없습니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. **앱 유형** 목록에서 앱 유형으로 **관리되는 Google Play**를 선택합니다.

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱 배포 <!-- 1672660  -->
디바이스 컨텍스트에서 필요로 하는 온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱을 할당할 수 있습니다. 이 방식으로 비즈니스용 Microsoft Store 앱을 배포하면 디바이스의 모든 사용자에 대해 앱을 설치할 수 있습니다. 이 기능은 Windows 10 RS4 이상 데스크톱 디바이스에만 적용됩니다. 디바이스 컨텍스트에 설치하는 옵션은 MSFB 온라인 라이선스가 부여된 앱에 대한 클라이언트 앱 할당 페이지에서 사용할 수 있습니다.

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>설정 도우미 수행 중에 일부 화면을 건너뛰도록 프로필 구성 <!-- 2276470  -->
macOS 등록 프로필을 만들 경우 사용자가 설정 도우미를 수행할 때 다음 화면 중 하나를 건너뛰도록 구성할 수 있습니다.
- Android 마이그레이션
- 표시 색상
- 개인 정보 취급 방침
- iCloudStorage

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522----"></a>Autopilot 프로필을 모든 디바이스 가상 그룹에 할당 <!--2715522  -->
Autopilot 프로필을 모든 디바이스 가상 그룹에 할당할 수 있습니다. 그렇게 하려면 **디바이스 등록** > **Windows 등록** > **배포 프로필** &gt; 프로필 선택 &gt; **할당**을 선택하고 **할당 대상**에서 **모든 디바이스**를 선택합니다. Autopilot 프로필에 대한 자세한 내용은 [Windows Autopilot을 사용하여 Windows 디바이스 등록](enrollment-autopilot.md)을 참조하세요.

### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324----"></a>디바이스 구성 프로필을 사용하여 감독되는 iOS 디바이스에서 배경 화면 사용자 지정 <!-- 2809324  -->
iOS 디바이스용 디바이스 구성 파일을 만들 때 프로필 형식에 대한 **디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 플랫폼용 > **디바이스 제한**에서 일부 설정을 허용하고 제한할 수 있습니다. 이 업데이트에는 관리자가 배경 무늬로 .png, .jpg 또는 .jpeg 이미지를 사용하고, 이미지를 미리 보고 사용자가 배경 무늬를 변경하지 못하도록 차단할 수 있는 새로운 **배경 무늬** 설정이 포함되어 있습니다. 배경 무늬 설정은 감독되는 디비이스에만 적용됩니다. 현재 설정 목록은 [iOS 디바이스 제한 설정](device-restrictions-ios.md)을 참조하세요.

### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 앱에 대한 알림 메시지 <!-- 3136566   -->
앱 할당마다 최종 사용자 알림 메시지를 표시하지 않을 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > 앱 선택 > **할당** > **포함 그룹**을 선택합니다. 

### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396---"></a>Bluetooth를 통한 연락처 공유가 디바이스 제한 사항 > Android Enterprise에 대한 디바이스 소유자에서 제거됨 <!-- 3598396 -->
Android Enterprise 디바이스용 디바이스 제한 프로필을 만들 때 **Bluetooth를 통한 연락처 공유** 설정이 있습니다. 이 업데이트에서는 **Bluetooth를 통한 연락처 공유** 설정이 제거됩니다(**디바이스 구성** > **프로필**  >  **프로필 만들기** > **Android Enterprise** 플랫폼용 > **디바이스 제한 사항 > 디바이스 소유자** 프로필 유형의 경우 > **일반**). 

**Bluetooth를 통한 연락처 공유** 설정은 Android Enterprise 디바이스 소유자 관리에 대해 지원되지 않습니다. 따라서 이 설정을 제거하면 사용자 환경에서 이 설정을 활성화하고 구성하더라도 디비이스나 테넌트에 영향을 주지 않습니다.

현재 설정 목록을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동합니다.

적용 대상: Android Enterprise 디바이스 소유자

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 엔터프라이즈 APP-WE 앱 배포 <!-- 1171203 -->
등록되지 않은 APP-WE(등록이 없는 앱 보호 정책) 배포 시나리오에 있는 Android 디바이스의 경우 관리형 Google Play를 사용하여 스토어 앱 및 LOB 앱을 사용자에게 배포할 수 있습니다. 특히 IT 부서에서는 최종 사용자에게 알 수 없는 소스에서 설치를 허용하여 해당 디바이스의 보안 상태를 느슨하게 하도록 더 이상 요구하지 않는 앱 카탈로그 및 설치 환경을 최종 사용자에게 제공할 수 있습니다. 또한 이 배포 시나리오는 향상된 최종 사용자 환경을 제공합니다.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune 앱 SDK는 256비트 암호화 키를 지원함 <!-- 1832174 -->
Android용 Intune 앱 SDK는 앱 보호 정책에서 암호화를 사용하도록 설정할 때 256비트 암호화 키를 사용합니다. SDK는 이전 SDK 버전을 사용하는 콘텐츠 및 앱과 호환성을 위해 128비트 키 지원을 계속 제공합니다.


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 정책에서 인증 방법 및 회사 포털 앱 설치를 업데이트함 <!-- 1927359 -->
Apple의 회사 디바이스 등록 방법 중 하나를 통해 설정 도우미에서 이미 등록한 디바이스에서는 최종 사용자가 앱 스토어에서 회사 포털 앱을 수동으로 설치하는 경우 Intune은 더 이상 해당 회사 포털 앱을 지원하지 않습니다. 이 변경은 등록 중에 Apple 설정 도우미로 인증하는 경우에만 적용됩니다. 또한 이 변경은 다음을 통해 등록된 iOS 디바이스에만 영향을 줍니다.  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple DEP(장비 등록 프로그램)

사용자가 App Store에서 회사 포털 앱을 설치한 다음, 이 앱을 통해 이러한 디바이스를 등록하는 경우 오류가 발생합니다. 이 디바이스는 등록 중에 Intune에서 자동으로 푸시된 경우에만 회사 포털을 사용해야 합니다. Azure Portal에서 Intune의 등록 프로필이 업데이트되므로 디바이스 인증 방법 및 디바이스가 회사 포털 앱을 받는 방법을 지정할 수 있습니다. DEP 디바이스 사용자가 회사 포털을 사용하도록 하려면 등록 프로필에서 기본 설정을 지정해야 합니다. 또한 회사 포털 앱에서 **디바이스 식별** 화면이 더 이상 사용되지 않습니다.  
이미 등록된 DEP 디바이스에 회사 포털을 설치하려면 Intune > 클라이언트 앱으로 이동하고 앱 구성 정책을 사용하여 이 앱을 관리형 앱으로 푸시해야 합니다. 이러한 단계를 수행하는 방법에 대한 자세한 내용은 이후 문서에서 간략하게 설명합니다.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>관리자가 아닌 사용자는 Azure AD에 조인된 Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 수 있음 <!-- 2147379 -->
Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼) > **Endpoint Protection**(프로필 유형) > **Windows 암호화**) BitLocker 설정을 추가합니다. 이 업데이트에는 표준 사용자(관리자가 아닌 사용자)가 암호화를 사용하도록 설정하게 허용하는 새 BitLocker 설정이 포함됩니다. 현재 설정을 보려면 [Windows 10용 Endpoint Protection 설정](endpoint-protection-windows-10.md#windows-encryption)을 참조하세요.


### <a name="additional-settings-for-outlook----3301182---"></a>Outlook에 대한 추가 설정 <!-- 3301182 -->
이제 Intune을 사용하여 Android 및 iOS용 Outlook에 대한 추가 설정을 구성할 수 있습니다.  이러한 설정은 다음과 같습니다.
- iOS 및 Android의 Outlook에서 사용할 회사 또는 학교 계정만 허용
- Office 365 및 하이브리드 최신 인증 온-프레미스 계정에 대한 최신 인증 배포
- 기본 인증을 선택한 경우 이메일 프로필의 사용자 이름 필드에 대한 `SAMAccountName` 사용
- 저장할 연락처 허용
- 외부 받는 사람 MailTips 구성
- **중요 받은 편지함** 구성
- iOS용 Outlook에 액세스하려면 생체 인식 필요 
- 외부 이미지 차단

> [!NOTE]
> 회사 ID에 대한 액세스를 관리하기 위해 Intune 앱 보호 정책을 사용하는 경우 **생체 인식 필요**를 사용하지 않도록 설정하는 것이 좋습니다. 자세한 내용은 [iOS 액세스 요구 사항](app-protection-policy-settings-ios.md#access-settings) 및 [Android 액세스 요구 사항](app-protection-policy-settings-android.md#access-settings)에 **액세스하려면 회사 자격 증명 필요**를 참조하세요.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>관리 템플릿은 공개 미리 보기로 제공되고 자체 구성 프로필 로 이동됨 <!-- 3322847 -->
Intune의 관리 템플릿(**디바이스 구성** > **관리 템플릿**)은 현재 비공개 미리 보기로 제공됩니다. 이 업데이트 포함: 관리 템플릿에는 Intune에서 관리할 수 있는 약 300개 설정이 포함됩니다. 이전에는 이러한 설정이 그룹 정책 편집기에만 있었습니다.
관리 템플릿은 공개 미리 보기로 제공 됩니다. 관리 템플릿은 **디바이스 구성** > **관리 템플릿**에서 **디바이스 구성** > **프로필** >**프로필 만들기** > **플랫폼**에서 **Windows 10 이상** 선택, **프로필 유형**에서 **관리 템플릿** 선택으로 이동됩니다.
보고는 사용하도록 설정됩니다. 적용 대상: Windows 10 이상

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune macOS 회사 포털 어두운 모드 <!-- 3300524 -->
Intune macOS 회사 포털은 이제 macOS용 어두운 모드를 지원합니다. macOS 10.14 이상 디바이스에서 어두운 모드를 활성화하면 회사 포털은 해당 모드를 리플렉션하는 색으로 모양을 조정합니다.

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Microsoft 권장 설정을 보안 기준과 함께 사용<!-- 2055484 -->
Intune은 Windows Defender ATP 및 Office 365 ATP를 비롯하여 보안에 중점을 둔 다른 서비스와 통합됩니다. 고객은 Microsoft 365 서비스에서 공통 전략 및 조화로운 종단 간 보안 워크플로 집합을 요청하고 있습니다. 우리의 목표는 보안 작업 및 공통 관리자 작업을 연결하는 솔루션을 빌드하기 위한 전략을 조정하는 것입니다. Intune에서는 Microsoft 권장 “보안 기준” 집합(**Intune** > **보안 기준**)을 게시하여 이 목표를 달성하고자 합니다.  관리자는 이러한 기준에서 직접 보안 정책을 만든 후 이를 사용자에게 배포할 수 있습니다. 또한 조직의 요구 사항을 충족하도록 최선의 권장 사항을 사용자 지정할 수도 있습니다. Intune은 디바이스가 이러한 기준을 계속 준수하는지 확인하고 준수하지 않는 디바이스나 사용자에 대해 관리자에게 알립니다.

### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>등록 디바이스 없이 WIP에 대한 선택적 초기화 지원 <!-- 1434452 -->
등록 없이 Windows 정보 보호(WIP-WE) 를 사용하면 고객은 전체 MDM 등록할 필요 없이 Windows 10 디바이스에서 회사 데이터를 보호할 수 있습니다. 문서가 WIP-WE 정책으로 보호되면 Intune 관리자는 보호되는 데이터를 선택적으로 초기화할 수 있습니다. 사용자 및 디바이스를 선택하고 초기화 요청을 보내면 WIP-WE 정책을 통해 보호된 모든 데이터를 사용할 수 없게 됩니다. Azure Portal의 Intune에서 **모바일 앱** > **앱 선택적 초기화**를 선택합니다.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>웹 데이터에 대한 APP(앱 보호 정책) 설정 <!-- 2662995 -->
Android 및 iOS 디바이스의 웹 콘텐츠에 대한 APP 정책 설정은 iOS 유니버설 링크 및 Android 앱 링크를 통한 데이터 전송을 비롯하여 http 및 https 웹 링크를 모두 더 잘 처리하기 위해 업데이트됩니다.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>다른 MDM에서 사용하는 Apple VPP 토큰 <!-- 1488946 -->
Intune과 다른 MDM에서 모두 Apple VPP(대량 구매 프로그램) 토큰을 사용하고 있으면 Intune에서 세부 정보를 검색하고 표시합니다.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>디바이스 준수 대시보드에 사용 중지된 디바이스가 있음 <!-- 1981119 -->
향후 업데이트에서는 사용 중지된 디바이스가 디바이스 준수 대시보드에서 제거됩니다. 이에 따라 규정 준수 번호도 변경됩니다.



<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Configuration Manager 준수 확인 <!-- 2192052 -->
향후 업데이트에는 새 System Center Configuration Manager 준수 설정이 포함됩니다(**디바이스 준수** > **정책** > **정책 만들기** > **Windows 10**). Configuration Manager는 Intune 준수에 신호를 보냅니다. Intune 설정을 사용하여 모든 Configuration Manager 신호에 “준수”를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 디바이스에 설치해야 합니다. Configuration Manager에서 이 요구 사항의 상태는 “설치됨”입니다. 디바이스의 프로그램이 알 수 없는 상태에 있는 경우 디바이스는 Intune에서 비준수가 됩니다.

적용 대상: Windows 10 이상



## <a name="notices"></a>알림

이번에는 활성 알림이 없습니다.

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.



