---
title: 도움말 시스템
description: PowerShell을 제대로 활용하려면 도움말 시스템을 숙지해야 합니다.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: cfb12f57b7bb6c514f4e19a93dfe9c77245bd977
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99601235"
---
# <a name="chapter-2---the-help-system"></a><span data-ttu-id="7eb1c-103">2장 - 도움말 시스템</span><span class="sxs-lookup"><span data-stu-id="7eb1c-103">Chapter 2 - The Help System</span></span>

<span data-ttu-id="7eb1c-104">두 IT 전문가 그룹이 PowerShell을 관련 기술 수준 확인을 위해 컴퓨터를 이용할 수 없는 필기시험을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-104">Two groups of IT pros were given a written test without access to a computer to determine their skill level with PowerShell.</span></span> <span data-ttu-id="7eb1c-105">한 그룹에는 PowerShell 초보자가 배정되고 다른 그룹에는 전문가가 배정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-105">PowerShell beginners were placed in one group and experts in another.</span></span>
<span data-ttu-id="7eb1c-106">테스트 결과 두 그룹 간의 기술 수준은 큰 차이가 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-106">Based on the results of the test, there didn't seem to be much difference in the skill level between the two groups.</span></span> <span data-ttu-id="7eb1c-107">두 그룹 모두 첫 번째 테스트와 유사한 두 번째 테스트를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-107">Both groups were given a second test similar to the first one.</span></span> <span data-ttu-id="7eb1c-108">이번에는 PowerShell이 설치된 컴퓨터가 제공되었지만 인터넷에 액세스할 수는 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-108">This time they were given access to a computer with PowerShell that didn't have access to the internet.</span></span> <span data-ttu-id="7eb1c-109">두 번째 테스트 결과에서는 두 그룹 간의 기술 수준 차이가 대단히 컸습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-109">The results of the second test showed a huge difference in the skill level between the two groups.</span></span> <span data-ttu-id="7eb1c-110">전문가 집단은 정답을 모를 때도 있었지만 정답을 파악하는 방법은 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-110">Experts don't always know the answers, but they know how to figure out the answers.</span></span>

<span data-ttu-id="7eb1c-111">첫 번째와 두 번째 테스트 결과가 두 그룹 사이에서 다르게 나타난 이유는 무엇일까요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-111">What was the difference in the results of the first and second test between these two groups?</span></span>

<span data-ttu-id="7eb1c-112">두 번의 테스트에서 차이가 나타난 이유는 전문가 집단은 PowerShell에서 수많은 명령을 사용하는 방법을 기억하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-112">The differences observed in these two tests were because experts don't memorize how to use thousands of commands in PowerShell.</span></span> <span data-ttu-id="7eb1c-113">그들은 PowerShell 내 도움말 시스템을 대단히 잘 활용하는 방법을 알고 있기에,</span><span class="sxs-lookup"><span data-stu-id="7eb1c-113">They learn how to use the help system within PowerShell extremely well.</span></span>
<span data-ttu-id="7eb1c-114">필요할 때 필요한 명령을 확인하고 확인한 명령의 사용 방법을 알아낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-114">This allows them to find the necessary commands when needed and how to use those commands once they've found them.</span></span>

<span data-ttu-id="7eb1c-115">PowerShell 개발자인 Jeffrey Snover가 이와 비슷한 이야기를 여러 번 들려주었습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-115">I've heard Jeffrey Snover, the inventor of PowerShell, tell a similar story a number of times.</span></span>

<span data-ttu-id="7eb1c-116">PowerShell을 제대로 활용하려면 도움말 시스템을 숙지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-116">Mastering the help system is the key to being successful with PowerShell.</span></span>

## <a name="discoverability"></a><span data-ttu-id="7eb1c-117">검색 기능</span><span class="sxs-lookup"><span data-stu-id="7eb1c-117">Discoverability</span></span>

<span data-ttu-id="7eb1c-118">PowerShell의 컴파일된 명령을 cmdlet이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-118">Compiled commands in PowerShell are called cmdlets.</span></span> <span data-ttu-id="7eb1c-119">Cmdlet은 (CMD let이 아닌) "command-let"으로 발음합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-119">Cmdlet is pronounced "command-let" (not CMD-let).</span></span> <span data-ttu-id="7eb1c-120">Cmdlet 이름은 단수형 "동사-명사" 명령이기 때문에 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-120">Cmdlets names have the form of singular "Verb-Noun" commands to make them easily discoverable.</span></span> <span data-ttu-id="7eb1c-121">예를 들어 실행 중인 프로세스를 확인하는 cmdlet은 `Get-Process`이며 서비스 목록과 서비스 상태를 검색하는 cmdlet은 `Get-Service`입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-121">For example, the cmdlet for determining what processes are running is `Get-Process` and the cmdlet for retrieving a list of services and their statuses is `Get-Service`.</span></span> <span data-ttu-id="7eb1c-122">PowerShell에는이 책의 뒷부분에서 설명하는 별칭이나 함수 같은 다른 유형의 명령도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-122">There are other types of commands in PowerShell such as aliases and functions that will be covered later in this book.</span></span> <span data-ttu-id="7eb1c-123">PowerShell 명령이라는 용어는 cmdlet, 함수 또는 별칭을 아우르는 PowerShell에서 사용하는 모든 유형의 명령을 나타내는 일반적인 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-123">The term PowerShell command is a generic term that's often used to refer to any type of command in PowerShell, regardless of whether or not it's a cmdlet, function, or alias.</span></span>

## <a name="the-three-core-cmdlets-in-powershell"></a><span data-ttu-id="7eb1c-124">PowerShell의 세 가지 주요 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7eb1c-124">The Three Core Cmdlets in PowerShell</span></span>

- `Get-Command`
- `Get-Help`
- <span data-ttu-id="7eb1c-125">`Get-Member`(3장에서 설명)</span><span class="sxs-lookup"><span data-stu-id="7eb1c-125">`Get-Member` (covered in chapter 3)</span></span>

