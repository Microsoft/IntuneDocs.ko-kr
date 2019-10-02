---
title: Intune이 Google에 보내는 데이터
titleSuffix: Microsoft Intune
description: Intune이 Google에 보내는 데이터 목록입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f0825d44ba52bee1331fe1d715e4e58806e80f5
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721489"
---
# <a name="data-intune-sends-to-google"></a>Intune이 Google에 보내는 데이터

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

디바이스에서 Android 엔터프라이즈 디바이스 관리를 사용하도록 설정할 경우 Microsoft Intune이 Google에 연결하고 사용자 및 디바이스 정보를 Google과 공유합니다. Microsoft Intune이 연결을 설정하기 전에 Google 계정을 만들어야 합니다.

다음 표는 디바이스에서 디바이스 관리를 사용하는 경우 Microsoft Intune이 Google에 보내는 데이터를 보여 줍니다.


| Google에 보낸 데이터 | 세부 정보 | 사용 목적 | 예제 |
|:---:|:---:|:---:|:---:|
| EnterpriseId | Intune에 Gmail 계정 바인딩 시 Google에서 발생합니다. | Intune과 Google 간 통신에 사용되는 기본 식별자입니다.  이 통신에는 정책 설정, 관리 디바이스, Intune과 Android Enterprise 간의 바인딩/바인딩 해제가 포함됩니다. | 고유 식별자, 형식 예: LC04eik8a6 |
| 정책 본문 | 새 응용 프로그램 또는 구성 정책을 저장하는 경우 Intune에서 발생합니다. | 디바이스에 정책을 적용합니다. | 애플리케이션 또는 구성 정책을 위해 구성된 모든 설정의 컬렉션입니다. 이 컬렉션에는 네트워크 이름, 애플리케이션 이름, 애플리케이션별 설정 같은 정책의 일부로서 제공되는 경우 고객 정보를 포함할 수 있습니다. |
| 디바이스 데이터 | 작업 프로필 시나리오를 위해 디바이스는 Intune에 등록을 시작합니다. 관리 디바이스 시나리오를 위해 디바이스는 Google에 등록을 시작합니다. | 디바이스 데이터 정보는 정책 적용, 디바이스 관리 및 일반적인 보고 같은 다양한 작업을 위해 Intune과 Google 간에 전송됩니다. | **디바이스 이름을 나타내는 고유 식별자입니다.** 예: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**사용자 이름을 나타내는 고유 식별자입니다.** 예: Enterprises/LC04ebru7b/users/116838519924207449711<br>**디바이스 상태입니다.** 예: 활성, 사용하지 않음, 프로비저닝.<br>**준수 상태입니다.** 예: 설정 지원되지 않음, 누락된 필수 앱<br>**소프트웨어 정보입니다.** 예제: 소프트웨어 버전 및 패치 수준.<br>**네트워크 정보입니다.** 예: IMEI, MEID, WifiMacAddress<br>**디바이스 설정입니다.** 예: 암호화 수준에 대한 정보 및 디바이스가 알려지지 않은 앱을 허용하는지 여부.<br> JSON 메시지의 예제는 아래를 참조하십시오. |
| newPassword | Intune에서 발생합니다. | 디바이스 암호를 재설정합니다. | 새 암호를 나타내는 문자열입니다. |
| Google 사용자 | Google | 작업 프로필(BYOD) 시나리오에 대한 작업 프로필을 관리합니다. | 연결된 Gmail 계정을 나타내는 고유 식별자입니다. 예: 114223373813435875042 |
| 애플리케이션 데이터 | 애플리케이션 정책을 저장하는 경우 Intune에서 발생 합니다. |  | 애플리케이션 이름 문자열입니다. 예: app:com.microsoft.windowsintune.companyportal |
| Enterprise 서비스 계정 | Intune 요청 시 Google에서 발생합니다. | 해당 고객 관련 트랜잭션을 위해 Intune과 Google 간 인증에 사용됩니다. | 몇 가지 파트가 있습니다.<br> **Enterprise Id**: 이전에 문서화됐습니다.<br>**UPN**: 고객 대신 인증에 사용된 UPN을 생성 했습니다.<br>예: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**키**: 해당 서비스에 암호화되어 저장되고 인증 요청에 사용되는 Base64로 인코딩된 BLOB입니다. 그러나 이것이 BLOB의 모습입니다.<br> 고객 키를 나타내는 고유 식별자<br>예: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |


Microsoft Intune에서 Android 엔터프라이즈 디바이스 관리의 사용을 중단하고 데이터를 삭제하려면 Microsoft Intune과 Android 엔터프라이즈 디바이스 관리를 둘 다 사용하지 않도록 설정하고 Google 계정도 삭제해야 합니다. 계정 관리를 수행하는 방법은 Google 계정을 참조하세요.


