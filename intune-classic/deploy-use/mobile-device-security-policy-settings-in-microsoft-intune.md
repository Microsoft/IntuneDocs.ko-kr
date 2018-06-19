---
title: 모바일 장치 보안 정책 설정
description: Intune을 사용하여 조직의 관리되는 장치에 배포할 수 있는 다양한 설정을 구성할 수 있습니다.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 83536a4d9858454505a84a2e394ace1119255049
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31031858"
---
# <a name="mobile-device-security-policy-settings-in-microsoft-intune"></a>Microsoft Intune의 모바일 장치 보안 정책 설정

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!IMPORTANT]
> 이제 Microsoft Intune에서는 각 장치 플랫폼에 대해 개별 구성 정책을 사용합니다. 이러한 정책에는 사용할 수 있는 가장 최신 설정이 포함되어 있습니다. 모바일 장치 보안 정책을 계속 사용할 수 있으며 기존 배포는 계속 작동합니다. 그러나 향후 모바일 장치 보안 정책이 제거될 예정이므로 새 구성 정책으로 최대한 빠르게 마이그레이션할 계획을 세워야 합니다.

Intune 모바일 장치 보안 정책을 사용하여 조직의 관리되는 장치에 배포할 수 있는 다양한 설정을 구성할 수 있습니다. 이러한 설정은 장치의 기능 및 보안을 제어하는 데 사용할 수 있습니다.

다음 장치 유형에 대해 모바일 장치 보안 정책을 만들고 배포할 수 있습니다.

-   Windows RT 8.1 및 등록된 Windows 8.1 장치

-   Windows RT

-   Windows Phone 8 및 Windows Phone 8.1

-   iOS

-   Android 및 Samsung KNOX Standard

> [!NOTE]
> 일부 설정은 일부 장치에 적용할 수 없습니다. 구성할 수 있는 설정의 전체 목록은 아래 표를 참조하세요.
> 2016년 10월부터 Microsoft Intune에서는 Windows 8 회사 포털 앱을 더 이상 지원하지 않습니다. 또한 Windows Phone 8 및 WinRT 플랫폼도 지원되지 않을 것입니다. 따라서 Windows Phone 8 또는 WinRT 장치를 등록하거나 업데이트할 수 없게 됩니다. 이미 등록된 Windows Phone 8, WinRT 및 Windows 8 장치는 계속 관리할 수 있습니다. 서비스 중단 없이 이러한 장치에 앱을 계속 배포하려면 Windows Phone 8 및 Windows 8 장치를 Windows 8.1 및 Windows Phone 8.1로 업데이트하고 해당하는 Windows 8.1 및 Windows Phone 8.1 회사 포털 앱을 사용하세요.

## <a name="security-settings"></a>보안 설정

