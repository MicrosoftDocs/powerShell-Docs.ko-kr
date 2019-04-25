---
ms.date: 08/24/2018
keywords: powershell,cmdlet
title: PowerShell 명령 이름 학습
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 8d50ca03f98ed4ca8f9c09c83ae57afbf0d7888d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086428"
---
# <a name="learning-powershell-command-names"></a><span data-ttu-id="82c43-103">PowerShell 명령 이름 학습</span><span class="sxs-lookup"><span data-stu-id="82c43-103">Learning PowerShell command names</span></span>

<span data-ttu-id="82c43-104">명령 및 매개 변수의 이름을 학습하는 것은 대부분의 명령줄 인터페이스에서 상당한 시간이 소요됩니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-104">Learning names of commands and parameters requires a significant time investment with most command-line interfaces.</span></span> <span data-ttu-id="82c43-105">이러한 문제는 몇 가지 패턴에 따라 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-105">The issue is that there are few patterns.</span></span> <span data-ttu-id="82c43-106">정기적으로 사용해야 하는 명령과 매개 변수를 배우는 유일한 방법은 외우는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-106">Memorization is the only way to learn the commands and parameters that you need to use on a regular basis.</span></span>

<span data-ttu-id="82c43-107">새 명령 또는 매개 변수를 사용할 때 항상 이미 알고 있는 것을 사용할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-107">When you work with a new command or parameter, you can't always use what you already know.</span></span> <span data-ttu-id="82c43-108">새 이름을 찾아 학습해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-108">You have to find and learn a new name.</span></span> <span data-ttu-id="82c43-109">일반적으로 명령줄 인터페이스는 하나의 작은 툴 세트로 시작해서 점점 증가하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-109">Traditionally, command-line interfaces start with a small set of tools and grow with incremental additions.</span></span> <span data-ttu-id="82c43-110">표준 구조가 없는 이유도 쉽게 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-110">It's easy to see why there's no standard structure.</span></span>
<span data-ttu-id="82c43-111">각 명령이 별도 도구이므로 명령의 이름에는 이러한 방식이 논리적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-111">This seems logical for command names since each command is a separate tool.</span></span> <span data-ttu-id="82c43-112">PowerShell에는 명령 이름을 처리하는 더 좋은 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-112">PowerShell has a better way to handle command names.</span></span>

## <a name="learning-command-names-in-traditional-shells"></a><span data-ttu-id="82c43-113">기존 셸에서 명령 이름 학습</span><span class="sxs-lookup"><span data-stu-id="82c43-113">Learning command names in traditional shells</span></span>

<span data-ttu-id="82c43-114">대부분의 명령은 서비스나 프로세스와 같은 운영 체제 또는 응용 프로그램의 요소를 관리하도록 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-114">Most commands are built to manage elements of the operating system or applications, such as services or processes.</span></span> <span data-ttu-id="82c43-115">명령의 이름은 패밀리에 맞거나 맞지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-115">The commands have names that may or may not fit into a family.</span></span> <span data-ttu-id="82c43-116">예를 들어 Windows 시스템에서는 `net start` 및 `net stop` 명령을 사용하여 서비스를 시작하고 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-116">For example, on Windows systems, you can use the `net start` and `net stop` commands to start and stop a service.</span></span> <span data-ttu-id="82c43-117">**Sc.exe**는 또 다른 Windows용 서비스 제어 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-117">**Sc.exe** is another service control tool for Windows.</span></span> <span data-ttu-id="82c43-118">이 이름은 **net.exe** 서비스 명령에 대한 명명 패턴에는 맞지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-118">That name does not fit into the naming pattern for the **net.exe** service commands.</span></span> <span data-ttu-id="82c43-119">프로세스 관리의 경우, Windows에는 프로세스를 표시하는 **tasklist.exe** 명령과 프로세스를 중단하는 **taskkill.exe** 명령이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-119">For process management, Windows has the **tasklist.exe** command to list processes and the **taskkill.exe** command to kill processes.</span></span>

