---
title: Android 엔터프라이즈 디바이스에 관리되는 Google Play 앱 할당
titleSuffix: Microsoft Intune
description: 관리되는 Google Play 스토어에서 Android 엔터프라이즈 디바이스에 앱을 동기화하고 할당하는 방법을 파악합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbcc777cc6d8b803c502d847114ef7cff04ceb26
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725337"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Intune을 사용하여 Android 엔터프라이즈 디바이스에 관리되는 Google Play 앱 추가

관리되는 Google Play는 Google의 엔터프라이즈 앱 스토어이며 Android 엔터프라이즈용 응용 프로그램의 유일한 출처입니다. Intune을 사용하여 Android 엔터프라이즈 시나리오(회사 프로필, 전용 및 완전 관리형 등록 포함)에 대한 관리되는 Google Play를 통해 앱 배포를 오케스트레이션할 수 있습니다. Intune에 관리되는 Google Play 앱을 추가하는 방법은 Android 외 Enterprise에 Android 앱을 추가하는 방법과 다릅니다. 스토어 앱, LOB(기간 업무) 앱 및 웹앱은 관리되는 Google Play에서 승인되거나 그에 추가된 후 Intune으로 동기화되어 클라이언트 앱 목록에 표시됩니다. 클라이언트 앱 목록에 표시되면 다른 앱과 마찬가지로 관리되는 Google Play 앱의 할당을 관리할 수 있습니다.

