---
title: 회사 데이터에 대한 무단 액세스 방지
titlesuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 회사 네트워크 외부에서 공유하는 경우 회사 데이터에 대한 무단 액세스를 방지합니다.
keywords: 외부 네트워크 회사 데이터를 보호하는 Office 365 O365 Azure Information Protection 데이터
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6a88573a-aa60-455c-858c-74562798246b
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d8ae737ee11f176c036382fbe77122ecebb722d2
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190016"
---
# <a name="prevent-unauthorized-access-to-company-data-using-microsoft-intune"></a>Microsoft Intune을 사용하여 회사 데이터에 대한 무단 액세스 방지

권한 있는 사용자만 데이터에 액세스할 수 있도록 Office 365 문서 및 전자 메일을 분류, 레이블 지정 및 보호할 수 있습니다. IT 관리자 또는 사용자가 규칙과 조건을 설정하면 설정이 자동으로 관리됩니다. 또는 IT 팀에서 사용자가 따라야 할 권장 설정을 제공할 수 있습니다. 또한 관리자와 사용자는 다른 기관의 도움 없이 다른 사용자와 이미 공유된 데이터에 대한 액세스 권한을 취소할 수도 있습니다. 이 작업의 결과는 데이터가 회사 네트워크를 떠나는 경우에도 보호된 데이터를 열거나 업데이트하는 사람을 제어하는 것입니다. 

## <a name="before-you-begin"></a>시작하기 전에

다음 요구 사항이 충족되면 뒤에서 설명하는 작업 계획을 사용할 수 있습니다.
* 회사에서 클라우드로 안전하게 전환할 준비가 되었습니다.
* 회사에서 Office 365 Exchange Online, SharePoint Online, 비즈니스용 OneDrive 또는 Yammer를 사용합니다.
* 회사에서 Microsoft 365, EMS(Enterprise Mobility + Security) 또는 Azure Information Protection에 대한 라이선스를 가지고 있습니다.
* 회사에서 Windows 7 서비스 팩 1 이상을 실행하는 장치를 사용합니다.
* 회사에서 2016 앱 또는 2013 앱, Office Professional Plus 2016, Office Professional Plus 2013(서비스 팩 1 포함) 또는 Office Professional Plus 2010과 함께 Office 365 ProPlus를 사용합니다.

## <a name="action-plan"></a>작업 계획

[Azure Information Protection 빠른 시작 자습서](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial)를 완료합니다.  

## <a name="what-to-tell-employees-and-students"></a>직원 및 학생에게 정보 안내

[중요한 정보가 포함된 문서와 전자 메일을 보호하는 방법 및 시기](https://docs.microsoft.com/information-protection/deploy-use/help-users)에 대한 세부 정보를 공유할 수 있습니다.

## <a name="next-steps"></a>다음 단계

다음 단계의 일부로, 다음을 비롯하여 회사 데이터의 보안을 향상할 수 있는 다른 방법에 대해 자세히 알아볼 수 있습니다. 

* [iOS 및 Android 장치에서 Azure Information Protection]를 사용하는 방법에 대해 알아봅니다(https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq.
* Windows Phone 및 Mac 컴퓨터의 경우 [Microsoft Rights Management 공유 응용 프로그램](https://technet.microsoft.com/dn451248)에 대해 알아봅니다.
