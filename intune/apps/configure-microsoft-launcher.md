---
title: Intune을 사용하여 Android Enterprise에 대한 Microsoft 시작 관리자 구성
titleSuffix: ''
description: Microsoft 시작 관리자에서 Intune 구성 정책을 사용합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 469f969b6429cc39b5a8b8d3c041b96fc773c9ec
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724960"
---
# <a name="configure-microsoft-launcher"></a>Microsoft 시작 관리자 구성

Microsoft 시작 관리자는 사용자가 휴대폰을 맞춤형으로 설정하고, 즉시 구성하고, 휴대폰 작업에서 PC로 전환할 수 있게 해 주는 Android 애플리케이션입니다. 

Android Enterprise 완전 관리형 디바이스에서 시작 관리자를 통해 엔터프라이즈 IT 관리자는 배경 무늬, 앱 및 아이콘 위치를 선택하여 관리되는 디바이스의 홈 화면을 사용자 지정할 수 있습니다. 이렇게 하면 여러 OEM 디바이스 및 시스템 버전에서 모든 관리되는 Android 디바이스의 모양과 느낌이 표준화됩니다. 

## <a name="how-to-configure-the-microsoft-managed-home-screen-app"></a>Microsoft Managed Home Screen 앱 구성 방법 

Azure Portal의 Intune 콘솔로 이동하여 **클라이언트 앱** > **앱 구성 정책**으로 이동합니다. **Android**를 실행하는 **관리 디바이스**에 대한 구성 정책을 추가하고 연결된 앱으로 **Microsoft 시작 관리자**를 선택합니다. **구성 설정**을 클릭하여 사용 가능한 여러 Managed Home Screen 설정을 구성할 수 있습니다. 

## <a name="choosing-a-configuration-settings-format"></a>구성 설정 형식 선택 

Managed Home Screen의 구성 설정을 정의할 때 선택할 수 있는 방법은 두 가지가 있습니다. 

- **구성 디자이너**를 사용하면 기능을 끄거나 켜게 토글하고 값을 설정할 수 있는 간편한 UI를 통해 설정을 구성할 수 있습니다. 이 방법에서는 값 형식이 BundleArray인 몇 가지 구성 키를 사용할 수 없습니다. 이러한 구성 키는 JSON 데이터 입력으로만 구성할 수 있습니다. 

- **JSON 데이터**를 사용하면 JSON 스크립트를 사용하여 가능한 모든 구성 키를 정의할 수 있습니다. 

**구성 디자이너**를 통해 속성을 추가하는 경우 아래에 표시된 것처럼 **구성 설정 형식** 드롭다운 목록에서 **JSON 입력 데이터**를 선택하여 이 속성을 자동으로 JSON으로 변환할 수 있습니다.

   ![구성 설정 형식 - 구성 디자이너 사용](./media/configure-microsoft-launcher/configure-microsoft-launcher-01.png)

## <a name="using-configuration-designer"></a>구성 디자이너 사용

구성 디자이너를 사용하면 미리 채워진 설정과 연결된 값을 선택할 수 있습니다.

   ![구성 설정 형식 - JSON 데이터 입력](./media/configure-microsoft-launcher/configure-microsoft-launcher-02.png)

다음 표는 Microsoft 시작 관리자의 사용 가능한 구성 키, 값 형식, 기본값 및 설명을 나열합니다. 설명은 선택한 값에서 예상되는 디바이스 작동을 제공합니다. 구성 디자이너에서 사용할 수 없는 구성 키는 이 표에 나열되지 않았습니다.

|    구성 키    |    값 형식    |    기본값    |    설명     |
|---------------------------------------------------|------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    등록 유형    |    문자열     |    Default    |    이 정책이 적용되는 등록 유형을 설정할 수 있습니다. 현재 값 **기본값**은 **CorporateOwnedBuisnessOnly**를 나타냅니다. 현재는 지원되는 다른 등록 유형이 없습니다.        JSON 키 이름: management_mode_key        |
|    Home Screen 앱 순서 사용자 변경 허용    |    부울    |    True    |    최종 사용자가 **Home Screen 앱 순서** 설정을 변경할 수 있는지 여부를 지정할 수 있습니다.<ul><li>**True**로 설정하면 정책에 정의된 앱 순서가 초기 배포에만 적용됩니다. 이후에는 사용자가 변경한 내용에는 해당 정책이 적용되지 않습니다.</li><li>**False**로 설정하면 앱 순서가 모든 동기화에 적용됩니다.</li></ul><br>**참고:** Home Screen 앱 순서는 JSON 편집기를 통해서만 구성할 수 있습니다.<br><br>JSON 키 이름:<br>`com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed`    |
|    그리드 크기 설정    |    문자열    |    자동    |    홈 화면에 배치할 앱의 그리드 크기를 설정할 수 있습니다. 앱 행과 열 수를 설정하여 `columns;rows` 형식으로 그리드 크기를 정의할 수 있습니다. 그리드 크기를 정의할 경우 홈 화면의 행에 표시되는 최대 앱 수는 설정한 행 수가 되고, 홈 화면의 열에 표시되는 최대 앱 수는 설정한 열 수가 됩니다.<br><br>        JSON 키 이름:<br>`com.microsoft.launcher.HomeScreen.GridSize`    |
|    디바이스 배경 무늬 설정    |    문자열    |    Null    |    배경 무늬로 설정하려는 이미지의 URL을 입력하여 원하는 배경 무늬를 설정할 수 있습니다.<br><br>JSON 키 이름:<br>`com.microsoft.launcher.Wallpaper.URL`    |
|    디바이스 배경 무늬 설정 사용자 변경 허용    |    Bool    |    True    |    최종 사용자가 디바이스 배경 무늬 설정을 디바이스 배경 무늬 설정을 변경할 수 있는지 여부를 지정할 수 있습니다.<ul><li>**True**로 설정하면 정책의 배경 무늬가 초기 배포에만 적용됩니다. 이후에는 사용자가 변경한 내용에는 해당 정책이 적용되지 않습니다.</li><li>**False**로 설정하면 배경 무늬가 모든 동기화에 적용됩니다.</li></ul><br>JSON 키 이름:<br>`com.microsoft.launcher.Wallpaper.URL.UserChangeAllowed`        |
|    피드 사용    |    부울    |    True    |    사용자가 홈 화면에서 오른쪽으로 살짝 밀 때 디바이스에서 시작 관리자 피드를 사용하도록 설정할 수 있습니다.<ul><li>**True**로 설정하면 피드가 사용됩니다.</li><li>**False**로 설정하면 피드가 사용되지 않습니다.</li></ul><br>JSON 키 이름:<br>`com.microsoft.launcher.Feed.Enabled`    |
|    피드 설정 사용자 변경 허용    |    부울    |    True    |     최종 사용자가 **피드 사용** 설정을 디바이스 배경 무늬 설정을 변경할 수 있는지 여부를 지정할 수 있습니다.<ul><li>**True**로 설정하면 피드가 초기 배포에만 적용됩니다. 이후에는 사용자가 변경한 내용에는 해당 정책이 적용되지 않습니다.</li><li>**False**로 설정하면 피드가 모든 동기화에 적용됩니다.</li></ul><br>JSON 키 이름:`com.microsoft.launcher.Feed.Enabled.UserChangeAllowed`    |

