---
description: PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSReadLine 정보
ms.openlocfilehash: 1188b8dc0b4099a7c1dcc472e3b02c2d4fa908bc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220809"
---
# <a name="psreadline"></a><span data-ttu-id="80e42-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="80e42-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="80e42-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="80e42-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="80e42-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="80e42-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="80e42-107">PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="80e42-108">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="80e42-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="80e42-109">PSReadLine 2.0은 PowerShell 콘솔에 대 한 강력한 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="80e42-110">이 콘솔은 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-110">It provides:</span></span>

- <span data-ttu-id="80e42-111">명령줄의 구문 색 지정</span><span class="sxs-lookup"><span data-stu-id="80e42-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="80e42-112">구문 오류를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="80e42-113">더 나은 여러 줄 환경 (편집 및 기록 모두)</span><span class="sxs-lookup"><span data-stu-id="80e42-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="80e42-114">사용자 지정 가능한 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="80e42-114">Customizable key bindings</span></span>
- <span data-ttu-id="80e42-115">Cmd 및 Emacs 모드</span><span class="sxs-lookup"><span data-stu-id="80e42-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="80e42-116">많은 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="80e42-116">Many configuration options</span></span>
- <span data-ttu-id="80e42-117">Bash 스타일 완성 (Cmd 모드에서는 선택 사항, Emacs 모드에서는 기본값)</span><span class="sxs-lookup"><span data-stu-id="80e42-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="80e42-118">Emacs yank/kill</span><span class="sxs-lookup"><span data-stu-id="80e42-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="80e42-119">PowerShell 토큰 기반 "word" 이동 및 중지</span><span class="sxs-lookup"><span data-stu-id="80e42-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="80e42-120">다음 함수는 **[PSConsoleReadLine]** 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

> [!NOTE]
> <span data-ttu-id="80e42-121">PowerShell 7.0부터 PowerShell은 화면 판독기 프로그램이 검색 된 경우 Windows에서 PSReadLine 자동 로드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="80e42-122">현재 PSReadLine은 화면 판독기에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="80e42-123">Windows에서 PowerShell 7.0의 기본 렌더링 및 형식이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="80e42-124">필요한 경우 모듈을 수동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="80e42-125">기본 편집 함수</span><span class="sxs-lookup"><span data-stu-id="80e42-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="80e42-126">중단</span><span class="sxs-lookup"><span data-stu-id="80e42-126">Abort</span></span>

<span data-ttu-id="80e42-127">현재 작업을 중단 합니다 (예: 증분 기록 검색).</span><span class="sxs-lookup"><span data-stu-id="80e42-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="80e42-128">Emacs `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="80e42-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="80e42-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="80e42-129">AcceptAndGetNext</span></span>

<span data-ttu-id="80e42-130">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-130">Attempt to execute the current input.</span></span> <span data-ttu-id="80e42-131">실행 될 수 있는 경우 (예: AcceptLine) 다음에 ReadLine이 호출 될 때 기록에서 다음 항목을 회수 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="80e42-132">Emacs `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="80e42-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="80e42-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="80e42-133">AcceptLine</span></span>

<span data-ttu-id="80e42-134">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-134">Attempt to execute the current input.</span></span> <span data-ttu-id="80e42-135">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="80e42-136">입력 `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="80e42-137">Emacs `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="80e42-138">Vi 삽입 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="80e42-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="80e42-139">AddLine</span></span>

<span data-ttu-id="80e42-140">연속 프롬프트가 다음 줄에 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="80e42-141">이는 한 줄이 자체적으로 전체 입력 인 경우에도 여러 줄 입력을 단일 명령으로 입력 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="80e42-142">입력 `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="80e42-143">Emacs `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="80e42-144">Vi 삽입 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="80e42-145">Vi 명령 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="80e42-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="80e42-146">BackwardDeleteChar</span></span>

<span data-ttu-id="80e42-147">커서 앞에 있는 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="80e42-148">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="80e42-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="80e42-149">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="80e42-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="80e42-150">Vi 삽입 모드: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="80e42-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="80e42-151">Vi 명령 모드: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="80e42-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="80e42-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="80e42-152">BackwardDeleteLine</span></span>

<span data-ttu-id="80e42-153">Like BackwardKillLine-점에서 줄의 시작 부분으로 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="80e42-154">입력 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="80e42-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="80e42-155">Vi 삽입 모드: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="80e42-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="80e42-156">Vi 명령 모드: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="80e42-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="80e42-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="80e42-157">BackwardDeleteWord</span></span>

<span data-ttu-id="80e42-158">이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-158">Deletes the previous word.</span></span>

- <span data-ttu-id="80e42-159">Vi 명령 모드: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="80e42-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="80e42-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="80e42-160">BackwardKillLine</span></span>

<span data-ttu-id="80e42-161">커서에 대 한 입력의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="80e42-162">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="80e42-163">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="80e42-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="80e42-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="80e42-164">BackwardKillWord</span></span>

<span data-ttu-id="80e42-165">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="80e42-166">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="80e42-167">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="80e42-168">Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="80e42-168">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="80e42-169">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="80e42-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="80e42-170">Vi 삽입 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="80e42-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="80e42-171">Vi 명령 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="80e42-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="80e42-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="80e42-172">CancelLine</span></span>

<span data-ttu-id="80e42-173">화면에 입력을 그대로 두고 현재 입력을 취소 합니다. 그러나 프롬프트가 다시 계산 되도록 다시 호스트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="80e42-174">Vi 삽입 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="80e42-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="80e42-175">Vi 명령 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="80e42-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="80e42-176">복사</span><span class="sxs-lookup"><span data-stu-id="80e42-176">Copy</span></span>

<span data-ttu-id="80e42-177">선택한 영역을 시스템 클립보드에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="80e42-178">선택 된 지역이 없으면 전체 줄을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="80e42-179">입력 `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="80e42-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="80e42-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="80e42-180">CopyOrCancelLine</span></span>

<span data-ttu-id="80e42-181">텍스트를 선택한 경우 클립보드로 복사 하 고, 그렇지 않으면 줄을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="80e42-182">입력 `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="80e42-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="80e42-183">Emacs `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="80e42-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="80e42-184">잘라내기</span><span class="sxs-lookup"><span data-stu-id="80e42-184">Cut</span></span>

<span data-ttu-id="80e42-185">삭제 된 텍스트를 시스템 클립보드에 배치 하는 선택한 영역을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="80e42-186">입력 `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="80e42-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="80e42-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="80e42-187">DeleteChar</span></span>

<span data-ttu-id="80e42-188">커서 아래의 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="80e42-189">입력 `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="80e42-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="80e42-190">Emacs `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="80e42-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="80e42-191">Vi 삽입 모드: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="80e42-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="80e42-192">Vi 명령 모드: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="80e42-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="80e42-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="80e42-193">DeleteCharOrExit</span></span>

