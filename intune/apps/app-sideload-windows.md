---
title: Windows 및 Windows Phone 앱 사이드로드
titleSuffix: Microsoft Intune
description: Intune을 사용하여 LOB(기간 업무) 앱을 배포할 수 있도록 앱에 서명하는 방법을 알아봅니다.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 09/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7500000f8a34120e69c27ce01a6cfdb85f447abe
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414694"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Intune으로 Windows 디바이스에 기간 업무 앱을 배포할 수 있도록 앱에 서명

Intune 관리자는 회사 포털 앱을 비롯한 LOB(기간 업무) 유니버설 앱을 Windows 8.1 Desktop 또는 Windows 10 Desktop 및 Mobile 디바이스에 배포할 수 있습니다. Windows 8.1 Desktop 또는 Windows 10 Desktop 및 Mobile 디바이스에 .appx 앱을 배포하려면 Windows 디바이스에서 이미 신뢰하는 퍼블릭 인증 기관의 코드 서명 인증서를 사용하거나 사용자 고유의 인증 기관을 사용할 수 있습니다.

 > [!NOTE]
 > Windows 8.1 Desktop에는 테스트용 로드를 사용하도록 설정하기 위한 엔터프라이즈 정책이나 테스트용 로드 키(도메인 가입 디바이스에 대해 자동으로 사용 가능)가 필요합니다. 자세한 내용은 [Windows 8 테스트용 로드](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/)를 참조하세요.

## <a name="windows-10-sideloading"></a>Windows 10 테스트용 로드

Windows 10에서 테스트용 로드는 다음과 같은 측면에서 이전 버전의 Windows와는 다릅니다.

- 엔터프라이즈 정책을 사용한 테스트용 로드를 위해 디바이스 잠금을 해제할 수 있습니다. Intune은 "신뢰할 수 있는 앱 설치"라는 디바이스 구성 정책을 제공합니다. appx 앱에 서명하는 데 사용되는 인증서를 이미 신뢰하는 디바이스에서는 이 정책을 <allow>로 설정해야 합니다.

- Symantec Phone 인증서 및 테스트용 로드 라이선스 키는 필요하지 않습니다. 그러나 온-프레미스 인증 기관을 사용할 수 없는 경우에는 퍼블릭 인증 기관에서 코드 서명 인증서를 가져와야 할 수 있습니다. 자세한 내용은 [코드 서명 소개](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing)를 참조하세요.

### <a name="code-sign-your-app"></a>앱에 코드 서명

첫 번째 단계는 appx 패키지에 코드 서명하는 것입니다. 자세한 내용은 [SignTool을 사용하여 앱 패키지에 서명](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool)을 참조하세요.

### <a name="upload-your-app"></a>앱 업로드

그 다음에는 서명된 appx 파일을 업로드해야 합니다. 자세한 내용은 [Microsoft Intune에 Windows 기간 업무 앱 추가](lob-apps-windows.md)를 참조하세요.

필요에 따라 사용자 또는 디바이스에 앱을 배포하는 경우 Inutne 회사 포털 앱이 필요하지 않습니다. 그러나 사용자에게 제공되는 앱을 배포하는 경우에는 퍼블릭 Microsoft Store의 회사 포털 앱을 사용하거나, 비즈니스용 프라이빗 Microsoft Store의 회사 포털 앱을 사용하거나, Intune 회사 포털 앱에 서명하고 수동으로 배포해야 합니다.

### <a name="upload-the-code-signing-certificate"></a>코드 서명 인증서 업로드

Windows 10 디바이스에서 인증 기관을 아직 신뢰하지 않는 경우, appx 패키지에 서명하고 Intune 서비스에 업로드한 후에 다음과 같이 Intune 포털에 코드 서명 인증서를 업로드해야 합니다.

1. 클라이언트 앱 클릭
2. Windows 엔터프라이즈 인증서 클릭
3. 코드 서명 인증서에서 '파일 선택' 선택
4. .cer 파일 선택 및 업로드 클릭

이제 Intune 서비스에서 appx 배포를 사용하는 모든 Windows 10 Desktop 및 Mobile 디바이스는 해당 엔터프라이즈 인증서를 자동으로 다운로드하며 설치 후에 애플리케이션을 시작할 수 있습니다.

Intune은 업로드된 최신 .cer 파일만 배포합니다. 조직과 연결되지 않은 다른 개발자가 여러 appx 파일을 만든 경우 개발자에게 인증서로 설명하기 위한 서명되지 않은 appx 파일을 제공하도록 하거나 조직이 사용하는 코드 서명 인증서를 제공해야 합니다.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Symantec 엔터프라이즈 코드 서명 인증서를 갱신하는 방법

