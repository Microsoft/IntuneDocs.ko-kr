---
title: 앱 보호 정책 조건부 시작 작업을 사용하여 데이터 초기화
titleSuffix: Microsoft Intune
description: Microsoft Intune에서 앱 보호 정책 조건부 시작 작업을 사용하여 선택적으로 데이터를 초기화하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a0440e2d6f5890b20ccf020c40bb1037bcfcae38
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564130"
---
# <a name="selectively-wipe-data-using-app-protection-policy-conditional-launch-actions-in-intune"></a>Intune에서 앱 보호 정책 조건부 시작 작업을 사용하여 선택적으로 데이터 초기화

Intune 앱 보호 정책을 사용하면 최종 사용자가 회사 앱 또는 계정에 액세스하지 못하게 차단하는 설정을 구성할 수 있습니다. 이러한 설정은 무단 해제 디바이스 및 최소 OS 버전과 같은 사항에 대해 조직에서 설정한 데이터 재배치 및 액세스 요구 사항을 대상으로 합니다.
 
이러한 설정을 사용하여 비준수에 대해 수행할 작업으로 최종 사용자 디바이스에서 회사의 회사 데이터를 초기화하도록 명시적으로 선택할 수 있습니다. 일부 설정의 경우 액세스 차단 및 다른 지정된 값에 따라 데이터 초기화와 같은 여러 작업을 구성할 수 있습니다.

## <a name="create-an-app-protection-policy-using-conditional-launch-actions"></a>조건부 시작 작업을 사용하여 앱 보호 정책 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **앱 보호 정책**을 선택합니다.
3. **정책 만들기**를 클릭하고 정책에 대한 디바이스의 플랫폼을 선택합니다. 
4. **필요한 설정 구성**을 클릭하여 정책에 대해 구성할 수 있는 설정 목록을 볼 수 있습니다. 
5. [설정] 창에서 아래로 스크롤하면 편집 가능한 테이블이 있는 **조건부 시작**이라는 섹션이 표시됩니다.

    ![Intune 앱 보호 액세스 작업의 스크린샷](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions01.png)

6. **설정**을 선택하고 사용자가 회사 앱에 로그인하기 위해 충족해야 하는 **값**을 입력합니다. 
7. 사용자가 요구 사항을 충족하지 않을 경우 **작업**을 선택합니다. 경우에 따라 단일 설정에 대해 여러 작업을 구성할 수 있습니다. 자세한 내용은 [앱 보호 정책을 만들고 할당하는 방법](app-protection-policies.md)을 참조하세요.

## <a name="policy-settings"></a>정책 설정 

앱 보호 정책 설정 테이블에는 **설정**, **값** 및 **작업**에 대한 열이 있습니다.

### <a name="ios-policy-settings"></a>iOS 정책 설정
iOS의 경우 **설정** 드롭다운을 사용하여 다음 설정에 대한 작업을 구성할 수 있습니다.
- 최대 PIN 시도 횟수
- 오프라인 유예 기간
- 무단 해제/루팅된 디바이스
- 최소 OS 버전
- 최소 앱 버전
- 최소 SDK 버전
- 디바이스 모델
- 허용된 최대 디바이스 위협 수준

