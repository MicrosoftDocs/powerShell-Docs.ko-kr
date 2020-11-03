---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 025e208fa5996a646cb066a703d51002b1b6d5ad
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224226"
---
# Write-Debug

## 개요
콘솔에 디버그 메시지를 씁니다.

## SYNTAX

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## 설명

`Write-Debug`Cmdlet은 스크립트 또는 명령에서 호스트에 디버그 메시지를 씁니다.

기본적으로 디버그 메시지는 콘솔에 표시 되지 않지만 **debug** 매개 변수 또는 변수를 사용 하 여 표시할 수 있습니다 `$DebugPreference` .

## 예제

### 예 1: $DebugPreference 이해

이 예제에서는 디버그 메시지를 작성 합니다.

```powershell
Write-Debug "Cannot open file."
```

의 기본값은 `$DebugPreference` **SilentlyContinue** 입니다. 따라서 메시지는 콘솔에 표시 되지 않습니다.

### 예제 2: 값 변경 $DebugPreference

이 예에서는 변수 값을 변경 하는 경우의 결과를 보여 줍니다 `$DebugPreference` . 먼저의 현재 값을 표시 하 `$DebugPreference` 고 디버그 메시지를 쓰려고 시도 합니다. 그런 다음 값을 `$DebugPreference` **Continue** 로 변경 하 여 디버그 메시지를 표시할 수 있도록 합니다.

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

에 대 한 자세한 내용은 `$DebugPreference` [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables)를 참조 하세요.

### 예제 3: Debug 매개 변수를 사용 하 여 $DebugPreference 재정의

`Test-Debug`함수는 변수 값을 `$DebugPreference` PowerShell 호스트 및 디버그 스트림에 씁니다. 이 예제에서는 **Debug** 매개 변수를 사용 하 여 값을 재정의 `$DebugPreference` 합니다.

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

Debug 매개 변수를 사용 하는 경우의 값이 변경 된 것을 확인할 `$DebugPreference` 수 있습니다. **Debug** 이 변경은 함수의 범위에만 영향을 줍니다. 값은 함수 외부에 영향을 받지 않습니다.

**Debug** 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조 하세요.

## PARAMETERS

### -메시지

콘솔에 보낼 디버그 메시지를 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

디버그 메시지를 포함 하는 문자열을로 파이프 할 수 있습니다 `Write-Debug` .

## 출력

### 없음

`Write-Debug` 는 디버그 스트림에만 씁니다. 파이프라인에 개체를 쓰지 않습니다.

## 참고

## 관련 링크

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[쓰기 오류](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
