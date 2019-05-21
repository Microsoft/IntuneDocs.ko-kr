---
title: 파일 포함
description: 파일 포함
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: ffcef5b4d78856709f8563ee1f667ec7e5d993b3
ms.sourcegitcommit: d2e04a38e024b0f5afb0ca202823227de9da3ad1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65732624"
---
이러한 알림은 향후 Intune 변경 사항 및 기능을 준비하는 데 도움이 되는 중요한 정보를 제공합니다. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>회사 iOS 디바이스에서 Intune 회사 포털을 사용하여 설치 도우미를 인증하는 등록 워크플로를 변경합니다. <!-- 1927359 -->
인증을 위해 설치 도우미를 사용할 경우 Apple Configurator, Apple Business Manager, Apple School Manager 또는 Apple DEP(장비 등록 프로그램) 중 하나를 통해 iOS 디바이스를 등록하는 방법에 변경이 있을 예정입니다. 이 변경 사항은 사용자 선호도에 등록된 디바이스에만 적용됩니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
이 변경 내용이 롤아웃되면 Azure Portal의 Intune에 있는 등록 프로필이 업데이트되어 디바이스 인증 방법과 디바이스가 회사 포털 앱을 수신했는지 여부를 지정할 수 있습니다. 위에 나열된 방법을 통해 iOS 디바이스를 등록할 수 있는 워크플로가 개선될 것입니다. 

- 새 디바이스를 등록하고 설치 도우미를 사용하여 인증할 때 회사 포털 앱을 자동으로 배포할지 여부를 선택할 수 있습니다. 최종 사용자는 등록 과정에서 더이상 “디바이스 식별” 화면과 “디바이스 확인” 화면을 보지 않아도 됩니다.  
- Apple 디바이스 등록 방법 중 하나를 통해 설치 도우미에 이미 등록된 디바이스의 경우 조건부 액세스를 활성화하려면 조치를 취해야합니다. 회사 포털을 이러한 디바이스로 푸시하려면 특정 xml로 [애플리케이션 정책](https://aka.ms/enrollment_setup_assistant)을 구성해야 합니다.  이 방식으로 회사 포털을 푸시하려는 경우, 최종 사용자는 등록 과정에서 더이상 “디바이스 식별” 화면과 “디바이스 확인” 화면을 보지 않아도 됩니다. 
- 이 변경 사항이 롤아웃된 후, 언급된 앱 구성 프로필을 사용하여 회사 포털을 배포하지 않고 최종 사용자가 앱 스토어에서 회사 포털 앱을 다운로드한 경우 로그인할 수 있지만 오류 메시지가 표시됩니다. 조건부 액세스에 앱을 사용할 수 없습니다. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
수정된 워크플로를 사용하려는 경우 최종 사용자 지침을 업데이트하여 다음을 나타낼 수 있습니다.

- 최종 사용자는 등록 과정에서 위에서 언급한 두 화면을 더이상 보지 않아도 됩니다. 
- 앱 스토어에서 다운로드하지 않고 자동으로 배포될 때 회사 포털에 로그인해야 합니다. 

이 변경에 대비하여 필요한 경우 지금 앱 구성 정책을 생성하도록 선택할 수 있습니다. 이 새 워크플로를 롤아웃하는 경우, 콘솔에서 업데이트된 등록 프로필을 보게 될 것입니다. 이 롤아웃에 대해서는 메시지 센터를 통해 알려드리겠습니다. 그런 다음 최종 사용자가 설치 도우미로 인증하여 DEP를 통해 등록하고 조건부 액세스를 위해 회사 포털을 사용할 수 있도록 조치를 취해야 합니다.

#### <a name="additional-information"></a>추가 정보 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Android 회사 포털 앱을 최신 버전으로 업데이트 <!--4536963-->
Intune은 Android 회사 포털 앱에 대한 업데이트를 주기적으로 릴리스합니다. 2018년 11월에 Microsoft는 회사 포털 업데이트를 발표했습니다. 이 업데이트에는 Google의 기존 알림 플랫폼에서 FCM(Firebase Cloud Messaging)으로 변경할 수 있도록 지원하는 백엔드 스위치가 포함되어 있습니다. Google이 기존 알림 플랫폼을 사용 중지하고 FCM으로 이동하면 최종 사용자는 회사 포털 앱을 2018년 11월 릴리스 이상으로 업데이트해야 Google Play 스토어와 계속 통신할 수 있습니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
원격 측정 결과 회사 포털 버전이 5.0.4269.0 이전인 디바이스가 있습니다. 회사 포털 앱이 이 버전 이상이 설치되지 않은 경우 IT 팀에서 시작한 디바이스 작업(예: 삭제, 암호 재설정, 사용 가능한 애플리케이션 설치 및 필수 애플리케이션 설치, 인증서 등록)이 예상대로 작동하지 않을 수 있습니다. 장치가 Intune에 등록된 MDM인 경우 클라이언트 앱 - 검색된 앱으로 이동하여 회사 포털 버전과 사용자를 볼 수 있습니다. 회사 포털의 이전 버전을 선택하면 회사 포털을 업데이트하지 않은 최종 사용자가 어떤 디바이스를 가지고 있는지 확인할 수 있습니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
업데이트되지 않은 Android 디바이스의 최종 사용자에게 Google 플레이를 통해 회사 포털을 업데이트하도록 요청합니다. 사용자가 회사 포털 앱을 자동 업데이트하지 않은 경우 기술 지원팀에 알립니다. Google의 FCM 플랫폼 및 변경 사항에 대한 자세한 내용은 추가 정보 링크를 참조하시기 바랍니다.

#### <a name="additional-information"></a>추가 정보
https://firebase.google.com/docs/cloud-messaging/