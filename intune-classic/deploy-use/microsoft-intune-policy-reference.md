---
title: 구성 정책 참조
description: 장치를 관리하는 데 사용해야 하는 Microsoft Intune 정책을 결정할 수 있도록 이 항목의 정보를 사용합니다.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d27f2739-9791-4aae-a9db-01a4e59ccfe5
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 46bc3408f861bcd249ca5071abf1ee80733af10d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31030529"
---
# <a name="microsoft-intune-configuration-policy-reference"></a>Microsoft Intune 구성 정책 참조

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

장치를 관리하는 데 사용해야 하는 Microsoft Intune 구성 정책을 결정할 수 있도록 이 항목의 정보를 사용합니다.

> [!TIP]
> 정책을 사용하는 방법에 대한 자세한 내용은 [Microsoft Intune 정책을 사용하여 장치의 설정 및 기능 관리](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) 항목을 참조하세요.


## <a name="android-configuration-policies"></a>Android 구성 정책

|정책 이름|다음을 수행하려는 경우에 사용|
|---------------|------------------------|
|**사용자 지정 구성(Android 4 이상, Samsung KNOX Standard 4.0 이상)**<br><br>**사용자 지정 구성(Android for Work)**|장치 기능을 제어하는 데 사용할 수 있는 Wi-Fi 설정과 같은 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 배포합니다. 필요한 설정을 구성 정책에서 사용할 수 없는 경우에 유용합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Android 정책 설정](android-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**메일 프로필(Samsung KNOX Standard 4.0 이상)**<br><br>**메일 프로필(Android for Work - Gmail)**<br><br>**메일 프로필(Android for Work - Nine Work)**|관리 장치에서 Exchange ActiveSync 메일 설정을 만들고 배포하고 모니터링합니다. 그러면 사용자가 설정할 필요 없이 개인 장치에서 회사 메일에 액세스할 수 있습니다.<br /><br />자세한 내용은 [Microsoft Intune에서 메일 프로필을 사용하여 회사 메일에 대한 액세스 구성](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)을 참조하세요.|
|**일반 구성(Android 4 이상, Samsung KNOX Standard 4.0 이상)**<br><br>**일반 구성(Android for Work)**|모바일 장치 보안 및 기능 설정을 구성합니다.<br />호환 또는 호환되지 않는 앱을 지정하고 사용되는 경우를 보고합니다.<br />장치를 잠가 특정 기능만 작동하도록 하는(예: 장치에서 하나의 앱만 실행되도록 하거나 볼륨 단추를 사용할 수 없도록 설정함) 키오스크 모드를 구성합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Android 정책 설정](android-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**PKCS #12(.PFX) 인증서 프로필(Android 4 이상)**<br><br>**PKCS #12(.PFX) 인증서 프로필(Android for Work)**|장치 인증서 요청용으로 .PFX 설정을 만들어 배포하려면 이 프로필을 사용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**SCEP 인증서 프로필(Android 4 이상)**<br><br>**SCEP 인증서 프로필(Android for Work)**|모바일 장치 인증에 사용하는 신뢰할 수 있는 모바일 장치 인증서와 함께 사용할 수 있는 단순 인증서 등록 프로토콜 인증서를 구성하여 Wi-Fi 및 VPN 프로필을 통해 구성된 네트워크 리소스에 대한 액세스를 허용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**신뢰할 수 있는 인증서 프로필(Android 4 이상)**<br><br>**신뢰할 수 있는 인증서 프로필(Android for Work)**|모바일 장치 인증에 사용할 수 있는 신뢰할 수 있는 모바일 장치 인증서를 구성하여 Wi-Fi 및 VPN 프로필을 통해 구성된 네트워크 리소스에 대한 액세스를 허용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**VPN 프로필(Android 4 이상)**<br><br>**VPN 프로필(Android for Work)**|사용자가 모바일 장치에서 회사 네트워크에 안전하게 액세스할 수 있도록 해주는 설정을 구성하고 배포합니다. 이러한 설정을 배포하여 최종 사용자의 작업에 대한 연결을 간소화합니다.<br /><br />자세한 내용은 [Microsoft Intune.md에서 VPN 연결](vpn-connections-in-microsoft-intune.md)를 참조하세요.|
|**Wi-Fi 프로필(Android 4 이상)**<br><br>**Wi-Fi 프로필(Android for Work)**|무선 네트워크 설정을 구성하고 조직의 사용자에게 배포합니다. 이러한 설정을 배포하여 최종 사용자의 무선 네트워크에 대한 연결을 간소화합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 Wi-Fi 연결](wi-fi-connections-in-microsoft-intune.md)를 참조하세요.|
|**모바일 앱 구성 정책(Android for Work)**|모바일 앱 구성 정책을 사용하여 사용자가 Android for Work 앱을 실행할 때 필요할 수 있는 설정을 자동으로 제공할 수 있습니다.<br /><br />자세한 내용은 [Microsoft Intune에서 모바일 앱 구성 정책을 사용하여 Android for Work 앱 구성](afw-app-configuration-policy.md)을 참조하세요.

