---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 2.0 엔진 사용
description: Windows PowerShell 2.0 엔진은 Windows PowerShell 2.0용으로 작성되고 CLR 2.0으로 컴파일된 호스트 프로그램을 수정 없이 실행할 수 없기 때문에 기존 스크립트 또는 호스트 프로그램을 실행할 수 없을 때만 사용해야 합니다.
ms.openlocfilehash: 214b87b7314f31974801bb07f98ddea3b68008f0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663996"
---
# <a name="using-the-windows-powershell-20-engine"></a><span data-ttu-id="258d6-104">Windows PowerShell 2.0 엔진 사용</span><span class="sxs-lookup"><span data-stu-id="258d6-104">Using the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="258d6-105">Windows PowerShell은 이전 버전과 호환되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-105">Windows PowerShell is designed to be backward compatible with previous versions.</span></span> <span data-ttu-id="258d6-106">Windows PowerShell 2.0용으로 작성된 cmdlet, 공급자, 스냅인, 모듈 및 스크립트는 Windows PowerShell 신규 버전에서 문제없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-106">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in newer versions Windows PowerShell.</span></span> <span data-ttu-id="258d6-107">그러나 Microsoft .NET Framework 4에서는 런타임 활성화 정책이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-107">However, Microsoft .NET Framework 4 changed the runtime activation policy.</span></span>
<span data-ttu-id="258d6-108">Windows PowerShell 2.0용으로 작성하고 CLR(공용 언어 런타임) 2.0으로 컴파일한 Windows PowerShell 호스트 프로그램은 CLR 4.0(또는 그 이상)으로 컴파일한 Windows PowerShell 신규 버전에서는 수정해야 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-108">Windows PowerShell host programs written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in new versions Windows PowerShell that are compiled with CLR 4.0 (or higher).</span></span>

<span data-ttu-id="258d6-109">Windows PowerShell 2.0 엔진은 기존 스크립트 또는 호스트 프로그램이 Windows PowerShell 5.1과 호환되지 않아 실행할 수 없는 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-109">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 5.1.</span></span> <span data-ttu-id="258d6-110">대표적인 예는 이전 버전의 Exchange 또는 SQL Server 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-110">Examples of this include older versions of Exchange or SQL Server modules.</span></span> <span data-ttu-id="258d6-111">이러한 경우는 많지 않을 것으로 예상됩니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-111">Such cases are expected to be rare.</span></span>

<span data-ttu-id="258d6-112">Windows PowerShell 2.0 엔진을 필요로 하는 대부분의 프로그램은 자동으로 엔진을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-112">Many programs that require the Windows PowerShell 2.0 Engine start it automatically.</span></span> <span data-ttu-id="258d6-113">이러한 지침은 엔진을 수동으로 시작해야 하는 드문 경우를 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-113">These instructions are included for the rare situations in which you need to start the engine manually.</span></span>

## <a name="deprecation-and-security-concerns"></a><span data-ttu-id="258d6-114">사용 중단 및 보안 우려</span><span class="sxs-lookup"><span data-stu-id="258d6-114">Deprecation and security concerns</span></span>

<span data-ttu-id="258d6-115">Windows PowerShell 2.0은 2017년 8월 부로 사용 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-115">Windows PowerShell 2.0 was deprecated in August, 2017.</span></span> <span data-ttu-id="258d6-116">자세한 내용은 [공지][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="258d6-116">For more information, see the [announcement][] on the PowerShell blog.</span></span>

<span data-ttu-id="258d6-117">Windows PowerShell 2.0에는 버전 3, 4, 5에서 추가된 강화 및 보안 기능 대부분이 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-117">Windows PowerShell 2.0 is missing a significant amount of the hardening and security features added in versions 3, 4, and 5.</span></span> <span data-ttu-id="258d6-118">되도록 사용하지 않을 것을 강력하게 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-118">We highly, highly recommend that users not use it if they can help it.</span></span> <span data-ttu-id="258d6-119">자세한 내용은 [셸 및 스크립팅 언어 보안 비교][]와 [PowerShell ♥ the Blue Team][blueteam]을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="258d6-119">For more information, see [A Comparison of Shell and Scripting Language Security][] and [PowerShell ♥ the Blue Team][blueteam].</span></span>

