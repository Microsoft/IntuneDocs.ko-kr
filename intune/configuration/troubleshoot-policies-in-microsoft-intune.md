---
title: Microsoft Intune에서 정책 문제 해결 - Azure | Microsoft Docs
description: 기본 제공 문제 해결 기능을 사용하는 방법과 Microsoft Intune에서 규정 준수 정책 및 구성 프로필을 사용하는 경우 발생하는 일반적인 문제나 해결 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8768022872d32116add0ed4ea4caf1f8fcb800f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059282"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>Intune의 문제 해결 정책 및 프로필

Microsoft Intune에는 몇 가지 기본 제공 문제 해결 기능이 포함됩니다. 이 기능을 사용하면 사용자의 환경에서 준수 정책과 구성 프로필 문제를 해결하는 데 도움이 됩니다.

이 문서에는 몇 가지 일반적인 문제 해결 기술이 나열되고 발생할 수 있는 몇 가지 문제가 설명되어 있습니다.

## <a name="check-tenant-status"></a>테 넌 트 상태 확인

[테 넌 트 상태](../fundamentals/tenant-status.md) 를 확인 하 고 구독이 활성 상태 인지 확인 합니다. 정책 또는 프로필 배포에 영향을 줄 수 있는 활성 인시던트 및 권고에 대 한 세부 정보를 볼 수도 있습니다.

## <a name="use-built-in-troubleshooting"></a>기본 제공 문제 해결 기능 사용

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **문제 해결 + 지원**을 선택 합니다.

    ![Intune에서 도움말 및 지원으로 이동하여 문제 해결을 선택합니다.](./media/troubleshoot-policies-in-microsoft-intune/help-and-support-troubleshoot.png)

2. **사용자 선택**을 선택하고 문제가 있는 사용자를 선택한 다음, **선택**을 클릭합니다.
3. **Intune 라이선스**와 **계정 상태** 모두에 녹색 확인 표시가 있는지 확인합니다.

    ![Intune에서 사용자를 선택하고 계정 상태와 Intune 라이선스의 상태에 녹색 확인 표시가 있는지 확인합니다.](./media/troubleshoot-policies-in-microsoft-intune/account-status-intune-license-show-green.png)

    **유용한 링크**:

    - [사용자가 디바이스를 등록하도록 라이선스 할당](../fundamentals/licenses-assign.md)
    - [Intune에 사용자 추가](../fundamentals/users-add.md)

