---
title: Microsoft Intune에서 Android Enterprise 디바이스에 OEMConfig 사용 - Azure | Microsoft Docs
description: Microsoft Intune을 사용하여 OEMConfig인 Android Enterprise를 실행하는 디바이스를 관리 및 사용합니다. 개요를 비롯한 모든 단계를 확인하고, 필수 조건을 확인하고, Intune에서 구성 프로필을 만들고, 지원되는 OEMConfig 앱 목록을 확인하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
ms.topic: conceptual
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
ms.openlocfilehash: 9cc568cbadb683f632ffd2365ab7023cd796f231
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886700"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Microsoft Intune에서 OEMConfig를 사용하여 Android Enterprise 디바이스 사용 및 관리

Microsoft Intune에서 OEMConfig를 사용하여 Android Enterprise 디바이스에 대한 OEM 관련 설정을 추가하고 만들고 사용자 지정할 수 있습니다. OEMConfig는 일반적으로 Intune에 기본 제공되지 않는 설정을 구성하는 데 사용됩니다. OEM(주문자 상표 부착 방식)마다 서로 다른 설정이 포함되어 있습니다. 사용할 수 있는 설정은 OEM이 OEMConfig 앱에 포함하는 항목에 따라 다릅니다.

이 기능은 다음에 적용됩니다.  

- Android Enterprise

이 문서에서는 OEMConfig에 대해 설명하고, 선제 조건을 나열하고, 구성 프로필을 만드는 방법을 설명하고, Intune에서 지원되는 OEMConfig 앱을 나열합니다.

## <a name="overview"></a>개요

OEMConfig 정책은 [앱 구성 정책](../apps/app-configuration-policies-overview.md)과 유사한 특수한 유형의 디바이스 구성 정책입니다. OEMConfig는 Google에서 정의한 표준으로, Android의 앱 구성을 사용하여 OEM(주문자 상표 부착 방식)에서 작성한 앱에 디바이스 설정을 보냅니다. 이 표준을 통해 OEM 및 EMM(엔터프라이즈 이동성 관리)에서는 표준화된 방법으로 OEM 관련 기능을 구축 및 지원할 수 있습니다. [OEMConfig에 대한 자세한 정보](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/)

지금까지 Intune과 같은 EMM은 OEM에 의해 도입된 이후 OEM 관련 기능에 대한 지원을 수동으로 구축합니다. 이 접근 방식을 사용하면 노력이 중복되고 채택이 지연됩니다.

OEM은 OEMConfig를 사용하여, OEM 전용 관리 기능을 정의하는 스키마를 만듭니다. OEM은 앱에 스키마를 포함한 다음 Google Play에 이 앱을 배치합니다. EMM은 앱에서 스키마를 읽고 EMM 관리자 콘솔에서 스키마를 노출합니다. 콘솔에서 Intune 관리자는 스키마의 설정을 구성할 수 있습니다.

OEMConfig 앱이 디바이스에 설치되면 EMM 관리자에 구성된 설정을 사용하여 디바이스를 관리합니다. 디바이스 설정은 EMM에서 구축된 MDM 에이전트 대신 OEMConfig 앱에서 실행됩니다.

OEM이 관리 기능을 추가하고 개선하면 Google Play에서도 앱을 업데이트합니다. 관리자는 EMM에서 이러한 업데이트를 포함하도록 기다리지 않고 새로운 기능 및 업데이트(수정 사항 포함)를 받게 됩니다.

> [!TIP]
> 이 기능을 지원하며 해당하는 OEMConfig 앱이 있는 디바이스에만 OEMConfig를 사용할 수 있습니다. 구체적인 세부 정보는 OEM에 문의하세요.

## <a name="before-you-begin"></a>시작하기 전에

OEMConfig를 사용할 때는 다음 정보를 알고 있어야 합니다.

