---
title: Telecom Expense Management 서비스 설정
titleSuffix: Microsoft Intune
description: Intune과 Saaswedo Telecom Expense Management 서비스를 통합합니다.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b3ca1b95a6dcf7bdc30b61469fa747894d20fe73
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188095"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Intune에서 Telecom Expense Management 서비스 설정
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune을 사용하면 회사 소유의 모바일 장치에서 데이터 사용으로 발생하는 통신 비용을 관리할 수 있습니다. 이 기능을 지원하기 위해 Intune에는 타사 소프트웨어 개발자인 Saaswedo의 [Datalert Telecom Expense Management](http://datalert.biz/get-started) 솔루션이 통합되어 있습니다. Datalert는 통신 데이터 사용량을 관리할 수 있는 실시간 통신 비용 관리 소프트웨어입니다. 이 소프트웨어는 Intune 관리 장치에 대해 로밍 초과분과 비용이 많이 들고 예기치 않은 데이터를 방지하게 해줍니다.

Intune은 Datalert와의 통합을 통해 로밍 및 국내 데이터 사용량 제한을 중앙에서 설정, 모니터링 및 적용할 수 있도록 지원합니다. 정의된 임계값을 초과할 경우 자동화된 경고가 작동됩니다. 사용자가 (임계값을 초과하거나 로밍을 해제하는 등) 개인 또는 최종 사용자 그룹에 여러 작업을 적용하도록 서비스를 구성할 수 있습니다. Datalert 관리 콘솔에서 데이터 사용량 및 모니터링 정보를 제공하는 보고서를 사용할 수 있습니다.

다음 다이어그램에서는 Intune이 Datalert에 어떻게 통합되어 있는지를 보여 줍니다.

  ![Intune과 Datalert 통합을 보여 주는 다이어그램](./media/tem-datalert-intune-solution-diagram.png)

Intune에서 Datalert 서비스를 사용하려면 먼저 Datalert 콘솔 및 Intune에서 설정을 구성해야 합니다. Datalert 서비스 및 Intune에 대한 연결을 설정해야 합니다. Datalert 측의 연결이 설정되었지만 Intune 측의 연결이 설정되지 않은 경우에는 Intune에서 통신을 수신하지만 이를 무시합니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

- Samsung Knox
- iOS 8.0 이상

## <a name="prerequisites"></a>전제 조건

- Microsoft Intune 구독 및 Azure Portal 액세스 권한
- Datalert Telecom Expense Management 서비스 구독

## <a name="list-of-telecom-expense-management-providers"></a>Telecom Expense Management 공급자 목록

Intune은 현재 다음 Telecom Expense Management 공급자와 통합되어 있습니다.

[Saaswedo Datalert Telecom Expense Management 서비스](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>Intune 및 Datalert 통합 솔루션 배포

시작하기 전에 Intune 및 Datalert Telecom Expense Management 서비스 구독이 있는지 확인합니다.

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>1단계: Microsoft Intune에 Datalert 서비스 연결

1. 관리자 자격 증명을 사용하여 Datalert 관리 콘솔에 로그인합니다.

2. Datalert 관리 콘솔에서 **설정** 탭으로 이동한 다음 **MDM configuration**(MDM 구성)으로 이동합니다.

3. 페이지 하단에서 **차단 해제**를 선택하면 페이지의 설정을 수정할 수 있습니다.

4. **Intune / Datalert Connection** 섹션에서 **Server MDM**에 대해 **Microsoft Intune**을 선택합니다.    

5. **Azure AD 도메인**에 Azure 테넌트 ID를 입력한 다음, **연결**을 선택합니다.

    **연결**을 선택하면 Datalert 서비스가 Intune에 체크 인되어 Datalert와 Intune의 기존 연결이 없는지 확인합니다. 몇 초 후 Microsoft 로그인 페이지가 표시되고 Datalert Azure 인증이 시작됩니다.

6. Microsoft 인증 페이지에서 **동의함**을 선택합니다. Datalert **thank you** 페이지로 리디렉션됩니다. 이 페이지는 몇 초 후 닫힙니다. Datalert에서 연결의 유효성을 검사하고 유효성이 확인된 항목 목록 옆에 녹색 확인 표시를 표시합니다. 유효성 검사에 실패하는 경우 메시지가 빨간색으로 표시되면 Datalert 지원 팀에 문의해 도움을 요청하십시오.

    다음 스크린샷에서는 연결되면 볼 수 있는 녹색 확인 표시를 보여 줍니다.

   ![연결 성공을 보여 주는 Datalert 페이지](./media/tem-datalert-connection.png)

7. **Datalert App / ADAL Consent** 섹션에서 스위치를 **켜기**로 설정합니다. Microsoft 인증 페이지에서 **동의함**을 선택합니다. Datalert **thank you** 페이지로 리디렉션됩니다. 이 페이지는 몇 초 후 닫힙니다. Datalert에서 연결의 유효성을 검사하고 유효성이 확인된 항목 목록 옆에 녹색 확인 표시를 표시합니다. 유효성 검사에 실패하는 경우 메시지가 빨간색으로 표시되면 Datalert 지원 팀에 문의해 도움을 요청하십시오.    

    다음 스크린샷에서는 연결되면 볼 수 있는 녹색 확인 표시를 보여 줍니다.

   ![연결 성공을 보여 주는 Datalert 페이지](./media/tem-datalert-adal-consent.png)

8. **MDM 프로필 관리(선택 사항)** 섹션에서 스위치를 **켜기**로 설정하여 Datalert가 정책을 설정하는 데 도움이 되도록 Intune에서 사용할 수 있는 프로필을 읽도록 허용합니다. Microsoft 인증 페이지에서 **동의함**을 선택합니다. Datalert **thank you** 페이지로 리디렉션됩니다. 이 페이지는 몇 초 후 닫힙니다. Datalert에서 연결의 유효성을 검사하고 유효성이 확인된 항목 목록 옆에 녹색 확인 표시를 표시합니다. 유효성 검사에 실패하는 경우 메시지가 빨간색으로 표시되면 Datalert 지원 팀에 문의해 도움을 요청하십시오.    

    다음 스크린샷에서는 연결되면 볼 수 있는 녹색 확인 표시를 보여 줍니다.

   ![연결 성공을 보여 주는 Datalert 페이지](./media/tem-datalert-mdm-profiles.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>2단계: Intune에서 Telecom Expense Management 기능이 활성 상태인지 확인

위 1단계를 완료하면 연결이 자동으로 사용하도록 설정되고 Azure Portal에서 연결 상태가 **활성**으로 표시됩니다. 다음 단계에서는 **활성** 상태인지 확인하는 방법을 설명합니다.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.

2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.

3. **Intune** 창에서 **장치 구성**을 선택합니다.

4. **장치 구성** 창에서 **설정** > **Telecom Expense Management**를 선택합니다.

   페이지 맨 위에서 **활성** 연결 상태를 찾습니다.

   ![Datalert 연결 상태가 활성임을 보여 주는 Intune 페이지](./media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>3단계: 회사에 등록된 장치에 Datalert 앱 배포

회사 소유의 선에서만 데이터 사용량이 수집되었는지 확인하려면 다음 두 가지 작업을 수행해야 합니다.
- Intune에서 장치 범주 만들기
- Datalert 앱은 회사 전화만 대상으로 합니다.

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>장치 범주와 해당 범주에 매핑되는 장치 그룹 정의

조직의 필요에 따라 두 개 이상의 장치 범주(예: 회사 및 개인)를 만듭니다. 그런 다음, 각 범주에 대한 동적 장치 그룹을 만듭니다. 필요에 따라 조직에 맞는 범주를 추가로 만들 수 있습니다.

이러한 범주는 사용자가 등록할 때 표시됩니다. 사용자가 선택하는 범주에 따라 등록된 장치는 해당하는 장치 그룹으로 이동됩니다. 장치 범주를 만드는 방법에 대한 단계는 [Map devices to groups](device-group-mapping.md)(그룹에 장치 매핑)를 참조하세요.

  ![정책 추가 창의 스크린 샷](./media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Intune에서 Datalert 앱 만들기

다음 단계에 따라 Intune에서 각 플랫폼용 Datalert 앱을 만듭니다. 다음 단계에서는 iOS를 예로 듭니다.

1. [Azure Portal](https://portal.azure.com)의 **Intune** 창에서 **클라이언트 앱**을 선택합니다.

2. **클라이언트 앱** 창에서 **관리** > **앱**을 선택합니다.

3. **추가**를 선택하여 앱을 추가합니다.

4. 앱 유형을 선택합니다. 예를 들어 iOS의 경우 **iOS 스토어 앱**을 선택합니다.

5. **앱 스토어 검색**에서 검색 창에 **Datalert**를 입력하여 Datalert 앱을 검색합니다.

6. **Datalert** 앱을 선택하고 **선택**을 선택합니다.

   ![정책 추가 창의 스크린 샷](./media/tem-select-app-from-apple-app-store.png)

7. 나머지 단계를 완료하여 iOS용 앱을 만듭니다.

   ![정책 추가 창의 스크린 샷](./media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>회사 장치 그룹에 Datalert 앱 할당

1. **클라이언트 앱 - 앱** 창에서 이전 단계에서 만든 iOS Datalert 앱을 선택합니다.

2. **앱** 창에서 **관리** > **할당**을 선택합니다.

3. **그룹 추가**를 선택하고 단계에 따라 회사 장치 그룹을 선택합니다.

4. 그룹에 대해 앱 설치를 필수 또는 선택 사항으로 설정할지 선택합니다. 다음 예제 스크린샷에서는 설치가 필수임을 보여 줍니다. 이 경우 사용자는 장치를 등록한 후 Datalert 앱을 설치해야 합니다.

   ![정책 추가 창의 스크린 샷](./media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>4단계: Datalert 콘솔에 회사 유료 전화 회선 추가

지금까지 Intune 및 Datalert 서비스가 서로 통신할 수 있도록 구성했습니다. 이제 Datalert 콘솔에 회사 유료 전화 회선을 추가하고 셀룰러 또는 로밍 사용량에 대한 임계값과 위반 시 작업을 정의해야 합니다. 회사 유료 전화 회선을 Datalert 콘솔에 수동으로 추가하거나, 장치를 Intune에 등록한 후 자동으로 추가할 수 있습니다.

이러한 항목을 설정하려면 [Microsoft Intune에 대한 Datalert 설정 페이지](http://www.datalert.fr/microsoft-intune/intune-setup)(http://www.datalert.fr/microsoft-intune/intune-setup))의 **설정** 탭에서 설정 마법사의 단계를 따르세요.

  ![정책 추가 창의 스크린 샷](./media/tem-add-phone-lines-to-datalert-console.png)


이제 Datalert 서비스가 활성화되어 데이터 사용량을 모니터링하고 구성된 사용량 제한을 초과한 장치에서 셀룰러 및 로밍 데이터를 해제하는 등의 작업을 시작합니다.

## <a name="client-enrollment-experience"></a>클라이언트 등록 환경
클라이언트 등록 환경에 대해서는 다음을 참조하세요.
-   [TEM(Telecom Expense Management)에 iOS 장치 등록](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-   [TEM(Telecom Expense Management)에 Android 장치 등록](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>Datalert 서비스 해제

Azure Portal에서 Datalert 서비스를 해제한 경우

- 이전의 사용량 제한 위반으로 인해 장치에 적용된 모든 작업이 실행 취소됩니다.
- 사용자의 데이터 액세스 및 로밍이 더 이상 차단되지 않습니다.
- Intune에서는 서비스에서 들어오는 신호를 계속 수신하지만 이를 무시합니다.

**서비스를 해제하려면**

1. Azure Portal의 **Telecom Expense Management** 창에서 **사용 안 함**을 선택합니다.

2. **저장**을 선택합니다.

## <a name="viewing-data-usage-and-roaming-reports"></a>데이터 사용량 및 로밍 보고서 보기

현재 데이터 사용량 보고는 Saaswedo의 Datalert 관리 콘솔에서만 사용할 수 있습니다.

Datalert 앱을 설치하는 단계에 대한 지침은 곧 추가할 예정입니다.
