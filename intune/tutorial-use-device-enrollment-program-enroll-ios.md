---
title: 자습서 - Apple Business Manager 또는 디바이스 등록 프로그램을 사용하여 Intune에서 iOS 디바이스 등록
titleSuffix: Microsoft Intune
description: 이 자습서에서는 ABM에서 Apple의 기업 디바이스 등록 기능을 설정하여 Intune에서 iOS 디바이스를 등록합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: faceee883194dbbdcec83f282806035ffc0432d1
ms.sourcegitcommit: 0f771585d3556c0af14500428d5c4c13c89b9b05
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174170"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-ios-devices-in-intune"></a>자습서: ABM(Apple Business Manager)의 Apple 기업 디바이스 등록 기능을 사용하여 Intune에서 iOS 디바이스 등록
Apple Business Manager의 디바이스 등록 기능을 사용하면 디바이스를 간단하게 등록할 수 있습니다. Intune에서는 Apple의 이전 DEP(디바이스 등록 프로그램) 포털도 지원하지만 이제 새 Apple Business Manager를 사용하는 것이 좋습니다. Microsoft Intune 및 Apple Corporate Device Enrollment를 사용할 경우 사용자가 처음 디바이스를 켜면 자동으로 디바이스가 안전하게 등록됩니다. 따라서 각 디바이스를 개별적으로 설정하지 않고도 여러 사용자에게 디바이스를 제공할 수 있습니다. 

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다.
> [!div class="checklist"]
> * Apple 디바이스 등록 토큰 받기
> * Intune에 관리 디바이스 동기화
> * 등록 프로필 만들기
> * 디바이스에 등록 프로필 할당

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건
- [Apple Business Manager](https://business.apple.com) 또는 [Apple 디바이스 등록 프로그램](http://deploy.apple.com)에서 구매한 디바이스
- [모바일 디바이스 관리 기관](mdm-authority-set.md) 설정
- [Apple MDM 푸시 인증서](apple-mdm-push-certificate-get.md) 가져오기

## <a name="get-an-apple-device-enrollment-token"></a>Apple 디바이스 등록 토큰 받기
Apple의 회사 등록 기능으로 iOS 디바이스를 등록하려면 먼저 Apple 디바이스 등록 토큰(.pem) 파일이 필요합니다. 이 토큰을 통해 Intune이 회사 보유 Apple 디바이스 정보를 동기화할 수 있습니다. 또한 Apple에 등록 프로필을 업로드하고 이러한 프로필에 디바이스를 할당할 수 있습니다.

ABM 또는 DEP 포털을 사용하여 디바이스 등록 토큰을 만듭니다. 또한 관리를 위해 포털을 사용하여 디바이스를 Intune에 할당할 수 있습니다.

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰** > **추가**를 선택합니다.

2. **동의**를 선택하여 Microsoft에서 Apple에 사용자 및 디바이스 정보를 보낼 수 있도록 권한을 부여합니다.

   ![공개 키를 다운로드하기 위한 Apple 인증서 작업 영역의 등록 프로그램 토큰 창 스크린샷](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. **공개 키 다운로드**를 선택하여 암호화 키(.pem) 파일을 다운로드하고 로컬로 저장합니다. .pem 파일은 ABM 또는 DEP 포털에서 트러스트 관계 인증서를 요청하는 데 사용됩니다.

4. **Apple 장비 등록 프로그램에 대한 토큰 만들기**를 선택하여 Apple 배포 프로그램 포털을 열고 회사 Apple ID로 로그인합니다. 이 Apple ID를 사용하여 DEP 토큰을 갱신할 수 있습니다.

5.  Apple [배포 프로그램 포털](https://deploy.apple.com)에서 **장비 등록 프로그램**에 대해 **시작**을 선택합니다. 해당 프로세스는 [Apple Business Manager](https://business.apple.com)에서 다음 단계와 약간 다를 수 있습니다.

4. **서버 관리** 페이지에서 **MDM 서버 추가**를 선택합니다.

5. **MDM 서버 이름**에 *TestMDMServer*를 입력한 다음, **다음**을 선택합니다. 서버 이름은 참조용으로 MDM(모바일 디바이스 관리) 서버를 식별하기 위한 것으로, Microsoft Intune 서버의 이름 또는 URL이 아닙니다.

6. **&lt;ServerName&gt; 추가** 대화 상자가 열리고 **공개 키 업로드**가 표시됩니다. **파일 선택...** 을 선택합니다. .pem 파일을 업로드하고 **다음**을 선택합니다.

6. **배포 프로그램** > **디바이스 등록 프로그램** > **디바이스 관리**로 이동합니다.
7. **디바이스 선택 기준**에서 **일련 번호**를 선택합니다. <!--ask Tiffany about this-->

8. **작업 선택**에서 **서버에 할당**, Microsoft Intune에 지정된 &lt;ServerName&gt; 및 **확인**을 순서대로 선택합니다. Apple Portal에서 관리를 위해 지정된 디바이스를 Intune 서버에 할당한 다음 **할당 완료**를 표시합니다.

   Apple Portal에서 **배포 프로그램**&gt;**장비 등록 프로그램**&gt;**할당 기록 보기**로 이동하여 디바이스 목록 및 해당 MDM 서버 할당을 확인합니다.

9. 나중에 참조할 수 있도록 Azure Portal의 Intune에서 이 토큰을 만드는 데 사용된 Apple ID를 제공합니다.

    ![등록 프로그램 토큰을 만드는 데 사용되는 Apple ID를 지정하고 등록 프로그램 토큰을 찾는 스크린샷](./media/device-enrollment-program-enroll-ios/image03.png)

10. **Apple 토큰** 상자에서 인증서(.pem) 파일을 찾은 다음 **열기**, **만들기**를 차례로 선택합니다. 

11. 범위 태그를 사용하여 관리자의 토큰 액세스를 제한하려면 범위를 선택합니다.

## <a name="create-an-apple-enrollment-profile"></a>Apple 등록 프로필 만들기
이제 토큰을 설치했으므로 회사 소유 iOS 디바이스의 등록 프로필을 만들 수 있습니다. 디바이스 등록 프로필은 등록 중에 디바이스 그룹에 적용되는 설정을 정의합니다.

1. Azure Portal의 Intune에서 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택합니다.

2. 방금 설치한 토큰을 선택하고, **프로필** > **프로필 만들기**를 선택합니다.

3. **프로필 만들기**에서 **이름**에 *TestDEPProfile*을 입력하고 **설명**에 *iOS 디바이스용 DEP 테스트*를 입력합니다. 사용자는 이러한 세부 정보를 볼 수 없습니다.

4. **플랫폼**에서 **iOS**를 선택합니다.

5. 등록할 때 디바이스의 **사용자 선호도**의 지정 여부를 결정합니다. 사용자 선호도는 특정 사용자가 사용하는 디바이스를 대상으로 설계되었습니다. 사용자가 앱 설치 같은 서비스에 회사 포털을 사용하려는 경우 **사용자 선호도를 사용하여 등록**을 선택합니다. 사용자가 회사 포털을 필요로 하지 않거나 많은 사용자를 대상으로 디바이스를 프로비저닝하려는 경우 **사용자 선호도 없이 등록**을 선택합니다.

6. 사용자 선호도를 사용한 등록을 선택할 경우 회사 포털 또는 Apple Setup Assistant로 인증할지 결정합니다. 다단계 인증을 사용하거나, 사용자가 최초 로그인에서 암호를 변경할 수 있게 하거나, 사용자가 등록 중에 만료된 암호를 다시 설정하도록 요청하려면 **Apple Setup Assistant 대신 회사 포털을 사용하여 인증**에서 **예**를 선택합니다. Apple에서 제공하는 Apple Setup Assistant를 사용한 기본 HTTP 인증에 익숙하다면 **아니요**를 선택합니다.

7. 사용자 선호도 및 회사 포털을 통한 인증 등록을 선택한 경우 Apple VPP(Volume Purchase Program)를 통해 회사 포털을 설치할지 결정합니다. VPP 토큰으로 회사 포털을 설치할 경우 등록 중에 App Store에서 회사 포털을 다운로드하기 위해 사용자가 Apple ID와 암호를 입력하지 않아도 됩니다. **VPP를 사용하여 회사 포털 설치**에서 **토큰 사용:** 을 선택하여 사용 가능한 회사 포털의 무료 라이선스가 있는 VPP 토큰을 선택합니다. VPP를 사용하여 회사 포털을 배포하지 않으려면 **VPP를 사용하여 회사 포털 설치**에서 **VPP 사용 안 함**을 선택합니다. 

8. 사용자 선호도로 등록, 회사 포털을 사용하여 인증, VPP를 사용하여 회사 포털 설치를 선택한 경우 인증될 때까지 단일 앱 모드에서 회사 포털을 실행할지 결정합니다. 이 설정을 사용하면 사용자가 회사 등록을 마치기 전까지는 다른 앱에 액세스하지 못하게 할 수 있습니다. 등록이 완료될 때까지 사용자에게 이 흐름을 제한하려면 **인증될 때까지 단일 앱 모드에서 포털 실행**에서 **예**를 선택합니다. 

9. **디바이스 관리 설정**을 선택하고, **감독됨** 아래에서 **예**를 선택합니다. 감독되는 디바이스는 회사 iOS 디바이스에 대한 대부분의 관리 옵션을 제공합니다.

10. 사용자가 회사 디바이스의 관리를 제거할 수 없도록 **잠긴 등록**에서 **예**를 선택합니다. 

11. **컴퓨터와 동기화**에서 옵션을 선택하여 iOS 디바이스가 컴퓨터에 동기화할 수 있는지 여부를 결정합니다.

12. 기본적으로 Apple은 디바이스를 디바이스 유형(예: iPad)으로 명명합니다. 다른 이름 템플릿을 제공하려면 **디바이스 이름 템플릿 적용**에서 **예**를 선택합니다. 디바이스에 적용할 이름을 입력합니다. 여기서 *{{SERIAL}}* 및 *{{DEVICETYPE}}* 문자열은 각 디바이스의 일련 번호와 디바이스 유형을 대체합니다. 그렇지 않으면 **디바이스 이름 템플릿 적용**에서 **아니요**를 선택합니다.

13. **확인**을 선택합니다.

14. **설치 도우미 사용자 지정**을 선택하고 **부서 이름**에 *자습서 부서*를 입력합니다. 이 문자열은 디바이스 정품 인증을 하는 동안 사용자가 **구성 정보**를 탭하는 경우 표시됩니다.

15. **부서 전화**에서 전화 번호를 입력합니다. 이 번호는 정품 인증을 하는 동안 사용자가 **도움이 필요하세요?** 단추를 탭하는 경우 표시됩니다.

16. 디바이스 정품 인증을 하는 동안 다양한 화면을 **표시**하거나 **숨길** 수 있습니다. 가장 원활한 등록 환경을 위해 모든 화면을 **숨기기**로 설정합니다.

17. **확인** > **만들기**를 선택합니다.

## <a name="sync-managed-devices-to-intune"></a>Intune에 관리 디바이스 동기화

ABM, ASM 또는 DEP에 등록 프로그램 토큰을 설정하고 디바이스에 MDM 서버를 할당한 후에는 이 디바이스가 Intune 서비스에 동기화되도록 기다리거나 직접 동기화를 푸시할 수 있습니다. 수동 동기화를 하지 않으면 디바이스가 Azure Portal에 표시되는 데 최대 24시간이 소요됩니다.

1. Azure Portal의 Intune에서 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 목록에서 토큰을 선택한 다음, **디바이스** > **동기화**를 선택합니다.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>iOS 디바이스에 등록 프로필 할당

먼저 등록 프로그램 프로필을 디바이스에 할당해야 디바이스를 등록할 수 있습니다. 이러한 디바이스는 Apple에서 Intune으로 동기화되며 ABM, ASM 또는 DEP 포털에서 적합한 MDM 토큰에 할당되어야 합니다.

1. Azure Portal의 Intune에서 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택한 다음, 목록에서 토큰을 선택합니다.
2. **디바이스**를 선택하고 목록에서 디바이스를 선택한 다음 **프로필 할당**을 선택합니다.
3. **프로필 할당** 아래에서 디바이스의 프로필 &gt; **할당**을 선택합니다.

## <a name="distribute-devices-to-users"></a>사용자에게 디바이스 배포

Apple과 Intune 간의 동기화 및 관리를 설정했으며, DEP 디바이스를 등록할 수 있는 프로필을 할당했습니다. 이제 사용자에게 디바이스를 배포할 수 있습니다. 사용자 선호도가 있는 디바이스의 경우 각 사용자에게 Intune 라이선스를 할당해야 합니다.

## <a name="next-steps"></a>다음 단계

iOS 디바이스를 등록할 수 있는 기타 옵션에 대한 자세한 정보를 찾을 수 있습니다.

> [!div class="nextstepaction"]
> [자세한 iOS DEP 등록 문서](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
