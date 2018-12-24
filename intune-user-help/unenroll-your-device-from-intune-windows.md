---
title: Intune 관리에서 Windows 디바이스 제거
description: Intune 관리에서 Windows 디바이스를 제거하는 방법 설명
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 5984ac8ebe825a187b33945699a5fadc27e0c0cc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828417"
---
# <a name="remove-your-windows-device-from-management"></a>관리에서 Windows 디바이스 제거

더 이상 다음이 필요하지 않을 경우 관리에서 등록된 Windows 디바이스를 제거합니다.  
* 회사 또는 학교용 디바이스 사용 
* 회사 또는 학교 메일, 앱 또는 기타 리소스에 액세스

디바이스를 등록 해제하면 해당 디바이스에서 학교 또는 회사 리소스에 액세스할 수 없습니다. 관리에서 다음 Windows 디바이스를 제거할 수 있습니다.  
* Windows 10 디바이스 
* Windows 8.1 컴퓨터
* Windows 8.1 휴대폰
 
관리에서 디바이스를 제거한 후 발생하는 상황에 대한 자세한 내용은 [Intune에서 디바이스를 제거하면 어떻게 되나요?](what-happens-if-you-unenroll-your-device-from-intune-windows.md)를 참조하세요.  

## <a name="remove-your-windows-10-device"></a>Windows 10 디바이스 제거
관리에서 Windows 10 디바이스를 제거하려면 다음 단계를 완료합니다.

### <a name="remove-in-company-portal-app-home-page"></a>회사 포털 앱, **홈**페이지에서 제거  

1. 회사 포털 앱을 엽니다.
2. **홈페이지**에서 **내 장치** 섹션으로 이동합니다.
3. 제거할 디바이스를 선택합니다.
3. 앱 오른쪽 위 모서리에서 **자세히 보기** 아이콘을 선택합니다.
4. **제거**를 선택합니다. 
5. 디바이스 제거를 확인하려면 **제거**를 선택합니다.  

### <a name="remove-in-company-portal-app-device-context-menu"></a>회사 포털 앱, 디바이스 상황에 맞는 메뉴에서 제거  

1. 회사 포털 앱을 열고 **내 디바이스**로 이동합니다.

    ![Windows용 회사 포털 앱, 홈페이지, 내 디바이스 섹션이 강조 표시된 예제 스크린샷](./media/1809_CheckAccess_Context_Select_Device.png)

2. 마우스 오른쪽 단추를 클릭하거나 디바이스를 길게 눌러 해당 [상황에 맞는 메뉴](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus)를 엽니다.  

3. **제거**를 선택합니다.  

    ![Windows용 회사 포털 앱, 홈페이지 예제 스크린샷 디바이스 상황에 맞는 메뉴는 페이지의 **내 디바이스** 섹션에 표시되며 “이름 바꾸기”, “제거” 및 “액세스 권한 확인” 작업을 표시합니다.](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. 확인에서 **자세한 정보**를 클릭하여 회사 및 학교 리소스에 대한 액세스 권한을 변경하는 방법을 알아봅니다. 디바이스 제거를 확인하려면 **제거**를 선택합니다.   

     ![Windows용 회사 포털 앱, 홈페이지 예제 스크린샷 사용자가 새 이름을 입력하고 이름 바꾸기 또는 취소를 클릭할 수 있는 디바이스에 대한 이름 바꾸기 필드가 나타납니다.](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>디바이스 설정 앱에서 제거
1. 설정 앱을 엽니다. 
2. **계정** > **회사 또는 학교 액세스**를 선택합니다.
3. 제거할 연결된 계정을 선택한 다음, **연결 끊기**를 선택합니다.
4. 디바이스 제거를 확인하려면 **예**를 선택합니다.

## <a name="remove-your-windows-81-computer"></a>Windows 8.1 컴퓨터 제거
Intune에서 Windows 8.1 컴퓨터를 제거하려면 다음 단계를 완료합니다.

1.  **PC 설정** > **네트워크** > **작업 공간**으로 이동합니다.
2.  **작업 공간 연결**에서 **나가기**를 선택합니다.
3.  **장치 관리 설정**에서 **끄기**를 선택합니다.
4.  팝업 창이 열리면 **해제**를 선택합니다.

## <a name="remove-your-windows-81-phone"></a>Windows 8.1 휴대폰 제거
Intune에서 Windows 8.1 휴대폰을 제거하려면 다음 단계를 완료합니다.

1.  **설정** > **작업 공간**으로 이동합니다.
2.  등록을 취소할 작업 공간 계정을 탭합니다.
3.  화면 맨 아래에서 **삭제**를 탭합니다.
4.  **계정 삭제** 대화 상자에서 **삭제**를 탭합니다.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>회사 포털을 제거한 후 개인 정보 제거  

회사 포털이 Windows 디바이스에 저장하는 두 종류의 데이터가 있습니다.

-   **진단 로그**: Microsoft에서 수집하는 표준 앱 작업 데이터입니다. 회사 포털 앱을 제거하면 자동으로 삭제됩니다. 예를 들어 앱 활동 데이터는 앱이 얼마나 오래 열려 있었는지 또는 작동 중단되었는지에 대한 데이터입니다.
-   **응용 프로그램 캐시**: 아이콘 및 설정과 같이 앱 작동에 필요한 지원 파일입니다.

저장된 로그 및 캐시를 삭제하려면 다음 단계 중 하나를 수행합니다.

* [회사 포털 앱 제거](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* 회사 포털 앱을 다시 설정합니다. **설정** 앱을 열고 **앱** > **회사 포털** > **고급 옵션** > **초기화**를 선택합니다. 

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
