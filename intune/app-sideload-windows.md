---
title: Intune용 Windows 및 Windows Phone 앱 사이드로드
description: Intune을 사용하여 LOB(기간 업무) 앱을 배포할 수 있도록 앱에 서명하는 방법을 알아봅니다.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
ms.custom: intune-classic
ms.openlocfilehash: 0c1daa93ff38d1f76ab8c203bf2d989318ecdf62
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425226"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Intune으로 Windows 장치에 기간 업무 앱을 배포할 수 있도록 앱에 서명

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Intune 관리자는 회사 포털 앱을 비롯한 LOB(기간 업무) 앱을 Windows 및 Windows 10 Mobile 장치에 배포할 수 있습니다. Windows 10 및 Windows 10 Mobile 장치에 .appx 또는 .xap 앱을 배포하거나 Windows 8.1 또는 Windows Phone 8.1 장치에 LOB 앱을 배포하려면 **Symantec Enterprise 모바일 코드 서명 인증서**를 얻어야 합니다. 해당 Windows 장치에서 이러한 앱용으로 Symantec 인증서만 신뢰할 수 있습니다. Windows 10 앱 및 "유니버설" 앱에는 사용자 고유의 인증 기관을 사용할 수 있습니다. 이 인증서는 다음을 위해 필요합니다.

-   Windows PC, Windows 10 Mobile 장치 및 Windows Phone 장치에 배포하기 위해 회사 포털 앱에 서명

-   Intune에서 회사 기간 업무 앱을 Windows 장치에 배포할 수 있도록 해당 앱에 서명

아래 단계에 따라 필요한 인증서를 가져오고 앱에 서명할 수 있습니다. Microsoft 개발자로 등록한 다음 Symantec 인증서를 구매해야 합니다.


