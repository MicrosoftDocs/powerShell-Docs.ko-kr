---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 시스템 관리용 샘플 스크립트
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 3c771c9568f40ec3a4bb7061c122f33bba7d0382
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058219"
---
# <a name="sample-scripts-for-system-administration"></a><span data-ttu-id="dc2e8-103">시스템 관리용 샘플 스크립트</span><span class="sxs-lookup"><span data-stu-id="dc2e8-103">Sample scripts for system administration</span></span>

<span data-ttu-id="dc2e8-104">PowerShell의 기본적인 목표는 대화형 환경이나 스크립트에서 시스템을 쉽게 관리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-104">The fundamental goal of PowerShell is providing easy administrative control over systems, either interactively or from script.</span></span> <span data-ttu-id="dc2e8-105">이 예제 컬렉션에서는 PowerShell을 사용하여 시스템을 관리하는 시나리오를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-105">This collection of examples walks through scenarios for administering systems with PowerShell.</span></span> <span data-ttu-id="dc2e8-106">이러한 예제를 나중에 스크립트에서 사용하거나 함수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-106">The examples can be used from scripts or as functions later.</span></span>

<span data-ttu-id="dc2e8-107">이러한 예제는 cmdlet과 외부 도구를 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-107">These examples use a mix of cmdlets and external tools.</span></span> <span data-ttu-id="dc2e8-108">외부 도구의 사용은 PowerShell의 장기적인 디자인 의도에 따른 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-108">Use of external tools is part of the long-term design intent of PowerShell.</span></span> <span data-ttu-id="dc2e8-109">시스템까지 확장되면서 사용 가능한 도구 집합으로 필요한 작업을 모두 수행할 수 없는 상황이 지속적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-109">Even as the system grows, users continually encounter situations where the available toolsets do not do everything they need.</span></span> <span data-ttu-id="dc2e8-110">PowerShell은 cmdlet 구현에만 의존하지 않고, 사용 가능한 모든 도구와 솔루션을 통합하도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-110">Rather than foster dependency solely on cmdlet implementations, PowerShell support integrating solutions all available tools.</span></span>