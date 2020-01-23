---
title: Microsoft Intune에 Windows 10용 Microsoft Edge 추가
titleSuffix: ''
description: Microsoft Intune에 Windows용 Microsoft Edge를 추가하는 방법에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 42f1c8fae156eaf08203f4a88cad8433749940ac
ms.sourcegitcommit: b6fe084b0419b3c9d456a8b0439b00f8c784db23
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2020
ms.locfileid: "76294798"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>Microsoft Intune에 Windows 10용 Microsoft Edge 추가

앱을 배포, 구성, 모니터링 또는 보호하려면 앱을 Intune에 추가해야 합니다. 사용 가능한 [앱 유형](~/apps/apps-add.md#app-types-in-microsoft-intune) 중 하나는 Microsoft Edge ‘버전 77 이상’입니다.  Intune에서 이 앱 유형을 선택하면 Windows 10을 실행하고 직접 관리하는 디바이스에 Microsoft Edge ‘버전 77 이상’을 할당하고 설치할 수 있습니다. 

> [!IMPORTANT]
> 이 앱 유형은 Windows 10용 안정, Beta 및 Dev 채널을 제공하는 **공개 미리 보기**입니다. 배포는 영어(EN)로만 가능하지만 최종 사용자가 브라우저의 **설정** > **언어**에서 표시 언어를 변경할 수 있습니다. Microsoft Edge는 시스템 컨텍스트 및 유사한 아키텍처(x86 OS의 x86 앱 및 x64 OS의 x64 앱)에 설치된 Win32 앱입니다. Intune은 기존의 모든 Microsoft Edge 설치를 검색합니다. 사용자 컨텍스트에 설치된 경우 시스템 설치가 덮어씁니다. 시스템 컨텍스트에 설치된 경우 설치 성공이 보고됩니다. 또한 Microsoft Edge의 자동 업데이트는 기본적으로 **On** 상태이며 Microsoft Edge는 제거할 수 없습니다.

> [!NOTE]
> Microsoft Edge ‘버전 77 이상’은 macOS에서도 사용할 수 있습니다. 
> 
> 작업 공간 연결 컴퓨터에는 Microsoft Edge의 기본 제공 애플리케이션 배포를 사용할 수 없습니다. 기본 제공 애플리케이션 배포에는 AAD 조인 디바이스용으로만 존재하는 Intune 관리 확장이 필요합니다. **앱**에 업로드된 *.msi*를 사용하여 Microsoft Edge *버전 77 이상*을 배포할 수 있습니다. [Microsoft Intune에 Windows 기간 업무 앱 추가](~/apps/lob-apps-windows.md)를 참조하세요.

## <a name="prerequisites"></a>전제 조건
- Windows 10 RS2 이상이 필요합니다.
- 사용자 컨텍스트의 모든 채널에 대한 Microsoft Edge *버전 77 이상*의 미리 설치된 버전은 시스템 컨텍스트에서 설치된 Edge가 덮어씁니다.

## <a name="configure-the-app-in-intune"></a>Intune에서 앱 구성
다음 단계를 사용하여 Microsoft Edge 버전 77 이상을 Intune에 추가할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **Microsoft Edge 버전 77 이상** 아래 **앱 유형**에서 **Windows 10**을 선택합니다.

## <a name="configure-app-information"></a>앱 정보 구성
이 단계에서는 이 앱 배포에 대한 정보를 제공합니다. 이 정보를 통해 Intune에서 앱을 식별하며 사용자가 회사 포털에서 앱을 찾을 수 있습니다.

1. **앱 정보**를 클릭하여 **앱 정보** 창을 표시합니다.
2. **앱 정보** 창에서 이 앱 배포에 대한 정보를 제공합니다. 이 정보를 통해 Intune에서 앱을 식별하며 사용자가 회사 포털에서 앱을 찾을 수 있습니다.
    - **이름**: 회사 포털에 표시되는 앱의 이름을 입력합니다. 모든 이름이 고유한지 확인합니다. 동일한 앱 이름을 두 번 사용하는 경우에는 회사 포털에서 앱 중 하나만 사용자에게 표시됩니다.
    - **설명**: 앱에 대한 설명을 입력합니다. 예를 들어 설명에 대상 사용자를 나열할 수 있습니다.
    - **게시자**: Microsoft가 게시자로 표시됩니다.
    - **범주**: 필요한 경우, 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이 설정을 통해 사용자가 회사 포털을 찾아볼 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱을 눈에 띄게 표시하려면 이 옵션을 선택합니다.
    - **정보 URL**: 필요에 따라 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 이 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자**: Microsoft가 개발자로 표시됩니다.
    - **소유자**: Microsoft가 소유자로 표시됩니다.
    - **메모**: 선택 사항으로, 이 앱과 연결할 모든 메모를 입력합니다.
3. **확인**을 선택합니다.

## <a name="configure-app-settings"></a>앱 설정 구성
이 단계에서는 앱에 대한 설치 옵션을 구성합니다.

1. **앱 추가** 창에서 **앱 설정**을 선택합니다.
2. **앱 설정** 창의 **채널** 목록에서 **안정**, **Beta** 또는 **Dev**를 선택하여 앱을 배포할 Edge 채널을 결정합니다.
    - **안정** 채널은 엔터프라이즈 환경에서 광범위하게 배포하도록 권장되는 채널입니다. 6주마다 업데이트되는 각 릴리스는 Beta 채널의 향상된 기능을 통합합니다.
    - **Beta** 채널은 가장 안정적인 Microsoft Edge 미리 보기 환경이며 조직 내에서 전체 파일럿에 대한 가장 적합한 선택입니다. 6주마다 제공되는 주요 업데이트를 통해 각 릴리스는 Dev 채널의 학습 및 향상된 기능을 통합합니다.
    - **Dev** 채널은 Windows, Windows Server 및 macOS에서 엔터프라이즈 피드백을 받을 수 있습니다. 매주 업데이트되며 최신 향상된 기능과 수정이 포함됩니다.

    > [!NOTE]
    > 사용자가 회사 포털을 찾아볼 때 Microsoft Edge 브라우저 로고가 앱과 함께 표시됩니다.

3.  **확인**을 선택합니다.

## <a name="select-scope-tags-optional"></a>범위 태그 선택(선택 사항)
범위 태그를 사용하여 Intune에서 클라이언트 앱 정보를 볼 수 있는 사용자를 결정할 수 있습니다. 범위 태그에 대한 자세한 내용은 분산형 IT에 역할 기반 액세스 제어 및 범위 태그 사용을 참조하세요.
1.  **범위(태그)**  > **추가**를 선택합니다.
2.  **선택** 상자를 사용하여 범위 태그를 검색합니다.
3.  이 앱에 할당하려는 범위 태그 옆의 확인란을 선택합니다.
4.  **선택** > **확인**을 클릭합니다.

## <a name="add-the-app"></a>앱 추가
앱 구성을 완료한 후 **App 앱** 창에서 **추가**를 선택합니다. 

만든 앱이 앱 목록에 표시되며, 여기서 이 앱을 선택한 그룹에 할당할 수 있습니다. 

> [!NOTE]
> 현재 Microsoft Edge 배포의 할당을 취소하는 경우 해당 배포는 디바이스에서 유지됩니다.

## <a name="troubleshooting"></a>문제 해결
**Windows 10용 Microsoft Edge 버전 77 이상:**<br>
Intune은 Intune 관리 확장을 사용하여 할당된 Windows 10 디바이스에 Microsoft Edge 설치 관리자를 다운로드하고 배포한 다음, CDN에서 직접 Microsoft Edge 브라우저를 다운로드하고 설치하는 Microsoft Edge 설치 관리자에 배포 설정을 전달합니다. [Intune 관리 확장의 필수 구성 요소](~/apps/intune-management-extension.md#prerequisites)와 Azure 업데이트 서비스 및 CDN 액세스에 간략하게 설명된 모범 사례를 참조하여 네트워크 구성에서 Windows 10 디바이스가 이 위치에 액세스하도록 허용하는지 확인합니다. 또한 브라우저 설치를 위해 CDN에서의 설치 파일 액세스를 허용하려면 Windows 업데이트 엔드포인트로의 액세스를 허용해야 합니다. 자세한 내용은 [Windows 10 버전 1809의 연결 엔드포인트 관리 – Windows 업데이트](https://docs.microsoft.com/windows/privacy/manage-windows-1809-endpoints#windows-update)와 [Microsoft Intune에 대한 네트워크 엔드포인트](~/fundamentals/intune-endpoints.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계
- [그룹에 앱 할당](~/apps/apps-deploy.md)
