---
title: Microsoft Intune에 macOS 사업 부문 앱을 추가하는 방법
titleSuffix: ''
description: Microsoft Intune에 macOS LOB(기간 업무) 앱을 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 112564e34f3f5c22bfed79f9c0e6810675ada341
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507191"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Microsoft Intune에 macOS LOB(사업 부문) 앱을 추가하는 방법

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

이 문서의 정보를 사용하면 Microsoft Intune에 macOS 사업 부문 앱을 추가하는 데 도움이 됩니다. 사업 부문 파일을 Microsoft Intune에 업로드하기 전에 *.pkg* 파일을 전처리하려면 외부 도구를 다운로드해야 합니다. *.pkg* 파일의 전처리는 macOS 디바이스에서 수행해야 합니다.

> [!NOTE]
> macOS 디바이스 사용자는 주식, 지도 같은 기본 제공 macOS 앱 중 일부를 제거할 수 있으나 Intune을 사용하여 해당 앱을 다시 배포할 수는 없습니다. 최종 사용자가 이러한 앱을 삭제하는 경우 앱 스토어로 이동하여 수동으로 다시 설치해야 합니다.

## <a name="before-your-start"></a>시작하기 전에

사업 부문 파일을 Microsoft Intune에 업로드하기 전에 외부 도구를 다운로드하여 다운로드한 도구를 실행 파일로 표시한 다음 *.pkg* 파일을 전처리해야 합니다. *.pkg* 파일의 전처리는 macOS 디바이스에서 수행해야 합니다. Mac용 Intune 앱 래핑 도구를 사용하여 Microsoft Intune에서 Mac 앱을 관리할 수 있도록 합니다.

> [!IMPORTANT]
> Apple Developer 계정에서 가져온 "Developer ID 설치 프로그램" 인증서를 사용하여 *.pkg*파일에 서명을 해야 합니다. macOS LOB 앱을 Microsoft Intune에 업로드하는 데는 *.pkg* 파일만 사용할 수 있습니다. *.dmg*와 다른 형식의 *.pkg*로의 변환은 지원되지 않습니다.
>

1. [Mac용 Intune 앱 래핑 도구](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac)를 다운로드합니다.

    > [!NOTE]
    > **Mac용 Intune 앱 래핑 도구**는 macOS 머신에서 실행되어야 합니다. 

2. 다음과 같이 다운로드한 도구를 실행 파일로 표시합니다.
   - 터미널 앱을 시작합니다.
   - `IntuneAppUtil`이 있는 위치로 디렉터리를 변경합니다.
   - 다음 명령을 실행하여 도구 실행 파일을 만듭니다.<br> 
       `chmod +x IntuneAppUtil`

3. **Mac용 Intune 앱 래핑 도구** 내에서 `IntuneAppUtil` 명령을 사용하여 *.intunemac* 파일에서 *.pkg* LOB 앱 파일을 래핑합니다.<br>

    macOS용 Microsoft Intune 앱 래핑 도구에 사용할 샘플 명령:
    
    - `IntuneAppUtil -h`<br>
    이 명령은 도구에 대한 사용 정보를 보여줍니다.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    이 명령은 *.pkg* LOB 앱 파일을 *.intunemac* 파일로 래핑합니다.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    이 명령은 생성된 *.intunemac* 파일에 대해 발견된 매개 변수 및 버전을 추출합니다.

## <a name="step-1---specify-the-software-setup-file"></a>단계 1 - 소프트웨어 설치 파일 지정

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드에서 **관리** > **앱**을 차례로 선택합니다.
5. 앱 목록 위에서 **추가**를 선택합니다.
6. **앱 추가** 창에서 **LOB(기간 업무) 앱**을 선택합니다.

## <a name="step-2---configure-the-app-package-file"></a>2단계: 앱 패키지 파일 구성

1. **앱 추가** 창에서 **앱 패키지 파일**을 선택합니다.
2. **앱 패키지 파일** 창에서 [찾아보기] 단추를 선택하고 확장명 *.intunemac*가 포함된 macOS 설치 파일을 선택합니다.
3. 작업이 끝나면 **확인**을 선택합니다.


## <a name="step-3---configure-app-information"></a>3단계 - 앱 정보 구성

1. **앱 추가** 창에서 **앱 정보**를 선택합니다.
2. **앱 정보** 창에서 앱의 세부 정보를 추가합니다. 선택한 앱에 따라 이 창의 일부 값이 자동으로 채워질 수 있습니다.
    - **이름** - 회사 포털에서 표시될 앱의 이름을 입력합니다. 사용하는 모든 앱 이름이 고유한지 확인합니다. 같은 앱 이름을 두 번 사용하는 경우에는 회사 포털에서 앱 중 하나만 사용자에게 표시됩니다.
    - **설명** - 회사 포털에서 사용자에게 표시될 앱의 설명을 입력합니다.
    - **게시자** - 앱의 게시자 이름을 입력합니다.
    - **최소 운영 체제** - 목록에서 앱을 설치할 수 있는 최소 운영 체제 버전을 선택합니다. 이전 버전의 운영 체제를 사용하는 디바이스에 앱을 할당할 경우 앱이 설치되지 않습니다.
    - **카테고리** - 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이렇게 하면 사용자가 회사 포털을 찾아볼 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시** - 사용자가 앱을 찾을 때 회사 포털의 기본 페이지에서 앱이 눈에 띄게 표시됩니다.
    - **정보 URL** - 필요에 따라 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인 정보 URL** - 필요에 따라 이 앱에 대한 개인 정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자** - 필요에 따라 앱 개발자의 이름을 입력합니다.
    - **소유자** - 필요에 따라 이 앱의 소유자 이름을 입력합니다(예: **HR 부서**).
    - **메모** - 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고** - 앱과 연결된 아이콘을 업로드합니다. 사용자가 회사 포털을 찾아볼 때 이 아이콘이 앱과 함께 표시됩니다.
3. 작업이 끝나면 **확인**을 선택합니다.

## <a name="step-4---finish-up"></a>4단계 - 끝내기

1. **앱 추가** 창에서 앱의 세부 정보가 올바른지 확인합니다.
2. **추가**를 선택하여 Intune에 앱을 업로드합니다.

만든 앱이 앱 목록에 표시됩니다. 이 목록에서 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

> [!NOTE]
> *.pkg* 파일에 여러 앱 또는 앱 설치 관리자가 포함되어 있는 경우 Microsoft Intune은 설치된 모든 앱이 디바이스에서 발견될 경우에만 ‘앱’이 성공적으로 설치되어 있다고 보고합니다. 

## <a name="step-5---update-a-line-of-business-app"></a>5단계 - 기간 업무(line-of-business) 앱 업데이트

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Intune 서비스에서 새 *.pkg* 파일을 디바이스에 성공적으로 배포하려면 *.pkg* 패키지의 *packageinfo* 파일에 있는 `version` 및 `CFBundleVersion` 문자열을 증분해야 합니다.

## <a name="next-steps"></a>다음 단계

- 만든 앱은 앱 목록에 표시됩니다. 이제 선택한 그룹에 앱을 할당할 수 있습니다. 도움말은 [그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요.

- 앱의 속성 및 할당을 모니터링할 수 있는 방법에 대해 자세히 알아봅니다. 자세한 내용은 [앱 정보 및 할당을 모니터링하는 방법](apps-monitor.md)을 참조하세요.

- Intune에서 앱의 컨텍스트에 대해 자세히 알아봅니다. 자세한 내용은 [디바이스 및 앱 수명 주기 개요](../fundamentals/device-lifecycle.md)를 참조하세요.
