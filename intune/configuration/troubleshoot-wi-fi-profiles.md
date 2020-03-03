---
title: Microsoft Intune에서 Wi-Fi 디바이스 프로필 로그 문제 해결 및 검토 - Azure | Microsoft Docs
description: Microsoft Intune에서 Android, iOS/iPadOS 및 Windows 디바이스에 대한 Wi-Fi 디바이스 구성 프로필 문제를 이해하고 해결합니다. 로그를 검토하고 몇 가지 일반적인 문제 및 가능한 해결 방법을 확인합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db663f96f1e4fe84c506395b98c52956069e5426
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512826"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Microsoft Intune에서 Wi-Fi 디바이스 구성 프로필 문제 해결

Intune에서 WiFi 네트워크에 대한 연결 설정을 포함하는 디바이스 구성 프로필을 만들 수 있습니다. 해당 설정을 사용하여 사용자의 Android, iOS/iPadOS 및 Windows 디바이스를 조직 네트워크에 연결합니다.

이 문서에서는 Wi-Fi 프로필을 디바이스에 성공적으로 적용한 경우의 모습을 보여 줍니다. 여기에는 로그 정보, 일반적인 문제 등도 포함됩니다. 이 문서를 사용하여 Wi-Fi 프로필 문제를 해결할 수 있습니다.

