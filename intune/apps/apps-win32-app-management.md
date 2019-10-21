---
title: Microsoft Intune에 Win32 앱 추가 및 할당
titleSuffix: ''
description: Microsoft Intune을 사용하여 Win32 앱을 추가, 할당 및 관리하는 방법을 알아봅니다. 이 항목에서는 Intune Win32 앱 제공 및 관리 기능에 대한 개요와 Win32 앱 문제 해결 정보를 제공합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21192d259de0711ad38fa35b294ea82c7d913292
ms.sourcegitcommit: fca2670142c083d7562c0a36547a6a451863e315
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72036504"
---
# <a name="intune-standalone---win32-app-management"></a>Intune 독립 실행형 - Win32 앱 관리

[Intune 독립 실행형](../fundamentals/mdm-authority-set.md)은 이제 더 나은 Win32 앱 관리 기능을 제공합니다. 클라우드로 연결된 고객은 Win32 앱 관리를 위한 Configuration Manager를 사용할 수 있지만, Intune 전용 고객은 Win32 LOB(사업 부문) 앱에 대한 보다 나은 관리 기능을 사용할 수 있습니다. 이 항목에서는 Intune Win32 앱 관리 기능과 문제 해결 정보에 대한 개요를 제공합니다.

> [!NOTE]
> 이 앱 관리 기능은 Windows 애플리케이션용 32비트 및 64비트 운영 체제 아키텍처를 모두 지원합니다.

> [!IMPORTANT]
> Win32 앱을 배포할 때 특히 다중 파일 Win32 앱 설치 프로그램을 사용하는 경우 [Intune 관리 확장](../apps/intune-management-extension.md)만 사용하는 것이 좋습니다. AutoPilot 등록 중에 Win32 앱과 기간 업무 앱 설치를 혼합하면 앱 설치에 실패할 수 있습니다.  

## <a name="prerequisites"></a>전제 조건

Win32 앱 관리를 사용하려면 다음 조건을 충족해야 합니다.

- Windows 10 버전 1607 이상(Enterprise, Pro 및 Education 버전)
- Windows 10 클라이언트의 필수 요건은 다음과 같습니다. 
  - 디바이스는 Azure AD에 조인되고 자동 등록되어야 합니다. Intune 관리 확장은 Azure AD 조인, 하이브리드 도메인 조인, 그룹 정책 등록 디바이스를 지원합니다. 
  > [!NOTE]
  > 그룹 정책 등록 시나리오의 경우 - 최종 사용자는 로컬 사용자 계정을 사용하여 AAD를 Windows 10 디바이스에 조인합니다. 사용자는 AAD 사용자 계정을 사용하여 디바이스에 로그온하고 Intune에 등록해야 합니다. PowerShell 스크립트 또는 Win32 앱에서 사용자 또는 디바이스를 대상으로 하는 경우 Intune은 Intune 관리 확장을 디바이스에 설치합니다.
- Windows 애플리케이션 크기는 앱당 8GB로 제한됩니다.

## <a name="prepare-the-win32-app-content-for-upload"></a>업로드할 Win32 앱 콘텐츠 준비