<span data-ttu-id="80e42-194">커서 아래의 문자를 삭제 하거나, 줄이 비어 있으면 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="80e42-195">Emacs `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="80e42-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="80e42-196">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="80e42-196">DeleteEndOfBuffer</span></span>

<span data-ttu-id="80e42-197">여러 줄 버퍼의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-197">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="80e42-198">Vi 명령 모드: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="80e42-198">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="80e42-199">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="80e42-199">DeleteEndOfWord</span></span>

<span data-ttu-id="80e42-200">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-200">Delete to the end of the word.</span></span>

- <span data-ttu-id="80e42-201">Vi 명령 모드: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="80e42-201">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="80e42-202">Deleteline.invoke</span><span class="sxs-lookup"><span data-stu-id="80e42-202">DeleteLine</span></span>

<span data-ttu-id="80e42-203">여러 줄 버퍼의 현재 논리 줄을 삭제 하 고 실행 취소를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-203">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="80e42-204">Vi 명령 모드: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="80e42-204">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="80e42-205">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="80e42-205">DeletePreviousLines</span></span>

<span data-ttu-id="80e42-206">여러 줄 버퍼에서 요청 된 이전 논리 줄과 현재 논리 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-206">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="80e42-207">Vi 명령 모드: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="80e42-207">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="80e42-208">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="80e42-208">DeleteRelativeLines</span></span>

<span data-ttu-id="80e42-209">버퍼의 시작 부분에서 여러 줄 버퍼의 현재 논리 줄까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-209">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="80e42-210">대부분의 Vi 명령으로 `<d,g,g>` 명령 앞에는 절대 줄 번호를 지정 하는 숫자 인수를 추가할 수 있습니다 .이 숫자는 현재 줄 번호와 함께 삭제 될 줄의 범위를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-210">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="80e42-211">지정 하지 않으면 숫자 인수는 기본적으로 1로 설정 되며이는 여러 줄 버퍼의 첫 번째 논리 줄을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-211">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="80e42-212">여러 줄에서 삭제 되는 실제 줄 수는 현재 논리 줄 번호와 지정 된 숫자 인수 간의 차이로 계산 되므로 음수가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-212">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="80e42-213">따라서 메서드 이름의 _상대_ 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-213">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="80e42-214">Vi 명령 모드: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="80e42-214">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="80e42-215">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="80e42-215">DeleteNextLines</span></span>

<span data-ttu-id="80e42-216">여러 줄 버퍼에서 현재 논리 줄 및 요청 된 다음 논리 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-216">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="80e42-217">Vi 명령 모드: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="80e42-217">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="80e42-218">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="80e42-218">DeleteLineToFirstChar</span></span>

<span data-ttu-id="80e42-219">커서에서 줄의 공백이 아닌 첫 번째 문자로 텍스트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-219">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="80e42-220">Vi 명령 모드: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="80e42-220">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="80e42-221">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="80e42-221">DeleteToEnd</span></span>

<span data-ttu-id="80e42-222">줄의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-222">Delete to the end of the line.</span></span>

- <span data-ttu-id="80e42-223">Vi 명령 모드: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="80e42-223">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="80e42-224">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="80e42-224">DeleteWord</span></span>

<span data-ttu-id="80e42-225">다음 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-225">Delete the next word.</span></span>

- <span data-ttu-id="80e42-226">Vi 명령 모드: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="80e42-226">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="80e42-227">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="80e42-227">ForwardDeleteLine</span></span>

<span data-ttu-id="80e42-228">Like ForwardKillLine-포인트에서 줄 끝 까지의 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-228">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="80e42-229">입력 `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="80e42-229">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="80e42-230">Vi 삽입 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="80e42-230">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="80e42-231">Vi 명령 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="80e42-231">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="80e42-232">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="80e42-232">InsertLineAbove</span></span>

<span data-ttu-id="80e42-233">현재 줄에 커서가 있는 위치에 관계 없이 새 빈 줄이 현재 줄 위에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-233">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="80e42-234">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-234">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="80e42-235">입력 `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-235">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="80e42-236">Insertlinenea</span><span class="sxs-lookup"><span data-stu-id="80e42-236">InsertLineBelow</span></span>

<span data-ttu-id="80e42-237">커서가 현재 줄에 있는지 여부에 관계 없이 현재 줄 아래에 빈 줄이 새로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-237">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="80e42-238">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-238">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="80e42-239">입력 `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-239">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="80e42-240">InvertCase</span><span class="sxs-lookup"><span data-stu-id="80e42-240">InvertCase</span></span>

<span data-ttu-id="80e42-241">현재 문자의 대/소문자를 반전 하 고 다음으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-241">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="80e42-242">Vi 명령 모드: `<~>`</span><span class="sxs-lookup"><span data-stu-id="80e42-242">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="80e42-243">KillLine</span><span class="sxs-lookup"><span data-stu-id="80e42-243">KillLine</span></span>

<span data-ttu-id="80e42-244">입력의 끝 부분까지 커서에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-244">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="80e42-245">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-245">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="80e42-246">Emacs `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="80e42-246">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="80e42-247">KillRegion</span><span class="sxs-lookup"><span data-stu-id="80e42-247">KillRegion</span></span>

<span data-ttu-id="80e42-248">커서와 표시 사이에 있는 텍스트를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-248">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="80e42-249">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-249">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="80e42-250">KillWord</span><span class="sxs-lookup"><span data-stu-id="80e42-250">KillWord</span></span>

<span data-ttu-id="80e42-251">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-251">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="80e42-252">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-252">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="80e42-253">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-253">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="80e42-254">Cmd: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="80e42-254">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="80e42-255">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="80e42-255">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="80e42-256">Vi 삽입 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="80e42-256">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="80e42-257">Vi 명령 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="80e42-257">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="80e42-258">붙여넣기</span><span class="sxs-lookup"><span data-stu-id="80e42-258">Paste</span></span>

<span data-ttu-id="80e42-259">시스템 클립보드에서 텍스트를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-259">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="80e42-260">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="80e42-260">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="80e42-261">Vi 삽입 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="80e42-261">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="80e42-262">Vi 명령 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="80e42-262">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80e42-263">**Paste** 함수를 사용 하는 경우 클립보드 버퍼의 전체 내용이 psreadline의 입력 버퍼에 붙여넣어집니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-263">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="80e42-264">그런 다음 입력 버퍼가 PowerShell 파서로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-264">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="80e42-265">콘솔 응용 프로그램의 **마우스 오른쪽 단추 클릭** 붙여넣기 메서드를 사용 하 여 붙여넣은 입력은 입력 버퍼에 한 번에 한 문자씩 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-265">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="80e42-266">입력 버퍼는 줄 바꿈 문자가 복사 될 때 파서에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-266">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="80e42-267">따라서 입력은 한 번에 한 줄씩 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-267">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="80e42-268">붙여넣기 메서드 간의 차이점으로 인해 실행 동작이 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-268">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="80e42-269">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="80e42-269">PasteAfter</span></span>

<span data-ttu-id="80e42-270">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 뒤에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-270">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="80e42-271">Vi 명령 모드: `<p>`</span><span class="sxs-lookup"><span data-stu-id="80e42-271">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="80e42-272">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="80e42-272">PasteBefore</span></span>

<span data-ttu-id="80e42-273">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 앞에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-273">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="80e42-274">Vi 명령 모드: `<P>`</span><span class="sxs-lookup"><span data-stu-id="80e42-274">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="80e42-275">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="80e42-275">PrependAndAccept</span></span>

<span data-ttu-id="80e42-276">' # ' 앞에를 추가 하 고 줄을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-276">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="80e42-277">Vi 명령 모드: `<#>`</span><span class="sxs-lookup"><span data-stu-id="80e42-277">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="80e42-278">다시 실행</span><span class="sxs-lookup"><span data-stu-id="80e42-278">Redo</span></span>

<span data-ttu-id="80e42-279">실행 취소를 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-279">Undo an undo.</span></span>

- <span data-ttu-id="80e42-280">입력 `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="80e42-280">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="80e42-281">Vi 삽입 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="80e42-281">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="80e42-282">Vi 명령 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="80e42-282">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="80e42-283">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="80e42-283">RepeatLastCommand</span></span>

<span data-ttu-id="80e42-284">마지막 텍스트 수정 작업을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-284">Repeat the last text modification.</span></span>

- <span data-ttu-id="80e42-285">Vi 명령 모드: `<.>`</span><span class="sxs-lookup"><span data-stu-id="80e42-285">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="80e42-286">RevertLine</span><span class="sxs-lookup"><span data-stu-id="80e42-286">RevertLine</span></span>

<span data-ttu-id="80e42-287">모든 입력을 현재 입력으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-287">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="80e42-288">입력 `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="80e42-288">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="80e42-289">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="80e42-289">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="80e42-290">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="80e42-290">ShellBackwardKillWord</span></span>

