---
description: PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSReadLine 정보
ms.openlocfilehash: 5b59ffcdfb35c2aa10f8e0caf3a3b365c5bcf93e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223690"
---
# <a name="psreadline"></a><span data-ttu-id="8ec54-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="8ec54-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="8ec54-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="8ec54-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="8ec54-107">PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="8ec54-108">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="8ec54-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="8ec54-109">PSReadLine 2.0은 PowerShell 콘솔에 대 한 강력한 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="8ec54-110">이 콘솔은 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-110">It provides:</span></span>

- <span data-ttu-id="8ec54-111">명령줄의 구문 색 지정</span><span class="sxs-lookup"><span data-stu-id="8ec54-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="8ec54-112">구문 오류를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="8ec54-113">더 나은 여러 줄 환경 (편집 및 기록 모두)</span><span class="sxs-lookup"><span data-stu-id="8ec54-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="8ec54-114">사용자 지정 가능한 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="8ec54-114">Customizable key bindings</span></span>
- <span data-ttu-id="8ec54-115">Cmd 및 Emacs 모드</span><span class="sxs-lookup"><span data-stu-id="8ec54-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="8ec54-116">많은 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="8ec54-116">Many configuration options</span></span>
- <span data-ttu-id="8ec54-117">Bash 스타일 완성 (Cmd 모드에서는 선택 사항, Emacs 모드에서는 기본값)</span><span class="sxs-lookup"><span data-stu-id="8ec54-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="8ec54-118">Emacs yank/kill</span><span class="sxs-lookup"><span data-stu-id="8ec54-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="8ec54-119">PowerShell 토큰 기반 "word" 이동 및 중지</span><span class="sxs-lookup"><span data-stu-id="8ec54-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="8ec54-120">다음 함수는 **[PSConsoleReadLine]** 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

> [!NOTE]
> <span data-ttu-id="8ec54-121">PowerShell 7.0부터 PowerShell은 화면 판독기 프로그램이 검색 된 경우 Windows에서 PSReadLine 자동 로드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="8ec54-122">현재 PSReadLine은 화면 판독기에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="8ec54-123">Windows에서 PowerShell 7.0의 기본 렌더링 및 형식이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="8ec54-124">필요한 경우 모듈을 수동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="8ec54-125">기본 편집 함수</span><span class="sxs-lookup"><span data-stu-id="8ec54-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="8ec54-126">중단</span><span class="sxs-lookup"><span data-stu-id="8ec54-126">Abort</span></span>

<span data-ttu-id="8ec54-127">현재 작업을 중단 합니다 (예: 증분 기록 검색).</span><span class="sxs-lookup"><span data-stu-id="8ec54-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="8ec54-128">Emacs `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="8ec54-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="8ec54-129">AcceptAndGetNext</span></span>

<span data-ttu-id="8ec54-130">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-130">Attempt to execute the current input.</span></span> <span data-ttu-id="8ec54-131">실행 될 수 있는 경우 (예: AcceptLine) 다음에 ReadLine이 호출 될 때 기록에서 다음 항목을 회수 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="8ec54-132">Emacs `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="8ec54-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-133">AcceptLine</span></span>

<span data-ttu-id="8ec54-134">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-134">Attempt to execute the current input.</span></span> <span data-ttu-id="8ec54-135">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="8ec54-136">입력 `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="8ec54-137">Emacs `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="8ec54-138">Vi 삽입 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="8ec54-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-139">AddLine</span></span>

<span data-ttu-id="8ec54-140">연속 프롬프트가 다음 줄에 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="8ec54-141">이는 한 줄이 자체적으로 전체 입력 인 경우에도 여러 줄 입력을 단일 명령으로 입력 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="8ec54-142">입력 `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="8ec54-143">Emacs `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="8ec54-144">Vi 삽입 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="8ec54-145">Vi 명령 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="8ec54-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-146">BackwardDeleteChar</span></span>

<span data-ttu-id="8ec54-147">커서 앞에 있는 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="8ec54-148">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="8ec54-149">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="8ec54-150">Vi 삽입 모드: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="8ec54-151">Vi 명령 모드: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="8ec54-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-152">BackwardDeleteLine</span></span>

<span data-ttu-id="8ec54-153">Like BackwardKillLine-점에서 줄의 시작 부분으로 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="8ec54-154">입력 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="8ec54-155">Vi 삽입 모드: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="8ec54-156">Vi 명령 모드: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="8ec54-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-157">BackwardDeleteWord</span></span>

<span data-ttu-id="8ec54-158">이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-158">Deletes the previous word.</span></span>

- <span data-ttu-id="8ec54-159">Vi 명령 모드: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="8ec54-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-160">BackwardKillLine</span></span>

<span data-ttu-id="8ec54-161">커서에 대 한 입력의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="8ec54-162">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="8ec54-163">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="8ec54-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-164">BackwardKillWord</span></span>

<span data-ttu-id="8ec54-165">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="8ec54-166">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="8ec54-167">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="8ec54-168">입력 `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-168">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="8ec54-169">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="8ec54-170">Vi 삽입 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="8ec54-171">Vi 명령 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="8ec54-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-172">CancelLine</span></span>

<span data-ttu-id="8ec54-173">화면에 입력을 그대로 두고 현재 입력을 취소 합니다. 그러나 프롬프트가 다시 계산 되도록 다시 호스트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="8ec54-174">Vi 삽입 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="8ec54-175">Vi 명령 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="8ec54-176">복사</span><span class="sxs-lookup"><span data-stu-id="8ec54-176">Copy</span></span>

<span data-ttu-id="8ec54-177">선택한 영역을 시스템 클립보드에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="8ec54-178">선택 된 지역이 없으면 전체 줄을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="8ec54-179">입력 `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="8ec54-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-180">CopyOrCancelLine</span></span>

<span data-ttu-id="8ec54-181">텍스트를 선택한 경우 클립보드로 복사 하 고, 그렇지 않으면 줄을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="8ec54-182">입력 `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="8ec54-183">Emacs `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="8ec54-184">잘라내기</span><span class="sxs-lookup"><span data-stu-id="8ec54-184">Cut</span></span>

<span data-ttu-id="8ec54-185">삭제 된 텍스트를 시스템 클립보드에 배치 하는 선택한 영역을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="8ec54-186">입력 `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="8ec54-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-187">DeleteChar</span></span>

<span data-ttu-id="8ec54-188">커서 아래의 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="8ec54-189">입력 `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="8ec54-190">Emacs `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="8ec54-191">Vi 삽입 모드: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="8ec54-192">Vi 명령 모드: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="8ec54-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="8ec54-193">DeleteCharOrExit</span></span>

<span data-ttu-id="8ec54-194">커서 아래의 문자를 삭제 하거나, 줄이 비어 있으면 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="8ec54-195">Emacs `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="8ec54-196">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-196">DeleteEndOfWord</span></span>

<span data-ttu-id="8ec54-197">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-197">Delete to the end of the word.</span></span>

