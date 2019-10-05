---
title: iOS 교실 앱에 대한 Intune 공유 디바이스 설정
titleSuffix: Microsoft Intune
description: iOS 디바이스에서 교실 앱에 대한 설정을 제어하는 데 사용할 수 있는 Intune 설정을 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a3129ee1590ba183ce60f6e4f1ad1318dd49e96
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735924"
---
# <a name="configure-intune-education-settings-for-shared-ipad-devices"></a>공유 iPad 디바이스에 대한 Intune 교육 설정 구성

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

> [!NOTE]
> Intune 앱에 대한 Intune 설정은 Intune에서 더 이상 사용되지 않습니다. 이 문서는 Intune에서 기존 교육 프로필이 있는 사용자에게만 적용할 수 있습니다.

Intune에서는 교사들이 학습을 지도하고 교실에서 학생 디바이스를 제어하는 데 도움이 되는 iOS 교실 앱을 지원합니다. 또한 Apple은 여러 학생이 단일 디바이스를 공유할 수 있도록 교실 앱에서 학생 iPad 디바이스를 구성할 수 있는 기능을 지원합니다. 이 문서에서는 Intune으로 이러한 작업을 수행하는 과정을 안내합니다.

교실 앱을 사용할 전용(1:1) iPad 디바이스를 구성하는 방법에 대한 자세한 내용은 [iOS 교실 앱에 대한 Intune 설정을 구성하는 방법](education-settings-configure-ios.md)을 참조하세요.

## <a name="before-you-start"></a>시작하기 전에

공유 iPad 기능을 사용하기 위한 필수 조건은 다음과 같습니다.

- [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md) 및 [SDS(학교 데이터 동기화)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617)를 설정합니다.
- Apple School Manager 설치 과정에서 학생에 대해 [관리되는 Apple ID](http://help.apple.com/schoolmanager/#/tes78b477c81)를 구성합니다. [관리되는 Apple ID에 대해 자세히 알아봅니다](https://support.apple.com/HT205918).
- Apple School Manager에서 동기화된 디바이스 일련 번호에 대한 등록 프로필을 만듭니다.

## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>1단계 - Azure Active Directory로 학교 데이터 가져오기

Microsoft SDS(학교 데이터 동기화)를 사용하여 기존 SIS(학교 정보 시스템)에서 Azure AD(Azure Active Directory)로 학교 레코드를 가져옵니다.
SDS는 SIS의 정보를 동기화하고 Azure AD에 저장합니다. Azure AD는 사용자 및 디바이스를 구성하도록 도와주는 Microsoft 관리 시스템입니다. 이 데이터를 사용하여 학생 및 수업을 관리할 수 있습니다. [SDS를 배포하는 방법에 대해 알아보세요](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>SDS를 사용하여 데이터를 가져오는 방법

다음 방법 중 하나를 사용하여 정보를 SDS로 가져올 수 있습니다.

- [CSV 파일](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) - 쉼표로 구분된 값(.csv) 파일을 수동으로 내보내고 컴파일합니다.
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) - Azure AD와의 동기화를 간소화하는 SIS 공급자입니다.
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) - Azure AD와 동기화하도록 내보내고 변환할 수 있는 CSV 형식입니다.

### <a name="find-out-more"></a>자세한 정보

