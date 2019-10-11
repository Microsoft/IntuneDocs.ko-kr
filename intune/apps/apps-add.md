---
title: Microsoft Intune에 앱 추가
titleSuffix: ''
description: 사용자 및 디바이스에 앱을 할당할 수 있도록 앱을 Microsoft Intune에 추가하는 방법을 알아봅니다. Intune은 다양한 앱 유형을 지원합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40bb96000513bb1de09ec8f8865735d70bddcd43
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725220"
---
# <a name="add-apps-to-microsoft-intune"></a>Microsoft Intune에 앱 추가 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

앱을 할당, 모니터링, 구성 또는 보호하려면 앱을 Microsoft Intune에 추가해야 합니다.

회사의 앱 및 디바이스 사용자(회사의 직원)에게 여러 가지 앱 요구 사항이 있을 수도 있습니다. Intune에 앱을 추가하고 직원이 사용할 수 있기 전에 앱의 몇 가지 기본 항목을 평가하고 이해해야 합니다. Intune에서 사용할 수 있는 다양한 앱 유형을 이해해야 합니다. 직원에게 필요한 플랫폼 및 기능과 같은 앱 요구 사항을 평가해야 합니다. Intune을 사용하여 디바이스(앱 포함)를 관리할지, 아니면 intune에서 디바이스를 관리하지 않고 앱을 관리할지 결정해야 합니다. 최종적으로, 직원에게 필요한 앱 및 기능과 필요한 사람을 결정해야 합니다. 이 문서의 정보는 시작하는 데 도움이 됩니다.

## <a name="app-types-in-microsoft-intune"></a>Microsoft Intune의 앱 형식

Intune은 다양한 앱 유형을 지원합니다. 사용 가능한 옵션은 앱 유형마다 다릅니다. Intune을 사용하여 다음 앱 유형을 추가하고 할당할 수 있습니다.

| 앱 유형 | 설치 | 업데이트 |
|---|---|---|
| 저장소의 앱(스토어 앱) | Intune이 디바이스에 앱을 설치합니다.  | 앱이 자동으로 업데이트됩니다. |
| 사내에서 작성한 앱(기간 업무) | Intune이 디바이스에 앱을 설치합니다(관리자가 설치 파일 제공). | 관리자가 앱을 업데이트해야 합니다. |
| 기본 제공된 앱(기본 제공 앱) | Intune이 디바이스에 앱을 설치합니다.  | 앱이 자동으로 업데이트됩니다. |
| 웹의 앱(웹 링크) | Intune이 디바이스 홈 화면에 웹앱의 바로 가기를 만듭니다. | 앱이 자동으로 업데이트됩니다. |

### <a name="specific-app-type-details"></a>특정 앱 형식 세부 정보
 
다음 표에는 특정 앱 유형과 Intune **앱 추가** 창에서 추가하는 방법이 나와 있습니다.

