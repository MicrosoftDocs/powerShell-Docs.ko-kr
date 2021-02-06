---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 479c099d2d5daf1cc50c5c645be053ff4ae02bdc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601854"
---
# Stop-Job

## 개요
PowerShell 백그라운드 작업을 중지 합니다.

## SYNTAX

### SessionIdParameterSet (기본값)

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Stop-Job`Cmdlet은 진행 중인 PowerShell 백그라운드 작업을 중지 합니다. 이 cmdlet을 사용 하 여 모든 작업을 중지 하거나 이름, ID, 인스턴스 ID 또는 상태를 기준으로 또는 작업 개체를에 전달 하 여 선택한 작업을 중지할 수 있습니다 `Stop-Job` .

Cmdlet을 사용 하 여 `Stop-Job` 시작한 것과 같은 백그라운드 작업 `Start-Job` 또는 Cmdlet의 **AsJob** 매개 변수를 사용 하 여 작업을 중지할 수 있습니다. 백그라운드 작업을 중지 하면 PowerShell은 해당 작업 큐에서 보류 중인 모든 작업을 완료 한 다음 작업을 종료 합니다. 이 명령을 제출한 후에는 새 작업이 큐에 추가되지 않습니다.

이 cmdlet은 백그라운드 작업을 삭제하지 않습니다. 작업을 삭제 하려면 cmdlet을 사용 `Remove-Job` 합니다.

Windows PowerShell 3.0부터에서는 `Stop-Job` 워크플로 작업 및 예약 된 작업 인스턴스 등의 사용자 지정 작업 유형도 중지 합니다. 에서 `Stop-Job` 사용자 지정 작업 유형을 사용 하 여 작업을 중지 하려면 `Stop-Job` cmdlet을 사용 `Import-Module` 하거나 모듈에서 cmdlet을 사용 하 여 명령을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다. 특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.

## 예제

### 예 1: Invoke-Command을 사용 하 여 원격 컴퓨터에서 작업 중지

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

이 예에서는 cmdlet을 사용 하 여 `Stop-Job` 원격 컴퓨터에서 실행 중인 작업을 중지 하는 방법을 보여 줍니다.

작업은 cmdlet을 사용 하 여 원격으로 명령을 실행 하 여 시작 되었으므로 `Invoke-Command` `Start-Job` 작업 개체가 원격 컴퓨터에 저장 됩니다. `Invoke-Command`명령을 원격으로 실행 하려면 다른 명령을 사용 해야 합니다 `Stop-Job` . 원격 백그라운드 작업에 대한 자세한 내용은 about_Remote_Jobs를 참조하세요.

첫 번째 명령은 Server01 컴퓨터에 PowerShell 세션 (**PSSession**)을 만든 다음 세션 개체를 변수에 저장 합니다 `$s` . 이 명령은 도메인 관리자의 자격 증명을 사용합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Start-Job` 세션에서 명령을 실행 합니다. 작업의 명령은 시스템 이벤트 로그에 있는 모든 이벤트를 가져옵니다. 결과 작업 개체는 변수에 저장 됩니다 `$j` .

세 번째 명령은 작업을 중지합니다. Cmdlet을 사용 하 여 `Invoke-Command` `Stop-Job` Server01의 **PSSession** 에서 명령을 실행 합니다. 작업 개체는 `$j` 로컬 컴퓨터의 변수인에 저장 되므로 명령에서 Using 범위 한정자를 사용 하 여을 `$j` 지역 변수로 식별 합니다.
Using 범위 한정자에 대 한 자세한 내용은 [about_Remote_Variables](about/about_Remote_Variables.md)를 참조 하세요.

명령이 완료 되 면 작업이 중지 되 고의 **PSSession** 을 `$s` 사용할 수 있습니다.

### 예 2: 백그라운드 작업 중지

```powershell
Stop-Job -Name "Job1"
```

이 명령은 Job1 백그라운드 작업을 중지합니다.

### 예제 3: 여러 백그라운드 작업 중지

```powershell
Stop-Job -Id 1, 3, 4
```

이 명령은 작업 3개를 중지합니다.
해당 ID로 작업을 식별합니다.

### 예제 4: 모든 백그라운드 작업 중지

```powershell
Get-Job | Stop-Job
```

이 명령은 현재 세션에서 모든 백그라운드 작업을 중지합니다.

### 예 5: 차단 된 모든 백그라운드 작업 중지

```powershell
Stop-Job -State Blocked
```

