---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 2eeacf8703dbe0f662d0b26d405c605d21c2b84e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390357"
---
# Wait-Job

## 개요
세션에서 실행 중인 PowerShell 백그라운드 작업 중 하나 또는 모두가 완료 될 때까지 명령 프롬프트를 표시 하지 않습니다.

## SYNTAX

### SessionIdParameterSet (기본값)

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### JobParameterSet

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### NameParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### StateParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### FilterParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## 설명

`Wait-Job`Cmdlet은 명령 프롬프트를 표시 하기 전에 PowerShell 백그라운드 작업이 완료 될 때까지 기다립니다. 백그라운드 작업 중 하나가 완료되거나 모든 백그라운드 작업이 완료될 때까지 기다릴 수 있으며 작업의 최대 대기 시간을 설정할 수 있습니다.

작업의 명령이 완료 되 면에서 `Wait-Job` 명령 프롬프트를 표시 하 고 작업 개체를 반환 하 여 다른 명령으로 파이프 합니다.

Cmdlet을 사용 하 여 cmdlet `Wait-Job` `Start-Job` 또는 Cmdlet의 **AsJob** 매개 변수를 사용 하 여 시작한 것과 같은 백그라운드 작업을 기다릴 수 있습니다 `Invoke-Command` . Windows PowerShell 백그라운드 작업에 대한 자세한 내용은 [about_Jobs](./about/about_Jobs.md)를 참조하세요.

Windows PowerShell 3.0부터 `Wait-Job` cmdlet은 워크플로 작업, 예약 된 작업 인스턴스 등의 사용자 지정 작업 유형도 대기 합니다. 를 사용 하 여 `Wait-Job` 특정 형식의 작업을 대기 하려면 cmdlet `Get-Job` 을 사용 `Import-Module` 하거나 모듈에서 cmdlet을 사용 하 여 cmdlet을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다. 특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.

## 예제

### 예 1: 모든 작업 대기

```powershell
Get-Job | Wait-Job
```

이 명령은 세션에서 실행 중인 모든 백그라운드 작업이 완료 될 때까지 대기 합니다.

### 예 2: Start-Job을 사용 하 여 원격 컴퓨터에서 시작 된 작업 대기

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

이 예에서는 cmdlet을 사용 하 `Wait-Job` 여 원격 컴퓨터에서 시작 된 작업과 cmdlet을 사용 하는 방법을 보여 줍니다 `Start-Job` . `Start-Job`및 `Wait-Job` 명령은 모두 cmdlet을 사용 하 여 원격 컴퓨터에 전송 됩니다 `Invoke-Command` .

이 예에서는 `Wait-Job` 를 사용 하 여 `Get-Date` 3 개의 다른 컴퓨터에서 백그라운드 작업으로 실행 되는 명령을 완료 했는지 확인 합니다.

첫 번째 명령은 각 원격 컴퓨터에 Windows PowerShell 세션 ( **PSSession** )을 만든 다음 변수에 저장 합니다 `$s` .

두 번째 명령은 `Invoke-Command` 를 사용 하 여 `Start-Job` 에 있는 세 개의 세션에서를 실행 `$s` 합니다.
모든 작업은 날짜 1로 지정 됩니다.

세 번째 명령은 `Invoke-Command` 를 사용 하 여를 실행 `Wait-Job` 합니다. 이 명령은 각 컴퓨터에서 Date1 작업이 완료 될 때까지 기다립니다. 작업 개체의 결과 컬렉션 (배열)을 `$done` 변수에 저장 합니다.

네 번째 명령은 변수에 작업 개체 배열의 **Count** 속성을 사용 하 여 `$done` 완료 된 작업의 수를 확인 합니다.

### 예 3: 첫 번째 백그라운드 작업이 완료 되는 시점 결정

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

이 예제에서는의 **Any** 매개 변수를 사용 하 여 `Wait-Job` 현재 세션에서 실행 중인 많은 백그라운드 작업 중 첫 번째 작업이 완료 된 시기를 확인 합니다. 또한 cmdlet을 사용 하 여 `Wait-Job` 원격 작업이 완료 될 때까지 대기 하는 방법을 보여 줍니다.

첫 번째 명령은 Machines.txt 파일에 나열 된 각 컴퓨터에 **pssession** 을 만들고 **pssession** 개체를 변수에 저장 합니다 `$s` . 이 명령은 cmdlet을 사용 하 여 `Get-Content` 파일의 내용을 가져옵니다. 명령은 `Get-Content` 명령 전에 실행 되도록 괄호로 묶습니다 `New-PSSession` .

두 번째 명령은 `Get-EventLog` 변수에 명령 문자열 (따옴표)을 저장 합니다 `$c` .

세 번째 명령은 cmdlet을 사용 하 여의 `Invoke-Command` `Start-Job` 각 세션에서를 실행 `$s` 합니다.
`Start-Job`명령은 `Get-EventLog` 변수에서 명령을 실행 하는 백그라운드 작업을 시작 합니다 `$c` .

