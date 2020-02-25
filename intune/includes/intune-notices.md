---
title: 파일 포함
description: 포함 파일
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: f23d81ddb07fcafb198cd725781747b61a3b73ea
ms.sourcegitcommit: 67f926ba83f8a955e16b741a610ad84d6044f8f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529341"
---
이러한 알림은 향후 Intune 변경 사항 및 기능을 준비하는 데 도움이 되는 중요한 정보를 제공합니다.

### <a name="microsoft-intune-support-for-windows-10-mobile-ending--3544938--"></a>Windows 10 Mobile에 대한 Microsoft Intune 지원 종료<!--3544938-->
Windows 10 Mobile에 대한 Microsoft 일반 지원은 2019년 12월에 종료되었습니다. 이 지원 정책에 설명된 대로 Windows 10 Mobile 사용자는 더 이상 Microsoft의 새로운 보안 패치, 비보안 핫픽스, 무료 보조 지원 옵션 또는 온라인 기술 콘텐츠 업데이트를 받을 수 없습니다. 모든 모바일 OS 지원에 따라 Microsoft Intune은 이제 2020년 5월 11일에 Windows 10 Mobile 앱 및 Windows 10 Mobile 운영 체제에 대한 회사 포털 지원을 종료합니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
조직에 Windows 10 Mobile 장치가 배포되어 있는 경우 2020년 5월 11일까지 새 디바이스를 등록하거나, 정책 및 앱을 추가 또는 제거하거나, 관리 설정을 업데이트할 수 있습니다. 5월 11일 이후에는 새 등록이 중지되고 최종적으로 Intune UI에서 Windows 10 Mobile 관리가 제거됩니다. 디바이스는 더 이상 Intune 서비스에 체크 인할 수 없으며 디바이스 및 정책 데이터는 삭제됩니다.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?
Intune 보고를 확인하여 디바이스 또는 사용자가 받을 수 있는 영향에 대해 알아볼 수 있습니다. **디바이스** > **모든 디바이스**로 이동하고 OS를 기준으로 필터링합니다. 추가 열에 추가하면 조직내 Windows 10 Mobile을 실행하는 디바이스를 가진 사용자를 식별하는 데 도움이 됩니다. 최종 사용자가 디바이스를 업그레이드하거나 회사 액세스에 해당 디바이스 사용을 중단할 것을 요청합니다.



### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>변경 계획: Intune에 Android 엔터프라이즈 전용 디바이스 등록 시 환경 변경<!--6114580-->
11월 릴리스에서 Android 엔터프라이즈 전용 디바이스에 SCEP 인증서 배포 지원을 추가하여 Wi-Fi 프로필에 대한 인증서 기반 액세스를 지원할 것이라는 소식을 전한 바 있습니다. 이러한 변경으로 인해 Android 엔터프라이즈 전용 디바이스에 대해 사소한 등록 과정에 작은 변화가 일부 있었습니다. 예정된 3월 서비스 업데이트 또는 2003에서의 몇 가지 변경 사항을 추가로 알려드리고자 합니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
사용 중인 환경에서 Android 엔터프라이즈 전용 디바이스를 관리하는 경우 3월에 일부 변경 내용이 롤아웃됩니다.
- 2019년 11월 22일 또는 1911 서비스 업데이트 이전에 등록된 기존 Android 전용 디바이스: 이 디바이스에는 Microsoft Intune 앱이 설치되어 있습니다. 3월에 Intune 서비스에서 백 엔드 변경이 롤아웃된 후에는 디바이스에 배포되고 Wi-Fi 프로필과 연결된 SCEP 인증서가 적용됩니다.
- 2019년 11월 22일 이후 및 이 변경 내용이 3월에 롤아웃되기 전에 등록된 디바이스: 이 디바이스에는 Microsoft Intune 앱이 설치되어 있습니다. 디바이스에 배포되고 Wi-Fi 프로필과 연결된 SCEP 인증서가 계속 적용 됩니다.
- 변경 내용이 3월에 롤아웃된 후 새로 등록된 Android 엔터프라이즈 전용 디바이스: 등록하는 동안 최종 사용자에게 디바이스에 대한 여러 단계가 표시됩니다. 등록은 현재와 같은 방식(QR, NFC, 자동(Zero-touch) 또는 디바이스 식별자 사용)으로 계속 시작되지만 필수 앱 설치 단계는 없습니다. 대신 Microsoft Intune 앱이 디바이스에 자동으로 설치됩니다. 또한 최종 사용자는 과정 중에 "Intune 에이전트 사용"을 탭할 필요가 없습니다. WiFi 프로필과 연결된 SCEP 인증서를 이 같은 디바이스에 배포할 수 있습니다.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?
최종 사용자 가이드를 업데이트하고 이 변경 내용을 기술 지원팀에 알릴 수 있습니다. Microsoft에서는 새로운 기능 페이지를 업데이트하고 이 변경 내용이 롤아웃되기 시작하면 메시지 센터를 통해 사용자에게 알립니다.

