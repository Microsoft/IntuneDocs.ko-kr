---
title: 초기 버전 | Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 초기 버전
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/3/2018
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
ms.openlocfilehash: 35298713738c666ca19d57e647412729a85bbc4a
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112836"
---
# <a name="the-early-edition-for-microsoft-intune---december-2018"></a>Microsoft Intune 초기 버전 - 2018년 12월

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

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 엔터프라이즈 APP-WE 앱 배포 <!-- 1171203 -->
등록되지 않은 APP-WE(등록이 없는 앱 보호 정책) 배포 시나리오에 있는 Android 디바이스의 경우 관리형 Google Play를 사용하여 스토어 앱 및 LOB 앱을 사용자에게 배포할 수 있습니다. 특히 IT 부서에서는 최종 사용자에게 알 수 없는 소스에서 설치를 허용하여 해당 디바이스의 보안 상태를 느슨하게 하도록 더 이상 요구하지 않는 앱 카탈로그 및 설치 환경을 최종 사용자에게 제공할 수 있습니다. 또한 이 배포 시나리오는 향상된 최종 사용자 환경을 제공합니다.

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Windows 10 이상 디바이스에서 DNS 설정을 사용할 때 자동으로 규칙을 연결 및 유지하는 새 옵션 <!-- 1333665, 2999078 -->
Windows 10 이상 디바이스에서는 contoso.com과 같은 도메인 확인을 위한 DNS 서버 목록을 포함하는 VPN 구성 프로필을 만들 수 있습니다. 여기에는 이름 확인(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **Windows 10 이상** 선택 > 프로필 유형에서 **VPN** 선택 > **DNS 설정** >**추가**)이 포함됩니다. 

- **자동으로 연결**: **사용하도록 설정**한 경우 디바이스가 입력한 도메인(예: contoso.com)에 연결되면 디바이스가 자동으로 VPN에 연결됩니다.
- **영구**: 기본적으로 모든 NRPT(이름 확인 정책 테이블) 규칙은 디바이스가 이 VPN 프로필을 사용하여 연결되어 있는 한 활성 상태입니다. NRPT 규칙에서 이 설정이 **사용하도록 설정**되면 VPN 연결이 끊어지거나 VPN 프로필이 제거되더라도 디바이스에서 규칙이 활성 상태로 유지됩니다. 규칙은 PowerShell 등을 사용하여 수동으로 제거될 때까지 유지됩니다.

[Windows 10 VPN 설정](vpn-settings-windows-10.md)에서는 현재 설정 목록을 설명합니다. 

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642-eeready---"></a>S/MIME를 사용하여 사용자의 여러 디바이스를 암호화 및 서명 <!-- 1333642 eeready -->
가져온 새 인증서 프로필을 사용하는 S/MIME 메일 암호화가 지원됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼 선택 > **PKCS 가져온 인증서** 프로필 유형). Intune에서 PFX 형식의 인증서를 가져올 수 있습니다. 그런 다음, Intune은 단일 사용자에 의해 등록된 여러 디바이스에 이러한 동일한 인증서를 제공할 수 있습니다. 다음도 포함되어 있습니다.

- 네이티브 iOS 이메일 프로필은 PFX 형식의 가져온 인증서를 사용하는 S/MIME 암호화 활성화를 지원합니다.
- Windows Phone 10 디바이스의 네이티브 메일 앱은 S/MIME 인증서를 자동으로 사용합니다.
- 여러 플랫폼에서 개인 인증서를 제공할 수 있습니다. 하지만 모든 이메일 앱이 S/MIME를 지원하지는 않습니다.
- 다른 플랫폼에서 S/MIME를 활성화하도록 메일 앱을 수동으로 구성해야 할 수 있습니다.  
- S/MIME 암호화를 지원하는 이메일 앱은 해당 게시자의 인증서 저장소에서 읽기와 같은 MDM에서 지원할 수 없는 방식으로 S/MIME 이메일 암호화에 대한 인증서 가져오기를 처리할 수 있습니다.