<span data-ttu-id="80e42-291">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-291">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="80e42-292">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-292">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="80e42-293">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-293">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="80e42-294">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-294">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="80e42-295">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="80e42-295">ShellKillWord</span></span>

<span data-ttu-id="80e42-296">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-296">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="80e42-297">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-297">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="80e42-298">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-298">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="80e42-299">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-299">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="80e42-300">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="80e42-300">SwapCharacters</span></span>

<span data-ttu-id="80e42-301">현재 문자와 그 앞의 문자를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-301">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="80e42-302">Emacs `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="80e42-302">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="80e42-303">Vi 삽입 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="80e42-303">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="80e42-304">Vi 명령 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="80e42-304">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="80e42-305">실행 취소</span><span class="sxs-lookup"><span data-stu-id="80e42-305">Undo</span></span>

<span data-ttu-id="80e42-306">이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-306">Undo a previous edit.</span></span>

- <span data-ttu-id="80e42-307">입력 `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="80e42-307">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="80e42-308">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="80e42-308">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="80e42-309">Vi 삽입 모드: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="80e42-309">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="80e42-310">Vi 명령 모드: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="80e42-310">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="80e42-311">모두를</span><span class="sxs-lookup"><span data-stu-id="80e42-311">UndoAll</span></span>

<span data-ttu-id="80e42-312">줄의 모든 이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-312">Undo all previous edits for line.</span></span>

- <span data-ttu-id="80e42-313">Vi 명령 모드: `<U>`</span><span class="sxs-lookup"><span data-stu-id="80e42-313">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="80e42-314">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="80e42-314">UnixWordRubout</span></span>

<span data-ttu-id="80e42-315">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-315">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="80e42-316">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-316">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="80e42-317">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-317">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="80e42-318">Emacs `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="80e42-318">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="80e42-319">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="80e42-319">ValidateAndAcceptLine</span></span>

<span data-ttu-id="80e42-320">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-320">Attempt to execute the current input.</span></span> <span data-ttu-id="80e42-321">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-321">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="80e42-322">Emacs `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="80e42-322">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="80e42-323">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="80e42-323">ViAcceptLine</span></span>

<span data-ttu-id="80e42-324">줄을 적용 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-324">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="80e42-325">Vi 명령 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="80e42-325">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="80e42-326">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="80e42-326">ViAcceptLineOrExit</span></span>

<span data-ttu-id="80e42-327">Emacs 모드에서 DeleteCharOrExit와 비슷하지만 문자를 삭제 하는 대신 줄을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-327">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="80e42-328">Vi 삽입 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="80e42-328">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="80e42-329">Vi 명령 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="80e42-329">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="80e42-330">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="80e42-330">ViAppendLine</span></span>

<span data-ttu-id="80e42-331">현재 줄 아래에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-331">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="80e42-332">Vi 명령 모드: `<o>`</span><span class="sxs-lookup"><span data-stu-id="80e42-332">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="80e42-333">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="80e42-333">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="80e42-334">공백을 단어 구분 기호로 사용 하 여 이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-334">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="80e42-335">Vi 명령 모드: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="80e42-335">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="80e42-336">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="80e42-336">ViBackwardGlob</span></span>

<span data-ttu-id="80e42-337">공백을 구분 기호로 사용 하 여 커서를 이전 단어의 시작 부분으로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-337">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="80e42-338">Vi 명령 모드: `<B>`</span><span class="sxs-lookup"><span data-stu-id="80e42-338">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="80e42-339">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="80e42-339">ViDeleteBrace</span></span>

<span data-ttu-id="80e42-340">괄호를 포함 하 여 일치 하는 중괄호, 괄호 또는 대괄호를 찾아 내에서 모든 내용을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-340">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="80e42-341">Vi 명령 모드: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="80e42-341">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="80e42-342">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="80e42-342">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="80e42-343">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-343">Delete to the end of the word.</span></span>

- <span data-ttu-id="80e42-344">Vi 명령 모드: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="80e42-344">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="80e42-345">Videletlob</span><span class="sxs-lookup"><span data-stu-id="80e42-345">ViDeleteGlob</span></span>

<span data-ttu-id="80e42-346">다음 glob (공백으로 구분 된 단어)를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-346">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="80e42-347">Vi 명령 모드: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="80e42-347">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="80e42-348">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="80e42-348">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="80e42-349">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-349">Deletes until given character.</span></span>

- <span data-ttu-id="80e42-350">Vi 명령 모드: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="80e42-350">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="80e42-351">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="80e42-351">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="80e42-352">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-352">Deletes until given character.</span></span>

- <span data-ttu-id="80e42-353">Vi 명령 모드: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="80e42-353">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="80e42-354">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="80e42-354">ViDeleteToChar</span></span>

<span data-ttu-id="80e42-355">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-355">Deletes until given character.</span></span>

- <span data-ttu-id="80e42-356">Vi 명령 모드: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="80e42-356">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="80e42-357">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="80e42-357">ViDeleteToCharBackward</span></span>

<span data-ttu-id="80e42-358">지정 된 문자까지 뒤로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-358">Deletes backwards until given character.</span></span>

- <span data-ttu-id="80e42-359">Vi 명령 모드: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="80e42-359">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="80e42-360">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="80e42-360">ViInsertAtBegining</span></span>

<span data-ttu-id="80e42-361">삽입 모드로 전환 하 고 줄의 시작 부분에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-361">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="80e42-362">Vi 명령 모드: `<I>`</span><span class="sxs-lookup"><span data-stu-id="80e42-362">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="80e42-363">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="80e42-363">ViInsertAtEnd</span></span>

<span data-ttu-id="80e42-364">삽입 모드로 전환 하 고 줄의 끝에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-364">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="80e42-365">Vi 명령 모드: `<A>`</span><span class="sxs-lookup"><span data-stu-id="80e42-365">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="80e42-366">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="80e42-366">ViInsertLine</span></span>

<span data-ttu-id="80e42-367">현재 줄 위에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-367">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="80e42-368">Vi 명령 모드: `<O>`</span><span class="sxs-lookup"><span data-stu-id="80e42-368">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="80e42-369">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="80e42-369">ViInsertWithAppend</span></span>

<span data-ttu-id="80e42-370">현재 줄 위치에서 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-370">Append from the current line position.</span></span>

- <span data-ttu-id="80e42-371">Vi 명령 모드: `<a>`</span><span class="sxs-lookup"><span data-stu-id="80e42-371">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="80e42-372">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="80e42-372">ViInsertWithDelete</span></span>

<span data-ttu-id="80e42-373">현재 문자를 삭제 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-373">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="80e42-374">Vi 명령 모드: `<s>`</span><span class="sxs-lookup"><span data-stu-id="80e42-374">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="80e42-375">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="80e42-375">ViJoinLines</span></span>

<span data-ttu-id="80e42-376">현재 줄과 다음 줄을 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-376">Joins the current line and the next line.</span></span>

- <span data-ttu-id="80e42-377">Vi 명령 모드: `<J>`</span><span class="sxs-lookup"><span data-stu-id="80e42-377">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="80e42-378">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="80e42-378">ViReplaceLine</span></span>

<span data-ttu-id="80e42-379">전체 명령줄을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-379">Erase the entire command line.</span></span>

- <span data-ttu-id="80e42-380">Vi 명령 모드: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="80e42-380">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="80e42-381">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="80e42-381">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="80e42-382">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-382">Replaces until given character.</span></span>

- <span data-ttu-id="80e42-383">Vi 명령 모드: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="80e42-383">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="80e42-384">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="80e42-384">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="80e42-385">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-385">Replaces until given character.</span></span>

- <span data-ttu-id="80e42-386">Vi 명령 모드: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="80e42-386">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="80e42-387">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="80e42-387">ViReplaceToChar</span></span>

<span data-ttu-id="80e42-388">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-388">Deletes until given character.</span></span>

- <span data-ttu-id="80e42-389">Vi 명령 모드: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="80e42-389">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="80e42-390">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="80e42-390">ViReplaceToCharBackward</span></span>

<span data-ttu-id="80e42-391">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-391">Replaces until given character.</span></span>

- <span data-ttu-id="80e42-392">Vi 명령 모드: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="80e42-392">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="80e42-393">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="80e42-393">ViYankBeginningOfLine</span></span>

<span data-ttu-id="80e42-394">버퍼의 시작 부분에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="80e42-394">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="80e42-395">Vi 명령 모드: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="80e42-395">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="80e42-396">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="80e42-396">ViYankEndOfGlob</span></span>

<span data-ttu-id="80e42-397">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-397">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="80e42-398">Vi 명령 모드: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="80e42-398">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="80e42-399">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="80e42-399">ViYankEndOfWord</span></span>

<span data-ttu-id="80e42-400">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-400">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="80e42-401">Vi 명령 모드: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="80e42-401">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="80e42-402">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="80e42-402">ViYankLeft</span></span>

<span data-ttu-id="80e42-403">커서의 왼쪽에 문자를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-403">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="80e42-404">Vi 명령 모드: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="80e42-404">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="80e42-405">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="80e42-405">ViYankLine</span></span>

<span data-ttu-id="80e42-406">전체 버퍼를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-406">Yank the entire buffer.</span></span>

- <span data-ttu-id="80e42-407">Vi 명령 모드: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="80e42-407">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="80e42-408">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="80e42-408">ViYankNextGlob</span></span>

<span data-ttu-id="80e42-409">커서에서 다음 단어의 시작 부분으로 Yank.</span><span class="sxs-lookup"><span data-stu-id="80e42-409">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="80e42-410">Vi 명령 모드: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="80e42-410">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="80e42-411">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="80e42-411">ViYankNextWord</span></span>

<span data-ttu-id="80e42-412">커서 뒤의 단어를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-412">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="80e42-413">Vi 명령 모드: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="80e42-413">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="80e42-414">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="80e42-414">ViYankPercent</span></span>

<span data-ttu-id="80e42-415">짝이 되는 중괄호에서 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-415">Yank to/from matching brace.</span></span>

- <span data-ttu-id="80e42-416">Vi 명령 모드: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="80e42-416">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="80e42-417">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="80e42-417">ViYankPreviousGlob</span></span>

<span data-ttu-id="80e42-418">단어의 시작부터 커서까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-418">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="80e42-419">Vi 명령 모드: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="80e42-419">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="80e42-420">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="80e42-420">ViYankPreviousWord</span></span>

<span data-ttu-id="80e42-421">커서 앞에 단어를 Yank.</span><span class="sxs-lookup"><span data-stu-id="80e42-421">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="80e42-422">Vi 명령 모드: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="80e42-422">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="80e42-423">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="80e42-423">ViYankRight</span></span>

<span data-ttu-id="80e42-424">커서 오른쪽의 및 아래에 Yank 문자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-424">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="80e42-425">Vi 명령 모드: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="80e42-425">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="80e42-426">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="80e42-426">ViYankToEndOfLine</span></span>

<span data-ttu-id="80e42-427">커서에서 버퍼 끝까지 Yank.</span><span class="sxs-lookup"><span data-stu-id="80e42-427">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="80e42-428">Vi 명령 모드: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="80e42-428">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="80e42-429">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="80e42-429">ViYankToFirstChar</span></span>

<span data-ttu-id="80e42-430">공백이 아닌 첫 번째 문자에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="80e42-430">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="80e42-431">Vi 명령 모드: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="80e42-431">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="80e42-432">Yank</span><span class="sxs-lookup"><span data-stu-id="80e42-432">Yank</span></span>

<span data-ttu-id="80e42-433">가장 최근에 종료 된 텍스트를 입력에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-433">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="80e42-434">Emacs `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="80e42-434">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="80e42-435">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="80e42-435">YankLastArg</span></span>

