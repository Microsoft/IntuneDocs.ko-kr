---
title: Android 디바이스가 암호화된 것 같음 | Microsoft Docs
description: 회사 포털 및 Microsoft Intune 앱에서 암호화 상태 확인
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d63ecdb23b107d844c37d7a805247092116618e1
ms.sourcegitcommit: b30a2ba2b67aa2fc3421f0b2f6c5f361a0de612a
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69022741"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>장치가 암호화 되어 있지만 앱에는 그렇지 않음

회사 포털 또는 Microsoft Intune 앱에서 장치가 암호화 되지 않은 것으로 표시 되는 경우이 문서의 단계를 수행 합니다.  

## <a name="add-a-startup-pin"></a>시작 PIN 추가

특정 Android 디바이스에서는 디바이스의 보안을 유지하기 위해 시작 PIN을 만들어야 합니다. 이 설정의 위치는 장치의 **설정** 앱에 배치 됩니다. 설정의 이름 및 위치는 다를 수 있습니다. 예를 들어 Samsung Galaxy S7에서 설정을 **보안 시작**이라고 합니다. 이를 사용 하도록 설정 하 고 암호를 만들려면 **설정** > **잠금 화면 및 보안** > 보안**시작**으로 이동 합니다.  

## <a name="encrypt-the-entire-device"></a>전체 디바이스 암호화

이 섹션은 회사 포털 앱에만 적용 됩니다. 일부 디바이스에서는 전체 디바이스를 암호화할지 아니면 사용된 공간만을 암호화할지 선택하도록 합니다. 전체 장치를 암호화 하는 옵션을 선택 합니다. 사용 된 공간만 암호화 하도록 선택한 경우:

1. [회사 포털에서 이 디바이스를 제거](unenroll-your-device-from-intune-android.md)합니다.
2. 사용된 공간의 암호를 해독합니다.  
3. 전체 디바이스를 암호화합니다.  
4. 디바이스 다시 등록.  

## <a name="downgrade-your-version-of-android"></a>Android 버전 다운그레이드

이 섹션은 회사 포털 앱에만 적용 됩니다. 디바이스에서 Android 6.0 이상으로 다운그레이드하는 옵션을 제공하는 경우 다운그레이드합니다. 디바이스 다운그레이드를 시도하는 경우 데이터 손실 위험이 있습니다. 그렇지 않으면 회사 지원팀에 문의하여 이 문제를 해결하는 것이 좋습니다. 회사 지원팀의 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에서 가져옵니다.  

## <a name="specific-manufacturer-issues"></a>특정 제조업체 문제

버전 7.0 이상의 일부 Android 디바이스에서는 특정 Android 플랫폼 표준과 일치하지 않는 방식으로 데이터를 암호화합니다. 이러한 암호화 방법은 장치 정보를 위험에 노출 합니다. 따라서 이러한 장치는 지원 되지 않습니다. 

지원 되는 Android 장치에 대 한 완전 하지 않은 목록은 [Intune에서 지원 되는 운영 체제 및 브라우저](https://docs.microsoft.com/intune/supported-devices-browsers#supported-samsung-knox-standard-devices)문서를 참조 하세요. 장치가 나열 되지 않은 경우 장치 제조업체를 참조 하거나 지원 담당자에 게 문의 하세요. 

> [!Note]
> Microsoft는 제조업체와 협력하여 테스트 중에 확인되거나 사용자들이 보고하는 문제를 해결합니다. 새로운 정보를 사용할 수 있을 때마다 이 문서를 업데이트합니다. 

## <a name="update-devices"></a>장치 업데이트   

장치를 최신 버전의 Android로 업데이트 하지 않은 경우 장치의 **설정** 앱으로 이동 하 여 **업데이트**를 선택 합니다.  

## <a name="next-steps"></a>다음 단계   
여전히 도움이 필요하세요? 회사 지원팀에 문의하거나(연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980) 확인) <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 팀</a>으로 메일을 보내세요.  
