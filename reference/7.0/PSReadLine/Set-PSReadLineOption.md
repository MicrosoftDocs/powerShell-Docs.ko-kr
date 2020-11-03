---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: ce5941787120988a3352153497c9a6df06ee9d89
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93225049"
---
# Set-PSReadLineOption

## 개요
**Psreadline** 에서 명령줄 편집의 동작을 사용자 지정 합니다.

## 구문

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [<CommonParameters>]
```

## Description

`Set-PSReadLineOption`Cmdlet은 명령줄을 편집 하는 동안 **psreadline** 모듈의 동작을 사용자 지정 합니다. **Psreadline** 설정을 보려면를 사용 `Get-PSReadLineOption` 합니다.

## 예

### 예제 1: 전경색 및 배경색 설정

이 예제에서는 **Psreadline** 을 설정 하 여 녹색 전경 텍스트가 있는 **주석** 토큰을 회색 배경에 표시 합니다. 예제에서 사용 된 이스케이프 시퀀스에서 **32** 은 전경색을 나타내고 **47** 은 배경색을 나타냅니다.

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

전경 텍스트 색만 설정 하도록 선택할 수 있습니다. 예를 들어 **주석** 토큰의 밝은 녹색 전경 텍스트 색은입니다. ``"Comment"="`e[92m"``

### 예제 2: 벨 스타일 설정

이 예제에서 **Psreadline** 은 사용자 주의가 필요한 오류나 조건에 응답 합니다.
**BellStyle** 는 60 밀리초 동안 1221 Hz에서 가청 경고음을 내보내도록 설정 되어 있습니다.

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> 이 기능은 플랫폼의 모든 호스트에서 작동 하지 않을 수 있습니다.

### 예제 3: 여러 옵션 설정

`Set-PSReadLineOption` 해시 테이블을 사용 하 여 여러 옵션을 설정할 수 있습니다.

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

`$PSReadLineOptions`해시 테이블은 키와 값을 설정 합니다. `Set-PSReadLineOption` 에서 키와 값을 사용 하 여 `@PSReadLineOptions` **psreadline** 옵션을 업데이트 합니다.

PowerShell 명령줄에서 해시 테이블 이름을 입력 하는 키와 값을 볼 수 있습니다 `$PSReadLineOptions` .

### 예제 4: 여러 색 옵션 설정

이 예제에서는 단일 명령에서 두 개 이상의 색 값을 설정 하는 방법을 보여 줍니다.

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### 예 5: 여러 형식에 대 한 색 값 설정

이 예제에서는 **Psreadline** 에 표시 되는 토큰의 색을 설정 하는 방법에 대 한 세 가지 방법을 보여 줍니다.

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### 예제 6: ViModeChangeHandler를 사용 하 여 Vi 모드 변경 내용 표시

이 예제에서는 **Vi** 모드 변경에 대 한 응답으로 커서 변경 VT 이스케이프를 내보냅니다.

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

**OnViModeChange** 함수는 **Vi** 모드: insert 및 command에 대 한 커서 옵션을 설정 합니다.
**ViModeChangeHandler** 는 공급자를 사용 하 여 `Function:` **OnViModeChange** 를 스크립트 블록 개체로 참조 합니다.

자세한 내용은 [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)를 참조하세요.

## 매개 변수

### -AddToHistoryHandler

**Psreadline** 기록에 추가 되는 명령을 제어 하는 **ScriptBlock** 을 지정 합니다.

**ScriptBlock** 은 명령줄을 입력으로 받습니다. **ScriptBlock** 이를 반환 하는 경우 `$True` 명령줄이 기록에 추가 됩니다.

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AnsiEscapeTimeout

이 옵션은 또는에서 실행 되는 경우와 같이 입력이 리디렉션되는 경우에만 Windows에 해당 `tmux` `screen` 합니다.

Windows에서 리디렉션된 입력을 사용 하면 많은 키가 이스케이프 문자에서 시작 하는 문자 시퀀스로 전송 됩니다. 단일 이스케이프 문자 다음에 더 많은 문자와 유효한 이스케이프 시퀀스를 구분 하는 것은 불가능 합니다.

터미널에서 사용자 유형 보다 더 빠르게 문자를 보낼 수 있다고 가정 합니다. **Psreadline** 은 전체 이스케이프 시퀀스를 수신 하기 전에이 시간 제한 동안 대기 합니다.

입력할 때 무작위 또는 예기치 않은 문자가 표시 되는 경우이 시간 제한을 조정할 수 있습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -BellStyle

**Psreadline** 이 다양 한 오류 및 모호한 조건에 응답 하는 방법을 지정 합니다.

유효한 값은 다음과 같습니다.

- **가청** : 짧은 경고음.
- **시각적 개체** : 텍스트가 잠시 깜박입니다.
- **없음** : 피드백이 없습니다.

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### -색

**Colors** 매개 변수는 **psreadline** 에서 사용 되는 다양 한 색을 지정 합니다.

인수는 키에서 색을 지정 하는 요소와 값을 지정 하는 해시 테이블입니다.
자세한 내용은 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)를 참조 하세요.

