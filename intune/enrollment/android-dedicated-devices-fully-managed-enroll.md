---
title: Intune에서 Android Enterprise 전용 디바이스 또는 완전 관리형 디바이스 등록
titleSuffix: Microsoft Intune
description: Intune에서 Android Enterprise 전용 디바이스 또는 완전 관리형 디바이스를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ad96c80a2cad71feec2afdfa87da767aa72fdb1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505618"
---
# <a name="enroll-your-android-enterprise-dedicated-devices-or-fully-managed-devices"></a>Android Enterprise 전용 디바이스 또는 완전 관리형 디바이스 등록

Intune에서 [Android Enterprise 전용 디바이스](android-kiosk-enroll.md) 또는 [완전 관리형 디바이스](android-fully-managed-enroll.md)를 설정한 후에 디바이스를 등록할 수 있습니다. 전용 디바이스와 완전 관리형 디바이스 모두에 대한 Intune 등록은 초기화로 시작됩니다. Android Enterprise 디바이스를 등록하는 방법은 운영 체제에 따라 다릅니다.

| 등록 메서드 | 전용 및 완전 관리형 디바이스에 대한 최소 Android OS 버전 |
| ----- | ----- |
| 근거리 통신 | 5.1 |
| 토큰 항목 | 6.0 |
| QR 코드 | 7.0 |
| Zero Touch  | 8.0\* |

\* 참여하는 제조업체.

## <a name="enroll-by-using-near-field-communication-nfc"></a>NFC(근거리 통신)를 사용하여 등록

NFC를 지원하는 디바이스의 경우 특별한 형식의 NFC 태그를 만들어 디바이스를 프로비저닝할 수 있습니다. 사용자 고유의 앱이나 NFC 태그 작성 도구를 사용할 수 있습니다. 자세한 내용은 [Microsoft Intune을 사용한 C 기반 Android 엔터프라이즈 디바이스 등록](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/) 및 [Google의 Android 관리 API 설명서](https://developers.google.com/android/management/provision-device#nfc_method)를 참조하세요.

## <a name="enroll-by-using-a-token"></a>토큰을 사용하여 등록

Android 6 이상 디바이스의 경우 토큰을 사용하여 디바이스를 등록할 수 있습니다. **afw#setup** 등록 메서드를 사용하는 경우 Android 6.1 이상 버전에서는 QR 코드 검사를 활용할 수도 있습니다.

1. 초기화된 디바이스를 켭니다.
2. **시작** 화면에서 언어를 선택합니다.
3. **Wifi**에 연결한 후, **다음**을 선택합니다.
4. Google 사용 약관에 동의한 후, **다음**을 선택합니다.
5. Google 로그인 화면에서 Gmail 계정 대신 **afw#setup**을 입력한 후, **다음**을 선택합니다.
6. **Android 디바이스 정책** 앱에 대해 **설치**를 선택합니다.
7. 이 정책의 설치를 계속합니다.  일부 디바이스에는 추가 사용 약관 동의가 필요할 수 있습니다.
8. **이 디바이스 등록** 화면에서 디바이스가 QR 코드를 스캔하거나 토큰을 수동으로 입력할 수 있도록 허용합니다.
9. 화면의 프롬프트에 따라 등록을 완료합니다.

## <a name="enroll-by-using-a-qr-code"></a>QR 코드를 사용하여 등록

Android 7 및 이상 디바이스에서는 등록 프로필에서 QR 코드를 스캔하여 디바이스를 등록할 수 있습니다.

> [!Note]
> 브라우저 확대/축소로 인해 디바이스가 QR 코드를 검사할 수 없게 될 수 있습니다. 브라우저를 더 확대/축소시키면 문제가 해결됩니다.

1. Android 디바이스에서 QR 읽기를 시작하려면 초기화 후 표시되는 첫 번째 화면을 여러 번 누릅니다.
2. Android 7 및 8 디바이스의 경우 QR reader를 설치하라는 메시지가 표시됩니다. Android 9 이상 디바이스에는 이미 QR reader가 설치되어 있습니다.
3. QR reader를 사용하여 등록 프로필 QR 코드를 스캔한 다음, 화면 프롬프트에 따라 등록합니다.

## <a name="enroll-by-using-google-zero-touch"></a>Google Zero Touch를 사용하여 등록

Google의 Zero Touch 시스템을 사용하려면 디바이스가 이를 지원해야 하며 서비스의 일부인 공급 업체와 제휴해야 합니다.  자세한 내용은 [Google Zero Touch 프로그램 웹 사이트](https://www.android.com/enterprise/management/zero-touch/)를 참조하세요.

1. Zero Touch 콘솔에서 새 구성을 만듭니다.
2. EMM DPC 드롭다운에서 **Microsoft Intune**을 선택합니다.
3. Google의 Zero Touch 콘솔에서 다음 JSON을 DPC 추가 필드에 복사/붙여넣기를 합니다. *YourEnrollmentToken* 문자열을 등록 프로필의 일부로 만든 등록 토큰으로 바꿉니다. 등록 토큰을 큰따옴표로 둘러싸십시오.

    ```json
    {
        "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver",

        "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg",

        "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup",

        "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": {
            "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken"
        }
    }
    ```

4. **적용**을 선택합니다.


## <a name="next-steps"></a>다음 단계
- [Android 앱 배포](../apps/apps-deploy.md)
- [Android 구성 정책 추가](../configuration/device-profiles.md)

