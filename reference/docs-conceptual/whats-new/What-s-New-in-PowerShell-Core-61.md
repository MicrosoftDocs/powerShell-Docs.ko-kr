---
title: PowerShell Core 6.1의 새로운 기능
description: PowerShell Core 6.1에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 09/13/2018
ms.openlocfilehash: 079d5a472c743ce94f2e93143c1dcb4ff406951f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78277745"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="83a7b-103">PowerShell Core 6.1의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="83a7b-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="83a7b-104">다음은 PowerShell Core 6.1에 도입된 몇 가지 새로운 주요 기능 및 변경 내용의 선택 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="83a7b-105">PowerShell을 더 빠르고 더 안정적으로 만들어주는 “지루한 작업”도 **많이** 있습니다(또한 아주 많은 버그 수정도)!</span><span class="sxs-lookup"><span data-stu-id="83a7b-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span> <span data-ttu-id="83a7b-106">변경 사항의 전체 목록은 [GitHub의 changelog](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="83a7b-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="83a7b-107">다음 이름 중 일부를 호출하는 동안 이 릴리스를 가능하게 해준 [커뮤니티 기여자 모두에게](https://github.com/PowerShell/PowerShell/graphs/contributors) 감사의 말씀을 드립니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="83a7b-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="83a7b-108">.NET Core 2.1</span></span>

<span data-ttu-id="83a7b-109">[5월에 출시](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/)된 후 PowerShell Core 6.1이 .NET Core 2.1로 이동되어 다음을 포함한 다양한 항목이 PowerShell에서 개선되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="83a7b-110">성능 향상([아래](#performance-improvements) 참조)</span><span class="sxs-lookup"><span data-stu-id="83a7b-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="83a7b-111">Alpine Linux 지원(미리 보기)</span><span class="sxs-lookup"><span data-stu-id="83a7b-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="83a7b-112">[.NET 글로벌 도구 지원](/dotnet/core/tools/global-tools) - PowerShell 곧 예정</span><span class="sxs-lookup"><span data-stu-id="83a7b-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="83a7b-113">.NET Core용 Windows 호환 기능 팩</span><span class="sxs-lookup"><span data-stu-id="83a7b-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="83a7b-114">Windows에서 .NET 팀은 제거된 많은 API를 다시 Windows의 .NET Core로 추가하는 어셈블리 집합인 [.NET Core용 Windows 호환 기능 팩](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="83a7b-115">Windows 호환 기능 팩을 PowerShell Core 6.1 릴리스에 추가하였으므로 이러한 API를 사용하는 모든 모듈 또는 스크립트는 사용 가능한 항목에 의존할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="83a7b-116">Windows 호환 기능 책을 통해 PowerShell Core는 **Windows 10 2018년 10월 업데이트 및 Windows Server 2019와 제공되는 1900개 이상의 cmdlet**을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="83a7b-117">애플리케이션 허용 목록에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="83a7b-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="83a7b-118">PowerShell Core 6.1에는 [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) 및 [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) 애플리케이션 허용 목록을 지원하는 Windows PowerShell 5.1을 사용한 패리티가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span> <span data-ttu-id="83a7b-119">애플리케이션 허용 목록은 PowerShell [제한된 언어 모드](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/)와 함께 사용되어 실행할 수 있도록 허용된 바이너리의 세부적 제어를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="83a7b-120">성능 향상</span><span class="sxs-lookup"><span data-stu-id="83a7b-120">Performance improvements</span></span>

<span data-ttu-id="83a7b-121">PowerShell Core 6.0은 일부 성능이 크게 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-121">PowerShell Core 6.0 made some significant performance improvements.</span></span> <span data-ttu-id="83a7b-122">PowerShell Core 6.1은 특정 작업의 속도를 계속 개선하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="83a7b-123">예를 들어 `Group-Object`의 속도는 66% 빨라졌습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="83a7b-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="83a7b-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="83a7b-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="83a7b-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="83a7b-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="83a7b-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="83a7b-127">시간(초)</span><span class="sxs-lookup"><span data-stu-id="83a7b-127">Time (sec)</span></span>   | <span data-ttu-id="83a7b-128">25.178</span><span class="sxs-lookup"><span data-stu-id="83a7b-128">25.178</span></span>                 | <span data-ttu-id="83a7b-129">19.653</span><span class="sxs-lookup"><span data-stu-id="83a7b-129">19.653</span></span>              | <span data-ttu-id="83a7b-130">6.641</span><span class="sxs-lookup"><span data-stu-id="83a7b-130">6.641</span></span>               |
| <span data-ttu-id="83a7b-131">속도 증가(%)</span><span class="sxs-lookup"><span data-stu-id="83a7b-131">Speed-up (%)</span></span> | <span data-ttu-id="83a7b-132">해당 없음</span><span class="sxs-lookup"><span data-stu-id="83a7b-132">N/A</span></span>                    | <span data-ttu-id="83a7b-133">21.9%</span><span class="sxs-lookup"><span data-stu-id="83a7b-133">21.9%</span></span>               | <span data-ttu-id="83a7b-134">66.2%</span><span class="sxs-lookup"><span data-stu-id="83a7b-134">66.2%</span></span>               |

<span data-ttu-id="83a7b-135">마찬가지로, 이와 같은 정렬 시나리오도 15% 이상 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="83a7b-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="83a7b-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="83a7b-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="83a7b-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="83a7b-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="83a7b-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="83a7b-139">시간(초)</span><span class="sxs-lookup"><span data-stu-id="83a7b-139">Time (sec)</span></span>   | <span data-ttu-id="83a7b-140">12.170</span><span class="sxs-lookup"><span data-stu-id="83a7b-140">12.170</span></span>                 | <span data-ttu-id="83a7b-141">8.493</span><span class="sxs-lookup"><span data-stu-id="83a7b-141">8.493</span></span>               | <span data-ttu-id="83a7b-142">7.08</span><span class="sxs-lookup"><span data-stu-id="83a7b-142">7.08</span></span>                |
| <span data-ttu-id="83a7b-143">속도 증가(%)</span><span class="sxs-lookup"><span data-stu-id="83a7b-143">Speed-up (%)</span></span> | <span data-ttu-id="83a7b-144">해당 없음</span><span class="sxs-lookup"><span data-stu-id="83a7b-144">N/A</span></span>                    | <span data-ttu-id="83a7b-145">30.2%</span><span class="sxs-lookup"><span data-stu-id="83a7b-145">30.2%</span></span>               | <span data-ttu-id="83a7b-146">16.6%</span><span class="sxs-lookup"><span data-stu-id="83a7b-146">16.6%</span></span>               |

<span data-ttu-id="83a7b-147">`Import-Csv`도 Windows PowerShell에서 회귀된 후 속도가 크게 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="83a7b-148">다음 예제에서는 26,616개 행과 6개의 열이 있는 CSV 테스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="83a7b-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="83a7b-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="83a7b-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="83a7b-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="83a7b-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="83a7b-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="83a7b-152">시간(초)</span><span class="sxs-lookup"><span data-stu-id="83a7b-152">Time (sec)</span></span>   | <span data-ttu-id="83a7b-153">0.441</span><span class="sxs-lookup"><span data-stu-id="83a7b-153">0.441</span></span>                  | <span data-ttu-id="83a7b-154">1.069</span><span class="sxs-lookup"><span data-stu-id="83a7b-154">1.069</span></span>               | <span data-ttu-id="83a7b-155">0.268</span><span class="sxs-lookup"><span data-stu-id="83a7b-155">0.268</span></span>                  |
| <span data-ttu-id="83a7b-156">속도 증가(%)</span><span class="sxs-lookup"><span data-stu-id="83a7b-156">Speed-up (%)</span></span> | <span data-ttu-id="83a7b-157">해당 없음</span><span class="sxs-lookup"><span data-stu-id="83a7b-157">N/A</span></span>                    | <span data-ttu-id="83a7b-158">-142.4%</span><span class="sxs-lookup"><span data-stu-id="83a7b-158">-142.4%</span></span>             | <span data-ttu-id="83a7b-159">74.9%(WPS에서 39.2%)</span><span class="sxs-lookup"><span data-stu-id="83a7b-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="83a7b-160">마지막으로, JSON에서 `PSObject`로 변환할 때 Windows PowerShell 이후에 50% 이상 속도가 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="83a7b-161">다음 예제에서는 ~2MB 테스트 JSON 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="83a7b-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="83a7b-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="83a7b-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="83a7b-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="83a7b-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="83a7b-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="83a7b-165">시간(초)</span><span class="sxs-lookup"><span data-stu-id="83a7b-165">Time (sec)</span></span>   | <span data-ttu-id="83a7b-166">0.259</span><span class="sxs-lookup"><span data-stu-id="83a7b-166">0.259</span></span>                  | <span data-ttu-id="83a7b-167">0.577</span><span class="sxs-lookup"><span data-stu-id="83a7b-167">0.577</span></span>               | <span data-ttu-id="83a7b-168">0.125</span><span class="sxs-lookup"><span data-stu-id="83a7b-168">0.125</span></span>                  |
| <span data-ttu-id="83a7b-169">속도 증가(%)</span><span class="sxs-lookup"><span data-stu-id="83a7b-169">Speed-up (%)</span></span> | <span data-ttu-id="83a7b-170">해당 없음</span><span class="sxs-lookup"><span data-stu-id="83a7b-170">N/A</span></span>                    | <span data-ttu-id="83a7b-171">-122.8%</span><span class="sxs-lookup"><span data-stu-id="83a7b-171">-122.8%</span></span>             | <span data-ttu-id="83a7b-172">78.3%(WPS에서 51.7%)</span><span class="sxs-lookup"><span data-stu-id="83a7b-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="83a7b-173">Windows에서 호환 미해결 모듈에 대한 `system32` 확인</span><span class="sxs-lookup"><span data-stu-id="83a7b-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="83a7b-174">Windows 10 1809 업데이트 및 Windows Server 2019에서 몇 가지 미해결 PowerShell 모듈을 업데이트하여 PowerShell Core와 호환되도록 표시했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="83a7b-175">PowerShell Core 6.1이 시작되면 자동으로 `$windir\System32`가 `PSModulePath` 환경 변수의 일부로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span> <span data-ttu-id="83a7b-176">단, 해당 `Get-Module`이 `Import-Module`와 호환되는 것으로 표시되는 경우 모듈을 `CompatiblePSEdition` 및 `Core`에만 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="83a7b-177">설치된 역할 및 기능에 따라 다양한 사용 가능한 모듈을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-177">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="83a7b-178">`-SkipEditionCheck` 스위치 매개 변수를 사용하여 모든 모듈을 표시하도록 이 동작을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="83a7b-179">또한 `PSEdition` 속성을 테이블 출력에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="83a7b-180">이 동작에 대한 자세한 내용은 [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="83a7b-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="83a7b-181">Markdown cmdlet 및 렌더링</span><span class="sxs-lookup"><span data-stu-id="83a7b-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="83a7b-182">Markdown은 HTML로 렌더링할 수 있는 기본 서식의 읽을 수 있는 일반 문서를 만들기 위한 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="83a7b-183">콘솔에서 Markdown 문서를 변환하고 렌더링할 수 있도록 6.1에 다음을 포함한 일부 cmdlet이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="83a7b-184">예를 들어 `Show-Markdown`은 콘솔에 Markdown 파일을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Show-Markdown 예제](media/What-s-New-in-PowerShell-Core-61/markdown_example.png)

<span data-ttu-id="83a7b-186">이러한 cmdlet의 작동 방식에 대한 자세한 내용은 [이 RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="83a7b-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="83a7b-187">실험적 기능 플래그</span><span class="sxs-lookup"><span data-stu-id="83a7b-187">Experimental feature flags</span></span>

<span data-ttu-id="83a7b-188">[실험적 기능][]에 대한 지원을 사용하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-188">We enabled support for [Experimental Features][].</span></span> <span data-ttu-id="83a7b-189">이 기능을 사용하여 PowerShell 개발자는 새로운 기능을 제공하고 디자인이 완료되기 전에 피드백을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-189">This allows PowerShell developers to deliver new features and get feedback before the design is complete.</span></span> <span data-ttu-id="83a7b-190">이 방법으로 디자인이 진전됨에 따라 호환성이 손상되는 변경이 생성되는 것을 피합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-190">This way we avoid making breaking changes as the design evolves.</span></span>

<span data-ttu-id="83a7b-191">`Get-ExperimentalFeature`를 사용하여 사용 가능한 실험적 기능 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-191">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="83a7b-192">`Enable-ExperimentalFeature` 및 `Disable-ExperimentalFeature`를 사용하여 이 기능을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-192">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

<span data-ttu-id="83a7b-193">[PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md)에서 이 기능에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-193">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="83a7b-194">웹 cmdlet 개선 사항</span><span class="sxs-lookup"><span data-stu-id="83a7b-194">Web cmdlet improvements</span></span>

<span data-ttu-id="83a7b-195">[@markekraus](https://github.com/markekraus) 덕분에 다음과 같은 우리의 웹 cmdlet에 많은 개선 사항이 적용되었습니다. [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="83a7b-195">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="83a7b-196">및 [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="83a7b-196">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="83a7b-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - `application-json` 응답을 위한 UTF-8로 설정된 기본 인코딩</span><span class="sxs-lookup"><span data-stu-id="83a7b-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="83a7b-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - 표준을 준수하지 않는 `-SkipHeaderValidation` 헤더를 허용하는 `Content-Type` 매개 변수</span><span class="sxs-lookup"><span data-stu-id="83a7b-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="83a7b-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - 간소화된 `Form`를 지원하는 `multipart/form-data` 매개 변수</span><span class="sxs-lookup"><span data-stu-id="83a7b-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="83a7b-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - 호환, 대/소문자를 구분하지 않는 관계 키 처리</span><span class="sxs-lookup"><span data-stu-id="83a7b-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="83a7b-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - 웹 cmdlet에 대한 `-Resume` 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="83a7b-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="83a7b-202">원격 기능 향상</span><span class="sxs-lookup"><span data-stu-id="83a7b-202">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="83a7b-203">컨테이너용 PowerShell Direct에서 먼저 PowerShell Core 사용을 시도</span><span class="sxs-lookup"><span data-stu-id="83a7b-203">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="83a7b-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)는 사용자가 네트워크 연결 또는 기타 원격 관리 서비스 없이 Hyper-V VM 또는 컨테이너에 연결할 수 있도록 허용하는 PowerShell 및 Hyper-V의 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="83a7b-205">과거에 PowerShell Direct는 받은 편지함 Windows PowerShell 인스턴스를 사용하여 컨테이너에 연결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-205">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span> <span data-ttu-id="83a7b-206">이제 PowerShell Direct는 먼저 `pwsh.exe` 환경 변수에서 사용 가능한 `PATH`를 사용하여 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-206">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span> <span data-ttu-id="83a7b-207">`pwsh.exe`를 사용할 수 없는 경우 PowerShell Direct는 `powershell.exe`를 다시 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-207">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="83a7b-208">`Enable-PSRemoting`은 이제 별도의 원격 엔드포인트를 미리 보기 버전으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-208">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="83a7b-209">`Enable-PSRemoting`은 이제 다음과 같이 두 개의 원격 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-209">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="83a7b-210">PowerShell의 주 버전에 대해 하나.</span><span class="sxs-lookup"><span data-stu-id="83a7b-210">One for the major version of PowerShell.</span></span> <span data-ttu-id="83a7b-211">`PowerShell.6`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-211">For example, `PowerShell.6`.</span></span> <span data-ttu-id="83a7b-212">부 버전에 의존할 수 있는 이 엔드포인트는 “시스템 수준” PowerShell 6 세션 구성으로 업데이트함</span><span class="sxs-lookup"><span data-stu-id="83a7b-212">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="83a7b-213">버전별 세션 구성에 대해 하나. 예를 들면 `PowerShell.6.1.0`입니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-213">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="83a7b-214">이 동작은 여러 PowerShell 6 버전을 동일한 머신에 설치하고 액세스하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-214">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="83a7b-215">또한 PowerShell의 미리 보기 버전은 이제 `Enable-PSRemoting` cmdlet을 실행한 후에 각자 자신의 원격 세션 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-215">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="83a7b-216">출력은 이전에 WinRM을 설정하지 않은 경우 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-216">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="83a7b-217">그런 다음, PowerShell 6의 미리 보기 및 안정적 빌드에 대해서와 각 특정 버전에 대해서 별도 PowerShell 세션 구성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-217">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="83a7b-218">SSH에 대해 지원되는 `user@host:port` 구문</span><span class="sxs-lookup"><span data-stu-id="83a7b-218">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="83a7b-219">SSH 클라이언트는 일반적으로 `user@host:port` 형식의 연결 문자열을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-219">SSH clients typically support a connection string in the format `user@host:port`.</span></span> <span data-ttu-id="83a7b-220">추가 SSH를 PowerShell 원격 기능에 대한 프로토콜로 사용하여 연결 문자열의 이 형식에 대한 지원을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-220">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="83a7b-221">Windows에서 탐색기 셸 상황에 맞는 메뉴를 추가하는 MSI 옵션</span><span class="sxs-lookup"><span data-stu-id="83a7b-221">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="83a7b-222">[@bergmeister](https://github.com/bergmeister) 덕분에 이제 Windows에서 상황에 맞는 메뉴를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-222">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="83a7b-223">이제 Windows 탐색기의 어느 폴더에서나 PowerShell 6.1의 시스템 수준 설치를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-223">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![PowerShell 6을 위한 셸 상황에 맞는 메뉴](media/What-s-New-in-PowerShell-Core-61/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="83a7b-225">혜택</span><span class="sxs-lookup"><span data-stu-id="83a7b-225">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="83a7b-226">Windows 바로 가기 점프 목록의 “관리자 권한으로 실행”</span><span class="sxs-lookup"><span data-stu-id="83a7b-226">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="83a7b-227">[@bergmeister](https://github.com/bergmeister) 덕분에 이제 “관리자 권한으로 실행”이 PowerShell Core 바로 가기의 점프 목록에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-227">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![PowerShell 6 점프 목록의 관리자 권한으로 실행](media/What-s-New-in-PowerShell-Core-61/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="83a7b-229">`cd -`가 이전 디렉터리를 반환</span><span class="sxs-lookup"><span data-stu-id="83a7b-229">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="83a7b-230">또는 Linux에서:</span><span class="sxs-lookup"><span data-stu-id="83a7b-230">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="83a7b-231">또한 `cd` 및 `cd --`가 `$HOME`으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-231">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="83a7b-232">[@iSazonov](https://github.com/iSazonov) 덕분에 [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet이 PowerShell Core에 포트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-232">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="83a7b-233">`Update-Help`, 관리자가 아님</span><span class="sxs-lookup"><span data-stu-id="83a7b-233">`Update-Help` as non-admin</span></span>

<span data-ttu-id="83a7b-234">많은 요청에 의해 `Update-Help`는 더 이상 관리자 권한으로 실행될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-234">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span> <span data-ttu-id="83a7b-235">`Update-Help`는 이제 기본 제공되어 사용자 범위 폴더에 대한 도움말을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-235">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="83a7b-236">`PSCustomObject`의 새 메서드/속성</span><span class="sxs-lookup"><span data-stu-id="83a7b-236">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="83a7b-237">[@iSazonov](https://github.com/iSazonov) 덕분에 새 메서드 및 속성을 `PSCustomObject`에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-237">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span> <span data-ttu-id="83a7b-238">`PSCustomObject`에는 이제 다른 개체처럼 `Count`/`Length` 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-238">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="83a7b-239">이 작업에는 `ForEach` 항목에서 작동하고 필터링할 수 있도록 허용하는 `Where` 및 `PSCustomObject` 메서드도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-239">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="83a7b-240">@SimonWahlin 덕분에 `-Not` 매개 변수를 `Where-Object`에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-240">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span> <span data-ttu-id="83a7b-241">이제 존재하지 않는 속성 또는 null/비어 있는 속성 값에 대한 파이프라인에서 개체를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-241">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="83a7b-242">예를 들어 이 명령은 정의된 모든 종속 서비스가 없는 모든 서비스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-242">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="83a7b-243">`New-ModuleManifest`는 BOM이 없는 UTF-8 문서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-243">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="83a7b-244">PowerShell 6.0에서 BOM이 없는 UTF-8로 이동하여 UTF-16 대신 BOM이 없는 UTF-8 문서를 만들도록 `New-ModuleManifest` cmdlet을 업데이트했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-244">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="83a7b-245">PSMethod에서 대리자로 변환</span><span class="sxs-lookup"><span data-stu-id="83a7b-245">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="83a7b-246">[@powercode](https://github.com/powercode) 덕분에 이제 대리자로의 `PSMethod` 변환을 지원하게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-246">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span> <span data-ttu-id="83a7b-247">이를 통해 `PSMethod` `[M]::DoubleStrLen`을 대리자 값으로 `[M]::AggregateString`에 전달하는 등의 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-247">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="83a7b-248">이러한 변경 사항에 대한 자세한 내용은 [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287)을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="83a7b-248">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="83a7b-249">`Measure-Object`의 표준 편차</span><span class="sxs-lookup"><span data-stu-id="83a7b-249">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="83a7b-250">[@CloudyDino](https://github.com/CloudyDino) 덕분에 `StandardDeviation` 속성을 `Measure-Object`에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-250">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="83a7b-251">[@maybe-hello-world](https://github.com/maybe-hello-world) 덕분에 `Get-PfxCertificate`는 이제 `Password`을 사용하는 `SecureString` 매개 변수를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-251">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="83a7b-252">이를 통해 비대화형으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-252">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="83a7b-253">`more` 함수 제거</span><span class="sxs-lookup"><span data-stu-id="83a7b-253">Removal of the `more` function</span></span>

<span data-ttu-id="83a7b-254">과거에 PowerShell은 Windows에서 `more`을 래핑한 `more.com`라는 함수를 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-254">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span> <span data-ttu-id="83a7b-255">해당 함수는 이제 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-255">That function has now been removed.</span></span>

<span data-ttu-id="83a7b-256">또한 `help` 함수가 Windows에서 `more.com`을 사용하거나 비Windows 플랫폼에서 `$env:PAGER`에 의해 지정된 시스템의 기본 호출기를 사용하도록 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-256">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="83a7b-257">`cd DriveName:`은 이제 해당 드라이브에서 현재 작업 디렉터리에 사용자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-257">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="83a7b-258">이전에는 `Set-Location` 또는 `cd`를 사용하여 PSDrive로 돌아가면 해당 드라이브의 기본 위치로 사용자를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-258">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="83a7b-259">[@mcbobke](https://github.com/mcbobke) 덕분에 이제는 해당 세션에 대해 마지막으로 알려진 현재 작업 디렉터리로 사용자를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-259">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="83a7b-260">Windows PowerShell 형식 가속기</span><span class="sxs-lookup"><span data-stu-id="83a7b-260">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="83a7b-261">Windows PowerShell에서 해당 형식과 손쉽게 작업할 수 있도록 다음과 같은 형식 가속기를 포함시켰습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-261">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="83a7b-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="83a7b-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="83a7b-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="83a7b-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="83a7b-264">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="83a7b-264">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="83a7b-265">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="83a7b-265">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="83a7b-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="83a7b-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="83a7b-267">이러한 형식 가속기는 PowerShell 6에는 포함되지 않았으나, Windows에서 실행 중인 PowerShell 6.1에는 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-267">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="83a7b-268">이러한 형식은 AD 및 WMI 개체를 손쉽게 구성하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-268">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="83a7b-269">예를 들어, LDAP를 사용하여 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-269">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="83a7b-270">다음 예제에서는 Win32_OperatingSystem CIM 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-270">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="83a7b-271">이 예제에서는 Win32_OperatingSystem 클래스에 대한 ManagementClass 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-271">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="83a7b-272">모든 `-lp` 매개 변수에 대한 `-LiteralPath` 별칭</span><span class="sxs-lookup"><span data-stu-id="83a7b-272">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="83a7b-273">[@kvprasoon](https://github.com/kvprasoon) 덕분에 이제 `-lp` 매개 변수가 있는 모든 기본 제공 PowerShell cmdlet에 대해 매개 변수 별칭 `-LiteralPath`가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-273">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="83a7b-274">주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="83a7b-274">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="83a7b-275">Windows의 MSI 기반 설치 경로</span><span class="sxs-lookup"><span data-stu-id="83a7b-275">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="83a7b-276">Windows에서 MSI 패키지는 이제 다음 경로에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-276">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="83a7b-277">`$env:ProgramFiles\PowerShell\6\` 6.x의 안정적인 설치용</span><span class="sxs-lookup"><span data-stu-id="83a7b-277">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="83a7b-278">`$env:ProgramFiles\PowerShell\6-preview\` 6.x의 미리 보기 설치용</span><span class="sxs-lookup"><span data-stu-id="83a7b-278">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="83a7b-279">이 변경 내용으로 PowerShell Core는 Microsoft Update에서 업데이트/제공될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-279">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="83a7b-280">자세한 내용은 [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md)을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="83a7b-280">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="83a7b-281">원격 분석은 환경 변수를 통해서만 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-281">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="83a7b-282">PowerShell Core는 시작할 때 기본 원격 분석 데이터를 Microsoft로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-282">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="83a7b-283">데이터에는 OS 이름, OS 버전 및 PowerShell 버전이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-283">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="83a7b-284">이 데이터를 사용하면 PowerShell이 사용되는 환경을 더 잘 이해할 수 있으며, 새 기능 및 수정 사항의 우선 순위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-284">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="83a7b-285">이 원격 분석을 옵트아웃하려면 환경 변수 `POWERSHELL_TELEMETRY_OPTOUT`을 `true`, `yes` 또는 `1`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-285">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="83a7b-286">원격 분석을 사용하지 않도록 설정하는 파일 `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY`의 삭제를 더 이상 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-286">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="83a7b-287">Unix 플랫폼에서 PowerShell 원격 기능의 HTTP를 통해 기본 인증 허용 안 함</span><span class="sxs-lookup"><span data-stu-id="83a7b-287">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="83a7b-288">암호화되지 않은 트래픽 사용을 방지하려면 Unix 플랫폼의 PowerShell 원격 기능은 이제 NTLM/Negotiate 또는 HTTPS를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-288">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="83a7b-289">이러한 변경 사항에 대한 자세한 내용은 [문제 #6779](https://github.com/PowerShell/PowerShell/issues/6779)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="83a7b-289">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="83a7b-290">Add-Type에서 지원되는 언어로 `VisualBasic` 제거</span><span class="sxs-lookup"><span data-stu-id="83a7b-290">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="83a7b-291">이전에는 `Add-Type` cmdlet을 사용하여 Visual Basic 코드를 컴파일할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-291">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span> <span data-ttu-id="83a7b-292">Visual Basic은 `Add-Type`과는 거의 사용되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-292">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="83a7b-293">PowerShell의 크기를 줄이기 위해 이 기능을 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-293">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="83a7b-294">`CommandTypes.Workflow` 및 `WorkflowInfoCleaned` 사용 정리</span><span class="sxs-lookup"><span data-stu-id="83a7b-294">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="83a7b-295">이러한 변경 사항에 대한 자세한 내용은 [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708)을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="83a7b-295">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="83a7b-296">이제 Group-Object가 그룹 정렬</span><span class="sxs-lookup"><span data-stu-id="83a7b-296">Group-Object now sorts the groups</span></span>

<span data-ttu-id="83a7b-297">성능 개선의 일환으로, `Group-Object`가 이제 정렬된 그룹 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-297">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="83a7b-298">순서에 의존해서는 안 되지만, 첫 번째 그룹을 원한 경우 이러한 변경으로 낙담할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-298">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="83a7b-299">Microsoft는 이전 동작에 종속되는 영향력이 낮으므로 이 성능 개선이 변경 가치가 있다고 결정했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a7b-299">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="83a7b-300">이 변경에 대한 자세한 내용은 [문제 #7409](https://github.com/PowerShell/PowerShell/issues/7409)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83a7b-300">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>

<!-- URL references -->
[실험적 기능]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
