---
description: PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSReadLine 정보
ms.openlocfilehash: ddc88dda3514e4279b6d91b023e26da88f645af7
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685220"
---
# <a name="psreadline"></a><span data-ttu-id="e989f-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="e989f-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="e989f-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="e989f-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="e989f-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="e989f-105">Short Description</span></span>

<span data-ttu-id="e989f-106">PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="e989f-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="e989f-107">Long Description</span></span>

<span data-ttu-id="e989f-108">PSReadLine 2.2은 PowerShell 콘솔에 대 한 강력한 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="e989f-109">이 콘솔은 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-109">It provides:</span></span>

- <span data-ttu-id="e989f-110">명령줄의 구문 색 지정</span><span class="sxs-lookup"><span data-stu-id="e989f-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="e989f-111">구문 오류를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="e989f-112">더 나은 여러 줄 환경 (편집 및 기록 모두)</span><span class="sxs-lookup"><span data-stu-id="e989f-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="e989f-113">사용자 지정 가능한 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="e989f-113">Customizable key bindings</span></span>
- <span data-ttu-id="e989f-114">Cmd 및 Emacs 모드</span><span class="sxs-lookup"><span data-stu-id="e989f-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="e989f-115">많은 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="e989f-115">Many configuration options</span></span>
- <span data-ttu-id="e989f-116">Bash 스타일 완성 (Cmd 모드에서는 선택 사항, Emacs 모드에서는 기본값)</span><span class="sxs-lookup"><span data-stu-id="e989f-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="e989f-117">Emacs yank/kill</span><span class="sxs-lookup"><span data-stu-id="e989f-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="e989f-118">PowerShell 토큰 기반 "word" 이동 및 중지</span><span class="sxs-lookup"><span data-stu-id="e989f-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="e989f-119">예측 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e989f-119">Predictive IntelliSense</span></span>

<span data-ttu-id="e989f-120">PSReadLine 2.2.0는 두 가지 새로운 예측 IntelliSense 기능을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="e989f-121">새를 선택할 수 있도록 **PredictionViewStyle** 매개 변수를 추가 했습니다 `ListView` .</span><span class="sxs-lookup"><span data-stu-id="e989f-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="e989f-122">PSReadLine을 `CommandPrediction` PS 7.1에 도입 된 api에 연결 하 여 사용자가 사용자 지정 원본에서 제안을 렌더링할 수 있는 예측 모듈을 가져올 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="e989f-123">PSReadLine에는 PowerShell 3.0 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="e989f-124">PSReadLine은 기본 콘솔 호스트, Visual Studio Code 및 창 터미널에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="e989f-125">PowerShell ISE에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="e989f-126">PSReadLine 2.2.0는 PowerShell 7.2과 함께 제공 되며, 지원 되는 모든 버전의 PowerShell에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="e989f-127">PowerShell 갤러리에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="e989f-128">지원 되는 버전의 PowerShell에서 PSReadLine 2.2.0을 설치 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="e989f-129">PowerShell 7.0부터 PowerShell은 화면 판독기 프로그램이 검색 된 경우 Windows에서 PSReadLine 자동 로드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="e989f-130">현재 PSReadLine은 화면 판독기에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="e989f-131">Windows에서 PowerShell 7.0의 기본 렌더링 및 형식이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="e989f-132">필요한 경우 모듈을 수동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="e989f-133">예측 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e989f-133">Predictive IntelliSense</span></span>

<span data-ttu-id="e989f-134">예측 IntelliSense는 사용자가 명령을 성공적으로 완료 하는 데 도움이 되는 탭 완성 이라는 개념에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="e989f-135">사용자가 사용자 기록과 추가 도메인 특정 플러그인의 일치 하는 예측에 따라 전체 명령을 검색, 편집 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="e989f-136">예측 IntelliSense 사용</span><span class="sxs-lookup"><span data-stu-id="e989f-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="e989f-137">예측 IntelliSense는 기본적으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="e989f-138">예측을 사용 하도록 설정 하려면 다음 명령을 실행 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="e989f-139">**PredictionSource** 매개 변수는 도메인 특정 요구 사항 및 사용자 지정 요구 사항에 대 한 플러그 인도 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="e989f-140">예측 IntelliSense를 사용 하지 않도록 설정 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="e989f-141">다음 함수는 **[PSConsoleReadLine]** 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="e989f-142">기본 편집 함수</span><span class="sxs-lookup"><span data-stu-id="e989f-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="e989f-143">중단</span><span class="sxs-lookup"><span data-stu-id="e989f-143">Abort</span></span>

<span data-ttu-id="e989f-144">현재 작업을 중단 합니다 (예: 증분 기록 검색).</span><span class="sxs-lookup"><span data-stu-id="e989f-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="e989f-145">Emacs `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="e989f-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="e989f-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="e989f-146">AcceptAndGetNext</span></span>

<span data-ttu-id="e989f-147">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-147">Attempt to execute the current input.</span></span> <span data-ttu-id="e989f-148">실행 될 수 있는 경우 (예: AcceptLine) 다음에 ReadLine이 호출 될 때 기록에서 다음 항목을 회수 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="e989f-149">Emacs `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="e989f-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="e989f-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="e989f-150">AcceptLine</span></span>

<span data-ttu-id="e989f-151">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-151">Attempt to execute the current input.</span></span> <span data-ttu-id="e989f-152">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="e989f-153">입력 `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="e989f-154">Emacs `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="e989f-155">Vi 삽입 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="e989f-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="e989f-156">AddLine</span></span>

<span data-ttu-id="e989f-157">연속 프롬프트가 다음 줄에 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="e989f-158">이는 한 줄이 자체적으로 전체 입력 인 경우에도 여러 줄 입력을 단일 명령으로 입력 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="e989f-159">입력 `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="e989f-160">Emacs `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="e989f-161">Vi 삽입 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="e989f-162">Vi 명령 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="e989f-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="e989f-163">BackwardDeleteChar</span></span>

<span data-ttu-id="e989f-164">커서 앞에 있는 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="e989f-165">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="e989f-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="e989f-166">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="e989f-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="e989f-167">Vi 삽입 모드: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e989f-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="e989f-168">Vi 명령 모드: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="e989f-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteinput"></a><span data-ttu-id="e989f-169">BackwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="e989f-169">BackwardDeleteInput</span></span>

<span data-ttu-id="e989f-170">Like BackwardKillInput-점에서 입력 시작 부분 까지의 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-170">Like BackwardKillInput - deletes text from the point to the start of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="e989f-171">입력 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="e989f-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="e989f-172">Vi 삽입 모드: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="e989f-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="e989f-173">Vi 명령 모드: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="e989f-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="e989f-174">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="e989f-174">BackwardDeleteLine</span></span>

<span data-ttu-id="e989f-175">Like BackwardKillLine-점에서 줄의 시작 부분으로 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-175">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="e989f-176">Vi 명령 모드: `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="e989f-176">Vi command mode: `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="e989f-177">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="e989f-177">BackwardDeleteWord</span></span>

<span data-ttu-id="e989f-178">이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-178">Deletes the previous word.</span></span>

- <span data-ttu-id="e989f-179">Vi 명령 모드: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="e989f-179">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillinput"></a><span data-ttu-id="e989f-180">BackwardKillInput</span><span class="sxs-lookup"><span data-stu-id="e989f-180">BackwardKillInput</span></span>

<span data-ttu-id="e989f-181">입력의 시작 부분부터 커서 까지의 텍스트를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-181">Clear the text from the start of the input to the cursor.</span></span> <span data-ttu-id="e989f-182">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e989f-183">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e989f-183">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="e989f-184">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="e989f-184">BackwardKillLine</span></span>

<span data-ttu-id="e989f-185">현재 논리 줄의 시작 부분부터 커서 까지의 텍스트를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-185">Clear the text from the start of the current logical line to the cursor.</span></span> <span data-ttu-id="e989f-186">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-186">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e989f-187">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-187">Function is unbound.</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="e989f-188">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="e989f-188">BackwardKillWord</span></span>

<span data-ttu-id="e989f-189">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-189">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="e989f-190">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-190">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="e989f-191">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-191">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e989f-192">Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="e989f-192">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="e989f-193">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e989f-193">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="e989f-194">Vi 삽입 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e989f-194">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="e989f-195">Vi 명령 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e989f-195">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="e989f-196">CancelLine</span><span class="sxs-lookup"><span data-stu-id="e989f-196">CancelLine</span></span>

<span data-ttu-id="e989f-197">화면에 입력을 그대로 두고 현재 입력을 취소 합니다. 그러나 프롬프트가 다시 계산 되도록 다시 호스트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-197">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="e989f-198">Vi 삽입 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="e989f-198">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="e989f-199">Vi 명령 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="e989f-199">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="e989f-200">복사</span><span class="sxs-lookup"><span data-stu-id="e989f-200">Copy</span></span>

