---
title: PowerShell Core 지원 수명 주기
description: PowerShell Core에 대한 정책 관리 지원
ms.date: 08/06/2018
ms.openlocfilehash: 27738514fc84105a0339eafcdbb540b7d3790052
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416295"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="90b0b-103">PowerShell Core 지원 수명 주기</span><span class="sxs-lookup"><span data-stu-id="90b0b-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="90b0b-104">PowerShell Core는 Windows PowerShell과 별개로 제공, 설치 및 구성되는 도구 및 구성 요소의 고유 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span> <span data-ttu-id="90b0b-105">따라서 PowerShell Core는 Windows 7/8.1/10 또는 Windows Server 라이선싱 계약에 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-105">So, PowerShell Core isn't included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="90b0b-106">그러나 PowerShell Core는 [프리미어][], [Microsoft 기업계약][enterprise-agreement] 및 [Microsoft 소프트웨어 보증][assurance]을 포함한 기존의 Microsoft 지원 계약으로 지원받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="90b0b-107">또한, 문제가 있는 경우 지원 요청서를 작성하여 PowerShell Core에 대한 [보조 지원][]을 유료로 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="90b0b-108">커뮤니티 지원</span><span class="sxs-lookup"><span data-stu-id="90b0b-108">Community Support</span></span>

<span data-ttu-id="90b0b-109">또한 GitHub에 대한 [커뮤니티 지원][]도 제공하여 문제, 버그 또는 기능 요청을 취합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="90b0b-110">또한 Microsoft [PowerShell 기술 커뮤니티][] 또는 [PowerShell][pshub] 허브 페이지의 커뮤니티 섹션에 나열된 포럼에서 커뮤니티의 다른 구성원에 게 도움을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-110">Also, you may find help from other members of the community in the Microsoft [PowerShell Tech Community][] or any of the forums listed in the community section of [PowerShell][pshub] hub page.</span></span> <span data-ttu-id="90b0b-111">단, 커뮤니티가 발생한 문제를 제때 처리하거나 해결한다는 보장은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span> <span data-ttu-id="90b0b-112">긴급하게 도움이 필요한 문제가 있는 경우 기존의 유료 지원 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="90b0b-113">PowerShell Core의 수명 주기</span><span class="sxs-lookup"><span data-stu-id="90b0b-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="90b0b-114">PowerShell Core는 [Microsoft 최신 수명 주기 정책][modern]을 채택합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span> <span data-ttu-id="90b0b-115">이 지원 수명 주기는 고객이 항상 최신 버전을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="90b0b-116">약 6개월 단위로 PowerShell Core의 6.x 버전이 분기별로 업데이트 됩니다(예: 6.0, 6.1, 6.2 등).</span><span class="sxs-lookup"><span data-stu-id="90b0b-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90b0b-117">지원을 계속 받으려면 부 버전이 새로 릴리스될 때마다 6개월 이내에 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="90b0b-118">예를 들어 PowerShell Core 6.1이 2018년 7월 1일에 릴리스 되고, 계속해서 지원을 받고자 하는 경우 2019년 1월 1일까지 PowerShell Core 6.1로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90b0b-119">지원을 계속 받으려면 새 패치가 릴리스될 때마다 30일 이내에 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="90b0b-120">예를 들어 PowerShell Core 6.1을 실행하고 있으며 6.1.3이 2019년 2월 19일에 릴리스된 경우 해당 릴리스가 지원을 유지하는 30일 후인 2019년 3월 21일까지 PowerShell Core 6.1.3으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-120">For example, If you're running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span> <span data-ttu-id="90b0b-121">수정 사항이 필요한 경우, 다음 누적 업데이트에서 수정 사항이 릴리스됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="90b0b-122">최신 수명 주기 정책에 따라 Microsoft는 해당 제품(즉, PowerShell Core)에 대한 지원을 중단하기 12개월 전에 고객 측에 공지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="90b0b-123">결국 PowerShell Core가 장기 서비스 방식을 채택하는 것을 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-123">Eventually, we expect PowerShell Core will adopt the long-term servicing approach.</span></span> <span data-ttu-id="90b0b-124">이 서비스 방식에서는 6.x의 특정 분기/버전에 필요한 지속적인 지원을 위해 서비스 및 보안 업데이트만 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="90b0b-125">지원되는 플랫폼</span><span class="sxs-lookup"><span data-stu-id="90b0b-125">Supported platforms</span></span>