지원 됩니다. Windows, Windows Phone 10, macOS, iOS, Android

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Windows 회사 포털 앱의 도움말 및 지원 페이지 <!-- 1488939 -->
새 페이지가 Windows 회사 포털 앱에 추가됩니다. 도움말 및 지원 페이지에서는 헬프 데스크 연락처 정보를 제공합니다. 또한 최종 사용자는 문제가 있는 경우 회사 포털 로그를 보낼 수 있습니다. 이 페이지에서는 최종 사용자를 지원하기 위한 FAQ 섹션도 제공합니다.

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Windows 10 디바이스의 VPN 프로필에 신뢰할 수 있는 네트워크 검색 사용 <!-- 1500165 -->
신뢰할 수 있는 네트워크 검색을 사용하는 경우 사용자가 이미 신뢰할 수 있는 네트워크에 있을 때 VPN 프로필에서 자동으로 VPN에 연결되지 않도록 할 수 있습니다. DNS 접미사를 추가하여 Windows 10 이상을 실행하는 디바이스에서 신뢰할 수 있는 네트워크 검색을 사용하도록 설정할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 프로필의 **Windows 10 이상** > 프로필 유형의 **VPN**).
[Windows 10 VPN 설정](vpn-settings-windows-10.md)에는 현재 VPN 설정이 나열됩니다.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune 앱 SDK는 256비트 암호화 키를 지원함 <!-- 1832174 -->
iOS용 Intune 앱 SDK는 앱 보호 정책에서 암호화를 사용하도록 설정할 때 256비트 암호화 키를 사용합니다. SDK는 이전 SDK 버전을 사용하는 콘텐츠 및 앱과 호환성을 위해 128비트 키 지원을 계속 제공합니다.

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917---"></a>Intune 프로필에서 공유 PC 설정 사용 <!-- 1907917 -->
현재는 사용자 지정 OMA-URI 설정을 사용하여 Windows 10 데스크톱 디바이스에서 공유 PC 설정을 구성할 수 있습니다. 새 프로필을 추가하여 공유 PC 설정을 구성합니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **공유 다중 사용자 디바이스**).
적용 대상: Windows 10 이상, Windows Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 정책에서 인증 방법 및 회사 포털 앱 설치를 업데이트함 <!-- 1927359 -->
Intune은 App Store에서 설치될 경우 회사 포털 앱을 특정 디바이스에서 더 이상 지원하지 않습니다. 이 변경은 등록 중에 Apple 설정 도우미로 인증하는 경우에만 적용됩니다. 또한 이 변경은 다음을 통해 등록된 iOS 디바이스에만 영향을 줍니다.  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple DEP(장비 등록 프로그램)

