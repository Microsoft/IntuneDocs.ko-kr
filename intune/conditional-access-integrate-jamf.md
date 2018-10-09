---
title: 준수를 위해 Microsoft Intune과 Jamf Pro 통합
titlesuffix: ''
description: 보안 Jamf 관리 장치를 도우려면 Azure Active Directory의 조건부 액세스와 함께 Microsoft Intune 준수 정책을 사용합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 516e2f935225b7142c75b01967977fe97297c8e2
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232183"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>준수를 위해 Intune과 Jamf Pro 통합

|적용 대상: Azure Portal의 Intune |
|--|
|클래식 포털의 Intune에 대한 설명서를 찾으시나요? [여기로 이동](/intune/introduction-intune?toc=/intune-classic/toc.json)하세요.|
| |

조직에서 [Jamf Pro](https://www.jamf.com)를 사용하여 최종 사용자의 Mac를 관리하는 경우 Azure Active Directory 조건부 액세스 권한을 가진 Microsoft Intune 준수 정책을 사용하여 조직의 장치가 규정을 준수하도록 합니다.

## <a name="prerequisites"></a>전제 조건

Jamf Pro를 사용하여 조건부 액세스를 구성하려면 다음이 필요합니다.

- Jamf Pro 10.1.0 이상
- [macOS용 회사 포털 앱](https://aka.ms/macoscompanyportal)
- OS X 10.11 Yosemite 이상의 macOS 장치

## <a name="connecting-intune-to-jamf-pro"></a>Intune을 Jamf Pro에 연결

다음 방법으로 Intune을 Jamf Pro에 연결할 수 있습니다.

1. Azure에서 새 응용 프로그램 만들기
2. Intune을 Jamf Pro와 통합할 수 있도록 설정
3. Jamf Pro에서 조건부 액세스 구성

## <a name="create-a-new-application-in-azure-active-directory"></a>Azure Active Directory에서 새 응용 프로그램 만들기

1. **Azure Active Directory** > **앱 등록**을 엽니다.
2. **+새 응용 프로그램 등록**을 클릭합니다.
3. **Jamf 조건부 액세스**와 같은 **표시 이름**을 입력합니다.
4. **웹앱/API**를 선택합니다.
5. Jamf Pro 인스턴스 URL을 사용하여 **로그온 URL**을 지정합니다.
6. **응용 프로그램 만들기**를 클릭합니다.
7. 새로 만든 **응용 프로그램 ID**를 저장한 다음 **설정**을 열고 **API 액세스** > **키**로 이동하여 새 응용 프로그램 키를 만듭니다. **설명**, **만료**되기까지 걸리는 시간을 입력한 다음 응용 프로그램 키를 저장합니다.

   > [!IMPORTANT]
   > 응용 프로그램 키는 이 프로세스 중에 한 번만 표시됩니다. 쉽게 검색할 수 있는 위치에 저장해야 합니다.

8. **설정**을 입력한 다음 **API 액세스** > **필수 권한**으로 이동하여 모든 권한을 삭제합니다.

   > [!NOTE]
   > 새 필수 권한을 추가합니다. 응용 프로그램은 단일 필수 권한이 있는 경우에만 제대로 작동할 수 있습니다.

9. **Microsoft Intune API**를 선택하고 **선택**을 클릭합니다.
10. **Microsoft Intune에 장치 속성 보내기**를 선택하고 **선택**을 클릭합니다.
11. 응용 프로그램에 필요한 권한을 저장한 후 **권한 부여** 단추를 클릭합니다.

    > [!NOTE]
    > 응용 프로그램 키가 만료되면 Microsoft Azure에서 새 응용 프로그램 키를 만든 다음 Jamf Pro의 조건부 액세스 데이터를 업데이트해야 합니다. Azure를 사용하면 서비스 중단을 방지하기 위해 이전 키와 새 키를 모두 활성화할 수 있습니다.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Intune을 Jamf Pro와 통합할 수 있도록 설정

1. Microsoft Azure Portal에서 **Microsoft Intune** > **장치 준수** > **Partner device management**(파트너 장지 관리)를 엽니다.
2. 응용 프로그램 ID를 **Jamf Azure Active Directory 앱 ID** 필드에 붙여넣어 Jamf용 준수 커넥터를 사용하도록 설정합니다.
3. **Save**을 클릭합니다.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Jamf Pro에서 Microsoft Intune 통합 구성

1. Jamf Pro에서 **전역 관리** > **조건부 액세스**로 이동합니다. **Microsoft Intune 통합** 탭에서 **편집** 단추를 클릭합니다.
2. **Microsoft Intune 통합 사용** 확인란을 선택합니다.
3. 이전 단계에서 저장한 **위치**, **도메인 이름** 및 **응용 프로그램 ID** 및 **응용 프로그램 키**를 포함하여 Azure 테넌트에 대한 필수 정보를 제공합니다.
4. **Save**을 클릭합니다. Jamf Pro가 설정을 테스트하고 성공을 확인합니다.

## <a name="set-up-compliance-policies-and-register-devices"></a>준수 정책 설정 및 장치 등록

Intune과 Jamf 사이의 통합을 구성한 후에는 [준수 정책을 Jamf에서 관리되는 장치에 적용](conditional-access-assign-jamf.md)해야 합니다.

## <a name="information-shared-from-jamf-pro-to-intune"></a>Jamf Pro에서 Intune으로 공유된 정보

Jamf Pro는 관리되는 macOS 장치에 대한 인벤토리 정보를 캡처합니다. Jamf Pro는 다음 정보를 Intune에 보고합니다.

* 장치 Azure AD ID
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

- [준수 정책을 Jamf에서 관리되는 장치에 적용](conditional-access-assign-jamf.md)
