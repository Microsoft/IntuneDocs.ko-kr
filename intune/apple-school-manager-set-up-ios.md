---
title: iOS 디바이스용 Apple School Manager 프로그램 등록
titleSuffix: Microsoft Intune
description: Intune을 사용하여 회사 소유 iOS 디바이스에 대해 Apple School Manager 프로그램 등록을 설정하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c35a23e-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: fdda0edd8c7bf67dbfce9d428f1b3ce0266b3726
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032421"
---
# <a name="set-up-ios-device-enrollment-with-apple-school-manager"></a>Apple School Manager를 통해 iOS 디바이스 등록 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[Apple School Manager](https://school.apple.com/) 프로그램을 통해 구입한 iOS 디바이스를 등록하도록 Intune을 설정할 수 있습니다. Intune을 Apple School Manager와 함께 사용하면 많은 수의 iOS 디바이스를 직접 조작하지 않고 쉽게 등록할 수 있습니다. 학생이나 교사가 디바이스를 켜면 설정 도우미가 미리 구성된 설정을 사용하여 실행되고 디바이스가 관리용으로 등록됩니다.

Apple School Manager 등록을 활성화하려면 Intune과 Apple School Manager 포털을 모두 사용해야 합니다. 관리용으로 Intune에 디바이스를 할당할 수 있으려면 일련 번호 또는 구매 주문 번호 목록이 필요합니다. 등록 중에 디바이스에 적용된 설정을 포함하는 DEP 등록 프로필을 만듭니다.

Apple School Manager 등록은 [Apple의 장비 등록 프로그램](device-enrollment-program-enroll-ios.md) 또는 [디바이스 등록 관리자](device-enrollment-manager-enroll.md)와 함께 사용할 수 없습니다.