Android 엔터프라이즈 관리를 더 쉽게 구성하고 사용할 수 있도록 Intune에서는 Intune 테넌트를 관리되는 Google Play에 연결하자마자 일반적인 Android 엔터프라이즈 관련 앱 4개를 Intune 관리자 콘솔에 자동으로 추가합니다. 이 네 가지 앱은 다음과 같습니다.

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise완전 관리형 시나리오에 사용합니다. 이 앱은 디바이스 등록 프로세스 중에 완전 관리형 디바이스에 자동으로 설치됩니다.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 2단계 인증을 사용하는 경우 계정에 로그인할 수 있도록 지원합니다. 이 앱은 디바이스 등록 프로세스 중에 완전 관리형 디바이스에 자동으로 설치됩니다.
- **[Intune 회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - APP(앱 보호 정책) 및 Android Enterprise 작업 프로필 시나리오에 사용합니다.
- **[관리 홈 화면](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** - Android 엔터프라이즈 전용 다중 앱 키오스크 시나리오에 사용합니다. IT 관리자는 할당을 만들어 다중 앱 키오스크 시나리오에서 사용할 전용 디바이스에 이 앱을 설치해야 합니다.

>[!NOTE]
>최종 사용자가 Android 엔터프라이즈 완전 관리형 디바이스를 등록하면 Intune 회사 포털 앱이 자동으로 설치되고 응용 프로그램 아이콘이 최종 사용자에게 표시됩니다. 최종 사용자가 Intune 회사 포털 앱을 시작하려고 하면 최종 사용자는 Microsoft Intune 앱으로 리디렉션되고 이어서 회사 포털 앱 아이콘이 숨겨집니다.

## <a name="before-you-start"></a>시작하기 전에
- 관리되는 Google Play에 Intune 테넌트를 연결했는지 확인합니다.  자세한 내용은 [Intune 계정을 관리형 Google Play 계정에 연결](../enrollment/connect-intune-android-enterprise.md)을 참조하세요.
- 회사 프로필 디바이스를 등록하려면 Intune과 Android 회사 프로필이 Azure Portal의 **디바이스 등록** 워크로드에서 함께 작동하도록 구성했는지 확인합니다. 자세한 내용은 [Android 디바이스 등록](../enrollment/android-work-profile-enroll.md)을 참조하세요.

>[!NOTE]
>Microsoft Intune에서 작업하는 경우 Microsoft Edge 또는 Google Chrome 브라우저를 사용하는 것이 좋습니다.

## <a name="managed-google-play-app-types"></a>관리되는 Google Play 앱 유형
관리되는 Google Play에서 사용할 수 있는 앱에는 다음과 같이 세 가지 유형이 있습니다.

* **관리되는 Google Play 스토어 앱** - Play 스토어에서 일반적으로 사용할 수 있는 공개 앱입니다. 관리하려는 앱을 찾아 승인한 후 Intune에 동기화하여 Intune에서 관리할 수 있습니다.
* **관리되는 Google Play 비공개 앱** - 관리되는 Google Play에 Intune 관리자가 게시한 LOB 앱입니다.  비공개 앱이며 Intune 테넌트에만 사용할 수 있습니다. 이는 관리되는 Google Play 및 Android 엔터프라이즈를 사용하여 LOB 앱을 관리하고 배포하는 방법입니다.
* **관리되는 Google Play 웹 링크** - Android 엔터프라이즈 디바이스에 배포 가능한 IT 관리자 정의 아이콘의 웹 링크입니다. 이러한 웹 링크는 일반 앱과 마찬가지로 디바이스의 앱 목록에 있는 디바이스에 표시됩니다.

## <a name="managed-google-play-store-apps"></a>관리되는 Google Play 스토어 앱
관리되는 Google Play 스토어 앱을 Intune을 사용해 찾고 승인하는 방법에는 다음과 같이 두 가지가 있습니다.

1. Intune 콘솔에서 직접 찾아 승인하는 방법 - Intune 내에서 호스팅되는 뷰에서 스토어 앱을 찾고 승인합니다. 이 뷰는 Intune 콘솔에서 직접 열리며 다른 계정으로 다시 인증하지 않아도 됩니다.
1. 관리되는 Google Play 콘솔에서 찾아 승인하는 방법 - 원하는 경우 관리되는 Google Play 콘솔을 직접 열어 여기에서 앱을 승인합니다. 자세한 내용은 [관리되는 Google Play 앱을 Intune과 동기화](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)를 참조하세요.  이렇게 하려면 Intune 테넌트를 관리되는 Google Play에 연결하는 데 사용한 계정을 사용하여 별도로 로그인해야 합니다.


### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>관리되는 Google Play 스토어 앱을 Intune 콘솔에서 직접 추가

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **클라이언트 앱** > **앱**을 선택합니다.
5. **앱** 창에서 **추가**를 선택합니다.
6. **앱 유형** 드롭다운 상자에서 **관리되는 Google Play**를 선택합니다.
7. **관리되는 Google Play - 열기**를 선택하여 관리되는 Google Play 카탈로그를 엽니다.
7. Google Play 카탈로그에서 **Play 스토어 검색**을 선택합니다.
8. 검색 상자를 사용하여 관리하려는 앱을 검색합니다.
9. **승인**을 클릭하여 관리되는 Google Play에서 앱을 승인하고 **승인**을 클릭하여 앱 권한을 허용합니다.
10. [승인 설정] 창에서 **앱이 새 권한을 요청할 때 승인 유지**를 선택한 후 **저장**을 클릭합니다. 이 옵션을 선택하지 않으면, 앱 개발자가 업데이트를 게시하는 경우, 새 권한을 수동으로 승인해야 합니다. 이렇게 하면 권한이 승인될 때까지 설치 및 업데이트가 중지됩니다. 이런 이유로 새 권한을 자동으로 승인하도록 옵션을 선택하는 것이 좋습니다. 
11. **확인**을 클릭하여 승인한 앱을 포함합니다.
12. **APP 앱** 창에서 **동기화**를 클릭하여 관리되는 Google Play 서비스와 동기화합니다.

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>관리되는 Google Play 콘솔에서 관리되는 Google Play 스토어 앱 추가(대안)
Intune을 사용하여 직접 추가하는 것이 아니라 Intune을 사용하여 관리되는 Google Play 앱을 동기화하려는 경우 다음 단계를 사용합니다.

> [!IMPORTANT]
> 아래에 제공된 정보는 위에 설명된 대로 Intune을 사용하여 관리되는 Google Play 앱을 추가하는 대체 방법입니다.

1. [관리되는 Google Play 스토어](https://play.google.com/work)로 이동합니다. Intune과 Android 엔터프라이즈 간 연결을 구성하는 데 사용한 계정으로 로그인합니다.
2. Intune을 사용하여 스토어를 검색하고 할당할 앱을 선택합니다.
3. 앱을 표시하는 페이지에서 **승인**을 선택합니다.  
    다음 예제에서는 Microsoft Excel 앱이 선택되었습니다.

    ![관리되는 Google Play 스토어의 승인 단추](./media/apps-add-android-for-work/approve.png)

   앱 창이 열리면서 앱에서 다양한 작업을 수행할 수 있는 권한을 부여하라는 메시지가 표시됩니다.

4. **승인**을 선택하여 앱 사용 권한에 동의하고 계속합니다.

    ![앱 권한에 대한 승인 단추](./media/apps-add-android-for-work/approve-app-permissions.png)

5. 새로운 앱 권한 요청을 처리하는 옵션을 선택한 다음 **저장**을 선택합니다.

    ![새로운 앱 권한 요청을 처리하는 옵션](./media/apps-add-android-for-work/approve-app-settings.png)

    앱이 승인되어 IT 관리 콘솔에 표시됩니다. 그런 다음 [Android 회사 프로필 앱을 Intune과 동기화](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)할 수 있습니다.

## <a name="managed-google-play-private-lob-apps"></a>관리형 Google Play 비공개(LOB) 앱

관리되는 Google Play에 LOB 앱을 추가하는 방법에는 다음과 같이 두 가지가 있습니다.

1. Intune 콘솔에서 직접 추가하는 방법 - Intune 내에서 직접 앱 APK 및 제목만 제출하여 LOB 앱을 추가할 수 있습니다. 이 방법의 경우 Google 개발자 계정이 필요 없고 개발자로 Google에 등록할 때 요금을 지불하지 않아도 됩니다.  이 방법은 더 간단하고 거쳐야 할 단계가 상당히 줄어들어 10분 내에 LOB 앱을 관리할 수 있습니다.
1. Google Play 개발자 콘솔에서 추가하는 방법 - Google 개발자 계정이 있거나 Google Play 개발자 콘솔에서만 사용할 수 있는 고급 배포 기능을 구성하려는 경우(예: 앱 스크린샷 추가) [Google Play 개발자 콘솔](https://play.google.com/apps/publish)을 사용하면 됩니다. 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>관리되는 Google Play 비공개(LOB) 앱을 Intune 콘솔에서 직접 게시

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **클라이언트 앱** > **앱**을 선택합니다.
5. **앱** 창에서 **추가**를 선택합니다.
6. **앱 유형** 드롭다운 상자에서 **관리되는 Google Play**를 선택합니다.
7. **관리되는 Google Play - 열기**를 선택하여 관리되는 Google Play 카탈로그를 엽니다.
7. Google Play 카탈로그에서 **비공개 앱**을 선택합니다.
7. **"+"** 단추를 클릭하여 새 앱을 추가합니다.
8. 앱에 대한 앱 제목 및 APK 패키지 제출
9. **만들기**를 클릭합니다.
9. 앱 추가를 완료했으면 관리되는 Google Play 창을 닫습니다.
12. **APP 앱** 창에서 **동기화**를 클릭하여 관리되는 Google Play 서비스와 동기화합니다. 비공개 앱은 동기화할 준비가 완료되는 데 몇 분 정도 걸릴 수 있습니다. 동기화를 처음 수행할 때 표시되지 않으면 몇 분 기다렸다가 새 동기화를 시작합니다.

FAQ를 비롯해 관리되는 Google Play 비공개 앱에 대한 자세한 내용은 Google의 지원 문서를 참조하세요. https://support.google.com/googleplay/work/answer/9146439

>[!NOTE]
>이 메서드를 사용하여 추가한 비공개 앱은 공개로 변경할 수 없습니다. 이 앱이 항상 조직 전용으로 사용되는 경우에만 이 게시 옵션을 사용하세요.
  

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>관리되는 Google Play 비공개(LOB) 앱을 Google 개발자 콘솔을 사용하여 게시

1. Intune과 Android 엔터프라이즈 간 연결을 구성하는 데 사용한 것과 동일한 계정으로 [Google Play 개발자 콘솔](https://play.google.com/apps/publish)에 로그인합니다.  
    처음 로그인하는 경우 Google Developer 프로그램 구성원이 되기 위해 등록하고 요금을 지불해야 합니다.
2. 콘솔에서 **새 애플리케이션 추가**를 선택합니다.
3. Google Play 스토어에 앱을 게시한 것과 동일한 방법으로 앱에 대한 정보를 업로드하고 제공합니다. 단, **이 애플리케이션을 내 조직만 사용(&lt;*조직 이름*&gt;)** 을 선택해야 합니다.

    ![내 조직에서만 앱을 사용할 수 있도록 설정](./media/apps-add-android-for-work/restrict.png)

    이 작업을 수행하면 조직에서만 앱을 사용할 수 있습니다. 공개 Google Play 스토어에서는 사용할 수 없습니다.

    Android 앱을 업로드 및 게시하는 방법에 대한 자세한 내용은 [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469)(Google 개발자 콘솔 도움말)를 참조하세요.
4. 앱을 게시했으면 Intune과 Android 엔터프라이즈 간 연결을 구성하는 데 사용한 것과 동일한 계정으로 [관리되는 Google Play 스토어](https://play.google.com/work)에 로그인합니다.
5. 스토어의 **앱** 노드에서 게시한 앱이 표시되는지 확인합니다.  
    앱이 Intune와 동기화되도록 자동으로 승인됩니다.

## <a name="managed-google-play-web-links"></a>관리되는 Google Play 웹 링크

관리되는 Google Play 웹 링크는 다른 Android 앱과 마찬가지로 설치 및 관리가 가능합니다. 디바이스에 설치된 경우 사용자가 설치한 다른 앱과 함께 사용자의 앱 목록에 표시됩니다. 웹 링크를 탭하면 디바이스의 브라우저에서 시작됩니다.

웹 링크는 Microsoft Edge 또는 배포하도록 선택한 다른 브라우저 앱에서 열립니다. 웹 링크를 제대로 열려면 하나 이상의 브라우저 앱을 디바이스에 배포해야 합니다. 그러나 웹 링크(전체 화면, 독립 실행형 및 최소 UI)에서 사용할 수 있는 모든 **디스플레이** 옵션은 크롬 브라우저에서만 작동합니다. 

> [!IMPORTANT]
> 이 문서를 게시할 때 웹 링크가 디바이스에서 크롬 이외의 브라우저로는 열리지 않게 방해하는 알려진 Google 버그가 있습니다. Google은 이 버그를 수정하기로 약속했습니다.  이 알림은 Microsoft가 Google에서 수정을 게시했음을 확인하면 제거됩니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **클라이언트 앱** > **앱**을 선택합니다.
5. **앱** 창에서 **추가**를 선택합니다.
6. **앱 유형** 드롭다운 상자에서 **관리되는 Google Play**를 선택합니다.
7. **관리되는 Google Play - 열기**를 선택하여 관리되는 Google Play 카탈로그를 엽니다.
7. Google Play 카탈로그에서 **웹앱**을 선택합니다.
7. **"+"** 단추를 클릭하여 새 앱을 추가합니다.
7. 필요한 정보를 입력한 다음 **만들기**를 클릭합니다.
7. 앱 추가를 완료했으면 관리되는 Google Play 창을 닫습니다.
12. **APP 앱** 창에서 **동기화**를 클릭하여 관리되는 Google Play 서비스와 동기화합니다. 비공개 앱은 동기화할 준비가 완료되는 데 몇 분 정도 걸릴 수 있습니다. 동기화를 처음 수행할 때 표시되지 않으면 몇 분 기다렸다가 새 동기화를 시작합니다.

## <a name="sync-a-managed-google-play-app-with-intune"></a>Intune과 관리되는 Google Play 앱 동기화

스토어에서 앱을 승인했지만 **클라이언트 앱** 워크로드에 표시되지 않으면 다음과 같이 강제로 즉시 동기화합니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드 창의 **설정** 아래에서 **관리되는 Google Play**를 선택합니다.
5. **관리되는 Google Play** 창에서 **새로 고침**을 선택합니다.  
    페이지에서 마지막 동기화의 시간 및 상태가 업데이트됩니다.
6. **클라이언트 앱** 워크로드 창에서 **앱**을 선택합니다.  
    새로 사용 가능한 관리되는 Google Play 앱이 표시됩니다.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>관리되는 Google Play 앱을 Android 엔터프라이즈 회사 프로필 디바이스에 할당

**클라이언트 앱** 워크로드 창의 **앱 라이선스** 노드에 앱이 표시되면 앱을 사용자 그룹에 할당하여 [다른 앱과 마찬가지로 앱을 할당](/intune-azure/manage-apps/deploy-apps)할 수 있습니다.

앱을 할당하고 나면 대상으로 지정한 사용자의 디바이스에 앱이 설치되거나 설치할 준비가 됩니다. 디바이스 사용자에게 설치 승인을 요청하지 않습니다. Android 엔터프라이즈 회사 프로필 디바이스에 대한 자세한 내용은 [Android 엔터프라이즈 회사 프로필 디바이스의 등록 설정](../enrollment/android-work-profile-enroll.md)을 참조하세요. 

> [!NOTE] 
> 할당된 앱만 최종 사용자의 관리되는 Google Play 스토어에 표시됩니다. 이것은 관리되는 Google Play를 사용하여 앱을 설정할 때 관리자가 수행해야 하는 주요 단계입니다.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>관리되는 Google Play 앱을 Android 엔터프라이즈 완전 관리형 디바이스에 할당

[Android 엔터프라이즈 완전 관리형 디바이스](../enrollment/android-fully-managed-enroll.md)는 단일 사용자와 연결되는 회사 소유 디바이스로, 개인 용도가 아닌 업무용으로만 사용됩니다. 완전 관리형 디바이스의 사용자는 자기 디바이스의 관리되는 Google Play 앱에서 사용 가능한 회사 앱을 가져올 수 있습니다.

기본적으로 Android 엔터프라이즈 완전 관리형 디바이스에서는 직원이 조직의 승인을 받지 않은 앱을 설치하도록 허용하지 않습니다. 또한 직원은 설치된 앱을 정책에 반하여 제거할 수 없습니다. 사용자가 관리되는 Google Play 스토어에서 승인된 앱에만 액세스하는 것이 아니라 전체 Google Play 스토어에 액세스하여 앱을 설치할 수 있게 허용하려면 **Google Play 스토어의 모든 앱에 대한 액세스 허용**을 **허용**으로 설정하면 됩니다. 이렇게 설정하면 사용자는 회사 계정을 사용하여 Google Play 스토어의 모든 앱에 액세스할 수 있습니다. 하지만 구매는 제한될 수 있습니다. 사용자가 디바이스에 새 계정을 추가하도록 허용하면 구매 제한을 제거할 수 있습니다. 이렇게 하면 최종 사용자가 개인 계정을 사용하여 Google Play 스토어에서 앱을 구매할 수 있을 뿐 아니라 앱에서 바로 구매할 수도 있습니다. 자세한 내용은 [Intune을 사용하여 기능을 허용하거나 제한하는 Android 엔터프라이즈 디바이스 설정](../configuration/device-restrictions-android-for-work.md)을 참조하세요. 

> [!NOTE]
> Microsoft Intune 앱 및 Microsoft Authenticator 앱은 온보딩 중에 모든 완전 관리형 디바이스에 필수 앱으로 설치됩니다. 이러한 앱을 자동으로 설치하면 조건부 액세스를 지원할 수 있고 Microsoft Intune 앱 사용자는 규정 준수 문제를 확인하고 해결할 수 있습니다. 

## <a name="manage-android-enterprise-app-permissions"></a>Android 엔터프라이즈 앱 권한 관리
Android 엔터프라이즈를 사용하려면 관리되는 Google Play 웹 콘솔에서 앱을 승인한 후 Intune과 동기화하고 사용자에게 할당해야 합니다. Android 엔터프라이즈를 통해 사용자 디바이스에 앱을 자동으로 푸시할 수 있으므로 모든 사용자를 대신하여 앱 권한을 허용해야 합니다. 사용자가 앱을 설치할 때 앱 권한이 표시되지 않으므로 권한을 이해하는 것이 중요합니다.

앱 개발자가 새 버전의 앱으로 권한을 업데이트하면 이전 권한을 승인했다 해도 권한이 자동으로 허용되지는 않습니다. 이전 버전의 앱을 실행하는 디바이스는 해당 앱을 계속 사용할 수 있습니다. 그러나 새 권한을 승인할 때까지는 앱이 업그레이드되지 않습니다. 앱이 설치되지 않은 디바이스는 앱의 새 권한을 승인할 때까지 앱을 설치하지 않습니다. 

### <a name="update-app-permissions"></a>앱 권한 업데이트

관리되는 Google Play 콘솔을 주기적으로 방문하여 새 권한을 확인합니다. 승인된 앱에 대해 새 권한이 필요할 때 자신이나 다른 사용자에게 메일을 전송하도록 Google Play를 구성할 수 있습니다. 앱을 할당할 때 디바이스에 설치되지 않은 것을 발견한 경우 다음 단계에 따라 새 권한을 확인합니다.

1. [Google Play](https://play.google.com/work)로 이동합니다.
2. 앱을 게시하고 승인하는 데 사용한 Google 계정으로 로그인합니다.
3. **업데이트** 탭을 선택하고 업데이트가 필요한 앱이 있는지 확인합니다.  
    나열된 모든 앱은 새 권한이 필요하므로 새 권한이 적용될 때까지 할당되지 않습니다.

앱별로 앱 권한을 자동으로 다시 승인하도록 Google Play를 구성할 수도 있습니다.

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>관리형 Google Play 앱에서 Android Enterprise 작업 프로필 디바이스에 대한 추가 보고

Android Enterprise 작업 프로필 디바이스에 배포된 관리형 Google Play 앱의 경우 디바이스에 설치된 앱의 특정 버전 번호를 볼 수 있습니다. 이는 필수 앱에만 적용됩니다. 


## <a name="delete-managed-google-play-apps"></a>관리되는 Google Play 앱 삭제
필요한 경우 Microsoft Intune에서 관리되는 Google Play 앱을 삭제할 수 있습니다. 관리되는 Google Play 앱을 삭제하려면 Azure Portal에서 Microsoft Intune을 열고 **클라이언트 앱** > **앱**을 선택합니다. 앱 목록에서 관리되는 Google Play 앱의 오른쪽에 있는 줄임표(...)를 선택한 다음, 표시된 목록에서 **삭제**를 선택합니다. 앱 목록에서 관리되는 Google Play 앱을 삭제하면 관리되는 Google Play 앱이 자동으로 승인되지 않습니다.

## <a name="android-enterprise-system-apps"></a>Android Enterprise 시스템 앱

[Android 엔터프라이즈 전용 디바이스](../enrollment/android-kiosk-enroll.md) 또는 [완전 관리형 디바이스](../enrollment/android-fully-managed-enroll.md)에 Android 엔터프라이즈 시스템 앱을 사용하도록 설정할 수 있습니다. Android 엔터프라이즈 시스템 앱 추가에 대한 자세한 내용은 [Microsoft Intune에 Android 엔터프라이즈 시스템 앱 추가](apps-ae-system.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [그룹에 앱 할당](apps-deploy.md)
