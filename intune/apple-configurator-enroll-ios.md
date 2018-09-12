---
title: iOS 장치 등록 - Apple Configurator 설정 도우미
titleSuffix: Microsoft Intune
description: Apple Configurator를 사용하여 설정 도우미를 통해 회사 소유 iOS 장치를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5653e5fda04295041ebc549977007e7060b5508b
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43312683"
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Apple Configurator를 사용한 iOS 장치 등록

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune은 Mac 컴퓨터에서 실행되는 [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344)를 사용하여 iOS 장치를 등록하도록 지원합니다. Apple Configurator를 사용하여 장치를 등록하려면 각 iOS 장치를 USB로 Mac 컴퓨터에 연결하여 회사 등록을 설정해야 합니다. 다음 두 가지 방법으로 Apple Configurator를 사용하여 Intune에 장치를 등록할 수 있습니다.
- **설정 도우미 등록** - 장치를 초기화하고, 설정 도우미 중에 등록하도록 준비합니다.
- **직접 등록** - 장치를 초기화하지 않고, iOS 설정을 통해 장치를 등록합니다. 이 방법은 **사용자 선호도가 없는** 장치만 지원합니다.

Apple Configurator 등록 방법은 [장치 등록 관리자](device-enrollment-manager-enroll.md)에서 사용할 수 없습니다.

## <a name="prerequisites"></a>전제 조건

- IOS 장치에 대한 실제 액세스
- [MDM 기관 설정](mdm-authority-set.md)
- [Apple MDM push certificate](apple-mdm-push-certificate-get.md)
- 장치 일련 번호(설정 도우미 등록에만 해당)
- USB 연결 케이블
- [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344)을 실행 중인 macOS 컴퓨터

## <a name="create-an-apple-configurator-profile-for-devices"></a>장치에 대한 Apple Configurator 프로필 만들기

