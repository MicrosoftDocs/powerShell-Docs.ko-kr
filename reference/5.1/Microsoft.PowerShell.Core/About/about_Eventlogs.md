---
description: Windows powershell은 windows powershell 이벤트를 기록 하는 "Windows PowerShell" 이라는 Windows 이벤트 로그를 만듭니다. 이 로그는 이벤트 뷰어에서 볼 수도 있고 cmdlet과 같이 이벤트를 가져오는 cmdlet을 사용 하 여 볼 수도 있습니다 `Get-EventLog` . 기본적으로 Windows PowerShell 엔진 및 공급자 이벤트는 이벤트 로그에 기록 되지만 이벤트 로그 기본 설정 변수를 사용 하 여 이벤트 로그를 사용자 지정할 수 있습니다. 예를 들어 Windows PowerShell 명령에 대 한 이벤트를 추가할 수 있습니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223506"
---
# <a name="about-eventlogs"></a><span data-ttu-id="3e91e-107">Eventlogs 정보</span><span class="sxs-lookup"><span data-stu-id="3e91e-107">About Eventlogs</span></span>

## <a name="short-description"></a><span data-ttu-id="3e91e-108">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="3e91e-108">Short Description</span></span>

<span data-ttu-id="3e91e-109">Windows powershell은 windows powershell 이벤트를 기록 하는 "Windows PowerShell" 이라는 Windows 이벤트 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-109">Windows PowerShell creates a Windows event log that is named "Windows PowerShell" to record Windows PowerShell events.</span></span> <span data-ttu-id="3e91e-110">이 로그는 이벤트 뷰어에서 볼 수도 있고 cmdlet과 같이 이벤트를 가져오는 cmdlet을 사용 하 여 볼 수도 있습니다 `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="3e91e-110">You can view this log in Event Viewer or by using cmdlets that get events, such as the `Get-EventLog` cmdlet.</span></span> <span data-ttu-id="3e91e-111">기본적으로 Windows PowerShell 엔진 및 공급자 이벤트는 이벤트 로그에 기록 되지만 이벤트 로그 기본 설정 변수를 사용 하 여 이벤트 로그를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-111">By default, Windows PowerShell engine and provider events are recorded in the event log, but you can use the event log preference variables to customize the event log.</span></span> <span data-ttu-id="3e91e-112">예를 들어 Windows PowerShell 명령에 대 한 이벤트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-112">For example, you can add events about Windows PowerShell commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="3e91e-113">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="3e91e-113">Long Description</span></span>

<span data-ttu-id="3e91e-114">Windows PowerShell 이벤트 로그는 프로그램 엔진 시작 및 중지, Windows PowerShell 공급자 시작 및 중지와 같은 Windows PowerShell 작업에 대 한 세부 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-114">The Windows PowerShell event log records details of Windows PowerShell operations, such as starting and stopping the program engine and starting and stopping the Windows PowerShell providers.</span></span> <span data-ttu-id="3e91e-115">Windows PowerShell 명령에 대 한 세부 정보를 기록할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-115">You can also log details about Windows PowerShell commands.</span></span>

<span data-ttu-id="3e91e-116">Windows PowerShell 이벤트 로그는 응용 프로그램 및 서비스 로그 그룹에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-116">The Windows PowerShell event log is in the Application and Services Logs group.</span></span> <span data-ttu-id="3e91e-117">Windows PowerShell 로그는 Windows 이벤트 기술을 사용 하지 않는 클래식 이벤트 로그입니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-117">The Windows PowerShell log is a classic event log that does not use the Windows Eventing technology.</span></span> <span data-ttu-id="3e91e-118">로그를 보려면와 같은 클래식 이벤트 로그에 대해 디자인 된 cmdlet을 사용 `Get-EventLog` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-118">To view the log, use the cmdlets designed for classic event logs, such as `Get-EventLog`.</span></span>

