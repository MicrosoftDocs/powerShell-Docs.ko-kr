---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 85cbfad2a4866bf18e69fb99afb8698e233c4c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212777"
---
# Resume-Job

## 개요
일시 중단된 작업을 다시 시작합니다.

## SYNTAX

### SessionIdParameterSet (기본값)

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Resume-job** cmdlet은 Suspend-Job cmdlet 또는 about_Suspend 워크플로 작업을 사용 하는 등 일시 중단 된 워크플로 작업을 다시 시작 합니다.
워크플로 작업이 다시 시작 되 면 작업 엔진은 검사점과 같은 저장 된 리소스에서 상태, 메타 데이터 및 출력을 다시 만듭니다.
상태 또는 데이터의 손실 없이 작업이 다시 시작 됩니다.
작업 상태가 **Suspended** 에서 **Running** 으로 변경됩니다.

**Resume-job** 매개 변수를 사용 하 여 작업을 **다시 시작** 하기 위해 이름, id, 인스턴스 ID 또는 작업 개체 (예: Get-Job cmdlet에서 반환 된 개체)를 파이프로 선택 합니다.
속성 필터를 사용하여 다시 시작할 작업을 선택할 수도 있습니다.

기본적으로 **Resume-Job** 은 일부 작업이 다시 시작되지 않은 경우에도 즉시 반환됩니다.
지정한 모든 작업이 다시 시작될 때까지 명령 프롬프트를 표시하지 않으려면 *Wait* 매개 변수를 사용합니다.

**Resume-Job** cmdlet은 워크플로 작업과 같은 사용자 지정 작업 유형에서만 작동하고
Start-Job cmdlet을 사용 하 여 시작한 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.
지원되지 않는 유형의 작업을 제출할 경우 **Resume-Job** 은 종료되는 오류를 생성하고 실행을 중지합니다.

워크플로 작업을 식별하려면 작업의 **PSJobTypeName** 속성에서 **PSWorkflowJob** 값을 찾습니다.
특정 사용자 지정 작업 유형이 **Resume-job** cmdlet을 지원 하는지 여부를 확인 하려면 사용자 지정 작업 유형에 대 한 도움말 항목을 참조 하세요.

사용자 지정 작업 유형에 대해 Job cmdlet을 사용 하기 전에 Import-Module cmdlet을 사용 하거나 모듈에서 cmdlet을 가져오거나 사용 하 여 사용자 지정 작업 유형을 지 원하는 모듈을 가져옵니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: ID로 작업 다시 시작

```
The first command uses the **Get-Job** cmdlet to get the job. The output shows that the job is a suspended workflow job.
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

The second command uses the *Id* parameter of the **Resume-Job** cmdlet to resume the job with an *Id* value of 4.
PS C:\> Resume-Job -Id 4
```

이 예제의 명령은 작업이 일시 중단된 워크플로 작업인지 확인한 다음 작업을 다시 시작합니다.

### 예 2: 이름으로 작업 다시 시작

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

이 명령은 *Name* 매개 변수를 사용하여 로컬 컴퓨터에서 여러 개의 워크플로 작업을 다시 시작합니다.

### 예제 3: 사용자 지정 속성 값 사용

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

이 명령은 사용자 지정 속성 값을 사용하여 다시 시작할 워크플로 작업을 식별합니다.
*Filter* 매개 변수를 사용하여 **CustomID** 속성으로 워크플로 작업을 식별합니다.
또한 *State* 매개 변수를 사용하여 다시 시작하기 전에 워크플로 작업이 일시 중단되었는지 확인합니다.

### 예제 4: 원격 컴퓨터에서 모든 일시 중단 된 작업 다시 시작

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

이 명령은 Srv01 원격 컴퓨터에서 모든 일시 중단된 작업을 다시 시작합니다.

이 명령은 Invoke-Command cmdlet을 사용 하 여 Srv01 컴퓨터에서 명령을 실행 합니다.
원격 명령은 **get-help** Cmdlet의 *State* 매개 변수를 사용 하 여 컴퓨터에 있는 모든 일시 중단 된 작업을 가져옵니다.
파이프라인 연산자(|)가 일시 중단된 작업을 **Resume-Job** cmdlet으로 보내면 이 cmdlet이 다시 시작합니다.

### 예 5: 작업이 다시 시작 될 때까지 대기

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

이 명령은 *Wait* 매개 변수를 사용 하 여 지정 된 모든 작업이 다시 시작 된 후에만 **다시 Resume 작업** 을 반환 합니다.
*Wait* 매개 변수는 작업이 다시 시작된 후 스크립트가 계속된다고 가정하는 스크립트에서 특히 유용합니다.

### 예제 6: 자신을 일시 중단 하는 워크플로 다시 시작

