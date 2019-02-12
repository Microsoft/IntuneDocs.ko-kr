---
title: Microsoft Intune-Azure를 사용한 Windows 10 디바이스 다시 설정 | Microsoft Docs
description: Microsoft Intune을 사용하여 Windows 10 PC에서 앱을 제거하기 위해 새로 시작을 사용합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 1eb1e671cc16196974cb15cdc785ba7d99fa8f46
ms.sourcegitcommit: 4bd992da609b8bcc85edc2d64fe8128546aa4617
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55303415"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Intune을 통해 새로 시작 기능을 사용하여 Windows 10 디바이스 다시 설정


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**새로 시작** 디바이스 작업은 Windows 10 버전 1703 이상을 실행하는 PC에 설치된 모든 앱을 제거합니다. 새로 시작을 통해 일반적으로 새로운 PC에 설치되는 사전 설치된(OEM) 앱을 제거할 수 있습니다.  

1. [Azure Portal](https://portal.azure.com)에 로그인하고 **Microsoft Intune** > **디바이스** > **모든 디바이스**로 이동합니다.
2. 관리하는 디바이스 목록에서 Windows 10 데스크톱 디바이스를 선택합니다.
3. **새로 시작**을 클릭합니다. 
4. **이 디바이스에 사용자 데이터 유지**를 선택합니다. 이렇게 하면
   * 디바이스의 Azure Active Directory를 조인된 상태로 유지할 수 있습니다.
    * Azure Active Directory를 사용하는 사용자가 디바이스에 로그인하면 모바일 디바이스 관리에 디바이스가 다시 등록됩니다.
    * 디바이스 사용자의 홈 폴더에 있는 콘텐츠를 유지하고 앱과 설정을 제거할 수 있습니다.  
  > [!IMPORTANT]
 > 사용자 데이터를 유지하지 않으면 디바이스가 초기 상태로 복원되고 Azure AD 및 모바일 디바이스 관리에서 BYOD 디바이스 등록이 취소됩니다.
 > Azure Active Directory를 사용하는 사용자가 디바이스에 로그인하면 모바일 디바이스 관리에 Azure AD 조인 디바이스가 다시 등록됩니다.
 
5. **확인**을 클릭합니다.   
6. 이 작업의 상태를 보려면 **디바이스**로 돌아가서 **디바이스 작업**을 클릭합니다.  
