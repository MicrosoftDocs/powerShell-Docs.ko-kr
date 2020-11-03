---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: 1cd86a1c9abe6c8a4af9f68ed17ea1876ff1bd20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215761"
---
# <span data-ttu-id="a0867-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="a0867-103">Find-Command</span></span>

## <span data-ttu-id="a0867-104">개요</span><span class="sxs-lookup"><span data-stu-id="a0867-104">SYNOPSIS</span></span>
<span data-ttu-id="a0867-105">모듈에서 PowerShell 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-105">Finds PowerShell commands in modules.</span></span>

## <span data-ttu-id="a0867-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0867-106">SYNTAX</span></span>

### <span data-ttu-id="a0867-107">모두</span><span class="sxs-lookup"><span data-stu-id="a0867-107">All</span></span>

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a0867-108">설명</span><span class="sxs-lookup"><span data-stu-id="a0867-108">DESCRIPTION</span></span>

<span data-ttu-id="a0867-109">`Find-Command`Cmdlet은 cmdlet, 별칭, 함수, 워크플로 등의 PowerShell 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-109">The `Find-Command` cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="a0867-110">`Find-Command` 등록 된 리포지토리의 모듈을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-110">`Find-Command` searches modules in registered repositories.</span></span>

<span data-ttu-id="a0867-111">에서 찾은 각 명령에 대해 `Find-Command` **Psgetcommandinfo** 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-111">For each command found by `Find-Command`, a **PSGetCommandInfo** object is returned.</span></span> <span data-ttu-id="a0867-112">**Psgetcommandinfo** 개체를 파이프라인에서 cmdlet으로 보낼 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="a0867-112">The **PSGetCommandInfo** object can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="a0867-113">`Install-Module` 명령이 포함 된 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-113">`Install-Module` installs the module that contains the command.</span></span>

## <span data-ttu-id="a0867-114">예제</span><span class="sxs-lookup"><span data-stu-id="a0867-114">EXAMPLES</span></span>

### <span data-ttu-id="a0867-115">예 1: 지정 된 리포지토리에서 모든 명령 찾기</span><span class="sxs-lookup"><span data-stu-id="a0867-115">Example 1: Find all commands in a specified repository</span></span>

<span data-ttu-id="a0867-116">`Find-Command`Cmdlet은 모듈에 대해 등록 된 리포지토리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-116">The `Find-Command` cmdlet searches a registered repository for modules.</span></span>

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

<span data-ttu-id="a0867-117">`Find-Command`**리포지토리** 매개 변수를 사용 하 여 등록 된 리포지토리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-117">`Find-Command` uses the **Repository** parameter to specify a registered repository's name.</span></span> <span data-ttu-id="a0867-118">개체는 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-118">The objects are sent down the pipeline.</span></span> <span data-ttu-id="a0867-119">`Select-Object` 개체를 수신 하 고 **첫** 번째 매개 변수를 사용 하 여 처음 10 개의 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-119">`Select-Object` receives the objects and uses the **First** parameter to display the first 10 results.</span></span>

### <span data-ttu-id="a0867-120">예 2: 이름별로 명령 찾기</span><span class="sxs-lookup"><span data-stu-id="a0867-120">Example 2: Find a command by name</span></span>

<span data-ttu-id="a0867-121">`Find-Command` 는 명령 이름을 사용 하 여 리포지토리에서 모듈을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-121">`Find-Command` can use the name of a command to locate the module in a repository.</span></span> <span data-ttu-id="a0867-122">명령 이름이 여러 **ModuleNames** 에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-122">It's possible that a command name exists in multiple **ModuleNames** .</span></span>

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

<span data-ttu-id="a0867-123">`Find-Command`**리포지토리** 매개 변수를 사용 하 여 **PSGallery** 를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-123">`Find-Command` uses the **Repository** parameter to search the **PSGallery** .</span></span> <span data-ttu-id="a0867-124">**Name** 매개 변수는 **test-targetresource** 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-124">The **Name** parameter specifies the command **Get-TargetResource** .</span></span>

