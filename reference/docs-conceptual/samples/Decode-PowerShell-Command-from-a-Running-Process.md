---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: 실행 중인 프로세스에서 PowerShell 명령 디코딩
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680763"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>실행 중인 프로세스에서 PowerShell 명령 디코딩

때때로 PowerShell 프로세스를 실행 하는 많은 양의 리소스를 차지 하는 할 수 있습니다.
이 프로세스의 컨텍스트에서 실행 될 수는 [작업 스케줄러][] 작업 또는 [SQL Server 에이전트][] 작업 합니다. 실행 중인 PowerShell 프로세스를 여러 개 있는를 프로세스 문제를 나타내는 알기가 어려울 수 있습니다. 이 문서에서는 PowerShell 프로세스를 현재 실행 중인 스크립트 블록을 디코딩하는 방법을 보여 줍니다.

## <a name="create-a-long-running-process"></a>장기 실행 프로세스 만들기

이 시나리오를 보여 주기 위해 새 PowerShell 창을 열고 다음 코드를 실행 합니다. 10 분 동안 1 분 마다 숫자를 출력 하는 PowerShell 명령을 실행 합니다.

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a>프로세스 뷰

PowerShell에서 실행 되는 명령의 본문에 저장 됩니다는 **명령줄** 의 속성을 [Win32_Process][] 클래스입니다. 명령이 있는 경우는 [명령 인코딩된][]의 **명령줄** 속성 "EncodedCommand" 문자열을 포함 합니다. 이 정보를 사용 하는 인코딩된 명령을 다음 프로세스를 통해 난독 처리가 취소 될 수 있습니다.

관리자 권한으로 PowerShell을 시작 합니다. PowerShell 관리자 권한으로 실행 되 고 있는지 중요 한 것이 고, 그렇지 없는 결과가 반환 됩니다 실행 중인 프로세스를 쿼리 하는 경우.

모든 PowerShell 프로세스에는 인코딩된 명령을 가져오려면 다음 명령을 실행 합니다.

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

다음 명령은 인코딩된 명령과 프로세스 ID를 포함 하는 사용자 지정 PowerShell 개체를 만듭니다.

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

이제 인코딩된 명령을 디코딩할 수 있습니다. 다음 코드 조각은 명령 세부 정보 개체를 반복 인코딩된 명령 디코딩하고 디코딩된 명령을 다시 추가로 조사 하기 위해 개체에 추가 합니다.

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

이제 디코딩된 command 속성을 선택 하 여 디코딩된 명령을 검토할 수 있습니다.

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[작업 스케줄러]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server 에이전트]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[명령 인코딩된]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
