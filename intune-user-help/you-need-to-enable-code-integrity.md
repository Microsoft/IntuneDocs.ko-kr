---
title: 코드 무결성을 사용하도록 설정해야 함 | Microsoft 문서
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 84892bbc-f888-417b-bbeb-978cc7e10028
searchScope:
- User help
ROBOTS: ''
ms.reviewer: scottduf
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 56982c6ce10f74617471307acd176a0506655398
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72501234"
---
# <a name="enable-code-integrity"></a>코드 무결성 사용

조직에서 *코드 무결성*이라는 위협 방지 기능을 사용 하 여 PC를 사용 하도록 요구할 수 있습니다. 코드 무결성은 장치의 드라이버 및 시스템 파일에서 손상이 나 악성 소프트웨어의 서명을 확인 합니다. 장치에서 코드 무결성이 작동 하려면 [*보안 부팅*](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process#secure-boot) 이라는 또 다른 보안 기능도 사용 하도록 설정 해야 합니다.

코드 무결성이 사용 하지 않도록 설정 되어 PC가 호환 되지 않는 경우 조직의 IT 지원 팀에 문의 해야 합니다. 다음에 장치를 시작할 때 코드 무결성을 트리거하는 보안 부팅을 사용 하는 데 도움이 됩니다.

사용자를 고급 장치 사용자로 식별 하는 경우 해당 단계를 직접 시도 하려면 [보안 부팅 다시 사용](https://docs.microsoft.com/windows-hardware/manufacture/desktop/disabling-secure-boot#re-enable-secure-boot)을 참조 하세요.

## <a name="additional-resources-for-it-administrators"></a>IT 관리자를 위한 추가 리소스

Intune 관리자 인 경우 intune의 장치 상태 준수 설정에 대해 자세히 알아보려면 [intune에서 Windows 10 장치에 대 한 장치 준수 정책 추가](https://docs.microsoft.com/intune/protect/compliance-policy-create-windows.md)를 참조 하세요. Intune에서 수행할 수 있는 준수 작업을 자세히 확인 하려면 [HEALTHATTESTATION CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp#step-8-take-appropriate-policy-action-based-on-evaluation-results)를 참조 하세요.  

## <a name="next-steps"></a>다음 단계

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
