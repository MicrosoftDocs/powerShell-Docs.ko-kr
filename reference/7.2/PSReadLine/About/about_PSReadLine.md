---
description: PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSReadLine 정보
ms.openlocfilehash: b0c5950b2af6a866d0ffcfdd6ce7ad92a1763778
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500215"
---
# <a name="psreadline"></a><span data-ttu-id="f86f1-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="f86f1-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="f86f1-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="f86f1-105">Short Description</span></span>

<span data-ttu-id="f86f1-106">PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="f86f1-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="f86f1-107">Long Description</span></span>

<span data-ttu-id="f86f1-108">PSReadLine 2.2은 PowerShell 콘솔에 대 한 강력한 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="f86f1-109">이 콘솔은 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-109">It provides:</span></span>

- <span data-ttu-id="f86f1-110">명령줄의 구문 색 지정</span><span class="sxs-lookup"><span data-stu-id="f86f1-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="f86f1-111">구문 오류를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="f86f1-112">더 나은 여러 줄 환경 (편집 및 기록 모두)</span><span class="sxs-lookup"><span data-stu-id="f86f1-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="f86f1-113">사용자 지정 가능한 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="f86f1-113">Customizable key bindings</span></span>
- <span data-ttu-id="f86f1-114">Cmd 및 Emacs 모드</span><span class="sxs-lookup"><span data-stu-id="f86f1-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="f86f1-115">많은 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="f86f1-115">Many configuration options</span></span>
- <span data-ttu-id="f86f1-116">Bash 스타일 완성 (Cmd 모드에서는 선택 사항, Emacs 모드에서는 기본값)</span><span class="sxs-lookup"><span data-stu-id="f86f1-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="f86f1-117">Emacs yank/kill</span><span class="sxs-lookup"><span data-stu-id="f86f1-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="f86f1-118">PowerShell 토큰 기반 "word" 이동 및 중지</span><span class="sxs-lookup"><span data-stu-id="f86f1-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="f86f1-119">예측 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f86f1-119">Predictive IntelliSense</span></span>

<span data-ttu-id="f86f1-120">PSReadLine 2.2.0는 두 가지 새로운 예측 IntelliSense 기능을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="f86f1-121">새를 선택할 수 있도록 **PredictionViewStyle** 매개 변수를 추가 했습니다 `ListView` .</span><span class="sxs-lookup"><span data-stu-id="f86f1-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="f86f1-122">PSReadLine을 `CommandPrediction` PS 7.1에 도입 된 api에 연결 하 여 사용자가 사용자 지정 원본에서 제안을 렌더링할 수 있는 예측 모듈을 가져올 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="f86f1-123">PSReadLine에는 PowerShell 3.0 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="f86f1-124">PSReadLine은 기본 콘솔 호스트, Visual Studio Code 및 창 터미널에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="f86f1-125">PowerShell ISE에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="f86f1-126">PSReadLine 2.2.0는 PowerShell 7.2과 함께 제공 되며, 지원 되는 모든 버전의 PowerShell에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="f86f1-127">PowerShell 갤러리에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="f86f1-128">지원 되는 버전의 PowerShell에서 PSReadLine 2.2.0을 설치 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="f86f1-129">PowerShell 7.0부터 PowerShell은 화면 판독기 프로그램이 검색 된 경우 Windows에서 PSReadLine 자동 로드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="f86f1-130">현재 PSReadLine은 화면 판독기에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="f86f1-131">Windows에서 PowerShell 7.0의 기본 렌더링 및 형식이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="f86f1-132">필요한 경우 모듈을 수동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="f86f1-133">예측 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f86f1-133">Predictive IntelliSense</span></span>

<span data-ttu-id="f86f1-134">예측 IntelliSense는 사용자가 명령을 성공적으로 완료 하는 데 도움이 되는 탭 완성 이라는 개념에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="f86f1-135">사용자가 사용자 기록과 추가 도메인 특정 플러그인의 일치 하는 예측에 따라 전체 명령을 검색, 편집 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="f86f1-136">예측 IntelliSense 사용</span><span class="sxs-lookup"><span data-stu-id="f86f1-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="f86f1-137">예측 IntelliSense는 기본적으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="f86f1-138">예측을 사용 하도록 설정 하려면 다음 명령을 실행 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="f86f1-139">**PredictionSource** 매개 변수는 도메인 특정 요구 사항 및 사용자 지정 요구 사항에 대 한 플러그 인도 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="f86f1-140">예측 IntelliSense를 사용 하지 않도록 설정 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="f86f1-141">다음 함수는 **[PSConsoleReadLine]** 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="f86f1-142">기본 편집 함수</span><span class="sxs-lookup"><span data-stu-id="f86f1-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="f86f1-143">중단</span><span class="sxs-lookup"><span data-stu-id="f86f1-143">Abort</span></span>

<span data-ttu-id="f86f1-144">현재 작업을 중단 합니다 (예: 증분 기록 검색).</span><span class="sxs-lookup"><span data-stu-id="f86f1-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="f86f1-145">Emacs `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="f86f1-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="f86f1-146">AcceptAndGetNext</span></span>

<span data-ttu-id="f86f1-147">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-147">Attempt to execute the current input.</span></span> <span data-ttu-id="f86f1-148">실행 될 수 있는 경우 (예: AcceptLine) 다음에 ReadLine이 호출 될 때 기록에서 다음 항목을 회수 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="f86f1-149">Emacs `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="f86f1-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-150">AcceptLine</span></span>

<span data-ttu-id="f86f1-151">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-151">Attempt to execute the current input.</span></span> <span data-ttu-id="f86f1-152">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="f86f1-153">입력 `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="f86f1-154">Emacs `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="f86f1-155">Vi 삽입 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="f86f1-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-156">AddLine</span></span>

<span data-ttu-id="f86f1-157">연속 프롬프트가 다음 줄에 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="f86f1-158">이는 한 줄이 자체적으로 전체 입력 인 경우에도 여러 줄 입력을 단일 명령으로 입력 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="f86f1-159">입력 `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="f86f1-160">Emacs `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="f86f1-161">Vi 삽입 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="f86f1-162">Vi 명령 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="f86f1-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-163">BackwardDeleteChar</span></span>

<span data-ttu-id="f86f1-164">커서 앞에 있는 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="f86f1-165">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="f86f1-166">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="f86f1-167">Vi 삽입 모드: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="f86f1-168">Vi 명령 모드: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="f86f1-169">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-169">BackwardDeleteLine</span></span>

<span data-ttu-id="f86f1-170">Like BackwardKillLine-점에서 줄의 시작 부분으로 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-170">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="f86f1-171">입력 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="f86f1-172">Vi 삽입 모드: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="f86f1-173">Vi 명령 모드: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="f86f1-174">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-174">BackwardDeleteWord</span></span>

<span data-ttu-id="f86f1-175">이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-175">Deletes the previous word.</span></span>

- <span data-ttu-id="f86f1-176">Vi 명령 모드: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-176">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="f86f1-177">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-177">BackwardKillLine</span></span>

<span data-ttu-id="f86f1-178">커서에 대 한 입력의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-178">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="f86f1-179">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-179">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f86f1-180">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-180">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="f86f1-181">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-181">BackwardKillWord</span></span>

<span data-ttu-id="f86f1-182">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-182">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="f86f1-183">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-183">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="f86f1-184">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-184">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f86f1-185">Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-185">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="f86f1-186">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-186">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="f86f1-187">Vi 삽입 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-187">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="f86f1-188">Vi 명령 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-188">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="f86f1-189">CancelLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-189">CancelLine</span></span>

<span data-ttu-id="f86f1-190">화면에 입력을 그대로 두고 현재 입력을 취소 합니다. 그러나 프롬프트가 다시 계산 되도록 다시 호스트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-190">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="f86f1-191">Vi 삽입 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-191">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="f86f1-192">Vi 명령 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-192">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="f86f1-193">복사</span><span class="sxs-lookup"><span data-stu-id="f86f1-193">Copy</span></span>

