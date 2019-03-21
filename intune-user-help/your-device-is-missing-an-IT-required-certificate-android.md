---
title: 디바이스에 인증서가 없는 경우 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0ef2bc644b537787bd5275e95a4ecc72c899393
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "55835880"
---
# <a name="your-android-device-is-missing-a-certificate-required-by-your-company-support"></a>Android 디바이스에는 회사 지원팀에 필요한 인증서가 누락되었습니다.

디바이스가 Intune에 등록되어 있지 않고 회사 지원팀에 필요한 특정 인증서가 없는 경우 회사 포털 앱에 로그인할 수 없습니다. 로그인하려고 시도하면 다음과 같은 메시지가 표시됩니다.

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

이 문제를 해결하고 필요한 인증서를 가져오려는 경우 다음 두 가지 주요 단계를 수행해야 합니다.

- 회사 또는 학교 PC를 확인하여 누락된 인증서를 식별합니다.
- 디바이스를 사용하여 인터넷에서 누락된 인증서를 다운로드합니다.

## <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>회사 또는 학교 PC를 확인하여 누락된 인증서를 식별합니다.

1. PC에서 Internet Explorer를 엽니다. 이 용도로 사용할 PC가 없으면 회사 지원팀에 문의하세요. 회사 지원팀의 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 확인하세요.

2. [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)로 이동한 후 회사 또는 학교 자격 증명으로 로그인합니다.

3. 브라우저의 주소 표시줄 맨 오른쪽에서 다음 스크린샷과 같이 자물쇠 모양의 기호를 선택합니다.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    자물쇠 기호가 보이지 않으면 중지하고 회사 지원팀에 문의하세요. 잠금은 안전하게 로그인되어 있음을 의미하므로 해당 기호가 표시되지 않으면 계속 진행하지 않아야 합니다.

4. **인증서 보기**를 선택합니다.

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. **인증서** 대화 상자에서 **인증 경로** 탭을 선택한 다음 인터넷에서 가져와야 하는 인증서를 식별합니다. 필요한 인증서의 이름은 앞의 예제 스크린샷에 강조 표시된 것과 같은 위치에 있습니다.

## <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>Android 모바일 디바이스에서 누락된 인증서를 다운로드한 후 설치합니다.

1. Bing이나 Google 같은 검색 엔진을 사용하여 이전 섹션에서 식별한 누락된 인증서의 이름을 검색합니다. 인증서는 ".crt" 또는 ".pem" 등의 다른 "확장명"으로 끝날 수 있습니다.

2. 웹 사이트에서 루트 인증서를 다운로드합니다.

3. 인증서 다운로드 후 디바이스 맨 위에서 아래로 끌어 알림을 열고, 알림 목록에서 인증서 이름을 누릅니다.

4. 다음 스크린샷에 표시된 **인증서 이름 지정** 대화 상자에서 기본 인증서 이름을 그대로 적용합니다.

5. **자격 증명 용도**가 **VPN 및 앱용**으로 설정되어 있는지 확인한 후 **확인**을 탭합니다.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. 회사 포털 앱을 닫습니다.

7. 회사 포털 앱을 다시 엽니다. 이제 회사 포털 앱에 로그인할 수 있습니다. 도움이 필요하면 회사 지원팀에 문의하세요.

앞서 표시된 것과 동일한 "인증서 없음" 메시지가 표시되고 해당 절차를 이미 진행했다면 회사 지원팀에서 설치하기 위해 필요한 다른 인증서가 있을 수 있습니다. 도움이 필요하면 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에 제공되는 연락처 정보를 사용하여 회사 지원팀에 문의하세요.
