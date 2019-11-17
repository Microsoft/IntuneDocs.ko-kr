---
title: Microsoft Intune에서 iOS 디바이스 등록 문제 해결
titleSuffix: Microsoft Intune
description: Intune에서 iOS 장치를 등록할 때 가장 일반적인 문제 중 일부에 대 한 문제 해결에 대 한 제안입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/25/2019
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
ms.openlocfilehash: 03ceaf5493f544dbb815146eb67c3fae8856d29e
ms.sourcegitcommit: 5c52879f3653e22bfeba4eef65e2c86025534dab
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74126140"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune에서 iOS 디바이스 등록 문제 해결

이 문서는 intune 관리자가 Intune에서 iOS 장치를 등록할 때의 문제를 이해 하 고 해결 하는 데 도움이 됩니다

## <a name="prerequisites"></a>전제 조건

문제 해결을 시작 하기 전에 몇 가지 기본적인 정보를 수집 하는 것이 중요 합니다. 이 정보를 통해 문제를 보다 잘 이해 하 고 해결 시간을 단축할 수 있습니다.

문제에 대 한 다음 정보를 수집 합니다.

- 정확한 오류 메시지가 무엇입니까?
- 어디서 오류 메시지가 표시됩니까?
- 문제가 언제 시작되었습니까? 등록이 작동 했습니까?
- 어떤 플랫폼 (Android, iOS, Windows)에 문제가 있나요?
- 영향을 받는 사용자는 몇 개입니까? 모든 사용자에 게 영향을 미치는지 아니면 일부에만 적용 되나요?
- 영향을 받는 장치는 몇 개입니까? 모든 장치가 영향을 받는지 아니면 일부 입니까?
- MDM 기관 이란? System Center Configuration Manager 경우 사용 중인 Configuration Manager 버전은 무엇 인가요?
- 등록을 수행 하는 방법 등록 프로필을 사용 하 여 BYOD (사용자 소유의 장치) 또는 DEP (Apple 장비 등록 프로그램)를 사용 하나요?

## <a name="error-messages"></a>오류 메시지

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>프로필 설치 실패. 네트워크 오류가 발생했습니다.

**원인:** 장치에서 iOS에 대 한 알 수 없는 문제가 발생 했습니다.

#### <a name="resolution"></a>해결 방법