- <span data-ttu-id="8ec54-198">Vi 명령 모드: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-198">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="8ec54-199">Deleteline.invoke</span><span class="sxs-lookup"><span data-stu-id="8ec54-199">DeleteLine</span></span>

<span data-ttu-id="8ec54-200">현재 줄을 삭제 하 고 실행 취소를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-200">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="8ec54-201">Vi 명령 모드: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-201">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="8ec54-202">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-202">DeleteLineToFirstChar</span></span>

<span data-ttu-id="8ec54-203">커서에서 줄의 공백이 아닌 첫 번째 문자로 텍스트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-203">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="8ec54-204">Vi 명령 모드: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-204">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="8ec54-205">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="8ec54-205">DeleteToEnd</span></span>

<span data-ttu-id="8ec54-206">줄의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-206">Delete to the end of the line.</span></span>

- <span data-ttu-id="8ec54-207">Vi 명령 모드: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-207">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="8ec54-208">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-208">DeleteWord</span></span>

<span data-ttu-id="8ec54-209">다음 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-209">Delete the next word.</span></span>

- <span data-ttu-id="8ec54-210">Vi 명령 모드: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-210">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="8ec54-211">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-211">ForwardDeleteLine</span></span>

<span data-ttu-id="8ec54-212">Like ForwardKillLine-포인트에서 줄 끝 까지의 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-212">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="8ec54-213">입력 `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-213">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="8ec54-214">Vi 삽입 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-214">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="8ec54-215">Vi 명령 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-215">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="8ec54-216">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="8ec54-216">InsertLineAbove</span></span>

<span data-ttu-id="8ec54-217">현재 줄에 커서가 있는 위치에 관계 없이 새 빈 줄이 현재 줄 위에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-217">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="8ec54-218">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="8ec54-219">입력 `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-219">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="8ec54-220">Insertlinenea</span><span class="sxs-lookup"><span data-stu-id="8ec54-220">InsertLineBelow</span></span>

<span data-ttu-id="8ec54-221">커서가 현재 줄에 있는지 여부에 관계 없이 현재 줄 아래에 빈 줄이 새로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-221">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="8ec54-222">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-222">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="8ec54-223">입력 `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-223">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="8ec54-224">InvertCase</span><span class="sxs-lookup"><span data-stu-id="8ec54-224">InvertCase</span></span>

<span data-ttu-id="8ec54-225">현재 문자의 대/소문자를 반전 하 고 다음으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-225">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="8ec54-226">Vi 명령 모드: `<~>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-226">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="8ec54-227">KillLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-227">KillLine</span></span>

<span data-ttu-id="8ec54-228">입력의 끝 부분까지 커서에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-228">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="8ec54-229">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-229">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="8ec54-230">Emacs `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-230">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="8ec54-231">KillRegion</span><span class="sxs-lookup"><span data-stu-id="8ec54-231">KillRegion</span></span>

<span data-ttu-id="8ec54-232">커서와 표시 사이에 있는 텍스트를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-232">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="8ec54-233">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-233">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="8ec54-234">KillWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-234">KillWord</span></span>

<span data-ttu-id="8ec54-235">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-235">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="8ec54-236">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-236">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="8ec54-237">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-237">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="8ec54-238">입력 `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-238">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="8ec54-239">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-239">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="8ec54-240">Vi 삽입 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-240">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="8ec54-241">Vi 명령 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-241">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="8ec54-242">붙여넣기</span><span class="sxs-lookup"><span data-stu-id="8ec54-242">Paste</span></span>

<span data-ttu-id="8ec54-243">시스템 클립보드에서 텍스트를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-243">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="8ec54-244">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-244">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="8ec54-245">Vi 삽입 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-245">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="8ec54-246">Vi 명령 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-246">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ec54-247">**Paste** 함수를 사용 하는 경우 클립보드 버퍼의 전체 내용이 psreadline의 입력 버퍼에 붙여넣어집니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-247">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="8ec54-248">그런 다음 입력 버퍼가 PowerShell 파서로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-248">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="8ec54-249">콘솔 응용 프로그램의 **마우스 오른쪽 단추 클릭** 붙여넣기 메서드를 사용 하 여 붙여넣은 입력은 입력 버퍼에 한 번에 한 문자씩 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-249">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="8ec54-250">입력 버퍼는 줄 바꿈 문자가 복사 될 때 파서에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-250">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="8ec54-251">따라서 입력은 한 번에 한 줄씩 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-251">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="8ec54-252">붙여넣기 메서드 간의 차이점으로 인해 실행 동작이 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-252">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="8ec54-253">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="8ec54-253">PasteAfter</span></span>

<span data-ttu-id="8ec54-254">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 뒤에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-254">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="8ec54-255">Vi 명령 모드: `<p>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-255">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="8ec54-256">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="8ec54-256">PasteBefore</span></span>

<span data-ttu-id="8ec54-257">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 앞에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-257">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="8ec54-258">Vi 명령 모드: `<P>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-258">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="8ec54-259">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="8ec54-259">PrependAndAccept</span></span>

<span data-ttu-id="8ec54-260">' # ' 앞에를 추가 하 고 줄을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-260">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="8ec54-261">Vi 명령 모드: `<#>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-261">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="8ec54-262">다시 실행</span><span class="sxs-lookup"><span data-stu-id="8ec54-262">Redo</span></span>

<span data-ttu-id="8ec54-263">실행 취소를 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-263">Undo an undo.</span></span>

- <span data-ttu-id="8ec54-264">입력 `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-264">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="8ec54-265">Vi 삽입 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-265">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="8ec54-266">Vi 명령 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-266">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="8ec54-267">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="8ec54-267">RepeatLastCommand</span></span>

<span data-ttu-id="8ec54-268">마지막 텍스트 수정 작업을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-268">Repeat the last text modification.</span></span>

- <span data-ttu-id="8ec54-269">Vi 명령 모드: `<.>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-269">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="8ec54-270">RevertLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-270">RevertLine</span></span>

<span data-ttu-id="8ec54-271">모든 입력을 현재 입력으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-271">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="8ec54-272">입력 `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-272">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="8ec54-273">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-273">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="8ec54-274">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-274">ShellBackwardKillWord</span></span>

<span data-ttu-id="8ec54-275">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-275">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="8ec54-276">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-276">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="8ec54-277">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-277">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="8ec54-278">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-278">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="8ec54-279">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-279">ShellKillWord</span></span>

<span data-ttu-id="8ec54-280">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-280">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="8ec54-281">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-281">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="8ec54-282">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-282">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="8ec54-283">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-283">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="8ec54-284">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="8ec54-284">SwapCharacters</span></span>

<span data-ttu-id="8ec54-285">현재 문자와 그 앞의 문자를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-285">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="8ec54-286">Emacs `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-286">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="8ec54-287">Vi 삽입 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-287">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="8ec54-288">Vi 명령 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-288">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="8ec54-289">실행 취소</span><span class="sxs-lookup"><span data-stu-id="8ec54-289">Undo</span></span>

<span data-ttu-id="8ec54-290">이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-290">Undo a previous edit.</span></span>

