---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 컴퓨터 상태 변경
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736916"
---
# <a name="changing-computer-state"></a><span data-ttu-id="f7806-103">컴퓨터 상태 변경</span><span class="sxs-lookup"><span data-stu-id="f7806-103">Changing Computer State</span></span>

<span data-ttu-id="f7806-104">PowerShell에서 컴퓨터를 다시 설정하려면 표준 명령줄 도구 WMI 또는 CIM 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-104">To reset a computer in PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span>
<span data-ttu-id="f7806-105">도구를 실행하기 위해서만 PowerShell을 사용하는 경우에도 PowerShell에서 컴퓨터의 전원 상태를 변경하는 방법을 알면 PowerShell에서 외부 도구를 사용하는 방법에 대한 몇 가지 중요한 세부 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-105">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="f7806-106">컴퓨터 잠금</span><span class="sxs-lookup"><span data-stu-id="f7806-106">Locking a Computer</span></span>

<span data-ttu-id="f7806-107">사용 가능한 표준 도구를 통해 직접 컴퓨터를 잠그는 유일한 방법은 **user32.dll**에서 **LockWorkstation()** 함수를 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="f7806-108">이 명령은 워크스테이션을 즉시 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="f7806-109">Windows Dll을 실행(및 반복 사용을 위해 해당 라이브러리 저장)하여 Windows 관리 함수 라이브러리인 `user32.dll`을 실행하는 **rundll32.exe**가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-109">It uses **rundll32.exe**, which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="f7806-110">Windows XP 등에서 빠른 사용자 전환이 사용되는 동안 워크스테이션을 잠그면 컴퓨터에서 현재 사용자의 화면 보호기가 시작되는 대신 사용자 로그온 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="f7806-111">터미널 서버에서 특정 세션을 종료하려면 **tsshutdn.exe** 명령줄 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="f7806-112">현재 세션 로그오프</span><span class="sxs-lookup"><span data-stu-id="f7806-112">Logging Off the Current Session</span></span>

<span data-ttu-id="f7806-113">여러 가지 방법을 사용하여 로컬 시스템에서 세션을 로그오프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="f7806-114">가장 간단한 방법은 원격 데스크톱/터미널 서비스 명령줄 도구인 **logoff.exe**를 사용하는 것입니다. 자세한 내용을 보려면 PowerShell 프롬프트에서 `logoff /?`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="f7806-115">현재 활성 세션을 로그오프하려면 인수 없이 `logoff`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-115">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="f7806-116">**shutdown.exe** 도구와 해당 로그오프 옵션을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="f7806-117">또 하나의 옵션은 WMI를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-117">Another option is to use WMI.</span></span> <span data-ttu-id="f7806-118">**Win32_OperatingSystem** 클래스에는 **Shutdown** 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-118">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="f7806-119">0 플래그로 메서드를 호출하면 로그오프가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-119">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="f7806-120">**Shutdown** 메서드에 대한 자세한 내용은 [Win32_OperatingSystem 클래스의 Shutdown 메서드](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7806-120">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="f7806-121">컴퓨터 종료 또는 다시 시작</span><span class="sxs-lookup"><span data-stu-id="f7806-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="f7806-122">컴퓨터 종료 및 다시 시작은 일반적으로 동일한 유형의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="f7806-123">컴퓨터를 종료하는 도구는 일반적으로 다시 시작하며, 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="f7806-124">PowerShell에서 컴퓨터를 다시 시작하는 두 가지 간단한 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-124">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="f7806-125">**tsshutdn.exe** 또는 **shutdown.exe** 중 하나와 적절한 인수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-125">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="f7806-126">`tsshutdn.exe /?` 또는 `shutdown.exe /?`에서 자세한 사용 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-126">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="f7806-127">PowerShell에서 직접 종료 및 다시 시작 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-127">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="f7806-128">컴퓨터를 종료하려면 Stop-Computer 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-128">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="f7806-129">운영 체제를 다시 시작하려면 Restart-Computer 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-129">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="f7806-130">컴퓨터를 강제로 즉시 다시 시작하려면 -Force 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7806-130">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