이 명령은 **Using** 범위 한정자를 사용 하 여 `$c` 변수가 로컬 컴퓨터에 정의 되어 있음을 표시 합니다. **Using** 범위 한정자는 Windows PowerShell 3.0에서 도입되었습니다. **Using** 범위 한정자에 대 한 자세한 내용은 [about_Remote_Variables](./about/about_Remote_Variables.md)를 참조 하세요.

네 번째 명령은 `Invoke-Command` 를 사용 하 여 `Wait-Job` 세션에서 명령을 실행 합니다. **모든** 매개 변수를 사용 하 여 원격 컴퓨터의 첫 번째 작업이 완료 될 때까지 대기 합니다.

### 예제 4: 원격 컴퓨터에서 작업에 대 한 대기 시간 설정

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

이 예제에서는의 **Timeout** 매개 변수를 사용 하 여 `Wait-Job` 원격 컴퓨터에서 실행 되는 작업의 최대 대기 시간을 설정 하는 방법을 보여 줍니다.

첫 번째 명령은 원격 컴퓨터 3 개 (Server01, Server02 및 Server03) 각각에 **pssession** 을 만든 다음, **pssession** 개체를 변수에 저장 합니다 `$s` .

두 번째 명령은를 사용 하 여의 `Invoke-Command` `Start-Job` 각 **PSSession** 개체에서를 실행 합니다 `$s` . 결과 작업 개체를 `$jobs` 변수에 저장 합니다.

세 번째 명령은를 사용 하 여의 `Invoke-Command` `Wait-Job` 각 세션에서를 실행 합니다 `$s` . `Wait-Job`명령은 모든 명령이 30 초 이내에 완료 되었는지 여부를 확인 합니다. **시간 제한** 매개 변수를 30 값으로 사용 하 여 최대 대기 시간을 설정 하 고 명령의 결과를 `$done` 변수에 저장 합니다.

이 경우 30초 후에 Server02 컴퓨터의 명령만 완료됩니다. `Wait-Job` 대기를 종료 하 고 명령 프롬프트를 표시 한 다음 완료 된 작업을 나타내는 개체를 반환 합니다.

`$done`변수에는 Server02에서 실행 된 작업을 나타내는 작업 개체가 포함 되어 있습니다.

### 예 5: 여러 작업 중 하나가 완료 될 때까지 대기

```powershell
Wait-Job -id 1,2,5 -Any
```

이 명령은 Id로 세 가지 작업을 식별 하 고 그 중 하나가 완료 될 때까지 대기 합니다.
첫 번째 작업이 완료 되 면 명령 프롬프트가 반환 됩니다.

### 예 6: 일정 기간 동안 기다린 후 작업이 백그라운드에서 계속 되도록 허용

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

이 명령은 DailyLog 작업이 완료 될 때까지 120 초 (2 분) 동안 대기 합니다. 작업이 다음 2 분 이내에 완료 되지 않으면 명령 프롬프트가 반환 되 고 작업은 백그라운드에서 계속 실행 됩니다.

### 예 7: 이름으로 작업 대기

```powershell
Wait-Job -Name "Job3"
```

이 명령은 작업 이름을 사용 하 여 기다릴 작업을 식별 합니다.

### 예 8: Start-Job 시작 하 여 로컬 컴퓨터에서 작업 대기

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

이 예에서는를 `Wait-Job` 사용 하 여 로컬 컴퓨터에서 시작 된 작업에 cmdlet을 사용 하는 방법을 보여 줍니다 `Start-Job` .

이 명령은 지난주에 추가 또는 업데이트된 Windows PowerShell 스크립트 파일을 가져오는 작업을 시작합니다.

첫 번째 명령은 `Start-Job` 를 사용 하 여 로컬 컴퓨터에서 백그라운드 작업을 시작 합니다. 작업은 `Get-ChildItem` 지난 주에 추가 되거나 업데이트 된 ps1 파일 이름 확장명을 가진 모든 파일을 가져오는 명령을 실행 합니다.

세 번째 명령은를 사용 하 여 `Wait-Job` 작업이 완료 될 때까지 대기 합니다. 작업이 완료 되 면 명령에서 작업에 대 한 정보가 포함 된 작업 개체를 표시 합니다.

### 예 9: Invoke-Command을 사용 하 여 원격 컴퓨터에서 시작 된 작업 대기

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

이 예에서는 `Wait-Job` 의 **AsJob** 매개 변수를 사용 하 여 원격 컴퓨터에서 시작 된 작업과 함께를 사용 하는 방법을 보여 줍니다 `Invoke-Command` . **AsJob** 을 사용할 경우 작업이 원격 컴퓨터에서 실행 되는 경우에도 로컬 컴퓨터에 작업이 만들어지고 결과가 로컬 컴퓨터에 자동으로 반환 됩니다.

