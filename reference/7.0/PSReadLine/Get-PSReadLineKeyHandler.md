---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlinekeyhandler?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineKeyHandler
ms.openlocfilehash: 4b29a95bc6c18f3126ff7929135b87742d06bafe
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93225090"
---
# <span data-ttu-id="85a67-103">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="85a67-103">Get-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="85a67-104">개요</span><span class="sxs-lookup"><span data-stu-id="85a67-104">SYNOPSIS</span></span>
<span data-ttu-id="85a67-105">PSReadLine 모듈에 대 한 키 바인딩을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="85a67-105">Gets the key bindings for the PSReadLine module.</span></span>

## <span data-ttu-id="85a67-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="85a67-106">SYNTAX</span></span>

```
Get-PSReadLineKeyHandler [-Bound] [-Unbound] [<CommonParameters>]
```

## <span data-ttu-id="85a67-107">설명</span><span class="sxs-lookup"><span data-stu-id="85a67-107">DESCRIPTION</span></span>

<span data-ttu-id="85a67-108">**Get PSReadLineKeyHandler** cmdlet은 현재 바인딩된 키 바인딩을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a67-108">The **Get-PSReadLineKeyHandler** cmdlet returns the currently bound key bindings.</span></span>

## <span data-ttu-id="85a67-109">예제</span><span class="sxs-lookup"><span data-stu-id="85a67-109">EXAMPLES</span></span>

### <span data-ttu-id="85a67-110">예제 1: 모든 키 매핑 가져오기</span><span class="sxs-lookup"><span data-stu-id="85a67-110">Example 1: Get all key mappings</span></span>

<span data-ttu-id="85a67-111">이 명령은 모든 키 매핑, 바인딩 및 바인딩 해제를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a67-111">This command returns all key mappings, bound and unbound.</span></span>

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

### <span data-ttu-id="85a67-112">예제 2: 바인딩된 키 가져오기</span><span class="sxs-lookup"><span data-stu-id="85a67-112">Example 2: Get bound keys</span></span>

<span data-ttu-id="85a67-113">이 명령은 바인딩된 키와 키 조합만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a67-113">This command returns only bound keys and key combinations.</span></span>

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

## <span data-ttu-id="85a67-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="85a67-114">PARAMETERS</span></span>

### <span data-ttu-id="85a67-115">-바인딩</span><span class="sxs-lookup"><span data-stu-id="85a67-115">-Bound</span></span>

<span data-ttu-id="85a67-116">이 cmdlet이 바인딩된 함수를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85a67-116">Indicates that this cmdlet returns functions that are bound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85a67-117">-바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="85a67-117">-Unbound</span></span>

<span data-ttu-id="85a67-118">이 cmdlet은 바인딩되지 않은 함수를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85a67-118">Indicates that this cmdlet returns functions that are unbound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85a67-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="85a67-119">CommonParameters</span></span>

<span data-ttu-id="85a67-120">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="85a67-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="85a67-121">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85a67-121">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="85a67-122">입력</span><span class="sxs-lookup"><span data-stu-id="85a67-122">INPUTS</span></span>

### <span data-ttu-id="85a67-123">없음</span><span class="sxs-lookup"><span data-stu-id="85a67-123">None</span></span>

<span data-ttu-id="85a67-124">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85a67-124">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="85a67-125">출력</span><span class="sxs-lookup"><span data-stu-id="85a67-125">OUTPUTS</span></span>

### <span data-ttu-id="85a67-126">Microsoft. PowerShell. KeyHandler</span><span class="sxs-lookup"><span data-stu-id="85a67-126">Microsoft.PowerShell.KeyHandler</span></span>

## <span data-ttu-id="85a67-127">참고</span><span class="sxs-lookup"><span data-stu-id="85a67-127">NOTES</span></span>

## <span data-ttu-id="85a67-128">관련 링크</span><span class="sxs-lookup"><span data-stu-id="85a67-128">RELATED LINKS</span></span>

[<span data-ttu-id="85a67-129">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="85a67-129">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="85a67-130">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="85a67-130">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="85a67-131">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="85a67-131">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="85a67-132">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="85a67-132">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
