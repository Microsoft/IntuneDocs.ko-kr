---
title: Microsoft Intune을 사용한 Check Point SandBlast MTD
titlesuffix: ''
description: 회사 리소스에 대한 모바일 장치 액세스를 제어하기 위해 Check Point SandBlast MTD(Mobile Threat Defense)를 사용하여 Intune을 통합하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5766c4ebe7b261356248b00d0ca2d8937d3db79a
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231528"
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Intune과 Check Point SandBlast Mobile Threat Defense 커넥터

Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Check Point SandBlast Mobile에서 수행한 위험 평가에 따라 조건부 액세스를 사용하여 회사 리소스에 대한 모바일 장치 액세스를 제어할 수 있습니다. Check Point SandBlast Mobile 앱을 실행하는 장치에서 수집된 원격 분석에 따라 위험이 평가됩니다.

Intune 장치 준수 정책을 통해 사용하도록 설정된 Check Point SandBlast Mobile 위험 평가에 따라 조건부 액세스 정책을 구성할 수 있습니다. 이 정책을 사용하여 회사 리소스에 액세스하는 미준수 장치를 감지된 위협에 따라 허용하거나 차단할 수 있습니다.

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>Intune과 Check Point SandBlast Mobile이 회사 리소스를 보호하는 데 어떤 도움이 되나요?

Android 및 iOS용 Check Point SandBlast Mobile 앱은 파일 시스템, 네트워크 스택, 장치 및 응용 프로그램 원격 분석(사용 가능한 경우)을 캡처한 다음, 원격 분석 데이터를 Check Point SandBlast 클라우드 서비스로 보내 모바일 위협에 대한 장치의 위험을 평가합니다.

Intune 장치 준수 정책에는 Check Point SandBlast 위험 평가를 기반으로 한 Check Point SandBlast Mobile Threat Defense에 대한 규칙이 포함되어 있습니다. 이 규칙을 사용하면 Intune에서 장치가 사용되는 정책을 준수하는지를 평가합니다. 장치가 정책을 준수하지 않으면 Exchange Online, SharePoint Online 등의 회사 리소스에 대한 사용자의 액세스가 차단됩니다. 사용자는 문제를 해결하고 회사 리소스에 대한 액세스 권한을 다시 얻을 수 있도록 장치에 설치된 Check Point SandBlast 모바일 앱에서 지침을 받습니다.

<!-- ## Sample scenarios 
closing syntax for comment above is missing. Please insert closing syntax at intended location. -->

다음은 몇 가지 일반적인 시나리오입니다.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어

맬웨어와 같은 악성 앱이 장치에서 감지되면 위협이 해결될 때까지 장치를 차단할 수 있습니다.

-   회사 메일에 연결

-   작업용 OneDrive 앱과 회사 파일 동기화

-   회사 앱에 액세스

**악성 앱이 발견되면 액세스 차단:**

![악성 앱이 발견되면 Check Point MTD 차단](./media/checkpoint-MTD-2.PNG)

**수정 시 액세스 권한 부여됨:**

![Check Point MTD 액세스 권한 부여됨](./media/checkpoint-MTD-3.PNG)

### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어

네트워크에서 **메시지 가로채기(man-in-the-middle)** 와 같은 위협을 감지하고 장치 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.

**Wi-Fi를 통한 네트워크 액세스 차단:**

![Wi-Fi를 통한 Check Point MTD 네트워크 액세스 차단](./media/checkpoint-MTD-4.PNG)

**수정 시 액세스 권한 부여됨:**

![Check Point MTD Wi-Fi 액세스 권한 부여됨](./media/checkpoint-MTD-5.PNG)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 SharePoint Online에 대한 액세스 제어

네트워크에서 **메시지 가로채기(man-in-the-middle)** 와 같은 공격을 감지하여, 장치 위험에 따라 회사 파일 동기화를 금지합니다.

**네트워크 위협이 감지할 경우 SharePoint Online 차단:**

![Check Point MTD SharePoint Online 액세스 차단](./media/checkpoint-MTD-6.PNG)

**수정 시 액세스 권한 부여됨:**

![Check Point MTD SharePoint Online 액세스 권한 부여됨](./media/checkpoint-MTD-7.PNG)

## <a name="supported-platforms"></a>지원되는 플랫폼

-   **Android 4.1 이상**

-   **iOS 8 이상**

## <a name="pre-requisites"></a>필수 구성 요소

-   Azure Active Directory Premium

-   Microsoft Intune 구독

-   Check Point SandBlast Mobile Threat Defense 구독
    -   자세한 내용은 [CheckPoint SandBlast 웹사이트](https://www.checkpoint.com/)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [Intune과 Check Point SandBlast 통합](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [Check Point SandBlast Mobile 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [CheckPoint SandBlast Mobile 장치 규정 준수 정책 만들기](mtd-device-compliance-policy-create.md)

- [CheckPoint SandBlast Mobile MTD 커넥터 사용](mtd-connector-enable.md)
