---
title: Intune을 사용하여 Wandera 모바일 보안 설정
titleSuffix: Intune on Azure
description: Microsoft Intune을 사용하여 Wandera 모바일 보안을 설정하여 회사 리소스의 모바일 디바이스 액세스를 제어하는 방법입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4043ddc2a9f960b30e753c24e0b806e72b6850c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728288"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Intune과 Wandera Mobile Threat Defense 커넥터 사용  

Wandera에서 수행한 위험 평가를 기반으로 조건부 액세스를 사용하여 회사 리소스에 대한 모바일 디바이스의 액세스를 제어하세요. Wandera는 Microsoft Intune과 통합된 MTD(모바일 위협 방어) 솔루션입니다.  위험은 다음을 비롯하여 Wandera 서비스를 통해 디바이스에서 수집된 원격 분석에 따라 평가됩니다.
- 운영 체제 취약점
- 설치된 악성 앱
- 악성 네트워크 프로필
- Cryptojacking

Intune 디바이스 규정 준수 정책을 통해 사용하도록 설정된 Wandera 위험 평가에 따라 ‘조건부 액세스’ 정책을 구성할 수 있습니다.  위험 평가 정책은 비규격 디바이스가 감지한 위협에 따라 회사 리소스에 액세스하는 것을 허용하거나 차단할 수 있습니다.  


## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Intune과 Wandera Mobile Threat Defense가 회사 리소스를 보호하는 데 어떤 도움이 되나요?  

Wandera의 모바일 앱은 Microsoft Intune을 사용하여 원활하게 설치됩니다. 이 앱은 사용 가능한 경우 파일 시스템, 네트워크 스택, 디바이스, 애플리케이션 원격 분석 데이터를 캡처합니다. 이 정보를 Wandera 클라우드 서비스에 동기화하여 디바이스가 모바일 위협을 받을 위험을 평가합니다. 이러한 위험 수준 분류는 Wandera 콘솔 RADAR에서 필요에 맞게 구성할 수 있습니다.

Intune의 준수 정책에는 Wandera의 위험 평가를 기반으로 한 MTD에 대한 규칙이 포함되어 있습니다. 이 규칙을 사용하면 Intune에서 디바이스가 사용되는 정책을 준수하는지를 평가합니다.

준수하지 않는 디바이스의 경우 Office 365와 같은 리소스에 대한 액세스가 차단될 수 있습니다. 차단된 디바이스의 사용자는 문제를 해결하고 액세스 권한을 다시 얻을 수 있도록 Wandera 앱에서 지침을 받습니다.

## <a name="supported-platforms"></a>지원되는 플랫폼  

Intune에 등록한 경우 다음과 같은 플랫폼에서 Wandera가 지원됩니다.

- Android 5.0 이상  
- iOS 10.2 이상  

플랫폼 및 디바이스에 대한 자세한 내용은 [Wandera 웹 사이트](https://www.wandera.com/why-wandera/features/device-support/)를 참조하세요.

## <a name="prerequisites"></a>전제 조건  

- Microsoft Intune 구독  
- Azure Active Directory  
- Wandera Mobile Threat Defense(이전의 Wandera Secure)  

자세한 내용은 [Wandera 모바일 보안](https://www.wandera.com/mobile-security/)을 참조하세요.
 
## <a name="sample-scenarios"></a>샘플 시나리오:

Intune과 함께 Wandera MTD를 사용할 때의 일반적인 시나리오는 다음과 같습니다.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어  

맬웨어와 같은 악성 앱이 디바이스에서 감지되면 위협이 해결될 때까지 일반 도구에서 디바이스를 차단할 수 있습니다. 일반 차단에는 다음이 포함됩니다.  
- 회사 메일에 연결  
- 작업용 OneDrive 앱과 회사 파일 동기화  
- 회사 앱에 액세스  

**악성 앱이 발견되면 액세스 차단:**

![감지된 악성 앱의 개념 이미지](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**수정 시 액세스 권한 부여됨**: 

![업데이트 관리 후 부여된 액세스 권한의 개념 이미지](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어  

중간자(man-in-the-middle) 공격과 같은 사용자 네트워크 위협을 검색하고 디바이스 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.  

**Wi-Fi를 통한 네트워크 액세스 차단**:  

![Wi-Fi를 통한 네트워크 액세스 차단](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**수정 시 액세스 권한 부여됨**:  

![수정 시 액세스 권한 부여됨](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 SharePoint Online에 대한 액세스 제어

메시지 가로채기(man-in-the-middle) 공격 같은 네트워크에 대한 위협을 감지하여, 디바이스 위험에 따라 회사 파일 동기화를 금지합니다.

**네트워크 위협이 감지되면 SharePoint Online 차단**:  

![네트워크 위협이 감지되면 SharePoint Online 차단](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**수정 시 액세스 권한 부여됨**:  

![SharePoint에 대해 수정 시 액세스 권한이 부여된 예](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>다음 단계

- [Wandera와 Intune 통합](wandera-mtd-connector-integration.md)
- [Wandera 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Wandera 디바이스 준수 정책 만들기](mtd-device-compliance-policy-create.md)
- [Wandera MTD 커넥터 사용](mtd-connector-enable.md)