<span data-ttu-id="f86f1-194">선택한 영역을 시스템 클립보드에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-194">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="f86f1-195">선택 된 지역이 없으면 전체 줄을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-195">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="f86f1-196">입력 `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-196">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="f86f1-197">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-197">CopyOrCancelLine</span></span>

<span data-ttu-id="f86f1-198">텍스트를 선택한 경우 클립보드로 복사 하 고, 그렇지 않으면 줄을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-198">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="f86f1-199">입력 `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-199">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="f86f1-200">Emacs `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-200">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="f86f1-201">잘라내기</span><span class="sxs-lookup"><span data-stu-id="f86f1-201">Cut</span></span>

<span data-ttu-id="f86f1-202">삭제 된 텍스트를 시스템 클립보드에 배치 하는 선택한 영역을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-202">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="f86f1-203">입력 `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-203">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="f86f1-204">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-204">DeleteChar</span></span>

<span data-ttu-id="f86f1-205">커서 아래의 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-205">Delete the character under the cursor.</span></span>

- <span data-ttu-id="f86f1-206">입력 `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-206">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="f86f1-207">Emacs `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-207">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="f86f1-208">Vi 삽입 모드: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-208">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="f86f1-209">Vi 명령 모드: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-209">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="f86f1-210">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="f86f1-210">DeleteCharOrExit</span></span>

<span data-ttu-id="f86f1-211">커서 아래의 문자를 삭제 하거나, 줄이 비어 있으면 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-211">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="f86f1-212">Emacs `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-212">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="f86f1-213">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="f86f1-213">DeleteEndOfBuffer</span></span>

<span data-ttu-id="f86f1-214">여러 줄 버퍼의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-214">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="f86f1-215">Vi 명령 모드: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-215">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="f86f1-216">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-216">DeleteEndOfWord</span></span>

<span data-ttu-id="f86f1-217">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-217">Delete to the end of the word.</span></span>

- <span data-ttu-id="f86f1-218">Vi 명령 모드: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-218">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="f86f1-219">Deleteline.invoke</span><span class="sxs-lookup"><span data-stu-id="f86f1-219">DeleteLine</span></span>

<span data-ttu-id="f86f1-220">여러 줄 버퍼의 현재 논리 줄을 삭제 하 고 실행 취소를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-220">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="f86f1-221">Vi 명령 모드: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-221">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="f86f1-222">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="f86f1-222">DeletePreviousLines</span></span>

<span data-ttu-id="f86f1-223">여러 줄 버퍼에서 요청 된 이전 논리 줄과 현재 논리 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-223">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="f86f1-224">Vi 명령 모드: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-224">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="f86f1-225">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="f86f1-225">DeleteRelativeLines</span></span>

<span data-ttu-id="f86f1-226">버퍼의 시작 부분에서 여러 줄 버퍼의 현재 논리 줄까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-226">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="f86f1-227">대부분의 Vi 명령으로 `<d,g,g>` 명령 앞에는 절대 줄 번호를 지정 하는 숫자 인수를 추가할 수 있습니다 .이 숫자는 현재 줄 번호와 함께 삭제 될 줄의 범위를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-227">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="f86f1-228">지정 하지 않으면 숫자 인수는 기본적으로 1로 설정 되며이는 여러 줄 버퍼의 첫 번째 논리 줄을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-228">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="f86f1-229">여러 줄에서 삭제 되는 실제 줄 수는 현재 논리 줄 번호와 지정 된 숫자 인수 간의 차이로 계산 되므로 음수가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-229">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="f86f1-230">따라서 메서드 이름의 _상대_ 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-230">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="f86f1-231">Vi 명령 모드: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-231">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="f86f1-232">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="f86f1-232">DeleteNextLines</span></span>

<span data-ttu-id="f86f1-233">여러 줄 버퍼에서 현재 논리 줄 및 요청 된 다음 논리 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-233">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="f86f1-234">Vi 명령 모드: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-234">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="f86f1-235">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-235">DeleteLineToFirstChar</span></span>

<span data-ttu-id="f86f1-236">여러 줄 버퍼에서 현재 논리 줄의 비어 있지 않은 첫 번째 문자에서 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-236">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="f86f1-237">Vi 명령 모드: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-237">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="f86f1-238">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="f86f1-238">DeleteToEnd</span></span>

<span data-ttu-id="f86f1-239">줄의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-239">Delete to the end of the line.</span></span>

- <span data-ttu-id="f86f1-240">Vi 명령 모드: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-240">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="f86f1-241">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-241">DeleteWord</span></span>

<span data-ttu-id="f86f1-242">다음 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-242">Delete the next word.</span></span>

- <span data-ttu-id="f86f1-243">Vi 명령 모드: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-243">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="f86f1-244">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-244">ForwardDeleteLine</span></span>

<span data-ttu-id="f86f1-245">Like ForwardKillLine-포인트에서 줄 끝 까지의 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-245">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="f86f1-246">입력 `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-246">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="f86f1-247">Vi 삽입 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-247">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="f86f1-248">Vi 명령 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-248">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="f86f1-249">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="f86f1-249">InsertLineAbove</span></span>

<span data-ttu-id="f86f1-250">현재 줄에 커서가 있는 위치에 관계 없이 새 빈 줄이 현재 줄 위에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-250">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="f86f1-251">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-251">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="f86f1-252">입력 `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-252">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="f86f1-253">Insertlinenea</span><span class="sxs-lookup"><span data-stu-id="f86f1-253">InsertLineBelow</span></span>

<span data-ttu-id="f86f1-254">커서가 현재 줄에 있는지 여부에 관계 없이 현재 줄 아래에 빈 줄이 새로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-254">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="f86f1-255">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-255">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="f86f1-256">입력 `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-256">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="f86f1-257">InvertCase</span><span class="sxs-lookup"><span data-stu-id="f86f1-257">InvertCase</span></span>

<span data-ttu-id="f86f1-258">현재 문자의 대/소문자를 반전 하 고 다음으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-258">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="f86f1-259">Vi 명령 모드: `<~>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-259">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="f86f1-260">KillLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-260">KillLine</span></span>

<span data-ttu-id="f86f1-261">입력의 끝 부분까지 커서에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-261">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="f86f1-262">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-262">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f86f1-263">Emacs `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-263">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="f86f1-264">KillRegion</span><span class="sxs-lookup"><span data-stu-id="f86f1-264">KillRegion</span></span>

<span data-ttu-id="f86f1-265">커서와 표시 사이에 있는 텍스트를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-265">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="f86f1-266">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-266">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="f86f1-267">KillWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-267">KillWord</span></span>

<span data-ttu-id="f86f1-268">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-268">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="f86f1-269">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-269">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="f86f1-270">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-270">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f86f1-271">Cmd: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-271">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="f86f1-272">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-272">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="f86f1-273">Vi 삽입 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-273">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="f86f1-274">Vi 명령 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-274">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="f86f1-275">붙여넣기</span><span class="sxs-lookup"><span data-stu-id="f86f1-275">Paste</span></span>

<span data-ttu-id="f86f1-276">시스템 클립보드에서 텍스트를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-276">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="f86f1-277">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-277">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="f86f1-278">Vi 삽입 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-278">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="f86f1-279">Vi 명령 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-279">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f86f1-280">**Paste** 함수를 사용 하는 경우 클립보드 버퍼의 전체 내용이 psreadline의 입력 버퍼에 붙여넣어집니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-280">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="f86f1-281">그런 다음 입력 버퍼가 PowerShell 파서로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-281">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="f86f1-282">콘솔 응용 프로그램의 **마우스 오른쪽 단추 클릭** 붙여넣기 메서드를 사용 하 여 붙여넣은 입력은 입력 버퍼에 한 번에 한 문자씩 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-282">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="f86f1-283">입력 버퍼는 줄 바꿈 문자가 복사 될 때 파서에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-283">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="f86f1-284">따라서 입력은 한 번에 한 줄씩 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-284">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="f86f1-285">붙여넣기 메서드 간의 차이점으로 인해 실행 동작이 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-285">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="f86f1-286">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="f86f1-286">PasteAfter</span></span>

<span data-ttu-id="f86f1-287">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 뒤에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-287">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="f86f1-288">Vi 명령 모드: `<p>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-288">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="f86f1-289">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="f86f1-289">PasteBefore</span></span>

<span data-ttu-id="f86f1-290">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 앞에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-290">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="f86f1-291">Vi 명령 모드: `<P>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-291">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="f86f1-292">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="f86f1-292">PrependAndAccept</span></span>