- Intune은 구성 가능하도록 OEMConfig 앱의 스키마를 노출합니다. Intune은 앱에서 제공하는 스키마의 유효성을 검사하거나 스키마를 변경하지 않습니다. 따라서 스키마가 잘못되었거나 부정확한 데이터가 있는 경우에도 여전히 이 데이터가 디바이스에 전송됩니다. 스키마에서 발생하는 문제를 발견하면 OEM에게 지침을 문의하세요.
- Intune은 앱 스키마의 콘텐츠를 제어하거나 콘텐츠에 영향을 주지 않습니다. 예를 들어 Intune은 문자열, 언어, 허용되는 작업 등을 제어하지 않습니다. OEMConfig를 사용하여 디바이스를 관리하는 방법에 대한 자세한 내용은 OEM에 문의하는 것이 좋습니다.
- OEM은 지원되는 기능 및 스키마를 언제든지 업데이트하고 Google Play에 새 앱을 업로드할 수 있습니다. Intune은 항상 Google Play에서 최신 버전의 OEMConfig 앱을 동기화합니다. Intune은 이전 버전의 스키마 또는 앱을 유지 관리하지 않습니다. 버전 충돌이 발생한 경우 OEM에 자세한 내용을 문의하는 것이 좋습니다.
- 디바이스당 OEMConfig 프로필 하나를 할당합니다. 동일한 디바이스에 여러 프로필을 할당하는 경우 일관되지 않은 동작이 나타날 수 있습니다. OEMConfig 모델은 디바이스당 정책 하나만 지원합니다.

## <a name="prerequisites"></a>전제 조건

디바이스에서 OEMConfig를 사용하려면 다음 요구 사항을 충족해야 합니다.

- Android Enterprise 디바이스를 Intune에 등록합니다.
- OEM에서 OEMConfig 앱을 작성하여 Google Play에 업로드합니다. Google Play에 앱이 없는 경우 OEM에 자세한 내용을 문의하세요.
- Intune 관리자에게 **모바일 앱**, **디바이스 구성**에 대한 RBAC(역할 기반 액세스 제어) 권한 및 **Android for Work**에 의거한 "읽기" 권한이 있습니다. 이러한 권한은 OEMConfig 프로필에서 관리형 앱 구성을 사용하여 디바이스 구성을 관리하기 때문에 필요합니다.

## <a name="prepare-the-oemconfig-app"></a>OEMConfig 앱 준비

디바이스에서 OEMConfig를 지원하고, 올바른 OEMConfig 앱이 Intune에 추가되며, 앱이 디바이스에 설치되어 있어야 합니다. 이 정보는 OEM에 문의하세요.

> [!TIP] 
> OEMConfig 앱은 OEM에 특정합니다. 예를 들어 Zebra Technologies 디바이스에 설치된 Sony OEMConfig 앱은 어떤 작업도 하지 않습니다.

1. 관리형 Google Play 스토어에서 OEMConfig 앱을 다운로드합니다. [Android 엔터프라이즈 디바이스에 관리되는 Google Play 앱 추가](../apps/apps-add-android-for-work.md)에서는 단계가 나열됩니다.
2. 일부 OEM은 OEMConfig 앱이 미리 설치되어 있는 디바이스를 제공할 수 있습니다. 앱이 미리 설치되지 않은 경우에는 Intune을 사용하여 [앱을 추가하고 디바이스에 배포](../apps/apps-deploy.md)합니다.

## <a name="create-an-oemconfig-profile"></a>OEMConfig 프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **플랫폼**: **Android Enterprise**를 선택합니다.
    - **프로필 유형**: **OEMConfig**를 선택합니다.

4. **만들기**를 선택합니다.
5. **기본**에서 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **OEMConfig 앱**: **OEMConfig 앱 선택**을 선택합니다.

