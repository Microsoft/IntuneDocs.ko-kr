---
title: WIP(Windows Information Protection) 앱 보호 정책 만들기 및 배포
titlesuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 WIP(Windows Information Protection) 앱 보호 정책 만들기 및 배포
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 425dce514d9cf0288a5e84ef5fa89790e6cee8be
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347310"
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Intune을 사용하여 WIP(Windows Information Protection) 앱 보호 정책 만들기 및 배포

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

장치 등록 없이 Windows 10 앱에서 앱 보호 정책을 사용하여 앱을 보호할 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

WIP 정책을 추가할 때 몇 가지 개념에 대해 이해해야 합니다.

### <a name="list-of-allowed-and-exempt-apps"></a>허용되는 앱과 예외 앱 목록

-   **보호되는 앱**: 이 정책을 준수해야 하는 앱입니다.

-   **예외 앱**: 이 정책에서 예외로 설정되며 제한 없이 회사 데이터에 액세스할 수 있는 앱입니다.

### <a name="types-of-apps"></a>앱의 유형

-   **권장 앱:** 사용자가 정책으로 쉽게 가져올 수 있도록 미리 채워진 앱(보통 Microsoft Office) 목록입니다.
-   **스토어 앱:** Windows 스토어의 모든 앱을 정책에 추가할 수 있습니다.
-   **Windows 데스크톱 앱:** 기존 Windows 데스크톱 앱을 정책에 추가할 수 있습니다(예: .exe, .dll).

## <a name="prerequisites"></a>전제 조건

WIP 앱 보호 정책을 만들려면 먼저 MAM 공급자를 구성해야 합니다. [Intune을 사용하여 MAM 공급자를 구성하는 방법](app-protection-policies-configure-windows-10.md)에 대해 자세히 알아보세요.

