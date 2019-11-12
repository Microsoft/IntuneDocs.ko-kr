---
title: 디바이스를 등록하면 회사에 어떤 정보가 표시되나요?
description: IT가 관리되는 디바이스에서 볼 수 있는 사항과 볼 수 없는 사항 설명
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.collection: M365-identity-device-management
ms.openlocfilehash: fc50f48afbd527f3c6d82cc0c71a166b0356ab9e
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801472"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>내 디바이스를 등록하면 조직에 어떤 정보가 표시되나요?

Microsoft Intune에 디바이스를 등록할 때 조직에서 개인 정보를 볼 수 없습니다. 디바이스를 등록할 때 디바이스 모델 및 일련 번호와 같은 디바이스의 특정 정보를 볼 수 있는 권한을 조직에 부여합니다. 조직은 이 정보를 사용하여 디바이스의 회사 데이터를 보호합니다.

**조직에서 절대 볼 수 없는 항목:**

- 호출 및 웹 검색 기록
- 전자 메일 및 문자 메시지
- 연락처
- 일정
- 암호
- 사진 앱 또는 카메라 앨범에 있는 사진을 비롯한 사진
- 파일

**조직에서 항상 볼 수 있는 항목:**

- Google Pixel 같은 디바이스 모델
- 디바이스 제조업체(예: Microsoft)
- 운영 체제 및 버전(예: iOS 12.0.1)
- Microsoft Word와 같은 앱 이름 및 앱 인벤토리 개인 디바이스에서 조직은 관리되는 앱 인벤토리만 볼 수 있습니다. 회사 소유 디바이스에서 조직은 모든 앱 인벤토리를 볼 수 있습니다.
- 디바이스 소유자
- 디바이스 이름
- 디바이스 일련 번호
- IMEI

**조직에서 볼 수도 있는 항목:**

- 전화 번호: 회사 소유 디바이스인 경우 전체 전화 번호를 볼 수 있습니다. 개인 소유 디바이스인 경우 전화 번호의 마지막 네 자리만 조직에 표시됩니다. **장치 세부 정보** 페이지에서 각 개별 장치의 소유권 유형을 볼 수 있습니다.
- 디바이스 스토리지 공간: 필수 앱을 설치할 수 없는 경우 조직은 디바이스의 스토리지 공간을 보고 공간이 너무 적은지 확인할 수 있습니다.  
- 위치: 사용자가 분실한 감독형 iOS 디바이스를 복구해야 하는 경우가 아니면 조직은 디바이스의 위치를 절대 알 수 없습니다. 감독형 디바이스에 대해 자세히 알아보려면 [Apple iOS 설명서](https://go.microsoft.com/fwlink/?linkid=853816)를 참조하세요.  
- 앱 인벤토리 세부 정보: 조직에서 Mobile Threat Defense를 사용하는 경우 iOS 디바이스에 있는 앱에 대한 세부 정보를 볼 수 있습니다. [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md)에 대해 자세히 알아보세요. 개인 소유 디바이스가 있는 경우, 조직은 관리되는 앱 인벤토리만 볼 수 있습니다. 회사 소유 디바이스가 있는 경우, 조직은 모든 앱 인벤토리를 볼 수 있습니다.
- 네트워크 정보: Android 디바이스의 네트워크 연결에 대한 일부 정보를 조직 지원에 사용할 수 있습니다. 예를 들어 디바이스를 조직의 특정 건물 내에서 유지해야 할 경우 디바이스는 연결된 네트워크를 식별합니다. 
