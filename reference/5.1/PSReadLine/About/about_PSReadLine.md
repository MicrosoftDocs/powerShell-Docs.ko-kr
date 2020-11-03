---
description: PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSReadLine 정보
ms.openlocfilehash: ad6e85a30f866cb332c89a4c36f42231f511f5ae
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224921"
---
# <a name="psreadline"></a><span data-ttu-id="0c8b7-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="0c8b7-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="0c8b7-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="0c8b7-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="0c8b7-107">PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="0c8b7-108">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="0c8b7-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="0c8b7-109">PSReadLine 2.0은 PowerShell 콘솔에 대 한 강력한 명령줄 편집 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="0c8b7-110">이 콘솔은 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-110">It provides:</span></span>

- <span data-ttu-id="0c8b7-111">명령줄의 구문 색 지정</span><span class="sxs-lookup"><span data-stu-id="0c8b7-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="0c8b7-112">구문 오류를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="0c8b7-113">더 나은 여러 줄 환경 (편집 및 기록 모두)</span><span class="sxs-lookup"><span data-stu-id="0c8b7-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="0c8b7-114">사용자 지정 가능한 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="0c8b7-114">Customizable key bindings</span></span>
- <span data-ttu-id="0c8b7-115">Cmd 및 Emacs 모드</span><span class="sxs-lookup"><span data-stu-id="0c8b7-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="0c8b7-116">많은 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="0c8b7-116">Many configuration options</span></span>
- <span data-ttu-id="0c8b7-117">Bash 스타일 완성 (Cmd 모드에서는 선택 사항, Emacs 모드에서는 기본값)</span><span class="sxs-lookup"><span data-stu-id="0c8b7-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="0c8b7-118">Emacs yank/kill</span><span class="sxs-lookup"><span data-stu-id="0c8b7-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="0c8b7-119">PowerShell 토큰 기반 "word" 이동 및 중지</span><span class="sxs-lookup"><span data-stu-id="0c8b7-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="0c8b7-120">다음 함수는 **[PSConsoleReadLine]** 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="0c8b7-121">기본 편집 함수</span><span class="sxs-lookup"><span data-stu-id="0c8b7-121">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="0c8b7-122">중단</span><span class="sxs-lookup"><span data-stu-id="0c8b7-122">Abort</span></span>

<span data-ttu-id="0c8b7-123">현재 작업을 중단 합니다 (예: 증분 기록 검색).</span><span class="sxs-lookup"><span data-stu-id="0c8b7-123">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="0c8b7-124">Emacs `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-124">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="0c8b7-125">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="0c8b7-125">AcceptAndGetNext</span></span>

<span data-ttu-id="0c8b7-126">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-126">Attempt to execute the current input.</span></span> <span data-ttu-id="0c8b7-127">실행 될 수 있는 경우 (예: AcceptLine) 다음에 ReadLine이 호출 될 때 기록에서 다음 항목을 회수 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-127">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="0c8b7-128">Emacs `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-128">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="0c8b7-129">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-129">AcceptLine</span></span>

<span data-ttu-id="0c8b7-130">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-130">Attempt to execute the current input.</span></span> <span data-ttu-id="0c8b7-131">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-131">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="0c8b7-132">입력 `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-132">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="0c8b7-133">Emacs `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-133">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="0c8b7-134">Vi 삽입 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-134">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="0c8b7-135">AddLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-135">AddLine</span></span>

<span data-ttu-id="0c8b7-136">연속 프롬프트가 다음 줄에 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-136">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="0c8b7-137">이는 한 줄이 자체적으로 전체 입력 인 경우에도 여러 줄 입력을 단일 명령으로 입력 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-137">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="0c8b7-138">입력 `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-138">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="0c8b7-139">Emacs `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-139">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="0c8b7-140">Vi 삽입 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-140">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="0c8b7-141">Vi 명령 모드: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-141">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="0c8b7-142">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-142">BackwardDeleteChar</span></span>

<span data-ttu-id="0c8b7-143">커서 앞에 있는 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-143">Delete the character before the cursor.</span></span>

- <span data-ttu-id="0c8b7-144">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-144">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="0c8b7-145">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-145">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="0c8b7-146">Vi 삽입 모드: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-146">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="0c8b7-147">Vi 명령 모드: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-147">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="0c8b7-148">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-148">BackwardDeleteLine</span></span>

<span data-ttu-id="0c8b7-149">Like BackwardKillLine-점에서 줄의 시작 부분으로 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-149">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="0c8b7-150">입력 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-150">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="0c8b7-151">Vi 삽입 모드: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-151">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="0c8b7-152">Vi 명령 모드: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-152">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="0c8b7-153">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-153">BackwardDeleteWord</span></span>

<span data-ttu-id="0c8b7-154">이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-154">Deletes the previous word.</span></span>

- <span data-ttu-id="0c8b7-155">Vi 명령 모드: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-155">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="0c8b7-156">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-156">BackwardKillLine</span></span>

<span data-ttu-id="0c8b7-157">커서에 대 한 입력의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-157">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="0c8b7-158">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-158">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="0c8b7-159">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-159">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="0c8b7-160">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-160">BackwardKillWord</span></span>

<span data-ttu-id="0c8b7-161">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-161">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="0c8b7-162">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-162">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="0c8b7-163">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-163">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="0c8b7-164">입력 `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-164">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="0c8b7-165">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-165">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="0c8b7-166">Vi 삽입 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-166">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="0c8b7-167">Vi 명령 모드: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-167">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="0c8b7-168">CancelLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-168">CancelLine</span></span>

<span data-ttu-id="0c8b7-169">화면에 입력을 그대로 두고 현재 입력을 취소 합니다. 그러나 프롬프트가 다시 계산 되도록 다시 호스트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-169">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="0c8b7-170">Vi 삽입 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-170">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="0c8b7-171">Vi 명령 모드: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-171">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="0c8b7-172">복사</span><span class="sxs-lookup"><span data-stu-id="0c8b7-172">Copy</span></span>

<span data-ttu-id="0c8b7-173">선택한 영역을 시스템 클립보드에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-173">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="0c8b7-174">선택 된 지역이 없으면 전체 줄을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-174">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="0c8b7-175">입력 `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-175">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="0c8b7-176">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-176">CopyOrCancelLine</span></span>

<span data-ttu-id="0c8b7-177">텍스트를 선택한 경우 클립보드로 복사 하 고, 그렇지 않으면 줄을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-177">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="0c8b7-178">입력 `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-178">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="0c8b7-179">Emacs `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-179">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="0c8b7-180">잘라내기</span><span class="sxs-lookup"><span data-stu-id="0c8b7-180">Cut</span></span>

<span data-ttu-id="0c8b7-181">삭제 된 텍스트를 시스템 클립보드에 배치 하는 선택한 영역을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-181">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="0c8b7-182">입력 `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-182">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="0c8b7-183">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-183">DeleteChar</span></span>

<span data-ttu-id="0c8b7-184">커서 아래의 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-184">Delete the character under the cursor.</span></span>

- <span data-ttu-id="0c8b7-185">입력 `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-185">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="0c8b7-186">Emacs `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-186">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="0c8b7-187">Vi 삽입 모드: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-187">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="0c8b7-188">Vi 명령 모드: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-188">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="0c8b7-189">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="0c8b7-189">DeleteCharOrExit</span></span>

