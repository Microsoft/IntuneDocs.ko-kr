---
title: Microsoft Intune - Azure를 사용하여 장치 세부 정보 보기 | Microsoft Docs
description: 운영 체제, 저장 공간, 제조업체 및 모델을 비롯한 장치 세부 정보를 봅니다. Azure에서 Microsoft Intune을 사용하여 설치된 앱의 목록을 가져오고, 준수 정책을 확인하고, TeamViewer를 설정합니다. 관리하는 장치의 인벤토리 보기와 유사합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f66c0695c7e3d1f4bb7a5ca3abceeb13f6af41f2
ms.sourcegitcommit: 3c4ea8d6809a63042705b5ed4f25ba80f522070e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2018
ms.locfileid: "34051609"
---
# <a name="see-device-details-in-intune"></a>Intune에서 장치 세부 정보 참조

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**장치** 기능은 하드웨어 및 설치된 앱을 비롯하여 관리하는 장치에 추가 세부 정보를 제공합니다.

이 문서는 Azure Portal에서 모든 장치 및 해당 속성을 보는 방법을 보여줍니다.

## <a name="view-the-device-details"></a>장치 세부 정보 보기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치** > **모든 장치** 선택 > 해당 세부 정보를 열려면 나열된 장치 중 하나를 선택합니다.

   - **개요**는 장치 이름을 표시하고, 체크 인할 경우 BYOD(bring-your-own-device) 장치인지 여부 등을 포함한 장치의 몇 가지 주요 속성을 나열합니다. **자세히**를 선택하여 다음을 수행합니다.
     - 회사 데이터 제거
     - 장치 삭제
     - 장치 원격 잠금
     - 지우기
     - 원격 지원 세션 시작
   - **속성**을 사용하여 [만든 장치 범주](device-group-mapping.md)를 할당하고, 장치 소유권을 개인 장치나 회사 장치로 변경합니다.
   - **하드웨어**에는 장치 ID, 운영 체제 및 버전, 저장소 공간, 모델 및 제조업체, 조건부 액세스 설정 및 자세한 세부 정보를 포함한 장치에 대한 많은 세부 정보가 포함됩니다.
   - **검색된 앱**은 Intune이 장치에 설치한 모든 앱 및 앱 버전을 표시합니다. 앱 목록을 .csv 파일로 **내보내기**할 수 있습니다.
   - **장치 준수**는 모든 할당된 준수 정책 및 장치가 준수 또는 비준수인지 여부를 표시합니다.
   - **장치 구성**은 장치에 할당된 모든 장치 구성 정책 및 정책이 성공 또는 실패인지 여부를 표시합니다.

Intune은 회사 소유 장치에서만 앱 목록을 수집합니다. 앱이 개인 장치에서 확인되지 않습니다. Windows 10 PC의 경우 최신 앱만이 회사 소유 장치에서 나열됩니다. Intune은 장치에서 Win32 앱에 대한 정보는 수집하지 않습니다. 장치별 이동 통신 사업자에 따라 일부 앱을 수집하지 않을 수 있습니다.

|플랫폼|개인 소유 장치|회사 소유 장치|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10(Configuration Manager 클라이언트 없음)|관리되는 앱만|관리되는 앱만|
|Windows 8.1(Configuration Manager 클라이언트 없음)|관리되는 앱만|관리되는 앱만|  
|Windows Phone 8|관리되는 앱만|관리되는 앱만|  
|Windows RT|관리되는 앱만|관리되는 앱만|  
|iOS|관리되는 앱만|장치에 설치되는 모든 앱|
|macOS|장치에 설치되는 모든 앱|장치에 설치되는 모든 앱|  
|Android|관리되는 앱만|장치에 설치되는 모든 앱|  

## <a name="next-steps"></a>다음 단계
Intune을 사용하여 [장치를 관리](device-management.md)하기 위해 수행할 수 있는 작업을 참조하세요.