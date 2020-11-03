---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: 42a2b37144d9af188a7204500227fddf4827bdf9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216513"
---
# <span data-ttu-id="6601d-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="6601d-103">Update-Module</span></span>

## <span data-ttu-id="6601d-104">개요</span><span class="sxs-lookup"><span data-stu-id="6601d-104">SYNOPSIS</span></span>
<span data-ttu-id="6601d-105">온라인 갤러리에서 지정된 모듈의 최신 버전을 로컬 컴퓨터에 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-105">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <span data-ttu-id="6601d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6601d-106">SYNTAX</span></span>

### <span data-ttu-id="6601d-107">모두</span><span class="sxs-lookup"><span data-stu-id="6601d-107">All</span></span>

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6601d-108">설명</span><span class="sxs-lookup"><span data-stu-id="6601d-108">DESCRIPTION</span></span>

<span data-ttu-id="6601d-109">`Update-Module`Cmdlet은 온라인 갤러리에서 모듈의 최신 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-109">The `Update-Module` cmdlet installs a module's newest version from an online gallery.</span></span> <span data-ttu-id="6601d-110">업데이트를 설치 하기 전에 확인 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-110">You're prompted to confirm the update before it's installed.</span></span> <span data-ttu-id="6601d-111">업데이트는를 사용 하 여 로컬 컴퓨터에 설치 된 모듈에 대해서만 설치 됩니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="6601d-111">Updates are installed only for modules that were installed on the local computer with `Install-Module`.</span></span> <span data-ttu-id="6601d-112">`Update-Module``$env:PSModulePath`설치 된 모듈을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-112">`Update-Module` searches `$env:PSModulePath` for installed modules.</span></span>

<span data-ttu-id="6601d-113">`Update-Module` 매개 변수를 지정 하지 않으면 설치 된 모든 모듈을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-113">`Update-Module` with no parameters specified updates all installed modules.</span></span> <span data-ttu-id="6601d-114">업데이트할 모듈을 지정 하려면 **Name** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-114">To specify a module to update, use the **Name** parameter.</span></span> <span data-ttu-id="6601d-115">**RequiredVersion** 매개 변수를 사용 하 여 모듈의 특정 버전으로 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-115">You can update to a module's specific version by using the **RequiredVersion** parameter.</span></span>

<span data-ttu-id="6601d-116">설치 된 모듈이 이미 최신 버전인 경우 모듈은 업데이트 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-116">If an installed module is already the newest version, the module isn't updated.</span></span> <span data-ttu-id="6601d-117">에서 모듈을 찾을 수 없는 경우 `$env:PSModulePath` 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-117">If the module isn't found in `$env:PSModulePath`, an error is displayed.</span></span>

<span data-ttu-id="6601d-118">설치 된 모듈을 표시 하려면를 사용 `Get-InstalledModule` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-118">To display the installed modules, use `Get-InstalledModule`.</span></span>

## <span data-ttu-id="6601d-119">예제</span><span class="sxs-lookup"><span data-stu-id="6601d-119">EXAMPLES</span></span>

### <span data-ttu-id="6601d-120">예제 1: 모든 모듈 업데이트</span><span class="sxs-lookup"><span data-stu-id="6601d-120">Example 1: Update all modules</span></span>

<span data-ttu-id="6601d-121">이 예제에서는 설치 된 모든 모듈을 온라인 갤러리의 최신 버전으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-121">This example updates all installed modules to the newest version in an online gallery.</span></span>

```powershell
Update-Module
```

### <span data-ttu-id="6601d-122">예제 2: 이름별로 모듈 업데이트</span><span class="sxs-lookup"><span data-stu-id="6601d-122">Example 2: Update a module by name</span></span>

<span data-ttu-id="6601d-123">이 예에서는 온라인 갤러리에서 특정 모듈을 최신 버전으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-123">This example updates a specific module to the newest version in an online gallery.</span></span>

```powershell
Update-Module -Name SpeculationControl
```

<span data-ttu-id="6601d-124">`Update-Module`**Name** 매개 변수를 사용 하 여 **SpeculationControl** 특정 모듈을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-124">`Update-Module` uses the **Name** parameter to update a specific module, **SpeculationControl**.</span></span>

