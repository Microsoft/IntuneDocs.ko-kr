---
title: Android 회사 프로필 장치에 앱 할당
titlesuffix: Microsoft Intune
description: 관리되는 Google Play 스토어에서 Android 회사 프로필 장치에 앱을 동기화하고 할당하는 방법을 파악합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: c7d5d29df0f91a4cff1060cd10a5d2355e196e39
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180142"
---
# <a name="assign-apps-to-android-work-profile-devices-with-intune"></a>Intune을 사용하여 Android 회사 프로필 장치에 앱 할당

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android 엔터프라이즈는 Android 회사 프로필 장치 및 키오스크 장치를 위한 프로그램입니다. Android 회사 프로필 장치의 경우 Android 엔터프라이즈는 개인 앱 및 데이터를 회사 앱 및 데이터와 구분하는 기능 및 서비스의 집합입니다. Android 엔터프라이즈는 사용자가 업무용 Android 장치를 사용할 때 추가 관리 옵션과 개인 정보를 제공합니다. Intune을 통해 Android 회사 프로필 장치에 앱과 설정을 배포하여 업무 및 개인 정보가 구분되어 있는지 확인할 수 있습니다. Android 회사 프로필 장치에 설치하는 모든 앱은 Google Play 스토어에서 제공됩니다. Android 회사 프로필 장치에 앱을 할당하는 방법은 표준 Android 장치에 앱을 할당하는 방법과 다릅니다. 스토어에 로그인한 다음 원하는 앱을 찾아서 승인합니다. 그러면 Azure Portal의 **사용이 허가된 앱** 노드에 앱이 표시되며, 다른 앱과 마찬가지로 앱의 할당을 관리할 수 있습니다.

또한 고유한 LOB(기간 업무) 앱을 만든 경우 다음과 같이 앱을 할당할 수 있습니다.
- Google Play 스토어의 개인 영역에 앱을 게시할 수 있는 Google 개발자 계정에 등록합니다.
- Intune과 앱을 동기화합니다.

## <a name="before-you-start"></a>시작하기 전에

Intune과 Android 회사 프로필이 Azure Portal의 **장치 등록** 워크로드에서 함께 작업할 수 있도록 구성했는지 확인합니다. 자세한 내용은 [Android 장치 등록](android-work-profile-enroll.md)을 참조하세요.

## <a name="synchronize-an-app-from-the-managed-google-play-store"></a>관리되는 Google Play 스토어에서 앱 동기화

