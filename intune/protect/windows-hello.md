---
title: Microsoft Intune과 비즈니스용 Windows Hello 통합
titleSuffix: Microsoft Intune
description: 관리 디바이스에서 비즈니스용 Windows Hello 사용을 제어하기 위한 정책을 만드는 방법을 알아봅니다."
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: ed3152a6717898aa1f758fb06a5f701048aebed4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508774"
---
# <a name="integrate-windows-hello-for-business-with-microsoft-intune"></a>Microsoft Intune과 비즈니스용 Windows Hello 통합  


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

비즈니스용 Windows Hello(이전의 Microsoft Passport for Work)과 Microsoft Intune을 통합할 수 있습니다.

 비즈니스용 Hello는 Active Directory 또는 Azure Active Directory 계정을 사용하여 암호, 스마트 카드 또는 가상 스마트 카드를 대신하는 대체 로그인 방법입니다. 이를 사용하면 암호 대신 *사용자 제스처*를 사용하여 로그인할 수 있습니다. 사용자 제스처는 단순 PIN, 생체 인식 인증(예: Windows Hello) 또는 외부 디바이스(예: 지문 판독기)일 수 있습니다.

Intune은 다음 두 가지 방법으로 비즈니스용 Hello에 통합됩니다.

- **디바이스 등록**에서 Intune 정책을 만들 수 있습니다. 이 정책은 전체 조직(테넌트 수준)을 대상으로 합니다. Windows AutoPilot OOBE(out-of-box-experience)를 지원하며 디바이스를 등록하는 경우 적용됩니다. 
- **디바이스 구성**에서 ID 보호 프로필을 만들 수 있습니다. 이 프로필은 할당된 사용자 및 디바이스를 대상으로 하고, 체크 인하는 동안 적용됩니다. 

이 문서를 사용하여 전체 조직을 대상으로 하는 기본 비즈니스용 Windows Hello 정책을 만듭니다. 사용자 및 디바이스 그룹 선택에 적용되는 ID 보호 프로필을 만들려면 [ID 보호 프로필 구성](identity-protection-configure.md)을 참조하세요.  

<!--- - You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> Windows 10 데스크톱 및 1주년 업데이트 전의 모바일 버전에서 리소스에 인증하는 데 사용할 수 있는 두 개의 서로 다른 PIN을 설정할 수 있습니다.
> - **디바이스 PIN**을 디바이스 잠금을 해제하고 클라우드 리소스에 연결하는 데 사용할 수 있습니다.
> - **작업 PIN**은 사용자의 개인 디바이스(BYOD)에서 Azure AD 리소스에 액세스하는 데 사용되었습니다.
> 
> 1주년 업데이트에서 이러한 두 PIN이 하나의 단일 디바이스 PIN에 병합되었습니다.
> 이제 디바이스 PIN을 제어하도록 설정한 Intune 구성 정책뿐 아니라, 구성한 비즈니스용 Windows Hello 정책 둘 다 이러한 새 PIN 값으로 설정되어 있습니다.
> PIN을 제어하기 위해 두 정책 유형을 설정한 경우 비즈니스용 Windows Hello 정책이 Windows 10 Desktop 및 모바일 디바이스에 모두 적용됩니다.
> 정책 충돌이 해결되어 있고 PIN 정책을 올바르게 적용되었는지 확인하려면 비즈니스용 Windows Hello 정책을 내 구성 정책의 설정에 맞게 업데이트한 다음, 회사 포털 앱에서 디바이스를 동기화하도록 사용자에게 요청합니다.



## <a name="create-a-windows-hello-for-business-policy"></a>비즈니스용 Windows Hello 정책 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.

2. **디바이스 등록** > **Windows 등록** > **비즈니스용 Windows Hello**로 이동합니다. 비즈니스용 Windows Hello 창이 열립니다.

3. 다음 중에서 **비즈니스용 Windows Hello 구성**을 위한 옵션을 선택합니다.

    - **Disabled**. 비즈니스용 Windows Hello를 사용하지 않으려면 이 설정을 선택합니다. 사용하지 않도록 설정된 경우 사용자는 프로비전이 필요할 수 있는 Azure Active Directory 가입 휴대폰을 제외하고 비즈니스용 Windows Hello를 프로비전할 수 없습니다.
    - **Enabled**. 비즈니스용 Windows Hello 설정을 구성하려면 이 설정을 선택합니다.  *Enabled*를 선택하면 WIndows Hello용 추가 설정이 표시됩니다. 
    - **구성되지 않음**. Intune을 사용하여 비즈니스용 Windows Hello 설정을 제어하지 않으려면 이 설정을 선택합니다. Windows 10 디바이스에서 기존 비즈니스용 Windows Hello 설정이 변경되지 않습니다. 창의 다른 모든 설정은 사용할 수 없게 됩니다.

