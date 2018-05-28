---
title: 모바일 장치 등록의 전제 조건
description: MDM(모바일 장치 관리) 필수 구성 요소를 설정하고 다른 운영 체제를 등록할 준비를 완료합니다.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 57dfc1bf2765de6c2e02352caca58f3859742fd6
ms.sourcegitcommit: 49dc405bb26270392ac010d4729ec88dfe1b68e4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2018
---
# <a name="prerequisites-for-mobile-device-management-in-intune"></a>Intune에서 모바일 장치 관리를 위한 필수 조건

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

직원이 Intune에 모바일 장치를 등록할 수 있도록 하려면 다음 단계가 필요합니다. 이러한 동일한 단계는 회사 소유 장치를 관리하는 데 필요합니다.

|단계|세부 정보|  
|-----------|-------------|  
|**1단계:** [연결 사용](#step-1-enable-connections)|사용자 지정 도메인 이름이 구성되어 있고 네트워크 통신이 준비되었는지 확인합니다.|  
|**2단계:** [MDM 기관 설정](#step-2-set-mdm-authority)|모바일 장치 관리 기관은 장치에 할당된 서비스를 정의합니다.|
|**3단계:** [그룹 만들기](#step-3-create-groups)|회사 포털 앱과 관련하여 사용자에게 표시되는 설정을 구성합니다.|  
|**4단계:** [회사 포털 구성](#step-4-configure-company-portal)|회사 포털 앱과 관련하여 사용자에게 표시되는 설정을 구성합니다.|  
|**5단계:** [사용자 라이선스 할당](#step-5-assign-user-licenses)|장치를 등록할 수 있도록 사용자에게 Intune 라이선스를 할당합니다.|
|**6단계:** [등록 사용](#step-6-enable-enrollment)|iOS 및 Windows 관리에 대해 플랫폼별 설정을 사용하도록 설정합니다. Android 장치에는 추가 구성이 필요하지 않습니다.|
|**7단계:** [다음 단계](#step-7-next-steps)|iOS 및 Windows 관리에 대해 플랫폼별 설정을 사용하도록 설정합니다. Android 장치에는 추가 구성이 필요하지 않습니다.|

Configuration Manager가 포함된 Intune을 찾고 있나요?
> [!div class="button"]
> [SCCM 문서 보기 >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## <a name="step-1-enable-connections"></a>1단계: 연결 사용

모바일 장치 등록을 사용하도록 설정하기 전에 다음을 수행했는지 확인합니다.
- [필요한 네트워크 URL 및 포트 검토](/intune/network-bandwidth-use)
- [도메인 이름 추가 및 확인](/intune/custom-domain-name-configure)

## <a name="step-2-set-mdm-authority"></a>2단계: MDM 기관 설정
MDM 기관은 일련의 장치를 관리할 권한을 가진 관리 서비스를 정의합니다. MDM 기관에 대한 옵션에는 Intune 자체 및 Intune을 사용하는 Configuration Manager가 포함됩니다. Configuration Manager를 관리 기관으로 설정한 경우 모바일 장치 관리에 다른 서비스를 사용할 수 없습니다.

>[!IMPORTANT]
> Configuration Manager 버전 1610 이상과 Microsoft Intune 버전 1705에서는 Microsoft 지원에 문의하여 기존의 관리 장치를 등록 취소했다가 다시 등록할 필요 없이 MDM 기관을 변경할 수 있습니다. 자세한 내용은 [잘못된 MDM 기관 설정을 선택한 경우 수행할 작업](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)을 참조하세요.

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **관리** &gt; **모바일 장치 관리**를 선택합니다.

2.  **작업** 목록에서 **모바일 장치 관리 기관 설정**을 클릭합니다. **MDM 기관 설정** 대화 상자가 열립니다.

    ![MDM 기관 설정 대화 상자](../media/intune-mdm-authority.png)

3.  Intune을 MDM 기관으로 지정할 것임을 확인하라는 요청 메시지가 표시됩니다. 이 확인란을 선택한 후 **예**를 선택하여 모바일 장치를 관리하는 데 Microsoft Intune을 사용합니다.

## <a name="step-3-create-groups"></a>3단계: 그룹 만들기

사용자 및 장치 그룹을 만들어 관리를 간소화하고 배포된 앱, 정책 및 회사 리소스에 대한 대상 지정 기능을 개선할 수 있습니다. [그룹을 만드는 방법을 알아봅니다](use-groups-to-manage-users-and-devices-with-microsoft-intune.md#create-groups).

## <a name="step-4-configure-company-portal"></a>4단계: 회사 포털 구성

Intune 회사 포털에서 사용자는 회사 데이터에 액세스하고 장치 등록, 앱 설치, IT 부서 지원 정보 찾기 등의 일반적인 작업을 수행할 수 있습니다.

> [!TIP]
> 회사 포털을 사용자 지정할 때는 구성이 회사 포털 웹 사이트 및 회사 포털 앱에 모두 적용됩니다.

회사 포털을 사용자 지정하면 최종 사용자에게 친숙하고 유용한 환경을 제공하는 데 도움이 됩니다. 이렇게 하려면 [Microsoft Intune 관리자 콘솔](https://manage.microsoft.com)에 테넌트 또는 서비스 관리자로 로그인하고, **관리** &gt; **회사 포털**을 선택하여 회사 포털 설정을 구성합니다.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### <a name="company-contact-information-and-privacy-statement"></a>회사 연락처 정보 및 개인정보취급방침

회사 이름은 회사 포털의 제목으로 표시됩니다. 연락처 정보 및 세부 정보는 회사 포털의 IT 담당자 화면에서 사용자에게 표시됩니다. 개인정보취급방침은 사용자가 개인정보취급방침 링크를 클릭하면 표시됩니다.


|          필드 이름           | 최대 길이 |                                                                                       추가 정보                                                                                        |
|-------------------------------|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         회사 이름          |     40     |                이 이름은 회사 포털의 제목으로 표시됩니다. <strong>참고</strong>: 영숫자 문자만 가능합니다. 이 필드는 특수 문자를 지원하지 않습니다.                |
|  IT 부서 연락처 이름   |     40     |                                                                이 이름은 <strong>IT 담당자</strong> 페이지에 표시됩니다.                                                                |
|  IT 부서 전화 번호   |     20     |                                                           이 연락처 번호는 <strong>IT 담당자</strong> 페이지에 표시됩니다.                                                           |
|  IT 부서 전자 메일 주소  |     40     |             이 연락처 주소는 <strong>IT 담당자</strong> 페이지에 표시됩니다. 유효한 메일 주소를 <strong>alias@domainname.com</strong> 형식으로 입력해야 합니다.              |
|    추가 정보     |    120     |                                                            이 정보는 <strong>IT 담당자</strong> 페이지에 표시됩니다.                                                             |
| 회사 개인정보취급방침 URL |     79     | 사용자가 회사 포털에서 개인정보취급방침 링크를 클릭할 때 표시되는 회사 개인정보취급방침을 지정할 수 있습니다. 올바른 URL을 <https://www.contoso.com> 형식으로 입력해야 합니다. |

### <a name="support-contacts"></a>지원 연락처
지원 웹 사이트가 회사 포털의 사용자에게 표시되어, 온라인 지원에 액세스할 수 있도록 합니다.

|필드 이름|최대 길이|추가 정보|
    |----------|------------------------|----------------|
    |지원 웹 사이트 URL|150|최종 사용자가 사용할 지원 웹 사이트가 있는 경우 여기에서 URL을 지정합니다. URL은 https://www.contoso.com 형식이어야 합니다. URL을 지정하지 않으면 회사 포털의 **IT 담당자** 페이지에서 지원 웹 사이트에 대해 아무 내용도 표시되지 않습니다.|
    |웹 사이트 이름|40|이 이름은 지원 웹 사이트의 URL에 대해 표시되는 식별 이름입니다. 지원 웹 사이트 URL을 지정하고 식별 이름을 지정하지 않으면 **IT 웹 사이트로 이동**이 회사 포털의 **IT 담당자** 페이지에 표시됩니다.|


### <a name="company-branding-customization"></a>회사 브랜딩 사용자 지정

회사 로고, 회사 이름, 테마 색 및 배경으로 회사 포털을 사용자 지정할 수 있습니다.

|필드 이름|추가 정보|
    |----------|----------------|
    |테마 색|회사 포털에 적용할 테마 색을 선택합니다.|
    |회사 로고 포함|이 옵션을 설정한 경우 회사 포털에서 표시할 회사 로고를 업로드할 수 있습니다. 회사 포털 배경이 흰색인 경우에 표시되는 로고 하나와 회사 포털 배경이 직접 선택한 테마 색을 사용하는 경우에 표시되는 로고 하나, 두 개의 로고를 업로드할 수 있습니다. 각 로고는 .png 또는 .jpg 파일이어야 하며 최대 해상도가 400 x 100픽셀이고 크기가 750KB 이하여야 합니다.|
    |회사 포털 앱의 배경 선택|이 설정은 회사 포털 앱의 배경에만 영향을 줍니다.|


변경 내용을 저장한 후 관리 콘솔의 **회사 포털** 페이지 맨 아래에 제공된 링크를 사용하여 회사 포털 웹 사이트를 확인할 수 있습니다. 이러한 링크는 변경할 수 없습니다. 사용자가 로그인하면 이러한 링크가 회사 포털에 구독을 표시합니다.

## <a name="step-5-assign-user-licenses"></a>5단계: 사용자 라이선스 할당

**Office 365 관리 포털**을 사용하여 클라우드 기반 사용자를 수동으로 추가하고, 클라우드 기반 사용자 계정 및 온-프레미스 Active Directory에서 Azure AD(Azure Active Directory)로 동기화한 계정에 라이선스를 할당합니다. [Azure AD와 온-프레미스 사용자를 동기화](/intune/users-permissions-add#how-to-sync-on-premises-users-with-azure-ad)할 수 있습니다.

1.  테넌트 관리자 자격 증명을 사용하여 [Office 365 관리 포털](https://portal.office.com/Admin/Default.aspx)에 로그인합니다.

2.  할당할 사용자 계정과 Intune 사용자 라이선스를 선택하고, 사용자 계정 속성의 **Microsoft Intune** 확인란을 선택합니다.

3.  사용자 계정이 Microsoft Intune 사용자 그룹에 추가되고 그에 따라 서비스를 사용하고 장치를 관리하도록 등록할 권한이 사용자에게 부여됩니다.

### <a name="to-synchronize-on-premises-users-with-azure-ad"></a>Azure AD와 온-프레미스 사용자를 동기화하려면

1. 온-프레미스 Active Directory에서 사용자 지정 도메인에 대한 [UPN 접미사를 추가](https://technet.microsoft.com/library/cc772007.aspx)합니다.
2. 가져오려는 온-프레미스 사용자에 대한 새 UPN 접미사를 설정합니다.
3. [Azure AD Connect 동기화](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)를 실행하여 온-프레미스 사용자를 Azure AD와 통합합니다.
4. 사용자 계정 정보가 동기화되면 [Office 365 관리 포털](https://portal.office.com/Admin/Default.aspx)을 사용하여 Microsoft Intune 라이선스를 할당할 수 있습니다.

## <a name="step-6-enable-enrollment"></a>6단계: 등록 사용
MDM 기관을 설정한 후 조직에서 지원하려는 운영 체제에 대한 장치 관리를 설정해야 합니다. 장치 관리를 설정하는 데 필요한 단계는 운영 체제에 따라 다릅니다. 예를 들어 Android OS는 Intune 관리 콘솔에서 아무런 작업이 필요하지 않습니다. 반면에 Windows 및 iOS는 관리를 허용하려면 장치와 Intune 간의 트러스트 관계가 필요합니다.

다음 플랫폼에 대해 관리를 설정합니다.
- [iOS 및 Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Android](set-up-android-management-with-microsoft-intune.md)
- [Android for Work](set-up-android-for-work.md)
- [Windows 10 Mobile 및 Windows Phone](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows PC 및 노트북](manage-windows-pcs-with-microsoft-intune.md)(Intune 클라이언트 소프트웨어)

[회사 소유 장치 등록](manage-corporate-owned-devices.md)을 사용하도록 설정할 수도 있습니다.

## <a name="step-7-next-steps"></a>7단계: 다음 단계

이제 등록이 사용되므로 비즈니스 요구 사항에 맞게 관리를 설정해야 합니다. 몇 가지 관리 옵션은 다음과 같습니다.

- [장치에서 설정 및 기능을 관리하는 정책 배포](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
- [메일, Wi-Fi 및 VPN 등 회사 리소스에 대한 액세스 사용](enable-access-to-company-resources-with-microsoft-intune.md)
- 관리되는 장치에 [앱 추가](add-apps.md) 및 [앱 배포](deploy-apps.md)
- [장치 준수 정책 만들기](introduction-to-device-compliance-policies-in-microsoft-intune.md) 및 [규정 준수를 기반으로 액세스 제한](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)

## <a name="what-to-do-if-you-choose-the-wrong-mdm-authority-setting"></a>잘못된 MDM 기관 설정을 선택한 경우 수행할 작업

잘못된 MDM 기관 설정을 선택했으며 변경해야 하는 경우 다음 옵션을 사용할 수 있습니다.

### <a name="change-the-mdm-authority-yourself"></a>직접 MDM 기관 변경
Configuration Manager 버전 1610 및 Microsoft Intune 버전 1705부터는 Microsoft 지원에 문의하여 기존의 관리 장치를 등록 취소했다가 다시 등록할 필요 없이 Microsoft Intune에서 Configuration Manager(하이브리드)로 변경하거나 그 반대로 변경하여 MDM 기관을 변경할 수 있습니다. 자세한 내용은 [MDM 기관 변경]( /sccm/mdm/deploy-use/change-mdm-authority)을 참조하세요.

### <a name="contact-microsoft-support"></a>Microsoft 지원에 문의
1610 이전 버전의 Configuration Manager를 사용하는 경우에는 Microsoft 지원에 문의해야 합니다. 직접 설정을 변경할 수는 없습니다. Microsoft 지원에 문의하기 전에, Microsoft 지원에서 설정을 변경하기 위해 제공해야 하는 정보를 설명하는 다음 정보를 검토합니다.

MDM 기관을 다시 설정할 수 있는 세 가지 가능한 방법이 있습니다. 지원 요청에서 상황에 맞는 방법을 선택해야 합니다. 요청하는 시나리오가 목록에 없는 경우 Microsoft 지원에 문의하세요.

Microsoft 지원에서 다음 정보를 확인하도록 요청합니다.

- 테넌트 ID: 서비스에 로그인하는 데 사용되는 도메인(예: intune.onmicrosoft.com)
- 변경하려는 MDM 기관
- 아래 나열된 대로 완료한 필수 조건 단계 확인

공존성을 사용하는 경우 Intune 및 Office 365 검사 목록을 둘 다 확인해야 합니다.

#### <a name="reset-mdm-authority-from-intune-to-configuration-manager"></a>MDM 기관을 Intune에서 Configuration Manager로 다시 설정

MDM 기관을 다시 설정하려면 Microsoft 지원에 문의하기 전에 다음 단계를 완료합니다.

- Intune 관리 콘솔에서 모든 장치를 사용 중지합니다. 장치 자체에서 장치를 사용 중지하지 마세요. 
- Service To Service Connector를 삭제(**관리** > **모바일 장치 관리** > **Microsoft Exchange**)하거나, Exchange Connector를 설정한 경우 사용하지 않도록 설정합니다.
- **관리** > **장치 등록 관리자**에서 장치 등록 관리자 역할을 제거합니다.
- **관리** > **모바일 장치 관리** > **장치 그룹 매핑**에서 장치 그룹 매핑을 끕니다.
- **관리** > **모바일 장치 관리** > **Windows** > **테스트용 로드 키**에서 테스트용 로드 키를 삭제합니다.
- **관리** > **모바일 장치 관리** > **iOS** 페이지에서 iOS APNs 인증서를 삭제합니다.
- **관리** > **모바일 장치 관리** > **iOS** 페이지에서 iOS DEP 토큰을 삭제합니다.
- **정책** > **구성 정책**에서 MDM 장치에 대한 정책을 모두 삭제합니다.
- **앱** > **관리 소프트웨어**에서 MDM 장치에 대해 게시된 모든 응용 프로그램을 삭제합니다.

#### <a name="reset-mdm-authority-from-configuration-manager-to-intune"></a>MDM 기관을 Configuration Manager에서 Intune으로 다시 설정

MDM 기관을 다시 설정하려면 Microsoft 지원에 문의하기 전에 다음 단계를 완료합니다.

- Configuration Manager 콘솔에서 모바일 장치로 관리되는 모든 장치를 사용 중지합니다. 장치 자체에서 장치를 사용 중지하지 마세요. 
- Intune 사용자 그룹에서 모든 사용자를 제거합니다. Intune 구독에서 빈 사용자 컬렉션을 가리키거나 대상 컬렉션에서 모든 사용자를 제거합니다.  CloudUserSync.log에서 사용자가 제거되었는지 확인합니다. 
- APNs 인증서를 삭제할 iOS 플랫폼의 선택을 취소합니다.
- MDM 장치에 대해 게시된 모든 응용 프로그램을 삭제합니다.
- MDM 장치에 대한 정책을 모두 삭제합니다.
- Configuration Manager 콘솔에서 Windows Intune 커넥터를 제거합니다(R2 SP1 이전에만 적용).
-구독을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택하여 Intune 구독을 제거합니다.
- SMS Executive 서비스를 다시 시작합니다.
- 프로세스가 완료된 후 Configuration Manager 라이선스가 제거되었는지 확인할 수 있도록 몇 개의 예제 사용자를 제공합니다.

#### <a name="reset-mdm-authority-from-office-365-to-configuration-manager"></a>MDM 기관을 Office 365에서 Configuration Manager로 다시 설정

1. [https://protection.office.com](https://protection.office.com)으로 이동합니다.
2. **보안 정책** 탭을 선택한 다음 **장치 관리**를 선택합니다.
3. **선택적 지우기**를 선택하여 모든 장치를 사용 중지합니다. 장치 자체에서 장치를 사용 중지하지 마세요. 선택적 지우기가 사용되지 않는 경우에는 추가 작업이 필요하지 않습니다.
4. **보안 정책** 탭을 선택한 다음 **장치 보안 정책**을 선택합니다.
5. 기존의 모든 정책에 대해 **삭제**를 선택합니다. 정책이 보류 중 상태이면 추가 작업이 필요하지 않습니다.

>[!NOTE]
>iOS APsN 인증서는 삭제할 수 없으며 계정에 연결된 상태로 유지됩니다.

#### <a name="next-steps-for-mdm-authority-resets"></a>MDM 기관 다시 설정을 위한 다음 단계

Microsoft 지원에서 적용 가능한 검사 목록의 항목을 확인한 후 MDM 기관을 다시 설정하는 데 영업일 기준 최대 3일이 걸릴 수 있지만 일반적으로 1일 내에 다시 설정됩니다.

>[!IMPORTANT]
>Microsoft 지원에서 다시 설정이 완료된 것을 확인할 때까지 구독을 구성하지 마세요. 중간에 구성하면 손상되거나 Intune 서비스를 사용하지 못할 수 있습니다.
