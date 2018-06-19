---
title: 모바일 장치 관리 기관 설정
titlesuffix: Microsoft Intune
description: Intune으로 모바일 장치 관리 기관을 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f903e9dfe5fb30f45806aac5694171814492f2e
ms.sourcegitcommit: 0f1a5d6e577915d2d748d681840ca04a0a2604dd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842274"
---
# <a name="set-the-mobile-device-management-authority"></a>모바일 장치 관리 기관 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

MDM(모바일 장치 관리) 기관 설정에 따라 장치를 관리하는 방법이 결정됩니다. IT 관리자가 MDM 기관을 설정해야 사용자가 관리를 위해 장치를 등록할 수 있습니다.

가능한 구성은 다음과 같습니다.

- **Intune 독립 실행형** - Azure Portal을 사용하여 구성하는 클라우드 전용 관리입니다. Intune에서 제공하는 모든 기능 집합을 포함합니다. [Intune 콘솔에서 MDM 기관을 설정합니다](#set-mdm-authority-to-intune).

- **Intune 하이브리드** - Intune 클라우드 솔루션과 System Center Configuration Manager의 통합입니다. Configuration Manager 콘솔을 사용하여 Intune을 구성합니다. [Configuration Manager에서 MDM 기관을 설정합니다](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Office 365용 모바일 장치 관리**  - Office 365와 Intune 클라우드 솔루션의 통합입니다. Office 365 관리 센터에서 Intune을 구성합니다. Intune 독립 실행형에서 제공되는 기능 중 일부를 포함합니다. Office 365 관리 센터에서 MDM 기관을 설정합니다.

> [!IMPORTANT]
> Configuration Manager 버전 1610 이상과 Microsoft Intune 버전 1705에서는 Microsoft 지원에 문의하여 기존의 관리 장치를 등록 취소했다가 다시 등록할 필요 없이 MDM 기관을 변경할 수 있습니다. 자세한 내용은 [잘못된 MDM 기관 설정을 선택한 경우 수행할 작업](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)을 참조하세요.

## <a name="set-mdm-authority-to-intune"></a>MDM 기관을 Intune으로 설정

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. 주황색 배너를 선택하여 **모바일 장치 관리 기관** 설정을 엽니다.
4. **모바일 장치 관리 기관** 아래에서, 다음 옵션 중에서 MDM 기관을 선택합니다.
   - **Intune MDM 기관**
   - **Configuration Manager MDM 기관**
   - **없음**

   ![Intune의 모바일 장치 관리 기관 설정 화면 스크린샷](media/set-mdm-auth.png)

   MDM 기관을 Intune으로 설정했음을 나타내는 메시지가 표시됩니다.

## <a name="enable-device-enrollment"></a>장치 등록 사용

Intune을 MDM 기관으로 설정하면, 사용자는 회사 포털을 설치하고(iOS, macOS 및 Android) 회사 자격 증명을 추가하거나(Windows) 회사 포털 웹 사이트에 액세스하여(iOS, Android, macOS) 다음과 같은 방법으로 개인적으로 소유한 장치를 등록하고 메일과 같은 리소스에 대한 액세스 권한을 얻을 수 있습니다.

다양한 플랫폼은 등록을 사용하도록 설정하거나 간소화하기 위한 다음과 같은 요구 사항이 있습니다.
- **iOS** - (필수) [Apple MDM 푸시 인증서 가져오기](apple-mdm-push-certificate-get.md) 및 [회사 소유 iOS 장치에 대해 등록 사용](ios-enroll.md)(선택 사항)
- **Android** - (선택 사항) [Android 회사 프로필 사용](android-enroll.md)
- **Windows** - (선택 사항) [자동 등록](windows-enroll.md) 또는 [대량 등록](windows-bulk-enroll.md) 사용
- **macOS** - (필수)[Apple MDM 푸시 인증서 가져오기](apple-mdm-push-certificate-get.md)

### <a name="workflow-of-intune-administration-ui"></a>Intune 관리 UI의 워크플로
Android 또는 Apple 장치 관리를 사용하는 경우 Intune은 이러한 타사 서비스와 통합하는 장치 및 사용자 정보를 보내 해당 장치를 관리합니다.

데이터 공유 동의를 추가하는 시나리오는 다음과 같습니다.
- Android for Work 사용.
- Apple MDM 푸시 인증서를 사용하고 업로드.
- DEP(장비 등록 프로그램), School Manager, Volume Purchasing Program 등의 Apple 서비스 중 하나를 사용.

각각의 경우에 동의는 IT 관리자가 등록을 위해 Google 또는 Apple 장치를 인증했는지 확인하는 것처럼 모바일 장치 관리 서비스 실행에 대해 엄격히 적용됩니다. 새 워크플로가 가동될 때 어떤 정보가 공유되는지 알려주는 설명서는 다음 위치에 있습니다.
- [Intune이 Google에 보내는 데이터](https://aka.ms/Data-intune-sends-to-google)
- [Intune이 Apple에 보내는 데이터](https://aka.ms/data-intune-sends-to-apple)

Microsoft의 GDPR 규정 준수에 대한 자세한 내용은 [보안 센터 - GDPR 규정 준수 평가](https://aka.ms/trust_center_info)를 참조하세요.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 인증서 만료 후 모바일 장치 정리

MDM 인증서는 모바일 장치가 Intune 서비스와 통신할 때 자동으로 갱신됩니다. 모바일 장치가 초기화되거나 일정 기간에 Intune 서비스와 통신하지 못한 경우에는 MDM 인증서가 갱신되지 않습니다. MDM 인증서가 만료되고 180일 후 Azure Portal에서 장치가 제거됩니다.
