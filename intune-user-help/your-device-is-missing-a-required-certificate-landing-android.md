---
title: 장치에 필요한 인증서가 없는 경우 | Microsoft Docs
titlesuffix: Microsoft Intune
description: 디바이스에 회사 지원팀에 필요한 인증서가 누락되었습니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser; seodec18
ms.openlocfilehash: e40ac2fd81375b84084dd229f4cb5a6ab3e9915f
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032217"
---
# <a name="your-device-is-missing-a-required-certificate"></a>장치에 필요한 인증서가 없습니다.

## <a name="whats-a-certificate"></a>인증서란?

[암호화](https://technet.microsoft.com/library/cc962030.aspx)는 정보에 대해 보안을 제공하는 기술입니다. 일반적으로 암호화는 코딩된 메시지를 전달하여 [통신을 안전하게 유지](https://technet.microsoft.com/library/cc962019.aspx)하는 데 사용되었습니다. 가장 간단한 형태의 암호화는 문자를 바꾸거나 위치를 옮겨 코딩된 메시지를 읽을 수 없거나, 뒤죽박죽 섞여 있거나, 숨겨진 메시지로 만듭니다. 디코딩 키 또는 _인증서_가 있는 사용자만 코딩된 메시지를 원래의 읽기 쉬운 형태로 다시 변환할 수 있습니다. Android 장치는 Intune과 함께 인증서를 사용하여 장치와 조직의 리소스(예: 전자 메일 및 문서) 간 통신이 완전히 안전하게 유지되도록 합니다.

## <a name="fixing-certificate-issues"></a>인증서 문제 해결

Android 장치가 Intune에 등록되어 있지 않고 회사 지원팀에 필요한 특정 인증서가 없는 경우 회사 포털 앱에 로그인할 수 없습니다. 로그인하려고 시도하면 다음과 같은 메시지가 표시됩니다.

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

수행해야 할 첫 번째 단계는 장치에 [일반적으로 사전 설치되어 제공되는 인증서가 누락되었는지를](your-device-is-missing-a-preinstalled-certificate-android.md) 확인하는 것입니다.

인증서 문제가 제대로 해결되지 않을 경우 회사 지원팀에서는 [추가 보안을 위해 두 번째 인증서를 설치하도록 요청](your-device-is-missing-an-IT-required-certificate-android.md)할 수 있습니다.

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