<span data-ttu-id="80e42-436">이전 기록 줄에서 마지막 인수를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-436">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="80e42-437">인수를 사용 하면 처음 호출 될 때 YankNthArg 처럼 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-437">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="80e42-438">여러 번 호출 된 경우에는 기록 및 인수에서 방향을 설정 합니다. (음수는 방향을 반대로 바꿉니다.)</span><span class="sxs-lookup"><span data-stu-id="80e42-438">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="80e42-439">입력 `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="80e42-439">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="80e42-440">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="80e42-440">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="80e42-441">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="80e42-441">YankNthArg</span></span>

<span data-ttu-id="80e42-442">이전 기록 줄에서 첫 번째 인수 (명령 뒤)를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-442">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="80e42-443">인수를 사용 하는 경우 n 번째 인수 (0부터 시작)를 yank. 인수가 음수 이면 마지막 인수부터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-443">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="80e42-444">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="80e42-444">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="80e42-445">YankPop</span><span class="sxs-lookup"><span data-stu-id="80e42-445">YankPop</span></span>

<span data-ttu-id="80e42-446">이전 작업이 Yank 또는 YankPop 인 경우 이전 빼낼 텍스트를 kill 링에서 다음에 종료 된 텍스트로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-446">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="80e42-447">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="80e42-447">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="80e42-448">커서 이동 함수</span><span class="sxs-lookup"><span data-stu-id="80e42-448">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="80e42-449">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="80e42-449">BackwardChar</span></span>

<span data-ttu-id="80e42-450">커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-450">Move the cursor one character to the left.</span></span> <span data-ttu-id="80e42-451">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-451">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="80e42-452">입력 `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-452">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="80e42-453">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="80e42-453">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="80e42-454">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="80e42-454">BackwardWord</span></span>

<span data-ttu-id="80e42-455">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-455">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="80e42-456">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-456">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="80e42-457">입력 `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-457">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="80e42-458">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="80e42-458">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="80e42-459">Vi 삽입 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-459">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="80e42-460">Vi 명령 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-460">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="80e42-461">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="80e42-461">BeginningOfLine</span></span>

<span data-ttu-id="80e42-462">입력에 여러 줄이 있는 경우 현재 줄의 시작 부분으로 이동 하거나 이미 줄의 시작 부분에 있는 경우 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-462">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="80e42-463">입력에 한 줄이 있으면 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-463">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="80e42-464">입력 `<Home>`</span><span class="sxs-lookup"><span data-stu-id="80e42-464">Cmd: `<Home>`</span></span>
- <span data-ttu-id="80e42-465">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="80e42-465">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="80e42-466">Vi 삽입 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="80e42-466">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="80e42-467">Vi 명령 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="80e42-467">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="80e42-468">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="80e42-468">EndOfLine</span></span>

<span data-ttu-id="80e42-469">입력에 여러 줄이 있는 경우 현재 줄의 끝으로 이동 하거나 줄의 끝에 있는 경우 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-469">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="80e42-470">입력에 한 줄이 있으면 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-470">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="80e42-471">입력 `<End>`</span><span class="sxs-lookup"><span data-stu-id="80e42-471">Cmd: `<End>`</span></span>
- <span data-ttu-id="80e42-472">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="80e42-472">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="80e42-473">Vi 삽입 모드: `<End>`</span><span class="sxs-lookup"><span data-stu-id="80e42-473">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="80e42-474">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="80e42-474">ForwardChar</span></span>

<span data-ttu-id="80e42-475">커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-475">Move the cursor one character to the right.</span></span> <span data-ttu-id="80e42-476">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-476">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="80e42-477">입력 `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-477">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="80e42-478">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="80e42-478">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="80e42-479">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="80e42-479">ForwardWord</span></span>

