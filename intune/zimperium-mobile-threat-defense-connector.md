---
title: Intune 및 Zimperium MTD 커넥터 통합
titleSuffix: Intune on Azure
description: 회사 리소스에 대한 모바일 장치 액세스를 제어하기 위해 Zimperium MTD(Mobile Threat Defense)와 Intune을 통합하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: aad6687a110642f3b21dc0cff3a791f4714c7949
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187466"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Intune 및 Zimperium MTD(Mobile Threat Defense) 커넥터 통합

Microsoft Intune과 통합되는 MTD(Mobile Threat Defense) 솔루션인 Zimperium에서 수행된 위험 평가에 따라 조건부 액세스를 사용하여 모바일 장치에서 회사 리소스에 대한 액세스를 제어할 수 있습니다. 위험은 Zimperium 앱을 실행하는 장치에서 수집된 원격 분석에 기반하여 평가됩니다.

Intune 장치 준수 정책을 통해 사용하도록 설정된 Zimperium 위험 평가에 따라 조건부 액세스 정책을 구성할 수 있습니다. 이 정책을 사용하여 감지된 위협에 따라 비규격 장치의 회사 리소스에 대한 액세스를 허용하거나 차단할 수 있습니다.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Intune과 Zimperium이 회사 리소스를 어떻게 보호하나요?

Android 및 iOS용 Zimperium 앱은 사용 가능한 경우 파일 시스템, 네트워크 스택, 장치 및 응용 프로그램 원격 분석을 캡처한 다음, 원격 분석 데이터를 Zimperium 클라우드 서비스로 보내 모바일 위협에 대한 장치의 위험을 평가합니다.

Intune 장치 준수 정책에는 Zimperium 위험 평가에 기반한 Zimperium Mobile Threat Defense에 대한 규칙이 포함되어 있습니다. 이 규칙을 사용하면 Intune에서 장치가 사용되는 정책을 준수하는지를 평가합니다. 장치가 정책을 준수하지 않으면 Exchange Online, SharePoint Online 등의 회사 리소스에 대한 사용자의 액세스가 차단됩니다. 또한 사용자는 장치에 설치된 Zimperium 앱에서 지침을 받아 문제를 해결하고 회사 리소스에 대한 액세스 권한을 다시 얻을 수 있습니다.

## <a name="sample-scenarios"></a>샘플 시나리오:

Intune과 Zimperium을 통합하는 경우 아래의 몇 가지 시나리오를 참조하세요.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어

맬웨어와 같은 악성 앱이 장치에서 감지되면 위협이 해결될 때까지 장치를 차단할 수 있습니다.

-   회사 메일에 연결

-   작업용 OneDrive 앱과 회사 파일 동기화

-   회사 앱에 액세스

**악성 앱이 발견되면 액세스 차단:**

![감지된 악성 앱](./media/Maliciousapps_blocked_Zimperium.png)

**수정 시 액세스 권한 부여됨:**

![감지된 악성 앱에 액세스 권한 부여됨](./media/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어

네트워크에서  **메시지 가로채기(Man-in-the-middle)** 와 같은 위협을 감지하고 디바이스 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.

**Wi-Fi를 통한 네트워크 액세스 차단:**

![Wi-Fi를 통한 네트워크 액세스 차단](./media/network_wifi_blocked_Zimperium.png)

**수정 시 액세스 권한 부여됨:**

![수정 시 액세스 권한 부여됨](./media/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 SharePoint Online에 대한 액세스 제어

네트워크에서  **메시지 가로채기(Man-in-the-middle)** 와 같은 공격을 감지하여, 디바이스 위험에 따라 회사 파일 동기화를 금지합니다.

**네트워크 위협이 감지할 경우 SharePoint Online 차단:**

![네트워크 위협이 감지되면 SharePoint Online 차단](./media/network_spo_blocked_Zimperium.png)

**수정 시 액세스 권한 부여됨:**

![SharePoint에 대해 수정 시 액세스 권한이 부여된 예](./media/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>지원되는 플랫폼

-   **Android 4.1 이상**

-   **iOS 8 이상**

## <a name="prerequisites"></a>전제 조건

-   Azure Active Directory Premium

-   Microsoft Intune 구독

-   Zimperium Mobile Threat Defense 구독

    -   자세한 내용은  [Zimperium 웹 사이트](https://www.zimperium.com/zips-mobile-ips) 를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [Intune 및 Zimperium 통합](zimperium-mtd-connector-integration.md)

- [Zimperium 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Zimperium 장치 준수 정책 만들기](mtd-device-compliance-policy-create.md)

- [Zimperium MTD 커넥터 사용](mtd-connector-enable.md)
