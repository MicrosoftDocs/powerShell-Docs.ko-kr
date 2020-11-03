---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 6ab50342e963832d89b3dfc4128a22fc16405926
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212722"
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
**작업 일시 중단** cmdlet은 워크플로 작업을 일시 중단 합니다.
일시 중단은 워크플로 작업을 일시적으로 중단 하거나 일시 중지 하는 것을 의미 합니다.
이 cmdlet을 사용하면 워크플로를 실행하는 사용자가 워크플로를 일시 중단할 수 있습니다.
워크플로를 https://go.microsoft.com/fwlink/?LinkId=267141 일시 중단 하는 워크플로의 명령 인 일시 중단 워크플로 작업을 보완 합니다.

**Suspend-Job** cmdlet은 워크플로 작업에서만 작동하고
Start-Job cmdlet을 사용 하 여 시작한 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.

워크플로 작업을 식별 하려면 작업의 **PSJobTypeName** 속성에서 PSWorkflowJob 값을 찾습니다.
특정 사용자 지정 작업 유형이 **Suspend-Job** cmdlet을 지원하는지 확인하려면 사용자 지정 작업 유형에 대한 도움말 항목을 참조하세요.

워크플로 작업을 일시 중단하면 워크플로 작업이 다음 검사점까지 실행된 다음 일시 중단되고 워크플로 작업 개체를 즉시 반환합니다.
작업을 가져오기 전에 일시 중단이 완료 될 때까지 기다리려면 **일시 중단-작업** 또는 Wait-Job Cmdlet의 *wait* 매개 변수를 사용 합니다.
워크플로 작업이 일시 중단 되 면 작업의 **State** 속성 값이 일시 중단 됩니다.

정확한 일시 중단은 검사점을 사용합니다.
상태 또는 데이터의 손실 없이 워크플로 작업을 다시 시작할 수 있도록 현재 작업 상태, 메타 데이터 및 출력이 검사점에 저장 됩니다.
워크플로 작업에 검사점이 없으면 제대로 일시 중단할 수 없습니다.
실행 중인 워크플로에 검사점을 추가하려면 *PSPersist* 워크플로 일반 매개 변수를 사용합니다.
*Force* 매개 변수를 사용 하 여 워크플로 작업을 즉시 일시 중단 하 고 검사점이 없는 워크플로 작업을 일시 중단할 수 있지만 상태 및 데이터가 손실 될 수 있습니다.

워크플로 작업 ( **PSWorkflowJob** )과 같은 사용자 지정 작업 유형에 대해 Job cmdlet을 사용 하기 전에 Import-Module cmdlet을 사용 하거나 모듈에서 cmdlet을 사용 하거나 사용 하 여 사용자 지정 작업 유형을 지 원하는 모듈을 가져옵니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 이름을 기준으로 워크플로 작업 일시 중단

```
The first command creates the Get-SystemLog workflow. The workflow uses the CheckPoint-Workflow activity to define a checkpoint in the workflow.
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

The second command uses the *AsJob* parameter that is common to all workflows to run the Get-SystemLog workflow as a background job. The command uses the *JobName* workflow common parameter to specify a friendly name for the workflow job.
PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

The third command uses the **Get-Job** cmdlet to get the Get-SystemLogJob workflow job. The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.
PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

The fourth command uses the **Suspend-Job** cmdlet to suspend the Get-SystemLogJob job. The job runs to the checkpoint and then suspends.
PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```

이 예제에서는 워크플로 작업을 일시 중단하는 방법을 보여 줍니다.

### 예 2: 워크플로 작업 일시 중단 및 다시 시작

```
The first command suspends the LogWorkflowJob job.The command returns immediately. The output shows that the workflow job is still running, even though it is being suspended.
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

The second command uses the **Get-Job** cmdlet to get the LogWorkflowJob job. The output shows that the workflow job suspended successfully.
PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

The third command uses the **Get-Job** cmdlet to get the LogWorkflowJob job and the Resume-Job cmdlet to resume it. The output shows that the workflow job resumed successfully and is now running.
PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```

이 예제에서는 워크플로 작업을 일시 중단하고 다시 시작하는 방법을 보여 줍니다.

### 예 3: 원격 컴퓨터에서 워크플로 작업 일시 중단

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

이 명령은 Invoke-Command cmdlet을 사용 하 여 Srv01 원격 컴퓨터에서 워크플로 작업을 일시 중단 합니다.
*Filter* 매개 변수의 값은 CustomID 값을 지정 하는 해시 테이블입니다.
이 **CustomID** 는 작업 메타데이터( **PSPrivateMetadata** )입니다.

### 예제 4: 워크플로 작업이 일시 중단 될 때까지 대기

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

