---
title: Intune의 장치 정책, 프로필 및 Q&A - Azure | Microsoft Docs
description: 디바이스를 구성하고, 회사 리소스에 대한 액세스를 가져오고, 조건부 액세스를 활성화하고 회사 디바이스를 등록하는 정책을 포함한 Microsoft Intune에서 사용할 수 있는 다른 정책 및 프로필에 대해 알아봅니다. 또한 자주 묻는 질문에 대한 답변을 가져옵니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 3b1115a91707c639caba6410ace3c2e255e40a39
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185001"
---
# <a name="manage-settings-and-features-on-your-devices-with-intune-policies"></a>Intune 정책을 사용하여 디바이스의 설정 및 기능 관리

Microsoft Intune *정책*은 모바일 디바이스 및 컴퓨터에서 기능을 제어하는 설정 그룹입니다. 권장되는 또는 사용자 지정 설정을 포함하는 템플릿을 사용하여 정책을 만듭니다. 그런 다음, 디바이스 또는 사용자 그룹에 배포합니다.

## <a name="types-of-policies"></a>정책 유형

Intune 정책은 다음과 같은 범주로 분류됩니다. 사용하는 범주는 정책을 만들고 배포하는 방법에 영향을 줍니다.

- **구성 정책:** 회사 리소스에 대한 액세스를 포함하여 장치에 대한 보안 설정 및 기능을 관리하는 데 널리 사용됩니다. [Intune 장치 프로필](device-profiles.md)에서 시작합니다.
- **장치 준수 정책**: 장치가 조건부 액세스 정책을 준수하는 것으로 간주되도록 준수해야 하는 규칙 및 설정을 정의합니다. 준수 정책을 사용하여 조건부 액세스와 독립적으로 디바이스의 준수를 모니터링하고 수정할 수도 있습니다. [장치 준수 정책](device-compliance-get-started.md)을 시작합니다.
- **조건부 액세스 정책:** 입력하는 조건에 따라 이메일 및 기타 서비스를 보호하는 데 도움이 됩니다. [조건부 액세스란](conditional-access.md) 및 [조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)은 시작하기 좋은 리소스입니다.
- **회사 장치 등록 정책:** 회사 장치 등록 정책에 대한 자세한 내용은 [iOS 장치 등록](ios-enroll.md)을 참조하세요.

## <a name="frequently-asked-questions-about-intune-policies"></a>Intune 정책에 대한 질문과 대답

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-being-deployed"></a>정책 또는 앱을 배포한 후 모바일 디바이스에서 해당 정책 또는 앱을 수신할 때까지 걸리는 시간
정책 또는 앱이 배포되면 Intune에서는 Intune 서비스에 체크 인해야 하는 알림을 디바이스에 즉시 보내기 시작합니다. 이 단계는 대개 5분 이내에 완료됩니다.

첫 번째 알림을 보낸 후 디바이스가 정책을 수신하기 위해 체크 인하지 않으면 알림을 3번 더 보냅니다.  디바이스가 꺼져 있거나 네트워크에 연결되어 있지 않은 등 오프라인 상태인 경우에는 알림을 받지 못할 수 있습니다. 이 경우 디바이스는 다음과 같이 Intune 서비스를 사용하여 예약된 다음 체크 인에서 정책을 가져옵니다.

| 플랫폼 | 체크 인 빈도 |
| --- | --- |
| iOS | 6시간마다 | 
| Mac OS X | 6시간마다 |
| Android | 8시간마다 | 
| Windows Phone | 8시간마다 | 
| Windows 8.1  | 8시간마다 |  
| 디바이스로 등록된 Windows 10 PC | 8시간마다 | 

최근 등록된 디바이스인 경우 다음과 같이 체크 인 빈도가 더 빈번합니다.

| 플랫폼 | 빈도 |
| --- | --- |
| iOS | 6시간 동안 15분마다/그 이후에는 6시간마다 |  
| Mac OS X | 6시간 동안 15분마다/그 이후에는 6시간마다 | 
| Android | 15분 동안 3분마다/그 이후 2시간 동안은 15분마다/그 이후에는 8시간마다 | 
| Windows Phone | 15분 동안 5분마다/그 이후 2시간 동안은 15분마다/그 이후에는 8시간마다 | 
| 디바이스로 등록된 Windows PC | 30분 동안 3분마다/그 이후에는 8시간마다 | 

사용자는 언제든지 회사 포털 앱을 열어 디바이스를 동기화해 즉시 정책을 확인할 수도 있습니다.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Intune에서 디바이스에 알림을 즉시 보내도록 하는 작업
디바이스는 체크 인하라는 알림을 받거나 정기 예약 체크 인 중에 Intune에 체크 인합니다.  초기화, 잠금, 암호 재설정, 앱 배포, 프로필 배포(Wi-Fi, VPN, 이메일) 또는 정책 배포와 같은 작업으로 디바이스나 사용자를 대상으로 지정하면 Intune에서는 Intune 서비스에 체크 인하라는 알림을 디바이스에 즉시 보내기 시작합니다.