- <span data-ttu-id="8ec54-291">입력 `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-291">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="8ec54-292">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-292">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="8ec54-293">Vi 삽입 모드: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-293">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="8ec54-294">Vi 명령 모드: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-294">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="8ec54-295">모두를</span><span class="sxs-lookup"><span data-stu-id="8ec54-295">UndoAll</span></span>

<span data-ttu-id="8ec54-296">줄의 모든 이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-296">Undo all previous edits for line.</span></span>

- <span data-ttu-id="8ec54-297">Vi 명령 모드: `<U>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-297">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="8ec54-298">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="8ec54-298">UnixWordRubout</span></span>

<span data-ttu-id="8ec54-299">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-299">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="8ec54-300">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-300">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="8ec54-301">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-301">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="8ec54-302">Emacs `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-302">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="8ec54-303">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-303">ValidateAndAcceptLine</span></span>

<span data-ttu-id="8ec54-304">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-304">Attempt to execute the current input.</span></span> <span data-ttu-id="8ec54-305">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-305">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="8ec54-306">Emacs `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-306">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="8ec54-307">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-307">ViAcceptLine</span></span>

<span data-ttu-id="8ec54-308">줄을 적용 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-308">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="8ec54-309">Vi 명령 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-309">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="8ec54-310">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="8ec54-310">ViAcceptLineOrExit</span></span>

<span data-ttu-id="8ec54-311">Emacs 모드에서 DeleteCharOrExit와 비슷하지만 문자를 삭제 하는 대신 줄을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-311">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="8ec54-312">Vi 삽입 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-312">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="8ec54-313">Vi 명령 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-313">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="8ec54-314">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-314">ViAppendLine</span></span>

<span data-ttu-id="8ec54-315">현재 줄 아래에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-315">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="8ec54-316">Vi 명령 모드: `<o>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-316">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="8ec54-317">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-317">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="8ec54-318">공백을 단어 구분 기호로 사용 하 여 이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-318">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="8ec54-319">Vi 명령 모드: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-319">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="8ec54-320">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-320">ViBackwardGlob</span></span>

<span data-ttu-id="8ec54-321">공백을 구분 기호로 사용 하 여 커서를 이전 단어의 시작 부분으로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-321">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="8ec54-322">Vi 명령 모드: `<B>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-322">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="8ec54-323">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="8ec54-323">ViDeleteBrace</span></span>

<span data-ttu-id="8ec54-324">괄호를 포함 하 여 일치 하는 중괄호, 괄호 또는 대괄호를 찾아 내에서 모든 내용을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-324">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="8ec54-325">Vi 명령 모드: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-325">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="8ec54-326">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-326">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="8ec54-327">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-327">Delete to the end of the word.</span></span>

- <span data-ttu-id="8ec54-328">Vi 명령 모드: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-328">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="8ec54-329">Videletlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-329">ViDeleteGlob</span></span>

<span data-ttu-id="8ec54-330">다음 glob (공백으로 구분 된 단어)를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-330">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="8ec54-331">Vi 명령 모드: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-331">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="8ec54-332">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-332">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="8ec54-333">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-333">Deletes until given character.</span></span>

- <span data-ttu-id="8ec54-334">Vi 명령 모드: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-334">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="8ec54-335">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="8ec54-335">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="8ec54-336">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-336">Deletes until given character.</span></span>

- <span data-ttu-id="8ec54-337">Vi 명령 모드: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-337">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="8ec54-338">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-338">ViDeleteToChar</span></span>

<span data-ttu-id="8ec54-339">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-339">Deletes until given character.</span></span>

- <span data-ttu-id="8ec54-340">Vi 명령 모드: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-340">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="8ec54-341">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="8ec54-341">ViDeleteToCharBackward</span></span>

<span data-ttu-id="8ec54-342">지정 된 문자까지 뒤로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-342">Deletes backwards until given character.</span></span>

- <span data-ttu-id="8ec54-343">Vi 명령 모드: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-343">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="8ec54-344">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="8ec54-344">ViInsertAtBegining</span></span>

<span data-ttu-id="8ec54-345">삽입 모드로 전환 하 고 줄의 시작 부분에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-345">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="8ec54-346">Vi 명령 모드: `<I>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-346">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="8ec54-347">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="8ec54-347">ViInsertAtEnd</span></span>

<span data-ttu-id="8ec54-348">삽입 모드로 전환 하 고 줄의 끝에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-348">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="8ec54-349">Vi 명령 모드: `<A>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-349">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="8ec54-350">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-350">ViInsertLine</span></span>

<span data-ttu-id="8ec54-351">현재 줄 위에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-351">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="8ec54-352">Vi 명령 모드: `<O>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-352">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="8ec54-353">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="8ec54-353">ViInsertWithAppend</span></span>

<span data-ttu-id="8ec54-354">현재 줄 위치에서 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-354">Append from the current line position.</span></span>

- <span data-ttu-id="8ec54-355">Vi 명령 모드: `<a>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-355">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="8ec54-356">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="8ec54-356">ViInsertWithDelete</span></span>

<span data-ttu-id="8ec54-357">현재 문자를 삭제 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-357">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="8ec54-358">Vi 명령 모드: `<s>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-358">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="8ec54-359">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="8ec54-359">ViJoinLines</span></span>

<span data-ttu-id="8ec54-360">현재 줄과 다음 줄을 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-360">Joins the current line and the next line.</span></span>

