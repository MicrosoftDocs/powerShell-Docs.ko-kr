---
title: PowerShell Core 지원 수명 주기
description: PowerShell Core에 대한 정책 관리 지원
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403495"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="a5bc5-103">PowerShell Core 지원 수명 주기</span><span class="sxs-lookup"><span data-stu-id="a5bc5-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="a5bc5-104">PowerShell Core는 Windows PowerShell과 별개로 제공, 설치 및 구성되는 도구 및 구성 요소의 고유 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="a5bc5-105">따라서 PowerShell Core는 Windows 7/8.1/10 또는 Windows Server 라이선싱 계약에 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-105">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="a5bc5-106">그러나 PowerShell Core는 [프리미어][], [Microsoft 기업 계약][enterprise-agreement] 및 [Microsoft 소프트웨어 보증][assurance]을 포함한 기존의 Microsoft 지원 계약에서 지원받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="a5bc5-107">또한, 문제가 있는 경우 지원 요청서를 작성하여 PowerShell Core에 대한 [보조 지원][]을 유료로 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="a5bc5-108">또한 GitHub에 대한 [커뮤니티 지원][]도 제공하여 문제, 버그 또는 기능 요청을 취합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="a5bc5-109">또는, [Microsoft 커뮤니티][] 또는 Microsoft [PowerShell 기술 커뮤니티][]와 같은 일반적인 커뮤니티에서 다양한 구성원들에게 도움을 받을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-109">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="a5bc5-110">단, 문제가 제때 해결된다는 보장은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-110">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="a5bc5-111">긴급하게 도움이 필요한 문제가 있는 경우 기존의 유료 지원 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="a5bc5-112">PowerShell Core의 수명 주기</span><span class="sxs-lookup"><span data-stu-id="a5bc5-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="a5bc5-113">PowerShell Core는 [Microsoft 최신 수명 주기 정책][modern]을 채택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="a5bc5-114">이 지원 수명 주기는 고객이 항상 최신 버전을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="a5bc5-115">약 6개월 단위로 PowerShell Core의 6.x 버전이 분기별로 업데이트 됩니다(예: 6.0, 6.1, 6.2 등).</span><span class="sxs-lookup"><span data-stu-id="a5bc5-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5bc5-116">지원을 계속 받으려면 부 버전이 새로 릴리스될 때마다 6개월 이내에 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="a5bc5-117">예를 들어 PowerShell Core 6.1이 2018년 7월 1일에 릴리스 되고, 계속해서 지원을 받고자 하는 경우 2019년 1월 1일까지 PowerShell Core 6.1로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-117">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core 분기 수명 주기][lifecycle-chart]

<span data-ttu-id="a5bc5-119">최신 수명 주기 정책에 따라 Microsoft는 해당 제품(예: PowerShell Core)에 대한 지원을 중단하기 12개월 전에 고객 측에 공지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="a5bc5-120">즉, PowerShell Core는 "장기 서비스"를 채택하여 6.x의 특정 분기/버전에 대한 지속적인 지원을 위해 서비스 및 보안 업데이트를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="a5bc5-121">지원되는 플랫폼</span><span class="sxs-lookup"><span data-stu-id="a5bc5-121">Supported platforms</span></span>

