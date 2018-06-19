---
title: 회사 소유의 iOS 장치 등록
description: Apple DEP(장치 등록 프로그램) 또는 Apple Configurator를 사용하여 회사 소유 iOS 장치 등록
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 93ff84d263c2fe8825d2cf5a86249bbf19cb9173
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020914"
---
# <a name="enroll-corporate-owned-ios-devices-in-microsoft-intune"></a>Microsoft Intune에서 회사 소유의 iOS 장치 등록

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune은 Mac 컴퓨터에서 실행되는 [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017) 도구 또는 Apple DEP(장치 등록 프로그램)를 통해 회사 소유의 iOS 장치를 등록하도록 지원합니다.

**필수 조건:** [Apple Push Notification Service 인증서](set-up-ios-and-mac-management-with-microsoft-intune.md)

세 가지 방법 중 하나를 사용하여 회사에 등록된 iOS 장치를 등록할 수 있습니다.

- Apple Configurator에서 설치 도우미 또는 직접 등록 사용
- 장치 등록 프로그램
- 회사 포털 앱

>[!NOTE]
>Apple Configurator 및 장치 등록 프로그램 등록 방법을 [장치 등록 관리자](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) 방법과 함께 사용할 수 없습니다.

기본적으로 모든 iOS 장치는 Intune에서 등록할 수 있습니다. 개인 또는 회사 소유의 장치 등록을 차단하려면 관리자 자격 증명을 사용하여 [Microsoft Intune 관리 포털](https://manage.microsoft.com)에 로그인합니다. **관리** > **모바일 장치 관리** > **등록 규칙**을 선택한 다음 해당 옵션을 선택 취소합니다.

## <a name="use-apple-configurator"></a>Apple Configurator 사용

회사 등록 프로필을 내보낸 후 해당 모바일 장치를 Apple Configurator를 실행하는 Mac에 연결하여 iOS 장치를 등록할 수 있습니다. Apple Configurator는 다음 두 가지 방식의 등록을 지원합니다.

- **설치 도우미 등록**: 장치를 공장 기본 설정으로 복원하고 장치의 새 사용자가 설치하도록 준비합니다. 이 방법을 사용하려면 관리자가 iOS 장치를 [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017)를 실행하는 Mac 컴퓨터에 USB로 연결하여 등록을 미리 구성해야 합니다. 그러면 설치 도우미 프로세스를 실행하는 사용자에게 장치가 제공됩니다. 이 프로세스에서는 회사 또는 학교 자격 증명을 사용하여 장치를 구성하고 등록 프로세스를 완료합니다. 자세한 내용은 [Apple Configurator 및 설정 도우미를 사용하여 iOS 장치 등록](ios-setup-assistant-enrollment-in-microsoft-intune.md)을 참조하세요.

- **직접 등록**: 장치를 준비하는 동안 사용할 수 있도록 Apple Configurator 규격 파일을 만듭니다. 등록된 장치가 공장 기본 설정으로 복원되지 않았으나 사용자 정보가 없습니다. 이 방법을 사용하려면 관리자가 iOS 장치를 [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017)를 실행하는 Mac 컴퓨터에 USB로 연결하여 장치를 등록해야 합니다. 자세한 내용은 [Apple Configurator 직접 등록을 사용하여 iOS 장치 등록](ios-direct-enrollment-in-microsoft-intune.md)을 참조하세요.

## <a name="use-the-device-enrollment-program-dep"></a>DEP(장비 등록 프로그램) 사용
DEP는 DEP를 통해 구입한 장치에 등록 프로필을 "무선으로" 배포합니다. 사용자가 장치에서 설정 도우미를 실행하는 경우 장치는 Intune에 등록됩니다. 자세한 내용은 [장치 등록 프로그램 iOS 장치 등록](ios-device-enrollment-program-in-microsoft-intune.md)을 참조하세요.

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>DEP 또는 Apple Configurator에 등록된 장치에서 회사 포털 사용

사용자 선호도로 구성한 장치에서 회사 포털 앱을 설치하고 실행하여 앱을 다운로드하고 장치를 관리할 수 있습니다. 사용자는 장치를 받은 후 몇 가지 추가 단계를 완료하여 설정 도우미를 완료하고 회사 포털 앱을 설치해야 합니다.

사용자 선호도는 다음을 지원하는 데 필요합니다.
  - MAM(모바일 응용 프로그램 관리) 앱
  - 메일 및 회사 데이터에 대한 조건부 액세스
  - 회사 포털 앱

**사용자가 사용자 선호도를 사용하여 회사 소유의 iOS 장치를 등록하는 방법**
1. 사용자가 장치를 켜면 설정 도우미를 완료하라는 메시지가 표시됩니다. 설정하는 동안 자격 증명을 묻는 메시지가 표시됩니다. Intune에서 구독과 연결된 자격 증명(즉, 고유 이름 또는 UPN)을 사용해야 합니다.

2. 설정하는 동안 Apple ID를 묻는 메시지가 표시됩니다. 장치에서 회사 포털을 설치할 수 있도록 Apple ID를 제공해야 합니다. 또한 iOS 설정 메뉴에서 설정을 완료한 후에 ID를 제공할 수도 있습니다.

3. 설정을 완료한 후 iOS 장치에서 앱 스토어를 통해 회사 포털 앱을 설치해야 합니다.

4. 이제 장치를 설정할 때 사용한 UPN을 사용하여 회사 포털에 로그인할 수 있습니다.

5. 로그인한 후에는 장치를 등록하라는 메시지가 표시됩니다. 첫 번째 단계는 장치를 식별하는 것입니다. 앱에서 이미 회사에 등록되어 사용자의 Intune 계정에 할당된 iOS 장치 목록을 표시합니다. 일치하는 장치를 선택해야 합니다.

   이 장치가 아직 회사에 등록되지 않은 경우 **새 장치**를 선택하여 표준 등록 흐름에 따라 계속 진행해야 합니다.

6. 다음 화면에서 새 장치의 일련 번호를 확인해야 합니다. 사용자는 **일련 번호 확인** 링크를 탭하여 설정 앱을 통해 일련 번호를 확인하는 지침을 시작할 수 있습니다. 그런 다음 회사 포털 앱에 일련 번호의 마지막 4자리를 입력해야 합니다.

   이 단계에서는 장치가 Intune에 등록된 회사 장치인지 확인합니다. 장치의 일련 번호와 일치하지 않으면 잘못된 장치를 선택한 것입니다. 이전 화면으로 돌아가서 다른 장치를 선택해야 합니다.

7. 일련 번호를 확인한 후 회사 포털 앱에서 회사 포털 웹 사이트로 리디렉션하여 등록을 마칩니다. 그런 다음 웹 사이트에서 앱으로 돌아가라는 메시지를 표시합니다.

8. 이제 등록이 완료됩니다. 이제 사용자는 이 장치에서 전체 기능을 사용할 수 있습니다.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>사용자 선호도가 없는, 회사에서 소유하는 관리 장치 정보

사용자 선호도 없음으로 구성된 장치에서는 회사 포털을 지원하지 않으므로 앱을 설치하지 않아야 합니다. 회사 포털은 회사 자격 증명을 갖고 있으며 개인 설정된 회사 리소스(예: 메일)에 대한 액세스 권한이 필요한 사용자를 위해 설계되었습니다. 사용자 선호도 없음으로 등록된 장치의 경우에는 전용 사용자가 로그인할 필요가 없습니다. 키오스크, POS(Point of Sale), 공유 유틸리티 장치 등이 사용자 선호도 없음으로 등록된 장치의 일반적인 사용 사례입니다.

사용자 선호도가 필요한 경우 장치를 등록하기 전에 장치의 등록 프로필에서 **사용자 선호도**가 선택되어 있어야 합니다. 장치에서 선호도 상태를 변경하려면 장치를 사용 중지한 후 다시 등록해야 합니다.



### <a name="see-also"></a>참고 항목
[Microsoft Intune에서 장치 등록을 위한 필수 구성 요소](prerequisites-for-enrollment.md)
