---
description: PowerShell 백그라운드 작업에서 현재 세션과 상호 작용 하지 않고 백그라운드에서 명령 또는 식을 실행 하는 방법에 대 한 정보를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 6ddb54bac62e7bc11a045874700acb3982a0093b
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524470"
---
# <a name="about-jobs"></a>작업 정보

## <a name="short-description"></a>간단한 설명
PowerShell 백그라운드 작업에서 현재 세션과 상호 작용 하지 않고 백그라운드에서 명령 또는 식을 실행 하는 방법에 대 한 정보를 제공 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다. PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 유형이 있습니다.

- `RemoteJob` -명령 및 스크립트가 원격 세션에서 실행 됩니다. 자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.
- `BackgroundJob` -명령 및 스크립트는 로컬 컴퓨터에서 별도의 프로세스로 실행 됩니다.
- `PSTaskJob` 또는 `ThreadJob` -명령 및 스크립트는 로컬 컴퓨터에서 동일한 프로세스 내에서 별도의 스레드에서 실행 됩니다. 자세한 내용은 [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)를 참조 하세요.

별도의 컴퓨터에서 또는 별도의 프로세스로 스크립트를 원격으로 실행 하는 것이 뛰어난 격리를 제공 합니다. 원격 작업에서 발생 하는 모든 오류는 실행 중인 다른 작업이 나 작업을 시작한 부모 세션에는 영향을 주지 않습니다. 그러나 원격 계층은 개체 serialization을 포함 하 여 오버 헤드를 추가 합니다. 모든 개체는 부모 세션과 원격 (작업) 세션 간에 전달 될 때 serialize 되 고 deserialize 됩니다. 크고 복잡 한 데이터 개체의 Serialization은 많은 양의 계산 및 메모리 리소스를 사용 하 고 네트워크를 통해 많은 양의 데이터를 전송할 수 있습니다.

스레드 기반 작업은 여러 스레드에서 동일한 프로세스로 실행 되기 때문에 원격 및 백그라운드 작업 만큼 강력 하지 않습니다. 한 작업에 프로세스를 중단 하는 중대 한 오류가 있는 경우 프로세스의 다른 모든 작업이 종료 됩니다.

그러나 스레드 기반 작업에는 오버 헤드가 적게 필요 합니다. Remoting 계층 또는 serialization은 사용 하지 않습니다. 결과 개체는 현재 세션의 라이브 개체에 대 한 참조로 반환 됩니다. 이러한 오버 헤드가 없으면 스레드 기반 작업은 더 빠르게 실행 되 고 다른 작업 유형에 비해 리소스를 적게 사용 합니다.

> [!IMPORTANT]
> 작업을 만든 부모 세션도 작업 상태를 모니터링 하 고 파이프라인 데이터를 수집 합니다. 작업이 완료 된 상태에 도달 하면 부모 프로세스가 작업 자식 프로세스를 종료 합니다. 부모 세션이 종료 되 면 모든 실행 중인 자식 작업은 자식 프로세스와 함께 종료 됩니다.

이 제한 사항을 해결 하는 방법에는 두 가지가 있습니다.

1. `Invoke-Command`를 사용 하 여 연결 되지 않은 세션에서 실행 되는 작업을 만듭니다. 자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.
1. `Start-Process`작업 대신 새 프로세스를 만들려면를 사용 합니다. 자세한 내용은 [시작-처리](xref:Microsoft.PowerShell.Management.Start-Process)를 참조 하세요.

## <a name="the-job-cmdlets"></a>작업 cmdlet

|Cmdlet          |Description                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |로컬 컴퓨터에서 백그라운드 작업을 시작 합니다.           |
|`Get-Job`       |에서 시작 된 백그라운드 작업을 가져옵니다.      |
|                |현재 세션입니다.                                       |
|`Receive-Job`   |백그라운드 작업의 결과를 가져옵니다.                   |
|`Stop-Job`      |백그라운드 작업을 중지 합니다.                                |
|`Wait-Job`      |하나 또는 모든 작업이 완료 될 때까지 명령 프롬프트를 표시 하지 않습니다.|
|                |완료.                                              |
|`Remove-Job`    |백그라운드 작업을 삭제 합니다.                              |
|`Invoke-Command`|**AsJob** 매개 변수는에 대 한 백그라운드 작업을 만듭니다.  |
|                |원격 컴퓨터. `Invoke-Command`를 사용 하 여를 실행할 수 있습니다.   |
|                |을 포함 하 여 원격으로 작업 명령 `Start-Job`       |

