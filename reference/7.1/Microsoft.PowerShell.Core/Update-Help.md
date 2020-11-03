---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: d2b80640a5cdc985d34e39fe608950ea5f4dfe2d
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "93219138"
---
# <span data-ttu-id="93684-103">Update-Help</span><span class="sxs-lookup"><span data-stu-id="93684-103">Update-Help</span></span>

## <span data-ttu-id="93684-104">개요</span><span class="sxs-lookup"><span data-stu-id="93684-104">SYNOPSIS</span></span>
<span data-ttu-id="93684-105">최신 도움말 파일을 다운로드하여 컴퓨터에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-105">Downloads and installs the newest help files on your computer.</span></span>

## <span data-ttu-id="93684-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="93684-106">SYNTAX</span></span>

### <span data-ttu-id="93684-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="93684-107">Path (Default)</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="93684-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="93684-108">LiteralPath</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="93684-109">설명</span><span class="sxs-lookup"><span data-stu-id="93684-109">DESCRIPTION</span></span>

<span data-ttu-id="93684-110">`Update-Help`Cmdlet은 PowerShell 모듈에 대 한 최신 도움말 파일을 다운로드 하 여 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-110">The `Update-Help` cmdlet downloads the newest help files for PowerShell modules and installs them on your computer.</span></span> <span data-ttu-id="93684-111">변경 내용을 적용 하려면 PowerShell을 다시 시작 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-111">You need not restart PowerShell to make the change effective.</span></span> <span data-ttu-id="93684-112">Cmdlet을 사용 `Get-Help` 하 여 새 도움말 파일을 즉시 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-112">You can use the `Get-Help` cmdlet to view the new help files immediately.</span></span>

<span data-ttu-id="93684-113">`Update-Help` 컴퓨터에 있는 도움말 파일의 버전을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-113">`Update-Help` checks the version of the help files on your computer.</span></span> <span data-ttu-id="93684-114">모듈에 대 한 도움말 파일이 없거나 도움말 파일이 오래 된 경우에서 `Update-Help` 최신 도움말 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-114">If you don't have help files for a module or if your help files are outdated, `Update-Help` downloads the newest help files.</span></span> <span data-ttu-id="93684-115">도움말 파일은 인터넷 또는 파일 공유에서 다운로드 하 여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-115">The help files can be downloaded and installed from the internet or a file share.</span></span>

<span data-ttu-id="93684-116">매개 변수를 사용 하지 않으면는 `Update-Help` 세션 및 업데이트할 수 있는 도움말을 지 원하는 모든 설치 된 모듈에 대 한 도움말 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-116">Without parameters, `Update-Help` updates the help files for modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="93684-117">현재 세션에 설치 되어 있지만 로드 되지 않은 모듈은 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-117">Modules that are installed but not loaded in the current session are included.</span></span> <span data-ttu-id="93684-118">PowerShell 모듈은 환경 변수에 나열 된 위치에 저장 됩니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="93684-118">PowerShell modules are stored in a location listed in the `$env:PSModulePath` environment variable.</span></span> <span data-ttu-id="93684-119">자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93684-119">For more information, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

<span data-ttu-id="93684-120">**Module** 매개 변수를 사용 하 여 특정 모듈에 대 한 도움말 파일을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-120">You can use the **Module** parameter to update help files for a particular module.</span></span> <span data-ttu-id="93684-121">**UICulture** 매개 변수를 사용 하 여 여러 언어 및 로캘로 도움말 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-121">Use the **UICulture** parameter to download help files in multiple languages and locales.</span></span>

<span data-ttu-id="93684-122">인터넷에 연결 되지 않은 컴퓨터 에서도를 사용할 수 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-122">You can also use `Update-Help` on computers that are not connected to the internet.</span></span> <span data-ttu-id="93684-123">먼저, cmdlet을 사용 `Save-Help` 하 여 인터넷에서 도움말 파일을 다운로드 하 고 인터넷에 연결 되지 않은 시스템에서 액세스할 수 있는 공유 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-123">First, use the `Save-Help`cmdlet to download help files from the internet and save them in a shared folder that is accessible to the system not connected to the internet.</span></span> <span data-ttu-id="93684-124">그런 다음의 **SourcePath** 매개 변수를 사용 `Update-Help` 하 여 공유에서 업데이트 된 도움말 파일을 다운로드 하 고 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-124">Then use the **SourcePath** parameter of `Update-Help` to download the updated help files from the shared and install them on the computer.</span></span>

<span data-ttu-id="93684-125">PowerShell 프로필에 cmdlet을 추가 하 여 도움말 업데이트를 자동화할 수 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-125">You can automate help updates by adding the `Update-Help` cmdlet to your PowerShell profile.</span></span> <span data-ttu-id="93684-126">기본적으로는 `Update-Help` 각 컴퓨터에서 하루에 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-126">By default, `Update-Help` runs only one time per day on each computer.</span></span> <span data-ttu-id="93684-127">매일 한 번이라는 제한을 재정의하려면 **Force** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-127">To override the once-per-day limit, use the **Force** parameter.</span></span>

