---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: 4ef0865e81e01746fed77b73e265e68086a7a9e1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "93219121"
---
# <span data-ttu-id="50704-103">Update-Help</span><span class="sxs-lookup"><span data-stu-id="50704-103">Update-Help</span></span>

## <span data-ttu-id="50704-104">개요</span><span class="sxs-lookup"><span data-stu-id="50704-104">SYNOPSIS</span></span>
<span data-ttu-id="50704-105">최신 도움말 파일을 다운로드하여 컴퓨터에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-105">Downloads and installs the newest help files on your computer.</span></span>

## <span data-ttu-id="50704-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="50704-106">SYNTAX</span></span>

### <span data-ttu-id="50704-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="50704-107">Path (Default)</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="50704-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="50704-108">LiteralPath</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="50704-109">설명</span><span class="sxs-lookup"><span data-stu-id="50704-109">DESCRIPTION</span></span>

<span data-ttu-id="50704-110">`Update-Help`Cmdlet은 PowerShell 모듈에 대 한 최신 도움말 파일을 다운로드 하 여 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-110">The `Update-Help` cmdlet downloads the newest help files for PowerShell modules and installs them on your computer.</span></span> <span data-ttu-id="50704-111">변경 내용을 적용 하려면 PowerShell을 다시 시작 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-111">You need not restart PowerShell to make the change effective.</span></span> <span data-ttu-id="50704-112">Cmdlet을 사용 `Get-Help` 하 여 새 도움말 파일을 즉시 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-112">You can use the `Get-Help` cmdlet to view the new help files immediately.</span></span>

<span data-ttu-id="50704-113">`Update-Help` 컴퓨터에 있는 도움말 파일의 버전을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-113">`Update-Help` checks the version of the help files on your computer.</span></span> <span data-ttu-id="50704-114">모듈에 대 한 도움말 파일이 없거나 도움말 파일이 오래 된 경우에서 `Update-Help` 최신 도움말 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-114">If you don't have help files for a module or if your help files are outdated, `Update-Help` downloads the newest help files.</span></span> <span data-ttu-id="50704-115">도움말 파일은 인터넷 또는 파일 공유에서 다운로드 하 여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-115">The help files can be downloaded and installed from the internet or a file share.</span></span>

<span data-ttu-id="50704-116">매개 변수를 사용 하지 않으면는 `Update-Help` 세션 및 업데이트할 수 있는 도움말을 지 원하는 모든 설치 된 모듈에 대 한 도움말 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-116">Without parameters, `Update-Help` updates the help files for modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="50704-117">현재 세션에 설치 되어 있지만 로드 되지 않은 모듈은 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-117">Modules that are installed but not loaded in the current session are included.</span></span> <span data-ttu-id="50704-118">PowerShell 모듈은 환경 변수에 나열 된 위치에 저장 됩니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="50704-118">PowerShell modules are stored in a location listed in the `$env:PSModulePath` environment variable.</span></span> <span data-ttu-id="50704-119">자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50704-119">For more information, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

<span data-ttu-id="50704-120">**Module** 매개 변수를 사용 하 여 특정 모듈에 대 한 도움말 파일을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-120">You can use the **Module** parameter to update help files for a particular module.</span></span> <span data-ttu-id="50704-121">**UICulture** 매개 변수를 사용 하 여 여러 언어 및 로캘로 도움말 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-121">Use the **UICulture** parameter to download help files in multiple languages and locales.</span></span>

<span data-ttu-id="50704-122">인터넷에 연결 되지 않은 컴퓨터 에서도를 사용할 수 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-122">You can also use `Update-Help` on computers that are not connected to the internet.</span></span> <span data-ttu-id="50704-123">먼저, cmdlet을 사용 `Save-Help` 하 여 인터넷에서 도움말 파일을 다운로드 하 고 인터넷에 연결 되지 않은 시스템에서 액세스할 수 있는 공유 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-123">First, use the `Save-Help`cmdlet to download help files from the internet and save them in a shared folder that is accessible to the system not connected to the internet.</span></span> <span data-ttu-id="50704-124">그런 다음의 **SourcePath** 매개 변수를 사용 `Update-Help` 하 여 공유에서 업데이트 된 도움말 파일을 다운로드 하 고 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-124">Then use the **SourcePath** parameter of `Update-Help` to download the updated help files from the shared and install them on the computer.</span></span>

<span data-ttu-id="50704-125">PowerShell 프로필에 cmdlet을 추가 하 여 도움말 업데이트를 자동화할 수 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-125">You can automate help updates by adding the `Update-Help` cmdlet to your PowerShell profile.</span></span> <span data-ttu-id="50704-126">기본적으로는 `Update-Help` 각 컴퓨터에서 하루에 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-126">By default, `Update-Help` runs only one time per day on each computer.</span></span> <span data-ttu-id="50704-127">매일 한 번이라는 제한을 재정의하려면 **Force** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-127">To override the once-per-day limit, use the **Force** parameter.</span></span>

