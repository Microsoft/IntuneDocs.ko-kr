---
title: Microsoft Intune에서 iOS/iPadOS 디바이스 등록 문제 해결
titleSuffix: Microsoft Intune
description: Intune에서 iOS/iPadOS 디바이스를 등록할 때 가장 일반적인 문제 중 일부에 대한 문제를 해결하기 위한 제안입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a29fab4be6e2046b2c6757505001a7ba3455b8d6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514322"
---
# <a name="troubleshoot-iosipados-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune에서 iOS/iPadOS 디바이스 등록 문제 해결

이 문서는 Intune 관리자가 Intune에서 iOS/iPadOS 디바이스를 등록할 때 나타나는 문제들을 이해하고 해결하는 데 도움이 됩니다.

## <a name="prerequisites"></a>전제 조건

문제 해결을 시작하기 전에 몇 가지 기본적인 정보를 수집하는 것이 중요합니다. 이 정보를 통해 문제를 보다 잘 이해하고 해결 시간을 단축하는데 도움을 얻을 수 있습니다.

문제에 대한 다음 정보를 수집합니다.

- 정확한 오류 메시지가 무엇입니까?
- 어디서 오류 메시지가 표시됩니까?
- 문제가 언제 시작되었습니까? 등록이 실행되었습니까?
- 어떤 플랫폼(Android, iOS/iPadOS, Windows)에 문제가 있습니까?
- 얼마나 많은 사용자가 영향을 받습니까? 영향을 받는 사용자는 전체입니까, 아니면 일부입니까?
- 영향을 받은 디바이스는 얼마나 됩니까? 영향을 받는 디바이스는 전체입니까, 아니면 일부입니까?
- MDM 기관이란 무엇입니까?
- 등록은 어떻게 진행됩니까? BYOD(Bring Your Own Device)와 등록 프로필이 포함된 Apple DEP(디바이스 등록 프로그램) 중 무엇을 사용합니까?

## <a name="error-messages"></a>오류 메시지

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>프로필 설치 실패. 네트워크 오류가 발생했습니다.

**원인:** 디바이스에서 iOS/iPadOS에 대해 불특정한 문제가 발생했습니다.

#### <a name="resolution"></a>해결 방법

