---
title: Microsoft Intune에서 SCEP를 사용할 때 디바이스에 인증서 배포 성공 보고 문제 해결 | Microsoft Docs
description: SCEP 인증서 프로필을 사용하여 프로비전된 인증서의 성공적 배포에 대한 NDES 및 Intune 커넥터의 보고 문제를 해결합니다.
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
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916021"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>Microsoft Intune에서 인증서 배포의 NDES 보고 문제 해결

다음 정보를 사용하여 NDES 및 Microsoft Intune Certificate Connector가 디바이스에 인증서가 배달되었음을 Intune에 성공적으로 보고하는지 확인합니다. Intune에 대한 보고는 SCEP 인증서 프로필을 사용하여 인증서로 Windows 디바이스를 프로비전하는 마지막 단계입니다.

이 문서는 [SCEP 통신 워크플로](troubleshoot-scep-certificate-profiles.md)의 6단계에 적용됩니다.

## <a name="review-for-signs-of-successful-reporting"></a>성공적 보고의 서명 검토

보고가 성공한 경우 NDES 서버에서 다음 예와 유사한 항목을 찾을 수 있습니다.

- **IIS 로그**:

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log**:

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  ![Intune Certificate Connector 로그](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog**:

  ![Intune Certificate Connector 로그](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus**:

  *%ProgramFiles%\Microsoft Intune\CertificateRequestStatus* 폴더로 이동하면 인증서 요청 상태 파일이 포함된 **Failed**, **Processing**, **Succeed** 폴더를 볼 수 있습니다.

  인증서 요청이 성공적으로 처리되면 **Succeed** 폴더에 새 파일이 표시됩니다. *Notepad.exe*를 사용하여 파일을 열고 Intune Certificate Connector에 의해 Intune 서비스에 업로드된 데이터를 볼 수 있습니다. 업로드된 데이터에는 **CertificateSerialNumber**, **UserID**, **DeviceID**, **지문** 같은 세부 정보가 포함됩니다.

### <a name="troubleshoot-stuck-files"></a>중단된 파일 문제 해결

생성되는 새 파일이 *Succeed* 폴더에 표시되지 않으면 *Processing* 폴더에 중단된 파일이 있는지 확인합니다.

NDES 서버에서 Intune Connector Service가 시작되었고 Ndesconnector.svclog에 오류가 없는지 확인합니다.

## <a name="next-steps"></a>다음 단계

[Microsoft Intune에 대한 관리 지원을 받는 방법](../fundamentals/get-support.md)
