---
title: 사용자 지정 설정 - Windows Holographic for Business 디바이스 - Microsoft Intune
description: Microsoft Hololens를 비롯하여 Microsoft Intune에서 Windows Holographic for Business를 실행하는 디바이스의 OMA-URI 설정을 사용하려면 사용자 지정 프로필을 추가하거나 만듭니다. AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates 및 ApplicationLaunchRestrictions 정책 CSP(구성 서비스 공급자) 설정을 설정할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.article: article
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.topic: reference
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8512f8270e7f219814aa5e3919f72b95de93cbcf
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048463"
---
# <a name="use-custom-settings-for-windows-holographic-for-business-devices-in-intune"></a>Intune에서 Windows Holographic for Business 디바이스에 대한 사용자 지정 설정 사용

Microsoft Intune을 사용하면 "사용자 지정 프로필"을 사용하여 Windows Holographic for Business 디바이스에 대한 사용자 지정 설정을 추가하거나 만들 수 있습니다. 사용자 지정 프로필은 Intune의 기능입니다. Intune에 기본 제공되지 않은 디바이스 설정 및 기능을 추가하도록 설계되었습니다.

Windows Holographic for Business 사용자 지정 프로필은 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 사용하여 다른 기능을 구성합니다. 이러한 설정은 일반적으로 모바일 디바이스 제조업체에서 디바이스에서 기능을 제어하기 위해 사용합니다.

Windows Holographic for Business는 많은 CSP(구성 서비스 공급자) 설정을 사용할 수 있게 합니다. CSP 개요는 [IT 전문가용 구성 CSP(구성 서비스 공급자) 소개](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)를 참조하세요. Windows Holographic에서 지원되는 특정 CSP의 경우 [Windows Holographic에서 지원되는 CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens)를 참조하세요.

특정 설정을 찾을 경우 [Windows Holographic for Business 디바이스 제한 프로필](device-restrictions-windows-holographic.md)에 많은 기본 제공 설정이 있습니다. 따라서 사용자 지정 값을 입력할 필요가 없습니다.

이 문서는 Windows Holographic for Business 디바이스의 사용자 지정 프로필을 만드는 방법을 보여줍니다. 권장된 OMA-URI 설정 목록도 포함합니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: `hololens custom profile` 등의 프로필의 이름을 입력합니다.
    - **설명**: 설정에 대한 설명을 입력합니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택합니다.

4. **사용자 지정 OMA-URI 설정**에서 **추가**를 선택합니다. 다음 설정을 입력합니다.

    - **이름**: 설정 목록에서 쉽게 식별할 수 있도록 OMA-URI 설정에 대한 고유한 이름을 입력합니다.
    - **설명**: 설정에 대한 개요와 기타 중요한 모든 세부 정보를 제공하는 설명을 입력합니다.
    - **OMA-URI**(대/소문자 구분): 설정으로 사용할 OMA-URI를 입력합니다.
    - **데이터 형식**: 이 OMA URI 설정에 사용할 데이터 형식을 선택합니다. 옵션은 다음과 같습니다.

        - 문자열
        - 문자열(XML 파일)
        - 날짜 및 시간
        - 정수
        - 부동 소수점
        - 부울
        - Base64(파일)

    - **값**: 입력한 OMA-URI와 연결할 데이터를 입력합니다. 값은 선택한 데이터 형식에 따라 달라집니다. 예를 들어 **날짜 및 시간**을 선택한 경우 날짜 선택에서 값을 선택합니다.

    일부 설정을 추가한 후 **내보내기**를 선택할 수 있습니다. **내보내기**는 쉼표로 구분된 값(.csv) 파일에서 추가한 모든 값의 목록을 만듭니다.

5. **확인**을 선택하여 변경 내용을 저장합니다. 필요에 따라 더 많은 설정을 계속 추가합니다.
6. 끝나면 **확인** > **만들기**를 선택하여 Intune 프로필을 만듭니다. 완료되면 프로필이 **디바이스 구성 - 프로필** 목록에 나타납니다.

