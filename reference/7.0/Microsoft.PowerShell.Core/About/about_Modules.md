---
description: PowerShell 모듈을 설치, 가져오기 및 사용 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: 79fdfe018539f804933cad2354e11e45f89f724e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222962"
---
# <a name="about-modules"></a><span data-ttu-id="0ce3b-104">모듈 정보</span><span class="sxs-lookup"><span data-stu-id="0ce3b-104">About Modules</span></span>

## <a name="short-description"></a><span data-ttu-id="0ce3b-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="0ce3b-105">Short Description</span></span>
<span data-ttu-id="0ce3b-106">PowerShell 모듈을 설치, 가져오기 및 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-106">Explains how to install, import, and use PowerShell modules.</span></span>

## <a name="long-description"></a><span data-ttu-id="0ce3b-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="0ce3b-107">Long Description</span></span>

<span data-ttu-id="0ce3b-108">모듈은 cmdlet, 공급자, 함수, 워크플로, 변수, 별칭 등의 PowerShell 명령을 포함 하는 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-108">A module is a package that contains PowerShell commands, such as cmdlets, providers, functions, workflows, variables, and aliases.</span></span>

<span data-ttu-id="0ce3b-109">명령을 작성하는 사용자는 모듈을 사용하여 자신의 명령을 구성하고 다른 사용자와 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-109">People who write commands can use modules to organize their commands and share them with others.</span></span> <span data-ttu-id="0ce3b-110">모듈을 받는 사용자는 모듈의 명령을 PowerShell 세션에 추가 하 고 기본 제공 명령과 같은 방법으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-110">People who receive modules can add the commands in the modules to their PowerShell sessions and use them just like the built-in commands.</span></span>

