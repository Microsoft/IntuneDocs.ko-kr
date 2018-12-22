---
title: Intune용 Apple MDM Push Certificate 가져오기
titlesuffix: ''
description: Intune에서 iOS 디바이스를 관리하기 위해 Apple MDM Push Certificate를 가져옵니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 053e3f42553268aaeff0502e2cfe05b33b18618b
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032166"
---
# <a name="get-an-apple-mdm-push-certificate"></a>Apple MDM 푸시 인증서 가져오기

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Apple MDM Push Certificate는 Intune에서 iOS 및 macOS 장치를 관리하는 데 필요합니다. 인증서를 Intune에 추가하면 사용자는 다음을 사용하여 장치를 등록할 수 있습니다.

- 회사 포털 앱.

- 장비 등록 프로그램, Apple School Manager 또는 Apple Configurator 같은 Apple의 대량 등록 메서드입니다.

등록 옵션에 대한 자세한 내용은 [iOS 장치를 등록하는 방법 선택](enrollment-method-choose-ios.md)을 참조하세요.

푸시 인증서가 만료되는 경우 갱신해야 합니다. 갱신하는 경우 처음 푸시 인증서를 만들 때 사용했던 동일한 Apple ID를 사용했는지 확인합니다.


## <a name="steps-to-get-your-certificate"></a>인증서를 가져오는 단계
[Azure Portal](https://portal.azure.com)에서 **장치 등록** > **Apple 등록** > **Apple MDM Push Certificate**를 선택한 후 [Azure Portal](https://portal.azure.com)에서 이런 단계를 따릅니다.

### <a name="step-1-grant-microsoft-permission-to-send-user-and-device-information-to-apple"></a>1단계. Apple에 사용자 및 장치 정보를 보내려면 Microsoft 권한 부여
**동의**를 선택합니다. Apple에 데이터를 보내려면 Microsoft 권한을 제공 합니다.

![MDM Push가 설정되지 않은 Configure MDM Push Certificate 화면입니다.](./media/create-mdm-push-certificate.png)

### <a name="step-2-download-the-intune-certificate-signing-request-required-to-create-an-apple-mdm-push-certificate"></a>2단계. Apple MDM Push Certificate를 만드는 데 필요한 Intune 인증서 서명 요청 다운로드
**CSR 다운로드**를 선택하여 요청 파일을 로컬로 다운로드하고 저장합니다. 이 파일은 APC(Apple Push Certificate) 포털에서 트러스트 관계 인증서를 요청하는 데 사용됩니다.

  ### <a name="step-3-create-an-apple-mdm-push-certificate"></a>3단계: Apple MDM Push Certificate 만들기
**MDM Push Certificate 만들기**를 선택하여 APC(Apple Push Certificate) 포털로 이동합니다. 회사 Apple ID로 로그인한 다음 **인증서 만들기**를 클릭합니다. **파일 선택**을 선택하고 인증서 서명 요청 파일을 찾은 다음 **업로드**를 선택합니다. 확인 페이지에서 **다운로드**를 선택하여 인증서 파일(.pem)을 다운로드하고 로컬에 파일을 저장합니다.

> [!NOTE]
> 인증서는 인증서 생성에 사용된 Apple ID와 연결됩니다. 모범 사례로 관리 작업에 대한 회사 Apple ID를 사용하고 사서함이 배포 목록과 같은 둘 이상의 사용자에 의해 모니터링되어야 합니다. 절대로 개인 Apple ID를 사용하지 마세요.

### <a name="step-4-enter-the-apple-id-used-to-create-your-apple-mdm-push-certificate"></a>4단계. MDM Push Certificate를 만드는 데 사용되는 Apple ID 입력
이 인증서를 갱신해야 하는 경우 참조할 수 있도록 이 ID를 기록합니다.

### <a name="step-5-browse-to-your-apple-mdm-push-certificate-to-upload"></a>5단계. Apple MDM Push Certificate로 이동하여 업로드
인증서(.pem) 파일로 이동한 후 **열기**를 선택하고 **업로드**를 선택합니다. 푸시 인증서를 사용하여 Intune에서 Apple 장치를 등록하고 관리할 수 있습니다.

## <a name="renew-apple-mdm-push-certificate"></a>Apple MDM 푸시 인증서 갱신
Apple MDM 푸시 인증서는 1년 동안 유효하며 iOS 및 macOS 장치 관리를 유지하려면 매년 갱신해야 합니다. 인증서가 만료되면 등록된 Apple 장치에 연결할 수 없습니다.

인증서는 인증서 생성에 사용된 Apple ID와 연결됩니다. MDM 푸시 인증서를 인증서 생성에 사용한 것과 같은 Apple ID로 갱신합니다.

1. [Azure Portal](https://portal.azure.com)에서 **장치 등록** > **Apple 등록**을 선택한 다음, 세부 정보 영역에서 **Apple MDM Push Certificate** 타일을 선택합니다.
2. **CSR 다운로드**를 선택하여 요청 파일을 로컬로 다운로드하고 저장합니다. 이 파일은 APC(Apple Push Certificate) 포털에서 트러스트 관계 인증서를 요청하는 데 사용됩니다.
3. **MDM Push Certificate 만들기**를 선택하여 APC(Apple Push Certificate) 포털로 이동합니다. 갱신할 인증서를 찾고 **갱신**을 선택합니다.
4. **푸시 인증서 갱신** 화면에서 나중에 인증서 구분에 도움이 되도록 메모를 입력하고 **파일 선택**을 선택하여 다운로드한 새로운 요청 파일을 선택한 후 **업로드**를 선택합니다.
   > [!TIP]
   > UID로 인증서를 식별할 수 있습니다. 인증서 세부 정보의 **주체 ID**를 검사하여 UID의 GUID 부분을 찾습니다. 또는 등록된 iOS 장치에서 **설정** > **일반** > **장치** **관리** > **관리 프로필** > **자세한 내용** > **관리 프로필**로 이동합니다. 두 번째 줄 항목 **토픽**에는 Apple Push Certificate 포털의 인증서와 일치시킬 수 있는 고유 GUID가 포함됩니다.
 
6. **확인** 화면에서 **다운로드**를 선택하고 .pem 파일을 로컬로 저장합니다.
7. [Azure Portal](https://portal.azure.com)에서 **Apple MDM 푸시 인증서** 찾아보기 아이콘을 선택하고 Apple에서 다운로드한 .pem 파일을 선택한 다음, **업로드**를 선택합니다.

Apple MDM 푸시 인증서가 **활성화**에 나타나고 365일 후 만료됩니다.
