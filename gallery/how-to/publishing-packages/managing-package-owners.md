---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 패키지 소유자 관리
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084150"
---
# <a name="managing-package-owners"></a><span data-ttu-id="a7ed6-103">패키지 소유자 관리</span><span class="sxs-lookup"><span data-stu-id="a7ed6-103">Managing package owners</span></span>

<span data-ttu-id="a7ed6-104">PowerShell 갤러리에 있는 패키지의 소유권은 갤러리에 패키지를 게시한 사람이 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="a7ed6-105">초기 패키지 게시 외에 이 메타데이터를 관리해야 하는 경우도 있으므로 패키지 자체는 변경할 수 없지만, 소유자 메타데이터는 변경할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="a7ed6-106">모든 패키지 소유자는 피어입니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-106">All package owners are peers.</span></span>
<span data-ttu-id="a7ed6-107">즉, 모든 패키지 소유자가 패키지의 새로운 버전을 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="a7ed6-108">또한 모든 패키지 소유자가 다른 패키지 소유자를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="a7ed6-109">모든 소유자가 동일한 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="a7ed6-110">패키지의 초기 소유자 설정</span><span class="sxs-lookup"><span data-stu-id="a7ed6-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="a7ed6-111">PowerShell 갤러리에 새 패키지를 게시할 때 패키지를 게시한 사용자가 초기 소유자를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="a7ed6-112">Publish-Module cmdlet에서 사용된 API 키의 소유자로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="a7ed6-113">소유자 추가</span><span class="sxs-lookup"><span data-stu-id="a7ed6-113">Adding Owners</span></span>

<span data-ttu-id="a7ed6-114">PowerShell 갤러리에 패키지를 게시한 후 추가 사용자를 패키지의 소유자로 쉽게 초대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="a7ed6-115">패키지의 현재 소유자인 계정을 사용하여 PowerShell 갤러리에 [로그온](https://powershellgallery.com/users/account/LogOn)합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="a7ed6-116">'항목' 탭을 사용하거나, 검색하거나, 사용자 이름, [**내 패키지 관리**](https://www.powershellgallery.com/account/Packages)를 차례로 클릭하여 패키지 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="a7ed6-117">패키지의 소유자로 로그온한 경우 왼쪽에 있는 '소유자 관리' 링크를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="a7ed6-118">소유자로 추가할 사람의 사용자 이름을 입력하고 '추가'를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="a7ed6-119">패키지의 소유자가 되도록 초대하는 메일이 새 공동 소유자에게 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="a7ed6-120">해당 사용자가 링크를 클릭하면 소유자인 다른 사용자를 제거하는 기능을 포함하여 패키지에 대한 모든 권한을 가진 전체 공동 소유자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="a7ed6-121">**참고**: 새 소유자가 소유권을 확인하기 전에는 패키지의 소유자로 나열되지 ‘않습니다’.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="a7ed6-122">**소유자 관리** 페이지를 보고 있는 경우 현재 소유자에 "승인 보류 중" 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="a7ed6-123">다른 소유자를 제거할 수 있는 것과 마찬가지로 해당 초대를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="a7ed6-124">이 초대 프로세스는 사용자가 다른 사용자를 패키지의 소유자로 거짓 추가하는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="a7ed6-125">"Authors" 메타데이터는 순수 자유형 텍스트이며 "Owners"만 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="a7ed6-126">소유자 제거</span><span class="sxs-lookup"><span data-stu-id="a7ed6-126">Removing Owners</span></span>

<span data-ttu-id="a7ed6-127">패키지에 여러 소유자가 있고 한 소유자를 제거해야 하는 경우 프로세스는 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="a7ed6-128">패키지의 현재 소유자인 계정을 사용하여 PowerShell 갤러리에 [로그온](https://powershellgallery.com/users/account/LogOn)합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="a7ed6-129">'패키지' 탭을 사용하거나, 검색하거나, 사용자 이름, [**내 패키지 관리**](https://www.powershellgallery.com/account/Packages)를 차례로 클릭하여 패키지 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="a7ed6-130">패키지의 소유자로 로그온한 경우 왼쪽에 있는 '소유자 관리' 링크를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="a7ed6-131">제거할 소유자 옆에 있는 '제거' 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="a7ed6-132">패키지 소유권 이전</span><span class="sxs-lookup"><span data-stu-id="a7ed6-132">Transferring Package Ownership</span></span>

<span data-ttu-id="a7ed6-133">패키지 소유권을 한 사용자에서 다른 사용자로 이전하기 위한 요청을 Microsoft에 제출할 수 있지만, 이 작업은 대부분 직접 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="a7ed6-134">소유권을 한 사용자에서 다른 사용자로 이전하는 프로세스는 단순히 위의 두 가지 기능이 조합된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="a7ed6-135">현재 소유자가 새 사용자를 공동 소유자로 초대하고 새 사용자가 초대를 수락합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="a7ed6-136">새 사용자가 소유자 목록에서 기존 사용자를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="a7ed6-137">이 요청은 두 가지 형태로 제공되었지만 프로세스는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="a7ed6-138">패키지 소유권이 한 개발자에서 다른 개발자로 변경되는 경우</span><span class="sxs-lookup"><span data-stu-id="a7ed6-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="a7ed6-139">패키지가 실수로 잘못된 계정을 사용하여 게시된 경우</span><span class="sxs-lookup"><span data-stu-id="a7ed6-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="a7ed6-140">분리된 패키지</span><span class="sxs-lookup"><span data-stu-id="a7ed6-140">Orphaned Packages</span></span>

<span data-ttu-id="a7ed6-141">마지막 시나리오는 자주 발생하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="a7ed6-142">패키지가 분리되었으며 유일한 패키지 소유자 계정을 사용하여 새 소유자를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="a7ed6-143">이 시나리오의 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="a7ed6-144">소유자 계정이 더 이상 존재하지 않는 메일 주소와 연결되어 있고 사용자가 암호를 잊어버린 경우</span><span class="sxs-lookup"><span data-stu-id="a7ed6-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="a7ed6-145">등록된 소유자가 패키지를 생성하는 회사를 퇴사하여 패키지 소유권을 업데이트하도록 연락할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="a7ed6-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="a7ed6-146">일부 패키지에만 영향을 미친 버그로 인해 갤러리에서 패키지의 소유자가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="a7ed6-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="a7ed6-147">PowerShell 갤러리 관리자는 모든 패키지에 대한 '소유자 관리' 링크에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="a7ed6-148">패키지의 정당한 소유자가 소유권 권한을 얻기 위해 현재 소유자에게 문의할 수 없는 경우 갤러리의 '신고하기' 링크를 사용하여 PowerShell 갤러리 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="a7ed6-149">그러면 프로세스에 따라 패키지의 소유권을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="a7ed6-150">패키지의 소유자로 확인되면 직접 패키지에 대한 '소유자 관리' 링크를 사용하여 소유자가 되도록 초대하는 메일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="a7ed6-151">이 작업은 사용자가 소유자로 확인된 후에만 수행되며 상황에 따라 프로세스가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="a7ed6-152">Microsoft는 대체로 패키지의 프로젝트 URL을 사용하여 프로젝트 소유자에게 문의하지만, Twitter, 메일 또는 다른 수단으로 프로젝트 소유자에게 문의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7ed6-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
