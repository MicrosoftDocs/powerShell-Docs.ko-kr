---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 9b18782fae77fa0776aa2cfaa39b74a2292099d9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388470"
---
# Suspend-Job

## 개요
워크플로 작업을 일시적으로 중지합니다.

## SYNTAX

### SessionIdParameterSet (기본값)

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Suspend-Job`Cmdlet은 워크플로 작업을 일시 중단 합니다. 일시 중단은 워크플로 작업을 일시적으로 중단 하거나 일시 중지 하는 것을 의미 합니다. 이 cmdlet을 사용하면 워크플로를 실행하는 사용자가 워크플로를 일시 중단할 수 있습니다. 워크플로를 https://go.microsoft.com/fwlink/?LinkId=267141 일시 중단 하는 워크플로의 명령 인 일시 중단 워크플로 작업을 보완 합니다.

`Suspend-Job`Cmdlet은 워크플로 작업 에서만 작동 합니다. Cmdlet을 사용 하 여 시작한 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다 `Start-Job` .

워크플로 작업을 식별 하려면 작업의 **PSJobTypeName** 속성에서 PSWorkflowJob 값을 찾습니다. 특정 사용자 지정 작업 유형이 cmdlet을 지원 하는지 여부를 확인 하려면 `Suspend-Job` 사용자 지정 작업 유형에 대 한 도움말 항목을 참조 하세요.

워크플로 작업을 일시 중단하면 워크플로 작업이 다음 검사점까지 실행된 다음 일시 중단되고 워크플로 작업 개체를 즉시 반환합니다. 작업을 가져오기 전에 일시 중단이 완료 될 때까지 기다리려면의 **wait** 매개 변수 또는 cmdlet을 사용 합니다 `Suspend-Job` `Wait-Job` . 워크플로 작업이 일시 중단 되 면 작업의 **State** 속성 값이 일시 중단 됩니다.

정확한 일시 중단은 검사점을 사용합니다. 상태 또는 데이터의 손실 없이 워크플로 작업을 다시 시작할 수 있도록 현재 작업 상태, 메타 데이터 및 출력이 검사점에 저장 됩니다. 워크플로 작업에 검사점이 없으면 제대로 일시 중단할 수 없습니다. 실행 중인 워크플로에 검사점을 추가하려면 **PSPersist** 워크플로 일반 매개 변수를 사용합니다. **Force** 매개 변수를 사용 하 여 워크플로 작업을 즉시 일시 중단 하 고 검사점이 없는 워크플로 작업을 일시 중단할 수 있지만 상태 및 데이터가 손실 될 수 있습니다.

워크플로 작업 ( **PSWorkflowJob** )과 같은 사용자 지정 작업 유형에 대해 Job cmdlet을 사용 하기 전에 cmdlet을 사용 하거나 `Import-Module` 모듈에서 cmdlet을 사용 하거나 사용 하 여 사용자 지정 작업 유형을 지 원하는 모듈을 가져옵니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 이름을 기준으로 워크플로 작업 일시 중단

이 예제에서는 워크플로 작업을 일시 중단하는 방법을 보여 줍니다.

첫 번째 명령은 워크플로를 만듭니다 `Get-SystemLog` . 워크플로는 활동을 사용 하 여 `CheckPoint-Workflow` 워크플로에서 검사점을 정의 합니다.

두 번째 명령은 모든 워크플로에 공통적으로 사용 되는 **AsJob** 매개 변수를 사용 하 여 `Get-SystemLog` 워크플로를 백그라운드 작업으로 실행 합니다. **JobName** 워크플로 일반 매개 변수를 사용하여 워크플로 작업의 이름을 지정합니다.

세 번째 명령은 cmdlet을 사용 하 여 `Get-Job` `Get-SystemLogJob` 워크플로 작업을 가져옵니다. 출력은 **PSJobTypeName** 속성의 값이 PSWorkflowJob 임을 보여 줍니다.

네 번째 명령은 cmdlet을 사용 하 여 `Suspend-Job` 작업을 일시 중단 합니다 `Get-SystemLogJob` . 작업이 검사점까지 실행된 다음 일시 중단됩니다.

```
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```


### 예 2: 워크플로 작업 일시 중단 및 다시 시작

이 예제에서는 워크플로 작업을 일시 중단하고 다시 시작하는 방법을 보여 줍니다.

첫 번째 명령은 LogWorkflowJob 작업을 일시 중단 합니다. 명령이 즉시 반환 됩니다. 출력은 워크플로 작업이 일시 중단 된 경우에도 여전히 실행 되 고 있음을 보여 줍니다.

두 번째 명령은 cmdlet을 사용 하 여 `Get-Job` LogWorkflowJob 작업을 가져옵니다. 출력은 워크플로 작업이 성공적으로 일시 중단되었음을 보여 줍니다.

세 번째 명령은 cmdlet을 사용 하 여 `Get-Job` LogWorkflowJob 작업을 가져온 다음 cmdlet을 사용 하 여 `Resume-Job` 다시 시작 합니다. 출력은 워크플로 작업이 성공적으로 다시 시작되었으며 현재 실행 중임을 보여 줍니다.

```
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```


### 예 3: 원격 컴퓨터에서 워크플로 작업 일시 중단

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

이 명령은 cmdlet을 사용 하 여 `Invoke-Command` Srv01 원격 컴퓨터에서 워크플로 작업을 일시 중단 합니다. **Filter** 매개 변수의 값은 CustomID 값을 지정 하는 해시 테이블입니다.
이 **CustomID** 는 작업 메타데이터( **PSPrivateMetadata** )입니다.

### 예제 4: 워크플로 작업이 일시 중단 될 때까지 대기

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

이 명령은 VersionCheck 워크플로 작업을 일시 중단합니다. **Wait** 매개 변수를 사용하여 워크플로 작업이 일시 중단될 때까지 대기합니다. 워크플로 작업이 다음 검사점까지 실행 되 고 일시 중단 되 면 명령이 완료 되 고 작업 개체를 반환 합니다.

### 예 5: 워크플로 작업을 강제로 일시 중단

```
PS C:\> Suspend-Job Maintenance -Force
```

이 명령은 Maintenance 워크플로 작업을 강제로 일시 중단합니다. 유지 관리 작업에 검사점이 없습니다. 이 파일은 올바르게 일시 중단 될 수 없으며 제대로 다시 시작 되지 않을 수 있습니다.

## PARAMETERS

### -Filter

조건에 대 한 해시 테이블을 지정 합니다. 이 cmdlet은 모든 조건을 충족 하는 작업을 일시 중단 합니다.
키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.

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

워크플로 작업을 즉시 일시 중단합니다. 이 작업으로 인해 상태 및 데이터가 손실 될 수 있습니다.

기본적으로에서는 `Suspend-Job` 워크플로 작업이 다음 검사점까지 실행 된 다음 일시 중단 될 수 있습니다.
이 매개 변수를 사용하여 검사점이 없는 워크플로 작업을 일시 중단할 수도 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

이 cmdlet이 일시 중단 하는 작업의 Id를 지정 합니다.

ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다. 인스턴스 ID 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다. 하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다. 작업 ID를 찾으려면 cmdlet을 사용 합니다 `Get-Job` .

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

이 cmdlet이 일시 중단 하는 작업의 인스턴스 Id를 지정 합니다. 기본값은 모든 작업입니다.

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

이 cmdlet이 중지 하는 워크플로 작업을 지정 합니다. 워크플로 작업이 포함된 변수 또는 워크플로 작업을 가져오는 명령을 입력합니다. 워크플로 작업을 cmdlet으로 파이프 할 수도 있습니다 `Suspend-Job` .

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

이 cmdlet이 일시 중단 하는 작업의 이름을 지정 합니다. 워크플로 작업 이름을 하나 이상 입력합니다.
와일드카드 문자가 지원됩니다.

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

`Suspend-Job`**실행** 상태의 워크플로 작업만 일시 중단 합니다.

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

### -Wait

이 cmdlet은 워크플로 작업이 일시 중단 상태가 될 때까지 명령 프롬프트를 표시 하지 않음을 나타냅니다. `Suspend-Job`워크플로 작업이 아직 일시 중단 된 상태가 아닌 경우에도 기본적으로는 즉시 반환 됩니다.

**Wait** 매개 변수는 `Suspend-Job` 명령을 cmdlet에 파이프 하는 것과 같습니다 `Wait-Job` .

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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

모든 유형의 작업을이 cmdlet으로 파이프 할 수 있습니다. 그러나에서 `Suspend-Job` 지원 되지 않는 형식의 작업을 가져오는 경우 종료 오류를 반환 합니다.

## 출력

### System.object.
이 cmdlet은 일시 중단 된 작업을 반환 합니다.

## 참고

- 일시 중단된 작업을 저장하는 메커니즘과 위치는 작업 유형에 따라 달라질 수 있습니다. 예를 들어 일시 중단된 워크플로 작업은 기본적으로 플랫 파일 저장소에 저장되지만 데이터베이스에 저장할 수도 있습니다.
- 실행 중 상태가 아닌 워크플로 작업을 제출 하는 경우에서 `Suspend-Job` 경고 메시지를 표시 합니다. 이 경고를 표시 하지 않으려면 SilentlyContinue의 값과 함께 **WarningAction** 일반 매개 변수를 사용 합니다.

  작업이 일시 중단을 지 원하는 형식이 아닌 경우는 `Suspend-Job` 종료 오류를 반환 합니다.

- 이 cmdlet에 의해 일시 중단 된 워크플로를 포함 하 여 일시 중단 된 워크플로 작업을 찾으려면 cmdlet의 **State** 매개 변수를 사용 `Get-Job` 하 여 일시 중단 된 상태의 워크플로 작업을 가져옵니다.
- 일부 작업 유형에는 Windows PowerShell에서 작업을 일시 중단할 수 없게 하는 옵션 또는 속성이 있습니다.
  작업을 일시 중단 하려는 시도가 실패 한 경우 작업 옵션 및 속성이 일시 중단을 허용 하는지 확인 합니다.

## 관련 링크

[Get-Job](Get-Job.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
