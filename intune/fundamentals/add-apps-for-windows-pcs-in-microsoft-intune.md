---
title: Intune 소프트웨어 클라이언트를 실행하는 Windows PC에 앱 추가
titleSuffix: Microsoft Intune
description: 이 항목의 정보를 사용하여 배포하기 전에 Intune에 Windows PC용 앱을 추가하는 방법을 알아봅니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/29/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 23868303d598be1bc2e45f0852edfd3cf8338ab3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509149"
---
# <a name="add-apps-for-windows-pcs-that-run-the-intune-software-client"></a>Intune 소프트웨어 클라이언트를 실행하는 Windows PC에 앱 추가

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

이 항목의 정보를 사용하여 배포하기 전에 Intune에 앱을 추가하는 방법을 알아봅니다.

> [!IMPORTANT]
> 이 항목의 정보를 참조하면 Intune 소프트웨어 클라이언트를 사용하여 관리하는 Windows PC에 앱을 추가할 수 있습니다. 등록된 Windows PC 및 기타 모바일 디바이스용 앱을 추가하려면 [Microsoft Intune에 앱 추가](../apps/apps-add.md)를 참조하세요.

PC에 앱을 설치하려면 앱이 사용자 조작 없이 자동으로 설치될 수 있어야 합니다. 그렇지 않은 경우 설치가 실패합니다.

## <a name="additional-security-settings-for-windows-installer"></a>Windows 설치 관리자에 대한 추가 보안 설정
사용자가 앱 설치를 제어하도록 허용할 수 있습니다. 사용하도록 설정한 경우 그렇지 않으면 보안 위반으로 인해 중지될 수 있는 설치를 계속 진행하도록 허용합니다. 시스템에 모든 프로그램을 설치할 경우 Windows 설치 관리자가 상승된 권한을 사용하도록 명령할 수 있습니다. 또한 인덱싱될 WIP(Windows Information Protection) 항목 및 암호화되지 않은 위치에 저장된 WIP 항목에 대한 메타데이터를 사용할 수 있습니다. 정책을 사용하지 않을 때 WIP로 보호되는 항목은 인덱싱되지 않고 Cortana 또는 파일 탐색기의 결과에도 표시되지 않습니다. 이러한 옵션에 대한 기능은 기본적으로 사용할 수 없게 설정되어 있습니다. 

## <a name="add-the-app"></a>앱 추가
다음 절차에 따라 Intune 소프트웨어 게시자를 사용하여 앱 속성을 구성한 다음 클라우드 스토리지 공간에 앱을 업로드합니다.