<span data-ttu-id="a5bc5-122">사용하는 PowerShell Core 버전에 대해 공식적으로 지원되는 플랫폼에 대해서는 다음 표를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-122">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="a5bc5-123">또한 커뮤니티에서 일부 플랫폼과 관련한 패키지를 제공하였으나 공식적으로 지원되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-123">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="a5bc5-124">이러한 패키지는 표에서 `Community`로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-124">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="a5bc5-125">`Experimental`로 나열되는 플랫폼은 공식적으로 지원되지는 않지만, 실험 및 피드백용으로 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-125">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="a5bc5-126">6.0</span><span class="sxs-lookup"><span data-stu-id="a5bc5-126">6.0</span></span>         | <span data-ttu-id="a5bc5-127">6.1</span><span class="sxs-lookup"><span data-stu-id="a5bc5-127">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="a5bc5-128">Windows 7, 8.1 및 10</span><span class="sxs-lookup"><span data-stu-id="a5bc5-128">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="a5bc5-129">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-129">Supported</span></span>   | <span data-ttu-id="a5bc5-130">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-130">Supported</span></span>   |
| <span data-ttu-id="a5bc5-131">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="a5bc5-131">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="a5bc5-132">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-132">Supported</span></span>   | <span data-ttu-id="a5bc5-133">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-133">Supported</span></span>   |
| <span data-ttu-id="a5bc5-134">[Windows 서버 반기 채널][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="a5bc5-134">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="a5bc5-135">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-135">Supported</span></span>   | <span data-ttu-id="a5bc5-136">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-136">Supported</span></span>   |
| <span data-ttu-id="a5bc5-137">Ubuntu 14.04, 16.04</span><span class="sxs-lookup"><span data-stu-id="a5bc5-137">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="a5bc5-138">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-138">Supported</span></span>   | <span data-ttu-id="a5bc5-139">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-139">Supported</span></span>   |
| <span data-ttu-id="a5bc5-140">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a5bc5-140">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="a5bc5-141">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-141">Supported</span></span>   |
| <span data-ttu-id="a5bc5-142">Ubuntu 18.10(맞춤 패키지를 통해)</span><span class="sxs-lookup"><span data-stu-id="a5bc5-142">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="a5bc5-143">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="a5bc5-143">Community</span></span>   |
| <span data-ttu-id="a5bc5-144">Debian 8.7+, 9</span><span class="sxs-lookup"><span data-stu-id="a5bc5-144">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="a5bc5-145">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-145">Supported</span></span>   | <span data-ttu-id="a5bc5-146">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-146">Supported</span></span>   |
| <span data-ttu-id="a5bc5-147">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a5bc5-147">CentOS 7</span></span>                                          | <span data-ttu-id="a5bc5-148">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-148">Supported</span></span>   | <span data-ttu-id="a5bc5-149">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-149">Supported</span></span>   |
| <span data-ttu-id="a5bc5-150">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="a5bc5-150">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="a5bc5-151">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-151">Supported</span></span>   | <span data-ttu-id="a5bc5-152">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-152">Supported</span></span>   |
| <span data-ttu-id="a5bc5-153">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="a5bc5-153">OpenSUSE 42.3</span></span>                                     | <span data-ttu-id="a5bc5-154">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-154">Supported</span></span>   | <span data-ttu-id="a5bc5-155">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-155">Supported</span></span>   |
| <span data-ttu-id="a5bc5-156">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="a5bc5-156">Fedora 27</span></span>                                         | <span data-ttu-id="a5bc5-157">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-157">Supported</span></span>   | <span data-ttu-id="a5bc5-158">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-158">Supported</span></span>   |
| <span data-ttu-id="a5bc5-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a5bc5-159">Fedora 28</span></span>                                         |             | <span data-ttu-id="a5bc5-160">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-160">Supported</span></span>   |
| <span data-ttu-id="a5bc5-161">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="a5bc5-161">macOS 10.12+</span></span>                                      | <span data-ttu-id="a5bc5-162">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-162">Supported</span></span>   | <span data-ttu-id="a5bc5-163">지원 여부</span><span class="sxs-lookup"><span data-stu-id="a5bc5-163">Supported</span></span>   |
| <span data-ttu-id="a5bc5-164">Arch</span><span class="sxs-lookup"><span data-stu-id="a5bc5-164">Arch</span></span>                                              | <span data-ttu-id="a5bc5-165">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="a5bc5-165">Community</span></span>   | <span data-ttu-id="a5bc5-166">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="a5bc5-166">Community</span></span>   |
| <span data-ttu-id="a5bc5-167">Raspbian</span><span class="sxs-lookup"><span data-stu-id="a5bc5-167">Raspbian</span></span>                                          | <span data-ttu-id="a5bc5-168">실험적</span><span class="sxs-lookup"><span data-stu-id="a5bc5-168">Experimental</span></span>| <span data-ttu-id="a5bc5-169">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="a5bc5-169">Community</span></span>   |
| <span data-ttu-id="a5bc5-170">Kali</span><span class="sxs-lookup"><span data-stu-id="a5bc5-170">Kali</span></span>                                              | <span data-ttu-id="a5bc5-171">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="a5bc5-171">Community</span></span>   | <span data-ttu-id="a5bc5-172">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="a5bc5-172">Community</span></span>   |
| <span data-ttu-id="a5bc5-173">AppImage(여러 Linux 플랫폼에서 사용)</span><span class="sxs-lookup"><span data-stu-id="a5bc5-173">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="a5bc5-174">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="a5bc5-174">Community</span></span>   | <span data-ttu-id="a5bc5-175">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="a5bc5-175">Community</span></span>   |
| [<span data-ttu-id="a5bc5-176">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="a5bc5-176">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="a5bc5-177">참고 참조</span><span class="sxs-lookup"><span data-stu-id="a5bc5-177">See note</span></span>    | <span data-ttu-id="a5bc5-178">참고 참조</span><span class="sxs-lookup"><span data-stu-id="a5bc5-178">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="a5bc5-179">맞춤 패키지는 일정 기간 동안 실험적입니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-179">Snap packages will be experimental for a period.</span></span>  <span data-ttu-id="a5bc5-180">이후에 맞춤에서는 새로운 지원 문제를 일으키지 않을 것입니다. 지원은 패키지를 실행하는 배포를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-180">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="a5bc5-181">지원되지 않는 플랫폼</span><span class="sxs-lookup"><span data-stu-id="a5bc5-181">Platform which are out of support</span></span>

<span data-ttu-id="a5bc5-182">플랫폼 버전이 플랫폼 소유자가 정의한 수명 종료에 도달하면 PowerShell Core도 해당 플랫폼 버전에 대한 지원 제공을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-182">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="a5bc5-183">이전에 릴리스된 패키지는 액세스가 필요한 고객이 계속 사용할 수는 있지만, 공식 지원 및 업데이트는 더 이상 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-183">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="a5bc5-184">그러므로 다음 버전에 대한 지원은 배포 소유자가 종료했으며, 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-184">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="a5bc5-185">OS</span><span class="sxs-lookup"><span data-stu-id="a5bc5-185">OS</span></span>       | <span data-ttu-id="a5bc5-186">버전</span><span class="sxs-lookup"><span data-stu-id="a5bc5-186">Version</span></span> | <span data-ttu-id="a5bc5-187">수명 종료</span><span class="sxs-lookup"><span data-stu-id="a5bc5-187">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="a5bc5-188">Fedora</span><span class="sxs-lookup"><span data-stu-id="a5bc5-188">Fedora</span></span>   | <span data-ttu-id="a5bc5-189">24</span><span class="sxs-lookup"><span data-stu-id="a5bc5-189">24</span></span>      | [<span data-ttu-id="a5bc5-190">2017년 8월</span><span class="sxs-lookup"><span data-stu-id="a5bc5-190">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="a5bc5-191">Fedora</span><span class="sxs-lookup"><span data-stu-id="a5bc5-191">Fedora</span></span>   | <span data-ttu-id="a5bc5-192">25</span><span class="sxs-lookup"><span data-stu-id="a5bc5-192">25</span></span>      | [<span data-ttu-id="a5bc5-193">2017년 12월</span><span class="sxs-lookup"><span data-stu-id="a5bc5-193">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="a5bc5-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="a5bc5-194">Fedora</span></span>   | <span data-ttu-id="a5bc5-195">26</span><span class="sxs-lookup"><span data-stu-id="a5bc5-195">26</span></span>      | [<span data-ttu-id="a5bc5-196">2018년 5월</span><span class="sxs-lookup"><span data-stu-id="a5bc5-196">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="a5bc5-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a5bc5-197">openSUSE</span></span> | <span data-ttu-id="a5bc5-198">42.1</span><span class="sxs-lookup"><span data-stu-id="a5bc5-198">42.1</span></span>    | [<span data-ttu-id="a5bc5-199">2017년 5월</span><span class="sxs-lookup"><span data-stu-id="a5bc5-199">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="a5bc5-200">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a5bc5-200">openSUSE</span></span> | <span data-ttu-id="a5bc5-201">42.2</span><span class="sxs-lookup"><span data-stu-id="a5bc5-201">42.2</span></span>    | [<span data-ttu-id="a5bc5-202">2018년 1월</span><span class="sxs-lookup"><span data-stu-id="a5bc5-202">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="a5bc5-203">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a5bc5-203">Ubuntu</span></span>   | <span data-ttu-id="a5bc5-204">16.10</span><span class="sxs-lookup"><span data-stu-id="a5bc5-204">16.10</span></span>   | [<span data-ttu-id="a5bc5-205">2017년 7월</span><span class="sxs-lookup"><span data-stu-id="a5bc5-205">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="a5bc5-206">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a5bc5-206">Ubuntu</span></span>   | <span data-ttu-id="a5bc5-207">17.04</span><span class="sxs-lookup"><span data-stu-id="a5bc5-207">17.04</span></span>   | [<span data-ttu-id="a5bc5-208">2018년 1월</span><span class="sxs-lookup"><span data-stu-id="a5bc5-208">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="a5bc5-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a5bc5-209">Ubuntu</span></span>   | <span data-ttu-id="a5bc5-210">17.10</span><span class="sxs-lookup"><span data-stu-id="a5bc5-210">17.10</span></span>   | [<span data-ttu-id="a5bc5-211">2018년 7월</span><span class="sxs-lookup"><span data-stu-id="a5bc5-211">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="a5bc5-212">라이선싱에 대한 메모</span><span class="sxs-lookup"><span data-stu-id="a5bc5-212">Notes on licensing</span></span>

<span data-ttu-id="a5bc5-213">PowerShell Core는 [MIT 라이선스][]에서 릴리스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-213">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="a5bc5-214">본 라이선스 및 유료 지원 계약이 안 된 경우 사용자는 [커뮤니티 지원][]으로 서비스가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-214">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="a5bc5-215">커뮤니티 지원을 이용하더라도 Microsoft는 문의 응답 및 해결 방안을 보장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-215">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="a5bc5-216">Windows PowerShell 모듈</span><span class="sxs-lookup"><span data-stu-id="a5bc5-216">Windows PowerShell Module</span></span>

<span data-ttu-id="a5bc5-217">PowerShell Core에 대한 지원은 명시적으로 이 모듈이 PowerShell Core를 지원하지 않는 한 다른 제품 모듈로 확장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-217">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="a5bc5-218">예를 들어, Windows Server에 부분적으로 제공되는 `ActiveDirectory` 모듈을 사용하는 경우 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-218">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="a5bc5-219">그러나 PowerShell Core를 명시적으로 지원하지 않는 모듈은 경우에 따라 호환이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-219">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="a5bc5-220">[`WindowsPSModulePath`][] 모듈을 설치하여 Windows PowerShell `PSModulePath` 를 PowerShell Core `PSModulePath`로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-220">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="a5bc5-221">먼저, PowerShell 갤러리에서 `WindowsPSModulePath` 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-221">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="a5bc5-222">이 모듈을 설치한 후에, `Add-WindowsPSModulePath` cmdlet을 실행하여 Windows PowerShell `PSModulePath`를 PowerShell Core에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a5bc5-222">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[프리미어]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[커뮤니티 지원]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft 커뮤니티]: https://answers.microsoft.com/
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell 기술 커뮤니티]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[보조 지원]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 라이선스]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
