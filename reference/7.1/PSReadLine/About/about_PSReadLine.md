---
description: PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSReadLine 정보
ms.openlocfilehash: 6d52bb04118914a9ccca5d3442a9d1915c1c2818
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692278"
---
# <a name="psreadline"></a><span data-ttu-id="11e5a-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="11e5a-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="11e5a-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="11e5a-106">Short Description</span></span>

<span data-ttu-id="11e5a-107">PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="11e5a-108">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="11e5a-108">Long Description</span></span>

<span data-ttu-id="11e5a-109">PSReadLine 2.1은 PowerShell 콘솔에 대 한 강력한 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-109">PSReadLine 2.1 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="11e5a-110">이 콘솔은 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-110">It provides:</span></span>

- <span data-ttu-id="11e5a-111">명령줄의 구문 색 지정</span><span class="sxs-lookup"><span data-stu-id="11e5a-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="11e5a-112">구문 오류를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="11e5a-113">더 나은 여러 줄 환경 (편집 및 기록 모두)</span><span class="sxs-lookup"><span data-stu-id="11e5a-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="11e5a-114">사용자 지정 가능한 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="11e5a-114">Customizable key bindings</span></span>
- <span data-ttu-id="11e5a-115">Cmd 및 Emacs 모드</span><span class="sxs-lookup"><span data-stu-id="11e5a-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="11e5a-116">많은 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="11e5a-116">Many configuration options</span></span>
- <span data-ttu-id="11e5a-117">Bash 스타일 완성 (Cmd 모드에서는 선택 사항, Emacs 모드에서는 기본값)</span><span class="sxs-lookup"><span data-stu-id="11e5a-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="11e5a-118">Emacs yank/kill</span><span class="sxs-lookup"><span data-stu-id="11e5a-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="11e5a-119">PowerShell 토큰 기반 "word" 이동 및 중지</span><span class="sxs-lookup"><span data-stu-id="11e5a-119">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="11e5a-120">예측 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="11e5a-120">Predictive IntelliSense</span></span>

<span data-ttu-id="11e5a-121">PSReadLine에는 PowerShell 3.0 이상 및 콘솔 호스트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-121">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="11e5a-122">PowerShell ISE에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-122">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="11e5a-123">Visual Studio Code 콘솔에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-123">It does work in the console of Visual Studio Code.</span></span>

<span data-ttu-id="11e5a-124">PSReadLine 2.1.0는 PowerShell 7.1과 함께 제공 되며, 지원 되는 모든 버전의 PowerShell에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-124">PSReadLine 2.1.0 ships with PowerShell 7.1 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="11e5a-125">PowerShell 갤러리에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-125">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="11e5a-126">지원 되는 버전의 PowerShell에서 PSReadLine 2.1.0을 설치 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-126">To install PSReadLine 2.1.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -RequiredVersion 2.1.0
```

> [!NOTE]
> <span data-ttu-id="11e5a-127">PowerShell 7.0부터 PowerShell은 화면 판독기 프로그램이 검색 된 경우 Windows에서 PSReadLine 자동 로드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-127">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="11e5a-128">현재 PSReadLine은 화면 판독기에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-128">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="11e5a-129">Windows에서 PowerShell 7.0의 기본 렌더링 및 형식이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-129">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="11e5a-130">필요한 경우 모듈을 수동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-130">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="11e5a-131">예측 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="11e5a-131">Predictive IntelliSense</span></span>

<span data-ttu-id="11e5a-132">예측 IntelliSense는 사용자가 명령을 성공적으로 완료 하는 데 도움이 되는 탭 완성 이라는 개념에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-132">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="11e5a-133">사용자가 사용자 기록과 추가 도메인 특정 플러그인의 일치 하는 예측에 따라 전체 명령을 검색, 편집 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-133">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="11e5a-134">예측 IntelliSense 사용</span><span class="sxs-lookup"><span data-stu-id="11e5a-134">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="11e5a-135">예측 IntelliSense는 기본적으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-135">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="11e5a-136">예측을 사용 하도록 설정 하려면 다음 명령을 실행 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-136">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="11e5a-137">**PredictionSource** 매개 변수는 도메인 특정 요구 사항 및 사용자 지정 요구 사항에 대 한 플러그 인도 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-137">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="11e5a-138">예측 IntelliSense를 사용 하지 않도록 설정 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-138">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="11e5a-139">다음 함수는 **[PSConsoleReadLine]** 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-139">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="11e5a-140">기본 편집 함수</span><span class="sxs-lookup"><span data-stu-id="11e5a-140">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="11e5a-141">중단</span><span class="sxs-lookup"><span data-stu-id="11e5a-141">Abort</span></span>

<span data-ttu-id="11e5a-142">현재 작업을 중단 합니다 (예: 증분 기록 검색).</span><span class="sxs-lookup"><span data-stu-id="11e5a-142">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="11e5a-143">Emacs `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-143">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="11e5a-144">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="11e5a-144">AcceptAndGetNext</span></span>

<span data-ttu-id="11e5a-145">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-145">Attempt to execute the current input.</span></span> <span data-ttu-id="11e5a-146">실행 될 수 있는 경우 (예: AcceptLine) 다음에 ReadLine이 호출 될 때 기록에서 다음 항목을 회수 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-146">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="11e5a-147">Emacs `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-147">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="11e5a-148">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-148">AcceptLine</span></span>

<span data-ttu-id="11e5a-149">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-149">Attempt to execute the current input.</span></span> <span data-ttu-id="11e5a-150">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-150">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="11e5a-151">입력 `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-151">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="11e5a-152">Emacs `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-152">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="11e5a-153">Vi 삽입 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-153">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="11e5a-154">AddLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-154">AddLine</span></span>

<span data-ttu-id="11e5a-155">연속 프롬프트가 다음 줄에 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-155">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="11e5a-156">이는 한 줄이 자체적으로 전체 입력 인 경우에도 여러 줄 입력을 단일 명령으로 입력 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-156">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="11e5a-157">입력 `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-157">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="11e5a-158">Emacs `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-158">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="11e5a-159">Vi 삽입 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-159">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="11e5a-160">Vi 명령 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-160">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="11e5a-161">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-161">BackwardDeleteChar</span></span>

<span data-ttu-id="11e5a-162">커서 앞에 있는 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-162">Delete the character before the cursor.</span></span>

- <span data-ttu-id="11e5a-163">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-163">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="11e5a-164">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-164">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="11e5a-165">Vi 삽입 모드: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-165">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="11e5a-166">Vi 명령 모드: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-166">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="11e5a-167">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-167">BackwardDeleteLine</span></span>

<span data-ttu-id="11e5a-168">Like BackwardKillLine-점에서 줄의 시작 부분으로 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-168">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="11e5a-169">입력 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-169">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="11e5a-170">Vi 삽입 모드: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-170">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="11e5a-171">Vi 명령 모드: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-171">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="11e5a-172">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-172">BackwardDeleteWord</span></span>

<span data-ttu-id="11e5a-173">이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-173">Deletes the previous word.</span></span>

- <span data-ttu-id="11e5a-174">Vi 명령 모드: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-174">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="11e5a-175">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-175">BackwardKillLine</span></span>

<span data-ttu-id="11e5a-176">커서에 대 한 입력의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-176">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="11e5a-177">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-177">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="11e5a-178">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-178">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="11e5a-179">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-179">BackwardKillWord</span></span>

<span data-ttu-id="11e5a-180">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-180">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="11e5a-181">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-181">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="11e5a-182">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="11e5a-183">Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-183">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="11e5a-184">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-184">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="11e5a-185">Vi 삽입 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-185">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="11e5a-186">Vi 명령 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-186">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="11e5a-187">CancelLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-187">CancelLine</span></span>