|                                                                                                                                                                                        설정 이름                                                                                                                                                                                         | Windows 8.1 및 Windows RT 8.1 | Windows RT | Windows Phone 8 및 Windows Phone 8.1 |       iOS       | Android 및 Samsung KNOX Standard |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------|------------|---------------------------------------|-----------------|-----------------------------------|
|                                                                                                                                                                <strong>모바일 장치의 잠금을 해제하는 데 암호 필요</strong>                                                                                                                                                                 |               아니요               |     아니요     |                  예                  |       예       |                예                |
|                                                                                                                 <strong>필수 암호 유형</strong><br /><br />이 설정에서는 숫자만 또는 영숫자와 같이 필요한 암호의 유형을 지정합니다.                                                                                                                 |              예               |    예     |                  예                  |       예       |                아니요                 |
| <strong>필수 암호 유형 - 최소 문자 집합 개수</strong><br /><br />소문자, 대문자, 숫자, 기호에 해당하는 4가지 문자 집합을 사용할 수 있습니다. 이 설정은 암호에 포함되어야 하는 다양한 문자 집합 수를 지정합니다. 그러나 iOS 장치의 경우에는 암호에 포함되어야 할 기호 문자의 수를 지정합니다. |              예               |    예     |                  예                  |       예       |                아니요                 |
|                                                                                                                                                                          <strong>최소 암호 길이</strong>                                                                                                                                                                           |              예               |    예     |                  예                  |       예       |                예                |
|                                                                                                                                               <strong>단순 암호 허용</strong><br /><br />단순한 암호에는 '0000' 및 '1234'가 있습니다.                                                                                                                                                |               아니요               |     아니요     |                  예                  |       예       |                아니요                 |
|                                                                                                                                                  <strong>장치를 초기화하기 전까지 허용되는 로그인 반복 오류 횟수</strong>                                                                                                                                                   |              예               |    예     |                  예                  |       예       |                예                |
|                                                                                                                                                         <strong>화면이 잠기기 전까지 비활성 시간(분)</strong><sup>1</sup>                                                                                                                                                          |              예               |    예     |                  예                  |       예       |                예                |
|                                                                                                                                                                         <strong>암호 만료(일)</strong>                                                                                                                                                                         |              예               |    예     |                  예                  |       예       |                예                |
|                                                                                                                                                                         <strong>암호 기록 기억</strong>                                                                                                                                                                          |              예               |    예     |                  예                  |       예       |                예                |
|                                                                                                                                              <strong>암호 기록 기억</strong> – <strong>이전 암호 다시 사용 안 함</strong>                                                                                                                                              |              예               |    예     |                  예                  |       예       |                예                |
|                                                                                                                                                                              <strong>암호 품질</strong>                                                                                                                                                                              |               아니요               |     아니요     |                  아니요                   |       아니요        |                예                |
|                                                                                                                                                                       <strong>그림 암호 및 PIN 허용</strong>                                                                                                                                                                       |              예               |    예     |                  아니요                   |       아니요        |                아니요                 |
|                                                                                                                                                             <strong>암호를 요구하기 전까지 비활성 시간(분)</strong>                                                                                                                                                              |               아니요               |     아니요     |                  아니요                   |       예       |                아니요                 |
|                                                                                                                                                                          <strong>지문 잠금 해제 허용</strong>                                                                                                                                                                          |               아니요               |     아니요     |                  아니요                   | iOS 7 이상 |                아니요                 |

<sup>1</sup> iOS 장치에서 **화면이 잠기기 전까지 비활성 시간(분)** 및 **암호를 요구하기 전까지 비활성 시간(분)** 설정을 구성하면 해당 설정이 순서대로 적용됩니다. 예를 들어 두 설정 값을 모두 **5** 분으로 지정하면 5분 뒤 화면이 자동으로 꺼지고 이후 5분이 더 지나면 장치가 잠깁니다. 그러나 사용자가 화면을 수동으로 끄면 두 번째 설정이 즉시 적용됩니다. 동일한 예에서 사용자가 화면을 끄면 5분 뒤 장치가 잠깁니다.

Windows RT를 실행하는 장치에 암호 길이 정책을 배포하면 사용자는 현재 암호가 정책 요구 사항을 준수하더라도 강제로 암호를 재설정해야 합니다.

## <a name="encryption-settings"></a>암호화 설정

|                                                                                                                                     설정 이름                                                                                                                                     | Windows 8.1 및 Windows RT 8.1 | Windows RT |              Windows Phone 8 및 Windows Phone 8.1              | iOS | Android 및 Samsung KNOX Standard |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------|------------|-----------------------------------------------------------------|-----|-----------------------------------|
| <strong>모바일 장치 암호화 필요</strong><sup>1</sup><br /><br />Windows Phone 8 장치의 경우 이 옵션을 <strong>예</strong>로 설정해야 합니다.<br /><br />iOS 장치에서 암호화를 사용하도록 설정하려면 <strong>모바일 장치를 잠금 해제하기 위해 암호 필요</strong>설정을 사용하도록 설정합니다. |              예               |     아니요     |                               예                               | 아니요  |                예                |
|                                                                    <strong>메모리 카드 암호화 필요</strong><br /><br />이 설정은 Exchange ActiveSync에서 관리하는 장치에도 적용됩니다.                                                                     |              해당 없음               |    해당 없음     | 해당 없음 <br />앱 및 연결된 데이터가 자동으로 암호화됩니다. | 해당 없음 |                예                |

