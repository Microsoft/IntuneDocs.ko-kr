---
title: "Microsoft Intune에 대한 릴리스 정보 | Microsoft 문서"
description: "Intune 릴리스 정보"
keywords: 
author: Staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: fd300a5dfe6d6976491988453ec69e99668889fb


---

# <a name="release-notes-for-microsoft-intune"></a>Microsoft Intune에 대한 릴리스 정보

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune은 최신 버전의 Windows에 도구, 보고서 및 업그레이드 라이선스를 제공하는 클라우드 기반의 통합 클라이언트 관리 솔루션입니다. 또한 컴퓨터를 최신 상태로 안전하게 유지할 수 있도록 지원합니다. 또한 Intune을 사용하여 Exchange ActiveSync를 통하거나 직접 Intune을 통해 네트워크의 모바일 장치를 관리할 수 있습니다. 다음 릴리스 정보에서는 Microsoft Intune의 중요 정보 및 알려진 문제에 대해 설명합니다.


## <a name="android-users-cant-send-email-when-conditional-access-for-exchange-online-is-implemented"></a>Android 사용자는 Exchange Online에 대한 조건부 액세스가 구현된 경우 전자 메일을 보낼 수 없습니다.

**문제:** 장치에 삼성 Android 5.1.1 이상을 실행하는 사용자는 Exchange Online에 대한 조건부 액세스가 설정된 경우 메일을 보낼 수 없습니다. 삼성에서는 Android 5.1.1 이상에 기본 제공된 메일 클라이언트에 문제가 있음을 알고 있으며 해결 방법을 모색 중입니다.

**해결 방법 1:** 사용자는 Android용 Outlook 앱을 사용하는 것이 좋습니다.

**해결 방법 2:** 영향을 받는 사용자가 메일을 보낼 수 있도록 다음 단계를 수행합니다.

1. 영향을 받은 각 사용자를 Exchange Online에 대한 조건부 액세스 정책에서 "제외된 그룹" 섹션의 보안 그룹에 배치합니다.
2. 사용자가 기본 제공된 메일 클라이언트에서 메일을 일시적으로 동기화하도록 합니다.
3. 제외된 그룹에서 영향을 받는 사용자를 제거하고 사용자가 메일을 보낼 수 있는지 확인합니다.

Microsoft에서는 삼성과 수정 또는 추가 해결 방법에 대해 긴밀히 협력하고 있습니다.



## <a name="changing-resource-access-profiles-between-groups-for-ios-and-android-might-fail"></a>iOS 및 Android 그룹 간에 리소스 액세스 프로필을 변경하면 오류가 발생할 수 있음
**문제:** 그룹 간에 메일 또는 SCEP(단순 인증서 등록 프로토콜) 리소스 액세스 프로필을 변경하면 프로필이 충돌하여 오류가 발생할 수 있습니다. 예를 들어 온-프레미스 Exchange 서버를 가리키며 그룹 A를 대상으로 하는 기존 메일 프로필이 있고 Exchange Online을 가리키며 그룹 B를 대상으로 하는 새 메일 프로필을 만든다고 가정해 보겠습니다. 그룹 A의 사용자를 그룹 B로 이동하는 경우 장치는 온-프레미스 Exchange 메일 프로필을 유지하고 그룹 B를 대상으로 하는 Exchange Online 메일 프로필을 설치하려고 합니다.

이때 다음 중 하나가 발생합니다. 
* 메일 프로필 A와 B가 동일한 경우 메일 프로필 B에 메일 프로필 A가 이미 포함되어 있으므로 장치가 프로필 B를 거부합니다.
* 예제에서 설명한 것처럼 메일 프로필 A가 메일 프로필 B와 다른 경우 장치에 두 개의 메일 프로필이 있습니다.

> [!NOTE]
> 사용자 이름에 사용되는 호스트 이름 및 특성을 검사하여 메일 프로필을 서로 구분합니다.

두 경우 모두, 메일 또는 클라이언트의 SCEP 인증서에 대한 사용자 액세스 권한이 의도하지 않게 제거되는 것을 방지하기 위해 리소스 액세스 프로필(메일 프로필)이 장치에서 제거되지 않았습니다.

**해결 방법:** 없습니다.

