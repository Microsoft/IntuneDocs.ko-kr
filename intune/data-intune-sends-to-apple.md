---
title: Intune이 Apple에 보내는 데이터
titleSuffix: Microsoft Intune
description: Intune이 Apple에 보내는 데이터 목록입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1fbf8f37b989112025bd6d54328dd61246913f7
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57400214"
---
# <a name="data-intune-sends-to-apple"></a>Intune이 Apple에 보내는 데이터

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

다음의 모든 Apple 서비스가 디바이스 디바이스에서 사용되는 경우 Microsoft Intune이 Apple과 연결되고 Apple과 사용자 및 디바이스 정보를 공유합니다. 

- [Apple 장비 등록 프로그램(DEP)](device-enrollment-program-enroll-ios.md)
- [Apple MDM 푸시 인증서(APNS)](apple-mdm-push-certificate-get.md)
- [Apple School Manager(ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Apple Volume Purchase Program(VPP)](vpp-apps-ios.md)

Microsoft Intune이 연결을 설정하기 전에 Apple 서비스 각각에 대해 Apple 계정을 만들어야 합니다.

다음 표에서는 Microsoft Intune이 디바이스에서 사용하는 Apple 서비스로 보내는 데이터를 나열합니다. 

| 서비스 | Apple에 보낸 데이터 | 사용 목적 |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token, PushMagic | 서버가 디바이스를 채택하는 경우 해당 디바이스는 서버에 푸시 알림 디바이스 토큰을 제공합니다. 서버는 이 토큰을 사용해 해당 디바이스에 푸시 메시지를 보내야 합니다. 이 체크 인 메시지도 PushMagic 문자열을 포함합니다. 서버는 해당 문자열을 기억하고 해당 디바이스에 보내는 모든 푸시 메시지에 포함시켜야 합니다. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 서버 토큰 | Apple 서비스를 인증하는 데 사용된 푸시 알림 디바이스 토큰입니다. |
| ASM/DEP | server_name | MDM 서버에 대해 식별 가능한 이름입니다. |
| ASM/DEP | server_uuid | 시스템 생성 서버 식별자입니다. |
| ASM/DEP | admin_id | 사용 중인 현재 토큰을 생성한 사용자의 Apple ID입니다. |
| ASM/DEP | org_name | 조직 이름입니다. |
| ASM/DEP | org_email | 조직의 이메일 주소입니다. |
| ASM/DEP | org_phone | 조직의 전화입니다. |
| ASM/DEP | org_address | 조직의 주소입니다. |
| ASM/DEP | org_id | DEP 고객 ID입니다. 이 키는 프로토콜 버전 3 이상에서만 사용할 수 있습니다. |
| ASM/DEP | serial_number | 디바이스 일련 번호(문자열)입니다. |
| ASM/DEP | model | 모델 이름(문자열)입니다. |
| ASM/DEP | description | 디바이스(문자열)에 대한 설명입니다. |
| ASM/DEP | asset_tag | 디바이스의 자산 태그(문자열)입니다. |
| ASM/DEP | profile_status | 프로필의 설치 상태입니다. 가능한 값: **빈**, **할당됨**, **푸시됨** 또는 **제거됨**입니다. |
| ASM/DEP | profile_uuid | 지정된 프로필의 고유 ID입니다. |
| ASM/DEP | device_assigned_by | 디바이스에 할당된 사용자의 이메일입니다. |
| ASM/DEP | os | 디바이스 운영 체제: iOS, OSX, 또는 tvOS입니다. 이 키는 X-서버-프로토콜-버전 2 이상에서 유효합니다. |
| ASM/DEP | device_family | 디바이스의 Apple 제품군: iPad, iPhone, iPod, Mac 또는 AppleTV입니다. 이 키는 X-서버-프로토콜-버전 2 이상에서 유효합니다. |
| ASM/DEP | profile_name | 문자열입니다. 사람이 읽을 수 있는 프로필 이름입니다. |
| ASM/DEP | support_phone_number | 선택 사항입니다. 문자열입니다. 조직에 대한 지원 전화 번호입니다. |
| ASM/DEP | support_email_address | 선택 사항입니다. 문자열입니다. 조직에 대한 지원 이메일입니다. 이 키는 X-서버-프로토콜-버전 2 이상에서 유효합니다. |
| ASM/DEP | department | 선택 사항입니다. 문자열입니다. 사용자 정의 부서 또는 위치 이름입니다. |
| ASM/DEP | 장치 | 디바이스 일련 번호를 포함하는 문자열의 배열입니다. (비어 있을 수 있습니다.) |
| VPP | Intune UserId guid | Intune으로 생성된 GUID입니다. |
| VPP | 관리되는 AppleId UPN | Apple과 VPP 토큰 연결을 구성할 경우 관리자가 지정한 AppleID입니다. |
| VPP | 일련 번호 | 관리 디바이스의 일련 번호입니다. |

Microsoft Intune으로 Apple 서비스 사용을 중단하고 데이터를 삭제하려면 Microsoft Intune Apple 토큰을 사용하지 않을 뿐 아니라 Apple 계정도 삭제해야 합니다. 계정 관리를 수행하는 방법은 Apple 계정을 참조하세요.