<span data-ttu-id="11e5a-188">화면에 입력을 그대로 두고 현재 입력을 취소 합니다. 그러나 프롬프트가 다시 계산 되도록 다시 호스트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-188">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="11e5a-189">Vi 삽입 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-189">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="11e5a-190">Vi 명령 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-190">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="11e5a-191">복사</span><span class="sxs-lookup"><span data-stu-id="11e5a-191">Copy</span></span>

<span data-ttu-id="11e5a-192">선택한 영역을 시스템 클립보드에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-192">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="11e5a-193">선택 된 지역이 없으면 전체 줄을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-193">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="11e5a-194">입력 `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-194">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="11e5a-195">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-195">CopyOrCancelLine</span></span>

<span data-ttu-id="11e5a-196">텍스트를 선택한 경우 클립보드로 복사 하 고, 그렇지 않으면 줄을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-196">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="11e5a-197">입력 `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-197">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="11e5a-198">Emacs `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-198">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="11e5a-199">잘라내기</span><span class="sxs-lookup"><span data-stu-id="11e5a-199">Cut</span></span>

<span data-ttu-id="11e5a-200">삭제 된 텍스트를 시스템 클립보드에 배치 하는 선택한 영역을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-200">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="11e5a-201">입력 `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-201">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="11e5a-202">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-202">DeleteChar</span></span>

<span data-ttu-id="11e5a-203">커서 아래의 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-203">Delete the character under the cursor.</span></span>

- <span data-ttu-id="11e5a-204">입력 `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-204">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="11e5a-205">Emacs `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-205">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="11e5a-206">Vi 삽입 모드: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-206">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="11e5a-207">Vi 명령 모드: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-207">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="11e5a-208">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="11e5a-208">DeleteCharOrExit</span></span>

<span data-ttu-id="11e5a-209">커서 아래의 문자를 삭제 하거나, 줄이 비어 있으면 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-209">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="11e5a-210">Emacs `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-210">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="11e5a-211">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="11e5a-211">DeleteEndOfBuffer</span></span>

<span data-ttu-id="11e5a-212">여러 줄 버퍼의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-212">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="11e5a-213">Vi 명령 모드: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-213">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="11e5a-214">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-214">DeleteEndOfWord</span></span>

<span data-ttu-id="11e5a-215">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-215">Delete to the end of the word.</span></span>

- <span data-ttu-id="11e5a-216">Vi 명령 모드: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-216">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="11e5a-217">Deleteline.invoke</span><span class="sxs-lookup"><span data-stu-id="11e5a-217">DeleteLine</span></span>

<span data-ttu-id="11e5a-218">여러 줄 버퍼의 현재 논리 줄을 삭제 하 고 실행 취소를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-218">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="11e5a-219">Vi 명령 모드: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-219">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="11e5a-220">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="11e5a-220">DeletePreviousLines</span></span>

<span data-ttu-id="11e5a-221">여러 줄 버퍼에서 요청 된 이전 논리 줄과 현재 논리 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-221">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="11e5a-222">Vi 명령 모드: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-222">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="11e5a-223">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="11e5a-223">DeleteRelativeLines</span></span>

<span data-ttu-id="11e5a-224">버퍼의 시작 부분에서 여러 줄 버퍼의 현재 논리 줄까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-224">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="11e5a-225">대부분의 Vi 명령으로 `<d,g,g>` 명령 앞에는 절대 줄 번호를 지정 하는 숫자 인수를 추가할 수 있습니다 .이 숫자는 현재 줄 번호와 함께 삭제 될 줄의 범위를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-225">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="11e5a-226">지정 하지 않으면 숫자 인수는 기본적으로 1로 설정 되며이는 여러 줄 버퍼의 첫 번째 논리 줄을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-226">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="11e5a-227">여러 줄에서 삭제 되는 실제 줄 수는 현재 논리 줄 번호와 지정 된 숫자 인수 간의 차이로 계산 되므로 음수가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-227">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="11e5a-228">따라서 메서드 이름의 _상대_ 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-228">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="11e5a-229">Vi 명령 모드: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-229">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="11e5a-230">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="11e5a-230">DeleteNextLines</span></span>

<span data-ttu-id="11e5a-231">여러 줄 버퍼에서 현재 논리 줄 및 요청 된 다음 논리 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-231">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="11e5a-232">Vi 명령 모드: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-232">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="11e5a-233">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-233">DeleteLineToFirstChar</span></span>

<span data-ttu-id="11e5a-234">커서에서 줄의 공백이 아닌 첫 번째 문자로 텍스트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-234">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="11e5a-235">Vi 명령 모드: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-235">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="11e5a-236">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="11e5a-236">DeleteToEnd</span></span>

<span data-ttu-id="11e5a-237">줄의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-237">Delete to the end of the line.</span></span>

- <span data-ttu-id="11e5a-238">Vi 명령 모드: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-238">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="11e5a-239">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-239">DeleteWord</span></span>

<span data-ttu-id="11e5a-240">다음 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-240">Delete the next word.</span></span>

- <span data-ttu-id="11e5a-241">Vi 명령 모드: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-241">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="11e5a-242">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-242">ForwardDeleteLine</span></span>

<span data-ttu-id="11e5a-243">Like ForwardKillLine-포인트에서 줄 끝 까지의 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-243">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="11e5a-244">입력 `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-244">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="11e5a-245">Vi 삽입 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-245">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="11e5a-246">Vi 명령 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-246">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="11e5a-247">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="11e5a-247">InsertLineAbove</span></span>

<span data-ttu-id="11e5a-248">현재 줄에 커서가 있는 위치에 관계 없이 새 빈 줄이 현재 줄 위에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-248">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="11e5a-249">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-249">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="11e5a-250">입력 `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-250">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="11e5a-251">Insertlinenea</span><span class="sxs-lookup"><span data-stu-id="11e5a-251">InsertLineBelow</span></span>

<span data-ttu-id="11e5a-252">커서가 현재 줄에 있는지 여부에 관계 없이 현재 줄 아래에 빈 줄이 새로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-252">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="11e5a-253">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-253">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="11e5a-254">입력 `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-254">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="11e5a-255">InvertCase</span><span class="sxs-lookup"><span data-stu-id="11e5a-255">InvertCase</span></span>

<span data-ttu-id="11e5a-256">현재 문자의 대/소문자를 반전 하 고 다음으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-256">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="11e5a-257">Vi 명령 모드: `<~>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-257">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="11e5a-258">KillLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-258">KillLine</span></span>

<span data-ttu-id="11e5a-259">입력의 끝 부분까지 커서에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-259">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="11e5a-260">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-260">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="11e5a-261">Emacs `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-261">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="11e5a-262">KillRegion</span><span class="sxs-lookup"><span data-stu-id="11e5a-262">KillRegion</span></span>

<span data-ttu-id="11e5a-263">커서와 표시 사이에 있는 텍스트를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-263">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="11e5a-264">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-264">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="11e5a-265">KillWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-265">KillWord</span></span>

<span data-ttu-id="11e5a-266">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-266">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="11e5a-267">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-267">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="11e5a-268">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-268">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="11e5a-269">Cmd: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-269">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="11e5a-270">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-270">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="11e5a-271">Vi 삽입 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-271">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="11e5a-272">Vi 명령 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-272">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="11e5a-273">붙여넣기</span><span class="sxs-lookup"><span data-stu-id="11e5a-273">Paste</span></span>

<span data-ttu-id="11e5a-274">시스템 클립보드에서 텍스트를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-274">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="11e5a-275">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-275">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="11e5a-276">Vi 삽입 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-276">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="11e5a-277">Vi 명령 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-277">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11e5a-278">**Paste** 함수를 사용 하는 경우 클립보드 버퍼의 전체 내용이 psreadline의 입력 버퍼에 붙여넣어집니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-278">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="11e5a-279">그런 다음 입력 버퍼가 PowerShell 파서로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-279">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="11e5a-280">콘솔 응용 프로그램의 **마우스 오른쪽 단추 클릭** 붙여넣기 메서드를 사용 하 여 붙여넣은 입력은 입력 버퍼에 한 번에 한 문자씩 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-280">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="11e5a-281">입력 버퍼는 줄 바꿈 문자가 복사 될 때 파서에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-281">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="11e5a-282">따라서 입력은 한 번에 한 줄씩 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-282">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="11e5a-283">붙여넣기 메서드 간의 차이점으로 인해 실행 동작이 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-283">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="11e5a-284">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="11e5a-284">PasteAfter</span></span>

<span data-ttu-id="11e5a-285">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 뒤에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-285">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="11e5a-286">Vi 명령 모드: `<p>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-286">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="11e5a-287">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="11e5a-287">PasteBefore</span></span>