| **앱 특정 유형** | **일반 유형** | **앱 특정 절차** |
| --- | --- | --- |
| Android 스토어 앱  | 스토어 앱  | **앱 유형**으로 **Android**를 선택하고 앱의 Google Play 스토어 URL을 입력합니다. |
| Android Enterprise 앱  | 스토어 앱  | **앱 유형**으로 **Android**를 선택하고 앱의 관리되는 Google Play 스토어 URL을 입력합니다. <sup>1</sup> |
| iOS 스토어 앱  | 스토어 앱  | **앱 유형**으로 **iOS**를 선택하고 앱을 검색한 다음 Intune에서 앱을 선택합니다. |
| Windows Phone 8.1 스토어 앱  | 스토어 앱  | **앱 유형**으로 **Windows Phone 8.1**을 선택하고 앱의 Microsoft Store URL을 입력합니다. |
| Microsoft Store 앱  | 스토어 앱  | **앱 유형**으로 **Windows**를 선택하고 앱의 Microsoft Store URL을 입력합니다. |
| 관리되는 Google Play 앱 | 스토어 앱  | **관리되는 Google Play**를 **앱 유형**으로 선택하고 앱을 검색한 후 Intune에서 앱을 선택합니다. |
| Windows 10용 Office 365 앱  | 스토어 앱(Office 365) | **앱 유형**으로 **Office 365 제품군** 아래의 **Windows 10**을 선택한 다음 설치할 Office 365 앱을 선택합니다.  |
| macOS용 Office 365 앱 | 스토어 앱(Office 365) | **앱 유형**으로 **Office 365 제품군** 아래의 **macOS**를 선택한 다음 Office 365 앱 제품군을 선택합니다. |
| Android LOB(기간 업무) 앱 | LOB 앱 | **앱 유형**으로 **기간 업무** 앱을 선택하고 **앱 패키지 파일**을 선택한 다음 확장명이 **.apk**인 Android 설치 파일을 입력합니다.  |
| iOS LOB 앱 | LOB 앱 | **앱 유형**으로 **기간 업무** 앱을 선택하고 **앱 패키지 파일**을 선택한 다음 확장명이 **.ipa**인 iOS 설치 파일을 입력합니다.  |
| Windows Phone LOB 앱 | LOB 앱 | **앱 유형**으로 **LOB(기간 업무)** 앱을 선택하고 **앱 패키지 파일**을 선택한 다음, 확장명이 **.xap**인 Windows Phone 설치 파일을 입력합니다.  |
| Windows LOB 앱 | LOB 앱 | 앱 유형으로 **사업 부문** 앱을 선택하고 **앱 패키지 파일**을 선택한 다음, 확장명이 **.msi**, **.appx**, **.appxbundle**, **.msix** 및 **.msixbundle**인 Windows 설치 파일을 입력합니다. |
| 기본 제공 iOS 앱  | 기본 제공 앱 | **앱 유형**으로 **기본 제공 앱**을 선택한 다음, 제공된 앱 목록에서 기본 제공 앱을 선택합니다.  |
| 기본 제공 Android 앱  | 기본 제공 앱 | **앱 유형**으로 **기본 제공 앱**을 선택한 다음, 제공된 앱 목록에서 기본 제공 앱을 선택합니다.  |
| 웹앱  | 웹앱  | **앱 유형**으로 **웹 링크**를 선택하고 웹앱을 가리키는 유효한 URL을 입력합니다.  |
| Android Enterprise 시스템 앱  | 스토어 앱  | **Android Enterprise 시스템 앱**을 **앱 유형**으로 선택한 다음 앱 이름, 게시자, 패키지 파일을 입력합니다.  |
| Windows 앱(Win32)  | LOB 앱  | **앱 유형**으로 **Windows 앱(Win32)** 을 선택하고 **앱 패키지 파일**을 선택한 다음, 확장명이 **.intunewin**인 설치 파일을 선택합니다.  |
| macOS LOB 앱 | LOB 앱  | **앱 유형**으로 **기간 업무**를 선택하고 **앱 패키지 파일**을 선택한 다음 확장명이 **.intunemac**인 설치 파일을 선택합니다.  |


