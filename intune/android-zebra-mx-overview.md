---
title: Microsoft Intune-Azure에서에서 Android 장치에서 얼룩말 모바일 확장 사용 | Microsoft Docs
description: Microsoft Intune을 사용 하 여 관리 하 고 얼룩말 Mobility 확장 (MX)를 사용 하 여 Android를 실행 하는 얼룩말 장치 사용. 모든 단계를 포함 하 여 회사 포털 앱을 사이드 로드 앱 설치, 장치 관리자 역할 할당, StageNow 프로필을 만들기를 참조 하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490607"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>사용 및 Microsoft Intune에서 얼룩말 Mobility 확장을 사용 하 여 얼룩말 장치를 관리 합니다.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 관리 앱 및 장치 설정 구성 등의 기능이 풍부한을 포함 합니다. 이러한 기본 제공 기능 및 설정을 제조 얼룩말 기술 "얼룩말 장치" 라고도 하는 Android 장치 관리에 사용 됩니다.

사용자 지정 하거나 얼룩말 관련 설정을 더 추가 하려는 경우 사용할 수도 있습니다 얼룩말 **Mobility 확장 (MX)** 이러한 장치에서. 

이 기능은 다음에 적용됩니다.

- Android

회사는 얼룩말 장치 공장 현장에서 일반 정품, 사용할 수 있습니다. 예를 들어, 소매점 및 수천 대의 영업 사원을 사용한 얼룩말 모바일 장치 환경에 포함 되어 있습니다. Intune 모바일 장치 관리 (MDM) 솔루션의 일부로 이러한 장치를 관리할 수 있습니다.

Intune을 사용 하 여 장치에 기간 업무 앱을 배포 하려면 얼룩말 장치를 등록할 수 있습니다. "장치 구성" 프로필을 통해 MX 얼룩말 관련 설정을 관리 하는 프로필을 만들 수 있습니다.

이 문서에서는 Microsoft Intune에서 얼룩말 장치의 얼룩말 Mobility 확장 (MX)를 사용 하는 방법을 보여 줍니다.

## <a name="before-you-begin"></a>시작하기 전에