- <span data-ttu-id="8ec54-361">Vi 명령 모드: `<J>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-361">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="8ec54-362">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-362">ViReplaceLine</span></span>

<span data-ttu-id="8ec54-363">전체 명령줄을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-363">Erase the entire command line.</span></span>

- <span data-ttu-id="8ec54-364">Vi 명령 모드: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-364">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="8ec54-365">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-365">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="8ec54-366">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-366">Replaces until given character.</span></span>

- <span data-ttu-id="8ec54-367">Vi 명령 모드: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-367">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="8ec54-368">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="8ec54-368">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="8ec54-369">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-369">Replaces until given character.</span></span>

- <span data-ttu-id="8ec54-370">Vi 명령 모드: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-370">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="8ec54-371">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-371">ViReplaceToChar</span></span>

<span data-ttu-id="8ec54-372">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-372">Deletes until given character.</span></span>

- <span data-ttu-id="8ec54-373">Vi 명령 모드: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-373">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="8ec54-374">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="8ec54-374">ViReplaceToCharBackward</span></span>

<span data-ttu-id="8ec54-375">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-375">Replaces until given character.</span></span>

- <span data-ttu-id="8ec54-376">Vi 명령 모드: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-376">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="8ec54-377">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-377">ViYankBeginningOfLine</span></span>

<span data-ttu-id="8ec54-378">버퍼의 시작 부분에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="8ec54-378">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="8ec54-379">Vi 명령 모드: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-379">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="8ec54-380">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-380">ViYankEndOfGlob</span></span>

<span data-ttu-id="8ec54-381">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-381">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="8ec54-382">Vi 명령 모드: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-382">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="8ec54-383">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-383">ViYankEndOfWord</span></span>

<span data-ttu-id="8ec54-384">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-384">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="8ec54-385">Vi 명령 모드: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-385">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="8ec54-386">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="8ec54-386">ViYankLeft</span></span>

<span data-ttu-id="8ec54-387">커서의 왼쪽에 문자를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-387">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="8ec54-388">Vi 명령 모드: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-388">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="8ec54-389">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-389">ViYankLine</span></span>

<span data-ttu-id="8ec54-390">전체 버퍼를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-390">Yank the entire buffer.</span></span>

- <span data-ttu-id="8ec54-391">Vi 명령 모드: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-391">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="8ec54-392">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-392">ViYankNextGlob</span></span>

<span data-ttu-id="8ec54-393">커서에서 다음 단어의 시작 부분으로 Yank.</span><span class="sxs-lookup"><span data-stu-id="8ec54-393">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="8ec54-394">Vi 명령 모드: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-394">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="8ec54-395">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-395">ViYankNextWord</span></span>

<span data-ttu-id="8ec54-396">커서 뒤의 단어를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-396">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="8ec54-397">Vi 명령 모드: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-397">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="8ec54-398">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="8ec54-398">ViYankPercent</span></span>

<span data-ttu-id="8ec54-399">짝이 되는 중괄호에서 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-399">Yank to/from matching brace.</span></span>

- <span data-ttu-id="8ec54-400">Vi 명령 모드: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-400">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="8ec54-401">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-401">ViYankPreviousGlob</span></span>

<span data-ttu-id="8ec54-402">단어의 시작부터 커서까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-402">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="8ec54-403">Vi 명령 모드: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-403">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="8ec54-404">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-404">ViYankPreviousWord</span></span>

<span data-ttu-id="8ec54-405">커서 앞에 단어를 Yank.</span><span class="sxs-lookup"><span data-stu-id="8ec54-405">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="8ec54-406">Vi 명령 모드: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-406">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="8ec54-407">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="8ec54-407">ViYankRight</span></span>

<span data-ttu-id="8ec54-408">커서 오른쪽의 및 아래에 Yank 문자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-408">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="8ec54-409">Vi 명령 모드: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-409">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="8ec54-410">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-410">ViYankToEndOfLine</span></span>

<span data-ttu-id="8ec54-411">커서에서 버퍼 끝까지 Yank.</span><span class="sxs-lookup"><span data-stu-id="8ec54-411">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="8ec54-412">Vi 명령 모드: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-412">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="8ec54-413">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-413">ViYankToFirstChar</span></span>

<span data-ttu-id="8ec54-414">공백이 아닌 첫 번째 문자에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="8ec54-414">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="8ec54-415">Vi 명령 모드: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-415">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="8ec54-416">Yank</span><span class="sxs-lookup"><span data-stu-id="8ec54-416">Yank</span></span>

<span data-ttu-id="8ec54-417">가장 최근에 종료 된 텍스트를 입력에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-417">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="8ec54-418">Emacs `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-418">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="8ec54-419">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="8ec54-419">YankLastArg</span></span>

<span data-ttu-id="8ec54-420">이전 기록 줄에서 마지막 인수를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-420">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="8ec54-421">인수를 사용 하면 처음 호출 될 때 YankNthArg 처럼 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-421">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="8ec54-422">여러 번 호출 된 경우에는 기록 및 인수에서 방향을 설정 합니다. (음수는 방향을 반대로 바꿉니다.)</span><span class="sxs-lookup"><span data-stu-id="8ec54-422">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="8ec54-423">입력 `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-423">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="8ec54-424">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-424">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="8ec54-425">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="8ec54-425">YankNthArg</span></span>

<span data-ttu-id="8ec54-426">이전 기록 줄에서 첫 번째 인수 (명령 뒤)를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-426">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="8ec54-427">인수를 사용 하는 경우 n 번째 인수 (0부터 시작)를 yank. 인수가 음수 이면 마지막 인수부터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-427">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="8ec54-428">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-428">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="8ec54-429">YankPop</span><span class="sxs-lookup"><span data-stu-id="8ec54-429">YankPop</span></span>

<span data-ttu-id="8ec54-430">이전 작업이 Yank 또는 YankPop 인 경우 이전 빼낼 텍스트를 kill 링에서 다음에 종료 된 텍스트로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-430">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="8ec54-431">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-431">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="8ec54-432">커서 이동 함수</span><span class="sxs-lookup"><span data-stu-id="8ec54-432">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="8ec54-433">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-433">BackwardChar</span></span>

<span data-ttu-id="8ec54-434">커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-434">Move the cursor one character to the left.</span></span> <span data-ttu-id="8ec54-435">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-435">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="8ec54-436">입력 `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-436">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="8ec54-437">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-437">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="8ec54-438">Vi 삽입 모드: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-438">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="8ec54-439">Vi 명령 모드: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-439">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="8ec54-440">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-440">BackwardWord</span></span>

<span data-ttu-id="8ec54-441">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-441">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="8ec54-442">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-442">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="8ec54-443">입력 `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-443">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="8ec54-444">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-444">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="8ec54-445">Vi 삽입 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-445">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="8ec54-446">Vi 명령 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-446">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="8ec54-447">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-447">BeginningOfLine</span></span>

<span data-ttu-id="8ec54-448">입력에 여러 줄이 있는 경우 현재 줄의 시작 부분으로 이동 하거나 이미 줄의 시작 부분에 있는 경우 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-448">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="8ec54-449">입력에 한 줄이 있으면 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-449">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="8ec54-450">입력 `<Home>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-450">Cmd: `<Home>`</span></span>
- <span data-ttu-id="8ec54-451">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-451">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="8ec54-452">Vi 삽입 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-452">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="8ec54-453">Vi 명령 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-453">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="8ec54-454">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-454">EndOfLine</span></span>

<span data-ttu-id="8ec54-455">입력에 여러 줄이 있는 경우 현재 줄의 끝으로 이동 하거나 줄의 끝에 있는 경우 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-455">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="8ec54-456">입력에 한 줄이 있으면 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-456">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="8ec54-457">입력 `<End>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-457">Cmd: `<End>`</span></span>
- <span data-ttu-id="8ec54-458">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-458">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="8ec54-459">Vi 삽입 모드: `<End>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-459">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="8ec54-460">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-460">ForwardChar</span></span>

<span data-ttu-id="8ec54-461">커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-461">Move the cursor one character to the right.</span></span> <span data-ttu-id="8ec54-462">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-462">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="8ec54-463">입력 `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-463">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="8ec54-464">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-464">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="8ec54-465">Vi 삽입 모드: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-465">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="8ec54-466">Vi 명령 모드: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-466">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="8ec54-467">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-467">ForwardWord</span></span>

<span data-ttu-id="8ec54-468">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-468">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="8ec54-469">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-469">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="8ec54-470">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-470">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="8ec54-471">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="8ec54-471">GotoBrace</span></span>

<span data-ttu-id="8ec54-472">짝이 되는 중괄호, 괄호 또는 대괄호로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-472">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="8ec54-473">입력 `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-473">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="8ec54-474">Vi 삽입 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-474">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="8ec54-475">Vi 명령 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-475">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="8ec54-476">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="8ec54-476">GotoColumn</span></span>

