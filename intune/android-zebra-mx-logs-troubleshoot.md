---
title: Microsoft Intune-Azur에서에서 얼룩말 Android 장치에서 사용 하 여 StageNow 기록 | Microsoft Docs
description: Microsoft Intune을 사용 하 여 Android 장치에서 StageNow를 사용 하는 경우 일반적인 문제 및 해결 방법을 참조 하세요. 또한 로그를 가져오고 성공 또는 오류에 대 한 로그를 읽는 방법의 예제를 참조 하는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36476820805c00cefafcd9f64dd2f08a014762c0
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490544"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Microsoft Intune에서 Android 얼룩말 장치에서 잠재적인 문제를 살펴보고 문제 해결

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune에서 사용할 수 있습니다 [얼룩말 Android 장치를 관리 하려면 얼룩말 Mobility 확장 (MX)](android-zebra-mx-overview.md)합니다. 얼룩말 장치를 사용 하는 경우 프로필에서 설정을 관리할 수는 StageNow 만들고 Intune에 업로드 합니다. Intune 장치에 설정을 적용 하려면 StageNow 앱을 사용 합니다. 또한 StageNow 앱 문제를 해결 하는 데 사용 되는 장치에 자세한 로그 파일을 만듭니다.

이 기능은 다음에 적용됩니다.

- Android

예를 들어, 장치를 구성 하는 StageNow에서 프로필을 만듭니다. StageNow 프로필을 만들 때 마지막 단계는 프로필을 테스트에 대 한 파일을 생성 합니다. 장치에서이 파일 StageNow 앱을 사용합니다.

또 다른 예로, StageNow에서 프로필을 만드는 하 고 테스트 합니다. Intune에서 StageNow 프로필을 추가한 다음 얼룩말 장치에 할당 합니다. 할당 된 프로필의 상태를 검사 하는 경우 프로필을 상위 수준 상태를 표시 합니다.

두 경우 모두 StageNow 프로필을 적용 될 때마다 장치에 저장 됩니다 StageNow 로그 파일에서 자세한 세부 정보를 가져올 수 있습니다.

일부 문제 StageNow 프로필 내용의 관련이 없는 및 로그에 반영 되지 않습니다.

이 문서에서는 StageNow 로그를 읽는 방법을 보여 줍니다 하 고 로그에 반영 되지 않을 얼룩말 장치와 다른 일부 잠재적인 문제를 나열 합니다.

[사용 및 관리 얼룩말 Mobility 확장을 사용 하 여 얼룩말 장치](android-zebra-mx-overview.md) 이 기능에 대 한 자세한 내용은 합니다.

## <a name="get-the-logs"></a>로그 가져오기

### <a name="use-the-stagenow-app-on-the-device"></a>장치의 StageNow 앱을 사용 합니다.
직접 StageNow를 사용 하 여 컴퓨터에 사용 하는 대신 프로필을 테스트할 때 [프로필을 배포 하려면 Intune](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), 장치의 StageNow 앱 테스트에서 로그를 저장 합니다. 로그 파일을 사용 합니다 **자세한 (...)**  StageNow 앱에서 장치의 옵션입니다.

### <a name="get-logs-using-android-debug-bridge"></a>Android 디버그 브리지를 사용 하 여 로그 가져오기
로그를 가져오려면 프로필은 Intune을 사용 하 여 이미 배포 된 후 장치를 컴퓨터에 연결 [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) (Android의 웹 사이트 열기).