#### <a name="additional-information"></a>추가 정보
[Android 엔터프라이즈 전용 디바이스에서의 SCEP 인증서 지원](https://aka.ms/Dedicated_devices_enrollment)

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>'Intune용 Adobe Acrobat Reader' 모바일 앱에 대한 업데이트된 지원 정책<!--5746776-->
8월 말에 MC188653에서 Intune용 Adobe Acrobat Reader 모바일 앱이 2019년 12월 1일에 지원 종료되며, Adobe가 주 Acrobat Reader 앱 내에서 Intune의 앱 보호 정책을 지원하도록 계획 중이라는 소식을 제공했습니다. 그 이후에 IT 관리자가 Intune용 Adobe Acrobat Reader를 대상으로 지정하고 최종 사용자가 Intune용 Adobe Acrobat Reader 사용을 시작할 수 있도록 시간을 좀 더 제공해야 한다는 고객 의견을 받았습니다. 최종 사용자 디바이스에서 Intune용 Adobe Acrobat Reader가 많이 사용되고 있으며 엔터프라이즈 시나리오에서 중요도가 높다고 가정할 경우, 작업 환경이 조직의 앱 보호 요구를 충족하는지 확인하려고 할 것입니다. 

Acrobat Reader 모바일 앱은 앱 보호 정책을 지원하고 Intune SDK에 연결하므로 정책에서 여전히 일반 Acrobat Reader 모바일 앱을 대상으로 지정하는 것이 좋지만, Intune용 Adobe Acrobat Reader 앱은 2020년 3월 31일까지 계속 지원될 예정입니다. 

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
이 보고 기능이 조직의 하나 이상의 정책이 Intune용 Adobe Acrobat Reader 애플리케이션을 대상으로 하기 때문에 여러분은 앞으로 메시지를 받게 되거나, 이전 EOL 통신을 받았을 수 있습니다. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?
최종 사용자와 기술 지원팀에 이 변경 내용을 알립니다. [회사 포털의 지원 정보 기능](../apps/company-portal-app.md#support-information)을 사용하여 Intune 관련 질문에 대한 채널을 설정할 수 있습니다.

#### <a name="additional-information"></a>추가 정보
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>작업 수행: 보호된 Intune 브라우저 환경에 Microsoft Edge 사용<!--5728447-->
작년 한 해 동안 공유하면서 Microsoft Edge 모바일은 Managed Browser와 동일한 관리 기능 집합을 지원하는 한편, 훨씬 향상된 최종 사용자 환경을 제공하고 있습니다. Microsoft Edge에서 제공하는 강력한 환경을 사용할 수 있도록 Intune Managed Browser의 사용을 중단합니다. 2020년 1월 27일부터 Intune은 더 이상 Intune Managed Browser를 지원하지 않습니다.  

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요? 
2020년 2월 1일부터 Intune Managed Browser는 더 이상 Google Play 스토어 또는 iOS 앱 스토어에서 사용할 수 없습니다. 이 시점에서 새 앱 보호 정책의 대상으로 Intune Managed Browser를 지정할 수는 있지만 새로운 사용자가 Intune Managed Browser 앱을 다운로드할 수 없습니다. 또한 iOS에서 MDM에 등록된 디바이스로 푸시되는 새 웹 클립이 Intune Managed Browser 대신 Microsoft Edge에서 열립니다.  

2020년 3월 31일로 Azure 콘솔에서 Intune Managed Browser가 제거됩니다. 즉, 더 이상 Intune Managed Browser에 대한 새 정책을 만들 수 없습니다. 기존 Intune Managed Browser 정책은 영향을 받지 않습니다. Intune Managed Browser는 콘솔에서 아이콘이 없는 LOB 앱으로 표시되고, 기존 정책은 이 앱을 대상으로 하는 것으로 계속 표시됩니다. 이 시점에서 앱 보호 정책의 데이터 보호 섹션 내에서 Intune Managed Browser 웹 콘텐츠를 리디렉션하는 옵션도 제거됩니다.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요? 
Intune Managed Browser에서 Microsoft Edge로 원활하게 전환하려면 다음 단계를 사전에 수행하는 것이 좋습니다. 

1. 앱 보호 정책(MAM이라고도 함) 및 앱 구성 설정의 대상으로 iOS 및 Android용 Microsoft Edge를 지정합니다. 기존 정책의 대상을 Microsoft Edge로 지정하면 Intune Managed Browser 정책을 Microsoft Edge에 다시 사용할 수 있습니다.  
2. 사용자 환경의 모든 MAM 보호 앱에서 앱 보호 정책 설정인 "다른 앱을 사용한 웹 콘텐츠 전송 제한"이 "정책 관리 브라우저"로 설정되어 있는지 확인합니다. 
3. 모든 MAM 보호 앱에 대해 앱 구성 설정 "com.microsoft.intune.useEdge"를 true로 설정합니다. 다음 달 1911 릴리스부터 앱 보호 정책의 데이터 보호 섹션에서 "다른 앱을 사용한 웹 콘텐츠 전송 제한" 설정에 "Microsoft Edge"를 선택하도록 구성하여 2단계와 3단계를 완료할 수 있습니다. 

iOS 및 Android의 웹 클립에 대한 지원이 제공됩니다. 이 지원이 릴리스될 때 기존 웹 클립의 대상을 변경하여 Managed Browser가 아닌 Microsoft Edge에서 열 수 있도록 해야 합니다. 

#### <a name="additional-information"></a>추가 정보
자세한 내용은 [앱 보호 정책과 함께 Microsoft Edge 사용](../apps/manage-microsoft-edge.md)에 대한 문서를 참조하거나 [지원 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269)을 참조하세요.


### <a name="end-of-support-for-legacy-pc-management"></a>레거시 PC 관리에 대한 지원 종료

레거시 PC 관리 지원이 2020년 10월 15일 종료됩니다. 디바이스가 Intune에서 계속 관리되도록 하려면 디바이스를 Windows 10으로 업그레이드하고 MDM(모바일 디바이스 관리) 디바이스로 다시 등록하세요.

[자세한 정보](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Android 디바이스 관리자에 대한 지원 감소 
Android 디바이스 관리자("레거시" Android 관리라고도 하며 Android 2.2를 통해 출시됨)는 Android 디바이스를 관리하는 방법입니다. 그러나 이제 향상된 관리 기능을 [Android Enterprise](../enrollment/connect-intune-android-enterprise.md)(Android 5.0을 통해 출시)에서 사용할 수 있습니다. 최신의 풍부하고 보다 안전한 디바이스 관리로 전환하기 위해 Google은 새로운 Android 릴리스에서 디바이스 관리자 지원을 줄이고 있습니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
Google의 이러한 변경으로 인해 Intune 사용자는 다음과 같은 방식으로 영향을 받습니다.  
- Intune은 Android 10 이상 ~ Q2 CY2020을 실행하는 디바이스 관리자 관리형 Android 디바이스만 지원할 수 있습니다. 이 시점 이후에 Android 10 이상을 실행하는 디바이스 관리자 관리형 디바이스는 더 이상 완전히 관리할 수는 없게 됩니다. 특히 영향을 받는 디바이스에는 새 암호 요구 사항이 없습니다.
    - Intune과 Knox 플랫폼의 통합을 통해 확장된 지원이 제공되므로 이 기간 동안 Samsung Knox 디바이스는 영향을 받지 않습니다. 이를 통해 더 많은 시간 동안 디바이스 관리 전환을 계획할 수 있습니다.    
- Android 10 미만의 Android 버전을 유지하는 디바이스 관리자 관리형 Android 디바이스는 영향을 받지 않으며, 디바이스 관리자를 통해 계속해서 완전히 관리할 수 있습니다.    
- Android 10 이상을 실행하는 모든 디바이스에 대해 Google은 회사 포털과 같은 디바이스 관리자 관리 에이전트가 디바이스 식별자 정보에 액세스하는 기능을 제한하고 있습니다. 이 제한 사항은 디바이스를 Android 10 이상으로 업데이트한 이후에 다음 Intune 기능에 영향을 줍니다.  
    - VPN에 대한 네트워크 액세스 제어는 더 이상 작동하지 않습니다.   
    - IMEI 또는 일련 번호를 사용하여 회사 소유의 디바이스를 식별해도 디바이스가 회사 소유로 자동으로 표시되지 않습니다.  
    - IMEI 및 일련 번호는 Intune의 IT 관리자에게 더 이상 표시되지 않습니다. 
        > [!NOTE]
        > 이러한 문제는 Android 10 이상의 디바이스 관리자 관리형 디바이스에만 영향을 주고 Android Enterprise로 관리되는 디바이스에는 영향을 주지 않습니다. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?
Q3 CY2020에 제공될 기능 감소를 피하려면 다음을 수행하는 것이 좋습니다.
- 새 디바이스를 디바이스 관리자 관리에 온보딩하지 마세요.
- 디바이스에 Android 10에 대한 업데이트가 수신될 예정인 경우, 디바이스 관리자 관리에서 Android Enterprise 관리 및/또는 앱 보호 정책으로 마이그레이션합니다.

#### <a name="additional-information"></a>추가 정보
- [디바이스 관리자에서 Android Enterprise로 마이그레이션하기 위한 Google 지침](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [디바이스 관리자 API 사용 중단 계획에 대한 Google 설명서](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>변경 계획: 향후 릴리스에서 Android 5.0 이상을 지원하도록 Android용 Intune 앱 SDK 및 앱 보호 정책 전환 <!--4911065 -->
Intune은 향후 릴리스에 Android 5.x(Lollipop) 이상을 지원하도록 전환되고 있습니다. 최신 Intune 앱 SDK를 사용하여 래핑된 앱을 업데이트하고 디바이스를 업데이트합니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
Android용 SDK 또는 앱을 사용하고 있지 않거나 향후 사용할 예정인 경우 이 변경의 영향을 받지 않습니다. Intune 앱 SDK를 사용하는 경우 최신 버전으로 업데이트하고, 디바이스를 Android 5.x 이상으로 업데이트해야 합니다. 업데이트하지 않으면 앱은 업데이트를 받지 못하며 해당 환경 품질이 시간이 흐름에 따라 저하됩니다.

아래에서 Android 버전 4.x를 실행하는 Intune에 등록된 일반 디바이스 목록을 찾아보세요. 이러한 디바이스 중 하나를 사용하는 경우 이 디바이스에서 Android 버전 5.0 이상을 지원하거나 Android 버전 5.0 이상을 지원하는 디바이스로 대체되도록 적절한 단계를 수행합니다. 이 목록은 평가해야 할 수 있는 모든 디바이스를 포함하지는 않습니다.

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?
최신 Intune 앱 SDK를 사용하여 앱을 래핑합니다. 사용자가 개인 디바이스의 최종 사용자에게 업그레이드할 것을 알리도록 "최소 OS 버전 필요(경고만)" 조건부 시작 설정을 지정할 수도 있습니다.