```
This code sample shows the **Suspend-Workflow** activity in a workflow.
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

The following command runs the Test-Suspend workflow on the Server01 computer.When you run the workflow, the workflow runs the Get-Date activity and stores the result in the $a variable. Then it runs the Suspend-Workflow activity. In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.  Suspend-Workflow returns a workflow job object even if the workflow is not explicitly run as a job.
PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

The following command resumes the Test-Suspend workflow in Job8. It uses the *Wait* parameter to hold the command prompt until the job is resumed.
PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command

--     ----            -------------   -----         -----------     --------             -------

8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

This command uses the **Receive-Job** cmdlet to get the results of the Test-Suspend workflow. The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the $a variable before the workflow was suspended.
PS C:\> Receive-Job -Name Job8
        Days              : 0
        Hours             : 0
        Minutes           : 0
        Seconds           : 19
        Milliseconds      : 823
        Ticks             : 198230041
        TotalDays         : 0.000229432917824074
        TotalHours        : 0.00550639002777778
        TotalMinutes      : 0.330383401666667
        TotalSeconds      : 19.8230041
        TotalMilliseconds : 19823.0041
        PSComputerName    : Server01
```

**Resume-job** cmdlet을 사용 하면 **일시 중단 워크플로** 작업을 사용 하 여 일시 중단 된 워크플로 작업을 다시 시작할 수 있습니다.
이 활동은 워크플로 내에서 워크플로를 일시 중단합니다.
이는 워크플로에서만 유효합니다.

Suspend-Workflow에 대한 자세한 내용은 about_Suspend-Workflow를 참조하세요.

## PARAMETERS

### -Filter
조건에 대 한 해시 테이블을 지정 합니다.
이 cmdlet은 해시 테이블의 모든 조건을 충족 하는 작업을 다시 시작 합니다.
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

### -Id
이 cmdlet이 다시 시작 하는 작업의 Id 배열을 지정 합니다.

ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.
인스턴스 ID 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.
하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.
작업 ID를 찾으려면 **작업** 을 실행 합니다.

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
이 cmdlet이 다시 시작 하는 작업의 인스턴스 Id 배열을 지정 합니다.
기본값은 모든 작업입니다.

인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.
작업의 인스턴스 ID를 찾으려면 **작업** 을 실행 합니다.

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
다시 시작할 작업을 지정합니다.
작업이 포함된 변수 또는 작업을 가져오는 명령을 입력합니다.
작업을 **Resume-Job** cmdlet으로 파이프할 수도 있습니다.

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
이 cmdlet이 다시 시작 하는 작업의 이름 배열을 지정 합니다.
작업 이름을 하나 이상 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

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
다시 시작할 작업의 상태를 지정 합니다.
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

이 cmdlet은 **일시 중단** 상태의 작업만 다시 시작 합니다.

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
모든 작업 결과가 다시 시작 될 때까지이 cmdlet이 명령 프롬프트를 표시 하지 않음을 나타냅니다.
기본적으로이 cmdlet은 사용 가능한 결과를 즉시 반환 합니다.

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
**작업 다시 시작** 이 지원 되지 않는 유형의 작업을 가져오는 경우 종료 오류를 반환 합니다.

## 출력

### 없음, 시스템 관리. 작업
이 cmdlet은 *PassThru* 매개 변수를 사용 하는 경우 다시 시작 하려고 하는 작업을 반환 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* **다시 시작 작업** 은 일시 중단 된 작업만 다시 시작할 수 있습니다. 다른 상태의 작업을 제출할 경우 **Resume-Job** 은 작업에 대해 다시 시작 작업을 실행하지만 작업을 다시 시작할 수 없음을 알리는 경고를 생성합니다. 이 경고를 표시 하지 않으려면 SilentlyContinue의 값과 함께 *WarningAction* 일반 매개 변수를 사용 합니다.
* 작업이 워크플로 작업 ( **PSWorkflowJob** )과 같은 다시 시작을 지 원하는 형식이 아닌 경우 **Resume 작업** 은 종료 오류를 반환 합니다.
* 일시 중단된 작업을 저장하는 메커니즘과 위치는 작업 유형에 따라 달라질 수 있습니다. 예를 들어 일시 중단된 워크플로 작업은 기본적으로 플랫 파일 저장소에 저장되지만 SQL 데이터베이스에 저장할 수도 있습니다.
* 작업을 다시 시작하면 작업 상태가 **Suspended** 에서 **Running** 으로 변경됩니다. 이 cmdlet에 의해 다시 시작 된 작업을 포함 하 여 실행 중인 작업을 찾으려면 작업 ( **job)** Cmdlet의 *state* 매개 변수를 사용 하 여 **실행** 상태의 작업을 가져옵니다.
* 일부 작업 유형에는 Windows PowerShell에서 작업을 일시 중단할 수 없게 하는 옵션 또는 속성이 있습니다. 작업을 일시 중단 하려는 시도가 실패 한 경우 작업 옵션 및 속성이 일시 중단을 허용 하는지 확인 합니다.

## 관련 링크

[Get-Job](Get-Job.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