<span data-ttu-id="93684-128">`Update-Help`이 cmdlet은 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-128">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93684-129">`Update-Help` PowerShell 6.0 및 아래에서 관리 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-129">`Update-Help` requires administrative privileges in PowerShell 6.0 and below.</span></span>
> <span data-ttu-id="93684-130">PowerShell 6.1 이상에서는 기본 **범위** 를로 설정 `CurrentUser` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-130">PowerShell 6.1 and above set the default **Scope** to `CurrentUser`.</span></span>
> <span data-ttu-id="93684-131">PowerShell 6.1 이전에는 **범위** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-131">Prior to PowerShell 6.1, the **Scope** parameter was not available.</span></span>
>
> <span data-ttu-id="93684-132">PowerShell 핵심 모듈에 대 한 도움말 파일을 업데이트 하려면 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-132">You must be a member of the Administrators group on the computer to update the help files for the PowerShell Core modules.</span></span>
>
> <span data-ttu-id="93684-133">Powershell Core 모듈을 비롯 하 여 powershell 설치 디렉터리 ()의 모듈에 대 한 도움말 파일을 다운로드 하거나 업데이트 하려면 `$PSHOME\Modules` **관리자 권한으로 실행** 옵션을 사용 하 여 powershell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-133">To download or update the help files for modules in the PowerShell installation directory (`$PSHOME\Modules`), including the PowerShell Core modules, start PowerShell by using the **Run as administrator** option.</span></span>
> <span data-ttu-id="93684-134">예: `Start-Process pwsh.exe -Verb RunAs`</span><span class="sxs-lookup"><span data-stu-id="93684-134">For example: `Start-Process pwsh.exe -Verb RunAs`.</span></span>

## <span data-ttu-id="93684-135">예제</span><span class="sxs-lookup"><span data-stu-id="93684-135">EXAMPLES</span></span>

### <span data-ttu-id="93684-136">예 1: 모든 모듈에 대 한 도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="93684-136">Example 1: Update help files for all modules</span></span>

<span data-ttu-id="93684-137">`Update-Help`Cmdlet은 업데이트할 수 있는 도움말을 지 원하는 설치 된 모듈에 대 한 도움말 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-137">The `Update-Help` cmdlet updates help files for installed modules that support Updatable Help.</span></span> <span data-ttu-id="93684-138">운영 체제에서 UI (사용자 인터페이스) 문화권 언어를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-138">The user-interface (UI) culture language is set in the operating system.</span></span>

```powershell
Update-Help
```

### <span data-ttu-id="93684-139">예 2: 지정 된 모듈에 대 한 도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="93684-139">Example 2: Update help files for specified modules</span></span>

<span data-ttu-id="93684-140">`Update-Help`이 cmdlet은 **Microsoft PowerShell** 로 시작 하는 모듈 이름에 대해서만 도움말 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-140">The `Update-Help` cmdlet updates help files only for module names that begin with **Microsoft.PowerShell**.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### <span data-ttu-id="93684-141">예 3: 다른 언어에 대 한 도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="93684-141">Example 3: Update help files for different languages</span></span>

<span data-ttu-id="93684-142">이 `Update-Help` cmdlet은 모든 모듈에 대해 일본어 (ja-jp) 및 영어 (en-us) 도움말 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-142">The `Update-Help` cmdlet updates the Japanese (ja-JP) and English (en-US) help files for all modules.</span></span>

<span data-ttu-id="93684-143">모듈에서 지정 된 UI 문화권에 대 한 도움말 파일을 제공 하지 않으면 모듈 및 UI 문화권에 대 한 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-143">If a module doesn't provide help files for a specified UI culture, an error message is displayed for the module and UI culture.</span></span> <span data-ttu-id="93684-144">이 예제에서 오류 메시지는 모듈 **Microsoft. PowerShell** 에 대 한 **ja-jp** 도움말 파일을 찾을 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93684-144">In this example, the error message indicates that the **ja-JP** help files were not found for module **Microsoft.PowerShell.Utility**.</span></span>

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### <span data-ttu-id="93684-145">예제 4: 파일 공유에서 여러 컴퓨터에 대 한 도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="93684-145">Example 4: Update help files on multiple computers from a file share</span></span>

<span data-ttu-id="93684-146">이 예제에서 업데이트 된 도움말 파일은 인터넷에서 다운로드 되 고 파일 공유에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-146">In this example, updated help files are downloaded from the internet and saved in a file share.</span></span> <span data-ttu-id="93684-147">파일 공유에 액세스 하 고 업데이트를 설치할 수 있는 권한이 있는 사용자 자격 증명이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-147">User credentials are needed that have permissions to access the file share and install updates.</span></span> <span data-ttu-id="93684-148">파일 공유를 사용 하는 경우 방화벽으로 보호 되거나 인터넷에 연결 되지 않은 컴퓨터를 업데이트 하는 것이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-148">When a file share is used, it's possible to update computers that are behind firewalls or aren't connected to the internet.</span></span>

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