## <a name="ios-configuration-policies"></a>iOS 구성 정책

|정책 이름|다음을 수행하려는 경우에 사용|
|---------------|------------------------|
|**사용자 지정 구성(iOS 8.0 이상)**|Apple Configurator를 사용하여 만든 구성 프로필을 iOS 장치에 배포합니다. 필요한 설정을 구성 정책에서 사용할 수 없는 경우에 유용합니다.<br /><br />자세한 내용은 [Microsoft Intune의 iOS 정책 설정](ios-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**메일 프로필(iOS 8.0 이상)**|관리 장치에서 Exchange ActiveSync 메일 설정을 만들고 배포하고 모니터링합니다. 그러면 사용자가 설정할 필요 없이 개인 장치에서 회사 메일에 액세스할 수 있습니다.<br /><br />자세한 내용은 [Microsoft Intune에서 메일 프로필을 사용하여 회사 메일에 대한 액세스 구성](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)을 참조하세요.|
|**일반 구성(iOS 8.0 이상)**|모바일 장치 보안 및 기능 설정을 구성합니다.<br />호환 또는 호환되지 않는 앱을 지정하고 사용되는 경우를 보고합니다.<br />장치를 잠가 특정 기능만 작동하도록 하는(예: 장치에서 하나의 앱만 실행되도록 하거나 볼륨 단추를 사용할 수 없도록 설정함) 키오스크 모드를 구성합니다.<br /><br />자세한 내용은 [Microsoft Intune의 iOS 정책 설정](ios-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**모바일 앱 구성 정책(iOS 8.0 이상)**|모바일 앱 구성 정책을 사용하여 사용자가 iOS 앱을 실행할 때 필요할 수 있는 설정을 자동으로 제공할 수 있습니다.<br /><br />자세한 내용은 [Microsoft Intune에서 모바일 앱 구성 정책을 사용하여 iOS 앱 구성](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)을 참조하세요.|
|**모바일 프로비전 프로필 정책(iOS 8.0 이상)**|Apple iOS 기간 업무 모바일 앱은 인증서에 포함되고 인증서로 코드 서명된 프로비전 프로필을 통해 빌드됩니다. 앱이 iOS 장치에서 실행되면 iOS는 iOS 앱의 무결성을 확인하고 프로비전 프로필에서 정의하는 정책을 적용합니다.<br><br>일반적으로 앱에 서명하기 위해 사용하는 엔터프라이즈 서명 인증서는 3년 동안 유지됩니다. 그러나 프로비전 프로필은 1년 후에 만료됩니다. 이 정책을 사용하면 인증서가 여전히 유효한 동안 만료일이 다가오는 앱이 있는 장치에 새 프로비전 프로필 정책을 미리 배포할 수 있습니다.<br><br>자세한 내용은 [iOS 프로비전 프로필 정책을 사용하여 모바일 앱이 만료되지 않도록 방지](ios-mobile-app-provisioning-profiles.md)를 참조하세요.|
|**PKCS #12(.PFX) 인증서 프로필(iOS 8.0 이상)**|장치 인증서 요청용으로 .PFX 설정을 만들어 배포하려면 이 프로필을 사용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**SCEP 인증서 프로필(iOS 8.0 이상)**|모바일 장치 인증에 사용하는 신뢰할 수 있는 모바일 장치 인증서와 함께 사용할 수 있는 단순 인증서 등록 프로토콜 인증서를 구성하여 Wi-Fi 및 VPN 프로필을 통해 구성된 네트워크 리소스에 대한 액세스를 허용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**신뢰할 수 있는 인증서 프로필(iOS 8.0 이상)**|모바일 장치 인증에 사용할 수 있는 신뢰할 수 있는 모바일 장치 인증서를 구성하여 Wi-Fi 및 VPN 프로필을 통해 구성된 네트워크 리소스에 대한 액세스를 허용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**VPN 프로필(iOS 8.0 이상)**|사용자가 모바일 장치에서 회사 네트워크에 안전하게 액세스할 수 있게 해주는 설정을 구성하고 배포합니다. 이러한 설정을 배포하여 최종 사용자의 작업에 대한 연결을 간소화합니다.<br /><br />자세한 내용은 [Microsoft Intune.md에서 VPN 연결](vpn-connections-in-microsoft-intune.md)를 참조하세요.|
|**Wi-Fi 프로필(iOS 8.0 이상)**|무선 네트워크 설정을 구성하고 조직의 사용자에게 배포합니다. 이러한 설정을 배포하여 최종 사용자의 무선 네트워크에 대한 연결을 간소화합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 Wi-Fi 연결](wi-fi-connections-in-microsoft-intune.md)를 참조하세요.|


## <a name="mac-os-x-configuration-policies"></a>Mac OS X 구성 정책

|정책 이름|다음을 수행하려는 경우에 사용|
|---------------|------------------------|
|**사용자 지정 구성(Mac OS X 10.9 이상)**|Apple Configurator를 사용하여 만든 구성 프로필을 Mac 컴퓨터에 배포합니다. 필요한 설정을 구성 정책에서 사용할 수 없는 경우에 유용합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Mac OS X 정책 설정](mac-os-x-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**일반 구성(Mac OS X 10.9 이상)**|모바일 장치 보안 및 기능 설정을 구성합니다.<br />호환 또는 호환되지 않는 앱을 지정하고 사용되는 경우를 보고합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Mac OS X 정책 설정](mac-os-x-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**SCEP 인증서 프로필(Mac OS X 10.9 이상)**|모바일 장치 인증에 사용하는 신뢰할 수 있는 모바일 장치 인증서와 함께 사용할 수 있는 단순 인증서 등록 프로토콜 인증서를 구성하여 Wi-Fi 및 VPN 프로필을 통해 구성된 네트워크 리소스에 대한 액세스를 허용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**신뢰할 수 있는 인증서 프로필(Mac OS X 10.9 이상)**|모바일 장치 인증에 사용할 수 있는 신뢰할 수 있는 모바일 장치 인증서를 구성하여 Wi-Fi 및 VPN 프로필을 통해 구성된 네트워크 리소스에 대한 액세스를 허용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**VPN 프로필(Mac OS X 10.9 이상)**|사용자가 모바일 장치에서 회사 네트워크에 안전하게 액세스할 수 있게 해주는 설정을 구성하고 배포합니다. 이러한 설정을 배포하여 최종 사용자의 작업에 대한 연결을 간소화합니다.<br /><br />자세한 내용은 [Microsoft Intune.md에서 VPN 연결](vpn-connections-in-microsoft-intune.md)를 참조하세요.|
|**Wi-Fi 프로필(Mac OS X 10.9 이상)**|무선 네트워크 설정을 구성하고 조직의 사용자에게 배포합니다. 이러한 설정을 배포하여 최종 사용자의 무선 네트워크에 대한 연결을 간소화합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 Wi-Fi 연결](wi-fi-connections-in-microsoft-intune.md)를 참조하세요.|