<span data-ttu-id="f86f1-293">' # ' 앞에를 추가 하 고 줄을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-293">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="f86f1-294">Vi 명령 모드: `<#>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-294">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="f86f1-295">다시 실행</span><span class="sxs-lookup"><span data-stu-id="f86f1-295">Redo</span></span>

<span data-ttu-id="f86f1-296">실행 취소를 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-296">Undo an undo.</span></span>

- <span data-ttu-id="f86f1-297">입력 `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-297">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="f86f1-298">Vi 삽입 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-298">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="f86f1-299">Vi 명령 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-299">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="f86f1-300">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="f86f1-300">RepeatLastCommand</span></span>

<span data-ttu-id="f86f1-301">마지막 텍스트 수정 작업을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-301">Repeat the last text modification.</span></span>

- <span data-ttu-id="f86f1-302">Vi 명령 모드: `<.>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-302">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="f86f1-303">RevertLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-303">RevertLine</span></span>

<span data-ttu-id="f86f1-304">모든 입력을 현재 입력으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-304">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="f86f1-305">입력 `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-305">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="f86f1-306">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-306">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="f86f1-307">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-307">ShellBackwardKillWord</span></span>

<span data-ttu-id="f86f1-308">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-308">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="f86f1-309">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-309">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="f86f1-310">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-310">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="f86f1-311">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-311">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="f86f1-312">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-312">ShellKillWord</span></span>

<span data-ttu-id="f86f1-313">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-313">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="f86f1-314">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-314">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="f86f1-315">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-315">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="f86f1-316">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-316">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="f86f1-317">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="f86f1-317">SwapCharacters</span></span>

<span data-ttu-id="f86f1-318">현재 문자와 그 앞의 문자를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-318">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="f86f1-319">Emacs `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-319">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="f86f1-320">Vi 삽입 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-320">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="f86f1-321">Vi 명령 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-321">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="f86f1-322">실행 취소</span><span class="sxs-lookup"><span data-stu-id="f86f1-322">Undo</span></span>

<span data-ttu-id="f86f1-323">이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-323">Undo a previous edit.</span></span>

- <span data-ttu-id="f86f1-324">입력 `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-324">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="f86f1-325">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-325">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="f86f1-326">Vi 삽입 모드: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-326">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="f86f1-327">Vi 명령 모드: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-327">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="f86f1-328">모두를</span><span class="sxs-lookup"><span data-stu-id="f86f1-328">UndoAll</span></span>

<span data-ttu-id="f86f1-329">줄의 모든 이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-329">Undo all previous edits for line.</span></span>

- <span data-ttu-id="f86f1-330">Vi 명령 모드: `<U>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-330">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="f86f1-331">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="f86f1-331">UnixWordRubout</span></span>

<span data-ttu-id="f86f1-332">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-332">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="f86f1-333">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-333">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="f86f1-334">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-334">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f86f1-335">Emacs `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-335">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="f86f1-336">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-336">ValidateAndAcceptLine</span></span>

<span data-ttu-id="f86f1-337">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-337">Attempt to execute the current input.</span></span> <span data-ttu-id="f86f1-338">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-338">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="f86f1-339">Emacs `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-339">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="f86f1-340">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-340">ViAcceptLine</span></span>

<span data-ttu-id="f86f1-341">줄을 적용 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-341">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="f86f1-342">Vi 명령 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-342">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="f86f1-343">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="f86f1-343">ViAcceptLineOrExit</span></span>

<span data-ttu-id="f86f1-344">Emacs 모드에서 DeleteCharOrExit와 비슷하지만 문자를 삭제 하는 대신 줄을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-344">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="f86f1-345">Vi 삽입 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-345">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="f86f1-346">Vi 명령 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-346">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="f86f1-347">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-347">ViAppendLine</span></span>

<span data-ttu-id="f86f1-348">현재 줄 아래에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-348">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="f86f1-349">Vi 명령 모드: `<o>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-349">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="f86f1-350">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-350">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="f86f1-351">공백을 단어 구분 기호로 사용 하 여 이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-351">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="f86f1-352">Vi 명령 모드: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-352">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="f86f1-353">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-353">ViBackwardGlob</span></span>

<span data-ttu-id="f86f1-354">공백을 구분 기호로 사용 하 여 커서를 이전 단어의 시작 부분으로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-354">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="f86f1-355">Vi 명령 모드: `<B>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-355">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="f86f1-356">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="f86f1-356">ViDeleteBrace</span></span>

<span data-ttu-id="f86f1-357">괄호를 포함 하 여 일치 하는 중괄호, 괄호 또는 대괄호를 찾아 내에서 모든 내용을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-357">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="f86f1-358">Vi 명령 모드: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-358">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="f86f1-359">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-359">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="f86f1-360">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-360">Delete to the end of the word.</span></span>

- <span data-ttu-id="f86f1-361">Vi 명령 모드: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-361">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="f86f1-362">Videletlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-362">ViDeleteGlob</span></span>

<span data-ttu-id="f86f1-363">다음 glob (공백으로 구분 된 단어)를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-363">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="f86f1-364">Vi 명령 모드: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-364">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="f86f1-365">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-365">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="f86f1-366">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-366">Deletes until given character.</span></span>

- <span data-ttu-id="f86f1-367">Vi 명령 모드: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-367">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="f86f1-368">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="f86f1-368">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="f86f1-369">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-369">Deletes until given character.</span></span>

- <span data-ttu-id="f86f1-370">Vi 명령 모드: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-370">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="f86f1-371">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-371">ViDeleteToChar</span></span>

<span data-ttu-id="f86f1-372">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-372">Deletes until given character.</span></span>

- <span data-ttu-id="f86f1-373">Vi 명령 모드: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-373">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="f86f1-374">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="f86f1-374">ViDeleteToCharBackward</span></span>

<span data-ttu-id="f86f1-375">지정 된 문자까지 뒤로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-375">Deletes backwards until given character.</span></span>

- <span data-ttu-id="f86f1-376">Vi 명령 모드: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-376">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="f86f1-377">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="f86f1-377">ViInsertAtBegining</span></span>

<span data-ttu-id="f86f1-378">삽입 모드로 전환 하 고 줄의 시작 부분에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-378">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="f86f1-379">Vi 명령 모드: `<I>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-379">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="f86f1-380">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="f86f1-380">ViInsertAtEnd</span></span>

<span data-ttu-id="f86f1-381">삽입 모드로 전환 하 고 줄의 끝에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-381">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="f86f1-382">Vi 명령 모드: `<A>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-382">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="f86f1-383">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-383">ViInsertLine</span></span>

<span data-ttu-id="f86f1-384">현재 줄 위에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-384">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="f86f1-385">Vi 명령 모드: `<O>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-385">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="f86f1-386">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="f86f1-386">ViInsertWithAppend</span></span>

<span data-ttu-id="f86f1-387">현재 줄 위치에서 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-387">Append from the current line position.</span></span>

- <span data-ttu-id="f86f1-388">Vi 명령 모드: `<a>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-388">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="f86f1-389">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="f86f1-389">ViInsertWithDelete</span></span>

<span data-ttu-id="f86f1-390">현재 문자를 삭제 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-390">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="f86f1-391">Vi 명령 모드: `<s>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-391">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="f86f1-392">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="f86f1-392">ViJoinLines</span></span>

<span data-ttu-id="f86f1-393">현재 줄과 다음 줄을 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-393">Joins the current line and the next line.</span></span>

