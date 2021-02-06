---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 3f01b7624ffcbca472b09bdb83a7440f3526db43
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599586"
---
# Debug-Runspace

## 개요
Runspace를 사용 하 여 대화형 디버깅 세션을 시작 합니다.

## SYNTAX

### RunspaceParameterSet (기본값)

```
Debug-Runspace [-Runspace] <Runspace> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Debug-Runspace [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### IdParameterSet

```
Debug-Runspace [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Debug-Runspace [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Debug-Runspace`Cmdlet은 로컬 또는 원격 활성 runspace를 사용 하 여 대화형 디버깅 세션을 시작 합니다. `Get-Process`Powershell과 연결 된 프로세스를 찾은 다음 `Enter-PSHostProcess` **id** 매개 변수에 지정 된 프로세스 id를 사용 하 여 프로세스에 연결 하 고 `Get-Runspace` powershell 호스트 프로세스 내에서 runspace을 나열 하려면 먼저를 실행 하 여 디버깅할 runspace를 찾을 수 있습니다.

디버깅할 runspace를 선택 하 고 runspace에서 현재 명령이 나 스크립트를 실행 하 고 있거나 스크립트가 중단점에서 중지 된 경우 PowerShell에서 runspace에 대 한 원격 디버거 세션을 엽니다. 원격 세션 스크립트를 디버깅 하는 것과 같은 방법으로 runspace 스크립트를 디버그할 수 있습니다.

프로세스를 실행 하는 컴퓨터의 관리자 이거나 디버깅 하려는 스크립트를 실행 하는 경우에만 PowerShell 호스트 프로세스에 연결할 수 있습니다. 또한 현재 PowerShell 세션을 실행 하는 호스트 프로세스를 입력할 수 없습니다. 다른 PowerShell 세션을 실행 하는 호스트 프로세스만 입력할 수 있습니다.

## 예제

### 예제 1: 원격 runspace 디버깅

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

이 예제에서는 원격 컴퓨터 WS10TestServer에서 열려 있는 runspace를 디버깅 합니다. 명령의 첫 번째 줄에서 `Get-Process` 원격 컴퓨터에서를 실행 하 고 Windows PowerShell 호스트 프로세스를 필터링 합니다. 이 예제에서는 Windows PowerShell ISE 호스트 프로세스의 프로세스 ID 1152을 디버깅 하려고 합니다.

두 번째 명령에서는 `Enter-PSSession` 를 실행 하 여 WS10TestServer에서 원격 세션을 엽니다. 세 번째 명령은를 실행 하 `Enter-PSHostProcess` 고 첫 번째 명령 1152에서 가져온 호스트 프로세스의 ID를 지정 하 여 원격 서버에서 실행 되는 Windows PowerShell ISE 호스트 프로세스에 연결 합니다.

네 번째 명령에서를 실행 하 여 프로세스 ID 1152에 대해 사용 가능한 runspace를 나열 `Get-Runspace` 합니다.
사용 중인 runspace의 ID 번호를 확인 합니다. 디버깅 하려는 스크립트를 실행 하 고 있습니다.

마지막 명령은 스크립트를 실행 하는 열린 runspace TestWFVar1.ps1를 디버깅 하기 시작 하 고,를 실행 하 `Debug-Runspace` 고, **id** 매개 변수를 추가 하 여 해당 id로 runspace를 식별 합니다 (2). 스크립트에 중단점이 있기 때문에 디버거가 열립니다.

## PARAMETERS

### -Id

Runspace의 ID 번호를 지정 합니다. `Get-Runspace`를 실행 하 여 Runspace id를 표시할 수 있습니다.

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

실행 하 여 표시할 수 있는 GUID 인 인스턴스 ID로 runspace를 지정 합니다 `Get-Runspace` .

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

이름을 기준으로 runspace를 지정 합니다. `Get-Runspace`을 실행 하 여 runspace의 이름을 표시할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Runspace

Runspace 개체를 지정 합니다. 이 매개 변수에 대 한 값을 제공 하는 가장 간단한 방법은 필터링 된 명령의 결과를 포함 하는 변수를 지정 하는 것입니다 `Get-Runspace` .

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -간

{{모든 설명 채우기 설명}}

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Runspace입니다.

명령의 결과를 `Get-Runspace` **디버그 Runspace** 로 파이프 할 수 있습니다.

## 출력

## 참고

`Debug-Runspace` 열림 상태의 runspace에서 작동 합니다. Runspace 상태가 열림에서 다른 상태로 변경 되는 경우이 runspace는 실행 중인 목록에서 자동으로 제거 됩니다. Runspace는 다음 조건을 충족 하는 경우에만 실행 목록에 추가 됩니다.

- 호출에서 오는 경우 즉, `Invoke-Command` GUID ID가 있습니다.
- 에서 제공 되는 경우입니다 `Debug-Runspace` . 즉, `Debug-Runspace` GUID ID가 있습니다.
- PowerShell 워크플로에서 오는 경우 워크플로 작업 ID가 현재 활성 디버거 워크플로 작업 ID와 동일 합니다.

## 관련 링크

[about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[Debug-Job](../Microsoft.PowerShell.Core/Debug-Job.md)

[Get-Runspace](Get-Runspace.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

[Enter-PSHostProcess](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[Enter-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)