## <a name="when-you-enroll-a-windows-81-device-that-must-authenticate-to-a-proxy-server-the-enrollment-process-fails-with-no-visible-cause"></a>프록시 서버에 인증해야 하는 Windows 8.1 장치를 등록할 경우 등록 프로세스가 실패하지만 원인이 표시되지 않음
**문제:** Windows 8.1 장치를 등록하고 해당 장치가 등록 프로세스 중 프록시 서버에 인증해야 할 때 해당 장치에서 프록시 서버 자격 증명을 캐시하지 않은 경우 등록이 실패합니다. 프록시 서버의 자격 증명이 장치에 캐시되지 않은 경우 등록 프로세스에서 사용자가 자격 증명을 입력할 때까지 기다려야 합니다. 그러나 프록시 서버 자격 증명을 입력하라는 메시지가 등록 프로세스 중에 표시되지 않습니다. 결과적으로 등록 프로세스는 프록시 서버를 인증할 수 없습니다. 이 오류는 사용자에게 표시되지 않습니다.

**해결 방법:** 인증된 프록시 서버를 사용해야 하는 네트워크에 등록해야 하는 Windows 8.1 장치의 경우 장치를 등록하기 전에 프록시 서버의 자격 증명을 설정하고 저장합니다. Windows 8.1 장치에서 자격 증명을 설정하고 저장하려면

1.  Windows 8.1 장치에서 Internet Explorer를 엽니다.
2.  프록시 서버 자격 증명을 입력하라는 메시지가 나타나면 자격 증명을 입력한 후 **내 자격 증명 기억**옵션을 선택합니다.
3.  장치를 등록합니다.

## <a name="windows-phone-81-devices-fail-to-enroll-with-microsoft-intune-when-device-authentication-is-enabled-in-ad-fs"></a>AD FS에서 장치 인증을 사용하는 경우 Windows Phone 8.1 장치를 Microsoft Intune에 등록하지 못함
**문제:** Windows Phone 8.1 장치를 등록할 때 AD FS(Active Directory Federation Services)에서 전역 인증 정책의 일부로 장치 인증에 대한 선택적 설정이 사용하도록 설정된 경우 등록에 실패합니다.

**해결 방법:** **전역 인증 정책 편집** 에서 **장치 인증 사용**의 선택을 취소하여 AD FS 서버에서 장치 인증을 사용하지 않도록 설정합니다. 자세한 내용은 [인증 정책 구성](http://technet.microsoft.com/library/dn486781.aspx)을 참조하세요.


## <a name="microsoft-intune-app-wrapping-tool-for-android-has-no-built-in-uninstall-capability"></a>Android용 Microsoft Intune 앱 래핑 도구에는 제거 기능이 기본 제공되지 않습니다.
**문제:** **Android용 Microsoft 앱 래핑 도구**에는 도구를 제거하기 위한 기능이 기본 제공되지 않습니다.

**해결 방법:** 도구를 설치한 위치를 탐색하고 디렉터리를 삭제합니다. 기본 설치 위치는 **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**입니다. 앱 래핑 도구에 대한 자세한 내용은 [앱 래핑 도구를 사용하여 관리용 Android 앱 준비](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)를 참조하세요.

## <a name="remote-assistance-is-not-available-on-computers-that-run-windows-8-or-windows-81"></a>Windows 8 또는 Windows 8.1을 실행하는 컴퓨터에서 원격 지원을 사용할 수 없음
**문제:** 이 릴리스의 경우 Windows 8 또는 Windows 8.1을 실행하는 컴퓨터에서 원격 지원 기능을 사용할 수 없습니다.

**해결 방법:** 없습니다.

## <a name="alert-notifications-for-recipients-that-are-automatically-added-might-not-work"></a>자동으로 추가되는 받는 사람에 대한 경고 알림이 작동하지 않을 수 있음
**문제:** 경고 알림에 받는 사람이 자동으로 추가되는 경우 알림을 받지 못하는 경우가 있을 수 있습니다.

**해결 방법:** 받는 사람이 메시지 알림을 받을 수 있도록 하려면 경고 알림에 받는 사람을 수동으로 추가해야 합니다.

## <a name="language-support-in-the-azure-portal"></a>Azure Portal의 언어 지원
Azure Portal은 중국어(간체), 중국어(번체), 체코어, 네덜란드어, 영어, 독일어, 헝가리어, 이탈리아어, 일본어, 포르투갈어(브라질), 포르투갈어(포르투갈), 러시아어, 스페인어, 영어, 프랑스어, 한국어, 폴란드어, 스웨덴어, 터키어를 지원합니다.

Intune 관리 콘솔 및 사용자에 연결하는 모바일 환경에서는 Azure Portal에서 지원하는 모든 언어 외에 덴마크어, 그리스어, 핀란드어, 노르웨이어 및 루마니아어를 지원합니다.



<!--HONumber=Dec16_HO2-->