<sup>1</sup>Windows 8.1을 실행하는 장치에 대한 추가 정보는 다음과 같습니다.

-   Windows 8.1을 실행하는 장치에 암호화를 적용하려면 각 장치에 [Windows용 December 2014 MDM 클라이언트 업데이트](http://support.microsoft.com/kb/3013816) 를 설치해야 합니다.

-   Windows 8.1 장치에 대해 이 설정을 사용하려면 장치의 모든 사용자가 Microsoft 계정을 가지고 있어야 합니다.

-   암호화가 작동하려면 장치가 Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) 하드웨어 인증 요구 사항을 만족해야 합니다.

-   장치에 암호화를 적용하는 경우, 복구 키는 자신의 OneDrive 계정에서 액세스한 Microsoft 계정에서만 액세스할 수 있습니다. 사용자를 대신하여 이 키를 복구할 수 없습니다.

## <a name="malware-settings"></a>맬웨어 설정

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**네트워크 방화벽 필요**|예|아니요|아니요|아니요|아니요|
|**SmartScreen 사용**|예|아니요|아니요|아니요|아니요|

## <a name="system-settings"></a>시스템 설정

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**자동 업데이트 필요**|예|아니요|아니요|아니요|아니요|
|**자동 업데이트 필요 - 자동으로 설치하기 위한 업데이트의 최소 분류**<br /><br />자동으로 설치될 업데이트의 분류를 선택합니다.<br /><br />- **중요**. 중요로 분류된 모든 업데이트를 설치합니다.<br /><br />- **권장**. 중요 또는 권장으로 분류된 모든 업데이트를 설치합니다.|예|아니요|아니요|아니요|아니요|
|**화면 캡처 허용**|아니요|아니요|Windows Phone 8.1만|예|예(Samsung KNOX Standard만)|
|**잠금 화면에서 제어 센터 허용**|아니요|아니요|아니요|iOS 7 이상|아니요|
|**잠금 화면에서 알림 보기 허용**|아니요|아니요|아니요|iOS 7 이상|아니요|
|**잠금 화면에서 오늘 보기 허용**|아니요|아니요|아니요|iOS 7 이상|아니요|
|**사용자 계정 컨트롤**|예|아니요|아니요|아니요|아니요|
|**진단 데이터 제출 허용**|예|아니요|Windows Phone 8.1만|예|예(Samsung KNOX Standard만)|
|**신뢰할 수 없는 TLS 인증서 허용**|아니요|아니요|아니요|예|아니요|
|**잠겨 있는 동안 개인 전자지갑 소프트웨어 허용**|아니요|아니요|아니요|예|아니요|
|**초기화 허용**|아니요|아니요|아니요|아니요|예(Samsung KNOX Standard만)|


## <a name="cloud-settings--documents-and-data"></a>클라우드 설정 – 문서 및 데이터

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**iCloud에 백업 허용**|아니요|아니요|아니요|예|아니요|
|**iCloud와 문서 동기화 허용**|아니요|아니요|아니요|예|아니요|
|**iCloud와 사진 스트림 동기화 허용**|아니요|아니요|아니요|예|아니요|
|**암호화된 백업 필요**|아니요|아니요|아니요|예|아니요|
|**작업 폴더 URL**<br /><br />이 설정은 문서를 장치 간에 동기화될 수 있도록 작업 폴더의 URL을 설정합니다.|예|아니요|아니요|아니요|아니요|
|**Google 백업 허용**|아니요|아니요|아니요|아니요|예(Samsung KNOX Standard만)|

## <a name="cloud-settings--accounts-and-synchronization"></a>클라우드 설정 – 계정 및 동기화

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Microsoft 계정 허용**|아니요|아니요|Windows Phone 8.1만|아니요|아니요|
|**Google 계정 자동 동기화 허용**|아니요|아니요|아니요|아니요|예(Samsung KNOX Standard만)|