<span data-ttu-id="82c43-120">또한 이러한 명령에는 불규칙한 매개 변수 사양이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-120">Also, these commands have irregular parameter specifications.</span></span> <span data-ttu-id="82c43-121">`net start` 명령을 사용하여 원격 컴퓨터에서 서비스를 시작할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-121">You can't use the `net start` command to start a service on a remote computer.</span></span> <span data-ttu-id="82c43-122">**sc.exe** 명령을 사용하여 원격 컴퓨터에서 서비스를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-122">The **sc.exe** command can start a service on a remote computer.</span></span> <span data-ttu-id="82c43-123">하지만 원격 컴퓨터를 지정하려면 이름 앞에 이중 백슬래시를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-123">But to specify the remote computer, you must prefix its name with a double backslash.</span></span> <span data-ttu-id="82c43-124">DC01이라는 원격 컴퓨터에서 스풀러 서비스를 시작하려면 `sc.exe \\DC01 start spooler`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-124">To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.</span></span>
<span data-ttu-id="82c43-125">DC01에서 실행되는 작업을 나열하려면 **/S** 매개 변수와 컴퓨터 이름을 백슬래시 없이 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-125">To list tasks running on DC01, you use the **/S** parameter and the computer name without backslashes.</span></span> <span data-ttu-id="82c43-126">정의합니다(예: `tasklist /S DC01`).</span><span class="sxs-lookup"><span data-stu-id="82c43-126">For example, `tasklist /S DC01`.</span></span>

> [!NOTE]
> <span data-ttu-id="82c43-127">PowerShell v6 이전에는 `sc`가 `Set-Content` cmdlet에 대한 별칭이었습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-127">Prior to PowerShell v6, `sc` was an alias for the `Set-Content` cmdlet.</span></span> <span data-ttu-id="82c43-128">따라서 **sc.exe** 명령을 v6 이전의 PowerShell 버전에서 실행하려면 파일 확장명 **exe**를 포함하여 전체 파일 이름 **sc.exe**를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-128">Therefore, to run the **sc.exe** command in a version of PowerShell prior to v6, you must include the full filename **sc.exe** including the file extension **exe**.</span></span>

<span data-ttu-id="82c43-129">서비스 및 프로세스는 수명 주기가 잘 정의된 컴퓨터에서 관리 가능한 요소의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-129">Services and processes are examples of manageable elements on a computer that have well-defined life cycles.</span></span> <span data-ttu-id="82c43-130">서비스 및 프로세스를 시작 또는 중지하거나, 현재 실행 중인 모든 서비스나 프로세스의 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-130">You may start or stop services and processes, or get a list of all currently running services or processes.</span></span> <span data-ttu-id="82c43-131">서비스 및 프로세스 간에는 중요한 기술적 차이가 있지만, 서비스 및 프로세스에서 수행하는 작업은 개념적으로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-131">Although there are important technical distinctions between them, the actions you perform on services and processes are conceptually the same.</span></span> <span data-ttu-id="82c43-132">또한 매개 변수를 지정하여 한 동작을 사용자 정의하기 위해 선택하는 것도 개념적으로 비슷할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-132">Furthermore, the choices we make to customize an action by specifying parameters may be conceptually similar as well.</span></span>

<span data-ttu-id="82c43-133">PowerShell은 이러한 유사성을 이용하여 cmdlet을 이해하고 사용하기 위해 알아야 하는 고유 이름 수를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-133">PowerShell exploits these similarities to reduce the number of distinct names you need to know to understand and use cmdlets.</span></span>

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a><span data-ttu-id="82c43-134">cmdlet에 명령을 쉽게 기억할 수 있도록 verb-noun 이름 사용</span><span class="sxs-lookup"><span data-stu-id="82c43-134">Cmdlets use verb-noun names to reduce command memorization</span></span>

<span data-ttu-id="82c43-135">PowerShell은 "동사-명사(Verb-noun)" 네이밍 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-135">PowerShell uses a "verb-noun" naming system.</span></span> <span data-ttu-id="82c43-136">각 cmdlet 이름은 표준 동사와 특정 명사를 하이픈으로 연결해 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-136">Each cmdlet name consists of a standard verb hyphenated with a specific noun.</span></span> <span data-ttu-id="82c43-137">PowerShell의 verb는 영어 동사가 아닐 수도 있지만 PowerShell에서는 특정 동작을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-137">PowerShell verbs are not always English verbs, but they express specific actions in PowerShell.</span></span> <span data-ttu-id="82c43-138">noun은 모든 언어의 명사와 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-138">Nouns are very much like nouns in any language.</span></span> <span data-ttu-id="82c43-139">시스템 관리에서 중요한 특정 유형의 개체를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-139">They describe specific types of objects that are important in system administration.</span></span> <span data-ttu-id="82c43-140">몇 가지 예를 살펴보면 두 부분으로 이루어진 이러한 이름이 학습에 어떻게 도움이 되는지를 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-140">It's easy to demonstrate how these two-part names reduce learning effort by looking at a few examples.</span></span>