1. 다음 단계에서 데이터 손실(iOS/iPadOS 복원 시 디바이스에서 모든 데이터를 삭제)을 방지하려면 데이터를 백업해야 합니다.
2. 디바이스를 복구 모드로 전환한 후 복원합니다. 디바이스를 새 디바이스로 설정했는지 확인합니다. iOS/iPadOS 디바이스를 복원하는 방법에 대한 자세한 내용은 [https://support.apple.com/HT201263](https://support.apple.com/HT201263)을 참조하세요.
3. 디바이스 다시 등록.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>프로필 설치 실패. 서버에 대한 연결을 설정할 수 없습니다.

**원인:** Intune 테넌트가 회사 소유의 디바이스만 허용하도록 구성되어 있습니다. 

#### <a name="resolution"></a>해결 방법
1. Azure Portal에 로그인합니다.
2. **추가 서비스**를 선택하고 Intune을 검색한 다음, **Intune**을 선택합니다.
3. **디바이스 등록** > **등록 제한**을 선택합니다.
4. **디바이스 유형 제한**에서 설정하려는 제한을 선택하고 **속성** > **플랫폼 선택** > **iOS**에 대해 **허용**을 차례대로 선택한 다음, **확인**을 클릭합니다.
5. **플랫폼 구성**을 선택하고 개인적으로 소유한 iOS/iPadOS 디바이스에 대해 **허용**을 선택한 다음, **확인**을 클릭합니다.
6. 디바이스 다시 등록.

**원인:** DNS에 필요한 CNAME 레코드가 없습니다.

#### <a name="resolution"></a>해결 방법
회사의 도메인에 대한 CNAME DNS 리소스 레코드를 만듭니다. 예를 들어 회사의 도메인이 contoso.com인 경우 DNS에 EnterpriseEnrollment.contoso.com을 EnterpriseEnrollment-s.manage.microsoft.com으로 리디렉션하는 CNAME을 만듭니다.

CNAME DNS 항목을 만드는 것은 선택 사항이지만 CNAME 레코드를 사용하면 사용자가 보다 쉽게 등록할 수 있습니다. 등록 CNAME 레코드가 없으면 사용자에게 MDM 서버 이름인 enrollment.manage.microsoft.com을 수동으로 입력하라는 메시지가 표시됩니다.

확인된 도메인이 둘 이상 있는 경우 각 도메인에 대해 CNAME 레코드를 만듭니다. CNAME 리소스 레코드에는 다음 정보가 포함되어야 합니다.

|유형|호스트 이름|지시 대상|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|1시간|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1시간|

회사에서 사용자 자격 증명에 여러 도메인을 사용하는 경우 각 도메인용으로 CNAME 레코드를 만듭니다.

> [!NOTE]
> DNS 레코드 변경 내용이 전파되는 데는 최대 72시간이 걸릴 수 있습니다. DNS 레코드가 전파될 때까지 Intune에서 DNS 변경 내용을 확인할 수 없습니다.

**원인:** 이전에 다른 사용자 계정에 등록된 디바이스를 등록하고 있으며, 이전 사용자가 Intune에서 적절하게 제거되지 않았습니다.

#### <a name="resolution"></a>해결 방법
1. 현재 프로필 설치를 취소합니다.
2. Safari에서 [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)을 엽니다.
3. 디바이스 다시 등록.

> [!NOTE]
> 등록이 여전히 실패할 경우, Safari(쿠키 차단 안 함)에서 쿠키를 제거하고 디바이스를 다시 등록합니다.

**원인:** 디바이스가 다른 MDM 공급자에 이미 등록되어 있습니다.

#### <a name="resolution"></a>해결 방법
1. iOS/iPadOS 디바이스에서 **설정**을 열고 **일반 > 디바이스 관리**로 이동합니다.
2. 기존 관리 프로필을 제거합니다.
3. 디바이스 다시 등록.

**원인:** 디바이스를 등록하려는 사용자에게 Microsoft Intune 라이선스가 없습니다.

#### <a name="resolution"></a>해결 방법
1. [Office 365 관리 센터](https://portal.office.com/adminportal/home#/homepage)로 이동한 다음, **사용자 > 활성 사용자**를 선택합니다.
2. Intune 사용자 라이선스를 할당할 사용자 계정을 선택한 후 **제품 라이선스 > 편집**을 선택합니다.
3. 이 사용자에게 할당하려는 라이선스에 대해 설정/해제 단추를 **On** 위치로 전환한 후 **저장**을 선택합니다.
4. 디바이스 다시 등록.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>이 서비스는 지원되지 않습니다. 등록 정책 없음.

**원인**: Apple MDM 푸시 인증서가 Intune에 구성되어 있지 않거나 인증서가 유효하지 않습니다. 

#### <a name="resolution"></a>해결 방법

- MDM 푸시 인증서가 구성되지 않은 경우, [Apple MDM 푸시 인증서 가져오기](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate)의 단계를 수행합니다.
- MDM 푸시 인증서가 유효하지 않은 경우, [Apple MDM 푸시 인증서 갱신](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)의 단계를 수행합니다.

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>회사 포털을 일시적으로 사용할 수 없음. 회사 포털 앱에서 문제가 발생했습니다. 문제가 계속되면 시스템 관리자에게 문의하세요.

**원인:** 회사 포털 앱이 만료되었거나 손상되었습니다.

#### <a name="resolution"></a>해결 방법
1. 디바이스에서 회사 포털 앱을 제거합니다.
2. **App Store**에서 **Microsoft Intune 회사 포털** 앱을 다운로드하고 설치합니다.
3. 디바이스 다시 등록.
 > [!NOTE]
    > 사용자가 디바이스 등록 구성 시 허용한 수량보다 더 많은 디바이스를 등록하려는 경우에도 이러한 오류가 발생할 수 있습니다. 이러한 단계를 수행해도 문제가 해결되지 않는다면 아래의 **디바이스 최댓값 도달**에 대한 해결 단계를 수행합니다.

### <a name="device-cap-reached"></a>디바이스 최댓값 도달

**원인:** 사용자가 디바이스 등록 한도보다 더 많은 디바이스를 등록하려고 합니다.

#### <a name="resolution"></a>해결 방법
1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **모든 디바이스**를 선택한 후 사용자가 등록한 디바이스의 수를 확인합니다.
    > [!NOTE]
    > 또한 [Intune 사용자 포털](https://portal.manage.microsoft.com/)에 대해서는 영향을 받은 사용자 로그온이 있어야 하며 등록된 디바이스를 확인해야 합니다. [Intune 사용자 포털](https://portal.manage.microsoft.com/)에는 표시되지만 [Intune 관리 포털](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)에는 표시되지 않는 디바이스가 존재할 수 있습니다. 이러한 디바이스도 디바이스 등록 제한에 포함됩니다.
2. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **등록 제한**을 선택한 후, 디바이스 등록 제한을 확인합니다. 기본적으로 제한은 15입니다. 
3. 등록된 디바이스의 수가 한도에 도달하면 불필요한 디바이스를 제거하거나 디바이스 등록 한도를 늘립니다. 등록된 모든 디바이스에서 Intune 라이선스를 사용하기 때문에 항상 불필요한 디바이스부터 먼저 제거하는 것이 좋습니다.
4. 디바이스 다시 등록.

### <a name="workplace-join-failed"></a>Workplace Join 실패

**원인:** 회사 포털 앱이 만료되었거나 손상되었습니다.  

#### <a name="resolution"></a>해결 방법
1. 디바이스에서 회사 포털 앱을 제거합니다.
2. **App Store**에서 **Microsoft Intune 회사 포털** 앱을 다운로드하고 설치합니다.
3. 디바이스 다시 등록.

### <a name="user-license-type-invalid"></a>사용자 라이선스 형식이 잘못됨

**원인:** 디바이스를 등록하려는 사용자에게 유효한 Intune 라이선스가 없습니다.

#### <a name="resolution"></a>해결 방법
1. [Microsoft 365 관리 센터](https://portal.office.com/adminportal/home#/homepage)로 이동한 다음, **사용자** > **활성 사용자**를 선택합니다.
2. 영향을 받는 사용자 계정 > **제품 라이선스** > **편집**을 차례대로 선택합니다.
3. 이 사용자에게 유효한 Intune 라이선스가 할당되어 있는지 확인합니다.
4. 디바이스 다시 등록.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>사용자 이름을 인식할 수 없습니다. 이 사용자 계정에는 Microsoft Intune을 사용할 수 있는 권한이 없습니다. 오류가 발생하여 이 메시지를 수신했다고 판단된다면 시스템 관리자에게 문의하세요.

**원인:** 디바이스를 등록하려는 사용자에게 유효한 Intune 라이선스가 없습니다.

1. [Microsoft 365 관리 센터](https://portal.office.com/adminportal/home#/homepage)로 이동한 다음, **사용자** > **활성 사용자**를 선택합니다.
2. 영향을 받는 사용자 계정을 선택한 다음, **제품 라이선스** > **편집**을 선택합니다.
3. 이 사용자에게 유효한 Intune 라이선스가 할당되어 있는지 확인합니다.
4. 디바이스 다시 등록.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>프로필 설치 실패. 새 MDM 페이로드가 이전 페이로드와 일치하지 않습니다.

**원인:** 관리 프로필이 디바이스에 이미 설치되어 있습니다.

#### <a name="resolution"></a>해결 방법

1. iOS/iPadOS 디바이스에서 **설정**을 열고 **일반** > **디바이스 관리**로 이동합니다.
2. 기존 관리 프로필을 탭한 후, **관리 제거**를 탭합니다.
3. 디바이스 다시 등록.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**원인:** APNs(Apple Push Notification Service) 인증서가 없거나 잘못되었거나 만료되었습니다.

#### <a name="resolution"></a>해결 방법
유효한 APNs 인증서가 Intune에 추가되었는지 확인합니다. 자세한 내용은 [iOS/iPadOS 등록 설정](ios-enroll.md)을 참조하세요.

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**원인:** Intune에서 구성된 APNs(Apple Push Notification Service) 인증서에 문제가 있습니다.

#### <a name="resolution"></a>해결 방법
APNs 인증서를 갱신하고 디바이스를 다시 등록합니다.

> [!IMPORTANT]
> APNs 인증서를 갱신해야 합니다. APNs 인증서를 교체하지 마세요. 인증서를 교체하는 경우, Intune에서 모든 iOS/iPadOS 디바이스를 다시 등록해야 합니다. 

- Intune 독립 실행형에서 APNs 인증서를 갱신하려면 [Apple MDM 푸시 인증서 갱신](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)을 참조하세요.
- Office 365에서 APNs 인증서를 갱신하려면 [iOS/iPadOS 디바이스에 대한 APNs 인증서 만들기](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7)를 참조하세요.

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR 연결이 잘못됨

등록 프로필이 할당된 DEP 관리 디바이스를 켜면 등록은 실패하며 다음과 같은 오류 메시지가 표시됩니다.

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**원인:** 디바이스와 Apple DEP 서비스 간의 연결 문제가 있습니다.

#### <a name="resolution"></a>해결 방법
연결 문제를 해결하거나 다른 네트워크 연결을 사용하여 디바이스를 등록하세요. 문제가 지속되면 Apple에 문의해야 할 수도 있습니다.


## <a name="other-issues"></a>기타 문제

### <a name="dep-enrollment-doesnt-start"></a>DEP 등록이 시작되지 않음
등록 프로필이 할당된 DEP 관리 디바이스를 켜면 Intune 등록 프로세스가 시작되지 않습니다.

**원인:** DEP 토큰을 Intune에 업로드하기 전에 등록 프로필이 생성됩니다.

#### <a name="resolution"></a>해결 방법

1. 등록 프로필을 편집합니다. 프로필을 변경할 수 있습니다. 그 목적은 프로필의 수정 시간을 업데이트하는 데 있습니다.
2. 다음과 같이 DEP 관리 디바이스를 동기화합니다. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스** > **iOS** > **iOS 등록** > **등록 프로그램 토큰**을 선택하고 토큰을 선택한 후 **지금 동기화**를 선택합니다. 동기화 요청이 Apple에 전송됩니다.

### <a name="dep-enrollment-stuck-at-user-login"></a>사용자 로그인 시 DEP 등록 중단
등록 프로필이 할당된 DEP 관리 디바이스를 켜면 자격 증명을 입력한 후 초기 설정이 중단됩니다.

**원인:** 다단계 인증(MFA)을 사용하도록 설정되어 있습니다. 현재 MFA는 DEP 디바이스에서 등록을 진행하는 동안 작동하지 않습니다.

#### <a name="resolution"></a>해결 방법
MFA를 사용하지 않도록 설정한 다음, 디바이스를 다시 등록합니다.


## <a name="next-steps"></a>다음 단계

- [Intune에서 디바이스 등록 문제 해결](../troubleshoot-device-enrollment-in-intune.md)
- [Intune 포럼에서 질문하기](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Microsoft Intune 지원 팀 블로그 보기](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Microsoft Enterprise Mobility + Security 블로그 보기](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