<span data-ttu-id="93684-149">`Save-Help`명령은 업데이트할 수 있는 도움말을 지 원하는 모든 모듈에 대 한 최신 도움말 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-149">The `Save-Help` command downloads the newest help files for all modules that support Updatable Help.</span></span>
<span data-ttu-id="93684-150">**DestinationPath** 매개 변수는 파일 공유에 파일을 저장 합니다 `\\Server01\Share\PSHelp` .</span><span class="sxs-lookup"><span data-stu-id="93684-150">The **DestinationPath** parameter saves the files in the `\\Server01\Share\PSHelp` file share.</span></span> <span data-ttu-id="93684-151">**Credential** 매개 변수는 파일 공유에 액세스할 수 있는 권한을 가진 사용자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-151">The **Credential** parameter specifies a user who has permission to access the file share.</span></span>

<span data-ttu-id="93684-152">`Invoke-Command`Cmdlet은 `Update-Help` 여러 컴퓨터에서 원격 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-152">The `Invoke-Command` cmdlet runs remote `Update-Help` commands on multiple computers.</span></span> <span data-ttu-id="93684-153">**ComputerName** 매개 변수는 **Servers.txt** 파일에서 원격 컴퓨터의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="93684-153">The **ComputerName** parameter gets a list of remote computers from the **Servers.txt** file.</span></span> <span data-ttu-id="93684-154">**ScriptBlock** 매개 변수는 `Update-Help` 명령을 실행 하 고 **SourcePath** 매개 변수를 사용 하 여 업데이트 된 도움말 파일을 포함 하는 파일 공유를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-154">The **ScriptBlock** parameter runs the `Update-Help` command and uses the **SourcePath** parameter to specify the file share that contains the updated help files.</span></span> <span data-ttu-id="93684-155">**Credential** 매개 변수는 파일 공유에 액세스 하 고 원격 명령을 실행할 수 있는 사용자를 지정 합니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-155">The **Credential** parameter specifies a user who can access the file share and run the remote `Update-Help` command.</span></span>

### <span data-ttu-id="93684-156">예 5: 업데이트 된 도움말 파일 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="93684-156">Example 5: Get a list of updated help files</span></span>

<span data-ttu-id="93684-157">`Update-Help`Cmdlet은 지정 된 모듈에 대 한 도움말을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-157">The `Update-Help` cmdlet updates help for a specified module.</span></span> <span data-ttu-id="93684-158">이 cmdlet은 **Verbose** 일반 매개 변수를 사용 하 여 업데이트 된 도움말 파일의 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-158">The cmdlet uses the **Verbose** common parameter to display the list of help files that were updated.</span></span> <span data-ttu-id="93684-159">**자세한 정보** 표시를 사용 하 여 특정 모듈에 대 한 모든 도움말 파일 또는 도움말 파일의 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-159">You can use **Verbose** to view output for all help files or help files for a specific module.</span></span>

<span data-ttu-id="93684-160">**Verbose** 매개 변수를 사용 하지 않으면 `Update-Help` 명령 결과를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-160">Without the **Verbose** parameter, `Update-Help` doesn't display the results of the command.</span></span> <span data-ttu-id="93684-161">**Verbose** 매개 변수 출력은 도움말 파일이 업데이트 되었는지 또는 최신 버전이 설치 되어 있는지 확인 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-161">The **Verbose** parameter output is useful to verify that the help files were updated or if the latest version is installed.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### <span data-ttu-id="93684-162">예제 6: 업데이트할 수 있는 도움말을 지 원하는 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="93684-162">Example 6: Find modules that support Updatable Help</span></span>

<span data-ttu-id="93684-163">이 예제에서는 업데이트할 수 있는 도움말을 지 원하는 모듈을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-163">This example lists modules that support Updatable Help.</span></span> <span data-ttu-id="93684-164">이 명령은 모듈의 **HelpInfoUri** 속성을 사용 하 여 업데이트할 수 있는 도움말을 지 원하는 모듈을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-164">The command uses the module's **HelpInfoUri** property to identify modules that support Updatable Help.</span></span> <span data-ttu-id="93684-165">**HelpInfoUri** 속성에는 cmdlet이 실행 될 때 리디렉션되는 주소가 포함 되어 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-165">The **HelpInfoUri** property contains an address that is redirected when the `Update-Help` cmdlet is run.</span></span>

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### <span data-ttu-id="93684-166">예 7: 업데이트 된 도움말 파일 인벤토리</span><span class="sxs-lookup"><span data-stu-id="93684-166">Example 7: Inventory updated help files</span></span>

<span data-ttu-id="93684-167">이 예제에서 스크립트는 `Get-UpdateHelpVersion.ps1` 각 모듈 및 해당 버전 번호에 대해 업데이트할 수 있는 도움말 파일의 인벤토리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93684-167">In this example, the script `Get-UpdateHelpVersion.ps1` creates an inventory of the Updatable Help files for each module and their version numbers.</span></span>