- <span data-ttu-id="f86f1-394">Vi 명령 모드: `<J>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-394">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="f86f1-395">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-395">ViReplaceLine</span></span>

<span data-ttu-id="f86f1-396">전체 명령줄을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-396">Erase the entire command line.</span></span>

- <span data-ttu-id="f86f1-397">Vi 명령 모드: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-397">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="f86f1-398">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-398">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="f86f1-399">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-399">Replaces until given character.</span></span>

- <span data-ttu-id="f86f1-400">Vi 명령 모드: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-400">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="f86f1-401">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="f86f1-401">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="f86f1-402">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-402">Replaces until given character.</span></span>

- <span data-ttu-id="f86f1-403">Vi 명령 모드: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-403">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="f86f1-404">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-404">ViReplaceToChar</span></span>

<span data-ttu-id="f86f1-405">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-405">Deletes until given character.</span></span>

- <span data-ttu-id="f86f1-406">Vi 명령 모드: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-406">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="f86f1-407">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="f86f1-407">ViReplaceToCharBackward</span></span>

<span data-ttu-id="f86f1-408">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-408">Replaces until given character.</span></span>

- <span data-ttu-id="f86f1-409">Vi 명령 모드: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-409">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="f86f1-410">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-410">ViYankBeginningOfLine</span></span>

<span data-ttu-id="f86f1-411">버퍼의 시작 부분에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="f86f1-411">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="f86f1-412">Vi 명령 모드: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-412">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="f86f1-413">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-413">ViYankEndOfGlob</span></span>

<span data-ttu-id="f86f1-414">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-414">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="f86f1-415">Vi 명령 모드: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-415">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="f86f1-416">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-416">ViYankEndOfWord</span></span>

<span data-ttu-id="f86f1-417">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-417">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="f86f1-418">Vi 명령 모드: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-418">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="f86f1-419">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="f86f1-419">ViYankLeft</span></span>

<span data-ttu-id="f86f1-420">커서의 왼쪽에 문자를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-420">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="f86f1-421">Vi 명령 모드: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-421">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="f86f1-422">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-422">ViYankLine</span></span>

<span data-ttu-id="f86f1-423">전체 버퍼를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-423">Yank the entire buffer.</span></span>

- <span data-ttu-id="f86f1-424">Vi 명령 모드: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-424">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="f86f1-425">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-425">ViYankNextGlob</span></span>

<span data-ttu-id="f86f1-426">커서에서 다음 단어의 시작 부분으로 Yank.</span><span class="sxs-lookup"><span data-stu-id="f86f1-426">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="f86f1-427">Vi 명령 모드: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-427">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="f86f1-428">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-428">ViYankNextWord</span></span>

<span data-ttu-id="f86f1-429">커서 뒤의 단어를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-429">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="f86f1-430">Vi 명령 모드: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-430">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="f86f1-431">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="f86f1-431">ViYankPercent</span></span>

<span data-ttu-id="f86f1-432">짝이 되는 중괄호에서 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-432">Yank to/from matching brace.</span></span>

- <span data-ttu-id="f86f1-433">Vi 명령 모드: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-433">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="f86f1-434">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-434">ViYankPreviousGlob</span></span>

<span data-ttu-id="f86f1-435">단어의 시작부터 커서까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-435">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="f86f1-436">Vi 명령 모드: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-436">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="f86f1-437">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-437">ViYankPreviousWord</span></span>

<span data-ttu-id="f86f1-438">커서 앞에 단어를 Yank.</span><span class="sxs-lookup"><span data-stu-id="f86f1-438">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="f86f1-439">Vi 명령 모드: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-439">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="f86f1-440">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="f86f1-440">ViYankRight</span></span>

<span data-ttu-id="f86f1-441">커서 오른쪽의 및 아래에 Yank 문자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-441">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="f86f1-442">Vi 명령 모드: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-442">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="f86f1-443">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-443">ViYankToEndOfLine</span></span>

<span data-ttu-id="f86f1-444">커서에서 버퍼 끝까지 Yank.</span><span class="sxs-lookup"><span data-stu-id="f86f1-444">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="f86f1-445">Vi 명령 모드: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-445">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="f86f1-446">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-446">ViYankToFirstChar</span></span>

<span data-ttu-id="f86f1-447">공백이 아닌 첫 번째 문자에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="f86f1-447">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="f86f1-448">Vi 명령 모드: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-448">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="f86f1-449">Yank</span><span class="sxs-lookup"><span data-stu-id="f86f1-449">Yank</span></span>

<span data-ttu-id="f86f1-450">가장 최근에 종료 된 텍스트를 입력에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-450">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="f86f1-451">Emacs `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-451">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="f86f1-452">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="f86f1-452">YankLastArg</span></span>

<span data-ttu-id="f86f1-453">이전 기록 줄에서 마지막 인수를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-453">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="f86f1-454">인수를 사용 하면 처음 호출 될 때 YankNthArg 처럼 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-454">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="f86f1-455">여러 번 호출 된 경우에는 기록 및 인수에서 방향을 설정 합니다. (음수는 방향을 반대로 바꿉니다.)</span><span class="sxs-lookup"><span data-stu-id="f86f1-455">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="f86f1-456">입력 `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-456">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="f86f1-457">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-457">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="f86f1-458">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="f86f1-458">YankNthArg</span></span>

<span data-ttu-id="f86f1-459">이전 기록 줄에서 첫 번째 인수 (명령 뒤)를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-459">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="f86f1-460">인수를 사용 하는 경우 n 번째 인수 (0부터 시작)를 yank. 인수가 음수 이면 마지막 인수부터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-460">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="f86f1-461">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-461">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="f86f1-462">YankPop</span><span class="sxs-lookup"><span data-stu-id="f86f1-462">YankPop</span></span>

<span data-ttu-id="f86f1-463">이전 작업이 Yank 또는 YankPop 인 경우 이전 빼낼 텍스트를 kill 링에서 다음에 종료 된 텍스트로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-463">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="f86f1-464">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-464">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="f86f1-465">커서 이동 함수</span><span class="sxs-lookup"><span data-stu-id="f86f1-465">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="f86f1-466">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-466">BackwardChar</span></span>

<span data-ttu-id="f86f1-467">커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-467">Move the cursor one character to the left.</span></span> <span data-ttu-id="f86f1-468">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-468">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="f86f1-469">입력 `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-469">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="f86f1-470">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-470">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="f86f1-471">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-471">BackwardWord</span></span>

<span data-ttu-id="f86f1-472">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-472">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="f86f1-473">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-473">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f86f1-474">입력 `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-474">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="f86f1-475">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-475">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="f86f1-476">Vi 삽입 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-476">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="f86f1-477">Vi 명령 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-477">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="f86f1-478">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-478">BeginningOfLine</span></span>

<span data-ttu-id="f86f1-479">입력에 여러 줄이 있는 경우 현재 줄의 시작 부분으로 이동 하거나 이미 줄의 시작 부분에 있는 경우 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-479">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="f86f1-480">입력에 한 줄이 있으면 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-480">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="f86f1-481">입력 `<Home>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-481">Cmd: `<Home>`</span></span>
- <span data-ttu-id="f86f1-482">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-482">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="f86f1-483">Vi 삽입 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-483">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="f86f1-484">Vi 명령 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-484">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="f86f1-485">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-485">EndOfLine</span></span>

<span data-ttu-id="f86f1-486">입력에 여러 줄이 있는 경우 현재 줄의 끝으로 이동 하거나 줄의 끝에 있는 경우 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-486">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="f86f1-487">입력에 한 줄이 있으면 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-487">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="f86f1-488">입력 `<End>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-488">Cmd: `<End>`</span></span>
- <span data-ttu-id="f86f1-489">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-489">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="f86f1-490">Vi 삽입 모드: `<End>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-490">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="f86f1-491">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-491">ForwardChar</span></span>

<span data-ttu-id="f86f1-492">커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-492">Move the cursor one character to the right.</span></span> <span data-ttu-id="f86f1-493">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-493">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="f86f1-494">입력 `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-494">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="f86f1-495">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-495">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="f86f1-496">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-496">ForwardWord</span></span>

<span data-ttu-id="f86f1-497">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-497">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="f86f1-498">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-498">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f86f1-499">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-499">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="f86f1-500">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="f86f1-500">GotoBrace</span></span>

<span data-ttu-id="f86f1-501">짝이 되는 중괄호, 괄호 또는 대괄호로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-501">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="f86f1-502">입력 `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-502">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="f86f1-503">Vi 삽입 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-503">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="f86f1-504">Vi 명령 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-504">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="f86f1-505">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="f86f1-505">GotoColumn</span></span>

<span data-ttu-id="f86f1-506">Arg로 표시 된 열로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-506">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="f86f1-507">Vi 명령 모드: `<|>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-507">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="f86f1-508">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-508">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="f86f1-509">줄에서 비어 있지 않은 첫 번째 문자로 커서를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-509">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="f86f1-510">Vi 명령 모드: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-510">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="f86f1-511">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-511">MoveToEndOfLine</span></span>

<span data-ttu-id="f86f1-512">커서를 입력 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-512">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="f86f1-513">Vi 명령 모드: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-513">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="f86f1-514">NextLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-514">NextLine</span></span>