<span data-ttu-id="8ec54-477">Arg로 표시 된 열로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-477">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="8ec54-478">Vi 명령 모드: `<|>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-478">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="8ec54-479">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-479">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="8ec54-480">줄에서 비어 있지 않은 첫 번째 문자로 커서를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-480">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="8ec54-481">Vi 명령 모드: `<^>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-481">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="8ec54-482">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-482">MoveToEndOfLine</span></span>

<span data-ttu-id="8ec54-483">커서를 입력 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-483">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="8ec54-484">Vi 명령 모드: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-484">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="8ec54-485">NextLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-485">NextLine</span></span>

<span data-ttu-id="8ec54-486">커서를 다음 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-486">Move the cursor to the next line.</span></span>

- <span data-ttu-id="8ec54-487">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-487">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="8ec54-488">NextWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-488">NextWord</span></span>

<span data-ttu-id="8ec54-489">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-489">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="8ec54-490">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-490">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="8ec54-491">입력 `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-491">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="8ec54-492">Vi 삽입 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-492">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="8ec54-493">Vi 명령 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-493">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="8ec54-494">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="8ec54-494">NextWordEnd</span></span>

<span data-ttu-id="8ec54-495">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="8ec54-496">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="8ec54-497">Vi 명령 모드: `<e>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-497">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="8ec54-498">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-498">PreviousLine</span></span>

<span data-ttu-id="8ec54-499">커서를 이전 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-499">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="8ec54-500">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-500">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="8ec54-501">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-501">ShellBackwardWord</span></span>

<span data-ttu-id="8ec54-502">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-502">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="8ec54-503">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="8ec54-504">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-504">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="8ec54-505">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-505">ShellForwardWord</span></span>

<span data-ttu-id="8ec54-506">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-506">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="8ec54-507">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="8ec54-508">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-508">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="8ec54-509">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-509">ShellNextWord</span></span>

<span data-ttu-id="8ec54-510">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-510">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="8ec54-511">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-511">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="8ec54-512">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-512">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="8ec54-513">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-513">ViBackwardWord</span></span>

<span data-ttu-id="8ec54-514">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="8ec54-515">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-515">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="8ec54-516">Vi 명령 모드: `<b>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-516">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="8ec54-517">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-517">ViEndOfGlob</span></span>

<span data-ttu-id="8ec54-518">공백을 구분 기호로 사용 하 여 커서를 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-518">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="8ec54-519">Vi 명령 모드: `<E>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-519">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="8ec54-520">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-520">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="8ec54-521">공백을 단어 구분 기호로 사용 하 여 이전 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-521">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="8ec54-522">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-522">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="8ec54-523">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="8ec54-523">ViGotoBrace</span></span>

<span data-ttu-id="8ec54-524">GotoBrace와 비슷하지만 토큰 기반이 아니라 문자 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-524">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="8ec54-525">Vi 명령 모드: `<%>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-525">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="8ec54-526">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="8ec54-526">ViNextGlob</span></span>

<span data-ttu-id="8ec54-527">공백을 단어 구분 기호로 사용 하 여 다음 단어로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-527">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="8ec54-528">Vi 명령 모드: `<W>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-528">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="8ec54-529">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-529">ViNextWord</span></span>

<span data-ttu-id="8ec54-530">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-530">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="8ec54-531">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-531">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="8ec54-532">Vi 명령 모드: `<w>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-532">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="8ec54-533">기록 함수</span><span class="sxs-lookup"><span data-stu-id="8ec54-533">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="8ec54-534">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="8ec54-534">BeginningOfHistory</span></span>

<span data-ttu-id="8ec54-535">기록의 첫 번째 항목으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-535">Move to the first item in the history.</span></span>

- <span data-ttu-id="8ec54-536">Emacs `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="8ec54-536">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="8ec54-537">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="8ec54-537">ClearHistory</span></span>

<span data-ttu-id="8ec54-538">PSReadLine에서 기록을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-538">Clears history in PSReadLine.</span></span> <span data-ttu-id="8ec54-539">PowerShell 기록에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-539">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="8ec54-540">입력 `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-540">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="8ec54-541">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="8ec54-541">EndOfHistory</span></span>

<span data-ttu-id="8ec54-542">기록에서 마지막 항목 (현재 입력)으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-542">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="8ec54-543">Emacs `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-543">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="8ec54-544">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="8ec54-544">ForwardSearchHistory</span></span>

<span data-ttu-id="8ec54-545">기록을 통해 증분 전달 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-545">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="8ec54-546">입력 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-546">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="8ec54-547">Emacs `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-547">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="8ec54-548">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="8ec54-548">HistorySearchBackward</span></span>

<span data-ttu-id="8ec54-549">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-549">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="8ec54-550">입력 `<F8>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-550">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="8ec54-551">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="8ec54-551">HistorySearchForward</span></span>

<span data-ttu-id="8ec54-552">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-552">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="8ec54-553">입력 `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-553">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="8ec54-554">NextHistory</span><span class="sxs-lookup"><span data-stu-id="8ec54-554">NextHistory</span></span>

<span data-ttu-id="8ec54-555">현재 입력을 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-555">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="8ec54-556">입력 `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-556">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="8ec54-557">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-557">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="8ec54-558">Vi 삽입 모드: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-558">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="8ec54-559">Vi 명령 모드: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-559">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="8ec54-560">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="8ec54-560">PreviousHistory</span></span>

<span data-ttu-id="8ec54-561">현재 입력을 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-561">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="8ec54-562">입력 `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-562">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="8ec54-563">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-563">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="8ec54-564">Vi 삽입 모드: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-564">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="8ec54-565">Vi 명령 모드: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="8ec54-565">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="8ec54-566">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="8ec54-566">ReverseSearchHistory</span></span>

<span data-ttu-id="8ec54-567">기록을 통해 증분 역방향 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-567">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="8ec54-568">입력 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-568">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="8ec54-569">Emacs `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-569">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="8ec54-570">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="8ec54-570">ViSearchHistoryBackward</span></span>

<span data-ttu-id="8ec54-571">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-571">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="8ec54-572">Vi 삽입 모드: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-572">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="8ec54-573">Vi 명령 모드: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-573">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="8ec54-574">완료 함수</span><span class="sxs-lookup"><span data-stu-id="8ec54-574">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="8ec54-575">완료</span><span class="sxs-lookup"><span data-stu-id="8ec54-575">Complete</span></span>

<span data-ttu-id="8ec54-576">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-576">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="8ec54-577">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-577">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="8ec54-578">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-578">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="8ec54-579">Emacs `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-579">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="8ec54-580">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="8ec54-580">MenuComplete</span></span>