<span data-ttu-id="93684-168">스크립트는 모듈의 **HelpInfoUri** 속성을 사용 하 여 업데이트할 수 있는 도움말을 지 원하는 모듈을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-168">The script identifies modules that support Updatable Help by using the **HelpInfoUri** property of modules.</span></span> <span data-ttu-id="93684-169">업데이트할 수 있는 도움말을 지 원하는 모듈의 경우 스크립트는 도움말 정보 파일 (\* helpinfo.xml)을 찾고 구문 분석 하 여 최신 버전 번호를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-169">For modules that support Updatable Help, the script looks for and parses the help information file (\*helpinfo.xml) to find the latest version number.</span></span>

<span data-ttu-id="93684-170">이 스크립트는 **PSCustomObject** 클래스 및 해시 테이블을 사용 하 여 사용자 지정 출력 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93684-170">The script uses the **PSCustomObject** class and a hash table to create a custom output object.</span></span>

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## <span data-ttu-id="93684-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="93684-171">PARAMETERS</span></span>

### <span data-ttu-id="93684-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="93684-172">-Credential</span></span>

<span data-ttu-id="93684-173">**SourcePath** 로 지정 된 파일 시스템 위치에 액세스할 수 있는 권한이 있는 사용자의 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-173">Specifies credentials of a user who has permission to access the file system location specified by **SourcePath**.</span></span> <span data-ttu-id="93684-174">이 매개 변수는 **SourcePath** 또는 **LiteralPath** 매개 변수가 명령에 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-174">This parameter is valid only when the **SourcePath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="93684-175">**Credential** 매개 변수를 사용 하면 `Update-Help` 원격 컴퓨터에서 **SourcePath** 매개 변수를 사용 하 여 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-175">The **Credential** parameter enables you to run `Update-Help` commands with the **SourcePath** parameter on remote computers.</span></span> <span data-ttu-id="93684-176">명시적 자격 증명을 제공 하 여 원격 컴퓨터에서 명령을 실행 하 고 액세스 거부 오류가 발생 하거나 CredSSP 인증을 사용 하 여 자격 증명을 위임 하지 않고도 세 번째 컴퓨터의 파일 공유에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-176">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="93684-177">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="93684-177">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="93684-178">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-178">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="93684-179">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-179">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="93684-180">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="93684-180">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93684-181">-Force</span><span class="sxs-lookup"><span data-stu-id="93684-181">-Force</span></span>

<span data-ttu-id="93684-182">이 cmdlet은 하루에 한 번만 수행 하 고, 버전 검사를 건너뛰고, 1gb 제한을 초과 하는 파일을 다운로드 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93684-182">Indicates that this cmdlet doesn't follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="93684-183">이 매개 변수를 사용 하지 않으면은 `Update-Help` 24 시간 마다 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-183">Without this parameter, `Update-Help` runs only once in each 24-hour period.</span></span> <span data-ttu-id="93684-184">다운로드는 모듈 별로 압축 되지 않은 1gb로 제한 되며, 도움말 파일은 컴퓨터의 기존 파일 보다 최신 버전인 경우에만 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-184">Downloads are limited to 1 GB of uncompressed content per module and help files are only installed when they're newer than the existing files on the computer.</span></span>

<span data-ttu-id="93684-185">매일 한 번 제한은 도움말 파일을 호스트 하는 서버를 보호 하 고, 반복 되는 `Update-Help` 연결 또는 다운로드의 리소스 비용을 들이지 않고 PowerShell 프로필에 명령을 추가 하는 것이 실용적입니다.</span><span class="sxs-lookup"><span data-stu-id="93684-185">The once-per-day limit protects the servers that host the help files and makes it practical for you to add an `Update-Help` command to your PowerShell profile without incurring the resource cost of repeated connections or downloads.</span></span>

<span data-ttu-id="93684-186">**Force** 매개 변수 없이 여러 UI 문화권의 모듈에 대한 도움말을 업데이트하려면 동일한 명령에 모든 UI 문화권을 포함합니다. 예:</span><span class="sxs-lookup"><span data-stu-id="93684-186">To update help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as:</span></span>

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93684-187">-변수인 fullyqualifiedmodule</span><span class="sxs-lookup"><span data-stu-id="93684-187">-FullyQualifiedModule</span></span>

<span data-ttu-id="93684-188">**ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-188">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="93684-189">이러한 모듈은 [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 설명 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-189">These modules are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="93684-190">예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식으로 지정 된 모듈 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-190">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

<span data-ttu-id="93684-191">또는</span><span class="sxs-lookup"><span data-stu-id="93684-191">or</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

<span data-ttu-id="93684-192">**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="93684-192">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="93684-193">**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-193">You can't specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93684-194">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="93684-194">-LiteralPath</span></span>

<span data-ttu-id="93684-195">인터넷에서 다운로드 하는 대신 업데이트 된 도움말 파일에 대 한 폴더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-195">Specifies the folder for updated help files instead of downloading them from the internet.</span></span> <span data-ttu-id="93684-196">Cmdlet을 사용 하 **SourcePath** 여 `Save-Help` 디렉터리에 도움말 파일을 다운로드 한 경우이 매개 변수 또는 SourcePath를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-196">Use this parameter or **SourcePath** if you've used the `Save-Help` cmdlet to download help files to a directory.</span></span>