<span data-ttu-id="f86f1-515">커서를 다음 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-515">Move the cursor to the next line.</span></span>

- <span data-ttu-id="f86f1-516">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-516">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="f86f1-517">NextWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-517">NextWord</span></span>

<span data-ttu-id="f86f1-518">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="f86f1-519">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-519">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f86f1-520">입력 `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-520">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="f86f1-521">Vi 삽입 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-521">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="f86f1-522">Vi 명령 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-522">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="f86f1-523">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="f86f1-523">NextWordEnd</span></span>

<span data-ttu-id="f86f1-524">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-524">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="f86f1-525">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-525">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f86f1-526">Vi 명령 모드: `<e>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-526">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="f86f1-527">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-527">PreviousLine</span></span>

<span data-ttu-id="f86f1-528">커서를 이전 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-528">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="f86f1-529">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-529">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="f86f1-530">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-530">ShellBackwardWord</span></span>

<span data-ttu-id="f86f1-531">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="f86f1-532">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-532">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="f86f1-533">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-533">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="f86f1-534">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-534">ShellForwardWord</span></span>

<span data-ttu-id="f86f1-535">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-535">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="f86f1-536">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-536">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="f86f1-537">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-537">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="f86f1-538">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-538">ShellNextWord</span></span>

<span data-ttu-id="f86f1-539">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-539">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="f86f1-540">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-540">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="f86f1-541">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-541">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="f86f1-542">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-542">ViBackwardChar</span></span>

<span data-ttu-id="f86f1-543">Vi 편집 모드에서 커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-543">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="f86f1-544">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-544">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="f86f1-545">Vi 삽입 모드: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-545">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="f86f1-546">Vi 명령 모드: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-546">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="f86f1-547">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-547">ViBackwardWord</span></span>

<span data-ttu-id="f86f1-548">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-548">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="f86f1-549">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-549">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f86f1-550">Vi 명령 모드: `<b>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-550">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="f86f1-551">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-551">ViForwardChar</span></span>

<span data-ttu-id="f86f1-552">Vi 편집 모드에서 커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-552">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="f86f1-553">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-553">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="f86f1-554">Vi 삽입 모드: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-554">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="f86f1-555">Vi 명령 모드: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-555">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="f86f1-556">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-556">ViEndOfGlob</span></span>

<span data-ttu-id="f86f1-557">공백을 구분 기호로 사용 하 여 커서를 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-557">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="f86f1-558">Vi 명령 모드: `<E>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-558">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="f86f1-559">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-559">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="f86f1-560">공백을 단어 구분 기호로 사용 하 여 이전 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-560">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="f86f1-561">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-561">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="f86f1-562">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="f86f1-562">ViGotoBrace</span></span>

<span data-ttu-id="f86f1-563">GotoBrace와 비슷하지만 토큰 기반이 아니라 문자 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-563">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="f86f1-564">Vi 명령 모드: `<%>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-564">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="f86f1-565">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="f86f1-565">ViNextGlob</span></span>

<span data-ttu-id="f86f1-566">공백을 단어 구분 기호로 사용 하 여 다음 단어로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-566">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="f86f1-567">Vi 명령 모드: `<W>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-567">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="f86f1-568">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-568">ViNextWord</span></span>

<span data-ttu-id="f86f1-569">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-569">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="f86f1-570">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-570">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f86f1-571">Vi 명령 모드: `<w>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-571">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="f86f1-572">기록 함수</span><span class="sxs-lookup"><span data-stu-id="f86f1-572">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="f86f1-573">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="f86f1-573">BeginningOfHistory</span></span>

<span data-ttu-id="f86f1-574">기록의 첫 번째 항목으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-574">Move to the first item in the history.</span></span>

- <span data-ttu-id="f86f1-575">Emacs `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-575">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="f86f1-576">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="f86f1-576">ClearHistory</span></span>

<span data-ttu-id="f86f1-577">PSReadLine에서 기록을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-577">Clears history in PSReadLine.</span></span> <span data-ttu-id="f86f1-578">PowerShell 기록에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-578">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="f86f1-579">입력 `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-579">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="f86f1-580">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="f86f1-580">EndOfHistory</span></span>

<span data-ttu-id="f86f1-581">기록에서 마지막 항목 (현재 입력)으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-581">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="f86f1-582">Emacs `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-582">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="f86f1-583">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="f86f1-583">ForwardSearchHistory</span></span>

<span data-ttu-id="f86f1-584">기록을 통해 증분 전달 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-584">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="f86f1-585">입력 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-585">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="f86f1-586">Emacs `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-586">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="f86f1-587">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="f86f1-587">HistorySearchBackward</span></span>

<span data-ttu-id="f86f1-588">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-588">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="f86f1-589">입력 `<F8>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-589">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="f86f1-590">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="f86f1-590">HistorySearchForward</span></span>

<span data-ttu-id="f86f1-591">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-591">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="f86f1-592">입력 `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-592">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="f86f1-593">NextHistory</span><span class="sxs-lookup"><span data-stu-id="f86f1-593">NextHistory</span></span>

<span data-ttu-id="f86f1-594">현재 입력을 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-594">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="f86f1-595">입력 `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-595">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="f86f1-596">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-596">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="f86f1-597">Vi 삽입 모드: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-597">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="f86f1-598">Vi 명령 모드: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-598">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="f86f1-599">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="f86f1-599">PreviousHistory</span></span>

<span data-ttu-id="f86f1-600">현재 입력을 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-600">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="f86f1-601">입력 `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-601">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="f86f1-602">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-602">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="f86f1-603">Vi 삽입 모드: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-603">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="f86f1-604">Vi 명령 모드: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="f86f1-604">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="f86f1-605">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="f86f1-605">ReverseSearchHistory</span></span>

<span data-ttu-id="f86f1-606">기록을 통해 증분 역방향 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-606">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="f86f1-607">입력 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-607">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="f86f1-608">Emacs `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-608">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="f86f1-609">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="f86f1-609">ViSearchHistoryBackward</span></span>

<span data-ttu-id="f86f1-610">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-610">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="f86f1-611">Vi 삽입 모드: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-611">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="f86f1-612">Vi 명령 모드: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-612">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="f86f1-613">완료 함수</span><span class="sxs-lookup"><span data-stu-id="f86f1-613">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="f86f1-614">완료</span><span class="sxs-lookup"><span data-stu-id="f86f1-614">Complete</span></span>

<span data-ttu-id="f86f1-615">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-615">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="f86f1-616">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-616">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="f86f1-617">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-617">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="f86f1-618">Emacs `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-618">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="f86f1-619">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="f86f1-619">MenuComplete</span></span>

<span data-ttu-id="f86f1-620">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-620">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="f86f1-621">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-621">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="f86f1-622">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-622">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="f86f1-623">Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-623">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="f86f1-624">Emacs `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-624">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="f86f1-625">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="f86f1-625">PossibleCompletions</span></span>

<span data-ttu-id="f86f1-626">가능한 완료 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-626">Display the list of possible completions.</span></span>

- <span data-ttu-id="f86f1-627">Emacs `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-627">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="f86f1-628">Vi 삽입 모드: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-628">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="f86f1-629">Vi 명령 모드: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-629">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="f86f1-630">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="f86f1-630">TabCompleteNext</span></span>

<span data-ttu-id="f86f1-631">다음에 사용 가능한 완료로 커서를 둘러싼 텍스트를 완성 해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-631">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="f86f1-632">입력 `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-632">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="f86f1-633">Vi 명령 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-633">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="f86f1-634">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="f86f1-634">TabCompletePrevious</span></span>

<span data-ttu-id="f86f1-635">이전에 사용 가능한 완료를 사용 하 여 커서를 둘러싼 텍스트를 완료 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-635">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="f86f1-636">입력 `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-636">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="f86f1-637">Vi 명령 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-637">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="f86f1-638">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="f86f1-638">ViTabCompleteNext</span></span>

<span data-ttu-id="f86f1-639">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompleteNext를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-639">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="f86f1-640">Vi 삽입 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-640">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="f86f1-641">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="f86f1-641">ViTabCompletePrevious</span></span>

