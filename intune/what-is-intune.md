---
title: Azure Portal의 Intune 소개
titlesuffix: ''
description: Azure Portal에서 Microsoft Intune을 사용할 수 있습니다. Azure Portal에서 Intune에 대한 기본 사항을 가져옵니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/28/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: ''
ms.openlocfilehash: 4dee2c2204b90a35f0b03e2cd78a6662f67f680d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31032645"
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Azure Portal의 Microsoft Intune 소개


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

다른 Azure 서비스와 비슷하게 Azure Portal에서 Microsoft Intune을 사용할 수 있습니다. Azure 포털 내에서 **Intune**을 선택하여 조직의 모바일 장치, PC 및 앱을 관리할 수 있습니다.

> [!NOTE]
> 이전 버전의 Microsoft Intune을 사용한 경우 다음 정보가 유용할 수 있습니다.
>     * [Azure에서 내 기능은 어디에 있나요?](ui-changes.md)는 Azure로 이동을 통해 변경된 특정 워크플로 및 UI를 보여 주는 참조입니다.
>     * [Azure Portal의 Intune 클래식 그룹](groups-get-started.md)에서는 그룹 관리를 위해 Azure Active Directory 보안 그룹으로 이동하는 의미를 설명합니다.

Azure Portal에서 Microsoft Intune 환경의 주요 특징은 다음과 같습니다.

- 모든 EMS(Enterprise Mobility + Security) 구성 요소에 대한 통합 콘솔
- 웹 표준을 기반으로 하는 HTML 기반 콘솔
- 많은 작업을 자동화하는 Microsoft Graph API 지원
- 모든 Azure 응용 프로그램에서 호환성을 제공하는 Azure AD(Active Directory) 그룹
- 대부분의 최신 웹 브라우저 지원

## <a name="before-you-start"></a>시작하기 전에

Azure Portal에서 Intune을 사용하려면 Intune 관리 및 테넌트 계정이 있어야 합니다. 계정이 아직 없는 경우 [계정에 등록](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)하세요.

## <a name="supported-web-browsers-for-the-azure-portal"></a>Azure Portal에 대해 지원되는 웹 브라우저

Azure Portal은 대부분의 최신 PC, Mac 및 태블릿에서 실행됩니다. 휴대폰은 지원되지 않습니다.
현재 지원되는 브라우저는 다음과 같습니다.

- Microsoft Edge(최신 버전)
- Microsoft Internet Explorer 11
- Safari(최신 버전, Mac만)
- Chrome(최신 버전)
- Firefox(최신 버전)

지원되는 브라우저에 대한 최신 정보는 [Azure Portal](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices)을 참조하세요.

## <a name="microsoft-intune-in-the-azure-portal"></a>Azure Portal의 Microsoft Intune

[Azure portal](https://portal.azure.com)은 Microsoft Intune 서비스를 찾을 수 있는 곳입니다. Azure에는 여러 서비스가 있으며, 이 중 상당수는 정기적으로 사용하지 않는 서비스일 것입니다. 사용자 포털 환경을 사용자 지정하는 빠른 가이드는 [Azure Portal에서 Intune 시작](get-started-azure.md)을 참조하세요.

## <a name="the-microsoft-intune-documentation"></a>Microsoft Intune 문서

이 항목뿐만 아니라 전체 Microsoft Intune 설명서가 지속적으로 업데이트됩니다. 제안 사항이 있는 경우 항목 설명에 의견을 남겨 주세요. 여러분의 의견을 듣고 싶습니다.

설명서에는 필요한 정보를 보다 쉽게 찾을 수 있도록 Azure Portal에서 Microsoft Intune의 레이아웃(아래 참조)이 반영됩니다.

![Azure Portal 워크로드](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>문서 가이드

다음 표를 사용하면 Microsoft Intune의 주요 영역을 신속하게 찾아 이해하는 데 유용합니다.

| 섹션                                                      | 설명                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [소개 및 시작](introduction-intune.md)       | 다음과 같은 Intune 기본 이해:<br /> - 일반적인 솔루션<br /> – Microsoft Intune 작동하는 방식<br /> – Intune에서 장치 관리<br /> – Intune에서 앱 관리<br /> - 장치 등록을 하거나 하지 않는 EMM(엔터프라이즈 이동성 관리).                                                         |
| [계획 및 디자인](planning-guide.md)                         | Microsoft Intune 환경을 성공적으로 계획하고 설계하는 데 유용한 지침입니다.                                                                                                                                                                                                             |
| [장치 등록](device-enrollment.md)                    | Microsoft Intune이 Intune 서비스에 장치를 등록하여 작업자의 장치를 관리하도록 도움을 주는 방법을 이해합니다. 작업자의 장치를 등록하는 몇 가지 방법이 있습니다.                                                                                                         |
| [장치 정책 준수](device-compliance.md)                    | Intune 장치 준수 정책은 장치가 Microsoft Intune에서 준수되는 것으로 간주하기 위해 준수해야 하는 규칙 및 설정을 정의합니다. 예를 들어 장치 액세스에 대한 암호 필요, 장치를 암호화, 최소 OS 버전 요구 등은 모두 규정 준수의 예입니다. |
| [장치 구성](device-profiles.md)                   | 장치 프로필을 만들어 Microsoft Intune을 사용하여 관리하는 모든 장치의 설정 및 기능을 구성합니다. 예를 들어, 알림, 데이터 공유, 이메일 지원, wifi 연결, 인증서 및 끝점 보호와 같은 기능을 구성할 수 있습니다.              |
| [장치](device-management.md)                              | 관리하는 장치가 위험으로부터 회사 데이터를 보호하는 동안 최종 사용자가 해당 작업을 수행해야 하는 리소스를 제공하도록 해야 합니다. 작업자 장치 인벤토리를 검토하고 원격 장치 작업을 수행하여 장치를 관리합니다.                                                      |
| [모바일 앱](app-management.md)                             | 앱을 추가, 배포, 모니터링, 구성 및 보호하는 방법을 이해합니다.                                                                                                                                                                                                                             |
| [조건부 액세스](conditional-access.md)                  | 회사 데이터에 액세스를 게이트로 제어하는 장치 및 앱 기반 조건을 정의합니다.                                                                                                                                                                                                            |
| [사용자](users-add.md)                                        | 관리하는 장치 및 앱의 사용자를 추가하는 방법에 대해 알아봅니다.                                                                                                                                                                                                                                           |
| [그룹](groups-get-started.md)                              | intune을 사용해 그룹을 만들고 관리하는 방법에 대해 알아봅니다. 그룹을 사용하여 장치, 앱 구성 및 보호 정책을 빠르게 지정할 수 있습니다.                                                                                                                                             |
| [Intune 역할](role-based-access-control.md)                 | 다양한 Intune 작업을 누가 수행할 수 있는지와 해당 작업을 어떻게 적용할지를 제어하는 방법에 대해 알아봅니다. 몇 가지 일반적인 Intune 시나리오에 적용되는 기본 제공 역할을 사용하거나, 사용자 고유의 역할을 만들 수 있습니다.                                                                                 |
| [소프트웨어 업데이트](windows-update-for-business-configure.md) | Windows 10 장치용 소프트웨어 업데이트를 구성하는 방법에 대해 알아봅니다.                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>새로운 기능은 무엇입니까?

Microsoft Intune의 최신 기능에 대해 알아보려면 [새로운 기능](whats-new.md)을 참조하세요.
