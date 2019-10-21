---
title: 파일 포함
description: 파일 포함
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 5ebab881a524bc361e271856b6762776974cea20
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601525"
---
이러한 알림은 향후 Intune 변경 사항 및 기능을 준비하는 데 도움이 되는 중요한 정보를 제공합니다.

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


### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>변경 계획: 10월에 Android 5.0 이상을 지원하도록 Android용 Intune 앱 SDK 및 앱 보호 정책 전환 <!--4911065 -->
Intune은 10월에 Android 5.x(Lollipop) 이상을 지원하도록 전환되고 있습니다. 최신 Intune 앱 SDK를 사용하여 래핑된 앱을 업데이트하고 디바이스를 업데이트합니다.

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

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Intune 변경 계획: Windows 7에 대한 지원이 거의 종료 <!-- 3042987 -->
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
