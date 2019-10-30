---
title: 단계별 시나리오 - 보안 Microsoft Office 모바일 앱
titleSuffix: Microsoft Intune
description: Microsoft 365 장치 관리 포털에서 보안 Microsoft Office 모바일 앱을 배포하는 단계별 시나리오에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd02e2b7f9582308109d1e6986d7e6a8014e5af7
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585711"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>단계별 시나리오 - 보안 Microsoft Office 모바일 앱 

장치 관리 포털에서 이 단계별 시나리오에 따라 iOS 및 Android 디바이스에서 기본 Intune 앱 보호를 사용하도록 설정할 수 있습니다.

사용하도록 설정한 앱 보호는 다음 작업을 적용합니다. 
- 작업 파일을 암호화합니다.
- 작업 파일에 액세스하는 데 PIN이 필요합니다.
- 시도가 5번 실패한 후 PIN을 다시 설정해야 합니다.
- 작업 파일이 iTunes, iCloud 또는 Android 백업 서비스에서 백업되지 않도록 합니다.  
- 작업 파일이 OneDrive 또는 SharePoint에만 저장되도록 합니다.
- 보호된 앱이 탈옥 또는 루팅된 디바이스에 작업 파일을 로드하지 못하도록 합니다.
- 디바이스가 720분 동안 오프라인 상태인 경우 작업 파일에 대한 액세스를 차단합니다.
- 디바이스가 90일 동안 오프라인 상태인 경우 작업 파일을 제거합니다. 

## <a name="background"></a>배경

Office 모바일 앱 및 모바일용 Microsoft Edge는 이중 ID를 지원합니다. 이중 ID를 사용하면 앱에서 개인 파일과 별도로 작업 파일을 관리할 수 있습니다. 