## <a name="installing-and-enabling-required-programs"></a><span data-ttu-id="258d6-120">필요한 프로그램 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="258d6-120">Installing and Enabling Required Programs</span></span>

<span data-ttu-id="258d6-121">Windows PowerShell 2.0 엔진을 시작하기 전에 Windows PowerShell 2.0 엔진과 Microsoft .NET Framework 3.5 서비스 팩 1을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-121">Before starting the Windows PowerShell 2.0 Engine, enable the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 with Service Pack 1.</span></span> <span data-ttu-id="258d6-122">자세한 내용은 [Windows PowerShell 설치][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="258d6-122">For instructions, see [Installing Windows PowerShell][].</span></span>

<span data-ttu-id="258d6-123">Windows Management Framework 3.0 이상이 설치된 시스템에는 필요한 구성 요소가 모두 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-123">Systems on which Windows Management Framework 3.0 or higher is installed have all of the required components.</span></span> <span data-ttu-id="258d6-124">추가 구성은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-124">No further configuration is necessary.</span></span> <span data-ttu-id="258d6-125">Windows Management Framework 설치에 대한 자세한 내용은 [WMF 설치 및 구성][]을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="258d6-125">For information about installing Windows Management Framework, see [Install and configure WMF][].</span></span>

## <a name="how-to-start-the-windows-powershell-20-engine"></a><span data-ttu-id="258d6-126">Windows PowerShell 2.0 엔진을 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="258d6-126">How to start the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="258d6-127">Windows PowerShell을 시작하는 경우 기본적으로 최신 버전이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-127">When you start Windows PowerShell the newest version starts by default.</span></span> <span data-ttu-id="258d6-128">Windows PowerShell을 Windows PowerShell 2.0 엔진으로 시작하려면 `PowerShell.exe`의 Version 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-128">To start Windows PowerShell with the Windows PowerShell 2.0 Engine, use the Version parameter of `PowerShell.exe`.</span></span> <span data-ttu-id="258d6-129">Windows PowerShell 및 Cmd.exe를 비롯한 모든 명령 프롬프트에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-129">You can run the command at any command prompt, including Windows PowerShell and Cmd.exe.</span></span>

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a><span data-ttu-id="258d6-130">Windows PowerShell 2.0 엔진과 원격 세션을 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="258d6-130">How to start a remote session with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="258d6-131">원격 세션으로 Windows PowerShell 2.0 엔진을 실행하려면 Windows PowerShell 2.0 엔진을 로드하는 원격 컴퓨터에서 세션 구성(엔드포인트라고도 함)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-131">To run the Windows PowerShell 2.0 Engine in a remote session, create a session configuration (also known as an _endpoint_ ) on the remote computer that loads the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="258d6-132">세션 구성은 원격 컴퓨터에 저장되며, Windows PowerShell 2.0 엔진을 사용하는 모든 권한 있는 사용자가 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-132">The session configuration is saved on the remote computer and can be used by any authorized user to create sessions that use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="258d6-133">이는 일반적으로 시스템 관리자가 수행하는 고급 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-133">This is an advanced task that is typically performed by a system administrator.</span></span>

