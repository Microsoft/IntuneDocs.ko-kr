---
title: Android 디바이스가 암호화된 것 같음 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2017
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
ms.openlocfilehash: 55935b2f69f9573d8df5ea5ca32fb4587c652b26
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389474"
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Android 디바이스가 암호화된 것 같은데 회사 포털에 다르게 표시됨

디바이스를 암호화하는 경우 자신만 알고 있는 비밀 키로 디바이스의 정보를 인코딩합니다. 이렇게 하면 권한이 없는 사용자가 해당 정보에 액세스할 수 없습니다. 많은 조직에서 해당 사용자가 Android 디바이스를 암호화해야 회사 파일, 메일 또는 데이터에 액세스할 수 있도록 합니다.

## <a name="common-issues"></a>일반적인 문제

최신 버전의 Android(특히 v7.0 이상 버전)에서는 디바이스가 완전하게 암호화되도록 시작 암호를 설정해야 합니다. 시작 암호의 설명과 위치는 디바이스 제조업체마다 다릅니다. 대부분의 경우 이 설정은 "보안 시작"이라고 합니다. 

## <a name="solutions"></a>솔루션

### <a name="add-a-startup-pin"></a>시작 PIN 추가

특정 Android 디바이스에서는 디바이스의 보안을 유지하기 위해 시작 PIN을 만들어야 합니다. 여러 제조업체에서 다양한 버전의 Android를 사용하고 있습니다. 설정 앱에서 이 옵션을 사용하도록 설정하는 위치를 찾아 이 문제의 해결을 시도해 볼 수 있습니다. 예를 들어 Samsung Galaxy S7에서는 **설정** > **잠금 화면 및 보안** > **보안 시작**으로 이동하여 보안 시작을 사용하도록 설정합니다.  

### <a name="encrypt-the-entire-device"></a>전체 디바이스 암호화

일부 디바이스에서는 전체 디바이스를 암호화할지 아니면 사용된 공간만을 암호화할지 선택하도록 합니다. "사용된 공간만 해당"이 아닌 전체 디바이스를 암호화하는 옵션을 선택합니다. 이미 사용된 공간만 암호화한 경우:

1. [회사 포털에서 이 디바이스 제거](unenroll-your-device-from-intune-android.md)
2. 사용된 공간의 암호 해독
3. 전체 디바이스 암호화
4. 디바이스 다시 등록

### <a name="downgrade-your-version-of-android"></a>Android 버전 다운그레이드

디바이스에서 Android 6.0 이상으로 다운그레이드하는 옵션을 제공하는 경우 다운그레이드합니다. 디바이스 다운그레이드를 시도해야 하는 경우 데이터 손실 위험이 있습니다. 그렇지 않으면 회사 지원팀에 문의하여 이 문제를 해결하는 것이 좋습니다. [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에서 회사 지원팀의 연락처 정보를 얻을 수 있습니다.

## <a name="specific-manufacturer-issues"></a>특정 제조업체 문제

버전 7.0 이상의 일부 Android 디바이스에서는 특정 Android 플랫폼 표준과 일치하지 않는 방식으로 데이터를 암호화합니다. 이러한 디바이스는 신규 제품인 경우에도 암호화된 상태로 표시될 수 있습니다. Intune에서는 이러한 디바이스의 암호화 방법으로 인해 디바이스 정보가 위험에 노출된다는 점을 인지하고 있습니다. 이러한 위험은 주로 디바이스에 물리적으로 액세스할 수 있는 악의적인 사용자에서 기인합니다.

> [!Note]
> Microsoft는 제조업체와 협력하여 테스트 중에 확인되거나 사용자들이 보고하는 문제를 해결합니다. 새로운 정보를 사용할 수 있을 때마다 이 문서를 업데이트합니다. 

## <a name="known-devices"></a>알려진 디바이스

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>이 문제를 해결하기 위해 업데이트할 수 있는 알려진 디바이스

최신 버전의 Android 장치를 업데이트 하지 않은, 경우 장치의으로 이동 **설정을** 앱을 선택 **업데이트**합니다. 이러한 장치를 업데이트할 때까지 호환 불가능으로 나타날 수 있습니다.  

- Huawei Honor 8
- Huawei P9

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>현재 이 문제를 해결하기 위해 업데이트할 수 없는 알려진 디바이스
다음 장치는 항상 암호화 된 상태로 표시 하 고 회사 리소스 액세스에 사용할 수 없습니다. 회사 리소스에 액세스 하려면 다른 장치를 사용 해야 합니다.  

- Huawei Mate 8
- OPPO 디바이스
- Vivo 디바이스
- Xiaomi Mi 스마트폰