<span data-ttu-id="0c8b7-190">커서 아래의 문자를 삭제 하거나, 줄이 비어 있으면 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-190">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="0c8b7-191">Emacs `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-191">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="0c8b7-192">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-192">DeleteEndOfWord</span></span>

<span data-ttu-id="0c8b7-193">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-193">Delete to the end of the word.</span></span>

- <span data-ttu-id="0c8b7-194">Vi 명령 모드: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-194">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="0c8b7-195">Deleteline.invoke</span><span class="sxs-lookup"><span data-stu-id="0c8b7-195">DeleteLine</span></span>

<span data-ttu-id="0c8b7-196">현재 줄을 삭제 하 고 실행 취소를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-196">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="0c8b7-197">Vi 명령 모드: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-197">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="0c8b7-198">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-198">DeleteLineToFirstChar</span></span>

<span data-ttu-id="0c8b7-199">커서에서 줄의 공백이 아닌 첫 번째 문자로 텍스트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-199">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="0c8b7-200">Vi 명령 모드: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-200">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="0c8b7-201">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="0c8b7-201">DeleteToEnd</span></span>

<span data-ttu-id="0c8b7-202">줄의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-202">Delete to the end of the line.</span></span>

- <span data-ttu-id="0c8b7-203">Vi 명령 모드: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-203">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="0c8b7-204">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-204">DeleteWord</span></span>

<span data-ttu-id="0c8b7-205">다음 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-205">Delete the next word.</span></span>

- <span data-ttu-id="0c8b7-206">Vi 명령 모드: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-206">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="0c8b7-207">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-207">ForwardDeleteLine</span></span>

<span data-ttu-id="0c8b7-208">Like ForwardKillLine-포인트에서 줄 끝 까지의 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-208">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="0c8b7-209">입력 `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-209">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="0c8b7-210">Vi 삽입 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-210">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="0c8b7-211">Vi 명령 모드: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-211">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="0c8b7-212">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="0c8b7-212">InsertLineAbove</span></span>

<span data-ttu-id="0c8b7-213">현재 줄에 커서가 있는 위치에 관계 없이 새 빈 줄이 현재 줄 위에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-213">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="0c8b7-214">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-214">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="0c8b7-215">입력 `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-215">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="0c8b7-216">Insertlinenea</span><span class="sxs-lookup"><span data-stu-id="0c8b7-216">InsertLineBelow</span></span>

<span data-ttu-id="0c8b7-217">커서가 현재 줄에 있는지 여부에 관계 없이 현재 줄 아래에 빈 줄이 새로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-217">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="0c8b7-218">커서가 새 줄의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="0c8b7-219">입력 `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-219">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="0c8b7-220">InvertCase</span><span class="sxs-lookup"><span data-stu-id="0c8b7-220">InvertCase</span></span>

<span data-ttu-id="0c8b7-221">현재 문자의 대/소문자를 반전 하 고 다음으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-221">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="0c8b7-222">Vi 명령 모드: `<~>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-222">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="0c8b7-223">KillLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-223">KillLine</span></span>

<span data-ttu-id="0c8b7-224">입력의 끝 부분까지 커서에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-224">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="0c8b7-225">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-225">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="0c8b7-226">Emacs `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-226">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="0c8b7-227">KillRegion</span><span class="sxs-lookup"><span data-stu-id="0c8b7-227">KillRegion</span></span>

<span data-ttu-id="0c8b7-228">커서와 표시 사이에 있는 텍스트를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-228">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="0c8b7-229">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-229">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="0c8b7-230">KillWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-230">KillWord</span></span>

<span data-ttu-id="0c8b7-231">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-231">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="0c8b7-232">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-232">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="0c8b7-233">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-233">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="0c8b7-234">입력 `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-234">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="0c8b7-235">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-235">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="0c8b7-236">Vi 삽입 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-236">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="0c8b7-237">Vi 명령 모드: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-237">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="0c8b7-238">붙여넣기</span><span class="sxs-lookup"><span data-stu-id="0c8b7-238">Paste</span></span>

<span data-ttu-id="0c8b7-239">시스템 클립보드에서 텍스트를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-239">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="0c8b7-240">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-240">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="0c8b7-241">Vi 삽입 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-241">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="0c8b7-242">Vi 명령 모드: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-242">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c8b7-243">**Paste** 함수를 사용 하는 경우 클립보드 버퍼의 전체 내용이 psreadline의 입력 버퍼에 붙여넣어집니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-243">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="0c8b7-244">그런 다음 입력 버퍼가 PowerShell 파서로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-244">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="0c8b7-245">콘솔 응용 프로그램의 **마우스 오른쪽 단추 클릭** 붙여넣기 메서드를 사용 하 여 붙여넣은 입력은 입력 버퍼에 한 번에 한 문자씩 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-245">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="0c8b7-246">입력 버퍼는 줄 바꿈 문자가 복사 될 때 파서에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-246">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="0c8b7-247">따라서 입력은 한 번에 한 줄씩 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-247">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="0c8b7-248">붙여넣기 메서드 간의 차이점으로 인해 실행 동작이 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-248">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="0c8b7-249">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="0c8b7-249">PasteAfter</span></span>

<span data-ttu-id="0c8b7-250">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 뒤에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-250">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="0c8b7-251">Vi 명령 모드: `<p>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-251">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="0c8b7-252">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="0c8b7-252">PasteBefore</span></span>

<span data-ttu-id="0c8b7-253">커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 앞에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-253">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="0c8b7-254">Vi 명령 모드: `<P>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-254">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="0c8b7-255">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="0c8b7-255">PrependAndAccept</span></span>

<span data-ttu-id="0c8b7-256">' # ' 앞에를 추가 하 고 줄을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-256">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="0c8b7-257">Vi 명령 모드: `<#>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-257">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="0c8b7-258">다시 실행</span><span class="sxs-lookup"><span data-stu-id="0c8b7-258">Redo</span></span>

<span data-ttu-id="0c8b7-259">실행 취소를 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-259">Undo an undo.</span></span>

- <span data-ttu-id="0c8b7-260">입력 `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-260">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="0c8b7-261">Vi 삽입 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-261">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="0c8b7-262">Vi 명령 모드: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-262">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="0c8b7-263">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="0c8b7-263">RepeatLastCommand</span></span>

<span data-ttu-id="0c8b7-264">마지막 텍스트 수정 작업을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-264">Repeat the last text modification.</span></span>

- <span data-ttu-id="0c8b7-265">Vi 명령 모드: `<.>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-265">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="0c8b7-266">RevertLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-266">RevertLine</span></span>

<span data-ttu-id="0c8b7-267">모든 입력을 현재 입력으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-267">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="0c8b7-268">입력 `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-268">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="0c8b7-269">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-269">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="0c8b7-270">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-270">ShellBackwardKillWord</span></span>

<span data-ttu-id="0c8b7-271">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-271">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="0c8b7-272">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-272">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="0c8b7-273">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-273">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="0c8b7-274">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-274">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="0c8b7-275">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-275">ShellKillWord</span></span>

<span data-ttu-id="0c8b7-276">커서에서 현재 단어의 끝까지 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-276">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="0c8b7-277">커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-277">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="0c8b7-278">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-278">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="0c8b7-279">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-279">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="0c8b7-280">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="0c8b7-280">SwapCharacters</span></span>

