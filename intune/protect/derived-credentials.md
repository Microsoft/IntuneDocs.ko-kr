---
title: Microsoft Intune에서 모바일 디바이스에 파생 자격 증명 사용 - Azure | Microsoft Docs
description: Intune VPN, 메일, Wi-Fi 프로필, 애플리케이션 및 S/MIME와 암호화를 위한 인증 방법으로 모바일 디바이스에서 파생 자격 증명을 사용합니다. 파생 자격 증명은 Special Publication 800-157에 대한 NIST 지침의 구현입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c42e5ef50f8a5a8514bc43670fc743f42b1b2d6
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585828"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>Microsoft Intune에서 파생 자격 증명 사용

‘이 문서는 iOS를 실행하는 디바이스에 적용됨’ 

인증 또는 암호화와 서명에 스마트 카드가 필요한 환경에서는 이제 Intune을 사용하여 사용자의 스마트 카드에서 파생된 인증서를 통해 모바일 디바이스를 프로비저닝할 수 있습니다. 이 인증서를 ‘파생 자격 증명’이라고 합니다.  Intune은 [여러 가지 파생 자격 증명 발급자를 지원](#supported-issuers)하지만, 한 번에 테넌트당 하나의 발급자만 사용할 수 있습니다. 

파생 자격 증명은 SP(Special Publication) 800-157의 일부로 PIV(Personal Identity Verification) 파생 자격 증명에 관한 NIST(미국 국립표준기술원) 지침을 구현한 것입니다.  

**Intune의 구현 포함**:  

- Intune 관리자는 지원되는 파생 자격 증명 발급자를 사용하도록 테넌트를 구성합니다. 파생 자격 증명 발급자의 시스템에서 Intune 관련 설정을 구성할 필요가 없습니다.

- Intune 관리자는 다음 개체의 ‘인증 방법’으로 **파생 자격 증명**을 지정합니다.   

  - iOS 네이티브 메일 앱을 포함하는 Wi-Fi, VPN 및 메일과 같은 일반적인 프로필 유형 

  - 앱 인증

  - S/MIME 서명 및 암호화 

- 사용자는 컴퓨터에서 스마트 카드를 통해 파생 자격 증명 발급자를 인증하여 파생 자격 증명을 얻습니다. 그러면 발급자는 사용자의 스마트 카드에서 파생된 인증서를 모바일 디바이스에 발급합니다. 

- 디바이스가 파생 자격 증명을 수신한 후 파생 자격 증명은 앱 또는 리소스 액세스 프로필에 파생 자격 증명이 필요할 때 인증과 S/MIME 서명 및 암호화에 사용됩니다. 

## <a name="prerequisites"></a>전제 조건

파생 자격 증명을 사용하도록 테넌트를 구성하기 전에 다음 정보를 검토합니다.

### <a name="supported-platforms"></a>지원되는 플랫폼

Intune은 다음 OS 플랫폼에서 파생 자격 증명을 지원합니다.
- iOS/iPadOS
 
### <a name="supported-issuers"></a>지원되는 발급자

Intune은 테넌트당 하나의 파생 자격 증명 발급자를 지원합니다. 다음 발급자를 사용하도록 Intune을 구성할 수 있습니다.  

- **DISA Purebred**: https://cyber.mil/pki-pke/purebred/ 
- **Entrust Datacard**: https://www.entrustdatacard.com/
- **Intercede**: https://www.intercede.com/

다른 발급자를 사용하는 방법에 대한 중요한 세부 정보는 발급자 최종 사용자 워크플로를 포함하여 해당 발급자에 대한 지침을 검토합니다. 자세한 내용은 이 문서에서 [파생 자격 증명에 대한 계획](#plan-for-derived-credentials)을 참조하세요.

> [!IMPORTANT]  
> 테넌트에서 파생 자격 증명 발급자를 삭제하면 해당 발급자를 통해 설정된 파생 자격 증명이 더 이상 작동하지 않습니다.  
> 
> 이 문서의 뒷부분에 나오는 [파생 자격 증명 발급자 변경](#change-the-derived-credential-issuer)을 참조하세요.   

### <a name="company-portal-app"></a>회사 포털 앱

파생 자격 증명을 등록할 디바이스에 Intune 회사 포털 앱을 배포하도록 계획합니다. 디바이스 사용자는 회사 포털 앱을 사용하여 자격 증명 등록 프로세스를 시작합니다. 

iOS 디바이스의 경우 [Microsoft Intune에 iOS 스토어 앱 추가](../apps/store-apps-ios.md)를 참조하세요.

## <a name="plan-for-derived-credentials"></a>파생 자격 증명에 대한 계획

파생 자격 증명 발급자를 설정하기 전에 다음 고려 사항을 이해해야 합니다.  

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) 선택한 파생 자격 증명 발급자에 대한 설명서 검토  

발급자를 구성하기 전에 해당 발급자의 설명서를 검토하여 시스템이 파생 자격 증명을 디바이스에 제공하는 방식을 이해합니다.  

선택한 발급자에 따라 등록 시 사용자가 프로세스를 완료하도록 도울 수 있는 직원이 필요할 수 있습니다. 또한 현재 Intune 구성을 검토하여 디바이스 또는 사용자가 자격 증명 요청을 완료하는 데 필요한 액세스를 차단하지 않는지 확인해야 합니다. 

예를 들어 조건부 액세스를 사용하여 비규격 디바이스의 메일 액세스를 차단할 수 있습니다. 파생 자격 증명 등록 프로세스를 시작하도록 사용자에게 알리는 데 메일 알림을 사용하는 경우 사용자는 정책을 준수할 때까지 해당 지침을 받지 못할 수 있습니다.  

마찬가지로 일부 파생 자격 증명 요청 워크플로의 경우 디바이스 카메라를 사용하여 스크린에 표시되는 QR 코드를 검색해야 합니다. 이 코드는 사용자의 스마트 카드 자격 증명을 통해 파생 자격 증명 발급자에 대해 발생한 인증 요청에 해당 디바이스를 연결합니다. 디바이스 구성 정책이 카메라 사용을 차단하면 사용자는 파생 자격 증명 등록 요청을 완료할 수 없습니다.  

일반 정보:  

- 한 번에 테넌트당 하나의 발급자만 구성할 수 있으며 테넌트의 모든 사용자 및 지원되는 디바이스가 해당 발급자를 사용할 수 있습니다.

- 파생 자격 증명을 요구하는 정책을 사용하여 대상으로 지정할 때까지 사용자는 파생 자격 증명을 등록해야 한다는 알림을 받지 않습니다.

- 알림은 회사 포털용 앱 알림, 메일 또는 두 방법을 통해 제공될 수 있습니다. 메일 알림을 사용하도록 선택하고 조건부 액세스를 사용하도록 설정하면 디바이스가 비규격인 경우 사용자가 메일 알림을 받지 못할 수 있습니다.

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) 선택한 발급자에 대한 최종 사용자 워크플로 검토

다음은 지원되는 각 파트너에 대한 주요 고려 사항과 해당 발급자 최종 사용자 워크플로의 링크입니다.  이 정보를 숙지하여 사용자 및 디바이스가 해당 발급자의 파생 자격 증명 등록을 완료하는 것이 Intune 정책 및 구성에 따라 차단되지 않도록 하세요.

#### <a name="disa-purebred"></a>DISA Purebred

[user workflow for DISA Purebred](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred)(DISA Purebred의 사용자 워크플로)를 검토하세요. 이 워크플로의 주요 요구 사항은 다음과 같습니다.  

- 사용자는 해당 스마트 카드를 사용하여 발급자에 대해 인증할 수 있는 컴퓨터 또는 키오스크에 액세스할 수 있어야 합니다. 

- 파생 자격 증명을 등록할 디바이스는 Intune 회사 포털 앱을 설치해야 합니다.

- Intune을 사용하여 파생 자격 증명을 등록할 디바이스에 [DISA Purebred 앱을 배포](#deploy-the-disa-purebred-app)합니다. 이 앱은 관리되도록 Intune을 통해 배포되어야 하며 Intune 회사 포털 앱과 함께 사용할 수 있습니다. 이 앱은 디바이스 사용자가 파생 자격 증명 요청을 완료하는 데 사용됩니다. 

- 앱이 파생 자격 증명을 등록하는 동안 DISA Purebred에 액세스할 수 있도록 DISA Purebred 앱에는 [앱별 VPN](../configuration/vpn-settings-configure.md)이 필요합니다. 

- 디바이스 사용자가 등록 프로세스 중에 라이브 에이전트를 사용해야 합니다. 등록하는 동안 사용자가 등록 프로세스를 진행할 때 시간이 제한된 일회성 암호가 사용자에게 제공됩니다.   

DISA Purebred 앱을 가져오고 구성하는 방법에 대한 자세한 내용은 이 문서의 뒷부분에 나오는 [DISA Purebred 앱 배포](#deploy-the-disa-purebred-app)를 참조하세요.  

#### <a name="entrust-datacard"></a>Entrust Datacard  
[user workflow for Entrust Datacard](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust)(Entrust Datacard의 사용자 워크플로)를 검토하세요. 이 워크플로의 주요 요구 사항은 다음과 같습니다. 

- 사용자는 해당 스마트 카드를 사용하여 발급자에 대해 인증할 수 있는 컴퓨터 또는 키오스크에 액세스할 수 있어야 합니다. 

- 파생 자격 증명을 등록할 디바이스는 Intune 회사 포털 앱을 설치해야 합니다.

- 디바이스 카메라를 사용하여 모바일 디바이스의 파생 자격 증명 요청에 인증 요청을 연결하는 QR 코드를 검색합니다.

#### <a name="intercede"></a>Intercede
[user workflow for Intercede](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede)(Intercede의 사용자 워크플로)를 검토하세요. 이 워크플로의 주요 요구 사항은 다음과 같습니다. 

- 사용자는 해당 스마트 카드를 사용하여 발급자에 대해 인증할 수 있는 컴퓨터 또는 키오스크에 액세스할 수 있어야 합니다. 

- 파생 자격 증명을 등록할 디바이스는 Intune 회사 포털 앱을 설치해야 합니다.

- 디바이스 카메라를 사용하여 모바일 디바이스의 파생 자격 증명 요청에 인증 요청을 연결하는 QR 코드를 검색합니다.

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) 디바이스에 신뢰할 수 있는 루트 인증서 배포 

신뢰할 수 있는 루트 인증서를 파생 자격 증명과 함께 사용하여 파생 자격 증명 인증서 체인이 유효하고 신뢰할 수 있는지 확인합니다. 정책에서 직접 참조되지 않는 경우에도 신뢰할 수 있는 루트 인증서가 필요합니다. [Microsoft Intune에서 디바이스에 대한 인증서 프로필 구성](certificates-configure.md)을 참조하세요.

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) 파생 자격 증명을 가져오는 방법에 대한 최종 사용자 지침 제공 

파생 자격 증명 등록 프로세스를 시작하고 선택한 발급자의 파생 자격 증명 등록 워크플로를 살펴보는 방법에 대한 지침을 만들고 사용자에게 제공합니다. 

지침을 호스트할 URL을 제공하는 것이 좋습니다. 테넌트를 위해 파생 자격 증명 발급자를 구성할 때 이 URL을 지정하며 회사 포털 앱 내에서 해당 URL을 사용할 수 있습니다. 고유한 URL을 지정하지 않으면 Intune이 일반적인 세부 정보의 링크를 제공합니다. 이 세부 정보는 모든 시나리오를 다루지 않으며 사용자 환경에 적합하지 않을 수 있습니다. 

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) 파생 자격 증명이 필요한 Intune 정책 배포 

