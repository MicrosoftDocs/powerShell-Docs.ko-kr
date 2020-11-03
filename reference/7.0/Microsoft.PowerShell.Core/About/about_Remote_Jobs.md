---
description: 원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 13202ae7b71512899b151c857760b40c3324260f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223778"
---
# <a name="about-remote-jobs"></a>원격 작업 정보

## <a name="short-description"></a>간단한 설명
원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법을 설명 합니다.

## <a name="detailed-description"></a>자세한 설명

백그라운드 작업은 현재 세션과 상호 작용 하지 않고 비동기적으로 실행 되는 명령입니다. 명령 프롬프트가 즉시 반환 되며 작업이 실행 되는 동안 세션을 계속 사용할 수 있습니다.

기본적으로 백그라운드 작업은 로컬 컴퓨터에서 실행 됩니다. 그러나 여러 가지 절차를 사용 하 여 원격 컴퓨터에서 백그라운드 작업을 실행할 수 있습니다.

이 항목에서는 원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법을 설명 합니다. 로컬 컴퓨터에서 백그라운드 작업을 실행 하는 방법에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요. 백그라운드 작업에 대 한 자세한 내용은 [about_Job_Details](about_Job_Details.md)를 참조 하세요.

## <a name="remote-background-jobs"></a>원격 백그라운드 작업

3 가지 방법을 사용 하 여 원격 컴퓨터에서 백그라운드 작업을 실행할 수 있습니다.

- 원격 컴퓨터와 대화형 세션을 시작 하 고 대화형 세션에서 작업을 시작 합니다. 모든 작업은 원격 컴퓨터에서 수행 되지만 절차는 로컬 작업 실행과 동일 합니다.

- 로컬 컴퓨터에 결과를 반환 하는 원격 컴퓨터에서 백그라운드 작업을 실행 합니다. 백그라운드 작업의 결과를 수집 하 고 로컬 컴퓨터의 중앙 위치에서 유지 관리 하려는 경우이 방법을 사용 합니다.

- 원격 컴퓨터에 대 한 결과를 유지 하는 원격 컴퓨터에서 백그라운드 작업을 실행 합니다. 작업 데이터가 원래 컴퓨터에서 더 안전 하 게 유지 되는 경우이 방법을 사용 합니다.

### <a name="start-a-background-job-in-an-interactive-session"></a>대화형 세션에서 백그라운드 작업 시작

원격 컴퓨터를 사용 하 여 대화형 세션을 시작한 다음 대화형 세션 중에 백그라운드 작업을 시작할 수 있습니다. 대화형 세션에 대 한 자세한 내용은 about_Remote를 참조 하 고 Enter-PSSession을 참조 하십시오.

대화형 세션에서 백그라운드 작업을 시작 하는 절차는 로컬 컴퓨터에서 백그라운드 작업을 시작 하는 절차와 거의 동일 합니다. 그러나 모든 작업은 로컬 컴퓨터가 아닌 원격 컴퓨터에서 발생 합니다.

#### <a name="step-1-enter-pssession"></a>1 단계: ENTER-PSSESSION

Enter-PSSession cmdlet을 사용 하 여 원격 컴퓨터와의 대화형 세션을 시작 합니다. Enter-PSSession의 ComputerName 매개 변수를 사용 하 여 대화형 세션에 대 한 임시 연결을 설정할 수 있습니다. 또는 Session 매개 변수를 사용 하 여 PowerShell 세션 (PSSession)에서 대화형 세션을 실행할 수 있습니다.

다음 명령은 Server01 컴퓨터에서 대화형 세션을 시작 합니다.

```powershell
C:\PS> Enter-PSSession -computername Server01
```

명령 프롬프트가 변경 되어 이제 Server01 컴퓨터에 연결 되어 있음을 보여 줍니다.

```
Server01\C:>
```

#### <a name="step-2-start-job"></a>2 단계: 작업 시작

세션에서 백그라운드 작업을 시작 하려면 Start-Job cmdlet을 사용 합니다.

다음 명령은 Server01 컴퓨터의 Windows PowerShell 이벤트 로그에 있는 이벤트를 가져오는 백그라운드 작업을 실행 합니다. Start-Job cmdlet은 작업을 나타내는 개체를 반환 합니다.

이 명령은 작업 변수에 작업 개체를 저장 \$ 합니다.

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

작업이 실행 되는 동안 대화형 세션을 사용 하 여 다른 백그라운드 작업을 비롯 한 다른 명령을 실행할 수 있습니다. 그러나 작업이 완료 될 때까지 대화형 세션을 열어 두어야 합니다. 세션을 종료 하면 작업이 중단 되 고 결과가 손실 됩니다.

#### <a name="step-3-get-job"></a>3 단계: 작업 가져오기

작업이 완료 되었는지 확인 하려면 작업 변수의 값을 표시 \$ 하거나 Get-Job cmdlet을 사용 하 여 작업을 가져옵니다. 다음 명령은 Get-Job cmdlet을 사용 하 여 작업을 표시 합니다.

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

