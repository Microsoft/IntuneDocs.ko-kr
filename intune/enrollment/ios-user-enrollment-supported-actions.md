---
title: Apple 사용자 등록에서 지원되는 Intune 작업 및 옵션
titleSuffix: Microsoft Intune
description: Apple 사용자 등록에서 지원되는 Intune 작업 및 옵션 알아보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: acf1112f96b28b156b3c4857485de30d7ad553ef
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955251"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Apple 사용자 등록에서 지원되는 Intune 작업 및 옵션

사용자 등록에서는 디바이스 관리 옵션의 하위 집합을 지원합니다. 기존 구성 프로필이 사용자 등록 디바이스에 적용되는 경우 사용자 등록에서 지원하는 설정만 해당 디바이스에 적용됩니다.

## <a name="password-settings"></a>암호 설정

사용자 등록 디바이스에서 어떤 암호 설정이든 구성하면 **단순 암호** 설정이 자동으로 **차단**으로 설정되고 6자리 PIN이 적용됩니다.

예를 들어 **암호 만료** 설정을 구성하고 이 정책을 사용자가 등록한 장치에 푸시하면 디바이스에 다음과 같은 상황이 발생합니다.
- **암호 만료** 설정은 무시됩니다.
- `1111` 또는 `1234`와 같은 단순 암호는 허용되지 않습니다.
- 6자리 PIN이 적용됩니다.

## <a name="administrator-remote-device-actions-and-options"></a>관리자 원격 디바이스 작업 및 옵션
관리자는 사용자 등록 디바이스에서 다음과 같은 작업 및 옵션을 수행할 수 있습니다.
- 사용 중지
- 삭제
- 원격 잠금
- 동기화

그 밖의 모든 작업은 지원되지 않습니다.

## <a name="end-user-actions"></a>최종 사용자 작업
최종 사용자는 사용자 등록 디바이스의 회사 포털 애플리케이션 및 웹 사이트에서 해당 디바이스에 대해 이러한 작업을 수행할 수 있습니다.
- 이름 바꾸기. 이 작업은 회사 포털 내에서 사용자에게 표시되는 이름에만 해당됩니다. 이 컨텍스트 외부에 있는 디바이스의 이름은 완전히 바꾸지 않습니다.
- 제거
- 원격 잠금
- 상태 확인

## <a name="other-supported-options"></a>기타 지원 옵션

Apple 사용자 등록을 사용하여 등록된 디바이스에 대해 Intune에서 지원하는 옵션은 다음과 같습니다.
- 앱별 VPN 사용자 등록에서 Safari 설정 구성을 지원하지 않으므로 이 지원에서 Safari 도메인은 제외됩니다.
- WiFi 
- 등록 취소 시 회사 앱 제거
- 사용자에게 사용이 허가된 VPP(대량 구매 계획)를 통한 앱 배포
- 탈옥 검색

지원되는 제한 사항은 다음과 같습니다.
- 관리되지 않는 앱에서 회사 문서 보기
- 회사 앱에서 사외 문서 보기
- 관리되지 않는 앱이 관리 연락처 계정에서 연락처를 읽을 수 있도록 허용
- 관리되지 않는 대상인 AirDrop
- 필요한 암호화 백업
- 클라우드에 관리 앱 동기화
- 디바이스가 잠겨 있는 동안 제어 센터 액세스
- 디바이스가 잠겨 있는 동안 알림 센터 액세스
- 디바이스가 잠겨 있는 동안 오늘 보기
- 스크린샷 차단
- Enterprise Book 백업 차단
- Enterprise Book 메타데이터 동기화 차단
- 암호화된 백업 필요
- 손목 인식 필요
- Siri 차단
- 디바이스가 잠겨 있는 동안 Siri 차단
- Safari 사기 경고 필요
- Apple에 대한 진단 제출 차단


## <a name="options-not-supported"></a>지원되지 않는 옵션
다음 옵션은 사용자 등록으로 등록된 디바이스에서 지원되지 않습니다. 이러한 옵션이 필요하면 개인 소유 디바이스에 대한 디바이스 등록이나 회사 디바이스에 대한 자동 디바이스 등록을 확인하세요.
- 관리 APFS 볼륨 외부에서 앱에 대해 앱 인벤토리를 수집합니다.
- 관리 APFS 볼륨 외부에서 인증서 및 프로비저닝 프로필의 인벤토리를 수집합니다.
- UDID 및 기타 영구 디바이스 식별자를 수집합니다.
- 사용자 등록에서는 등록된 각 디바이스에 대해 고유한 등록 ID를 지원하지만 등록 취소 후에는 이 ID가 유지되지 않습니다.
- 이러한 제한으로 인해 지원되지 않는 Intune 기능은 다음과 같습니다.
- 주체 이름 형식의 일련 번호가 있는 SCEP 사용자 프로필.
- 디바이스 수준 VPN.
- 디바이스에 사용이 허가된 VPP 앱 배포.
- 관리 APFS 볼륨 외부의 애플리케이션에 대한 MDM 제어.
- 애플리케이션 보호 정책은 이러한 앱에 계속 적용됩니다. 그러나 사용자가 이 앱의 관리 버전을 디바이스에서 삭제하지 않으면 이 앱에 대한 관리를 인수받거나 이 앱을 배포할 수 없습니다.
- 감독해야 하는 작업, 구성, 설정 및 명령입니다. 

## <a name="next-steps"></a>다음 단계

[iOS 및 iPadOS 사용자 등록 설정](ios-user-enrollment.md)