---
title: Microsoft Intune에서 관리 템플릿을 사용하여 Office 365 업데이트 - Azure | Microsoft Docs
description: Microsoft Intune의 관리 템플릿을 사용하여 Office 365 앱을 최신 버전으로 업데이트하고 Office에서 업데이트를 확인하는 빈도를 선택합니다. Office 업데이트에 대한 Intune 정책이 적용될 때 업데이트되는 디바이스 레지스트리 키를 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63ebbc22c5452c99439d34813509b5652daef1f0
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548094"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>업데이트 채널 및 대상 버전 설정을 사용하여 Microsoft Intune 관리 템플릿으로 Office 365를 업데이트합니다.

Intune에서 [Windows 10 템플릿을 사용하여 그룹 정책 설정을 구성](administrative-templates-windows.md)할 수 있습니다. 이 문서에서는 Intune에서 관리 템플릿을 사용하여 Office 365을 업데이트하는 방법을 보여 줍니다. 또한 정책이 성공적으로 적용되는지 확인하는 방법에 대한 지침도 제공합니다. 이 정보는 문제를 해결할 때도 유용합니다.

이 시나리오에서는 Intune에서 디바이스의 Office 365를 업데이트하는 관리 템플릿을 만듭니다.

관리 템플릿에 대한 자세한 내용은 [그룹 정책 설정을 구성하기 위한 Windows 10 템플릿](administrative-templates-windows.md)을 참조하세요.

적용 대상:

- Windows 10 이상
- Office 365

## <a name="prerequisites"></a>전제 조건

Office 앱에 대해 [Office365 ProPlus 자동 업데이트를 사용하도록 설정](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus)해야 합니다. 그룹 정책 또는 Intune Office 2016 ADMX 템플릿을 사용하여 이 작업을 수행할 수 있습니다.

