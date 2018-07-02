---
title: 정책을 사용하여 Windows PC 관리 간소화
titlesuffix: Microsoft Intune
description: Windows PC 관리 정책 및 Microsoft Intune Center에 대한 설정을 설명합니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0afda7e-f4c3-4bcd-b4bf-4304103cf73e
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic-keep
ms.openlocfilehash: 5d026ee3c9a6461e327c952a3d702936907d59b5
ms.sourcegitcommit: 116be0eaa44fd5518ff34780d39569224ef4746b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36310524"
---
# <a name="use-policies-to-simplify-windows-pc-management"></a>정책을 사용하여 Windows PC 관리 간소화

[!INCLUDE [classic-portal](includes/classic-portal.md)]

PC에서 Intune 소프트웨어 클라이언트를 실행하여 Windows 데스크톱을 PC로 관리하기 위해서는 Intune 관리 콘솔의 **컴퓨터 관리** 정책에 있는 정책만 사용할 수 있습니다. 관리 콘솔에 나열된 다른 모든 정책은 모바일 장치 전용입니다. **컴퓨터 관리** 정책을 사용하여 Microsoft Intune Center에서 설정을 구성하고, PC에 대한 업데이트를 제어하고, PC에 대한 Windows 방화벽을 구성할 수 있습니다.

![Windows PC의 정책 템플릿](media/pc_policy_template.png)

### <a name="manage-the-microsoft-intune-center"></a>Microsoft Intune Center 관리
사용자에게는 Intune 소프트웨어 클라이언트가 **Microsoft Intune Center**로 표시됩니다. Microsoft Intune Center를 통해 사용자는 다음을 수행할 수 있습니다.

-   회사 포털에서 응용 프로그램 가져오기

-   업데이트 확인

-   Microsoft Intune Endpoint Protection 관리

-  원격 지원 요청

Microsoft Intune Center는 모든 관리 컴퓨터에 설치됩니다. Intune 정책에서 다음 설정을 구성할 수 있으며 이러한 설정은 Microsoft Intune Center에 표시됩니다.

|정책 설정|세부 정보|
|------------------|--------------------|
|**Name**|컴퓨터를 관리하는 관리자의 이름<br />최대 길이: 40자|
|**전화 번호**|컴퓨터를 관리하는 관리자의 전화번호<br />최대 길이: 20자|
|**메일 주소**|컴퓨터를 관리하는 관리자의 전자 메일 주소<br />최대 길이: 40자|
|**웹 사이트 이름**|사용자를 위한 지원 웹 사이트 이름<br />>최대 길이: 40자|
|**웹 사이트 URL**|지원 웹 사이트의 URL<br />최대 길이: 150자|
|**참고**|사용자에게 표시되는 참고 사항<br />최대 길이: 120자|

Windows PC에 대해 구성할 수 있는 정책 및 설정에 대한 자세한 내용은 다음 리소스를 참조하세요.

- [Microsoft Intune에서 소프트웨어 업데이트를 사용하여 Windows PC를 최신 상태로 유지](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) - 이 정책을 사용하면 관리되는 컴퓨터를 확인하고 Microsoft 및 타사의 소프트웨어 업데이트를 다운로드할 수 있습니다. Windows 7에서 Windows 10으로 업그레이드하거나 Windows 10의 특정 버전에서 최신 버전으로 업그레이드하는 등의 작업은 이러한 업데이트에 포함되지 않습니다.

- [Microsoft Intune용 Endpoint Protection을 사용한 Windows PC의 보안 유지 방법](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) - 이러한 설정에는 검색 일정 및 맬웨어 검색 시 수행할 작업이 포함됩니다.

- [Microsoft Intune에서 Windows 방화벽 정책을 사용하여 Windows PC 보호](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) - 이러한 정책을 사용하면 관리 컴퓨터에서 Windows 방화벽 설정을 쉽게 관리할 수 있습니다.


### <a name="see-also"></a>참고 항목

[Intune 소프트웨어 클라이언트를 사용하는 일반 Windows PC 관리 작업](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
