---
title: Microsoft Intune에서 Android Enterprise 디바이스에 OEMConfig 사용 - Azure | Microsoft Docs
description: Microsoft Intune를 사용 하 여 OEMConfig에서 Android Enterprise를 실행 하는 장치를 관리 및 사용 합니다. 개요를 비롯 한 모든 단계를 확인 하 고, 필수 구성 요소를 확인 하 고, Intune에서 구성 프로필을 만들고, 지원 되는 OEMConfig 앱 목록을 확인 하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
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
ms.openlocfilehash: e514c10ea61bb12ef3c4626b077aa105b66866f1
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206876"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Microsoft Intune에서 OEMConfig를 사용 하 여 Android Enterprise 장치 사용 및 관리



Microsoft Intune에서 OEMConfig를 사용 하 여 Android Enterprise 장치에 대 한 OEM 관련 설정을 추가, 작성 및 사용자 지정할 수 있습니다. OEMConfig는 일반적으로 Intune에 기본 제공 되지 않는 설정을 구성 하는 데 사용 됩니다. OEM (원본 장비 제조업체) 마다 다른 설정이 포함 되어 있습니다. 사용 가능한 설정은 해당 OEMConfig 앱에서 OEM이 포함 하는 기능에 따라 달라 집니다.

이 기능은 다음에 적용됩니다.  

- Android Enterprise

이 문서에서는 OEMConfig에 대해 설명 하 고, 필수 구성 요소를 나열 하 고, 구성 프로필을 만드는 방법을 보여 주고, Intune에서 지원 되는 OEMConfig 앱을 나열 합니다.

## <a name="overview"></a>개요

