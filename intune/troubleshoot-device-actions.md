---
title: Microsoft Intune - Azure에서 디바이스 작동 문제 해결 | Microsoft Docs
description: 장치 작업 문제 해결에 대 한 도움을 받으세요.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8324f53d787bd307ac3befd0ccee52cb8153b611
ms.sourcegitcommit: d2989b9992d10d133573d9bc31479659fb7e242c
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71080024"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Intune에서 장치 작업 문제 해결

Microsoft Intune에는 관리 장치에 도움이 되는 많은 작업이 있습니다. 이 문서에서는 장치 작업 문제 해결에 도움이 되는 몇 가지 일반적인 질문에 대 한 답변을 제공 합니다.

## <a name="bypass-activation-lock-action"></a>활성화 잠금 무시 동작

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>포털에서 "바이패스 활성화 잠금" 작업을 클릭 했지만 장치에서 아무 일도 발생 하지 않았습니다.
이는 예상 된 것입니다. 바이패스 활성화 잠금 작업을 시작한 후에는 Intune에서 Apple의 업데이트 된 코드를 요청 합니다. 장치가 활성화 잠금 화면에 있는 경우 암호 필드에 코드를 수동으로 입력 합니다. 이 코드는 15 일 동안만 유효 하므로 초기화를 실행 하기 전에 동작을 클릭 하 고 코드를 복사 해야 합니다.

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>IOS 장치의 하드웨어 개요 블레이드에서 바이패스 활성화 잠금 코드가 표시 되지 않는 이유는 무엇 인가요?
가장 가능성이 높은 원인은 다음과 같습니다.
- 코드가 만료 되어 서비스에서 제거 되었습니다.
- 장치는 활성화 잠금을 허용 하는 장치 제한 정책으로 감독 되지 않습니다.

다음 쿼리를 사용 하 여 그래프 탐색기에서 코드를 확인할 수 있습니다.

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>내 iOS 장치에서 바이패스 활성화 잠금 작업이 회색으로 표시 되는 이유는 무엇 인가요?
가장 가능성이 높은 원인은 다음과 같습니다. 
- 코드가 만료 되어 서비스에서 제거 되었습니다.
- 장치는 활성화 잠금을 허용 하는 장치 제한 정책으로 감독 되지 않습니다.

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>바이패스 활성화 잠금 코드 대/소문자 구분 여부
아니요. 대시를 입력할 필요가 없습니다.

## <a name="remove-devices-action"></a>장치 제거 작업

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>사용 중지/초기화를 시작한 사용자를 알려 어떻게 할까요??
**Intune** > **장치** **** **** 장치 작업으로 이동 하 > 시작 열을 선택 합니다. > 
항목이 표시 되지 않으면 장치 사용자가 작업을 시작할 가능성이 가장 큽니다. 회사 포털 앱 또는 portal.manage.microsoft.com를 사용 했을 수 있습니다.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>사용 중지를 사용한 후에도 응용 프로그램이 제거 되지 않는 이유는 무엇 인가요?
관리 되는 응용 프로그램으로 간주 되지 않기 때문입니다. 이 컨텍스트에서 관리 되는 응용 프로그램은 Intune 서비스를 사용 하 여 설치 된 응용 프로그램입니다. 여기에는 다음 항목이 포함됩니다.
- 앱이 필수로 배포 되었습니다.
- 앱이 사용 가능으로 배포 된 다음 최종 사용자가 회사 포털 앱 내에서 설치 되었습니다.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Android Enterprise Work Profile 장치에 대해 초기화가 회색으로 표시 되는 이유는 무엇 인가요?
이는 예상된 동작입니다. Google은 MDM 공급자에서 회사 프로필 장치를 공장 재설정 하는 것을 허용 하지 않습니다.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>장치가 사용 중지 된 후 Office 앱에 다시 로그인 할 수 있는 이유는 무엇 인가요?
장치를 사용 중지 하면 액세스 토큰이 해지 되지 않으므로 조건부 액세스 정책을 사용 하 여이 문제를 완화할 수 있습니다.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>사용 중지/초기화 작업을 실행 한 후 모니터링 하려면 어떻게 해야 하나요?
**Intune** >  **** 장치장치 > **작업**으로 이동 합니다.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>때로는가 무기한 보류 중인 것으로 표시 되는 이유는 무엇 인가요?
다시 설정이 시작 되기 전에 장치는 항상 Intune 서비스에 상태를 보고 하지 않습니다. 따라서 작업은 보류 중으로 표시 됩니다. 작업이 성공 했음을 확인 한 경우 서비스에서 장치를 삭제 합니다.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>잠시 동안 서비스와 통신 하지 않은 오프 라인 장치 또는 장치에서 사용 중지/초기화를 시작 하면 어떻게 되나요?
MDM 인증서가 만료 될 때까지 장치는 사용 **중지/초기화 보류 중** 상태로 유지 됩니다. MDM 인증서는 등록에서 1 년 동안 지속 되며 매년 자동으로 갱신 됩니다. MDM 인증서가 만료 되기 전에 장치가 체크 인 되 면 사용 중지/초기화 됩니다. MDM 인증서가 만료 되기 전에 장치가 체크 인 되지 않으면 서비스를 체크 인할 수 없습니다. 180 일 후 MDM 인증서가 만료 되 면 장치가 Azure Portal에서 자동으로 제거 됩니다.


## <a name="reset-passcode-action"></a>암호 다시 설정 작업

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Android 장치 관리자가 등록 한 장치에서 암호 재설정 작업을 회색으로 표시 하는 이유는 무엇 인가요?
Ransom 웨어를 공격 하기 위해 Google은 장치 관리 API (Android 버전 7.0 이상 장치에 적용)에서 암호 재설정 기능을 제거 했습니다.

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Android 8.0 이상 작업 프로필에 등록 된 장치에 암호 재설정을 실행 하는 경우 "지원 되지 않음" 메시지가 표시 되는 이유는 무엇 인가요?
다시 설정 토큰이 장치에서 활성화 되지 않았기 때문입니다. 다시 설정 토큰을 활성화 하려면:
1. 구성 정책에서 회사 프로필 암호를 요구 해야 합니다.
2. 최종 사용자는 적절 한 작업 프로필 암호를 설정 해야 합니다.
3. 최종 사용자는 암호 재설정을 허용 하기 위해 보조 프롬프트를 수락 해야 합니다.
이러한 단계를 완료 한 후에는 더 이상이 응답을 받을 수 없습니다.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>암호 제거 작업을 실행할 때 iOS 장치에 새 암호를 설정 하 라는 메시지가 표시 되는 이유는 무엇 인가요?
준수 정책 중 하나에 암호가 필요 하기 때문입니다.

## <a name="next-steps"></a>다음 단계

[Microsoft의 지원 도움말](get-support.md)을 받거나 [커뮤니티 포럼](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)을 이용하세요.