새 정책을 만들거나 기존 정책을 편집하여 파생 자격 증명을 사용합니다. 파생 자격 증명은 앱 인증, Wi-Fi, VPN, 메일과 S/MIME 서명 및 암호화를 위한 기타 인증 방법을 대체합니다. 

사용자가 요청을 완료하지 못하게 차단할 수 있으므로 파생 자격 증명을 가져오는 프로세스의 일부로 사용할 프로세스에 액세스하는 데는 파생 자격 증명 사용을 요구하지 마세요. 

## <a name="set-up-a-derived-credential-issuer"></a>파생 자격 증명 발급자 설정

파생 자격 증명 사용을 요구하는 정책을 만들기 전에 Intune 콘솔에서 자격 증명 발급자를 설정합니다. 파생 자격 증명 발급자는 테넌트 전체 설정입니다. 테넌트는 한 번에 하나의 발급자만 지원합니다. 

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스 구성** > **파생 자격 증명**으로 이동합니다.  

   ![콘솔에서 파생 자격 증명 구성](./media/derived-credentials/configure-provider.png)   

2. 파생 자격 증명 발급자 정책의 친숙한 **표시 이름**을 지정합니다.  이 이름은 디바이스 사용자에게 표시되지 않습니다.

3. **파생 자격 증명 발급자**에 대해 테넌트를 위해 선택한 파생 자격 증명 발급자를 선택합니다.
   - DISA Purebred
   - Entrust Datacard
   - Intercede  

