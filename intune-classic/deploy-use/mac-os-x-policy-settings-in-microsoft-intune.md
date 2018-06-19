---
title: Mac OS X 정책 설정
description: Intune은 Mac OS X 장치에서 구성할 수 있는 기본 제공 일반 설정의 범위를 제공합니다. 또한 Intune에서 사용할 수 없는 사용자 지정 설정을 만들려면 Apple Configurator 도구를 사용할 수 있습니다.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: afc5e32cd2db5755ad6fb570aabae27c4d23e827
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31026298"
---
# <a name="mac-os-x-configuration-policy-settings-in-microsoft-intune"></a>Microsoft Intune의 Mac OS X 구성 정책 설정

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune은 Mac OS X 장치에서 구성할 수 있는 기본 제공 일반 설정의 범위를 제공합니다. 또한 Intune에서 사용할 수 없는 사용자 지정 설정을 만들려면 Apple Configurator 도구를 사용할 수 있습니다.

## <a name="general-configuration-policy-settings"></a>일반 구성 정책 설정

Microsoft Intune **Mac OS X 일반 구성 정책**을 사용하여 다음 설정을 구성할 수 있습니다.

-   **장치 보안 설정**. 장치에서 다양한 기능을 제어할 수 있는 미리 정의된 설정 목록에서 선택합니다.

-   **호환 및 비호환 앱**. 회사의 호환 또는 비호환 앱 목록을 지정할 수 있습니다. 호환되지 않는 앱 보고서를 사용하면 사용자가 설치한 앱과 목록에 지정한 앱 호환을 비교해서 확인할 수 있습니다. 그렇지만 실제로 앱의 설치를 차단할 수는 없습니다.

원하는 설정이 이 목록에 표시되지 않으면 직접 만들 수 있습니다. Apple Configurator 도구를 사용하여 만든 설정을 가져올 수 있도록 하는 Mac OS X 사용자 지정 정책을 사용하면 됩니다. 자세한 내용은 나중에 이 항목에서 “사용자 지정 정책 설정”을 참조하세요.

### <a name="password-settings"></a>암호 설정

|설정 이름|세부 정보|
|----------------|---------------|
|**장치의 잠금을 해제하는 데 암호 필요**|사용자가 암호를 사용하여 Mac 컴퓨터에 액세스해야 하는지 여부를 지정합니다. **중요:** Mac OS X 장치에서는 iOS 장치와 달리 이 설정을 준수하도록 암호를 업데이트하라는 알림이 사용자에게 즉시 표시되지 않습니다.|
|**필수 암호 유형**|암호를 **숫자만**으로 구성할 수 있는지 아니면 **영숫자**(문자와 숫자 포함)로 구성해야 하는지 지정합니다. **중요:** 이 설정은 Mac OS X 버전 10.10.3 이상에서만 지원됩니다.|
|**암호에 필요한 복합 문자 수**|암호에 필요한 복합 문자 수를 **0**-**4**자 사이로 지정합니다.<br /><br />복합 문자는 **?** 등의 기호입니다.|
|**최소 암호 길이**|최소 암호 길이를 **4**자에서 **14**자 사이로 지정합니다.|
|**단순 암호 허용**|**0000** 또는**1234**와 같은 단순 암호 사용을 허용합니다.|
|**암호를 요구하기 전까지 비활성 시간(분)**|컴퓨터 잠금을 해제하려면 암호를 입력해야 할 때까지 컴퓨터가 비활성 상태로 유지되는 시간을 지정합니다.|
|**암호 만료(일)**|사용자가 암호를 변경해야 할 때까지의 기간을 **1**-**255**일 사이로 지정합니다.|
|**암호 기록 기억**|사용자가 이전에 사용했던 암호를 사용하지 못하게 합니다. 이 설정을 지정하는 경우에는 **이전 암호 다시 사용 안 함**도 설정하여 이전에 사용했으며 다시 사용할 수 없는 암호의 수를 **1**-**24**개 사이로 지정할 수 있습니다.|
|**화면 보호기가 활성화되기까지의 비활성 시간(분)**|화면 보호기가 활성화되기까지 컴퓨터가 유휴 상태로 유지되는 시간을 지정합니다.|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>규격 및 비규격 앱에 대한 설정
**Mac OS X에 대한 호환 &amp; 비호환 앱 목록**에서 **장치에 대한 관리되는 설정**을 설정하고 다음 정보를 사용하여 호환 또는 비호환 앱 목록을 지정합니다.

