---
title: 대량 구매 iOS 전자책 관리
titlesuffix: Microsoft Intune
description: iOS 스토어에서 대량 구매한 책을 Intune에 동기화하고 해당 사용을 추적 및 관리하는 방법에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b43e7df72e709cfdd929085b1d6718f1afcdf9f
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347355"
---
# <a name="how-to-manage-ios-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Microsoft Intune을 사용하여 대량 구매 프로그램을 통해 구매한 iOS 전자책을 관리하는 방법


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Apple VPP(대량 구매 프로그램)를 사용하면 회사의 사용자에게 배포하려는 전자책용으로 라이선스를 여러 개 구매할 수 있습니다. 책을 비즈니스용 스토어나 교육용 스토어에서 배포할 수 있습니다.

Microsoft Intune을 사용하면 이 프로그램을 통해 구매한 책을 동기화, 관리 및 할당할 수 있습니다. 스토어에서 라이선스 정보를 가져와서 사용한 라이선스의 수를 추적할 수 있습니다.

책 관리 절차는 [VPP 앱 관리](vpp-apps-ios.md)와 비슷합니다.

## <a name="manage-volume-purchased-books-for-ios-devices"></a>iOS 장치용 대량 구매 책 관리
[Apple 비즈니스용 대량 구매 프로그램](http://www.apple.com/business/vpp/) 또는 [Apple 교육용 대량 구매 프로그램](http://volume.itunes.apple.com/us/store)을 통해 iOS 책용 라이선스를 여러 개 구매합니다. 이 프로세스에서는 Apple 웹 사이트에서 Apple VPP 계정을 설정하고 Apple VPP 토큰을 Intune에 업로드합니다.  그런 다음 대량 구매 정보를 Intune과 동기화하고 대량 구매 전자책 사용을 추적할 수 있습니다.

## <a name="before-you-start"></a>시작하기 전에
시작하기 전에 Apple에서 VPP 토큰 하나를 가져와 Intune 계정에 업로드하세요. 추가 필수 구성 요소:

* Intune 계정에는 VPP 토큰을 256개까지 연결할 수 있습니다.
* 이전에 VPP 토큰을 다른 제품에 사용한 경우 Intune에 사용할 토큰을 새로 생성해야 합니다.
* 각 토큰은 1년 동안 유효합니다.
* 기본적으로 Intune에서는 하루에 두 번 Apple VPP 서비스와 동기화합니다. 언제든지 수동 동기화를 시작할 수 있습니다.
* VPP 토큰을 Intune으로 가져온 후 같은 토큰을 다른 장치 관리 솔루션으로 가져오지 마세요. 가져오면 라이선스 할당과 사용자 레코드가 손실될 수 있습니다.
* Intune에서 iOS 책을 사용하기 전에 다른 MDM(모바일 장치 관리) 공급업체를 사용하여 만든 기존 VPP 사용자 계정을 제거합니다. Intune은 보안 조치로 해당 사용자 계정을 Intune에 동기화하지 않습니다. Intune은 Intune에서 만든 Apple VPP 서비스의 데이터만 동기화합니다.
* 장치에 책을 할당할 때 해당 장치에는 기본 제공 iBooks 앱이 설치되어 있어야 합니다. 이 앱이 설치되어 있지 않은 경우 최종 사용자는 앱을 다시 설치해야 전자책을 읽을 수 있습니다. 현재로는 Intune을 사용하여 제거된 기본 제공 앱을 복원할 수 없습니다.
* Apple 대량 구매 프로그램 사이트의 책만 할당할 수 있습니다. 내부에서 만든 책은 업로드한 다음 할당할 수 없습니다.
* 현재는 앱에 사용하는 것과 같은 방법으로 책을 최종 사용자 범주에 할당할 수 없습니다.
* 할당한 전자책은 회수할 수 없습니다.
* 적합한 장치를 가진 사용자가 VPP 전자책을 처음 설치하려는 경우 Apple 대량 구매 프로그램에 가입해야 전자책을 설치할 수 있습니다. 관리되는 Apple ID를 사용하여 보안 그룹에 라이선스를 할당할 수도 있습니다. 이렇게 하면 사용자가 전자책을 설치할 때 Apple ID를 입력하라는 메시지가 표시되지 않습니다.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Apple VPP 토큰을 가져와 업로드하려면

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
1.  **클라이언트 앱** 워크로드에서 **설정** > **iOS VPP 토큰**을 선택합니다.
2.  VPP 토큰 목록 창에서 **만들기**를 클릭합니다.
3.  **새 VPP 토큰** 창에서 다음 정보를 지정합니다.
    - **VPP 토큰 파일** - 비즈니스 또는 교육용 대량 구매 프로그램에 등록했는지 확인합니다. 그런 다음 계정용 Apple VPP 토큰을 다운로드하고 여기서 선택합니다.
    - **Apple ID** - 대량 구매 프로그램과 연결된 계정의 Apple ID를 입력합니다.
    - **VPP 계정 유형** - **비즈니스** 또는 **교육**을 선택합니다.
4. 완료되면 **만들기**를 클릭합니다.

토큰은 토큰 목록 창에 표시됩니다.


언제든지 **지금 동기화**를 선택하여 Apple에 보관된 데이터를 Intune과 동기화할 수 있습니다.

## <a name="to-assign-a-volume-purchased-app"></a>대량 구매 앱을 할당하려면

3. **Intune** 창에서 **전자책**을 선택합니다.
1. **전자책** 워크로드에서 **관리** > **모든 전자책**을 선택합니다.
2. 전자책 목록 창에서 할당할 전자책을 선택한 다음, ‘**...**’ > **그룹 할당**을 선택합니다.
3. <*전자책 이름*> - **할당된 그룹** 창에서 **관리** > **할당된 그룹**을 선택합니다.
4. **그룹 할당**을 선택하고 **그룹 선택** 창에서 전자책을 할당할 Azure AD 사용자 그룹을 선택합니다. 장치 그룹은 현재 지원되지 않습니다.
할당 작업 **사용 가능** 또는 **필수**를 선택합니다. 
5. 작업이 끝나면 **저장**을 선택합니다.

## <a name="next-steps"></a>다음 단계

전자책 할당을 모니터링하는 데 유용한 정보는 [앱을 모니터링하는 방법](apps-monitor.md)을 참조하세요.






