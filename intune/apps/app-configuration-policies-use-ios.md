---
title: 관리되는 iOS 디바이스용 앱 구성 정책 추가
titleSuffix: Microsoft Intune
description: 앱 구성 정책을 사용하여 iOS 앱을 실행할 때 이 앱에 구성 데이터를 제공하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ee3ecd64254c0e212ffc86155d677bf18ba647a
ms.sourcegitcommit: f6b82c62af81a2643a1aaec774afa42d02eef352
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566175"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>관리되는 iOS 디바이스용 앱 구성 정책 추가

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune에서 앱 구성 정책을 사용하여 iOS 앱에 대한 사용자 지정 구성 설정을 제공합니다. 이러한 구성 설정을 사용하면 앱 공급자 방향에 따라 앱을 사용자 지정할 수 있습니다. 앱의 공급자로부터 이러한 구성 설정(키 및 값)을 가져와야 합니다. 앱을 구성하려면 설정을 키와 값으로 지정하거나 키와 값이 포함된 XML로 지정합니다.

Microsoft Intune 관리자는 관리되는 디바이스에서 Microsoft Office 애플리케이션에 추가할 사용자 계정을 제어할 수 있습니다. 허용되는 조직 사용자 계정만 액세스하도록 제한하고 등록된 디바이스에서 개인 계정을 차단할 수 있습니다. 지원 애플리케이션이 앱 구성을 처리하고 승인되지 않은 계정을 제거 및 차단합니다. 구성 정책 설정은 앱에서 해당 설정을 확인할 때(일반적으로는 앱을 처음 실행할 때) 사용됩니다.

앱 구성 정책을 추가하면 앱 구성 정책에 대한 할당을 설정할 수 있습니다. 정책에 대한 할당을 설정할 때 정책이 적용될 사용자 그룹을 포함할지 제외할지 선택할 수 있습니다. 하나 이상의 그룹을 포함하도록 선택하면 기본 제공 그룹을 포함하거나 선택하기 위해 특정 그룹을 선택할 수 있습니다. 기본 제공 그룹에는 **모든 사용자**, **모든 디바이스** 및 **모든 사용자 + 모든 디바이스**가 포함됩니다. 

> [!NOTE]
> Intune은 편의를 위해 콘솔에서 미리 만든 **모든 사용자** 및 **모든 디바이스** 그룹에 기본 최적화 기능을 제공합니다. 이들 그룹을 사용하여 직접 만든 '모든 사용자' 또는 '모든 디바이스' 그룹 대신 모든 사용자와 모든 디바이스를 지정하는 것이 좋습니다.

