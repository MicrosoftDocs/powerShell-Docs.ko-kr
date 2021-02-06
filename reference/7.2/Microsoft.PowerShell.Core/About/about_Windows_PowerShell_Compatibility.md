---
description: PowerShell 7에 대 한 Windows PowerShell 호환성 기능을 설명 합니다.
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 3a7605765da8c17bad2d98a1d3fc3f7cc96f57b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605496"
---
# <a name="about-windows-powershell-compatibility"></a><span data-ttu-id="f734d-103">Windows PowerShell 호환성 정보</span><span class="sxs-lookup"><span data-stu-id="f734d-103">About Windows PowerShell compatibility</span></span>

## <a name="short-description"></a><span data-ttu-id="f734d-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="f734d-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="f734d-105">PowerShell 7에 대 한 Windows PowerShell 호환성 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-105">Describes the Windows PowerShell Compatibility functionality for PowerShell 7.</span></span>

## <a name="long-description"></a><span data-ttu-id="f734d-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="f734d-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="f734d-107">모듈 매니페스트가 PowerShell Core와 호환 되는 것으로 표시 되지 않는 한 폴더의 모듈은 `%windir%\system32\WindowsPowerShell\v1.0\Modules` Windows Powershell 호환성 기능을 통해 백그라운드 Windows powershell 5.1 프로세스에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-107">Unless the module manifest indicates that module is compatible with PowerShell Core, modules in the `%windir%\system32\WindowsPowerShell\v1.0\Modules` folder are loaded in a background Windows PowerShell 5.1 process by Windows PowerShell Compatibility feature.</span></span>

### <a name="using-the-compatibility-feature"></a><span data-ttu-id="f734d-108">호환성 기능 사용</span><span class="sxs-lookup"><span data-stu-id="f734d-108">Using the Compatibility feature</span></span>

<span data-ttu-id="f734d-109">Windows PowerShell 호환성 기능을 사용 하 여 첫 번째 모듈을 가져오는 경우 PowerShell `WinPSCompatSession` 은 백그라운드 Windows powershell 5.1 프로세스에서 실행 되는 라는 원격 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-109">When the first module is imported using Windows PowerShell Compatibility feature, PowerShell creates a remote session named `WinPSCompatSession` that is running in a background Windows PowerShell 5.1 process.</span></span> <span data-ttu-id="f734d-110">이 프로세스는 호환성 기능이 첫 번째 모듈을 가져올 때 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-110">This process is created when the Compatibility feature imports the first module.</span></span> <span data-ttu-id="f734d-111">마지막 해당 모듈이 제거 되거나 (를 사용 하 여 `Remove-Module` ) PowerShell 프로세스가 종료 되 면 프로세스가 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-111">The process is closed when the last such module is removed (using `Remove-Module`) or when PowerShell process exits.</span></span>

<span data-ttu-id="f734d-112">세션에서 로드 된 모듈은 `WinPSCompatSession` 암시적 원격을 통해 사용 되며 현재 PowerShell 세션에 반영 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-112">The modules loaded in the `WinPSCompatSession` session are used via implicit remoting and reflected into current PowerShell session.</span></span> <span data-ttu-id="f734d-113">PowerShell 작업에 사용 되는 것과 동일한 전송 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-113">This is the same transport method used for PowerShell jobs.</span></span>

<span data-ttu-id="f734d-114">모듈을 세션으로 가져올 때 `WinPSCompatSession` 암시적 원격은 사용자의 디렉터리에 프록시 모듈을 생성 `$env:Temp` 하 고이 프록시 모듈을 현재 PowerShell 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-114">When a module is imported into the `WinPSCompatSession` session, implicit remoting generates a proxy module in the user's `$env:Temp` directory and imports this proxy module into current PowerShell session.</span></span> <span data-ttu-id="f734d-115">이렇게 하면 PowerShell에서 모듈이 Windows PowerShell 호환성 기능을 사용 하 여 로드 되었는지 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-115">This allows PowerShell to detect that the module was loaded using Windows PowerShell Compatibility functionality.</span></span>