## <a name="viewing-the-windows-powershell-event-log"></a><span data-ttu-id="3e91e-119">Windows PowerShell 이벤트 로그 보기</span><span class="sxs-lookup"><span data-stu-id="3e91e-119">Viewing the Windows PowerShell Event Log</span></span>

<span data-ttu-id="3e91e-120">이벤트 뷰어에서 또는 및 cmdlet을 사용 하 여 Windows PowerShell 이벤트 로그를 볼 수 있습니다 `Get-EventLog` `Get-WmiObject` .</span><span class="sxs-lookup"><span data-stu-id="3e91e-120">You can view the Windows PowerShell event log in Event Viewer or by using the `Get-EventLog` and `Get-WmiObject` cmdlets.</span></span> <span data-ttu-id="3e91e-121">Windows PowerShell 로그의 내용을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-121">To view the contents of the Windows PowerShell log, type:</span></span>

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

<span data-ttu-id="3e91e-122">이벤트 및 해당 속성을 검사 하려면 cmdlet, cmdlet `Sort-Object` `Group-Object` 및 `Format` 동사 (cmdlet)를 포함 하는 cmdlet을 사용 `Format` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-122">To examine the events and their properties, use the `Sort-Object` cmdlet, the `Group-Object` cmdlet, and the cmdlets that contain the `Format` verb (the `Format` cmdlets).</span></span>

<span data-ttu-id="3e91e-123">예를 들어 이벤트 ID 별로 그룹화 된 로그의 이벤트를 보려면 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-123">For example, to view the events in the log grouped by the event ID, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

<span data-ttu-id="3e91e-124">또는 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-124">Or, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

<span data-ttu-id="3e91e-125">모든 클래식 이벤트 로그를 보려면 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-125">To view all the classic event logs, type:</span></span>

```powershell
Get-EventLog -List
```

<span data-ttu-id="3e91e-126">Cmdlet을 사용 하 여 이벤트 `Get-WmiObject` 관련 WMI(Windows Management Instrumentation) (WMI) 클래스를 사용 하 여 이벤트 로그를 검사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-126">You can also use the `Get-WmiObject` cmdlet to use the event-related Windows Management Instrumentation (WMI) classes to examine the event log.</span></span> <span data-ttu-id="3e91e-127">예를 들어 이벤트 로그 파일의 모든 속성을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-127">For example, to view all the properties of the event log file, type:</span></span>

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

<span data-ttu-id="3e91e-128">Win32 이벤트 관련 WMI 클래스를 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-128">To find the Win32 event-related WMI classes, type:</span></span>

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

<span data-ttu-id="3e91e-129">자세한 내용을 보려면 "Get-help get-EventLog" 및 "Get-help Get-wmiobject"를 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3e91e-129">For more information, type "Get-Help Get-EventLog" and "Get-Help Get-WmiObject".</span></span>

## <a name="selecting-events-for-the-windows-powershell-event-log"></a><span data-ttu-id="3e91e-130">Windows PowerShell 이벤트 로그에 대 한 이벤트 선택</span><span class="sxs-lookup"><span data-stu-id="3e91e-130">Selecting Events for the Windows PowerShell Event Log</span></span>

<span data-ttu-id="3e91e-131">이벤트 로그 기본 설정 변수를 사용 하 여 Windows PowerShell 이벤트 로그에 기록 되는 이벤트를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-131">You can use the event log preference variables to determine which events are recorded in the Windows PowerShell event log.</span></span>

<span data-ttu-id="3e91e-132">6 개의 이벤트 로그 기본 설정 변수가 있습니다. 세 가지 로깅 구성 요소 각각에 대 한 두 가지 변수: 엔진 (Windows PowerShell 프로그램), 공급자 및 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-132">There are six event log preference variables; two variables for each of the three logging components: the engine (the Windows PowerShell program), the providers, and the commands.</span></span> <span data-ttu-id="3e91e-133">LifeCycleEvent 변수는 정상적으로 시작 하 고 중지 하는 이벤트를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-133">The LifeCycleEvent variables log normal starting and stopping events.</span></span> <span data-ttu-id="3e91e-134">상태 변수는 오류 이벤트를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-134">The Health variables log error events.</span></span>