회사 포털에서 연락처 정보를 수정하는 등의 기타 변경 작업을 수행하는 경우에는 디바이스에 알림이 즉시 전송되지 않습니다.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-are-applied"></a>여러 정책을 같은 사용자 또는 디바이스에 배포하는 경우 적용되는 설정을 확인하는 방법
둘 이상의 정책을 같은 사용자 또는 디바이스에 배포할 때는 개별 설정 수준에서 적용되는 설정을 평가합니다.

- 준수 정책 설정은 항상 구성 정책 설정보다 우선적으로 적용됩니다.

- 다른 준수 정책의 동일 설정과 대조하여 평가하는 경우 더 제한적인 준수 정책 설정이 적용됩니다.

- 구성 정책 설정이 다른 구성 정책의 설정과 충돌하는 경우 이 충돌은 Intune에 표시됩니다. 수동으로 이러한 충돌을 해결합니다.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-applies-to-the-app"></a>모바일 응용 프로그램 관리 정책이 서로 충돌하는 경우 앱에 적용되는 대상
다시 설정 전까지의 PIN 입력 시도와 같이 숫자 입력 필드에 대한 설정을 제외하면, 충돌하는 값은 MAM 정책에서 사용 가능한 가장 제한적인 설정으로 지정됩니다.  권장 설정 옵션을 사용하여 콘솔에서 MAM 정책을 만든 것처럼 숫자 입력 필드는 값과 동일하게 설정됩니다.

두 정책 설정이 동일하면 충돌이 발생합니다.  복사/붙여넣기 설정을 제외하면 동일한 두 MAM 정책을 구성한 경우를 예로 들 수 있습니다.  이 시나리오에서는 복사/붙여넣기 설정이 가장 제한적인 값으로 설정되지만, 나머지 설정은 구성된 대로 적용됩니다.

정책 하나를 앱에 배포하여 적용한 후에 두 번째 정책을 배포하는 경우 첫 번째 앱이 우선권을 가지게 되므로 적용된 상태로 유지됩니다. 두 번째 정책은 충돌하는 정책으로 표시됩니다. 둘 다 동시에 적용되면 이전 정책이 없으므로 두 정책이 충돌하게 됩니다. 충돌하는 설정은 가장 제한적인 값으로 설정됩니다.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>iOS 사용자 지정 정책 충돌 시의 결과
Intune은 Apple 구성 파일 또는 사용자 지정 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 정책 페이로드를 평가하지 않으며 전달 메커니즘으로만 작동합니다.

사용자 지정 정책을 배포할 때는 구성된 설정이 준수, 구성 또는 기타 사용자 지정 정책과 충돌하지 않는지 확인해야 합니다. 설정이 충돌하는 사용자 지정 정책에서는 설정이 임의 순서에 따라 적용됩니다.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>정책이 삭제되거나 더 이상 적용할 수 없는 경우 어떻게 되나요?
정책을 삭제하거나 배포된 정책이 있는 그룹에서 디바이스를 제거하면, 정책 및 설정이 다음 목록에 따라 디바이스에서 제거됩니다.

#### <a name="enrolled-devices"></a>등록된 디바이스

- Wi-Fi, VPN, 인증서 및 전자 메일 프로필: 이러한 프로필은 지원되는 모든 등록된 디바이스에서 제거됩니다.
- 다른 모든 정책 유형:
  - **Windows 및 Android 장치**: 설정이 장치에서 제거되지 않습니다.
  - **Windows Phone 8.1 장치**: 다음 설정이 제거됩니다.
    - 모바일 디바이스의 잠금을 해제하는 데 암호 필요
    - 단순 암호 허용
    - 최소 암호 길이
    - 필수 암호 유형
    - 암호 만료(일)
    - 암호 기록 기억
    - 디바이스를 초기화하기 전까지 허용되는 로그인 반복 오류 횟수
    - 암호를 요구하기 전까지 비활성 시간(분)
    - 필수 암호 유형 - 최소 문자 집합 수
    - 카메라 허용
    - 모바일 디바이스 암호화 필요
    - 이동식 저장소 허용
    - 웹 브라우저 허용
    - 앱 스토어 허용
    - 화면 캡처 허용
    - 지리적 위치 허용
    - Microsoft 계정 허용
    - 복사 및 붙여넣기 허용
    - Wi-Fi 테더링 허용
    - 무료 Wi-Fi 핫스팟에 자동 연결 허용
    - Wi-Fi 핫스팟 보고 허용
    - 초기화 허용
    - Bluetooth 허용
    - NFC 허용
    - Wi-Fi 허용

  - **iOS**: 다음을 제외한 모든 설정이 제거됩니다.
    - 음성 로밍 허용
    - 데이터 로밍 허용
    - 로밍하는 동안 자동 동기화 허용

### <a name="where-can-i-find-help-troubleshooting-policies"></a>문제 해결 정책 도움말은 어디서 찾을 수 있나요?

[정책 문제 해결](troubleshoot-policies-in-microsoft-intune.md)을 참조하세요.