<span data-ttu-id="f734d-116">세션을 만든 후에는 deserialize 된 개체에서 제대로 작동 하지 않는 작업에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-116">Once the session is created, it can be used for operations that don't work correctly on deserialized objects.</span></span> <span data-ttu-id="f734d-117">전체 파이프라인은 Windows PowerShell에서 실행 되며 최종 결과만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-117">The entire pipeline is executed in Windows PowerShell and only the final result is returned.</span></span> <span data-ttu-id="f734d-118">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f734d-118">For example:</span></span>

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

<span data-ttu-id="f734d-119">호환성 기능은 다음 두 가지 방법으로 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-119">The Compatibility feature can be invoked in two ways:</span></span>

- <span data-ttu-id="f734d-120">명시적으로 **UseWindowsPowerShell** 매개 변수를 사용 하 여 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-120">Explicitly by importing a module using the **UseWindowsPowerShell** parameter</span></span>

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- <span data-ttu-id="f734d-121">명령 검색을 통해 모듈 이름, 경로 또는 자동 로드로 Windows PowerShell 모듈을 가져와 암시적으로.</span><span class="sxs-lookup"><span data-stu-id="f734d-121">Implicitly by importing a Windows PowerShell module by module name, path, or autoloading via command discovery.</span></span>

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   <span data-ttu-id="f734d-122">아직 로드 되지 않은 경우를 실행할 때 AppLocker 모듈이 자동으로 로드 됩니다  `Get-AppLockerPolicy` .</span><span class="sxs-lookup"><span data-stu-id="f734d-122">If not already loaded, the AppLocker module is autoloaded when you run  `Get-AppLockerPolicy`.</span></span>

<span data-ttu-id="f734d-123">Windows PowerShell 호환성은 `WindowsPowerShellCompatibilityModuleDenyList` powershell 구성 파일의 설정에 나열 된 모듈을 로드 하는 것을 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-123">Windows PowerShell Compatibility blocks loading of modules that are listed in the `WindowsPowerShellCompatibilityModuleDenyList` setting in PowerShell configuration file.</span></span>

<span data-ttu-id="f734d-124">이 설정의 기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-124">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a><span data-ttu-id="f734d-125">암시적 모듈 로드 관리</span><span class="sxs-lookup"><span data-stu-id="f734d-125">Managing implicit module loading</span></span>

<span data-ttu-id="f734d-126">Windows PowerShell 호환성 기능의 암시적 가져오기 동작을 사용 하지 않도록 설정 하려면 `DisableImplicitWinCompat` powershell 구성 파일의 설정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-126">To disable implicit import behavior of the Windows PowerShell Compatibility feature, use the `DisableImplicitWinCompat` setting in a PowerShell configuration file.</span></span> <span data-ttu-id="f734d-127">이 설정은 파일에 추가할 수 있습니다 `powershell.config.json` .</span><span class="sxs-lookup"><span data-stu-id="f734d-127">This setting can be added to the `powershell.config.json` file.</span></span> <span data-ttu-id="f734d-128">자세한 내용은 [about_powershell_config](about_powershell_config.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f734d-128">For more information, see [about_powershell_config](about_powershell_config.md).</span></span>

<span data-ttu-id="f734d-129">이 예제에서는 Windows PowerShell 호환성의 암시적 모듈 로드 기능을 사용 하지 않도록 설정 하는 구성 파일을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-129">This example shows how to create a configuration file that disables the implicit module-loading feature of Windows PowerShell Compatibility.</span></span>

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