사용자가 App Store에서 회사 포털 앱을 설치한 다음, 이 앱을 통해 이러한 디바이스를 등록하는 경우 오류가 발생합니다. 이 디바이스는 등록 중에 Intune에서 자동으로 푸시된 경우에만 회사 포털을 사용해야 합니다. Azure Portal에서 Intune의 등록 프로필이 업데이트되므로 디바이스 인증 방법 및 디바이스가 회사 포털 앱을 받는 방법을 지정할 수 있습니다. DEP 디바이스 사용자가 회사 포털을 사용하도록 하려면 등록 프로필에서 기본 설정을 지정해야 합니다. 또한 회사 포털 앱에서 **디바이스 식별** 화면이 더 이상 사용되지 않습니다.  
이미 등록된 DEP 디바이스에 회사 포털을 설치하려면 Intune > 클라이언트 앱으로 이동하고 앱 구성 정책을 사용하여 이 앱을 관리형 앱으로 푸시해야 합니다. 이러한 단계를 수행하는 방법에 대한 자세한 내용은 이후 문서에서 간략하게 설명합니다.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>관리자가 아닌 사용자는 Azure AD에 조인된 Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 수 있음 <!-- 2147379 -->
Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼) > **Endpoint Protection**(프로필 유형) > **Windows 암호화**) BitLocker 설정을 추가합니다. 이 업데이트에는 표준 사용자(관리자가 아닌 사용자)가 암호화를 사용하도록 설정하게 허용하는 새 BitLocker 설정이 포함됩니다. 현재 설정을 보려면 [Windows 10용 Endpoint Protection 설정](endpoint-protection-windows-10.md#windows-encryption)을 참조하세요.

### <a name="intune-app-pin----2298397---"></a>Intune 앱 PIN <!-- 2298397 -->
IT 관리자는 최종 사용자의 Intune 앱 PIN을 변경해야 할 때까지 최종 사용자가 대기할 수 있는 기간(일)을 구성할 수 있습니다. Azure Portal에서 **Intune** > **클라이언트 앱** > **앱 보호 정책** > **정책 만들기** > **설정** > **액세스 요구 사항**을 선택하여 새 설정을 사용할 수 있습니다. 이 기능은 iOS 및 Android 디바이스에서 사용할 수 있습니다. 이 설정은 양의 정수 값을 지원합니다.

### <a name="new-windows-10-update-settings----2626030-2512994---"></a>새 Windows 10 업데이트 설정 <!-- 2626030 2512994 -->
Windows 10 업데이트 링의 경우 다음을 수행할 수 있습니다.
- ‘2018년 10월 업데이트’를 실행 중인 컴퓨터의 Windows 10 컴퓨터에서 원래 자동 업데이트 설정 복원
- 사용자가 컴퓨터의 ‘설정’에서 업데이트 설치를 일시 중지하는 기능을 차단 또는 허용할 수 있는 새 소프트웨어 업데이트 설정 구성 



### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 메일 프로필은 S/MIME 서명 및 암호화를 사용할 수 있음 <!-- 2662949 -->
다양한 설정을 포함하는 메일 프로필을 만들 수 있습니다. 여기에는 iOS 디바이스에서 메일 통신 서명 및 암호화에 사용할 수 있는 S/MIME 설정이 포함됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **iOS** 선택 > **메일**(프로필 유형)).

[iOS 메일 구성 설정](email-settings-ios.md)에는 현재 설정이 나열됩니다.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>iOS DEP 디바이스에서 설정 도우미 화면 건너뛰기 <!-- 2687509 -->
현재 건너뛸 수 있는 화면 외에도 사용자가 디바이스를 등록할 때 설정 도우미에서 다음 화면을 건너뛰도록 iOS DEP 디바이스를 설정할 수 있습니다. 표시음, 개인 정보, Android 마이그레이션, 홈 단추, iMessage 및 FaceTime, 온보딩, 마이그레이션 보기, 모양, 화면 시간, 소프트웨어 업데이트, SIM 설치.
건너뛸 화면을 선택하려면 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰** > 토큰 선택 > **프로필** > 프로필 선택 > **속성** > **설정 도우미 사용자 지정** > 건너뛸 화면의 **숨기기** 선택 > **확인**으로 이동합니다.

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>일부 BitLocker 설정은 Windows 10 Pro Edition을 지원함 <!-- 2727036 -->
BitLocker를 포함하여 Windows 10 디바이스에서 Endpoint Protection 설정을 설정하는 구성 프로필을 만들 수 있습니다. 이를 통해 BitLocker 설정에 대한 Windows 10 Professional Edition 지원이 추가됩니다. 현재 Windows 10 에디션 설정을 보려면 [Windows 10용 Endpoint Protection 설정](endpoint-protection-windows-10.md#windows-encryption)을 참조하세요.
Intune은 Android 제조업체, 모델 및 보안 패치 버전을 비롯한 추가 디바이스 보고 필드와 iOS 모델을 제공합니다. Intune에서 이러한 필드를 사용하려면 **클라이언트 앱** > **앱 보호 상태**를 선택하고 **앱 보호 보고서: iOS, Android**를 선택합니다. 또한 이러한 매개 변수를 사용하여 디바이스 제조업체(Android)의 **허용** 목록, 디바이스 모델(Android 및 iOS)의 **허용** 목록 및 최소 Android 보안 패치 버전 설정을 구성할 수 있습니다. 

### <a name="intune-device-reporting-fields----2748738---"></a>Intune 디바이스 보고 필드 <!-- 2748738 -->
Intune은 Android 제조업체, 모델 및 보안 패치 버전을 비롯한 추가 디바이스 보고 필드와 iOS 모델을 제공합니다. Intune에서 이러한 필드를 사용하려면 **클라이언트 앱** > **앱 보호 상태**를 선택하고 **앱 보호 보고서: iOS, Android**를 선택합니다. 또한 이러한 매개 변수를 사용하여 디바이스 제조업체(Android)의 **허용** 목록, 디바이스 모델(Android 및 iOS)의 **허용** 목록 및 최소 Android 보안 패치 버전 설정을 구성할 수 있습니다. 

### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal----2809362---"></a>공유 디바이스 구성은 Azure Portal에서 iOS 디바이스의 잠금 화면 메시지로 이름이 바뀜 <!-- 2809362 -->
iOS 디바이스용 구성 프로필을 만들 경우 **공유 디바이스 구성** 설정에 추가하여 잠금 화면에 특정 텍스트를 표시할 수 있습니다. 여기에는 다음 변경 내용이 포함됩니다. 

- Azure Portal의 **공유 디바이스 구성** 설정은 “잠금 화면 메시지(감독 모드인 경우에만)”으로 이름이 바뀝니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **iOS** 선택 > 프로필 유형에서 **디바이스 기능** 선택 > **잠금 화면 메시지**).
- 잠금 화면 메시지를 추가하면 일련 번호, 디바이스 이름 또는 또 다른 디바이스별 값을 **자산 태그 정보**의 변수로 삽입할 수 있습니다. 예를 들어 중괄호를 사용하여 `Device name: {{device name}}` 또는 `Serial number is {{serial number}}`를 입력할 수 있습니다. [iOS 토큰](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)에는 사용할 수 있는 사용 가능한 토큰이 나열됩니다.