<span data-ttu-id="80e42-480">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-480">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="80e42-481">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-481">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="80e42-482">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="80e42-482">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="80e42-483">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="80e42-483">GotoBrace</span></span>

<span data-ttu-id="80e42-484">짝이 되는 중괄호, 괄호 또는 대괄호로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-484">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="80e42-485">입력 `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="80e42-485">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="80e42-486">Vi 삽입 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="80e42-486">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="80e42-487">Vi 명령 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="80e42-487">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="80e42-488">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="80e42-488">GotoColumn</span></span>

<span data-ttu-id="80e42-489">Arg로 표시 된 열로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-489">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="80e42-490">Vi 명령 모드: `<|>`</span><span class="sxs-lookup"><span data-stu-id="80e42-490">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="80e42-491">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="80e42-491">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="80e42-492">줄에서 비어 있지 않은 첫 번째 문자로 커서를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-492">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="80e42-493">Vi 명령 모드: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="80e42-493">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="80e42-494">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="80e42-494">MoveToEndOfLine</span></span>

<span data-ttu-id="80e42-495">커서를 입력 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-495">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="80e42-496">Vi 명령 모드: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="80e42-496">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="80e42-497">NextLine</span><span class="sxs-lookup"><span data-stu-id="80e42-497">NextLine</span></span>

<span data-ttu-id="80e42-498">커서를 다음 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-498">Move the cursor to the next line.</span></span>

- <span data-ttu-id="80e42-499">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-499">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="80e42-500">NextWord</span><span class="sxs-lookup"><span data-stu-id="80e42-500">NextWord</span></span>

<span data-ttu-id="80e42-501">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-501">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="80e42-502">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-502">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="80e42-503">입력 `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-503">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="80e42-504">Vi 삽입 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-504">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="80e42-505">Vi 명령 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-505">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="80e42-506">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="80e42-506">NextWordEnd</span></span>

<span data-ttu-id="80e42-507">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="80e42-508">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="80e42-509">Vi 명령 모드: `<e>`</span><span class="sxs-lookup"><span data-stu-id="80e42-509">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="80e42-510">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="80e42-510">PreviousLine</span></span>

<span data-ttu-id="80e42-511">커서를 이전 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-511">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="80e42-512">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-512">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="80e42-513">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="80e42-513">ShellBackwardWord</span></span>

<span data-ttu-id="80e42-514">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="80e42-515">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-515">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="80e42-516">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-516">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="80e42-517">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="80e42-517">ShellForwardWord</span></span>

<span data-ttu-id="80e42-518">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="80e42-519">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-519">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="80e42-520">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-520">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="80e42-521">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="80e42-521">ShellNextWord</span></span>

<span data-ttu-id="80e42-522">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="80e42-523">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-523">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="80e42-524">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-524">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="80e42-525">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="80e42-525">ViBackwardChar</span></span>

<span data-ttu-id="80e42-526">Vi 편집 모드에서 커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-526">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="80e42-527">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-527">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="80e42-528">Vi 삽입 모드: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-528">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="80e42-529">Vi 명령 모드: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="80e42-529">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="80e42-530">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="80e42-530">ViBackwardWord</span></span>

<span data-ttu-id="80e42-531">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="80e42-532">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-532">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="80e42-533">Vi 명령 모드: `<b>`</span><span class="sxs-lookup"><span data-stu-id="80e42-533">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="80e42-534">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="80e42-534">ViForwardChar</span></span>

<span data-ttu-id="80e42-535">Vi 편집 모드에서 커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-535">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="80e42-536">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-536">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="80e42-537">Vi 삽입 모드: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-537">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="80e42-538">Vi 명령 모드: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="80e42-538">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="80e42-539">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="80e42-539">ViEndOfGlob</span></span>

<span data-ttu-id="80e42-540">공백을 구분 기호로 사용 하 여 커서를 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-540">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="80e42-541">Vi 명령 모드: `<E>`</span><span class="sxs-lookup"><span data-stu-id="80e42-541">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="80e42-542">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="80e42-542">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="80e42-543">공백을 단어 구분 기호로 사용 하 여 이전 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-543">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="80e42-544">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-544">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="80e42-545">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="80e42-545">ViGotoBrace</span></span>

<span data-ttu-id="80e42-546">GotoBrace와 비슷하지만 토큰 기반이 아니라 문자 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-546">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="80e42-547">Vi 명령 모드: `<%>`</span><span class="sxs-lookup"><span data-stu-id="80e42-547">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="80e42-548">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="80e42-548">ViNextGlob</span></span>

<span data-ttu-id="80e42-549">공백을 단어 구분 기호로 사용 하 여 다음 단어로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-549">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="80e42-550">Vi 명령 모드: `<W>`</span><span class="sxs-lookup"><span data-stu-id="80e42-550">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="80e42-551">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="80e42-551">ViNextWord</span></span>

<span data-ttu-id="80e42-552">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-552">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="80e42-553">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-553">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="80e42-554">Vi 명령 모드: `<w>`</span><span class="sxs-lookup"><span data-stu-id="80e42-554">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="80e42-555">기록 함수</span><span class="sxs-lookup"><span data-stu-id="80e42-555">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="80e42-556">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="80e42-556">BeginningOfHistory</span></span>

<span data-ttu-id="80e42-557">기록의 첫 번째 항목으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-557">Move to the first item in the history.</span></span>

- <span data-ttu-id="80e42-558">Emacs `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="80e42-558">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="80e42-559">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="80e42-559">ClearHistory</span></span>

<span data-ttu-id="80e42-560">PSReadLine에서 기록을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-560">Clears history in PSReadLine.</span></span> <span data-ttu-id="80e42-561">PowerShell 기록에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-561">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="80e42-562">입력 `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="80e42-562">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="80e42-563">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="80e42-563">EndOfHistory</span></span>

<span data-ttu-id="80e42-564">기록에서 마지막 항목 (현재 입력)으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-564">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="80e42-565">Emacs `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="80e42-565">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="80e42-566">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="80e42-566">ForwardSearchHistory</span></span>

<span data-ttu-id="80e42-567">기록을 통해 증분 전달 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-567">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="80e42-568">입력 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="80e42-568">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="80e42-569">Emacs `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="80e42-569">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="80e42-570">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="80e42-570">HistorySearchBackward</span></span>

<span data-ttu-id="80e42-571">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-571">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="80e42-572">입력 `<F8>`</span><span class="sxs-lookup"><span data-stu-id="80e42-572">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="80e42-573">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="80e42-573">HistorySearchForward</span></span>

<span data-ttu-id="80e42-574">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-574">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="80e42-575">입력 `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="80e42-575">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="80e42-576">NextHistory</span><span class="sxs-lookup"><span data-stu-id="80e42-576">NextHistory</span></span>

<span data-ttu-id="80e42-577">현재 입력을 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-577">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="80e42-578">입력 `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-578">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="80e42-579">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="80e42-579">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="80e42-580">Vi 삽입 모드: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-580">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="80e42-581">Vi 명령 모드: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="80e42-581">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="80e42-582">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="80e42-582">PreviousHistory</span></span>

<span data-ttu-id="80e42-583">현재 입력을 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-583">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="80e42-584">입력 `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-584">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="80e42-585">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="80e42-585">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="80e42-586">Vi 삽입 모드: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-586">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="80e42-587">Vi 명령 모드: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="80e42-587">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="80e42-588">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="80e42-588">ReverseSearchHistory</span></span>

