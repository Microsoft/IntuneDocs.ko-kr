---
title: Intune에서 Android 엔터프라이즈 키오스크 장치 등록
titlesuffix: Microsoft Intune
description: Intune에서 Android 엔터프라이즈 키오스크 장치를 등록하는 방법에 대해 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5ea4d41477f2f0c6dc1314e47072d2c4cf862e23
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184831"
---
# <a name="set-up-enrollment-of-android-enterprise-kiosk-devices"></a>Android 엔터프라이즈 키오스크 장치 등록 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android는 회사 소유의 일회용 솔루션 집합을 통해 키오스크 스타일의 장치를 지원합니다. 이러한 장치는 몇 가지 예로서 디지털 간판, 티켓 인쇄, 재고 관리와 같은 단일 용도로 사용됩니다. 관리자는 제한된 앱 및 웹 링크 집합에 대한 장치 사용을 잠급니다. 또한 사용자가 다른 앱을 추가하거나 장치에서 다른 작업을 수행하는 것을 방지합니다.

Intune을 통해 Android 키오스크 장치에 앱 및 설정을 배포할 수 있습니다. Android 엔터프라이즈에 대한 특정 세부 정보는 [Android 엔터프라이즈 요구 사항](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)을 참조하세요.

이러한 방식으로 관리하는 장치는 사용자 계정 없이 Intune에 등록되며 어떠한 최종 사용자와도 연결되지 않습니다. 개인용 응용 프로그램이나 Outlook 또는 Gmail과 같은 사용자별 계정 데이터에 대한 강력한 요구 사항이 있는 앱을 대상으로 만들어진 것은 아닙니다.

## <a name="device-requirements"></a>장치 요구 사항

Android 엔터프라이즈 키오스크 장치로 관리하려면 장치가 다음 요구 사항을 충족해야 합니다.

- Android OS 버전 5.1 이상.
- 장치는 GMS(Google 모바일 서비스) 연결성을 갖춘 Android의 배포를 실행해야 합니다. 장치는 GMS를 사용할 수 있어야 하며 GMS에 연결할 수 있어야 합니다.

## <a name="set-up-android-kiosk-management"></a>Android 키오스크 관리 설정

Android 키오스크 관리를 설정하려면 다음 단계를 따릅니다.

