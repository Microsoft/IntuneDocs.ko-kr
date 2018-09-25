---
title: 삼성 Knox 모바일 등록을 사용하여 Android 장치 자동 등록
titlesuffix: Microsoft Intune
description: 삼성 KME를 사용하여 Android 장치를 등록하는 방법 알아보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f7565972d37c5df5acb83012bb7cebbdc1fa1cec
ms.sourcegitcommit: 378474debffbc85010c54e20151d81b59b7a7828
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028650"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>삼성 Knox 모바일 등록을 사용하여 Android 장치 자동 등록

이 항목은 삼성 KME(Knox 모바일 등록)를 사용하여 지원되는 Android 장치를 등록하도록 Intune을 설정하는 데 도움이 됩니다. Intune을 삼성 KME와 함께 사용하여 최종 사용자가 장치를 처음 켜고 WiFi 또는 셀룰러 네트워크에 연결할 때 많은 회사 소유 Android 장치를 등록할 수 있습니다. 또한 Knox 배포 앱을 사용하는 경우 Bluetooth 또는 NFC를 사용하여 장치를 등록할 수 있습니다.

삼성 KME를 사용하여 Intune 등록을 사용하도록 설정하려면 Intune 및 삼성 Knox 포털을 모두 다음 순서로 사용합니다.