<span data-ttu-id="e989f-201">선택한 영역을 시스템 클립보드에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-201">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="e989f-202">선택 된 지역이 없으면 전체 줄을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-202">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="e989f-203">입력 `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="e989f-203">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="e989f-204">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="e989f-204">CopyOrCancelLine</span></span>

<span data-ttu-id="e989f-205">텍스트를 선택한 경우 클립보드로 복사 하 고, 그렇지 않으면 줄을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-205">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="e989f-206">입력 `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="e989f-206">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="e989f-207">Emacs `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="e989f-207">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="e989f-208">잘라내기</span><span class="sxs-lookup"><span data-stu-id="e989f-208">Cut</span></span>

<span data-ttu-id="e989f-209">삭제 된 텍스트를 시스템 클립보드에 배치 하는 선택한 영역을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-209">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="e989f-210">입력 `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="e989f-210">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="e989f-211">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="e989f-211">DeleteChar</span></span>

<span data-ttu-id="e989f-212">커서 아래의 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-212">Delete the character under the cursor.</span></span>

- <span data-ttu-id="e989f-213">입력 `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="e989f-213">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="e989f-214">Emacs `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="e989f-214">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="e989f-215">Vi 삽입 모드: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="e989f-215">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="e989f-216">Vi 명령 모드: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e989f-216">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="e989f-217">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="e989f-217">DeleteCharOrExit</span></span>

<span data-ttu-id="e989f-218">커서 아래의 문자를 삭제 하거나, 줄이 비어 있으면 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-218">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="e989f-219">Emacs `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="e989f-219">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="e989f-220">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="e989f-220">DeleteEndOfBuffer</span></span>

<span data-ttu-id="e989f-221">여러 줄 버퍼의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-221">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="e989f-222">Vi 명령 모드: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="e989f-222">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="e989f-223">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="e989f-223">DeleteEndOfWord</span></span>

<span data-ttu-id="e989f-224">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-224">Delete to the end of the word.</span></span>

- <span data-ttu-id="e989f-225">Vi 명령 모드: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="e989f-225">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="e989f-226">Deleteline.invoke</span><span class="sxs-lookup"><span data-stu-id="e989f-226">DeleteLine</span></span>

<span data-ttu-id="e989f-227">여러 줄 버퍼의 현재 논리 줄을 삭제 하 고 실행 취소를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-227">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="e989f-228">Vi 명령 모드: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="e989f-228">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="e989f-229">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="e989f-229">DeletePreviousLines</span></span>

<span data-ttu-id="e989f-230">여러 줄 버퍼에서 요청 된 이전 논리 줄과 현재 논리 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-230">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="e989f-231">Vi 명령 모드: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="e989f-231">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="e989f-232">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="e989f-232">DeleteRelativeLines</span></span>

<span data-ttu-id="e989f-233">버퍼의 시작 부분에서 여러 줄 버퍼의 현재 논리 줄까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-233">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="e989f-234">대부분의 Vi 명령으로 `<d,g,g>` 명령 앞에는 절대 줄 번호를 지정 하는 숫자 인수를 추가할 수 있습니다 .이 숫자는 현재 줄 번호와 함께 삭제 될 줄의 범위를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-234">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="e989f-235">지정 하지 않으면 숫자 인수는 기본적으로 1로 설정 되며이는 여러 줄 버퍼의 첫 번째 논리 줄을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-235">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="e989f-236">여러 줄에서 삭제 되는 실제 줄 수는 현재 논리 줄 번호와 지정 된 숫자 인수 간의 차이로 계산 되므로 음수가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-236">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="e989f-237">따라서 메서드 이름의 _상대_ 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-237">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="e989f-238">Vi 명령 모드: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="e989f-238">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="e989f-239">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="e989f-239">DeleteNextLines</span></span>

<span data-ttu-id="e989f-240">여러 줄 버퍼에서 현재 논리 줄 및 요청 된 다음 논리 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-240">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="e989f-241">Vi 명령 모드: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="e989f-241">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="e989f-242">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="e989f-242">DeleteLineToFirstChar</span></span>

<span data-ttu-id="e989f-243">여러 줄 버퍼에서 현재 논리 줄의 비어 있지 않은 첫 번째 문자에서 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-243">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="e989f-244">Vi 명령 모드: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="e989f-244">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="e989f-245">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="e989f-245">DeleteToEnd</span></span>

<span data-ttu-id="e989f-246">줄의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-246">Delete to the end of the line.</span></span>

- <span data-ttu-id="e989f-247">Vi 명령 모드: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="e989f-247">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="e989f-248">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="e989f-248">DeleteWord</span></span>

<span data-ttu-id="e989f-249">다음 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-249">Delete the next word.</span></span>

- <span data-ttu-id="e989f-250">Vi 명령 모드: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="e989f-250">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteinput"></a><span data-ttu-id="e989f-251">ForwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="e989f-251">ForwardDeleteInput</span></span>

<span data-ttu-id="e989f-252">Like KillLine-포인트에서 입력 끝 까지의 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-252">Like KillLine - deletes text from the point to the end of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="e989f-253">입력 `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="e989f-253">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="e989f-254">Vi 삽입 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="e989f-254">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="e989f-255">Vi 명령 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="e989f-255">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="e989f-256">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="e989f-256">ForwardDeleteLine</span></span>

<span data-ttu-id="e989f-257">점에서 현재 논리 줄 끝까지 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-257">Deletes text from the point to the end of the current logical line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="e989f-258">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-258">Function is unbound</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="e989f-259">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="e989f-259">InsertLineAbove</span></span>

<span data-ttu-id="e989f-260">현재 줄에 커서가 있는 위치에 관계 없이 새 빈 줄이 현재 줄 위에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-260">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="e989f-261">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-261">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="e989f-262">입력 `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-262">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="e989f-263">Insertlinenea</span><span class="sxs-lookup"><span data-stu-id="e989f-263">InsertLineBelow</span></span>

<span data-ttu-id="e989f-264">커서가 현재 줄에 있는지 여부에 관계 없이 현재 줄 아래에 빈 줄이 새로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-264">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="e989f-265">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-265">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="e989f-266">입력 `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-266">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="e989f-267">InvertCase</span><span class="sxs-lookup"><span data-stu-id="e989f-267">InvertCase</span></span>

<span data-ttu-id="e989f-268">현재 문자의 대/소문자를 반전 하 고 다음으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-268">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="e989f-269">Vi 명령 모드: `<~>`</span><span class="sxs-lookup"><span data-stu-id="e989f-269">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="e989f-270">KillLine</span><span class="sxs-lookup"><span data-stu-id="e989f-270">KillLine</span></span>

<span data-ttu-id="e989f-271">입력의 끝 부분까지 커서에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-271">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="e989f-272">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-272">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e989f-273">Emacs `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="e989f-273">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="e989f-274">KillRegion</span><span class="sxs-lookup"><span data-stu-id="e989f-274">KillRegion</span></span>

<span data-ttu-id="e989f-275">커서와 표시 사이에 있는 텍스트를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-275">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="e989f-276">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-276">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="e989f-277">KillWord</span><span class="sxs-lookup"><span data-stu-id="e989f-277">KillWord</span></span>

<span data-ttu-id="e989f-278">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-278">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="e989f-279">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-279">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="e989f-280">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-280">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e989f-281">Cmd: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="e989f-281">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="e989f-282">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="e989f-282">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="e989f-283">Vi 삽입 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="e989f-283">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="e989f-284">Vi 명령 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="e989f-284">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="e989f-285">붙여넣기</span><span class="sxs-lookup"><span data-stu-id="e989f-285">Paste</span></span>

<span data-ttu-id="e989f-286">시스템 클립보드에서 텍스트를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-286">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="e989f-287">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="e989f-287">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="e989f-288">Vi 삽입 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="e989f-288">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="e989f-289">Vi 명령 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="e989f-289">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e989f-290">**Paste** 함수를 사용 하는 경우 클립보드 버퍼의 전체 내용이 psreadline의 입력 버퍼에 붙여넣어집니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-290">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="e989f-291">그런 다음 입력 버퍼가 PowerShell 파서로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-291">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="e989f-292">콘솔 응용 프로그램의 **마우스 오른쪽 단추 클릭** 붙여넣기 메서드를 사용 하 여 붙여넣은 입력은 입력 버퍼에 한 번에 한 문자씩 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-292">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="e989f-293">입력 버퍼는 줄 바꿈 문자가 복사 될 때 파서에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-293">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="e989f-294">따라서 입력은 한 번에 한 줄씩 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-294">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="e989f-295">붙여넣기 메서드 간의 차이점으로 인해 실행 동작이 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-295">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="e989f-296">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="e989f-296">PasteAfter</span></span>

<span data-ttu-id="e989f-297">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 뒤에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-297">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="e989f-298">Vi 명령 모드: `<p>`</span><span class="sxs-lookup"><span data-stu-id="e989f-298">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="e989f-299">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="e989f-299">PasteBefore</span></span>

<span data-ttu-id="e989f-300">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 앞에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-300">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="e989f-301">Vi 명령 모드: `<P>`</span><span class="sxs-lookup"><span data-stu-id="e989f-301">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="e989f-302">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="e989f-302">PrependAndAccept</span></span>

<span data-ttu-id="e989f-303">' # ' 앞에를 추가 하 고 줄을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-303">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="e989f-304">Vi 명령 모드: `<#>`</span><span class="sxs-lookup"><span data-stu-id="e989f-304">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="e989f-305">다시 실행</span><span class="sxs-lookup"><span data-stu-id="e989f-305">Redo</span></span>

