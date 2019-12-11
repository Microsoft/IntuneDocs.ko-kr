---
title: 디바이스 등록이란 | Microsoft Docs
description: 회사 포털 및 Microsoft Intune 앱에 장치를 등록 하는 것이 무엇을 의미 하는지 이해 합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/13/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca1776915d50858c28b43a49faa7c737c825c67d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72501863"
---
# <a name="what-is-device-enrollment"></a>디바이스 등록이란?
장치에서 회사 또는 학교 리소스에 액세스 하려면 Intune 회사 포털 앱 또는 Microsoft Intune 앱에 장치를 등록 해야 합니다. 

장치 등록 중:

* 장치가 조직에 등록 되어 있습니다. 이 단계를 수행 하면 조직의 전자 메일, 앱 및 Wi-fi에 액세스할 수 있는 권한이 부여 됩니다. 
* 조직의 장치 관리 정책이 장치에 적용 됩니다. 정책에는 장치 암호 및 암호화와 같은 항목에 대 한 요구 사항이 포함 될 수 있습니다. 이러한 요구 사항의 목적은 장치 및 조직의 데이터를 무단 액세스 로부터 보호 하는 것입니다.

조직의 요구 사항에 맞게 장치 설정을 업데이트 하면 등록이 완료 됩니다. 거의 모든 위치에서 회사 또는 학교 계정에 안전 하 게 로그인 할 수 있습니다.  

이 문서에서는 앱을 가져오고, 지원 되는 장치를 가져오고, 장치를 제거 하거나 다시 설정 하는 방법과 같은 등록의 다른 측면을 설명 합니다.  

## <a name="company-portal-and-microsoft-intune-app"></a>회사 포털 및 Microsoft Intune 앱

회사 포털 및 Microsoft Intune 앱은 정책 또는 설정 변경에 대해 경고 하므로 회사 또는 학교에 대 한 액세스 권한을 잃지 않고 작업을 수행할 수 있습니다. 

회사 포털 앱은 개인 정보 및 작업 정보를 별도로 유지 하므로 생산적이 고 집중할 수 있습니다. 또한 회사 및 학교 앱을 사용할 수 있으므로 작업 줄과 관련 된 작업을 찾아 설치할 수 있습니다.  

### <a name="get-company-portal"></a>회사 포털 사용하기

경우에 따라 조직에서 장치에 회사 포털 앱을 설치 하 게 됩니다. 앱은 Microsoft Store, 앱 스토어 및 Google Play 스토어와 같은 앱 스토어에서 설치할 수도 있습니다. 웹 브라우저에서 앱에 액세스 하려면 회사 또는 학교 계정을 사용 하 여 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 에 로그인 합니다.  

### <a name="get-microsoft-intune-app"></a>Microsoft Intune 앱 사용하기

Microsoft Intune 앱을 사용 해야 하는 경우 조직에서 장치에 설치 합니다.  

## <a name="whats-the-difference-between-the-apps-and-the-website"></a>앱과 웹 사이트의 차이는 무엇인가요?
회사 포털 앱은 Windows 10, iOS, macOS 및 Android 장치에서 사용할 수 있습니다. 장치의 각 플랫폼과 원활 하 게 통합 됩니다. 웹 사이트 버전은 모든 디바이스에서 액세스할 수 있으며,사용하고 있는 디바이스에 관계없이 동일한 범용 환경을 제공합니다. 

Microsoft Intune 앱은 회사 소유의 Android 장치용 이며 웹 사이트가 없습니다.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>회사 포털를 사용 하 여 등록할 수 있는 장치 종류는 무엇 인가요?
회사 포털를 사용 하 여 다음 장치를 등록할 수 있습니다.  

- Windows 디바이스
  - Windows 10 Mobile
  - Windows 10 Desktop
  - Windows Phone 8.1
  - Windows 8.1
- Apple 장치
    - iOS
    - macOS
- Android 디바이스


## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Microsoft Intune 앱에 등록할 수 있는 장치 종류는 무엇 인가요?  
조직이 앱에서 사용 하도록 설정한 회사 소유의 Android 장치를 등록할 수 있습니다. 앱은 Android 6.0 이상을 지원 합니다. 

## <a name="can-you-remove-a-device-from-the-company-portal"></a>회사 포털에서 디바이스를 제거할 수 있나요?
회사 포털에서 장치를 제거 하거나 다시 설정할 수 있습니다. **제거** 및 **재설정** 간에 차이가 있습니다.

장치를 제거 하는 동안 장치의 등록을 취소 하 고 등록을 취소할 회사 포털. 해당 장치는 회사 포털에 대 한 액세스 권한을 잃게 됩니다. 회사 또는 학교 데이터가 제거 될 수도 있습니다. 

디바이스 재설정 중 회사 포털에서 컴퓨터 또는 디바이스를 제조업체의 기본 설정으로 초기화합니다. 모든 회사 또는 학교 데이터 및 모든 개인 데이터는 장치에서 제거 됩니다. 재설정은 예를 들어 장치를 분실 한 경우에 유용 합니다. 회사 포털 웹 사이트에서 원격으로 다시 설정할 수 있습니다.  

## <a name="can-you-remove-a-device-from-the-microsoft-intune-app"></a>Microsoft Intune 앱에서 장치를 제거할 수 있나요?
아니요, Microsoft Intune 앱에서 회사 소유의 장치를 제거할 수 있는 방법이 없습니다.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>회사 포털 또는 Microsoft Intune 앱에서 장치를 볼 수 없는 경우 어떻게 되나요?
회사 포털에서 장치를 확인 하려면 먼저 등록 해야 합니다. 등록 후에도 장치가 모두 표시 되지 않으면 회사 포털를 통해 동기화 하거나 액세스를 확인 합니다. 회사에서 소유하고 관리하는 디바이스가 표시되지 않습니다.

Microsoft Intune 앱에는 현재 사용 중인 장치만 표시 됩니다. 등록 된 다른 장치는 앱에서 볼 수 없습니다.  

## <a name="where-else-can-i-go-for-help"></a>다른 어디서 도움을 받을 수 있나요?  
일반적인 문제를 해결 하려면 다음과 같은 플랫폼별 문서를 확인 하세요.  

- [Android 디바이스의 일반적인 문제 해결](check-compliance-on-your-device-android.md)  
- [iOS 디바이스의 일반적인 문제 해결](troubleshoot-your-device-ios.md)
- [macOS 디바이스의 일반적인 문제 해결](troubleshoot-your-device-macos.md)
- [Windows 디바이스의 일반적인 문제 해결](troubleshoot-your-device-windows.md)

IT 지원 담당자에 게 문의할 수도 있습니다. 회사 포털 및 Microsoft Intune 앱은 연락처 정보 및 문제를 보고 하는 방법을 나열 하는 도움말 및 지원 페이지를 제공 합니다. 연락처 정보는 조직의 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에서도 사용할 수 있습니다.  

## <a name="next-steps"></a>다음 단계  

회사 또는 학교 계정에 액세스할 준비가 되었으면 조직의 지침에 따라 장치를 등록 하세요. 다음 문서에서 단계별 등록 지침을 찾을 수도 있습니다.

* [Windows 10 디바이스 등록](enroll-windows-10-device.md)
* [Android 디바이스 등록](enroll-device-android-company-portal.md)
* [Android 회사 프로필에 등록](enroll-device-android-work-profile.md)
* [Microsoft Intune 앱에 등록](enroll-device-android-microsoft-intune-app.md)
* [iOS 디바이스 등록](enroll-your-device-in-intune-ios.md)
* [조직 제공 iOS 디바이스 등록](enroll-your-device-dep-ios.md)
* [macOS 디바이스 등록](enroll-your-device-in-intune-macos-cp.md)
* [조직 제공 macOS 디바이스 등록](enroll-company-device-macos.md)


