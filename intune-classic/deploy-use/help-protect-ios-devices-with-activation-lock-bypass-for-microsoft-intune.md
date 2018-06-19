---
title: 장치에서 iOS 활성화 잠금 관리
description: Microsoft Intune에서는 iOS 7.1 이상 장치용 나의 iPhone 찾기(Find My iPhone) 앱의 기능인 iOS 활성화 잠금을 관리할 수 있습니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 04/24/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 37593e8c554cad73182873b01f6388bdb9cb0035
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020132"
---
# <a name="help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune"></a>Microsoft Intune의 활성화 잠금 무시를 사용하여 iOS 장치 보호

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune에서는 iOS 8.0 이상 장치용 나의 iPhone 찾기(Find My iPhone) 앱의 기능인 iOS 활성화 잠금을 관리할 수 있습니다. 활성화 잠금은 사용자가 장치에서 나의 iPhone 찾기 앱을 열 때 자동으로 설정됩니다. 활성화 잠금이 설정되면 사용자의 Apple ID와 암호를 입력해야 다음 작업을 수행할 수 있습니다. 

-   나의 iPhone 찾기 끄기

-   장치의 콘텐츠 지우기

-   장치 다시 활성화

## <a name="how-activation-lock-affects-you"></a>활성화 잠금 사용 시의 영향
활성화 잠금 기능을 사용하면 iOS 장치를 보호하고, 손실되었거나 도난당한 장치의 복구 가능성을 높일 수는 있지만 IT 관리자의 경우에는 여러 가지 문제를 해결해야 할 수도 있습니다. 예를 들면 다음과 같습니다.

-   사용자가 장치에서 활성화 잠금을 설정합니다. 해당 사용자가 퇴사하게 되어 장치를 반납합니다. 이 경우 해당 사용자의 Apple ID와 암호가 없으면 장치를 다시 활성화할 수 없습니다.

-   활성화 잠금을 설정한 모든 장치의 보고서를 작성해야 합니다.

-   조직에서 장치 새로고침을 진행하는 동안 일부 장치를 다른 부서에 다시 할당해야 하는 경우가 있습니다. 이때 활성화 잠금이 설정되지 않은 장치만 다시 할당할 수 있습니다.

이러한 문제를 해결할 수 있도록 Apple은 iOS 7.1에 활성화 잠금 무시 기능을 도입했습니다. 이 기능을 통해 사용자의 Apple ID와 암호가 없어도 감독된 장치에서 활성화 잠금을 제거할 수 있습니다. 감독된 장치는 장치별 활성화 잠금 무시 코드를 생성할 수 있으며, 이 코드는 Apple 활성화 서버에 저장됩니다.

> [!TIP]
> iOS 장치에 대해 감독 모드를 사용하면 Apple Configurator를 통해 장치를 잠그고 특정 업무용으로 기능을 제한할 수 있습니다. 감독 모드는 대개 회사가 소유한 장치에서만 사용됩니다.

활성화 잠금에 대한 자세한 내용은 [여기](https://support.apple.com/en-us/HT201365)에서 확인할 수 있습니다.

## <a name="how-intune-helps-you-manage-activation-lock"></a>Intune을 통해 활성화 잠금을 관리하는 방법
Intune에서는 iOS 8.0 이상을 실행하는 감독된 장치의 활성화 잠금 상태를 요청할 수 있습니다. 감독된 장치의 경우에만 Intune은 활성화 잠금 무시 코드를 검색하여 장치에 직접 제공할 수 있습니다. 장치를 초기화한 경우에는 사용자 이름은 비워 두고 코드를 암호로 사용하는 방식으로 장치에 직접 액세스할 수 있습니다.

**이러한 방식의 업무상 이점은 다음과 같습니다**.

-   사용자가 나의 iPhone 찾기 앱의 보안 이점을 활용할 수 있습니다.

-   사용자가 안심하고 장치에서 작업할 수 있게 하며, 장치의 용도를 다시 설정해야 하는 경우 장치를 사용 중지하거나 잠금 해제할 수 있습니다.

## <a name="before-you-start"></a>시작하기 전에

장치에서 활성화 잠금을 바이패스하려면 먼저 활성화 잠금을 사용하도록 설정해야 합니다. 이렇게 하려면 다음을 수행합니다.

1. [Microsoft Intune 정책을 사용하여 장치의 설정 및 기능 관리](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)의 내용을 참조하세요.
2. 설정 페이지의 **등록** 섹션에서 **장치가 감독 모드에 있을 경우 활성화 잠금 허용** 설정을 **예**로 구성합니다.
3. 정책을 저장한 다음 활성화 잠금 바이패스를 관리하려는 장치에 배포합니다.

## <a name="how-to-use-activation-lock-bypass-from-the-intune-admin-console"></a>Intune 관리 콘솔에서 활성화 잠금 무시를 사용하는 방법
> [!IMPORTANT]
> 장치에서 활성화 잠금을 무시하도록 설정한 후 나의 iPhone 찾기 앱을 열면 새 활성화 잠금이 자동으로 적용됩니다. 따라서 **이 절차를 수행하려면 장치를 실제로 보유해야 합니다**.

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **그룹** &gt; **모든 장치** &gt; **회사가 소유한 모든 장치**를 선택합니다.

2.  활성화 잠금을 무시할 장치를 선택합니다. **활성화 잠금 무시**를 선택합니다.

3.  경고 메시지를 읽습니다. **예**를 선택하여 작업을 계속 진행합니다.

장치 세부 정보 페이지에서 잠금 해제 요청의 상태를 점검할 수 있습니다.

## <a name="how-to-see-which-devices-are-using-activation-lock"></a>활성화 잠금을 사용 중인 장치를 확인하는 방법
다음의 두 가지 방법으로 활성화 잠금을 사용 중인 장치를 확인할 수 있습니다.

-   **모바일 장치 인벤토리 보고서**를 실행합니다. 이 보고서에는 장치의 상태를 나타내는 **활성화 잠금 상태** 및 **감독됨** 열이 표시됩니다. **감독됨**의 값은 **예** 또는 **아니요**이고 **활성화 잠금 상태**의 값은 다음과 같습니다.

    -   바이패스 코드로 사용됨

    -   바이패스 코드 없이 사용됨(장치가 감독되지 않음)

    -   바이패스 코드 없이 사용됨(장치에 연결할 수 없음)

    -   사용 안 함

    iOS 8.0 이상을 실행하지 않는 장치의 경우 **활성화 잠금 상태** 상자가 비어 있습니다.

-   그룹 보기에서 장치를 선택하여 장치 세부 정보 창에서 활성화 잠금 상태를 확인합니다.

    **회사가 소유한 모든 장치** 노드에서 선택한 장치에 활성화 잠금이 설정되어 있는 경우에는 무시 코드도 확인할 수 있습니다. 이 코드를 사용하면 활성화 잠금 무시를 수동으로 실행할 수 있습니다.

    > [!IMPORTANT]
    >Intune은 7일 간격으로 장치의 인벤토리에 대해 활성화 잠금을 해제합니다. 이로 인해 Intune 콘솔에서 장치가 활성화 잠금 상태로 즉시 표시되지 않을 수 있습니다.


### <a name="see-also"></a>참고 항목
[장치 사용 중지](retire-devices-from-microsoft-intune-management.md)
[원격 잠금 또는 암호 재설정으로 장치 보호 지원](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)
