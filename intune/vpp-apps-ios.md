---
title: Microsoft Intune에서 iOS 대량 구매 앱 관리
titlesuffix: ''
description: iOS 스토어에서 대량 구매한 앱을 Microsoft Intune에 동기화하고 해당 사용을 추적 및 관리하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 606fe0dfe7160d6fe61366db98b7f22a45216bd0
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229839"
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Microsoft Intune을 사용하여 대량 구매 프로그램을 통해 구매한 iOS 앱을 관리하는 방법


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

iOS 앱 스토어는 회사에서 실행하려는 앱의 라이선스를 여러 개 구매하는 기능을 제공합니다. 여러 복사본을 구매하면 회사에서 앱을 효율적으로 관리할 수 있습니다.

Microsoft Intune에서는 다음을 수행하여 이 프로그램을 통해 구매한 여러 앱 복사본을 관리할 수 있습니다.

- 앱 스토어에서 라이선스 정보 보고.
- 사용한 라이선스 수 추적.
- 소유한 것보다 많은 앱 복사본을 설치하지 않도록 도움.

대량 구매 앱을 할당하는 데 사용할 수 있는 방법은 다음 두 가지입니다.

### <a name="device-licensing"></a>디바이스 라이선싱

디바이스에 앱을 할당하면 하나의 앱 라이선스가 사용되고 사용자가 할당한 디바이스와 연결된 상태로 남아 있습니다.

디바이스에 대량 구매 앱을 할당하면 디바이스의 최종 사용자가 Store에 액세스하기 위해 Apple ID를 제공하지 않아도 됩니다.

### <a name="user-licensing"></a>사용자 라이선스

사용자에게 앱을 할당하면 하나의 앱 라이선스가 사용되고 해당 사용자와 연결됩니다. 앱은 사용자가 소유한 여러 디바이스에서 실행될 수 있습니다(단, Apple에서 제어하는 제한이 적용됨).

사용자에게 대량 구매 앱을 할당할 때 앱 스토어에 액세스하려면 각각의 최종 사용자에 유효하고 고유한 Apple ID가 있어야 합니다.

또한 Apple VPP(Volume Purchase Program) 스토어에서 구매한 책을 Intune에서 동기화, 관리 및 할당할 수 있습니다. 자세한 내용은 [대량 구매 프로그램을 통해 구매한 iOS 전자책을 관리하는 방법](vpp-ebooks-ios.md)을 참조하세요.

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>iOS 디바이스용 대량 구매 앱 관리

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>iOS 디바이스용 Apple Volume Purchase Program 대량 구매 앱 지원