6. **연결된 앱**에서 이전에 추가한 기존 OEMConfig 앱을 선택한 후 **선택**합니다. 정책을 할당할 디바이스에 맞는 올바른 OEMConfig 앱을 선택해야 합니다.

    앱이 나열되지 않는 경우 관리형 Google Play를 설정하고 관리형 Google Play 스토어에서 앱을 가져옵니다. [Android Enterprise 디바이스에 관리형 Google Play 앱 추가](../apps/apps-add-android-for-work.md)에서 단계를 안내합니다.

    > [!IMPORTANT]
    > OEMConfig 앱을 추가하고 Google Play에 동기화했지만 이 앱이 **연결된 앱**으로 나열되지 않는 경우 앱을 등록하도록 Intune에 문의해야 할 수 있습니다. [새 앱 추가](#supported-oemconfig-apps)(이 문서)를 참조하세요.

7. **다음**을 선택합니다.
8. **설정 구성**에서 **구성 디자이너** 또는 **JSON 편집기**를 선택합니다.

    > [!TIP]
    > OEM 설명서를 읽고 속성을 올바르게 구성하고 있는지 확인합니다. 이러한 앱 속성은 Intune이 아니라 OEM에서 포함합니다. Intune은 속성에 대해 최소한으로 또는 입력한 대로 유효성 검사를 합니다. 예를 들어 포트 번호로 `abcd`를 입력하면 프로필은 그대로 저장되며 구성한 값으로 디바이스에 배포됩니다. 올바른 정보를 입력해야 합니다.

    - **구성 디자이너**:이 옵션을 선택하면 구성할 수 있도록 앱 스키마 내에서 사용할 수 있는 속성이 표시됩니다.

      - 구성 디자이너에 상황에 맞는 메뉴가 있는 경우 더 많은 옵션을 사용할 수 있음을 나타냅니다. 예를 들어 상황에 맞는 메뉴를 사용하여 설정을 추가, 삭제 및 다시 정렬할 수 있습니다. 이러한 옵션은 OEM에서 포함합니다. 프로필을 만들 때 이러한 옵션을 사용하는 방법을 알아보려면 OEM 앱 설명서를 참조하세요.

      - 많은 설정에 OEM이 제공하는 기본값이 있습니다. 기본값이 있는지 확인하려면 설정 옆의 정보 아이콘을 마우스로 가리킵니다. 도구 설명에는 해당 설정의 기본값(해당하는 경우)과 OEM에서 제공하는 자세한 정보가 표시됩니다.

      - **지우기**를 클릭하면 프로필에서 설정이 삭제됩니다. 프로필에 설정이 없는 경우 프로필이 적용될 때 디바이스에서 해당 값이 변경되지 않습니다.

      - 구성 디자이너에서 비어 있는(구성되지 않은) 번들을 만드는 경우 JSON 편집기로 전환하면 번들이 삭제됩니다.

    - **JSON 편집기**: 이 옵션을 선택하면 앱에 포함된 전체 구성 스키마에 대한 템플릿이 JSON 편집기로 열립니다. 편집기에서 다른 설정의 값으로 템플릿을 사용자 지정합니다. **구성 디자이너**를 사용하여 값을 변경하는 경우 JSON 편집기는 구성 디자이너의 값으로 템플릿을 덮어씁니다.

      - 기존 프로필을 업데이트하는 경우 JSON 편집기는 프로필을 사용하여 마지막으로 저장된 설정을 표시합니다.

      - OEMConfig 스키마는 크고 복잡할 수 있습니다. 다른 편집기를 사용하여 이 설정을 업데이트하려면 **JSON 템플릿 다운로드** 단추를 선택합니다. 원하는 편집기를 사용하여 템플릿에 구성 값을 추가합니다. 그런 다음 업데이트된 JSON을 복사해 **JSON 편집기** 속성에 붙여넣습니다.

      - JSON 편집기를 사용하여 구성의 백업을 만들 수 있습니다. 설정을 구성한 후에 이 기능을 사용하여 JSON 설정을 값과 함께 가져옵니다. JSON을 복사해 파일에 붙여넣고 저장합니다. 이제 백업 파일이 있습니다.

    구성 디자이너에서 변경한 내용은 JSON 편집기에서도 자동으로 적용됩니다. 마찬가지로 JSON 편집기에서 변경한 내용은 구성 디자이너에서 자동으로 적용됩니다. 입력에 잘못된 값이 포함된 경우 문제를 해결할 때까지 구성 디자이너와 JSON 편집기 사이를 전환할 수 없습니다.

9. **다음**을 선택합니다.
10. **범위 태그**(선택 사항)에서 프로필을 특정 IT 그룹(예: `US-NC IT Team` 또는 `JohnGlenn_ITDepartment`)으로 필터링하는 태그를 할당합니다. 범위 태그에 대한 자세한 내용은 [분산형 IT에 RBAC 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.

    **다음**을 선택합니다.

11. **할당**에서 프로필을 수신할 사용자 또는 그룹을 선택합니다. 각 디바이스에 하나의 프로필을 할당합니다. OEMConfig 모델은 디바이스당 정책 하나만 지원합니다.

    프로필 할당에 대한 자세한 내용은 [사용자 및 디바이스 프로필 할당](device-profile-assign.md)을 참조하세요.

    **다음**을 선택합니다.

12. **검토 + 만들기**에서 설정을 검토합니다. **만들기**를 선택하면 변경 사항이 저장되고 프로필이 할당됩니다. 정책은 프로필 목록에도 표시됩니다.

다음에 디바이스에서 구성 업데이트를 확인할 때 구성한 OEM 관련 설정이 OEMConfig 앱에 적용됩니다.

> [!NOTE]
> 현재 OEMConfig 표준은 상태 보고를 포함하지 않습니다. 따라서 기본적으로 프로필에는 **보류 중** 상태가 표시됩니다.

## <a name="supported-oemconfig-apps"></a>지원되는 OEMConfig 앱

표준 앱에 비해, OEMConfig 앱은 Google에서 부여한 관리형 구성 권한을 확장하여 더 복잡한 스키마를 지원합니다. Intune은 현재 다음과 같은 OEMConfig 앱을 지원합니다.

-----------------

| OEM | 번들 ID | OEM 설명서(사용할 수 있는 경우) |
| --- | --- | ---|
| 삼성 | com.samsung.android.knox.kpu | [Knox Service Plugin 관리자 가이드](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Zebra Technologies | com.zebra.oemconfig.common | [Zebra OEMConfig 개요](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com.datalogic.oemconfig | [Datalogic OEMConfig 사용자 설명서](https://datalogic.github.io/oemconfig/) |
| Honeywell | com.honeywell.oemconfig |  |
| Kyocera | jp.kyocera.enterprisedeviceconfig |  |
| Spectralink - 바코드 | com.spectralink.barcode.service |  |
| Spectralink - 단추 | com.spectralink.buttons |  |
| Spectralink - 디바이스 | com.spectralink.slnkdevicesettings  |  |
| Spectralink - 로깅 | com.spectralink.slnklogger |  |
| Spectralink - VQO | com.spectralink.slnkvqo |  |
| HMD Global | com.hmdglobal.app.oemconfig.ironman |  |

-----------------

사용하는 디바이스용 OEMConfig 애플리케이션이 있지만 위의 표에 나와 있지 않거나 Intune 콘솔에 표시되지 않는다면 `IntuneOEMConfig@microsoft.com`에 메일을 보내 주세요.

> [!NOTE]
> OEMConfig 앱은 먼저 Intune에서 등록해야 OEMConfig 프로필을 사용해 구성할 수 있습니다. 앱이 지원되면 테넌트에서 설정하는 방법에 대해 Microsoft에 문의할 필요가 없습니다. 이 페이지의 지침을 따르면 됩니다.

## <a name="next-steps"></a>다음 단계

[프로필 상태를 모니터링](device-profile-monitor.md)합니다.