<span data-ttu-id="0ce3b-111">이 항목에서는 PowerShell 모듈을 사용 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-111">This topic explains how to use PowerShell modules.</span></span> <span data-ttu-id="0ce3b-112">PowerShell 모듈을 작성 하는 방법에 대 한 자세한 내용은 [Powershell 모듈 작성](/powershell/scripting/developer/module/writing-a-windows-powershell-module)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-112">For information about how to write PowerShell modules, see [Writing a PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="what-is-a-module"></a><span data-ttu-id="0ce3b-113">모듈 이란?</span><span class="sxs-lookup"><span data-stu-id="0ce3b-113">What Is a Module?</span></span>

<span data-ttu-id="0ce3b-114">모듈은 명령의 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-114">A module is a package of commands.</span></span> <span data-ttu-id="0ce3b-115">세션의 모든 cmdlet 및 공급자는 모듈 또는 스냅인에 의해 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-115">All cmdlets and providers in your session are added by a module or a snap-in.</span></span>

## <a name="module-auto-loading"></a><span data-ttu-id="0ce3b-116">모듈 자동 로드</span><span class="sxs-lookup"><span data-stu-id="0ce3b-116">Module Auto-Loading</span></span>

<span data-ttu-id="0ce3b-117">PowerShell 3.0부터 PowerShell은 설치 된 모듈에서 명령을 처음 실행할 때 자동으로 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-117">Beginning in PowerShell 3.0, PowerShell imports modules automatically the first time that you run any command in an installed module.</span></span> <span data-ttu-id="0ce3b-118">이제는 설정 및 프로필 구성 없이도 모듈의 명령을 사용할 수 있으므로 컴퓨터에 모듈을 설치한 후에 모듈을 관리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-118">You can now use the commands in a module without any set-up or profile configuration, so there's no need to manage modules after you install them on your computer.</span></span>

<span data-ttu-id="0ce3b-119">또한 모듈의 명령이 보다 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-119">The commands in a module are also easier to find.</span></span> <span data-ttu-id="0ce3b-120">`Get-Command`이제 cmdlet은 아직 세션에 있지 않더라도 설치 된 모든 모듈의 모든 명령을 가져오므로 명령을 검색 하지 않고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-120">The `Get-Command` cmdlet now gets all commands in all installed modules, even if they are not yet in the session, so you can find a command and use it without importing.</span></span>

<span data-ttu-id="0ce3b-121">다음의 각 예에서는를 포함 하는 CimCmdlets 모듈을 `Get-CimInstance` 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-121">Each of the following examples cause the CimCmdlets module, which contains `Get-CimInstance`, to be imported into your session.</span></span>

- <span data-ttu-id="0ce3b-122">명령 실행</span><span class="sxs-lookup"><span data-stu-id="0ce3b-122">Run the Command</span></span>

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- <span data-ttu-id="0ce3b-123">명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="0ce3b-123">Get the Command</span></span>

  ```powershell
  Get-Command Get-CimInstance
  ```

- <span data-ttu-id="0ce3b-124">명령에 대 한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="0ce3b-124">Get Help for the Command</span></span>

  ```powershell
  Get-Help Get-CimInstance
  ```

<span data-ttu-id="0ce3b-125">`Get-Command` 와일드 카드 문자 ()를 포함 하는 명령은 `*` 검색을 위해 사용 하지 않는 것으로 간주 되며 모듈을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-125">`Get-Command` commands that include a wildcard character (`*`) are considered to be for discovery, not use, and do not import any modules.</span></span>

<span data-ttu-id="0ce3b-126">PSModulePath 환경 변수에 지정 된 위치에 저장 된 모듈만 자동으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-126">Only modules that are stored in the location specified by the PSModulePath environment variable are automatically imported.</span></span> <span data-ttu-id="0ce3b-127">Cmdlet을 실행 하면 다른 위치의 모듈을 가져와야 합니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="0ce3b-127">Modules in other locations must be imported by running the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="0ce3b-128">또한 PowerShell 공급자를 사용 하는 명령은 모듈을 자동으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-128">Also, commands that use PowerShell providers do not automatically import a module.</span></span> <span data-ttu-id="0ce3b-129">예를 들어 cmdlet과 같이 WSMan: 드라이브가 필요한 명령을 사용 하는 경우이 cmdlet을 `Get-PSSessionConfiguration` 실행 하 여 `Import-Module` 드라이브를 포함 하는 **Microsoft-wsman. 관리** 모듈을 가져와야 할 수 있습니다. `WSMan:`</span><span class="sxs-lookup"><span data-stu-id="0ce3b-129">For example, if you use a command that requires the WSMan: drive, such as the `Get-PSSessionConfiguration` cmdlet, you might need to run the `Import-Module` cmdlet to import the **Microsoft.WSMan.Management** module that includes the `WSMan:` drive.</span></span>

<span data-ttu-id="0ce3b-130">명령을 계속 실행 하 여 `Import-Module` 모듈을 가져오고 변수를 사용 하 여 `$PSModuleAutoloadingPreference` 모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-130">You can still run the `Import-Module` command to import a module and use the `$PSModuleAutoloadingPreference` variable to enable, disable and configure automatic importing of modules.</span></span> <span data-ttu-id="0ce3b-131">자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-131">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="how-to-use-a-module"></a><span data-ttu-id="0ce3b-132">모듈을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0ce3b-132">How to Use a Module</span></span>

<span data-ttu-id="0ce3b-133">모듈을 사용하려면 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-133">To use a module, perform the following tasks:</span></span>

1. <span data-ttu-id="0ce3b-134">모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-134">Install the module.</span></span> <span data-ttu-id="0ce3b-135">대부분의 경우 이 작업은 자동으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-135">(This is often done for you.)</span></span>
1. <span data-ttu-id="0ce3b-136">모듈에서 추가한 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-136">Find the commands that the module added.</span></span>
1. <span data-ttu-id="0ce3b-137">모듈에서 추가한 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-137">Use the commands that the module added.</span></span>

<span data-ttu-id="0ce3b-138">항목에서는 이러한 작업을 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-138">This topic explains how to perform these tasks.</span></span> <span data-ttu-id="0ce3b-139">또한 모듈 관리에 대한 유용한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-139">It also includes other useful information about managing modules.</span></span>

## <a name="how-to-install-a-module"></a><span data-ttu-id="0ce3b-140">모듈을 설치 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0ce3b-140">How to Install a Module</span></span>

<span data-ttu-id="0ce3b-141">파일이 포함 된 폴더로 모듈을 수신 하는 경우 PowerShell에서 사용 하기 전에 컴퓨터에 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-141">If you receive a module as a folder with files in it, you need to install it on your computer before you can use it in PowerShell.</span></span>

<span data-ttu-id="0ce3b-142">대부분의 모듈은 자동으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-142">Most modules are installed for you.</span></span> <span data-ttu-id="0ce3b-143">PowerShell은 몇 가지 미리 설치 된 모듈 ( _핵심_ 모듈 이라고 함)과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-143">PowerShell comes with several preinstalled modules, sometimes called the _core_ modules.</span></span> <span data-ttu-id="0ce3b-144">Windows 기반 컴퓨터에서 운영 체제에 포함 된 기능에 관리 하는 cmdlet이 있는 경우 해당 모듈은 사전 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-144">On Windows-based computers, if features that are included with the operating system have cmdlets to manage them, those modules are preinstalled.</span></span> <span data-ttu-id="0ce3b-145">Windows 기능을 설치 하는 경우 예를 들어 서버 관리자의 역할 및 기능 추가 마법사 또는 제어판의 Windows 기능 사용/사용 안 함 대화 상자를 사용 하 여 기능에 포함 된 모든 PowerShell 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-145">When you install a Windows feature, by using, for example, the Add Roles and Features Wizard in Server Manager, or the Turn Windows features on or off dialog box in Control Panel, any PowerShell modules that are part of the feature are installed.</span></span> <span data-ttu-id="0ce3b-146">다른 대부분의 모듈은 모듈을 설치하는 설치 관리자나 설치 프로그램에 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-146">Many other modules come in an installer or Setup program that installs the module.</span></span>

<span data-ttu-id="0ce3b-147">다음 명령을 사용 하 여 현재 사용자의 **Modules** 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-147">Use the following command to create a **Modules** directory for the current user:</span></span>

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="0ce3b-148">전체 모듈 폴더를 Modules 디렉터리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-148">Copy the entire module folder into the Modules directory.</span></span> <span data-ttu-id="0ce3b-149">모든 방법을 사용 하 여 Windows 탐색기, Cmd.exe 및 PowerShell을 포함 하 여 폴더를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-149">You can use any method to copy the folder, including Windows Explorer and Cmd.exe, as well as PowerShell.</span></span> <span data-ttu-id="0ce3b-150">PowerShell에서 cmdlet을 사용 `Copy-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-150">In PowerShell use the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="0ce3b-151">예를 들어에서 MyModule 폴더를 `C:\ps-test\MyModule` Modules 디렉터리에 복사 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-151">For example, to copy the MyModule folder from `C:\ps-test\MyModule` to the Modules directory, type:</span></span>

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="0ce3b-152">원하는 어떤 위치에도 모듈을 설치할 수 있지만 기본 모듈 위치에 모듈을 설치하면 관리하기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-152">You can install a module in any location, but installing your modules in a default module location makes them easier to manage.</span></span> <span data-ttu-id="0ce3b-153">기본 모듈 위치에 대 한 자세한 내용은 [모듈 및 DSC 리소스 위치 및 PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-153">For more information about the default module locations, see the [Module and DSC Resource Locations, and PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) section.</span></span>

## <a name="how-to-find-installed-modules"></a><span data-ttu-id="0ce3b-154">설치 된 모듈을 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="0ce3b-154">How to Find Installed Modules</span></span>

<span data-ttu-id="0ce3b-155">기본 모듈 위치에 설치되었으나 세션에 아직 가져오지 않은 모듈을 찾으려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-155">To find modules that are installed in a default module location, but not yet imported into your session, type:</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="0ce3b-156">이미 세션으로 가져온 모듈을 찾으려면 PowerShell 프롬프트에서 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-156">To find the modules that have already been imported into your session, at the PowerShell prompt, type:</span></span>

```powershell
Get-Module
```

<span data-ttu-id="0ce3b-157">Cmdlet에 대 한 자세한 내용은 `Get-Module` [import-module](xref:Microsoft.PowerShell.Core.Get-Module)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-157">For more information about the `Get-Module` cmdlet, see [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

## <a name="how-to-find-the-commands-in-a-module"></a><span data-ttu-id="0ce3b-158">모듈의 명령을 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="0ce3b-158">How to Find the Commands in a Module</span></span>

<span data-ttu-id="0ce3b-159">Cmdlet을 사용 `Get-Command` 하 여 사용 가능한 모든 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-159">Use the `Get-Command` cmdlet to find all available commands.</span></span> <span data-ttu-id="0ce3b-160">Cmdlet의 매개 변수를 사용 `Get-Command` 하 여 모듈, 이름 및 명사 등의 명령을 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-160">You can use the parameters of the `Get-Command` cmdlet to filter commands such as by module, name, and noun.</span></span>

<span data-ttu-id="0ce3b-161">모듈의 명령을 모두 찾으려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-161">To find all commands in a module, type:</span></span>

```powershell
Get-Command -Module <module-name>
```

<span data-ttu-id="0ce3b-162">예를 들어 BitsTransfer 모듈의 명령을 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-162">For example, to find the commands in the BitsTransfer module, type:</span></span>

```powershell
Get-Command -Module BitsTransfer
```

<span data-ttu-id="0ce3b-163">Cmdlet에 대 한 자세한 내용은 `Get-Command` [get-help](xref:Microsoft.PowerShell.Core.Get-Command)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-163">For more information about the `Get-Command` cmdlet, see [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command).</span></span>

## <a name="how-to-get-help-for-the-commands-in-a-module"></a><span data-ttu-id="0ce3b-164">모듈의 명령에 대 한 도움말을 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="0ce3b-164">How to Get Help for the Commands in a Module</span></span>

<span data-ttu-id="0ce3b-165">모듈에 내보내는 명령에 대 한 도움말 파일이 포함 되어 있는 경우 `Get-Help` cmdlet에 도움말 항목이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-165">If the module contains Help files for the commands that it exports, the `Get-Help` cmdlet will display the Help topics.</span></span> <span data-ttu-id="0ce3b-166">`Get-Help`PowerShell에서 명령에 대 한 도움말을 가져오는 데 사용 하는 것과 동일한 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-166">Use the same `Get-Help` command format that you would use to get help for any command in PowerShell.</span></span>

<span data-ttu-id="0ce3b-167">PowerShell 3.0부터 모듈에 대 한 도움말 파일을 다운로드 하 고 도움말 파일에 대 한 업데이트를 다운로드 하 여 사용 되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-167">Beginning in PowerShell 3.0, you can download Help files for a module and download updates to the Help files so they are never obsolete.</span></span>

<span data-ttu-id="0ce3b-168">모듈의 명령에 대한 도움말을 보려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-168">To get help for a commands in a module, type:</span></span>

```powershell
Get-Help <command-name>
```

<span data-ttu-id="0ce3b-169">모듈의 명령에 대 한 온라인 도움말을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-169">To get help online for command in a module, type:</span></span>

```powershell
Get-Help <command-name> -Online
```

<span data-ttu-id="0ce3b-170">모듈의 명령에 대 한 도움말 파일을 다운로드 하 여 설치 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-170">To download and install the help files for the commands in a module, type:</span></span>

```powershell
Update-Help -Module <module-name>
```

<span data-ttu-id="0ce3b-171">자세한 내용은 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 및 [update-help](xref:Microsoft.PowerShell.Core.Update-Help)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-171">For more information, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help).</span></span>

## <a name="how-to-import-a-module"></a><span data-ttu-id="0ce3b-172">모듈을 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="0ce3b-172">How to Import a Module</span></span>

<span data-ttu-id="0ce3b-173">모듈을 가져오거나 모듈 파일을 가져와야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-173">You might have to import a module or import a module file.</span></span> <span data-ttu-id="0ce3b-174">가져오기는 모듈이 **PSModulePath** 환경 변수, 또는로 지정 된 위치에 설치 되어 있지 않거나, `$env:PSModulePath` 모듈이 폴더로 배달 되는 일반적인 모듈이 아니라 .dll 또는. .psm1 파일과 같은 파일로 구성 된 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-174">Importing is required when a module is not installed in the locations specified by the **PSModulePath** environment variable, `$env:PSModulePath`, or the module consists of file, such as a .dll or .psm1 file, instead of typical module that is delivered as a folder.</span></span>

<span data-ttu-id="0ce3b-175">`Import-Module`가져온 모든 명령의 명사 이름에 고유한 접두사를 추가 하는 prefix 매개 변수 또는 모듈이 세션의 기존 명령을 숨기 거 나 바꾸는 명령을 추가 하지 못하게 하는 **NoClobber** 매개 변수 등 명령의 매개 변수를 사용할 수 있도록 모듈을 가져오도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-175">You might also choose to import a module so that you can use the parameters of the `Import-Module` command, such as the Prefix parameter, which adds a distinctive prefix to the noun names of all imported commands, or the **NoClobber** parameter, which prevents the module from adding commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="0ce3b-176">모듈을 가져오려면 cmdlet을 사용 `Import-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-176">To import modules, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="0ce3b-177">PSModulePath 위치의 모듈을 현재 세션으로 가져오려면 다음 명령 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-177">To import modules in a PSModulePath location into the current session, use the following command format.</span></span>

```powershell
Import-Module <module-name>
```

<span data-ttu-id="0ce3b-178">예를 들어 다음 명령은 BitsTransfer 모듈을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-178">For example, the following command imports the BitsTransfer module into the current session.</span></span>

```powershell
Import-Module BitsTransfer
```

<span data-ttu-id="0ce3b-179">기본 모듈 위치에 없는 모듈을 가져오려면 명령에서 모듈 폴더에 대한 정규화된 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-179">To import a module that is not in a default module location, use the fully qualified path to the module folder in the command.</span></span>

<span data-ttu-id="0ce3b-180">예를 들어 디렉터리의 TestCmdlets 모듈을 `C:\ps-test` 세션에 추가 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-180">For example, to add the TestCmdlets module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets
```

<span data-ttu-id="0ce3b-181">모듈 폴더에 없는 모듈 파일을 가져오려면 명령에 모듈 파일에 대한 정규화된 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-181">To import a module file that is not contained in a module folder, use the fully qualified path to the module file in the command.</span></span>

<span data-ttu-id="0ce3b-182">예를 들어 디렉터리의 TestCmdlets.dll 모듈을 `C:\ps-test` 세션에 추가 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-182">For example, to add the TestCmdlets.dll module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

<span data-ttu-id="0ce3b-183">세션에 모듈을 추가 하는 방법에 대 한 자세한 내용은 [import-module](xref:Microsoft.PowerShell.Core.Import-Module)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-183">For more information about adding modules to your session, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="how-to-import-a-module-into-every-session"></a><span data-ttu-id="0ce3b-184">모듈을 모든 세션으로 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="0ce3b-184">How to Import a Module into Every Session</span></span>

<span data-ttu-id="0ce3b-185">이 `Import-Module` 명령은 모듈을 현재 PowerShell 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-185">The `Import-Module` command imports modules into your current PowerShell session.</span></span> <span data-ttu-id="0ce3b-186">시작 하는 모든 PowerShell 세션으로 모듈을 가져오려면 `Import-Module` powershell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-186">To import a module into every PowerShell session that you start, add the `Import-Module` command to your PowerShell profile.</span></span>

<span data-ttu-id="0ce3b-187">프로필에 대한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-187">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="how-to-remove-a-module"></a><span data-ttu-id="0ce3b-188">모듈을 제거 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0ce3b-188">How to Remove a Module</span></span>

<span data-ttu-id="0ce3b-189">모듈을 제거하면 모듈에서 추가한 명령이 세션에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-189">When you remove a module, the commands that the module added are deleted from the session.</span></span>

<span data-ttu-id="0ce3b-190">세션에서 모듈을 제거 하려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-190">To remove a module from your session, use the following command format.</span></span>

```powershell
Remove-Module <module-name>
```

<span data-ttu-id="0ce3b-191">예를 들어 다음 명령은 현재 세션에서 BitsTransfer 모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-191">For example, the following command removes the BitsTransfer module from the current session.</span></span>

```powershell
Remove-Module BitsTransfer
```

<span data-ttu-id="0ce3b-192">모듈을 제거하는 작업은 모듈을 가져오는 작업과 반대입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-192">Removing a module reverses the operation of importing a module.</span></span> <span data-ttu-id="0ce3b-193">모듈을 제거해도 모듈이 제거되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-193">Removing a module does not uninstall the module.</span></span> <span data-ttu-id="0ce3b-194">자세한 내용은 [Remove 모듈](xref:Microsoft.PowerShell.Core.Remove-Module)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-194">For more information, see [Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module).</span></span>

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a><span data-ttu-id="0ce3b-195">모듈 및 DSC 리소스 위치 및 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="0ce3b-195">Module and DSC Resource Locations, and PSModulePath</span></span>

<span data-ttu-id="0ce3b-196">`$env:PSModulePath`환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-196">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="0ce3b-197">기본적으로에 할당 되는 유효 위치는 `$env:PSModulePath` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-197">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="0ce3b-198">시스템 차원의 위치: `$PSHOME\Modules`</span><span class="sxs-lookup"><span data-stu-id="0ce3b-198">System-wide locations: `$PSHOME\Modules`</span></span>

  <span data-ttu-id="0ce3b-199">이러한 폴더에는 Windows 및 PowerShell과 함께 제공 되는 모듈이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-199">These folders contain modules that ship with Windows and PowerShell.</span></span>

  <span data-ttu-id="0ce3b-200">PowerShell에 포함 된 DSC 리소스는 폴더에 저장 됩니다 `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` .</span><span class="sxs-lookup"><span data-stu-id="0ce3b-200">DSC resources that are included with PowerShell are stored in the `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` folder.</span></span>

- <span data-ttu-id="0ce3b-201">사용자 지정 모듈: 사용자의 범위에 사용자가 설치 하는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-201">User-specific modules: These are modules installed by the user in the user's scope.</span></span> <span data-ttu-id="0ce3b-202">`Install-Module` 에는 현재 사용자 또는 모든 사용자에 대해 모듈이 설치 되어 있는지 여부를 지정할 수 있는 **범위** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-202">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="0ce3b-203">자세한 내용은 [모듈 설치](xref:PowerShellGet.Install-Module)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-203">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  <span data-ttu-id="0ce3b-204">Windows의 사용자 관련 **CurrentUser** 위치는 `PowerShell\Modules` 사용자 프로필의 **문서** 위치에 있는 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-204">The user-specific **CurrentUser** location on Windows is the `PowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="0ce3b-205">해당 위치의 특정 경로는 Windows의 버전에 따라 다르며 폴더 리디렉션을 사용 하는지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-205">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="0ce3b-206">Microsoft OneDrive는 **문서** 폴더의 위치를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-206">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span>

  <span data-ttu-id="0ce3b-207">기본적으로 Windows 10의 경우 해당 위치는 `$HOME\Documents\PowerShell\Modules` 입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-207">By default, on Windows 10, that location is `$HOME\Documents\PowerShell\Modules`.</span></span> <span data-ttu-id="0ce3b-208">Linux 또는 Mac에서 **CurrentUser** 위치는 `$HOME/.local/share/powershell/Modules` 입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-208">On Linux or Mac, the **CurrentUser** location is `$HOME/.local/share/powershell/Modules`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0ce3b-209">다음 명령을 사용 하 여 **문서** 폴더의 위치를 확인할 수 있습니다 `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="0ce3b-209">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

- <span data-ttu-id="0ce3b-210">**AllUsers** 위치는 `$env:PROGRAMFILES\PowerShell\Modules` Windows에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-210">The **AllUsers** location is `$env:PROGRAMFILES\PowerShell\Modules` on Windows.</span></span> <span data-ttu-id="0ce3b-211">Linux 또는 Mac에서 모듈은에 저장 됩니다 `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="0ce3b-211">On Linux or Mac the modules are stored at `/usr/local/share/powershell/Modules`.</span></span>

> [!NOTE]
> <span data-ttu-id="0ce3b-212">디렉터리에서 파일을 추가 하거나 변경 하려면 `$env:Windir\System32` **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-212">To add or change files in the `$env:Windir\System32` directory, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="0ce3b-213">**PSModulePath** 환경 변수의 값을 변경 하 여 시스템에서 기본 모듈 위치를 변경할 수 있습니다 `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="0ce3b-213">You can change the default module locations on your system by changing the value of the **PSModulePath** environment variable, `$Env:PSModulePath`.</span></span> <span data-ttu-id="0ce3b-214">**PSModulePath** 환경 변수는 Path 환경 변수에서 모델링 되며 동일한 형식을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-214">The **PSModulePath** environment variable is modeled on the Path environment variable and has the same format.</span></span>

<span data-ttu-id="0ce3b-215">기본 모듈 위치를 보려면 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-215">To view the default module locations, type:</span></span>

```powershell
$Env:PSModulePath
```

<span data-ttu-id="0ce3b-216">기본 모듈 위치를 추가하려면 다음 명령 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-216">To add a default module location, use the following command format.</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

<span data-ttu-id="0ce3b-217">명령의 세미콜론 ()은 `;` 목록에서 앞에 나오는 경로와 새 경로를 분리 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-217">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="0ce3b-218">예를 들어 디렉터리를 추가 하려면 `C:\ps-test\Modules` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-218">For example, to add the `C:\ps-test\Modules` directory, type:</span></span>

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

<span data-ttu-id="0ce3b-219">Linux 또는 MacOS에서 기본 모듈 위치를 추가 하려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-219">To add a default module location on Linux or MacOS, use the following command format:</span></span>

```powershell
$Env:PSModulePath += ":<path>"
```

<span data-ttu-id="0ce3b-220">예를 들어 `/usr/local/Fabrikam/Modules` **PSModulePath** 환경 변수의 값에 디렉터리를 추가 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-220">For example, to add the `/usr/local/Fabrikam/Modules` directory to the value of the **PSModulePath** environment variable, type:</span></span>

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

<span data-ttu-id="0ce3b-221">Linux 또는 MacOS에서 명령의 콜론 ( `:` )은 목록에서 앞에 나오는 경로와 새 경로를 분리 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-221">On Linux or MacOS, the colon (`:`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="0ce3b-222">**PSModulePath** 에 경로를 추가 하면 `Get-Module` 및 명령에 `Import-Module` 해당 경로에 있는 모듈이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-222">When you add a path to **PSModulePath** , `Get-Module` and `Import-Module` commands include modules in that path.</span></span>

<span data-ttu-id="0ce3b-223">설정한 값은 현재 세션에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-223">The value that you set affects only the current session.</span></span> <span data-ttu-id="0ce3b-224">변경 내용을 영구적으로 적용 하려면 PowerShell 프로필에 명령을 추가 하거나 제어판의 시스템을 사용 하 여 레지스트리에서 **PSModulePath** 환경 변수의 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-224">To make the change persistent, add the command to your PowerShell profile or use System in Control Panel to change the value of the **PSModulePath** environment variable in the registry.</span></span>

<span data-ttu-id="0ce3b-225">또한 변경 내용을 영구적으로 적용 하려면 SetEnvironmentVariable 클래스의 **SetEnvironmentVariable** 메서드를 사용 하 여 **PSModulePath** 환경 변수에 대 한 경로를 추가할 수 **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="0ce3b-225">Also, to make the change persistent, you can also use the **SetEnvironmentVariable** method of the **System.Environment** class to add a Path to the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="0ce3b-226">**PSModulePath** 변수에 대 한 자세한 내용은 [about_Environment_Variables](about_Environment_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-226">For more information about the **PSModulePath** variable, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

## <a name="modules-and-name-conflicts"></a><span data-ttu-id="0ce3b-227">모듈 및 이름 충돌</span><span class="sxs-lookup"><span data-stu-id="0ce3b-227">Modules and Name Conflicts</span></span>

<span data-ttu-id="0ce3b-228">세션에 이름이 동일한 명령이 두 개 이상 있을 경우 이름이 충돌합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-228">Name conflicts occur when more than one command in the session has the same name.</span></span> <span data-ttu-id="0ce3b-229">모듈의 명령이 세션의 명령 또는 항목과 동일한 이름을 가질 경우 모듈을 가져올 때 이름 충돌을 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-229">Importing a module causes a name conflict when commands in the module have the same names as commands or items in the session.</span></span>

<span data-ttu-id="0ce3b-230">이름 충돌로 인해 명령이 숨겨지거나 바뀔 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-230">Name conflicts can result in commands being hidden or replaced.</span></span>

### <a name="hidden"></a><span data-ttu-id="0ce3b-231">숨김</span><span class="sxs-lookup"><span data-stu-id="0ce3b-231">Hidden</span></span>

<span data-ttu-id="0ce3b-232">명령 이름을 입력할 때 실행되는 명령이 아니고 명령을 시작한 모듈이나 스냅인의 이름으로 명령 이름을 정규화하는 것과 같은 기타 방법을 사용하여 실행할 수 있을 때 명령은 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-232">A command is hidden when it is not the command that runs when you type the command name, but you can run it by using another method, such as by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

### <a name="replaced"></a><span data-ttu-id="0ce3b-233">대체됨</span><span class="sxs-lookup"><span data-stu-id="0ce3b-233">Replaced</span></span>

<span data-ttu-id="0ce3b-234">동일한 이름의 명령 파일로 덮어쓰였으므로 명령을 실행할 수 없는 경우 명령이 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-234">A command is replaced when you cannot run it because it has been overwritten by a command with the same name.</span></span> <span data-ttu-id="0ce3b-235">충돌을 유발한 모듈을 제거하더라도 세션을 다시 시작해야만 바뀐 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-235">Even when you remove the module that caused the conflict, you cannot run a replaced command unless you restart the session.</span></span>

<span data-ttu-id="0ce3b-236">`Import-Module` 현재 세션의 명령을 숨기 거 나 바꾸는 명령을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-236">`Import-Module` might add commands that hide and replace commands in the current session.</span></span> <span data-ttu-id="0ce3b-237">또한 세션의 명령이 모듈에서 추가한 명령을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-237">Also, commands in your session can hide commands that the module added.</span></span>

<span data-ttu-id="0ce3b-238">이름 충돌을 검색 하려면 cmdlet의 **All** 매개 변수를 사용 합니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="0ce3b-238">To detect name conflicts, use the **All** parameter of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="0ce3b-239">PowerShell 3.0부터 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-239">Beginning in PowerShell 3.0, `Get-Command` gets only that commands that run when you type the command name.</span></span> <span data-ttu-id="0ce3b-240">**All** 매개 변수는 세션에서 특정 이름의 명령을 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-240">The **All** parameter gets all commands with the specific name in the session.</span></span>

<span data-ttu-id="0ce3b-241">이름 충돌을 방지 하려면 cmdlet의 **NoClobber** 또는 **Prefix** 매개 변수를 사용 합니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="0ce3b-241">To prevent name conflicts, use the **NoClobber** or **Prefix** parameters of the `Import-Module` cmdlet.</span></span> <span data-ttu-id="0ce3b-242">**Prefix** 매개 변수는 세션에서 고유 하도록 가져온 명령의 이름에 접두사를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-242">The **Prefix** parameter adds a prefix to the names of imported commands so that they are unique in the session.</span></span> <span data-ttu-id="0ce3b-243">**NoClobber** 매개 변수는 세션의 기존 명령을 숨기 거 나 바꾸는 명령은 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-243">The **NoClobber** parameter does not import any commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="0ce3b-244">의 **Alias** , **Cmdlet** , **Function** 및 **Variable** 매개 변수를 사용 `Import-Module` 하 여 가져올 명령만 선택할 수 있으며, 세션에서 이름 충돌을 일으키는 명령을 제외할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-244">You can also use the **Alias** , **Cmdlet** , **Function** , and **Variable** parameters of `Import-Module` to select only the commands that you want to import, and you can exclude commands that cause name conflicts in your session.</span></span>

<span data-ttu-id="0ce3b-245">모듈 작성자는 모듈 매니페스트의 **Defaultcommandprefix** 속성을 사용 하 여 모든 명령 이름에 기본 접두사를 추가 함으로써 이름 충돌을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-245">Module authors can prevent name conflicts by using the **DefaultCommandPrefix** property of the module manifest to add a default prefix to all command names.</span></span>
<span data-ttu-id="0ce3b-246">**Prefix** 매개 변수 값은 **defaultcommandprefix** 값 보다 우선 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-246">The value of the **Prefix** parameter takes precedence over the value of **DefaultCommandPrefix**.</span></span>

<span data-ttu-id="0ce3b-247">명령이 숨겨지더라도 명령을 시작한 모듈이나 스냅인의 이름으로 명령 이름을 정규화하여 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-247">Even if a command is hidden, you can run it by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

<span data-ttu-id="0ce3b-248">PowerShell 명령 우선 순위 규칙은 세션에 같은 이름의 명령이 포함 된 경우 실행 되는 명령을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-248">The PowerShell command precedence rules determine which command runs when the session includes commands with the same name.</span></span>

<span data-ttu-id="0ce3b-249">예를 들어 세션에 이름이 같은 함수 및 cmdlet이 포함 되어 있는 경우 PowerShell은 기본적으로 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-249">For example, when a session includes a function and a cmdlet with the same name, PowerShell runs the function by default.</span></span> <span data-ttu-id="0ce3b-250">세션에 이름과 형식이 같은 명령이 포함된 경우(예: 이름이 같은 두 개의 cmdlet) 기본적으로 가장 최근에 추가한 명령이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-250">When the session includes commands of the same type with the same name, such as two cmdlets with the same name, by default, it runs the most recently added command.</span></span>

<span data-ttu-id="0ce3b-251">선행 규칙에 대 한 설명 및 숨겨진 명령 실행에 대 한 지침을 비롯 한 자세한 내용은 [about_Command_Precedence](about_Command_Precedence.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-251">For more information, including an explanation of the precedence rules and instructions for running hidden commands, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

## <a name="modules-and-snap-ins"></a><span data-ttu-id="0ce3b-252">모듈 및 스냅인</span><span class="sxs-lookup"><span data-stu-id="0ce3b-252">Modules and Snap-ins</span></span>

<span data-ttu-id="0ce3b-253">모듈 및 스냅인에서 세션에 명령을 추가할 수 있습니다. 모듈은 cmdlet, 공급자, 함수 및 항목 (예: 변수, 별칭 및 PowerShell 드라이브)을 비롯 한 모든 유형의 명령을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-253">You can add commands to your session from modules and snap-ins. Modules can add all types of commands, including cmdlets, providers, and functions, and items, such as variables, aliases, and PowerShell drives.</span></span> <span data-ttu-id="0ce3b-254">스냅인에서는 cmdlet과 공급자만 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-254">Snap-ins can add only cmdlets and providers.</span></span>

<span data-ttu-id="0ce3b-255">사용자 세션에서 모듈이나 스냅인을 제거하기 전에 다음 명령을 사용하여 제거할 명령을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-255">Before removing a module or snap-in from your session, use the following commands to determine which commands will be removed.</span></span>

<span data-ttu-id="0ce3b-256">세션에서 cmdlet의 원본을 찾으려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-256">To find the source of a cmdlet in your session, use the following command format:</span></span>

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

<span data-ttu-id="0ce3b-257">예를 들어 cmdlet의 원본을 찾으려면 다음과 같이 `Get-Date` 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-257">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a><span data-ttu-id="0ce3b-258">모듈 관련 경고 및 오류</span><span class="sxs-lookup"><span data-stu-id="0ce3b-258">Module-related Warnings and Errors</span></span>

<span data-ttu-id="0ce3b-259">모듈에서 내보내는 명령은 PowerShell 명령 명명 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-259">The commands that a module exports should follow the PowerShell command naming rules.</span></span> <span data-ttu-id="0ce3b-260">가져오는 모듈이 이름에 승인 되지 않은 동사가 포함 된 cmdlet 또는 함수를 내보내는 경우 `Import-Module` cmdlet은 다음 경고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-260">If the module that you import exports cmdlets or functions that have unapproved verbs in their names, the `Import-Module` cmdlet displays the following warning message.</span></span>

> <span data-ttu-id="0ce3b-261">경고: 일부 가져온 명령 이름에는 검색 하기 어려울 수 있는 승인 되지 않은 동사가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-261">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="0ce3b-262">자세한 내용을 보려면 Verbose 매개 변수를 사용하거나 승인된 동사 목록을 보려면 Get-Verb를 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-262">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="0ce3b-263">이 메시지는 경고일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-263">This message is only a warning.</span></span> <span data-ttu-id="0ce3b-264">비준수 명령을 포함하여 전체 모듈을 계속 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-264">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="0ce3b-265">메시지가 모듈 사용자에게 표시되더라도 명명 문제는 모듈 작성자가 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-265">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

<span data-ttu-id="0ce3b-266">경고 메시지를 표시 하지 않으려면 cmdlet의 **DisableNameChecking** 매개 변수를 사용 합니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="0ce3b-266">To suppress the warning message, use the **DisableNameChecking** parameter of the `Import-Module` cmdlet.</span></span>

## <a name="built-in-modules-and-snap-ins"></a><span data-ttu-id="0ce3b-267">기본 제공 모듈 및 스냅인</span><span class="sxs-lookup"><span data-stu-id="0ce3b-267">Built-in Modules and Snap-ins</span></span>

<span data-ttu-id="0ce3b-268">Powershell 2.0 및 powershell 3.0 이상의 이전 스타일 호스트 프로그램에서 powershell과 함께 설치 되는 핵심 명령은 모든 PowerShell 세션에 자동으로 추가 되는 스냅인에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-268">In PowerShell 2.0 and in older-style host programs in PowerShell 3.0 and later, the core commands that are installed with PowerShell are packaged in snap-ins that are added automatically to every PowerShell session.</span></span>

<span data-ttu-id="0ce3b-269">PowerShell 3.0부터 초기 세션 상태 API를 구현 하는 호스트 프로그램의 경우 `InitialSessionState.CreateDefault2` 기본적으로 모든 세션에 Microsoft. PowerShell. 코어 스냅인이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-269">Beginning in PowerShell 3.0, for host programs that implement the `InitialSessionState.CreateDefault2` initial session state API the Microsoft.PowerShell.Core snap-in is added to every session by default.</span></span> <span data-ttu-id="0ce3b-270">모듈은 처음 사용할 때 자동으로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-270">Modules are loaded automatically on first-use.</span></span>

> [!NOTE]
> <span data-ttu-id="0ce3b-271">Cmdlet을 사용 하 여 시작 된 세션을 비롯 한 원격 세션 `New-PSSession` 은 기본 제공 명령이 스냅인에 패키지 되는 이전 스타일의 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-271">Remote sessions, including sessions that are started by using the `New-PSSession` cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="0ce3b-272">다음 모듈 (또는 스냅인)은 PowerShell과 함께 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-272">The following modules (or snap-ins) are installed with PowerShell.</span></span>

- <span data-ttu-id="0ce3b-273">CimCmdlets</span><span class="sxs-lookup"><span data-stu-id="0ce3b-273">CimCmdlets</span></span>
- <span data-ttu-id="0ce3b-274">Microsoft.PowerShell.Archive</span><span class="sxs-lookup"><span data-stu-id="0ce3b-274">Microsoft.PowerShell.Archive</span></span>
- <span data-ttu-id="0ce3b-275">Microsoft.PowerShell.Core</span><span class="sxs-lookup"><span data-stu-id="0ce3b-275">Microsoft.PowerShell.Core</span></span>
- <span data-ttu-id="0ce3b-276">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="0ce3b-276">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="0ce3b-277">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="0ce3b-277">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="0ce3b-278">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="0ce3b-278">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="0ce3b-279">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="0ce3b-279">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="0ce3b-280">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="0ce3b-280">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="0ce3b-281">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="0ce3b-281">Microsoft.WSMan.Management</span></span>
- <span data-ttu-id="0ce3b-282">PackageManagement</span><span class="sxs-lookup"><span data-stu-id="0ce3b-282">PackageManagement</span></span>
- <span data-ttu-id="0ce3b-283">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="0ce3b-283">PowerShellGet</span></span>
- <span data-ttu-id="0ce3b-284">PSDesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0ce3b-284">PSDesiredStateConfiguration</span></span>
- <span data-ttu-id="0ce3b-285">PSDiagnostics</span><span class="sxs-lookup"><span data-stu-id="0ce3b-285">PSDiagnostics</span></span>
- <span data-ttu-id="0ce3b-286">PSReadline</span><span class="sxs-lookup"><span data-stu-id="0ce3b-286">PSReadline</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="0ce3b-287">모듈 이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="0ce3b-287">Logging Module Events</span></span>

<span data-ttu-id="0ce3b-288">PowerShell 3.0부터 모듈 및 스냅인의 **LogPipelineExecutionDetails** 속성을로 설정 하 여 powershell 모듈 및 스냅인의 cmdlet 및 함수에 대 한 실행 이벤트를 기록할 수 있습니다 `$True` .</span><span class="sxs-lookup"><span data-stu-id="0ce3b-288">Beginning in PowerShell 3.0, you can record execution events for the cmdlets and functions in PowerShell modules and snap-ins by setting the **LogPipelineExecutionDetails** property of modules and snap-ins to `$True`.</span></span>
<span data-ttu-id="0ce3b-289">그룹 정책 설정인 모듈 로깅을 설정 하 여 모든 PowerShell 세션에서 모듈 로깅을 사용 하도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-289">You can also use a Group Policy setting, Turn on Module Logging, to enable module logging in all PowerShell sessions.</span></span> <span data-ttu-id="0ce3b-290">자세한 내용은 로깅 및 그룹 정책 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0ce3b-290">For more information, see the logging and group policy articles.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ce3b-291">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ce3b-291">See Also</span></span>

[<span data-ttu-id="0ce3b-292">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="0ce3b-292">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="0ce3b-293">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="0ce3b-293">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="0ce3b-294">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="0ce3b-294">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="0ce3b-295">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="0ce3b-295">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="0ce3b-296">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="0ce3b-296">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="0ce3b-297">Get-Command</span><span class="sxs-lookup"><span data-stu-id="0ce3b-297">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="0ce3b-298">Get-Help</span><span class="sxs-lookup"><span data-stu-id="0ce3b-298">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="0ce3b-299">Get-Module</span><span class="sxs-lookup"><span data-stu-id="0ce3b-299">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="0ce3b-300">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="0ce3b-300">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="0ce3b-301">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="0ce3b-301">Remove-Module</span></span>](xref:Microsoft.PowerShell.Core.Remove-Module)