1. Knox 포털에서:
    1. [MDM 프로필 만들기](#create-mdm-profile)
    2. [장치 추가](#add-devices)
    3. [장치에 MDM 프로필 할당](#assign-an-mdm-profile-to-devices)
2. Knox 포털에서 [최종 사용자 로그인을 구성](#configure-how-end-users-sign-in)합니다.
3. [장치를 배포](#distribute-devices)합니다.


Knox 배포 프로그램에 참여하는 공인 재판매인으로부터 장치를 구매하면 장치 식별자(일련 번호 및 IMEI) 목록이 자동으로 Knox 포털에 추가됩니다.


## <a name="prerequisites"></a>전제 조건

KME를 사용하여 Intune에 등록하려면 먼저 다음 단계에 따라 삼성 Knox 포털에 회사를 등록해야 합니다.
1.  [해당 지역에서 KME를 사용할 수 있는지 확인](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME는 55개 이상의 국가에서 사용할 수 있습니다. 해당 국가의 배포가 지원되는지 확인합니다.

2.  [지원되는 장치](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): KME는 Knox 2.4 이상이 설치된 모든 삼성 장치에서 사용할 수 있습니다.

3.  [네트워크 요구 사항](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): 필요한 방화벽 및 네트워크 액세스 규칙이 네트워크에서 허용되는지 확인합니다.

4.  [Samsung 계정에 등록](https://www2.samsungknox.com/en/user/register): 삼성 계정을 사용하려면 KME를 등록하고 사용하도록 설정하며 모든 Knox Enterprise 자격을 한 곳에서 관리해야 합니다.

5.  등록 검토: 프로필이 완료되고 제출된 후 삼성은 응용 프로그램을 검토하고 즉시 승인하거나 추가 후속 조치를 위해 보류 중인 검토 상태로 설정합니다. 계정이 승인되면 추가 단계를 진행할 수 있습니다.

## <a name="create-mdm-profile"></a>MDM 프로필 만들기

회사가 성공적으로 등록되면 아래 정보를 사용하여 Knox 포털에서 Microsoft Intune용 MDM 프로필을 만들 수 있습니다. 단계별 지침은 [Samsung Knox Profile Setup Wizard](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm)(삼성 Knox 프로필 설정 마법사)를 참조하세요.

| MDM 프로필 필드| 필수 여부 | 값 |
|-------------------|-----------|-------|
|MDM 서버 URI     | 아니요        |이 필드를 비워 둡니다.
|프로필 이름       | 예       |선택한 프로필 이름을 입력합니다.
|description        | 아니요        |프로필을 설명하는 텍스트를 입력합니다.
|MDM 에이전트 APK      | 예       |https://aka.ms/intune_kme
|설정 마법사 건너뛰기  | 아니요        |최종 사용자 대신 표준 장치 설정 프롬프트를 건너뛰려면 이 옵션을 선택합니다.
|최종 사용자가 등록을 취소하도록 허용 | 아니요 | 사용자가 KME를 취소하도록 허용하려면 이 옵션을 선택합니다.
|사용자 지정 JSON        | 아니요        |이 필드를 비워 둡니다.
| EULA, 서비스 약관 및 사용자 계약| 아니요 | 사용자 동의를 위해 Knox 관련 계약을 표시하려면 이 옵션을 선택합니다.
이 프로필과 Knox 라이선스 연결 | 아니요 | 이 옵션을 선택 취소한 상태로 둡니다. KME를 사용하여 Intune에 등록하는 데는 Knox 라이선스가 필요하지 않습니다.

## <a name="add-devices"></a>장치 추가

MDM 프로필을 장치에 할당하려면 다음 방법 중 하나를 사용하여 지원되는 삼성 Knox 장치를 Knox 포털에 추가해야 합니다.
- **삼성 공인 대리점 사용**: 삼성 공인 재판매인 중 하나로부터 장치를 구매하는 경우 이 방법을 사용합니다. 재판매인은 승인 시 장치를 자동 업로드할 수 있습니다. [재판매인을 추가하는 방법을 알아보려면 삼성 Knox 등록 사용자 가이드를 참조하세요](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **KDA(Knox 배포 앱) 사용**: KME를 사용하여 등록해야 하는 기존 장치가 있는 경우 이 방법을 사용합니다. Bluetooth 또는 NFC를 사용하여 이 방법으로 Knox 포털에 장치를 추가할 수 있습니다. [KDA 사용에 대해 알아보려면 삼성 Knox 등록 사용자 가이드를 참조하세요](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>장치에 MDM 프로필 할당
등록하려면 먼저 Knox 포털에서 추가된 장치에 MDM 프로필을 할당해야 합니다. [장치 구성에 대해 알아보려면 삼성 Knox 등록 사용자 가이드를 참조하세요](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>최종 사용자가 로그인하는 방법 구성

KME를 사용하여 Intune에 등록된 장치의 경우, 최종 사용자가 로그인하는 방법을 다음과 같이 구성할 수 있습니다.

- **사용자 이름 연결 없음:** Knox 포털의 **장치 세부 정보** 아래에서 추가된 장치의 **사용자 ID** 및 **암호** 필드를 비워 둡니다. 이 작업을 수행하려면 Intune에 등록할 때 최종 사용자가 사용자 이름과 암호를 모두 입력해야 합니다.

- **사용자 이름 연결 사용:** Knox 포털의 **장치 세부 정보** 아래에서 추가된 장치의 **사용자 ID**(예: 할당된 사용자 또는 [장치 등록 관리자](https://docs.microsoft.com/intune/device-enrollment-manager-enroll) 계정의 사용자 이름)를 입력합니다. 이 필드의 경우 사용자 이름이 미리 채워져 있고 최종 사용자가 Intune에 등록할 때 암호를 입력해야 합니다.

> [!NOTE]
>
>사용자 연결이 정의된 경우 연결된 사용자만 KME를 사용하여 장치를 등록할 수 있습니다. 장치를 초기화한 후에도 마찬가지입니다. 사용자 연결이 Knox 포털에서 정의되어 있지 않으면 유효한 Intune 라이선스를 가진 모든 사용자가 KME를 사용하여 장치를 등록할 수 있습니다.
>

## <a name="distribute-devices"></a>장치 배포

MDM 프로필을 만들고 할당하고, 사용자 이름을 연결하고, Intune에서 장치를 회사 소유로 식별한 후 사용자에게 장치를 배포할 수 있습니다.

여전히 도움이 필요하세요? 전체 [Knox 모바일 등록 사용자 가이드](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm)를 체크 아웃하세요.

## <a name="frequently-asked-questions"></a>질문과 대답
- **Google Play 계정:** Google Play 계정은 장치를 Microsoft Intune에 등록하는 데 필요하지 않습니다. 그러나 이후 Intune 회사 포털 앱을 업데이트하려면 장치에서 Google Play 계정이 필요할 수 있습니다.

- **Google 장치 소유자 모드:** KME를 사용하여 Google 장치 소유자 모드에서 등록하는 기능은 이 미리 보기에서 지원되지 않습니다. 이 시나리오는 현재 조사 중입니다.

- **“암호” 필드가 무시됨:** Knox 포털의 **장치 세부 정보**에서 채워져 있는 **암호** 필드는 Intune 회사 포털 앱에서 무시됩니다. 장치 등록을 완료하려면 최종 사용자가 장치에서 암호를 입력해야 합니다.

- **"Android Enterprise 등록:** KME는 Android Enterprise 등록을 지원하지 않습니다.

## <a name="getting-support"></a>지원 받기
[삼성 KME에 대한 지원을 받는 방법](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm)에 대해 자세히 알아보세요.


