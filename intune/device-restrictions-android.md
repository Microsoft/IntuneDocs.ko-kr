---
title: Android에 대한 Microsoft Intune 장치 제한 설정
titlesuffix: ''
description: Android를 실행하는 장치에서 장치 설정 및 기능을 제어하는 데 사용할 수 있는 Intune 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 100742b378b30eab84b28c01728b2b382dd5155c
ms.sourcegitcommit: af0cc27b05bf0743f7d0970f5f3822f0aab346af
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190659"
---
# <a name="microsoft-intune-android-and-samsung-knox-standard-device-restriction-settings"></a>Microsoft Intune Android 및 Samsung Knox Standard 장치 제한 설정 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 Android를 실행하는 장치에 대해 구성할 수 있는 모든 Microsoft Intune 장치 제한 설정을 보여줍니다.

>[!TIP]
>원하는 설정을 사용할 수 없는 경우 [사용자 지정 프로필](custom-settings-android.md)을 사용하여 장치를 구성할 수 있습니다.

## <a name="general"></a>일반

- **카메라** - 장치 카메라를 사용할 수 있습니다.
- **복사 및 붙여넣기(Samsung Knox만 해당)** - 장치의 복사 및 붙여넣기 기능을 사용할 수 있습니다.
- **앱 간의 클립보드 공유(Samsung Knox만 해당)** - 클립보드를 사용하여 앱 간에 복사하여 붙여넣을 수 있습니다.
- **진단 데이터 제출(Samsung Knox만 해당)** - 사용자가 장치에서 진단 데이터를 제출하는 것을 중지합니다.
- **초기화(Samsung Knox만 해당)** - 사용자가 장치를 공장 기본 설정으로 복원할 수 있습니다.
- **지리적 위치(Samsung Knox만 해당)** - 장치에서 위치 정보를 활용할 수 있습니다.
- **전원 끄기(Samsung Knox만 해당)** - 사용자가 장치의 전원을 끌 수 있습니다.<br>사용하지 않도록 설정하면 **장치를 초기화하기 전 로그인 오류 발생 횟수**를 설정할 수 없습니다.
- **화면 캡처(Samsung Knox만 해당)** - 사용자가 화면 콘텐츠를 이미지로 캡처할 수 있습니다.
- **음성 도우미(Samsung Knox만 해당)** - 장치에서 음성 도우미 소프트웨어를 사용할 수 있습니다.
- **YouTube(Samsung Knox만 해당)** - 장치에서 YouTube 앱을 사용할 수 있습니다.
- **공유 장치(Samsung Knox만 해당)** - 관리되는 Samsung Knox Standard 장치를 공유 장치로 구성합니다. 이 모드에서는 최종 사용자가 Azure AD 자격 증명을 사용하여 장치 로그인/로그아웃을 수행할 수 있습니다. 장치는 사용 중인지 여부에 관계없이 관리되는 상태로 유지됩니다.<br>이 기능을 SCEP 인증서 프로필과 함께 사용하면 최종 사용자가 모든 사용자에 대해 동일한 앱 집합으로 장치를 공유할 수 있습니다. 단 자신의 SCEP 사용자 인증서를 사용해야 합니다.  사용자가 로그아웃하면 모든 앱 데이터가 지워집니다.  이 기능은 LOB 앱으로만 제한됩니다.
- **날짜 및 시간 변경 차단(Samsung Knox)** - 사용자가 장치의 날짜 및 시간 설정을 변경할 수 없도록 합니다. 

## <a name="password"></a>암호

- **암호** - 최종 사용자에게 장치에 액세스하려면 암호를 입력하도록 요구합니다.|Yes|Yes|

    > [!NOTE]
    > 삼성 Knox 장치는 MDM 등록 중에 4자리 PIN을 자동으로 요구합니다. 네이티브 Android 장치는 조건부 액세스와의 호환을 위해 자동으로 PIN을 요구할 수 있습니다.

- **최소 암호 길이** - 사용자가 구성해야 하는 암호의 최소 길이(4~16자)를 입력합니다.
- **화면이 잠기기 전까지 최대 비활성 시간(분)** - 장치가 자동으로 잠길 때까지 비활성 상태로 유지되는 시간(분)을 지정합니다.
- **장치를 초기화하기 전 로그인 오류 발생 횟수** - 장치를 초기화하기 전까지 허용되는 로그인 오류 횟수를 지정합니다.
- **암호 만료(일)** - 장치 암호를 변경해야 할 때까지의 기간(일)을 지정합니다.
-  **필수 암호 형식** - 필요한 암호 복잡도 수준과 생체 인식 장치 사용 가능 여부를 지정합니다. 다음 중에서 선택합니다.
    - **장치 기본값**
    - **낮은 보안 생체 인식**
    - **최소 숫자**
    - **복합 숫자** - “1111” 또는 “1234”와 같이 반복 또는 연속된 숫자는 허용되지 않습니다.<sup>1</sup>
    - **최소 알파벳**
    - **최소 영숫자**
    - **기호가 포함된 최소 영숫자**