**필수 구성 요소**
- [Apple MDM Push certificate](apple-mdm-push-certificate-get.md)
- [MDM 기관](mdm-authority-set.md)
- [Apple MDM Push certificate](apple-mdm-push-certificate-get.md)
- ADFS를 사용하는 경우 사용자 선호도에는 [WS-Trust 1.3 사용자 이름/혼합 엔드포인트](https://technet.microsoft.com/library/adfs2-help-endpoints)가 필요합니다. [자세히 알아봅니다](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- [Apple School Management](http://school.apple.com) 프로그램으로 구입한 장치

## <a name="get-an-apple-token-and-assign-devices"></a>Apple 토큰 가져오기 및 디바이스 할당

회사 소유 iOS 디바이스를 Apple School Manager에 등록하려면 Apple의 토큰(.p7m) 파일이 필요합니다. Intune에서는 이 토큰을 통해 Apple School Manager 참가 디바이스에 대한 정보를 동기화할 수 있습니다. 또한 Apple에 등록 프로필을 업로드하고 이러한 프로필에 디바이스를 할당할 수 있습니다. Apple 포털을 사용하는 동안 관리할 디바이스 일련 번호를 할당할 수도 있습니다.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-an-apple-token"></a>1단계. Apple 토큰을 만드는 데 필요한 Intune 공개 키 인증서 다운로드

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰** > **추가**를 선택합니다.

   ![등록 프로그램 토큰을 가져옵니다.](./media/device-enrollment-program-enroll-ios/image01.png)

2. **등록 프로그램 토큰** 블레이드에서 **공개 키 다운로드**를 선택하여 암호화 키(.pem) 파일을 다운로드하고 로컬로 저장합니다. .pem 파일은 Apple School Manager 포털에서 트러스트 관계 인증서를 요청하는 데 사용됩니다.
     ![등록 프로그램 토큰 블레이드입니다.](./media/device-enrollment-program-enroll-ios/image02.png)

### <a name="step-2-download-a-token-and-assign-devices"></a>2단계. 토큰 다운로드 및 디바이스 할당
1. **Apple School Manager를 통해 토큰 만들기**를 선택하고 회사 Apple ID로 Apple School에 로그인합니다. 이 Apple ID를 사용하여 Apple School Manager 토큰을 갱신할 수 있습니다.
2.  [Apple School Manager 포털](https://school.apple.com)에서 **MDM 서버**로 이동한 다음 오른쪽 위에 있는 **MDM 서버 추가**를 선택합니다.
3.  **MDM 서버 이름**을 입력합니다. 서버 이름은 참조용으로 MDM(모바일 디바이스 관리) 서버를 식별하기 위한 것으로, Microsoft Intune 서버의 이름 또는 URL이 아닙니다.
   ![일련 번호 옵션이 선택된 Apple School Manager 포털 스크린샷](./media/asm-server-assignment.png)

4.  Apple 포털에서 **파일 업로드...** 를 선택하고 .pem 파일이 있는 위치로 이동한 다음 오른쪽 아래에 있는 **MDM 서버 저장**을 선택합니다.
5.  **토큰 가져오기**를 선택하고 컴퓨터에 서버 토큰(.p7m) 파일을 다운로드합니다.
6. **장치 할당**으로 이동한 다음 **장치 선택**에서 **일련 번호**, **주문 번호**를 수동으로 입력하거나 **CSV 파일 업로드**를 선택합니다.
     ![일련 번호 옵션이 선택된 Apple School Manager 포털 스크린샷](./media/asm-device-assignment.png)
7.  **서버에 할당** 작업을 선택하고 작성한 **MDM 서버**를 선택합니다.
8. **장치 선택** 방법을 지정한 다음 장치 정보 및 세부 정보를 제공합니다.
9. **서버에 할당**을 선택하고 Microsoft Intune에 대해 지정된 &lt;ServerName&gt;을 선택한 다음 **확인**을 선택합니다.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>3단계: 이 토큰을 만드는 데 사용되는 Apple ID 저장

Azure 포털의 Intune에서 나중에 참조할 수 있도록 Apple ID를 제공합니다.

![등록 프로그램 토큰을 만드는 데 사용되는 Apple ID를 지정하고 등록 프로그램 토큰을 찾는 스크린샷](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>4단계. 토큰 업로드
**Apple 토큰** 상자에서 인증서(.pem) 파일을 찾은 다음 **열기**, **만들기**를 차례로 선택합니다. Push Certificate가 있으면 Intune에서 등록된 모바일 디바이스에 정책을 푸시하여 iOS 디바이스를 등록하고 관리할 수 있습니다. Intune은 Apple에서 Apple School Manager 디바이스를 자동으로 동기화합니다.

## <a name="create-an-apple-enrollment-profile"></a>Apple 등록 프로필 만들기
이제 토큰을 설치했으므로 Apple School 디바이스의 등록 프로필을 만들 수 있습니다. 디바이스 등록 프로필은 등록 중에 디바이스 그룹에 적용되는 설정을 정의합니다.

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택합니다.
2. 토큰을 선택하고 **프로필**을 선택한 다음 **프로필 만들기**를 선택합니다.

3. **프로필 만들기**에서 관리 목적으로 프로필의 **이름** 및 **설명**을 입력합니다. 사용자는 이러한 세부 정보를 볼 수 없습니다. 이 **이름** 필드를 사용하여 Azure Active Directory에 동적 그룹을 만들 수 있습니다. 이 등록 프로필로 디바이스를 할당하기 위해 프로필 이름을 사용하여 enrollmentProfileName 매개 변수를 정의합니다. [Azure Active Directory 동적 그룹](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)에 대해 자세히 알아보세요.

    ![프로필 이름 및 설명](./media/device-enrollment-program-enroll-ios/image05.png)

4. **사용자 선호도**에서 이 프로필이 있는 장치가 할당된 사용자로 등록되어야 하는지, 할당된 사용자 없이 등록되어야 하는지 선택합니다.
    - **사용자 선호도를 사용하여 등록** - 사용자에게 속하고 앱 설치 같은 서비스에 회사 포털을 사용하려는 장치의 경우 이 옵션을 선택합니다. 이 옵션을 사용하면 사용자가 회사 포털을 통해 디바이스를 인증할 수도 있습니다. ADFS를 사용하는 경우 사용자 선호도에는 [WS-Trust 1.3 사용자 이름/혼합 엔드포인트](https://technet.microsoft.com/library/adfs2-help-endpoints)가 필요합니다. [자세히 알아봅니다](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).   Apple School Manager의 공유 iPad 모드에서는 사용자가 사용자 선호도를 사용하지 않고 등록해야 합니다.

    - **사용자 선호도를 사용하지 않고 등록** - 공유 장치와 같이 단일 사용자로 등록되지 않은 장치의 경우 이 옵션을 선택합니다. 로컬 사용자 데이터에 액세스하지 않고 작업을 수행하는 디바이스에 이 옵션을 사용합니다. 회사 포털 앱과 같은 앱이 작동하지 않습니다.

5. **사용자 선호도를 사용하여 등록**을 선택한 경우 사용자가 Apple 설정 도우미 대신 회사 포털에서 인증할 수 있도록 하는 옵션이 있습니다.

    ![회사 포털에서 인증합니다.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > 다음 중 하나를 수행하려면 **Authenticate with Company Portal instead of Apple Setup Assistant**(Apple 설정 도우미 대신 회사 포털로 인증)를 **예**로 설정합니다.
    >    - 다단계 인증 사용
    >    - 처음 로그인할 때 암호를 변경해야 하는 사용자에게 메시지 표시
    >    - 등록 중에 만료된 암호를 재설정하도록 사용자에게 요청
    >
    > Apple 설정 도우미를 사용하여 인증하는 경우에는 지원되지 않습니다.

6. **장치 관리 설정**을 선택한 다음 이 프로필을 사용하는 장치를 감독할지 여부를 선택합니다.
    **감독**되는 장치의 경우 더 많은 관리 옵션이 제공되며 기본적으로 활성화 잠금을 사용할 수 없습니다. 특히 많은 수의 iOS 디바이스를 배포하는 조직의 경우 감독됨 모드를 사용하기 위한 메커니즘으로 DEP를 사용하는 것이 좋습니다.

    사용자는 해당 디바이스가 감독된다는 알림을 다음 두 가지 방법으로 받습니다.

   - 잠금 화면에는 다음이 표시됩니다. “이 iPhone은 Contoso에서 관리됩니다.”
   - **설정** > **일반** > **정보** 화면에 다음이 표시됩니다. “이 iPhone은 감독됩니다. Contoso는 사용자의 인터넷 트래픽을 모니터링하고 이 장치를 찾습니다.”라는 메시지를

     > [!NOTE]
     > 감독 없이 등록된 디바이스는 Apple Configurator를 사용하여 감독으로만 다시 설정할 수 있습니다. 이러한 방식으로 디바이스를 다시 설정하려면 iOS 디바이스를 Mac에 USB 케이블로 연결해야 합니다. 이에 대해 [Apple Configurator 문서](http://help.apple.com/configurator/mac/2.3)에서 자세히 알아보세요.

7. 이 프로필을 사용하는 디바이스에 대해 잠긴 환경을 사용할지 여부를 선택합니다. **잠긴 환경**에서는 **설정** 메뉴에서 관리 프로필을 제거할 수 있는 iOS 설정을 사용할 수 없습니다. 디바이스를 등록한 후에 이 설정을 변경하려면 디바이스를 초기화해야 합니다. 이러한 디바이스는 **감독됨** 관리 모드가 *예*로 설정되어 있어야 합니다. 

8. 여러 사용자가 관리되는 Apple ID를 사용하여 등록된 iPad에 로그온할 수 있게 하려면 **공유 iPad**에서 **예**를 선택합니다(이 옵션을 사용하려면 **사용자 선호도를 사용하지 않고 등록** 및 **감독됨** 모드를 **예**로 설정해야 함). 관리되는 Apple ID는 Apple School Manager 포털에서 작성됩니다. [공유 iPad](education-settings-configure-ios-shared.md) 및 [Apple의 공유 iPad 요구 사항](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56)에 대해 자세히 알아보세요.

9. 이 프로필을 사용하는 디바이스가 **컴퓨터와 동기화**할 수 있도록 할지 여부를 선택합니다. **인증서로 Apple Configurator 허용**을 선택한 경우 **Apple Configurator 인증서** 아래에서 인증서를 선택해야 합니다.

10. 이전 단계에서 **인증서로 Apple Configurator 허용**을 선택한 경우 가져올 Apple Configurator 인증서를 선택합니다.

11. **확인**을 선택합니다.

12. **설정 도우미 설정**을 선택하여 다음 프로필 설정을 구성합니다. ![설정 도우미 사용자 지정.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    |                 Setting                  |                                                                                               설명                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>부서 이름</strong>     |                                                             정품 인증을 하는 동안 사용자가 <strong>구성 정보</strong>를 탭하면 표시됩니다.                                                              |
    |    <strong>부서 전화</strong>     |                                                          정품 인증을 하는 동안 사용자가 <strong>도움이 필요하세요?</strong> 단추를 클릭하면 표시됩니다.                                                          |
    | <strong>설정 도우미 옵션</strong> |                                                     다음 선택적 설정은 나중에 iOS <strong>설정</strong> 메뉴에서 지정할 수 있습니다.                                                      |
    |        <strong>암호</strong>         | 정품 인증을 하는 동안 암호를 묻는 메시지가 표시됩니다. 디바이스가 보안된 상태가 아니거나 다른 방식으로 액세스가 제어된 상태(즉, 하나의 앱만 사용할 수 있도록 디바이스를 제한하는 키오스크 모드)가 아니면 항상 암호를 요구합니다. |
    |    <strong>위치 서비스</strong>    |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 서비스를 확인하는 메시지가 표시됩니다.                                                                  |
    |         <strong>복원</strong>         |                                                                이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 iCloud 백업을 확인하는 메시지가 표시됩니다.                                                                 |
    |   <strong>iCloud 및 Apple ID</strong>   |                         이 옵션을 사용하도록 설정하면 설정 도우미에서 Apple ID로 로그인하라는 메시지가 표시되고, 앱 및 데이터 화면을 통해 iCloud 백업에서 장치를 복원할 수 있습니다.                         |
    |  <strong>계약조건</strong>   |                                                   이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 Apple 사용 약관에 동의하라는 메시지가 표시됩니다.                                                   |
    |        <strong>터치 ID</strong>         |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |
    |          <strong>확대/축소</strong>           |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |
    |          <strong>Siri</strong>           |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |
    |     <strong>진단 데이터</strong>     |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |


13. **확인**을 선택합니다.

14. 프로필을 저장하려면 **만들기**를 선택합니다.

## <a name="connect-school-data-sync"></a>학교 데이터 동기화 연결
(선택 사항) Apple School Manager에서는 Microsoft SDS(학교 데이터 동기화)를 사용하여 학급 명단 데이터를 Azure AD(Active Directory)에 동기화할 수 있습니다. 하나의 토큰만 SDS와 동기화할 수 있습니다. 학교 데이터 동기화를 사용하여 다른 토큰을 설정하면 이전에 SDS가 설정된 토큰에서 SDS가 제거됩니다. 새 연결이 현재 토큰을 대체합니다. SDS를 사용하여 학교 데이터를 동기화하려면 다음 단계를 완료하세요.

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택합니다.
2. Apple School Manager 토큰을 선택한 다음 **학교 데이터 동기화**를 선택합니다.
3. **학교 데이터 동기화**에서 **허용**을 선택합니다. Intune은 이 설정을 통해 Office 365에서 SDS와 연결할 수 있습니다.
4. Apple School Manager와 Azure AD 간의 연결을 사용하도록 설정하려면 **Microsoft School Data Sync 설정**을 선택합니다. [학교 데이터 동기화를 설정하는 방법](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1)에 대해 자세히 알아보세요.
5. **저장** > **확인**을 클릭합니다.

## <a name="sync-managed-devices"></a>관리되는 디바이스 동기화

Intune에 Apple School Manager 디바이스 관리 권한이 할당된 후 Intune을 Apple 서비스와 동기화하여 Intune에서 관리 디바이스를 확인합니다.

[Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 목록에서 토큰을 선택한 다음 **장치** > **동기화**를 선택합니다. ![등록 프로그램 장치 노드가 선택되고 동기화 링크를 선택하는 스크린샷](./media/device-enrollment-program-enroll-ios/image06.png)

  허용되는 등록 프로그램 트래픽에 대한 Apple 약관을 준수하기 위해 Intune에서는 다음과 같은 제한 사항을 적용합니다.
  - 전체 동기화는 7일마다 한 번씩만 실행할 수 있습니다. 전체 동기화 동안 Intune은 Intune에 할당된 모든 Apple 일련 번호를 새로 고칩니다. 전체 동기화를 이전 전체 동기화의 7일 이내에 시도하는 경우 Intune은 Intune에 나열되지 않은 일련 번호만 새로 고칩니다.
  - 모든 동기화 요청은 완료하는 데 15분이 주어집니다. 이 시간 동안 또는 요청이 성공될 때까지 **동기화** 단추는 비활성화됩니다.
  - Intune은 24시간마다 새 디바이스 및 제거된 디바이스를 Apple과 동기화합니다.

>[!NOTE]
>**등록 프로그램 장치** 블레이드에서 프로필에 Apple School Manager 일련 번호를 할당할 수도 있습니다.

## <a name="assign-a-profile-to-devices"></a>디바이스에 프로필 할당
Intune에서 관리하는 Apple School Manager 디바이스를 등록하려면 등록 프로필을 할당해야 합니다.

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택한 다음 목록에서 토큰을 선택합니다.
2. **장치**를 선택하고 목록에서 장치를 선택한 다음 **프로필 할당**을 선택합니다.
3. **프로필 할당**에서 장치의 프로필을 선택한 다음, **할당**을 선택합니다.

## <a name="distribute-devices-to-users"></a>사용자에게 디바이스 배포

Apple과 Intune 간의 동기화 및 관리를 사용하도록 설정했으며 Apple School 디바이스의 등록을 허용하는 프로필을 할당했습니다. 이제 사용자에게 디바이스를 배포할 수 있습니다. 켜져 있는 iOS Apple School Manager 디바이스는 Intune에서 관리하도록 등록됩니다. 디바이스가 활성화되어 사용 중이면 디바이스를 초기화할 때까지 프로필을 적용할 수 없습니다.