[Microsoft Win32 콘텐츠 준비 도구](https://go.microsoft.com/fwlink/?linkid=2065730)를 사용하여 Windows 클래식(Win32) 앱을 전처리합니다. 도구는 애플리케이션 설치 파일을 *.intunewin* 형식으로 변환합니다. 또한 이 도구는 Intune에 필요한 일부 특성을 검색하여 애플리케이션 설치 상태를 확인합니다. 앱 설치 관리자 폴더에서 이 도구를 사용하면 Intune 콘솔에서 Win32 앱을 만들 수 있습니다.

> [!IMPORTANT]
> [Microsoft Win32 콘텐츠 준비 도구](https://go.microsoft.com/fwlink/?linkid=2065730)는 *.intunewin* 파일을 만들 때 모든 파일과 하위 폴더를 압축합니다. *.intunewin* 파일에 도구 또는 다른 불필요한 파일 및 폴더가 포함되지 않도록 Microsoft Win32 콘텐츠 준비 도구를 설치 관리자 파일 및 폴더와 별도로 유지해야 합니다.

GitHub에서 [Microsoft Win32 콘텐츠 준비 도구](https://go.microsoft.com/fwlink/?linkid=2065730)를 zip 파일로 다운로드할 수 있습니다. 압축된 파일에는 **Microsoft-Win32-Content-Prep-Tool-master**라는 폴더가 있습니다. 이 폴더에는 준비 도구, 라이선스, 추가 정보 및 릴리스 노트가 포함되어 있습니다. 

### <a name="process-flow-to-create-intunewin-file"></a>.intunewin 파일을 만드는 프로세스 흐름

   ![.intunewin 파일을 만드는 프로세스 흐름](./media/apps-win32-app-management/prepare-win32-app.svg)

### <a name="run-the-microsoft-win32-content-prep-tool"></a>Microsoft Win32 콘텐츠 준비 도구 실행

명령 창에서 매개 변수 없이 `IntuneWinAppUtil.exe`를 실행하면 도구에서 필요한 매개 변수를 단계별로 입력하도록 안내합니다. 또는 다음과 같은 사용 가능한 명령줄 매개 변수를 기반으로 하여 매개 변수를 명령에 추가할 수 있습니다.

### <a name="available-command-line-parameters"></a>사용 가능한 명령줄 매개 변수 

|    **명령줄 매개 변수**    |    **설명**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    도움말    |
|    `-c <setup_folder>`     |    모든 설치 파일에 대한 폴더입니다. 이 폴더의 모든 파일은 *.intunewin* 파일로 압축됩니다.    |
|    `-s <setup_file>`     |    설치 파일(예: *setup.exe* 또는 *setup.msi*)    |
|    `-o <output_folder>`     |    생성된 *.intunewin* 파일의 출력 폴더    |
|    `-q`       |    자동 모드    |

### <a name="example-commands"></a>예제 명령

|    **명령 예**    |    **설명**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    이 명령은 도구에 대한 사용 정보를 보여줍니다.    |
|    `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q`    |    이 명령은 지정된 원본 폴더 및 설치 파일에서 `.intunewin` 파일을 생성합니다. MSI 설치 파일의 경우 이 도구는 Intune에 필요한 정보를 검색합니다. `-q`가 지정되면 명령이 자동 모드로 실행되고, 출력 파일이 이미 있으면 덮어씁니다. 또한 출력 폴더가 없으면 자동으로 생성됩니다.    |

*.intunewin* 파일을 생성하는 경우 참조해야 하는 모든 파일을 설치 폴더의 하위 폴더에 배치합니다. 그런 후, 상대 경로를 사용하여 필요한 특정 파일을 참조합니다. 예를 들면 다음과 같습니다.

**설치 원본 폴더:** *c:\testapp\v1.0*<br>
**라이선스 파일:** *c:\testapp\v1.0\licenses\license.txt*

상대 경로 *licenses\license.txt*를 사용하여 *license.txt* 파일을 참조하세요.

## <a name="create-assign-and-monitor-a-win32-app"></a>Win32 앱 만들기, 할당 및 모니터링

LOB(사업 부문) 앱과 마찬가지로 Win32 앱을 Microsoft Intune에 추가할 수 있습니다. 이 유형의 앱은 일반적으로 사내 또는 타사에서 작성됩니다. 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>Win32 앱을 Intune에 추가하는 프로세스 흐름

<img alt="Process flow to add a Win32 app to Intune" src="./media/apps-win32-app-management/add-win32-app.svg" width="500">

### <a name="add-a-win32-app-to-intune"></a>Intune에 Win32 앱 추가

다음 단계는 Windows 앱을 Intune에 추가할 수 있도록 지침을 제공합니다.

### <a name="step-1-specify-the-software-setup-file"></a>1단계: 소프트웨어 설치 파일 지정

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **클라이언트 앱** > **앱** > **추가**을 선택합니다.
4. **앱 추가** 창에 제공된 드롭다운 목록에서 **Windows 앱(Win32)** 를 선택합니다.

    ![앱 추가 블레이드 - 형식 추가 드롭다운 상자 스크린샷](./media/apps-win32-app-management/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>2단계: 앱 패키지 파일 업로드

1. **앱 추가** 창에서 **앱 패키지 파일**을 선택하여 파일을 선택합니다. 앱 패키지 파일 창이 표시됩니다.

    ![앱 패키지 파일 블레이드 스크린샷](./media/apps-win32-app-management/apps-win32-app-02.png)

2. **앱 패키지 파일** 창에서 찾아보기 단추를 선택합니다. 그런 다음 확장명이 *.intunewin*인 Windows 설치 파일을 선택합니다.

    > [!IMPORTANT]
    > 최신 버전의 Microsoft Win32 콘텐츠 준비 도구를 사용해야 합니다. 최신 버전을 사용하지 않으면, 오래된 버전의 Microsoft Win32 콘텐츠 준비 도구를 사용하여 앱이 패키징되었다고 알리는 경고가 표시됩니다. 

3. 작업을 마쳤으면 **확인**을 선택합니다.

### <a name="step-3-configure-app-information"></a>3단계: 앱 정보 구성

1. **앱 추가** 창에서 **앱 정보**를 선택해 앱을 구성합니다.
2. **앱 정보** 창에서 다음 정보를 구성합니다. 이 창의 일부 값은 자동으로 채워질 수 있습니다.
    - **이름**: 회사 포털에 표시되는 앱 이름을 입력합니다. 동일한 앱 이름을 두 번 사용하는 경우 각 앱이 회사 포털에 표시됩니다.
    - **설명**: 앱에 대한 설명을 입력합니다. 설명은 회사 포털에 표시됩니다.
    - **게시자**: 앱 게시자의 이름을 입력합니다.
    - **범주**: 기본 제공 앱 범주를 하나 이상 선택하거나 직접 만든 범주를 선택합니다. 범주를 사용하면 사용자가 회사 포털을 탐색할 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱을 쉽게 확인할 수 있도록 표시합니다.
    - **정보 URL**: 필요에 따라 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에 표시됩니다.
    - **개발자**: 선택적으로, 앱 개발자의 이름을 입력합니다.
    - **소유자**: 선택적으로, 이 앱의 소유자 이름을 입력합니다. 예를 들어 **HR 부서** 등을 입력합니다.
    - **메모**: 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고**: 앱과 연결된 아이콘을 업로드합니다. 사용자가 회사 포털을 탐색할 때 이 아이콘이 앱과 함께 표시됩니다.
3. 작업을 마쳤으면 **확인**을 선택합니다.

### <a name="step-4-configure-app-installation-details"></a>4단계: 앱 설치 정보 구성
1. **앱 추가** 창에서 **프로그램**을 선택하여 앱에 대한 설치 및 제거 명령을 구성합니다.
2. 전체 설치 명령줄을 추가하여 앱을 설치합니다. 

    예를 들어 앱 파일 이름이 **MyApp123**이면 다음을 추가합니다.<br>
    `msiexec /p “MyApp123.msp”`<p>
    그리고 애플리케이션이 `ApplicationName.exe`이면 명령은 애플리케이션 이름 뒤에 패키지에서 지원하는 명령 인수(스위치)가 나옵니다. <br>예를 들면 다음과 같습니다.<br>
    `ApplicationName.exe /quiet`<br>
    위의 명령에서 `ApplicationName.exe` 패키지는 `/quiet` 명령 인수를 지원합니다.<p> 
    애플리케이션 패키지에서 지원하는 특정 인수에 대해서는 애플리케이션 공급업체에 문의하세요.

3. 앱의 GUID를 기반으로 앱을 제거하려면 전체 제거 명령줄을 추가합니다. 

    예:  `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > **사용자** 또는 **시스템** 컨텍스트에 설치되도록 Win32 앱을 구성할 수 있습니다. **사용자** 컨텍스트는 지정된 사용자만을 가리킵니다. **시스템** 컨텍스트는 Windows 10 디바이스의 모든 사용자를 가리킵니다.
    >
    > 최종 사용자는 Win32 앱을 설치할 디바이스에 로그인할 필요가 없습니다.
    > 
    > 앱이 사용자 컨텍스트에서 설치되도록 설정되고 디바이스의 최종 사용자에게 관리자 권한이 있는 경우 기본적으로 Win32 앱 설치 및 제거는 관리자 권한으로 실행됩니다.

4. 작업을 마쳤으면 **확인**을 선택합니다.

### <a name="step-5-configure-app-requirements"></a>5단계: 앱 요구 사항 구성

1. **앱 추가** 창에서 **요구 사항**을 선택하여 앱 설치 전에 디바이스가 충족시켜야 할 요구 사항을 구성합니다.
2. **요구 사항 규칙 추가** 창에서 다음 정보를 구성합니다. 이 창의 일부 값은 자동으로 채워질 수 있습니다.
    - **운영 체제 아키텍처**: 앱을 설치하는 데 필요한 아키텍처를 선택합니다.
    - **최소 운영 체제**: 앱을 설치하는 데 필요한 최소 운영 체제를 선택합니다.
    - **필요한 디스크 공간(MB)** : 앱을 설치할 시스템 드라이브에 필요한 사용 가능한 디스크 공간을 선택적으로 추가합니다.
    - **필요한 실제 메모리(MB)** : 앱을 설치하는 데 필요한 실제 메모리(RAM)를 선택적으로 추가합니다.
    - **필요한 최소 논리 프로세서 수**: 앱을 설치하는 데 필요한 최소 논리 프로세서 수를 선택적으로 추가합니다.
    - **필요한 최소 CPU 속도(MHz)** : 앱을 설치하는 데 필요한 최소 CPU 속도를 선택적으로 추가합니다.

3. **추가**를 클릭하여 **요구 사항 규칙 추가** 블레이드를 표시하고 추가 요구 사항 규칙을 구성합니다. **요구 사항 유형**을 선택하여 요구 사항에 대한 유효성을 검사하는 방법을 결정하는 데 사용할 규칙 유형을 선택합니다. 요구 사항 규칙은 파일 시스템 정보, 레지스트리 값 또는 PowerShell 스크립트를 기반으로 할 수 있습니다. 
    - **파일**: **파일**을 **요구 사항 유형**으로 선택하는 경우 요구 사항 규칙에서 파일이나 폴더, 날짜, 버전 또는 크기를 검색해야 합니다. 
        - **경로** - 검색할 파일 또는 폴더가 포함된 폴더의 전체 경로입니다.
        - **파일 또는 폴더** - 검색할 파일 또는 폴더입니다.
        - **속성** – 앱의 존재 여부를 확인하는 데 사용되는 규칙 유형을 선택합니다.
        - **64비트 클라이언트에서 32비트 앱과 연결됨** - 64비트 클라이언트의 32비트 컨텍스트에서 경로 환경 변수를 확장하려면 **예**를 선택합니다. 64비트 클라이언트의 64비트 컨텍스트에서 경로 변수를 확장하려면 **아니요**(기본값)를 선택합니다. 32비트 클라이언트는 항상 32비트 컨텍스트를 사용합니다.
    - **레지스트리**: **레지스트리**를 **요구 사항 유형**으로 선택하는 경우 요구 사항 규칙에서 값, 문자열, 정수 또는 버전에 따라 레지스트리 설정을 검색해야 합니다.
        - **키 경로** - 검색할 값을 포함하는 레지스트리 항목의 전체 경로입니다.
        - **값 이름** - 검색할 레지스트리 값의 이름입니다. 이 값이 비어 있으면 키에서 검색이 수행됩니다. 검색 방법이 파일 또는 폴더 존재 검색이 아닌 경우에는 키의 값(기본값)이 검색 값으로 사용됩니다.
        - **레지스트리 키 요구 사항** – 요구 사항 규칙의 유효성을 검사하는 데 사용되는 레지스트리 키 비교 유형을 선택합니다.
        - **64비트 클라이언트에서 32비트 앱과 연결됨** - 64비트 클라이언트에서 32비트 레지스트리를 검색하려면 **예**를 선택하세요. 64비트 클라이언트에서 64비트 레지스트리를 검색하려면 **아니요**(기본값)를 선택하세요. 32비트 클라이언트는 항상 32비트 레지스트리를 검색합니다.
    - **스크립트**: Intune 콘솔에서 사용할 수 있는 파일, 레지스트리 또는 다른 메서드를 기반으로 하여 요구 사항 규칙을 만들 수 없는 경우 **스크립트**를 **요구 사항 유형**으로 선택합니다.
        - **스크립트 파일** – PowerShell 스크립트 기반 요구 사항 규칙의 경우 존재하는 코드가 0이면 STDOUT를 더 자세히 검색합니다. 예를 들어 STDOUT를 1 값을 갖는 정수로 검색할 수 있습니다.
        - **64비트 클라이언트에서 32비트 프로세스로 스크립트 실행** - 64비트 클라이언트에서 32비트 프로세스로 스크립트를 실행하려면 **예**를 선택합니다. 64비트 클라이언트에서 64비트 프로세스로 스크립트를 실행하려면 **아니요**(기본값)를 선택합니다. 32비트 클라이언트는 32비트 프로세스로 스크립트를 실행합니다.
        - **로그온된 자격 증명을 사용하여 이 스크립트 실행**: 로그온된 디바이스 자격 증명**을 사용하여 스크립트를 실행하려면 **예**를 선택합니다.
        - **스크립트 서명 확인 강제 적용** - 스크립트가 신뢰할 수 있는 게시자에 의해 서명되었는지 확인하려면 **예**를 선택합니다. 그러면 경고 또는 프롬프트가 표시되지 않고 스크립트가 실행되도록 할 수 있습니다. 스크립트가 차단 해제된 상태로 실행됩니다. 서명 확인 없이 최종 사용자 확인으로 스크립트를 실행하려면 **아니요**(기본값)를 선택합니다.
        - **출력 데이터 형식 선택**: 요구 사항 규칙이 일치하는지 결정할 때 사용되는 데이터 형식을 선택합니다.
4. 작업을 마쳤으면 **확인**을 선택합니다.

### <a name="step-6-configure-app-detection-rules"></a>6단계: 앱 검색 규칙 구성

1. **앱 추가** 창에서 **검색 규칙**을 선택하여 앱의 존재를 검색하기 위한 규칙을 구성합니다.
2. **규칙 형식** 필드에서 앱의 존재를 검색하는 방법을 선택합니다. 검색 규칙을 수동으로 구성할 수도 있고, 사용자 정의 스크립트를 사용하여 앱의 존재를 검색할 수도 있습니다. 하나 이상의 검색 규칙을 선택해야 합니다. 

    > [!NOTE]
    > **검색 규칙** 창에서 여러 규칙을 추가하도록 선택할 수 있습니다. **모든** 규칙의 조건이 충족되어야 앱을 검색할 수 있습니다.
    >
    > Intune에서 앱이 디바이스에 존재하지 않음을 감지하면 Intune은 24시간 후에 앱을 다시 제공합니다. 이러한 작업은 필수 의도가 있는 대상 앱에 대해서만 수행됩니다.

    - **검색 규칙을 수동으로 구성** - 다음 규칙 유형 중 하나를 선택할 수 있습니다.
        1. **MSI** - MSI 버전 확인을 기반으로 확인합니다. 이 옵션은 한 번만 추가할 수 있습니다. 이 규칙 유형을 선택하면 다음 두 가지 설정이 가능합니다.
            - **MSI 제품 코드** - 앱에 유효한 MSI 제품 코드를 추가합니다.
            - **MSI 제품 버전 확인** - MSI 제품 코드 외에 MSI 제품 버전을 확인하려면 **예**를 선택합니다.
        2. **파일** - 파일 또는 폴더 검색, 날짜, 버전 또는 크기를 기준으로 확인합니다.
            - **경로** - 검색할 파일 또는 폴더가 포함된 폴더의 전체 경로입니다.
            - **파일 또는 폴더** - 검색할 파일 또는 폴더입니다.
            - **검색 방법** - 앱의 존재를 확인하는 데 사용되는 검색 방법 유형을 선택합니다.
            - **64비트 클라이언트에서 32비트 앱과 연결됨** - 64비트 클라이언트의 32비트 컨텍스트에서 경로 환경 변수를 확장하려면 **예**를 선택합니다. 64비트 클라이언트의 64비트 컨텍스트에서 경로 변수를 확장하려면 **아니요**(기본값)를 선택합니다. 32비트 클라이언트는 항상 32비트 컨텍스트를 사용합니다.
            
            **파일 기반 검색 예**
            1. 파일 존재 여부를 확인합니다.
         
                ![검색 규칙 창의 스크린샷 - 파일 존재](./media/apps-win32-app-management/apps-win32-app-03.png)
        
            2. 폴더 존재 여부를 확인합니다.
         
                ![검색 규칙 창의 스크린샷 - 폴더 존재](./media/apps-win32-app-management/apps-win32-app-04.png)
        
        3. **레지스트리** - 값, 문자열, 정수 또는 버전을 기반으로 확인합니다.
            - **키 경로** - 검색할 값을 포함하는 레지스트리 항목의 전체 경로입니다.
            - **값 이름** - 검색할 레지스트리 값의 이름입니다. 이 값이 비어 있으면 키에서 검색이 수행됩니다. 검색 방법이 파일 또는 폴더 존재 검색이 아닌 경우에는 키의 값(기본값)이 검색 값으로 사용됩니다.
            - **검색 방법** - 앱의 존재를 확인하는 데 사용되는 검색 방법 유형을 선택합니다.
            - **64비트 클라이언트에서 32비트 앱과 연결됨** - 64비트 클라이언트에서 32비트 레지스트리를 검색하려면 **예**를 선택하세요. 64비트 클라이언트에서 64비트 레지스트리를 검색하려면 **아니요**(기본값)를 선택하세요. 32비트 클라이언트는 항상 32비트 레지스트리를 검색합니다.
            
            **레지스트리 기반 검색 예**
            1. 레지스트리 키가 존재하는지 확인합니다.
            
                ![검색 규칙 창의 스크린샷 - 레지스트리 키가 존재함](./media/apps-win32-app-management/apps-win32-app-05.png)    
            
            2. 레지스트리 값이 존재하는지 확인합니다.
        
                ![검색 규칙 창의 스크린샷 - 레지스트리 값이 존재함](./media/apps-win32-app-management/apps-win32-app-06.png)    
        
            3. 레지스트리 값 문자열이 일치하는지 확인합니다.
        
                ![검색 규칙 창의 스크린샷 - 레지스트리 값 문자열이 일치함](./media/apps-win32-app-management/apps-win32-app-07.png)    
     
    - **사용자 지정 검색 스크립트 사용** - 이 앱을 검색하는 데 사용할 PowerShell 스크립트를 지정합니다. 
    
        1. **스크립트 파일** - 클라이언트에 앱이 있는지 검색하는 PowerShell 스크립트를 선택합니다. 스크립트가 모두 0 값 종료 코드를 반환하고 문자열 값을 STDOUT에 작성하면 앱이 검색됩니다.

        2. **64비트 클라이언트에서 32비트 프로세스로 스크립트 실행** - 64비트 클라이언트에서 32비트 프로세스로 스크립트를 실행하려면 **예**를 선택합니다. 64비트 클라이언트에서 64비트 프로세스로 스크립트를 실행하려면 **아니요**(기본값)를 선택합니다. 32비트 클라이언트는 32비트 프로세스로 스크립트를 실행합니다.

        3. **스크립트 서명 확인 강제 적용** - 스크립트가 신뢰할 수 있는 게시자에 의해 서명되었는지 확인하려면 **예**를 선택합니다. 그러면 경고 또는 프롬프트가 표시되지 않고 스크립트가 실행되도록 할 수 있습니다. 스크립트가 차단 해제된 상태로 실행됩니다. 서명 확인 없이 최종 사용자 확인으로 스크립트를 실행하려면 **아니요**(기본값)를 선택합니다.
    
            Intune 에이전트는 스크립트에서 결과를 확인합니다. 스크립트에 의해 표준 출력(STDOUT) 스트림, 표준 오류(STDERR) 스트림 및 종료 코드에 기록된 값을 읽습니다. 스크립트가 0이 아닌 값으로 끝나는 경우 스크립트는 실패하고 애플리케이션 검색 상태는 설치되지 않음 상태입니다. 종료 코드가 0이고 STDOUT에 데이터가 포함되어 있으면 애플리케이션 검색 상태는 설치됨 상태인 것입니다. 

            > [!NOTE]
            > 스크립트를 UTF-8로 인코딩하는 것이 좋습니다. 스크립트가 0 값으로 종료되면 스크립트 실행이 성공한 것입니다. 두 번째 출력 채널은 앱이 검색되었음을 나타냅니다. STDOUT 데이터는 앱이 클라이언트에서 발견되었음을 나타냅니다. STDOUT에서 특정 문자열을 찾지 않습니다.

        4. 규칙을 추가한 후 **추가** > **확인**을 선택합니다.

### <a name="step-7-configure-app-return-codes"></a>7단계: 앱 반환 코드 구성

1. **앱 추가** 창에서 **반환 코드**를 선택하여 앱 설치 재시도 동작 또는 설치 후 동작을 지정하는 데 사용되는 반환 코드를 추가합니다. 기본적으로 앱을 만드는 동안 반환 코드 항목이 추가됩니다. 그러나 추가 반환 코드를 추가하거나 기존 반환 코드를 변경할 수 있습니다. 
2. **반환 코드** 창에서 반환 코드를 추가하거나 기존 반환 코드를 수정합니다.
    - **실패** - 앱 설치 실패를 나타내는 반환 값입니다.
    - **하드 재부팅** - 하드 재부팅 반환 코드는 재부팅 없이 클라이언트에 다음 Win32 앱 설치를 허용하지 않습니다. 
    - **소프트 재부팅** - 소프트 재부팅 반환 코드는 클라이언트 재부팅을 요구하지 않고 다음 Win32 앱 설치를 허용합니다. 현재 애플리케이션의 설치를 완료하려면 재부팅해야 합니다.
    - **재시도** - 재시도 반환 코드 에이전트가 3회에 걸쳐 앱 설치를 시도합니다. 각 시도 사이의 대기 시간은 5분입니다. 
    - **성공** - 앱이 성공적으로 설치되었음을 나타내는 반환 값입니다.
3. 반환 코드 목록을 추가 또는 수정했으면 **확인**을 선택합니다.

### <a name="step-8-add-the-app"></a>8단계: 앱 추가

1. **앱 추가** 창에서 앱 정보를 올바르게 구성했는지 확인합니다.
2. **추가**를 선택하여 Intune에 앱을 업로드합니다.

### <a name="step-9-assign-the-app"></a>9단계: 앱 할당

1. 앱 창에서 **할당**을 선택합니다.
2. **그룹 추가**를 선택하여 앱과 관련된 **그룹 추가** 창을 엽니다.
3. 특정 앱의 경우 **할당 유형**을 선택합니다.
    - **등록된 디바이스에 사용 가능**: 사용자가 회사 포털 앱 또는 회사 포털 웹 사이트에서 앱을 설치합니다.
    - **필수**: 앱이 선택한 그룹의 디바이스에 설치됩니다.
    - **제거**: 앱이 선택한 그룹의 디바이스에서 제거됩니다.
4. **포함된 그룹**을 선택하고 이 앱을 사용할 그룹을 할당합니다.
5. **할당** 창에서 **확인**을 선택하여 포함된 그룹 선택을 완료합니다.
6. 이 앱 할당에서 영향을 주지 않도록 사용자 그룹을 제외하려면 **그룹 제외**를 선택합니다.
7. **그룹 추가** 창에서 **확인**을 선택합니다.
8. 앱 **할당** 창에서 **저장**을 선택합니다.

이 시점에서는 Win32 앱을 Intune에 추가하는 단계를 완료했습니다. 앱 할당 및 모니터링에 대한 자세한 내용은 [Microsoft Intune으로 그룹에 앱 할당](apps-deploy.md) 및 [Microsoft Intune으로 앱 정보 및 할당 모니터링](apps-monitor.md)을 참조하세요.

## <a name="app-dependencies"></a>앱 종속성

앱 종속성은 Win32 앱을 설치하기 전에 설치해야 하는 애플리케이션입니다. 다른 앱이 종속성으로 설치되도록 요구할 수 있습니다. 특히 디바이스는 Win32 앱을 설치하기 전에 종속 앱을 설치해야 합니다. 최대 100개의 종속성이 있으며, 여기에는 앱 자체뿐만 아니라 포함된 모든 종속성의 종속성도 포함됩니다. Win32 앱이 Intune에 추가되고 업로드된 후에만 Win32 앱 종속성을 추가할 수 있습니다. Win32 앱이 추가되면 Win32 앱에 대한 블레이드에 **종속성** 옵션이 표시됩니다. 

모든 Win32 앱 종속성도 Win32 앱이어야 합니다. 단일 MSI LOB 앱 또는 스토어 앱과 같은 다른 앱 유형에 따라 지원하지 않습니다.

앱 종속성을 추가하는 경우 앱 이름과 게시자를 기준으로 검색할 수 있습니다. 또한 앱 이름과 게시자에 따라 추가된 종속성을 정렬할 수도 있습니다. 이전에 추가된 앱 종속성은 이전에 추가된 앱 종속성 목록에서 선택할 수 없습니다. 

각 종속 앱을 자동으로 설치할지 여부를 선택할 수 있습니다. **자동 설치** 옵션은 기본적으로 각 종속성에 대해 **예**로 설정됩니다. 종속 앱을 자동으로 설치하면 종속 앱에서 사용자 또는 디바이스를 대상으로 하지 않더라도 Win32 앱을 설치하기 전에 Intune에서 종속성을 충족시키기 위해 앱을 디바이스에 설치합니다. 종속성에 재귀적 하위 종속성이 있을 수 있으며, 먼저 각 하위 종속성을 설치한 후에 주 종속성이 설치된다는 점에 유의해야 합니다. 또한 종속성 설치는 지정된 종속성 수준에서 설치 순서를 따르지 않습니다.

앱 종속성을 Win32 앱에 추가하려면 다음 단계를 사용합니다.

1. Intune에서 **클라이언트 앱** > **앱**을 차례로 선택하여 추가된 클라이언트 앱 목록을 확인합니다. 
2. 추가된 **Windows 앱(Win32)** 앱을 선택합니다. 
3. **종속성**을 선택하여 Win32 앱을 설치하기 전에 설치해야 하는 종속 앱을 추가합니다. 
4. **추가**를 클릭하여 앱 종속성을 추가합니다.
5. 종속 앱이 추가되면 **선택**을 클릭합니다.
6. **자동 설치** 아래에서 **예** 또는 **아니요**를 선택하여 종속 앱을 자동으로 설치할지 여부를 선택합니다.
7. **저장**을 클릭합니다.

최종 사용자는 Win32 앱 설치 프로세스의 일부로 종속 앱이 다운로드 및 설치되고 있음을 나타내는 Windows 알림 메시지를 볼 수 있습니다. 또한 종속 앱이 설치되지 않는 경우 최종 사용자는 일반적으로 다음 알림 중 하나를 볼 수 있습니다.
- 하나 이상의 종속 앱을 설치하지 못함
- 하나 이상의 종속 앱 요구 사항이 충족되지 않음
- 하나 이상의 종속 앱에서 디바이스 다시 부팅 보류 중

종속성을 **자동으로 설치**하지 않도록 선택하면 Win32 앱 설치가 시도되지 않습니다. 또한 앱 보고에서 `failed`라는 플래그가 종속성에 지정되었음을 보여 주고 실패 이유도 제공합니다. Win 32 앱 [설치 세부 정보](troubleshoot-app-install.md#win32-app-installation-troubleshooting)에 제공된 실패(또는 경고)를 클릭하여 종속성 설치 실패를 볼 수 있습니다. 

각 종속성은 Intune Win32 앱 재시도 논리(5분 동안 기다린 후 3회 설치 시도) 및 글로벌 재평가 일정을 준수합니다. 또한 종속성은 Win32 앱을 디바이스에 설치할 때만 적용됩니다. Win32 앱을 제거하는 경우 종속성이 적용되지 않습니다. 종속성을 삭제하려면 종속성 목록의 행 끝에 있는 종속 앱의 왼쪽에 있는 줄임표(...)를 클릭해야 합니다. 

## <a name="delivery-optimization"></a>배달 최적화

Windows 10 1709 이상 클라이언트는 Windows 10 클라이언트의 전송 최적화 구성 요소를 사용하여 Intune Win32 앱 콘텐츠를 다운로드합니다. 배달 최적화는 기본적으로 켜져 있는 피어 투 피어 기능을 제공합니다. 전송 최적화는 그룹 정책 및 Intune 디바이스 구성을 통해 구성할 수 있습니다. 자세한 내용은 [Windows 10 배달 최적화](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)를 참조하세요. 

## <a name="install-required-and-available-apps-on-devices"></a>디바이스에 사용 가능한 필수 앱 설치

최종 사용자는 사용 가능한 필수 앱 설치에 대한 Windows 알림 메시지를 받게 됩니다. 다음 이미지는 디바이스가 다시 시작될 때까지 앱 설치가 완료되지 않았다는 알림 메시지를 나타낸 것입니다. 

![앱 설치에 대한 Windows 알림 메시지 스크린샷](./media/apps-win32-app-management/apps-win32-app-08.png)    

다음은 디바이스에 앱 변경이 적용되고 있음을 최종 사용자에게 알리는 이미지입니다.

![앱이 변경되고 있음을 사용자에게 알리는 스크린샷](./media/apps-win32-app-management/apps-win32-app-09.png)    

## <a name="toast-notifications-for-win32-apps"></a>Win32 앱에 대한 알림 메시지 
필요한 경우 앱 할당마다 최종 사용자 알림 메시지를 표시하지 않을 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > 앱 선택 > **할당** > **포함 그룹**을 선택합니다. 

> [!NOTE]
> Win32 앱에 설치된 Intune 관리 확장은 등록되지 않은 디바이스에서 제거되지 않습니다. 관리자는 할당 제외를 활용하여 Win32 앱을 BYOD 디바이스에 제공하지 않을 수 있습니다.

## <a name="troubleshoot-win32-app-issues"></a>Win32 앱 문제 해결
클라이언트 컴퓨터에 대한 에이전트 로그는 일반적으로 `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`에 있습니다. `CMTrace.exe`를 이용하여 이러한 로그 파일을 볼 수 있습니다. *CMTrace.exe*는 [Configuration Manager 클라이언트 도구](https://docs.microsoft.com/sccm/core/support/tools)에서 다운로드할 수 있습니다. 

![클라이언트 컴퓨터의 에이전트 로그 스크린샷](./media/apps-win32-app-management/apps-win32-app-10.png)    

> [!IMPORTANT]
> LOB Win32 앱을 올바르게 설치하고 실행하도록 허용하려면 다음 디렉터리를 검사 대상에서 제외해야 합니다.<p>
> **X64 클라이언트 머신**:<br>
> *C:\Program Files(x86)\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **X86 클라이언트 머신**:<br>
> *C:\Program Files\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="detecting-the-win32-app-file-version-using-powershell"></a>PowerShell을 사용하여 Win32 앱 파일 버전 검색

Win32 앱 파일 버전을 검색하는 데 문제가 있는 경우 다음 PowerShell 명령을 사용하거나 수정합니다.

``` PowerShell

$FileVersion = [System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion
#The below line trims the spaces before and after the version name
$FileVersion = $FileVersion.Trim();
if ("<file version of successfully detected file>" -eq $FileVersion)
{
#Write the version to STDOUT by default
$FileVersion
exit 0
}
else
{
#Exit with non-zero failure code
exit 1
}
```

위의 PowerShell 명령에서 `<path to binary file>` 문자열을 Win32 앱 파일의 경로로 바꿉니다. 예제 경로는 다음과 유사합니다.<br>
`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

또한 `<file version of successfully detected file>` 문자열을 검색해야 하는 파일 버전으로 바꿉니다. 예제 파일 버전 문자열은 다음과 유사합니다.<br>
`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

Win32 앱의 버전 정보를 가져오기 위해 다음 PowerShell 명령을 사용할 수 있습니다.

``` PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

위의 PowerShell 명령에서 `<path to binary file>`을 파일 경로로 바꿉니다.

### <a name="additional-troubleshooting-areas-to-consider"></a>고려해야 할 추가 문제 해결 영역
- 대상을 확인하여 에이전트가 디바이스에 설치되어 있는지 확인합니다. 그룹을 대상으로 하는 Win32 앱 또는 그룹을 대상으로 하는 PowerShell 스크립트는 보안 그룹에 대한 에이전트 설치 정책을 만듭니다.
- OS 버전 확인 – Windows 10 1607 이상.  
- Windows 10 SKU 확인 - Windows 10 S 또는 S-mode가 사용으로 설정된 Windows 버전은 MSI 설치를 지원하지 않습니다.

Win32 앱 문제를 해결하는 방법에 대한 자세한 내용은 [Win32 앱 설치 문제 해결](troubleshoot-app-install.md#win32-app-installation-troubleshooting)을 참조하세요.

## <a name="next-steps"></a>다음 단계

- Intune의 앱을 추가하는 방법에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](apps-add.md)를 참조하세요.