> [!NOTE]
> 단일 정책에는 규격 앱 목록이나 비규격 앱 목록만 포함될 수 있습니다. 동일한 정책에 둘 다 지정할 수는 없습니다.
>
> Intune에서는 비규격 앱이 설치된 장치를 보고할 수 있습니다. 그러나 비호환 앱이 제거되거나 설치가 차단되지는 않습니다.

|                                    설정 이름                                    |                                                                                                                                                                                                                                                                                                                                                     세부 정보                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      <strong>사용자가 나열된 앱을 설치할 때 비호환성 보고</strong>      |                                                                                                                                                                                                                                                                    사용자가 설치할 수 없는 Mac OS X 앱의 목록이 표시됩니다. 사용자가 이러한 앱을 설치하면  <strong>앱 보고서</strong>에 해당 내용이 보고됩니다.                                                                                                                                                                                                                                                                    |
| <strong>사용자가 나열되지 않은 앱을 설치할 때 비호환성 보고</strong> |                                                                                                                                                                                                                                                                       사용자가 설치할 수 있는 Mac OS X 앱의 목록이 표시됩니다. 사용자가 다른 앱을 설치하면  <strong>앱 보고서</strong>에 해당 내용이 보고됩니다.                                                                                                                                                                                                                                                                        |
|                                <strong>추가</strong>                                | 앱을 선택한 목록에 추가합니다. 원하는 이름, 앱 게시자(선택 사항) 및 앱의 번들 ID를 지정합니다. <strong>팁:</strong> 앱의 번들 ID를 찾으려면 앱이 설치된 Mac 컴퓨터에서 아래 단계를 수행합니다.<ol><li>앱이 설치되어 있는 폴더(예: <strong>/Applications</strong>)를 엽니다.</li><li><em>&lt;앱 이름&gt;</em><strong>.app</strong> 번들을 선택하고 <strong>패키지 내용 표시</strong>를 선택합니다.</li><li><strong>Info.plist</strong> 파일을 엽니다.</li><li><strong>CFBundleIdentifier</strong> 키와 연결된 값을 확인합니다.</li></ol>번들 ID의 형식은 <strong>com.contoso.appname</strong>입니다. |
|                            <strong>앱 가져오기</strong>                            |                                                                                                                                                                                                                                                                                지정한 앱 목록을 쉼표로 구분된 값 파일로 가져옵니다. 파일에서 앱 이름, 게시자, 앱 번들 ID 형식을 사용합니다.                                                                                                                                                                                                                                                                                 |
|                               <strong>편집</strong>                                |                                                                                                                                                                                                                                                                                                                         선택한 앱의 이름, 게시자 및 앱 번들 ID를 편집합니다.                                                                                                                                                                                                                                                                                                                         |
|                              <strong>삭제</strong>                               |                                                                                                                                                                                                                                                                                                                                      목록에서 선택한 앱을 삭제합니다.                                                                                                                                                                                                                                                                                                                                      |

> [!TIP]
> Intune 보고서에 대한 자세한 내용은 [보고서를 사용하는 Microsoft Intune 작업 이해](understand-microsoft-intune-operations-by-using-reports.md) 항목을 참조하세요.

> [!IMPORTANT]
> Mac OS X 장치가 절전 모드이면 정책과 프로필을 전달하거나 인벤토리에 추가할 수 없습니다. 따라서 다음번에 장치를 절전 모드에서 해제할 때까지 Intune 콘솔에 **오류가 있는 정책 설정** 상태가 일시적으로 표시될 수도 있습니다.