<span data-ttu-id="f86f1-642">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompletePrevious를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-642">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="f86f1-643">Vi 삽입 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-643">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="prediction-functions"></a><span data-ttu-id="f86f1-644">예측 함수</span><span class="sxs-lookup"><span data-stu-id="f86f1-644">Prediction functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="f86f1-645">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-645">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="f86f1-646">`InlineView`예측에 대 한 보기 스타일로를 사용 하는 경우 인라인 제안의 다음 단어를 그대로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-646">When using `InlineView` as the view style for prediction, accept the next word of the inline suggestion.</span></span>

- <span data-ttu-id="f86f1-647">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-647">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="f86f1-648">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="f86f1-648">AcceptSuggestion</span></span>

<span data-ttu-id="f86f1-649">`InlineView`예측에 대 한 보기 스타일로를 사용 하는 경우 현재 인라인 제안을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-649">When using `InlineView` as the view style for prediction, accept the current inline suggestion.</span></span>

- <span data-ttu-id="f86f1-650">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-650">Function is unbound.</span></span>

### <a name="nextsuggestion"></a><span data-ttu-id="f86f1-651">NextSuggestion</span><span class="sxs-lookup"><span data-stu-id="f86f1-651">NextSuggestion</span></span>

<span data-ttu-id="f86f1-652">`ListView`예측에 대 한 보기 스타일로를 사용 하는 경우 목록에서 다음 제안으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-652">When using `ListView` as the view style for prediction, navigate to the next suggestion in the list.</span></span>

- <span data-ttu-id="f86f1-653">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-653">Function is unbound.</span></span>

### <a name="previoussuggestion"></a><span data-ttu-id="f86f1-654">PreviousSuggestion</span><span class="sxs-lookup"><span data-stu-id="f86f1-654">PreviousSuggestion</span></span>

<span data-ttu-id="f86f1-655">`ListView`예측에 대 한 보기 스타일로을 사용 하는 경우 목록에서 이전 제안으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-655">When using `ListView` as the view style for prediction, navigate to the previous suggestion in the list.</span></span>

- <span data-ttu-id="f86f1-656">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-656">Function is unbound.</span></span>

### <a name="switchpredictionview"></a><span data-ttu-id="f86f1-657">SwitchPredictionView</span><span class="sxs-lookup"><span data-stu-id="f86f1-657">SwitchPredictionView</span></span>

<span data-ttu-id="f86f1-658">및 간의 예측에 대 한 뷰 스타일을 전환 합니다 `InlineView` `ListView` .</span><span class="sxs-lookup"><span data-stu-id="f86f1-658">Switch the view style for prediction between `InlineView` and `ListView`.</span></span>

- <span data-ttu-id="f86f1-659">입력 `<F2>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-659">Cmd: `<F2>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="f86f1-660">기타 함수</span><span class="sxs-lookup"><span data-stu-id="f86f1-660">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="f86f1-661">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="f86f1-661">CaptureScreen</span></span>

<span data-ttu-id="f86f1-662">대화형 화면 캡처 시작-위쪽/아래쪽 화살표 선 선택, 선택한 텍스트를 클립보드에 텍스트 및 html로 복사를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-662">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="f86f1-663">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-663">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="f86f1-664">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="f86f1-664">ClearScreen</span></span>

<span data-ttu-id="f86f1-665">화면을 지우고 화면 위쪽에 현재 줄을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-665">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="f86f1-666">입력 `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-666">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="f86f1-667">Emacs `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-667">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="f86f1-668">Vi 삽입 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-668">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="f86f1-669">Vi 명령 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-669">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="f86f1-670">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="f86f1-670">DigitArgument</span></span>

<span data-ttu-id="f86f1-671">다른 함수에 전달할 새 숫자 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-671">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="f86f1-672">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="f86f1-672">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="f86f1-673">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="f86f1-673">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="f86f1-674">Vi 명령 모드: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` `<7>` `<8>` ,,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-674">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="f86f1-675">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="f86f1-675">InvokePrompt</span></span>

<span data-ttu-id="f86f1-676">현재 프롬프트를 지우고 prompt 함수를 호출 하 여 프롬프트를 다시 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-676">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="f86f1-677">상태를 변경 하는 사용자 지정 키 처리기 (예: 현재 디렉터리 변경)에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-677">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="f86f1-678">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-678">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="f86f1-679">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="f86f1-679">ScrollDisplayDown</span></span>

<span data-ttu-id="f86f1-680">한 화면 아래로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-680">Scroll the display down one screen.</span></span>

- <span data-ttu-id="f86f1-681">입력 `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-681">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="f86f1-682">Emacs `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-682">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="f86f1-683">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-683">ScrollDisplayDownLine</span></span>

<span data-ttu-id="f86f1-684">표시를 한 줄 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-684">Scroll the display down one line.</span></span>

- <span data-ttu-id="f86f1-685">입력 `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-685">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="f86f1-686">Emacs `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-686">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="f86f1-687">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="f86f1-687">ScrollDisplayToCursor</span></span>

<span data-ttu-id="f86f1-688">표시를 커서로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-688">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="f86f1-689">Emacs `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-689">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="f86f1-690">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="f86f1-690">ScrollDisplayTop</span></span>

<span data-ttu-id="f86f1-691">표시를 맨 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-691">Scroll the display to the top.</span></span>

- <span data-ttu-id="f86f1-692">Emacs `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-692">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="f86f1-693">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="f86f1-693">ScrollDisplayUp</span></span>

<span data-ttu-id="f86f1-694">한 화면 위로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-694">Scroll the display up one screen.</span></span>

- <span data-ttu-id="f86f1-695">입력 `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-695">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="f86f1-696">Emacs `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-696">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="f86f1-697">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-697">ScrollDisplayUpLine</span></span>

<span data-ttu-id="f86f1-698">디스플레이를 한 줄 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-698">Scroll the display up one line.</span></span>

- <span data-ttu-id="f86f1-699">입력 `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-699">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="f86f1-700">Emacs `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-700">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="f86f1-701">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="f86f1-701">SelfInsert</span></span>

<span data-ttu-id="f86f1-702">키를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-702">Insert the key.</span></span>

- <span data-ttu-id="f86f1-703">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-703">Function is unbound.</span></span>

### <a name="showcommandhelp"></a><span data-ttu-id="f86f1-704">ShowCommandHelp</span><span class="sxs-lookup"><span data-stu-id="f86f1-704">ShowCommandHelp</span></span>

<span data-ttu-id="f86f1-705">**Microsoft. PowerShell** 호출기를 사용 하 여 대체 화면 버퍼에 대 한 전체 cmdlet 도움말 보기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-705">Provides a view of full cmdlet help on alternate screen buffer using a Pager from **Microsoft.PowerShell.Pager**.</span></span>

- <span data-ttu-id="f86f1-706">입력 `<F1>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-706">Cmd: `<F1>`</span></span>
- <span data-ttu-id="f86f1-707">Emacs `<F1>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-707">Emacs: `<F1>`</span></span>
- <span data-ttu-id="f86f1-708">Vi 삽입 모드: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-708">Vi insert mode: `<F1>`</span></span>
- <span data-ttu-id="f86f1-709">Vi 명령 모드: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-709">Vi command mode: `<F1>`</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="f86f1-710">ShowKeyBindings 바인딩</span><span class="sxs-lookup"><span data-stu-id="f86f1-710">ShowKeyBindings</span></span>

<span data-ttu-id="f86f1-711">모든 바인딩된 키를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-711">Show all bound keys.</span></span>

- <span data-ttu-id="f86f1-712">입력 `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-712">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="f86f1-713">Emacs `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-713">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="f86f1-714">Vi 삽입 모드: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-714">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="showparameterhelp"></a><span data-ttu-id="f86f1-715">ShowParameterHelp</span><span class="sxs-lookup"><span data-stu-id="f86f1-715">ShowParameterHelp</span></span>

<span data-ttu-id="f86f1-716">는와 같이 현재 명령줄 아래에 표시 하 여 매개 변수에 대 한 동적 도움말을 제공 `MenuComplete` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-716">Provides dynamic help for parameters by showing it below the current command line like `MenuComplete`.</span></span>