<span data-ttu-id="50704-128">`Update-Help`이 cmdlet은 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-128">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50704-129">`Update-Help` 관리 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-129">`Update-Help` requires administrative privileges.</span></span>
>
> <span data-ttu-id="50704-130">PowerShell 핵심 모듈에 대 한 도움말 파일을 업데이트 하려면 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-130">You must be a member of the Administrators group on the computer to update the help files for the PowerShell Core modules.</span></span>
>
> <span data-ttu-id="50704-131">Powershell Core 모듈을 비롯 하 여 powershell 설치 디렉터리 ()의 모듈에 대 한 도움말 파일을 다운로드 하거나 업데이트 하려면 `$PSHOME\Modules` 관리자 권한으로 실행 옵션을 사용 하 여 powershell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-131">To download or update the help files for modules in the PowerShell installation directory (`$PSHOME\Modules`), including the PowerShell Core modules, start PowerShell by using the Run as administrator option.</span></span>
> <span data-ttu-id="50704-132">예: `Start-Process powershell.exe -Verb RunAs`</span><span class="sxs-lookup"><span data-stu-id="50704-132">For example: `Start-Process powershell.exe -Verb RunAs`.</span></span>
>
> <span data-ttu-id="50704-133">Windows PowerShell ISE (통합 스크립팅 환경)의 도움말 메뉴에서 Windows PowerShell 도움말 업데이트 메뉴 항목을 사용 하 여 도움말 파일을 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-133">You can also update help files by using the Update Windows PowerShell Help menu item in the Help menu in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
>
> <span data-ttu-id="50704-134">업데이트 Windows PowerShell 도움말 항목은 `Update-Help` 매개 변수 없이 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-134">The Update Windows PowerShell Help item runs an `Update-Help` cmdlet without parameters.</span></span>
> <span data-ttu-id="50704-135">디렉터리의 모듈에 대 한 도움말을 업데이트 하려면 `$PSHOME` 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell ISE를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-135">To update help for modules in the `$PSHOME` directory, start Windows PowerShell ISE by using the Run as administrator option.</span></span>

## <span data-ttu-id="50704-136">예제</span><span class="sxs-lookup"><span data-stu-id="50704-136">EXAMPLES</span></span>

### <span data-ttu-id="50704-137">예 1: 모든 모듈에 대 한 도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="50704-137">Example 1: Update help files for all modules</span></span>

<span data-ttu-id="50704-138">`Update-Help`Cmdlet은 업데이트할 수 있는 도움말을 지 원하는 설치 된 모듈에 대 한 도움말 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-138">The `Update-Help` cmdlet updates help files for installed modules that support Updatable Help.</span></span> <span data-ttu-id="50704-139">운영 체제에서 UI (사용자 인터페이스) 문화권 언어를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-139">The user-interface (UI) culture language is set in the operating system.</span></span>

```powershell
Update-Help
```

### <span data-ttu-id="50704-140">예 2: 지정 된 모듈에 대 한 도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="50704-140">Example 2: Update help files for specified modules</span></span>

<span data-ttu-id="50704-141">`Update-Help`이 cmdlet은 **Microsoft PowerShell** 로 시작 하는 모듈 이름에 대해서만 도움말 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-141">The `Update-Help` cmdlet updates help files only for module names that begin with **Microsoft.PowerShell**.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### <span data-ttu-id="50704-142">예 3: 다른 언어에 대 한 도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="50704-142">Example 3: Update help files for different languages</span></span>

<span data-ttu-id="50704-143">이 `Update-Help` cmdlet은 모든 모듈에 대해 일본어 (ja-jp) 및 영어 (en-us) 도움말 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-143">The `Update-Help` cmdlet updates the Japanese (ja-JP) and English (en-US) help files for all modules.</span></span>

<span data-ttu-id="50704-144">모듈에서 지정 된 UI 문화권에 대 한 도움말 파일을 제공 하지 않으면 모듈 및 UI 문화권에 대 한 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-144">If a module doesn't provide help files for a specified UI culture, an error message is displayed for the module and UI culture.</span></span> <span data-ttu-id="50704-145">이 예제에서 오류 메시지는 모듈 **Microsoft. PowerShell** 에 대 한 **ja-jp** 도움말 파일을 찾을 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50704-145">In this example, the error message indicates that the **ja-JP** help files were not found for module **Microsoft.PowerShell.Utility**.</span></span>

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### <span data-ttu-id="50704-146">예제 4: 도움말 파일 자동 업데이트</span><span class="sxs-lookup"><span data-stu-id="50704-146">Example 4: Update help files automatically</span></span>

<span data-ttu-id="50704-147">이 예에서는 매일 오전 3:00에 모든 모듈에 대 한 도움말을 업데이트 하는 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50704-147">This example creates a scheduled job that updates help for all modules every day at 3:00 AM.</span></span>

```powershell
$jobParams = @{
  Name = 'UpdateHelpJob'
  Credential = 'Domain01\User01'
  ScriptBlock = '{Update-Help}'
  Trigger = (New-JobTrigger -Daily -At "3 AM")
}
Register-ScheduledJob @jobParams
```

```Output
Id         Name            JobTriggers     Command                                  Enabled
--         ----            -----------     -------                                  -------
1          UpdateHelpJob   1               Update-Help                              True
```