<span data-ttu-id="7eb1c-126">필자가 자주 하는 질문은 PowerShell에서 명령을 어떻게 확인할 수 있는가입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-126">One question I'm often asked is how do you figure out what the commands are in PowerShell?</span></span> <span data-ttu-id="7eb1c-127">`Get-Command`와 `Get-Help`는 둘 다 명령을 확인하는 용도로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-127">Both `Get-Command` and `Get-Help` can be used to determine the commands.</span></span>

## <a name="get-help"></a><span data-ttu-id="7eb1c-128">Get-Help</span><span class="sxs-lookup"><span data-stu-id="7eb1c-128">Get-Help</span></span>

<span data-ttu-id="7eb1c-129">`Get-Help`는 다목적 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-129">`Get-Help` is a multipurpose command.</span></span> <span data-ttu-id="7eb1c-130">`Get-Help`를 이용하면 찾아낸 명령의 사용 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-130">`Get-Help` helps you learn how to use commands once you find them.</span></span> <span data-ttu-id="7eb1c-131">`Get-Help`는 명령을 찾을 때도 도움이 되지만 `Get-Command`와 비교하면 좀 더 간접적인 방법으로 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-131">`Get-Help` can also be used to help locate commands, but in a different and more indirect way when compared to `Get-Command`.</span></span>

<span data-ttu-id="7eb1c-132">`Get-Help`로 명령을 찾을 때는 제공된 입력을 바탕으로 명령 이름의 와일드카드 일치 항목을 먼저 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-132">When `Get-Help` is used to locate commands, it first searches for wildcard matches of command names based on the provided input.</span></span> <span data-ttu-id="7eb1c-133">일치 항목이 없다면 도움말 항목 전체를 검색하며, 그래도 일치하는 항목이 없으면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-133">If it doesn't find a match, it searches through the help topics themselves, and if no match is found an error is returned.</span></span> <span data-ttu-id="7eb1c-134">많은 이들의 생각과는 달리 `Get-Help`로 도움말 항목이 없는 명령도 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-134">Contrary to popular belief, `Get-Help` can be used to find commands that don't have help topics.</span></span>

<span data-ttu-id="7eb1c-135">PowerShell의 도움말 시스템에 대해 가장 먼저 알아야 할 사항은 `Get-Help` cmdlet을 사용하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-135">The first thing you need to know about the help system in PowerShell is how to use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="7eb1c-136">다음 명령은 `Get-Help` 관련 도움말 항목을 표시할 때 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-136">The following command is used to display the help topic for `Get-Help`.</span></span>

```powershell
Get-Help -Name Get-Help
```