<span data-ttu-id="258d6-134">다음 절차에서는 [Register-PSSessionConfiguration][] cmdlet의 **PSVersion** 매개 변수를 통해 Windows PowerShell 2.0 엔진을 사용하는 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-134">The following procedure uses the **PSVersion** parameter of the [Register-PSSessionConfiguration][] cmdlet to create a session configuration that uses the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="258d6-135">[New-PSSessionConfigurationFile][] cmdlet의 **PowerShellVersion** 매개 변수를 사용하여 Windows PowerShell 2.0 엔진을 로드하는 세션에 대한 세션 구성 파일을 만들 수도 있으며, [Set-PSSessionConfiguration][] 매개 변수의 **PSVersion** 매개 변수를 통해 Windows PowerShell 2.0 엔진을 사용하도록 세션 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-135">You can also use the **PowerShellVersion** parameter of the [New-PSSessionConfigurationFile][] cmdlet to create a session configuration file for a session that loads the Windows PowerShell 2.0 Engine and you can use the **PSVersion** parameter of the [Set-PSSessionConfiguration][] parameter to change a session configuration to use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="258d6-136">세션 구성 파일에 대한 자세한 내용은 [about_Session_Configuration_Files][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="258d6-136">For more information about session configuration files, see [about_Session_Configuration_Files][].</span></span>
<span data-ttu-id="258d6-137">설치와 보안을 비롯한 세션 구성에 대한 자세한 내용은 [about_Session_Configurations][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="258d6-137">For information about session configurations, including setup and security, see [about_Session_Configurations][].</span></span>

### <a name="to-start-a-remote-windows-powershell-20-session"></a><span data-ttu-id="258d6-138">원격 Windows PowerShell 2.0 세션을 시작하려면</span><span class="sxs-lookup"><span data-stu-id="258d6-138">To start a remote Windows PowerShell 2.0 session</span></span>

1. <span data-ttu-id="258d6-139">Windows PowerShell 2.0 엔진을 필요로 하는 세션 구성을 만들려면 `Register-PSSessionConfiguration` cmdlet의 **PSVersion** 매개 변수에 값 `2.0`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-139">To create a session configuration that requires the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet with a value of `2.0`.</span></span>
   <span data-ttu-id="258d6-140">연결의 "서버 쪽" 또는 수신 끝에 있는 컴퓨터에서 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-140">Run this command on the computer at the "server side" or receiving end of the connection.</span></span>

   <span data-ttu-id="258d6-141">다음 샘플 명령은 Server01 컴퓨터에서 PS2 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-141">The following sample command creates the PS2 session configuration on the Server01 computer.</span></span> <span data-ttu-id="258d6-142">이 명령을 실행하려면 **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-142">To run this command, start Windows PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. <span data-ttu-id="258d6-143">PS2 세션 구성을 사용하는 Server01 컴퓨터에서 세션을 만들려면 New-PSSession cmdlet 같은 원격 세션을 만드는 cmdlet의 **ConfigurationName** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-143">To create a session on the Server01 computer that uses the PS2 session configuration, use the **ConfigurationName** parameter of cmdlets that create a remote session, such as the \`New-PSSession cmdlet.</span></span>

   <span data-ttu-id="258d6-144">세션 구성을 사용하는 세션이 시작되면 Windows PowerShell 2.0 엔진이 자동으로 세션에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-144">When a session that uses the session configuration starts, the Windows PowerShell 2.0 Engine is automatically loaded into the session.</span></span>

   <span data-ttu-id="258d6-145">다음 명령은 PS2 세션 구성을 사용하는 Server01 컴퓨터에서 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-145">The following command starts a session on the Server01 computer that uses the PS2 session configuration.</span></span> <span data-ttu-id="258d6-146">이 명령은 세션을 `$s` 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-146">The command saves the session in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a><span data-ttu-id="258d6-147">Windows PowerShell 2.0 엔진을 사용하여 백그라운드 작업을 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="258d6-147">How to start a background job with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="258d6-148">Windows PowerShell 2.0 엔진을 사용하여 백그라운드 작업을 시작하려면 [Start-Job][] cmdlet의 **PSVersion** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-148">To start a background job with the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Start-Job][] cmdlet.</span></span>

<span data-ttu-id="258d6-149">다음 명령은 Windows PowerShell 2.0 엔진을 사용하여 백그라운드 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="258d6-149">The following command starts a background job with the Windows PowerShell 2.0 Engine</span></span>

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

<span data-ttu-id="258d6-150">백그라운드 작업에 대한 자세한 내용은 [about_Jobs][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="258d6-150">For more information about background jobs, see [about_Jobs][].</span></span>

<!-- link references -->
[공지]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[announcement]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[셸 및 스크립팅 언어 보안 비교]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[A Comparison of Shell and Scripting Language Security]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Windows PowerShell 설치]: install/Installing-Windows-PowerShell.md
[Installing Windows PowerShell]: install/Installing-Windows-PowerShell.md
[WMF 설치 및 구성]: wmf/setup/install-configure.md
[Install and configure WMF]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfigurationFile
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
