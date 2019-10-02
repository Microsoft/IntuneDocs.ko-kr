---
title: 출시 통신 계획 개발
titleSuffix: Microsoft Intune
description: 이 아티클은 Microsoft Intune 배포에 대한 출시 통신 계획을 개발하는 데 도움이 됩니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/30/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 393ebe75-d001-485a-b81c-6361c8b5e6ee
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1882a9d196cd9877cde37e9d7ef280b718b470cb
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727391"
---
# <a name="develop-a-rollout-communication-plan"></a>출시 통신 계획 개발

올바른 변경 관리에는 예정된 변경에 대한 명확하고 유용한 통신이 필요합니다. 원활한 Intune 배포를 위해 출시 통신 계획에는 다음 네 가지 영역이 포함되어야 합니다.

- 전달할 정보

- 통신에 사용되는 배달 방법

- 통신 수신 대상

- 통신 타임라인

각 영역을 더 자세히 살펴보겠습니다.

## <a name="what-needs-to-be-communicated"></a>통신을 통해 전달해야 하는 내용

전달할 정보는 통신 중인 Intune 출시 프로세스의 시기에 따라 결정됩니다. 웨이브(출시 프로세스 단계)에 따라 해당 조직 그룹 및 사용자와 통신할 수 있습니다. 먼저 Intune 출시 킥오프부터 시작하여 차례로 등록 전, 등록 후 통신을 수행합니다. 각 웨이브에서 전달될 수 있는 정보의 유형에 대해 살펴보겠습니다.

**킥오프 웨이브** <br/>Intune 프로젝트 자체를 소개하는 광범위한 통신입니다. Intune이란 무엇이고 왜 조직이 Intune을 채택하는지(조직 및 사용자에 대한 혜택)의 질문에 대답하고 배포 및 출시의 대략적인 계획을 제공해야 합니다.

**등록 전 웨이브**<br/> Intune에 대한 추가 정보, 보완 제공 사항(예: Office, Outlook, OneDrive), 사용자 리소스, 조직 그룹과 사용자가 Intune을 받기로 예약된 시기에 대한 구체적인 타임라인이 포함된 광범위 통신입니다.

**등록 웨이브**<br/> Intune을 수신하도록 예약된 조직 그룹 및 사용자를 대상으로 하는 통신입니다. 사용자에게 Intune을 수신할 준비가 되었음을 알리고 등록 지침과 지원을 받거나 질문을 하기 위한 연락처 정보를 제공해야 합니다.

**등록 후 웨이브**<br/> Intune에 등록한 조직 그룹 및 사용자를 대상으로 하는 통신입니다. 사용자에게 유용할 수 있는 추가 리소스를 제공하고 등록 중과 등록 후의 경험에 대한 피드백을 수집해야 합니다.

이 [Intune Adoption Kit](https://aka.ms/IntuneAdoptionKit)가 도움이 될 수 있습니다. 이 키트를 그대로 사용하거나 조직에 맞게 수정할 수 있습니다.

## <a name="communication-delivery-methods"></a>통신 배달 방법

대상 조직 그룹 및 사용자에게 Intune 출시 정보를 전달하는 데 사용할 수 있는 몇 가지 배달 방법이 있습니다. 다음 목록에는 몇 가지 예와 해당 방법과 함께 사용할 수 있는 웨이브가 나와 있습니다.

- 킥오프 웨이브에 사용되는 조직 전체의 개별 모임 또는 Microsoft Teams 회의

- 등록 전, 등록 및 등록 후 웨이브에 사용되는 전자 메일

- 모든 웨이브에 사용되는 조직 웹 사이트

- 킥오프 및 등록 전 웨이브에 사용되는 Yammer, 포스터 및 전단

## <a name="communications-timeline"></a>통신 타임라인

통신해야 하는 내용과 사용할 방법을 확인한 후 통신을 수신하는 시기와 대상을 포함하는 통신 타임라인을 결정합니다.

예를 들어 초기 Intune 프로젝트 킥오프 통신은 전체 조직 또는 하위 집합을 대상으로 할 수 있으며, Intune 출시가 시작되기 전에 몇 주에 걸쳐 수행될 수 있습니다. 그런 다음, 해당 Intune 출시 일정에 맞춰 조직 그룹 및 사용자에게 웨이브에 따라 정보를 전달할 수 있습니다. 아래 예는 개략적인 Intune 출시 통신 계획의 샘플입니다.

  | **통신 계획** | **7월** | **8월** | **9월** | **10월** |
|:---:|:---:|:---:|:---:|:---:|
| 웨이브 1  | 모두 |  |  |  |
| 킥오프 회의 | 첫째 주 |  |  |  |
| 웨이브 2 | IT | 영업 및 마케팅 | 소매 | HR, 재무 및 임원 |
| 출시 전 메일 1 | 첫째 주 | 첫째 주 | 첫째 주 | 첫째 주 |
| 웨이브 3 | IT | 영업 및 마케팅 | 소매 | HR, 재무 및 임원 |
| 출시 전 메일 2 | 둘째 주 | 둘째 주 | 둘째 주 | 둘째 주 |
| 웨이브 4 | IT | 영업 및 마케팅 | 소매 | HR, 재무 및 임원 |
| 등록 메일 | 셋째 주 | 셋째 주 | 셋째 주 | 셋째 주 |
| 웨이브 5 | IT | 영업 및 마케팅 | 소매 | HR, 재무 및 임원 |
| 등록 후 메일 | 넷째 주 | 넷째 주 | 넷째 주 | 넷째 주 |

[위 표의 템플릿을 다운로드](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)하여 통신 계획을 개발할 수 있습니다.

## <a name="next-step"></a>다음 단계

다음 섹션에서는 [지원 계획 개발](planning-guide-support-plan.md)에 대한 지침을 제공합니다.
