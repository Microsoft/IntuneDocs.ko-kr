---
title: 디바이스에서 사용자가 볼 수 있는 회사 포털 메시지
titleSuffix: Microsoft Intune
description: 최종 사용자가 회사 포털에서 볼 수 있는 다양한 메시지를 이해합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/09/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 700bded8930385c5576a198dc0364c64066121e5
ms.sourcegitcommit: 71314481e644025c005019b478b4cbeaf2390ea9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59569131"
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>최종 사용자가 회사 포털 앱 메시지를 이해할 수 있도록 지원

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

> [!NOTE]
> 다음 정보는 Android 6.0 이상 디바이스에만 적용됩니다.

최종 사용자가 회사 포털에서 볼 수 있는 다양한 앱을 이해합니다. 이러한 앱 메시지는 일반적으로 등록 프로세스의 여러 지점에 표시됩니다. 메시지가 표시되는 위치, 메시지의 의미, 사용자가 액세스를 거부하는 경우 발생되는 작업에 대해 알아봅니다. 또한 사용자에게 메시지를 가장 잘 설명하는 방법에 대해서도 알아봅니다.

- __회사 포털에서 통화를 하고 전화 통화를 관리하도록 허용하시나요?__
- __회사 포털에서 디바이스의 사진, 미디어 및 파일에 액세스하도록 허용하시겠습니까?__

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>회사 포털에서 통화를 하고 전화 통화를 관리하도록 허용하시겠습니까?

### <a name="where-it-appears"></a>표시되는 곳
**회사 포털에서 통화를 하고 전화 통화를 관리하도록 허용하시겠습니까?** 라는 메시지는 사용자가 디바이스를 등록하는 동안 회사 포털 앱에서 **등록**을 탭하면 표시됩니다.

### <a name="what-it-means"></a>의미
이 메시지를 수락하면 디바이스의 전화 및 IMEI 번호를 Intune 서비스에 보낼 수 있습니다. 이러한 번호는 관리 콘솔의 __하드웨어__ 페이지에 표시됩니다.

> [!NOTE]
> **회사 포털 앱에서 통화를 하거나 전화 통화를 관리하지 못합니다!** 메시지 텍스트는 Google에서 제어하므로 변경할 수 없습니다.

**하드웨어 페이지**를 표시하려면 **그룹** > **모든 모바일 디바이스** > **디바이스**로 이동해야 합니다. 사용자의 디바이스를 선택하고 **속성 보기** > **하드웨어**로 이동합니다.

### <a name="what-happens-if-users-deny-access"></a>사용자가 액세스를 거부하는 경우 발생되는 작업
사용자가 액세스를 거부하는 경우 계속해서 회사 포털 앱을 사용하고 디바이스를 등록할 수 있습니다. 그러나 디바이스 전화 번호와 IMEI 번호가 관리 콘솔의 __하드웨어__ 페이지에 비어 있게 됩니다. 사용자가 액세스 거부 후 두 번째로 회사 포털 앱에 로그인할 때 메시지 표시를 중지할 수 있는 **다시 묻지 않음** 확인란이 메시지에 표시됩니다.

사용자가 액세스를 허용하지만 나중에 거부하는 경우 등록 후 다음에 사용자가 회사 포털 앱에 로그인할 때 메시지가 표시됩니다.

사용자가 나중에 액세스를 허용하려는 경우 **설정** > **앱** > **회사 포털** > **사용 권한** > **전화**로 이동하면 됩니다.

### <a name="how-to-explain-this-to-your-users"></a>사용자에게 이를 설명하는 방법
사용자에게 [Intune에서 Android 디바이스 등록](/intune-user-help/enroll-your-device-in-intune-android) 항목에서 자세한 내용을 참조하라고 합니다.

## <a name="allow-company-portal-to-access-your-contacts"></a>회사 포털에 연락처에 대한 액세스를 허용하시겠습니까?

### <a name="where-it-appears"></a>표시되는 곳
**회사 포털에서 연락처에 액세스하도록 허용하시겠습니까?** 라는 메시지는 사용자가 디바이스를 등록하는 동안 회사 포털 앱에서 **등록**을 탭하면 표시됩니다.

### <a name="what-it-means"></a>의미
Intune이 회사 계정을 만들어 해당 디바이스에 등록된 사용자의 Azure Active Directory ID를 관리하도록 허용하려면 이 메시지에 동의합니다.

> [!NOTE]
> **Microsoft는 사용자의 연락처에 액세스하지 않습니다.** 메시지 텍스트는 Google에서 제어하므로 변경할 수 없습니다.

### <a name="what-happens-if-users-deny-access"></a>사용자가 액세스를 거부하는 경우 발생되는 작업
사용자가 액세스를 거부하면 디바이스가 Intune에 등록되지 않고 관리되지도 않습니다. 사용자가 액세스 거부 후 두 번째로 회사 포털 앱에 로그인할 때 메시지 표시를 중지할 수 있는 **다시 묻지 않음** 확인란이 메시지에 표시됩니다.

사용자가 액세스를 허용하지만 나중에 거부하는 경우 등록 후 다음에 사용자가 회사 포털 앱에 로그인할 때 메시지가 표시됩니다.

사용자가 나중에 액세스를 허용하려는 경우 **설정** > **앱** > **회사 포털** > **사용 권한** > **전화**로 이동하면 됩니다.