<span data-ttu-id="f734d-130">모듈 호환성에 대 한 최신 정보는 [PowerShell 7 모듈 호환성](https://aka.ms/PSModuleCompat) 목록을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f734d-130">For more the latest information about module compatibility, see the [PowerShell 7 module compatibility](https://aka.ms/PSModuleCompat) list.</span></span>

### <a name="managing-cmdlet-clobbering"></a><span data-ttu-id="f734d-131">Cmdlet clobbering 관리</span><span class="sxs-lookup"><span data-stu-id="f734d-131">Managing cmdlet clobbering</span></span>

<span data-ttu-id="f734d-132">Windows PowerShell 호환성 기능은 암시적 원격을 사용 하 여 호환성 모드에서 모듈을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-132">The Windows PowerShell Compatibility feature uses implicit remoting to load modules in compatibility mode.</span></span> <span data-ttu-id="f734d-133">그러면 모듈에서 내보낸 명령이 현재 PowerShell 7 세션에서 이름이 같은 명령 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-133">The result is that commands exported by the module take precedence over commands of the same name in the current PowerShell 7 session.</span></span> <span data-ttu-id="f734d-134">PowerShell 7.0.0 릴리스에는 PowerShell과 함께 제공 되는 핵심 모듈이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-134">In the PowerShell 7.0.0 release, this included the core modules that ship with PowerShell.</span></span>

<span data-ttu-id="f734d-135">PowerShell 7.1에서는 다음 핵심 PowerShell 모듈을 레지스터가 하지 않도록 동작이 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-135">In PowerShell 7.1, the behavior was changed so that the following core PowerShell modules are not clobbered:</span></span>

- <span data-ttu-id="f734d-136">ConsoleHost</span><span class="sxs-lookup"><span data-stu-id="f734d-136">Microsoft.PowerShell.ConsoleHost</span></span>
- <span data-ttu-id="f734d-137">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="f734d-137">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="f734d-138">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="f734d-138">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="f734d-139">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="f734d-139">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="f734d-140">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="f734d-140">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="f734d-141">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="f734d-141">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="f734d-142">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="f734d-142">Microsoft.WSMan.Management</span></span>

<span data-ttu-id="f734d-143">PowerShell 7.1에는 호환성 모드로 레지스터가 되지 않아야 하는 추가 모듈을 나열 하는 기능도 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-143">PowerShell 7.1 also added the ability to list additional modules that should not be clobbered by compatibility mode.</span></span>

<span data-ttu-id="f734d-144">`WindowsPowerShellCompatibilityNoClobberModuleList`PowerShell 구성 파일에 설정을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-144">You can add the `WindowsPowerShellCompatibilityNoClobberModuleList` setting to PowerShell configuration file.</span></span> <span data-ttu-id="f734d-145">이 설정의 값은 쉼표로 구분 된 모듈 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-145">The value of this setting is a comma-separated list of module names.</span></span> <span data-ttu-id="f734d-146">이 설정의 기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-146">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a><span data-ttu-id="f734d-147">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f734d-147">Limitations</span></span>

<span data-ttu-id="f734d-148">Windows PowerShell 호환성 기능:</span><span class="sxs-lookup"><span data-stu-id="f734d-148">The Windows PowerShell Compatibility functionality:</span></span>

1. <span data-ttu-id="f734d-149">Windows 컴퓨터 에서만 로컬로 작동</span><span class="sxs-lookup"><span data-stu-id="f734d-149">Only works locally on Windows computers</span></span>
1. <span data-ttu-id="f734d-150">Windows PowerShell 5.1이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-150">Requires that Windows PowerShell 5.1</span></span>
1. <span data-ttu-id="f734d-151">라이브 개체가 아닌 serialize 된 cmdlet 매개 변수 및 반환 값에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-151">Operates on serialized cmdlet parameters and return values, not on live objects</span></span>
1. <span data-ttu-id="f734d-152">Windows PowerShell 원격 세션으로 가져온 모든 모듈은 동일한 runspace를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="f734d-152">All modules imported into the Windows PowerShell remoting session share the same runspace.</span></span>

## <a name="keywords"></a><span data-ttu-id="f734d-153">키워드</span><span class="sxs-lookup"><span data-stu-id="f734d-153">Keywords</span></span>

<span data-ttu-id="f734d-154">about_Windows_PowerShell_Compatibility</span><span class="sxs-lookup"><span data-stu-id="f734d-154">about_Windows_PowerShell_Compatibility</span></span>

## <a name="see-also"></a><span data-ttu-id="f734d-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f734d-155">See also</span></span>

[<span data-ttu-id="f734d-156">about_Modules</span><span class="sxs-lookup"><span data-stu-id="f734d-156">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="f734d-157">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="f734d-157">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