1. **Microsoft 개발자로 등록**<br>
   회사 계정을 구매하기 위해 로그인할 때 사용한 회사 계정 정보를 이용하여 [Microsoft 개발자로 등록](http://go.microsoft.com/fwlink/?LinkId=268442)합니다. 이 요청의 경우 코드 서명 인증서를 받기 전에 회사 관리자의 승인을 받아야 합니다.

2. **회사 Symantec 인증서 가져오기**<br>
  Symantec ID를 사용하여 [Symantec 웹 사이트](http://go.microsoft.com/fwlink/?LinkId=268441) 에서 인증서를 구입합니다. 인증서를 구매하고 나면 Microsoft 개발자로 등록할 때 지정한 회사 승인자에게 인증서 요청을 승인하라는 전자 메일이 수신됩니다. Symantec 인증서 요구 사항에 대한 자세한 내용은 [Windows Phone에 Symantec 인증서가 필요한 이유는 무엇인가요?](https://technet.microsoft.com/library/dn764959.aspx#BKMK_Symantec)를 참조하세요. Windows 장치 등록 FAQ.

3.  **인증서 가져오기**<br>
    요청이 승인되면 인증서 가져오기에 대한 지침이 포함된 전자 메일을 받습니다. 전자 메일의 지침에 따라 인증서를 가져옵니다.

4.  **가져온 인증서 확인**<br>
    인증서를 제대로 가져왔는지 확인하려면 **인증서** 스냅인으로 이동하여 **인증서**를 마우스 오른쪽 단추로 클릭하고 **인증서 찾기**를 선택합니다. **포함** 필드에 “Symantec”을 입력하고 **지금 찾기**를 클릭합니다. 가져온 인증서가 결과에 표시됩니다.

    ![Symantec 인증서 찾기](./media/wit.gif)

5. **서명 인증서 내보내기**<br>
    인증서가 있는 것을 확인했으면 .pfx 파일을 내보내 회사 포털에 서명할 수 있습니다. **용도** 가 "코드 서명"인 Symantec 인증서를 선택합니다. 코드 서명 인증서를 마우스 오른쪽 단추로 클릭하고 **내보내기**를 선택합니다.

    ![서명 인증서 내보내기](./media/wit-walk-cert2.gif)

    **인증서 내보내기 마법사**페이지에서 **예, 개인 키를 내보냅니다.** 를 클릭하고 **다음**을 클릭합니다. **개인 정보 교환 –PKCS #12(.PFX)** 를 선택하고 **가능하면 인증 경로에 있는 인증서 모두 포함**을 선택합니다. 마법사를 완료합니다. 자세한 내용은 [개인 키와 함께 인증서 내보내기](http://go.microsoft.com/fwlink/?LinkID=203031)를 참조하세요.

6.  **앱을 Intune에 업로드**<br>
    서명한 앱 파일 및 코드 서명 인증서를 업로드하여 최종 사용자가 앱을 사용할 수 있도록 합니다.

    1.  Azure Portal에서 **관리** &gt; **Windows Phone**을 클릭합니다.

    2.  **서명된 앱 파일 업로드**를 클릭하고 Intune 관리자 ID로 로그인합니다.

    3.  내보낸 인증서(.pfx) 파일을 **코드 서명 인증서**에 추가하고 인증서의 암호를 만듭니다.

    4.  마법사를 완료합니다.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>예: Windows 장치용 회사 포털 앱 다운로드, 서명 및 배포

회사 포털 앱을 Windows Phone 스토어에서 설치하지 않고 Intune을 사용해 Windows Phone 및 Windows 10 Mobile 장치를 비롯한 Microsoft 장치에 배포할 수 있습니다. 회사 포털 앱을 다운로드하고 인증서로 서명해야 합니다.  사용자가 회사 저장소를 사용하지 않으며 회사 포털을 Windows Phone 8.1 장치에 배포하려는 경우에만 필요합니다.


1.  **회사 포털 다운로드**

    Intune을 사용하여 회사 포털 앱을 배포하려면 다운로드 센터에서 [Windows Phone 8.1용 Microsoft Intune 회사 포털 앱](http://go.microsoft.com/fwlink/?LinkId=615799)을 다운로드하고 자동으로 압축 해제되는 파일(.exe)을 실행합니다. 이 파일에는 두 개의 파일이 들어 있습니다.

    -   CompanyPortal.appx – Windows Phone 8.1용 회사 포털 설치 앱

    -   WinPhoneCompanyPortal.ps1 – 회사 포털 앱 파일을 Windows Phone 8.1 장치에 배포할 수 있도록 서명하는 데 사용할 수 있는 PowerShell 스크립트

    또는 [비즈니스용 Microsoft 스토어](http://businessstore.microsoft.com/)에서 Windows Phone 8.1 회사 포털(오프라인 사용이 허가된 패키지) 또는 Windows 10 회사 포털(오프라인 사용이 허가된 패키지)을 다운로드할 수 있습니다. 회사 포털 앱과 함께 오프라인 라이선스 및 오프라인에서 사용하기 위해 다운로드한 적절한 패키지를 얻어야 합니다. 선택 영역의 Windows 8 및 Windows Phone 8 플랫폼 목록은 상응하는 8.1 플랫폼을 나타냅니다. Intune을 사용하여 이 작업을 수행하는 방법에 대한 자세한 내용은 [비즈니스용 Microsoft 스토어에서 구입한 앱 관리](windows-store-for-business.md)를 참조하세요.

2.  **Windows Phone SDK 다운로드** Windows Phone SDK 8.0](http://go.microsoft.com/fwlink/?LinkId=615570)을 다운로드하고 이 SDK를 컴퓨터에 설치합니다. 이 SDK는 응용 프로그램 등록 토큰을 생성하는 데 필요합니다.

3.  **AETX 파일 생성** Windows Phone SDK 8.0의 일부인 AETGenerator.exe를 사용하여 Symantec PFX 에서 응용 프로그램 등록 토큰(.aetx) 파일을 생성합니다. AETX 파일을 생성하는 방법에 대한 지침은 [Windows Phone용 응용 프로그램 등록 토큰을 생성하는 방법](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx)을 참조하세요.

4.  **Windows 8.1용 Windows SDK 다운로드** [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=613525)(http://go.microsoft.com/fwlink/?LinkId=613525)를 다운로드하여 설치합니다. 참고로 회사 포털 앱에 포함된 PowerShell 스크립트는 기본 설치 위치 `${env:ProgramFiles(x86)}\Windows Kits\8.1`을 사용합니다. 다른 위치에 설치하는 경우 cmdlet 매개 변수에 해당 위치를 포함해야 합니다.

5.  **PowerShell을 사용하여 앱에 코드 서명** 관리자로 로그인하고 Windows SDK, Symantec Enterprise 모바일 코드 서명 인증서가 설치된 호스트 컴퓨터에서 **Windows PowerShell**을 열어 Sign-WinPhoneCompanyPortal.ps1 파일을 찾아 스크립트를 실행합니다.

    **예 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    이 예에서는 C:\temp\에 있는 CompanyPortal.appx에 서명하고 CompanyPortalEnterpriseSigned.appx를 생성합니다. 이 파일은 PFX 암호 1234를 사용하고 PFX 파일에서 게시자 ID를 읽습니다. 또한 cert.aetx 파일에서 엔터프라이즈 ID도 읽습니다.

    **예 2**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    이 예에서는 C:\temp\에 있는 CompanyPortal.appx에 서명하고 CompanyPortalEnterpriseSigned.appx를 생성합니다. 이 파일은 PFX 암호 1234를 사용하고 지정된 게시자 ID를 사용합니다.

    **매개 변수:**

    -   `-InputAppx` –작은따옴표로 묶은 CompanyPortal.appx 파일에 대한 로컬 경로입니다. 예: 'C:\temp\CompanyPortal.appx'

    -   `-OutputAppx` – 작은따옴표로 묶은 서명된 회사 포털 앱에 대한 로컬 경로 및 파일 이름입니다. 예: 'C:\temp\CompanyPortalEnterpriseSigned.appx'

    -   `-PfxFilePath` – Symantec 인증서의 내보낸 PFX 파일에 대한 로컬 경로 및 파일 이름입니다. 예: 'C:\signing\cert.pfx'

    -   `-PfxPassword` – 작은따옴표로 묶은 PFX 파일에 서명하는 데 사용되는 암호입니다. 예: '1234'

    -   `-AetxPath` – 'EnterpriseId' 인수가 정의되지 않은 경우 엔터프라이즈 ID를 읽는 데 사용되는 .aetx 파일에 대한 로컬 경로입니다. 이 인수 또는 EnterpriseId를 제공해야 합니다. 예: 'C:\signing\cert.aetx'

    -   `-PublisherId` - 엔터프라이즈의 게시자 ID입니다. 없는 경우 Symantec Enterprise 모바일 코드 서명 인증서의 '제목' 필드를 사용합니다. 예: 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1'

    -   `-SdkPath` - Windows 8.1용 Windows SDK의 루트 폴더에 대한 경로입니다. 이 인수는 선택 사항이며 기본적으로 ${env:ProgramFiles(x86)}\Windows Kits\8.1입니다.

    -   `-EnterpriseId` - 엔터프라이즈 ID입니다. 이 인수 또는 'AetxPath'를 제공해야 합니다. 이 인수를 제공하지 않으면 AETX 파일에서 엔터프라이즈 ID를 읽습니다. 예: 1000000001

6.  Windows Phone 8.1 회사 포털(SSP.appx) 앱을 배포합니다. 관련 지침은 [Windows Phone LOB(기간 업무) 앱을 추가하는 방법](lob-apps-windows-phone.md)을 참조하세요.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Symantec 엔터프라이즈 코드 서명 인증서를 갱신하는 방법

Windows 및 Windows Phone 모바일 앱을 배포하는 데 사용되는 Symantec 인증서는 주기적으로 갱신해야 합니다.

1.  인증서가 만료되기 약 14일 전에 Symantec에서 보낸 갱신 전자 메일을 찾습니다. 이 전자 메일에 Symantec의 엔터프라이즈 인증서 갱신 관련 지침이 포함되어 있습니다.

    Symantec 인증서에 대한 자세한 내용을 확인하려면 [www.symantec.com](http://www.symantec.com) 을 방문하거나 1-877-438-8776 또는 1-650-426-3400로 전화 문의하세요.

2.  웹사이트(예: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do))로 이동하여 인증서와 연결된 Symantec 게시자 ID 및 이메일 주소를 사용하여 로그인합니다. 이때 인증서를 다운로드하는 데 사용하려는 것과 같은 컴퓨터를 사용하여 갱신을 시작해야 합니다.

3.  갱신이 승인 및 결제되면 인증서를 다운로드합니다.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>LOB(기간 업무) 앱에 업데이트된 인증서를 설치하는 방법

1.  기간 업무 앱의 최신 버전에 서명합니다.

2.  Azure Portal을 열고 **관리** &gt; **모바일 장치 관리** &gt; **Windows Phone**으로 이동한 후에 **서명된 앱 업로드**를 클릭합니다.

3.  새로 서명된 회사 포털을 업로드합니다. 새로 서명된 SSP.xap와 Symantec에서 받은 새로운 .PFX 파일 또는 이러한 새 .PFX 파일로 생성한 응용 프로그램 등록 토큰이 필요합니다.

4.  업로드가 완료되면 **소프트웨어**  작업 영역에서 이전 회사 포털 버전을 제거합니다.

5.  새 인증서를 사용하여 모든 신규 및 업데이트된 엔터프라이즈 기간 업무 앱에 서명합니다. 기존 응용 프로그램에 다시 서명하고 다시 배포할 필요가 없습니다.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Windows 10 회사 포털 앱 수동 배포
비즈니스용 Microsoft 스토어와 Intune을 통합하지 않았더라도 Intune에서 곧바로 Windows 10 회사 포털 앱을 수동으로 배포할 수 있습니다.

 > [!NOTE]
 > 이 옵션을 사용하려면 앱 업데이트가 릴리스될 때마다 수동 업데이트를 배포해야 합니다.

1. 자신의 계정으로 [비즈니스용 Microsoft 스토어](https://www.microsoft.com/business-store)에 로그인하고 **오프라인 라이선스** 버전의 회사 포털 앱을 가져옵니다.  
2. 앱을 가져왔으면 **인벤토리** 페이지에서 앱을 선택합니다.  
3. **플랫폼**으로 **Windows 10 all devices**(Windows 10 모든 장치)를 선택한 다음 적절한 **아키텍처**를 선택하고 다운로드합니다. 이 앱에는 앱 라이선스 파일이 필요 없습니다.
![Windows 10 모든 장치 및 아키텍처 X86 패키지 다운로드 세부 정보를 보여 주는 이미지](./media/Win10CP-all-devices.png)
4. "Required Frameworks"(필요한 프레임워크)에 나온 모든 패키지를 다운로드합니다. x86, x64 및 ARM 아키텍처에 대해 수행해야 하므로 아래와 같이 총 9개의 패키지가 됩니다.

![다운로드할 종속성 파일의 이미지 ](./media/Win10CP-dependent-files.png)
5. 회사 포털 앱을 Intune에 업로드하기 전에 패키지를 포함하는 폴더(예: C:&#92;Company Portal)를 다음과 같은 방법으로 만듭니다.
   1. C:\Company Portal에 회사 포털 패키지를 배치합니다. 이 위치에 Dependencies 하위 폴더도 만듭니다.  
   ![APPXBUN 파일과 함께 저장된 Dependencies 폴더의 이미지](./media/Win10CP-Dependencies-save.png)
   2. Dependencies 폴더에 9개의 종속성 패키지를 배치합니다.  
   종속성을 이 형식으로 배치하지 않는 경우 Intune은 패키지 업로드 도중에 패키지를 인식 및 업로드할 수 없습니다. 이에 따라 업로드에 실패하고 다음과 같은 오류가 표시됩니다.  
   ![이 소프트웨어 설치 관리자의 Windows 앱 종속성이 응용 프로그램 폴더에 없습니다. 이 응용 프로그램을 계속 만들고 배포할 수 있지만 누락된 Windows 앱 종속성이 제공될 때까지 실행되지 않습니다.](./media/Win10CP-error-message.png)
6. Intune으로 돌아간 후 회사 포털 앱을 새 앱으로 업로드합니다. 원하는 대상 사용자 집합에게 필수 앱으로 배포합니다.  

Intune에서 유니버설 앱의 종속성을 처리하는 방식에 대한 자세한 내용은 [Deploying an appxbundle with dependencies via Microsoft Intune MDM(Microsoft Intune MDM을 통해 종속성이 포함된 appxbundle 배포)](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)을 참조하세요.  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>사용자가 이미 스토어에서 이전 앱을 설치한 경우 어떻게 사용자의 장치에서 회사 포털을 업데이트하나요?
사용자가 이미 스토어에서 Windows 8.1 또는 Windows Phone 8.1 회사 포털 앱을 설치한 경우 관리자나 사용자의 별도 조치가 필요 없이 앱이 자동으로 새 버전으로 업데이트됩니다. 업데이트가 이루어지지 않는 경우 사용자에게 장치에서 스토어 앱에 대해 자동 업데이트를 활성화했는지 확인하도록 요청합니다.   

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
