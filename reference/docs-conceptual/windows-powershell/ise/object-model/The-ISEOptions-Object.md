---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEOptions 개체
ms.openlocfilehash: 9caa78a70cb837c755b2eff9af6ce0aa5dbb7452
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808629"
---
# <a name="the-iseoptions-object"></a>ISEOptions 개체

**ISEOptions** 개체는 Windows PowerShell ISE에 대한 다양한 설정을 나타냅니다. **Microsoft.PowerShell.Host.ISE.ISEOptions** 클래스의 인스턴스입니다.

**ISEOptions** 개체는 다음 메서드 및 속성을 제공합니다.

## <a name="methods"></a>메서드

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

콘솔 창에서 토큰 색의 기본값을 복원합니다.

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

콘솔 창에 있는 모든 옵션 설정의 기본값을 복원합니다. 또한 메시지가 다시 표시되지 않도록 하기 위해 표준 확인란을 제공하는 다양한 경고 메시지의 동작을 다시 설정합니다.

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

스크립트 창에서 토큰 색의 기본값을 복원합니다.

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

Windows PowerShell ISE에 표시되는 XML 요소에 대한 토큰 색의 기본값을 복원합니다. [XmlTokenColors](#xmltokencolors)도 참조하세요.

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>속성

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

Windows PowerShell ISE의 파일 자동 저장 작업 간격(분 단위 수)을 지정합니다. 기본값은 2분입니다. 이 값은 정수입니다.

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다. 이후 버전에 대해서는 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)를 참조하세요.

명령 창에 대한 배경색을 지정합니다. **System.Windows.Media.Color** 클래스의 인스턴스입니다.

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.

명령 창이 출력 창 위에 있는지 여부를 지정합니다.

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

콘솔 창에 대한 배경색을 지정합니다. **System.Windows.Media.Color** 클래스의 인스턴스입니다.

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

콘솔 창에 있는 텍스트의 전경색을 지정합니다.

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

콘솔 창에 있는 텍스트의 배경색을 지정합니다.

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

