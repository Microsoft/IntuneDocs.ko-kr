---
title: Microsoft Intune용 앱 구성 정책
titleSuffix: ''
description: Microsoft Intune에서 iOS/iPadOS 또는 Android 디바이스에 앱 구성 정책을 사용하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2cf53b26c1617ca7fc493c837e57823c23781bc
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414848"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Microsoft Intune용 앱 구성 정책

앱 구성 정책을 사용하면 앱을 실행하기 전에 최종 사용자에게 할당된 정책에 구성 설정을 할당할 수 있으므로 앱 설정 문제를 방지할 수 있습니다. 그러면 최종 사용자 디바이스에서 앱이 구성될 때 설정이 자동으로 제공되므로 최종 사용자가 작업을 수행할 필요가 없습니다. 구성 설정은 각 앱에 대해 고유합니다. 

앱 구성 정책을 만들고 사용하여 iOS/iPadOS 또는 Android 앱용 구성 설정을 제공할 수 있습니다. 이러한 구성 설정을 사용하면 앱 구성 및 관리를 이용해 앱을 사용자 지정할 수 있습니다. 구성 정책 설정은 앱에서 이러한 설정을 확인할 때(일반적으로는 앱을 처음 실행할 때) 사용됩니다. 

예를 들어 앱 구성 설정에서 다음 세부 정보 중 하나를 지정해야 할 수도 있습니다.

- 사용자 지정 포트 번호
- 언어 설정
- 보안 설정
- 회사 로고와 같은 브랜딩 설정

최종 사용자가 이러한 설정을 대신 입력해야 한다면 이 작업을 제대로 수행할 수 없을 것입니다. 앱 구성 정책은 엔터프라이즈 전체에서 일관성을 제공하고 설정을 직접 구성하려고 하는 최종 사용자가 전화로 기술 지원 팀에 문의하는 횟수를 줄일 수 있도록 합니다. 앱 구성 정책을 사용하면 새 앱을 더 쉽고 빠르게 채택할 수 있습니다.

사용 가능한 구성 매개 변수는 궁극적으로 앱 개발자가 결정합니다. 애플리케이션 공급업체의 설명서를 검토하여 앱에서 구성을 지원하는지 여부와 사용할 수 있는 구성을 확인해야 합니다. 일부 애플리케이션의 경우 Intune에서 사용 가능한 구성 설정이 자동으로 입력됩니다. 