## <a name="how-to-start-a-job-on-the-local-computer"></a>로컬 컴퓨터에서 작업을 시작 하는 방법

로컬 컴퓨터에서 백그라운드 작업을 시작 하려면 cmdlet을 사용 `Start-Job` 합니다.

명령을 작성 하려면 `Start-Job` 작업을 실행 하는 명령을 중괄호 ()로 묶습니다 `{}` . **ScriptBlock** 매개 변수를 사용 하 여 명령을 지정 합니다.

다음 명령은 `Get-Process` 로컬 컴퓨터에서 명령을 실행 하는 백그라운드 작업을 시작 합니다.

```powershell
Start-Job -ScriptBlock {Get-Process}
```

백그라운드 작업을 시작 하면 작업을 완료 하는 데 오랜 시간이 소요 되는 경우에도 명령 프롬프트가 즉시 반환 됩니다. 작업이 실행되는 동안 중단 없이 세션에서 작업을 계속할 수 있습니다.

`Start-Job`이 명령은 작업을 나타내는 개체를 반환 합니다. 작업 개체에는 작업에 대한 유용한 정보가 포함되어 있지만 작업 결과는 포함되어 있지 않습니다.

작업 개체를 변수에 저장 한 다음 다른 **작업** cmdlet과 함께 사용 하 여 백그라운드 작업을 관리할 수 있습니다. 다음 명령은 작업 개체를 시작 하 고 결과 작업 개체를 변수에 저장 합니다 `$job` .

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

