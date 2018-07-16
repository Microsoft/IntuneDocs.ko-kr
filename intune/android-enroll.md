---
title: Intune에 Android 장치 등록
titlesuffix: Microsoft Intune
description: Intune에 Android 장치를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f03c60c12bfd759c738de50d320787bf4b85f99d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909187"
---
# <a name="enroll-android-devices"></a>Android 장치 등록

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 관리자는 다음 Android 장치를 관리할 수 있습니다.
- Samsung Knox Standard 장치를 포함한 Android 장치입니다.
- [Android 회사 프로필 장치](#enable-enrollment-of-android-for-work-devices) 및 Android 키오스크 장치를 포함한 Android 엔터프라이즈 장치입니다.

Samsung Knox Standard를 실행하는 장치가 Intune의 다중 사용자 관리에서 지원됩니다. 즉, 사용자가 Azure AD 자격 증명을 사용하여 장치에 로그인하고 로그아웃할 수 있습니다. 장치는 사용 여부와 관계없이 중앙에서 관리됩니다. 사용자가 로그인하면 앱에 액세스할 수 있고 앱에 정책을 적용할 수도 있습니다. 사용자가 로그아웃하면 모든 앱 데이터가 지워집니다.

## <a name="prerequisite"></a>필수 구성 요소

모바일 장치 관리를 준비하려면 MDM 기관을 **Microsoft Intune**으로 설정해야 합니다. 지침은 [MDM 기관 설정](mdm-authority-set.md)을 참조하세요. 이 항목은 모바일 장치 관리에 대해 Intune을 처음 설정할 때 한 번만 설정하면 됩니다.

## <a name="set-up-android-enrollment"></a>Android 등록 설정

기본적으로 Intune에서는 Android 및 Samsung Knox Standard 장치 등록을 허용합니다. 사전 요구 사항을 모두 충족한 후 관리자는 [사용자에게 장치를 등록하는 방법을 알리기](/intune-user-help/enroll-your-device-in-intune-android.md)만 하면 됩니다.

사용자가 등록한 후 [규정 준수 정책 할당](compliance-policy-create-android.md), [앱 관리](app-management.md) 등을 포함한 Intune에서 장치 관리를 시작할 수 있습니다.

다른 사용자 작업에 대한 정보는 다음 문서를 참조하세요.

- [Microsoft Intune에서 최종 사용자 환경 관련 리소스](end-user-educate.md)
- [Intune에서 Android 장치 사용](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Android 장치를 차단하거나 등록에서 개인적으로 소유한 Android 장치를 차단하려면 [장치 유형 제한 설정](enrollment-restrictions-set.md)을 참조하세요.

## <a name="set-up-android-enterprise-enrollment"></a>Android 엔터프라이즈 등록 설정

Android 엔터프라이즈는 개인 앱 및 데이터를 회사 앱 및 데이터가 포함된 회사 프로필과 구분하는 Android 장치 기능 및 서비스의 집합니다. Android 엔터프라이즈 장치에는 회사 프로필 장치 및 키오스크 장치가 포함됩니다. 

Android 엔터프라이즈 장치에 대한 등록을 설정하려면 먼저 [Android 엔터프라이즈를 Intune에 연결](connect-intune-android-enterprise.md)해야 합니다. 이 단계를 완료한 후 다음을 수행할 수 있습니다.

[Android 회사 프로필 등록 설정](android-work-profile-enroll.md)
[Android 키오스크 등록 설정](android-kiosk-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Samsung Knox 장치를 등록할 때 최종 사용자 환경
Samsung Knox 장치를 등록할 때 몇 가지 고려 사항이 있습니다.
-   PIN을 요구하는 정책이 없는 경우에도 등록을 위해 장치에 최소 4자리 PIN이 있어야 합니다. 장치에 PIN이 없는 경우 PIN을 만들라는 메시지가 사용자에게 표시됩니다.
-   WPJ(작업 공간 연결) 인증서를 위한 사용자 상호 작용이 없습니다.
-   서비스 등록 정보 및 앱이 수행할 수 있는 사항에 관한 메시지가 사용자에게 표시됩니다.
-   Knox 등록 정보 및 앱이 수행할 수 있는 사항에 관한 메시지가 사용자에게 표시됩니다.
-   암호화 정책이 적용되는 경우 사용자는 장치 암호에 대한 6자 복합 암호를 설정해야 합니다.
-   회사 리소스 액세스를 위해 서비스에서 푸시되는 인증서를 설치하라는 추가 사용자 프롬프트는 없습니다.
- 일부 이전 Knox 장치의 경우 회사 리소스 액세스에 사용되는 추가 인증서에 관한 메시지가 사용자에게 표시됩니다.
- Samsung 미니 장치가 **인증서를 찾을 수 없습니다** 또는 **장치를 등록할 수 없습니다** 오류와 함께 WPJ를 설치하지 못하는 경우 최신 Samsung 펌웨어 업데이트를 설치합니다.