### <a name="how-to-explain-this-to-your-users"></a>사용자에게 이를 설명하는 방법
사용자에게 [Intune에서 Android 디바이스 등록](/intune-user-help/enroll-your-device-in-intune-android) 항목에서 자세한 내용을 참조하라고 합니다.

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>회사 포털에서 디바이스의 사진, 미디어 및 파일에 액세스하도록 허용하시겠습니까?

### <a name="where-it-appears"></a>표시되는 곳
**회사 포털에서 디바이스의 사진, 미디어 및 파일에 액세스하도록 허용하시겠습니까?** 메시지는 사용자가 IT 관리자에게 로그를 보내기 위해 **데이터 전송**을 탭하면 표시됩니다.

### <a name="what-it-means"></a>의미
이 메시지에 동의함으로써 사용자는 해당 디바이스에서 데이터 로그를 디바이스의 SD 카드에 기록하게 합니다. 또한 USB 케이블을 사용하여 이러한 로그를 이동하게 할 수 있습니다.   

> [!NOTE]
> **회사 포털 앱에서 사용자의 사진, 미디어 및 파일에 액세스하지 못합니다.** 메시지 텍스트는 Google에서 제어하므로 변경할 수 없습니다.

### <a name="what-happens-if-users-deny-access"></a>사용자가 액세스를 거부하는 경우 발생되는 작업
사용자가 액세스를 거부하는 경우 메일을 통해 계속 로그 데이터를 보낼 수 있지만 로그가 디바이스의 SD 카드에 복사되지는 않습니다.

사용자가 액세스 거부 후 두 번째로 회사 포털 앱에 로그인할 때 메시지가 다시 표시되지 않도록 선택할 수 있는 **다시 묻지 않음** 확인란이 메시지에 표시됩니다. 사용자가 액세스를 허용하지만 나중에 거부하는 경우 다음에 로그를 보내려고 시도할 때 메시지가 표시됩니다. 그러나 사용자가 나중에 액세스를 허용할 경우 **설정** > **앱** > **회사 포털** > **사용 권한** > **저장소**로 이동한 다음, 사용 권한을 설정할 수 있습니다.


### <a name="how-to-explain-this-to-your-users"></a>사용자에게 이를 설명하는 방법
사용자에게 [메일을 통해 IT 관리자에게 로그 보내기](/intune-user-help/send-logs-to-your-it-admin-by-email-android) 항목을 참조하라고 합니다. 

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>회사 지원은 회사 리소스에 대한 액세스 권한을 제공해야 합니다.

### <a name="where-it-appears"></a>표시되는 곳
회사 포털 앱을 **허용된 앱** 또는 **예외 앱** 목록에 추가하지 않은 경우 사용자가 로그인하려고 하면 로그인에 실패합니다. 다음과 같은 메시지가 표시됩니다.

> **회사 지원은 회사 리소스에 대한 액세스 권한을 제공해야 합니다.**  
> 회사는 디바이스를 보호하기 위해 Information Protection 정책을 사용합니다. 회사 지원은 회사 포털이 이런 리소스에 액세스하도록 허용하는지 확인해야 합니다.

### <a name="what-it-means"></a>의미

WIP(Windows Information Protection) 앱 보호 정책에서 **허용된 앱** 또는 **예외 앱** 목록에 회사 포털을 추가합니다. 자세한 내용은 [Intune을 사용하여 WIP(Windows Information Protection) 앱 보호 정책 만들기 및 배포](windows-information-protection-policy-create.md)를 참조하세요.

## <a name="approve-a-ios-company-app-line-of-business-app-on-your-ios-device"></a>iOS 디바이스에서 iOS 회사 앱(기간 업무 앱) 승인 

### <a name="where-it-appears"></a>표시되는 곳
조직에서 개발된 iOS 앱이 앱 스토어에서 사용할 수 없으면 해당 앱은 기본적으로 디바이스에서 신뢰할 수 없습니다. 회사 포털을 사용하여 해당 앱을 설치하고 앱을 시작하면 다음 메시지가 표시됩니다.

![iOS 앱 메시지 - 신뢰할 수 없는 엔터프라이즈 개발자](./media/end-user-company-portal-messages/end-user-company-portal-messages-01.png)

### <a name="what-it-means"></a>의미
이 메시지는 iOS 디바이스에서 회사가 개발한 앱을 승인 및 설치하려면 iOS 디바이스 설정을 수정해야 함을 의미합니다.

회사 포털을 사용하여 해당 앱을 설치하고 앱을 시작하는 경우에는 다음 단계에 따라 앱을 다운로드한 후 앱을 승인합니다.

1. 설치된 회사 앱(기간 업무 앱)을 시작하면 “신뢰할 수 없는 엔터프라이즈 개발자” 메시지가 표시됩니다. <br>
   **취소**를 누릅니다.
2. **설정** > **일반** > **디바이스 관리**로 이동합니다.

   ![iOS 디바이스 UI - 디바이스 관리](./media/end-user-company-portal-messages/end-user-company-portal-messages-02.png)

3. **관리 프로필** > **엔터프라이즈 앱**을 선택합니다.
4. 개발자 이름을 선택합니다.
5. **_개발자 이름_ 신뢰**를 누릅니다.
6. 앱 설치 팝업 메시지에서 **신뢰**를 선택하여 앱을 확인합니다.

   ![iOS 디바이스 UI - 앱 신뢰 메시지](./media/end-user-company-portal-messages/end-user-company-portal-messages-03.png)

    회사 앱을 시작하고 사용할 수 있어야 합니다.


### <a name="see-also"></a>참고 항목
[Intune 사용 방법에 대해 최종 사용자에게 알릴 내용](end-user-educate.md)
