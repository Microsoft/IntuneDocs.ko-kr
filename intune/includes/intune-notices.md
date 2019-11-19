---
title: 파일 포함
description: 파일 포함
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/4/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 3d49d31ed08683508d3d231521e578688dd21bac
ms.sourcegitcommit: 737ad6c675deedfc6009f792023ff95981b06582
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74125542"
---
이러한 알림은 향후 Intune 변경 사항 및 기능을 준비하는 데 도움이 되는 중요한 정보를 제공합니다.

### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Intune 변경 계획: Windows 10, 버전 1703 회사 포털 지원 종료<!--5026679-->
Windows 10, 버전 1703(Windows 10, RS2라고도 함)은 2019년 10월 8일 자로 Enterprise 및 EDU Edition에 대한 서비스가 중단되었습니다. Intune은 2019년 12월 26일부터 RS2/RS1용 회사 포털 앱에 대한 지원을 종료합니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
앞으로 이 버전의 회사 포털 앱에 새 기능이 표시되지는 않지만, 2019년 12월 26일까지 필요에 따라 회사 포털 앱에 대한 보안 업데이트 제공을 포함하여 이 회사 포털 앱 버전을 계속 지원합니다. 그러나 서비스 중단 이후에는 Windows 10, 버전 1703이 보안 업데이트를 받지 못하므로 새로운 기능 및 추가 기능을 계속 제공받을 수 있도록 Windows 디바이스를 보다 최신의 Windows 버전으로 업데이트하고 최신 회사 포털 앱을 사용하는 것이 좋습니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
수행할 단계는 환경 구성에 따라 달라집니다. 일반적으로 이전 버전의 OS 및/또는 회사 포털이 설치된 디바이스를 식별하여 업데이트해야 합니다. Windows 10 업데이트 링을 설정하려면 Intune -> 소프트웨어 업데이트 – Windows 10 업데이트 링에 로그인합니다. 최신 버전의 회사 포털은 버전 10.3.5601.0입니다. 사용자에게 향후 릴리스로 최신 상태를 유지할 수 있게 Microsoft Store에서 최신 버전을 다운로드하도록 지시하세요. Intune을 사용하여 [비즈니스용 Microsoft Store](https://docs.microsoft.com/intune/windows-store-for-business)를 통해 Windows 디바이스에 최신 버전을 설치할 수도 있습니다.

#### <a name="additional-information"></a>추가 정보
[Microsoft Intune을 사용하여 Windows 10 회사 포털 앱 수동으로 추가](https://docs.microsoft.com/intune/store-apps-company-portal-app)


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>작업 수행: 보호된 Intune 브라우저 환경에 Microsoft Edge 사용<!--5728447-->
작년 한 해 동안 공유하면서 Microsoft Edge 모바일은 Managed Browser와 동일한 관리 기능 집합을 지원하는 한편, 훨씬 향상된 최종 사용자 환경을 제공하고 있습니다. Microsoft Edge에서 제공하는 강력한 환경을 사용할 수 있도록 Intune Managed Browser의 사용을 중단합니다. 2020년 1월 27일부터 Intune은 더 이상 Intune Managed Browser를 지원하지 않습니다.  

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요? 
2020년 2월 1일부터 Intune Managed Browser는 더 이상 Google Play 스토어 또는 iOS 앱 스토어에서 사용할 수 없습니다. 이 시점에서 새 앱 보호 정책의 대상으로 Intune Managed Browser를 지정할 수는 있지만 새로운 사용자가 Intune Managed Browser 앱을 다운로드할 수 없습니다. 또한 iOS에서 MDM에 등록된 디바이스로 푸시되는 새 웹 클립이 Intune Managed Browser 대신 Microsoft Edge에서 열립니다.  

2020년 3월 31일로 Azure 콘솔에서 Intune Managed Browser가 제거됩니다. 즉, 더 이상 Intune Managed Browser에 대한 새 정책을 만들 수 없습니다. 기존 Intune Managed Browser 정책은 영향을 받지 않습니다. Intune Managed Browser는 콘솔에서 아이콘이 없는 LOB 앱으로 표시되고, 기존 정책은 이 앱을 대상으로 하는 것으로 계속 표시됩니다. 이 시점에서 앱 보호 정책의 데이터 보호 섹션 내에서 Intune Managed Browser 웹 콘텐츠를 리디렉션하는 옵션도 제거됩니다.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요? 
Intune Managed Browser에서 Microsoft Edge로 원활하게 전환하려면 다음 단계를 사전에 수행하는 것이 좋습니다. 

1. 앱 보호 정책(MAM이라고도 함) 및 앱 구성 설정의 대상으로 iOS 및 Android용 Microsoft Edge를 지정합니다. 기존 정책의 대상을 Microsoft Edge로 지정하기만 해도 Intune Managed Browser 정책을 Microsoft Edge에 다시 사용할 수 있습니다.  
2. 사용자 환경의 모든 MAM 보호 앱에서 앱 보호 정책 설정인 "다른 앱을 사용한 웹 콘텐츠 전송 제한"이 "정책 관리 브라우저"로 설정되어 있는지 확인합니다. 
3. 모든 MAM 보호 앱에 대해 앱 구성 설정 "com.microsoft.intune.useEdge"를 true로 설정합니다. 다음 달 1911 릴리스부터 앱 보호 정책의 데이터 보호 섹션에서 "다른 앱을 사용한 웹 콘텐츠 전송 제한" 설정에 "Microsoft Edge"를 선택하도록 구성하여 2단계와 3단계를 완료할 수 있습니다. 

iOS 및 Android의 웹 클립에 대한 지원이 제공됩니다. 이 지원이 릴리스될 때 기존 웹 클립의 대상을 변경하여 Managed Browser가 아닌 Microsoft Edge에서 열 수 있도록 해야 합니다. 

#### <a name="additional-information"></a>추가 정보
자세한 내용은 [앱 보호 정책과 함께 Microsoft Edge 사용](../apps/manage-microsoft-edge.md)에 대한 문서를 참조하거나 [지원 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269)을 참조하세요.


### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>변경 계획: Intune에서 Android Enterprise 전용 디바이스를 등록할 때 업데이트된 환경<!--5198878-->
Intune의 11월 또는 1911 릴리스에서는 Android Enterprise 전용 디바이스에 SCEP 디바이스 인증서 배포 지원을 추가하여 Wi-Fi 프로필에 대한 인증서 기반 액세스를 지원합니다. 이러한 변경 내용에는 Android Enterprise 전용 디바이스를 등록하는 경우 몇 가지 사소한 변경 내용도 포함됩니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
사용 중인 환경에서 Android Enterprise 전용 디바이스를 관리하는 경우 11월에 일부 변경 내용이 롤아웃됩니다.

- 새로운 Android 엔터프라이즈 전용 디바이스를 등록하는 경우: 등록하는 동안 최종 사용자에게 디바이스에 대한 여러 단계가 표시됩니다. 등록은 현재와 같은 방식(QR, NFC, Zero-touch 또는 디바이스 식별자 사용)으로 계속 시작되지만 11월 서비스 릴리스 이후에는 필수 앱 설치 단계가 있습니다.
- 전용 디바이스로 등록된 기존 Android 디바이스의 경우: Intune은 11월 초부터 디바이스에 Microsoft Intune 앱을 자동으로 설치합니다. 사용자는 아무 작업도 수행할 필요가 없습니다. 해당 앱이 자동으로 다운로드되고 디바이스에 설치됩니다. 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?
최종 사용자 지침 업데이트를 계획하고 이 변경 내용을 지원 센터에 알려야 합니다. 자세한 내용 및 스크린샷을 보려면 추가 정보를 클릭하세요. 이 변경 내용이 롤아웃될 때 새로운 기능 페이지가 업데이트됩니다.

#### <a name="additional-information"></a>추가 정보
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>변경 계획: Intune 콘솔에서 ‘Siri 명령의 서버 쪽 로깅’ 설정이 제거됩니다. <!-- 5468501-->

Intune 서비스의 11월 업데이트에서 Intune 콘솔에서 "Siri 명령의 서버 쪽 로깅" 설정을 제거할 예정입니다. 이 변경 사항은 Apple 측에서 이미 설정을 제거한 상태입니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
11월 업데이트나 1911이 11월 중반에 롤아웃되면, Intune 콘솔에서 iOS 구성 프로필에 대해 디바이스 제한 메뉴(기본 제공 앱)에서 이 설정이 제거된 것을 확인할 수 있습니다. 정책 및 대상 디바이스의 관리 프로필에 나타날 수 있지만 설정은 디바이스에 영향을 주지 않습니다. 관리 프로필에 표시되더라도 현재 디바이스에서 작동하지 않으므로 기능에 많은 영향을 미치지 않을 것으로 예상합니다.

다음 두 경로 중 하나를 선택할 수 있습니다.
- 정책에서 이 설정을 삭제하려는 경우 이 설정이 있는 프로필로 이동하여 약간 편집하고 정책을 저장합니다. 이 정책은 백 엔드에서 다시 컴퓨팅되고 설정은 정책에서 삭제됩니다.
- 이 작업을 수행하지 않도록 선택하면 최종 사용자는 디바이스의 관리 프로필에서 이 설정을 볼 수 있지만 설정은 적용되지 않습니다.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?
위의 섹션에 따라 작업을 수행하거나 정책을 그대로 둘 수 있습니다. 이 변경 내용이 롤아웃될 때 새로운 기능 페이지 및 설명서를 업데이트할 예정입니다.

### <a name="end-of-support-for-legacy-pc-management"></a>레거시 PC 관리에 대한 지원 종료

레거시 PC 관리 지원이 2020년 10월 15일 종료됩니다. 디바이스가 Intune에서 계속 관리되도록 하려면 디바이스를 Windows 10으로 업그레이드하고 MDM 디바이스로 다시 등록하세요.

[자세한 정보](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Android 디바이스 관리자에 대한 지원 감소 
Android 디바이스 관리자("레거시" Android 관리라고도 하며 Android 2.2를 통해 출시됨)는 Android 디바이스를 관리하는 방법입니다. 그러나 이제 향상된 관리 기능을 [Android Enterprise](../enrollment/connect-intune-android-enterprise.md)(Android 5.0을 통해 출시)에서 사용할 수 있습니다. 최신의 풍부하고 보다 안전한 디바이스 관리로 전환하기 위해 Google은 새로운 Android 릴리스에서 디바이스 관리자 지원을 줄이고 있습니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
Google의 이러한 변경으로 인해 Intune 사용자는 다음과 같은 방식으로 영향을 받습니다.  
- Intune은 Android 10 이상(Android Q라고도 함)을 실행하는 디바이스 관리자 관리형 Android 디바이스에 대한 지원을 2020년 여름까지만 제공할 수 있습니다. 이 날짜는 Android의 차기 주 버전이 출시될 것으로 예상되는 날짜입니다.   
- 2020 여름 이후에 Android 10 이상을 실행하는 디바이스 관리자 관리형 디바이스는 더 이상 완전히 관리할 수는 없게 됩니다.       
- Android 10 미만의 Android 버전을 유지하는 디바이스 관리자 관리형 Android 디바이스는 영향을 받지 않으며, 디바이스 관리자를 통해 계속해서 완전히 관리할 수 있습니다.    
- Android 10 이상을 실행하는 모든 디바이스에 대해 Google은 회사 포털과 같은 디바이스 관리자 관리 에이전트가 디바이스 식별자 정보에 액세스하는 기능을 제한하고 있습니다. 이러한 점은 디바이스를 Android 10 이상으로 업데이트한 이후에 다음 Intune 기능에 영향을 줍니다.  
    - VPN에 대한 네트워크 액세스 제어는 더 이상 작동하지 않습니다.   
    - IMEI 또는 일련 번호를 사용하여 회사 소유의 디바이스를 식별해도 디바이스가 회사 소유로 자동으로 표시되지 않습니다.  
    - IMEI 및 일련 번호는 Intune의 IT 관리자에게 더 이상 표시되지 않습니다. 
        > [!NOTE]
        > 이러한 문제는 Android 10 이상의 디바이스 관리자 관리형 디바이스에만 영향을 주고 Android Enterprise로 관리되는 디바이스에는 영향을 주지 않습니다. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
2020년 여름에 시작될 기능 감소를 피하려면 다음을 수행하는 것이 좋습니다.
- 새 디바이스를 디바이스 관리자 관리에 온보딩하지 마세요.
- 디바이스에 Android 10에 대한 업데이트가 수신될 예정인 경우, 디바이스 관리자 관리에서 Android Enterprise 관리 및/또는 앱 보호 정책으로 마이그레이션합니다.

#### <a name="additional-information"></a>추가 정보
- [디바이스 관리자에서 Android Enterprise로 마이그레이션하기 위한 Google 지침](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [디바이스 관리자 API 사용 중단 계획에 대한 Google 설명서](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Android 회사 포털 앱을 최신 버전으로 업데이트 <!--4536963-->
Intune은 Android 회사 포털 앱에 대한 업데이트를 주기적으로 릴리스합니다. 2018년 11월에 Microsoft는 회사 포털 업데이트를 발표했습니다. 이 업데이트에는 Google의 기존 알림 플랫폼에서 FCM(Firebase Cloud Messaging)으로 변경할 수 있도록 지원하는 백엔드 스위치가 포함되어 있습니다. Google이 기존 알림 플랫폼을 사용 중지하고 FCM으로 이동하면 최종 사용자는 회사 포털 앱을 2018년 11월 릴리스 이상으로 업데이트해야 Google Play 스토어와 계속 통신할 수 있습니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
원격 측정 결과 회사 포털 버전이 5.0.4269.0 이전인 디바이스가 있습니다. 회사 포털 앱이 이 버전 이상이 설치되지 않은 경우 IT 팀에서 시작한 디바이스 작업(예: 삭제, 암호 재설정, 사용 가능한 애플리케이션 설치 및 필수 애플리케이션 설치, 인증서 등록)이 예상대로 작동하지 않을 수 있습니다. 디바이스가 Intune에 등록된 MDM인 경우 클라이언트 앱 - 검색된 앱으로 이동하여 회사 포털 버전과 사용자를 볼 수 있습니다. 회사 포털 앱의 이전 버전을 선택하면 회사 포털 앱을 업데이트하지 않은 최종 사용자가 어떤 디바이스를 가지고 있는지 확인할 수 있습니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
업데이트되지 않은 Android 디바이스의 최종 사용자에게 Google Play를 통해 회사 포털 앱을 업데이트하도록 요청합니다. 사용자가 회사 포털 앱을 자동 업데이트하지 않은 경우 기술 지원팀에 알립니다. Google의 FCM 플랫폼 및 변경 사항에 대한 자세한 내용은 *추가 정보* 링크를 참조하시기 바랍니다.

#### <a name="additional-information"></a>추가 정보
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Intune에 제공하는 새로운 전체 화면 환경 <!--4593669-->
Azure Portal의 Intune에 업데이트된 UI 작성 및 편집 환경을 제공합니다. 이 새로운 환경은 하나의 블레이드 내에 압축된 마법사 스타일 형식을 사용하여 기존 워크플로를 단순화합니다. 이 업데이트는 "블레이드 확장"또는 딥 블레이드 이동 경로에 드릴다운해야 하는 모든 작성 및 편집 흐름을 제거합니다. 또한 앱 할당을 제외한 할당을 포함하도록 생성 워크플로도 업데이트됩니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
전체 화면 환경은 다음 몇 달 동안 portal.azure.com 및 devicemanagement.microsoft.com 모두에서 Intune으로 롤아웃됩니다. UI에 대한 이 업데이트는 기존 정책 및 프로필의 기능에 영향을 주지 않지만 약간 수정된 워크플로를 볼 수 있습니다. 예를 들어 새 정책을 생성할 때 정책을 생성한 후 할당을 설정하지 않고 이 흐름의 일부로 설정할 수 있습니다. 콘솔에서 새로운 환경이 어떻게 보일지 스크린샷에 대한 *추가 정보*는 블로그 게시물을 참조하세요.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?
어떠한 조치도 취할 필요가 없지만 필요한 경우 IT 전문가 지침 업데이트를 고려할 수 있습니다. 이 환경이 Azure Portal의 Intune에 있는 다양한 블레이드에 롤아웃됨에 따라 문서를 업데이트할 것입니다.

#### <a name="additional-information"></a>추가 정보 
https://aka.ms/intune_fullscreen

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

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
최신 Intune 앱 SDK를 사용하여 앱을 래핑합니다. 사용자가 개인 디바이스의 최종 사용자에게 업그레이드할 것을 알리도록 "최소 OS 버전 필요(경고만)" 조건부 시작 설정을 지정할 수도 있습니다.

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Intune 변경 계획: Windows 7에 대한 지원이 거의 종료<!-- 3042987 -->
지난 2018년 9월에 MC148476에서 그리고 2019년 3월에 MC176794에서 다시 공지한 대로 2020년 1월 14일에 Windows 7 연장 지원이 종료됩니다. 이때 Intune은 Windows 7을 실행하는 디바이스에 대한 지원을 중지하므로 새로운 기술 지원 및 새로운 최종 사용자 환경을 제공하는 데 집중할 수 있습니다. 이 날짜 이후에는 Windows 7 PC를 보호하는 데 유용한 기술 지원과 자동 업데이트를 더 이상 Intune을 통해 받을 수 없습니다. 서비스 또는 지원을 더 이상 받을 수 없게 되는 시나리오를 방지하려면 2020년 1월 1일 이전에 Windows 10으로 전환하는 것이 좋습니다. Windows 지원 수명 주기에 대한 자세한 정보는 [여기](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)를 참조하세요.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
현재 레거시 Intune PC 소프트웨어 에이전트를 사용하여 Windows 7 PC를 관리하고 있는 경우 이 메시지가 표시됩니다. Windows 7 연장 지원이 종료되기까지 1년도 남지 않았으므로, 가능하면 빨리 조직 차원에서 Windows 10으로 업그레이드를 시작하는 것이 좋습니다.  

PC 관리 기능은 Windows 10 운영 체제에 직접 구축되므로 Windows 7용 Intune 소프트웨어 클라이언트와 같은 클라이언트 에이전트를 더 이상 설치할 필요가 없습니다. Windows 8.1부터 Microsoft는 MDM(모바일 장치 관리) 아키텍처를 사용하여 Windows PC를 프로비전, 구성, 업데이트 및 관리합니다. Intune을 설정하면 MDM 채널을 통해 [Windows 10 PC를 Intune에 등록](..\windows-enroll.md)함으로써 Windows 등록을 간소화할 수 있습니다. 이러한 "에이전트 없는" MDM 관리 솔루션을 사용하여 Windows 10 PC를 관리하는 것이 좋습니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
조직 차원에서 이 작업 계획을 즉시 고려하는 것이 좋습니다.

- 2020년 1월 14일 이전에 Windows 7 제품군을 Windows 10으로 업그레이드하는 계획을 세우세요.
- 기존 Windows 7 PC 그룹을 Windows 10으로 업그레이드하는 방법에 대한 자세한 내용은 [Windows 10 배포 지원](https://docs.microsoft.com/windows/deployment/)을 살펴보세요.
- Microsoft 애플리케이션 호환성 약속을 지원하는 FastTrack을 통해 [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) 제안을 검토합니다.
- 기존 레거시 Intune 소프트웨어 클라이언트 관리 디바이스를 Microsoft 권장 솔루션으로 전환함으로써 MDM 관리를 사용하여 Windows 10을 관리합니다. Azure Portal에서 Intune용 MDM 관리를 사용하여 모든 새로운 Windows 10 PC를 등록합니다.

자세한 정보는 [여기에서 블로그 게시물](https://aka.ms/Windows7_Intune)을 참조하세요.
