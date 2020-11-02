---
ms.date: 06/12/2017
title: 목록에서 패키지 제거
description: PowerShell 갤러리에서는 사용자가 패키지를 영구적으로 삭제할 수 없습니다. 따라서 다른 사용자가 이후의 가능한 손상에 대해 염려하지 않고 패키지를 사용할 수 있습니다.
ms.openlocfilehash: 738167011f64b5174df3504c8e1d06146f4c7db5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662430"
---
# <a name="unlisting-packages"></a><span data-ttu-id="3c655-104">목록에서 패키지 제거</span><span class="sxs-lookup"><span data-stu-id="3c655-104">Unlisting Packages</span></span>

<span data-ttu-id="3c655-105">**옵션으로 노출되지 않는 패키지를 PowerShell 갤러리에서 제거해야 하는 것은 무엇 때문일까요?**</span><span class="sxs-lookup"><span data-stu-id="3c655-105">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="3c655-106">PowerShell 갤러리에서는 사용자가 패키지를 영구적으로 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-106">The PowerShell Gallery does not support users permanently deleting their packages.</span></span> <span data-ttu-id="3c655-107">따라서 다른 사용자가 이후의 가능한 손상에 대해 염려하지 않고 패키지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-107">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="3c655-108">예를 들어 Pester 모듈이 Azure 모듈을 사용하는데 Azure 모듈이 갤러리에서 제거되면 사용자가 Pester 모듈을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-108">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then users can no longer use the Pester module.</span></span>

<span data-ttu-id="3c655-109">패키지를 제거하는 대신 나열 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-109">Instead of removing a package you can unlist it.</span></span>

<span data-ttu-id="3c655-110">**PowerShell 갤러리의 목록에서 패키지를 제거하면 어떻게 될까요?**</span><span class="sxs-lookup"><span data-stu-id="3c655-110">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="3c655-111">PowerShell 갤러리의 목록에서 모듈 또는 스크립트와 같은 패키지를 제거하면 패키지 탭에서 제거됩니다. 또한 목록에 없는 패키지는 검색 표시줄을 사용하여 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-111">Unlisting a package such as a module or script in the PowerShell Gallery removes it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span> <span data-ttu-id="3c655-112">목록에 없는 패키지를 다운로드하려면 패키지의 정확한 이름 및 버전을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-112">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span> <span data-ttu-id="3c655-113">이 때문에 목록에서 패키지를 제거하는 경우 해당 패키지를 사용하는 다른 모듈이나 스크립트가 손상되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-113">Because of this, the unlisting of a package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="3c655-114">목록에서 패키지를 제거하려면 패키지 세부 정보 페이지로 이동한 다음 '모듈 삭제'를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-114">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="3c655-115">'목록에 포함' 확인란의 선택을 취소하고 '저장'을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-115">Uncheck the 'Listed' checkbox, and select 'Save'.</span></span>

<span data-ttu-id="3c655-116">**패키지를 제거하려면 어떻게 하나요?**</span><span class="sxs-lookup"><span data-stu-id="3c655-116">**How can I remove a package?**</span></span>

<span data-ttu-id="3c655-117">패키지를 삭제해야 하는 경우에는 PowerShell 갤러리 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="3c655-117">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span> <span data-ttu-id="3c655-118">유효한 삭제 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-118">Valid deletion scenarios are:</span></span>

- <span data-ttu-id="3c655-119">저작권 침해 문제</span><span class="sxs-lookup"><span data-stu-id="3c655-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="3c655-120">패키지에 잠재적으로 유해한 콘텐츠가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="3c655-120">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="3c655-121">패키지에 중요한 데이터가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="3c655-121">Package contains sensitive data.</span></span>

<span data-ttu-id="3c655-122">PowerShell 갤러리 관리자에게 패키지 삭제 요청을 제출하려면 패키지 세부 정보 페이지로 이동한 다음 고객 지원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c655-122">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
