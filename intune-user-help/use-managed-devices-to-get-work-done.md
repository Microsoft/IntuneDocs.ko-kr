---
title: 관리되는 디바이스를 사용하여 작업 완료 | Microsoft 문서
description: Intune에서 디바이스를 관리에 등록한다는 것이 무엇을 의미하는지 이해합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883866"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>회사 또는 학교 리소스에 액세스 하기 위해 장치 등록
장치를 등록 하 고 전자 메일 및 앱에 대 한 액세스 권한을 얻으려면 Intune 회사 포털 앱 또는 Microsoft Intune 앱을 설치 해야 합니다. 등록할 때 조직에서 구성한 기본 관리 정책 (예: 암호, PIN 및 암호화)이 장치에 적용 됩니다. 장치 설정이 조직의 요구 사항을 모두 충족 하면 거의 모든 위치에서 작업 정보에 안전 하 게 액세스할 수 있습니다.  

회사 포털 및 Microsoft Intune 앱은 장치 설정이 조직의 정책과 일치 하는지 확인 하 여 등록 된 장치를 안전 하 게 유지 합니다. 

회사 포털 앱 또한  
* 개인 및 작업 정보를 별도로 유지 합니다.  
* 를 사용 하면 관련 회사 및 학교 앱을 쉽게 찾고 설치할 수 있습니다.   

## <a name="get-the-apps"></a>앱 다운로드
회사 포털을 가져오려면

- 플랫폼별 앱 스토어에서 회사 포털 앱을 설치 합니다. 경우에 따라 조직에서 회사 포털 앱을 설치 하 게 됩니다.  
- 브라우저에서 앱에 액세스 하려면 [회사 포털 웹 사이트로](https://go.microsoft.com/fwlink/?linkid=2010980) 이동 하세요.  

Microsoft Intune 앱을 사용 해야 하는 경우 조직에서 해당 앱을 설치 합니다.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>등록하면 회사에 어떤 정보가 표시되나요?
장치를 등록 한 후에는 조직의 지원 담당자가 작업과 관련 된 정보만 볼 수 있습니다. 개인 정보는 볼 수 없습니다. 회사에서 사용 하기 위해 개인 장치를 등록 하는 경우에는 무엇을 볼 [수 있는지 정확히 알 수 없습니다](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>앱과 웹 사이트의 차이는 무엇인가요?
회사 포털 앱은 Windows 10, iOS, macOS 및 Android 장치에서 사용할 수 있습니다. 장치의 각 플랫폼과 원활 하 게 통합 됩니다. 웹 사이트 버전은 모든 디바이스에서 액세스할 수 있으며,사용하고 있는 디바이스에 관계없이 동일한 범용 환경을 제공합니다. 

Microsoft Intune 앱은 회사 소유의 Android 장치용입니다.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>회사 포털를 사용 하 여 등록할 수 있는 장치 종류는 무엇 인가요?
- iOS(iPhone, iPad 등) 및 macOS(MacBook, iMac 등)를 사용하는 Apple 디바이스
- Android 디바이스
- Windows 디바이스
  - Windows 10 Mobile
  - Windows 10 Desktop
  - Windows Phone 8.1
  - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Microsoft Intune 앱에 등록할 수 있는 장치 종류는 무엇 인가요?  
조직이 앱에서 사용 하도록 설정한 회사 소유의 Android 장치를 등록할 수 있습니다. 앱은 Android 6.0 이상을 지원 합니다. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>회사 포털에서 컴퓨터 또는 디바이스를 제거할 수 있나요?
회사 포털에서 컴퓨터 또는 디바이스를 제거하거나 초기화할 수 있습니다. **제거** 및 **재설정** 간에 차이가 있습니다.

회사 포털에서 컴퓨터 또는 디바이스를 제거하면 Intune에서 디바이스 등록이 취소됩니다. 등록 취소하면 더 이상 디바이스에서 회사 포털에 액세스할 수 없게 되고, 일부 회사 데이터가 디바이스에서 제거될 수 있습니다. 회사 포털에서 장치를 제거 하는 방법을 알아보려면 다음 링크를 참조 하세요.  

- [Android 디바이스 등록 취소](unenroll-your-device-from-intune-android.md)
- [iOS 디바이스 등록 취소](unenroll-your-device-from-intune-ios.md)
- [macOS 디바이스 등록 취소](unenroll-your-device-from-intune-macos.md)
- [Windows 디바이스 등록 취소](unenroll-your-device-from-intune-windows.md)

컴퓨터 또는 디바이스를 초기화하면 회사 포털에서 컴퓨터 또는 디바이스를 제조업체의 기본 설정으로 초기화합니다. 디바이스를 초기화하면 디바이스에서 모든 회사 및 개인 데이터가 제거됩니다. 디바이스를 잃어버린 경우 회사 포털 웹 사이트에서 원격으로 디바이스를 초기화할 수도 있습니다.  

장치를 다시 설정 하는 방법을 알아보려면 [회사 포털 웹 사이트에서 장치 다시 설정](reset-erase-your-device-cpwebsite.md)을 참조 하세요.  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>Microsoft Intune 앱에서 컴퓨터 또는 장치를 제거할 수 있나요?
아니요, Microsoft Intune 앱에서 회사 소유의 장치를 제거할 수 있는 방법이 없습니다.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>회사 포털 또는 Microsoft Intune 앱에서 장치를 볼 수 없는 경우 어떻게 되나요?
디바이스를 표시할 수 있으려면 먼저 회사 포털에 추가해야 합니다. 관리자가 권장한 회사 포털로 이동하여 디바이스에 대한 단계를 따릅니다. 또한 회사에서 소유하고 관리하는 디바이스가 표시되지 않습니다.

Microsoft Intune 앱을 사용 하는 경우 현재 사용 중인 장치만 표시 됩니다. 등록 된 다른 장치는 앱에서 볼 수 없습니다.  

## <a name="where-else-can-i-go-for-help"></a>다른 어디서 도움을 받을 수 있나요?  
일반적인 문제 및 질문을 해결 하려면 다음과 같은 플랫폼별 문서를 확인 하세요.  

- [Android 디바이스의 일반적인 문제 해결](check-compliance-on-your-device-android.md)  
- [iOS 디바이스의 일반적인 문제 해결](troubleshoot-your-device-ios.md)
- [macOS 디바이스의 일반적인 문제 해결](troubleshoot-your-device-macos.md)
- [Windows 디바이스의 일반적인 문제 해결](troubleshoot-your-device-windows.md)

지원 담당자에 게 연락할 수도 있습니다. 회사 포털 및 Microsoft Intune 앱은 연락처 정보 및 문제를 보고 하는 방법을 나열 하는 도움말 및 지원 페이지를 제공 합니다. 연락처 정보는 조직의 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에서도 사용할 수 있습니다.  

## <a name="next-steps"></a>다음 단계  

장치 플랫폼과 관련 된 등록으로 시작 하는 도움을 받으세요.  

- [Android 디바이스 사용](using-your-android-device-with-intune.md)
- [iOS 디바이스 사용](using-your-ios-device-with-intune.md)
- [macOS 디바이스 사용](using-your-macos-device-with-intune.md)
- [Windows 디바이스 사용](using-your-windows-device-with-intune.md)
- [회사 포털 웹 사이트 사용](using-the-intune-company-portal-website.md)


