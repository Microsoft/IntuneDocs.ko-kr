---
title: Microsoft Intune에서 앱 시작
titlesuffix: ''
description: 앱을 찾고 장치에 추가하여 직원이 작업을 수행할 수 있게 합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 767402326c2b87043eea776a83d58a08072cd301
ms.sourcegitcommit: 399f34cd169e2e352b49aad1dcb7e88294a4a9f1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37869341"
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Microsoft Intune에서 앱 추가 시작

앱을 할당, 모니터링, 구성 또는 보호하려면 앱을 Intune에 추가해야 합니다. Intune은 여러 앱 유형을 지원합니다. 또한 사용 가능한 옵션은 앱 유형마다 다릅니다.

Intune을 사용하여 기업 장치에 다음 앱 유형을 추가하고 할당할 수 있습니다.
- **스토어 앱**: 앱 스토어에서 제공되는 앱에 추가 모바일 응용 프로그램 관리가 적용되어야 하는 장치의 경우.
- **사내에서 작성한 앱(기간 업무)**: 사용자 장치에 다운로드되는 파일을 업로드하는 경우.
- **기본 제공되는 앱** - Office 365 앱과 같이 엄격히 관리되는 앱을 iOS 및 Android 장치에 할당하는 경우.
- **웹앱** - Intune이 장치 홈 화면에 웹앱의 바로 가기를 만드는 경우.

> [!NOTE]
> 동적 장치 그룹에 적용되는 새 정책은 그룹의 모든 장치에 전파하는 데 최대 8시간이 걸릴 수 있습니다.

## <a name="how-do-i-assign-a-public-store-app"></a>공용 저장소 앱을 할당하려면 어떻게 하나요?

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Mobile Apps**를 선택한 다음 **앱**을 선택합니다.
4. **추가**를 선택한 다음, **iOS**를 **앱 형식**으로 선택합니다.
5. **앱 선택**을 선택하여 **앱 스토어 검색** 창을 표시합니다.
6. 텍스트 상자에서 장치에 할당할 앱을 검색합니다. 앱을 선택하고 **선택**을 클릭합니다.
7. **앱 추가** 창에서 **앱 정보**를 선택한 다음, 앱 정보가 모두 채워졌는지 확인합니다. **소유자**, **메모**, **개발자**, 회사의 개인 정보 취급 방침에 대한 **개인 정보 보호 URL** 등 이 앱을 구성하는 데 유용한 다른 선택적 세부 정보를 추가할 수 있습니다.
8. **회사 포털에서 이 항목을 추천 앱으로 표시**에 대해 **예**를 선택했는지 확인하고 **확인**을 선택합니다.
9. **앱 추가** 창에서 **추가**를 선택하여 앱을 추가합니다. 이렇게 하면 해당 앱의 **개요**로 이동합니다. **할당**을 선택한 다음, **그룹 추가**를 클릭하여 테스트 그룹에 할당합니다. 앱을 다운로드에 **사용 가능**하도록 설정합니다. 앱이 테스트 장치에서 **추천 앱**으로 표시됩니다.


- [그룹에 앱을 할당하는 방법](apps-deploy.md)

## <a name="learn-more"></a>자세한 정보

* [Intune을 사용한 앱 관리란?](app-management.md)
* [앱 수명 주기 개요](app-lifecycle.md)
* [앱 보호 정책이란?](app-protection-policy.md)
