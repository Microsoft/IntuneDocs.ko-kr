---
title: Microsoft Intune에서 Telecom Expense Management 서비스 설정 - Azure | Microsoft Docs
titleSuffix: ''
description: Microsoft Intune을 Saaswedo Telecom Expense Management 서비스와 통합하여 데이터 사용량을 모니터링하고 Android 및 iOS 디바이스에 대한 임계값 또는 제한을 설정합니다.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 340659adfa3bbd40f98ccec9d8d44e952f7ec9b9
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059935"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Intune에서 Telecom Expense Management 서비스 설정

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune을 사용하여 조직 소유의 모바일 디바이스에서 데이터 사용량으로부터 통신 비용을 관리할 수 있습니다. Intune은 Saaswedo의 [Datalert Telecom Expense Management](http://datalert.biz/get-started)와 통합됩니다. Datalert는 통신 데이터 사용량을 관리할 수 있는 실시간 통신 비용 관리 솔루션입니다. 이 솔루션은 Intune 관리 디바이스에 대해 비용이 많이 들고 예기치 않은 데이터와 로밍 요금을 방지하게 해줍니다.

Datalert와의 통합을 통해 로밍 및 국내 데이터 사용량 제한을 설정, 모니터링 및 적용할 수 있습니다. 정의된 임계값을 초과할 경우 경고가 자동으로 작동됩니다. 사용자가 (로밍을 해제하거나 임계값을 초과하는 등) 개인 또는 그룹에 여러 작업을 적용하도록 서비스를 구성할 수 있습니다. Datalert 관리 콘솔에는 데이터 사용량 및 모니터링 정보를 제공하는 보고서가 포함되어 있습니다.

다음 이미지에서는 Intune이 Datalert에 어떻게 통합되어 있는지를 보여 줍니다.

  ![Intune과 Datalert 통합을 보여 주는 다이어그램](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

Intune과 함께 Datalert 서비스를 사용할 수 있도록 Datalert 및 Intune에 몇 가지 구성 설정이 있습니다. 이 문서에서는 다음 방법을 보여 줍니다.

- Datalert 콘솔의 설정을 구성하여 Datalert 서비스를 Intune에 연결합니다.
- Intune에서 이 연결이 활성 상태이고 사용하도록 설정되어 있는지 확인합니다.
- Intune을 사용하여 Datalert 앱을 디바이스에 추가합니다.
- Datalert 서비스 및 Intune(선택 사항)을 해제합니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

- Knox를 지원하는 Android 4.4 이상 디바이스(삼성)

  [Knox를 지원하는 Android 버전](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0)(삼성의 웹 사이트 열림)은 Knox 지원 버전을 나열합니다.

- iOS 8.0 이상

## <a name="prerequisites"></a>전제 조건

- Microsoft Intune에 대한 구독 및 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 대한 액세스 권한
- [Datalert](http://www.datalert.biz/)에 대한 구독(Datalert의 웹 사이트 열림)

## <a name="telecom-expense-management-providers"></a>Telecom Expense Management 공급자

Intune은 다음 Telecom Expense Management 공급자와 통합되어 있습니다.

- [Saaswedo Datalert Telecom Expense Management 서비스](http://www.datalert.biz/)(Datalert의 웹 사이트 열림)

## <a name="deploy-the-intune-and-datalert-solution"></a>Intune 및 Datalert 솔루션 배포

### <a name="step-1-connect-the-datalert-service-to-intune"></a>1단계: Intune에 Datalert 서비스 연결

1. 관리자 자격 증명을 사용하여 Datalert 관리 콘솔에 로그인합니다.

2. 콘솔에서 **설정** 탭 > **MDM 구성**으로 이동합니다.

3. **차단 해제**를 선택합니다. **차단 해제**하면 페이지의 설정을 변경하거나 업데이트할 수 있습니다.

4. **Intune/Datalert 연결** > **Server MDM**에서 **Microsoft Intune**을 선택합니다.

5. **Azure AD 도메인**에 Azure 테넌트 ID를 입력합니다. **연결**을 선택합니다.

    **연결**을 선택하면 Datalert 서비스가 Intune을 사용하여 체크 인됩니다. 기존 Datalert 연결이 없는지 확인합니다. 몇 초 후 Microsoft 로그인 페이지가 표시되고 Datalert Azure 인증이 시작됩니다.

6. Microsoft 인증 페이지에서 **동의함**을 선택합니다.

    Datalert **thank you** 페이지로 리디렉션됩니다. 이 페이지는 몇 초 후 닫힙니다. Datalert에서 연결의 유효성을 검사하고 유효성이 확인된 항목 목록 옆에 녹색 확인 표시가 나타납니다. 유효성 검사에 실패하면 빨간색 메시지가 표시됩니다. Datalert 지원에 도움을 요청하세요.

    다음 이미지는 연결에 성공했을 때 녹색 확인 표시를 보여 줍니다.

      ![연결 성공을 보여 주는 Datalert 페이지](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. **Datalert App/ADAL Consent** 섹션에서 스위치를 **켜기**로 설정합니다. Microsoft 인증 페이지에서 **동의함**을 선택합니다.

    Datalert **thank you** 페이지로 리디렉션됩니다. 이 페이지는 몇 초 후 닫힙니다. Datalert에서 연결의 유효성을 검사하고 유효성이 확인된 항목 목록 옆에 녹색 확인 표시가 나타납니다. 유효성 검사에 실패하면 빨간색 메시지가 표시됩니다. Datalert 지원에 도움을 요청하세요.

    다음 이미지는 연결에 성공했을 때 녹색 확인 표시를 보여 줍니다.

      ![연결 성공을 보여 주는 Datalert 페이지](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. **MDM 프로필 관리 (선택 사항)** 에서 스위치를 **켜기**로 설정합니다. 이 설정을 사용하면 Datalert가 Intune에서 사용 가능한 프로필을 읽어 정책을 설정하는 데 도움이 됩니다. 

    Microsoft 인증 페이지에서 **동의함**을 선택합니다.

    Datalert **thank you** 페이지로 리디렉션됩니다. 이 페이지는 몇 초 후 닫힙니다. Datalert에서 연결의 유효성을 검사하고 유효성이 확인된 항목 목록 옆에 녹색 확인 표시가 나타납니다. 유효성 검사에 실패하면 빨간색 메시지가 표시됩니다. Datalert 지원에 도움을 요청하세요.

    다음 이미지는 연결에 성공했을 때 녹색 확인 표시를 보여 줍니다.

   ![연결 성공을 보여 주는 Datalert 페이지](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>2단계: Intune에서 Telecom Expense Management가 활성 상태인지 확인

1단계를 완료하면 연결이 자동으로 설정됩니다. Intune에서 연결 상태는 **활성**을 표시합니다. 활성 상태인지 확인하려면 다음 단계를 사용 합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **테넌트 관리** > **커넥터 및 토큰** > **Telecom Expense Management**를 차례로 선택합니다. **활성** 연결 상태를 찾습니다.

   ![Datalert 연결 상태가 활성임을 보여 주는 Intune 페이지](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>3단계: 디바이스에 Datalert 앱 배포

조직 소유의 줄에서만 데이터 사용량 현황이 수집되는지 확인하려면 다음을 수행해야 합니다.

- Intune에서 디바이스 범주를 만듭니다.
- 조직의 전화만 Datalert 앱의 대상으로 지정합니다.

이 섹션에서는 이러한 단계를 설명합니다.

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>디바이스 범주와 해당 범주에 매핑되는 디바이스 그룹 만들기

조직의 필요에 따라 두 개 이상의 디바이스 범주(예: 회사 및 개인)를 만듭니다. 그런 다음, 각 범주에 대한 동적 디바이스 그룹을 만듭니다. 필요에 따라 조직에 맞는 범주를 추가로 만들 수 있습니다.

Intune에서 디바이스 범주를 만드는 방법은 [그룹에 디바이스 매핑](../enrollment/device-group-mapping.md)을 참조하세요.

이러한 범주는 등록 중에 사용자에게 표시 됩니다([Android 디바이스 등록](../enrollment/android-enroll.md)). 사용자가 선택하는 범주에 따라 등록된 디바이스는 해당하는 디바이스 그룹으로 이동됩니다.

  ![정책 추가 창의 스크린 샷](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>Intune에서 Datalert 앱 추가

다음은 Datalert 앱을 추가하는 단계입니다. 예를 들어, iOS가 사용됩니다. [앱 추가](../apps/apps-add.md) 및 [범위 태그 사용](../fundamentals/scope-tags.md)에 이러한 단계에 대한 보다 구체적인 정보가 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **앱** > **모든 앱** > **추가**를 선택합니다.

2. **앱 유형**을 선택합니다. 예를 들어 iOS의 경우 **스토어 앱 - iOS**를 선택합니다.

3. **앱 스토어를 검색하고** **Datalert**를 입력하여 Dalert 앱을 찾습니다.

4. 다음과 같이 **Datalert** 앱 > **선택**을 선택합니다.

   ![앱 스토어의 Datalert 앱을 Intune 클라이언트 앱에 추가](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. 앱 정보 및 범위 태그와 같은 추가 속성을 입력합니다.

   ![Intune에서 앱에 대한 이름, 설명, OS 선택, 추가 설정 등 앱 속성을 해당 앱에 입력합니다.](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. **확인** > **추가**를 선택하여 변경 내용을 저장합니다. Datalert 앱이 목록에 표시됩니다.

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>회사 디바이스 그룹에 Datalert 앱 할당

1. **앱** > **모든 앱**에서 이전 단계에서 추가한 Datalert 앱을 선택합니다.

2. **할당** > **그룹 추가**를 선택합니다. 앱이 할당되는 방식을 선택합니다. [Intune에서 그룹에 앱 할당](../apps/apps-deploy.md)은 이러한 설정에 대한 자세한 정보를 포함합니다.

    이러한 단계에서 그룹에 대해 앱 설치를 필수 또는 선택 사항으로 설정할지 선택합니다. 다음 예에서는 필요에 따라 설치를 보여 줍니다. 필요한 경우 사용자는 디바이스를 등록한 후 Datalert 앱을 설치해야 합니다.

   ![정책 추가 창의 스크린 샷](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>4단계: Datalert 콘솔에 조직의 유료 전화 회선 추가

이제 Intune 및 Datalert 서비스가 서로 통신할 수 있도록 구성되었습니다. 다음으로, Datalert 콘솔에 조직의 유료 전화 회선을 추가합니다. 그리고 셀룰러 또는 로밍 사용량 위반에 대한 임계값 및 작업을 입력합니다. 회사 유료 전화 회선을 Datalert 콘솔에 수동으로 추가하거나, 디바이스를 Intune에 등록한 후 자동으로 추가할 수 있습니다.

이러한 항목을 설정하려면[ Microsoft Intune에 대한 Datalert 설정](http://www.datalert.fr/microsoft-intune/intune-setup)(Datalert의 웹 사이트 열림)으로 이동합니다. **설정** 탭에서 설정 마법사의 단계를 따릅니다.

  ![정책 추가 창의 스크린 샷](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

이제 Datalert 서비스가 활성 상태입니다. 데이터 사용량의 모니터링을 시작하고 구성된 사용량 제한을 초과한 디바이스에서 셀룰러 및 로밍 데이터를 해제하는 등의 작업을 시작합니다.

## <a name="end-user-enrollment"></a>최종 사용자 등록

최종 사용자 환경에서는 다음 문서를 참조하세요.

- [TEM(Telecom Expense Management)에 iOS 디바이스 등록](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [TEM(Telecom Expense Management)에 Android 디바이스 등록](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>Datalert 서비스 해제

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **테넌트 관리** > **커넥터 및 토큰** > **Telecom Expense Management**를 선택합니다.
2. **Telecom Expense Management를 사용하도록 설정하고, 사용 할당량을 초과하는 디바이스에서 셀룰러 또는 로밍 데이터를 차단**하여 **사용하지 않도록 설정**합니다.
3. 변경 내용을 **저장**합니다.

> [!IMPORTANT]
> Intune에서 Datalert 서비스를 사용하지 않도록 설정하는 경우:
>
> - 이전의 사용량 제한 위반으로 인해 디바이스에 적용된 모든 작업이 실행 취소됩니다.
> - 사용자의 데이터 액세스 및 로밍이 더 이상 차단되지 않습니다.
> - Intune에서는 서비스에서 들어오는 신호를 계속 수신하지만 이러한 신호를 무시합니다.

## <a name="next-steps"></a>다음 단계

데이터 사용량 보고는 Saaswedo의 Datalert 관리 콘솔에서 사용할 수 있습니다.