[잠금 화면에 메시지를 표시하기 위한 설정](shared-device-settings-ios.md)에는 현재 설정이 나열됩니다.

### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564--"></a>자세한 등록 제한 실패 메시징 <!-- 3111564-->
등록 제한 사항이 충족되지 않으면 더 자세한 오류 메시지가 제공됩니다. 이러한 메시지를 보려면 **Intune** > **문제 해결**로 이동하고 등록 실패 테이블을 확인합니다.

### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Android 엔터프라이즈 디바이스 소유자 디바이스의 새 알림, 힌트 및 Keyguard 설정 <!-- 3201839 3201843 -->
이 업데이트에는 디바이스 소유자로 실행할 경우 Android 엔터프라이즈 디바이스의 여러 가지 새로운 기능이 포함됩니다. 이러한 기능을 사용하려면 **디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Android 엔터프라이즈** 선택 > **프로필 유형**에서 **디바이스 소유자만** 선택 > **디바이스 제한 사항**으로 이동합니다.
새로운 기능은 다음과 같습니다. 
- 들어오는 호출, 시스템 경고, 시스템 오류 등을 포함하여 시스템 알림이 표시되지 않도록 설정
- 처음 열린 앱에 대한 시작 자습서 및 힌트 건너뛰기 제안
- 카메라, 알림, 지문 잠금 해제 등의 고급 Keyguard 설정 사용 안 함

현재 설정을 보려면 [Android 엔터프라이즈 디바이스 제한 사항 설정](device-restrictions-android-for-work.md)으로 이동합니다.

### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android 엔터프라이즈 디바이스 소유자 디바이스는 Always On VPN 연결을 사용할 수 있음 <!-- 3202194 -->
이 업데이트에서는 Android 엔터프라이즈 디바이스 소유자 디바이스에서 Always on VPN 연결을 사용할 수 있습니다. 상시 VPN 연결은 계속 연결된 상태로 유지되거나 사용자가 디바이스를 잠금 해제한 경우, 디바이스가 다시 시작된 경우 또는 무선 네트워크가 변경된 경우 바로 다시 연결됩니다. 또한 VPN 연결이 활성화될 때까지 모든 네트워크 트래픽을 차단하는 “잠금” 모드로 연결 상태를 전환할 수도 있습니다.
**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) > **디바이스 제한 사항**(디바이스 소유자만) > **연결** 설정에서 Always-on VPN을 사용하도록 설정할 수 있습니다. 현재 설정을 보려면 [Android 엔터프라이즈 디바이스 제한 사항 설정](device-restrictions-android-for-work.md)으로 이동합니다.

### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 디바이스의 작업 관리자에서 프로세스를 종료하는 새로운 설정 <!-- 3285177 --> 
이 업데이트에는 Windows 10 디바이스의 작업 관리자를 사용하여 프로세스를 종료하는 새로운 설정이 포함됩니다. 디바이스 구성 프로필(**디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Windows 10** 선택 > **프로필 유형**에서 **디바이스 제한 사항** 선택 > **일반** 설정)을 사용하여 이 설정을 허용하거나 차단하도록 선택합니다.
현재 설정을 보려면 [Windows 10 디바이스 제한 사항 설정](device-restrictions-windows-10.md)으로 이동합니다.
적용 대상: Windows 10 이상

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>관리 템플릿은 공개 미리 보기로 제공되고 자체 구성 프로필 로 이동됨 <!-- 3322847 -->
Intune의 관리 템플릿(**디바이스 구성** > **관리 템플릿**)은 현재 비공개 미리 보기로 제공됩니다. 이 업데이트 포함: 관리 템플릿에는 Intune에서 관리할 수 있는 약 300개 설정이 포함됩니다. 이전에는 이러한 설정이 그룹 정책 편집기에만 있었습니다.
관리 템플릿은 공개 미리 보기로 제공 됩니다. 관리 템플릿은 **디바이스 구성** > **관리 템플릿**에서 **디바이스 구성** > **프로필** >**프로필 만들기** > **플랫폼**에서 **Windows 10 이상** 선택, **프로필 유형**에서 **관리 템플릿** 선택으로 이동됩니다.
보고는 사용하도록 설정됩니다. 적용 대상: Windows 10 이상


<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Microsoft 권장 설정을 보안 기준과 함께 사용<!-- 2055484 -->
Intune은 Windows Defender ATP 및 Office 365 ATP를 비롯하여 보안에 중점을 둔 다른 서비스와 통합됩니다. 고객은 Microsoft 365 서비스에서 공통 전략 및 조화로운 종단 간 보안 워크플로 집합을 요청하고 있습니다. 우리의 목표는 보안 작업 및 공통 관리자 작업을 연결하는 솔루션을 빌드하기 위한 전략을 조정하는 것입니다. Intune에서는 Microsoft 권장 “보안 기준” 집합(**Intune** > **보안 기준**)을 게시하여 이 목표를 달성하고자 합니다.  관리자는 이러한 기준에서 직접 보안 정책을 만든 후 이를 사용자에게 배포할 수 있습니다. 또한 조직의 요구 사항을 충족하도록 최선의 권장 사항을 사용자 지정할 수도 있습니다. Intune은 디바이스가 이러한 기준을 계속 준수하는지 확인하고 준수하지 않는 디바이스나 사용자에 대해 관리자에게 알립니다.

### <a name="scope-tags-for-apps---1081941---"></a>앱의 범위 태그 <!--1081941 -->
범위 태그를 만들어 Intune 리소스에 대한 액세스를 제한할 수 있습니다. 역할 할당에 범위 태그를 추가한 다음, 범위 태그를 구성 프로필에 추가합니다. 역할은 일치하는 범위 태그가 있거나 범위 태그가 없는 구성 프로필이 있는 리소스에만 액세스할 수 있습니다.
범위 태그를 만들려면 **Intune 역할** > **범위(태그)** > **만들기**를 선택합니다.
역할 할당에 범위 태그를 추가하려면 **Intune 역할** > **모든 역할** > **정책 및 프로필 관리자** > **할당** > **범위(태그)** 를 차례로 선택합니다.
범위 태그를 구성 프로필에 추가하려면 **장치 구성** > **프로필** > 프로필 선택 > **속성** > **범위(태그)** 를 차례로 선택합니다.

