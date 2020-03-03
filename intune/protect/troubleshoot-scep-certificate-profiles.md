---
title: SCEP 인증서 프로필을 사용하여 Microsoft Intune으로 인증서를 프로비전하는 문제 해결 | Microsoft Docs
description: 디바이스와 NDES의 통신, NDES와 인증 기관의 통신, Intune Certificate Connector와 Intune 서비스의 통신을 포함하여 Intune에 사용하기 위해 인증서를 요청하는 디바이스별 SCEP 사용 문제를 해결합니다.
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
ms.openlocfilehash: 4496a5bbc6d5ee5134dc4e6a795494710ea6865d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515223"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>Microsoft Intune에서 SCEP 인증서 프로필 문제 해결 개요

SCEP(단순 인증서 등록 프로토콜) 인증서 프로필 사용 문제는 Intune에서 해결하기 어려울 수 있습니다. 이 문서는 다음을 통해 문제 해결을 돕습니다.

- SCEP 프로세스의 아키텍처 및 통신 흐름 설명
- 해당 통신 흐름에서 문제가 있는 위치의 범위를 좁힐 수 있도록 지원
- 인증서 프로필 문제 해결을 위한 후속 문서에서 참조되는 주요 로그 파일 식별

이 문서와 관련 SCEP 인증서 문제 해결 문서의 정보는 Android, iOS/iPad, Windows 디바이스에서 SCEP 인증서 프로필을 사용하는 경우에 적용됩니다. macOS의 경우 지금은 비슷한 정보가 제공되지 않습니다.

NDES(네트워크 장치 등록 서비스) 문제를 해결하려면 support.microsoft.com에서 다음 문서를 참조하세요.

- [Verify NDES configuration on-premises for SCEP certificates in Intune](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)(Intune에서 SCEP 인증서의 온-프레미스 NDES 구성 확인)
- [Troubleshooting NDES configuration for use with Microsoft Intune certificate profiles]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)(Microsoft Intune 인증서 프로필과 함께 사용할 NDES 구성 문제 해결)

계속하기 전에 신뢰할 수 있는 인증서 프로필을 통한 루트 인증서 배포를 포함하여 [SCEP 인증서 프로필을 사용하기 위한 필수 구성 요소](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates)를 충족했는지 확인합니다.

## <a name="scep-communication-flow-overview"></a>SCEP 통신 흐름 개요

다음 그림은 Intune에서의 SCEP 통신 프로세스 기본 개요를 보여 줍니다.