- [Azure Active Directory와 온-프레미스 디렉터리 통합](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [Find out more about Microsoft School Data Sync](https://sds.microsoft.com/)(Microsoft 학교 데이터 동기화에 대해 자세히 알아보기)
- [Azure Active Directory에서 그룹 기반 라이선스 기본](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)


## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>2단계 - Intune에서 iOS 교육 프로필 만들기 및 할당

### <a name="configure-general-settings"></a>일반 설정 구성

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **디바이스 구성**을 선택합니다.
2. **관리** 섹션 아래의 **디바이스 구성** 창에서 **프로필**을 선택합니다.
5. 프로필 창에서 **프로필 만들기**를 선택합니다.
6. **프로필 만들기** 창에서 iOS 교육 프로필에 대한 **이름** 및 **설명**을 입력합니다.
7. **플랫폼** 드롭다운 목록에서 **iOS**를 선택합니다.
8. **프로필** 유형 드롭다운 목록에서 선택 **교육**을 선택합니다.
9. **설정** > **구성**을 선택합니다.

그 다음에 교사 및 학생 iPad 간에 트러스트 관계를 설정하려면 인증서가 필요합니다. 인증서는 사용자 이름 및 암호를 입력할 필요 없이 디바이스 간 연결을 원활하게 자동으로 인증하는 데 사용됩니다.

>[!Important]
>사용할 교사 및 학생 인증서는 서로 다른 CA(인증 기관)에서 발급되어야 합니다. 기존 인증서 인프라에 연결된 두 개의 새 하위 CA를 교사 및 학생에 대해 하나씩 만들어야 합니다.

iOS 교육 프로필은 PFX 인증서만 지원하고 SCEP 인증서는 지원되지 않습니다.

만들려는 인증서는 사용자 인증 외에 서버 인증을 지원해야 합니다.

### <a name="configure-teacher-certificates"></a>교사 인증서 구성

**교육** 창에서 **교사 인증서**를 선택합니다.

#### <a name="configure-teacher-root-certificate"></a>교사 루트 인증서 구성

**교사 루트 인증서**에서 [찾아보기] 단추를 선택하여 확장명이 .cer(DER 또는 Base64로 인코딩됨) 또는 .P7B(전체 체인 포함 또는 제외)인 교사 루트 인증서를 선택합니다.

#### <a name="configure-teacher-pkcs12-certificate"></a>교사 PKCS#12 인증서 구성

**교사 PKCS#12 인증서**에서 다음 값을 구성합니다.

- **주체 이름 형식** - Intune에서 인증서 일반 이름에 **leader**(교사 인증서) 및 **member**(학생 인증서)가 접두사로 추가됩니다.
- **인증 기관**: Windows Server 2008 R2 이상의 Enterprise Edition에서 실행되는 엔터프라이즈 CA(인증 기관)입니다. 독립 실행형 CA는 지원되지 않습니다.
- **인증 기관 이름** - 인증 기관의 이름을 입력합니다.
- **인증서 템플릿 이름** - 발급 CA에 추가된 인증서 템플릿의 이름을 입력합니다.
- **갱신 임계값(%)** - 디바이스에서 인증서 갱신을 요청하기 전까지 남은 인증서 수명을 백분율로 지정합니다.
- **인증서 유효 기간** - 인증서가 만료되기 전까지 남은 시간을 지정합니다. 지정된 인증서 템플릿에서 유효 기간보다 작은 값은 지정할 수 있지만 높은 값은 지정할 수 없습니다. 예를 들어 인증서 템플릿의 인증서 유효 기간이 2년이면 값을 1년으로 지정할 수는 있어도 5년으로는 지정할 수 없습니다. 또한 이 값은 발급 CA 인증서의 남은 유효 기간보다 작아야 합니다.

교사 인증서 구성을 마치면 **확인**을 선택합니다.

### <a name="configure-student-certificates"></a>학생 인증서 구성

1. **교육** 창에서 **학생 인증서**를 선택합니다.
2. **학생 인증서** 창의 **학생 디바이스 인증서 유형** 목록에서 **공유 iPad**를 선택합니다.

#### <a name="configure-student-root-certificate"></a>학생 루트 인증서 구성

**디바이스 루트 인증서**에서 찾아보기 단추를 선택하여 확장명이 .cer(DER 또는 Base64로 인코딩됨) 또는 .P7B(전체 체인 포함 또는 제외)인 학생 루트 인증서를 선택합니다.

#### <a name="configure-device-pkcs12-certificate"></a>디바이스 PKCS#12 인증서 구성

**학생 PKCS#12 인증서**에서 다음 값을 구성합니다.

- **주체 이름 형식** - Intune에서 인증서 일반 이름에 leader(교사 인증서) 및 member(학생 인증서)가 접두사로 자동으로 추가됩니다.
- **인증 기관**: Windows Server 2008 R2 이상의 Enterprise Edition에서 실행되는 엔터프라이즈 CA(인증 기관)입니다. 독립 실행형 CA는 지원되지 않습니다.
- **인증 기관 이름** - 인증 기관의 이름을 입력합니다.
- **인증서 템플릿 이름** - 발급 CA에 추가된 인증서 템플릿의 이름을 입력합니다.
- **갱신 임계값(%)** - 디바이스에서 인증서 갱신을 요청하기 전까지 남은 인증서 수명을 백분율로 지정합니다.
- **인증서 유효 기간** - 인증서가 만료되기 전까지 남은 시간을 지정합니다. 지정된 인증서 템플릿에서 유효 기간보다 작은 값은 지정할 수 있지만 높은 값은 지정할 수 없습니다. 예를 들어 인증서 템플릿의 인증서 유효 기간이 2년이면 값을 1년으로 지정할 수는 있어도 5년으로는 지정할 수 없습니다. 또한 이 값은 발급 CA 인증서의 남은 유효 기간보다 작아야 합니다.

인증서 구성을 마치면 **확인**을 선택합니다.

### <a name="complete-certificate-setup"></a>인증서 설치 완료

1. **교육** 창에서 **확인**을 선택합니다.
2. **프로필 만들기** 창에서 **만들기**를 선택합니다.

프로필이 만들어지고 프로필 목록 창에 표시됩니다.

## <a name="step-3---create-a-device-category"></a>3단계 - 디바이스 범주 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **디바이스 등록**을 선택합니다.
4. **디바이스 등록 - 개요** 창에서 **디바이스 범주**를 선택합니다.
5. **등록 - 디바이스 범주** 창에서 **만들기**를 선택합니다.
6. **디바이스 범주 만들기** 창에서 범주에 대한 **이름** 및 **설명**을 입력합니다.
7. **디바이스 범주 만들기** 창에서 **만들기**를 선택합니다.

**등록 – 디바이스 범주** 창에 디바이스 범주가 생성됩니다.

## <a name="step-4--create-a-dynamic-group"></a>4단계 - 동적 그룹 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **그룹**을 선택합니다.
4. **사용자 및 그룹 - 모든 그룹** 창에서 **새 그룹**을 선택합니다.
5. **그룹** 창에서 **그룹 유형**을 선택한 다음, 그룹의 **이름**과 **설명**을 입력합니다.
6. **멤버 자격 유형** 드롭다운 목록에서 **동적 디바이스**를 선택합니다.
7. **동적 디바이스 멤버**를 선택하여 멤버 관리 규칙을 만듭니다.
8. **동적 멤버 관리 규칙** 창에서 다음을 수행합니다.
1. **디바이스 추가** 드롭다운 목록에서 **deviceCategory**를 선택합니다.
2. **같음**을 선택합니다.
3. 직접 만든 디바이스 범주를 빈 텍스트 상자에 입력합니다.
9. **동적 멤버 관리 규칙** 창에서 **쿼리 추가**를 선택합니다.
10. **그룹** 창에서 **만들기**를 선택합니다.

**사용자 및 그룹 - 모든 그룹** 창에 동적 그룹이 생성됩니다.

## <a name="step-5--assign-a-device-to-a-category-carts"></a>5단계 - 범주에 디바이스 할당(장바구니)

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **디바이스**를 선택합니다.
4. **디바이스** 창에서 **모든 디바이스**를 선택합니다.
5. **디바이스 - 모든 디바이스** 창에서 디바이스를 선택합니다.
6. 디바이스 창에서 **속성**을 선택합니다.
7. 디바이스 속성 창의 **디바이스 범주** 텍스트 상자에 디바이스 범주를 입력합니다.
8. 디바이스 창에서 **저장**을 선택합니다.

이제 디바이스가 디바이스 범주에 연결됩니다. 직접 만든 디바이스 범주에 연결하려는 모든 디바이스에 대해 이 프로세스를 반복합니다.

## <a name="step-6--create-classroom-profiles"></a>6단계 – 교실 프로필 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **디바이스 구성**을 선택합니다.
4. **디바이스 구성** 창에서 **관리** > **카트 프로필**을 선택합니다.
5. 프로필 창에서 **프로필 만들기**를 선택합니다.
6. **연결 만들기** 창에서 **이름** 및 **설명**을 입력합니다.
7. **클래스 선택** > **구성**을 선택하여 그룹을 카트 프로필에 연결합니다.
8. 카트 프로필에 포함할 클래스를 선택한 다음 **선택**을 선택합니다. 
9. **카트 선택** > **구성**을 선택하여 그룹을 카트 프로필에 연결합니다.
10. 카트 프로필에 포함할 그룹을 선택한 다음 **선택**을 선택합니다.
11. **연결 만들기** 창에서 **저장**을 선택하여 카트 프로필을 저장합니다.

프로필이 만들어지고 프로필 목록 창에 표시됩니다.

## <a name="step-7---assign-the-cart-profile-to-classes"></a>7단계 - 클래스에 카트 프로필 할당

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **디바이스 구성**을 선택합니다.
4. **디바이스 구성** 창에서 **모니터** > **할당 상태**를 선택합니다.
5. **할당 상태** 창에서 직접 만든 **카트 프로필**을 선택합니다.
6. **카트 프로필** 창에서 **할당**을 선택한 다음, **포함**에서 **포함할 그룹 선택**을 선택합니다.
7. 카트 프로필의 대상으로 지정할 클래스(그룹을 선택하지 않음)를 선택한 다음 **선택**을 선택합니다. 
8. 작업이 끝나면 **저장**을 선택합니다.

할당이 완료되고, Intune에서 교실 할당에 따라 대상 디바이스에 교실 프로필을 배포합니다.

## <a name="next-steps"></a>다음 단계

이제 학생들이 서로 디바이스를 공유할 수 있으며, 학생이 교실의 모든 iPad를 선택하고 PIN으로 로그인한 다음 해당 콘텐츠로 개인 설정되도록 할 수 있습니다. 공유 iPad에 대한 자세한 내용은 [Apple 웹 사이트](https://www.apple.com/education/it/)를 참조하세요.
