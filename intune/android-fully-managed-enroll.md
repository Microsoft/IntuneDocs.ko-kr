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
ms.openlocfilehash: 0035f8d5cd67a995924f7d07a662d8c0671bf063
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163791"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices"></a>Android 엔터프라이즈 완전 관리형 디바이스의 Intune 등록 설정 

Android 엔터프라이즈 완전 관리형 디바이스는 단일 사용자와 연결되는 회사 소유 디바이스로, 개인 용도가 아닌 업무용으로만 사용됩니다. 관리자는 전체 디바이스를 관리할 수 있으며 다음과 같은 회사 프로필에 사용할 수 없는 정책 제어를 적용할 수 있습니다.
- 관리형 Google Play에서만 앱 설치를 허용합니다.
- 관리형 앱의 제거를 차단합니다.
- 사용자가 디바이스 초기화 등을 못 하도록 합니다.

Intune을 사용하면 Android 엔터프라이즈 완전 관리형 디바이스를 비롯한 Android 엔터프라이즈 디바이스에 앱과 설정을 배포할 수 있습니다. Android 엔터프라이즈에 대한 자세한 내용은 [Android 엔터프라이즈 요구 사항](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)을 참조하세요.

## <a name="technical-requirements"></a>기술 요구 사항

Android 엔터프라이즈 완전 관리형 디바이스를 관리하려면 Intune 독립 실행형 테넌트가 있어야 합니다. 하이브리드(Configuration Manager가 연결됨) 모드 또는 레거시 Silverlight 관리 콘솔에서는 완전 관리형 디바이스 관리를 사용할 수 없습니다.

Android 엔터프라이즈 완전 관리형 디바이스로 관리하려면 디바이스가 다음 요구 사항을 충족해야 합니다.

- Android OS 버전 6.0 이상.
- 디바이스는 GMS(Google 모바일 서비스) 연결성을 갖춘 Android의 빌드를 실행해야 합니다. 디바이스는 GMS를 사용할 수 있어야 하며 GMS에 연결할 수 있어야 합니다.

위의 요구 사항이 충족되면 디바이스 제조업체/OEM에 대한 제한이 없습니다.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Android 엔터프라이즈 완전 관리형 디바이스 관리 설정

Android 엔터프라이즈 완전 관리형 디바이스 관리를 설정하려면 다음 단계를 따릅니다.

1. 모바일 디바이스 관리를 준비하려면 [MDM 기관을 **Microsoft Intune**으로 설정](mdm-authority-set.md)해야 합니다. 이 항목은 모바일 디바이스 관리에 대해 Intune을 처음 설정할 때 한 번만 설정하면 됩니다.
2. [Intune 테넌트 계정을 Android 엔터프라이즈 계정에 연결](connect-intune-android-enterprise.md)합니다.
3. [회사 소유 사용자 디바이스 사용](#enable-corporate-owned-user-devices)
4. [완전 관리형 디바이스를 등록](#enroll-the-fully-managed-devices)합니다.

### <a name="enable-corporate-owned-user-devices"></a>회사 소유 사용자 디바이스 사용

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하여 **디바이스 등록** > **Android 등록** > **회사 소유의 완전 관리형 사용자 디바이스**를 선택합니다.
2. **사용자가 회사 소유 디바이스를 등록할 수 있도록 허용**에서 **예**를 선택합니다.

> [!NOTE]
> *규정 준수 상태로 표시된 디바이스 필요* 컨트롤을 사용하고 **모든 클라우드 앱**, **Android** 및 **브라우저**에 적용되는 Azure AD 조건부 액세스 정책이 정의된 경우, 이 정책에서 **Microsoft Intune** 클라우드 앱을 제외해야 합니다. 이는 Android 설치 프로세스가 Chrome 탭을 사용하여 등록 중에 사용자를 인증하기 때문입니다. 자세한 내용은 [Azure AD 조건부 액세스 설명서](https://docs.microsoft.com/azure/active-directory/conditional-access/)를 참조하세요.

이 설정이 **예**로 설정된 경우 등록 토큰(임의 문자열)과 Intune 테넌트에 대한 QR 코드를 제공합니다. 이 단일 등록 토큰은 모든 사용자에게 유효하며 만료되지 않습니다. Android OS 및 디바이스 버전에 따라 토큰 또는 QR 코드를 사용하여 키오스크 디바이스를 등록할 수 있습니다.

## <a name="enroll-the-fully-managed-devices"></a>완전 관리형 디바이스 등록
이제 [완전 관리형 디바이스를 등록](android-dedicated-devices-fully-managed-enroll.md)할 수 있습니다.

## <a name="next-steps"></a>다음 단계
- [Android 엔터프라이즈 완전 관리형 디바이스 구성 정책 추가](device-restrictions-android-for-work.md#device-owner-only)
- [Android 엔터프라이즈 완전 관리형 디바이스의 앱 구성 정책 구성](app-configuration-policies-use-android.md)