<span data-ttu-id="e989f-306">실행 취소를 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-306">Undo an undo.</span></span>

- <span data-ttu-id="e989f-307">입력 `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e989f-307">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="e989f-308">Vi 삽입 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e989f-308">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="e989f-309">Vi 명령 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e989f-309">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="e989f-310">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="e989f-310">RepeatLastCommand</span></span>

<span data-ttu-id="e989f-311">마지막 텍스트 수정 작업을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-311">Repeat the last text modification.</span></span>

- <span data-ttu-id="e989f-312">Vi 명령 모드: `<.>`</span><span class="sxs-lookup"><span data-stu-id="e989f-312">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="e989f-313">RevertLine</span><span class="sxs-lookup"><span data-stu-id="e989f-313">RevertLine</span></span>

<span data-ttu-id="e989f-314">모든 입력을 현재 입력으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-314">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="e989f-315">입력 `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="e989f-315">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="e989f-316">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="e989f-316">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="e989f-317">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="e989f-317">ShellBackwardKillWord</span></span>

<span data-ttu-id="e989f-318">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-318">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="e989f-319">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-319">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="e989f-320">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-320">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="e989f-321">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-321">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="e989f-322">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="e989f-322">ShellKillWord</span></span>

<span data-ttu-id="e989f-323">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-323">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="e989f-324">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-324">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="e989f-325">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-325">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="e989f-326">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-326">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="e989f-327">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="e989f-327">SwapCharacters</span></span>

<span data-ttu-id="e989f-328">현재 문자와 그 앞의 문자를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-328">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="e989f-329">Emacs `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="e989f-329">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="e989f-330">Vi 삽입 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="e989f-330">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="e989f-331">Vi 명령 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="e989f-331">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="e989f-332">실행 취소</span><span class="sxs-lookup"><span data-stu-id="e989f-332">Undo</span></span>

<span data-ttu-id="e989f-333">이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-333">Undo a previous edit.</span></span>

- <span data-ttu-id="e989f-334">입력 `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="e989f-334">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="e989f-335">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="e989f-335">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="e989f-336">Vi 삽입 모드: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="e989f-336">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="e989f-337">Vi 명령 모드: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="e989f-337">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="e989f-338">모두를</span><span class="sxs-lookup"><span data-stu-id="e989f-338">UndoAll</span></span>

<span data-ttu-id="e989f-339">줄의 모든 이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-339">Undo all previous edits for line.</span></span>

- <span data-ttu-id="e989f-340">Vi 명령 모드: `<U>`</span><span class="sxs-lookup"><span data-stu-id="e989f-340">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="e989f-341">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="e989f-341">UnixWordRubout</span></span>

<span data-ttu-id="e989f-342">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-342">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="e989f-343">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-343">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="e989f-344">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-344">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e989f-345">Emacs `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="e989f-345">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="e989f-346">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="e989f-346">ValidateAndAcceptLine</span></span>

<span data-ttu-id="e989f-347">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-347">Attempt to execute the current input.</span></span> <span data-ttu-id="e989f-348">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-348">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="e989f-349">Emacs `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="e989f-349">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="e989f-350">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="e989f-350">ViAcceptLine</span></span>

<span data-ttu-id="e989f-351">줄을 적용 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-351">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="e989f-352">Vi 명령 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="e989f-352">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="e989f-353">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="e989f-353">ViAcceptLineOrExit</span></span>

<span data-ttu-id="e989f-354">Emacs 모드에서 DeleteCharOrExit와 비슷하지만 문자를 삭제 하는 대신 줄을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-354">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="e989f-355">Vi 삽입 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="e989f-355">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="e989f-356">Vi 명령 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="e989f-356">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="e989f-357">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="e989f-357">ViAppendLine</span></span>

<span data-ttu-id="e989f-358">현재 줄 아래에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-358">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="e989f-359">Vi 명령 모드: `<o>`</span><span class="sxs-lookup"><span data-stu-id="e989f-359">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="e989f-360">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="e989f-360">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="e989f-361">공백을 단어 구분 기호로 사용 하 여 이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-361">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="e989f-362">Vi 명령 모드: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="e989f-362">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="e989f-363">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="e989f-363">ViBackwardGlob</span></span>

<span data-ttu-id="e989f-364">공백을 구분 기호로 사용 하 여 커서를 이전 단어의 시작 부분으로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-364">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="e989f-365">Vi 명령 모드: `<B>`</span><span class="sxs-lookup"><span data-stu-id="e989f-365">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="e989f-366">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="e989f-366">ViDeleteBrace</span></span>

<span data-ttu-id="e989f-367">괄호를 포함 하 여 일치 하는 중괄호, 괄호 또는 대괄호를 찾아 내에서 모든 내용을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-367">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="e989f-368">Vi 명령 모드: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="e989f-368">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="e989f-369">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="e989f-369">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="e989f-370">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-370">Delete to the end of the word.</span></span>

- <span data-ttu-id="e989f-371">Vi 명령 모드: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="e989f-371">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="e989f-372">Videletlob</span><span class="sxs-lookup"><span data-stu-id="e989f-372">ViDeleteGlob</span></span>

<span data-ttu-id="e989f-373">다음 glob (공백으로 구분 된 단어)를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-373">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="e989f-374">Vi 명령 모드: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="e989f-374">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="e989f-375">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="e989f-375">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="e989f-376">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-376">Deletes until given character.</span></span>

- <span data-ttu-id="e989f-377">Vi 명령 모드: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="e989f-377">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="e989f-378">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="e989f-378">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="e989f-379">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-379">Deletes until given character.</span></span>

- <span data-ttu-id="e989f-380">Vi 명령 모드: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="e989f-380">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="e989f-381">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="e989f-381">ViDeleteToChar</span></span>

<span data-ttu-id="e989f-382">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-382">Deletes until given character.</span></span>

- <span data-ttu-id="e989f-383">Vi 명령 모드: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="e989f-383">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="e989f-384">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="e989f-384">ViDeleteToCharBackward</span></span>

<span data-ttu-id="e989f-385">지정 된 문자까지 뒤로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-385">Deletes backwards until given character.</span></span>

- <span data-ttu-id="e989f-386">Vi 명령 모드: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="e989f-386">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="e989f-387">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="e989f-387">ViInsertAtBegining</span></span>

<span data-ttu-id="e989f-388">삽입 모드로 전환 하 고 줄의 시작 부분에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-388">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="e989f-389">Vi 명령 모드: `<I>`</span><span class="sxs-lookup"><span data-stu-id="e989f-389">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="e989f-390">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="e989f-390">ViInsertAtEnd</span></span>

<span data-ttu-id="e989f-391">삽입 모드로 전환 하 고 줄의 끝에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-391">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="e989f-392">Vi 명령 모드: `<A>`</span><span class="sxs-lookup"><span data-stu-id="e989f-392">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="e989f-393">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="e989f-393">ViInsertLine</span></span>

<span data-ttu-id="e989f-394">현재 줄 위에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-394">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="e989f-395">Vi 명령 모드: `<O>`</span><span class="sxs-lookup"><span data-stu-id="e989f-395">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="e989f-396">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="e989f-396">ViInsertWithAppend</span></span>

<span data-ttu-id="e989f-397">현재 줄 위치에서 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-397">Append from the current line position.</span></span>

- <span data-ttu-id="e989f-398">Vi 명령 모드: `<a>`</span><span class="sxs-lookup"><span data-stu-id="e989f-398">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="e989f-399">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="e989f-399">ViInsertWithDelete</span></span>

<span data-ttu-id="e989f-400">현재 문자를 삭제 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-400">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="e989f-401">Vi 명령 모드: `<s>`</span><span class="sxs-lookup"><span data-stu-id="e989f-401">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="e989f-402">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="e989f-402">ViJoinLines</span></span>

<span data-ttu-id="e989f-403">현재 줄과 다음 줄을 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-403">Joins the current line and the next line.</span></span>

- <span data-ttu-id="e989f-404">Vi 명령 모드: `<J>`</span><span class="sxs-lookup"><span data-stu-id="e989f-404">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="e989f-405">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="e989f-405">ViReplaceLine</span></span>

<span data-ttu-id="e989f-406">전체 명령줄을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-406">Erase the entire command line.</span></span>

- <span data-ttu-id="e989f-407">Vi 명령 모드: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="e989f-407">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="e989f-408">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="e989f-408">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="e989f-409">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-409">Replaces until given character.</span></span>

- <span data-ttu-id="e989f-410">Vi 명령 모드: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="e989f-410">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="e989f-411">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="e989f-411">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="e989f-412">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-412">Replaces until given character.</span></span>

- <span data-ttu-id="e989f-413">Vi 명령 모드: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="e989f-413">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="e989f-414">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="e989f-414">ViReplaceToChar</span></span>

<span data-ttu-id="e989f-415">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-415">Deletes until given character.</span></span>

- <span data-ttu-id="e989f-416">Vi 명령 모드: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="e989f-416">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="e989f-417">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="e989f-417">ViReplaceToCharBackward</span></span>

<span data-ttu-id="e989f-418">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-418">Replaces until given character.</span></span>

- <span data-ttu-id="e989f-419">Vi 명령 모드: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="e989f-419">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="e989f-420">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="e989f-420">ViYankBeginningOfLine</span></span>

<span data-ttu-id="e989f-421">버퍼의 시작 부분에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="e989f-421">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="e989f-422">Vi 명령 모드: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="e989f-422">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="e989f-423">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="e989f-423">ViYankEndOfGlob</span></span>

<span data-ttu-id="e989f-424">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-424">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="e989f-425">Vi 명령 모드: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="e989f-425">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="e989f-426">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="e989f-426">ViYankEndOfWord</span></span>

<span data-ttu-id="e989f-427">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-427">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="e989f-428">Vi 명령 모드: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="e989f-428">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="e989f-429">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="e989f-429">ViYankLeft</span></span>

<span data-ttu-id="e989f-430">커서의 왼쪽에 문자를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-430">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="e989f-431">Vi 명령 모드: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="e989f-431">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="e989f-432">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="e989f-432">ViYankLine</span></span>

<span data-ttu-id="e989f-433">전체 버퍼를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-433">Yank the entire buffer.</span></span>

- <span data-ttu-id="e989f-434">Vi 명령 모드: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="e989f-434">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="e989f-435">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="e989f-435">ViYankNextGlob</span></span>

<span data-ttu-id="e989f-436">커서에서 다음 단어의 시작 부분으로 Yank.</span><span class="sxs-lookup"><span data-stu-id="e989f-436">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="e989f-437">Vi 명령 모드: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="e989f-437">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="e989f-438">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="e989f-438">ViYankNextWord</span></span>

<span data-ttu-id="e989f-439">커서 뒤의 단어를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-439">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="e989f-440">Vi 명령 모드: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="e989f-440">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="e989f-441">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="e989f-441">ViYankPercent</span></span>

<span data-ttu-id="e989f-442">짝이 되는 중괄호에서 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-442">Yank to/from matching brace.</span></span>

- <span data-ttu-id="e989f-443">Vi 명령 모드: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="e989f-443">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="e989f-444">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="e989f-444">ViYankPreviousGlob</span></span>

<span data-ttu-id="e989f-445">단어의 시작부터 커서까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-445">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="e989f-446">Vi 명령 모드: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="e989f-446">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="e989f-447">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="e989f-447">ViYankPreviousWord</span></span>

<span data-ttu-id="e989f-448">커서 앞에 단어를 Yank.</span><span class="sxs-lookup"><span data-stu-id="e989f-448">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="e989f-449">Vi 명령 모드: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="e989f-449">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="e989f-450">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="e989f-450">ViYankRight</span></span>

<span data-ttu-id="e989f-451">커서 오른쪽의 및 아래에 Yank 문자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-451">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="e989f-452">Vi 명령 모드: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e989f-452">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="e989f-453">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="e989f-453">ViYankToEndOfLine</span></span>

<span data-ttu-id="e989f-454">커서에서 버퍼 끝까지 Yank.</span><span class="sxs-lookup"><span data-stu-id="e989f-454">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="e989f-455">Vi 명령 모드: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="e989f-455">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="e989f-456">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="e989f-456">ViYankToFirstChar</span></span>

<span data-ttu-id="e989f-457">공백이 아닌 첫 번째 문자에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="e989f-457">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="e989f-458">Vi 명령 모드: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="e989f-458">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="e989f-459">Yank</span><span class="sxs-lookup"><span data-stu-id="e989f-459">Yank</span></span>

<span data-ttu-id="e989f-460">가장 최근에 종료 된 텍스트를 입력에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-460">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="e989f-461">Emacs `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e989f-461">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="e989f-462">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="e989f-462">YankLastArg</span></span>