## <a name="windows-configuration-policies"></a>Windows 구성 정책
Windows Phone 및 등록된 Windows 장치에만 적용됩니다.

|정책 이름|다음을 수행하려는 경우에 사용|
|---------------|------------------------|
|**사용자 지정 구성(Windows 10 Desktop 및 Mobile 이상)**|장치 기능을 제어하는데 사용할 수 있는 OMA-URI 설정을 배포합니다. 필요한 설정을 구성 정책에서 사용할 수 없는 경우에 유용합니다.<br />    자세한 내용은 [Microsoft Intune의 Windows 10 정책 설정](windows-10-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**사용자 지정 구성(Windows Phone 8.1 이상)**|장치 기능을 제어하는데 사용할 수 있는 OMA-URI 설정을 배포합니다. 필요한 설정을 구성 정책에서 사용할 수 없는 경우에 유용합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Windows Phone 8.1 설정](windows-phone-8-1-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**버전 업그레이드 정책(Windows 10 Desktop 이상)**<br><br>**버전 업그레이드 정책(Windows 10 Holographic 이상)**<br><br>**버전 업그레이드 정책(Windows 10 Mobile 이상)**|Windows 10 장치를 최신 버전으로 업데이트하는 데 사용되는 라이선스 또는 제품 키 정보가 포함된 정책을 구성하고 배포합니다.<br><br>자세한 내용은 [Microsoft Intune의 버전 업그레이드 정책 설정](edition-upgrade-policy-settings-in-microsoft-intune.md)을 참조하세요.|  
|**메일 프로필(Windows Phone 8.1 이상)**<br /><br />**메일 프로필(Windows 10 Desktop 및 Mobile 이상)**|관리 장치에서 Exchange ActiveSync 메일 설정을 만들고 배포하고 모니터링합니다. 그러면 사용자가 설정할 필요 없이 개인 장치에서 회사 메일에 액세스할 수 있습니다.<br /><br />자세한 내용은 [Microsoft Intune에서 메일 프로필을 사용하여 회사 메일에 대한 액세스 구성](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)을 참조하세요.|
|**일반 구성(Windows 10 Desktop 및 Mobile 이상)**|등록된 Windows 10 Desktop 및 Mobile 장치에 대한 모바일 장치 보안 및 기능 설정을 구성합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Windows 10 정책 설정](windows-10-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**일반 구성(Windows 10 Team 이상)**|등록된 Windows 10 Team 장치(예: Surface Hub 장치)에 대한 장치 보안 및 기능 설정을 구성합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Windows 팀 구성 정책 설정](windows-team-configuration-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**일반 구성(Windows 8.1 이상)**|모바일 장치 보안 및 등록된 Windows 장치의 기능 설정을 구성합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Windows 정책 설정](windows-configuration-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**일반 구성(Windows Phone 8.1 이상)**|모바일 장치 보안 및 기능 설정을 구성합니다.<br />사용자가 사용할 수 있거나 사용할 수 없는 앱을 지정하고, 비규격 앱을 설치하거나 사용하지 못하도록 합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Windows Phone 8.1 설정](windows-phone-8-1-policy-settings-in-microsoft-intune.md)을 참조하세요.|
|**PKCS #12(.PFX) 인증서 프로필(Windows 10 Desktop 및 Mobile 이상)**|장치 인증서 요청용으로 .PFX 설정을 만들어 배포하려면 이 프로필을 사용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**SCEP 인증서 프로필(Windows 8.1 이상)**<br /><br />**SCEP 인증서 프로필(Windows Phone 8.1 이상)**|모바일 장치 인증에 사용하는 신뢰할 수 있는 모바일 장치 인증서와 함께 사용할 수 있는 단순 인증서 등록 프로토콜 인증서를 구성하여 Wi-Fi 및 VPN 프로필을 통해 구성된 네트워크 리소스에 대한 액세스를 허용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**신뢰할 수 있는 인증서 프로필(Windows 8.1 이상)**<br /><br />**신뢰할 수 있는 인증서 프로필(Windows Phone 8.1 이상)**|모바일 장치 인증에 사용할 수 있는 신뢰할 수 있는 모바일 장치 인증서를 구성하여 Wi-Fi 및 VPN 프로필을 통해 구성된 네트워크 리소스에 대한 액세스를 허용합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.|
|**VPN 프로필(Windows 10 Desktop 및 Mobile 이상)**<br /><br />**VPN 프로필(Windows 8.1 이상)**<br /><br />**VPN 프로필(Windows Phone 8.1 이상)**|사용자가 모바일 장치에서 회사 네트워크에 안전하게 액세스할 수 있게 해주는 설정을 구성하고 배포합니다. 이러한 설정을 배포하여 최종 사용자의 작업에 대한 연결을 간소화합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 VPN 연결](vpn-connections-in-microsoft-intune.md)을 참조하세요.|
|**Wi-Fi 가져오기**|이전에 파일로 내보낸 Windows Wi-Fi 구성을 가져와서 배포합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 Wi-Fi 연결](wi-fi-connections-in-microsoft-intune.md)를 참조하세요.|
|**Windows Information Protection**<br>(이전의 엔터프라이즈 데이터 보호)|기업에서 직원 소유 장치가 증가됨에 따라 메일, 소셜 미디어, 공용 클라우드 등의 앱 및 서비스를 통해 실수에 의한 데이터 유출의 위험도 증가하며, 이러한 상황은 기업에서 제어할 수 없습니다. 예를 들어 직원이 개인 메일 계정에서 최신 엔지니어링 사진을 전송하거나, 제품 정보를 복사한 후 트윗에 붙여넣거나, 진행 중인 판매 보고서를 공용 클라우드 저장소에 저장합니다.<br><br>Windows 정보 보호는 직원 환경을 방해하지 않으면서 이러한 잠재적인 데이터 유출로부터 보호하는 데 도움이 됩니다. 또한 작업 환경이나 기타 앱을 변경하지 않고도 엔터프라이즈 앱 및 데이터가 회사 소유 장치 및 직원이 회사에 가져오는 개인 장치에서 실수로 누출되지 않도록 보호하는 데도 유용합니다.<br><br>이 Intune 정책은 Windows Information Protection, 엔터프라이즈 네트워크 위치, 보호 수준 및 암호화 설정으로 보호되는 앱 목록을 관리합니다.<br><br>자세한 내용은 [Windows 정보 보호를 사용하여 엔터프라이즈 데이터 보호](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp)를 참조하세요.|


