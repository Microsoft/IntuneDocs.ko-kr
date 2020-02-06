---
title: Microsoft Intune - Azure에서 디바이스 작동 문제 해결 | Microsoft Docs
description: 디바이스 작업 문제 해결을 위한 도움말을 확인하세요.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d4517d89e3b7365834e904c815b30a362540906
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755598"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Intune에서 디바이스 작업 문제 해결

Microsoft Intune에는 관리 디바이스에 도움이 되는 많은 작업이 있습니다. 이 문서에서는 디바이스 작업 문제 해결에 도움이 되는 일반적인 질문에 대한 대답을 제공합니다.

## <a name="disable-activation-lock-action"></a>활성화 잠금 사용 안 함 작업

### <a name="i-clicked-the-disable-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>포털에서 "활성화 잠금 사용 안 함" 작업을 클릭했지만 디바이스에서 아무 일도 발생하지 않았습니다.
이는 예상된 결과입니다. 활성화 잠금 사용 안 함 작업이 시작된 후에는 Apple에서 Intune에 업데이트된 코드를 요청합니다. 디바이스가 활성화 잠금 화면에 있는 경우 암호 필드에 코드를 수동으로 입력합니다. 이 코드는 15일 동안만 유효하므로, 작업을 클릭하고 코드를 복사한 후에 초기화를 실행해야 합니다.

### <a name="why-dont-i-see-the-disable-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>iOS 디바이스의 하드웨어 개요 블레이드에서 활성화 잠금 사용 안 함 코드가 표시되지 않는 이유는 무엇인가요?
가장 가능성이 큰 원인은 다음과 같습니다.
- 코드가 만료되어 서비스에서 지워졌습니다.
- 디바이스가 활성화 잠금을 허용하는 디바이스 제한 정책으로 감독되지 않습니다.

다음 쿼리를 사용하여 Graph 탐색기에서 코드를 확인할 수 있습니다.

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-disable-activation-lock-action-greyed-out-for-my-ios-device"></a>iOS 디바이스에 대해 활성화 잠금 사용 안 함 작업이 회색으로 표시되는 이유는 무엇인가요?
가장 가능성이 큰 원인은 다음과 같습니다. 
- 코드가 만료되어 서비스에서 지워졌습니다.
- 디바이스가 활성화 잠금을 허용하는 디바이스 제한 정책으로 감독되지 않습니다.

### <a name="is-the-disable-activation-lock-code-case-sensitive"></a>활성화 잠금 사용 안 함 코드는 대/소문자를 구분하나요?
아니요. 또한 대시를 입력할 필요가 없습니다.

## <a name="remove-devices-action"></a>디바이스 제거 작업

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>사용 중지/초기화를 시작한 사용자를 어떻게 구별하나요?
[Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **테넌트 관리** > **감사 로그**로 이동하여 **초기화 실행자** 열을 확인합니다.
항목이 표시되지 않으면 디바이스 사용자가 작업을 시작했을 가능성이 가장 큽니다. 회사 포털 앱 또는 portal.manage.microsoft.com을 사용했을 수 있습니다.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>사용 중지를 사용한 후에도 애플리케이션이 제거되지 않는 이유는 무엇인가요?
관리형 애플리케이션으로 간주되지 않기 때문입니다. 이 컨텍스트에서 관리형 애플리케이션은 Intune 서비스를 사용하여 설치된 애플리케이션입니다. 여기에는 다음 항목이 포함됩니다.
- 필수로 배포된 앱
- 사용 가능으로 배포된 후 최종 사용자가 회사 포털 앱 내에서 설치된 앱입니다.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Android Enterprise 회사 프로필 디바이스에 대해 초기화가 회색으로 표시되는 이유는 무엇인가요?
이는 예상된 동작입니다. Google은 MDM 공급자에서 회사 프로필 디바이스를 초기화하는 것을 허용하지 않습니다.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>디바이스가 사용 중지된 후 Office 앱에 다시 로그인할 수 있는 이유는 무엇인가요?
디바이스를 사용 중지해도 액세스 토큰이 해지되지 않으므로, 조건부 액세스 정책을 사용하여 이 상태를 완화할 수 있습니다.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>사용 중지/초기화 작업을 실행한 후 모니터링은 어떻게 할 수 있나요?
[Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **테넌트 관리** > **감사 로그**로 이동합니다.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>초기화가 보류 중으로 무기한으로 표시되는 경우가 있는 이유는 무엇인가요?
재설정이 시작되기 전에 디바이스가 Intune 서비스에 상태를 보고하지 않는 경우가 있습니다. 그래서 작업이 보류 중으로 표시됩니다. 작업 성공을 확인했다면 서비스에서 디바이스를 삭제해도 됩니다.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>오프라인 디바이스나 한동안 서비스와 통신하지 않은 디바이스에서 사용 중지/초기화를 시작하면 어떻게 되나요?
MDM 인증서가 만료될 때까지 디바이스는 **사용 중지/초기화 보류 중** 상태로 유지됩니다. MDM 인증서는 등록으로부터 1년 동안 지속되며 매년 자동으로 갱신됩니다. MDM 인증서가 만료되기 전에 디바이스가 체크 인되는 경우 디바이스는 사용 중지/초기화됩니다. MDM 인증서가 만료되기 전에 디바이스가 체크 인되지 않는 경우 디바이스는 서비스를 체크 인할 수 없습니다. MDM 인증서가 만료된 지 180일 후에 디바이스는 자동으로 Azure Portal에서 제거됩니다.


## <a name="reset-passcode-action"></a>암호 재설정 작업

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Android 디바이스 관리자 등록 디바이스에서 암호 재설정 작업이 회색으로 표시되는 이유는 무엇인가요?
랜섬웨어를 해결하기 위해 Google은 디바이스 관리 API(Android 버전 7.0 이상 디바이스에 적용)에서 암호 재설정 기능을 제거했습니다.

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Android 8.0 이상의 회사 프로필 등록 디바이스에서 암호 재설정을 실행할 때 "지원되지 않음" 메시지가 표시되는 이유는 무엇인가요?
재설정 토큰이 디바이스에서 활성화되지 않았기 때문입니다. 재설정 토큰을 활성화하려면 다음을 따릅니다.
1. 구성 정책에서 회사 프로필 암호를 요구해야 합니다.
2. 최종 사용자는 적절한 회사 프로필 암호를 설정해야 합니다.
3. 최종 사용자는 보조 프롬프트를 수락하여 암호 재설정을 허용해야 합니다.
이러한 단계를 완료한 후에는 더 이상 이 응답을 받지 않게 됩니다.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>iOS 디바이스에서 암호 제거 작업을 실행할 때 새 암호를 설정하라는 메시지가 표시되는 이유는 무엇인가요?
규정 준수 정책 중 하나에 암호가 필요하기 때문입니다.

## <a name="next-steps"></a>다음 단계

[Microsoft의 지원 도움말](../fundamentals/get-support.md)을 받거나 [커뮤니티 포럼](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)을 이용하세요.