애플리케이션 구성 정책에 대해 포함된 그룹을 선택하면 제외할 특정 그룹을 선택할 수도 있습니다. 자세한 내용은 [Microsoft Intune에서 앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요.

> [!TIP]
> 이 정책 유형은 현재 iOS 8.0 이상을 실행하는 디바이스에서만 사용 가능합니다. 지원하는 앱 설치 유형은 다음과 같습니다.
>
> - **앱 스토어의 관리되는 iOS 앱**
> - **iOS용 앱 패키지**
>
> 앱 설치 유형에 대한 자세한 내용은 [Microsoft Intune에 앱을 추가하는 방법](apps-add.md)을 참조하세요. 관리되는 장치의 .ipa 앱 패키지로 앱 구성을 통합하는 방법에 대한 자세한 내용은 [iOS 개발자 설명서](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html)의 관리되는 앱 구성을 참조하세요.

## <a name="create-an-app-configuration-policy"></a>앱 구성 정책 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **클라이언트 앱** 워크로드를 선택합니다.
4. **관리** 그룹에서 **앱 구성 정책**을 선택한 다음 **추가**를 선택합니다.
5. 다음 세부 정보를 설정합니다.
    - **이름** - Azure Portal에 표시되는 프로필의 이름입니다.
    - **설명** - Azure Portal에 표시되는 프로필의 설명입니다.
    - **디바이스 등록 유형** - Intune에 등록된 디바이스에 대해 **관리 디바이스**를 선택합니다.
6. **플랫폼**으로 **iOS**를 선택합니다.
7. **연결된 앱**을 선택합니다. 그런 다음, **연결된 앱** 창에서 구성을 적용할 관리되는 앱을 선택하고 **확인**을 선택합니다.
8. **구성 정책 추가** 창서 **구성 설정**을 선택합니다.
9. **구성 설정 형식**을 선택합니다. 다음 방법 중 하나를 선택하여 구성 정보를 추가합니다.
    - **구성 디자이너 사용**
    - **XML 데이터 입력**<br><br>
    구성 디자이너 사용에 대한 자세한 내용은 [구성 디자이너 사용](#use-configuration-designer)을 참조하세요. XML 데이터 입력에 대한 자세한 내용은 [XML 데이터 입력](#enter-xml-data)을 참조하세요. 
10. 구성 정보를 추가했으면 **확인**을 선택한 다음, **추가**를 선택하여 구성 정책을 추가합니다. 구성 정책에 대한 개요 창이 표시됩니다.
11. **할당**을 선택하여 포함 및 제외 옵션을 표시합니다. 

    ![정책 할당 포함 탭의 스크린샷](./media/app-configuration-policies-use-ios/app-config-policy01.png)
12. **포함** 탭에서 **모든 사용자**를 선택합니다.

    ![정책 할당의 스크린샷 - 모든 사용자 드롭다운 옵션](./media/app-configuration-policies-use-ios/app-config-policy02.png)
13. **제외** 탭을 선택합니다. 
14. **제외할 그룹 선택**을 클릭하여 관련 창을 표시합니다.

    ![정책 할당의 스크린샷 - 제외할 그룹 블레이드 선택](./media/app-configuration-policies-use-ios/app-config-policy03.png)
15. 제외하려는 그룹을 클릭한 다음, **선택**을 클릭합니다.

    >[!NOTE]
    >그룹을 추가할 때 주어진 할당 유형에 이미 다른 그룹이 포함되어 있으면 다른 포함 할당 유형에 대해 사전 선택되며 변경할 수 없습니다. 따라서 사용된 해당 그룹은 제외된 그룹으로 사용할 수 없습니다.
16. **저장**을 클릭합니다.

## <a name="use-configuration-designer"></a>구성 디자이너 사용

Microsoft Intune은 앱에 고유한 구성 설정을 제공합니다. Microsoft Intune에 등록되었거나 등록되지 않은 디바이스에서 앱에 대한 구성 디자이너를 사용할 수 있습니다. 디자이너를 사용하면 기본 XML을 만드는 데 도움이 되는 특정 구성 키 및 값을 구성할 수 있습니다. 또한 각 값에 대한 데이터 형식을 지정해야 합니다. 이러한 설정은 앱을 설치하면 앱에 자동으로 제공됩니다.

### <a name="add-a-setting"></a>설정 추가

1. 구성의 각 키 및 값의 경우 다음을 설정합니다.
   - **구성 키** - 특정 설정 구성을 고유하게 식별하는 키입니다.
   - **값 형식** - 구성 값의 데이터 형식입니다. 형식에는 정수, 실수, 문자열 또는 부울이 포함됩니다.
   - **구성 값** - 구성의 값입니다.
2. **확인**을 선택하여 구성 설정을 설정합니다.

### <a name="delete-a-setting"></a>설정 삭제

1. 설정 옆의 줄임표( **...** )를 선택합니다.
2. **삭제**를 선택합니다.

\{\{ 및 \}\} 문자는 토큰 형식에만 사용되며 다른 용도로 사용하면 안 됩니다.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>다중 ID 앱에서 구성된 조직 계정만 허용 

iOS 디바이스의 경우 다음 키/값 쌍을 사용합니다.

| **Key** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **값** | <ul><li>**사용**: 유일하게 허용되는 계정은 [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm) 키로 정의된 관리되는 사용자 계정입니다.</li><li>**사용 안 함**(또는 **사용**과 대소문자를 구분하지 않고 일치하는 모든 값): 모든 계정이 허용됩니다.</li></ul> |.

   > [!NOTE]
   > 다중 ID로 구성된 조직 계정만 허용하는 경우에는 iOS용 OneDrive 10.34 이상, iOS용 Outlook 2.99.0 이상 또는 iOS용 Edge 44.8.7 이상을 사용해야 하고 앱을 [Intune 앱 보호 정책](app-protection-policy.md)의 대상으로 지정해야 합니다.

## <a name="enter-xml-data"></a>XML 데이터 입력

Intune에 등록된 디바이스에 대한 앱 구성 설정이 포함된 XML 속성 목록을 입력하거나 붙여넣을 수 있습니다. XML 속성 목록의 형식은 구성하는 앱에 따라 달라집니다. 사용할 정확한 형식에 대한 자세한 내용은 앱 공급업체에 문의하세요.

Intune에서 XML 형식의 유효성을 검사합니다. 그러나 Intune은 해당 XML 속성 목록(PList)이 대상 앱에서 작동하는지는 확인하지 않습니다.

XML 속성 목록에 대한 자세한 내용을 보려면 다음을 수행합니다.

- iOS 개발자 라이브러리에서 [XML 속성 목록 이해](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)를 참조하세요.

### <a name="example-format-for-an-app-configuration-xml-file"></a>앱 구성 XML 파일의 형식 예

앱 구성 파일을 만들 때 이 형식을 사용하여 다음 값 중 하나 이상을 지정할 수 있습니다.

```xml
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
</dict>
```

### <a name="supported-xml-plist-data-types"></a>지원되는 XML PList 데이터 형식

Intune에서는 속성 목록의 다음 데이터 형식을 지원합니다.

- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; 또는 &lt;false /&gt;

### <a name="tokens-used-in-the-property-list"></a>속성 목록에 사용되는 토큰

또한 Intune은 속성 목록에서 다음과 같은 토큰 형식을 지원합니다.
- \{\{userprincipalname\}\} - 예: **John\@contoso.com**
- \{\{mail\}\} - 예: **John\@contoso.com**
- \{\{partialupn\}\}—예: **John**
- \{\{accountid\}\}—예: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\}—예: **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\}—예: **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\}—예: **John Doe**
- \{\{serialnumber\}\}—예: **F4KN99ZUG5V2**(iOS 디바이스)
- \{\{serialnumberlast4digits\}\}—예: **G5V2**(iOS 디바이스)
- \{\{aaddeviceid\}\}-예: **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="configure-the-company-portal-app-to-support-ios-dep-devices"></a>iOS DEP 디바이스를 지원하도록 회사 포털 앱 구성