## <a name="software-policies"></a>소프트웨어 정책

|정책 이름|다음을 수행하려는 경우에 사용|
|---------------|------------------------|
|**관리되는 브라우저 정책(Android 4 이상)**<br /><br />**Managed Browser 정책(iOS 8.0 이상)**|사용자가 관리되는 브라우저 앱을 사용할 때 액세스할 수 있는 웹 사이트 및 액세스할 수 없는 웹 사이트를 지정합니다.<br /><br />자세한 내용은 [Microsoft Intune에서 Managed Browser 정책을 사용하여 인터넷 액세스 관리](manage-internet-access-using-managed-browser-policies.md)를 참조하세요.|
|**모바일 응용 프로그램 관리(Android 4 이상)**<br /><br />**모바일 응용 프로그램 관리 정책(iOS 8.0 이상)**|회사 규정 준수 및 보안 정책에 맞도록 배포하는 앱의 기능을 수정합니다. 예를 들어 제한된 앱 내에서의 잘라내기, 복사 및 붙여넣기 작업을 제한하거나, 관리되는 브라우저 내에서 모든 웹 링크를 열도록 앱을 구성할 수 있습니다.<br /><br />자세한 내용은 [Microsoft Intune 콘솔에서 모바일 응용 프로그램 관리 정책 구성 및 배포](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)를 참조하세요.|