Get-Job 출력은 작업이 시작 되어 동일한 컴퓨터에서 실행 되 고 있으므로 (이 경우 Server01) "localhost" 컴퓨터에서 작업이 실행 되 고 있음을 보여 줍니다.

#### <a name="step-4-receive-job"></a>4 단계: 수신 작업

작업의 결과를 가져오려면 Receive-Job cmdlet을 사용 합니다. 대화형 세션에서 결과를 표시 하거나 원격 컴퓨터의 파일에 저장할 수 있습니다. 다음 명령은 $job 변수의 작업 결과를 가져옵니다. 이 명령은 리디렉션 연산자 (>)를 사용 하 여 작업 결과를 Server01 컴퓨터의 PsLog.txt 파일에 저장 합니다.

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a>5 단계: 종료 PSSESSION

대화형 세션을 종료 하려면 Exit-PSSession cmdlet을 사용 합니다. 명령 프롬프트가 변경 되어 로컬 컴퓨터의 원래 세션으로 돌아갑니다.

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a>6 단계: 명령 호출: GET 콘텐츠

Server01 컴퓨터에서 언제 든 지 PsLog.txt 파일의 콘텐츠를 보려면 다른 대화형 세션을 시작 하거나 원격 명령을 실행 합니다. 여러 명령을 사용 하 여 PsLog.txt 파일의 데이터를 조사 하 고 관리 하려는 경우이 유형의 명령은 PSSession (영구 연결)에서 가장 잘 실행 됩니다. Pssession에 대 한 자세한 내용은 about_PSSessions를 참조 하세요.

다음 명령은 New-PSSession cmdlet을 사용 하 여 Server01 컴퓨터에 연결 된 PSSession을 만들고, Invoke-Command cmdlet을 사용 하 여 PSSession에서 Get-Content 명령을 실행 하 여 파일의 내용을 확인 합니다.

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>로컬 컴퓨터 ASJOB에 결과를 반환 하는 원격 작업을 시작 합니다. \(\)

로컬 컴퓨터에 명령 결과를 반환 하는 원격 컴퓨터에서 백그라운드 작업을 시작 하려면 Invoke-Command cmdlet과 같은 cmdlet의 AsJob 매개 변수를 사용 합니다.

AsJob 매개 변수를 사용 하는 경우 작업이 원격 컴퓨터에서 실행 되는 경우에도 실제로 작업 개체는 로컬 컴퓨터에 만들어집니다. 작업이 완료 되 면 결과는 로컬 컴퓨터에 반환 됩니다.

작업 명사 (Job cmdlet)를 포함 하는 cmdlet을 사용 하 여 모든 cmdlet에 의해 생성 된 작업을 관리할 수 있습니다. AsJob 매개 변수를 포함 하는 많은 cmdlet은 PowerShell 원격을 사용 하지 않으므로 원격 기능을 사용 하도록 구성 되지 않고 원격 기능에 대 한 요구 사항을 충족 하지 않는 컴퓨터 에서도 사용할 수 있습니다.

#### <a name="step-1-invoke-command--asjob"></a>1 단계: 명령 호출-ASJOB

다음 명령은 Invoke-Command의 AsJob 매개 변수를 사용 하 여 Server01 컴퓨터에서 백그라운드 작업을 시작 합니다. 이 작업은 시스템 로그에서 이벤트를 가져오는 Get-Eventlog 명령을 실행합니다. JobName 매개 변수를 사용 하 여 작업에 표시 이름을 할당할 수 있습니다.

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

명령의 결과는 다음 샘플 출력과 유사 합니다.

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

AsJob 매개 변수를 사용 하는 경우 Invoke-Command는 Start-Job 반환 하는 것과 동일한 유형의 작업 개체를 반환 합니다. 작업 개체를 변수에 저장 하거나 Get-Job 명령을 사용 하 여 작업을 가져올 수 있습니다.

Location 속성의 값은 작업이 Server01 컴퓨터에서 실행 되었음을 보여 줍니다.

#### <a name="step-2-get-job"></a>2 단계: 작업 가져오기

Invoke-Command cmdlet의 AsJob 매개 변수를 사용 하 여 시작 된 작업을 관리 하려면 Job cmdlet을 사용 합니다. 원격 작업을 나타내는 작업 개체는 로컬 컴퓨터에 있기 때문에 작업을 관리 하기 위해 원격 명령을 실행할 필요가 없습니다.

작업이 완료 되었는지 여부를 확인 하려면 Get-Job 명령을 사용 합니다. 다음 명령은 현재 세션에서 시작 된 모든 작업을 가져옵니다.

```powershell
get-job
```

원격 작업이 현재 세션에서 시작 되었기 때문에 로컬 Get-Job 명령은 작업을 가져옵니다. 작업 개체의 State 속성은 명령이 성공적으로 완료 되었음을 보여 줍니다.

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a>3 단계: 수신 작업

