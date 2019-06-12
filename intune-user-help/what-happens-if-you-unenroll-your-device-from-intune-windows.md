---
title: Windows 디바이스 등록을 취소하면 어떻게 되나요? | Microsoft 문서
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c28d5b122bda537d4707bc0fdc2bfc74bcb823a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "55847287"
---
# <a name="what-happens-if-you-unenroll-your-windows-device-from-intune"></a>Intune에서 Windows 디바이스 등록을 취소하면 어떻게 되나요?

**이 문서의 내용**에서 이 페이지의 오른쪽에 있는 링크를 사용하여 사용 중인 디바이스 유형에 대한 정보를 찾을 수 있습니다.


## <a name="windows-10-windows-81-windows-8-windows-7-windows-vista"></a>Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista

-   디바이스가 더 이상 회사 포털에 나타나지 않으며 회사 포털에서 앱을 설치할 수 없습니다.

-   Intune 클라이언트 소프트웨어를 설치한 경우 컴퓨터에서 제거됩니다.

-   Intune Endpoint Protection 소프트웨어가 컴퓨터에서 제거됩니다. 컴퓨터에 다른 바이러스 방지 소프트웨어가 설치되어 있지만 사용되지 않도록 설정된 경우, Intune Endpoint Protection을 제거하면 이 응용 프로그램이 다시 사용되도록 설정될 수 있습니다. 회사 포털에서 컴퓨터를 제거한 후 해당 컴퓨터를 확인합니다.

    > [!IMPORTANT]
    > 다른 바이러스 방지 소프트웨어가 다시 사용되도록 설정되지 않거나 다른 바이러스 방지 소프트웨어가 설치되어 있지 않은 경우 컴퓨터는 바이러스 및 맬웨어 공격에 취약해질 수 있습니다.

-   디바이스를 추가할 때 디바이스에서 변경된 모든 설정(예: 카메라 사용 안 함)이 더 이상 적용되지 않습니다.

-   컴퓨터가 Intune 서비스로부터 더 이상 자동 소프트웨어 업데이트 또는 바이러스 백신 소프트웨어 업데이트를 받지 못합니다. 그러나 컴퓨터가 설정된 방식에 따라 Windows Server Update Services, Windows 업데이트 또는 Microsoft 업데이트를 사용하여 업데이트를 계속 받을 수 있습니다.

또한 Windows 8.1의 경우

-   디바이스에서 더 이상 회사 앱 및 회사 데이터를 사용할 수 없습니다.

-   Windows 메일과 같은 일부 메일 앱에서 더 이상 디바이스에 저장된 회사 메일에 액세스할 수 없습니다.

-   Wi-Fi 또는 VPN(가상 프라이빗 네트워크)을 사용하여 회사 네트워크에 연결할 수 없습니다.

-   디바이스에서 더 이상 일부 회사 리소스(예: 파일 공유 또는 내부 웹 사이트)에 액세스하지 못할 수 있습니다.

## <a name="windows-10-mobile-and-windows-phone-81"></a>Windows 10 Mobile 및 Windows Phone 8.1

-   회사 포털 앱이 디바이스에서 제거됩니다. 즉, 디바이스가 더 이상 회사 포털에 나타나지 않으며 회사 포털 앱 또는 회사 포털 웹 사이트에서 앱을 설치할 수 없습니다.

-   디바이스에서 더 이상 회사 앱 및 회사 데이터를 사용할 수 없습니다.

-   디바이스를 추가할 때 디바이스에서 변경된 모든 설정(예: 카메라 사용 안 함 또는 특정 암호 길이 요구)이 더 이상 적용되지 않습니다.

    > [!IMPORTANT]
    > 유일한 예외는 암호화 정책이며, 이 정책은 여전히 적용됩니다. 회사 정책에서 Windows Phone의 암호화를 요구하는 경우 휴대폰을 암호 해제하는 유일한 방법은 **설정** 메뉴를 사용하는 것입니다.

## <a name="windows-rt-running-windows-81"></a>Windows 8.1을 실행하는 Windows RT

-   회사 포털 앱이 디바이스에서 제거됩니다. 즉, 디바이스가 더 이상 회사 포털에 나타나지 않으며 회사 포털에서 앱을 설치할 수 없습니다.

-   디바이스에서 더 이상 회사 앱 및 회사 데이터를 사용할 수 없습니다.

-   디바이스를 추가할 때 디바이스에서 변경된 모든 설정(예: 카메라 사용 안 함 또는 특정 암호 길이 요구)이 더 이상 적용되지 않습니다.

-   더 이상 Wi-Fi 또는 VPN(가상 프라이빗 네트워크)을 사용하여 회사 네트워크에 연결할 수 없습니다.

-   디바이스에서 더 이상 일부 회사 리소스(예: 파일 공유 또는 내부 웹 사이트)에 액세스하지 못할 수 있습니다.

-   Windows 메일과 같은 일부 메일 앱에서 더 이상 디바이스에 저장된 회사 메일에 액세스할 수 없습니다.

Windows RT 디바이스를 제거하면 다음과 같은 상황이 발생합니다.

-   회사 포털 앱이 디바이스에서 제거됩니다. 즉, 디바이스가 더 이상 회사 포털에 나타나지 않으며 회사 포털에서 앱을 설치할 수 없습니다.

-   디바이스에서 더 이상 회사 앱 및 회사 데이터를 사용할 수 없습니다.

-   디바이스를 추가할 때 디바이스에서 변경된 모든 설정(예: 카메라 사용 안 함 또는 특정 암호 길이 요구)이 더 이상 적용되지 않습니다.

질문이 있다면 회사 지원팀에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