## <a name="common-mobile-device-settings"></a>공용 모바일 장치 설정

|                  정책 이름                   |                                                                                                                       다음을 수행하려는 경우에 사용                                                                                                                       |
|------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <strong>Exchange ActiveSync 정책</strong>   | 모바일 장치 보안 및 Exchange ActiveSync에서 관리되는 장치에 대한 기능 설정을 구성합니다.<br /><br />자세한 내용은 [Microsoft Intune의 Exchange ActiveSync 정책 설정](exchange-activesync-policy-settings-in-microsoft-intune.md)을 참조하세요. |
| <strong>모바일 장치 보안 정책</strong> |                                  <ul><li>다음을 포함한 모바일 장치(모든 플랫폼)에 대한 설정을 구성합니다.<br /><br /><ul><li>보안</li><li>암호화</li><li>시스템</li><li>메일</li><li>응용 프로그램</li></ul></li></ul>                                  |

> [!IMPORTANT]
> 이제 Microsoft Intune에서는 각 장치 플랫폼에 대해 개별 **구성 정책**을 사용하며 이러한 정책에는 사용할 수 있는 최신 설정이 포함되어 있습니다. 모바일 장치 보안 정책을 계속해서 사용할 수 있으며 기존 배포가 계속 작동하지만, 새 구성 정책으로 최대한 빨리 마이그레이션하는 계획을 세워야 합니다.<br />자세한 내용은 [Microsoft Intune의 모바일 장치 보안 정책 설정](mobile-device-security-policy-settings-in-microsoft-intune.md)을 참조하세요.

