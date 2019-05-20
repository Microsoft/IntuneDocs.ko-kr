---
title: 관리되는 Android 디바이스용 앱 구성 정책 추가
titleSuffix: Microsoft Intune
description: Microsoft Intune에서 앱 구성 정책을 사용하여 사용자가 Android 회사 프로필 앱을 실행할 때 설정을 제공할 수 있습니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dccbfe597fa4bd461bb71cb86d38ffdfd52d719a
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567428"
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>관리되는 Android 디바이스용 앱 구성 정책 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune에서 앱 구성 정책을 사용하여 Android 회사 프로필 앱에 설정을 제공할 수 있습니다. 앱에 대한 구성 설정을 지정하려면 앱 개발자는 Android 관리되는 앱 구성 설정을 공개해야 합니다. 설정을 적용하려는 사용자 그룹에 앱 구성 정책을 할당합니다.  정책 설정은 앱에서 해당 설정을 확인할 때(일반적으로는 앱을 처음 실행할 때) 사용됩니다.

> [!Note]  
> 모든 앱이 앱 구성을 지원하지는 않습니다. 앱 구성 정책을 지원하도록 앱을 빌드했는지 앱 개발자와 확인하세요.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **클라이언트 앱** 워크로드를 선택합니다.
4. **관리** 그룹에서 **앱 구성 정책**을 선택한 다음 **추가**를 선택합니다.
5. 다음 세부 정보를 설정합니다.
    - **이름** - Azure Portal에 표시되는 프로필의 이름입니다.
    - **설명** - Azure Portal에 표시되는 프로필의 설명입니다.
    - **디바이스 등록 형식** - **관리 디바이스**를 선택합니다.
