---
title: Microsoft Intune의 Android 얼룩말 장치에서 StageNow 로그 사용-Azure | Microsoft Docs
description: Microsoft Intune를 사용 하 여 Android 장치에서 StageNow를 사용 하는 경우 일반적인 문제 및 해결 방법을 참조 하세요. 로그를 가져오는 방법에 대해 알아보고 성공 또는 오류에 대 한 로그를 읽는 방법에 대 한 예제를 확인 합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7ed93c86d3fbe7ed7a6ac5d4b1a3494fb55f2bc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506997"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Microsoft Intune에서 Android 얼룩말 장치에 대 한 문제 해결 및 잠재적인 문제 확인

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune에서 [MX (얼룩말 Mobility Extensions)를 사용 하 여 Android 얼룩말 장치를 관리할](android-zebra-mx-overview.md)수 있습니다. 얼룩말 장치를 사용 하는 경우 StageNow에서 프로필을 만들어 설정을 관리 하 고 Intune에 업로드 합니다. Intune은 StageNow 앱을 사용 하 여 장치에 설정을 적용 합니다. 또한 StageNow 앱은 문제를 해결 하는 데 사용 되는 자세한 로그 파일을 장치에 만듭니다.

이 기능은 다음에 적용됩니다.

- Android

예를 들어 StageNow에서 프로필을 만들어 장치를 구성 합니다. StageNow 프로필을 만들 때 마지막 단계에서는 프로필을 테스트 하는 데 사용할 파일을 생성 합니다. 장치에서 StageNow 앱을 사용 하 여이 파일을 사용 합니다.

또 다른 예로 StageNow에서 프로필을 만들고 테스트 합니다. Intune에서 StageNow 프로필을 추가한 다음 얼룩말 장치에 할당 합니다. 할당 된 프로필의 상태를 확인할 때 프로필에는 높은 수준의 상태가 표시 됩니다.

이러한 두 경우 모두 StageNow 프로필이 적용 될 때마다 장치에 저장 되는 StageNow 로그 파일에서 자세한 정보를 얻을 수 있습니다.

일부 문제는 StageNow 프로필의 내용과 관련이 없으며 로그에 반영 되지 않습니다.

이 문서에서는 StageNow 로그를 읽고 로그에 반영 되지 않을 수 있는 얼룩말 장치를 사용 하 여 다른 잠재적인 문제를 나열 하는 방법을 보여 줍니다.

이 기능에 대 한 자세한 내용은 [얼룩말 Mobility Extensions를 사용 하 여 얼룩말 장치 사용 및 관리를 사용](android-zebra-mx-overview.md) 합니다.

## <a name="get-the-logs"></a>로그 가져오기

### <a name="use-the-stagenow-app-on-the-device"></a>장치에서 StageNow 앱 사용
에서 컴퓨터의 StageNow을 사용 하 여 프로필을 직접 테스트 하는 경우 [Intune을](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow)사용 하 여 프로필을 배포 하는 대신 장치의 StageNow 앱에서 테스트의 로그를 저장 합니다. 로그 파일을 가져오려면 장치에서 StageNow 앱의 **자세히 (...)** 옵션을 사용 합니다.

### <a name="get-logs-using-android-debug-bridge"></a>Android Debug Bridge를 사용 하 여 로그 가져오기
Intune을 사용 하 여 프로필을 이미 배포한 후에 로그를 가져오려면 [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) 를 사용 하 여 컴퓨터에 장치를 연결 합니다 (Android의 웹 사이트를 엽니다).

장치에서 로그는 `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`에 저장 됩니다.