1. [Microsoft Intune 관리자 콘솔](https://manage.microsoft.com)에서 **앱** &gt; **앱 추가**를 선택하여 Intune 소프트웨어 게시자를 시작합니다.

   > [!TIP]
   > 게시자를 시작하기 전에 Intune 사용자 이름과 암호를 입력해야 할 수도 있습니다.

2. 게시자의 **소프트웨어 설치** 페이지의 **디바이스에 이 소프트웨어를 사용할 수 있는 방법 선택**에서 **소프트웨어 설치 관리자**를 선택하고 다음을 지정합니다.

   - **소프트웨어 설치 관리자 파일 형식 선택**. 배포할 소프트웨어의 유형을 나타냅니다. Windows PC의 경우 **Windows Installer**를 선택합니다.
   - **소프트웨어 설치 파일의 위치 지정**. 설치 파일의 위치를 입력하거나 **찾아보기**를 선택하여 목록에서 위치를 선택합니다.
   - **동일한 폴더의 추가 파일 및 하위 폴더 포함**. Windows Installer를 사용하는 일부 소프트웨어의 경우 지원 파일이 필요합니다. 이러한 파일은 설치 파일과 같은 폴더 내에 있어야 합니다. 이러한 지원 파일도 배포하려는 경우 이 옵션을 선택합니다.

   예를 들어 Application.msi라는 앱을 Intune에 게시하려는 경우 페이지는 다음과 같은 모습으로 나타납니다. ![게시자의 소프트웨어 설정 페이지](./media/add-apps-for-windows-pcs-in-microsoft-intune/publisher-for-pc.png)

   이 설치 유형에서는 클라우드 스토리지 공간 중 일부를 사용합니다.

3. **소프트웨어 설명** 페이지에서 다음 항목을 구성합니다.

   > [!NOTE]
   > 사용하는 설치 관리자 파일에 따라 이러한 값 중 일부는 자동으로 입력되어 있거나 표시되지 않을 수도 있습니다.

   - **게시자**. 앱 게시자의 이름을 입력합니다.
   - **이름**. 회사 포털에 표시되는 앱의 이름을 입력합니다.<br />사용하는 모든 앱 이름이 고유한지 확인합니다. 같은 앱 이름을 두 번 사용하는 경우에는 회사 포털에서 앱 중 하나만 사용자에게 표시됩니다.
   - **설명**. 앱에 대한 설명을 입력합니다. 이 설명은 회사 포털에서 사용자에게 표시됩니다.
   - **소프트웨어 정보 URL**(선택 사항). 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
   - **개인정보취급방침 URL**(선택 사항). 이 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
   - **범주**(선택 사항). 기본 제공 앱 범주 중 하나를 선택합니다. 이렇게 하면 사용자가 회사 포털을 찾아볼 때 앱을 더 쉽게 찾을 수 있습니다.
   - **아이콘**(선택 사항). 앱과 연결할 아이콘을 업로드합니다. 사용자가 회사 포털을 찾아볼 때 이 아이콘이 앱과 함께 표시됩니다.

4. **요구 사항** 페이지에서 앱을 설치하려면 충족해야 하는 요구 사항을 선택합니다. 다음 중에서 선택합니다.

   - **아키텍처**. 이 앱을 설치할 수 있는 운영 체제(32비트, 64비트 또는 두 운영 체제 모두)를 선택합니다.
   - **운영 체제**. 이 앱을 설치할 수 있는 최소 운영 체제를 선택합니다.

5. **검색 규칙** 페이지에서 구성 중인 앱이 PC에 이미 설치되어 있는지 여부를 검색하는 규칙을 구성할 수 있습니다. 또는 기본 검색 규칙을 사용하여 이전에 설치된 앱 버전을 자동으로 덮어쓸 수 있습니다. 이 옵션은 Windows Installer에만 적용됩니다(.exe 파일에만 해당).

   구성할 수 있는 규칙은 다음과 같습니다.
   - **파일 있음**. 검색하려는 파일의 경로를 지정합니다. PC의 **%ProgramFiles%** (**Program Files**\&lt;경로&gt; and **Program Files (x86)** \&lt;경로&gt;를 검색함) 또는 **%SystemDrive%** (일반적으로 C 드라이브인 PC의 루트 드라이브에서 검색함)에서 검색할 수 있습니다.
   - **MSI 제품 코드가 존재합니다**. **찾아보기**를 클릭하여 검색할 Windows Installer(msi) 파일을 선택합니다.
   - <strong>레지스트리 키가 존재합니다</strong>. <strong>HKEY_LOCAL_MACHINE\</strong>으로 시작하는 레지스트리 키를 지정합니다. 32비트 및 64비트 레지스트리 경로를 모두 검색합니다. 지정한 키가 두 위치 중 하나에 있으면 검색 규칙이 충족됩니다.

   구성된 규칙을 충족하는 앱은 설치되지 않습니다.

6. **Windows Installer** 파일 형식(.msi 및 .exe)에 한해 **명령줄 인수** 페이지에서 설치 관리자에 대해 선택적인 명령줄 인수를 제공할지 여부를 선택합니다.
   다음 매개 변수는 Intune에서 자동으로 추가합니다.
   - .exe 파일의 경우 **/install**이 추가됩니다.
   - .msi 파일의 경우 **/quiet**가 추가됩니다.
   이러한 옵션은 앱 패키지를 만든 사람이 이 패키지에 대해 기능을 사용하도록 설정한 경우에만 사용할 수 있습니다.

7. **Windows Installer** 파일 형식(.exe만 해당)에 한해 **반환 코드** 페이지에서 관리되는 Windows PC에 앱을 설치할 때 Intune에서 해석하는 새 오류 코드를 추가할 수 있습니다.

   기본적으로 Intune는 업계 표준 반환 코드를 사용하여 앱 패키지 설치의 실패 또는 성공 여부를 보고합니다. 성공을 의미하는 **0**이나 다시 시작 성공을 나타내는 **3010** 코드가 표시됩니다. 이 목록에 고유한 반환 코드를 추가할 수도 있습니다. 반환 코드 목록을 지정하는 경우 앱 설치 시 목록에 없는 코드가 반환되면 해당 설치는 실패로 해석됩니다.

8. **요약** 페이지에서 지정한 정보를 검토합니다. 준비가 되면 **업로드**를 선택합니다.

9. **닫기**를 선택하여 완료합니다.

앱이 **앱** 작업 영역의 **앱** 노드에 표시됩니다.

## <a name="next-steps"></a>다음 단계

앱을 만들면 다음 단계는 배포입니다. 자세한 내용은 [Microsoft Intune을 사용하여 그룹에 앱 할당](../apps/apps-deploy.md)을 참조하세요.

Windows PC에 소프트웨어를 배포하기 위한 팁과 요령에 대해 자세히 알아보려면 [Support Tip: Best Practices for Intune Software Distribution to PC’s](https://support.microsoft.com/en-US/help/2583929)(지원 팁: PC에 Intune 소프트웨어 배포를 위한 모범 사례) 블로그 게시물을 참조하세요.
