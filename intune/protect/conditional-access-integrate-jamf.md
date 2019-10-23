---
title: 준수를 위해 Microsoft Intune과 Jamf Pro 통합
titleSuffix: Microsoft Intune
description: Jamf 관리 디바이스를 통합 및 보호하려면 Azure Active Directory의 조건부 액세스와 함께 Microsoft Intune 준수 정책을 사용합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a75b1403e351981d1f6ab827d4c10648430b21fb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504603"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>준수를 위해 Intune과 Jamf Pro 통합

적용 대상: Azure Portal의 Intune

조직에서 [Jamf Pro](https://www.jamf.com)를 사용하여 macOS 디바이스를 관리하는 경우 Azure Active Directory(Azure AD) 조건부 액세스 권한이 있는 Microsoft Intune 준수 정책을 사용하여 조직의 디바이스가 규정을 준수하게 하면 디바이스가 회사 리소스에 액세스할 수 있습니다. 이 문서는 Jamf와 Intune 간 통합을 구성하는 데 도움이 됩니다.

Jamf Pro를 Intune과 통합하면 Azure AD를 통해 macOS 디바이스의 인벤토리 데이터를 Intune과 동기화할 수 있습니다. 그런 다음 Intune의 규정 준수 엔진은 인벤토리 데이터를 분석하여 보고서를 생성합니다. Intune의 분석은 디바이스 사용자의 Azure AD ID에 대한 인텔리전스와 결합되어 조건부 액세스를 통한 적용을 촉진합니다. 조건부 액세스 정책을 준수하는 디바이스는 보호된 회사 리소스에 대한 액세스 권한을 얻을 수 있습니다.

통합을 구성한 후에는 Jamf에서 관리하는 디바이스에서 [조건부 액세스 준수를 적용하도록 Jamf 및 Intune을 구성](conditional-access-assign-jamf.md)합니다.  


## <a name="prerequisites"></a>전제 조건

### <a name="products-and-services"></a>제품 및 서비스
Jamf Pro를 사용하여 조건부 액세스를 구성하려면 다음이 필요합니다.

- Jamf Pro 10.1.0 이상
- [macOS용 회사 포털 앱](https://aka.ms/macoscompanyportal)
- OS X 10.11 Yosemite 이상의 macOS 디바이스

### <a name="network-ports"></a>네트워크 포트
<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
Jamf 및 Intune이 올바르게 통합되려면 다음 포트에 액세스할 수 있어야 합니다. 
- **Intune**: 포트 443
- **Apple**: 포트 2195, 2196 및 5223(Intune에 푸시 알림)
- **Jamf**: 포트 80 및 5223

APNS가 네트워크에서 올바르게 작동하게 하려면 다음으로 나가는 연결과 다음으로부터의 리디렉션을 사용해야 합니다.
- 모든 클라이언트 네트워크의 TCP 포트 5223 및 443을 통한 Apple 17.0.0.0/8 블록.   
- Jamf Pro 서버의 2195 및 2196 포트.  

이 포트에 대한 자세한 내용은 다음 문서를 참조하세요.  
- [Intune 네트워크 구성 요구 사항 및 대역폭](../fundamentals/network-bandwidth-use.md).
- Jamf.com의 [Jamf Pro에서 사용하는 네트워크 포트](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro).
- support.apple.com의 [Apple 소프트웨어 제품에서 사용하는 TCP 및 UDP 포트](https://support.apple.com/HT202944)


## <a name="connect-intune-to-jamf-pro"></a>Intune을 Jamf Pro에 연결

Intune을 Jamf Pro에 연결하려면 다음을 수행합니다.

1. Azure에서 새 애플리케이션을 만듭니다.
2. Intune을 Jamf Pro와 통합할 수 있도록 설정합니다.
3. Jamf Pro에서 조건부 액세스를 구성합니다.

## <a name="create-an-application-in-azure-active-directory"></a>Azure Active Directory에서 애플리케이션 만들기

1. [Azure Portal](https://portal.azure.com)에서 **Azure Active Directory** > **앱 등록**으로 이동한 후 **새 등록**을 선택합니다. 

2. **애플리케이션 등록** 페이지에서 다음 세부 정보를 지정합니다.
   - **이름** 섹션에서 의미 있는 애플리케이션 이름을 입력합니다(예: **Jamf 조건부 액세스**).
   - **지원되는 계정 유형** 섹션에서 **모든 조직 디렉터리의 계정**을 선택합니다. 
   - **리디렉션 URI**에서 기본값인 웹을 그대로 사용한 후 Jamf Pro 인스턴스의 URL을 지정합니다.  

3. **등록**을 선택하여 애플리케이션을 만들고 새 앱의 **개요** 페이지를 엽니다.  

4. 앱 **개요** 페이지에서 **애플리케이션(클라이언트) ID** 값을 복사하고 나중에 사용할 수 있도록 기록합니다. 나중 절차에서 이 값이 필요합니다.  

5. **관리** 아래에서 **인증서 및 비밀**을 선택합니다. **새 클라이언트 암호** 단추를 선택합니다. **설명**에 값을 입력하고, **만료** 옵션을 선택하고, **추가**를 선택합니다.

   > [!IMPORTANT]  
   > 이 페이지를 나가기 전에 클라이언트 암호 값을 복사하고 나중에 사용할 수 있도록 기록합니다. 나중 절차에서 이 값이 필요합니다. 앱 등록을 다시 만들지 않으면 이 값을 다시 사용할 수 없습니다.  

6. **관리**에서 **API 사용 권한**을 선택합니다. 기존 권한을 선택한 후 **권한 제거**를 선택하여 해당 권한을 삭제합니다. 새 권한을 추가하고, 애플리케이션은 단일 필수 권한이 있는 경우에만 작동하므로 기존 권한을 모두 제거해야 합니다.  

7. 새 권한을 할당하려면 **권한 추가**를 선택합니다. **API 사용 권한 요청** 페이지에서 **Intune**을 선택한 후 **애플리케이션 권한**을 선택합니다. **update_device_attributes** 확인란만 선택합니다.  

   **권한 추가**를 선택하여 이 구성을 저장합니다.  

8. **API 사용 권한** 페이지에서 ***\<테넌트>*에 대한 관리자 동의 허용**을 선택한 후 **예**를 선택합니다.  앱이 성공적으로 등록되면 API 사용 권한이 다음과 같이 표시됩니다. ![성공적인 사용 권한](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   Azure AD에서 앱 등록 프로세스가 완료되었습니다.


    > [!NOTE]
    > 클라이언트 암호가 만료되면 Azure에서 새 클라이언트 암호를 만든 후 Jamf Pro에서 조건부 액세스 데이터를 업데이트해야 합니다. Azure를 사용하면 서비스 중단을 방지하기 위해 이전 비밀과 새 비밀을 모두 활성화할 수 있습니다.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Intune을 Jamf Pro와 통합할 수 있도록 설정

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **Microsoft Intune** > **디바이스 준수** > **파트너 디바이스 관리**로 이동합니다.

2. 이전 절차 중 저장한 애플리케이션 ID를 **Jamf Azure Active Directory 앱 ID** 필드에 붙여넣어 Jamf용 준수 커넥터를 사용하도록 설정합니다.

3. **저장**을 선택합니다.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Jamf Pro에서 Microsoft Intune 통합 구성

1. Jamf Pro에서 **전역 관리** > **조건부 액세스**로 이동합니다. **macOS Intune 통합** 탭에서 **편집** 단추를 클릭합니다.

2. **macOS용 Intune 통합 사용** 확인란을 선택합니다.

3. Azure AD에서 앱을 만들 때 저장한 **위치**, **도메인 이름** 및 **애플리케이션 ID** 및 *클라이언트 암호*를 포함하여 Azure 테넌트에 대한 필수 정보를 제공합니다.  

4. **저장**을 선택합니다. Jamf Pro가 설정을 테스트하고 성공을 확인합니다.

## <a name="set-up-compliance-policies-and-register-devices"></a>준수 정책 설정 및 디바이스 등록

Intune과 Jamf 사이의 통합을 구성한 후에는 [규정 준수 정책을 Jamf에서 관리되는 디바이스에 적용](conditional-access-assign-jamf.md)해야 합니다.


## <a name="disconnect-jamf-pro-and-intune"></a>Jamf Pro와 Intune 연결 끊기 

조직에서 Jamf Pro로 Mac을 관리하고 싶지 않으며 사용자를 Intune으로 관리하게 하려면, Jamf Pro와 Intune의 연결을 끊어야 합니다. Jamf Pro 콘솔을 사용하여 연결을 제거하세요. 

1. Jamf Pro에서 **전역 관리** > **조건부 액세스**로 이동합니다. **macOS Intune 통합** 탭에서 **편집**을 선택합니다.
2. **macOS용 Intune 통합 사용** 확인란을 선택 취소합니다.
3. **저장**을 선택합니다. Jamf Pro가 Intune에 구성을 보내고 통합이 종료됩니다.
4. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다. **Microsoft Intune** > **디바이스 준수** > **파트너 디바이스 관리**로 이동해 상태가 **종료됨**으로 변경되었는지 확인합니다. 

   > [!NOTE]
   > 조직의 Mac 디바이스는 콘솔에 표시되는 날짜(3개월)에 제거됩니다. 

## <a name="next-steps"></a>다음 단계

- [준수 정책을 Jamf에서 관리되는 디바이스에 적용](conditional-access-assign-jamf.md)
- [Intune에 보내는 데이터 Jamf](data-jamf-sends-to-intune.md)
