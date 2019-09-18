---
title: Android 엔터프라이즈 완전 관리형 디바이스의 Intune 등록 설정
titleSuffix: Microsoft Intune
description: Intune에서 Android 엔터프라이즈 완전 관리형 디바이스를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dff37794d6c58094749821748dcc96a4f36e28a
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071617"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices-preview"></a>Android 엔터프라이즈 완전 관리형 디바이스의 Intune 등록 설정(미리 보기)

Android 엔터프라이즈 완전 관리형 디바이스는 단일 사용자와 연결되는 회사 소유 디바이스로, 개인 용도가 아닌 업무용으로만 사용됩니다. 관리자는 전체 디바이스를 관리할 수 있으며 다음과 같은 회사 프로필에 사용할 수 없는 정책 제어를 적용할 수 있습니다.
- 관리형 Google Play에서만 앱 설치를 허용합니다.
- 관리형 앱의 제거를 차단합니다.
- 사용자가 디바이스 초기화 등을 못 하도록 합니다.

Intune을 사용하면 Android 엔터프라이즈 완전 관리형 디바이스를 비롯한 Android 엔터프라이즈 디바이스에 앱과 설정을 배포할 수 있습니다. Android 엔터프라이즈에 대한 자세한 내용은 [Android 엔터프라이즈 요구 사항](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)을 참조하세요.

## <a name="technical-requirements"></a>기술 요구 사항

Android 엔터프라이즈 완전 관리형 디바이스를 관리하려면 Intune 독립 실행형 테넌트가 있어야 합니다. 하이브리드(Configuration Manager가 연결됨) 모드 또는 레거시 Silverlight 관리 콘솔에서는 완전 관리형 디바이스 관리를 사용할 수 없습니다.

Android 엔터프라이즈 완전 관리형 디바이스로 관리하려면 디바이스가 다음 요구 사항을 충족해야 합니다.

- Android OS 버전 5.1 이상.
- 디바이스는 GMS(Google 모바일 서비스) 연결성을 갖춘 Android의 빌드를 실행해야 합니다. 디바이스는 GMS를 사용할 수 있어야 하며 GMS에 연결할 수 있어야 합니다.

위의 요구 사항이 충족되면 디바이스 제조업체/OEM에 대한 제한이 없습니다.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Android 엔터프라이즈 완전 관리형 디바이스 관리 설정

Android 엔터프라이즈 완전 관리형 디바이스 관리를 설정하려면 다음 단계를 따릅니다.

1. 모바일 디바이스 관리를 준비하려면 [MDM 기관을 **Microsoft Intune**으로 설정](mdm-authority-set.md)해야 합니다. 이 항목은 모바일 디바이스 관리에 대해 Intune을 처음 설정할 때 한 번만 설정하면 됩니다.
2. [Intune 테넌트 계정을 Android 엔터프라이즈 계정에 연결](connect-intune-android-enterprise.md)합니다.
3. [회사 소유 사용자 디바이스 사용](#enable-corporate-owned-user-devices)
4. [완전 관리형 디바이스를 등록](#enroll-the-fully-managed-devices)합니다.

### <a name="enable-corporate-owned-user-devices"></a>회사 소유 사용자 디바이스 사용

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하여 **디바이스 등록** > **Android 등록** > **회사 소유의 완전 관리형 사용자 디바이스(미리 보기)** 를 선택합니다.
2. **사용자가 회사 소유 디바이스를 등록할 수 있도록 허용**에서 **예**를 선택합니다.

> [!NOTE]
> *규정 준수 상태로 표시된 디바이스 필요* 컨트롤을 사용하고 **모든 클라우드 앱**, **Android** 및 **브라우저**에 적용되는 Azure AD 조건부 액세스 정책이 정의된 경우, 이 정책에서 **Microsoft Intune** 클라우드 앱을 제외해야 합니다. 이는 Android 설치 프로세스가 Chrome 탭을 사용하여 등록 중에 사용자를 인증하기 때문입니다. 자세한 내용은 [Azure AD 조건부 액세스 설명서](https://docs.microsoft.com/azure/active-directory/conditional-access/)를 참조하세요.

이 설정이 **예**로 설정된 경우 등록 토큰(임의 문자열)과 Intune 테넌트에 대한 QR 코드를 제공합니다. 이 단일 등록 토큰은 모든 사용자에게 유효하며 만료되지 않습니다. Android OS 및 디바이스 버전에 따라 토큰 또는 QR 코드를 사용하여 키오스크 디바이스를 등록할 수 있습니다.

## <a name="enroll-the-fully-managed-devices"></a>완전 관리형 디바이스 등록
이제 [완전 관리형 디바이스를 등록](android-dedicated-devices-fully-managed-enroll.md)할 수 있습니다.

## <a name="considerations-for-this-preview-feature"></a>이 미리 보기 기능에 대한 고려 사항
이 공개 미리 보기에는 Android 엔터프라이즈 완전 관리형 솔루션 세트의 핵심 기능 세트가 포함되어 있습니다. [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)와 같은 팀에 현재 통신 채널을 통해 미리 보기 기능을 사용한 경험에 대한 의견을 듣고 싶습니다.

이 미리 보기는 Android 엔터프라이즈 완전 관리형 디바이스를 위한 다음 기능을 지원합니다.
- NFC, 토큰 항목, QR 코드 및 Zero Touch를 사용한 디바이스 등록
- 사용자 그룹의 디바이스 구성
- 사용자 그룹에 대한 앱 배포 및 구성


이러한 미리 보기 기능을 사용할 때는 다음 사항에 유의하세요.
- 중요 업무용 또는 프로덕션 배포에는 미리 보기 기능이 권장되지 않습니다. 
- 미리 보기 기능은 Microsoft Intune 프로덕션 표준으로 구현됩니다. 그러나 모든 Intune 기능을 Android 엔터프라이즈 완전 관리형 디바이스와 함께 사용할 수 있는 것은 아닙니다. 미리 보기 기능은 Intune 콘솔에서 "(미리 보기)"로 명확하게 레이블이 지정됩니다. 
- 미리 보기 기능은 일반적인 Intune 지원 채널을 통해 완전히 지원됩니다.
- Samsung Knox 모바일 등록을 사용하여 Android 엔터프라이즈 완전 관리형 디바이스를 등록하는 기능은 미리 보기에서 지원되지 않습니다. 
- Intune 회사 포털 앱은 Android 엔터프라이즈 완전 관리형 디바이스에서 사용할 수 없습니다. 
- 조건부 액세스, 앱 보호 정책 및 인증서 배포와 같은 Intune 기능은 미리 보기에서 지원되지 않습니다. 
- 모든 프로필 또는 앱을 대상으로 하는 디바이스 그룹은 미리 보기에서 지원되지 않습니다. 사용자 그룹 대상 지정만 지원됩니다. 
- 이메일, WiFi 또는 VPN을 구성할 수 있는 최상의 UI는 없습니다. 앱 구성 정책을 사용하여 지원되는 앱 구성 설정을 구성합니다.

## <a name="next-steps"></a>다음 단계
- [Android 엔터프라이즈 완전 관리형 디바이스 구성 정책 추가](device-restrictions-android-for-work.md#device-owner-only)
- [Android 엔터프라이즈 완전 관리형 디바이스의 앱 구성 정책 구성](app-configuration-policies-use-android.md)