<span data-ttu-id="50704-148">`Register-ScheduledJob`Cmdlet은 명령을 실행 하는 예약 된 작업을 만듭니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-148">The `Register-ScheduledJob` cmdlet creates a scheduled job that runs an `Update-Help` command.</span></span> <span data-ttu-id="50704-149">이 명령은 **Credential** 매개 변수를 사용 하 여 `Update-Help` 컴퓨터에서 Administrators 그룹의 구성원 자격 증명을 사용 하 여를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-149">The command uses the **Credential** parameter to run `Update-Help` by using the credentials of a member of the Administrators group on the computer.</span></span> <span data-ttu-id="50704-150">**Trigger** 매개 변수 값은 `New-JobTrigger` 매일 오전 3:00에 작업을 시작 하는 작업 트리거를 만드는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="50704-150">The value of the **Trigger** parameter is a `New-JobTrigger` command that creates a job trigger that starts the job every day at 3:00 AM.</span></span>

<span data-ttu-id="50704-151">명령을 실행 하려면 `Register-ScheduledJob` **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-151">To run the `Register-ScheduledJob` command, start PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="50704-152">PowerShell에서 **Credential** 매개 변수에 지정 된 사용자의 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-152">PowerShell prompts you for the password of the user specified in the **Credential** parameter.</span></span> <span data-ttu-id="50704-153">자격 증명은 예약 된 작업과 함께 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-153">The credentials are stored with the scheduled job.</span></span> <span data-ttu-id="50704-154">작업이 실행 될 때 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-154">You aren't prompted when the job runs.</span></span>