### <span data-ttu-id="6601d-125">예 3: Update-Module 실행 보기</span><span class="sxs-lookup"><span data-stu-id="6601d-125">Example 3: View what-if Update-Module runs</span></span>

<span data-ttu-id="6601d-126">이 예에서는 가상 시나리오를 수행 하 여가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="6601d-126">This example does a what-if scenario to show what happens if `Update-Module` is run.</span></span> <span data-ttu-id="6601d-127">명령이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-127">The command isn't run.</span></span>

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

<span data-ttu-id="6601d-128">`Update-Module`**WhatIf** 매개 변수를 사용 하 여가 실행 된 경우 발생 하는 결과를 표시 `Update-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-128">`Update-Module` uses the **WhatIf** parameter display what would happen if `Update-Module` were run.</span></span>

### <span data-ttu-id="6601d-129">예제 4: 모듈을 지정 된 버전으로 업데이트</span><span class="sxs-lookup"><span data-stu-id="6601d-129">Example 4: Update a module to a specified version</span></span>

<span data-ttu-id="6601d-130">이 예제에서는 모듈이 특정 버전으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-130">In this example, a module is updated to a specific version.</span></span> <span data-ttu-id="6601d-131">버전이 온라인 갤러리에 있어야 합니다. 그렇지 않으면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-131">The version must exist in the online gallery or an error is displayed.</span></span>

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

<span data-ttu-id="6601d-132">`Update-Module`**Name** 매개 변수를 사용 하 여 **SpeculationControl** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-132">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="6601d-133">**RequiredVersion** 매개 변수는 **1.0.14** 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-133">The **RequiredVersion** parameter specifies the version, **1.0.14**.</span></span>

### <span data-ttu-id="6601d-134">예 5: 확인 하지 않고 모듈 업데이트</span><span class="sxs-lookup"><span data-stu-id="6601d-134">Example 5: Update a module without confirmation</span></span>

<span data-ttu-id="6601d-135">이 예에서는 온라인 갤러리에서 모듈을 최신 버전으로 업데이트 하기 위한 확인을 요청 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-135">This example doesn't request confirmation to update the module to the newest version from an online gallery.</span></span> <span data-ttu-id="6601d-136">모듈이 이미 설치 되어 있는 경우 **Force** 매개 변수는 모듈을 다시 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-136">If the module is already installed, the **Force** parameter reinstalls the module.</span></span>

```powershell
Update-Module -Name SpeculationControl -Force
```

<span data-ttu-id="6601d-137">`Update-Module`**Name** 매개 변수를 사용 하 여 **SpeculationControl** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-137">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="6601d-138">**Force** 매개 변수는 사용자 확인을 요청 하지 않고 모듈을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-138">The **Force** parameter updates the module without requesting user confirmation.</span></span>

## <span data-ttu-id="6601d-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6601d-139">PARAMETERS</span></span>

### <span data-ttu-id="6601d-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6601d-140">-AcceptLicense</span></span>

<span data-ttu-id="6601d-141">패키지에 필요한 경우 설치 하는 동안 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="6601d-142">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="6601d-142">-AllowPrerelease</span></span>

<span data-ttu-id="6601d-143">시험판으로 표시 된 최신 모듈을 사용 하 여 모듈을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-143">Allows you to update a module with the newer module marked as a prerelease.</span></span>

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

### <span data-ttu-id="6601d-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6601d-144">-Confirm</span></span>

<span data-ttu-id="6601d-145">실행 하기 전에 확인 메시지를 표시 `Update-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-145">Prompts you for confirmation before running `Update-Module`.</span></span>

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

### <span data-ttu-id="6601d-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="6601d-146">-Credential</span></span>

<span data-ttu-id="6601d-147">모듈을 업데이트할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-147">Specifies a user account that has permission to update a module.</span></span>

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

### <span data-ttu-id="6601d-148">-Force</span><span class="sxs-lookup"><span data-stu-id="6601d-148">-Force</span></span>

<span data-ttu-id="6601d-149">확인을 요청 하는 메시지가 표시 되지 않고 지정 된 각 모듈을 강제로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-149">Forces an update of each specified module without a prompt to request confirmation.</span></span> <span data-ttu-id="6601d-150">모듈이 이미 설치 되어 있는 경우에는에서 모듈을 **강제로** 다시 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-150">If the module is already installed, **Force** reinstalls the module.</span></span>

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

