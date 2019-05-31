---
title: Intune 회사 포털을 사용하여 Android 디바이스 등록 | Microsoft Docs
description: Intune 회사 포털을 사용하여 Android 디바이스를 등록하는 방법을 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 736b1d891207a19f281aa1127975de1a55889e8b
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197026"
---
# <a name="enroll-your-device-with-company-portal"></a>회사 포털을 사용하여 디바이스 등록  
개인 또는 회사 소유의 Android 디바이스를 등록하면 회사 이메일, 앱 및 데이터에 안전하게 액세스할 수 있습니다. 회사 포털은 삼성 Knox를 비롯한 Android 4.4 이상을 실행하는 Android 디바이스를 지원합니다.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> 삼성 Knox는 특정 Samsung 디바이스에서 네이티브 Android가 제공하지 않는 추가 보호를 위해 사용하는 보안 유형입니다. 삼성 Knox 디바이스가 있는지 확인하려면 **설정** > **디바이스 정보**로 이동합니다. **Knox 버전**이 표시되지 않는 경우 네이티브 Android 디바이스가 있는 것입니다.

## <a name="enroll-device"></a>디바이스 등록  
[Google Play에서 무료 Intune 회사 포털 앱을 설치](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)합니다. 

등록하는 동안 디바이스 사용 방법을 가장 잘 설명하는 범주를 선택하라는 메시지가 표시될 수도 있습니다. 회사 지원팀은 사용자의 답변을 사용하여 액세스할 수 있는 앱을 확인합니다.  

1. 회사 포털 앱을 엽니다.  

3. 회사 포털의 **시작** 화면에서 **로그인**을 탭한 다음, 회사 또는 학교 계정으로 로그인합니다.

   ![Android용 회사 포털 앱의 시작 화면이며 사용자에게 필수 회사 또는 학교 계정으로 로그인하도록 요청합니다. 또한 Microsoft 계정과 기타 개인 계정은 허용되지 않는다고 주의 사항을 설명합니다.](./media/and-enroll-0-welcome-screen.png)   

4. 조직의 약관을 수락하라는 메시지가 표시되면 **동의**를 탭합니다. 이 화면은 아래 예제 스크린샷과 약간 다를 수 있습니다. 

   ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5. 회사 또는 학교 계정과 암호를 사용하여 회사 포털 앱에 로그인하고 **로그인**을 탭합니다.

   ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6. **회사 액세스 설정** 화면에서 **계속**을 탭합니다.

   ![회사 액세스 설정 화면](/intune/media/android_cp_enroll_01_1709_new.png)

   > [!NOTE]
   > 노란색 삼각형은 이미 오류가 발생했음을 의미하지 않습니다. 이 아이콘은 등록 프로세스에서 완료해야 할 단계가 여전히 남아 있음을 나타냅니다.

7. 회사 지원팀이 디바이스에서 볼 수 있는 사항과 볼 수 없는 사항의 목록을 검토하고 **계속**을 누릅니다.

   ![개인 정보 설정](/intune/media/android_cp_enroll_02_after_1710.png)

8. **다음 단계는?** 화면에서 등록하는 동안 발생하는 상황을 확인하고 **등록**을 누릅니다.

   ![다음 단계는 화면](/intune/media/android_cp_enroll_03_after_1710.png)

9. Android 6.0 이상을 사용하는 경우 이 단계를 수행합니다. 그렇지 않으면 다음 단계로 진행합니다.

   회사 지원팀이 특정 정책을 설정한 경우 다음과 같은 메시지가 표시될 수 있습니다.
   - **회사 포털에서 통화를 하고 전화 통화를 관리하도록 허용하시나요?**

     ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

   이 메시지가 표시되면 **허용**을 탭합니다. **Microsoft는 결코 전화를 걸거나 전화 통화를 관리하지 않으므로** 허용을 탭하는 것이 안전합니다. Google이 메시지 텍스트를 제어하므로 Microsoft에서 변경할 수 없습니다. 액세스를 허용하면 디바이스를 통해 디바이스의 IMEI(International Mobile Station Equipment Identity) 번호를 Intune에 보내도록 허용하기만 하면 됩니다. IMEI 번호는 모바일 디바이스를 고유하게 식별하는 일련 번호와 같습니다.

   액세스를 거부하는 경우 다음에 회사 포털에 로그인할 때 메시지가 다시 표시됩니다. 이후에 메시지가 표시되지 않도록 하려면 **다시 묻지 않음**을 선택합니다. 액세스 권한을 되돌리려면 **설정** > **앱** > **회사 포털** > **사용 권한** > **휴대폰**으로 이동한 다음, 사용 권한을 켭니다.  

   - **회사 포털에 연락처에 대한 액세스를 허용하시나요?**

     ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

     이 메시지가 표시되면 **허용**을 탭합니다. **Microsoft는 결코 연락처에 액세스하지 않으므로** 허용을 탭하는 것이 안전합니다. Google이 메시지 텍스트를 제어하므로 Microsoft에서 변경할 수 없습니다. 액세스를 허용하는 경우 회사 포털 앱을 통해서만 회사 계정을 만들고, 사용하고 관리할 수 있습니다.

     액세스를 거부하면 다음에 회사 포털에 로그인할 때 메시지가 다시 표시되지만, **다시 묻지 않음** 상자를 탭하여 이후 메시지를 해제할 수 있습니다. 사용자가 나중에 액세스를 허용할 경우 **설정** &gt; **앱** &gt; **회사 포털** &gt; **사용 권한** &gt; **전화**로 이동한 다음 사용 권한을 설정합니다.

