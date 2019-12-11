---
title: Intune에 보내는 데이터 JAMF Pro
titleSuffix: Microsoft Intune
description: Jamf Pro가 Intune을 사용하여 Mac을 관리하기 위해 Jamf Pro를 통합할 때 Microsoft Intune에 보내는 데이터의 목록을 검토합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4bf6df44335f3375d58d3c2c11da7cb3f982b3e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502410"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Intune에 보내는 데이터 Jamf Pro

[Jamf Pro](https://www.jamf.com)를 사용하여 Intune으로 최종 사용자 Mac을 관리할 때 Jamf Pro는 관리되는 macOS 디바이스에 대한 인벤토리 정보를 캡처합니다. 

## <a name="data"></a>Data  
Jamf Pro가 Intune과 공유하는 데이터의 목록은 Jamf Pro 기술 문서에 있는 [Appendix: Inventory Information Shared with Microsoft Intune](https://docs.jamf.com/technical-papers/jamf-pro/microsoft-intune/10.9.0/Appendix__Inventory_Information_Shared_with_Microsoft_Intune.html)을 참조하세요. 

<!--  
Jamf Pro reports the following information to Intune:  

* Device Azure AD ID
* JAMF Inventory State (inventory state of a computer checked in with Jamf Pro within the last 24 hours)
* OS Version
* User Azure AD ID
* Encrypted (FileVault 2)
* Gatekeeper Status
* Password: minimum number of character sets
* Password expiration (days)
* Password Type - simple, alphanumeric, or unknown
* Prevent Auto Login
* Required Passcode Length
* Password: number of previous passwords to prevent reuse
* System Integrity Protection
* Last Check-In Time
* Architecture Type
* Available RAM Slots
* Battery Capacity
* Boot ROM
* Bus Speed
* Cache Size
* Device Name
* Domain Join
* Jamf ID
* MAC address
* Make
* Model
* Model Identifier
* NIC Speed
* Number of Cores
* Number of Processors
* OS
* Platform
* Processor Speed
* Processor Type
* Secondary MAC Address
* Serial Number
* SMC Version
* Total RAM
* UDID
* User Email
--> 

<!-- 
You can remove a Jamf-managed device from the Intune console by selecting **Delete** in the **All devices** view. Bulk device deletion can be enabled by selecting multiple devices and clicking **Delete**.
-->

## <a name="next-steps"></a>다음 단계
[Jamf 관리 디바이스를 Jamf Pro 문서에서 제거](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)하는 방법에 대해 알아봅니다. 또한 추가 도움을 위해 지원 티켓을 [Jamf 지원](https://www.jamf.com/support/)와 함께 제출할 수 있습니다. 

