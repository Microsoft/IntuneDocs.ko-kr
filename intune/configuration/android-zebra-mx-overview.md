---
title: Microsoft Intune의 Android 디바이스에서 Zebra Mobility Extensions 사용 - Azure | Microsoft Docs
description: Microsoft Intune을 통해 Zebra MX(Mobility Extensions)를 사용하여 Android를 실행하는 Zebra 디바이스를 관리하고 사용합니다. 회사 포털 앱 설치, 앱 사이드로드, 디바이스 관리자 역할 할당, StageNow 프로필 만들기 등을 포함한 모든 단계를 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: beeef8775e6399b252d612f2b5f944d230fe1dd4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735222"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Microsoft Intune에서 Zebra Mobility Extensions를 사용하여 Zebra 디바이스 사용 및 관리

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune에는 앱 관리 및 디바이스 설정 구성 등 다양한 기능이 포함되어 있습니다. 이러한 기본 제공 기능 및 설정은 "Zebra 디바이스"라고도 알려진 Zebra Technologies에서 제조한 Android 디바이스를 관리합니다.

Android 디바이스에서 **MX(Mobility Extensions)** 프로필을 사용하여 Zebra 관련 설정을 사용자 지정하거나 추가합니다.

이 문서에서는 Microsoft Intune의 Zebra 디바이스에서 Zebra MX(Mobility Extensions)를 사용하는 방법을 보여줍니다.

이 기능은 다음에 적용됩니다.

- Android

회사는 소매업, 제조 현장 등에 Zebra 디바이스를 사용할 수 있습니다. 예를 들어 소매업자이고 환경에는 영업 사원이 사용하는 수천 대의 Zebra 모바일 디바이스가 포함되어 있습니다. Intune은 MDM(모바일 디바이스 관리) 솔루션의 일부로 이러한 디바이스를 관리하는 데 도움을 줄 수 있습니다.

Intune을 사용하면 Zebra 디바이스를 등록하여 기간 업무 앱을 디바이스에 배포할 수 있습니다. "디바이스 구성" 프로필을 통해 Zebra 관련 설정을 관리할 수 있는 MX 프로필을 만들 수 있습니다.

