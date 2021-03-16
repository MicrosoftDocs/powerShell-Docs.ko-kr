---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineKeyHandler
ms.openlocfilehash: bb1e92a8f4bca96dc369b5b799c7e89245e432be
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600430"
---
# <span data-ttu-id="505de-102">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="505de-102">Get-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="505de-103">개요</span><span class="sxs-lookup"><span data-stu-id="505de-103">SYNOPSIS</span></span>
<span data-ttu-id="505de-104">PSReadLine 모듈에 대 한 바인딩된 키 함수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="505de-104">Gets the bound key functions for the PSReadLine module.</span></span>

## <span data-ttu-id="505de-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="505de-105">SYNTAX</span></span>

### <span data-ttu-id="505de-106">FullListing (기본값)</span><span class="sxs-lookup"><span data-stu-id="505de-106">FullListing (default)</span></span>

```
Get-PSReadLineKeyHandler [-Bound] [-Unbound] [<CommonParameters>]
```

### <span data-ttu-id="505de-107">SpecificBindings</span><span class="sxs-lookup"><span data-stu-id="505de-107">SpecificBindings</span></span>

```
Get-PSReadLineKeyHandler [-Chord] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="505de-108">설명</span><span class="sxs-lookup"><span data-stu-id="505de-108">DESCRIPTION</span></span>

<span data-ttu-id="505de-109">매개 변수를 지정 하지 않으면 PSReadLine 모듈에 대 한 현재 바인딩된 키 함수를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-109">If no parameter is specified, returns the currently bound key functions for the PSReadLine module.</span></span>

<span data-ttu-id="505de-110">**현** 매개 변수가 지정 된 경우 cmdlet은 특정 바인딩된 키를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-110">If **Chord** parameter is specified, the cmdlet returns the specific bound keys.</span></span>

## <span data-ttu-id="505de-111">예제</span><span class="sxs-lookup"><span data-stu-id="505de-111">EXAMPLES</span></span>

### <span data-ttu-id="505de-112">예제 1: 모든 키 매핑 가져오기</span><span class="sxs-lookup"><span data-stu-id="505de-112">Example 1: Get all key mappings</span></span>

<span data-ttu-id="505de-113">이 명령은 모든 키 매핑, 바인딩 및 바인딩 해제를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-113">This command returns all key mappings, bound and unbound.</span></span>

```powershell
Get-PSReadLineKeyHandler -Bound -Unbound
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
Shift+Tab             TabCompletePrevious     Complete the input using the previous completion
Ctrl+a                SelectAll               Select the entire line. Moves the cursor to the end of the line
Ctrl+c                CopyOrCancelLine        Either copy selected text to the clipboard, or if no text is selected, cancel editing the line with Cancel...
Ctrl+C                Copy                    Copy selected region to the system clipboard.  If no region is selected, copy the whole line
Ctrl+l                ClearScreen             Clear the screen and redraw the current line at the top of the screen
Ctrl+r                ReverseSearchHistory    Search history backwards interactively
...
```

### <span data-ttu-id="505de-114">예제 2: 바인딩된 키 가져오기</span><span class="sxs-lookup"><span data-stu-id="505de-114">Example 2: Get bound keys</span></span>

<span data-ttu-id="505de-115">이 명령은 바인딩된 키와 키 조합만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-115">This command returns only bound keys and key combinations.</span></span>

```powershell
Get-PSReadLineKeyHandler
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
...
```

### <span data-ttu-id="505de-116">예 3: 특정 키 바인딩 가져오기</span><span class="sxs-lookup"><span data-stu-id="505de-116">Example 3: Get specific key bindings</span></span>

<span data-ttu-id="505de-117">이 명령은 지정 된 키에 대 한 바인딩만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-117">This command returns only the bindings for the specified keys.</span></span>

```powershell
Get-PSReadLineKeyHandler -Chord Enter, Shift+Enter
```

```Output
Key         Function   Description
---         --------   -----------
Enter       AcceptLine Accept the input or move to the next line if input is missing a closing token.
Shift+Enter AddLine    Move the cursor to the next line without attempting to execute the input
...
```

## <span data-ttu-id="505de-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="505de-118">PARAMETERS</span></span>

### <span data-ttu-id="505de-119">-바인딩</span><span class="sxs-lookup"><span data-stu-id="505de-119">-Bound</span></span>

<span data-ttu-id="505de-120">이 cmdlet이 바인딩된 함수를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="505de-120">Indicates that this cmdlet returns functions that are bound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="505de-121">-바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="505de-121">-Unbound</span></span>

<span data-ttu-id="505de-122">이 cmdlet은 바인딩되지 않은 함수를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="505de-122">Indicates that this cmdlet returns functions that are unbound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="505de-123">-현</span><span class="sxs-lookup"><span data-stu-id="505de-123">-Chord</span></span>

<span data-ttu-id="505de-124">특정 키 또는 시퀀스에 바인딩된 함수만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-124">Return only functions bound to specific keys or sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SpecificBindings
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="505de-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="505de-125">CommonParameters</span></span>

<span data-ttu-id="505de-126">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="505de-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="505de-127">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="505de-127">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="505de-128">입력</span><span class="sxs-lookup"><span data-stu-id="505de-128">INPUTS</span></span>

### <span data-ttu-id="505de-129">없음</span><span class="sxs-lookup"><span data-stu-id="505de-129">None</span></span>

<span data-ttu-id="505de-130">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="505de-130">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="505de-131">출력</span><span class="sxs-lookup"><span data-stu-id="505de-131">OUTPUTS</span></span>

### <span data-ttu-id="505de-132">Microsoft. PowerShell. KeyHandler</span><span class="sxs-lookup"><span data-stu-id="505de-132">Microsoft.PowerShell.KeyHandler</span></span>

## <span data-ttu-id="505de-133">참고</span><span class="sxs-lookup"><span data-stu-id="505de-133">NOTES</span></span>

## <span data-ttu-id="505de-134">관련 링크</span><span class="sxs-lookup"><span data-stu-id="505de-134">RELATED LINKS</span></span>

[<span data-ttu-id="505de-135">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="505de-135">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="505de-136">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="505de-136">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="505de-137">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="505de-137">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="505de-138">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="505de-138">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
