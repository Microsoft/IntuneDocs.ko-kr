---
title: Intune 회사 포털을 사용하여 Windows 10 디바이스 등록 | Microsoft Docs
description: Intune 회사 포털에서 Windows 10 디바이스를 등록하는 단계
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/21/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: df83f2763d5fe7ae26ad30fecca56128aaa8437c
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856238"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Intune 회사 포털을 사용하여 Windows 10 디바이스 등록

Intune 회사 포털을 사용하여 Windows 10 디바이스를 조직의 관리 하에 등록합니다. 이 문서에서는 Windows 10 버전 1607 이상 및 Windows 10 버전 1511 이전 버전을 사용하는 디바이스를 등록하는 방법을 설명합니다. 시작하기 전에 올바른 단계를 수행할 수 있도록 [디바이스의 버전을 확인](windows-enrollment-company-portal.md#find-windows-10-version-number)하세요.  

Windows 10은 데스크톱, 휴대폰 및 태블릿을 비롯한 다양한 디바이스 유형에서 지원됩니다. 어떤 디바이스를 사용하든 등록 단계는 동일합니다. 그러나 화면은 이 문서에 표시된 이미지와 약간 다르게 보일 수 있습니다.  
</br>
> [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Windows 10 버전 1607 이상 디바이스 등록 
이러한 단계는 Windows 10 버전 1607 이상에서 실행되는 디바이스를 등록하는 방법을 설명합니다.  

1. **시작**으로 이동합니다. Windows 10 모바일 디바이스를 사용하는 경우 **모든 앱** 목록으로 계속 진행합니다.

2. **설정** 앱을 엽니다. 앱 목록에서 앱을 쉽게 사용할 수 없는 경우 검색 창에서 “설정”을 입력합니다.

3. **계정** > **회사 또는 학교 액세스** > **연결**을 선택합니다.  


    ![회사 또는 학교 계정 액세스 선택](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. 조직의 Intune 로그인 페이지로 이동 하려면 회사 또는 학교 전자 메일 주소를 입력 합니다. **다음**을 선택합니다.  


   ![회사 또는 학교 계정 입력](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. 회사 또는 학교 계정을 사용하여 Intune에 로그인합니다.  


    ![회사 또는 학교 계정 추가](./media/w10-enroll-rs1-enter-your-credentials.png)  

    회사 또는 학교에서 내 디바이스를 등록하고 있다는 메시지가 최종적으로 표시됩니다.

6. 조직에서 Windows Hello에 대한 PIN을 설정해야 하는 경우 확인 코드를 입력하라는 메시지가 표시됩니다. 코드를 입력하고 PIN을 만들기 위해 화면에 나타나는 단계를 계속 진행합니다.  

7. **모든 설정이 끝났습니다.** 화면에서 **완료**를 선택하여 이제 디바이스가 등록됩니다.  

8. 연결을 다시 한 번 확인하려면 **설정** > **계정** > **회사 또는 학교 액세스**로 이동합니다.  이제 계정이 나열됩니다.  


    ![연결이 제대로 설정되었는지 확인](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

회사 또는 학교 메일, 파일 또는 기타 데이터에 여전히 액세스할 수 없나요? [계정 문제를 해결](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)하는 방법을 알아봅니다.  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Windows 10 버전 1511 이전 디바이스 등록  
이러한 단계는 Windows 10 버전 1511 이전에서 실행되는 디바이스를 등록하는 방법을 설명합니다.  

1. **시작**으로 이동합니다. Windows 10 모바일 디바이스를 사용하는 경우 **모든 앱** 목록으로 계속 진행합니다.

2. **설정** 앱을 엽니다. 앱 목록에서 앱을 쉽게 사용할 수 없는 경우 검색 창에서 “설정”을 입력합니다.

3. **계정** > **사용자의 계정**을 선택합니다.  


    ![계정 선택](./media/W10-enroll-2-accounts-your-account.png)  

5. **회사 또는 학교 계정 추가**를 선택합니다.  


    ![회사 또는 학교 계정 추가 선택](./media/w10-enroll-3-add-work-school-acct.png)  

6. 회사 또는 학교 자격 증명으로 로그인합니다.  


    ![로그인](./media/W10-enroll-4-sign-in.png)  

회사 또는 학교 메일, 파일 또는 기타 데이터에 여전히 액세스할 수 없나요? 등록하는 도중에 [계정 관련 문제를 해결](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account)하는 방법을 알아봅니다.  

## <a name="it-administrator-support"></a>IT 관리자 지원   

IT 관리자가 디바이스를 등록하는 동안 문제가 발생하면 [Microsoft Intune에서 Windows 디바이스 등록 문제 해결](https://support.microsoft.com/help/4469913)을 참조하세요. 이 문서에는 일반적인 오류와 그 원인 및 해결 단계가 나열되어 있습니다. 

## <a name="next-steps"></a>다음 단계  
회사 포털 또는 등록에 대한 도움이 필요하면 조직의 IT 지원팀에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)에서 찾을 수 있습니다. 회사 또는 학교 계정을 사용하여 사이트에 로그인합니다.  

 

