---
title: Microsoft Intune의 Windows Hello for Business 설정 - Azure | Microsoft Docs
description: Microsoft Intune의 Windows 10 디바이스에서 Windows Hello for Business를 사용하고 구성하려면 ID 보호 프로필의 모든 PIN, 생체 인식 및 스푸핑 방지 설정 목록을 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b5eb25c48e3724fdc9277a790d01908e976c75be
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54832653"
---
# <a name="windows-10-and-newer-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Intune에서 Windows Hello for Business를 지원하는 Windows 10(이상) 디바이스 설정

이 문서에서는 Intune의 Windows 10 디바이스에서 제어할 수 있는 Windows Hello for Business 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로 이러한 설정을 사용하여 PIN 또는 지문을 통해 로그인 등의 작업을 수행합니다.

Intune 관리자는 이러한 설정을 만들어 Windows 10 이상의 디바이스에 할당할 수 있습니다.

Intune의 Windows Hello for Business 프로필에 대한 자세한 내용은 [ID 보호 구성](identity-protection-configure.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[구성 프로필을 만듭니다](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>비즈니스용 Windows Hello

- **Windows Hello for Business 구성**: 이 기능을 사용하고 해당 설정을 구성하려면 **사용 가능**을 선택합니다.
- **최소 PIN 길이**: 디바이스에서 허용할 최소 PIN 길이를 입력합니다. 기본 PIN 길이는 6자입니다. 최소 PIN 길이는 4자입니다.
- **최대 PIN 길이**: 디바이스에서 허용할 최대 PIN 길이를 입력합니다. 기본 PIN 길이는 6자입니다. 최대 PIN 길이는 127자입니다.  
- **PIN에 소문자 사용**: 최종 사용자에게 소문자를 포함하도록 요구함으로써 더 강력한 PIN을 적용할 수 있습니다. 옵션은 다음과 같습니다.

  - **허용되지 않음**(기본값): 사용자가 PIN에 소문자를 사용하지 못하도록 차단합니다. 이 동작은 설정이 구성되지 않은 경우에도 발생합니다.
  - **허용**: 사용자가 PIN에서 소문자를 사용할 수 있도록 허용하지만 필수 사항은 아닙니다.
  - **필수**: 사용자는 PIN에 하나 이상의 소문자를 포함해야 합니다. 예를 들어, 일반적으로 하나 이상의 대문자 및 특수 문자가 필요합니다.

- **PIN에 대문자 사용**: 최종 사용자에게 대문자를 포함하도록 요구함으로써 더 강력한 PIN을 적용할 수 있습니다. 옵션은 다음과 같습니다.

  - **허용되지 않음**(기본값): 사용자가 PIN에 대문자를 사용하지 못하도록 차단합니다. 이 동작은 설정이 구성되지 않은 경우에도 발생합니다.
  - **허용**: 사용자가 PIN에서 대문자를 사용할 수 있도록 허용하지만 필수 사항은 아닙니다.
  - **필수**: 사용자는 PIN에 하나 이상의 대문자를 포함해야 합니다. 예를 들어, 일반적으로 하나 이상의 대문자 및 특수 문자가 필요합니다.

- **PIN에 특수 문자 사용**: 최종 사용자에게 특수 문자를 요구함으로써 더 강력한 PIN을 적용할 수 있습니다. 옵션은 다음과 같습니다.

  - **허용되지 않음**(기본값): 사용자가 PIN에 특수 문자를 사용하지 못하도록 차단합니다. 이 동작은 설정이 구성되지 않은 경우에도 발생합니다.
    특수 문자에는 `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`가 포함됩니다.
  - **허용**: 사용자가 PIN에서 대문자를 사용할 수 있도록 허용하지만 필수 사항은 아닙니다.
  - **필수**: 사용자는 PIN에 하나 이상의 대문자를 포함해야 합니다. 예를 들어, 일반적으로 하나 이상의 대문자 및 특수 문자가 필요합니다.

- **PIN 만료(일)**: 사용자가 변경해야 하는 기간 이후에 PIN에 대한 만료 기간을 지정하는 것이 좋습니다. 기본값은 41일입니다.

- **PIN 기록 저장**: 이전에 사용한 PIN의 재사용을 제한합니다. 기본적으로 마지막 5개 PIN을 다시 사용할 수 없습니다.  
- **PIN 복구 사용**: 사용자가 Windows Hello for Business PIN 복구 서비스를 사용하여 PIN을 변경할 수 있습니다.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **TPM(신뢰할 수 있는 플랫폼 모듈) 사용**: TPM 칩은 추가적인 데이터 보안 계층을 제공합니다. 다음 값 중 하나를 선택합니다.  
  - **사용**: 액세스할 수는 TPM이 있는 디바이스만 비즈니스용 Windows Hello를 프로비전할 수 있습니다.
  - **구성되지 않음** 모든 디바이스는 사용 가능한 TPM이 없는 경우에도 비즈니스용 Windows Hello를 프로비전할 수 있습니다. 디바이스는 먼저 TPM을 사용하려고 시도하지만 TPM을 사용할 수 없는 경우 디바이스는 소프트웨어 암호화를 사용할 수 있습니다.  

- **생체 인식 인증 허용**: 비즈니스용 Windows Hello PIN 대신 안면 인식 또는 지문과 같은 생체 인식 인증을 설정합니다. 사용자는 생체 인식 인증에 실패하는 경우 작업 PIN을 구성해야 합니다. 다음 중에서 선택합니다.

  - **사용**: 비즈니스용 Windows Hello에서 생체 인식이 허용됩니다.
  - **구성되지 않음**(기본값): 비즈니스용 Windows Hello에서 모든 계정 유형에 대해 생체 인식 인증을 금지합니다.

- **사용 가능한 경우 향상된 스푸핑 방지 사용**: Windows Hello의 스푸핑 방지 기능을 지원하는 디바이스에서 사용할 경우 선택합니다. 예를 들어 실제 얼굴 대신 얼굴 사진을 감지합니다.

  - **사용**: 지원될 경우 모든 사용자는 안면에 대해 스푸핑 방지 기능을 사용하도록 요구됩니다.  
  - **구성되지 않음**(기본값): Windows는 디바이스의 스푸핑 방지 구성을 적용합니다.

- **온-프레미스 리소스에 대한 인증서**: 

  - **사용**: 비즈니스용 Windows Hello는 인증서를 사용하여 온-프레미스 리소스에 인증할 수 있습니다.
  - **구성되지 않음**(기본값): 비즈니스용 Windows Hello에서 인증서를 사용하여 온-프레미스 리소스에 인증하지 못하도록 합니다.  

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.