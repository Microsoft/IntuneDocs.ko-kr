---
title: Intune을 사용하여 디바이스에 Office 365 앱 설치
titlesuffix: ''
description: Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 더 간편하게 설치하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c98eb7795ca01db9a78b428faf433109928cff76
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182274"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당

이 앱 형식을 통해 관리하는 Windows 10 실행 디바이스에 Office 365 앱을 쉽게 할당할 수 있습니다. Microsoft Project Online 데스크톱 클라이언트 및 Microsoft Visio Pro for Office 365에 대한 라이선스가 있는 경우 관련 앱을 설치할 수 있습니다. 원하는 앱이 Intune 콘솔의 앱 목록에 하나의 항목으로 표시됩니다.

> [!NOTE]
> Office 365 ProPlus 라이선스를 사용하여 Microsoft Intune을 통해 배포된 Office 365 ProPlus 앱을 활성화해야 합니다. 현재 Office 365 Business 버전은 Intune에서 지원되지 않습니다.

## <a name="before-you-start"></a>시작하기 전에

> [!IMPORTANT]
> 최종 사용자 디바이스에 .msi Office 앱이 있으면 **MSI 제거** 기능을 사용하여 이러한 앱을 안전하게 제거해야 합니다. 이렇게 하지 않으면 Intune에서 제공하는 Office 365 앱이 설치되지 않습니다.

- 이러한 앱을 배포할 디바이스에서 Windows 10 크리에이터스 업데이트 이상을 실행하고 있어야 합니다.
- Intune에서는 Office 365 제품군에서 Office 앱을 추가하는 기능만 지원합니다.
- Intune에서 앱 제품군을 설치할 때 Office 앱이 열리면, 설치가 실패할 수 있으며 사용자는 저장되지 않은 파일의 데이터를 잃을 수 있습니다.
- 이 설치 방법은 Windows 10 S, Windows Home, Windows Team, Windows Holographic 또는 Windows Holographic for Business 디바이스에서 지원되지 않습니다.
- Intune은 Microsoft 스토어의 365 데스크톱 앱(Office Centennial 앱)을 이미 Intune으로 Office 365 앱을 배포한 디바이스에 설치하는 것을 지원하지 않습니다. 이 구성을 설치할 경우 데이터 손실이나 손상이 발생할 수 있습니다.
- 다수의 필수 또는 사용 가능한 앱 할당은 추가되지 않습니다. 이후 앱 할당은 기존에 설치된 앱 할당을 덮어씁니다. 예를 들어, 첫 번째 Office 앱 집합에 Word가 포함되어 있고 이후 Office 앱에는 포함되어 있지 않으면 Word가 제거됩니다. 이 조건은 모든 Visio 또는 Project 애플리케이션에 적용되지 않습니다.
- **Office 버전** - Office의 32비트 또는 64비트 비전을 할당할지 여부를 선택합니다. 32비트 버전은 32비트 및 64비트 디바이스에 모두 설치할 수 있지만, 64비트 버전은 64비트 디바이스에만 설치할 수 있습니다.
- **최종 사용자 장치에서 MSI 제거** - 최종 사용자 장치에서 기존 Office .MSI 앱을 제거할지 여부를 선택합니다. 최종 사용자 디바이스에 기존 .MSI 앱이 있으면 설치가 실패합니다. 최종 사용자 디바이스에서 모든 Office(MSI) 앱을 제거하므로 제거할 앱은 **앱 제품군 구성**에서 설치하도록 선택한 앱으로만 제한되지 않습니다. 자세한 내용은 [Office 365 ProPlus로 업그레이드 시 기존 MSI 버전의 Office 제거](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)를 참조하세요. Intune에서 최종 사용자의 머신에 Office를 재설치하면 최종 사용자는 이전 .MSI Office 설치 프로그램과 함께 갖고 있던 것과 동일한 언어 팩을 자동으로 가져옵니다.

## <a name="get-started"></a>시작

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드 창의 **관리** 아래에서 **앱**을 선택합니다.
5. **추가**를 선택합니다.
6. **앱 추가** 창의 **앱 유형** 목록에 있는 **Office 365 제품군** 아래에서 **Windows 10**을 선택합니다.

이제 앱 제품군을 구성할 수 있습니다.

## <a name="configure-the-app-suite"></a>앱 패키지 구성

디바이스에 할당할 Office 앱을 선택합니다.

1. **앱 추가** 창에서 **앱 제품군 구성**을 선택합니다.
2. **앱 제품군 구성** 창에서 장치에 할당할 표준 Office 앱을 선택합니다.  
    또한 Microsoft Project Online 데스크톱 클라이언트 및 Microsoft Visio Pro for Office 365에 대한 라이선스가 있는 경우 관련 앱을 설치할 수 있습니다.
