---
title: Intune 회사 포털에서 Windows 장치 등록 | Microsoft Docs
description: 회사 포털에서 Windows 장치 등록 시작
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/12/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: a637b6eed162243d2be81ac08fbcc055e1fd5816
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069176"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Intune 회사 포털에서 Windows 장치 등록  

회사 및 학교 앱, 이메일 및 파일에 보안 액세스를 Intune 회사 포털 앱에서 Windows 장치를 등록 합니다. 조직의 필요 하거나 권장 특정 앱, Office 또는 OneDrive와 같은 하거나 받게 하 등록 중 또는 등록 후 회사 포털에서 사용할 수 있는 수 됩니다.  

회사 포털 웹 사이트를 통해 Windows 10 장치를 등록할 수 있습니다 *또는* 앱. 이전 버전의 Windows 사용 하 여 장치를 등록 하는 경우 회사 포털 웹 사이트를 통해 장치를 등록 해야 합니다.  

## <a name="install-company-portal-app"></a>설치 회사 포털 앱  
장치에 설치 된 회사 포털 앱을 이미 있을 수 있습니다. 앱에 대 한 확인 프로그램 __모든 앱__ 목록입니다.  앱 목록에 회사 포털이 표시되지 않으면 다음 단계를 따라 설치합니다.  

1. 오픈 **Microsoft Store** 장치의 합니다.

2. 에 **검색** 필드에 입력 **회사 포털**합니다.

3. 결과 목록에서 **회사 포털** > **설치**를 선택합니다.

4. **설치** 또는 **무료** 중 하나를 선택합니다. 이러한 두 옵션 간에 차이가 없습니다. 조직 앱을 설정 하는 방법에 따라 표시 됩니다.  

## <a name="find-windows-10-version-number"></a>Windows 10 버전 번호를 찾습니다.  
다른 버전의 Windows 10 장치에 대 한 등록 단계가 다릅니다. 다음 단계는 Windows 10의 버전 번호를 찾는 방법 설명 데스크톱 및 모바일 장치. 버전을 확인 한 후에 권장 되는 등록 단계를 계속 합니다.  

### <a name="windows-10-desktop-devices"></a>Windows 10 데스크톱 디바이스  

1. **시작**으로 이동합니다.

2. 검색 표시줄을 PC."정보" 라고 입력 선택 __PC 정보__ 결과에서 합니다.  


   ![PC 정보 설정 검색](media/searching_for_about_your_pc.png)  

3. 아래로 스크롤하여 **Windows 사양** 찾으려고 합니다 **버전** PC에 설치 된 Windows 10의.  


   ![Windows 10 데스크톱 PC 정보](media/settings_about_pc.png)  

4. 버전인 경우  

    *  __1607 이상을__:의 방식으로 장치를 등록 합니다 [ **설정** > **계정** > **회사 또는 학교액세스**경로](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)합니다.   
    * __1511 이하의__:의 방식으로 장치를 등록 합니다 [ **설정** > **계정** > **계정의** 경로](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)합니다.  

### <a name="windows-10-mobile-devices"></a>Windows 10 모바일 디바이스       

1.  로 이동 __모든 앱__ 선택 합니다 __설정__ 앱.  
2.  __시스템__ > __정보__를 선택합니다.      
3.  아래 __장치 정보__를 찾을 합니다 __버전__합니다.  
4. 버전인 경우  

    *  __1607 이상을__: 사용 하 여 장치를 등록 합니다 [ **설정** > **회사 또는 학교 액세스** 경로](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)합니다.   
    * __1511 이하의__: 사용 하 여 장치를 등록 합니다 [ **설정** > **계정** 경로](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

## <a name="enroll-non-windows-10-devices"></a>비 Windows 10 장치를 등록 합니다.  
회사 포털 웹 사이트를 통해 지원 되는 다른 Windows 장치를 등록 하려면 다음 문서를 사용 합니다.   
* [Windows 8.1 또는 Windows RT 8.1 디바이스](enroll-your-W81-or-rt81-windows.md)  
* [Windows Phone 8.1 디바이스](enroll-your-wp81-windows.md)    

## <a name="next-steps"></a>다음 단계  
지원 되는 장치 및 Windows 10 버전 번호가 파악 했으므로 권장 되는 등록 문서를 진행 합니다.  
 
회사 포털 및 둘 다 사용 하는 방법 회사, 학교에는 장치 관리에 대 한 자세한 내용은 다음 문서를 참조 합니다.  
* [관리 디바이스를 사용하여 회사 또는 학교 리소스에 액세스](use-managed-devices-to-get-work-done.md)  
* [Intune에 디바이스를 등록할 때 발생되는 작업](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [내 디바이스를 등록하면 조직에 어떤 정보가 표시되나요?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

도움이 필요하십니까? 회사 지원 부서에 문의하세요. [회사 포털 웹 사이트로 이동](https://go.microsoft.com/fwlink/?linkid=2010980) 찾을 조직의 IT 연락처 정보.  