<span data-ttu-id="e989f-463">이전 기록 줄에서 마지막 인수를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-463">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="e989f-464">인수를 사용 하면 처음 호출 될 때 YankNthArg 처럼 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-464">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="e989f-465">여러 번 호출 된 경우에는 기록 및 인수에서 방향을 설정 합니다. (음수는 방향을 반대로 바꿉니다.)</span><span class="sxs-lookup"><span data-stu-id="e989f-465">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="e989f-466">입력 `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="e989f-466">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="e989f-467">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="e989f-467">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="e989f-468">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="e989f-468">YankNthArg</span></span>

<span data-ttu-id="e989f-469">이전 기록 줄에서 첫 번째 인수 (명령 뒤)를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-469">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="e989f-470">인수를 사용 하는 경우 n 번째 인수 (0부터 시작)를 yank. 인수가 음수 이면 마지막 인수부터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-470">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="e989f-471">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e989f-471">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="e989f-472">YankPop</span><span class="sxs-lookup"><span data-stu-id="e989f-472">YankPop</span></span>

<span data-ttu-id="e989f-473">이전 작업이 Yank 또는 YankPop 인 경우 이전 빼낼 텍스트를 kill 링에서 다음에 종료 된 텍스트로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-473">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="e989f-474">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="e989f-474">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="e989f-475">커서 이동 함수</span><span class="sxs-lookup"><span data-stu-id="e989f-475">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="e989f-476">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="e989f-476">BackwardChar</span></span>

<span data-ttu-id="e989f-477">커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-477">Move the cursor one character to the left.</span></span> <span data-ttu-id="e989f-478">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-478">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="e989f-479">입력 `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-479">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="e989f-480">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="e989f-480">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="e989f-481">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="e989f-481">BackwardWord</span></span>

<span data-ttu-id="e989f-482">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-482">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="e989f-483">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-483">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e989f-484">입력 `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-484">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="e989f-485">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="e989f-485">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="e989f-486">Vi 삽입 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-486">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="e989f-487">Vi 명령 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-487">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="e989f-488">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="e989f-488">BeginningOfLine</span></span>

<span data-ttu-id="e989f-489">입력에 여러 줄이 있는 경우 현재 줄의 시작 부분으로 이동 하거나 이미 줄의 시작 부분에 있는 경우 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-489">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="e989f-490">입력에 한 줄이 있으면 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-490">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="e989f-491">입력 `<Home>`</span><span class="sxs-lookup"><span data-stu-id="e989f-491">Cmd: `<Home>`</span></span>
- <span data-ttu-id="e989f-492">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="e989f-492">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="e989f-493">Vi 삽입 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="e989f-493">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="e989f-494">Vi 명령 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="e989f-494">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="e989f-495">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="e989f-495">EndOfLine</span></span>

<span data-ttu-id="e989f-496">입력에 여러 줄이 있는 경우 현재 줄의 끝으로 이동 하거나 줄의 끝에 있는 경우 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-496">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="e989f-497">입력에 한 줄이 있으면 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-497">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="e989f-498">입력 `<End>`</span><span class="sxs-lookup"><span data-stu-id="e989f-498">Cmd: `<End>`</span></span>
- <span data-ttu-id="e989f-499">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="e989f-499">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="e989f-500">Vi 삽입 모드: `<End>`</span><span class="sxs-lookup"><span data-stu-id="e989f-500">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="e989f-501">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="e989f-501">ForwardChar</span></span>

<span data-ttu-id="e989f-502">커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-502">Move the cursor one character to the right.</span></span> <span data-ttu-id="e989f-503">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-503">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="e989f-504">입력 `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-504">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="e989f-505">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="e989f-505">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="e989f-506">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="e989f-506">ForwardWord</span></span>

<span data-ttu-id="e989f-507">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="e989f-508">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e989f-509">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="e989f-509">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="e989f-510">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="e989f-510">GotoBrace</span></span>

<span data-ttu-id="e989f-511">짝이 되는 중괄호, 괄호 또는 대괄호로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-511">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="e989f-512">입력 `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="e989f-512">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="e989f-513">Vi 삽입 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="e989f-513">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="e989f-514">Vi 명령 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="e989f-514">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="e989f-515">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="e989f-515">GotoColumn</span></span>

<span data-ttu-id="e989f-516">Arg로 표시 된 열로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-516">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="e989f-517">Vi 명령 모드: `<|>`</span><span class="sxs-lookup"><span data-stu-id="e989f-517">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="e989f-518">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="e989f-518">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="e989f-519">줄에서 비어 있지 않은 첫 번째 문자로 커서를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-519">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="e989f-520">Vi 명령 모드: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="e989f-520">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="e989f-521">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="e989f-521">MoveToEndOfLine</span></span>

<span data-ttu-id="e989f-522">커서를 입력 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-522">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="e989f-523">Vi 명령 모드: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="e989f-523">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="e989f-524">NextLine</span><span class="sxs-lookup"><span data-stu-id="e989f-524">NextLine</span></span>

<span data-ttu-id="e989f-525">커서를 다음 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-525">Move the cursor to the next line.</span></span>

- <span data-ttu-id="e989f-526">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-526">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="e989f-527">NextWord</span><span class="sxs-lookup"><span data-stu-id="e989f-527">NextWord</span></span>

<span data-ttu-id="e989f-528">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-528">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="e989f-529">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-529">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e989f-530">입력 `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-530">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="e989f-531">Vi 삽입 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-531">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="e989f-532">Vi 명령 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-532">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="e989f-533">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="e989f-533">NextWordEnd</span></span>

