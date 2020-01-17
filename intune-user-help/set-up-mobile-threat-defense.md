---
title: 모바일 디바이스에 Mobile Threat Defense 설치
description: 모바일 디바이스에 Mobile Threat Defense 설치하는 방법을 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 6b75712cf05626999c09e8d74fd28252666313c4
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857877"
---
# <a name="install-mobile-threat-defense"></a>Mobile Threat Defense 설치   

조직의 보안 요구 사항에 따라 MTD (모바일 위협 방어) 공급 업체 앱을 설치 해야 할 수 있습니다. 이 유형의 앱은 의심 스러운 앱, 네트워크, OS 취약성 등의 장치에 대 한 위협을 감지 하 고 경고 합니다.  

필수 MTD 앱이 없으면 회사 또는 학교 계정을 사용 하 여 보호 된 앱에 로그인 하지 못하게 됩니다. 이 문서에서는 차단을 해제 하기 위해 [MTD 앱을 설치 하는 방법을](set-up-mobile-threat-defense.md#install-app) 알아봅니다.  

설치할 수 있는 다양 한 MTD 공급 업체 앱이 있습니다. 조직에서 사용할 항목을 알려 드리겠습니다. 


## <a name="information-your-organization-can-see"></a>조직에서 볼 수 있는 정보   

조직에서는 개인 앱에서 텍스트, 전자 메일, 사진 등의 데이터를 볼 수 없습니다. MTD 앱은 이름 및 버전과 같은 앱에 대 한 정보를 조직에 보고 합니다. 보고 되는 실제 정보는 회사에서 사용 하는 MTD 공급 업체에 따라 다릅니다. 조직에 다음이 표시 될 수 있습니다.   

* 앱 이름  
* 앱 ID: Google Play에서 앱을 식별하는 고유한 이름입니다.  
* 앱 버전 및 짧은 버전 번호: 앱의 특정 릴리스 번호입니다.  
* 앱 번들 및 동적 크기: 디바이스에서 앱이 사용하는 공간의 크기입니다. 


## <a name="install-app"></a>앱 설치    
보호 된 앱에 로그인 할 때 MTD 앱을 설치 하 라는 메시지가 자동으로 표시 됩니다. 화면의 단계를 따라 설치를 완료 합니다. 추가 도움말을 보려면이 섹션의 단계를 사용 합니다.  
 
장치를 등록 하 라는 메시지가 표시 될 수도 있습니다. Id를 확인 하 고 학교 또는 회사 계정을 장치에 연결 하려면 등록이 필요 합니다. 등록 되지 않은 경우 MTD 앱을 설치 하기 전에 해당 설치 프로그램을 자동으로 안내 합니다. **액세스 권한 가져오기** 화면으로 이동 하면 설치 단계를 시작할 수 있습니다.  

장치 등록에 대 한 자세한 내용은 [조직의 네트워크에 개인 장치 등록](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)을 참조 하세요.  

### <a name="ios-setup"></a>iOS 설정  

1. **액세스 권한 가져오기** 화면에서 지침에 따라 조직에 필요한 MTD 앱을 설치 합니다.   
2. **액세스 권한 가져오기** 화면으로 돌아가서 **열기**를 선택 합니다.  
3. MTD 앱은 Microsoft Authenticator를 열 수 있는 권한을 요청 합니다. **열기**를 선택합니다. 
4. 로그인 할 회사 계정을 선택 합니다. 
5. MTD 앱이 장치에서 보안 위협을 검색 하는 동안 기다립니다. 
6. 처음에 액세스 하려고 했던 학교 또는 회사 앱으로 돌아갑니다. 이 시점에서 조직에는 PIN 작성과 같은 기타 앱 보안 요구 사항을 구성 하 라는 메시지가 표시 될 수 있습니다.   
7. 이제 앱에 액세스할 수 있습니다. 여전히 차단 된 경우:  
    * **액세스 권한 가져오기** 화면에서 다시 확인 **을 선택 합니다**.  
    * MTD 앱으로 이동 하 여 기존 위협에 대해 확인 합니다. 권장 단계를 완료 하 여 위협을 해결 하 고 액세스 권한을 다시 얻을 수 있습니다.    

### <a name="android-setup"></a>Android 설정 

1. **액세스 권한 가져오기** 화면에서 지침에 따라 조직에 필요한 MTD 앱을 설치 합니다.  
2. **액세스 권한 가져오기** 화면으로 돌아가서 **열기**를 선택 합니다.  
3. MTD 앱은 필요한 경우 장치에서 특정 영역에 액세스할 수 있는 권한을 요청 합니다. 이 앱이 제대로 작동 하려면 연락처에 대 한 액세스를 **허용** 해야 합니다. 요청 된 권한은 MTD 공급 업체에 따라 다릅니다.  
4. 로그인 할 회사 계정을 선택 합니다.  
5. MTD 앱이 장치에서 보안 위협을 검색 하는 동안 기다립니다.  
6. 처음에 액세스 하려고 했던 학교 또는 회사 앱으로 돌아갑니다. 이 시점에서 조직에는 PIN 작성과 같은 기타 앱 보안 요구 사항을 구성 하 라는 메시지가 표시 될 수 있습니다.  
7. 이제 앱에 액세스할 수 있습니다. 여전히 차단 된 경우:  
    * **액세스 권한 가져오기** 화면에서 다시 확인 **을 선택 합니다**.  
    * MTD 앱으로 이동 하 여 기존 위협에 대해 확인 합니다. 권장 단계를 완료 하 여 위협을 해결 하 고 액세스 권한을 다시 얻을 수 있습니다.  

### <a name="installation-failed"></a>설치 실패  

설치에 실패 하면 IT 지원 담당자에 게 문의 하세요. [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)로 이동하면 귀사의 연락처 정보를 찾을 수 있습니다.  

또한 IT 지원 담당자에 게 앱 로그를 보내 설치에 대 한 추가 컨텍스트를 제공할 수 있습니다.  
* Android 사용자: 회사 포털에서 [로그를 업로드 하 고 전자 메일로 보냅니다](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android) .   

* iOS 장치 사용자: iOS 용 Microsoft Edge에서 [로그를 검색 하 고 전송](https://docs.microsoft.com/intune/apps/manage-microsoft-edge#use-microsoft-edge-on-ios-to-access-managed-app-logs) 합니다.  

## <a name="resolve-a-threat"></a>위협 해결  
위협이 조직의 정의 된 위협 수준을 초과 하는 경우 조직에서 다음을 수행 합니다.  
   
* 액세스 차단: 회사 또는 학교 계정에 로그인 한 상태에서 조직의 보호 된 앱을 사용 하는 것을 차단 합니다.  
* 데이터 초기화: 조직의 보호 된 앱 중 하나 이상에서 회사 또는 학교 데이터를 삭제 합니다.  

위협을 해결 하 고 액세스 권한을 다시 얻으려면 장치에서 MTD 앱을 엽니다. 제공 된 정보를 읽고 위협이 장치에 어떤 영향을 주는지 확인 하 고 해결 하는 방법을 알아보세요. 위협을 해결 하는 단계를 수행한 후 MTD 앱으로 돌아가서 새 검색을 시작 합니다. 조직에 액세스 하는 데 몇 분 정도 걸릴 수 있습니다.  

## <a name="next-steps"></a>다음 단계  

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.