## <a name="email-settings"></a>전자 메일 설정

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**사용자가 메일 첨부 파일을 다운로드하도록 허용**<sup>1</sup>|해당 없음|해당 없음|해당 없음|해당 없음|해당 없음|
|**메일 동기화 기간** <br /><br />이 설정은 Exchange ActiveSync에서 관리하는 장치에도 적용됩니다.|해당 없음|해당 없음|해당 없음|해당 없음|해당 없음|
|**이러한 설정을 완전하게 지원하지 않는 모바일 장치에서 Exchange(Exchange ActiveSync)와 동기화할 수 있도록 허용** <br /><br />이 설정은 Exchange ActiveSync에서 관리하는 장치에도 적용됩니다.|해당 없음|해당 없음|해당 없음|해당 없음|해당 없음|
|**Windows Mail 응용 프로그램에서 Microsoft 계정을 옵션으로 설정**|예|아니요|아니요|아니요|아니요|
|**사용자 지정 메일 계정 허용**|아니요|아니요|Windows Phone 8.1만|아니요|아니요|

## <a name="application-settings---browser"></a>응용 프로그램 설정 - 브라우저

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**웹 브라우저 허용**|아니요|아니요|Windows Phone 8.1만|예|예(Samsung KNOX Standard만)|
|**자동 채우기 허용**|예|아니요|아니요|예|예(Samsung KNOX Standard만)|
|**팝업 차단 허용**|예|아니요|아니요|예|예(Samsung KNOX Standard만)|
|**쿠키 허용**|아니요|아니요|아니요|예|예(Samsung KNOX Standard만)|
|**플러그 인 허용**|예|아니요|아니요|아니요|아니요|
|**액티브 스크립팅 허용**|예|아니요|아니요|예|예(Samsung KNOX Standard만)|
|**사기 경고 허용**|예|아니요|아니요|예|아니요|
|**한 단어 입력으로 인트라넷 사이트 허용**<br /><br />(이 설정을 사용하면 한 단어를 사용하여 Internet Explorer를 ‘Bing’ 등과 같은 웹 사이트로 디렉션할 수 있음)|예|아니요|아니요|아니요|아니요|
|**인트라넷 네트워크의 자동 검색 허용**|예|아니요|아니요|아니요|아니요|
|**인터넷의 보안 수준**|예|아니요|아니요|아니요|아니요|
|**인트라넷의 보안 수준**|예|아니요|아니요|아니요|아니요|
|**신뢰할 수 있는 사이트의 보안 수준**|예|아니요|아니요|아니요|아니요|
|**제한된 사이트의 보안 수준**|예|아니요|아니요|아니요|아니요|
|**Do Not Track 헤더 보내기**|예|아니요|아니요|아니요|아니요|
|**엔터프라이즈 모드 메뉴 액세스 허용**|예|아니요|아니요|아니요|아니요|
|**엔터프라이즈 모드 사이트 목록 위치**|예|아니요|아니요|아니요|아니요|

## <a name="application-settings---apps"></a>응용 프로그램 설정 - 앱

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**앱 스토어 허용**|아니요|아니요|Windows Phone 8.1만|예|예(Samsung KNOX Standard만)|
|**앱 스토어에 액세스하려면 암호 필요**|아니요|아니요|아니요|예|아니요|
|**앱에서 바로 구매 허용**|아니요|아니요|아니요|예|아니요|
|**다른 관리되지 않는 앱에서 관리되는 문서 허용**|아니요|아니요|아니요|iOS 7 이상|아니요|
|**다른 관리되는 앱에서 관리되지 않는 문서 허용**|아니요|아니요|아니요|iOS 7 이상|아니요|
|**비디오 회의 허용**|아니요|아니요|아니요|예|아니요|
|**미디어 스토어의 성인 콘텐츠 허용**|아니요|아니요|아니요|예|아니요|
|**앱 설치 허용**|아니요|아니요|아니요|iOS 6 이상|아니요|

