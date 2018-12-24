---
title: Microsoft Intune에서 정책 문제 해결 - Azure | Microsoft Docs
description: Microsoft Intune에서 정책을 사용하는 경우 일반적으로 발생하는 문제와 해결 방법
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: bb55ddc283ce4633b5057d5b96ae2ed6973dcf8a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181771"
---
# <a name="troubleshoot-policies-in-intune"></a>Intune에서 정책 문제 해결

Intune 정책을 배포하고 관리하는 데 문제가 있는 경우 여기서 시작하세요. 이 문서에서는 발생할 수 있는 일반적인 몇 가지 문제와 가능한 해결 방법을 설명합니다.

## <a name="general-issues"></a>일반적인 문제

### <a name="was-a-deployed-policy-applied-to-the-device"></a>배포된 정책이 디바이스에 적용되었나요?
**문제:** 정책이 올바르게 적용되었는지 확실하지 않습니다.

Intune에서 **장치** > **모든 장치**로 이동해 장치 > **장치 구성**을 선택하면 각 장치마다 정책이 나열됩니다. 각 정책에는 **상태**가 있습니다. 상태는 디바이스에 적용되는 모든 정책 및 하드웨어와 운영 체제의 제한 사항과 요구 사항을 함께 고려할 때 적용되는 상태를 말합니다. 가능한 상태는 다음과 같습니다.

- **준수**: 장치가 설정을 준수하는 정책 및 서비스에 대한 보고서를 받았습니다.

- **적용할 수 없음**: 정책 설정을 적용할 수 없습니다. 예를 들어 iOS 디바이스의 메일 설정이 Android 디바이스에 적용되지 않습니다.

- **보류 중**: 정책이 장치에 전송되었지만, 서비스에 상태를 보고하지 않았습니다. 예를 들어 Android에서의 암호화의 경우, 사용자가 암호화를 사용하도록 설정해야 하고 보류 중으로 표시될 수 있습니다.

> [!NOTE]
> 제한 수준이 다른 두 정책을 같은 디바이스나 사용자에 적용하면 보다 제한적인 정책이 적용됩니다.

## <a name="issues-with-enrolled-devices"></a>등록된 디바이스 문제

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>경고: Exchange에 액세스 규칙 저장 실패
**문제**: 관리 콘솔에에 **Exchange에 액세스 규칙 저장 실패**  라는 경고가 표시됩니다.

관리 콘솔의 Exchange 온-프레미스 정책 작업 영역에서 정책을 만들었지만, O365를 사용하고 있는 경우, 구성된 정책 설정이 Intune에 의해 적용되지 않습니다. 경고의 정책 소스를 확인합니다.  Exchange 온-프레미스 정책에 따라 작업 영역에서는 레거시 규칙을 삭제합니다. 레거시 규칙은 Intune 내에서 온-프레미스 Exchange의 전역 Exchange 규칙으로 O365와는 관계가 없습니다. 그런 다음 O365에 대한 새 정책을 만듭니다.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>등록된 다양한 디바이스에 대한 보안 정책을 변경할 수 없음
Windows Phone 디바이스는 MDM 또는 EAS를 통해 보안 정책을 설정하면 이 정책의 보안 강도가 줄어드는 것을 허용하지 않습니다. 예를 들어 **문자 암호의 최소 수** 를 8로 설정한 다음 4로 줄이려고 합니다. 더 제한적인 정책이 이미 디바이스에 적용되었습니다.

디바이스 플랫폼에 따라서는 정책을 덜 안전한 값으로 변경하려는 경우 보안 정책을 다시 설정해야 할 수 있습니다.

예를 들어, Windows의 바탕 화면에서 오른쪽에서 살짝 밀어 **참 메뉴** 모음을 엽니다. **설정** > **제어판**을 선택하고 **사용자 계정**을 선택합니다. 왼쪽에서 **보안 정책 재설정** 링크를 선택하고 **정책 재설정**을 선택합니다.

Android, Windows Phone 8.1 이상 및 iOS와 같은 기타 MDM 디바이스의 경우 제한적인 정책을 적용할 수 있도록 사용을 중지하고 서비스에 다시 등록해야 해야 합니다.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Intune 소프트웨어 클라이언트를 실행하는 PC 관련 문제

클래식 포털에 적용됩니다.

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>policyplatform.log의 Microsoft Intune 정책 관련 오류
Intune 소프트웨어 클라이언트로 관리되는 Windows PC의 경우 policyplatform.log 파일의 정책 오류는 디바이스의 Windows UAC(사용자 계정 컨트롤)에서 기본값이 아닌 설정을 사용한 결과일 수 있습니다. 기본값이 아닌 일부 UAC 설정은 Microsoft Intune 클라이언트 설치와 정책 실행에 영향을 줄 수 있습니다.

#### <a name="resolve-uac-issues"></a>UAC 문제 해결

1. 컴퓨터를 사용 중지합니다. [장치 제거](devices-wipe.md)를 참조하세요.

2. 클라이언트 소프트웨어가 제거될 때까지 20분 정도 기다립니다.

    > [!NOTE]
    > 프로그램 및 기능에서 클라이언트를 제거하지 마세요.

3. 시작 메뉴에서 **UAC**를 입력하여 사용자 계정 컨트롤 설정을 엽니다.

4. 알림 슬라이더를 기본 설정으로 이동합니다.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>오류: 0x80041013 컴퓨터에서 값을 가져올 수 없습니다.
로컬 시스템의 시간이 5분 이상 동기화되지 않는 경우에 발생할 수 있습니다. 로컬 컴퓨터의 시간이 동기화되지 않으면 타임스탬프가 유효하지 않으므로 보안 트랜잭션이 실패합니다.

이 문제를 해결하려면 로컬 시스템 시간을 인터넷 시간 또는 네트워크의 도메인 컨트롤러에서 설정된 시간에 최대한 가깝게 설정합니다.

### <a name="next-steps"></a>다음 단계
문제 해결 정보가 도움이 되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](get-support.md)의 설명에 따라 Microsoft 지원에 문의하세요.
