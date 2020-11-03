---
description: PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다. 스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 4951ac2c14c0685fbf2ead16bc52c64096231260
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93224594"
---
# <a name="about-thread-jobs"></a>스레드 작업 정보

## <a name="short-description"></a>간단한 설명

PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다. 스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.

## <a name="long-description"></a>자세한 설명입니다.

이 문서에서는 로컬 컴퓨터의 PowerShell에서 스레드 작업을 실행 하는 방법을 설명 합니다.
로컬 컴퓨터에서 백그라운드 작업을 실행 하는 방법에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요.

Cmdlet을 사용 하 여 스레드 작업을 시작 `Start-ThreadJob` 합니다. 이 cmdlet은 PowerShell과 함께 제공 되는 **Threadjob** 모듈에서 사용할 수 있습니다.
`Start-ThreadJob` 실행 중인 명령이 나 스크립트를 캡슐화 하 고 모든 PowerShell 작업에서 cmdlet을 조작 하는 데 사용할 수 있는 단일 작업 개체를 반환 합니다.

## <a name="the-job-cmdlets"></a>작업 cmdlet

|cmdlet           |Description                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|로컬 컴퓨터에서 스레드 작업을 시작 합니다.               |
|`Get-Job`        |현재 세션에서 시작 된 작업을 가져옵니다.|
|`Receive-Job`    |작업의 결과를 가져옵니다.                              |
|`Stop-Job`       |실행 중인 작업을 중지 합니다.                                   |
|`Wait-Job`       |하나 또는 모든 작업이 완료 될 때까지 명령 프롬프트를 표시 하지 않습니다.|
|                 |완료.                                              |
|`Remove-Job`     |작업을 삭제합니다.                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a>로컬 컴퓨터에서 스레드 작업을 시작 하는 방법

로컬 컴퓨터에서 스레드 작업을 시작 하려면 cmdlet을 사용 `Start-ThreadJob` 합니다.

명령을 작성 하려면 `Start-ThreadJob` 명령이 나 스크립트를 중괄호 ()로 묶습니다 `{ }` .

다음 명령은 `Get-Process` 로컬 컴퓨터에서 명령을 실행 하는 스레드 작업을 시작 합니다.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

`Start-ThreadJob`명령은 `ThreadJob` 실행 중인 작업을 나타내는 개체를 반환 합니다. 작업 개체에는 현재 실행 상태를 포함 하 여 작업에 대 한 유용한 정보가 포함 되어 있습니다. 결과를 생성 하는 중에 작업의 결과를 수집 합니다.

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>작업이 완료 될 때까지 대기 하 고 작업 결과를 검색 하는 방법

PowerShell 작업 cmdlet (예: 및)을 `Wait-Job` 사용 `Receive-Job` 하 여 작업이 완료 될 때까지 기다린 다음 작업에 의해 생성 된 모든 결과를 반환할 수 있습니다.

다음 명령은 명령을 실행 하는 스레드 작업을 시작 하 고 `Get-Process` 명령이 완료 될 때까지 대기한 다음 명령에 의해 생성 된 모든 데이터 결과를 반환 합니다.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

## <a name="powershell-concurrency-and-jobs"></a>PowerShell 동시성 및 작업

PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다. PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 기반 솔루션이 있습니다.

|작업            |Description                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |명령 및 스크립트가 원격 컴퓨터에서 실행 됩니다.                 |
|`BackgroundJob`|명령 및 스크립트가 로컬에서 별도의 프로세스로 실행 됩니다.    |
|               |할당합니다.                                                     |
|`ThreadJob`    |명령 및 스크립트가 동일한 내에서 별도의 스레드에서 실행 됩니다.  |
|               |로컬 컴퓨터의 프로세스입니다.                                |

각 유형의 작업에는 장점과 단점이 있습니다. 별도의 컴퓨터나 별도의 프로세스에서 원격으로 스크립트를 실행 하는 것은 매우 효율적입니다. 모든 오류는 실행 중인 다른 작업이 나 작업을 시작한 클라이언트에는 영향을 주지 않습니다. 하지만 원격 계층은 개체 serialization을 포함 하 여 오버 헤드를 추가 합니다. 원격 세션과 주고 받은 모든 개체는 클라이언트와 대상 세션 간에 전달 될 때 serialize 된 다음 deserialize 되어야 합니다. Serialization 작업은 복잡 한 데이터 개체에 많은 계산 및 메모리 리소스를 사용할 수 있습니다.

## <a name="powershell-thread-based-jobs"></a>PowerShell 스레드 기반 작업

스레드 기반 작업은 여러 스레드에서 동일한 프로세스로 실행 되기 때문에 원격 및 백그라운드 작업 만큼 강력 하지 않습니다. 한 작업에 프로세스를 중단 하는 중대 한 오류가 있는 경우 프로세스의 다른 작업도 모두 실패 합니다.

그러나 스레드 기반 작업의 오버 헤드가 훨씬 줄어듭니다. 원격 계층 또는 serialization을 사용할 필요가 없습니다. 따라서 스레드 기반 작업은 훨씬 더 빨리 실행 되 고 다른 작업 유형에 비해 훨씬 더 작은 리소스를 사용 하는 경향이 있습니다.

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
10457.962


(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
24.9277
```

위의 첫 번째 예제에서는 간단한 문자열 쓰기를 수행 하는 1000 스레드 작업을 만드는 foreach 루프를 보여 줍니다. 작업 오버 헤드로 인해 완료 하는 데 33 초 이상이 소요 됩니다.

두 번째 예제에서는 cmdlet을 실행 `ForEach` 하 여 동일한 1000 작업을 수행 하 고 각 문자열 쓰기가 작업 오버 헤드 없이 순차적으로 실행 됩니다. 25 밀리초 안에 완료 됩니다.

```powershell
$logNames.count
10

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

위의 예제에서는 10 개의 개별 시스템 로그에 대해 최대 5000 개의 항목이 수집 됩니다. 스크립트에는 많은 로그 읽기가 포함 되므로 작업을 병렬로 수행 하는 것이 의미가 있습니다. 그리고 작업은 스크립트를 순차적으로 실행 하는 것 처럼 두 번 이상 완료 됩니다.

```powershell
Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a>스레드 작업 및 변수

변수는 다양 한 방식으로 스레드 작업에 전달 됩니다.

`Start-ThreadJob` 는 cmdlet으로 파이프 되는 변수, 키워드를 통해 스크립트 블록으로 전달 `$using` 되거나 **argumentlist** 매개 변수를 통해 전달 되는 변수를 사용할 수 있습니다.

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

스레드 작업은 동일한 프로세스에서 실행 되므로 작업에 전달 되는 변수 참조 형식은 신중 하 게 처리 해야 합니다. 스레드로부터 안전한 개체가 아닌 경우에는 할당 되지 않아야 하 고 메서드 및 속성을 호출 하면 안 됩니다.

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

위의 예제에서는 `ConcurrentDictionary` 모든 자식 작업에 스레드로부터 안전한 dotNet 개체를 전달 하 여 고유 하 게 명명 된 프로세스 개체를 수집 합니다. 스레드로부터 안전한 개체 이므로 작업이 프로세스에서 동시에 실행 되는 동안 안전 하 게 사용할 수 있습니다.

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
