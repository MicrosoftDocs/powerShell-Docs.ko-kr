---
description: Windows PowerShell ISE (통합 스크립팅 환경)의 기능 및 시스템 요구 사항에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_ISE
ms.openlocfilehash: ff543024d7c62c70217eeaf3ded192a5a24c4757
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388844"
---
# <a name="about-windows-powershell-ise"></a><span data-ttu-id="bc51c-104">Windows PowerShell ISE 정보</span><span class="sxs-lookup"><span data-stu-id="bc51c-104">About Windows PowerShell ISE</span></span>

## <a name="short-description"></a><span data-ttu-id="bc51c-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="bc51c-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="bc51c-106">Windows PowerShell ISE (통합 스크립팅 환경)의 기능 및 시스템 요구 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-106">Describes the features and system requirements of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="long-description"></a><span data-ttu-id="bc51c-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="bc51c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="bc51c-108">Windows PowerShell ISE은 Windows PowerShell 용 그래픽 호스트 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-108">Windows PowerShell ISE is a graphical host application for Windows PowerShell.</span></span>
<span data-ttu-id="bc51c-109">Windows PowerShell ISE에서는 명령을 실행 하 고 단일 Windows 기반 그래픽 사용자 인터페이스에서 스크립트를 작성, 테스트 및 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-109">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphical user interface.</span></span> <span data-ttu-id="bc51c-110">이러한 기능에는 Intellisense, 여러 줄 편집, 탭 완성, 자동 저장, 구문 색 지정, 선택적 실행, 상황에 맞는 도움말, 표시 명령 (창에 작성 명령) 및 더블 바이트 문자 집합 및 오른쪽에서 왼쪽으로 쓰기 언어에 대 한 지원이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-110">Its features include Intellisense, multiline editing, tab completion, auto-save, syntax coloring, selective execution, context-sensitive help, Show Command (compose commands in a window) and support for double-byte character sets and right-to-left languages.</span></span>

<span data-ttu-id="bc51c-111">Windows PowerShell ISE은 초보자를 위한 훌륭한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-111">Windows PowerShell ISE is an excellent tool for beginners.</span></span> <span data-ttu-id="bc51c-112">명령 창 및 새 원격 PowerShell 표시 탭에서는 첫 번째 시도에서 성공할 수 있도록 작업을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-112">The Show Command window and New Remote PowerShell Tab guide you through tasks so that you can be successful on the first try.</span></span> <span data-ttu-id="bc51c-113">코드 조각 및 오류 표시기를 사용 하면 Windows PowerShell 언어를 학습 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-113">Snippets and error indicators help you learn the Windows PowerShell language as you work.</span></span>

<span data-ttu-id="bc51c-114">고급 사용자는 정교한 디버깅 기능, 추가 기능 및 Windows PowerShell ISE 개체 모델을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-114">Advanced users can take advantage of the sophisticated debugging features, add-ons, and the Windows PowerShell ISE object model.</span></span>

<span data-ttu-id="bc51c-115">Windows PowerShell 4.0에 Windows PowerShell ISE의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="bc51c-115">What's New in Windows PowerShell ISE in Windows PowerShell 4.0</span></span>

<span data-ttu-id="bc51c-116">Windows PowerShell ISE에는 Windows PowerShell 4.0의 두 가지 새로운 기능이 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-116">Windows PowerShell ISE introduces two new features in Windows PowerShell 4.0.</span></span>

- <span data-ttu-id="bc51c-117">Windows PowerShell ISE는 이제 Windows PowerShell 워크플로 디버깅과 원격 스크립트 디버깅을 모두 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-117">Windows PowerShell ISE now supports both Windows PowerShell Workflow debugging and remote script debugging.</span></span> <span data-ttu-id="bc51c-118">자세한 내용은 about_Debuggers를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bc51c-118">For more Information, see about_Debuggers.</span></span>

- <span data-ttu-id="bc51c-119">Windows PowerShell 필요한 상태 구성 공급자 및 구성에 대한 IntelliSense 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-119">IntelliSense support has been added for Windows PowerShell Desired State Configuration providers and configurations.</span></span>

## <a name="starting-windows-powershell-ise"></a><span data-ttu-id="bc51c-120">시작 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="bc51c-120">Starting Windows PowerShell ISE</span></span>

