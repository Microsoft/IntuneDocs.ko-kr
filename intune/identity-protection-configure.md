---
title: Microsoft Intune에서 ID 보호 설정 구성 - Azure | Microsoft Docs
description: 장치 프로필을 추가하여 Microsoft Intune에서 Windows 10 장치에 비즈니스용 Windows Hello 설정 지정
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f9d0db8e15e6de1241984f98bf651fcff1578033
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188648"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>Microsoft Intune에서 ID 보호 설정 구성

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

ID 보호 프로필 제어는 비즈니스용 Windows Hello가 관리되는 Windows 10 장치에서 프로비전되고 구성되는 방법입니다. 다음을 구성하려면 이 프로필을 만듭니다.  
* 장치 및 사용자에 대한 비즈니스용 Windows Hello 가용성
* 장치 핀 요구 사항
* 제스처 사용자가 해당 장치에 로그인하는 데 사용할 수 있는지 여부  

 사용자 및 장치 그룹을 선택하도록 또는 모든 사용자 및 모든 장치에 이 프로필을 할당할 수 있습니다. 그룹은 Intune에 체크 인할 때 ID 보호 프로필을 수신합니다.    

이 문서의 정보를 사용하여 ID 보호 프로필을 만듭니다. 그런 다음, 사용자 및 장치 그룹에 [프로필을 할당](device-profile-assign.md)합니다.

이 기능은 다음을 실행하는 장치에 적용됩니다.  
- Windows 10 이상
- Windows Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>ID보호 설정으로 장치 프로필 만들기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
4. ID 보호 프로필의 **이름** 및 **설명**을 입력합니다.
5. **플랫폼** 드롭다운 목록에서 **Windows 10 이상**을 선택합니다. 비즈니스용 Windows Hello는 Windows 10 이상을 실행하는 장치에서만 지원됩니다.
6. **프로필 형식** 드롭다운 목록에서 **ID 보호**를 선택합니다.
7. 비즈니스용 Windows Hello 창에서 비즈니스용 Windows Hello 구성에서 다음 옵션 중 하나를 선택합니다.
    * 사용 안 함. 비즈니스용 Windows Hello를 사용하지 않으려면 이 설정을 선택합니다. 화면의 다른 모든 설정은 사용할 수 없게 됩니다.
    * 사용 비즈니스용 Windows Hello 설정을 구성하려면 이 설정을 선택합니다.  

8. 이전 단계에서 **사용**을 선택한 경우에는 등록된 대상 Windows 10 및 Windows 10 모바일 장치 및 사용자에 적용될 필요한 설정을 구성합니다.

> [!NOTE]
> 사용자에게만 ID 보호 프로필을 할당하는 경우 장치 컨텍스트 기본값은 **구성되지 않음**으로 지정됩니다.  

   - **최소 PIN 길이**/**최대 PIN 길이**. 로그인을 보호하기 위해 지정한 최소 및 최대 PIN 길이를 사용하도록 장치를 구성합니다. 기본 PIN 길이는 6자이지만 최소 길이인 4자를 적용할 수 있습니다. 최대 PIN 길이는 127자입니다.  

   - **PIN에 소문자**/**PIN에 대문자**/**PIN에 특수 문자**. PIN에 대문자, 소문자, 특수 문자를 사용하도록 요구하여 강력한 PIN을 적용할 수 있습니다. 다음 중에서 선택합니다.

     - **허용**. 사용자는 해당 PIN에 문자 형식을 사용할 수 있지만 필수는 아닙니다.

     - **필수**. 사용자는 PIN에 하나 이상의 문자 형식을 포함해야 합니다. 예를 들어, 일반적으로 하나 이상의 대문자 및 특수 문자가 필요합니다.

     - **허용되지 않음**(기본값). PIN에서 대문자 형식을 사용하지 않아야 합니다. (이 동작은 설정이 구성되지 않은 경우에도 발생합니다.)<br>특수 문자에는 다음이 포함됩니다. **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **PIN 만료(일)**. 사용자가 변경해야 하는 기간 이후에 PIN에 대한 만료 기간을 지정하는 것이 좋습니다. 기본값은 41일입니다.

   - **PIN 기록 저장**. 이전에 사용한 PIN의 재사용을 제한합니다. 기본적으로 마지막 5개 PIN을 다시 사용할 수 없습니다.  
   - **PIN 복구 사용**: 사용자가 비즈니스용 Windows Hello PIN 복구 서비스를 사용하여 PIN을 변경할 수 있습니다. 
       - **사용** 클라우드 서비스는 장치에 저장할 PIN 복구 비밀을 암호화합니다. 필요한 경우 사용자는 해당 PIN을 변경할 수 있습니다.  
       - **구성되지 않음**(기본값) PIN 복구 비밀이 만들어지거나 저장되지 않았습니다. 사용자의 PIN을 잊어버린 경우 새 PIN을 가져올 유일한 방법은 기존 PIN를 삭제하고 새로 만드는 것입니다. 사용자는 액세스를 제공한 이전 PIN을 모든 서비스에 다시 등록해야 합니다.  
   
   - **TPM(신뢰할 수 있는 플랫폼 모듈) 사용**. TPM 칩은 추가적인 데이터 보안 계층을 제공합니다. 다음 값 중 하나를 선택합니다.  
     - **사용** 액세스할 수는 TPM이 있는 장치만 비즈니스용 Windows Hello를 프로비전할 수 있습니다.
     - **구성되지 않음**. 모든 장치는 사용 가능한 TPM이 없는 경우에도 비즈니스용 Windows Hello를 프로비전할 수 있습니다. 장치는 먼저 TPM을 사용하려고 시도하지만 TPM을 사용할 수 없는 경우 장치는 소프트웨어 암호화를 사용할 수 있습니다.  

   - **생체 인식 인증 허용**. 비즈니스용 Windows Hello PIN 대신 안면 인식 또는 지문과 같은 생체 인식 인증을 설정합니다. 사용자는 생체 인식 인증에 실패하는 경우 작업 PIN을 구성해야 합니다. 다음 중에서 선택합니다.

     - **사용** 비즈니스용 Windows Hello에서 생체 인식이 허용됩니다.
     - **구성되지 않음**(기본값) 비즈니스용 Windows Hello에서 모든 계정 유형에 대해 생체 인식 인증을 금지합니다.

   - **사용 가능한 경우 향상된 스푸핑 방지 사용**. Windows Hello의 스푸핑 방지 기능을 지원하는 장치에서 사용할지 여부를 구성합니다(예: 실제 얼굴 대신 얼굴 사진 검색).
       - **사용** 지원될 경우 모든 사용자는 안면에 대해 스푸핑 방지 기능을 사용하도록 요구됩니다.  
       - **구성되지 않음**(기본값) Windows는 장치의 스푸핑 방지 구성을 적용합니다.

   - **온-프레미스 리소스에 대한 인증서** 
       - **사용** 비즈니스용 Windows Hello는 인증서를 사용하여 온-프레미스 리소스에 인증할 수 있습니다.
       - **구성되지 않음**(기본값) 비즈니스용 Windows Hello에서 인증서를 사용하여 온-프레미스 리소스에 인증하지 못하도록 합니다.  
9. **확인**을 클릭하여 프로필을 저장합니다.  

프로필이 만들어지고 **장치 구성 - 프로필** 목록에 나타납니다. 계속해서 이 프로필을 그룹에 할당하려면 [장치 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
