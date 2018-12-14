---
title: Microsoft Intune을 사용하여 Windows 10 앱 배포
titlesuffix: ''
description: Microsoft Intune으로 사용할 수 있는 Windows 10 앱 시나리오에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 00e8b0e35514fe583027d15fdcc810295aa9fa9e
ms.sourcegitcommit: 88f760abcea7348a0c6d00b533b54a6ff68d3985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977289"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Microsoft Intune을 사용하여 Windows 10 앱 배포 

현재 Microsoft Intune은 Windows 10 장치에서 다양한 앱 형식 및 배포 시나리오를 지원합니다. Intune에 앱이 추가되면 사용자와 장치에 해당 앱을 할당할 수 있습니다. 다음 정보에서는 지원되는 Windows 10 시나리오와 관련된 자세한 세부 정보를 제공합니다. 또한 Windows에 앱을 배포할 때 참고할 키 정보도 제공합니다. 

기간 업무(LOB) 앱 및 비즈니스용 Microsoft 스토어 앱은 Windows 10 장치에서 지원되는 앱 형식입니다. Windows 앱의 파일 확장명에는 **.msi**, **.appx** 및 **.appxbundle**이 포함됩니다.  

> [!Note]
> 최신 앱을 배포하는 데 필요한 최소 Windows 10 업데이트는 다음과 같습니다.
> - Windows 10 1803의 경우, [2018년 5월 23일—KB4100403(OS 빌드 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403)입니다.
> - Windows 10 1709의 경우, [2018년 6월 21일—KB4284822(OS 빌드 16299.522)](https://support.microsoft.com/help/4284822)입니다.

## <a name="windows-10-line-of-business-apps"></a>Windows 10 기간 업무 앱

서명하고 Intune 관리자 콘솔에 업로드한 Windows 10 LOB 앱에는 UWP(유니버설 Windows 플랫폼) 앱 및 Windows 앱 패키지(AppX) 같은 최신 앱뿐만 아니라, 간단한 MSI(Microsoft Installer) 패키지 파일 같은 Win 32 앱도 포함될 수 있습니다. LOB 앱의 업데이트는 매번 관리자가 수동으로 업로드하고 배포해야 합니다. 배포되는 업데이트는 사용자 개입 없이 앱이 설치된 최종 사용자 장치에서 자동으로 설치됩니다. 사용자에게 업데이트에 대한 제어권이 없습니다. 

## <a name="microsoft-store-for-business-apps"></a>비즈니스용 Microsoft 스토어 앱

비즈니스용 Microsoft 스토어 관리자 포털에서 구매한 최신 앱인 비즈니스용 Microsoft 스토어 앱은 관리용 Microsoft Intune에 동기화됩니다. 이 앱은 **온라인에서 라이선스**되거나 **오프라인에서 라이선스**될 수 있습니다. 비즈니스용 Microsoft 스토어 앱의 업데이트는 관리자에 의한 추가 작업이 필요 없이 Microsoft Store에서 직접 관리합니다. 관리자는 사용자 지정 URI(Uniform Resource Identifier)를 사용하여 특정 앱에 대한 업데이트를 방지할 수 있습니다. 자세한 내용은 [엔터프라이즈 앱 관리 - 앱의 자동 업데이트 방지](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates)를 참조합니다. 장치에서 최종 사용자는 모든 비즈니스용 Microsoft 스토어 앱에 대한 업데이트를 사용하지 못하도록 설정할 수도 있습니다. 

## <a name="installing-apps-on-windows-10-devices"></a>Windows 10 장치에서 앱 설치
앱 형식에 따라 두 가지 방법 중 하나로 Windows 10 장치에 앱을 설치할 수 있습니다.

- **사용자 컨텍스트**: 사용자 컨텍스트에서 앱을 배포할 경우 관리되는 앱은 사용자가 디바이스에 로그인할 때 해당 사용자를 위해 디바이스에 설치됩니다. 사용자가 장치에 로그인할 때까지 앱 설치는 성공할 수 없습니다. 
    - 최신 기간 업무 앱 및 비즈니스용 Microsoft 스토어 앱(온라인 및 오프라인)은 사용자 컨텍스트에서 배포될 수 있으며 필수적이고 사용 가능한 의도를 지원합니다.
    - **사용자 모드** 또는 **이중 모드**로 빌드된 Win32 앱은 사용자 컨텍스트에서 배포할 수 있으며 **필수** 및 **사용 가능** 의도를 모두 지원합니다. 
- **디바이스 컨텍스트**: 디바이스 컨텍스트에서 앱을 배포하면 Intune에서 관리되는 앱을 디바이스에 직접 설치합니다.
    - 최신 기간 업무 앱 및 오프라인에서 라이선스된 비즈니스용 Microsoft Store 앱은 디바이스 컨텍스트에서 배포될 수 있으며 필수적인 의도만 지원합니다.
    - **컴퓨터 모드** 또는 **이중 모드**로 빌드된 Win32 앱은 사용자 컨텍스트에서 배포할 수 있으며 **필수** 의도만 지원합니다.

> [!NOTE]
> **이중 모드** 앱으로 빌드된 Win32 앱의 경우 관리자는 해당 인스턴스와 연결된 모든 할당에 대해 앱이 **사용자 모드** 또는 **컴퓨터 모드** 중 어떤 모드의 앱으로 작동하도록 할지 선택해야 합니다. 배포 컨텍스트를 할당마다 변경할 수는 없습니다.  

장치 컨텍스트에서 앱을 배포하면 설치가 장치 컨텍스트를 지원하는 장치를 대상으로 하는 경우에만 성공할 수 있습니다. 또한 장치 컨텍스트에서 배포가 지원하는 조건은 다음과 같습니다.
- 앱이 장치 컨텍스트에서 배포되고 사용자를 대상으로 하는 경우 관리자 콘솔에 표시되는 다음 상태 및 오류로 인해 설치가 실패합니다.
    - 상태: 실패
    - 오류: 사용자는 디바이스 컨텍스트 설치를 대상으로 할 수 없습니다.
- 앱이 장치 컨텍스트에서 배포되지만 장치 컨텍스트를 지원하지 않는 장치를 대상으로 하는 경우 관리자 콘솔에 표시되는 다음 상태 및 오류로 인해 설치가 실패합니다.
    - 상태: 실패
    - 오류: 이 플랫폼은 디바이스 컨텍스트 설치를 지원하지 않습니다. 

> [!Note]
> 특정 배포를 사용하여 앱 할당이 저장되면 최신 앱을 제외하고 해당 할당에 대한 컨텍스트를 변경할 수 없습니다. 최신 앱의 경우 사용자 컨텍스트에서 장치 컨텍스트로 컨텍스트를 변경할 수 있습니다. 

단일 사용자/장치에서 정책 충돌이 발생하는 경우 마지막 정책을 결정하는 데 사용할 정책 우선 순위는 다음과 같습니다.
- 장치 컨텍스트 정책은 사용자 컨텍스트 정책보다 우선 순위가 높습니다. 
- 설치 정책이 제거 정책보다 우선 순위가 높습니다.

Microsoft Intune을 사용하여 앱을 할당하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 그룹에 앱 할당](apps-deploy.md) 및 [Microsoft Intune에서 앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요. Intune의 앱 형식에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](apps-add.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- 그룹에 앱을 할당하는 방법에 대한 자세한 내용은 [Microsoft intune을 사용하여 그룹에 앱 할당](apps-deploy.md)을 참조하세요.
- 앱 할당 모니터링에 대한 자세한 내용은 [앱을 모니터링하는 방법](apps-monitor.md)을 참조하세요.