<span data-ttu-id="11e5a-288">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 앞에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-288">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="11e5a-289">Vi 명령 모드: `<P>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-289">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="11e5a-290">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="11e5a-290">PrependAndAccept</span></span>

<span data-ttu-id="11e5a-291">' # ' 앞에를 추가 하 고 줄을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-291">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="11e5a-292">Vi 명령 모드: `<#>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-292">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="11e5a-293">다시 실행</span><span class="sxs-lookup"><span data-stu-id="11e5a-293">Redo</span></span>

<span data-ttu-id="11e5a-294">실행 취소를 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-294">Undo an undo.</span></span>

- <span data-ttu-id="11e5a-295">입력 `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-295">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="11e5a-296">Vi 삽입 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-296">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="11e5a-297">Vi 명령 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-297">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="11e5a-298">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="11e5a-298">RepeatLastCommand</span></span>

<span data-ttu-id="11e5a-299">마지막 텍스트 수정 작업을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-299">Repeat the last text modification.</span></span>

- <span data-ttu-id="11e5a-300">Vi 명령 모드: `<.>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-300">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="11e5a-301">RevertLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-301">RevertLine</span></span>

<span data-ttu-id="11e5a-302">모든 입력을 현재 입력으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-302">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="11e5a-303">입력 `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-303">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="11e5a-304">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-304">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="11e5a-305">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-305">ShellBackwardKillWord</span></span>

<span data-ttu-id="11e5a-306">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-306">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="11e5a-307">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-307">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="11e5a-308">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-308">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="11e5a-309">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-309">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="11e5a-310">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-310">ShellKillWord</span></span>

<span data-ttu-id="11e5a-311">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-311">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="11e5a-312">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-312">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="11e5a-313">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-313">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="11e5a-314">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-314">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="11e5a-315">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="11e5a-315">SwapCharacters</span></span>

<span data-ttu-id="11e5a-316">현재 문자와 그 앞의 문자를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-316">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="11e5a-317">Emacs `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-317">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="11e5a-318">Vi 삽입 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-318">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="11e5a-319">Vi 명령 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-319">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="11e5a-320">실행 취소</span><span class="sxs-lookup"><span data-stu-id="11e5a-320">Undo</span></span>

<span data-ttu-id="11e5a-321">이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-321">Undo a previous edit.</span></span>

- <span data-ttu-id="11e5a-322">입력 `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-322">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="11e5a-323">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-323">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="11e5a-324">Vi 삽입 모드: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-324">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="11e5a-325">Vi 명령 모드: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-325">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="11e5a-326">모두를</span><span class="sxs-lookup"><span data-stu-id="11e5a-326">UndoAll</span></span>

<span data-ttu-id="11e5a-327">줄의 모든 이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-327">Undo all previous edits for line.</span></span>

- <span data-ttu-id="11e5a-328">Vi 명령 모드: `<U>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-328">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="11e5a-329">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="11e5a-329">UnixWordRubout</span></span>

<span data-ttu-id="11e5a-330">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-330">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="11e5a-331">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-331">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="11e5a-332">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-332">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="11e5a-333">Emacs `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-333">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="11e5a-334">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-334">ValidateAndAcceptLine</span></span>

<span data-ttu-id="11e5a-335">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-335">Attempt to execute the current input.</span></span> <span data-ttu-id="11e5a-336">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-336">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="11e5a-337">Emacs `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-337">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="11e5a-338">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-338">ViAcceptLine</span></span>

<span data-ttu-id="11e5a-339">줄을 적용 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-339">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="11e5a-340">Vi 명령 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-340">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="11e5a-341">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="11e5a-341">ViAcceptLineOrExit</span></span>

<span data-ttu-id="11e5a-342">Emacs 모드에서 DeleteCharOrExit와 비슷하지만 문자를 삭제 하는 대신 줄을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-342">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="11e5a-343">Vi 삽입 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-343">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="11e5a-344">Vi 명령 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-344">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="11e5a-345">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-345">ViAppendLine</span></span>

<span data-ttu-id="11e5a-346">현재 줄 아래에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-346">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="11e5a-347">Vi 명령 모드: `<o>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-347">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="11e5a-348">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-348">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="11e5a-349">공백을 단어 구분 기호로 사용 하 여 이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-349">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="11e5a-350">Vi 명령 모드: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-350">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="11e5a-351">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-351">ViBackwardGlob</span></span>

<span data-ttu-id="11e5a-352">공백을 구분 기호로 사용 하 여 커서를 이전 단어의 시작 부분으로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-352">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="11e5a-353">Vi 명령 모드: `<B>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-353">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="11e5a-354">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="11e5a-354">ViDeleteBrace</span></span>

<span data-ttu-id="11e5a-355">괄호를 포함 하 여 일치 하는 중괄호, 괄호 또는 대괄호를 찾아 내에서 모든 내용을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-355">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="11e5a-356">Vi 명령 모드: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-356">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="11e5a-357">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-357">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="11e5a-358">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-358">Delete to the end of the word.</span></span>

- <span data-ttu-id="11e5a-359">Vi 명령 모드: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-359">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="11e5a-360">Videletlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-360">ViDeleteGlob</span></span>

<span data-ttu-id="11e5a-361">다음 glob (공백으로 구분 된 단어)를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-361">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="11e5a-362">Vi 명령 모드: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-362">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="11e5a-363">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-363">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="11e5a-364">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-364">Deletes until given character.</span></span>

- <span data-ttu-id="11e5a-365">Vi 명령 모드: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-365">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="11e5a-366">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="11e5a-366">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="11e5a-367">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-367">Deletes until given character.</span></span>

- <span data-ttu-id="11e5a-368">Vi 명령 모드: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-368">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="11e5a-369">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-369">ViDeleteToChar</span></span>

<span data-ttu-id="11e5a-370">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-370">Deletes until given character.</span></span>

- <span data-ttu-id="11e5a-371">Vi 명령 모드: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-371">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="11e5a-372">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="11e5a-372">ViDeleteToCharBackward</span></span>

<span data-ttu-id="11e5a-373">지정 된 문자까지 뒤로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-373">Deletes backwards until given character.</span></span>

- <span data-ttu-id="11e5a-374">Vi 명령 모드: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-374">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="11e5a-375">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="11e5a-375">ViInsertAtBegining</span></span>

<span data-ttu-id="11e5a-376">삽입 모드로 전환 하 고 줄의 시작 부분에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-376">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="11e5a-377">Vi 명령 모드: `<I>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-377">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="11e5a-378">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="11e5a-378">ViInsertAtEnd</span></span>

<span data-ttu-id="11e5a-379">삽입 모드로 전환 하 고 줄의 끝에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-379">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="11e5a-380">Vi 명령 모드: `<A>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-380">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="11e5a-381">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-381">ViInsertLine</span></span>

<span data-ttu-id="11e5a-382">현재 줄 위에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-382">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="11e5a-383">Vi 명령 모드: `<O>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-383">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="11e5a-384">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="11e5a-384">ViInsertWithAppend</span></span>