이 명령은 VersionCheck 워크플로 작업을 일시 중단합니다.
*Wait* 매개 변수를 사용하여 워크플로 작업이 일시 중단될 때까지 대기합니다.
워크플로 작업이 다음 검사점까지 실행 되 고 일시 중단 되 면 명령이 완료 되 고 작업 개체를 반환 합니다.

### 예 5: 워크플로 작업을 강제로 일시 중단

```
PS C:\> Suspend-Job Maintenance -Force
```

이 명령은 Maintenance 워크플로 작업을 강제로 일시 중단합니다.
유지 관리 작업에 검사점이 없습니다.
이 파일은 올바르게 일시 중단 될 수 없으며 제대로 다시 시작 되지 않을 수 있습니다.

## PARAMETERS

### -Filter
조건에 대 한 해시 테이블을 지정 합니다.
이 cmdlet은 모든 조건을 충족 하는 작업을 일시 중단 합니다.
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
워크플로 작업을 즉시 일시 중단합니다.
이 작업으로 인해 상태 및 데이터가 손실 될 수 있습니다.

기본적으로 **Suspend-Job** 은 워크플로 작업이 다음 검사점까지 실행되도록 한 다음 일시 중단합니다.
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

ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.
인스턴스 ID 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.
하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.
작업 ID를 찾으려면 Get-Job cmdlet을 사용 합니다.

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
이 cmdlet이 일시 중단 하는 작업의 인스턴스 Id를 지정 합니다.
기본값은 모든 작업입니다.

인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.
작업의 인스턴스 ID를 찾으려면 **Get-Job** 을 사용합니다.

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
이 cmdlet이 중지 하는 워크플로 작업을 지정 합니다.
워크플로 작업이 포함된 변수 또는 워크플로 작업을 가져오는 명령을 입력합니다.
워크플로 작업을 **Suspend-Job** cmdlet으로 파이프할 수도 있습니다.

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
이 cmdlet이 일시 중단 하는 작업의 이름을 지정 합니다.
워크플로 작업 이름을 하나 이상 입력합니다.
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
작업 상태를 지정 합니다.
이 cmdlet은 지정 된 상태의 작업만 중지 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

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

**일시 중단-작업** 은 **실행 중** 상태의 워크플로 작업만 일시 중단 합니다.

작업 상태에 대 한 자세한 내용은 MSDN library에서 [JobState 열거](https://msdn.microsoft.com/library/system.management.automation.jobstate) 를 참조 하세요.

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
이 cmdlet은 워크플로 작업이 일시 중단 상태가 될 때까지 명령 프롬프트를 표시 하지 않음을 나타냅니다.
기본적으로 **일시 중단 작업** 은 워크플로 작업이 아직 일시 중단 된 상태가 아닌 경우에도 즉시 반환 됩니다.

*Wait* 매개 변수는 **작업 일시 중단** 명령을 **대기 작업** cmdlet으로 파이프 하는 것과 같습니다.

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

### System.object.
모든 유형의 작업을이 cmdlet으로 파이프 할 수 있습니다.
그러나 **일시 중단 작업** 은 지원 되지 않는 유형의 작업을 가져오는 경우 종료 오류를 반환 합니다.

## 출력

### System.object.
이 cmdlet은 일시 중단 된 작업을 반환 합니다.

## 참고

* 일시 중단된 작업을 저장하는 메커니즘과 위치는 작업 유형에 따라 달라질 수 있습니다. 예를 들어 일시 중단된 워크플로 작업은 기본적으로 플랫 파일 저장소에 저장되지만 데이터베이스에 저장할 수도 있습니다.
* 실행 중 상태가 아닌 워크플로 작업을 제출 하는 경우 **일시 중단 작업** 은 경고 메시지를 표시 합니다. 이 경고를 표시 하지 않으려면 SilentlyContinue의 값과 함께 *WarningAction* 일반 매개 변수를 사용 합니다.

  작업이 일시 중단을 지 원하는 형식이 아닌 경우 **일시 중단 작업** 은 종료 오류를 반환 합니다.

* 이 cmdlet에 의해 일시 중단 된 워크플로를 포함 하 여 일시 중단 된 워크플로 작업을 찾으려면 **작업** Cmdlet의 *State* 매개 변수를 사용 하 여 일시 중단 된 상태의 워크플로 작업을 가져옵니다.
* 일부 작업 유형에는 Windows PowerShell에서 작업을 일시 중단할 수 없게 하는 옵션 또는 속성이 있습니다. 작업을 일시 중단 하려는 시도가 실패 한 경우 작업 옵션 및 속성이 일시 중단을 허용 하는지 확인 합니다.

## 관련 링크

[Get-Job](Get-Job.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
