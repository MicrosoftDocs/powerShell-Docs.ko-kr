---
title: PowerShell Core 지원 수명 주기
description: PowerShell Core에 대한 정책 관리 지원
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623861"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="7edc8-103">PowerShell Core 지원 수명 주기</span><span class="sxs-lookup"><span data-stu-id="7edc8-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="7edc8-104">PowerShell Core는 Windows PowerShell과 별개로 제공, 설치 및 구성되는 도구 및 구성 요소의 고유 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="7edc8-105">따라서 PowerShell Core는 Windows 7/8.1/10 또는 Windows Server 라이선싱 계약에 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="7edc8-106">그러나 PowerShell Core는 [프리미어][], [Microsoft 기업 계약][enterprise-agreement] 및 [Microsoft 소프트웨어 보증][assurance]을 포함한 기존의 Microsoft 지원 계약에서 지원받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="7edc8-107">또한, 문제가 있는 경우 지원 요청서를 작성하여 PowerShell Core에 대한 [보조 지원][]을 유료로 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="7edc8-108">커뮤니티 지원</span><span class="sxs-lookup"><span data-stu-id="7edc8-108">Community Support</span></span>

<span data-ttu-id="7edc8-109">또한 GitHub에 대한 [커뮤니티 지원][]도 제공하여 문제, 버그 또는 기능 요청을 취합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="7edc8-110">또는, [Microsoft 커뮤니티][] 또는 Microsoft [PowerShell 기술 커뮤니티][]와 같은 일반적인 커뮤니티에서 다양한 구성원들에게 도움을 받을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="7edc8-111">단, 커뮤니티가 발생한 문제를 제때 처리하거나 해결한다는 보장은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="7edc8-112">긴급하게 도움이 필요한 문제가 있는 경우 기존의 유료 지원 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="7edc8-113">PowerShell Core의 수명 주기</span><span class="sxs-lookup"><span data-stu-id="7edc8-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="7edc8-114">PowerShell Core는 [Microsoft 최신 수명 주기 정책][modern]을 채택합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="7edc8-115">이 지원 수명 주기는 고객이 항상 최신 버전을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="7edc8-116">약 6개월 단위로 PowerShell Core의 6.x 버전이 분기별로 업데이트 됩니다(예: 6.0, 6.1, 6.2 등).</span><span class="sxs-lookup"><span data-stu-id="7edc8-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7edc8-117">지원을 계속 받으려면 부 버전이 새로 릴리스될 때마다 6개월 이내에 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="7edc8-118">예를 들어 PowerShell Core 6.1이 2018년 7월 1일에 릴리스 되고, 계속해서 지원을 받고자 하는 경우 2019년 1월 1일까지 PowerShell Core 6.1로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7edc8-119">지원을 계속 받으려면 새 패치가 릴리스될 때마다 30일 이내에 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="7edc8-120">예를 들어 PowerShell Core 6.1을 실행하고 있으며 6.1.3이 2019년 2월 19일에 릴리스된 경우, 해당 릴리스가 지원을 유지하는 30일 후인 2019년 3월 21일까지 PowerShell Core 6.1.3으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="7edc8-121">수정 사항이 필요한 경우, 다음 누적 업데이트에서 수정 사항이 릴리스됩니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

![PowerShell Core 분기 수명 주기][lifecycle-chart]

<span data-ttu-id="7edc8-123">최신 수명 주기 정책에 따라 Microsoft는 해당 제품(즉, PowerShell Core)에 대한 지원을 중단하기 12개월 전에 고객 측에 공지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-123">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="7edc8-124">결국 PowerShell Core가 “장기 서비스” 방식을 채택하는 것을 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-124">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="7edc8-125">이 서비스 방식에서는 6.x의 특정 분기/버전에 필요한 지속적인 지원을 위해 서비스 및 보안 업데이트만 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-125">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="7edc8-126">지원되는 플랫폼</span><span class="sxs-lookup"><span data-stu-id="7edc8-126">Supported platforms</span></span>

