---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: PowerShell이란?
ms.openlocfilehash: 267b2938a0892c99c3a961bc7107f573df40a683
ms.sourcegitcommit: 38215ad49e237b219e62bb5a5f0eb3b6b048df1e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2020
ms.locfileid: "83868482"
---
# <a name="what-is-powershell"></a><span data-ttu-id="1b3b1-103">PowerShell이란?</span><span class="sxs-lookup"><span data-stu-id="1b3b1-103">What is PowerShell?</span></span>

<span data-ttu-id="1b3b1-104">PowerShell은 명령줄 셸 및 스크립팅 언어로 구성된 플랫폼 간 작업 자동화 및 구성 관리 프레임워크입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-104">PowerShell is a cross-platform task automation and configuration management framework, consisting of a command-line shell and scripting language.</span></span> <span data-ttu-id="1b3b1-105">텍스트를 받아들이고 반환하는 대부분의 셸과는 달리 PowerShell은 .NET CLR(공용 언어 런타임)을 기반으로 하여 .NET 개체를 받아들이고 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-105">Unlike most shells, which accept and return text, PowerShell is built on top of the .NET Common Language Runtime (CLR), and accepts and returns .NET objects.</span></span> <span data-ttu-id="1b3b1-106">이러한 근본적인 변화는 자동화를 위한 완전히 새로운 도구와 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-106">This fundamental change brings entirely new tools and methods for automation.</span></span>

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a><span data-ttu-id="1b3b1-107">개체 기반의 출력</span><span class="sxs-lookup"><span data-stu-id="1b3b1-107">Output is object-based</span></span>

<span data-ttu-id="1b3b1-108">기존 명령줄 인터페이스와 달리 PowerShell cmdlet은 개체를 처리하도록 디자인되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-108">Unlike traditional command-line interfaces, PowerShell cmdlets are designed to deal with objects.</span></span>
<span data-ttu-id="1b3b1-109">개체는 화면에 표시되는 문자열 이상의 의미를 갖는 구조화된 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-109">An object is structured information that is more than just the string of characters appearing on the screen.</span></span> <span data-ttu-id="1b3b1-110">명령 출력에는 필요할 때 사용할 수 있는 추가 정보가 항상 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-110">Command output always carries extra information that you can use if you need it.</span></span>

<span data-ttu-id="1b3b1-111">이전에 텍스트 처리 도구를 사용하여 데이터를 처리한 경우 PowerShell에서는 이러한 도구가 다르게 동작한다는 것을 알게 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-111">If you've used text-processing tools to process data in the past, you'll find that they behave differently when used in PowerShell.</span></span> <span data-ttu-id="1b3b1-112">대부분의 경우 텍스트 처리 도구를 사용하여 특정 정보를 추출할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-112">In most cases, you don't need text-processing tools to extract specific information.</span></span> <span data-ttu-id="1b3b1-113">표준 PowerShell 개체 구문을 사용하여 데이터 부분에 직접 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-113">You directly access portions of the data using standard PowerShell object syntax.</span></span>

## <a name="the-command-family-is-extensible"></a><span data-ttu-id="1b3b1-114">확장 가능한 명령 패밀리</span><span class="sxs-lookup"><span data-stu-id="1b3b1-114">The command family is extensible</span></span>

<span data-ttu-id="1b3b1-115">`cmd.exe`와 같은 인터페이스에서는 기본 제공 명령 세트를 직접 확장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-115">Interfaces such as `cmd.exe` don't provide a way for you to directly extend the built-in command set.</span></span> <span data-ttu-id="1b3b1-116">`cmd.exe`에서 실행되는 외부 명령줄 도구를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-116">You can create external command-line tools that run in `cmd.exe`.</span></span> <span data-ttu-id="1b3b1-117">하지만 이러한 외부 도구에는 도움말 통합과 같은 서비스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-117">But these external tools don't have services, such as Help integration.</span></span> <span data-ttu-id="1b3b1-118">`cmd.exe`는 이러한 외부 도구가 유효한 명령이라는 사실을 자동으로 알지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-118">`cmd.exe` doesn't automatically know that these external tools are valid commands.</span></span>