### <span data-ttu-id="a0867-125">예제 3: 이름을 기준으로 명령 찾기 및 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="a0867-125">Example 3: Find commands by name and install the module</span></span>

<span data-ttu-id="a0867-126">`Find-Command` 는 명령 및 모듈을 찾은 다음 개체를로 보낼 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="a0867-126">`Find-Command` can locate the command and module, then send the object to `Install-Module`.</span></span> <span data-ttu-id="a0867-127">명령이 여러 모듈에 포함 된 경우 `Find-Command` Cmdlet **모듈-Name** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-127">If a command is included in multiple modules, use the `Find-Command` cmdlets **Module-Name** parameter.</span></span>
<span data-ttu-id="a0867-128">그렇지 않으면 설치 하지 않으려는 모듈이 설치 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-128">Otherwise, modules might be installed that you didn't want to install.</span></span>

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

<span data-ttu-id="a0867-129">`Find-Command`**Name** 매개 변수를 사용 하 여 **test-targetresource** 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-129">`Find-Command` uses the **Name** parameter to specify the command **Get-TargetResource** .</span></span> <span data-ttu-id="a0867-130">**리포지토리** 매개 변수는 **PSGallery** 를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-130">The **Repository** parameter searches the **PSGallery** .</span></span> <span data-ttu-id="a0867-131">**ModuleName** 매개 변수는 설치 하려는 모듈을 **Systemlocaledsc** 로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-131">The **ModuleName** parameter specifies the module you want to install, **SystemLocaleDsc** .</span></span> <span data-ttu-id="a0867-132">개체가 파이프라인으로 전송 되 `Install-Module` 고 모듈이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-132">The object is sent down the pipeline to `Install-Module` and the module is installed.</span></span> <span data-ttu-id="a0867-133">설치가 완료 되 면를 사용 하 여 `Get-InstalledModule` 결과를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-133">After the installation finishes, you can use `Get-InstalledModule` to display the results.</span></span>

### <span data-ttu-id="a0867-134">예제 4: 명령 찾기 및 해당 모듈 저장</span><span class="sxs-lookup"><span data-stu-id="a0867-134">Example 4: Find a command and save its module</span></span>

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

<span data-ttu-id="a0867-135">`Find-Command`**Name** 및 **리포지토리** 매개 변수를 사용 하 여 **PSGallery** 리포지토리에서 명령 **호출** 을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-135">`Find-Command` uses the **Name** and **Repository** parameters to search for the command **Invoke-ScriptAnalyzer** in the **PSGallery** repository.</span></span> <span data-ttu-id="a0867-136">개체는 파이프라인에서로 전송 됩니다 `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="a0867-136">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="a0867-137">**Path** 매개 변수는 모듈을 저장할 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-137">The **Path** parameter determines the location to save the module.</span></span> <span data-ttu-id="a0867-138">**Verbose** 는 선택적 매개 변수 이지만 PowerShell 콘솔에 상태 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-138">**Verbose** is an optional parameter, but displays status output in the PowerShell console.</span></span> <span data-ttu-id="a0867-139">자세한 정보 출력은 문제 해결에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-139">The verbose output is beneficial for troubleshooting.</span></span>

## <span data-ttu-id="a0867-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a0867-140">PARAMETERS</span></span>

### <span data-ttu-id="a0867-141">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="a0867-141">-AllowPrerelease</span></span>

<span data-ttu-id="a0867-142">결과에서 시험판으로 표시 된 모듈을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-142">Includes modules marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="a0867-143">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="a0867-143">-AllVersions</span></span>

<span data-ttu-id="a0867-144">이 cmdlet은 모듈의 모든 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-144">Indicates that this cmdlet gets all versions of a module.</span></span>

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

