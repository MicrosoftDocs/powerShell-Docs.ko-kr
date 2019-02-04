---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680783"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="88cc5-102">LCM 상태에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="88cc5-102">Detailed information about LCM state</span></span>

<span data-ttu-id="88cc5-103">LCM 상태에 대한 세부 정보를 노출하는 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88cc5-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="88cc5-104">이제 Get-DscLocalConfigurationManager에서 반환되는 LCMState에 다음과 같은 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cc5-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="88cc5-105">**유휴 상태**</span><span class="sxs-lookup"><span data-stu-id="88cc5-105">**Idle**</span></span>
* <span data-ttu-id="88cc5-106">**사용 중**</span><span class="sxs-lookup"><span data-stu-id="88cc5-106">**Busy**</span></span>
* <span data-ttu-id="88cc5-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="88cc5-107">**PendingReboot**</span></span>
* <span data-ttu-id="88cc5-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="88cc5-108">**PendingConfiguration**</span></span>

<span data-ttu-id="88cc5-109">또한 상태에 대한 자세한 정보를 포함하는 LCMStateDetail 속성이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88cc5-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
