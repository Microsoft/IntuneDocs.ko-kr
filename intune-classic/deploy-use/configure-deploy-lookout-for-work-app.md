---
title: Lookout for Work 앱 배포
description: Android용 Lookout for Work 앱을 구성하고 배포합니다.
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/21/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d997e9db7aa2af4e598d47ab3c9a678e889632e8
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34569394"
---
# <a name="configure-and-deploy-lookout-for-work-app"></a>Lookout for Work 앱 구성 및 배포

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

이 문서에서는 Android 및 iOS 장치에서 Lookout for Work 앱을 구성하고 배포하는 방법을 설명합니다.

## <a name="android-google-play-store-app"></a>Android(Google Play 스토어 앱)

1. [Microsoft Intune 관리자 콘솔](https://manage.microsoft.com)에서 **앱**으로 이동하고 **앱 추가**를 선택합니다.
2. 게시자의 **소프트웨어 설정** 페이지에서 **외부 링크**를 선택하고, 다음 URL을 지정하합니다. https://play.google.com/store/apps/details?id=com.lookout.enterprise
   >[!NOTE]
   >관리되는 브라우저가 필요한 상자는 클릭하지 마세요.

3. **소프트웨어 설명** 페이지에서 다음 정보를 입력합니다.
   * **게시자:** Lookout Mobile Security
   * **이름:** Lookout for Work
   * **설명:** Lookout은 우수한 보호 기능으로 장치를 모바일 위협으로부터 안전하게 지켜줍니다. Lookout 앱을 장치에 설치하면 앱이 위협으로부터 장치를 보호하고 위협을 발견하면 사용자는 물론, 사용자의 회사 관리자에게 알려줍니다.
   * **범주:** 컴퓨터 관리

4. 완료하면 **Microsoft Intune으로 데이터를 업로드했습니다.** 라는 메시지가 나타납니다.

   Intune 콘솔에서 **앱**을 클릭하면 목록에 **Lookout for Work** 앱이 표시됩니다. ![목록에 나타난 Lookout for work 앱을 보여주는 Intune 관리 콘솔 앱 페이지의 스크린샷](../media/mtp/lookout-app-listed-intune-console.png)

5. Lookout for Work 앱을 선택하고 **배포 관리**를 선택하여 사용자에게 앱을 배포합니다.

   Lookout MTP 콘솔의 등록 관리 옵션에 추가한 사용자와 동일한 사용자를 선택해야 합니다.  Lookout MTP에 사용자 그룹을 추가하는 방법에 대한 정보는 [Lookout MTP 구독 구성 섹션](configure-deploy-lookout-for-work-app.md)에 나온 3단계를 참조하세요.

   >[!IMPORTANT]
   > Intune 앱 배포 마법사는 Azure AD 사용자 그룹을 인식하지 못하기 때문에 Intune 사용자 그룹을 대신 사용합니다. 따라서 [이](plan-your-user-and-device-groups.md) 항목에 설명한 대로, Lookout MTP 콘솔에 등록된 Azure AD 사용자 그룹을 기반으로 Intune 사용자 그룹을 만들어야 합니다.

6. Lookout 앱을 사용자 장치에 설치하도록 하는 **필수 설치** 옵션를 선택합니다.

## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS(Lookout 앱의 엔터프라이즈 서명된 버전)

1. 장치에 **iOS 관리**가 설정되어 있는지 확인합니다. iOS 관리용으로 장치를 설정하는 방법에 대한 자세한 내용은 [iOS 및 Mac 장치 관리 설정](set-up-ios-and-mac-management-with-microsoft-intune.md)을 참조하세요.

2. Lookout for Work iOS 앱을 **다시 서명**합니다. Lookout에서는 iOS App Store 외부에 Lookout for Work iOS 앱을 배포합니다. **앱을 배포하기 전에** iOS 엔터프라이즈 개발자 인증서를 사용하여 앱에 다시 서명해야 합니다. Lookout for Work iOS 앱에 다시 서명하는 방법에 대한 자세한 내용은 Lookout 사이트에서 [Lookout for Work iOS 앱 다시 서명 프로세스](https://personal.support.lookout.com/hc/articles/114094038714)를 참조하세요.

3. 다음을 수행하여 iOS 사용자에게 Azure Active Directory 인증을 사용하도록 설정합니다.
   1.  [Azure Active Directory 관리 포털](https://manage.windowsazure.com)에 로그인하여 응용 프로그램 페이지로 이동합니다.
   2.  **Lookout for Work iOS 앱**을 **네이티브 클라이언트 응용 프로그램**으로 추가합니다.
   ![네이티브 클라이언트 앱 옵션을 보여 주는 앱 추가 대화 상자 스크린샷](../media/mtp/aad-add-app.png)
   3. **com.lookout.enterprise.yourcompanyname**을 IPA에 서명할 때 선택한 고객 번들 ID로 바꿉니다.
   4.  원래 리디렉션 URI의 URL 인코드된 버전을 뒤에 추가하여 다른 리디렉션 URI(**&lt;companyportal://code/>**)를 추가합니다.
   5.  **위임된 권한**을 앱에 추가합니다.

   자세한 내용은 [네이티브 클라이언트 응용 프로그램을 구성](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)을 참조하세요.

4. [Microsoft Intune에서 모바일 장치용 앱 추가](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) 항목에 설명된 대로 다시 서명된 .ipa 파일을 업로드합니다. 최소 OS 버전을 iOS 8.0 이상으로 설정합니다.

   ![앱 목록에 표시되는 Lookout for Work 앱이 포함된 Intune 관리자 콘솔의 앱 페이지 스크린샷](../media/mtp/ios-app-uploaded-intune.png)

5. [Microsoft Intune에서 모바일 앱 구성 정책을 사용하여 iOS 앱 구성](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune) 항목에 설명된 대로 관리되는 앱 구성 정책을 만듭니다.

   ![iOS 8.0 이상 앱 구성 정책이 강조 표시된 새 정책 마법사의 스크린샷](../media/mtp/ios-app-config.png)

6. **사용자에게 앱을 배포하려면** Lookout for Work 앱을 선택하고 **배포 관리**를 선택합니다.

   Lookout  콘솔의 등록 관리 옵션에 추가된 사용자와 동일한 사용자를 선택해야 합니다.  Lookout MTP에 사용자 그룹을 추가하는 방법에 대한 자세한 내용은 [Lookout 구독 섹션 구성](https://docs.microsoft.com/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps)에 나온 3단계를 참조하세요.

   >[!IMPORTANT]
   > Intune 앱 배포 마법사는 Azure AD 사용자 그룹을 인식하지 못하기 때문에 Intune 사용자 그룹을 대신 사용합니다. 따라서 [이](plan-your-user-and-device-groups.md) 항목에 설명한 대로, Lookout 콘솔에 등록된 Azure AD 사용자 그룹을 기반으로 Intune 사용자 그룹을 만들어야 합니다.

   Lookout 앱을 사용자 장치에 설치하도록 하는 **필수 설치** 옵션를 선택합니다.

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>장치에서 배포된 앱을 열 때 수행되는 작업 
사용자가 장치에서 Lookout for Work를 열면 앱을 활성화하고 Azure Active Directory를 사용하여 로그인 옵션을 선택하라는 메시지가 표시됩니다. 최종 사용자 흐름을 사용하는 자세한 연습은 다음 항목에서 확인할 수 있습니다.

* [Android 장치에 Lookout for Work를 설치하라는 메시지가 표시됨](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)
    
* [Lookout for Work가 Android 장치에서 발견한 위협을 해결해야 함](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>다음 단계
* [Intune에서 Lookout 장치 준수 정책 만들기](https://docs.microsoft.com/sccm/protect/deploy-use/enable-device-threat-protection-rule-compliance-policy)