[비즈니스용 Apple Volume Purchase Program](https://www.apple.com/business/vpp/) 또는 [교육용 Apple Volume Purchase Program](https://volume.itunes.apple.com/us/store)을 통해 iOS 앱의 라이선스를 여러 개 구매합니다. 이 프로세스에서는 Apple 웹 사이트에서 Apple VPP 계정을 설정하고 Apple VPP 토큰을 Intune에 업로드합니다.  그런 다음 대량 구매 정보를 Intune과 동기화하고 대량 구매 앱 사용을 추적할 수 있습니다.

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>iOS 디바이스의 기업 간 대량 구매 앱 지원

또한 타사 개발자가 iTunes Connect에서 지정된 권한 있는 Volume Purchase Program for Business 멤버에 대해 개인적으로 앱을 배포할 수도 있습니다. 이러한 VPP for Business 멤버는 Volume Purchase Program 앱 스토어에 로그인하고 해당 앱을 구입할 수 있습니다. 최종 사용자가 구매한 VPP for Business 앱은 Intune 테넌트에 동기화됩니다.

## <a name="before-you-start"></a>시작하기 전에
시작하기 전에 Apple에서 VPP 토큰 하나를 가져와 Intune 계정에 업로드해야 합니다. 또한 다음 조건을 이해해야 합니다.

* 여러 VPP 토큰을 Intune 계정과 연결할 수 있습니다.
* 이전에 VPP 토큰을 다른 제품에 사용한 경우 Intune에 사용할 토큰을 새로 생성해야 합니다.
* 각 토큰은 1년 동안 유효합니다.
* 기본적으로 Intune에서는 하루에 두 번 Apple VPP 서비스와 동기화합니다. 언제든지 수동 동기화를 시작할 수 있습니다.
* Intune에서 Apple VPP를 사용하기 전에 먼저 다른 MDM(모바일 디바이스 관리) 공급업체를 사용하여 만든 기존 VPP 사용자 계정을 제거합니다. Intune은 보안 조치로 해당 사용자 계정을 Intune에 동기화하지 않습니다. Intune은 Intune에서 만든 Apple VPP 서비스의 데이터만 동기화합니다.
* Intune은 최대 256개의 VPP 토큰 추가를 지원합니다.
* Apple DEP(디바이스 등록 프로필) 프로그램은 MDM(모바일 디바이스 관리) 등록을 자동화합니다. DEP를 사용하여 터치하지 않고도 엔터프라이즈 디바이스를 구성할 수 있습니다. Apple의 VPP에서 사용한 것과 동일한 프로그램 에이전트 계정을 사용하여 DEP 프로그램에서 등록할 수 있습니다. Apple 배포 프로그램 ID는 [Apple 배포 프로그램](https://deploy.apple.com) 웹 사이트 아랭 나열된 프로그램에 대해 고유하고 iTunes 스토어와 같은 Apple 서비스에 로그인하는 데 사용할 수 없습니다.
* 사용자 라이선스 모델을 사용하는 VPP 앱을 사용자 또는 디바이스(사용자 선호도 있음)에 할당하는 경우 해당 디바이스에서 Apple 계약조건에 동의할 때 각 Intune 사용자를 고유 Apple ID 또는 메일 주소와 연결해야 합니다.
* 새 Intune 사용자에 대해 디바이스를 설정하는 경우 해당 사용자의 고유한 Apple ID 또는 메일 주소로 구성해야 합니다. Apple ID 또는 메일 주소와 Intune 사용자는 고유한 쌍을 생성하며 최대 5개 디바이스에서 사용할 수 있습니다.
* VPP 토큰은 한 번에 하나의 Intune 계정에만 사용할 수 있습니다. 여러 Intune 테넌트에 대해 동일한 VPP 토큰을 다시 사용하지 마세요.

>[!IMPORTANT]
>VPP 토큰을 Intune으로 가져온 후 같은 토큰을 다른 디바이스 관리 솔루션으로 가져오지 마세요. 가져오면 라이선스 할당과 사용자 레코드가 손실될 수 있습니다.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Apple VPP 토큰을 가져와 업로드하려면

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3.  **Intune** 창의 **설정** 아래에서 **클라이언트 앱** > **iOS VPP 토큰**을 차례로 선택합니다.
4.  VPP 토큰 목록 창에서 **만들기**를 선택합니다.
5. **VPP 토큰 만들기** 창에서 다음 정보를 지정합니다.
    - **VPP 토큰 파일** - 아직 수행하지 않은 경우 비즈니스용 Volume Purchase Program 또는 교육용 Volume Purchase Program에 등록합니다. 등록한 후 계정에 대한 Apple VPP 토큰을 다운로드하여 선택합니다.
    - **Apple ID** - 대량 구매 프로그램과 연결된 계정의 Apple ID를 입력합니다.
    - **국가/지역** - VPP 국가별 스토어를 선택합니다.  Intune은 지정된 VPP 국가 스토어의 모든 로캘에 대해 VPP 앱을 동기화합니다.
        > [!WARNING]  
        > 국가를 변경하면 이 토큰으로 만든 앱에 대한 Apple 서비스를 통한 다음 동기화에서 앱 메타데이터와 스토어 URL이 업데이트됩니다. 앱이 새 국가별 스토어에 없으면 해당 앱은 업데이트되지 않습니다.

    - **VPP 계정 유형** - **비즈니스** 또는 **교육**을 선택합니다.
    - **자동 앱 업데이트** - **켜기** 또는 **끄기**를 선택하여 자동 업데이트를 사용하도록 설정합니다. 사용하도록 설정되면 Intune에서 앱 스토어 내의 VPP 앱 업데이트를 검색하고, 디바이스가 체크 인하면 업데이트를 디바이스에 푸시합니다. Apple VPP 앱에 대한 자동 앱 업데이트는 **필수** 설치 목적으로 배포된 앱만 자동으로 업데이트합니다. **사용 가능** 설치 목적으로 배포된 앱의 경우 자동 업데이트는 새 버전의 앱을 사용할 수 있다는 알림을 관리자를 위해 자동으로 생성합니다. 새 버전의 앱을 설치하려면 설치를 클릭해야 합니다. 또한 이전 버전의 앱이 설치되어 있더라도 회사 포털에는 앱이 설치되지 않은 것으로 사용자에게 표시됩니다. 이 경우 사용자는 앱을 다시 설치할 수 있습니다.
    
        > [!NOTE]
        > 자동 앱 업데이트는 iOS 버전 11.0 이상의 디바이스 및 사용자에게 사용이 허가된 앱 모두에서 작동합니다.
6. 작업이 완료되면 **만들기**를 선택합니다.

토큰은 토큰 목록 창에 표시됩니다.

언제든지 **지금 동기화**를 선택하여 Apple에 보관된 데이터를 Intune과 동기화할 수 있습니다.

## <a name="to-assign-a-volume-purchased-app"></a>대량 구매 앱을 할당하려면

1.  **Intune** 창의 **관리** 아래에서 **클라이언트 앱** > **앱**을 차례로 선택합니다.
2.  앱 목록 창에서 할당할 앱을 선택한 다음, **할당**을 선택합니다.
3.  ***앱 이름*** - **할당**에서 **그룹 선택**을 선택한 다음, **그룹 추가** 창에서 **할당 형식**을 선택하고, 앱을 할당하려는 Azure AD 사용자 또는 디바이스 그룹을 선택합니다.
5.  선택한 각 그룹에 대해 다음 설정을 선택합니다.
    - **형식** - 앱이 **사용 가능**(최종 사용자가 회사 포털에서 앱 설치 가능)인지 또는 **필수**(최종 사용자 디바이스에서 자동으로 앱 설치)인지를 선택합니다.
    - **라이선스 형식** - **사용자 라이선싱** 또는 **디바이스 라이선싱**을 선택합니다.
6.  작업이 끝나면 **저장**을 선택합니다.


>[!NOTE]
>표시되는 앱 목록은 토큰과 관련이 있습니다. 여러 개의 VPP 토큰과 연결된 앱이 있을 경우 동일한 앱이 각 토큰마다 한 번씩, 여러 번 표시됩니다.

## <a name="end-user-prompts-for-vpp"></a>VPP에 대한 최종 사용자 프롬프트

최종 사용자는 다양한 시나리오에서 VPP 앱을 설치하도록 요구하는 메시지를 받게 됩니다. 다음 표에서는 각 조건에 대해 설명합니다.

| # | 시나리오                                | Apple VPP 프로그램에 초대                              | 앱 설치 프롬프트 | Apple ID에 대한 프롬프트 |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – 사용이 허가된 사용자                             | Y                                                                                               | Y                                           | Y                                 |
| 2 | 회사 – 사용이 허가된 사용자(감독되지 않은 디바이스)     | Y                                                                                               | Y                                           | Y                                 |
| 3 | 회사 – 사용이 허가된 사용자(감독된 디바이스)         | Y                                                                                               | N                                           | Y                                 |
| 4 | BYOD – 사용이 허가된 디바이스                           | N                                                                                               | Y                                           | N                                 |
| 5 | 회사 – 사용이 허가된 디바이스(감독되지 않은 디바이스)                           | N                                                                                               | Y                                           | N                                 |
| 6 | 회사 – 사용이 허가된 디바이스(감독된 디바이스)                           | N                                                                                               | N                                           | N                                 |
| 7 | 키오스크 모드(감독된 디바이스) – 사용이 허가된 디바이스 | N                                                                                               | N                                           | N                                 |
| 8 | 키오스크 모드(감독된 디바이스) – 사용이 허가된 사용자   | --- | ---                                          | ---                                |

> [!Note]  
> VPP 사용자 라이선스를 사용하여 VPP 앱을 키오스크 모드 디바이스에 할당하는 것은 권장되지 않습니다.

## <a name="revoking-app-licenses-and-deleting-tokens"></a>앱 라이선스 취소 및 토큰 삭제 

지정된 디바이스, 사용자 또는 앱에 따라 모든 연결된 iOS VPP(volume-purchase program) 앱 라이선스를 철회할 수 있습니다. 앱이 더 이상 할당되지 않는 경우 사용자에게 알릴 수 있습니다. 앱 라이선스를 철회해도 디바이스에서 관련 VPP 앱이 제거되지 않습니다. VPP 앱을 제거하고 사용자 또는 디바이스에 할당된 앱 라이선스를 회수하려면 할당 작업을 변경하여 **제거**해야 합니다. 사용자에게 할당된 앱을 제거하는 경우 Intune은 사용자 또는 디바이스 라이선스를 회수하고 디바이스에서 앱을 제거합니다. 회수된 라이선스 수는 Intune의 **앱** 워크로드의 **사용이 허가된 앱** 노드에 반영됩니다. VPP 앱이 제거되고 앱 라이선스가 회수되면 다른 사용자 또는 디바이스에 앱 라이선스 할당을 선택할 수 있습니다. 

>[!NOTE]
>직원이 퇴직하면서 더 이상 AAD 그룹에 속하지 않을 때 Intune은 모든 사용자에게 라이선스가 허가된 iOS VPP 앱 라이선스를 검색합니다.

<!-- 820879 -->  
콘솔을 사용하여 iOS VPP(Volume-Purchase Program) 토큰을 삭제할 수 있습니다. VPP 토큰의 중복 인스턴스가 있는 경우 이 기능이 필요할 수 있습니다. 토큰을 삭제하면 연결된 모든 앱과 할당도 삭제하게 됩니다. 그러나 토큰을 삭제하면 앱 라이선스를 해지하거나 앱을 제거하지 않습니다. 

>[!NOTE]
>Intune은 토큰이 삭제된 후에 앱 라이선스를 취소할 수 없습니다. 

<!-- 820870 -->  
지정된 VPP 토큰에 대해 모든 VPP 앱 라이선스를 해지하려면 먼저 토큰과 연결된 모든 앱 라이선스를 해지한 다음, 해당 토큰을 삭제해야 합니다.

## <a name="renewing-app-licenses"></a>앱 라이선스 갱신

Apple Volume Purchase Program 포털에서 새로운 토큰을 다운로드하고 Intune에서 기존 토큰을 업데이트하여 Apple VPP 토큰을 갱신할 수 있습니다.

## <a name="deleting-an-ios-vpp-app"></a>iOS VPP 앱 삭제

현재 iOS VPP 앱은 Microsoft Intune에서 삭제할 수 없습니다.

## <a name="additional-information"></a>추가 정보

적합한 디바이스를 가진 사용자가 디바이스에 VPP 앱을 처음 설치하려고 하면 Apple Volume Purchase Program에 가입하라는 메시지가 표시됩니다. 가입해야만 앱 설치가 진행됩니다. Apple 대량 구매 프로그램 참여 초대를 받으려면 사용자가 iOS 디바이스에서 iTunes 앱을 사용할 수 있어야 합니다. iTunes Store 앱을 사용하지 않도록 하는 정책을 설정한 경우에는 VPP 앱용 사용자 기반 라이선싱이 적용되지 않습니다. 이 경우에는 정책을 제거하여 iTunes 앱을 허용하거나, 디바이스 기반 라이선싱을 사용하면 됩니다.

Apple에서는 VPP 토큰을 만들고 갱신하기 위한 직접적인 지원을 제공합니다. 자세한 내용은 Apple 설명서의 일부인 [VPP(볼륨 구매 프로그램)를 이용하여 사용자에게 콘텐츠 배포하기](https://go.microsoft.com/fwlink/?linkid=2014661)를 참조하세요. 

Intune 포털에 **외부 MDM에 할당됨**이 표시되는 경우 관리자는 Intune에서 VPP 토큰을 사용하기 전에 타사 MDM에서 VPP 토큰을 제거해야 합니다.

## <a name="frequently-asked-questions"></a>질문과 대답

#### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>앱이 설치되거나 디바이스에서 제거되면 포털이 라이선스 개수를 업데이트하는 데 얼마나 걸리나요?
라이선스는 앱을 설치하거나 제거한 후에 몇 시간 이내에 업데이트되어야 합니다. 최종 사용자가 디바이스에서 앱을 제거하는 경우 라이선스는 여전히 해당 사용자 또는 디바이스에 할당되어 있습니다.

#### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>앱을 초과 구독할 수 있나요, 그렇다면 어떤 상황에서 가능한가요?
예. Intune 관리자는 앱을 초과 구독할 수 있습니다. 예를 들어 관리자가 XYZ 앱에 대한 100개의 라이선스를 구입한 다음, 500명의 멤버를 포함한 그룹에 앱을 대상으로 지정하는 경우 처음 100명의 멤버(사용자 또는 디바이스)는 라이선스를 할당받습니다. 그리고 나머지 멤버는 라이선스 할당에 실패합니다.

#### <a name="i-understand-intune-automatically-syncs-app-licenses-each-day-with-apple-is-that-correct"></a>Intune이 Apple과 앱 라이선스를 매일 자동으로 동기화하는 것이 맞나요?
Intune에서는 Apple과 하루에 두 번 앱 라이선스를 동기화합니다.

## <a name="next-steps"></a>다음 단계

앱 할당을 모니터링하는 데 유용한 정보는 [앱을 모니터링하는 방법](apps-monitor.md)을 참조하세요.