이 예에서는 `Wait-Job` 를 사용 하 여 `Get-Process` 원격 컴퓨터 3 대의 세션에서 실행 중인 명령이 완료 되었는지 여부를 확인 합니다.

첫 번째 명령은 3 대의 컴퓨터에 **PSSession** 개체를 만든 후 변수에 저장 합니다 `$s` .

두 번째 명령은 `Invoke-Command` 를 사용 하 여 `Get-Process` 에 있는 세 개의 세션에서를 실행 `$s` 합니다.
이 명령은 **AsJob** 매개 변수를 사용 하 여 백그라운드 작업으로 비동기적으로 명령을 실행 합니다. 를 사용 하 여 시작 된 작업과 마찬가지로 작업 개체가 반환 `Start-Job` 되 고 작업 개체가 변수에 저장 됩니다 `$j` .

세 번째 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 작업 개체를 `$j` cmdlet으로 보냅니다 `Wait-Job` . `Invoke-Command`작업이 로컬 컴퓨터에 있기 때문에이 경우에는 명령이 필요 하지 않습니다.

### 예 10: ID가 있는 작업 대기

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

이 명령은 ID 값이 1인 작업이 완료될 때까지 대기합니다.

## PARAMETERS

### -Any

작업이 완료 되 면이 cmdlet이 명령 프롬프트를 표시 하 고 작업 개체를 반환 함을 나타냅니다. 기본적으로는 `Wait-Job` 지정 된 모든 작업이 완료 될 때까지 기다렸다가 프롬프트가 표시 됩니다.

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

### -Filter

조건에 대 한 해시 테이블을 지정 합니다. 이 cmdlet은 해시 테이블의 모든 조건을 충족 하는 작업을 대기 합니다. 키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.

이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다. Cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다 `Start-Job` . 이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

이 cmdlet이 일시 중단 되었거나 연결 되지 않은 상태의 작업을 계속 대기 하 고 있음을 나타냅니다. 기본적으로는 `Wait-Job` 작업이 다음 상태 중 하나일 때 대기를 반환 하거나 종료 합니다.

- Completed
- 실패
- 중지됨
- 일시 중단
- 연결 끊김

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -Id

이 cmdlet이 대기 하는 작업의 Id 배열을 지정 합니다.

ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다. 인스턴스 ID 보다 더 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다. 하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다. 작업 ID를 찾으려면를 입력 `Get-Job` 합니다.

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

이 cmdlet이 대기 하는 작업의 인스턴스 Id 배열을 지정 합니다. 기본값은 모든 작업입니다.

인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다. 작업의 인스턴스 ID를 찾으려면를 사용 `Get-Job` 합니다.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Job

이 cmdlet이 대기 하는 작업을 지정 합니다. 작업 개체가 포함된 변수 또는 작업 개체를 가져오는 명령을 입력하세요. 파이프라인 연산자를 사용 하 여 작업 개체를 cmdlet으로 보낼 수도 있습니다 `Wait-Job` . 기본적으로는 `Wait-Job` 현재 세션에서 생성 된 모든 작업을 대기 합니다.

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

이 cmdlet이 대기 하는 작업의 이름을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -상태

작업 상태를 지정 합니다. 이 cmdlet은 지정 된 상태의 작업만 대기 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- NotStarted
- 실행 중
- 완료됨
- 실패
- 중지됨
- 차단
- 일시 중단
- 연결 끊김
- Suspending
- 중지 중

작업 상태에 대 한 자세한 내용은 [JobState 열거](/dotnet/api/system.management.automation.jobstate)를 참조 하세요.

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -시간 제한

각 백그라운드 작업에 대 한 최대 대기 시간 (초)을 지정 합니다. 기본값-1은 작업이 완료 될 때까지 cmdlet이 대기 함을 나타냅니다. 타이밍은 명령이 아니라 명령을 제출할 때 시작 됩니다 `Wait-Job` `Start-Job` .

이 시간을 초과할 경우 작업이 여전히 실행 중이어도 대기가 종료되고 명령 프롬프트가 반환됩니다. 이 명령은 오류 메시지를 표시 하지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. Remorererea 작업

작업 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### System.web. a p.

이 cmdlet은 완료 된 작업을 나타내는 작업 개체를 반환 합니다. **Timeout** 매개 변수의 값이 초과 되어 대기가 종료 되는 경우는 `Wait-Job` 개체를 반환 하지 않습니다.

## 참고

기본적으로는 `Wait-Job` 작업이 다음 상태 중 하나일 때 대기를 반환 하거나 종료 합니다.

- Completed
- 실패
- 중지됨
- 일시 중단
- 직접 이동 하 여 `Wait-Job` 일시 중단 되 고 연결 되지 않은 작업을 계속 대기 하려면 **Force** 매개 변수를 사용 합니다.

## 관련 링크

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)
