---
title: Intune에 Android 디바이스 등록
titlesuffix: Microsoft Intune
description: Intune에 Android 디바이스를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 3d86afec4e501533ab0048e866969a5bf73c2c57
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54387039"
---
# <a name="enroll-android-devices"></a>Android 디바이스 등록

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 관리자는 다음 Android 디바이스를 관리할 수 있습니다.
- Samsung Knox Standard 디바이스를 포함한 Android 디바이스입니다.
- 다음을 포함하는 Android 엔터프라이즈 디바이스:
    - **Android 회사 프로필 디바이스**: 개인 디바이스에 회사 데이터에 액세스할 수 있는 권한을 부여합니다. 관리자는 회사 계정, 앱 및 데이터를 관리할 수 있습니다. 디바이스에 있는 개인 데이터는 회사 데이터와 분리되며, 관리자는 개인 설정이나 데이터를 제어하지 않습니다. 
    - **Android 전용 디바이스**: 디지털 신호, 티켓 인쇄 또는 재고 관리와 같은 회사 소유의 단일 사용 디바이스입니다. 관리자는 제한된 앱 및 웹 링크 집합에 대한 디바이스 사용을 잠급니다. 또한 사용자가 다른 앱을 추가하거나 디바이스에서 다른 작업을 수행하는 것을 방지합니다.
    - **Android 완전 관리형 디바이스**: 회사 소유의 단일 사용자 디바이스로 개인 용도가 아닌 업무용으로만 사용됩니다. 관리자는 전체 디바이스를 관리하고 회사 프로필에 사용할 수 없는 정책 제어를 적용할 수 있습니다. 

## <a name="prerequisite"></a>필수 구성 요소

모바일 디바이스 관리를 준비하려면 MDM 기관을 **Microsoft Intune**으로 설정해야 합니다. 지침은 [MDM 기관 설정](mdm-authority-set.md)을 참조하세요. 이 항목은 모바일 디바이스 관리에 대해 Intune을 처음 설정할 때 한 번만 설정하면 됩니다.

## <a name="set-up-android-enrollment"></a>Android 등록 설정

기본적으로 Intune에서는 Android 및 Samsung Knox Standard 디바이스 등록을 허용합니다. 사전 요구 사항이 충족되면 관리자는 [사용자에게 자신의 디바이스를 등록하는 방법을 알리기](/intune-user-help/enroll-your-device-in-intune-android)만 하면 됩니다.

사용자가 등록한 후 [규정 준수 정책 할당](compliance-policy-create-android.md), [앱 관리](app-management.md) 등을 포함한 Intune에서 디바이스 관리를 시작할 수 있습니다.

다른 사용자 작업에 대한 정보는 다음 문서를 참조하세요.

- [Microsoft Intune에서 최종 사용자 환경 관련 리소스](end-user-educate.md)
- [Intune에서 Android 디바이스 사용](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Android 디바이스를 차단하거나 등록에서 개인적으로 소유한 Android 디바이스를 차단하려면 [디바이스 유형 제한 설정](enrollment-restrictions-set.md)을 참조하세요.

## <a name="set-up-android-enterprise-enrollment"></a>Android 엔터프라이즈 등록 설정

Android 엔터프라이즈는 개인 앱 및 데이터를 회사 앱 및 데이터가 포함된 회사 프로필과 구분하는 Android 디바이스 기능 및 서비스의 집합니다. Android 엔터프라이즈 디바이스에는 회사 프로필 디바이스, 완전 관리형 디바이스 및 전용 디바이스가 포함됩니다. 

- [Android 회사 프로필 등록 설정](android-work-profile-enroll.md)
- [Android 전용 디바이스 등록 설정](android-kiosk-enroll.md)
- [Android 완전 관리형 등록 설정](android-fully-managed-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Samsung Knox 디바이스를 등록할 때 최종 사용자 환경

Samsung Knox Standard 디바이스는 Intune에서 다중 사용자 관리를 지원합니다. 즉, 사용자가 Azure AD 자격 증명을 사용하여 디바이스에 로그인하고 로그아웃할 수 있습니다. 디바이스는 사용 여부와 관계없이 중앙에서 관리됩니다. 사용자가 로그인하면 앱에 액세스할 수 있고 앱에 정책을 적용할 수도 있습니다. 사용자가 로그아웃하면 모든 앱 데이터가 지워집니다.

Samsung Knox 디바이스를 등록할 때 몇 가지 고려 사항이 있습니다.
-   PIN을 요구하는 정책이 없는 경우에도 등록을 위해 디바이스에 최소 4자리 PIN이 있어야 합니다. 디바이스에 PIN이 없는 경우 PIN을 만들라는 메시지가 사용자에게 표시됩니다.
-   WPJ(작업 공간 연결) 인증서를 위한 사용자 상호 작용이 없습니다.
-   서비스 등록 정보 및 앱이 수행할 수 있는 사항에 관한 메시지가 사용자에게 표시됩니다.
-   Knox 등록 정보 및 앱이 수행할 수 있는 사항에 관한 메시지가 사용자에게 표시됩니다.
-   암호화 정책이 적용되는 경우 사용자는 디바이스 암호에 대한 6자 복합 암호를 설정해야 합니다.
-   회사 리소스 액세스를 위해 서비스에서 푸시되는 인증서를 설치하라는 추가 사용자 프롬프트는 없습니다.
- 일부 이전 Knox 디바이스의 경우 회사 리소스 액세스에 사용되는 추가 인증서에 관한 메시지가 사용자에게 표시됩니다.
- Samsung 미니 디바이스가 **인증서를 찾을 수 없습니다** 또는 **디바이스를 등록할 수 없습니다** 오류와 함께 WPJ를 설치하지 못하는 경우 최신 Samsung 펌웨어 업데이트를 설치합니다.

## <a name="next-steps"></a>다음 단계

- [Android 회사 프로필 등록 설정](android-work-profile-enroll.md)
- [Android 전용 디바이스 등록 설정](android-kiosk-enroll.md)
- [Android 완전 관리형 등록 설정](android-fully-managed-enroll.md)
