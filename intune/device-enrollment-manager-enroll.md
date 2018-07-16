---
title: 장치 등록 관리자 계정을 사용하여 장치 등록
titlesuffix: Microsoft Intune
description: 장치 등록 관리자 계정을 사용하여 Intune에 장치를 등록합니다. "
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b18a55d7bd37ab32f6b2f64eee00489389ea323d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905226"
---
# <a name="enroll-devices-by-using-a-device-enrollment-manager-account"></a>장치 등록 관리자 계정을 사용하여 장치 등록

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

조직에서는 Intune을 사용하여 단일 사용자 계정으로 많은 수의 모바일 장치를 관리할 수 있습니다. *DEM(장치 등록 관리자)* 계정은 1000개까지 장치를 등록할 수 있는 특수한 사용자 계정입니다. 기존 사용자를 DEM 계정에 추가하여 특수 DEM 기능을 제공합니다. 등록된 각 장치는 단일 라이선스를 사용합니다. 이 계정을 통해 등록한 장치는 개인("BYOD") 장치가 아닌 공유 장치로 사용하는 것이 좋습니다.  

장치 등록 관리자로 추가하려면 [Azure Portal](https://portal.azure.com)에 사용자가 존재해야 합니다. 보안 최적화를 위해 DEM 사용자는 Intune 관리자여서도 안 됩니다.

>[!NOTE]
>DEM 등록 방법은 [Apple Configurator에서 설정 도우미 사용](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator에서 직접 등록](apple-configurator-direct-enroll-ios.md), [ASM(Apple School Manager) 사용](apple-school-manager-set-up-ios.md) 또는 [DEP(장치 등록 프로그램) 사용](device-enrollment-program-enroll-ios.md) 등의 다른 등록 방법과 함께 사용할 수 없습니다.

## <a name="example-of-a-device-enrollment-manager-scenario"></a>장치 등록 관리자 시나리오의 예

식당에는 서빙 직원을 위한 50대의 POS 태블릿과 주방 직원을 위한 주문 모니터를 공급하기를 원합니다. 직원은 회사 데이터에 액세스하거나 사용자로 로그인할 필요가 없습니다. Intune 관리자는 식당 감독자에 대한 새 장치 등록 관리자 계정을 만듭니다.  이 계정은 감독자의 기본 계정과 별도로 intune에 공유 장치를 등록하는 용도로만 사용됩니다. 이제 감독자는 DEM 자격 증명을 사용하여 50대의 태블릿 장치를 등록할 수 있습니다.

[Azure Portal](https://portal.azure.com)의 사용자만 장치 등록 관리자가 될 수 있습니다. 장치 등록 관리자 사용자는 Intune 관리자일 수 없습니다.

DEM 사용자는 다음 작업을 수행할 수 있습니다.

-   Intune에서 최대 1,000개의 장치 등록
-   회사 포털에 로그인하여 회사 앱 가져오기
-   태블릿에 역할별 앱을 배포하여 회사 데이터에 대한 액세스 구성

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>DEM 계정을 사용하여 등록된 장치의 제한 사항

장치 등록 관리자 계정을 사용하여 등록한 장치에는 다음과 같은 제한 사항이 적용됩니다.

  - 사용자별 액세스는 불가능합니다. 장치에 할당된 사용자가 없기 때문에 장치에는 메일 또는 회사 데이터 액세스 권한이 없습니다. VPN 구성 등을 계속 사용하여 장치 앱에 데이터 액세스 권한을 제공할 수는 있습니다.
  - DEM 사용자는 회사 포털을 사용하여 장치 자체에서 DEM에 등록된 장치 등록을 해제할 수 없습니다. Intune 관리는 등록을 해제할 수 있습니다.
  - 회사 포털 앱 또는 웹 사이트에 로컬 장치만 표시됩니다.
  - 앱 관리에 대한 사용자별 Apple ID 요구 사항으로 인해 사용자 라이선스를 통해 Apple VPP(Volume Purchase Program) 앱을 사용할 수 없습니다.
  - (iOS에만 해당) DEM을 사용하여 iOS 장치를 등록하는 경우 Apple Configurator, Apple DEP(장치 등록 프로그램) 또는 ASM(Apple School Manager)를 사용하여 장치를 등록할 수 없습니다.
  - (Android에만 해당) 단일 DEM 계정으로 등록할 수 있는 Android 회사 프로필 장치의 수에는 제한이 있습니다. DEM 계정당 10개까지 Android 회사 프로필 장치를 등록할 수 있습니다. 이 제한은 기존 Android 등록에는 적용되지 않습니다.
  - 장치 라이선스가 있는 경우 장치는 VPP 앱을 설치할 수 있습니다.
  - 각 장치에 장치 라이선스가 필요합니다. [사용자 및 장치 라이선스](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services)에 대해 자세히 알아보세요.


> [!NOTE]
> 장치 등록 관리자에서 관리하는 장치에 회사 앱을 배포할 수 있습니다. **필수 설치**인 회사 포털 앱을 장치 등록 관리자의 사용자 계정에 배포합니다.
> 성능 향상을 위해 DEM 장치에서 회사 포털 앱을 보면 로컬 장치만 표시됩니다. 다른 DEM 장치의 원격 관리는 Intune 관리 콘솔에서만 수행할 수 있습니다.


## <a name="add-a-device-enrollment-manager"></a>장치 등록 관리자 추가

1.  [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **장치 등록 관리자**를 선택합니다.

2.  **추가**를 선택합니다.

3.  **사용자 추가** 블레이드에서 DEM 사용자의 사용자 계정 이름을 입력하고 **추가**를 선택합니다. DEM 사용자가 DEM 사용자 목록에 추가됩니다.

## <a name="permissions-for-dem"></a>DEM에 대한 권한

Admin Portal에서 DEM 등록 관련 작업을 수행하려면 전역 또는 Intune 서비스 관리자 Azure AD 역할이 필요합니다. 또한 사용자 지정 사용자 역할 아래에 RBAC 권한이 나열되어 있고 사용 가능하더라도 모든 DEM 사용자를 보려면 이러한 역할이 필요합니다. 전역 관리자 또는 Intune 서비스 관리자 역할은 할당되지 않고 장치 등록 관리자 역할에 대한 읽기 권한은 있는 사용자의 경우 자신이 만든 DEM 사용자만 볼 수 있습니다. 이러한 기능에 필요한 RBAC 역할 지원이 향후 발표될 예정입니다.

전역 관리자 또는 Intune 서비스 관리자 역할은 할당되지 않고 장치 등록 관리자 역할용으로 사용하도록 설정된 읽기 권한은 할당된 사용자의 경우 자신이 만든 DEM 사용자만 볼 수 있습니다.

## <a name="remove-a-device-enrollment-manager"></a>장치 등록 관리자 제거

장치 등록 관리자를 제거해도 등록된 장치에는 영향을 주지 않습니다. 장치 등록 관리자를 제거하는 경우:

-   등록된 장치는 영향을 받지 않으며 계속 완전하게 관리됩니다.
-   제거된 장치 등록 관리자 계정 자격 증명은 계속 유효합니다.
-   제거된 장치 등록 관리자는 여전히 장치를 초기화하거나 사용 중지할 수 없습니다.
-   제거된 장치 등록 관리자는 Intune 관리자가 구성한 사용자별 제한 수까지만 장치를 등록할 수 있습니다.

**장치 등록 관리자를 제거하려면**

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록**을 선택한 다음, **장치 등록 관리자**를 선택합니다.
2. **장치 등록 관리자** 블레이드에서 DEM 사용자를 선택하고 **삭제**를 선택합니다.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>장치 등록 관리자의 속성 보기

1. [Azure Portal](https://portal.azure.com)에서 **장치 등록**을 선택한 다음, **장치 등록 관리자**를 선택합니다.
2. **장치 등록 관리자** 블레이드에서 DEM 사용자를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