4. **파생 자격 증명 도움말 URL**을 지정하여 사용자가 조직의 파생 자격 증명을 가져오는 데 도움이 되는 사용자 지정 지침을 포함하는 위치의 링크를 제공합니다. 이 지침은 조직에 관련되며 선택한 발급자의 자격 증명을 가져오는 데 필요한 워크플로에 관련되어야 합니다. 이 링크는 회사 포털 앱에 표시되며 디바이스에서 액세스할 수 있어야 합니다. 

   고유한 URL을 지정하지 않으면 Intune이 일부 시나리오를 다루지 않는 일반적인 세부 정보의 링크를 제공합니다. 이 일반 지침은 사용자 환경에 적합하지 않을 수 있습니다.

5. **알림 유형** 옵션을 하나 이상 선택합니다. 알림 유형은 사용자에게 다음 시나리오를 알리는 데 사용하는 방법입니다.

   - 발급자에 디바이스를 등록하여 새 파생 자격 증명을 가져옵니다. 
   - 현재 자격 증명이 만료될 예정인 경우 새 파생 자격 증명을 가져옵니다. 
   - Wi-Fi, VPN, 메일 또는 앱 인증뿐 아니라 S/MIME 서명 및 암호화를 위한 정책과 함께 파생 자격 증명을 사용합니다. 