장치에서 로그에 저장 됩니다. `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>전자 메일에서 로그 가져오기
로그를 가져오려면 프로필은 Intune을 사용 하 여 이미 배포 된 후 최종 사용자에 게 전자 메일을 보내도 장치의 메일 앱을 사용 하 여 로그 합니다. 얼룩말 장치에서 회사 포털 앱을 열고 하 고 [로그를 전송할](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)합니다. 전송 로그 기능을 사용 하 여 만들어지기를 PowerLift 인시던트 ID를 Microsoft 지원에 문의 하는 경우를 참조할 수 있습니다.

## <a name="read-the-logs"></a>로그 읽기

로그를 볼 때 오류가 발생 하는 표시 될 때마다는 `<characteristic-error>` 태그입니다. 오류 세부 정보에 기록 되는 `<parm-error>` 태그 > `desc` 속성입니다.

## <a name="error-types"></a>오류 유형

얼룩말 장치에는 다양 한 오류 보고 수준을 포함 됩니다.

- CSP는 장치에서 지원 되지 않습니다. 예를 들어 장치가 셀룰러 장치 아니며 셀룰러 관리자가 없습니다.
- MX 또는 OSX 버전 일치 하지 않습니다. 각 CSP는 버전이 있습니다. 전체 지원 매트릭스를 참조 하세요 [얼룩말의 설명서](http://techdocs.zebra.com/mx/) (얼룩말의 웹 사이트 열기).
- 장치는 다른 문제 또는 오류를 보고합니다.

## <a name="examples"></a>예

예를 들어, 다음 프로필 입력된 해야합니다.

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

로그에서 XML 입력와 동일합니다. 이 일치 하는 출력 오류 없이 장치에 성공적으로 적용 하는 프로필을 의미 합니다.

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

또 다른 예로, 다음 입력을 해야합니다.

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

포함 된 로그 오류를 보여 줍니다는 `<characteristic-error>` 태그입니다. 이 시나리오에서는 프로필 지정된 된 경로에 존재 하지 않는 Android 패키지 (APK)를 설치 하려고 합니다.

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

## <a name="other-potential-issues-with-zebra-devices"></a>얼룩말 장치와 다른 잠재적인 문제

이 섹션에서는 장치 관리자를 사용 하 여 얼룩말 장치를 사용할 때 표시 될 수 있습니다 다른 가능한 문제를 나열 합니다. 이러한 문제는 StageNow 로그에 보고 되지 않습니다.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView 만료 되었습니다.

이전 버전의 장치를 회사 포털 앱을 사용 하 여 로그인 할 때 사용자는 메시지는 시스템 WebView 구성 요소는 오래 된 필요한 업그레이드 볼 수 있습니다. Google Play를 설치 하는 장치에 있는 경우, 인터넷 및 업데이트 확인에 연결 합니다. 장치가 없는 경우 Google Play를 설치, 구성 요소의 업데이트 된 버전 및 장치에 적용 합니다. 또는 최신 장치 얼룩말에서 발급 한 OS 업데이트 합니다.

### <a name="management-actions-take-a-long-time"></a>관리 작업에 시간이 오래 걸릴

Google Play services을 사용할 수 없는 경우 일부 작업 완료 하는 데 최대 8 시간이 수행 됩니다. [Android에 대 한 제한 사항의 Intune 회사 포털 앱](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (다른 Microsoft 웹 사이트 열기)은 좋은 리소스일 수 있습니다.

### <a name="device-spoofing-suspected-shows-in-intune"></a>Intune에서 "의심 스러운 스푸핑된 장치"를 보여 줍니다.

이 오류는 Intune에서 해당 모델과 얼룩말 장치 제조업체가 아닌-얼룩말 Android 장치를 보고 검색 하 의미 합니다.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>필요한 최소 버전 보다 오래 된 회사 포털 앱

Intune 회사 포털 앱의 최소 필수 버전을 업데이트할 수 있습니다. Google Play 장치에 설치 되지 않은 경우 회사 포털 앱을 자동으로 업데이트 되지 않습니다. 필요한 최소 버전은 설치 된 버전 보다 최신, 회사 포털 앱 작동을 멈춥니다. 사용 하 여 최신 회사 포털 앱 업데이트 [얼룩말 장치에서 테스트용 로드](android-zebra-mx-overview.md#sideload-the-company-portal-app)합니다.

## <a name="next-steps"></a>다음 단계

[얼룩말 토론 게시판](https://developer.zebra.com/community/home/discussions) (얼룩말의 웹 사이트 열기)

[사용 하 고 Intune에서 얼룩말 Mobility 확장을 사용 하 여 얼룩말 장치 관리](android-zebra-mx-overview.md)
