---
title: iOS 교실 앱에 대한 Intune 설정
titleSuffix: Microsoft Intune
description: iOS 디바이스에서 교실 앱에 대한 설정을 제어하는 데 사용할 수 있는 Intune 설정을 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/9/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: derriw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 578dcf8a714197d9414e8ffeeec9a6c6e8a30311
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "71302170"
---
# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>iOS 교실 앱에 대한 Intune 설정을 구성하는 방법

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> Intune 앱에 대한 Intune 설정은 Intune에서 더 이상 사용되지 않습니다. 이 문서는 Intune에서 기존 교육 프로필이 있는 사용자에게만 적용할 수 있습니다.

## <a name="introduction"></a>소개
[교실](https://itunes.apple.com/app/id1085319084)은 교사들이 교실에서 학습을 지도하고 학생 디바이스를 제어하도록 도와주는 앱입니다. 예를 들어 앱을 통해 교사는 다음을 수행할 수 있습니다.

- 학생 디바이스에서 앱 열기
- iPad 화면 잠금 및 잠금 해제
- 학생 iPad의 화면 보기
- 학생 iPad를 책의 책갈피 또는 장으로 이동
- 학생 iPad의 화면을 Apple TV에 표시

디바이스에서 교실을 설정하려면 Intune iOS 교육 디바이스 프로필을 만들고 구성해야 합니다.

## <a name="before-you-start"></a>시작하기 전에

이러한 설정을 구성하기 전에 다음을 고려하세요.

- 교사 및 학생 iPad가 Intune에 등록되어 있어야 합니다.
- 교사의 디바이스에 [Apple 교실](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) 앱을 설치했는지 확인합니다. 앱을 수동으로 설치하거나 [Intune 앱 관리](app-management.md)를 사용할 수 있습니다.
- 교사 디바이스와 학생 디바이스 간 연결을 인증하도록 인증서를 구성해야 합니다(2단계, Intune에서 iOS 교육 프로필 만들기 및 할당 참조).
- 교사 및 학생 iPad가 같은 Wi-Fi 네트워크에 있고 Bluetooth를 사용할 수 있어야 합니다.
- 교실 앱은 iOS 9.3 이상을 실행하는 감독 모드 iPad에서 실행됩니다.
- 이 릴리스의 Intune에서는 각 학생이 전용 iPad를 보유한 1:1 시나리오 관리를 지원합니다.


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


다음 섹션에서는 교사 및 학생 iPad 간에 트러스트 관계를 설정하기 위한 인증서를 만듭니다. 인증서는 사용자 이름 및 암호를 입력할 필요 없이 디바이스 간 연결을 원활하게 자동으로 인증하는 데 사용됩니다.

>[!IMPORTANT]
>사용할 교사 및 학생 인증서는 서로 다른 CA(인증 기관)에서 발급되어야 합니다. 기존 인증서 인프라에 연결된 두 개의 새 하위 CA를 교사 및 학생에 대해 하나씩 만들어야 합니다.

iOS 교육 프로필은 PFX 인증서만 지원하고 SCEP 인증서는 지원되지 않습니다.

만든 인증서에서 서버 인증과 사용자 인증을 지원해야 합니다.

### <a name="configure-teacher-certificates"></a>교사 인증서 구성

**교육** 창에서 **교사 인증서**를 선택합니다.

#### <a name="configure-teacher-root-certificate"></a>교사 루트 인증서 구성

**교사 루트 인증서**에서 찾아보기 단추를 선택합니다. 다음 조건 중 하나를 충족하는 루트 인증서를 선택합니다.
- 확장명 .cer(DER 또는 Base64로 인코딩됨) 
- 확장명 .P7B(전체 체인 포함 또는 제외)

#### <a name="configure-teacher-pkcs12-certificate"></a>교사 PKCS#12 인증서 구성

**교사 PKCS#12 인증서**에서 다음 값을 구성합니다.

- **주체 이름 형식** - Intune에서 교사 인증서의 일반 이름 앞에 **leader** 접두사를 자동으로 추가합니다. 학생 인증서의 일반 이름 앞에는 **member** 접두사가 추가됩니다.
- **인증 기관**: Windows Server 2008 R2 이상의 Enterprise Edition에서 실행되는 엔터프라이즈 CA(인증 기관)입니다. 독립 실행형 CA는 지원되지 않습니다. 
- **인증 기관 이름** - 인증 기관의 이름을 입력합니다.
- **인증서 템플릿 이름** - 발급 CA에 추가된 인증서 템플릿의 이름을 입력합니다. 
- **갱신 임계값(%)** - 디바이스에서 인증서 갱신을 요청하기 전까지 남은 인증서 수명을 백분율로 지정합니다.
- **인증서 유효 기간** - 인증서가 만료되기 전까지 남은 시간을 지정합니다.
지정된 인증서 템플릿에서 유효 기간보다 작은 값은 지정할 수 있지만 높은 값은 지정할 수 없습니다. 예를 들어 인증서 템플릿의 인증서 유효 기간이 2년이면 값을 1년으로 지정할 수는 있어도 5년으로는 지정할 수 없습니다. 또한 이 값은 발급 CA 인증서의 남은 유효 기간보다 작아야 합니다.

인증서 구성을 마쳤으면 **확인**을 선택합니다.

### <a name="configure-student-certificates"></a>학생 인증서 구성

1. **교육** 창에서 **학생 인증서**를 선택합니다.
2. **학생 인증서** 창의 **학생 디바이스 인증서** 유형 목록에서 **1:1**을 선택합니다.

#### <a name="configure-student-root-certificate"></a>학생 루트 인증서 구성

**학생 루트 인증서**에서 찾아보기 단추를 선택합니다. 다음 조건 중 하나를 충족하는 루트 인증서를 선택합니다.
- 확장명 .cer(DER 또는 Base64로 인코딩됨) 
- 확장명 .P7B(전체 체인 포함 또는 제외)

#### <a name="configure-student-pkcs12-certificate"></a>학생 PKCS#12 인증서 구성

**학생 PKCS#12 인증서**에서 다음 값을 구성합니다.

- **주체 이름 형식** - Intune에서 교사 인증서의 일반 이름 앞에 **leader** 접두사를 자동으로 추가합니다. 학생 인증서의 일반 이름 앞에는 **member** 접두사가 추가됩니다.
- **인증 기관**: Windows Server 2008 R2 이상의 Enterprise Edition에서 실행되는 엔터프라이즈 CA(인증 기관)입니다. 독립 실행형 CA는 지원되지 않습니다. 
- **인증 기관 이름** - 인증 기관의 이름을 입력합니다.
- **인증서 템플릿 이름** - 발급 CA에 추가된 인증서 템플릿의 이름을 입력합니다. 
- **갱신 임계값(%)** - 디바이스에서 인증서 갱신을 요청하기 전까지 남은 인증서 수명을 백분율로 지정합니다.
- **인증서 유효 기간** - 인증서가 만료되기 전까지 남은 시간을 지정합니다.
지정된 인증서 템플릿에서 유효 기간보다 작은 값은 지정할 수 있지만 높은 값은 지정할 수 없습니다. 예를 들어 인증서 템플릿의 인증서 유효 기간이 2년이면 값을 1년으로 지정할 수는 있어도 5년으로는 지정할 수 없습니다. 또한 이 값은 발급 CA 인증서의 남은 유효 기간보다 작아야 합니다.

인증서 구성을 마쳤으면 **확인**을 선택합니다.

## <a name="finish-up"></a>끝내기

1. **교육** 창에서 확인을 선택합니다.
2. **프로필 만들기** 창에서 **만들기**를 선택합니다.

프로필이 만들어지고 프로필 목록 창에 표시됩니다.

학교 데이터를 Azure AD와 동기화할 때 만들어진 교실 그룹의 학생 디바이스에 프로필을 할당합니다([디바이스 프로필을 할당하는 방법](device-profile-assign.md) 참조.

## <a name="next-steps"></a>다음 단계

이제 교사가 교실 앱을 사용할 때 학생 디바이스를 완전히 제어할 수 있습니다.

교실 앱에 대한 자세한 내용은 Apple 웹 사이트에서 [교실 앱 도움말](https://help.apple.com/classroom/ipad/2.0/)을 참조하세요.

학생용 공유 iPad 디바이스를 구성하려면 [공유 iPad 디바이스에 대한 Intune 교육 설정을 구성하는 방법](education-settings-configure-ios-shared.md)을 참조하세요.