색은 **ConsoleColor** 의 값 (예: `[ConsoleColor]::Red` 또는 유효한 ANSI 이스케이프 시퀀스) 중 하나일 수 있습니다. 유효한 이스케이프 시퀀스는 터미널에 따라 다릅니다. PowerShell 5.0에서 빨강 텍스트에 대 한 예제 이스케이프 시퀀스는 `$([char]0x1b)[91m` 입니다. PowerShell 6 이상에서 같은 이스케이프 시퀀스는 `` `e[91m`` 입니다. 다음 형식을 포함 하 여 다른 이스케이프 시퀀스를 지정할 수 있습니다.

- 256 색
- 24 비트 색
- 전경, 배경 또는 둘 다
- 반전, 굵게

ANSI 색 코드에 대 한 자세한 내용은 위키백과의 [ansi 이스케이프 코드](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) 를 참조 하세요.

유효한 키는 다음과 같습니다.

- **ContinuationPrompt** : 연속 프롬프트의 색입니다.
- **강조** : 강조 색입니다. 예를 들어 기록을 검색할 때 일치 하는 텍스트가 있습니다.
- **오류** : 오류 색입니다. 예를 들어 프롬프트에서을 입력 합니다.
- **Selection** : 메뉴 선택 영역이 나 선택 된 텍스트를 강조 표시 하는 색입니다.
- **기본값** : 기본 토큰 색입니다.
- **Comment** : 주석 토큰 색입니다.
- **키워드** : 키워드 토큰 색입니다.
- **문자열** : 문자열 토큰 색입니다.
- **Operator** : 연산자 토큰 색입니다.
- **Variable** : 변수 토큰 색입니다.
- **Command** : 명령 토큰 색입니다.
- **매개 변수** : 매개 변수 토큰 색입니다.
- **형식** : 형식 토큰 색입니다.
- **Number** : 숫자 토큰 색입니다.
- **Member** : 구성원 이름 토큰 색입니다.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandValidationHandler

**Validateandacceptline** 에서 호출 되는 **ScriptBlock** 을 지정 합니다. 예외가 throw 되 면 유효성 검사가 실패 하 고 오류가 보고 됩니다.

예외를 throw 하기 전에 유효성 검사 처리기는 오류 발생 지점에 커서를 놓고 쉽게 수정할 수 있습니다. 유효성 검사 처리기는 일반적인 철자 오류를 수정 하기 위해와 같은 명령줄을 변경할 수도 있습니다.

**Validateandacceptline** 은 작업을 수행할 수 없는 명령을 사용 하 여 기록의 복잡 한 문제를 방지 하는 데 사용 됩니다.

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -전체 Queryitems

메시지를 표시 하지 않고 표시 되는 최대 완료 항목 수를 지정 합니다.

표시할 항목 수가이 값 보다 크면 **Psreadline** 은 완료 항목을 표시 하기 전에 **예/아니요** 를 표시 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContinuationPrompt

여러 줄 입력을 입력할 때 다음 줄의 시작 부분에 표시 되는 문자열을 지정 합니다. 기본값은 이중 보다 큼 기호 ( `>>` )입니다. 빈 문자열이 유효 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingDuration

**BellStyle** 가 **가청** 으로 설정 된 경우 경고음의 기간을 지정 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingTone

**BellStyle** 가 **가청** 으로 설정 된 경우 경고음의 톤 (hz)을 지정 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### -EditMode

명령줄 편집 모드를 지정 합니다. 이 매개 변수를 사용 하면에 의해 설정 된 모든 키 바인딩이 다시 설정 `Set-PSReadLineKeyHandler` 됩니다.

유효한 값은 다음과 같습니다.

- **Windows** : 키 바인딩은 PowerShell, Cmd 및 Visual Studio를 에뮬레이트합니다.
- **Emacs** : 키 바인딩은 Bash 또는 Emacs을 에뮬레이트합니다.
- **Vi** : 키 바인딩은 Vi를 에뮬레이트합니다.

`Get-PSReadLineKeyHandler`현재 구성 된 **EditMode** 의 키 바인딩을 보려면를 사용 합니다.

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExtraPromptLineCount

추가 줄의 수를 지정 합니다.

프롬프트가 두 줄 이상으로 확장 되는 경우이 매개 변수의 값을 지정 합니다. **Psreadline** 에서 일부 출력을 표시 한 후에 프롬프트가 표시 될 때 추가 줄을 사용 하려면이 옵션을 사용 합니다. 예를 들어 **Psreadline** 은 완료 목록을 반환 합니다.

이 옵션은 이전 버전의 **Psreadline** 에서 보다 더 필요 하지만 함수를 사용 하는 경우에 유용 `InvokePrompt` 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistoryNoDuplicates

이 옵션은 회수 동작을 제어 합니다. 중복 된 명령은 여전히 기록 파일에 추가 됩니다.
이 옵션을 설정 하면 명령을 회수할 때 가장 최근의 호출만 표시 됩니다. 회수 하는 동안 순서를 유지 하기 위해 기록에 반복 명령이 추가 됩니다. 그러나 기록을 회수 하거나 검색할 때 일반적으로 명령을 여러 번 표시 하지 않으려고 합니다.

기본적으로 global **PSConsoleReadLineOptions** 개체의 **HistoryNoDuplicates** 속성은로 설정 됩니다 `True` . 이 **Switchparameter** 를 사용 하면 속성 값이로 설정 `True` 됩니다. 속성 값을 변경 하려면 다음과 같이 **Switchparameter** 값을 지정 해야 합니다 `-HistoryNoDuplicates:$False` .

다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySavePath

기록이 저장 되는 파일의 경로를 지정 합니다. Windows 또는 Windows 이외의 플랫폼을 실행 하는 컴퓨터는 다른 위치에 파일을 저장 합니다. 파일 이름은 변수에 저장 됩니다 `$($host.Name)_history.txt` (예:) `ConsoleHost_history.txt` .

이 매개 변수를 사용 하지 않는 경우 기본 경로는 다음과 같습니다.

**Windows**

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

**비 Windows**

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySaveStyle

**Psreadline** 에서 기록을 저장 하는 방법을 지정 합니다.

유효한 값은 다음과 같습니다.

- **Saveincrementally** : 각 명령이 실행 된 후 기록을 저장 하 고 PowerShell의 여러 인스턴스 간에 공유 합니다.
- **SaveAtExit** : PowerShell이 종료 될 때 기록 파일을 추가 합니다.
- **SaveNothing** : 기록 파일을 사용 하지 않습니다.

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCaseSensitive

**ReverseSearchHistory** 또는 **HistorySearchBackward** 와 같은 함수에서 기록 검색에서 대/소문자를 구분 하도록 지정 합니다.

기본적으로 global **PSConsoleReadLineOptions** 개체의 **HistorySearchCaseSensitive** 속성은로 설정 됩니다 `False` . 이 **Switchparameter** 를 사용 하면 속성 값이로 설정 `True` 됩니다. 속성 값을 다시 변경 하려면 **Switchparameter** 의 값을 다음과 같이 지정 해야 합니다 `-HistorySearchCaseSensitive:$False` .

다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCursorMovesToEnd

검색을 사용 하 여 기록에서 로드 하는 명령의 끝으로 커서를 이동 함을 나타냅니다.
이 매개 변수를로 설정 하면 `$False` 위로 또는 아래로 화살표를 누를 때 커서가 있던 위치에 커서가 표시 됩니다.

기본적으로 global **PSConsoleReadLineOptions** 개체의 **HistorySearchCursorMovesToEnd** 속성은로 설정 됩니다 `False` . 이 **Switchparameter** 를 사용 하 여 속성 값을로 설정 `True` 합니다. 속성 값을 다시 변경 하려면 **Switchparameter** 의 값을 다음과 같이 지정 해야 합니다 `-HistorySearchCursorMovesToEnd:$False` .

다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumHistoryCount

**Psreadline** 기록에 저장할 최대 명령 수를 지정 합니다.

**Psreadline** 기록은 PowerShell 기록과 별개입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumKillRingCount

Kill 링에 저장 된 최대 항목 수를 지정 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -PromptText

구문 분석 오류가 발생 하는 경우 **Psreadline** 은 프롬프트의 일부를 빨간색으로 변경 합니다. **Psreadline** 은 프롬프트 함수를 분석 하 여 프롬프트 부분의 색만 변경 하는 방법을 결정 합니다. 이 분석은 100% 안정적이 아닙니다.

**Psreadline** 에서 예기치 않은 방법으로 프롬프트를 변경 하는 경우이 옵션을 사용 합니다. 후행 공백을 포함 합니다.

예를 들어, 프롬프트 함수는 다음 예제와 같이 표시 됩니다.

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

그런 다음 다음을 설정 합니다.

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowToolTips

가능한 완료를 표시 하면 도구 설명이 완성 목록에 표시 됩니다.

기본적으로 이 옵션은 사용하도록 설정됩니다. 이 옵션은 이전 버전의 **Psreadline** 에서 기본적으로 사용 하도록 설정 되지 않았습니다. 사용 하지 않도록 설정 하려면이 옵션을로 설정 `$False` 합니다.

기본적으로 전역 **PSConsoleReadLineOptions** 개체의 **showtooltips** 속성은로 설정 됩니다 `True` . 이 **Switchparameter** 를 사용 하면 속성 값이로 설정 `True` 됩니다. 속성 값을 변경 하려면 다음과 같이 **Switchparameter** 값을 지정 해야 합니다 `-ShowToolTips:$False` .

다음 명령을 사용 하 여 속성 값을 직접 설정할 수 있습니다.

`(Get-PSReadLineOption).ShowToolTips = $False`

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

### -ViModeChangeHandler

**Vimodeindicator** 로 설정 된 경우 `Script` 모드가 변경 될 때마다 제공 된 스크립트 블록이 호출 됩니다. 스크립트 블록은 형식의 인수 하나를 제공 합니다 `ViMode` .

이 매개 변수는 PowerShell 7에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeIndicator

이 옵션은 현재 **Vi** 모드의 시각적 표시를 설정 합니다. 삽입 모드 또는 명령 모드 중 하나입니다.

유효한 값은 다음과 같습니다.

- **없음** : 표시 되지 않습니다.
- **Prompt** : 프롬프트에서 색을 변경 합니다.
- **Cursor** : 커서 크기가 변경 됩니다.
- **스크립트** : 사용자 지정 텍스트가 인쇄 됩니다.

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WordDelimiters 기호

**Forwardword** 또는 **KillWord** 같은 함수의 단어를 구분 하는 문자를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"–—―
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

개체를 파이프로 사용할 수 없습니다. `Set-PSReadLineOption.`

## outputs

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 메모

## 관련 링크

[about_PSReadLine](./About/about_PSReadLine.md)

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
