---
title: Microsoft Intune을 사용한 Lookout MTD 커넥터
titleSuffix: Microsoft Intune
description: 회사 리소스에 대한 모바일 디바이스 액세스를 제어하기 위해 Lookout MTD(모바일 위협 방어)를 사용하여 Intune을 통합하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/09/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cf507ba470013bddf4809b6ad6ad54b4cb52d9d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61507293"
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Intune과 Lookout 모바일 위협 방어 커넥터

Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Lookout에서 수행한 위험 평가에 따라 회사 리소스에 대한 모바일 디바이스의 액세스를 제어할 수 있습니다. 위험은 다음을 비롯하여 Lookout 서비스를 통해 디바이스에서 수집된 원격 분석에 따라 평가됩니다.
- 운영 체제 취약점
- 설치된 악성 앱
- 악성 네트워크 프로필

Intune 준수 정책을 통해 사용하도록 설정된 Lookout의 위험 평가에 따라 조건부 액세스 정책을 구성할 수 있습니다. 설정을 통해 감지된 위협에 따라 검색 비규격 디바이스를 허용하거나 차단할 수 있습니다.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>Intune과 Lookout Mobile Threat Defense가 회사 리소스를 보호하는 데 어떤 도움이 되나요?
Lookout의 모바일 앱인 **Lookout for Work**가 모바일 디바이스에서 설치되어 실행됩니다. 이 앱은 파일 시스템, 네트워크 스택, 디바이스 및 앱 원격 분석(사용 가능한 경우)을 캡처한 다음, Lookout 클라우드 서비스로 보내 모바일 위협에 대한 디바이스의 위험을 평가합니다. 요구 사항에 맞게 Lookout 콘솔에서 위협에 대한 위험 수준 분류를 변경할 수 있습니다.  

Intune의 준수 정책에는 Lookout 위험 평가를 기반으로 하는 Lookout Mobile Threat Defense에 대한 규칙이 포함되어 있습니다. 이 규칙을 사용하면 Intune에서 디바이스가 사용되는 정책을 준수하는지를 평가합니다.

디바이스는 정책을 준수하지 않으면 Exchange Online, SharePoint Online 등의 리소스에 대한 액세스가 차단될 수 있습니다. 차단된 디바이스의 사용자는 문제를 해결하고 다시 액세스하는 단계에 대한 지침을 받습니다. 지침은 Lookout for Work 앱에서 실행됩니다.

## <a name="supported-platforms"></a>지원되는 플랫폼
Intune에 등록한 경우 다음과 같은 플랫폼에서 Lookout이 지원됩니다.
* **Android 4.1 이상**
* **iOS 8 이상** 플랫폼 및 언어 지원에 대한 자세한 내용은 [Lookout 웹 사이트](https://personal.support.lookout.com/hc/articles/114094140253)를 참조하세요.

## <a name="prerequisites"></a>전제 조건
* Microsoft Intune 구독
* Azure Active Directory
* Lookout Mobile EndPoint Security 엔터프라이즈 구독  

자세한 내용은 [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)를 참조하세요.

## <a name="sample-scenarios"></a>샘플 시나리오

Intune과 함께 Lookout Mobile Threat Defense를 사용할 때의 일반적인 시나리오는 다음과 같습니다.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어
맬웨어와 같은 악성 앱이 디바이스에서 감지되면 위협이 해결될 때까지 다음으로부터 디바이스를 차단할 수 있습니다.
* 회사 메일에 연결
* 작업용 OneDrive 앱과 회사 파일 동기화
* 회사 앱에 액세스

**악성 앱이 발견되면 액세스 차단:**

![악성 앱으로 인해 액세스를 차단하는 정책의 개념 이미지](./media/malicious-apps-blocked.png)

**수정 시 액세스 권한 부여됨:**

![업데이트 관리 후 디바이스에 부여된 액세스 권한을 보여주는 개념 이미지](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어
메시지 가로채기(man-in-the-middle) 공격과 같은 사용자 네트워크 위협을 검색하고 디바이스 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.

**Wi-Fi를 통한 네트워크 액세스 차단:**

![네트워크 위협에 따라 WiFi 액세스 차단을 보여주는 이미지](./media/network-wifi-blocked.png)

**수정 시 액세스 권한 부여됨:**

![업데이트 관리 후 액세스를 허용하는 조건부 액세스의 개념 이미지](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 SharePoint Online에 대한 액세스 제어

메시지 가로채기(man-in-the-middle) 공격 같은 네트워크에 대한 위협을 감지하여, 디바이스 위험에 따라 회사 파일 동기화를 금지합니다.

**네트워크 위협이 감지할 경우 SharePoint Online 차단:**

![SharePoint Online에 대한 액세스 차단의 개념 이미지](./media/network-spo-blocked.png)


**수정 시 액세스 권한 부여됨:**

![네트워크 위협이 해결된 후 액세스를 허용하는 개념 이미지](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>다음 단계
이 솔루션을 구현하기 위해 수행해야 하는 주요 단계는 다음과 같습니다.
1.  [Lookout 통합 설정](lookout-mtd-connector-integration.md)
2.  [Intune에서 Lookout Mobile Threat Defense를 사용하도록 설정](mtd-connector-enable.md)
3.  [Lookout for Work 앱 추가 및 할당](mtd-apps-ios-app-configuration-policy-add-assign.md)
4.  [Lookout 디바이스 준수 정책 구성](mtd-device-compliance-policy-create.md)