1. [관리되는 Google Play 스토어](https://play.google.com/work)로 이동합니다. Intune과 Android 엔터프라이즈 간 연결을 구성하는 데 사용한 동일한 계정으로 로그인합니다.
2. Intune을 사용하여 스토어를 검색하고 할당할 앱을 선택합니다.
3. 앱을 표시하는 페이지에서 **승인**을 선택합니다.  
    다음 예제에서는 Microsoft Excel 앱이 선택되었습니다.

    ![관리되는 Google Play 스토어의 승인 단추](media/approve.png)
    
   앱 창이 열리면서 앱에서 다양한 작업을 수행할 수 있는 권한을 부여하라는 메시지가 표시됩니다. 

4. **승인**을 선택하여 앱 사용 권한에 동의하고 계속합니다.

    ![앱 권한에 대한 승인 단추](media/approve-app-permissions.png)

5. 새로운 앱 권한 요청을 처리하는 옵션을 선택한 다음 **저장**을 선택합니다.

    ![새로운 앱 권한 요청을 처리하는 옵션](media/approve-app-settings.png)

    앱이 승인되어 IT 관리 콘솔에 표시됩니다. 다음으로, [Intune과 Android 회사 프로필 앱을 동기화](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune)할 수 있습니다. 

## <a name="sync-a-managed-google-play-app-with-intune"></a>Intune과 관리되는 Google Play 앱 동기화

스토어에서 앱을 승인했지만 **클라이언트 앱** 워크로드의 **사용이 허가된 앱** 노드에 표시되지 않으면 다음과 같이 강제로 즉시 동기화합니다.

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드 창의 **설정** 아래에서 **관리되는 Google Play**를 선택합니다.
5. **관리되는 Google Play** 창에서 **새로 고침**을 선택합니다.  
    페이지에서 마지막 동기화의 시간 및 상태가 업데이트됩니다.
6. **클라이언트 앱** 워크로드 창에서 **앱**을 선택합니다.  
    새로 사용 가능한 관리되는 Google Play 앱이 표시됩니다.

**클라이언트 앱** 워크로드 창의 **앱 라이선스** 노드에 앱이 표시되면 [다른 앱과 마찬가지로 앱을 할당](/intune-azure/manage-apps/deploy-apps)할 수 있습니다. 앱은 사용자의 그룹에만 할당할 수 있습니다.

앱을 할당하고 나면 대상으로 지정한 장치에 설치됩니다. 장치 사용자에게 설치 승인을 요청하지 않습니다.

## <a name="manage-android-enterprise-app-permissions"></a>Android 엔터프라이즈 앱 권한 관리
Android 엔터프라이즈를 사용하려면 관리되는 Google Play 웹 콘솔에서 앱을 승인한 후 Intune과 동기화하고 사용자에게 할당해야 합니다. Android 엔터프라이즈를 통해 사용자 장치에 앱을 자동으로 푸시할 수 있으므로 모든 사용자를 대신해서 앱 권한을 허용해야 합니다. 사용자가 앱을 설치할 때 앱 권한이 표시되지 않으므로 권한을 이해하는 것이 중요합니다.

앱 개발자가 새 버전의 앱으로 권한을 업데이트하면 이전 권한을 승인했다 해도 권한이 자동으로 허용되지는 않습니다. 이전 버전의 앱을 실행하는 장치는 해당 앱을 계속 사용할 수 있습니다. 그러나 새 권한을 승인할 때까지는 앱이 업그레이드되지 않습니다. 앱이 설치되지 않은 장치는 앱의 새 권한을 승인할 때까지 앱을 설치하지 않습니다.

### <a name="update-app-permissions"></a>앱 권한 업데이트

관리되는 Google Play 콘솔을 주기적으로 방문하여 새 권한을 확인합니다. 승인된 앱에 대해 새 권한이 필요할 때 자신이나 다른 사용자에게 메일을 전송하도록 Google Play를 구성할 수 있습니다. 앱을 할당할 때 장치에 설치되지 않은 것을 발견한 경우 다음 단계에 따라 새 권한을 확인합니다.

1. [Google Play](http://play.google.com/work)로 이동합니다.
2. 앱을 게시하고 승인하는 데 사용한 Google 계정으로 로그인합니다.
3. **업데이트** 탭을 선택하고 업데이트가 필요한 앱이 있는지 확인합니다.  
    나열된 모든 앱은 새 권한이 필요하므로 새 권한이 적용될 때까지 할당되지 않습니다.

앱별로 앱 권한을 자동으로 다시 승인하도록 Google Play를 구성할 수도 있습니다. 

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>관리되는 Google Play 스토어에서 기간 업무 앱 작업

1. Intune과 Android 엔터프라이즈 간 연결을 구성하는 데 사용한 것과 동일한 계정으로 [Google Play 개발자 콘솔](https://play.google.com/apps/publish)에 로그인합니다.  
    처음 로그인하는 경우 Google Developer 프로그램 구성원이 되기 위해 등록하고 요금을 지불해야 합니다.
2. 콘솔에서 **새 응용 프로그램 추가**를 선택합니다.
3. Google Play 스토어에 앱을 게시한 것과 동일한 방법으로 앱에 대한 정보를 업로드하고 제공합니다. 단, **이 응용 프로그램을 내 조직만 사용(<*조직 이름*>)** 을 선택해야 합니다.

    ![내 조직에서만 앱을 사용할 수 있도록 설정](media/restrict.png)

    이 작업을 수행하면 조직에서만 앱을 사용할 수 있습니다. 공개 Google Play 스토어에서는 사용할 수 없습니다.

    Android 앱을 업로드 및 게시하는 방법에 대한 자세한 내용은 [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469)(Google 개발자 콘솔 도움말)를 참조하세요.
4. 앱을 게시한 후 Intune과 Android 엔터프라이즈 간 연결을 구성하는 데 사용한 것과 동일한 계정으로 [관리되는 Google Play 스토어](https://play.google.com/work)에 로그인합니다.
5. 스토어의 **앱** 노드에서 게시한 앱이 표시되는지 확인합니다.  
    앱이 Intune와 동기화되도록 자동으로 승인됩니다.

## <a name="next-steps"></a>다음 단계

- [그룹에 앱 할당](apps-deploy.md) 