<span data-ttu-id="80e42-589">기록을 통해 증분 역방향 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-589">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="80e42-590">입력 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="80e42-590">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="80e42-591">Emacs `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="80e42-591">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="80e42-592">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="80e42-592">ViSearchHistoryBackward</span></span>

<span data-ttu-id="80e42-593">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-593">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="80e42-594">Vi 삽입 모드: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="80e42-594">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="80e42-595">Vi 명령 모드: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="80e42-595">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="80e42-596">완료 함수</span><span class="sxs-lookup"><span data-stu-id="80e42-596">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="80e42-597">완료</span><span class="sxs-lookup"><span data-stu-id="80e42-597">Complete</span></span>

<span data-ttu-id="80e42-598">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-598">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="80e42-599">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-599">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="80e42-600">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-600">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="80e42-601">Emacs `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="80e42-601">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="80e42-602">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="80e42-602">MenuComplete</span></span>

<span data-ttu-id="80e42-603">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-603">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="80e42-604">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-604">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="80e42-605">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-605">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="80e42-606">Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="80e42-606">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="80e42-607">Emacs `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="80e42-607">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="80e42-608">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="80e42-608">PossibleCompletions</span></span>

<span data-ttu-id="80e42-609">가능한 완료 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-609">Display the list of possible completions.</span></span>

- <span data-ttu-id="80e42-610">Emacs `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="80e42-610">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="80e42-611">Vi 삽입 모드: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="80e42-611">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="80e42-612">Vi 명령 모드: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="80e42-612">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="80e42-613">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="80e42-613">TabCompleteNext</span></span>

<span data-ttu-id="80e42-614">다음에 사용 가능한 완료로 커서를 둘러싼 텍스트를 완성 해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-614">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="80e42-615">입력 `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="80e42-615">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="80e42-616">Vi 명령 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="80e42-616">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="80e42-617">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="80e42-617">TabCompletePrevious</span></span>

<span data-ttu-id="80e42-618">이전에 사용 가능한 완료를 사용 하 여 커서를 둘러싼 텍스트를 완료 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-618">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="80e42-619">입력 `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="80e42-619">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="80e42-620">Vi 명령 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="80e42-620">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="80e42-621">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="80e42-621">ViTabCompleteNext</span></span>

<span data-ttu-id="80e42-622">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompleteNext를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-622">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="80e42-623">Vi 삽입 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="80e42-623">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="80e42-624">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="80e42-624">ViTabCompletePrevious</span></span>

<span data-ttu-id="80e42-625">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompletePrevious를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-625">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="80e42-626">Vi 삽입 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="80e42-626">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="80e42-627">기타 함수</span><span class="sxs-lookup"><span data-stu-id="80e42-627">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="80e42-628">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="80e42-628">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="80e42-629">인라인 또는 선택한 제안의 다음 단어를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-629">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="80e42-630">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-630">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="80e42-631">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="80e42-631">AcceptSuggestion</span></span>

<span data-ttu-id="80e42-632">현재 인라인 또는 선택한 제안에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-632">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="80e42-633">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-633">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="80e42-634">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="80e42-634">CaptureScreen</span></span>

<span data-ttu-id="80e42-635">대화형 화면 캡처 시작-위쪽/아래쪽 화살표 선 선택, 선택한 텍스트를 클립보드에 텍스트 및 html로 복사를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-635">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="80e42-636">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-636">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="80e42-637">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="80e42-637">ClearScreen</span></span>

<span data-ttu-id="80e42-638">화면을 지우고 화면 위쪽에 현재 줄을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-638">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="80e42-639">입력 `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="80e42-639">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="80e42-640">Emacs `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="80e42-640">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="80e42-641">Vi 삽입 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="80e42-641">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="80e42-642">Vi 명령 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="80e42-642">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="80e42-643">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="80e42-643">DigitArgument</span></span>

<span data-ttu-id="80e42-644">다른 함수에 전달할 새 숫자 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-644">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="80e42-645">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="80e42-645">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="80e42-646">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="80e42-646">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="80e42-647">Vi 명령 모드: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` `<7>` `<8>` ,,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="80e42-647">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="80e42-648">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="80e42-648">InvokePrompt</span></span>

<span data-ttu-id="80e42-649">현재 프롬프트를 지우고 prompt 함수를 호출 하 여 프롬프트를 다시 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-649">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="80e42-650">상태를 변경 하는 사용자 지정 키 처리기 (예: 현재 디렉터리 변경)에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-650">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="80e42-651">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-651">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="80e42-652">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="80e42-652">ScrollDisplayDown</span></span>

<span data-ttu-id="80e42-653">한 화면 아래로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-653">Scroll the display down one screen.</span></span>

- <span data-ttu-id="80e42-654">입력 `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="80e42-654">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="80e42-655">Emacs `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="80e42-655">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="80e42-656">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="80e42-656">ScrollDisplayDownLine</span></span>

<span data-ttu-id="80e42-657">표시를 한 줄 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-657">Scroll the display down one line.</span></span>

- <span data-ttu-id="80e42-658">입력 `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="80e42-658">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="80e42-659">Emacs `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="80e42-659">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="80e42-660">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="80e42-660">ScrollDisplayToCursor</span></span>

<span data-ttu-id="80e42-661">표시를 커서로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-661">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="80e42-662">Emacs `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="80e42-662">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="80e42-663">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="80e42-663">ScrollDisplayTop</span></span>

<span data-ttu-id="80e42-664">표시를 맨 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-664">Scroll the display to the top.</span></span>

- <span data-ttu-id="80e42-665">Emacs `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="80e42-665">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="80e42-666">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="80e42-666">ScrollDisplayUp</span></span>

<span data-ttu-id="80e42-667">한 화면 위로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-667">Scroll the display up one screen.</span></span>

- <span data-ttu-id="80e42-668">입력 `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="80e42-668">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="80e42-669">Emacs `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="80e42-669">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="80e42-670">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="80e42-670">ScrollDisplayUpLine</span></span>

<span data-ttu-id="80e42-671">디스플레이를 한 줄 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-671">Scroll the display up one line.</span></span>

- <span data-ttu-id="80e42-672">입력 `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="80e42-672">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="80e42-673">Emacs `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="80e42-673">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="80e42-674">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="80e42-674">SelfInsert</span></span>

<span data-ttu-id="80e42-675">키를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-675">Insert the key.</span></span>

- <span data-ttu-id="80e42-676">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-676">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="80e42-677">ShowKeyBindings 바인딩</span><span class="sxs-lookup"><span data-stu-id="80e42-677">ShowKeyBindings</span></span>

<span data-ttu-id="80e42-678">모든 바인딩된 키를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-678">Show all bound keys.</span></span>

- <span data-ttu-id="80e42-679">입력 `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="80e42-679">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="80e42-680">Emacs `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="80e42-680">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="80e42-681">Vi 삽입 모드: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="80e42-681">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="80e42-682">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="80e42-682">ViCommandMode</span></span>

<span data-ttu-id="80e42-683">Vi-Insert에서 현재 운영 모드를 Vi 명령으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-683">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="80e42-684">Vi 삽입 모드: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="80e42-684">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="80e42-685">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="80e42-685">ViDigitArgumentInChord</span></span>

<span data-ttu-id="80e42-686">Vi의 누르는 중 하나에서 다른 함수에 전달할 새 digit 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-686">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="80e42-687">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-687">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="80e42-688">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="80e42-688">ViEditVisually</span></span>

<span data-ttu-id="80e42-689">$Env: 편집기 또는 $env: 시각적 개체에 지정 된 텍스트 편집기에서 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-689">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="80e42-690">Emacs `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="80e42-690">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="80e42-691">Vi 명령 모드: `<v>`</span><span class="sxs-lookup"><span data-stu-id="80e42-691">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="80e42-692">ViExit</span><span class="sxs-lookup"><span data-stu-id="80e42-692">ViExit</span></span>