<span data-ttu-id="1b3b1-119">PowerShell의 명령을 _cmdlets_라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-119">The commands in PowerShell are known as _cmdlets_.</span></span> <span data-ttu-id="1b3b1-120">각 cmdlet을 개별적으로 사용할 수 있지만, 조합하여 복잡한 작업을 수행할 때 그 능력이 실현됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-120">You can use each cmdlet separately, but their power is realized when you combine them to perform complex tasks.</span></span> <span data-ttu-id="1b3b1-121">많은 셸과 마찬가지로, PowerShell을 통해 컴퓨터의 파일 시스템에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-121">Like many shells, PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="1b3b1-122">PowerShell ‘공급자’를 통해 레지스트리 및 인증서 스토리지와 같은 다른 데이터 스토리지를 파일 시스템처럼 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-122">PowerShell _providers_ enable you to access other data stores, such as the registry and the certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="1b3b1-123">컴파일된 코드 또는 스크립트를 사용하여 사용자 고유의 cmdlet 및 함수 모듈을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-123">You can create your own cmdlet and function modules using compiled code or scripts.</span></span> <span data-ttu-id="1b3b1-124">모듈은 셸에 cmdlet 및 공급자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-124">Modules can add cmdlets and providers to the shell.</span></span> <span data-ttu-id="1b3b1-125">또한 PowerShell은 UNIX 셸 스크립트 및 `cmd.exe` 배치 파일과 유사한 스크립트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-125">PowerShell also supports scripts that are analogous to UNIX shell scripts and `cmd.exe` batch files.</span></span>

## <a name="support-for-command-aliases"></a><span data-ttu-id="1b3b1-126">명령 별칭 지원</span><span class="sxs-lookup"><span data-stu-id="1b3b1-126">Support for command aliases</span></span>

<span data-ttu-id="1b3b1-127">PowerShell은 대체 이름으로 명령을 참조하도록 별칭을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-127">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="1b3b1-128">별칭은 다른 셸을 사용해 본 경험이 있는 사용자가 이미 알고 있는 일반적인 명령 이름을 PowerShell의 유사한 작업에 사용할 수 있도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-128">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="1b3b1-129">별칭은 새 이름을 다른 명령과 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-129">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="1b3b1-130">예를 들어 PowerShell에는 출력 창을 지우는 `Clear-Host`라는 내부 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-130">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="1b3b1-131">명령 프롬프트에서 `cls` 또는 `clear` 별칭을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-131">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="1b3b1-132">PowerShell은 이러한 별칭을 해석하고 `Clear-Host` 함수를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-132">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="1b3b1-133">이 기능은 사용자가 PowerShell을 익히는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-133">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="1b3b1-134">첫째, 대부분의 `cmd.exe` 및 Unix 사용자는 이름으로 이미 알고 있는 대규모 명령 모음을 보유하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-134">First, most `cmd.exe` and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="1b3b1-135">PowerShell의 해당 명령이 동일한 결과를 생성하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-135">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="1b3b1-136">그러나 결과는 사용자가 PowerShell 명령 이름을 모르는 상태로 사용해도 될만큼 충분히 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-136">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="1b3b1-137">“머슬 메모리”는 새 명령 셸을 학습할 때 겪게 되는 또 다른 어려움입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-137">"Muscle memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="1b3b1-138">수년 동안 `cmd.exe`를 사용해왔다면 화면을 지우기 위해 반사적으로 `cls` 명령을 입력할 수 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-138">If you have used `cmd.exe` for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="1b3b1-139">`Clear-Host`에 대한 별칭이 없으면, 오류 메시지가 수신되고 출력을 지우기 위해 어떻게 해야 할지 알 수 없을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-139">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

## <a name="powershell-handles-console-input-and-display"></a><span data-ttu-id="1b3b1-140">Powershell로 콘솔 입력 및 표시 처리</span><span class="sxs-lookup"><span data-stu-id="1b3b1-140">PowerShell handles console input and display</span></span>

