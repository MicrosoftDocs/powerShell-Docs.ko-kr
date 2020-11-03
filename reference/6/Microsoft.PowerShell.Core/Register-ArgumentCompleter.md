---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: af36f19b2ad399bccaa462c0e0e65f70da276705
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217186"
---
# Register-ArgumentCompleter

## 개요

Completer 사용자 지정 인수를 등록 합니다.

## SYNTAX

### NativeSet

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### PowerShellSet

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## 설명

`Register-ArgumentCompleter`Cmdlet은 사용자 지정 인수 completer을 등록 합니다. 인수 completer를 사용 하면 런타임에 사용자가 지정 하는 명령에 대해 동적 탭 완성 기능을 제공할 수 있습니다.

## 예제

### 예제 1: 사용자 지정 인수 completer 등록

다음 예에서는 cmdlet의 **Id** 매개 변수에 completer 인수를 등록 합니다 `Set-TimeZone` .

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

첫 번째 명령은 사용자가 <kbd>Tab</kbd>키를 누를 때 전달 되는 필수 매개 변수를 사용 하는 스크립트 블록을 만듭니다. 자세한 내용은 **ScriptBlock** 매개 변수 설명을 참조 하세요.

스크립트 블록 내에서 **Id** 에 사용할 수 있는 값은 cmdlet을 사용 하 여 검색 됩니다 `Get-TimeZone` . 각 표준 시간대에 대 한 **Id** 속성은 cmdlet으로 파이프 됩니다 `Where-Object` . `Where-Object`Cmdlet은에서 제공 하는 값으로 시작 하지 않는 모든 id를 필터링 합니다 .이 값은 `$wordToComplete` 사용자가 <kbd>Tab</kbd>키를 눌러 입력 한 텍스트를 나타냅니다. 필터링 된 id는 `For-EachObject` 값에 공백이 포함 되어 있는 경우 각 값을 따옴표로 묶는 cmdlet으로 파이프 됩니다.

두 번째 명령은 scriptblock, **ParameterName** **Id** 및 **CommandName** 을 전달 하 여 completer 인수를 등록 합니다 `Set-TimeZone` .

### 예제 2: 탭 완성 값에 세부 정보 추가

다음 예에서는 cmdlet의 **Name** 매개 변수에 대 한 탭 완성을 덮어쓰고 `Stop-Service` 실행 중인 서비스만 반환 합니다.

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

첫 번째 명령은 사용자가 <kbd>Tab</kbd>키를 누를 때 전달 되는 필수 매개 변수를 사용 하는 스크립트 블록을 만듭니다. 자세한 내용은 **ScriptBlock** 매개 변수 설명을 참조 하세요.

스크립트 블록 내에서 첫 번째 명령은 cmdlet을 사용 하 여 실행 중인 모든 서비스를 검색 합니다 `Where-Object` . 서비스는 cmdlet으로 파이프 됩니다 `ForEach-Object` . `ForEach-Object`Cmdlet은 새 [system.object](/dotnet/api/system.management.automation.completionresult) 를 만들고이 개체를 현재 서비스의 이름으로 채웁니다 (파이프라인 변수로 나타냄 `$_.Name` ).

가 중 **결과** 개체를 사용 하 여 반환 된 각 값에 추가 세부 정보를 제공할 수 있습니다.

- **완성도 텍스트** (String)-자동 완성 결과로 사용할 텍스트입니다. 이 값은 명령으로 전송 됩니다.
- **listitemtext** (String)-사용자가 <kbd>Ctrl</kbd>Space를 누르는 경우와 같이 목록에 표시 되는 텍스트 + <kbd>Space</kbd>입니다. 이는 표시 용 으로만 사용 되며 선택한 경우 명령에 전달 되지 않습니다.
- **resultType** ( [완성도 resultType](/dotnet/api/system.management.automation.completionresulttype))-완료 결과의 유형입니다.
- **tooltip** (String)-개체에 대 한 세부 정보가 표시 되는 도구 설명 텍스트입니다.
  이는 <kbd>Ctrl</kbd>Space를 누른 후 사용자가 항목을 선택할 때 표시 됩니다 + <kbd>Space</kbd>.

마지막 명령은 중지 된 서비스를 계속 cmdlet에 수동으로 전달할 수 있음을 보여 줍니다 `Stop-Service` . 탭 완성은 영향을 받는 유일한 측면입니다.

### 예제 3: 사용자 지정 네이티브 인수 등록 completer

**네이티브 매개 변수** 를 사용 하 여 네이티브 명령에 대 한 탭 완성 기능을 제공할 수 있습니다. 다음 예제에서는 `dotnet` CLI (명령줄 인터페이스)에 대 한 탭 완성 기능을 추가 합니다.