<span data-ttu-id="50704-155">Cmdlet을 사용 하 여 예약 된 작업을 확인 하 고 cmdlet을 사용 하 여 변경 하 고 cmdlet을 사용 하 여 `Get-ScheduledJob` 해당 작업을 삭제할 수 있습니다 `Set-ScheduledJob` `Unregister-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="50704-155">You can use the `Get-ScheduledJob` cmdlet to view the scheduled job, use the `Set-ScheduledJob` cmdlet to change it, and use the `Unregister-ScheduledJob` cmdlet to delete it.</span></span> <span data-ttu-id="50704-156">또한 다음 경로에서 작업 Scheduler의 예약된 작업을 보고 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-156">You can also view and manage the scheduled job in Task Scheduler in the following path:</span></span>

<span data-ttu-id="50704-157">`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`.</span><span class="sxs-lookup"><span data-stu-id="50704-157">`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`.</span></span>

### <span data-ttu-id="50704-158">예 5: 파일 공유에서 여러 컴퓨터에 대 한 도움말 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="50704-158">Example 5: Update help files on multiple computers from a file share</span></span>

<span data-ttu-id="50704-159">이 예제에서 업데이트 된 도움말 파일은 인터넷에서 다운로드 되 고 파일 공유에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-159">In this example, updated help files are downloaded from the internet and saved in a file share.</span></span> <span data-ttu-id="50704-160">파일 공유에 액세스 하 고 업데이트를 설치할 수 있는 권한이 있는 사용자 자격 증명이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-160">User credentials are needed that have permissions to access the file share and install updates.</span></span> <span data-ttu-id="50704-161">파일 공유를 사용 하는 경우 방화벽으로 보호 되거나 인터넷에 연결 되지 않은 컴퓨터를 업데이트 하는 것이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-161">When a file share is used, it's possible to update computers that are behind firewalls or aren't connected to the internet.</span></span>

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

<span data-ttu-id="50704-162">`Save-Help`명령은 업데이트할 수 있는 도움말을 지 원하는 모든 모듈에 대 한 최신 도움말 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-162">The `Save-Help` command downloads the newest help files for all modules that support Updatable Help.</span></span>
<span data-ttu-id="50704-163">**DestinationPath** 매개 변수는 파일 공유에 파일을 저장 합니다 `\\Server01\Share\PSHelp` .</span><span class="sxs-lookup"><span data-stu-id="50704-163">The **DestinationPath** parameter saves the files in the `\\Server01\Share\PSHelp` file share.</span></span> <span data-ttu-id="50704-164">**Credential** 매개 변수는 파일 공유에 액세스할 수 있는 권한을 가진 사용자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-164">The **Credential** parameter specifies a user who has permission to access the file share.</span></span>

<span data-ttu-id="50704-165">`Invoke-Command`Cmdlet은 `Update-Help` 여러 컴퓨터에서 원격 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-165">The `Invoke-Command` cmdlet runs remote `Update-Help` commands on multiple computers.</span></span> <span data-ttu-id="50704-166">**ComputerName** 매개 변수는 **Servers.txt** 파일에서 원격 컴퓨터의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="50704-166">The **ComputerName** parameter gets a list of remote computers from the **Servers.txt** file.</span></span> <span data-ttu-id="50704-167">**ScriptBlock** 매개 변수는 `Update-Help` 명령을 실행 하 고 **SourcePath** 매개 변수를 사용 하 여 업데이트 된 도움말 파일을 포함 하는 파일 공유를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-167">The **ScriptBlock** parameter runs the `Update-Help` command and uses the **SourcePath** parameter to specify the file share that contains the updated help files.</span></span> <span data-ttu-id="50704-168">**Credential** 매개 변수는 파일 공유에 액세스 하 고 원격 명령을 실행할 수 있는 사용자를 지정 합니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-168">The **Credential** parameter specifies a user who can access the file share and run the remote `Update-Help` command.</span></span>

### <span data-ttu-id="50704-169">예제 6: 업데이트 된 도움말 파일 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="50704-169">Example 6: Get a list of updated help files</span></span>

<span data-ttu-id="50704-170">`Update-Help`Cmdlet은 지정 된 모듈에 대 한 도움말을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-170">The `Update-Help` cmdlet updates help for a specified module.</span></span> <span data-ttu-id="50704-171">이 cmdlet은 **Verbose** 일반 매개 변수를 사용 하 여 업데이트 된 도움말 파일의 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-171">The cmdlet uses the **Verbose** common parameter to display the list of help files that were updated.</span></span> <span data-ttu-id="50704-172">**자세한 정보** 표시를 사용 하 여 특정 모듈에 대 한 모든 도움말 파일 또는 도움말 파일의 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-172">You can use **Verbose** to view output for all help files or help files for a specific module.</span></span>

<span data-ttu-id="50704-173">**Verbose** 매개 변수를 사용 하지 않으면 `Update-Help` 명령 결과를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-173">Without the **Verbose** parameter, `Update-Help` doesn't display the results of the command.</span></span> <span data-ttu-id="50704-174">**Verbose** 매개 변수 출력은 도움말 파일이 업데이트 되었는지 또는 최신 버전이 설치 되어 있는지 확인 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-174">The **Verbose** parameter output is useful to verify that the help files were updated or if the latest version is installed.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### <span data-ttu-id="50704-175">예 7: 업데이트할 수 있는 도움말을 지 원하는 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="50704-175">Example 7: Find modules that support Updatable Help</span></span>

<span data-ttu-id="50704-176">이 예제에서는 업데이트할 수 있는 도움말을 지 원하는 모듈을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-176">This example lists modules that support Updatable Help.</span></span> <span data-ttu-id="50704-177">이 명령은 모듈의 **HelpInfoUri** 속성을 사용 하 여 업데이트할 수 있는 도움말을 지 원하는 모듈을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-177">The command uses the module's **HelpInfoUri** property to identify modules that support Updatable Help.</span></span> <span data-ttu-id="50704-178">**HelpInfoUri** 속성에는 cmdlet이 실행 될 때 리디렉션되는 주소가 포함 되어 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-178">The **HelpInfoUri** property contains an address that is redirected when the `Update-Help` cmdlet is run.</span></span>

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

### <span data-ttu-id="50704-179">예 8: 업데이트 된 도움말 파일 인벤토리</span><span class="sxs-lookup"><span data-stu-id="50704-179">Example 8: Inventory updated help files</span></span>

<span data-ttu-id="50704-180">이 예제에서 스크립트는 `Get-UpdateHelpVersion.ps1` 각 모듈 및 해당 버전 번호에 대해 업데이트할 수 있는 도움말 파일의 인벤토리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50704-180">In this example, the script `Get-UpdateHelpVersion.ps1` creates an inventory of the Updatable Help files for each module and their version numbers.</span></span>

<span data-ttu-id="50704-181">스크립트는 모듈의 **HelpInfoUri** 속성을 사용 하 여 업데이트할 수 있는 도움말을 지 원하는 모듈을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-181">The script identifies modules that support Updatable Help by using the **HelpInfoUri** property of modules.</span></span> <span data-ttu-id="50704-182">업데이트할 수 있는 도움말을 지 원하는 모듈의 경우 스크립트는 도움말 정보 파일 (\* helpinfo.xml)을 찾고 구문 분석 하 여 최신 버전 번호를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-182">For modules that support Updatable Help, the script looks for and parses the help information file (\*helpinfo.xml) to find the latest version number.</span></span>

<span data-ttu-id="50704-183">이 스크립트는 **PSCustomObject** 클래스 및 해시 테이블을 사용 하 여 사용자 지정 출력 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50704-183">The script uses the **PSCustomObject** class and a hash table to create a custom output object.</span></span>

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

## <span data-ttu-id="50704-184">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="50704-184">PARAMETERS</span></span>

### <span data-ttu-id="50704-185">-Credential</span><span class="sxs-lookup"><span data-stu-id="50704-185">-Credential</span></span>

<span data-ttu-id="50704-186">**SourcePath** 로 지정 된 파일 시스템 위치에 액세스할 수 있는 권한이 있는 사용자의 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-186">Specifies credentials of a user who has permission to access the file system location specified by **SourcePath**.</span></span> <span data-ttu-id="50704-187">이 매개 변수는 **SourcePath** 또는 **LiteralPath** 매개 변수가 명령에 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-187">This parameter is valid only when the **SourcePath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="50704-188">**Credential** 매개 변수를 사용 하면 `Update-Help` 원격 컴퓨터에서 **SourcePath** 매개 변수를 사용 하 여 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-188">The **Credential** parameter enables you to run `Update-Help` commands with the **SourcePath** parameter on remote computers.</span></span> <span data-ttu-id="50704-189">명시적 자격 증명을 제공 하 여 원격 컴퓨터에서 명령을 실행 하 고 액세스 거부 오류가 발생 하거나 CredSSP 인증을 사용 하 여 자격 증명을 위임 하지 않고도 세 번째 컴퓨터의 파일 공유에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-189">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="50704-190">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="50704-190">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="50704-191">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-191">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="50704-192">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-192">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="50704-193">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="50704-193">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="50704-194">-Force</span><span class="sxs-lookup"><span data-stu-id="50704-194">-Force</span></span>

<span data-ttu-id="50704-195">이 cmdlet은 하루에 한 번만 수행 하 고, 버전 검사를 건너뛰고, 1gb 제한을 초과 하는 파일을 다운로드 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50704-195">Indicates that this cmdlet doesn't follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="50704-196">이 매개 변수를 사용 하지 않으면은 `Update-Help` 24 시간 마다 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-196">Without this parameter, `Update-Help` runs only once in each 24-hour period.</span></span> <span data-ttu-id="50704-197">다운로드는 모듈 별로 압축 되지 않은 1gb로 제한 되며, 도움말 파일은 컴퓨터의 기존 파일 보다 최신 버전인 경우에만 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-197">Downloads are limited to 1 GB of uncompressed content per module and help files are only installed when they're newer than the existing files on the computer.</span></span>

<span data-ttu-id="50704-198">매일 한 번 제한은 도움말 파일을 호스트 하는 서버를 보호 하 고, 반복 되는 `Update-Help` 연결 또는 다운로드의 리소스 비용을 들이지 않고 PowerShell 프로필에 명령을 추가 하는 것이 실용적입니다.</span><span class="sxs-lookup"><span data-stu-id="50704-198">The once-per-day limit protects the servers that host the help files and makes it practical for you to add an `Update-Help` command to your PowerShell profile without incurring the resource cost of repeated connections or downloads.</span></span>

<span data-ttu-id="50704-199">**Force** 매개 변수 없이 여러 UI 문화권의 모듈에 대한 도움말을 업데이트하려면 동일한 명령에 모든 UI 문화권을 포함합니다. 예:</span><span class="sxs-lookup"><span data-stu-id="50704-199">To update help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as:</span></span>

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

### <span data-ttu-id="50704-200">-변수인 fullyqualifiedmodule</span><span class="sxs-lookup"><span data-stu-id="50704-200">-FullyQualifiedModule</span></span>

<span data-ttu-id="50704-201">**ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-201">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="50704-202">이러한 모듈은 [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 설명 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-202">These modules are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="50704-203">예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식으로 지정 된 모듈 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-203">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

<span data-ttu-id="50704-204">또는</span><span class="sxs-lookup"><span data-stu-id="50704-204">or</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

<span data-ttu-id="50704-205">**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="50704-205">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="50704-206">**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-206">You can't specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span>

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

### <span data-ttu-id="50704-207">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="50704-207">-LiteralPath</span></span>

<span data-ttu-id="50704-208">인터넷에서 다운로드 하는 대신 업데이트 된 도움말 파일에 대 한 폴더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-208">Specifies the folder for updated help files instead of downloading them from the internet.</span></span> <span data-ttu-id="50704-209">Cmdlet을 사용 하 **SourcePath** 여 `Save-Help` 디렉터리에 도움말 파일을 다운로드 한 경우이 매개 변수 또는 SourcePath를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-209">Use this parameter or **SourcePath** if you've used the `Save-Help` cmdlet to download help files to a directory.</span></span>

<span data-ttu-id="50704-210">또는 cmdlet과 같은 디렉터리 개체를로 파이프라인을 만들 수 있습니다 `Get-Item` `Get-ChildItem` `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-210">You can pipeline a directory object, such as from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="50704-211">**SourcePath** 의 값과 달리 **LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-211">Unlike the value of **SourcePath** , the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="50704-212">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-212">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="50704-213">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="50704-213">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="50704-214">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-214">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="50704-215">-모듈</span><span class="sxs-lookup"><span data-stu-id="50704-215">-Module</span></span>