<span data-ttu-id="e989f-534">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-534">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="e989f-535">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-535">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e989f-536">Vi 명령 모드: `<e>`</span><span class="sxs-lookup"><span data-stu-id="e989f-536">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="e989f-537">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="e989f-537">PreviousLine</span></span>

<span data-ttu-id="e989f-538">커서를 이전 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-538">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="e989f-539">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-539">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="e989f-540">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="e989f-540">ShellBackwardWord</span></span>

<span data-ttu-id="e989f-541">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-541">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="e989f-542">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-542">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="e989f-543">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-543">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="e989f-544">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="e989f-544">ShellForwardWord</span></span>

<span data-ttu-id="e989f-545">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-545">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="e989f-546">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-546">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="e989f-547">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-547">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="e989f-548">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="e989f-548">ShellNextWord</span></span>

<span data-ttu-id="e989f-549">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-549">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="e989f-550">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-550">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="e989f-551">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-551">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="e989f-552">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="e989f-552">ViBackwardChar</span></span>

<span data-ttu-id="e989f-553">Vi 편집 모드에서 커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-553">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="e989f-554">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-554">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="e989f-555">Vi 삽입 모드: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-555">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="e989f-556">Vi 명령 모드: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="e989f-556">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="e989f-557">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="e989f-557">ViBackwardWord</span></span>

<span data-ttu-id="e989f-558">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-558">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="e989f-559">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-559">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e989f-560">Vi 명령 모드: `<b>`</span><span class="sxs-lookup"><span data-stu-id="e989f-560">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="e989f-561">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="e989f-561">ViForwardChar</span></span>

<span data-ttu-id="e989f-562">Vi 편집 모드에서 커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-562">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="e989f-563">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-563">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="e989f-564">Vi 삽입 모드: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-564">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="e989f-565">Vi 명령 모드: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="e989f-565">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="e989f-566">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="e989f-566">ViEndOfGlob</span></span>

<span data-ttu-id="e989f-567">공백을 구분 기호로 사용 하 여 커서를 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-567">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="e989f-568">Vi 명령 모드: `<E>`</span><span class="sxs-lookup"><span data-stu-id="e989f-568">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="e989f-569">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="e989f-569">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="e989f-570">공백을 단어 구분 기호로 사용 하 여 이전 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-570">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="e989f-571">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-571">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="e989f-572">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="e989f-572">ViGotoBrace</span></span>

<span data-ttu-id="e989f-573">GotoBrace와 비슷하지만 토큰 기반이 아니라 문자 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-573">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="e989f-574">Vi 명령 모드: `<%>`</span><span class="sxs-lookup"><span data-stu-id="e989f-574">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="e989f-575">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="e989f-575">ViNextGlob</span></span>

<span data-ttu-id="e989f-576">공백을 단어 구분 기호로 사용 하 여 다음 단어로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-576">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="e989f-577">Vi 명령 모드: `<W>`</span><span class="sxs-lookup"><span data-stu-id="e989f-577">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="e989f-578">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="e989f-578">ViNextWord</span></span>

<span data-ttu-id="e989f-579">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-579">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="e989f-580">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-580">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e989f-581">Vi 명령 모드: `<w>`</span><span class="sxs-lookup"><span data-stu-id="e989f-581">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="e989f-582">기록 함수</span><span class="sxs-lookup"><span data-stu-id="e989f-582">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="e989f-583">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="e989f-583">BeginningOfHistory</span></span>

<span data-ttu-id="e989f-584">기록의 첫 번째 항목으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-584">Move to the first item in the history.</span></span>

- <span data-ttu-id="e989f-585">Emacs `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="e989f-585">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="e989f-586">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="e989f-586">ClearHistory</span></span>

<span data-ttu-id="e989f-587">PSReadLine에서 기록을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-587">Clears history in PSReadLine.</span></span> <span data-ttu-id="e989f-588">PowerShell 기록에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-588">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="e989f-589">입력 `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="e989f-589">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="e989f-590">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="e989f-590">EndOfHistory</span></span>

<span data-ttu-id="e989f-591">기록에서 마지막 항목 (현재 입력)으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-591">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="e989f-592">Emacs `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="e989f-592">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="e989f-593">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="e989f-593">ForwardSearchHistory</span></span>

<span data-ttu-id="e989f-594">기록을 통해 증분 전달 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-594">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="e989f-595">입력 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="e989f-595">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="e989f-596">Emacs `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="e989f-596">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="e989f-597">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="e989f-597">HistorySearchBackward</span></span>

<span data-ttu-id="e989f-598">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-598">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="e989f-599">입력 `<F8>`</span><span class="sxs-lookup"><span data-stu-id="e989f-599">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="e989f-600">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="e989f-600">HistorySearchForward</span></span>

<span data-ttu-id="e989f-601">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-601">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="e989f-602">입력 `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="e989f-602">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="e989f-603">NextHistory</span><span class="sxs-lookup"><span data-stu-id="e989f-603">NextHistory</span></span>

<span data-ttu-id="e989f-604">현재 입력을 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-604">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="e989f-605">입력 `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-605">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="e989f-606">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="e989f-606">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="e989f-607">Vi 삽입 모드: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-607">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="e989f-608">Vi 명령 모드: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="e989f-608">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="e989f-609">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="e989f-609">PreviousHistory</span></span>

<span data-ttu-id="e989f-610">현재 입력을 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-610">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="e989f-611">입력 `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-611">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="e989f-612">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="e989f-612">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="e989f-613">Vi 삽입 모드: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-613">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="e989f-614">Vi 명령 모드: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="e989f-614">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="e989f-615">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="e989f-615">ReverseSearchHistory</span></span>

<span data-ttu-id="e989f-616">기록을 통해 증분 역방향 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-616">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="e989f-617">입력 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="e989f-617">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="e989f-618">Emacs `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="e989f-618">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="e989f-619">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="e989f-619">ViSearchHistoryBackward</span></span>

<span data-ttu-id="e989f-620">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-620">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="e989f-621">Vi 삽입 모드: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="e989f-621">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="e989f-622">Vi 명령 모드: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="e989f-622">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="e989f-623">완료 함수</span><span class="sxs-lookup"><span data-stu-id="e989f-623">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="e989f-624">완료</span><span class="sxs-lookup"><span data-stu-id="e989f-624">Complete</span></span>

<span data-ttu-id="e989f-625">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-625">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="e989f-626">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-626">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="e989f-627">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-627">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="e989f-628">Emacs `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="e989f-628">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="e989f-629">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="e989f-629">MenuComplete</span></span>

<span data-ttu-id="e989f-630">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-630">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="e989f-631">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-631">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="e989f-632">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-632">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="e989f-633">Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e989f-633">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="e989f-634">Emacs `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e989f-634">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="e989f-635">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="e989f-635">PossibleCompletions</span></span>

<span data-ttu-id="e989f-636">가능한 완료 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-636">Display the list of possible completions.</span></span>

- <span data-ttu-id="e989f-637">Emacs `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="e989f-637">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="e989f-638">Vi 삽입 모드: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e989f-638">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="e989f-639">Vi 명령 모드: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e989f-639">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="e989f-640">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="e989f-640">TabCompleteNext</span></span>

<span data-ttu-id="e989f-641">다음에 사용 가능한 완료로 커서를 둘러싼 텍스트를 완성 해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-641">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="e989f-642">입력 `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="e989f-642">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="e989f-643">Vi 명령 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="e989f-643">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="e989f-644">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="e989f-644">TabCompletePrevious</span></span>

<span data-ttu-id="e989f-645">이전에 사용 가능한 완료를 사용 하 여 커서를 둘러싼 텍스트를 완료 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-645">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="e989f-646">입력 `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="e989f-646">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="e989f-647">Vi 명령 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="e989f-647">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="e989f-648">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="e989f-648">ViTabCompleteNext</span></span>

<span data-ttu-id="e989f-649">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompleteNext를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-649">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="e989f-650">Vi 삽입 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="e989f-650">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="e989f-651">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="e989f-651">ViTabCompletePrevious</span></span>

<span data-ttu-id="e989f-652">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompletePrevious를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-652">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="e989f-653">Vi 삽입 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="e989f-653">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="prediction-functions"></a><span data-ttu-id="e989f-654">예측 함수</span><span class="sxs-lookup"><span data-stu-id="e989f-654">Prediction functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="e989f-655">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="e989f-655">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="e989f-656">`InlineView`예측에 대 한 보기 스타일로를 사용 하는 경우 인라인 제안의 다음 단어를 그대로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-656">When using `InlineView` as the view style for prediction, accept the next word of the inline suggestion.</span></span>

- <span data-ttu-id="e989f-657">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-657">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="e989f-658">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="e989f-658">AcceptSuggestion</span></span>

<span data-ttu-id="e989f-659">`InlineView`예측에 대 한 보기 스타일로를 사용 하는 경우 현재 인라인 제안을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-659">When using `InlineView` as the view style for prediction, accept the current inline suggestion.</span></span>

- <span data-ttu-id="e989f-660">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-660">Function is unbound.</span></span>

