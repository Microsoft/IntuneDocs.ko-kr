---
title: GCC High 및 DoD 환경용 앱
titleSuffix: Microsoft Intune
description: Microsoft Intune을 사용하는 GCC High 및 DoD 환경과 관련된 앱에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d37bf060f11be9e295a9ef2743fa0ba33844df7
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839345"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Intune을 사용하여 GCC High 및 DoD 환경에 앱 배포 

테넌트 관리자는 Microsoft Intune을 사용하여 인력에게 앱을 배포할 수 있습니다. 인력은 회사 직원이자 앱 사용자입니다. Intune에서 GCC High 또는 DoD 환경에 배포할 수 있는 다양한 종류의 앱이 있습니다. 관리자는 타사 공급업체에서 GCC High 또는 DoD 고객용으로 맞춤 제작했거나 [비즈니스용 Microsoft Store](https://businessstore.microsoft.com/store)에서 오프라인 앱으로 다운로드한 Windows 앱을 업로드하고 배포해야 하는 경우 [기간 업무 앱](apps-add.md#app-types-in-microsoft-intune)으로 배포하도록 선택할 수 있습니다.  

> [!NOTE]
> 상용 환경에서는 테넌트 관리자가 비즈니스용 Microsoft Store를 Intune과 동기화할 수 잇지만, GCC High 및 DoD 환경에서는 이 서비스를 사용할 수 없습니다. 이 경우 관리자는 Intune에 앱을 직접 업로드하여 배포해야 합니다.  

## <a name="add-line-of-business-apps-using-intune"></a>Intune을 사용하여 기간 업무 앱 추가 

Intune을 사용하여 GCC High 또는 DoD 환경용 앱을 추가하려면 [Windows LOB 앱](lob-apps-windows.md) 지침을 따릅니다. 비즈니스용 Microsoft Store에서 회사 포털을 먼저 배포하도록 선택할 수 있습니다. 회사 포털을 사용하기로 선택하는 경우 회사 포털을 수동으로 설치하고 배포할 수 있습니다. 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요. 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Intune을 사용하여 비즈니스용 Microsoft Store의 오프라인 앱 배포  

비즈니스용 Microsoft Store에서 [오프라인 라이선스 앱을 다운로드](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app)해야 하는 경우 다음 단계에 따라 애플리케이션을 다운로드합니다. 

1. [비즈니스용 Microsoft Store](https://businessstore.microsoft.com/)에 로그인합니다.
2. **관리** > **설정**을 선택합니다.
3. **쇼핑 경험**에서 **오프라인 앱 표시**를 **켬**으로 설정합니다.

앱을 쇼핑할 때 오프라인 버전이 있는 경우 라이선스 유형을 오프라인으로 변경할 수 있습니다. 앱에서 받은 후 [비즈니스용 Microsoft Store](https://businessstore.microsoft.com/)에서 **관리** > **제품 및 서비스**를 선택하여 앱을 관리할 수 있습니다. 또한 앱과 앱의 종속 요소를 다운로드할 수 있습니다. 이렇게 다운로드한 앱(및 종속 요소)은 Intune을 사용하여 사용자에게 배포할 수 있습니다.  

## <a name="syncing-intune-to-the-store-for-business"></a>Intune을 비즈니스용 Microsoft Store와 동기화 

상용(비 정부) 환경에서는 관리자가 Intune을 비즈니스용 Microsoft Store와 동기화 수 있습니다. 정부 환경에서는 이 기능을 사용할 수 없습니다. 상용 환경의 Intune과 정부 환경의 Intune이 어떻게 다른지 자세히 알아보려면 [US Government용 Enterprise Mobility + Security 서비스 설명](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description)을 참조하세요.  

Intune을 비즈니스용 Microsoft Store 계정과 동기화하려면 [Microsoft Intune을 사용하여 비즈니스용 Microsoft Store에서 구입한 앱을 관리하는 방법](windows-store-for-business.md)을 참조하세요.  

## <a name="compliance"></a>준수 

서비스가 적절하게 사용되고 있는지 평가할 때 앱의 프라이버시 및 규정 준수 방침을 검토하고 소속 조직의 규정 준수, 보안 및 프라이버시 요구 사항과 비교합니다.   

## <a name="next-steps"></a>다음 단계

앱을 배포하고 할당하는 방법에 대한 자세한 내용은 [Microsoft intune을 사용하여 그룹에 앱 할당](apps-deploy.md)을 참조하세요.

 