> [!NOTE]
> 관리형 Google Play 스토어에서 구성을 지원하는 앱은 다음과 같이 표시됩니다.
> 
> ![구성된 앱 스크린샷](./media/app-configuration-policies-overview/configured-app.png)
>
> 관리형 디바이스를 Enrollment Type for Android 디바이스로 사용할 경우 [Google Play 스토어](https://play.google.com/store/apps)가 아닌 [관리형 Google Play 스토어](https://play.google.com/work)의 앱만 표시됩니다. AfW(Android for Work) 및 Android Enterprise로도 알고 있을 수 있는 관리형 Google Play 스토어는 앱 구성을 지원하는 앱 버전을 포함하는 회사 프로필의 앱입니다.

[포함 및 제외 할당](apps-inc-exl-assignments.md)의 조합을 사용하여 최종 사용자 및 디바이스 그룹에 앱 구성 정책을 할당할 수 있습니다. 앱 구성 정책을 추가하면 앱 구성 정책에 대한 할당을 설정할 수 있습니다. 정책에 대한 할당을 설정할 때 정책이 적용될 최종 사용자 [그룹](../fundamentals/groups-add.md)을 포함할지 제외할지 선택할 수 있습니다. 하나 이상의 그룹을 포함하도록 선택하면 기본 제공 그룹을 포함하거나 선택하기 위해 특정 그룹을 선택할 수 있습니다. 기본 제공 그룹에는 **모든 사용자**, **모든 디바이스** 및 **모든 사용자 + 모든 디바이스**가 포함됩니다.

Intune에서 앱 구성 정책을 사용하는 두 가지 옵션이 있습니다.
- **관리 디바이스** - 디바이스는 MDM(모바일 디바이스 관리) 공급자로 Intune에서 관리됩니다. 앱 구성을 지원하도록 앱을 디자인해야 합니다.
- **관리형 앱** - Intune 앱 SDK를 통합하기 위해 개발된 앱입니다. 이러한 앱을 등록 없는 모바일 애플리케이션 관리([MAM-WE](app-management.md#mobile-application-management-mam-basics))라고 합니다. Intune 앱 SDK를 구현하고 지원하기 위해 앱을 래핑할 수도 있습니다. 앱을 래핑하는 방법에 대한 자세한 내용은 [앱 보호 정책에 대해 LOB(기간 업무) 앱 준비](../developer/apps-prepare-mobile-application-management.md)를 참조하세요.

    > [!NOTE]
    > Intune 관리형 앱은 Intune 앱 보호 정책과 함께 배포되는 경우 Intune 앱 구성 정책 상태를 30분 간격으로 체크 인합니다. Intune 앱 보호 정책이 사용자에게 할당되지 않은 경우 Intune 앱 구성 정책 체크 인 간격이 720분으로 설정됩니다.

## <a name="apps-that-support-app-configuration"></a>앱 구성을 지원하는 앱

### <a name="managed-devices"></a>관리되는 디바이스
앱 구성 정책을 지원하는 앱에서 해당 정책을 사용할 수 있습니다. Intune에서 앱 구성을 지원하려면 OS에 정의된 대로 앱 구성 사용을 지원하도록 앱을 작성해야 합니다. 지원되는 앱 구성 키에 대한 자세한 내용은 앱 공급업체에 문의하세요.

### <a name="managed-apps"></a>관리되는 앱
[Intune 앱 SDK](../developer/app-sdk.md)를 앱에 연결하거나 앱이 개발된 후 [Intune 앱 래핑 도구](../developer/apps-prepare-mobile-application-management.md)로 앱을 래핑하여 기간 업무 앱을 준비할 수 있습니다. Intune 앱 SDK는 앱 개발자에게 요구되는 코드 변경의 양을 최소화하기 위해 노력합니다. 자세한 내용은 [Intune 앱 SDK 개요](../developer/app-sdk.md)를 참조하세요. Intune 앱 SDK와 intune 앱 래핑 도구를 비교하려면 [앱 보호 정책에 대해 LOB(기간 업무) 앱 준비](../developer/apps-prepare-mobile-application-management.md#feature-comparison)를 참조하세요.

**관리형 앱**을 **디바이스 등록 유형**으로 선택하면 구체적으로 디바이스 관리에 등록되지 않은 디바이스에서 Intune 구성 정책으로 구성된 앱을 나타내지만, **관리형 디바이스**는 MDM 채널을 통해 배포되므로 Intune에서 관리되는 앱에 적용됩니다. 이러한 설명에 따라 적절한 선택 항목을 선택합니다. 

![디바이스 등록 유형](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> Microsoft Outlook과 같은 다중 ID 앱의 경우 사용자 기본 설정을 고려할 수 있습니다. 예를 들어, 중요 받은 편지함은 사용자 설정을 준수하며 구성은 변경하지 않습니다. 다른 매개 변수를 사용하여 사용자가 설정을 변경할 수 있는지 여부를 제어할 수 있습니다. 자세한 내용은 [iOS/iPadOS 및 Android용 Outlook 앱 구성 설정 배포](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)를 참조하세요.

## <a name="validate-the-applied-app-configuration-policy"></a>적용된 앱 구성 정책 유효성 검사

다음 세 가지 방법을 사용하여 앱 구성 정책의 유효성을 검사할 수 있습니다.

   1. 디바이스에 표시됩니다. 대상 앱이 앱 구성 정책에서 적용되는 동작을 표시하고 있나요?
   2. 진단 로그를 통해(아래의 진단 로그 섹션 참조)
   3. Intune 포털에서 정책의 **모니터링** 섹션은 관련 상태를 제공할 수 있습니다.

      ![디바이스 설치 상태의 첫 번째 스크린샷](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![디바이스 설치 상태의 두 번째 스크린샷](./media/app-configuration-policies-overview/device-install-status-2.png)

      또한 화면 왼쪽의 **Intune** -> **디바이스** -> **모든 디바이스**에서 **앱 구성** 옵션은 할당된 모든 정책 및 해당 상태를 표시합니다.

      ![앱 구성 스크린샷](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="diagnostic-logs"></a>진단 로그

### <a name="ios-configuration-on-unmanaged-devices"></a>관리되지 않는 디바이스에서 iOS 구성

관리 앱 구성에 대해 관리되지 않는 디바이스의 **Intune 진단 로그**를 사용하여 iOS/iPadOS 구성의 유효성을 검사할 수 있습니다. 아래 단계 외에도 Microsoft Edge를 사용하여 관리형 앱 로그에 액세스할 수 있습니다. 자세한 내용은 [iOS/iPadOS에서 Microsoft Edge를 사용하여 관리형 앱 로그에 액세스](~/apps/manage-microsoft-edge.md#use-microsoft-edge-on-ios-to-access-managed-app-logs)를 참조하세요.

1. **Microsoft Edge**가 디바이스에 아직 설치되지 않았다면 앱 스토어에서 다운로드하여 설치합니다. 자세한 내용은 [Microsoft Intune 보호 앱](apps-supported-intune-apps.md)을 참조하세요.
2. **Microsoft Edge**를 시작하고 탐색 모음에서 **정보** > **intunehelp**를 선택합니다.
3. **시작**을 클릭합니다.
4. **로그 공유**를 클릭합니다.
5. PC에서 볼 수 있도록 원하는 메일 앱을 사용하여 로그를 자신에게 보냅니다. 
6. 텍스트 파일 뷰어에서 **IntuneMAMDiagnostics.txt**를 검토합니다.
7. `ApplicationConfiguration`를 검색합니다. 결과는 다음과 같이 나타납니다.

    ``` JSON
        {
            (
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.BlockListURLs";
                    Value = "https://www.aol.com";
                },
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.bookmarks";
                    Value = "Outlook Web|https://outlook.office.com||Bing|https://www.bing.com";
                }
            );
        },
        {
            ApplicationConfiguration =             
            (
                {
                Name = IntuneMAMUPN;
                Value = "CMARScrubbedM:13c45c42712a47a1739577e5c92b5bc86c3b44fd9a27aeec3f32857f69ddef79cbb988a92f8241af6df8b3ced7d5ce06e2d23c33639ddc2ca8ad8d9947385f8a";
                },
                {
                Name = "com.microsoft.outlook.Mail.NotificationsEnabled";
                Value = false;
                }
            );
        }
    ```

애플리케이션 구성 세부 정보는 테넌트에 대해 구성된 애플리케이션 구성 정책과 일치해야 합니다. 

![대상 지정 앱 구성](./media/app-configuration-policies-overview/targeted-app-configuration-3.png)

### <a name="ios-configuration-on-managed-devices"></a>관리 디바이스에서 iOS 구성

관리 앱 구성에 대해 관리 디바이스의 **Intune 진단 로그**를 사용하여 iOS/iPadOS 구성의 유효성을 검사할 수 있습니다.

1. **Microsoft Edge**가 디바이스에 아직 설치되지 않았다면 앱 스토어에서 다운로드하여 설치합니다. 자세한 내용은 [Microsoft Intune 보호 앱](apps-supported-intune-apps.md)을 참조하세요.
2. **Microsoft Edge**를 시작하고 탐색 모음에서 **정보** > **intunehelp**를 선택합니다.
3. **시작**을 클릭합니다.
4. **로그 공유**를 클릭합니다.
5. PC에서 볼 수 있도록 원하는 메일 앱을 사용하여 로그를 자신에게 보냅니다. 
6. 텍스트 파일 뷰어에서 **IntuneMAMDiagnostics.txt**를 검토합니다.
7. `AppConfig`를 검색합니다. 결과는 테넌트에 대해 구성된 애플리케이션 구성 정책과 일치해야 합니다.

### <a name="android-configuration-on-managed-devices"></a>관리 디바이스에서 Android 구성

관리 앱 구성에 대해 관리 디바이스의 **Intune 진단 로그**를 사용하여 iOS/iPadOS 구성의 유효성을 검사할 수 있습니다.

Android 디바이스에서 로그를 수집하려면 사용자 또는 최종 사용자가 USB 연결(또는 디바이스에서 **파일 탐색기**에 해당하는 것)을 통해 디바이스에서 로그를 다운로드해야 합니다. 실행할 단계는 다음과 같습니다.

1. USB 케이블로 컴퓨터에 Android 디바이스를 연결합니다.
2. 컴퓨터에서 디바이스 이름을 가진 디렉터리를 찾습니다. 해당 디렉터리에서 `Android Device\Phone\Android\data\com.microsoft.windowsintune.companyportal`을 찾습니다.
3. `com.microsoft.windowsintune.companyportal` 폴더에서 파일 폴더를 열고 `OMADMLog_0`을 엽니다.
3. `AppConfigHelper`를 검색하여 앱 구성 관련 메시지를 찾습니다. 결과는 다음 데이터 블록과 비슷합니다.

    `2019-06-17T20:09:29.1970000       INFO   AppConfigHelper     10888  02256  Returning app config JSON [{"ApplicationConfiguration":[{"Name":"com.microsoft.intune.mam.managedbrowser.BlockListURLs","Value":"https:\/\/www.aol.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.bookmarks","Value":"Outlook Web|https:\/\/outlook.office.com||Bing|https:\/\/www.bing.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.homepage","Value":"https:\/\/www.arstechnica.com"}]},{"ApplicationConfiguration":[{"Name":"IntuneMAMUPN","Value":"AdeleV@M365x935807.OnMicrosoft.com"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled","Value":"false"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed","Value":"false"}]}] for user User-875363642`
    
## <a name="graph-api-support-for-app-configuration"></a>앱 구성에 대한 Graph API 지원

Graph API를 사용하여 앱 구성 작업을 수행할 수 있습니다. 자세한 내용은 [Graph API Reference MAM Targeted Config](https://docs.microsoft.com/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta)(Graph API 참조 MAM 대상 구성)를 참조하세요. Intune과 Graph에 대한 자세한 내용은 [Microsoft Graph에서 Intune 사용](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-beta)을 참조하세요.

## <a name="troubleshooting"></a>문제 해결

### <a name="using-logs-to-show-a-configuration-parameter"></a>로그를 사용하여 구성 매개 변수 표시
로그가 적용 중인 것으로 확인되었으나 작동하지 않는 것처럼 보이는 구성 매개 변수를 표시하는 경우 앱 개발자의 구성 구현에 문제가 있을 수 있습니다. 먼저 해당 앱 개발자에게 연락하거나 기술 자료를 확인하여 Microsoft로의 지원 통화를 줄일 수 있습니다. 앱 내에서 구성을 처리하는 방법에 문제가 있는 경우 해당 앱의 이후 업데이트 버전에서 해당 문제를 해결해야 할 수 있습니다.

## <a name="next-steps"></a>다음 단계

### <a name="managed-devices"></a>관리되는 디바이스

- iOS/iPadOS 디바이스로 앱 구성을 사용하는 방법을 알아봅니다.  [관리형 iOS/iPadOS 디바이스용 앱 구성 정책 추가](app-configuration-policies-use-ios.md)를 참조하세요.
- Android 디바이스로 앱 구성을 사용하는 방법을 알아봅니다.  [관리되는 Android 디바이스용 앱 구성 정책 추가](app-configuration-policies-use-android.md)를 참조하세요.

### <a name="managed-apps"></a>관리되는 앱

- 관리되는 앱으로 앱 구성을 사용하는 방법을 알아봅니다. [디바이스 등록 없이 관리되는 앱용 앱 구성 정책 추가](app-configuration-policies-managed-app.md)를 참조하세요.