## <a name="enter-json-data"></a>JSON 데이터 입력

JSON 데이터를 입력하여 아래와 같이 Microsoft 시작 관리자에 사용 가능한 모든 설정과 **구성 디자이너**에서 사용하지 않게 지정된 설정을 구성합니다.

   ![구성 디자이너 - JSON 데이터](./media/configure-microsoft-launcher/configure-microsoft-launcher-03.png)

위의 구성 디자이너 표에 나열된 목록 외에도 다음 표는 JSON 데이터를 통해서만 구성할 수 있는 구성 키를 제공합니다.

|    구성 키    |    값 형식    |    기본값    |    설명     |
|----------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    허용 목록에 있는 애플리케이션 설정<br>JSON 키:`com.microsoft.launcher.HomeScreen.Applications`    |    BundleArray    | 참조: [허용 목록에 있는 애플리케이션 설정](configure-microsoft-launcher.md#set-allow-listed-applications)</sup>    |    디바이스에 설치된 앱 중에서 홈 화면에 표시할 앱 세트를 정의할 수 있습니다. 표시하려는 앱의 앱 패키지 이름을 입력해 정의할 수 있습니다. 예를 들어, `com.android.settings`는 홈 화면에서 설정에 액세스할 수 있게 지정합니다. 이 섹션에서 허용 목록에 넣은 앱은 기존에 디바이스에 설치되어 있어야 홈 화면에 표시될 수 있습니다.<p>속성:<ul><li>**패키지:** 애플리케이션 패키지 이름</li><li>**클래스:** : 특정 앱 페이지와 관련된 애플리케이션 작업입니다. 이 값이 비어 있는 경우 기본 앱 페이지를 사용합니다.</li></ul>      |
|    Home Screen 앱 순서<br>JSON 키:`com.microsoft.launcher.HomeScreen.AppOrder`    |    BundleArray    |    참조: [Home Screen 앱 순서](configure-microsoft-launcher.md#home-screen-app-order)      |    홈 화면에서 앱 순서를 지정할 수 있습니다.<p>속성:<br><ul><li>**유형:** 지원되는 유일한 형식은 `application`입니다.</li><li>**위치:** 홈 화면의 애플리케이션 아이콘 슬롯입니다. 왼쪽 위의 위치 1부터 시작해서 왼쪽에서 오른쪽, 위쪽에서 아래쪽으로 이동합니다.</li><li>**패키지:** 애플리케이션 패키지 이름입니다.</li><li>**클래스:** : 특정 앱 페이지와 관련된 애플리케이션 작업입니다. 이 값이 비어 있는 경우 기본 앱 페이지를 사용합니다.</li></ul>    |

### <a name="set-allow-listed-applications"></a>허용 목록에 있는 애플리케이션 설정

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.Applications",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

### <a name="home-screen-app-order"></a>Home Screen 앱 순서

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.AppOrder",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "type",
                    "valueString": "application"
                },
                {
                    "key": "position",
                    "valueInteger": 0
                },
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

다음은 모든 사용 가능한 구성 키를 포함한 JSON 스크립트 예제입니다.

```JSON
{
    "kind": "androidenterprise#managedConfiguration", 
    "productId": "app:com.microsoft.launcher", 
    "managedProperty": [
        {
            "key": "management_mode_key", 
            "valueString": "Default"
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable", 
            "valueBool": true
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url", 
            "valueBool": "http://www.contoso.com/wallpaper.png"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.GridSize", 
            "valueString": "5;5"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.Applications", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 17
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 18
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 19
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="next-steps"></a>다음 단계

- Android Enterprise 완전 관리형 디바이스에 대한 자세한 정보는 [Android Enterprise 완전 관리형 디바이스의 Intune 등록 설정](../enrollment/android-fully-managed-enroll.md)을 참조하세요.