<span data-ttu-id="11e5a-385">현재 줄 위치에서 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-385">Append from the current line position.</span></span>

- <span data-ttu-id="11e5a-386">Vi 명령 모드: `<a>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-386">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="11e5a-387">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="11e5a-387">ViInsertWithDelete</span></span>

<span data-ttu-id="11e5a-388">현재 문자를 삭제 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-388">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="11e5a-389">Vi 명령 모드: `<s>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-389">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="11e5a-390">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="11e5a-390">ViJoinLines</span></span>

<span data-ttu-id="11e5a-391">현재 줄과 다음 줄을 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-391">Joins the current line and the next line.</span></span>

- <span data-ttu-id="11e5a-392">Vi 명령 모드: `<J>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-392">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="11e5a-393">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-393">ViReplaceLine</span></span>

<span data-ttu-id="11e5a-394">전체 명령줄을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-394">Erase the entire command line.</span></span>

- <span data-ttu-id="11e5a-395">Vi 명령 모드: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-395">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="11e5a-396">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-396">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="11e5a-397">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-397">Replaces until given character.</span></span>

- <span data-ttu-id="11e5a-398">Vi 명령 모드: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-398">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="11e5a-399">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="11e5a-399">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="11e5a-400">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-400">Replaces until given character.</span></span>

- <span data-ttu-id="11e5a-401">Vi 명령 모드: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-401">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="11e5a-402">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-402">ViReplaceToChar</span></span>

<span data-ttu-id="11e5a-403">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-403">Deletes until given character.</span></span>

- <span data-ttu-id="11e5a-404">Vi 명령 모드: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-404">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="11e5a-405">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="11e5a-405">ViReplaceToCharBackward</span></span>

<span data-ttu-id="11e5a-406">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-406">Replaces until given character.</span></span>

- <span data-ttu-id="11e5a-407">Vi 명령 모드: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-407">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="11e5a-408">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-408">ViYankBeginningOfLine</span></span>

<span data-ttu-id="11e5a-409">버퍼의 시작 부분에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="11e5a-409">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="11e5a-410">Vi 명령 모드: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-410">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="11e5a-411">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-411">ViYankEndOfGlob</span></span>

<span data-ttu-id="11e5a-412">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-412">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="11e5a-413">Vi 명령 모드: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-413">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="11e5a-414">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-414">ViYankEndOfWord</span></span>

<span data-ttu-id="11e5a-415">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-415">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="11e5a-416">Vi 명령 모드: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-416">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="11e5a-417">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="11e5a-417">ViYankLeft</span></span>

<span data-ttu-id="11e5a-418">커서의 왼쪽에 문자를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-418">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="11e5a-419">Vi 명령 모드: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-419">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="11e5a-420">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-420">ViYankLine</span></span>

<span data-ttu-id="11e5a-421">전체 버퍼를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-421">Yank the entire buffer.</span></span>

- <span data-ttu-id="11e5a-422">Vi 명령 모드: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-422">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="11e5a-423">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-423">ViYankNextGlob</span></span>

<span data-ttu-id="11e5a-424">커서에서 다음 단어의 시작 부분으로 Yank.</span><span class="sxs-lookup"><span data-stu-id="11e5a-424">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="11e5a-425">Vi 명령 모드: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-425">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="11e5a-426">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-426">ViYankNextWord</span></span>

<span data-ttu-id="11e5a-427">커서 뒤의 단어를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-427">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="11e5a-428">Vi 명령 모드: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-428">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="11e5a-429">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="11e5a-429">ViYankPercent</span></span>

<span data-ttu-id="11e5a-430">짝이 되는 중괄호에서 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-430">Yank to/from matching brace.</span></span>

- <span data-ttu-id="11e5a-431">Vi 명령 모드: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-431">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="11e5a-432">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-432">ViYankPreviousGlob</span></span>

<span data-ttu-id="11e5a-433">단어의 시작부터 커서까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-433">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="11e5a-434">Vi 명령 모드: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-434">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="11e5a-435">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-435">ViYankPreviousWord</span></span>

<span data-ttu-id="11e5a-436">커서 앞에 단어를 Yank.</span><span class="sxs-lookup"><span data-stu-id="11e5a-436">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="11e5a-437">Vi 명령 모드: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-437">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="11e5a-438">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="11e5a-438">ViYankRight</span></span>

<span data-ttu-id="11e5a-439">커서 오른쪽의 및 아래에 Yank 문자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-439">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="11e5a-440">Vi 명령 모드: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-440">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="11e5a-441">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-441">ViYankToEndOfLine</span></span>

<span data-ttu-id="11e5a-442">커서에서 버퍼 끝까지 Yank.</span><span class="sxs-lookup"><span data-stu-id="11e5a-442">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="11e5a-443">Vi 명령 모드: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-443">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="11e5a-444">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-444">ViYankToFirstChar</span></span>

<span data-ttu-id="11e5a-445">공백이 아닌 첫 번째 문자에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="11e5a-445">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="11e5a-446">Vi 명령 모드: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-446">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="11e5a-447">Yank</span><span class="sxs-lookup"><span data-stu-id="11e5a-447">Yank</span></span>

<span data-ttu-id="11e5a-448">가장 최근에 종료 된 텍스트를 입력에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-448">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="11e5a-449">Emacs `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-449">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="11e5a-450">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="11e5a-450">YankLastArg</span></span>

<span data-ttu-id="11e5a-451">이전 기록 줄에서 마지막 인수를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-451">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="11e5a-452">인수를 사용 하면 처음 호출 될 때 YankNthArg 처럼 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-452">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="11e5a-453">여러 번 호출 된 경우에는 기록 및 인수에서 방향을 설정 합니다. (음수는 방향을 반대로 바꿉니다.)</span><span class="sxs-lookup"><span data-stu-id="11e5a-453">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="11e5a-454">입력 `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-454">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="11e5a-455">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-455">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="11e5a-456">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="11e5a-456">YankNthArg</span></span>

<span data-ttu-id="11e5a-457">이전 기록 줄에서 첫 번째 인수 (명령 뒤)를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-457">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="11e5a-458">인수를 사용 하는 경우 n 번째 인수 (0부터 시작)를 yank. 인수가 음수 이면 마지막 인수부터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-458">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="11e5a-459">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-459">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="11e5a-460">YankPop</span><span class="sxs-lookup"><span data-stu-id="11e5a-460">YankPop</span></span>

<span data-ttu-id="11e5a-461">이전 작업이 Yank 또는 YankPop 인 경우 이전 빼낼 텍스트를 kill 링에서 다음에 종료 된 텍스트로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-461">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="11e5a-462">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-462">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="11e5a-463">커서 이동 함수</span><span class="sxs-lookup"><span data-stu-id="11e5a-463">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="11e5a-464">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-464">BackwardChar</span></span>

<span data-ttu-id="11e5a-465">커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-465">Move the cursor one character to the left.</span></span> <span data-ttu-id="11e5a-466">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-466">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="11e5a-467">입력 `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-467">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="11e5a-468">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-468">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="11e5a-469">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-469">BackwardWord</span></span>

<span data-ttu-id="11e5a-470">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-470">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="11e5a-471">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-471">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="11e5a-472">입력 `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-472">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="11e5a-473">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-473">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="11e5a-474">Vi 삽입 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-474">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="11e5a-475">Vi 명령 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-475">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="11e5a-476">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-476">BeginningOfLine</span></span>

<span data-ttu-id="11e5a-477">입력에 여러 줄이 있는 경우 현재 줄의 시작 부분으로 이동 하거나 이미 줄의 시작 부분에 있는 경우 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-477">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="11e5a-478">입력에 한 줄이 있으면 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-478">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="11e5a-479">입력 `<Home>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-479">Cmd: `<Home>`</span></span>
- <span data-ttu-id="11e5a-480">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-480">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="11e5a-481">Vi 삽입 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-481">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="11e5a-482">Vi 명령 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-482">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="11e5a-483">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-483">EndOfLine</span></span>

