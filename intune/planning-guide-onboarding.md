---
title: Intune 온보딩 프로세스
titleSuffix: Microsoft Intune
description: 이 아티클에는 Microsoft Intune 클라우드 전용 솔루션을 환경에 온보딩할 때 고려해야 하는 유용한 모든 세부 정보가 포함되어 있습니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d05d9dd896321e48c3d1d9dec22cd0d1192dc0b6
ms.sourcegitcommit: 7273100afc51fd808558dc05c651358145d4fa6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68533189"
---
# <a name="implement-your-microsoft-intune-plan"></a>Microsoft Intune 계획 구현

온보딩 단계에서 프로덕션 환경에 Intune을 배포합니다. 구현 프로세스는 [사용 사례 요구 사항](planning-guide-requirements.md)에 따른 Intune 및 외부 종속성(필요한 경우) 설정과 구성으로 이루어져 있습니다.

다음 섹션에서는 요구 사항 및 대략적인 작업이 포함된 Intune 구현 프로세스의 개요를 제공합니다.

## <a name="intune-requirements"></a>Intune 요구 사항

주요 Intune 독립 실행형 요구 사항은 다음과 같습니다.

- EMS(Enterprise Mobility + Security)/Intune 구독

- Office 365 구독(Office 앱 및 앱 보호 정책 관리 앱용)

- Apple APNs 인증서(iOS 디바이스 플랫폼 관리를 사용하도록 설정하기 위해)

- Azure AD Connect(디렉터리 동기화용)

- Exchange용 Intune 온-프레미스 Connector(필요한 경우 Exchange 온-프레미스에 대한 조건부 액세스에 사용하기 위해)

- Intune Certificate Connector(필요한 경우 SCEP 인증서 배포용)

>[!TIP]
> Intune으로 관리할 수 있는 디바이스의 전체 목록을 보려면 [지원되는 디바이스](supported-devices-browsers.md) 목록을 참조하세요.

## <a name="intune-implementation-process"></a>Intune 구현 프로세스

Intune 배포를 구현하기 위한 작업은 13가지입니다. 비즈니스 요구 사항, 기존 인프라 및 디바이스 관리 전략에 따라 이러한 작업 중 일부는 이미 완료되었을 수 있습니다. 다른 작업은 계획에 적용되지 않을 수 있습니다.

### <a name="task-1-get-an-intune-subscription"></a>태스크 1: Intune 구독 가져오기

위의 Intune 요구 사항 섹션에서 확인했듯이 EMS 또는 Intune 구독이 필요합니다. 조직에 구독이 없는 경우 EMS(Enterprise Mobility + Security) 또는 Intune 구매에 관심이 있으면 관련 Microsoft 계정 팀 또는 Microsoft에 문의하세요.

- [Microsoft Intune을 구매하는 방법](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)에 대해 자세히 알아보세요.

### <a name="task-2-add-office-365-subscription"></a>태스크 2: Office 365 구독 추가

이 단계는 선택 사항입니다. Exchange Online을 사용하고 앱 보호 전략으로 Office 모바일 앱을 관리할 계획이 있는 경우 Office 365 구독이 필요합니다. 조직에 Office 365 구독이 없는 경우 Office 365 구매에 관심이 있으면 관련 Microsoft 계정 팀 또는 Microsoft에 문의하세요.

