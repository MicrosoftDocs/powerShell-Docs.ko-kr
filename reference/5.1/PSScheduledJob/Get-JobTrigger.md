---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-JobTrigger
ms.openlocfilehash: 7a75a5a7e6875ed88fd31ea0f385c19f1991f8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213441"
---
# Get-JobTrigger

## 개요
예약된 작업의 작업 트리거를 가져옵니다.

## SYNTAX

### JobDefinition (기본값)

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## 설명
**Get-JobTrigger** cmdlet은 예약된 작업의 작업 트리거를 가져옵니다.
이 명령을 사용하여 작업 트리거를 검사하거나 작업 트리거를 다른 cmdlet으로 파이프할 수 있습니다.

작업 트리거는 예약 된 작업을 시작 하기 위한 되풀이 일정 또는 조건을 정의 합니다.
작업 트리거는 독립적으로 디스크에 저장되지 않고 예약된 작업의 일부입니다.
작업 트리거를 가져오려면 트리거가 시작하는 예약된 작업을 지정합니다.

**Get-JobTrigger** cmdlet의 매개 변수를 사용하여 예약된 작업을 식별할 수 있습니다.
이름 또는 id 번호를 기준으로 예약 된 작업을 식별 하거나, Get-ScheduledJob cmdlet에서 반환 되 **는 개체 (** 예: cmdlet에서 반환 하는 개체)를 입력 하거나 파이프 하 여 **가져올** 수 있습니다.

**JobTrigger** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 예약 된 작업 이름으로 작업 트리거 가져오기

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

이 명령은 **Get JobTrigger** 의 *Name* 매개 변수를 사용 하 여 backupjob 예약 된 작업의 작업 트리거를 가져옵니다.

### 예제 2: ID로 작업 트리거 가져오기

```
The first command uses the Get-ScheduledJob cmdlet to display the scheduled jobs on the local computer. The display includes the IDs of the scheduled jobs.
PS C:\> Get-ScheduledJob
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProjects {1}             \\Server\Share\Archive-Projects.ps1      True
2          Backup          {1,2}           \\Server\Share\Run-Backup.ps1            True
3          Test-HelpFiles  {1}             \\Server\Share\Test-HelpFiles.ps1        True
4          TestJob         {}              \\Server\Share\Run-AllTests.ps1          True

The second command uses the **Get-JobTrigger** cmdlet to get the job trigger for the Test-HelpFiles job (ID = 3)
PS C:\> Get-JobTrigger -ID 3
```

이 예에서는 **Get JobTrigger** 의 *ID* 매개 변수를 사용 하 여 예약 된 작업의 작업 트리거를 가져옵니다.

### 예 3: 작업을 파이프 하 여 작업 트리거 가져오기

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

이 명령은 이름에 백업이 나 보관 된 모든 작업의 작업 트리거를 가져옵니다.

### 예 4: 원격 컴퓨터에서 작업의 작업 트리거 가져오기

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

이 명령은 원격 컴퓨터에 있는 예약된 작업의 작업 트리거 2개 중 하나를 가져옵니다.

이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.
Get-ScheduledJob cmdlet을 사용 하 여 Backup 예약 된 작업을 가져옵니다 .이 작업은 **Get JobTrigger** cmdlet에 파이프 합니다.
*TriggerID* 매개 변수를 사용 하 여 두 번째 트리거를 가져옵니다.

### 예 5: 모든 작업 트리거 가져오기

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

이 명령은 로컬 컴퓨터에 있는 모든 예약된 작업의 모든 작업 트리거를 가져옵니다.

이 명령은 Get-ScheduledJob를 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져온 다음 각 예약 된 작업 (있는 경우)의 작업 트리거를 **가져오는 jobtrigger** 로 파이프 합니다.

작업 트리거 표시에 예약 된 작업의 이름을 추가 하기 위해이 명령은 Format-Table cmdlet의 계산 된 속성 기능을 사용 합니다.
이 명령은 기본적으로 표시 되는 작업 트리거 속성 외에 예약 된 작업의 이름을 표시 하는 새 Set-scheduledjob 속성을 만듭니다.

### 예 6: 예약 된 작업의 작업 트리거 속성 가져오기

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

예약된 작업의 작업 트리거는 작업의 JobTriggers 속성에 저장됩니다.
이 예에서는 **Get JobTrigger** cmdlet을 사용 하 여 작업 트리거를 가져오는 방법을 보여 줍니다.
결과는 **Get-JobTrigger** cmdlet을 사용하는 것과 동일하며 교환해서 사용할 수 있습니다.

### 예 7: 작업 트리거 비교

```
The first command gets the job trigger of the ArchiveProjects scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T1 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name ArchiveProjects | Get-JobTrigger | Tee-Object -Variable T1
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The second command gets the job trigger of the Test-HelpFiles scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T2 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name "Test-HelpFiles" | Get-JobTrigger | Tee-Object -Variable T2
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The third command compares the job triggers in the $t1 and $t2 variables. It uses the Get-Member cmdlet to get the properties of the job trigger in the $t1 variable. It pipes the properties to the ForEach-Object cmdlet, which compares each property to the properties of the job trigger in the $t2 variable by name. The command then pipes the differing properties to the Format-List cmdlet, which displays them in a list.The output indicates that, although the job triggers appear to be the same, the HelpFiles job trigger includes a random delay of three (3) minutes.
PS C:\> $T1 | Get-Member -Type Property | ForEach-Object { Compare-Object $T1 $T2 -Property $_.Name}
RandomDelay                                                 SideIndicator
-----------                                                 -------------
00:00:00                                                    =>
00:03:00                                                    <=
```

이 예제에서는 두 예약된 작업의 작업 트리거를 비교하는 방법을 보여 줍니다.

## PARAMETERS

### -Id
예약된 작업의 ID 번호를 지정합니다.
**Get-JobTrigger** 는 지정한 예약된 작업의 작업 트리거를 가져옵니다.

로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 id 번호를 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
예약된 작업을 지정합니다.
**Set-scheduledjob** 개체가 포함 된 변수를 입력 하거나 **set-scheduledjob** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.
**Set-scheduledjob** 개체를 **가져오기-jobtrigger** 로 파이프 할 수도 있습니다.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
예약된 작업의 이름을 지정합니다.
**Get-JobTrigger** 는 지정한 예약된 작업의 작업 트리거를 가져옵니다.
와일드카드가 지원됩니다.

로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 이름을 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TriggerId
지정한 작업 트리거를 가져옵니다.
예약된 작업의 하나 이상 작업 트리거에 대한 트리거 ID를 입력합니다.
*Name* , *ID* 또는 *InputObject* 매개 변수로 지정된 예약된 작업에 여러 개의 작업 트리거가 있을 때 이 매개 변수를 사용합니다.

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Set-scheduledjob. ScheduledJobDefinition
Get-ScheduledJob에서 **가져오기-JobTrigger** 로 예약 된 작업을 파이프 할 수 있습니다.

## 출력

### Set-scheduledjob. ScheduledJobTrigger

## 참고

## 관련 링크

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[Register-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Unregister-ScheduledJob](Unregister-ScheduledJob.md)
