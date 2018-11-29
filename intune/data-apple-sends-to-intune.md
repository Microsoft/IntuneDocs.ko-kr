---
title: Apple이 Intune에 보내는 데이터
titleSuffix: Microsoft Intune
description: Apple이 Intune에 보내는 데이터 목록입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cf27fdb8-f408-425c-9a7c-146de1534425
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 12f9b6aa5fb9a7b1f31b43dc7faf3e36cdd49157
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186548"
---
# <a name="data-apple-sends-to-intune"></a>Apple이 Intune에 보내는 데이터

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

장치에서 다음 Apple 서비스를 사용하도록 설정할 경우 Microsoft Intune이 Apple에 연결하여 사용자 및 장치 정보를 공유합니다.

- [Apple 장비 등록 프로그램(DEP)](device-enrollment-program-enroll-ios.md)
- [Apple MDM 푸시 인증서(APNs)](apple-mdm-push-certificate-get.md)
- [Apple School Manager(ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Apple Volume Purchase Program(VPP)](vpp-apps-ios.md)

Microsoft Intune이 연결을 설정하기 전에 Apple 서비스 각각에 대해 Apple 계정을 만들어야 합니다.

다음 표에는 Apple 장치가 Intune에 보내는 데이터가 나와 있습니다. [Intune에서도 Apple에 데이터를 보냅니다](data-intune-sends-to-apple.md). 

| 서비스 | 메시지 | Intune에 보내는 데이터 | 사용 목적 |
|:---:|:---:|:---:| ---|
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 토큰 인증 | MessageType | 메시지 유형(인증) |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 토큰 인증 | 항목 | 장치에서 수신 대기하는 토픽 |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 토큰 인증 | MesUDID | 장치 UDID |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 토큰 인증 | OSVersion | 장치의 OS 버전 |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 토큰 인증 | BuildVersion | 장치의 빌드 버전 |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 토큰 인증 | ProductName | 장치의 제품 이름 |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 토큰 인증 | SerialNumber | 장치 일련 번호 |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 토큰 인증 | IMEI | 장치의 IMEI(International station Mobile Equipment Identity) |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 토큰 인증 | MEID | 장치의 MEID(Mobile Equipment Identifier) |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | 항목 | 장치에서 수신 대기하는 토픽 |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | UDID | 장치의 UDID |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | 토큰 | 장치의 푸시 토큰. 서버는 장치에 푸시 알림을 보낼 때 이 업데이트된 토큰을 사용해야 합니다. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | PushMagic | 푸시 알림 메시지에 포함되어야 하는 자동 문자열  |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | UnlockToken | 장치를 잠금 해제하는 데 사용할 수 있는 데이터 Blob |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | AwaitingConfiguration | true로 설정하면 장치가 설정 도우미를 진행하기 전에 DeviceConfigured MDM 명령을 기다립니다.  |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 체크 아웃 | MessageType | 메시지 유형(체크 아웃) |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 체크 아웃 | 항목 | 장치에서 수신 대기하는 토픽 |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 체크 아웃 | UDID | 장치의 UDID |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | MDM 프로토콜 | 상태 | 상태  |
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | MDM 프로토콜 | UDID |장치의 UDID  |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | MDM 프로토콜 | CommandUUID | 이 응답이 사용되는 명령의 UUID |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | MDM 프로토콜 | ErrorChain | 발생한 오류 체인을 나타내는 사전 배열  |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 일련 번호 | 장치 일련 번호 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | model | 장치의 모델 이름 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 설명 | 장치에 대한 설명 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 색상 | 장치의 색 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 자산 태그 | 장치의 자산 태그 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 프로필 상태 | 프로필 설치 상태 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 프로필 UUID | 할당된 프로필의 UUID |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 프로필 할당 시간 | 프로필이 장치에 할당된 경우를 나타내는 ISO 8601 형식의 타임스탬프 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 프로필 푸시 시간 | 프로필이 장치에 푸시된 경우를 나타내는 ISO 8601 형식의 타임스탬프|
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 장치 할당 날짜 | 장치가 장치 등록 프로그램에 등록되었음을 나타내는 ISO 8601 형식의 타임스탬프 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 장치 할당자 | 장치에 할당된 사용자의 이메일입니다. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | OS | 장치 운영 체제 |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | 등록 프로그램 토큰 | 장치 제품군 | 장치의 Apple 제품군 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | Apple 사용자 ID | Apple에서 생성된 사용자 ID |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 응용 프로그램 설명 | VPP 응용 프로그램에 대한 설명 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 응용 프로그램 아이콘 | VPP 앱에 대한 Apple 호스트됨 아이콘의 URL |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 응용 프로그램 ID | Apple 응용 프로그램 ID(adamsId라고도 함) |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 응용 프로그램 이름 | VPP 응용 프로그램 이름 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | assignedCount | 앱에 대해 할당된 라이선스 수 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | availableCount | 앱에 대해 할당되지 않은 라이선스 수 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | bundleId | 앱의 bundleId |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 저작권 | 앱의 저작권 정보 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | CountryCode | VPP 프로그램의 국가 코드 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | deviceAssignable | 관리자가 앱에 대해 장치 라이선스를 할당할 수 있는 경우 Apple에서 true가 반환됩니다. 할당할 수 없으면 false가 반환됩니다. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | facilitatorMemberId | VPP 계정 진행자의 구성원 ID  |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 장르 | 앱 장르 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | Intune UserId guid | Intune에서 생성된 GUID |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | isIrrevocable | 라이선스를 해지할 수 없는 경우 Apple에서 true가 반환됩니다. 해지할 수 있으면 false가 반환됩니다. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 라이선스 ID | 특정 라이선스를 식별하기 위해 Apple에서 생성된 ID |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 위치 | Apple VPP 구성 데이터에 저장된 위치 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 관리되는 AppleId UPN | 사용자, 관리자 및 진행자 구성원의 Apple ID 메일 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | OrganizationId | Apple에서 할당된 조직 ID |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | pricingParam | 앱의 Apple 가격 유형 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | productType | VPP 응용 프로그램의 제품 유형 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | retiredCount | 앱에 대해 사용 중지된 라이선스 수 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | totalCount | 앱에 대해 구매한 총 라이선스 수 |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | url | 앱의 iTunes 스토어 URL|
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Apple VPP 토큰 | 사용자 상태 | Apple VPP 프로그램의 사용자 상태 |


Microsoft Intune으로 Apple 서비스 사용을 중단하고 데이터를 삭제하려면 Microsoft Intune Apple 토큰을 사용하지 않을 뿐 아니라 Apple 계정도 삭제해야 합니다. 계정 관리를 수행하는 방법은 Apple 계정을 참조하세요.