<span data-ttu-id="3e91e-135">다음 표에서는 이벤트 로그 기본 설정 변수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-135">The following table lists the event log preference variables.</span></span>

|<span data-ttu-id="3e91e-136">변수</span><span class="sxs-lookup"><span data-stu-id="3e91e-136">Variable</span></span>                  |<span data-ttu-id="3e91e-137">Description</span><span class="sxs-lookup"><span data-stu-id="3e91e-137">Description</span></span>                                    |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="3e91e-138">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-138">$LogEngineLifeCycleEvent</span></span>  |<span data-ttu-id="3e91e-139">PowerShell의 시작 및 중지를 로깅합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-139">Logs the start and stop of PowerShell</span></span>          |
|<span data-ttu-id="3e91e-140">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-140">$LogEngineHealthEvent</span></span>     |<span data-ttu-id="3e91e-141">PowerShell 프로그램 오류를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-141">Logs PowerShell program errors</span></span>                 |
|<span data-ttu-id="3e91e-142">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-142">$LogProviderLifeCycleEvent</span></span>|<span data-ttu-id="3e91e-143">PowerShell 공급자의 시작 및 중지를 로깅합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-143">Logs the start and stop of PowerShell providers</span></span>|
|<span data-ttu-id="3e91e-144">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-144">$LogProviderHealthEvent</span></span>   |<span data-ttu-id="3e91e-145">로그 PowerShell 공급자 오류</span><span class="sxs-lookup"><span data-stu-id="3e91e-145">Logs PowerShell provider errors</span></span>                |
|<span data-ttu-id="3e91e-146">$LogCommandLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-146">$LogCommandLifeCycleEvent</span></span> |<span data-ttu-id="3e91e-147">명령의 시작 및 완료를 로깅합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-147">Logs the starting and completion of commands</span></span>   |
|<span data-ttu-id="3e91e-148">$LogCommandHealthEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-148">$LogCommandHealthEvent</span></span>    |<span data-ttu-id="3e91e-149">명령 오류 기록</span><span class="sxs-lookup"><span data-stu-id="3e91e-149">Logs command errors</span></span>                            |