- **이전 암호 다시 사용 방지** - 최종 사용자가 이전에 사용한 암호를 만드는 것을 중지합니다.
- **지문 잠금 해제(Samsung Knox만 해당)** - 지문을 사용하여 지원되는 장치의 잠금을 해제할 수 있습니다.
- **Smart Lock 및 기타 신뢰 에이전트** - 호환되는 Android 장치(Samsung Knox Standard 5.0 이상)에서 Smart Lock 기능을 제어할 수 있습니다. 신뢰 에이전트라고도 하는 이 전화 기능을 통해 장치가 신뢰할 수 있는 위치에 있는 경우 장치 잠금 화면 암호를 사용하지 않도록 설정하거나 무시할 수 있습니다. 예를 들어 장치가 특정 Bluetooth 장치에 연결되어 있거나 NFC 태그 근처에 있을 때 이 기능을 사용할 수 있습니다. 이 설정을 사용하면 사용자가 스마트 잠금 기능을 구성하는 것을 방지할 수 있습니다.
- **암호화** - 장치의 파일을 암호화해야 합니다.

    > [!NOTE]
    > 암호화 정책이 적용되는 경우 삼성 Knox 장치는 사용자에게 장치 암호에 대해 6자 복합 암호를 설정하도록 요구합니다.

<sup>1</sup> 이 설정을 장치에 할당하기 전에 해당 장치에서 회사 포털 앱을 최신 버전으로 업데이트하세요.

**복합 숫자** 설정을 구성한 다음 Android 5.0 이전 버전을 실행 중인 장치에 할당하는 경우 다음 동작이 적용됩니다.
- 회사 포털 앱에서 1704 이전 버전을 실행하는 경우 PIN 정책이 장치에 적용되지 않고 오류가 Azure Portal에 표시됩니다.
- 회사 포털 앱에서 1704 버전 이상을 실행하는 경우에는 단순 PIN만 적용할 수 있습니다. Android 5.0 이전 버전에서는 이 설정이 지원되지 않습니다. Azure Portal에 오류가 표시되지 않습니다.


## <a name="google-play-store"></a>Google Play 스토어

- **Google Play 스토어(Samsung Knox만 해당)** - 사용자가 장치에서 Google Play 스토어에 액세스할 수 있습니다.

## <a name="restricted-apps"></a>제한된 앱

제한된 앱 목록에서는 Android 및 Samsung Knox Standard 장치 둘 다에 대해 다음 목록 중 하나를 구성할 수 있습니다.

**금지된 앱** 목록 - 사용자가 설치하고 실행하는 경우 보고되는 Intune에서 관리되지 않는 앱을 나열합니다.
**승인된 앱** 목록 - 사용자가 설치할 수 있는 앱을 나열합니다. 호환성을 유지하려면 사용자가 다른 앱을 설치하지 않아야 합니다. Intune에서 관리되는 앱은 자동으로 허용됩니다.
제한된 앱 설정이 포함된 장치 프로필을 사용자 그룹에 할당해야 합니다.

목록을 구성하려면 **추가**를 클릭한 다음 원하는 이름, 앱 게시자(선택 사항) 및 앱 스토어의 앱 URL을 지정합니다.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>스토어의 앱에 대한 URL을 지정하는 방법

규격 및 비규격 앱 목록에 앱 URL을 지정하려면 다음 단계를 수행합니다.

