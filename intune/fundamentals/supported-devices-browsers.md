---
title: Microsoft Intune에서 지원하는 운영 체제 및 브라우저
titleSuffix: ''
description: Intune 디바이스 관리용으로 지원되는 디바이스 플랫폼 및 브라우저를 나열합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 536f689a009f3e7e0128c350bafd3bf1340aeaaa
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260217"
---
# <a name="supported-operating-systems-and-browsers-in-intune"></a>Intune의 지원되는 운영 체제 및 브라우저

Microsoft Intune을 설정하기 전에 지원되는 운영 체제 및 브라우저를 검토합니다.

디바이스에 Intune을 설치하는 방법에 대한 도움말은 [관리 디바이스를 사용하여 작업 완료](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions) 및 [Intune 네트워크 대역폭 사용](network-bandwidth-use.md)을 참조하세요.

구성 서비스 공급자 지원에 대한 자세한 내용은 [구성 서비스 공급자 참조](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)를 참조하세요.

> [!NOTE]
> 이제 애플리케이션 및 디바이스가 Android용 회사 포털 앱 및 Android용 Intune 앱 SDK를 통해 회사 리소스에 액세스하려면 Intune에는 Android 5.x(롤리팝) 이상이 필요합니다. 4\.4를 실행하는 Polycom Android 기반 Teams 디바이스에는 이 요구 사항이 적용되지 않습니다. 해당 디바이스는 계속 지원됩니다. 

## <a name="intune-supported-operating-systems"></a>Intune에서 지원하는 운영 체제

다음 운영 체제를 실행하는 디바이스를 관리할 수 있습니다.

[!INCLUDE [mdm-supported-devices](../includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>지원되는 Samsung Knox Standard 디바이스

MDM 등록을 방해하는 Knox 활성화 오류를 방지하기 위해 회사 포털 앱은 디바이스가 [지원되는 Knox 디바이스 목록](https://www.samsungknox.com/knox-supported-devices/knox-workspace)에 표시되는 경우에만 MDM 등록 중에 Samsung Knox 활성화를 시도합니다. Samsung Knox 활성화를 지원하지 않는 디바이스는 표준 Android 디바이스로 등록됩니다. 모든 Samsung 디바이스에 Knox를 지원하는 모델 번호가 있는 것은 아닙니다. Samsung 디바이스를 구매하고 배포하기 전에 디바이스 재판매인의 Knox 호환성을 검사합니다.

> [!NOTE]
> Samsung Knox 디바이스를 등록하는 경우 [Samsung 서버에 대한 액세스를 허용](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers)해야 할 수도 있습니다.

다음 Samsung 디바이스 모델 목록은 Knox를 지원하지 않습니다. Android용 회사 포털 앱에서 네이티브 Android 디바이스로 등록됩니다.

| **디바이스 이름** | **디바이스 모델 번호** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM-T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |

### <a name="windows-pc-software-client"></a>Windows PC 소프트웨어 클라이언트

Windows PC에서는 대체 등록 방법으로 [Intune 소프트웨어 클라이언트](manage-windows-pcs-with-microsoft-intune.md)를 배포하고 설치할 수 있습니다. 이 기능은 Intune 클래식 포털을 통해서만 사용할 수 있습니다. Intune 소프트웨어 클라이언트를 사용하면 10 이상의 버전(Windows 10 Home Edition은 제외)을 실행하는 PC를 관리할 수 있습니다.

> [!Note]
> Microsoft는 2020년 1월 14일부로 Windows 7 지원을 중단한다고 발표했습니다. 이 날짜에 Intune도 Windows 7을 실행하는 디바이스에 대한 지원을 만료합니다.
>
> 자세한 내용은 [Intune 변경 계획: Windows 7 지원 종료](https://docs.microsoft.com/intune/fundamentals/whats-new#windows-7-ends-extended-support-)를 참조하세요.
>
> Microsoft Intune은 Silverlight 기반 Intune 콘솔 지원을 2020년 10월 15일에 중단할 예정입니다. Silverlight 콘솔 구성된 PC소프트웨어 클라이언트(또한 PC에이전트로 알려진)도 포함됩니다.
>
> 자세한 내용은 [Microsoft Intune Silverlight 기반 관리 콘솔 지원 종료](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Take-Action-Microsoft-Intune-ending-support-for-the-Silverlight/ba-p/916249)를 참조하세요.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](../enrollment/device-enrollment.md#mobile-device-management-with-exchange-activesync-and-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Intune 지원 웹 브라우저

여러 관리 태스크를 수행하려면 다음과 같은 관리 웹 사이트 중 하나를 사용해야 합니다.

- [Microsoft 365 관리 센터](https://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure Portal](https://portal.azure.com/)

이러한 포털에 대해 지원되는 브라우저는 다음과 같습니다.

- Microsoft Edge(최신 버전)
- Microsoft Internet Explorer 11
- Safari(최신 버전, Mac만)
- Chrome(최신 버전)
- Firefox(최신 버전)

### <a name="intune-classic-portal"></a>Intune 클래식 포털

Intune 클래식 포털은 Intune PC 소프트웨어 클라이언트에 등록된 디바이스를 관리하는 데만 사용됩니다(https://manage.microsoft.com) ). Intune 클래식 포털에는 Silverlight 브라우저 지원이 필요합니다.

Intune 콘솔을 지원하는 Silverlight 브라우저는 다음과 같습니다.

- Internet Explorer 10 이상
- Google Chrome(버전 42 이전 버전)
- Silverlight가 지원되는 Mozilla Firefox(버전 56 이전 버전)

> [!Note]
> Microsoft Edge 및 모바일 브라우저는 [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx)를 지원하지 않기 때문에 Intune 클래식 포털용으로 지원되지 않습니다.

서비스 관리자 권한이 있는 사용자이거나 전역 관리자 역할이 있는 테넌트 관리자만이 이 포털에 로그인할 수 있습니다. 관리 콘솔에 액세스하려면 계정에 Intune을 사용할 수 있는 라이선스가 있어야 하며 계정의 로그인 상태가 **허용**이어야 합니다.
