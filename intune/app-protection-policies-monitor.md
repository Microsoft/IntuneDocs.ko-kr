---
title: 앱 보호 정책을 모니터링하는 방법
titleSuffix: Microsoft Intune
description: Intune에서 모바일 앱 관리 정책의 준수 상태를 모니터링합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 765fae6f0e860935f5ceccadfdf1d9c3fe45d60e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181907"
---
# <a name="how-to-monitor-app-protection-policies"></a>앱 보호 정책을 모니터링하는 방법
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[Azure Portal](https://portal.azure.com)의 Intune 앱 보호 창에서 사용자에게 적용한 MAM(모바일 앱 관리) 정책의 준수 상태를 모니터링합니다. MAM 정책, 준수 상태 및 사용자에게 발생할 수 있는 문제의 영향을 받는 사용자에 대한 정보를 확인합니다.

다음 세 가지 방법으로 규정 준수 상태를 모니터링할 수 있습니다.

-   요약 보기

-   상세 보기

-   보고 보기

> [!NOTE]
> 앱 보호 정책 만들기에 대한 자세한 내용은 [앱 보호 정책을 만들고 할당하는 방법](app-protection-policies.md)을 참조하세요.

## <a name="summary-view"></a>요약 보기

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드에서 **모니터** > **앱 보호 상태**를 선택하여 요약 보기를 표시합니다.

![Intune 모바일 애플리케이션 관리 창의 요약 타일](./media/app-protection-user-status-summary.png)

-   **사용자**: 회사에서 업무 환경의 정책과 연결된 앱을 사용하는 총 사용자 수입니다.

-   **정책으로 관리**: 업무 환경에서 할당된 정책이 있는 앱을 사용한 사용자 수입니다.

-   **정책 없음**: 업무 환경에서 정책의 대상이 되지 않는 앱을 사용하는 사용자 수입니다. 정책에 이러한 사용자를 추가하는 것이 좋습니다.
    > [!NOTE]
    > 플랫폼당 정책이 여러 개 있는 경우 사용자에게 하나 이상의 정책이 할당되면 정책을 통해 사용자를 관리하는 것으로 간주됩니다.

- **플래그가 지정된 사용자**: 문제가 발생하는 사용자 수입니다. 현재 탈옥된 디바이스를 가진 사용자만이 **플래그가 지정된 사용자**로 표시됩니다.


## <a name="detailed-view"></a>상세 보기
**사용자 상태** 타일(장치 OS 플랫폼 기반) 및 **플래그가 지정된 사용자** 타일을 선택하여 요약의 상세 보기에 도달할 수 있습니다.

### <a name="user-status"></a>사용자 상태
단일 사용자를 검색하고 해당 사용자에 대한 준수 상태를 확인할 수 있습니다. **앱 보고** 창은 선택한 사용자에 대한 다음 정보를 표시합니다.
- 사용자 계정에 연결된 디바이스

- 디바이스에 대한 MAM 정책이 있는 앱

- 상태:

  - **체크 인됨**: 정책이 사용자에게 배포되었고, 앱이 회사 컨텍스트에서 적어도 한 번 사용되었습니다.

  - **체크 인 안 됨**: 정책이 사용자에게 정책이 배포되었지만 그 후 회사 컨텍스트에서 앱이 사용되지 않았습니다.

>[!NOTE]
> 검색한 사용자에게 배포된 MAM 정책이 없으면 해당 사용자가 MAM 정책의 대상이 아니라는 메시지가 표시됩니다.

사용자에 대한 보고를 확인하려면 다음 단계를 수행합니다.

1.  사용자를 선택하려면 **요약** 타일을 선택합니다.

    ![Intune 모바일 애플리케이션 관리인 설정 블레이드에서 요약 타일을 강조 표시하는 스크린샷](./media/MAM-reporting-6.png)

2. 열리는 **앱 보고** 창에서 **사용자 선택**을 선택하여 Azure Active Directory 사용자를 검색합니다.

    ![앱 보고 창에서 사용자 선택 옵션을 강조 표시 하는 스크린샷](./media/MAM-reporting-2.png)

3. 목록에서 사용자를 선택합니다. 해당 사용자에 대한 준수 상태의 세부 정보를 확인할 수 있습니다.

### <a name="flagged-users"></a>플래그가 지정된 사용자
상세 보기는 오류 메시지, 오류가 발생했을 때 액세스된 앱, 영향을 받는 디바이스 OS 플랫폼 및 타임스탬프를 표시합니다.

## <a name="reporting-view"></a>보고 보기

상세 보기에서 동일한 보고서와 추가 보고서를 통하여 MAM 정책 준수 상태를 확인할 수 있습니다.

![설정 페이지에서 사용할 수 있는 2개 보고서를 강조 표시하는 스크린샷](./media/MAM-reporting-7.png)

-   **앱 보호 사용자 보고서:** 위 상세 보기 섹션의 **사용자 상태** 보고서에서 찾을 수 있는 정보와 동일한 내용에 대해 간략하게 설명합니다.

-   **앱 보호 응용 앱 보고서:** 보고서를 생성하기 전에 관리자가 선택할 수 있는 두 개의 서로 다른 응용 프로그램 보호 상태를 제공합니다. 보호되거나 보호되지 않은 상태일 수 있습니다.

    -   관리되는 MAM 작업(보호됨)에 대한 사용자 상태: 이 보고서에서는 사용자 단위로 관리되는 각 MAM 앱의 작업에 대해 간략하게 설명합니다.

        -   각 사용자에 대해 MAM 정책에서 대상으로 지정한 모든 앱이 표시되며, MAM 정책에서 체크 인할 때의 각 앱 상태와 MAM 정책에서 대상이 지정되었지만 앱이 체크 인되지 않은 앱의 상태가 구분되어 나타납니다.
<br></br>
    -   관리되지 않는 MAM 작업(보호되지 않음)에 대한 사용자 상태: 이 보고서에서는 사용자 단위로 현재 관리되지 않는 MAM 지원 앱 작업에 대해 간략하게 설명합니다. 다음과 같은 이유로 이러한 경우가 발생할 수 있습니다.

        -   해당 앱을 한 명의 사용자가 사용하거나, 현재 MAM 정책에서 대상으로 지정되지 않은 앱에서 사용

        -   모든 앱이 체크 인되었으나 MAM 정책을 가져오지 않음

![등록된 앱 3개에 대한 세부내용 표가 있는 사용자의 앱 보고 블레이드를 보여주는 스크린샷](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>테이블 그룹화

**앱 보호 사용자 보고서**에 데이터가 표시되면 다음을 기준으로 데이터를 집계할 수 있습니다.

- **유효성 검사 결과:** 데이터가 앱 보호 상태(실패, 경고 또는 성공)별로 그룹화되어 표시됩니다.
- **앱 이름:** 데이터가 실패, 경고 또는 성공 상태의 앱(실제 앱 이름)별로 그룹화되어 표시됩니다.

## <a name="export-app-protection-activities-to-csv"></a>CSV로 앱 보호 활동 내보내기

모든 앱 보호 정책 활동을 단일 .csv 파일로 내보낼 수 있습니다. 이를 통해 사용자로부터 보고된 모든 앱 보호 상태를 분석할 수 있습니다.

앱 보호 보고서를 생성하려면 다음 단계를 수행합니다.

1. Intune 모바일 애플리케이션 관리 창에서 **앱 보호 보고서**를 선택합니다.

    ![Intune 모바일 애플리케이션 관리 창에서 앱 보호 다운로드 링크를 강조 표시하는 스크린샷](./media/app-protection-report-csv-2.png)

2. 예를 선택하여 보고서를 저장한 다음 다른 이름으로 저장을 선택하고 보고서를 저장할 폴더를 선택합니다.

    ![보고서 저장 확인 상자 스크린 샷](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>참고 항목
[iOS 앱 간의 데이터 전송 관리](data-transfer-between-apps-manage-ios.md)

* [Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](app-protection-enabled-apps-android.md)
* [iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](app-protection-enabled-apps-ios.md)
