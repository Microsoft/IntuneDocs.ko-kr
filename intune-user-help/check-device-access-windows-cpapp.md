---
title: 디바이스 액세스 확인 | Microsoft Docs
description: 디바이스 액세스를 확인하여 디바이스가 요구 사항을 충족하고, 회사 또는 학교 리소스에 액세스할 수 있는지 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 0cae5a5e398af77cc626f87f43fb5a21b0489b4e
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857007"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>Windows용 회사 포털 앱에서 액세스 확인

디바이스에서 회사 또는 학교 리소스에 액세스할 수 있는지 확인합니다. 

조직은 암호화 및 암호 제한과 같은 요구 사항을 적용하여 신뢰할 수 있는 보안 디바이스만 데이터에 액세스할 수 있도록 합니다. 관리 디바이스는 조직의 리소스에 액세스하기 위해 이러한 요구 사항을 충족하고 유지 관리해야 합니다.

**액세스 확인** 작업은 디바이스의 설정 및 해당 액세스 상태를 평가합니다. **디바이스 세부 정보** 페이지에는 다시 액세스하기 위해 조정해야 하는 설정이 표시됩니다. 

이 문서의 단계를 완료하여 Windows용 회사 포털 앱에서 액세스를 확인합니다.  

## <a name="check-access-from-device-details-page"></a>디바이스 세부 정보 페이지에서 액세스 확인  
1. Windows용 회사 포털 앱을 열고 **내 디바이스**로 이동합니다.  

    ![Windows용 회사 포털 앱, 홈페이지, 내 디바이스 섹션이 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Context_Select_Device.png)  
2. 디바이스를 선택합니다.  
3. **디바이스 세부 정보** 페이지에서 **액세스 확인**을 선택합니다. 앱은 디바이스를 조직의 현재 요구 사항과 동기화하고 디바이스가 해당 요구 사항과 일치하는지 확인합니다. 이 확인은 몇 분 정도 걸릴 수 있습니다.  

    ![Windows용 회사 포털 앱, 디바이스 세부 정보 페이지, 액세스 확인 단추가 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Checking_Status.png) 

4. 상태 업데이트를 확인합니다. 디바이스가 **조직의 리소스에 액세스할 수 있음**또는**조직의 리소스에 액세스할 수 없음**을 표시합니다.  

   ![Windows용 회사 포털 앱, 디바이스 세부 정보 페이지, 상태 섹션이 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. 디바이스에서 리소스에 액세스할 수 없는 경우 페이지 상단에 있는 경고로 이동합니다. 세부 사항을 확장하려면 **자세히**를 클릭합니다. 축소하려면 **간단히**를 클릭합니다.  

    ![Windows용 회사 포털 앱, 디바이스 세부 정보 페이지, 페이지 상단의 경고가 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Device_details_alert1.png)  

6. 해당되는 경우, 메시지에 추가 도움말 링크 및 수정 작업이 표시됩니다. 문제 해결을 즉시 시작하려면 이러한 옵션 중 하나 이상을 선택합니다. 아래에 설명된 해결, 동기화 및 연락 작업은 영향을 받는 디바이스에서 회사 포털을 사용할 때만 표시됩니다.  

     * **이 문제를 해결하는 방법**은 관련 도움말 문서(사용 가능한 경우)를 엽니다.  
     * **해결**은 디바이스의 설정으로 리디렉션합니다.  
     * **동기화**는 디바이스를 평가하여 조직 요구 사항과 일치하는지 확인합니다.  
     * **IT 담당자**는 IT 팀의 담당자 정보로 리디렉션합니다.   
 
6. 설정을 업데이트한 후 **액세스 확인**을 클릭하여 디바이스의 상태를 확인합니다.  

    ![Windows용 회사 포털 앱, 디바이스 세부 정보 페이지, 상태 섹션이 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>디바이스 상황에 맞는 메뉴에서 액세스 확인  
1. Windows용 회사 포털 앱을 열고 **내 디바이스**로 이동합니다.  

    ![Windows용 회사 포털 앱, 홈페이지, 내 디바이스 섹션이 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Context_Select_Device.png)  

2. 마우스 오른쪽 단추를 클릭하거나 디바이스를 길게 눌러 해당 [상황에 맞는 메뉴](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus)를 엽니다.  

    ![Windows용 회사 포털 앱, 홈페이지 예제 스크린샷 디바이스 상황에 맞는 메뉴는 페이지의 **내 디바이스** 섹션에 표시되며 “이름 바꾸기”, “제거” 및 “액세스 권한 확인” 작업을 표시합니다.](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. **액세스 확인**을 선택합니다. 앱은 디바이스를 조직의 현재 요구 사항과 동기화하고 디바이스가 해당 요구 사항과 일치하는지 확인합니다. 이 확인은 몇 분 정도 걸릴 수 있습니다.  
 
4. 디바이스에서 **회사 리소스에 액세스할 수 있음** 또는 **회사 리소스에 액세스할 수 없음**을 알려 주는 메시지가 디바이스 아래에 나타납니다. 

    ![Windows용 회사 포털 앱, 디바이스 세부 정보 페이지, 상태 섹션이 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. 디바이스에서 리소스에 액세스할 수 없는 경우 해당 디바이스를 선택합니다.  
6. **디바이스 세부 정보** 페이지 맨 위에 있는 경고로 이동합니다. 세부 사항을 확장하려면 **자세히**를 클릭합니다. 축소하려면 **간단히**를 클릭합니다.  

    ![Windows용 회사 포털 앱, 디바이스 세부 정보 페이지, 페이지 상단의 경고가 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Device_details_alert1.png)  

6. 해당되는 경우, 메시지에 추가 도움말 링크 및 수정 작업이 표시됩니다. 문제 해결을 즉시 시작하려면 이러한 옵션 중 하나 이상을 선택합니다. 아래에 설명된 해결, 동기화 및 연락 작업은 영향을 받는 디바이스에서 회사 포털을 사용할 때만 표시됩니다.  

     * **이 문제를 해결하는 방법**은 관련 도움말 문서(사용 가능한 경우)를 엽니다.  
     * **해결**은 디바이스의 설정으로 리디렉션합니다.  
     * **동기화**는 디바이스를 평가하여 조직 요구 사항과 일치하는지 확인합니다.  
     * **IT 담당자**는 IT 팀의 담당자 정보로 리디렉션합니다.    

7. 설정을 업데이트한 후 페이지 하단에 있는 **액세스 확인**을 클릭합니다.  

    ![Windows용 회사 포털 앱, 디바이스 세부 정보 페이지, 액세스 확인 작업이 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Device_details_button.png) 


도움이 더 필요하신가요? 회사 지원팀의 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에서 확인합니다.
