---
title: Microsoft Intune - Azure의 Windows Holographic for Business 장치에 대한 사용자 지정 설정 | Microsoft Docs
description: Microsoft Intune에서 Windows Holographic for Business를 실행하는 장치 OMA-URI 설정을 사용하려면 사용자 지정 프로필을 만듭니다. AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates 및 ApplicationLaunchRestrictions 정책 CSP(구성 서비스 공급자) 설정을 설정할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/26/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7272e8e088ae2c2ecad1756233281c42a80a279b
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "32328081"
---
# <a name="custom-device-settings-for-devices-running-windows-holographic-for-business-in-intune"></a>Intune에서 Windows Holographic for Business를 실행하는 장치에 사용자 지정 장치 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 장치의 기능을 제어하는 데 사용할 수 있는 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 설정을 배포하려면 Windows Holographic for Business용 Microsoft Intune **사용자 지정** 프로필을 사용합니다. Windows Holographic for Business는 많은 CSP(구성 서비스 공급자) 설정을 사용할 수 있게 합니다. CSP 개요는 [IT 전문가용 구성 CSP(구성 서비스 공급자) 소개](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)를 참조하세요. Windows Holographic에서 지원되는 특정 CSP의 경우 [Windows Holographic에서 지원되는 CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens)를 참조하세요.

특정 설정을 찾고 있는 경우 [Windows Holographic for Business 장치 제한 프로필](device-restrictions-windows-holographic.md)에 기본 제공 설정이 많기 때문에 사용자 지정 값을 지정할 필요가 없습니다.

## <a name="create-the-custom-oma-uri-profile"></a>사용자 지정 OMA-URI 프로필 만들기

1. [Microsoft Intune에서 사용자 지정 장치 설정 구성](custom-settings-configure.md)의 지침을 사용하여 시작합니다.
2. **프로필 만들기**에서 **설정**을 선택하여 하나 이상의 OMA-URI 설정을 추가합니다.
3. **사용자 지정 OMA-URI 설정**에서 **추가**를 클릭하여 새 값을 추가합니다. **내보내기**를 클릭하여 쉼표로 구분된 값(.csv) 파일로 구성한 모든 값의 목록을 만들 수도 있습니다.
4. 추가하려는 각 OMA-URI 설정에 대해 다음 정보를 입력합니다.
  - **설정 이름**: 설정 목록에서 쉽게 식별할 수 있도록 OMA-URI 설정에 대한 고유한 이름을 입력합니다.
  - **설정 설명**: 필요에 따라 설정에 대한 설명을 입력합니다.
  - **데이터 형식**: 다음 중에서 선택합니다.
    - **문자열**
    - **문자열(XML)**
    - **날짜 및 시간**
    - **정수**
    - **부동 소수점**
    - **부울**
  - **OMA-URI(대/소문자 구분)**: 설정을 제공할 OMA-URI를 입력합니다.
  - **값**: 입력한 OMA-URI와 연결할 값을 입력합니다.
5. 완료되면 **프로필 만들기**로 돌아와서 **만들기**를 클릭합니다. 프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="recommended-custom-settings"></a>권장되는 사용자 지정 설정

다음 설정은 Windows Holographic for Business를 실행하는 장치에 유용합니다.

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
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Integer<br/>0 – 구성되지 않음. 장치는 모든 적용 가능한 업데이트를 설치합니다.<br/>1 – 장치는 적용 가능한 업데이트뿐 아니라 승인된 업데이트 목록에 있는 업데이트도 설치합니다. 배포에 앞서 테스트가 필요한 경우처럼 장치에 업데이트의 배포를 IT로 제어하고자 하는 경우 이 정책을 1로 설정하십시오.|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|0=12AM 및 23=11PM인 경우 Integer는 0-23<br/>기본값은 3입니다.|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA URI|데이터 형식|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|문자열<br/>URL - 장치가 지정된 URL의 WSUS 서버에서 업데이트를 확인합니다.<br/>구성되지 않음 - 장치가 Microsoft Update에서 업데이트를 확인합니다.|

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
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|Integer<br/>0 - 장치가 현재 활성 사용자가 없는 상태로 돌아오는 경우 즉시 삭제<br/>1 - 저장소 용량 임계값(기본값)에서 삭제<br/>2 - 저장소 용량 임계값 및 프로필 비활성 임계값 모두에서 삭제|

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

[Windows Holographic에서 지원되는 CSP](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens)에서 Windows Holographic이 지원하는 모든 CSP(구성 서비스 공급자)의 전체 목록을 찾을 수 있습니다. 일부 Windows Holographic 버전과 호환되지 않는 설정도 있습니다. Windows 아티클의 표에서 각 CSP에 지원되는 버전을 알려줍니다.

또한, Intune은 아티클에 나열된 설정 모두를 지원하지 않습니다. 원하는 설정을 Intune에서 지원하는지 확인하려면 해당 설정에 대한 아티클을 엽니다. 각 설정 페이지에 지원되는 작업이 표시되어 있습니다. Intune으로 작업하려면 설정에서 **추가** 또는 **대체** 작업을 지원해야 합니다.
