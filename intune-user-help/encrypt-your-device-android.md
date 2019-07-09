---
title: Intune에 대 한 Android 장치를 암호화 합니다. | Microsoft Docs
description: Intune에 필요한 경우에 Android 장치 암호화를 설정 하는 단계
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfc17c60412a1cfe90693216caa69ada3d2d2c9a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545254"
---
# <a name="encrypting-your-android-device"></a>Android 디바이스 암호화

장치 암호화 장치를 분실 하거나 도난당 하는 경우 무단된 액세스 로부터 파일 및 폴더 보호 합니다. 장치 암호화를 설정한 후에 올바른 암호 또는 pin을 사용 하 여 개인만 장치에 로그인 할 수 있게 됩니다. 

학교 또는 회사 리소스에 액세스 하려면 조직 Android 장치 암호화 하도록 요구할 수 있습니다. 일부 최신 Android 장치는 기본적으로 암호화 된 기본 제공 합니다.  

## <a name="turn-on-encryption"></a>암호화 설정

회사 포털 또는 Microsoft Intune 앱 장치를 암호화 하 라는 메시지가 표시를 하는 경우 다음 단계를 완료 합니다. 

> [!Note]
> Huawei, 제품과 Vivo 및 OPPO에서 특정 Android 장치를 암호화할 수 없습니다. 자세한 내용은 [여기](your-device-appears-encrypted-but-cp-says-otherwise-android.md)를 참조하세요.  

1. 장치 화면 잠금을 설정 합니다.  
    a. **설정** > **잠금 화면 및 보안** > **화면 잠금**으로 이동합니다.  
    b. 중 하나를 선택 **PIN**하십시오 **암호**, 또는 **패턴**합니다.  
    c. 화면 잠금을 구성 하려면 화면의 지침을 따릅니다.  

2. 로 돌아가서 **잠금 화면 및 보안** 선택한 **안전한 시작**합니다.
3. 선택할 **장치 설정 하는 경우 PIN 요청** > **확인**합니다.
4. 확인 하 고 장치를 암호화 하려면 PIN을 입력 합니다.
5. 회사 포털 또는 Microsoft Intune 앱을 엽니다.
    * 회사 포털 앱 사용자: 디바이스를 선택하고 **디바이스 설정 확인**을 탭합니다. 
    * Microsoft Intune 사용자: 페이지 업데이트 될 때까지 대기 해야 하지만 암호화 상태를 준수에 변경 해야 합니다.  

Android 4.4 이전 버전을 실행 하는 장치 수 없게 합니다 **보안 시작** 옵션입니다. 이 경우 장치를 암호화 하려면 다음 단계를 완료 합니다.

1. 로 이동 **설정을** > **Security** > **장치를 암호화**합니다. 화면에 나타나는 레이블을 Android 장치 마다 다릅니다. 표시 되지 않는 경우는 **장치 암호화** 옵션, 체크 인 합니다.
    * **저장소** > **Storage 암호화**
    * **저장소** > **잠금 화면 및 보안** > **기타 보안 설정** 

2. 화면의 지시를 따릅니다. 암호화가 진행되는 동안 디바이스가 여러 번 다시 시작될 수 있습니다.
3. 회사 포털 또는 Microsoft Intune 앱을 엽니다.
    * 회사 포털 앱 사용자: 디바이스를 선택하고 **디바이스 설정 확인**을 탭합니다.  
    * Microsoft Intune 사용자: 페이지 업데이트 될 때까지 대기 해야 하지만 암호화 상태를 준수에 변경 해야 합니다.

## <a name="troubleshoot"></a>문제 해결  
**문제**: 장치를 이미 암호화 했으므로 및

- 암호화 단추를 사용할 수 없습니다.
- 여전히 암호화해야 한다는 메시지가 표시됩니다.
- 회사 포털 또는 Microsoft Intune 앱을 사용 하려고 할 때 오류를 가져옵니다.

**시도할 작업**

- 디바이스가 충전되었고 전원에 연결되어 있는지 확인합니다.  
- 디바이스에서 PIN 또는 암호를 설정했는지 확인합니다.  

여전히 도움이 필요하세요? 회사 지원팀에 문의하거나(연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 확인) <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 팀</a>으로 메일을 보내세요.  