### <a name="nextsuggestion"></a><span data-ttu-id="e989f-661">NextSuggestion</span><span class="sxs-lookup"><span data-stu-id="e989f-661">NextSuggestion</span></span>

<span data-ttu-id="e989f-662">`ListView`예측에 대 한 보기 스타일로를 사용 하는 경우 목록에서 다음 제안으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-662">When using `ListView` as the view style for prediction, navigate to the next suggestion in the list.</span></span>

- <span data-ttu-id="e989f-663">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-663">Function is unbound.</span></span>

### <a name="previoussuggestion"></a><span data-ttu-id="e989f-664">PreviousSuggestion</span><span class="sxs-lookup"><span data-stu-id="e989f-664">PreviousSuggestion</span></span>

<span data-ttu-id="e989f-665">`ListView`예측에 대 한 보기 스타일로을 사용 하는 경우 목록에서 이전 제안으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-665">When using `ListView` as the view style for prediction, navigate to the previous suggestion in the list.</span></span>

- <span data-ttu-id="e989f-666">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-666">Function is unbound.</span></span>

### <a name="switchpredictionview"></a><span data-ttu-id="e989f-667">SwitchPredictionView</span><span class="sxs-lookup"><span data-stu-id="e989f-667">SwitchPredictionView</span></span>

<span data-ttu-id="e989f-668">및 간의 예측에 대 한 뷰 스타일을 전환 합니다 `InlineView` `ListView` .</span><span class="sxs-lookup"><span data-stu-id="e989f-668">Switch the view style for prediction between `InlineView` and `ListView`.</span></span>

- <span data-ttu-id="e989f-669">입력 `<F2>`</span><span class="sxs-lookup"><span data-stu-id="e989f-669">Cmd: `<F2>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="e989f-670">기타 함수</span><span class="sxs-lookup"><span data-stu-id="e989f-670">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="e989f-671">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="e989f-671">CaptureScreen</span></span>

<span data-ttu-id="e989f-672">대화형 화면 캡처 시작-위쪽/아래쪽 화살표 선 선택, 선택한 텍스트를 클립보드에 텍스트 및 html로 복사를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-672">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="e989f-673">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-673">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="e989f-674">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="e989f-674">ClearScreen</span></span>

<span data-ttu-id="e989f-675">화면을 지우고 화면 위쪽에 현재 줄을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-675">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="e989f-676">입력 `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="e989f-676">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="e989f-677">Emacs `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="e989f-677">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="e989f-678">Vi 삽입 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="e989f-678">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="e989f-679">Vi 명령 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="e989f-679">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="e989f-680">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="e989f-680">DigitArgument</span></span>

<span data-ttu-id="e989f-681">다른 함수에 전달할 새 숫자 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-681">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="e989f-682">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="e989f-682">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="e989f-683">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="e989f-683">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="e989f-684">Vi 명령 모드: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` `<7>` `<8>` ,,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="e989f-684">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="e989f-685">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="e989f-685">InvokePrompt</span></span>

<span data-ttu-id="e989f-686">현재 프롬프트를 지우고 prompt 함수를 호출 하 여 프롬프트를 다시 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-686">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="e989f-687">상태를 변경 하는 사용자 지정 키 처리기 (예: 현재 디렉터리 변경)에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-687">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="e989f-688">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-688">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="e989f-689">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="e989f-689">ScrollDisplayDown</span></span>

<span data-ttu-id="e989f-690">한 화면 아래로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-690">Scroll the display down one screen.</span></span>

- <span data-ttu-id="e989f-691">입력 `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="e989f-691">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="e989f-692">Emacs `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="e989f-692">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="e989f-693">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="e989f-693">ScrollDisplayDownLine</span></span>

<span data-ttu-id="e989f-694">표시를 한 줄 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-694">Scroll the display down one line.</span></span>

- <span data-ttu-id="e989f-695">입력 `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="e989f-695">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="e989f-696">Emacs `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="e989f-696">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="e989f-697">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="e989f-697">ScrollDisplayToCursor</span></span>

<span data-ttu-id="e989f-698">표시를 커서로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-698">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="e989f-699">Emacs `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="e989f-699">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="e989f-700">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="e989f-700">ScrollDisplayTop</span></span>

<span data-ttu-id="e989f-701">표시를 맨 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-701">Scroll the display to the top.</span></span>

- <span data-ttu-id="e989f-702">Emacs `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="e989f-702">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="e989f-703">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="e989f-703">ScrollDisplayUp</span></span>

<span data-ttu-id="e989f-704">한 화면 위로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-704">Scroll the display up one screen.</span></span>

- <span data-ttu-id="e989f-705">입력 `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="e989f-705">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="e989f-706">Emacs `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="e989f-706">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="e989f-707">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="e989f-707">ScrollDisplayUpLine</span></span>

<span data-ttu-id="e989f-708">디스플레이를 한 줄 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-708">Scroll the display up one line.</span></span>

- <span data-ttu-id="e989f-709">입력 `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="e989f-709">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="e989f-710">Emacs `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="e989f-710">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="e989f-711">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="e989f-711">SelfInsert</span></span>

<span data-ttu-id="e989f-712">키를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-712">Insert the key.</span></span>

- <span data-ttu-id="e989f-713">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-713">Function is unbound.</span></span>

### <a name="showcommandhelp"></a><span data-ttu-id="e989f-714">ShowCommandHelp</span><span class="sxs-lookup"><span data-stu-id="e989f-714">ShowCommandHelp</span></span>

<span data-ttu-id="e989f-715">전체 cmdlet 도움말의 뷰를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-715">Provides a view of full cmdlet help.</span></span> <span data-ttu-id="e989f-716">커서가 완전히 확장 된 매개 변수의 끝에 있을 때 키를 누르면 `<F1>` 해당 매개 변수 위치에 도움말 표시 위치가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-716">When the cursor is at the end of a fully-expanded parameter, hitting the `<F1>` key positions the display of help at the location of that parameter.</span></span>

<span data-ttu-id="e989f-717">도움말은 **Microsoft. PowerShell** 호출기를 사용 하 여 대체 화면 버퍼에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-717">The help is displayed on an alternate screen buffer using a Pager from **Microsoft.PowerShell.Pager**.</span></span> <span data-ttu-id="e989f-718">페이저를 종료 하면 원래 화면에서 원래 커서 위치로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-718">When you exit the pager you are returned to the original cursor position on the original screen.</span></span> <span data-ttu-id="e989f-719">이 호출기는 [Windows 터미널](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701)과 같은 최신 터미널 응용 프로그램 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-719">This pager only works in modern terminal applications such as [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701).</span></span>

- <span data-ttu-id="e989f-720">입력 `<F1>`</span><span class="sxs-lookup"><span data-stu-id="e989f-720">Cmd: `<F1>`</span></span>
- <span data-ttu-id="e989f-721">Emacs `<F1>`</span><span class="sxs-lookup"><span data-stu-id="e989f-721">Emacs: `<F1>`</span></span>
- <span data-ttu-id="e989f-722">Vi 삽입 모드: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="e989f-722">Vi insert mode: `<F1>`</span></span>
- <span data-ttu-id="e989f-723">Vi 명령 모드: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="e989f-723">Vi command mode: `<F1>`</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="e989f-724">ShowKeyBindings 바인딩</span><span class="sxs-lookup"><span data-stu-id="e989f-724">ShowKeyBindings</span></span>

<span data-ttu-id="e989f-725">모든 바인딩된 키를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-725">Show all bound keys.</span></span>

- <span data-ttu-id="e989f-726">입력 `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e989f-726">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="e989f-727">Emacs `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e989f-727">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="e989f-728">Vi 삽입 모드: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e989f-728">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="showparameterhelp"></a><span data-ttu-id="e989f-729">ShowParameterHelp</span><span class="sxs-lookup"><span data-stu-id="e989f-729">ShowParameterHelp</span></span>

<span data-ttu-id="e989f-730">는와 같이 현재 명령줄 아래에 표시 하 여 매개 변수에 대 한 동적 도움말을 제공 `MenuComplete` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-730">Provides dynamic help for parameters by showing it below the current command line like `MenuComplete`.</span></span> <span data-ttu-id="e989f-731">키를 누를 때 커서는 완전히 확장 된 매개 변수 이름의 끝에 있어야 합니다 `<Alt+h>` .</span><span class="sxs-lookup"><span data-stu-id="e989f-731">The cursor must be at the end of the fully-expanded parameter name when you press the `<Alt+h>` key.</span></span>