<span data-ttu-id="50704-216">지정된 모듈에 대한 도움말을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-216">Updates help for the specified modules.</span></span> <span data-ttu-id="50704-217">쉼표로 구분 된 목록에 하나 이상의 모듈 이름 또는 이름 패턴을 입력 하거나 각 줄에 하나의 모듈 이름을 나열 하는 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-217">Enter one or more module names or name patterns in a comma-separated list, or specify a file that lists one module name on each line.</span></span> <span data-ttu-id="50704-218">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-218">Wildcard characters are permitted.</span></span> <span data-ttu-id="50704-219">Cmdlet에서 cmdlet으로 모듈 파이프라인을 만들 수 있습니다 `Get-Module` `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-219">You can pipeline modules from the `Get-Module` cmdlet to the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="50704-220">지정 하는 모듈은 컴퓨터에 설치 해야 하지만 현재 세션으로 가져올 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-220">The modules that you specify must be installed on the computer, but they don't have to be imported into the current session.</span></span> <span data-ttu-id="50704-221">환경 변수에 나열 된 위치에 설치 된 모듈 또는 세션의 모든 모듈을 지정할 수 있습니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="50704-221">You can specify any module in the session or any module that is installed in a location listed in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="50704-222">값 `*` (모두)은 컴퓨터에 설치 되어 있는 모든 모듈에 대 한 도움말을 업데이트 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-222">A value of `*` (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="50704-223">업데이트할 수 있는 도움말을 지원 하지 않는 모듈은 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-223">Modules that don't support Updatable Help are included.</span></span> <span data-ttu-id="50704-224">이 값은 명령이 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 발견 하면 오류를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-224">This value might generate errors when the command encounters modules that don't support Updatable Help.</span></span> <span data-ttu-id="50704-225">대신 `Update-Help` 매개 변수 없이 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-225">Instead, run `Update-Help` without parameters.</span></span>

<span data-ttu-id="50704-226">Cmdlet의 **module** 매개 변수는 `Update-Help` 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-226">The **Module** parameter of the `Update-Help` cmdlet doesn't accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="50704-227">위치에 없는 모듈에 대 한 도움말을 업데이트 하려면 `$env:PSModulePath` 명령을 실행 하기 전에 모듈을 현재 세션으로 가져옵니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-227">To update help for a module that isn't in a `$env:PSModulePath` location, import the module into the current session before you run the `Update-Help` command.</span></span>

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

### <span data-ttu-id="50704-228">-재귀</span><span class="sxs-lookup"><span data-stu-id="50704-228">-Recurse</span></span>

<span data-ttu-id="50704-229">지정 된 디렉터리에 있는 도움말 파일에 대 한 재귀 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-229">Performs a recursive search for help files in the specified directory.</span></span> <span data-ttu-id="50704-230">이 매개 변수는 명령에서 **SourcePath** 매개 변수를 사용 하는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-230">This parameter is valid only when the command uses the **SourcePath** parameter.</span></span>

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

### <span data-ttu-id="50704-231">-SourcePath</span><span class="sxs-lookup"><span data-stu-id="50704-231">-SourcePath</span></span>

<span data-ttu-id="50704-232">가 `Update-Help` 인터넷에서 다운로드 하는 대신 업데이트 된 도움말 파일을 가져오는 파일 시스템 폴더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-232">Specifies a file system folder where `Update-Help` gets updated help files, instead of downloading them from the internet.</span></span> <span data-ttu-id="50704-233">폴더의 경로를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-233">Enter the path of a folder.</span></span> <span data-ttu-id="50704-234">파일 이름 또는 파일 이름 확장명을 지정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="50704-234">Don't specify a file name or file name extension.</span></span> <span data-ttu-id="50704-235">또는 cmdlet의 폴더와 같은 폴더를로 파이프라인을 만들 수 있습니다 `Get-Item` `Get-ChildItem` `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-235">You can pipeline a folder, such as one from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="50704-236">기본적으로는 `Update-Help` 업데이트 된 도움말 파일을 인터넷에서 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-236">By default, `Update-Help` downloads updated help files from the internet.</span></span> <span data-ttu-id="50704-237">Cmdlet **SourcePath** 을 사용 `Save-Help` 하 여 업데이트 된 도움말 파일을 디렉터리에 다운로드 한 경우 SourcePath를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-237">Use **SourcePath** when you've used the `Save-Help` cmdlet to download updated help files to a directory.</span></span>

<span data-ttu-id="50704-238">**SourcePath** 의 기본값을 지정 하려면 **그룹 정책** , **컴퓨터 구성** 으로 이동 하 여 **update-help에 대 한 기본 원본 경로를 설정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-238">To specify a default value for **SourcePath** , go to **Group Policy** , **Computer Configuration** , and **Set the default source path for Update-Help**.</span></span> <span data-ttu-id="50704-239">이 그룹 정책 설정은 사용자가를 사용 하 여 `Update-Help` 인터넷에서 도움말 파일을 다운로드 하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-239">This Group Policy setting prevents users from using `Update-Help` to download help files from the internet.</span></span>
<span data-ttu-id="50704-240">자세한 내용은 [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50704-240">For more information, see [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="50704-241">-UICulture</span><span class="sxs-lookup"><span data-stu-id="50704-241">-UICulture</span></span>

<span data-ttu-id="50704-242">`Update-Help`에서 업데이트 된 도움말 파일을 가져오는 데 사용 하는 UI 문화권 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-242">Specifies UI culture values that `Update-Help` uses to get updated help files.</span></span> <span data-ttu-id="50704-243">하나 이상의 언어 코드 (예: **es)** , culture 개체를 포함 하는 변수 또는 문화권 개체를 가져오는 명령 (예: 또는 명령)을 입력 `Get-Culture` `Get-UICulture` 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-243">Enter one or more language codes, such as **es-ES** , a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span> <span data-ttu-id="50704-244">와일드 카드 문자를 사용할 수 없으며 **de** 와 같은 부분 언어 코드를 제출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-244">Wildcard characters aren't permitted and you can't submit a partial language code, such as **de**.</span></span>

<span data-ttu-id="50704-245">기본적으로는 `Update-Help` 운영 체제에 대해 설정 된 UI 문화권의 도움말 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="50704-245">By default, `Update-Help` gets help files in the UI culture set for the operating system.</span></span> <span data-ttu-id="50704-246">**UICulture** 매개 변수를 지정 하는 경우는 `Update-Help` 지정 된 UI 문화권에 대 한 도움말만 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-246">If you specify the **UICulture** parameter, `Update-Help` looks for help only for the specified UI culture.</span></span>

<span data-ttu-id="50704-247">**UICulture** 매개 변수를 사용하는 명령은 모듈이 지정된 UI 문화권에 대한 도움말 파일을 제공하는 경우에 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-247">Commands that use the **UICulture** parameter succeed only when the module provides help files for the specified UI culture.</span></span> <span data-ttu-id="50704-248">지정 된 UI 문화권이 지원 되지 않기 때문에 명령이 실패 하면 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-248">If the command fails because the specified UI culture isn't supported, an error message is displayed.</span></span>

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

### <span data-ttu-id="50704-249">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="50704-249">-UseDefaultCredentials</span></span>

<span data-ttu-id="50704-250">에서 `Update-Help` 현재 사용자의 자격 증명을 사용 하 여 인터넷 다운로드를 포함 하 여 명령을 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50704-250">Indicates that `Update-Help` runs the command, including the internet download, by using the credentials of the current user.</span></span> <span data-ttu-id="50704-251">기본적으로 명령은 명시적 자격 증명 없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-251">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="50704-252">이 매개 변수는 웹 다운로드에서 NTLM (NT LAN Manager), 협상 또는 Kerberos 기반 인증을 사용 하는 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-252">This parameter is effective only when the web download uses NT LAN Manager (NTLM), negotiate, or Kerberos-based authentication.</span></span>

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

### <span data-ttu-id="50704-253">-Confirm</span><span class="sxs-lookup"><span data-stu-id="50704-253">-Confirm</span></span>

<span data-ttu-id="50704-254">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-254">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="50704-255">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="50704-255">-WhatIf</span></span>

<span data-ttu-id="50704-256">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-256">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="50704-257">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-257">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="50704-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="50704-258">CommonParameters</span></span>

<span data-ttu-id="50704-259">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="50704-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="50704-260">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50704-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="50704-261">입력</span><span class="sxs-lookup"><span data-stu-id="50704-261">INPUTS</span></span>

### <span data-ttu-id="50704-262">System.io.directoryinfo</span><span class="sxs-lookup"><span data-stu-id="50704-262">System.IO.DirectoryInfo</span></span>

<span data-ttu-id="50704-263">디렉터리 경로를로 파이프 할 수 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-263">You can pipe a directory path to `Update-Help`.</span></span>

### <span data-ttu-id="50704-264">System.object..</span><span class="sxs-lookup"><span data-stu-id="50704-264">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="50704-265">Cmdlet에서로 모듈 개체를 파이프 할 수 있습니다 `Get-Module` `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="50704-265">You can pipe a module object from the `Get-Module` cmdlet to `Update-Help`.</span></span>

## <span data-ttu-id="50704-266">출력</span><span class="sxs-lookup"><span data-stu-id="50704-266">OUTPUTS</span></span>

### <span data-ttu-id="50704-267">없음</span><span class="sxs-lookup"><span data-stu-id="50704-267">None</span></span>

<span data-ttu-id="50704-268">`Update-Help` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-268">`Update-Help` doesn't generate any output.</span></span>

## <span data-ttu-id="50704-269">참고</span><span class="sxs-lookup"><span data-stu-id="50704-269">NOTES</span></span>

<span data-ttu-id="50704-270">Powershell과 함께 설치 되는 명령 또는 디렉터리의 모듈을 포함 하는 PowerShell 핵심 모듈에 대 한 도움말을 업데이트 하려면 `$PSHOME\Modules` **관리자 권한으로 실행** 하는 옵션을 사용 하 여 powershell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-270">To update help for the PowerShell Core modules, that contain the commands that are installed with PowerShell, or any module in the `$PSHOME\Modules` directory, start PowerShell with the option to **Run as administrator**.</span></span>

<span data-ttu-id="50704-271">컴퓨터의 Administrators 그룹 구성원만 PowerShell 핵심 모듈에 대 한 도움말, PowerShell과 함께 설치 되는 명령, 폴더의 모듈에 대 한 도움말을 업데이트할 수 있습니다 `$PSHOME\Modules` .</span><span class="sxs-lookup"><span data-stu-id="50704-271">Only members of the Administrators group on the computer can update help for the PowerShell Core modules, the commands that are installed together with PowerShell, and for modules in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="50704-272">도움말 파일을 업데이트할 수 있는 권한이 없는 경우 온라인으로 도움말 파일을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-272">If you don't have permission to update help files, you can read the help files online.</span></span> <span data-ttu-id="50704-273">예들 들어 `Get-Help Update-Help -Online`입니다.</span><span class="sxs-lookup"><span data-stu-id="50704-273">For example, `Get-Help Update-Help -Online`.</span></span>

<span data-ttu-id="50704-274">모듈은 업데이트할 수 있는 도움말의 가장 작은 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="50704-274">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="50704-275">특정 cmdlet에 대 한 도움말을 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-275">You can't update help for a particular cmdlet.</span></span> <span data-ttu-id="50704-276">특정 cmdlet이 포함 된 모듈을 찾으려면 cmdlet의 **ModuleName** 속성 (예:)을 사용 `Get-Command` `(Get-Command Update-Help).ModuleName` 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-276">To find the module that contains a particular cmdlet, use the **ModuleName** property of the `Get-Command` cmdlet, for example, `(Get-Command Update-Help).ModuleName`.</span></span>

<span data-ttu-id="50704-277">도움말 파일이 모듈 디렉터리에 설치 되어 있기 때문에 `Update-Help` cmdlet은 컴퓨터에 설치 된 모듈에 대해서만 업데이트 된 도움말 파일을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-277">Because help files are installed in the module directory, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span> <span data-ttu-id="50704-278">그러나 cmdlet은 `Save-Help` 컴퓨터에 설치 되지 않은 모듈에 대 한 도움말을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-278">However, the `Save-Help` cmdlet can save help for modules that aren't installed on the computer.</span></span>

<span data-ttu-id="50704-279">에서 `Update-Help` 모듈에 대해 업데이트 된 도움말 파일을 찾을 수 없거나 지정 된 언어로 업데이트 된 도움말을 찾을 수 없는 경우 오류 메시지를 표시 하지 않고 자동으로 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50704-279">If `Update-Help` can't find updated help files for a module, or can't find updated help in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="50704-280">세부적인 상태 및 진행 상황을 보려면 **Verbose** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-280">To see status and progress details, use the **Verbose** parameter.</span></span>

<span data-ttu-id="50704-281">`Update-Help`이 cmdlet은 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-281">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="50704-282">이전 버전의 PowerShell에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-282">It doesn't work in earlier versions of PowerShell.</span></span> <span data-ttu-id="50704-283">Windows powershell 2.0 및 Windows PowerShell 3.0이 모두 있는 컴퓨터에서 `Update-Help` Windows powershell 3.0 세션의 cmdlet을 사용 하 여 도움말 파일을 다운로드 하 고 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-283">On computers that have both Windows PowerShell 2.0 and Windows PowerShell 3.0, use the `Update-Help` cmdlet in a Windows PowerShell 3.0 session to download and update help files.</span></span> <span data-ttu-id="50704-284">도움말 파일은 Windows PowerShell 2.0 및 Windows PowerShell 3.0에서 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-284">The help files are available to both Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span>

<span data-ttu-id="50704-285">`Update-Help`및 `Save-Help` cmdlet은 다음 포트를 사용 하 여 도움말 파일을 다운로드 합니다. HTTP의 경우 포트 80, HTTPS의 경우 포트 443</span><span class="sxs-lookup"><span data-stu-id="50704-285">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>

<span data-ttu-id="50704-286">`Update-Help` 모든 모듈과 PowerShell 핵심 스냅인을 지원 합니다. 다른 스냅인은 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-286">`Update-Help` supports all modules and the PowerShell Core snap-ins. It doesn't support any other snap-ins.</span></span>

<span data-ttu-id="50704-287">환경 변수에 나열 되지 않은 위치에 있는 모듈에 대 한 도움말을 업데이트 하려면 `$env:PSModulePath` 모듈을 현재 세션으로 가져온 다음 `Update-Help` 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-287">To update help for a module in a location that isn't listed in the `$env:PSModulePath` environment variable, import the module into the current session and then run an `Update-Help` command.</span></span> <span data-ttu-id="50704-288">`Update-Help`매개 변수 없이 실행 하거나 **module** 매개 변수를 사용 하 여 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50704-288">Run `Update-Help` without parameters or use the **Module** parameter to specify the module name.</span></span> <span data-ttu-id="50704-289">및 cmdlet의 **module** 매개 변수는 `Update-Help` `Save-Help` 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-289">The **Module** parameter of the `Update-Help` and `Save-Help` cmdlets doesn't accept the full path of a module file or module manifest file.</span></span>

<span data-ttu-id="50704-290">모듈은 업데이트할 수 있는 도움말을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-290">Any module can support Updatable Help.</span></span> <span data-ttu-id="50704-291">작성 하는 모듈에서 업데이트할 수 있는 도움말을 지 원하는 방법에 대 한 지침은 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="50704-291">For instructions for supporting Updatable Help in the modules that you author, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="50704-292">`Update-Help`및 `Save-Help` cmdlet은 Windows 사전 설치 환경 (Windows PE)에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50704-292">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="50704-293">관련 링크</span><span class="sxs-lookup"><span data-stu-id="50704-293">RELATED LINKS</span></span>

[<span data-ttu-id="50704-294">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="50704-294">Get-Culture</span></span>](../Microsoft.PowerShell.Utility/Get-Culture.md)

[<span data-ttu-id="50704-295">Get-Help</span><span class="sxs-lookup"><span data-stu-id="50704-295">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="50704-296">Get-Module</span><span class="sxs-lookup"><span data-stu-id="50704-296">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="50704-297">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="50704-297">Get-UICulture</span></span>](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[<span data-ttu-id="50704-298">Start-Job</span><span class="sxs-lookup"><span data-stu-id="50704-298">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="50704-299">Save-Help</span><span class="sxs-lookup"><span data-stu-id="50704-299">Save-Help</span></span>](Save-Help.md)