### <a name="tenant-health-dashboard----1124854---"></a>테넌트 상태 대시보드 <!-- 1124854 -->
Intune의 테넌트 상태 페이지는 단일 위치에서 테넌트 상태 정보를 제공합니다. 페이지는 4개 섹션으로 구분됩니다.  
- **테넌트 세부 정보**: MDM 권한, 테넌트에 등록된 총 디바이스 수, 라이선스 수와 같은 정보를 포함합니다. 이 섹션은 테넌트에 대한 최신 서비스 릴리스도 제공합니다.
- **커넥터 상태**: Apple VPP, 비즈니스용 Microsoft Store, 인증서 커넥터와 같은 구성된 커넥터에 대한 정보를 포함합니다. 현재 상태에 따라 커넥터는 ‘정상’, ‘경고’ 또는 ‘비정상’으로 플래그 지정됩니다.
- **Intune Service Health**: 테넌트에 대해 활성 인시던트 또는 중단 상태가 포함됩니다. 이 섹션의 정보는 Office Message Center([https://portal.office.com](https://portal.office.com))에서 직접 검색됩니다.
- **Intune 뉴스**: 테넌트가 최신 Intune 기능을 수신했다는 알림과 같은 항목을 포함한 테넌트에 대한 활성 메시지가 포함됩니다. 이 섹션의 정보는 Office Message Center([https://portal.office.com](https://portal.office.com))에서 직접 검색됩니다.


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>사용자 등록 없이 배포된 WIP 정책 <!-- 1434452 -->
WIP(Windows Information Protection) 정책은 MDM 사용자가 Windows 10 디바이스를 등록하지 않고 배포할 수 있습니다. 이 구성을 사용하면 회사는 WIP 구성을 기반으로 회사 문서를 보호할 수 있는 한편 사용자는 자신의 Windows 디바이스를 관리할 수 있습니다. 문서가 WIP 정책으로 보호되면 Intune 관리자는 보호되는 데이터를 선택적으로 초기화할 수 있습니다. 사용자 및 디바이스를 선택하고 초기화 요청을 보내면 WIP 정책을 통해 보호된 모든 데이터를 사용할 수 없게 됩니다. Azure Portal의 Intune에서 **모바일 앱** > **앱 선택적 초기화**를 선택합니다.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>웹 데이터에 대한 APP(앱 보호 정책) 설정 <!-- 2662995 -->
Android 및 iOS 디바이스의 웹 콘텐츠에 대한 APP 정책 설정은 iOS 유니버설 링크 및 Android 앱 링크를 통한 데이터 전송을 비롯하여 http 및 https 웹 링크를 모두 더 잘 처리하기 위해 업데이트됩니다.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>다른 MDM에서 사용하는 Apple VPP 토큰 <!-- 1488946 -->
Intune과 다른 MDM에서 모두 Apple VPP(대량 구매 프로그램) 토큰을 사용하고 있으면 Intune에서 세부 정보를 검색하고 표시합니다.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>디바이스 준수 대시보드에 사용 중지된 디바이스가 있음 <!-- 1981119 -->
향후 업데이트에서는 사용 중지된 디바이스가 디바이스 준수 대시보드에서 제거됩니다. 이에 따라 규정 준수 번호도 변경됩니다.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>온-프레미스 커넥터에 대한 업데이트 프로세스 변경 <!-- 2277554 -->
고객의 의견에 따라 온-프레미스 커넥터가 업데이트되는 방식이 변경됩니다. 온-프레미스 커넥터를 처음 설치하면 업데이트가 자동으로 수행됩니다. 이 변경은 Microsoft Intune용 새 PFX 인증서 커넥터를 사용하여 시작되며 이후에는 다른 유형의 온-프레미스 커넥터로 롤아웃됩니다. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Configuration Manager 준수 확인 <!-- 2192052 -->
향후 업데이트에는 새 System Center Configuration Manager 준수 설정이 포함됩니다(**디바이스 준수** > **정책** > **정책 만들기** > **Windows 10**). Configuration Manager는 Intune 준수에 신호를 보냅니다. Intune 설정을 사용하여 모든 Configuration Manager 신호에 “준수”를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 디바이스에 설치해야 합니다. Configuration Manager에서 이 요구 사항의 상태는 “설치됨”입니다. 디바이스의 프로그램이 알 수 없는 상태에 있는 경우 디바이스는 Intune에서 비준수가 됩니다.

적용 대상: Windows 10 이상



## <a name="notices"></a>알림

이번에는 활성 알림이 없습니다.

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.