## <a name="application-settings---gaming"></a>응용 프로그램 설정 - 게임

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**게임 센터 친구 허용**|아니요|아니요|아니요|예|아니요|
|**다중 접속 게임 허용**|아니요|아니요|아니요|예|아니요|

## <a name="device-capabilities-settings---hardware"></a>장치 기능 설정 - 하드웨어

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**카메라 허용**|아니요|아니요|Windows Phone 8.1만|예|예|
|**이동식 저장소 허용**|아니요|아니요|예|아니요|예(Samsung KNOX Standard만)|
|**Wi-Fi 허용**|아니요|아니요|Windows Phone 8.1만|아니요|예(Samsung KNOX Standard만)|
|**Wi-Fi 테더링 허용**|아니요|아니요|Windows Phone 8.1만|아니요|예(Samsung KNOX Standard만)|
|**무료 Wi-Fi 핫스팟에 자동 연결 허용**|아니요|아니요|Windows Phone 8.1만|아니요|아니요|
|**Wi-Fi 핫스팟 보고 허용**<br /><br />이 설정은 주변의 연결을 쉽게 검색할 수 있도록 Wi-Fi 연결에 관한 정보를 보냅니다.|아니요|아니요|Windows Phone 8.1만|아니요|아니요|
|**지리적 위치 허용**<br /><br />이 설정은 장치에서 위치 정보를 활용하도록 허용합니다.|아니요|아니요|Windows Phone 8.1만|아니요|예(Samsung KNOX Standard만)|
|**NFC 허용**<br /><br />이 설정은 NFC(근거리 통신)를 사용하는 작업을 허용합니다.|아니요|아니요|Windows Phone 8.1만|아니요|예(Samsung KNOX Standard만)|
|**Bluetooth 허용**|아니요|아니요|Windows Phone 8.1만|아니요|예(Samsung KNOX Standard만)|
|**전원 끄기 허용**<br>이 설정을 사용하지 않도록 설정하면 Samsung KNOX Standard 장치에 대한 **장치를 초기화하기 전까지 허용되는 로그인 반복 오류 횟수** 설정이 작동하지 않습니다.|아니요|아니요|아니요|아니요|예(Samsung KNOX Standard만)|

## <a name="device-capabilities-settings---cellular"></a>장치 기능 설정 - 셀룰러

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**음성 로밍 허용**|아니요|아니요|아니요|예|예(Samsung KNOX Standard만)|
|**데이터 로밍 허용**|예|아니요|아니요|예|예(Samsung KNOX Standard만)|
|**로밍하는 동안 자동 동기화 허용**|아니요|아니요|아니요|예|아니요|
|**SMS/MMS 메시징 허용**|아니요|아니요|아니요|아니요|예(Samsung KNOX Standard만)|

## <a name="device-capabilities-settings---features"></a>장치 기능 설정 - 기능

|설정 이름|Windows 8.1 및 Windows RT 8.1|Windows RT|Windows Phone 8 및 Windows Phone 8.1|iOS|Android 및 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**음성 지원 허용**|아니요|아니요|아니요|예|예(Samsung KNOX Standard만)|
|**장치가 잠겨 있는 동안 음성 지원 허용**|아니요|아니요|아니요|예|아니요|
|**음성 전화 걸기 허용**|아니요|아니요|아니요|예|예(Samsung KNOX Standard만)|
|**복사 및 붙여넣기 허용**|아니요|아니요|Windows Phone 8.1만|아니요|예(Samsung KNOX Standard만)|
|**응용 프로그램 간에 클립보드 공유 허용**|아니요|아니요|아니요|아니요|예(Samsung KNOX Standard만)|
|**YouTube 허용**|아니요|아니요|아니요|아니요|예(Samsung KNOX Standard만)|

### <a name="see-also"></a>참고 항목
[Microsoft Intune 정책을 사용하여 장치의 설정 및 기능 관리](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
