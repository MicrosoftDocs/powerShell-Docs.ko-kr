---
description: 로컬 및 원격 컴퓨터의 백그라운드 작업에 대 한 세부 정보를 제공 합니다.
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: 1ceb0be9cc140b69afdebaaf336dad75e482aa22
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599366"
---
# <a name="about-job-details"></a>작업 정보 정보

## <a name="short-description"></a>간단한 설명
로컬 및 원격 컴퓨터의 백그라운드 작업에 대 한 세부 정보를 제공 합니다.

## <a name="detailed-description"></a>자세한 설명

이 항목에서는 백그라운드 작업의 개념에 대해 설명 하 고 PowerShell에서 백그라운드 작업의 작동 방식에 대 한 기술 정보를 제공 합니다.

이 항목은 [about_Jobs](about_Jobs.md), [about_Thread_Jobs](about_Thread_Jobs.md)및 [about_Remote_Jobs](about_Remote_Jobs.md) 항목에 대 한 추가 자료입니다.

### <a name="about-background-jobs"></a>백그라운드 작업 정보

백그라운드 작업은 명령 또는 식을 비동기식으로 실행 합니다. Cmdlet, 함수, 스크립트 또는 다른 명령 기반 작업을 실행할 수 있습니다. 이는 오랜 시간 동안 실행 되는 명령을 실행 하도록 설계 되었지만이를 사용 하 여 백그라운드에서 명령을 실행할 수 있습니다.

동기식 명령이 실행 되 면 명령이 완료 될 때까지 PowerShell 명령 프롬프트가 표시 되지 않습니다. 그러나 백그라운드 작업은 PowerShell 프롬프트를 표시 하지 않습니다. 백그라운드 작업을 시작 하는 명령은 job 개체를 반환 합니다.
메시지가 즉시 반환 되므로 백그라운드 작업이 실행 되는 동안 다른 작업을 수행할 수 있습니다.

그러나 백그라운드 작업을 시작 하면 작업이 매우 빠르게 실행 되더라도 결과가 즉시 표시 되지 않습니다. 반환 되는 작업 개체에는 작업에 대 한 유용한 정보가 포함 되어 있지만 작업 결과는 포함 되어 있지 않습니다. 작업 결과를 가져오려면 별도의 명령을 실행 해야 합니다. 또한 명령을 실행 하 여 작업을 중지 하 고, 작업이 완료 될 때까지 기다리거나, 작업을 삭제할 수 있습니다.

백그라운드 작업의 타이밍을 다른 명령과 독립적으로 만들기 위해 각 백그라운드 작업은 자체 PowerShell 세션에서 실행 됩니다. 그러나이는 작업을 실행 하는 경우에만 생성 되 고 삭제 되는 임시 연결 일 수 있습니다. 또는 여러 관련 작업 또는 명령을 실행 하는 데 사용할 수 있는 영구적인 **PSSession** 이 될 수 있습니다.

### <a name="using-the-job-cmdlets"></a>작업 cmdlet 사용

명령을 사용 `Start-Job` 하 여 로컬 컴퓨터에서 백그라운드 작업을 시작 합니다.
`Start-Job` 작업 개체를 반환 합니다. Cmdlet을 사용 하 여 로컬 컴퓨터에서 시작 된 작업을 나타내는 개체를 가져올 수도 있습니다 `Get-Job` .

작업 결과를 가져오려면 `Receive-Job` 명령을 사용 합니다. 작업이 완료 되지 않으면에서 `Receive-Job` 일부 결과를 반환 합니다. Cmdlet을 사용 하 여 `Wait-Job` 세션에서 시작 된 작업 중 하나 또는 모두가 완료 될 때까지 명령 프롬프트를 표시 하지 않을 수도 있습니다.

백그라운드 작업을 중지 하려면 cmdlet을 사용 `Stop-Job` 합니다. 작업을 삭제 하려면 cmdlet을 사용 `Remove-Job` 합니다.

Cmdlet의 작동 방식에 대 한 자세한 내용은 각 cmdlet에 대 한 도움말 항목을 참조 하 고 [about_Jobs](about_Jobs.md)를 참조 하세요.

### <a name="starting-background-jobs-on-remote-computers"></a>원격 컴퓨터에서 백그라운드 작업 시작

로컬 또는 원격 컴퓨터에서 백그라운드 작업을 만들고 관리할 수 있습니다. 백그라운드 작업을 원격으로 실행 하려면와 같은 cmdlet의 **AsJob** 매개 변수를 사용 `Invoke-Command` 하거나 cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격으로 명령을 실행 합니다. 대화형 세션에서 백그라운드 작업을 시작할 수도 있습니다.

