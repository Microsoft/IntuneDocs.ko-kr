---
title: 관리에 조직 제공 iOS 디바이스를 등록합니다. | Microsoft 문서
description: 조직에서 구입하여 제공한 Intune에서 iOS 디바이스를 등록하는 방법에 대해 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: b93f02011b0900b1a64ae6cb10a84a52cd40187a
ms.sourcegitcommit: 11cad61c565c474a8d653181675cc1109d562626
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43241799"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>관리에 조직 제공 iOS 디바이스 등록

Intune에서 새 iOS 디바이스를 관리하는 방법을 알아봅니다.  

회사 또는 학교에서 제공되는 iOS 디바이스는 받기 전에 종종 미리 구성됩니다. 디바이스를 켜고 처음 로그인하면 조직에서는 이러한 미리 구성된 설정을 디바이스로 보냅니다. 디바이스에서 설정을 완료한 후 회사 또는 학교 리소스에 액세스할 수 있습니다.  

설정을 시작하려면 디바이스의 전원을 켜고 회사 또는 학교 자격 증명으로 로그인합니다. 이 문서의 나머지 부분에서는 설정 도우미를 통해 볼 수 있는 단계와 화면에 대해 설명합니다. 

## <a name="what-is-apple-dep"></a>Apple DEP란?
조직은 *Apple 장비 등록 프로그램*(DEP)이라는 것을 통해 해당 디바이스를 구매했을 수 있습니다. Apple DEP를 통해 조직은 대량의 iOS 또는 macOS 디바이스를 구입할 수 있습니다. 그런 다음, 조직은 Intune과 같이 선호하는 모바일 디바이스 관리 공급자 내에서 해당 디바이스를 구성하고 관리할 수 있습니다. 관리자이고 Apple DEP에 대한 자세한 내용을 확인하려면 [Apple의 장비 등록 프로그램을 사용하여 자동으로 iOS 디바이스 등록](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios)을 참조하세요.  

## <a name="set-up-your-ios-device"></a>iOS 디바이스 설정  
조직 제공 디바이스가 아닌 자신의 iOS 디바이스를 사용하는 경우 [개인용 및 개인 소유 디바이스 가져오기](enroll-your-device-in-intune-ios.md)의 단계를 따릅니다.  

1. iOS 디바이스를 켭니다. 
2. **언어**를 선택하고 장치를 Wi-Fi에 연결합니다.
3. **iOS 장치 설정** 화면에서 다음과 같은 작업을 수행할지 여부를 선택합니다. 
 
   - **새 장치로 설정**
   - **iCloud 백업에서 복원**
   - **iTunes 백업에서 복원**

4. Wi-Fi에 연결되면 **구성** 화면이 표시됩니다. **[사용자 회사]에서 자동으로 장치를 구성합니다.** 라고 표시합니다.

   **구성을 통해 [사용자 조직]이 이 장치를 무선으로 관리할 수 있습니다. 관리자가 이메일 및 네트워크 계정을 설정하고, 앱을 설치 및 구성하고, 원격으로 설정을 관리하도록 지원할 수 있습니다. 관리자는 기능을 사용하지 않도록 설정하고, 앱을 설치 및 제거하고, 인터넷 트래픽을 모니터링 및 제한하고, 이 디바이스를 원격으로 지울 수 있습니다.**
 
   **구성은 다음에서 제공합니다.[사용자 회사의] iOS 팀 [주소]**

5. Apple ID에 로그인합니다. 로그인을 통해 회사 포털 앱을 설치하고 관리 프로필을 설치하여 회사에 이메일 및 앱과 같은 해당 리소스에 대한 액세스 권한을 부여할 수 있습니다. 
6. **사용 약관**에 동의하고 진단 정보를 Apple로 보낼 것인지 결정합니다.
7. 등록이 완료되면 추가 작업을 수행하라는 메시지가 디바이스에 표시됩니다. 이러한 단계에서 이메일 액세스를 위한 암호를 입력하거나 암호를 설정합니다.

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