<span data-ttu-id="80e42-693">셸을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-693">Exits the shell.</span></span>

- <span data-ttu-id="80e42-694">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-694">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="80e42-695">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="80e42-695">ViInsertMode</span></span>

<span data-ttu-id="80e42-696">삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-696">Switch to Insert mode.</span></span>

- <span data-ttu-id="80e42-697">Vi 명령 모드: `<i>`</span><span class="sxs-lookup"><span data-stu-id="80e42-697">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="80e42-698">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="80e42-698">WhatIsKey</span></span>

<span data-ttu-id="80e42-699">키를 읽고 키가 바인딩된 정보를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-699">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="80e42-700">입력 `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="80e42-700">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="80e42-701">Emacs `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="80e42-701">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="80e42-702">선택 함수</span><span class="sxs-lookup"><span data-stu-id="80e42-702">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="80e42-703">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="80e42-703">ExchangePointAndMark</span></span>

<span data-ttu-id="80e42-704">커서는 표시 위치에 배치 되 고 표시는 커서의 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-704">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="80e42-705">Emacs `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="80e42-705">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="80e42-706">SelectAll</span><span class="sxs-lookup"><span data-stu-id="80e42-706">SelectAll</span></span>

<span data-ttu-id="80e42-707">전체 줄을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-707">Select the entire line.</span></span>

- <span data-ttu-id="80e42-708">입력 `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="80e42-708">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="80e42-709">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="80e42-709">SelectBackwardChar</span></span>

<span data-ttu-id="80e42-710">이전 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-710">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="80e42-711">입력 `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-711">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="80e42-712">Emacs `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-712">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="80e42-713">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="80e42-713">SelectBackwardsLine</span></span>

<span data-ttu-id="80e42-714">커서에서 줄의 시작 부분까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-714">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="80e42-715">입력 `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="80e42-715">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="80e42-716">Emacs `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="80e42-716">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="80e42-717">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="80e42-717">SelectBackwardWord</span></span>

<span data-ttu-id="80e42-718">이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-718">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="80e42-719">입력 `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-719">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="80e42-720">Emacs `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="80e42-720">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="80e42-721">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="80e42-721">SelectForwardChar</span></span>

<span data-ttu-id="80e42-722">다음 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-722">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="80e42-723">입력 `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-723">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="80e42-724">Emacs `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-724">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="80e42-725">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="80e42-725">SelectForwardWord</span></span>

<span data-ttu-id="80e42-726">ForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-726">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="80e42-727">Emacs `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="80e42-727">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="80e42-728">줄을 select</span><span class="sxs-lookup"><span data-stu-id="80e42-728">SelectLine</span></span>

<span data-ttu-id="80e42-729">커서에서 줄의 끝까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-729">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="80e42-730">입력 `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="80e42-730">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="80e42-731">Emacs `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="80e42-731">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="80e42-732">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="80e42-732">SelectNextWord</span></span>

<span data-ttu-id="80e42-733">다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-733">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="80e42-734">입력 `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="80e42-734">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="80e42-735">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="80e42-735">SelectShellBackwardWord</span></span>

<span data-ttu-id="80e42-736">ShellBackwardWord를 사용 하 여 이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-736">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="80e42-737">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-737">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="80e42-738">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="80e42-738">SelectShellForwardWord</span></span>

<span data-ttu-id="80e42-739">ShellForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-739">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="80e42-740">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-740">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="80e42-741">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="80e42-741">SelectShellNextWord</span></span>

<span data-ttu-id="80e42-742">ShellNextWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-742">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="80e42-743">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-743">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="80e42-744">SetMark</span><span class="sxs-lookup"><span data-stu-id="80e42-744">SetMark</span></span>

<span data-ttu-id="80e42-745">이후 편집 명령에 사용할 커서의 현재 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-745">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="80e42-746">Emacs `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="80e42-746">Emacs: `<Ctrl+@>`</span></span>

## <a name="search-functions"></a><span data-ttu-id="80e42-747">검색 함수</span><span class="sxs-lookup"><span data-stu-id="80e42-747">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="80e42-748">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="80e42-748">CharacterSearch</span></span>