<span data-ttu-id="1b3b1-141">사용자가 명령을 입력하면 PowerShell은 항상 이 명령줄 입력을 직접 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-141">When you type a command, PowerShell always processes the command-line input directly.</span></span> <span data-ttu-id="1b3b1-142">또한 PowerShell은 화면에 표시되는 출력의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-142">PowerShell also formats the output that you see on the screen.</span></span> <span data-ttu-id="1b3b1-143">이러한 차이점은 각 cmdlet에 대해 필요한 작업을 줄여주므로 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-143">This difference is significant because it reduces the work required of each cmdlet.</span></span> <span data-ttu-id="1b3b1-144">또한 사용자가 항상 어떤 cmdlet으로도 동일한 방식으로 작업할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-144">It ensures that you can always do things the same way with any cmdlet.</span></span> <span data-ttu-id="1b3b1-145">따라서 cmdlet 개발자는 명령줄 인수를 구문 분석하거나 출력 형식을 지정하기 위해 코드를 작성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-145">Cmdlet developers don't need to write code to parse the command-line arguments or format the output.</span></span>

<span data-ttu-id="1b3b1-146">이전의 명령줄 도구는 도움말을 요청하고 표시하는 자체 구성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-146">Traditional command-line tools have their own schemes for requesting and displaying Help.</span></span> <span data-ttu-id="1b3b1-147">일부 명령줄 도구는 `/?`을 사용하여 도움말 표시를 트리거합니다. 다른 경우에는 `-?`, `/H` 또는 심지어 `//`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-147">Some command-line tools use `/?` to trigger the Help display; others use `-?`, `/H`, or even `//`.</span></span> <span data-ttu-id="1b3b1-148">또한 일부 명령줄 도구는 콘솔 화면 대신 GUI 창에 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-148">Some will display Help in a GUI window, rather than in the console display.</span></span> <span data-ttu-id="1b3b1-149">사용자가 잘못된 매개 변수를 사용할 경우 이러한 도구는 사용자의 입력 내용을 무시하고 자동으로 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-149">If you use the wrong parameter, the tool might ignore what you typed and begin executing a task automatically.</span></span>
<span data-ttu-id="1b3b1-150">PowerShell은 명령줄을 자동으로 구문 분석하고 처리하므로 `-?` 매개 변수는 항상 “이 명령에 대한 도움말 표시”를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-150">Since PowerShell automatically parses and processes the command line, the `-?` parameter always means "show me Help for this command".</span></span>

> [!NOTE]
> <span data-ttu-id="1b3b1-151">PowerShell에서 그래픽 애플리케이션을 실행하면 해당 애플리케이션의 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-151">If you run a graphic application in PowerShell, the window for the application opens.</span></span>
> <span data-ttu-id="1b3b1-152">PowerShell은 사용자가 제공하는 명령줄 입력이나 콘솔 창에 반환되는 애플리케이션 출력을 처리할 때만 개입합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-152">PowerShell intervenes only when processing the command-line input you supply or the application output returned to the console window.</span></span> <span data-ttu-id="1b3b1-153">애플리케이션이 내부적으로 작업을 수행하는 방식에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-153">It does not affect how the application works internally.</span></span>

## <a name="powershell-has-a-pipeline"></a><span data-ttu-id="1b3b1-154">PowerShell에는 파이프라인이 있음</span><span class="sxs-lookup"><span data-stu-id="1b3b1-154">PowerShell has a pipeline</span></span>

<span data-ttu-id="1b3b1-155">파이프라인은 명령줄 인터페이스에 사용되는 가장 중요한 개념이라고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-155">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="1b3b1-156">적절히 사용하는 경우 파이프라인은 복잡한 명령을 사용할 필요를 줄여주고, 작업 흐름을 보다 쉽게 확인할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-156">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work.</span></span> <span data-ttu-id="1b3b1-157">파이프라인의 각 명령은 출력을 항목별로 다음 명령에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-157">Each command in a pipeline passes its output, item by item, to the next command.</span></span> <span data-ttu-id="1b3b1-158">따라서 명령이 한 번에 둘 이상의 항목을 처리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-158">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="1b3b1-159">그 결과 리소스 사용량이 줄어들고 출력이 바로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-159">The result is reduced resource consumption and the ability to get output immediately.</span></span>

