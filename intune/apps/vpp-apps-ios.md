---
title: Apple 대량 구매 앱 관리
titleSuffix: Microsoft Intune
description: iOS 및 macOS App Store에서 대량 구매한 앱을 Microsoft Intune에 동기화하고 해당 사용을 추적 및 관리하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d965ac35719d809ab922d28f76dec1754e9a4c6b
ms.sourcegitcommit: 9b29478f815e10c46c8030abe0146d601ce0e28c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051629"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Microsoft Intune을 사용하여 Apple Volume Purchase Program을 통해 구매한 iOS 및 macOS 앱을 관리하는 방법


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple을 사용하면 사용자의 조직 내에서 [Apple Business Manager](https://business.apple.com/)나 [Apple School Manager](https://school.apple.com/)를 이용 중인 iOS 및 macOS 디바이스로 사용하려는 앱에 대해 여러 라이선스를 구매할 수 있습니다. 그런 다음 대량 구매 정보를 Intune과 동기화하고 대량 구매 앱 사용을 추적할 수 있습니다. 앱 라이선스를 구매하면 회사 내에서의 효율적 앱 관리, 구매된 앱의 소유권 보유와 지속적인 제어가 가능합니다. 

Microsoft Intune에서는 다음을 수행하여 이 프로그램을 통해 구매한 앱을 관리할 수 있습니다.

- Apple Business Manager에서 다운로드하는 위치 토큰을 동기화합니다.
- 구매된 앱에 사용 가능하거나 이미 사용된 라이선스의 수를 추적합니다.
- 사용자가 소유한 라이선스 수만큼 앱을 설치하는 데 도움이 됩니다.

또한 Apple Business Manager에서 구매한 책을 Intune에서 iOS로 동기화, 관리 및 할당할 수 있습니다. 자세한 내용은 [대량 구매 프로그램을 통해 구매한 iOS 전자책을 관리하는 방법](vpp-ebooks-ios.md)을 참조하세요.

## <a name="what-are-location-tokens"></a>위치 토큰이란 무엇인가요?
위치 토큰은 VPP(Volume Purchase Program) 토큰이라고도 합니다. 이 토큰은 Apple Business Manager를 사용하여 구매한 라이선스를 할당 및 관리하는 데 사용됩니다. 콘텐츠 관리자는 Apple Business Manager에서 권한을 보유한 위치 토큰으로 라이선스를 구매하고 연결할 수 있습니다. 이러한 위치 토큰은 이후에 Apple Business Manager에서 다운로드되고 Microsoft Intune에서 업로드됩니다. Microsoft Intune은 테넌트별로 여러 위치 토큰의 업로드를 지원합니다. 각 토큰은 1년 동안 유효합니다.

## <a name="how-are-purchased-apps-licensed"></a>구매한 앱의 라이선스는 어떻게 되나요?
구매한 앱은 Apple에서 iOS 및 macOS 디바이스에 대해 제공하는 두 유형의 라이선스를 사용하여 그룹에 할당할 수 있습니다.

|   | 디바이스 라이선싱 | 사용자 라이선싱 |
|-----|------------------|----------------|
| **앱 스토어 로그인** | 필수 아님. | 각 최종 사용자는 App Store에 로그인하라는 메시지가 표시될 때 고유의 Apple ID를 사용해야 함. |
| **App Store 액세스가 차단되는 디바이스 구성** | 앱은 회사 포털로 설치 및 업데이트할 수 있음. | Apple VPP 가입 초대에는 App Store 액세스 권한이 필요함. App Store를 사용하지 않도록 하는 정책을 설정한 경우에는 VPP 앱용 사용자 라이선싱이 적용되지 않음. |
| **자동 앱 업데이트** | 앱의 **할당 유형**이 **필수**일 경우 Apple VPP 토큰 설정에서 Intune 관리자에 의해 구성됨. <br> <br> **할당 유형**이 **등록된 디바이스에 사용 가능**일 경우에는 사용 가능한 앱 업데이트를 회사 포털에서 설치할 수 있음. | 개인 앱 스토어 설정에서 최종 사용자가 구성함. Intune 관리자는 관리할 수 없음. |
| **사용자 등록** | 지원 안 됨 | 관리형 Apple ID를 사용하여 지원됨. |
| **책** | 지원 안 됨 | 지원됨. |
| **사용된 라이선스 수** | 디바이스당 1개 라이선스임. 라이선스는 디바이스와 연결됨. | 동일한 개인 Apple ID를 사용하는 디바이스 최대 5개까지 1개 라이선스 사용 가능. 라이선스는 사용자와 연결됨. <br> <br> Intune에서 개인 Apple ID 및 관리형 Apple ID와 연결된 최종 사용자는 2개의 앱 라이선스를 사용함.|
| **라이선스 마이그레이션** | 앱은 사용자에서 디바이스 라이선스로 자동으로 마이그레이션할 수 있습니다. | 앱은 디바이스에서 사용자 라이선스로 마이그레이션할 수 없습니다. |

> [!NOTE]  
> 사용자 등록 디바이스에는 사용자에게 사용이 허가된 앱만 설치가 가능하므로 회사 포털에서는 사용자 등록 디바이스에 디바이스 사용이 허가된 앱이 표시되지 않습니다.

## <a name="what-app-types-are-supported"></a>어떤 앱 유형이 지원되나요?
Apple Business Manager를 사용하여 퍼블릭 및 프라이빗 앱을 구매하고 배포할 수 있습니다.
- **스토어 앱:** 콘텐츠 관리자는 Apple Business Manager를 사용하여 앱 스토어에서 사용 가능한 무료 및 유료 앱을 모두 구매할 수 있습니다.
- **사용자 지정 앱:** 또한 콘텐츠 관리자는 Apple Business Manager를 사용하여 사용자의 조직에서만 사용 가능한 사용자 지정 앱을 구매할 수도 있습니다. 이러한 앱은 사용자와 직접 협업 중인 개발자가 조직의 특정 필요에 맞추어 조정했습니다. [사용자 지정 앱 배포 방법](https://developer.apple.com/business/custom-apps/)에 대해 자세히 알아보세요.

## <a name="prerequisites"></a>전제 조건
- 사용자 조직의 [Apple Business Manager](https://business.apple.com/) 또는 [Apple School Manager](https://school.apple.com/) 계정이어야 함. 
- 하나 이상의 위치 토큰으로 할당된 구매된 앱 라이선스. 
- 다운로드된 위치 토큰. 

> [!IMPORTANT]
> - 위치 토큰은 한 번에 하나의 디바이스 관리 솔루션으로만 사용할 수 있습니다. Intune에서 구매된 앱을 사용하기 전에 다른 MDM(모바일 디바이스 관리) 공급업체를 통해 사용된 기존의 위치 토큰을 해지 및 제거합니다. 
> - 위치 토큰은 한 번에 하나의 Intune 테넌트에 대해서만 지원됩니다. 여러 Intune 테넌트에 대해 동일한 위치 토큰을 다시 사용하지 마세요.
> - 기본적으로 Intune은 Apple과 위치 토큰을 하루에 두 번씩 동기화합니다. 물론 Intune에서는 수동 동기화를 언제든 시작할 수 있습니다.
> - 위치 토큰을 Intune으로 가져온 후에는 동일한 토큰을 다른 디바이스 관리 솔루션으로 가져오지 마세요. 가져오면 라이선스 할당과 사용자 레코드가 손실될 수 있습니다.

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>VPP(Volume Purchase Program)에서 앱과 책으로의 마이그레이션
사용자의 조직이 Apple Business Manager나 Apple School Manager를 아직 마이그레이션하지 않았다면 Intune에서 구매된 앱을 관리하기에 앞서 [앱과 책으로의 마이그레이션에 관한 Apple 지침](https://support.apple.com/HT208257)을 검토하시기 바랍니다.

> [!IMPORTANT]
> - 최상의 마이그레이션 환경을 위해 위치별로 하나의 VPP 구매자만 마이그레이션합니다. 각 구매자가 고유의 위치로 마이그레이션되면 모든 라이선스가(할당 및 비할당) 앱과 책으로 이동합니다.
> - Intune 내의 기존 레거시 VPP 토큰이나 해당 토큰과 관련된 앱 및 할당은 삭제하지 마세요. 이 작업을 수행하려면 모든 앱 할당이 Intune에서 다시 생성되어야 합니다.

Apple Business Manager나 Apple School Manager에서 구매된 기존 VPP 콘텐츠와 토큰을 앱과 책으로 다음과 같이 마이그레이션합니다.

1. VPP 구매자가 사용자의 조직에 가입하도록 초대하고 각 사용자가 고유의 위치를 선택하도록 합니다. 
2. 진행 전에 조직 내의 모든 VPP 구매자가 1단계를 완료했는지 확인합니다.
3. Apple Business Manager나 Apple School Manager에서 구매된 모든 앱과 라이선스가 앱과 책으로 마이그레이션되었는지 확인합니다.
4. **Apple Business(또는 School) Manager** > **설정** > **앱 및 책** > **내 서버 토큰** 순서로 이동해 새 위치 토큰을 다운로드합니다.
5. Microsoft 엔드포인트 관리자 관리 센터에서 **테넌트 관리** > **커넥터 및 토큰** > **Apple VPP 토큰** 순서로 이동해 토큰을 동기화해서 위치 토큰을 업데이트합니다.

## <a name="upload-an-apple-vpp-or-location-token"></a>Apple VPP 또는 위치 토큰 업로드

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
3. **테넌트 관리** > **커넥터 및 토큰** > **Apple VPP 토큰**을 선택합니다.
4. VPP 토큰 목록 창에서 **만들기**를 선택합니다.
5. **VPP 토큰 만들기** 창에서 다음 정보를 지정합니다.
    - **VPP 토큰 파일** - 아직 완료되지 않았다면 Apple Business Manager나 Apple School Manager에 로그인합니다. 등록한 후 계정에 대한 Apple VPP 토큰을 다운로드하여 선택합니다.
    - **Apple ID** - 업로드된 토큰과 연결된 계정의 관리형 Apple ID를 입력합니다.
    - **다른 MDM에서 토큰 제어** - 이 옵션을 **예**로 설정하면 다른 MDM 솔루션에서 Intune으로 토큰을 다시 할당할 수 있습니다.
    - **토큰 이름** - 토큰 이름을 설정하기 위한 관리 필드입니다.    
    - **국가/지역** - VPP 국가/지역 스토어를 선택합니다.  Intune은 지정된 VPP 국가/지역 스토어의 모든 로캘에 대해 VPP 앱을 동기화합니다.
        > [!WARNING]  
        > 국가/지역을 변경하면 이 토큰으로 만든 앱에 대한 Apple 서비스를 통한 다음 동기화에서 앱 메타데이터와 앱 스토어 URL이 업데이트됩니다. 앱이 새 국가/지역 스토어에 없으면 해당 앱은 업데이트되지 않습니다.

    - **VPP 계정 유형** - **비즈니스** 또는 **교육**을 선택합니다.
    - **자동 앱 업데이트** - **켜기** 또는 **끄기**를 선택하여 자동 업데이트를 사용하도록 설정합니다. 사용하도록 설정되면 Intune에서 앱 스토어 내의 VPP 앱 업데이트를 검색하고, 디바이스가 체크 인하면 업데이트를 디바이스에 푸시합니다. 
        
        > [!NOTE] 
        > Apple VPP 앱에 대한 자동 앱 업데이트는 **필수** 설치 목적으로 배포된 앱만 자동으로 업데이트합니다. **사용 가능** 설치 목적으로 배포된 앱의 경우 자동 업데이트는 새 버전의 앱을 사용할 수 있다는 상태 메시지를 IT 관리자를 위해 자동으로 생성합니다. 앱을 선택하고, 디바이스 설치 상태를 선택하고, 상태 정보를 확인하여 이 상태 메시지를 볼 수 있습니다.  

    - **Microsoft에서 Apple에 사용자 및 디바이스 정보를 보낼 수 있도록 권한을 부여합니다.** - 계속하려면 **동의함**을 선택해야 합니다. Microsoft에서 Apple로 전송하는 데이터를 검토하려면 [Intune이 Apple에 보내는 데이터](~/protect/data-intune-sends-to-apple.md)를 참조하세요.

6. 작업이 완료되면 **만들기**를 선택합니다. 토큰은 토큰 목록 창에 표시됩니다.

## <a name="synchronize-a-vpp-token"></a>VPP 토큰 동기화
선택된 토큰에 대해 **동기화**를 선택하면 구매한 앱의 이름, 메타데이터, 라이선스 정보를 Intune에서 동기화할 수 있습니다.

## <a name="assign-a-volume-purchased-app"></a>대량 구매 앱 할당

1. **앱** > **모든 앱**을 선택합니다.
2. 앱 목록 창에서 할당할 앱을 선택한 다음, **할당**을 선택합니다.
3. **앱 이름** - **할당**에서 **그룹 선택**을 선택한 다음, **그룹 추가** 창에서 **할당 형식**을 선택하고, 앱을 할당하려는 Azure AD 사용자 또는 디바이스 그룹을 선택합니다.
5. 선택한 각 그룹에 대해 다음 설정을 선택합니다.
    - **형식** - 앱이 **사용 가능**(최종 사용자가 회사 포털에서 앱 설치 가능)인지 또는 **필수**(최종 사용자 디바이스에서 자동으로 앱 설치)인지를 선택합니다.
    - **라이선스 형식** - **사용자 라이선싱** 또는 **디바이스 라이선싱**을 선택합니다.
6. 작업이 끝나면 **저장**을 선택합니다.


>[!NOTE]
>사용 가능한 배포 의도는 디바이스 그룹에 대해서는 지원되지 않고 사용자 그룹에 대해서만 지원됩니다. 표시되는 앱 목록은 토큰과 관련이 있습니다. 여러 개의 VPP 토큰과 연결된 앱이 있을 경우 동일한 앱이 각 토큰마다 한 번씩, 여러 번 표시됩니다.

> [!NOTE]  
> Intune(또는 해당 문제에 대한 다른 MDM)은 실제로 VPP 앱을 설치하지 않습니다. 대신 Intune은 VPP 계정에 연결하여 어떤 디바이스에 어떤 앱 라이선스를 할당할지 Apple에 알려줍니다. 이제부터 실제 설치는 모두 Apple과 디바이스 사이에서 처리됩니다.
> 
> [Apple MDM 프로토콜 참조, 135페이지](https://developer.apple.com/business/documentation/MDM-Protocol-Reference.pdf)

## <a name="end-user-prompts-for-vpp"></a>VPP에 대한 최종 사용자 프롬프트

최종 사용자는 다양한 시나리오에서 VPP 앱을 설치하도록 요구하는 메시지를 받게 됩니다. 다음 표에서는 각 조건에 대해 설명합니다.

| # | 시나리오                                | Apple VPP 프로그램에 초대                              | 앱 설치 프롬프트 | Apple ID에 대한 프롬프트 |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – 사용이 허가된 사용자(사용자 등록 디바이스가 아님)                             | 지원                                                                                               | 지원                                           | 지원                                 |
| 2 | 회사 – 사용이 허가된 사용자(감독되지 않은 디바이스)     | 지원                                                                                               | 지원                                           | 지원                                 |
| 3 | 회사 – 사용이 허가된 사용자(감독된 디바이스)         | 지원                                                                                               | N                                           | 지원                                 |
| 4 | BYOD – 사용이 허가된 디바이스                           | N                                                                                               | 지원                                           | N                                 |
| 5 | 회사 – 사용이 허가된 디바이스(감독되지 않은 디바이스)                           | N                                                                                               | 지원                                           | N                                 |
| 6 | 회사 – 사용이 허가된 디바이스(감독된 디바이스)                           | N                                                                                               | N                                           | N                                 |
| 7 | 키오스크 모드(감독된 디바이스) – 사용이 허가된 디바이스 | N                                                                                               | N                                           | N                                 |
| 8 | 키오스크 모드(감독된 디바이스) – 사용이 허가된 사용자   | --- | ---                                          | ---                                |

> [!Note]  
> 사용자 라이선스를 사용하여 VPP 앱을 키오스크 모드 디바이스에 할당하는 것은 권장되지 않습니다.

## <a name="revoking-app-licenses"></a>앱 라이선스 철회

지정된 디바이스, 사용자 또는 앱에 따라 모든 연결된 iOS 또는 macOS VPP(volume-purchase program) 앱 라이선스를 철회할 수 있습니다.  그러나 iOS 및 macOS 플랫폼 간에는 몇 가지 차이점이 있습니다. 

|   | iOS | macOS |
|-----|------------------|----------------|
| **앱 할당 제거** | 사용자에게 할당된 앱을 제거하는 경우 Intune은 사용자 또는 디바이스 라이선스를 회수하고 디바이스에서 앱을 제거합니다. | 사용자에게 할당된 앱을 제거하는 경우 Intune은 사용자 또는 디바이스 라이선스를 회수합니다. 앱은 디바이스에서 제거되지 않습니다. |
| **앱 라이선스 해지** | 앱 라이선스를 해지하면 사용자 또는 디바이스에서 앱 라이선스가 회수됩니다. 디바이스에서 앱을 제거하려면 할당을 **제거**로 변경해야 합니다. | 앱 라이선스를 해지하면 사용자 또는 디바이스에서 앱 라이선스가 회수됩니다. 라이선스가 철회된 macOS 앱은 장치에서 계속 사용할 수 있지만, 사용자 또는 디바이스에 라이선스가 다시 할당될 때까지는 업데이트할 수 없습니다. Apple에 따라 이러한 앱은 30일 유예 기간이 지난 후 제거됩니다. 그러나 Apple은 제거 할당 작업을 사용하여 Intune에서 앱을 제거하는 수단을 제공하지 않습니다.

>[!NOTE]
> - 직원이 퇴직하면서 더 이상 AAD 그룹에 속하지 않을 때 Intune은 앱 라이선스를 회수합니다.
> - 구매된 앱을 **제거**할 의향으로 할당하면 Intune은 라이선스 회수와 앱 제거를 모두 진행합니다.
> - Intune 관리에서 디바이스가 제거될 경우 앱 라이선스는 회수되지 않습니다. 

## <a name="deleting-vpp-tokens"></a>VPP 토큰 삭제
<!-- 820879 -->  
콘솔을 사용하여 Apple VPP(Volume-Purchase Program) 토큰을 삭제할 수 있습니다. VPP 토큰의 중복 인스턴스가 있는 경우 이 기능이 필요할 수 있습니다. 토큰을 삭제하면 연결된 모든 앱과 할당도 삭제하게 됩니다. 그러나 토큰을 삭제하면 앱 라이선스를 해지하거나 앱을 제거하지 않습니다. 

>[!NOTE]
>Intune은 토큰이 삭제된 후에 앱 라이선스를 취소할 수 없습니다. 

<!-- 820870 -->  
지정된 VPP 토큰에 대해 모든 VPP 앱 라이선스를 해지하려면 먼저 토큰과 연결된 모든 앱 라이선스를 해지한 다음, 해당 토큰을 삭제해야 합니다.

## <a name="renewing-app-licenses"></a>앱 라이선스 갱신

Apple Business Manager나 Apple School Manager에서 새로운 토큰을 다운로드하고 Intune에서 기존 토큰을 업데이트하여 Apple VPP 토큰을 갱신할 수 있습니다.

## <a name="deleting-a-vpp-app"></a>VPP 앱 삭제

현재 iOS VPP 앱은 Microsoft Intune에서 삭제할 수 없습니다.

## <a name="assigning-custom-role-permissions-for-vpp"></a>VPP에 대한 사용자 지정 역할 권한 할당

Intune에서 사용자 지정 관리자 역할에 할당된 사용 권한을 사용하여 Apple VPP 토큰 및 VPP 앱에 대한 액세스를 독립적으로 제어할 수 있습니다.

* Intune 사용자 지정 역할로 **앱** > **Apple VPP 토큰**에서 Apple VPP 토큰을 관리하도록 허용하려면 **관리되는 앱**에 대한 권한을 할당합니다.
* Intune 사용자 지정 역할로 **앱** > **모든 앱**에서 iOS VPP 토큰을 사용하여 구입한 앱을 관리하도록 허용하려면 **모바일 앱**에 대한 권한을 할당합니다. 

## <a name="additional-information"></a>추가 정보

Apple에서는 VPP 토큰을 만들고 갱신하기 위한 직접적인 지원을 제공합니다. 자세한 내용은 Apple 설명서의 일부인 [VPP(볼륨 구매 프로그램)를 이용하여 사용자에게 콘텐츠 배포하기](https://go.microsoft.com/fwlink/?linkid=2014661)를 참조하세요. 

Intune 포털에 **외부 MDM에 할당됨**이 표시되는 경우 관리자는 Intune에서 VPP 토큰을 사용하기 전에 타사 MDM에서 VPP 토큰을 제거해야 합니다.

## <a name="frequently-asked-questions"></a>자주 묻는 질문

### <a name="how-many-tokens-can-i-upload"></a>토큰은 몇 개나 업로드할 수 있나요?
Intune에서는 토큰을 3,000개까지 업로드할 수 있습니다.

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>앱이 설치되거나 디바이스에서 제거되면 포털이 라이선스 개수를 업데이트하는 데 얼마나 걸리나요?
라이선스는 앱을 설치하거나 제거한 후에 몇 시간 이내에 업데이트되어야 합니다. 최종 사용자가 디바이스에서 앱을 제거하는 경우 라이선스는 여전히 해당 사용자 또는 디바이스에 할당되어 있습니다.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>앱을 초과 구독할 수 있나요, 그렇다면 어떤 상황에서 가능한가요?
예. Intune 관리자는 앱을 초과 구독할 수 있습니다. 예를 들어 관리자가 XYZ 앱에 대한 100개의 라이선스를 구입한 다음, 500명의 멤버를 포함한 그룹에 앱을 대상으로 지정하는 경우 처음 100명의 멤버(사용자 또는 디바이스)는 라이선스를 할당받습니다. 그리고 나머지 멤버는 라이선스 할당에 실패합니다.


## <a name="next-steps"></a>다음 단계

앱 할당을 모니터링하는 데 유용한 정보는 [앱을 모니터링하는 방법](apps-monitor.md)을 참조하세요.

앱 관련 문제 해결에 대한 내용은 [앱 문제 해결 방법](~/apps/troubleshoot-app-install.md)을 참조하세요.