<span data-ttu-id="11e5a-484">입력에 여러 줄이 있는 경우 현재 줄의 끝으로 이동 하거나 줄의 끝에 있는 경우 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-484">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="11e5a-485">입력에 한 줄이 있으면 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-485">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="11e5a-486">입력 `<End>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-486">Cmd: `<End>`</span></span>
- <span data-ttu-id="11e5a-487">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-487">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="11e5a-488">Vi 삽입 모드: `<End>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-488">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="11e5a-489">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-489">ForwardChar</span></span>

<span data-ttu-id="11e5a-490">커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-490">Move the cursor one character to the right.</span></span> <span data-ttu-id="11e5a-491">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-491">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="11e5a-492">입력 `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-492">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="11e5a-493">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-493">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="11e5a-494">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-494">ForwardWord</span></span>

<span data-ttu-id="11e5a-495">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="11e5a-496">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="11e5a-497">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-497">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="11e5a-498">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="11e5a-498">GotoBrace</span></span>

<span data-ttu-id="11e5a-499">짝이 되는 중괄호, 괄호 또는 대괄호로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-499">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="11e5a-500">입력 `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-500">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="11e5a-501">Vi 삽입 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-501">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="11e5a-502">Vi 명령 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-502">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="11e5a-503">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="11e5a-503">GotoColumn</span></span>

<span data-ttu-id="11e5a-504">Arg로 표시 된 열로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-504">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="11e5a-505">Vi 명령 모드: `<|>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-505">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="11e5a-506">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-506">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="11e5a-507">줄에서 비어 있지 않은 첫 번째 문자로 커서를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-507">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="11e5a-508">Vi 명령 모드: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-508">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="11e5a-509">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-509">MoveToEndOfLine</span></span>

<span data-ttu-id="11e5a-510">커서를 입력 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-510">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="11e5a-511">Vi 명령 모드: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-511">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="11e5a-512">NextLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-512">NextLine</span></span>

<span data-ttu-id="11e5a-513">커서를 다음 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-513">Move the cursor to the next line.</span></span>

- <span data-ttu-id="11e5a-514">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-514">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="11e5a-515">NextWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-515">NextWord</span></span>

<span data-ttu-id="11e5a-516">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-516">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="11e5a-517">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-517">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="11e5a-518">입력 `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-518">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="11e5a-519">Vi 삽입 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-519">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="11e5a-520">Vi 명령 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-520">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="11e5a-521">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="11e5a-521">NextWordEnd</span></span>

<span data-ttu-id="11e5a-522">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="11e5a-523">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-523">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="11e5a-524">Vi 명령 모드: `<e>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-524">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="11e5a-525">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-525">PreviousLine</span></span>

<span data-ttu-id="11e5a-526">커서를 이전 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-526">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="11e5a-527">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-527">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="11e5a-528">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-528">ShellBackwardWord</span></span>

<span data-ttu-id="11e5a-529">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-529">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="11e5a-530">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-530">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="11e5a-531">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-531">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="11e5a-532">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-532">ShellForwardWord</span></span>

<span data-ttu-id="11e5a-533">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-533">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="11e5a-534">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-534">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="11e5a-535">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-535">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="11e5a-536">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-536">ShellNextWord</span></span>

<span data-ttu-id="11e5a-537">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-537">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="11e5a-538">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-538">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="11e5a-539">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-539">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="11e5a-540">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-540">ViBackwardChar</span></span>

<span data-ttu-id="11e5a-541">Vi 편집 모드에서 커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-541">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="11e5a-542">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-542">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="11e5a-543">Vi 삽입 모드: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-543">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="11e5a-544">Vi 명령 모드: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-544">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="11e5a-545">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-545">ViBackwardWord</span></span>

<span data-ttu-id="11e5a-546">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-546">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="11e5a-547">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-547">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="11e5a-548">Vi 명령 모드: `<b>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-548">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="11e5a-549">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-549">ViForwardChar</span></span>

<span data-ttu-id="11e5a-550">Vi 편집 모드에서 커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-550">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="11e5a-551">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-551">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="11e5a-552">Vi 삽입 모드: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-552">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="11e5a-553">Vi 명령 모드: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-553">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="11e5a-554">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-554">ViEndOfGlob</span></span>

<span data-ttu-id="11e5a-555">공백을 구분 기호로 사용 하 여 커서를 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-555">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="11e5a-556">Vi 명령 모드: `<E>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-556">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="11e5a-557">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-557">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="11e5a-558">공백을 단어 구분 기호로 사용 하 여 이전 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-558">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="11e5a-559">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-559">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="11e5a-560">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="11e5a-560">ViGotoBrace</span></span>

<span data-ttu-id="11e5a-561">GotoBrace와 비슷하지만 토큰 기반이 아니라 문자 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-561">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="11e5a-562">Vi 명령 모드: `<%>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-562">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="11e5a-563">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="11e5a-563">ViNextGlob</span></span>

<span data-ttu-id="11e5a-564">공백을 단어 구분 기호로 사용 하 여 다음 단어로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-564">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="11e5a-565">Vi 명령 모드: `<W>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-565">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="11e5a-566">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-566">ViNextWord</span></span>

<span data-ttu-id="11e5a-567">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-567">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="11e5a-568">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-568">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="11e5a-569">Vi 명령 모드: `<w>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-569">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="11e5a-570">기록 함수</span><span class="sxs-lookup"><span data-stu-id="11e5a-570">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="11e5a-571">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="11e5a-571">BeginningOfHistory</span></span>

<span data-ttu-id="11e5a-572">기록의 첫 번째 항목으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-572">Move to the first item in the history.</span></span>

- <span data-ttu-id="11e5a-573">Emacs `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-573">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="11e5a-574">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="11e5a-574">ClearHistory</span></span>

<span data-ttu-id="11e5a-575">PSReadLine에서 기록을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-575">Clears history in PSReadLine.</span></span> <span data-ttu-id="11e5a-576">PowerShell 기록에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-576">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="11e5a-577">입력 `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-577">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="11e5a-578">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="11e5a-578">EndOfHistory</span></span>

<span data-ttu-id="11e5a-579">기록에서 마지막 항목 (현재 입력)으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-579">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="11e5a-580">Emacs `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-580">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="11e5a-581">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="11e5a-581">ForwardSearchHistory</span></span>

<span data-ttu-id="11e5a-582">기록을 통해 증분 전달 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-582">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="11e5a-583">입력 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-583">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="11e5a-584">Emacs `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-584">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="11e5a-585">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="11e5a-585">HistorySearchBackward</span></span>

<span data-ttu-id="11e5a-586">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-586">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="11e5a-587">입력 `<F8>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-587">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="11e5a-588">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="11e5a-588">HistorySearchForward</span></span>

<span data-ttu-id="11e5a-589">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-589">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="11e5a-590">입력 `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-590">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="11e5a-591">NextHistory</span><span class="sxs-lookup"><span data-stu-id="11e5a-591">NextHistory</span></span>

<span data-ttu-id="11e5a-592">현재 입력을 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-592">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="11e5a-593">입력 `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-593">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="11e5a-594">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-594">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="11e5a-595">Vi 삽입 모드: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-595">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="11e5a-596">Vi 명령 모드: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-596">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="11e5a-597">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="11e5a-597">PreviousHistory</span></span>

<span data-ttu-id="11e5a-598">현재 입력을 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-598">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="11e5a-599">입력 `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-599">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="11e5a-600">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-600">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="11e5a-601">Vi 삽입 모드: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-601">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="11e5a-602">Vi 명령 모드: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="11e5a-602">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="11e5a-603">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="11e5a-603">ReverseSearchHistory</span></span>

