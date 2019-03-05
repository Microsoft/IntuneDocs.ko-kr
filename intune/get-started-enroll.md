---
title: IOS 디바이스 등록 경험 이해
titlesuffix: Microsoft Intune
description: iOS 디바이스의 전체 등록 과정을 안내하여 등록 과정을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 376d00a03feb78b4e66b3f8a4ed15567d3bc7976
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230281"
---
# <a name="understand-the-users-experience-enrolling-an-ios-device"></a>IOS 디바이스를 등록하는 사용자의 경험 이해

Microsoft Intune을 사용하면 회사 데이터 보호를 유지하면서 직원들이 모바일 디바이스를 이용할 수 있습니다. 최종 사용자는 관리 콘솔보다 해당 디바이스에서 Intune을 조작하기 때문에 등록 환경을 숙지하는 것이 좋습니다. 그러면 잘 작성된 준수 정책과 경험을 결합하여 사용자에 대한 공감을 표시할 수 있습니다. 이는 특히 관리자가 볼 수 있는 정보를 사용자가 정확히 알게 되기 때문에 중요합니다.

| IT 부서에서 볼 수 없는 사항 | IT 부서에서 볼 수 있는 사항 |
|---|---|
| 호출 및 웹 검색 기록 | 모델 |
| 위치 | 일련 번호 |
| 개인 메일 | 운영 체제 버전 |
| 문자 메시지 | 앱 이름 |
| 연락처 | Owner |
| 개인 계정의 암호 | 디바이스 이름 |
| 일정 이벤트 | (Apple에서 제조되지 않은 디바이스의) 제조업체 |
| 사진 앱 또는 카메라 앨범에 있는 사진을 비롯한 사진 | 전화 번호(업무용 디바이스의 경우 전체 번호, 개인 디바이스의 경우 마지막 4자리만) |

## <a name="how-do-i-enroll-a-device"></a>디바이스를 등록하려면 어떻게 하나요?

디바이스 등록은 많은 최종 사용자가 회사 리소스에 액세스할 때 얻게 되는 첫 번째 경험입니다. [해당 경험을 이해](end-user-educate.md)하면 불쾌할 수 있는 경험을 개선할 수 있습니다.

1. **앱 스토어**를 열고 **intune 회사 포털**을 검색합니다.
2. **Microsoft Intune 회사 포털** 앱을 다운로드합니다.
3. **회사 포털** 앱을 열고 테스트 사용자의 메일 주소와 암호를 입력한 다음 **로그인**을 탭합니다.
4. 임시 암호를 새 암호로 업데이트합니다.
5. **회사 액세스 설정** 페이지에서 **디바이스 등록**을 탭합니다.
6. **왜 디바이스를 등록하나요?** 페이지에서 사용자가 디바이스를 등록할 때 수행할 수 있는 작업을 확인하고 **계속**을 탭합니다.
7. 등록 시 사용자에게 부여되는 액세스 권한 목록을 검토한 다음 **계속**을 탭합니다.
8. IT 관리자가 디바이스에서 볼 수 있는 정보와 볼 수 없는 정보를 검토한 다음 **계속**을 탭합니다.
9. **다음 단계는?** 페이지에서 등록하는 동안 발생하는 상황을 확인하고 **등록**을 탭합니다.
10. **프로필 설치** 페이지에서 **설치**를 탭한 다음 메시지가 표시되면 디바이스 암호를 입력합니다.
11. **설치**를 탭합니다.
12. **설치**를 다시 탭하여 경고를 읽었음을 나타냅니다.
13. **경고** 팝업에서 **신뢰**를 탭합니다.
14. 프로필 설치를 완료했다고 표시하도록 화면이 변경되면 **완료**를 탭합니다.
15. "디바이스 등록 중" 메시지가 화면에 표시된 후 디바이스가 성공적으로 등록되었음을 보여 줍니다. 회사 포털에서 페이지를 열라는 팝업이 표시됩니다. **열기**를 탭합니다.
16. **회사 액세스 설정** 화면으로 돌아갑니다. 테스트 정책이 설정되어 있지 않으면 디바이스가 규격으로 표시됩니다. 테스트 정책이 있는 경우 **디바이스 준수**를 탭하면 디바이스의 보안 유지를 위해 수행해야 하는 작업이 있다고 표시됩니다.

## <a name="next-steps"></a>다음 단계

[앱 추가 시작](get-started-apps.md) - 앱을 찾고 디바이스에 추가하여 직원이 작업을 수행할 수 있게 합니다.

## <a name="learn-more"></a>자세한 정보

* [Intune 등록 옵션](enrollment-options.md)
* [Intune으로 Bring Your Own Device를 사용하도록 설정](byod-enable.md)
* [등록 및 디바이스 관리에 대해 최종 사용자 교육](end-user-educate.md)