<span data-ttu-id="0c8b7-281">현재 문자와 그 앞의 문자를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-281">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="0c8b7-282">Emacs `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-282">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="0c8b7-283">Vi 삽입 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-283">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="0c8b7-284">Vi 명령 모드: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-284">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="0c8b7-285">실행 취소</span><span class="sxs-lookup"><span data-stu-id="0c8b7-285">Undo</span></span>

<span data-ttu-id="0c8b7-286">이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-286">Undo a previous edit.</span></span>

- <span data-ttu-id="0c8b7-287">입력 `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-287">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="0c8b7-288">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-288">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="0c8b7-289">Vi 삽입 모드: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-289">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="0c8b7-290">Vi 명령 모드: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-290">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="0c8b7-291">모두를</span><span class="sxs-lookup"><span data-stu-id="0c8b7-291">UndoAll</span></span>

<span data-ttu-id="0c8b7-292">줄의 모든 이전 편집을 실행 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-292">Undo all previous edits for line.</span></span>

- <span data-ttu-id="0c8b7-293">Vi 명령 모드: `<U>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-293">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="0c8b7-294">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="0c8b7-294">UnixWordRubout</span></span>

<span data-ttu-id="0c8b7-295">커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-295">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="0c8b7-296">커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-296">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="0c8b7-297">지워진 텍스트는 kill 링에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-297">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="0c8b7-298">Emacs `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-298">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="0c8b7-299">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-299">ValidateAndAcceptLine</span></span>

<span data-ttu-id="0c8b7-300">현재 입력을 실행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-300">Attempt to execute the current input.</span></span> <span data-ttu-id="0c8b7-301">누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-301">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="0c8b7-302">Emacs `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-302">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="0c8b7-303">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-303">ViAcceptLine</span></span>

<span data-ttu-id="0c8b7-304">줄을 적용 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-304">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="0c8b7-305">Vi 명령 모드: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-305">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="0c8b7-306">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="0c8b7-306">ViAcceptLineOrExit</span></span>

<span data-ttu-id="0c8b7-307">Emacs 모드에서 DeleteCharOrExit와 비슷하지만 문자를 삭제 하는 대신 줄을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-307">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="0c8b7-308">Vi 삽입 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-308">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="0c8b7-309">Vi 명령 모드: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-309">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="0c8b7-310">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-310">ViAppendLine</span></span>

<span data-ttu-id="0c8b7-311">현재 줄 아래에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-311">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="0c8b7-312">Vi 명령 모드: `<o>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-312">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="0c8b7-313">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-313">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="0c8b7-314">공백을 단어 구분 기호로 사용 하 여 이전 단어를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-314">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="0c8b7-315">Vi 명령 모드: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-315">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="0c8b7-316">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-316">ViBackwardGlob</span></span>

<span data-ttu-id="0c8b7-317">공백을 구분 기호로 사용 하 여 커서를 이전 단어의 시작 부분으로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-317">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="0c8b7-318">Vi 명령 모드: `<B>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-318">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="0c8b7-319">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="0c8b7-319">ViDeleteBrace</span></span>

<span data-ttu-id="0c8b7-320">괄호를 포함 하 여 일치 하는 중괄호, 괄호 또는 대괄호를 찾아 내에서 모든 내용을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-320">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="0c8b7-321">Vi 명령 모드: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-321">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="0c8b7-322">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-322">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="0c8b7-323">단어의 끝까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-323">Delete to the end of the word.</span></span>

- <span data-ttu-id="0c8b7-324">Vi 명령 모드: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-324">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="0c8b7-325">Videletlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-325">ViDeleteGlob</span></span>

<span data-ttu-id="0c8b7-326">다음 glob (공백으로 구분 된 단어)를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-326">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="0c8b7-327">Vi 명령 모드: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-327">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="0c8b7-328">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-328">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="0c8b7-329">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-329">Deletes until given character.</span></span>

- <span data-ttu-id="0c8b7-330">Vi 명령 모드: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-330">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="0c8b7-331">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-331">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="0c8b7-332">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-332">Deletes until given character.</span></span>

- <span data-ttu-id="0c8b7-333">Vi 명령 모드: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-333">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="0c8b7-334">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-334">ViDeleteToChar</span></span>

<span data-ttu-id="0c8b7-335">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-335">Deletes until given character.</span></span>

- <span data-ttu-id="0c8b7-336">Vi 명령 모드: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-336">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="0c8b7-337">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-337">ViDeleteToCharBackward</span></span>

<span data-ttu-id="0c8b7-338">지정 된 문자까지 뒤로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-338">Deletes backwards until given character.</span></span>

- <span data-ttu-id="0c8b7-339">Vi 명령 모드: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-339">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="0c8b7-340">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="0c8b7-340">ViInsertAtBegining</span></span>

<span data-ttu-id="0c8b7-341">삽입 모드로 전환 하 고 줄의 시작 부분에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-341">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="0c8b7-342">Vi 명령 모드: `<I>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-342">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="0c8b7-343">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="0c8b7-343">ViInsertAtEnd</span></span>

<span data-ttu-id="0c8b7-344">삽입 모드로 전환 하 고 줄의 끝에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-344">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="0c8b7-345">Vi 명령 모드: `<A>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-345">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="0c8b7-346">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-346">ViInsertLine</span></span>

<span data-ttu-id="0c8b7-347">현재 줄 위에 새 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-347">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="0c8b7-348">Vi 명령 모드: `<O>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-348">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="0c8b7-349">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="0c8b7-349">ViInsertWithAppend</span></span>

<span data-ttu-id="0c8b7-350">현재 줄 위치에서 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-350">Append from the current line position.</span></span>

- <span data-ttu-id="0c8b7-351">Vi 명령 모드: `<a>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-351">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="0c8b7-352">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="0c8b7-352">ViInsertWithDelete</span></span>

<span data-ttu-id="0c8b7-353">현재 문자를 삭제 하 고 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-353">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="0c8b7-354">Vi 명령 모드: `<s>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-354">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="0c8b7-355">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="0c8b7-355">ViJoinLines</span></span>

<span data-ttu-id="0c8b7-356">현재 줄과 다음 줄을 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-356">Joins the current line and the next line.</span></span>