6. **플랫폼**으로 **Android**를 선택합니다.
7. **연결된 앱**을 선택하여 앱 구성 정책을 정의하려는 앱을 선택합니다. Intune과 동기화하고 승인한 앱을 Android 회사 프로필 앱 목록에서 선택합니다.
8. **사용 권한**을 선택합니다. 다음을 사용하여 구성을 설정할 수 있습니다.
    - [구성 디자이너](#use-the-configuration-designer)
    - [JSON 편집기](#enter-the-json-editor)
9. **확인**을 선택한 다음 **추가**를 선택합니다.

## <a name="use-the-configuration-designer"></a>구성 디자이너 사용

앱이 구성 설정을 지원하도록 디자인된 경우 Android 앱에 구성 디자이너를 사용할 수 있습니다. 구성은 Intune에 등록된 디바이스에 적용됩니다. 디자이너를 사용하면 앱이 공개하는 설정에 대한 특정 구성 값을 구성할 수 있습니다.

**추가**를 선택하여 앱에 대해 지정하려는 구성 설정 목록을 선택합니다.  
구성의 각 키 및 값의 경우 다음을 설정합니다.

  - **값 형식**  
    구성 값의 데이터 형식입니다. 문자열 값 형식의 경우 값 형식으로 변수 또는 인증서 프로필을 필요에 따라 선택할 수 있습니다.
  - **구성 값**  
    구성의 값입니다. 값 형식에 대해 변수 또는 인증서를 선택하는 경우 구성 값 드롭다운 목록의 변수 또는 인증서 프로필 목록에서 선택할 수 있습니다.  인증서를 선택하면 디바이스에 배포되는 인증서 별칭이 런타임 시 채워집니다.
    
### <a name="supported-variables-for-configuration-values"></a>구성 값에 대해 지원되는 변수

값 형식으로 변수를 선택하는 경우 다음 옵션을 선택할 수 있습니다.

| 옵션 | 예제 |
|----|----|
| Mail | john@contoso.com |
| 사용자 계정 이름 | john@contoso.com |
| 부분 UPN | john |
| 도메인 | contoso.com |
| 사용자 이름 | John Doe |
| 계정 ID | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| 사용자 ID | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| 장치 ID | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>다중 ID 앱에서 구성된 조직 계정만 허용 

Android 디바이스의 경우 다음 키/값 쌍을 사용합니다.

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **값** | <ul><li>하나 이상의 <code>;</code>으로 구분된 UPN입니다.</li><li>허용된 계정만 이 키로 정의된 관리되는 사용자 계정입니다.</li><li> Intune 등록 디바이스의 경우 <code>{{userprincipalname}}</code> 토큰을 사용하여 등록된 사용자 계정을 나타낼 수 있습니다.</li></ul> |

   > [!NOTE]
   > 다중 ID를 사용하는 구성된 조직 계정만 허용하는 경우 Android용 Outlook 2.2.222 이상을 사용해야 합니다.<p></p>
   > Microsoft Intune 관리자는 관리되는 장치에서 Microsoft Office 애플리케이션에 추가할 사용자 계정을 제어할 수 있습니다. 허용되는 조직 사용자 계정만 액세스하도록 제한하고 등록된 디바이스에서 개인 계정을 차단할 수 있습니다. 지원 애플리케이션이 앱 구성을 처리하고 승인되지 않은 계정을 제거 및 차단합니다.<p></p>
   > Microsoft Word, Microsoft Excel, Microsoft PowerPoint의 경우 앱 버전 16.0.9327.1000 이상을 사용해야 합니다. 

## <a name="enter-the-json-editor"></a>JSON 편집기 입력

앱의 일부 구성 설정(예: 번들 유형 관련 설정)은 구성 디자이너를 사용하여 구성할 수 없습니다. 이러한 값에는 JSON 편집기를 사용해야 합니다. 설정은 앱을 설치하면 앱에 자동으로 제공됩니다.

1. **구성 설정 형식**으로 **JSON 편집기 입력**을 선택합니다.
2. 편집기에서 구성 설정에 대한 JSON 값을 정의할 수 있습니다. **JSON 템플릿 다운로드**를 선택하여 샘플 파일을 다운로드한 다음 구성할 수 있습니다.
3. **확인**을 선택한 다음 **추가**를 선택합니다.

정책이 만들어지고 정책 목록 블레이드에 나타납니다.

할당된 앱은 디바이스에서 실행될 때 앱 구성 정책에서 구성한 설정을 사용하여 실행됩니다.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>앱에 대한 사용 권한 부여 상태 미리 구성

Android 디바이스 기능에 액세스하기 위한 앱의 권한을 미리 구성할 수도 있습니다. 기본적으로 위치 또는 디바이스 카메라에 대한 액세스와 같이 디바이스 권한이 필요한 Android 앱에서는 권한을 허용할 것인지 거부할 것인지 묻는 메시지를 사용자에게 표시합니다. 예를 들어, 앱에서 디바이스의 마이크를 사용하는 경우 앱에 마이크 사용 권한을 부여할 것인지 묻는 메시지가 사용자에게 표시됩니다.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **클라이언트 앱**을 선택합니다.
3. **관리**에서 **앱 구성 정책**을 선택하고 **추가**를 선택합니다.
4. 다음 세부 정보를 설정합니다.
    - **이름**. Azure Portal에 표시되는 프로필의 이름입니다.
    - **설명**. Azure Portal에 표시되는 프로필의 설명입니다.
    - **디바이스 등록 유형**. **관리되는 디바이스**를 선택합니다.
    - **플랫폼**. **Android**를 선택합니다.
5. **연결된 앱**을 선택하여 구성 정책을 정의할 앱을 선택합니다. Intune과 동기화하고 승인한 앱을 Android 회사 프로필 앱 목록에서 선택합니다.
6. **권한**과 **추가**를 차례로 선택합니다.
7. 사용 가능한 앱 권한 목록에서 원하는 권한을 선택하고 **확인**을 선택합니다.
8. 이 정책을 통해 부여하려는 각 권한에 대한 옵션을 선택합니다.
    - **프롬프트**. 사용자에게 허용할 것인지 거부할 것인지 묻는 메시지 표시
    - **자동 허용**. 사용자에게 알리지 않고 자동으로 승인합니다.
    - **자동 거부**. 사용자에게 알리지 않고 자동으로 거부합니다.
9. 앱 구성 정책을 할당하려면 앱 구성 정책을 선택하고 **할당**을 선택한 후에 **그룹 선택**을 선택합니다.
10. 할당할 사용자 그룹을 선택하고 **선택**을 선택합니다.
11. **저장**을 선택하여 정책을 할당합니다.

## <a name="next-steps"></a>다음 단계

앱을 계속 [할당](apps-deploy.md) 및 [모니터링](apps-monitor.md)합니다.

