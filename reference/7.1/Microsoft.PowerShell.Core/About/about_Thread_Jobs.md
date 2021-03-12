---
description: PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다. 스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.
Locale: en-US
ms.date: 11/11/2020
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 67f3fc585a8c2d1c3ca98c7336a7e367ed6c66c7
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194235"
---
# <a name="about-thread-jobs"></a>스레드 작업 정보

## <a name="short-description"></a>간단한 설명

PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다. 스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다. PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 유형이 있습니다.

- `RemoteJob` -명령 및 스크립트가 원격 세션에서 실행 됩니다. 자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.
- `BackgroundJob` -명령 및 스크립트는 로컬 컴퓨터에서 별도의 프로세스로 실행 됩니다. 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조하세요.
- `PSTaskJob` 또는 `ThreadJob` -명령 및 스크립트는 로컬 컴퓨터에서 동일한 프로세스 내에서 별도의 스레드에서 실행 됩니다.

스레드 기반 작업은 여러 스레드에서 동일한 프로세스로 실행 되기 때문에 원격 및 백그라운드 작업 만큼 강력 하지 않습니다. 한 작업에 프로세스를 중단 하는 중대 한 오류가 있는 경우 프로세스의 다른 모든 작업이 종료 됩니다.

그러나 스레드 기반 작업에는 오버 헤드가 적게 필요 합니다. Remoting 계층 또는 serialization은 사용 하지 않습니다. 결과 개체는 현재 세션의 라이브 개체에 대 한 참조로 반환 됩니다. 이러한 오버 헤드가 없으면 스레드 기반 작업은 더 빠르게 실행 되 고 다른 작업 유형에 비해 리소스를 적게 사용 합니다.

> [!IMPORTANT]
> 작업을 만든 부모 세션도 작업 상태를 모니터링 하 고 파이프라인 데이터를 수집 합니다. 작업이 완료 된 상태에 도달 하면 부모 프로세스가 작업 자식 프로세스를 종료 합니다. 부모 세션이 종료 되 면 모든 실행 중인 자식 작업은 자식 프로세스와 함께 종료 됩니다.

이러한 상황을 해결 하는 방법에는 두 가지가 있습니다.

1. `Invoke-Command`를 사용 하 여 연결 되지 않은 세션에서 실행 되는 작업을 만듭니다. 자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.
1. `Start-Process`작업 대신 새 프로세스를 만들려면를 사용 합니다. 자세한 내용은 [시작-처리](xref:Microsoft.PowerShell.Management.Start-Process)를 참조 하세요.

## <a name="how-to-start-and-manage-thread-based-jobs"></a>스레드 기반 작업을 시작 하 고 관리 하는 방법

스레드 기반 작업을 시작 하는 방법에는 두 가지가 있습니다.

- `Start-ThreadJob` - **Threadjob** 모듈에서
- `ForEach-Object -Parallel -AsJob` -병렬 기능이 PowerShell 7.0에서 추가 되었습니다.

[About_Jobs](about_Jobs.md) 에 설명 된 것과 동일한 **작업** cmdlet을 사용 하 여 스레드 기반 작업을 관리 합니다.

### <a name="using-start-threadjob"></a>`Start-ThreadJob` 사용

**Threadjob** 모듈은 먼저 PowerShell 6과 함께 제공 됩니다. Windows PowerShell 5.1에 대 한 PowerShell 갤러리에서 설치할 수도 있습니다.

로컬 컴퓨터에서 스레드 작업을 시작 하려면 중괄호 `Start-ThreadJob` ()로 묶인 명령이 나 스크립트를 사용 하 여 cmdlet을 사용 `{ }` 합니다.

다음 예제에서는 `Get-Process` 로컬 컴퓨터에서 명령을 실행 하는 스레드 작업을 시작 합니다.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

`Start-ThreadJob`명령은 `ThreadJob` 실행 중인 작업을 나타내는 개체를 반환 합니다. 작업 개체에는 현재 실행 상태를 포함 하 여 작업에 대 한 유용한 정보가 포함 되어 있습니다. 결과를 생성 하는 중에 작업의 결과를 수집 합니다.

### <a name="using-foreach-object--parallel--asjob"></a>`ForEach-Object -Parallel -AsJob` 사용

PowerShell 7.0이 cmdlet에 새 매개 변수 집합을 추가 했습니다 `ForEach-Object` . 새 매개 변수를 사용 하 여 병렬 스레드에서 스크립트 블록을 PowerShell 작업으로 실행할 수 있습니다.

데이터를로 파이프 할 수 있습니다 `ForEach-Object -Parallel` . 데이터는 병렬로 실행 되는 스크립트 블록으로 전달 됩니다. `-AsJob`매개 변수는 각 병렬 스레드에 대해 작업 개체를 만듭니다.

다음 명령은 명령으로 파이프 된 각 입력 값에 대 한 자식 작업을 포함 하는 작업을 시작 합니다. 각 자식 작업은 `Write-Output` 파이프 된 입력 값을 인수로 사용 하 여 명령을 실행 합니다.

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

