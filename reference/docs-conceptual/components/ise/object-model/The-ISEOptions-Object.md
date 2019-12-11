---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEOptions 개체
ms.openlocfilehash: e9dcb13c14212ec4aec40a7f163e2ed56ceea6f9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028917"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="35963-103">ISEOptions 개체</span><span class="sxs-lookup"><span data-stu-id="35963-103">The ISEOptions Object</span></span>

<span data-ttu-id="35963-104">**ISEOptions** 개체는 Windows PowerShell ISE에 대한 다양한 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="35963-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="35963-105">**Microsoft.PowerShell.Host.ISE.ISEOptions** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="35963-106">**ISEOptions** 개체는 다음 메서드 및 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="35963-107">메서드</span><span class="sxs-lookup"><span data-stu-id="35963-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="35963-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="35963-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="35963-109">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-110">콘솔 창에서 토큰 색의 기본값을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="35963-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="35963-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="35963-112">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-113">콘솔 창에 있는 모든 옵션 설정의 기본값을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="35963-114">또한 메시지가 다시 표시되지 않도록 하기 위해 표준 확인란을 제공하는 다양한 경고 메시지의 동작을 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="35963-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="35963-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="35963-116">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-117">스크립트 창에서 토큰 색의 기본값을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="35963-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="35963-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="35963-119">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-120">Windows PowerShell ISE에 표시되는 XML 요소에 대한 토큰 색의 기본값을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="35963-121">[XmlTokenColors](#xmltokencolors)도 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35963-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="35963-122">속성</span><span class="sxs-lookup"><span data-stu-id="35963-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="35963-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="35963-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="35963-124">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-125">Windows PowerShell ISE의 파일 자동 저장 작업 간격(분 단위 수)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="35963-126">기본값은 2분입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-126">The default value is 2 minutes.</span></span> <span data-ttu-id="35963-127">이 값은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="35963-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="35963-129">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="35963-130">이후 버전에 대해서는 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35963-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="35963-131">명령 창에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="35963-132">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="35963-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="35963-133">CommandPaneUp</span></span>

<span data-ttu-id="35963-134">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="35963-135">명령 창이 출력 창 위에 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="35963-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="35963-137">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-138">콘솔 창에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="35963-139">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="35963-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="35963-141">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-142">콘솔 창에 있는 텍스트의 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="35963-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="35963-144">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-145">콘솔 창에 있는 텍스트의 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="35963-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="35963-146">ConsoleTokenColors</span></span>

<span data-ttu-id="35963-147">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-148">Windows PowerShell ISE 콘솔 창에서 IntelliSense 토큰의 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="35963-149">이 속성은 토큰 형식과 콘솔 창에 대한 색의 이름/값 쌍을 포함하는 사전 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="35963-150">스크립트 창에서 IntelliSense 토큰의 색을 변경하려면 [TokenColors](#tokencolors)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="35963-151">색을 기본값으로 다시 설정하려면 [RestoreDefaultConsoleTokenColors()](#restoredefaultconsoletokencolors)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="35963-152">다음에 대한 토큰 색상을 설정할 수 있습니다. Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="35963-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="35963-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-153">DebugBackgroundColor</span></span>

<span data-ttu-id="35963-154">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-155">콘솔 창에 표시되는 디버그 텍스트의 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="35963-156">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="35963-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-157">DebugForegroundColor</span></span>

<span data-ttu-id="35963-158">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-159">콘솔 창에 표시되는 디버그 텍스트의 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="35963-160">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="35963-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="35963-161">DefaultOptions</span></span>

<span data-ttu-id="35963-162">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-163">Reset 메서드를 사용할 때 사용할 기본값을 지정하는 속성의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a><span data-ttu-id="35963-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="35963-165">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-166">콘솔 창에 나타나는 오류 텍스트에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="35963-167">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="35963-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-168">ErrorForegroundColor</span></span>

<span data-ttu-id="35963-169">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-170">콘솔 창에 나타나는 오류 텍스트의 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="35963-171">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="35963-172">FontName</span><span class="sxs-lookup"><span data-stu-id="35963-172">FontName</span></span>

<span data-ttu-id="35963-173">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-174">현재 스크립트 창과 콘솔 창 모두에서 사용 중인 글꼴 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="35963-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="35963-175">FontSize</span></span>

<span data-ttu-id="35963-176">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-177">글꼴 크기를 정수로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="35963-178">스크립트 창, 명령 창 및 출력 창에서 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="35963-179">값의 유효한 범위는 8-32입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="35963-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="35963-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="35963-181">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-182">IntelliSense에서 현재 입력한 텍스트를 확인하는 데 사용하는 시간(초)의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="35963-183">이 시간(초)이 지나면 IntelliSense에서는 제한 시간이 끝나서 계속 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="35963-184">기본값은 3초입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-184">The default value is 3 seconds.</span></span> <span data-ttu-id="35963-185">이 값은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="35963-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="35963-186">MruCount</span></span>

<span data-ttu-id="35963-187">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-188">Windows PowerShell ISE에서 추적하는 최근에 열린 파일의 수를 지정하고 **파일 열기** 메뉴의 맨 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="35963-189">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-189">The default value is 10.</span></span> <span data-ttu-id="35963-190">이 값은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="35963-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="35963-192">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="35963-193">이후 버전에 대해서는 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35963-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="35963-194">출력 창 자체에 대한 배경색을 가져오거나 설정하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="35963-195">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="35963-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="35963-197">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="35963-198">이후 버전에 대해서는 [ConsolePaneForegroundColor](#consolepaneforegroundcolor)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35963-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="35963-199">Windows PowerShell ISE 2.0의 출력 창에 있는 텍스트의 전경색을 변경하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="35963-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="35963-201">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="35963-202">이후 버전에 대해서는 [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35963-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="35963-203">출력 창에 있는 텍스트의 배경색을 변경하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="35963-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="35963-205">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-206">파일에 대한 배경색을 가져오거나 설정하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="35963-207">**System.Windows.Media.Color** 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="35963-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="35963-209">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-210">스크립트 창에서 스크립트가 아닌 파일에 대한 전경색을 가져오거나 설정하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="35963-211">스크립트 파일에 대한 전경색을 설정하려면 [TokenColors](#tokencolors)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="35963-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="35963-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="35963-213">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-214">디스플레이에서의 스크립트 창 위치를 가져오거나 설정하는 읽기/쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="35963-215">이 문자열은 ‘최대화’, ‘맨 위’ 또는 ‘오른쪽’일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="35963-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="35963-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="35963-217">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-218">코드 조각의 **CTRL+J** 목록에 Windows PowerShell에 포함된 시작 세트가 포함되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="35963-219">**$false**로 설정하면 사용자가 정의한 코드 조각만 **CTRL+J** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="35963-220">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-220">The default value is **$true**.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="35963-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="35963-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="35963-222">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-223">IntelliSense가 콘솔 창에서 구문, 매개 변수 및 값 제안을 제공하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="35963-224">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-224">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="35963-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="35963-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="35963-226">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-227">IntelliSense가 스크립트 창에서 구문, 매개 변수 및 값 제안을 제공하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="35963-228">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-228">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="35963-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="35963-229">ShowLineNumbers</span></span>

<span data-ttu-id="35963-230">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-231">스크립트 창의 왼쪽 여백에 줄 번호가 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="35963-232">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-232">The default value is **$true**.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="35963-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="35963-233">ShowOutlining</span></span>

<span data-ttu-id="35963-234">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-235">스크립트 창에서 왼쪽 여백에 있는 코드 섹션 옆에 확장 및 축소가 가능한 대괄호가 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="35963-236">표시된다면 텍스트 블록의 옆에 있는 빼기(\(-\)) 아이콘을 클릭하여 텍스트 블록을 축소하거나 더하기(\(+\)) 아이콘을 클릭하여 텍스트 블록을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="35963-237">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-237">The default value is **$true**.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="35963-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="35963-238">ShowToolBar</span></span>

<span data-ttu-id="35963-239">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-240">Windows PowerShell ISE 창의 맨 위에 ISE 도구 모음이 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="35963-241">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-241">The default value is **$true**.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="35963-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="35963-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="35963-243">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-244">스크립트를 실행하기 전에 자동으로 저장할 때 경고 메시지가 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="35963-245">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-245">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="35963-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="35963-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="35963-247">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-248">다른 PowerShell 탭에 동일한 파일이 열리면 경고 메시지가 표시되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="35963-249">**$true**로 설정된 경우, 여러 탭에서 같은 파일을 열려고 하면 "이 파일의 복사본이 다른 Windows PowerShell 탭에서 열려 있습니다. 이 파일의 변경 내용은 열려 있는 모든 복사본에 적용됩니다."라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="35963-250">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-250">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="35963-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="35963-251">TokenColors</span></span>

<span data-ttu-id="35963-252">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-253">Windows PowerShell ISE 스크립트 창에서 IntelliSense 토큰의 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="35963-254">이 속성은 토큰 형식과 스크립트 창에 대한 색의 이름/값 쌍을 포함하는 사전 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="35963-255">콘솔 창에서 IntelliSense 토큰의 색을 변경하려면 [ConsoleTokenColors](#consoletokencolors)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="35963-256">색을 기본값으로 다시 설정하려면 [RestoreDefaultTokenColors](#restoredefaulttokencolors)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="35963-257">다음에 대한 토큰 색상을 설정할 수 있습니다. Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="35963-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="35963-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="35963-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="35963-259">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-260">콘솔 창에서 IntelliSense 제공 옵션을 선택하기 위해 Enter 키를 사용할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="35963-261">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-261">The default value is **$true**.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="35963-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="35963-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="35963-263">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-264">스크립트 창에서 IntelliSense 제공 옵션을 선택하기 위해 Enter 키를 사용할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="35963-265">기본값은 **$true**입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-265">The default value is **$true**.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="35963-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="35963-266">UseLocalHelp</span></span>

<span data-ttu-id="35963-267">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-268">커서가 키워드 있는 상태에서 F1 키를 누를 때 로컬로 설치된 도움말이나 온라인 TechNet 라이브러리 도움말이 나타나는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="35963-269">**$true**로 설정된 경우, 팝업 창에 로컬로 설치된 도움말 콘텐츠가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="35963-270">`Update-Help` 명령을 실행하여 도움말 파일을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="35963-271">**$false**로 설정된 경우, 브라우저로 TechNet 라이브러리에 있는 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="35963-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="35963-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="35963-273">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-274">콘솔 창에 나타나는 자세한 정보 텍스트에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="35963-275">**System.Windows.Media.Color** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="35963-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-276">VerboseForegroundColor</span></span>

<span data-ttu-id="35963-277">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-278">콘솔 창에 나타나는 자세한 정보 텍스트에 대한 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="35963-279">**System.Windows.Media.Color** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="35963-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-280">WarningBackgroundColor</span></span>

<span data-ttu-id="35963-281">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-282">콘솔 창에 나타나는 경고 텍스트에 대한 배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="35963-283">**System.Windows.Media.Color** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="35963-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="35963-284">WarningForegroundColor</span></span>

<span data-ttu-id="35963-285">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="35963-286">출력 창에 나타나는 경고 텍스트의 전경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="35963-287">**System.Windows.Media.Color** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="35963-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="35963-288">XmlTokenColors</span></span>

<span data-ttu-id="35963-289">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-290">Windows PowerShell ISE에 표시되는 토큰 형식과 XML 콘텐츠에 대한 색의 이름/값 쌍을 포함하는 사전 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="35963-291">다음에 대한 토큰 색상을 설정할 수 있습니다. Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="35963-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="35963-292">[RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors)도 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35963-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="35963-293">확대/축소</span><span class="sxs-lookup"><span data-stu-id="35963-293">Zoom</span></span>

<span data-ttu-id="35963-294">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35963-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="35963-295">콘솔 창과 스크립트 창 모두에서 텍스트의 상대 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35963-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="35963-296">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-296">The default value is 100.</span></span> <span data-ttu-id="35963-297">값이 작을수록 Windows PowerShell ISE의 텍스트가 작게 표시되고, 큰 숫자일수록 텍스트가 더 크게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35963-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="35963-298">값은 20에서 400 사이의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="35963-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="35963-299">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35963-299">See Also</span></span>

- [<span data-ttu-id="35963-300">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="35963-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="35963-301">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="35963-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