<span data-ttu-id="90b0b-126">PowerShell Core의 플랫폼과 버전이 공식적으로 지원되는지 확인하려면 다음 표를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90b0b-126">To confirm if your platform and version of PowerShell Core are officially supported, see the following table.</span></span>

<span data-ttu-id="90b0b-127">또한 커뮤니티에서 일부 플랫폼과 관련한 패키지를 제공하였으나 공식적으로 지원되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-127">Our community has also contributed packages for some platforms, but they aren't officially supported.</span></span> <span data-ttu-id="90b0b-128">이러한 패키지는 표에서 `Community`로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="90b0b-129">`Experimental`로 나열되는 플랫폼은 공식적으로 지원되지는 않지만, 실험 및 피드백용으로 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-129">Platforms listed as `Experimental` aren't officially supported, but are available for experimentation and feedback.</span></span>

| <span data-ttu-id="90b0b-130">플랫폼</span><span class="sxs-lookup"><span data-stu-id="90b0b-130">Platform</span></span>                                          |      <span data-ttu-id="90b0b-131">6.2</span><span class="sxs-lookup"><span data-stu-id="90b0b-131">6.2</span></span>      |    <span data-ttu-id="90b0b-132">7.0</span><span class="sxs-lookup"><span data-stu-id="90b0b-132">7.0</span></span>    |
|---------------------------------------------------|:-------------:|:---------:|
| <span data-ttu-id="90b0b-133">Windows 7, 8.1 및 10</span><span class="sxs-lookup"><span data-stu-id="90b0b-133">Windows 7, 8.1, and 10</span></span>                            |   <span data-ttu-id="90b0b-134">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-134">Supported</span></span>   | <span data-ttu-id="90b0b-135">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-135">Supported</span></span> |
| <span data-ttu-id="90b0b-136">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="90b0b-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             |   <span data-ttu-id="90b0b-137">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-137">Supported</span></span>   | <span data-ttu-id="90b0b-138">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-138">Supported</span></span> |
| <span data-ttu-id="90b0b-139">[Windows Server 반기 채널][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="90b0b-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> |   <span data-ttu-id="90b0b-140">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-140">Supported</span></span>   | <span data-ttu-id="90b0b-141">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-141">Supported</span></span> |
| <span data-ttu-id="90b0b-142">Ubuntu 16.04 및 18.04</span><span class="sxs-lookup"><span data-stu-id="90b0b-142">Ubuntu 16.04 and 18.04</span></span>                            |   <span data-ttu-id="90b0b-143">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-143">Supported</span></span>   | <span data-ttu-id="90b0b-144">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-144">Supported</span></span> |
| <span data-ttu-id="90b0b-145">Ubuntu 18.10(맞춤 패키지를 통해)</span><span class="sxs-lookup"><span data-stu-id="90b0b-145">Ubuntu 18.10 (via Snap Package)</span></span>                   |   <span data-ttu-id="90b0b-146">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-146">Community</span></span>   | <span data-ttu-id="90b0b-147">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-147">Community</span></span> |
| <span data-ttu-id="90b0b-148">Ubuntu 19.04(맞춤 패키지를 통해)</span><span class="sxs-lookup"><span data-stu-id="90b0b-148">Ubuntu 19.04 (via Snap Package)</span></span>                   |   <span data-ttu-id="90b0b-149">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-149">Community</span></span>   | <span data-ttu-id="90b0b-150">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-150">Community</span></span> |
| <span data-ttu-id="90b0b-151">Debian 9</span><span class="sxs-lookup"><span data-stu-id="90b0b-151">Debian 9</span></span>                                          |   <span data-ttu-id="90b0b-152">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-152">Supported</span></span>   | <span data-ttu-id="90b0b-153">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-153">Supported</span></span> |
| <span data-ttu-id="90b0b-154">Debian 10</span><span class="sxs-lookup"><span data-stu-id="90b0b-154">Debian 10</span></span>                                         | <span data-ttu-id="90b0b-155">지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="90b0b-155">Not Supported</span></span> | <span data-ttu-id="90b0b-156">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-156">Supported</span></span> |
| <span data-ttu-id="90b0b-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="90b0b-157">CentOS 7</span></span>                                          |   <span data-ttu-id="90b0b-158">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-158">Supported</span></span>   | <span data-ttu-id="90b0b-159">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-159">Supported</span></span> |
| <span data-ttu-id="90b0b-160">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="90b0b-160">Red Hat Enterprise Linux 7</span></span>                        |   <span data-ttu-id="90b0b-161">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-161">Supported</span></span>   | <span data-ttu-id="90b0b-162">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-162">Supported</span></span> |
| <span data-ttu-id="90b0b-163">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="90b0b-163">openSUSE 42.3</span></span>                                     |   <span data-ttu-id="90b0b-164">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-164">Supported</span></span>   | <span data-ttu-id="90b0b-165">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-165">Supported</span></span> |
| <span data-ttu-id="90b0b-166">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="90b0b-166">Fedora 28</span></span>                                         |   <span data-ttu-id="90b0b-167">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-167">Supported</span></span>   | <span data-ttu-id="90b0b-168">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-168">Supported</span></span> |
| <span data-ttu-id="90b0b-169">Fedora 29, 30</span><span class="sxs-lookup"><span data-stu-id="90b0b-169">Fedora 29, 30</span></span>                                     | <span data-ttu-id="90b0b-170">지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="90b0b-170">Not Supported</span></span> | <span data-ttu-id="90b0b-171">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-171">Supported</span></span> |
| <span data-ttu-id="90b0b-172">Alpine 3.8</span><span class="sxs-lookup"><span data-stu-id="90b0b-172">Alpine 3.8</span></span>                                        |   <span data-ttu-id="90b0b-173">참고 참조</span><span class="sxs-lookup"><span data-stu-id="90b0b-173">See Note</span></span>    | <span data-ttu-id="90b0b-174">참고 참조</span><span class="sxs-lookup"><span data-stu-id="90b0b-174">See Note</span></span>  |
| <span data-ttu-id="90b0b-175">Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="90b0b-175">Alpine 3.9 and 3.10</span></span>                               | <span data-ttu-id="90b0b-176">지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="90b0b-176">Not Supported</span></span> | <span data-ttu-id="90b0b-177">참고 참조</span><span class="sxs-lookup"><span data-stu-id="90b0b-177">See Note</span></span>  |
| <span data-ttu-id="90b0b-178">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="90b0b-178">macOS 10.12+</span></span>                                      |   <span data-ttu-id="90b0b-179">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-179">Supported</span></span>   | <span data-ttu-id="90b0b-180">지원 여부</span><span class="sxs-lookup"><span data-stu-id="90b0b-180">Supported</span></span> |
| <span data-ttu-id="90b0b-181">Arch</span><span class="sxs-lookup"><span data-stu-id="90b0b-181">Arch</span></span>                                              |   <span data-ttu-id="90b0b-182">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-182">Community</span></span>   | <span data-ttu-id="90b0b-183">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-183">Community</span></span> |
| <span data-ttu-id="90b0b-184">Raspbian</span><span class="sxs-lookup"><span data-stu-id="90b0b-184">Raspbian</span></span>                                          |   <span data-ttu-id="90b0b-185">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-185">Community</span></span>   | <span data-ttu-id="90b0b-186">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-186">Community</span></span> |
| <span data-ttu-id="90b0b-187">Kali</span><span class="sxs-lookup"><span data-stu-id="90b0b-187">Kali</span></span>                                              |   <span data-ttu-id="90b0b-188">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-188">Community</span></span>   | <span data-ttu-id="90b0b-189">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-189">Community</span></span> |
| <span data-ttu-id="90b0b-190">AppImage(여러 Linux 플랫폼에서 사용)</span><span class="sxs-lookup"><span data-stu-id="90b0b-190">AppImage (works on multiple Linux platforms)</span></span>      |   <span data-ttu-id="90b0b-191">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-191">Community</span></span>   | <span data-ttu-id="90b0b-192">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="90b0b-192">Community</span></span> |
| [<span data-ttu-id="90b0b-193">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="90b0b-193">Snap Package</span></span>](https://snapcraft.io/powershell)   |   <span data-ttu-id="90b0b-194">참고 참조</span><span class="sxs-lookup"><span data-stu-id="90b0b-194">See note</span></span>    | <span data-ttu-id="90b0b-195">참고 참조</span><span class="sxs-lookup"><span data-stu-id="90b0b-195">See note</span></span>  |

> [!NOTE]
> <span data-ttu-id="90b0b-196">맞춤 패키지는 패키지를 실행하고 있는 배포와 동일하게 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-196">Snap packages are supported the same as the distribution you're running the package on.</span></span>

> [!NOTE]
> <span data-ttu-id="90b0b-197">CIM, PowerShell Remoting, DSC는 Alpine에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-197">CIM, PowerShell Remoting, and DSC are not supported on Alpine.</span></span>

## <a name="powershell-releases-end-of-life"></a><span data-ttu-id="90b0b-198">PowerShell 릴리스 수명 종료</span><span class="sxs-lookup"><span data-stu-id="90b0b-198">PowerShell releases end-of-life</span></span>

<span data-ttu-id="90b0b-199">[PowerShell Core의 수명 주기](#lifecycle-of-powershell-core)에 따라 다음 표에는 다양한 릴리스의 지원 중단 날짜가 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-199">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various releases will no longer be supported.</span></span>

| <span data-ttu-id="90b0b-200">버전</span><span class="sxs-lookup"><span data-stu-id="90b0b-200">Version</span></span> | <span data-ttu-id="90b0b-201">수명 종료</span><span class="sxs-lookup"><span data-stu-id="90b0b-201">End-of-life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="90b0b-202">6.0</span><span class="sxs-lookup"><span data-stu-id="90b0b-202">6.0</span></span>     | <span data-ttu-id="90b0b-203">2019년 2월 13일</span><span class="sxs-lookup"><span data-stu-id="90b0b-203">February 13, 2019</span></span>             |
| <span data-ttu-id="90b0b-204">6.1</span><span class="sxs-lookup"><span data-stu-id="90b0b-204">6.1</span></span>     | <span data-ttu-id="90b0b-205">2019년 9월 28일</span><span class="sxs-lookup"><span data-stu-id="90b0b-205">September 28, 2019</span></span>            |
| <span data-ttu-id="90b0b-206">6.2</span><span class="sxs-lookup"><span data-stu-id="90b0b-206">6.2</span></span>     | <span data-ttu-id="90b0b-207">7 릴리스 후 6개월</span><span class="sxs-lookup"><span data-stu-id="90b0b-207">6 months after 7 releases</span></span>     |

## <a name="unsupported-platforms"></a><span data-ttu-id="90b0b-208">지원되지 않는 플랫폼</span><span class="sxs-lookup"><span data-stu-id="90b0b-208">Unsupported platforms</span></span>

<span data-ttu-id="90b0b-209">플랫폼 버전이 플랫폼 소유자가 정의한 수명 종료에 도달하면 PowerShell Core도 해당 플랫폼 버전의 지원 제공을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-209">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span> <span data-ttu-id="90b0b-210">이전에 릴리스된 패키지는 액세스가 필요한 고객이 계속 사용할 수는 있지만, 공식 지원 및 업데이트는 더 이상 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-210">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="90b0b-211">그러므로 다음 버전의 지원을 배포 소유자가 종료했으며 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-211">So, the distribution owners ended support for the following versions and aren't supported.</span></span>

| <span data-ttu-id="90b0b-212">플랫폼</span><span class="sxs-lookup"><span data-stu-id="90b0b-212">Platform</span></span> | <span data-ttu-id="90b0b-213">버전</span><span class="sxs-lookup"><span data-stu-id="90b0b-213">Version</span></span> | <span data-ttu-id="90b0b-214">수명 종료</span><span class="sxs-lookup"><span data-stu-id="90b0b-214">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="90b0b-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="90b0b-215">Fedora</span></span>   | <span data-ttu-id="90b0b-216">24</span><span class="sxs-lookup"><span data-stu-id="90b0b-216">24</span></span>      | [<span data-ttu-id="90b0b-217">2017년 8월</span><span class="sxs-lookup"><span data-stu-id="90b0b-217">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="90b0b-218">Fedora</span><span class="sxs-lookup"><span data-stu-id="90b0b-218">Fedora</span></span>   | <span data-ttu-id="90b0b-219">25</span><span class="sxs-lookup"><span data-stu-id="90b0b-219">25</span></span>      | [<span data-ttu-id="90b0b-220">2017년 12월</span><span class="sxs-lookup"><span data-stu-id="90b0b-220">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="90b0b-221">Fedora</span><span class="sxs-lookup"><span data-stu-id="90b0b-221">Fedora</span></span>   | <span data-ttu-id="90b0b-222">26</span><span class="sxs-lookup"><span data-stu-id="90b0b-222">26</span></span>      | [<span data-ttu-id="90b0b-223">2018년 5월</span><span class="sxs-lookup"><span data-stu-id="90b0b-223">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="90b0b-224">openSUSE</span><span class="sxs-lookup"><span data-stu-id="90b0b-224">openSUSE</span></span> | <span data-ttu-id="90b0b-225">42.1</span><span class="sxs-lookup"><span data-stu-id="90b0b-225">42.1</span></span>    | [<span data-ttu-id="90b0b-226">2017년 5월</span><span class="sxs-lookup"><span data-stu-id="90b0b-226">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="90b0b-227">openSUSE</span><span class="sxs-lookup"><span data-stu-id="90b0b-227">openSUSE</span></span> | <span data-ttu-id="90b0b-228">42.2</span><span class="sxs-lookup"><span data-stu-id="90b0b-228">42.2</span></span>    | [<span data-ttu-id="90b0b-229">2018년 1월</span><span class="sxs-lookup"><span data-stu-id="90b0b-229">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="90b0b-230">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="90b0b-230">Ubuntu</span></span>   | <span data-ttu-id="90b0b-231">16.10</span><span class="sxs-lookup"><span data-stu-id="90b0b-231">16.10</span></span>   | [<span data-ttu-id="90b0b-232">2017년 7월</span><span class="sxs-lookup"><span data-stu-id="90b0b-232">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="90b0b-233">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="90b0b-233">Ubuntu</span></span>   | <span data-ttu-id="90b0b-234">17.04</span><span class="sxs-lookup"><span data-stu-id="90b0b-234">17.04</span></span>   | [<span data-ttu-id="90b0b-235">2018년 1월</span><span class="sxs-lookup"><span data-stu-id="90b0b-235">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="90b0b-236">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="90b0b-236">Ubuntu</span></span>   | <span data-ttu-id="90b0b-237">17.10</span><span class="sxs-lookup"><span data-stu-id="90b0b-237">17.10</span></span>   | [<span data-ttu-id="90b0b-238">2018년 7월</span><span class="sxs-lookup"><span data-stu-id="90b0b-238">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="90b0b-239">Debian</span><span class="sxs-lookup"><span data-stu-id="90b0b-239">Debian</span></span>   | <span data-ttu-id="90b0b-240">8</span><span class="sxs-lookup"><span data-stu-id="90b0b-240">8</span></span>       | [<span data-ttu-id="90b0b-241">2018년 6월</span><span class="sxs-lookup"><span data-stu-id="90b0b-241">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="90b0b-242">Fedora</span><span class="sxs-lookup"><span data-stu-id="90b0b-242">Fedora</span></span>   | <span data-ttu-id="90b0b-243">27</span><span class="sxs-lookup"><span data-stu-id="90b0b-243">27</span></span>      | [<span data-ttu-id="90b0b-244">2018년 11월</span><span class="sxs-lookup"><span data-stu-id="90b0b-244">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="90b0b-245">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="90b0b-245">Ubuntu</span></span>   | <span data-ttu-id="90b0b-246">14.04</span><span class="sxs-lookup"><span data-stu-id="90b0b-246">14.04</span></span>   | [<span data-ttu-id="90b0b-247">2019년 4월</span><span class="sxs-lookup"><span data-stu-id="90b0b-247">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="90b0b-248">라이선싱에 대한 메모</span><span class="sxs-lookup"><span data-stu-id="90b0b-248">Notes on licensing</span></span>

<span data-ttu-id="90b0b-249">PowerShell Core는 [MIT 라이선스][]에서 릴리스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-249">PowerShell Core is released under the [MIT license][].</span></span> <span data-ttu-id="90b0b-250">본 라이선스 및 유료 지원 계약이 안 된 경우 사용자는 [커뮤니티 지원][]으로 서비스가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-250">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span> <span data-ttu-id="90b0b-251">커뮤니티 지원을 이용하더라도 Microsoft는 문의 응답 및 해결 방안을 보장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-251">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="90b0b-252">Windows PowerShell 모듈</span><span class="sxs-lookup"><span data-stu-id="90b0b-252">Windows PowerShell Module</span></span>

<span data-ttu-id="90b0b-253">PowerShell Core에 대한 지원은 명시적으로 이 모듈이 PowerShell Core를 지원하지 않는 한 다른 제품 모듈을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-253">Support for PowerShell Core doesn't include product modules, unless those modules explicitly support PowerShell Core.</span></span> <span data-ttu-id="90b0b-254">예를 들어, Windows Server에 부분적으로 제공되는 `ActiveDirectory` 모듈을 사용하는 경우 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-254">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="90b0b-255">그러나 PowerShell Core를 명시적으로 지원하지 않는 모듈은 경우에 따라 호환이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-255">However, modules that don't explicitly support PowerShell Core may be compatible in some cases.</span></span> <span data-ttu-id="90b0b-256">[WindowsPSModulePath][] 모듈을 설치하여 Windows PowerShell `PSModulePath`를 PowerShell Core `PSModulePath`에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-256">By installing the [WindowsPSModulePath][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="90b0b-257">먼저 PowerShell 갤러리에서 **WindowsPSModulePath** 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-257">First, install the **WindowsPSModulePath** module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="90b0b-258">이 모듈을 설치한 후에, `Add-WindowsPSModulePath` cmdlet을 실행하여 Windows PowerShell `PSModulePath`를 PowerShell Core에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-258">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="90b0b-259">실험적 기능</span><span class="sxs-lookup"><span data-stu-id="90b0b-259">Experimental features</span></span>

<span data-ttu-id="90b0b-260">[실험적 기능][]은 [커뮤니티 지원](#community-support)으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="90b0b-260">[Experimental features][] are limited to [community support](#community-support).</span></span>

[프리미어]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[커뮤니티 지원]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[pshub]: https://docs.microsoft.com/powershell
[PowerShell 기술 커뮤니티]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[보조 지원]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 라이선스]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[실험적 기능]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