DEP(Apple의 장비 등록 프로그램) 등록은 회사 포털 앱의 앱 스토어 버전과 호환되지 않습니다. 그러나 다음 단계를 사용하여 iOS DEP 디바이스를 지원하도록 회사 포털 앱을 구성할 수 있습니다.

1. Azure Portal의 Intune에서 다음을 수행합니다.
    - 필요한 경우 **Intune** > **클라이언트 앱** > **앱** > **추가**로 이동하여 Intune 회사 포털을 추가합니다.
    - **클라이언트 앱** > **앱 구성 정책**으로 이동하여 회사 포털 앱에 대한 앱 구성 정책을 만듭니다.
2. 아래 XML을 사용하여 앱 구성 정책을 만듭니다. 앱 구성 정책을 만들고 XML 데이터를 입력하는 방법에 대한 자세한 내용은 [관리되는 iOS 디바이스에 대한 앱 구성 정책 추가](app-configuration-policies-use-ios.md)에서 또는 하이브리드 MDM의 경우 [System Center Configuration Manager에서 앱 구성 정책을 사용하여 iOS 앱에 설정 적용](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-ios-apps-with-app-configuration-policies)에서 확인할 수 있습니다.

    ``` xml
    <dict>
        <key>IntuneCompanyPortalEnrollmentAfterUDA</key>
        <dict>
            <key>IntuneDeviceId</key>
            <string>{{deviceid}}</string>
            <key>UserId</key>
            <string>{{userid}}</string>
        </dict>
    </dict>
    ```

3. 원하는 그룹을 대상으로 하는 앱 구성 정책을 사용하여 디바이스에 회사 포털을 배포합니다. 이미 DEP가 등록된 디바이스 그룹에만 정책을 배포해야 합니다.
4. 최종 사용자에게 회사 포털 앱이 자동으로 설치되면 로그인하도록 알립니다.

## <a name="monitor-ios--app-configuration-status-per-device"></a>디바이스별 iOS 앱 구성 상태 모니터링 
구성 정책이 할당되면 각 관리 디바이스에 대한 iOS 앱 구성 상태를 모니터링할 수 있습니다. Azure Portal의 **Microsoft Intune**에서 **디바이스** > **모든 디바이스**를 차례로 선택합니다. 관리 디바이스 목록에서 디바이스에 대한 블레이드를 표시할 특정 디바이스를 선택합니다. 디바이스 블레이드에서 **앱 구성**을 선택합니다.  

## <a name="additional-information"></a>추가 정보

- [iOS 및 Android용 Outlook 앱 구성 설정 배포](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>다음 단계

앱을 계속 [할당](apps-deploy.md) 및 [모니터링](apps-monitor.md)합니다.
