---
title: 초기 버전 | Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 초기 버전
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 8cd32a7ec99064a36d58a5a714406659d9d16675
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072442"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Microsoft Intune 초기 버전 - 2019년 1월

> [!Note]
> NDA 알림: Intune에 대해 다음 변경 사항을 개발 중입니다. 이 정보는 매우 제한된 기준에 따라 NDA에서 공유됩니다. Twitter, UserVoice, Reddit 등과 같은 소셜 미디어 또는 공개 웹 사이트에 이 정보를 게시하지 마세요. 

**초기 버전**에서는 Microsoft Intune의 향후 릴리스에서 도입될 기능(NDA로 공유됨) 목록을 제공합니다. 이 정보는 제한적으로 제공되며 변경될 수 있습니다. Twitter, UserVoice에 게시 또는 다른 방법으로 이 정보를 회사 외부에서 공유하지 마세요. 여기 나열된 일부 기능은 마감일을 맞추지 못할 위험이 있으며 다음 릴리스까지 지연될 수 있습니다. 다른 기능은 고객용 준비 상태를 확인하기 위해, 파일럿(플라이팅) 테스트 중 입니다. 질문이나 궁금한 내용이 있으면 Microsoft 제품 그룹 담당자에게 연락하세요.

이 페이지는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal의 Intune

<!-- 1901 start -->


### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱 배포 <!-- 1672660  -->
디바이스 컨텍스트에서 필요로 하는 온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱을 할당할 수 있습니다. 이 방식으로 비즈니스용 Microsoft Store 앱을 배포하면 디바이스의 모든 사용자에 대해 앱을 설치할 수 있습니다. 이 기능은 Windows 10 RS4 이상 데스크톱 디바이스에만 적용됩니다. 디바이스 컨텍스트에 설치하는 옵션은 MSFB 온라인 라이선스가 부여된 앱에 대한 클라이언트 앱 할당 페이지에서 사용할 수 있습니다.


<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 엔터프라이즈 APP-WE 앱 배포 <!-- 1171203 -->
등록되지 않은 APP-WE(등록이 없는 앱 보호 정책) 배포 시나리오에 있는 Android 디바이스의 경우 관리형 Google Play를 사용하여 스토어 앱 및 LOB 앱을 사용자에게 배포할 수 있습니다. 특히 IT 부서에서는 최종 사용자에게 알 수 없는 소스에서 설치를 허용하여 해당 디바이스의 보안 상태를 느슨하게 하도록 더 이상 요구하지 않는 앱 카탈로그 및 설치 환경을 최종 사용자에게 제공할 수 있습니다. 또한 이 배포 시나리오는 향상된 최종 사용자 환경을 제공합니다.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune 앱 SDK는 256비트 암호화 키를 지원함 <!-- 1832174 -->
Android용 Intune 앱 SDK는 앱 보호 정책에서 암호화를 사용하도록 설정할 때 256비트 암호화 키를 사용합니다. SDK는 이전 SDK 버전을 사용하는 콘텐츠 및 앱과 호환성을 위해 128비트 키 지원을 계속 제공합니다.


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 정책에서 인증 방법 및 회사 포털 앱 설치를 업데이트함 <!-- 1927359 -->
Apple의 회사 디바이스 등록 방법 중 하나를 통해 설정 도우미에서 이미 등록한 디바이스에서는 최종 사용자가 앱 스토어에서 회사 포털 앱을 수동으로 설치하는 경우 Intune은 더 이상 해당 회사 포털 앱을 지원하지 않습니다. 이 변경은 등록 중에 Apple 설정 도우미로 인증하는 경우에만 적용됩니다. 또한 이 변경은 다음을 통해 등록된 iOS 디바이스에만 영향을 줍니다.  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple DEP(장비 등록 프로그램)

사용자가 App Store에서 회사 포털 앱을 설치한 다음, 이 앱을 통해 이러한 디바이스를 등록하는 경우 오류가 발생합니다. 이 디바이스는 등록 중에 Intune에서 자동으로 푸시된 경우에만 회사 포털을 사용해야 합니다. Azure Portal에서 Intune의 등록 프로필이 업데이트되므로 디바이스 인증 방법 및 디바이스가 회사 포털 앱을 받는 방법을 지정할 수 있습니다. DEP 디바이스 사용자가 회사 포털을 사용하도록 하려면 등록 프로필에서 기본 설정을 지정해야 합니다. 또한 회사 포털 앱에서 **디바이스 식별** 화면이 더 이상 사용되지 않습니다.  
이미 등록된 DEP 디바이스에 회사 포털을 설치하려면 Intune > 클라이언트 앱으로 이동하고 앱 구성 정책을 사용하여 이 앱을 관리형 앱으로 푸시해야 합니다. 이러한 단계를 수행하는 방법에 대한 자세한 내용은 이후 문서에서 간략하게 설명합니다.


### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>관리 템플릿은 공개 미리 보기로 제공되고 자체 구성 프로필 로 이동됨 <!-- 3322847 -->
Intune의 관리 템플릿(**디바이스 구성** > **관리 템플릿**)은 현재 비공개 미리 보기로 제공됩니다. 이 업데이트 포함: 관리 템플릿에는 Intune에서 관리할 수 있는 약 300개 설정이 포함됩니다. 이전에는 이러한 설정이 그룹 정책 편집기에만 있었습니다.
관리 템플릿은 공개 미리 보기로 제공 됩니다. 관리 템플릿은 **디바이스 구성** > **관리 템플릿**에서 **디바이스 구성** > **프로필** >**프로필 만들기** > **플랫폼**에서 **Windows 10 이상** 선택, **프로필 유형**에서 **관리 템플릿** 선택으로 이동됩니다.
보고는 사용하도록 설정됩니다. 적용 대상: Windows 10 이상

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune macOS 회사 포털 어두운 모드 <!-- 3300524 -->
Intune macOS 회사 포털은 이제 macOS용 어두운 모드를 지원합니다. macOS 10.14 이상 디바이스에서 어두운 모드를 활성화하면 회사 포털은 해당 모드를 리플렉션하는 색으로 모양을 조정합니다.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>웹 데이터에 대한 APP(앱 보호 정책) 설정 <!-- 2662995 -->
Android 및 iOS 디바이스의 웹 콘텐츠에 대한 APP 정책 설정은 iOS 유니버설 링크 및 Android 앱 링크를 통한 데이터 전송을 비롯하여 http 및 https 웹 링크를 모두 더 잘 처리하기 위해 업데이트됩니다.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>다른 MDM에서 사용하는 Apple VPP 토큰 <!-- 1488946 -->
Intune과 다른 MDM에서 모두 Apple VPP(대량 구매 프로그램) 토큰을 사용하고 있으면 Intune에서 세부 정보를 검색하고 표시합니다.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>디바이스 준수 대시보드에 사용 중지된 디바이스가 있음 <!-- 1981119 -->
향후 업데이트에서는 사용 중지된 디바이스가 디바이스 준수 대시보드에서 제거됩니다. 이에 따라 규정 준수 번호도 변경됩니다.


## <a name="notices"></a>알림

이번에는 활성 알림이 없습니다.

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.



