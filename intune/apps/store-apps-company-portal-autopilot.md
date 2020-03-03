---
title: Autopilot 프로비저닝된 디바이스용 Windows 10 회사 포털 앱 추가 및 할당
titleSuffix: Microsoft Intune
description: Intune에 Autopilot 프로비저닝된 디바이스용 Windows 10 회사 포털 앱 추가 및 할당
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c13d8d774037f0d2db5832af7f39c864330fef30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77577287"
---
# <a name="add-and-assign-the-windows-10-company-portal-app-for-autopilot-provisioned-devices"></a>Autopilot 프로비저닝된 디바이스용 Windows 10 회사 포털 앱 추가 및 할당

디바이스를 관리하고 앱을 설치하려 사용자는 회사 포털 앱을 사용할 수 있습니다. Intune에서 직접 Windows 10 회사 포털 앱을 할당할 수 있습니다. 

## <a name="prerequisites"></a>전제 조건

Windows 10 Autopilot 프로비저닝된 디바이스의 경우 비즈니스용 Microsoft Store 계정을 Intune과 연결하는 것이 좋습니다. 자세한 내용은 [Microsoft Intune을 사용하여 비즈니스용 Microsoft Store에서 대량 구매 앱을 관리하는 방법](~/apps/windows-store-for-business.md)을 참조하세요.

다음 단계를 사용하여 회사 포털(오프라인)을 설치하도록 선택합니다. 회사 포털 앱은 Autopilot 그룹에 할당되고 사용자가 로그인하기 전에 디바이스에 설치될 경우 디바이스 컨텍스트에서 설치됩니다. 

## <a name="configure-settings-to-show-offline-apps"></a>오프라인 앱을 표시하도록 설정 구성
1. 관리자 계정을 사용하여 [비즈니스용 Microsoft 스토어](https://www.microsoft.com/business-store)에 로그인합니다.
2. 창 위쪽 부근에 있는 **관리** 탭을 선택합니다.
3. 왼쪽 창에서 **설정**을 선택합니다.
4. **쇼핑 경험**에서 **오프라인 앱 표시**를 **켬**으로 설정합니다.  
    오프라인 사용이 허가된 앱이 표시됩니다.

## <a name="get-the-offline-company-portal-app"></a>오프라인 회사 포털 앱 가져오기
1. **회사 포털** 앱을 검색하고 선택합니다.
2. **라이선스 유형**을 **오프라인**으로 설정합니다.
3. **앱 가져오기**를 선택하여 오프라인 회사 포털 앱을 가져와 인벤토리에 추가합니다.

## <a name="assign-the-company-portal-app"></a>회사 포털 앱 할당
1. 관리자 계정으로  [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다. 
2. 오른쪽 창에서  **앱** 탭을 선택합니다. 
3.  **플랫폼별**에서 **Windows**를 선택합니다. 
4.  **회사 포털(오프라인)** 을 선택합니다.   
5. 동기화 일정이 완료될 때까지 기다리거나 Microsoft Endpoint Manager 관리 센터에서 수동 동기화를 수행해야 합니다.
6. 선택한 Autopilot 디바이스 그룹에 회사 포털 앱을 필수 앱으로 할당합니다.

## <a name="next-steps"></a>다음 단계

- 앱 할당에 대한 자세한 내용은 [그룹에 앱 할당](apps-deploy.md)을 참조하세요.