<span data-ttu-id="7edc8-127">사용하는 PowerShell Core 버전에 대해 공식적으로 지원되는 플랫폼에 대해서는 다음 표를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7edc8-127">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="7edc8-128">또한 커뮤니티에서 일부 플랫폼과 관련한 패키지를 제공하였으나 공식적으로 지원되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-128">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="7edc8-129">이러한 패키지는 표에서 `Community`로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-129">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="7edc8-130">`Experimental`로 나열되는 플랫폼은 공식적으로 지원되지는 않지만, 실험 및 피드백용으로 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-130">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="7edc8-131">6.1</span><span class="sxs-lookup"><span data-stu-id="7edc8-131">6.1</span></span>         | <span data-ttu-id="7edc8-132">6.2</span><span class="sxs-lookup"><span data-stu-id="7edc8-132">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="7edc8-133">Windows 7, 8.1 및 10</span><span class="sxs-lookup"><span data-stu-id="7edc8-133">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="7edc8-134">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-134">Supported</span></span>   | <span data-ttu-id="7edc8-135">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-135">Supported</span></span>   |
| <span data-ttu-id="7edc8-136">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="7edc8-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="7edc8-137">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-137">Supported</span></span>   | <span data-ttu-id="7edc8-138">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-138">Supported</span></span>   |
| <span data-ttu-id="7edc8-139">[Windows 서버 반기 채널][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="7edc8-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="7edc8-140">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-140">Supported</span></span>   | <span data-ttu-id="7edc8-141">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-141">Supported</span></span>   |
| <span data-ttu-id="7edc8-142">Ubuntu 16.04 및 18.04</span><span class="sxs-lookup"><span data-stu-id="7edc8-142">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="7edc8-143">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-143">Supported</span></span>   | <span data-ttu-id="7edc8-144">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-144">Supported</span></span>   |
| <span data-ttu-id="7edc8-145">Ubuntu 18.10(맞춤 패키지를 통해)</span><span class="sxs-lookup"><span data-stu-id="7edc8-145">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="7edc8-146">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-146">Community</span></span>   | <span data-ttu-id="7edc8-147">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-147">Community</span></span>   |
| <span data-ttu-id="7edc8-148">Debian 9</span><span class="sxs-lookup"><span data-stu-id="7edc8-148">Debian 9</span></span>                                          | <span data-ttu-id="7edc8-149">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-149">Supported</span></span>   | <span data-ttu-id="7edc8-150">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-150">Supported</span></span>   |
| <span data-ttu-id="7edc8-151">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7edc8-151">CentOS 7</span></span>                                          | <span data-ttu-id="7edc8-152">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-152">Supported</span></span>   | <span data-ttu-id="7edc8-153">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-153">Supported</span></span>   |
| <span data-ttu-id="7edc8-154">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="7edc8-154">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="7edc8-155">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-155">Supported</span></span>   | <span data-ttu-id="7edc8-156">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-156">Supported</span></span>   |
| <span data-ttu-id="7edc8-157">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="7edc8-157">openSUSE 42.3</span></span>                                     | <span data-ttu-id="7edc8-158">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-158">Supported</span></span>   | <span data-ttu-id="7edc8-159">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-159">Supported</span></span>   |
| <span data-ttu-id="7edc8-160">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7edc8-160">Fedora 28</span></span>                                         | <span data-ttu-id="7edc8-161">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-161">Supported</span></span>   | <span data-ttu-id="7edc8-162">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-162">Supported</span></span>   |
| <span data-ttu-id="7edc8-163">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="7edc8-163">macOS 10.12+</span></span>                                      | <span data-ttu-id="7edc8-164">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-164">Supported</span></span>   | <span data-ttu-id="7edc8-165">지원 여부</span><span class="sxs-lookup"><span data-stu-id="7edc8-165">Supported</span></span>   |
| <span data-ttu-id="7edc8-166">Arch</span><span class="sxs-lookup"><span data-stu-id="7edc8-166">Arch</span></span>                                              | <span data-ttu-id="7edc8-167">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-167">Community</span></span>   | <span data-ttu-id="7edc8-168">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-168">Community</span></span>   |
| <span data-ttu-id="7edc8-169">Raspbian</span><span class="sxs-lookup"><span data-stu-id="7edc8-169">Raspbian</span></span>                                          | <span data-ttu-id="7edc8-170">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-170">Community</span></span>   | <span data-ttu-id="7edc8-171">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-171">Community</span></span>   |
| <span data-ttu-id="7edc8-172">Kali</span><span class="sxs-lookup"><span data-stu-id="7edc8-172">Kali</span></span>                                              | <span data-ttu-id="7edc8-173">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-173">Community</span></span>   | <span data-ttu-id="7edc8-174">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-174">Community</span></span>   |
| <span data-ttu-id="7edc8-175">AppImage(여러 Linux 플랫폼에서 사용)</span><span class="sxs-lookup"><span data-stu-id="7edc8-175">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="7edc8-176">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-176">Community</span></span>   | <span data-ttu-id="7edc8-177">커뮤니티</span><span class="sxs-lookup"><span data-stu-id="7edc8-177">Community</span></span>   |
| [<span data-ttu-id="7edc8-178">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="7edc8-178">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="7edc8-179">참고 참조</span><span class="sxs-lookup"><span data-stu-id="7edc8-179">See note</span></span>    | <span data-ttu-id="7edc8-180">참고 참조</span><span class="sxs-lookup"><span data-stu-id="7edc8-180">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="7edc8-181">스냅 패키지는 패키지를 실행하고 있는 배포와 동일하게 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-181">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="7edc8-182">PowerShell 릴리스 종료</span><span class="sxs-lookup"><span data-stu-id="7edc8-182">PowerShell release end of life</span></span>

<span data-ttu-id="7edc8-183">[PowerShell Core의 수명 주기](#lifecycle-of-powershell-core)에 따라 다음 표에는 다양한 릴리스의 지원 중단 날짜가 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-183">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="7edc8-184">버전</span><span class="sxs-lookup"><span data-stu-id="7edc8-184">Version</span></span> | <span data-ttu-id="7edc8-185">수명 종료</span><span class="sxs-lookup"><span data-stu-id="7edc8-185">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="7edc8-186">6.0</span><span class="sxs-lookup"><span data-stu-id="7edc8-186">6.0</span></span>     | <span data-ttu-id="7edc8-187">2019년 2월 13일</span><span class="sxs-lookup"><span data-stu-id="7edc8-187">February 13, 2019</span></span>             |
| <span data-ttu-id="7edc8-188">6.1</span><span class="sxs-lookup"><span data-stu-id="7edc8-188">6.1</span></span>     | <span data-ttu-id="7edc8-189">2019년 9월 28일</span><span class="sxs-lookup"><span data-stu-id="7edc8-189">September 28, 2019</span></span>            |
| <span data-ttu-id="7edc8-190">6.2</span><span class="sxs-lookup"><span data-stu-id="7edc8-190">6.2</span></span>     | <span data-ttu-id="7edc8-191">6.3 릴리스 후 6개월</span><span class="sxs-lookup"><span data-stu-id="7edc8-191">6 months after 6.3 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="7edc8-192">지원되지 않는 플랫폼</span><span class="sxs-lookup"><span data-stu-id="7edc8-192">Platforms, which are out of support</span></span>

<span data-ttu-id="7edc8-193">플랫폼 버전이 플랫폼 소유자가 정의한 수명 종료에 도달하면 PowerShell Core도 해당 플랫폼 버전의 지원 제공을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-193">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="7edc8-194">이전에 릴리스된 패키지는 액세스가 필요한 고객이 계속 사용할 수는 있지만, 공식 지원 및 업데이트는 더 이상 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-194">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="7edc8-195">그러므로 다음 버전의 지원을 배포 소유자가 종료했으며 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-195">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="7edc8-196">OS</span><span class="sxs-lookup"><span data-stu-id="7edc8-196">OS</span></span>       | <span data-ttu-id="7edc8-197">버전</span><span class="sxs-lookup"><span data-stu-id="7edc8-197">Version</span></span> | <span data-ttu-id="7edc8-198">수명 종료</span><span class="sxs-lookup"><span data-stu-id="7edc8-198">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="7edc8-199">Fedora</span><span class="sxs-lookup"><span data-stu-id="7edc8-199">Fedora</span></span>   | <span data-ttu-id="7edc8-200">24</span><span class="sxs-lookup"><span data-stu-id="7edc8-200">24</span></span>      | [<span data-ttu-id="7edc8-201">2017년 8월</span><span class="sxs-lookup"><span data-stu-id="7edc8-201">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="7edc8-202">Fedora</span><span class="sxs-lookup"><span data-stu-id="7edc8-202">Fedora</span></span>   | <span data-ttu-id="7edc8-203">25</span><span class="sxs-lookup"><span data-stu-id="7edc8-203">25</span></span>      | [<span data-ttu-id="7edc8-204">2017년 12월</span><span class="sxs-lookup"><span data-stu-id="7edc8-204">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="7edc8-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="7edc8-205">Fedora</span></span>   | <span data-ttu-id="7edc8-206">26</span><span class="sxs-lookup"><span data-stu-id="7edc8-206">26</span></span>      | [<span data-ttu-id="7edc8-207">2018년 5월</span><span class="sxs-lookup"><span data-stu-id="7edc8-207">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="7edc8-208">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7edc8-208">openSUSE</span></span> | <span data-ttu-id="7edc8-209">42.1</span><span class="sxs-lookup"><span data-stu-id="7edc8-209">42.1</span></span>    | [<span data-ttu-id="7edc8-210">2017년 5월</span><span class="sxs-lookup"><span data-stu-id="7edc8-210">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="7edc8-211">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7edc8-211">openSUSE</span></span> | <span data-ttu-id="7edc8-212">42.2</span><span class="sxs-lookup"><span data-stu-id="7edc8-212">42.2</span></span>    | [<span data-ttu-id="7edc8-213">2018년 1월</span><span class="sxs-lookup"><span data-stu-id="7edc8-213">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="7edc8-214">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7edc8-214">Ubuntu</span></span>   | <span data-ttu-id="7edc8-215">16.10</span><span class="sxs-lookup"><span data-stu-id="7edc8-215">16.10</span></span>   | [<span data-ttu-id="7edc8-216">2017년 7월</span><span class="sxs-lookup"><span data-stu-id="7edc8-216">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="7edc8-217">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7edc8-217">Ubuntu</span></span>   | <span data-ttu-id="7edc8-218">17.04</span><span class="sxs-lookup"><span data-stu-id="7edc8-218">17.04</span></span>   | [<span data-ttu-id="7edc8-219">2018년 1월</span><span class="sxs-lookup"><span data-stu-id="7edc8-219">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="7edc8-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7edc8-220">Ubuntu</span></span>   | <span data-ttu-id="7edc8-221">17.10</span><span class="sxs-lookup"><span data-stu-id="7edc8-221">17.10</span></span>   | [<span data-ttu-id="7edc8-222">2018년 7월</span><span class="sxs-lookup"><span data-stu-id="7edc8-222">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="7edc8-223">Debian</span><span class="sxs-lookup"><span data-stu-id="7edc8-223">Debian</span></span>   | <span data-ttu-id="7edc8-224">8</span><span class="sxs-lookup"><span data-stu-id="7edc8-224">8</span></span>       | [<span data-ttu-id="7edc8-225">2018년 6월</span><span class="sxs-lookup"><span data-stu-id="7edc8-225">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="7edc8-226">Fedora</span><span class="sxs-lookup"><span data-stu-id="7edc8-226">Fedora</span></span>   | <span data-ttu-id="7edc8-227">27</span><span class="sxs-lookup"><span data-stu-id="7edc8-227">27</span></span>      | [<span data-ttu-id="7edc8-228">2018년 11월</span><span class="sxs-lookup"><span data-stu-id="7edc8-228">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="7edc8-229">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7edc8-229">Ubuntu</span></span>   | <span data-ttu-id="7edc8-230">14.04</span><span class="sxs-lookup"><span data-stu-id="7edc8-230">14.04</span></span>   | [<span data-ttu-id="7edc8-231">2019년 4월</span><span class="sxs-lookup"><span data-stu-id="7edc8-231">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="7edc8-232">라이선싱에 대한 메모</span><span class="sxs-lookup"><span data-stu-id="7edc8-232">Notes on licensing</span></span>

<span data-ttu-id="7edc8-233">PowerShell Core는 [MIT 라이선스][]에서 릴리스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-233">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="7edc8-234">본 라이선스 및 유료 지원 계약이 안 된 경우 사용자는 [커뮤니티 지원][]으로 서비스가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-234">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="7edc8-235">커뮤니티 지원을 이용하더라도 Microsoft는 문의 응답 및 해결 방안을 보장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-235">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="7edc8-236">Windows PowerShell 모듈</span><span class="sxs-lookup"><span data-stu-id="7edc8-236">Windows PowerShell Module</span></span>

<span data-ttu-id="7edc8-237">PowerShell Core에 대한 지원은 명시적으로 이 모듈이 PowerShell Core를 지원하지 않는 한 다른 제품 모듈을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-237">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="7edc8-238">예를 들어, Windows Server에 부분적으로 제공되는 `ActiveDirectory` 모듈을 사용하는 경우 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-238">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="7edc8-239">그러나 PowerShell Core를 명시적으로 지원하지 않는 모듈은 경우에 따라 호환이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-239">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="7edc8-240">[`WindowsPSModulePath`][] 모듈을 설치하여 Windows PowerShell `PSModulePath`를 PowerShell Core `PSModulePath`에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-240">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="7edc8-241">먼저 PowerShell 갤러리에서 `WindowsPSModulePath` 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-241">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="7edc8-242">이 모듈을 설치한 후에, `Add-WindowsPSModulePath` cmdlet을 실행하여 Windows PowerShell `PSModulePath`를 PowerShell Core에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-242">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="7edc8-243">실험적 기능</span><span class="sxs-lookup"><span data-stu-id="7edc8-243">Experimental features</span></span>

<span data-ttu-id="7edc8-244">[실험적 기능][]은 [커뮤니티 지원](#community-support)으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="7edc8-244">[Experimental features][] are limited to [community support](#community-support).</span></span>

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
[실험적 기능]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
