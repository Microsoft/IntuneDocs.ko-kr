---
title: Microsoft Intune의 새로운 기능 - Azure | Microsoft Docs
titlesuffix: ''
description: Intune Azure 포털의 새로운 기능 알아보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6d346d7f060b5e997577b09c3ee8b006843ab7b
ms.sourcegitcommit: 8e503c1b350f7b29a045b7daf3eece64be4ca3c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56302237"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

매주 Microsoft Intune에 추가되는 새로운 기능에 대해 알아봅니다. 예정된 변경, [중요 공지](#notices) 및 [이전 릴리스](whats-new-archive.md)에 대한 정보도 확인할 수 있습니다. 

> [!Note]
> 일부 기능은 몇 주에 걸쳐 출시될 수 있고 첫 번째 주에는 모든 고객에게 제공되지 않습니다.
>
> 하이브리드 MDM(모바일 디바이스 관리)의 새로운 기능에 대한 자세한 내용은 [하이브리드의 새로운 기능 페이지](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)를 참조하세요.

**RSS 피드**: 다음 URL을 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알림을 받을 수 있습니다. `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     
## <a name="week-of-february-4-2019"></a>2019년 2월 4일 주

### <a name="app-management"></a>앱 관리

#### <a name="intune-macos-company-portal-dark-mode----3300524-eeready---"></a>Intune macOS 회사 포털 어두운 모드 <!-- 3300524 eeready -->
Intune macOS 회사 포털은 이제 macOS용 어두운 모드를 지원합니다. macOS 10.14 이상 디바이스에서 어두운 모드를 활성화하면 회사 포털은 해당 모드를 리플렉션하는 색으로 모양을 조정합니다.

## <a name="week-of-january-21-2019"></a>2019년 1월 21일 주

### <a name="app-management"></a>앱 관리

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 앱에 대한 알림 메시지 <!-- 3136566   -->
앱 할당마다 최종 사용자 토스트 알림을 표시하지 않을 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > 앱 선택 > **할당** > **포함 그룹**을 선택합니다. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Intune 앱 보호 정책 UI 업데이트 <!-- 3251427  -->
각각 더 쉽게 이해할 수 있도록 Intune 앱 보호 설정 및 단추의 레이블을 변경했습니다. 일부 변경 내용은 다음과 같습니다.  
- 컨트롤은 **예** / **아니요** 컨트롤에서 기본 **차단** / **허용** 및 **사용 안 함** / **사용** 컨트롤로 변경됩니다. 레이블도 업데이트됩니다.  
- 설정이 다시 포맷되므로 설정과 레이블이 컨트롤에 나란히 있어 더 효율적으로 검색할 수 있습니다.   

기본 설정과 설정 수는 동일하게 유지되지만, 이 변경으로 인해 사용자가 선택한 앱 보호 정책을 적용하기 위해 설정을 더 쉽게 이해, 검색 및 활용할 수 있습니다. 자세한 내용은 [iOS 설정](app-protection-policy-settings-ios.md) 및 [Android 설정](app-protection-policy-settings-android.md)을 참조하세요.

#### <a name="additional-settings-for-outlook----3301182----"></a>Outlook에 대한 추가 설정 <!-- 3301182  -->
이제 Intune을 사용하여 Android 및 iOS용 Outlook에 대한 다음과 같은 추가 설정을 구성할 수 있습니다.
- iOS 및 Android의 Outlook에서 사용할 회사 또는 학교 계정만 허용
- Office 365 및 하이브리드 최신 인증 온-프레미스 계정에 대한 최신 인증 배포
- 기본 인증을 선택한 경우 이메일 프로필의 사용자 이름 필드에 대한 `SAMAccountName` 사용

여전히 다음 설정이 점진적으로 롤아웃되고 곧 콘솔에서 사용할 수 있게 됩니다.
- 저장할 연락처 허용
- 외부 받는 사람 MailTips 구성
- **중요 받은 편지함** 구성
- iOS용 Outlook에 액세스하려면 생체 인식 필요

아래 설정이 Intune 콘솔에 표시되지만 구성되는 경우 예상대로 작동하지 않습니다. 이 문제는 곧 해결됩니다.
- 외부 이미지 차단

> [!NOTE]
> 회사 ID에 대한 액세스를 관리하기 위해 Intune 앱 보호 정책을 사용하는 경우 **생체 인식 필요**를 사용하지 않도록 설정하는 것이 좋습니다. 자세한 내용은 [iOS 액세스 요구 사항](app-protection-policy-settings-ios.md#access-requirements) 및 [Android 액세스 설정](app-protection-policy-settings-android.md#access-requirements)에 **액세스하려면 회사 자격 증명 필요**를 참조하세요.

#### <a name="delete-android-enterprise-apps----1352553---"></a>Android Enterprise 앱 삭제 <!-- 1352553 -->
Microsoft Intune에서 관리되는 Google Play 앱을 삭제할 수 있습니다. 관리되는 Google Play 앱을 삭제하려면 Azure Portal에서 Microsoft Intune을 열고 **클라이언트 앱** > **앱**을 선택합니다. 앱 목록에서 관리되는 Google Play 앱의 오른쪽에 있는 줄임표(...)를 선택한 다음, 표시된 목록에서 **삭제**를 선택합니다. 앱 목록에서 관리되는 Google Play 앱을 삭제하면 관리되는 Google Play 앱이 자동으로 승인되지 않습니다.

#### <a name="managed-google-play-app-type----1352580---"></a>관리되는 Google Play 앱 유형 <!-- 1352580 -->
**관리되는 Google Play** 앱 형식을 사용하면 [관리되는 Google Play 앱](https://play.google.com/work/search?q=microsoft&c=apps)을 Intune에 추가할 수 있습니다. Intune 관리자는 이제 Intune 내에서 승인된 관리되는 Google Play 앱을 찾고, 검색하고, 승인하며, 동기화하고 할당할 수 있습니다.  더 이상 관리되는 Google Play 콘솔을 개별적으로 찾아보지 않아도 되며 더 이상 재인증할 필요가 없습니다.  Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. **앱 유형** 목록에서 앱 유형으로 **관리되는 Google Play**를 선택합니다.

### <a name="default-android-pin-keyboard----3802457---"></a>기본 Android PIN 키보드 <!-- 3802457 -->
'숫자' PIN 형식을 사용하여 Android 디바이스에서 Intune APP(앱 보호 정책) PIN을 설정한 최종 사용자에게는 이제 이전에 설계된 고정 Android 키보드 UI 대신 기본 Android 키보드가 표시됩니다. '숫자' 및/또는 '암호' PIN 형식 모두에 대해 iOS 및 Android 디바이스 모두에서 기본 키보드를 사용하는 경우 일치하도록 이렇게 변경되었습니다. Android에서 APP PIN과 같은 최종 사용자 액세스 설정에 대한 자세한 내용은 [Android 액세스 요구 사항](app-protection-policy-settings-android.md#access-requirements)을 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Microsoft 권장 설정을 보안 기준과 함께 사용(공개 미리 보기)<!-- 2055484   -->

Intune은 Windows Defender ATP 및 Office 365 ATP를 비롯하여 보안에 중점을 둔 다른 서비스와 통합됩니다. 고객은 Microsoft 365 서비스에서 공통 전략 및 조화로운 종단 간 보안 워크플로 집합을 요청하고 있습니다. 우리의 목표는 보안 작업 및 공통 관리자 작업을 연결하는 솔루션을 빌드하기 위한 전략을 조정하는 것입니다. Intune에서는 Microsoft 권장 “보안 기준” 집합(**Intune** > **보안 기준**)을 게시하여 이 목표를 달성하고자 합니다.  관리자는 이러한 기준에서 직접 보안 정책을 만든 다음, 이를 사용자에게 배포할 수 있습니다. 또한 조직의 요구 사항을 충족하도록 최선의 권장 사항을 사용자 지정할 수도 있습니다. Intune은 디바이스가 이러한 기준을 계속 준수하는지 확인하고 준수하지 않는 디바이스나 사용자에 대해 관리자에게 알립니다.

이 기능은 공개 미리 보기이므로 이제 만든 모든 프로필이 일반 공급(GA)되는 보안 기준 템플릿으로 이동하지 않습니다. 프로덕션 환경에서 이러한 미리 보기 템플릿을 사용하려고 하지 말아야 합니다.

보안 기준에 대해 자세히 알아보려면 [Intune에서 Windows 10 보안 기준 만들기](security-baselines-monitor.md)를 참조하세요.

이 기능은 다음에 적용됩니다. Windows 10 이상

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>관리자가 아닌 사용자는 Azure AD에 조인된 Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 수 있음 <!-- 2147379   -->
Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼) > **Endpoint Protection**(프로필 유형) > **Windows 암호화**) BitLocker 설정을 추가합니다. 

이 업데이트에는 표준 사용자(관리자가 아닌 사용자)가 암호화를 사용하도록 설정하게 허용하는 새 BitLocker 설정이 포함됩니다. 

설정을 보려면 [Windows 10용 엔드포인트 보호 설정](endpoint-protection-windows-10.md#windows-encryption)으로 이동합니다.

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Configuration Manager 준수 확인 <!-- 2192052  eepublished  -->
이 업데이트에는 새 System Center Configuration Manager 준수 설정(**디바이스 준수** > **정책** > **정책 만들기** > **Windows 10 이상** > **Configuration Manager 준수**)이 포함됩니다. Configuration Manager는 Intune 준수에 신호를 보냅니다. 이 설정을 사용하여 모든 Configuration Manager 신호에 “준수”를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 디바이스에 설치해야 합니다. Configuration Manager에서 이 요구 사항의 상태는 “설치됨”입니다. 디바이스의 프로그램이 알 수 없는 상태인 경우 디바이스는 Intune에서 비준수가 됩니다.

[Configuration Manager 준수](compliance-policy-create-windows.md#configuration-manager-compliance)에 이 설정이 설명되어 있습니다.

적용 대상: Windows 10 이상

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>디바이스 구성 프로필을 사용하여 감독되는 iOS 디바이스에서 배경 화면 사용자 지정 <!-- 2809324   -->
iOS 디바이스에 대한 디바이스 구성 프로필을 만드는 경우 일부 기능(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대한 **iOS** > 프로필 유형에 대한 **디바이스 기능**)을 사용자 지정할 수 있습니다. 이 업데이트에는 관리자가 홈 화면 또는 잠금 화면에 .png, .jpg 또는 .jpeg 이미지를 사용하도록 허용하는 새 **배경 무늬** 설정이 포함됩니다. 이러한 배경 무늬 설정은 감독되는 디바이스에만 적용됩니다. 

이러한 설정의 목록은 [iOS 디바이스 기능 설정](ios-device-features-settings.md)을 참조하세요.

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10 키오스크 일반 공급됨 <!-- 3594661  -->
이 업데이트에서 Windows 10 이상 디바이스의 키오스크 기능이 일반 공급(GA)됩니다. 추가 및 구성할 수 있는 모든 설정을 보려면 [Windows 10(및 이상)에 대한 키오스크 설정](kiosk-settings.md)을 참조하세요.

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Bluetooth를 통한 연락처 공유가 디바이스 제한 사항 > Android Enterprise에 대한 디바이스 소유자에서 제거됨 <!-- 3598396   -->
Android Enterprise 디바이스용 디바이스 제한 프로필을 만들 때 **Bluetooth를 통한 연락처 공유** 설정이 있습니다. 이 업데이트에서 **Bluetooth를 통한 연락처 공유** 설정이 제거됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Android Enterprise** > **디바이스 제한 사항 > 프로필 유형에 대한 디바이스 소유자** > **일반**). 

**Bluetooth를 통한 연락처 공유** 설정은 Android Enterprise 디바이스 소유자 관리에 대해 지원되지 않습니다. 따라서 이 설정을 제거하면 사용자 환경에서 이 설정을 활성화하고 구성하더라도 디비이스나 테넌트에 영향을 주지 않습니다.

현재 설정 목록을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동합니다.

적용 대상: Android Enterprise 디바이스 소유자

### <a name="device-management"></a>디바이스 관리

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>등록 디바이스 없이 WIP에 대한 선택적 초기화 지원 <!-- 1434452 -->
등록 없이 Windows 정보 보호(WIP-WE) 를 사용하면 고객은 전체 MDM 등록할 필요 없이 Windows 10 디바이스에서 회사 데이터를 보호할 수 있습니다. 문서가 WIP-WE 정책으로 보호되면 Intune 관리자는 보호되는 데이터를 선택적으로 초기화할 수 있습니다. 사용자 및 디바이스를 선택하고 초기화 요청을 보내면 WIP-WE 정책을 통해 보호된 모든 데이터를 사용할 수 없게 됩니다. Azure Portal의 Intune에서 **모바일 앱** > **앱 선택적 초기화**를 선택합니다.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>새 작업 로그 및 Azure Monitor 서비스에 로그를 보낼 수 있는 기능 <!-- 3762211  -->
Intune에는 변경 사항이 발생할 때 이벤트를 추적하는 기본 제공 감사 로깅 기능이 있습니다. 이 업데이트에는 다음을 비롯한 새 로깅 기능이 포함됩니다. 
- 성공 및 실패한 시도를 포함한 등록된 사용자 및 디바이스의 세부 정보를 표시하는 작업 로그(미리 보기).
- 감사 로그 및 작업 로그를 스토리지 계정, Event Hubs 및 Log Analytics를 비롯한 Azure Monitor에 보낼 수 있습니다. 이러한 서비스를 통해 Splunk 및 QRadar와 같은 분석을 저장하고 사용하며 로깅 데이터의 시각화를 가져올 수 있습니다.

[Intune에서 스토리지, Event Hubs 또는 Log Analytics에 로그 데이터 전송](review-logs-using-azure-monitor.md)에 이 기능에 대한 자세한 정보가 나와 있습니다.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>iOS DEP 디바이스에서 설정 도우미 화면 건너뛰기 <!-- 2687509  -->
현재 건너뛸 수 있는 화면 외에도 사용자가 디바이스를 등록할 때 설정 도우미에서 다음 화면을 건너뛰도록 iOS DEP 디바이스를 설정할 수 있습니다. 표시음, 개인 정보, Android 마이그레이션, 홈 단추, iMessage 및 FaceTime, 온보딩, 마이그레이션 보기, 모양, 화면 시간, 소프트웨어 업데이트, SIM 설치.
건너뛸 화면을 선택하려면 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰** > 토큰 선택 > **프로필** > 프로필 선택 > **속성** > **설정 도우미 사용자 지정** > 건너뛸 화면의 **숨기기** 선택 > **확인**으로 이동합니다.
새 프로필을 만들거나 프로필을 편집하는 경우 선택한 건너뛰기 화면이 Apple MDM 서버와 동기화되어야 합니다. 사용자는 프로필 변경 내용을 선택하는 데 지연이 발생하지 않도록 디바이스의 수동 동기화를 발행할 수 있습니다.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 엔터프라이즈 APP-WE 앱 배포 <!-- 1171203 -->
등록되지 않은 APP-WE(등록이 없는 앱 보호 정책) 배포 시나리오에 있는 Android 디바이스의 경우 관리형 Google Play를 사용하여 스토어 앱 및 LOB 앱을 사용자에게 배포할 수 있습니다. 특히 최종 사용자에게 알 수 없는 소스에서 설치를 허용하여 해당 디바이스의 보안 상태를 느슨하게 하도록 더 이상 요구하지 않는 앱 카탈로그 및 설치 환경을 제공할 수 있습니다. 또한 이 배포 시나리오는 향상된 최종 사용자 환경을 제공합니다.

## <a name="week-of-january-14-2019"></a>2019년 1월 14일의 주

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Android 회사 소유의 완전 관리형 디바이스 지원 미리 보기 <!-- 1574342  -->
Intune은 이제 디바이스가 IT 부서에서 긴밀하게 관리되고 개별 사용자와 관련된 회사 소유 "디바이스 소유자" 시나리오인 완전 관리형 Android 디바이스를 지원합니다. 이를 통해 관리자는 전체 디바이스를 관리하고, 확장된 범위의 정책 제어를 회사 프로필에 사용할 수 없게 할 수 있고 사용자가 관리형 Google Play의 앱만 설치하도록 제한합니다. 자세한 내용은 [Android 완전 관리형 디바이스의 Intune 등록 설정](android-fully-managed-enroll.md) 및 [전용 디바이스 또는 완전 관리형 디바이스 등록](android-dedicated-devices-fully-managed-enroll.md)을 참조하세요.  이 기능은 미리 보기에 있습니다. 인증서, 규정 준수 및 조건부 액세스와 같은 일부 Intune 기능은 현재 Android 완전 관리형 사용자 디바이스에서 사용할 수 없습니다.

## <a name="week-of-january-7-2019"></a>2019년 1월 7일의 주

### <a name="app-management"></a>앱 관리

#### <a name="intune-app-pin----2298397---"></a>Intune 앱 PIN <!-- 2298397 -->
IT 관리자는 이제 최종 사용자의 Intune 앱 PIN을 변경해야 할 때까지 최종 사용자가 대기할 수 있는 기간(일)을 구성할 수 있습니다. 새 설정은 *다음 일마다 PIN 다시 설정*이며 Azure Portal에서 **Intune** > **클라이언트 앱** > **앱 보호 정책** > **정책 만들기** > **설정** > **액세스 요구 사항**을 선택하여 사용할 수 있습니다. [iOS](app-protection-policy-settings-ios.md) 및 [Android](app-protection-policy-settings-android.md) 디바이스에서 사용 가능하며, 이 기능은 양의 정수 값을 지원합니다.


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune 디바이스 보고 필드 <!-- 2748738 -->
Intune은 앱 등록 ID, Android 제조업체, 모델 및 보안 패치 버전을 비롯한 추가 디바이스 보고 필드와 iOS 모델을 제공합니다. Intune에서 이러한 필드를 사용하려면 **클라이언트 앱** > **앱 보호 상태**를 선택하고 **앱 보호 보고서: iOS, Android**를 선택합니다. 또한 이러한 매개 변수를 사용하여 디바이스 제조업체(Android)의 **허용** 목록, 디바이스 모델(Android 및 iOS)의 **허용** 목록 및 최소 Android 보안 패치 버전 설정을 구성할 수 있습니다. 


### <a name="device-configuration"></a>디바이스 구성

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>관리 템플릿은 공개 미리 보기로 제공되고 자체 구성 프로필 로 이동됨 <!-- 3322847 -->

Intune의 관리 템플릿(**디바이스 구성** > **관리 템플릿**)은 현재 비공개 미리 보기로 제공됩니다. 이 업데이트 포함:

- 관리 템플릿에는 Intune에서 관리할 수 있는 약 300개 설정이 포함됩니다. 이전에는 이러한 설정이 그룹 정책 편집기에만 있었습니다.
- 관리 템플릿은 공개 미리 보기로 제공됩니다.
- 관리 템플릿은 **디바이스 구성** > **관리 템플릿**에서 **디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Windows 10 이상** 선택, **프로필 유형**에서 **관리 템플릿** 선택으로 이동됩니다.
- 보고가 사용하도록 설정됩니다.

이 기능에 대해 자세히 알아보려면 [그룹 정책 설정을 구성하기 위한 Windows 10 템플릿](administrative-templates-windows.md)으로 이동합니다.

적용 대상: Windows 10 이상

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>S/MIME를 사용하여 사용자의 여러 디바이스를 암호화 및 서명 <!-- 1333642 -->
이 업데이트에는 가져온 새 인증서 프로필을 사용하는 S/MIME 이메일 암호화가 포함됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** &gt; 플랫폼 선택 &gt; **PKCS 가져온 인증서** 프로필 유형). Intune에서 PFX 형식의 인증서를 가져올 수 있습니다. 그런 다음, Intune은 단일 사용자에 의해 등록된 여러 디바이스에 이러한 동일한 인증서를 제공할 수 있습니다. 다음도 포함되어 있습니다.
- 네이티브 iOS 이메일 프로필은 PFX 형식의 가져온 인증서를 사용하는 S/MIME 암호화 활성화를 지원합니다.
- Windows Phone 10 디바이스의 네이티브 메일 앱은 S/MIME 인증서를 자동으로 사용합니다.
- 여러 플랫폼에서 개인 인증서를 제공할 수 있습니다. 하지만 모든 이메일 앱이 S/MIME를 지원하지는 않습니다.
- 다른 플랫폼에서 S/MIME를 활성화하도록 메일 앱을 수동으로 구성해야 할 수 있습니다.  
- S/MIME 암호화를 지원하는 이메일 앱은 해당 게시자의 인증서 저장소에서 읽기와 같은 MDM에서 지원할 수 없는 방식으로 S/MIME 이메일 암호화에 대한 인증서 가져오기를 처리할 수 있습니다.
이 기능에 대한 자세한 내용은 [이메일 서명 및 암호화를 위한 S/MIME 개요](certificates-s-mime-encryption-sign.md)를 참조하세요.
지원 됩니다. Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Windows 10 이상 디바이스에서 DNS 설정을 사용할 때 자동으로 규칙을 연결 및 유지하는 새 옵션 <!-- 1333665, 2999078 -->
Windows 10 이상 디바이스에서는 contoso.com과 같은 도메인 확인을 위한 DNS 서버 목록을 포함하는 VPN 구성 프로필을 만들 수 있습니다. 이 업데이트에는 이름 확인(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **Windows 10 이상** 선택 > 프로필 유형에서 **VPN** 선택 > **DNS 설정** >**추가**)에 대한 새 설정이 포함됩니다. 
- **자동으로 연결**: **사용하도록 설정**한 경우 디바이스가 입력한 도메인(예: contoso.com)에 연결되면 디바이스가 자동으로 VPN에 연결됩니다.
- **영구**: 기본적으로 모든 NRPT(이름 확인 정책 테이블) 규칙은 디바이스가 이 VPN 프로필을 사용하여 연결되어 있는 한 활성 상태입니다. NRPT 규칙에서 이 설정이 **사용하도록 설정**되면 VPN 연결이 끊어지더라도 디바이스에서 규칙이 활성 상태로 유지됩니다. 규칙은 VPN 프로필이 제거되거나 PowerShell을 통해 규칙을 수동으로 제거할 때까지 유지됩니다.
[Windows 10 VPN 설정](vpn-settings-windows-10.md)에서는 설정을 설명합니다. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Windows 10 디바이스의 VPN 프로필에 신뢰할 수 있는 네트워크 검색 사용 <!-- 1500165 -->
신뢰할 수 있는 네트워크 검색을 사용하는 경우 사용자가 이미 신뢰할 수 있는 네트워크에 있을 때 VPN 프로필에서 자동으로 VPN에 연결되지 않도록 할 수 있습니다. 이 업데이트를 사용하여 DNS 접미사를 추가하여 Windows 10 이상을 실행하는 디바이스에서 신뢰할 수 있는 네트워크 검색을 사용하도록 설정할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼의 **Windows 10 이상** > 프로필 유형의 **VPN**).
[Windows 10 VPN 설정](vpn-settings-windows-10.md)에는 현재 VPN 설정이 나열됩니다.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>여러 사용자가 사용하는 Windows Holographic for Business 디바이스 관리 <!-- 1907917, 1063203 -->
현재는 사용자 지정 OMA-URI 설정을 사용하여 Windows 10 및 Windows Holographic for Business 디바이스에서 공유 PC 설정을 구성할 수 있습니다. 이 업데이트를 사용하여 새 프로필을 추가하여 공유 디바이스 설정을 구성합니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **공유 다중 사용자 디바이스**).
이 기능에 대해 자세히 알아보려면 [공유 디바이스를 관리하기 위한 Intune 설정](shared-user-device-settings.md)으로 이동합니다.
적용 대상: Windows 10 이상, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>새 Windows 10 업데이트 설정 <!--2626030  2512994  -->
[Windows 10 업데이트 링](windows-update-for-business-configure.md)의 경우 다음을 구성할 수 있습니다.
- **자동 업데이트 동작** - 새 옵션 사용, *2018년 10월 업데이트*를 실행 중인 머신의 Windows 10 머신에서 원래 자동 업데이트 설정을 복원하도록 *기본값으로 다시 설정*
- **사용자가 Windows 업데이트를 일시 중지하는 것을 차단** - 사용자가 머신의 *설정*에서 업데이트 설치를 일시 중지하는 기능을 차단 또는 허용할 수 있는 새 소프트웨어 업데이트 설정 구성 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 메일 프로필은 S/MIME 서명 및 암호화를 사용할 수 있음 <!-- 2662949 -->
다양한 설정을 포함하는 이메일 프로필을 만들 수 있습니다. 이 업데이트에는 iOS 디바이스에서 이메일 통신 서명 및 암호화에 사용할 수 있는 S/MIME 설정이 포함됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **iOS** 선택 > 프로필 유형에서 **이메일**).
[iOS 이메일 구성 설정](email-settings-ios.md)에는 설정이 나열됩니다.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>일부 BitLocker 설정은 Windows 10 Pro Edition을 지원함 <!-- 2727036 -->
BitLocker를 포함하여 Windows 10 디바이스에서 엔드포인트 보호 설정을 설정하는 구성 프로필을 만들 수 있습니다. 이 업데이트는 일부 BitLocker 설정에 대한 Windows 10 Professional Edition 지원을 추가합니다. 이러한 보호 설정을 보려면 [Windows 10용 엔드포인트 보호 설정](endpoint-protection-windows-10.md#windows-encryption)으로 이동합니다.

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>공유 디바이스 구성은 Azure Portal에서 iOS 디바이스의 잠금 화면 메시지로 이름이 바뀜<!-- 2809362 -->
iOS 디바이스용 구성 프로필을 만들 경우 **공유 디바이스 구성** 설정을 추가하여 잠금 화면에 특정 텍스트를 표시할 수 있습니다. 이 업데이트에는 다음 변경 내용이 포함됩니다. 
- Azure Portal의 **공유 디바이스 구성** 설정은 “잠금 화면 메시지(감독 모드인 경우에만)”으로 이름이 바뀝니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **iOS** 선택 > 프로필 유형에서 **디바이스 기능** 선택 > **잠금 화면 메시지**).
- 잠금 화면 메시지를 추가하면 일련 번호, 디바이스 이름 또는 또 다른 디바이스별 값을 **자산 태그 정보** 및 **잠금 화면 각주**의 변수로 삽입할 수 있습니다. 예를 들어 중괄호를 사용하여 `Device name: {{devicename}}` 또는 `Serial number is {{serialnumber}}`를 입력할 수 있습니다. [iOS 토큰](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)에는 사용할 수 있는 사용 가능한 토큰이 나열됩니다.
[잠금 화면에 메시지를 표시하기 위한 설정](shared-device-settings-ios.md)에는 설정이 나열됩니다.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>iOS 디바이스에 추가된 새 앱 스토어, 문서 보기, 게임 디바이스 제한 사항 설정 <!-- 2827760-->
**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 플랫폼에 대해 > **디바이스 제한** 프로필 유형에 대해 > **앱 스토어, 문서 보기, 게임**에서 다음 설정이 추가되었습니다. 관리되는 앱이 관리되지 않는 연락처 계정에 연락처를 쓸 수 있도록 허용. 관리되지 않는 앱이 관리되는 연락처 계정에서 연락처를 읽을 수 있도록 허용. 이러한 설정을 보려면 [iOS 디바이스 제한 사항](device-restrictions-ios.md#app-store-doc-viewing-gaming)으로 이동합니다.

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Android 엔터프라이즈 디바이스 소유자 디바이스의 새 알림, 힌트 및 Keyguard 설정 <!-- 3201839 3201843 -->
이 업데이트에는 디바이스 소유자로 실행할 경우 Android 엔터프라이즈 디바이스의 여러 가지 새로운 기능이 포함됩니다. 이러한 기능을 사용하려면 **디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Android 엔터프라이즈** 선택 > **프로필 유형**에서 **디바이스 소유자만** 선택 > **디바이스 제한 사항**으로 이동합니다.

새로운 기능은 다음과 같습니다. 

- 들어오는 호출, 시스템 경고, 시스템 오류 등을 포함하여 시스템 알림이 표시되지 않도록 설정
- 처음 열린 앱에 대한 시작 자습서 및 힌트 건너뛰기 제안
- 카메라, 알림, 지문 잠금 해제 등의 고급 Keyguard 설정을 사용하지 않도록 설정


설정을 보려면 [Android 엔터프라이즈 디바이스 제한 사항 설정](device-restrictions-android-for-work.md)으로 이동합니다.

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android 엔터프라이즈 디바이스 소유자 디바이스는 Always On VPN 연결을 사용할 수 있음 <!-- 3202194 -->
이 업데이트에서는 Android 엔터프라이즈 디바이스 소유자 디바이스에서 Always on VPN 연결을 사용할 수 있습니다. 상시 VPN 연결은 계속 연결된 상태로 유지되거나 사용자가 디바이스를 잠금 해제한 경우, 디바이스가 다시 시작된 경우 또는 무선 네트워크가 변경된 경우 바로 다시 연결됩니다. 또한 VPN 연결이 활성화될 때까지 모든 네트워크 트래픽을 차단하는 “잠금” 모드로 연결 상태를 전환할 수도 있습니다.
**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) > **디바이스 제한 사항**(디바이스 소유자만) > **연결** 설정에서 Always-on VPN을 사용하도록 설정할 수 있습니다. 설정을 보려면 [Android 엔터프라이즈 디바이스 제한 사항 설정](device-restrictions-android-for-work.md)으로 이동합니다.

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 디바이스의 작업 관리자에서 프로세스를 종료하는 새로운 설정 <!-- 3285177 --> 
이 업데이트에는 Windows 10 디바이스의 작업 관리자를 사용하여 프로세스를 종료하는 새로운 설정이 포함됩니다. 디바이스 구성 프로필(**디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Windows 10** 선택 > **프로필 유형**에서 **디바이스 제한 사항** 선택 > **일반** 설정)을 사용하여 이 설정을 허용하거나 차단하도록 선택합니다.
이러한 설정을 보려면 [Windows 10 디바이스 제한 사항 설정](device-restrictions-windows-10.md)으로 이동합니다.
적용 대상: Windows 10 이상


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>자세한 등록 제한 실패 메시징 <!-- 3111564 -->
등록 제한 사항이 충족되지 않으면 더 자세한 오류 메시지가 제공됩니다. 이러한 메시지를 보려면 **Intune** > **문제 해결**로 이동하고 등록 실패 테이블을 확인합니다. 자세한 내용은 [등록 실패 목록](help-desk-operators.md#configuration-policies-reference)을 참조하세요.



### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="tenant-status-dashboard-----1124854---"></a>테넌트 상태 대시보드 <!-- 1124854 -->
새 [테넌트 상태 페이지](tenant-status.md)는 테넌트에 대한 상태와 관련된 세부 정보를 볼 수 있는 단일 위치를 제공합니다.  대시보드는 4개 영역으로 구분됩니다.
- **테넌트 세부 정보** - 테넌트 이름 및 위치, MDM 권한, 테넌트에 등록된 총 디바이스 수, 라이선스 수를 포함하는 정보를 포함합니다. 이 섹션은 테넌트에 대한 현재 서비스 릴리스도 나열합니다.
- **커넥터 상태** - 사용자가 구성한 사용 가능한 커넥터에 대한 정보를 표시하고 아직 활성화하지 않은 항목도 나열할 수 있습니다.  
   각 커넥터의 현재 상태에 따라 정상, 경고 또는 비정상으로 플래그가 지정됩니다. 커넥터를 선택하여 세부 정보를 드릴스루하고 보거나 추가 정보를 구성합니다.
-  **Intune Service Health** - 테넌트의 활성 인시던트 또는 중단 상태에 대한 세부 정보를 표시합니다. 이 섹션의 정보는 Office Message Center에서 직접 검색됩니다.
-  **Intune 뉴스** - 테넌트에 대한 활성 메시지를 표시합니다. 메시지는 테넌트에서 최신 Intune 기능을 받는 경우 알림과 같은 항목을 포함합니다.  이 섹션의 정보는 Office Message Center에서 직접 검색됩니다.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Windows 10용 회사 포털에서 새 도움말 및 지원 환경 <!-- 1488939-->
새 회사 포털 도움말 및 지원 페이지는 사용자가 문제를 해결하고 앱 및 액세스 문제에 대한 도움을 요청하는 데 도움이 됩니다. 새 페이지에서 오류 및 진단 로그 세부 정보에 대한 이메일을 보내고 해당 조직의 기술 지원팀 세부 정보를 찾을 수 있습니다. 또한 관련 Intune 설명서에 대한 링크를 사용하여 FAQ 섹션을 찾을 수도 있습니다. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Intune에 대한 새 도움말 및 지원 환경 <!-- #3307080 -->
다음 며칠 동안 새 도움말 및 지원 환경을 모든 테넌트에게 롤아웃합니다. 이 새로운 환경은 Intune에 대해 사용할 수 있으며 [Azure Portal](https://portal.azure.com/)에서 Intune 블레이드를 사용하는 경우에 액세스할 수 있습니다.
새 환경을 사용하면 문제를 사용자 고유의 언어로 설명하고, 문제 해결 인사이트와 웹 기반 수정 콘텐츠를 받을 수 있습니다. 이러한 솔루션은 사용자 문의에 따라 구동되는 규칙 기반 기계 학습 알고리즘을 통해 제공됩니다. 문제별 지침 외에도 새 사례 만들기 워크플로를 사용하여 이메일 또는 전화를 통해 지원 사례를 엽니다. 이 새로운 환경은 도움말 및 지원을 열 때 제공되는 콘솔의 영역에 따라 미리 선택된 옵션의 정적 집합에 대한 이전의 도움말 및 지원 환경을 대체합니다. 자세한 내용은 [Microsoft Intune에 대한 지원을 받는 방법](get-support.md)을 참조하세요.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="scope-tags-for-apps----1081941---"></a>앱의 범위 태그 <!-- 1081941 -->
범위 태그를 만들어 역할 및 앱에 대한 액세스를 제한할 수 있습니다. 해당 범위 태그가 할당된 역할이 있는 사용자만 앱에 액세스할 수 있도록 앱에 범위 태그를 추가할 수 있습니다. 현재는 관리되는 Google Play에서 Intune에 추가된 앱 또는 Apple VPP(Volume Purchase Program)를 통해 구매한 앱에는 범위 태그를 할당할 수 없습니다(향후 지원될 예정임). 자세한 내용은 [범위 태그를 사용하여 정책 필터링](scope-tags.md)을 참조하세요.



## <a name="week-of-december-10-2018"></a>2018년 12월 10일 주

### <a name="app-management"></a>앱 관리

#### <a name="updates-for-application-transport-security----748318---"></a>애플리케이션 전송 보안 업데이트 <!-- 748318 -->

Microsoft Intune은 TLS(전송 계층 보안) 1.2 이상을 지원하여 동급 최고의 암호화 기능을 제공하고, Intune의 보안을 기본적으로 강화하며, Microsoft Office 365와 같은 다른 Microsoft 서비스와 호환될 수 있도록 합니다. 이 요구 사항을 충족하기 위해 iOS 및 macOS 회사 포털은 Apple의 업데이트된 ATS(애플리케이션 전송 보안) 요구 사항(TLS 1.2 이상도 필요)을 적용합니다. ATS는 HTTPS를 통한 모든 앱 통신에서 보다 엄격한 보안을 적용하는 데 사용됩니다. 이 변경 사항은 iOS 및 macOS 회사 포털 앱을 사용하는 Intune 고객에게 영향을 줍니다. 자세한 내용은 [Intune 지원 블로그](https://aka.ms/compportalats)를 참조하세요.

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune 앱 SDK는 256비트 암호화 키를 지원함 <!-- 1832174 -->
이제 Android용 Intune 앱 SDK는 앱 보호 정책에서 암호화를 사용하도록 설정할 때 256비트 암호화 키를 사용합니다. SDK는 이전 SDK 버전을 사용하는 콘텐츠 및 앱과 호환성을 위해 128비트 키 지원을 계속 제공합니다.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>macOS 디바이스에 필요한 Microsoft 자동 업데이트 버전 4.5.0 <!-- 3503442 -->
회사 포털 및 기타 Office 애플리케이션에 대한 업데이트를 계속 받으려면 Intune에서 관리하는 macOS 디바이스는 Microsoft 자동 업데이트 4.5.0으로 업그레이드해야 합니다. 사용자가 해당 Office 앱에 이미 이 버전을 사용하고 있을 수 있습니다.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune에는 macOS 10.12 이상이 필요함 <!-- 2827778 -->
Intune에는 이제 macOS 버전 10.12 이상이 필요합니다. 이전 macOS 버전을 사용하는 디바이스는 Intune에 등록하는 데 회사 포털을 사용할 수 없습니다. 지원 및 새로운 기능을 받으려면 사용자는 해당 디바이스를 macOS 10.12 이상으로 업그레이드하고 회사 포털을 최신 버전으로 업그레이드해야 합니다.

## <a name="week-of-november-26-2018"></a>2018년 11월 26일 주

### <a name="app-management"></a>앱 관리

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>회사 소유의 감독되는 iOS 디바이스에서 앱 제거 <!-- 1281677 -->

회사 소유의 감독되는 iOS 디바이스에서 앱을 제거할 수 있습니다. **제거** 할당 유형을 사용하여 사용자 또는 디바이스 그룹을 대상으로 하여 앱을 제거할 수 있습니다. 개인 또는 감독되지 않은 iOS 디바이스의 경우 Intune을 사용하여 설치된 앱만 계속 제거할 수 있습니다.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Intune Win32 앱 콘텐츠 다운로드 <!-- 2617320 -->
Windows 10 RS3 이상 클라이언트는 Windows 10 클라이언트의 배달 최적화 구성 요소를 사용하여 Intune Win32 앱 콘텐츠를 다운로드합니다. 배달 최적화는 기본적으로 켜져 있는 피어 투 피어 기능을 제공합니다. 배달 최적화는 그룹 정책을 통해 구성되고 나중에는 Intune MDM을 통해 구성될 수 있습니다. 자세한 내용은 [Windows 10 배달 최적화](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)를 참조하세요. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>최종 사용자 디바이스 및 앱 콘텐츠 메뉴 <!-- 2771453 -->
최종 사용자는 이제 디바이스와 앱에서 상황에 맞는 메뉴를 사용하여 디바이스 이름 바꾸기 또는 준수 확인 같은 일반적인 작업을 트리거할 수 있습니다.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>관리 홈 화면(Managed Home Screen) 앱에서 사용자 지정 배경 설정 <!-- 3041945 -->
Android 엔터프라이즈, 다중 앱, 키오스크 모드 디바이스에서 관리 홈 화면 앱의 배경 모양을 사용자 지정할 수 있는 설정을 추가합니다.  **사용자 지정 URL 배경**을 구성하려면 Azure Portal에서 Intune &gt; 디바이스 구성으로 차례로 이동합니다. 현재 디바이스 구성 프로필을 선택하거나 새 프로필을 만들어 키오스크 설정을 편집합니다.
키오스크 설정을 확인하려면 [Android Enterprise 디바이스 제한 사항](device-restrictions-android-for-work.md)을 참조하세요.

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>앱 보호 정책 할당 저장 및 적용 <!-- 3104570 -->
이제 [앱 보호 정책 할당](app-protection-policies.md#deploy-a-policy-to-users)을 더 효율적으로 제어할 수 있습니다. ‘할당’을 선택하여 정책 할당을 설정하거나 편집할 경우 변경을 적용하기 전에 구성을 **저장**해야 합니다. 포함 또는 제외 목록의 변경 내용을 저장하지 않고 모든 변경 내용을 지우려면 **취소**를 사용합니다.  저장 또는 취소를 선택하도록 요구하여 의도한 사용자에게만 앱 보호 정책을 할당합니다.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Windows 10 이상에 대한 새 Microsoft Edge 브라우저 설정 <!-- 3174639 -->
이 업데이트에는 디바이스에서 Microsoft Edge 브라우저를 제어하고 관리하는 데 도움이 되는 새 설정이 포함됩니다. 이러한 설정 목록은 [Windows 10(이상)에 대한 디바이스 제한](device-restrictions-windows-10.md#microsoft-edge-browser)을 참조하세요.

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>앱 보호 정책을 사용하는 새 앱 지원 <!-- 3330037 -->
이제 [Intune 앱 보호 정책](app-protection-policies.md)을 사용하여 다음 앱을 관리할 수 있습니다.
- Stream(iOS)
- To DO(Android, iOS)
- PowerApps(Android, iOS)
- Flow(Android, iOS)

앱 보호 정책을 사용하여 회사 데이터를 보호하고 다른 Intune 정책 관리 앱과 같은 앱의 데이터 전송을 제어합니다. 참고: 콘솔에 Flow가 아직 표시되지 않으면 앱 보호 정책을 만들거나 편집할 때 Flow를 추가합니다. 이렇게 하려면 **+ 추가 앱** 옵션을 사용한 다음, 입력 필드에 Flow의 *앱 ID*를 지정합니다. Android의 경우 *com.microsoft.flow*를 사용하고 iOS의 경우 *com.microsoft.procsimo*를 사용합니다.


### <a name="device-configuration"></a>디바이스 구성

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>iOS 및 macOS 버전 번호와 빌드 번호가 <!-- 1892471 -->로 표시됩니다.
**디바이스 준수** > **디바이스 준수**에서 iOS 및 macOS 운영체제 버전이 표시되고 준수 정책에 사용할 수 있습니다. 이 업데이트에는 두 플랫폼에 모두 구성 가능한 빌드 번호가 포함됩니다.
보안 업데이트가 릴리스되는 경우 Apple에서는 일반적으로 버전 번호는 그대로 유지하지만 빌드 번호는 업데이트합니다. 준수 정책의 빌드 번호를 사용하면 취약성 업데이트가 설치되어 있는지 쉽게 확인할 수 있습니다.
이 기능을 사용하려면 [iOS](compliance-policy-create-ios.md#device-health) 및 [macOS](compliance-policy-create-mac-os.md#device-properties) 규정 준수 정책을 참조하세요.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>업데이트 링이 Windows 10 이상의 배달 최적화 설정으로 대체됨 <!-- 2753807 -->
배달 최적화는 Windows 10 이상의 새로운 구성 프로필입니다. 이 기능은 조직의 디바이스에 소프트웨어 업데이트를 배달하는 보다 간소화된 환경을 제공합니다. 또한 이 업데이트를 통해 구성 프로필을 사용하여 새 업데이트 링과 기존 업데이트 링의 설정을 배달할 수 있습니다.
배달 최적화 구성 프로필을 구성하려면 [Windows 10 이상 배달 최적화 설정](delivery-optimization-windows.md)을 참조하세요.

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>iOS 및 macOS 디바이스에 추가된 새 디바이스 제한 설정 <!-- 2827760 -->
이 업데이트는 iOS 12와 함께 릴리스된 iOS 및 macOS 디바이스용 새 설정을 포함합니다.

**iOS 설정**: 
- 일반: 앱 제거 차단(감독 모드인 경우에만)
- 일반: USB 제한 모드 차단(감독 모드인 경우에만)
- 일반: 자동 날짜 및 시간 강제 적용(감독 모드인 경우에만)
- 암호: 암호 자동 채우기 차단(감독 모드인 경우에만)
- 암호: 암호 근접 요청 차단(감독 모드인 경우에만)
- 암호: 암호 공유 차단(감독 모드인 경우에만)

**macOS 설정**: 
- 암호: 암호 자동 채우기 차단
- 암호: 암호 근접 요청 차단
- 암호: 암호 공유 차단

이러한 설정에 대한 자세한 내용은 [iOS](device-restrictions-ios.md) 및 [macOS](device-restrictions-macos.md) 디바이스 제한 설정을 참조하세요.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>등록 상태 페이지에서 추적되는 앱 선택 <!-- 2531007 -->
등록 상태 페이지에서 추적할 앱을 선택할 수 있습니다. 이러한 앱이 설치될 때까지 사용자는 디바이스를 사용할 수 없습니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>일련 번호로 Autopilot 디바이스 검색 <!--2595788 -->
이제 일련 번호로 Autopilot 디바이스를 검색할 수 있습니다. 이렇게 하려면 **디바이스 등록** > **Windows 등록** > **디바이스**를 선택하고, **일련 번호로 검색** 상자에 일련 번호를 입력한 다음, Enter 키를 누릅니다.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Office ProPlus 설치 추적 <!--2620217 -->
사용자는 [등록 상태 페이지](windows-enrollment-status.md)를 사용하여 [Office ProPlus](apps-add-office365.md)의 설치 진행률을 추적할 수 있습니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 토큰 만료 또는 회사 포털 라이선스 부족에 대한 경고 <!-- 2237572 -->
VPP(대량 구매 프로그램)를 사용하여 DEP 등록 중 회사 포털을 사전 프로비전하는 경우 Intune은 VPP 토큰이 만료되려고 하는 경우 및 회사 포털에 대한 라이선스가 부족한 경우 경고를 표시합니다.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Apple School Manager 계정에 대한 macOS 장비 등록 프로그램 지원 <!--3006133 -->
이제 Intune은 Apple School Manager 계정에 대한 macOS 디바이스에서 장비 등록 프로그램을 사용할 수 있도록 지원합니다.  자세한 내용은 [Apple School Manager 또는 장비 등록 프로그램을 통해 자동으로 macOS 디바이스 등록](device-enrollment-program-enroll-macos.md)을 참조하세요.

### <a name="new-intune-device-subscription-sku---3312071--"></a>새 Intune 디바이스 구독 SKU <!--3312071-->
엔터프라이즈 내 디바이스 관리 비용을 절감하기 위해 새 디바이스 기반 구독 SKU를 이제 사용할 수 있습니다. 이 Intune 디바이스 SKU는 월별로 디바이스당 사용이 허가됩니다. 가격은 라이선스 프로그램에 따라 다릅니다. Office 관리 포털을 통해 바로 사용할 수 있으며 EA([기업계약](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2)), MPSA([Microsoft 제품 및 서비스 계약](https://www.microsoft.com/licensing/mpsa/default)), [Microsoft 오픈 계약](https://partner.microsoft.com/licensing/licensing-agreements) 및 CSP([클라우드 솔루션 공급자](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453))를 통해 사용할 수 있습니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Android 디바이스에서 키오스크 모드를 일시적으로 중지하여 변경 <!-- 3041935 -->
다중 앱 키오스크 모드에서 Android 디바이스를 사용하는 경우 IT 관리자가 디바이스를 변경해야 할 수 있습니다. 이 업데이트에는 IT 관리자가 PIN을 사용하여 일시적으로 키오스크 모드를 중지하고 전체 디바이스에 액세스할 수 있게 하는 새 다중 앱 키오스크 설정이 포함됩니다.
키오스크 설정을 확인하려면 [Android Enterprise 디바이스 제한 사항](device-restrictions-android-for-work.md)을 참조하세요.

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Android 엔터프라이즈 키오스크 디바이스에서 가상 홈 단추 사용 <!-- 3042021 -->
사용자는 새 설정을 통해 해당 디바이스의 소프트 키 단추를 탭하여 관리 홈 화면 앱과 다중 앱 키오스크 디바이스에 할당된 다른 앱 간에 전환할 수 있습니다. 이 설정은 사용자의 키오스크 앱에서 "뒤로" 단추에 적절하게 응답하지 않는 시나리오에서 특히 유용합니다. 회사 소유의 단일 사용 Android 디바이스에 이 설정을 구성할 수 있습니다. **가상 홈 단추**를 사용하거나 사용하지 않도록 설정하려면 Azure Portal에서 Intune &gt; 디바이스 구성으로 차례로 이동합니다. 현재 디바이스 구성 프로필을 선택하거나 새 프로필을 만들어 키오스크 설정을 편집합니다.
키오스크 설정을 확인하려면 [Android Enterprise 디바이스 제한 사항](device-restrictions-android-for-work.md)을 참조하세요.

## <a name="week-of-november-12-2018"></a>2018년 11월 12일 주

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>iOS용 Citrix SSO에 대한 NAC(네트워크 액세스 제어) <!-- 3259404 -->지원

Citrix는 Intune에서 iOS용 Citrix SSO에 대해 NAC(네트워크 액세스 제어)를 허용하도록 Citrix Gateway 업데이트를 출시했습니다. Intune에서 VPN 프로필 내에 디바이스 ID를 포함하도록 선택한 후 이 프로필을 iOS 디바이스에 푸시할 수 있습니다. 이 기능을 사용하려면 Citrix Gateway의 최신 업데이트를 설치해야 합니다.

[iOS 디바이스에서 VPN 설정 구성](vpn-settings-ios.md#base-vpn-settings)에서는 몇 가지 추가 요구 사항을 포함하여 NAC 사용에 대한 자세한 정보를 제공합니다. 

## <a name="week-of-november-5-2018"></a>2018년 11월 5일 주

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>iOS 메일 프로필에서 iOS 12 OAuth 지원 <!--2155106 -->

Intune의 iOS 이메일 프로필은 iOS 12 OAuth(Open Authorization)를 지원합니다. 이 기능을 확인하려면 새 프로필(플랫폼용 **디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** > 프로필 유형에 대한 **이메일**)을 만들거나 기존 iOS 이메일 프로필을 업데이트합니다. 사용자에게 이미 배포된 프로필에서 OAuth를 사용하도록 설정하면 사용자에게 다시 인증하고 이메일을 다시 다운로드하라는 메시지가 표시됩니다.

[iOS 이메일 프로필](email-settings-ios.md)에는 이메일 프로파일에서 OAuth 사용에 대한 자세한 정보가 있습니다.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>하이브리드 Azure Active Directory 조인 디바이스에 대한 Autopilot 지원(미리 보기) <!-- 1048100-->
이제 Autopilot을 사용하여 하이브리드 Azure Active Directory 조인 디바이스를 설정할 수 있습니다. 하이브리드 Autopilot 기능을 사용하려면 디바이스가 조직의 네트워크에 조인되어 있어야 합니다. 자세한 내용은 [Intune 및 Windows Autopilot를 사용하여 하이브리드 Azure AD 조인 디바이스 배포](windows-autopilot-hybrid.md)를 참조하세요.
이 기능은 앞으로 며칠 동안 사용자 기반 전체에 롤아웃됩니다. 따라서 계정에 롤아웃될 때까지 다음 단계를 수행하지 못할 수도 있습니다.

## <a name="week-of-october-29-2018"></a>2018년 10월 29일이 있는 주

### <a name="app-management"></a>앱 관리

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>지정된 시간 제한 이후 비생체 인식 PIN 요구 <!-- 1506985 -->
관리자가 지정한 시간 제한 후에 비생체 인식 PIN을 요구하면, Intune에서 회사 데이터에 액세스하는 데 사용하는 생체 인식 ID를 제한하여 MAM(모바일 애플리케이션 관리) 지원 앱에 향상된 보안을 제공합니다. 이 설정은 Touch ID(iOS), Face ID(iOS), Android 생체 인식 또는 향후의 다른 생체 인식 인증 방법을 사용하여 APP/MAM 지원 애플리케이션에 액세스하는 사용자에게 영향을 줍니다. 이러한 설정을 사용하면 Intune 관리자가 사용자 액세스를 더 자세히 제어할 수 있으므로 여러 지문 또는 다른 생체 인식 액세스 방법을 사용하는 디바이스로 인해 회사 데이터가 잘못된 사용자에게 노출될 수 있는 경우를 제거할 수 있습니다. Azure Portal에서 **Microsoft Intune**을 엽니다. **클라이언트 앱** > **앱 보호 정책** > **정책 추가** > **설정**을 차례로 선택합니다. 특정 설정에 대한 **액세스** 섹션을 찾습니다. 액세스 설정에 대한 자세한 내용은 [iOS 설정](app-protection-policy-settings-ios.md#access-requirements) 및 [Android 설정](app-protection-policy-settings-android.md#access-requirements)을 참조하세요.

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM 등록 디바이스의 Intune APP 데이터 전송 설정 <!-- 2244713 -->
iOS MDM 등록 디바이스의 Intune APP 데이터 전송 설정에 대한 제어를 등록된 사용자의 ID(UPN(사용자 계정 이름)이라고도 함) 지정과 분리할 수 있습니다. IntuneMAMUPN을 사용하지 않는 관리자는 동작 변경을 관찰하지 않습니다. 이 기능을 사용할 수 있게 되면 IntuneMAMUPN을 사용해 등록된 디바이스의 데이터 전송 동작을 제어하는 관리자가 새로운 설정을 살펴보고 필요에 따라 APP 설정을 업데이트해야 합니다.

#### <a name="windows-10-win32-apps----2617325---"></a>Windows 10 Win32 앱 <!-- 2617325 -->
디바이스의 모든 사용자에 대해 앱을 설치하는 대신 개별 사용자에 대해 사용자 컨텍스트에 맞게 Win32 앱을 설치하도록 구성할 수 있습니다.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Windows Win32 앱 및 PowerShell 스크립트 <!-- 2617330 -->
최종 사용자는 더 이상 디바이스에 로그인하여 Win32 앱을 설치하거나 PowerShell 스크립트를 실행할 필요가 없습니다. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>클라이언트 앱 설치 문제 해결 <!-- 1363711 -->
**문제 해결** 블레이드에서 **앱 설치**라는 열을 검토하여 클라이언트 앱의 설치 성공 문제를 해결할 수 있습니다. **문제 해결** 블레이드를 보려면 Intune 포털의 **도움말 및 지원** 아래에서 **문제 해결**을 선택합니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>iOS VPN 클라이언트에서 네트워크 액세스 제어 지원 <!-- 1333693 -->
이 업데이트를 사용하면 iOS용 Cisco AnyConnect, F5 Access 및 Citrix SSO에 대한 VPN 구성 프로필을 만들 때 NAC(네트워크 액세스 제어)를 사용하도록 설정할 수 있는 새로운 설정이 있습니다. 디바이스의 NAC ID가 이 설정을 통해 VPN 프로필에 포함될 수 있습니다. 현재 이 새로운 NAC ID를 지원하는 VPN 클라이언트 또는 NAC 파트너 솔루션이 없지만, 지원되는 경우 [지원 블로그 게시물](ttps://aka.ms/iOS12_and_vpn)을 통해 계속 알려드리겠습니다.

NAC를 사용하려면 다음을 수행해야 합니다.
1. Intune에서 VPN 프로필에 디바이스 ID를 포함할 수 있도록 옵트인합니다.
2. NAC 공급자의 지침을 직접 사용하여 NAC 공급자 소프트웨어/펌웨어를 업데이트합니다.

iOS VPN 프로필 내의 이 설정에 대한 자세한 내용은 [Microsoft Intune에서 iOS 디바이스용 VPN 설정 추가](vpn-settings-ios.md)를 참조하세요. 네트워크 액세스 제어에 대한 자세한 내용은 [Intune과 NAC(네트워크 액세스 제어) 통합](network-access-control-integrate.md)을 참조하세요. 

적용 대상: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>이메일 프로필이 하나만 있는 경우에도 디바이스에서 이메일 프로필을 제거합니다 <!-- 1818139 -->
이전에는, 이메일 프로필이 유일한 *경우* 이 이메일 프로필을 디바이스에서 제거할 수 없었습니다. 이 업데이트를 통해 이러한 동작이 변경됩니다. 이제는 디바이스에 이메일 프로필이 유일한 경우에도 이메일 프로필을 삭제할 수 있습니다. 자세한 내용은 [Intune을 사용하여 디바이스에 이메일 설정 추가](email-settings-configure.md)를 참조하세요.

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell 스크립트 및 AAD <!-- 2309469 -->
Intune의 PowerShell 스크립트는 AAD 디바이스 보안 그룹을 대상으로 할 수 있습니다.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Android, Android Enterprise에 대한 새 “필수 암호 유형” 기본 설정<!-- 2649963 -->
새 준수 정책을 만들 때(**Intune** > **장치 준수** > **정책** > **정책 만들기** >  플랫폼에 대한 **Android** 또는 **Android 엔터프라이즈** > 시스템 보안) **필수 암호 유형**의 기본값은 다음과 같이 변경됩니다.

시작: 디바이스 기본값 종료: 숫자 이상

적용 대상: Android, Android Enterprise

이러한 설정을 확인하려면 [Android](compliance-policy-create-android.md) 및 [Android 엔터프라이즈](compliance-policy-create-android-for-work.md)로 이동합니다.

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Windows 10 Wi-Fi 프로필에서 미리 공유한 키 사용 <!-- 2662938 -->
이 업데이트를 사용하면 WPA/WPA2-개인 보안 프로토콜을 통해 PSK(미리 공유한 키)를 사용하여 Windows 10용 Wi-Fi 구성 프로필을 인증할 수 있습니다. 또한 Windows 10 2018년 10월 업데이트에서 디바이스에 대해 계량된 네트워크의 비용 구성을 지정할 수도 있습니다.

현재, 미리 공유한 키를 사용하려면 Wi-Fi 프로필을 가져오거나 사용자 지정 프로필을 만들어야 합니다. [Windows 10의 Wi-Fi 설정](wi-fi-settings-windows.md)에는 현재 설정이 나열됩니다. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>디바이스에서 PKCS 및 SCEP 인증서를 제거합니다 <!-- 3218390 -->
일부 시나리오에서는 그룹에서 정책을 제거하거나 구성 또는 규정 준수 배포를 삭제하거나 관리자가 기존 SCEP 또는 PKCS 프로필을 업데이트한 경우에도 PKCS 및 SCEP 인증서가 디바이스에 남아 있었습니다. 이 업데이트가 이러한 동작을 변경합니다. PKCS 및 SCEP 인증서가 디바이스에서 제거되는 경우와 이러한 인증서가 디바이스에 남아있는 시나리오가 있습니다. 이러한 시나리오의 경우 [Microsoft Intune에서 SCEP 및 PKCS 인증서 제거](remove-certificates.md)를 참조하세요.

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>규정 준수를 위해 macOS 디바이스에서 게이트키퍼 사용 <!-- 2504381 -->
이 업데이트에는 디바이스의 규정 준수를 평가하는 macOS 게이트키퍼가 포함되어 있습니다. 게이트키퍼 속성을 설정하려면 [macOS 디바이스에 대한 디바이스 준수 정책을 추가](compliance-policy-create-mac-os.md)합니다.


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="enrollment-abandonment-report----1382924---"></a>등록 중단 보고서 <!-- 1382924 -->
중단된 등록에 대한 세부 정보를 제공하는 새 보고서는 **디바이스 등록** > **모니터**에서 사용할 수 있습니다. 자세한 내용은[회사 포털 중단 보고서](enrollment-report-company-portal-abandon.md)를 참조하세요.

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>새 Azure Active Directory 사용 약관 기능 <!-- 2870393 -->
Azure Active Directory에는 기존 Intune 사용 약관을 대신 사용할 수 있는 사용 약관 기능이 있습니다. Azure AD 사용 약관은 표시할 조건 및 표시 방법에 있어서 유연성을 높이고 보다 나은 현지화 지원을 제공하며, 사용 약관을 렌더링하는 방식을 보다 잘 제어하고 보고 기능을 개선할 수 있도록 지원합니다. Azure AD 사용 약관 기능을 사용하려면 Enterprise Mobility + Security E3 도구 모음의 일부이기도 한 Azure Active Directory Premium P1이 필요합니다. 자세한 내용은 [사용자 액세스 문서에 대한 회사의 사용 약관 관리](terms-and-conditions-create.md)를 참조하세요.

#### <a name="android-device-owner-mode-support---3188762--"></a>Android 디바이스 소유자 모드 지원 <!--3188762-->
Samsung Knox 모바일 등록의 경우 이제 Intune에서 디바이스를 Android 디바이스 소유자 모드로 등록할 수 있습니다. WiFi 또는 셀룰러 네트워크의 사용자는 디바이스를 처음 켤 때 몇 번만 탭하면 등록할 수 있습니다. 자세한 내용은 [삼성 Knox 모바일 등록을 사용하여 Android 디바이스 자동 등록](android-samsung-knox-mobile-enroll.md)을 참조하세요.

### <a name="device-management"></a>디바이스 관리
#### <a name="new-settings-for-software-updates------1907869---"></a>소프트웨어 업데이트를 위한 새 설정 <!-- 1907869 -->  
- 이제 일부 알림을 구성하여 최신 소프트웨어 업데이트 설치를 완료하는 데 필요한 다시 시작 알림을 최종 사용자에게 표시할 수 있습니다.   
- 이제 BYOD 시나리오를 지원하는 작업 시간 외에 발생하는 다시 시작에 대한 다시 시작 경고 프롬프트를 구성할 수 있습니다.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>관련자 ID로 Windows Autopilot에 등록된 디바이스 그룹화 <!-- 2075110 -->
Configuration Manager를 통해 [기존 디바이스에 대해 Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)을 사용하여 등록할 때 이제 Intune에서 관련자 ID 기준으로 Windows 디바이스를 그룹화할 수 있도록 지원합니다. 관련자 ID는 Autopilot 구성 파일의 매개 변수입니다. Intune에서 자동으로 Azure AD 디바이스 특성인 [enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects)을 "OfflineAutopilotprofile-<correlator ID>"와 동일하게 설정합니다. 이것으로 오프라인 Autopilot 등록을 위한 enrollmentprofileName 특성을 통해 관련자 ID를 기반으로 임의의 Azure AD 동적 그룹을 만들 수 있습니다. 자세한 내용은 [기존 디바이스에 대한 Windows Autopilot](enrollment-autopilot.md#windows-autopilot-for-existing-devices)을 참조하세요.

#### <a name="intune-app-protection-policies----2984657---"></a>Intune 앱 보호 정책 <!-- 2984657 -->
Intune 앱 보호 정책을 사용하면 Microsoft Outlook 및 Microsoft Word와 같이 Intune으로 보호되는 앱에 대한 다양한 데이터 보호 설정을 구성할 수 있습니다. 개별 설정을 더 쉽게 찾을 수 있도록 [iOS](app-protection-policy-settings-ios.md) 및 [Android](app-protection-policy-settings-android.md) 모두에 대해 이러한 설정의 모양과 느낌을 변경했습니다. 정책 설정에는 다음 세 가지 범주가 있습니다.
- **데이터 재배치** - 이 그룹에는 잘라내기, 복사, 붙여넣기 및 다른 이름으로 저장 제한과 같은 DLP(데이터 손실 방지) 컨트롤이 포함되어 있습니다. 이러한 설정은 사용자가 앱의 데이터와 상호 작용하는 방식을 결정합니다.
- **액세스 요구 사항** - 이 그룹에는 최종 사용자가 작업 컨텍스트에 맞게 앱에 액세스하는 방법을 결정하는 앱별 PIN 옵션이 포함되어 있습니다.  
- **조건부 시작** - 이 그룹에는 최소 OS 설정, 탈옥 및 루팅된 디바이스 검색 및 오프라인 유예 기간과 같은 설정이 포함됩니다.  
  
설정의 기능은 변경되지 않았지만 정책 작성 흐름에서 작업할 때 더 쉽게 찾을 수 있습니다.

### <a name="intune-apps"></a>Intune 앱

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune에서 LOB 앱에 대해 최대 8GB의 패키지 크기 지원 <!-- 1727158 -->
Intune에서 LOB(기간 업무) 앱의 최대 패키지 크기가 8GB로 늘어났습니다. 자세한 내용은 [Microsoft Intune에 앱 추가](apps-add.md)를 참조하세요.

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>회사 포털 앱에 대한 사용자 지정 브랜드 이미지 추가 <!-- 1916266 -->
Microsoft Intune 관리자는 iOS 회사 포털 앱의 사용자 프로필 페이지에 배경 이미지로 표시될 사용자 지정 브랜드 이미지를 업로드할 수 있습니다. 회사 포털 앱 구성에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요.

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>최종 사용자 컴퓨터에서 Office를 업데이트할 때 Intune에서 Office 현지화 언어 유지 관리 <!-- 2971030 -->
Intune에서 최종 사용자의 머신에 Office를 설치하면 최종 사용자가 이전 .MSI Office 설치에서 사용한 것과 동일한 언어 팩을 자동으로 얻을 수 있습니다. 자세한 내용은 [Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당](apps-add-office365.md) 참조하세요.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Microsoft 365 디바이스 관리 포털의 새로운 Intune 지원 환경 <!-- 3076965 -->
[Microsoft 365 디바이스 관리 포털]( http://devicemanagement.microsoft.com)에서 Intune에 대한 새로운 도움말 및 지원 환경을 롤아웃하고 있습니다. 새 환경을 사용하면 문제를 사용자 고유의 언어로 설명하고, 문제 해결 인사이트와 웹 기반 수정 콘텐츠를 받을 수 있습니다. 이러한 솔루션은 사용자 문의에 따라 구동되는 규칙 기반 기계 학습 알고리즘을 통해 제공됩니다.  

문제별 지침 외에도 새 사례 만들기 워크플로를 사용하여 이메일 또는 전화를 통해 지원 사례를 열 수도 있습니다.  

롤아웃에 참여하는 고객의 경우 이 새로운 환경은 도움말 및 지원을 열 때 제공되는 콘솔의 영역에 따라 미리 선택된 옵션의 정적 집합에 대한 현재 도움말 및 지원 환경을 대체합니다.  

*이 새로운 도움말 및 지원 환경은 일부 테넌트에만 롤아웃되며 디바이스 관리 포털에서 사용할 수 있습니다. 이 새로운 환경에 대한 참가자는 사용 가능한 Intune 테넌트 중에서 임의로 선택됩니다. 롤아웃이 확장됨에 따라 새 테넌트가 추가됩니다.*  

자세한 내용은 Microsoft Intune에 대한 지원을 받는 방법의 [도움말 및 지원 환경](get-support.md#help-and-support-experience)을 참조하세요.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Intune용 PowerShell 모듈 - 미리 보기 사용 가능 <!-- 951068 -->
Microsoft Graph를 통해 Intune API를 지원하는 새로운 PowerShell 모듈을 이제 [GitHub]( https://aka.ms/intunepowershell)에서 미리 볼 수 있습니다. 이 모듈을 사용하는 방법에 대한 자세한 내용은 해당 위치의 추가 정보를 참조하세요. 


## <a name="week-of-october-15-2018"></a>2018년 10월 15일이 있는 주

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>iOS 디바이스에서 지문 또는 얼굴 ID를 변경할 때 표시되는 PIN 프롬프트  <!-- 2637704  -->
이제 iOS 디바이스에서 생체 인식 내용을 변경한 후 PIN을 입력하라는 메시지가 사용자에게 표시됩니다. 여기에는 등록된 지문 또는 얼굴 ID의 변경이 포함됩니다. 프롬프트의 타이밍은 ‘다음 시간 이후에 액세스 요구 사항 다시 확인:’ 시간 제한의 구성 방법에 따라 다릅니다.  PIN이 설정되지 않은 경우에는 설정하라는 메시지가 사용자에게 표시됩니다. 
 
이 기능은 iOS에만 제공되고 iOS용 Intune 앱 SDK, 버전 9.0.1 이상을 통합하는 애플리케이션의 참여가 필요합니다. 대상 애플리케이션에 동작이 적용될 수 있도록 SDK의 통합이 필요합니다. 이 통합은 롤링 기반으로 특정 애플리케이션 팀에서 수행합니다. 참여하는 일부 앱에는 WXP, Outlook, Managed Browser 및 Yammer가 포함됩니다.


## <a name="week-of-october-1-2018"></a>2018년 10월 1일이 있는 주

### <a name="app-management"></a>앱 관리

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>회사 포털 앱을 사용하여 키 프로필 속성에 액세스 <!-- 772203 -->
최종 사용자는 이제 회사 포털 앱에서 암호 재설정과 같은 주요 계정 속성 및 동작에 액세스할 수 있습니다. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS의 APP 설정으로 차단할 수 있는 타사 키보드 <!-- 1248481 -->
iOS 디바이스에서 Intune 관리자는 정책으로 보호된 앱에서 조직 데이터에 액세스할 때 타사 키보드 사용을 차단할 수 있습니다. 타사 키보드를 차단하도록 APP(애플리케이션 보호 정책)를 설정하면, 타사 키보드를 사용하여 처음으로 회사 데이터와 상호 작용할 때 장치 사용자가 메시지를 받습니다. 기본 키보드 이외의 모든 옵션이 차단되고 디바이스 사용자에게 표시되지 않습니다. 대화 메시지가 디바이스 사용자에게 한 번만 표시됩니다. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>관리되는 Android 및 iOS 디바이스에서 Intune 앱의 사용자 계정 액세스 <!-- 1248496 -->
Microsoft Intune 관리자는 관리되는 장치에서 Microsoft Office 애플리케이션에 추가할 사용자 계정을 제어할 수 있습니다. 허용되는 조직 사용자 계정만 액세스하도록 제한하고 등록된 디바이스에서 개인 계정을 차단할 수 있습니다. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Outlook iOS 및 Android 앱 구성 정책 <!--1828527 -->
이제 ActiveSync 프로토콜을 사용하여 기본 인증을 활용하는 온-프레미스 사용자의 iOS 및 Android에 대한 Outlook iOS 및 Android 앱 구성 정책을 만들 수 있습니다. 추가 구성 설정은 iOS 및 Android용 Outlook에 사용하도록 설정된 경우 추가됩니다.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 언어 팩 <!-- 1833450 -->
Intune 관리자는 Intune을 통해 관리되는 Office 365 Pro Plus 앱에 대한 추가 언어를 배포할 수 있습니다. 사용 가능한 언어 목록에는 언어 팩 **유형**(코어, 부분 및 언어 교정)이 포함되어 있습니다. Azure Portal에서 **Microsoft Intune** > **클라이언트 앱** > **앱** > **추가**를 차례로 선택합니다. **앱 추가** 블레이드의**앱 유형** 목록에 있는 **Office 365 제품군** 아래에서 **Windows 10**을 선택합니다. **앱 제품군 설정** 블레이드에서 **언어**를 선택합니다.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows LOB(기간 업무) 앱 파일 확장명<!-- 1884873 -->
이제 Windows LOB 앱에 대한 파일 확장명에는 *.msi*, *.appx*, *.appxbundle*, *.msix* 및 *.msixbundle*이 포함됩니다. Microsoft Intune에서 **클라이언트 앱** > **앱** > **추가**를 차례로 선택하여 앱을 추가할 수 있습니다. **앱 유형**을 선택할 수 있는 **앱 추가** 창이 표시됩니다. Windows LOB 앱의 경우 앱 유형으로 **기간 업무** 앱을 선택하고, **앱 패키지 파일**을 선택한 다음, 적절한 확장명이 있는 설치 파일을 입력합니다.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Intune을 사용하여 Windows 10 앱 배포 <!-- 2309001 -->
관리자는 LOB(사업 부문) 앱 및 비즈니스용 Microsoft Store 앱에 대한 기존 지원을 토대로, Intune을 사용하여 조직의 기존 애플리케이션 대부분을 Windows 10 장치의 최종 사용자에게 배포할 수 있습니다. 관리자는 MSIs, Setup.exe 또는 MSP와 같은 다양한 형식의 Windows 10 사용자에 대한 애플리케이션을 추가, 설치 및 제거할 수 있습니다. Intune는 다운로드 및 설치 전에 요구 사항 규칙을 평가하여 최종 사용자에게 Windows 10 알림 센터를 사용하여 상태 또는 재부팅 요구 사항을 알립니다. 이 기능은 이 워크로드를 Intune로 이동하는 데 관심이 있는 조직과 클라우드를 효과적으로 차단 해제합니다. 이 기능은 현재 공개 미리 보기에 있으며, 다음 몇 달 동안 이 기능에 새로운 기능이 상당히 추가될 것입니다. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>최종 사용자 디바이스 및 앱 콘텐츠 메뉴 <!-- 2771453 -->
이제 최종 사용자는 디바이스 및 앱의 컨텍스트 메뉴를 사용하여 디바이스 이름 바꾸기 또는 준수 검사와 같은 일반 작업 트리거할 수 있습니다. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows 회사 포털 바로 가기 키 <!-- 2771518 -->
최종 사용자는 바로 가기 키(액셀러레이터 키)를 사용하여 Windows 회사 포털에서 앱 및 디바이스 작업을 트리거할 수 있습니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Windows 10을 실행하는 디바이스의 VPN 구성 프로파일에서 DNS 접미사 생성<!-- 1333668 -->
VPN 디바이스 구성 프로필을 만들 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** 플랫폼 &gt; **VPN** 프로필 유형) DNS 설정을 몇 개 입력합니다. 이 업데이트를 사용하면 Intune에서 여러 **DNS 접미사**를 입력할 수도 있습니다. DNS 접미사를 사용하는 경우 FQDN(정규화된 도메인 이름) 대신 짧은 이름을 사용해 네트워크 리소스를 검색할 수 있습니다. 이 업데이트를 설치하면 Intune에서 DNS 접미사의 순서를 변경할 수도 있습니다.
[Windows 10 VPN 설정](vpn-settings-windows-10.md#dns-settings)에는 현재 DNS 설정이 나열됩니다.
적용 대상: Windows 10 디바이스

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Android 엔터프라이즈 작업 프로필의 상시 VPN에 대한 지원<!-- 1333705 -->
이 업데이트에서 Android 엔터프라이즈 디바이스에서는 관리되는 작업 프로필과 함께 상시 VPN 연결을 사용할 수 있습니다. 상시 VPN 연결은 계속 연결된 상태로 유지되거나 사용자가 디바이스를 잠금 해제한 경우, 디바이스가 다시 시작된 경우 또는 무선 네트워크가 변경된 경우 바로 다시 연결됩니다. 또한 VPN 연결이 활성화될 때까지 모든 네트워크 트래픽을 차단하는 “잠금” 모드로 연결 상태를 전환할 수도 있습니다.
**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) &gt; **디바이스 제한** > **연결** 설정에서 상시 VPN을 활성화할 수 있습니다.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>사용자가 지정되지 않은 디바이스에 SCEP 인증서 발급 <!-- 1744554 -->
현재, 인증서가 사용자에게 발급되었습니다. 이 업데이트를 사용하면 키오스크 등과 같이 사용자가 지정되지 않은 디바이스를 포함한 디바이스에 SCEP 인증서를 발급할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** >  플랫폼용 **Windows 10 이상** &gt; 프로필용 **SCEP 인증서**). 기타 업데이트는 다음과 같습니다.
- SCEP 프로필의 **주체** 속성은 이제 사용자 지정 텍스트 상자로, 새로운 변수를 포함할 수 있습니다. 
- SCEP 프로필의 **SAN(주체 대체 이름)** 속성은 이제 테이블 형식으로 새로운 변수를 포함할 수 있습니다. 관리자는 이 테이블에서 특성을 추가하고 사용자 지정 텍스트 상자에 값을 입력할 수 있습니다. SAN은 다음 특성을 지원합니다. 
  - DNS
  - 전자 메일 주소
  - UPN

  사용자 정의 값 텍스트 상자에 정적 텍스트와 함께 새 변수를 추가할 수 있습니다. 예를 들어, DNS 특성을 `DNS = {{AzureADDeviceId}}.domain.com`으로 추가할 수 있습니다.

  > [!NOTE]
  > 중괄호, 세미콜론 및 파이프 기호 “{}; |”는 SAN의 정적 텍스트에서 작동하지 않습니다. `Subject` 또는 `Subject alternative name`에 대해 허용되도록 새 디바이스 인증서 변수 중 하나만 중괄호로 묶어야 합니다. 

새 디바이스 인증서 변수:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}`은 Windows 및 도메인에 가입된 디바이스에서만 작동합니다. 
>  -  디바이스 인증서의 주체 또는 SAN에서 디바이스 속성(예: IMEI, 일련 번호 및 정규화된 도메인 이름)을 지정하는 경우 이러한 속성은 해당 디바이스의 액세스 권한을 가진 사람이 스푸핑할 수 있습니다. 

SCEP 구성 프로필을 만들 때 [SCEP 인증서 프로필 만들기](certificates-scep-configure.md#create-a-scep-certificate-profile)는 현재 변수를 나열합니다. 

적용 대상: Windows 10 이상 및 iOS, Wi-Fi 지원

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>원격으로 비규격 디바이스 잠그기 <!-- 2064495 -->
비규격 디바이스인 경우 원격으로 디바이스를 잠그는 준수 정책의 작업을 생성할 수 있습니다. Intune &gt; **디바이스 준수**에서 새 정책을 생성하거나, 기존 정책 &gt; **속성**을 선택합니다. **비준수에 대한 작업** > **추가**를 선택하고 디바이스를 원격으로 잠그도록 선택합니다.
지원 됩니다. 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 이상 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Azure Portal에서 Windows 10 이상 키오스크 프로필 개선 사항 <!-- 2748224 -->
업데이트에는 Windows 10 Kiosk 디바이스 구성 프로필에 대한 다음 개선 사항이 포함되어 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Windows 10 이상** &gt; 프로필 유형의 **키오스크 미리 보기**). 
- 현재, 동일한 디바이스에서 여러 키오스크 프로필을 만들 수 있습니다. 이 업데이트를 설치하면 Intune에서는 디바이스당 키오스크 프로필을 하나만 지원합니다. 단일 디바이스에서 키오스크 프로필이 여러 개 필요한 경우 사용자 지정 URI를 사용할 수 있습니다.
- **다중 앱 키오스크** 프로필의 애플리케이션 그리드에서 **시작 메뉴 레이아웃**의 애플리케이션 타일 크기와 순서를 선택할 수 있습니다. 더 많은 부분을 사용자 지정하려는 경우 XML 파일을 계속해서 업로드할 수 있습니다.
- 키오스크 브라우저 설정은 **키오스크** 설정으로 이동합니다. 지금은 Azure Portal에 **키오스크 웹 브라우저** 설정의 고유 범주가 있습니다.
적용 대상: Windows 10 이상




### <a name="device-enrollment"></a>디바이스 등록

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>아직 Autopilot에는 등록하지 않았지만 등록된 Win 10 디바이스에 Autopilot 프로필 적용 <!-- 1558983 -->
아직 Autopilot에 등록되지 않은 등록한 Win 10 디바이스에 Autopilot 프로필을 적용할 수 있습니다. Autopilot 프로필에서 **모든 대상 디바이스를 Autopilot으로 변환** 옵션을 선택하면 Autopilot 배포 서비스에 Autopilot 디바이스 이외 디바이스를 자동으로 등록합니다. 등록을 처리하는 데 48시가 가량 걸립니다. 디바이스 등록을 취소하고 재설정하면 Autopilot이 해당 디바이스를 프로비전합니다.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>등록 상태 페이지 프로필을 여러 개 만들어 Azure AD 그룹에 할당 <!-- 2526564 -->
이제 등록 상태 페이지 프로필을 여러 개 [만들어 Azure AD 그룹에 할당](windows-enrollment-status.md)할 수 있습니다.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Intune의 장비 등록 프로그램에서 Apple Business Manager로 마이그레이션 <!--2748613-->
ABM(Apple Business Manager)은 Intune에서 작동하므로, 사용 중인 계정을 DEP(장비 등록 프로그램)에서 ABM으로 업그레이드할 수 있습니다. Intune의 프로세스는 동일합니다. DEP에서 ABM으로 Apple 계정을 업그레이드하려면 [ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817)로 이동하세요.

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>디바이스 등록 개요 페이지 <!--2748656-->의 경고 및 등록 상태 탭
이제 디바이스 등록 개요 페이지의 별도 탭에 경고 및 등록 오류가 표시됩니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Android 디바이스에서 앱 제한 및 회사 리소스에 대한 액세스 차단 <!-- 2451462  -->  
**디바이스 준수** > **정책** > **정책 만들기** > **Android** > **시스템 보안**에서 *디바이스 보안* 섹션에 **제한된 앱**이라고 하는 새로운 설정이 있습니다. **제한된 앱** 설정은 특정 앱이 디바이스에 설치되어 있는 경우 준수 정책을 사용하여 회사 리소스에 대한 액세스를 차단합니다. 제한된 응용 프로그램이 디바이스에서 제거될 때까지 디바이스는 정책을 준수하지 않는 것으로 간주됩니다.
적용 대상: 
- Android




## <a name="week-of-september-24-2018"></a>2018년 9월 24일이 있는 주

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Microsoft 365 디바이스 관리 센터 <!-- 3078424 -->
Microsoft 365의 약속 중 하나는 단순화된 관리이며, 백엔드 Microsoft 365 서비스를 통합하여 Intune 및 Azure AD 조건부 액세스와 같은 통합형 시나리오를 제공하는 것입니다. 새 [Microsoft 365 관리 센터](http://devicemanagement.microsoft.com)는 관리 환경을 통합, 단순화 및 통합하는 작업 공간입니다. 디바이스 관리 팀의 전문가 작업 공간에서는 조직에 필요한 모든 디바이스 및 앱 관리 정보와 작업에 쉽게 액세스할 수 있습니다. 이 작업 공간은 엔터프라이즈 최종 사용자 컴퓨팅 팀의 기본 클라우드 작업 공간이 될 것으로 예상합니다.

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>타사 CA(인증 기관)에 대한 지원 <!-- 3093107 -->
이제 SCEP(단순 인증서 등록 프로토콜)를 사용하면 Windows, iOS, Android 및 macOS를 사용하는 모바일 디바이스에서 새로운 인증서를 발급하고 기존 인증서를 갱신할 수 있습니다.

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune에서 iOS 10 이상 지원 <!-- 2454656 -->  
이제 Intune 등록, 회사 포털 및 관리되는 브라우저에서 iOS 10 이상을 실행하는 iOS 디바이스만 지원합니다. 조직에 영향을 주는 디바이스 또는 사용자를 확인하려면 Azure Portal &gt; **디바이스** > **모든 디바이스**에서 Intune으로 이동합니다. OS별로 필터링한 다음, **열**을 클릭하여 OS 버전 세부 사항을 표시합니다. 이러한 사용자에게 지원되는 OS 버전으로 디바이스를 업그레이드하도록 요청합니다.  

아래에 나열된 모든 디바이스가 있거나 아래에 나열된 모든 디바이스를 등록하려는 경우 이러한 디바이스가 iOS 9 이하만 지원한다는 것을 잊지 마세요.  Intune 회사 포털에 액세스를 계속하려면 이러한 디바이스를 iOS 10 이상을 지원하는 디바이스로 업그레이드해야 합니다.  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad(3세대) 
* iPad 미니(1세대)  

## <a name="week-of-september-17-2018"></a>2018년 9월 17일이 있는 주

### <a name="app-management"></a>앱 관리

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>앱 보호 상태 타일의 중복 제거 <!-- 3083391 -->
**iOS 사용자 상태** 및 **Android 사용자 상태** 타일은 **클라이언트 앱 - 개요** 페이지와 **클라이언트 앱 - 앱 보호 상태** 페이지에 모두 있습니다. 상태 타일은 복제되지 않도록 **클라이언트 앱 - 개요** 페이지에서 제거되었습니다. 

## <a name="week-of-august-27-2018"></a>2018년 8월 27일 주

### <a name="app-management"></a>앱 관리

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>사용자 지정 및 Pulse Secure 연결 형식에 대한 iOS 앱당 VPN 프로필의 패킷 터널 지원 <!-- 1520957 -->
iOS 앱당 VPN 프로필을 사용할 때 앱 계층 터널링(app-proxy) 또는 패킷 수준 터널링(packet-tunnel)을 사용하도록 선택할 수 있습니다. 이러한 옵션을 사용할 수 있는 연결 형식은 다음과 같습니다.
- 사용자 지정 VPN
- Pulse Secure. 사용할 값을 모르는 경우 VPN 공급자의 설명서를 참조하세요.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>디바이스에 표시될 때의 iOS 소프트웨어 업데이트 지연 <!-- 1949583 -->
Intune &gt; **소프트웨어 업데이트** > **iOS용 정책 업데이트**에서 디바이스에 업데이트를 설치하지 않으려는 일 수와 시간을 구성할 수 있습니다. 향후 업데이트에서는 소프트웨어 업데이트가 디바이스에 표시될 때 해당 업데이트를 1-90일 동안 지연시킬 수 있습니다. 
[Microsoft Intune에서 iOS 업데이트 정책 구성](software-updates-ios.md)에는 현재 설정이 나열되어 있습니다.

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 ProPlus 버전 <!-- 2213968 -->
Intune을 사용하여 Office 365 ProPlus 앱을 Windows 10 디바이스에 할당하는 경우 Office 버전을 선택할 수 있습니다. Azure Portal에서 **Microsoft Intune** > **앱** > **앱 추가**를 차례로 선택합니다. 그런 다음, **형식** 드롭다운 목록에서 **Office 365 ProPlus 제품군(Windows 10)** 을 선택합니다. 연결된 블레이드를 표시하려면 **앱 제품군 설정**을 선택합니다. **업데이트 채널**을 **매월**과 같은 값으로 설정합니다. 필요에 따라 **예**를 선택하여 최종 사용자 디바이스에서 다른 버전의 Office(msi)를 제거합니다. 최종 사용자 디바이스에서 선택한 채널에 대한 특정 버전의 Office를 설치하려면 **특정**을 선택합니다. 여기서는 사용할 Office의 **특정 버전**을 선택할 수 있습니다. 사용 가능한 버전은 시간이 지남에 따라 변경됩니다. 따라서 새 배포를 만들 때 사용 가능한 버전이 최신 버전일 수 있으며 이전 버전이 제공되지 않을 수 있습니다. 현재 배포에서는 이전 버전을 계속 배포하지만, 버전 목록은 채널별로 지속적으로 업데이트됩니다. 자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요.

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Windows 10 VPN에 대한 DNS 등록 설정 지원 <!-- 2282852 -->
이 업데이트를 사용하여 사용자 지정 프로필을 사용하지 않고도 VPN 인터페이스에 할당된 IP 주소를 내부 DNS와 동적으로 등록하도록 Windows 10 VPN 프로필을 구성할 수 있습니다.
현재 사용 가능한 VPN 프로필 설정에 대한 자세한 내용은 [Windows 10 VPN 설정](vpn-settings-windows-10.md)을 참조하세요. 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>이제 macOS 회사 포털 설치 관리자는 설치 관리자 파일 이름에 버전 번호를 포함함 <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>iOS 자동 앱 업데이트 <!-- 2729759 -->
자동 앱 업데이트는 iOS 버전 11.0 이상의 디바이스 및 사용자에게 사용이 허가된 앱 모두에서 작동합니다.




### <a name="device-configuration"></a>디바이스 구성

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello는 사용자 및 디바이스를 대상으로 함 <!-- 1106609 -->
[비즈니스용 Windows Hello](windows-hello.md) 정책을 만들면 조직 내의 모든 사용자(테넌트 수준)에게 적용됩니다. 이 업데이트를 사용하면 디바이스 구성 정책을 사용하여 특정 사용자 또는 특정 디바이스에 정책을 적용할 수도 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **ID 보호** > **비즈니스용 Windows Hello**).
Windows Hello 구성 및 설정은 이제 Azure Portal의 Intune에서 **디바이스 등록** 및 **디바이스 구성**에 모두 존재합니다. **디바이스 등록**은 전체 조직(테넌트 수준)을 대상으로 하며 Windows AutoPilot(OOBE)을 지원합니다. **디바이스 구성**은 체크 인 중에 적용되는 정책을 사용하는 디바이스와 사용자를 대상으로 합니다.
이 기능은 다음에 적용됩니다.  
- Windows 10 이상
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler는 iOS의 VPN 프로필에 사용할 수 있는 연결임 <!-- 1769858 -->
iOS VPN 디바이스 구성 프로필을 만드는 경우(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 플랫폼 &gt; **VPN** 프로필 유형), Cisco, Citrix 등과 같은 몇 가지 연결 형식이 있습니다. 이 업데이트는 연결 형식으로 Zscaler를 추가합니다. 
[iOS를 실행하는 디바이스에 대한 VPN 설정](vpn-settings-ios.md)에는 사용 가능한 연결 형식이 나열되어 있습니다.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>Windows 10용 엔터프라이즈 Wi-Fi 프로필에 대한 FIPS 모드 <!-- 1879077 -->
이제 Intune Azure Portal에서 Windows 10용 엔터프라이즈 Wi-Fi 프로필에 대해 FIPS(Federal Information Processing Standards) 모드를 사용할 수 있습니다. Wi-Fi 프로필에서 사용하는 경우 Wi-Fi 인프라에서 FIPS 모드가 활성화되어 있어야 합니다.
[Intune에서 Windows 10 이상 디바이스에 대한 Wi-Fi 설정](wi-fi-settings-windows.md)은 Wi-Fi 프로필을 만드는 방법을 보여줍니다.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Windows 10 이상의 디바이스에서 S 모드 제어 - 공개 미리 보기 <!-- 1958649 -->
이 기능 업데이트를 사용하여 Windows 10 디바이스를 S 모드에서 전환하거나 사용자가 S 모드에서 디바이스를 전환하지 못하게 하는 디바이스 구성 프로필을 만들 수 있습니다. 이 기능은 Intune &gt; **디바이스 구성** > **프로필** >  **Windows 10 이상** > **버전 업그레이드 및 모드 전환**에 있습니다.
[Windows 10 S 모드 소개](https://www.microsoft.com/windows/s-mode)에서 S 모드에 대한 자세한 정보를 제공합니다.
적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>구성 프로필에 자동으로 추가된 Windows Defender ATP 구성 패키지 <!-- 2144658 -->
Intune에서 [고급 위협 보호 및 온보딩](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) 디바이스를 사용하는 경우 이전에 구성 패키지를 다운로드하고, 구성 프로필에 추가해야 했습니다. 이 업데이트를 사용하여 Intune은 Windows Defender Security Center에서 패키지를 자동으로 가져오고, 프로필에 추가합니다.
Windows 10 이상에 적용됩니다.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>사용자는 디바이스 설정 중에 연결해야 함 <!--2311457-->
이제 Windows 10을 설치하는 동안 네트워크 페이지를 지나 계속 진행하기 전에 네트워크에 디바이스를 연결하도록 요구하는 디바이스 프로필을 설정할 수 있습니다. 이 기능이 미리 보기 상태인 동안 이 설정을 사용하려면 Windows Insider build 1809 이상이 필요합니다.
적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>앱을 제한하고, iOS 및 Android Enterprise 디바이스의 회사 리소스에 대한 액세스를 차단함 <!-- 2451462 -->
**장치 준수** > **정책** > **정책 만들기** > **iOS** > **시스템 보안**에는 새로운 **제한된 애플리케이션** 설정이 있습니다. 특정 응용 프로그램이 디바이스에 설치되어 있는 경우 이 새로운 설정은 준수 정책을 사용하여 회사 리소스에 대한 액세스를 차단합니다. 제한된 응용 프로그램이 디바이스에서 제거될 때까지 디바이스는 정책을 준수하지 않는 것으로 간주됩니다.
적용 대상: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>iOS에 대한 최신 VPN 지원 업데이트 <!-- 2459928, 1819876, and 2650856 -->
이 업데이트는 다음 iOS VPN 클라이언트 지원을 추가합니다. 
- F5 Access(버전 3.0.1 이상)
- Citrix SSO
- Palo Alto Networks GlobalProtect 버전 5.0 이상 또한 이 업데이트에서는 다음과 같이 적용됩니다.
- 기존 **F5 Access** 연결 형식의 이름은 iOS에 대해 **F5 Access Legacy**로 변경됩니다.
- 기존 **Palo Alto Networks GlobalProtect** 연결 형식의 이름이 iOS에 대해 **Palo Alto Networks GlobalProtect(레거시)** 로 변경됩니다.
이러한 연결 형식의 기존 프로필은 해당 레거시 VPN 클라이언트에서 계속 사용됩니다. iOS에서 Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN 또는 Palo Alto Networks GlobalProtect 버전 4.1 이전을 사용하는 경우 새 앱으로 전환해야 합니다. iOS 디바이스에서 iOS 12로 업데이트하는 대로 가능한 한 빨리 이 작업을 수행하여 VPN 액세스를 사용할 수 있도록 합니다.
iOS 12 및 VPN 프로필에 대한 자세한 내용은 [Microsoft Intune 지원 팀 블로그](https://go.microsoft.com/fwlink/?linkid=2013806)를 참조하세요.

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Intune Azure Portal에서 이러한 정책을 다시 만들도록 Azure 클래식 포털 준수 정책 내보내기 <!-- 2469637 -->
Azure 클래식 포털에서 만든 준수 정책은 더 이상 사용되지 않습니다. 기존 준수 정책을 검토하고 삭제할 수 있지만 업데이트할 수는 없습니다. 준수 정책을 현재 Intune Azure Portal로 마이그레이션하려는 경우 쉼표로 구분된 파일로 정책을 내보낼 수 있습니다(*.csv* 파일). 그런 다음, 파일의 세부 정보를 사용하여 Intune Azure Portal에서 이러한 정책을 다시 만듭니다.

> [!IMPORTANT]
> Azure 클래식 포털에서 사용 중지하는 경우 더 이상 준수 정책에 액세스하거나 볼 수 없습니다. 따라서 Azure 클래식 포털이 사용 중지되기 전에 Azure Portal에서 정책을 내보내고 다시 만들어야 합니다.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile - 새 Mobile Threat Defense 파트너 <!-- 22662717 -->
Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Better Mobile에서 수행된 위험 평가에 따라 조건부 액세스를 사용하여 모바일 디바이스에서 회사 리소스에 대한 액세스를 제어할 수 있습니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>사용자가 로그인할 때까지 회사 포털을 단일 앱 모드로 잠금 <!--1067692 --> 
DEP 등록 중에 설정 도우미 대신 회사 포털을 통해 사용자를 인증하는 경우 이제 회사 포털을 단일 앱 모드에서 실행할 수 있습니다. 이 옵션을 사용하면 설정 도우미가 완료되는 즉시 디바이스를 잠그므로 사용자가 디바이스에 액세스하려면 로그인해야 합니다. 이 프로세스는 디바이스가 온보딩을 완료하고 사용자가 연결되지 않은 상태에서 분리되지 않도록 합니다.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Autopilot 디바이스에 사용자 및 식별 이름 할당 <!--1346521 -->
이제 [단일 Autopilot 디바이스에 사용자를 할당](enrollment-autopilot.md)할 수 있습니다. 또한 관리자는 AutoPilot을 사용하여 디바이스를 설정할 때 사용자에게 친숙한 식별 이름도 지정할 수 있습니다.
적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>VPP 디바이스 라이선스를 사용하여 DEP 등록 중 회사 포털 사전 프로비전 <!-- 1608345 -->
이제 VPP(대량 구매 프로그램) 디바이스 라이선스를 사용하여 DEP(장비 등록 프로그램) 등록 중 회사 포털을 사전 프로비전할 수 있습니다. 이렇게 하려면 [등록 프로필을 만들거나 편집](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)할 때 회사 포털을 설치하는 데 사용하려는 VPP 토큰을 지정합니다. 토큰이 만료되지 않았고 회사 포털 앱에 대한 충분한 라이선스가 있는지 확인합니다. 토큰이 만료되거나 라이선스가 부족한 경우 Intune은 App Store 회사 포털을 대신 푸시합니다(Apple ID에 대한 메시지를 표시함).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>회사 포털 사전 프로비전에 사용되는 VPP 토큰을 삭제하는 데 필요한 확인 <!-- 2237634 -->
DEP 등록 중 회사 포털을 사전 프로비전하는 데 VPP(대량 구매 프로그램) 토큰이 사용되는 경우 이를 삭제하는 데 이제는 확인이 필요합니다.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Windows 개인 디바이스 등록 차단 <!-- 1849498 -->
Intune에서 [모바일 디바이스 관리](windows-enroll.md)를 사용하여 [Windows 개인 디바이스를 등록하지 못하도록 차단](enrollment-restrictions-set.md#set-device-type-restrictions)할 수 있습니다. [Intune PC 에이전트](manage-windows-pcs-with-microsoft-intune.md)를 통해 등록된 디바이스는 이 기능을 사용하여 차단할 수 없습니다. 이 기능은 향후 2주 이내에 출시 예정이기 때문에 당장은 사용자 인터페이스에서 보이지 않을 수 있습니다.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Autopilot 프로필에 머신 이름 패턴 지정 <!--1849855-->
Autopilot 등록 중에 [컴퓨터 이름 템플릿을 지정](enrollment-autopilot.md#create-an-autopilot-deployment-profile)하여 [컴퓨터 이름](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)을 생성하고 설정할 수 있습니다. 적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Windows Autopilot 프로필의 경우 회사 로그인 페이지 및 도메인 오류 페이지에서 계정 변경 옵션을 숨김 <!--1901669 -->
관리자가 회사 로그인 및 도메인 오류 페이지에서 계정 변경 옵션을 숨기는 [새 Windows Autopilot 프로필 옵션](enrollment-autopilot.md#create-an-autopilot-deployment-profile)이 포함됩니다. 이러한 옵션을 숨기려면 Azure Active Directory에서 회사 브랜딩을 구성해야 합니다. 적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)



### <a name="device-management"></a>디바이스 관리

#### <a name="delete-jamf-devices----2653306--"></a>Jamf 디바이스 삭제 <!-- 2653306-->
**디바이스** &gt; Jamf 디바이스 선택 &gt; **삭제**로 이동하여 JAMF 관리 디바이스를 삭제할 수 있습니다.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>“사용 중지” 및 “초기화” 용어 변경 <!-- 2175759 -->
Graph API와 일관성을 유지하도록 Intune 사용자 인터페이스 및 설명서에서 다음 용어가 변경됩니다.
- **회사 데이터 제거**가 "사용 중지"로 변경됩니다.
- **출하 시 설정으로 초기화**가 **초기화**로 변경됩니다.

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>관리자가 MDM Push 인증서를 삭제하려고 하는 경우 확인 대화 상자 <!-- 297909500-->
누군가 Apple MDM Push Certificate를 삭제하려고 하면 확인 대화 상자에 관련된 iOS 및 macOS 디바이스의 번호가 표시됩니다. 인증서가 삭제되는 경우 이러한 디바이스를 다시 등록해야 합니다.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows 설치 관리자에 대한 보안 설정 추가 <!-- 2282430 -->
사용자가 앱 설치를 제어하도록 허용할 수 있습니다. 사용하도록 설정한 경우 그렇지 않으면 보안 위반으로 인해 중지될 수 있는 설치를 계속 진행하도록 허용합니다. 시스템에 모든 프로그램을 설치할 경우 Windows 설치 관리자가 상승된 권한을 사용하도록 명령할 수 있습니다. 또한 인덱싱될 WIP(Windows Information Protection) 항목 및 암호화되지 않은 위치에 저장된 WIP 항목에 대한 메타데이터를 사용할 수 있습니다. 정책을 사용하지 않을 때 WIP로 보호되는 항목은 인덱싱되지 않고 Cortana 또는 파일 탐색기의 결과에도 표시되지 않습니다. 이러한 옵션에 대한 기능은 기본적으로 사용할 수 없게 설정되어 있습니다. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>회사 포털 웹 사이트의 새로운 사용자 환경 업데이트<!--2000968 -->
고객으로부터의 피드백에 기반한 새 기능을 회사 포털 웹 사이트에 추가했습니다. 디바이스의 기존 기능과 유용성이 크게 향상됩니다. 사이트 영역&ndash;예: 디바이스 세부 정보, 피드백, 지원 및 디바이스 개요&ndash;은 응답성이 높은 최신의 새로운 디자인을 제공합니다. 또한 다음을 확인할 수 있습니다.

- 모든 디바이스 플랫폼에서 간소화된 워크플로
- 향상된 디바이스 식별 및 등록 흐름
- 더 유용한 오류 메시지
- 전문 기술 용어는 줄이고 친근한 언어 사용
- 앱에 대한 직접 링크를 공유하는 기능
- 대규모 앱 카탈로그의 성능 개선
- 향상된 모든 사용자에 대한 접근성  

[Intune 회사 포털 웹 사이트 설명서](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website)는 이러한 변경 내용을 반영하도록 업데이트되었습니다. 향상된 앱의 예제를 보려면 [Intune 최종 사용자 앱 UI 업데이트](whats-new-app-ui.md)를 참조하세요.  

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>준수 보고에서 향상된 탈옥 검색<!-- 2198738 -->
향상된 탈옥 검색 상태는 이제 관리 콘솔의 모든 준수 보고에 나타납니다.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="scope-tags-for-policies---1081974---"></a>정책에 대한 범위 태그 <!--1081974 -->
[범위 태그를 만들어](scope-tags.md) Intune 리소스에 대한 액세스를 제한할 수 있습니다. 역할 할당에 범위 태그를 추가한 다음, 범위 태그를 구성 프로필에 추가합니다. 역할은 일치하는 범위 태그가 있거나 범위 태그가 없는 구성 프로필이 있는 리소스에만 액세스할 수 있습니다.

## <a name="week-of-august-14-2018"></a>2018년 8월 14일 주

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Apple 장비 등록 프로그램에 대한 macOS 지원 <!-- 747651 -->
이제 Intune은 macOS 디바이스를 Apple DEP(장비 등록 프로그램)에 등록할 수 있도록 지원합니다. 자세한 내용은 [Apple 장비 등록 프로그램을 통해 자동으로 macOS 디바이스 등록](device-enrollment-program-enroll-macos.md)을 참조하세요.

## <a name="week-of-july-23-2018"></a>2018년 7월 23일 주

### <a name="app-management"></a>앱 관리

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>macOS에 대한 LOB(기간 업무) 앱 지원 <!-- 1895847 -->
Microsoft Intune은 macOS LOB 앱을 **요청** 또는 **등록 시 사용 가능**으로 배포하게 허용합니다. 최종 사용자는 macOS용 회사 포털 또는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)를 사용하여 **사용 가능**으로 앱을 배포할 수 있습니다.

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>키오스크 모드 <!-- 2051098 -->에 대한 기본 제공 iOS 앱 지원
스토어 앱 및 관리되는 앱 외에도 iOS 디바이스에서 키오스크 모드로 실행되는 기본 제공 앱(예: Safari)을 이제 선택할 수 있습니다.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus 앱 배포 편집 <!-- 2150145 -->
Microsoft Intune 관리자가 Office 365 Pro Plus 앱 배포를 편집할 수 있는 기능이 향상되었습니다. 또한 제품군의 속성을 변경하기 위해 더 이상 배포를 삭제할 필요가 없습니다. Azure Portal에서 **Microsoft Intune** > **클라이언트 앱** > **앱**을 차례로 선택합니다. 앱 목록에서 Office 365 Pro Plus 제품군을 선택합니다.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>업데이트된 Android용 Intune 앱 SDK 사용 가능 <!-- 2744271-->

Android P 릴리스를 지원하도록 Android용 Intune 앱 SDK의 업데이트된 버전이 제공됩니다. 앱 개발자이며 Android용 Intune SDK를 사용하는 경우 업데이트된 버전의 Intune 앱 SDK를 설치하여 Android 앱 내의 Intune 기능이 Android P 디바이스에서도 계속 예상대로 작동하는지 확인해야 합니다. 이 버전의 Intune 앱 SDK에는 SDK 업데이트를 수행하는 기본 제공 플러그인을 제공합니다. 통합된 모든 기존 코드를 다시 쓸 필요가 없습니다. 자세한 내용은 [Intune SDK for Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)(Android용 Intune SDK)를 참조하세요. Intune의 이전 배지 스타일을 사용하는 경우 서류 가방 아이콘을 사용하는 것이 좋습니다. 브랜딩 세부 정보는 [this GitHub repository](https://github.com/msintuneappsdk/intune-app-partner-badge)(이 GitHub 리포지토리)를 참조하세요.


### <a name="device-configuration"></a>디바이스 구성

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>macOS 디바이스에서 방화벽 설정을 사용하는 디바이스 준수 정책 만들기 <!-- 1497640 -->
새 macOS 준수 정책을 만들면(**디바이스 준수** > **정책** > **정책 만들기** > **플랫폼: macOS** > **시스템 보안**) 다음과 같은 일부 새 **방화벽** 설정을 사용할 수 있습니다. 

- **방화벽**: 사용자 환경에서 들어오는 연결을 처리하는 방법을 구성합니다.
- **들어오는 연결**: DHCP, Bonjour 및 IPSec과 같은 기본 인터넷 서비스에 필요한 연결을 제외한 모든 들어오는 연결을 **차단**합니다. 이 설정은 모든 공유 서비스도 차단합니다.
- **은폐 모드**: 디바이스에서 검색 요청에 응답하지 못하도록 은폐 모드를 **사용하도록 설정**합니다. 디바이스는 권한이 부여된 앱에 대해 들어오는 요청에 계속 응답합니다.

적용 대상: macOS 10.12 이상

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 이상용 새 Wi-Fi 디바이스 구성 프로필 <!-- 1879077 -->
현재 XML 파일을 사용하여 Wi-Fi 프로필 가져오고 내보낼 수 있습니다. 이 업데이트를 사용하면 일부 다른 플랫폼과 마찬가지로 Intune에서 직접 Wi-Fi 디바이스 구성 프로필을 만들 수 있습니다.

프로필을 만들려면 **디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **Wi-Fi**를 엽니다. 

Windows 10 이상에 적용됩니다.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>키오스크 - 사용되지 않음은 회색으로 처리되고, 변경할 수 없음 <!-- 2149998 -->
[키오스크 기능](device-restrictions-windows-10.md#kiosk-preview---obsolete)(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **디바이스 제한**)은 사용되지 않으며, [Windows 10 이상용 키오스크 설정](kiosk-settings.md)으로 대체됩니다. 이 업데이트를 사용하면 **Kiosk - 사용되지 않음** 기능은 회색으로 처리되고, 사용자 인터페이스를 변경하거나 업데이트할 수 없습니다. 

키오스크 모드를 활성화하려면 [Windows 10 이상용 키오스크 설정](kiosk-settings.md)을 참조하세요.

적용 대상: Windows 10 이상, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>타사 인증 기관을 사용하는 API <!-- 2184013 -->
이 업데이트에는 Intune 및 SCEP와 통합하도록 타사 인증 기관을 활성화하는 Java API가 있습니다. 그러면 사용자는 프로필에 SCEP 인증서를 추가하고, MDM을 사용하여 디바이스에 적용할 수 있습니다.

현재 Intune은 [Active Directory 인증서 서비스를 사용하여 SCEP 요청](certificates-scep-configure.md)을 지원합니다.

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>키오스크 브라우저에서 세션 종료 단추를 표시할지 여부를 설정/해제 <!-- 2455253 -->
이제 키오스크 브라우저에서 세션 종료 단추를 표시할지 여부를 구성할 수 있습니다. **디바이스 구성** > **키오스크(미리 보기)** > **키오스크 웹 브라우저**에서 컨트롤을 볼 수 있습니다. 설정된 경우 사용자가 단추를 클릭하면 앱은 세션을 종료할지 확인하는 메시지를 표시합니다. 확인한 경우 브라우저는 모든 검색 데이터를 지우고 기본 URL로 다시 이동합니다.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>eSIM 셀룰러 구성 프로필 만들기 <!-- 2564077 -->
**디바이스 구성**에서 eSIM 셀룰러 프로필을 만들 수 있습니다. 모바일 운영자가 제공하는 셀룰러 활성화 코드를 포함하는 파일을 가져올 수 있습니다. 그런 다음, 이러한 프로필을 Surface Pro LTE 및 eSIM 지원 디바이스와 같은 eSIM LTE가 활성화된 Windows 10 디바이스에 배포할 수 있습니다.

[디바이스에서 eSIM 프로필을 지원](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)하는지 확인합니다.

Windows 10 이상에 적용됩니다. 




### <a name="device-enrollment"></a>디바이스 등록

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>삼성 Knox 모바일 등록을 사용하여 등록된 Android 디바이스를 자동으로 "회사"로 표시합니다. <!-- 2404851 -->
기본적으로 삼성 Knox 모바일 등록을 사용하여 등록된 Android 디바이스는 이제 **디바이스 소유권** 아래에 **회사**로 표시됩니다. Knox 모바일 등록을 사용하여 등록하기 전에 IMEI 또는 일련 번호를 사용하여 회사 디바이스를 수동으로 식별할 필요가 없습니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>디바이스 블레이드의 대량 삭제 디바이스 <!-- 1793693 -->

이제 디바이스 블레이드에서 한 번에 여러 디바이스를 삭제할 수 있습니다. **디바이스** > **모든 디바이스** &gt; 삭제할 디바이스 &gt; **삭제**를 선택합니다. 삭제할 수 없는 디바이스의 경우 경고가 표시됩니다.

## <a name="week-of-july-16-2018"></a>2018년 7월 16일 주  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱에서 동기화할 수 있는 더 많은 기회  
이제 Windows용 회사 포털 앱을 사용하여 Windows 작업 표시줄 및 시작 메뉴에서 직접 동기화를 시작할 수 있습니다. 이 기능은 디바이스를 동기화하고 회사 리소스에 액세스하는 작업만 수행하는 경우에 특히 유용합니다. 새 기능에 액세스하려면 작업 표시줄 또는 시작 메뉴에 고정되어 있는 회사 포털 아이콘을 마우스 오른쪽 단추로 클릭합니다. 메뉴 옵션(점프 목록이라고도 함)에서 **이 디바이스 동기화**를 선택합니다. 회사 포털에 **설정** 페이지가 열리고 동기화가 시작됩니다. 새로운 기능에 대한 내용은 [UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱의 새 검색 환경  

이제 Windows용 회사 포털 앱에서 앱을 탐색하거나 검색하면 기존 **타일** 보기와 새로 추가된 **세부 정보** 보기 간에 전환할 수 있습니다. 새 보기에는 이름, 게시자, 게시 날짜 및 설치 상태와 같은 애플리케이션 세부 정보가 나열됩니다.  

**앱** 페이지의 **설치됨** 보기를 통해 완료 및 진행 중인 앱 설치에 대한 세부 정보를 볼 수 있습니다. 새 보기의 모양을 보려면 [UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>디바이스 등록 관리자를 위한 회사 포털 앱 환경 개선  
DEM(디바이스 등록 관리자)이 Windows용 회사 포털 앱에 로그인하면 이제 앱은 DEM의 현재 실행 중인 디바이스만 나열됩니다. 이러한 향상된 기능은 앱이 모든 DEM 등록 디바이스를 표시하려고 시도할 때 이전에 발생한 시간 초과를 줄입니다.  


## <a name="week-of-july-9-2018"></a>2018년 7월 9일 주

### <a name="app-management"></a>앱 관리

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>승인되지 않은 디바이스 공급업체 및 모델을 기준으로 앱 액세스 차단 <!-- 1425689 ! -->
Intune IT 관리자는 Intune 앱 보호 정책을 통해 지정된 Android 제조업체 및/또는 iOS 모델 목록을 적용할 수 있습니다. IT 관리자는 Android 정책용 제조업체 및 iOS 정책용 디바이스 모델의 세미콜론으로 구분된 목록을 제공할 수 있습니다. Intune 앱 보호 정책은 Android 및 iOS에만 적용됩니다. 이 지정된 목록에서 수행할 수 있는 두 가지 개별 작업은 다음과 같습니다.
- 지정되지 않은 디바이스에 대한 앱 액세스 차단
- 또는 지정되지 않은 디바이스에서 회사 데이터 선택적 초기화. 

정책을 통한 요구 사항이 충족되지 않으면 사용자가 대상 애플리케이션에 액세스할 수 없습니다. 설정에 따라 사용자는 차단되거나 앱 내의 해당 회사 데이터에서 선택적으로 초기화될 수 있습니다. iOS 장치에서 이 기능을 사용하려면 애플리케이션(예: WXP, Outlook, Managed Browser, Yammer)에 참여하여 대상 애플리케이션에 이 기능을 적용하기 위해 Intune APP SDK를 통합해야 합니다. 이 통합은 롤링 기반으로 특정 애플리케이션 팀에서 수행합니다. Android에서 이 기능을 사용하려면 최신 회사 포털이 필요합니다. 

최종 사용자 장치에서 Intune 클라이언트는 애플리케이션 보호 정책에 대한 Intune 블레이드에 지정된 문자열의 단순 일치를 기반으로 동작을 수행합니다. 이 동작은 전적으로 디바이스가 보고하는 값에 따라 결정됩니다. 따라서 IT 관리자는 의도한 동작이 정확한지 확인하는 것이 좋습니다. 이를 확인하려면 작은 사용자 그룹을 대상으로 하는 다양한 디바이스 제조업체 및 모델을 기반으로 이 설정을 테스트하면 됩니다. Microsoft Intune에서 **클라이언트 앱** > **앱 보호 정책**을 선택하여 앱 보호 정책을 보고 추가합니다. 앱 보호 정책에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md) 및 [Intune에서 앱 보호 정책 액세스 작업을 사용하여 선택적으로 데이터 초기화](app-protection-policies-access-actions.md)를 참조하세요.

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>macOS 회사 포털 시험판 빌드에 액세스 <!-- 1734766 -->
Microsoft 자동 업데이트를 사용하여 등록할 수 있으며 Insider 프로그램에 참여하여 빌드를 조기에 받을 수 있습니다. 등록하면 업데이트된 회사 포털을 사용해 본 이후에 최종 사용자에게 제공할 수 있습니다. 자세한 내용은 [Microsoft Intune 블로그](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/)를 참조하세요.

## <a name="week-of-july-2-2018"></a>2018년 7월 2일 주

### <a name="app-management"></a>앱 관리

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>디바이스별 iOS 앱 구성 상태 모니터링 <!-- 880037 -->
Microsoft Intune 관리자는 각 관리 디바이스에 대한 iOS 앱 구성 상태를 모니터링할 수 있습니다. Azure Portal의 **Microsoft Intune**에서 **디바이스** > **모든 디바이스**를 차례로 선택합니다. 관리 디바이스 목록에서 디바이스에 대한 블레이드를 표시할 특정 디바이스를 선택합니다. 디바이스 블레이드에서 **앱 구성**을 선택합니다.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>앱 보호 정책에 대한 액세스 작업 <!-- 1483510 -->
규정을 준수하지 않는 디바이스를 명시적으로 초기화, 차단 또는 경고하도록 앱 보호 정책을 구성할 수 있습니다. *초기화* 작업은 디바이스에서 회사의 회사 데이터를 제거합니다. 초기화가 수행되면 디바이스 사용자에게는 초기화 및 수정 단계의 이유가 포함된 알림이 제공됩니다. 최소 OS 버전과 같은 일부 설정의 경우 차단 및 초기화와 같은 여러 작업을 적용할 수 있습니다. 앱이 시작되면 이러한 작업이 트리거됩니다.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>선택적으로 조직의 앱 데이터 지우기 <!-- 1507030 -->
APP(애플리케이션 보호 정책) 액세스 설정 조건이 충족되지 않으면 관리자가 이제 조직의 데이터를 선택적으로 지우도록 구성할 수 있습니다.  이 기능을 사용하면 관리자가 미리 구성된 기준에 따라 애플리케이션에서 중요한 조직 데이터를 자동으로 보호하고 제거할 수 있습니다.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>VPP를 통해 구매한 iOS 앱 해지 <!-- 1777384 -->
Microsoft Intune 관리자는 VPP(대량 구매 프로그램)를 통해 구매한 iOS 앱에 대한 모든 라이선스를 선택적으로 해지할 수 있습니다. 사용자 라이선스된 앱이 더 이상 할당되지 않는 경우 사용자에게 알릴 수 있습니다. 앱 라이선스를 철회해도 디바이스에서 관련 VPP 앱이 제거되지 않습니다. VPP 앱을 제거하려면 할당 작업을 **제거**로 변경해야 합니다. 회수된 라이선스 수는 Intune의 **앱** 워크로드의 **사용이 허가된 앱** 노드에 반영됩니다. iOS VPP 앱과 관련된 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 프로그램을 통해 구매한 iOS 앱을 관리하는 방법](vpp-apps-ios.md)을 참조하세요.

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>회사 포털 앱의 규정을 준수하지 않는 메시지 업데이트 <!-- 1832222 -->
디바이스가 규정을 준수하지 않을 때 디바이스 사용자에게 표시되는 메시지를 수정했습니다. 메시지의 원래 의미는 그대로 유지되지만 더 친숙한 언어와 덜 전문적인 용어로 업데이트되었습니다. 또한 설명서 및 수정 단계에 대한 링크를 최신 상태로 유지하기 위해 새로 고쳤습니다.
다음에서 볼 수 있는 전후 텍스트는 메시징 향상 기능의 한 예입니다.
- **이전**: 이 디바이스는 IT 관리자가 요구한 특정 기간 내에 Intune 서비스에 연결되지 않았습니다.* 이 문제를 해결하려면 디바이스에서 회사 포털 앱을 열고 준수 확인 단추를 클릭합니다.*
- **이후**: 디바이스가 얼마 동안 조직에 체크 인되지 않았습니다.* 연결을 다시 설정하려면 디바이스에서 회사 포털 앱을 열고 디바이스의 설정 확인을 누릅니다.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>iOS VPP 앱 라이선스 해지 <!-- 1863797 -->
관리자는 사용자 또는 디바이스에 할당된 iOS VPP 앱 라이선스를 회수할 수 있습니다. iOS VPP 앱을 제거하면 앱 라이선스를 회수할 수도 있습니다. 앱을 제거하기 전에 먼저 사용자 또는 디바이스가 앱의 대상인 그룹에서 제거되어야 합니다. 사용자 또는 디바이스를 그룹에서 제거하면 앱의 재설치를 방지할 수 있습니다. 이러한 단계가 완료되면 해당 앱 라이선스를 다른 사용자 또는 디바이스에 할당하도록 선택할 수 있습니다. iOS VPP 앱 라이선스에 대한 자세한 내용은 [Microsoft Intune에서 iOS 볼륨을 구매한 앱 관리](vpp-apps-ios.md)를 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>회사 또는 학교 액세스 설정을 사용하여 디바이스 범주 선택 <!-- 1058963 eenotready --> 
[디바이스 그룹 매핑](https://docs.microsoft.com/intune/device-group-mapping)을 사용하도록 설정한 경우, Windows 10의 사용자에게 **설정** > **계정** > **회사 또는 학교 액세스**의 **연결** 단추를 통해 등록한 후 디바이스 범주를 선택하라는 메시지가 표시됩니다. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>sAMAccountName을 이메일 프로필에 대한 계정 사용자 이름으로 사용 <!-- 1500307 -->
온-프레미스 **sAMAccountName**을 Android, iOS 및 Windows 10용 이메일 프로필에 대한 계정 사용자 이름으로 사용할 수 있습니다. Azure AD(Azure Active Directory)의 `domain` 또는 `ntdomain` 특성에서 도메인을 가져올 수도 있습니다. 또는 사용자 지정 정적 도메인을 입력합니다.

이 기능을 사용하려면 온-프레미스 Active Directory 환경의 `sAMAccountName` 특성을 Azure AD에 동기화해야 합니다.

[Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 이상](email-settings-windows-10.md)에 적용

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>충돌에서 디바이스 구성 프로필 참조 <!-- 1556983 -->
**디바이스 구성**에 기존 프로필의 목록이 표시됩니다. 이 업데이트를 사용하면 충돌하는 프로필에 대한 세부 정보를 제공하는 새 열이 추가됩니다. 충돌하는 행을 선택하여 충돌이 있는 설정 및 프로필을 볼 수 있습니다. 

[구성 프로필 관리](device-profile-monitor.md#view-conflicts)에 대한 자세한 정보입니다.

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>디바이스 준수의 새로운 디바이스 상태 <!-- 2308882 -->
**디바이스 준수** > **정책** &gt; 정책 선택 &gt; **개요**에서 다음과 같은 새 상태가 추가됩니다.
- 성공
- 오류
- 충돌
- 보류 중
- 해당 없음. 다른 플랫폼의 디바이스 수를 보여 주는 이미지도 표시됩니다. 예를 들어 iOS 프로필을 보고 있는 경우 이 프로필에도 할당된 비iOS 디바이스의 수가 새 타일에 표시됩니다. [디바이스 준수 정책](compliance-policy-monitor.md#view-status-of-device-policies)을 참조합니다.

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>디바이스 준수에서 타사 바이러스 백신 솔루션 지원 <!-- 2325484 -->
디바이스 준수 정책(**디바이스 준수** > **정책** > **정책 만들기** > **플랫폼: Windows 10 이상** > **설정** > **시스템 보안**)을 만들면 다음과 같은 새 **[디바이스 보안](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)** 옵션이 제공됩니다. 
- **바이러스 백신**: **필수**로 설정하면 Symantec 및 Windows Defender와 같은 Windows Security Center에 등록된 바이러스 백신 솔루션을 사용하여 준수를 확인할 수 있습니다. 
- **스파이웨어 방지**: **필수**로 설정하면 Symantec 및 Windows Defender와 같은 Windows Security Center에 등록된 스파이웨어 방지 솔루션을 사용하여 준수를 확인할 수 있습니다. 

적용 대상: Windows 10 이상 

### <a name="device-enrollment"></a>디바이스 등록

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>등록 프로그램 토큰 목록에서 프로필이 없는 디바이스 열 <!-- 1853904 -->
프로필이 할당되지 않는 디바이스 수를 보여주는 새 열이 등록 프로그램 토큰 목록에 제공됩니다. 이렇게 하면 관리자는 프로필을 사용자에게 전달하기 전에 이러한 디바이스에 할당할 수 있습니다. 새 열을 보려면 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**으로 이동합니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work 및 Play for Work에 대한 Google 이름 변경 <!--842873 -->
Intune은 Google 브랜딩 변경 내용을 반영하도록 "Android for Work" 용어를 업데이트했습니다. "Android for Work" 및 "Play for Work" 용어는 더 이상 사용되지 않습니다. 컨텍스트에 따라 서로 다른 용어가 사용됩니다.
- "Android 엔터프라이즈"는 전반적인 최신 Android 관리 스택을 나타냅니다.
- "회사 프로필" 또는 "프로필 소유자"는 회사 프로필을 통해 관리되는 BYOD 디바이스를 가리킵니다.
- "관리되는 Google Play"는 Google 앱 스토어를 나타냅니다.

#### <a name="rules-for-removing-devices----1609459---"></a>디바이스 제거에 대한 규칙 <!-- 1609459 -->
설정한 일 수 동안 체크 인하지 않은 디바이스를 자동으로 제거할 수 있는 새 규칙이 제공됩니다. 새 규칙을 보려면 **Intune** 창으로 이동하여 **디바이스**를 선택하고 **디바이스 정리 규칙**을 선택합니다.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Android 디바이스에 대한 회사 소유의 일회용 지원 <!-- 1630973 -->

Intune은 이제 고도로 관리되고 잠겨 있는 키오스크 스타일의 Android 디바이스를 지원합니다. 관리자는 이를 통해 디바이스 사용을 하나의 앱 또는 작은 앱 집합에 추가로 잠그고 사용자가 다른 앱을 사용하거나 디바이스에서 다른 작업을 수행하지 못하도록 차단할 수 있습니다. Android 키오스크를 설정하려면 Intune &gt; **디바이스 등록** > **Android 등록** > **키오스크 및 작업 디바이스 등록**으로 이동합니다. 자세한 내용은 [Android 엔터프라이즈 키오스크 디바이스 등록 설정](android-kiosk-enroll.md)을 참조합니다.

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>중복된 회사 디바이스 식별자의 행 단위 검토 업로드 <!-- 2203794-->
회사 ID를 업로드할 때 Intune에서 모든 중복된 항목의 목록을 제공하고, 기존 정보를 대체하거나 유지할 수 있는 옵션을 제공합니다. **디바이스 등록** > **회사 디바이스 식별자** > **식별자 추가**를 차례로 선택한 후에 중복된 항목이 있으면 보고서가 표시됩니다. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>수동으로 회사 디바이스 식별자 추가 <!-- 2203803 -->
수동으로 회사 디바이스 ID를 추가할 수 있습니다. **디바이스 등록** > **회사 디바이스 식별자** > **추가**를 차례로 선택합니다. 

## <a name="week-of-june-25-2018"></a>2018년 6월 25일 주

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo - 새 Mobile Threat Defense 파트너 <!-- 1169249 -->

Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Pradeo에서 수행한 위험 평가에 따라 조건부 액세스를 사용하여 회사 리소스에 대한 모바일 디바이스의 액세스를 제어할 수 있습니다.

## <a name="week-of-june-18-2018"></a>2018년 6월 18일 주

### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Intune 앱 보호 정책용 Microsoft Edge 모바일 지원<!-- 1817882 -->

모바일 디바이스용 Microsoft Edge 브라우저는 이제 Intune에 정의된 앱 보호 정책을 지원합니다.

## <a name="week-of-june-11-2018"></a>2018년 6월 11일 주

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>NDES 인증서 커넥터에서 FIPS 모드 사용 <!-- 1333688 -->
FIPS(Federal Information Processing Standard) 모드를 사용하는 컴퓨터에 NDES 인증서 커넥터를 설치하면 인증서 발급 및 해지가 예상대로 작동하지 않았습니다. 이 업데이트에는 NDES 인증서 커넥터와 관련된 FIPS 지원이 포함되어 있습니다. 

이 업데이트에는 다음도 포함됩니다.

- NDES 인증서 커넥터에는 Windows Server 2016 및 Windows Server 2012 R2에 자동으로 포함되는 .NET 4.5 Framework가 필요합니다. 이전에는 .NET 3.5 Framework가 최소 필수 버전이었습니다.
- TLS 1.2 지원은 NDES 인증서 커넥터에 포함되어 있습니다. 따라서 NDES 인증서 커넥터가 설치된 서버가 TLS 1.2를 지원하는 경우 TLS 1.2가 사용됩니다. 서버가 TLS 1.2를 지원하지 않으면 TLS 1.1이 사용됩니다. 현재 TLS 1.1은 디바이스와 서버 간 인증에 사용됩니다.

자세한 내용은 [SCEP 인증서 구성 및 사용](certificates-scep-configure.md), [PKCS 인증서 구성 및 사용](certficates-pfx-configure.md)을 참조하세요.

## <a name="week-of-june-4-2018"></a>2018년 6월 4일 주

### <a name="app-management"></a>앱 관리

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>키오스크 모드에서 비즈니스용 Microsoft 스토어 앱에 대한 연결된 앱 사용자 모델 ID(AUMID) 검색 <!-- 1560077 ! -->
Intune에서는 이제 WSfB(비즈니스용 Microsoft 스토어) 앱에 대한 AUMID(응용 프로그램 사용자 모델 ID)를 검색하여 향상된 키오스크 프로필 구성을 제공할 수 있습니다.

비즈니스용 Microsoft 스토어에서 앱에 대한 자세한 내용은 [비즈니스용 Microsoft 스토어에서 앱 관리](windows-store-for-business.md)를 참조하세요.

#### <a name="new-company-portal-branding-page----1916370---"></a>새 회사 포털 브랜딩 페이지 <!-- 1916370 -->
회사 포털 브랜딩 페이지에는 새로운 레이아웃, 메시지 및 도구 설명이 있습니다.


### <a name="device-configuration"></a>디바이스 구성

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Palo Alto Networks GlobalProtect VPN 프로필 <!-- 1333680 ! --> 지원
이 업데이트에서는 Palo Alto Networks GlobalProtect를 Intune의 VPN 프로필에 대한 VPN 연결 형식으로 선택할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **프로필 형식** > **VPN**). 이 릴리스에서 지원되는 플랫폼은 다음과 같습니다. 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>로컬 디바이스 보안 옵션 설정에 대한 추가 <!-- 1403702 -->
Windows 10 디바이스에 대한 추가 로컬 디바이스 보안 옵션 설정을 구성할 수 있습니다. 추가 설정은 Microsoft 네트워크 클라이언트, Microsoft 네트워크 서버, 네트워크 액세스/보안 및 대화형 로그온 영역에서 사용할 수 있습니다. Windows 10 디바이스 구성 정책을 만들 때 Endpoint Protection 범주에서 이러한 설정을 찾아보세요.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Windows 10 디바이스에서 키오스크 모드 사용 <!-- 1560072 ! -->
Windows 10 디바이스에서 구성 프로필을 만들고 키오스크 모드를 사용하도록 설정할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10** > **디바이스 제한 사항** > **키오스크**). 이 업데이트에서 **키오스크(미리 보기)** 설정은 **키오스크(사용되지 않음)** 로 이름이 바뀝니다. **키오스크(사용되지 않음)** 는 더 이상 사용하지 않는 것이 좋지만 7월 업데이트까지 계속 작동합니다. **키오스크(사용되지 않음)** 는 새로운 **키오스크** 프로필 유형(**프로필 만들기** > **Windows 10** > **키오스크(미리 보기)**)으로 바뀌고 이 프로필 유형에는 Windows 10 RS4 이상에서 키오스크를 구성하는 설정이 포함됩니다.

Windows 10 이상에 적용됩니다.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>디바이스 프로필 그래픽 사용자 차트가 다시 표시됨 <!-- 2160133 -->
디바이스 프로필 그래픽 차트(**디바이스 구성** > **프로필** &gt; 기존 프로필 선택 &gt; **개요**)에 표시되는 개수를 개선하기 위해 그래픽 사용자 차트가 일시적으로 제거되었습니다.

이 업데이트를 사용하면 그래픽 사용자 차트가 Azure Portal에 다시 표시됩니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>사용자 인증이 없는 Windows Autopilot 등록 지원 <!-- 1165118 -->
Intune에서는 이제 사용자 인증 없이 Windows Autopilot 등록을 지원합니다. 여기에는 Windows Autopilot 배포 프로필인 "Autopilot 배포 모드"가 "자체 배포"로 설정된 새 옵션이 있습니다.  이 디바이스는 Windows 10 Insider Preview Build 17672 이상을 실행 중이고 TPM 2.0 칩을 가지고 있어야 이 등록 유형을 성공적으로 완료할 수 있습니다. 사용자 인증이 필요하지 않으므로 물리적으로 제어할 수 있는 디바이스에만 이 옵션을 할당해야 합니다.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Autopilot에 대한 OOBE를 구성할 경우, 새 언어 지역 설정 <!-- 1821766 -->
새 구성 설정은 독창적인 환경(Out of Box Experience)에서 Autopilot 프로필에 대한 언어와 지역을 설정하는 데 사용할 수 있습니다. 새 설정을 확인하려면 **디바이스 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기** > **배포 모드** = **자체 배포** > **기본값 구성됨**을 차례로 선택합니다.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>디바이스 키보드 구성에 대한 새 설정 <!-- 1821768 -->
새 설정을 통해 첫 실행 경험 중에 Autopilot 프로필에 대한 키보드를 구성할 수 있습니다. 새 설정을 확인하려면 **디바이스 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기** > **배포 모드** = **자체 배포** > **기본값 구성됨**을 차례로 선택합니다.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Autopilot 프로필을 대상 지정 그룹으로 이동 <!-- 1877935 -->
AutoPilot 배포 프로필을 AutoPilot 디바이스를 포함하는 Azure AD 그룹에 할당할 수 있습니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="set-compliance-by-device-location----851881----"></a>디바이스 위치별 준수 설정 <!-- 851881 ! -->
상황에 따라 회사 리소스에 대한 액세스를 네트워크 연결로 정의된 특정 위치로 제한할 수 있습니다. 이제 디바이스의 IP 주소를 기반으로 하여 준수 정책을 만들 수 있습니다(**디바이스 준수** > **위치**). IP 범위를 벗어난 디바이스는 회사 리소스에 액세스할 수 없습니다.

적용 대상: 업데이트된 회사 포털 앱이 있는 Android 디바이스 6.0 이상

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot 디바이스에서 소비자 앱과 경험을 방지<!-- 1621980 -->
Windows 10 Enterprise RS4 AutoPilot 디바이스에서 소비자 앱 및 환경을 설치하지 못하도록 방지할 수 있습니다. 이 기능을 확인하려면 **Intune** > **장치 구성** > **프로필** > **프로필 만들기** > **플랫폼** = **Windows 10 이상** > **프로필 유형** = **장치 제한** > **구성** > **Windows 추천** > **소비자 기능**으로 차례로 이동합니다. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Windows 10 소프트웨어 업데이트에서 최신 버전 제거 <!-- 1732948 -->
Windows 10 컴퓨터에서 주요 문제가 발견되면 최신 기능 업데이트 또는 최신 품질 업데이트를 제거(롤백)하도록 선택할 수 있습니다. 기능 또는 품질 업데이트의 제거는 디바이스가 켜져 있는 서비스 채널에서만 사용할 수 있습니다. 제거하면 Windows 10 컴퓨터에서 이전 업데이트를 복원하는 정책이 트리거됩니다. 특히 기능 업데이트의 경우 최신 버전 제거를 적용할 수 있는 시간을 2-60일로 제한할 수 있습니다. 소프트웨어 업데이트 제거 옵션을 설정하려면 Azure Portal의 **Microsoft Intune** 블레이드에서 **소프트웨어 업데이트**를 선택합니다. 그런 다음, **소프트웨어 업데이트** 블레이드에서 **Windows 10 업데이트 링**을 선택합니다. 그런 다음, **개요** 섹션에서 **제거** 옵션을 선택할 수 있습니다.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>모든 디바이스에서 IMEI 및 일련 번호 검색 <!-- 1793685 -->
이제 모든 디바이스 블레이드에서 IMEI 및 일련 번호를 검색할 수 있습니다(이메일, UPN, 디바이스 이름 및 관리 이름을 계속 사용할 수 있음). Intune에서 **디바이스** > **모든 디바이스**를 차례로 선택한 다음, 검색 상자에서 검색 항목을 입력합니다.

#### <a name="management-name-field-will-be-editable----1875989---"></a>관리 이름 필드를 편집할 수 있음 <!-- 1875989 -->
이제 디바이스의 **속성** 블레이드에서 관리 이름 필드를 편집할 수 있습니다. 이 필드를 편집하려면 **디바이스** > **모든 디바이스**를 선택하고, 디바이스를 선택한 다음, **속성**을 선택합니다. 관리 이름 필드를 사용하여 디바이스를 고유하게 식별할 수 있습니다.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>새로운 모든 디바이스 필터: 디바이스 범주 <!-- 1878520 -->
이제 디바이스 범주별로 **모든 디바이스** 목록을 필터링할 수 있습니다. 이렇게 하려면 **디바이스** > **모든 디바이스** > **필터** > **디바이스 범주**를 차례로 선택합니다.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>TeamViewer를 사용하여 iOS 및 MacOS 디바이스의 화면 공유 <!-- 1985547 -->
관리자는 이제 [TeamViewer](device-profile-android-teamviewer.md)에 연결하고 iOS 및 macOS 디바이스에서 화면 공유 세션을 시작할 수 있습니다. iPhone, iPad 및 macOS 사용자는 자신의 화면을 다른 데스크톱 또는 모바일 디바이스와 실시간으로 공유할 수 있습니다. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>여러 Exchange Connector 지원 <!-- 2070451 -->
더 이상 테넌트당 하나의 Microsoft Intune Exchange Connector로 제한되지 않습니다. Intune에서는 이제 여러 온-프레미스 Exchange 조직에서 Intune 조건부 액세스를 설정할 수 있도록 여러 Exchange Connector를 지원합니다.

Intune 온-프레미스 Exchange Connector를 사용하여 디바이스가 Intune에 등록했는지 여부 및 Intune 디바이스 준수 정책을 준수하는지 여부에 따라 온-프레미스 Exchange 사서함에 대한 디바이스 액세스를 관리할 수 있습니다. 커넥터를 설정하려면 Azure Portal에서 Intune 온-프레미스 Exchange Connector를 다운로드해 이를 Exchange 조직의 서버에 설치합니다. Microsoft Intune 대시보드에서 **온-프레미스 액세스**를 선택한 다음, **설치** 아래에서 **Exchange ActiveSync Connector**를 선택합니다. Exchange 온-프레미스 Connector를 다운로드하고 Exchange 조직의 서버에 설치합니다. 더 이상 테넌트당 하나의 Exchange Connector로 제한되지 않으므로 추가 Exchange 조직이 있는 경우 동일한 다운로드 절차를 따라 각 추가 Exchange 조직에 대해 커넥터를 설치할 수 있습니다.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>새로운 디바이스 하드웨어 세부 정보: CCID <!-- 2156657 -->
이제 각 디바이스에 대한 CCID(칩 카드 인터페이스 디바이스) 정보가 포함됩니다. 이를 확인하려면 **디바이스** > **모든 디바이스**를 차례로 선택하고, 디바이스를 선택하고, **하드웨어**를 선택한 다음, **네트워크 정보**> 아래에서 확인합니다.

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>모든 사용자 및 모든 디바이스를 범위 그룹으로 할당 <!-- 2196803 -->
이제 범위 그룹에서 모든 사용자, 모든 디바이스 및 모든 사용자/디바이스를 할당할 수 있습니다. 이렇게 하려면 **Intune 역할** > **모든 역할** > **정책 및 프로필 관리자** > **할당**을 차례로 선택하고, 할당을 선택한 다음, **범위(그룹)** 를 선택합니다.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>iOS 및 macOS 디바이스에 대한 UDID 정보 포함 <!-- 2219806 -->
iOS 및 macOS 디바이스에 대한 UDID(고유 디바이스 식별자)를 확인하려면 **디바이스** > **모든 디바이스**로 차례로 이동하고, 디바이스를 선택한 다음, **하드웨어**를 선택합니다. UDID는 **디바이스** > **모든 디바이스** &gt; 디바이스 선택 &gt; **속성** > **디바이스 소유권** 아래에 설정한 회사 디바이스에만 사용할 수 있습니다.

### <a name="intune-apps"></a>Intune 앱

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>앱 설치에 대한 향상된 문제 해결 <!-- 928990 -->
Microsoft Intune MDM 관리 디바이스에서 앱 설치에 실패하는 경우도 있습니다. 이러한 앱 설치에 실패할 경우, 실패 이유를 파악하거나 문제를 해결하기 어려울 수 있습니다. Microsoft에서는 앱 문제 해결 기능의 공개 미리 보기를 제공합니다. 개별 디바이스 아래에서 **관리 앱**이라는 새 노드를 확인할 수 있습니다. 여기에는 Intune MDM을 통해 전달된 앱이 나열됩니다. 노드 내부에는 앱 설치 상태 목록이 표시됩니다. 개별 앱을 선택하면 해당 앱에 대한 문제 해결 보기가 표시됩니다. 문제 해결 보기에는 응용 프로그램이 언제 생성, 수정, 대상 지정 및 디바이스에 전달되었는지를 포함한 앱의 전체 수명 주기기 표시됩니다. 또한 앱 설치에 실패할 경우, 오류 코드 및 오류의 원인에 대한 유용한 메시지가 표시됩니다. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune 앱 보호 정책 및 Microsoft Edge <!-- 1818968 -->
모바일 디바이스(iOS 및 Android)용 Microsoft Edge 브라우저에서는 이제 Microsoft Intune 앱 보호 정책을 지원합니다. Edge 애플리케이션에서 회사 Azure AD 계정으로 로그인하는 iOS 및 Android 장치 사용자는 Intune에서 보호됩니다. iOS 디바이스에서 **웹 콘텐츠에 대한 관리되는 요구** 정책을 사용하면 관리될 때 사용자가 Microsoft Edge에서 링크를 열 수 있습니다.

## <a name="week-of-may-14-2018"></a>2018년 5월 14일 주

### <a name="app-management"></a>앱 관리

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>정책, 앱, 인증서 및 네트워크 프로필의 설치 필요 <!-- 1553555 -->

관리자는 AutoPilot 디바이스를 프로비전하는 동안 Intune에서 정책, 앱, 인증서 및 네트워크 프로필을 설치할 때까지 최종 사용자가 Windows 10 RS4 데스크톱에 액세스하지 못하도록 차단할 수 있습니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>앱 보호 정책 <!-- 2144597 Part 2 --> 구성

Azure Portal에서 Intune 앱 보호 서비스 블레이드로 이동하는 대신 이제 Intune으로 직접 이동하면 됩니다. 이제 Intune 내에서는 앱 보호 정책에 대한 위치가 하나입니다. 모든 앱 보호 정책은 이미 앱 구성에서 Intune의 **모바일 앱** 블레이드에서 **앱 보호 정책** 아래에 있습니다. 이 통합은 클라우드 관리를 단순화하는 데 도움이 됩니다. Intune에서 모든 앱 보호 정책이 이미 설정되어 있으므로 이전에 구성한 정책을 수정할 수 있습니다. Intune APP(앱 보호 정책) 및 CA(조건부 액세스) 정책은 이제 **조건부 액세스**에 있으며 **Microsoft Intune** 블레이드의 **관리** 섹션이나 **Azure Active Directory** 블레이드의 **보안** 섹션에서 찾을 수 있습니다. 조건부 액세스 정책을 수정하는 방법에 대한 자세한 내용은 [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)를 참조하세요. 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

## <a name="week-of-may-7-2018"></a>2018년 5월 7일 주

### <a name="app-management"></a>앱 관리

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>삼성 Knox 모바일 등록 지원 <!--1112863-->

삼성 KME(Knox 모바일 등록)와 함께 Intune을 사용하는 경우, 많은 회사 소유 Android 디바이스를 등록할 수 있습니다. WiFi 또는 셀룰러 네트워크의 사용자는 디바이스를 처음 켤 때 몇 번만 탭하면 등록할 수 있습니다. Knox 배포 앱을 사용하는 경우 Bluetooth 또는 NFC를 사용하여 디바이스를 등록할 수 있습니다. 자세한 내용은 [삼성 Knox 모바일 등록을 사용하여 Android 디바이스 자동 등록](android-samsung-knox-mobile-enroll.md)을 참조하세요.

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Windows 10용 회사 포털에서 도움말 요청 <!-- 1874137 -->

이제 Windows 10용 회사 포털은 사용자가 문제에 대한 도움을 받기 위해 워크플로를 시작할 때 Microsoft에 직접 앱 로그를 전송합니다. 이렇게 하면 Microsoft에 제기된 문제를 더 쉽게 해결할 수 있습니다.

## <a name="week-of-april-23-2018"></a>2018년 4월 23일 주간

### <a name="app-management"></a>앱 관리

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android에서 MAM PIN에 대한 암호 지원<!-- 1438086 -->

Intune 관리자는 숫자 MAM PIN 대신 암호를 적용하는 애플리케이션 시작 요구 사항을 설정할 수 있습니다. 항목이 구성되면 사용자는 MAM 지원 애플리케이션에 대한 액세스 권한을 가져오기 전에 메시지가 표시될 때 암호를 설정하고 사용해야 합니다. 암호는 하나 이상의 특수 문자 또는 대/소문자 알파벳을 포함한 숫자 PIN으로 정의됩니다. Intune은 기존 숫자 PIN과 유사한 방식으로 암호를 지원합니다. 즉, 최소 길이를 설정하며 관리자 콘솔을 통해 반복 문자 및 시퀀스를 허용합니다. 이 기능을 사용하려면 Android에서 회사 포털의 최신 버전이 필요합니다. 현재 iOS에서는 이 기능을 사용할 수 있습니다.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS에 대한 LOB(기간 업무) 앱 지원 <!-- 1473977 -->
Microsoft Intune은 Azure Portal에서 macOS LOB 앱을 설치하는 기능을 제공할 예정입니다. GitHub에서 사용할 수 있는 도구에서 미리 처리된 macOS LOB 앱을 Intune에 추가할 수 있습니다. Azure Portal에서 **Intune** 블레이드의 **클라이언트 앱**을 선택합니다. **클라이언트 앱** 블레이드에서 **앱** > **추가**를 선택합니다. **앱 추가** 블레이드에서 **LOB(기간 업무) 앱**을 선택합니다. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Android Enterprise 작업 프로필 앱 할당을 위한 기본 제공된 모든 사용자 및 모든 디바이스 그룹 <!-- 1813073 -->
Android Enterprise 작업 프로필 앱 할당을 위해 기본 제공된 **모든 사용자** 및 **모든 디바이스** 그룹을 활용할 수 있습니다. 자세한 내용은 [Microsoft Intune에서 앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요.

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>사용자가 제거한 필수 앱을 Intune에서 다시 설치함 <!-- 1947010 -->
최종 사용자가 필수 앱을 제거할 경우 Intune에서 7일 재평가 주기를 기다리지 않고 24시간 이내에 앱을 자동으로 다시 설치합니다.

### <a name="device-configuration"></a>디바이스 구성

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>디바이스 프로필 차트 및 상태 목록에서 그룹의 모든 디바이스를 표시 <!-- 1449153 -->
디바이스 프로필을 구성할 때(**디바이스 구성** > **프로필**), iOS와 같은 디바이스 프로필을 선택합니다. iOS 디바이스 및 비 iOS 디바이스를 포함하는 그룹에 이 프로필을 할당합니다. 그래픽 차트 수는 프로필이 iOS *및* 비 iOS 디바이스에 적용되었음을 나타냅니다(**디바이스 구성** > **프로필** &gt; 기존 프로필 선택 &gt; **개요**). **개요** 탭에서 그래픽 차트를 선택하면 **디바이스 상태**에 iOS 디바이스 대신 그룹의 모든 디바이스가 나열됩니다. 

이 업데이트를 사용하면 그래픽 차트(**디바이스 구성** > **프로필** &gt; 기존 프로필 선택 &gt; **개요**)에는 특정 디바이스 프로필에 대한 개수만 표시됩니다. 예를 들어 구성 디바이스 프로필이 iOS 디바이스에 적용되는 경우 차트는 iOS 디바이스의 개수만 나열됩니다. 그래픽 차트를 선택하고 **디바이스 상태**를 열면 iOS 디바이스만 나열됩니다.

이 업데이트를 수행하는 동안 그래픽 사용자 차트는 일시적으로 제거됩니다. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Always On VPN for Windows 10 <!--1333666 -->

현재 [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)은 OMA-URI를 통해 만든 사용자 지정 VPN(가상 사설망) 프로필을 사용하여 Windows 10 디바이스에서 사용할 수 있습니다.

이 업데이트를 사용하면 관리자는 Azure Portal의 Intune에서 직접 Always On for Windows 10 VPN 프로필을 사용하도록 설정할 수 있습니다. Always On VPN 프로필은 다음과 같은 경우 자동으로 연결됩니다.

- 자신의 디바이스에 사용자가 로그인하는 경우
- 디바이스의 네트워크가 변경되는 경우
- 디바이스의 화면이 꺼졌다가 다시 켜지는 경우

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>교육 프로필에 대한 새 프린터 설정 <!-- 1308900 -->

교육 프로필의 경우 **프린터** 범주의 **프린터**, **기본 프린터**, **새 프린터 추가**에서 새 설정을 사용할 수 있습니다.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>개인 프로필에 호출자 ID 표시 - Android Enterprise 작업 프로필 <!--1098984 -->
디바이스에서 개인 프로필을 사용하는 경우 회사 연락처의 발신자 ID 정보가 최종 사용자에게 표시되지 않을 수 있습니다. 

이 업데이트에서는 **Android Enterprise** > **장치 제한** > **작업 프로필 설정**에서 새 설정이 지정됩니다.
- 개인 프로필에 회사 연락처의 발신자 ID 표시

사용하도록 설정하면(구성하지 않음) 회사 연락처의 발신자 정보가 개인 프로필에 표시됩니다. 차단하면 회사 연락처의 발신자 번호가 개인 프로필에 표시되지 않습니다. 

적용 대상: Android OS v6.0 이상의 Android 회사 프로필 디바이스

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>엔드포인트 보호 설정에 추가된 새 Windows Defender Credential Guard 설정 <!--1102252 --><!--from 1802 and 1804-->

이 업데이트를 사용하면 [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard)(**디바이스 구성** > **프로필** > **Endpoint Protection**)에 다음 설정이 포함됩니다. 

- **Windows Defender Credential Guard**: 가상화 기반 보안이 포함된 Credential Guard를 켭니다. 이 기능을 사용하도록 설정하면, **Platform Security Level with Secure Boot**(보안 부팅이 사용된 플랫폼 보안 수준) 및 **가상화 기반 보안**을 둘 다 사용하도록 설정할 경우, 다음 다시 부팅 시 자격 증명을 보호하는 데 도움이 됩니다. 다음 옵션을 사용할 수 있습니다.
  - **사용 안 함**: 이전에 **잠금 없이 설정** 옵션을 사용하여 Credential Guard를 켠 경우 원격으로 Credential Guard를 끕니다.

  - **UEFI 잠금을 사용하여 설정**: 레지스트리 키 또는 그룹 정책을 사용하여 Credential Guard를 사용하지 않도록 설정할 수 없게 합니다. 이 설정을 사용한 후 Credential Guard를 사용하지 않도록 설정하려면 그룹 정책을 “사용 안 함”으로 설정해야 합니다. 그런 다음, 물리적으로 존재하는 사용자가 있는 각 컴퓨터에서 보안 기능을 제거합니다. 이러한 단계는 UEFI에서 지속되는 구성을 지웁니다. UEFI 구성이 지속되는 한, Credential Guard는 사용하도록 설정됩니다.

  - **잠금 없이 설정**: 그룹 정책을 사용하여 원격으로 Credential Guard를 사용하지 않도록 설정할 수 있게 합니다. 이 설정을 사용하는 디바이스는 Windows 10(버전 1511) 이상에서 실행되어야 합니다.

다음 종속 기술은 Credential Guard를 구성할 때 자동으로 사용하도록 설정됩니다. 

  - **VBS(가상화 기반 보안) 사용**: 다음 다시 부팅 시 VBS(가상화 기반 보안)를 켭니다. 가상화 기반 보안에서는 Windows 하이퍼바이저를 사용하여 보안 서비스에 대한 지원을 제공하며, 보안 부팅이 필요합니다.
  - **보안 부팅 및 DMA(직접 메모리 액세스)**: 보안 부팅 및 직접 메모리 액세스를 통해 VBS를 켭니다. DMA 보호는 하드웨어 지원이 필요하며 제대로 구성된 디바이스에서만 사용하도록 설정됩니다. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>SCEP 인증서에서 사용자 지정 주체 이름 사용 <!-- 2064190 -->
SCEP 인증서 프로필에서 사용자 지정 주체에 **OnPremisesSamAccountName** 일반 이름을 사용할 수 있습니다. 예를 들어 `CN={OnPremisesSamAccountName})`를 사용할 수 있습니다.

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Android Enterprise 작업 프로필에서 카메라 및 화면 캡처 차단 <!-- 1098977 -->
두 개의 새로운 속성은 Android 디바이스에 대한 디바이스 제한을 구성할 때 차단하는 데 사용할 수 있습니다. 
- 카메라: 디바이스에서 모든 카메라에 대한 액세스 차단
- 화면 캡처: 화면 캡처를 차단하고, 안전하지 않은 동영상 출력의 디스플레이 디바이스에 콘텐츠가 표시되지 않도록 방지

Android Enterprise 작업 프로필에 적용됩니다.


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>macOS High Sierra 10.13.2+를 사용하는 디바이스에서 사용자를 위한 새로운 등록 단계 <!--1734567 -->
macOS high Sierra 10.13.2에 “사용자 승인” MDM 등록의 개념이 도입되었습니다. 승인된 등록을 사용하면 Intune에서 몇 가지 보안에 민감한 설정을 관리할 수 있습니다. 자세한 내용은 Apple의 지원 문서를 참조하세요. https://support.apple.com/HT208019

macOS 회사 포털을 사용하여 등록된 디바이스는 최종 사용자가 [시스템 기본 설정]을 열고 수동으로 승인을 제공하지 않는 한 “사용자 승인되지 않음”으로 간주됩니다. 이를 위해 macOS 회사 포털은 이제 macOS 10.13.2 이상의 사용자에게 등록 프로세스 마지막 단계에서 해당 등록을 수동으로 승인하도록 안내합니다. Intune 관리 콘솔은 등록된 디바이스가 사용자 승인되지 않은 경우 보고합니다.



### <a name="device-management"></a>디바이스 관리

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>ATP(Advanced Threat Protection)와 Intune이 완전히 통합됨 <!-- 1629303 -->

[ATP(Advanced Threat Protection)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)는 Windows 10 디바이스의 위험 수준을 표시합니다. Windows Defender 보안 센터(ATP 포털)에서 Microsoft Intune에 대한 연결을 만들 수 있습니다. 연결이 생성되면 Intune 준수 정책을 사용하여 허용되는 위협 수준이 결정됩니다. 위협 수준을 초과할 경우 AD(Azure Active Directory) 조건부 액세스 정책을 통해 조직 내의 여러 앱에 대한 액세스를 차단할 수 있습니다.

이 기능을 사용하면 ATP가 Windows 10 디바이스에서 파일 검사, 위협 검색, 위험 보고 등을 수행할 수 있습니다.

[Intune에서 조건부 액세스로 ATP 사용](advanced-threat-protection.md)을 참조하세요.

#### <a name="support-for-user-less-devices----1637553---"></a>사용자가 지정되지 않은 디바이스에 대한 지원 <!-- 1637553 -->
Intune은 Microsoft Surface Hub와 같은 사용자가 지정되지 않은 디바이스에서 준수를 평가하는 기능을 지원합니다. 준수 정책은 특정 디바이스를 대상으로 지정할 수 있습니다. 따라서 연결된 사용자가 없는 디바이스에 대해 준수(및 비준수)를 확인할 수 있습니다.

#### <a name="delete-autopilot-devices----1713650---"></a>Autopilot 디바이스 삭제 <!-- 1713650 -->
Intune 관리자는 [Autopilot 디바이스를 삭제](enrollment-autopilot.md#delete-autopilot-devices)할 수 있습니다.

#### <a name="improved-device-deletion-experience---1832333---"></a>향상된 디바이스 삭제 환경 <!--1832333 -->
이제 [Intune에서 디바이스를 삭제](devices-wipe.md#delete-devices-from-the-intune-portal)하기 전에 회사 데이터를 제거하거나 디바이스를 출하 시 설정으로 초기화할 필요가 없습니다.

새 환경을 보려면 Intune에 로그인하고 **디바이스** > **모든 디바이스** &gt; 디바이스 이름 &gt; **삭제**를 선택합니다.

초기화/사용 중지 확인을 수행하려면 **삭제**하기 전에 **회사 데이터 제거** 및 **출하 시 설정으로 리셋**을 실행하여 표준 디바이스 수명 주기를 사용할 수 있습니다. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>분실 모드에 있을 때 iOS에서 소리 재생 <!-- 1947769 -->
감독 중인 iOS 디바이스가 MDM(모바일 디바이스 관리) [분실 모드](device-lost-mode.md)에 있는 경우 [소리를 재생](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device)할 수 있습니다(**디바이스** > **모든 디바이스** &gt; iOS 디바이스 선택 &gt; **개요** > **자세히**). 소리는 디바이스가 분실 모드에서 제거되거나 사용자가 디바이스에서 소리를 사용하지 않도록 설정할 때까지 계속 재생됩니다. iOS 디바이스 9.3 이상에서 적용됩니다.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Intune 디바이스에서 수행된 검색에서 웹 결과 차단 또는 허용 <!--1972804-->

이제 관리자는 디바이스에서 수행된 검색에서 웹 결과를 차단할 수 있습니다.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Apple MDM 푸시 인증서 업로드 실패에 대한 향상된 오류 메시지 <!-- 2172331 -->

오류 메시지는 기존 MDM 인증서를 갱신할 때 동일한 Apple ID를 사용해야 함을 설명합니다.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>가상 머신에서 macOS용 회사 포털 테스트 <!-- 2216679 -->

Microsoft에서는 IT 관리자가 Parallels Desktop 및 VMware Fusion에서 가상 머신의 macOS용 회사 포털 앱을 테스트하는 데 도움이 되는 지침을 게시했습니다. [테스트를 위해 macOS 가상 머신 등록](macos-enroll.md#enroll-virtual-macos-machines-for-testing)에서 자세히 알아보세요.


### <a name="user-interface"></a>사용자 인터페이스

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Windows 10 회사 포털의 개선된 디바이스 타일 <!--2213364 -->

저시력 사용자가 더 쉽게 액세스할 수 있고 화면 읽기 도구의 성능이 개선되도록 타일이 업데이트되었습니다.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>macOS용 회사 포털 앱에 진단 보고서 보내기 <!-- 2216677 -->
사용자가 Intune 관련 오류를 보고하는 방법을 개선하기 위해 macOS 디바이스용 회사 포털 앱이 업데이트되었습니다. 회사 포털 앱에서 직원은 다음을 수행할 수 있습니다.

- Microsoft 개발자 팀에 직접 진단 보고서를 업로드합니다.
- 인시던트 ID를 회사의 IT 지원 팀에게 이메일로 전송합니다.

자세한 내용은 [macOS에 대한 오류 보내기](/intune-user-help/send-errors-macos)를 참조하세요.

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Windows 10용 회사 포털 앱에서 Intune이 Fluent Design System에 적응함 <!-- 1195010 -->
Windows 10용 Intune 회사 포털 앱이 [Fluent Design System의 탐색 보기](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics)로 업데이트되었습니다. 앱의 옆쪽에 모든 최상위 페이지의 정적 세로 목록이 표시됩니다. 링크를 클릭하여 빠르게 페이지를 보고 페이지 간에 전환할 수 있습니다. 이 업데이트는 Intune에서 더욱 공감할 수 있고 친숙한 적응형 환경을 만들려는 Microsoft의 지속적인 노력의 일부로 여러 업데이트 중 첫 번째로 선보이는 것입니다. 업데이트된 형태를 보려면 [앱 UI 의 새로운 기능](whats-new-app-ui.md)으로 이동하세요.

## <a name="week-of-april-16-2018"></a>2018년 4월 16일 주간

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>iOS용 Cisco AnyConnect 클라이언트 사용 <!-- 1333708 -->

iOS용 새 VPN 프로필을 만들 때 이제 **Cisco AnyConnect** 및 **Cisco Legacy AnyConnect**의 두 가지 옵션이 있습니다. Cisco AnyConnect 프로필은 4.0.7x 이상 버전을 지원합니다. 기존 iOS Cisco AnyConnect VPN 프로필은 **Cisco Legacy AnyConnect**로 레이블이 지정되며, 현재와 마찬가지로 Cisco AnyConnect 4.0.5x 및 이전 버전에서 계속 작동합니다.

> [!NOTE]
> 이 변경 내용은 iOS에만 적용됩니다. Android, Android Enterprise 작업 프로필 및 macOS 플랫폼에는 계속해서 Cisco AnyConnect 옵션을 하나만 사용할 수 있습니다.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>이제 Jamf에 등록된 macOS 디바이스를 Intune에 등록할 수 있음 <!-- 2370684 -->

macOS 회사 포털 버전 1.3 및 1.4에서는 Jamf 디바이스가 Intune에 등록되지 않았습니다. macOS 포털 버전 1.4.2에서 이 문제가 해결되었습니다.


## <a name="week-of-april-9-2018"></a>2018년 4월 9일 주간  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Android용 회사 포털 앱에서 업데이트된 도움말 환경 <!-- 1631531 -->

Android 플랫폼에 대한 모범 사례에 맞추기 위해 Android용 회사 포털 앱에서 도움말 환경을 업데이트했습니다. 이제 사용자 앱에서 문제가 발생하는 경우 **메뉴** > **도움말**을 누르면 됩니다.
- 또한 진단 로그를 Microsoft에 업로드합니다.
- 회사 지원 담당자에게 문제 및 인시던트 ID를 설명하는 이메일을 보냅니다.  

업데이트된 도움말 환경을 확인하려면 [이메일을 사용하여 로그 보내기](/intune-user-help/send-logs-to-your-it-admin-by-email-android) 및 [Microsoft에 오류 보내기](/intune-user-help/send-logs-to-microsoft-android)로 이동합니다.


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>새 등록 실패 추세 차트 및 실패 이유 테이블 <!-- 1471783 -->

등록 개요 페이지에서 등록 실패의 추세와 실패 원인 상위 5개를 확인할 수 있습니다. 차트 또는 테이블을 클릭하면 세부 사항을 드릴스루하여 문제 해결 도움말 및 재구성 제안을 찾을 수 있습니다.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>앱 보호 정책을 구성한 업데이트 <!-- 2144597 -->

Azure Portal의 Microsoft Intune 서비스에서는 **Intune 앱 보호** 서비스 블레이드에서 **모바일 앱** 블레이드로 일시적으로 리디렉션됩니다. 모든 앱 보호 정책이 Intune의 앱 구성에 있는 **모바일 앱** 블레이드에 이미 있습니다. Intune 앱 보호로 이동하는 대신 Intune으로 이동하세요. 2018년 4월에는 리디렉션을 중지하고 **Intune 앱 보호** 서비스 블레이드를 완전히 제거하여 Intune 내 앱 보호 정책의 위치가 하나만 있도록 합니다. 

**이 변경 사항은 어떤 영향을 미치나요?**
이 변경 사항은 Intune 독립형 고객과 하이브리드(Configuration Manager와 Intune) 고객 모두에 영향을 줍니다. 이 통합은 클라우드 관리 관리를 단순화하는 데 도움이 됩니다.

**이러한 변경에 대비하려면 어떻게 해야 하나요?**
**Intune 앱 보호** 서비스 블레이드 대신 **Intune**을 즐겨찾기로 태그를 지정하고 Intune 내 **모바일** 앱 블레이드의 앱 보호 정책 워크플로에 익숙해지도록 합니다. 짧은 시간 동안 리디렉션된 다음, **앱 보호** 블레이드가 제거됩니다. Intune에서 모든 앱 보호 정책이 이미 설정되어 있으므로 조건부 액세스 정책을 수정할 수 있습니다. 조건부 액세스 정책을 수정하는 방법에 대한 자세한 내용은 [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)를 참조하세요. 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요. 


## <a name="week-of-april-2-2018"></a>2018년 4월 2일의 주간

### <a name="intune-apps"></a>Intune 앱

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>iOS용 회사 포털 앱의 사용자 환경 업데이트 <!--1412866 -->
iOS용 회사 포털 앱에 대한 주요 사용자 환경 업데이트가 릴리스되었습니다. 이 업데이트는 현대적인 모양과 느낌을 포함하여 시각적으로 완전히 새롭게 설계했습니다. 앱의 기능은 유지하면서도 유용성과 접근성을 향상시켰습니다.  

또한 다음을 확인할 수 있습니다.
- iPhone X 지원
- 더 빨라진 앱 시작과 응답 로드로 사용자 시간 단축
- 사용자에게 최신 상태 정보를 제공하는 추가 진행률 표시줄
- 문제 발생 시 이를 보고하기 쉽도록 사용자가 로그를 업로드하는 방식 개선 사항  

업데이트된 형태를 보려면 [앱 UI 의 새로운 기능](whats-new-app-ui.md)으로 이동하세요.

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Intune APP 및 CA를 사용하여 온-프레미스 Exchange 데이터 보호 <!-- 1056954 -->
이제 Intune APP(앱 정책 보호) 및 CA(조건부 액세스)를 사용하여 Outlook Mobile에서 온-프레미스 Exchange 데이터에 대한 액세스를 보호할 수 있습니다. Azure Portal 내에서 앱 보호 정책을 추가하거나 수정하려면 **Microsoft Intune** > **클라이언트 앱** > **앱 보호 정책**을 선택합니다. 이 기능을 사용하기 전에 [iOS 및 Android 요구 사항에 대한 Outlook](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)을 충족하는지 확인합니다.

## <a name="notices"></a>알림

### <a name="upcoming-password-enforcement-change-for-macos-10142-in-intune---1873216--"></a>Intune의 macOS 10.14.2에 대한 암호 적용 변경 예정 <!--1873216-->
Intune이 macOS 버전 10.13 이상을 실행하는 디바이스에 대해 새로 릴리스된 Apple의 "다음 인증 시 암호 변경" 설정을 통합할 계획임을 7월에 MC145129에서 다시 알려드립니다. 현재 2월에 macOS 10.14.2 이상에 대해 이 설정을 배포할 계획입니다. 

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
이는 macOS 10.14.2 이상을 실행하는 디바이스를 보유하거나 보유할 계획 중인 경우에 영향을 줍니다. 이제 Apple이 "새 인증에서 암호 변경" 설정을 도입했으므로 Intune은 암호 정책을 적용할 때 호환되는 해당 암호를 사용자가 업데이트하도록 강제할 수 있습니다. macOS 사용자는 해당 암호가 이미 규정을 준수하는 경우라도 이 새로운 Apple 기능을 통합하면 해당 암호를 업데이트하라는 요청을 받게 됩니다. 암호가 이미 규격이고 암호 반복에 대한 요구 사항이 없는 경우 최종 사용자는 기존 암호로 업데이트할 수 있습니다. 최종 사용자는 해당 디바이스에 인증 또는 로그인하려고 할 때 해당 암호를 업데이트하라는 요청만 볼 수 있습니다. 디바이스가 규정 준수로 표시될 때까지 회사 리소스를 차단하면 macOS 10.14.2가 설치된 디바이스의 최종 사용자가 암호를 재설정할 때까지 이메일 또는 SharePoint 사이트와 같은 회사 리소스에 액세스하는 것이 차단될 수 있습니다. 나중에 구성 및 규정 준수 정책으로 모두 업데이트하면 대상 사용자에게 자신의 암호를 업데이트하도록 강제할 수 있습니다. 이 변경을 구현하기 전에 고객 조사에 따르면 최종 사용자는 일반적으로 해당 암호를 등록하거나 규정 준수 유지를 위해 해당 암호를 재설정하라는 요청을 받은 후 암호를 업데이트하기 때문에 대부분의 고객은 이러한 변경에 영향을 받지 않습니다.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?
기술 지원팀에게 알리려고 할 수 있습니다. 이 변경 내용이 롤아웃될 때 이 새로운 기능 페이지가 업데이트됩니다. 이 macOS 디바이스 암호 정책을 적용하지 않으려면 기존 macOS 정책을 할당 해제하거나 삭제하는 것이 좋습니다.

###<a name="plan-for-change-update-to-ios-setting-for-supervised-devices-in-the-intune-console"></a>변경 계획: Intune 콘솔에서 감독되는 디바이스에 대한 iOS 설정 업데이트  
Intune 서비스의 2월 업데이트에서 감독되는 iOS 디바이스에 대해 '디바이스 설정에서 제한 사용' 설정을 "화면 시간(감독 모드인 경우에만)"으로 이름을 바꿉니다. 이렇게 변경하면 최종 사용자 환경이 iOS 버전에 따라 변경됩니다.

####<a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
"디바이스 설정에서 제한 사용(감독 모드인 경우에만)"의 설정을 "화면 시간(감독 모드인 경우에만)"으로 이름을 바꾸면 감독되는 디바이스의 환경은 다음과 같습니다(Apple 등록 프로그램을 사용하여 등록된 디바이스). 

iOS 11.4 이전 버전의 디바이스의 경우: 이전처럼 사용자가 디바이스 제한을 수정하지 못하게 하려면 이 설정을 사용할 수 있습니다. 최종 사용자에게 환경의 변경이 표시되지 않습니다.
 
iOS 12 이상의 디바이스의 경우: 설정 > 일반 > 디바이스 관리 > 관리 프로필 > 제한에서 제한 탭이 더 이상 최종 사용자에게 표시되지 않습니다.
대신 이 제한 탭은 설정 > 일반 > 화면 시간에 속하게 됩니다. 이 설정을 "차단"으로 구성하면 사용자는 해당 디바이스에서 화면 시간 설정을 변경하지 못하며, 또한 콘텐츠 및 개인 정보 제한이 포함됩니다.

####<a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?
iOS 12 이상 버전으로 업그레이드하는 디바이스의 환경 변경을 확인하려면 최종 사용자 지침을 업데이트합니다.


###<a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>변경 계획: Intune에서 iOS 12 등록에 대한 워크플로 변경
Apple에서는 MDM(모바일 디바이스 관리) 서비스에 등록된 iOS 디바이스와 관련한 몇 가지 변경 사항을 발표했습니다. 이러한 변경은 향후 모든 iOS 릴리스를 비롯하여 2019년 봄 iOS 릴리스에 표시될 가능성이 있습니다.

####<a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
최종 사용자가 봄에 자신의 디바이스를 이 iOS 12의 새 버전으로 업그레이드하는 경우 수정된 워크플로가 있으며 Intune에 등록을 완료하려면 추가 단계를 수행해야 합니다. Apple에서 이러한 변경 내용을 도입하는 경우 최종 사용자는 다음을 수행해야 합니다. • 관리 프로필을 다운로드하려면 회사 포털 앱에서 등록 프로세스를 시작하고 • 설정 > 일반 > 프로필로 이동하고 • 올바른 프로필을 선택하고 클릭하여 설치하고 • 등록을 완료하려면 회사 포털로 되돌아갑니다. 

이미 등록된 디바이스 및 새 iOS 릴리스로 업그레이드는 등록되지 않고 새 등록이 필요하지 않은 경우 영향을 받지 않아야 합니다.
Apple에서는 iOS 12.1 이전 버전에서 실행되는 디바이스의 등록 환경을 이 새 릴리스를 통해 변경하지 않습니다.

####<a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?
설명서 및 최종 사용자 지침의 업그레이드를 계획해야 합니다. 이러한 변경 내용을 기술 지원팀에도 알려주려 할 수 있습니다. 이 변경 내용이 실현되면 메시지 센터 및 새로운 기능 페이지를 통해 계속 알려드리겠습니다.

예상 등록 흐름의 스크린샷 및 비디오를 통해 지원 블로그 게시물에 대한 추가 정보를 클릭합니다.

####<a name="additional-information"></a>추가 정보
https://aka.ms/iOS_enrollment_changes

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>변경 계획: iOS용 Intune 회사 포털 앱으로 사용자 환경 업데이트
Intune이 곧 iOS 회사 포털 앱에 대한 주요 사용자 환경 업데이트를 릴리스할 예정임을 알려드립니다. 이 업데이트는 고급 필터를 갖춘 홈 페이지의 시각적 개체 디자인과 앱 및 책에 대한 빠른 액세스 기능을 제공합니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
이 사용자 환경 업데이트는 현재 iOS 회사 포털 기능을 유지 관리하면서 다음과 같은 기능을 제공합니다.
- 네이티브 iOS 모양과 느낌을 갖춘 홈 페이지 
- 콘텐츠 형식(앱 또는 전자책) 및 가용성(등록 없이 필요하거나 사용 가능한 디바이스 관리)을 기준으로 필터링하는 기능을 비롯하여 콘텐츠 목록 및 검색 필터링 기능
- 전자책 검색 기능
- 앱 및 전자책 검색 기록 - Apple TestFlight 프로그램의 일부인 경우 Intune의 업데이트된 iOS 회사 포털 앱이 출시될 때 시험판 버전에 대한 알림을 받게 됩니다. Apple TestFlight 프로그램에 속해 있지 않다면 등록할 수 있습니다. 등록하면 업데이트된 회사 포털 앱을 사용해 본 이후에 최종 사용자에게 제공할 수 있습니다. Intune 팀에 직접 피드백을 제공할 수도 있습니다.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?
어떠한 작업도 수행할 필요가 없습니다. 이러한 변경 내용은 향후 iOS CP 앱 릴리스에서 발표될 것입니다. 

#### <a name="additional-information"></a>추가 정보
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="plan-for-change-exchange-online-to-intune-connector-will-not-be-available-in-intune----3105122---"></a>변경 계획: Exchange Online-Intune 커넥터는 Intune에서 사용할 수 없음 <!-- 3105122 -->
Exchange Online 및 조건부 액세스 환경을 간소화하기 위해 Exchange Online-Intune ‘서비스 간’ 커넥터는 사용하지 않도록 설정됩니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
당사 기록에 따르면 사용자 환경에서 ‘서비스 간’ 커넥터 기능을 사용할 수 있으므로 이 메시지가 표시됩니다. ‘서비스 간’ 커넥터는 Exchange Online에 대한 Exchange Active Sync 전용 디바이스의 Intune 관리를 지원하지만 온-프레미스 인프라를 지원하지 않습니다. 이 커넥터는 콘솔에 표시되는 방법 때문에 실제로 CA에 필요하지 않을 때 CA(조건부 액세스)에 필요한 것처럼 보입니다. Intune 서비스의 2월 업데이트에서 이 커넥터를 콘솔에 표시하지 않으려면 새 커넥터 설정 단추를 사용하지 않도록 설정합니다. 그런 다음, 2019년 3월에는 모든 기존 Exchange Online-Intune 커넥터를 사용하지 않도록 설정합니다.

사용자 환경에서 이러한 커넥터를 사용하는 경우 커넥터가 3월에 사용되지 않도록 설정된 후에는 Intune에서 Exchange Active Sync 전용 디바이스를 모니터링하거나 초기화할 수 없습니다. 이 변경 중에 최종 사용자에게 미치는 영향은 없습니다.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?

서비스 간 커넥터가 설정되어 있고 Exchange Active Sync 전용 디바이스가 있는 경우에는 다른 디바이스 관리 방법으로 전환하세요. 다음과 같은 옵션을 선택할 수 있습니다.

- MDM(모바일 디바이스 관리)에 디바이스 등록
- Intune 앱 보호 정책을 사용하여 디바이스 관리
- 이 설명서에 설명된 대로 Exchange 컨트롤을 사용합니다. 

#### <a name="additional-information"></a>추가 정보
[Intune 및 Exchange Online용 Exchange 서비스 커넥터 구성](https://docs.microsoft.com/intune/exchange-service-connector-configure)



### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>변경 계획: Intune for Education의 성능 업데이트 <!--1750215-->
사용자 또는 디바이스에 설정을 할당할 때 속도 및 신뢰성을 높이기 위해 Intune for Education에 몇 가지 업데이트가 추가될 예정입니다. 이러한 변경의 일환으로 11월 말경에 정책 또는 설정 할당을 새 그룹으로 이전할 예정입니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?

Intune for Education 고객으로서, 두 개의 동적 Azure AD(Azure Active Directory) 그룹인 “모든 사용자” 및 “모든 디바이스”를 갖게 됩니다. 이러한 업데이트를 통해 해당 "모든 사용자" 및 "모든 디바이스" Azure AD 그룹은 Intune for Education 콘솔에 표시되지 않습니다. 그러나 여전히 Azure 콘솔의 Intune에서 볼 수 있으며 "모든 사용자(폐기됨, 사용하지 마세요)" 및 "모든 디바이스(폐기됨, 사용하지 마세요)"로 이름이 변경됩니다.

업데이트가 출시되면 더 이상 Azure AD 그룹을 사용하여 Intune에서 앱과 설정을 할당할 필요가 없습니다. 대신, 이전처럼 "모든 사용자" 및 "모든 디바이스"로 계속 표시되는 Intune for Education 콘솔의 새 그룹으로 설정 할당을 이동할 예정입니다. 이러한 변경 내용은 백엔드에 있으므로 Intune for Education 콘솔에서 다른 점을 발견하지 못합니다. 최종 사용자 또는 등록된 디바이스에 미치는 영향은 없습니다. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
정책 할당을 이동하는 동안 작업을 수행할 필요가 없습니다. 현재 Intune for Education 콘솔에 정책을 할당한 경우 계속 그렇게 수행합니다.

현재 위의 언급한 Azure의 Intune에서 Azure AD 그룹에 정책을 할당하는 경우 대신 Intune for Education 콘솔의 모든 사용자 및 모든 디바이스 그룹에 정책을 할당합니다. 콘솔에서 Azure AD 그룹의 이름이 사용되지 않는 것으로 변경되면 Azure AD에서 정책 할당을 중지합니다. 이름이 변경된 그룹을 현재 다른 용도로 사용하지 않는 경우 삭제해야 합니다.


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>작업 수행: Intune에서 Android 디바이스 제한 또는 규정 준수 정책 암호 설정을 업데이트하세요.
Intune은 Android 4.4 이상의 디바이스에 사용 가능한 암호 유형 "디바이스 기본값"을 제거합니다. Android 플랫폼과 디바이스 기본값의 차이로 인해 해당 정책은 종종 디바이스에서 선택 사항으로 처리됩니다. Android에서 이 설정을 적용할 때 혼동을 없애기 위해 향후 출시될 UI에서 이 설정을 제거할 예정입니다. 
#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
- 디바이스에 암호가 필요한 경우 "디바이스 기본값"을 사용하는 대신 Android 플랫폼 프로필을 편집하여 필요한 암호 유형을 명확히 밝히는 것이 좋습니다.
- 최종 사용자가 암호를 만들지 여부를 결정하도록 하려면 "구성되지 않음" 단추를 선택합니다. UI에서 이 설정을 제거할 때 설정이 여전히 설정된 경우, 다음 프로필 편집 시 "디바이스 기본값" 이외의 값을 선택하라는 메시지가 표시됩니다.
이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
Android 및 Android 엔터프라이즈 디바이스 제한 및 규정 준수 정책의 암호 설정을 검토하세요. 이러한 설정은 규정 준수 정책의 시스템 보안 및 디바이스 제한에 대한 디바이스 암호 또는 작업 프로필 설정 중 하나에서 나열됩니다. 추가 정보에는 이러한 설정이 구성된 위치에 대한 자세한 정보 및 스크린샷 링크가 있습니다.
#### <a name="additional-information"></a>추가 정보
https://aka.ms/PasswordSettings 

