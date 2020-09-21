---
title: 다중 스레딩 중에 진행률 표시
description: Foreach-Object -Parallel을 통해 여러 스레드에서 Write-Progress를 사용하는 방법
ms.date: 08/02/2020
ms.openlocfilehash: 909fc1bbdeded8845b1955e3384fb55db7173030
ms.sourcegitcommit: 640646992955116def23d16dd12c221857d37b68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89410845"
---
# <a name="writing-progress-across-multiple-threads-with-foreach-parallel"></a>Foreach Parallel을 사용하여 여러 스레드에서 진행률 기록

PowerShell 7.0부터, [Foreach-Object](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) cmdlet에서 **Parallel** 매개 변수를 사용하여 여러 스레드에서 동시에 작업할 수 있습니다. 그렇지만 스레드의 진행률을 모니터링하는 것이 문제일 수 있습니다. 일반적으로 [Write-Progress](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress)를 사용하여 프로세스의 진행률을 모니터링할 수 있습니다.
그러나 **Parallel**을 사용하면 PowerShell에서 각 스레드에 별도의 runspace를 사용하기 때문에 진행률을 다시 호스트에 보고하는 것이 일반적인 `Write-Progress` 사용만큼 간단하지 않습니다.

## <a name="using-a-synced-hashtable-to-track-progress"></a>동기화된 해시 테이블을 사용하여 진행률 추적

여러 스레드에서 진행률을 기록하는 경우 PowerShell에서 병렬 프로세스를 실행할 때 각 프로세스에 자체 runspace가 있기 때문에 추적이 어려워집니다. 이 문제를 해결하는 데는 [동기화된 해시 테이블](/dotnet/api/system.collections.hashtable.synchronized)을 사용할 수 있습니다. 동기화된 해시 테이블은 오류를 throw하지 않고 여러 스레드에서 동시에 수정할 수 있는 스레드로부터 안전한 데이터 구조입니다.

### <a name="set-up"></a>설정

이 접근 방식의 단점 중 하나는 모든 것이 오류 없이 실행될 수 있도록 다소 복잡한 설정을 사용한다는 것입니다.

```powershell
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)
```

이 섹션에서는 세 가지 용도의 세 가지 데이터 구조를 만듭니다.

`$dataSet` 변수는 수정될 위험 없이 다음 단계를 조정하는 데 사용되는 해시 테이블의 배열을 저장합니다. 컬렉션을 반복하는 동안 개체 컬렉션이 수정되면 PowerShell에서 오류를 throw합니다. 수정되는 개체와는 별도로 개체 컬렉션을 루프에서 유지해야 합니다. 각 해시 테이블의 `Id` 키는 모의 프로세스의 식별자입니다. `Wait` 키는 추적되는 각 모의 프로세스의 워크로드를 시뮬레이트합니다.

`$origin` 변수는 각 키가 모의 프로세스 ID 중 하나인 중첩된 해시 테이블을 저장합니다.
그런 다음, `$sync` 변수에 저장된 동기화된 해시 테이블을 하이드레이션하는 데 사용됩니다. `$sync` 변수는 진행률을 표시하는 부모 runspace에 진행률을 다시 보고하는 작업을 수행합니다.

### <a name="running-the-processes"></a>프로세스 실행

이 섹션에서는 다중 스레드 프로세스를 실행하고 진행률을 표시하는 데 사용되는 일부 출력을 만듭니다.

```powershell
$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}
```

모의 프로세스는 `Foreach-Object`로 전송되고 작업으로 시작됩니다. **ThrottleLimit**를 **3**으로 설정하여 큐에서 여러 프로세스 실행을 강조 표시합니다. 작업은 `$job` 변수에 저장되며 나중에 모든 프로세스가 완료된 시기를 알려 줄 수 있습니다.

`using:` 문을 사용하여 PowerShell에서 부모 범위 변수를 참조하는 경우 동적으로 설정하는 데 식을 사용할 수 없습니다. 예를 들어 `$process = $using:sync.$($PSItem.id)`와 같이 `$process` 변수를 만들려고 시도하면 여기에 식을 사용할 수 없다는 오류 메시지가 표시됩니다. 따라서 실패할 위험 없이 `$sync` 변수를 참조 및 수정할 수 있는 `$syncCopy` 변수를 만듭니다.

다음으로, 동기화된 해시 테이블 키를 참조하여 `$process` 변수를 통해 현재 루프에서 프로세스의 진행률을 나타내는 해시 테이블을 빌드합니다. **Activity** 및 **Status** 키는 다음 섹션에서 지정된 모의 프로세스의 상태를 표시하는 `Write-Progress`의 매개 변수 값으로 사용됩니다.

`foreach` 루프는 프로세스 작동을 시뮬레이트하는 한 가지 방법일 뿐이며 밀리초를 사용하여 `Start-Sleep`을 설정하는 `$dataSet` **Wait** 특성에 따라 무작위로 지정됩니다. 프로세스의 진행률을 계산하는 방법은 달라질 수 있습니다.

### <a name="displaying-the-progress-of-multiple-processes"></a>여러 프로세스의 진행률 표시

이제 모의 프로세스가 작업으로 실행되므로 PowerShell 창에 프로세스 진행률을 기록하기 시작할 수 있습니다.

```powershell
while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

`$job` 변수는 부모 **작업**을 포함하며 각 모의 프로세스의 자식 **작업**을 포함합니다. 자식 작업이 계속 실행되는 동안 부모 작업 **상태**는 “실행 중”으로 유지됩니다. 따라서 `while` 루프를 사용하여 모든 프로세스가 완료될 때까지 모든 프로세스의 진행률을 지속적으로 업데이트할 수 있습니다.

while 루프 내에서 `$sync` 변수의 각 키를 반복합니다. 이는 동기화된 해시 테이블이므로 지속적으로 업데이트되지만 오류를 throw하지 않고 계속 액세스할 수 있습니다.

보고되는 프로세스가 실제로 `IsNullOrEmpty()` 메서드를 사용하여 실행되는지 확인하는 검사가 있습니다. 프로세스가 시작되지 않은 경우 루프는 이를 보고하지 않고 시작된 프로세스에 도달할 때까지 다음으로 이동합니다. 프로세스가 시작되면 현재 키의 해시 테이블은 `Write-Progress`에 매개 변수를 스플랫하는 데 사용됩니다.

### <a name="full-example"></a>전체 예제

```powershell
# Example workload
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)

$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}

while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

## <a name="related-links"></a>관련 링크

- [about_Jobs](/powershell/module/Microsoft.PowerShell.Core/About/about_Jobs)
- [about_Scopes](/powershell/module/Microsoft.PowerShell.Core/About/about_Scopes)
- [about_Splatting](/powershell/module/Microsoft.PowerShell.Core/About/about_Splatting)
