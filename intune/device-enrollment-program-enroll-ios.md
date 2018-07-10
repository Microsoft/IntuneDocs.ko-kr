---
title: iOS 장치 등록 - 장비 등록 프로그램
titleSuffix: Microsoft Intune
description: 장비 등록 프로그램을 사용하여 회사 소유 iOS 장치를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8c0eda06c0c781f0a789034abbf5ef8799a9b45c
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34474449"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Apple 장치 등록 프로그램을 통해 iOS 장치를 자동으로 등록

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 항목의 정보를 참조하여 Apple의 [DEP(장비 등록 프로그램)](https://deploy.apple.com)를 통해 구매한 장치에 대해 iOS 장치 등록을 사용할 수 있습니다. 장치를 건드리지 않고 다수의 장치에 대한 DEP 등록을 사용할 수 있습니다. iPhones 및 iPads와 같은 장치를 직접 사용자에게 제공할 수 있습니다. 사용자가 장치를 켜면 설정 도우미가 미리 구성된 설정을 사용하여 실행되고 장치가 관리용으로 등록됩니다.

DEP 등록을 사용하도록 설정하려면 Intune과 Apple DEP 포털을 둘 다 사용합니다. 관리용으로 Intune에 장치를 할당할 수 있으려면 일련 번호 또는 구매 주문 번호 목록이 필요합니다. 등록 중에 장치에 적용된 설정을 포함하는 DEP 등록 프로필을 만듭니다.

그러나 DEP 등록은 [장치 등록 관리자](device-enrollment-manager-enroll.md)에서 작동할 수 없습니다.

## <a name="what-is-supervised-mode"></a>감독됨 모드란?
Apple은 iOS 5에서 감독됨 모드를 도입했습니다. 감독됨 모드에서 iOS 장치를 더 세밀하게 관리할 수 있습니다. 이와 같이 회사 소유 장치에 특히 유용합니다. Intune은 Apple DEP(장치 등록 프로그램)의 일부로 감독됨 모드의 장치를 구성하도록 지원합니다. 

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>전제 조건
- [Apple의 장치 등록 프로그램](http://deploy.apple.com)에서 구매한 장치
- [MDM 기관](mdm-authority-set.md)
- [Apple MDM Push certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Apple DEP 토큰 가져오기

iOS 장치를 DEP에 등록하려면 Apple의 DEP 토큰(.p7m) 파일이 필요합니다. Intune에서는 이 토큰을 통해 회사에서 소유한 DEP 장치에 대한 정보를 동기화할 수 있습니다. 또한 Apple에 등록 프로필을 업로드하고 이러한 프로필에 장치를 할당할 수 있습니다.

Apple DEP 포털을 사용하여 DEP 토큰을 만듭니다. 관리용으로 Intune에 장치를 할당하는 데도 DEP 포털을 사용할 수 있습니다.

> [!NOTE]
> Azure로 마이그레이션하기 전에 Intune 클래식 포털에서 토큰을 삭제하면 Intune이 삭제된 Apple DEP 토큰을 복원할 수 있습니다. Azure Portal에서 DEP 토큰을 다시 삭제할 수 있습니다. Azure Portal에서 DEP 토큰을 다시 삭제할 수 있습니다.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>1단계. 토큰을 만드는 데 필요한 Intune 공개 키 인증서 다운로드

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰** > **추가**를 선택합니다.

    ![등록 프로그램 토큰을 가져옵니다.](./media/device-enrollment-program-enroll-ios/image01.png)

2. **동의**를 선택하여 Microsoft에서 Apple에 사용자 및 장치 정보를 보낼 수 있도록 권한을 부여합니다.

   ![공개 키를 다운로드하기 위한 Apple 인증서 작업 영역의 등록 프로그램 토큰 창 스크린샷](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. **공개 키 다운로드**를 선택하여 암호화 키(.pem) 파일을 다운로드하고 로컬로 저장합니다. .pem 파일은 Apple 장비 등록 프로그램 포털에서 트러스트 관계 인증서를 요청하는 데 사용됩니다.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>2단계. 키를 사용하여 Apple에서 토큰 다운로드

1. **Apple 장비 등록 프로그램에 대한 토큰 만들기**를 선택하여 Apple 배포 프로그램 포털을 열고 회사 Apple ID로 로그인합니다. 이 Apple ID를 사용하여 DEP 토큰을 갱신할 수 있습니다.
2.  Apple [배포 프로그램 포털](https://deploy.apple.com)에서 **장비 등록 프로그램**에 대해 **시작**을 선택합니다.

3. **서버 관리** 페이지에서 **MDM 서버 추가**를 선택합니다.
4. **MDM 서버 이름**을 입력하고 **다음**을 선택합니다. 서버 이름은 참조용으로 MDM(모바일 장치 관리) 서버를 식별하기 위한 것으로, Microsoft Intune 서버의 이름 또는 URL이 아닙니다.

5. **&lt;ServerName&gt; 추가** 대화 상자가 열리고 **공개 키 업로드**가 표시됩니다. **파일 선택...** 을 선택하여 .pem 파일을 업로드하고 **다음**을 선택합니다.

6. **배포 프로그램** &gt; **장비 등록 프로그램** &gt; **장치 관리**로 이동합니다.
7. **장치 선택 기준**에서 장치를 식별하는 방법을 지정합니다.
    - **일련 번호**
    - **주문 번호**
    - **CSV 파일 업로드**

   ![일련 번호로 장치 선택을 지정하고 작업 선택을 서버에 할당으로 설정한 다음 서버 이름을 선택하는 스크린샷](./media/enrollment-program-token-specify-serial.png)

8. **작업 선택**에서 **서버에 할당**, Microsoft Intune에 지정된 &lt;ServerName&gt; 및 **확인**을 순서대로 선택합니다. Apple Portal에서 관리를 위해 지정된 장치를 Intune 서버에 할당한 다음 **할당 완료**를 표시합니다.

   Apple Portal에서 **배포 프로그램** &gt; **장비 등록 프로그램** &gt; **할당 기록 보기**로 이동하여 장치 목록 및 해당 MDM 서버 할당을 확인합니다.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>3단계: 이 토큰을 만드는 데 사용되는 Apple ID 저장

Azure 포털의 Intune에서 나중에 참조할 수 있도록 Apple ID를 제공합니다.

![등록 프로그램 토큰을 만드는 데 사용되는 Apple ID를 지정하고 등록 프로그램 토큰을 찾는 스크린샷](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>4단계. 토큰 업로드
**Apple 토큰** 상자에서 인증서(.pem) 파일을 찾은 다음 **열기**, **만들기**를 차례로 선택합니다. Push Certificate가 있으면 Intune에서 등록된 모바일 장치에 정책을 푸시하여 iOS 장치를 등록하고 관리할 수 있습니다. Intune이 Apple과 자동으로 동기화되어 등록 프로그램 계정을 확인합니다.

## <a name="create-an-apple-enrollment-profile"></a>Apple 등록 프로필 만들기

이제 토큰을 설치했으므로 DEP 장치의 등록 프로필을 만들 수 있습니다. 장치 등록 프로필은 등록 중에 장치 그룹에 적용되는 설정을 정의합니다.

1. Azure Portal의 Intune에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택합니다.
2. 토큰을 선택하고 **프로필**을 선택한 다음 **프로필 만들기**를 선택합니다.

    ![프로필 만들기 스크린샷](./media/device-enrollment-program-enroll-ios/image04.png)

3. **프로필 만들기**에서 관리 목적으로 프로필의 **이름** 및 **설명**을 입력합니다. 사용자는 이러한 세부 정보를 볼 수 없습니다. 이 **이름** 필드를 사용하여 Azure Active Directory에 동적 그룹을 만들 수 있습니다. 이 등록 프로필로 장치를 할당하기 위해 프로필 이름을 사용하여 enrollmentProfileName 매개 변수를 정의합니다. [Azure Active Directory 동적 그룹](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)에 대해 자세히 알아보세요.

    ![프로필 이름 및 설명](./media/device-enrollment-program-enroll-ios/image05.png)

4. **사용자 선호도**에서 이 프로필이 있는 장치가 할당된 사용자로 등록되어야 하는지, 할당된 사용자 없이 등록되어야 하는지 선택합니다.
    - **사용자 선호도를 사용하여 등록** - 사용자에게 속하고 앱 설치 같은 서비스에 회사 포털을 사용하려는 장치의 경우 이 옵션을 선택합니다. 이 옵션을 사용하면 사용자가 회사 포털을 통해 장치를 인증할 수도 있습니다. 사용자 선호도에는 [WS-Trust 1.3 사용자 이름/혼합 끝점](https://technet.microsoft.com/library/adfs2-help-endpoints)이 필요합니다. [자세히 알아봅니다](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **사용자 선호도를 사용하지 않고 등록** - 단일 사용자로 등록되지 않은 장치의 경우 이 옵션을 선택합니다. 로컬 사용자 데이터에 액세스하지 않고 작업을 수행하는 장치에 이 옵션을 사용합니다. 회사 포털 앱과 같은 앱이 작동하지 않습니다.

5. **사용자 선호도를 사용하여 등록**을 선택한 경우 사용자가 Apple 설정 도우미 대신 회사 포털에서 인증할 수 있도록 하는 옵션이 있습니다.

    ![회사 포털에서 인증합니다.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > 프로필 속성이 **사용자 선호도를 사용하여 등록**하도록 설정되어 있는 경우 DEP를 등록하는 동안 MFA(다단계 인증)가 작동하지 않습니다. 등록 후 MFA는 장치에서 예상대로 작동합니다. 처음 로그인할 때 암호를 변경해야 하는 사용자에게 장치가 메시지를 표시할 수 없습니다. 또한 암호가 만료된 사용자는 등록 중에 암호를 재설정하라는 메시지가 표시되지 않습니다. 사용자가 다른 장치를 사용하여 암호를 재설정해야 합니다.

6. **장치 관리 설정**을 선택한 다음 이 프로필을 사용하는 장치를 감독할지 여부를 선택합니다.

    ![장치 관리 설정 스크린샷](./media/device-enrollment-program-enroll-ios/devicemanagementsettingsblade.png)

    **감독**되는 장치의 경우 더 많은 관리 옵션이 제공되며 기본적으로 활성화 잠금을 사용할 수 없습니다. 특히 많은 수의 iOS 장치를 배포하는 조직의 경우 감독됨 모드를 사용하기 위한 메커니즘으로 DEP를 사용하는 것이 좋습니다.

    사용자는 해당 장치가 감독된다는 알림을 다음 두 가지 방법으로 받습니다.

   - 잠금 화면에 “이 iPhone은 Contoso에서 관리됩니다.”라는 메시지가 표시됩니다.
   - **설정** > **일반** > **정보** 화면에 “이 iPhone은 감독됩니다. Contoso는 사용자의 인터넷 트래픽을 모니터링하고 이 장치를 찾습니다."라는 메시지를

     > [!NOTE]
     > 감독 없이 등록된 장치는 Apple Configurator를 사용하여 감독으로만 다시 설정할 수 있습니다. 이러한 방식으로 장치를 다시 설정하려면 iOS 장치를 Mac에 USB 케이블로 연결해야 합니다. 이에 대해 [Apple Configurator 문서](http://help.apple.com/configurator/mac/2.3)에서 자세히 알아보세요.

7. 이 프로필을 사용하는 장치에 대해 잠긴 환경을 사용할지 여부를 선택합니다. **잠긴 환경**에서는 **설정** 메뉴에서 관리 프로필을 제거할 수 있는 iOS 설정을 사용할 수 없습니다. 장치 등록 후 장치를 초기화하지 않고는 이 설정을 변경할 수 없습니다. 이러한 장치는 **감독됨** 관리 모드가 *예*로 설정되어 있어야 합니다. 

8. 이 프로필을 사용하는 장치가 **컴퓨터와 동기화**할 수 있도록 할지 여부를 선택합니다. **인증서로 Apple Configurator 허용**을 선택한 경우 **Apple Configurator 인증서** 아래에서 인증서를 선택해야 합니다.

9. 이전 단계에서 **인증서로 Apple Configurator 허용**을 선택한 경우 가져올 Apple Configurator 인증서를 선택합니다.

10. **확인**을 선택합니다.

11. **설정 도우미 설정**을 선택하여 다음 프로필 설정을 구성합니다. ![설정 도우미 사용자 지정](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    |                 Setting                  |                                                                                               설명                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>부서 이름</strong>     |                                                             정품 인증을 하는 동안 사용자가 <strong>구성 정보</strong>를 탭하면 표시됩니다.                                                              |
    |    <strong>부서 전화</strong>     |                                                          정품 인증을 하는 동안 사용자가 <strong>도움이 필요하세요?</strong> 단추를 클릭하면 표시됩니다.                                                          |
    | <strong>설정 도우미 옵션</strong> |                                                     다음 선택적 설정은 나중에 iOS <strong>설정</strong> 메뉴에서 지정할 수 있습니다.                                                      |
    |        <strong>암호</strong>         | 정품 인증을 하는 동안 암호를 묻는 메시지가 표시됩니다. 장치가 보안된 상태가 아니거나 다른 방식으로 액세스가 제어된 상태(즉, 하나의 앱만 사용할 수 있도록 장치를 제한하는 키오스크 모드)가 아니면 항상 암호를 요구합니다. |
    |    <strong>위치 서비스</strong>    |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 서비스를 확인하는 메시지가 표시됩니다.                                                                  |
    |         <strong>복원</strong>         |                                                                이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 iCloud 백업을 확인하는 메시지가 표시됩니다.                                                                 |
    |   <strong>iCloud 및 Apple ID</strong>   |                         이 옵션을 사용하도록 설정하면 설정 도우미에서 Apple ID로 로그인하라는 메시지가 표시되고, 앱 및 데이터 화면을 통해 iCloud 백업에서 장치를 복원할 수 있습니다.                         |
    |  <strong>계약조건</strong>   |                                                   이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 Apple 사용 약관에 동의하라는 메시지가 표시됩니다.                                                   |
    |        <strong>터치 ID</strong>         |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |
    |          <strong>확대/축소</strong>           |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |
    |          <strong>Siri</strong>           |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |
    |     <strong>진단 데이터</strong>     |                                                                 이 옵션을 사용하도록 설정하면 정품 인증을 하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.                                                                 |


12. **확인**을 선택합니다.

13. 프로필을 저장하려면 **만들기**를 선택합니다.

## <a name="sync-managed-devices"></a>관리되는 장치 동기화
이제 Intune에 장치 관리 권한이 있으므로 Intune을 Apple과 동기화하여 Azure 포털의 Intune에서 관리되는 장치를 확인할 수 있습니다.

1. Azure Portal의 Intune에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 목록에서 토큰을 선택한 다음 **장치** > **동기화**를 선택합니다. ![등록 프로그램 장치 노드가 선택되고 동기화 링크를 선택하는 스크린샷](./media/device-enrollment-program-enroll-ios/image06.png)

   허용되는 등록 프로그램 트래픽에 대한 Apple 약관을 준수하기 위해 Intune에서는 다음과 같은 제한 사항을 적용합니다.
   - 전체 동기화는 7일마다 한 번씩만 실행할 수 있습니다. 전체 동기화 중에 Intune은 Intune에 연결된 Apple MDM 서버에 할당된 일련 번호의 전체 업데이트된 목록을 가져옵니다. Intune 포털에서 등록 프로그램 장치가 삭제된 후에는 전체 동기화가 실행될 때까지 해당 장치를 다시 가져올 수 없습니다.   
   - 동기화는 24시간마다 자동으로 실행됩니다. **동기화** 단추를 클릭하여 동기화할 수도 있습니다(15분마다 한 번만). 모든 동기화 요청은 완료하는 데 15분이 주어집니다. **동기화** 단추는 동기화가 완료될 때까지 사용할 수 없습니다. 이 동기화는 기존 장치 상태를 새로 고치고 Apple MDM 서버에 할당된 새 장치를 가져옵니다.   


## <a name="assign-an-enrollment-profile-to-devices"></a>장치에 등록 프로필 할당
먼저 등록 프로그램 프로필을 장치에 할당해야 장치를 등록할 수 있습니다.

>[!NOTE]
>**Apple 일련 번호** 블레이드에서 프로필에 일련 번호를 할당할 수도 있습니다.

1. Azure Portal의 Intune에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택한 다음 목록에서 토큰을 선택합니다.
2. **장치**를 선택하고 목록에서 장치를 선택한 다음 **프로필 할당**을 선택합니다.
3. **프로필 할당**에서 장치의 프로필을 선택한 다음 **할당**을 선택합니다.

### <a name="assign-a-default-profile"></a>기본 프로필 할당

특정 토큰에 등록하는 모든 장치에 적용할 기본 프로필을 선택할 수 있습니다.

1. Azure Portal의 Intune에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택한 다음 목록에서 토큰을 선택합니다.
2. **기본 프로필 설정**을 선택하고 드롭다운 목록에서 프로필을 선택한 다음 **저장**을 선택합니다. 이 프로필은 토큰에 등록하는 모든 장치에 적용됩니다.

## <a name="distribute-devices"></a>장치 배포
Apple과 Intune 간의 동기화 및 관리를 사용하도록 설정했으며 DEP 장치를 등록할 수 있는 프로필을 할당했습니다. 이제 사용자에게 장치를 배포할 수 있습니다. 사용자 선호도가 있는 장치의 경우 각 사용자에게 Intune 라이선스를 할당해야 합니다. 사용자 선호도를 사용하지 않는 장치에는 장치 라이선스가 필요합니다. 활성화된 장치는 초기화될 때까지 등록 프로필을 적용할 수 없습니다.

[장비 등록 프로그램을 통해 Intune에서 iOS 장치 등록](/intune-user-help/enroll-your-device-dep-ios)을 참조하세요.

## <a name="renew-a-dep-token"></a>DEP 토큰 갱신  
1. deploy.apple.com으로 이동합니다.  
2. **서버 관리**에서 갱신할 토큰 파일과 연결된 MDM 서버를 선택합니다.
3. **새 토큰 생성**을 선택합니다.

    ![새 토큰 생성의 스크린샷입니다.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. **서버 토큰**을 선택합니다.  
5. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 토큰을 선택합니다.
    ![등록 프로그램 토큰의 스크린샷입니다.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. **토큰 갱신**을 선택하고 원래 토큰을 만드는 데 사용되는 Apple ID를 입력합니다.  
    ![새 토큰 생성의 스크린샷입니다.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. 새로 다운로드된 토큰을 업로드합니다.  
9. **토큰 갱신**을 선택합니다. 토큰이 갱신되었다는 확인 메시지가 표시됩니다.   
    ![확인의 스크린샷입니다.](./media/device-enrollment-program-enroll-ios/confirmation.png)
