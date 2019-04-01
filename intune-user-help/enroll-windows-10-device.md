---
title: Intune 회사 포털에서 Windows 10 장치 등록 | Microsoft Docs
description: Intune 회사 포털에서 Windows 10 장치를 등록 하는 단계
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/11/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4eb5dbb150559de7ad30a598fb78a4fa78033c42
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069166"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Intune 회사 포털을 사용 하 여 Windows 10 장치를 등록 합니다.

Intune 회사 포털을 사용 하 여 조직의 관리 Windows 10 장치를 등록 합니다. 이 문서에서는 Windows 10 버전 1607 이상 및 Windows 10 버전 1511 및 이전 버전을 사용 하 여 장치를 등록 하는 방법을 설명 합니다. 시작 하기 전에 했는지 [장치의 버전을 확인할](windows-enrollment-company-portal.md#find-windows-10-version-number) 올바른 단계를 수행할 수 있도록 합니다.  

Windows 10은 데스크톱, 휴대폰 및 태블릿을 비롯 한 다양 한 장치 유형에 서 지원 합니다. 등록 단계를 사용 하는 어떤 장치에서 동일 합니다. 그러나 화면은이 문서에 표시 된 이미지에서 약간 다르게 보일 수 있습니다.  

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Windows-Enrollment/player]  

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Windows 10 버전 1607 및 이상 장치를 등록 합니다. 
이러한 단계는 Windows 10 버전 1607 이상에서 실행 되는 장치를 등록 하는 방법을 설명 합니다.  

1. **시작**으로 이동합니다. Windows 10 Mobile 장치를 사용 하는 경우 계속 해 서 합니다 **모든 앱** 목록입니다.

2. **설정** 앱을 엽니다. 검색 표시줄 및 형식 "설정입니다."로 이동 하는 앱을 앱 목록에서 쉽게 사용할 수 없으면

3. **계정** > **회사 또는 학교 액세스** > **연결**을 선택합니다.  


    ![회사 또는 학교 계정 액세스 선택](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. 회사 또는 학교 메일 주소를 입력하고 **다음**을 선택합니다.  


   ![회사 또는 학교 계정 입력](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. 회사 또는 학교 계정을 사용하여 Intune에 로그인합니다.  


    ![회사 또는 학교 계정 추가](./media/w10-enroll-rs1-enter-your-credentials.png)  

    회사 또는 학교에서 내 디바이스를 등록하고 있다는 메시지가 최종적으로 표시됩니다.

6. Windows Hello PIN을 설정 해야 하는 조직에서 확인 코드를 입력 하 라는 메시지가 됩니다. 코드를 입력 하 고 계속 진행 된 PIN을 화면에 나타나는 단계입니다.  

7. **모든 설정이 끝났습니다.** 화면에서 **완료**를 선택하여 이제 디바이스가 등록됩니다.  

8. 연결을 다시 한 번으로 돌아가서 **설정을** > **계정** > **회사 또는 학교 액세스**합니다.  이제 계정이 나열 됩니다.  


    ![연결이 제대로 설정되었는지 확인](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

회사 또는 학교 메일, 파일 또는 기타 데이터에 여전히 액세스할 수 없나요? 설명 하는 방법 [계정 문제를 해결](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)합니다.  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Windows 10 버전 1511 및 이전 장치를 등록 합니다.  
이러한 단계는 Windows 10 버전 1511 및 이전 버전에서 실행 되는 장치를 등록 하는 방법을 설명 합니다.  

1. **시작**으로 이동합니다. Windows 10 Mobile 장치를 사용 하는 경우 계속 해 서 합니다 **모든 앱** 목록입니다.

2. **설정** 앱을 엽니다. 검색 표시줄 및 형식 "설정입니다."로 이동 하는 앱을 앱 목록에서 쉽게 사용할 수 없으면

3. 선택 **계정을** > **계정의**합니다.  


    ![계정 선택](./media/W10-enroll-2-accounts-your-account.png)  

5. **회사 또는 학교 계정 추가**를 선택합니다.  


    ![회사 또는 학교 계정 추가 선택](./media/w10-enroll-3-add-work-school-acct.png)  

6. 회사 또는 학교 자격 증명으로 로그인합니다.  


    ![로그인](./media/W10-enroll-4-sign-in.png)  

회사 또는 학교 메일, 파일 또는 기타 데이터에 여전히 액세스할 수 없나요? 설명 하는 방법 [계정 문제를 해결](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account)합니다.   

## <a name="next-steps"></a>다음 단계  

도움말을 보려면 회사 지원에 문의 합니다. 조직의 있습니다 IT에 대 한 정보를 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)합니다. 회사 또는 학교 계정을 사용하여 사이트에 로그인합니다.  

 