- <span data-ttu-id="f86f1-717">입력 `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-717">Cmd: `<Alt+h>`</span></span>
- <span data-ttu-id="f86f1-718">Emacs `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-718">Emacs: `<Alt+h>`</span></span>
- <span data-ttu-id="f86f1-719">Vi 삽입 모드: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-719">Vi insert mode: `<Alt+h>`</span></span>
- <span data-ttu-id="f86f1-720">Vi 명령 모드: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-720">Vi command mode: `<Alt+h>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="f86f1-721">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="f86f1-721">ViCommandMode</span></span>

<span data-ttu-id="f86f1-722">Vi-Insert에서 현재 운영 모드를 Vi 명령으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-722">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="f86f1-723">Vi 삽입 모드: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-723">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="f86f1-724">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="f86f1-724">ViDigitArgumentInChord</span></span>

<span data-ttu-id="f86f1-725">Vi의 누르는 중 하나에서 다른 함수에 전달할 새 digit 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-725">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="f86f1-726">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-726">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="f86f1-727">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="f86f1-727">ViEditVisually</span></span>

<span data-ttu-id="f86f1-728">$Env: 편집기 또는 $env: 시각적 개체에 지정 된 텍스트 편집기에서 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-728">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="f86f1-729">Emacs `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-729">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="f86f1-730">Vi 명령 모드: `<v>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-730">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="f86f1-731">ViExit</span><span class="sxs-lookup"><span data-stu-id="f86f1-731">ViExit</span></span>

<span data-ttu-id="f86f1-732">셸을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-732">Exits the shell.</span></span>

- <span data-ttu-id="f86f1-733">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-733">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="f86f1-734">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="f86f1-734">ViInsertMode</span></span>

<span data-ttu-id="f86f1-735">삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-735">Switch to Insert mode.</span></span>

- <span data-ttu-id="f86f1-736">Vi 명령 모드: `<i>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-736">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="f86f1-737">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="f86f1-737">WhatIsKey</span></span>

<span data-ttu-id="f86f1-738">키를 읽고 키가 바인딩된 정보를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-738">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="f86f1-739">입력 `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-739">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="f86f1-740">Emacs `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-740">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="f86f1-741">선택 함수</span><span class="sxs-lookup"><span data-stu-id="f86f1-741">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="f86f1-742">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="f86f1-742">ExchangePointAndMark</span></span>

<span data-ttu-id="f86f1-743">커서는 표시 위치에 배치 되 고 표시는 커서의 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-743">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="f86f1-744">Emacs `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-744">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="f86f1-745">SelectAll</span><span class="sxs-lookup"><span data-stu-id="f86f1-745">SelectAll</span></span>

<span data-ttu-id="f86f1-746">전체 줄을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-746">Select the entire line.</span></span>

- <span data-ttu-id="f86f1-747">입력 `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-747">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="f86f1-748">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-748">SelectBackwardChar</span></span>

<span data-ttu-id="f86f1-749">이전 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-749">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="f86f1-750">입력 `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-750">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="f86f1-751">Emacs `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-751">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="f86f1-752">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-752">SelectBackwardsLine</span></span>

<span data-ttu-id="f86f1-753">커서에서 줄의 시작 부분까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-753">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="f86f1-754">입력 `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-754">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="f86f1-755">Emacs `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-755">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="f86f1-756">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-756">SelectBackwardWord</span></span>

<span data-ttu-id="f86f1-757">이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-757">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="f86f1-758">입력 `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-758">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="f86f1-759">Emacs `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-759">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="f86f1-760">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-760">SelectForwardChar</span></span>

<span data-ttu-id="f86f1-761">다음 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-761">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="f86f1-762">입력 `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-762">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="f86f1-763">Emacs `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-763">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="f86f1-764">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-764">SelectForwardWord</span></span>

<span data-ttu-id="f86f1-765">ForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-765">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="f86f1-766">Emacs `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-766">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="f86f1-767">줄을 select</span><span class="sxs-lookup"><span data-stu-id="f86f1-767">SelectLine</span></span>

<span data-ttu-id="f86f1-768">커서에서 줄의 끝까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-768">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="f86f1-769">입력 `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-769">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="f86f1-770">Emacs `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-770">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="f86f1-771">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-771">SelectNextWord</span></span>

<span data-ttu-id="f86f1-772">다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-772">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="f86f1-773">입력 `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-773">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="f86f1-774">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-774">SelectShellBackwardWord</span></span>

<span data-ttu-id="f86f1-775">ShellBackwardWord를 사용 하 여 이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-775">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="f86f1-776">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-776">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="f86f1-777">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-777">SelectShellForwardWord</span></span>

<span data-ttu-id="f86f1-778">ShellForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-778">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="f86f1-779">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-779">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="f86f1-780">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="f86f1-780">SelectShellNextWord</span></span>

<span data-ttu-id="f86f1-781">ShellNextWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-781">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="f86f1-782">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-782">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="f86f1-783">SetMark</span><span class="sxs-lookup"><span data-stu-id="f86f1-783">SetMark</span></span>

<span data-ttu-id="f86f1-784">이후 편집 명령에 사용할 커서의 현재 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-784">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="f86f1-785">Emacs `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-785">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="f86f1-786">예측 IntelliSense 함수</span><span class="sxs-lookup"><span data-stu-id="f86f1-786">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="f86f1-787">이러한 함수를 사용 하려면 예측 IntelliSense를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-787">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="f86f1-788">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="f86f1-788">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="f86f1-789">예측 IntelliSense에서 인라인 제안의 다음 단어를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-789">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="f86f1-790">이 함수 <kbd></kbd> + 는 다음 명령을 실행 하 여 Ctrl<kbd>F</kbd> 를 사용 하 여 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-790">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="f86f1-791">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="f86f1-791">AcceptSuggestion</span></span>

<span data-ttu-id="f86f1-792">커서가 현재 줄의 끝에 있을 때 <kbd>오른쪽 화살표</kbd> 를 눌러 예측 IntelliSense의 현재 인라인 제안을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-792">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="f86f1-793">검색 함수</span><span class="sxs-lookup"><span data-stu-id="f86f1-793">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="f86f1-794">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="f86f1-794">CharacterSearch</span></span>

<span data-ttu-id="f86f1-795">문자를 읽고 그 다음 번에 해당 문자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-795">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="f86f1-796">인수를 지정 하는 경우 n 번째 발생에 대해 앞으로 (음수 이면 뒤로) 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-796">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="f86f1-797">입력 `<F3>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-797">Cmd: `<F3>`</span></span>
- <span data-ttu-id="f86f1-798">Emacs `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-798">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="f86f1-799">Vi 삽입 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-799">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="f86f1-800">Vi 명령 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-800">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="f86f1-801">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="f86f1-801">CharacterSearchBackward</span></span>

<span data-ttu-id="f86f1-802">문자를 읽은 다음 해당 문자의 다음 항목을 뒤로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-802">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="f86f1-803">인수를 지정 하는 경우 n 번째 발생에 대해 뒤로 검색 하거나 음수 이면 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-803">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="f86f1-804">입력 `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-804">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="f86f1-805">Emacs `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-805">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="f86f1-806">Vi 삽입 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-806">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="f86f1-807">Vi 명령 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-807">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="f86f1-808">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="f86f1-808">RepeatLastCharSearch</span></span>

<span data-ttu-id="f86f1-809">마지막으로 기록 된 문자 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-809">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="f86f1-810">Vi 명령 모드: `<;>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-810">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="f86f1-811">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="f86f1-811">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="f86f1-812">마지막으로 기록 된 문자 검색을 반대 방향으로 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-812">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="f86f1-813">Vi 명령 모드: `<,>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-813">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="f86f1-814">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="f86f1-814">RepeatSearch</span></span>

<span data-ttu-id="f86f1-815">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-815">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="f86f1-816">Vi 명령 모드: `<n>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-816">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="f86f1-817">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="f86f1-817">RepeatSearchBackward</span></span>

<span data-ttu-id="f86f1-818">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-818">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="f86f1-819">Vi 명령 모드: `<N>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-819">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="f86f1-820">SearchChar</span><span class="sxs-lookup"><span data-stu-id="f86f1-820">SearchChar</span></span>

<span data-ttu-id="f86f1-821">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-821">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="f86f1-822">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-822">This is for 't' functionality.</span></span>

