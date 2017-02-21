---
title: "관리되는 장치를 사용하여 작업 완료 | Microsoft Docs"
description: "회사 포털 앱에 대해 자세히 알아보기."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 68c7a23dc8769330c14f74e6aebb07eeb188a991
ms.openlocfilehash: 1ca19828902585bf6011713ab214619b7f8c12c5


---

# <a name="using-managed-devices-to-get-work-done"></a>관리되는 장치를 사용하여 작업 완료
Microsoft Intune은 조직에서 장치(예: 스마트폰, 태블릿 및 PC), 앱 및 기타 회사 리소스(예: 메일)를 관리하는 데 사용할 수 있는 일종의 소프트웨어입니다. 이를 통해 회사 정보의 보안을 유지하면서 직원이 거의 모든 장치에서 어디서나 자신의 작업 정보에 액세스하도록 할 수 있습니다.

Intune을 사용하여 관리하도록 장치를 등록하면 IT 부서에서 해당 회사 또는 학교 리소스를 관리하고 장치를 보다 안전하게 유지하면서 선호하는 장치를 자유롭게 사용하여 작업을 완료할 수 있습니다. 이렇게 하는 기본 방법은 회사 포털을 통해 관리에 장치를 등록하는 것입니다.

다음과 같은 두 가지 방법으로 회사 포털을 사용할 수 있습니다.

- 장치에 회사 포털 앱을 설치합니다. 일반적으로 장치의 앱 스토어로 이동하여 회사 포털 앱을 가져오지만, IT 관리자가 사용자 대신에 회사 포털 앱을 설치할 수도 있습니다.
- IT 관리자가 설정한 [회사 포털 웹 사이트](http://portal.manage.microsoft.com)로 이동합니다.

## <a name="whats-the-difference-between-the-app-and-the-website"></a>앱과 웹 사이트의 차이는 무엇인가요?
회사 포털 앱과 회사 포털 웹 사이트 사이에는 몇 가지 사소한 차이점이 있지만, 둘 다에서 대부분의 동일한 작업을 수행할 수 있습니다. 수행할 수 있는 일부 작업은 다음과 같습니다.

- 관리에 장치 등록
- 장치의 상태 확인
- 조직의 권장 및 필수 앱 다운로드
- 장치 이름 바꾸기
- 장치의 PIN 또는 암호 재설정
- IT 부서에 지원 문의

장치에서 회사 포털 앱을 사용하여 수행할 수 있는 작업과 회사 포털 웹 사이트를 사용하여 수행할 수 있는 작업을 비교하여 보려면 다음 링크 중 하나를 선택하세요.

- [Android 장치 사용](using-your-android-device-with-intune.md)
- [iOS 또는 macOS 장치 사용](using-your-ios-or-macOS-device-with-intune.md)
- [Windows 장치 사용](using-your-windows-device-with-intune.md)
- [회사 포털 웹 사이트 사용](using-the-intune-company-portal-website.md)

## <a name="what-happens-when-you-add-a-computer-or-device-to-the-company-portal"></a>회사 포털에 컴퓨터 또는 장치를 추가하면 어떻게 되나요?
회사 포털에 컴퓨터 또는 장치를 추가하면 장치에 따라 몇 가지 소프트웨어를 설치할 수도 있고 앱을 다운로드할 수도 있습니다. 회사 포털에 장치를 추가하는 것은 IT 관리자가 장치의 회사 정보를 보호하기 위해 사용자의 장치를 관리할 수 있는 권한도 부여하는 것입니다.

IT 관리자가 장치에서 볼 수 있는 항목과 볼 수 없는 항목에 대해 알아보려면 다음 중 사용하고 있는 장치 유형에 해당하는 링크를 사용하세요.

- [Android용 회사 포털 앱 설치](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-android.md)
- [iOS 및 macOS용 회사 포털 앱 설치](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)
- [Windows용 회사 포털 앱 설치](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

## <a name="what-kind-of-computers-or-devices-can-you-add-to-the-company-portal"></a>회사 포털에 추가할 수 있는 컴퓨터 또는 장치 종류는 무엇인가요?
-   iOS(iPhone, iPad 등) 및 macOS(MacBook, iMac 등)를 사용하는 Apple 장치
-   Android 장치
-   Windows 장치
    -   Windows 10 Mobile
    -   Windows 10 Desktop
    -   Windows Phone 8.1
    -   Windows 8.1

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>회사 포털에서 컴퓨터 또는 장치를 제거할 수 있나요?
회사 포털에서 컴퓨터 또는 장치를 제거하거나 초기화할 수 있습니다. **제거** 및 **재설정** 간에 차이가 있습니다.

컴퓨터 또는 장치를 *제거*하는 경우 장치를 Intune에서 등록 취소합니다. 등록 취소하면 더 이상 장치에서 회사 포털에 액세스할 수 없게 되고, 일부 회사 데이터가 장치에서 제거될 수 있습니다. 회사 포털에서 장치를 제거하는 방법을 알아보려면 다음 링크 중 하나를 선택하세요.

- [Android 장치 등록 취소](unenroll-your-device-from-intune-android.md)
- [iOS 또는 macOS 장치 등록 취소](unenroll-your-device-from-intune-ios.md)
- [Windows 장치 등록 취소](unenroll-your-device-from-intune-windows.md)

컴퓨터 또는 장치를 *초기화*하면 회사 포털에서 컴퓨터 또는 장치를 제조업체의 기본 설정으로 초기화합니다. 장치를 초기화하면 장치에서 모든 회사 및 개인 데이터가 제거됩니다! 장치를 잃어버린 경우 회사 포털 웹 사이트에서 원격으로 장치를 초기화할 수도 있습니다.

장치를 초기화하는 방법을 알아보려면 다음 링크 중 하나를 선택하세요.

- [Android 장치 다시 설정(지우기)](reset-erase-your-lost-or-stolen-device-android.md)
- [iOS 또는 macOS 장치 다시 설정(지우기)](reset-erase-your-lost-or-stolen-device-ios.md)
- [Windows 장치 다시 설정](reset-erase-your-lost-or-stolen-device-windows.md)
- [회사 포털 웹 사이트에서 장치 다시 설정](reset-your-device-cpwebsite.md)

## <a name="what-if-i-cant-see-my-device-in-the-company-portal"></a>회사 포털에 장치가 보이지 않으면 어떻게 해야 하나요?
장치를 표시할 수 있으려면 먼저 회사 포털에 추가해야 합니다. 관리자가 권장한 회사 포털로 이동하여 장치에 대한 단계를 따릅니다. 또한 회사에서 소유하고 관리하는 장치가 표시되지 않습니다.

## <a name="if-you-have-questions-contact-your-it-admin"></a>의문 사항이 있으면 IT 관리자에게 문의하세요.
도움이 필요하면 IT 관리자에게 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](http://portal.manage.microsoft.com)를 참조하세요.



<!--HONumber=Feb17_HO2-->

