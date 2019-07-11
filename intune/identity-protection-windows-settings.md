---
title: Microsoft Intune의 Windows Hello for Business 설정 - Azure | Microsoft Docs
description: Microsoft Intune의 Windows 10 디바이스에서 Windows Hello for Business를 사용하고 구성하려면 ID 보호 프로필의 모든 PIN, 생체 인식 및 스푸핑 방지 설정 목록을 참조하세요.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 5a8111d2542269441c7305aad0aad0b7c2162037
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735622"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Intune에서 Windows Hello for Business를 사용하기 위한 Windows 10 디바이스 설정

이 문서에서는 Intune의 Windows 10 디바이스에서 제어할 수 있는 Windows Hello for Business 설정을 나열하고 설명합니다. Intune 관리자인 경우 이러한 설정을 MDM(모바일 디바이스 관리) 솔루션의 일부로 구성하고 Windows 10 디바이스에 할당할 수 있습니다. 

이러한 설정에 대한 추가 정보는 Windows Hello 설명서의 [비즈니스용 Windows Hello 정책 설정 구성](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings)에서 확인할 수 있습니다.


Intune의 Windows Hello for Business 프로필에 대한 자세한 내용은 [ID 보호 구성](identity-protection-configure.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[구성 프로필을 만듭니다](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>비즈니스용 Windows Hello
- **Windows Hello for Business 구성**:
  - **구성되지 않음** - Intune을 사용하여 비즈니스용 Windows Hello 설정을 제어하지 않으려면 이 설정을 선택합니다. Windows 10 디바이스에서 기존 비즈니스용 Windows Hello 설정이 변경되지 않습니다. 창의 다른 모든 설정은 사용할 수 없게 됩니다.

  - **사용 안 함** - 비즈니스용 Windows Hello를 사용하지 않으려면 이 설정을 선택합니다. 화면의 다른 모든 설정은 사용할 수 없게 됩니다.
  - **사용** - 비즈니스용 Windows Hello 설정을 구성하려면 이 설정을 선택합니다.  
  
  **기본값**: 구성되지 않음

  *사용*으로 설정 된 경우 다음 설정을 사용할 수 있습니다.

  - **최소 PIN 길이**  
    장치에 대 한 최소 PIN 길이를 지정 하 여 로그인의 보안을 유지 합니다. Windows 장치 기본값은 6 자 이지만이 설정은 최소 4 ~ 127 문자를 적용할 수 있습니다. 

    **기본값**: *구성되지 않음*

  - **최대 PIN 길이**  
  장치에 대 한 최대 PIN 길이를 지정 하 여 로그인의 보안을 유지 합니다. Windows 장치 기본값은 6 자 이지만이 설정은 최소 4 ~ 127 문자를 적용할 수 있습니다.  

    **기본값**: *구성되지 않음*  

  - **PIN에 소문자 사용**  
    최종 사용자에게 소문자를 포함하도록 요구함으로써 더 강력한 PIN을 적용할 수 있습니다. 옵션은 다음과 같습니다.

    - **허용되지 않음** - 사용자가 PIN에 소문자를 사용하지 못하도록 차단합니다. 이 동작은 설정이 구성되지 않은 경우에도 발생합니다.
    - **허용** - 사용자가 PIN에서 소문자를 사용할 수 있도록 허용하지만 필수 사항은 아닙니다.
    - **필수** - 사용자는 PIN에 하나 이상의 소문자를 포함해야 합니다. 예를 들어, 일반적으로 하나 이상의 대문자 및 특수 문자가 필요합니다.

  - **PIN에 대문자 사용**  
    최종 사용자에게 대문자를 포함하도록 요구함으로써 더 강력한 PIN을 적용할 수 있습니다. 옵션은 다음과 같습니다.

    - **허용되지 않음** - 사용자가 PIN에 대문자를 사용하지 못하도록 차단합니다. 이 동작은 설정이 구성되지 않은 경우에도 발생합니다.
    - **허용** - 사용자가 PIN에서 대문자를 사용할 수 있도록 허용하지만 필수 사항은 아닙니다.
    - **필수** - 사용자는 PIN에 하나 이상의 대문자를 포함해야 합니다. 예를 들어, 일반적으로 하나 이상의 대문자 및 특수 문자가 필요합니다.

  - **PIN에 특수 문자 사용**  
    최종 사용자에게 특수 문자를 요구함으로써 더 강력한 PIN을 적용할 수 있습니다. 특수 문자에는 `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`가 포함됩니다.  

    옵션은 다음과 같습니다.
    - **허용되지 않음** - 사용자가 PIN에 특수 문자를 사용하지 못하도록 차단합니다. 이 동작은 설정이 구성되지 않은 경우에도 발생합니다.
    - **허용** - 사용자가 PIN에서 대문자를 사용할 수 있도록 허용하지만 필수 사항은 아닙니다.
    - **필수** - 사용자는 PIN에 하나 이상의 대문자를 포함해야 합니다. 예를 들어, 일반적으로 하나 이상의 대문자 및 특수 문자가 필요합니다.

    **기본값**: 허용 되지 않음

  - **PIN 만료(일)**  
    사용자가 변경해야 하는 기간 이후에 PIN에 대한 만료 기간을 지정하는 것이 좋습니다. Windows 장치 기본값은 41 일입니다.

    **기본값**: 구성되지 않음

  - **PIN 기록 저장**  
    이전에 사용한 PIN의 재사용을 제한합니다. Windows 장치는 마지막 5 개 Pin의 재사용을 방지 하기 위해 기본적으로 사용 됩니다.  

    **기본값**: 구성되지 않음  

  - **PIN 복구 사용**   
    사용자가 비즈니스용 Windows Hello PIN 복구 서비스를 사용할 수 있습니다. 
    
    - **사용** -pin 복구 암호는 장치에 저장 되 고 사용자는 필요한 경우 pin을 변경할 수 있습니다.  
    - **사용** 안 함-복구 암호가 만들어지거나 저장 되지 않습니다.

    **기본값**: 구성되지 않음

  - **TPM(신뢰할 수 있는 플랫폼 모듈) 사용**   
    TPM 칩은 추가적인 데이터 보안 계층을 제공합니다.  

    - **사용** - 액세스할 수는 TPM이 있는 디바이스만 비즈니스용 Windows Hello를 프로비저닝할 수 있습니다.
    - **구성되지 않음** - 디바이스에서 먼저 TPM을 사용하려고 합니다. 사용할 수 없는 경우에는 소프트웨어 암호화를 사용할 수 있습니다.
    
    **기본값**: 구성되지 않음

  - **생체 인식 인증 허용**  
     비즈니스용 Windows Hello PIN 대신 안면 인식 또는 지문과 같은 생체 인식 인증을 설정합니다. 사용자는 생체 인식 인증에 실패하는 경우 작업 PIN을 구성해야 합니다. 다음 중에서 선택합니다.

    - **사용** - 비즈니스용 Windows Hello에서 생체 인식 인증이 허용됩니다.
    - **구성되지 않음** - 비즈니스용 Windows Hello에서 모든 계정 유형에 대해 생체 인식 인증을 금지합니다.

    **기본값**: 구성되지 않음

  - **사용 가능한 경우 향상된 스푸핑 방지 사용**  
    Windows Hello의 스푸핑 방지 기능을 지원하는 디바이스에서 사용할지 여부를 구성합니다(예: 실제 얼굴 대신 얼굴 사진 검색).  
    - **사용** - Windows는 지원되는 경우 모든 사용자는 안면에 대해 스푸핑 방지 기능을 사용하도록 요구됩니다.
    - **구성되지 않음** - Windows는 디바이스의 스푸핑 방지 구성을 적용합니다.

    **기본값**: 구성되지 않음

  - **온-프레미스 리소스에 대한 인증서**  

    - **사용** - 비즈니스용 Windows Hello는 인증서를 사용하여 온-프레미스 리소스에 인증할 수 있습니다.
    - **구성되지 않음** - 비즈니스용 Windows Hello에서 인증서를 사용하여 온-프레미스 리소스에 인증하지 못하도록 합니다. 대신 디바이스가 *키 신뢰 온-프레미스 인증*의 기본 동작을 사용합니다. 자세한 내용은 Windows Hello 설명서에서 [온-프레미스 인증에 대한 사용자 인증서](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication)를 참조하세요.  

  **기본값**: 구성되지 않음

- **로그인에 보안 키 사용**  
  이 설정은 Windows 10 버전 1903 이상을 실행 하는 장치에 사용할 수 있습니다. 이 기능을 사용 하 여 로그인에 Windows Hello 보안 키 사용에 대 한 지원을 관리 합니다.  

  - **사용** -사용자는이 정책을 대상으로 하는 pc에 대 한 로그온 자격 증명으로 Windows Hello 보안 키를 사용할 수 있습니다. 
  - **사용** 안 함-보안 키가 사용 하지 않도록 설정 되며 사용자가 pc에 로그인 하는 데 사용할 수 없습니다.   

  **기본값**: 구성되지 않음

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