### <span data-ttu-id="6601d-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6601d-151">-MaximumVersion</span></span>

<span data-ttu-id="6601d-152">업데이트할 단일 모듈의 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-152">Specifies the maximum version of a single module to update.</span></span> <span data-ttu-id="6601d-153">여러 모듈을 업데이트 하려는 경우에는이 매개 변수를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-153">You can't add this parameter if you're attempting to update multiple modules.</span></span> <span data-ttu-id="6601d-154">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-154">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6601d-155">-Name</span><span class="sxs-lookup"><span data-stu-id="6601d-155">-Name</span></span>

<span data-ttu-id="6601d-156">업데이트할 하나 이상의 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-156">Specifies the names of one or more modules to update.</span></span> <span data-ttu-id="6601d-157">`Update-Module``$env:PSModulePath`업데이트할 모듈을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-157">`Update-Module` searches `$env:PSModulePath` for the modules to update.</span></span> <span data-ttu-id="6601d-158">지정 된 모듈 이름에 대해 일치 하는 항목이 없는 경우 `$env:PSModulePath` 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-158">If no matches are found in `$env:PSModulePath` for the specified module name, an error occurs.</span></span>

<span data-ttu-id="6601d-159">와일드 카드는 모듈 이름에 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-159">Wildcards are accepted in module names.</span></span> <span data-ttu-id="6601d-160">지정 된 이름에 와일드 카드 문자를 추가 하 고 일치 항목을 찾을 수 없는 경우 오류가 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-160">If you add wildcard characters to the specified name and no matches are found, no error occurs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6601d-161">-PassThru</span><span class="sxs-lookup"><span data-stu-id="6601d-161">-PassThru</span></span>

<span data-ttu-id="6601d-162">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-162">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="6601d-163">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-163">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="6601d-164">-프록시</span><span class="sxs-lookup"><span data-stu-id="6601d-164">-Proxy</span></span>

<span data-ttu-id="6601d-165">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-165">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="6601d-166">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="6601d-166">-ProxyCredential</span></span>

<span data-ttu-id="6601d-167">**프록시** 매개 변수로 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-167">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="6601d-168">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6601d-168">-RequiredVersion</span></span>

<span data-ttu-id="6601d-169">기존에 설치 된 모듈을 업데이트할 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-169">Specifies the exact version to which the existing installed module will be updated.</span></span> <span data-ttu-id="6601d-170">**RequiredVersion** 에 지정 된 버전이 온라인 갤러리에 있어야 합니다. 그렇지 않으면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-170">The version specified by **RequiredVersion** must exist in the online gallery or an error is displayed.</span></span> <span data-ttu-id="6601d-171">단일 명령으로 둘 이상의 모듈이 업데이트 되는 경우 **RequiredVersion** 을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-171">If more than one module is updated in a single command, you can't use **RequiredVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6601d-172">-범위</span><span class="sxs-lookup"><span data-stu-id="6601d-172">-Scope</span></span>

<span data-ttu-id="6601d-173">모듈의 설치 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-173">Specifies the installation scope of the module.</span></span> <span data-ttu-id="6601d-174">이 매개 변수에 허용 되는 값은 **AllUsers** 및 **CurrentUser** 입니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-174">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span> <span data-ttu-id="6601d-175">**Scope** 가 지정 되지 않은 경우 업데이트는 **CurrentUser** 범위에 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-175">If **Scope** isn't specified, the update is installed in the **CurrentUser** scope.</span></span>

<span data-ttu-id="6601d-176">**AllUsers** 범위에는 상승 된 권한이 필요 하 고 컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-176">The **AllUsers** scope requires elevated permissions and installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="6601d-177">**CurrentUser** 는 높은 권한이 필요 하지 않으며 컴퓨터의 현재 사용자만 액세스할 수 있는 위치에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-177">The **CurrentUser** doesn't require elevated permissions and installs modules in a location that is accessible only to the current user of the computer:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="6601d-178">**범위** 를 정의 하지 않으면 PowerShellGet 버전에 따라 기본값이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-178">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="6601d-179">PowerShellGet 버전 2.0.0 이상에서 기본값은 **CurrentUser** 이며, 설치 시 권한 상승이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-179">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser** , which does not require elevation for install.</span></span>
- <span data-ttu-id="6601d-180">PowerShellGet 1. x 버전에서 기본값은 **AllUsers** 이며, 설치 시 권한 상승이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-180">In PowerShellGet 1.x versions, the default is **AllUsers** , which requires elevation for install.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6601d-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6601d-181">-WhatIf</span></span>