<span data-ttu-id="93684-197">또는 cmdlet과 같은 디렉터리 개체를로 파이프라인을 만들 수 있습니다 `Get-Item` `Get-ChildItem` `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-197">You can pipeline a directory object, such as from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="93684-198">**SourcePath** 의 값과 달리 **LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-198">Unlike the value of **SourcePath** , the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="93684-199">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-199">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="93684-200">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="93684-200">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="93684-201">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-201">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93684-202">-모듈</span><span class="sxs-lookup"><span data-stu-id="93684-202">-Module</span></span>

<span data-ttu-id="93684-203">지정된 모듈에 대한 도움말을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-203">Updates help for the specified modules.</span></span> <span data-ttu-id="93684-204">쉼표로 구분 된 목록에 하나 이상의 모듈 이름 또는 이름 패턴을 입력 하거나 각 줄에 하나의 모듈 이름을 나열 하는 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-204">Enter one or more module names or name patterns in a comma-separated list, or specify a file that lists one module name on each line.</span></span> <span data-ttu-id="93684-205">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-205">Wildcard characters are permitted.</span></span> <span data-ttu-id="93684-206">Cmdlet에서 cmdlet으로 모듈 파이프라인을 만들 수 있습니다 `Get-Module` `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-206">You can pipeline modules from the `Get-Module` cmdlet to the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="93684-207">지정 하는 모듈은 컴퓨터에 설치 해야 하지만 현재 세션으로 가져올 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-207">The modules that you specify must be installed on the computer, but they don't have to be imported into the current session.</span></span> <span data-ttu-id="93684-208">환경 변수에 나열 된 위치에 설치 된 모듈 또는 세션의 모든 모듈을 지정할 수 있습니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="93684-208">You can specify any module in the session or any module that is installed in a location listed in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="93684-209">값 `*` (모두)은 컴퓨터에 설치 되어 있는 모든 모듈에 대 한 도움말을 업데이트 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-209">A value of `*` (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="93684-210">업데이트할 수 있는 도움말을 지원 하지 않는 모듈은 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-210">Modules that don't support Updatable Help are included.</span></span> <span data-ttu-id="93684-211">이 값은 명령이 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 발견 하면 오류를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-211">This value might generate errors when the command encounters modules that don't support Updatable Help.</span></span> <span data-ttu-id="93684-212">대신 `Update-Help` 매개 변수 없이 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-212">Instead, run `Update-Help` without parameters.</span></span>

<span data-ttu-id="93684-213">Cmdlet의 **module** 매개 변수는 `Update-Help` 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-213">The **Module** parameter of the `Update-Help` cmdlet doesn't accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="93684-214">위치에 없는 모듈에 대 한 도움말을 업데이트 하려면 `$env:PSModulePath` 명령을 실행 하기 전에 모듈을 현재 세션으로 가져옵니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-214">To update help for a module that isn't in a `$env:PSModulePath` location, import the module into the current session before you run the `Update-Help` command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="93684-215">-재귀</span><span class="sxs-lookup"><span data-stu-id="93684-215">-Recurse</span></span>

<span data-ttu-id="93684-216">지정 된 디렉터리에 있는 도움말 파일에 대 한 재귀 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-216">Performs a recursive search for help files in the specified directory.</span></span> <span data-ttu-id="93684-217">이 매개 변수는 명령에서 **SourcePath** 매개 변수를 사용 하는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-217">This parameter is valid only when the command uses the **SourcePath** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93684-218">-범위</span><span class="sxs-lookup"><span data-stu-id="93684-218">-Scope</span></span>

<span data-ttu-id="93684-219">도움말이 업데이트 되는 시스템 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-219">Specifies the system scope where help is updated.</span></span> <span data-ttu-id="93684-220">**AllUsers** 범위의 업데이트에는 Windows 시스템에 대 한 관리 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-220">Updates at the **AllUsers** scope require administrative privileges on Windows systems.</span></span> <span data-ttu-id="93684-221">`-Scope`매개 변수는 PowerShell Core 버전 6.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-221">The `-Scope` parameter was introduced in PowerShell Core version 6.1.</span></span>

<span data-ttu-id="93684-222">**CurrentUser** 는 PowerShell 6.1 이상에서 도움말 파일에 대 한 기본 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="93684-222">**CurrentUser** is the default scope for help files in PowerShell 6.1 and above.</span></span> <span data-ttu-id="93684-223">**AllUsers** 를 지정 하 여 모든 사용자에 대 한 도움말을 설치 하거나 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-223">**AllUsers** can be specified to install or update help for all users.</span></span> <span data-ttu-id="93684-224">Unix 시스템에서 `sudo` 모든 사용자에 대 한 도움말을 업데이트 하려면 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-224">On Unix systems `sudo` privileges are required to update help for all users.</span></span> <span data-ttu-id="93684-225">`sudo pwsh -c Update-Help`</span><span class="sxs-lookup"><span data-stu-id="93684-225">For example: `sudo pwsh -c Update-Help`</span></span>

