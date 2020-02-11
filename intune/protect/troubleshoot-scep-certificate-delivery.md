---
title: Microsoft Intune에서 SCEP를 사용할 때 디바이스에 대한 인증서 배달 문제 해결 | Microsoft Docs
description: Intune에 SCEP 인증서 프로필을 사용하여 인증서를 배포할 때 CA에서 디바이스로의 인증서 배달 문제를 해결합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77be59d126dc7e73bee468ca938938c6bb1b2e1a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915878"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>Microsoft Intune에서 SCEP에 의해 디바이스로 프로비전되는 인증서의 배달 문제 해결

이 문서의 정보는 SCEP(단순 인증서 등록 프로토콜)를 사용하여 Intune에서 인증서를 프로비전할 때 디바이스에 대한 인증서 배달을 조사하는 데 도움이 됩니다. NDES(네트워크 장치 등록 서비스) 서버는 CA(인증 기관)에서 디바이스에 대해 요청된 인증서를 받은 후 해당 인증서를 디바이스에 다시 전달합니다.

이 문서는 [SCEP 통신 워크플로](troubleshoot-scep-certificate-profiles.md)의 5단계인 인증서 요청을 제출한 디바이스에 대한 인증서 배달에 적용됩니다.

## <a name="review-the-certification-authority"></a>인증 기관 검토

CA가 인증서를 발급하면 CA에서 다음 예와 유사한 항목이 표시됩니다.

![발급된 인증서의 예](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>디바이스 검토

### <a name="android"></a>Android

장치 관리자 등록 디바이스의 경우 인증서를 설치 하라는 메시지를 표시하는 다음 이미지와 유사한 알림이 표시됩니다.

![Android 알림](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

Android Enterprise 또는 Samsung Knox의 경우 인증서가 자동으로 설치됩니다.

Android에서 설치된 인증서를 보려면 타사 인증서 보기 앱을 사용합니다.

[디바이스 OMADM 로그](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)를 검토할 수도 있습니다. 인증서가 설치될 때 기록되는 다음과 유사한 항목을 찾습니다.

**루트 인증서**:

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**SCEP를 통해 프로비전된 인증서**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="ios-and-ipados"></a>iOS 및 iPadOS

iOS 또는 iPadOS 디바이스에서는 장치 관리 프로필 아래에서 인증서를 볼 수 있습니다. 설치된 인증서의 세부 정보를 보려면 드릴인합니다.

![iOS 인증서](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

[iOS 디버그 로그](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)에서 다음과 유사한 항목을 찾을 수도 있습니다.

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

Windows 디바이스에서 인증서가 배달되었는지 확인합니다.

- **eventvwr.msc**를 실행하여 이벤트 뷰어를 엽니다. **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**으로 이동하여 **이벤트 39**를 찾습니다. 이 이벤트의 일반적 설명은 다음과 같아야 합니다. **SCEP: 인증서가 설치되었습니다.**

   ![Windows 응용 프로그램 로그의 이벤트 39](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

디바이스에서 인증서를 보려면 **certmgr.exe**를 실행하여 인증서 MMC를 열고 개인 저장소에서 루트 및 SCEP 인증서가 디바이스에 제대로 설치되어 있는지 확인합니다.

   1. **인증서(로컬 컴퓨터)**  > **신뢰할 수 있는 루트 인증 기관** > **인증서**로 이동하여 CA의 루트 인증서가 있는지 확인합니다. *발급 대상* 값과 *발급자* 값이 동일합니다.
   2. 인증서 MMC에서 **인증서 – 현재 사용자** > **개인** > **인증서**로 이동하여 CA 이름과 동일한 *발급자*로 요청된 인증서가 있는지 확인합니다.

## <a name="troubleshoot-failures"></a>오류 문제 해결

### <a name="android"></a>Android

이 단계의 문제를 해결하려면 OMA DM 로그에 기록된 오류를 검토합니다.

### <a name="ios-and-ipados"></a>iOS 및 iPadOS

이 단계의 문제를 해결하려면 디바이스 디버그 로그에 기록된 오류를 검토합니다.

### <a name="windows"></a>Windows

디바이스에 설치되지 않은 인증서와 관련된 문제를 해결하려면 Windows 이벤트 로그에서 문제를 나타내는 오류를 찾습니다.

- 디바이스에서 **eventvwr.msc**를 실행하여 이벤트 뷰어를 연 다음 **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**으로 이동합니다.

디바이스에 대한 인증서 배달 및 설치 오류는 일반적으로 Intune이 아니라 Windows 작업과 관련됩니다.

## <a name="next-steps"></a>다음 단계

인증서가 디바이스에 성공적으로 배포되었지만 Intune에서 성공 여부를 보고하지 않는 경우 [Intune에 NDES 보고](troubleshoot-scep-certificate-reporting.md)를 참조하여 보고 문제를 해결합니다.
