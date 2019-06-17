---
title: 파일 포함
description: 파일 포함
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fab8f2be48a30f6ad058b3eeb6874a44ff04e6ac
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744308"
---
이러한 알림은 향후 Intune 변경 사항 및 기능을 준비하는 데 도움이 되는 중요한 정보를 제공합니다. 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Android 회사 포털 앱을 최신 버전으로 업데이트 <!--4536963-->
Intune은 Android 회사 포털 앱에 대한 업데이트를 주기적으로 릴리스합니다. 2018년 11월에 Microsoft는 회사 포털 업데이트를 발표했습니다. 이 업데이트에는 Google의 기존 알림 플랫폼에서 FCM(Firebase Cloud Messaging)으로 변경할 수 있도록 지원하는 백엔드 스위치가 포함되어 있습니다. Google이 기존 알림 플랫폼을 사용 중지하고 FCM으로 이동하면 최종 사용자는 회사 포털 앱을 2018년 11월 릴리스 이상으로 업데이트해야 Google Play 스토어와 계속 통신할 수 있습니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
원격 측정 결과 회사 포털 버전이 5.0.4269.0 이전인 디바이스가 있습니다. 회사 포털 앱이 이 버전 이상이 설치되지 않은 경우 IT 팀에서 시작한 디바이스 작업(예: 삭제, 암호 재설정, 사용 가능한 애플리케이션 설치 및 필수 애플리케이션 설치, 인증서 등록)이 예상대로 작동하지 않을 수 있습니다. 장치가 Intune에 등록된 MDM인 경우 클라이언트 앱 - 검색된 앱으로 이동하여 회사 포털 버전과 사용자를 볼 수 있습니다. 회사 포털의 이전 버전을 선택하면 회사 포털을 업데이트하지 않은 최종 사용자가 어떤 디바이스를 가지고 있는지 확인할 수 있습니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
업데이트되지 않은 Android 디바이스의 최종 사용자에게 Google 플레이를 통해 회사 포털을 업데이트하도록 요청합니다. 사용자가 회사 포털 앱을 자동 업데이트하지 않은 경우 기술 지원팀에 알립니다. Google의 FCM 플랫폼 및 변경 사항에 대한 자세한 내용은 추가 정보 링크를 참조하시기 바랍니다.

#### <a name="additional-information"></a>추가 정보
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Intune에 제공하는 새로운 전체 화면 환경 <!--4593669-->
Azure Portal의 Intune에 업데이트된 UI 작성 및 편집 환경을 제공합니다. 이 새로운 환경은 하나의 블레이드 내에 압축된 마법사 스타일 형식을 사용하여 기존 워크플로를 단순화합니다. 이 업데이트는 "블레이드 확장"또는 딥 블레이드 이동 경로에 드릴다운해야 하는 모든 작성 및 편집 흐름을 제거합니다. 또한 앱 할당을 제외한 할당을 포함하도록 생성 워크플로도 업데이트됩니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
전체 화면 환경은 다음 몇 달 동안 portal.azure.com과 devicemanagement.microsoft.com에서 모두 Intune으로 롤아웃됩니다. UI에 대한 이 업데이트는 기존 정책 및 프로필의 기능에 영향을 주지 않지만 약간 수정된 워크플로를 볼 수 있습니다. 예를 들어 새 정책을 생성할 때 정책을 생성한 후 할당을 설정하지 않고 이 흐름의 일부로 설정할 수 있습니다. 콘솔에서 새로운 환경이 어떻게 보일지 스크린샷에 대한 추가 정보는 블로그 게시물을 참조하세요.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?
어떠한 조치도 취할 필요가 없지만 필요한 경우 IT 전문가 지침 업데이트를 고려할 수 있습니다. 이 환경이 Azure Portal의 Intune에 있는 다양한 블레이드에 롤아웃됨에 따라 문서를 업데이트할 것입니다.