## <a name="policies-for-windows-pcs-managed-by-the-intune-software-client"></a>Intune 소프트웨어 클라이언트를 통해 관리하는 Windows PC용 정책

|정책 이름|다음을 수행하려는 경우에 사용|
|---------------|------------------------|
|**Microsoft Intune 에이전트 설정**|다음에 대한 설정을 포함하여 컴퓨터에서 Intune PC 클라이언트를 구성합니다.<br /><br />-   Endpoint Protection<br />-   소프트웨어 업데이트<br />-   정책 확인 일정<br /><br />이 유형의 정책은 장치 그룹에만 배포할 수 있습니다.<br /><br />Intune 클라이언트는 **업데이트 및 응용 프로그램 검색 주기** 설정(기본값은 8시간으로 설정)에 따라 새로운 정책 및 업데이트된 정책을 다운로드합니다. 그러나 언제든지 컴퓨터에서 정책을 강제로 새로 고칠 수 있습니다.<br /><br />자세한 내용은 [Microsoft Intune에서 소프트웨어 업데이트를 사용하여 Windows PC를 최신 상태로 유지](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) 항목을 참조하세요.|
|**Microsoft Intune Center 설정**|관리되는 컴퓨터의 Microsoft Intune 센터에 표시되는 세부 정보를 구성합니다.<br /><br />이 유형의 정책은 장치 그룹에만 배포할 수 있습니다.<br /><br />자세한 내용은 [Microsoft Intune 컴퓨터 클라이언트를 사용한 일반 Windows PC 관리 작업](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) 항목을 참조하세요.|
|**Windows 방화벽 설정**|컴퓨터에서 다음을 포함한 공용 네트워크 통신에 대해 Windows 방화벽 정책 및 예외를 구성합니다.<br /><br />-   BranchCache<br />-   원격 지원<br />-   미디어 공유<br /><br />이 유형의 정책은 장치 그룹에만 배포할 수 있습니다.<br /><br />자세한 내용은 [Microsoft Intune용 Endpoint Protection을 사용한 Windows PC의 보안 유지 방법](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) 항목을 참조하세요.|

### <a name="see-also"></a>참고 항목

[Microsoft Intune 정책을 사용하여 장치의 설정 및 기능 관리](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