6. 준비가 되면 **저장**을 선택하여 파생 자격 증명 발급자의 구성을 완료합니다. 

구성을 저장한 후에는 ‘파생 자격 증명 발급자’를 제외한 모든 필드를 변경할 수 있습니다.   발급자를 변경하려면 [파생 자격 증명 발급자 변경](#change-the-derived-credential-issuer)을 참조하세요. 

## <a name="deploy-the-disa-purebred-app"></a>DISA Purebred 앱 배포

‘이 섹션은 DISA Purebred를 사용하는 경우에만 적용됩니다.’ 

Intune용 파생 자격 증명 발급자로 **DISA Purebred**를 사용하려면 DISA Purebred 앱을 가져온 후 Intune을 사용하여 앱을 디바이스에 배포해야 합니다. 디바이스 사용자는 디바이스에서 앱을 사용하여 DISA Purebred의 파생 자격 증명을 요청합니다. 

Intune을 사용하여 앱을 배포하는 것 외에도 DISA Purebred 애플리케이션에 대한 Intune 앱별 VPN을 구성합니다. 

**다음 작업을 완료합니다.** 
  
1. [DISA Purebred 애플리케이션](https://cyber.mil/pki-pke/purebred/)을 다운로드합니다.
2. Intune에 DISA Purebred 애플리케이션을 배포합니다.  [Microsoft Intune에 iOS 기간 업무 앱 추가](../apps/lob-apps-ios.md)를 참조하세요.
3. DISA Purebred 애플리케이션용 [앱별 VPN](../configuration/vpn-settings-configure.md)을 만듭니다.

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>인증과 S/MIME 서명 및 암호화에 파생 자격 증명 사용

다음 프로필 유형 및 용도를 위해 **파생 자격 증명**을 지정할 수 있습니다.  
- [애플리케이션](#use-derived-credentials-for-app-authentication)
- [전자 메일](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [S/MIME 서명 및 암호화](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  Wi-Fi 프로필의 경우 *인증 방법*은 **EAP 유형**이 다음 값 중 하나로 설정된 경우에만 사용할 수 있습니다. 
  - EAP – TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>앱 인증에 파생 자격 증명 사용

웹 사이트 및 애플리케이션에 대한 인증서 기반 인증에 파생 자격 증명을 사용합니다. 앱 인증을 위해 파생 자격 증명을 제공하려면 Intune 콘솔에서 다음 단계를 수행합니다.  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스 구성** > **프로필**로 이동한 후 **프로필 만들기**를 선택합니다.

2. **이름** 아래에 프로필의 이름을 입력합니다.

3. **플랫폼**에서 **iOS**를 선택합니다.

4. **프로필 유형**에 대해 **파생 자격 증명**을 선택합니다.

5. **확인**을 선택한 후 **만들기**를 클릭합니다.

6. **할당**을 선택하여 정책을 받아야 하는 그룹을 선택합니다.
 
사용자는 파생 자격 증명 발급자를 설정할 때 지정한 설정에 따라 앱 또는 메일 알림을 받습니다. 이 알림은 파생 자격 증명 정책을 처리할 수 있게 사용자에게 회사 포털을 시작하도록 알립니다.

## <a name="renew-a-derived-credential"></a>파생 자격 증명 갱신

파생 자격 증명은 연장하거나 갱신할 수 없습니다. 대신, 사용자는 자격 증명 요청 워크플로를 사용하여 디바이스에 대한 새 파생 자격 증명을 요청해야 합니다.

**알림 유형**에 대한 방법을 하나 이상 구성하면 Intune은 현재 파생 자격 증명이 해당 수명의 80%에 도달할 때 사용자에게 자동으로 알립니다. 이 알림을 통해 사용자는 새 파생 자격 증명을 가져오는 자격 증명 요청 프로세스를 진행할 수 있습니다. 

디바이스가 새 파생 자격 증명을 받은 후 파생 자격 증명을 사용하는 정책이 해당 디바이스에 다시 배포됩니다. 


## <a name="change-the-derived-credential-issuer"></a>파생 자격 증명 발급자 변경

테넌트에 대해 한 번에 하나의 발급자만 지원되지만 테넌트 수준에서 자격 증명 발급자를 변경할 수 있습니다. 

발급자를 변경한 후 새 발급자의 새 파생 자격 증명을 가져올지 묻는 메시지가 사용자에게 표시됩니다. 인증에 파생 자격 증명을 사용하려면 먼저 이 작업을 수행해야 합니다.

### <a name="change-the-issuer-for-your-tenant"></a>테넌트의 발급자 변경

> [!IMPORTANT]  
> 발급자를 삭제하고 즉시 이 동일한 발급자를 다시 구성하는 경우에도 해당 발급자의 파생 자격 증명을 사용하도록 프로필 및 디바이스를 업데이트해야 합니다. 발급자를 삭제하기 전에 얻은 파생 자격 증명은 더 이상 유효하지 않습니다. 

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스 구성** > **파생 자격 증명**으로 이동합니다.

2. **삭제**를 선택하여 현재 파생 자격 증명 발급자를 제거합니다.

3. 새 발급자를 구성합니다. 


### <a name="update-profiles-that-use-derived-credentials"></a>파생 자격 증명을 사용하는 프로필 업데이트

발급자를 삭제하고 새 발급자를 추가한 후 파생 자격 증명을 사용하는 각 프로필을 편집합니다. 이전 발급자를 복원하는 경우에도 이 규칙이 적용됩니다. 프로필 ‘설명’에 대한 간단한 편집을 포함하여 프로필을 편집하면 업데이트가 실행됩니다. 

### <a name="update-derived-credentials-on-devices"></a>디바이스에서 파생 자격 증명 업데이트

발급자가 삭제되고 새 발급자가 추가된 후 디바이스 사용자는 새 파생 자격 증명을 요청해야 합니다. 제거한 동일한 발급자를 추가하는 경우에도 이 규칙이 적용됩니다. 새 파생 자격 증명을 요청하는 프로세스는 새 디바이스를 등록하거나 기존 자격 증명을 갱신하는 경우에도 동일합니다. 

## <a name="next-steps"></a>다음 단계

[디바이스 구성 프로필 만들기](../configuration/device-profile-create.md)


 