## <a name="recommended-custom-settings"></a>권장되는 사용자 지정 설정

다음 설정은 Windows Holographic for Business를 실행하는 디바이스에 유용합니다.

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Integer<br/>0 – 허용되지 않음<br/>1 - 허용됨(기본값)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Integer<br/>0 - 업데이트 서비스가 허용되지 않습니다 <br/>1 - 업데이트 서비스가 허용됨(기본값).|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Integer<br/>0 – 허용되지 않음<br/>1 - 허용됨(기본값)|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Integer<br/>0 – 구성되지 않음. 디바이스는 모든 적용 가능한 업데이트를 설치합니다.<br/>1 – 디바이스는 적용 가능한 업데이트뿐 아니라 승인된 업데이트 목록에 있는 업데이트도 설치합니다. 배포에 앞서 테스트가 필요한 경우처럼 디바이스에 업데이트의 배포를 IT로 제어하고자 하는 경우 이 정책을 1로 설정하십시오.|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|0=12AM 및 23=11PM인 경우 Integer는 0-23<br/>기본값은 3입니다.|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|문자열<br/>URL - 디바이스가 지정된 URL의 WSUS 서버에서 업데이트를 확인합니다.<br/>구성되지 않음 - 디바이스가 Microsoft Update에서 업데이트를 확인합니다.|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |---|---|
> |./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br/><br/>**중요**<br/>최종 사용자를 대신하여 업데이트 EULA를 읽고 동의해야 합니다. 이렇게 하지 않으면 법률 또는 계약상 의무 위반입니다.|최종 사용자를 대신하여 EULA 동의 및 업데이트 승인 노드.<br/><br/>자세한 내용은 [업데이트 CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp)를 참조하세요.|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |----|---|
> |./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br/><br/>**중요**<br/>AppLocker CSP 아티클은 이스케이프된 XML 예제를 사용합니다. Intune 사용자 지정 프로필을 사용해 설정을 구성하려면 일반 XML을 사용해야 합니다.|문자열<br/>자세한 내용은 [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)를 참조하세요.|

### <a name="deletionpolicyhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[DeletionPolicy](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|Integer<br/>0 - 디바이스가 현재 활성 사용자가 없는 상태로 돌아오는 경우 즉시 삭제<br/>1 - 스토리지 용량 임계값(기본값)에서 삭제<br/>2 - 스토리지 용량 임계값 및 프로필 비활성 임계값 모두에서 삭제|

### <a name="enableprofilemanagerhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[EnableProfileManager](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager|부울<br/>True - 활성화<br/>False - 비활성화(기본값)|

### <a name="profileinactivitythresholdhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[ProfileInactivityThreshold](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold|Integer<br/>기본값은 30입니다.|


### <a name="storagecapacitystartdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStartDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion|Integer<br/>기본값은 25입니다.|

### <a name="storagecapacitystopdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStopDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion|Integer<br/>기본값은 50입니다.|

## <a name="find-the-policies-you-can-configure"></a>구성할 수 있는 정책 찾기

[Windows Holographic에서 지원되는 CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens)에서 Windows Holographic이 지원하는 모든 CSP(구성 서비스 공급자)의 전체 목록을 찾을 수 있습니다. 일부 Windows Holographic 버전과 호환되지 않는 설정도 있습니다. [Windows Holographic에서 지원되는 CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens)의 표에는 각 CSP에 지원되는 버전을 나열합니다.

또한, Intune은 [Windows Holographic에서 지원되는 CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens)에 나열된 설정 모두를 지원하지 않습니다. 원하는 설정을 Intune에서 지원하는지 확인하려면 해당 설정에 대한 아티클을 엽니다. 각 설정 페이지는 지원되는 작업이 표시됩니다. Intune으로 작업하려면 설정에서 **추가** 또는 **대체** 작업을 지원해야 합니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 그런 다음, [프로필을 할당합니다](device-profile-assign.md).

[Windows 10 디바이스](custom-settings-windows-10.md)에 대한 사용자 지정 프로필을 만드는 방법을 참조하세요.