4. 이전 단계에서 **사용**을 선택한 경우에는 등록된 모든 Windows 10 및 Windows 10 모바일 디바이스에 적용될 필요한 설정을 구성합니다. 이러한 설정을 구성한 후에 **저장**을 선택합니다.

   - **TPM(신뢰할 수 있는 플랫폼 모듈) 사용**:  
     TPM 칩은 추가적인 데이터 보안 계층을 제공합니다. 다음 값 중 하나를 선택합니다.

     - **필수**(기본값). 액세스할 수는 TPM이 있는 디바이스만 비즈니스용 Windows Hello를 프로비전할 수 있습니다.
     - **기본 설정**. 디바이스에서 먼저 TPM을 사용하려고 합니다. 사용할 수 없는 경우에는 소프트웨어 암호화를 사용할 수 있습니다.

   - **최소 PIN 길이** 및 **최대 PIN 길이**:  
     로그인을 보호하기 위해 지정한 최소 및 최대 PIN 길이를 사용하도록 디바이스를 구성합니다. 기본 PIN 길이는 6자이지만 최소 길이인 4자를 적용할 수 있습니다. 최대 PIN 길이는 127자입니다.

   - **PIN의 소문자**, **PIN의 대문자** 및 **PIN의 특수 문자**.  
     PIN에 대문자, 소문자, 특수 문자를 사용하도록 요구하여 강력한 PIN을 적용할 수 있습니다. 각각에 대해 다음을 선택합니다.

     - **허용**. 사용자는 해당 PIN에 문자 형식을 사용할 수 있지만 필수는 아닙니다.

     - **필수**. 사용자는 PIN에 하나 이상의 문자 형식을 포함해야 합니다. 예를 들어, 일반적으로 하나 이상의 대문자 및 특수 문자가 필요합니다.

     - **허용되지 않음**(기본값). PIN에서 대문자 형식을 사용하지 않아야 합니다. (설정이 구성되지 않은 경우에도 이 동작 수행)   

       특수 문자에는 다음이 포함됩니다. **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **PIN 만료(일)** :  
     사용자가 변경해야 하는 기간 이후에 PIN에 대한 만료 기간을 지정하는 것이 좋습니다. 기본값은 41일입니다.

   - **PIN 기록 저장**:  
     이전에 사용한 PIN의 재사용을 제한합니다. 기본적으로 마지막 5개 PIN을 다시 사용할 수 없습니다.

   - **생체 인식 인증 허용**:  
     비즈니스용 Windows Hello PIN 대신 안면 인식 또는 지문과 같은 생체 인식 인증을 설정합니다. 사용자는 생체 인식 인증에 실패하는 경우 작업 PIN을 구성해야 합니다. 다음 중에서 선택합니다.

     - **예**. 비즈니스용 Windows Hello에서 생체 인식이 허용됩니다.
     - **아니요**. 비즈니스용 Windows Hello에서 모든 계정 유형에 대해 생체 인식 인증을 금지합니다.

   - **사용 가능한 경우 향상된 스푸핑 방지 사용**:  
     Windows Hello의 스푸핑 방지 기능을 지원하는 디바이스에서 사용할지 여부를 구성합니다(예: 실제 얼굴 대신 얼굴 사진 검색).  

     **예**로 설정하면 Windows에서는 모든 사용자가 얼굴 인식 기능(지원되는 경우)에 대해 스푸핑 방지 기능을 사용해야 합니다.

   - **휴대폰 로그인 허용**:  
     이 옵션이 **예**로 설정되면 원격 Passport를 데스크톱 컴퓨터 인증을 위한 휴대용 포함 디바이스로 사용할 수 있습니다. 데스크톱 컴퓨터가 Azure Active Directory에 가입되어 있어야 하고 해당 포함 디바이스는 비즈니스용 Windows Hello PIN으로 구성되어야 합니다.

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business 지원

Windows Holographic for Business는 다음과 같은 비즈니스용 Windows Hello 설정을 지원합니다.

- Use a Trusted Platform Module (TPM)(TPM(신뢰할 수 있는 플랫폼 모듈) 사용)
- 최소 PIN 길이
- 최대 PIN 길이
- PIN에 소문자 사용
- PIN에 대문자 사용
- PIN에 특수 문자 사용
- PIN 만료(일)
- PIN 기록 기억

## <a name="further-information"></a>추가 정보
비즈니스용 Windows Hello에 관한 자세한 내용은 Windows 10 설명서의 [가이드](https://technet.microsoft.com/library/mt589441.aspx)를 참조하십시오.