```Output
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="7eb1c-137">PowerShell 도움말은 PowerShell 버전 3부터는 운영 체제와 함께 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-137">Beginning with PowerShell version 3, PowerShell help doesn't ship with the operating system.</span></span> <span data-ttu-id="7eb1c-138">명령에 대해 `Get-Help`를 처음 실행하면 앞의 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-138">The first time `Get-Help` is run for a command, the previous message is displayed.</span></span> <span data-ttu-id="7eb1c-139">`Get-Help` cmdlet 대신 `help` 함수나 `man` 별칭을 사용하면 이 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-139">If the `help` function or `man` alias is used instead of the `Get-Help` cmdlet, you don't receive this prompt.</span></span>

<span data-ttu-id="7eb1c-140"><kbd>Y</kbd>를 눌러 수락한다고 답변하면 기본적으로 인터넷 액세스를 요구하는 `Update-Help` cmdlet이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-140">Answering yes by pressing <kbd>Y</kbd> runs the `Update-Help` cmdlet, which requires internet access by default.</span></span> <span data-ttu-id="7eb1c-141">`Y`는 대문자와 소문자를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-141">`Y` can be specified in either upper or lower case.</span></span>

<span data-ttu-id="7eb1c-142">도움말이 다운로드되고 업데이트가 끝나면 지정된 명령에 대한 도움말 항목이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-142">Once the help is downloaded and the update is complete, the help topic is returned for the specified command:</span></span>

```powershell
Get-Help -Name Get-Help
```

<span data-ttu-id="7eb1c-143">잠시 시간을 내 컴퓨터에서 이 예제를 실행하고, 출력을 검토하고, 정보를 그룹화하는 방법을 기록해 보세요.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-143">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="7eb1c-144">NAME</span><span class="sxs-lookup"><span data-stu-id="7eb1c-144">NAME</span></span>
- <span data-ttu-id="7eb1c-145">개요</span><span class="sxs-lookup"><span data-stu-id="7eb1c-145">SYNOPSIS</span></span>
- <span data-ttu-id="7eb1c-146">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7eb1c-146">SYNTAX</span></span>
- <span data-ttu-id="7eb1c-147">설명</span><span class="sxs-lookup"><span data-stu-id="7eb1c-147">DESCRIPTION</span></span>
- <span data-ttu-id="7eb1c-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7eb1c-148">RELATED LINKS</span></span>
- <span data-ttu-id="7eb1c-149">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7eb1c-149">REMARKS</span></span>

<span data-ttu-id="7eb1c-150">화면에서처럼 도움말 항목은 방대한 정보를 포함할 수 있으며, 이 역시 전체 도움말 항목은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-150">As you can see, help topics can contain an enormous amount of information and this isn't even the entire help topic.</span></span>

<span data-ttu-id="7eb1c-151">PowerShell 전용 기능은 아니지만 매개 변수로도 명령에 입력을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-151">While not specific to PowerShell, a parameter is a way to provide input to a command.</span></span> <span data-ttu-id="7eb1c-152">`Get-Help`에는 전체 도움말 항목이나 항목 하위 집합을 반환하도록 지정할 수 있는 다양한 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-152">`Get-Help` has many parameters that can be specified in order to return the entire help topic or a subset of it.</span></span>

<span data-ttu-id="7eb1c-153">앞의 결과 집합에 표시되는 도움말 항목의 구문 섹션에는 `Get-Help`용 매개 변수가 모두 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-153">The syntax section of the help topic shown in the previous set of results lists all of the parameters for `Get-Help`.</span></span> <span data-ttu-id="7eb1c-154">언뜻 보기에는 동일한 매개 변수가 6번 나열되는 것처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-154">At first glance, it appears the same parameters are listed six different times.</span></span> <span data-ttu-id="7eb1c-155">구문 섹션에 있는 각 블록이 매개 변수 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-155">Each of those different blocks in the syntax section is a parameter set.</span></span> <span data-ttu-id="7eb1c-156">즉 `Get-Help` cmdlet에는 서로 다른 매개 변수 6개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-156">This means the `Get-Help` cmdlet has six different parameter sets.</span></span> <span data-ttu-id="7eb1c-157">자세히 살펴보면 각 매개 변수 집합에서 고유한 매개 변수가 하나 이상 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-157">If you take a closer look, you'll notice that at least one parameter is different in each of the parameter sets.</span></span>

<span data-ttu-id="7eb1c-158">매개 변수 집합은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-158">Parameter sets are mutually exclusive.</span></span> <span data-ttu-id="7eb1c-159">특정 매개 변수 집합에만 존재하는 고유 매개 변수를 사용하면 해당 매개 변수 집합에 있는 매개 변수만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-159">Once a unique parameter that only exists in one of the parameter sets is used, only parameters contained within that parameter set can be used.</span></span> <span data-ttu-id="7eb1c-160">예를 들어 **Full** 과 **Detailed** 매개 변수는 서로 다른 매개 변수 집합에 있기 때문에 동시에 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-160">For example, both the **Full** and **Detailed** parameters couldn't be specified at the same time because they are in different parameter sets.</span></span>

<span data-ttu-id="7eb1c-161">다음 매개 변수는 각각 서로 다른 매개 변수 집합에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-161">Each of the following parameters are in different parameter sets:</span></span>

- <span data-ttu-id="7eb1c-162">전체</span><span class="sxs-lookup"><span data-stu-id="7eb1c-162">Full</span></span>
- <span data-ttu-id="7eb1c-163">Detailed</span><span class="sxs-lookup"><span data-stu-id="7eb1c-163">Detailed</span></span>
- <span data-ttu-id="7eb1c-164">예제</span><span class="sxs-lookup"><span data-stu-id="7eb1c-164">Examples</span></span>
- <span data-ttu-id="7eb1c-165">온라인</span><span class="sxs-lookup"><span data-stu-id="7eb1c-165">Online</span></span>
- <span data-ttu-id="7eb1c-166">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7eb1c-166">Parameter</span></span>
- <span data-ttu-id="7eb1c-167">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="7eb1c-167">ShowWindow</span></span>

<span data-ttu-id="7eb1c-168">구문 섹션의 대괄호와 꺾쇠 괄호 같은 모든 암호화 구문은 저마다 의미가 있지만 이 책의 부록 A에서 다루는 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-168">All of the cryptic syntax such as square and angle brackets in the syntax section means something but will be covered in Appendix A of this book.</span></span> <span data-ttu-id="7eb1c-169">중요한 내용이긴 하지만 암호화 구문은 PowerShell 초보자에게는 어려운 내용이며 매일 사용하는 기능도 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-169">While important, learning the cryptic syntax is often difficult to retain for someone who is new to PowerShell and may not use it everyday.</span></span>

<span data-ttu-id="7eb1c-170">암호화 구문에 관한 자세한 정보를 알고 싶다면 [부록 A][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-170">For more information to better understand the cryptic syntax, see [Appendix A][].</span></span>

<span data-ttu-id="7eb1c-171">초보자에게는 같은 정보를 평이한 말로 설명하는 더 쉬운 방법을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-171">For beginners, there's an easier way to figure out the same information except in plain language.</span></span>

<span data-ttu-id="7eb1c-172">`Get-Help`의 **Full** 매개 변수가 지정되면 전체 도움말 항목이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-172">When the **Full** parameter of `Get-Help` is specified, the entire help topic is returned.</span></span>

```powershell
Get-Help -Name Get-Help -Full
```

<span data-ttu-id="7eb1c-173">잠시 시간을 내 컴퓨터에서 이 예제를 실행하고, 출력을 검토하고, 정보를 그룹화하는 방법을 기록해 보세요.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-173">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="7eb1c-174">NAME</span><span class="sxs-lookup"><span data-stu-id="7eb1c-174">NAME</span></span>
- <span data-ttu-id="7eb1c-175">개요</span><span class="sxs-lookup"><span data-stu-id="7eb1c-175">SYNOPSIS</span></span>
- <span data-ttu-id="7eb1c-176">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7eb1c-176">SYNTAX</span></span>
- <span data-ttu-id="7eb1c-177">설명</span><span class="sxs-lookup"><span data-stu-id="7eb1c-177">DESCRIPTION</span></span>
- <span data-ttu-id="7eb1c-178">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7eb1c-178">PARAMETERS</span></span>
- <span data-ttu-id="7eb1c-179">입력</span><span class="sxs-lookup"><span data-stu-id="7eb1c-179">INPUTS</span></span>
- <span data-ttu-id="7eb1c-180">출력</span><span class="sxs-lookup"><span data-stu-id="7eb1c-180">OUTPUTS</span></span>
- <span data-ttu-id="7eb1c-181">참고</span><span class="sxs-lookup"><span data-stu-id="7eb1c-181">NOTES</span></span>
- <span data-ttu-id="7eb1c-182">예제</span><span class="sxs-lookup"><span data-stu-id="7eb1c-182">EXAMPLES</span></span>
- <span data-ttu-id="7eb1c-183">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7eb1c-183">RELATED LINKS</span></span>

<span data-ttu-id="7eb1c-184">**Full** 매개 변수를 사용하면 몇 가지 추가 섹션이 반환됩니다. 그중에는 암호화 SYNTAX 섹션에 비해 더 자세한 정보를 제공하는 PARAMETERS 섹션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-184">Notice that using the **Full** parameter returned several additional sections, one of which is the PARAMETERS section that provides more information than the cryptic SYNTAX section.</span></span>

<span data-ttu-id="7eb1c-185">**Full** 매개 변수는 스위치 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-185">The **Full** parameter is a switch parameter.</span></span> <span data-ttu-id="7eb1c-186">값을 요구하지 않는 매개 변수를 스위치 매개 변수라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-186">A parameter that doesn't require a value is called a switch parameter.</span></span> <span data-ttu-id="7eb1c-187">스위치 매개 변수가 지정되면 값은 true이고 지정되지 않으면 값은 false입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-187">When a switch parameter is specified, its value is true and when it's not, its value is false.</span></span>

<span data-ttu-id="7eb1c-188">PowerShell 콘솔에서 이 장을 작업하고 있다면 이전 명령은 `Get-Help`에 대한 전체 도움말 항목을 표시하기 때문에 읽을 수가 없을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-188">If you've been working through this chapter in the PowerShell console, you noticed that the previous command to display the full help topic for `Get-Help` flew by on the screen without giving you a chance to read it.</span></span> <span data-ttu-id="7eb1c-189">더 나은 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-189">There's a better way.</span></span>

<span data-ttu-id="7eb1c-190">`Help`는 `Get-Help`를 `more`이라는 함수에 파이프합니다. 이 함수는 Windows `more.com` 실행 파일의 래퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-190">`Help` is a function that pipes `Get-Help` to a function named `more`, which is a wrapper for the `more.com` executable file in Windows.</span></span> <span data-ttu-id="7eb1c-191">PowerShell 콘솔에서 `help`는 도움말 페이지를 한 번에 하나씩 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-191">In the PowerShell console, `help` provides one page of help at a time.</span></span> <span data-ttu-id="7eb1c-192">ISE에서 이 기능은 `Get-Help`와 동일한 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-192">In the ISE, it works the same way as `Get-Help`.</span></span> <span data-ttu-id="7eb1c-193">필자는 `Get-Help` 대신 `help` cmdlet 사용을 권장합니다. 사용 환경이 더 낫고 입력할 내용이 적기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-193">My recommendation is to use the `help` function instead of the `Get-Help` cmdlet since it provides a better experience and it's less to type.</span></span>

<span data-ttu-id="7eb1c-194">하지만 입력할 내용이 적다는 것이 항상 좋은 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-194">Less typing isn't always a good thing, however.</span></span> <span data-ttu-id="7eb1c-195">명령을 스크립트로 저장하거나 다른 사용자와 공유하려면 전체 cmdlet 및 매개 변수 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-195">If you're going to save your commands as a script or share them with someone else, be sure to use full cmdlet and parameter names.</span></span> <span data-ttu-id="7eb1c-196">전체 이름은 자체 문서화되므로 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-196">The full names are self-documenting, which makes them easier to understand.</span></span> <span data-ttu-id="7eb1c-197">여러분의 명령을 읽고 이해해야 하는 다음 사람을 생각해 보세요.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-197">Think about the next person that has to read and understand your commands.</span></span> <span data-ttu-id="7eb1c-198">그 사람이 여러분일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-198">It could be you.</span></span> <span data-ttu-id="7eb1c-199">동료와 미래의 여러분이 지금의 여러분에게 감사할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-199">Your coworkers and future self will thank you.</span></span>

<span data-ttu-id="7eb1c-200">Windows 10 랩 환경 컴퓨터의 PowerShell 콘솔에서 다음 명령을 실행해 보세요.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-200">Try running the following commands in the PowerShell console on your Windows 10 lab environment computer.</span></span>

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

<span data-ttu-id="7eb1c-201">Windows 10 랩 환경 컴퓨터에서 앞에 나온 명령을 실행했을 때 출력에 차이가 있음을 눈치채셨나요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-201">Did you notice any differences in the output from the previously listed commands when you ran them on your Windows 10 lab environment computer?</span></span>

<span data-ttu-id="7eb1c-202">마지막 두 옵션이 결과를 한 번에 한 페이지씩 반환한다는 것 외에는 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-202">There aren't any differences other than the last two options return the results one page at a time.</span></span>
<span data-ttu-id="7eb1c-203">`Help` 함수를 사용할 때는 <kbd>스페이스바</kbd>로 콘텐츠 다음 페이지를 표시하며 <kbd>Ctrl</kbd>+<kbd>C</kbd>는 PowerShell 콘솔에서 실행 중인 명령을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-203">The <kbd>spacebar</kbd> is used to display the next page of content when using the `Help` function and <kbd>Ctrl</kbd>+<kbd>C</kbd> cancels commands that are running in the PowerShell console.</span></span>

<span data-ttu-id="7eb1c-204">첫 번째 예제에서는 `Get-Help` cmdlet을 사용하고, 두 번째에서는 `Help` 함수를 사용하며, 세 번째에서는 `Help` 함수를 사용할 때 **Name** 매개 변수를 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-204">The first example uses the `Get-Help` cmdlet, the second uses the `Help` function, and the third omits the **Name** parameter when using the `Help` function.</span></span> <span data-ttu-id="7eb1c-205">**Name** 은 위치 매개 변수이며 해당 예제에서 위치를 기준으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-205">**Name** is a positional parameter and it's being used positionally in that example.</span></span> <span data-ttu-id="7eb1c-206">따라서 값 자체를 올바른 위치에 지정한다면 매개 변수 이름을 지정하지 않고도 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-206">This means the value can be specified without specifying the parameter name, as long as the value itself is specified in the correct position.</span></span> <span data-ttu-id="7eb1c-207">필자는 값을 지정할 위치를 어떻게 알았을까요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-207">How did I know what position to specify the value in?</span></span> <span data-ttu-id="7eb1c-208">다음 예제에 나오는 도움말을 읽었기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-208">By reading the help as shown in the following example.</span></span>

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

<span data-ttu-id="7eb1c-209">앞의 예제에서는 **Parameter** 매개 변수를 Help 함수와 함께 사용하여 **Name** 매개 변수에 대한 도움말 항목의 정보만 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-209">Notice that in the previous example, the **Parameter** parameter was used with the Help function to only return information from the help topic for the **Name** parameter.</span></span> <span data-ttu-id="7eb1c-210">때로는 수백 페이지에 달하는 것처럼 보이기도 하는 도움말 항목 전체를 일일이 살펴보는 방법보다 훨씬 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-210">This is much more concise than trying to manually sift through what sometimes seems like a hundred page help topic.</span></span>

<span data-ttu-id="7eb1c-211">이러한 결과를 살펴보면 **Name** 매개 변수는 위치적이며, 위치를 기준으로 사용될 때는 위치 0(첫 번째 위치)에 지정해야 함을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-211">Based on those results, you can see that the **Name** parameter is positional and must be specified in position zero (the first position) when used positionally.</span></span> <span data-ttu-id="7eb1c-212">매개 변수 이름을 지정했다면 매개 변수가 지정되는 순서는 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-212">The order that parameters are specified in doesn't matter if the parameter name is specified.</span></span>

<span data-ttu-id="7eb1c-213">또 다른 중요 정보는 **Name** 매개 변수가 자신의 값에 대한 데이터 유형이 `<String>`으로 표시되는 단일 문자열이라 예상한다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-213">One other important piece of information is that the **Name** parameter expects the datatype for its value to be a single string, which is denoted by `<String>`.</span></span> <span data-ttu-id="7eb1c-214">여러 문자열을 허용하는 경우 데이터 유형은 `<String[]>`으로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-214">If it accepted multiple strings, the datatype would be listed as `<String[]>`.</span></span>

<span data-ttu-id="7eb1c-215">명령에 대한 전체 도움말 항목을 표시하고 싶지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-215">Sometimes you simply don't want to display the entire help topic for a command.</span></span> <span data-ttu-id="7eb1c-216">**Full** 외에도 다양한 매개 변수를 `Get-Help` 또는 `Help`를 이용해 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-216">There are a number of other parameters besides **Full** that can be specified with `Get-Help` or `Help`.</span></span> <span data-ttu-id="7eb1c-217">Windows 10 랩 환경 컴퓨터에서 다음 명령을 실행해 보세요.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-217">Try running the following commands on your Windows 10 lab environment computer:</span></span>

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

<span data-ttu-id="7eb1c-218">필자는 일반적으로 `help <command name>`를 **Full** 또는 **Online** 매개 변수와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-218">I typically use `help <command name>` with the **Full** or **Online** parameter.</span></span> <span data-ttu-id="7eb1c-219">예제에만 관심이 있다면 **Examples** 매개 변수를 사용하고, 특정 매개 변수에만 관심이 있다면 **Parameter** 매개 변수를 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-219">If I'm only interested in the examples, I'll use the **Examples** parameter and if I'm only interested in a specific parameter, I'll use the **Parameter** parameter.</span></span> <span data-ttu-id="7eb1c-220">**ShowWindow** 매개 변수는 여러 모니터를 사용할 경우 다른 모니터에 배치할 수 있는 별도의 검색 가능한 창에서 도움말 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-220">The **ShowWindow** parameter opens the help topic in a separate searchable window that can be placed on a different monitor if you have multiple monitors.</span></span> <span data-ttu-id="7eb1c-221">전체 도움말 항목을 표시하지 않는 확인된 버그가 있으므로 필자는 **ShowWindow** 매개 변수를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-221">I've avoided the **ShowWindow** parameter because there's a known bug where it doesn't display the entire help topic.</span></span>

<span data-ttu-id="7eb1c-222">별도의 창에 도움말을 표시하려면 다음 예제에서처럼 **Online** 매개 변수를 사용하거나 **Full** 매개 변수를 사용하고 결과를 `Out-GridView`로 파이프하는 방법을 추천합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-222">If you want help in a separate window, my recommendation is to either use the **Online** parameter or use the **Full** parameter and pipe the results to `Out-GridView`, as shown in the following example.</span></span>

```powershell
help Get-Command -Full | Out-GridView
```

<span data-ttu-id="7eb1c-223">`Out-GridView` cmdlet와 `Get-Help` cmdlet의 **ShowWindow** 매개 변수는 모두 GUI(그래픽 사용자 인터페이스)를 사용하는 운영 체제가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-223">Both the `Out-GridView` cmdlet and the **ShowWindow** parameter of the `Get-Help` cmdlet require an operating system with a GUI (Graphical User Interface).</span></span> <span data-ttu-id="7eb1c-224">(GUI를 사용하지 않는) 서버 코어 설치 옵션을 사용하여 설치된 Windows Server에서 둘 중 하나를 사용하면 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-224">They will generate an error message if you attempt to use either of them on Windows Server that's been installed using the server core (no-GUI) installation option.</span></span>

<span data-ttu-id="7eb1c-225">`Get-Help`를 사용하여 명령을 찾으려면 별표(`*`) 와일드카드 문자와 **Name** 매개 변수를 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-225">To use `Get-Help` to find commands, use the asterisk (`*`) wildcard character with the **Name** parameter.</span></span> <span data-ttu-id="7eb1c-226">다음 예제에서처럼 명령에 대한 검색어를 **Name** 매개 변수에 대한 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-226">Specify a term that you're searching for commands on as the value for the **Name** parameter as shown in the following example.</span></span>

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

<span data-ttu-id="7eb1c-227">앞의 예제에서는 `*` 와일드카드 문자가 필요하지 않으며 생략해도 결과는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-227">In the previous example, the `*` wildcard characters are not required and omitting them produces the same result.</span></span> <span data-ttu-id="7eb1c-228">`Get-Help`는 사용자를 대신해 와일드카드 문자를 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-228">`Get-Help` automatically adds the wildcard characters behind the scenes.</span></span>

```powershell
help process
```

<span data-ttu-id="7eb1c-229">앞의 명령은 프로세스의 끝부분마다 `*` 와일드카드 문자를 지정하는 것과 동일한 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-229">The previous command produces the same results as specifying the `*` wildcard character on each end of process.</span></span>

<span data-ttu-id="7eb1c-230">항상 일관적으로 작동하는 옵션이기 때문에 필는 자주 추가하는 편입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-230">I prefer to add them since that's the option that always works consistently.</span></span> <span data-ttu-id="7eb1c-231">추가하지 않으면 특정 시나리오에서는 필요하지만 다른 시나리오에서는 필요하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-231">Otherwise, they are required in certain scenarios and not others.</span></span> <span data-ttu-id="7eb1c-232">값 중간에 와일드카드 문자를 추가하면 사용자가 지정된 값에 자동으로 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-232">As soon as you add a wildcard character in the middle of the value, they're no longer automatically added behind the scenes to the value you specified.</span></span>

```powershell
help pr*cess
```

<span data-ttu-id="7eb1c-233">`pr*cess`의 시작과 끝에 `*` 와일드카드 문자를 추가하지 않으면 해당 명령은 어떤 결과도 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-233">No results are returned by that command unless the `*` wildcard character is added to the beginning, end, or both the beginning and end of `pr*cess`.</span></span>

<span data-ttu-id="7eb1c-234">지정한 값이 대시로 시작한다면 PowerShell이 이를 매개 변수 이름으로 해석하고 `Get-Help` cmdlet의 매개 변수 이름은 존재하지 않기 때문에 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-234">If the value you specified begins with a dash, then an error is generated because PowerShell interprets it as a parameter name and no such parameter name exists for the `Get-Help` cmdlet.</span></span>

```powershell
help -process
```

<span data-ttu-id="7eb1c-235">찾으려는 항목이 `-process`로 끝나는 명령이라면 값의 시작 부분에 `*` 와일드카드 문자를 추가하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-235">If what you're attempting to look for are commands that end with `-process`, you only need to add the `*` wildcard character to the beginning of the value.</span></span>

```powershell
help *-process
```

<span data-ttu-id="7eb1c-236">`Get-Help`를 사용하여 PowerShell 명령을 검색할 때는 검색 대상을 너무 구체적으로 지정하지 말고 조금 모호하게 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-236">When searching for PowerShell commands with `Get-Help`, you want to be a little more vague instead of being too specific with what you're searching for.</span></span>

<span data-ttu-id="7eb1c-237">앞에서 `process`를 검색했을 때는 명령 이름에 `process`가 있는 명령만 발견하고 관련 결과만 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-237">Searching for `process` earlier found only commands that contained `process` in the name of the command and returned only those results.</span></span> <span data-ttu-id="7eb1c-238">`Get-Help`를 사용하여 `processes`를 검색한다면 명령 이름에 일치하는 항목을 찾지 못하기 때문에 시스템에서 PowerShell의 모든 도움말 항목을 검색하고 발견한 일치 항목을 모두 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-238">When `Get-Help` is used to search for `processes`, it doesn't find any matches for command names, so it performs a search of every help topic in PowerShell on your system and returns any matches it finds.</span></span> <span data-ttu-id="7eb1c-239">따라서 엄청난 수의 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-239">This causes it to return an enormous number of results.</span></span>

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

<span data-ttu-id="7eb1c-240">`Help`를 사용하여 `process`를 검색하면 결과 10개가 반환되고 `processes`를 검색하면 결과 68개가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-240">Using `Help` to search for `process` returned 10 results and using it to search for `processes` returned 68 results.</span></span> <span data-ttu-id="7eb1c-241">결과가 하나만 있다면 명령 목록 대신 도움말 항목 자체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-241">If only one result is found, the help topic itself will be displayed instead of a list of commands.</span></span>

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

<span data-ttu-id="7eb1c-242">지금부터는 PowerShell에서 `Help`를 이용하면 도움말 항목이 있는 명령만 찾을 수 있다는 오해를 바로잡겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-242">Now to debunk the myth that `Help` in PowerShell can only find commands that have help topics.</span></span>

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

<span data-ttu-id="7eb1c-243">이전 예제에서 `more`에는 도움말 항목이 없지만 PowerShell의 `Help` 시스템에서 찾을 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-243">Notice in the previous example that `more` doesn't have a help topic, yet the `Help` system in PowerShell was able to find it.</span></span> <span data-ttu-id="7eb1c-244">일치 항목을 하나만 찾은 기본 구문 정보를 반환하기 때문에 명령은 도움말 항목이 없을 때 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-244">It only found one match and returned the basic syntax information that you'll see when a command doesn't have a help topic.</span></span>

<span data-ttu-id="7eb1c-245">PowerShell에는 다양한 개념적(About) 도움말 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-245">PowerShell contains numerous conceptual (About) help topics.</span></span> <span data-ttu-id="7eb1c-246">다음 명령을 사용하면 시스템의 모든 **About** 도움말 항목 목록이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-246">The following command can be used to return a list of all **About** help topics on your system.</span></span>

```powershell
help About_*
```

<span data-ttu-id="7eb1c-247">결과를 단일 About 도움말 항목으로 제한하면 목록 대신 실제 도움말 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-247">Limiting the results to one single About help topic displays the actual help topic instead of returning a list.</span></span>

```powershell
help about_Updatable_Help
```

<span data-ttu-id="7eb1c-248">**About** 도움말 항목이 존재하려면 PowerShell의 도움말 시스템을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-248">The help system in PowerShell has to be updated in order for the **About** help topics to be present.</span></span> <span data-ttu-id="7eb1c-249">컴퓨터에서 도움말 시스템의 초기 업데이트가 실패하면 `Update-Help` cmdlet이 성공적으로 실행될 때까지는 파일을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-249">If for some reason the initial update of the help system failed on your computer, the files will not be available until the `Update-Help` cmdlet has been run successfully.</span></span>

## <a name="get-command"></a><span data-ttu-id="7eb1c-250">Get-Command</span><span class="sxs-lookup"><span data-stu-id="7eb1c-250">Get-Command</span></span>

<span data-ttu-id="7eb1c-251">`Get-Command`는 명령을 쉽게 찾을 수 있도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-251">`Get-Command` is designed to help you locate commands.</span></span> <span data-ttu-id="7eb1c-252">매개 변수 없이 `Get-Command`를 실행하면 시스템의 모든 명령 목록이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-252">Running `Get-Command` without any parameters returns a list of all the commands on your system.</span></span> <span data-ttu-id="7eb1c-253">다음 예제는 `Get-Command` cmdlet을 사용하여 프로세스 작업에 사용할 수 있는 명령을 확인하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-253">The following example demonstrates using the `Get-Command` cmdlet to determine what commands exist for working with processes:</span></span>

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

<span data-ttu-id="7eb1c-254">`Get-Command`를 실행하는 이전 예제에서는 **Noun** 매개 변수를 사용하고 `Process`를 **Noun** 매개 변수의 값으로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-254">Notice in the previous example where `Get-Command` was run, the **Noun** parameter is used and `Process` is specified as the value for the **Noun** parameter.</span></span> <span data-ttu-id="7eb1c-255">`Get-Command` cmdlet 사용 방법을 모른다면 어떻게 해야 할까요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-255">What if you didn't know how to use the `Get-Command` cmdlet?</span></span> <span data-ttu-id="7eb1c-256">`Get-Help`를 사용하면 `Get-Command` 관련 도움말 항목을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-256">You could use `Get-Help` to display the help topic for `Get-Command`.</span></span>

<span data-ttu-id="7eb1c-257">**Name**, **Noun**, **Verb** 매개 변수는 와일드카드를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-257">The **Name**, **Noun**, and **Verb** parameters accept wildcards.</span></span> <span data-ttu-id="7eb1c-258">다음 예제에서는 **Name** 매개 변수와 함께 사용하는 와일드카드를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-258">The following example shows wildcards being used with the **Name** parameter:</span></span>

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

<span data-ttu-id="7eb1c-259">기본 PowerShell 명령이 아닌 실행 파일도 반환하기 때문에 필자는 `Get-Command`의 **Name** 매개 변수에서 와일드카드를 잘 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-259">I'm not a fan of using wildcards with the **Name** parameter of `Get-Command` since it also returns executable files that are not native PowerShell commands.</span></span>

<span data-ttu-id="7eb1c-260">**Name** 매개 변수를 와일드카드와 함께 사용하고 싶다면 **CommandType** 매개 변수를 사용하여 결과를 제한하는 방법을 추천합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-260">If you are going to use wildcard characters with the **Name** parameter, I recommend limiting the results with the **CommandType** parameter.</span></span>

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

<span data-ttu-id="7eb1c-261">더 좋은 방법은 **Verb** 또는 **Noun** 매개 변수를 사용하거나 둘 다 사용하는 것입니다. PowerShell 명령은 동사와 명사를 모두 지원하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-261">A better option is to use either the **Verb** or **Noun** parameter or both of them since only PowerShell commands have both verbs and nouns.</span></span>

<span data-ttu-id="7eb1c-262">도움말 항목 관련 문제가 있나요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-262">Found something wrong with a help topic?</span></span> <span data-ttu-id="7eb1c-263">다행히도 PowerShell의 도움말 항목은 오픈 소스이며 GitHub의 [PowerShell-Docs][] 리포지토리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-263">The good news is the help topics for PowerShell have been open-sourced and available in the [PowerShell-Docs][] repository on GitHub.</span></span> <span data-ttu-id="7eb1c-264">자신뿐만 아니라 다른 사용자를 위해서도 잘못된 정보를 수정하는 친절을 베풀어 보세요.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-264">Pay it forward by not only fixing the incorrect information for yourself, but everyone else as well.</span></span> <span data-ttu-id="7eb1c-265">GitHub에서 PowerShell 설명서 리포지토리를 포크하고, 도움말 항목을 업데이트한 다음 끌어오기 요청을 제출하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-265">Simply fork the PowerShell documentation repository on GitHub, update the help topic, and submit a pull request.</span></span>
<span data-ttu-id="7eb1c-266">끌어오기 요청이 수락되면 모든 사용자가 수정된 설명서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-266">Once the pull request is accepted, the corrected documentation is available for everyone.</span></span>

## <a name="updating-help"></a><span data-ttu-id="7eb1c-267">도움말 업데이트</span><span class="sxs-lookup"><span data-stu-id="7eb1c-267">Updating Help</span></span>

<span data-ttu-id="7eb1c-268">PowerShell 도움말 항목의 로컬 복사본은 명령에 대한 도움말을 처음 요청했을 때 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-268">The local copy of the PowerShell help topics was previously updated the first-time help on a command was requested.</span></span> <span data-ttu-id="7eb1c-269">도움말 콘텐츠는 때때로 업데이트되므로 도움말 시스템을 주기적으로 업데이트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-269">It's recommended to periodically update the help system because there can be updates to the help content from time to time.</span></span> <span data-ttu-id="7eb1c-270">`Update-Help` cmdlet은 도움말 항목을 업데이트하는 용도로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-270">The `Update-Help` cmdlet is used to update the help topics.</span></span>
<span data-ttu-id="7eb1c-271">기본적으로 인터넷 액세스를 요구하며 사용자는 관리자 자격으로 PowerShell을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-271">It requires internet access by default and for you to be running PowerShell elevated as an administrator.</span></span>

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : Unable to retrieve the HelpInfo XML file for UI culture en-US. Make sure the HelpInfoUri
property in the module manifest is valid or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

<span data-ttu-id="7eb1c-272">몇 개의 모듈에서 오류를 반환했지만 일반적인 일은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-272">A couple of the modules returned errors, which is not uncommon.</span></span> <span data-ttu-id="7eb1c-273">컴퓨터가 인터넷에 연결되어 있지 않다면 인터넷에 액세스할 수 있는 다른 컴퓨터에서 `Save-Help` cmdlet을 사용하여 업데이트된 도움말 정보를 네트워크상의 파일 공유에 먼저 저장한 다음 `Update-Help`의 **SourcePath** 매개 변수를 사용하여 도움말 항목에 이 네트워크 위치를 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-273">If the machine didn't have internet access, you could use the `Save-Help` cmdlet on another machine that does have internet access to first save the updated help information to a file share on your network and then use the **SourcePath** parameter of `Update-Help` to specify this network location for the help topics.</span></span>

<span data-ttu-id="7eb1c-274">PowerShell에서 예약 작업을 설정하거나 프로젝트 스크립트에 일부 논리를 추가하여 컴퓨터의 도움말 콘텐츠를 정기적으로 업데이트하는 방법을 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-274">Consider setting up a scheduled task or adding some logic to your profile script in PowerShell to periodically update the help content on your computer.</span></span> <span data-ttu-id="7eb1c-275">프로필 스크립트는 이후 장에서 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-275">Profile scripts will be discussed in an upcoming chapter.</span></span>

## <a name="summary"></a><span data-ttu-id="7eb1c-276">요약</span><span class="sxs-lookup"><span data-stu-id="7eb1c-276">Summary</span></span>

<span data-ttu-id="7eb1c-277">이 장에서는 `Get-Help`와 `Get-Command`를 모두 사용하여 명령을 찾는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-277">In this chapter you've learned how to find commands with both `Get-Help` and `Get-Command`.</span></span> <span data-ttu-id="7eb1c-278">발견한 명령의 사용 방법을 도움말 시스템을 사용하여 확인하는 방법도 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-278">You've learned how to use the help system to figure out how to use commands once you find them.</span></span> <span data-ttu-id="7eb1c-279">그리고 업데이트를 사용할 수 있는 경우 도움말 항목의 내용을 업데이트하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-279">You've also learned how to update the content of the help topics when updates are available.</span></span>

<span data-ttu-id="7eb1c-280">하루에 PowerShell 명령을 하나씩 학습해 보시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-280">My challenge to you is to learn a PowerShell command a day.</span></span>

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a><span data-ttu-id="7eb1c-281">검토</span><span class="sxs-lookup"><span data-stu-id="7eb1c-281">Review</span></span>

1. <span data-ttu-id="7eb1c-282">`Get-Service`의 **DisplayName** 매개 변수는 위치적인가요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-282">Is the **DisplayName** parameter of `Get-Service` positional?</span></span>
1. <span data-ttu-id="7eb1c-283">`Get-Process` cmdlet에는 매개 변수 집합이 몇 개나 있나요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-283">How many parameter sets does the `Get-Process` cmdlet have?</span></span>
1. <span data-ttu-id="7eb1c-284">이벤트 로그를 처리하는 PowerShell 명령은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-284">What PowerShell commands exist for working with event logs?</span></span>
1. <span data-ttu-id="7eb1c-285">컴퓨터에서 실행 중인 PowerShell 프로세스 목록을 반환하는 PowerShell 명령은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-285">What is the PowerShell command for returning a list of PowerShell processes running on your computer?</span></span>
1. <span data-ttu-id="7eb1c-286">컴퓨터에 저장된 PowerShell 도움말 콘텐츠를 업데이트하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="7eb1c-286">How do you update the PowerShell help content that's stored on your computer?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="7eb1c-287">권장 참조 항목</span><span class="sxs-lookup"><span data-stu-id="7eb1c-287">Recommended Reading</span></span>

<span data-ttu-id="7eb1c-288">이 장에서 다루는 항목에 대한 자세한 정보를 확인하려면 다음 PowerShell 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-288">If you want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="7eb1c-289">[Get-Help][]</span><span class="sxs-lookup"><span data-stu-id="7eb1c-289">[Get-Help][]</span></span>
- <span data-ttu-id="7eb1c-290">[Get-Command][]</span><span class="sxs-lookup"><span data-stu-id="7eb1c-290">[Get-Command][]</span></span>
- <span data-ttu-id="7eb1c-291">[Update-Help][]</span><span class="sxs-lookup"><span data-stu-id="7eb1c-291">[Update-Help][]</span></span>
- <span data-ttu-id="7eb1c-292">[Save-Help][]</span><span class="sxs-lookup"><span data-stu-id="7eb1c-292">[Save-Help][]</span></span>
- <span data-ttu-id="7eb1c-293">[about_Updatable_Help][]</span><span class="sxs-lookup"><span data-stu-id="7eb1c-293">[about_Updatable_Help][]</span></span>
- <span data-ttu-id="7eb1c-294">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="7eb1c-294">[about_Command_Syntax][]</span></span>

<span data-ttu-id="7eb1c-295">다음 장에서는 `Get-Member` cmdlet과 개체, 속성, 메서드를 함께 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7eb1c-295">In the next chapter, you'll learn about the `Get-Member` cmdlet as well as objects, properties, and methods.</span></span>

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[부록 A]: appendix-a.md
[Appendix A]: appendix-a.md
