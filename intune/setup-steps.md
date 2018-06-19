---
title: Microsoft Intune 설정
description: Intune 구독 사용을 시작하기 위한 요구 사항 및 필수 구성 요소
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f818c35a008c24a529967b09a37917343433ff7d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31023192"
---
# <a name="set-up-intune"></a>Intune 설정

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

이러한 설정 단계는 Intune을 이용하여 MDM(모바일 장치 관리)을 사용하도록 할 수 있습니다. 사용자에게 회사 리소스에 대한 액세스 권한을 부여하거나 해당 장치에서 설정을 관리할 수 있으려면 먼저 장치가 관리되어야 합니다.

Intune 구독 설정 및 MDM 기관 설정과 같은 일부 단계는 대부분의 시나리오에 필요합니다. 사용자 지정 도메인 구성 또는 앱 추가와 같은 다른 단계는 회사의 요구 사항에 따라 적용할 수 있는 선택 사항입니다.

현재 Microsoft System Center Configuration Manager를 사용하여 컴퓨터와 서버를 관리하는 경우에는 [Configuration Manager를 확장하여 모바일 장치를 관리](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)할 수 있습니다.

>[!TIP]
>적격 플랜을 통해 Intune에 대한 라이선스를 150개 이상 구매하는 경우 *FastTrack 센터 혜택*을 사용할 수 있습니다. 이 서비스를 통해 Microsoft 전문가는 사용자와 협력하여 Intune에 맞게 사용자 환경을 준비합니다. [EMS(Enterprise Mobility + Security)에 대한 FastTrack 센터 혜택](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program)을 참조하세요.



| 단계 |                                                                                                                       상태                                                                                                                       |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   1   |                                        [지원되는 구성](supported-devices-browsers.md) - 시작하기 전에 알아야 하는 정보입니다. 지원되는 구성 및 네트워킹 요구 사항이 여기에 포함됩니다.                                         |
|   2   |                                                                 [Intune에 로그인](account-sign-up.md) - 평가판 구독에 로그인하거나 새 Intune 구독을 만듭니다.                                                                  |
|   3   |                [도메인 이름 구성](custom-domain-name-configure.md) - 회사의 도메인 이름이 Intune과 연결되도록 DNS 등록을 설정합니다. 이렇게 하면 Intune에 연결하고 리소스를 사용할 때 사용자에게 친숙한 도메인이 제공됩니다.                |
|   4   |                                   [사용자 추가](users-add.md) - 수동으로 사용자를 추가하거나 Active Directory를 연결하여 사용자를 Intune과 동기화합니다. 예를 들어 장치가 “사용자가 없는” 키오스크 장치가 아닌 한 필수입니다.                                    |
|   5   |                                            [라이선스 할당](licenses-assign.md) - 사용자에게 Intune 사용 권한을 부여합니다. 각 사용자 또는 사용자가 없는 장치가 서비스에 액세스하려면 Intune 라이선스가 필요합니다.                                             |
|   6   |                                               [그룹 추가](groups-add.md) - 사용자 및 장치 그룹을 사용하여 관리 작업을 간소화합니다. 그룹은 앱, 설정 및 기타 리소스를 할당하는 데 사용됩니다.                                                |
|   7   |                                                                        [앱 추가](apps-add.md) - 앱을 그룹에 할당하여 자동으로 또는 필요에 따라 설치할 수 있습니다.                                                                         |
|   8   | [장치 구성](device-profiles.md) - 장치 설정을 관리하는 프로필을 설정합니다. 장치 프로필은 메일, VPN, Wi-Fi 및 장치 기능에 대한 설정을 미리 구성할 수 있습니다. 장치 프로필은 장치 및 데이터 보호를 위해 장치를 제한할 수도 있습니다. |
|   9   |       [회사 포털 사용자 지정](company-portal-app.md) - 사용자가 장치를 등록하고 앱을 설치하는 데 사용하는 Intune 회사 포털을 사용자 지정합니다. 이러한 설정은 회사 포털 앱과 Intune 회사 포털 웹 사이트 둘 다에 표시됩니다.       |
|  10   |                                [장치 등록 사용](mdm-authority-set.md) - MDM 기관을 설정하고 특정 플랫폼을 사용하도록 설정하여 iOS, Windows, Android 및 Mac 장치의 Intune 관리를 사용하도록 설정합니다.                                 |
|  11   |                                                        [앱 정책 구성](app-protection-policy.md) - Microsoft Intune의 앱 보호 정책에 따라 특정 설정을 지정합니다.                                                         |

