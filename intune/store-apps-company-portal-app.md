---
title: Windows 10 회사 포털 앱 수동으로 추가
titleSuffix: Microsoft Intune
description: Windows 10 회사 포털 앱을 수동으로 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 109ba2ddeca3af3f1dbb9834e206330f6146b819
ms.sourcegitcommit: 445a54dc6826a549d770a9953549ae2191d391c2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45727563"
---
# <a name="manually-add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>Microsoft Intune을 사용하여 Windows 10 회사 포털 앱 수동으로 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

장치를 관리하고 앱을 설치하려는 사용자는 Microsoft Store에서 직접 회사 포털 앱을 설치하면 됩니다. 그러나 비즈니스 요구 사항에 따라 회사 포털 앱을 할당해야 하는 경우에는 Intune에서 바로 Windows 10 회사 포털 앱을 수동으로 할당할 수 있습니다. Intune을 Microsoft Store for Business와 통합하지 않은 경우 통합할 수 있습니다.

 > [!NOTE]
 > 이 문서에서 설명하는 옵션은 앱 업데이트가 발표될 때마다 수동 업데이트를 할당해야 합니다.

## <a name="configure-settings-to-show-offline-apps"></a>오프라인 앱을 표시하도록 설정 구성
1. 관리자 계정을 사용하여 [비즈니스용 Microsoft 스토어](https://www.microsoft.com/business-store)에 로그인합니다.
2. 창 위쪽 부근에 있는 **관리** 탭을 선택합니다.
3. 왼쪽 창에서 **설정**을 선택합니다.
4. **쇼핑 경험**에서 **오프라인 앱 표시**를 **켬**으로 설정합니다.  
    오프라인 사용이 허가된 앱이 표시됩니다.

## <a name="download-the-offline-company-portal-app"></a>오프라인 회사 포털 앱 다운로드
1. **회사 포털** 앱을 검색하고 선택합니다.
2. **라이선스 유형**을 **오프라인**으로 설정합니다.
3. **앱 가져오기**를 선택하여 오프라인 회사 포털 앱을 가져와 인벤토리에 추가합니다.
4. **회사 포털** 앱 페이지에서 **관리**를 선택합니다.
5. **플랫폼**으로 **Windows 10 모든 장치**를 선택한 다음, 적절한 **최소 버전**, **아키텍처** 및 **앱 메타데이터 다운로드** 값을 선택합니다. 
6. **다운로드**를 선택하여 로컬 컴퓨터에 파일을 저장합니다.

    ![다운로드를 선택한 "Windows 10 모든 장치" 및 아키텍처 X86 패키지 세부 정보](./media/Win10CP-all-devices.png)

7. **다운로드**를 선택하여 "필요한 프레임워크" 아래의 모든 패키지를 다운로드합니다.  
    이 작업은 x86, x64, ARM 아키텍처에 대해 수행해야 하므로 총 12개의 패키지가 됩니다.
8. 회사 포털 앱을 Intune에 업로드하기 전에 패키지를 포함하는 폴더(예: C:\Company Portal)를 다음과 같은 방법으로 만듭니다.
   - C:\Company Portal에 회사 포털 패키지를 배치합니다. 이 위치에 *Dependencies* 하위 폴더도 만듭니다.  

     ![APPXBUN 파일과 함께 저장된 Dependencies 폴더](./media/Win10CP-Dependencies-save.png)

   - *Dependencies* 폴더에 종속성 패키지를 배치합니다. 

     > [!NOTE]
     > 종속성이 올바른 형식으로 배치되지 않으면 Intune이 패키지 업로드 중에 파일을 인식하고 업로드할 수 없고, 결과적으로 업로드가 실패하고 오류가 표시됩니다.

9. Azure Portal의 Microsoft Intune에서 회사 포털 앱을 새 앱으로 업로드합니다. 
10. 선택한 대상 사용자 집합에 회사 포털 앱을 필수 앱으로 할당합니다.  

Intune이 유니버설 앱의 종속성을 처리하는 방식에 대한 자세한 내용은 [Microsoft Intune MDM을 통해 종속성이 포함된 appxbundle 배포](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)를 참조하세요.  

## <a name="frequently-asked-questions"></a>질문과 대답 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>사용자가 이미 스토어에서 이전 앱을 설치한 경우 어떻게 사용자의 장치에서 회사 포털 앱을 업데이트하나요?
사용자가 이미 Microsoft Store에서 Windows 8.1 또는 Windows Phone 8.1 회사 포털 앱을 설치한 경우 관리자나 사용자의 별도 조치가 없어도 앱이 자동으로 최신 버전으로 업데이트됩니다. 앱이 업데이트되지 않는 경우 사용자에게 장치에서 스토어 앱에 자동 업데이트를 사용하도록 설정했는지 확인해 보라고 요청합니다.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>사이드로드한 Windows 8.1 회사 포털 앱을 Windows 10 회사 포털 앱으로 어떻게 업그레이드하나요?
권장되는 마이그레이션 경로는 할당 작업을 **제거**로 설정하여 Windows 8.1 회사 포털 앱의 할당을 삭제하는 것입니다. 이 설정을 선택한 후에는 이전에 설명한 옵션 중 하나를 사용하여 Windows 10 회사 포털 앱을 할당할 수 있습니다.  

앱을 사이드로드해야 하며 Symantec 인증서로 서명하지 않고 Windows 8.1 회사 포털을 할당한 경우에는 이 문서의 이전 섹션에 설명된 단계를 완료하여 업그레이드를 완료합니다.

앱을 사이드로드해야 하고 Symantec 코드 서명 인증서로 Windows 8.1 회사 포털 앱을 서명하고 할당한 경우 다음 섹션의 단계를 수행합니다.

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>서명 및 사이드로드된 Windows Phone 8.1 회사 포털 앱이나 Windows 8.1 회사 포털 앱을 어떻게 Windows 10 회사 포털 앱으로 업그레이드하나요?
권장되는 마이그레이션 경로는 할당 작업을 **제거**로 설정하여 Windows Phone 8.1 회사 포털 앱 또는 Windows 8.1 회사 포털 앱의 기존 할당을 삭제하는 것입니다. 이 설정을 선택하면 Windows 10 회사 포털 앱을 정상적으로 할당할 수 있습니다.  

선택하지 않으면 업그레이드 경로를 준수하도록 Windows 10 회사 포털 앱을 적절하게 업데이트하고 서명해야 합니다.  

이 방법으로 Windows 10 회사 포털 앱을 서명하고 할당할 경우 스토어에서 사용할 수 있는 새 앱 업데이트마다 이 프로세스를 반복해야 합니다. 앱은 스토어가 업데이트될 때 자동으로 업데이트되지 않습니다.  

이러한 방식으로 앱을 서명하고 할당하는 방법은 다음과 같습니다.

1. [Microsoft Intune Windows 10 회사 포털 앱 서명 스크립트](https://aka.ms/win10cpscript)를 다운로드합니다.  
    이 스크립트가 작동하려면 호스트 컴퓨터에 Windows 10용 Windows SDK가 설치되어야 있어야 합니다. [Windows 10용 Windows SDK를 다운로드합니다](https://go.microsoft.com/fwlink/?LinkId=619296).
2. 앞에서 설명한 대로 비즈니스용 Microsoft 스토어에서 Windows 10 회사 포털 앱을 다운로드합니다.  
3. Windows 10 회사 포털 앱을 서명하려면 다음 표와 같이 스크립트 헤더에 설명된 입력 매개 변수를 사용하여 스크립트를 실행합니다.  
    종속성은 스크립트에 전달할 필요가 없습니다. 앱을 Intune 관리 콘솔에 업로드할 때만 필요합니다.

| 매개 변수 |  설명  |
|---|---|
| InputWin10AppxBundle  |  원본 appxbundle 파일의 경로입니다. |
| OutputWin10AppxBundle | 서명된 appxbundle 파일의 출력 경로입니다. 
| Win81Appx  | Windows 8.1 또는 Windows Phone 8.1 회사 포털(.APPX) 파일의 경로입니다. |
| PfxFilePath  |  Symantec Enterprise 모바일 코드 서명 인증서(.PFX) 파일의 경로입니다.  |
| PfxPassword  | Symantec Enterprise 모바일 코드 서명 인증서의 암호입니다. |
| PublisherId | 엔터프라이즈의 게시자 ID입니다. 이 ID가 없는 경우 Symantec Enterprise 모바일 코드 서명 인증서의 제목 필드를 사용합니다. |
| SdkPath | Windows 10용 Windows SDK의 루트 폴더에 대한 경로입니다. 이 인수는 선택 사항이며 기본적으로 ${env:ProgramFiles(x86)}\Windows Kits\10입니다.  |

스크립트는 실행을 마치면 서명된 버전의 Windows 10 회사 포털 앱을 출력합니다. 그러면 서명된 버전의 앱을 Intune을 통해 LOB 앱으로 할당할 수 있으며, 현재 할당된 버전이 이 새 앱으로 업그레이드됩니다.  

## <a name="next-steps"></a>다음 단계

- [그룹에 앱 할당](apps-deploy.md)

