---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEEditor 개체
ms.openlocfilehash: cb63acebc1a8bb9fa6cc07199088ae0d5441bc91
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736192"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="67244-103">ISEEditor 개체</span><span class="sxs-lookup"><span data-stu-id="67244-103">The ISEEditor Object</span></span>

<span data-ttu-id="67244-104">**ISEEditor** 개체는 Microsoft.PowerShell.Host.ISE.ISEEditor 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="67244-105">콘솔 창은 **ISEEditor** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="67244-106">각 [ISEFile](The-ISEFile-Object.md) 개체에는 연결된 **ISEEditor** 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67244-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="67244-107">다음 섹션에는 **ISEEditor** 개체의 메서드 및 속성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="67244-108">메서드</span><span class="sxs-lookup"><span data-stu-id="67244-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="67244-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="67244-109">Clear\(\)</span></span>

<span data-ttu-id="67244-110">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-111">편집기에서 텍스트를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="67244-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="67244-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="67244-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="67244-113">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-114">지정된 **lineNumber** 매개 변수 값에 해당하는 줄이 표시되도록 편집기를 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="67244-115">지정된 줄 번호가 유효한 줄 번호를 정의하는 마지막 줄 번호인 1의 범위 밖에 있는 경우 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="67244-116">**lineNumber** 표시할 줄의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="67244-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="67244-117">Focus\(\)</span></span>

<span data-ttu-id="67244-118">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-119">포커스를 편집기로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="67244-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="67244-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="67244-121">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-122">줄 번호로 지정된 줄에 대한 정수 줄 길이를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="67244-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="67244-123">**lineNumber** 길이를 가져올 줄의 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="67244-124">**Returns** 지정된 줄 번호의 줄에 대한 줄 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="67244-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="67244-125">GoToMatch\(\)</span></span>

<span data-ttu-id="67244-126">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67244-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="67244-127">편집기 개체의 **CanGoToMatch** 속성이 `$true`인 경우, 캐럿을 일치하는 문자로 이동합니다. 캐럿이 여는 괄호, 대괄호 또는 중괄호 `(`,`[`,`{` 바로 앞에 있거나 닫는 괄호, 대괄호 또는 중괄호 `)`,`]`,`}` 바로 뒤에 있을 때 이런 일이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is `$true`, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - `(`,`[`,`{` - or immediately after a closing parenthesis, bracket, or brace - `)`,`]`,`}`.</span></span> <span data-ttu-id="67244-128">캐럿은 여는 문자가 앞이나 닫는 문자 뒤에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="67244-129">**CanGoToMatch** 속성이 `$false`이면, 이 메서드는 아무 작업도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67244-129">If the **CanGoToMatch** property is `$false`, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="67244-130">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="67244-130">InsertText\( text \)</span></span>

<span data-ttu-id="67244-131">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-132">선택 영역을 텍스트로 바꾸거나, 현재 캐럿 위치에 텍스트를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="67244-133">**text** - String 삽입할 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="67244-134">이 항목의 뒷부분에 나오는 [스크립팅 예제](#scripting-example)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67244-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="67244-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="67244-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="67244-136">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-137">**startLine**, **startColumn**, **endLine** 및 **endColumn** 매개 변수에서 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="67244-138">**startLine** - Integer 선택이 시작되는 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="67244-139">**startColumn** - Integer 선택이 시작되는 시작 줄 내의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="67244-140">**endLine** - Integer 선택이 끝나는 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="67244-141">**endColumn** - Integer 선택이 끝나는 끝 줄 내의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="67244-142">이 항목의 뒷부분에 나오는 [스크립팅 예제](#scripting-example)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67244-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="67244-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="67244-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="67244-144">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-145">현재 캐럿을 포함하는 텍스트의 전체 줄을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="67244-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="67244-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="67244-147">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-148">줄 번호 및 열 번호로 캐럿 위치를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="67244-149">캐럿 줄 번호 또는 캐럿 열 번호가 각각의 유효한 범위를 벗어나는 경우 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-149">It throws an exception if either the caret line number or the caret column number are out of their respective valid ranges.</span></span>

<span data-ttu-id="67244-150">**lineNumber** - Integer 캐럿 줄 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="67244-151">**columnNumber** - Integer 캐럿 열 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="67244-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="67244-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="67244-153">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67244-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="67244-154">모든 개요 섹션을 확장하거나 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="67244-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="67244-155">속성</span><span class="sxs-lookup"><span data-stu-id="67244-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="67244-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="67244-156">CanGoToMatch</span></span>

<span data-ttu-id="67244-157">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67244-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="67244-158">캐럿이 괄호, 대괄호 또는 중괄호(`()`,`[]`,`{}`) 옆에 있는지 여부를 나타내는 읽기 전용 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - `()`, `[]`, `{}`.</span></span> <span data-ttu-id="67244-159">캐럿이 여는 문자의 바로 앞 또는 닫는 문자 바로 뒤에 있다면 이 속성 값은 `$true`입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is `$true`.</span></span> <span data-ttu-id="67244-160">그렇지 않으면 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-160">Otherwise, it is `$false`.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="67244-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="67244-161">CaretColumn</span></span>

<span data-ttu-id="67244-162">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-163">캐럿의 위치에 해당하는 열 번호를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="67244-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="67244-164">CaretLine</span></span>

<span data-ttu-id="67244-165">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-166">캐럿을 포함하는 줄 번호를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="67244-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="67244-167">CaretLineText</span></span>

<span data-ttu-id="67244-168">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-169">캐럿을 포함하는 텍스트의 전체 줄을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="67244-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="67244-170">LineCount</span></span>

<span data-ttu-id="67244-171">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-172">편집기에서 줄 수를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="67244-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="67244-173">SelectedText</span></span>

<span data-ttu-id="67244-174">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-175">편집기에서 선택한 텍스트를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="67244-176">이 항목의 뒷부분에 나오는 [스크립팅 예제](#scripting-example)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67244-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="67244-177">텍스트</span><span class="sxs-lookup"><span data-stu-id="67244-177">Text</span></span>

<span data-ttu-id="67244-178">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67244-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="67244-179">편집기에 있는 텍스트를 설정하거나 가져오는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="67244-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="67244-180">이 항목의 뒷부분에 나오는 [스크립팅 예제](#scripting-example)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67244-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="67244-181">스크립팅 예제</span><span class="sxs-lookup"><span data-stu-id="67244-181">Scripting Example</span></span>

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="67244-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67244-182">See Also</span></span>

- [<span data-ttu-id="67244-183">ISEFile 개체</span><span class="sxs-lookup"><span data-stu-id="67244-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="67244-184">PowerShellTab 개체</span><span class="sxs-lookup"><span data-stu-id="67244-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="67244-185">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="67244-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="67244-186">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="67244-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
