---
title: 디바이스 등록 문제 해결
titleSuffix: Microsoft Intune
description: Microsoft Intune에서 디바이스 등록 문제 해결을 위한 제안 사항.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/09/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cb323dc6f8110d77343fb11c9e0a1c40f9e3cd8
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415273"
---
# <a name="troubleshoot-device-enrollment-in-microsoft-intune"></a>Microsoft Intune에서 디바이스 등록 문제 해결

이 문서에서는 [디바이스 등록](device-enrollment.md) 문제 해결을 위한 제안 사항을 제공합니다. 이 정보로 문제가 해결되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](../fundamentals/get-support.md)을 참조하여 도움을 얻을 수 있는 다른 방법을 찾아보세요.


## <a name="initial-troubleshooting-steps"></a>초기 문제 해결 단계

문제 해결을 시작하기 전에 등록이 설정되도록 Intune을 올바르게 구성했는지 확인하세요. 다음에서 이러한 구성 요구 사항에 대해 자세히 읽어볼 수 있습니다.

- [Microsoft Intune에 디바이스를 등록하도록 준비](../fundamentals/setup-steps.md)
- [iOS/iPadOS 및 Mac 디바이스 관리 설정](../ios-enroll.md)
- [Windows 디바이스 관리 설정](windows-enroll.md)
- [Android 디바이스 관리 설정](android-enroll.md) - 추가 단계 불필요

사용자 디바이스의 시간과 날짜가 올바르게 설정되었는지 확인할 수도 있습니다.

1. 디바이스를 다시 시작합니다.
2. 시간과 날짜가 최종 사용자의 표준 시간대에 대해 GMT 표준(+ 또는 - 12시간)에 가깝게 설정되었는지 확인합니다.
3. Intune 회사 포털을 제거하고 다시 설치합니다(해당하는 경우).

관리되는 디바이스 사용자는 여러분이 검토할 등록 및 진단 로그를 수집할 수 있습니다. 로그 수집에 대한 지침은 다음과 같이 제공됩니다.