원격 백그라운드 작업에 대 한 자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.

### <a name="child-jobs"></a>자식 작업

각 백그라운드 작업은 부모 작업과 하나 이상의 자식 작업으로 구성 됩니다. `Start-Job`또는 **AsJob** 매개 변수를 사용 하 여 시작한 작업에서 `Invoke-Command` 부모 작업은 executive입니다. 명령을 실행 하거나 아무 결과도 반환 하지 않습니다. 명령은 실제로 자식 작업에서 실행 됩니다. 다른 cmdlet을 사용 하 여 시작 하는 작업은 다르게 작동할 수 있습니다.

자식 작업은 부모 작업 개체의 **childjobs** 속성에 저장 됩니다. **Childjobs** 속성은 하나 이상의 자식 작업 개체를 포함할 수 있습니다.
자식 작업 개체는 부모 작업과 다른 **이름**, **ID** 및 **InstanceId** 를 가지 므로 부모 및 자식 작업을 개별적으로 또는 하나의 단위로 관리할 수 있습니다.

작업의 부모 및 자식 작업을 가져오려면 cmdlet의 **IncludeChildJobs** 매개 변수를 사용 합니다 `Get-Job` . **IncludeChildJob** 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

부모 작업과 특정 **상태** 값을 가진 자식 작업만 가져오려면 Cmdlet의 **ChildJobState** 매개 변수를 사용 합니다 `Get-Job` . **ChildJobState** 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

모든 버전의 PowerShell에서 작업의 자식 작업을 가져오려면 부모 작업의 **childjob** 속성을 사용 합니다.

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

`Get-Job`다음 명령에 표시 된 것 처럼 자식 작업에서 명령을 사용할 수도 있습니다.

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

자식 작업의 구성은 작업을 시작 하는 데 사용 하는 명령에 따라 달라 집니다.

- 를 사용 `Start-Job` 하 여 로컬 컴퓨터에서 작업을 시작 하는 경우이 작업은 executive 부모 작업과 명령을 실행 하는 자식 작업으로 구성 됩니다.

- 의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` 하나 이상의 컴퓨터에서 작업을 시작 하는 경우이 작업은 executive 부모 작업과 각 컴퓨터에서 실행 되는 각 작업에 대 한 자식 작업으로 구성 됩니다.

- `Invoke-Command`를 사용 하 여 하나 이상의 `Start-Job` 원격 컴퓨터에서 명령을 실행 하는 경우 결과는 각 원격 컴퓨터에서 실행 되는 로컬 명령과 동일 합니다. 이 명령은 각 컴퓨터의 작업 개체를 반환 합니다. 작업 개체는 executive 부모 작업과 명령을 실행 하는 하나의 자식 작업으로 구성 됩니다.

부모 작업은 모든 자식 작업을 나타냅니다. 부모 작업을 관리 하는 경우에도 연결 된 자식 작업을 관리 합니다. 예를 들어 부모 작업을 중지 하면 모든 자식 작업이 중지 됩니다. 부모 작업의 결과를 가져오는 경우 모든 자식 작업의 결과를 가져옵니다.

그러나 자식 작업을 개별적으로 관리할 수도 있습니다. 이는 작업의 문제를 조사 하거나의 **AsJob** 매개 변수를 사용 하 여 시작 된 여러 자식 작업 중 하나의 결과만 가져오는 경우에 가장 유용 합니다 `Invoke-Command` .

다음 명령은의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` 로컬 컴퓨터와 두 개의 원격 컴퓨터에서 백그라운드 작업을 시작 합니다. 이 명령은 작업을 `$j` 변수에 저장 합니다.

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

에서 작업의 Name 및 **childjob** 속성을 표시 하면 `$j` 명령에서 각 컴퓨터에 대해 하나씩 세 개의 자식 작업이 있는 작업 개체를 반환 하는 것을 보여 줍니다.

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

부모 작업을 표시 하면 작업이 실패 한 것으로 표시 됩니다.

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

그러나 `Get-Job` 자식 작업을 가져오는 명령을 실행 하면 하나의 자식 작업만 실패 한 것으로 출력에 표시 됩니다.

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

모든 자식 작업의 결과를 가져오려면 cmdlet을 사용 `Receive-Job` 하 여 부모 작업의 결과를 가져옵니다. 그러나 다음 명령에 표시 된 것 처럼 특정 자식 작업의 결과를 가져올 수도 있습니다.

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

PowerShell 백그라운드 작업의 자식 작업 기능을 사용 하면 실행 하는 작업을 보다 효과적으로 제어할 수 있습니다.

