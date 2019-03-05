---
title: Intune에 보내는 데이터 JAMF Pro | Microsoft Intune
description: Jamf Pro가 Microsoft Intune에 보내는 데이터 목록
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22d81c768fb7f80498da483421f8b358d59ab8c2
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233252"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Intune에 보내는 데이터 Jamf Pro

[Jamf Pro](https://www.jamf.com)를 사용하여 Intune으로 최종 사용자 Mac을 관리할 때 Jamf Pro는 관리되는 macOS 디바이스에 대한 인벤토리 정보를 캡처합니다. Jamf Pro는 다음 정보를 Intune에 보고합니다.

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


**모든 디바이스** 보기에서 **삭제**를 선택하여 Intune 콘솔에서 Jamf 관리 디바이스를 제거할 수 있습니다. 여러 디바이스를 선택하고 **삭제**를 클릭하여 대량 디바이스 삭제를 사용하도록 설정할 수 있습니다.

[Jamf 관리 디바이스를 Jamf Pro 문서에서 제거](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)하는 방법에 대해 알아봅니다. 또한 추가 도움을 위해 지원 티켓을 [Jamf 지원](https://www.jamf.com/support/)와 함께 제출할 수 있습니다. 

