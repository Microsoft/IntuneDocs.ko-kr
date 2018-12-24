---
title: Intune에서 데이터 수집
description: Intune에서 개인 데이터를 수집하는 방법에 대해 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 73cd8b4f0cf5bdfa02a301d476df31a01fc9691f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186123"
---
# <a name="data-collection-in-intune"></a>Intune에서 데이터 수집

사용자가 Intune을 사용하여 회사 또는 개인 디바이스를 등록하면 Intune은 일부 개인 데이터를 수집하고 공유합니다. Intune은 다음 소스에서 개인 데이터를 수집합니다.

- Azure Portal에서 관리자의 Intune 사용 현황.
- 최종 사용자 디바이스(Intune 관리 대상으로 등록되고 사용 중인 경우).
- 타사 서비스의 고객 계정(관리자 지침을 따름).
- 진단, 성능 및 사용 정보.

이러한 소스에서 Intune은 [식별된](#identified-data) 데이터, [가명 처리된](#pseudonymized-data) 데이터 및 [집계된](#aggregated-data) 세 가지 범주로 분류되는 정보를 수집합니다.

## <a name="identified-data"></a>식별된 데이터

Intune에서 수집하는 대부분의 개인 데이터는 식별된 데이터입니다. 이 데이터는 사용자, 디바이스 또는 응용 프로그램에 연결되며 관리 특성에 매우 중요합니다. 식별된 데이터는 사용자의 디바이스 및 응용 프로그램을 관리하고 Intune 서비스를 프로비전하는 데 사용됩니다.

Intune에서 수집하는 식별된 데이터는 다음을 포함할 수 있지만 이에 한정되지는 않습니다. 

- 사용자 정보
    - 소유자 이름/사용자 표시(theAzureUserID로 식별된 사용자의 Azure 등록 이름)
    - 사용자 계정 이름 또는 이메일 주소
    - 타사 사용자 ID(예: AppleID)
- 하드웨어 인벤토리 정보
    - 디바이스 이름
    - 제조업체
    - 운영 체제
    - 일련 번호
    - IMEI 번호
    - IP 주소
    - Wi-Fi MacAddress
    - ICCID
    - 전화 번호
- 다음 작업에 대한 데이터를 포함하는 감사 로그 정보
    - 관리
    - 만들기
    - 업데이트(편집)
    - 삭제
    - 할당
    - 원격 작업
- 지원 정보
    - 연락처 정보(이름, 전화번호, 이메일 주소)
    - Microsoft 지원, 제품 및/또는 고객 환경 팀 멤버와 이메일 토론
- 액세스 제어 정보(Intune은 이 데이터를 사용하여 [역할 기반 액세스 제어](role-based-access-control.md)와 같은 기능을 통해 관리 역할 및 기능에 대한 액세스를 관리합니다.)
    - 정적 인증자(고객의 암호)
    - 인증서의 개인 정보 키 
- 관리자 및 계정 정보
    - 관리 사용자 이름 및 성
    - 관리 사용자 이름
    - UPN(이메일)
    - 전화 번호
    - 계정 소유자의 이메일 주소
    - 각 고객 IT 관리자의 Active Directory ID
    - 고객 대금 결제 데이터
    - 구독 키
- 응용 프로그램 인벤토리 등
    - 앱 이름
    - 버전
    - 앱 ID
    - 크기
    - 설치 위치
    - 응용 프로그램 인벤토리 데이터는 관리자가 회사 소유 디바이스로 표시하거나 호환되는 앱 기능이 설정된 경우에만 수집됩니다.  
- 고객 타사 테넌트 ID입니다(예: Apple ID). 

## <a name="pseudonymized-data"></a>가명 처리된 데이터

가명 처리된 데이터는 고유한 식별자와 연관되어 있으며, 일반적으로 시스템에 의해 생성된 번호로, 자체적으로 개별 사용자를 식별할 수 없지만 사용자에게 엔터프라이즈 서비스를 제공하는 데 사용됩니다. 

Intune에서 수집되는 가명 처리된 데이터는 다음을 포함할 수 있지만 이에 한정되지는 않습니다. 

- 사용자 및/또는 디바이스에 연결된 진단, 성능 및 사용 현황 데이터
    - 기능이 사용된 횟수
    - 기능에 제공된 명령
    - 서비스 응답 시간
    - 설치 및 기타 프로세스의 성공률
    - Intune 회사 포털 응용 프로그램 오류
    - 사용자 및 디바이스 식별자
    - 참조, 상관 관계, 관리 목적을 위한 식별자 
- 디바이스 또는 사용자에 연결되지 않은 디바이스 데이터(디바이스 또는 사용자에 연결된 데이터는 Intune에서 식별된 데이터로 처리함)
    - Intune 디바이스 ID
    - Azure Active Directory 디바이스 ID
    - Intune 디바이스 관리 ID
    - 테넌트 ID
    - 계정 ID
    - EAS 디바이스 ID
    - 플랫폼별 ID
    - iOS 디바이스용 AppleID
    - Mac 디바이스용 Mac 주소
    - Windows 디바이스용 Windows ID
- 관리되는 응용 프로그램 정보
    - 관리되는 응용 프로그램 ID
    - 관리되는 응용 프로그램 디바이스 태그
    - Intune 디바이스 관리 ID
    - Azure Active Directory 디바이스 ID
    - 암호화 키

## <a name="aggregated-data"></a>집계된 데이터

집계된 데이터는 Intune 서비스를 프로비전하고 향상시키는 데 사용됩니다. 

Intune에서 수집되는 집계된 데이터는 다음을 포함할 수 있지만 이에 한정되지는 않습니다. 

- 모든 Intune 테넌트의 관리자 사용 현황 데이터(예: 관리 콘솔과 상호 작용할 때 선택된 관리 컨트롤)
- 테넌트 계정 정보(이 데이터는 Intune 블레이드에서 사용할 수 있음)
    - 등록된 디바이스 또는 사용자 수
    - 식별된 디바이스 플랫폼의 수  
    - 설치된 디바이스 수
    - installedDeviceCount: 응용 프로그램이 설치된 디바이스의 수입니다.
    - notApplicableDeviceCount: 응용 프로그램을 적용할 수 없는 디바이스의 수입니다.
    - notInstalledDeviceCount: 응용 프로그램을 적용할 수 있지만 설치하지 않은 디바이스의 수입니다.
    - pendingInstallDeviceCount: 응용 프로그램을 적용할 수 있고 설치가 보류 중인 디바이스의 수입니다.
    
## <a name="next-steps"></a>다음 단계

Intune의 개인 데이터 [저장 및 처리](privacy-data-store-process.md), [공유](privacy-data-secure-share.md) 방법에 대해 자세히 알아봅니다. 