### <a name="job-types"></a>작업 유형

PowerShell은 작업 마다 다른 유형의 작업을 지원 합니다. Windows PowerShell 3.0부터 개발자는 새 작업 유형을 PowerShell에 추가 하 고 작업 원본 어댑터를 모듈에 포함 하는 "작업 원본 어댑터"를 작성할 수 있습니다.
모듈을 가져올 때 세션에서 새 작업 유형을 사용할 수 있습니다.

예를 들어 PSScheduledJob 모듈은 예약 된 작업을 추가 하 고 PSWorkflow 모듈은 워크플로 작업을 추가 합니다.

사용자 지정 작업 유형은 표준 PowerShell 백그라운드 작업과 크게 다를 수 있습니다. 예를 들어 예약 된 작업은 디스크에 저장 됩니다. 특정 세션에만 존재 하지 않습니다. 워크플로 작업을 일시 중단 하 고 다시 시작할 수 있습니다.

사용자 지정 작업을 관리 하는 데 사용 하는 cmdlet은 작업 유형에 따라 달라 집니다. 일부 경우에는 및와 같은 표준 작업 cmdlet을 사용 `Get-Job` `Start-Job` 합니다. 다른 작업은 특정 유형의 작업을 관리 하는 특수 한 cmdlet과 함께 제공 됩니다. 사용자 지정 작업 유형에 대 한 자세한 내용은 작업 유형에 대 한 도움말 항목을 참조 하세요.

작업의 작업 유형을 찾으려면 cmdlet을 사용 합니다 `Get-Job` . `Get-Job` 는 다른 작업 유형에 대해 서로 다른 작업 개체를 반환 합니다. 가 반환 하는 작업 개체의 **PSJobTypeName** 속성 값은 `Get-Job` 작업 유형을 나타냅니다.

다음 표에서는 PowerShell과 함께 제공 되는 작업 유형을 보여 줍니다.

|    작업 유형    |                       설명                        |
| -------------- | -------------------------------------------------------- |
| BackgroundJob  | Cmdlet을 사용 하 여 시작 되었습니다 `Start-Job` .                    |
| RemoteJob      | 의 **AsJob** 매개 변수를 사용 하 여 시작 되었습니다.             |
|                | `Invoke-Command` cmdlet                                 |
| PSWorkflowJob  | 워크플로의 **AsJob** 매개 변수를 사용 하 여 시작 되었습니다.     |
| PSScheduledJob | 작업 트리거에서 시작한 예약 된 작업의 인스턴스입니다. |
| CIMJob         | 에서 cmdlet의 **AsJob** 매개 변수를 사용 하기 시작 했습니다. |
|                | CDXML 모듈.                                            |
| WMIJob         | 에서 cmdlet의 **AsJob** 매개 변수를 사용 하기 시작 했습니다. |
|                | WMI 모듈.                                              |
| PSEventJob     | 를 사용 하 여 만든 `Register-ObjectEvent` 다음를 지정 합니다.    |
|                | **action 매개 변수** 를 사용 하는 작업입니다.                    |

참고: cmdlet을 사용 하 여 `Get-Job` 특정 유형의 작업을 가져오기 전에 작업 유형을 추가 하는 모듈을 현재 세션으로 가져왔는지 확인 합니다.
그렇지 않으면 `Get-Job` 는 해당 형식의 작업을 가져오지 않습니다.

## <a name="examples"></a>예

다음 명령은 로컬 백그라운드 작업, 원격 백그라운드 작업, 워크플로 작업 및 예약 된 작업을 만듭니다. 그런 다음 cmdlet을 사용 하 여 `Get-Job` 작업을 가져옵니다. `Get-Job` 는 예약 된 작업을 가져오지 않지만 예약 된 작업의 시작 된 인스턴스를 가져옵니다.

로컬 컴퓨터에서 백그라운드 작업을 시작 합니다.

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

원격 컴퓨터에서 실행 되는 백그라운드 작업을 시작 합니다.

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

예약된 작업 만들기

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

워크플로를 만듭니다.

```powershell
PS> workflow Test-Workflow {Get-Process}
```

워크플로를 작업으로 실행 합니다.

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

작업을 가져옵니다. `Get-Job`이 명령은 예약 된 작업을 가져오지 않지만 시작 된 예약 된 작업의 인스턴스를 가져옵니다.

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

예약 된 작업을 가져오려면 cmdlet을 사용 `Get-ScheduledJob` 합니다.

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a>참고 항목

- [about_Jobs](about_Jobs.md)
- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Remote](about_Remote.md)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