[Google Play의 앱 섹션](https://play.google.com/store/apps)에서 사용하려는 앱을 검색합니다.

앱 설치 페이지를 열고 클립보드에 URL을 복사합니다. 이제 규격 또는 비규격 앱 목록에서 이 URL을 사용할 수 있습니다.

예: [Google Play의 앱 섹션](https://play.google.com/store/apps)에서 **Microsoft 플래너**를 검색합니다. URL 사용: **https://play.google.com/store/apps/details?id=com.microsoft.planner**.

### <a name="additional-options"></a>추가 옵션

**가져오기**를 클릭하여 목록을 csv 파일에서 가져올 수도 있습니다. <*앱 URL*>, <*앱 이름*>, <*앱 게시자*> 형식을 사용하거나 같은 형식의 제한된 앱 목록 내용이 포함된 csv 파일에서 **내보내기**를 클릭합니다.      

## <a name="browser"></a>브라우저

- **웹 브라우저(Samsung Knox만 해당)** - 장치의 기본 웹 브라우저 사용 가능 여부를 지정합니다.
- **자동 채우기(Samsung Knox만 해당)** - 웹 브라우저의 자동 채우기 기능을 사용할 수 있습니다.
- **쿠키(Samsung Knox만 해당)** - 장치 웹 브라우저가 쿠키를 사용할 수 있습니다.
- **Javascript(Samsung Knox만 해당)** - 장치 웹 브라우저가 Javascript를 사용할 수 있습니다.
- **팝업(Samsung Knox만 해당)** - 웹 브라우저에서 팝업 차단을 사용할 수 있습니다.

## <a name="allow-or-block-apps"></a>앱 허용 또는 차단

이러한 설정은 Samsung Knox Standard를 실행하는 장치에만 설치하거나 시작할 수 있는 앱을 지정하는 데 사용할 수 있습니다.
설치된 앱 중 장치 사용자에게 숨겨진 앱을 지정할 수도 있습니다. 사용자는 이러한 앱을 실행할 수 없습니다.

- **설치가 허용된 앱(Samsung Knox Standard만 해당)**
- **시작이 차단된 앱(Samsung Knox Standard만 해당)**
- **사용자에게 숨겨진 앱(Samsung Knox Standard만 해당)**

각 설정에 대해 다음 중 하나를 사용하여 앱 목록을 구성합니다.

- **패키지 이름으로 앱 추가** - 주로 LOB(기간 업무) 앱에 사용합니다. 앱 이름과 앱 패키지 이름을 입력합니다.
- **URL로 앱 추가** - 앱 이름과 Google Play 스토어의 해당 URL을 입력합니다.
- **관리되는 앱 추가** - Intune으로 관리하는 앱 목록에서 필요한 앱을 선택합니다.

## <a name="cloud-and-storage"></a>클라우드 및 저장소

- **Google 백업(Samsung Knox만 해당)** - Google 백업을 사용할 수 있습니다.
- **Google 계정 자동 동기화(Samsung Knox만 해당)** - Google 계정 설정을 자동으로 동기화할 수 있습니다.
- **이동식 저장소(Samsung Knox만 해당)** - 장치에서 SD 카드와 같은 이동식 저장소를 사용할 수 있습니다.
- **저장소 카드의 암호화(Samsung Knox만 해당)** - 장치 저장소 카드를 암호화해야 하는지 여부를 지정합니다.

## <a name="cellular-and-connectivity"></a>셀룰러 및 연결

- **데이터 로밍(Samsung Knox만 해당)** - 장치가 셀룰러 네트워크에 있을 때 데이터 로밍을 사용할 수 있습니다.
- **SMS/MMS 메시지(Samsung Knox만 해당)** - 장치에서 SMS 및 MMS 메시지를 사용할 수 있습니다.
- **음성 전화 걸기(Samsung Knox만 해당)** - 장치에서 음성 전화 걸기 기능을 사용하거나 사용하지 않도록 설정합니다.
- **음성 로밍(Samsung Knox만 해당)** - 장치가 셀룰러 네트워크에 있을 때 음성 로밍을 사용할 수 있습니다.
- **Bluetooth(Samsung Knox만 해당)** - 장치에서 Bluetooth를 사용할 수 있습니다.
- **NFC(Samsung Knox만 해당)** - 지원되는 장치에서는 작업에서 근거리 통신을 사용할 수 있습니다.
- **Wi-Fi(Samsung Knox만 해당)** - 장치에서 Wi-Fi 기능을 사용할 수 있습니다.
- **Wi-Fi 테더링(Samsung Knox만 해당)** - 장치에서 Wi-Fi 테더링을 사용할 수 있습니다.

## <a name="kiosk"></a>키오스크

키오스크 설정은 Samsung Knox Standard 장치와 Intune을 사용하여 관리하는 앱에만 적용됩니다.

- **관리되는 앱 선택** - 다음 옵션 중 하나를 선택하여 장치가 키오스크 모드일 때 실행할 수 있는 관리되는 앱을 하나 이상 추가합니다. 다른 앱은 장치에서 실행할 수 없습니다. 장치가 키오스크 모드인 경우 사전 설치된 브라우저는 실행하도록 허용된 앱으로 정의될 수 없습니다. 브라우저가 필요한 경우 [Managed Browser](app-configuration-managed-browser.md)를 사용하는 것이 좋습니다.
    - **패키지 이름으로 앱 추가**
    - **URL로 앱 추가**
    - **관리되는 앱 추가**.
- **화면 절전 모드 단추** - 장치에서 화면 절전 모드 해제 단추를 사용하거나 사용하지 않도록 설정합니다.
- **볼륨 단추** - 장치에서 볼륨 단추를 사용하거나 사용하지 않도록 설정합니다.


## <a name="next-steps"></a>다음 단계

계속해서 [장치 제한 설정 구성 방법](device-restrictions-configure.md)의 지침을 활용하여 장치 제한 프로필을 만들고 할당하세요.