- <span data-ttu-id="e989f-732">입력 `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="e989f-732">Cmd: `<Alt+h>`</span></span>
- <span data-ttu-id="e989f-733">Emacs `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="e989f-733">Emacs: `<Alt+h>`</span></span>
- <span data-ttu-id="e989f-734">Vi 삽입 모드: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="e989f-734">Vi insert mode: `<Alt+h>`</span></span>
- <span data-ttu-id="e989f-735">Vi 명령 모드: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="e989f-735">Vi command mode: `<Alt+h>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="e989f-736">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="e989f-736">ViCommandMode</span></span>

<span data-ttu-id="e989f-737">Vi-Insert에서 현재 운영 모드를 Vi 명령으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-737">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="e989f-738">Vi 삽입 모드: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="e989f-738">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="e989f-739">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="e989f-739">ViDigitArgumentInChord</span></span>

<span data-ttu-id="e989f-740">Vi의 누르는 중 하나에서 다른 함수에 전달할 새 digit 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-740">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="e989f-741">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-741">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="e989f-742">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="e989f-742">ViEditVisually</span></span>

<span data-ttu-id="e989f-743">$Env: 편집기 또는 $env: 시각적 개체에 지정 된 텍스트 편집기에서 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-743">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="e989f-744">Emacs `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="e989f-744">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="e989f-745">Vi 명령 모드: `<v>`</span><span class="sxs-lookup"><span data-stu-id="e989f-745">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="e989f-746">ViExit</span><span class="sxs-lookup"><span data-stu-id="e989f-746">ViExit</span></span>

<span data-ttu-id="e989f-747">셸을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-747">Exits the shell.</span></span>

- <span data-ttu-id="e989f-748">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-748">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="e989f-749">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="e989f-749">ViInsertMode</span></span>

<span data-ttu-id="e989f-750">삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-750">Switch to Insert mode.</span></span>

- <span data-ttu-id="e989f-751">Vi 명령 모드: `<i>`</span><span class="sxs-lookup"><span data-stu-id="e989f-751">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="e989f-752">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="e989f-752">WhatIsKey</span></span>

<span data-ttu-id="e989f-753">키를 읽고 키가 바인딩된 정보를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-753">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="e989f-754">입력 `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e989f-754">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="e989f-755">Emacs `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e989f-755">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="e989f-756">선택 함수</span><span class="sxs-lookup"><span data-stu-id="e989f-756">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="e989f-757">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="e989f-757">ExchangePointAndMark</span></span>

<span data-ttu-id="e989f-758">커서는 표시 위치에 배치 되 고 표시는 커서의 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-758">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="e989f-759">Emacs `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="e989f-759">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="e989f-760">SelectAll</span><span class="sxs-lookup"><span data-stu-id="e989f-760">SelectAll</span></span>

<span data-ttu-id="e989f-761">전체 줄을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-761">Select the entire line.</span></span>

- <span data-ttu-id="e989f-762">입력 `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="e989f-762">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="e989f-763">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="e989f-763">SelectBackwardChar</span></span>

<span data-ttu-id="e989f-764">이전 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-764">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="e989f-765">입력 `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-765">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="e989f-766">Emacs `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-766">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="e989f-767">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="e989f-767">SelectBackwardsLine</span></span>

<span data-ttu-id="e989f-768">커서에서 줄의 시작 부분까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-768">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="e989f-769">입력 `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="e989f-769">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="e989f-770">Emacs `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="e989f-770">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="e989f-771">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="e989f-771">SelectBackwardWord</span></span>

<span data-ttu-id="e989f-772">이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-772">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="e989f-773">입력 `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-773">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="e989f-774">Emacs `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="e989f-774">Emacs: `<Alt+B>`</span></span>

### <a name="selectcommandargument"></a><span data-ttu-id="e989f-775">SelectCommandArgument</span><span class="sxs-lookup"><span data-stu-id="e989f-775">SelectCommandArgument</span></span>

<span data-ttu-id="e989f-776">명령 인수를 시각적으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-776">Make visual selection of the command arguments.</span></span> <span data-ttu-id="e989f-777">인수 선택은 스크립트 블록 내에서 범위가 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-777">Selection of arguments is scoped within a script block.</span></span> <span data-ttu-id="e989f-778">커서 위치에 따라 가장 안쪽의 스크립트 블록에서 쿼리의 가장 바깥쪽 많은 스크립트 블록으로 검색 하 고 스크립트 블록 범위에서 인수를 찾으면 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-778">Based on the cursor position, it searches from the innermost script block to the outmost script block, and stops when it finds any arguments in a script block scope.</span></span>

<span data-ttu-id="e989f-779">이 함수는 DigitArgument를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-779">This function honors DigitArgument.</span></span> <span data-ttu-id="e989f-780">긍정 또는 음수 인수 값을 현재 선택 된 인수에서 앞으로 또는 뒤로 오프셋 하거나, 인수를 선택 하지 않은 경우 현재 커서 위치에서 해당 값으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-780">It treats the positive or negative argument values as the forward or backward offsets from the currently selected argument, or from the current cursor position when no argument is selected.</span></span>

- <span data-ttu-id="e989f-781">입력 `<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="e989f-781">Cmd: `<Alt+a>`</span></span>
- <span data-ttu-id="e989f-782">Emacs `<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="e989f-782">Emacs: `<Alt+a>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="e989f-783">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="e989f-783">SelectForwardChar</span></span>

<span data-ttu-id="e989f-784">다음 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-784">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="e989f-785">입력 `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-785">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="e989f-786">Emacs `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-786">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="e989f-787">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="e989f-787">SelectForwardWord</span></span>

<span data-ttu-id="e989f-788">ForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-788">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="e989f-789">Emacs `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="e989f-789">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="e989f-790">줄을 select</span><span class="sxs-lookup"><span data-stu-id="e989f-790">SelectLine</span></span>

<span data-ttu-id="e989f-791">커서에서 줄의 끝까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-791">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="e989f-792">입력 `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="e989f-792">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="e989f-793">Emacs `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="e989f-793">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="e989f-794">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="e989f-794">SelectNextWord</span></span>

<span data-ttu-id="e989f-795">다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-795">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="e989f-796">입력 `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e989f-796">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="e989f-797">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="e989f-797">SelectShellBackwardWord</span></span>

<span data-ttu-id="e989f-798">ShellBackwardWord를 사용 하 여 이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-798">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="e989f-799">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-799">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="e989f-800">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="e989f-800">SelectShellForwardWord</span></span>

<span data-ttu-id="e989f-801">ShellForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-801">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="e989f-802">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-802">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="e989f-803">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="e989f-803">SelectShellNextWord</span></span>

<span data-ttu-id="e989f-804">ShellNextWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-804">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="e989f-805">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-805">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="e989f-806">SetMark</span><span class="sxs-lookup"><span data-stu-id="e989f-806">SetMark</span></span>

<span data-ttu-id="e989f-807">이후 편집 명령에 사용할 커서의 현재 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-807">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="e989f-808">Emacs `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="e989f-808">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="e989f-809">예측 IntelliSense 함수</span><span class="sxs-lookup"><span data-stu-id="e989f-809">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="e989f-810">이러한 함수를 사용 하려면 예측 IntelliSense를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-810">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="e989f-811">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="e989f-811">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="e989f-812">예측 IntelliSense에서 인라인 제안의 다음 단어를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-812">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="e989f-813">이 함수 <kbd></kbd> + 는 다음 명령을 실행 하 여 Ctrl<kbd>F</kbd> 를 사용 하 여 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-813">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="e989f-814">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="e989f-814">AcceptSuggestion</span></span>

<span data-ttu-id="e989f-815">커서가 현재 줄의 끝에 있을 때 <kbd>오른쪽 화살표</kbd> 를 눌러 예측 IntelliSense의 현재 인라인 제안을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-815">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="e989f-816">검색 함수</span><span class="sxs-lookup"><span data-stu-id="e989f-816">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="e989f-817">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="e989f-817">CharacterSearch</span></span>