<sup>1</sup> Android Enterprise 및 Android 회사 프로필에 대한 자세한 내용은 아래의 [사용이 허가된 앱 이해](apps-add.md#understanding-licensed-apps)를 참조하세요.

Microsoft Intune에서 **클라이언트 앱** > **앱** > **추가**를 차례로 선택하여 앱을 추가할 수 있습니다. **앱 추가** 창이 표시되고 **앱 유형**을 선택할 수 있습니다. 

>[!TIP]
> LOB 앱은 앱 설치 파일에서 추가하는 앱입니다. 예를 들어 iOS LOB 앱을 설치하려면 **앱 추가** 창에서 **앱 유형**으로 **기간 업무 앱**을 선택하여 애플리케이션을 추가합니다. 그런 다음, 앱 패키지 파일(확장명 .ipa)을 선택합니다. 이러한 유형의 앱은 일반적으로 사내에서 작성됩니다.

## <a name="assess-app-requirements"></a>앱 요구 사항 평가
IT 관리자는 그룹에서 사용해야 하는 앱뿐 아니라 각 그룹과 하위 그룹에 필요한 기능도 결정합니다. 각 앱에 대해 필요한 플랫폼, 앱이 필요한 사용자 그룹, 해당 그룹에 적용할 구성 정책, 적용할 보호 정책을 결정합니다.  

또한 MDM(모바일 디바이스 관리)에 집중할지, 아니면 MAM(모바일 애플리케이션 관리)에만 집중할지 결정해야 합니다. 

Intune을 사용하여 MDM으로 디바이스를 관리하면 다음과 같은 경우에 유용합니다.
- 사용자가 생산성 유지를 위해 Wi-Fi 또는 VPN 회사 연결 프로필이 필요한 경우.
- 사용자가 자신의 디바이스에 앱 집합을 푸시해야 하는 경우.
- 조직이 보안이나 암호화 같은 특정 MDM 컨트롤을 호출하는 규정 또는 기타 정책을 준수해야 하는 경우.

Intune을 사용하여 디바이스를 관리하지 않고 MAM으로 앱을 관리하면 다음과 같은 경우에 유용합니다.
- 사용자에게 BYOD를 허용하려는 경우.
- 사용자에게 MAM 보호가 작동하고 있다는 사실을 지속적인 디바이스 수준 알림이 아닌 일회성 팝업 메시지를 통해 알리려는 경우.
- 개인 디바이스에서 필요한 관리 기능이 더 적은 정책을 준수하려는 경우. 예를 들어 디바이스 전체에 대한 회사 데이터를 관리하는 대신 앱에 대한 회사 데이터를 관리할 수 있습니다.

자세한 내용은 [MDM 및 MAM 비교](../fundamentals/byod-technology-decisions.md)를 참조하세요.

### <a name="determine-who-will-use-the-app"></a>앱을 사용할 사람 결정

직원에게 필요한 앱을 결정할 때 다양한 사용자 그룹과 사용되는 다양한 앱을 고려하세요. 이러한 그룹을 알고 있으면 앱을 추가한 후에도 도움이 됩니다. 앱을 추가한 후 해당 앱을 사용할 수 있는 사용자 그룹을 할당합니다. 

먼저 앱에 포함된 데이터의 중요도에 따라 앱에 액세스할 수 있는 그룹을 결정해야 합니다. 조직 내의 특정 역할 유형을 포함하거나 제외해야 할 수도 있습니다. 예를 들어 영업 그룹은 특정 LOB 앱만 필요한 반면 엔지니어링, 재무, HR 또는 법무 관련 직원들은 LOB 앱을 사용할 필요가 없을 수 있습니다. 또한 영업 그룹은 모바일 디바이스에서 내부 회사 서비스에 액세스할 수 있는 권한과 추가 데이터 보호 기능이 필요할 수 있습니다. 이 그룹이 앱을 사용하여 리소스에 연결하는 방식을 결정해야 합니다. 앱이 액세스하는 데이터가 클라우드에 있나요, 아니면 온-프레미스에 있나요? 또한 사용자가 앱을 사용하여 어떻게 리소스에 연결하나요? 

또한 Intune에서는 사업 부문 앱 서버와 같은 온-프레미스 데이터에 대한 보안 액세스가 필요한 클라이언트 앱에 대한 액세스를 지원합니다. 이러한 유형의 액세스는 일반적으로 경계에 있는 표준 VPN 게이트웨이 또는 프록시(예: Azure Active Directory 애플리케이션 프록시)와 더불어 액세스 제어에 [Intune 관리 인증서](../protect/certificates-configure.md)를 사용하여 제공됩니다. Intune [앱 래핑 도구 및 앱 SDK](../developer/apps-prepare-mobile-application-management.md)를 사용하면 소비자 앱 또는 서비스에 회사 데이터를 전달할 수 없도록 액세스한 데이터를 기간 업무 앱에 포함할 수 있습니다.

[Intune 배포 계획, 설계 및 구현 가이드](../fundamentals/planning-guide.md)를 사용하여 각 사용 사례 및 하위 사용 사례 앱 시나리오와 연결된 조직 그룹을 식별하는 방법을 확인하세요. 그룹에 앱을 할당하는 방법에 대한 자세한 내용은 [Microsoft intune을 사용하여 그룹에 앱 할당](apps-deploy.md)을 참조하세요.

### <a name="determine-the-type-of-app-for-your-solution"></a>솔루션에 사용할 앱 유형 결정

다음 앱 유형 중에서 선택할 수 있습니다.
- **스토어의 앱**: Microsoft Store, iOS 스토어 또는 Android 스토어에 업로드된 앱은 스토어 앱입니다. 스토어 앱의 공급자가 앱 업데이트를 유지 관리하고 제공합니다. 스토어 목록에서 앱을 선택하고, Intune을 통해 사용자가 사용할 수 있는 앱으로 추가합니다.
- **사내에서 작성한 앱(기간 업무)** : 사내에서 만든 앱은 LOB(기간 업무) 앱입니다. 이러한 유형의 앱 기능은 Windows, iOS, macOS 또는 Android 등 Intune에서 지원하는 플랫폼 중 하나에서 사용할 수 있도록 개발되었습니다. 조직에서 업데이트를 별도 파일로 만들어서 관리자에게 제공합니다. 관리자는 Intune으로 업데이트를 추가 및 배포하여 사용자에게 앱 업데이트를 제공합니다.
- **웹의 앱**: 웹앱은 클라이언트-서버 애플리케이션입니다. 서버는 UI, 콘텐츠 및 기능을 포함하는 웹앱을 제공합니다. 또한 플랫폼을 호스팅하는 현대식 웹은 일반적으로 보안, 부하 분산 및 기타 이점을 제공합니다. 이 앱 유형은 웹에서 별도로 유지 관리됩니다. Intune을 사용하여 이 앱 유형을 가리킵니다. 앱에 액세스할 수 있는 사용자 그룹도 할당합니다. Android는 웹앱을 지원하지 않습니다.

조직에 필요한 앱을 결정하는 경우 앱이 클라우드 서비스와 통합되는 방식, 앱이 액세스하는 데이터, BYOD 사용자가 앱을 사용할 수 있는지 여부, 앱에 인터넷 액세스가 필요한지 여부를 고려하세요.

조직에 필요한 앱 유형에 대한 자세한 내용은 [디자인 만들기](../fundamentals/planning-guide-design.md#feature-requirements)의 “기능 요구 사항” 섹션에서 “앱” 섹션을 참조하세요.

### <a name="understanding-app-management-and-protection-policies"></a>앱 관리 및 보호 정책 이해
앱이 회사의 규정 준수 및 보안 정책을 따르도록 Intune을 사용하여 배포하는 앱의 기능을 수정할 수 있습니다. 이를 통해 회사 데이터를 보호하는 방식을 결정할 수 있습니다. Intune 관리 앱은 다음과 같은 풍부한 모바일 애플리케이션 보호 정책을 지원합니다.

- 복사하여 붙여넣기 및 다른 이름으로 저장 기능 제한
- Intune Managed Browser 앱 내에서 열리도록 웹 링크 구성
- 다중 ID 사용 및 앱 수준 조건부 액세스 사용

Intune 관리 앱은 등록 없이 앱 보호를 사용할 수도 있으므로 사용자 디바이스를 관리하지 않고도 데이터 손실 방지 정책을 적용할 수 있습니다. 또한 Intune 앱 SDK와 앱 래핑 도구를 사용하여 모바일 및 기간 업무 앱에 회사 모바일 앱 관리를 통합할 수 있습니다. 이러한 도구에 대한 자세한 내용은 [Intune 앱 SDK 개요](../developer/app-sdk.md)를 참조하세요.

### <a name="understanding-licensed-apps"></a>라이선스 앱 이해
웹앱, 스토어 앱, LOB 앱을 이해하는 것은 물론 다음과 같은 대량 구매 프로그램 앱과 사용이 허가된 앱의 대상도 알고 있어야 합니다. 
- **비즈니스용 Apple 대량 구매 프로그램(iOS)** : iOS App Store에서는 회사에서 실행하려는 앱의 라이선스를 여러 개 구매할 수 있습니다. 여러 복사본을 구매하면 회사에서 앱을 효율적으로 관리할 수 있습니다. 자세한 내용은 [iOS 대량 구매 앱 관리](vpp-apps-ios.md)를 참조하세요.
- **Android 회사 프로필**: Android 회사 프로필 디바이스에 앱을 할당하는 방법은 표준 Android 디바이스에 앱을 할당하는 방법과 다릅니다. Android 회사 프로필에 대해 설치하는 모든 앱은 Google Play 스토어에서 제공됩니다. Intune을 사용하여 원하는 앱을 찾아 승인합니다. 그러면 Azure Portal의 **사용이 허가된 앱** 노드에 앱이 표시되며, 다른 앱과 마찬가지로 앱의 할당을 관리할 수 있습니다.
- **비즈니스용 Microsoft Store(Windows 10)** : 비즈니스용 Microsoft Store에서는 조직에서 사용하는 앱을 하나씩 또는 대량으로 찾아 구매할 수 있습니다. 스토어를 Microsoft Intune에 연결하면 Azure Portal에서 대량 구매 앱을 관리할 수 있습니다. 자세한 내용은 [비즈니스용 Microsoft 스토어에서 앱 관리](windows-store-for-business.md)를 참조하세요.

    > [!NOTE]
    > Windows 앱의 파일 확장명에는 **.msi**, **.appx**, **.appxbundle**, **.msix** 및 **.msixbundle**이 포함됩니다.  

## <a name="before-you-add-apps"></a>앱을 추가하기 전에
앱을 추가하고 할당하기 전에 다음 사항을 고려하세요.

- 스토어에서 앱을 추가하고 할당하는 경우 해당 스토어에 사용자 계정이 있어야 앱을 설치할 수 있습니다.
- 할당한 앱 또는 항목 중 일부는 기본 제공 iOS 앱에 종속될 수 있습니다. 예를 들어 iOS 스토어에서 책을 할당하는 경우 iBooks 앱이 디바이스에 있어야 합니다. iBooks 기본 제공 앱을 제거한 경우에는 Intune을 사용하여 복구할 수 없습니다.

> [!IMPORTANT]
> 앱을 배포하고 설치한 뒤에 Intune Azure Portal에서 앱의 이름을 변경하면 더 이상 명령을 사용하여 앱을 대상으로 지정할 수 없습니다.

## <a name="cloud-storage-space"></a>클라우드 스토리지 공간
소프트웨어 설치 관리자 설치 유형(예: 기간 업무 앱)을 사용하여 만든 모든 앱은 패키징된 후 Intune 클라우드 스토리지로 업로드됩니다. Intune의 평가판 구독에는 관리 앱 및 업데이트를 저장하는 데 사용되는 클라우드 기반의 2GB 스토리지가 포함됩니다. 전체 구독에서는 총 스토리지 공간 크기에 제한이 없습니다.

클라우드 스토리지 공간에 대한 요구 사항은 다음과 같습니다.

- 모든 앱 설치 파일이 같은 폴더 내에 있어야 합니다.
- 업로드하는 파일의 최대 크기는 8GB입니다.

  > [!NOTE]
  > Windows LOB(기간 업무) 앱의 최대 크기 한도는 앱당 8GB입니다. iOS LOB 앱의 최대 크기 한도는 앱당 4GB입니다.

## <a name="create-and-edit-categories-for-apps"></a>앱의 범주 만들기 및 편집

앱 범주를 사용하여 사용자가 회사 포털에서 보다 쉽게 찾을 수 있도록 앱을 정렬할 수 있습니다. 하나 이상의 범주(예: *개발자 앱*, 또는 *통신 앱*)를 앱에 할당할 수 있습니다.

Intune에 앱을 추가하는 경우 원하는 범주를 선택할 수 있는 옵션이 제공됩니다. 플랫폼 관련 항목을 사용하여 앱을 추가하고 범주를 할당합니다. 사용자 고유의 범주를 만들고 편집하려면 다음 절차를 사용합니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드 창의 **설정** 아래에서 **앱 범주**를 선택합니다.  
    **앱 범주** 창에 현재 범주 목록이 표시됩니다. 
5. 다음 중 하나를 수행합니다.
    - 범주를 추가하려면 **범주 만들기** 창에서 **추가**를 선택하고 범주 이름을 입력합니다.  
    이름은 하나의 언어로만 입력할 수 있으며, Intune에서 번역되지 않습니다.
    - 범주를 편집하려면 범주 옆에 있는 줄임표( **...** )를 선택한 다음 **대시보드에 고정** 또는 **삭제**를 선택합니다.
6. **만들기**를 선택합니다.

## <a name="apps-that-are-added-automatically-by-intune"></a>Intune에서 자동으로 추가된 앱

이전에는 Intune에 신속하게 할당할 수 있는 많은 기본 제공 앱이 포함되어 있었습니다. Intune 고객 피드백에 따라 이 목록은 제거되었으며, 기본 제공 앱이 더 이상 표시되지 않습니다. 그러나 기본 제공 앱을 이미 할당한 경우 해당 앱은 앱 목록에 계속 표시됩니다. 필요에 따라 앱을 계속 할당할 수 있습니다.

> [!NOTE]
> 필요한 비기간 업무 앱을 설치하기 위해 Intune에서는 앱이 검색되지 않고 앱의 설치 상태가 *설치 보류 중*이 아닌 경우 디바이스에서 체크 인할 때마다 설치 명령을 보내서 앱을 설치하려고 합니다.

## <a name="installing-updating-or-removing-required-apps"></a>필수 앱 설치, 업데이트 또는 제거

Intune은 7일 재평가 주기를 기다리지 않고 24시간 이내에 필수 앱을 자동으로 재설치, 업데이트 또는 제거합니다.

Intune은 다음 조건에 따라 필수 앱을 자동으로 재설치, 업데이트 또는 제거합니다.
- 최종 사용자의 디바이스에 반드시 설치하도록 지정한 앱을 최종 사용자가 제거할 경우 Intune은 이 일정이 경과하면 자동으로 해당 앱을 다시 설치합니다.
- 필수 앱 설치가 실패하거나 앱이 디바이스에 없는 경우 Intune은 이 일정이 경과하면 규정 준수를 평가하고 앱을 다시 설치합니다.  
- 관리자는 사용자 그룹에 사용할 수 있는 앱을 대상으로 하고 최종 사용자는 회사 포털의 앱을 디바이스에 설치합니다. 나중에 관리자가 앱을 v1에서 v2로 업데이트합니다. 여전히 이전 버전 앱이 디바이스에 남이 있는 경우 Intune은 이 일정이 경과하면 앱을 업데이트합니다.
- 관리자가 제거 의도를 배포하고, 앱이 디바이스에 있고, 제거에 실패할 경우 Intune은 이 일정이 경과하면 규정 준수를 평가하고 앱을 제거합니다.   

## <a name="app-installation-errors"></a>앱 설치 오류

Intune 앱 설치 오류에 대한 자세한 내용은 [앱 설치 오류](troubleshoot-app-install.md#app-installation-errors)를 참조하세요.

## <a name="next-steps"></a>다음 단계

각 플랫폼용 앱을 Intune에 추가하는 방법에 대한 자세한 내용은 다음을 참조하세요.

- [Android 스토어 앱](store-apps-android.md)
- [Android LOB 앱](lob-apps-android.md)
- [iOS 스토어 앱](store-apps-ios.md)
- [iOS LOB 앱](lob-apps-ios.md)
- [macOS LOB 앱](lob-apps-macos.md)
- [웹앱(모든 플랫폼)](web-app.md)
- [Windows Phone 8.1 스토어 앱](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB 앱](lob-apps-windows-phone.md)
- [Microsoft Store 앱](store-apps-windows.md)
- [Windows LOB 앱](lob-apps-windows.md)
- [Windows 10용 Office 365 앱](apps-add-office365.md)
- [macOS용 Office 365 앱](apps-add-office365-macos.md)
- [기본 제공 앱](apps-add-built-in.md)
- [Android Enterprise 시스템 앱](apps-ae-system.md)
- [Win32 앱](app-management.md)