Intune의 Wi-Fi 프로필에 대한 자세한 내용은 [디바이스에서 Wi-Fi 설정 추가 및 사용](wi-fi-settings-configure.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

이 문서의 예제에서는 Intune 프로필에 SCEP 인증서 인증을 사용합니다. 또한 디바이스에서 신뢰할 수 있는 루트 및 SCEP 프로필이 제대로 작동한다고 가정합니다.

## <a name="android"></a>Android

이 섹션에서는 Android 디바이스에 구성 프로필을 설치할 때 최종 사용자 환경을 단계별로 설명합니다.

### <a name="end-user-experience-example"></a>최종 사용자 환경 예

이 시나리오에서는 Nokia 6.1 디바이스를 사용합니다. 디바이스에 Wi-Fi 프로필을 설치하기 전에 신뢰할 수 있는 루트 및 SCEP 프로필을 설치합니다.

1. 최종 사용자에게 신뢰할 수 있는 루트 인증서 프로필을 설치하라는 알림이 표시됩니다.

    > [!div class="mx-imgBorder"]
    > ![신뢰할 수 있는 루트 인증서 프로필 설치에 대한 Android의 샘플 회사 포털 앱 알림](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. 다음 알림은 SCEP 인증서 프로필을 설치하라는 메시지를 표시합니다.

    > [!div class="mx-imgBorder"]
    > ![SCEP 인증서 프로필 설치에 대한 Android의 샘플 회사 포털 앱 알림](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > 디바이스 관리자가 관리하는 Android 디바이스를 사용하는 경우 여러 인증서가 나열될 수 있습니다. 인증서 프로필이 해지 또는 제거되어도 인증서는 디바이스에 유지됩니다. 이 시나리오에서는 최신 인증서를 선택합니다. 일반적으로 목록에 표시되는 마지막 인증서가 최신 인증서입니다.
    >
    > Android Enterprise 및 Samsung Knox 디바이스에서는 이러한 상황이 발생하지 않습니다. 자세한 내용은 [Android 회사 프로필 디바이스 관리](../enrollment/android-enterprise-overview.md) 및 [SCEP 및 PKCS 인증서 제거](../protect/remove-certificates.md#android-knox-devices)를 참조하세요.

3. 다음으로 사용자는 Wi-Fi 프로필을 설치하라는 알림을 받게 됩니다.

    > [!div class="mx-imgBorder"]
    > ![SCEP 인증서 프로필 설치에 대한 Android의 샘플 회사 포털 앱 알림](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. 완료되면 Wi-Fi 연결이 저장된 네트워크로 표시됩니다.

    > [!div class="mx-imgBorder"]
    > ![Wi-Fi 연결이 저장된 네트워크로 표시됨](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>회사 포털 앱 로그 검토

Android에서 **Omadmlog.log** 파일은 디바이스에 설치된 Wi-Fi 프로필의 작업을 자세히 설명합니다. Omadmlog 로그 파일은 최대 5개까지 있을 수 있습니다. 관련 로그 항목을 찾는 데 도움이 되므로 마지막 동기화의 타임스탬프를 가져와야 합니다.

다음 예제에서는 [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace)를 사용하여 로그를 읽고 "wifimgr"을 검색합니다.

> [!div class="mx-imgBorder"]
> ![Wi-Fi 연결이 저장된 네트워크로 표시됨](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

다음 로그에는 검색 결과가 표시되며, Wi-Fi 프로필이 성공적으로 적용되었다고 표시됩니다.

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="iosipados"></a>iOS/iPadOS

Wi-Fi 프로필을 디바이스에 설치하면 **관리 프로필**에 표시됩니다.

> [!div class="mx-imgBorder"]
> ![Intune에 있는 iOS/iPadOS 디바이스의 관리 프로필](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![Wi-Fi 연결이 Intune에 있는 iOS/iPadOS 디바이스에서 Wi-Fi 네트워크로 표시됨](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-iosipados-console-and-device-logs"></a>iOS/iPadOS 콘솔 및 디바이스 로그 검토

iOS/iPadOS 디바이스에서 회사 포털 앱 로그는 Wi-Fi 프로필에 대한 정보를 포함하지 않습니다. Wi-Fi 프로필에 대한 설치 세부 정보를 보려면 콘솔/디바이스 로그를 사용합니다.

1. iOS/iPadOS 디바이스를 Mac에 연결합니다. **애플리케이션** > **유틸리티**로 이동한 후 콘솔 앱을 엽니다.
2. **작업**에서 **정보 메시지 포함** 및 **디버그 메시지 포함**을 선택합니다.

    > [!div class="mx-imgBorder"]
    > ![iOS/iPadOS 콘솔 앱에 정보 메시지 포함 및 디버그 메시지 포함](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. 시나리오를 재현하고 로그를 텍스트 파일에 저장합니다.

    1. 현재 화면에서 모든 메시지를 선택합니다. **편집** > **모두 선택**.
    2. 다음과 같이 메시지를 복사합니다. **편집** > **복사**.
    3. 로그 데이터를 텍스트 편집기에 붙여 넣고 파일을 저장합니다.

4. 저장된 로그 파일을 검색하여 자세한 정보를 확인합니다. 프로필이 성공적으로 설치되면 출력은 다음 로그와 유사하게 표시됩니다.

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

디바이스에 Wi-Fi 프로필이 설치되면 **설정** > **계정** > **회사 또는 학교 액세스**로 이동합니다. 다음과 같이 계정 > **정보**를 선택합니다.

> [!div class="mx-imgBorder"]
> ![회사 또는 학교에 액세스하고 Windows 디바이스에서 정보 선택](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

**Microsoft에서 관리하는 영역**에서 **WiFi**가 표시됩니다.

> [!div class="mx-imgBorder"]
> ![Microsoft에서 관리하는 영역에서 Windows에 WiFi가 나열됨](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

Wi-Fi 연결을 보려면 **설정** > **네트워크 및 인터넷**  > **Wi-Fi**로 이동합니다.

> [!div class="mx-imgBorder"]
> ![Windows에서 Wi-Fi 연결이 설정에 알려진 네트워크로 표시됨](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>이벤트 뷰어 로그 검토

Windows 디바이스에서 Wi-Fi 프로필에 대한 세부 정보는 다음과 같이 이벤트 뷰어에 기록됩니다.

1. **이벤트 뷰어** 앱을 엽니다.
2. **보기** 메뉴에서 **분석 및 디버그 로그 표시**를 선택합니다.
3. **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin** 확장

다음 로그와 비슷한 출력이 표시됩니다.

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>일반적인 문제

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>문제 1: Wi-Fi 프로필이 디바이스에 배포되지 않습니다.

- Wi-Fi 프로필이 올바른 그룹에 할당되었는지 확인합니다.

    1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **구성 프로필**을 선택합니다.
    2. 프로필 > **할당**을 선택합니다. 선택한 그룹이 올바른지 확인합니다.
    3. Endpoint Manager에서 **문제 해결 + 지원**을 선택합니다. **할당** 정보를 검토합니다.

- Endpoint Manager에서 **문제 해결 + 지원**을 선택합니다. **마지막 체크 인** 시간을 확인하여 디바이스를 Intune과 동기화할 수 있는지 확인합니다.

- Wi-Fi 프로필이 신뢰할 수 있는 루트 및 SCEP 프로필에 연결된 경우 두 프로필이 디바이스에 배포되었는지 확인합니다. Wi-Fi 프로필은 이러한 프로필에 종속되어 있습니다.

- Windows 10 이상 디바이스에서 MDM 진단 정보 로그를 검토합니다.

  1. **설정** > **계정** > **회사 또는 학교 액세스**로 이동합니다.
  2. 회사 또는 학교 계정 > **정보**를 선택합니다.
  3. **설정** 페이지 맨 아래에서 **보고서 만들기**를 선택합니다.
  4. 로그 파일에 대한 경로를 표시하는 창이 열립니다. **내보내기**를 선택합니다.
  5. `\Users\Public\Documents\MDMDiagnostics` 경로로 이동한 후 보고서를 봅니다.

      > [!div class="mx-imgBorder"]
      > ![Windows 10 디바이스에 WiFi 프로필 구성을 표시하는 샘플 MDM 진단 정보](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > 자세한 내용은 [Windows 10의 MDM 오류 진단](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)을 참조하세요.

- Android 디바이스에서 신뢰할 수 있는 루트 및 SCEP 프로필을 설치하지 않은 경우 회사 포털 앱 Omadmlog 파일에 다음 항목이 표시됩니다.

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - 신뢰할 수 있는 루트 및 SCEP 프로필이 Android 디바이스에 있고 규정을 준수하는 데, Wi-Fi 프로필이 디바이스에 없을 수 있습니다. 이 문제는 회사 포털 앱의 **CertificateSelector** 공급자가 지정된 조건과 일치하는 인증서를 찾지 못하는 경우에 발생합니다. 구체적인 조건은 인증서 템플릿 또는 SCEP 프로필에 있을 수 있습니다.

    일치하는 인증서를 찾을 수 없는 경우 디바이스에 인증서가 설치되지 않은 것입니다. Wi-Fi 프로필은 올바른 인증서를 포함하지 않으므로 적용되지 않습니다. 이 시나리오에서는 회사 포털 앱 Omadmlog 파일에 다음 항목이 표시됩니다.

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    다음 샘플 로그는 **범용** EKU(확장된 키 사용) 조건을 지정했기 때문에 제외되는 인증서를 보여 줍니다. 그러나 디바이스에 할당된 인증서에는 해당 EKU가 없습니다.

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    다음 샘플에서는 SCEP 프로필이 **범용** EKU를 입력했음을 보여 줍니다. 그렇지만 CA(인증 기관)의 인증서 템플릿에는 입력되지 않습니다. 이 문제를 해결하려면 **범용** 옵션을 인증서 템플릿에 추가합니다. 또는 SCEP 프로필에서 **범용** 옵션을 제거합니다.

    > [!div class="mx-imgBorder"]
    > ![Android에서 인증 기관의 인증서 템플릿에 범용 추가](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![Android에서 Intune의 SCEP 인증서 구성 프로필에 범용 추가](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - 전체 인증서 체인의 모든 필수 인증서가 Android 디바이스에 있는지 확인합니다. 그렇지 않으면 디바이스에 Wi-Fi 프로필을 설치할 수 없습니다. 자세한 내용은 [중간 인증 기관 누락](https://developer.android.com/training/articles/security-ssl#MissingCa)(Android의 웹 사이트 열기)를 참조하세요.
  - 키워드로 Omadmlog를 필터링하여 Wi-Fi 프로필에 사용되는 인증서 및 프로필이 성공적으로 적용되었는지 여부 등의 정보를 확인합니다.

    예를 들어 [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace)를 사용하여 로그를 읽습니다. 다음과 같이 검색 문자열을 사용하여 "wifimgr"을 필터링합니다.

    > [!div class="mx-imgBorder"]
    > ![CMTrace를 필터링하여 Android 디바이스에서 WiFiMgr 구성 프로필 찾기](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    출력은 다음 로그와 같이 표시됩니다.

    > [!div class="mx-imgBorder"]
    > ![디바이스에 성공적으로 적용된 WiFi Intune 구성 프로필을 보여 주는 샘플 CMTrace 로그 출력](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    로그에 오류가 표시되면 오류의 타임스탬프를 복사하고 로그의 필터링을 해제합니다. 그런 다음, 타임스탬프와 함께 "찾기" 옵션을 사용하여 오류 직전에 발생한 상황을 확인합니다.

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>문제 2: Wi-Fi 프로필이 디바이스에 배포되었지만 디바이스에서 네트워크에 연결할 수 없습니다.

일반적으로 이 문제는 Intune 외부의 원인으로 인해 발생합니다. 다음 작업은 연결 문제를 이해하고 해결하는 데 도움이 될 수 있습니다.

- Wi-Fi 프로필의 경우와 동일한 조건으로 인증서를 사용하여 네트워크에 수동으로 연결합니다.

  연결할 수 있는 경우 수동 연결에서 인증서 속성을 확인합니다. 그런 다음, 동일한 인증서 속성으로 Intune Wi-Fi 프로필을 업데이트합니다.
- 연결 오류는 일반적으로 Radius 서버 로그에 기록됩니다. 예를 들어, 디바이스가 Wi-Fi 프로필에 연결하려고 시도했는지 여부가 표시됩니다.

## <a name="need-more-help"></a>추가 도움 필요

- [Intune 사용자 포럼](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)을 사용하거나 [Microsoft에서 지원을 받으세요](../fundamentals/get-support.md).

- Microsoft Intune의 Wi-Fi 프로필에 대한 자세한 내용은 다음 문서를 참조하세요.

  - [Android](wi-fi-settings-android.md), [iOS/iPadOS](wi-fi-settings-ios.md) 및 [Windows 10 이상](wi-fi-settings-windows.md)을 실행하는 디바이스에서 Wi-Fi 설정을 추가합니다.
  - [지원 팁 - Intune에서 SCEP 인증서 배포를 위해 NDES를 구성하는 방법](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - [SCEP 인증서 프로필 배포](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune) 및 [NDES 구성](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune) 문제를 해결합니다.

- 최신 뉴스, 정보 및 기술 팁은 공식 블로그를 참조하세요.
  - [Microsoft Intune 지원 팀 블로그](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Microsoft Enterprise Mobility + Security 블로그](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>다음 단계

[프로필을 모니터링합니다](device-profile-monitor.md).
