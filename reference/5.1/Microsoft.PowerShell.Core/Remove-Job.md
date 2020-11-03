---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 589c43c814d5d68e57fd20226c675bf0f9587b69
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212793"
---
# Remove-Job

## 개요
PowerShell 백그라운드 작업을 삭제 합니다.

## SYNTAX

### SessionIdParameterSet (기본값)

```
Remove-Job [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Remove-Job [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Remove-Job [-InstanceId] <Guid[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Remove-Job [-Filter] <Hashtable> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandParameterSet

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Remove-Job`Cmdlet은 `Start-Job` Cmdlet 또는 `Invoke-Command` **AsJob** 매개 변수를 지 원하는 Cmdlet에 의해 시작 된 PowerShell 백그라운드 작업을 삭제 합니다.

`Remove-Job`를 사용 하 여 모든 작업을 삭제 하거나 선택한 작업을 삭제할 수 있습니다. 작업은 **이름** , **ID** , **인스턴스 id** , **명령** 또는 **상태로** 식별 됩니다. 또는 파이프라인에서로 작업 개체를 보낼 수 있습니다 `Remove-Job` . 매개 변수 또는 매개 변수 값이 없으면는 영향을 주지 `Remove-Job` 않습니다.

PowerShell 3.0부터는 `Remove-Job` 예약 된 작업 및 워크플로 작업과 같은 사용자 지정 작업 유형을 삭제할 수 있습니다. 예를 들어는 예약 된 작업 `Remove-Job` , 디스크에 있는 예약 된 작업의 모든 인스턴스 및 모든 트리거된 작업 인스턴스의 결과를 삭제 합니다.

실행 중인 작업을 삭제 하려고 하면이 `Remove-Job` 실패 합니다. Cmdlet을 사용 `Stop-Job` 하 여 실행 중인 작업을 중지 합니다. 또는 `Remove-Job` **Force** 매개 변수와 함께를 사용 하 여 실행 중인 작업을 삭제 합니다.

백그라운드 작업을 삭제 하거나 PowerShell 세션을 닫을 때까지 작업이 전역 작업 캐시에 남아 있습니다.

## 예제

### 예제 1: 이름을 사용 하 여 작업 삭제

이 예제에서는 변수와 파이프라인을 사용 하 여 이름을 기준으로 작업을 삭제 합니다.

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

`Get-Job`**Name** 매개 변수를 사용 하 여 **batchjob** 작업을 지정 합니다. 작업 개체는 변수에 저장 됩니다 `$batch` . 의 개체는 `$batch` 파이프라인에서로 전송 됩니다 `Remove-Job` .

대신 **작업** 매개 변수 (예:)를 사용 `Remove-Job -Job $batch` 합니다.

### 예 2: 세션의 모든 작업 삭제

이 예에서는 현재 PowerShell 세션의 모든 작업을 삭제 합니다.

```powershell
Get-job | Remove-Job
```

`Get-Job` 현재 PowerShell 세션의 모든 작업을 가져옵니다. 작업 개체는 파이프라인에서로 전송 됩니다 `Remove-Job` .

### 예 3: NotStarted 작업 삭제

이 예에서는 현재 PowerShell 세션에서 아직 시작 되지 않은 모든 작업을 삭제 합니다.

```powershell
Remove-Job -State NotStarted
```

`Remove-Job`**State** 매개 변수를 사용 하 여 작업 상태를 지정 합니다.

### 예제 4: 친숙 한 이름을 사용 하 여 작업 삭제

이 예에서는를 실행 하는 작업을 포함 하 여 이름이 * batch * *로 끝나는 현재 세션에서 모든 작업을 삭제 합니다.

```powershell
Remove-Job -Name *batch -Force
```

`Remove-Job`**name** 매개 변수를 사용 하 여 작업 이름 패턴을 지정 합니다. 패턴에는 `*` **batch** 로 끝나는 모든 작업 이름을 찾기 위한 별표 () 와일드 카드가 포함 되어 있습니다. **Force** 매개 변수는를 실행 하는 작업을 삭제 합니다.

### 예 5: Invoke-Command 여 만든 작업 삭제

이 예에서는를 사용 하 여 원격 컴퓨터에서 시작 된 작업을 `Invoke-Command` **AsJob** 매개 변수와 함께 제거 합니다.

이 예제에서는 **AsJob** 매개 변수를 사용 하기 때문에 작업 개체는 로컬 컴퓨터에 만들어집니다.
그러나이 작업은 원격 컴퓨터에서 실행 됩니다. 따라서 로컬 명령을 사용하여 작업을 관리합니다.

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

`Invoke-Command`**Server01** 컴퓨터에서 작업을 실행 합니다. **AsJob** 매개 변수는 **ScriptBlock** 을 백그라운드 작업으로 실행 합니다. 작업 개체는 변수에 저장 됩니다 `$job` . `$job`변수 개체는 파이프라인에서로 전송 됩니다 `Remove-Job` .

### 예 6: Invoke-Command 및 Start-Job에서 만든 작업 삭제