장치 등록 프로필은 등록 중에 적용되는 설정을 정의합니다. 이러한 설정은 한 번만 적용됩니다. Apple Configurator로 iOS 장치를 등록하기 위한 등록 프로필을 만들려면 이 단계를 따릅니다.

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **Apple Configurator** > **프로필** > **만들기**를 선택합니다.

    ![Apple Configurator에 대한 프로필 만들기](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. **등록 프로필 만들기**에서 관리 목적으로 프로필의 **이름** 및 **설명**을 입력합니다. 사용자는 이러한 세부 정보를 볼 수 없습니다. 이 이름 필드를 사용하여 Azure Active Directory에 동적 그룹을 만들 수 있습니다. 이 등록 프로필로 장치를 할당하기 위해 프로필 이름을 사용하여 enrollmentProfileName 매개 변수를 정의합니다. Azure Active Directory 동적 그룹에 대해 자세히 알아보세요.

    ![사용자 선호도를 사용하여 등록이 선택된 프로필 만들기 화면의 스크린샷](./media/apple-configurator-profile-create.png)

3. **사용자 선호도**에서 이 프로필이 있는 장치가 할당된 사용자로 등록되어야 하는지, 할당된 사용자 없이 등록되어야 하는지 선택합니다.

    - **사용자 선호도를 사용하여 등록** - 사용자에게 속하고 앱 설치 같은 서비스에 회사 포털을 사용하려는 장치의 경우 이 옵션을 선택합니다. 설정 도우미를 사용하여 장치에 사용자를 등록해야 합니다. 그러면 장치에서 회사 데이터와 메일에 액세스할 수 있습니다. 설치 도우미 등록에만 지원됩니다. 사용자 선호도에는 [WS-Trust 1.3 사용자 이름/혼합 엔드포인트](https://technet.microsoft.com/library/adfs2-help-endpoints)가 필요합니다. [자세히 알아봅니다](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **사용자 선호도를 사용하지 않고 등록** - 단일 사용자로 등록되지 않은 장치의 경우 이 옵션을 선택합니다. 로컬 사용자 데이터에 액세스하지 않고 작업을 수행하는 장치에 이 옵션을 사용합니다. 기간 업무 앱을 설치하는 데 사용하는 회사 포털 앱 등 사용자 정보가 필요한 앱은 작동하지 않습니다. 직접 등록의 경우 필수입니다.

4. **사용자 선호도를 사용하여 등록**을 선택한 경우 사용자가 Apple 설정 도우미 대신 회사 포털에서 인증할 수 있도록 하는 옵션이 있습니다.

    > [!NOTE]
    > 다음 중 하나를 수행하려면 **Authenticate with Company Portal instead of Apple Setup Assistant**(Apple 설정 도우미 대신 회사 포털로 인증)를 **예**로 설정합니다.
    >    - 다단계 인증 사용
    >    - 처음 로그인할 때 암호를 변경해야 하는 사용자에게 메시지 표시
    >    - 등록 중에 만료된 암호를 재설정하도록 사용자에게 요청
    >
    > Apple 설정 도우미를 사용하여 인증하는 경우에는 지원되지 않습니다.


6. **만들기**를 선택하여 프로필을 저장합니다.

## <a name="setup-assistant-enrollment"></a>설치 도우미 등록

### <a name="add-apple-configurator-serial-numbers"></a>Apple Configurator 일련 번호 추가

1. 헤더 없이 2열로 구성된 쉼표로 구분된 값(.csv) 목록을 만듭니다. 왼쪽 열에 일련 번호를 추가하고, 오른쪽 열에 세부 정보를 추가합니다. 현재 목록의 최대값은 5,000개 행입니다. 텍스트 편집기에 .csv 목록이 다음과 같이 표시됩니다.

    F7TLWCLBX196,장치 세부 정보</br>
    DLXQPCWVGHMJ,장치 세부 정보

   [iOS 장치 일련 번호를 확인하는 방법](https://support.apple.com/HT204073)을 알아봅니다.
2. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **Apple Configurator** > **장치** > **추가**를 선택합니다.

5. 가져올 일련 번호에 적용할 **등록 프로필**을 선택합니다. 기존 세부 정보를 새 일련 번호 정보로 덮어쓰려는 경우 **기존 식별자에 대한 세부 정보를 덮어씁니다.** 를 선택합니다.
6. **장치 가져오기**에서 일련 번호의 csv 파일을 찾은 다음 **추가**를 선택합니다.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>장치 일련 번호에 프로필 재할당

Apple Configurator 등록을 위해 iOS 일련 번호를 가져올 때 등록 프로필을 할당할 수 있습니다. Azure Portal의 다음 두 위치에서 프로필을 할당할 수도 있습니다.
- **Apple Configurator 장치**
- **AC 프로필**

#### <a name="assign-from-apple-configurator-devices"></a>Apple Configurator 장치에서 할당
1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **Apple Configurator** > **장치**를 선택하고 일련 번호를 선택한 다음 **프로필 할당**을 선택합니다.
2. **프로필 할당**에서 할당할 **새 프로필**을 선택한 다음 **할당**을 선택합니다.

#### <a name="assign-from-profiles"></a>프로필에서 할당
1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **Apple Configurator** > **프로필**을 선택한 다음 프로필을 선택합니다.
2. 프로필에서 **할당된 장치**를 선택한 다음 **할당**을 선택합니다.
3. 프로필에 할당할 장치 일련 번호를 찾기 위해 필터링하고, 장치를 선택한 다음 **할당**을 선택합니다.

### <a name="export-the-profile"></a>프로필 내보내기
프로필을 만들고 일련 번호를 할당한 다음 Intune에서 프로필을 URL로 내보내야 합니다. 그런 다음 장치에 배포하기 위해 Mac에서 Apple Configurator로 가져옵니다.

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **Apple Configurator** > **프로필**을 선택한 다음 내보낼 프로필을 선택합니다.
2. 프로필에서 **프로필 내보내기**를 선택합니다.
3. **프로필 URL**을 복사합니다. 그런 다음 Apple Configurator에서 추가하여 iOS 장치가 사용하는 Intune 프로필을 정의할 수 있습니다.

   다음 절차에서 Apple Configurator에 이 프로필을 가져와 iOS 장치에서 사용하는 Intune 프로필을 정의합니다.

### <a name="enroll-devices-with-setup-assistant"></a>설정 도우미를 사용하여 장치 등록

1. Mac 컴퓨터에서 **Apple Configurator 2**를 엽니다. 메뉴 모음에서 **Apple Configurator 2**를 선택한 후 **기본 설정**을 선택합니다.
    > [!WARNING]
    > 장치는 등록 프로세스 중에 공장 구성으로 재설정됩니다. 장치를 초기화하고 전원을 켜는 것이 좋습니다. 장치를 연결할 때 장치가 **Hello** 화면에 있어야 합니다.

2. **기본 설정** 창에서 **서버**를 선택하고 더하기 기호(+)를 선택하여 MDM 서버 마법사를 시작합니다. **다음**을 선택합니다.
3. Microsoft Intune을 사용한 iOS 장치용 설정 도우미 등록 아래 MDM 서버에 대한 **호스트 이름 또는 URL** 및 **등록 URL**을 입력합니다. 등록 URL에 Intune에서 내보낸 등록 프로필 URL을 입력합니다. **다음**을 선택합니다.  
    "서버 URL이 확인되지 않음"을 알리는 경고는 무시해도 안전합니다. 계속하려면 마법사가 완료될 때까지 **다음**을 선택합니다.
4.  USB 어댑터를 사용하여 Mac 컴퓨터에 iOS 모바일 장치를 연결합니다.
5.  관리하려는 iOS 장치를 선택한 후 **준비**를 선택합니다. **iOS 장치 준비** 창에서 **수동**을 선택하고 **다음**을 선택합니다.
6. **MDM 서버에 등록** 창에서 만든 서버 이름을 선택하고 **다음**을 선택합니다.
7. **장치 감독** 창에서 감독 수준을 선택하고 **다음**을 선택합니다.
8. **조직 만들기** 창에서 **조직**을 선택하거나 새 조직을 만들고 **다음**을 선택합니다.
9. **iOS 설정 도우미 구성** 창에서 사용자에게 제공되는 단계를 선택하고 **준비**를 선택합니다. 메시지가 표시되면 신뢰 설정을 업데이트하도록 인증합니다.  
10. iOS 장치 준비가 완료되면 USB 케이블을 분리합니다.  

### <a name="distribute-devices"></a>장치 배포
이제 장치를 회사에 등록할 준비가 되었습니다. 장치를 끈 다음 사용자에게 배포합니다. 사용자가 장치를 켜면 설정 도우미가 시작됩니다.

사용자가 장치를 받으면 설정 도우미를 완료해야 합니다. 사용자 선호도로 구성한 장치에서 회사 포털 앱을 설치하고 실행하여 앱을 다운로드하고 장치를 관리할 수 있습니다.

## <a name="direct-enrollment"></a>직접 등록
Apple Configurator를 사용하여 iOS 장치를 직접 등록하는 경우 장치의 일련 번호를 몰라도 장치를 등록할 수 있습니다. 또한 등록 중에 Intune에서 장치 이름을 확인하기 전에 식별을 위해 장치에 이름을 지정할 수도 있습니다. 직접 등록된 장치의 경우 회사 포털 앱이 지원되지 않습니다. 이 방법은 장치를 초기화하지 않습니다.

기간 업무 앱을 설치하는 데 사용하는 회사 포털 앱 등 사용자 정보가 필요한 앱은 설치할 수 없습니다.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>프로필을 .mobileconfig로 iOS 장치에 내보내기

1. [Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Apple 등록** > **Apple Configurator** > **프로필**을 선택하고 내보낼 프로필을 선택한 다음 **프로필 내보내기**를 선택합니다.
2. **직접 등록**에서 **프로필 다운로드**를 선택하고 파일을 저장합니다. 등록 프로필 파일은 2주 동안만 유효합니다. 이 때에 다시 만들어야 합니다.
3. [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)를 실행하는 Mac 컴퓨터에 파일을 전송하여 iOS 장치에 관리 프로필로 직접 푸시합니다.
4. 다음 단계를 사용하여 Apple Configurator로 장치를 준비합니다.
    1. Mac 컴퓨터에서 Apple Configurator 2.0을 엽니다.
    2. USB 코드를 사용하여 iOS 장치를 Mac 컴퓨터에 연결합니다. 사진, iTunes 및 장치를 검색할 때 장치에 대해 열려 있는 기타 앱을 닫습니다.
    3. Apple Configurator에서 연결된 iOS 장치를 한 번 선택한 다음 **추가** 단추를 선택합니다. 장치에 추가할 수 있는 옵션이 드롭다운 목록에 나타납니다. **프로필**을 선택합니다.

        ![프로필 URL이 강조 표시된 설정 도우미 등록의 스크린샷 프로필 내보내기](./media/ios-apple-configurator-add-profile.png)

    4. 파일 선택기를 사용하여 Intune에서 내보낸 .mobileconfig 파일을 선택하고 **추가**를 선택합니다. 프로필이 장치에 추가됩니다. 장치가 감독되지 않음인 경우 장치에서 설치에 동의해야 합니다.
5. 다음 단계를 사용하여 iOS 장치에 프로필을 설치합니다. 장치가 설정 도우미를 이미 완료했으며 사용할 준비가 된 상태여야 합니다. 등록 시 앱을 배포해야 하는 경우 앱 배포 시 Apple ID로 앱 스토어에 로그인해야 하기 때문에 장치에 Apple ID가 설정되어 있어야 합니다.
    1. iOS 장치 잠금을 해제합니다.
    2. **관리 프로필**에 대한 **프로필 설치** 대화 상자에서 **설치**를 선택합니다.
    3. 필요한 경우 장치 암호 또는 Apple ID를 제공합니다.
    4. **경고**를 수락하고 **설치**를 선택합니다.
    5. **원격 경고**를 수락하고 **신뢰**를 선택합니다.
    6. **프로필 설치됨** 상자에서 프로필이 설치됨 상태임을 확인하면 **완료**를 선택합니다.

6. iOS 장치에서 **설정**을 열고 **일반** > **장치 관리** > **관리 프로필**로 이동합니다. 프로필 설치가 나열되는지 확인하고 iOS 정책 제한 및 설치된 앱을 확인합니다. 정책 제한 및 앱이 장치에 표시되는 데 최대 10분 정도 걸릴 수 있습니다.

7. 장치를 배포합니다. 이제 iOS 장치가 Intune에 등록되고 관리됩니다.





