---
title: iOS 장치에서 관리되는 앱 사용 | Microsoft 문서
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 0f8139d5a17d1a6594354994fda6c0eef64a22f3
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43147505"
---
# <a name="use-managed-apps-on-your-ios-device"></a>iOS 장치에서 관리되는 앱 사용

관리되는 앱은 해당 앱에서 액세스할 수 있는 회사 데이터를 보호하기 위해 회사 지원팀이 설정할 수 있는 앱입니다. iOS 장치의 관리되는 앱에서 회사 데이터에 액세스할 경우 앱이 예상과 약간 다르게 작동하는 것을 확인할 수 있습니다. 예를 들어 보호된 회사 데이터를 복사하고 붙여넣을 수 없거나, 해당 데이터를 특정 위치에 저장할 수 없습니다.

또한 여러 개의 관리되는 앱이 장치에서 함께 작동하여 회사 데이터를 보호된 상태로 유지하는 동시에 일상적인 작업을 허용할 수도 있습니다. 예를 들어 관리되는 앱에서 회사 파일을 열고 해당 파일을 보기 위해 다른 관리되는 앱이 필요한 경우 파일을 볼 수 있는 관리되는 앱이 자동으로 열립니다. 필수 앱을 사용할 수 없는 경우 문서 열기 또는 관리되는 문서 내에서 웹 링크 액세스와 같은 특정 작업을 사용하지 못할 수도 있습니다.

관리되는 앱에서 회사 데이터에 액세스하면 아래와 같은 메시지가 표시되어 여는 앱이 관리되고 있음을 알려줍니다.

![managed-apps-message-ios](./media/managed-apps-message.png)

### <a name="how-do-i-get-managed-apps"></a>관리되는 앱을 가져오려면 어떻게 하나요?
관리되는 앱을 가져오는 방법에는 몇 가지가 있습니다.

-   장치가 Microsoft Intune에 등록된 경우 사용자가 회사 포털 앱 또는 회사 포털 웹 사이트에서 앱을 설치하거나, 회사 지원팀이 장치에 설치할 수 있습니다. 등록에 대해 알아보려면 [Intune에서 iOS 장치 등록](enroll-your-device-in-intune-ios.md) 또는 [Intune에서 macOS 장치 등록](enroll-your-device-in-intune-macos.md)을 참조하세요.

-   앱 스토어에서 앱을 설치하고 Intune으로 관리되는 회사 사용자 계정을 사용하여 로그인합니다.

경우에 따라 회사 지원팀은 설치하는 앱에 대한 여러 라이선스를 구매할 수 있습니다. Apple Volume Purchase Program 규약에 동의하도록 요청하는 메시지가 표시되는 것은 정상적이며 이 규약에 동의할 수 있습니다. 동의하지 않으면 앱을 설치할 수 없습니다.

### <a name="what-can-my-company-support-manage-in-an-app"></a>회사 지원팀이 앱에서 관리할 수 있는 항목은 무엇인가요?
회사 지원팀이 앱에서 관리할 수 있고, 장치에서 회사 데이터 조작에 영향을 줄 수 있는 옵션의 몇 가지 예는 다음과 같습니다.

-   특정 웹사이트에 대 한 액세스

-   응용 프로그램 간에 데이터를 전송

-   파일 저장

-   복사 및 붙여넣기 작업

-   PIN 액세스 요구 사항

-   회사 자격 증명을 사용하는 로그인

-   클라우드로 백업하는 기능

-   스크린샷을 만드는 기능

-   데이터 암호화 요구 사항

장치에서 관리되는 앱에 대한 자세한 내용은 회사 지원팀에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
