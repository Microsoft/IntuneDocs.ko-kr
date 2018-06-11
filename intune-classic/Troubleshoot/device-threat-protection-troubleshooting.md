---
title: Lookout 통합 문제 해결
description: 이 항목에서는 Lookout 통합에서 흔히 발생하는 문제의 해결 방법을 설명합니다.
keywords: ''
author: NathBarn
ms.author: nathbarn
manager: dougeby
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6262fee0051827794c49ebe10361b1a3b280b140
ms.sourcegitcommit: f21287c66dd5559688f08bd98b6c976a0dea055d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2018
ms.locfileid: "34470800"
---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Intune과 Lookout의 통합 문제 해결

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

이 항목에서는 Lookout MTP(Mobile Threat Protection) 설정 시 흔히 발생하는 몇 가지 문제를 설명합니다.

**로그인 오류**

## <a name="403-errors"></a>403 오류
[Lookout MTP 콘솔](https://aad.lookout.com)에 로그인할 때 403 오류(**서비스에 액세스할 권한이 없습니다.**)가 표시됩니다. 이 오류는 지정된 사용자 이름이 Lookout MTP에 액세스하도록 구성된 Azure AD(Azure Active Directory) 그룹의 구성원이 아닌 경우에 발생할 수 있습니다.

Lookout MTP를 통해, 구성된 Azure AD 그룹의 사용자만 서비스에 액세스할 수 있습니다. Lookout MTP에 액세스하도록 구성된 그룹을 확인하려면 다음 방법으로 Lookout 지원 부서에 문의하세요.

* 메일: enterprisesupport@lookout.com
* [MTP 콘솔](http://aad.lookout.com)에 로그인한 다음 **지원** 모듈로 이동합니다.
* <https://enterprise.support.lookout.com/hc/requests>로 이동하고 지원을 요청합니다.

## <a name="unable-to-sign-in"></a>로그인할 수 없음
Azure AD 전역 관리자가 초기 Lookout 설정을 수락하지 않은 경우 다음 오류가 표시됩니다.

![로그인 오류를 보여 주는 Lookout 로그인 화면의 스크린샷](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

이 문제를 해결하려면 전역 관리자가 https://aad.lookout.com/les?action=consent에 로그인하고 메시지에 동의하여 설정을 시작해야 합니다. 자세한 정보는 [Lookout MTP 구독 설정](../deploy-use/setup-your-lookout-mtd-subscription.md) 항목에서 확인할 수 있습니다.

**장치 상태 문제**

## <a name="device-missing-from-lookout-device-list"></a>Lookout 장치 목록에서 누락된 장치

이 문제는 다음 시나리오에서 발생할 수 있습니다.
* 장치 사용자가 **Lookout MTP 콘솔**에서 지정된 **등록 그룹**에 없습니다.  [Lookout 콘솔](http://aad.lookout.com)에서 **시스템** > **Intune 커넥터** > **등록 관리**로 이동합니다.  등록에 대해 구성된 Azure AD 그룹을 검토하고, 장치 사용자가 Azure AD 그룹 중 하나에 속해 있는지 확인합니다.  사용자를 등록 그룹에 추가하면 장치가 Lookout MTP 콘솔의 **장치** 모듈에 표시되는 데 구성된 최대 폴링 간격(5분이 기본값임)까지 걸릴 수 있습니다.
* 장치가 Lookout MTP에서 지원되지 않는 경우.  지원되지 않는 장치는 Lookout MTP 콘솔의 커넥터 설정에서 **관리되는 장치** 섹션에 나타납니다.

### <a name="device-reported-as-pending"></a>**보류 중**으로 보고된 장치

최종 사용자가 아직 Lookout for Work 앱을 열어 **활성화** 단추를 탭하지 않은 경우 장치가 **보류 중**으로 표시됩니다. Lookout for work 앱 관련 장치 활성화에 대한 자세한 내용은 [Android 장치에 Lookout for Work를 설치하라는 메시지가 표시됨](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android) 또는 [iOS 장치에 Lookout for Work를 설치하라는 메시지가 표시됨](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-ios)을 참조하세요.

## <a name="device-whos-active-but-has-no-device-id"></a>활성 상태이지만 장치 ID가 없는 장치
Lookout MTP 콘솔에서, 활성 장치에 장치 ID가 없으면 장치 사용자가 등록 그룹에 없습니다. 장치 사용자가 등록 그룹에서 제거되었거나 등록 그룹이 제거된 경우에도 장치는 이 상태가 될 수 있습니다.

[Lookout 콘솔](http://aad.lookout.com)에서 **시스템** > **Intune 커넥터** > **등록**으로 이동하여 설정을 검토합니다.  Azure AD 그룹을 검토하고, 장치 사용자가 Azure AD 그룹 중 하나에 속해 있는지 확인합니다.

장치가 이 상태에 있다면 Lookout은 위협을 감지하면 계속해서 사용자에게 알려주기는 하지만 Intune에 위협 정보를 전송하지는 않습니다.

## <a name="device-reported-as-disconnected"></a>**연결 끊김**으로 보고된 장치

**연결 끊김**이란 장치가 구성된 시간(기본적으로 30일, 최소 7일) 내에 Lookout MTP와 동기화하지 않음을 의미합니다. 회사 포털 앱 또는 Lookout for Work 앱이 장치에서 누락되었습니다. 앱을 다시 설치하면 이 문제가 해결될 것입니다. 사용자가 Lookout for Work를 열어 앱을 활성화하면 장치가 Lookout MTP, Intune과 함께 다시 동기화됩니다.

### <a name="forcing-a-device-sync"></a>장치 동기화 강제 적용
관리자는 Lookout MTP 콘솔의 **장치** 모듈에서 장치를 선택한 후 삭제하도록 선택할 수 있습니다.   다음번에 장치 소유자가 Lookout for Work 앱을 열어 **활성화**를 탭하면 장치 상태가 완전히 다시 동기화됩니다.

## <a name="device-has-a-new-user"></a>장치에 새 사용자가 있음
장치를 초기화하고 새 사용자에게 등록하도록 요청해야 합니다.  장치를 관리에서 제거하도록, [Intune 관리자 콘솔](https://manage.microsoft.com)에서 장치를 선택한 후 마우스 오른쪽 단추로 클릭하여 **사용 중지/초기화**를 선택합니다. 장치를 사용 중지한 후 삭제할 수 있습니다.

![사용 중지/초기화 옵션이 표시된 Intune 관리 콘솔의 장치 모듈 스크린샷](../media/mtp/mtp-retire-device-intune-console.png)

[Lookout 콘솔](http://aad.lookout.com)의 **장치** 모듈로 이동하여 **삭제**를 선택할 수도 있습니다.

새 사용자가 Lookout MTP 등록 그룹에 속해 있는 경우 Azure AD에서 장치를 새 사용자에 연결하면 장치가 표시됩니다.

## <a name="compliance-remediation-workflows"></a>규정 준수 수정 워크플로
- [Android 장치에 Lookout for Work를 설치하라는 메시지가 표시됨](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)
- [Lookout for Work가 Android 장치에서 발견한 위협을 해결해야 함](http://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [iOS 장치에서 Lookout for Work가 발견한 위협을 해결해야 함](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>참고 항목
[Lookout MTP 구독 설정](/intune-classic/deploy-use/set-up-your-subscription-with-lookout-mtp)
