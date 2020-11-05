---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: PowerShell 스크립트 디버깅의 향상된 기능
description: WMF 5.0은 Windows PowerShell에 새 디버깅 기능을 추가합니다.
ms.openlocfilehash: 5703343e1b85024931638e8b04a09f7208ea123c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646731"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="f6022-104">PowerShell 스크립트 디버깅의 향상된 기능</span><span class="sxs-lookup"><span data-stu-id="f6022-104">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="f6022-105">PowerShell 5.0에는 디버깅 환경을 개선하는 여러 향상된 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-105">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="f6022-106">모두 중단</span><span class="sxs-lookup"><span data-stu-id="f6022-106">Break All</span></span>

<span data-ttu-id="f6022-107">이제 PowerShell 콘솔 및 PowerShell ISE를 사용하면 스크립트를 실행하기 위해 디버거를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-107">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="f6022-108">이 기능은 로컬 및 원격 세션에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-108">This works in both local and remote sessions.</span></span>

<span data-ttu-id="f6022-109">콘솔에서 <kbd>Ctrl</kbd>+<kbd>Break</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-109">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="f6022-110">ISE에서 <kbd>Ctrl</kbd>+<kbd>B</kbd>를 누르거나 **디버그 -> 모두 중단** 메뉴 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-110">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="f6022-111">PowerShell ISE에서 원격 디버깅 및 원격 파일 편집</span><span class="sxs-lookup"><span data-stu-id="f6022-111">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="f6022-112">PowerShell ISE를 사용하면 PSEdit 명령을 실행하여 원격 세션에서 파일을 열고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-112">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="f6022-113">예를 들어 다음과 같이 원격 세션의 명령줄에서 파일을 열어 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-113">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="f6022-114">또한 중단점을 누르면 PowerShell ISE에서 자동으로 열리는 원격 파일에서 편집하고 변경 내용을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-114">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="f6022-115">이제 원격 컴퓨터에서 실행되는 스크립트 파일을 디버그하고 파일을 편집하여 오류를 해결한 다음 수정된 스크립트를 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-115">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="f6022-116">고급 스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="f6022-116">Advanced Script Debugging</span></span>

<span data-ttu-id="f6022-117">PowerShell을 로드한 로컬 컴퓨터 프로세스에 연결하고 해당 프로세스에서 임의 runspace를 디버그할 수 있는 새로운 고급 디버깅 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-117">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="f6022-118">Runspace 디버깅</span><span class="sxs-lookup"><span data-stu-id="f6022-118">Runspace Debugging</span></span>

<span data-ttu-id="f6022-119">프로세스의 현재 runspace를 나열하고 스크립트 디버깅을 위해 해당 runspace에 PowerShell 콘솔이나 PowerShell ISE 디버거를 연결할 수 있는 새로운 cmdlet이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-119">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="f6022-120">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="f6022-120">Get-Runspace</span></span>
- <span data-ttu-id="f6022-121">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="f6022-121">Debug-Runspace</span></span>
- <span data-ttu-id="f6022-122">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f6022-122">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="f6022-123">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f6022-123">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="f6022-124">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f6022-124">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="f6022-125">PowerShell을 호스트하는 프로세스에 연결</span><span class="sxs-lookup"><span data-stu-id="f6022-125">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="f6022-126">이제 PowerShell이 로드된 모든 컴퓨터 프로세스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-126">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="f6022-127">호스트 프로세스를 통해 대화형 세션을 시작하여 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f6022-127">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="f6022-128">자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6022-128">For more information, see:</span></span>

- [<span data-ttu-id="f6022-129">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f6022-129">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="f6022-130">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f6022-130">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