작업의 결과를 가져오려면 Receive-Job cmdlet을 사용 합니다. 작업 결과가 작업 개체가 있는 컴퓨터에 자동으로 반환 되므로 로컬 Receive-Job 명령을 사용 하 여 결과를 가져올 수 있습니다.

다음 명령은 Receive-Job cmdlet을 사용 하 여 작업의 결과를 가져옵니다. 세션 ID를 사용 하 여 작업을 식별 합니다. 이 명령은 $results 변수에 작업 결과를 저장 합니다. 또한 결과를 파일로 리디렉션할 수 있습니다.

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>원격 컴퓨터에 결과를 보관 하는 원격 작업 시작

원격 컴퓨터에서 명령 결과를 유지 하는 원격 컴퓨터에서 백그라운드 작업을 시작 하려면 Invoke-Command cmdlet을 사용 하 여 원격 컴퓨터에서 Start-Job 명령을 실행 합니다. 이 메서드를 사용 하 여 여러 컴퓨터에서 백그라운드 작업을 실행할 수 있습니다.

Start-Job 명령을 원격으로 실행 하는 경우 작업 개체가 원격 컴퓨터에 만들어지고 작업 결과가 원격 컴퓨터에서 유지 관리 됩니다.
작업의 관점에서 보면 모든 작업은 로컬입니다. 원격 컴퓨터에서 로컬 작업을 관리 하기 위해 원격으로 명령을 실행 하는 것입니다.

#### <a name="step-1-invoke-command-start-job"></a>1 단계: 명령 시작-작업

Invoke-Command cmdlet을 사용 하 여 원격 컴퓨터에서 Start-Job 명령을 실행 합니다.

이 명령에는 PSSession (영구 연결)이 필요 합니다. Invoke-Command의 ComputerName 매개 변수를 사용 하 여 임시 연결을 설정 하는 경우 작업 개체가 반환 될 때 Invoke-Command 명령이 완료 된 것으로 간주 됩니다. 결과적으로 임시 연결이 닫히고 작업이 취소 됩니다.

다음 명령은 New-PSSession cmdlet을 사용 하 여 Server01 컴퓨터에 연결 된 PSSession을 만듭니다. 이 명령은 PSSession을 \$ s 변수에 저장 합니다.

```powershell
$s = new-pssession -computername Server01
```

다음 명령은 Invoke-Command cmdlet을 사용 하 여 PSSession에서 Start-Job 명령을 실행 합니다. Start-Job 명령과 Get-Eventlog 명령은 중괄호로 묶여 있습니다.

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

결과는 다음 예제 출력과 유사 합니다.

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

Start-Job 명령을 원격으로 실행 하는 경우 Invoke-Command는 Start-Job 반환 하는 것과 동일한 유형의 작업 개체를 반환 합니다. 작업 개체를 변수에 저장 하거나 Get-Job 명령을 사용 하 여 작업을 가져올 수 있습니다.

Location 속성의 값은 작업이 Server01 컴퓨터에서 실행 된 경우에도 "LocalHost" 라는 로컬 컴퓨터에서 실행 된 것을 보여 줍니다. 작업 개체는 Server01 컴퓨터에 생성 되 고 작업은 동일한 컴퓨터에서 실행 되기 때문에 로컬 백그라운드 작업으로 간주 됩니다.

#### <a name="step-2-invoke-command-get-job"></a>2 단계: 명령 호출 가져오기

원격 백그라운드 작업을 관리 하려면 Job cmdlet을 사용 합니다. 작업 개체가 원격 컴퓨터에 있기 때문에 작업 결과를 가져오기, 중지, 대기 또는 검색 하기 위해 원격 명령을 실행 해야 합니다.

작업이 완료 되었는지 확인 하려면 Invoke-Command 명령을 사용 하 여 Server01 컴퓨터에 연결 된 PSSession에서 Get-Job 명령을 실행 합니다.

```powershell
invoke-command -session $s -scriptblock {get-job}
```

작업 개체를 반환합니다. 작업 개체의 State 속성은 명령이 성공적으로 완료 되었음을 보여 줍니다.

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a>3 단계: 명령 수신-작업

작업의 결과를 가져오려면 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에 연결 된 PSSession에서 Receive-Job 명령을 실행 합니다.

다음 명령은 Receive-Job cmdlet을 사용 하 여 작업의 결과를 가져옵니다. 세션 ID를 사용 하 여 작업을 식별 합니다. 이 명령은 결과 변수에 작업 결과를 저장 \$ 합니다. 이는 Receive-Job의 Keep 매개 변수를 사용 하 여 결과를 원격 컴퓨터의 작업 캐시에 보관 합니다.

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

로컬 또는 원격 컴퓨터의 파일로 결과를 리디렉션할 수도 있습니다.
다음 명령은 리디렉션 연산자를 사용 하 여 Server01 컴퓨터의 파일에 결과를 저장 합니다.

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a>참고 항목

[about_Jobs](about_Jobs.md)

[about_Job_Details](about_Job_Details.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)

[Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)

[Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)

[Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)

[Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