10. **활성화 디바이스 관리자** 화면에서 **활성화**를 탭합니다.

    ![디바이스 관리자 활성화 화면](./media/and-enroll-5-activate.png)

    디바이스 관리자 역할은 회사 포털에서 디바이스 관리 시 필요한 역할입니다. 이 역할을 사용하면 관리자는 화면 잠금 해제 시도 횟수와 같은 특정 항목을 보고 여러 작업을 수행할 수 있습니다.    

    Microsoft는 이 메시지를 규제하지 않습니다. 또한 이러한 표현이 다소 극단적으로 보일 수도 있음을 알고 있습니다. 하지만 회사 포털에서 조직과 관련된 제한 사항 및 액세스 권한만 표시하는 것은 적절한 방법이 아닙니다. 모든 작업이 이 화면에서 한 번에 제공됩니다. 개별 조직의 사용 관련 질문이 있는 경우 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)의 연락처 정보를 사용하여 회사 지원팀에 자세한 내용을 문의하세요.  

11. 지시에 따라 PIN이나 암호를 입력합니다. 이미 이 디바이스에서 암호나 PIN을 설정했다면 이 화면에 표시되지 않거나 새 PIN이나 암호를 입력할 필요가 없습니다.  

    ![PIN 또는 암호 입력](./media/and-enroll-6-PIN-native.png)

12. Samsung Knox 디바이스를 사용하는 경우 **확인**을 탭하면 디바이스가 등록되고 있음을 나타내는 메시지를 확인할 수 있습니다. 기본 Android 디바이스를 사용하는 경우 디바이스가 등록되고 있음을 보여 주는 다음 화면을 확인할 수 있습니다.

    ![Samsung Knox 개인 정보 취급 방침](./media/and-enroll-7-knox-privacy-policy.png)

    이 화면은 디바이스가 등록되고 있음을 보여 줍니다.

    ![디바이스 등록 화면](./media/and-enroll-8-device-enrolling.png)

13. **회사 액세스 설정** 화면이 나타나면 **계속**을 탭합니다. 디바이스가 규정을 준수하지 않음을 나타내는 메시지가 표시되면 지침에 따라 문제를 해결하고 **계속**을 탭합니다.

    ![디바이스가 비준수 상태이지만 등록되어 있음](/intune/media/android_cp_enroll_05_post_1709.png)

    ![해결이 필요한 디바이스 준수 문제가 나타남](/intune/media/android_cp_enroll_03_post_1709.png)

    탭하여 문제에 대해 더 자세히 확인할 수 있습니다.

    ![디바이스 준수 문제 확장됨](/intune/media/android_cp_enroll_04_post_1709.png)

    ![회사 액세스 설정 화면](./media/and-enroll-9d-comp-access-setup.png)  

14. **회사 액세스 설정 완료** 화면에서 **완료**를 탭합니다. 이제 디바이스가 등록됩니다.

    ![회사 액세스 설정 완료 화면](./media/and-enroll-10-comp-access-setup-complete.png)

## <a name="next-steps"></a>다음 단계  

회사 앱을 설치하기 전에 **설정** > **보안**으로 이동하여 **알 수 없는 원본**을 켭니다. 앱을 설치하기 전에 이 옵션을 설정하지 않으면 "설치가 차단되었습니다. 보안상의 이유로 디바이스가 알 수 없는 소스에서 가져온 앱의 설치를 차단하도록 설정되었습니다."라는 메시지가 표시됩니다. 오류 대화 상자에서 **설정**을 탭하여 **알 수 없는 소스** 옵션으로 이동할 수 있습니다.  

> [!Note]
> 조직에서 TEM(Telecom Expense Management) 소프트웨어를 사용하는 경우 몇 가지 추가 단계를 완료해야 디바이스가 완전히 등록됩니다. 자세한 내용은 [여기](enroll-your-device-with-telecom-expense-management-android.md)를 참조하세요.

Intune에서 디바이스를 등록하는 동안 오류가 발생할 경우 [회사 지원팀에 이메일로 보낼](send-logs-to-your-it-admin-by-email-android.md) 수 있습니다.  

여전히 도움이 필요하세요? 회사 지원팀에 문의하거나(연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 확인) <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 팀</a>으로 메일을 보내세요.