- <span data-ttu-id="0c8b7-357">Vi 명령 모드: `<J>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-357">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="0c8b7-358">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-358">ViReplaceLine</span></span>

<span data-ttu-id="0c8b7-359">전체 명령줄을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-359">Erase the entire command line.</span></span>

- <span data-ttu-id="0c8b7-360">Vi 명령 모드: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-360">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="0c8b7-361">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-361">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="0c8b7-362">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-362">Replaces until given character.</span></span>

- <span data-ttu-id="0c8b7-363">Vi 명령 모드: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-363">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="0c8b7-364">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-364">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="0c8b7-365">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-365">Replaces until given character.</span></span>

- <span data-ttu-id="0c8b7-366">Vi 명령 모드: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-366">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="0c8b7-367">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-367">ViReplaceToChar</span></span>

<span data-ttu-id="0c8b7-368">지정 된 문자가 나타날 때까지 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-368">Deletes until given character.</span></span>

- <span data-ttu-id="0c8b7-369">Vi 명령 모드: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-369">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="0c8b7-370">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-370">ViReplaceToCharBackward</span></span>

<span data-ttu-id="0c8b7-371">지정 된 문자가 될 때까지 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-371">Replaces until given character.</span></span>

- <span data-ttu-id="0c8b7-372">Vi 명령 모드: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-372">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="0c8b7-373">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-373">ViYankBeginningOfLine</span></span>

<span data-ttu-id="0c8b7-374">버퍼의 시작 부분에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-374">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="0c8b7-375">Vi 명령 모드: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-375">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="0c8b7-376">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-376">ViYankEndOfGlob</span></span>

<span data-ttu-id="0c8b7-377">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-377">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="0c8b7-378">Vi 명령 모드: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-378">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="0c8b7-379">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-379">ViYankEndOfWord</span></span>

<span data-ttu-id="0c8b7-380">커서에서 단어의 끝까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-380">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="0c8b7-381">Vi 명령 모드: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-381">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="0c8b7-382">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="0c8b7-382">ViYankLeft</span></span>

<span data-ttu-id="0c8b7-383">커서의 왼쪽에 문자를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-383">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="0c8b7-384">Vi 명령 모드: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-384">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="0c8b7-385">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-385">ViYankLine</span></span>

<span data-ttu-id="0c8b7-386">전체 버퍼를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-386">Yank the entire buffer.</span></span>

- <span data-ttu-id="0c8b7-387">Vi 명령 모드: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-387">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="0c8b7-388">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-388">ViYankNextGlob</span></span>

<span data-ttu-id="0c8b7-389">커서에서 다음 단어의 시작 부분으로 Yank.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-389">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="0c8b7-390">Vi 명령 모드: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-390">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="0c8b7-391">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-391">ViYankNextWord</span></span>

<span data-ttu-id="0c8b7-392">커서 뒤의 단어를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-392">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="0c8b7-393">Vi 명령 모드: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-393">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="0c8b7-394">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="0c8b7-394">ViYankPercent</span></span>

<span data-ttu-id="0c8b7-395">짝이 되는 중괄호에서 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-395">Yank to/from matching brace.</span></span>

- <span data-ttu-id="0c8b7-396">Vi 명령 모드: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-396">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="0c8b7-397">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-397">ViYankPreviousGlob</span></span>

<span data-ttu-id="0c8b7-398">단어의 시작부터 커서까지 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-398">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="0c8b7-399">Vi 명령 모드: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-399">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="0c8b7-400">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-400">ViYankPreviousWord</span></span>

<span data-ttu-id="0c8b7-401">커서 앞에 단어를 Yank.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-401">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="0c8b7-402">Vi 명령 모드: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-402">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="0c8b7-403">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="0c8b7-403">ViYankRight</span></span>

<span data-ttu-id="0c8b7-404">커서 오른쪽의 및 아래에 Yank 문자를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-404">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="0c8b7-405">Vi 명령 모드: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-405">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="0c8b7-406">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-406">ViYankToEndOfLine</span></span>

<span data-ttu-id="0c8b7-407">커서에서 버퍼 끝까지 Yank.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-407">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="0c8b7-408">Vi 명령 모드: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-408">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="0c8b7-409">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-409">ViYankToFirstChar</span></span>

<span data-ttu-id="0c8b7-410">공백이 아닌 첫 번째 문자에서 커서로 Yank.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-410">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="0c8b7-411">Vi 명령 모드: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-411">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="0c8b7-412">Yank</span><span class="sxs-lookup"><span data-stu-id="0c8b7-412">Yank</span></span>

<span data-ttu-id="0c8b7-413">가장 최근에 종료 된 텍스트를 입력에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-413">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="0c8b7-414">Emacs `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-414">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="0c8b7-415">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="0c8b7-415">YankLastArg</span></span>

<span data-ttu-id="0c8b7-416">이전 기록 줄에서 마지막 인수를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-416">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="0c8b7-417">인수를 사용 하면 처음 호출 될 때 YankNthArg 처럼 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-417">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="0c8b7-418">여러 번 호출 된 경우에는 기록 및 인수에서 방향을 설정 합니다. (음수는 방향을 반대로 바꿉니다.)</span><span class="sxs-lookup"><span data-stu-id="0c8b7-418">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="0c8b7-419">입력 `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-419">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="0c8b7-420">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-420">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="0c8b7-421">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="0c8b7-421">YankNthArg</span></span>

<span data-ttu-id="0c8b7-422">이전 기록 줄에서 첫 번째 인수 (명령 뒤)를 Yank 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-422">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="0c8b7-423">인수를 사용 하는 경우 n 번째 인수 (0부터 시작)를 yank. 인수가 음수 이면 마지막 인수부터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-423">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="0c8b7-424">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-424">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="0c8b7-425">YankPop</span><span class="sxs-lookup"><span data-stu-id="0c8b7-425">YankPop</span></span>

<span data-ttu-id="0c8b7-426">이전 작업이 Yank 또는 YankPop 인 경우 이전 빼낼 텍스트를 kill 링에서 다음에 종료 된 텍스트로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-426">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="0c8b7-427">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-427">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="0c8b7-428">커서 이동 함수</span><span class="sxs-lookup"><span data-stu-id="0c8b7-428">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="0c8b7-429">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-429">BackwardChar</span></span>

<span data-ttu-id="0c8b7-430">커서를 한 문자 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-430">Move the cursor one character to the left.</span></span> <span data-ttu-id="0c8b7-431">이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-431">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="0c8b7-432">입력 `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-432">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="0c8b7-433">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-433">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="0c8b7-434">Vi 삽입 모드: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-434">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="0c8b7-435">Vi 명령 모드: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-435">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="0c8b7-436">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-436">BackwardWord</span></span>

<span data-ttu-id="0c8b7-437">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-437">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="0c8b7-438">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-438">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="0c8b7-439">입력 `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-439">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="0c8b7-440">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-440">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="0c8b7-441">Vi 삽입 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-441">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="0c8b7-442">Vi 명령 모드: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-442">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="0c8b7-443">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-443">BeginningOfLine</span></span>

<span data-ttu-id="0c8b7-444">입력에 여러 줄이 있는 경우 현재 줄의 시작 부분으로 이동 하거나 이미 줄의 시작 부분에 있는 경우 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-444">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="0c8b7-445">입력에 한 줄이 있으면 입력의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-445">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="0c8b7-446">입력 `<Home>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-446">Cmd: `<Home>`</span></span>
- <span data-ttu-id="0c8b7-447">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-447">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="0c8b7-448">Vi 삽입 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-448">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="0c8b7-449">Vi 명령 모드: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-449">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="0c8b7-450">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-450">EndOfLine</span></span>

<span data-ttu-id="0c8b7-451">입력에 여러 줄이 있는 경우 현재 줄의 끝으로 이동 하거나 줄의 끝에 있는 경우 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-451">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="0c8b7-452">입력에 한 줄이 있으면 입력의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-452">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="0c8b7-453">입력 `<End>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-453">Cmd: `<End>`</span></span>
- <span data-ttu-id="0c8b7-454">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-454">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="0c8b7-455">Vi 삽입 모드: `<End>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-455">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="0c8b7-456">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-456">ForwardChar</span></span>

