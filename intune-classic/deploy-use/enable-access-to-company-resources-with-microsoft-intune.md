---
title: 회사 리소스에 대한 액세스 허용
description: Wi-Fi, VPN 및 전자 메일 프로필은 함께 작동하여 사용자에게 필요한 파일 및 리소스에 쉽게 액세스할 수 있게 해줍니다.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5bfc02f5f10ce88b992d0ea250d7b36fdf3f66dc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31017311"
---
# <a name="enable-access-to-company-resources-with-microsoft-intune"></a>Microsoft Intune을 사용하여 회사 리소스에 대한 액세스 허용

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune Wi-Fi, VPN 및 전자 메일 프로필은 함께 작동하여 사용자가 어디에 있든지 상관없이 정상적인 작업 수행에 필요한 파일 및 리소스에 쉽게 액세스하게 해 줍니다. 인증서 프로필은 해당 액세스를 보호하도록 도움을 줍니다.

## <a name="wi-fi-profileswi-fi-connections-in-microsoft-intunemd-and-supported-platforms"></a>[Wi-Fi 프로필](wi-fi-connections-in-microsoft-intune.md) 및 지원되는 플랫폼

사용자에게 무선 네트워크 설정을 배포합니다. 이러한 설정을 통해 사용자가 기업 네트워크에 간편하게 연결할 수 있습니다.
#### <a name="supported-platforms"></a>지원되는 플랫폼

|Windows 8.1 이상|Windows Phone 8.1 이상|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|예(Windows Wi-Fi 프로필을 가져올 수 있음)|예(OMA-URI를 구성할 수 있음) |예|예|예|

## <a name="vpn-profilesvpn-connections-in-microsoft-intunemd-and-supported-platforms"></a>[VPN 프로필](vpn-connections-in-microsoft-intune.md) 및 지원되는 플랫폼
VPN(가상 사설망) 설정을 사용자에게 배포합니다. 이러한 설정을 통해 사용자가 기업 네트워크의 리소스에 간편하게 연결할 수 있습니다.

|Windows 8.1 이상|Windows Phone 8.1 이상|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|예|예|예|예|예|

## <a name="email-profilesconfigure-access-to-corporate-email-using-email-profiles-with-microsoft-intunemd-and-supported-platforms"></a>[전자 메일 프로필](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md) 및 지원되는 플랫폼
조직의 장치에서 네이티브 전자 메일 클라이언트 설정을 만들고, 배포하고, 모니터링할 수 있습니다.


| Windows 8.1 이상 | Windows Phone 8.1 이상 | iOS | Android | Samsung KNOX Standard |
|-----------------------|-----------------------------|-----|---------|-----------------------|
|          아니요           |             예             | 예 |   아니요    |          예          |

> [!NOTE]
> [이 Intune 팀 블로그 게시물](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/)에서는 OMA-URI를 사용하여 Windows Phone 8.1 Wi-Fi 프로필을 구성하는 방법에 대한 자세한 내용을 제공합니다.

## <a name="certificate-profilessecure-resource-access-with-certificate-profilesmd-and-supported-platforms"></a>[인증서 프로필](secure-resource-access-with-certificate-profiles.md) 및 지원되는 플랫폼
무선 네트워크 및 VPN 연결을 포함하여 회사 리소스에 안전하게 액세스할 수 있습니다.


| Windows 8.1 이상 | Windows Phone 8.1 이상 | iOS | Android | Samsung KNOX Standard |
|-----------------------|-----------------------------|-----|---------|-----------------------|
|          예          |             예             | 예 |   예   |          예          |

