---
title: Microsoft Intune 장치 등록이란?
titlesuffix: Microsoft Intune
description: iOS, Android 및 Windows 장치 등록에 대해 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: c46a90d36ba8b50703e62fc663b1d090ac1bcfc7
ms.sourcegitcommit: b96568a77d3cb6f602e7577446996fe7dde169bd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51610127"
---
# <a name="what-is-device-enrollment"></a>장치 등록이란?
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune을 사용하여 직원의 장치 및 앱을 관리하고 회사 데이터에 액세스하는 방법을 관리할 수 있습니다. 이 모바일 장치 관리(MDM)를 사용하려면 먼저 장치를 Intune 서비스에 등록해야 합니다. 장치가 등록되면 MDM 인증서가 발급됩니다. 이 인증서는 Intune 서비스와 통신하는 데 사용됩니다.

다음 표에서 볼 수 있듯이 직원의 장치를 등록하는 몇 가지 방법이 있습니다. 각 방법은 장치의 소유권(개인 또는 회사), 기기 유형(iOS, Windows, Android) 및 관리 요구 사항(재설정, 선호도, 잠금)에 따라 다릅니다.

기본적으로 모든 플랫폼의 장치를 Intune에서 등록할 수 있습니다. 그러나 [플랫폼별로 장치를 제한](enrollment-restrictions-set.md#set-device-type-restrictions)할 수 있습니다.

## <a name="ios-enrollment-methods"></a>iOS 등록 방법

| **방법** |  **초기화 필요** |    [**사용자 선호도**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) |   **잠김** | **세부 정보** |
|:---:|:---:|:---:|:---:|:---:|
| | 장치는 등록 중 초기화됩니다. |  각 장치를 사용자와 연결합니다.| 사용자가 장치 등록을 해제할 수 없습니다.  | |
|**[BYOD](#bring-your-own-device)** | 아니요|   예 |   아니요 | [추가 정보](./apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| 아니요 |아니요 |아니요  | [추가 정보](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**|   예 |   선택 사항 |  선택 사항|[추가 정보](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| 예 |   선택 사항 |  아니요| [추가 정보](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| 아니요 |    아니요  | 아니요|[추가 정보](./apple-configurator-direct-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>macOS 등록 방법
| **방법** |  **초기화 필요** |  **사용자 선호도** | **잠김** | **세부 정보**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | 아니요| 예 | 아니요 | [추가 정보](./macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| 아니요 |아니요 |아니요  | [추가 정보](./device-enrollment-manager-enroll.md)|


## <a name="windows-enrollment-methods"></a>Windows 등록 방법

| **방법** |  **초기화 필요** |    **사용자 선호도**   |   **잠김** | **세부 정보**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | 아니요 |  예 |   아니요 | [추가 정보](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| 아니요 |아니요 |아니요  |[추가 정보](device-enrollment-manager-enroll.md)|
|**자동 등록** | 아니요 |예 |아니요 | [추가 정보](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |예 |예 |아니요 | [자세한 정보](enrollment-autopilot.md)]
|**대량 등록** |아니요 |아니요 |아니요 | [추가 정보](./windows-bulk-enroll.md) |
|**공동 관리** |아니요 |예 |아니요 | [자세한 정보](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)]
|**GPO** |아니요 |예 |아니요 | [자세한 정보](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)]


## <a name="android-enrollment-methods"></a>Android 등록 방법

| **방법** |  **초기화 필요** |    **사용자 선호도**   |   **잠김** | **세부 정보**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | 아니요|   예 |   아니요 | [추가 정보](./android-enroll.md)|
|**[DEM](#device-enrollment-manager)**| 아니요 |아니요 |아니요  |[추가 정보](./device-enrollment-manager-enroll.md)|
|**Android 회사 프로필**| 아니요 | 예 | 아니요| [추가 정보](./android-work-profile-enroll.md) |


## <a name="bring-your-own-device"></a>Bring Your Own Device
Bring Your Own Device(BYOD)에는 개인 전화, 태블릿 및 PC가 있습니다. 사용자는 회사 포털 앱을 설치 및 실행하여 BYOD를 등록합니다. 사용자는 이 프로그램을 통해 전자 메일 등의 회사 리소스에 액세스할 수 있습니다.

## <a name="corporate-owned-device"></a>회사 소유 장치
[COD(회사 소유 장치)](corporate-identifiers-add.md)에는 회사가 직원에게 배포한 전화, 태블릿, PC가 있습니다. COD 등록은 자동 등록, 공유 장치 또는 사전 승인된 등록 요구 사항과 같은 관리 시나리오를 지원합니다. COD를 등록하는 일반적인 방법은 관리자가 장치 등록 관리자(DEM)를 사용하는 것입니다. Apple에서 제공한 장비 등록 프로그램(DEP) 도구를 통해 iOS 장치를 직접 등록할 수 있습니다. IMEI 번호가 있는 장치도 회사 소유로 식별되고 태그가 지정됩니다.

### <a name="device-enrollment-manager"></a>장치 등록 관리자
DEM(장치 등록 관리자)은 회사 소유 장치를 여러 개 등록하여 관리할 수 있는 특수 사용자 계정입니다. 관리자는 회사 포털을 설치하고 사용자가 없는 많은 장치를 등록할 수 있습니다. 이러한 장치 유형은 예를 들어 POS(Point-Of-Sale) 또는 유틸리티 앱에는 유용하지만 이메일 또는 회사 리소스에 액세스해야 하는 사용자에게는 유용하지 않습니다. [DEM](./device-enrollment-manager-enroll.md)에 대해 자세히 알아보세요. 

### <a name="apple-device-enrollment-program"></a>Apple 장비 등록 프로그램
Apple DEP(장치 등록 프로그램) 관리에서는 정책을 만든 후, 구입한 iOS 장치 중에서 DEP로 관리하는 장치에 "무선으로" 정책을 배포할 수 있습니다. 사용자가 처음으로 장치를 켜고 iOS 설치 도우미를 실행하면 장치가 등록됩니다. 이 방법은 iOS 감독 모드를 지원하며, 이 모드에서는 특정 기능을 사용하여 장치를 구성할 수 있습니다.

iOS DEP 등록에 대한 자세한 내용은 다음을 참조하세요.

- [iOS 장치를 등록하는 방법 선택](ios-enroll.md)
- [장치 등록 프로그램을 사용하여 iOS 장치 등록](https://docs.microsoft.com/intune/device-restrictions-ios#device-enrollment-program)

### <a name="usb-sa"></a>USB-SA
IT 관리자는 USB를 통해 Apple Configurator를 사용하여 등록할 각 회사 소유 장치를 설정 도우미를 사용하여 수동으로 준비합니다. IT 관리자는 등록 프로필을 만들어 Apple Configurator로 내보냅니다. 사용자가 장치를 받으면 [설정 도우미]를 실행하여 장치를 등록하라는 메시지가 표시됩니다. 이 방법은 **iOS 감독** 모드를 지원하며, 이 모드에서는 다음 기능을 사용할 수 있습니다.
  - 잠긴 등록
  - 키오스크 모드와 다른 고급 구성 및 제한 사항

설정 도우미를 사용한 iOS Apple Configurator 등록에 대한 자세한 내용은 다음을 참조하세요.

- [iOS 장치를 등록하는 방법 결정](enrollment-method-choose-ios.md)
- [Configurator 및 설정 도우미를 사용하여 iOS 장치 등록](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
직접 등록의 경우 관리자가 등록 정책을 만들고 Apple Configurator로 내보내어 각 장치를 수동으로 등록해야 합니다. USB로 연결된 회사 소유의 장치는 직접 등록되고 초기화할 필요가 없습니다. 장치는 사용자가 지정되지 않은 장치로 관리됩니다. 장치는 잠기거나 감독이 되지 않으며, 조건부 액세스, 탈옥 검색, 모바일 응용 프로그램 관리를 지원할 수 없습니다.

iOS 등록에 대한 자세한 내용은 다음을 참조하세요.

- [iOS 장치를 등록하는 방법 결정](enrollment-method-choose-ios.md)
- [Configurator 및 직접 등록을 사용하여 iOS 장치 등록](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Exchange ActiveSync와 Intune을 사용한 모바일 장치 관리
EAS MDM 정책을 사용하면 등록되지는 않았지만 EAS(Exchange ActiveSync)에 연결하는 모바일 장치를 Intune에서 관리할 수 있습니다. Intune에서는 Exchange 커넥터를 사용하여 EAS 및 클라우드 호스티드 온-프레미스와 통신합니다. 자세한 내용은 곧 제공 예정

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 인증서 만료 후 모바일 장치 정리

MDM 인증서는 모바일 장치가 Intune 서비스와 통신할 때 자동으로 갱신됩니다. 모바일 장치가 초기화되거나 일정 기간 동안 Intune 서비스와 통신하지 못한 경우에는 MDM 인증서가 갱신되지 않습니다. MDM 인증서가 만료되고 180일 후 Azure Portal에서 장치가 제거됩니다.
