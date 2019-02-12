---
title: 자습서 - 디바이스 등록 프로그램을 사용하여 Intune에서 iOS 디바이스 등록
titleSuffix: Microsoft Intune
description: 이 자습서에서는 Intune에서 iOS 디바이스를 등록하도록 Apple의 DEP을 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/30/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17258ce2bd671dba091fa7206e599858e5ec7a93
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841541"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>자습서: 디바이스 등록 프로그램을 사용하여 Intune에서 iOS 디바이스 등록
Apple의 DEP(디바이스 등록 프로그램)는 디바이스 등록을 간소화합니다. Microsoft Intune 및 DEP를 사용하면 디바이스는 사용자가 처음으로 디바이스를 작동하는 경우 자동으로 등록됩니다. 따라서 각 디바이스를 개별적으로 설정하지 않고도 여러 사용자에게 디바이스를 제공할 수 있습니다. 

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다.
> [!div class="checklist"]
> * Apple DEP 토큰 가져오기
> * Autopilot 디바이스 그룹 만들기
> * Autopilot 배포 프로필 만들기
> * 디바이스 그룹에 Autopilot 배포 프로필 할당
> * 사용자에게 Windows 디바이스 배포

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건
- [Apple의 디바이스 등록 프로그램](http://deploy.apple.com)에서 구매한 디바이스
- [모바일 디바이스 관리 기관](mdm-authority-set.md) 설정
- [Apple MDM 푸시 인증서](apple-mdm-push-certificate-get.md) 가져오기

## <a name="get-an-apple-dep-token"></a>Apple DEP 토큰 가져오기
DEP에 iOS 디바이스를 등록하기에 앞서 Apple DEP 토큰(.pem) 파일이 필요합니다. Intune에서는 이 토큰을 통해 회사에서 소유한 DEP 디바이스에 대한 정보를 동기화할 수 있습니다. 또한 Apple에 등록 프로필을 업로드하고 이러한 프로필에 디바이스를 할당할 수 있습니다.

Apple DEP 포털을 사용하여 DEP 토큰을 만듭니다. 관리용으로 Intune에 디바이스를 할당하는 데도 DEP 포털을 사용할 수 있습니다.

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰** > **추가**를 선택합니다.

2. **동의**를 선택하여 Microsoft에서 Apple에 사용자 및 디바이스 정보를 보낼 수 있도록 권한을 부여합니다.

   ![공개 키를 다운로드하기 위한 Apple 인증서 작업 영역의 등록 프로그램 토큰 창 스크린샷](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. **공개 키 다운로드**를 선택하여 암호화 키(.pem) 파일을 다운로드하고 로컬로 저장합니다. .pem 파일은 Apple 디바이스 등록 프로그램 포털에서 트러스트 관계 인증서를 요청하는 데 사용됩니다.

4. **Apple 장비 등록 프로그램에 대한 토큰 만들기**를 선택하여 Apple 배포 프로그램 포털을 열고 회사 Apple ID로 로그인합니다. 이 Apple ID를 사용하여 DEP 토큰을 갱신할 수 있습니다.

5.  Apple [배포 프로그램 포털](https://deploy.apple.com)에서 **장비 등록 프로그램**에 대해 **시작**을 선택합니다.

4. **서버 관리** 페이지에서 **MDM 서버 추가**를 선택합니다.

5. **MDM 서버 이름**에 *TestMDMServer*를 입력한 다음, **다음**을 선택합니다. 서버 이름은 참조용으로 MDM(모바일 디바이스 관리) 서버를 식별하기 위한 것으로, Microsoft Intune 서버의 이름 또는 URL이 아닙니다.

6. **&lt;ServerName&gt; 추가** 대화 상자가 열리고 **공개 키 업로드**가 표시됩니다. **파일 선택...** 을 선택하여 .pem 파일을 업로드하고 **다음**을 선택합니다.

6. **배포 프로그램** > **디바이스 등록 프로그램** > **디바이스 관리**로 이동합니다.
7. **디바이스 선택 기준**에서 **일련 번호**를 선택합니다. <!--ask Tiffany about this-->

8. **작업 선택**에서 **서버에 할당**, Microsoft Intune에 지정된 &lt;ServerName&gt; 및 **확인**을 순서대로 선택합니다. Apple Portal에서 관리를 위해 지정된 디바이스를 Intune 서버에 할당한 다음 **할당 완료**를 표시합니다.

   Apple Portal에서 **배포 프로그램**&gt;**장비 등록 프로그램**&gt;**할당 기록 보기**로 이동하여 디바이스 목록 및 해당 MDM 서버 할당을 확인합니다.

9. 나중에 참조할 수 있도록 Azure Portal의 Intune에서 이 토큰을 만드는 데 사용된 Apple ID를 제공합니다.

    ![등록 프로그램 토큰을 만드는 데 사용되는 Apple ID를 지정하고 등록 프로그램 토큰을 찾는 스크린샷](./media/device-enrollment-program-enroll-ios/image03.png)

10. **Apple 토큰** 상자에서 인증서(.pem) 파일을 찾은 다음 **열기**, **만들기**를 차례로 선택합니다. 

## <a name="create-an-apple-enrollment-profile"></a>Apple 등록 프로필 만들기
이제 토큰을 설치했으므로 DEP 디바이스의 등록 프로필을 만들 수 있습니다. 디바이스 등록 프로필은 등록 중에 디바이스 그룹에 적용되는 설정을 정의합니다.

1. Azure Portal의 Intune에서 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택합니다.

2. 방금 설치한 토큰을 선택하고, **프로필** > **프로필 만들기**를 선택합니다.

3. **프로필 만들기**에서 **이름**에 *TestDEPProfile*을 입력하고 **설명**에 *iOS 디바이스용 DEP 테스트*를 입력합니다. 사용자는 이러한 세부 정보를 볼 수 없습니다.

4. **사용자 선호도**의 경우 **사용자 선호도를 사용하여 등록**을 선택합니다. 이 옵션은 앱 설치 같은 서비스에 회사 포털을 사용하려는 사용자의 디바이스를 위한 것입니다.

5. **Apple 설정 도우미 대신 회사 포털을 사용하여 인증**에서 **아니요**를 선택합니다.

6. **디바이스 관리 설정**을 선택하고, **감독됨** 아래에서 **아니요**를 선택합니다. 감독되는 디바이스는 더 많은 관리 옵션을 제공하지만 이 자습서의 목적에 맞게 사용되지는 않습니다.

7. **확인**을 선택합니다.

8. **설치 도우미 사용자 지정**을 선택하고 **부서 이름**에 *자습서 부서*를 입력합니다. 이 문자열은 디바이스 정품 인증을 하는 동안 사용자가 **구성 정보**를 탭하는 경우 표시됩니다.

9. **부서 전화**에서 전화 번호를 입력합니다. 이 번호는 정품 인증을 하는 동안 사용자가 **도움이 필요하세요?** 단추를 탭하는 경우 표시됩니다.

10. 디바이스 정품 인증을 하는 동안 다양한 화면을 **표시**하거나 **숨길** 수 있습니다. 이 자습서에서는 **암호**를 **표시**로, 기타 모든 것은 **숨기기**로 설정합니다.

11. **확인** > **만들기**를 선택합니다.

## <a name="sync-managed-devices"></a>관리되는 디바이스 동기화

이제 이 토큰에 할당된 디바이스를 확인할 수 있습니다.

1. Azure Portal의 Intune에서 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 목록에서 토큰을 선택한 다음, **디바이스** > **동기화**를 선택합니다.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>iOS 디바이스에 등록 프로필 할당

먼저 등록 프로그램 프로필을 디바이스에 할당해야 디바이스를 등록할 수 있습니다.

1. Azure Portal의 Intune에서 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택한 다음, 목록에서 토큰을 선택합니다.
2. **디바이스**를 선택하고 목록에서 디바이스를 선택한 다음 **프로필 할당**을 선택합니다.
3. **프로필 할당** 아래에서 디바이스의 프로필 &gt; **할당**을 선택합니다.

## <a name="distribute-devices-to-users"></a>사용자에게 디바이스 배포

Apple과 Intune 간의 동기화 및 관리를 설정했으며, DEP 디바이스를 등록할 수 있는 프로필을 할당했습니다. 이제 사용자에게 디바이스를 배포할 수 있습니다. 사용자 선호도가 있는 디바이스의 경우 각 사용자에게 Intune 라이선스를 할당해야 합니다.

## <a name="clean-up-resources"></a>리소스 정리

더 이상 사용하지 않으려는 경우 Autopilot 디바이스를 삭제할 수 있습니다.

- 디바이스가 Intune에 등록된 경우 먼저 [Azure Active Directory 포털에서 삭제](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)해야 합니다.

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>다음 단계

iOS 디바이스를 등록할 수 있는 기타 옵션에 대한 자세한 정보를 찾을 수 있습니다.

> [!div class="nextstepaction"]
> [자세한 iOS DEP 등록 문서](device-enrollment-program-enroll-ios.md)
