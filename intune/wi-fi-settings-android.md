---
title: Android를 실행하는 장치용 Microsoft Intune Wi-Fi 설정 구성
titleSuffix: ''
description: Android 및 Android for Work를 실행하는 장치에서 Intune Wi-Fi 구성 설정에 대해 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ee82da997a794bb2f65929a6fd9e0de0cc776a6e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831064"
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>Android 및 Android for Work를 실행하는 장치에 대해 Microsoft Intune에서 Wi-Fi 설정 구성  

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 Android 및 Android for Work을 실행하는 장치에 대해 Microsoft Intune에서 구성할 수 있는 Wi-Fi 설정을 설명합니다.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>기본 및 엔터프라이즈 프로필에 대한 Wi-Fi 설정

Android 및 Android for Work 장치 둘 다에 대해 다음 Wi-Fi 설정을 사용할 수 있습니다.

- **네트워크 이름** - 이 Wi-Fi 네트워크 설정에 대한 이름을 입력합니다. 사용자가 장치에서 사용 가능한 연결 목록을 찾아볼 때 확인하는 이름입니다.
- **SSID** - Service Set Identifier(서비스 집합 ID)의 약어입니다. 장치에 연결할 무선 네트워크의 실제 이름입니다. 그러나 사용자에게는 연결을 선택할 때 구성한 네트워크 이름만 표시됩니다.
- **자동으로 연결** - 이 네트워크 범위에 있을 때마다 장치를 연결합니다.
- **숨겨진 네트워크** - 이 네트워크가 장치의 사용 가능한 네트워크 목록에 표시되지 않도록 합니다.


## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>엔터프라이즈 프로필에만 적용되는 Wi-Fi 설정

- **EAP 유형** -보안 무선 연결을 인증하는 데 사용되는 EAP(확장할 수 있는 인증 프로토콜) 유형을 선택합니다.
    - **EAP-TLS**
    - **EAP-TTLS**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>EAP 유형을 선택할 때의 추가 옵션

#### <a name="server-trust"></a>서버 트러스트



|설정 이름|추가 정보|사용하는 경우|
|-------------|---------------|-----------|
|**인증서 서버 이름**|신뢰할 수 있는 CA(인증 기관)에서 발급하는 인증서에 사용되는 일반적인 이름입니다. 이 정보를 제공하는 경우 Wi-Fi 네트워크에 연결할 때 사용자 장치에 표시되는 동적 트러스트 대화 상자를 무시할 수 있습니다.|EAP 유형이 **EAP-TLS** 또는 **EAP-TTLS**인 경우|
|**서버 유효성 검사에 대한 루트 인증서**|연결을 인증하는 데 사용되는 신뢰할 수 있는 루트 인증서 프로필을 선택합니다. |EAP 유형이 **EAP-TLS**, **EAP-TTLS** 또는 **PEAP**인 경우|
|**ID 개인 정보 사용(외부 ID)**|EAP ID 요청에 대한 응답으로 전송되는 텍스트를 지정합니다. 이 텍스트에는 원하는 값을 사용할 수 있습니다. 인증하는 동안 이 익명 ID가 먼저 전송된 다음 실제 ID가 보안 채널을 통해 전송됩니다.|EAP 유형이 **PEAP**인 경우|


#### <a name="client-authentication"></a>클라이언트 인증


|                                     설정 이름                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       추가 정보                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                            사용하는 경우                            |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| <strong>클라이언트 인증에 사용할 클라이언트 인증서(ID 인증서)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       연결을 인증하는 데 사용되는 SCEP 또는 PKCS 인증서 프로필을 선택합니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |              EAP 유형이 <strong>EAP-TLS</strong>인 경우              |
|                        <strong>인증 방법</strong>                        | 연결에 대한 인증 방법을 선택합니다.<br>- <strong>인증서</strong> - 서버에 제공되는 ID 인증서인 SCEP 또는 PKCS 클라이언트 인증서를 선택하려는 경우<br><br>- <strong>사용자 이름 및 암호</strong> - 다른 인증 방법을 지정하려는 경우 <br><br><strong>사용자 이름 및 암호</strong>를 선택한 경우<br><br>-  <strong>EAP 이외의 방법(내부 ID)</strong>을 구성한 다음, 연결을 인증할 방법으로 다음 중 하나를 선택합니다.<br>- <strong>없음</strong><br>- <strong>암호화되지 않은 암호(PAP)</strong><br>- <strong>CHAP(Challenge Handshake 인증 프로토콜)</strong><br>- <strong>MS-CHAP(Microsoft CHAP)</strong><br>- <strong>MS-CHAP v2(Microsoft CHAP 버전 2)</strong><br>사용 가능한 옵션은 선택한 EAP 종류에 따라 달라집니다.<br><br><strong>및</strong><br><br>- <strong>ID 개인 정보(외부 ID)</strong> - EAP ID 요청에 대한 응답으로 전송되는 텍스트를 지정하려는 경우 이 텍스트에는 원하는 값을 사용할 수 있습니다. 인증하는 동안 이 익명 ID가 먼저 전송된 다음 실제 ID가 보안 채널을 통해 전송됩니다. | EAP 유형이 <strong>EAP-TTLS</strong> 또는 <strong>PEAP</strong>인 경우 |

