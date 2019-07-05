---
title: Windows 디바이스의 Intune 등록 방법
titleSuffix: Microsoft Intune
description: Intune에 Windows 디바이스를 등록하는 여러 가지 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: b8b1c47e4a2eb46bb8f7190ede351ed77a1bfef4
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494509"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>Windows 디바이스의 Intune 등록 방법

Intune에서 디바이스를 관리하려면 먼저 Intune 서비스에 디바이스를 등록해야 합니다. 개인 소유 디바이스와 회사 소유 디바이스 둘 다 Intune에 등록하여 관리할 수 있습니다. 

Intune에 디바이스를 등록하는 방법은 다음과 같은 두 가지가 있습니다.
- 사용자가 자신의 Windows PC를 직접 등록 
- 관리자가 사용자 개입 없이 자동으로 등록하는 정책을 구성

## <a name="user-self-enrollment-in-intune"></a>Intune에서 사용자가 직접 등록

사용자는 다음 중 아무 방법을 사용하여 Windows 디바이스를 직접 등록할 수 있습니다.

- [BYOD(Bring Your Own Device)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device): 사용자가 디바이스 **설정**에서 **회사 및 학교** 계정에 연결하도록 선택하여 개인 소유의 디바이스를 등록합니다. 이 프로세스는 다음과 같습니다.
    - 디바이스를 Azure Active Directory에 등록하여 이메일 같은 회사 리소스에 대한 액세스 권한을 얻습니다.
    - 디바이스를 Intune에 개인 소유 디바이스(BYOD)로 등록합니다.
관리자가 자동 등록을 구성한 경우(zure AD 프리미엄 구독에서 사용 가능) 사용자는 자격 증명을 한 번만 입력하면 됩니다. 구성하지 않은 경우 MDM 전용 록을 통해 별도로 등록하고 자격 증명을 다시 입력해야 합니다.  
- **MDM 전용 등록**을 사용하면 사용자는 기존 작업 그룹, Active Directory 또는 Azure Active Directory 조인 PC를 Intune에 등록할 수 있습니다. 사용자는 기존 Windows PC의 설정에서 등록합니다. 이 방법은 디바이스를 Azure Active Directory에 등록하지 않으므로 권장되지 않습니다. 뿐만 아니라 조건부 액세스 같은 기능을 사용할 수 없습니다.
- [Azure AD(Azure Active Directory) 조인](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) - 디바이스를 Azure Active Directory에 등록하고 사용자가 자신의 Azure AD 자격 증명으로 Windows에 로그인 할 수 있도록 합니다. 자동 등록을 사용하면 디바이스가 Intune에 자동으로 등록됩니다. 자동 등록의 이점은 사용자가 1단계 프로세스만 수행하면 된다는 점입니다. 구성하지 않은 경우 MDM 전용 록을 통해 별도로 등록하고 자격 증명을 다시 입력해야 합니다. 사용자는 초기 Windows OOBE 과정 중에 또는 설정에서 이 방법으로 등록합니다. 디바이스는 Intune에서 회사 소유 디바이스로 표시됩니다.
- [Autopilot](enrollment-autopilot.md) - Azure AD 조인을 자동화하고 새로운 회사 소유 디바이스를 Intune에 등록합니다. 이 방법을 선택하면 첫 실행 경험이 간소화되고 사용자 지정 운영 체제 이미지를 디바이스에 적용할 필요가 없습니다. 관리자가 Intune을 사용하여 Autopilot 디바이스를 관리하는 경우 디바이스를 등록한 후에 정책, 프로필, 앱 등을 관리할 수 있습니다.  Autopilot 배포에는 다음과 같은 네 가지 유형이 있습니다. [자체 배포 모드](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying)(키오스크, 디지털 간판 또는 공유 디바이스용), [사용자 기반 모드](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)(기존 사용자용), [화이트 글러브](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) 를 사용하면 파트너 또는 IT 담당자가 Windows 10 PC를 사전 프로비저닝하여 완전히 구성하여 비즈니스를 준비하고, [기존 디바이스용 Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) 를 사용하면 최신 버전의 Windows 10을 기존 디바이스에 쉽게 배포할 수 있습니다.

## <a name="administrator-based-enrollment-in-intune"></a>Intune에서 관리자 기반으로 등록

관리자는 사용자 상호 작용이 필요 없는 다음과 같은 등록 방법을 설정할 수 있습니다.

- [하이브리드 Azure AD 조인](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)을 사용하면 관리자는 하이브리드 Azure AD 조인 디바이스를 자동으로 등록하는 Active Directory 그룹 정책을 구성할 수 있습니다. 
- [Configuration Manager 공동 관리](https://docs.microsoft.com/sccm/comanage/overview)를 사용하면 관리자는 기존 Configuration Manager를 통해 관리 디바이스를 Intune에 등록하여 Intune과 Configuration Manager의 이점을 모두 누릴 수 있습니다. 
- [DEM(디바이스 등록 관리자)](device-enrollment-manager-enroll.md)은 특수 서비스 계정입니다. DEM 계정은 권한 있는 사용자가 여러 회사 소유 디바이스를 등록하고 관리할 수 있는 권한을 갖고 있습니다. 이러한 디바이스 유형은 예를 들어 POS(Point-Of-Sale) 또는 유틸리티 앱에는 유용하지만 이메일 또는 회사 리소스에 액세스해야 하는 사용자에게는 유용하지 않습니다. 이 방법은 조건부 액세스 같은 기능을 사용할 수 없습니다. 
- [대량 등록](windows-bulk-enroll.md)을 사용하면 권한 있는 사용자는 새 회사 소유 디바이스를 Azure Active Directory 및 Intune에 대량으로 조인할 수 있습니다. WCD(Windows 구성 디자이너) 앱을 사용하여 프로비저닝 패키지를 만듭니다. 그런 다음, 초기 Windows OOBE 경험 중에 또는 기존 Windows PC에서 USB 미디어를 사용하여 자동으로 Intune에 디바이스를 등록하는 프로비저닝 패키지를 설치합니다. 이 방법은 조건부 액세스를 사용할 수 없습니다. 
- [Windows IoT Core 디바이스 등록](https://docs.microsoft.com/windows/iot-core/manage-your-device/intunedeviceenrollment)을 수행하려면 Windows IoT Core 대시보드를 사용하여 디바이스를 준비한 다음 Windows 구성 디자이너를 사용하여 프로비저닝 패키지를 만듭니다. 그런 다음 처음 부팅할 때 SD 카드 미디어를 사용해 프로비저닝 패키지를 설치하여 디바이스를 Intune에 자동으로 등록합니다.

## <a name="next-steps"></a>다음 단계

[Windows 등록 방법의 기능 알아보기](enrollment-method-capab.md)
