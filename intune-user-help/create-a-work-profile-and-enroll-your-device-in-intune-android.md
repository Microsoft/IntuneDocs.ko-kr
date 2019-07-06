---
title: Android 회사 프로필을 사용하여 디바이스 등록 | Microsoft Docs
description: 회사 프로필을 만들고 디바이스를 등록하는 방법
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 33ffff16-0280-43bf-87b3-74ddf4439bfa
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0a8b0b633f64a2ed6e3e14d5d884df80342067a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545476"
---
# <a name="enroll-device-with-android-work-profile"></a>Android 회사 프로필을 사용하여 디바이스 등록

개인 Android 디바이스를 등록하면 회사 이메일, 앱 및 기타 업무용 데이터에 액세스할 수 있습니다. 등록하는 동안 Android 회사 프로필을 설정할 수 있습니다. 이 프로필은 사용자 디바이스에서 개인 데이터와 회사 데이터를 구분합니다. 회사 지원팀은 회사 파일 및 데이터로 구성된 회사 프로필만 관리합니다. 회사 지원팀은 사용자 디바이스의 개인 데이터를 관리할 수 없습니다. [업무용 프로필을 만들면 어떻게 되나요?](what-happens-when-you-create-a-work-profile-android.md)에서 자세한 내용을 알아보세요.  
</br>
> [!VIDEO https://www.youtube.com/embed/9Dl8HsGk4tI?rel=0]

## <a name="create-work-profile-and-enroll-device"></a>회사 프로필 만들기 및 디바이스 등록

1. Android 회사 포털의 **시작** 화면에서 **로그인**을 탭한 다음, 회사 또는 학교 계정으로 로그인합니다. 무료 앱을 아직 설치하지 않은 경우 [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)에서 다운로드하여 설치합니다.

    ![Android 회사 포털 앱 시작 화면](./media/and-enroll-0-welcome-screen.png)

2. **회사 액세스 설정** 화면에서 **계속**을 탭합니다.

    ![회사 액세스 설정 화면](/intune/media/android_cp_enroll_01_1709_new.png)

3. **업무용 프로필을 만드는 이유** 화면에서 수행할 수 있는 작업을 확인하고 **계속**을 탭합니다.

    ![업무용 프로필을 만드는 이유](./media/andr-afw-why-create-a-work-profile.png)

4. 회사 지원팀이 디바이스에서 볼 수 있는 사항과 볼 수 없는 사항의 목록을 검토하고 **계속**을 누릅니다.

    ![회사 지원팀이 디바이스에서 볼 수 있는 항목과 볼 수 없는 항목](/intune/media/android_cp_enroll_02_after_1710.png)

5. **다음 단계는?** 화면에서 등록하는 동안 발생하는 상황을 확인하고 **등록**을 누릅니다.

    ![다음 단계 화면](/intune/media/android_work_cp_enroll_03_after_1710.png)

6. **업무용 프로필 설정** 화면에서 **다음**을 탭하여 회사 포털 앱에서 업무용 프로필에 액세스할 수 있도록 합니다.

    ![업무용 프로필에 회사 포털 앱 액세스 권한 제공](./media/andr-afw-tap-next-to-set-up-work-profile.png)

7. 업무용 프로필을 만들 때 회사 지원팀이 수행할 수 있는 작업에 대해 설명하는 Google 화면의 내용을 검토하고 **확인**을 누릅니다.

    ![업무용 프로필에 대한 Google의 정보를 검토합니다.](./media/andr-afw-google-screen-what-it-can-do.png)

    "업무용 프로필 설정 중" 및 "디바이스 등록 중" 등 여러 메시지가 표시됩니다.

8. **절반쯤 처리되었습니다.** 화면에서 회사 포털 앱이 열릴 때까지 몇 초 동안 대기합니다.

    ![배지가 있는 회사 포털 앱 탭하기](./media/andr-afw-tap-work-badged-company-portal-icon2.png)

9. Android 회사 포털의 **시작** 화면에서 **로그인**을 탭한 다음 이 프로세스 초반에 로그인할 때 사용한 동일한 회사 또는 학교 계정을 사용하여 로그인합니다.

10. **회사 액세스 설정** 화면에서 업무용 프로필 설정이 완료되었음을 확인한 다음 **계속**을 탭합니다.

    ![회사 액세스 설정에 업무용 프로필 설치가 완료되었음이 표시됨](./media/andr-afw-work-profile-now-set-up.png)

    "디바이스 등록 중."이라는 메시지가 간단하게 표시됩니다.

11. **모든 설정이 끝났습니다.** 화면에서 모든 항목이 올바르게 설정되었음을 보여 주면 **완료**를 누릅니다.

    ![회사 액세스 설정에 업무용 프로필 및 등록이 완료되었음이 표시됨](/intune/media/android_work_cp_enroll_04_after_1710.png)

    이제 Play Store for Work에서 회사 앱을 다운로드할 수 있습니다.

    ![Play Store for Work 앱 페이지](./media/andr-afw-tap-work-play-store-icon.png)

## <a name="next-steps"></a>다음 단계  

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
