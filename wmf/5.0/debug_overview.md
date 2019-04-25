---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058667"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="58c10-102">PowerShell 스크립트 디버깅의 향상된 기능</span><span class="sxs-lookup"><span data-stu-id="58c10-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="58c10-103">PowerShell 5.0에서는 디버깅 환경을 개선하기 위해 다양한 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="58c10-104">모두 중단</span><span class="sxs-lookup"><span data-stu-id="58c10-104">Break All</span></span>

<span data-ttu-id="58c10-105">이제 PowerShell 콘솔 및 Windows PowerShell ISE를 사용하면 스크립트를 실행하기 위해 디버거를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="58c10-106">이 기능은 로컬 및 원격 세션에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="58c10-107">콘솔에서 **Ctrl+Break**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="58c10-108">ISE에서 **Ctrl+B**를 누르거나 **디버그 -> 모두 중단** 메뉴 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="58c10-109">Windows PowerShell ISE에서 원격 디버깅 및 원격 파일 편집</span><span class="sxs-lookup"><span data-stu-id="58c10-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="58c10-110">Windows PowerShell ISE를 사용하면 PSEdit 명령을 실행하여 원격 세션에서 파일을 열고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="58c10-111">예를 들어 다음과 같이 원격 세션의 명령줄에서 파일을 열어 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="58c10-112">또한 중단점을 누르면 Windows PowerShell ISE에서 자동으로 열리는 원격 파일에서 편집하고 변경 내용을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="58c10-113">이제 원격 컴퓨터에서 실행되는 스크립트 파일을 디버그하고 파일을 편집하여 오류를 해결한 다음 수정된 스크립트를 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="58c10-114">고급 스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="58c10-114">Advanced Script Debugging</span></span>

<span data-ttu-id="58c10-115">Windows PowerShell을 로드한 로컬 컴퓨터 프로세스에 연결하고 해당 프로세스에서 임의 runspace를 디버그할 수 있는 새로운 고급 디버깅 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="58c10-116">Runspace 디버깅</span><span class="sxs-lookup"><span data-stu-id="58c10-116">Runspace Debugging</span></span>

<span data-ttu-id="58c10-117">프로세스의 현재 runspace를 나열하고 스크립트 디버깅을 위해 해당 runspace에 Windows PowerShell 콘솔이나 ISE 디버거를 연결할 수 있는 새로운 cmdlet이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="58c10-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="58c10-118">Get-Runspace</span></span>
-   <span data-ttu-id="58c10-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="58c10-119">Debug-Runspace</span></span>
-   <span data-ttu-id="58c10-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="58c10-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="58c10-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="58c10-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="58c10-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="58c10-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="58c10-123">PowerShell을 호스트하는 프로세스에 연결</span><span class="sxs-lookup"><span data-stu-id="58c10-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="58c10-124">이제 Windows PowerShell이 로드된 모든 컴퓨터 프로세스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="58c10-125">Enter-PSSession cmdlet을 실행하여 대화형 원격 세션을 시작하는 방법과 유사하게 프로세스에서 대화형 세션을 시작하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="58c10-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="58c10-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="58c10-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="58c10-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="58c10-127">Exit-PSHostProcess</span></span>
