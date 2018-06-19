---
title: Microsoft Intune 용어
titleSuffix: Microsoft Intune
description: Microsoft Intune에서 사용되는 용어의 의미에 대해 알아봅니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 07/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
ms.custom: intune-azure
ms.openlocfilehash: 2b59ed38329462ad8d8db604979c8eb725f7973a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31026655"
---
# <a name="microsoft-intune-glossary"></a>Microsoft Intune 용어
Microsoft Intune에서 사용되는 일반적인 용어의 정의에 대해 알아봅니다.

## <a name="a"></a>A

|||
|-|-|
|앱 할당|사용자가 필요한 앱을 [찾고 다운로드하고 설치](/intune/app-management)할 수 있도록 하는 과정입니다. 이전 명칭은 *앱 배포*였습니다.|
|앱 구성 프로필 <br/><br/>앱 구성 정책|공급업체별 구성이 있는 모바일 앱에 사용 가능합니다. [iOS](/intune/app-configuration-policies-use-ios) or [Android](/intune/app-configuration-policies-use-android) 앱을 실행하기 전에 특정 설정을 사용하여 앱을 구성합니다.|
|앱 모니터링|앱 할당과 관련된 [최근 상태 및 활동을 검토](/intune/apps-monitor)할 수 있는 작업입니다.|
|앱 보호 데이터 제거 작업|사용자의 장치에서 [앱 데이터를 제거](/intune/app-protection-policies)합니다.|
|앱 보호 정책|EMS(Enterprise Mobility + Security) 기술과 통합된 모바일 앱에 사용 가능합니다. 사용자의 앱이 [회사 데이터 보호 정책](/intune/app-protection-policies)을 준수하는지를 확인합니다.|
|앱 SDK|[Microsoft Intune 앱 SDK](/intune/app-sdk)를 사용하면 사내에서 작성된 앱에 Intune 앱 보호 정책으로 해당 앱을 관리할 수 있는 기능을 추가할 수 있습니다.|
|앱 제거 작업|사용자의 장치에서 [앱을 제거](/intune/apps-deploy)할 수 있는 작업입니다.|
|앱 래핑 도구|Intune 앱 보호 정책을 통해 앱을 관리할 수 있도록 기간 업무 앱을 둘러싸는 래퍼를 만드는 [명령줄 응용 프로그램](/intune/apps-prepare-mobile-application-management)입니다.|
|할당 작업|[앱을 할당](/intune/apps-deploy)할 때 할 수 있는 선택입니다. 앱 설치를 필수 또는 선택 사항으로 설정하거나 앱을 제거할 수 있습니다.|
|사용 가능한 설치|이 작업을 통해 앱을 할당하면 앱이 회사 포털에 표시되어 사용자가 [요청 시 앱을 설치](/intune/apps-deploy)할 수 있습니다.|
|Azure 포털|Intune용 새 콘솔입니다. [자세한 내용을 확인해 보세요](/intune/what-is-intune).|

## <a name="b"></a>B

|||
|-|-|
|BYOD|[Bring Your Own Device](/intune/device-enrollment)를 의미합니다. 사용자가 자신의 장치에 Intune 회사 포털 앱을 설치한 후 메일, 회사 앱, 회사 데이터 및 지원과 같은 회사 리소스에 액세스할 수 있습니다.|

## <a name="c"></a>C

|||
|-|-|
|인증서 프로필|Wi-Fi, 메일 또는 VPN 프로필을 사용할 경우 이 정책 형식을 사용하여 인증서를 통해 [회사 리소스에 대한 액세스를 보호](/intune/certificates-configure)합니다.|
|COD|[회사 소유 장치](/intune/device-enrollment)는 조직의 요구 사항과 관리하는 장치의 유형에 따라 다양한 방법으로 등록될 수 있습니다.|
|회사 포털|사용자에게 [회사 데이터 및 앱에 대한 액세스](/intune/company-portal-customize)를 제공하는 앱 또는 웹 사이트입니다.|
|준수 정책|장치가 PIN을 사용하여 장치에 액세스, 장치에 저장된 데이터의 암호화 등 [특정 규칙을 준수](/intune/device-compliance)하는지 확인합니다.|
|규격 및 비규격 앱|[장치 제한 프로필](/intune/device-restrictions-configure)의 일부로, 이러한 설정을 통해 사용자가 실행하거나 실행할 수 없는 앱의 목록을 정의할 수 있습니다. 그러면 Intune은 비규격 앱이 설치되거나 실행되었음을 보고서를 통해 알립니다. 일부 플랫폼의 경우 Intune에서 비규격 앱의 설치를 차단할 수도 있습니다.|
|조건부 액세스|설정한 규칙을 준수하는 장치에서만 [회사 메일, Office 365 및 기타 서비스에 액세스할 수 있도록 허용](/intune/conditional-access)합니다.|
|사용자 지정 정책|일반 구성 정책에 요구 사항을 충족하는 기본 제공 설정이 포함되지 않은 경우 [이러한 정책을 사용](/intune/custom-settings-configure)합니다. 사용자 지정 정책을 사용하여 Apple Configurator 또는 OMA-URI와 같은 다른 방법으로 설정을 만들 수 있습니다.|