<span data-ttu-id="11e5a-604">기록을 통해 증분 역방향 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-604">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="11e5a-605">입력 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-605">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="11e5a-606">Emacs `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-606">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="11e5a-607">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="11e5a-607">ViSearchHistoryBackward</span></span>

<span data-ttu-id="11e5a-608">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-608">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="11e5a-609">Vi 삽입 모드: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-609">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="11e5a-610">Vi 명령 모드: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-610">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="11e5a-611">완료 함수</span><span class="sxs-lookup"><span data-stu-id="11e5a-611">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="11e5a-612">완료</span><span class="sxs-lookup"><span data-stu-id="11e5a-612">Complete</span></span>

<span data-ttu-id="11e5a-613">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-613">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="11e5a-614">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-614">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="11e5a-615">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-615">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="11e5a-616">Emacs `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-616">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="11e5a-617">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="11e5a-617">MenuComplete</span></span>

<span data-ttu-id="11e5a-618">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-618">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="11e5a-619">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-619">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="11e5a-620">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-620">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="11e5a-621">Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-621">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="11e5a-622">Emacs `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-622">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="11e5a-623">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="11e5a-623">PossibleCompletions</span></span>

<span data-ttu-id="11e5a-624">가능한 완료 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-624">Display the list of possible completions.</span></span>

- <span data-ttu-id="11e5a-625">Emacs `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-625">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="11e5a-626">Vi 삽입 모드: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-626">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="11e5a-627">Vi 명령 모드: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-627">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="11e5a-628">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="11e5a-628">TabCompleteNext</span></span>

<span data-ttu-id="11e5a-629">다음에 사용 가능한 완료로 커서를 둘러싼 텍스트를 완성 해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-629">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="11e5a-630">입력 `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-630">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="11e5a-631">Vi 명령 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-631">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="11e5a-632">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="11e5a-632">TabCompletePrevious</span></span>

<span data-ttu-id="11e5a-633">이전에 사용 가능한 완료를 사용 하 여 커서를 둘러싼 텍스트를 완료 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-633">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="11e5a-634">입력 `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-634">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="11e5a-635">Vi 명령 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-635">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="11e5a-636">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="11e5a-636">ViTabCompleteNext</span></span>

<span data-ttu-id="11e5a-637">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompleteNext를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-637">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="11e5a-638">Vi 삽입 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-638">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="11e5a-639">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="11e5a-639">ViTabCompletePrevious</span></span>

<span data-ttu-id="11e5a-640">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompletePrevious를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-640">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="11e5a-641">Vi 삽입 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-641">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="11e5a-642">기타 함수</span><span class="sxs-lookup"><span data-stu-id="11e5a-642">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="11e5a-643">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-643">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="11e5a-644">인라인 또는 선택한 제안의 다음 단어를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-644">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="11e5a-645">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-645">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="11e5a-646">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="11e5a-646">AcceptSuggestion</span></span>

<span data-ttu-id="11e5a-647">현재 인라인 또는 선택한 제안에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-647">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="11e5a-648">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-648">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="11e5a-649">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="11e5a-649">CaptureScreen</span></span>

<span data-ttu-id="11e5a-650">대화형 화면 캡처 시작-위쪽/아래쪽 화살표 선 선택, 선택한 텍스트를 클립보드에 텍스트 및 html로 복사를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-650">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="11e5a-651">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-651">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="11e5a-652">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="11e5a-652">ClearScreen</span></span>

<span data-ttu-id="11e5a-653">화면을 지우고 화면 위쪽에 현재 줄을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-653">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="11e5a-654">입력 `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-654">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="11e5a-655">Emacs `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-655">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="11e5a-656">Vi 삽입 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-656">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="11e5a-657">Vi 명령 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-657">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="11e5a-658">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="11e5a-658">DigitArgument</span></span>

<span data-ttu-id="11e5a-659">다른 함수에 전달할 새 숫자 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-659">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="11e5a-660">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="11e5a-660">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="11e5a-661">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="11e5a-661">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="11e5a-662">Vi 명령 모드: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` `<7>` `<8>` ,,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-662">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="11e5a-663">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="11e5a-663">InvokePrompt</span></span>

<span data-ttu-id="11e5a-664">현재 프롬프트를 지우고 prompt 함수를 호출 하 여 프롬프트를 다시 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-664">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="11e5a-665">상태를 변경 하는 사용자 지정 키 처리기 (예: 현재 디렉터리 변경)에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-665">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="11e5a-666">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-666">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="11e5a-667">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="11e5a-667">ScrollDisplayDown</span></span>

<span data-ttu-id="11e5a-668">한 화면 아래로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-668">Scroll the display down one screen.</span></span>

- <span data-ttu-id="11e5a-669">입력 `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-669">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="11e5a-670">Emacs `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-670">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="11e5a-671">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-671">ScrollDisplayDownLine</span></span>

<span data-ttu-id="11e5a-672">표시를 한 줄 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-672">Scroll the display down one line.</span></span>

- <span data-ttu-id="11e5a-673">입력 `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-673">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="11e5a-674">Emacs `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-674">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="11e5a-675">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="11e5a-675">ScrollDisplayToCursor</span></span>

<span data-ttu-id="11e5a-676">표시를 커서로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-676">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="11e5a-677">Emacs `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-677">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="11e5a-678">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="11e5a-678">ScrollDisplayTop</span></span>

<span data-ttu-id="11e5a-679">표시를 맨 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-679">Scroll the display to the top.</span></span>

- <span data-ttu-id="11e5a-680">Emacs `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-680">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="11e5a-681">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="11e5a-681">ScrollDisplayUp</span></span>

<span data-ttu-id="11e5a-682">한 화면 위로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-682">Scroll the display up one screen.</span></span>

- <span data-ttu-id="11e5a-683">입력 `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-683">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="11e5a-684">Emacs `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-684">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="11e5a-685">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-685">ScrollDisplayUpLine</span></span>

<span data-ttu-id="11e5a-686">디스플레이를 한 줄 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-686">Scroll the display up one line.</span></span>

- <span data-ttu-id="11e5a-687">입력 `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-687">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="11e5a-688">Emacs `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-688">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="11e5a-689">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="11e5a-689">SelfInsert</span></span>

<span data-ttu-id="11e5a-690">키를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-690">Insert the key.</span></span>

- <span data-ttu-id="11e5a-691">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-691">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="11e5a-692">ShowKeyBindings 바인딩</span><span class="sxs-lookup"><span data-stu-id="11e5a-692">ShowKeyBindings</span></span>

<span data-ttu-id="11e5a-693">모든 바인딩된 키를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-693">Show all bound keys.</span></span>

- <span data-ttu-id="11e5a-694">입력 `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-694">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="11e5a-695">Emacs `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-695">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="11e5a-696">Vi 삽입 모드: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-696">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="11e5a-697">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="11e5a-697">ViCommandMode</span></span>

<span data-ttu-id="11e5a-698">Vi-Insert에서 현재 운영 모드를 Vi 명령으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-698">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="11e5a-699">Vi 삽입 모드: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-699">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="11e5a-700">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="11e5a-700">ViDigitArgumentInChord</span></span>

<span data-ttu-id="11e5a-701">Vi의 누르는 중 하나에서 다른 함수에 전달할 새 digit 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-701">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="11e5a-702">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-702">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="11e5a-703">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="11e5a-703">ViEditVisually</span></span>