<span data-ttu-id="bc51c-121">Windows PowerShell ISE은 지원 되는 모든 Windows 버전에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-121">Windows PowerShell ISE is installed, enabled, and ready to use in all supported versions of Windows.</span></span>

- <span data-ttu-id="bc51c-122">Windows 8.1, Windows 8, Windows Server 2012 R2 및 Windows Server 2012의 시작 화면에서 PowerShell_ISE를 입력 한 다음 PowerShell_ISE 또는 Windows PowerShell ISE를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-122">In Windows 8.1, Windows 8, Windows Server 2012 R2, and Windows Server 2012, on the Start screen, type PowerShell_ISE, and then click PowerShell_ISE or Windows PowerShell ISE.</span></span>

- <span data-ttu-id="bc51c-123">Windows Server 2012 R2 및 Windows Server 2012의 서버 관리자에 있는 도구 메뉴에서 Windows PowerShell ISE를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-123">In Windows Server 2012 R2 and Windows Server 2012, in Server Manager, on the Tools menu, click Windows PowerShell ISE.</span></span>

- <span data-ttu-id="bc51c-124">이전 버전의 Windows에서는 시작, 모든 프로그램, 보조 프로그램, Windows PowerShell을 차례로 클릭 한 다음 Windows PowerShell ISE를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-124">In earlier versions of Windows, click Start, All Programs, Accessories, Windows PowerShell, and then click Windows PowerShell ISE.</span></span>