<span data-ttu-id="0c8b7-457">커서를 한 문자 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-457">Move the cursor one character to the right.</span></span> <span data-ttu-id="0c8b7-458">그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-458">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="0c8b7-459">입력 `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-459">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="0c8b7-460">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-460">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="0c8b7-461">Vi 삽입 모드: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-461">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="0c8b7-462">Vi 명령 모드: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-462">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="0c8b7-463">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-463">ForwardWord</span></span>

<span data-ttu-id="0c8b7-464">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-464">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="0c8b7-465">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-465">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="0c8b7-466">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-466">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="0c8b7-467">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="0c8b7-467">GotoBrace</span></span>

<span data-ttu-id="0c8b7-468">짝이 되는 중괄호, 괄호 또는 대괄호로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-468">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="0c8b7-469">입력 `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-469">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="0c8b7-470">Vi 삽입 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-470">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="0c8b7-471">Vi 명령 모드: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-471">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="0c8b7-472">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="0c8b7-472">GotoColumn</span></span>

<span data-ttu-id="0c8b7-473">Arg로 표시 된 열로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-473">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="0c8b7-474">Vi 명령 모드: `<|>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-474">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="0c8b7-475">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-475">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="0c8b7-476">줄에서 비어 있지 않은 첫 번째 문자로 커서를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-476">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="0c8b7-477">Vi 명령 모드: `<^>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-477">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="0c8b7-478">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-478">MoveToEndOfLine</span></span>

<span data-ttu-id="0c8b7-479">커서를 입력 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-479">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="0c8b7-480">Vi 명령 모드: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-480">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="0c8b7-481">NextLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-481">NextLine</span></span>

<span data-ttu-id="0c8b7-482">커서를 다음 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-482">Move the cursor to the next line.</span></span>

- <span data-ttu-id="0c8b7-483">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-483">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="0c8b7-484">NextWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-484">NextWord</span></span>

<span data-ttu-id="0c8b7-485">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-485">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="0c8b7-486">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-486">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="0c8b7-487">입력 `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-487">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="0c8b7-488">Vi 삽입 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-488">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="0c8b7-489">Vi 명령 모드: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-489">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="0c8b7-490">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="0c8b7-490">NextWordEnd</span></span>

<span data-ttu-id="0c8b7-491">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-491">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="0c8b7-492">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-492">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="0c8b7-493">Vi 명령 모드: `<e>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-493">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="0c8b7-494">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-494">PreviousLine</span></span>

<span data-ttu-id="0c8b7-495">커서를 이전 줄로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-495">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="0c8b7-496">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-496">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="0c8b7-497">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-497">ShellBackwardWord</span></span>

<span data-ttu-id="0c8b7-498">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-498">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="0c8b7-499">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-499">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="0c8b7-500">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-500">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="0c8b7-501">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-501">ShellForwardWord</span></span>

<span data-ttu-id="0c8b7-502">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-502">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="0c8b7-503">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="0c8b7-504">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-504">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="0c8b7-505">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-505">ShellNextWord</span></span>

<span data-ttu-id="0c8b7-506">커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-506">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="0c8b7-507">단어 경계는 PowerShell 토큰에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="0c8b7-508">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-508">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="0c8b7-509">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-509">ViBackwardWord</span></span>

<span data-ttu-id="0c8b7-510">커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-510">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="0c8b7-511">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-511">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="0c8b7-512">Vi 명령 모드: `<b>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-512">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="0c8b7-513">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-513">ViEndOfGlob</span></span>

<span data-ttu-id="0c8b7-514">공백을 구분 기호로 사용 하 여 커서를 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-514">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="0c8b7-515">Vi 명령 모드: `<E>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-515">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="0c8b7-516">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-516">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="0c8b7-517">공백을 단어 구분 기호로 사용 하 여 이전 단어의 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-517">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="0c8b7-518">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-518">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="0c8b7-519">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="0c8b7-519">ViGotoBrace</span></span>

<span data-ttu-id="0c8b7-520">GotoBrace와 비슷하지만 토큰 기반이 아니라 문자 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-520">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="0c8b7-521">Vi 명령 모드: `<%>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-521">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="0c8b7-522">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="0c8b7-522">ViNextGlob</span></span>

<span data-ttu-id="0c8b7-523">공백을 단어 구분 기호로 사용 하 여 다음 단어로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-523">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="0c8b7-524">Vi 명령 모드: `<W>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-524">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="0c8b7-525">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-525">ViNextWord</span></span>

<span data-ttu-id="0c8b7-526">커서를 다음 단어의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-526">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="0c8b7-527">단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-527">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="0c8b7-528">Vi 명령 모드: `<w>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-528">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="0c8b7-529">기록 함수</span><span class="sxs-lookup"><span data-stu-id="0c8b7-529">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="0c8b7-530">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="0c8b7-530">BeginningOfHistory</span></span>

<span data-ttu-id="0c8b7-531">기록의 첫 번째 항목으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-531">Move to the first item in the history.</span></span>

- <span data-ttu-id="0c8b7-532">Emacs `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-532">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="0c8b7-533">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="0c8b7-533">ClearHistory</span></span>

<span data-ttu-id="0c8b7-534">PSReadLine에서 기록을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-534">Clears history in PSReadLine.</span></span> <span data-ttu-id="0c8b7-535">PowerShell 기록에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-535">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="0c8b7-536">입력 `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-536">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="0c8b7-537">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="0c8b7-537">EndOfHistory</span></span>

<span data-ttu-id="0c8b7-538">기록에서 마지막 항목 (현재 입력)으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-538">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="0c8b7-539">Emacs `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-539">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="0c8b7-540">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="0c8b7-540">ForwardSearchHistory</span></span>

<span data-ttu-id="0c8b7-541">기록을 통해 증분 전달 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-541">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="0c8b7-542">입력 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-542">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="0c8b7-543">Emacs `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-543">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="0c8b7-544">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-544">HistorySearchBackward</span></span>

<span data-ttu-id="0c8b7-545">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-545">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="0c8b7-546">입력 `<F8>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-546">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="0c8b7-547">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-547">HistorySearchForward</span></span>

<span data-ttu-id="0c8b7-548">현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-548">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="0c8b7-549">입력 `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-549">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="0c8b7-550">NextHistory</span><span class="sxs-lookup"><span data-stu-id="0c8b7-550">NextHistory</span></span>

<span data-ttu-id="0c8b7-551">현재 입력을 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-551">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="0c8b7-552">입력 `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-552">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="0c8b7-553">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-553">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="0c8b7-554">Vi 삽입 모드: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-554">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="0c8b7-555">Vi 명령 모드: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-555">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="0c8b7-556">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="0c8b7-556">PreviousHistory</span></span>

<span data-ttu-id="0c8b7-557">현재 입력을 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-557">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="0c8b7-558">입력 `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-558">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="0c8b7-559">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-559">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="0c8b7-560">Vi 삽입 모드: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-560">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="0c8b7-561">Vi 명령 모드: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-561">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="0c8b7-562">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="0c8b7-562">ReverseSearchHistory</span></span>

<span data-ttu-id="0c8b7-563">기록을 통해 증분 역방향 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-563">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="0c8b7-564">입력 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-564">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="0c8b7-565">Emacs `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-565">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="0c8b7-566">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-566">ViSearchHistoryBackward</span></span>

<span data-ttu-id="0c8b7-567">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-567">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="0c8b7-568">Vi 삽입 모드: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-568">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="0c8b7-569">Vi 명령 모드: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-569">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="0c8b7-570">완료 함수</span><span class="sxs-lookup"><span data-stu-id="0c8b7-570">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="0c8b7-571">완료</span><span class="sxs-lookup"><span data-stu-id="0c8b7-571">Complete</span></span>

<span data-ttu-id="0c8b7-572">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-572">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="0c8b7-573">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-573">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="0c8b7-574">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-574">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="0c8b7-575">Emacs `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-575">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="0c8b7-576">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="0c8b7-576">MenuComplete</span></span>