<span data-ttu-id="82c43-141">PowerShell에는 권장되는 표준 verb 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-141">PowerShell has a recommended set of standard verbs.</span></span> <span data-ttu-id="82c43-142">noun은 덜 제한적이지만 verb가 작용하는 대상을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-142">Nouns are less restricted, but always describe what the verb acts upon.</span></span> <span data-ttu-id="82c43-143">PowerShell에는 `Get-Process`, `Stop-Process`, `Get-Service` 및 `Stop-Service`와 같은 명령이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-143">PowerShell has commands such as `Get-Process`, `Stop-Process`, `Get-Service`, and `Stop-Service`.</span></span>

<span data-ttu-id="82c43-144">noun 2개와 verb 2개를 포함하는 이 예제에서 일관성을 유지해도 학습이 크게 간소화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-144">For this example of two nouns and verbs, consistency does not simplify learning that much.</span></span> <span data-ttu-id="82c43-145">이 목록을 10개의 verb와 10개의 noun으로 이루어진 표준화된 집합으로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-145">Extend that list to a standardized set of 10 verbs and 10 nouns.</span></span> <span data-ttu-id="82c43-146">이제 20개의 단어만 이해하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-146">Now you only have 20 words to understand.</span></span>
<span data-ttu-id="82c43-147">하지만 이러한 단어는 100개의 고유한 명령 이름으로 조합될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-147">But those words can be combined to form 100 distinct command names.</span></span>

<span data-ttu-id="82c43-148">이름을 참조하여 PowerShell 명령이 수행하는 작업을 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-148">It's easy to understand what a PowerShell command does by reading its name.</span></span> <span data-ttu-id="82c43-149">컴퓨터를 종료하는 명령은 `Stop-Computer`입니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-149">The command to shut down a computer is `Stop-Computer`.</span></span> <span data-ttu-id="82c43-150">네트워크에 있는 모든 컴퓨터를 나열하는 명령은 `Get-Computer`입니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-150">The command to list all computers on a network is `Get-Computer`.</span></span> <span data-ttu-id="82c43-151">시스템 날짜를 가져오는 명령은 `Get-Date`입니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-151">The command to get the system date is `Get-Date`.</span></span>

<span data-ttu-id="82c43-152">`Get-Command`에 대해 **Verb** 매개 변수를 사용하여 특정 verb를 포함하는 모든 명령을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-152">You can list all commands that include a particular verb with the **Verb** parameter for `Get-Command`.</span></span> <span data-ttu-id="82c43-153">예를 들어 verb `Get`을 사용하는 모든 cmdlet을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-153">For example, to see all cmdlets that use the verb `Get`, type:</span></span>

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

<span data-ttu-id="82c43-154">동일한 유형의 개체에 영향을 주는 명령 패밀리를 표시하려면 **Noun** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-154">Use the **Noun** parameter to see a family of commands that affect the same type of object.</span></span> <span data-ttu-id="82c43-155">예를 들어, 서비스 관리에 사용할 수 있는 명령을 보려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-155">For example, run following command to see the commands  available for managing services:</span></span>

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a><span data-ttu-id="82c43-156">cmdlet에서 표준 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="82c43-156">Cmdlets use standard parameters</span></span>

<span data-ttu-id="82c43-157">앞에서 설명한 것처럼 기존 명령줄 인터페이스에서 사용되는 명령이 항상 일관된 매개 변수 이름을 갖는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-157">As noted earlier, commands used in traditional command-line interfaces don't always have consistent parameter names.</span></span> <span data-ttu-id="82c43-158">매개 변수는 입력하기는 쉽지만 초보 사용자가 이해하기 어려운 단일 문자나 약어로 되어 있는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-158">Parameters are often single-character or abbreviated words that are easy to type but aren't easily understood by new users.</span></span>

