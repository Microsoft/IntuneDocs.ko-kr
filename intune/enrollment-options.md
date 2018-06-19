---
title: Microsoft Intune에서 관리되는 장치에 대한 등록 옵션
titleSuffix: ''
description: Microsoft Intune에서 관리되는 장치에 대해 관리자가 설정할 수 있는 등록 옵션 목록입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
ms.openlocfilehash: 67805253f432098736e0fb96776e8f7f0ff44cc3
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2018
ms.locfileid: "29748721"
---
# <a name="enrollment-options-for-devices-managed-by-intune"></a>Intune에서 관리되는 장치에 대한 등록 옵션

Intune 관리자는 장치 등록을 구성하여 사용자에게 도움을 주고 Intune 기능을 사용하도록 설정할 수 있습니다.  Intune에서 제공하는 등록 옵션은 다음과 같습니다.

## <a name="terms-and-conditions"></a>Terms and conditions

사용자가 회사의 사용 약관에 동의해야만 회사 포털을 통해 장치를 등록하고 회사 앱 및 메일 같은 리소스에 액세스하도록 요구할 수 있습니다. 사용 약관의 구성은 선택 사항입니다. [사용 약관](terms-and-conditions-create.md)에 대해 자세히 알아보세요.

## <a name="enrollment-restrictions"></a>등록 제한 사항

다음과 같은 요소에 따라 장치 등록을 제한하도록 선택할 수 있습니다.
- 장치 플랫폼
- 사용자당 장치 수
- 개인 장치 차단

[등록 제한 사항](enrollment-restrictions-set.md)에 대해 자세히 알아보세요.

## <a name="enable-apple-device-enrollment"></a>Apple 장치 등록 사용

iOS 및 macOS 장치 등록에는 MDM 푸시 인증서가 필요합니다. [MDM 푸시 인증서](apple-mdm-push-certificate-get.md)에 대해 자세히 알아보세요.

## <a name="corporate-identifiers"></a>회사 식별자

IMEI(International Mobile Equipment Identity) 번호 또는 일련 번호를 표시하여 회사 소유의 장치를 식별할 수 있습니다. [기업 식별자](corporate-identifiers-add.md)에 대해 자세히 알아보세요.
## <a name="multi-factor-authentication"></a>Multi-factor Authentication

장치를 등록할 때 전화, PIN 또는 생체 인식 데이터와 같은 추가 확인 방법을 사용하도록 사용자에게 요구할 수 있습니다. [다단계 인증](multi-factor-authentication.md)에 대해 자세히 알아보세요.

## <a name="device-enrollment-manager"></a>장치 등록 관리자
사용자를 장치 등록 관리자로 지정할 수 있습니다.  DEM 사용자는 단일 사용자 계정으로 많은 수의 모바일 장치를 등록할 수 있습니다. DEM(장치 등록 관리자) 계정은 최대 1,000개의 장치를 등록할 수 있습니다. [장치 등록 관리자](device-enrollment-manager-enroll.md)에 대해 자세히 알아보세요.

## <a name="device-categories"></a>장치 범주

장치 범주를 사용하여 정의된 범주에 따라 자동으로 장치를 그룹에 추가할 수 있습니다. 장치를 그룹으로 구성하면 더욱 쉽게 해당 장치를 관리할 수 있습니다. [장치 범주](device-group-mapping.md)에 대해 자세히 알아보세요.