<span data-ttu-id="0c8b7-577">커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-577">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="0c8b7-578">가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-578">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="0c8b7-579">가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-579">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="0c8b7-580">입력 `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-580">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="0c8b7-581">Emacs `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-581">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="0c8b7-582">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="0c8b7-582">PossibleCompletions</span></span>

<span data-ttu-id="0c8b7-583">가능한 완료 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-583">Display the list of possible completions.</span></span>

- <span data-ttu-id="0c8b7-584">Emacs `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-584">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="0c8b7-585">Vi 삽입 모드: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-585">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="0c8b7-586">Vi 명령 모드: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-586">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="0c8b7-587">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="0c8b7-587">TabCompleteNext</span></span>

<span data-ttu-id="0c8b7-588">다음에 사용 가능한 완료로 커서를 둘러싼 텍스트를 완성 해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-588">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="0c8b7-589">입력 `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-589">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="0c8b7-590">Vi 명령 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-590">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="0c8b7-591">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="0c8b7-591">TabCompletePrevious</span></span>

<span data-ttu-id="0c8b7-592">이전에 사용 가능한 완료를 사용 하 여 커서를 둘러싼 텍스트를 완료 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-592">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="0c8b7-593">입력 `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-593">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="0c8b7-594">Vi 명령 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-594">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="0c8b7-595">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="0c8b7-595">ViTabCompleteNext</span></span>

<span data-ttu-id="0c8b7-596">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompleteNext를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-596">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="0c8b7-597">Vi 삽입 모드: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-597">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="0c8b7-598">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="0c8b7-598">ViTabCompletePrevious</span></span>

<span data-ttu-id="0c8b7-599">필요한 경우 현재 편집 그룹을 종료 하 고 TabCompletePrevious를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-599">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="0c8b7-600">Vi 삽입 모드: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-600">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="0c8b7-601">기타 함수</span><span class="sxs-lookup"><span data-stu-id="0c8b7-601">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="0c8b7-602">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="0c8b7-602">CaptureScreen</span></span>

<span data-ttu-id="0c8b7-603">대화형 화면 캡처 시작-위쪽/아래쪽 화살표 선 선택, 선택한 텍스트를 클립보드에 텍스트 및 html로 복사를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-603">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="0c8b7-604">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-604">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="0c8b7-605">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="0c8b7-605">ClearScreen</span></span>

<span data-ttu-id="0c8b7-606">화면을 지우고 화면 위쪽에 현재 줄을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-606">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="0c8b7-607">입력 `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-607">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="0c8b7-608">Emacs `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-608">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="0c8b7-609">Vi 삽입 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-609">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="0c8b7-610">Vi 명령 모드: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-610">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="0c8b7-611">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="0c8b7-611">DigitArgument</span></span>

<span data-ttu-id="0c8b7-612">다른 함수에 전달할 새 숫자 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-612">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="0c8b7-613">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-613">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="0c8b7-614">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-614">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="0c8b7-615">Vi 명령 모드: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` `<7>` `<8>` ,,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-615">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="0c8b7-616">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="0c8b7-616">InvokePrompt</span></span>

<span data-ttu-id="0c8b7-617">현재 프롬프트를 지우고 prompt 함수를 호출 하 여 프롬프트를 다시 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-617">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="0c8b7-618">상태를 변경 하는 사용자 지정 키 처리기 (예: 현재 디렉터리 변경)에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-618">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="0c8b7-619">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-619">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="0c8b7-620">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="0c8b7-620">ScrollDisplayDown</span></span>

<span data-ttu-id="0c8b7-621">한 화면 아래로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-621">Scroll the display down one screen.</span></span>

- <span data-ttu-id="0c8b7-622">입력 `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-622">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="0c8b7-623">Emacs `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-623">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="0c8b7-624">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-624">ScrollDisplayDownLine</span></span>

<span data-ttu-id="0c8b7-625">표시를 한 줄 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-625">Scroll the display down one line.</span></span>

- <span data-ttu-id="0c8b7-626">입력 `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-626">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="0c8b7-627">Emacs `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-627">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="0c8b7-628">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="0c8b7-628">ScrollDisplayToCursor</span></span>

<span data-ttu-id="0c8b7-629">표시를 커서로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-629">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="0c8b7-630">Emacs `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-630">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="0c8b7-631">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="0c8b7-631">ScrollDisplayTop</span></span>

<span data-ttu-id="0c8b7-632">표시를 맨 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-632">Scroll the display to the top.</span></span>

- <span data-ttu-id="0c8b7-633">Emacs `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-633">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="0c8b7-634">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="0c8b7-634">ScrollDisplayUp</span></span>

<span data-ttu-id="0c8b7-635">한 화면 위로 표시를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-635">Scroll the display up one screen.</span></span>

- <span data-ttu-id="0c8b7-636">입력 `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-636">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="0c8b7-637">Emacs `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-637">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="0c8b7-638">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-638">ScrollDisplayUpLine</span></span>

<span data-ttu-id="0c8b7-639">디스플레이를 한 줄 위로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-639">Scroll the display up one line.</span></span>

- <span data-ttu-id="0c8b7-640">입력 `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-640">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="0c8b7-641">Emacs `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-641">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="0c8b7-642">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="0c8b7-642">SelfInsert</span></span>

<span data-ttu-id="0c8b7-643">키를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-643">Insert the key.</span></span>

- <span data-ttu-id="0c8b7-644">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-644">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="0c8b7-645">ShowKeyBindings 바인딩</span><span class="sxs-lookup"><span data-stu-id="0c8b7-645">ShowKeyBindings</span></span>

<span data-ttu-id="0c8b7-646">모든 바인딩된 키를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-646">Show all bound keys.</span></span>

- <span data-ttu-id="0c8b7-647">입력 `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-647">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="0c8b7-648">Emacs `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-648">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="0c8b7-649">Vi 삽입 모드: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-649">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="0c8b7-650">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="0c8b7-650">ViCommandMode</span></span>

<span data-ttu-id="0c8b7-651">Vi-Insert에서 현재 운영 모드를 Vi 명령으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-651">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="0c8b7-652">Vi 삽입 모드: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-652">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="0c8b7-653">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-653">ViDigitArgumentInChord</span></span>

<span data-ttu-id="0c8b7-654">Vi의 누르는 중 하나에서 다른 함수에 전달할 새 digit 인수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-654">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="0c8b7-655">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-655">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="0c8b7-656">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="0c8b7-656">ViEditVisually</span></span>

<span data-ttu-id="0c8b7-657">$Env: 편집기 또는 $env: 시각적 개체에 지정 된 텍스트 편집기에서 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-657">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="0c8b7-658">Emacs `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-658">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="0c8b7-659">Vi 명령 모드: `<v>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-659">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="0c8b7-660">ViExit</span><span class="sxs-lookup"><span data-stu-id="0c8b7-660">ViExit</span></span>

<span data-ttu-id="0c8b7-661">셸을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-661">Exits the shell.</span></span>

- <span data-ttu-id="0c8b7-662">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-662">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="0c8b7-663">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="0c8b7-663">ViInsertMode</span></span>

<span data-ttu-id="0c8b7-664">삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-664">Switch to Insert mode.</span></span>

- <span data-ttu-id="0c8b7-665">Vi 명령 모드: `<i>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-665">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="0c8b7-666">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="0c8b7-666">WhatIsKey</span></span>