- 얼룩말 기술에서 StageNow 데스크톱 앱의 최신 버전 있어야 합니다.
- 확인 해야 [얼룩말의 전체 MX 기능 매트릭스](http://techdocs.zebra.com/mx/compatibility) (얼룩말의 웹 사이트 열기) 만든 프로필은 장치의 MX 버전, OS 버전 및 모델을 사용 하 여 호환 확인 합니다.
- TC20/25 장치 같은 특정 장치 StageNow에서 사용할 수 있는 MX 기능의 일부를 지원 하지 않습니다. 확인 해야 [얼룩말의 기능 매트릭스](http://techdocs.zebra.com/mx/tc2x/) (얼룩말의 웹 사이트 열기) 업데이트 된 지원 정보에 대 한 합니다.

## <a name="step-1-install-the-latest-company-portal-app"></a>1 단계: 최신 회사 포털 앱 설치

장치에서 Google Play 스토어로 이동 하 고 다운로드에서 Microsoft Intune 회사 포털 앱을 설치 합니다. Google Play에서 설치 하는 경우 회사 포털 앱 업데이트를 가져오고 자동으로 수정 합니다.

Google Play를 사용할 수 없는 경우 다운로드 합니다 [Android 용 Microsoft Intune 회사 포털](https://www.microsoft.com/download/details.aspx?id=49140) (다른 Microsoft 웹 사이트 열기) 및 [테스트용으로 로드 것](#sideload-the-company-portal-app) (이 문서의). 이러한 방식으로 설치 될 때 앱 업데이트를 받지 못하면 또는 자동으로 수정 합니다. 정기적으로 업데이트 하 고 앱을 수동으로 패치 해야 합니다.

### <a name="sideload-the-company-portal-app"></a>회사 포털 앱 사이드로드

앱을 설치 하려면 Google Play를 사용 하지 않는 경우 "사이드 로딩"입니다. 회사 포털 앱을 테스트용으로 로드, StageNow 사용 합니다. 

다음 단계를 간략하게를 제공합니다. 특정 세부 정보를 얼룩말의 설명서를 참조 하십시오. [StageNow를 사용 하 여 MDM에 등록](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (얼룩말의 웹 사이트 열기)은 좋은 리소스일 수 있습니다.

1. StageNow에 대 한 프로필을 만듭니다 **MDM에 등록**합니다.
2. **배포**, MDM 에이전트 파일을 다운로드 하도록 선택 합니다.
3. 설정 합니다 **지원 앱** 및 **다운로드 구성** 단계 **No**합니다.
4. **다운로드 MDM**를 선택 **전송/복사 파일**합니다. 원본 및 대상의 회사 포털 Android 패키지 (APK)를 추가 합니다.
5. **MDM 시작**,으로 기본값을 그대로-됩니다. 다음 세부 정보를 추가합니다.

    - **패키지 이름**: `com.microsoft.windowsintune.companyportal`
    - **클래스 이름**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

게시 프로필을 장치에서 StageNow 앱과 함께 사용을 계속 합니다. 회사 포털 앱 설치 및 장치에서 열립니다.

> [!TIP]
> StageNow, 및 수행 하는 작업에 대 한 자세한 내용은 참조 하세요. [StageNow Android 장치 준비](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (얼룩말의 웹 사이트 열기).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>2 단계: 회사 포털 앱에서 장치 관리자 역할을 확인

회사 포털 앱을 Android 장치를 관리 하려면 장치 관리자에 필요 합니다. 장치 관리자 역할을 활성화 하려면 일부 얼룩말 장치 장치에서 사용자 인터페이스 (UI)를 포함 합니다. 장치 UI에 포함 된 경우 회사 포털 앱을 종료 하 라는 중 장치 관리자 권한을 부여할 [등록](#step-3-enroll-the-device-in-to-intune) (이 문서의).

UI를 사용할 수 없는 경우 사용 합니다 **DevAdmin Manager** 수동으로 장치 관리자가 회사 포털 앱에 부여 하는 프로필을 만들려면 StageNow에서.

다음 단계를 간략하게를 제공합니다. 특정 세부 정보를 얼룩말의 설명서를 참조 하십시오. 
[배터리 교체 모드 장치 관리자로 설정](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (얼룩말의 웹 사이트 열기)은 좋은 리소스일 수 있습니다.

1. StageNow에서 프로필을 만들고 선택 **Xpert 모드**합니다.
2. 추가 **DevAdmin Manager** 프로필입니다.
3. 설정할 **장치 관리 작업** 하 **장치 관리자로 설정**합니다.
4. 설정할 **장치 관리자 패키지 이름** 에 `com.microsoft.windowsintune.companyportal`입니다.
5. 설정할 **장치 관리자 클래스 이름** 에 `com.microsoft.omadm.client.PolicyManagerReceiver`입니다.

게시 프로필을 장치에서 StageNow 앱과 함께 사용을 계속 합니다. 회사 포털 앱을 장치 관리자 역할이 부여 됩니다.

## <a name="step-3-enroll-the-device-in-to-intune"></a>3 단계: intune에서 장치를 등록 합니다.

처음 두 단계를 완료 한 후 회사 포털 앱을 장치에 설치 됩니다. 장치를 Intune에 등록 하는 일을 준비가 되었습니다.

[Android 장치를 등록할](android-enroll.md) 단계를 나열 합니다. 사용 하려는 많은 얼룩말 장치에 있는 경우는 [장치 등록 관리자 계정을](device-enrollment-manager-enroll.md)합니다.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>4 단계: StageNow에서 장치 관리 프로필 만들기

StageNow를 사용 하 여 장치에서 관리 하려는 설정을 구성 하는 프로필을 만듭니다. 특정 세부 정보를 얼룩말의 설명서를 참조 하십시오. [프로필](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (얼룩말의 웹 사이트 열기)은 좋은 리소스일 수 있습니다.

마지막 단계에서 StageNow에서 프로필을 만들 때 선택할 **MDM 내보내려면**합니다. 이 XML 파일을 생성 합니다. 이 파일을 저장 합니다. 이후 단계에서 필요 합니다.

> [!TIP]
> 조직에서 장치에 배포 하기 전에 프로필을 테스트 하이 좋습니다. StageNow를 사용 하 여 컴퓨터에 프로필을 만들 때 마지막 단계에서 테스트 하려면 사용 합니다 **테스트** 옵션입니다. 그런 다음 파일을 사용할 StageNow 생성 StageNow 앱을 사용 하 여 장치에서. 
> 
> 장치의 StageNow 앱 프로필을 테스트할 때 생성 된 로그를 보여 줍니다. [Intune에서 Android를 실행 하는 얼룩말 장치에서 사용 하 여 StageNow 로그](android-zebra-mx-logs-troubleshoot.md) StageNow 로그를 사용 하 여 오류를 이해 하는 정보가 있습니다.

> [!NOTE]
> 앱을 참조할 패키지, 업데이트 또는 StageNow 프로필에서 다른 파일을 업데이트 하는 경우 이러한 업데이트를 가져오는 장치를 합니다. 업데이트를 가져오려면 장치 프로필이 적용 될 때 StageNow 배포 서버에 연결 해야 합니다. 
> 
> 또는 포함 하 여 이러한 변경 내용을 가져오려면 Intune에서 기본 제공 기능을 사용할 수 있습니다. 
> - 앱 관리 기능을 [추가](apps-add.md)를 [배포](apps-deploy.md)를 업데이트 하 고 [모니터](apps-monitor.md) 앱.
> - 관리할 [시스템 및 앱 업데이트](device-restrictions-android-for-work.md#device-owner-only) 장치의 Android Enterprise를 실행 합니다.

파일을 테스트 한 후 Intune을 사용 하 여 장치 프로필을 배포 하려면 다음 단계가입니다.

> [!NOTE]
> 각 장치에 프로필을 배포 합니다. 여러 StageNow 프로필이 장치에 배포 하려는 경우 StageNow 프로필 내보내기 및 Intune에 추가 하기 전에 단일 XML 파일에 설정을 결합 하는 것입니다. 
> 
> 동일한 XML 파일에서 동일한 속성을 구성 하는 두 가지 설정 하지 않으려고 합니다. 목표는 장치의 설정 간에 충돌을 방지 하는 것입니다.

## <a name="step-5-create-a-profile-in-intune"></a>5 단계: Intune에서 프로필 만들기

Intune에서 디바이스 구성 프로필 만들기:

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링하고 **Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 설정에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼** - **Android**를 선택합니다.
    - **프로필 유형**: 선택 **MX 프로필 (얼룩말에만 해당)** 합니다.

4. **.xml 형식의 MX 프로필**, XML 프로필 파일 추가 [StageNow에서 내보낸](#step-4-create-a-device-management-profile-in-stagenow) (이 문서의).
5. **확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 정책 생성 되어 목록에 표시 됩니다.

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

다음에 장치가 확인 구성 업데이트에 대 한 MX 프로필은 장치에 배포 됩니다. 장치를 등록할 때 장치를 Intune와 동기화 한 후 대략 8 시간 마다. 할 수도 있습니다 [Intune에서 동기화를 강제로](device-sync.md)입니다. 또는 장치에서 엽니다는 **회사 포털 앱** > **설정** > **동기화**합니다. 

> [!TIP]
> - 보안상의 이유로 저장 한 후 프로필 XML 텍스트를 볼 수 있습니다. 텍스트 암호화 되 고 별표 표시 (`****`). 참조용으로 것이 좋습니다 Intune에 추가 하기 전에 MX 프로필의 복사본을 저장 합니다.
> 
> - 얼룩말 장치에 할당 한 후 프로필을 업데이트 하려면 업데이트 StageNow XML 파일을 만들고, 기존 Intune 프로필을 편집 하 고 새 StageNow XML 파일 추가. 이 새 파일에는 프로필에서 이전 StageNow 정책을 덮어씁니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[StageNow 로그 얼룩말 장치 문제를 해결 하는 데](android-zebra-mx-logs-troubleshoot.md)합니다.
