---
title: Android 디바이스에서 관리되는 앱 사용 | Microsoft 문서
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ed10a62c-b026-4ad3-ac41-641933522df2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 60df25542e69422e15a2a57473a3fbfa2cc413a5
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959505"
---
# <a name="use-managed-apps-on-your-android-device"></a>Android 디바이스에서 관리되는 앱 사용
관리되는 앱은 조직의 보안 요구 사항을 충족시키고 회사 및 학교 데이터를 보호하도록 구성됩니다. 이러한 앱은 디바이스에서 자동으로 설치 또는 사용할 수 있습니다. 

관리되는 앱을 받고 설치하기 전에 조직에서 권한을 구성합니다. 앱 기능이나 사용자 상호 작용을 제한하여 승인되지 않은 개인이 앱 데이터를 공유하거나 볼 수 없도록 차단할 수 있습니다. 예를 들어, 앱을 사용하는 동안 조직이 복사 및 붙여넣기 사용을 차단할 수 있습니다. 또는 디바이스의 로컬 저장소에 데이터를 저장하는 것을 제한할 수 있습니다.

데이터 보호를 극대화하기 위해 조직은 여러 관리되는 앱들이 연동되도록 구성할 수 있습니다. 예를 들면 다음과 같습니다.
1. Microsoft Edge와 같은 관리되는 브라우저 앱에서 회사 네트워크에 연결합니다.
2. 링크를 클릭하여 동료의 프레젠테이션 파일을 엽니다.
3. Microsoft PowerPoint와 같은 적절히 관리되는 앱이 파일을 엽니다.

조직에서 작업 파일 열기 또는 웹 링크 액세스와 같이 관리되는 앱을 사용하여 작업을 수행하도록 요구할 수 있습니다. 앱이 없는 경우 작업을 계속하지 못할 수 있습니다. 일부 관리되는 앱의 경우 설치는 할 수 있으나 필수는 아닙니다.

## <a name="how-do-i-know-im-using-a-managed-app"></a>관리되는 앱을 사용하는지 어떻게 알 수 있습니까?
관리되는 앱에서 회사 또는 학교 데이터에 처음 액세스하면 아래의 예제 스크린샷과 유사한 메시지가 표시됩니다. 계속하면 앱을 다시 시작하라는 메시지가 나타납니다.

![사용자가 디바이스에서 관리되는 앱을 열 때 표시되는 메시지 스크린샷입니다. "조직이 이제 이 앱에서 조직 데이터를 보호합니다. 계속하려면 앱을 다시 시작해야 합니다."라는 메시지가 표시되면 확인 버튼을 클릭합니다.](./media/managed-apps-message.png)

## <a name="commonly-managed-apps"></a>일반적으로 관리되는 앱  
학교와 직장 내에서 일반적으로 필요하거나 사용할 수 있는 관리되는 앱의 예제는 다음과 같습니다.

-   Microsoft Edge

-   Microsoft Outlook

-   Microsoft Word, Excel 및 PowerPoint

## <a name="how-do-i-get-managed-apps"></a>관리되는 앱을 가져오려면 어떻게 하나요?
먼저 회사 포털을 설치해야 하며 필요한 경우 디바이스를 관리합니다. 그런 다음, 세 가지 방법으로 관리되는 앱을 가져올 수 있습니다.
* 조직은 등록 시 자동으로 앱을 디바이스에 설치합니다. 등록에 대해 자세히 알아보려면 [Intune에서 디바이스 등록](enroll-your-device-in-Intune-android.md)을 참조하세요.
* 조직은 회사 포털에서 관리되는 앱을 사용할 수 있도록 합니다. 회사 포털 앱 또는 웹 사이트로 이동하여 이러한 앱을 검색하고 보고 설치합니다. 
* Google Play 스토어에서 앱을 설치한 다음, 회사 또는 학교 계정으로 앱에 로그인합니다.  

## <a name="what-can-my-company-support-manage-in-an-app"></a>회사 지원팀이 앱에서 관리할 수 있는 항목은 무엇인가요?
다음 목록은 앱 내에서 회사 지원팀에서 관리할 수 있는 설정을 설명합니다. 이 설정은 디바이스에서 회사 또는 학교 데이터를 보고 액세스하고 사용하는 방식에 영향을 줍니다.

* 특정 웹사이트에 대 한 액세스  

* Edge와 Azure Active Directory 프록시를 사용하여 회사 내부 웹 사이트에 액세스  

* 최소 앱 버전, OS 버전

* 앱 간에 데이터를 공유 및 전송하는 기능  

* 파일을 저장하는 방법 및 위치  

* 복사 및 붙여넣기 기능  

* PIN 액세스 요구 사항  

* 회사 자격 증명을 사용하여 로그인하는 방법  

* 클라우드에 데이터를 백업하는 기능  

* 스크린샷을 만드는 기능  

* 데이터 암호화 요구 사항  

디바이스에서 관리되는 앱에 대한 자세한 내용은 회사 지원팀에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