### <a name="get-logs-from-email"></a>전자 메일에서 로그 가져오기
Intune을 사용 하 여 프로필을 이미 배포한 후에 로그를 가져오기 위해 최종 사용자는 장치에서 전자 메일 앱을 사용 하 여 로그를 전자 메일로 보낼 수 있습니다. 얼룩말 장치에서 회사 포털 앱을 열고 [로그를 보냅니다](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 로그 보내기 기능을 사용 하면 Microsoft 지원에 문의 하는 경우 참조할 수 있는 PowerLift 인시던트 ID도 만들어집니다.

## <a name="read-the-logs"></a>로그 읽기

로그를 볼 때 `<characteristic-error>` 태그가 표시 될 때마다 오류가 발생 합니다. 오류 세부 정보는 `<parm-error>` 태그 > `desc` 속성에 기록 됩니다.

## <a name="error-types"></a>오류 유형

얼룩말 장치에는 여러 오류 보고 수준이 포함 됩니다.

- CSP는 장치에서 지원 되지 않습니다. 예를 들어 장치는 셀룰러 장치가 아니며 셀룰러 관리자를 포함 하지 않습니다.
- MX 또는 OSX 버전이 일치 하지 않습니다. 각 CSP에는 버전이 지정 되어 있습니다. 전체 지원 매트릭스는 [얼룩말의 설명서](http://techdocs.zebra.com/mx/) (얼룩말의 웹 사이트 열림)를 참조 하세요.
- 장치에서 다른 문제 또는 오류를 보고 합니다.

## <a name="examples"></a>예

예를 들어 다음과 같은 입력 프로필을 사용할 수 있습니다.

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

로그에서 XML은 입력과 동일 합니다. 이 일치 하는 출력은 프로필을 오류 없이 장치에 성공적으로 적용 했음을 의미 합니다.

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

다른 예제에는 다음과 같은 입력이 있습니다.

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

`<characteristic-error>` 태그를 포함 하 고 있으므로 로그에 오류가 표시 됩니다. 이 시나리오에서 프로필은 지정 된 경로에 없는 APK (Android 패키지)를 설치 하려고 시도 했습니다.

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>얼룩말 장치에 대 한 기타 잠재적인 문제

이 섹션에는 장치 관리자와 얼룩말 장치를 사용할 때 나타날 수 있는 다른 문제가 나열 되어 있습니다. 이러한 문제는 StageNow 로그에 보고 되지 않습니다.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView 만료 됨

이전 장치에서 회사 포털 앱을 사용 하 여 로그인 하는 경우에는 시스템 웹 보기 구성 요소가 최신이 아니므로 업그레이드 해야 한다는 메시지가 사용자에 게 표시 될 수 있습니다. 장치에 Google Play 설치 되어 있으면 인터넷에 연결 하 고 업데이트를 확인 합니다. 장치에 Google Play 설치 되어 있지 않으면 구성 요소의 업데이트 된 버전을 가져와서 장치에 적용 합니다. 또는 얼룩말에서 발행 한 최신 장치 OS로 업데이트 합니다.

### <a name="management-actions-take-a-long-time"></a>관리 작업에 시간이 오래 걸립니다.

Google Play 서비스를 사용할 수 없는 경우 몇 가지 작업을 완료 하는 데 최대 8 시간이 걸립니다. [Android 용 Intune 회사 포털 앱](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (다른 Microsoft 웹 사이트 열기)의 제한 사항이 좋은 리소스 일 수 있습니다.

### <a name="device-spoofing-suspected-shows-in-intune"></a>Intune의 "장치 스푸핑 의심" 표시

이 오류는 Intune이 얼룩말 않은 Android 장치에서 해당 모델 및 제조업체를 얼룩말 장치로 보고 하는 것으로 의심 됨을 의미 합니다.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>회사 포털 앱이 필요한 최소 버전 보다 이전 버전입니다.

Intune은 회사 포털 앱의 최소 필수 버전을 업데이트할 수 있습니다. Google Play 장치에 설치 되어 있지 않으면 회사 포털 앱이 자동으로 업데이트 되지 않습니다. 필요한 최소 버전이 설치 된 버전 보다 최신인 경우 회사 포털 앱의 작동이 중지 됩니다. [얼룩말 장치에서 테스트용 로드](android-zebra-mx-overview.md#sideload-the-company-portal-app)를 사용 하 여 최신 회사 포털 앱으로 업데이트 합니다.

## <a name="next-steps"></a>다음 단계

[얼룩말 토론 게시판](https://developer.zebra.com/community/home/discussions) (얼룩말의 웹 사이트 열림)

[Intune에서 Zebra Mobility Extensions를 사용하여 Zebra 디바이스 사용 및 관리](android-zebra-mx-overview.md)
