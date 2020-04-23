---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 소셜 미디어나 댓글을 통해 피드백 제공
ms.openlocfilehash: 95e5db22b94151c3974189c30f1d4e580b47eeb5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71327884"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="57c6c-103">소셜 미디어나 댓글을 통해 피드백 제공</span><span class="sxs-lookup"><span data-stu-id="57c6c-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="57c6c-104">PowerShell 갤러리에서는 사용자에게 두 가지 방식으로 패키지에 대한 공개 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-104">The PowerShell Gallery supports two approaches for users to provide public feedback on a package:</span></span>

- <span data-ttu-id="57c6c-105">왼쪽 모서리의 링크를 사용하여 Facebook, LinkedIn 또는 Twitter 소셜 미디어 사이트에서 패키지를 "공유"합니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-105">Use the links on the left edge to "share" a package in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="57c6c-106">댓글 기능을 사용하여 패키지에 대한 댓글을 게시합니다. 그러면 작성자가 게시한 패키지에 대한 댓글을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-106">Use the Comment feature to post comments on a package, and to allow Authors to watch for comments on packages they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="57c6c-107">소셜 미디어 피드백</span><span class="sxs-lookup"><span data-stu-id="57c6c-107">Social Media Feedback</span></span>

<span data-ttu-id="57c6c-108">PowerShell 갤러리에 있는 각 패키지의 페이지 왼쪽에는 Facebook, LinkedIn 및 Twitter의 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-108">On the left side of the page for each package in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="57c6c-109">이러한 링크를 클릭하면 소셜 미디어 사이트가 열리므로 패키지 링크를 빠르게 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the package.</span></span>

<span data-ttu-id="57c6c-110">사용자는 선택한 사이트에 로그인해야 PowerShell 갤러리 패키지를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery package.</span></span>

<span data-ttu-id="57c6c-111">다른 사람들에게 추천하려는 패키지가 있는 경우 소셜 미디어에서 공유하면 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-111">Users are encouraged to do this if they find that a package is something they would recommend to others.</span></span>
<span data-ttu-id="57c6c-112">PowerShell 갤러리에서는 각 소셜 미디어 사이트에서 "공유"된 패키지를 확인하여 해당 패키지가 각 소셜 미디어 사이트에서 공유된 횟수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-112">The PowerShell Gallery will check each social media site for "shares" of the package, and display how many times that package has been shared in each of the social media sites.</span></span>
<span data-ttu-id="57c6c-113">이 경우 해당 패키지가 공유된 횟수만 표시되므로 다른 사용자들은 해당 횟수를 패키지의 "좋아요" 수로 해석하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-113">Since this shows only the count of times something has been shared, it will be interpreted other users as "liking" the package.</span></span>

## <a name="comments"></a><span data-ttu-id="57c6c-114">주석</span><span class="sxs-lookup"><span data-stu-id="57c6c-114">Comments</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57c6c-115">Livefyre 댓글 처리는 타사 공급 업체가 제공하며 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-115">Livefyre commenting is provided by a third-party vendor and is no longer supported.</span></span>
> <span data-ttu-id="57c6c-116">2019년 5월 1일부터 더 이상 Livefyre 댓글 처리를 PowerShell 갤러리에서 이용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-116">Livefyre commenting will no longer be available on the PowerShell Gallery starting 05/01/2019.</span></span> 

<span data-ttu-id="57c6c-117">PowerShell 갤러리는 LiveFyre 서비스를 통해 패키지에 대한 사용자의 댓글 게시를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-117">The PowerShell Gallery uses the LiveFyre service to allow users to comment on packages.</span></span>
<span data-ttu-id="57c6c-118">패키지에 대한 권장 사항이나 피드백이 있는 사용자는 이 기능을 통해 모든 패키지 페이지 방문자에게 표시되는 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-118">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the package page.</span></span>
<span data-ttu-id="57c6c-119">패키지 소유자는 이 피드백을 팔로우하여 댓글이 게시되면 알림을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-119">Package owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="57c6c-120">댓글 시스템은 Microsoft에서 관리하지 않는 별도의 서비스인 LiveFyre를 통해 제공되므로 고유한 로그인 정보가 있어야 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-120">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="57c6c-121">처음으로 댓글을 남기거나 패키지 중 하나의 댓글을 팔로우하도록 선택하면 LiveFyre 계정을 만들라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-121">The first time you choose to leave a comment or follow comments on one of your packages, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="57c6c-122">LiveFyre 계정을 만들어서 로그인한 후에 패키지에 대한 피드백을 제공하는 댓글을 작성하여 "댓글 게시..."를 클릭하면 됩니다. 하지만 댓글이 즉시 표시되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-122">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the package, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="57c6c-123">갤러리 패키지에 대한 댓글은 PowerShell 갤러리 관리자가 중재하며, 게시한 모든 댓글은 중재자가 검토한 후에 다른 사용자들이 볼 수 있도록 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-123">Comments for gallery packages are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="57c6c-124">이처럼 댓글을 중재하는 이유는 PowerShell 갤러리 [사용 약관](https://www.powershellgallery.com/policies/Terms)에 맞는 공개 댓글을 게시하기 위해서입니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-124">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="57c6c-125">패키지 소유자는 LiveFyre에 게시되는 댓글을 팔로우하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-125">Package owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="57c6c-126">LiveFyre 계정은 필수 항목이며, LiveFyre에서 패키지를 게시하는 데 사용하는 것과 같은 메일 주소를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-126">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your package in LiveFyre.</span></span>
<span data-ttu-id="57c6c-127">댓글을 팔로우하려면 LiveFyre에 로그인한 다음 소유자로 등재된 패키지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-127">To Follow comments, log into LiveFyre, and navigate to any package where you are listed as an Owner.</span></span>
<span data-ttu-id="57c6c-128">각 패키지 아래쪽의 댓글 상자 밑에 "+팔로우"가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-128">Below the Comment box at the bottom of each package you will see "+Follow".</span></span>
<span data-ttu-id="57c6c-129">이 단추를 클릭하면 패키지에 대해 새 댓글이 게시될 때마다 LiveFyre에서 등록된 메일 주소로 메일을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="57c6c-129">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the package.</span></span>