- [Office 365 구매 방법](https://products.office.com/business/compare-office-365-for-business-plans)에 대해 자세히 알아보세요.

### <a name="task-3-add-users-groups-in-azure-ad"></a>태스크 3: Azure AD에서 사용자 그룹 추가

Intune 배포 사용 사례 시나리오 및 요구 사항에 따라 Active Directory 또는 Azure Active Directory에서 사용자 또는 보안 그룹을 추가해야 할 수 있습니다. Active Directory 또는 Azure Active Directory의 현재 사용자 및 보안 그룹을 검토하고, 해당 사용자 및 보안 그룹이 요구를 완벽하게 충족하는지 확인해야 합니다. 새 사용자 및 보안 그룹을 추가하는 경우 Active Directory에서 추가하고 Azure AD Connect를 통해 Azure Active Directory와 동기화하는 것이 좋습니다.


- [Intune에 사용자/그룹을 추가하는 방법](users-permissions-add.md)에 대해 자세히 알아보세요.
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect--->



### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>태스크 4: Intune 및 Office 365 사용자 라이선스 할당

EMS/Intune 및 Office 365 출시 대상으로 지정될 모든 사용자에게는 할당받은 라이선스가 있어야 합니다. Microsoft 365 관리 센터 포털에서 EMS/Intune 및 Office 365 라이선스를 할당할 수 있습니다.

- [Intune 라이선스를 할당하는 방법](licenses-assign.md)에 대해 자세히 알아보세요.

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>태스크 5: Intune으로 모바일 디바이스 관리 기관 설정

Intune을 사용하여 디바이스를 설치/구성/관리/등록하려면 먼저 디바이스 관리 기관을 Intune으로 설정해야 합니다.

- [디바이스 관리 기관을 설정하는 방법](mdm-authority-set.md)에 대해 자세히 알아보세요.

### <a name="task-6-enable-device-platforms"></a>태스크 6: 디바이스 플랫폼을 사용하도록 설정

기본적으로 Apple 디바이스(iOS 및 Mac)를 제외한 대부분의 디바이스 플랫폼을 사용하도록 설정할 수 있습니다. Intune에서 iOS 디바이스를 등록하고 관리하려면 먼저, 디바이스 플랫폼을 사용하도록 설정해야 합니다. 이렇게 하려면 MDM 푸시 인증서를 만들어 Intune에 추가해야 합니다.

- [등록을 위해 Apple 디바이스를 사용하도록 설정하는 방법](apple-mdm-push-certificate-get.md)을 자세히 알아보세요.

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>태스크 7: 사용 약관 정책 추가 및 배포

Intune은 사용 약관 정책을 지원합니다. 사용 약관 정책을 적절히 추가하고, Intune 배포 사용 사례 및 요구 사항에 따라 대상 그룹에 배포합니다.

- [사용 약관 정책을 추가하고 배포하는 방법](terms-and-conditions-create.md)에 대해 자세히 알아보세요.

### <a name="task-8-add-and-deploy-configuration-policies"></a>태스크 8: 구성 정책 추가 및 배포

Intune은 두 가지 유형의 구성 정책 즉, 일반 및 사용자 지정 구성 정책을 지원합니다. 구성 정책을 적절히 추가하고, Intune 배포 사용 사례 및 요구 사항에 따라 대상 그룹에 배포합니다.

- [구성 정책을 추가하고 배포하는 방법](device-profiles.md)에 대해 자세히 알아보세요.

### <a name="task-9-add-and-deploy-resource-profiles"></a>태스크 9: 리소스 프로필 추가 및 배포

Intune은 메일, Wi-Fi 및 VPN 프로필을 지원합니다. 이러한 프로필을 적절히 추가하고, Intune 배포 사용 사례 및 요구 사항에 따라 대상 그룹에 배포합니다.

- [Intune을 사용하여 회사 리소스에 대한 액세스를 허용하는 방법](device-profiles.md)에 대해 자세히 알아보세요.

### <a name="task-10-add-and-deploy-apps"></a>태스크 10: 앱 추가 및 배포

Intune은 웹, 기간 업무 및 공용 저장소 앱의 배포를 지원합니다. 또한 앱 보호 정책과 연결함으로써 Intune SDK를 통합한 앱을 관리할 수 있습니다. 앱을 적절히 추가하고, Intune 배포 사용 사례 및 요구 사항에 따라 대상 그룹에 배포합니다.

- [앱 추가 및 배포](app-management.md)에 대해 자세히 알아보세요.

### <a name="task-11-add-and-deploy-compliance-policies"></a>태스크 11: 규정 준수 정책 추가 및 배포

Intune은 준수 정책을 지원합니다. 준수 정책을 적절히 추가하고, Intune 배포 사용 사례 및 요구 사항에 따라 대상 그룹에 배포합니다.

- [준수 정책](device-compliance.md)에 대해 자세히 알아보세요.

### <a name="task-12-enable-conditional-access-policies"></a>태스크 12: 조건부 액세스 정책 사용

Intune은 Exchange Online, Exchange 온-프레미스, SharePoint Online, 비즈니스용 Skype Online 및 Dynamics CRM Online에 대한 조건부 액세스를 지원합니다. Intune 배포 사용 사례 및 요구 사항에 따라 적절히 조건부 액세스를 사용하도록 설정하고 구성합니다.

- [조건부 액세스](conditional-access.md)에 대해 자세히 알아보세요.

### <a name="task-13-enroll-devices"></a>태스크 13: 디바이스 등록

Intune은 iOS, Mac OS, Android, Windows 데스크톱 및 Windows 모바일 디바이스 플랫폼을 지원합니다. Intune 배포 사용 사례 및 요구 사항에 따라 적절히 모바일 디바이스 플랫폼을 등록합니다.

- [디바이스를 등록하는 방법](device-enrollment.md)에 대해 자세히 알아보세요.


## <a name="next-steps"></a>다음 단계
[Intune 배포 테스트 및 유효성 검사](planning-guide-test-validation.md)의 지침을 참조하세요.