<span data-ttu-id="93684-226">사용 가능한 값은</span><span class="sxs-lookup"><span data-stu-id="93684-226">The acceptable values are:</span></span>

- <span data-ttu-id="93684-227">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="93684-227">CurrentUser</span></span>
- <span data-ttu-id="93684-228">AllUsers</span><span class="sxs-lookup"><span data-stu-id="93684-228">AllUsers</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93684-229">-SourcePath</span><span class="sxs-lookup"><span data-stu-id="93684-229">-SourcePath</span></span>

<span data-ttu-id="93684-230">가 `Update-Help` 인터넷에서 다운로드 하는 대신 업데이트 된 도움말 파일을 가져오는 파일 시스템 폴더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-230">Specifies a file system folder where `Update-Help` gets updated help files, instead of downloading them from the internet.</span></span> <span data-ttu-id="93684-231">폴더의 경로를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-231">Enter the path of a folder.</span></span> <span data-ttu-id="93684-232">파일 이름 또는 파일 이름 확장명을 지정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="93684-232">Don't specify a file name or file name extension.</span></span> <span data-ttu-id="93684-233">또는 cmdlet의 폴더와 같은 폴더를로 파이프라인을 만들 수 있습니다 `Get-Item` `Get-ChildItem` `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-233">You can pipeline a folder, such as one from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="93684-234">기본적으로는 `Update-Help` 업데이트 된 도움말 파일을 인터넷에서 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-234">By default, `Update-Help` downloads updated help files from the internet.</span></span> <span data-ttu-id="93684-235">Cmdlet **SourcePath** 을 사용 `Save-Help` 하 여 업데이트 된 도움말 파일을 디렉터리에 다운로드 한 경우 SourcePath를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-235">Use **SourcePath** when you've used the `Save-Help` cmdlet to download updated help files to a directory.</span></span>