<span data-ttu-id="80e42-749">문자를 읽고 그 다음 번에 해당 문자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-749">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="80e42-750">인수를 지정 하는 경우 n 번째 발생에 대해 앞으로 (음수 이면 뒤로) 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-750">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="80e42-751">입력 `<F3>`</span><span class="sxs-lookup"><span data-stu-id="80e42-751">Cmd: `<F3>`</span></span>
- <span data-ttu-id="80e42-752">Emacs `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="80e42-752">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="80e42-753">Vi 삽입 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="80e42-753">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="80e42-754">Vi 명령 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="80e42-754">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="80e42-755">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="80e42-755">CharacterSearchBackward</span></span>

<span data-ttu-id="80e42-756">문자를 읽은 다음 해당 문자의 다음 항목을 뒤로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-756">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="80e42-757">인수를 지정 하는 경우 n 번째 발생에 대해 뒤로 검색 하거나 음수 이면 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-757">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="80e42-758">입력 `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="80e42-758">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="80e42-759">Emacs `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="80e42-759">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="80e42-760">Vi 삽입 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="80e42-760">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="80e42-761">Vi 명령 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="80e42-761">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="80e42-762">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="80e42-762">RepeatLastCharSearch</span></span>

<span data-ttu-id="80e42-763">마지막으로 기록 된 문자 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-763">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="80e42-764">Vi 명령 모드: `<;>`</span><span class="sxs-lookup"><span data-stu-id="80e42-764">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="80e42-765">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="80e42-765">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="80e42-766">마지막으로 기록 된 문자 검색을 반대 방향으로 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-766">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="80e42-767">Vi 명령 모드: `<,>`</span><span class="sxs-lookup"><span data-stu-id="80e42-767">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="80e42-768">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="80e42-768">RepeatSearch</span></span>

<span data-ttu-id="80e42-769">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-769">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="80e42-770">Vi 명령 모드: `<n>`</span><span class="sxs-lookup"><span data-stu-id="80e42-770">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="80e42-771">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="80e42-771">RepeatSearchBackward</span></span>

<span data-ttu-id="80e42-772">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-772">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="80e42-773">Vi 명령 모드: `<N>`</span><span class="sxs-lookup"><span data-stu-id="80e42-773">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="80e42-774">SearchChar</span><span class="sxs-lookup"><span data-stu-id="80e42-774">SearchChar</span></span>

<span data-ttu-id="80e42-775">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-775">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="80e42-776">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-776">This is for 't' functionality.</span></span>

- <span data-ttu-id="80e42-777">Vi 명령 모드: `<f>`</span><span class="sxs-lookup"><span data-stu-id="80e42-777">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="80e42-778">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="80e42-778">SearchCharBackward</span></span>

<span data-ttu-id="80e42-779">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-779">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="80e42-780">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-780">This is for 'T' functionality.</span></span>

- <span data-ttu-id="80e42-781">Vi 명령 모드: `<F>`</span><span class="sxs-lookup"><span data-stu-id="80e42-781">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="80e42-782">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="80e42-782">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="80e42-783">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-783">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="80e42-784">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-784">This is for 'T' functionality.</span></span>

- <span data-ttu-id="80e42-785">Vi 명령 모드: `<T>`</span><span class="sxs-lookup"><span data-stu-id="80e42-785">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="80e42-786">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="80e42-786">SearchCharWithBackoff</span></span>

<span data-ttu-id="80e42-787">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-787">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="80e42-788">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-788">This is for 't' functionality.</span></span>

- <span data-ttu-id="80e42-789">Vi 명령 모드: `<t>`</span><span class="sxs-lookup"><span data-stu-id="80e42-789">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="80e42-790">SearchForward</span><span class="sxs-lookup"><span data-stu-id="80e42-790">SearchForward</span></span>

<span data-ttu-id="80e42-791">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-791">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="80e42-792">Vi 삽입 모드: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="80e42-792">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="80e42-793">Vi 명령 모드: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="80e42-793">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="80e42-794">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="80e42-794">Custom Key Bindings</span></span>

<span data-ttu-id="80e42-795">PSReadLine은 cmdlet을 사용 하 여 사용자 지정 키 바인딩을 지원 `Set-PSReadLineKeyHandler` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-795">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="80e42-796">대부분의 사용자 지정 키 바인딩은 위의 함수 중 하나를 호출 합니다. 예를 들면</span><span class="sxs-lookup"><span data-stu-id="80e42-796">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="80e42-797">ScriptBlock을 키에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-797">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="80e42-798">ScriptBlock은 필요한 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-798">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="80e42-799">몇 가지 유용한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-799">Some useful examples include</span></span>

- <span data-ttu-id="80e42-800">명령줄 편집</span><span class="sxs-lookup"><span data-stu-id="80e42-800">edit the command line</span></span>
- <span data-ttu-id="80e42-801">새 창 열기 (예: 도움말)</span><span class="sxs-lookup"><span data-stu-id="80e42-801">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="80e42-802">명령줄을 변경 하지 않고 디렉터리를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-802">change directories without changing the command line</span></span>

<span data-ttu-id="80e42-803">ScriptBlock은 두 개의 인수를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-803">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="80e42-804">`$key` -사용자 지정 바인딩을 트리거한 키 인 **[ConsoleKeyInfo]** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-804">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="80e42-805">동일한 ScriptBlock을 여러 키에 바인딩하고 키에 따라 다른 작업을 수행 해야 하는 경우 $key를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-805">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="80e42-806">많은 사용자 지정 바인딩에서이 인수를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-806">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="80e42-807">`$arg` -임의의 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-807">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="80e42-808">가장 자주 사용 되는 정수 인수는 사용자가 키 바인딩 DigitArgument에서 전달 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-808">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="80e42-809">바인딩에서 인수를 허용 하지 않는 경우에는이 인수를 무시 하는 것이 합리적입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-809">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="80e42-810">실행 하지 않고 기록에 명령줄을 추가 하는 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-810">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="80e42-811">이는 작업을 수행 하지 못했지만 이미 입력 한 명령줄을 다시 입력 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-811">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="80e42-812">PSReadLine 모듈 폴더에 설치 된 파일에서 더 많은 예제를 볼 수 있습니다 `SamplePSReadLineProfile.ps1` .</span><span class="sxs-lookup"><span data-stu-id="80e42-812">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="80e42-813">대부분의 키 바인딩은 일부 도우미 함수를 사용 하 여 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-813">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="80e42-814">이러한 Api는 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-814">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="80e42-815">사용자 지정 키 바인딩 지원 Api</span><span class="sxs-lookup"><span data-stu-id="80e42-815">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="80e42-816">다음 함수는 PSConsoleReadLine에서 공용 이지만 키에 직접 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-816">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="80e42-817">대부분은 사용자 지정 키 바인딩에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-817">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="80e42-818">실행 하지 않고 기록에 명령줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-818">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="80e42-819">Kill 링을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-819">Clear the kill-ring.</span></span>  <span data-ttu-id="80e42-820">이는 주로 테스트에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-820">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="80e42-821">시작에서 길이 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-821">Delete length characters from start.</span></span>  <span data-ttu-id="80e42-822">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-822">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="80e42-823">사용자 기본 설정에 따라 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-823">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="80e42-824">이러한 두 함수는 입력 버퍼의 현재 상태에 대 한 유용한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-824">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="80e42-825">첫 번째는 간단한 경우에 보다 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-825">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="80e42-826">두 번째는 바인딩에서 Ast를 사용 하 여 더 높은 작업을 수행 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-826">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="80e42-827">이러한 두 함수는에 사용 됩니다 `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="80e42-827">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="80e42-828">첫 번째는 모든 키 바인딩을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-828">The first is used to get all key bindings.</span></span> <span data-ttu-id="80e42-829">두 번째는 특정 키 바인딩을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-829">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="80e42-830">이 함수는 Get-PSReadLineOption에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-830">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="80e42-831">명령줄에 선택 항목이 없으면-1이 시작 및 길이 둘 다에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-831">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="80e42-832">명령줄에 선택 항목이 있는 경우 선택의 시작 및 길이가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-832">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="80e42-833">커서에 문자 또는 문자열을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-833">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="80e42-834">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-834">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="80e42-835">PSReadLine에 대 한 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-835">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="80e42-836">재귀를 지원 하지 않으므로 사용자 지정 키 바인딩에는 유용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-836">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="80e42-837">이 함수는 Remove-PSReadLineKeyHandler에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-837">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="80e42-838">일부 입력을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-838">Replace some of the input.</span></span> <span data-ttu-id="80e42-839">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-839">This operation supports undo/redo.</span></span> <span data-ttu-id="80e42-840">이는 실행 취소의 단일 작업으로 처리 되기 때문에 Delete 뒤에 Insert를 통해 선호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-840">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="80e42-841">커서를 지정 된 오프셋으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-841">Move the cursor to the given offset.</span></span> <span data-ttu-id="80e42-842">실행 취소를 위해 커서 이동이 추적 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-842">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="80e42-843">이 함수는 cmdlet Set-PSReadLineOption에서 사용 되는 도우미 메서드로, 설정을 일시적으로 변경 하려는 사용자 지정 키 바인딩에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-843">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="80e42-844">이 도우미 메서드는 DigitArgument을 준수 하는 사용자 지정 바인딩에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-844">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="80e42-845">일반적인 호출은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-845">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="80e42-846">참고</span><span class="sxs-lookup"><span data-stu-id="80e42-846">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="80e42-847">POWERSHELL 호환성</span><span class="sxs-lookup"><span data-stu-id="80e42-847">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="80e42-848">PSReadLine에는 PowerShell 3.0 이상 및 콘솔 호스트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-848">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="80e42-849">PowerShell ISE에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-849">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="80e42-850">Visual Studio Code 콘솔에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-850">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="80e42-851">명령 기록</span><span class="sxs-lookup"><span data-stu-id="80e42-851">COMMAND HISTORY</span></span>

<span data-ttu-id="80e42-852">PSReadLine은 명령줄에서 입력 한 모든 명령 및 데이터를 포함 하는 기록 파일을 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-852">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="80e42-853">여기에는 암호를 비롯 한 중요 한 데이터가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-853">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="80e42-854">예를 들어 cmdlet을 사용 하는 경우 `ConvertTo-SecureString` 암호는 일반 텍스트로 기록 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-854">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="80e42-855">기록 파일은 라는 파일입니다 `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="80e42-855">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="80e42-856">Windows 시스템에서 기록 파일은에 저장 됩니다 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="80e42-856">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="80e42-857">Windows가 아닌 시스템에서 기록 파일은 또는에 저장 됩니다 `$env:XDG_DATA_HOME/powershell/PSReadLine` `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="80e42-857">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="80e42-858">PSReadLine에 영향을 주는 & 피드백</span><span class="sxs-lookup"><span data-stu-id="80e42-858">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="80e42-859">GitHub의 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="80e42-859">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="80e42-860">GitHub 페이지에서 끌어오기 요청을 제출 하거나 피드백을 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-860">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="80e42-861">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80e42-861">SEE ALSO</span></span>

<span data-ttu-id="80e42-862">PSReadLine은 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 라이브러리의 영향을 많이 받습니다.</span><span class="sxs-lookup"><span data-stu-id="80e42-862">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>