<span data-ttu-id="8ec54-581">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-581">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="8ec54-582">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-582">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="8ec54-583">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-583">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="8ec54-584">입력 `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-584">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="8ec54-585">Emacs `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-585">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="8ec54-586">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="8ec54-586">PossibleCompletions</span></span>

<span data-ttu-id="8ec54-587">가능한 완료 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-587">Display the list of possible completions.</span></span>

- <span data-ttu-id="8ec54-588">Emacs `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-588">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="8ec54-589">Vi 삽입 모드: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-589">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="8ec54-590">Vi 명령 모드: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-590">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="8ec54-591">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="8ec54-591">TabCompleteNext</span></span>

<span data-ttu-id="8ec54-592">다음에 사용 가능한 완료로 커서를 둘러싼 텍스트를 완성 해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-592">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="8ec54-593">입력 `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-593">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="8ec54-594">Vi 명령 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-594">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="8ec54-595">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="8ec54-595">TabCompletePrevious</span></span>

<span data-ttu-id="8ec54-596">이전에 사용 가능한 완료를 사용 하 여 커서를 둘러싼 텍스트를 완료 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-596">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="8ec54-597">입력 `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-597">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="8ec54-598">Vi 명령 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-598">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="8ec54-599">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="8ec54-599">ViTabCompleteNext</span></span>

<span data-ttu-id="8ec54-600">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompleteNext를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-600">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="8ec54-601">Vi 삽입 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-601">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="8ec54-602">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="8ec54-602">ViTabCompletePrevious</span></span>

<span data-ttu-id="8ec54-603">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompletePrevious를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-603">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="8ec54-604">Vi 삽입 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-604">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="8ec54-605">기타 함수</span><span class="sxs-lookup"><span data-stu-id="8ec54-605">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="8ec54-606">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="8ec54-606">CaptureScreen</span></span>

<span data-ttu-id="8ec54-607">대화형 화면 캡처 시작-위쪽/아래쪽 화살표 선 선택, 선택한 텍스트를 클립보드에 텍스트 및 html로 복사를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-607">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="8ec54-608">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-608">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="8ec54-609">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="8ec54-609">ClearScreen</span></span>

<span data-ttu-id="8ec54-610">화면을 지우고 화면 위쪽에 현재 줄을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-610">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="8ec54-611">입력 `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-611">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="8ec54-612">Emacs `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-612">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="8ec54-613">Vi 삽입 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-613">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="8ec54-614">Vi 명령 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-614">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="8ec54-615">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="8ec54-615">DigitArgument</span></span>

<span data-ttu-id="8ec54-616">다른 함수에 전달할 새 숫자 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-616">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="8ec54-617">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="8ec54-617">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="8ec54-618">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="8ec54-618">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="8ec54-619">Vi 명령 모드: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` `<7>` `<8>` ,,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-619">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="8ec54-620">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="8ec54-620">InvokePrompt</span></span>

<span data-ttu-id="8ec54-621">현재 프롬프트를 지우고 prompt 함수를 호출 하 여 프롬프트를 다시 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-621">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="8ec54-622">상태를 변경 하는 사용자 지정 키 처리기 (예: 현재 디렉터리 변경)에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-622">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="8ec54-623">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-623">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="8ec54-624">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="8ec54-624">ScrollDisplayDown</span></span>

<span data-ttu-id="8ec54-625">한 화면 아래로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-625">Scroll the display down one screen.</span></span>

- <span data-ttu-id="8ec54-626">입력 `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-626">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="8ec54-627">Emacs `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-627">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="8ec54-628">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-628">ScrollDisplayDownLine</span></span>

<span data-ttu-id="8ec54-629">표시를 한 줄 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-629">Scroll the display down one line.</span></span>

- <span data-ttu-id="8ec54-630">입력 `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-630">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="8ec54-631">Emacs `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-631">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="8ec54-632">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="8ec54-632">ScrollDisplayToCursor</span></span>

<span data-ttu-id="8ec54-633">표시를 커서로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-633">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="8ec54-634">Emacs `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-634">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="8ec54-635">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="8ec54-635">ScrollDisplayTop</span></span>

<span data-ttu-id="8ec54-636">표시를 맨 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-636">Scroll the display to the top.</span></span>

- <span data-ttu-id="8ec54-637">Emacs `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-637">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="8ec54-638">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="8ec54-638">ScrollDisplayUp</span></span>

<span data-ttu-id="8ec54-639">한 화면 위로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-639">Scroll the display up one screen.</span></span>

- <span data-ttu-id="8ec54-640">입력 `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-640">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="8ec54-641">Emacs `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-641">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="8ec54-642">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-642">ScrollDisplayUpLine</span></span>

<span data-ttu-id="8ec54-643">디스플레이를 한 줄 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-643">Scroll the display up one line.</span></span>

- <span data-ttu-id="8ec54-644">입력 `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-644">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="8ec54-645">Emacs `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-645">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="8ec54-646">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="8ec54-646">SelfInsert</span></span>

<span data-ttu-id="8ec54-647">키를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-647">Insert the key.</span></span>

- <span data-ttu-id="8ec54-648">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-648">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="8ec54-649">ShowKeyBindings 바인딩</span><span class="sxs-lookup"><span data-stu-id="8ec54-649">ShowKeyBindings</span></span>

<span data-ttu-id="8ec54-650">모든 바인딩된 키를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-650">Show all bound keys.</span></span>

- <span data-ttu-id="8ec54-651">입력 `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-651">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="8ec54-652">Emacs `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-652">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="8ec54-653">Vi 삽입 모드: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-653">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="8ec54-654">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="8ec54-654">ViCommandMode</span></span>

<span data-ttu-id="8ec54-655">Vi-Insert에서 현재 운영 모드를 Vi 명령으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-655">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="8ec54-656">Vi 삽입 모드: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-656">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="8ec54-657">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="8ec54-657">ViDigitArgumentInChord</span></span>

<span data-ttu-id="8ec54-658">Vi의 누르는 중 하나에서 다른 함수에 전달할 새 digit 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-658">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="8ec54-659">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-659">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="8ec54-660">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="8ec54-660">ViEditVisually</span></span>

<span data-ttu-id="8ec54-661">$Env: 편집기 또는 $env: 시각적 개체에 지정 된 텍스트 편집기에서 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-661">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="8ec54-662">Emacs `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-662">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="8ec54-663">Vi 명령 모드: `<v>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-663">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="8ec54-664">ViExit</span><span class="sxs-lookup"><span data-stu-id="8ec54-664">ViExit</span></span>

<span data-ttu-id="8ec54-665">셸을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-665">Exits the shell.</span></span>

- <span data-ttu-id="8ec54-666">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-666">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="8ec54-667">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="8ec54-667">ViInsertMode</span></span>

<span data-ttu-id="8ec54-668">삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-668">Switch to Insert mode.</span></span>

- <span data-ttu-id="8ec54-669">Vi 명령 모드: `<i>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-669">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="8ec54-670">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="8ec54-670">WhatIsKey</span></span>