3. **확인**을 선택합니다.

## <a name="configure-app-information"></a>앱 정보 구성

이 단계에서는 앱 제품군에 대한 정보를 제공합니다. 이 정보를 사용하여 Intune에서 앱 제품군을 식별할 수 있으며, 사용자가 회사 포털에서 앱 제품군을 찾을 수도 있습니다.

1. **앱 추가** 창에서 **앱 제품군 정보**를 선택합니다.
2. **앱 제품군 정보** 창에서 다음을 수행합니다.
    - **제품군 이름**: 회사 포털에 표시되는 앱 제품군의 이름을 입력합니다. 사용하는 모든 제품군 이름이 고유한지 확인합니다. 같은 앱 패키지 이름이 두 번 나타나는 경우 앱 중 하나만 회사 포털에서 사용자에게 표시됩니다.
    - **제품군 설명**: 앱 제품군에 대한 설명을 입력합니다. 예를 들어 포함하도록 선택한 앱을 나열할 수 있습니다.
    - **게시자**: Microsoft가 게시자로 표시됩니다.
    - **범주**: 필요한 경우, 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이 설정을 통해 사용자가 회사 포털을 찾아볼 때 앱 패키지를 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 이 옵션을 선택하면 사용자가 앱을 찾을 때 회사 포털의 기본 페이지에 앱 제품군이 눈에 띄게 표시됩니다.
    - **정보 URL**: 선택적으로, 이 앱에 대한 정보가 포함된 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인 정보 URL**: 선택적으로, 이 앱에 대한 개인 정보 관련 정보가 포함된 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자**: Microsoft가 개발자로 표시됩니다.
    - **소유자**: Microsoft가 소유자로 표시됩니다.
    - **메모**: 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고**: Office 365 로고는 사용자가 회사 포털을 찾을 때 앱과 함께 표시되는 로고입니다.
3. **확인**을 선택합니다.

## <a name="configure-app-settings"></a>앱 설정 구성

이 단계에서는 앱 패키지에 대한 설치 옵션을 구성합니다. 설정은 제품군에 추가한 모든 앱에 적용됩니다.

1. **앱 추가** 창에서 **앱 제품군 설정**을 선택합니다.
2. **앱 제품군 설정** 창에서 다음을 수행합니다.
    - **Office 버전**: Office의 32비트 또는 64비트 비전을 할당할지 여부를 선택합니다. 32비트 버전은 32비트 및 64비트 디바이스에 모두 설치할 수 있지만, 64비트 버전은 64비트 디바이스에만 설치할 수 있습니다.
    - **업데이트 채널**: 장치에서 Office를 업데이트하는 방법을 선택합니다. 다양한 업데이트 채널에 대한 자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요. 다음 중에서 선택합니다.
        - **매월**
        - **매월(대상 지정됨)**
        - **반년마다**
        - **반년마다(대상 지정됨)**

        채널이 선택되면 필요에 따라 **특정**을 선택하여 최종 사용자 디바이스에서 선택한 채널에 대한 특정 버전의 Office를 설치할 수 있습니다. 그런 다음, 사용할 Office의 **특정 버전**을 선택합니다.
        
        사용 가능한 버전은 시간이 지남에 따라 변경됩니다. 따라서 새 배포를 만들 때 사용 가능한 버전이 최신 버전일 수 있으며 이전 버전이 제공되지 않을 수 있습니다. 현재 배포에서는 이전 버전을 계속 배포하지만, 버전 목록은 채널별로 지속적으로 업데이트됩니다.
        
        고정된 버전을 업데이트하거나 다른 속성을 업데이트하고 사용 가능한 디바이스로 배포되는 디바이스의 경우, 디바이스를 체크 인할 때까지 이전 버전이 설치되어 있으면 보고 상태가 [설치됨]으로 표시됩니다. 디바이스가 체크 인되면 상태가 일시적으로 [알 수 없음]으로 변경되지만 사용자에게는 표시되지 않습니다. 사용자가 사용 가능한 최신 버전의 설치를 시작하면 상태가 [설치됨]으로 표시됩니다.
        
        자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요.

    - **최종 사용자 장치에서 MSI 제거** - 최종 사용자 장치에서 기존 Office .MSI 앱을 제거할지 여부를 선택합니다. 최종 사용자 디바이스에 기존 .MSI 앱이 있으면 설치가 실패합니다. 최종 사용자 디바이스에서 모든 Office(MSI) 앱을 제거하므로 제거할 앱은 **앱 제품군 구성**에서 설치하도록 선택한 앱으로만 제한되지 않습니다. 자세한 내용은 [Office 365 ProPlus로 업그레이드 시 기존 MSI 버전의 Office 제거](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)를 참조하세요. Intune에서 최종 사용자의 머신에 Office를 재설치하면 최종 사용자는 이전 .MSI Office 설치 프로그램과 함께 갖고 있던 것과 동일한 언어 팩을 자동으로 가져옵니다. 
    - **Automatically accept the app end user license agreement**(앱 최종 사용자 사용권 계약 자동으로 동의): 최종 사용자가 사용권 계약에 동의하도록 요구하지 않으려면 이 옵션을 선택합니다. Intune에서 자동으로 계약에 동의합니다.
    - **공유 컴퓨터 인증 사용**: 여러 사용자가 컴퓨터를 공유할 경우 이 옵션을 사용합니다. 자세한 내용은 [Office 365의 공유 컴퓨터 인증 개요](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus)를 참조하세요.
    - **언어**: Office는 최종 사용자 장치에 Windows와 함께 설치된 지원 언어로 자동으로 설치됩니다. 앱 패키지와 함께 추가 언어를 설치하려면 이 옵션을 선택합니다. <p></p>
    Intune을 통해 관리되는 Office 365 Pro Plus 앱의 추가 언어를 배포할 수 있습니다. 사용 가능한 언어 목록에는 언어 팩 **유형**(코어, 부분 및 언어 교정)이 포함되어 있습니다. Azure Portal에서 **Microsoft Intune** > **클라이언트 앱** > **앱** > **추가**를 차례로 선택합니다. **앱 추가** 블레이드의**앱 유형** 목록에 있는 **Office 365 제품군** 아래에서 **Windows 10**을 선택합니다. **앱 제품군 설정** 블레이드에서 **언어**를 선택합니다. 추가 정보는 [Office 365 ProPlus의 언어 배포 개요](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus)를 참조하세요.