`ForEach-Object -Parallel`이 명령은 파이프 된 `PSTaskJob` 각 입력 값에 대 한 자식 작업을 포함 하는 개체를 반환 합니다. 작업 개체에는 자식 작업 실행 상태에 대 한 유용한 정보가 포함 되어 있습니다. 결과를 생성 하는 중에 자식 작업의 결과를 수집 합니다.

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>작업이 완료 될 때까지 대기 하 고 작업 결과를 검색 하는 방법

PowerShell 작업 cmdlet (예: 및)을 `Wait-Job` 사용 `Receive-Job` 하 여 작업이 완료 될 때까지 기다린 다음 작업에 의해 생성 된 모든 결과를 반환할 수 있습니다.

다음 명령은 명령을 실행 하는 스레드 작업을 시작 하 고 `Get-Process` 명령이 완료 될 때까지 대기한 다음 명령에 의해 생성 된 모든 데이터 결과를 반환 합니다.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

다음 명령은 파이프 된 각 입력에 대해 명령을 실행 하는 작업을 시작한 `Write-Output` 다음 모든 자식 작업이 완료 될 때까지 대기 하 고, 마지막으로 자식 작업에 의해 생성 된 모든 데이터 결과를 반환 합니다.

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

이 `Receive-Job` cmdlet은 자식 작업의 결과를 반환 합니다.

```powershell
1
3
2
4
5
```

각 자식 작업은 병렬로 실행 되므로 생성 된 결과의 순서는 보장 되지 않습니다.

## <a name="thread-job-performance"></a>스레드 작업 성능

스레드 작업은 다른 유형의 작업 보다 더 빠르고 가벼운 가중치입니다. 하지만 작업에서 수행 하는 작업에 비해 오버 헤드가 클 수 있습니다.

PowerShell은 세션에서 명령 및 스크립트를 실행 합니다. 세션에서 한 번에 하나의 명령 또는 스크립트만 실행할 수 있습니다. 따라서 여러 작업을 실행할 때 각 작업은 별도의 세션에서 실행 됩니다. 각 세션은 오버 헤드에 기여 합니다.

스레드 작업은 수행 하는 작업이 작업을 실행 하는 데 사용 되는 세션의 오버 헤드 보다 큰 경우 최적의 성능을 제공 합니다. 이 조건을 충족 하는 두 가지 사례가 있습니다.

- 작업은 계산 집약적입니다. 여러 스레드 작업에서 스크립트를 실행 하면 여러 프로세서 코어를 활용 하 여 더 빨리 완료할 수 있습니다.

- 작업은 i/o 또는 원격 호출 결과를 대기 하는 데 시간을 소비 하는 스크립트를 대기 하는 중요 한 부분으로 구성 됩니다. 병렬로 실행 하는 것은 일반적으로 순차적으로 실행 하는 경우 보다 더 빨리 완료 됩니다.

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

위의 첫 번째 예제에서는 간단한 문자열 쓰기를 수행 하는 1000 스레드 작업을 만드는 foreach 루프를 보여 줍니다. 작업 오버 헤드로 인해 완료 하는 데 36 초 이상이 소요 됩니다.

두 번째 예제는 cmdlet을 실행 `ForEach` 하 여 동일한 1000 작업을 수행 합니다.
이번에는 `ForEach-Object` 작업 오버 헤드 없이 단일 스레드에서 순차적으로 실행 됩니다. 이는 단지 7 밀리초 안에 완료 됩니다.

다음 예제에서는 10 개의 개별 시스템 로그에 대해 최대 5000 개의 항목이 수집 됩니다. 스크립트에는 많은 로그 읽기가 포함 되므로 작업을 병렬로 수행 하는 것이 의미가 있습니다.

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

작업을 병렬로 실행 하는 경우 스크립트가 완료 됩니다.

```powershell
Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a>스레드 작업 및 변수

여러 가지 방법으로 스레드 기반 작업에 값을 전달할 수 있습니다.

`Start-ThreadJob` 는 cmdlet으로 파이프 되는 변수, 키워드를 통해 스크립트 블록으로 전달 `$using` 되거나 **argumentlist** 매개 변수를 통해 전달 되는 변수를 사용할 수 있습니다.

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

`ForEach-Object -Parallel` 변수에서 파이프를 수락 하 고 키워드를 통해 스크립트 블록에 직접 전달 되는 변수를 허용 `$using` 합니다.

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

스레드 작업은 동일한 프로세스에서 실행 되므로 작업에 전달 되는 변수 참조 형식은 신중 하 게 처리 해야 합니다. 스레드로부터 안전한 개체가 아닌 경우에는 할당 되지 않아야 하 고 메서드 및 속성을 호출 하면 안 됩니다.

다음 예제에서는 스레드로부터 안전한 .NET `ConcurrentDictionary` 개체를 모든 자식 작업에 전달 하 여 고유 하 게 명명 된 프로세스 개체를 수집 합니다. 스레드로부터 안전한 개체 이므로 작업이 프로세스에서 동시에 실행 되는 동안 안전 하 게 사용할 수 있습니다.

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

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