### <a name="monitor-compliant-and-noncompliant-apps"></a>규격 및 비규격 앱 모니터링
 **앱 보고서**를 사용하여 지정한 앱의 규정 준수 여부를 확인할 수 있습니다.

#### <a name="to-run-a-report"></a>보고서를 실행하려면

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **보고서** &gt; **호환되지 않는 앱 보고서**를 선택합니다.

2.  확인할 장치 그룹을 선택하고 호환 앱이나 비호환 앱을 확인할지 또는 둘 다 확인할지를 선택한 다음 **보고서 보기**를 선택합니다.

## <a name="mac-os-x-custom-policy-settings-in-microsoft-intune"></a>Microsoft Intune의 Mac OS X 사용자 지정 정책 설정
Microsoft Intune **Mac OS X 사용자 지정 구성 정책**을 사용하면 [Apple Configurator 도구](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)에서 만든 설정을 Mac OS X 장치에 배포할 수 있습니다. 이 도구를 사용하면 이러한 장치의 작업을 제어하는 많은 설정을 만들어 구성 프로필에 내보낼 수 있습니다. 그런 다음 이 구성 프로필을 Intune Mac OS X 사용자 지정 정책으로 가져와서 조직의 사용자 및 정책에 배포할 수 있습니다.

이 기능을 통해 Intune Mac OS X 일반 구성 정책으로는 구성할 수 없는 Mac OS X 설정을 배포할 수 있습니다.

### <a name="prerequisites"></a>필수 구성 요소
시작하기 전에 Apple Configurator를 설치하고 사용자 또는 장치를 배포할 설정이 포함된 구성 파일을 만들어야 합니다. [Mac 앱 스토어](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)에서 Apple Configurator를 다운로드하고 이에 대해 알아볼 수 있습니다.

> [!NOTE]
> Intune은 Mac OS X 사용자 지정 정책에 있는 개별 설정의 규정 준수를 보고하지 않습니다. 그러나 정책의 전반적인 규정 준수는 보고 됩니다.

### <a name="general-settings"></a>일반 설정

|설정 이름|세부 정보|
    |----------------|--------------------|
    |**Name**|Intune 콘솔에서 쉽게 식별할 수 있도록 Mac OS X 사용자 지정 정책에 대한 고유한 이름을 입력합니다.|
    |**설명**|Mac OS X 사용자 지정 정책의 개요에 대한 설명과 해당 정책을 찾을 때 유용한 기타 관련 정보를 제공합니다.|


### <a name="custom-settings"></a>사용자 지정 설정

|설정 이름|세부 정보|
    |----------------|--------------------|
    |**사용자 지정 구성 프로필 이름(사용자에게 표시됨)**|장치 및 Intune 정책 보고서에 표시될 정책 이름을 제공합니다.|
    |**구성 프로필 파일**|**가져오기**를 선택한 다음 Apple Configurator를 사용하여 만든 구성 프로필을 찾아 봅니다. **팁:** 구성 프로필 만들기에 대한 도움말은 이 항목의 “구성 프로필 파일을 만드는 방법”을 참조하세요.|
    |**구성 프로필 세부 정보**|가져온 구성 프로필에 대한 XML 코드를 표시합니다.|



### <a name="how-to-create-a-configuration-profile-file"></a>구성 프로필 파일을 만드는 방법
두 가지 방법으로 사용자 지정 정책에서 사용되는 구성 프로필 파일을 만들 수 있습니다.

-   Apple Configurator 도구에서 확장명이 **.mobileconfig**인 파일을 내보냅니다.

-   [Apple 구성 프로필 키 참조](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html)에서 적합한 스키마를 사용하여 파일을 직접 작성합니다.


### <a name="see-also"></a>참고 항목
[Microsoft Intune 정책을 사용하여 장치의 설정 및 기능 관리](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