<span data-ttu-id="11e5a-704">$Env: 편집기 또는 $env: 시각적 개체에 지정 된 텍스트 편집기에서 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-704">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="11e5a-705">Emacs `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-705">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="11e5a-706">Vi 명령 모드: `<v>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-706">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="11e5a-707">ViExit</span><span class="sxs-lookup"><span data-stu-id="11e5a-707">ViExit</span></span>

<span data-ttu-id="11e5a-708">셸을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-708">Exits the shell.</span></span>

- <span data-ttu-id="11e5a-709">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-709">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="11e5a-710">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="11e5a-710">ViInsertMode</span></span>

<span data-ttu-id="11e5a-711">삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-711">Switch to Insert mode.</span></span>

- <span data-ttu-id="11e5a-712">Vi 명령 모드: `<i>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-712">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="11e5a-713">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="11e5a-713">WhatIsKey</span></span>

<span data-ttu-id="11e5a-714">키를 읽고 키가 바인딩된 정보를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-714">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="11e5a-715">입력 `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-715">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="11e5a-716">Emacs `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-716">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="11e5a-717">선택 함수</span><span class="sxs-lookup"><span data-stu-id="11e5a-717">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="11e5a-718">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="11e5a-718">ExchangePointAndMark</span></span>

<span data-ttu-id="11e5a-719">커서는 표시 위치에 배치 되 고 표시는 커서의 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-719">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="11e5a-720">Emacs `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-720">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="11e5a-721">SelectAll</span><span class="sxs-lookup"><span data-stu-id="11e5a-721">SelectAll</span></span>

<span data-ttu-id="11e5a-722">전체 줄을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-722">Select the entire line.</span></span>

- <span data-ttu-id="11e5a-723">입력 `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-723">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="11e5a-724">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-724">SelectBackwardChar</span></span>

<span data-ttu-id="11e5a-725">이전 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-725">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="11e5a-726">입력 `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-726">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="11e5a-727">Emacs `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-727">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="11e5a-728">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-728">SelectBackwardsLine</span></span>

<span data-ttu-id="11e5a-729">커서에서 줄의 시작 부분까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-729">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="11e5a-730">입력 `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-730">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="11e5a-731">Emacs `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-731">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="11e5a-732">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-732">SelectBackwardWord</span></span>

<span data-ttu-id="11e5a-733">이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-733">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="11e5a-734">입력 `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-734">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="11e5a-735">Emacs `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-735">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="11e5a-736">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-736">SelectForwardChar</span></span>

<span data-ttu-id="11e5a-737">다음 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-737">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="11e5a-738">입력 `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-738">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="11e5a-739">Emacs `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-739">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="11e5a-740">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-740">SelectForwardWord</span></span>

<span data-ttu-id="11e5a-741">ForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-741">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="11e5a-742">Emacs `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-742">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="11e5a-743">줄을 select</span><span class="sxs-lookup"><span data-stu-id="11e5a-743">SelectLine</span></span>

<span data-ttu-id="11e5a-744">커서에서 줄의 끝까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-744">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="11e5a-745">입력 `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-745">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="11e5a-746">Emacs `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-746">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="11e5a-747">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-747">SelectNextWord</span></span>

<span data-ttu-id="11e5a-748">다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-748">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="11e5a-749">입력 `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-749">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="11e5a-750">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-750">SelectShellBackwardWord</span></span>

<span data-ttu-id="11e5a-751">ShellBackwardWord를 사용 하 여 이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-751">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="11e5a-752">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-752">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="11e5a-753">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-753">SelectShellForwardWord</span></span>

<span data-ttu-id="11e5a-754">ShellForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-754">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="11e5a-755">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-755">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="11e5a-756">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="11e5a-756">SelectShellNextWord</span></span>

<span data-ttu-id="11e5a-757">ShellNextWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-757">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="11e5a-758">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-758">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="11e5a-759">SetMark</span><span class="sxs-lookup"><span data-stu-id="11e5a-759">SetMark</span></span>

<span data-ttu-id="11e5a-760">이후 편집 명령에 사용할 커서의 현재 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-760">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="11e5a-761">Emacs `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-761">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="11e5a-762">예측 IntelliSense 함수</span><span class="sxs-lookup"><span data-stu-id="11e5a-762">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="11e5a-763">이러한 함수를 사용 하려면 예측 IntelliSense를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-763">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="11e5a-764">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="11e5a-764">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="11e5a-765">예측 IntelliSense에서 인라인 제안의 다음 단어를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-765">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="11e5a-766">이 함수 <kbd></kbd> + 는 다음 명령을 실행 하 여 Ctrl<kbd>F</kbd> 를 사용 하 여 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-766">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="11e5a-767">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="11e5a-767">AcceptSuggestion</span></span>

<span data-ttu-id="11e5a-768">커서가 현재 줄의 끝에 있을 때 <kbd>오른쪽 화살표</kbd> 를 눌러 예측 IntelliSense의 현재 인라인 제안을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-768">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="11e5a-769">검색 함수</span><span class="sxs-lookup"><span data-stu-id="11e5a-769">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="11e5a-770">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="11e5a-770">CharacterSearch</span></span>

<span data-ttu-id="11e5a-771">문자를 읽고 그 다음 번에 해당 문자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-771">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="11e5a-772">인수를 지정 하는 경우 n 번째 발생에 대해 앞으로 (음수 이면 뒤로) 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-772">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="11e5a-773">입력 `<F3>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-773">Cmd: `<F3>`</span></span>
- <span data-ttu-id="11e5a-774">Emacs `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-774">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="11e5a-775">Vi 삽입 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-775">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="11e5a-776">Vi 명령 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-776">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="11e5a-777">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="11e5a-777">CharacterSearchBackward</span></span>

<span data-ttu-id="11e5a-778">문자를 읽은 다음 해당 문자의 다음 항목을 뒤로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-778">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="11e5a-779">인수를 지정 하는 경우 n 번째 발생에 대해 뒤로 검색 하거나 음수 이면 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-779">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="11e5a-780">입력 `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-780">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="11e5a-781">Emacs `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-781">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="11e5a-782">Vi 삽입 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-782">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="11e5a-783">Vi 명령 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-783">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="11e5a-784">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="11e5a-784">RepeatLastCharSearch</span></span>

<span data-ttu-id="11e5a-785">마지막으로 기록 된 문자 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-785">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="11e5a-786">Vi 명령 모드: `<;>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-786">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="11e5a-787">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="11e5a-787">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="11e5a-788">마지막으로 기록 된 문자 검색을 반대 방향으로 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-788">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="11e5a-789">Vi 명령 모드: `<,>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-789">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="11e5a-790">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="11e5a-790">RepeatSearch</span></span>

<span data-ttu-id="11e5a-791">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-791">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="11e5a-792">Vi 명령 모드: `<n>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-792">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="11e5a-793">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="11e5a-793">RepeatSearchBackward</span></span>

<span data-ttu-id="11e5a-794">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-794">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="11e5a-795">Vi 명령 모드: `<N>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-795">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="11e5a-796">SearchChar</span><span class="sxs-lookup"><span data-stu-id="11e5a-796">SearchChar</span></span>

<span data-ttu-id="11e5a-797">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-797">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="11e5a-798">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-798">This is for 't' functionality.</span></span>

- <span data-ttu-id="11e5a-799">Vi 명령 모드: `<f>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-799">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="11e5a-800">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="11e5a-800">SearchCharBackward</span></span>

<span data-ttu-id="11e5a-801">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-801">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="11e5a-802">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-802">This is for 'T' functionality.</span></span>

- <span data-ttu-id="11e5a-803">Vi 명령 모드: `<F>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-803">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="11e5a-804">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="11e5a-804">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="11e5a-805">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-805">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="11e5a-806">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-806">This is for 'T' functionality.</span></span>

