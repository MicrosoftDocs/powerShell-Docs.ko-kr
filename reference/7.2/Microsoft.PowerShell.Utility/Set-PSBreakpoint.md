---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 5e2bdf435bf7cb9da3f31712c346beff29a11baf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603307"
---
# Set-PSBreakpoint

## 개요
줄, 명령 또는 변수에 중단점을 설정합니다.

## SYNTAX

### 줄 (기본값)

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### 명령

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### 변수

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## 설명

`Set-PSBreakpoint`Cmdlet은 현재 세션에서 실행 되는 명령 또는 스크립트에 중단점을 설정 합니다. 를 사용 하 여 스크립트를 실행 `Set-PSBreakpoint` 하거나 명령을 실행 하기 전에 또는 다른 중단점에서 중지 된 경우 디버깅 중에 중단점을 설정할 수 있습니다.

`Set-PSBreakpoint` 원격 컴퓨터에 중단점을 설정할 수 없습니다. 원격 컴퓨터에서 스크립트를 디버그하려면 스크립트를 로컬 컴퓨터로 복사한 다음 로컬로 디버그하세요.

각 `Set-PSBreakpoint` 명령은 다음 세 가지 중단점 유형 중 하나를 만듭니다.

- 줄 중단점-특정 줄과 열 좌표에 중단점을 설정 합니다.
- 명령 중단점-명령 및 함수에 대 한 중단점을 설정 합니다.
- 변수 중단점-변수에 중단점을 설정 합니다.

단일 명령으로 여러 줄, 명령 또는 변수에 중단점을 설정할 수 `Set-PSBreakpoint` 있지만 각 `Set-PSBreakpoint` 명령은 하나의 중단점 유형만 설정 합니다.

중단점에서 PowerShell은 일시적으로 실행을 중지 하 고 디버거에 제어를 제공 합니다. 명령 프롬프트가로 변경 `DBG\>` 되 고 디버거 명령 집합을 사용할 수 있게 됩니다. 그러나 **Action** 매개 변수를 사용 하 여 로깅 또는 진단과 같은 추가 작업을 수행 하는 중단점 또는 명령 조건과 같은 대체 응답을 지정할 수 있습니다.

`Set-PSBreakpoint`Cmdlet은 PowerShell 스크립트 디버깅을 위해 설계 된 여러 cmdlet 중 하나입니다.
PowerShell 디버거에 대 한 자세한 내용은 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)를 참조 하세요.

## 예제

### 예제 1: 줄에 중단점 설정

이 예에서는 Sample.ps1 스크립트의 줄 5에 중단점을 설정 합니다. 스크립트가 실행 되 면 줄 5가 실행 되기 직전에 실행이 중지 됩니다.

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

줄 번호로 새 중단점을 설정 하는 경우 cmdlet은 `Set-PSBreakpoint` 중단점 ID 및 적중 횟수를 포함 하는 줄 중단점 개체 (**system.web**)를 생성 합니다.

### 예제 2: 함수에 중단점 설정

이 예에서는 `Increment` Sample.ps1 cmdlet의 함수에 명령 중단점을 만듭니다. 매번 지정된 함수를 호출하기 직전에 스크립트의 실행이 중지됩니다.

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

그 결과로, 명령 중단점 개체가 생성됩니다. 스크립트를 실행 하기 전에 **HitCount** 속성의 값은 0입니다.

### 예제 3: 변수에 중단점 설정

이 예에서는 Sample.ps1 스크립트의 **서버** 변수에 중단점을 설정 합니다. **ReadWrite** 값과 함께 **Mode** 매개 변수를 사용 하 여 변수 값을 읽을 때 실행을 중지 하 고 값이 변경 되기 직전에 실행을 중지 합니다.

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### 예제 4: 지정 된 텍스트로 시작 하는 모든 명령에 중단점 설정

이 예에서는와 같이 "write"로 시작 하는 Sample.ps1 스크립트의 모든 명령에 대 한 중단점을 설정 `Write-Host` 합니다.

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### 예 5: 변수 값에 따라 중단점 설정

이 예에서는 `DiskTest` 변수 값이 2 보다 큰 경우에만 Test.ps1 스크립트의 함수에서 실행을 중지 `$Disk` 합니다.

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

**동작** 의 값은 함수의 변수 값을 테스트 하는 스크립트 블록입니다 `$Disk` .

`break`이 동작은 조건을 충족 하는 경우 키워드를 사용 하 여 실행을 중지 합니다. 대안 (및 기본값)은 **계속** 입니다.

### 예제 6: 함수에 중단점 설정

이 예제에서는 함수에 대 한 중단점을 설정 `CheckLog` 합니다. 이 명령은 스크립트를 지정하지 않으므로 중단점은 현재 세션에서 실행되는 모든 항목에 설정됩니다. 디버거는 함수가 선언될 때가 아니라 호출될 때 중단됩니다.

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### 예제 7: 여러 줄에 중단점 설정

이 예제에서는 Sample.ps1 스크립트에 세 개의 줄 중단점을 설정 합니다. 스크립트에서 지정된 각 줄의 열 2에 중단점을 하나씩 설정합니다. **Action** 매개 변수에 지정 된 작업은 모든 중단점에 적용 됩니다.

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## PARAMETERS

### -Action