PowerShell 6.0부터 파이프라인 끝에 백그라운드 연산자 ()를 사용 `&` 하 여 백그라운드 작업을 시작할 수 있습니다. 자세한 내용은 [background operator](about_Operators.md#background-operator-)를 참조 하세요.

백그라운드 연산자를 사용 하는 것은 이전 예제에서 cmdlet을 사용 하는 것과 기능적으로 동일 `Start-Job` 합니다.

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a>작업 개체 가져오기

`Get-Job`Cmdlet은 현재 세션에서 시작 된 백그라운드 작업을 나타내는 개체를 반환 합니다. 매개 변수가 없으면 `Get-Job` 현재 세션에서 시작 된 모든 작업을 반환 합니다.

```powershell
Get-Job
```

작업 개체에는 작업이 완료 되었는지 여부를 나타내는 작업의 상태가 포함 됩니다. 완료 된 작업의 상태가 **완료** 또는 **실패** 입니다. 작업이 **차단** 되거나 **실행 중일** 수도 있습니다.

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

작업 개체를 변수에 저장 하 고이를 사용 하 여 이후 명령에서 작업을 나타낼 수 있습니다. 다음 명령은 ID가 1 인 작업을 가져와서 변수에 저장 합니다 `$job` .

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a>작업 결과 가져오기

백그라운드 작업을 실행 하면 결과가 즉시 표시 되지 않습니다. 백그라운드 작업의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .

다음 예에서는 cmdlet이 `Receive-Job` 변수에 job 개체를 사용 하 여 작업의 결과를 가져옵니다 `$job` .

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

작업의 결과를 변수에 저장할 수 있습니다. 다음 명령은 변수에 있는 작업의 결과를 변수에 저장 합니다 `$job` `$results` .

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a>부분 작업 결과 가져오기 및 유지

`Receive-Job`Cmdlet은 백그라운드 작업의 결과를 가져옵니다. 작업이 완료 되 면 `Receive-Job` 모든 작업 결과를 가져옵니다. 작업이 계속 실행 중인 경우 `Receive-Job` 지금까지 생성 된 결과를 가져옵니다. `Receive-Job`명령을 다시 실행 하 여 나머지 결과를 가져올 수 있습니다.

기본적으로는 `Receive-Job` 작업 결과가 저장 되는 캐시에서 결과를 삭제 합니다. `Receive-Job`을 다시 실행 하면 첫 번째 실행 후 도착 한 새 결과만 얻을 수 있습니다.

다음 명령은 `Receive-Job` 작업이 완료 되기 전에 실행 된 명령의 결과를 보여 줍니다.

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

**Keep** 매개 변수를 사용 하 여 반환 되는 `Receive-Job` 작업 결과를 삭제 하지 못하도록 합니다. 다음 명령은 아직 완료 되지 않은 작업에 대해 **Keep** 매개 변수를 사용 하는 경우의 효과를 보여 줍니다.

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a>결과를 기다리는 중

완료 하는 데 시간이 오래 걸리는 명령을 실행 하는 경우 작업 개체의 속성을 사용 하 여 작업이 완료 된 시간을 확인할 수 있습니다. 다음 명령은 개체를 사용 하 여 `Get-Job` 현재 세션의 모든 백그라운드 작업을 가져옵니다.

```powershell
Get-Job
```

결과는 테이블에 표시 됩니다. 작업 상태가 **상태** 열에 표시 됩니다.

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

이 경우 **State** 속성은 작업 2가 여전히 실행 되 고 있음을 나타냅니다. Cmdlet을 사용 하 여 `Receive-Job` 지금 작업 결과를 가져오는 경우 결과가 완전 하지 않습니다. `Receive-Job`Cmdlet을 반복 해 서 사용 하 여 모든 결과를 가져올 수 있습니다. **상태** 속성을 사용 하 여 작업이 완료 된 시기를 확인 합니다.

또한 cmdlet의 **Wait** 매개 변수를 사용할 수 있습니다 `Receive-Job` . 이 매개 변수를 사용 하는 경우 작업이 완료 되 고 모든 결과를 사용할 수 있을 때까지 cmdlet은 명령 프롬프트를 반환 하지 않습니다.

Cmdlet을 사용 하 여 `Wait-Job` 작업 결과의 일부 또는 모두를 기다릴 수도 있습니다. `Wait-Job` 하나 이상의 특정 작업 또는 모든 작업에 대해 대기할 수 있습니다.
다음 명령은 cmdlet을 사용 하 여 `Wait-Job` **ID가** 인 작업을 대기 합니다.
10.

```powershell
Wait-Job -ID 10
```

따라서 작업이 완료 될 때까지 PowerShell 프롬프트가 표시 되지 않습니다.

미리 정해진 시간 동안 기다릴 수도 있습니다. 이 명령은 Timeout 매개 변수를 사용 하 여 대기 **시간** 을 120 초로 제한 합니다. 시간이 만료 되 면 명령 프롬프트가 반환 되지만 작업은 백그라운드에서 계속 실행 됩니다.

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a>작업 중지

백그라운드 작업을 중지 하려면 cmdlet을 사용 `Stop-Job` 합니다. 다음 명령을 실행 하 여 시스템 이벤트 로그의 모든 항목을 가져오는 작업을 시작 합니다. 작업 개체를 `$job` 변수에 저장 합니다.

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

다음 명령은 작업을 중지 합니다. 파이프라인 연산자 ()를 사용 하 여 `|` 변수에서 작업을 `$job` 로 보냅니다 `Stop-Job` .

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a>작업 삭제

백그라운드 작업을 삭제 하려면 cmdlet을 사용 `Remove-Job` 합니다. 다음 명령은 변수에서 작업을 삭제 합니다 `$job` .

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a>실패 한 작업 조사

작업은 여러 가지 이유로 실패할 수 있습니다. 작업 개체에는 실패 원인에 대 한 정보를 포함 하는 **Reason** 속성이 포함 되어 있습니다.

다음 예에서는 필수 자격 증명 없이 작업을 시작 합니다.

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

**Reason** 속성을 검사 하 여 작업이 실패 하 게 만든 오류를 확인 합니다.

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

이 경우 원격 컴퓨터에서 명령을 실행 하기 위한 명시적 자격 증명이 필요 하기 때문에 작업이 실패 했습니다. **Reason** 속성은 다음과 같은 메시지를 포함 합니다.

> "액세스가 거부 되었습니다." 라는 오류 메시지와 함께 원격 서버에 연결 하지 못했습니다.

## <a name="see-also"></a>참고 항목

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_PSSessions](about_PSSessions.md)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
