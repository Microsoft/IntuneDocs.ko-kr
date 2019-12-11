---
title: Microsoft Edge에 대 한 Intune 보안 기준 설정
titleSuffix: Microsoft Intune
description: Microsoft Edge 브라우저 관리를 위해 Intune에서 지원 되는 보안 기준 설정
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c75029c60609b0383e2f647e5b94144d4186248c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73754872"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Intune에 대 한 Microsoft Edge 기준선 설정

Microsoft Intune에서 지 원하는 Microsoft Edge 웹 브라우저 기준 설정을 봅니다. Microsoft Edge 기준선 기본값은 Microsoft Edge 브라우저에 권장 되는 구성을 나타내며 다른 보안 기준의 기준선 기본값과 일치 하지 않을 수 있습니다.

> [!NOTE]
> Microsoft Edge 기준선은 공개 미리 보기로 제공 됩니다. 

## <a name="microsoft-edge"></a>Microsoft Edge

- **사이트에 대 한 Microsoft Defender SmartScreen 프롬프트 무시 방지**  
  **기본**: 사용  
  Microsoft Edge CSP: [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  이 정책 설정을 통해 사용자가 잠재적으로 악성 웹 사이트에 대 한 Microsoft Defender SmartScreen 경고를 재정의할 수 있는지 여부를 결정할 수 있습니다. 
  - 이 설정을 사용 하도록 설정 하면 사용자는 Microsoft Defender SmartScreen 경고를 무시할 수 없으며 사이트를 계속 진행 하지 못하도록 차단 됩니다. 
  - 이 설정을 사용 하지 않도록 설정 하거나 구성 하지 않으면 사용자가 Microsoft Defender SmartScreen 경고를 무시 하 고 사이트를 계속 진행할 수 있습니다.

- **최소 SSL 버전 사용**  
  **기본**: 사용  

  지원 되는 최소 버전의 SSL을 설정 합니다. 이 정책을 *구성 되지 않음*으로 설정 하면 Microsoft Edge에서 기본 최소 버전의 *TLS 1.0*을 사용 합니다. *사용*으로 설정 되 면 다음 값에서 최소 버전을 선택할 수 있습니다.

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **최소 SSL 버전 사용**  
    **기본값**: TLS 1.2

- **다운로드에 대 한 Microsoft Defender SmartScreen 경고 바이패스 방지**  
  **기본**: 사용  
  Microsoft Edge CSP: [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  이 정책을 사용 하면 사용자가 확인 되지 않은 다운로드에 대해 Microsoft Defender SmartScreen 경고를 재정의할 수 있는지 여부를 결정할 수 있습니다.
  - 이 정책을 사용 하도록 설정 하면 조직의 사용자가 Microsoft Defender SmartScreen 경고를 무시할 수 없으며, 확인 되지 않은 다운로드를 완료할 수 없습니다.
  - 이 정책을 사용 하지 않도록 설정 하거나 구성 하지 않으면 사용자가 Microsoft Defender SmartScreen 경고를 무시 하 고 확인 되지 않은 다운로드를 완료할 수 있습니다.

- **사용자가 SSL 경고 페이지에서 계속할 수 있도록 허용**  
  **기본**: 사용 안 함  
  Microsoft Edge CSP: [Browser/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  Microsoft Edge는 사용자가 SSL 오류가 있는 사이트를 방문할 때 경고 페이지를 표시 합니다. 이 정책을 *사용 또는 사용* *안*함으로 설정 하면 사용자가 이러한 경고 페이지를 클릭할 수 있습니다. 이 정책을 *사용 하지 않도록 설정*하면 사용자는 경고 페이지를 클릭 하지 못하도록 차단 됩니다. 

- **기본 Adobe Flash 설정**  
  **기본**: 사용  
  Microsoft Edge CSP: [browser/AllowFlash](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflash)및 [browser/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  ' PluginsAllowedForUrls ' 또는 ' PluginsBlockedForUrls '가 적용 되지 않는 웹 사이트에서 Adobe Flash 플러그 인을 자동으로 실행할 수 있는지 여부를 결정 합니다. 

  - 모든 사이트에서 Adobe Flash를 차단 하려면 ' BlockPlugins 인 '을 선택 합니다.
  - Adobe Flash를 실행 하려면 [클릭 하 여 재생]을 선택 하 고, 사용자는 자리 표시자를 클릭 하 여 시작 해야 합니다.
  
   어떤 경우 든 ' PluginsAllowedForUrls ' 및 ' PluginsBlockedForUrls ' 정책은 ' DefaultPluginsSetting ' 보다 우선적으로 적용 됩니다. 자동 재생은 ' PluginsAllowedForUrls ' 정책에 명시적으로 나열 된 도메인에만 허용 됩니다. 
   모든 사이트에 대해 자동 재생을 사용 하려면이 목록에 http://* 및 https://*를 추가 하는 것이 좋습니다. 
   
   - 이 정책을 *구성 되지 않음*으로 설정 하면 사용자가이 설정을 수동으로 변경할 수 있습니다. * 2 = Adobe Flash 플러그 인 차단 * 3 = 이전 ' 1 ' 옵션 집합 모두 사용을 재생 하려면 클릭 하세요. 그러나 이제이 기능은 ' PluginsAllowedForUrls ' 정책에 의해서만 처리 됩니다. ' 1 '을 사용 하는 기존 정책은 클릭 하 여 재생 모드로 작동 합니다.  
 
  - **기본 Adobe Flash 설정**  
    **기본값**: Adobe Flash 플러그 인 차단

- **모든 사이트에 사이트 격리 사용**  
  **기본**: 사용  

  ' SitePerProcess ' 정책을 사용 하면 사용자가 모든 사이트를 격리 하는 기본 동작을 옵트아웃 하는 것을 방지할 수 있습니다. IsolateOrigins 정책을 사용 하 여 보다 세분화 된 추가 원본을 격리할 수도 있습니다.

  - 이 정책을 *사용*으로 설정 하면 사용자는 각 사이트가 자체 프로세스에서 실행 되는 기본 동작을 옵트아웃 (opt out) 할 수 없습니다. 
  - 사용 *안 함* 또는 *구성 되지 않음*을 사용 하는 경우 사용자는 사이트 격리를 옵트아웃 (opt out) 할 수 있습니다. 예를 들어 edge://flags의 "사이트 격리 사용 안 함" 항목을 사용 합니다. 정책을 사용 하지 않도록 설정 하거나 정책을 구성 하지 않으면 사이트 격리가 해제 되지 않습니다.

- **지원 되는 인증 체계**  
  **기본**: 사용  

  지원 되는 HTTP 인증 체계를 지정 합니다. ' 기본 ', ' 다이제스트 ', ' ntlm ' 및 ' negotiate ' 값을 사용 하 여 정책을 구성할 수 있습니다. 여러 값을 쉼표로 구분 합니다. 이 정책을 구성 하지 않으면 네 가지 구성표가 모두 사용 됩니다.
 
  - **지원 되는 인증 체계**  
    다음 옵션 중에서 선택합니다. 
    - 기본
    - 다이제스트
    - NTLM *(기본적으로 선택됨)*
    - Negotiate *(기본적으로 선택 됨)*

- **암호 관리자에 암호 저장 사용**  
  **기본**: 사용 안 함  
  Microsoft Edge CSP: [Browser/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Microsoft Edge를 사용 하 여 사용자 암호를 저장 합니다. 
  - 이 정책을 사용 하도록 설정 하면 사용자가 Microsoft Edge에 암호를 저장할 수 있습니다. 다음 번에 사이트를 방문할 때 Microsoft Edge가 자동으로 암호를 입력 합니다. 
  - 이 정책을 사용 하지 않도록 설정 하면 사용자는 새 암호를 저장할 수 없지만 이전에 저장 된 암호는 계속 사용할 수 있습니다. 
  
  이 정책을 *사용* 또는 사용 *안 함*으로 설정 하면 사용자가 Microsoft Edge에서이 정책을 변경 하거나 재정의할 수 없습니다. 
  
  *구성 되지 않음*으로 설정 하면 사용자가 암호를 저장할 수 있을 뿐 아니라이 기능을 해제할 수 있습니다.

- **설치할 수 없는 확장 제어**  
  **기본**: 사용  

  사용자가 Microsoft Edge에서 설치할 수 없는 특정 확장을 나열 합니다. 이 정책을 배포 하면 이전에 설치 된이 목록에 있는 모든 확장을 사용할 수 없게 되며 사용자는이를 사용 하도록 설정할 수 없습니다. 차단 된 확장 목록에서 항목을 제거 하는 경우 해당 확장은 이전에 설치 된 모든 위치에서 자동으로 다시 사용 하도록 설정 됩니다.
  
  허용 목록에 명시적으로 나열 되지 않은 모든 확장을 차단 하려면 **\*** 을 사용 합니다. 이 정책이 *구성 되지 않음*으로 설정 된 경우 사용자는 Microsoft Edge에 확장을 설치할 수 있습니다. 
  
  값 예: extension_id1 extension_id2.  
  <br>
  - **확장 Id 사용자를 설치할 수 없도록 방지 해야 합니다 (또는 * all).**  
    **추가** 를 선택 하 고 추가 확장을 지정 합니다. **\*** 이(가) 기본적으로 선택됩니다.

- **Microsoft Defender SmartScreen 구성**  
  **기본**: 사용  
  Microsoft Edge CSP: [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  이 정책 설정을 사용 하면 Microsoft Defender SmartScreen을 켤 지 여부를 구성할 수 있습니다. Microsoft Defender SmartScreen은 잠재적인 피싱 사기 및 악성 소프트웨어 로부터 사용자를 보호 하는 데 도움이 되는 경고 메시지를 제공 합니다. 
  
  - 기본적으로 Microsoft Defender SmartScreen은 설정 되어 있습니다. 이 설정을 사용 하도록 설정 하면 Microsoft Defender SmartScreen이 설정 되 고 사용자가 해제할 수 없습니다.
  - 이 설정을 사용 하지 않도록 설정 하면 Microsoft Defender SmartScreen이 꺼지고 사용자가 켤 수 없습니다. 
  - *구성 되지 않음*으로 설정 하면 사용자가 Microsoft Defender SmartScreen을 사용할지 여부를 선택할 수 있습니다. 
  
  이 정책은 Microsoft Active Director 도메인에 조인 된 Windows 인스턴스나 장치 관리를 위해 등록 된 Windows 10 Pro 또는 Enterprise 인스턴스에만 사용할 수 있습니다.

- **사용자 수준 기본 메시징 호스트 허용 (관리자 권한 없이 설치 됨)**  
  **기본**: 사용 안 함  

  기본 메시징 호스트의 사용자 수준 설치를 사용 하도록 설정 합니다. 
  - 이 정책을 사용 하지 않도록 설정 하는 경우 Microsoft Edge는 시스템 수준에 설치 된 네이티브 메시징 호스트만 사용 합니다. 기본적으로이 정책을 구성 하지 않으면 Microsoft Edge에서 사용자 수준 기본 메시징 호스트의 사용을 허용 합니다.

## <a name="next-steps"></a>다음 단계

[Intune에서 보안 기준 사용](security-baselines.md)
