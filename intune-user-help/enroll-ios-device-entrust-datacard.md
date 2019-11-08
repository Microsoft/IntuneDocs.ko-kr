---
title: Intune 회사 포털 및 Entrust Datacard를 사용 하 여 iOS 또는 iPadOS 장치 등록
description: IOS 또는 iPadOS 장치를 등록 하 고 Entrust Datacard를 사용 하 여 파생 된 자격 증명 인증을 설정 합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfafa4f35d0b8f1255d66a70c3f7cd0acf01a889
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415765"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-entrust-datacard"></a>회사 포털 및 Entrust Datacard를 사용 하 여 iOS 또는 iPadOS 장치 설정

Intune 회사 포털 앱으로 디바이스를 등록하여 조직의 메일, 파일 및 앱에 대한 보안 모바일 액세스 권한을 얻습니다. 디바이스가 등록되면 *관리*됩니다. 조직은 Intune과 같은 MDM(모바일 디바이스 관리) 공급자를 통해 디바이스에 정책과 앱을 할당할 수 있습니다.  

등록 하는 동안 장치에 파생 된 자격 증명을 설치 합니다. 조직에서 리소스에 액세스 하거나 메일을 서명 하 고 암호화 하는 경우 파생 자격 증명을 인증 방법으로 사용 하도록 요구할 수 있습니다. 

스마트 카드를 사용 하 여 다음을 수행 하는 경우 파생 자격 증명을 설정 해야 할 수 있습니다.  

* 학교 또는 업무용 앱, Wi-fi 및 VPN (가상 사설망)에 로그인
* S/MIME 인증서를 사용 하 여 학교 또는 직장 메일 서명 및 암호화  