<span data-ttu-id="0c8b7-667">키를 읽고 키가 바인딩된 정보를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-667">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="0c8b7-668">입력 `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-668">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="0c8b7-669">Emacs `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-669">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="0c8b7-670">선택 함수</span><span class="sxs-lookup"><span data-stu-id="0c8b7-670">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="0c8b7-671">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="0c8b7-671">ExchangePointAndMark</span></span>

<span data-ttu-id="0c8b7-672">커서는 표시 위치에 배치 되 고 표시는 커서의 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-672">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="0c8b7-673">Emacs `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-673">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="0c8b7-674">SelectAll</span><span class="sxs-lookup"><span data-stu-id="0c8b7-674">SelectAll</span></span>

<span data-ttu-id="0c8b7-675">전체 줄을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-675">Select the entire line.</span></span>

- <span data-ttu-id="0c8b7-676">입력 `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-676">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="0c8b7-677">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-677">SelectBackwardChar</span></span>

<span data-ttu-id="0c8b7-678">이전 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-678">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="0c8b7-679">입력 `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-679">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="0c8b7-680">Emacs `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-680">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="0c8b7-681">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-681">SelectBackwardsLine</span></span>

<span data-ttu-id="0c8b7-682">커서에서 줄의 시작 부분까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-682">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="0c8b7-683">입력 `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-683">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="0c8b7-684">Emacs `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-684">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="0c8b7-685">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-685">SelectBackwardWord</span></span>

<span data-ttu-id="0c8b7-686">이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-686">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="0c8b7-687">입력 `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-687">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="0c8b7-688">Emacs `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-688">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="0c8b7-689">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-689">SelectForwardChar</span></span>

<span data-ttu-id="0c8b7-690">다음 문자를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-690">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="0c8b7-691">입력 `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-691">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="0c8b7-692">Emacs `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-692">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="0c8b7-693">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-693">SelectForwardWord</span></span>

<span data-ttu-id="0c8b7-694">ForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-694">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="0c8b7-695">Emacs `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-695">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="0c8b7-696">줄을 select</span><span class="sxs-lookup"><span data-stu-id="0c8b7-696">SelectLine</span></span>

<span data-ttu-id="0c8b7-697">커서에서 줄의 끝까지 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-697">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="0c8b7-698">입력 `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-698">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="0c8b7-699">Emacs `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-699">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="0c8b7-700">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-700">SelectNextWord</span></span>

<span data-ttu-id="0c8b7-701">다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-701">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="0c8b7-702">입력 `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-702">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="0c8b7-703">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-703">SelectShellBackwardWord</span></span>

<span data-ttu-id="0c8b7-704">ShellBackwardWord를 사용 하 여 이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-704">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="0c8b7-705">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-705">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="0c8b7-706">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-706">SelectShellForwardWord</span></span>

<span data-ttu-id="0c8b7-707">ShellForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-707">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="0c8b7-708">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-708">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="0c8b7-709">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="0c8b7-709">SelectShellNextWord</span></span>

<span data-ttu-id="0c8b7-710">ShellNextWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-710">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="0c8b7-711">함수가 바인딩 해제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-711">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="0c8b7-712">SetMark</span><span class="sxs-lookup"><span data-stu-id="0c8b7-712">SetMark</span></span>

<span data-ttu-id="0c8b7-713">이후 편집 명령에 사용할 커서의 현재 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-713">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="0c8b7-714">Emacs `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-714">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="0c8b7-715">검색 함수</span><span class="sxs-lookup"><span data-stu-id="0c8b7-715">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="0c8b7-716">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="0c8b7-716">CharacterSearch</span></span>

<span data-ttu-id="0c8b7-717">문자를 읽고 그 다음 번에 해당 문자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-717">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="0c8b7-718">인수를 지정 하는 경우 n 번째 발생에 대해 앞으로 (음수 이면 뒤로) 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-718">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="0c8b7-719">입력 `<F3>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-719">Cmd: `<F3>`</span></span>
- <span data-ttu-id="0c8b7-720">Emacs `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-720">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="0c8b7-721">Vi 삽입 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-721">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="0c8b7-722">Vi 명령 모드: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-722">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="0c8b7-723">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-723">CharacterSearchBackward</span></span>

<span data-ttu-id="0c8b7-724">문자를 읽은 다음 해당 문자의 다음 항목을 뒤로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-724">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="0c8b7-725">인수를 지정 하는 경우 n 번째 발생에 대해 뒤로 검색 하거나 음수 이면 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-725">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="0c8b7-726">입력 `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-726">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="0c8b7-727">Emacs `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-727">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="0c8b7-728">Vi 삽입 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-728">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="0c8b7-729">Vi 명령 모드: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-729">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="0c8b7-730">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="0c8b7-730">RepeatLastCharSearch</span></span>

<span data-ttu-id="0c8b7-731">마지막으로 기록 된 문자 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-731">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="0c8b7-732">Vi 명령 모드: `<;>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-732">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="0c8b7-733">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="0c8b7-733">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="0c8b7-734">마지막으로 기록 된 문자 검색을 반대 방향으로 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-734">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="0c8b7-735">Vi 명령 모드: `<,>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-735">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="0c8b7-736">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="0c8b7-736">RepeatSearch</span></span>

<span data-ttu-id="0c8b7-737">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-737">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="0c8b7-738">Vi 명령 모드: `<n>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-738">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="0c8b7-739">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-739">RepeatSearchBackward</span></span>

<span data-ttu-id="0c8b7-740">이전과 동일한 방향으로 마지막 검색을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-740">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="0c8b7-741">Vi 명령 모드: `<N>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-741">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="0c8b7-742">SearchChar</span><span class="sxs-lookup"><span data-stu-id="0c8b7-742">SearchChar</span></span>

<span data-ttu-id="0c8b7-743">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-743">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="0c8b7-744">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-744">This is for 't' functionality.</span></span>

- <span data-ttu-id="0c8b7-745">Vi 명령 모드: `<f>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-745">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="0c8b7-746">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-746">SearchCharBackward</span></span>

<span data-ttu-id="0c8b7-747">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-747">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="0c8b7-748">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-748">This is for 'T' functionality.</span></span>

- <span data-ttu-id="0c8b7-749">Vi 명령 모드: `<F>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-749">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="0c8b7-750">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="0c8b7-750">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="0c8b7-751">다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="0c8b7-752">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="0c8b7-753">Vi 명령 모드: `<T>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-753">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="0c8b7-754">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="0c8b7-754">SearchCharWithBackoff</span></span>

<span data-ttu-id="0c8b7-755">다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-755">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="0c8b7-756">' T '의 기능에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-756">This is for 't' functionality.</span></span>

