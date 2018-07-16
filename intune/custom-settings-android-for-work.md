---
title: Android 회사 프로필에 대한 Intune 사용자 지정 프로필 설정
titlesuffix: Microsoft Intune
description: Android 회사 프로필 장치에 대한 Microsoft Intune 사용자 지정 프로필 설정을 만드는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/12/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 109c50acf194598017aa507a0979ad3b9298de9e
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905294"
---
# <a name="create-intune-custom-profile-settings-for-android-work-profile-devices"></a>Android 회사 프로필 장치에 대한 Intune 사용자 지정 프로필 설정 만들기

Intune Android 회사 프로필 사용자 지정 구성 정책을 사용하여 Android 회사 프로필 장치에서 기능을 제어하는 데 사용할 수 있는 OMA-URI 설정을 할당합니다. 이는 많은 모바일 장치 제조업체가 장치 기능을 제어하는 데 사용하는 표준 설정입니다.

이 기능은 Intune 정책을 사용하여 구성할 수 없는 Android 설정을 할당할 수 있도록 하기 위한 것입니다. Intune은 현재 제한된 수의 Android 사용자 지정 정책을 지원합니다. 이 문서의 예제를 참조하여 구성할 수 있는 정책이 무엇인지 알아보세요.

## <a name="create-a-custom-profile"></a>사용자 지정 프로필 만들기

1. [사용자 지정 장치 설정을 구성하는 방법](custom-settings-configure.md)의 지침을 사용하여 시작합니다. **플랫폼**의 경우 **Android 엔터프라이즈**를 선택하고, **프로필 유형**의 경우 **사용자 지정**을 선택합니다.
2. **사용자 지정 OMA-URI 설정** 블레이드에서 **추가**를 선택하여 새 설정을 추가합니다.
3. **행 추가** 블레이드에서 다음을 구성합니다.
    - **이름** - Azure Portal에서 쉽게 식별할 수 있도록 Android 회사 프로필 사용자 지정 설정에 대한 고유한 이름을 입력합니다.
    - **설명** - Android 사용자 지정 정책의 개요에 대한 설명과 찾을 때 도움이 되는 기타 관련 정보를 제공합니다.
    - **OMA-URI** - 설정을 제공하려는 OMA-URI를 입력합니다.
    - **데이터 형식** - 이 OMA-URI 설정을 지정할 데이터 형식을 선택합니다. **문자열**, **문자열(XML 파일)**, **날짜 및 시간**, **정수**, **부동 소수점**, **부울** 또는 **Base64(파일)** 중에서 선택합니다.
    - **값** - 이전에 지정한 OMA-URI와 연결할 값을 지정합니다. 이 값을 제공하는 데 사용하는 방법은 선택한 데이터 형식에 따라 달라집니다. 예를 들어 **날짜 및 시간**을 선택한 경우 날짜 선택기에서 값을 선택합니다.
4. 완료되면 확인을 선택하여 **사용자 지정 OMA-URI 설정**으로 돌아간 다음 설정을 더 추가하거나, **만들기**를 선택하여 사용자 지정 프로필을 만듭니다.


## <a name="example"></a>예제

이 예에서는 Android 회사 프로필 장치에서 회사와 개인 앱 간에 복사 및 붙여넣기 작업을 허용할지 여부를 제한하는 데 사용할 수 있는 사용자 지정 프로필을 만들겠습니다.

1. 이 문서의 절차를 통해 다음 값을 사용하여 Android 회사 프로필 장치에 대한 사용자 지정 프로필을 만들어 보세요.
    - **이름** - "복사 및 붙여넣기 차단" 또는 직접 선택한 텍스트를 입력합니다.
    - **설명** - “회사와 개인 앱 간 복사/붙여넣기 차단” 또는 직접 선택한 텍스트를 입력합니다.
    - **OMA URI** - **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**를 입력합니다.
    - **데이터 형식** - 이 OMA-URI에 대한 값이 **True** 또는 **False**임을 나타내도록 **부울**을 선택합니다.
    - **값** - **True**를 선택합니다.
2. 이 이미지와 유사한 설정으로 완료합니다.
![Android 회사 프로필에 대한 복사 및 붙여넣기 기능 차단](./media/custom-policy-afw-copy-paste.png)
3. 이제 관리하는 Android 회사 프로필 장치에 이 사용자 지정 프로필을 할당하면 회사 프로필과 개인 프로필에 있는 앱 간 복사 및 붙여넣기 기능이 차단됩니다.