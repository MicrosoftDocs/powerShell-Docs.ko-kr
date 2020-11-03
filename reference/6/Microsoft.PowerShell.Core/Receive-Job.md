---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 0d22f99341c487d2bd1b64d621cdca99d20e5328
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216402"
---
# Receive-Job

## 개요
현재 세션의 PowerShell 백그라운드 작업 결과를 가져옵니다.

## SYNTAX

### Location (기본값)

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### 컴퓨터 이름

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### 세션

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### NameParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### SessionIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## 설명

Cmdlet은 cmdlet `Receive-Job` `Start-Job` 또는 **AsJob** 매개 변수를 사용 하 여 시작 된 것과 같은 PowerShell 백그라운드 작업의 결과를 가져옵니다.
모든 작업의 결과를 가져오거나, 이름, ID, 인스턴스 ID, 컴퓨터 이름, 위치 또는 세션으로 또는 작업 개체를 전송하여 작업을 식별할 수 있습니다.

PowerShell 백그라운드 작업을 시작 하면 작업이 시작 되지만 결과가 즉시 표시 되지 않습니다. 대신 이 명령은 백그라운드 작업을 나타내는 개체를 반환합니다.
작업 개체에는 작업에 대한 유용한 정보가 포함되어 있지만 결과는 포함되어 있지 않습니다.
이 방법을 사용 하면 작업이 실행 되는 동안 세션에서 작업을 계속할 수 있습니다.
PowerShell의 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](./About/about_Jobs.md)를 참조 하세요.

`Receive-Job`Cmdlet은 명령이 전송 된 시간에 의해 생성 된 결과를 가져옵니다 `Receive-Job` .
결과가 아직 완료 되지 않았으면 추가 `Receive-Job` 명령을 실행 하 여 나머지 결과를 얻을 수 있습니다.

기본적으로 작업 결과는 해당 결과를 받을 때 시스템에서 삭제되지만 **Keep** 매개 변수를 사용하여 결과를 다시 받을 수 있도록 저장할 수 있습니다.
작업 결과를 삭제 하려면 `Receive-Job` **Keep** 매개 변수 없이 명령을 다시 실행 하거나, 세션을 닫거나, cmdlet을 사용 `Remove-Job` 하 여 세션에서 작업을 삭제 합니다.

Windows PowerShell 3.0부터는 `Receive-Job` 워크플로 작업 및 예약 된 작업 인스턴스와 같은 사용자 지정 작업 유형의 결과도 가져옵니다.
에서 `Receive-Job` 결과를 사용자 지정 작업 형식으로 가져오도록 하려면 `Receive-Job` cmdlet을 사용 `Import-Module` 하거나 모듈에서 cmdlet을 사용 하 여 명령을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다.
특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.

## 예제

### 예 1: 특정 작업에 대 한 결과 가져오기

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

이러한 명령은의 **job** 매개 변수를 사용 `Receive-Job` 하 여 특정 작업의 결과를 가져옵니다.

첫 번째 명령은를 사용 하 여 작업을 시작 `Start-Job` 하 고 해당 개체를 변수에 저장 합니다 `$job` .

두 번째 명령은 cmdlet을 사용 하 여 `Receive-Job` 작업의 결과를 가져옵니다.
**Job** 매개 변수를 사용하여 작업을 지정합니다.

### 예제 2: Keep 매개 변수 사용

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

이 예에서는 작업을 변수에 저장 `$job` 하 고 작업을 cmdlet으로 파이프 `Receive-Job` 합니다. `-Keep`매개 변수를 사용 하 여 첫 번째 뷰 후 집계 된 모든 스트림 데이터를 다시 검색할 수 있습니다.

### 예제 3: 여러 백그라운드 작업의 결과 가져오기

의 **AsJob** 매개 변수를 사용 하 여 작업을 시작 하는 경우 작업이 `Invoke-Command` 원격 컴퓨터에서 실행 되더라도 작업 개체는 로컬 컴퓨터에 만들어집니다.
따라서 로컬 명령을 사용하여 작업을 관리합니다.

또한 **AsJob** 을 사용 하는 경우 PowerShell은 시작 된 각 작업에 대 한 자식 작업을 포함 하는 하나의 작업 개체를 반환 합니다. 여기서는 작업 개체에 각 원격 컴퓨터의 작업마다 하나씩 세 개의 자식 작업이 포함됩니다.

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### 예제 4: 여러 원격 컴퓨터에서 백그라운드 작업의 결과 가져오기

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

이 예제에서는 세 개의 원격 컴퓨터에서 실행되는 백그라운드 작업의 결과를 가져오는 방법을 보여 줍니다.
이전 예제와 달리를 사용 하 여 명령을 실행 하는 것은 `Invoke-Command` `Start-Job` 실제로 세 컴퓨터 각각에 대해 3 개의 독립적인 작업을 시작 했습니다. 따라서 이 명령은 세 컴퓨터에서 로컬로 실행된 세 작업을 나타내는 세 작업 개체를 반환했습니다.

> [!NOTE]
> 마지막 명령에서 `$j` 는 지역 변수 이기 때문에 스크립트 블록은 **Using** 범위 한정자를 사용 하 여 변수를 식별 `$j` 합니다. **Using** 범위 한정자에 대 한 자세한 내용은 [about_Remote_Variables](./About/about_Remote_Variables.md)를 참조 하세요.

### 예 5: 자식 작업 액세스