## <a name="finish-up"></a>끝내기

작업을 완료하면 **앱 추가** 창에서 **추가**를 선택합니다. 만든 앱은 앱 목록에 표시됩니다.

## <a name="errors-during-installation-of-the-app-suite"></a>앱 제품군 설치 중에 오류 발생

다음 표에는 발생할 수 있는 일반적인 오류 코드와 해당 의미가 나와 있습니다.

### <a name="status-for-office-csp"></a>Office CSP 상태

||||
|-|-|-|
|상태|단계|설명|
|1460(ERROR_TIMEOUT)|다운로드|Office 배포 도구를 다운로드하지 못함|    
|13(ERROR_INVALID_DATA)|-|다운로드된 Office 배포 도구의 서명을 확인할 수 없음|
|CertVerifyCertificateChainPolicy의 오류 코드|-|다운로드된 Office 배포 도구의 인증 확인 실패|    
|997|WIP|설치|
|0|설치 후|설치 성공|    
|1603(ERROR_INSTALL_FAILURE)|-|필수 구성 요소 확인 실패, 예:<ul><li>SxS(2016 MSI 설치 시 설치를 시도함)</li><li>버전 불일치</li><li>기타</li></ul>|  
|0x8000ffff(E_UNEXPECTED)|-|머신에 간편 실행 Office가 없을 때 제거를 시도함|     
|17002|-|시나리오를 완료하지 못함(설치). 가능한 원인:<ul><li>사용자가 설치를 취소함</li><li>다른 설치가 설치를 취소함</li><li>설치 시 디스크 공간 부족</li><li>알 수 없는 언어 ID</li></ul>|
|17004|-|알 수 없는 SKU|   


### <a name="office-deployment-tool-error-codes"></a>Office 배포 도구 오류 코드

|||||
|-|-|-|-|
|시나리오|반환 코드|UI|참고|
|활성 간편 실행 설치가 없는 경우 제거 작업|-2147418113, 0x8000ffff 또는 2147549183|오류 코드: 30088-1008<br>오류 코드: 30125-1011(404)|Office 배포 도구|
|설치된 MSI 버전이 있는 경우 설치|1603|-|Office 배포 도구|
|사용자가 설치를 취소함 또는 다른 설치가 설치를 취소함|17002|-|간편 실행|
|32비트가 설치된 디바이스에 64비트 설치 시도.|1603|-|Office 배포 도구 반환 코드|
|알 수 없는 SKU 설치 시도(유효한 SKU만 전달해야 하므로 Office CSP에 대한 올바른 사용 사례가 아님)|17004|-|간편 실행|
|공간 부족|17002|-|간편 실행|
|간편 실행 클라이언트를 시작하지 못함(예기치 않음)|17000|-|간편 실행|
|간편 실행 클라이언트가 시나리오를 큐에 넣지 못함(예기치 않음)|17001|-|간편 실행|

## <a name="next-steps"></a>다음 단계

- 선택한 그룹에 앱을 할당하려면 [그룹에 앱 할당](/intune-azure/manage-apps/deploy-apps)을 참조하세요.
