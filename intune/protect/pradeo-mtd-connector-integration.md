---
title: Intune과 Pradeo 통합 설정
titleSuffix: Intune on Azure
description: Intune과 Pradeo 커넥터 통합
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 32e67ac961f2831a881bc160e19cefdb75723ff0
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72681247"
---
# <a name="integrate-pradeo-mobile-threat-defense-with-intune"></a>Pradeo Mobile Threat Defense와 Intune 통합

Intune과 Pradeo Mobile Threat Defense 솔루션을 통합하려면 다음 단계를 완료하세요.

> [!NOTE]  
> 이 Mobile Threat Defense 공급업체는 등록되지 않은 디바이스에서 지원되지 않습니다.

## <a name="before-you-begin"></a>시작하기 전에

> [!NOTE]
> [Pradeo Security 콘솔](https://www.apps-security.com)에서 다음 단계를 완료해야 합니다.

Intune과 Pradeo을 통합하는 과정을 시작하기 전에 다음 항목이 있는지 확인합니다.

- Microsoft Intune 구독

- 다음 권한을 부여할 Azure Active Directory 관리자 자격 증명

  - 로그인 및 사용자 프로필 읽기

  - 로그인한 사용자로 디렉터리에 액세스

  - 디렉터리 데이터 읽기

  - Intune에 디바이스 정보 보내기

- Pradeo Security 콘솔에 액세스하기 위한 관리자 자격 증명.

### <a name="pradeo-app-authorization"></a>Pradeo 앱 권한 부여

Pradeo 앱 권한 부여 프로세스는 다음과 같습니다.

- Pradeo 서비스에서 디바이스 상태와 관련된 정보를 Intune으로 다시 전달하도록 허용합니다.

- Pradeo는 Azure AD 등록 그룹 멤버 자격과 동기화하여 해당 디바이스의 데이터베이스를 채웁니다.

- Pradeo 관리 콘솔에서 Azure AD SSO(Single Sign On)를 사용하도록 허용합니다.

- Pradeo 앱에서 Azure AD SSO를 사용하여 로그인하도록 허용합니다.

## <a name="to-set-up-pradeo-integration"></a>Pradeo 통합을 설정하려면

1. [Pradeo Security 콘솔](https://www.apps-security.com)로 이동하여 자격 증명으로 로그인합니다.

2. 메뉴에서 **관리 - Enterprise Mobility Management**를 선택합니다.

3. **Intune 로고**를 선택합니다.

4. **EMM(엔터프라이즈 이동성 관리) - Intune** 창의 **1단계** 아래에서 **Pradeo Connector** 단추를 선택합니다. 

    ![Pradeo EMM Intune 창의 스크린샷](./media/pradeo-mtd-connector-integration/pradeo_setup.png)

5. Microsoft Intune 연결 창에서 Intune 자격 증명을 입력합니다.

5. Pradeo 웹 페이지가 다시 열립니다. **2단계** 아래에서 **Pradeo 디바이스 상태** 단추를 선택합니다.

7. Pradeo-Intune Connector 창에서 **동의**를 선택합니다. 

8. Pradeo 디바이스 API 커넥터 창에서 **동의**를 선택합니다.

9. Pradeo 웹 페이지가 다시 열립니다. **3단계** 아래에서 **Microsoft에 연결** 단추를 선택합니다. 

10. Microsoft Intune 인증 창에서 Intune 자격 증명을 입력합니다.

11. **통합 성공** 메시지가 나타나면 통합이 완료된 것입니다.

## <a name="next-steps"></a>다음 단계

- [등록된 디바이스용 Pradeo 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)
