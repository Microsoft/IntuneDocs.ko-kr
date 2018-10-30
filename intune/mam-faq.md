---
title: MAM 및 앱 보호에 대한 질문과 대답
description: 이 문서에서는 Intune MAM(모바일 응용 프로그램 관리) 및 Intune 앱 보호에 대한 일부 질문과 대답을 제공합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f27baf7d40a6eb4d89769eeab7a6e035e3468825
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2018
ms.locfileid: "49643028"
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>MAM 및 앱 보호에 대한 질문과 대답

이 문서에서는 Intune MAM(모바일 응용 프로그램 관리) 및 Intune 앱 보호에 대한 일부 질문과 대답을 제공합니다.

## <a name="mam-basics"></a>MAM 기본 사항


**MAM이란?**<br></br>
[Intune MAM(모바일 응용 프로그램 관리)](/intune/app-lifecycle)은 사용자를 위해 모바일 앱을 게시, 푸시, 구성, 보호, 모니터링 및 업데이트할 수 있는 Intune 관리 기능 제품군을 나타냅니다.

**MAM 앱 보호의 이점은 무엇인가요?**<br></br>
MAM은 응용 프로그램 내에서 조직의 데이터를 보호합니다. 중요한 데이터를 포함하는 회사 또는 학교 관련 앱인 MAM-WE(등록 없는 MAM)는 BYOD(Bring-your-own-device) 시나리오의 개인 장치를 비롯한 거의 모든 장치에서 관리할 수 있습니다. Microsoft Office 앱과 같은 많은 생산성 앱은 Intune MAM에서 관리할 수 있습니다. 공개적으로 사용 가능한 공식적인 [Intune 관리 앱](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) 목록을 참조하세요.

