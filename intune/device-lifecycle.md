---
title: Microsoft Intune MDM 수명 주기 개요
description: Intune에서 등록부터 구성 및 최종 사용 중지에 이르는 수명 주기 동안 디바이스를 관리하는 데 어떤 도움을 주는지 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22398d24ed7b488fa24b414fbdf24483cf81cf2b
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57234890"
---
# <a name="overview-of-the-microsoft-intune-mobile-device-management-mdm-lifecycle"></a>Microsoft Intune 모바일 디바이스 관리(MDM) 수명 주기 개요

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

관리하는 모든 디바이스에는 *수명 주기*가 있습니다. Intune은 등록, 구성 및 보호부터 더 이상 필요하지 않아 디바이스 사용을 중지할 때까지의 수명 주기를 관리하는 데 도움을 줄 수 있습니다.

![디바이스 수명 주기](./media/device-lifecycle.png "Intune 디바이스 수명 주기")

## <a name="enroll"></a>등록
오늘날의 MDM(모바일 디바이스 관리) 전략은 다양한 휴대폰, 태블릿 및 PC(iOS, Android, Windows 및 Mac OS X)에 적용됩니다. 회사 소유 디바이스에 대한 일반적인 경우처럼 디바이스를 관리할 수 있어야 하는 경우, 첫 단계는 [디바이스 등록을 설정](device-enrollment.md)하는 것입니다. Windows PC를 Intune(MDM)에 등록하거나 [Intune 클라이언트 소프트웨어를 설치](manage-windows-pcs-with-microsoft-intune.md)하여 관리할 수도 있습니다.

## <a name="configure"></a>구성
디바이스 등록은 첫 단계에 불과합니다. Intune이 제공하는 모든 기능을 이용하고 디바이스가 안전하고 회사 표준을 준수하게 하도록 다양한 정책 중에서 선택할 수 있습니다. 따라서 관리 디바이스가 작동하는 방식의 거의 모든 측면을 구성할 수 있습니다. 예를 들어 사용자는 회사 데이터가 있는 디바이스에 대한 암호를 가지고 있어야 하나요? 암호를 사용하도록 요청할 수 있습니다. 회사 Wi-Fi가 있나요? 이러한 사항을 자동으로 구성할 수 있습니다. 다음은 사용할 수 있는 구성 옵션의 유형입니다.

- [**디바이스 구성**](device-profiles.md). 이러한 정책을 통해 관리하는 디바이스의 특징 및 기능을 구성할 수 있습니다. 예를 들어 Windows 휴대폰에 대해 암호 사용을 요구하거나 iPhone에서 카메라 사용을 비활성화할 수 있습니다.
- [**회사 리소스 액세스**](device-profiles.md). 사용자가 개인 디바이스에서 작업에 액세스할 수 있도록 하는 경우 관리자가 다루어야 할 문제가 발생할 수 있습니다. 예를 들어 회사 전자 메일에 액세스해야 하는 모든 디바이스를 올바르게 구성하는 방법은 무엇입니까? 사용자가 복잡한 설정을 알 필요 없이 VPN 연결을 사용하여 회사 네트워크에 액세스할 수 있도록 하는 방법은 무엇인가요? Intune은 관리하는 디바이스를 일반적인 회사 리소스에 액세스하도록 자동으로 구성하여 이러한 부담을 덜어줄 수 있습니다.
- [**Windows PC 관리 정책(Intune 클라이언트 소프트웨어 사용)**](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md). Intune에 Windows PC를 등록하면 최상의 디바이스 관리 기능을 제공하며, 한편 Intune은 Intune 클라이언트 소프트웨어를 사용하여 Windows PC 관리를 계속 지원합니다. PC를 사용하여 수행할 수 있는 일부 작업에 대한 정보가 필요한 경우 여기서 시작하세요.

## <a name="protect"></a>보호
최신 IT 세계에서 디바이스를 무단 액세스로부터 보호하는 것은 수행하는 매우 중요한 작업 중 하나입니다. 디바이스 수명 주기의 **구성** 단계에 있는 항목 외에 Intune은 관리하는 디바이스를 무단 액세스 또는 악의적인 공격으로부터 보호하도록 도와 주는 이러한 기능을 제공합니다.
- [**다단계 인증**](multi-factor-authentication.md). 사용자 로그인에 추가적인 인증 계층을 추가하면 디바이스를 훨씬 더 안전하게 만드는 데 도움이 될 수 있습니다. 대부분의 디바이스는 사용자가 전화 통화 또는 문자 메시지와 같은 두 번째 인증 단계를 거쳐야만 액세스 권한을 획득할 수 있는 다단계 인증을 지원합니다.
- [**비즈니스용 Windows Hello 설정**](windows-hello.md). 비즈니스용 Windows Hello는 사용자가 암호 필요 없이 지문 또는 Windows Hello 등과 같은 *제스처*를 사용여 로그인할 수 있도록 하는 대체 로그인 방법입니다.
- [**Windows PC를 보호하기 위한 정책(Intune 클라이언트 소프트웨어 사용)**](policies-to-protect-windows-pcs-in-microsoft-intune.md). Intune 클라이언트 소프트웨어를 사용하여 Windows PC를 관리하는 경우 관리하는 PC에서 Endpoint Protection, 소프트웨어 업데이트 및 Windows 방화벽에 대한 설정을 제어할 수 있는 정책을 사용할 수 있습니다.

## <a name="retire"></a>사용 중지
디바이스를 분실하거나 도난당한 경우, 디바이스를 교체해야 할 경우 또는 사용자가 다른 위치로 이동한 경우 일반적으로 디바이스를 [사용 중지 또는 초기화](device-management.md)해야 합니다. 디바이스 초기화, 관리에서 디바이스 제거 또는 디바이스의 회사 데이터 초기화 등 이 작업을 수행할 수 있는 다양한 방법이 있습니다.

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune에서 디바이스 관리](device-management.md)에 대해 알아봅니다.
