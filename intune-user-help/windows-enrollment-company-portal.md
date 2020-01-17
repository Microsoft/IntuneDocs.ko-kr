---
title: Intune 회사 포털에서 Windows 디바이스 등록| Microsoft Docs
description: 회사 포털에서 Windows 디바이스 등록 시작
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 86c158f73d820fa2e719fe92b884c77f315fcb94
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75858814"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Intune 회사 포털에서 Windows 디바이스 등록  

회사 포털에서 Windows 디바이스를 등록하면 회사 및 학교 앱, 이메일 및 파일에 안전하게 액세스할 수 있습니다. 조직에서 Office나 OneDrive와 같은 특정 앱이 필요하거나 권장하는 경우, 등록하는 동안 받거나, 등록한 후에 회사 포털에서 사용할 수 있습니다.  

Windows 10 디바이스는 회사 포털 웹 사이트 또는(*or*) 앱을 통해 등록할 수 있습니다. 이전 버전의 Windows가 설치된 디바이스를 등록하는 경우에는 회사 포털을 통해 디바이스를 등록해야 합니다.  

## <a name="install-company-portal-app"></a>회사 포털 앱 설치  
회사 포털 앱이 디바이스에 이미 설치되어 있을 수도 있습니다. __모든 앱__ 목록에서 앱이 있는지 확인하세요.  앱 목록에 회사 포털이 표시되지 않으면 다음 단계를 따라 설치합니다.  

1. 디바이스에서 **Microsoft Store**를 엽니다.

2. **검색** 필드에 **회사 포털**을 입력합니다.

3. 결과 목록에서 **회사 포털** > **설치**를 선택합니다.

4. **설치** 또는 **무료** 중 하나를 선택합니다. 이 두 가지 옵션은 차이가 없습니다. 조직에서 앱이 설정된 방식을 기반으로 다른 단어가 표시됩니다.  

## <a name="find-windows-10-version-number"></a>Windows 10 버전 번호 찾기  
Windows 10 디바이스의 버전에 따라 등록 단계가 다릅니다. 다음 단계는 Windows 10 Desktop 및 Mobile 디바이스에서 버전 번호를 찾는 방법을 설명합니다. 버전이 확인되면 권장되는 등록 단계를 계속 진행하세요.  

### <a name="windows-10-desktop-devices"></a>Windows 10 데스크톱 디바이스  

1. **시작**으로 이동합니다.

2. 검색 창에 "PC 정보"라는 문구를 입력합니다. 결과에서 __PC 정보__를 선택합니다.  


   ![PC 정보 설정 검색](media/searching_for_about_your_pc.png)  

3. **Windows 사양**이 보일 때까지 아래로 스크롤하여 PC에 설치된 Windows 10 **버전**을 확인합니다.  


   ![Windows 10 데스크톱 PC 정보](media/settings_about_pc.png)  

4. 확인된 버전이:  

    * __1607 이상__: [**설정** > **계정** > **회사 또는 학교 액세스** 경로](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)를 통해 디바이스를 등록합니다.   
    * __1511 이하__: [**설정** > **계정** > **내 계정** 경로](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)를 통해 디바이스를 등록합니다.  

### <a name="windows-10-mobile-devices"></a>Windows 10 모바일 디바이스

1. __모든 앱__으로 이동하여 __설정__ 앱을 선택합니다.
2. __시스템__ > __정보__를 선택합니다.
3. __디바이스 정보__에서 __버전__을 확인합니다.  
4. 확인된 버전이:  

    * __1607 이상__: [**설정** > **회사 또는 학교 액세스** 경로](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)를 사용하여 디바이스를 등록합니다.   
    * __1511 이하__: [**설정** > **계정** 경로](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)를 사용하여 디바이스를 등록합니다.  

## <a name="enroll-non-windows-10-devices"></a>Windows 10 이외의 디바이스 등록  
다음 문서를 사용하여 회사 포털 웹 사이트를 통해 지원되는 기타 Windows 디바이스를 등록할 수 있습니다.   
* [Windows 8.1 또는 Windows RT 8.1 디바이스](enroll-your-W81-or-rt81-windows.md)  
* [Windows Phone 8.1 디바이스](enroll-your-wp81-windows.md)    

## <a name="it-administrator-support"></a>IT 관리자 지원  
IT 관리자가 디바이스를 등록하는 동안 문제가 발생하면 [Microsoft Intune에서 Windows 디바이스 등록 문제 해결](https://support.microsoft.com/help/4469913)을 참조하세요. 이 문서에는 일반적인 오류와 그 원인 및 해결 단계가 나열되어 있습니다.  

## <a name="next-steps"></a>다음 단계  
지원되는 디바이스와 Windows 10 버전 번호를 파악했으면, 권장되는 등록 문서로 진행하세요.  
 
디바이스 관리, 회사 포털 및 회사와 학교에서 이 모두를 사용하는 방법에 대한 자세한 내용은 다음 문서를 참조하세요.  
* [관리 디바이스를 사용하여 회사 또는 학교 리소스에 액세스](use-managed-devices-to-get-work-done.md)  
* [Intune에 디바이스를 등록할 때 발생되는 작업](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [내 디바이스를 등록하면 조직에 어떤 정보가 표시되나요?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

도움이 필요하십니까? 회사 지원 부서에 문의하세요. [회사 포털 웹 사이트로 이동](https://go.microsoft.com/fwlink/?linkid=2010980)하면 귀사의 IT 연락처 정보를 찾을 수 있습니다.  