이 명령은 차단된 모든 작업을 중지합니다.

### 예 6: 인스턴스 ID를 사용 하 여 작업 중지

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

이 명령은 해당 인스턴스 ID를 기준으로 작업을 중지하는 방법을 보여 줍니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Job` 현재 세션의 작업을 가져옵니다. 이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 작업을 명령으로 보냅니다 `Format-Table` .이 명령은 각 작업의 지정 된 속성 테이블을 표시 합니다. 테이블에는 각 작업의 인스턴스 ID가 포함되어 있습니다. 또한 계산된 속성을 사용하여 작업 상태를 표시합니다.

두 번째 명령은 `Stop-Job` **InstanceID** 매개 변수가 있는 명령을 사용 하 여 선택한 작업을 중지 합니다.

### 예 7: 원격 컴퓨터에서 작업 중지

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

이 예에서는 cmdlet을 사용 하 여 `Stop-Job` 원격 컴퓨터에서 실행 중인 작업을 중지 하는 방법을 보여 줍니다.

Cmdlet의 **AsJob** 매개 변수를 사용 하 여 작업을 시작 했으므로 작업이 `Invoke-Command` 원격 컴퓨터에서 실행 되더라도 작업 개체는 로컬 컴퓨터에 있습니다. 따라서 로컬 명령을 사용 하 여 작업을 중지할 수 있습니다 `Stop-Job` .

첫 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` Server01 컴퓨터에서 백그라운드 작업을 시작 합니다. **AsJob** 매개 변수를 사용하여 원격 명령을 백그라운드 작업으로 실행합니다.

이 명령은 cmdlet이 반환 하는 것과 동일한 작업 개체인 작업 개체를 반환 `Start-Job` 합니다.
이 명령은 작업 개체를 `$j` 변수에 저장 합니다.

두 번째 명령은 파이프라인 연산자를 사용 하 여 변수에서 작업을 `$j` 로 보냅니다 `Stop-Job` . 이 명령은 **PassThru** 매개 변수를 사용 하 여 `Stop-Job` 작업 개체를 반환 하도록 지시 합니다. 작업 개체 표시는 작업 상태가 중지 됨 인지 확인 합니다.

원격 백그라운드 작업에 대한 자세한 내용은 about_Remote_Jobs를 참조하세요.

## PARAMETERS

### -Filter

조건에 대 한 해시 테이블을 지정 합니다. 이 cmdlet은 모든 조건을 충족 하는 작업을 중지 합니다.
키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.

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

### -Id

이 cmdlet이 중지 하는 작업의 Id를 지정 합니다. 기본값은 현재 세션의 모든 작업입니다.

ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다. 인스턴스 ID 보다 더 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다. 하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다. 작업 ID를 찾으려면를 입력 `Get-Job` 합니다.

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

이 cmdlet이 중지 하는 작업의 인스턴스 Id를 지정 합니다. 기본값은 모든 작업입니다.

인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다. 작업의 인스턴스 ID를 찾으려면를 사용 `Get-Job` 합니다.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Job

이 cmdlet이 중지 하는 작업을 지정 합니다. 작업이 포함된 변수 또는 작업을 가져오는 명령을 입력합니다. 파이프라인 연산자를 사용 하 여 작업을 cmdlet에 제출할 수도 있습니다 `Stop-Job` . 기본적으로는 `Stop-Job` 현재 세션에서 시작 된 모든 작업을 삭제 합니다.

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

이 cmdlet이 중지 하는 작업의 이름을 지정 합니다. 쉼표로 구분된 목록으로 작업 이름을 입력하거나 와일드카드 문자(*)를 사용하여 작업 이름 패턴을 입력합니다. 기본적으로는 `Stop-Job` 현재 세션에서 만든 모든 작업을 중지 합니다.

이름이 고유 하지 않을 수 있으므로 작업을 이름별로 중지할 때 **WhatIf** 및 **Confirm** 매개 변수를 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -상태

작업 상태를 지정 합니다. 이 cmdlet은 지정 된 상태의 작업만 중지 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

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
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
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
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. Remorererea 작업

작업 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음, 시스템 관리.

**PassThru** 매개 변수를 지정 하는 경우이 cmdlet은 작업 개체를 반환 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

## 관련 링크

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Wait-Job](Wait-Job.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Remote_Variables](About/about_Remote_Variables.md)

[about_Jobs](About/about_Jobs.md)

[about_Scopes](About/about_scopes.md)