<span data-ttu-id="1b3b1-160">파이프라인에 사용되는 표기법은 다른 셸에 사용되는 표기법과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-160">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="1b3b1-161">얼핏 보면 파이프라인이 PowerShell과 어떻게 다른지 명확하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-161">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="1b3b1-162">화면에 텍스트가 표시되어 있는 경우에도 PowerShell은 명령 사이에 있는 텍스트가 아닌 개체를 파이프합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-162">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

<span data-ttu-id="1b3b1-163">예를 들어 `Out-Host` cmdlet을 사용하여 다른 명령의 출력을 페이지 단위로 표시하면 다음과 같이 일반 텍스트가 페이지 단위로 나뉘어져 화면에 표시된 것처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-163">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="1b3b1-164">페이징을 사용하면 전체 페이지를 표시할 준비가 되면 처리가 `Out-Host` cmdlet으로 전송되므로 역시 CPU 사용률을 줄이는 데 효과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-164">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="1b3b1-165">파이프라인의 앞에 나오는 cmdlet은 출력의 다음 페이지를 사용할 수 있게 될 때까지 실행을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-165">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

### <a name="objects-in-the-pipeline"></a><span data-ttu-id="1b3b1-166">파이프라인의 개체</span><span class="sxs-lookup"><span data-stu-id="1b3b1-166">Objects in the pipeline</span></span>

<span data-ttu-id="1b3b1-167">PowerShell에서 cmdlet을 실행하면 개체를 콘솔 창에 텍스트로 표시해야 하므로 텍스트 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-167">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="1b3b1-168">텍스트 출력에 출력되는 개체의 모든 속성이 표시되지는 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-168">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="1b3b1-169">예를 들어 `Get-Location` cmdlet을 고려해보세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-169">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="1b3b1-170">텍스트 출력은 `Get-Location`에서 반환된 개체의 완전한 표현이 아니라 정보의 요약입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-170">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="1b3b1-171">화면에 표시되는 데이터에 서식을 지정하는 프로세스에 따라 출력의 제목이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-171">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

```powershell
Get-Location
```

```Output
Path
----
C:\
```

<span data-ttu-id="1b3b1-172">출력을 `Get-Member` cmdlet으로 파이프하면 `Get-Location`에서 반환된 개체에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-172">Piping the output to the `Get-Member` cmdlet displays information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="1b3b1-173">`Get-Location`는 현재 경로 및 기타 정보를 포함하는 **PathInfo** 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-173">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>

## <a name="built-in-help-system"></a><span data-ttu-id="1b3b1-174">기본 제공 도움말 시스템</span><span class="sxs-lookup"><span data-stu-id="1b3b1-174">Built-in help system</span></span>

<span data-ttu-id="1b3b1-175">Unix `man` 페이지와 비슷하게 PowerShell에는 PowerShell 개념과 명령 구문을 설명하는 자세한 도움말 문서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-175">Similar to Unix `man` pages, PowerShell includes detailed help articles that explain PowerShell concepts and command syntax.</span></span> <span data-ttu-id="1b3b1-176">[Get-Help][] cmdlet을 사용하여 명령 프롬프트에서 이러한 도움말 문서를 표시하거나 PowerShell 온라인 설명서에서 이러한 문서의 가장 최근 업데이트 버전을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-176">Use the [Get-Help][] cmdlet to display these articles at the command prompt or view the most recently updated versions of these articles in the PowerShell documentation online.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1b3b1-177">다음 단계</span><span class="sxs-lookup"><span data-stu-id="1b3b1-177">Next steps</span></span>

<span data-ttu-id="1b3b1-178">PowerShell에 대한 자세한 내용은 이 사이트의 **PowerShell 학습** 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b1-178">To learn more about PowerShell, see the **Learning PowerShell** section of this site.</span></span>

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
