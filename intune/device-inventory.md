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
ms.openlocfilehash: 2c47cd8ea136bcead14e70769f63df7b9b8f0e20
ms.sourcegitcommit: b96568a77d3cb6f602e7577446996fe7dde169bd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51610093"
---
# <a name="see-device-details-in-intune"></a>Intune에서 장치 세부 정보 참조

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**장치** 기능은 하드웨어 및 설치된 앱을 비롯하여 관리하는 장치에 추가 세부 정보를 제공합니다.

이 문서는 Azure Portal에서 모든 장치 및 해당 속성을 보는 방법을 보여줍니다.

## <a name="view-the-device-details"></a>장치 세부 정보 보기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치** > **모든 장치** 선택 > 해당 세부 정보를 열려면 나열된 장치 중 하나를 선택합니다.

   - **개요**는 장치 이름을 표시하고, 체크 인할 경우 BYOD(bring-your-own-device) 장치인지 여부 등을 포함한 장치의 몇 가지 주요 속성을 나열합니다. 장치에서 다음 작업을 수행할 수 있습니다.
      - [사용 중지](devices-wipe.md#retire)
        - [초기화](devices-wipe.md#wipe)
        - [원격 잠금](device-remote-lock.md)
        - [장치 동기화](device-sync.md)
        - [암호 초기화](device-passcode-reset.md)
        - [다시 시작](device-restart.md)(Windows만 해당)
        - [새로 시작](device-fresh-start.md)(Windows만 해당)
     - 원격 지원 세션 시작
   - **속성**을 사용하여 [만든 장치 범주](device-group-mapping.md)를 할당하고, 장치 소유권을 개인 장치나 회사 장치로 변경합니다.
   - **하드웨어**에는 장치 ID, 운영 체제 및 버전, 저장소 공간, 모델 및 제조업체, 조건부 액세스 설정 및 자세한 세부 정보를 포함한 장치에 대한 많은 세부 정보가 포함됩니다.
   - **검색된 앱**은 Intune이 장치에 설치한 모든 앱 및 앱 버전을 표시합니다. 앱 목록을 .csv 파일로 **내보내기**할 수 있습니다. 이 목록은 7일마다 업데이트됩니다.
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
|Android Enterprise|관리되는 앱만|작업 프로필에 설치된 앱만|  

## <a name="hardware-device-details"></a>하드웨어 장치 세부 정보
디바이스별 이동 통신 사업자에 따라 일부 세부 정보를 수집하지 않을 수 있습니다.

|세부 정보|설명|플랫폼| 
|--------------|----------------------|----|  
|이름|서버의 이름입니다.|Windows, iOS|
|관리 이름|콘솔에서만 사용되는 장치 이름입니다. 이 이름을 변경해도 장치의 이름을 변경하지 않습니다.|Windows, iOS|
|UDID|장치의 고유한 장치 식별자입니다.|Windows, iOS|
|Intune 장치 ID|장치를 고유하게 식별하는 GUID입니다.|Windows, iOS|
|일련 번호|제조업체에서 장치의 일련 번호입니다.|Windows, iOS|
|공유 장치|**예**인 경우 장치가 둘 이상의 사용자에 의해 공유됩니다.|Windows, iOS|
|사용자 승인 등록|**예**인 경우 장치에는 관리자가 장치에서 특정 보안 설정을 관리할 수 있는 사용자 승인 등록이 있습니다.|Windows, iOS|
|운영 체제|장치에서 사용된 운영 체제입니다.|Windows, iOS|
|운영 체제 버전|장치의 운영 체제 버전입니다.|Windows, iOS|
|운영 체제 언어|장치의 운영 체제에 대해 설정된 언어입니다.|Windows, iOS|
|총 저장소 공간|장치에서 총 저장소 공간(기가바이트)입니다.|Windows, iOS|
|사용 가능한 저장소 공간|장치에서 사용되지 않은 저장소 공간(기가바이트)입니다.|Windows, iOS|
|IMEI|장치의 IMEI(International Mobile Equipment Identity)입니다.|Windows, iOS, Android|
|MEID|장치의 MEID(Mobile Equipment Identifier)입니다.|Windows, iOS, Android|
|제조업체|장치의 제조업체입니다.|Windows, iOS, Android|
|모델|장치의 모델입니다.|Windows, iOS, Android|
|전화 번호|장치에 할당된 전화 번호입니다.|Windows, iOS, Android|
|구독자의 통신사|장치의 무선 통신사입니다.|Windows, iOS, Android|
|셀룰러 기술|장치에서 사용하는 라디오 시스템입니다.|Windows, iOS, Android|
|Wi-Fi MAC|장치의 미디어 액세스 제어 주소입니다.|Windows, iOS, Android|
|ICCID|집적 회로 카드 식별자, 즉, SIM 카드의 고유한 ID 번호입니다.|Windows, iOS, Android|
|등록된 날짜|Intune에서 장치를 등록한 날짜 및 시간입니다.|Windows, iOS, Android|
|마지막 연결 시간|Intune에 장치를 마지막으로 연결한 날짜 및 시간입니다.|Windows, iOS, Android|
|활성화 잠금 무시 코드|활성화 잠금을 무시할 수 있는 코드입니다.|Windows, iOS, Android|
|Azure AD 등록됨|**예**인 경우 장치가 Azure Active Directory에 등록되어 있습니다.|Windows, iOS, Android|
|준수|장치의 준수 상태입니다.|Windows, iOS, Android|
|EAS 활성화됨|**예**인 경우 장치는 교환 사서함과 동기화됩니다.|Windows, iOS, Android|
|EAS 활성화 ID|장치의 Exchange ActiveSync 식별자입니다.|Windows, iOS, Android|
|감독됨|**예**인 경우 관리자는 장치에 대한 제어를 강화했습니다.|Windows, iOS, Android|
|암호화됨|**예**인 경우 장치에 저장된 데이터가 암호화됩니다.|Windows, iOS, Android|



## <a name="next-steps"></a>다음 단계
Intune을 사용하여 [장치를 관리](device-management.md)하기 위해 수행할 수 있는 작업을 참조하세요.
