---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212033"
---
# Get-Job

## 개요
현재 세션에서 실행 중인 PowerShell 백그라운드 작업을 가져옵니다.

## SYNTAX

### SessionIdParameterSet (기본값)

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### NameParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### StateParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## 설명

**Get-Job** cmdlet은 현재 세션에서 시작된 백그라운드 작업을 나타내는 개체를 가져옵니다.
**작업 (job)** 을 사용 하 여 Start-Job cmdlet을 사용 하거나 Cmdlet의 *AsJob* 매개 변수를 사용 하 여 시작 된 작업을 가져올 수 있습니다.

매개 변수가 없는 경우에는 **Get job** 명령이 현재 세션의 모든 작업을 가져옵니다.
**Get-Job** 의 매개 변수를 사용하여 특정 작업을 가져올 수 있습니다.

**Get-Job** 에서 반환하는 작업 개체에는 작업에 대한 유용한 정보가 포함되지만 작업 결과는 포함되지 않습니다.
결과를 얻으려면 Receive-Job cmdlet을 사용 합니다.

Windows PowerShell 백그라운드 작업은 현재 세션과 상호 작용 하지 않고 백그라운드에서 실행 되는 명령입니다.
일반적으로 백그라운드 작업을 사용 하 여 완료 하는 데 오랜 시간이 걸리는 복잡 한 명령을 실행 합니다.
Windows PowerShell의 백그라운드 작업에 대한 자세한 내용은 about_Jobs를 참조하세요.

Windows PowerShell 3.0부터 **Get-Job** cmdlet은 워크플로 작업 및 예약된 작업의 인스턴스와 같은 사용자 지정 작업 유형도 가져옵니다.
작업의 작업 유형을 찾으려면 해당 작업의 **PSJobTypeName** 속성을 사용합니다.

**작업** 자가 사용자 지정 작업 유형을 가져올 수 있도록 하려면 Import-Module cmdlet을 사용 하거나 모듈에서 cmdlet을 사용 하 여 **작업** 을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다.
특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.

## 예제

### 예 1: 현재 세션에서 시작 된 모든 백그라운드 작업 가져오기

```
PS C:\> Get-Job
```

이 명령은 현재 세션에서 시작된 모든 백그라운드 작업을 가져옵니다.
다른 세션에서 만들어진 작업은 로컬 컴퓨터에서 실행되는 경우에도 포함되지 않습니다.

### 예 2: 인스턴스 ID를 사용 하 여 작업 중지

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

이들 명령은 작업의 인스턴스 ID를 가져온 다음 이 ID를 사용하여 작업을 중지하는 방법을 보여 줍니다.
고유하지 않은 작업의 이름과 달리 인스턴스 ID는 고유합니다.

### 예 3: 특정 명령이 포함 된 작업 가져오기

```
PS C:\> Get-Job -Command "*get-process*"
```

이 명령은 Get-Process 명령을 포함 하는 시스템의 작업을 가져옵니다.
이 명령은 *Get-Job* 의 **Command** 매개 변수를 사용하여 검색된 작업을 제한합니다.
이 명령은 와일드 카드 문자 (*)를 사용 하 여 명령 문자열의 임의 위치에 **Get Process** 명령을 포함 하는 작업을 가져옵니다.

### 예제 4: 파이프라인을 사용 하 여 특정 명령을 포함 하는 작업 가져오기

```
PS C:\> "*get-process*" | Get-Job
```

이전 예제의 명령과 마찬가지로이 명령은 시스템에서 **Get Process** 명령이 포함 된 작업을 가져옵니다.
이 명령은 파이프라인 연산자 (|)를 사용 하 여 문자열을 따옴표 안에 있는 **가져오기 작업** cmdlet으로 보냅니다.
이 명령은 이전 명령과 동일합니다.

### 예 5: 시작 되지 않은 작업 가져오기

```
PS C:\> Get-Job -State NotStarted
```

이 명령은 만들어졌지만 아직 시작되지 않은 작업만 가져옵니다.
여기에는 이후에 실행되도록 예약된 작업과 아직 예약되지 않은 작업이 포함됩니다.