![회사 데이터 및 개인 데이터의 이미지](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

[Intune 앱 보호 정책](~/apps/app-protection-policy.md)을 사용하면 Intune에 등록된 디바이스에서 작업 파일을 보호하는 데 도움이 됩니다. Intune에서 관리를 위해 등록되지 않은 직원 소유 디바이스에서 앱 보호 정책을 사용할 수도 있습니다. 이 경우 회사에서 디바이스를 관리하지 않더라도 여전히 작업 파일과 리소스가 보호되고 있음을 확인해야 합니다.

앱 보호 정책을 사용하여 사용자가 보호되지 않는 위치에 작업 파일을 저장하지 못하도록 할 수 있습니다. 앱 보호 정책으로 보호되지 않는 다른 앱으로 데이터 이동을 제한할 수도 있습니다. 앱 보호 정책 설정은 다음과 같습니다.
- 다른 이름으로 저장 차단 및 잘라내기, 복사 및 붙여넣기 제한과 같은 데이터 재배치 정책
- 단순한 액세스용 PIN을 요구하고 관리형 앱이 탈옥 또는 루팅된 디바이스에서 실행되는 것을 차단하는 액세스 정책 설정

앱 기반 조건부 액세스 및 클라이언트 앱 관리는 Intune 앱 보호 정책을 지원하는 클라이언트 앱만 Exchange Online 및 기타 Office 365 서비스에 액세스할 수 있도록 함으로써 보안 계층을 추가합니다.

Microsoft Outlook 앱만 Exchange Online에 액세스할 수 있도록 하려는 경우 iOS 및 Android에서 기본 제공 메일 앱을 차단할 수 있습니다. 또한 Intune 앱 보호 정책이 적용되지 않은 앱은 SharePoint Online에 액세스하지 못하도록 차단할 수 있습니다.

이 예에서는 관리자가 앱 보호 정책을 Outlook 앱에 적용한 다음, 회사 전자 메일에 액세스할 때 사용할 수 있는 승인된 앱 목록에 Outlook 앱을 추가하는 조건부 액세스 규칙을 적용합니다.

![Outlook 앱 조건부 액세스 프로세스 흐름](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>전제 조건

다음 Intune 관리자 권한이 필요합니다.

   - 관리형 앱 읽기, 만들기, 삭제 및 할당 권한
   - 정책 세트 읽기, 만들기 및 할당 권한
   - 조직 읽기 권한

## <a name="step-1---introduction"></a>1단계 - 소개

**Intune 앱 보호** 단계별 시나리오에 따라 데이터가 조직 외부에서 공유되거나 누출되지 않도록 합니다. 

할당된 iOS 및 Android 사용자는 Office 앱을 열 때마다 PIN을 입력해야 합니다. 시도가 5번 실패한 후 사용자는 PIN을 다시 설정해야 합니다. 이미 디바이스 PIN을 요구한 경우 사용자는 영향을 받지 않습니다.

### <a name="what-you-will-need-to-continue"></a>계속해야 하는 작업

사용자에게 필요한 앱과 해당 앱에 액세스하는 데 필요한 항목에 대해 질문합니다. 다음과 같은 정보를 준비해야 합니다.
- 회사용으로 승인된 Office 앱 목록
- 비관리형 디바이스에서 승인된 앱을 시작하기 위한 PIN 요구 사항

## <a name="step-2---basics"></a>2단계 - 기본 사항

이 단계에서는 새 앱 보호 정책에 대한 **접두사** 및 **설명**을 입력해야 합니다. **접두사**를 추가하면 단계별 시나리오에서 만드는 리소스에 관련된 세부 정보가 업데이트됩니다. 할당 및 구성을 변경해야 하는 경우 나중에 이 세부 정보를 통해 정책을 쉽게 찾을 수 있습니다. 

> [!TIP]
> 나중에 참조할 수 있도록 생성될 리소스를 적어 두는 것이 좋습니다.

## <a name="step-3---apps"></a>3단계 - 앱

시작하는 데 도움이 되도록 이 단계별 시나리오에는 iOS 및 Android 디바이스를 보호하기 위해 다음 모바일 앱이 미리 선택되어 있습니다.
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

또한 이 단계별 시나리오에서는 이 앱이 Microsoft Edge에서 웹 링크를 열도록 구성하여 작업 사이트가 보호된 브라우저에서 열리도록 보장합니다.

보호하려는 정책 관리 앱의 목록을 수정합니다. 이 목록에서 앱을 추가 또는 제거합니다. 

앱을 선택한 경우 **다음**을 클릭합니다.

## <a name="step-4---configuration"></a>4단계 - 구성

이 단계에서는 이 앱에서 회사 파일과 메일에 액세스하고 이를 공유하기 위한 요구 사항을 구성해야 합니다. 기본적으로 사용자는 조직의 OneDrive 및 SharePoint 계정에 데이터를 저장할 수 있습니다.

| Setting | 설명 | 기본값 |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| PIN 형식 | 숫자 PIN은 모두 숫자로 구성됩니다. 암호는 영숫자 및 특수 문자로 구성됩니다.  iOS/iPadOS에서 “암호” 형식을 구성하려면 앱에 Intune SDK 버전 7.1.12 이상이 설치되어야 합니다. 숫자 형식에는 Intune SDK 버전 제한이 없습니다. | 숫자 |
| 최소 PIN 길이 선택 | PIN 시퀀스의 최소 자릿수를 지정합니다. | 6 |
| 비활성인 시간(분)이 지난 후에 액세스 요구 사항 다시 확인 | 정책 관리 앱이 지정된 비활성 시간(분)보다 더 오랫동안 비활성 상태이면 앱에서 앱이 시작된 후 액세스 요구 사항(PIN, 조건부 시작 설정)을 다시 확인하도록 요청합니다. | 30 |
| 조직 데이터 인쇄 | 차단된 경우 앱에서 보호된 데이터를 인쇄할 수 없습니다. | 차단 |
| 관리되지 않는 브라우저에서 정책 관리 앱 링크 열기 | 차단된 경우 정책 관리 앱 링크를 관리형 브라우저에서 열어야 합니다. | 차단 |
| 관리되지 않는 앱에 데이터 복사 | 차단된 경우 관리되는 데이터는 관리형 앱에 남아 있습니다. | 허용 |

## <a name="step-5---assignments"></a>5단계 - 할당

이 단계에서는 회사 데이터에 액세스할 수 있도록 포함하려는 사용자 그룹을 선택할 수 있습니다. 앱 보호는 디바이스가 아니라 사용자에게 할당되므로 회사 데이터는 사용된 디바이스와 해당 등록 상태에 관계없이 보호됩니다.

할당된 앱 보호 정책 및 조건부 액세스 설정이 없는 사용자는 회사 프로필의 데이터를 모바일 디바이스의 개인 앱 및 관리되지 않는 로컬 스토리지에 저장할 수 있습니다. 또한 개인 앱을 통해 Microsoft Exchange와 같은 회사 데이터 서비스에 연결할 수 있습니다.

## <a name="step-6---review--create"></a>6단계 - 검토 + 만들기

마지막 단계에서는 구성한 설정의 요약을 검토할 수 있습니다. 선택 항목을 검토한 후에는 **만들기**를 클릭하여 단계별 시나리오를 완료합니다. 단계별 시나리오를 완료한 후에는 리소스 테이블이 표시됩니다. 나중에 이 리소스를 편집할 수 있지만 요약 보기를 종료하면 테이블이 저장되지 않습니다.

> [!IMPORTANT]
> 단계별 시나리오가 완료되면 요약이 표시됩니다. 나중에 요약에 나열된 리소스를 수정할 수 있지만 이 리소스를 표시하는 테이블은 저장되지 않습니다.
## <a name="next-steps"></a>다음 단계

- 클라우드 서비스가 작업 파일을 보호되지 않는 앱으로 보내지 못하도록 사용자를 앱 기반 조건부 액세스 정책에 할당하여 작업 파일의 보안을 강화합니다. 자세한 내용은 [Intune을 사용하는 앱 기반 조건부 액세스 정책 설정](~/protect/app-based-conditional-access-intune-create.md)을 참조하세요.

