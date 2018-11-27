---
title: 앱 보호 정책을 사용하는 Android 앱
titlesuffix: Microsoft Intune
description: 보호 정책이 있는 Android 앱에서 예상되는 상황을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6e38ac954f0b8c85b7127143c98f41bfe5497ef9
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179578"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Android 앱이 앱 보호 정책에 의해 관리될 때 예상되는 상황 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

보호 정책이 있는 Android 앱에서 예상되는 상황을 알아봅니다. 앱 보호 정책은 앱이 회사 컨텍스트에서 사용되는 경우에만 적용됩니다. 예를 들어 회사 계정을 사용하여 앱에 액세스할 때 또는 회사의 OneDrive 위치에 저장된 파일에 액세스할 때입니다.
##  <a name="accessing-apps"></a>앱 액세스

회사 포털 앱은 Android 장치의 모든 앱에 대해 앱 보호 정책을 갖추도록 요구합니다.

Intune에 등록 되지 않은 모든 장치에 회사 포털을 설치 합니다. 앱 보호 정책이 있는 앱을 사용하려면 사용자가 회사 포털 앱에 로그인을 할 필요가 없습니다.
회사 포털 앱을 사용하면 안전한 위치에서 데이터를 공유할 수 있습니다. 따라서 이는 등록 해제된 장치에 대해서도 요구하는 사항입니다.


##  <a name="using-apps-with-multi-identity-support"></a>다중 ID가 지원되는 앱 사용

사용자가 작업 관련 데이터에 액세스하려 할 때만 앱 보호 정책이 적용됩니다.  사용자가 사적 용도로 앱에 액세스하는 경우 다른 동작이 표시될 수 있습니다.

일부 앱은 다중 ID를 지원합니다. 사용자가 작업 데이터에 액세스할 경우 Intune만 앱 보호 정책을 적용합니다.  예를 들어 사용자는 PIN 프롬프트를 얻을 수 있습니다.  **Outlook 앱**에서 사용자가 앱을 시작하는 경우 프롬프트가 표시됩니다. **OneDrive 앱**에서는 사용자가 회사 계정을 입력할 때 프롬프트가 표시됩니다.  Microsoft **Word**, **PowerPoint** 및 **Excel**에서 프롬프트는 사용자가 회사의 OneDrive 문서에 액세스할 때 나타납니다.
##  <a name="managing-user-accounts-on-the-device"></a>장치에서 사용자 계정 관리

Intune은 장치 당 하나의 사용자 계정에 앱 보호 정책을 배포하도록 지원합니다.

* 사용 중인 앱에 따라 두 번째 사용자는 장치에서 차단될 수도 있고 차단되지 않을 수도 있습니다. 그러나 어떤 경우이든 앱 보호 정책을 가져오는 첫 번째 사용자만이 정책에 영향을 받습니다.

  * **Microsoft Word**, **Excel** 및 **PowerPoint**는 추가 사용자 계정에 대 한 액세스를 차단하지 않습니다. 그러나 해당 사용자 계정은 앱 보호 정책의 영향을 받지 않습니다.

  * **OneDrive 및 Outlook 앱**의 경우 회사 계정을 하나만 사용할 수 있습니다.  해당 앱에서는 여러 회사 계정의 추가가 차단됩니다.  그러나 사용자를 장치에서 제거한 다음, 해당 장치에 다른 사용자를 추가할 수 있습니다.


* 앱 보호 정책을 배포하기 전에 장치에는 기존 사용자 계정이 여러 개 있을 수 있습니다. 이 경우 앱 보호 정책이 배포되는 첫 번째 계정은 Intune 앱 보호 정책에서 관리합니다.


Intune에서 여러 사용자 계정을 어떻게 처리하는지 알고 싶으면 다음 예제 시나리오를 읽습니다.

사용자 A는 **회사 X** 및 **회사 Y**에서 일합니다. 사용자 A는 각 회사에 회사 계정을 보유하고 둘 다 Intune을 사용하여 앱 보호 정책을 배포합니다. **회사 X**는 **회사 Y**보다 **먼저** 앱 보호 정책을 배포합니다. **회사 X**와 연결된 계정은 앱 보호 정책을 가져오지만 회사 Y와 관련된 계정이 아닙니다. 회사 Y 사용자 계정이 앱 보호 정책에 의해 관리되게 하려면 사용자 A는 회사 X 사용자 계정을 제거해야 합니다.
### <a name="adding-a-second-account"></a>두 번째 계정 추가
####  <a name="android"></a>Android
또한 기존 계정을 제거하고 새 계정을 추가하는 프롬프트가 표시됩니다.  기존 계정을 제거하려면 **설정 &gt; 일반 &gt; 응용 프로그램 관리자 &gt; 회사 포털로 이동합니다. "데이터 지우기"를 선택합니다.**

![오류 메시지 및 계정을 제거하는 지침의 스크린 샷](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>Azure Information Protection 앱(이전에는 Rights Management 공유 앱)으로 미디어 파일 보기
Android 장치에서 회사 AV, PDF 및 이미지 파일을 보려면 [Azure Information Protection 앱](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)을 사용합니다.

Google Play 스토어에서 이 응앱을 다운로드합니다.  

다음 파일 형식이 지원됩니다.

* **오디오:** AAC LC, HE-AACv1(AAC+), HE-AACv2(향상된 AAC+), AAC ELD(향상된 낮은 지연 AAC), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE.
* **비디오:** H.263, H.264 AVC, MPEG-4 SP, VP8.
* **이미지:** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg.
* **문서:** PDF, PPDF

------------

|                                                                                 <strong>pfile</strong>                                                                                 |                                                                      <strong>텍스트</strong>                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pfile은 보호된 파일에 대한 일반 "래퍼" 형식입니다. 암호화된 콘텐츠 및 Azure Information Protection 라이선스를 캡슐화합니다. pfile을 사용하면 모든 파일 형식을 보호할 수 있습니다. | XML, CSV 등을 포함하는 텍스트 파일은 보호되는 경우에도 앱에서 열어서 볼 수 있습니다. 파일 형식: txt, ptxt, csv, pcsv, log, plog, xml, pxml |

---------------
## <a name="next-steps"></a>다음 단계
[iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>참고 항목
[Microsoft Intune으로 앱 보호 정책 만들기 및 배포](app-protection-policies.md)
