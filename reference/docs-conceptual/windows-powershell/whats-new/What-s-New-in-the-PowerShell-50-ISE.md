---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: PowerShell 5.0 ISE의 새로운 기능
description: 이 문서에서는 Windows PowerShell ISE(통합 스크립팅 환경)의 5.0 버전에서 도입된 새로운 기능과 업데이트된 기능에 대해 설명합니다.
ms.openlocfilehash: 75d37d0dafe381c84898ac48343336cd525d2dd1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660819"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="59090-104">Windows PowerShell 5.0 ISE의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="59090-104">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="59090-105">이 문서에서는 Windows PowerShell ISE(통합 스크립팅 환경)의 5.0 버전에서 도입된 새로운 기능과 업데이트된 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-105">This article explains the new and updated features that have been introduced in version 5.0 of the Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

> [!NOTE]
> <span data-ttu-id="59090-106">PowerShell ISE는 더 이상 활성 기능 개발에 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-106">The PowerShell ISE is no longer in active feature development.</span></span> <span data-ttu-id="59090-107">Windows의 배송 구성 요소로서 보안 및 우선 순위가 높은 서비스 수정 사항을 위해 공식적으로 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59090-107">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="59090-108">현재 Windows에서 ISE를 제거할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-108">We currently have no plans to remove the ISE from Windows.</span></span>
>
> <span data-ttu-id="59090-109">PowerShell v6 이상에서는 ISE가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-109">There is no support for the ISE in PowerShell v6 and beyond.</span></span> <span data-ttu-id="59090-110">ISE를 대체하려는 사용자는 [PowerShell 확장](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)을 통해 [Visual Studio Code](https://code.visualstudio.com/)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-110">Users looking for replacement for the ISE should use [Visual Studio Code](https://code.visualstudio.com/) with the [PowerShell Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span></span>

## <a name="feature-description"></a><span data-ttu-id="59090-111">기능 설명</span><span class="sxs-lookup"><span data-stu-id="59090-111">Feature description</span></span>

<span data-ttu-id="59090-112">Windows PowerShell ISE는 그래픽 환경 및 직관적인 환경에서 스크립트 및 모듈을 작성, 실행 및 테스트할 수 있는 호스트 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="59090-112">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="59090-113">구문 색 지정, 탭 완성, 시각적 디버깅, 유니코드 규정 준수 및 상황에 맞는 도움말과 같은 주요 기능을 통해 풍부한 스크립팅 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-113">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="59090-114">자세한 내용은 [Windows PowerShell ISE 소개](../ise/Introducing-the-Windows-PowerShell-ISE.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59090-114">For more information, see [Introducing the Windows PowerShell ISE](../ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="59090-115">다음 표에는 Windows PowerShell에 있는 이 Windows PowerShell ISE 릴리스용의 새로운 기능과 변경된 기능이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-115">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="59090-116">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="59090-116">IntelliSense</span></span>

> <span data-ttu-id="59090-117">ISE 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-117">Added in ISE 3.0</span></span>

<span data-ttu-id="59090-118">IntelliSense는 Windows PowerShell ISE의 일부인 자동 완성 지원 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="59090-118">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="59090-119">IntelliSense는 입력하는 동안 잠재적으로 일치하는 cmdlet, 매개 변수, 매개 변수 값, 파일 또는 폴더가 포함된 클릭 가능한 메뉴를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-119">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="59090-120">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-120">**What value does this change add?**</span></span>

<span data-ttu-id="59090-121">IntelliSense를 추가하면 Windows PowerShell ISE를 사용하여 스크립트를 작성할 때 cmdlet과 구문을 더 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-121">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="59090-122">새 스크립트를 만드는 동안 Windows PowerShell ISE를 사용하여 Windows PowerShell에 대해 알아볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-122">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="59090-123">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-123">**What works differently?**</span></span>

<span data-ttu-id="59090-124">Windows PowerShell ISE에서 cmdlet을 입력하면 스크롤 및 클릭 가능한 메뉴가 표시되므로 적절한 명령을 찾아서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-124">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="59090-125">코드 조각</span><span class="sxs-lookup"><span data-stu-id="59090-125">Snippets</span></span>

> <span data-ttu-id="59090-126">ISE 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-126">Added in ISE 3.0</span></span>

<span data-ttu-id="59090-127">*코드 조각* 은 Windows PowerShell ISE에서 만든 스크립트에 삽입할 수 있는 Windows PowerShell 코드의 짧은 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="59090-127">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="59090-128">Windows PowerShell ISE에는 기본 코드 조각 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-128">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="59090-129">Windows PowerShell ISE에서 작업하는 동안 `New-Snippet` cmdlet을 사용하여 코드 조각을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-129">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="59090-130">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-130">**What value does this change add?**</span></span>

<span data-ttu-id="59090-131">코드 조각을 사용하면 빠르게 스크립트를 조합하고 만들어 사용자 환경을 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-131">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="59090-132">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-132">**What works differently?**</span></span>

<span data-ttu-id="59090-133">Windows PowerShell 3.0 이상에서 코드 조각을 사용하려면 **편집** 메뉴에서 **조각 시작** 을 클릭하거나 <kbd>Ctrl</kbd>+<kbd>J</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="59090-133">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets** , or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="59090-134">추가 기능 도구</span><span class="sxs-lookup"><span data-stu-id="59090-134">Add-on tools</span></span>

> <span data-ttu-id="59090-135">PowerShell 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-135">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59090-136">이제 Windows PowerShell ISE는 개체 모델을 사용하여 추가 기능 도구를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-136">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="59090-137">이러한 추가 기능은 콘솔에서 세로 또는 가로 창으로 표시되는 WPF(Windows Presentation Foundation) 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="59090-137">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="59090-138">하나의 창에 있는 여러 가지 추가 기능 도구는 탭 컨트롤로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59090-138">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="59090-139">타사에서 만든 추가 기능 도구를 추가하거나 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-139">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="59090-140">자세한 내용은 [Windows PowerShell ISE 스크립팅 개체 모델의 용도](../ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59090-140">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="59090-141">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-141">**What value does this change add?**</span></span>

<span data-ttu-id="59090-142">추가 기능을 사용하면 기능 추가 및 스크립팅 환경 향상이 가능한 도구로 Windows PowerShell ISE를 확장하고 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-142">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="59090-143">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-143">**What works differently?**</span></span>

<span data-ttu-id="59090-144">Windows PowerShell ISE 3.0 이상에는 **Commands** 추가 기능이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-144">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="59090-145">**Commands** 추가 기능을 사용하면 cmdlet을 찾고 **스크립트** 창과 **콘솔** 창에서 cmdlet에 대한 도움말을 나란히 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-145">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="59090-146">**추가 기능** 메뉴의 **추가 기능 도구 웹 사이트 열기** 명령을 사용하여 추가 기능을 더 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-146">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="59090-147">관리자 다시 시작 및 자동 저장</span><span class="sxs-lookup"><span data-stu-id="59090-147">Restart manager and auto-save</span></span>

> <span data-ttu-id="59090-148">PowerShell 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-148">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59090-149">이제 Windows PowerShell ISE에서 열려 있는 스크립트를 2분마다 개별 위치에 자동으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-149">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="59090-150">예기치 않은 충돌로 인해 또는 다시 부팅하여 Windows PowerShell ISE가 다시 시작되면 스크립트를 저장하지 않았더라도 마지막 세션에 열려 있던 스크립트가 복구됩니다.</span><span class="sxs-lookup"><span data-stu-id="59090-150">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="59090-151">자동 저장 간격을 변경하려면 콘솔 창에서 다음 명령을 실행합니다. `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="59090-151">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="59090-152">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-152">**What value does this change add?**</span></span>

<span data-ttu-id="59090-153">이제 열려 있는 스크립트가 자동으로 저장된다는 것을 알고 Windows PowerShell ISE 내에서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-153">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="59090-154">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-154">**What works differently?**</span></span>

<span data-ttu-id="59090-155">Windows PowerShell ISE 2.0은 스크립트를 자동으로 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-155">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="59090-156">가장 최근에 사용한 목록</span><span class="sxs-lookup"><span data-stu-id="59090-156">Most-recently used list</span></span>

> <span data-ttu-id="59090-157">PowerShell 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-157">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59090-158">이제 Windows PowerShell ISE에 가장 최근에 사용한 파일 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-158">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="59090-159">Windows PowerShell ISE에서 파일을 열면 **파일** 메뉴의 가장 최근에 사용한 목록에 해당 파일이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="59090-159">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="59090-160">가장 최근에 사용한 목록의 기본 파일 수를 변경하려면 콘솔 창에서 다음 명령을 실행합니다. `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="59090-160">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="59090-161">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-161">**What value does this change add?**</span></span>

<span data-ttu-id="59090-162">이제 가장 최근에 사용한 목록을 통해 최근에 사용한 파일을 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-162">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="59090-163">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-163">**What works differently?**</span></span>

<span data-ttu-id="59090-164">Windows PowerShell ISE 2.0에는 가장 최근에 사용한 목록이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-164">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="59090-165">콘솔 창</span><span class="sxs-lookup"><span data-stu-id="59090-165">Console Pane</span></span>

> <span data-ttu-id="59090-166">PowerShell 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-166">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59090-167">Windows PowerShell ISE의 첫 번째 릴리스에서 제공된 별도의 명령 및 출력 창이 단일 콘솔 창으로 결합되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-167">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="59090-168">콘솔 창의 기능과 모양은 일반적인 Windows PowerShell 콘솔과 유사하지만 다음과 같은 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-168">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="59090-169">XML 구문을 포함하여 입력 텍스트(출력 텍스트가 아님)의 구문 색 지정</span><span class="sxs-lookup"><span data-stu-id="59090-169">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="59090-170">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="59090-170">IntelliSense</span></span>
- <span data-ttu-id="59090-171">중괄호 일치</span><span class="sxs-lookup"><span data-stu-id="59090-171">Brace matching</span></span>
- <span data-ttu-id="59090-172">오류 표시</span><span class="sxs-lookup"><span data-stu-id="59090-172">Error indication</span></span>
- <span data-ttu-id="59090-173">전체 유니코드 지원</span><span class="sxs-lookup"><span data-stu-id="59090-173">Full Unicode support</span></span>
- <span data-ttu-id="59090-174"><kbd>F1</kbd> 상황에 맞는 도움말</span><span class="sxs-lookup"><span data-stu-id="59090-174"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="59090-175"><kbd>Ctrl</kbd>+<kbd>F1</kbd> 상황에 맞는 Show-Command</span><span class="sxs-lookup"><span data-stu-id="59090-175"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="59090-176">복잡한 스크립트 및 오른쪽에서 왼쪽으로 쓰는 언어 지원</span><span class="sxs-lookup"><span data-stu-id="59090-176">Complex script and right-to-left support</span></span>
- <span data-ttu-id="59090-177">글꼴 지원</span><span class="sxs-lookup"><span data-stu-id="59090-177">Font support</span></span>
- <span data-ttu-id="59090-178">Zoom</span><span class="sxs-lookup"><span data-stu-id="59090-178">Zoom</span></span>
- <span data-ttu-id="59090-179">줄 선택 및 블록 선택 모드</span><span class="sxs-lookup"><span data-stu-id="59090-179">Line-select and block-select modes</span></span>
- <span data-ttu-id="59090-180"><kbd>위쪽 화살표</kbd>를 눌러 콘솔에서 기록을 볼 때 명령줄에 입력된 콘텐츠 유지</span><span class="sxs-lookup"><span data-stu-id="59090-180">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="59090-181">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-181">**What value does this change add?**</span></span>

<span data-ttu-id="59090-182">이러한 콘솔 창 변경 내용이 추가되어 콘솔 인터페이스와 보다 일치하는 스크립팅 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-182">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="59090-183">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-183">**What works differently?**</span></span>

<span data-ttu-id="59090-184">Windows PowerShell ISE 2.0에는 별도의 명령 창과 출력 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-184">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="59090-185">명령줄 스위치</span><span class="sxs-lookup"><span data-stu-id="59090-185">Command-line switches</span></span>

> <span data-ttu-id="59090-186">PowerShell 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-186">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59090-187">**powershell_ise.exe** 를 입력하여 명령줄에서 Windows PowerShell ISE를 시작하면 다음과 같은 새 명령줄 스위치를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-187">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe** ), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="59090-188">`-NoProfile`: `$profile`을 실행하지 않고 Windows PowerShell ISE를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-188">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="59090-189">`-Help`: 도움말 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-189">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="59090-190">`-mta`: 다중 스레드 아파트 모드로 Windows PowerShell ISE를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-190">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="59090-191">Windows PowerShell ISE에 대한 기본 작업 모드는 단일 스레드 아파트 모드, 즉 `-sta`입니다.</span><span class="sxs-lookup"><span data-stu-id="59090-191">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="59090-192">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-192">**What value does this change add?**</span></span>

<span data-ttu-id="59090-193">이러한 명령줄 스위치가 추가되어 Windows PowerShell ISE가 실행되는 환경을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-193">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="59090-194">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-194">**What works differently?**</span></span>

<span data-ttu-id="59090-195">Windows PowerShell ISE 2.0에서는 이러한 명령줄 스위치를 인식할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-195">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="59090-196">새 편집기 기능</span><span class="sxs-lookup"><span data-stu-id="59090-196">New editor features</span></span>

> <span data-ttu-id="59090-197">PowerShell 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-197">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59090-198">다른 Windows PowerShell ISE에는 다음과 같은 편집 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="59090-198">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="59090-199">**XML 구문 색 지정** - 이제 Windows PowerShell ISE에서 Windows PowerShell 구문에 색을 지정하는 것과 동일한 방법으로 XML 구문에 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-199">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="59090-200">**중괄호 일치** - Windows PowerShell ISE에는 중괄호 일치 및 강조 표시가 포함되어 있으며, 다음과 같은 방법으로 사용할 수 있습니다. 예를 들어 여는 중괄호가 선택되어 있는 경우 **일치 항목으로 이동** 명령 또는 <kbd>Ctrl</kbd>+<kbd>]</kbd>를 사용하면 닫는 중괄호를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-200">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="59090-201">**개요 보기** 스크립트 창에서 개요 기능을 지원하므로 왼쪽 여백의 더하기 또는 빼기 기호를 클릭하여 코드의 섹션을 축소하거나 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-201">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="59090-202">중괄호 또는 `#region` 및 `#endregion` 태그를 사용하여 축소 가능한 섹션의 시작이나 끝을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-202">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="59090-203">모든 영역을 확장하거나 축소하려면 <kbd>Ctrl</kbd>+<kbd>M</kbd>을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="59090-203">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="59090-204">**텍스트 끌어서 놓기** - 이제 Windows PowerShell ISE에서 텍스트 끌어서 놓기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-204">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="59090-205">텍스트 블록을 선택한 다음 텍스트를 편집기 또는 콘솔의 다른 위치로 끌어서 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-205">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="59090-206"><kbd>Ctrl</kbd> 키를 누른 채 선택한 텍스트를 끄는 경우 마우스 단추를 놓으면 텍스트가 새 위치에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="59090-206">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="59090-207">이 버전의 Windows PowerShell ISE에서 파일을 Windows PowerShell ISE로 끌어다 놓으면 Windows PowerShell ISE에서 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="59090-207">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="59090-208">**구문 분석 오류 표시** - 빨간색 밑줄을 사용하여 구문 분석 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-208">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="59090-209">표시된 오류 위에 마우스를 놓으면 코드에서 검색된 문제가 도구 설명 텍스트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59090-209">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="59090-210">**확대/축소** - 확대/축소 슬라이더(Windows PowerShell ISE 창의 오른쪽 맨 아래에 있음)를 사용하거나 콘솔 창에 `$psise.options.Zoom` 명령을 입력하여 콘솔 콘텐츠의 확대/축소 비율을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-210">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="59090-211">**서식 있는 텍스트 복사 및 붙여넣기** - Windows PowerShell ISE에서 클립보드로 복사하면 원래 선택 항목의 글꼴, 크기 및 색상 정보가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="59090-211">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="59090-212">**블록 선택** - <kbd>ALT</kbd> 키를 누른 채 스크립트 창에서 마우스로 텍스트를 선택하거나 <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>화살표</kbd>를 눌러 텍스트 블록을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-212">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="59090-213">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-213">**What value does this change add?**</span></span>

<span data-ttu-id="59090-214">추가 편집 기능은 보다 일관되고 강력한 편집 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-214">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="59090-215">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-215">**What works differently?**</span></span>

<span data-ttu-id="59090-216">Windows PowerShell ISE 2.0에는 이러한 향상된 편집 기능이 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-216">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="59090-217">새 도움말 뷰어 창</span><span class="sxs-lookup"><span data-stu-id="59090-217">New Help viewer window</span></span>

> <span data-ttu-id="59090-218">PowerShell 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-218">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59090-219">커서가 cmdlet에 있을 때 <kbd>F1</kbd> 키를 누르거나 cmdlet 일부를 강조 표시하면 강조 표시된 cmdlet에 대한 상황에 맞는 도움말이 새 도움말 뷰어에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59090-219">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="59090-220">Windows PowerShell **정보** 도움말을 표시하려면 콘솔 창에 `operators`를 입력한 다음 <kbd>F1</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="59090-220">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="59090-221">이 기능을 사용하려면 먼저 Microsoft 웹 사이트에서 최신 버전의 Windows PowerShell 도움말 항목을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-221">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="59090-222">도움말 항목을 다운로드하는 가장 간단한 방법은 관리자 권한으로 Windows PowerShell ISE를 실행할 때 콘솔 창에서 `Update-Help` cmdlet을 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="59090-222">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="59090-223"><kbd>F1</kbd> 키가 도움말을 찾는 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-223">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="59090-224">**도구**/**옵션** 메뉴의 **일반 설정** 탭에서 **기타 설정** 아래에 있는 **온라인 콘텐츠 대신 로컬 도움말 콘텐츠 사용** 확인란을 설정하거나 선택을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-224">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings** , you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="59090-225">이 확인란을 선택하면 클라이언트는 모듈 폴더에 다운로드된 도움말에서 cmdlet 도움말을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-225">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="59090-226">이 확인란을 선택하지 않으면 클라이언트가 온라인 도움말을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-226">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="59090-227">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-227">**What value does this change add?**</span></span>

<span data-ttu-id="59090-228">현재 cmdlet 또는 스크립트를 종료하지 않고 상황에 맞는 도움말을 사용함으로써 통합된 학습 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59090-228">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="59090-229">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-229">**What works differently?**</span></span>

<span data-ttu-id="59090-230">이전 버전의 Windows PowerShell ISE에서 <kbd>F1</kbd> 키를 누르면 로컬 컴퓨터의 도움말 파일이 열렸습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-230">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="59090-231">Windows PowerShell ISE 3.0 이상에서는 검색 및 구성할 수 있는 cmdlet 도움말이 포함된 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="59090-231">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="59090-232">이 도움말 환경은 Windows PowerShell ISE 3.0의 새로운 기능이며, 업데이트 가능한 도움말은 Windows PowerShell 3.0의 새로운 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="59090-232">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="59090-233">Show-Command cmdlet</span><span class="sxs-lookup"><span data-stu-id="59090-233">Show-Command cmdlet</span></span>

> <span data-ttu-id="59090-234">PowerShell 3.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-234">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59090-235">`Show-Command` cmdlet을 사용하면 그래픽 양식에 입력하여 cmdlet 또는 함수를 작성하거나 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-235">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="59090-236">이 양식을 사용하면 사용자가 그래픽 환경에서 Windows PowerShell을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-236">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="59090-237">또한 `Show-Command`를 사용하면 고급 스크립터가 Windows PowerShell 기반 GUI를 빠르게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-237">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="59090-238">**이와 같은 변경을 통해 더해지는 가치**</span><span class="sxs-lookup"><span data-stu-id="59090-238">**What value does this change add?**</span></span>

<span data-ttu-id="59090-239">Windows PowerShell 스크립트에서 `Show-Command`를 사용하면 익숙한 그래픽 환경을 사용자에게 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-239">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="59090-240">`Show-Command`는 초급 사용자가 Windows PowerShell을 익히는 데 도움이 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59090-240">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="59090-241">**달라진 기능**</span><span class="sxs-lookup"><span data-stu-id="59090-241">**What works differently?**</span></span>

<span data-ttu-id="59090-242">`Show-Command`는 새로운 Windows PowerShell ISE 3.0입니다.</span><span class="sxs-lookup"><span data-stu-id="59090-242">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="59090-243">추가 정보</span><span class="sxs-lookup"><span data-stu-id="59090-243">See also</span></span>

<span data-ttu-id="59090-244">Windows PowerShell ISE 사용에 대한 자세한 내용은 [Windows PowerShell 통합 스크립팅 환경 탐색](../ise/exploring-the-windows-powershell-ise.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59090-244">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../ise/exploring-the-windows-powershell-ise.md).</span></span>
