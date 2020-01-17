---
title: Intune 회사 포털을 사용하여 Android 디바이스 등록 | Microsoft Docs
description: Intune 회사 포털을 사용하여 Android 디바이스를 등록하는 방법을 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: e0a2297509d6077d6508adaab96ae6eb3cf9b28f
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856737"
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

1. 회사 포털 앱을 열고 회사 또는 학교 계정으로 로그인합니다.  

2. 조직의 약관을 수락하라는 메시지가 표시되면 **모두 동의**를 탭합니다.  

   ![회사 포털, 용어 화면, "모두 수락" 단추를 강조 표시 하는 예제 이미지입니다.](./media/accept-terms-1911.png)  


3. 조직에서 볼 수 있거나 볼 수 없는 내용을 검토 합니다. 그런 다음, **계속**을 탭합니다.


    ![회사 포털 이미지 예, 사용자의 개인 정보 화면에서 계속 단추를 강조 표시 합니다.](./media/android-privacy-screen-1911.png)  
4. 예정 된 단계에서 예측할 사항을 검토 합니다. 그런 후 **다음**을 탭 합니다.  

    ![회사 포털 이미지 예: 다음 단계는 다음 단추를 강조 표시 합니다.](./media/android-whats-next-1911.png)  


5. Android 버전에 따라 장치의 특정 부분에 대 한 액세스를 허용 하 라는 메시지가 표시 될 수 있습니다. 이러한 메시지는 Google에서 필요 하며 Microsoft에서 제어 하지 않습니다.  

    다음 사용 권한에 대해 **허용** 을 탭 합니다.  
    * **전화 통화를 만들고 관리 하는 회사 포털 허용**:이 사용 권한을 통해 장치는 조직의 장치 관리 공급자 인 Intune을 사용 하 여 국제 IMEI (모바일 스테이션 장비 id) 번호를 공유할 수 있습니다. 이 사용 권한을 허용 하는 것이 안전 합니다. Microsoft는 전화 통화를 수행 하거나 관리 하지 않습니다.  
    * **회사 포털 연락처에 액세스할 수 있도록 허용**:이 사용 권한을 통해 회사 포털 앱에서 회사 계정을 만들고, 사용 하 고, 관리할 수 있습니다.  이 사용 권한을 허용 하는 것이 안전 합니다. Microsoft는 귀하의 연락처에 액세스 하지 않습니다. 

    권한을 거부 하는 경우 다음에 회사 포털에 로그인 할 때 메시지가 다시 표시 됩니다. 이러한 메시지가 표시되지 않도록 하려면 **다시 묻지 않음**을 선택합니다. 앱 사용 권한을 관리 하려면 설정 앱 > **앱** > **회사 포털** > **권한** > **휴대폰**으로 이동 합니다.  

6. 장치 관리 앱을 활성화 합니다. 

    장치를 안전 하 게 관리 하려면 회사 포털 장치 관리자 권한이 필요 합니다. 앱을 활성화 하면 조직에서 장치의 잠금을 해제 하는 데 실패 한 반복적인 시도와 같은 잠재적인 보안 문제를 식별 하 고 적절 하 게 응답할 수 있습니다.  

    ![활성화 단추를 강조 표시 하는 장치 관리자 활성화 화면의 예제 이미지](./media/activate-device-administrator-1911.png)  

> [!NOTE]
> Microsoft는이 화면에서 메시징을 제어 하지 않습니다. 이러한 구문에는 약간의 차이가 있을 수 있습니다. 회사 포털 조직과 관련 된 제한 및 액세스를 지정할 수 없습니다. 조직에서 앱을 사용 하는 방법에 대 한 질문이 있는 경우 IT 지원 담당자에 게 문의 하세요. [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)로 이동하면 귀사의 연락처 정보를 찾을 수 있습니다.  


7. 장치를 등록 하기 시작 합니다. Samsung Knox 장치를 사용 하는 경우 먼저 느릅나무 에이전트 개인 정보 취급 방침을 검토 하 고 승인 하 라는 메시지가 표시 됩니다.   

    ![등록 하는 동안 표시 되는 Samsung Knox 개인 정보 취급 방침 화면의 예제 이미지입니다.](./media/and-enroll-7-knox-privacy-policy.png)  

8. **회사 액세스 설정** 화면에서 장치가 등록 되어 있는지 확인 합니다. 그런 다음, **계속**을 탭합니다.  

    ![장치 관리를 완료 하는 것을 보여 주는 회사 포털, 회사 액세스 설정 화면의 예 이미지입니다.](./media/update-settings-1911.png)  

9. 조직에서 장치 설정을 업데이트 해야 할 수 있습니다. **확인** 을 탭 하 여 설정을 조정 합니다. 설정 업데이트가 완료 되 면 **계속**을 탭 합니다.  

   ![회사 포털 이미지 예: 장치 설정 업데이트, 해결 및 계속 단추 강조 표시](./media/resolve-settings-1911.png)  

10. 설치가 완료 되 면 **완료**를 탭 합니다.    

    ![회사 포털, 회사 액세스 설정 화면의 예제 이미지를 사용 하 여 완료 된 설정 및 작업 강조 표시 단추를 표시 합니다.](./media/android-enrollment-done-1911.png) 

## <a name="next-steps"></a>다음 단계  

학교 또는 업무용 앱을 설치 하기 전에 **설정** > **보안**으로 이동 하 여 **알 수 없는 소스**를 설정 합니다. 이 옵션을 설정하지 않으면 앱을 설치하려고 할 때 “설치가 차단되었습니다. 보안상의 이유로 디바이스가 알 수 없는 소스에서 가져온 앱의 설치를 차단하도록 설정되었습니다."라는 메시지가 표시됩니다. 메시지의 **설정** 을 탭 하 여 **알 수 없는 원본**으로 직접 이동할 수 있습니다.  

> [!Note]
> 조직에서 TEM(Telecom Expense Management) 소프트웨어를 사용하는 경우 몇 가지 추가 단계를 완료해야 디바이스가 완전히 등록됩니다. 자세한 내용은 [여기](enroll-your-device-with-telecom-expense-management-android.md)를 참조하세요.

Intune에서 디바이스를 등록하는 동안 오류가 발생할 경우 [회사 지원팀에 이메일로 보낼](send-logs-to-your-it-admin-by-email-android.md) 수 있습니다.  

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.  