---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: 실행 중인 프로세스에서 PowerShell 명령 디코딩
author: randomnote1
ms.openlocfilehash: a6c01d8edf67aba6c47350a97cc0ceec4801ad29
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470974"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="d991a-103">실행 중인 프로세스에서 PowerShell 명령 디코딩</span><span class="sxs-lookup"><span data-stu-id="d991a-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="d991a-104">때때로 많은 리소스를 점유 중인 PowerShell 프로세스가 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="d991a-105">이 프로세스는 [작업 스케줄러][] 작업이나 [SQL Server 에이전트][] 작업의 컨텍스트에서 실행되고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="d991a-106">여러 PowerShell 프로세스가 실행되는 경우 어떤 프로세스가 문제를 나타내지 알기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="d991a-107">이 문서에서는 PowerShell 프로세스가 현재 실행 중인 스크립트 블록을 디코드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="d991a-108">장기 실행 프로세스 만들기</span><span class="sxs-lookup"><span data-stu-id="d991a-108">Create a long running process</span></span>

<span data-ttu-id="d991a-109">이 시나리오를 설명하기 위해 새 PowerShell 창을 열고 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="d991a-110">이 코드는 10분 동안 1분마다 숫자를 출력하는 PowerShell 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

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

## <a name="view-the-process"></a><span data-ttu-id="d991a-111">프로세스 보기</span><span class="sxs-lookup"><span data-stu-id="d991a-111">View the process</span></span>

<span data-ttu-id="d991a-112">PowerShell이 실행 중인 명령의 본문은 [Win32_Process][] 클래스의 **CommandLine** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="d991a-113">명령이 인코딩된 명령인 경우 **CommandLine** 속성에는 문자열 "EncodedCommand"가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-113">If the command is an encoded command, the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="d991a-114">이 정보를 사용하면 다음 프로세스를 통해 인코딩된 명령의 난독 처리를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="d991a-115">관리자 권한으로 PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="d991a-116">PowerShell은 관리자 권한으로 실행 중이어야 합니다. 그렇지 않으면 실행 프로세스를 쿼리할 때 결과가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="d991a-117">다음 명령을 실행하여 인코딩된 명령이 있는 모든 PowerShell 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="d991a-118">다음 명령은 프로세스 ID 및 인코딩된 명령이 포함된 사용자 지정 PowerShell 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

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

<span data-ttu-id="d991a-119">이제 인코딩된 명령을 디코딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="d991a-120">다음 코드 조각은 명령 세부 정보 개체에서 반복되고, 인코딩된 명령을 디코드하고, 추가 조사를 위해 디코드된 명령을 다시 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

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

<span data-ttu-id="d991a-121">이제 디코드된 명령 속성을 선택하여 디코드된 명령을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d991a-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

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
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server 에이전트]: /sql/ssms/agent/sql-server-agent
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