<span data-ttu-id="6601d-182">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="6601d-182">Shows what would happen if `Update-Module` runs.</span></span> <span data-ttu-id="6601d-183">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="6601d-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6601d-184">CommonParameters</span></span>

<span data-ttu-id="6601d-185">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6601d-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6601d-186">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6601d-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6601d-187">입력</span><span class="sxs-lookup"><span data-stu-id="6601d-187">INPUTS</span></span>

### <span data-ttu-id="6601d-188">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6601d-188">System.String[]</span></span>

### <span data-ttu-id="6601d-189">System.String</span><span class="sxs-lookup"><span data-stu-id="6601d-189">System.String</span></span>

### <span data-ttu-id="6601d-190">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="6601d-190">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="6601d-191">System.Uri</span><span class="sxs-lookup"><span data-stu-id="6601d-191">System.Uri</span></span>

## <span data-ttu-id="6601d-192">출력</span><span class="sxs-lookup"><span data-stu-id="6601d-192">OUTPUTS</span></span>

### <span data-ttu-id="6601d-193">System.Object</span><span class="sxs-lookup"><span data-stu-id="6601d-193">System.Object</span></span>

## <span data-ttu-id="6601d-194">참고</span><span class="sxs-lookup"><span data-stu-id="6601d-194">NOTES</span></span>

<span data-ttu-id="6601d-195">PowerShell 버전 6.0 이상에서는 기본 설치 범위가 항상 **CurrentUser** 입니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-195">For PowerShell version 6.0 and above, the default installation scope is always **CurrentUser**.</span></span>
<span data-ttu-id="6601d-196">**CurrentUser** 의 모듈 업데이트에 `$home\Documents\PowerShell\Modules` 는 상승 된 권한이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-196">Module updates for **CurrentUser** , `$home\Documents\PowerShell\Modules`, don't need elevated permissions.</span></span> <span data-ttu-id="6601d-197">**AllUsers** ,에 대 한 모듈 업데이트에는 `$env:ProgramFiles\PowerShell\Modules` 상승 된 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-197">Module updates for **AllUsers** , `$env:ProgramFiles\PowerShell\Modules`, need elevated permissions.</span></span>

<span data-ttu-id="6601d-198">`Update-Module` powershell 3.0 이상 버전의 PowerShell, windows 7 또는 Windows 2008 R2 이상 버전에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-198">`Update-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="6601d-199">**Name** 매개 변수를 사용 하 여 지정한 모듈을를 사용 하 여 설치 하지 않은 경우 `Install-Module` 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-199">If the module that you specify with the **Name** parameter wasn't installed by using `Install-Module`, an error occurs.</span></span>

<span data-ttu-id="6601d-200">을 `Update-Module` 실행 하 여 온라인 갤러리에서 설치한 모듈 에서만 실행할 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="6601d-200">You can only run `Update-Module` on modules that you installed from the online gallery by running `Install-Module`.</span></span>

<span data-ttu-id="6601d-201">`Update-Module`에서 사용 중인 이진 파일을 업데이트 하려고 하면에서 `Update-Module` 문제 프로세스를 식별 하는 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-201">If `Update-Module` attempts to update binaries that are in use, `Update-Module` returns an error that identifies the problem processes.</span></span> <span data-ttu-id="6601d-202">프로세스가 중지 된 후 사용자에 게 다시 시도 하는 알림이 사용자에 게 `Update-Module` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6601d-202">The user is informed to retry `Update-Module` after the processes are stopped.</span></span>

## <span data-ttu-id="6601d-203">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6601d-203">RELATED LINKS</span></span>

[<span data-ttu-id="6601d-204">Find-Module</span><span class="sxs-lookup"><span data-stu-id="6601d-204">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="6601d-205">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="6601d-205">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="6601d-206">Install-Module</span><span class="sxs-lookup"><span data-stu-id="6601d-206">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="6601d-207">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="6601d-207">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="6601d-208">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="6601d-208">Uninstall-Module</span></span>](Uninstall-Module.md)
