---
title: Microsoft Intune을 사용한 Symantec 커넥터
titleSuffix: Microsoft Intune
description: 회사 리소스에 대한 모바일 디바이스 액세스를 제어하기 위해 Symantec Endpoint Protection Mobile을 사용하여 Intune을 통합하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 884d7f5d4710b44c302598b3c34e704beace240a
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515274"
---
# <a name="symantec-endpoint-protection-mobile-connector"></a>Symantec Endpoint Protection Mobile 커넥터

Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 SEP Mobile(Symantec Endpoint Protection Mobile)에서 수행한 위험 평가에 따라 조건부 액세스를 사용하여 회사 리소스에의 모바일 디바이스 액세스를 제어할 수 있습니다. 위험은 다음을 비롯하여 SEP Mobile을 실행하는 디바이스에서 수집된 원격 분석에 따라 평가됩니다.

- 물리적 방어

- 네트워크 방어

- 애플리케이션 방어

- 취약성 방어

Intune 디바이스 준수 정책을 통해 SEP Mobile 위협 평가를 사용하도록 설정한 다음, 조건부 액세스 정책을 사용하여 회사 리소스에 액세스하는 비규격 디바이스를 감지된 위협에 따라 허용하거나 차단할 수 있습니다.

## <a name="how-do-intune-and-sep-mobile-help-protect-your-company-resources"></a>Intune과 SEP Mobile이 회사 리소스를 보호하는 데 어떤 도움이 되나요?

Android 또는 iOS/iPadOS용 SEP Mobile 앱은 파일 시스템, 네트워크 스택, 디바이스 및 애플리케이션 원격 분석(사용 가능한 경우)을 캡처한 다음, Symantec 클라우드 서비스로 보내 모바일 위협에 대한 디바이스의 위험을 평가합니다.

Intune 디바이스 준수 정책에는 SEP Mobile 위험 평가를 기반으로 하는 SEP Mobile에 대한 규칙이 포함되어 있습니다. 이 규칙을 사용하면 Intune에서 디바이스가 사용되는 정책을 준수하는지를 평가합니다.

디바이스가 정책을 준수하지 않으면 Exchange Online, SharePoint Online 등의 리소스에 대한 액세스가 차단됩니다. 차단된 디바이스의 사용자는 문제를 해결하고 회사 리소스에 대한 액세스 권한을 다시 얻을 수 있도록 SEP Mobile 모바일 앱에서 지침을 받습니다.

Intune은 SEP Mobile과의 통합을 두 가지 모드로 지원합니다.

- **기본 설정**은 읽기 전용 모드로, Intune에서 디바이스에 대한 SEP Mobile 표시를 허용합니다.

- **전체 통합**을 사용하면 SEP Mobile에서 디바이스 위험 및 보안 문제 세부 정보를 Intune에 보고할 수 있습니다.

## <a name="sample-scenarios"></a>샘플 시나리오:

다음은 몇 가지 일반적인 시나리오입니다.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>악성 앱의 위협에 따라 액세스 제어

맬웨어와 같은 악성 앱이 디바이스에서 감지되면 위협이 해결될 때까지 디바이스를 차단할 수 있습니다.

- 회사 메일에 연결

- 작업용 OneDrive 앱과 회사 파일 동기화

- 회사 앱에 액세스

**악성 앱이 발견되면 액세스 차단:**

![감지된 악성 앱의 개념 이미지](./media/skycure-mobile-threat-defense-connector/symantec-arch-1.png)

**수정 시 액세스 권한 부여됨:**

![악성 앱이 감지된 후 수정 시 부여된 액세스 권한의 이미지](./media/skycure-mobile-threat-defense-connector/symantec-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>네트워크에 대한 위협에 따라 액세스 제어

네트워크에서 **메시지 가로채기(man-in-the-middle)** 와 같은 위협을 감지하고 디바이스 위험에 따라 Wi-Fi 네트워크에 대한 액세스를 보호합니다.

**Wi-Fi를 통한 네트워크 액세스 차단:**

![Wi-Fi를 통한 네트워크 액세스 차단](./media/skycure-mobile-threat-defense-connector/symantec-arch-3.png)

**수정 시 액세스 권한 부여됨:**

![수정 시 액세스 권한 부여됨](./media/skycure-mobile-threat-defense-connector/symantec-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>네트워크 위협에 따라 SharePoint Online에 대한 액세스 제어

네트워크에서 **메시지 가로채기(man-in-the-middle)** 와 같은 공격을 감지하여, 디바이스 위험에 따라 회사 파일 동기화를 금지합니다.

**네트워크 위협이 감지할 경우 SharePoint Online 차단:**

![네트워크 위협이 감지되면 SharePoint Online 차단](./media/skycure-mobile-threat-defense-connector/symantec-arch-5.png)

**수정 시 액세스 권한 부여됨:**

![SharePoint에 대해 수정 시 액세스 권한이 부여된 예](./media/skycure-mobile-threat-defense-connector/symantec-arch-6.png)

## <a name="supported-platforms"></a>지원되는 플랫폼

- **Android 4.1 이상**

- **iOS 8 이상**

## <a name="pre-requisites"></a>필수 구성 요소

- Azure Active Directory Premium

- Microsoft Intune 구독

- Symantec Endpoint Protection Mobile 구독

자세한 내용은 [Symantec 웹 사이트](https://www.skycure.com/skycure-microsoft-integration/)를 참조하세요.

## <a name="next-steps"></a>다음 단계

SEP Mobile과 Intune을 통합하기 위해 완료해야 할 단계는 다음과 같습니다.

- [Intune과 SEP Mobile 통합 설정](skycure-mtd-connector-integration.md)

- [SEP Mobile 앱, Microsoft Authenticator 및 iOS/iPadOS 앱 구성 정책 추가 및 할당](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Intune을 사용하여 SEP Mobile 디바이스 준수 정책 만들기](mtd-device-compliance-policy-create.md)

- [Intune에서 SEP Mobile MTD 커넥터 사용](mtd-connector-enable.md)