> [!NOTE]
> `dotnet complete`이 명령은 dotnet cli 버전 2.0 이상 에서만 사용할 수 있습니다.

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

첫 번째 명령은 사용자가 <kbd>Tab</kbd>키를 누를 때 전달 되는 필수 매개 변수를 사용 하는 스크립트 블록을 만듭니다. 자세한 내용은 **ScriptBlock** 매개 변수 설명을 참조 하세요.

스크립트 블록 내에서 `dotnet complete` 명령은 탭 완성을 수행 하는 데 사용 됩니다.
결과는 cmdlet으로 파이프 됩니다. `ForEach-Object` 이 cmdlet은 각 값에 대해 새로운 [메이 션](/dotnet/api/system.management.automation.completionresult) 개체를 만들기 위해 **새** 정적 메서드를 사용 하 여 **CompletionResult** 합니다.

## PARAMETERS

### -CommandName

명령의 이름을 배열로 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -네이티브

Completer 인수가 PowerShell에서 매개 변수 이름을 완료할 수 없는 네이티브 명령에 대 한 것임을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParameterName

인수를 완료할 매개 변수의 이름을 지정 합니다. 지정 된 매개 변수 이름은 cmdlet의 **ForegroundColor** 매개 변수와 같은 열거 값일 수 없습니다 `Write-Host` .

열거형에 대 한 자세한 내용은 [about_Enum](./About/about_Enum.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

탭 완성을 수행 하기 위해 실행할 명령을 지정 합니다. 사용자가 제공 하는 스크립트 블록은 입력을 완료 하는 값을 반환 해야 합니다. 스크립트 블록은 파이프라인 ( `ForEach-Object` , 등 `Where-Object` ) 또는 다른 적합 한 메서드를 사용 하 여 값을 언 롤 해야 합니다. 값의 배열을 반환 하면 PowerShell에서 전체 배열을 **하나의** 탭 완성 값으로 처리 합니다.

스크립트 블록은 아래 지정 된 순서 대로 다음 매개 변수를 허용 해야 합니다. PowerShell이 위치에 따라 값을 전달 하므로 매개 변수 이름은 중요 하지 않습니다.

- `$commandName` (위치 0)-이 매개 변수는 스크립트 블록에서 탭 완성 기능을 제공 하는 명령 이름으로 설정 됩니다.
- `$parameterName` (위치 1)-이 매개 변수는 값이 탭 완성이 필요한 매개 변수로 설정 됩니다.
- `$wordToComplete` (위치 2)-이 매개 변수는 <kbd>Tab</kbd>키를 누를 때 사용자가 제공한 값으로 설정 됩니다. 스크립트 블록은이 값을 사용 하 여 탭 완성 값을 결정 해야 합니다.
- `$commandAst` (위치 3)-이 매개 변수는 현재 입력 줄에 대 한 AST (추상 구문 트리)로 설정 됩니다. 자세한 내용은 [Ast 클래스](/dotnet/api/system.management.automation.language.ast)를 참조 하세요.
- `$fakeBoundParameters` (위치 4)-이 매개 변수는 `$PSBoundParameters` 사용자가 <kbd>Tab</kbd>키를 눌러 cmdlet에 대 한를 포함 하는 해시 테이블로 설정 됩니다. 자세한 내용은 [about_Automatic_Variables](./About/about_Automatic_Variables.md)를 참조 하세요.

**네이티브** 매개 변수를 지정 하는 경우 스크립트 블록은 지정 된 순서로 다음 매개 변수를 사용 해야 합니다. PowerShell이 위치에 따라 값을 전달 하므로 매개 변수 이름은 중요 하지 않습니다.

- `$wordToComplete` (위치 0)-이 매개 변수는 <kbd>Tab</kbd>키를 누르기 전에 사용자가 제공한 값으로 설정 됩니다. 스크립트 블록은이 값을 사용 하 여 탭 완성 값을 결정 해야 합니다.
- `$commandAst` (위치 1)-이 매개 변수는 현재 입력 줄에 대 한 AST (추상 구문 트리)로 설정 됩니다. 자세한 내용은 [Ast 클래스](/dotnet/api/system.management.automation.language.ast)를 참조 하세요.
- `$cursorPosition` (위치 2)-이 매개 변수는 사용자가 <kbd>Tab</kbd>키를 누를 때 커서의 위치로 설정 됩니다.

**ArgumentCompleter** 를 매개 변수 특성으로 제공할 수도 있습니다. 자세한 내용은 [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](./About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### 없음

이 cmdlet은 출력을 반환하지 않습니다.

## 참고

## 관련 링크
