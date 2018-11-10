---
title: Intune에서 회사 포털 등록 중단
titlesuffix: Microsoft Intune
description: 회사 포털 중단 보고서에 대해 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: ba1ee5a6811457b8c6e7343de7355261a2fcecdb
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236757"
---
# <a name="company-portal-abandonment-report"></a>회사 포털 중단 보고서

이 보고서는 등록 사용자가 회사 포털에서 등록 프로세스를 중단했음을 알려줍니다.

보고서를 보려면 **Intune** > **장치 등록** > **회사 포털 중단**을 선택합니다.

이 중단 정보를 사용하여 사용자가 등록을 완료하도록 온보딩 문서를 업데이트할 수 있습니다. 예를 들어 많은 사용자가 사용 약관에서 그만두는 경우 해당 영역을 조사하고 사용자에게 보다 직관적으로 만들 수 있습니다.

## <a name="what-is-abandonment"></a>중단이란?

중단은 사용자가 다음 중 하나를 수행하는 경우입니다.

-   명시적으로 등록을 중지하는 작업을 선택합니다.
-   등록하는 동안 회사 포털을 닫습니다.
-   등록 섹션 사이에 30분을 초과하여 소요됩니다.

사용자가 등록을 중지하고 여러 번 다시 시작을 선택한 경우 여러 번 시도하고 여러 번 중단한 것으로 표시됩니다. 사용자가 등록 화면 사이에 30분 동안 대기한 경우 여러 번 중단한 것으로 간주됩니다.

## <a name="what-does-the-report-show"></a>보고서에 표시된 내용은 무엇인가요?

등록 보고서에는 iOS 및 Android 장치에 대한 데이터가 포함됩니다.

보고서는 최근 2주 동안의 데이터를 표시하지만 과거의 최대 30일 기간을 표시하도록 보고서를 필터링할 수 있습니다.

**필터**를 선택하여 날짜 범위, 운영 체제 및 등록 섹션을 필터링할 수 있습니다.

### <a name="number-and-percentage-tiles"></a>개수 및 백분율 타일

보고서의 맨 위에서 모든 등록과 관련된 중단된 보고서의 개수 및 백분율을 볼 수 있습니다.

-   시작된 등록: 등록을 시도한 횟수입니다.
-   중단된 등록: 완전히 등록된 규격 장치가 생성되지 않은 등록을 시도한 횟수입니다.
-   중단률: 등록 시도을 중단한 백분율입니다(중단된 등록/시작된 등록).

### <a name="line-graph"></a>꺾은선형 그래프

꺾은선형 그래프는 다음과 같은 네 가지 핵심 등록 섹션 각각에 대해 하루 동안 중단된 등록을 보여줍니다.

-   설정 확인 목록
-   플랫폼 화면
-   사용 조건
-   규정 준수/활성화

### <a name="user-abandonment-actions"></a>사용자 중단 작업

다음 표에서는 중단으로 한정된 사용자 작업 목록을 보여줍니다. 등록 화면 예제를 보려면 [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) 및 [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment) 등록 비디오를 시청하면 됩니다. 


#### <a name="setup-checklist-section"></a>설정 확인 목록 섹션

| 중단 이름 | 화면 또는 흐름 | 플랫폼 | 작업 |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | 회사 포털에서 페이지를 여는 프롬프트 | iOS/Android | **취소** |
| EnrollmentWrapUp | **회사 리소스 로드**가 완료될 때까지의 등록 장치 화면 | iOS/Android | 30분 초과 소요 |
| DeviceCategory | **완료**를 클릭할 때까지의 장치 범주 선택 영역(관리자가 구성한 경우) | iOS/Android | 30분 초과 소요 |
| PreEnrollmentWizard | 등록을 시작했지만 액세스 설정으로 반환한 경우 액세스 설정 화면 | iOS/Android| **연기** |
| PreEnrollmentWizard | **다음 항목** 화면에서 **다음**을 클릭할 때까지의 액세스 설정 화면 | iOS/Android | 30분 초과 소요 |

#### <a name="platform-screens-section"></a>플랫폼 화면 섹션

| 중단 이름 | 화면 또는 흐름 | 플랫폼 | 작업 |
| ---- |---- |---- |---- |
| iOSProfileLaunch | 구성 프로필을 표시하는 프롬프트 | iOS | **무시** |
| iOSProfileLaunch | 프로필 설치 화면 | iOS | **취소** |
| iOSProfileLaunch | 장치를 등록할 프로필의 원본을 신뢰하는 프롬프트 | iOS | **취소** |
| iOSProfileLaunch | 프로필이 설치될 때까지의 프로필 설치 화면 | iOS | 30분 초과 소요 |
| AndroidPermissions | 장치 관리자 활성화 화면 | Android | **취소** |
| AndroidPermissions | 장치 관리자가 **활성화**될 때까지의 전화 통화를 수행하고 관리하는 승인 프롬프트 | Android | 30분 초과 소요 |
| KnoxActivation | KLMS 에이전트 활성화(Samsung에만 해당) | Android| **취소** |
| KnoxActivation | **확인**할 때까지의 KLMS 에이전트 활성화 | Android | 30분 초과 소요|

#### <a name="terms-of-use-section"></a>사용 약관 섹션

| 중단 이름 | 화면 또는 흐름 | 플랫폼 | 작업 |
| ---- |---- |---- |---- |
| TermsofUse | 사용 약관(관리자가 구성한 경우) | iOS/Android | **모두 거부** |
| TermsofUse | **모두 동의**할 때까지의 사용 약관 | iOS/Android | 30분 초과 소요 |

#### <a name="complianceactivation-section"></a>규정 준수/활성화 섹션

| 중단 이름 | 화면 또는 흐름 | 플랫폼 | 작업 |
| ---- |---- |---- |---- |
| 준수 | 장치 준수(관리자가 구성한 경우)는 액세스 설정 후 등록에서 녹색이 아닌 색으로 표시됩니다.| iOS/Android | **연기** |
| 준수 | 장치 준수는 녹색을 표시하도록 업데이트될 때까지 녹색이 아닌 색을 표시합니다. | iOS/Android | 30분 초과 소요 |
| 정품 인증 | 등록 활성화(관리자가 구성한 경우)는 액세스 설정에서 녹색이 아닌 색으로 표시됩니다. | iOS/Android | **연기** |
| 준수 | 장치 활성화는 녹색을 표시하도록 업데이트될 때까지 녹색이 아닌 색을 표시합니다. | iOS/Android | 30분 초과 소요 |

## <a name="next-steps"></a>다음 단계

중단률을 확인한 후에 [등록 옵션](enrollment-options.md)을 검토하여 등록을 개선하기 위해 변경할 수 있는지를 확인할 수 있습니다.