**MAM은 어떤 장치 구성을 지원하나요?**<br></br>
Intune MAM은 다음과 같은 두 가지 구성을 지원합니다.
- **Intune MDM + MAM**: IT 관리자는 Intune MDM(모바일 장치 관리)에 등록된 장치에서 MAM 및 앱 보호 정책을 사용하여 앱을 관리할 수만 있습니다. MDM + MAM을 사용하여 앱을 관리하려면 Azure Portal(https://portal.azure.com)에서 Intune 콘솔을 사용해야 합니다.

- **장치를 등록하지 않은 MAM**: 장치를 등록하지 않은 MAM 또는 MAM-WE를 통해 IT 관리자는 Intune MDM에 등록되지 않은 장치에서 MAM 및 앱 보호 정책을 사용하여 앱을 관리할 수 있습니다. 즉, 타사 EMM 공급자에 등록된 장치의 Intune으로 앱을 관리할 수 있습니다. MAM-WE를 사용하여 앱을 관리하려면 Azure Portal(http://portal.azure.com)에서 Intune 콘솔을 사용해야 합니다. 또한 타사 EMM(Enterprise Mobility Management) 공급자에 등록되었거나 MDM에 등록되지 않은 장치에서 Intune를 통해 앱을 관리할 수 있습니다.


## <a name="app-protection-policies"></a>앱 보호 정책

**앱 보호 정책이란?**<br></br>
앱 보호 정책은 관리되는 앱에서 조직의 데이터를 안전하게 보호하거나 유지되도록 하는 규칙입니다. 정책은 사용자가 "회사" 데이터를 액세스하거나 이동하려고 할 때 적용되는 규칙이거나, 사용자가 앱 내에 있을 때 금지되거나 모니터링되는 일련의 작업일 수 있습니다.

**앱 보호 정책의 예는 무엇인가요?**<br></br>
각 앱 보호 정책 설정에 대한 자세한 내용은 [Android 앱 보호 정책 설정](app-protection-policy-settings-android.md) 및 [iOS 앱 보호 정책 설정](app-protection-policy-settings-ios.md)을 참조하세요.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>앱 보호 정책으로 관리할 수 있는 앱

**앱 보호 정책에서 관리될 수 있는 앱은 어느 것인가요?**<br></br>
[Intune 앱 SDK](/intune/app-sdk)와 통합되었거나 [Intune 앱 래핑 도구](/intune/apps-prepare-mobile-application-management)로 래핑된 모든 앱은 Intune 앱 보호 정책을 사용하여 관리할 수 있습니다. 공개적으로 사용 가능한 공식적인 [Intune 관리 앱](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) 목록을 참조하세요.

**Intune 관리 앱에 대해 앱 보호 정책을 사용하기 위한 기본 요구 사항은 무엇인가요?**

- 최종 사용자에게 AAD(Azure Active Directory) 계정이 있어야 합니다. Azure Active Directory에서 Intune 사용자를 만드는 방법을 알아보려면 [Intune에 사용자 추가 및 관리 권한 부여](/intune/users-permissions-add)를 참조하세요.

- 최종 사용자의 Azure Active Directory 계정에 Microsoft Intune 라이선스가 할당되어 있어야 합니다. 최종 사용자에게 Intune 라이선스를 할당하는 방법을 알아보려면 [Intune 라이선스 관리](/intune/licenses-assign)를 참조하세요.

- 최종 사용자가 앱 보호 정책의 대상으로 지정된 보안 그룹에 속해야 합니다. 동일한 앱 보호 정책은 사용 중인 특정 앱을 대상으로 해야 합니다. [Azure Portal](http://portal.azure.com)의 Intune 콘솔에서 앱 보호 정책을 만들고 배포할 수 있습니다. 보안 그룹은 현재 [Office 포털](http://portal.office.com)에서 만들 수 있습니다.

- 최종 사용자가 자신의 AAD 계정을 사용하여 앱에 로그인해야 합니다.

**[Outlook 모바일 앱](https://products.office.com/outlook) 사용에 대한 추가 요구 사항은 무엇인가요?**

- 최종 사용자의 장치에 Outlook 모바일 앱이 설치되어 있어야 합니다.

- 최종 사용자의 Azure Active Directory 계정에 [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) 사서함 및 라이선스가 연결되어 있어야 합니다.

  >[!NOTE]
  > Outlook 모바일 앱은 현재 Microsoft Exchange Online용 만 Intune App Protection 및 [하이브리드 최신 인증을 사용하는 Exchange Server](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)만 지원하며 Office 365 전용 Exchange는 지원하지 않습니다.

**[Word, Excel 및 PowerPoint](https://products.office.com/business/office) 앱 사용을 위한 추가 요구 사항은 무엇인가요?**

- 최종 사용자의 Azure Active Directory 계정에 [Office 365 Business 또는 Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) 라이선스가 연결되어 있어야 합니다. 구독에는 모바일 장치의 Office 앱이 포함되어야 하며 [비즈니스용 OneDrive](https://onedrive.live.com/about/business/)의 클라우드 저장소 계정을 포함할 수 있습니다. 다음 [지침](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)에 따라 [Office 포털](http://portal.office.com)에서 Office 365 라이선스를 할당받을 수 있습니다.

- 최종 사용자에게 “다른 이름으로 저장 금지” 응용 프로그램 보호 정책 설정에서 세분화된 다른 이름으로 저장 기능을 사용하여 구성된 관리 위치가 있어야 합니다. 예를 들어 관리 위치가 OneDrive인 경우 최종 사용자의 Word, Excel 또는 PowerPoint 앱에 [OneDrive](https://onedrive.live.com/about/) 앱이 구성되어 있어야 합니다.

- 관리 위치가 OneDrive인 경우 해당 앱이 최종 사용자에게 배포된 앱 보호 정책의 대상으로 지정되어야 합니다.

  >[!NOTE]
  > Office 모바일 앱은 현재 SharePoint Online만 지원하고 SharePoint 온-프레미스는 지원하지 않습니다.

**Office에 관리 위치(예: OneDrive)가 필요한 이유는 무엇인가요?**<br></br>
Intune에서는 앱의 모든 데이터를 "회사" 또는 "개인" 데이터로 표시합니다. 데이터는 비즈니스 위치에서 시작될 경우 "회사" 데이터로 간주됩니다. Office 앱의 경우 Intune은 전자 메일(Exchange) 또는 클라우드 저장소(비즈니스용 OneDrive 계정이 있는 OneDrive 앱)를 비즈니스 위치로 간주합니다.

**비즈니스용 Skype 사용에 대한 추가 요구 사항은 무엇인가요?**<br></br>
[비즈니스용 Skype](https://products.office.com/skype-for-business/it-pros) 라이선스 요구 사항을 참조하세요. SfB(비즈니스용 Skype) 하이브리드 및 온-프레미스 구성에 대해서는 [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756)(SfB 및 Exchange의 하이브리드 최신 인증이 GA(일반 공급) 상태가 됨) 및 [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910)(AAD를 사용한 SfB 온-프레미스의 최신 인증)를 각각 참조하세요.

## <a name="app-protection-features"></a>앱 보호 기능

**다중 ID 지원이란?**<br></br>
다중 ID 지원은 Intune 앱 SDK가 앱에 로그인한 회사 또는 학교 계정에만 앱 보호 정책을 적용하도록 하는 기능입니다. 개인 계정으로 앱에 로그인하면 이 데이터는 그대로 유지됩니다.

**다중 ID 지원의 용도는 무엇인가요?**<br></br>
다중 ID 지원을 사용하면 “회사” 및 소비자 대상 그룹이 둘 다 있는 앱(예: Office 앱)을 “회사” 계정에 대한 Intune 앱 보호 기능을 통해 공개적으로 릴리스할 수 있습니다.

**Outlook 및 다중 ID의 경우는 어떤가요?**<br></br>
Outlook에는 개인 및 "회사" 전자 메일이 결합된 전자 메일 보기가 제공되므로 Outlook 앱은 시작 시 Intune PIN을 요구합니다.

**Intune 앱 PIN이란?**<br></br>
PIN(개인 식별 번호)은 올바른 사용자가 응용 프로그램에서 조직의 데이터에 액세스하는지 확인하는 데 사용하는 암호입니다.

- **사용자가 PIN을 입력해야 하는 경우는 언제인가요?**<br></br> 사용자가 “회사” 데이터에 액세스하려고 하면 Intune에서 사용자의 앱 PIN을 묻는 메시지가 표시됩니다. Word/Excel/PowerPoint와 같은 다중 ID 앱에서는 사용자가 "회사" 문서나 파일을 열려고 할 때 PIN이 필요합니다. Intune 앱 래핑 도구를 사용하여 관리되는 기간 업무 앱 등의 단일 ID 앱에서는 Intune 앱 SDK에서 앱의 사용자 환경이 항상 “회사”라는 사실을 알고 있기 때문에 시작 시 PIN을 묻는 메시지가 표시됩니다.

- **Intune PIN을 입력하라는 메시지는 얼마나 자주 나타납니까?**<br></br> IT 관리자는 Intune 관리 콘솔에서 Intune 앱 보호 정책 설정인 '다음 시간(분) 후에 액세스 요구 사항 다시 확인'을 정의할 수 있습니다. 이 설정은 장치에서 액세스 요구 사항을 확인하고 응용 프로그램 PIN 화면이 다시 표시되기까지의 시간을 지정합니다. 그러나 사용자에게 표시되는 빈도에 영향을 미치는 PIN에 대한 중요한 세부 정보는 다음과 같습니다. 

    - **PIN은 사용 가능성을 향상시키기 위해 동일한 게시자의 앱 간에서 공유됩니다.** iOS의 경우 **동일한 앱 게시자의** 모든 앱 간에서 하나의 앱 PIN이 공유됩니다. Android의 경우 하나의 앱 PIN이 모든 앱 간에서 공유됩니다.
    - **장치를 재부팅한 후 '다음 시간(분) 후에 액세스 요구 사항 다시 확인' 동작:** "PIN 타이머"는 다음에 Intune 앱 PIN을 표시할 시기를 결정하는 비활성 시간(분)을 추적합니다. iOS에서 PIN 타이머는 장치 재부팅에 영향을 받지 않습니다. 따라서 장치 다시 시작은 Intune PIN 정책을 사용하는 iOS 앱에서 사용자가 비활성화된 시간(분)에 영향을 주지 않습니다. Android에서는 PIN 타이머가 장치 재부팅 시 다시 설정됩니다. 따라서 Intune PIN 정책을 사용하는 Android 앱은 **장치 재부팅 후** ‘다음 시간(분) 후에 액세스 요구 사항 다시 확인’ 설정 값에 상관없이 앱 PIN을 묻는 메시지를 표시합니다.  
    - **PIN과 관련된 타이머의 롤링 특성:** 앱(앱 A)에 액세스하기 위해 PIN을 입력하고 앱이 장치에서 포그라운드(기본 입력 포커스)를 나가면, PIN 타이머가 해당 PIN을 재설정합니다. 이 PIN을 공유하는 어떠한 앱(앱 B)도 타이머가 재설정되었기 때문에 사용자에게 PIN 입력을 요구하지는 않습니다. '다음 시간(분) 후에 액세스 요구 사항 다시 확인' 값이 다시 충족되면 메시지가 다시 나타납니다.

iOS 장치의 경우 PIN이 다른 게시자의 앱 간에 공유되는 경우에도 **다음 시간(분) 후에 액세스 요구 사항 다시 확인** 값이 주 입력 포커스가 아닌 앱에 다시 충족할 때 프롬프트가 다시 표시됩니다. 따라서 예를 들어 사용자에게 게시자 _X_의 앱 _A_와 게시자 _Y_의 앱 _B_가 있는 경우 이러한 두 앱은 동일한 PIN을 공유합니다. 사용자는 앱 _A_(전경)에 중점을 두고, 앱 _B_는 최소화됩니다. **다음 시간(분) 후에 액세스 요구 사항 다시 확인** 값이 충족되고 사용자가 앱 _B_로 전환한 후 PIN이 필요합니다.

  >[!NOTE] 
  > 특히 자주 사용하는 앱의 경우 사용자의 액세스 요구 사항을 보다 자주 확인하려면(즉, PIN 프롬프트) ‘다음 시간(분) 후에 액세스 요구 사항 다시 확인’ 설정 값을 줄이는 것이 좋습니다. 
      
- **Intune PIN이 Outlook 및 OneDrive용 기본 제공 앱 PIN으로 작동하는 방법은?**<br></br>
Intune PIN은 비활성 타이머(즉, '다음 시간(분) 후에 액세스 요구 사항 다시 확인' 값)를 기반으로 작동합니다. 따라서 Intune PIN 프롬프트는 기본적으로 앱 실행과 연결된 경우가 많은 Outlook 및 OneDrive용 기본 제공 앱 PIN 프롬프트와 별도로 표시됩니다. 사용자가 두 PIN 프롬프트를 동시에 받는 경우 Intune PIN이 우선적으로 표시되어야 합니다. 

- **PIN은 안전한가요?**<br></br> PIN을 사용하면 올바른 사용자만 앱에서 조직의 데이터에 액세스할 수 있습니다. 따라서 최종 사용자는 해당 Intune 앱 PIN을 설정하거나 다시 설정하기 전에 회사 또는 학교 계정으로 로그인해야 합니다. 이 인증은 보안 토큰 교환을 통해 Azure Active Directory에 의해 처리되며 Intune 앱 SDK에 투명하게 공개되지 않습니다. 보안의 관점에서 회사 또는 학교 데이터를 보호하는 가장 좋은 방법은 암호화하는 것입니다. 암호화는 앱 PIN과 관련이 없으며 고유한 앱 보호 정책입니다.

- **Intune은 어떤 방식으로 무차별 암호 대입 공격(brute force attack)으로부터 PIN을 보호하나요?**<br></br> 앱 PIN 정책의 일환으로, IT 관리자는 앱을 잠그기 전에 사용자가 PIN 인증을 시도할 수 있는 최대 횟수를 설정할 수 있습니다. 이 횟수가 충족되면 Intune 앱 SDK는 앱에서 "회사" 데이터를 초기화할 수 있습니다.
  
- **동일한 게시자의 앱에서 PIN을 두 번 설정해야 하는 이유는 무엇인가요?**<br></br> MAM(iOS)은 현재 영숫자 및 특수 문자를 사용하는 응용 프로그램 수준 PIN을 허용합니다. 이 경우 iOS용 Intune 앱 SDK를 통합하려면 응용 프로그램(예: WXP, Outlook, Managed Browser, Yammer)이 참가해야 합니다. 이렇게 하지 않으면 대상 응용 프로그램에 암호 설정이 제대로 적용되지 않습니다. 이는 iOS용 Intune SDK 버전 7.1.12에서 출시된 기능입니다. <br><br> 이 기능을 지원하고 이전 버전의 iOS용 Intune SDK와 호환성을 보장하기 위해 7.1.12 이상의 모든 PIN(숫자 또는 암호)은 이전 SDK 버전의 숫자 PIN과 별도로 처리됩니다. 따라서 동일한 게시자의 iOS용 Intune SDK 7.1.12 이전 버전과 7.1.12 이상 버전을 사용하는 응용 프로그램이 장치에 있는 경우 두 개의 PIN을 설정해야 합니다. <br><br> 즉, 두 개의 PIN(각 앱용)은 어떤 방식으로든 서로 관련이 없으며 앱에 적용되는 앱 보호 정책을 준수해야 합니다. 따라서 PIN과 관련해서 앱 A와 B에 동일한 정책이 적용되는 *경우에만* 사용자가 동일한 PIN을 두 번 설정할 수 있습니다. <br><br> 이 동작은 Intune 모바일 앱 관리에서 사용하도록 설정된 iOS 응용 프로그램의 PIN과 관련이 있습니다. 시간이 지나 응용 프로그램이 최신 버전의 iOS용 Intune SDK를 채택하면서 동일한 게시자의 앱에서 PIN을 두 번 설정해야 하는 문제는 완화됩니다. 예를 보려면 아래 참고를 참조하세요.

  >[!NOTE]
  > 예를 들어 앱 A는 7.1.12 이전 버전으로 빌드되고 앱 B는 동일한 게시자의 7.1.12 이상 버전으로 빌드된 경우, iOS 장치에 두 앱이 모두 설치되어 있으면 최종 사용자가 A와 B에 대해 별도로 PIN을 설정해야 합니다. <br><br> SDK 버전 7.1.9를 사용하는 앱 C가 장치에 설치되면 앱 A와 동일한 PIN을 공유합니다. <br><br> 7.1.14로 빌드된 앱 D는 앱 B와 동일한 PIN을 공유합니다. <br><br> 앱 A와 C만 장치에 설치된 경우 하나의 PIN만 설정하면 됩니다. 앱 B와 D만 장치에 설치된 경우에도 마찬가지입니다.

**암호화의 경우는 어떤가요?**<br></br>
IT 관리자는 앱 데이터 암호화를 요구하는 앱 보호 정책을 배포할 수 있습니다. 이러한 정책의 일환으로, IT 관리자는 콘텐츠가 암호화되는 경우를 지정할 수도 있습니다.

- **Intune에서는 어떤 방식으로 데이터가 암호화되나요?**<br></br> 암호화 앱 보호 정책 설정에 대한 자세한 내용은 [Android 앱 보호 정책 설정](app-protection-policy-settings-android.md) 및 [iOS 앱 보호 정책 설정](app-protection-policy-settings-ios.md)을 참조하세요.

- **암호화되는 대상은 무엇인가요?**<br></br> IT 관리자의 앱 보호 정책에 따라 "회사"로 표시된 데이터만 암호화됩니다. 데이터는 비즈니스 위치에서 시작될 경우 "회사" 데이터로 간주됩니다. Office 앱의 경우 Intune은 전자 메일(Exchange) 또는 클라우드 저장소(비즈니스용 OneDrive 계정이 있는 OneDrive 앱)를 비즈니스 위치로 간주합니다. Intune 앱 래핑 도구에서 관리되는 기간 업무 앱의 경우 모든 앱 데이터가 “회사” 데이터로 간주됩니다.

**Intune에서는 어떻게 원격으로 데이터를 초기화하나요?**<br></br>
Intune에서는 전체 장치 초기화, MDM에 대한 선택적 초기화 및 MAM 선택적 초기화라는 세 가지 방법으로 앱 데이터를 초기화할 수 있습니다. MDM의 원격 초기화에 대한 자세한 내용은 [초기화 또는 사용 중지를 사용하여 장치 제거](devices-wipe.md)를 참조하세요. MAM을 사용하는 선택적 초기화에 대한 자세한 내용은 [사용 중지 작업](devices-wipe.md#retire) 및 [앱에서 회사 데이터만 초기화하는 방법](apps-selective-wipe.md)을 참조하세요.

- **초기화란?**<br></br> [초기화](devices-wipe.md)는 장치를 출하 시 기본 설정으로 복원하여 **장치**에서 모든 사용자 데이터 및 설정을 제거합니다. 그리고 장치가 Intune에서 제거됩니다.
  >[!NOTE]
  > 초기화는 Intune MDM(모바일 장치 관리)에 등록된 장치에서만 수행할 수 있습니다.

- **MDM에 대한 선택적 초기화란?**<br></br> 회사 데이터를 제거하는 방법에 대한 자세한 내용은 [장치 제거 -사용 중지](devices-wipe.md#retire)를 참조하세요.

- **MAM에 대한 선택적 초기화란?**<br></br> MAM에 대한 선택적 초기화는 단순히 앱에서 업무용 앱 데이터를 제거합니다. 이 요청은 Intune Azure Portal 포털에서 시작됩니다. 초기화 요청을 시작하는 방법을 알아보려면 [앱에서 회사 데이터만 초기화하는 방법](apps-selective-wipe.md)을 참조하세요.

- **MAM에 대한 선택적 초기화는 얼마나 빠르게 수행되나요?**<br></br> 선택적 초기화가 시작된 상태로 앱을 사용하면 Intune 앱 SDK는 Intune MAM 서비스에서 선택적 초기화 요청을 30분 간격으로 확인합니다. 또한 사용자가 앱을 처음 시작하고 회사 또는 학교 계정으로 로그인할 때에도 선택적 초기화를 확인합니다.

**온-프레미스 서비스가 Intune 보호 앱에 작동하지 않는 이유는 무엇인가요?**<br></br>
Intune 앱 보호 기능은 응용 프로그램과 Intune 앱 SDK에서 일관되게 작동하기 위해 사용자의 ID에 의존합니다. 이를 보장하는 유일한 방법은 최신 인증뿐입니다. 앱이 온-프레미스 구성에 작동하는데도 일관되거나 보장되지 않는 시나리오가 있습니다.

**관리되는 앱에서 웹 링크를 안전하게 여는 방법이 있나요?**<br></br>
예. IT 관리자는 Intune을 사용하여 쉽게 관리할 수 있는 Microsoft Intune에서 개발된 웹 브라우저인 [Intune Managed Browser 앱](app-configuration-managed-browser.md)에 대한 앱 보호 정책을 배포 및 설정할 수 있습니다. IT 관리자는 Intune 관리 앱의 모든 웹 링크가 Managed Browser 앱을 사용하여 열리도록 지정할 수 있습니다.

**Intune APP SDK가 MSAL(Microsoft 인증 라이브러리) 또는 소셜 계정을 지원합니까?**
Intune APP SDK는 자사 및 타사의 SDK 버전 모두에 고급 ADAL 기능을 사용합니다. 따라서 MSAL은 Intune 앱 보호 서비스 인증 및 조건부 실행과 같은 여러 핵심 시나리오에서 잘 작동하지 않습니다. 현재 이를 지원할 계획은 없습니다.

## <a name="app-experience-on-android"></a>Android의 앱 환경

**Intune 앱 보호 기능을 Android 장치에서 작동하기 위해 회사 포털 앱이 필요한 이유는 무엇인가요?**<br></br>
많은 앱 보호 기능이 회사 포털 앱에 기본 제공됩니다. 회사 포털 앱이 항상 필요한 경우에도 장치 등록은 _필요하지 않습니다_. MAM-WE의 경우 최종 사용자가 회사 포털 앱을 장치에 설치하기만 하면 됩니다.

**Android에서 앱 및 사용자 작업의 동일한 집합에 구성된 여러 Intune 앱 보호 액세스 설정은 어떻게 합니까?**<br></br>
액세스에 대한 Intune 앱 보호 정책은 최종 사용자 장치가 회사 계정에서 대상 앱에 액세스하려 하기 때문에 해당 장치에 지정된 순서에 따라 적용됩니다. 일반적으로 차단이 우선 적용된 다음, 무시할 수 있는 경고가 적용됩니다. 예를 들어 특정 사용자/앱에 적용되는 경우 사용자의 액세스를 차단하는 최소 Android 패치 버전 설정 적용 후 패치 업그레이드를 적용하도록 사용자에게 경고하는 최소 Android 패치 버전 설정이 적용됩니다. 따라서 IT 관리자가 최소 Android 패치 버전을 2018-03-01로, 최소 Android 패치 버전(경고에서만 해당)을 2018-02-01로 구성하는 반면 앱에 액세스하려는 장치의 패치 버전은 2018-01-01인 시나리오에서 최종 사용자는 결국 액세스 차단을 야기하는 최소 Android 패치 버전에 대한 더 제한적인 설정을 기반으로 차단되게 됩니다. 

다른 두 유형의 설정을 처리할 경우 앱 버전 요구 사항이 우선하고 이어 Android 운영 체제 버전 요구 사항 및 Android 패치 버전 요구 사항이 차례로 처리됩니다. 그런 다음, 동일한 순서로 설정의 모든 형식에 대한 모든 경고를 확인합니다.

## <a name="app-experience-on-ios"></a>iOS의 앱 환경
**장치에 지문 또는 얼굴을 추가하거나 제거하면 어떻게 되나요?**
Intune 앱 보호 정책을 사용하면 Intune의 사용이 허가된 사용자에 대해서만 앱 액세스를 제어할 수 있습니다. 앱에 대한 액세스를 제어하는 한 가지 방법으로, 지원되는 장치에서 Apple의 Touch ID 또는 Face ID를 요구하는 방법이 있습니다. Intune은 장치의 생체 인식 데이터베이스에 변경 사항이 있는 경우 동작을 구현하며, Intune은 다음 비활성 시간 제한 값이 충족될 때 사용자에게 PIN을 요구하는 메시지를 표시합니다. 생체 인식 데이터의 변경 사항에는 지문 또는 얼굴의 추가나 제거가 포함됩니다. Intune 사용자에게 설정한 PIN이 없는 경우 Intune PIN 설정으로 안내됩니다.
 
Intune PIN은 앱 내의 조직 데이터를 앱 수준에서 보호하고 계속 안전하게 유지하기 위한 것입니다. 이 기능은 iOS에만 제공되고 iOS용 Intune 앱 SDK, 버전 9.0.1 이상을 통합하는 응용 프로그램의 참여가 필요합니다. 대상 응용 프로그램에 동작이 적용될 수 있도록 SDK의 통합이 필요합니다. 이 통합은 롤링 기반으로 특정 응용 프로그램 팀에서 수행합니다. 참여하는 일부 앱에는 WXP, Outlook, Managed Browser 및 Yammer가 포함됩니다. 
  
**데이터 전송 정책이 "관리되는 앱만" 또는 "앱 없음"으로 설정된 경우에도 iOS 공유 확장을 사용하여 관리되지 않는 앱에서 회사 또는 학교 데이터를 열 수 있습니다. 데이터가 유출되지는 않나요?**<br></br>
Intune 앱 보호 정책은 장치를 관리하지 않고는 iOS 공유 확장을 제어할 수 없습니다. 따라서 Intune은 _**"회사" 데이터를 앱 외부에서 공유하기 전에 먼저 암호화합니다**_. 관리되는 앱 외부에서 "회사" 파일 열기를 시도하여 이를 확인할 수 있습니다. 파일이 암호화되어야 하며, 관리되는 앱 외부에서 파일을 열 수 없어야 합니다.

**iOS에서 앱 및 사용자 작업의 동일한 집합에 구성된 여러 Intune 앱 보호 액세스 설정은 어떻게 합니까?**<br></br>
액세스에 대한 Intune 앱 보호 정책은 최종 사용자 장치가 회사 계정에서 대상 앱에 액세스하려 하기 때문에 해당 장치에 지정된 순서에 따라 적용됩니다. 일반적으로 초기화가 우선 적용되고, 차단이 적용된 다음, 무시할 수 있는 경고가 적용됩니다. 예를 들어 특정 사용자/앱에 적용되는 경우 사용자의 액세스를 차단하는 최소 iOS 운영 체제 설정 적용 후 iOS 버전을 업그레이드하도록 사용자에게 경고하는 최소 iOS 운영 체제 설정이 적용됩니다. 따라서 IT 관리자가 최소 iOS 운영 체제를 11.0.0.0으로, 최소 iOS 운영 체제(경고에서만 해당)를 11.1.0.0으로 구성하는 반면 앱에 액세스하려는 장치는 iOS 10인 시나리오에서 최종 사용자는 결국 액세스 차단을 야기하는 최소 iOS 운영 체제에 대한 더 제한적인 설정을 기반으로 차단되게 됩니다.

다른 유형의 설정을 처리할 경우 Intune 앱 SDK 버전 요구 사항이 우선하고 이어 앱 버전 요구 사항, iOS 운영 체제 버전 요구 사항이 처리됩니다. 그런 다음, 동일한 순서로 설정의 모든 형식에 대한 모든 경고를 확인합니다. Intune 앱 SDK 버전 요구 사항은 필수 차단 시나리오의 경우 Intune 제품 팀의 안내에 따라 구성하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목
- [Intune 계획 구현](planning-guide-onboarding.md)
- [Intune 테스트 및 유효성 검사](planning-guide-test-validation.md)
- [Microsoft Intune의 Android 모바일 앱 관리 정책 설정](app-protection-policy-settings-android.md)
- [iOS 모바일 앱 관리 정책 설정](app-protection-policy-settings-ios.md)
- [앱 보호 정책 유효성 검사](app-protection-policies-validate.md)
- [장치 등록 없이 관리되는 앱용 앱 구성 정책 추가](app-configuration-policies-managed-app.md)
- [Microsoft Intune에 대한 관리 지원을 받는 방법](get-support.md)