#### <a name="additional-information"></a>추가 정보 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>변경 계획: 9월에 Intune이 iOS 11 이상 지원으로 전환 <!-- 4665342-->
9월에 Apple이 iOS 13을 출시할 예정입니다. Intune 등록, 회사 포털 및 관리 브라우저는 iOS 13 릴리스 직후에 iOS 11 이상을 지원하도록 전환할 예정입니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
O365 모바일 앱이 iOS 11.0 이상에서 지원되는 경우 이는 사용자에게 영향을 주지 않을 수 있습니다. 이미 OS 또는 디바이스를 업그레이드했을 가능성이 큽니다. 그러나 아래에 나열된 모든 디바이스가 있거나 아래에 나열된 모든 디바이스를 등록하려는 경우 아래의 디바이스가 iOS 10보다 큰 OS를 지원하지 않는다는 것을 알고 있어야 합니다. 이러한 디바이스는 iOS 11 이상을 지원하는 디바이스로 업그레이드해야 합니다.

- iPhone 5
- iPhone 5c
- iPad(4세대)

7월부터 MDM에 iOS 10을 사용하는 디바이스가 등록되고 회사 포털에는 해당 OS 또는 디바이스를 업그레이드하라는 메시지가 표시됩니다. APP(애플리케이션 보호 정책)를 사용하는 경우 “최소 iOS 운영 체제 필수(경고만)” 액세스 설정도 설정할 수 있습니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
디바이스 또는 사용자가 받을 수 있는 영향에 대해 알아보려면 Intune 보고를 확인하세요. **디바이스** > **모든 디바이스**로 이동하고 OS를 기준으로 필터링합니다. 추가 열에 추가하면 iOS 10을 실행하는 디바이스를 가진 조직의 사용자를 식별하는 데 도움이 됩니다. 최종 사용자는 9월 전에 지원되는 OS 버전으로 자신의 디바이스를 업그레이드하도록 요청합니다.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>변경 계획: iOS용 Intune App SDK 버전 8.1.1 이상 지원 <!-- 3586942-->
2019년 9월부터 Intune은 Intune App SDK 8.1.1 이상을 사용하여 iOS 앱 지원으로 전환됩니다. 8\.1.1 미만의 SDK 버전으로 빌드된 앱은 더 이상 지원되지 않습니다. 이 변경 내용은 9월경에 출시될 예정이며 MC181399에서도 공지되는 Apple의 iOS 13 릴리스와 함께 적용될 예정입니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
Intune App SDK 또는 App Wrapping 통합을 사용하면 데이터 암호화를 통해 승인되지 않은 애플리케이션 및 사용자로부터 회사 데이터를 보호할 수 있습니다. iOS용 Intune App SDK는 Intune APP(앱 보호 정책)에서 암호화를 사용하도록 설정할 때 기본적으로 256비트 암호화 키를 사용합니다. 이 변경 후 128비트 암호화 키를 사용하는 8.1.1 이전 SDK 버전의 iOS 앱은 더 이상 SDK 8.1.1과 통합된 애플리케이션 또는 256비트 키를 사용하여 데이터를 공유할 수 없습니다. 모든 iOS 앱에는 보호된 데이터 공유를 허용하기 위해 SDK 버전 8.1.1 이상이 있어야 합니다.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변화를 위해 무엇을 준비할 수 있나요?
Microsoft, 타사 및 LOB(기간 업무) 앱을 확인합니다. Intune 앱으로 보호되는 모든 애플리케이션이 SDK 버전 8.1.1 이상을 사용하고 있는지 확인해야 합니다.

- LOB 앱의 경우: SDK 버전 8.1.1 이상과 통합된 앱을 다시 게시해야 할 수도 있습니다. 최신 SDK 버전을 사용하는 것이 좋습니다. 앱 보호 정책용 LOB 앱을 준비하는 방법에 대한 정보는 [앱 보호 정책용 기간 업무 앱 준비](../apps-prepare-mobile-application-management.md)를 참조하세요.
- Microsoft/타사 앱의 경우: 이러한 앱의 최신 버전을 사용자에게 배포하고 있는지 확인합니다.

SDK에 대한 이 변경 내용을 포함하려면 설명서 또는 개발자 지침도 업데이트해야 합니다.

#### <a name="additional-information"></a>추가 정보
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management
