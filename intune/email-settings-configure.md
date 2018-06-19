---
title: Microsoft Intune 이메일 설정 구성하는 방법
titleSuffix: ''
description: 관리하는 장치에서 회사 이메일에 대한 연결을 만들도록 Microsoft Intune을 구성하는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b71c004a165bd6d38cd1907eadc05ac20f27bd1a
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31834213"
---
# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>Microsoft Intune에서 메일 설정을 구성하는 방법

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

메일 프로필을 사용하여 연결하는 데 필요한 설정으로 관리하는 장치를 구성하고 회사 메일과 동기화할 수 있습니다. 이를 통해 모든 장치에서 설정을 표준화하고 올바른 메일 설정을 모르는 최종 사용자의 지원 요청을 줄일 수 있습니다.

기본 제공 메일 클라이언트는 대부분의 플랫폼에 지원됩니다. 대부분의 타사 메일 앱은 현재 지원되지 않습니다.

전자 메일 프로필을 사용하여 다음 장치 유형에서 네이티브 전자 메일 클라이언트를 구성할 수 있습니다.

- Android Samsung Knox Standard 4.0 이상
- Android for Work
- iOS 8.0 이상
- Windows Phone 8.1 이상
- Windows 10(데스크톱) 및 Windows 10 Mobile

이 아티클의 정보를 사용하여 메일 프로필 구성에 대한 기본 사항을 알아본 다음, 각 플랫폼에 대한 추가 항목을 통해 장치에 특정한 정보를 확인할 수 있습니다.

## <a name="create-a-device-profile-containing-email-settings"></a>메일 설정을 포함하는 장치 프로필 만들기

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **장치 구성**을 선택합니다.
2. **관리** 섹션 아래의 **장치 구성** 창에서 **프로필**을 선택합니다.
3. 프로필 창에서 **프로필 만들기**를 선택합니다.
4. **프로필 만들기** 창에서 이메일 프로필에 대한 **이름** 및 **설명**을 입력합니다.
5. **플랫폼** 드롭다운 목록에서 메일 설정을 적용할 장치 플랫폼을 선택합니다. 현재 메일 장치 설정에 대해 다음 플랫폼 중 하나를 선택할 수 있습니다.
    - **Android**(Samsung Android Knox Standard만 해당)
    - **Android for Work**
    - **Android**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 이상**
    - **Windows 10 이상**
6. **프로필** 유형 드롭다운 목록에서 선택 **메일**을 선택합니다.
7. 선택한 플랫폼에 따라 구성할 수 있는 설정이 다릅니다. 각 플랫폼에 대한 자세한 설정을 보려면 다음 항목 중 하나로 이동하세요.
    - [Android for Work 및 Samsung Knox Standard 설정](email-settings-android.md)
    - [iOS 설정](email-settings-ios.md)
    - [Windows Phone 8.1 설정](email-settings-windows-phone-8-1.md)
    - [Windows 10 설정](email-settings-windows-10.md)
8. 작업이 완료되면 **프로필 만들기** 창으로 돌아가서 **만들기**를 누릅니다.

프로필이 만들어지고 프로필 목록 창에 표시됩니다.
계속해서 이 프로필을 그룹에 할당하려면 [장치 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.

## <a name="further-information"></a>추가 정보

### <a name="remove-an-email-profile"></a>메일 프로필 제거

장치에서 메일 프로필을 제거하려면 할당을 편집하고 장치가 멤버로 포함된 그룹을 모두 제거합니다. 이메일 프로필이 장치에 있는 유일한 메일 프로필인 경우 이 방식으로 이메일 프로필을 제거할 수 없습니다.

### <a name="securing-email-access"></a>메일 액세스 보안

다음 두 가지 방법 중 하나를 사용하여 메일 프로필을 보호할 수 있습니다.

1. **인증서** - 메일 프로필을 만들 때 이전에 Intune에서 만든 인증서 프로필을 선택합니다. 이를 ID 인증서라고 부르며, 사용자 장치의 연결 허용을 설정하기 위해 신뢰할 수 있는 인증서 프로필(또는 루트 인증서)에 대해 인증하는 데 사용됩니다. 신뢰할 수 있는 인증서는 메일 연결을 인증하는 컴퓨터(대개 네이티브 메일 서버)에 할당됩니다.
Intune에서 인증서 프로필을 만들고 사용하는 방법에 대한 자세한 내용은 [Intune을 사용하여 인증서를 구성하는 방법](certificates-configure.md)을 참조하세요.
2. **사용자 이름 및 암호** - 사용자는 사용자 이름과 암호를 제공하여 네이티브 메일 서버에 인증합니다.
전자 메일 프로필에는 암호가 포함되어 있지 않아 사용자가 전자 메일에 연결할 때 암호를 입력해야 합니다.


### <a name="how-intune-handles-existing-email-accounts"></a>Intune에서 기존 메일 계정을 처리하는 방법

사용자가 메일 계정을 이미 구성한 경우 Intune 메일 프로필 할당의 결과는 장치 플랫폼에 따라 달라집니다.

- **iOS**: 호스트 이름 및 메일 주소를 기반으로 기존에 중복된 메일 프로필이 검색됩니다. 중복된 이메일 프로필은 Intune 프로필 할당을 차단합니다. 이 경우 회사 포털에서 사용자에게 규정을 준수하지 않음을 알리고 수동으로 구성한 프로필을 제거하라는 메시지를 표시합니다. 이 문제를 방지하려면 메일 프로필을 설치하기 전에 등록하여 Intune의 프로필 설정을 허용하라고 안내합니다.
- **Windows**: 호스트 이름 및 메일 주소를 기반으로 기존에 중복된 메일 프로필이 검색됩니다. Intune은 사용자가 만든 기존 전자 메일 프로필을 덮어씁니다.
- **Android Samsung Knox Standard**: 메일 주소를 기준으로 중복된 기존 메일 프로필을 검색한 다음 Intune 프로필로 덮어씁니다.
Android에서는 프로필 식별에 호스트 이름을 사용하지 않으므로 여러 호스트에서 동일한 메일 주소에 사용할 메일 프로필을 여러 개 만들지 않는 것이 좋습니다. 이렇게 하면 각각 덮어쓰게 됩니다.
- **Android for Work**: Intune은 Android for Work 전자 메일 프로필 2개(Gmail 및 Nine Work 전자 메일 앱용으로 하나씩)를 제공합니다. 이러한 앱은 Google Play 스토어에서 제공되며 장치 작업 프로필에 설치되므로 프로필이 중복될 수 없습니다. 두 앱 모두 Exchange에 대한 연결을 지원합니다. 메일 연결을 사용하도록 설정하려면 사용자의 장치에 이러한 메일 앱 중 하나를 배포한 후 적절한 메일 프로필을 만들어 배포합니다. Nine Work 등의 메일 앱은 무료가 아닐 수도 있습니다. 앱의 라이선스 정보를 검토하거나, 질문이 있으면 앱 회사에 문의하세요.

### <a name="update-an-email-profile"></a>전자 메일 프로필 업데이트

이전에 할당한 전자 메일 프로필을 변경할 경우 최종 사용자가 자신의 전자 메일 설정 재구성 승인을 요청하는 메시지가 표시될 수 있습니다.
