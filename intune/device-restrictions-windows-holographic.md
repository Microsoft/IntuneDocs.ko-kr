---
title: Windows Holographic Business 디바이스 설정 - Microsoft Intune - Azure | Microsoft Docs
description: 등록 취소, 지리적 위치, 암호, 앱 스토어에서 앱 설치, Microsoft Edge에서 쿠키 및 팝업, Windows Defender, 검색, 클라우드 및 스토리지, Bluetooth 연결, 시스템 시간 및 Azure에서 사용량 데이터를 포함하여 Windows Holographic for Business에 대한 Microsoft Intune에서 디바이스 제한 설정을 읽고 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: cdac4623c6c5c9e7258897e1536856e6b24492ea
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032013"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Intune를 사용하여 기능을 허용하거나 제한하는 Windows Holographic for Business 디바이스 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 문서에서는 Microsoft Hololens와 같은 Windows Holographic for Business 디바이스에서 제어할 수 있는 다양한 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로 이러한 설정을 사용하여 기능을 허용하거나 사용하지 않도록 설정하고, 보안을 제어할 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](device-restrictions-configure.md).

## <a name="general"></a>일반

- **수동 등록 취소** 디바이스에서 회사 계정을 수동으로 삭제할 수 있습니다.
- **Cortana**: Cortana 음성 지원을 허용하거나 허용하지 않습니다.
- **지리적 위치**: 디바이스에서 위치 서비스 정보를 사용할 수 있는지 여부를 지정합니다.

## <a name="password"></a>암호

- **암호**: 최종 사용자에게 디바이스에 액세스하려면 암호를 입력하도록 요구합니다.
- **디바이스가 유휴 상태에서 되돌아오는 경우 암호 필요**: 사용자가 암호를 입력해야 디바이스 잠금을 해제할 수 있도록 지정합니다.

## <a name="app-store"></a>앱 스토어

- **Store에서 앱 자동 업데이트**: Microsoft Store에서 설치된 앱이 자동으로 업데이트되도록 합니다.
- **신뢰할 수 있는 앱 설치**: 신뢰할 수 있는 인증서로 서명된 앱을 테스트용으로 로드할 수 있습니다.
- **개발자 잠금 해제**: Windows 개발자 설정을 허용합니다(예: 테스트용으로 로드된 앱을 최종 사용자가 수정하도록 허용).

## <a name="microsoft-edge-browser"></a>Microsoft Edge 브라우저

- **쿠키**: 브라우저에서 디바이스에 인터넷 쿠키를 저장할 수 있도록 합니다.
- **팝업**: 브라우저에서 팝업 창을 차단합니다(Windows 10 Desktop에만 적용).
- **검색 제안**: 검색 구를 입력할 때 검색 엔진이 사이트를 제안하도록 허용합니다.
- **암호 관리자**: Microsoft Edge 암호 관리자 기능을 사용하거나 사용하지 않습니다.
- **Do Not Track 헤더 보내기**: 사용자가 방문하는 웹 사이트에 Do Not Track 헤더를 보내도록 Microsoft Edge 브라우저를 구성합니다.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **Microsoft Edge용 SmartScreen**: 사이트 및 파일 다운로드에 액세스하는 데 Microsoft Edge SmartScreen을 사용합니다.

## <a name="search"></a>검색

- **위치 검색** - 검색에서 위치를 사용할 수 있는지를 지정합니다. 정보

## <a name="cloud-and-storage"></a>클라우드 및 저장소

- **Microsoft 계정**: 사용자가 Microsoft 계정을 디바이스와 연결하도록 허용합니다.

## <a name="cellular-and-connectivity"></a>셀룰러 및 연결

- **Bluetooth**: 사용자가 디바이스에서 Bluetooth를 설정하고 구성할 수 있는지 여부를 제어합니다.
- **Bluetooth 검색 가능**: Bluetooth를 사용하는 다른 디바이스에서 이 디바이스를 검색하도록 허용합니다.
- **Bluetooth 광고**: 디바이스에서 Bluetooth를 통해 광고를 받을 수 있습니다.

## <a name="control-panel-and-settings"></a>제어판 및 설정

- **시스템 시간 수정**: 최종 사용자가 디바이스 날짜 및 시간을 변경할 수 없도록 합니다.

## <a name="kiosk---obsolete"></a>키오스크 - 사용되지 않음

이러한 설정은 읽기 전용이며 변경할 수 없습니다. 키오스크 모드를 구성하려면 [키오스크 설정](kiosk-settings.md#windows-holographic-for-business)을 참조하세요.

키오스크 디바이스는 일반적으로 특정 앱을 실행합니다. 사용자는 키오스크 앱 외부의 디바이스에서 모든 기능 또는 함수에 액세스할 수 없습니다.

- **키오스크 모드**: 정책에서 지원되는 키오스크 모드 유형을 식별합니다. 다음 옵션을 사용할 수 있습니다.

  - **구성되지 않음**(기본값): 이 정책은 키오스크 모드를 사용하도록 설정하지 않습니다. 
  - **단일 앱 키오스크**: 프로필을 통해 디바이스가 하나의 앱만 실행하도록 설정합니다. 사용자가 로그인할 때 특정 앱이 시작됩니다. 또한 이 모드는 사용자가 새 앱을 열거나 실행 중인 앱을 변경하는 것을 제한합니다.
  - **다중 앱 키오스크**: 프로필을 통해 디바이스가 여러 앱을 실행하도록 설정합니다. 사용자는 추가한 앱만 사용할 수 있습니다. 다중 앱 키오스크 또는 용도가 고정된 디바이스의 혜택은 필요한 앱에만 액세스함으로써 개인이 이해하기 쉬운 환경을 제공하는 것입니다. 필요하지 않은 앱을 해당 보기에서 제거합니다. 
  
    다중 앱 키오스크 환경에 대해 앱을 추가하는 경우 시작 메뉴 레이아웃 파일도 추가합니다. [시작 메뉴 레이아웃 파일](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune)은 Intune에서 사용할 수 있는 XML 샘플을 포함합니다. 

#### <a name="single-app-kiosks"></a>단일 앱 키오스크

다음 설정을 입력합니다.

- **사용자 계정**: 키오스크 앱과 연결된 로컬(디바이스에 대한) 사용자 계정 또는 Azure AD 계정 로그인을 입력합니다. Azure AD 도메인에 가입된 계정의 경우 `domain\username@tenant.org` 형식을 사용하여 계정을 입력합니다. 

    자동 로그온을 사용할 수 있는 공용 환경의 키오스크에서는 최소한의 권한(예: 로컬 표준 사용자 계정)을 지닌 사용자 유형을 사용해야 합니다. 키오스크 모드에 대해 Azure AD(Active Directory) 계정을 구성하려면 `AzureAD\user@contoso.com` 형식을 사용합니다.

- **앱의 AUMID(애플리케이션 사용자 모델 ID)**: 키오스크 앱의 AUMID를 입력합니다. 자세한 내용은 [설치된 앱의 애플리케이션 사용자 모델 ID 찾기](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)를 참조하세요.

## <a name="reporting-and-telemetry"></a>보고 및 원격 분석

- **사용 데이터 공유**: 진단 데이터 제출 수준을 선택합니다.
