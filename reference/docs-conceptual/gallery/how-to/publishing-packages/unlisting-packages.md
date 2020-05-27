---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 목록에서 패키지 제거
ms.openlocfilehash: 4291b910dcea65b2ca241e55838ea00d4ec53ee4
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692355"
---
# <a name="unlisting-packages"></a><span data-ttu-id="eaeb0-103">목록에서 패키지 제거</span><span class="sxs-lookup"><span data-stu-id="eaeb0-103">Unlisting Packages</span></span>

<span data-ttu-id="eaeb0-104">**옵션으로 노출되지 않는 패키지를 PowerShell 갤러리에서 제거해야 하는 것은 무엇 때문일까요?**</span><span class="sxs-lookup"><span data-stu-id="eaeb0-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="eaeb0-105">PowerShell 갤러리에서는 사용자가 패키지를 영구적으로 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="eaeb0-106">따라서 다른 사용자가 이후의 가능한 손상에 대해 염려하지 않고 패키지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="eaeb0-107">예를 들어 Pester 모듈이 Azure 모듈을 사용하는데 Azure 모듈이 갤러리에서 제거되면 사용자가 Pester 모듈을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then users can no longer use the Pester module.</span></span>

<span data-ttu-id="eaeb0-108">패키지를 제거하는 대신 나열 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-108">Instead of removing a package you can unlist it.</span></span>

<span data-ttu-id="eaeb0-109">**PowerShell 갤러리의 목록에서 패키지를 제거하면 어떻게 될까요?**</span><span class="sxs-lookup"><span data-stu-id="eaeb0-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="eaeb0-110">PowerShell 갤러리의 목록에서 모듈 또는 스크립트와 같은 패키지를 제거하면 패키지 탭에서 제거됩니다. 또한 목록에 없는 패키지는 검색 표시줄을 사용하여 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-110">Unlisting a package such as a module or script in the PowerShell Gallery removes it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="eaeb0-111">목록에 없는 패키지를 다운로드하려면 패키지의 정확한 이름 및 버전을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="eaeb0-112">이 때문에 목록에서 패키지를 제거하는 경우 해당 패키지를 사용하는 다른 모듈이나 스크립트가 손상되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-112">Because of this, the unlisting of a package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="eaeb0-113">목록에서 패키지를 제거하려면 패키지 세부 정보 페이지로 이동한 다음 '모듈 삭제'를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="eaeb0-114">'목록에 포함' 확인란의 선택을 취소하고 '저장'을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-114">Uncheck the 'Listed' checkbox, and select 'Save'.</span></span>

<span data-ttu-id="eaeb0-115">**패키지를 제거하려면 어떻게 하나요?**</span><span class="sxs-lookup"><span data-stu-id="eaeb0-115">**How can I remove a package?**</span></span>

<span data-ttu-id="eaeb0-116">패키지를 삭제해야 하는 경우에는 PowerShell 갤러리 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="eaeb0-117">유효한 삭제 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-117">Valid deletion scenarios are:</span></span>

- <span data-ttu-id="eaeb0-118">저작권 침해 문제</span><span class="sxs-lookup"><span data-stu-id="eaeb0-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="eaeb0-119">패키지에 잠재적으로 유해한 콘텐츠가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="eaeb0-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="eaeb0-120">패키지에 중요한 데이터가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="eaeb0-120">Package contains sensitive data.</span></span>

<span data-ttu-id="eaeb0-121">PowerShell 갤러리 관리자에게 패키지 삭제 요청을 제출하려면 패키지 세부 정보 페이지로 이동한 다음 고객 지원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eaeb0-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
