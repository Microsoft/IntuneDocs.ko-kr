---
title: Intune 앱 SDK의 이점
titlesuffix: Microsoft Intune
description: Intune 앱 SDK는 iOS 및 Android 플랫폼 둘 다에 사용할 수 있으며 Microsoft Intune을 통해 모바일 앱 관리 기능을 사용할 수 있게 합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 55df1b152ee32456d577afacedd034583e591e3e
ms.sourcegitcommit: d047a692c798e1fb61ee43a487d6332bce344610
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44058723"
---
# <a name="intune-app-sdk-overview"></a>Intune 앱 SDK 개요
iOS와 Android 둘 다에 사용할 수 있는 Intune 앱 SDK를 통해 앱을 앱 보호 정책에 사용할 수 있도록 설정할 수 있습니다. Intune 앱 SDK는 앱 개발자에게서 필요한 코드 변경의 양을 최소화하려고 합니다. 앱의 동작을 변경하지 않고 대부분의 SDK 기능을 사용하도록 설정할 수 있습니다. 최종 사용자 및 IT 관리자 환경을 개선하기 위해 API를 활용하여 앱 참여를 요구하는 기능에 대한 앱 동작을 사용자 지정할 수 있습니다.

앱을 앱 보호 정책에 사용할 수 있도록 설정한 후 IT 관리자는 앱 내에서 회사 데이터를 보호하기 위해 이러한 정책을 배포할 수 있습니다.

## <a name="app-protection-features"></a>앱 보호 기능

다음은 SDK와 함께 사용할 수 있는 Intune 앱 보호 기능의 예입니다.

### <a name="control-users-ability-to-move-corporate-files"></a>회사 파일을 이동할 수 있는 사용자의 기능을 제어합니다.
IT 관리자가 앱의 회사 또는 학교 데이터를 이동할 수 있는 위치를 제어할 수 있습니다. 예를 들어 앱에서 회사 데이터를 클라우드로 백업할 수 없도록 하는 정책을 배포할 수 있습니다.

### <a name="configure-clipboard-restrictions"></a>클립보드 제한 구성
IT 관리자는 Intune 관리 앱의 클립보드 동작을 구성할 수 있습니다. 예를 들어 최종 사용자가 앱에서 데이터를 잘라내거나 복사하여 관리되지 않는, 개인 앱에 붙여넣는 것을 방지하는 정책을 배포할 수 있습니다.

### <a name="enforce-encryption-on-saved-data"></a>저장된 데이터에 암호화 적용
IT 관리자는 앱에서 장치에 저장하는 데이터가 암호화되도록 하는 정책을 적용할 수 있습니다.

### <a name="remotely-wipe-corporate-data"></a>원격으로 회사 데이터 초기화
IT 관리자는 Intune 관리 앱에서 회사 데이터를 원격으로 초기화할 수 있습니다. 이 기능은 ID 기반이며 최종 사용자의 회사 ID와 연결된 파일만 삭제합니다. 이렇게 하려면 기능에 앱 참여가 필요합니다. 앱은 사용자 설정에 따라 초기화를 수행할 ID를 지정할 수 있습니다. 앱에서 지정된 이러한 사용자 설정이 없을 경우 기본 동작은 응용 프로그램 디렉터리를 초기화하고 최종 사용자에게 액세스가 제거되었음을 알리는 것입니다.

### <a name="enforce-the-use-of-a-managed-browser"></a>Managed Browser 사용 적용
IT 관리자가 앱의 웹 링크를 [Intune Managed Browser 앱](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)에서 열도록 강제할 수 있습니다. 이 기능은 회사 환경에 표시되는 링크가 Intune 관리 앱의 도메인 내에 유지되게 합니다.

### <a name="enforce-a-pin-policy"></a>PIN 정책 적용
IT 관리자가 앱의 회사 데이터에 액세스하기 전에 PIN을 입력하도록 최종 사용자에게 요구할 수 있습니다. 이렇게 하면 앱을 사용하는 사용자가 회사 또는 학교 계정으로 처음 로그인한 사용자와 동일하도록 보장됩니다. 최종 사용자가 해당 PIN을 구성할 때 Intune 앱 SDK는 Azure Active Directory를 사용하여 등록된 Intune 계정과 최종 사용자의 자격 증명을 비교하여 확인합니다.

