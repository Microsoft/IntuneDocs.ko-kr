---
title: Azure에서 Intune 기능은 어디에 있나요?
titleSuffix: Microsoft Intune
description: Azure Portal에서 Microsoft Intune 기능을 찾는 데 도움이 되는 정보를 제공합니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 1/4/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 861be39feab15c453fd102593b0501202faa3684
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232939"
---
# <a name="where-did-my-intune-feature-go-in-azure"></a>Azure에서 Intune 기능은 어디에 있나요?
Intune 기능을 Azure Portal로 이동하면서 일부 작업을 더 논리적으로 구성할 수 있게 되었습니다. 하지만 개선 작업을 진행할 때마다 항상 새 구성을 학습하는 비용이 발생하게 됩니다. 이 참조 가이드는 클래식 포털의 Intune에 완전히 익숙하고 Azure Portal의 Intune에서 작업을 수행하는 방법을 궁금해하는 사용자를 위한 것입니다. 찾고 있는 기능이 이 문서에서 다루어지지 않은 경우 Microsoft에서 문서를 업데이트할 수 있도록 문서 하단에 의견을 남겨주세요.
## <a name="quick-reference-guide"></a>빠른 참조 가이드

|기능 |클래식 포털의 경로|Azure Portal의 Intune 경로|
|------------|---------------|---------------|
|DEP(장치 등록 프로그램)[iOS만 해당]|관리 > 모바일 장치 관리 > iOS > 장치 등록 프로그램|[장치 등록 > Apple 등록 > 등록 프로그램 토큰](#where-did-apple-dep-go) |
|DEP(장치 등록 프로그램)[iOS만 해당]| 관리 > 모바일 장치 관리 > iOS 및 Mac OS X > 장치 등록 프로그램 |[장치 등록 > Apple 등록 > 등록 프로그램 일련 번호](#where-did-apple-dep-go) |
|등록 규칙 |관리 > 모바일 장치 관리 > 등록 규칙|[장치 등록 > 등록 제한](#where-did-enrollment-rules-go) |
|iOS 일련 번호 기준 그룹 |그룹 > 모든 장치 > 회사에서 사전 등록한 장치 > iOS 일련번호 기준|[장치 등록 > Apple 등록 > 등록 프로그램 일련 번호](#where-did-corporate-pre-enrolled-devices-go) |
|iOS 일련 번호 기준 그룹 |그룹 > 모든 장치 > 회사에서 사전 등록한 장치 > iOS 일련번호 기준| [장치 등록 > Apple 등록 > AC 일련 번호](#where-did-corporate-pre-enrolled-devices-go)|
|IMEI 기준 그룹(모든 플랫폼)| 그룹 > 모든 장치 > 회사에서 사전 등록한 장치 > IMEI 기준(모든 플랫폼) | [장치 등록 > 회사 장치 식별자](#by-imei-all-platforms)|
| 회사 장치 등록 프로필| 정책 > 회사 장치 등록 | [장치 등록 > Apple 등록 > 등록 프로그램 프로필](#where-did-corporate-pre-enrolled-devices-go) |
| 회사 장치 등록 프로필 | 정책 > 회사 장치 등록 | [장치 등록 > Apple 등록 > AC 프로필](#where-did-corporate-pre-enrolled-devices-go) |
| Android for Work | 관리 > 모바일 장치 관리 > Android for Work | 장치 등록 > Android for Work 등록 |
| 사용 약관 | 정책 > 사용 약관 정보 | 장치 등록 > 사용 약관 |
회사 포털 설정|관리 > 회사 포털|**관리** > 모바일 앱<br> **설정** > 회사 포털 브랜딩


## <a name="where-do-i-manage-groups"></a>그룹은 어디에서 관리하나요?
Azure Portal의 Intune은 [Azure AD(Active Directory)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)를 사용하여 그룹을 관리합니다.

## <a name="where-did-enrollment-rules-go"></a>등록 규칙은 어디에 있나요?
클래식 포털에서는 모바일 장치와 최신 Windows 및 macOS 장치의 MDM 등록을 제어하는 규칙을 설정할 수 있었습니다.

![클래식 모바일 장치 등록 규칙의 이미지](./media/01-classic-rules.png)

이러한 규칙은 Intune 계정의 모든 사용자에게 예외 없이 적용되었습니다. Azure Portal에서는 이제 이러한 규칙이 장치 유형 제한과 장치 개수 제한이라는 두 가지 고유한 정책 유형으로 나타납니다.

![Azure 모바일 장치 등록 제한의 이미지](./media/02-azure-enroll-restrictions.png)

기본 장치 개수 제한은 클래식 포털의 장치 등록 제한에 해당됩니다.

![Azure 장치 개수 제한의 이미지](./media/03-azure-device-limit.png)

기본 장치 유형 제한은 클래식 포털의 플랫폼 제한에 해당됩니다.

![Azure 장치 유형 제한의 이미지](./media/04-azure-platform-restrictions.png)

개인이 소유하는 장치를 허용하거나 차단할 수 있는 기능은 이제 장치 유형 제한의 플랫폼 구성에서 관리됩니다.

![Azure 개인 장치 차단 설정의 이미지](./media/05-azure-personal-block.png)

새로운 제한 기능은 Azure Portal에만 추가됩니다.

## <a name="where-did-my-conditional-access-policies-go"></a>조건부 액세스 정책은 어디로 이동했습니까?
테넌트가 Azure Portal로 마이그레이션된 후 테넌트의 조건부 액세스 정책이 계속 적용됩니다. 그러나 Azure Portal에서는 Intune의 조건부 액세스 정책을 보고 수정할 수 없습니다.

Azure Portal에서 조건부 액세스 정책을 보고 변경하려면 클래식 포털에서 이전 정책을 제거해야 합니다. 그런 다음, Azure Portal에서 다시 만듭니다. 조건부 액세스 정책을 마이그레이션하는 방법에 대한 자세한 내용은 [Azure Portal에서 클래식 정책 마이그레이션](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-migration)을 참조하세요. 

## <a name="where-did-my-compliance-policies-go"></a>준수 정책이 어디로 이동했습니까?
테넌트가 Azure Portal로 마이그레이션된 후 테넌트의 준수 정책이 계속 적용됩니다. 그러나 Azure Portal에서는 Intune의 조건부 액세스 정책을 보고 수정할 수 없습니다.

Azure Portal에서 준수 정책을 보고 변경하려면 클래식 포털에서 이전 정책을 제거해야 합니다. 그런 다음, Azure Portal에서 다시 만듭니다. 장치 준수 정책에 대한 자세한 내용은 [Intune에서 장치 준수 정책 시작](https://docs.microsoft.com/en-us/intune/known-issues#compliance)을 참조하세요. 

## <a name="where-did-apple-dep-go"></a>Apple DEP는 어디에 있나요?
클래식 포털에서는 Apple 장비 등록 프로그램과 통합되도록 Intune을 설정하고 Apple 서비스와의 동기화를 수동으로 요청할 수 있었습니다.

![클래식 DEP 토큰의 이미지](./media/06-classic-dep-token.png)

Azure Portal에서는 Intune 클래식에서와 동일한 단계를 통해 Apple 장비 등록 프로그램을 설정합니다.

![Azure DEP 토큰의 이미지](./media/07-azure-dep-token.png)

하지만 클래식 포털의 **동기화** 옵션은 일련 번호 관리 워크플로로 이동되었습니다. 수동 동기화 결과가 해당 워크플로에 표시되기 때문입니다.

![Azure DEP 동기화의 이미지](./media/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>회사에서 사전 등록한 장치는 어디에 있나요?
### <a name="by-ios-serial-number"></a>iOS 일련 번호 기준
클래식 포털에서는 Apple DEP(장비 등록 프로그램) 및 Apple Configurator 도구를 통해 iOS 장치를 등록할 수 있습니다. 두 방법 모두 일련 번호로 장치를 사전 등록하며 특별한 회사 장치 등록 프로필을 할당합니다. 등록 전에는 **Corporate Pre-enrolled Device by iOS Serial Number**(iOS 일련 번호를 기준으로 회사에서 사전 등록한 장치) 장치 그룹을 통해 등록 프로필 할당을 관리할 수 있습니다.

![클래식 Apple 일련 번호의 이미지](./media/09-classic-apple-serials.png)

여기에는 Apple DEP 및 Configurator 등록 모두의 일련 번호가 하나의 목록으로 나열됩니다. 프로필 할당 불일치(DEP 프로필에서 AC 일련 번호로, 또는 그 반대)를 줄이기 위해 Azure Portal에서는 일련 번호를 두 개의 목록으로 구분했습니다.

**DEP 일련 번호**
![Azure DEP 일련 번호의 이미지](./media/10-azure-dep-serials.png)

**Apple Configurator 일련 번호**
![Azure Apple Configurator 일련 번호의 이미지](./media/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>IMEI 기준(모든 플랫폼)

클래식 포털에서는 장치를 Intune에 등록했을 때 장치의 IMEI 번호를 미리 나열하여 장치를 회사 소유로 표시할 수 있습니다.

![IMEI 번호 클래식 목록의 이미지](./media/12-classic-corp-imei.png)

Azure Portal에서는 CSV(쉼표로 구분된 값) 파일을 사용하여 동일한 IMEI를 회사 장치 식별자 목록에 업로드해야 합니다. 새 포털에서는 IMEI 번호를 수동으로 입력할 수 없습니다.

![Azure IMEI 번호 목록의 이미지](./media/13-azure-corp-imei.png)

Azure Portal의 Intune은 향후에도 IMEI 외에 다른 식별자 형식을 지원할 예정이지만 현재는 IMEI 번호만 미리 나열할 수 있습니다.

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>회사 장치 등록 프로필은 어디에 있나요?
Apple 장비 등록 프로그램이나 Apple Configurator 도구를 통해 iOS 장치를 등록하려면 장치를 할당할 회사 장치 등록 프로필을 제공해야 합니다. 클래식 포털에서는 이러한 프로필을 만들고 관리하는 작업이 한 목록에 있었습니다.

![클래식 장치 등록 프로필의 이미지](./media/14-classic-corp-profiles.png)

이 목록에서는 Apple 장비 등록 프로그램에서 사용하도록 설정된 프로필(**DEP On**(DEP 설정)) 및 Apple Configurator 도구에서만 사용하도록 설정된 프로필(**DEP Off**(DEP 해제))을 표시합니다.

두 프로필 유형 간의 혼동과, DEP 프로필을 Configurator 장치로 또는 그 반대로 잘못 일치하게 할당하는 가능성을 줄이기 위해 등록 프로그램 프로필(Apple 장비 등록 프로그램 및 Apple School Manager 모두 지원)의 만들기 및 관리를 Apple Configurator 프로필의 만들기 및 관리와 분리했습니다.

**DEP 프로필**
![Azure DEP 프로필의 이미지](./media/15-azure-dep-profiles.png)

**Apple Configurator 프로필**
![Azure Apple Configurator 프로필의 이미지](./media/16-azure-ac-profiles.png)