Windows PowerShell ISE 콘솔 창에서 IntelliSense 토큰의 색을 지정합니다. 이 속성은 토큰 형식과 콘솔 창에 대한 색의 이름/값 쌍을 포함하는 사전 개체입니다. 스크립트 창에서 IntelliSense 토큰의 색을 변경하려면 [TokenColors](#tokencolors)를 참조합니다.
색을 기본값으로 다시 설정하려면 [RestoreDefaultConsoleTokenColors()](#restoredefaultconsoletokencolors)를 참조합니다.
다음에 대한 토큰 색상을 설정할 수 있습니다. Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

콘솔 창에 표시되는 디버그 텍스트의 배경색을 지정합니다. **System.Windows.Media.Color** 클래스의 인스턴스입니다.

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

콘솔 창에 표시되는 디버그 텍스트의 전경색을 지정합니다. **System.Windows.Media.Color** 클래스의 인스턴스입니다.

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

Reset 메서드를 사용할 때 사용할 기본값을 지정하는 속성의 컬렉션입니다.

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions
```

```Output
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

### <a name="errorbackgroundcolor"></a>ErrorBackgroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

콘솔 창에 나타나는 오류 텍스트에 대한 배경색을 지정합니다. **System.Windows.Media.Color** 클래스의 인스턴스입니다.

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

콘솔 창에 나타나는 오류 텍스트의 전경색을 지정합니다. **System.Windows.Media.Color** 클래스의 인스턴스입니다.

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

현재 스크립트 창과 콘솔 창 모두에서 사용 중인 글꼴 이름을 지정합니다.

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

글꼴 크기를 정수로 지정합니다. 스크립트 창, 명령 창 및 출력 창에서 사용합니다. 값의 유효한 범위는 8-32입니다.

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

IntelliSense에서 현재 입력한 텍스트를 확인하는 데 사용하는 시간(초)의 수를 지정합니다.
이 시간(초)이 지나면 IntelliSense에서는 제한 시간이 끝나서 계속 입력할 수 있습니다. 기본값은 3초입니다. 이 값은 정수입니다.

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

Windows PowerShell ISE에서 추적하는 최근에 열린 파일의 수를 지정하고 **파일 열기** 메뉴의 맨 아래에 표시됩니다. 기본값은 10입니다. 이 값은 정수입니다.

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다. 이후 버전에 대해서는 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)를 참조하세요.

출력 창 자체에 대한 배경색을 가져오거나 설정하는 읽기/쓰기 속성입니다. **System.Windows.Media.Color** 클래스의 인스턴스입니다.

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다. 이후 버전에 대해서는 [ConsolePaneForegroundColor](#consolepaneforegroundcolor)를 참조하세요.

Windows PowerShell ISE 2.0의 출력 창에 있는 텍스트의 전경색을 변경하는 읽기/쓰기 속성입니다.

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다. 이후 버전에 대해서는 [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor)를 참조하세요.

출력 창에 있는 텍스트의 배경색을 변경하는 읽기/쓰기 속성입니다.

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

파일에 대한 배경색을 가져오거나 설정하는 읽기/쓰기 속성입니다. **System.Windows.Media.Color** 클래스의 인스턴스입니다.

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

스크립트 창에서 스크립트가 아닌 파일에 대한 전경색을 가져오거나 설정하는 읽기/쓰기 속성입니다.
스크립트 파일에 대한 전경색을 설정하려면 [TokenColors](#tokencolors)를 사용합니다.

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

디스플레이에서의 스크립트 창 위치를 가져오거나 설정하는 읽기/쓰기 속성입니다. 이 문자열은 ‘최대화’, ‘맨 위’ 또는 ‘오른쪽’일 수 있습니다.

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

코드 조각의 <kbd>Ctrl</kbd>+<kbd>J</kbd> 목록에 Windows PowerShell에 포함된 시작 세트가 포함되는지 여부를 지정합니다. `$false`로 설정하면 사용자가 정의한 코드 조각만 <kbd>Ctrl</kbd>+<kbd>J</kbd> 목록에 표시됩니다.
기본값은 `$true`입니다.

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

IntelliSense가 콘솔 창에서 구문, 매개 변수 및 값 제안을 제공하는지 여부를 지정합니다.
기본값은 `$true`입니다.

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

IntelliSense가 스크립트 창에서 구문, 매개 변수 및 값 제안을 제공하는지 여부를 지정합니다.
기본값은 `$true`입니다.

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

스크립트 창의 왼쪽 여백에 줄 번호가 표시되는지 여부를 지정합니다. 기본값은 `$true`입니다.

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

스크립트 창에서 왼쪽 여백에 있는 코드 섹션 옆에 확장 및 축소가 가능한 대괄호가 표시되는지 여부를 지정합니다. 표시된다면 텍스트 블록의 옆에 있는 빼기(`-`) 아이콘을 클릭하여 텍스트 블록을 축소하거나 더하기(`+`) 아이콘을 클릭하여 텍스트 블록을 확장할 수 있습니다. 기본값은 `$true`입니다.

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

Windows PowerShell ISE 창의 맨 위에 ISE 도구 모음이 표시되는지 여부를 지정합니다. 기본값은 `$true`입니다.

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

스크립트를 실행하기 전에 자동으로 저장할 때 경고 메시지가 표시되는지 여부를 지정합니다.
기본값은 `$true`입니다.

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

다른 PowerShell 탭에 동일한 파일이 열리면 경고 메시지가 표시되는지 여부를 지정합니다. `$true`로 설정된 경우, 여러 탭에서 같은 파일을 열려고 하면 "이 파일의 복사본이 다른 Windows PowerShell 탭에서 열려 있습니다. 이 파일의 변경 내용은 열려 있는 모든 복사본에 적용됩니다."라는 메시지가 표시됩니다. 기본값은 `$true`입니다.

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

Windows PowerShell ISE 스크립트 창에서 IntelliSense 토큰의 색을 지정합니다. 이 속성은 토큰 형식과 스크립트 창에 대한 색의 이름/값 쌍을 포함하는 사전 개체입니다. 콘솔 창에서 IntelliSense 토큰의 색을 변경하려면 [ConsoleTokenColors](#consoletokencolors)를 참조합니다.
색을 기본값으로 다시 설정하려면 [RestoreDefaultTokenColors](#restoredefaulttokencolors)를 참조합니다.
다음에 대한 토큰 색상을 설정할 수 있습니다. Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

콘솔 창에서 IntelliSense 제공 옵션을 선택하기 위해 Enter 키를 사용할 수 있는지 여부를 지정합니다. 기본값은 `$true`입니다.

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

스크립트 창에서 IntelliSense 제공 옵션을 선택하기 위해 Enter 키를 사용할 수 있는지 여부를 지정합니다. 기본값은 `$true`입니다.

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

커서가 키워드 있는 상태에서 <kbd>F1</kbd> 키를 누를 때 로컬로 설치된 도움말이나 온라인 TechNet 라이브러리 도움말이 나타나는지 여부를 지정합니다. `$true`로 설정된 경우, 팝업 창에 로컬로 설치된 도움말 콘텐츠가 표시됩니다. `Update-Help` 명령을 실행하여 도움말 파일을 설치할 수 있습니다. `$false`로 설정된 경우, 브라우저로 TechNet 라이브러리에 있는 페이지가 열립니다.

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

콘솔 창에 나타나는 자세한 정보 텍스트에 대한 배경색을 지정합니다. **System.Windows.Media.Color** 개체입니다.

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

콘솔 창에 나타나는 자세한 정보 텍스트에 대한 전경색을 지정합니다. **System.Windows.Media.Color** 개체입니다.

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

콘솔 창에 나타나는 경고 텍스트에 대한 배경색을 지정합니다. **System.Windows.Media.Color** 개체입니다.

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

출력 창에 나타나는 경고 텍스트의 전경색을 지정합니다. **System.Windows.Media.Color** 개체입니다.

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

Windows PowerShell ISE에 표시되는 토큰 형식과 XML 콘텐츠에 대한 색의 이름/값 쌍을 포함하는 사전 개체를 지정합니다. 다음에 대한 토큰 색상을 설정할 수 있습니다. Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable. [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors)도 참조하세요.

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Zoom

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

콘솔 창과 스크립트 창 모두에서 텍스트의 상대 크기를 지정합니다. 기본값은 100입니다.
값이 작을수록 Windows PowerShell ISE의 텍스트가 작게 표시되고, 큰 숫자일수록 텍스트가 더 크게 표시됩니다. 값은 20에서 400 사이의 정수입니다.

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>참고 항목

- [Windows PowerShell ISE 스크립팅 개체 모델의 용도](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)
