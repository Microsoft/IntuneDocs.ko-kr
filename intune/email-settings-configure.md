---
title: Microsoft Intune에서 이메일 설정 구성 - Azure | Microsoft Docs
titleSuffix: ''
description: Microsoft Intune에서 이메일 프로필을 만들고 Android Enterprise, iOS 및 Windows 디바이스에 이 프로필을 배포합니다. 이메일 프로필을 사용하여 관리 대상 디바이스에서 회사 이메일에 연결하는 데 사용할 인증 방법과 이메일 서버를 비롯한 일반적인 이메일 설정을 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e0c59ba8744272dd1038ede854ae49879c66f39
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513242"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Intune을 사용하여 디바이스에 이메일 설정 추가

Microsoft Intune에는 조직의 디바이스에 배포할 수 있는 여러 이메일 설정이 포함됩니다. IT 관리자는 Office 365 및 Gmail 등 이메일 서버에 연결하기 위해 특정 설정으로 이메일 프로필을 만듭니다. 그런 다음, 최종 사용자는 모바일 디바이스에서 조직의 이메일 계정을 연결, 인증 및 동기화합니다. 이메일 프로필을 만들고 배포하여 여러 디바이스에서 설정이 표준인지 확인할 수 있습니다. 그리고 올바른 이메일 설정을 모르는 최종 사용자의 지원 요청을 줄이는 데 도움이 됩니다.

이메일 프로필을 사용하여 다음 디바이스에 기본 제공되는 이메일 설정을 구성할 수 있습니다.

- Android Samsung Knox Standard 4.0 이상
- Android Enterprise
- iOS 8.0 이상
- Windows Phone 8.1 이상
- Windows 10(데스크톱) 및 Windows 10 Mobile

이 문서에서는 Microsoft Intune에서 이메일 프로필을 만드는 방법을 보여 줍니다. 또한 구체적인 설정을 보여주기 위해 다양한 플랫폼에 대한 링크를 포함합니다.

## <a name="create-a-device-profile"></a>디바이스 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고, **Intune**을 기준으로 필터링한 다음, **Microsoft Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 이메일 프로필의 **이름**과 **설명**을 입력합니다.
4. 드롭다운 목록에서 **플랫폼**을 선택합니다. 옵션은 다음과 같습니다.

    - **Android**(Samsung Android Knox Standard만 해당)
    - **Android 엔터프라이즈**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 이상**

5. **프로필** 유형 드롭다운 목록에서 선택 **메일**을 선택합니다.
6. 구성 가능한 설정은 플랫폼별로 다를 수 있습니다. 구체적인 설정을 보려면 플랫폼을 선택하세요.

    - [Android Samsung Knox Standard 설정](email-settings-android.md)
    - [Android Enterprise 설정](email-settings-android-enterprise.md)
    - [iOS 설정](email-settings-ios.md)
    - [Windows Phone 8.1 설정](email-settings-windows-phone-8-1.md)
    - [Windows 10 설정](email-settings-windows-10.md)

설정을 입력하고 프로필을 만들면 프로필 목록에 프로필이 표시됩니다. 그런 다음, [이 프로필을 그룹에 할당](device-profile-assign.md)합니다.

## <a name="remove-an-email-profile"></a>메일 프로필 제거

이메일 프로필은 사용자 그룹이 아닌 디바이스 그룹에 할당됩니다. 디바이스에 이메일 프로필이 하나뿐인 경우에도 디바이스에서 이메일 프로필을 제거하는 여러 가지 방법이 있습니다.

- **옵션 1**: 이메일 프로필을 열고(**디바이스 구성** > **프로필**) **할당**을 선택합니다. **포함** 탭은 프로필에 할당된 그룹을 보여줍니다. 그룹을 마우스 오른쪽 단추로 클릭하고 **제거**를 선택합니다. 변경 내용을 **저장**합니다.

- **옵션 2**: [디바이스를 초기화 또는 사용 중지합니다](devices-wipe.md). 이러한 작업을 통해 데이터 및 설정을 선택적으로 또는 완전히 제거할 수 있습니다.

