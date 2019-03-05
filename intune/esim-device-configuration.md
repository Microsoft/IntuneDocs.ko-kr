---
title: Microsoft Intune에서 eSIM 데이터 연결 사용하도록 설정 - Azure | Microsoft Docs
description: 다른 data plan를 사용하여 인터넷 및 데이터 액세스를 가져오려면 eSIM을 추가하거나 사용합니다. Intune에서 정품 인증 코드를 추가하거나 가져온 다음, 구성 프로필을 사용하여 이런 정품 인증 코드를 할당합니다. eSIM 프로필을 모니터링하고 eSIM 지원 디바이스의 상태를 확인할 수도 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 680853446b40949309ef406a6cab5b6b0181798a
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233086"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>Intune에서 eSIM 셀룰러 프로필 구성 - 공개 미리 보기

> [!NOTE]
> Microsoft는 귀하의 의견을 듣고 싶습니다. `eSIMonIntune@microsoft.com`로 이메일을 보내 질문을 보내거나 토론을 시작합니다.

## <a name="introduction"></a>소개

eSIM는 내장형 SIM 칩이며, [Surface LTE Pro](https://www.microsoft.com/surface/business/surface-pro) 같은 eSIM 지원 디바이스에서 셀룰러 데이터 연결을 통해 인터넷에 연결할 수 있습니다. eSIM을 사용하면 모바일 운영자에서 SIM 카드를 가져올 필요가 없습니다. 전 세계 여행자는 모바일 운영자와 데이터 요금제 간에 전환하여 연결 상태를 항상 유지할 수도 있습니다.

예를 들어 회사용 셀룰러 데이터 요금제 및 개인 용도로 다른 모바일 운영자를 통한 다른 데이터 요금제가 있습니다. 여행할 때 해당 지역의 데이터 요금제에 맞는 모바일 운영자를 찾아 인터넷에 액세스할 수 있습니다.

Intune에서 모바일 운영자가 제공하는 일회용 활성화 코드를 가져올 수 있습니다. eSIM 모듈에서 셀룰러 데이터 요금제를 구성하려면 해당 활성화 코드를 eSIM 지원 디바이스에 배포합니다. Intune에서 활성화 코드를 설치하면 eSIM 하드웨어 모듈은 활성화 코드의 데이터를 사용하여 모바일 운영자에게 연락합니다. 완료되면 eSIM 프로필을 디바이스에 다운로드하고 구성하여 셀룰러를 활성화합니다.

Intune을 사용하여 eSIM을 디바이스에 배포하려면 다음이 필요합니다.

- Surface LTE 같은 **eSIM 지원 디바이스**: [디바이스가 eSIM을 지원하는지](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data) 확인합니다. 또는 이 문서에서 [알려진 eSIM 지원 디바이스 중 일부](#esim-capable-devices) 목록을 참조합니다.
- Intune에서 관리하는 MDM이며 등록된 **Windows 10 Fall Creators Update PC**(1709 이상).
- 모바일 운영자가 제공하는 **활성화 코드**. 이러한 일회용 활성화 코드는 Intune에 추가되고 eSIM 지원 디바이스에 배포됩니다. 모바일 운영자에게 연락해 eSIM 활성화 코드를 가져옵니다.

## <a name="deploy-esim-to-devices---overview"></a>디바이스에 eSIM 배포 - 개요

디바이스에 eSIM을 배포하려면 관리자는 다음 작업을 완료합니다.

1. 모바일 운영자가 제공하는 활성화 코드 가져오기
2. eSIM 지원 디바이스를 포함하는 Azure AD(Azure Active Directory) 디바이스 그룹 만들기
3. 가져온 구독 풀에 Azure AD 그룹 할당
4. 배포 모니터링

이 문서에서는 이러한 단계를 안내합니다.

## <a name="esim-capable-devices"></a>eSIM 지원 디바이스

eSIM 지원 디바이스로 공표됐거나 현재 시장에서 유통되는 디바이스는 다음과 같습니다. [사용자 디바이스가 eSIM을 지원하는지](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data) 확인합니다.

- Acer Swift 7
- Asus NovoGo TP370QL
- Asus TP401
- Asus Transformer Mini T103
- HP Elitebook G5
- HP Envy x2
- HP Probook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE
- HP Spectre Folio 13
- Lenovo Yoga C630
- Samsung Galaxy Book 2

## <a name="step-1-add-cellular-activation-codes"></a>1단계: 셀룰러 활성화 코드 추가

셀룰러 활성화 코드는 쉼표로 구분된 파일(csv)로 모바일 운영자에 의해 제공됩니다. 이 파일이 있는 경우 다음 단계를 사용하여 Intune에 추가합니다.

1. [Azure 포털](https://portal.azure.com/)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **디바이스 구성** > **eSIM 셀룰러 프로필** > **추가**를 차례로 선택합니다.
4. 활성화 코드가 포함된 CSV 파일을 선택합니다.
5. **확인**을 선택하여 변경 내용을 저장합니다.

#### <a name="csv-file-requirements"></a>CSV 파일 요구 사항

활성화 코드를 사용하여 csv 파일에서 작동하는 경우 모바일 운영자는 다음 요구 사항을 따릅니다.

- csv 형식(filename.csv)의 파일이어야 합니다.
- 엄격한 형식을 따라는 파일 구조이어야 합니다. 그렇지 않으면 가져오기가 실패합니다. Intune은 가져올 파일을 확인하고, 오류가 있으면 실패합니다.
- 활성화 코드는 한 번만 사용됩니다. 전에 가져온 활성화 코드를 가져오는 것은 동일하거나 다른 디바이스에 배포할 때 문제가 발생할 수 있기 때문에 좋지 않습니다.
- 각 파일은 단일 모바일 운영자마다 다르고, 모든 활성화 코드는 동일한 청구 계획에 따라 달라야 합니다. Intune은 대상 디바이스에 활성화 코드를 임의로 분산합니다. 디바이스가 특정 활성화 코드를 가져온다는 보장은 없습니다.
- 하나의 csv 파일에 가져올 수 있는 활성화 코드는 최대 1000개입니다.

#### <a name="csv-file-example"></a>CSV 파일 예제

1. csv의 첫 번째 행 및 첫 번째 셀은 SM-DP+(Subscription Manager Data Preparation 서버)라고 하는 모바일 운영자 eSIM 정품 인증 서비스의 URL입니다. URL은 쉼표 없이 정규화된 도메인 이름(FQDN)이어야 합니다.
2. 두 번째 및 이후의 모든 행은 두 개의 값이 포함된 고유한 일회용 활성화 코드입니다.

    1. 첫 번째 열은 고유한 ICCID(SIM 칩의 식별자)입니다.
    2. 두 번째 열은 쉼표로만 구분하는(끝에 쉼표가 없음) 일치 ID입니다. 다음 예제를 참조하세요.

        ![모바일 운영자 활성화 코드 샘플 csv 파일](./media/esim-device-configuration/url-activation-code-examples.png)

3. csv 파일 이름은 Azure Portal에서 셀룰러 구독 풀 이름으로 됩니다. 이전 이미지에서 파일 이름은 `UnlimitedDataSkynet.csv`이므로, Intune도 구독 풀을 `UnlimitedDataSkynet.csv`로 명명합니다.

    ![셀룰러 구독 풀은 활성화 코드 샘플 csv 파일 이름으로 명명됩니다.](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>2단계: Azure AD 디바이스 그룹 만들기

eSIM 지원 디바이스를 포함하는 디바이스 그룹을 만듭니다. [그룹 추가](groups-add.md)는 단계를 나열합니다.

> [!NOTE]
> - 만 디바이스를 대상으로, 사용자를 대상으로 되지 않습니다.
> - eSIM 디바이스를 포함하는 고정 Azure AD 디바이스 그룹을 만드는 것이 좋습니다. 그룹을 사용하여 eSIM 디바이스만 대상으로 하는 것을 확인합니다.

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>3단계: 디바이스에 eSIM 활성화 코드 할당

eSIM 디바이스를 포함하는 Azure AD 그룹에 프로필을 할당합니다.

1. [Azure Portal](https://portal.azure.com/)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음, **Microsoft Intune**을 선택합니다.
2. **디바이스 구성** > **eSIM 셀룰러** > **프로필**을 차례로 선택합니다.
3. 프로필 목록에서 할당하려는 eSIM 셀룰러 구독 풀을 선택한 다음, **할당**을 선택합니다.
4. 그룹을 **포함**하거나 **제외**하기로 선택한 다음, 그룹을 선택합니다.

    ![프로필을 할당할 디바이스 그룹을 포함합니다.](./media/esim-device-configuration/include-exclude-groups.png)

5. 그룹을 선택하면 Azure AD 그룹을 선택합니다. 여러 그룹을 선택하려면 **Ctrl** 키를 사용하여 그룹을 선택합니다.
6. 완료되면 변경 내용을 **저장**합니다.

eSIM 활성화 코드는 한 번만 사용됩니다. Intune에서 디바이스에 활성화 코드를 설치한 후 eSIM 모듈은 모바일 운영자에게 연락해 셀룰러 프로필을 다운로드합니다. 이 연락으로 모바일 운영자 네트워크에 디바이스 등록을 완료합니다.

## <a name="step-4-monitor-deployment"></a>4단계: 배포 모니터링

#### <a name="review-the-deployment-status"></a>배포 상태 검토

프로필을 할당한 후에 구독 풀의 배포 상태를 모니터링할 수 있습니다.

1. [Azure 포털](https://portal.azure.com/)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **디바이스 구성** > **eSIM 셀룰러 프로필**을 차례로 선택합니다. 기존 eSIM 셀룰러 구독 풀이 모두 나열됩니다.
4. 구독을 선택하고 **배포 상태**를 검토합니다.

#### <a name="check-the-profile-status"></a>프로필 상태 확인
디바이스 프로필을 만든 후 Intune에서 그래픽 차트를 제공합니다. 이러한 차트에는 프로필이 디바이스에 성공적으로 할당되어 있는 상태 또는 프로필에 충돌이 표시되는지 여부 등의 프로필 상태가 표시됩니다.

1. **디바이스 구성** > **eSIM 셀룰러 프로필** &gt; 기존 구독을 차례로 선택합니다.
2. **개요** 탭에서 위쪽 그래픽 차트는 특정 eSIM 셀룰러 구독 풀 배포에 할당된 디바이스 수를 보여줍니다.

    또한 동일한 디바이스 프로필이 할당된 기타 플랫폼의 디바이스 수도 표시됩니다.

    Intune에 디바이스를 대상으로 한 활성화 코드에 대한 배포 및 설치 상태가 표시됩니다.

    - **디바이스가 동기화되지 않음**: eSIM 배포 정책을 만든 후 대상 디바이스에서 Intune을 연결하지 않았습니다
    - **활성화 보류 중**: Intune에서 적극 활성화 코드를 디바이스에 설치할 경우의 일시적인 상태
    - **활성**: 활성화 코드 설치 성공
    - **활성화 실패**: 활성화 코드 설치가 실패했습니다 - 문제 해결 가이드를 참조하세요.

#### <a name="view-the-detailed-device-status"></a>자세한 디바이스 상태 보기

디바이스 상태에서 볼 수 있는 자세한 디바이스 목록을 모니터링하고 볼 수 있습니다.**

1. **디바이스 구성** > **eSIM 셀룰러 프로필** &gt; 기존 구독을 차례로 선택합니다.
2. **디바이스 상태**를 선택합니다. Intune에 디바이스에 대한 추가 세부 정보가 표시됩니다.

  - **디바이스 이름**: 대상 디바이스의 이름
  - **사용자**: 등록된 디바이스의 사용자
  - **ICCID**: 모바일 운영자가 디바이스에 설치된 활성화 코드 내에 제공하는 고유한 코드
  - **활성화 상태**: 디바이스에서 활성화 코드의 Intune 배포 및 설치 상태
  - **셀룰러 상태**: 통신사가 제공하는 상태입니다. 문제를 해결하려면 모바일 운영자와 후속 작업을 합니다.
  - **마지막 체크 인**: 디바이스가 Intune과 마지막으로 통신한 날짜

#### <a name="monitor-esim-profile-details-on-the-actual-device"></a>실제 디바이스에서 eSIM 프로필 세부 정보 모니터링

1. 디바이스에서 **설정**을 열고 &gt; **네트워크 및 인터넷**으로 이동합니다.
2. **셀룰러** > **eSIM 프로필 관리** 선택
3. eSIM 프로필을 나열합니다.

    ![디바이스 설정에서 eSIM 프로필 보기](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>디바이스에서 eSIM 프로필 제거

Azure AD 그룹에서 디바이스를 제거하면 eSIM 프로필도 제거됩니다. 다음을 확인합니다.

1. eSIM 디바이스 Azure AD 그룹을 사용하고 있는지 확인합니다.
2. Azure AD 그룹으로 이동하고 그룹에서 디바이스를 제거합니다.
3. 제거된 디바이스에서 Intune에 연결하는 경우 업데이트된 정책이 평가되고 eSIM 프로필이 제거됩니다.

디바이스가 [사용 중지](devices-wipe.md#retire)되거나 사용자가 디바이스를 등록 취소하는 경우 또는 [디바이스 원격 작업 다시 설정](devices-wipe.md#wipe)이 디바이스에서 실행되는 경우 eSIM 프로필도 제거됩니다.

> [!NOTE]
> 프로필 제거하면 청구가 중지되지 않을 수 있습니다. 디바이스에 대한 청구 상태를 확인하려면 모바일 운영자에게 문의합니다.

## <a name="best-practices--troubleshooting"></a>모범 사례 및 문제 해결

- csv 파일 형식이 제대로 지정됐는지 확인합니다. 파일이 중복 코드를 포함하지 않는지, 여러 모바일 운영자를 포함하지 않는지 또는 다른 데이터 요금제를 포함하지 않는지 확인합니다. 각 파일은 모바일 운영자 및 셀룰러 데이터 요금제에 고유해야 합니다.
- 대상으로 하는 eSIM 디바이스만 포함하는 고정 디바이스 Azure AD 그룹을 만듭니다.
- 배포 상태에 문제가 있으면 다음 사항을 확인합니다.
  - **적절하지 않은 파일 형식**: 파일 형식을 올바르게 지정하는 방법은 이 항목의 **1단계: 셀룰러 활성화 코드 추가**를 참조하세요.
  - **셀룰러 활성화 실패, 통신사에 문의**: 활성화 코드가 네트워크 내에 활성화되어 있지 않을 수 있습니다. 또는 프로필 다운로드 및 셀룰러 활성화에 실패했습니다.

## <a name="next-steps"></a>다음 단계
[디바이스 프로필 구성](device-profiles.md)
