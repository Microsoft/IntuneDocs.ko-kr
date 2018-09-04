---
title: 장치에 인증서가 없는 경우 | Microsoft Docs
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
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: d51b141b09090119f7c9711ffd56d6b382f6e3dc
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43147954"
---
# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>Android 장치에 일반적으로 휴대폰에 설치되는 인증서가 없습니다.

장치가 Intune에 등록되어 있지 않고 휴대폰에 보통 설치되어 나오는 인증서가 없는 경우 회사 포털 앱에 로그인할 수 없습니다. 로그인하려고 시도하면 다음과 같은 메시지가 표시됩니다.

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

[Digicert의 인증서 페이지](https://www.digicert.com/digicert-root-certificates.htm)에서 필요한 인증서를 가져와 이 문제를 해결할 수 있습니다.

1. __Baltimore CyberTrust Root__ 인증서를 찾아 다운로드합니다. [여기](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)에서 직접 다운로드할 수도 있습니다.

2. 화면 위쪽에서 아래로 끌어 최근 알림 목록을 표시하고 **BaltimoreCyberTrustRoot.crt**를 탭합니다.

3. 장치에서 **인증서 이름을 지정**하도록 요구합니다. 표시되는 기본 인증서 이름을 변경하지 마세요.

4. **자격 증명 용도**가 **VPN 및 앱용**으로 설정되어 있는지 확인한 후 **확인**을 탭합니다.

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

5. 회사 포털 앱 및 브라우저를 닫습니다.

6. 회사 포털 앱을 다시 엽니다. 이제 회사 포털 앱에 로그인할 수 있습니다. 여전히 회사 포털 앱을 사용할 수 없는 경우 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에 제공된 정보를 사용하여 회사 지원팀에 추가 지침을 문의하세요.

>[!NOTE]
> 이 인증서를 설치해도 문제가 해결되지 않고 다른 "인증서 누락" 메시지가 표시되는 경우 추가 단계를 수행하여 [누락된 인증서를 설치](your-device-is-missing-an-IT-required-certificate-android.md)해야 합니다.

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