- <span data-ttu-id="0c8b7-757">Vi 명령 모드: `<t>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-757">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="0c8b7-758">SearchForward</span><span class="sxs-lookup"><span data-stu-id="0c8b7-758">SearchForward</span></span>

<span data-ttu-id="0c8b7-759">검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-759">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="0c8b7-760">Vi 삽입 모드: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-760">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="0c8b7-761">Vi 명령 모드: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="0c8b7-761">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="0c8b7-762">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="0c8b7-762">Custom Key Bindings</span></span>

<span data-ttu-id="0c8b7-763">PSReadLine은 cmdlet을 사용 하 여 사용자 지정 키 바인딩을 지원 `Set-PSReadLineKeyHandler` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-763">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="0c8b7-764">대부분의 사용자 지정 키 바인딩은 위의 함수 중 하나를 호출 합니다. 예를 들면</span><span class="sxs-lookup"><span data-stu-id="0c8b7-764">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="0c8b7-765">ScriptBlock을 키에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-765">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="0c8b7-766">ScriptBlock은 필요한 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-766">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="0c8b7-767">몇 가지 유용한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-767">Some useful examples include</span></span>

- <span data-ttu-id="0c8b7-768">명령줄 편집</span><span class="sxs-lookup"><span data-stu-id="0c8b7-768">edit the command line</span></span>
- <span data-ttu-id="0c8b7-769">새 창 열기 (예: 도움말)</span><span class="sxs-lookup"><span data-stu-id="0c8b7-769">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="0c8b7-770">명령줄을 변경 하지 않고 디렉터리를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-770">change directories without changing the command line</span></span>

<span data-ttu-id="0c8b7-771">ScriptBlock은 두 개의 인수를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-771">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="0c8b7-772">`$key` -사용자 지정 바인딩을 트리거한 키 인 **[ConsoleKeyInfo]** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-772">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="0c8b7-773">동일한 ScriptBlock을 여러 키에 바인딩하고 키에 따라 다른 작업을 수행 해야 하는 경우 $key를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-773">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="0c8b7-774">많은 사용자 지정 바인딩에서이 인수를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-774">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="0c8b7-775">`$arg` -임의의 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-775">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="0c8b7-776">가장 자주 사용 되는 정수 인수는 사용자가 키 바인딩 DigitArgument에서 전달 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-776">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="0c8b7-777">바인딩에서 인수를 허용 하지 않는 경우에는이 인수를 무시 하는 것이 합리적입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-777">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="0c8b7-778">실행 하지 않고 기록에 명령줄을 추가 하는 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-778">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="0c8b7-779">이는 작업을 수행 하지 못했지만 이미 입력 한 명령줄을 다시 입력 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-779">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="0c8b7-780">PSReadLine 모듈 폴더에 설치 된 파일에서 더 많은 예제를 볼 수 있습니다 `SamplePSReadLineProfile.ps1` .</span><span class="sxs-lookup"><span data-stu-id="0c8b7-780">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="0c8b7-781">대부분의 키 바인딩은 일부 도우미 함수를 사용 하 여 명령줄을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-781">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="0c8b7-782">이러한 Api는 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-782">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="0c8b7-783">사용자 지정 키 바인딩 지원 Api</span><span class="sxs-lookup"><span data-stu-id="0c8b7-783">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="0c8b7-784">다음 함수는 PSConsoleReadLine에서 공용 이지만 키에 직접 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-784">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="0c8b7-785">대부분은 사용자 지정 키 바인딩에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-785">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="0c8b7-786">실행 하지 않고 기록에 명령줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-786">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="0c8b7-787">Kill 링을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-787">Clear the kill-ring.</span></span>  <span data-ttu-id="0c8b7-788">이는 주로 테스트에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-788">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="0c8b7-789">시작에서 길이 문자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-789">Delete length characters from start.</span></span>  <span data-ttu-id="0c8b7-790">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-790">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="0c8b7-791">사용자 기본 설정에 따라 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-791">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="0c8b7-792">이러한 두 함수는 입력 버퍼의 현재 상태에 대 한 유용한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-792">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="0c8b7-793">첫 번째는 간단한 경우에 보다 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-793">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="0c8b7-794">두 번째는 바인딩에서 Ast를 사용 하 여 더 높은 작업을 수행 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-794">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="0c8b7-795">이 함수는 Get-PSReadLineKeyHandler에서 사용 되며 사용자 지정 키 바인딩에서 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-795">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="0c8b7-796">이 함수는 Get-PSReadLineOption에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-796">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="0c8b7-797">명령줄에 선택 항목이 없으면-1이 시작 및 길이 둘 다에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-797">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="0c8b7-798">명령줄에 선택 항목이 있는 경우 선택의 시작 및 길이가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-798">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="0c8b7-799">커서에 문자 또는 문자열을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-799">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="0c8b7-800">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-800">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="0c8b7-801">PSReadLine에 대 한 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-801">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="0c8b7-802">재귀를 지원 하지 않으므로 사용자 지정 키 바인딩에는 유용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-802">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="0c8b7-803">이 함수는 Remove-PSReadLineKeyHandler에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-803">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="0c8b7-804">일부 입력을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-804">Replace some of the input.</span></span> <span data-ttu-id="0c8b7-805">이 작업은 실행 취소/다시 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-805">This operation supports undo/redo.</span></span> <span data-ttu-id="0c8b7-806">이는 실행 취소의 단일 작업으로 처리 되기 때문에 Delete 뒤에 Insert를 통해 선호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-806">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="0c8b7-807">커서를 지정 된 오프셋으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-807">Move the cursor to the given offset.</span></span> <span data-ttu-id="0c8b7-808">실행 취소를 위해 커서 이동이 추적 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-808">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="0c8b7-809">이 함수는 cmdlet Set-PSReadLineOption에서 사용 되는 도우미 메서드로, 설정을 일시적으로 변경 하려는 사용자 지정 키 바인딩에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-809">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="0c8b7-810">이 도우미 메서드는 DigitArgument을 준수 하는 사용자 지정 바인딩에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-810">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="0c8b7-811">일반적인 호출은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-811">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="0c8b7-812">참고</span><span class="sxs-lookup"><span data-stu-id="0c8b7-812">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="0c8b7-813">POWERSHELL 호환성</span><span class="sxs-lookup"><span data-stu-id="0c8b7-813">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="0c8b7-814">PSReadLine에는 PowerShell 3.0 이상 및 콘솔 호스트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-814">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="0c8b7-815">PowerShell ISE에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-815">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="0c8b7-816">Visual Studio Code 콘솔에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-816">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="0c8b7-817">명령 기록</span><span class="sxs-lookup"><span data-stu-id="0c8b7-817">COMMAND HISTORY</span></span>

<span data-ttu-id="0c8b7-818">PSReadLine은 명령줄에서 입력 한 모든 명령 및 데이터를 포함 하는 기록 파일을 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-818">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="0c8b7-819">여기에는 암호를 비롯 한 중요 한 데이터가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-819">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="0c8b7-820">예를 들어 cmdlet을 사용 하는 경우 `ConvertTo-SecureString` 암호는 일반 텍스트로 기록 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-820">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="0c8b7-821">기록 파일은 라는 파일입니다 `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="0c8b7-821">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="0c8b7-822">Windows 시스템에서 기록 파일은에 저장 됩니다 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="0c8b7-822">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="0c8b7-823">PSReadLine에 영향을 주는 & 피드백</span><span class="sxs-lookup"><span data-stu-id="0c8b7-823">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="0c8b7-824">GitHub의 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="0c8b7-824">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="0c8b7-825">GitHub 페이지에서 끌어오기 요청을 제출 하거나 피드백을 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-825">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c8b7-826">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c8b7-826">SEE ALSO</span></span>

<span data-ttu-id="0c8b7-827">PSReadLine은 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 라이브러리의 영향을 많이 받습니다.</span><span class="sxs-lookup"><span data-stu-id="0c8b7-827">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
