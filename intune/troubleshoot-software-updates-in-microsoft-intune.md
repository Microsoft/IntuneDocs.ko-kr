---
title: Microsoft Intune에서 소프트웨어 업데이트 문제 해결 - Azure | Microsoft Docs
description: Microsoft Intune에서 소프트웨어 업데이트 문제를 해결합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7ec762e7e7299e400fefedbf7a8810e1da929f
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461348"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Microsoft Intune에서 소프트웨어 업데이트 문제 해결

Microsoft Intune에서 소프트웨어 업데이트 문제를 해결하는 데 도움을 줍니다.

이 정보가 도움이 되지 않으면 [Microsoft Intune에 대한 지원을 받을](get-support.md) 수도 있습니다.

## <a name="update-agent-error-codes"></a>업데이트 에이전트 오류 코드

다음 표에는 Intune **업데이트 에이전트** 오류 코드가 정리되어 있습니다. 이 표에서 특정 오류 코드를 찾을 수 없는 경우 [Windows 업데이트 오류 코드 목록](https://support.microsoft.com/help/938205/windows-update-error-code-list)을 참조하세요.

|오류 코드|심볼 이름|추가 정보|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|에이전트가 중지되었습니다.|
|**0x00cf0003**|OM_S_UPDATE_ERROR|작업이 완료되었지만 업데이트 적용 중 오류가 발생했습니다.|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|콜백을 실행하는 동안 작업의 연결을 끊는 요청이 발생해서 콜백이 나중에 연결 끊김으로 표시되었습니다.|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|업데이트 설치를 완료하려면 시스템을 다시 시작해야 합니다.|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|설치할 업데이트가 이미 시스템에 설치되어 있습니다.|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|제거할 업데이트가 시스템에 설치되어 있지 않습니다.|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|업데이트 설치가 진행되고 있습니다.|
|**0x80cf0001**|OM_E_NO_SERVICE|에이전트에서 서비스를 제공할 수 없습니다.|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|서비스의 최대 용량을 초과했습니다.|
|**0x80cf0003**|OM_E_UNKNOWN_ID|ID를 찾을 수 없습니다.|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|개체를 초기화할 수 없습니다.|
|**0x80cf0007**|OM_E_INVALIDINDEX|컬렉션의 색인이 잘못되었습니다.|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|쿼리한 항목의 키를 찾을 수 없습니다.|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|충돌하는 작업이 진행되고 있었습니다. 다중 설치와 같은 일부 작업을 동시에 수행할 수 없습니다.|
|**0x80cf000B**|OM_E_CALL_CANCELLED|작업이 취소되었습니다.|
|**0x80cf000C**|OM_E_NOOP|필요한 작업이 없습니다.|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|에이전트가 업데이트의 XML 데이터에서 필요한 정보를 찾을 수 없습니다.|
|**0x80cf000E**|OM_E_XML_INVALID|에이전트가 업데이트의 XML 데이터에서 잘못된 정보를 찾았습니다.|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|메타데이터에서 순환 업데이트 관계가 감지되었습니다.|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|업데이트 관계의 중첩이 너무 깊어서 평가할 수 없습니다.|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|잘못된 업데이트 관계가 발견되었습니다.|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|잘못된 레지스트리 값을 읽었습니다.|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|작업이 목록에 중복된 항목을 추가하려고 했습니다.|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|호출자가 설치하도록 요청된 업데이트를 설치할 수 없습니다.|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|다른 설치가 진행되고 있는 동안 작업이 설치하려고 시도했거나 시스템이 필요한 다시 시작을 보류하고 있습니다.|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|적용할 수 있는 업데이트가 없어서 작업을 수행하지 못했습니다.|
|**0x80cf0018**|OM_E_NO_USERTOKEN|필요한 사용자 토큰이 없어서 작업이 실패했습니다.|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|배타적인 업데이트는 다른 업데이트와 동시에 설치할 수 없습니다.|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|정책 값이 설정되지 않았습니다.|
|**0x80cf001D**|OM_E_INVALID_UPDATE|업데이트에 잘못된 메타데이터가 포함되어 있습니다.|
|**0x80cf001E**|OM_E_SERVICE_STOP|서비스 또는 시스템이 종료되고 있어서 작업을 완료할 수 없습니다.|
|**0x80cf001F**|OM_E_NO_CONNECTION|네트워크 연결을 사용할 수 없어서 작업을 완료할 수 없습니다.|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|로그온한 대화형 사용자가 없어서 작업을 완료할 수 없습니다.|
|**0x80cf0021**|OM_E_TIME_OUT|시간이 초과되어 작업을 완료할 수 없습니다.|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|모든 업데이트에 대한 작업이 실패했습니다.|
|**0x80cf0024**|OM_E_NO_UPDATE|업데이트가 없습니다.|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|그룹 정책 설정으로 인해 Windows 업데이트에 액세스하지 못했습니다.|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|업데이트 형식이 잘못되었습니다.|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|요청이 WSUS 서버에서 나오지 않아서 업데이트를 제거할 수 없습니다.|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|검색에서 일부 업데이트를 놓쳤거나 시스템에 허가되지 않은 애플리케이션이 있을 수 있습니다.|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|원본이 필요하므로 델타 압축된 업데이트를 설치할 수 없습니다.|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|원본이 필요하므로 전체 파일 업데이트를 설치할 수 없습니다.|
|**0x80cf002E**|OM_E_WU_DISABLED|관리되지 않는 서버에는 액세스할 수 없습니다.|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|**DisableWindowsUpdateAccess** 정책이 설정되어 있어서 작업을 완료할 수 없습니다.|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|프록시 목록 형식이 잘못되었습니다.|
|**0x80cf0031**|OM_E_INVALID_FILE|파일의 형식이 잘못되었습니다.|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|검색 조건 문자열이 잘못되었습니다.|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|업데이트를 다운로드하지 못했습니다.|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|업데이트를 처리하지 못했습니다.|
|**0x80cf0036**|OM_E_INVALID_OPERATION|개체의 현재 상태에서 작업을 허용하지 않습니다.|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|작업이 지원되지 않습니다.|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|다운로드한 파일에 예기치 않은 콘텐츠 형식이 있습니다.|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|서버가 에이전트에 재동기화를 너무 많이 요청했습니다.|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|WUA UI를 지원하지 않습니다.|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|관리자만 컴퓨터별 업데이트에서 이 작업을 수행할 수 있습니다.|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|지원되지 않는 범위의 검색을 시도했습니다.|
|**0x80cf0046**|OM_E_BAD_FILE_URL|URL이 파일을 가리키지 않습니다.|
|**0x80cf0047**|OM_E_NOTSUPPORTED|요청한 작업이 지원되지 않습니다.|
|**0x80cf0049**|OM_E_OUTOFRANGE|데이터가 범위를 벗어났습니다.|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|데이터에 잘못된 버전이 있습니다.|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|검색 호출이 완료되었지만 일부 업데이트를 감지하지 못했습니다.|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|다운로드 호출이 완료되었지만 일부 업데이트를 감지하지 못했습니다.|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|설치 호출이 완료되었지만 일부 업데이트를 감지하지 못했습니다.|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|Windows 업데이트 캐시가 초기화되지 않아서 캐시가 비어 있습니다.|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|서버가 범주별 검색을 지원하지 않습니다. 전체 카탈로그 검색을 대신 발급해야 합니다.|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|서비스에 권한을 부여하는 데 문제가 있습니다.|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|엔드포인트에 대한 경로 또는 네트워크 연결이 없습니다.|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|수신한 데이터가 데이터 계약 예상을 충족하지 않습니다.|
|**0x80cf043A**|OM_E_PT_INVALID_URL|URL이 잘못되었습니다.|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|NWS 런타임을 로드할 수 없습니다.|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|프록시 인증 체계가 지원되지 않습니다.|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|요청된 서비스 속성을 사용할 수 없습니다.|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|엔드포인트 공급자 플러그 인을 사용하려면 온라인 새로 고침을 수행해야 합니다.|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|요청된 서비스 엔드포인트의 URL을 사용할 수 없습니다.|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|서비스 엔드포인트에 대한 연결이 종료되었습니다.|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|프로토콜 토커가 적절하지 않은 상태여서 작업이 잘못되었습니다.|
|**0x80cf0FFF**|OM_E_UNEXPECTED|다른 오류 코드로 설명되지 않는 이유 때문에 작업이 실패했습니다.|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|Windows Installer 버전이 3.1 이전이어서 검색이 일부 업데이트를 놓쳤을 수 있습니다.|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|Windows Installer가 구성되어 있지 않아서 검색이 일부 업데이트를 놓쳤을 수 있습니다.|
|**0x80cf1003**|OM_E_MSP_DISABLED|정책에서 Windows Installer 패치를 사용하지 않도록 설정하여 검색이 일부 업데이트를 놓쳤을 수 있습니다.|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|애플리케이션이 사용자별로 설치되어서 업데이트를 적용할 수 없습니다.|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|원격 프로세스를 사용할 수 없어서 원격 업데이트 처리기에 대한 요청을 완료할 수 없습니다.|
|**0x80cf2001**|OM_E_UH_LOCALONLY|처리기가 로컬 전용이어서 원격 업데이트 처리기에 대한 요청을 완료할 수 없습니다.|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|원격 업데이트 처리기가 이미 존재해서 원격 업데이트 처리기를 만들 수 없습니다.|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|업데이트에서 설치(제거)를 지원하지 않아서 업데이트를 설치(제거)하라는 처리기에 대한 요청을 완료할 수 없습니다.|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|잘못된 처리기가 지정되어서 작업을 완료할 수 없습니다.|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|업데이트에 잘못된 메타데이터가 포함되어 있어서 처리기 작업을 완료할 수 없습니다.|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|설치 관리자가 시간 제한을 초과해서 작업을 완료할 수 없습니다. 사용자의 상호 작용이 필요한 업데이트를 배포하도록 승인했는지 확인하십시오. 이런 경우 자동으로 설치하도록 업데이트 설치 매개 변수를 수정해야 합니다.|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|업데이트 처리기에서 수행하는 작업이 취소되었습니다.|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|처리기 관련 메타데이터가 잘못되어서 작업을 완료할 수 없습니다.|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|설치 관리자에서 업데이트를 하나 이상 설치(제거)하지 못했습니다.|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|다시 다운로드해야 해서 업데이트 처리기가 업데이트를 설치하지 못했습니다.|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|업데이트 처리기가 설치(제거) 작업의 상태에 대한 알림을 보내지 못했습니다.|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|업데이트의 다시 부팅 후 작업이 아직 진행되고 있습니다.|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|업데이트의 다시 부팅 후 작업의 결과를 확인할 수 없습니다.|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|다시 부팅 후 작업이 완료된 후 업데이트 상태가 예상치 못한 상태입니다.|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|이 업데이트를 다운로드하거나 설치하려면 먼저 운영 체제 서비스 스택을 업데이트해야 합니다.|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|콜백 설치 관리자가 오류로 인해 콜백되었습니다.|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|사용자 지정 설치 관리자 서명이 업데이트에 필요한 서명과 일치하지 않습니다.|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|설치 관리자에서 설치 구성을 지원하지 않습니다.|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|설치의 대상 세션이 잘못되었습니다.|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|업데이트 처리기 오류는 다른 OM_E_UH_&#42; 코드로 설명되지 않습니다.|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|비UI 모드에 있을 때 UI를 표시할 수 없습니다. Windows 업데이트 클라이언트 UI 모듈을 설치하지 못할 수 있습니다.|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|이 버전의 내보낸 WU 클라이언트 UI 기능은 지원되지 않습니다.|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|다른 OM_E_AUCLIENT_&#42; 오류 코드로 설명되지 않는 사용자 인터페이스 오류가 발생했습니다.|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|**SOAPCLIENT_SOAPFAULT**와 같습니다. **OM_E_PT_SOAP_&#42;** 오류 코드 유형의 SOAP 실패가 발생하여 SOAP 클라이언트가 실패했습니다.|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|**SOAPCLIENT_PARSEFAULT_ERROR**와 같습니다.  SOAP 클라이언트가 SOAP 실패 오류를 구문 분석하지 못했습니다.|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|**SOAPCLIENT_PARSE_ERROR**와 같습니다.  SOAP 클라이언트가 서버의 응답을 구문 분석하지 못했습니다.|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|**SOAP_E_VERSION_MISMATCH**와 같습니다. SOAP 클라이언트가 SOAP 봉투의 인식 불가능한 네임스페이스를 발견했습니다.|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|**SOAP_E_MUST_UNDERSTAND**와 같습니다. SOAP 클라이언트가 헤더를 해석할 수 없습니다.|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|**SOAP_E_CLIENT**와 같습니다. SOAP 클라이언트가 메시지 형식이 잘못되었다는 걸 발견했습니다. 다시 전송하기 전에 수정하십시오.|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|**SOAP_E_SERVER**와 같습니다. 서버 오류로 인해 SOAP 메시지를 처리할 수 없습니다. 나중에 다시 보내십시오.|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|서버에 대한 왕복 수가 최대 한계를 초과했습니다.|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|개체가 이미 초기화되어서 초기화하지 못했습니다.|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|컴퓨터 이름을 확인할 수 없습니다.|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|서버의 회신에 따르면 서버가 변경되었거나 쿠키가 잘못되었습니다. 내부 캐시를 새로 고치고 다시 시도하십시오.|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|**HTTP 상태 400**과 같습니다. 구문이 잘못되어서 서버가 요청을 처리할 수 없습니다.|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|**HTTP 상태 401**과 같습니다. 요청한 리소스를 사용하려면 사용자 인증이 필요합니다.|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|**HTTP 상태 403**과 같습니다. 서버가 요청을 인식했지만 수행을 거부했습니다.|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|**HTTP 상태 404**와 같습니다. 서버가 요청된 URI(Uniform Resource Identifier)를 찾을 수 없습니다.|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|**HTTP 상태 405**와 같습니다. HTTP 메서드가 허용되지 않습니다.|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|**HTTP 상태 407**과 같습니다. 프록시 인증이 필요합니다.|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|**HTTP 상태 408**과 같습니다. 서버가 요청을 기다리는 동안 시간이 초과되었습니다.|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|**HTTP 상태 409**와 같습니다. 리소스의 현재 상태와 충돌이 발생하여 요청을 완료하지 못했습니다.|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|**HTTP 상태 410**과 같습니다. 서버에서 요청된 리소스를 더 이상 사용할 수 없습니다.|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|**HTTP 상태 500**과 같습니다. 서버의 내부 오류로 인해 요청을 수행하지 못했습니다.|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|**HTTP 상태 500**과 같습니다. 서버가 요청을 처리하는 데 필요한 기능을 지원하지 않습니다.|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|**HTTP 상태 502**와 같습니다. 게이트웨이 또는 프록시 역할을 하는 서버가 요청을 처리하려고 하는 동안 액세스한 업스트림 서버에서 잘못된 응답을 받았습니다.|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|**HTTP 상태 503**과 같습니다. 서비스가 일시적으로 오버로드됩니다.|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|**HTTP 상태 503**과 같습니다. 게이트웨이를 대기하는 동안 요청의 시간이 초과되었습니다.|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|**HTTP 상태 505**와 같습니다. 서버가 요청에 사용되는 HTTP 프로토콜 버전을 지원하지 않습니다.|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|파일 위치가 변경되어서 작업이 실패했습니다. 내부 상태를 새로 고치고 다시 보내십시오.|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|서버가 빈 인증 정보 목록을 반환했습니다.|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|에이전트가 올바른 인증 쿠키를 만들 수 없습니다.|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|구성 속성 값이 잘못되었습니다.|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|구성 속성 값이 누락되었습니다.|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|HTTP 요청을 완료하지 못했으며 그 원인이 **OM_E_PT_HTTP_&#42;** 오류 코드 중 어느 오류에도 해당하지 않습니다.|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|**ERROR_WINHTTP_NAME_NOT_RESOLVED**와 같습니다. 프록시 서버 또는 대상 서버 이름을 확인할 수 없습니다.|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|외부 .cab 파일 처리가 완료되었지만 몇 가지 오류를 반환했습니다.|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|외부.cab 프로세서 초기화가 완료되지 않았습니다.|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|메타데이터 파일의 형식이 잘못되었습니다.|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|외부 cab 프로세서가 잘못된 메타데이터를 발견했습니다.|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|외부 .cab 파일에서 파일 다이제스트를 추출할 수 없습니다.|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|외부.cab 파일에서 압축을 풀 수 없습니다.|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|외부 cab 프로세서가 파일 위치를 가져올 수 없습니다.|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|다른 **OM_E_PT_&#42;** 오류 코드로 설명되지 않는 통신 오류가 발생했습니다.|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|요청된 파일에 URL이 없어서 다운로드 관리자 작업을 완료할 수 없습니다.|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|파일 다이제스트를 인식할 수 없어서 다운로드 관리자 작업을 완료할 수 없습니다.|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|파일 메타데이터가 인식할 수 없는 해시 알고리즘을 요청해서 다운로드 관리자 작업을 완료할 수 없습니다.|
|**0x80cf6005**|OM_E_DM_NONETWORK|네트워크 연결을 사용할 수 없어서 다운로드 관리자 작업을 완료할 수 없습니다.|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|업데이트가 다운로드되지 않았습니다.|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|다운로드 관리자가 BITS(Background Intelligent Transfer Service)에 연결할 수 없어서 다운로드 관리자 작업이 실패했습니다.|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|지정되지 않은 BITS(Background Intelligent Transfer Service) 전송 오류가 발생하여 다운로드 관리자 작업이 실패했습니다.|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|다운로드 출처 위치가 변경되어서 다운로드를 다시 시작해야 합니다.|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|업데이트 콘텐츠가 새로운 버전으로 변경되어서 다운로드를 다시 시작해야 합니다.|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|다른 **OM_E_DM_&#42;** 오류 코드로 설명되지 않는 다운로드 관리자 오류가 발생했습니다.|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|잘못된 이벤트 페이로드가 지정되었습니다.|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|제출된 이벤트 페이로드의 크기가 잘못되었습니다.|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|서비스가 등록되지 않았습니다.|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|에이전트가 종료되고 있어서 작업이 실패했습니다.|
|**0x80cf8001**|OM_E_DS_INUSE|데이터 저장소가 사용 중이어서 작업이 실패했습니다.|
|**0x80cf8002**|OM_E_DS_INVALID|데이터 저장소의 현재 상태와 예상 상태가 일치하지 않습니다.|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|데이터 저장소에 테이블이 없습니다.|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|데이터 저장소에 예상치 못한 열이 포함된 테이블이 있습니다.|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|테이블이 데이터 저장소에 없어서 테이블을 열 수 없습니다.|
|**0x80cf8006**|OM_E_DS_BADVERSION|데이터 저장소의 현재 버전과 예상 버전이 일치하지 않습니다.|
|**0x80cf8007**|OM_E_DS_NODATA|요청된 정보가 데이터 저장소에 없습니다.|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|데이터 저장소에 필수 정보가 없거나 Null이 아닌 값이 필요한 테이블 열에 Null 값이 있습니다.|
|**0x80cf8009**|OM_E_DS_MISSINGREF|데이터 저장소에 필수 정보가 없거나 존재하지 않는 사용 조건, 파일, 지역화된 속성 또는 링크된 행에 대한 참조가 있습니다.|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|업데이트 처리기가 인식되지 않아서 업데이트가 처리되지 않았습니다.|
|**0x80cf800B**|OM_E_DS_CANTDELETE|하나 이상의 서비스에서 참조되고 있어서 업데이트를 삭제할 수 없습니다.|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|할당된 시간 내에 데이터 저장소 섹션을 잠글 수 없습니다.|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|기존 행에 동일한 기본 키가 있어서 행이 추가되지 않았습니다.|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|데이터 저장소가 다른 프로세스에 의해 잠겨 있어서 해당 데이터 저장소를 초기화할 수 없습니다.|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|현재 프로세스에서 데이터 저장소를 COM에 등록할 수 없습니다.|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|작업이 다른 프로세스에서 데이터 저장소 개체를 만들 수 없습니다.|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|서버가 두 개의 다른 버전 ID를 가진 동일한 업데이트를 클라이언트에 보냈습니다.|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|서비스가 데이터 저장소에 없어서 작업을 완료할 수 없습니다.|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|서비스 등록이 만료되어서 작업을 완료할 수 없습니다.|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|필수 업데이트이거나 마감일이 지정된 상태로 배포되어서 업데이트를 숨기는 요청이 거부되었습니다.|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|세션과 연결되어 있지 않아서 테이블을 닫지 못했습니다.|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|세션과 연결되어 있지 않아서 테이블을 닫지 못했습니다.|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|기본 제공되는 서비스이거나 자동 업데이트가 다른 서비스로 대체될 수 없어서 서비스를 제거하거나 등록 취소하는 요청이 거부되었습니다.|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|작업이 허용되지 않아서 요청이 거부되었습니다.|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|현재 데이터 저장소의 체계와 백업 XML 문서의 테이블 체계가 일치하지 않습니다.|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|데이터 저장소를 사용하려면 세션을 다시 설정해야 합니다. 세션을 해제하고 새로운 세션으로 다시 시도하십시오.|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|가장된 ID로 요청되어서 데이터 저장소 작업을 완료할 수 없습니다.|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|다른 **OM_E_DS_&#42;** 코드로 설명되지 않는 데이터 저장소 오류가 발생했습니다.|
|**0x80cfA000**|OM_E_AU_NOSERVICE|자동 업데이트가 들어오는 요청을 처리할 수 없습니다.|
|**0x80cfA004**|OM_E_AU_PAUSED|일시 중지된 상태여서 자동 업데이트가 들어오는 요청을 처리할 수 없습니다.|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|자동 업데이트에 등록된 관리되지 않는 서비스가 없습니다.|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|자동 업데이트에 등록된 기본 서비스가 검색 중 변경되었습니다.|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|자동 업데이트에서 다시 시작하라는 메시지를 이미 사용자에게 표시했습니다.|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|다른 **OM_E_AU &#42;** 코드에서 다루지 않는 자동 업데이트 오류가 발생했습니다.|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|식이 인식되지 않아서 식 계산기 작업을 완료할 수 없습니다.|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|식이 잘못되어서 식 계산기 작업을 완료할 수 없습니다.|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|식에 잘못된 개수의 메타데이터 노드가 포함되어 있어서 식 계산기 작업을 완료할 수 없습니다.|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|직렬화된 식 데이터의 버전이 잘못되어서 식 계산기 작업을 완료할 수 없습니다.|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|식 계산기를 초기화할 수 없습니다.|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|특성이 잘못되어서 식 계산기 작업을 완료할 수 없습니다.|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|컴퓨터의 클러스터 상태를 확인할 수 없어서 식 계산기 작업을 완료할 수 없습니다.|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|다른 **OM_E_EE_&#42;** 오류 코드에서 다루지 않는 식 계산기 오류가 발생했습니다.|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|이벤트 캐시 파일이 손상되었습니다.|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|이벤트 네임스페이스 설명자의 XML을 구문 분석할 수 없습니다.|
|**0x80cfF003**|OM_E_INVALID_EVENT|이벤트 네임스페이스 설명자의 XML이 잘못되었습니다.|
|**0x80cfF004**|OM_E_SERVER_BUSY|서버 사용량이 많아서 서버가 이벤트를 거부했습니다.|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|다른 오류 코드로 설명할 수 없는 보고서 오류가 발생했습니다.|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|필요한 컴퓨터 다시 시작이 보류 중이어서 설치에 실패했습니다.|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|다운로드가 취소되었습니다.|

## <a name="windows-7-based-computers-with-lots-of-superseded-updates-stop-reporting-to-the-microsoft-intune-console"></a>다수의 대체된 업데이트를 포함하는 Windows 7 기반 컴퓨터에서 Microsoft Intune 콘솔에 대한 보고가 중지됨
**문제**: Microsoft Intune 클라이언트에 다음과 같은 증상이 하나 이상 나타나는 상황이 발생할 수 있습니다.
- Microsoft 관리 콘솔에 대한 보고가 갑자기 중단됩니다.  
- CPU 사용률이 높아집니다.
- Intune 포털을 통해 설치하는 경우, 애플리케이션이 느리게 설치됩니다.
- Microsoft Intune Center에서 다음과 같은 오류가 트리거됩니다. *컴퓨터를 업데이트하는 동안 오류가 발생했습니다. 발견된 오류: 코드 0x800705b4*.
- Intune 관리 콘솔 &gt; 그룹 &gt; 모든 디바이스 아래 상태 필드에 다음 메시지가 표시됩니다. *이 컴퓨터에 설치된 하나 이상의 에이전트에서 오류가 발생했습니다. 이 컴퓨터에 대한 정보는 정확하지 않거나 최신 상태가 아닐 수 있습니다*.

이 문제는 대체된 업데이트(다른 업데이트에 의해 대체된 업데이트)가 오랜 기간 동안 거부되지 않은 경우에 발생할 수 있습니다. 특정한 프로세스(예: 애플리케이션 설치)가 진행되는 동안, Windows는 업데이트 및 그 후속 작업이 올바르게 매핑될 수 있도록, 대체된 모든 업데이트를 순서대로 확인합니다. 대체된 업데이트 목록이 너무 커지면, 이러한 확인 작업에 필요한 시간 및 처리 부하로 인해 CPU 사용률이 높아질 수 있습니다. 이 문제는 Windows 7에 제공되는 대체된 업데이트의 수가 많기 때문에 주로 Windows 7을 실행하는 클라이언트에 영향을 미칩니다. Windows 8 이상의 운영 체제에는 대체된 업데이트가 그만큼 많지 않기 때문에 이러한 문제의 영향을 덜 받습니다.

**해결 방법**:  
1. [Azure Portal](https://portal.azure.com)에 로그인하고 **Microsoft Intune**을 엽니다. 
2. **소프트웨어 업데이트**를 선택합니다.
3. Windows 7 또는 영향을 받는 클라이언트에 설치된 애플리케이션(예: Microsoft Office)에 적용될만한 대체되는 업데이트를 모두 거부합니다.
4. 영향을 받는 클라이언트를 다시 시작합니다.

또한 Windows 7을 실행하는 경우, 다음 업데이트를 반드시 설치해야 합니다. [3050265 Windows Update Client for Windows 7: June 2015](https://support.microsoft.com/kb/3050265)

### <a name="next-steps"></a>다음 단계
이 정보가 도움이 되지 않으면 [Microsoft Intune에 대한 지원을 받을](get-support.md) 수도 있습니다.
