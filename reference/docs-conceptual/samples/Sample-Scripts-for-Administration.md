---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 시스템 관리용 샘플 스크립트
ms.openlocfilehash: 6b7e6d59bcbd8d30fd583102e326a8f394a4f9e6
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030800"
---
# <a name="sample-scripts-for-system-administration"></a><span data-ttu-id="b686b-103">시스템 관리용 샘플 스크립트</span><span class="sxs-lookup"><span data-stu-id="b686b-103">Sample scripts for system administration</span></span>

<span data-ttu-id="b686b-104">PowerShell의 기본적인 목표는 대화형 환경이나 스크립트에서 시스템을 쉽게 관리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b686b-104">The fundamental goal of PowerShell is providing easy administrative control over systems, either interactively or from script.</span></span> <span data-ttu-id="b686b-105">이 예제 컬렉션에서는 PowerShell을 사용하여 시스템을 관리하는 시나리오를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="b686b-105">This collection of examples walks through scenarios for administering systems with PowerShell.</span></span> <span data-ttu-id="b686b-106">이러한 예제를 나중에 스크립트에서 사용하거나 함수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b686b-106">The examples can be used from scripts or as functions later.</span></span>

<span data-ttu-id="b686b-107">이러한 예제는 cmdlet과 외부 도구를 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b686b-107">These examples use a mix of cmdlets and external tools.</span></span> <span data-ttu-id="b686b-108">외부 도구의 사용은 PowerShell의 장기적인 디자인 의도에 따른 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b686b-108">Use of external tools is part of the long-term design intent of PowerShell.</span></span> <span data-ttu-id="b686b-109">시스템까지 확장되면서 사용자는 사용 가능한 도구 집합으로 필요한 작업을 모두 수행할 수 없는 상황이 지속적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b686b-109">Even as the system grows, users continually encounter situations where the available toolsets don't do everything they need.</span></span> <span data-ttu-id="b686b-110">PowerShell 솔루션은 cmdlet 구현에만 의존하지 않고, 사용 가능한 외부 도구와의 통합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b686b-110">Rather than foster dependency solely on cmdlet implementations, PowerShell solutions support integration with available external tools.</span></span>
