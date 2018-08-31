---
title: 회사 소유 또는 제공된 macOS 장치 관리 등록 | Microsoft Docs
description: 조직에서 구입하여 제공한 Intune에서 macOS 장치를 등록하는 방법에 대해 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 272a82f7d3d62d117fa5506ccf446b3169ff514f
ms.sourcegitcommit: bb56ada81e6d4950f130415918c4acc455bb52dd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43016230"
---
# <a name="get-your-company-owned-macos-device-managed"></a>회사 소유 macOS 장치 관리

Intune에서 자동으로 관리되는 새 macOS 장치를 가져오는 방법에 대해 알아봅니다.

회사 및 학교 소유 장치는 받기 전에 미리 구성된 경우가 많습니다. 장치를 켜고 처음 로그인할 때 조직에서는 미리 구성된 설정을 장치로 보냅니다. 장치에서 설정을 완료한 후 회사 또는 학교 리소스에 액세스할 수 있습니다. 

관리 설정을 시작하려면 장치의 전원을 켜고 회사 또는 학교 자격 증명으로 로그인합니다. 이 문서의 나머지 부분에서는 설정 도우미를 통해 볼 수 있는 단계와 화면에 대해 설명합니다.   

## <a name="what-is-apple-dep"></a>Apple DEP란?
회사 소유 장치가 있는 경우 Apple DEP(장치 등록 프로그램)에서 구입했을 수 있습니다. 일부 조직은 Apple DEP를 통해 iOS 또는 macOS 장치를 구입합니다. 그런 다음, 조직은 Intune과 같이 선호하는 모바일 장치 관리 공급자 내에서 장치를 구성하고 관리할 수 있습니다. 관리자이고 Apple DEP에 대한 자세한 내용을 확인하려면 [Apple의 장비 등록 프로그램을 사용하여 자동으로 macOS 장치 등록](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos)을 참조하세요.  

## <a name="set-up-your-macos-device"></a>macOS 장치 설정  
macOS 장치를 관리에 등록하려면 다음 단계를 완료합니다. 회사 소유 장치가 아닌 자신의 장치를 사용하는 경우 [개인용 및 개인 소유 장치 가져오기](enroll-your-device-in-intune-macos-cp.md)의 단계를 따릅니다.  

1. macOS 장치 전원을 켭니다. 
2. **언어**를 선택하고 **계속**을 클릭합니다.  

   ![macOS 장치 설치 도우미 시작 화면의 스크린샷은 선택하는 언어의 목록을 표시합니다.](./media/macos-dep-welcome-1808.png)   
3. 키보드 레이아웃을 선택합니다. 목록에는 선택한 언어에 따라 하나 이상의 옵션이 표시됩니다. 선택한 언어에 관계없이 모든 레이아웃 옵션을 보려면 **모두 표시**를 클릭합니다. 작업이 완료되면 **계속**을 클릭합니다.  

   ![macOS 장치 설치 도우미 키보드 레이아웃 화면의 스크린샷에서는 선택할 키보드 언어 목록, 선택하지 않은 모두 표시 옵션 및 돌아가기와 계속 단추가 표시됩니다.](./media/macos-dep-keyboard-1808.png)  
4. Wi-Fi 네트워크를 선택합니다. 설치를 계속하려면 인터넷에 연결되어 있어야 합니다. 네트워크가 표시되지 않거나 유선 네트워크를 통해 연결해야 하는 경우 **기타 네트워크 옵션**을 클릭합니다. 작업이 완료되면 **계속**을 클릭합니다.  

   ![macOS 장치 설치 도우미 선택 Wi-Fi 네트워크 화면의 스크린샷은 선택 가능한 네트워크 목록을 표시합니다. 기타 네트워크 옵션 단추, 돌아가기 단추 및 계속 단추도 표시합니다.](./media/macos-dep-wifi-1808.png)  
5. Wi-Fi에 연결되면 **원격 관리** 화면이 나타납니다. 원격 관리를 통해 조직의 관리자는 회사에서 필요로 하는 계정, 설정, 앱 및 네트워크를 사용하여 장치를 원격으로 구성할 수 있습니다. 계속하기 전에 장치를 관리하는 방법을 이해하는 데 도움이 되는 설명서를 읽습니다. **계속**을 클릭합니다.  

   ![macOS 장치 설치 도우미 원격 관리 화면의 스크린샷은 원격 관리 설명 텍스트 및 자세한 내용에 대한 설명서 링크를 포함합니다. 돌아가기 단추와 계속 단추도 표시합니다.](./media/macos-dep-remote-management-1-1808.png)  
6. 메시지가 나타나면 회사 또는 학교 계정으로 로그인합니다. 인증 후 장치에서 관리 프로필을 설치합니다. 프로필은 조직의 리소스에 대한 액세스를 구성하고 활성화합니다.  
7. 나중에 개인 정보가 수집되는 시기를 식별할 수 있도록 Apple 데이터 및 개인 정보 아이콘에 대해 읽어 보세요. **계속**을 클릭합니다.  

   ![macOS 장치 설치 도우미 데이터 및 개인 정보 화면의 스크린샷으로 두 사람이 악수하는 예시를 보여주고, Apple의 개인 정보 사용을 설명합니다. 돌아가기 및 계속 단추도 표시합니다.](./media/macos-dep-apple-data-privacy-1808.png)  
8. 장치를 등록한 후 완료해야 할 추가 단계가 있을 수 있습니다. 표시되는 단계는 조직에서 설치 환경을 사용자 지정하는 방법에 따라 다릅니다. 다음을 수행해야 할 수 있습니다.
    * Apple 계정에 로그인
    * 사용 약관에 동의함
    * 컴퓨터 계정 만들기
    * 빠른 설정을 통해 진행
    * Mac 설정  
## <a name="get-the-company-portal-app"></a>회사 포털 앱 가져오기      
App Store로 이동하여 장치에서 Intune 회사 포털 앱을 가져옵니다. 이 앱을 사용하면 관리에서 장치를 모니터링, 동기화, 추가 및 제거하고 앱을 설치할 수 있습니다.

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com#HelpDeskDialog)를 참조하세요.