### <a name="require-users-to-sign-in-with-work-or-school-account-for-app-access"></a>앱 액세스를 위해 회사 또는 학교 계정으로 로그인하도록 요구
IT 관리자가 앱에 액세스하려면 회사 또는 학교 계정으로 로그인하도록 사용자에게 요구할 수 있습니다. Intune 앱 SDK는 Azure Active Directory를 사용하여 입력된 자격 증명이 후속 로그인에 다시 사용되는 Single Sign-On 환경을 제공합니다. Azure Active Directory와 페더레이션된 ID 관리 솔루션의 인증도 지원됩니다.

### <a name="check-device-health-and-compliance"></a>장치 상태 및 규정 준수 확인
IT 관리자가 최종 사용자가 앱에 액세스하기 전에 장치 상태 및 Intune 정책 준수를 확인할 수 있습니다. iOS에서 이 정책은 장치가 무단 해제되었는지 여부를 확인합니다. Android에서 이 정책은 장치가 루팅되었는지 여부를 확인합니다.

### <a name="multi-identity-support"></a>다중 ID 지원
다중 ID 지원은 단일 앱에서 정책 관리(회사) 계정과 관리되지 않는(개인) 계정을 동시에 사용할 수 있도록 지원하는 SDK의 기능입니다.

예를 들어 많은 사용자가 iOS 및 Android용 Office 모바일 앱에서 회사 및 개인 메일 계정을 둘 다 구성합니다. 사용자가 회사 계정으로 데이터에 액세스할 때 IT 관리자가 앱 보호 정책이 적용될 것임을 확신할 수 있어야 합니다. 그러나 사용자가 개인 메일 계정에 액세스할 때는 해당 데이터가 IT 관리자의 제어를 벗어나야 합니다. Intune 앱 SDK는 앱 보호 정책의 대상을 **오직** 앱의 회사 ID로만 지정하여 이 작업을 수행합니다.

다중 ID 기능은 조직이 개인 및 회사 계정을 둘 다 지원하는 스토어 앱에서 발생하는 데이터 보호 문제를 해결하는 데 도움이 됩니다.
 
### <a name="app-protection-without-device-enrollment"></a>장치 등록이 제외된 앱 보호

>[!IMPORTANT]
>장치 등록이 제외된 Intune 앱 보호는 Intune 앱 래핑 도구, Android용 Intune 앱 SDK, iOS용 Intune 앱 SDK, Intune App SDK Xamarin 바인딩에서 사용할 수 있습니다.

개인 장치가 있는 많은 사용자는 MDM(모바일 장치 관리) 공급자에 개인 장치를 등록하지 않고 회사 데이터에 액세스하여 사용할 수 있기를 원합니다. MDM 등록 시 장치에 대한 전역 제어를 요구하므로 사용자는 대개 개인 장치에 대한 제어를 회사에 부여하는 것을 주저합니다.

장치 등록이 제외된 앱 보호를 사용하면 Microsoft Intune 서비스가 장치 관리 채널을 통해 정책을 배포하지 않고 직접 앱 보호 정책을 앱에 배포할 수 있습니다.

### <a name="on-demand-application-vpn-connections-with-citrix-mvpn"></a>Citrix mVPN을 통한 주문형 응용 프로그램 VPN 
Citrix XenMobile MDX와 Microsoft Intune의 조합으로 장치와 앱을 관리할 수 있습니다. 이 조합은 Citrix의 mVPN 기술을 사용하는 동안 Intune 앱 보호 정책으로 앱을 관리할 수 있음을 의미합니다. Citrix와의 통합은 iOS 및 Android용 Intune 앱 SDK, iOS 및 Android용 Intune 앱 Wrapping Tool(-citrix flag 포함)을 사용할 수 있습니다.
 
Citrix MDX에 대한 자세한 내용은 [MDX Toolkit 정보](http://docs.citrix.com/en-us/mdx-toolkit/10/about-mdx-toolkit.html), [iOS용 Citrix MDX 앱 래퍼](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) 및 [Android용 Citrix MDX 앱 래퍼](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-android.html)를 참조하세요.