`-Keep`매개 변수는 작업을 다시 볼 수 있도록 집계 된 스트림의 상태를 유지 합니다. 이 매개 변수를 사용 하지 않으면 집계 된 모든 스트림 데이터가 작업이 수신 될 때 지워집니다. 자세한 내용은 [about_Job_Details](About/about_Job_Details.md#child-jobs) 를 참조 하세요.

> [!NOTE]
> 집계 스트림은 모든 자식 작업의 스트림을 포함 합니다. 작업 개체 및 자식 작업 개체를 통해 데이터의 개별 스트림에 계속 도달할 수 있습니다.

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## PARAMETERS

### -AutoRemoveJob

이 cmdlet이 작업 결과를 반환한 후 작업을 삭제 함을 나타냅니다.
작업에 더 많은 결과가 포함 된 경우에도 작업이 삭제 되지만 `Receive-Job` 메시지가 표시 됩니다.

이 매개 변수는 사용자 지정 작업 유형에서만 사용할 수 있으며,
작업을 저장하는 작업 유형 또는 세션에서 벗어난 유형의 인스턴스(예: 예약된 작업의 인스턴스)용으로 설계되었습니다.

이 매개 변수는 **Wait** 매개 변수 없이 사용할 수 없습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -ComputerName

컴퓨터 이름 배열을 지정 합니다.

이 매개 변수는 로컬 컴퓨터에 저장된 작업 결과 중에서 선택하며,
원격 컴퓨터에서 실행 되는 작업에 대 한 데이터는 가져오지 않습니다.
원격 컴퓨터에 저장 된 작업 결과를 가져오려면 cmdlet을 사용 하 여 원격 `Invoke-Command` `Receive-Job` 으로 명령을 실행 합니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Force

작업이 **일시 중단** 되거나 **연결** 되지 않은 상태에 있는 경우이 cmdlet이 계속 대기 함을 나타냅니다. 기본적으로의 **wait** 매개 변수는 `Receive-Job` 작업이 다음 상태 중 하나일 때을 반환 하거나 대기를 종료 합니다.

- Completed
- 실패
- 중지됨
- 일시 중단
- 연결 끊김

**Force** 매개 변수는 명령에 **Wait** 변수가 사용된 경우에만 유효합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -Id

ID 배열을 지정합니다.
이 cmdlet은 지정 된 Id의 작업 결과를 가져옵니다.

ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.
인스턴스 ID 보다 더 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다. 하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.
작업 ID를 찾으려면를 사용 `Get-Job` 합니다.

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

인스턴스 Id의 배열을 지정 합니다.
이 cmdlet은 지정한 인스턴스 Id를 가진 작업의 결과를 가져옵니다.

인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.
작업의 인스턴스 ID를 확인 하려면 cmdlet을 사용 합니다 `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Job

결과를 검색할 작업을 지정합니다.

작업이 포함된 변수나 작업을 가져오는 명령을 입력하세요.
작업 개체를로 파이프 할 수도 있습니다 `Receive-Job` .

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -유지

이 cmdlet을 받은 후에도이 cmdlet이 집계 된 스트림 데이터를 시스템에 저장 함을 나타냅니다. 기본적으로 집계 된 스트림 데이터는로 본 후에 지워집니다 `Receive-Job` .

세션을 닫거나 cmdlet을 사용 하 여 작업을 제거 하면 `Remove-Job` 집계 된 스트림 데이터도 삭제 됩니다.

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

### -Location

위치 배열을 지정 합니다.
이 cmdlet은 지정 된 위치에 있는 작업의 결과만 가져옵니다.

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

이름 배열을 지정합니다.
이 cmdlet은 지정 된 이름의 작업 결과를 가져옵니다.
와일드카드 문자가 지원됩니다.

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

### -NoRecurse

이 cmdlet이 지정 된 작업 에서만 결과를 가져오는 것을 나타냅니다.
기본적으로는 `Receive-Job` 지정 된 작업의 모든 자식 작업에 대 한 결과를 가져옵니다.

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

### -Session

세션의 배열을 지정 합니다.
이 cmdlet은 지정 된 PowerShell 세션 ( **PSSession** )에서 실행 된 작업의 결과를 가져옵니다.
**Pssession** 이 포함 된 변수를 입력 하거나 **pssession** 을 가져오는 명령 (예: 명령)을 입력 합니다 `Get-PSSession` .

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Wait

모든 작업 결과를 받을 때까지이 cmdlet이 명령 프롬프트를 표시 하지 않음을 나타냅니다.
기본적으로는 `Receive-Job` 사용 가능한 결과를 즉시 반환 합니다.

**Wait** 매개 변수는 기본적으로 작업이 다음 상태 중 하나일 때까지 대기합니다.

- Completed
- 실패
- 중지됨
- 일시 중단
- 연결 끊김

작업 상태가 일시 중단 되거나 연결이 끊어진 경우 **대기 매개 변수를 계속** 대기 하려면 **wait** 매개 변수와 함께 **Force** 매개 변수를 사용 합니다.

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

### -WriteEvents

작업이 완료 되기를 기다리는 동안이 cmdlet이 작업 상태의 변경 내용을 보고 함을 나타냅니다.

이 매개 변수는 명령에서 **Wait** 매개 변수를 사용하고 **Keep** 매개 변수를 생략하는 경우에만 유효합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### -WriteJobInResults

이 cmdlet은 작업 개체를 반환 하 고 그 뒤에 결과를 반환 함을 나타냅니다.

이 매개 변수는 명령에서 **Wait** 매개 변수를 사용하고 **Keep** 매개 변수를 생략하는 경우에만 유효합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](./About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.object.

작업 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### PSObject

이 cmdlet은 작업의 명령 결과를 반환 합니다.

## 참고

## 관련 링크

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)
