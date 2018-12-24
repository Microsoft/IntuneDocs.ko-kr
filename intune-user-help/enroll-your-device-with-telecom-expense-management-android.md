---
title: Intune을 사용하여 TEM(Telecom Expense Management)에 Android 디바이스 등록
description: TEM(Telecom Expense Management)에 Android 디바이스를 등록하는 방법에 대해 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 26aa3698-7e4d-453a-8852-ab75e72b6485
searchScope:
- User help
ROBOTS: ''
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 56682656ce9b935bbde595663e4feb0cdc725cb3
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43147887"
---
# <a name="enroll-your-android-device-in-telecom-expense-management"></a>TEM(Telecom Expense Management)에 Android 디바이스 등록

조직에서 데이터 및 음성 요금제가 허용 한도 내에서 사용되고 있는지 확인하기 위해 TEM(Telecom Expense Management)을 사용하고 있을 수 있습니다. 디바이스를 등록하면 해당 디바이스의 가장 적합한 범주를 선택하라는 메시지가 표시됩니다.

![iOS 디바이스의 "가장 적합한 범주 선택" 화면의 스크린샷 회사 또는 개인 등록 선택 항목이 표시됩니다.](./media/and-enroll-11-tem-select-best-category.png)

적절한 옵션을 선택하면 Google Play 스토어에서 [__Datalert__](https://play.google.com/store/apps/details?id=fr.memobox.databox) 앱을 설치하라는 알림이 제공됩니다. Datalert 앱은 조직에서 데이터 사용량을 측정하는 데 사용됩니다. 조직에서 회사 또는 학교 등록 옵션을 구성한 경우 회사 또는 학교 계정으로 로그인해야 합니다. 사용하도록 설정되지 않은 경우에는 전화번호와 같은 정보를 제공하고 앱에서 Datalert 서비스에 등록하는 코드를 사용하여 디바이스를 확인해야 합니다.

화면 오른쪽 위에 있는 __다음__ 화살표를 탭하여 계속 진행합니다. 회사 지원팀은 __Microsoft 회사 또는 학교 계정__으로 로그인할지, __전화번호__를 사용할지를 알려 주어야 합니다.

  ![Datalert에서 데이터 요금제를 최대한 활용할 수 있는 방법에 대한 간략한 설명을 제공한 후 다음 화면으로 이동하라는 메시지가 표시된 Datalert 앱 시작 화면의 스크린샷](./media/and-enroll-12-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>Microsoft 회사 또는 학교 계정을 사용하여 Datalert에 등록

1. __Microsoft 계정으로 등록__을 선택합니다.

   ![Microsoft Office 365 계정 및 Intune 구독이 있는 경우에 한해 Datalert 앱의 설정 화면 상단에서 디바이스를 등록하는 전화번호 필드를 제공하는 해당 화면 이미지](./media/and-enroll-12a-tem-datalert-enroll-msft-account.png)

2. 사용할 수 있는 계정에서 회사 또는 학교 계정을 선택합니다. 사용자 계정이 목록에 없는 경우에는 **계정 추가** 단추를 사용하여 로그인할 수 있습니다.

   ![샘플 계정 및 계정 추가 단추를 보여 주는 "계정 선택" 화면의 스크린샷](./media/and-enroll-12b-tem-datalert-enroll-select-msft-account.png)

3. 잠시 동안 Datalert 설정이 진행되고 난 후 완료됩니다. 완료되면 __마침__을 탭합니다.

## <a name="enroll-into-datalert-using-your-phone-number"></a>전화번호를 사용하여 Datalert에 등록

1. 디바이스의 전화 번호를 제공합니다.

   ![전화 번호를 요청하는 Datalert 앱의 스크린샷](./media/and-enroll-13-tem-datalert-phone-number.png)

2. 그러면 SMS 메시지를 통해 확인 코드가 제공됩니다. 코드를 제공하고 __확인__를 탭합니다.

   ![SMS 확인 코드를 요청하는 Datalert 앱의 스크린샷](./media/and-enroll-14-tem-datalert-sms.png)

3. 확인 코드를 제공하면 Datalert 설치가 완료됩니다. __마침__을 탭하면 Datalert 앱에서 데이터를 모니터링할 수 있습니다.

   ![오늘의 데이터 사용량을 모니터링하는 Datalert 앱의 스크린샷](./media/and-enroll-15-tem-datalert-monitoring-active.png)

등록을 완료했으면 Datalert 앱에서 데이터 사용량을 확인하기 시작합니다.

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