다음과 같은 라이센스와 업데이트도 필요합니다.

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 라이선스
-   [Windows 크리에이터 업데이트](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP에서는 여러 ID를 사용할 수 없으며 한 번에 하나의 관리 ID만 사용할 수 있습니다.

## <a name="to-add-a-wip-app-protection-policy"></a>WIP 앱 보호 정책을 추가하려면

조직에 Intune을 설치한 후에 WIP 관련 정책을 만들 수 있습니다.

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다.
3. **Microsoft Intune** 블레이드에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 블레이드에서 **앱 보호 정책**을 선택합니다.
5. **정책 추가**를 선택하여 **정책 추가** 블레이드를 표시합니다.
6. 다음 값을 추가합니다.
    - **이름:** 새 정책의 이름(필수)을 입력합니다.
    - **설명:** (선택 사항)설명을 입력합니다.
    - **플랫폼:** 앱 보호 정책에 지원되는 플랫폼으로 **Windows 10**을 선택합니다.
    - **등록 상태:** 정책의 등록 상태로 **등록 없음**을 선택합니다.
7.  **만들기**를 선택합니다. 정책이 만들어져 **앱 보호 정책** 블레이드의 표에 표시됩니다.

## <a name="to-add-recommended-apps-to-your-protected-apps-list"></a>보호되는 앱 목록에 권장 앱을 추가하려면

1. **Microsoft Intune** 블레이드에서 **클라이언트 앱**을 선택합니다.
2. **클라이언트 앱** 블레이드에서 **앱 보호 정책**을 선택합니다.
3. **앱 보호 정책** 블레이드에서 수정하려는 정책을 선택합니다. **Intune 앱 보호** 블레이드가 표시됩니다.
4. **Intune 앱 보호** 블레이드에서 **보호되는 앱**을 선택합니다. **보호되는 앱** 블레이드가 열리고 이 앱 보호 정책의 목록에 이미 포함된 모든 앱이 표시됩니다.
5. **앱 추가**를 선택합니다. **앱 추가** 정보는 앱의 필터링된 목록을 표시합니다. 블레이드 맨 위쪽에 있는 목록을 사용하면 목록 필터를 변경할 수 있습니다.
6. 회사 데이터에 액세스하려는 각 앱을 선택합니다.
7. **확인**을 클릭합니다. **보호되는 앱** 블레이드가 업데이트되어 선택한 모든 앱이 표시됩니다.
8. **Save**을 클릭합니다.

## <a name="add-a-store-app-to-your-protected-apps-list"></a>보호되는 앱 목록에 스토어 앱 추가

**스토어 앱을 추가하려면**
1. **Microsoft Intune** 블레이드에서 **클라이언트 앱**을 선택합니다.
2. **클라이언트 앱** 블레이드에서 **앱 보호 정책**을 선택합니다.
3. **앱 보호 정책** 블레이드에서 수정하려는 정책을 선택합니다. **Intune 앱 보호** 블레이드가 표시됩니다.
4. **Intune 앱 보호** 블레이드에서 **보호되는 앱**을 선택합니다. **보호되는 앱** 블레이드가 열리고 이 앱 보호 정책의 목록에 이미 포함된 모든 앱이 표시됩니다.
5. **앱 추가**를 선택합니다. **앱 추가** 정보는 앱의 필터링된 목록을 표시합니다. 블레이드 맨 위쪽에 있는 목록을 사용하면 목록 필터를 변경할 수 있습니다.
6. 목록에서 **앱 저장**을 선택합니다.
7. **이름**, **게시자**, **제품 이름** 및 **작업**에 대한 값을 입력합니다. 앱이 회사 데이터에 액세스할 수 있도록 **작업** 값을 **허용**으로 설정해야 합니다.
9. **확인**을 클릭합니다. **보호되는 앱** 블레이드가 업데이트되어 선택한 모든 앱이 표시됩니다.
10. **Save**을 클릭합니다.

## <a name="add-a-desktop-app-to-your-protected-apps-list"></a>보호되는 앱 목록에 데스크톱 앱 추가

**데스크톱 앱을 추가하려면**
1. **Microsoft Intune** 블레이드에서 **클라이언트 앱**을 선택합니다.
2. **클라이언트 앱** 블레이드에서 **앱 보호 정책**을 선택합니다.
3. **앱 보호 정책** 블레이드에서 수정하려는 정책을 선택합니다. **Intune 앱 보호** 블레이드가 표시됩니다.
4. **Intune 앱 보호** 블레이드에서 **보호되는 앱**을 선택합니다. **보호되는 앱** 블레이드가 열리고 이 앱 보호 정책의 목록에 이미 포함된 모든 앱이 표시됩니다.
5. **앱 추가**를 선택합니다. **앱 추가** 정보는 앱의 필터링된 목록을 표시합니다. 블레이드 맨 위쪽에 있는 목록을 사용하면 목록 필터를 변경할 수 있습니다.
6. 목록에서 **데스크톱 앱**을 선택합니다.
7. **이름**, **게시자**, **제품 이름**, **파일**, **최소 버전**, **최대 버전** 및 **작업**에 대한 값을 입력합니다. 앱이 회사 데이터에 액세스할 수 있도록 **작업** 값을 **허용**으로 설정해야 합니다.
9. **확인**을 클릭합니다. **보호되는 앱** 블레이드가 업데이트되어 선택한 모든 앱이 표시됩니다.
10. **Save**을 클릭합니다.

## <a name="wip-learning"></a>WIP 학습
WIP를 통해 보호하려는 앱을 추가한 후에는 **WIP 학습**을 사용하여 보호 모드를 적용해야 합니다.

### <a name="before-you-begin"></a>시작하기 전에

WIP 학습은 WIP 지원 앱 및 WIP 알 수 없는 앱을 모니터하는 데 사용할 수 있는 보고서입니다. 알 수 없는 앱은 조직의 IT 부서에서 배포하지 않은 앱입니다. “차단” 모드에서 WIP를 적용하기 전에 생산성 저하를 방지하기 위해 보고서에서 이러한 앱을 내보내 WIP 정책에 추가할 수 있습니다.

<!-- 1631908 --> WIP 지원 앱에 대한 정보뿐 아니라 웹 사이트와 작업 데이터를 공유한 장치 요약도 볼 수 있습니다. 이 정보를 사용하여 그룹 및 사용자 WIP 정책에 추가할 웹 사이트를 확인할 수 있습니다. 요약은 WIP 지원 앱에서 액세스할 수 있는 웹 사이트 URL을 보여줍니다.

WIP 지원 앱 및 WIP 알 수 없는 앱으로 작업하는 경우, 보호되는 앱 목록에 올바른 앱이 있는지 소그룹으로 확인하면서 **자동** 또는 **재정의 허용**으로 시작하는 것이 좋습니다. 이 확인이 완료되면 최종 적용 정책인 **차단**으로 변경할 수 있습니다.

### <a name="what-are-the-protection-modes"></a>보호 모드의 종류

#### <a name="block"></a>차단
WIP가 부적절한 데이터 공유 사례를 찾아 사용자의 작업 완료를 중지시킵니다. 부적절한 데이터 공유 사례에는 회사에서 보호하지 않는 앱 간에 정보를 공유하는 행위, 조직 외부의 타인과 장치 간에 회사 데이터를 공유하는 행위 등이 포함될 수 있습니다.

#### <a name="allow-overrides"></a>재정의 허용
WIP가 부적절한 데이터 공유를 찾은 다음, 사용자가 안전하지 않을 수 있는 작업을 수행할 때 경고를 표시합니다. 그러나 이 모드에서는 사용자가 정책을 재정의하고 데이터를 공유할 수 있습니다. 그러면 해당 작업이 감사 로그에 로깅됩니다.

#### <a name="silent"></a>자동
재정의 허용 모드에서 직원 상호 작용을 묻는 메시지를 차단하지 않고도 WIP가 자동으로 실행되어 부적절한 데이터 공유를 로깅합니다. 그러나 네트워크 리소스 또는 WIP로 보호되는 데이터에 대한 앱의 부적절한 액세스 시도와 같은 허용되지 않는 작업은 계속 중지됩니다.

#### <a name="off-not-recommended"></a>해제(권장되지 않음)
WIP가 해제되며 데이터를 보호하거나 감사하지 않습니다.

WIP를 해제하고 나면 로컬로 연결된 드라이브에서 WIP 태그가 지정된 파일의 암호 해독이 시도됩니다. WIP 보호를 다시 설정해도 이전의 암호 해독 및 정책 정보는 자동으로 다시 적용되지 않습니다.

### <a name="add-a-protection-mode"></a>보호 모드 추가

1.  **앱 정책** 블레이드에서 정책의 이름을 선택한 다음, **필수 설정**을 선택합니다.

    ![학습 모드 스크린샷](./media/learning-mode-sc1.png)

1.  설정을 선택한 다음, **저장**을 선택합니다.

### <a name="use-wip-learning"></a>WIP 학습 사용

1. [Azure Portal](https://portal.azure.com)을 엽니다. **모든 서비스**를 선택합니다. 텍스트 상자 필터에 **Intune**을 입력합니다.

3. **Intune** > **클라이언트 앱**을 선택합니다.

4. **앱 보호 상태** > **보고서** > **Windows Information Protection 학습**을 선택합니다.  

    WIP 학습 로깅 보고서에 앱이 표시되면 앱 보호 정책에 해당 앱을 추가할 수 있습니다.

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>Windows Search Indexer가 암호화된 항목을 검색 하게 합니다
항목의 인덱싱을 허용하거나 허용하지 않습니다. WIP(Windows Information Protection)로 보호되는 파일 같이 암호화된 항목을 인덱싱할지 여부를 제어하는 Windows Search Indexer용 스위치입니다.

이 앱 보호 정책은 WIP 정책의 **고급 설정**에 있습니다. 앱 보호 정책은 *Windows 10* 플랫폼에 설정돼야 하며 해당 앱 정책 **등록 상태**는 **등록을 통해** 설정돼야 합니다.

정책을 사용할 때 WIP로 보호되는 항목은 인덱싱되고 이 항목에 대한 메타데이터는 암호화되지 않은 위치에 저장됩니다. 해당 메타데이터는 파일 경로 및 수정된 날짜 같은 것을 포함합니다.

정책을 사용하지 않을 때 WIP로 보호되는 항목은 인덱싱되지 않고 Cortana 또는 파일 탐색기의 결과에도 표시되지 않습니다. 해당 장치에 WIP로 보호되는 미디어 파일이 많은 경우 사진이나 Groove 앱의 성능에 영향을 줄 수도 있습니다.

## <a name="add-encrypted-file-extensions"></a>암호화된 파일 확장명 추가

**Windows Search Indexer가 암호화된 항목 검색하도록 허용** 옵션을 설정할 뿐 아니라 파일 확장명 목록도 지정할 수 있습니다. 네트워크 위치 목록에서 정의된 것처럼 기업 내의 SMB(서버 메시지 블록) 공유에서 복사하는 경우 이러한 확장명의 파일은 암호화됩니다. 이 정책이 지정되지 않은 경우 기존 자동 암호화 동작이 적용됩니다. 이 정책이 구성된 경우 목록에서 확장명을 가진 파일만 암호화됩니다.

## <a name="deploy-your-wip-app-protection-policy"></a>WIP 앱 보호 정책 배포

> [!IMPORTANT]
> 이 정보는 장치 등록 없이 WIP에 적용됩니다.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

WIP 앱 보호 정책을 만든 후에는 MAM을 사용하여 조직에 정책을 배포해야 합니다.

1.  **앱 정책** 블레이드에서 새로 만든 앱 보호 정책을 선택하고 **사용자 그룹** > **사용자 그룹 추가**를 선택합니다.

    **사용자 그룹 추가** 블레이드에서 Azure Active Directory의 모든 보안 그룹이 포함된 사용자 그룹 목록이 열립니다.

2.  정책을 적용할 그룹을 선택하고 **선택**을 선택하여 정책을 배포합니다.

## <a name="next-steps"></a>다음 단계

WIP에 대한 자세한 내용은 [WIP(Windows Information Protection)를 사용하여 엔터프라이즈 데이터 보호](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)를 참조하세요.
