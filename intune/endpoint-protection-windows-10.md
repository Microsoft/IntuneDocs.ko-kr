---
title: Microsoft Intune - Azure의 Windows 10에서 엔드포인트 보호 추가 | Microsoft Docs
description: Windows 10 장치에서 엔드포인트 보호 설정을 사용하거나 추가하여 Windows Defender 기능을 사용하도록 설정합니다. 여기에는 Application Guard, 방화벽, SmartScreen, 암호화 및 bitlocker, Exploit Guard, Application Control, Security Center 및 Microsoft Intune의 로컬 장치에 대한 보안이 포함됩니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0831f374b9c6da417d8159dce1b58e40f0d3643c
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744944"
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Intune의 Windows 10 이상용 Endpoint Protection 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Endpoint Protection 프로필을 사용하면 BitLocker 및 Windows Defender와 같은 Windows 10 장치의 보안 기능을 제어할 수 있습니다.

이 문서의 정보를 사용하여 Endpoint Protection 프로필을 만듭니다. Windows Defender 바이러스 백신을 구성하려면 [Windows 10 장치 차단](device-restrictions-windows-10.md#windows-defender-antivirus)을 참조하세요. 

> [!NOTE]
> Windows 10 Home 및 Professional 버전에서는 이러한 설정이 지원되지 않습니다.

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Microsoft Edge를 사용하는 동안 Windows Defender Application Guard는 조직에서 신뢰할 수 있는 것으로 정의되지 않은 사이트에서 환경을 보호합니다. 사용자가 격리된 네트워크 경계에 나열되지 않은 사이트를 방문하면 Hyper-V의 가상 검색 세션에서 사이트가 열립니다. 신뢰할 수 있는 사이트는 장치 구성에서 구성할 수 있는 네트워크 경계로 정의됩니다. 

Application Guard는 Windows 10(64비트) 장치에서만 사용할 수 있습니다. 이 프로필을 사용하면 Win32 구성 요소가 설치되어 Application Guard를 활성화할 수 있습니다.

- **Application Guard**: Hyper-V 가상화된 검색 컨테이너에서 승인되지 않은 사이트를 엽니다.
- **클립보드 동작**: 로컬 PC와 Application Guard 가상 브라우저 간에 허용되는 복사/붙여넣기 작업을 선택합니다.
- **엔터프라이즈 사이트의 외부 콘텐츠**: 승인되지 않은 웹 사이트의 콘텐츠를 로드하지 못하도록 차단합니다.
- **가상 브라우저에서 인쇄**: PDF, XPS, 로컬 및/또는 네트워크 프린터에서 가상 브라우저의 내용을 인쇄할 수 있습니다.
- **로그 수집**: Application Guard 검색 세션에서 발생하는 이벤트에 대한 로그를 수집합니다.
- **사용자가 생성한 브라우저 데이터 보존**: Application Guard 가상 검색 세션 중에 만들어진 사용자 데이터(예: 암호, 즐겨찾기 및 쿠키)를 저장합니다.
- **그래픽 가속**: Application Guard 가상 검색 세션 내에서 작업할 때 그래픽 집약적 웹 사이트를 더 빠르게 로드합니다. 가상 그래픽 처리 장치에 대한 액세스를 사용하여 웹 사이트를 더 빠르게 로드합니다.
- **호스트 파일 시스템에 파일을 다운로드**: 사용자가 호스트 운영 체제에 가상화된 브라우저에서 파일을 다운로드하도록 허용합니다.

## <a name="windows-defender-firewall"></a>Windows Defender 방화벽

### <a name="global-settings"></a>전역 설정

다음 설정은 모든 네트워크 형식에 적용할 수 있습니다.

- **파일 전송 프로토콜**: 상태 저장 FTP를 차단합니다.
- **삭제 전 보안 연결 유휴 시간**: *n*초 동안 네트워크 트래픽이 검색되지 않으면 보안 연결이 삭제됩니다.
- **미리 공유한 키 인코딩**: UTF-8을 사용하여 미리 공유한 키를 인코드합니다.
- **IPsec 예외**: **IPv6 ICMP 종류 코드 네트워크 환경 검색**, **ICMP**, **IPv6 ICMP 종류 코드 라우터 검색** 및 **IPv4 및 IPv6 DHCP 네트워크 트래픽**을 포함하여 특정 트래픽이 IPsec에서 제외되도록 구성합니다.
- **인증서 해지 목록 확인**: **CRL 확인 사용 안 함**, **해지된 인증서에 대한 CRL 확인만 실패** 및 **오류 발생 시 CRL 확인 실패**를 포함하여 인증서 해지 목록 확인이 적용되는 방법에 대한 값을 설정합니다.
- **키 지정 모듈에 대해 선택적으로 인증 집합 일치**: 키 지정 모듈에서 인증 집합의 모든 인증 도구 모음을 지원하지 않는 경우 해당 인증 집합 전체를 무시하도록 설정합니다.
- **패킷 큐**: IPsec 터널 게이트웨이 시나리오의 암호화된 수신 및 일반 텍스트 전달에 대해 수신 쪽 소프트웨어의 크기 조정이 활성화되는 방법을 지정합니다. 이 설정을 통해 패킷 순서가 유지됩니다.

### <a name="network-settings"></a>네트워크 설정

다음 설정은 **도메인(작업 공간) 네트워크**, **사설(검색 가능) 네트워크** 및 **공용(검색 불가능) 네트워크**를 포함한 특정 네트워크 형식에 적용할 수 있습니다.

#### <a name="general-settings"></a>일반 설정

- **Windows Defender 방화벽**: 네트워크 트래픽을 차단하려면 이 설정을 사용합니다.
- **은폐 모드**: 방화벽이 은폐 모드에서 작동하지 못하도록 차단합니다. 은폐 모드를 차단하면 **IPsec 보안 패킷 예외**도 차단할 수 있습니다.
- **차폐**: 이 설정과 방화벽 설정을 사용하면 들어오는 모든 트래픽이 차단됩니다.
- **멀티캐스트 브로드캐스트에 대한 유니캐스트 응답**: 멀티캐스트 브로드캐스트에 대한 유니캐스트 응답을 차단합니다. 일반적으로 멀티캐스트 또는 브로드캐스트 메시지에 대한 유니캐스트 응답을 수신하려 하지 않습니다. 이러한 응답은 서비스 거부(DOS) 공격 또는 알려진 라이브 컴퓨터를 프로브하려고 시도하는 공격자를 나타낼 수 있습니다.
- **인바운드 알림**: 응용 프로그램이 포트에서 수신 대기하지 못하도록 차단될 때 사용자에 대한 알림 표시를 차단합니다.
- **인바운드 연결에 대한 기본 작업**: 방화벽이 인바운드 연결에서 수행하는 기본 작업을 차단합니다.

#### <a name="rule-merging"></a>규칙 병합

- **로컬 저장소의 권한 있는 응용 프로그램 Windows Defender 방화벽 규칙**: 인식하고 적용할 권한 있는 방화벽 규칙을 로컬 저장소에 적용합니다.
- **로컬 저장소의 전역 포트 Windows Defender 방화벽 규칙**: 인식하고 적용할 전역 포트 방화벽 규칙을 로컬 저장소에 적용합니다.
- **로컬 저장소의 Windows Defender 방화벽 규칙**: 인식하고 적용할 전역 방화벽 규칙을 로컬 저장소에 적용합니다.
- **로컬 저장소의 IPsec 규칙**: 스키마 또는 연결 보안 규칙 버전과 관계없이 로컬 저장소에서 연결 보안 규칙을 적용합니다.

## <a name="windows-defender-smartscreen-settings"></a>Windows Defender SmartScreen 설정

- **앱 및 파일용 SmartScreen**: 파일 실행 및 앱 실행에 대해 Windows SmartScreen을 사용하도록 설정합니다.
- **확인되지 않은 파일 실행**: Windows SmartScreen에서 확인하지 않은 파일을 최종 사용자가 실행하지 못하도록 차단합니다.

## <a name="windows-encryption"></a>Windows 암호화

### <a name="windows-settings"></a>Windows 설정

다음 두 설정은 모든 버전의 Windows 10에 적용됩니다.

- **장치 암호화**: 이 설정을 사용하면 장치 암호화를 사용하도록 설정하라는 메시지가 표시됩니다. 또한 다른 공급자의 암호화가 사용하도록 설정되지 않았는지 확인하라는 메시지도 표시됩니다. 다른 암호화 방법이 활성화된 상태에서 Windows 암호화를 켜면 장치가 불안정해질 수 있습니다.
- **메모리 카드 암호화**: 이 설정을 사용하면 장치에서 사용하는 모든 이동식 저장소 카드를 암호화합니다.


### <a name="bitlocker-base-settings"></a>BitLocker 기본 설정

기본 설정은 모든 종류의 데이터 드라이브에 대한 범용 BitLocker 설정입니다. BitLocker 그룹 정책 설정은 최종 사용자가 모든 종류의 데이터 드라이브에서 수정할 수 있는 드라이브 암호화 작업 또는 구성 옵션을 관리합니다.

- **다른 디스크 암호화에 대한 경고**: 최종 사용자 컴퓨터의 다른 디스크 암호화에 대한 경고 메시지가 표시되지 않도록 설정합니다.
- **암호화 방법 구성**: 운영 체제, 데이터 및 이동식 드라이브에 대한 암호화 알고리즘을 구성하려면 이 설정을 사용하도록 설정합니다.
  - **운영 체제 드라이브에 대한 암호화**: 운영 체제 드라이브에 대한 암호화 방법을 선택합니다. XTS-AES 알고리즘을 사용하는 것이 좋습니다.
  - **고정 데이터 드라이브에 대한 암호화**: 고정(기본 제공) 데이터 드라이브에 대한 암호화 방법을 선택합니다. XTS-AES 알고리즘을 사용하는 것이 좋습니다.
  - **이동식 데이터 드라이브에 대한 암호화**: 이동식 데이터 드라이브에 대한 암호화 방법을 선택합니다. 이동식 드라이브가 Windows 10을 실행하지 않는 장치와 함께 사용되는 경우 AES-CBC 알고리즘을 사용하는 것이 좋습니다.

### <a name="bitlocker-os-drive-settings"></a>BitLocker OS 드라이브 설정

다음 설정은 특히 운영 체제 데이터 드라이브에 적용됩니다.

- **시작 시 추가 인증**: TPM(신뢰할 수 있는 플랫폼 모듈) 사용을 포함하여 컴퓨터 시작에 필요한 인증 요구 사항을 구성합니다.
  - **호환되지 않는 TPM 칩과 BitLocker**
  - **호환되는 TPM 시작**: TPM 칩을 허용하거나, 허용하지 않거나, 필수로 요청하도록 선택합니다.
  - **호환되는 TPM 시작 PIN**: TPM 칩과 함께 시작 PIN 사용을 허용하거나, 허용하지 않거나, 필수로 요청하도록 선택합니다.
  - **호환되는 TPM 시작 키**: TPM 칩과 함께 시작 키 사용을 허용하거나, 허용하지 않거나, 필수로 요청하도록 선택합니다.
  - **호환되는 TPM 시작 키 및 PIN**: TPM 칩과 함께 시작 키 및 PIN 사용을 허용하거나, 허용하지 않거나, 필수로 요청하도록 선택합니다.
- **최소 PIN 길이**: TPM 시작 PIN의 최소 길이를 구성하려면 이 설정을 사용하도록 설정합니다.
  - **최소 문자**: 시작 PIN에 필요한 문자 수를 **4**-**20** 사이로 입력합니다.
- **OS 드라이브 복구**: 이 설정을 사용하면 필요한 시작 정보를 사용할 수 없을 때 BitLocker로 보호된 운영 체제 드라이브를 복구하는 방법을 제어할 수 있습니다.
  - **인증서 기반 데이터 복구 에이전트**: 데이터 복구 에이전트를 BitLocker로 보호된 운영 체제 드라이브와 함께 사용할 수 있게 하려면 이 설정을 사용하도록 설정합니다.
  - **사용자의 복구 암호 생성**: 사용자가 48자리 복구 암호를 생성하는 것이 허용되는지, 허용되지 않는지 또는 필수인지를 선택합니다.
  - **사용자의 복구 키 생성**: 사용자가 256비트 복구 키를 생성하는 것이 허용되는지, 허용되지 않는지 또는 필수인지를 선택합니다.
  - **BitLocker 설치 마법사의 복구 옵션**: 이 설정을 사용하면 BitLocker가 작동될 때 사용자가 복구 옵션을 보거나 변경하지 못하도록 방지할 수 있습니다.
  - **BitLocker 복구 정보를 AD DS에 저장**: BitLocker 복구 정보를 Active Directory에 저장할 수 있게 합니다.
  - **AD DS에 저장된 BitLocker 복구 정보**: Active Directory에 저장될 BitLocker 복구 정보 부분을 구성합니다. 다음 중에서 선택합니다.
    - **백업 복구 암호 및 키 패키지**
    - **백업 복구 암호만**
  - **BitLocker를 활성화하기 전에 AD DS에 복구 정보 저장**: 이 설정을 사용하면 장치가 도메인에 조인되어 있고 BitLocker 복구 정보가 Active Directory에 성공적으로 저장되어 있지 않을 때 사용자가 BitLocker를 작동할 수 없도록 합니다.
- **부팅 전 복구 메시지 및 URL**: 이 설정을 사용하면 부팅 전 키 복구 화면에 표시되는 메시지와 URL을 구성할 수 있습니다.
  - **부팅 전 복구 메시지**: 부팅 전 복구 메시지가 사용자에게 표시되는 방식을 구성합니다. 다음 중에서 선택합니다.
    - **기본 복구 메시지 및 URL 사용**
    - **빈 복구 메시지 및 URL 사용**
    - **사용자 지정 복구 메시지 사용**
    - **사용자 지정 복구 URL 사용**

### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 고정 데이터 드라이브 설정

- **BitLocker로 보호되지 않는 고정 데이터 드라이브에 대한 쓰기 액세스**: 이 설정을 사용하면 모든 고정 또는 기본 제공 데이터 드라이브에서 BitLocker 보호를 사용하도록 설정해야 드라이브에 쓸 수 있습니다.
- **고정식 드라이브 복구**: 이 설정을 사용하면 필요한 시작 정보를 사용할 수 없을 때 BitLocker로 보호된 고정 드라이브를 복구하는 방법을 제어할 수 있습니다.
  - **데이터 복구 에이전트**: 데이터 복구 에이전트를 BitLocker로 보호된 고정 드라이브와 함께 사용하려면 이 설정을 사용하도록 설정합니다.
  - **사용자의 복구 암호 생성**: 사용자가 48자리 복구 암호를 생성하는 것이 허용되는지, 허용되지 않는지 또는 필수인지를 구성합니다.  
  - **사용자의 복구 키 생성**: 사용자가 256비트 복구 키를 생성하는 것이 허용되는지, 허용되지 않는지 또는 필수인지를 구성합니다.
  - **BitLocker 설치 마법사의 복구 옵션**: 이 설정을 사용하면 BitLocker가 작동될 때 사용자가 복구 옵션을 보거나 변경하지 못하도록 방지할 수 있습니다.
  - **BitLocker 복구 정보를 AD DS에 저장**: BitLocker 복구 정보를 Active Directory에 저장할 수 있게 합니다.
  - **AD DS에 저장된 BitLocker 복구 정보**: Active Directory에 저장될 BitLocker 복구 정보 부분을 구성합니다. 다음 중에서 선택합니다.
    - **백업 복구 암호 및 키 패키지**
    - **백업 복구 암호만**
  - **BitLocker를 활성화하기 전에 AD DS에 복구 정보 저장**: 이 설정을 사용하면 장치가 도메인에 조인되어 있고 BitLocker 복구 정보가 Active Directory에 성공적으로 저장되어 있지 않을 때 사용자가 BitLocker를 작동할 수 없도록 합니다.

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 이동식 데이터 드라이브 설정

- **BitLocker로 보호되지 않는 이동식 데이터 드라이브에 대한 쓰기 액세스**: 이동식 저장소 드라이브에 BitLocker 암호화가 필요한지 여부를 지정합니다.
  - **다른 조직에서 구성된 장치에 대한 쓰기 액세스**: 다른 조직에 속한 이동식 데이터 드라이브에 쓸 수 있는지 여부를 지정합니다.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

[Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard)를 사용하여 직원이 사용하는 앱의 공격 노출 영역을 관리하고 줄입니다.

### <a name="attack-surface-reduction"></a>공격 노출 영역 축소

- **Windows 로컬 보안 기관 하위 시스템에서 도용하는 자격 증명에 플래그 지정**

악용 검색 맬웨어가 컴퓨터를 감염시키는 데 일반적으로 사용되는 [작업과 앱을 방지](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard)합니다.

#### <a name="rules-to-prevent-office-macro-threats"></a>Office 매크로 위협을 방지하는 규칙

Office 앱에서 다음 작업을 수행하지 못하도록 차단합니다.

- **다른 프로세스에 삽입되는 Office 앱(예외 없음)**
- **실행 가능 콘텐츠를 만드는 Office 앱/매크로**
- **자식 프로세스를 실행하는 Office 앱**
- **Office 매크로 코드에서 Win32 가져오기**

#### <a name="rules-to-prevent-script-threats"></a>스크립트 위협을 방지하는 규칙

스크립트 위협을 방지하기 위해 다음 항목을 차단합니다.

- **난독 처리된 js/vbs/ps/매크로 코드**
- **인터넷에서 다운로드된 페이로드를 실행하는 js/vbs(예외 없음)**
- **PSExec 및 WMI 명령에서 프로세스 만들기**
- **USB에서 실행되는 신뢰할 수 없고 서명되지 않은 프로세스**
- **전파, 처리 기간 또는 신뢰할 수 있는 목록 조건을 충족하지 않는 실행 파일**

#### <a name="rules-to-prevent-email-threats"></a>이메일 위협을 방지하는 규칙

이메일 위협을 방지하기 위해 다음 항목을 차단합니다.

- **이메일(웹 메일/메일 클라이언트)에서 삭제된 실행 파일 콘텐츠(exe, dll, ps, js, vbs 등)의 실행(예외 없음)**

#### <a name="rules-to-protect-against-ransomware"></a>랜섬웨어로부터 보호하기 위한 규칙
- **고급 랜섬웨어 보호**

> [!TIP]
> [Windows Defender Exploit Guard를 통한 공격 노출 영역 축소](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard)에서 이러한 규칙에 대한 자세한 세부 정보를 제공합니다.

#### <a name="attack-surface-reduction-exceptions"></a>공격 노출 영역 축소 예외

- **공격 노출 영역 축소 규칙에서 제외할 파일 및 폴더**: 구성된 규칙에서 제외할 위치 목록을 가져오거나 추가합니다.

### <a name="controlled-folder-access"></a>폴더 액세스 제어

랜섬웨어와 같은 악성 앱과 위협으로부터 중요한 데이터를 보호합니다.

- **폴더 보호**: 악성 앱에 의한 원하지 않는 변경으로부터 파일 및 폴더를 보호합니다. **보호된 폴더에 액세스할 수 있는 앱 목록**을 가져오거나 수동으로 추가할 수 있습니다. 또한 업로드가 포함된 **보호해야 하는 추가 폴더의 목록**을 추가하거나 수동으로 추가할 수도 있습니다.

### <a name="network-filtering"></a>네트워크 필터링

모든 앱에서 평판이 낮은 IP/도메인으로의 아웃바운드 연결을 차단합니다.

### <a name="exploit-protection"></a>악용 방지

메모리, 제어 흐름 및 정책 제한을 구성할 수 있는 XML 파일을 업로드하여 **Exploit Protection 인터페이스의 사용자 편집**을 차단합니다. XML 파일의 설정을 사용하여 응용 프로그램의 악용을 방지할 수 있습니다.

Exploit Protection을 사용하려면 선택한 시스템 및 응용 프로그램 완화 설정을 나타내는 XML 파일을 만듭니다. 다음 두 가지 방법 중 하나를 사용하여 수행할 수 있습니다.

 1. PowerShell: Get-ProcessMitigation, Set-ProcessMitigation 및 ConvertTo-ProcessMitigationPolicy PowerShell cmdlet 중 하나 이상을 사용합니다. cmdlet은 완화 설정을 구성하고 이들의 XML 표현을 내보냅니다.

 2. Windows Defender 보안 센터 UI: Windows Defender 보안 센터에서 앱 및 브라우저 컨트롤을 클릭한 다음, 결과 화면의 아래쪽으로 스크롤하여 Exploit Protection을 찾습니다. 먼저 시스템 설정 및 프로그램 설정 탭을 사용하여 완화 설정을 구성합니다. 그런 다음 화면 아래쪽의 설정 내보내기 링크를 찾아서 해당 XML 표현을 내보냅니다.

## <a name="windows-defender-application-control"></a>Windows Defender 응용 프로그램 제어

**응용 프로그램 제어 코드 무결성 정책**을 사용하여 감사해야 하거나 Windows Defender 응용 프로그램 제어에서 실행하도록 신뢰할 수 있는 추가 앱을 선택합니다. Windows 구성 요소 및 모든 Windows 저장소 앱의 실행은 자동으로 신뢰할 수 있습니다.

**감사 전용** 모드에서 실행하는 경우 응용 프로그램이 차단되지 않습니다. **감사 전용** 모드는 로컬 클라이언트 로그에 있는 모든 이벤트를 기록합니다.

사용하도록 설정되면 응용 프로그램 제어는 **적용**에서 **감사 전용**으로 모드를 변경할 때에만 해제될 수 있습니다. 모드를 **적용**에서 **구성하지 않음**으로 변경하면 응용 프로그램 제어가 할당된 장치에 계속 적용됩니다.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard
Windows Defender Credential Guard는 자격 증명 도난 공격을 방어합니다. 권한 있는 시스템 소프트웨어만 액세스할 수 있도록 비밀을 격리합니다.

**Credential Guard** 설정은 다음과 같습니다.

- **사용 안 함**: 이전에 **UEFI 잠금 없이 사용** 옵션을 사용하여 Credential Guard를 켠 경우 원격으로 Credential Guard를 끕니다.
- **UEFI 잠금을 사용하여 설정**: 레지스트리 키 또는 그룹 정책을 사용하여 원격으로 Credential Guard를 사용할 수 없도록 합니다.

    > [!NOTE]
    > 이 설정을 사용하고 나중에 Credential Guard를 사용하지 않으려는 경우 그룹 정책을 **사용 안 함**으로 설정해야 합니다. 그리고 각 컴퓨터에서 UEFI 구성 정보를 물리적으로 지웁니다. UEFI 구성이 지속되는 한, Credential Guard가 계속 사용됩니다.

- **UEFI 잠금 없이 설정**: 그룹 정책을 사용하여 원격으로 Credential Guard를 사용할 수 없도록 합니다. 이 설정을 사용하는 장치에서는 Windows 10 버전 1511 이상을 실행 중이어야 합니다.

Credential Guard를 사용하도록 설정할 경우 다음 필수 기능도 사용하도록 설정됩니다.

- VBS(**가상화 기반 보안**): 다음 재부팅 중에 켜집니다. 가상화 기반 보안은 Windows 하이퍼바이저를 사용하여 보안 서비스에 대한 지원을 제공합니다.
- **보안 부팅 및 DMA(직접 메모리 액세스)**: 보안 부팅 및 DMA(직접 메모리 액세스) 보호를 사용하여 VBS를 켭니다. DMA 보호는 하드웨어 지원이 필요하며 올바르게 구성된 장치에서만 작동합니다.

## <a name="windows-defender-security-center"></a>Windows Defender 보안 센터

Windows Defender 보안 센터 앱은 개별 기능별로 별도의 앱 또는 프로세스로 작동합니다. 또한 알림 센터를 통해 알림을 표시합니다. 수집기 또는 단일 위치로 작동하여 상태를 확인하고 각 기능에 대한 일부 구성을 수행합니다. [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) 문서에서 자세한 내용을 알아보세요.

#### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender 보안 센터 앱 및 알림

Windows Defender Security Center 앱의 다양한 영역에 대한 최종 사용자 액세스를 차단합니다. 또한 섹션을 숨기면 관련 알림도 차단됩니다.

- **바이러스 및 위협 방지**
- **장치 성능 및 상태**
- **방화벽 및 네트워크 보호**
- **앱 및 브라우저 제어**
- **제품군 옵션**
- **앱 표시 영역의 알림**: 최종 사용자에게 표시할 알림을 선택합니다. 중요하지 않은 알림에는 검색 완료 시 알림을 포함한 Windows Defender 바이러스 백신 활동의 요약이 포함됩니다. 다른 모든 알림은 중요 알림으로 간주합니다.

#### <a name="it-contact-information"></a>IT 연락처 정보

Windows Defender Security Center 앱 및 앱 알림에 표시할 IT 연락처 정보를 제공합니다. **앱 및 알림에 표시**, **앱에만 표시**, **알림에만 표시** 또는 **표시 안 함**을 선택할 수 있습니다. **IT 조직 이름**과 다음 연락처 옵션 중 하나 이상을 입력해야 합니다.

- **IT 부서 전화 번호 또는 Skype ID**
- **IT 부서 이메일 주소**
- **IT 지원 웹 사이트 URL**

## <a name="local-device-security-options"></a>로컬 장치 보안 옵션

이러한 옵션을 사용하여 Windows 10 장치에서 로컬 보안 설정을 구성합니다.

### <a name="accounts"></a>계정

- **새 Microsoft 계정 추가**: 사용자가 이 컴퓨터에 새 Microsoft 계정을 추가하지 못하도록 합니다.
- **암호 없이 원격 로그온**: 암호로 보호되지 않은 로컬 계정이 물리적 장치가 아닌 위치에서 로그온할 수 있도록 합니다.

#### <a name="admin"></a>관리자

- **로컬 관리자 계정**: 로컬 관리자 계정을 사용하도록 설정할지 여부를 결정합니다.
- **관리자 계정 이름 바꾸기**: 관리자 계정의 SID(보안 ID)와 연결할 다른 계정 이름을 정의합니다.

#### <a name="guest"></a>게스트

- **게스트 계정**: 게스트 계정을 사용하도록 설정할지 여부를 결정합니다.
- **게스트 계정 이름 바꾸기**: 게스트 계정의 SID(보안 ID)와 연결할 다른 계정 이름을 정의합니다.

### <a name="devices"></a>장치

- **로그온 없이 장치 도킹 해제**: 로그인할 필요 없이 휴대용 컴퓨터가 도킹 해제되지 않도록 합니다.
- **공유 프린터에 대한 프린터 드라이버 설치**: 공유 프린터에 연결하는 중에 프린터 드라이버 설치를 관리자만으로 제한합니다.
- **CD-ROM 액세스를 로컬 활성 사용자로 제한**: 이 설정을 사용하도록 설정하면 대화형으로 로그온한 사용자만 CD-ROM 미디어에 액세스할 수 있습니다.
- **이동식 미디어 포맷 및 꺼내기**: 이동식 NTFS 미디어를 포맷하고 꺼낼 수 있는 사용자를 정의합니다.
  - **구성되지 않음**
  - **관리자 및 고급 사용자**
  - **관리자 및 대화형 사용자**

### <a name="interactive-logon"></a>대화형 로그온

- **화면 보호기가 활성화될 때까지 잠금 화면 비활성 시간(분)**: 화면 보호기가 실행될 때까지 대화형 데스크톱의 로그인 화면에서 비활성 상태인 최대 시간을 정의합니다.
- **로그온하려면 Ctrl+Alt+Del을 눌러야 함**: 사용자가 로그온하려면 먼저 Ctrl+Alt+Del을 눌러야 합니다.
- **스마트 카드 제거 동작**: 로그온한 사용자의 스마트 카드가 스마트 카드 판독기에서 제거될 때 수행되는 동작을 결정합니다. 옵션은 다음과 같습니다.

  - **워크스테이션 잠금**: 스마트 카드를 제거하면 워크스테이션이 잠깁니다. 이 옵션을 사용하면 사용자가 해당 영역을 그대로 두고, 스마트 카드를 사용하고, 보호된 세션을 계속 유지할 수 있습니다.
  - **강제 로그오프**: 스마트 카드를 제거하면 사용자가 자동으로 로그오프됩니다.
  - **원격 데스크톱 서비스 세션인 경우 연결 끊기**: 스마트 카드를 제거하면 사용자를 로그오프하지 않고 세션의 연결이 끊어집니다. 이 옵션을 사용하면 사용자가 다시 로그인하지 않고도 스마트 카드를 삽입하고, 나중에 세션을 다시 시작하거나 다른 스마트 카드 판독기가 장착된 컴퓨터에서 다시 시작할 수 있습니다. 세션이 로컬이면 이 정책은 워크스테이션 잠금과 동일하게 작동합니다.

    [LocalPoliciesSecurity 옵션](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior)에서 자세한 정보를 제공합니다.

#### <a name="display"></a>표시

- **잠금 화면의 사용자 정보**: 세션이 잠겨 있을 때 표시되는 사용자 정보를 구성합니다. 구성하지 않으면 사용자 표시 이름, 도메인 및 사용자 이름이 표시됩니다.
  - **구성되지 않음**: 사용자 표시 이름, 도메인 및 사용자 이름
  - **사용자 표시 이름, 도메인 및 사용자 이름**
  - **사용자 표시 이름만**
  - **사용자 정보 표시 안 함**
- **마지막으로 로그인한 사용자 숨기기**: 이 장치에 마지막으로 로그인한 사용자의 사용자 이름을 표시하지 않습니다.
- **로그인 시 사용자 이름 숨기기**: 자격 증명이 입력된 후, 장치의 바탕 화면이 표시되기 전에 이 장치에 로그인하는 사용자의 사용자 이름을 표시하지 않습니다.
- **로그온 메시지 제목**: 로그인하려는 사용자에 대한 메시지 제목을 설정합니다.
- **로그온 메시지 텍스트**: 로그인하려는 사용자에 대한 메시지 텍스트를 설정합니다.

### <a name="network-access-and-security"></a>네트워크 액세스 및 보안

- **명명된 파이프 및 공유에 대한 익명 액세스**: **구성되지 않음**(기본값)은 공유 및 명명된 파이프 설정에 대한 익명 액세스를 제한합니다. 익명으로 액세스할 수 있는 설정에 적용됩니다.
- **SAM 계정의 익명 열거**: 익명 사용자가 SAM 계정을 열거할 수 있도록 **허용**합니다. Windows에서는 익명 사용자가 도메인 계정 및 네트워크 공유의 이름을 열거할 수 있습니다.
- **SAM 계정 및 공유의 익명 열거**: **구성되지 않음**(기본값)은 익명 사용자가 도메인 계정 및 네트워크 공유의 이름을 열거할 수 있음을 의미합니다. SAM 계정 및 공유의 익명 열거를 방지하려면 **차단**으로 설정합니다.
- **암호 변경 시 LAN Manager 해시 값 저장됨**: 다음 암호 변경 시 LM(LAN Manager)에서 새 암호에 대한 해시 값을 저장할 수 있도록 **허용**합니다. **구성되지 않음**(기본값)으로 설정하면 해시 값이 저장되지 않습니다.
- **PKU2U 인증 요청**: 온라인 ID를 사용하도록 장치에 대한 PKU2U 인증 요청을 **차단**합니다. **구성되지 않음**(기본값)은 이러한 요청을 허용합니다.
- **원격 RPC 연결을 SAM으로 제한**: 기본 Security Descriptor Definition Language 문자열을 사용하여 사용자 및 그룹에서 SAM에 대한 원격 호출을 거부하도록 **허용**합니다. **구성되지 않음**(기본값)은 기본 Security Descriptor Definition Language 문자열을 사용하여 사용자 및 그룹에서 SAM에 대한 원격 호출을 수행하도록 허용합니다.
  - **보안 설명자**

### <a name="recovery-console-and-shutdown"></a>복구 콘솔 및 종료

- **종료할 때 가상 메모리 페이지 파일 지우기**: 장치 전원이 꺼질 대 가상 메모리 페이지 파일을 지웁니다.
- **로그온 없이 종료**: Windows 로그온 화면에서 컴퓨터를 종료하는 옵션을 차단합니다. 이 경우 시스템 종료를 수행하기 전에 컴퓨터에 성공적으로 로그온할 수 있어야 합니다.

### <a name="user-account-control"></a>사용자 계정 컨트롤

- **안전한 위치 없는 UIA 무결성**: UIAccess 무결성 수준으로 실행할 파일 시스템의 안전하지 않은 위치에서 앱을 사용하도록 설정합니다.
- **사용자별 위치로 파일 및 레지스트리 쓰기 오류를 가상화**: 앱 쓰기 오류를 정의된 레지스트리 및 파일 시스템 위치로 리디렉션할지 여부를 결정합니다. 그렇지 않으면 앱에서 오류가 발생합니다.
- **서명되고 유효성이 검사된 실행 파일만 권한 상승**: 지정된 실행 파일의 실행을 허용하기 전에 파일에 대해 PKI 인증서 경로 유효성 검사를 적용합니다.

#### <a name="uia-elevation-prompt-behavior-settings"></a>UIA 권한 상승 프롬프트 동작 설정

- **관리자에 대한 권한 상승 프롬프트**: 관리자 승인 모드에서 관리자에 대한 권한 상승 프롬프트의 동작을 정의합니다.
  - **권한 상승 전에 확인 안 함**
  - **보안된 데스크톱에서 자격 증명 확인**
  - **보안된 데스크톱에서 동의 확인**
  - **자격 증명 확인**
  - **동의 확인**
  - **구성되지 않음**: 비 Windows 이진 파일에 대한 동의 확인
- **표준 사용자에 대한 권한 상승 프롬프트**: 표준 사용자에 대한 권한 상승 프롬프트의 동작을 정의합니다.
  - **권한 상승 요청 자동으로 거부**
  - **보안된 데스크톱에서 자격 증명 확인**
  - **구성되지 않음**: 자격 증명 확인
- **사용자의 대화형 데스크톱으로 권한 상승 프롬프트 라우팅**: 모든 권한 상승 요청이 보안 데스크톱이 아닌 대화형 사용자 데스크톱으로 이동하도록 합니다. 관리자 및 표준 사용자에 대한 프롬프트 동작 정책 설정이 사용됩니다.
- **앱 설치에 대한 관리자 권한 프롬프트**: 관리자 권한이 필요한 앱 설치 시 관리자 자격 증명을 요청합니다.
- **보안된 데스크톱 없는 UIA 권한 상승 프롬프트**: UIAccess 앱이 보안 데스크톱을 사용하지 않고 권한 상승 메시지를 표시하도록 허용합니다.

#### <a name="admin-approval-mode-settings"></a>관리자 승인 모드 설정

- **기본 제공 관리자에 대한 관리자 승인 모드**: 기본 제공 관리자 계정이 관리자 승인 모드를 사용하거나 전체 관리자 권한으로 모든 앱을 실행할지 여부를 정의합니다.
- **관리자 승인 모드에서 모든 관리자 실행**: 관리자 승인 모드 및 모든 UAC 정책 설정을 사용하도록 설정할지 여부를 정의합니다.

### <a name="microsoft-network-client"></a>Microsoft 네트워크 클라이언트

- **통신에 디지털 서명(서버가 동의한 경우)**: SMB 클라이언트에서 SMB 패킷 서명 협상을 시도할지 여부를 결정합니다. 사용하도록 설정되면(구성되지 않음) Microsoft 네트워크 클라이언트에서 세션 설정 시 SMB 패킷 서명을 수행하도록 서버에 요청합니다. 서버에서 패킷 서명을 사용하도록 설정되면 패킷 서명이 협상됩니다. 이 정책이 사용할 수 없는 경우 SMB 클라이언트는 SMB 패킷 서명을 협상하지 않습니다.
- **암호화되지 않은 암호를 타사 SMB 서버로 보내기**: 사용 가능한 경우, SMB(Server Message Block) 리디렉터는 인증하는 동안 암호의 암호화를 지원하지 않는 Microsoft 이외 SMB 서버로 일반 텍스트 암호를 보낼 수 있습니다.

### <a name="microsoft-network-server"></a>Microsoft 네트워크 서버

- **통신에 디지털 서명(클라이언트가 동의한 경우)**: SMB 서버가 SMB 패킷 서명을 요청하는 클라이언트와 이 서명을 협상할지 여부를 결정합니다. 사용 가능한 경우, Microsoft 네트워크 서버는 클라이언트가 요청한 대로 SMB 패킷 서명을 협상합니다. 즉, 클라이언트에서 패킷 서명이 사용 가능한 경우, 패킷 서명이 협상됩니다. **구성되지 않음**이거나 사용하지 않도록 설정된 경우(기본값) SMB 클라이언트에서 SMB 패킷 서명을 협상하지 않습니다.
- **통신에 디지털 서명(항상)**: SMB 서버 구성 요소가 패킷 서명을 요구할지 여부를 결정합니다. 사용 가능한 경우, Microsoft 네트워크 서버는 클라이언트가 SMB 패킷 서명을 수행하는데 동의하지 않는 한 Microsoft 네트워크 클라이언트와 통신하지 않습니다. **구성되지 않음**을 사용하지 않도록 설정된 경우(기본값) 클라이언트와 서버 간에 SMB 패킷 서명을 협상합니다.

## <a name="next-steps"></a>다음 단계

이 프로필을 그룹에 할당하려면 [장치 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.