---
title: macOS 장치에 대한 등록 설정
titlesuffix: Microsoft Intune
description: Intune에서 macOS 장치 등록을 설정하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 85a05f4816692d3bccfe695c7e69f54d007f3b59
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187007"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Intune에서 macOS 장치 등록 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune에서는 macOS 장치를 관리하여 사용자에게 회사 전자 메일 및 앱에 대한 액세스 권한을 부여할 수 있습니다.

Intune 관리자는 회사 소유 macOS 장치와 개인 소유 macOS 장치("Bring Your Own Device" 또는 BYOD)에 대해 등록을 설정할 수 있습니다. 

## <a name="prerequisites"></a>전제 조건

macOS 장치 등록을 설정하기 전에 다음 필수 구성 요소를 완료합니다.

- [도메인 구성](custom-domain-name-configure.md)
- [MDM 기관 설정](mdm-authority-set.md)
- [그룹 만들기](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [회사 포털 구성](company-portal-app.md)
- [Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)에서 사용자 라이선스 할당
- [Apple MDM Push Certificate 가져오기](apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>사용자 소유 macOS 장치(BYOD)

사용자가 Intune 관리에 대해 개인 장치를 등록하도록 할 수 있습니다. 이를 "Bring Your Own Device" 또는 BYOD라고 합니다. 필수 사전 작업을 완료하고 사용자 라이선스를 할당하면 사용자는 다음과 같은 방법으로 장치를 등록할 수 있습니다.
- [회사 포털 웹 사이트](https://portal.manage.microsoft.com)로 이동
- 회사 포털 앱 다운로드
또한 온라인 등록 단계: [macOS Intune에서 장치 등록](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)에 대한 링크를 최종 사용자에게 전송할 수 있습니다.

최종 사용자의 다른 작업에 대한 정보는 다음 문서를 참조하세요.

- [Microsoft Intune에서 최종 사용자 환경 관련 리소스](end-user-educate.md)
- [Intune에서 macOS 장치 사용](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>회사 소유 macOS 장치
사용자를 위해 장치를 구입하는 조직의 경우, Intune은 다음과 같은 macOS 회사 소유 장치 등록 방법을 지원합니다.
- [Apple의 DEP(장비 등록 프로그램)](device-enrollment-program-enroll-macos.md): 조직은 Apple의 DEP(장비 등록 프로그램)를 통해 iOS 장치를 구매할 수 있습니다. DEP를 통해 등록 프로필을 "무선"으로 배포하여 장치를 관리할 수 있습니다.
- [DEM(장치 등록 관리자)](device-enrollment-manager-enroll.md): DEM 계정을 사용하여 최대 1,000개의 장치를 등록할 수 있습니다.

## <a name="block-macos-enrollment"></a>macOS 등록 차단
기본적으로 Intune에서는 macOS 장치의 등록이 허용됩니다. 등록에서 macOS 장치를 차단하려면 [Set device type restrictions](enrollment-restrictions-set.md)(장치 유형 제한 설정)를 참조하세요.

## <a name="enroll-virtual-macos-machines-for-testing"></a>테스트를 위해 macOS 가상 머신 등록

> [!NOTE]
> 테스트에는 macOS 가상 머신만이 지원됩니다. 최종 사용자에 대한 프로덕션 장치로 macOS 가상 머신을 사용하지 않아야 합니다. 

병렬 데스크톱 또는 VMware Fusion 중 하나를 사용하여 테스트를 위해 macOS 가상 머신을 등록할 수 있습니다. 

병렬 데스크톱의 경우 Intune이 인식할 수 있도록 가상 머신의 하드웨어 형식 및 일련 번호를 설정해야 합니다. [하드웨어 형식](http://kb.parallels.com/123594) 및 [일련 번호](http://kb.parallels.com/123455)를 설정하는 병렬 지침에 따라 테스트에 필요한 설정을 지정합니다. 가상 머신을 실행하는 장치의 하드웨어 형식을 사용자가 만드는 가상 머신의 하드웨어 형식과 일치시키는 것이 좋습니다. **Apple 메뉴** > **이 Mac 정보** > **시스템 보고서** > **모델 식별자**에서 이러한 하드웨어 형식을 찾을 수 있습니다. 

VMware Fusion의 경우 [.vmx 파일을 편집](https://kb.vmware.com/s/article/1014782)하여 가상 머신의 하드웨어 모델 및 일련 번호를 설정해야 합니다. 가상 머신을 실행하는 장치의 하드웨어 형식을 사용자가 만드는 가상 머신의 하드웨어 형식과 일치시키는 것이 좋습니다. **Apple 메뉴** > **이 Mac 정보** > **시스템 보고서** > **모델 식별자**에서 이러한 하드웨어 형식을 찾을 수 있습니다. 

## <a name="user-approved-enrollment"></a>사용자 승인됨 등록

사용자 승인됨 MDM 등록은 특정 보안 관련 설정을 관리하는 데 사용할 수 있는 macOS 등록 유형입니다. 자세한 내용은 [Apple의 지원 문서](https://support.apple.com/HT208019)를 참조하세요.

사용자가 승인되려면 최종 사용자가 macOS 회사 포털을 사용하여 등록한 후에 시스템 환경설정을 사용하여 수동으로 승인을 제공해야 합니다. 이 작업에 대한 지침은 macOS 10.13.2 이상에서 사용자의 macOS 회사 포털을 통해 제공됩니다.

장치가 사용자 승인됨 상태인지 확인하려면 Intune 포털로 이동한 다음, **장치** > **모든 장치** > 장치 > **하드웨어**를 선택합니다. **사용자 승인됨** 필드를 확인합니다.

## <a name="next-steps"></a>다음 단계

macOS 장치가 등록되면 [macOS 장치용 사용자 지정 설정을 생성](custom-settings-macos.md)할 수 있습니다.