<span data-ttu-id="8ec54-671">키를 읽고 키가 바인딩된 정보를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-671">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="8ec54-672">입력 `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-672">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="8ec54-673">Emacs `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-673">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="8ec54-674">선택 함수</span><span class="sxs-lookup"><span data-stu-id="8ec54-674">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="8ec54-675">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="8ec54-675">ExchangePointAndMark</span></span>

<span data-ttu-id="8ec54-676">커서는 표시 위치에 배치 되 고 표시는 커서의 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-676">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="8ec54-677">Emacs `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-677">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="8ec54-678">SelectAll</span><span class="sxs-lookup"><span data-stu-id="8ec54-678">SelectAll</span></span>

<span data-ttu-id="8ec54-679">전체 줄을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-679">Select the entire line.</span></span>

- <span data-ttu-id="8ec54-680">입력 `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-680">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="8ec54-681">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-681">SelectBackwardChar</span></span>

<span data-ttu-id="8ec54-682">이전 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-682">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="8ec54-683">입력 `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-683">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="8ec54-684">Emacs `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-684">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="8ec54-685">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-685">SelectBackwardsLine</span></span>

<span data-ttu-id="8ec54-686">커서에서 줄의 시작 부분까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-686">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="8ec54-687">입력 `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-687">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="8ec54-688">Emacs `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-688">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="8ec54-689">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-689">SelectBackwardWord</span></span>

<span data-ttu-id="8ec54-690">이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-690">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="8ec54-691">입력 `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-691">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="8ec54-692">Emacs `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-692">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="8ec54-693">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-693">SelectForwardChar</span></span>

<span data-ttu-id="8ec54-694">다음 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-694">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="8ec54-695">입력 `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-695">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="8ec54-696">Emacs `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-696">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="8ec54-697">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-697">SelectForwardWord</span></span>

<span data-ttu-id="8ec54-698">ForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-698">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="8ec54-699">Emacs `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-699">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="8ec54-700">줄을 select</span><span class="sxs-lookup"><span data-stu-id="8ec54-700">SelectLine</span></span>

<span data-ttu-id="8ec54-701">커서에서 줄의 끝까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-701">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="8ec54-702">입력 `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-702">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="8ec54-703">Emacs `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-703">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="8ec54-704">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-704">SelectNextWord</span></span>

<span data-ttu-id="8ec54-705">다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-705">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="8ec54-706">입력 `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-706">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="8ec54-707">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-707">SelectShellBackwardWord</span></span>

<span data-ttu-id="8ec54-708">ShellBackwardWord를 사용 하 여 이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-708">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="8ec54-709">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-709">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="8ec54-710">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-710">SelectShellForwardWord</span></span>

<span data-ttu-id="8ec54-711">ShellForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-711">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="8ec54-712">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-712">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="8ec54-713">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="8ec54-713">SelectShellNextWord</span></span>

<span data-ttu-id="8ec54-714">ShellNextWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-714">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="8ec54-715">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-715">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="8ec54-716">SetMark</span><span class="sxs-lookup"><span data-stu-id="8ec54-716">SetMark</span></span>

<span data-ttu-id="8ec54-717">이후 편집 명령에 사용할 커서의 현재 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-717">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="8ec54-718">Emacs `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="8ec54-718">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="8ec54-719">검색 함수</span><span class="sxs-lookup"><span data-stu-id="8ec54-719">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="8ec54-720">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="8ec54-720">CharacterSearch</span></span>

<span data-ttu-id="8ec54-721">문자를 읽고 그 다음 번에 해당 문자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-721">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="8ec54-722">인수를 지정 하는 경우 n 번째 발생에 대해 앞으로 (음수 이면 뒤로) 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-722">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="8ec54-723">입력 `<F3>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-723">Cmd: `<F3>`</span></span>
- <span data-ttu-id="8ec54-724">Emacs `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-724">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="8ec54-725">Vi 삽입 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-725">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="8ec54-726">Vi 명령 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-726">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="8ec54-727">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="8ec54-727">CharacterSearchBackward</span></span>

<span data-ttu-id="8ec54-728">문자를 읽은 다음 해당 문자의 다음 항목을 뒤로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-728">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="8ec54-729">인수를 지정 하는 경우 n 번째 발생에 대해 뒤로 검색 하거나 음수 이면 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-729">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="8ec54-730">입력 `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-730">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="8ec54-731">Emacs `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-731">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="8ec54-732">Vi 삽입 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-732">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="8ec54-733">Vi 명령 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-733">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="8ec54-734">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="8ec54-734">RepeatLastCharSearch</span></span>

<span data-ttu-id="8ec54-735">마지막으로 기록 된 문자 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-735">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="8ec54-736">Vi 명령 모드: `<;>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-736">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="8ec54-737">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="8ec54-737">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="8ec54-738">마지막으로 기록 된 문자 검색을 반대 방향으로 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-738">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="8ec54-739">Vi 명령 모드: `<,>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-739">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="8ec54-740">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="8ec54-740">RepeatSearch</span></span>

<span data-ttu-id="8ec54-741">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-741">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="8ec54-742">Vi 명령 모드: `<n>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-742">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="8ec54-743">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="8ec54-743">RepeatSearchBackward</span></span>

<span data-ttu-id="8ec54-744">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-744">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="8ec54-745">Vi 명령 모드: `<N>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-745">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="8ec54-746">SearchChar</span><span class="sxs-lookup"><span data-stu-id="8ec54-746">SearchChar</span></span>

<span data-ttu-id="8ec54-747">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-747">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="8ec54-748">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-748">This is for 't' functionality.</span></span>

- <span data-ttu-id="8ec54-749">Vi 명령 모드: `<f>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-749">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="8ec54-750">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="8ec54-750">SearchCharBackward</span></span>

<span data-ttu-id="8ec54-751">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="8ec54-752">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="8ec54-753">Vi 명령 모드: `<F>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-753">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="8ec54-754">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="8ec54-754">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="8ec54-755">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-755">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="8ec54-756">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-756">This is for 'T' functionality.</span></span>

- <span data-ttu-id="8ec54-757">Vi 명령 모드: `<T>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-757">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="8ec54-758">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="8ec54-758">SearchCharWithBackoff</span></span>

<span data-ttu-id="8ec54-759">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-759">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="8ec54-760">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-760">This is for 't' functionality.</span></span>

- <span data-ttu-id="8ec54-761">Vi 명령 모드: `<t>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-761">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="8ec54-762">SearchForward</span><span class="sxs-lookup"><span data-stu-id="8ec54-762">SearchForward</span></span>

<span data-ttu-id="8ec54-763">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-763">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="8ec54-764">Vi 삽입 모드: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-764">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="8ec54-765">Vi 명령 모드: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="8ec54-765">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="8ec54-766">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="8ec54-766">Custom Key Bindings</span></span>