### <span data-ttu-id="a0867-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="a0867-145">-Filter</span></span>

<span data-ttu-id="a0867-146">**PackageManagement** 공급자의 검색 구문에 따라 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-146">Finds modules based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="a0867-147">예를 들어 **ModuleName** 및 **Description** 속성 내에서 검색할 단어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-147">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a0867-148">-MaximumVersion</span></span>

<span data-ttu-id="a0867-149">결과에 포함할 모듈의 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-149">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="a0867-150">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-150">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a0867-151">-MinimumVersion</span></span>

<span data-ttu-id="a0867-152">결과에 포함할 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-152">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="a0867-153">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-153">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-154">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="a0867-154">-ModuleName</span></span>

<span data-ttu-id="a0867-155">명령을 검색할 모듈의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-155">Specifies the name of a module to search for commands.</span></span> <span data-ttu-id="a0867-156">기본값은 모든 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-156">The default is all modules.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-157">-Name</span><span class="sxs-lookup"><span data-stu-id="a0867-157">-Name</span></span>

<span data-ttu-id="a0867-158">리포지토리에서 검색할 명령 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-158">Specifies the command name to search for in a repository.</span></span> <span data-ttu-id="a0867-159">명령 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-159">Use commas to separate an array of command names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-160">-프록시</span><span class="sxs-lookup"><span data-stu-id="a0867-160">-Proxy</span></span>

<span data-ttu-id="a0867-161">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-161">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a0867-162">-ProxyCredential</span></span>

<span data-ttu-id="a0867-163">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-163">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-164">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="a0867-164">-Repository</span></span>

<span data-ttu-id="a0867-165">명령을 검색할 리포지토리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-165">Specifies the repository to search for commands.</span></span> <span data-ttu-id="a0867-166">저장소 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-166">Use commas to separate an array of repository names.</span></span> <span data-ttu-id="a0867-167">기본값은 모든 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-167">The default is all repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-168">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a0867-168">-RequiredVersion</span></span>

<span data-ttu-id="a0867-169">결과에 포함할 모듈의 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-169">Specifies the version of the module to include in the results.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-170">-Tag</span><span class="sxs-lookup"><span data-stu-id="a0867-170">-Tag</span></span>

<span data-ttu-id="a0867-171">리포지토리의 모듈을 범주화 하는 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-171">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="a0867-172">태그 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-172">Use commas to separate an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0867-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0867-173">CommonParameters</span></span>

<span data-ttu-id="a0867-174">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0867-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0867-175">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0867-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0867-176">입력</span><span class="sxs-lookup"><span data-stu-id="a0867-176">INPUTS</span></span>

## <span data-ttu-id="a0867-177">출력</span><span class="sxs-lookup"><span data-stu-id="a0867-177">OUTPUTS</span></span>

### <span data-ttu-id="a0867-178">PSGetCommandInfo</span><span class="sxs-lookup"><span data-stu-id="a0867-178">PSGetCommandInfo</span></span>

<span data-ttu-id="a0867-179">`Find-Command`**Psgetcommandinfo** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0867-179">`Find-Command` outputs a **PSGetCommandInfo** object.</span></span>

## <span data-ttu-id="a0867-180">참고</span><span class="sxs-lookup"><span data-stu-id="a0867-180">NOTES</span></span>

## <span data-ttu-id="a0867-181">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a0867-181">RELATED LINKS</span></span>

[<span data-ttu-id="a0867-182">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a0867-182">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="a0867-183">Install-Module</span><span class="sxs-lookup"><span data-stu-id="a0867-183">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="a0867-184">Save-Module</span><span class="sxs-lookup"><span data-stu-id="a0867-184">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="a0867-185">Select-Object</span><span class="sxs-lookup"><span data-stu-id="a0867-185">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="a0867-186">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="a0867-186">Uninstall-Module</span></span>](Uninstall-Module.md)

