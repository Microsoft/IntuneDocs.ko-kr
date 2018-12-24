---
title: 앱 보호 정책을 사용하는 Android 앱
description: 이 항목에서는 앱 보호 정책을 통해 앱이 관리될 때 예상되는 결과를 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 06115170300909d1683f44e565161d189f345ab8
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188052"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Android 앱이 앱 보호 정책에 의해 관리될 때 예상되는 상황

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

이 아티클에서는 앱 보호 정책이 적용되는 앱에 대한 사용자 환경을 설명합니다. 앱 보호 정책은 사용자가 회사 계정을 사용하여 앱에 액세스하거나 회사의 비즈니스용 OneDrive 위치에 저장된 파일에 액세스하는 경우처럼 앱이 업무용으로 사용될 때만 적용됩니다.

##  <a name="access-apps"></a>앱 액세스

회사 포털 앱에는 Android 디바이스에서 앱 보호 정책과 관련된 모든 앱이 필요합니다.

Intune에 등록되지 않은 디바이스의 경우 회사 포털 앱을 디바이스에 설치해야 합니다. 그러나 사용자는 앱 보호 정책에 의해 관리되는 앱을 사용하기 위해 먼저 회사 포털 앱을 시작하거나 회사 포털 앱에 로그인해야 할 필요가 없습니다.

회사 포털 앱을 사용하면 Intune이 안전한 위치에서 데이터를 공유할 수 있습니다. 따라서 디바이스가 Intune에 등록되어 있지 않더라도 앱 보호 정책과 연결된 모든 앱에서는 회사 포털 앱을 사용해야 합니다.


##  <a name="use-apps-with-multi-identity-support"></a>다중 ID가 지원되는 앱 사용

앱 보호 정책은 앱을 업무용으로 사용할 때만 적용됩니다. 즉, 앱을 업무용으로 사용하는지 아니면 개인용으로 사용하는지에 따라 작동 방식이 달라질 수 있습니다.

예를 들어 사용자가 업무 데이터에 액세스하면 PIN 프롬프트가 표시됩니다. **Outlook 앱**에서는 사용자가 앱을 시작할 때 PIN을 입력하라는 메시지가 표시됩니다. **OneDrive 앱**에서는 사용자가 회사 계정을 입력할 때 PIN을 입력하라는 메시지가 표시됩니다. Microsoft **Word**, **PowerPoint** 및 **Excel**의 경우에는 사용자가 회사의 비즈니스용 OneDrive 위치에 저장된 문서에 액세스할 때 PIN을 입력하라는 메시지가 표시됩니다.

##  <a name="manage-user-accounts-on-the-device"></a>디바이스에서 사용자 계정 관리

다중 ID 응용 프로그램에서 사용자는 계정을 여러 개 추가할 수 있습니다.  Intune 앱은 하나의 관리 계정만을 지원합니다.  Intune 앱은 관리되지 않는 계정 수를 제한하지 않습니다.

응용 프로그램에 관리 계정이 있는 경우:
*   사용자가 두 번째 관리 계정을 추가하려고 시도한다면 어떤 관리 계정을 사용할 것인지 선택하라는 메시지가 표시됩니다.  다른 계정은 제거됩니다.
*   IT 관리자가 두 번째 기존 계정에 정책을 추가한다면 어떤 관리 계정을 사용할 것인지 선택하라는 메시지가 표시됩니다.  다른 계정은 제거됩니다.

여러 사용자 계정이 처리되는 방법을 더욱 상세하게 파악하려면 다음 예제 시나리오를 확인하세요.

사용자 A는 **회사 X** 및 **회사 Y**에서 일합니다. 사용자 A는 각 회사에 회사 계정을 보유하고 둘 다 Intune을 사용하여 앱 보호 정책을 배포합니다. **회사 X**는 **회사 Y**보다 **먼저** 앱 보호 정책을 배포합니다. **회사 X**와 연결된 계정은 앱 보호 정책을 가져오지만 회사 Y와 연결된 계정은 앱 보호 정책을 가져오지 않습니다. 회사 Y와 연결된 사용자 계정을 앱 보호 정책으로 관리하려는 경우에는 회사 X와 연결된 사용자 계정을 제거하고 회사 Y와 연결된 사용자 계정을 추가해야 합니다.
### <a name="add-a-second-account"></a>두 번째 계정 추가
####  <a name="android"></a>Android
Android 디바이스를 사용하는 경우 기존 계정을 제거하고 새 계정을 추가하는 지침이 포함된 차단 메시지가 표시될 수 있습니다.  기존 계정을 제거하려면 **설정 &gt; 일반 &gt; 응용 프로그램 관리자 &gt; 회사 포털**로 이동합니다. 그런 후에 **데이터 지우기**를 선택합니다.

![오류 메시지 및 계정을 제거하는 지침의 스크린 샷](./media/Android_SwitchUser.png)

##  <a name="view-media-files-with-the-azure-information-protection-app"></a>Azure Information Protection 앱을 사용하여 미디어 파일 보기
Android 디바이스에서 회사 AV, PDF 및 이미지 파일을 보려면 [Azure Information Protection 앱](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)(이전 명칭은 Rights Management 공유 앱)을 사용합니다.

Google Play 스토어에서 이 앱을 다운로드합니다.  

다음 파일 형식이 지원됩니다.

* **오디오:** AAC LC, HE-AACv1(AAC+), HE-AACv2(향상된 AAC+), AAC ELD(향상된 낮은 지연 AAC), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **비디오:** H.263, H.264 AVC, MPEG-4 SP, VP8
* **이미지:** .jpg, .pjpg, .png, .ppng, .bmp, .pbmp, .gif, .pgif, .jpeg, .pjpeg
* **문서:** PDF, PPDF


|**pfile**|
|----|
|pfile은 암호화된 콘텐츠와 Azure Information Protection 라이선스를 캡슐화하는 보호된 파일용 일반 "래퍼" 형식입니다. pfile을 사용하면 모든 파일 형식을 보호할 수 있습니다.|

## <a name="next-steps"></a>다음 단계
[iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](end-user-mam-apps-ios.md)