<span data-ttu-id="93684-236">**SourcePath** 의 기본값을 지정 하려면 **그룹 정책** , **컴퓨터 구성** 으로 이동 하 여 **update-help에 대 한 기본 원본 경로를 설정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-236">To specify a default value for **SourcePath** , go to **Group Policy** , **Computer Configuration** , and **Set the default source path for Update-Help**.</span></span> <span data-ttu-id="93684-237">이 그룹 정책 설정은 사용자가를 사용 하 여 `Update-Help` 인터넷에서 도움말 파일을 다운로드 하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-237">This Group Policy setting prevents users from using `Update-Help` to download help files from the internet.</span></span>
<span data-ttu-id="93684-238">자세한 내용은 [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93684-238">For more information, see [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93684-239">-UICulture</span><span class="sxs-lookup"><span data-stu-id="93684-239">-UICulture</span></span>

<span data-ttu-id="93684-240">`Update-Help`에서 업데이트 된 도움말 파일을 가져오는 데 사용 하는 UI 문화권 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-240">Specifies UI culture values that `Update-Help` uses to get updated help files.</span></span> <span data-ttu-id="93684-241">하나 이상의 언어 코드 (예: **es)** , culture 개체를 포함 하는 변수 또는 문화권 개체를 가져오는 명령 (예: 또는 명령)을 입력 `Get-Culture` `Get-UICulture` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-241">Enter one or more language codes, such as **es-ES** , a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span> <span data-ttu-id="93684-242">와일드 카드 문자를 사용할 수 없으며 **de** 와 같은 부분 언어 코드를 제출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-242">Wildcard characters aren't permitted and you can't submit a partial language code, such as **de**.</span></span>

<span data-ttu-id="93684-243">기본적으로는 `Update-Help` 운영 체제에 대해 설정 된 UI 문화권의 도움말 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="93684-243">By default, `Update-Help` gets help files in the UI culture set for the operating system.</span></span> <span data-ttu-id="93684-244">**UICulture** 매개 변수를 지정 하는 경우는 `Update-Help` 지정 된 UI 문화권에 대 한 도움말만 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-244">If you specify the **UICulture** parameter, `Update-Help` looks for help only for the specified UI culture.</span></span>

> [!NOTE]
> <span data-ttu-id="93684-245">Ubuntu 18.04에서 기본 로캘 설정을 인식할 수 `C.UTF.8` 없는 UI 문화권이 아닌로 변경 했습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-245">Ubuntu 18.04 changed the default locale setting to `C.UTF.8`, which is not a recognized UI culture.</span></span> <span data-ttu-id="93684-246">`Update-Help` 와 같은 지원 되는 로캘에서이 매개 변수를 사용 하지 않는 한 자동으로 도움말 다운로드에 실패 `en-US` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-246">`Update-Help` silently fails to download help unless you use this parameter with a supported locale like `en-US`.</span></span> <span data-ttu-id="93684-247">지원 되지 않는 값을 사용 하는 모든 플랫폼에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-247">This could occur on any platform that uses an unsupported value.</span></span>

<span data-ttu-id="93684-248">**UICulture** 매개 변수를 사용하는 명령은 모듈이 지정된 UI 문화권에 대한 도움말 파일을 제공하는 경우에 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-248">Commands that use the **UICulture** parameter succeed only when the module provides help files for the specified UI culture.</span></span> <span data-ttu-id="93684-249">지정 된 UI 문화권이 지원 되지 않기 때문에 명령이 실패 하면 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-249">If the command fails because the specified UI culture isn't supported, an error message is displayed.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93684-250">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="93684-250">-UseDefaultCredentials</span></span>

<span data-ttu-id="93684-251">에서 `Update-Help` 현재 사용자의 자격 증명을 사용 하 여 인터넷 다운로드를 포함 하 여 명령을 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93684-251">Indicates that `Update-Help` runs the command, including the internet download, by using the credentials of the current user.</span></span> <span data-ttu-id="93684-252">기본적으로 명령은 명시적 자격 증명 없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-252">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="93684-253">이 매개 변수는 웹 다운로드에서 NTLM (NT LAN Manager), 협상 또는 Kerberos 기반 인증을 사용 하는 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-253">This parameter is effective only when the web download uses NT LAN Manager (NTLM), negotiate, or Kerberos-based authentication.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93684-254">-Confirm</span><span class="sxs-lookup"><span data-stu-id="93684-254">-Confirm</span></span>

<span data-ttu-id="93684-255">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-255">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93684-256">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="93684-256">-WhatIf</span></span>

<span data-ttu-id="93684-257">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-257">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="93684-258">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-258">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93684-259">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="93684-259">CommonParameters</span></span>

<span data-ttu-id="93684-260">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="93684-260">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="93684-261">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93684-261">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="93684-262">입력</span><span class="sxs-lookup"><span data-stu-id="93684-262">INPUTS</span></span>

### <span data-ttu-id="93684-263">System.io.directoryinfo</span><span class="sxs-lookup"><span data-stu-id="93684-263">System.IO.DirectoryInfo</span></span>

<span data-ttu-id="93684-264">디렉터리 경로를로 파이프 할 수 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-264">You can pipe a directory path to `Update-Help`.</span></span>

### <span data-ttu-id="93684-265">System.object..</span><span class="sxs-lookup"><span data-stu-id="93684-265">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="93684-266">Cmdlet에서로 모듈 개체를 파이프 할 수 있습니다 `Get-Module` `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="93684-266">You can pipe a module object from the `Get-Module` cmdlet to `Update-Help`.</span></span>

## <span data-ttu-id="93684-267">출력</span><span class="sxs-lookup"><span data-stu-id="93684-267">OUTPUTS</span></span>

### <span data-ttu-id="93684-268">없음</span><span class="sxs-lookup"><span data-stu-id="93684-268">None</span></span>

<span data-ttu-id="93684-269">`Update-Help` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-269">`Update-Help` doesn't generate any output.</span></span>

## <span data-ttu-id="93684-270">참고</span><span class="sxs-lookup"><span data-stu-id="93684-270">NOTES</span></span>

<span data-ttu-id="93684-271">Powershell과 함께 설치 되는 명령 또는 디렉터리의 모듈을 포함 하는 PowerShell 핵심 모듈에 대 한 도움말을 업데이트 하려면 `$PSHOME\Modules` **관리자 권한으로 실행** 하는 옵션을 사용 하 여 powershell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-271">To update help for the PowerShell Core modules, that contain the commands that are installed with PowerShell, or any module in the `$PSHOME\Modules` directory, start PowerShell with the option to **Run as administrator**.</span></span>

<span data-ttu-id="93684-272">컴퓨터의 Administrators 그룹 구성원만 PowerShell 핵심 모듈에 대 한 도움말, PowerShell과 함께 설치 되는 명령, 폴더의 모듈에 대 한 도움말을 업데이트할 수 있습니다 `$PSHOME\Modules` .</span><span class="sxs-lookup"><span data-stu-id="93684-272">Only members of the Administrators group on the computer can update help for the PowerShell Core modules, the commands that are installed together with PowerShell, and for modules in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="93684-273">도움말 파일을 업데이트할 수 있는 권한이 없는 경우 온라인으로 도움말 파일을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-273">If you don't have permission to update help files, you can read the help files online.</span></span> <span data-ttu-id="93684-274">예들 들어 `Get-Help Update-Help -Online`입니다.</span><span class="sxs-lookup"><span data-stu-id="93684-274">For example, `Get-Help Update-Help -Online`.</span></span>

<span data-ttu-id="93684-275">모듈은 업데이트할 수 있는 도움말의 가장 작은 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="93684-275">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="93684-276">특정 cmdlet에 대 한 도움말을 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-276">You can't update help for a particular cmdlet.</span></span> <span data-ttu-id="93684-277">특정 cmdlet이 포함 된 모듈을 찾으려면 cmdlet의 **ModuleName** 속성 (예:)을 사용 `Get-Command` `(Get-Command Update-Help).ModuleName` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-277">To find the module that contains a particular cmdlet, use the **ModuleName** property of the `Get-Command` cmdlet, for example, `(Get-Command Update-Help).ModuleName`.</span></span>

<span data-ttu-id="93684-278">도움말 파일이 모듈 디렉터리에 설치 되어 있기 때문에 `Update-Help` cmdlet은 컴퓨터에 설치 된 모듈에 대해서만 업데이트 된 도움말 파일을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-278">Because help files are installed in the module directory, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span> <span data-ttu-id="93684-279">그러나 cmdlet은 `Save-Help` 컴퓨터에 설치 되지 않은 모듈에 대 한 도움말을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-279">However, the `Save-Help` cmdlet can save help for modules that aren't installed on the computer.</span></span>

<span data-ttu-id="93684-280">에서 `Update-Help` 모듈에 대해 업데이트 된 도움말 파일을 찾을 수 없거나 지정 된 언어로 업데이트 된 도움말을 찾을 수 없는 경우 오류 메시지를 표시 하지 않고 자동으로 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93684-280">If `Update-Help` can't find updated help files for a module, or can't find updated help in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="93684-281">세부적인 상태 및 진행 상황을 보려면 **Verbose** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-281">To see status and progress details, use the **Verbose** parameter.</span></span>

<span data-ttu-id="93684-282">`Update-Help`이 cmdlet은 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-282">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="93684-283">이전 버전의 PowerShell에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-283">It doesn't work in earlier versions of PowerShell.</span></span> <span data-ttu-id="93684-284">Windows powershell 2.0 및 Windows PowerShell 3.0이 모두 있는 컴퓨터에서 `Update-Help` Windows powershell 3.0 세션의 cmdlet을 사용 하 여 도움말 파일을 다운로드 하 고 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-284">On computers that have both Windows PowerShell 2.0 and Windows PowerShell 3.0, use the `Update-Help` cmdlet in a Windows PowerShell 3.0 session to download and update help files.</span></span> <span data-ttu-id="93684-285">도움말 파일은 Windows PowerShell 2.0 및 Windows PowerShell 3.0에서 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-285">The help files are available to both Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span>

<span data-ttu-id="93684-286">`Update-Help`및 `Save-Help` cmdlet은 다음 포트를 사용 하 여 도움말 파일을 다운로드 합니다. HTTP의 경우 포트 80, HTTPS의 경우 포트 443</span><span class="sxs-lookup"><span data-stu-id="93684-286">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>

<span data-ttu-id="93684-287">`Update-Help` 모든 모듈과 PowerShell 핵심 스냅인을 지원 합니다. 다른 스냅인은 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-287">`Update-Help` supports all modules and the PowerShell Core snap-ins. It doesn't support any other snap-ins.</span></span>

<span data-ttu-id="93684-288">환경 변수에 나열 되지 않은 위치에 있는 모듈에 대 한 도움말을 업데이트 하려면 `$env:PSModulePath` 모듈을 현재 세션으로 가져온 다음 `Update-Help` 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-288">To update help for a module in a location that isn't listed in the `$env:PSModulePath` environment variable, import the module into the current session and then run an `Update-Help` command.</span></span> <span data-ttu-id="93684-289">`Update-Help`매개 변수 없이 실행 하거나 **module** 매개 변수를 사용 하 여 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93684-289">Run `Update-Help` without parameters or use the **Module** parameter to specify the module name.</span></span> <span data-ttu-id="93684-290">및 cmdlet의 **module** 매개 변수는 `Update-Help` `Save-Help` 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-290">The **Module** parameter of the `Update-Help` and `Save-Help` cmdlets doesn't accept the full path of a module file or module manifest file.</span></span>

<span data-ttu-id="93684-291">모듈은 업데이트할 수 있는 도움말을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-291">Any module can support Updatable Help.</span></span> <span data-ttu-id="93684-292">작성 하는 모듈에서 업데이트할 수 있는 도움말을 지 원하는 방법에 대 한 지침은 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93684-292">For instructions for supporting Updatable Help in the modules that you author, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="93684-293">`Update-Help`및 `Save-Help` cmdlet은 Windows 사전 설치 환경 (Windows PE)에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93684-293">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="93684-294">관련 링크</span><span class="sxs-lookup"><span data-stu-id="93684-294">RELATED LINKS</span></span>

[<span data-ttu-id="93684-295">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="93684-295">Get-Culture</span></span>](../Microsoft.PowerShell.Utility/Get-Culture.md)

[<span data-ttu-id="93684-296">Get-Help</span><span class="sxs-lookup"><span data-stu-id="93684-296">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="93684-297">Get-Module</span><span class="sxs-lookup"><span data-stu-id="93684-297">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="93684-298">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="93684-298">Get-UICulture</span></span>](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[<span data-ttu-id="93684-299">Start-Job</span><span class="sxs-lookup"><span data-stu-id="93684-299">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="93684-300">Save-Help</span><span class="sxs-lookup"><span data-stu-id="93684-300">Save-Help</span></span>](Save-Help.md)
