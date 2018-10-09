---
title: Microsoft Intune을 사용한 Lookout MTD 커넥터
titlesuffix: ''
description: 회사 리소스에 대한 모바일 장치 액세스를 제어하기 위해 Lookout MTD(모바일 위협 방어)를 사용하여 Intune을 통합하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/09/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a10c392f91c3c2992f1eebf8e71814520fbb4aa0
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231936"
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Intune과 Lookout 모바일 위협 방어 커넥터

Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Lookout에서 수행한 위험 평가에 따라 회사 리소스에 대한 모바일 장치의 액세스를 제어할 수 있습니다. 위험은 다음을 비롯하여 Lookout 서비스를 통해 장치에서 수집된 원격 분석에 따라 평가됩니다.
- 운영 체제 취약점
- 설치된 악성 앱
- 악성 네트워크 프로필

Intune 준수 정책을 통해 사용하도록 설정된 Lookout의 위험 평가에 따라 조건부 액세스 정책을 구성할 수 있습니다. 설정을 통해 감지된 위협에 따라 검색 비규격 장치를 허용하거나 차단할 수 있습니다.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>Intune과 Lookout Mobile Threat Defense가 회사 리소스를 보호하는 데 어떤 도움이 되나요?
Lookout의 모바일 앱인 **Lookout for Work**가 모바일 장치에서 설치되어 실행됩니다. 이 앱은 파일 시스템, 네트워크 스택, 장치 및 앱 원격 분석(사용 가능한 경우)을 캡처한 다음, Lookout 클라우드 서비스로 보내 모바일 위협에 대한 장치의 위험을 평가합니다. 요구 사항에 맞게 Lookout 콘솔에서 위협에 대한 위험 수준 분류를 변경할 수 있습니다.  

Intune의 준수 정책에는 Lookout 위험 평가를 기반으로 하는 Lookout Mobile Threat Defense에 대한 규칙이 포함되어 있습니다. 이 규칙을 사용하면 Intune에서 장치가 사용되는 정책을 준수하는지를 평가합니다.

장치는 정책을 준수하지 않으면 Exchange Online, SharePoint Online 등의 리소스에 대한 액세스가 차단될 수 있습니다. 차단된 장치의 사용자는 문제를 해결하고 다시 액세스하는 단계에 대한 지침을 받습니다. 지침은 Lookout for Work 앱에서 실행됩니다.

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
맬웨어와 같은 악성 앱이 장치에서 감지되면 위협이 해결될 때까지 다음으로부터 장치를 차단할 수 있습니다.
* 회사 메일에 연결
* 작업용 OneDrive 앱과 회사 파일 동기화
* 회사 앱에 액세스

**악성 앱이 발견되면 액세스 차단:**

![장치의 악성 앱으로 인해 장치가 비규격으로 확인되면 액세스를 차단하는 조건부 액세스 정책을 보여 주는 다이어그램](./media/malicious-apps-blocked.png)

**수정 시 액세스 권한 부여됨:**

![해결 후 장치가 규정을 준수하는 것으로 확인되면 조건부 액세스 정책을 통해 액세스를 부여하는 모습을 나타낸 다이어그램](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어
메시지 가로채기(man-in-the-middle) 공격과 같은 사용자 네트워크 위협을 검색하고 장치 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.

**Wi-Fi를 통한 네트워크 액세스 차단:**

![네트워크 위협에 따라 WiFi 액세스를 차단하는 조건부 액세스를 보여 주는 다이어그램](./media/network-wifi-blocked.png)

**수정 시 액세스 권한 부여됨:**

![위협 해결 시 조건부 액세스를 통해 액세스를 허용하는 모습을 나타낸 다이어그램](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 SharePoint Online에 대한 액세스 제어

메시지 가로채기(man-in-the-middle) 공격 같은 네트워크에 대한 위협을 감지하여, 장치 위험에 따라 회사 파일 동기화를 금지합니다.

**네트워크 위협이 감지할 경우 SharePoint Online 차단:**

![발견된 위협에 따라 조건부 액세스를 통해 SharePoint Online에 대한 장치의 액세스를 차단하는 모습을 나타낸 다이어그램](./media/network-spo-blocked.png)


**수정 시 액세스 권한 부여됨:**

![네트워크 위협이 수정된 후 액세스를 허용하는 조건부 액세스를 보여 주는 다이어그램](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>다음 단계
이 솔루션을 구현하기 위해 수행해야 하는 주요 단계는 다음과 같습니다.
1.  [Lookout 통합 설정](lookout-mtd-connector-integration.md)
2.  [Intune에서 Lookout Mobile Threat Defense를 사용하도록 설정](mtd-connector-enable.md)
3.  [Lookout for Work 앱 추가 및 할당](mtd-apps-ios-app-configuration-policy-add-assign.md)
4.  [Lookout 장치 준수 정책 구성](mtd-device-compliance-policy-create.md)
