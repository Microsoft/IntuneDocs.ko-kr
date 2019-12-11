---
title: 수동으로 Windows 디바이스 동기화 | Microsoft 문서
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 289d99603314be7c1097d54d59d4a0e90cae0bed
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508340"
---
# <a name="sync-your-windows-device-manually"></a>수동으로 Windows 디바이스 동기화

앱 설치 속도가 최적 속도보다 느린 경우 수동 디바이스 동기화를 시작합니다. 수동 동기화는 최신 업데이트 및 통신을 위해 디바이스를 Intune과 강제로 연결합니다. 디바이스 동기화가 완료된 후에 설치 속도가 증가할 수 있습니다.

Intune은 회사 포털 앱, 바탕 화면 작업 표시줄 또는 시작 메뉴 및 디바이스 설정 앱에서 수동 동기화를 지원합니다. 회사 포털 앱 기능은 크리에이터스 업데이트(1703) 이상을 실행하는 Windows 10 디바이스에서 지원됩니다. 

모든 Windows 디바이스는 다음을 포함한 디바이스 설정 앱에서 동기화할 수 있습니다.

* [Windows 10 Desktop](#windows-10-desktop)  
* [Microsoft HoloLens](#microsoft-hololens)   
* [Windows 10 Mobile](#windows-10-mobile)  
* [Windows Phone 8.1](#windows-phone-81)    

## <a name="sync-directly-from-company-portal-app-for-windows"></a>Windows용 회사 포털 앱에서 직접 동기화
크리에이터스 업데이트(버전 1703) 이상을 실행하는 Windows 10 디바이스를 수동으로 동기화하려면 다음 단계를 완료합니다.

1. 디바이스에서 회사 포털 앱을 엽니다.

2. **설정** > **동기화**를 선택합니다.

    ![회사 포털 앱의 홈페이지 스크린샷, 설정 강조 표시됨](./media/RS1_homePage_settings_04.png)  
    
    ![회사 포털 앱의 설정 페이지 스크린샷, 동기화 단추 강조 표시됨](./media/RS1_settingspage_sync05.png)  

## <a name="sync-from-device-taskbar-or-start-menu"></a>디바이스 작업 표시줄 또는 시작 메뉴에서 동기화   

디바이스의 바탕 화면에서 앱 외부의 동기화 컨트롤에 액세스할 수도 있습니다. 이 방법은 앱이 작업 표시줄 또는 시작 메뉴에 직접 고정되어 있고 빠르게 동기화하려는 경우에 유용합니다.  

1. 작업 표시줄 또는 시작 메뉴에서 회사 포털 앱 아이콘을 찾습니다.  
2. 해당 메뉴(점프 목록이라고도 함)가 표시되도록 앱의 아이콘을 마우스 오른쪽 단추로 클릭합니다.  

    ![디바이스의 바탕 화면에 있는 Windows 작업 표시줄의 스크린샷입니다. 회사 포털 앱 아이콘을 클릭하여 "작업 표시줄에 고정", "창 닫기" 및 "이 디바이스 동기화" 작업 옵션이 있는 메뉴를 표시했습니다.](./media/sync-device-from-start-menu-1807.png)  

3. **이 디바이스 동기화**를 선택합니다. 회사 포털 앱에서 **설정** 페이지가 열리고 동기화가 시작됩니다.  

## <a name="sync-from-settings-app"></a>설정 앱에서 동기화 
설정 앱에서 Microsoft HoloLens, Windows 10 desktop, Windows 10 Mobile 또는 Windows Phone 8.1 디바이스를 수동으로 동기화하려면 다음 단계를 완료합니다.  

### <a name="windows-10-desktop"></a>Windows 10 Desktop
1. 디바이스에서 **시작** > **설정**을 선택합니다.

2. **계정**을 선택합니다.

    ![설정 페이지에서 계정 선택](./media/win10pc-sync-2-settings-accounts.png)  

3. 데스크톱용 Windows 10은 버전이 여러 개 있습니다. 아래 스크린샷과 화면을 비교하여 수행할 일련의 단계를 확인합니다. 

    * 화면에 **회사 또는 학교 액세스**가 표시되면 [회사 또는 학교 액세스](#access-work-or-school-steps)의 단계로 건너뜁니다.

    ![설정 앱의 회사 또는 학교 액세스 옵션](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

    * 화면에 **회사 액세스**가 표시되면 [회사 액세스](#work-access-steps) 아래의 단계로 건너뜁니다.  

    ![계정 유형으로 회사 액세스 선택](./media/win10pc-sync-3-work-access.png)

#### <a name="access-work-or-school-steps"></a>회사 또는 학교 액세스

1. **회사 또는 학교 액세스**를 클릭합니다.

    ![회사 또는 학교 액세스 옵션을 보여주는 스크린샷](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

2. 옆에 서류 가방 아이콘이 있는 계정을 선택합니다. 이 계정이 표시되지 않으면 회사에서 설정을 다른 방식으로 구성했을 수 있습니다. 대신에 옆에 Microsoft 로고가 있는 계정을 클릭합니다.

     ![서류 가방 또는 Microsoft 로고 옆에 있는 계정 이름 선택](./media/win10pc-rs1-sync-info-button.png)

3. **정보**를 클릭합니다. 

4. **동기화**를 클릭합니다. 

#### <a name="work-access-steps"></a>회사 액세스 단계

1. **회사 액세스**를 클릭합니다.

    ![계정 유형으로 회사 액세스 선택](./media/win10pc-sync-3-work-access.png)

2. **디바이스 관리에 등록**에서 회사 이름을 선택합니다.

    ![디바이스 관리에 대한 회사 이름 선택](./media/win10pc-sync-4-tap-com-name.png)

3. **동기화**를 클릭합니다. 동기화가 완료될 때까지 단추를 사용할 수 없습니다.

    ![동기화 단추 선택](./media/win10pc-sync-5-tap-sync.png)  


### <a name="windows-10-mobile"></a>Windows 10 Mobile

   1. 디바이스에서 **모든 앱** > **설정** > **계정**으로 이동합니다.

       ![설정 화면에서 계정 선택](./media/win10m-sync-1-settings-accounts.png)

   2. **회사 액세스**를 선택합니다.

       ![계정 유형으로 회사 액세스 선택](./media/win10m-sync-2-work-access.png)

   3. **디바이스 관리에 등록**에서 회사 이름을 선택합니다.

       ![디바이스 관리에 대한 회사 이름 선택](./media/win10m-sync-3-tap-comp-name.png)

   4. **동기화** 아이콘을 선택합니다. 동기화가 완료될 때까지 단추를 사용할 수 없습니다.

       ![동기화 아이콘 선택](./media/win10m-sync-4-tap-sync.png)  
### <a name="microsoft-hololens"></a>Microsoft HoloLens  
이러한 지침은 Windows 10 1주년 업데이트(RS1이라고도 함)를 실행하는 HoloLens 디바이스에 적용됩니다. 
1. 디바이스에서 설정 앱을 엽니다.  

2. **계정** > **회사 액세스**를 선택합니다.  
    ![HoloLens 설정 앱 스크린샷, 계정 링크 강조 표시됨](./media/RS1_holoLens_SettingsRS1_Accounts_06.png)  

3. 연결된 계정 > **동기화**를 선택합니다.  ![HoloLens 설정 앱 스크린샷, 동기화 단추 강조 표시됨](./media/RS1_holoLens_SyncRS1_Sync_08.png)  

### <a name="windows-phone-81"></a>Windows Phone 8.1

1. **모든 앱** > **설정** > **회사**로 이동합니다.

    ![설정 목록](./media/wp81-1-sync-settings-workplace.png)

2. 회사 이름을 선택합니다.

    ![회사 계정의 회사 이름 선택](./media/wp81-2-sync-tap-compname.png)

3. **동기화** 아이콘을 선택합니다.

    ![동기화 아이콘 선택](./media/wp81-3-sync-tap-sync-button.png)

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
