---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: PowerShell 스크립트 디버깅의 향상된 기능
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808949"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="6bef4-103">PowerShell 스크립트 디버깅의 향상된 기능</span><span class="sxs-lookup"><span data-stu-id="6bef4-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="6bef4-104">PowerShell 5.0에는 디버깅 환경을 개선하는 여러 향상된 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="6bef4-105">모두 중단</span><span class="sxs-lookup"><span data-stu-id="6bef4-105">Break All</span></span>

<span data-ttu-id="6bef4-106">이제 PowerShell 콘솔 및 PowerShell ISE를 사용하면 스크립트를 실행하기 위해 디버거를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="6bef4-107">이 기능은 로컬 및 원격 세션에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="6bef4-108">콘솔에서 <kbd>Ctrl</kbd>+<kbd>Break</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="6bef4-109">ISE에서 <kbd>Ctrl</kbd>+<kbd>B</kbd>를 누르거나 **디버그 -> 모두 중단** 메뉴 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="6bef4-110">PowerShell ISE에서 원격 디버깅 및 원격 파일 편집</span><span class="sxs-lookup"><span data-stu-id="6bef4-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="6bef4-111">PowerShell ISE를 사용하면 PSEdit 명령을 실행하여 원격 세션에서 파일을 열고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="6bef4-112">예를 들어 다음과 같이 원격 세션의 명령줄에서 파일을 열어 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="6bef4-113">또한 중단점을 누르면 PowerShell ISE에서 자동으로 열리는 원격 파일에서 편집하고 변경 내용을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="6bef4-114">이제 원격 컴퓨터에서 실행되는 스크립트 파일을 디버그하고 파일을 편집하여 오류를 해결한 다음 수정된 스크립트를 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="6bef4-115">고급 스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="6bef4-115">Advanced Script Debugging</span></span>

<span data-ttu-id="6bef4-116">PowerShell을 로드한 로컬 컴퓨터 프로세스에 연결하고 해당 프로세스에서 임의 runspace를 디버그할 수 있는 새로운 고급 디버깅 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="6bef4-117">Runspace 디버깅</span><span class="sxs-lookup"><span data-stu-id="6bef4-117">Runspace Debugging</span></span>

<span data-ttu-id="6bef4-118">프로세스의 현재 runspace를 나열하고 스크립트 디버깅을 위해 해당 runspace에 PowerShell 콘솔이나 PowerShell ISE 디버거를 연결할 수 있는 새로운 cmdlet이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="6bef4-119">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="6bef4-119">Get-Runspace</span></span>
- <span data-ttu-id="6bef4-120">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="6bef4-120">Debug-Runspace</span></span>
- <span data-ttu-id="6bef4-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="6bef4-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="6bef4-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="6bef4-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="6bef4-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="6bef4-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="6bef4-124">PowerShell을 호스트하는 프로세스에 연결</span><span class="sxs-lookup"><span data-stu-id="6bef4-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="6bef4-125">이제 PowerShell이 로드된 모든 컴퓨터 프로세스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="6bef4-126">호스트 프로세스를 통해 대화형 세션을 시작하여 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6bef4-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="6bef4-127">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bef4-127">For more information, see:</span></span>

- [<span data-ttu-id="6bef4-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="6bef4-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="6bef4-129">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="6bef4-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
