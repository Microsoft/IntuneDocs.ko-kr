---
title: Google이 Intune에 보내는 데이터
titleSuffix: Microsoft Intune
description: Google이 Intune에 보내는 데이터 목록입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 914ce3aa15099b7692d524dbfa368f99f0d092e8
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504497"
---
# <a name="data-google-sends-to-intune"></a>Google이 Intune에 보내는 데이터

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

디바이스에서 Android 엔터프라이즈 디바이스 관리를 사용하도록 설정할 경우 Microsoft Intune이 Google에 연결하고, Intune과 Google 간에 사용자 및 디바이스 정보가 공유됩니다. Microsoft Intune이 연결을 설정하기 전에 Google 계정을 만들어야 합니다.

다음 표는 디바이스에서 디바이스 관리를 사용하도록 설정할 경우 Google이 Intune에 보내는 데이터를 보여 줍니다.


| Google이 Intune에 보내는 데이터 | 세부 정보 | 사용 목적 | 예제 |
|:---:|:---:|:---:|:---:|
| 엔터프라이즈 데이터 | Google에서 고객의 엔터프라이즈 식별자입니다. | Intune과 Google 간에 고객 정보를 연결합니다. | **enterpriseId** 예: LC04eik8a6.<br>**이름**. Android 엔터프라이즈를 구성할 때 입력한 관리자 이름입니다. 예: Joe Smith.<br>**관리자 메일**. Android 엔터프라이즈를 구성할 때 사용된 YourAdmin@gmail.com입니다. |
| 애플리케이션 데이터 | 관리되는 Play 스토어 애플리케이션에 대한 데이터입니다. | 애플리케이션 대상 사용자 또는 디바이스를 사용 가능이나 필수로 지정합니다. | **애플리케이션 이름** 예: Contoso Warehouse Inventory Application.<br>**애플리케이션을 나타내는 고유 식별자** 예: app:com.Contoso.Warehouse.InventoryTracking |
| 서비스 계정 | 특정 고객 통화에 사용할 고유한 내부 Google 서비스 계정입니다. | 앱, 디바이스 등을 보기 위해 고객을 대신해서 Google에 전화를 거는 데 사용됩니다. | **이름** 예: InternalAccount@InternalService.com<br>**키** 예: ServiceAccountPassword |


Microsoft Intune에서 Android 엔터프라이즈 디바이스 관리의 사용을 중단하고 데이터를 삭제하려면 Microsoft Intune과 Android 엔터프라이즈 디바이스 관리를 둘 다 사용하지 않도록 설정하고 Google 계정도 삭제해야 합니다. 계정 관리를 수행하는 방법은 Google 계정을 참조하세요.


