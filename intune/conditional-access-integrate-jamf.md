---
title: 규정 준수를 위해 Microsoft Intune과 Jamf Pro 통합 | Microsoft Intune
description: 보안 Jamf 관리 디바이스를 도우려면 Azure Active Directory의 조건부 액세스와 함께 Microsoft Intune 준수 정책을 사용합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/12/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 8e607dc612f71cdf72322b9fa7ecf14abb5fd809
ms.sourcegitcommit: d54a12a836503f7e8b90346f16b7ad2d83b710dc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54270591"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>준수를 위해 Intune과 Jamf Pro 통합

적용 대상: Azure Portal의 Intune

조직에서 [Jamf Pro](https://www.jamf.com)를 사용하여 최종 사용자의 Mac을 관리하는 경우 Azure Active Directory 조건부 액세스 권한을 가진 Microsoft Intune 준수 정책을 사용하여 조직의 디바이스가 규정을 준수하도록 합니다.

## <a name="prerequisites"></a>전제 조건

Jamf Pro를 사용하여 조건부 액세스를 구성하려면 다음이 필요합니다.

- Jamf Pro 10.1.0 이상
- [macOS용 회사 포털 앱](https://aka.ms/macoscompanyportal)
- OS X 10.11 Yosemite 이상의 macOS 디바이스

## <a name="connecting-intune-to-jamf-pro"></a>Intune을 Jamf Pro에 연결

Intune을 Jamf Pro에 연결하려면 다음을 수행합니다.

1. Azure에서 새 애플리케이션 만들기
2. Intune을 Jamf Pro와 통합할 수 있도록 설정
3. Jamf Pro에서 조건부 액세스 구성

## <a name="create-an-application-in-azure-active-directory"></a>Azure Active Directory에서 애플리케이션 만들기

1. [Azure Portal](https://portal.azure.com)에서 **Azure Active Directory** > **앱 등록**으로 이동합니다.
2. **+새 애플리케이션 등록**을 선택합니다.
3. **Jamf 조건부 액세스**와 같은 **표시 이름**을 입력합니다.
4. **웹앱/API**를 선택합니다.
5. Jamf Pro 인스턴스 URL을 사용하여 **로그온 URL**을 지정합니다.
6. **만들기**를 선택합니다. 애플리케이션이 만들어지고 포털에서 애플리케이션 세부 정보를 제공합니다.
7. 새 애플리케이션에 대한 **애플리케이션 ID**의 복사본을 저장합니다. 이후 절차에서 이 ID를 지정합니다. 다음으로 **설정**을 선택하고 **API 액세스** > **키**로 이동합니다.
8. *키* 창에서 **설명**, **만료**되기까지 걸리는 시간을 지정한 다음, **저장**을 선택하여 애플리케이션 키(값)를 생성합니다.

   > [!IMPORTANT]
   > 애플리케이션 키는 이 프로세스 중에 한 번만 표시됩니다. 쉽게 검색할 수 있는 위치에 저장해야 합니다.

8. 앱의 *설정* 창에서 **API 액세스** > **필요한 사용 권한**으로 이동합니다. 모든 기존 사용 권한을 선택한 다음, **삭제**를 클릭하고 모든 사용 권한을 삭제합니다. 새 사용 권한을 추가하고, 애플리케이션은 단일 필수 사용 권한이 있는 경우에만 작동하므로 기존 사용 권한을 삭제해야 합니다.  
9. 새 사용 권한을 할당하려면 **+추가** > **API 선택** > **Microsoft Intune API**를 선택한 다음, **선택**을 클릭합니다.
10. *액세스 사용* 창에서 **Microsoft Intune에 디바이스 속성 보내기**를 선택한 다음, **선택**, **수행**을 차례로 클릭합니다.
11. *필요한 사용 권한* 창에서 **사용 권한 부여**, **예**를 차례로 선택하여 애플리케이션에 필요한 사용 권한을 적용합니다.

    > [!NOTE]
    > 애플리케이션 키가 만료되면 Microsoft Azure에서 새 애플리케이션 키를 만든 다음 Jamf Pro의 조건부 액세스 데이터를 업데이트해야 합니다. Azure를 사용하면 서비스 중단을 방지하기 위해 이전 키와 새 키를 모두 활성화할 수 있습니다.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Intune을 Jamf Pro와 통합할 수 있도록 설정

1. [Azure Portal](https://portal.azure.com)에서 **Microsoft Intune** > **디바이스 준수** > **파트너 디바이스 관리**로 이동합니다.
2. 이전 절차 중 저장한 애플리케이션 ID를 **Jamf Azure Active Directory 앱 ID** 필드에 붙여넣어 Jamf용 준수 커넥터를 사용하도록 설정합니다.
3. **저장**을 선택합니다.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Jamf Pro에서 Microsoft Intune 통합 구성

1. Jamf Pro에서 **전역 관리** > **조건부 액세스**로 이동합니다. **Microsoft Intune 통합** 탭에서 **편집** 단추를 클릭합니다.
2. **Microsoft Intune 통합 사용** 확인란을 선택합니다.
3. 이전 단계에서 저장한 **위치**, **도메인 이름** 및 **애플리케이션 ID** 및 **애플리케이션 키**를 포함하여 Azure 테넌트에 대한 필수 정보를 제공합니다.
4. **저장**을 선택합니다. Jamf Pro가 설정을 테스트하고 성공을 확인합니다.

## <a name="set-up-compliance-policies-and-register-devices"></a>준수 정책 설정 및 디바이스 등록

Intune과 Jamf 사이의 통합을 구성한 후에는 [규정 준수 정책을 Jamf에서 관리되는 디바이스에 적용](conditional-access-assign-jamf.md)해야 합니다.

## <a name="information-shared-from-jamf-pro-to-intune"></a>Jamf Pro에서 Intune으로 공유된 정보

Jamf Pro는 관리되는 macOS 디바이스에 대한 인벤토리 정보를 캡처합니다. Jamf Pro는 다음 정보를 Intune에 보고합니다.

* 디바이스 Azure AD ID
* JAMF 인벤토리 상태(최근 24시간 이내에 Jamf Pro를 통해 확인된 컴퓨터의 인벤토리 상태)
* OS 버전
* 사용자 Azure AD ID
* 암호화됨(FileVault 2)
* 게이트키퍼 상태
* 암호: 최소 문자 집합 수
* 암호 만료(일)
* 암호 유형 - 단순, 영숫자 또는 알 수 없음
* 자동 로그인 방지
* 필수 암호 길이
* 암호: 재사용을 방지하기 위한 이전 암호 수
* 시스템 무결성 보호
* 마지막 체크인 시간
* 아키텍처 유형
* 사용 가능한 RAM 슬롯
* 배터리 용량
* 부팅 ROM
* 버스 속도
* 캐시 크기
* 장치 이름
* 도메인 가입
* Jamf ID
* MAC 주소
* Make
* 모델
* 모델 식별자
* NIC 속도
* 코어 수
* 프로세서 수
* OS
* 플랫폼
* 프로세서 속도
* 프로세서 유형
* 보조 MAC 주소
* 일련 번호
* SMC 버전
* 총 RAM
* UDID
* 사용자 메일

## <a name="next-steps"></a>다음 단계

- [준수 정책을 Jamf에서 관리되는 디바이스에 적용](conditional-access-assign-jamf.md)
