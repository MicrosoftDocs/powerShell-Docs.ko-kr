---
description: 원격 컴퓨터에서 작업을 실행 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 71f59fcb8e656e4ac439028507f15cf36b8402f6
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524929"
---
# <a name="about-remote-jobs"></a>원격 작업 정보

## <a name="short-description"></a>간단한 설명
원격 컴퓨터에서 작업을 실행 하는 방법을 설명 합니다.

## <a name="detailed-description"></a>자세한 설명

PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다. PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 유형이 있습니다.

- `RemoteJob` -명령 및 스크립트가 원격 세션에서 실행 됩니다.
- `BackgroundJob` -명령 및 스크립트는 로컬 컴퓨터에서 별도의 프로세스로 실행 됩니다. 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조하세요.
- `PSTaskJob` 또는 `ThreadJob` -명령 및 스크립트는 로컬 컴퓨터에서 동일한 프로세스 내에서 별도의 스레드에서 실행 됩니다. 자세한 내용은 [about_Thread_Jobs](about_Thread_Jobs.md)를 참조 하세요.

별도의 컴퓨터에서 또는 별도의 프로세스로 스크립트를 원격으로 실행 하면 뛰어난 격리를 제공 합니다. 원격 작업에서 발생 하는 모든 오류는 실행 중인 다른 작업이 나 작업을 시작한 부모 세션에는 영향을 주지 않습니다. 그러나 원격 계층은 개체 serialization을 포함 하 여 오버 헤드를 추가 합니다. 모든 개체는 부모 세션과 원격 (작업) 세션 간에 전달 될 때 serialize 되 고 deserialize 됩니다. 크고 복잡 한 데이터 개체의 Serialization은 많은 양의 계산 및 메모리 리소스를 사용 하 고 네트워크를 통해 많은 양의 데이터를 전송할 수 있습니다.

> [!IMPORTANT]
> 작업을 만든 부모 세션도 작업 상태를 모니터링 하 고 파이프라인 데이터를 수집 합니다. 작업이 완료 된 상태에 도달 하면 부모 프로세스가 작업 자식 프로세스를 종료 합니다. 부모 세션이 종료 되 면 모든 실행 중인 자식 작업은 자식 프로세스와 함께 종료 됩니다.

이러한 상황을 해결 하는 방법에는 두 가지가 있습니다.