<span data-ttu-id="e989f-818">문자를 읽고 그 다음 번에 해당 문자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-818">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="e989f-819">인수를 지정 하는 경우 n 번째 발생에 대해 앞으로 (음수 이면 뒤로) 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-819">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="e989f-820">입력 `<F3>`</span><span class="sxs-lookup"><span data-stu-id="e989f-820">Cmd: `<F3>`</span></span>
- <span data-ttu-id="e989f-821">Emacs `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="e989f-821">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="e989f-822">Vi 삽입 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="e989f-822">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="e989f-823">Vi 명령 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="e989f-823">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="e989f-824">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="e989f-824">CharacterSearchBackward</span></span>

<span data-ttu-id="e989f-825">문자를 읽은 다음 해당 문자의 다음 항목을 뒤로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-825">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="e989f-826">인수를 지정 하는 경우 n 번째 발생에 대해 뒤로 검색 하거나 음수 이면 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-826">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="e989f-827">입력 `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="e989f-827">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="e989f-828">Emacs `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="e989f-828">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="e989f-829">Vi 삽입 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="e989f-829">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="e989f-830">Vi 명령 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="e989f-830">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="e989f-831">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="e989f-831">RepeatLastCharSearch</span></span>

<span data-ttu-id="e989f-832">마지막으로 기록 된 문자 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-832">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="e989f-833">Vi 명령 모드: `<;>`</span><span class="sxs-lookup"><span data-stu-id="e989f-833">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="e989f-834">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="e989f-834">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="e989f-835">마지막으로 기록 된 문자 검색을 반대 방향으로 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-835">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="e989f-836">Vi 명령 모드: `<,>`</span><span class="sxs-lookup"><span data-stu-id="e989f-836">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="e989f-837">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="e989f-837">RepeatSearch</span></span>

<span data-ttu-id="e989f-838">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-838">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="e989f-839">Vi 명령 모드: `<n>`</span><span class="sxs-lookup"><span data-stu-id="e989f-839">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="e989f-840">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="e989f-840">RepeatSearchBackward</span></span>

<span data-ttu-id="e989f-841">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-841">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="e989f-842">Vi 명령 모드: `<N>`</span><span class="sxs-lookup"><span data-stu-id="e989f-842">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="e989f-843">SearchChar</span><span class="sxs-lookup"><span data-stu-id="e989f-843">SearchChar</span></span>

<span data-ttu-id="e989f-844">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-844">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="e989f-845">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-845">This is for 't' functionality.</span></span>

- <span data-ttu-id="e989f-846">Vi 명령 모드: `<f>`</span><span class="sxs-lookup"><span data-stu-id="e989f-846">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="e989f-847">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="e989f-847">SearchCharBackward</span></span>

<span data-ttu-id="e989f-848">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-848">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="e989f-849">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-849">This is for 'T' functionality.</span></span>

- <span data-ttu-id="e989f-850">Vi 명령 모드: `<F>`</span><span class="sxs-lookup"><span data-stu-id="e989f-850">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="e989f-851">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="e989f-851">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="e989f-852">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-852">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="e989f-853">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-853">This is for 'T' functionality.</span></span>

- <span data-ttu-id="e989f-854">Vi 명령 모드: `<T>`</span><span class="sxs-lookup"><span data-stu-id="e989f-854">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="e989f-855">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="e989f-855">SearchCharWithBackoff</span></span>

<span data-ttu-id="e989f-856">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-856">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="e989f-857">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-857">This is for 't' functionality.</span></span>

- <span data-ttu-id="e989f-858">Vi 명령 모드: `<t>`</span><span class="sxs-lookup"><span data-stu-id="e989f-858">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="e989f-859">SearchForward</span><span class="sxs-lookup"><span data-stu-id="e989f-859">SearchForward</span></span>

<span data-ttu-id="e989f-860">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-860">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="e989f-861">Vi 삽입 모드: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="e989f-861">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="e989f-862">Vi 명령 모드: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="e989f-862">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="e989f-863">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="e989f-863">Custom Key Bindings</span></span>

<span data-ttu-id="e989f-864">PSReadLine은 cmdlet을 사용 하 여 사용자 지정 키 바인딩을 지원 `Set-PSReadLineKeyHandler` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-864">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="e989f-865">대부분의 사용자 지정 키 바인딩은 위의 함수 중 하나를 호출 합니다. 예를 들면</span><span class="sxs-lookup"><span data-stu-id="e989f-865">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="e989f-866">ScriptBlock을 키에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-866">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="e989f-867">ScriptBlock은 필요한 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-867">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="e989f-868">몇 가지 유용한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-868">Some useful examples include</span></span>

- <span data-ttu-id="e989f-869">명령줄 편집</span><span class="sxs-lookup"><span data-stu-id="e989f-869">edit the command line</span></span>
- <span data-ttu-id="e989f-870">새 창 열기 (예: 도움말)</span><span class="sxs-lookup"><span data-stu-id="e989f-870">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="e989f-871">명령줄을 변경 하지 않고 디렉터리를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-871">change directories without changing the command line</span></span>

<span data-ttu-id="e989f-872">ScriptBlock은 두 개의 인수를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-872">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="e989f-873">`$key` -사용자 지정 바인딩을 트리거한 키 인 **[ConsoleKeyInfo]** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-873">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="e989f-874">동일한 ScriptBlock을 여러 키에 바인딩하고 키에 따라 다른 작업을 수행 해야 하는 경우 $key를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-874">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="e989f-875">많은 사용자 지정 바인딩에서이 인수를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-875">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="e989f-876">`$arg` -임의의 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-876">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="e989f-877">가장 자주 사용 되는 정수 인수는 사용자가 키 바인딩 DigitArgument에서 전달 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-877">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="e989f-878">바인딩에서 인수를 허용 하지 않는 경우에는이 인수를 무시 하는 것이 합리적입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-878">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="e989f-879">실행 하지 않고 기록에 명령줄을 추가 하는 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-879">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="e989f-880">이는 작업을 수행 하지 못했지만 이미 입력 한 명령줄을 다시 입력 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-880">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

<span data-ttu-id="e989f-881">PSReadLine 모듈 폴더에 설치 된 파일에서 더 많은 예제를 볼 수 있습니다 `SamplePSReadLineProfile.ps1` .</span><span class="sxs-lookup"><span data-stu-id="e989f-881">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="e989f-882">대부분의 키 바인딩은 일부 도우미 함수를 사용 하 여 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-882">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="e989f-883">이러한 Api는 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-883">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="e989f-884">사용자 지정 키 바인딩 지원 Api</span><span class="sxs-lookup"><span data-stu-id="e989f-884">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="e989f-885">다음 함수는 PSConsoleReadLine에서 공용 이지만 키에 직접 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-885">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="e989f-886">대부분은 사용자 지정 키 바인딩에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-886">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="e989f-887">실행 하지 않고 기록에 명령줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-887">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="e989f-888">Kill 링을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-888">Clear the kill-ring.</span></span>  <span data-ttu-id="e989f-889">이는 주로 테스트에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-889">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="e989f-890">시작에서 길이 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-890">Delete length characters from start.</span></span>  <span data-ttu-id="e989f-891">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-891">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="e989f-892">사용자 기본 설정에 따라 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-892">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="e989f-893">이러한 두 함수는 입력 버퍼의 현재 상태에 대 한 유용한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-893">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="e989f-894">첫 번째는 간단한 경우에 보다 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-894">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="e989f-895">두 번째는 바인딩에서 Ast를 사용 하 여 더 높은 작업을 수행 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-895">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="e989f-896">이러한 두 함수는에 사용 됩니다 `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="e989f-896">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="e989f-897">첫 번째는 모든 키 바인딩을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-897">The first is used to get all key bindings.</span></span> <span data-ttu-id="e989f-898">두 번째는 특정 키 바인딩을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-898">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="e989f-899">이 함수는 Get-PSReadLineOption에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-899">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="e989f-900">명령줄에 선택 항목이 없으면-1이 시작 및 길이 둘 다에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-900">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="e989f-901">명령줄에 선택 항목이 있는 경우 선택의 시작 및 길이가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-901">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="e989f-902">커서에 문자 또는 문자열을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-902">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="e989f-903">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-903">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="e989f-904">PSReadLine에 대 한 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-904">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="e989f-905">재귀를 지원 하지 않으므로 사용자 지정 키 바인딩에는 유용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-905">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="e989f-906">이 함수는 Remove-PSReadLineKeyHandler에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-906">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="e989f-907">일부 입력을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-907">Replace some of the input.</span></span> <span data-ttu-id="e989f-908">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-908">This operation supports undo/redo.</span></span> <span data-ttu-id="e989f-909">이는 실행 취소의 단일 작업으로 처리 되기 때문에 Delete 뒤에 Insert를 통해 선호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-909">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="e989f-910">커서를 지정 된 오프셋으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-910">Move the cursor to the given offset.</span></span> <span data-ttu-id="e989f-911">실행 취소를 위해 커서 이동이 추적 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-911">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="e989f-912">이 함수는 cmdlet Set-PSReadLineOption에서 사용 되는 도우미 메서드로, 설정을 일시적으로 변경 하려는 사용자 지정 키 바인딩에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-912">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="e989f-913">이 도우미 메서드는 DigitArgument을 준수 하는 사용자 지정 바인딩에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-913">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="e989f-914">일반적인 호출은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-914">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="e989f-915">메모</span><span class="sxs-lookup"><span data-stu-id="e989f-915">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="e989f-916">명령 기록</span><span class="sxs-lookup"><span data-stu-id="e989f-916">Command History</span></span>

<span data-ttu-id="e989f-917">PSReadLine은 명령줄에서 입력 한 모든 명령 및 데이터를 포함 하는 기록 파일을 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-917">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="e989f-918">여기에는 암호를 비롯 한 중요 한 데이터가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-918">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="e989f-919">예를 들어 cmdlet을 사용 하는 경우 `ConvertTo-SecureString` 암호는 일반 텍스트로 기록 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-919">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="e989f-920">기록 파일은 라는 파일입니다 `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="e989f-920">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="e989f-921">Windows 시스템에서 기록 파일은에 저장 됩니다 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="e989f-921">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="e989f-922">Windows가 아닌 시스템에서 기록 파일은 또는에 저장 됩니다 `$env:XDG_DATA_HOME/powershell/PSReadLine` `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="e989f-922">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="e989f-923">PSReadLine에 영향을 주는 & 피드백</span><span class="sxs-lookup"><span data-stu-id="e989f-923">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="e989f-924">GitHub의 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="e989f-924">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="e989f-925">GitHub 페이지에서 끌어오기 요청을 제출 하거나 피드백을 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-925">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="e989f-926">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e989f-926">See Also</span></span>

<span data-ttu-id="e989f-927">PSReadLine은 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 라이브러리의 영향을 많이 받습니다.</span><span class="sxs-lookup"><span data-stu-id="e989f-927">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
