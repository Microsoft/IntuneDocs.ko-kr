---
title: Intune과 Pradeo Mobile Threat Defense 커넥터
titleSuffix: Intune on Azure
description: Intune과 Pradeo Mobile Threat Defense 커넥터를 설정합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
ms.openlocfilehash: 784d51822425decc900e8a4ae0d348291f0a0c88
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232157"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>Intune과 Pradeo Mobile Threat Defense 커넥터

Microsoft Intune과 통합된 MTD(Mobile Threat Defense) 솔루션인 Pradeo에서 수행된 위험 평가에 따라 조건부 액세스를 사용하여 모바일 장치에서 회사 리소스에 대한 액세스를 제어할 수 있습니다. 위험은 Pradeo 앱을 실행하는 장치에서 수집된 원격 분석에 기반하여 평가됩니다.

Intune 장치 준수 정책을 통해 사용하도록 설정된 Pradeo 위험 평가에 따라 조건부 액세스 정책을 구성할 수 있습니다. 이 정책을 사용하여 회사 리소스에 액세스하는 비규격 장치를 감지된 위협에 따라 허용하거나 차단할 수 있습니다.

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>Intune과 Pradeo가 회사 리소스를 보호하는 데 어떤 도움이 되나요?

Android 및 iOS용 Pradeo 앱은 사용 가능한 경우 파일 시스템, 네트워크 스택, 장치 및 응용 프로그램 원격 분석을 캡처한 다음, 원격 분석 데이터를 Pradeo 클라우드 서비스로 보내 모바일 위협에 대한 장치의 위험을 평가합니다.

Intune 장치 준수 정책에는 Pradeo 위험 평가에 기반을 둔 Pradeo Mobile Threat Defense에 대한 규칙이 포함되어 있습니다. 이 규칙을 사용하면 Intune에서 장치가 사용되는 정책을 준수하는지를 평가합니다. 장치가 정책을 준수하지 않으면 Exchange Online, SharePoint Online 등의 회사 리소스에 대한 사용자의 액세스가 차단됩니다. 또한 사용자는 장치에 설치된 Pradeo 앱에서 지침을 받아 문제를 해결하고 회사 리소스에 대한 액세스 권한을 다시 얻을 수 있습니다.

## <a name="sample-scenarios"></a>샘플 시나리오:

다음은 몇 가지 일반적인 시나리오입니다.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어

맬웨어와 같은 악성 앱이 장치에서 감지되면 위협이 해결될 때까지 장치에서 다음 작업을 차단할 수 있습니다.

-   회사 메일에 연결

-   작업용 OneDrive 앱과 회사 파일 동기화

-   회사 앱에 액세스

**악성 앱이 발견되면 액세스 차단:**

![감지된 악성 앱](./media/pradeo_maliciousapps_blocked.png)

**수정 시 액세스 권한 부여됨:**

![감지된 악성 앱에 액세스 권한 부여됨](./media/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어

**메시지 가로채기(man-in-the-middle)** 공격과 같은 사용자 네트워크 위협을 검색하고 장치 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.

**Wi-Fi를 통한 네트워크 액세스 차단:**

![Wi-Fi를 통한 네트워크 액세스 차단](./media/pradeo_network_wifi_blocked.png)

**수정 시 액세스 권한 부여됨:**

![수정 시 액세스 권한 부여됨](./media/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 SharePoint Online에 대한 액세스 제어

**메시지 가로채기(man-in-the-middle)** 공격 같은 네트워크에 대한 위협을 감지하여, 장치 위험에 따라 회사 파일 동기화를 금지합니다.

**네트워크 위협이 감지할 경우 SharePoint Online 차단:**

![네트워크 위협이 감지되면 SharePoint Online 차단](./media/pradeo_network_spo_blocked.png)

**수정 시 액세스 권한 부여됨:**

![SharePoint에 대해 수정 시 액세스 권한이 부여된 예](./media/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>지원되는 플랫폼

-   **Android 4.0.3 이상**

-   **iOS 7 이상**

## <a name="prerequisites"></a>전제 조건

-   Azure Active Directory Premium

-   Microsoft Intune 구독

-   Pradeo Security for Mobile Threat Defense 구독

    -   자세한 내용은 [Pradeo 웹 사이트](https://www.pradeo.com/en-US/mobile-threat-protection)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [Intune과 Pradeo 통합](pradeo-mtd-connector-integration.md)

- [Pradeo 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Pradeo 장치 준수 정책 만들기](mtd-device-compliance-policy-create.md)

- [Pradeo MTD 커넥터 사용](mtd-connector-enable.md)