### 예 6: 이름이 할당 되지 않은 작업 가져오기

```
PS C:\> Get-Job -Name Job*
```

이 명령은 작업으로 시작 하는 작업 이름이 있는 모든 작업을 가져옵니다.
작업 \<number\> 은 작업의 기본 이름 이므로이 명령은 명시적으로 할당 된 이름이 없는 모든 작업을 가져옵니다.

### 예 7: 작업 개체를 사용 하 여 명령에서 작업 표시

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

이 예제에서는 **Get-Job** 을 사용하여 작업 개체를 가져오는 방법을 보여 준 다음 작업 개체를 사용하여 명령에 작업을 나타내는 방법을 보여 줍니다.

### 예 8: 다른 방법으로 시작 된 작업을 포함 하 여 모든 작업 가져오기

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

이 예에서는 다른 방법을 사용 하 여 시작 된 경우에도 **작업** cmdlet이 현재 세션에서 시작 된 모든 작업을 가져올 수 있음을 보여 줍니다.

### 예 9: 실패 한 작업 조사

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
PS C:\> Get-Job | Format-List -Property *
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

이 명령은 작업이 실패 한 이유를 조사 하기 위해 **Get 작업** 에서 반환 하는 작업 개체를 사용 하는 방법을 보여 줍니다.
또한 각 작업의 하위 작업을 가져오는 방법을 보여 줍니다.

### 예 10: 필터링 된 결과 가져오기

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

이 예제에서는 *Filter* 매개 변수를 사용하여 워크플로 작업을 가져오는 방법을 보여 줍니다.
Windows PowerShell 3.0에서 도입된 *Filter* 매개 변수는 워크플로 작업 및 예약된 작업과 같은 사용자 지정 작업 유형에서만 유효합니다.

### 예 11: 자식 작업에 대 한 정보 가져오기

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
PS C:\> Get-Job -IncludeChildJob
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

이 예제에서는 *Get-Job* cmdlet의 *IncludeChildJob* 및 **ChildJobState** 매개 변수 사용 결과를 보여 줍니다.

## PARAMETERS

### -이후

지정된 날짜 및 시간 이후에 종료되어 완료된 작업을 가져옵니다.
Get-Date cmdlet에서 반환 된 것과 같은 **datetime** 개체 또는 **datetime** 개체 (예: 또는)로 변환할 수 있는 문자열을 입력 `Dec 1, 2012 2:00 AM` `11/06` 합니다.

이 매개 변수는 워크플로 작업 및 예약된 작업과 같이 **EndTime** 속성이 있는 사용자 지정 작업 유형에서만 적용됩니다.
**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.
이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -이전

지정된 날짜 및 시간 이전에 종료되어 완료된 작업을 가져옵니다.
**DateTime** 개체를 입력 합니다.

이 매개 변수는 워크플로 작업 및 예약된 작업과 같이 **EndTime** 속성이 있는 사용자 지정 작업 유형에서만 적용됩니다.
**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.
이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ChildJobState

지정된 상태가 있는 자식 개체만 가져옵니다.
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

기본적으로 **Get-Job** 은 자식 작업을 가져오지 않습니다.
*IncludeChildJob* 매개 변수를 사용 하 여 모든 자식 **작업을 가져옵니다** .
*ChildJobState* 매개 변수를 사용하는 경우 *IncludeChildJob* 매개 변수는 영향을 주지 않습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

명령 배열을 문자열로 지정 합니다.
이 cmdlet은 지정 된 명령을 포함 하는 작업을 가져옵니다.
기본값은 모든 작업입니다.
와일드 카드 문자를 사용 하 여 명령 패턴을 지정할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Filter

조건에 대 한 해시 테이블을 지정 합니다.
이 cmdlet은 모든 조건을 충족 하는 작업을 가져옵니다.
키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.

이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다.
**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.
이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.

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

### -HasMoreData