> [!NOTE]
> 기본적으로 얼룩말 MX Api는 장치에서 잠기지 않습니다. Intune에서 장치를 등록 하기 전에 장치를 악성 방식으로 손상 시킬 수 있습니다. 장치가 깨끗 한 상태 이면 Access Manager (AccessMgr)를 사용 하 여 MX Api를 잠그는 것이 좋습니다. 예를 들어 신뢰할 수 있는 회사 포털 앱 및 앱만 MX Api를 호출할 수 있도록 선택할 수 있습니다.
>
> 자세한 내용은 얼룩말의 웹 사이트에서 [장치 잠그기](https://developer.zebra.com/community/home/blog/2017/04/11/locking-down-your-device) 를 참조 하세요.

## <a name="before-you-begin"></a>시작하기 전에

- Zebra Technologies의 StageNow 데스크톱 앱의 최신 버전이 있는지 확인합니다.
- [Zebra의 전체 MX 기능 매트릭스](http://techdocs.zebra.com/mx/compatibility)(Zebra의 웹 사이트 열기)를 확인하여 만든 프로필이 디바이스의 MX 버전, OS 버전 및 모델과 호환되는지 확인합니다.
- TC20/25 디바이스와 같은 특정 디바이스는 StageNow에서 사용할 수 있는 모든 MX 기능을 지원하지 않습니다. 업데이트된 지원 정보는 [Zebra의 기능 매트릭스](http://techdocs.zebra.com/mx/tc2x/)(Zebra의 웹 사이트 열기)를 확인합니다.

## <a name="step-1-install-the-latest-company-portal-app"></a>1단계: 최신 회사 포털 앱 설치

장치에서 Google Play 저장소를 엽니다. Microsoft의 Intune 회사 포털 앱을 다운로드고 설치합니다. Google Play에서 설치하는 경우 회사 포털 앱은 자동으로 업데이트를 가져오고 수정합니다.

Google Play를 사용할 수 없는 경우 [Android용 Microsoft Intune 회사 포털](https://www.microsoft.com/download/details.aspx?id=49140)(다른 Microsoft 웹 사이트 열기) 및 [사이드로드](#sideload-the-company-portal-app)를 다운로드합니다(이 문서에서). 이러한 방식으로 설치하면 앱은 자동으로 업데이트 또는 수정 사항을 받지 못합니다. 정기적으로 앱을 업데이트하고 수동으로 패치해야 합니다.

### <a name="sideload-the-company-portal-app"></a>회사 포털 앱 사이드로드

"사이드로딩"은 Google Play를 사용하여 앱을 설치하지 않는 경우입니다. 회사 포털 앱을 사이드로드하려면 StageNow를 사용합니다. 

다음 단계에서는 개요를 제공합니다. 자세한 내용은 Zebra 설명서를 참조하세요. [StageNow를 사용하여 MDM에 등록](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/)(Zebra의 웹 사이트 열기)은 좋은 리소스일 수 있습니다.

1. StageNow에서 **MDM에 등록**할 프로필을 만듭니다.
2. **배포**에서 MDM 에이전트 파일을 다운로드하도록 선택합니다.
3. **지원 앱** 및 **다운로드 구성** 단계를 **아니요**로 설정합니다.
4. **MDM 다운로드**에서 **파일 전송/복사**를 선택합니다. 회사 포털 Android 패키지(APK)의 소스 및 대상을 추가합니다.
5. **MDM 시작**에서 기본값을 그대로 둡니다. 다음 세부 정보를 추가합니다.

    - **패키지 이름**: `com.microsoft.windowsintune.companyportal`
    - **클래스 이름**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

프로필을 계속 게시하고 디바이스의 StageNow 앱과 함께 사용합니다. 회사 포털 앱이 설치되고 디바이스에서 열립니다.

> [!TIP]
> StageNow 및 기능에 대한 자세한 내용은 [StageNow Android 디바이스 준비](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html)(Zebra의 웹 사이트 열기)를 참조하세요.

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>2단계: 회사 포털 앱에 디바이스 관리자 역할이 있는지 확인

회사 포털 앱은 Android 디바이스를 관리하기 위한 디바이스 관리자가 필요합니다. 디바이스 관리자 역할을 활성화하기 위해 일부 Zebra 디바이스에는 디바이스 UI(사용자 인터페이스)가 포함되어 있습니다. 디바이스에 UI가 포함된 경우 회사 포털 앱은 최종 사용자에게 [등록](#step-3-enroll-the-device-in-to-intune) 기간 동안 디바이스 관리자에게 권한을 부여하라는 메시지를 표시합니다(이 문서에서).

UI를 사용할 수 없는 경우 StageNow의 **DevAdmin Manager**를 사용하여 디바이스 관리자를 회사 포털 앱에 수동으로 권한을 부여하는 프로필을 만듭니다.

다음 단계에서는 개요를 제공합니다. 자세한 내용은 Zebra 설명서를 참조하세요. 
[배터리 교체 모드를 디바이스 관리자로 설정](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool)(Zebra의 웹 사이트 열기)은 좋은 리소스일 수 있습니다.

1. StageNow에서 프로필을 만들고 **Xpert 모드**를 선택합니다.
2. **DevAdmin Manager**를 프로필에 추가합니다.
3. **디바이스 관리 작업**을 **디바이스 관리자로 켜기**로 설정합니다.
4. **디바이스 관리자 패키지 이름**을 `com.microsoft.windowsintune.companyportal`로 설정합니다.
5. **디바이스 관리자 클래스 이름**을 `com.microsoft.omadm.client.PolicyManagerReceiver`로 설정합니다.

프로필을 계속 게시하고 디바이스의 StageNow 앱과 함께 사용합니다. 회사 포털 앱에는 디바이스 관리자 역할이 부여됩니다.

## <a name="step-3-enroll-the-device-in-to-intune"></a>3단계: intune에 디바이스 등록

처음 두 단계를 완료하면 회사 포털 앱이 디바이스에 설치됩니다. 디바이스가 Intune에 등록할 준비가 되었습니다.

[Android 디바이스를 등록](../enrollment/android-enroll.md)할 단계를 나열합니다. 많은 Zebra 디바이스가 있는 경우 [DEM(디바이스 등록 관리자) 계정](../enrollment/device-enrollment-manager-enroll.md)을 사용할 수 있습니다. 또한 DEM 계정을 사용하면 회사 포털 앱에서 등록 취소 옵션이 제거됨으로 사용자가 쉽게 등록 취소할 수 없습니다.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>4단계: StageNow에서 디바이스 관리 프로필 만들기

StageNow를 사용하여 디바이스에서 관리하려는 설정을 구성하는 프로필을 만듭니다. 자세한 내용은 Zebra 설명서를 참조하세요. [프로필](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/)(Zebra의 웹 사이트 열기)은 좋은 리소스일 수 있습니다.

StageNow에서 프로필을 만들 때 마지막 단계에서 **MDM으로 내보내기**를 선택합니다. 이 단계에서는 XML 파일을 생성 합니다. 이 파일을 저장합니다. 이후 단계에서 필요합니다.

- 프로필을 조직의 디바이스에 배포하기 전에 테스하는 것이 좋습니다. 테스트하려면 컴퓨터에서 StageNow를 통해 프로필을 만들 때 마지막 단계에서 **테스트** 옵션을 사용합니다. 그런 다음, 디바이스의 StageNow 앱으로 StageNow 생성 파일을 사용합니다.

  디바이스의 StageNow 앱은 프로필을 테스트할 때 생성되는 로그를 표시합니다. [Intune에서 Android를 실행하는 Zebra 디바이스에서 StageNow 로그 사용](android-zebra-mx-logs-troubleshoot.md)에는 오류를 이해하기 위해 StageNow 로그를 사용하는 방법에 대한 정보가 있습니다.

- StageNow 프로필에서 앱 참조, 패키지 업데이트 또는 다른 파일을 업데이트하는 경우 디바이스에서 이러한 업데이트를 가져올 수 있습니다. 업데이트를 가져오려면 프로필이 적용될 때 디바이스가 StageNow 배포 서버에 연결되어야 합니다. 

  또는 Intune에서 기본 제공 기능을 사용하여 다음과 같은 변경 내용을 가져올 수 있습니다.

  - [추가](../apps/apps-add.md), [배포](../apps/apps-deploy.md), 업데이트 및 [모니터](../apps/apps-monitor.md) 앱에 대한 앱 관리 기능.
  - Android Enterprise를 실행하는 디바이스에서 [시스템 및 앱 업데이트](device-restrictions-android-for-work.md#device-owner-only) 관리

파일을 테스트한 후 다음 단계는 Intune을 사용하여 프로필을 디바이스에 배포하는 것입니다.

- 하나 또는 여러 개의 MX 프로필을 장치에 배포할 수 있습니다.
- 여러 StageNow 프로필을 내보내고 설정을 단일 XML 파일로 결합할 수도 있습니다. 그런 다음 Intune에 XML 파일을 업로드 하 여 장치에 배포 합니다.

  > [!WARNING]
  > 여러 MX 프로필이 동일한 그룹을 대상으로 하 고 동일한 속성을 구성 하는 경우에는 장치에 충돌이 발생 합니다.
  >
  > 동일한 속성이 단일 MX 프로필에서 여러 번 구성 된 경우 마지막 구성이 적용 됩니다.

## <a name="step-5-create-a-profile-in-intune"></a>5단계: Intune에서 프로필 만들기

Intune에서 디바이스 구성 프로필 만들기:

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 설정에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼** - **Android**를 선택합니다.
    - **프로필 유형**: **MX 프로필(Zebra에만 해당)** 을 선택합니다.

4. **.xml 형식의 MX 프로필**에서 [StageNow에서 내보낸](#step-4-create-a-device-management-profile-in-stagenow) XML 프로필 파일을 추가합니다(이 문서에서).
5. **확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 정책이 만들어지고 목록에 표시됩니다.

    > [!TIP]
    > 보안상의 이유로 저장한 후에는 프로필 XML 텍스트를 볼 수 없습니다. 텍스트가 암호화되어 별표(`****`)만 볼 수 있습니다. 참고로 Intune에 추가하기 전에 MX 프로필 복사본을 저장하는 것이 좋습니다.

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

다음에 디바이스가 구성 업데이트를 확인할 때 MX 프로필이 디바이스에 배포됩니다. 디바이스가 등록될 때 Intune과 디바이스를 동기화한 다음, 약 8시간마다 동기화합니다. [Intune에서 동기화를 강제로 수행](../remote-actions/device-sync.md)할 수도 있습니다. 또는 디바이스에서 **회사 포털 앱** > **설정** > **동기화**를 엽니다. 

## <a name="update-a-zebra-mx-configuration-after-its-assigned"></a>할당 된 후 얼룩말 MX 구성 업데이트

얼룩말 장치의 MX 관련 구성을 업데이트 하려면 다음을 수행할 수 있습니다. 

- 업데이트 된 StageNow XML 파일을 만들고, 기존 Intune MX 프로필을 편집 하 고, 새 StageNow XML 파일을 업로드 합니다. 이 새 파일은 프로필의 이전 정책을 덮어쓰고 이전 구성을 대체 합니다.
- 다른 설정을 구성 하는 새 StageNow XML 파일을 만들고, 새 Intune MX 프로필을 만들고, 새 StageNow XML 파일을 업로드 하 여 동일한 그룹에 할당 합니다. 여러 프로필을 배포 합니다. 새 프로필이 기존 프로필에 이미 존재 하는 설정을 구성 하는 경우 충돌이 발생 합니다.

## <a name="next-steps"></a>다음 단계

- [프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
- [StageNow 로그를 사용하여 Zebra 디바이스 문제를 해결합니다](android-zebra-mx-logs-troubleshoot.md).
