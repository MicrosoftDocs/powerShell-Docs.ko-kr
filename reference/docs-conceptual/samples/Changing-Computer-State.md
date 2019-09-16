---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 컴퓨터 상태 변경
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386292"
---
# <a name="changing-computer-state"></a><span data-ttu-id="73d42-103">컴퓨터 상태 변경</span><span class="sxs-lookup"><span data-stu-id="73d42-103">Changing Computer State</span></span>

<span data-ttu-id="73d42-104">Windows PowerShell에서 컴퓨터를 다시 설정하려면 표준 명령줄 도구 WMI 또는 CIM 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-104">To reset a computer in Windows PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span> <span data-ttu-id="73d42-105">도구를 실행하기 위해서만 Windows PowerShell을 사용하는 경우에도 Windows PowerShell에서 컴퓨터의 전원 상태를 변경하는 방법을 알면 Windows PowerShell에서 외부 도구를 사용하는 방법에 대한 몇 가지 중요한 세부 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="73d42-106">컴퓨터 잠금</span><span class="sxs-lookup"><span data-stu-id="73d42-106">Locking a Computer</span></span>

<span data-ttu-id="73d42-107">사용 가능한 표준 도구를 통해 직접 컴퓨터를 잠그는 유일한 방법은 **user32.dll**에서 **LockWorkstation()** 함수를 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="73d42-108">이 명령은 워크스테이션을 즉시 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="73d42-109">Windows Dll을 실행(및 반복 사용을 위해 해당 라이브러리 저장)하여 Windows 관리 함수 라이브러리인 user32.dll을 실행하는 *rundll32.exe*가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="73d42-110">Windows XP 등에서 빠른 사용자 전환이 사용되는 동안 워크스테이션을 잠그면 컴퓨터는 현재 사용자의 화면 보호기를 시작하지 않고 사용자 로그온 화면을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="73d42-111">터미널 서버에서 특정 세션을 종료하려면 **tsshutdn.exe** 명령줄 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="73d42-112">현재 세션 로그오프</span><span class="sxs-lookup"><span data-stu-id="73d42-112">Logging Off the Current Session</span></span>

<span data-ttu-id="73d42-113">여러 가지 방법을 사용하여 로컬 시스템에서 세션을 로그오프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="73d42-114">가장 간단한 방법은 원격 데스크톱/터미널 서비스 명령줄 도구인 **logoff.exe**를 사용하는 것입니다. 자세한 내용을 보려면 Windows PowerShell 프롬프트에서 **logoff /?** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="73d42-115">현재 활성 세션을 로그오프하려면 인수 없이 **logoff**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="73d42-116">**shutdown.exe** 도구와 해당 로그오프 옵션을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="73d42-117">또 하나의 옵션은 WMI를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-117">Another option is to use WMI.</span></span> <span data-ttu-id="73d42-118">Win32_OperatingSystem 클래스에는 Win32Shutdown 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="73d42-119">0 플래그로 메서드를 호출하면 로그오프가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="73d42-120">자세한 내용을 보고 Win32Shutdown 메서드의 다른 기능을 찾으려면 MSDN에서 "Win32_OperatingSystem 클래스의 Win32Shutdown 메서드"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73d42-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

<span data-ttu-id="73d42-121">마지막으로 앞서 WMI 방법에서 설명한 것과 마찬가지로 CIM을 Win32_OperatingSystem 클래스와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-121">Finally you can use CIM with the same Win32_OperatingSystem class as described above in the WMI method.</span></span>

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="73d42-122">컴퓨터 종료 또는 다시 시작</span><span class="sxs-lookup"><span data-stu-id="73d42-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="73d42-123">컴퓨터 종료 및 다시 시작은 일반적으로 동일한 유형의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="73d42-124">컴퓨터를 종료하는 도구는 일반적으로 다시 시작하며, 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="73d42-125">Windows PowerShell에서 컴퓨터를 다시 시작하는 두 가지 간단한 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-125">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="73d42-126">Tsshutdn.exe 또는 Shutdown.exe 중 하나와 적절한 인수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-126">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="73d42-127">**tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="73d42-127">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="73d42-128">또는 **shutdown.exe /?** 를 통해 자세한 사용 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-128">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="73d42-129">Windows PowerShell에서 직접 종료 및 다시 시작 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-129">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="73d42-130">컴퓨터를 종료하려면 Stop-Computer 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-130">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="73d42-131">운영 체제를 다시 시작하려면 Restart-Computer 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-131">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="73d42-132">컴퓨터를 강제로 즉시 다시 시작하려면 -Force 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73d42-132">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
