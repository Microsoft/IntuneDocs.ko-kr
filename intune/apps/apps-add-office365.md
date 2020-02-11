---
title: Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 추가
titleSuffix: ''
description: Microsoft Intune을 사용하여 Windows 10 디바이스에 Office 365 앱을 설치하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86d02ae1277ff2fd6dfce9bf206628f5dc1c2a84
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755331"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 추가

앱을 할당, 모니터링, 구성 또는 보호하려면 앱을 Intune에 추가해야 합니다. 사용 가능한 [앱 유형](apps-add.md#app-types-in-microsoft-intune) 중 하나는 Windows 10 디바이스용 Office 365 앱입니다. Intune에서 이 앱 유형을 선택하면 Windows 10을 실행하는 디바이스에 Office 365 앱을 설치하고 배포할 수 있습니다. 또한 Microsoft Project Online 데스크톱 클라이언트 및 Microsoft Visio Online Plan 2에 대한 라이선스가 있는 경우 관련 앱을 할당하고 설치할 수 있습니다. 사용 가능한 Office 365 앱은 Azure 내부에서 Intune 콘솔의 앱 목록에 단일 항목으로 표시됩니다.

> [!NOTE]
> Office 365 ProPlus 라이선스를 사용하여 Microsoft Intune을 통해 배포된 Office 365 ProPlus 앱을 활성화해야 합니다. 현재 Office 365 Business 버전은 Intune에서 지원되지 않습니다.

## <a name="before-you-start"></a>시작하기 전에

> [!IMPORTANT]
> 최종 사용자 디바이스에 .msi Office 앱이 있으면 **MSI 제거** 기능을 사용하여 이러한 앱을 안전하게 제거해야 합니다. 이렇게 하지 않으면 Intune에서 제공하는 Office 365 앱이 설치되지 않습니다.

- 이러한 앱을 배포할 디바이스에서 Windows 10 크리에이터스 업데이트 이상을 실행하고 있어야 합니다.
- Intune에서는 Office 365 제품군에서 Office 앱을 추가하는 기능만 지원합니다.
- Intune에서 앱 제품군을 설치할 때 Office 앱이 열리면, 설치가 실패할 수 있으며 사용자는 저장되지 않은 파일의 데이터를 잃을 수 있습니다.
- 이 설치 방법은 Windows Home, Windows Team, Windows Holographic 또는 Windows Holographic for Business 디바이스에서 지원되지 않습니다.
- Intune은 Microsoft 스토어의 365 데스크톱 앱(Office Centennial 앱)을 이미 Intune으로 Office 365 앱을 배포한 디바이스에 설치하는 것을 지원하지 않습니다. 이 구성을 설치할 경우 데이터 손실이나 손상이 발생할 수 있습니다.
- 다수의 필수 또는 사용 가능한 앱 할당은 추가되지 않습니다. 이후 앱 할당은 기존에 설치된 앱 할당을 덮어씁니다. 예를 들어, 첫 번째 Office 앱 집합에 Word가 포함되어 있고 이후 Office 앱에는 포함되어 있지 않으면 Word가 제거됩니다. 이 조건은 모든 Visio 또는 Project 애플리케이션에 적용되지 않습니다.
- 현재 여러 개의 Office 365 배포는 지원되지 않습니다. 디바이스에 하나의 배포만 제공됩니다.
- **Office 버전** - Office의 32비트 또는 64비트 비전을 할당할지 여부를 선택합니다. 32비트 버전은 32비트 및 64비트 디바이스에 모두 설치할 수 있지만, 64비트 버전은 64비트 디바이스에만 설치할 수 있습니다.
- **최종 사용자 디바이스에서 MSI 제거** - 최종 사용자 디바이스에서 기존 Office .MSI 앱을 제거할지 여부를 선택합니다. 최종 사용자 디바이스에 기존 .MSI 앱이 있으면 설치가 실패합니다. 최종 사용자 디바이스에서 모든 Office(MSI) 앱을 제거하므로 제거할 앱은 **앱 제품군 구성**에서 설치하도록 선택한 앱으로만 제한되지 않습니다. 자세한 내용은 [Office 365 ProPlus로 업그레이드 시 기존 MSI 버전의 Office 제거](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)를 참조하세요. Intune에서 최종 사용자의 머신에 Office를 재설치하면 최종 사용자는 이전 .MSI Office 설치 프로그램과 함께 갖고 있던 것과 동일한 언어 팩을 자동으로 가져옵니다.

## <a name="select-the-office-365-suite-app-type"></a>Office 365 제품군 앱 유형 선택

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **앱 유형 선택** 창의 **Office 365 제품군** 섹션에서 **Windows 10**을 선택합니다.
4. **선택**을 클릭합니다. **Office 365 제품군 추가** 단계가 표시됩니다.


## <a name="step-1---app-suite-information"></a>1단계 - 앱 제품군 정보

이 단계에서는 앱 제품군에 대한 정보를 제공합니다. 이 정보를 사용하여 Intune에서 앱 제품군을 식별할 수 있으며, 사용자가 회사 포털에서 앱 제품군을 찾을 수도 있습니다.

1. **앱 제품군 정보** 페이지에서 기본값을 확인하거나 수정할 수 있습니다.
    - **제품군 이름**: 회사 포털에 표시되는 앱 제품군의 이름을 입력합니다. 사용하는 모든 제품군 이름이 고유한지 확인합니다. 같은 앱 패키지 이름이 두 번 나타나는 경우 앱 중 하나만 회사 포털에서 사용자에게 표시됩니다.
    - **제품군 설명**: 앱 제품군에 대한 설명을 입력합니다. 예를 들어 포함하도록 선택한 앱을 나열할 수 있습니다.
    - **게시자**: Microsoft가 게시자로 표시됩니다.
    - **범주**: 필요한 경우, 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이 설정을 통해 사용자가 회사 포털을 찾아볼 때 앱 패키지를 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱 제품군을 눈에 띄게 표시하려면 이 옵션을 선택합니다.
    - **정보 URL**: 필요에 따라 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 이 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자**: Microsoft가 개발자로 표시됩니다.
    - **소유자**: Microsoft가 소유자로 표시됩니다.
    - **메모**: 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고**: Office 365 로고는 사용자가 회사 포털을 찾을 때 앱과 함께 표시되는 로고입니다.
2. **다음**을 클릭하여 **앱 제품군 구성** 페이지를 표시합니다.

## <a name="step-2---option-1-configure-app-suite-using-the-configuration-designer"></a>2단계 - (**옵션 1**) 구성 디자이너를 사용하여 앱 제품군 구성 

**구성 설정 형식**을 선택하여 앱 설정을 구성하는 방법을 선택할 수 있습니다. 다음과 같은 설정 형식 옵션이 있습니다.
- 구성 디자이너
- XML 데이터 입력

**구성 디자이너**를 선택하면 **앱 추가** 창이 다음과 같은 세 가지 추가 설정 영역을 제공하도록 변경됩니다.
- 앱 제품군 구성
- 앱 제품군 정보
- 속성

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

1. **구성 앱 제품군** 페이지에서 **구성 디자이너**를 선택합니다.
   - **Office 앱 선택**: 드롭다운 목록에서 앱을 선택하여 디바이스에 할당할 표준 Office 앱을 선택합니다.
   - **다른 Office 앱 선택(라이선스 필요)** : 드롭다운 목록에서 앱을 선택하여 라이선스가 있고 디바이스에 할당할 추가 Office 앱을 선택합니다. 이러한 앱에는 Microsoft Project Online 데스크톱 클라이언트 및 Microsoft Visio Online Plan 2와 같은 사용이 허가된 앱이 포함됩니다.
   - **아키텍처**: Office ProPlus **32비트** 버전을 할당할지 **64비트** 버전을 할당할지 선택합니다. 32비트 버전은 32비트 및 64비트 디바이스에 모두 설치할 수 있지만, 64비트 버전은 64비트 디바이스에만 설치할 수 있습니다.
    - **업데이트 채널**: 디바이스에서 Office를 업데이트하는 방법을 선택합니다. 다양한 업데이트 채널에 대한 자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요. 다음 중에서 선택합니다.
        - **매월**
        - **매월(대상 지정됨)**
        - **반년마다**
        - **반년마다(대상 지정됨)**

        채널을 선택한 후 다음을 선택할 수 있습니다.
        - **다른 버전 제거**: 사용자 디바이스에서 다른 버전의 Office(MSI)를 제거하려면 **예**를 선택합니다. 최종 사용자 디바이스에서 기존 Office .MSI 앱을 제거하려면 이 옵션을 선택합니다. 최종 사용자 디바이스에 기존 .MSI 앱이 있으면 설치가 실패합니다. 최종 사용자 디바이스에서 모든 Office(MSI) 앱을 제거하므로 제거할 앱은 **앱 제품군 구성**에서 설치하도록 선택한 앱으로만 제한되지 않습니다. 자세한 내용은 [Office 365 ProPlus로 업그레이드 시 기존 MSI 버전의 Office 제거](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)를 참조하세요. Intune에서 최종 사용자의 머신에 Office를 재설치하면 최종 사용자는 이전 .MSI Office 설치 프로그램과 함께 갖고 있던 것과 동일한 언어 팩을 자동으로 가져옵니다. 
        - **설치할 버전**: 설치해야 하는 Office 버전을 선택합니다.
        - **특정 버전**: 위의 설정에서 **설치할 버전**으로 **특정** 버전을 선택한 경우 최종 사용자 디바이스에서 선택한 채널에 대해 특정 버전의 Office를 설치하도록 선택할 수 있습니다. 
            
            사용 가능한 버전은 시간이 지남에 따라 변경됩니다. 따라서 새 배포를 만들 때 사용 가능한 버전이 최신 버전일 수 있으며 이전 버전이 제공되지 않을 수 있습니다. 현재 배포에서는 이전 버전을 계속 배포하지만, 버전 목록은 채널별로 지속적으로 업데이트됩니다.
            
            고정된 버전을 업데이트하거나 다른 속성을 업데이트하고 사용 가능한 디바이스로 배포되는 디바이스의 경우, 디바이스를 체크 인할 때까지 이전 버전이 설치되어 있으면 보고 상태가 [설치됨]으로 표시됩니다. 디바이스가 체크 인되면 상태가 일시적으로 [알 수 없음]으로 변경되지만 사용자에게는 표시되지 않습니다. 사용자가 사용 가능한 최신 버전의 설치를 시작하면 상태가 [설치됨]으로 표시됩니다.
            
            자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요.
    - **공유 컴퓨터 인증 사용**: 여러 사용자가 컴퓨터를 공유할 경우 이 옵션을 선택합니다. 자세한 내용은 [Office 365의 공유 컴퓨터 인증 개요](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus)를 참조하세요.
    - **앱 최종 사용자 사용권 계약에 자동으로 동의**: 최종 사용자가 사용권 계약에 동의하도록 요구하지 않으려는 경우 이 옵션을 선택합니다. Intune에서 자동으로 계약에 동의합니다.
    - **언어**: Office는 최종 사용자 디바이스에 Windows와 함께 설치된 지원 언어로 자동으로 설치됩니다. 앱 패키지와 함께 추가 언어를 설치하려면 이 옵션을 선택합니다. <p></p>
        Intune을 통해 관리되는 Office 365 Pro Plus 앱의 추가 언어를 배포할 수 있습니다. 사용 가능한 언어 목록에는 언어 팩 **유형**(코어, 부분 및 언어 교정)이 포함되어 있습니다. Azure Portal에서 **Microsoft Intune** > **앱** > **앱 추가** > **추가**를 차례로 선택합니다. **앱 추가** 창의 **앱 유형** 목록에 있는 **Office 365 제품군** 아래에서 **Windows 10**을 선택합니다. **앱 제품군 설정** 창에서 **언어**를 선택합니다. 추가 정보는 [Office 365 ProPlus의 언어 배포 개요](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus)를 참조하세요.
2. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.

## <a name="step-2---option-2-configure-app-suite-using-xml-data"></a>2단계 - (**옵션 2**) XML 데이터를 사용하여 앱 제품군 구성 

**앱 제품군 구성** 페이지의 **설정 형식** 드롭다운 상자에서 **XML 데이터 입력** 옵션을 선택한 경우 사용자 지정 구성 파일을 사용하여 Office 앱 제품군을 구성할 수 있습니다.

![Office 365 구성 디자이너 추가](./media/apps-add-office365/apps-add-office365-01.png)

1. 추가된 구성 XML.
2. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.

XML 데이터 입력에 대한 자세한 내용은 [Office 배포 도구의 구성 옵션](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)을 참조하세요.

## <a name="step-3---select-scope-tags-optional"></a>3단계 - 범위 태그 선택(선택 사항)
범위 태그를 사용하여 Intune에서 클라이언트 앱 정보를 볼 수 있는 사용자를 결정할 수 있습니다. 범위 태그에 대한 자세한 내용은 [분산형 IT에 역할 기반 액세스 제어 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.

1. **범위 태그 선택**을 클릭하여 앱 제품군의 범위 태그를 선택적으로 추가합니다. 
2. **다음**을 클릭하여 **할당** 페이지를 표시합니다.

## <a name="step-4---assignments"></a>4단계 - 할당

1. 앱 제품군에 대해 **필수**, **등록된 디바이스에 사용 가능** 또는 **제거** 그룹 할당을 선택합니다. 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](~/fundamentals/groups-add.md) 및 [Microsoft Intune을 사용하여 그룹에 앱 할당](apps-deploy.md)을 참조하세요.
2. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다. 

## <a name="step-5---review--create"></a>5단계 - 검토 + 만들기

1. 앱 제품군에 대해 입력한 값과 설정을 검토합니다.
2. 완료되면 **만들기**를 클릭하여 Intune에 앱을 추가합니다.

    만든 Office 365 Windows 10 앱 제품군의 **개요 블레이드**가 표시됩니다.

## <a name="deployment-details"></a>배포 세부 정보

[Office CSP(Configuration Service Provider )](https://docs.microsoft.com/windows/client-management/mdm/office-csp)를 통해 Intune의 배포 정책을 대상 머신에 할당하면 최종 디바이스가 *officecdn.microsoft.com* 위치에서 설치 패키지를 자동으로 다운로드합니다. *Program Files* 디렉터리에 두 개의 디렉터리가 표시됩니다.

![Program Files 디렉터리의 Office 설치 패키지](./media/apps-add-office365/office-folder.png)

*Microsoft Office* 디렉터리에서 설치 파일이 저장된 위치에 새 폴더가 만들어집니다.

![Microsoft Office 디렉터리에 새로 만든 폴더](./media/apps-add-office365/created-folder.png)

*Microsoft Office 15* 디렉터리에 Office 간편 실행 설치 시작 관리자 파일이 저장됩니다. 할당 형식이 필요한 경우 설치가 자동으로 시작됩니다.

![설치 시작 관리자 파일을 실행하려면 클릭](./media/apps-add-office365/clicktorun-files.png)

O365 제품군의 할당이 필수로 구성된 경우 설치는 자동 모드로 설정됩니다. 설치에 성공하면 다운로드한 설치 파일이 삭제됩니다. 할당이 **사용 가능**으로 구성된 경우에는 최종 사용자가 설치를 수동으로 트리거할 수 있도록 Office 애플리케이션이 회사 포털 애플리케이션에 표시됩니다.

## <a name="troubleshooting"></a>문제 해결
Intune은 [Office 배포 도구](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool)를 사용하여 Office 365 ProPlus를 다운로드하고 [Office 365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks)을 사용하는 클라이언트 컴퓨터에 배포합니다. [Office 365 엔드포인트 관리](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints)에 설명된 모범 사례를 참조하여 네트워크 구성에서 클라이언트가 중앙 프록시를 통해 CDN 트래픽을 라우팅하지 않고 CDN에 직업 액세스하도록 허용하여 불필요한 대기 시간을 초래하지 않는지 확인합니다.

설치 또는 런타임 문제가 발생하는 경우 대상 디바이스에서 [Office 365용 Microsoft 지원 및 복구 도우미](https://diagnostics.office.com)를 실행합니다.

### <a name="additional-troubleshooting-details"></a>추가 문제 해결 세부 정보

디바이스에 O365 앱을 설치할 수 없는 경우 문제가 Intune 관련 또는 OS/Office 관련인지 여부를 확인해야 합니다. 디바이스의 *Program Files* 디렉터리에 두 개의 폴더(*Microsoft Office* 및 *Microsoft Office 15*)가 표시되면 Intune에서 배포를 성공적으로 시작했는지 확인할 수 있습니다. *Program Files*에 두 개의 폴더가 표시되지 않으면 다음 사항을 확인해야 합니다.

- 디바이스가 Microsoft Intune에 제대로 등록되어 있습니다. 
- 디바이스에 활성 네트워크 연결이 있습니다. 디바이스가 비행기 모드이거나, 꺼져 있거나, 서비스가 제공되지 않는 위치에 있는 경우에는 네트워크 연결이 설정될 때까지 정책이 적용되지 않습니다.
- Intune 및 Office 365 네트워크 요구 사항이 모두 충족되었으며 다음 문서에 따라 관련 IP 범위에 액세스할 수 있습니다.

  - [Intune 네트워크 구성 요구 사항 및 대역폭](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [Office 365 URL 및 IP 주소 범위](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- 올바른 그룹이 O365 앱 제품군에 할당되었습니다. 

또한 *C:\Program Files\Microsoft Office\Updates\Download* 디렉터리의 크기를 모니터링합니다. Intune 클라우드에서 다운로드한 설치 패키지는 이 위치에 저장됩니다. 크기가 증가하지 않거나 매우 느린 속도로만 증가하는 경우 네트워크 연결 및 대역폭을 다시 확인하는 것이 좋습니다.

Intune 및 네트워크 인프라가 모두 정상적으로 작동한다고 결론을 내리면 OS 관점에서 문제를 추가로 분석해야 합니다. 다음 조건을 확인합니다.

- 대상 디바이스는 Windows 10 크리에이터스 업데이트 이상에서 실행해야 합니다.
- Intune에서 애플리케이션을 배포하는 동안 기존 Office 앱이 열리지 않습니다.
- 기존 MSI 버전의 Office가 디바이스에서 제대로 제거되었습니다. Intune에서 Office MSI와 호환되지 않는 Office 간편 실행을 활용합니다. 이 동작은 이 문서에 자세히 설명되어 있습니다.<br>
  [동일한 컴퓨터에 간편 실행 및 Windows Installer로 설치된 Office는 지원되지 않음](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd)
- 로그인 사용자에게는 디바이스에 애플리케이션을 설치할 수 있는 권한이 있어야 합니다.
- Windows 이벤트 뷰어 로그 **Windows 로그** -> **애플리케이션**을 기반으로 문제가 없는지 확인합니다.
- 설치하는 동안 Office 설치 자세한 정보 표시 로그를 캡처합니다. 이를 수행하려면 다음 단계를 따르십시오.<br>
    1. 대상 머신에 Office 설치를 위한 자세한 정보 표시 로깅을 활성화합니다. 이 작업을 수행하려면 다음 명령을 실행하여 레지스트리를 수정합니다.<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. 대상 머신에 Office 365 제품군을 다시 배포합니다.<br>
    3. 약 15~20분 동안 기다린 후 **%temp%** 폴더, **%windir%\temp** 폴더로 차례로 이동하고 **수정된 날짜**별로 정렬한 다음, 재현 시간에 따라 수정된 *{Machine Name}-{TimeStamp}.log* 파일을 선택합니다.<br>
    4. 자세한 정보 표시 로그를 사용하지 않도록 설정하려면 다음 명령을 실행합니다.<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        자세한 정보 표시 로그를 통해 설치 프로세스에 대한 자세한 정보를 추가로 제공할 수 있습니다.

## <a name="errors-during-installation-of-the-app-suite"></a>앱 제품군 설치 중에 오류 발생

자세한 설치 로그를 보는 방법에 대한 자세한 내용은 [How to enable Office 365 ProPlus ULS logging](/office/troubleshoot/diagnostic-logs/how-to-enable-office-365-proplus-uls-logging)(Office 365 ProPlus ULS 로깅을 사용하도록 설정하는 방법)을 참조하세요.

다음 표에는 발생할 수 있는 일반적인 오류 코드와 해당 의미가 나와 있습니다.

### <a name="status-for-office-csp"></a>Office CSP 상태

| 상태 | 단계 | 설명 |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460(ERROR_TIMEOUT) | 다운로드 | Office 배포 도구를 다운로드하지 못함 |
| 13(ERROR_INVALID_DATA) | - | 다운로드된 Office 배포 도구의 서명을 확인할 수 없음 |
| CertVerifyCertificateChainPolicy의 오류 코드 | - | 다운로드된 Office 배포 도구의 인증 확인 실패 |
| 997 | WIP | 설치 |
| 0 | 설치 후 | 설치 성공 |
| 1603(ERROR_INSTALL_FAILURE) | - | 필수 구성 요소 확인 실패, 예: SxS(2016 MSI 설치 시 설치를 시도함) 버전 불일치 기타 |
| 0x8000ffff(E_UNEXPECTED) | - | 머신에 간편 실행 Office가 없을 때 제거를 시도함 |
| 17002 | - | 시나리오를 완료하지 못함(설치). 가능한 이유: 다른 설치가 설치를 취소함 다른 설치가 설치를 취소함 설치 시 디스크 공간 부족 알 수 없는 언어 ID |
| 17004 | - | 알 수 없는 SKU |


### <a name="office-deployment-tool-error-codes"></a>Office 배포 도구 오류 코드

| 시나리오 | 반환 코드 | UI | 참고 |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| 활성 간편 실행 설치가 없는 경우 제거 작업 | -2147418113, 0x8000ffff 또는 2147549183 | 오류 코드: 30088-1008 오류 코드: 30125-1011(404) | Office 배포 도구 |
| 설치된 MSI 버전이 있는 경우 설치 | 1603 | - | Office 배포 도구 |
| 사용자가 설치를 취소함 또는 다른 설치가 설치를 취소함 | 17002 | - | 간편 실행 |
| 32비트가 설치된 디바이스에 64비트 설치 시도. | 1603 | - | Office 배포 도구 반환 코드 |
| 알 수 없는 SKU 설치 시도(유효한 SKU만 전달해야 하므로 Office CSP에 대한 올바른 사용 사례가 아님) | 17004 | - | 간편 실행 |
| 공간 부족 | 17002 | - | 간편 실행 |
| 간편 실행 클라이언트를 시작하지 못함(예기치 않음) | 17000 | - | 간편 실행 |
| 간편 실행 클라이언트가 시나리오를 큐에 넣지 못함(예기치 않음) | 17001 | - | 간편 실행 |

## <a name="next-steps"></a>다음 단계

- 추가 그룹에 앱 제품군을 할당하려면 [그룹에 앱 할당](/intune-azure/manage-apps/deploy-apps)을 참조하세요.
