---
title: 파일 포함
description: 파일 포함
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 1073a38da8a5b2467b1ff8c97b32b93f92e34e4c
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454133"
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
