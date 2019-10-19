---
title: Intune 용 Android 장치 암호화 | Microsoft Docs
description: Intune에서 필요한 경우 Android 장치 암호화를 설정 하는 단계
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2965d6a017d92bd4535a29a2257c0cac5e6deaf
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506353"
---
# <a name="encrypting-your-android-device"></a>Android 디바이스 암호화

장치 암호화는 장치를 분실 하거나 도난당 한 경우 무단 액세스 로부터 파일 및 폴더를 보호 합니다. 장치 암호화를 켜면 올바른 암호나 pin이 있는 개인만 장치에 로그인 할 수 있습니다. 

학교 또는 회사 리소스에 액세스 하기 전에 조직에서 Android 장치를 암호화 하도록 요구할 수 있습니다. 최신 Android 장치는 기본적으로 기본적으로 암호화 되어 있습니다.  

## <a name="turn-on-encryption"></a>암호화 설정

회사 포털 또는 Microsoft Intune 앱에서 장치를 암호화 하 라는 메시지가 표시 되 면 다음 단계를 완료 합니다. 

> [!Note]
> Huawei, Vivo 및 OPPO의 특정 Android 장치는 암호화할 수 없습니다. 자세한 내용은 [여기](your-device-appears-encrypted-but-cp-says-otherwise-android.md)를 참조하세요.  

1. 장치 화면 잠금을 설정 합니다.  
    a. **설정** > **잠금 화면 및 보안** > **화면 잠금**으로 이동합니다.  
    b. **PIN**, **암호**또는 **패턴**중 하나를 선택 합니다.  
    c. 화면의 지시에 따라 화면 잠금을 구성 합니다.  

2. **잠금 화면 및 보안** 으로 돌아가서 **보안 시작**을 선택 합니다.
3. **장치가 켜지 면 PIN 필요**  > **확인을**선택 합니다.
4. PIN을 입력 하 여 장치를 확인 하 고 암호화 합니다.
5. 회사 포털 또는 Microsoft Intune 앱을 엽니다.
    * 회사 포털 앱 사용자: 디바이스를 선택하고 **디바이스 설정 확인**을 탭합니다. 
    * Microsoft Intune 사용자: 페이지를 업데이트할 때까지 기다려야 합니다. 단, 암호화 상태를 준수로 변경 해야 합니다.  

Android 4.4 이전 버전을 실행 하는 장치에는 **보안 시작** 옵션이 없을 수 있습니다. 이 경우 다음 단계를 완료 하 여 장치를 암호화 합니다.

1. **설정**  > **보안**  > **장치 암호화**로 이동 합니다. 화면 레이블은 Android 장치 마다 다릅니다. **장치 암호화** 옵션이 표시 되지 않으면 다음을 선택 합니다.
    * **저장소**  > **storage 암호화**
    * **저장소**  > **잠금 화면 및 보안**  > **기타 보안 설정** 

2. 화면의 지시를 따릅니다. 암호화가 진행되는 동안 디바이스가 여러 번 다시 시작될 수 있습니다.
3. 회사 포털 또는 Microsoft Intune 앱을 엽니다.
    * 회사 포털 앱 사용자: 디바이스를 선택하고 **디바이스 설정 확인**을 탭합니다.  
    * Microsoft Intune 사용자: 페이지를 업데이트할 때까지 기다려야 합니다. 단, 암호화 상태를 준수로 변경 해야 합니다.

## <a name="troubleshoot"></a>문제 해결  
**문제**: 장치를 이미 암호화 했습니다.

- 암호화 단추를 사용할 수 없습니다.
- 여전히 암호화해야 한다는 메시지가 표시됩니다.
- 회사 포털 또는 Microsoft Intune 앱을 사용 하려고 할 때 오류가 발생 합니다.

**시도할 작업**

- 디바이스가 충전되었고 전원에 연결되어 있는지 확인합니다.  
- 디바이스에서 PIN 또는 암호를 설정했는지 확인합니다.  

여전히 도움이 필요하세요? 회사 지원팀에 문의하거나(연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 확인) <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 팀</a>으로 메일을 보내세요.  
