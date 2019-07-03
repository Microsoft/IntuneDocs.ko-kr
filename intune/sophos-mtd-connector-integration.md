---
title: Intune과 Sophos Mobile 통합 설정
titleSuffix: Intune on Azure
description: 회사 리소스에 대한 모바일 디바이스 액세스를 제어하기 위해 Microsoft Intune을 사용하여 Sophos Mobile 솔루션을 설정하는 방법입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec60a618280caf6a5b7ef242c192cc64b5d839de
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67511916"
---
# <a name="integrate-sophos-mobile-with-intune"></a>Intune과 Sophos Mobile 통합  

Intune과 Sophos Mobile Threat Defense 솔루션을 통합하려면 다음 단계를 완료하세요.  

## <a name="before-you-begin"></a>시작하기 전에  

Intune과 Sophos Mobile을 통합하는 과정을 시작하기 전에 다음 항목이 있는지 확인합니다.  
- Microsoft Intune 구독  
- 다음 권한을 부여할 Azure Active Directory 관리자 자격 증명  
  - 로그인 및 사용자 프로필 읽기  
  - 로그인한 사용자로 디렉터리에 액세스  
  - 디렉터리 데이터 읽기  
  - Intune에 디바이스 정보 보내기  
- Sophos Mobile 관리 콘솔에 액세스하기 위한 관리자 자격 증명  


### <a name="sophos-mobile-app-authorization"></a>Sophos Mobile 앱 권한 부여  
  
Sophos Mobile 앱 권한 부여 프로세스는 다음과 같습니다.  
- Sophos Mobile 서비스에서 디바이스 상태와 관련된 정보를 Intune으로 다시 전달하도록 허용합니다.  
- Sophos Mobile은 Azure AD 등록 그룹 멤버 자격과 동기화하여 해당 디바이스의 데이터베이스를 채웁니다.  
- Sophos Mobile 관리 콘솔에서 Azure AD SSO(Single Sign On)를 사용하도록 허용합니다.  
- Sophos Mobile 앱에서 Azure AD SSO를 사용하여 로그인하도록 허용합니다.  


## <a name="to-set-up-sophos-mobile-integration"></a>Sophos Mobile 통합을 설정하려면  

1. [Azure Portal]( https://portal.azure.com/)에 로그인하고 **Intune** > **디바이스 규정 준수** > **Mobile Threat Defense**로 이동한 다음, **추가**를 선택합니다.  
2. **커넥터 추가** 페이지에서 드롭다운을 사용하여 **Sophos**를 선택합니다. 그런 다음, **만들기**를 선택합니다.  
3. *Sophos 관리자 콘솔 열기* 링크를 선택합니다.  
4. Sophos 자격 증명을 사용하여 [Sophos 관리자 콘솔](https://central.sophos.com/)에 로그인합니다.  
5. **모바일** > **설정** > **설치** > **Sophos 설치**로 이동합니다.  
6. **Sophos 설치** 페이지에서 **Intune MTD** 탭을 선택합니다.  
   ![Sophos 설치](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. **바인딩**을 선택한 다음, **예**를 선택합니다. Sophos가 Intune에 연결하며 Intune 구독 로그인을 요청합니다. 
8. Microsoft Intune 인증 창에서 Intune 자격 증명을 입력하고 *Sophos Mobile Thread Defense*에 대한 권한 요청을 **승인**합니다.  
   ![Intune 인증](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. **Sophos 설치** 페이지에서 **저장**을 선택하여 Intune에 대한 구성을 완료합니다.  
   ![Sophos 설치 저장](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. **통합 성공** 메시지가 나타나면 통합이 완료된 것입니다.  
1. 이제 Intune 콘솔에서 Sophos를 사용할 수 있습니다.  


## <a name="next-steps"></a>다음 단계  
[Sophos 클라이언트 앱 구성](mtd-apps-ios-app-configuration-policy-add-assign.md)