4. **디바이스**에서 문제가 있는 디바이스를 찾습니다. 다른 열을 검토합니다.

    - **관리**: 디바이스가 규정 준수 정책이나 구성 정책을 수신하려면 이 속성에 **MDM** 또는 **EAS/MDM**이 표시되어야 합니다.

        - **관리됨**이 **MDM**이나 **EAS/MDM**으로 설정되어 있지 않으면 디바이스가 등록되지 않은 것입니다. 등록될 때까지 준수 정책이나 구성 정책을 수신하지 못합니다.

        - 앱 보호 정책(모바일 애플리케이션 관리)은 디바이스를 등록할 필요가 없습니다. 자세한 내용은 [앱 보호 정책 만들기 및 할당](../apps/app-protection-policies.md)을 참조하세요.

    - **Azure AD 조인 유형**: **작업 공간** 또는 **AzureAD**로 설정되어야 합니다.
 
        - 열이 **등록 안 됨**이면, 등록에 문제가 있는 것입니다. 일반적으로 디바이스 등록을 취소했다가 다시 등록하면 이 문제가 해결됩니다.

    - **Intune 준수**: **예**여야 합니다. **아니오**가 표시되면 준수 정책에 문제가 있거나, 디바이스가 Intune 서비스에 연결되지 않은 것입니다. 예를 들어 디바이스가 꺼져 있거나 네트워크에 연결되어 있지 않을 수 있습니다. 그러면, 30일 후에 디바이스가 비준수 상태가 됩니다.

        자세한 내용은 [디바이스 준수 정책 시작](../protect/device-compliance-get-started.md)을 참조하세요.

    - **Azure AD 준수**: **예**여야 합니다. **아니오**가 표시되면 준수 정책에 문제가 있거나, 디바이스가 Intune 서비스에 연결되지 않은 것입니다. 예를 들어 디바이스가 꺼져 있거나 네트워크에 연결되어 있지 않을 수 있습니다. 그러면, 30일 후에 디바이스가 비준수 상태가 됩니다.

        자세한 내용은 [디바이스 준수 정책 시작](../protect/device-compliance-get-started.md)을 참조하세요.

    - **마지막 체크 인**: 최근 시간 및 날짜여야 합니다. 기본적으로 Intune 디바이스는 8시간마다 확인합니다.

        - **마지막 체크 인**이 24시간을 초과하면 디바이스에 문제가 있을 수 있습니다. 체크 인할 수 없는 디바이스는 Intune에서 정책을 받을 수 없습니다.

        - 체크 인을 강제로 수행하려면:
            - Android 디바이스를 열고 회사 포털 앱 > **디바이스**를 열고 목록에서 디바이스를 선택한 다음, **디바이스 설정 확인**을 선택합니다.
            - iOS 디바이스를 열고 회사 포털 앱 > **디바이스**를 열고 목록에서 디바이스를 선택한 다음, **설정 확인**을 선택합니다.

        - Windows 디바이스에서 **설정** > **계정** > **회사 또는 학교 액세스**를 열어서 계정이나 MDM 등록을 선택하고 **정보** > **동기화**를 선택합니다.

    - 정책별 정보를 보려면 디바이스를 선택합니다.

        **디바이스 준수**는 디바이스에 할당된 준수 정책의 상태를 보여줍니다.

        **디바이스 구성**은 디바이스에 할당된 구성 정책의 상태를 보여줍니다.

        원하는 정책이 **디바이스 준수**나 **디바이스 구성**에 표시되지 않으면 정책이 올바르게 지정되지 않은 것입니다. 정책을 열고 사용자 또는 디바이스에 정책을 할당하십시오.

        **정책 상태**:

        - **적용되지 않음**: 이 정책은 이 플랫폼에서 지원되지 않습니다. 예를 들어, iOS 정책은 Android에서 작동하지 않습니다. Samsung KNOX 정책은 Windows 디바이스에서 작동하지 않습니다.
        - **충돌**: 디바이스에 Intune이 재정의할 수 없는 기존 설정이 있습니다. 아니면, 다른 값을 사용하여 동일한 설정으로 두 개의 정책을 배포했습니다.
        - **보류 중**: 디바이스가 Intune에 체크 인되지 않아서 정책을 수신하지 못했습니다. 아니면, 디바이스가 정책을 수신했지만 Intune에 상태가 보고되지 않았습니다.
        - **오류**: 오류 및 가능한 해결 방법은 [회사 리소스 액세스 문제 해결](../fundamentals/troubleshoot-company-resource-access-problems.md)에서 찾아보세요.

        **유용한 링크**: 

        - [디바이스 준수 정책을 배포하는 방법](../protect/device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
        - [디바이스 준수 정책 모니터링](../protect/compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>프로필이 제대로 적용되었는지 확실하지 않은 경우

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **모든 디바이스**를 선택하고 디바이스를 선택한 다음, **디바이스 구성**을 선택합니다. 

    모든 디바이스는 해당 프로필이 나열됩니다. 모든 프로필에는 **상태**가 있습니다. 상태는 하드웨어 및 OS 제한 사항과 요구 사항을 비롯한 할당된 모든 프로필이 함께 고려되어 적용됩니다. 가능한 상태는 다음과 같습니다.

    - **준수**: 디바이스가 프로필을 수신하고 Intune에 설정을 준수한다고 보고합니다.

    - **적용할 수 없음**: 프로필 설정을 적용할 수 없습니다. 예를 들어 iOS 디바이스의 이메일 설정은 Android 디바이스에 적용되지 않습니다.

    - **보류 중**: 프로필이 디바이스에 전송되었지만, Intune에 상태를 보고하지 않았습니다. 예를 들어 Android에서의 암호화의 경우, 사용자가 암호화를 사용하도록 설정해야 하고 보류 중으로 표시될 수 있습니다.

**유용한 링크**: [구성 디바이스 프로필 모니터링](../configuration/device-profile-monitor.md)

> [!NOTE]
> 제한 수준이 다른 두 정책을 같은 디바이스나 사용자에 적용하면 보다 제한적인 정책이 적용됩니다.

## <a name="policy-troubleshooting-resources"></a>정책 문제 해결 리소스

- [장치에 적용 되지 않는 iOS 또는 Android 정책 문제 해결](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-tip-Troubleshooting-iOS-or-Android-policies-not-applying/ba-p/280154) (다른 Microsoft 사이트 열기)
- [Windows 10 Intune 정책 오류 문제 해결](https://blogs.technet.microsoft.com/configmgrdogs/2018/08/09/troubleshooting-windows-10-intune-policy-failures/) (블로그 열기)
- [Windows 10에 대 한 CSP 사용자 지정 설정 문제 해결](https://support.microsoft.com/en-us/help/4055338/troubleshoot-csp-setting-windows-10-computer-intune) (다른 Microsoft 사이트 열기)
- [Windows 10 그룹 정책 Vs INTUNE MDM 정책](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/) (다른 Microsoft 사이트 열기)

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>경고: Exchange에 액세스 규칙 저장 실패

**문제**: 관리 콘솔에에 **Exchange에 액세스 규칙 저장 실패**  라는 경고가 표시됩니다.

Exchange 온-프레미스 정책 작업 영역(관리 콘솔)에서 정책을 만들었지만, Office 365를 사용하고 있는 경우, 구성된 정책 설정이 Intune에 의해 적용되지 않습니다. 경고에서 정책 소스를 확인하십시오. Exchange 온-프레미스 정책 작업 영역에서 레거시 규칙을 삭제합니다. 레거시 규칙은 Intune 내에서 온-프레미스 Exchange의 글로벌 Exchange 규칙이며 Office 365와는 관계가 없습니다. 그런 다음, Office 365에 대한 새 정책을 만듭니다.

[Intune 온-프레미스 Exchange Connector 문제 해결](../protect/troubleshoot-exchange-connector.md)이 유용한 리소스가 될 수 있습니다.

## <a name="cant-change-security-policies-for-enrolled-devices"></a>등록된 디바이스에 대한 보안 정책을 변경할 수 없는 경우

Windows Phone 디바이스는 MDM 또는 EAS를 사용하여 보안 정책을 설정하면 이 정책의 보안이 저하되는 것을 허용하지 않습니다. 예를 들어 **암호의 최소 문자 수**를 8로 설정한 다음, 4로 줄이려고 하면, 더 제한적인 정책이 디바이스에 적용됩니다.

정책 할당을 취소 하면 Windows 10 장치에서 보안 정책을 제거할 수 없습니다 (배포 중지). 정책을 할당 된 상태로 두고 보안 설정을 다시 기본값으로 변경 해야 할 수 있습니다.

디바이스 플랫폼에 따라서, 보안 수준이 낮은 값으로 정책을 변경하려면 보안 정책을 다시 설정해야 할 수 있습니다.

예를 들어, 데스크톰의 Windows 8.1에서 오른쪽으로 살짝 밀어 **참 메뉴** 모음을 엽니다. **설정** > **제어판** > **U사용자 계정**을 선택합니다. 왼쪽에서 **보안 정책 재설정** 링크를 선택하고 **정책 재설정**을 선택합니다.

Android, iOS, Windows Phone 8.1과 같은 기타 플랫폼의 경우, 덜 엄격한 정책을 적용하려면 사용을 중지하고 다시 등록해야 해야 합니다.

[디바이스 등록 문제 해결](../enrollment/troubleshoot-device-enrollment-in-intune.md)이 유용한 리소스가 될 수 있습니다.

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>Intune 소프트웨어 클라이언트를 사용하는 PC - 클래식 포털

> [!NOTE]
> 이 섹션은 클래식 포털에 적용됩니다. 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>policyplatform.log의 Microsoft Intune 정책 관련 오류

Intune 소프트웨어 클라이언트로 관리되는 Windows PC의 경우 `policyplatform.log` 파일의 정책 오류는 디바이스의 Windows UAC(사용자 계정 컨트롤)에서 기본값이 아닌 설정을 사용한 결과일 수 있습니다. 기본값이 아닌 일부 UAC 설정은 Microsoft Intune 클라이언트 설치와 정책 실행에 영향을 줄 수 있습니다.

#### <a name="resolve-uac-issues"></a>UAC 문제 해결

1. 컴퓨터를 사용 중지합니다. [디바이스 제거](../remote-actions/devices-wipe.md)를 참조하세요.

2. 클라이언트 소프트웨어가 제거될 때까지 20분 정도 기다립니다.

    > [!NOTE]
    > 프로그램 및 기능에서 클라이언트를 제거하지 마세요.

3. 시작 메뉴에서 **UAC**를 입력하여 사용자 계정 컨트롤 설정을 엽니다.

4. 알림 슬라이더를 기본 설정으로 이동합니다.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>오류: 0x80041013 컴퓨터에서 값을 가져올 수 없습니다.

로컬 시스템의 시간이 5분 이상 동기화되지 않는 경우에 발생할 수 있습니다. 로컬 컴퓨터의 시간이 동기화되어 있지 않으면 타임스탬프가 유효하지 않으므로 보안 트랜잭션이 실패합니다.

이 문제를 해결하려면 로컬 시스템 시간을 인터넷 시간에 최대한 가깝게 설정합니다. 아니면, 네트워크의 도메인 컨트롤러 시간으로 설정합니다.

## <a name="next-steps"></a>다음 단계

[메일 프로필 관련 일반적인 문제와 해결 방법](../configuration/troubleshoot-email-profiles-in-microsoft-intune.md)

[Microsoft의 지원 도움말](../fundamentals/get-support.md)을 받거나 [커뮤니티 포럼](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)을 이용하세요.