OEMConfig 정책은 [앱 구성 정책과](../apps/app-configuration-policies-overview.md)유사한 특수 한 유형의 장치 구성 정책입니다. OEMConfig는 Android에서 앱 구성을 활용 하 여 Oem (Oem에서 작성 한 앱 (원래 장비 제조업체)에 장치 설정을 전송 하는 Google에서 정의 된 표준입니다. 이 표준을 통해 Oem과 Emms 명령이 (enterprise mobility management)에서 표준화 된 방법으로 OEM 관련 기능을 빌드 및 지원할 수 있습니다. [OEMConfig에 대해 자세히 알아보세요](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

지금까지 Intune과 같은 Emms 명령이은 oem에 의해 도입 된 후 OEM 관련 기능에 대 한 지원을 수동으로 작성 합니다. 이 방법을 사용 하면 중복 된 노력과 도입이 지연 됩니다.

OEM은 OEMConfig를 사용 하 여 OEM 특정 관리 기능을 정의 하는 스키마를 만듭니다. OEM은 앱에 스키마를 포함 한 다음 Google Play에이 앱을 배치 합니다. EMM은 앱에서 스키마를 읽고 EMM 관리자 콘솔에서 스키마를 노출 합니다. 콘솔에서 Intune 관리자는 스키마의 설정을 구성할 수 있습니다.

장치에 설치 된 OEMConfig 앱은 EMM 관리자 콘솔에 구성 된 설정을 사용 하 여 장치를 관리 합니다. 장치에 대 한 설정은 EMM에서 빌드된 MDM 에이전트 대신 OEMConfig 앱에 의해 실행 됩니다.

OEM은 관리 기능을 추가 하 고 개선 하는 경우 Google Play 에서도 앱을 업데이트 합니다. 관리자는 이러한 업데이트를 포함 하는 Emms 명령이를 기다리지 않고 이러한 새로운 기능 및 업데이트 (픽스 포함)를 얻을 수 있습니다.

> [!TIP]
> 이 기능을 지원 하 고 해당 하는 OEMConfig 앱이 있는 장치에는 OEMConfig만 사용할 수 있습니다. OEM에 특정 세부 정보를 참조 하세요.

## <a name="before-you-begin"></a>시작하기 전에

OEMConfig를 사용 하는 경우 다음 정보를 알고 있어야 합니다.

- Intune은 구성할 수 있도록 OEMConfig 앱의 스키마를 노출 합니다. Intune은 앱에서 제공 하는 스키마의 유효성을 검사 하거나 변경 하지 않습니다. 따라서 스키마가 잘못 되었거나 부정확 한 데이터가 있는 경우이 데이터는 여전히 장치에 전송 됩니다. 스키마에서 발생 한 문제를 발견 한 경우 OEM에 게 문의 하십시오.
- Intune은 앱 스키마의 콘텐츠를 영향을 주거나 제어 하지 않습니다. 예를 들어, Intune은 문자열, 언어, 허용 되는 작업 등을 제어 하지 않습니다. Microsoft는 OEMConfig를 사용 하 여 장치를 관리 하는 방법에 대 한 자세한 내용과 모범 사례를 제공 합니다.
- Oem은 언제 든 지 지원 되는 기능 및 스키마를 업데이트 하 고 Google Play에 새 앱을 업로드할 수 있습니다. Intune은 항상 Google Play에서 최신 버전의 OEMConfig 앱을 동기화 합니다. Intune은 스키마 또는 앱의 이전 버전을 유지 관리 하지 않습니다. 버전 충돌이 발생 한 경우 자세한 내용을 보려면 OEM에 문의 하는 것이 좋습니다.
- 하나의 OEMConfig 프로필을 장치에 할당 합니다. 동일한 장치에 여러 프로필을 할당 하는 경우 일관 되지 않은 동작이 표시 될 수 있습니다. OEMConfig 모델은 장치당 단일 정책만 지원 합니다.

## <a name="prerequisites"></a>전제 조건

장치에서 OEMConfig를 사용 하려면 다음 요구 사항을 충족 해야 합니다.

- Intune에 등록 된 Android Enterprise 장치입니다.
- OEM에서 빌드하고 Google Play로 업로드 되는 OEMConfig 앱입니다. Google Play 되지 않은 경우 자세한 내용은 OEM에 게 문의 하세요.
- Intune 관리자는 **Mobile apps**에 대 한 RBAC (역할 기반 액세스 제어) 권한, **장치 구성**및 **Android for Work**의 "읽기" 권한이 있습니다. 이러한 권한은 OEMConfig 프로필에서 관리 되는 앱 구성을 사용 하 여 장치 구성을 관리 하기 때문에 필요 합니다.

## <a name="prepare-the-oemconfig-app"></a>OEMConfig 앱 준비

장치에서 OEMConfig를 지원 하 고, 올바른 OEMConfig 앱이 Intune에 추가 되 고, 앱이 장치에 설치 되어 있어야 합니다. OEM에 게이 정보를 문의 하세요.

> [!TIP] 
> OEMConfig 앱은 OEM에만 적용 됩니다. 예를 들어 얼룩말 기술 장치에 설치 된 Sony OEMConfig 앱은 어떤 작업도 수행 하지 않습니다.

1. 관리 되는 Google Play 스토어에서 OEMConfig 앱을 가져옵니다. [Android 엔터프라이즈 디바이스에 관리되는 Google Play 앱 추가](../apps/apps-add-android-for-work.md)에서는 단계가 나열됩니다.
2. 일부 Oem은 OEMConfig 앱이 미리 설치 된 장치를 배송할 수 있습니다. 앱이 사전 설치 되지 않은 경우 Intune을 사용 하 여 [앱을 추가 하 고 장치에 배포](../apps/apps-deploy.md)합니다.

## <a name="create-an-oemconfig-profile"></a>OEMConfig 프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Android Enterprise**를 선택합니다.
    - **프로필 유형**: **oemconfig**를 선택 합니다.

4. **연결 된 앱**을 선택 하 고 이전에 추가한 기존 oemconfig 앱을 선택 > **확인**합니다. 정책을 할당 하는 장치에 대 한 올바른 OEMConfig 앱을 선택 해야 합니다.

    나열 된 앱이 표시 되지 않는 경우 관리 Google Play를 설정 하 고 관리 되는 Google Play 저장소에서 앱을 가져옵니다. [Android 엔터프라이즈 디바이스에 관리되는 Google Play 앱 추가](../apps/apps-add-android-for-work.md)에서는 단계가 나열됩니다.

    > [!IMPORTANT]
    > OEMConfig 앱을 추가 하 고 Google Play에 동기화 했지만 **연결 된 앱**으로 나열 되지 않은 경우 Intune에 앱을 등록 해야 할 수 있습니다. [새 앱 추가](#supported-oemconfig-apps) (이 문서)를 참조 하세요.

5. **설정 구성**에서 **구성 디자이너** 또는 **JSON 편집기**를 사용 하도록 선택 합니다.

    > [!TIP]
    > OEM 설명서를 읽고 속성을 올바르게 구성 하 고 있는지 확인 합니다. 이러한 앱 속성은 Intune이 아닌 OEM에 의해 포함 됩니다. Intune은 속성에 대 한 유효성 검사를 최소한으로 수행 하거나 입력 한 내용을 확인 합니다. 예를 들어 포트 번호에 대 한 `abcd`를 입력 하면 프로필은 그대로 저장 되 고 사용자가 구성한 값으로 장치에 배포 됩니다. 올바른 정보를 입력 해야 합니다.

    - **구성 디자이너**:이 옵션을 선택 하면 사용자가 구성할 수 있도록 앱 스키마 내에서 사용할 수 있는 속성이 표시 됩니다.

      - 구성 디자이너의 상황에 맞는 메뉴에서 더 많은 옵션을 사용할 수 있음을 표시 합니다. 예를 들어 상황에 맞는 메뉴를 사용 하 여 설정을 추가, 삭제 및 다시 정렬할 수 있습니다. 이러한 옵션은 OEM에 의해 포함 됩니다. 이러한 옵션을 사용 하 여 프로필을 만드는 방법을 알아보려면 OEM 앱 설명서를 참조 하세요.

      - 많은 설정에 OEM에서 제공 하는 기본값이 있습니다. 기본값이 있는지 확인 하려면 설정 옆의 정보 아이콘을 마우스로 가리킵니다. 도구 설명에는 해당 설정의 기본값 (해당 하는 경우)과 OEM에서 제공 하는 자세한 정보가 표시 됩니다.

      - **지우기** 를 클릭 하면 프로필에서 설정이 삭제 됩니다. 프로필이 프로필에 없는 경우 프로필이 적용 될 때 장치에서 해당 값이 변경 되지 않습니다.

      - 구성 디자이너에서 비어 있는 (구성 되지 않은) 번들을 만드는 경우 JSON 편집기로 전환할 때 삭제 됩니다.

    - **Json 편집기**:이 옵션을 선택 하면 앱에 포함 된 전체 구성 스키마에 대 한 템플릿이 포함 된 JSON 편집기가 열립니다. 편집기에서 다른 설정의 값으로 템플릿을 사용자 지정 합니다. **구성 디자이너** 를 사용 하 여 값을 변경 하는 경우 JSON 편집기는 구성 디자이너의 값으로 템플릿을 덮어씁니다.

      - 기존 프로필을 업데이트 하는 경우 JSON 편집기는 프로필을 사용 하 여 마지막으로 저장 한 설정을 표시 합니다.

      - OEMConfig 스키마는 크고 복잡할 수 있습니다. 다른 편집기를 사용 하 여 이러한 설정을 업데이트 하려면 **JSON 템플릿 다운로드** 단추를 선택 합니다. 선택한 편집기를 사용 하 여 템플릿에 구성 값을 추가 합니다. 그런 다음 업데이트 된 JSON을 복사 하 여 **json 편집기** 속성에 붙여넣습니다.

      - JSON 편집기를 사용 하 여 구성의 백업을 만들 수 있습니다. 설정을 구성한 후에는이 기능을 사용 하 여 JSON 설정을 값으로 가져옵니다. JSON을 복사 하 여 파일에 붙여넣고 저장 합니다. 이제 백업 파일이 있습니다.

    구성 디자이너에서 변경한 내용은 JSON 편집기 에서도 자동으로 수행 됩니다. 마찬가지로 JSON 편집기에서 변경한 내용은 구성 디자이너에서 자동으로 수행 됩니다. 입력에 잘못 된 값이 포함 된 경우 문제를 해결할 때까지 구성 디자이너와 JSON 편집기 사이를 전환할 수 없습니다.

6. **확인** > **추가**를 선택하여 변경 내용을 저장합니다. 정책이 만들어지고 목록에 표시됩니다.

[프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.

 > [!NOTE]
 > 각 디바이스에 하나의 프로필을 할당합니다. OEMConfig 모델은 장치당 하나의 정책만 지원 합니다.

다음 번에 장치에서 구성 업데이트를 확인할 때 구성한 OEM 관련 설정이 OEMConfig 앱에 적용 됩니다.

> [!NOTE]
> OEMConfig 표준은 현재 상태 보고를 포함 하지 않습니다. 따라서 기본적으로 프로필은 **보류 중** 상태를 표시 합니다.

## <a name="supported-oemconfig-apps"></a>지원 되는 OEMConfig 앱

표준 앱에 비해, OEMConfig 앱은 Google에서 부여 된 관리 되는 구성 권한을 확장 하 여 더 복잡 한 스키마를 지원 합니다. Intune은 현재 다음과 같은 OEMConfig 앱을 지원 합니다.

-----------------

| OEM | 번들 ID | OEM 설명서 (사용할 수 있는 경우) |
| --- | --- | ---|
| 삼성 | kpu입니다. | [Knox 서비스 플러그 인 관리자 가이드](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| 얼룩말 기술 | 얼룩말. common | [얼룩말 OEMConfig 개요](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | datalogic 구성 | [Datalogic OEMConfig에 대 한 사용자 설명서](https://datalogic.github.io/oemconfig/) |
| Honeywell | honeywell 구성 |  |
| Kyocera | kyocera. enterprisedeviceconfig |  |
| Spectralink-바코드 | spectralink. |  |
| Spectralink-단추 | spectralink |  |
| Spectralink-장치 | spectralink nkdevicesettings  |  |
| Spectralink-로깅 | spectralink. nknnn로거에서 |  |
| Spectralink-VQO | spectralink. slnkvqo |  |

-----------------

장치에 대 한 OEMConfig 응용 프로그램이 있지만 위의 표에 없거나 Intune 콘솔에 표시 되지 않는 경우 전자 메일을 `IntuneOEMConfig@microsoft.com`하세요.

> [!NOTE]
> Oemconfig 앱은 등록를 사용 하 여 구성 해야 합니다. 앱이 지원 되 면 테 넌 트에서 설정 하는 방법에 대해 Microsoft에 문의할 필요가 없습니다. 이 페이지의 지침을 따르세요.

## <a name="next-steps"></a>다음 단계

- [프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
