---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 6afabaf46907d317ec864519a658c500466d4c38
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213041"
---
# Get-PSBreakpoint

## 개요
현재 세션에 설정된 중단점을 가져옵니다.

## SYNTAX

### 스크립트 (기본값)

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### 변수

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### 명령

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### 유형

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### Id

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## 설명

**Get psbreakpoint** cmdlet은 현재 세션에 설정 된 중단점을 가져옵니다.
cmdlet 매개 변수를 사용하여 특정 중단점을 가져올 수 있습니다.

중단점은 명령 또는 스크립트에서 명령을 조사할 수 있도록 실행이 일시적으로 중지되는 지점입니다.
**Get PSBreakpoint** 은 PowerShell 스크립트 및 명령을 디버깅 하기 위해 디자인 된 여러 cmdlet 중 하나입니다. PowerShell 디버거에 대 한 자세한 내용은 about_Debuggers를 참조 하세요.

## 예제

### 예제 1: 모든 스크립트 및 함수에 대 한 모든 중단점 가져오기

```
PS C:\> Get-PSBreakpoint
```

이 명령은 현재 세션의 모든 스크립트 및 함수에 설정된 모든 중단점을 가져옵니다.

### 예제 2: ID로 중단점 가져오기

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

이 명령은 중단점 ID가 2인 중단점을 가져옵니다.

### 예 3: Get-PSBreakpoint에 대 한 ID 파이프

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

이 명령은 중단점 ID를 **Get psbreakpoint** 에 파이프 하 여 중단점을 가져오는 방법을 보여 줍니다.

첫 번째 명령은 Set-PSBreakpoint cmdlet을 사용하여 Sample.ps1 스크립트의 Increment 함수에 중단점을 만들고, $B 변수에 중단점 개체를 저장 합니다.

두 번째 명령은 점 연산자 (.)를 사용 하 여 $B 변수에서 중단점 개체의 Id 속성을 가져옵니다. 파이프라인 연산자 (|)를 사용 하 여 ID를 **Get PSBreakpoint** cmdlet으로 보냅니다.

결과적으로, **Get psbreakpoint** 지정 된 ID의 중단점을 가져옵니다.

### 예제 4: 지정 된 스크립트 파일에서 중단점 가져오기

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

이 명령은 Sample.ps1 및 SupportScript.ps1 파일에서 모든 중단점을 가져옵니다.

이 명령은 세션의 다른 스크립트나 함수에 설정 되었을 수 있는 다른 중단점을 가져오지 않습니다.

### 예 5: 지정 된 cmdlet에서 중단점 가져오기

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

이 명령은 Sample.ps1 파일의 Read-Host 또는 Write-Host 명령에 설정된 모든 Command 중단점을 가져옵니다.

### 예제 6: 지정 된 파일에서 명령 중단점 가져오기

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

이 명령은 Sample.ps1 파일에서 모든 Command 중단점을 가져옵니다.

### 예 7: 변수를 기준으로 중단점 가져오기

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

이 명령은 $Index에 설정 된 중단점과 현재 세션의 $Swap 변수를 가져옵니다.

### 예 8: 파일에서 모든 줄 및 변수 중단점 가져오기

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

이 명령은 Sample.ps1 스크립트에서 모든 줄 및 변수 중단점을 가져옵니다.

## PARAMETERS

### -Command

지정 된 명령 이름에 설정 된 명령 중단점의 배열을 지정 합니다.
cmdlet이나 함수의 이름과 같은 명령 이름을 입력합니다.

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

이 cmdlet이 가져오는 중단점 Id를 지정 합니다.
쉼표로 구분된 목록에 ID를 입력합니다.
중단점 Id를 **psbreakpoint** 로 파이프 할 수도 있습니다.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -스크립트

중단점이 포함 된 스크립트의 배열을 지정 합니다.
하나 이상의 스크립트 파일의 경로 (선택 사항) 및 이름을 입력 합니다.
경로를 생략할 경우 기본 위치는 현재 디렉터리입니다.

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Type

이 cmdlet이 가져오는 중단점 형식의 배열을 지정 합니다.
하나 이상의 유형을 입력합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 선
- 명령
- 변수

중단점 형식을 **Get psbreakpoint** 로 파이프 할 수도 있습니다.

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Variable

지정 된 변수 이름에 설정 된 변수 중단점의 배열을 지정 합니다.
달러 기호 없이 변수 이름을 입력합니다.

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 about_CommonParameters(https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.object, Microsoft. PowerShell.

중단점 Id 및 중단점 형식을 **Get psbreakpoint** 에 파이프 할 수 있습니다.

## 출력

### System.object. 중단점

**Get PSBreakPoint** 세션의 중단점을 나타내는 개체를 반환 합니다.

## 참고

* **Get PSBreakpoint** 나 해당 별칭인 "gbp"를 사용할 수 있습니다.

## 관련 링크

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