## <a name="d"></a>D

|||
|-|-|
|배포|관리하는 장치 또는 사용자에게 앱 또는 정책을 보내는 동작입니다. 이 작업의 현재 명칭은 *할당*입니다.|
|장치 등록 관리자|조직에서는 Intune을 사용하여 단일 사용자 계정으로 많은 수의 모바일 장치를 관리할 수 있습니다. [DEM(장치 등록 관리자) 계정](/intune/device-enrollment-program-enroll-ios)은 장치를 최대 1,000개 등록할 수 있는 특수한 Intune 계정입니다.|
|장치 프로필|[이러한 프로필](/intune/device-profile-create)을 사용하면 관리하는 장치에서 광범위한 보안, 기능 및 액세스 설정을 구성할 수 있습니다.|

## <a name="e"></a>E

|||
|-|-|
|전자 메일 프로필|이 정책을 사용하여 모바일 장치에서 [전자 메일 액세스 설정](/intune/email-settings-configure)을 지정하여 최종 사용자가 수행해야 하는 설정의 양을 최소화할 수 있습니다.|
|EMS|Microsoft Enterprise Mobility + Security(이전의 Enterprise Mobility Suite)는 사용자가 [필요한 앱 및 콘텐츠에 액세스](https://www.microsoft.com/cloud-platform/enterprise-mobility)할 수 있도록 하면서 회사 데이터를 계속 보호해 줍니다.|
|최종 사용자|Intune을 사용하여 관리되는 [휴대폰 및 PC와 같은 장치의 사용자](/intune/end-user-educate)입니다.|
|등록|Microsoft Intune에서는 [등록](/intune/device-enrollment)을 사용하여 장치를 관리하며 리소스에 대한 액세스를 허용합니다.|

## <a name="f"></a>F

|||
|-|-|
|FastTrack|적격 플랜에 150개의 라이선스가 포함된 Intune 사용자에 대한 [Microsoft 서비스](https://technet.microsoft.com/library/mt228265.aspx)입니다. 이 서비스를 사용하여 Microsoft 전문가는 Intune을 시작 및 실행하기 위해 관리자와 협력할 수 있습니다.|

## <a name="g"></a>G

|||
|-|-|
|Groups|그룹을 사용하면 [사용자 또는 장치를 논리적으로 함께 수집](/intune/groups-get-started)할 수 있습니다. 예를 들어 모든 Windows PC가 포함된 그룹을 만들 수 있습니다. 그런 다음 이러한 그룹에 앱과 프로필을 할당할 수 있습니다.|

## <a name="h"></a>H

|||
|-|-|
|하이브리드|System Center Configuration Manager 콘솔을 통해 Intune에 등록된 장치를 관리할 수 있는 구성입니다.|

## <a name="i"></a>I

|||
|-|-|
|Azure 포털|대부분의 Intune 관리 작업에 사용하는 Azure Portal입니다.|
|Intune 소프트웨어 클라이언트|사용할 방법 결정을 돕기 위한 [일부 Windows PC 관리](/intune-classic/get-started/choose-how-to-manage-devices)의 또 다른 방법입니다.|
|Intune 소프트웨어 게시자|[배포할 앱을 정의하고 이러한 앱을 클라우드 저장소 공간에 업로드](/intune-classic/deploy-use/add-apps)하는 데 사용하는 도구입니다.|
|재고|관리하는 장치의 [하드웨어 및 설치된 소프트웨어](/intune/device-inventory)를 확인하는 데 사용합니다.|

## <a name="k"></a>K

|||
|-|-|
|키오스크 모드|[장치 제한 프로필](/intune/device-restrictions-configure)의 일부로 구성된 이 모드를 사용하여 장치를 잠글 수 있습니다. 예를 들어 일부앱만 실행될 수 있도록 소매용 장치를 구성할 수 있습니다.|

## <a name="m"></a>M

|||
|-|-|
|Managed Browser|Intune을 사용하여 조직에서 할당할 수 있는 [웹 브라우징 응용 프로그램](/intune/app-configuration-managed-browser)입니다. 관리 브라우저 정책은 관리 브라우저의 사용자가 방문할 수 있는 웹 사이트를 제한하는 허용 목록 또는 차단 목록을 구성합니다.|
|MDM 기관|[MDM 기관](/intune/mdm-authority-set)은 일련의 장치를 관리할 권한을 가진 관리 서비스를 정의합니다. MDM 기관에 대한 옵션에는 Intune 자체 및 Intune을 사용하는 Configuration Manager가 포함됩니다.|
|모바일 앱 구성 정책|공급업체별 구성이 있는 모바일 앱에 사용 가능합니다. 예를 들어, 호환되는 앱이 실행될 때 회사 이름, 서버 주소 등의 설정을 해당 앱에 제공하는 데 사용되는 [iOS](/intune/app-configuration-policies-use-ios) 또는 [Android](/intune/app-configuration-policies-use-android) 정책입니다.|
|모바일 앱 프로비전 정책|할당하는 iOS 앱에 대한 [프로비전 프로필](/intune/app-provisioning-profile-ios)이 만료되지 않게 하는 iOS 정책입니다.|
|모바일 응용 프로그램 관리|[MAM(모바일 응용 프로그램 관리)](/intune/app-lifecycle)을 사용하여 사용자를 위해 모바일 앱을 게시, 푸시, 구성, 보호, 모니터링 및 업데이트할 수 있습니다.
|모바일 장치 관리|[MDM(모바일 장치 관리)](/intune/device-lifecycle)을 사용하면 장치를 프로비저닝, 구성, 모니터링 및 관리할 수 있도록 Intune에 해당 장치를 등록할 수 있습니다.



## <a name="o"></a>O

|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management를 의미합니다. 많은 하드웨어 제조업체에서 모바일 장치 및 PC의 기능을 제어할 수 있도록 하는 사용되는 업계 표준 장치 관리 프로토콜입니다.|
|OMA URI|Open Mobile Alliance Uniform Resource Identifier를 의미합니다. 이러한 항목은 OMA-DM 표준을 준수하는 개별 장치 설정을 식별합니다. 요구 사항을 충족하는 기본 제공 설정이 없는 경우 [Intune 사용자 지정 프로필](/intune/custom-settings-configure)에서 이러한 설정을 사용할 수 있습니다.|

## <a name="p"></a>P

|||
|-|-|
|암호 재설정|지원되는 장치에서 강제로 최종 사용자가 [암호를 재설정](/intune/device-passcode-reset)하도록 하는 Intune 기능입니다.|

## <a name="r"></a>R

|||
|-|-|
|원격 잠금|지원되는 장치를 가지고 있지 않더라도 [해당 장치를 잠글](/intune/device-remote-lock) 수 있는 Intune 기능입니다.|
|필수 설치|이 작업을 사용하여 앱을 할당하면 [사용자 간섭](/intune/apps-deploy) 없이도 설치를 완료할 수 있습니다. 플랫폼에 따라서는 사용자가 설치를 수락해야 할 수도 있습니다.|


## <a name="s"></a>S

|||
|-|-|
|선택적 초기화|[선택적 초기화](/intune/device-company-data-remove)는 앱 보호 정책을 통해 보호되는 설정 및 메일 프로필을 비롯한 회사 데이터만 장치에서 제거합니다. 선택적 초기화는 사용자의 개인적인 데이터를 장치에 남겨둡니다.|
|테스트용 로드|앱 스토어에서 기간 업무 앱에 액세스하지 않고 해당 앱을 설치하는 작업입니다.|
|구독|Intune 테넌트에 액세스하는 데 사용되는, 직접 입력한 계약입니다.|

## <a name="t"></a>T

|||
|-|-|
|TeamViewer|Intune으로 관리하는 Android 장치에 [원격 지원 기능](/intune/device-profile-android-teamviewer)을 제공하기 위해 Intune과 연동되는 타사 응용 프로그램입니다.|
|테넌트|구독을 통해 액세스할 수 있는 Intune 서비스의 단일 인스턴스입니다.|
|Terms and conditions|사용자가 회사 포털을 사용하여 등록하고 작업에 액세스하기 전에 먼저 [읽고 동의](/intune/terms-and-conditions-create)해야 하는 정보를 포한, 사용자에게 할당할 정책 형식입니다.|

## <a name="v"></a>V

|||
|-|-|
|대량 구매 앱 및 전자책|일부 앱 스토어는 회사에서 사용하려는 앱이나 전자책의 라이선스를 여러 개 구매하는 기능을 제공합니다. Intune에서는 [이러한 프로그램을 통해 구매](/intune/vpp-apps)한 앱과 전자책을 관리할 수 있습니다. 앱 스토어에서 라이선스 정보를 가져오고, 사용한 라이선스 수를 추적하고, 소유한 앱 복사본 수를 초과하여 설치하지 않도록 할 수 있습니다.|
|VPN 프로필|관리하는 장치에 [VPN 설정](/intune/vpn-settings-configure)을 할당하여 최종 사용자에게 필요한 설정을 최소화하는 정책입니다.|

## <a name="w"></a>W

|               |                                                                                                                                                                                                 |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Wi-Fi 프로필 | 사용자가 설정을 알거나 구성할 필요 없이 회사 네트워크에 연결할 수 있도록 장치에 [무선 네트워크 설정](/intune/wi-fi-settings-configure)을 할당하는 정책입니다. |