각 중단점에서 중단되지 않는 대신 실행되는 명령을 지정합니다. 명령을 포함하는 스크립트 블록을 입력합니다. 이 매개 변수를 사용하여 조건부 중단점을 설정하거나 테스트 또는 로깅 같은 다른 작업을 수행할 수 있습니다.

이 매개 변수를 생략하거나 작업을 지정하지 않으면 중단점에서 실행이 중지되고 디버거가 시작됩니다.

**Action** 매개 변수를 사용 하면 각 중단점에서 action 스크립트 블록이 실행 됩니다. 스크립트 블록에 Break 키워드가 포함되지 않은 한 계속 실행됩니다. 스크립트 블록에서 Continue 키워드를 사용하면 다음 중단점까지 실행이 다시 시작됩니다.

자세한 내용은 [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)및 [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md)를 참조 하세요.

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

### -열

스크립트 파일에서 실행이 중지되는 열의 열 번호를 지정합니다. 열 번호는 하나만 입력합니다. 기본값은 열 1입니다.

열 값은 **Line** 매개 변수 값과 함께 중단점을 지정 하는 데 사용 됩니다. **Line** 매개 변수가 여러 줄을 지정 하는 경우 **Column** 매개 변수는 지정 된 각 줄의 지정 된 열에 중단점을 설정 합니다. PowerShell은 지정 된 줄 및 열 위치에 있는 문자가 포함 된 문 또는 식 앞에서 실행을 중지 합니다.

열은 왼쪽 위 여백에서부터 열 번호 1(0 아님)로 계산됩니다. 스크립트에 없는 열을 지정하는 경우 오류가 선언되지는 않지만 중단점도 실행되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

명령 중단점을 설정합니다. Cmdlet 이름 (예: `Get-Process` 또는 함수 이름)을 입력 합니다. 와일드카드가 지원됩니다.

각 명령의 각 인스턴스가 실행되기 직전에 실행이 중지됩니다. 명령이 함수인 경우 함수가 호출될 때마다, 그리고 각 BEGIN, PROCESS 및 END 섹션에서 실행이 중지됩니다.

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -줄

스크립트에 줄 중단점을 설정합니다. 하나 이상의 줄 번호를 쉼표로 구분하여 입력합니다. PowerShell은 지정 된 각 줄에서 시작 하는 문을 실행 하기 직전에 중지 됩니다.

줄은 스크립트 파일의 왼쪽 위 여백에서부터 줄 번호 1(0 아님)로 계산됩니다.
빈 줄을 지정하면 빈 줄이 아닌 다음 줄 앞에서 실행이 중지됩니다. 줄이 범위를 벗어나는 경우 중단점은 실행되지 않습니다.

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Mode

변수 중단점을 트리거하는 액세스 모드를 지정 합니다. 기본값은 **Write** 입니다.

이 매개 변수는 명령에서 **변수** 매개 변수가 사용 되는 경우에만 유효 합니다. 이 모드는 명령에 설정된 모든 중단점에 적용됩니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- **쓰기** -변수에 새 값을 쓰기 직전에 실행을 중지 합니다.
- **읽기** -변수를 읽을 때 즉, 할당, 표시 또는 사용 하기 위해 해당 값에 액세스 하는 경우 실행을 중지 합니다. 읽기 모드에서는 변수 값이 변경될 때 실행이 중지되지 않습니다.
- **ReadWrite** -변수를 읽거나 쓸 때 실행을 중지 합니다.

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -스크립트

이 cmdlet이 중단점을 설정 하는 스크립트 파일의 배열을 지정 합니다. 스크립트 파일 중 하나 이상의 경로 및 파일 이름을 입력합니다. 파일이 현재 디렉터리에 있는 경우 경로를 생략할 수 있습니다.
와일드카드가 지원됩니다.

기본적으로 변수 중단점과 명령 중단점은 현재 세션에서 실행되는 모든 명령에 설정할 수 있습니다. 이 매개 변수는 줄 중단점을 설정하는 경우에만 필요합니다.

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

이 cmdlet이 중단점을 설정 하는 변수의 배열을 지정 합니다. 달러 기호 ()를 제외 하 고 쉼표로 구분 된 변수 목록을 입력 `$` 합니다.

**Mode** 매개 변수를 사용 하 여 중단점을 트리거하는 액세스 모드를 확인 합니다. 기본 모드인 Write에서는 변수에 새 값을 쓰기 직전에 실행이 중지됩니다.

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
입력을로 파이프 할 수 없습니다 `Set-PSBreakpoint` .

## 출력

### 중단점 개체 (VariableBreakpoint,, System.web. n a m a. n a m.

`Set-PSBreakpoint` 설정 하는 각 중단점을 나타내는 개체를 반환 합니다.

## 참고

- `Set-PSBreakpoint` 원격 컴퓨터에 중단점을 설정할 수 없습니다. 원격 컴퓨터에서 스크립트를 디버그하려면 스크립트를 로컬 컴퓨터로 복사한 다음 로컬로 디버그하세요.
- 둘 이상의 줄, 명령 또는 변수에 중단점을 설정 하면에서 `Set-PSBreakpoint` 각 항목에 대 한 중단점 개체를 생성 합니다.
- 명령 프롬프트에서 함수 또는 변수에 중단점을 설정하는 경우 함수 또는 변수를 만들기 전이나 만든 후에 중단점을 설정할 수 있습니다.

## 관련 링크

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