이 cmdlet이 지정 된 **HasMoreData** 속성 값을 가진 작업만 가져오는 지 여부를 나타냅니다.
**HasMoreData** 속성은 모든 작업 결과가 현재 세션에서 수신되었는지를 나타냅니다.
더 많은 결과를 포함 하는 작업을 가져오려면 $True 값을 지정 합니다.
더 이상 결과가 없는 작업을 가져오려면 $False 값을 지정 합니다.

작업의 결과를 가져오려면 Receive-Job cmdlet을 사용 합니다.

**수신 작업** cmdlet을 사용 하면 반환 된 결과를 메모리 내 세션 관련 저장소에서 삭제 합니다.
작업의 모든 결과를 현재 세션에서 반환 하는 경우 작업의 **HasMoreData** 속성 값을 $False)로 설정 하 여 현재 세션에서 작업에 대 한 결과가 더 이상 없음을 나타낼 수 있습니다.
*Receive-Job* 의 **Keep** 매개 변수를 사용하여 **Receive-Job** 에서 결과를 삭제하고 **HasMoreData** 속성의 값을 변경할 수 없도록 합니다.
자세한 내용을 보려면 `Get-Help Receive-Job`를 입력하십시오.

**HasMoreData** 속성은 현재 세션에만 적용됩니다.
작업 결과를 디스크에 저장 하는 예약 된 작업 유형과 같이 사용자 지정 작업 유형에 대 한 결과가 세션 외부에 저장 된 경우 **HasMoreData** 의 값이 $False 경우에도 다른 세션에서 **Receive-job** cmdlet을 사용 하 여 작업 결과를 다시 가져올 수 있습니다.
자세한 내용은 사용자 지정 작업 유형에 대한 도움말 항목을 참조하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

이 cmdlet이 가져오는 작업의 Id 배열을 지정 합니다.

ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.
인스턴스 ID 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.
하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.
작업의 ID를 찾으려면 `Get-Job` 매개 변수 없이를 입력 합니다.

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeChildJob

부모 작업 외에도이 cmdlet이 자식 작업을 반환 함을 나타냅니다.

이 매개 변수는 워크플로 작업을 조사 하는 데 특히 유용 합니다 .이 경우 실패 이유는 자식 작업의 속성에 저장 되므로 작업에서 컨테이너 부모 작업 및 작업 실패 **를 반환 합니다** .

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

이 cmdlet이 가져오는 작업의 인스턴스 Id 배열을 지정 합니다.
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

### -Name

이 cmdlet이 가져오는 작업의 인스턴스 이름을 지정 합니다.
작업 이름을 입력하거나 와일드카드 문자를 사용하여 작업 이름 패턴을 입력하세요.
기본적으로 **Get-Job** 은 현재 세션의 모든 작업을 가져옵니다.

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

### -최신

가져올 작업 수를 지정 합니다.
이 cmdlet은 가장 최근에 종료 된 작업을 가져옵니다.

*Newest* 매개 변수는 최신 작업을 종료 시간 순서대로 정렬하거나 반환하지 않습니다.
출력을 정렬 하려면 Sort-Object cmdlet을 사용 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -상태

작업 상태를 지정 합니다.
이 cmdlet은 지정 된 상태의 작업만 가져옵니다.
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

기본적으로 **Get-Job** 은 현재 세션의 모든 작업을 가져옵니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.web. Remorererea 작업

이 cmdlet은 세션의 작업을 나타내는 개체를 반환 합니다.

## 참고

* 작업의 **PSJobTypeName** 속성은 작업의 작업 유형을 나타냅니다. 속성 값은 작업 유형 작성자에 따라 결정됩니다. 다음 목록에서는 일반적인 작업 유형을 보여 줍니다.

  - **BackgroundJob** .
**시작-작업** 을 사용 하 여 로컬 작업을 시작 했습니다.

  - **Remotejob** .
Invoke-Command cmdlet의 *AsJob* 매개 변수를 사용 하 여 **PSSession** 에서 작업을 시작 했습니다.

  - **PSWorkflowJob** .
워크플로의 *AsJob* 일반 매개 변수를 사용하여 시작된 작업입니다.

## 관련 링크

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)

[about_Jobs](About/about_Jobs.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md)
