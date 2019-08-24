---
title: Microsoft Intune과 Lookout 통합 설정
titleSuffix: Microsoft Intune
description: 회사 리소스에의 모바일 디바이스 액세스를 제어하기 위해 Mobile Threat Defense 솔루션인 Lookout Mobile Endpoint Security와 Intune을 통합하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be2e9371288961d0afdf7ad6e8cfec8f734087f6
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529904"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Intune과 Lookout Mobile Endpoint Security 통합 설정
[필수 조건](lookout-mobile-threat-defense-connector.md#prerequisites)에 맞는 환경에서는 Intune과 Lookout Mobile Endpoint Security를 통합할 수 있습니다. 이 문서의 정보에서는 통합을 설정하고 Intune과 함께 사용하기 위해 Lookout에서 중요 설정을 구성하는 방법을 안내합니다.  

> [!IMPORTANT]
> 아직 Azure AD 테넌트와 연결되지 않은 기존 Lookout Mobile Endpoint Security 테넌트는 Azure AD와 Intune을 통합하는 데 사용할 수 없습니다. 새 Lookout Mobile Endpoint Security 테넌트를 만들려면 Lookout 지원 센터로 문의하세요. 새 테넌트를 사용하여 Azure AD 사용자를 등록할 수 있습니다.

## <a name="collect-azure-ad-information"></a>Azure AD 정보 수집  
Intune과 Lookout을 통합하려면 Lookout Mobility Endpoint Security 테넌트를 Azure AD(Active Directory) 구독에 연결합니다.

Intune과 Lookout Mobile Endpoint Security 구독 통합을 사용하도록 설정하려면 Lookout 지원 센터(enterprisesupport@lookout.com)에 다음 정보를 제공합니다.  

- **Azure AD 테넌트 디렉터리 ID**  

- **모든** Lookout MES(Mobile Endpoint Security) 콘솔 권한이 있는 그룹의 **Azure AD 그룹 개체 ID**입니다.  
  **Lookout 콘솔**에 로그인할 수 있는 *모든 권한*이 있는 사용자를 포함하려면 Azure AD에서 이 사용자 그룹을 만듭니다. 사용자가 이 그룹 또는 선택적 ‘제한된 권한’ 그룹의 구성원이어야만 Lookout 콘솔에 로그인할 수 있습니다.  

- **제한된** Lookout MES 콘솔 액세스 권한이 있는 그룹’(선택적 그룹)’의**Azure AD 그룹 개체 ID**입니다.  
  Lookout 콘솔의 여러 구성 및 등록 관련 모듈에 액세스할 수 없는 사용자를 포함하려면 Azure AD에서 이 선택적 사용자 그룹을 만듭니다. 대신 이러한 사용자는 Lookout 콘솔의 **보안 정책** 모듈에 대한 읽기 전용 권한을 가집니다. 사용자가 이 선택적 그룹 또는 필요한 ‘모든 권한’ 그룹의 구성원이어야만 Lookout 콘솔에 로그인할 수 있습니다. 

 > [!TIP] 
 > 사용 권한에 대한 자세한 내용은 Lookout 웹 사이트에서 [이 문서](https://personal.support.lookout.com/hc/articles/114094105653)를 참조하세요.

### <a name="collect-information-from-azure-ad"></a>Azure AD에서 정보 수집 

1. [Azure Portal](https://portal.azure.com)에 전역 관리자 계정으로 로그인합니다.

2. **Azure Active Directory** > **속성**으로 이동하고 **디렉터리 ID**를 찾습니다. ‘복사’ 단추를 사용하여 디렉터리 ID를 복사한 다음 텍스트 파일에 저장합니다. 

   ![Azure AD 속성](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. 그런 다음 Azure AD 사용자에게 Lookout 콘솔에 대한 권한을 부여하는 데 사용할 Azure AD 그룹 ID를 찾습니다. 한 그룹은 ‘모든 권한’을 부여하기 위한 것이며, ‘제한된 권한’의 두 번째 그룹은 선택 사항입니다.   각 계정의 ‘개체 ID’를 가져오려면 다음과 같이 합니다.   
   1. **Azure Active Directory** > **그룹**으로 이동하여 그룹 - 모든 그룹  창을 엽니다.  

   2. ‘모든 권한’을 부여하기 위해 만든 그룹을 선택하여 ‘개요’ 창을 엽니다.    

   3. ‘복사’ 단추를 사용하여 개체 ID를 복사한 다음 텍스트 파일에 저장합니다.   

   4. 제한된 권한 그룹을 사용하는 경우 이 그룹을 대상으로 프로세스를 반복합니다.   

      ![Azure AD 그룹 개체 ID](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   이 정보를 수집한 후 Lookout 지원 센터로 문의하세요(메일: enterprisesupport@lookout.com). Lookout 지원 팀은 주요 담당자와 함께 제공받은 정보를 사용하여 구독을 등록하고 Lookout 엔터프라이즈 계정을 만듭니다.  

## <a name="configure-your-lookout-subscription"></a>Lookout 구독 구성  
Lookout 지원 팀이 Lookout 엔터프라이즈 계정을 만들면 사용자 회사의 주요 담당자에게 로그인 URL의 링크(https://aad.lookout.com/les?action=consent )가 포함된 이메일을 전송합니다. 

### <a name="initial-sign-in"></a>초기 로그인  
MES Lookout 콘솔에 처음 로그인하면 동의 페이지(https://aad.lookout.com/les?action=consent) 가 표시됩니다. Azure AD 전역 관리자가 로그인하고 **동의**하면 됩니다. 이후 로그인에서 사용자는 이 수준의 Azure AD 권한이 필요하지 않습니다. 

 동의 페이지가 표시됩니다. **동의**를 선택하여 등록을 완료합니다. 
   ![Lookout 콘솔의 첫 번째 로그인 페이지 스크린샷](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

동의하고 승인하면 Lookout 콘솔로 리디렉션됩니다.

초기 로그인과 동의를 완료한 이후에 https://aad.lookout.com 에서 로그인하는 사용자는 MES 콘솔로 리디렉션됩니다. 동의가 아직 승인되지 않은 경우 로그인을 시도하면 모두 잘못된 로그인 오류가 발생합니다.

### <a name="configure-the-intune-connector"></a>Intune Connector 구성  
다음 절차에서는 Lookout 배포를 테스트하기 위해 이전에 Azure AD에서 사용자 그룹을 만들었다고 가정합니다. 작은 그룹의 사용자로 시작하여 Lookout 및 Intune 관리자가 제품 통합에 익숙해지도록 하는 것이 가장 좋습니다. 익숙해진 후에 추가 사용자 그룹으로 등록을 확장할 수 있습니다.

1. [Lookout MES 콘솔](https://aad.lookout.com)에 로그인하고 **시스템** > **커넥터**로 이동한 다음 **커넥터 추가**를 선택합니다.  **Intune**을 선택합니다.

   ![커넥터 탭의 Intune 옵션이 포함된 Lookout 콘솔의 이미지](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. ‘Microsoft Intune’ 창에서 **연결 설정**을 선택하고 **Heartbeat Frequency**(하트비트 빈도)를 지정합니다.  

   ![하트비트 주기가 구성된 연결 설정 탭의 이미지](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. **Enrollment Management**(등록 관리)를 선택하고 **Use the following Azure AD security groups to identify devices that should be enrolled in Lookout for Work**(다음 Azure AD 보안 그룹을 사용하여 Lookout for Work에서 등록할 디바이스 식별)에서 Lookout에서 사용할 Azure AD 그룹의 ‘그룹 이름’을 지정한 다음 **변경 내용 저장**을 선택합니다. 

    ![Intune Connector 등록 페이지의 스크린샷](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **사용하는 그룹에 관한 내용**:
   - 모범 사례로 Lookout 통합을 테스트하는 작은 수의 사용자를 포함하는 Azure AD 보안 그룹으로 시작합니다.
   - Azure Portal에서 보안 그룹의 **속성**에 나와 있는 것처럼 **그룹 이름**은 대/소문자가 구분됩니다.  
   - **Enrollment Management**(등록 관리)에 지정하는 그룹에 따라 Lookout에 디바이스가 등록되는 사용자 세트가 정의됩니다. 사용자가 등록 그룹에 속해 있으면 Azure AD의 사용자 디바이스가 등록되며 Lookout MES에서 활성화될 수 있습니다. 사용자가 지원되는 디바이스에서 ‘Lookout for Work’ 애플리케이션을 처음으로 열면 활성화하라는 메시지가 표시됩니다. 

4. **State Sync**(상태 동기화)를 선택하고 디바이스 상태  와 ‘위협 상태’가 모두 **켬**으로 설정되어 있는지 확인합니다.   Lookout Intune 통합이 제대로 작동하려면 둘 다 필요합니다.  

5. **Error Management**(오류 관리)를 선택하고 오류 보고서를 받을 메일 주소를 지정한 다음 **변경 내용 저장**을 선택합니다.
 
   ![Intune Connector 오류 관리 페이지의 스크린샷](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. **커넥터 만들기**를 선택하여 커넥터 구성을 완료합니다. 결과에 만족한 경우 나중에 등록을 추가 사용자 그룹으로 확장할 수 있습니다.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Lookout을 Mobile Threat Defense 공급자로 사용하도록 Intune 구성
Lookout MES를 구성한 후에 Intune에서 Lookout의 연결을 설정해야 합니다.  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.

2. **디바이스 준수** > **Mobile Threat Defense**로 이동하고 **추가**를 선택합니다.

3. ‘커넥터 추가’ 창에서 드롭다운 목록을 사용하여 **Lookout for Work**를 선택합니다.   

4. **만들기**를 선택합니다. 커넥터에서 Lookout MES와의 연결이 설정되면 ‘커넥터 설정’을 사용할 수 있습니다. 

5. **iOS 디바이스에 대해 앱 동기화 사용**을 **켬**으로 설정합니다. 

6. **저장**을 선택하여 구성을 완료합니다.  Intune과 Lookout MES가 이제 통합되고 사용할 준비가 됩니다.


## <a name="additional-settings-in-the-lookout-mes-console"></a>MES Lookout 콘솔의 추가 설정
다음은 MES Lookout 콘솔에서 구성할 수 있는 추가 설정입니다.  

### <a name="configure-enrollment-settings"></a>등록 설정 구성
Lookout MES 콘솔에서 **시스템** > **Manage Enrollment**(등록 관리) > **등록 설정**을 선택합니다.  

- **Disconnected Status**(연결이 끊긴 상태)에 연결이 끊긴 디바이스를 연결 끊김으로 표시하기 전의 일 수를 지정합니다.  

  연결이 끊긴 디바이스는 Intune 조건부 액세스 정책을 기반으로 규정 비준수로 간주되어 회사 애플리케이션 액세스가 차단됩니다. 1일에서 90일 사이의 값을 지정할 수 있습니다.

  ![시스템 모듈의 Lookout 등록 설정](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>메일 알림 구성
위협 경고를 메일로 받으려면 알림을 받아야 하는 사용자 계정으로 [Lookout MES 콘솔](https://aad.lookout.com)에 로그인합니다.  

- **기본 설정**으로 이동한 다음 받으려는 알림을 **켬**으로 설정한 다음 변경 내용을 **저장**합니다.  

- 메일 알림을 더 이상 받지 않으려면 알림을 **끔**으로 설정하고 변경 내용을 저장합니다.

  ![사용자 계정이 표시된 기본 설정 페이지의 스크린샷](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>위협 분류 구성  
Lookout Mobile Endpoint Security는 다양한 종류의 모바일 위협을 분류합니다. Lookout 위협 분류에는 기본 위험 수준이 연결되어 있습니다. 위협 수준은 언제든지 회사 요구 사항에 맞게 변경할 수 있습니다.

위협 수준 분류에 관한 자세한 내용과 연결된 위협 수준을 관리하는 방법은 [Lookout 위협 참조](https://enterprise.support.lookout.com/hc/articles/360011812974)를 참조하세요.

>[!IMPORTANT]
> 위험 수준은 런타임 시 이러한 위험 수준에 따라 Intune 통합에서 디바이스 규정 준수를 측정하기 때문에 Mobile Endpoint Security의 중요한 측면입니다.  
> 
> Intune 관리자가 디바이스에 최소 수준의 활성 위협(**높음**, **중간** 또는 **낮음**)이 있다면 디바이스가 규정을 준수하지 않는 것으로 식별하도록 정책 규칙을 설정할 수 있습니다. Lookout Mobile Endpoint Security의 위협 분류 정책을 통해 디바이스의 규정 준수 여부가 Intune에서 바로 측정됩니다.  

## <a name="monitor-enrollment"></a>등록 모니터링
설정이 완료되면 Lookout Mobile Endpoint Security에서 지정한 등록 그룹에 해당하는 디바이스를 Azure AD에 폴링하기 시작합니다.  Lookout MES 콘솔에서 **디바이스**로 이동하여 등록된 디바이스에 관한 정보를 확인할 수 있습니다.  
- 디바이스의 초기 상태는 ‘보류 중’입니다.   
- 디바이스에서 ‘Lookout for Work’ 앱을 설치하고 열고 활성화하면 디바이스 상태가 업데이트됩니다. 

‘Lookout for Work’ 앱을 디바이스에 배포하는 방법에 대한 자세한 내용은 [Intune을 사용하여 Lookout for Work 앱 추가](mtd-apps-ios-app-configuration-policy-add-assign.md)를 참조하세요. 

## <a name="next-steps"></a>다음 단계

[Lookout 앱 설정](mtd-apps-ios-app-configuration-policy-add-assign.md)