- <span data-ttu-id="11e5a-807">Vi 명령 모드: `<T>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-807">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="11e5a-808">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="11e5a-808">SearchCharWithBackoff</span></span>

<span data-ttu-id="11e5a-809">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-809">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="11e5a-810">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-810">This is for 't' functionality.</span></span>

- <span data-ttu-id="11e5a-811">Vi 명령 모드: `<t>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-811">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="11e5a-812">SearchForward</span><span class="sxs-lookup"><span data-stu-id="11e5a-812">SearchForward</span></span>

<span data-ttu-id="11e5a-813">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-813">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="11e5a-814">Vi 삽입 모드: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-814">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="11e5a-815">Vi 명령 모드: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="11e5a-815">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="11e5a-816">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="11e5a-816">Custom Key Bindings</span></span>

<span data-ttu-id="11e5a-817">PSReadLine은 cmdlet을 사용 하 여 사용자 지정 키 바인딩을 지원 `Set-PSReadLineKeyHandler` 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-817">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="11e5a-818">대부분의 사용자 지정 키 바인딩은 위의 함수 중 하나를 호출 합니다. 예를 들면</span><span class="sxs-lookup"><span data-stu-id="11e5a-818">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="11e5a-819">ScriptBlock을 키에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-819">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="11e5a-820">ScriptBlock은 필요한 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-820">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="11e5a-821">몇 가지 유용한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-821">Some useful examples include</span></span>

- <span data-ttu-id="11e5a-822">명령줄 편집</span><span class="sxs-lookup"><span data-stu-id="11e5a-822">edit the command line</span></span>
- <span data-ttu-id="11e5a-823">새 창 열기 (예: 도움말)</span><span class="sxs-lookup"><span data-stu-id="11e5a-823">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="11e5a-824">명령줄을 변경 하지 않고 디렉터리를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-824">change directories without changing the command line</span></span>

<span data-ttu-id="11e5a-825">ScriptBlock은 두 개의 인수를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-825">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="11e5a-826">`$key` -사용자 지정 바인딩을 트리거한 키 인 **[ConsoleKeyInfo]** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-826">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="11e5a-827">동일한 ScriptBlock을 여러 키에 바인딩하고 키에 따라 다른 작업을 수행 해야 하는 경우 $key를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-827">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="11e5a-828">많은 사용자 지정 바인딩에서이 인수를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-828">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="11e5a-829">`$arg` -임의의 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-829">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="11e5a-830">가장 자주 사용 되는 정수 인수는 사용자가 키 바인딩 DigitArgument에서 전달 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-830">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="11e5a-831">바인딩에서 인수를 허용 하지 않는 경우에는이 인수를 무시 하는 것이 합리적입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-831">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="11e5a-832">실행 하지 않고 기록에 명령줄을 추가 하는 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-832">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="11e5a-833">이는 작업을 수행 하지 못했지만 이미 입력 한 명령줄을 다시 입력 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-833">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="11e5a-834">PSReadLine 모듈 폴더에 설치 된 파일에서 더 많은 예제를 볼 수 있습니다 `SamplePSReadLineProfile.ps1` .</span><span class="sxs-lookup"><span data-stu-id="11e5a-834">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="11e5a-835">대부분의 키 바인딩은 일부 도우미 함수를 사용 하 여 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-835">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="11e5a-836">이러한 Api는 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-836">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="11e5a-837">사용자 지정 키 바인딩 지원 Api</span><span class="sxs-lookup"><span data-stu-id="11e5a-837">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="11e5a-838">다음 함수는 PSConsoleReadLine에서 공용 이지만 키에 직접 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-838">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="11e5a-839">대부분은 사용자 지정 키 바인딩에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-839">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="11e5a-840">실행 하지 않고 기록에 명령줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-840">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="11e5a-841">Kill 링을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-841">Clear the kill-ring.</span></span>  <span data-ttu-id="11e5a-842">이는 주로 테스트에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-842">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="11e5a-843">시작에서 길이 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-843">Delete length characters from start.</span></span>  <span data-ttu-id="11e5a-844">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-844">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="11e5a-845">사용자 기본 설정에 따라 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-845">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="11e5a-846">이러한 두 함수는 입력 버퍼의 현재 상태에 대 한 유용한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-846">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="11e5a-847">첫 번째는 간단한 경우에 보다 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-847">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="11e5a-848">두 번째는 바인딩에서 Ast를 사용 하 여 더 높은 작업을 수행 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-848">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="11e5a-849">이러한 두 함수는에 사용 됩니다 `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="11e5a-849">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="11e5a-850">첫 번째는 모든 키 바인딩을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-850">The first is used to get all key bindings.</span></span> <span data-ttu-id="11e5a-851">두 번째는 특정 키 바인딩을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-851">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="11e5a-852">이 함수는 Get-PSReadLineOption에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-852">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="11e5a-853">명령줄에 선택 항목이 없으면-1이 시작 및 길이 둘 다에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-853">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="11e5a-854">명령줄에 선택 항목이 있는 경우 선택의 시작 및 길이가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-854">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="11e5a-855">커서에 문자 또는 문자열을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-855">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="11e5a-856">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-856">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="11e5a-857">PSReadLine에 대 한 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-857">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="11e5a-858">재귀를 지원 하지 않으므로 사용자 지정 키 바인딩에는 유용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-858">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="11e5a-859">이 함수는 Remove-PSReadLineKeyHandler에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-859">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="11e5a-860">일부 입력을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-860">Replace some of the input.</span></span> <span data-ttu-id="11e5a-861">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-861">This operation supports undo/redo.</span></span> <span data-ttu-id="11e5a-862">이는 실행 취소의 단일 작업으로 처리 되기 때문에 Delete 뒤에 Insert를 통해 선호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-862">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="11e5a-863">커서를 지정 된 오프셋으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-863">Move the cursor to the given offset.</span></span> <span data-ttu-id="11e5a-864">실행 취소를 위해 커서 이동이 추적 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-864">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="11e5a-865">이 함수는 cmdlet Set-PSReadLineOption에서 사용 되는 도우미 메서드로, 설정을 일시적으로 변경 하려는 사용자 지정 키 바인딩에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-865">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="11e5a-866">이 도우미 메서드는 DigitArgument을 준수 하는 사용자 지정 바인딩에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-866">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="11e5a-867">일반적인 호출은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-867">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="11e5a-868">참고</span><span class="sxs-lookup"><span data-stu-id="11e5a-868">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="11e5a-869">명령 기록</span><span class="sxs-lookup"><span data-stu-id="11e5a-869">Command History</span></span>

<span data-ttu-id="11e5a-870">PSReadLine은 명령줄에서 입력 한 모든 명령 및 데이터를 포함 하는 기록 파일을 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-870">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="11e5a-871">여기에는 암호를 비롯 한 중요 한 데이터가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-871">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="11e5a-872">예를 들어 cmdlet을 사용 하는 경우 `ConvertTo-SecureString` 암호는 일반 텍스트로 기록 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-872">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="11e5a-873">기록 파일은 라는 파일입니다 `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="11e5a-873">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="11e5a-874">Windows 시스템에서 기록 파일은에 저장 됩니다 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="11e5a-874">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="11e5a-875">Windows가 아닌 시스템에서 기록 파일은 또는에 저장 됩니다 `$env:XDG_DATA_HOME/powershell/PSReadLine` `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="11e5a-875">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="11e5a-876">PSReadLine에 영향을 주는 & 피드백</span><span class="sxs-lookup"><span data-stu-id="11e5a-876">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="11e5a-877">GitHub의 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="11e5a-877">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="11e5a-878">GitHub 페이지에서 끌어오기 요청을 제출 하거나 피드백을 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-878">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="11e5a-879">참고 항목</span><span class="sxs-lookup"><span data-stu-id="11e5a-879">See Also</span></span>

<span data-ttu-id="11e5a-880">PSReadLine은 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 라이브러리의 영향을 많이 받습니다.</span><span class="sxs-lookup"><span data-stu-id="11e5a-880">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