1. 모바일 장치 관리를 준비하려면 지침에 따라 [MDM(모바일 장치 관리) 기관을 **Microsoft Intune**](mdm-authority-set.md)으로 설정해야 합니다. 이 항목은 모바일 장치 관리에 대해 Intune을 처음 설정할 때 한 번만 설정하면 됩니다.
2. [Intune 테넌트 계정을 Android 엔터프라이즈 계정에 연결합니다](connect-intune-android-enterprise.md).
3. [등록 프로필을 만듭니다.](#create-an-enrollment-profile)
4. [장치 그룹을 만듭니다](#create-a-device-group).
5. [키오스크 장치를 등록합니다](#enroll-the-kiosk-devices).

### <a name="create-an-enrollment-profile"></a>등록 프로필 만들기

키오스크 장치를 등록할 수 있도록 등록 프로필을 만들어야 합니다. 프로필이 만들어지면 등록 토큰(임의 문자열) 및 QR 코드를 제공합니다. Android OS 및 장치 버전에 따라 토큰 또는 QR 코드를 사용하여 [키오스크 장치를 등록](#enroll-the-kiosk-devices)할 수 있습니다.

1. [Intune 포털](https://portal.azure.com)로 이동하여 **장치 등록** > **Android 등록** > **키오스크 및 작업 장치 등록**을 선택합니다.
2. **만들기**를 선택하고 필수 필드를 작성합니다.
    - **이름**: 프로필을 동적 장치 그룹에 할당할 때 사용할 이름을 입력합니다.
    - **토큰 만료 날짜**: 토큰이 만료되는 날짜입니다. Google은 최대 90일을 적용합니다.
3. **만들기**를 선택하여 프로필을 저장합니다.

### <a name="create-a-device-group"></a>장치 그룹 만들기

앱 및 정책의 대상을 할당된 장치 그룹이나 동적 장치 그룹으로 지정할 수 있습니다. 다음 단계에 따라 특정 등록 프로필에 등록된 장치를 자동으로 채우도록 동적 AAD 장치 그룹을 구성할 수 있습니다.

1. [Intune 포털](https://portal.azure.com)로 이동하여 **그룹** > **모든 그룹** > **새 그룹**을 선택합니다.
2. **그룹** 블레이드에서 다음과 같은 필수 필드를 입력합니다.
    - **그룹 유형**: 보안
    - **그룹 이름**: 직관적인 이름(예: 팩터리 1 장치)
    - **멤버 자격 유형**: 동적 장치
3. **동적 쿼리 추가**를 선택합니다.
4. **동적 멤버 관리 규칙** 블레이드에서 다음과 같은 필드를 입력합니다.
    - **동적 멤버 관리 규칙 추가**: 단순 규칙
    - **다음 위치에 장치 추가**: enrollmentProfileName
    - 가운데 상자에서 **일치**를 선택합니다.
    - 마지막 필드에 이전에 만든 등록 프로필 이름을 입력합니다.
    동적 멤버 관리 규칙에 대한 자세한 내용은 [AAD에서 그룹에 대한 동적 멤버 관리 규칙](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)을 참조하세요. 
5. **쿼리 추가** > **만들기**를 선택합니다.

### <a name="replace-or-remove-tokens"></a>토큰 교체 또는 제거

토큰 및 QR 코드를 교체하거나 제거할 수 있습니다.

- **토큰 바꾸기**: 토큰 바꾸기를 사용하여 만료일이 임박했을 때 새 토큰/QR 코드를 생성할 수 있습니다.
- **토큰 해지**: 토큰/QR 코드를 즉시 만료시킬 수 있습니다. 이 시점부터 토큰/QR 코드를 더 이상 사용할 수 없습니다. 다음과 같은 경우 이 옵션을 사용할 수 있습니다.
    - 토큰/QR 코드를 권한이 없는 사람과 실수로 공유
    - 모든 등록을 완료하고 더 이상 토큰/QR 코드가 필요하지 않음

토큰/QR 코드를 교체하거나 취소해도 이미 등록된 장치에는 영향을 주지 않습니다.

1. [Intune 포털](https://portal.azure.com)로 이동하여 **장치 등록** > **Android 등록** > **키오스크 및 작업 장치 등록**을 선택합니다.
2. 사용하려는 프로필을 선택합니다.
3. **토큰**을 선택합니다.
4. 토큰을 바꾸려면 **토큰 바꾸기**를 선택합니다.
5. 토큰을 해지하려면 **토큰 해지**를 선택합니다.

## <a name="enroll-the-kiosk-devices"></a>키오스크 장치 등록

등록 프로필 및 동적 장치 그룹을 만든 후 키오스크 장치를 등록할 수 있습니다. Android 장치를 등록하는 방법은 운영 체제에 따라 다릅니다.

| 등록 메서드 | 지원되는 최소 Android OS 버전 |
| ----- | ----- |
| 근거리 통신 | 5.1 |
| 토큰 항목 | 6.0 |
| QR 코드 | 7.0 |
| Zero Touch | 8.0, 참여하는 제조업체 |

### <a name="enroll-by-using-near-field-communication-nfc"></a>NFC(근거리 통신)를 사용하여 등록

NFC를 지원하는 Android 5.1 이상 장치의 경우 특별한 형식의 NFC 태그를 만들어 장치를 제공할 수 있습니다. 사용자 고유의 앱이나 NFC 태그 작성 도구를 사용할 수 있습니다. 자세한 내용은 [Google의 Android Management API 설명서](https://developers.google.com/android/management/provision-device#nfc_method)를 참조하세요.

### <a name="enroll-by-using-a-token"></a>토큰을 사용하여 등록

Android 6 이상 장치의 경우 토큰을 사용하여 장치를 등록할 수 있습니다. **aft#setup** 등록 메서드를 사용하는 경우 Android 6.1 이상 버전에서는 QR 코드 검사를 활용할 수도 있습니다.

1. 초기화된 장치를 켭니다.
2. **시작** 화면에서 언어를 선택합니다.
3. **Wifi**에 연결한 후, **다음**을 선택합니다.
4. Google 사용 약관에 동의한 후, **다음**을 선택합니다.
5. Google 로그인 화면에서 Gmail 계정 대신 **afw#setup**을 입력한 후, **다음**을 선택합니다.
6. **Android 장치 정책** 앱에 대해 **설치**를 선택합니다.
7. 이 정책의 설치를 계속합니다.  일부 장치에는 추가 사용 약관 동의가 필요할 수 있습니다. 
8. **이 장치 등록** 화면에서 장치가 QR 코드를 스캔하거나 토큰을 수동으로 입력할 수 있도록 허용합니다.
9. 화면의 프롬프트에 따라 등록을 완료합니다. 

### <a name="enroll-by-using-a-qr-code"></a>QR 코드를 사용하여 등록

Android 7 및 이상 장치에서는 등록 프로필에서 QR 코드를 스캔하여 장치를 등록할 수 있습니다.

> [!Note]
> 브라우저 확대/축소로 인해 장치가 QR 코드를 검사할 수 없게 될 수 있습니다. 브라우저를 더 확대/축소시키면 문제가 해결됩니다.

1. Android 장치에서 QR 읽기를 시작하려면 초기화 후 표시되는 첫 번째 화면을 여러 번 누릅니다.
2. Android 7 및 8 장치의 경우 QR reader를 설치하라는 메시지가 표시됩니다. Android 9 이상 장치에는 이미 QR reader가 설치되어 있습니다.
3. QR reader를 사용하여 등록 프로필 QR 코드를 스캔한 다음, 화면 프롬프트에 따라 등록합니다.

### <a name="enroll-by-using-google-zero-touch"></a>Google Zero Touch를 사용하여 등록

Google의 Zero Touch 시스템을 사용하려면 장치가 이를 지원해야 하며 서비스의 일부인 공급 업체와 제휴해야 합니다.  자세한 내용은 [Google Zero Touch 프로그램 웹 사이트](https://www.android.com/enterprise/management/zero-touch/)를 참조하세요. 


1. Zero Touch 콘솔에서 새 구성을 만듭니다.
2. EMM DPC 드롭다운에서 **Microsoft Intune**을 선택합니다.
3. Google의 Zero Touch 콘솔에서 다음 JSON을 DPC 추가 필드에 복사/붙여넣기를 합니다. *YourEnrollmentToken* 문자열을 등록 프로필의 일부로 만든 등록 토큰으로 바꿉니다. 등록 토큰을 큰따옴표로 둘러싸십시오.

```
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

## <a name="managing-apps-on-android-kiosk-devices"></a>Android 키오스크 장치에서 앱 관리

할당 유형이 [필수로 설정](apps-deploy.md#to-assign-an-app)된 앱만 Android 키오스크 장치에 설치할 수 있습니다. 앱은 Android 회사 프로필 장치와 동일한 방식으로 관리되는 Google Play 스토어에서 설치됩니다.

앱 개발자가 Google Play에 대한 업데이트를 게시하면 관리되는 장치에서 앱이 자동으로 업데이트됩니다.

Android 키오스크 장치에서 앱을 제거하려면 다음 중 하나를 수행합니다.
-   필수 앱 배포를 삭제합니다.
-   앱에 대한 제거 배포를 만듭니다.


## <a name="next-steps"></a>다음 단계
- [Android 키오스크 앱 배포](apps-deploy.md)
- [Android 키오스크 구성 정책 추가](device-profiles.md)