![Intune 관리 템플릿에서 Office에 대한 자동 업데이트 사용 설정을 지정합니다.](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>Intune 관리 템플릿에서 업데이트 채널 설정

1. [Intune 관리 템플릿](administrative-templates-windows.md#create-a-template)에서 **채널 업데이트** 설정으로 이동한 후 원하는 채널을 입력합니다. 예를 들어 `Semi-Annual Channel`을 선택합니다.

    ![Intune 관리 템플릿에서 Office에 대한 업데이트 채널 설정을 지정합니다.](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > 좀 더 자주 업데이트하는 것이 좋습니다. 반기는 예제로만 사용됩니다.

2. [정책](device-profile-assign.md)을 Windows 10 디바이스에 할당해야 합니다. 정책을 더 빠르게 테스트하려면 다음과 같이 정책을 동기화할 수도 있습니다.

    - [Intune에서 정책 동기화](../remote-actions/device-sync.md)
    - [디바이스에서 정책 수동 동기화](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>Intune 레지스트리 키 확인

정책을 할당하고 디바이스를 동기화한 후에 정책이 적용되는지 확인할 수 있습니다.

1. 디바이스에서 **레지스트리 편집기** 앱을 엽니다.
2. Intune 정책 경로 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`로 이동합니다.

    > [!TIP]
    > 레지스트리 키의 `<Provider ID>`가 변경됩니다. 디바이스의 공급자 ID를 찾으려면 **레지스트리 편집기** 앱을 열고 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`로 이동합니다. 공급자 ID가 표시됩니다.

    정책이 적용되면 다음 레지스트리 키가 표시됩니다.

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    다음 예제를 살펴보면 `L_UpdateBranch`가 `<enabled /><data id="L_UpdateBranchID" value="Deferred" />`와 유사한 값을 갖는다는 것을 알 수 있습니다. 이 값은 반기 채널로 설정됨을 의미합니다.

    ![관리 템플릿 L_Updatebranch 레지스트리 키 예제](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > [Configuration Manager를 사용하여 Office 365 ProPlus 관리](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel)에 값과 의미가 나와 있습니다. 레지스트리 값은 선택된 배포 채널을 기준으로 합니다.
    >
    >- 월별 채널                - value="Current"
    >- 월별 채널(대상 지정)     - value="Current"
    >- 반기 채널            - value="Current"
    >- 반기 채널(대상 지정) - value="FirstReleaseDeferred"
    >- 초기 참가자                   - value="InsiderFast"

이때 Intune 정책이 디바이스에 성공적으로 적용됩니다.

## <a name="check-the-office-registry-keys"></a>Office 레지스트리 키 확인

1. 디바이스에서 **레지스트리 편집기** 앱을 엽니다.
2. Office 정책 경로 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`으로 이동합니다.

    다음 레지스트리 키를 확인합니다.

    - `UpdateChannel`: 구성된 설정에 따라 변경되는 동적 키입니다.
    - `CDNBaseUrl`: 디바이스에 Office 365를 설치할 때 설정합니다.

3. `UpdateChannel` 값을 확인하세요. 값은 Office가 업데이트되는 빈도를 알려 줍니다. [Configuration Manager를 사용하여 Office 365 ProPlus 관리](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel)에 값과 설정 값이 나와 있습니다.

    다음 예제를 살펴보면 `UpdateChannel`이 `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`(**월별**)으로 설정되어 있는 것을 알 수 있습니다.

    ![관리 템플릿 Office UpdateChannel 레지스트리 키 예제](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    이 예제에서는 **반기** 대신 **월별**로 설정되어 있으므로 정책이 아직 적용되지 않은 것을 의미합니다.

이 레지스트리 키는 **작업 스케줄러** > **Office 자동 업데이트 2.0**이 실행되거나 사용자가 디바이스에 로그인할 때 업데이트됩니다. 확인하려면 **Office 자동 업데이트 2.0** 작업 > **트리거**를 엽니다. 트리거에 따라 `UpdateChannel` 레지스트리 키를 업데이트하기 전에 적어도 하루 이상 걸릴 수 있습니다.

## <a name="force-office-automatic-updates-to-run"></a>강제로 Office 자동 업데이트 실행

정책을 테스트하려면 디바이스에서 강제로 정책 설정을 적용할 수 있습니다. 다음 단계에서는 레지스트리를 업데이트합니다. 레지스트리를 업데이트할 때는 항상 주의해야 합니다.

1. 다음과 같이 레지스트리 키를 지웁니다.

    1. `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates` 으로 이동합니다.
    2. `UpdateDetectionLastRunTime` 키를 두 번 선택하고 값 데이터를 삭제하고 **확인**을 선택합니다.

2. 다음과 같이 Office 자동 업데이트 작업을 실행합니다.

    1. 디바이스에서 **작업 스케줄러** 앱을 엽니다.
    2. **작업 스케줄러 라이브러리** > **Microsoft** > **Office**를 확장합니다.
    3. **Office 자동 업데이트 2.0** > **실행**을 선택합니다.

        ![작업 일정을 열고 Office 자동 업데이트를 실행합니다.](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        작업이 완료될 때까지 기다립니다. 몇 분 정도 걸릴 수 있습니다.

3. **레지스트리 편집기** 앱에서 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`으로 이동합니다. `UpdateChannel` 값을 확인합니다.

    정책에 설정된 값으로 업데이트되어야 합니다. 이 예제에서는 값을 `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`로 설정해야 합니다.

이때 디바이스에서 Office 업데이트 채널이 성공적으로 변경됩니다. 이 업데이트를 수신하는 사용자가 상태를 확인할 수 있도록 Office 365 앱을 열 수 있습니다.

## <a name="force-the-office-synchronization-to-update-account-information"></a>Office 동기화를 강제로 수행하여 계정 정보 업데이트  

더 많은 작업을 수행하려는 경우 강제로 Office에서 최신 버전 업데이트를 가져오도록 할 수 있습니다. 다음 단계는 확인이 필요하거나, 디바이스가 해당 채널에서 최신 버전 업데이트를 신속하게 가져오도록 하려는 경우에만 수행합니다. 그렇지 않으면 Office에서 해당 작업을 수행하고 자동으로 업데이트되도록 합니다.

### <a name="step-1-force-the-office-version-to-update"></a>1단계: 강제로 Office 버전 업데이트

1. Office 버전이 선택하는 업데이트 채널을 지원하는지 확인합니다. [Office 365 ProPlus의 업데이트 기록](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date)에는 다른 업데이트 채널을 지원하는 빌드 번호가 나열되어 있습니다.

2. [Intune 관리 템플릿](administrative-templates-windows.md#create-a-template)에서 **대상 버전** 설정으로 이동하고 원하는 버전을 입력합니다.

    **대상 버전** 설정은 다음 설정과 비슷합니다.

    ![Intune 관리 템플릿에서 Office에 대한 대상 버전 설정을 지정합니다.](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - 정책을 할당해야 합니다.
> - 기존 정책을 변경하는 경우 변경 내용이 할당된 모든 사용자에게 영향을 줍니다.
> - 이 기능을 테스트하는 경우 테스트 정책을 만들고 테스트 사용자 그룹에 정책을 할당하는 것이 좋습니다.

### <a name="step-2-check-the-office-version"></a>2단계: Office 버전 확인

모든 사용자에게 정책을 배포하기 다음 단계에 따라 정책을 테스트하는 것이 좋습니다.

1. **레지스트리 편집기** 앱에서 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`으로 이동합니다.

2. `L_UpdateTargetVersion` 값을 확인하세요. 정책이 적용되면 값은 사용자가 입력한 버전(예: `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`)으로 설정됩니다.

    이때 Intune 정책이 디바이스에 성공적으로 적용됩니다.

3. 다음으로, Office를 강제로 업데이트할 수 있습니다. Excel과 같은 Office 앱을 엽니다. 지금 업데이트를 선택합니다(**계정** 메뉴에 있을 수 있음).

    업데이트에는 몇 분 정도 걸립니다. Office에서 입력한 버전을 가져오려고 하는지 확인할 수 있습니다.

      1. 디바이스에서 `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`으로 이동합니다.
      2. `VersionDescriptor.xml` 파일을 열고 `<Version>` 섹션으로 이동합니다. 사용 가능한 버전은 다음과 같이 Intune 정책에 입력한 버전과 동일해야 합니다.

          ![버전 설명자 Office XML 파일에서 버전 섹션 확인](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. 업데이트가 설치된 후에는 Office 앱이 새 버전(예: **계정** 메뉴에 있음)를 표시해야 합니다.

## <a name="next-steps"></a>다음 단계

[Office 365 클라이언트의 업데이트 채널 값](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel)

[Office 365 ProPlus의 Office 클라우드 정책 서비스 개요](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[Windows 10 템플릿을 사용하여 Microsoft Intune에서 그룹 정책 설정(ADMX 템플릿) 구성](administrative-templates-windows.md)
