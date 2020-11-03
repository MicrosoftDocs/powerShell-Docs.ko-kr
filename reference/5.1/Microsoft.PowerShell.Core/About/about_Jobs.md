---
description: PowerShell 백그라운드 작업에서 현재 세션과 상호 작용 하지 않고 백그라운드에서 명령 또는 식을 실행 하는 방법에 대 한 정보를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: a2fba9024f9b365c79ea5d59d6840a72ba1f8b21
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93224569"
---
# <a name="about-jobs"></a>작업 정보

## <a name="short-description"></a>간단한 설명
PowerShell 백그라운드 작업에서 현재 세션과 상호 작용 하지 않고 백그라운드에서 명령 또는 식을 실행 하는 방법에 대 한 정보를 제공 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다. PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 기반 솔루션이 있습니다.

|작업            |Description                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |명령 및 스크립트가 원격 컴퓨터에서 실행 됩니다.                 |
|`BackgroundJob`|명령 및 스크립트가 로컬에서 별도의 프로세스로 실행 됩니다.    |
|               |할당합니다.                                                     |
|`ThreadJob`    |명령 및 스크립트가 동일한 내에서 별도의 스레드에서 실행 됩니다.  |
|               |로컬 컴퓨터의 프로세스입니다.                                |

각 유형의 작업에는 장점과 단점이 있습니다. 별도의 컴퓨터나 별도의 프로세스에서 원격으로 스크립트를 실행 하는 것은 매우 효율적입니다. 모든 오류는 실행 중인 다른 작업이 나 작업을 시작한 클라이언트에는 영향을 주지 않습니다. 하지만 원격 계층은 개체 serialization을 포함 하 여 오버 헤드를 추가 합니다. 원격 세션과 주고 받은 모든 개체는 클라이언트와 대상 세션 간에 전달 될 때 serialize 된 다음 deserialize 되어야 합니다. Serialization 작업은 복잡 한 데이터 개체에 많은 계산 및 메모리 리소스를 사용할 수 있습니다.

이 항목에서는 로컬 컴퓨터의 PowerShell에서 백그라운드 작업을 실행 하는 방법에 대해 설명 합니다. 원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법에 대 한 자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요. 스레드 작업에 대 한 자세한 내용은 [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)를 참조 하세요.

백그라운드 작업을 시작 하면 작업을 완료 하는 데 오랜 시간이 소요 되는 경우에도 명령 프롬프트가 즉시 반환 됩니다. 작업이 실행되는 동안 중단 없이 세션에서 작업을 계속할 수 있습니다.

## <a name="the-job-cmdlets"></a>작업 cmdlet

|cmdlet          |Description                                            |
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

`Start-Job`이 명령은 작업을 나타내는 개체를 반환 합니다. 작업 개체에는 작업에 대한 유용한 정보가 포함되어 있지만 작업 결과는 포함되어 있지 않습니다.

작업 개체를 변수에 저장 한 다음 다른 작업 cmdlet과 함께 사용 하 여 백그라운드 작업을 관리 합니다. 다음 명령은 작업 개체를 시작 하 고 결과 작업 개체를 변수에 저장 합니다 `$job` .

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

Cmdlet을 사용 하 여 `Get-Job` 현재 세션에서 시작 된 작업을 나타내는 개체를 가져올 수도 있습니다. `Get-Job` 에서 반환 하는 것과 동일한 작업 개체를 반환 `Start-Job` 합니다.

## <a name="getting-job-objects"></a>작업 개체 가져오기

현재 세션에서 시작 된 백그라운드 작업을 나타내는 개체를 가져오려면 cmdlet을 사용 합니다 `Get-Job` . 매개 변수가 없으면 `Get-Job` 현재 세션에서 시작 된 모든 작업을 반환 합니다.

예를 들어 다음 명령은 현재 세션의 작업을 가져옵니다.

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

작업 개체를 변수에 저장 하 고이를 사용 하 여 이후 명령에서 작업을 나타낼 수도 있습니다. 다음 명령은 ID가 1 인 작업을 가져와서 변수에 저장 합니다 `$job` .

```powershell
$job = Get-Job -Id 1
```

작업 개체에는 작업이 완료 되었는지 여부를 나타내는 작업의 상태가 포함 됩니다. 완료 된 작업의 상태가 **완료** 또는 **실패** 입니다. 작업이 **차단** 되거나 **실행 중일** 수도 있습니다.

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a>작업 결과 가져오기

백그라운드 작업을 실행 하면 결과가 즉시 표시 되지 않습니다. 대신 `Start-Job` 이 cmdlet은 작업을 나타내는 작업 개체를 반환 하지만 결과는 포함 하지 않습니다. 백그라운드 작업의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .

다음 명령은 cmdlet을 사용 하 여 `Receive-Job` 작업의 결과를 가져옵니다. 변수에 저장 된 작업 개체를 사용 하 여 `$job` 작업을 식별 합니다.

```powershell
Receive-Job -Job $job
```

`Receive-Job`Cmdlet은 작업의 결과를 반환 합니다.

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

작업의 결과를 변수에 저장할 수도 있습니다. 다음 명령은 변수에 있는 작업의 결과를 변수에 저장 합니다 `$job` `$results` .

```powershell
$results = Receive-Job -Job $job
```

그리고 리디렉션 연산자 () 또는 cmdlet을 사용 하 여 작업 결과를 파일에 저장할 수 있습니다 `>` `Out-File` . 다음 명령은 리디렉션 연산자를 사용 하 여 작업 결과를 `$job` 파일의 변수에 저장 `Results.txt` 합니다.

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a>부분 작업 결과 가져오기 및 유지

`Receive-Job`Cmdlet은 백그라운드 작업의 결과를 가져옵니다. 작업이 완료 되 면 `Receive-Job` 모든 작업 결과를 가져옵니다. 작업이 계속 실행 중인 경우 `Receive-Job` 지금까지 생성 된 결과를 가져옵니다. `Receive-Job`명령을 다시 실행 하 여 나머지 결과를 가져올 수 있습니다.

는 `Receive-Job` 결과를 반환할 때 기본적으로 작업 결과가 저장 되는 캐시에서 해당 결과를 삭제 합니다. 다른 명령을 실행 하면 `Receive-Job` 아직 수신 되지 않은 결과만 얻게 됩니다.

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

반환 된 `Receive-Job` 작업 결과를 삭제 하지 않으려면 **Keep** 매개 변수를 사용 합니다. 결과적으로 `Receive-Job` 는 해당 시간까지 생성 된 모든 결과를 반환 합니다.

다음 명령은 아직 완료 되지 않은 작업에 대해 **Keep** 매개 변수를 사용 하는 경우의 효과를 보여 줍니다.

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

## <a name="waiting-for-the-results"></a>결과를 기다리는 중

완료 하는 데 시간이 오래 걸리는 명령을 실행 하는 경우 작업 개체의 속성을 사용 하 여 작업이 완료 된 시간을 확인할 수 있습니다. 다음 명령은 개체를 사용 하 여 `Get-Job` 현재 세션의 모든 백그라운드 작업을 가져옵니다.

```powershell
Get-Job
```

결과는 테이블에 표시 됩니다. 작업 상태가 **상태** 열에 표시 됩니다.

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

이 경우 State 속성은 작업 2가 여전히 실행 되 고 있음을 나타냅니다. Cmdlet을 사용 하 여 `Receive-Job` 지금 작업 결과를 가져오는 경우 결과가 완전 하지 않습니다. `Receive-Job`Cmdlet을 반복 해 서 사용 하 여 모든 결과를 가져올 수 있습니다. 기본적으로 사용할 때마다 아직 수신 되지 않은 결과만 가져오지만 cmdlet의 **Keep** 매개 변수를 사용 `Receive-Job` 하 여 결과를 이미 받은 경우라도 유지할 수 있습니다.

파일에 부분 결과를 기록한 다음 도착 하면 최신 결과를 추가 하거나 나중에 작업 상태를 확인 하 고 확인할 수 있습니다.

Cmdlet의 **Wait** 매개 변수를 사용할 수 있습니다 .이 매개 변수는 `Receive-Job` 작업이 완료 되 고 모든 결과를 사용할 수 있을 때까지 명령 프롬프트를 반환 하지 않습니다.

Cmdlet을 사용 하 여 `Wait-Job` 작업 결과의 일부 또는 모두를 기다릴 수도 있습니다. `Wait-Job` 모든 작업에 대해 특정 작업이 수행 될 때까지 기다리거나 작업을 완료할 때까지 기다릴 수 있습니다.

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

작업이 실패 한 이유를 확인 하려면 작업 개체의 **Reason** 속성을 사용 합니다.

다음 명령은 필수 자격 증명 없이 작업을 시작 합니다. 작업 개체를 `$job` 변수에 저장 합니다.

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

다음 명령은 Reason 속성을 사용 하 여 작업 실패를 일으킨 오류를 찾습니다.

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

이 경우 원격 컴퓨터에서 명령을 실행 하기 위한 명시적 자격 증명이 필요 하기 때문에 작업이 실패 했습니다. **Reason** 속성의 값은 다음과 같습니다.

"액세스가 거부 되었습니다." 라는 오류 메시지와 함께 원격 서버에 연결 하지 못했습니다.

## <a name="see-also"></a>참고 항목

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)
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