이 예제에서는를 실행 하 여를 실행 하는 원격 컴퓨터에서 작업을 제거 하는 방법을 보여 줍니다 `Invoke-Command` `Start-Job` . 작업 개체는 원격 컴퓨터에서 만들어지며 원격 명령은 작업을 관리 하는 데 사용 됩니다. 원격 명령을 실행 하는 경우 영구 연결이 필요 `Start-Job` 합니다.

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

`New-PSSession`**Server01** 컴퓨터에 대 한 **PSSession** (영구 연결)을 만듭니다. 연결은 변수에 저장 됩니다 `$S` .

`Invoke-Command` 에 저장 된 세션에 연결 `$S` 합니다. **ScriptBlock** 은 `Start-Job` 를 사용 하 여 원격 작업을 시작 합니다. 작업은 명령을 실행 하 `Get-Process` 고 **name** 매개 변수를 사용 하 여 친숙 한 작업 이름 **myjob** 을 지정 합니다.

`Invoke-Command` 세션을 사용 하 `$S` 고를 실행 `Remove-Job` 합니다. **Name** 매개 변수는 **myjob** 이라는 작업을 삭제 하도록 지정 합니다.

### 예 7: InstanceId를 사용 하 여 작업 삭제

이 예에서는 **InstanceId** 를 기준으로 작업을 제거 합니다.

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` 백그라운드 작업을 시작 하 고 작업 개체가 변수에 저장 됩니다 `$job` .

의 개체는 `$job` 파이프라인에서로 전송 됩니다 `Format-List` . **Property** 매개 변수는 별표 ()를 사용 하 여 `*` 모든 개체의 속성이 목록에 표시 되도록 지정 합니다.

`Remove-Job`**InstanceId** 매개 변수를 사용 하 여 삭제할 작업을 지정 합니다.

## PARAMETERS

### -Command

지정한 단어가 명령에 포함된 작업을 삭제합니다. 쉼표로 구분 된 배열을 입력할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

을 실행 하기 전에 확인 메시지를 표시 `Remove-Job` 합니다.

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

### -Filter

연결 된 해시 테이블에 설정 된 모든 조건을 충족 하는 작업을 삭제 합니다. 키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.

이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다. 을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다 `Start-Job` .

이 매개 변수는 PowerShell 3.0에서 도입되었습니다.

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

작업 상태를 **실행** 하는 경우에도 작업을 삭제 합니다. **Force** 매개 변수가 지정 되지 않은 경우는 `Remove-Job` 실행 중인 작업을 삭제 하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, NameParameterSet, InstanceIdParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

지정 된 **Id** 를 가진 백그라운드 작업을 삭제 합니다. 쉼표로 구분 된 배열을 입력할 수 있습니다. 작업 **Id** 는 현재 세션 내에서 작업을 식별 하는 고유한 정수입니다.

작업 **Id** 를 찾으려면 `Get-Job` 매개 변수 없이를 사용 합니다.

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

지정 된 **InstanceId** 를 사용 하 여 작업을 삭제 합니다. 쉼표로 구분 된 배열을 입력할 수 있습니다. **InstanceId** 는 작업을 식별 하는 고유 GUID입니다.

작업의 **InstanceId** 를 찾으려면를 사용 `Get-Job` 합니다.

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

삭제할 작업을 지정합니다. 작업이 포함된 변수 또는 작업을 가져오는 명령을 입력합니다. 쉼표로 구분 된 배열을 입력할 수 있습니다.

파이프라인에서 작업 개체를로 보낼 수 있습니다 `Remove-Job` .

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

지정한 이름을 가진 작업만 삭제 합니다. 와일드카드가 지원됩니다. 쉼표로 구분 된 배열을 입력할 수 있습니다.

작업 이름은 PowerShell 세션 내 에서도 고유 하지 않을 수 있습니다. 이름을 기준으로 파일을 삭제 하는 경우 **WhatIf** 및 **Confirm** 매개 변수를 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -상태

지정 된 상태의 작업만 삭제 합니다. **실행** 상태의 작업을 삭제 하려면 **Force** 매개 변수를 사용 합니다.

허용 되는 값:

- AtBreakpoint
- 차단
- 완료됨
- 연결 끊김
- 실패
- NotStarted
- 실행 중
- 중지됨
- 중지 중
- 일시 중단
- Suspending

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Remove-Job` . Cmdlet이 실행 되지 않습니다.

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

### System.object.

파이프라인에서 작업 개체를로 보낼 수 있습니다 `Remove-Job` .

## 출력

### 없음

`Remove-Job` 는 출력을 생성 하지 않습니다.

## 참고

PowerShell 작업에서 새 프로세스를 만듭니다. 작업이 완료 되 면 프로세스가 종료 됩니다. `Remove-Job`을 실행 하면 작업의 상태가 제거 됩니다.

작업이 완료 되기 전에 중지 되 고 해당 프로세스가 종료 되지 않으면 프로세스가 강제로 종료 됩니다.

## 관련 링크

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
