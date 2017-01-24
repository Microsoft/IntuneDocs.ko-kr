---
title: "Microsoft Intune으로 MAM 정책 모니터링 | Microsoft 문서"
description: "해당 정책이 있는 사용자 수를 확인하고 드릴다운하여 자세한 내용을 확인하세요."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fe44466fbcef67d02b16d3d2d335f657251451d3
ms.openlocfilehash: e60d707833ee276971000411e50564f39b41b207


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>Microsoft Intune으로 모바일 앱 관리 정책 모니터링
[Azure 포털](https://portal.azure.com)의 Intune 앱 보호 블레이드에서 사용자에게 적용한 MAM(모바일 앱 관리) 정책의 준수 상태를 모니터링할 수 있습니다. MAM 정책, 준수 상태 및 사용자에게 발생할 수 있는 문제의 영향을 받는 사용자에 대한 정보를 확인할 수 있습니다.

다음 세 가지 방법으로 규정 준수 상태를 모니터링할 수 있습니다.

-   요약 보기

-   상세 보기

-   보고 보기

## <a name="summary-view"></a>요약 보기

요약 보기를 열려면 아래 세 가지 단계를 따르세요.

1. [Azure Portal](https://portal.azure.com)로 이동한 다음 자격 증명을 입력합니다.
2. **추가 서비스**를 선택하고, "Intune"을 입력합니다.
3. **Intune 앱 보호**를 선택합니다.

**Intune 모바일 응용 프로그램 관리** 블레이드에서 준수 상태에 대한 요약을 볼 수 있습니다.

![Intune 모바일 응용 프로그램 관리 블레이드의 요약 타일](../media/mam-azure-portal-user-status-summary.png)

-   **사용자**: 정책과 연결된 앱을 사용하는 회사 사용자의 총수입니다.

-   **정책으로 관리됨**: 회사 컨텍스트에서 적어도 한 개의 앱을 사용한 적이 있는 사용자 수입니다.

-   **정책 없음**: 정책과 연결된 앱을 사용하지만 정책의 대상이 아닌 사용자 수입니다. 정책에 이러한 사용자를 추가하는 것이 좋습니다.

- **플래그가 지정된 사용자**: 문제가 발생하는 사용자 수입니다. 현재 탈옥된 장치를 가진 사용자만이 **플래그가 지정된 사용자**로 표시됩니다.


## <a name="detailed-view"></a>상세 보기
**사용자 상태** 타일(장치 OS 플랫폼 기반) 및 **플래그가 지정된 사용자** 타일을 선택하여 요약의 상세 보기에 도달할 수 있습니다.

### <a name="user-status"></a>사용자 상태
단일 사용자를 검색하고 해당 사용자에 대한 준수 상태를 확인할 수 있습니다. **앱 보고** 블레이드는 선택한 사용자에 대한 다음 정보를 표시합니다.
- 사용자 계정에 연결된 장치

- 장치에 대한 MAM 정책이 있는 앱

- 상태:

  - **체크 인됨**: 정책이 사용자에게 배포되었고, 앱이 회사 컨텍스트에서 적어도 한 번 사용되었습니다.

  - **체크 인 안 됨**: 정책이 사용자에게 정책이 배포되었지만 그 후 회사 컨텍스트에서 앱이 사용되지 않았습니다.

>[!NOTE]
> 검색한 사용자에게 배포된 MAM 정책이 없으면 해당 사용자가 MAM 정책의 대상이 아니라는 메시지가 표시됩니다.

사용자에 대한 보고를 확인하려면 다음 단계를 수행합니다.

1.  사용자를 선택하려면 **요약** 타일을 선택합니다.

    ![스크린샷 3](../media/MAM-reporting-6.png)

2. 열리는 **앱 보고** 블레이드에서 **사용자 선택**을 선택하여 Azure Active Directory 사용자를 검색합니다.

    ![앱 보고 블레이드에서 사용자 옵션 선택](../media/MAM-reporting-2.png)

3. 목록에서 사용자를 선택합니다. 해당 사용자에 대한 준수 상태의 세부 정보를 확인합니다.

### <a name="flagged-users"></a>플래그가 지정된 사용자
상세 보기는 오류 메시지, 오류가 발생했을 때 액세스된 앱, 영향을 받는 장치 OS 플랫폼 및 타임스탬프를 표시합니다.

## <a name="reporting-view"></a>보고 보기

상세 보기에서 동일한 보고서와 추가 보고서를 통하여 MAM 정책 준수 상태를 확인할 수 있습니다.

![스크린샷 4](../media/MAM-reporting-7.png)

-   **앱 보호 사용자 보고서:** 위 상세 보기 섹션의 **사용자 상태** 보고서에서 찾을 수 있는 정보와 동일한 내용에 대해 간략하게 설명합니다.

-   **앱 보호 응용 앱 보고서:** 보고서를 생성하기 전에 관리자가 선택할 수 있는 두 개의 서로 다른 응용 프로그램 보호 상태를 제공합니다. 보호되거나 보호되지 않은 상태일 수 있습니다.

    ![스크린샷 1](../media/MAM-reporting-1.png)

    -   관리되는 MAM 작업(보호됨)에 대한 사용자 상태: 이 보고서에서는 사용자 단위로 관리되는 각 MAM 앱의 작업에 대해 간략하게 설명합니다.

        -   각 사용자에 대해 MAM 정책에서 대상으로 지정한 모든 앱이 표시되며, MAM 정책에서 체크 인할 때의 각 앱 상태와 MAM 정책에서 대상이 지정되었지만 앱이 체크 인되지 않은 앱의 상태가 구분되어 나타납니다.
<br></br>
    -   관리되지 않는 MAM 작업(보호되지 않음)에 대한 사용자 상태: 이 보고서에서는 사용자 단위로 현재 관리되지 않는 MAM 지원 앱 작업에 대해 간략하게 설명합니다. 다음과 같은 이유로 이러한 경우가 발생할 수 있습니다.

        -   해당 앱을 한 명의 사용자가 사용하거나, 현재 MAM 정책에서 대상으로 지정되지 않은 앱에서 사용

        -   모든 앱이 체크 인되었으나 MAM 정책을 가져오지 않음

![스크린샷 2](../media/MAM-reporting-4.png)

## <a name="see-also"></a>참고 항목
[iOS 앱 간의 데이터 전송 관리](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Android 앱이 MAM 정책으로 관리될 때 예상되는 상황](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [iOS 앱이 MAM 정책으로 관리될 때 예상되는 상황](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Jan17_HO2-->