- [IT 관리자에게 Android 등록 오류 보내기](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [IT 관리자에게 iOS/iPadOS 오류 보내기](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>일반적인 등록 문제
이러한 문제는 모든 디바이스 플랫폼에서 발생할 수 있습니다.

### <a name="device-cap-reached"></a>디바이스 최대값 도달
**문제:** 등록 중에 사용자에게 오류가 표시됩니다(예: **회사 포털을 일시적으로 사용할 수 없음**).

**해결 방법:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>등록된 디바이스 수와 및 허용된 디바이스 수 확인

다음 단계에 따라 사용자가 최대 디바이스 수를 초과하여 할당받지 않았는지 확인합니다.

1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **등록 제한** > **디바이스 개수 제한**을 차례로 선택합니다. **디바이스 제한** 열의 값을 확인합니다.

2. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **사용자** > **모든 사용자**를 차례로 선택하고 **디바이스**를 선택합니다. 디바이스 수를 확인합니다.

3. 사용자의 등록된 디바이스 수가 이미 해당 디바이스 개수 제한과 동일한 경우 다음이 될 때까지 더 이상 등록할 수 없습니다.
    - [기존 디바이스가 제거됨](../remote-actions/devices-wipe.md) 또는
    - [디바이스 제한을 설정](enrollment-restrictions-set.md)하여 디바이스 제한을 늘립니다.

디바이스 캡에 도달을 방지하려면 부실 디바이스 레코드를 제거해야 합니다.

> [!NOTE]
> 
> [Microsoft Intune에서 디바이스 등록 관리자 계정을 사용하여 회사 소유 디바이스 등록](device-enrollment-manager-enroll.md)에 설명된 대로 디바이스 등록 관리자를 사용하여 디바이스 등록 최대값에 도달하는 것을 방지할 수 있습니다.
> 
> 디바이스 등록 관리자 계정에 추가된 사용자 계정은 해당 특정 사용자 로그인에 대해 조건부 액세스 정책이 적용되는 경우 등록을 완료할 수 없습니다.

### <a name="company-portal-temporarily-unavailable"></a>회사 포털을 일시적으로 사용할 수 없음
**문제:** 디바이스에서 **회사 포털을 일시적으로 사용할 수 없음** 오류가 사용자에게 표시됩니다.

**해결 방법:**

1. 디바이스에서 Intune 회사 포털 앱을 제거합니다.

2. 디바이스에서 브라우저를 열고, [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)으로 이동하고, 사용자 로그인을 시도합니다.

3. 사용자가 로그인하지 못하면 다른 네트워크를 시도해야 합니다.

4. 이것이 하면 사용자의 자격 증명이 Azure Active Directory와 올바로 동기화했는지 확인합니다.

5. 사용자가 성공적으로 로그인하면 iOS/iPadOS 디바이스에 Intune 회사 포털 앱을 설치하고 등록하라는 메시지가 나타납니다. Android 디바이스에서는 Intune 회사 포털 앱을 수동으로 설치해야 합니다. 그런 후에 다시 등록할 수 있습니다.

### <a name="mdm-authority-not-defined"></a>MDM 기관이 정의되지 않았습니다
**문제:** 사용자에게 **MDM 기관이 정의되지 않았습니다.** 오류가 표시됩니다.

**해결 방법:**

1. MDM 기관이 [적절하게 설정](../fundamentals/mdm-authority-set.md)되었는지 확인합니다.
    
2. 사용자의 자격 증명이 Azure Active Directory와 올바로 동기화되었는지 확인합니다. 사용자의 UPN이 Microsoft 365 관리 센터에서 Active Directory 정보와 일치하는지 확인할 수 있습니다.
    UPN이 Active Directory 정보와 일치하지 않으면 다음을 수행합니다.

    1. 로컬 서버에서 DirSync를 해제합니다.

    2. 일치하지 않는 사용자를 **Intune 계정 포털** 사용자 목록에서 삭제합니다.

    3. Azure 서비스에서 잘못된 데이터를 제거할 수 있도록 1시간 가량 기다립니다.

    4. DirSync를 다시 설정하고 이제 사용자가 제대로 동기화되었는지 확인합니다.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>회사 이름에 특수 문자가 포함되어 있으면 정책을 만들거나 디바이스를 등록할 수 없습니다.
**문제:** 정책을 만들거나 디바이스를 등록할 수 없습니다.

**해결 방법:** [Microsoft 365 관리 센터](https://admin.microsoft.com/)에서 회사 이름의 특수 문자를 제거하고 회사 정보를 저장합니다.

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>확인된 도메인이 여럿이면 로그인하거나 디바이스를 등록할 수 없습니다.
**문제:** ADFS에 두 번째 확인된 도메인을 추가하면 이 문제가 발생할 수 있습니다. 두 번째 도메인을 UPN(사용자 계정 이름) 접미사로 사용하는 사용자는 포털에 로그인하거나 디바이스를 등록할 수 없습니다.


<strong>해결 방법:</strong> Microsoft Office 365 고객은 다음과 같은 경우 각 접미사에 대해 AD FS 2.0 페더레이션 서비스의 별도 인스턴스를 배포해야 합니다.
- AD FS 2.0을 통해 SSO(Single Sign-On) 사용 및
- 조직 내 사용자의 UPN 접미사에 대해 여러 최상위 도메인 보유(예: @contoso.com 또는 @fabrikam.com)


[AD FS 2.0 롤업](https://support.microsoft.com/kb/2607496)은 <strong>SupportMultipleDomain</strong> 스위치와 함께 작동하여 AD FS 서버가 추가적인 AD FS 2.0 서버를 필요로 하지 않고 이 시나리오를 지원할 수 있도록 합니다. 자세한 내용은 [이 블로그](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/)를 참조하세요.


## <a name="android-issues"></a>Android 문제

### <a name="android-enrollment-errors"></a>Android 등록 오류

다음 표에서는 Intune에 Android 디바이스를 등록하는 동안 최종 사용자에게 표시될 수 있는 오류를 보여 줍니다.

|오류 메시지|문제|해결 방법|
|---|---|---|
|**IT 관리자가 액세스에 대한 라이선스를 할당해야 함**<br>IT 관리자는 사용자에게 이 앱을 사용할 수 있는 액세스 권한을 할당하지 않았습니다. IT 관리자에게 도움을 받거나 나중에 다시 시도하세요.|사용자 계정에 필요한 라이선스가 없으므로 디바이스를 등록할 수 없습니다.|사용자가 디바이스를 등록하려면 먼저 필요한 라이선스를 할당받아야 합니다. 이 메시지는 모바일 디바이스 관리 기관에 맞지 않는 라이선스 형식이 있음을 의미합니다. 예를 들어 다음 두 가지가 모두 true인 경우 이 오류가 표시됩니다.<ol><li>Intune이 모바일 디바이스 관리 기관으로 설정되었습니다.</li><li>System Center 2012 R2 Configuration Manager를 사용하고 있습니다.</li></ol>자세한 내용은 [사용자 계정에 Intune 라이선스 할당](/intune/licenses-assign)을 참조하세요.|
|**IT 관리자가 MDM 기관을 설정해야 함**<br>IT 관리자가 MDM 기관을 설정하지 않은 것 같습니다. IT 관리자에게 도움을 받거나 나중에 다시 시도하세요.|모바일 디바이스 관리 기관이 정의되지 않았습니다.|모바일 디바이스 관리 기관이 Intune에서 설정되지 않았습니다. [모바일 디바이스 관리 기관을 설정](/intune/mdm-authority-set)하는 방법을 참조하세요.|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>디바이스가 Intune 서비스에 체크 인되지 않고 Intune 관리 콘솔에서 "비정상"으로 표시됨
**문제:** Android 버전 4.4.x 및 5.x를 실행하는 일부 삼성 디바이스에서 Intune 서비스에 체크 인이 중지될 수 있습니다. 디바이스가 체크 인되지 않으면 다음과 같이 됩니다.

- 장치가 Intune 서비스에서 정책, 앱 및 원격 명령을 받을 수 없습니다.
- 관리자 콘솔에서 관리 상태가 **비정상**으로 표시됩니다.
- 조건부 액세스 정책으로 보호되는 사용자가 회사 리소스에 액세스할 수 없게 될 수 있습니다.

특정 Samsung 디바이스에 탑재되는 Samsung Smart Manager 소프트웨어는 Intune 회사 포털 및 해당 구성 요소를 비활성화할 수 있습니다. 회사 포털이 비활성화된 상태이면 백그라운드에서 실행될 수 없으므로 Intune 서비스에 연결할 수 없습니다.

**해결 방법 1:**

사용자에게 회사 포털 앱을 수동으로 시작하도록 요청합니다. 앱이 다시 시작되면 디바이스가 Intune 서비스에 체크 인됩니다.

> [!IMPORTANT]
> Samsung Smart Manager가 회사 포털 앱을 다시 비활성화할 수 있으므로 회사 포털 앱을 수동으로 여는 방법은 일시적인 해결 방법입니다.

**해결 방법 2:**

사용자에게 Android 6.0으로 업그레이드해 보도록 요청합니다. Android 6.0 디바이스에서는 비활성화 문제가 발생하지 않습니다. 업데이트를 사용할 수 있는지 확인하려면 **설정** > **디바이스 정보** > **수동으로 업데이트 다운로드**로 이동하고 프롬프트를 따릅니다.

**3:**

해결 방법 2로 해결되지 않으면 사용자에게 다음 단계에 따라 Smart Manager에서 회사 포털 앱을 제외하도록 설정하라고 요청합니다.

1. 디바이스에서 Smart Manager 앱을 시작합니다.

   ![디바이스에서 Smart Manager 아이콘 선택](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. **배터리** 타일을 선택합니다.

   ![배터리 타일 선택](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. **앱 절전** 또는 **앱 최적화** 아래에서 **세부 정보**를 선택합니다.

   ![앱 절전 또는 앱 최적화 아래에서 세부 정보 선택](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. 앱 목록에서 **회사 포털**을 선택합니다.

   ![앱 목록에서 회사 포털 선택](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. **꺼짐**을 선택합니다.

   ![앱 최적화 대화 상자에서 꺼짐 선택](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. **앱 절전** 또는 **앱 최적화** 아래에서 회사 포털이 꺼져 있는지 확인합니다.

   ![회사 포털이 꺼져 있는지 확인](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>프로필 설치 실패
**문제:** Android 디바이스에서 **프로필 설치 실패** 오류가 사용자에게 표시됩니다.

**해결 방법:**

1. 사용자가 사용 중인 Intune 서비스 버전에 적절한 라이선스를 할당받았는지 확인합니다.

2. 디바이스가 다른 MDM 공급자에 등록되지 않았는지 확인합니다.

3. 디바이스에 관리 프로필이 설치되지 않았는지 확인합니다.

4. Android용 Chrome이 기본 브라우저이고 쿠키가 사용할 수 있도록 설정되어 있는지 확인합니다.

### <a name="android-certificate-issues"></a>Android 인증서 문제

**문제**: 사용자가 디바이스에서 다음 메시지를 받습니다. *필요한 인증서가 디바이스에 없으므로 로그인할 수 없습니다.*

**해결 방법 1**:

사용자가 [디바이스에 필수 인증서가 없음](/intune-user-help/your-device-is-missing-a-required-certificate-android)의 지침에 따라 누락된 인증서를 검색할 수 있습니다. 오류가 지속되면 해결 방법 2를 시도하세요.

**해결 방법 2**:

회사 자격 증명을 입력하고 페더레이션된 로그인에 대해 리디렉션된 후에 사용자에게는 누락된 인증서 오류가 계속 표시될 수 있습니다. 이 경우에 오류는 중간 인증서가 AD FS(Active Directory Federation Services) 서버에서 누락되었음을 의미할 수 있습니다.

Android 디바이스의 경우 중간 인증서가 [SSL 서버 hello](https://technet.microsoft.com/library/cc783349.aspx)에 포함되어야 하므로 인증서 오류가 발생합니다. 현재, 기본 AD FS 서버 또는 WAP - AD FS 프록시 서버 설치에서는 SSL 클라이언트 hello에 대한 SSL 서버 hello 응답에 AD FS 서비스 SSL 인증서만 전송합니다.

이 문제를 해결하려면 다음과 같이 인증서를 AD FS 서버 또는 프록시의 컴퓨터 개인 인증서로 가져옵니다.

1. ADFS 및 프록시 서버에서 **시작** > **실행** > **certlm.msc**를 마우스 오른쪽 단추로 클릭하여 로컬 머신 인증서 관리 콘솔을 시작합니다.
2. **개인**을 확장하고 **인증서**를 선택합니다.
3. AD FS 서비스 통신용 인증서(공개 서명된 인증서)를 찾은 다음 두 번 클릭하여 해당 속성을 확인합니다.
4. **인증 경로** 탭을 선택하여 해당 인증서의 상위 인증서를 확인합니다.
5. 각 상위 인증서에서 **인증서 보기**를 선택합니다.
6. **세부 정보** > **파일에 복사...** 를 선택합니다.
7. 마법사의 프롬프트에 따라 부모 인증서의 공개 키를 선택한 파일 위치에 내보내거나 저장합니다.
8. **인증서** > **모든 작업** > **가져오기**를 마우스 오른쪽 단추로 클릭합니다.
9. 마법사의 메시지에 따라 상위 인증서를 **LocalComputer\Personal\Certificates**로 가져옵니다.
10. AD FS 서버를 다시 시작합니다.
11. 모든 AD FS 및 프록시 서버에서 위의 단계를 반복합니다.

적절한 인증서 설치를 확인하기 위해 [https://www.digicert.com/help/](https://www.digicert.com/help/)에서 사용 가능한 진단 도구를 사용할 수 있습니다. **서버 주소** 상자에 ADFS 서버의 FQDN(IE: sts.contso.com)을 입력하고 **서버 확인**을 클릭합니다.

**인증서가 제대로 설치되었는지 유효성을 검사하려면**:

아래 단계에서는 인증서가 올바르게 설치되었는지 유효성을 검사하는 데 사용할 수 있는 여러 방법과 도구 중 하나를 설명합니다.

1. [무료 Digicert 도구](ttps://www.digicert.com/help/)로 이동합니다.
2. AD FS 서버의 정규화된 도메인 이름(예: sts.contoso.com)을 입력하고 **CHECK SERVER**(서버 확인)를 선택합니다.

서버 인증서가 올바르게 설치되어 있으면 결과의 모든 항목에 확인 표시가 나타납니다. 위에서 설명한 문제가 있는 경우에는 보고서의 "Certificate Name Matches"(인증서 이름 일치) 및 "SSL Certificate is correctly Installed"(SSL 인증서가 올바르게 설치됨) 섹션에 빨간색 X가 표시됩니다.


## <a name="iosipados-issues"></a>iOS/iPadOS 문제

### <a name="iosipados-enrollment-errors"></a>iOS/iPadOS 등록 오류
다음 표에서는 Intune에 iOS/iPadOS 디바이스를 등록하는 동안 최종 사용자에게 표시될 수 있는 오류를 보여 줍니다.

|오류 메시지|문제|해결 방법|
|-------------|-----|----------|
|NoEnrollmentPolicy|등록 정책을 찾을 수 없음|APNs(Apple Push Notification Service)와 같은 모든 등록 필수 구성 요소가 설정되었는지와 "플랫폼으로 iOS/iPadOS 사용"이 설정되었는지 확인합니다. 자세한 내용은 [iOS/iPadOS 및 Mac 디바이스 관리 설정](../ios-enroll.md)을 참조하세요.|
|DeviceCapReached|너무 많은 모바일 디바이스가 이미 등록되어 있습니다.|사용자는 다른 모바일 디바이스를 등록하기 전에 현재 등록된 모바일 디바이스 중 하나를 회사 포털에서 제거해야 합니다. 다음 중에서 사용 중인 디바이스 유형에 대한 지침을 참조하세요. [Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android), [iOS/iPadOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios), [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|모바일 디바이스가 회사 네트워크와 통신할 수 있도록 하는 인증서에 문제가 있습니다.<br /><br />|APNs(Apple Push Notification Service)에서 등록된 iOS/iPadOS 디바이스에 연결할 수 있는 채널을 제공합니다. 다음과 같은 경우 등록에 실패하면 이 메시지가 표시됩니다.<ul><li>APNs 인증서를 가져오는 단계가 완료되지 않았거나</li><li>APNs 인증서가 만료되었습니다.</li></ul>[Active Directory를 동기화하고 Intune에 사용자 추가](../fundamentals/users-add.md) 및 [사용자 및 디바이스 구성](../fundamentals/groups-add.md)에서 사용자를 설정하는 방법에 대한 정보를 검토하세요.|
|AccountNotOnboarded|모바일 디바이스가 회사 네트워크와 통신할 수 있도록 하는 인증서에 문제가 있습니다.<br /><br />|APNs(Apple Push Notification Service)에서 등록된 iOS/iPadOS 디바이스에 연결할 수 있는 채널을 제공합니다. 다음과 같은 경우 등록에 실패하면 이 메시지가 표시됩니다.<ul><li>APNs 인증서를 가져오는 단계가 완료되지 않았거나</li><li>APNs 인증서가 만료되었습니다.</li></ul>자세한 내용은 [Microsoft Intune을 사용한 iOS/iPadOS 및 Mac 관리 설정](../ios-enroll.md)을 검토하세요.|
|DeviceTypeNotSupported|사용자가 비 iOS 디바이스를 사용하여 등록하려고 했을 수 있습니다. 등록하려는 모바일 디바이스 유형이 지원되지 않습니다.<br /><br />디바이스가 iOS/iPadOS 버전 8.0 이상을 실행하고 있는지 확인합니다.<br /><br />|사용자 디바이스가 iOS/iPadOS 버전 8.0 이상을 실행하고 있어야 합니다.|
|UserLicenseTypeInvalid|사용자 계정이 아직 필수 사용자 그룹의 멤버가 아니므로 디바이스를 등록할 수 없습니다.<br /><br />|사용자가 디바이스를 등록하려면 올바른 사용자 그룹의 구성원이어야 합니다. 이 메시지는 모바일 디바이스 관리 기관에 맞지 않는 라이선스 형식이 있음을 의미합니다. 예를 들어 다음 두 가지가 모두 true인 경우 이 오류가 표시됩니다.<ol><li>Intune이 모바일 디바이스 관리 기관으로 설정되었습니다.</li><li>System Center 2012 R2 Configuration Manager를 사용하고 있습니다.</li></ol>자세한 내용은 다음 문서를 검토하세요.<br /><br />[Microsoft Intune을 사용한 iOS/iPadOS 및 Mac 관리 설정](../ios-enroll.md)과 [Active Directory를 동기화하고 Intune에 사용자 추가](../fundamentals/users-add.md) 및 [사용자 및 디바이스 구성](../fundamentals/groups-add.md)의 사용자를 설정하는 방법에 대한 정보를 검토하세요.|
|MdmAuthorityNotDefined|모바일 디바이스 관리 기관이 정의되지 않았습니다.<br /><br />|모바일 디바이스 관리 기관이 Intune에서 설정되지 않았습니다.<br /><br />그러면 [Microsoft Intune 30일 평가판으로 시작하기](../fundamentals/free-trial-sign-up.md)에서 “6단계: 모바일 디바이스 등록 및 앱 설치” 섹션의 항목 #1을 검토합니다.|

### <a name="devices-are-inactive-or-the-admin-console-cant-communicate-with-them"></a>디바이스가 비활성 상태이거나, 관리 콘솔에서 통신할 수 없습니다.
**문제:** iOS/iPadOS 디바이스가 Intune 서비스에서 체크 인되지 않습니다. 디바이스는 보호되는 회사 리소스에 대한 액세스를 유지하기 위해 서비스와 정기적으로 체크 인해야 합니다. 디바이스가 체크 인되지 않으면 다음과 같이 됩니다.

- 장치가 Intune 서비스에서 정책, 앱 및 원격 명령을 받을 수 없습니다.
- 관리자 콘솔에서 관리 상태가 **비정상**으로 표시됩니다.
- 조건부 액세스 정책으로 보호되는 사용자가 회사 리소스에 액세스할 수 없게 될 수 있습니다.

**해결 방법:** 최종 사용자에게 다음 해결 방법을 공유하여 회사 리소스에 대한 액세스 권한을 다시 얻도록 지원합니다.

iOS/iPadOS 회사 포털 앱을 시작할 때 디바이스와 Intune과의 연결이 끊겼는지 알 수 있습니다. 연결이 끊겼다고 감지되면 다시 연결하기 위해 Intune과 동기화를 자동으로 시도합니다(사용자에게는 **동기화하는 중...** 이라는 메시지가 표시됨).

  ![동기화하는 중 알림](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

동기화에 성공한 경우 iOS/iPadOS 회사 포털 앱에 **동기화 성공** 인라인 알림이 표시되어 디바이스가 정상 상태임을 나타냅니다.

  ![동기화 성공 알림](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

동기화에 실패할 경우 iOS/iPadOS 회사 포털 앱에 **동기화할 수 없음** 인라인 알림이 표시됩니다.

  ![동기화할 수 없음 알림](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

이 문제를 해결하려면 사용자는 **동기화할 수 없음** 알림 오른쪽에 있는 **설정** 단추를 선택해야 합니다. 설정 단추를 통해 사용자는 회사 액세스 설정 흐름 화면으로 이동하며, 여기에서 프롬프트에 따라 디바이스를 등록할 수 있습니다.

  ![회사 액세스 설정 화면](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

등록하고 나면 디바이스는 정상 상태로 되돌아가고 회사 리소스에 대한 액세스 권한을 다시 얻게 됩니다.

### <a name="verify-ws-trust-13-is-enabled"></a>WS-Trust 1.3이 사용하도록 설정되어 있는지 확인
**문제** DEP(디바이스 등록 프로그램) iOS/iPadOS 디바이스를 등록할 수 없습니다.

사용자 선호도를 사용하여 DEP 디바이스를 등록하려면 WS-Trust 1.3 사용자 이름/혼합 엔드포인트를 사용하도록 설정하여 사용자 토큰을 요청해야 합니다. 기본적으로 Active Directory에서는 이 엔드포인트를 사용하도록 설정합니다. 설정된 엔드포인트 목록을 가져오려면 Get-AdfsEndpoint PowerShell cmdlet을 사용하고 trust/13/UsernameMixed 엔드포인트를 조회합니다. 예를 들면 다음과 같습니다.

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

자세한 내용은 [Get-AdfsEndpoint 설명서](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)를 참조하세요.

자세한 내용은 [Active Directory Federation Services 보안에 대한 모범 사례](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs)를 참조하세요. WS-Trust 1.3 사용자 이름/혼합을 ID 페더레이션 공급자에 사용할지 여부를 결정하는 도움말의 경우:
- ADFS를 사용한다면 Microsoft 지원에 문의하세요.
- 타사 ID 공급 업체에 문의하세요.


### <a name="profile-installation-failed"></a>프로필 설치 실패
**문제:** iOS/iPadOS 디바이스에서 **프로필 설치 실패** 오류가 사용자에게 표시됩니다.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>실패한 프로필 설치에 대한 문제 해결 절차

1. 사용자가 사용 중인 Intune 서비스 버전에 적절한 라이선스를 할당받았는지 확인합니다.

2. 디바이스가 다른 MDM 공급자에 등록되지 않았는지 확인합니다.

3. 디바이스에 관리 프로필이 설치되지 않았는지 확인합니다.

4. [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)으로 이동하고 메시지가 표시되면 프로필을 설치하도록 시도합니다.

5. iOS/iPadOS용 Safari가 기본 브라우저이고 쿠키가 사용할 수 있도록 설정되어 있는지 확인합니다.

### <a name="users-iosipados-device-is-stuck-on-an-enrollment-screen-for-more-than-10-minutes"></a>10분 넘게 사용자의 iOS/iPadOS 디바이스가 등록 화면에서 중단되었습니다.

**문제**: 등록 중인 디바이스가 두 화면 중 하나에서 중단되었을 수 있습니다.
- "Microsoft"에서 최종 구성 대기 중
- 안내된 액세스 앱을 사용할 수 없음 관리자에게 문의하세요.

이 문제는 다음과 같은 경우에 발생할 수 있습니다.
- Apple 서비스에서 임시 중단이 발생했거나
- iOS/iPadOS 등록은 테이블에 표시된 대로 VPP 토큰을 사용하도록 설정되어 있지만 VPP 토큰에 문제가 발생했습니다.

| 등록 설정 | 값 |
| ---- | ---- |
| 플랫폼 | iOS/iPadOS |
| 사용자 선호도 | 사용자 선호도를 사용하여 등록 |
|Apple 설정 도우미 대신 회사 포털을 사용하여 인증 | 예 |
| VPP를 사용하여 회사 포털 설치 | 토큰 사용: 토큰 주소 |
| 인증할 때까지 회사 포털을 단일 앱 모드로 실행 | 예 |

**해결 방법**: 이 문제를 해결하려면 다음을 수행해야 합니다.
1. VPP 토큰에서 문제가 발생했는지 확인하고 해결합니다.
2. 차단된 디바이스를 식별합니다.
3. 영향을 받는 디바이스를 초기화합니다.
4. 등록 프로세스를 다시 시작한다고 사용자에게 알립니다.

#### <a name="determine-if-theres-something-wrong-with-the-vpp-token"></a>VPP 토큰에서 문제가 발생했는지 확인
1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **iOS** > **iOS 등록** > **등록 프로그램 토큰** > 토큰 이름 > **프로필** > 프로필 이름 > **관리** > **속성**을 선택합니다.
2. 속성을 검토하여 다음과 유사한 오류가 표시되는지 확인합니다.
    - 이 토큰은 만료되었습니다.
    - 이 토큰은 회사 포털 라이선스에 해당되지 않습니다.
    - 다른 서비스에서 이 토큰을 사용 중입니다.
    - 다른 테넌트에서 이 토큰을 사용 중입니다.
    - 이 토큰은 삭제되었습니다.
3. 토큰에 대한 문제를 해결합니다.

#### <a name="identify-which-devices-are-blocked-by-the-vpp-token"></a>VPP 토큰에서 차단된 디바이스 식별
1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **iOS**k > **iOS 등록** > **등록 프로그램 토큰** > 토큰 이름 > **디바이스**를 선택합니다.
2. **프로필 상태** 열을 **차단됨**으로 필터링합니다.
3. **차단됨** 상태인 모든 디바이스에 대한 일련 번호를 기록해 둡니다.

#### <a name="remotely-wipe-the-blocked-devices"></a>원격으로 차단된 디바이스 초기화
VPP 토큰에서 발생한 문제를 해결한 후에 차단된 디바이스를 초기화해야 합니다.
1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **모든 디바이스** > **열** > **일련 번호** > **적용**을 선택합니다. 
2. 차단된 디바이스 각각의 경우 **모든 디바이스** 목록에서 선택한 다음, **초기화** > **예**를 선택합니다.

#### <a name="tell-the-users-to-restart-the-enrollment-process"></a>등록 프로세스를 다시 시작한다고 사용자에게 알립니다.
차단된 디바이스를 초기화한 후에 등록 프로세스를 다시 시작한다고 사용자에게 알릴 수 있습니다.

## <a name="macos-issues"></a>macOS 문제

### <a name="macos-enrollment-errors"></a>macOS 등록 오류
**오류 메시지 1:** *가상 머신을 사용하는 것 같습니다. 일련 번호 및 하드웨어 모델을 포함하여 가상 머신을 완전히 구성했는지 확인합니다. 가상 머신이 아닌 경우 지원 부서에 문의하세요.*  

**오류 메시지 2:** *디바이스를 관리하는 데 문제가 있습니다. 이 문제는 가상 머신을 사용 중이거나 제한된 일련 번호가 있거나 이 디바이스가 이미 다른 사용자에게 할당된 경우 발생할 수 있습니다. 이러한 문제를 해결하는 방법을 알아보거나 회사 지원 부서에 문의하세요.*

**문제:** 이 메시지는 다음과 같은 이유로 인해 발생할 수 있습니다.  
- macOS VM(가상 머신)이 올바르게 구성되지 않았습니다.  
- 디바이스가 회사 소유이거나 Intune에 등록된 디바이스 일련 번호가 필요한 디바이스 제한을 사용하도록 설정했습니다.  
- 디바이스가 이미 등록되어 있고 Intune의 다른 사용자에게 할당되어 있습니다.  

**해결 방법:** 먼저 사용자에게 확인하여 디바이스에 영향을 주는 문제를 확인합니다. 그런 다음, 가장 관련성이 높은 다음 솔루션을 완료합니다.

- 사용자가 테스트를 위해 VM을 등록하는 경우 Intune이 일련 번호와 하드웨어 모델을 인식할 수 있도록 VM이 완전히 구성되었는지 확인합니다. Intune에서 [VM을 설정](macos-enroll.md#enroll-virtual-macos-machines-for-testing)하는 방법에 대해 자세히 알아보세요.
- 조직에서 개인 macOS 디바이스를 차단하는 등록 제한을 설정하는 경우 수동으로 [개인 디바이스 일련 번호 추가](corporate-identifiers-add.md#manually-enter-corporate-identifiers)를 Intune에 추가해야 합니다.  
- 디바이스가 Intune의 다른 사용자에게 여전히 할당된 경우 이전 소유자가 회사 포털 앱을 사용하여 디바이스를 제거하거나 재설정하지 않았습니다. Intune에서 부실 디바이스 레코드를 정리하려면:  

    1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 관리 자격 증명을 사용하여 로그인합니다.
    2. **디바이스** > **모든 디바이스**를 선택합니다.  
    3. 등록 문제가 있는 디바이스를 찾습니다. 디바이스 이름 또는 MAC/HW 주소로 검색하여 결과를 좁힙니다.
    4. 디바이스 > **삭제**를 선택합니다. 디바이스와 연결된 다른 모든 항목을 삭제합니다.  

## <a name="pc-issues"></a>PC 문제

|오류 메시지|문제|해결 방법|
|---|---|---|
|**IT 관리자가 액세스에 대한 라이선스를 할당해야 함**<br>IT 관리자는 사용자에게 이 앱을 사용할 수 있는 액세스 권한을 할당하지 않았습니다. IT 관리자에게 도움을 받거나 나중에 다시 시도하세요.|사용자 계정에 필요한 라이선스가 없으므로 디바이스를 등록할 수 없습니다.|사용자가 디바이스를 등록하려면 먼저 필요한 라이선스를 할당받아야 합니다. 이 메시지는 모바일 디바이스 관리 기관에 맞지 않는 라이선스 형식이 있음을 의미합니다. 예를 들어 다음 두 가지가 모두 true인 경우 이 오류가 표시됩니다. <ol><li>Intune이 모바일 디바이스 관리 기관으로 설정되었습니다.</li><li>System Center 2012 R2 Configuration Manager를 사용하고 있습니다.</li></ol>[사용자 계정에 Intune 라이선스를 할당하는 방법](../fundamentals/licenses-assign.md)에 대한 정보를 참조하세요.|

### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>컴퓨터가 이미 등록되었습니다. - 오류: hr 0x8007064c

**문제:** **머신이 이미 등록되었습니다.** 라는 오류와 함께 등록에 실패합니다. 등록 로그에 **hr 0x8007064c** 오류가 표시됩니다.

이 오류는 컴퓨터가 다음과 같은 상태이기 때문에 발생할 수 있습니다.

- 이전에 등록되었거나
- 이미 등록된 컴퓨터의 복제된 이미지를 포함합니다.
이전 계정의 계정 인증서가 컴퓨터에 아직 존재합니다.

**해결 방법:**

1. **시작** 메뉴에서 **실행** -> **MMC**를 입력합니다.
1. **파일** > **스냅인 추가/제거**를 선택합니다.
1. **인증서**를 두 번 클릭하고 **컴퓨터 계정** > **다음**을 선택한 후 **로컬 컴퓨터**를 선택합니다.
1. **인증서(로컬 컴퓨터)** 를 두 번 클릭하고 **개인/인증서**를 선택합니다.
1. Sc_Online_Issuing에서 발급한 Intune 인증서를 찾아서 있으면 삭제합니다.
1. 다음 레지스트리 키가 있으면 삭제합니다. **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** 및 모든 하위 키
1. 다시 등록해 보세요.
1. PC를 여전히 등록할 수 없으면 이 키를 찾은 다음, 해당 키가 있으면 삭제합니다. **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**
1. 다시 등록해 보세요.

    > [!IMPORTANT]
    > 이 섹션, 방법, 또는 작업에는 레지스트리를 수정하는 방법이 포함됩니다. 하지만, 레지스트리를 잘못 수정하면 심각한 문제가 발생할 수 있습니다. 따라서, 단계를 신중하게 따라야 합니다. 추가적인 보호를 위해, 수정하기 전에 레지스트리를 백업하세요. 그러면 문제가 발생했을 때 레지스트리를 복원할 수 있습니다.
    > 레지스트리를 백업하고 복원하는 방법에 대한 자세한 내용은 [How to back up and restore the registry in Windows](https://support.microsoft.com/kb/322756)(Windows에서 레지스트리를 백업하고 복원하는 방법)을 참조하세요.

## <a name="general-enrollment-error-codes"></a>일반적인 등록 오류 코드

|오류 코드|가능한 문제|권장되는 해결 방법|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |클라이언트 컴퓨터의 시계가 올바른 시간으로 설정되어 있지 않습니다.|클라이언트 컴퓨터의 시계 및 표준 시간대가 올바른 시간 및 표준 시간대로 설정되어 있는지 확인합니다.|
|0x80240438, 0x80CF0438, 0x80CF402C|Intune 서비스에 연결할 수 없습니다. 클라이언트 프록시 설정을 확인합니다.|Intune이 클라이언트 컴퓨터의 프록시 구성을 지원하는지 확인합니다. 클라이언트 컴퓨터가 인터넷에 연결되어 있는지 확인합니다.|
|0x80240438, 0x80CF0438|Internet Explorer 및 로컬 시스템의 프록시 설정이 구성되어 있지 않습니다.|Intune 서비스에 연결할 수 없습니다. 클라이언트 프록시 설정을 확인합니다. Intune이 클라이언트 컴퓨터의 프록시 구성을 지원하는지 확인합니다. 클라이언트 컴퓨터가 인터넷에 연결되어 있는지 확인합니다.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|등록 패키지가 오래되었습니다.|관리 작업 영역에서 최신 클라이언트 소프트웨어 패키지를 다운로드하여 설치합니다.|
|0x80043002, 0x80CF3002|계정이 유지 관리 모드에 있습니다.|계정이 유지 관리 모드인 경우 새 클라이언트 컴퓨터를 등록할 수 없습니다. 계정 설정을 보려면 자신의 계정으로 로그인합니다.|
|0x80043003, 0x80CF3003|계정이 삭제되었습니다.|Intune에 대한 계정과 구독이 계속 활성 상태인지 확인하십시오. 계정 설정을 보려면 자신의 계정으로 로그인합니다.|
|0x80043005, 0x80CF3005|클라이언트 컴퓨터가 사용 중지되었습니다.|몇 시간 기다렸다가 이전 버전의 클라이언트 소프트웨어를 컴퓨터에서 제거한 다음 클라이언트 소프트웨어를 다시 설치해 봅니다.|
|0x80043006, 0x80CF3006|계정에 허용되는 최대 사용자 수에 도달했습니다.|서비스에 클라이언트 컴퓨터를 더 등록하려면 조직에서 추가 사용자 수를 구입해야 합니다.|
|0x80043007, 0x80CF3007|설치 관리자 프로그램과 같은 폴더에서 인증서 파일을 찾을 수 없습니다.|모든 파일을 추출한 후에 설치를 시작합니다. 추출된 파일의 이름이나 위치를 바꾸지 마십시오. 모든 파일은 같은 폴더에 있어야 합니다. 그렇지 않으면 설치할 수 없습니다.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|클라이언트 컴퓨터를 다시 시작하는 작업이 보류되어 소프트웨어를 설치할 수 없습니다.|컴퓨터를 다시 시작한 다음 클라이언트 소프트웨어를 다시 설치해 봅니다.|
|0x80070032|클라이언트 컴퓨터에 클라이언트 소프트웨어를 설치하기 위한 필수 구성 요소가 하나 이상 없습니다.|클라이언트 컴퓨터에 필수 업데이트가 모두 설치되었는지 확인한 다음 클라이언트 소프트웨어를 다시 설치해 봅니다.|
|0x80043008, 0x80CF3008|Microsoft Online Management Updates 서비스를 시작하지 못했습니다.|[Microsoft Intune에 대한 지원을 받는 방법](../fundamentals/get-support.md)의 설명에 따라 Microsoft 지원에 문의합니다.|
|0x80043009, 0x80CF3009|클라이언트 컴퓨터가 이미 서비스에 등록되어 있습니다.|클라이언트 컴퓨터를 서비스에 다시 등록하기 전에 사용 중지해야 합니다.|
|0x8004300B, 0x80CF300B|클라이언트를 실행 중인 Windows 버전이 지원되지 않으므로 클라이언트 소프트웨어 설치 패키지를 실행할 수 없습니다.|Intune에서 클라이언트 컴퓨터에서 실행 중인 Windows 버전을 지원하지 않습니다.|
|0xAB2|Windows Installer에서 사용자 지정 작업에 대한 VBScript 런타임에 액세스할 수 없습니다.|이 오류는 DLL(동적 연결 라이브러리)에 기반한 사용자 지정 작업으로 인해 발생합니다. DLL 문제를 해결할 때 [Microsoft 지원 KB198038: 패키지 및 배포 문제에 대한 유용한 도구](https://support.microsoft.com/kb/198038)에 설명된 도구를 사용해야 할 수 있습니다.|
|0x80cf0440|서비스 엔드포인트에 대한 연결이 종료되었습니다.|평가판 또는 유료 계정 일시 중단되었습니다. 새 평가판 또는 유료 계정을 만들고 다시 등록합니다.|

## <a name="next-steps"></a>다음 단계

문제 해결 정보가 도움이 되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](../fundamentals/get-support.md)의 설명에 따라 Microsoft 지원에 문의하세요.