- <span data-ttu-id="f86f1-823">Vi 명령 모드: `<f>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-823">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="f86f1-824">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="f86f1-824">SearchCharBackward</span></span>

<span data-ttu-id="f86f1-825">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-825">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="f86f1-826">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-826">This is for 'T' functionality.</span></span>

- <span data-ttu-id="f86f1-827">Vi 명령 모드: `<F>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-827">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="f86f1-828">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="f86f1-828">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="f86f1-829">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-829">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="f86f1-830">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-830">This is for 'T' functionality.</span></span>

- <span data-ttu-id="f86f1-831">Vi 명령 모드: `<T>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-831">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="f86f1-832">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="f86f1-832">SearchCharWithBackoff</span></span>

<span data-ttu-id="f86f1-833">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-833">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="f86f1-834">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-834">This is for 't' functionality.</span></span>

- <span data-ttu-id="f86f1-835">Vi 명령 모드: `<t>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-835">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="f86f1-836">SearchForward</span><span class="sxs-lookup"><span data-stu-id="f86f1-836">SearchForward</span></span>

<span data-ttu-id="f86f1-837">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-837">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="f86f1-838">Vi 삽입 모드: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-838">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="f86f1-839">Vi 명령 모드: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="f86f1-839">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="f86f1-840">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="f86f1-840">Custom Key Bindings</span></span>

<span data-ttu-id="f86f1-841">PSReadLine은 cmdlet을 사용 하 여 사용자 지정 키 바인딩을 지원 `Set-PSReadLineKeyHandler` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-841">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="f86f1-842">대부분의 사용자 지정 키 바인딩은 위의 함수 중 하나를 호출 합니다. 예를 들면</span><span class="sxs-lookup"><span data-stu-id="f86f1-842">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="f86f1-843">ScriptBlock을 키에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-843">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="f86f1-844">ScriptBlock은 필요한 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-844">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="f86f1-845">몇 가지 유용한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-845">Some useful examples include</span></span>

- <span data-ttu-id="f86f1-846">명령줄 편집</span><span class="sxs-lookup"><span data-stu-id="f86f1-846">edit the command line</span></span>
- <span data-ttu-id="f86f1-847">새 창 열기 (예: 도움말)</span><span class="sxs-lookup"><span data-stu-id="f86f1-847">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="f86f1-848">명령줄을 변경 하지 않고 디렉터리를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-848">change directories without changing the command line</span></span>

<span data-ttu-id="f86f1-849">ScriptBlock은 두 개의 인수를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-849">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="f86f1-850">`$key` -사용자 지정 바인딩을 트리거한 키 인 **[ConsoleKeyInfo]** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-850">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="f86f1-851">동일한 ScriptBlock을 여러 키에 바인딩하고 키에 따라 다른 작업을 수행 해야 하는 경우 $key를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-851">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="f86f1-852">많은 사용자 지정 바인딩에서이 인수를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-852">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="f86f1-853">`$arg` -임의의 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-853">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="f86f1-854">가장 자주 사용 되는 정수 인수는 사용자가 키 바인딩 DigitArgument에서 전달 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-854">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="f86f1-855">바인딩에서 인수를 허용 하지 않는 경우에는이 인수를 무시 하는 것이 합리적입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-855">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="f86f1-856">실행 하지 않고 기록에 명령줄을 추가 하는 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-856">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="f86f1-857">이는 작업을 수행 하지 못했지만 이미 입력 한 명령줄을 다시 입력 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-857">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="f86f1-858">PSReadLine 모듈 폴더에 설치 된 파일에서 더 많은 예제를 볼 수 있습니다 `SamplePSReadLineProfile.ps1` .</span><span class="sxs-lookup"><span data-stu-id="f86f1-858">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="f86f1-859">대부분의 키 바인딩은 일부 도우미 함수를 사용 하 여 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-859">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="f86f1-860">이러한 Api는 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-860">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="f86f1-861">사용자 지정 키 바인딩 지원 Api</span><span class="sxs-lookup"><span data-stu-id="f86f1-861">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="f86f1-862">다음 함수는 PSConsoleReadLine에서 공용 이지만 키에 직접 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-862">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="f86f1-863">대부분은 사용자 지정 키 바인딩에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-863">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="f86f1-864">실행 하지 않고 기록에 명령줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-864">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="f86f1-865">Kill 링을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-865">Clear the kill-ring.</span></span>  <span data-ttu-id="f86f1-866">이는 주로 테스트에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-866">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="f86f1-867">시작에서 길이 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-867">Delete length characters from start.</span></span>  <span data-ttu-id="f86f1-868">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-868">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="f86f1-869">사용자 기본 설정에 따라 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-869">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="f86f1-870">이러한 두 함수는 입력 버퍼의 현재 상태에 대 한 유용한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-870">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="f86f1-871">첫 번째는 간단한 경우에 보다 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-871">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="f86f1-872">두 번째는 바인딩에서 Ast를 사용 하 여 더 높은 작업을 수행 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-872">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="f86f1-873">이러한 두 함수는에 사용 됩니다 `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="f86f1-873">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="f86f1-874">첫 번째는 모든 키 바인딩을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-874">The first is used to get all key bindings.</span></span> <span data-ttu-id="f86f1-875">두 번째는 특정 키 바인딩을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-875">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="f86f1-876">이 함수는 Get-PSReadLineOption에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-876">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="f86f1-877">명령줄에 선택 항목이 없으면-1이 시작 및 길이 둘 다에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-877">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="f86f1-878">명령줄에 선택 항목이 있는 경우 선택의 시작 및 길이가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-878">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="f86f1-879">커서에 문자 또는 문자열을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-879">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="f86f1-880">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-880">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="f86f1-881">PSReadLine에 대 한 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-881">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="f86f1-882">재귀를 지원 하지 않으므로 사용자 지정 키 바인딩에는 유용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-882">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="f86f1-883">이 함수는 Remove-PSReadLineKeyHandler에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-883">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="f86f1-884">일부 입력을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-884">Replace some of the input.</span></span> <span data-ttu-id="f86f1-885">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-885">This operation supports undo/redo.</span></span> <span data-ttu-id="f86f1-886">이는 실행 취소의 단일 작업으로 처리 되기 때문에 Delete 뒤에 Insert를 통해 선호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-886">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="f86f1-887">커서를 지정 된 오프셋으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-887">Move the cursor to the given offset.</span></span> <span data-ttu-id="f86f1-888">실행 취소를 위해 커서 이동이 추적 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-888">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="f86f1-889">이 함수는 cmdlet Set-PSReadLineOption에서 사용 되는 도우미 메서드로, 설정을 일시적으로 변경 하려는 사용자 지정 키 바인딩에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-889">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="f86f1-890">이 도우미 메서드는 DigitArgument을 준수 하는 사용자 지정 바인딩에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-890">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="f86f1-891">일반적인 호출은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-891">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="f86f1-892">참고</span><span class="sxs-lookup"><span data-stu-id="f86f1-892">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="f86f1-893">명령 기록</span><span class="sxs-lookup"><span data-stu-id="f86f1-893">Command History</span></span>

<span data-ttu-id="f86f1-894">PSReadLine은 명령줄에서 입력 한 모든 명령 및 데이터를 포함 하는 기록 파일을 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-894">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="f86f1-895">여기에는 암호를 비롯 한 중요 한 데이터가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-895">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="f86f1-896">예를 들어 cmdlet을 사용 하는 경우 `ConvertTo-SecureString` 암호는 일반 텍스트로 기록 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-896">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="f86f1-897">기록 파일은 라는 파일입니다 `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="f86f1-897">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="f86f1-898">Windows 시스템에서 기록 파일은에 저장 됩니다 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="f86f1-898">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="f86f1-899">Windows가 아닌 시스템에서 기록 파일은 또는에 저장 됩니다 `$env:XDG_DATA_HOME/powershell/PSReadLine` `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="f86f1-899">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="f86f1-900">PSReadLine에 영향을 주는 & 피드백</span><span class="sxs-lookup"><span data-stu-id="f86f1-900">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="f86f1-901">GitHub의 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="f86f1-901">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="f86f1-902">GitHub 페이지에서 끌어오기 요청을 제출 하거나 피드백을 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-902">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="f86f1-903">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f86f1-903">See Also</span></span>

<span data-ttu-id="f86f1-904">PSReadLine은 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 라이브러리의 영향을 많이 받습니다.</span><span class="sxs-lookup"><span data-stu-id="f86f1-904">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