**디바이스 모델** 설정을 사용하려면 세미콜론으로 구분된 iOS 모델 식별자 목록을 입력합니다. 이러한 값은 대/소문자를 구분하지 않습니다. '디바이스 모델'의 입력에 대한 Intune 보고 외에, [HockeyApp의 지원 설명서](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types) 또는 이 [타사 GitHub 리포지토리](https://gist.github.com/adamawolf/3048717)의 디바이스 유형 열에서도 iOS 모델 식별자를 찾을 수 있습니다.<br>
입력의 예: *iPhone5,2;iPhone5,3*

최종 사용자 디바이스에서 Intune 클라이언트는 애플리케이션 보호 정책에 대한 Intune에 지정된 디바이스 모델 문자열의 단순 일치를 기반으로 작업을 수행합니다. 일치 여부는 전적으로 디바이스가 보고하는 내용에 따라 결정됩니다. 사용자(IT 관리자)는 다양한 디바이스 제조업체 및 모델을 기반으로 하며 소규모 사용자 그룹을 대상으로 이 설정을 테스트하여 의도한 동작이 발생하는지 확인하는 것이 좋습니다. 기본값은 **구성되지 않음**입니다.<br>
다음 작업 중 하나를 설정합니다. 
- 지정됨(비지정 차단)
- 지정됨(비지정 초기화)

**IT 관리자가 동일한 Intune 사용자의 동일한 앱을 대상으로 하는 정책 간 다른 iOS 모델 식별자 목록을 입력하면 어떻게 되나요?**<br>
구성된 값에 대한 두 개의 앱 보호 정책 간 충돌이 발생하면 Intune은 일반적으로 가장 제한적인 방식을 사용합니다. 따라서 대상 Intune 사용자에 의해 열리는 대상 앱으로 전송되는 결과 정책은 동일한 앱/사용자 조합을 대상으로 하는 *정책A* 및 *정책 B*에 나열된 iOS 모델 식별자의 교차점이 됩니다. 예를 들어 ‘정책 A’는 “iPhone5,2;iPhone5,3”을 지정하고 ‘정책 B’는 “iPhone5,3”을 지정합니다. ‘정책 A’와 ‘정책 B’ 둘 모두를 대상으로 하는 Intune 사용자의 결과 정책은 “iPhone5,3”이 됩니다.     

### <a name="android-policy-settings"></a>Android 정책 설정

Android의 경우 **설정** 드롭다운을 사용하여 다음 설정에 대한 작업을 구성할 수 있습니다.
- 최대 PIN 시도 횟수
- 오프라인 유예 기간
- 무단 해제/루팅된 디바이스
- 최소 OS 버전
- 최소 앱 버전
- 최소 패치 버전
- 디바이스 제조업체
- SafetyNet 디바이스 증명
- 앱에서 위협 검색 필요
- 최소 회사 포털 버전
- 허용된 최대 디바이스 위협 수준

**최소 회사 포털 버전**으로는 최종 사용자의 디바이스에 적용되는 정의된 특정 최소 버전의 회사 포털을 지정할 수 있습니다. 이 조건부 시작 설정을 통해서는 각 값이 일치하지 않을 때 가능한 조치로서 **액세스 차단**, **데이터 지우기**, **경고** 값을 설정할 수 있습니다. 이 값에 가능한 형식은 *[주].[부]* , *[주].[부].[빌드]* , or *[주].[부].[빌드].[수정]* 의 패턴을 따릅니다. 일부 최종 사용자는 즉각적인 강제 업데이트를 선호하지 않을 수 있다는 점을 고려하면 이 설정을 구성할 때 ‘경고’ 옵션이 가장 바람직할 수 있습니다. Google Play Store는 앱 업데이트의 델타 바이트를 전송만 한다는 데서 바람직하다고 할 수 있지만, 이 또한 사용자가 업데이트가 필요한 시점의 데이터일 경우 사용을 원하지 않을 수도 있는 대용량 데이터가 될 소지가 있습니다. 업데이트를 강제로 적용하여 업데이트된 앱을 다운로드하면 업데이트 당시에 예기치 않은 데이터 변경이 발생할 수 있습니다. **최소 회사 포털 버전** 설정은 구성될 경우 버전 5.0.4560.0이나 그 이후의 회사 포털을 받는 최종 사용자에게 영향을 미칩니다. 이 설정은 이 기능이 릴리스되는 버전 이전의 회사 포털을 사용할 경우 영향을 미치지 않습니다. 앱 자동 업데이트를 디바이스에서 사용 중인 최종 사용자에게는 최신 버전의 회사 포털을 사용하고 있을 수 있으므로 이 기능의 대화 상자가 표시되지 않을 수도 있습니다. 이 설정은 등록 및 미등록 디바이스용 앱 보호 장치가 있는 Android로 한정됩니다.

**디바이스 제조업체** 설정을 사용하려면 세미콜론으로 구분된 Android 제조업체 목록을 입력합니다. 이러한 값은 대/소문자를 구분하지 않습니다. Intune 보고 외에, 디바이스 설정에서도 디바이스의 Android 제조업체를 찾을 수 있습니다. <br>
입력의 예: ‘제조업체 A;제조업체 B’  

>[!NOTE]
> 다음은 Intune을 사용하여 디바이스에서 보고하는 일반적인 제조업체로, 입력으로 사용할 수 있습니다. Asus;Blackberry;Bq;Gionee;Google;Hmd global;Htc;Huawei;Infinix;Kyocera;Lemobile;Lenovo;Lge;Motorola;Oneplus;Oppo;Samsung;Sharp;Sony;Tecno;Vivo;Vodafone;Xiaomi;Zte;Zuk

최종 사용자 디바이스에서 Intune 클라이언트는 애플리케이션 보호 정책에 대한 Intune에 지정된 디바이스 모델 문자열의 단순 일치를 기반으로 작업을 수행합니다. 일치 여부는 전적으로 디바이스가 보고하는 내용에 따라 결정됩니다. 사용자(IT 관리자)는 다양한 디바이스 제조업체 및 모델을 기반으로 하며 소규모 사용자 그룹을 대상으로 이 설정을 테스트하여 의도한 동작이 발생하도록 합니다. 기본값은 **구성되지 않음**입니다.<br>
다음 작업 중 하나를 설정합니다. 
- 지정됨(지정되지 않은 경우 차단)
- 지정됨(지정되지 않은 경우 초기화)

**IT 관리자가 동일한 Intune 사용자의 동일한 앱을 대상으로 하는 정책 간 다른 Android 제조업체 목록을 입력하면 어떻게 되나요?**<br>
구성된 값에 대한 두 개의 앱 보호 정책 간 충돌이 발생하면 Intune은 일반적으로 가장 제한적인 방식을 사용합니다. 따라서 대상 Intune 사용자에 의해 열리는 대상 앱으로 전송되는 결과 정책은 동일한 앱/사용자 조합을 대상으로 하는 *정책A* 및 *정책 B*에 나열된 Android 제조업체의 교차점이 됩니다. 예를 들어 ‘정책 A’는 “Google;Samsung”을 지정하고 ‘정책 B’는 “Google”을 지정합니다. ‘정책 A’와 ‘정책 B’ 둘 모두를 대상으로 하는 Intune 사용자의 결과 정책은 “Google”이 됩니다.     

### <a name="additional-settings-and-actions"></a>추가 설정 및 작업 

기본적으로 **액세스용 PIN 필요** 설정이 **예**로 설정된 경우, 테이블에는 **오프라인 유예 기간** 및 **최대 PIN 입력 시도**로 구성된 설정으로 채워진 행이 있습니다.
 
설정을 구성하려면 **설정** 열의 드롭다운에서 설정을 선택합니다. 값을 설정해야 하는 경우 설정을 선택하면 동일한 행의 **값** 열 아래에서 편집 가능한 텍스트 상자가 활성화됩니다. 또한 드롭다운은 설정에 적용할 수 있는 조건부 실행 작업 집합과 함께 **작업** 열 아래에서 활성화됩니다. 

다음 목록은 일반적인 작업 목록을 제공합니다.
- **액세스 차단** – 최종 사용자가 회사 앱에 액세스하는 것을 차단합니다.
- **데이터 초기화** – 최종 사용자의 디바이스에서 회사 데이터를 초기화합니다.
- **경고** – 최종 사용자에게 경고 메시지로 대화 상자를 제공합니다.

**최소 OS 버전** 설정과 같은 일부의 경우에는 다른 버전 번호에 따라 적용 가능한 모든 작업을 수행하도록 설정을 구성할 수 있습니다. 

![앱 보호 액세스 작업 - 최소 OS 버전 스크린샷](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions05.png)

설정이 완전히 구성되면 행은 읽기 전용 보기에 표시되며 언제든지 편집할 수 있습니다. 또한 행에 **설정** 열의 드롭다운을 사용하여 선택할 수 있습니다. 이미 구성되어 있고 여러 작업을 허용하지 않는 설정은 드롭다운에서 선택할 수 없습니다.

## <a name="next-steps"></a>다음 단계

Intune 앱 보호 정책에 대한 자세한 내용은 다음을 참조하세요.
- [앱 보호 정책을 만들고 할당하는 방법](app-protection-policies.md)
- [iOS 앱 보호 정책 설정](app-protection-policy-settings-ios.md)
- [Microsoft Intune의 Android 앱 보호 정책 설정](app-protection-policy-settings-android.md) 