<span data-ttu-id="8ec54-767">PSReadLine은 cmdlet을 사용 하 여 사용자 지정 키 바인딩을 지원 `Set-PSReadLineKeyHandler` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-767">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="8ec54-768">대부분의 사용자 지정 키 바인딩은 위의 함수 중 하나를 호출 합니다. 예를 들면</span><span class="sxs-lookup"><span data-stu-id="8ec54-768">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="8ec54-769">ScriptBlock을 키에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-769">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="8ec54-770">ScriptBlock은 필요한 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-770">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="8ec54-771">몇 가지 유용한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-771">Some useful examples include</span></span>

- <span data-ttu-id="8ec54-772">명령줄 편집</span><span class="sxs-lookup"><span data-stu-id="8ec54-772">edit the command line</span></span>
- <span data-ttu-id="8ec54-773">새 창 열기 (예: 도움말)</span><span class="sxs-lookup"><span data-stu-id="8ec54-773">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="8ec54-774">명령줄을 변경 하지 않고 디렉터리를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-774">change directories without changing the command line</span></span>

<span data-ttu-id="8ec54-775">ScriptBlock은 두 개의 인수를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-775">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="8ec54-776">`$key` -사용자 지정 바인딩을 트리거한 키 인 **[ConsoleKeyInfo]** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-776">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="8ec54-777">동일한 ScriptBlock을 여러 키에 바인딩하고 키에 따라 다른 작업을 수행 해야 하는 경우 $key를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-777">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="8ec54-778">많은 사용자 지정 바인딩에서이 인수를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-778">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="8ec54-779">`$arg` -임의의 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-779">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="8ec54-780">가장 자주 사용 되는 정수 인수는 사용자가 키 바인딩 DigitArgument에서 전달 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-780">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="8ec54-781">바인딩에서 인수를 허용 하지 않는 경우에는이 인수를 무시 하는 것이 합리적입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-781">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="8ec54-782">실행 하지 않고 기록에 명령줄을 추가 하는 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-782">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="8ec54-783">이는 작업을 수행 하지 못했지만 이미 입력 한 명령줄을 다시 입력 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-783">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="8ec54-784">PSReadLine 모듈 폴더에 설치 된 파일에서 더 많은 예제를 볼 수 있습니다 `SamplePSReadLineProfile.ps1` .</span><span class="sxs-lookup"><span data-stu-id="8ec54-784">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="8ec54-785">대부분의 키 바인딩은 일부 도우미 함수를 사용 하 여 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-785">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="8ec54-786">이러한 Api는 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-786">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="8ec54-787">사용자 지정 키 바인딩 지원 Api</span><span class="sxs-lookup"><span data-stu-id="8ec54-787">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="8ec54-788">다음 함수는 PSConsoleReadLine에서 공용 이지만 키에 직접 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-788">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="8ec54-789">대부분은 사용자 지정 키 바인딩에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-789">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="8ec54-790">실행 하지 않고 기록에 명령줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-790">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="8ec54-791">Kill 링을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-791">Clear the kill-ring.</span></span>  <span data-ttu-id="8ec54-792">이는 주로 테스트에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-792">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="8ec54-793">시작에서 길이 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-793">Delete length characters from start.</span></span>  <span data-ttu-id="8ec54-794">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-794">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="8ec54-795">사용자 기본 설정에 따라 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-795">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="8ec54-796">이러한 두 함수는 입력 버퍼의 현재 상태에 대 한 유용한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-796">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="8ec54-797">첫 번째는 간단한 경우에 보다 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-797">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="8ec54-798">두 번째는 바인딩에서 Ast를 사용 하 여 더 높은 작업을 수행 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-798">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="8ec54-799">이 함수는 Get-PSReadLineKeyHandler에서 사용 되며 사용자 지정 키 바인딩에서 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-799">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="8ec54-800">이 함수는 Get-PSReadLineOption에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-800">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="8ec54-801">명령줄에 선택 항목이 없으면-1이 시작 및 길이 둘 다에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-801">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="8ec54-802">명령줄에 선택 항목이 있는 경우 선택의 시작 및 길이가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-802">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="8ec54-803">커서에 문자 또는 문자열을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-803">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="8ec54-804">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-804">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="8ec54-805">PSReadLine에 대 한 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-805">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="8ec54-806">재귀를 지원 하지 않으므로 사용자 지정 키 바인딩에는 유용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-806">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="8ec54-807">이 함수는 Remove-PSReadLineKeyHandler에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-807">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="8ec54-808">일부 입력을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-808">Replace some of the input.</span></span> <span data-ttu-id="8ec54-809">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-809">This operation supports undo/redo.</span></span> <span data-ttu-id="8ec54-810">이는 실행 취소의 단일 작업으로 처리 되기 때문에 Delete 뒤에 Insert를 통해 선호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-810">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="8ec54-811">커서를 지정 된 오프셋으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-811">Move the cursor to the given offset.</span></span> <span data-ttu-id="8ec54-812">실행 취소를 위해 커서 이동이 추적 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-812">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="8ec54-813">이 함수는 cmdlet Set-PSReadLineOption에서 사용 되는 도우미 메서드로, 설정을 일시적으로 변경 하려는 사용자 지정 키 바인딩에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-813">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="8ec54-814">이 도우미 메서드는 DigitArgument을 준수 하는 사용자 지정 바인딩에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-814">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="8ec54-815">일반적인 호출은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-815">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="8ec54-816">참고</span><span class="sxs-lookup"><span data-stu-id="8ec54-816">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="8ec54-817">POWERSHELL 호환성</span><span class="sxs-lookup"><span data-stu-id="8ec54-817">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="8ec54-818">PSReadLine에는 PowerShell 3.0 이상 및 콘솔 호스트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-818">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="8ec54-819">PowerShell ISE에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-819">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="8ec54-820">Visual Studio Code 콘솔에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-820">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="8ec54-821">명령 기록</span><span class="sxs-lookup"><span data-stu-id="8ec54-821">COMMAND HISTORY</span></span>

<span data-ttu-id="8ec54-822">PSReadLine은 명령줄에서 입력 한 모든 명령 및 데이터를 포함 하는 기록 파일을 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-822">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="8ec54-823">여기에는 암호를 비롯 한 중요 한 데이터가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-823">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="8ec54-824">예를 들어 cmdlet을 사용 하는 경우 `ConvertTo-SecureString` 암호는 일반 텍스트로 기록 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-824">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="8ec54-825">기록 파일은 라는 파일입니다 `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="8ec54-825">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="8ec54-826">Windows 시스템에서 기록 파일은에 저장 됩니다 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="8ec54-826">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="8ec54-827">Windows가 아닌 시스템에서 기록 파일은 또는에 저장 됩니다 `$env:XDG_DATA_HOME/powershell/PSReadLine` `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="8ec54-827">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="8ec54-828">PSReadLine에 영향을 주는 & 피드백</span><span class="sxs-lookup"><span data-stu-id="8ec54-828">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="8ec54-829">GitHub의 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="8ec54-829">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="8ec54-830">GitHub 페이지에서 끌어오기 요청을 제출 하거나 피드백을 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-830">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ec54-831">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ec54-831">SEE ALSO</span></span>

<span data-ttu-id="8ec54-832">PSReadLine은 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 라이브러리의 영향을 많이 받습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec54-832">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