<span data-ttu-id="82c43-159">대부분의 다른 기존 명령줄 인터페이스와 달리 PowerShell은 매개 변수를 직접 처리하며, 매개 변수에 대한 이러한 직접 액세스와 함께 개발자 지침을 사용하여 매개 변수 이름을 표준화합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-159">Unlike most other traditional command-line interfaces, PowerShell processes parameters directly, and it uses this direct access to the parameters along with developer guidance to standardize parameter names.</span></span> <span data-ttu-id="82c43-160">이 지침에 따르면 모든 cmdlet이 표준을 준수하도록 권장되지만 항상 표준을 따른다고 보장할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-160">This guidance encourages but does not guarantee that every cmdlet conforms to the standard.</span></span>

<span data-ttu-id="82c43-161">PowerShell은 매개 변수 구분 기호도 표준화합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-161">PowerShell also standardizes the parameter separator.</span></span> <span data-ttu-id="82c43-162">매개 변수를 PowerShell 명령과 함께 사용할 때는 항상 이름 앞에 ‘-’을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-162">Parameter names always have a '-' prepended to them with a PowerShell command.</span></span> <span data-ttu-id="82c43-163">다음과 같은 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82c43-163">Consider the following example:</span></span>

```powershell
Get-Command -Name Clear-Host
```

<span data-ttu-id="82c43-164">매개 변수의 이름은 **Name**이지만 명령줄에서 매개 변수로 사용할 때는 `-Name`으로 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-164">The parameter's name is **Name**, but it is typed as `-Name` when used on the command line as a parameter.</span></span>

<span data-ttu-id="82c43-165">다음은 표준 매개 변수 이름 및 사용법의 몇 가지 일반적인 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-165">Here are some of the general characteristics of the standard parameter names and usages.</span></span>

### <a name="the-help-parameter-"></a><span data-ttu-id="82c43-166">도움말 매개 변수(?)</span><span class="sxs-lookup"><span data-stu-id="82c43-166">The Help parameter (?)</span></span>

<span data-ttu-id="82c43-167">cmdlet에서 `-?` 매개 변수를 지정하면 PowerShell에서 해당 cmdlet에 대한 도움말이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-167">When you specify the `-?` parameter on any cmdlet, PowerShell displays help for the cmdlet.</span></span>
<span data-ttu-id="82c43-168">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-168">The cmdlet is not executed.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="82c43-169">공통 매개 변수</span><span class="sxs-lookup"><span data-stu-id="82c43-169">Common parameters</span></span>

<span data-ttu-id="82c43-170">PowerShell에는 몇 가지 *공통 매개 변수*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-170">PowerShell has several *common parameters*.</span></span> <span data-ttu-id="82c43-171">이러한 매개 변수는 PowerShell 엔진에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-171">These parameters are controlled by the PowerShell engine.</span></span> <span data-ttu-id="82c43-172">공통 매개 변수는 항상 동일한 방법으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-172">Common parameters always behave the same way.</span></span> <span data-ttu-id="82c43-173">일반 매개 변수로는 **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** 및 **OutBuffer**가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-173">The common parameters are **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable**, and **OutBuffer**.</span></span>

### <a name="recommended-parameter-names"></a><span data-ttu-id="82c43-174">권장되는 매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="82c43-174">Recommended parameter names</span></span>

<span data-ttu-id="82c43-175">PowerShell 핵심 cmdlet은 유사한 매개 변수에 표준 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-175">The PowerShell core cmdlets use standard names for similar parameters.</span></span> <span data-ttu-id="82c43-176">반드시 이러한 표준 이름을 사용해야 하는 것은 아니지만 표준 이름 사용을 권장하는 명시적 지침이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-176">The use of these standard names is not enforced, but there is explicit guidance to encourage standardization.</span></span>

<span data-ttu-id="82c43-177">예를 들어 컴퓨터를 나타내는 매개 변수의 권장되는 이름은 Server, Host, System, Node 또는 기타 일반적인 대체 단어가 아니라 **ComputerName**입니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-177">For example, the recommended name for a parameter that refers to a computer is **ComputerName**, rather than Server, Host, System, Node, or some other common alternative.</span></span> <span data-ttu-id="82c43-178">기타 중요한 권장 매개 변수 이름으로는 **Force**, **Exclude**, **Include**, **PassThru**, **Path** 및 **CaseSensitive**가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82c43-178">Other important recommended parameter names are **Force**, **Exclude**, **Include**, **PassThru**, **Path**, and **CaseSensitive**.</span></span>