![SCEP 인증서 프로필 흐름](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [SCEP 인증서 프로필을 배포](troubleshoot-scep-certificate-profile-deployment.md)합니다. Intune은 특정 사용자, 인증서 용도, 인증서 유형을 요구하는 챌린지 문자열을 생성합니다.

2. [디바이스와 NDES 서버의 통신](troubleshoot-scep-certificate-device-to-ndes.md). 디바이스는 프로필의 NDES용 URI를 사용하여 NDES 서버에 연결하므로 챌린지를 제공할 수 있습니다.

3. [NDES와 정책 모듈의 통신](troubleshoot-scep-certificate-ndes-policy-module.md). NDES가 챌린지를 서버의 Intune Certificate Connector 정책 모듈에 전달하면 정책 모듈이 요청의 유효성을 검사합니다.

4. [NDES와 인증 기관의 통신](troubleshoot-scep-certificate-ndes-policy-module.md). NDES는 유효한 인증서 발급 요청을 CA(인증 기관)에 전달합니다.

5. [디바이스에 인증서 배달](troubleshoot-scep-certificate-delivery.md). 인증서가 디바이스에 배달됩니다.

6. [Intune에 배포 보고](troubleshoot-scep-certificate-reporting.md). Intune Certificate Connector는 인증서 발급 이벤트를 Intune에 보고합니다.

## <a name="log-files"></a>로그 파일

통신 및 인증서 프로비전 워크플로의 문제를 식별 하려면 서버 인프라 및 디바이스의 로그 파일을 검토합니다. SCEP 인증서 프로필 문제 해결에 대한 이후 섹션에서는 이 섹션에서 참조하는 로그 파일을 참조합니다.

- [인프라 및 서버 로그](#logs-for-on-premises-infrastructure)

디바이스 로그는 디바이스 플랫폼에 따라 달라집니다.  

- [iOS 및 iPadOS](#logs-for-ios-and-ipados-devices)
- [OWA(Outlook Web Access)](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>온-프레미스 인프라 로그
  
인증서 배포에 SCEP 인증서 프로필을 사용하도록 지원하는 온-프레미스 인프라에는 Microsoft Intune Certificate Connector, Windows Server에서 실행되는 NDES 및 인증 기관이 포함됩니다.

이러한 역할의 로그 파일에는 Windows 이벤트 뷰어, 인증서 콘솔, Intune Certificate Connector, NDES 또는 온-프레미스 인프라의 일부인 그 밖의 역할 및 작업에 관련된 다양한 로그 파일이 포함됩니다.

다음 목록에는 후속 SCEP 문제 해결 문서에서 참조되는 로그 또는 콘솔이 포함됩니다. 

- **NDESConnector_date_time.svclog**:

  이 로그는 Microsoft Intune Certificate Connector와 Intune 클라우드 서비스의 통신을 보여 줍니다. 이 로그 파일은 [서비스 추적 뷰어 도구](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe)를 사용하여 볼 수 있습니다.

  관련 레지스트리 키: *HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  위치: *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*에서 NDES를 호스트하는 서버

- **CertificateRegistrationPoint_date_time.svclog**:

  이 로그는 인증서 요청을 받고 확인하는 NDES 정책 모듈을 보여 줍니다. 이 로그 파일은 [서비스 추적 뷰어 도구](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe)를 사용하여 볼 수 있습니다.

  위치: *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*에서 NDES를 호스트하는 서버

- **NDESPlugin.log**:

  이 로그는 인증서 등록 지점으로의 인증서 요청 전달 및 이러한 요청의 결과 확인을 보여 줍니다.

  위치: *%program_files%\Microsoft Intune\NDESPolicyModule\logs*에서 NDES를 호스트하는 서버

- **IIS 로그**:

  IIS 로그는 NDES에 들어가는 모바일 디바이스의 인증서 요청을 보여 줍니다.

  위치: *c:\inetpub\logs\LogFiles\W3SVC1*에서 NDES를 호스트하는 서버

- **Windows 응용 프로그램 로그**:

  이 로그는 SCEP 애플리케이션 풀과 같은 IIS 문제를 조사할 때 유용합니다.

  위치: NDES: **eventvwr.msc**를 실행하여 Windows 이벤트 뷰어 열기를 호스트하는 서버




### <a name="logs-for-android-devices"></a>Android 디바이스의 로그

Android를 실행하는 디바이스의 경우 **Android 회사 포털** 앱 로그 파일 **OMADM.log**를 사용합니다. 로그를 수집하고 검토하기 전에 [자세한 정보 로깅](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)을 사용하도록 설정되었는지 확인한 다음 문제를 재현합니다.

디바이스에서 OMADM.log를 수집하려면 [USB 케이블을 사용하여 로그 업로드 및 전자 메일 보내기](/intune-user-help/send-logs-to-your-it-admin-using-cable-android)를 참조하세요.

지원을 위한 [로그 업로드 및 전자 메일 보내기](/intune-user-help/send-logs-to-your-it-admin-by-email-android#upload-and-email-logs-from-microsoft-intune-app)도 가능합니다.

### <a name="logs-for-ios-and-ipados-devices"></a>iOS 및 iPadOS 디바이스의 로그

iOS/iPadOS를 실행하는 디바이스의 경우 디버그 로그 및 Mac 컴퓨터에서 실행되는 **Xcode**를 사용합니다.

1. iOS/iPadOS 디바이스를 Mac에 연결하고 **애플리케이션** > **유틸리티**로 이동하여 콘솔 앱을 엽니다. 

2. **작업**에서 **정보 메시지 포함** 및 **디버그 메시지 포함**을 선택합니다.

   ![로그 옵션 선택](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. 문제를 재현한 다음 로그를 텍스트 파일에 저장합니다.
   1. **편집** > **모두 선택**을 선택하여 현재 화면의 모든 메시지를 선택한 다음 **편집** > **복사**를 선택하여 메시지를 클립보드에 복사합니다. 
   2. TextEdit 애플리케이션을 열고 복사한 로그를 새 텍스트 파일에 붙여 넣은 다음 파일을 저장합니다.


iOS 및 iPadOS 디바이스의 회사 포털 로그에는 SCEP 인증서 프로필에 대한 정보가 포함되어 있지 않습니다.

### <a name="logs-for-windows-devices"></a>Windows 디바이스의 로그

Windows를 실행하는 디바이스의 경우 Windows 이벤트 로그를 사용하여 Intune으로 관리하는 디바이스의 등록 또는 디바이스 관리 문제를 진단합니다.

디바이스에서 **이벤트 뷰어** > **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider**를 엽니다.

![Windows 이벤트 로그](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>다음 단계

[SCEP 인증서 프로필의 배포](troubleshoot-scep-certificate-profile-deployment.md) 검토 
