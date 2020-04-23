---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Process Cmdlet으로 프로세스 관리
ms.openlocfilehash: 8de0cbae508958bf7970ce69e03257ea0a8dca6f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870747"
---
# <a name="managing-processes-with-process-cmdlets"></a>Process Cmdlet으로 프로세스 관리

Windows PowerShell에서 Process cmdlet을 사용하여 Windows PowerShell의 로컬 및 원격 프로세스를 관리할 수 있습니다.

## <a name="getting-processes-get-process"></a>프로세스 가져오기(Get-Process)

로컬 컴퓨터에서 실행 중인 프로세스를 가져오려면 **Get-Process**를 매개 변수 없이 실행합니다.

프로세스 이름 또는 프로세스 ID를 지정하여 특정 프로세스를 가져올 수 있습니다. 다음 명령은 Idle 프로세스를 가져옵니다.

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

일반적으로 cmdlet이 데이터를 반환하지 않아도 오류 메시지가 나타나지 않지만 ProcessId를 사용하여 프로세스를 지정한 경우 **Get-Process**가 일치하는 항목을 찾지 못하면 오류 메시지가 나타납니다. 이 cmdlet의 기본 목적이 실행 중인 프로세스를 검색하는 것이기 때문입니다. 해당 Id를 가진 프로세스가 없으면 Id가 잘못되었거나 해당 프로세스가 이미 종료된 것일 수 있습니다.

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Get-Process cmdlet의 Name 매개 변수를 사용하면 프로세스 이름을 기반으로 프로세서의 하위 집합을 지정할 수 있습니다. Name 매개 변수는 여러 개의 이름을 쉼표로 구분된 목록으로 받아들일 수 있으며 와일드카드 사용을 지원하기 때문에 사용자는 이름 패턴을 입력할 수 있습니다.

예를 들어 다음 명령은 이름이 "ex"로 시작되는 프로세스를 가져옵니다.

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

.NET System.Diagnostics.Process 클래스는 Windows PowerShell 프로세스의 기초이므로 System.Diagnostics.Process가 사용하는 일부 규칙을 따릅니다. 이러한 규칙 중 하나는 실행 파일의 프로세스 이름에 ".exe" 확장명을 포함하지 않는 것입니다.

또한 **Get-Process**는 Name 매개 변수에 대해 여러 값을 허용합니다.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Get-Process의 ComputerName 매개 변수를 사용하여 원격 컴퓨터의 프로세스를 가져올 수 있습니다. 예를 들어 다음 명령은 로컬 컴퓨터("localhost"로 표현됨)에 있는 PowerShell 프로세스와 두 개의 원격 컴퓨터에 있는 PowerShell 프로세스를 가져옵니다.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

이 표시에서는 컴퓨터 이름이 분명히 나타나지 않지만 Get-Process가 반환하는 프로세스 개체의 MachineName 속성에 저장됩니다. 다음 명령은 Format-Table cmdlet을 사용하여 프로세스 개체의 프로세스 ID, ProcessName 및 MachineName(ComputerName) 속성을 표시합니다.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 |
  Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

더욱 복잡한 이 명령은 MachineName 속성을 표준 Get-Process 표시에 추가합니다.

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>프로세스 중지(Stop-Process)

Windows PowerShell에서는 다양한 방법으로 프로세스를 표시할 수 있지만 프로세스 중지의 경우는 어떨까요?

**Stop-Process** cmdlet은 Name 또는 Id를 사용하여 중지할 프로세스를 지정합니다. 프로세스를 중지할 수 있는지 여부는 사용 권한에 의해 결정됩니다. 일부 프로세스는 중지할 수 없습니다. 예를 들어 유휴 프로세스를 중지하려고 하면 다음과 같은 오류 메시지가 나타납니다.

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

**Confirm** 매개 변수를 사용하여 강제로 확인하도록 지정할 수도 있습니다. 이 매개 변수는 프로세스 이름을 지정할 때 와일드카드를 사용할 경우 원하지 않는 프로세스가 중지될 수 있으므로 특히 유용합니다.

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

일부 개체 필터링 cmdlet을 사용하면 복잡한 프로세스 조작이 가능합니다. 프로세스 개체에는 더 이상 응답이 없을 때 true인 응답 속성이 있으므로 다음 명령을 사용하여 응답이 없는 모든 애플리케이션을 중지할 수 있습니다.

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

위와 동일한 방법을 다른 경우에 사용할 수도 있습니다. 예를 들어 다른 애플리케이션을 시작하면 보조 알림 영역 애플리케이션이 자동으로 실행된다고 가정할 경우 이 보조 알림 영역 응용 프로그램이 터미널 서비스 세션에서 올바로 작동하지 않는 것을 알았지만 실제 컴퓨터 콘솔에서 실행되는 세션에서 이 응용 프로그램을 계속 실행할 수 있습니다. 실제 컴퓨터의 데스크톱에 연결된 세션에는 항상 세션 ID로 0이 지정되므로 다음과 같이 **Where-Object**와 **SessionId** 프로세스를 사용하여 다른 세션에 있는 프로세스의 인스턴스를 모두 중지할 수 있습니다.

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Stop-Process cmdlet에는 ComputerName 매개 변수가 없습니다. 따라서 원격 컴퓨터에서 프로세스 중지 명령을 실행하려면 Invoke-Command cmdlet을 사용해야 합니다. 예를 들어 Server01 원격 컴퓨터에서 PowerShell 프로세스를 중지하려면 다음과 같이 입력합니다.

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>다른 모든 Windows PowerShell 세션 중지

경우에 따라 현재 세션을 제외하고 실행 중인 다른 모든 Windows PowerShell 세션을 중지할 수 있는 기능이 유용할 수 있습니다. 세션에서 너무 많은 리소스를 사용하고 있거나 세션에 액세스할 수 없으면(원격에서 실행 중이거나 다른 데스크톱 세션에서 실행 중인 경우) 세션을 직접 중지하지 못할 수도 있습니다. 그러나 실행 중인 세션을 모두 중지하려고 하면 현재 세션이 대신 종료될 수 있습니다.

각 Windows PowerShell 세션에는 Windows PowerShell 프로세스의 Id가 들어 있는 환경 변수 PID가 있습니다. 각 세션의 Id에 대해 $PID를 확인하고 다른 Id를 가진 Windows PowerShell 세션만 종료할 수 있습니다. 다음 파이프라인 명령은 이 작업을 수행하고 종료된 세션의 목록을 반환합니다. 이 명령이 종료된 세션의 목록을 반환하는 것은 **PassThru** 매개 변수를 사용하기 때문입니다.

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a>프로세스 시작, 디버그 및 대기

Windows PowerShell에는 프로세스를 시작(또는 다시 시작)하고, 프로세스를 디버그하고, 명령을 실행하기 전에 프로세스의 완료를 기다리는 cmdlet도 함께 제공됩니다. 이러한 cmdlet에 대한 자세한 내용은 각 cmdlet의 cmdlet 도움말 항목을 참조하세요.

## <a name="see-also"></a>참고 항목

- [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)
- [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)
- [Start-Process](/powershell/module/Microsoft.PowerShell.Management/Start-Process)
- [Wait-Process](/powershell/module/Microsoft.PowerShell.Management/Wait-Process)
- [Debug-Process](/powershell/module/Microsoft.PowerShell.Management/Debug-Process)
- [Invoke-Command](/powershell/module/Microsoft.PowerShell.Core/Invoke-Command)
