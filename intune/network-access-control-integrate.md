---
title: Microsoft Intune - Azure와 네트워크 액세스 제어 통합 | Microsoft Docs
description: NAC(네트워크 액세스 제어) 솔루션은 Intune을 사용하여 장치에 대한 준수 및 등록을 확인합니다. NAC는 조건부 액세스를 사용한 특정 동작 및 작업을 포함합니다. 등록된 단계를 참조하고 파트너 솔루션 목록을 가져옵니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: edac1701de22fd94eac3990949d18389841a5444
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231539"
---
# <a name="network-access-control-nac-integration-with-intune"></a>Intune과 NAC(네트워크 액세스 제어) 통합

Intune은 장치가 온-프레미스 리소스에 액세스하려고 할 때 조직이 회사 데이터를 보호할 수 있도록 네트워크 액세스 제어 파트너와 통합됩니다.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Intune 및 NAC 솔루션은 조직 리소스를 어떻게 보호하나요?

NAC 솔루션은 액세스 제어 결정을 내리기 위해 Intune에서 장치 등록 및 규정 준수 상태를 확인합니다. 장치가 등록되지 않았거나 등록되었으나 Intune 장치 준수 정책을 준수하지 않을 경우 등록 및/또는 장치 준수 확인을 위해 Intune에 리디렉션되어야 합니다.

### <a name="example"></a>예제

장치가 등록되었으며 Intune 규격인 경우 NAC 솔루션에서 회사 리소스에 대한 장치 액세스를 허용해야 합니다. 예를 들어 사용자가 회사 Wi-Fi 또는 VPN 리소스에 액세스하려고 할 때 액세스가 허용되거나 거부될 수 있습니다.

## <a name="feature-behaviors"></a>기능 동작

Intune에 능동적으로 동기화하는 장치는 **준수** / **비준수**에서 **동기화되지 않음**(또는 **알 수 없음**)으로 이동할 수 없습니다. **알 수 없음** 상태는 아직 준수 여부가 평가되지 않은 새로 등록된 장치에 예약되었습니다.

리소스에 대한 액세스가 차단된 장치의 경우, 차단 서비스가 모든 사용자를 [관리 포털](https://portal.manage.microsoft.com)로 리디렉션하여 장치가 차단된 이유를 확인할 수 있도록 해야 합니다.  사용자가 이 페이지를 방문하면 해당 장치의 준수 여부가 동기적으로 재평가됩니다.

## <a name="nac-and-conditional-access"></a>NAC 및 조건부 액세스

NAC는 조건부 액세스와 연동하여 액세스 제어 결정을 제공합니다. 자세한 내용은 [Intune에서 조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)을 참조하세요.

## <a name="how-the-nac-integration-works"></a>NAC 통합의 작동 방식

다음 목록은 Intune과 통합된 경우 NAC 통합의 작동 방식에 대한 개요입니다. 처음 세 단계인 1-3단계에서는 온보딩 프로세스에 대해 설명합니다. NAC 솔루션이 Intune과 통합된 후 4-9단계에서는 지속적인 작업을 설명합니다.

![NAC와 Intune의 연동 방식](./media/ca-intune-common-ways-2.png)

1. NAC 파트너 솔루션을 AAD(Azure Active Directory)에 등록하고 Intune NAC API에 위임된 사용 권한을 부여합니다.
2. Intune 검색 URL을 포함한 적절한 설정으로 NAC 파트너 솔루션을 구성합니다.
3. 인증서 인증을 위해 NAC 파트너 솔루션을 구성합니다.
4. 사용자가 회사 Wi-Fi 액세스 지점에 연결하거나 VPN 연결 요청을 수행합니다.
5. NAC 파트너 솔루션이 장치 정보를 Intune에 전달하고 장치 등록 및 준수 상태를 Intune에 요청합니다.
6. 장치가 규격이 아니거나 등록되지 않은 경우 NAC 파트너 솔루션이 사용자에게 등록하거나 장치 준수를 수정하도록 알립니다.
7. 장치가 해당 준수 및/또는 등록 상태를 확인하려고 합니다.
8. 장치가 등록되고 규격이면 NAC 파트너 솔루션이 Intune에서 상태를 가져옵니다.
9. 성공적으로 연결되어 장치가 회사 리소스에 액세스할 수 있게 됩니다.

## <a name="next-steps"></a>다음 단계

- [Intune과 Cisco ISE 통합](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Intune과 Citrix NetScaler 통합](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Intune과 HP Aruba Clear Pass 통합](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=23757)
- [Intune을 사용한 Squadra 보안 이동식 미디어 관리자(secRMM) 통합](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)