<span data-ttu-id="3e91e-150">Windows PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](about_Providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e91e-150">(For information about Windows PowerShell providers, see [about_Providers](about_Providers.md).)</span></span>

<span data-ttu-id="3e91e-151">기본적으로 다음 이벤트 유형만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-151">By default, only the following event types are enabled:</span></span>

* <span data-ttu-id="3e91e-152">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-152">$LogEngineLifeCycleEvent</span></span>
* <span data-ttu-id="3e91e-153">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-153">$LogEngineHealthEvent</span></span>
* <span data-ttu-id="3e91e-154">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-154">$LogProviderLifeCycleEvent</span></span>
* <span data-ttu-id="3e91e-155">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="3e91e-155">$LogProviderHealthEvent</span></span>

<span data-ttu-id="3e91e-156">이벤트 유형을 사용 하도록 설정 하려면 해당 이벤트 유형에 대 한 기본 설정 변수를 $true 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-156">To enable an event type, set the preference variable for that event type to $true.</span></span> <span data-ttu-id="3e91e-157">예를 들어, 명령 수명 주기 이벤트를 사용 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-157">For example, to enable command life-cycle events, type:</span></span>

```powershell
$LogCommandLifeCycleEvent
```

<span data-ttu-id="3e91e-158">또는 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-158">Or, type:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="3e91e-159">이벤트 유형을 사용 하지 않도록 설정 하려면 해당 이벤트 유형에 대 한 기본 설정 변수를 $false 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-159">To disable an event type, set the preference variable for that event type to $false.</span></span> <span data-ttu-id="3e91e-160">예를 들어, 명령 수명 주기 이벤트를 사용 하지 않도록 설정 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-160">For example, to disable command life-cycle events, type:</span></span>

```powershell
$LogProviderLifeCycleEvent = $false
```

<span data-ttu-id="3e91e-161">Windows PowerShell 엔진과 핵심 공급자가 시작 되었음을 나타내는 이벤트를 제외 하 고 모든 이벤트를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-161">You can disable any event, except for the events that indicate that the Windows PowerShell engine and the core providers are started.</span></span> <span data-ttu-id="3e91e-162">이러한 이벤트는 Windows PowerShell 프로필이 실행 되기 전에 호스트 프로그램에서 명령을 수락할 준비가 되기 전에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-162">These events are generated before the Windows PowerShell profiles are run and before the host program is ready to accept commands.</span></span>

<span data-ttu-id="3e91e-163">변수 설정은 현재 Windows PowerShell 세션에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-163">The variable settings apply only for the current Windows PowerShell session.</span></span>
<span data-ttu-id="3e91e-164">모든 Windows PowerShell 세션에 적용 하려면 Windows PowerShell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-164">To apply them to all Windows PowerShell sessions, add them to your Windows PowerShell profile.</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="3e91e-165">모듈 이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="3e91e-165">Logging Module Events</span></span>

<span data-ttu-id="3e91e-166">Windows PowerShell 3.0부터 모듈 및 스냅인의 LogPipelineExecutionDetails 속성을 TRUE로 설정 하 여 Windows PowerShell 모듈 및 스냅인의 cmdlet 및 함수에 대 한 실행 이벤트를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-166">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets and functions in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="3e91e-167">Windows PowerShell 2.0에서이 기능은 스냅인에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-167">In Windows PowerShell 2.0, this feature is available only for snap-ins.</span></span>

<span data-ttu-id="3e91e-168">LogPipelineExecutionDetails 속성 값이 TRUE () 인 경우 `$true` Windows powershell은 세션의 cmdlet 및 함수 실행 이벤트를 Windows powershell 로그인 이벤트 뷰어에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-168">When the LogPipelineExecutionDetails property value is TRUE (`$true`), Windows PowerShell writes cmdlet and function execution events in the session to the Windows PowerShell log in Event Viewer.</span></span> <span data-ttu-id="3e91e-169">설정은 현재 세션 에서만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-169">The setting is effective only in the current session.</span></span>

<span data-ttu-id="3e91e-170">모듈의 cmdlet 및 함수에 대 한 실행 이벤트 로깅을 사용 하도록 설정 하려면 다음 명령 시퀀스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-170">To enable logging of execution events of cmdlets and functions in a module, use the following command sequence.</span></span>

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

<span data-ttu-id="3e91e-171">스냅인에서 cmdlet의 실행 이벤트 로깅을 사용 하도록 설정 하려면 다음 명령 시퀀스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-171">To enable logging of execution events of cmdlets in a snap-in, use the following command sequence.</span></span>

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

<span data-ttu-id="3e91e-172">로깅을 사용 하지 않도록 설정 하려면 동일한 명령 시퀀스를 사용 하 여 속성 값을 FALSE ()로 설정 `$false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-172">To disable logging, use the same command sequence to set the property value to FALSE (`$false`).</span></span>

<span data-ttu-id="3e91e-173">"모듈 로깅 켜기" 그룹 정책 설정을 사용 하 여 모듈 및 스냅인 로깅을 사용 하거나 사용 하지 않도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-173">You can also use the "Turn on Module Logging" Group Policy setting to enable and disable module and snap-in logging.</span></span> <span data-ttu-id="3e91e-174">정책 값에는 모듈 및 스냅인 이름 목록이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-174">The policy value includes a list of module and snap-in names.</span></span> <span data-ttu-id="3e91e-175">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-175">Wildcards are supported.</span></span>

<span data-ttu-id="3e91e-176">모듈에 대해 "모듈 로깅 켜기"가 설정 된 경우 모듈의 LogPipelineExecutionDetails 속성 값은 모든 세션에서 TRUE 이며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-176">When "Turn on Module Logging" is set for a module, the value of the LogPipelineExecutionDetails property of the module is TRUE in all sessions and it cannot be changed.</span></span>

<span data-ttu-id="3e91e-177">모듈 로깅 켜기 그룹 정책 설정은 다음 그룹 정책 경로에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-177">The Turn On Module Logging group policy setting is located in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

<span data-ttu-id="3e91e-178">사용자 구성 정책이 컴퓨터 구성 정책 보다 우선적으로 적용 되 고 두 정책은 모두 모듈 및 스냅인의 LogPipelineExecutionDetails 속성 값에 우선 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-178">The User Configuration policy takes precedence over the Computer Configuration policy, and both policies take preference over the value of the LogPipelineExecutionDetails property of modules and snap-ins.</span></span>

<span data-ttu-id="3e91e-179">이 그룹 정책 설정에 대 한 자세한 내용은 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e91e-179">For more information about this Group Policy setting, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="security-and-auditing"></a><span data-ttu-id="3e91e-180">보안 및 감사</span><span class="sxs-lookup"><span data-stu-id="3e91e-180">Security and Auditing</span></span>

<span data-ttu-id="3e91e-181">Windows PowerShell 이벤트 로그는 활동을 표시 하 고 문제 해결을 위한 작업 세부 정보를 제공 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-181">The Windows PowerShell event log is designed to indicate activity and to provide operational details for troubleshooting.</span></span>

<span data-ttu-id="3e91e-182">그러나 대부분의 Windows 기반 응용 프로그램 이벤트 로그와 마찬가지로 Windows PowerShell 이벤트 로그는 안전 하지 않도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-182">However, like most Windows-based application event logs, the Windows PowerShell event log is not designed to be secure.</span></span> <span data-ttu-id="3e91e-183">보안을 감사 하거나 기밀 정보나 독점 정보를 기록 하는 데 사용 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-183">It should not be used to audit security or to record confidential or proprietary information.</span></span>

<span data-ttu-id="3e91e-184">이벤트 로그는 사용자가 읽고 이해할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-184">Event logs are designed to be read and understood by users.</span></span> <span data-ttu-id="3e91e-185">사용자는 로그에서 읽고 로그에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-185">Users can read from and write to the log.</span></span> <span data-ttu-id="3e91e-186">악의적인 사용자가 로컬 또는 원격 컴퓨터에서 이벤트 로그를 읽고 false 데이터를 기록한 다음 해당 작업의 로깅을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-186">A malicious user could read an event log on a local or remote computer, record false data, and then prevent the logging of their activities.</span></span>

## <a name="notes"></a><span data-ttu-id="3e91e-187">메모</span><span class="sxs-lookup"><span data-stu-id="3e91e-187">Notes</span></span>

<span data-ttu-id="3e91e-188">모듈 작성자의 작성자는 해당 모듈에 로깅 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e91e-188">Authors of module authors can add logging features to their modules.</span></span> <span data-ttu-id="3e91e-189">자세한 내용은 [Windows PowerShell 모듈 작성](/powershell/scripting/developer/module/writing-a-windows-powershell-module)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e91e-189">For more information, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e91e-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e91e-190">See Also</span></span>

[<span data-ttu-id="3e91e-191">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="3e91e-191">Get-EventLog</span></span>](xref:Microsoft.PowerShell.Management.Get-EventLog)

[<span data-ttu-id="3e91e-192">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="3e91e-192">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="3e91e-193">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="3e91e-193">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="3e91e-194">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="3e91e-194">about_Preference_Variables</span></span>](about_Preference_Variables.md)