이 문서에서는 다음을 수행합니다.  

   * Intune 회사 포털를 사용 하 여 모바일 iOS 또는 iPadOS 장치를 등록 합니다.  
   * 조직의 파생 자격 증명 공급자 [Entrust Datacard](https://www.entrustdatacard.com/)에서 파생 된 자격 증명을 가져옵니다.  

### <a name="what-are-derived-credentials"></a>파생 된 자격 증명 이란?  
파생 된 자격 증명은 스마트 카드 자격 증명에서 파생 되 고 장치에 설치 되는 인증서입니다. 회사 리소스에 대 한 원격 액세스 권한을 부여 하는 동시에 권한 없는 사용자가 중요 한 정보에 액세스 하지 못하도록 합니다.  

파생 된 자격 증명을 사용 하 여 다음을 수행 합니다. 
* 학교 또는 업무용 앱, Wi-fi 및 VPN에 로그인 하는 학생 및 직원 인증
* S/MIME 인증서를 사용 하 여 학교 또는 직장 메일 서명 및 암호화

파생 자격 증명은 SP(Special Publication) 800-157의 일부로 PIV(Personal Identity Verification) 파생 자격 증명에 관한 NIST(미국 국립표준기술원) 지침을 구현한 것입니다.  

## <a name="prerequisites"></a>전제 조건

 등록을 완료 하려면 다음이 있어야 합니다.

* 학교 또는 회사에서 제공 하는 스마트 카드
* 스마트 카드를 사용 하 여 로그인 할 수 있는 컴퓨터 또는 키오스크에 대 한 액세스
* 모바일 장치
* 장치에 설치 된 iOS 및 iPadOS 용 Intune 회사 포털 앱  


## <a name="enroll-device"></a>디바이스 등록  
1. 모바일 장치에서 iOS/iPadOS 용 회사 포털 앱을 열고 회사 계정으로 로그인 합니다.  

2. 화면 코드를 기록 합니다.  

    ![화면 메시지 및 코드가 있는 회사 포털 앱의 예제 이미지입니다.](./media/copy-code-intercede.png)   

3. 스마트 카드 사용 장치로 전환 하 고 https://microsoft.com/devicelogin 로 이동 합니다. 
4. 이전에 작성 한 코드를 입력 합니다.  

    !["코드 입력" 프롬프트 회사 포털 웹 사이트의 예제 스크린샷](./media/enter-code-intercede.png)   

5. 로그인 하려면 스마트 카드를 삽입 합니다.   
6. 모바일 장치의 회사 포털 앱으로 돌아가서 화면의 지시에 따라 장치를 등록 합니다.  
7. 등록이 완료 된 후 회사 포털는 스마트 카드를 설정 하는 것을 알려 줍니다. 알림을 탭합니다. 알림을 얻지 못한 경우 전자 메일을 확인 합니다.   

    ![장치 홈 화면에서 회사 포털 푸시 알림에 대 한 예제 스크린샷](./media/action-required-in-app-intercede.png)  

8. **모바일 스마트 카드 액세스 설정** 화면에서 다음을 수행 합니다.   
    a. 조직의 설치 지침에 대 한 링크를 탭 합니다. 조직에서 추가 지침을 제공 하지 않으면이 문서에 전송 됩니다.  
    b. **시작**을 탭 합니다.  

    ![모바일 스마트 카드 액세스 화면을 설정 하 회사 포털의 예제 스크린샷](./media/smart-card-info-intercede.png)

9. 스마트 카드 사용 장치로 전환 하 고 IdentityGuard을 엽니다. 
10. 스마트 자격 증명 로그인 영역을 찾고 로그인 단추를 선택 합니다.  
11. 인증서를 선택 하 라는 메시지가 표시 되 면 스마트 카드 자격 증명을 선택 합니다. 그런 다음 **확인을**선택 합니다. 
12. 스마트 카드 PIN을 입력 합니다.  
13. 작업 목록에서 선택 하 라는 메시지가 표시 됩니다. 파생 된 모바일 스마트 자격 증명을 등록할 수 있는 항목을 선택 합니다. 링크 또는 단추는 파생 된 **모바일 스마트 카드 자격 증명을 등록 하** 는 것을 말합니다.  
14. 스마트 자격 증명 사용 응용 프로그램을 다운로드 하 고 설치 했는지 선택 합니다. 그런 후 다음 화면으로 진행 합니다.   
15. 파생 된 스마트 카드 자격 증명에 대 한 정보를 입력 합니다.  
    a. Id 이름에 *Entrust 파생 된 자격 증명*등의 이름을 입력 합니다.  
    b. 드롭다운 메뉴에서 **Entrust IdentityGudard Mobile 스마트 증명**을 선택 합니다.  
    c. 다음 화면으로 진행 합니다. 여기에 숫자 암호가 있는 QR 코드가 표시 됩니다.  

16. 모바일 장치로 돌아갑니다. 회사 포털 > **QR 코드 가져오기** 화면에서 **계속**을 탭 합니다. 

    ![QR 코드 가져오기 화면 회사 포털의 예제 스크린샷](./media/get-qr-code-intercede.png)  
17. **카메라 사용** > **확인을**탭 합니다.  

    ![카메라 액세스를 허용 하는 권한을 요청 하는 회사 포털 프롬프트의 예제 스크린샷](./media/allow-cp-camera-access-intercede.png)  
18. 스마트 카드 사용 장치에 있는 QR 코드 이미지를 검색 합니다.  
19. QR 코드 아래에 표시 되는 숫자 암호를 입력 합니다.  

    ![회사 포털 암호 필요 화면의 예 스크린샷, 암호 입력 필드입니다.](./media/enter-password-derived-credentials.png)   

20. 회사 포털에서 장치 설정을 마칠 때까지 기다립니다.  


## <a name="next-steps"></a>다음 단계  
등록이 완료 되 면 전자 메일, Wi-fi 및 조직에서 사용할 수 있는 모든 앱과 같은 회사 리소스에 액세스할 수 있습니다. 회사 포털에서 앱을 가져오고, 검색 하 고, 설치 하 고, 제거 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.

* [회사 포털 웹 사이트에서 앱 관리](manage-apps-cpweb.md)  
* [디바이스에서 관리되는 앱 사용](use-managed-apps-on-your-device-ios.md)  

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.  