## <a name="secure-email-access"></a>이메일 액세스 보호

다음 옵션을 사용하여 이메일 프로필을 보호할 수 있습니다.

- **인증서**: 이메일 프로필을 만들 때 이전에 Intune에서 만든 인증서 프로필을 선택합니다. 이 인증서를 ID 인증서라고 합니다. 이는 사용자 디바이스의 연결이 허용되었음을 확인하기 위해 신뢰할 수 있는 인증서 프로필 또는 루트 인증서에 대해 인증하는 데 사용됩니다. 신뢰할 수 있는 인증서는 메일 연결을 인증하는 컴퓨터에 할당됩니다. 일반적으로 이 컴퓨터는 네이티브 메일 서버입니다.

  Intune에서 인증서 프로필을 만들고 사용하는 방법에 대한 자세한 내용은 [Intune을 사용하여 인증서를 구성하는 방법](certificates-configure.md)을 참조하세요.

- **사용자 이름 및 암호**: 최종 사용자는 사용자 이름과 암호를 입력하여 네이티브 메일 서버에 인증합니다. 암호는 이메일 프로필에 존재하지 않습니다. 따라서 최종 사용자는 이메일에 연결할 때 암호를 입력합니다.

## <a name="how-intune-handles-existing-email-accounts"></a>Intune에서 기존 메일 계정을 처리하는 방법

사용자가 이메일 계정을 이미 구성한 경우 플랫폼에 따라 이메일 프로필이 다르게 할당됩니다.

- **iOS**: 호스트 이름 및 전자 메일 주소를 기반으로 기존에 중복된 전자 메일 프로필이 검색됩니다. 중복된 이메일 프로필은 Intune 프로필 할당을 차단합니다. 이 경우 회사 포털 앱에서 최종 사용자에게 규정을 준수하지 않음을 알리고 수동으로 구성한 프로필을 제거하라는 메시지를 표시합니다. 이 시나리오를 방지하려면 이메일 프로필을 설치하기 *전에* 최종 사용자에게 등록하여 Intune의 프로필 설정을 허용하라고 안내합니다.

- **Windows:** 호스트 이름 및 전자 메일 주소를 기반으로 기존에 중복된 전자 메일 프로필이 검색됩니다. Intune은 최종 사용자가 만든 기존 이메일 프로필을 덮어씁니다.

- **Android Samsung Knox Standard**: 전자 메일 주소를 기반으로 기존에 중복된 전자 메일 프로필이 검색되고 Intune 프로필로 덮어씁니다. Android는 호스트 이름을 사용하여 프로필을 식별하지 않습니다. 서로 다른 호스트에서 동일한 이메일 주소를 사용하여 여러 이메일 프로필을 만들지 마세요. 프로필이 서로를 덮어씁니다.

- **Android 회사 프로필**: Intune은 Android 회사 이메일 프로필 두 개(Gmail 및 Nine Work 앱용으로 하나씩)를 제공합니다. 이러한 앱은 Google Play 스토어에서 제공되며 디바이스 회사 프로필에 설치됩니다. 이러한 앱은 중복 프로필을 만들지 않습니다. 두 앱 모두 Exchange에 대한 연결을 지원합니다. 이메일 연결을 사용하려면 사용자의 디바이스에 이러한 이메일 앱 중 하나를 배포합니다. 그런 다음, 적절한 이메일 프로필을 만들고 배포합니다. Nine Work 등의 이메일 앱은 무료가 아닐 수 있습니다. 앱의 라이선스 정보를 검토하거나, 질문이 있으면 앱 회사에 문의하세요.

## <a name="changes-to-assigned-email-profiles"></a>할당된 이메일 프로필에 대한 변경 내용

이전에 할당한 이메일 프로필을 변경할 경우 최종 사용자가 자신의 이메일 설정 재구성 승인을 요청하는 메시지가 표시될 수 있습니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성되면 아직 아무 작업도 수행하지 않습니다. 다음으로, [일부 디바이스에 프로필을 할당](device-profile-assign.md)합니다.