- <span data-ttu-id="bc51c-125">Windows에서 Windows PowerShell 콘솔, Cmd.exe 또는 실행 또는 검색 상자에 "PowerShell_ise.exe"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-125">In a Windows PowerShell console, Cmd.exe, or the Run or Search box in Windows, type "PowerShell_ise.exe".</span></span> <span data-ttu-id="bc51c-126">NoProfile 스위치를 포함 하 여 명령줄 매개 변수를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-126">You can also use the command-line parameters, including the NoProfile switch.</span></span> <span data-ttu-id="bc51c-127">자세한 내용은 [PowerShell_ISE.exe 콘솔 도움말](about_powershell_ise_exe.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bc51c-127">For more information, see [PowerShell_ISE.exe Console Help](about_powershell_ise_exe.md).</span></span>

## <a name="running-interactive-commands"></a><span data-ttu-id="bc51c-128">대화형 명령 실행</span><span class="sxs-lookup"><span data-stu-id="bc51c-128">Running Interactive Commands</span></span>

<span data-ttu-id="bc51c-129">Windows PowerShell ISE에서 모든 Windows PowerShell 식 또는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-129">You can run any Windows PowerShell expression or command in Windows PowerShell ISE.</span></span> <span data-ttu-id="bc51c-130">Windows PowerShell 콘솔에서 사용할 때와 마찬가지로 cmdlet, 공급자, 스냅인 및 모듈을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-130">You can use cmdlets, providers, snap-ins, and modules as you would use them in the Windows PowerShell console.</span></span>

<span data-ttu-id="bc51c-131">콘솔 창에서 대화형 명령을 입력 하거나 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-131">You can type or paste interactive commands in the Console pane.</span></span> <span data-ttu-id="bc51c-132">명령을 실행 하려면 단추, 메뉴 항목 및 바로 가기 키를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-132">To run the commands, you can use buttons, menu items, and keyboard shortcuts.</span></span>

<span data-ttu-id="bc51c-133">여러 줄 편집 기능을 사용 하 여 한 번에 여러 줄의 코드를 콘솔 창에 입력 하거나 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-133">You can use the multiline editing feature to type or paste several lines of code into the Console pane at once.</span></span> <span data-ttu-id="bc51c-134">위쪽 화살표 키를 눌러 이전 명령을 회수할 때 명령의 모든 줄이 회수 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-134">When you press the UP ARROW key to recall the previous command, all the lines in the command are recalled.</span></span> <span data-ttu-id="bc51c-135">명령을 입력 하는 경우 SHIFT + ENTER를 눌러 현재 줄 아래에 새 빈 줄이 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-135">When you type commands, press SHIFT+ENTER to make a new blank line appear under the current line.</span></span>

## <a name="viewing-output"></a><span data-ttu-id="bc51c-136">출력 보기</span><span class="sxs-lookup"><span data-stu-id="bc51c-136">Viewing Output</span></span>

<span data-ttu-id="bc51c-137">명령 및 스크립트의 결과는 콘솔 창에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-137">The results of commands and scripts are displayed in the Console pane.</span></span> <span data-ttu-id="bc51c-138">콘솔 창에서 바로 가기 키 또는 도구 모음의 복사 단추를 사용 하 여 결과를 이동 하거나 복사할 수 있으며 스크립트 창이 나 콘솔 창이 나 다른 프로그램에 결과를 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-138">You can move or copy the results from the Console pane by using keyboard shortcuts or the Copy button on the toolbar, and you can paste the results in the Script pane or Console panes or other programs.</span></span> <span data-ttu-id="bc51c-139">콘솔 창을 지우려면 "출력 창 지우기" 단추를 클릭 하거나 다음 명령 중 하나를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-139">To clear the Console pane, click the "Clear Output Pane" button or type one of the following commands:</span></span>

```
Clear-Host
cls
```

## <a name="writing-scripts-and-functions"></a><span data-ttu-id="bc51c-140">스크립트 및 함수 작성</span><span class="sxs-lookup"><span data-stu-id="bc51c-140">Writing Scripts and Functions</span></span>

<span data-ttu-id="bc51c-141">스크립트 창에서 스크립트를 열고, 작성 하 고, 편집 하 고, 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-141">In the Script pane, you can open, compose, edit, and run scripts.</span></span> <span data-ttu-id="bc51c-142">스크립트 창에서 단추 및 바로 가기 키를 사용 하 여 스크립트를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-142">The Script pane lets you edit scripts by using buttons and keyboard shortcuts.</span></span> <span data-ttu-id="bc51c-143">스크립트 창과 콘솔 창 사이에서 텍스트를 복사 하 고 잘라내어 붙여 넣을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-143">You can also copy, cut, and paste text between the Script pane and the Console pane.</span></span>

<span data-ttu-id="bc51c-144">선택적 실행 기능을 사용 하 여 스크립트 전체 또는 일부를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-144">You can use the selective run feature to run all or part of a script.</span></span> <span data-ttu-id="bc51c-145">스크립트의 일부를 실행 하려면 실행할 텍스트를 선택한 다음 실행 선택 단추를 클릭 하거나 F8 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-145">To run part of a script, select the text you want to run, and then click the Run Selection button or press F8.</span></span> <span data-ttu-id="bc51c-146">기본적으로 F8는 현재 줄을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-146">By default, F8 runs the current line.</span></span>

<span data-ttu-id="bc51c-147">고급 편집 기능에는 중괄호 일치, 확장-축소, 줄 번호, 오류 표시기, 블록 편집 및 들여쓰기, 다양 한 복사 및 대/소문자 변환이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-147">Advanced editing features include brace-matching, expand-collapse, line numbers, error indicators, block editing and indenting, rich copy, and case conversion.</span></span>

## <a name="getting-help"></a><span data-ttu-id="bc51c-148">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="bc51c-148">Getting Help</span></span>

<span data-ttu-id="bc51c-149">Windows PowerShell ISE에는 사용을 설명 하는 도움말 항목이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-149">Windows PowerShell ISE includes help topics that describe its use.</span></span> <span data-ttu-id="bc51c-150">또한 모든 설치 된 도움말 파일은 스크립트와 명령 창에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-150">In addition, all installed help files are accessible from the Script and Command panes.</span></span>

<span data-ttu-id="bc51c-151">Windows PowerShell ISE는 상황에 맞는 도움말도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-151">Windows PowerShell ISE also supports context-sensitive help.</span></span> <span data-ttu-id="bc51c-152">특정 cmdlet, 공급자 또는 키워드에 대 한 도움말을 보려면 항목 이름에 커서를 놓고 F1 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-152">To get help about a particular cmdlet, provider, or keyword, place the cursor in the name of the item and press F1.</span></span> <span data-ttu-id="bc51c-153">도움말 항목을 검색 하려면 F1 키를 누르고 검색어를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-153">To search the help topics, press F1 and type the search term.</span></span>

<span data-ttu-id="bc51c-154">컴퓨터에서 도움말 항목을 업데이트 하려면 도움말 메뉴에서 Windows PowerShell 업데이트 도움말 항목을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-154">To update the help topics on the computer, use the Update Windows PowerShell Help item in the Help menu.</span></span> <span data-ttu-id="bc51c-155">이 항목은 현재 UI 문화권의 현재 세션에 있는 모듈에 대 한 도움말을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-155">This item updates help for the modules in the current session in the current UI culture.</span></span> <span data-ttu-id="bc51c-156">매개 변수 없이 Update-Help cmdlet을 실행 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-156">It is equivalent to running the Update-Help cmdlet without parameters.</span></span> <span data-ttu-id="bc51c-157">Windows PowerShell과 함께 제공 되는 cmdlet에 대 한 도움말을 업데이트 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell ISE를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-157">To update help for the cmdlets that come with Windows PowerShell, start Windows PowerShell ISE with the "Run as administrator" option.</span></span>

<span data-ttu-id="bc51c-158">Windows PowerShell 콘솔에서 사용 하는 것 처럼 Get-help, Save Help 및 Update-Help cmdlet을 Windows PowerShell ISE에서 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-158">You can also use the Get-Help, Save-Help, and Update-Help cmdlets in Windows PowerShell ISE, just as you use it in the Windows PowerShell console.</span></span> <span data-ttu-id="bc51c-159">그러나 Windows PowerShell ISE 도움말 함수는 전체 도움말 항목을 표시 하 고 한 번에 한 페이지씩 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-159">However, in Windows PowerShell ISE, the Help function displays the entire help topic, not one page at a time.</span></span>

## <a name="debugging-scripts"></a><span data-ttu-id="bc51c-160">스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="bc51c-160">Debugging Scripts</span></span>

<span data-ttu-id="bc51c-161">Windows PowerShell ISE 디버거를 사용 하 여 Windows PowerShell 스크립트 또는 함수를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-161">You can use the Windows PowerShell ISE debugger to debug a Windows PowerShell script or function.</span></span> <span data-ttu-id="bc51c-162">스크립트를 디버그할 때 메뉴 항목 및 바로 가기 키를 사용 하 여 Windows PowerShell 콘솔에서 수행 하는 것과 동일한 많은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-162">When you debug a script, you can use menu items and shortcut keys to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span> <span data-ttu-id="bc51c-163">예를 들어 스크립트에서 줄 중단점을 설정 하려면 코드 줄을 마우스 오른쪽 단추로 클릭 한 다음 중단점 설정/해제를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-163">For example, to set a line breakpoint in a script, right-click the line of code, and then click Toggle Breakpoint.</span></span>

<span data-ttu-id="bc51c-164">디버깅 하는 동안 스크립트를 단계별로 실행 하는 동안 디버깅 형광펜은 실행 중인 명령의 일부를 정확 하 게 표시 하 고, 호출 된 함수 및 스크립트를 포함 하는 파일을 자동으로 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-164">As you step through a script while debugging, the debugging highlighter shows precisely which part of the command is running and automatically opens files that include called functions and scripts.</span></span>

<span data-ttu-id="bc51c-165">기본적으로 중단점 설정/해제 메뉴 항목은 스크립트의 전체 줄에 중단점을 설정 하지만 변수나 명령 이름에 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-165">By default, the Toggle Breakpoint menu item sets a breakpoint on an entire line in a script, but you can set a breakpoint on a variable or command name.</span></span>
<span data-ttu-id="bc51c-166">줄 및 열 번호를 기준으로 명령에 중단점을 설정 하 여 긴 파이프라인 명령을 더 쉽게 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-166">You can also set a breakpoint on a command by line and column number, making it easier to debug long pipeline commands.</span></span>

<span data-ttu-id="bc51c-167">Windows PowerShell ISE에서 스크립트 파일을 열어 스크립트에서 구문 오류를 디버그할 수 있는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-167">Often, you can debug syntax errors in a script just by opening the script file in Windows PowerShell ISE.</span></span> <span data-ttu-id="bc51c-168">오류 표시기는 구문 오류를 식별 하 고 개요 기능을 사용 하면 스크립트의 일부를 축소 하 여 문제에 초점을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-168">The error indicators identify syntax errors and the outlining features let you collapse parts of the script to focus on trouble spots.</span></span>

<span data-ttu-id="bc51c-169">콘솔에서 사용 하는 것 처럼 명령 창에서 Windows PowerShell 디버거 cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-169">You can also use the Windows PowerShell debugger cmdlets in the Command pane just as you would use them in the console.</span></span>

## <a name="running-remote-commands"></a><span data-ttu-id="bc51c-170">원격 명령 실행</span><span class="sxs-lookup"><span data-stu-id="bc51c-170">Running Remote Commands</span></span>

<span data-ttu-id="bc51c-171">새 원격 PowerShell 탭 기능을 사용 하면 로컬 컴퓨터 또는 원격 컴퓨터에 대 한 영구 사용자 관리 Windows PowerShell 세션 ("PSSession")을 쉽게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-171">The New Remote PowerShell Tab feature makes it easy to establish a persistent user-managed Windows PowerShell session ("PSSession") to the local computer or a remote computer.</span></span> <span data-ttu-id="bc51c-172">명령을 실행 하면 원격 컴퓨터에서 명령을 실행할 수 있는 권한이 있는 사용자 계정 및 컴퓨터 이름을 입력 하 라는 팝업 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-172">The command opens a pop-up window that prompts you for a computer name and for the user account that has permission to run commands on the remote computer.</span></span>

## <a name="customizing-the-view"></a><span data-ttu-id="bc51c-173">뷰 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="bc51c-173">Customizing the View</span></span>

<span data-ttu-id="bc51c-174">Windows PowerShell ISE 기능을 사용 하 여 콘솔 창과 스크립트 창을 이동 하 고 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-174">You can use Windows PowerShell ISE features to move and to resize the Console pane and the Script pane.</span></span> <span data-ttu-id="bc51c-175">창을 표시 하거나 숨길 수 있으며 모든 창의 텍스트 크기를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-175">You can show and hide either pane, and you can change the text size in all the panes.</span></span>

<span data-ttu-id="bc51c-176">옵션 창을 사용 하 여 Windows PowerShell ISE의 모양과 연산을 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-176">You can also use the Options window to customize the appearance and operation of Windows PowerShell ISE.</span></span> <span data-ttu-id="bc51c-177">또한 Windows PowerShell ISE에는 메뉴 및 메뉴 항목 추가를 비롯 하 여 Windows PowerShell ISE을 사용자 지정 하는 데 사용할 수 있는 사용자 지정 호스트 변수 $psISE 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-177">In addition, Windows PowerShell ISE has a custom host variable, $psISE, that you can use to customize Windows PowerShell ISE, including adding menus and menu items.</span></span>

## <a name="windows-powershell-ise-profile"></a><span data-ttu-id="bc51c-178">Windows PowerShell ISE 프로필</span><span class="sxs-lookup"><span data-stu-id="bc51c-178">Windows PowerShell ISE Profile</span></span>

<span data-ttu-id="bc51c-179">Windows PowerShell ISE에는 Microsoft.PowerShellISE_profile.ps1 자체 Windows PowerShell 프로필이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-179">Windows PowerShell ISE has its own Windows PowerShell profile, Microsoft.PowerShellISE_profile.ps1.</span></span> <span data-ttu-id="bc51c-180">이 프로필에는 Windows PowerShell ISE에서 사용 하는 함수, 별칭, 변수 및 명령을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-180">In this profile, you can store functions, aliases, variables, and commands that you use in Windows PowerShell ISE.</span></span>

<span data-ttu-id="bc51c-181">Windows PowerShell AllHosts 프로필 (CurrentUser \\ allhosts 및 AllUsers \\ allhosts)의 항목은 windows powershell 호스트 프로그램에 있는 것 처럼 Windows PowerShell ISE 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-181">Items in the Windows PowerShell AllHosts profiles (CurrentUser\\AllHosts and AllUsers\\AllHosts) are also available in Windows PowerShell ISE, just as they are in any Windows PowerShell host program.</span></span> <span data-ttu-id="bc51c-182">그러나 Windows PowerShell 콘솔 프로필의 항목은 Windows PowerShell ISE에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-182">However, the items in your Windows PowerShell console profiles are not available in Windows PowerShell ISE.</span></span>

<span data-ttu-id="bc51c-183">프로필 이동 및 다시 구성에 대 한 지침은 Windows PowerShell ISE 도움말 및 about_Profiles에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-183">Instructions for moving and reconfiguring your profiles are available in Windows PowerShell ISE Help and in about_Profiles.</span></span>

## <a name="notes"></a><span data-ttu-id="bc51c-184">참고</span><span class="sxs-lookup"><span data-stu-id="bc51c-184">NOTES</span></span>

<span data-ttu-id="bc51c-185">Windows PowerShell ISE은 Windows의 클라이언트 및 서버 버전에서 기본적으로 설정 되는 선택적 Windows 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-185">Windows PowerShell ISE is an optional Windows Feature that is turned on by default on client and server versions of Windows.</span></span> <span data-ttu-id="bc51c-186">클라이언트 버전의 Windows에서 Windows PowerShell ISE를 사용 하거나 사용 하지 않도록 설정 하려면 제어판에서 Windows 기능 사용/사용 안 함을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-186">To enable and disable Windows PowerShell ISE in client versions of Windows, use Turn Windows Features On or Off in Control Panel.</span></span> <span data-ttu-id="bc51c-187">서버 버전의 Windows에서 Windows PowerShell ISE를 사용 하거나 사용 하지 않도록 설정 하려면 서버 관리자에서 역할 및 기능 추가 마법사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-187">To enable and disable Windows PowerShell ISE in server versions of Windows, use the Add Roles and Features Wizard in Server Manager.</span></span>

<span data-ttu-id="bc51c-188">Windows PowerShell ISE에는 사용자 인터페이스가 필요 하므로 Windows Server의 Server Core 설치에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-188">Because Windows PowerShell ISE requires a user interface, it does not work on Server Core installations of Windows Server.</span></span> <span data-ttu-id="bc51c-189">그러나 Windows PowerShell ISE 기능을 추가 하는 경우 설치는 GUI 포함 서버를 자동으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-189">However, if you add the Windows PowerShell ISE feature, the installation automatically converts to Server with a GUI.</span></span>

<span data-ttu-id="bc51c-190">Windows PowerShell ISE는 WPF(Windows Presentation Foundation)를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-190">Windows PowerShell ISE is built on the Windows Presentation Foundation (WPF).</span></span>
<span data-ttu-id="bc51c-191">Windows PowerShell ISE의 그래픽 요소가 시스템에서 제대로 렌더링 되지 않는 경우 시스템에서 "WPF 하드웨어 가속 사용 안 함" 그래픽 렌더링 설정을 추가 하거나 조정 하 여 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc51c-191">If the graphical elements of Windows PowerShell ISE do not render correctly on your system, you might resolve the problem by adding or adjusting the "Disable WPF Hardware acceleration" graphics rendering settings on your system.</span></span> <span data-ttu-id="bc51c-192">자세한 내용은 [그래픽 렌더링 레지스트리 설정](/dotnet/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bc51c-192">For more information, see [Graphics Rendering Registry Settings](/dotnet/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc51c-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc51c-193">SEE ALSO</span></span>

[<span data-ttu-id="bc51c-194">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="bc51c-194">about_Debuggers</span></span>](about_Debuggers.md)

[<span data-ttu-id="bc51c-195">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="bc51c-195">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="bc51c-196">about_Updatable_Help</span><span class="sxs-lookup"><span data-stu-id="bc51c-196">about_Updatable_Help</span></span>](about_Updatable_Help.md)

[<span data-ttu-id="bc51c-197">Get-Help</span><span class="sxs-lookup"><span data-stu-id="bc51c-197">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="bc51c-198">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="bc51c-198">Get-IseSnippet</span></span>](xref:ISE.Get-IseSnippet)

[<span data-ttu-id="bc51c-199">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="bc51c-199">Import-IseSnippet</span></span>](xref:ISE.Import-IseSnippet)

[<span data-ttu-id="bc51c-200">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="bc51c-200">New-IseSnippet</span></span>](xref:ISE.New-IseSnippet)

[<span data-ttu-id="bc51c-201">Save-Help</span><span class="sxs-lookup"><span data-stu-id="bc51c-201">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

[<span data-ttu-id="bc51c-202">Show-Command</span><span class="sxs-lookup"><span data-stu-id="bc51c-202">Show-Command</span></span>](xref:Microsoft.PowerShell.Utility.Show-Command)

[<span data-ttu-id="bc51c-203">Update-Help</span><span class="sxs-lookup"><span data-stu-id="bc51c-203">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)