1. `Invoke-Command`를 사용 하 여 연결 되지 않은 세션에서 실행 되는 작업을 만듭니다. 이 문서의 [분리 된 프로세스](#how-to-run-as-a-detached-process) 섹션을 참조 하세요.
1. `Start-Process`작업 대신 새 프로세스를 만들려면를 사용 합니다. 자세한 내용은 [시작-처리](xref:Microsoft.PowerShell.Management.Start-Process)를 참조 하세요.

## <a name="remote-jobs"></a>원격 작업

3 가지 방법을 사용 하 여 원격 컴퓨터에서 작업을 실행할 수 있습니다.

- 원격 컴퓨터에서 대화형 세션을 시작 합니다. 그런 다음 대화형 세션에서 작업을 시작 합니다. 모든 작업은 원격 컴퓨터에서 수행 되지만 절차는 로컬 작업 실행과 동일 합니다.

- 로컬 컴퓨터에 결과를 반환 하는 원격 컴퓨터에서 작업을 실행 합니다. 작업의 결과를 수집 하 고 로컬 컴퓨터의 중앙 위치에서 유지 관리 하려는 경우이 방법을 사용 합니다.

- 원격 컴퓨터에 대 한 결과를 유지 하는 원격 컴퓨터에서 작업을 실행 합니다. 작업 데이터가 원래 컴퓨터에서 더 안전 하 게 유지 되는 경우이 방법을 사용 합니다.

### <a name="start-a-job-in-an-interactive-session"></a>대화형 세션에서 작업 시작

원격 컴퓨터를 사용 하 여 대화형 세션을 시작한 다음 대화형 세션 중에 작업을 시작할 수 있습니다. 대화형 세션에 대 한 자세한 내용은 about_Remote 및을 참조 하세요 `Enter-PSSession` .

대화형 세션에서 작업을 시작 하는 절차는 로컬 컴퓨터에서 백그라운드 작업을 시작 하는 절차와 거의 동일 합니다. 그러나 모든 작업은 로컬 컴퓨터가 아닌 원격 컴퓨터에서 발생 합니다.

1. Cmdlet을 사용 `Enter-PSSession` 하 여 원격 컴퓨터와의 대화형 세션을 시작 합니다. 의 ComputerName 매개 변수를 사용 `Enter-PSSession` 하 여 대화형 세션에 대 한 임시 연결을 설정할 수 있습니다. 또는 Session 매개 변수를 사용 하 여 PowerShell 세션 (PSSession)에서 대화형 세션을 실행할 수 있습니다.

   다음 명령은 Server01 컴퓨터에서 대화형 세션을 시작 합니다.

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   명령 프롬프트가 변경 되어 이제 Server01 컴퓨터에 연결 되어 있음을 보여 줍니다.

   ```
   Server01\C:>
   ```

1. 세션에서 원격 작업을 시작 하려면 cmdlet을 사용 `Start-Job` 합니다. 다음 명령은 Server01 컴퓨터의 Windows PowerShell 이벤트 로그에 있는 이벤트를 가져오는 원격 작업을 실행 합니다. `Start-Job`Cmdlet은 작업을 나타내는 개체를 반환 합니다.

   이 명령은 작업 개체를 `$job` 변수에 저장 합니다.

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   작업이 실행 되는 동안 대화형 세션을 사용 하 여 다른 작업을 비롯 한 다른 명령을 실행할 수 있습니다. 그러나 작업이 완료 될 때까지 대화형 세션을 열어 두어야 합니다. 세션을 종료 하면 작업이 중단 되 고 결과가 손실 됩니다.

1. 작업이 완료 되었는지 확인 하려면 변수 값을 표시 `$job` 하거나 cmdlet을 사용 `Get-Job` 하 여 작업을 가져옵니다. 다음 명령은 cmdlet을 사용 하 여 `Get-Job` 작업을 표시 합니다.

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   `Get-Job`작업은 작업을 시작 하 고 동일한 컴퓨터에서 실행 되 고 있기 때문에 (이 경우 Server01) "localhost" 컴퓨터에서 작업이 실행 되는 것을 출력에 표시 합니다.

1. 작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` . 대화형 세션에서 결과를 표시 하거나 원격 컴퓨터의 파일에 저장할 수 있습니다. 다음 명령은 $job 변수의 작업 결과를 가져옵니다. 이 명령은 리디렉션 연산자 ()를 사용 `>` 하 여 작업 결과를 Server01 컴퓨터의 PsLog.txt 파일에 저장 합니다.

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. 대화형 세션을 종료 하려면 cmdlet을 사용 `Exit-PSSession` 합니다. 명령 프롬프트가 변경 되어 로컬 컴퓨터의 원래 세션으로 돌아갑니다.

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. 언제 `PsLog.txt` 든 지 Server01 컴퓨터에서 파일의 내용을 보려면 다른 대화형 세션을 시작 하거나 원격 명령을 실행 합니다. 여러 명령을 사용 하 여 파일의 데이터를 조사 하 고 관리 하려는 경우이 유형의 명령은 PSSession (영구 연결)에서 가장 잘 실행 됩니다 `PsLog.txt` . Pssession에 대 한 자세한 내용은 [about_PSSessions](about_PSSessions.md)를 참조 하세요.

   다음 명령은 cmdlet을 사용 `New-PSSession` 하 여 Server01 컴퓨터에 연결 된 **pssession** 을 만들고, cmdlet을 사용 하 여 `Invoke-Command` `Get-Content` pssession에서 명령을 실행 하 여 파일의 내용을 확인 합니다.

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>결과를 로컬 컴퓨터 (AsJob)로 반환 하는 원격 작업을 시작 합니다.

로컬 컴퓨터에 명령 결과를 반환 하는 원격 컴퓨터에서 작업을 시작 하려면 cmdlet과 같은 cmdlet의 **AsJob** 매개 변수를 사용 합니다 `Invoke-Command` .

**AsJob** 매개 변수를 사용 하는 경우 작업이 원격 컴퓨터에서 실행 되는 경우에도 실제로 작업 개체는 로컬 컴퓨터에 만들어집니다. 작업이 완료 되 면 결과는 로컬 컴퓨터에 반환 됩니다.

작업 명사 (Job cmdlet)를 포함 하는 cmdlet을 사용 하 여 모든 cmdlet에 의해 생성 된 작업을 관리할 수 있습니다. **AsJob** 매개 변수를 포함 하는 많은 Cmdlet은 PowerShell 원격을 사용 하지 않으므로 원격 기능을 사용 하도록 구성 되지 않고 원격 기능에 대 한 요구 사항을 충족 하지 않는 컴퓨터 에서도 사용할 수 있습니다.

1. 다음 명령은의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` Server01 컴퓨터에서 작업을 시작 합니다. 작업은 `Get-Eventlog` 시스템 로그의 이벤트를 가져오는 명령을 실행 합니다. JobName 매개 변수를 사용 하 여 작업에 표시 이름을 할당할 수 있습니다.

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   명령의 결과는 다음 샘플 출력과 유사 합니다.

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   **AsJob** 매개 변수를 사용 하는 경우는를 `Invoke-Command` 반환 하는 동일한 유형의 작업 개체를 반환 합니다 `Start-Job` . 작업 개체를 변수에 저장 하거나 명령을 사용 하 여 작업을 가져올 수 있습니다 `Get-Job` .

   Location 속성의 값은 작업이 Server01 컴퓨터에서 실행 되었음을 보여 줍니다.

1. Cmdlet의 **AsJob** 매개 변수를 사용 하 여 시작 된 작업을 관리 하려면 `Invoke-Command` job cmdlet을 사용 합니다. 원격 작업을 나타내는 작업 개체는 로컬 컴퓨터에 있기 때문에 작업을 관리 하기 위해 원격 명령을 실행할 필요가 없습니다.

   작업이 완료 되었는지 여부를 확인 하려면 `Get-Job` 명령을 사용 합니다. 다음 명령은 현재 세션에서 시작 된 모든 작업을 가져옵니다.

   ```powershell
   Get-Job
   ```

   원격 작업이 현재 세션에서 시작 되었기 때문에 로컬 `Get-Job` 명령은 작업을 가져옵니다. 작업 개체의 State 속성은 명령이 성공적으로 완료 되었음을 보여 줍니다.

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. 작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` . 작업 결과가 작업 개체가 있는 컴퓨터에 자동으로 반환 되므로 로컬 명령을 사용 하 여 결과를 가져올 수 있습니다 `Receive-Job` .

   다음 명령은 cmdlet을 사용 하 여 `Receive-Job` 작업의 결과를 가져옵니다. 세션 ID를 사용 하 여 작업을 식별 합니다. 이 명령은 $results 변수에 작업 결과를 저장 합니다. 또한 결과를 파일로 리디렉션할 수 있습니다.

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>원격 컴퓨터에 결과를 보관 하는 원격 작업 시작

원격 컴퓨터에서 명령 결과를 유지 하는 원격 컴퓨터에서 작업을 시작 하려면 cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터에서 명령을 실행 합니다. 이 메서드를 사용 하 여 여러 컴퓨터에서 작업을 실행할 수 있습니다.

명령을 원격으로 실행 하는 경우 `Start-Job` 작업 개체가 원격 컴퓨터에 만들어지고 작업 결과가 원격 컴퓨터에서 유지 관리 됩니다.
작업의 관점에서 보면 모든 작업은 로컬입니다. 원격 컴퓨터에서 로컬 작업을 관리 하기 위해 원격으로 명령을 실행 하는 것입니다.

1. Cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터에서 명령을 실행 합니다.

   이 명령에는 PSSession (영구 연결)이 필요 합니다. 의 ComputerName 매개 변수를 사용 하 여 임시 연결을 설정 하는 경우 `Invoke-Command` `Invoke-Command` 작업 개체가 반환 될 때 명령이 완료 된 것으로 간주 됩니다. 결과적으로 임시 연결이 닫히고 작업이 취소 됩니다.

   다음 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 컴퓨터에 연결 된 PSSession을 만듭니다. 이 명령은 PSSession을 변수에 저장 합니다 `$s` .

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   다음 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Start-Job` PSSession에서 명령을 실행 합니다. `Start-Job`명령과 `Get-Eventlog` 명령이 중괄호로 묶여 있습니다.

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   결과는 다음 예제 출력과 유사 합니다.

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   명령을 원격으로 실행 하는 경우는 `Start-Job` 를 `Invoke-Command` 반환 하는 동일한 유형의 작업 개체를 반환 합니다 `Start-Job` . 작업 개체를 변수에 저장 하거나 명령을 사용 하 여 작업을 가져올 수 있습니다 `Get-Job` .

   **Location** 속성의 값은 작업이 Server01 컴퓨터에서 실행 된 경우에도 "LocalHost" 라는 로컬 컴퓨터에서 실행 된 것을 보여 줍니다. 작업 개체는 Server01 컴퓨터에 생성 되 고 작업은 동일한 컴퓨터에서 실행 되기 때문에 로컬 백그라운드 작업으로 간주 됩니다.

1. 원격 작업을 관리 하려면 **job** cmdlet을 사용 합니다. 작업 개체가 원격 컴퓨터에 있기 때문에 작업 결과를 가져오기, 중지, 대기 또는 검색 하기 위해 원격 명령을 실행 해야 합니다.

   작업이 완료 되었는지 확인 하려면 명령을 사용 하 여 `Invoke-Command` `Get-Job` Server01 컴퓨터에 연결 된 PSSession에서 명령을 실행 합니다.

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   작업 개체를 반환합니다. 작업 개체의 **State** 속성은 명령이 성공적으로 완료 되었음을 보여 줍니다.

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. 작업 결과를 가져오려면 cmdlet을 사용 `Invoke-Command` 하 여 `Receive-Job` Server01 컴퓨터에 연결 된 PSSession에서 명령을 실행 합니다.

   다음 명령은 cmdlet을 사용 하 여 `Receive-Job` 작업의 결과를 가져옵니다. 세션 ID를 사용 하 여 작업을 식별 합니다. 이 명령은 작업 결과를 `$results` 변수에 저장 합니다. 의 Keep 매개 변수를 사용 하 여 `Receive-Job` 결과를 원격 컴퓨터의 작업 캐시에 보관 합니다.

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   로컬 또는 원격 컴퓨터의 파일로 결과를 리디렉션할 수도 있습니다.
   다음 명령은 리디렉션 연산자를 사용 하 여 Server01 컴퓨터의 파일에 결과를 저장 합니다.

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a>분리 된 프로세스로 실행 하는 방법

앞서 언급 했 듯이 부모 세션이 종료 되 면 실행 중인 모든 자식 작업은 자식 프로세스와 함께 종료 됩니다. 로컬 컴퓨터에서 원격을 사용 하 여 현재 PowerShell 세션에 연결 되지 않은 작업을 실행할 수 있습니다.

로컬 컴퓨터에서 새 PowerShell 세션을 만듭니다. `Invoke-Command`이 세션에서 작업을 시작 하는 데 사용 하는입니다. `Invoke-Command` 원격 세션의 연결을 끊고 부모 세션을 종료할 수 있습니다. 나중에 새 PowerShell 세션을 시작 하 고 이전에 연결이 끊어진 세션에 연결 하 여 작업 모니터링을 다시 시작할 수 있습니다. 그러나 해당 세션이 종료 되 면 원래 PowerShell 세션에 반환 된 모든 데이터가 손실 됩니다. 다시 연결할 때 연결 끊기 후에 생성 된 새 데이터 개체만 반환 됩니다.

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

이 예에서는 작업이 부모 PowerShell 세션에 계속 연결 되어 있습니다.
그러나 부모 세션은가 실행 되는 원래 PowerShell 세션이 아닙니다 `Invoke-Command` .

## <a name="see-also"></a>참고 항목

- [about_Jobs](about_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_Remote_Variables](about_Remote_Variables.md)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