1. 다음 단계에서 데이터 손실을 방지 하려면 (iOS 복원은 장치의 모든 데이터를 삭제 함) 데이터를 백업 해야 합니다.
2. 장치를 복구 모드로 전환 하 고 복원 합니다. 새 장치로 설정 했는지 확인 합니다. IOS 장치를 복원 하는 방법에 대 한 자세한 내용은 [https://support.apple.com/HT201263](https://support.apple.com/HT201263)를 참조 하세요.
3. 디바이스 다시 등록.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>프로필 설치 실패. 서버에 대한 연결을 설정할 수 없습니다.

**원인:** Intune 테 넌 트가 회사 소유의 장치만 허용 하도록 구성 되어 있습니다. 

#### <a name="resolution"></a>해결 방법
1. Azure Portal에 로그인합니다.
2. **추가 서비스**를 선택하고 Intune을 검색한 다음, **Intune**을 선택합니다.
3. **디바이스 등록** > **등록 제한**을 선택합니다.
4. **장치 유형 제한**에서 **속성** > 설정 하려는 제한을 선택 하  > **플랫폼** 을 선택 하 > **iOS**에 대해 **허용** 을 선택 하 고 **확인**을 클릭 합니다.
5. **플랫폼 구성**을 선택 하 고 개인적으로 소유한 iOS 장치에 대해 **허용** 을 선택한 다음 **확인**을 클릭 합니다.
6. 디바이스 다시 등록.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>이 서비스는 지원 되지 않습니다. 등록 정책 없음.

**원인**: Apple MDM push Certificate가 Intune에 구성 되어 있지 않거나 인증서가 유효 하지 않습니다. 

#### <a name="resolution"></a>해결 방법

- MDM 푸시 인증서가 구성 되지 않은 경우 [APPLE mdm push Certificate 가져오기](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate)의 단계를 따릅니다.
- MDM 푸시 인증서가 유효 하지 않은 경우 [APPLE mdm push Certificate 갱신](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)의 단계를 따릅니다.

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>회사 포털을 일시적으로 사용할 수 없음. 회사 포털 앱에서 문제가 발생 했습니다. 문제가 계속되면 시스템 관리자에게 문의하세요.

**원인:** 회사 포털 앱이 만료 되었거나 손상 되었습니다.

#### <a name="resolution"></a>해결 방법
1. 디바이스에서 회사 포털 앱을 제거합니다.
2. **App Store**에서 **Microsoft Intune 회사 포털** 앱을 다운로드하고 설치합니다.
3. 디바이스 다시 등록.
 > [!NOTE]
    > 사용자가 장치 등록을 허용 하도록 구성 된 것 보다 많은 장치를 등록 하려고 하는 경우에도이 오류가 발생할 수 있습니다. 이러한 단계를 수행 해도 문제가 해결 되지 않으면 아래 **에 있는 장치 상한** 에 대 한 해결 단계를 따르세요.

### <a name="device-cap-reached"></a>디바이스 최댓값 도달

**원인:** 사용자가 장치 등록 제한 보다 더 많은 장치를 등록 하려고 합니다.

#### <a name="resolution"></a>해결 방법
1. **모든 장치** >  [Intune 관리 포털](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)  >  열고 사용자가 등록**한 장치의 수** 를 확인 합니다.
    > [!NOTE]
    > 또한 [Intune 사용자 포털](https://portal.manage.microsoft.com/) 에 영향을 받는 사용자 로그온이 있어야 하 고 등록 된 장치를 확인 해야 합니다. Intune [사용자 포털](https://portal.manage.microsoft.com/) 에는 표시 되지만 [intune 관리 포털](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)에는 표시 되지 않는 장치가 있을 수 있습니다. 이러한 장치는 장치 등록 제한에도 해당 합니다.
2. **관리자**  > **모바일 장치 관리**  > **등록 규칙** 으로 이동 하 > 장치 등록 제한을 확인 합니다. 기본적으로 제한은 15입니다. 
3. 등록 된 장치의 수가 한도에 도달 하면 불필요 한 장치를 제거 하거나 장치 등록 제한을 늘립니다. 등록 된 모든 장치에서 Intune 라이선스를 사용 하기 때문에 항상 불필요 한 장치를 먼저 제거 하는 것이 좋습니다.
4. 디바이스 다시 등록.

### <a name="workplace-join-failed"></a>Workplace Join 실패

**원인:** 회사 포털 앱이 만료 되었거나 손상 되었습니다.  

#### <a name="resolution"></a>해결 방법
1. 디바이스에서 회사 포털 앱을 제거합니다.
2. **App Store**에서 **Microsoft Intune 회사 포털** 앱을 다운로드하고 설치합니다.
3. 디바이스 다시 등록.

### <a name="user-license-type-invalid"></a>사용자 라이선스 유형이 잘못 되었습니다.

**원인:** 장치를 등록 하려고 하는 사용자에 게 유효한 Intune 라이선스가 없습니다.

#### <a name="resolution"></a>해결 방법
1. [Microsoft 365 관리 센터](https://portal.office.com/adminportal/home#/homepage)로 이동한 다음 **사용자**  > **활성 사용자**를 선택 합니다.
2. 영향을 받는 사용자 계정 > **제품 라이선스**  > **편집**을 선택 합니다.
3. 이 사용자에 게 유효한 Intune 라이선스가 할당 되어 있는지 확인 하십시오.
4. 디바이스 다시 등록.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>사용자 이름을 인식할 수 없습니다. 이 사용자 계정에는 Microsoft Intune을 사용할 수 있는 권한이 없습니다. 오류가 발생 하 여이 메시지를 받은 경우 시스템 관리자에 게 문의 하십시오.

**원인:** 장치를 등록 하려고 하는 사용자에 게 유효한 Intune 라이선스가 없습니다.

1. [Microsoft 365 관리 센터](https://portal.office.com/adminportal/home#/homepage)로 이동한 다음 **사용자**  > **활성 사용자**를 선택 합니다.
2. 영향을 받는 사용자 계정을 선택한 다음 **제품 라이선스**  > **편집**을 선택 합니다.
3. 이 사용자에 게 유효한 Intune 라이선스가 할당 되어 있는지 확인 하십시오.
4. 디바이스 다시 등록.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>프로필 설치 실패. 새 MDM 페이로드가 이전 페이로드와 일치 하지 않습니다.

**원인:** 관리 프로필이 장치에 이미 설치 되어 있습니다.

#### <a name="resolution"></a>해결 방법

1. IOS 장치에서 **설정** > **일반**  > **장치 관리**를 엽니다.
2. 기존 관리 프로필을 탭 하 고 **관리 제거**를 탭 합니다.
3. 디바이스 다시 등록.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**원인:** APNs (Apple Push Notification Service) 인증서가 없거나 잘못 되었거나 만료 되었습니다.

#### <a name="resolution"></a>해결 방법
유효한 APNs 인증서가 Intune에 추가 되었는지 확인 합니다. 자세한 내용은 [iOS 및 Mac 디바이스 관리 설정](https://docs.microsoft.com/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)을 참조하세요. 

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**원인:** Intune에서 구성 된 APNs (Apple Push Notification service) 인증서에 문제가 있습니다.

#### <a name="resolution"></a>해결 방법
APNs 인증서를 갱신 하 고 장치를 다시 등록 합니다.

> [!IMPORTANT]
> APNs 인증서를 갱신 해야 합니다. APNs 인증서를 바꾸지 마세요. 인증서를 교체 하는 경우 Intune에서 모든 iOS 장치를 다시 등록 해야 합니다. 

- Intune 독립 실행형에서 APNs 인증서를 갱신 하려면 [APPLE MDM push Certificate 갱신](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)을 참조 하세요.
- Configuration Manager를 사용 하 여 Intune 하이브리드에서 APNs 인증서를 갱신 하려면 [System Center Configuration Manager 및 Microsoft Intune를 사용 하 여 iOS 하이브리드 장치 관리 설정](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)을 참조 하세요.
- Office 365에서 APNs 인증서를 갱신 하려면 [iOS 장치용 Apns 인증서 만들기](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7)를 참조 하세요.

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR 연결이 잘못 되었습니다.

등록 프로필이 할당 된 DEP 관리 장치를 켜면 등록이 실패 하 고 다음과 같은 오류 메시지가 표시 됩니다.

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**원인:** 장치와 Apple DEP 서비스 간의 연결 문제가 있습니다.

#### <a name="resolution"></a>해결 방법
연결 문제를 해결 하거나 다른 네트워크 연결을 사용 하 여 장치를 등록 하십시오. 문제가 지속 되 면 Apple에 문의 해야 할 수도 있습니다.


## <a name="other-issues"></a>기타 문제

### <a name="dep-enrollment-doesnt-start"></a>DEP 등록이 시작 되지 않음
등록 프로필이 할당 된 DEP 관리 장치를 켜면 Intune 등록 프로세스가 시작 되지 않습니다.

**원인:** DEP 토큰을 Intune에 업로드 하기 전에 등록 프로필이 생성 됩니다.

#### <a name="resolution"></a>해결 방법

1. 등록 프로필을 편집 합니다. 프로필을 변경할 수 있습니다. 용도는 프로필의 수정 시간을 업데이트 하는 것입니다.
2. DEP 관리 장치 동기화: Intune 포털 > **Admin**  > **모바일 장치 관리**  > **iOS**  > **장비 등록 프로그램** **지금 동기화**를 엽니다. 동기화 요청이 Apple에 전송됩니다.

### <a name="dep-enrollment-stuck-at-user-login"></a>사용자 로그인 시 DEP 등록 중단
등록 프로필을 할당 하는 DEP 관리 장치를 켜면 자격 증명을 입력 한 후 초기 설치가 시작 됩니다.

**원인:** MFA (multi-factor authentication)를 사용 하도록 설정 합니다. 현재 MFA는 DEP 장치에 등록 하는 동안 작동 하지 않습니다.

#### <a name="resolution"></a>해결 방법
MFA를 사용 하지 않도록 설정 하 고 장치를 다시 등록 합니다.

## <a name="next-steps"></a>다음 단계

- [Intune에서 디바이스 등록 문제 해결](../troubleshoot-device-enrollment-in-intune.md)
- [Intune 포럼에서 질문하기](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Microsoft Intune 지원 팀 블로그를 확인 하세요.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Microsoft Enterprise Mobility 및 보안 블로그 확인](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