Windows Phone 8.1 모바일 앱을 배포하는 데 사용되는 인증서는 2019년 2월 28일에 중단되었으며 Symantec에서 더 이상 갱신될 수 없습니다. WIndows 10 모바일에 배포하는 경우 [Windows 10 테스트용 로드](app-sideload-windows.md#windows-10-sideloading) 지침에 따라 Symantec Desktop Enterprise 코드 서명 인증서를 계속 사용할 수 있습니다.

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>LOB(기간 업무) 앱에 업데이트된 인증서를 설치하는 방법

Windows Phone 8.1

기존 Symantec Mobile Enterprise 코드 서명 인증서가 만료되면 Intune 서비스는 이 플랫폼용 LOB 앱을 더 이상 배포할 수 없습니다. SD 카드를 사용하거나 디바이스에 파일을 다운로드하여 서명되지 않은 XAP/APPX 파일을 테스트용으로 로드하는 것도 가능합니다. 자세한 내용은 [Windows Phone에 XAP 파일을 설치하는 방법](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280)을 참조하세요.

Windows 8.1 Desktop/Windows 10 Desktop 및 Mobile

인증서 기간이 만료된 경우 appx 파일이 더 이상 시작되지 않을 수 있습니다. 새 .cer 파일을 얻고 지침에 따라 배포된 각 appx 파일을 코드 서명하고 모든 appx 파일 및 업데이트된 .cer 파일을 Intune 포털의 Windows 엔터프라이즈 인증서 섹션에 다시 업로드해야 합니다.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Windows 10 회사 포털 앱 수동 배포

Microsoft Store에 대한 액세스 권한을 제공하지 않으려는 경우 MSFB(비즈니스용 Microsoft Store)와 Intune을 통합하지 않았더라도 Intune에서 곧바로 Windows 10 회사 포털 앱을 수동으로 배포할 수 있습니다. 또는 통합한 경우에는 [MSFB를 사용하여 앱 배포](store-apps-windows.md)를 사용하여 회사 포털 앱을 배포할 수 있습니다.

 > [!NOTE]
 > 이 옵션을 사용하려면 앱 업데이트가 릴리스될 때마다 수동 업데이트를 배포해야 합니다.

1. 자신의 계정으로 [비즈니스용 Microsoft 스토어](https://www.microsoft.com/business-store)에 로그인하고 **오프라인 라이선스** 버전의 회사 포털 앱을 가져옵니다.  
2. 앱을 가져왔으면 **인벤토리** 페이지에서 앱을 선택합니다.  
3. **플랫폼**으로 **Windows 10 all devices**(Windows 10 모든 디바이스)를 선택한 다음 적절한 **아키텍처**를 선택하고 다운로드합니다. 이 앱에는 앱 라이선스 파일이 필요 없습니다.
   ![다운로드용 Windows 10 X86 패키지 세부 정보를 표시하는 이미지](./media/app-sideload-windows/Win10CP-all-devices.png)
4. "Required Frameworks"(필요한 프레임워크)에 나온 모든 패키지를 다운로드합니다. x86, x64 및 ARM 아키텍처에 대해 수행해야 하므로 아래와 같이 총 9개의 패키지가 됩니다.

   ![다운로드할 종속성 파일의 이미지 ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. 회사 포털 앱을 Intune에 업로드하기 전에 패키지를 포함하는 폴더(예: C:&#92;Company Portal)를 다음과 같은 방법으로 만듭니다.
   1. C:\Company Portal에 회사 포털 패키지를 배치합니다. 이 위치에 Dependencies 하위 폴더도 만듭니다.  
      ![APPXBUN 파일과 함께 저장된 Dependencies 폴더의 이미지](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Dependencies 폴더에 9개의 종속성 패키지를 배치합니다.  
      종속성을 이 형식으로 배치하지 않는 경우 Intune은 패키지 업로드 도중에 패키지를 인식 및 업로드할 수 없습니다. 이에 따라 업로드에 실패하고 다음과 같은 오류가 표시됩니다.  
      ![오류 메시지 - Windows 앱 종속성을 제공해야 합니다.](./media/app-sideload-windows/Win10CP-error-message.png)
6. Intune으로 돌아간 후 회사 포털 앱을 새 앱으로 업로드합니다. 원하는 대상 사용자 집합에게 필수 앱으로 배포합니다.  

Intune에서 유니버설 앱의 종속성을 처리하는 방식에 대한 자세한 내용은 [Deploying an appxbundle with dependencies via Microsoft Intune MDM(Microsoft Intune MDM을 통해 종속성이 포함된 appxbundle 배포)](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)을 참조하세요.  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>사용자가 이미 스토어에서 이전 앱을 설치한 경우 어떻게 사용자의 디바이스에서 회사 포털을 업데이트하나요?

사용자가 이미 스토어에서 Windows 8.1 또는 Windows Phone 8.1 회사 포털 앱을 설치한 경우 관리자나 사용자의 별도 조치가 필요 없이 앱이 자동으로 새 버전으로 업데이트됩니다. 업데이트가 이루어지지 않는 경우 사용자에게 디바이스에서 스토어 앱에 대해 자동 업데이트를 활성화했는지 확인하도록 요청합니다.

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>사이드로드한 Windows 8.1 회사 포털 앱을 Windows 10 회사 포털 앱으로 어떻게 업그레이드하나요?

권장되는 마이그레이션 경로는 배포 작업을 "제거"로 설정하여 Windows 8.1 회사 포털 앱의 배포를 삭제하는 것입니다. 이 작업이 완료되면 위의 옵션 중 하나를 사용하여 Windows 10 회사 포털 앱을 배포할 수 있습니다.  

앱을 사이드로드해야 하며 Symantec 인증서로 서명하지 않고 Windows 8.1 회사 포털을 배포한 경우에는 위의 Intune 섹션을 통해 직접 배포의 단계를 따라 업그레이드를 완료합니다.

앱을 사이드로드해야 하며 Symantec 코드 서명 인증서로 Windows 8.1 회사 포털을 서명 및 배포한 경우에는 아래 섹션의 단계를 따릅니다.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>서명 및 사이드로드된 Windows Phone 8.1 회사 포털 앱이나 Windows 8.1 회사 포털 앱을 어떻게 Windows 10 회사 포털 앱으로 업그레이드하나요?

권장되는 마이그레이션 경로는 배포 작업을 "제거"로 설정하여 Windows Phone 8.1 회사 포털 앱 또는 Windows 8.1 회사 포털 앱의 기존 배포를 삭제하는 것입니다. 이 작업이 완료되면 Windows 10 회사 포털 앱을 정상적으로 배포할 수 있습니다.  

이 작업을 마치지 않는 경우에는 업그레이드 경로를 준수하도록 Windows 10 회사 포털 앱을 적절하게 업데이트하고 서명해야 합니다.  

이 방법으로 Windows 10 회사 포털 앱이 서명 및 배포된 경우에는 스토어에서 사용할 수 있는 새 앱 업데이트 각각에 대해 이 프로세스를 반복해야 합니다. 앱은 스토어가 업데이트될 때 자동으로 업데이트되지 않습니다.  

이러한 방식으로 앱을 서명하고 배포하는 방법은 다음과 같습니다.

1. [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript)에서 Microsoft Intune Windows 10 회사 포털 앱 서명 스크립트를 다운로드합니다.  이 스크립트가 작동하려면 호스트 컴퓨터에 Windows 10용 Windows SDK가 설치되어야 있어야 합니다. Windows 10용 Windows SDK를 다운로드하려면 [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296)을 방문해 보세요.
2. 위에서 설명한 대로 비즈니스용 Microsoft 스토어에서 Windows 10 회사 포털 앱을 다운로드합니다.  
3. Windows 10 회사 포털 앱을 서명하려면 스크립트 헤더에 입력 매개 변수를 자세히 지정하여 스크립트를 실행합니다(아래에 추출됨). 종속성은 스크립트에 전달할 필요가 없습니다. 앱을 Intune 관리 콘솔에 업로드할 때만 필요합니다.

|       매개 변수       |                                                                    설명                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             원본 appxbundle 파일이 위치한 경로입니다.                                              |
| OutputWin10AppxBundle |                                                  서명된 appxbundle 파일의 출력 경로입니다.                                                  |
|       Win81Appx       |                          Windows 8.1 또는 Windows Phone 8.1 회사 포털(.APPX) 파일이 위치한 경로입니다.                           |
|      PfxFilePath      |                                   Symantec Enterprise 모바일 코드 서명 인증서(.PFX) 파일의 경로입니다.                                    |
|      PfxPassword      |                                     Symantec Enterprise 모바일 코드 서명 인증서의 암호입니다.                                      |
|      PublisherId      |      엔터프라이즈의 게시자 ID입니다. 없는 경우 Symantec Enterprise 모바일 코드 서명 인증서의 '제목' 필드를 사용합니다.       |
|        SdkPath        | Windows 10용 Windows SDK의 루트 폴더에 대한 경로입니다. 이 인수는 선택 사항이며 기본적으로 ${env:ProgramFiles(x86)}\Windows Kits\10입니다. |

실행이 완료되면 스크립트는 서명된 버전의 Windows 10 회사 포털 앱을 출력합니다. 그러면 서명된 버전의 앱을 Intune 통해 LOB 앱으로 배포할 수 있으며, 현재 배포된 버전이 이 새 앱으로 업그레이드됩니다.  
