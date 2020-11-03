---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: 5e210a626c0b64884bb95807a51d712061276122
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2020
ms.locfileid: "93219106"
---
# <span data-ttu-id="df4d9-103">Install-Module</span><span class="sxs-lookup"><span data-stu-id="df4d9-103">Install-Module</span></span>

## <span data-ttu-id="df4d9-104">개요</span><span class="sxs-lookup"><span data-stu-id="df4d9-104">SYNOPSIS</span></span>
<span data-ttu-id="df4d9-105">리포지토리에서 하나 이상의 모듈을 다운로드 하 고 로컬 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-105">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

## <span data-ttu-id="df4d9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="df4d9-106">SYNTAX</span></span>

### <span data-ttu-id="df4d9-107">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="df4d9-107">NameParameterSet (Default)</span></span>

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="df4d9-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="df4d9-108">InputObject</span></span>

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="df4d9-109">설명</span><span class="sxs-lookup"><span data-stu-id="df4d9-109">DESCRIPTION</span></span>

<span data-ttu-id="df4d9-110">`Install-Module`Cmdlet은 온라인 리포지토리에서 지정 된 조건을 충족 하는 하나 이상의 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-110">The `Install-Module` cmdlet gets one or more modules that meet specified criteria from an online repository.</span></span> <span data-ttu-id="df4d9-111">Cmdlet은 검색 결과가 유효한 모듈 인지 확인 하 고 모듈 폴더를 설치 위치로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-111">The cmdlet verifies that search results are valid modules and copies the module folders to the installation location.</span></span> <span data-ttu-id="df4d9-112">설치 후 설치 된 모듈을 자동으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-112">Installed modules are not automatically imported after installation.</span></span>
<span data-ttu-id="df4d9-113">지정 된 모듈의 최소, 최대 및 정확한 버전에 따라 설치 되는 모듈을 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-113">You can filter which module is installed based on the minimum, maximum, and exact versions of specified modules.</span></span>

<span data-ttu-id="df4d9-114">설치 되는 모듈의 이름이 나 버전이 같거나 기존 모듈의 명령을 포함 하는 경우 경고 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-114">If the module being installed has the same name or version, or contains commands in an existing module, warning messages are displayed.</span></span> <span data-ttu-id="df4d9-115">모듈을 설치 하 고 경고를 재정의할지를 확인 한 후에는 `-Force` 및 `-AllowClobber` 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-115">After you confirm that you want to install the module and override the warnings, use the `-Force` and `-AllowClobber` parameters.</span></span> <span data-ttu-id="df4d9-116">리포지토리 설정에 따라 계속 하려면 모듈 설치에 대 한 프롬프트에 응답 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-116">Dependent upon your repository settings, you might need to answer a prompt for the module installation to continue.</span></span>

<span data-ttu-id="df4d9-117">이 예제에서는 [PowerShell 갤러리](https://www.powershellgallery.com/) 를 등록 된 유일한 리포지토리로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-117">These examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="df4d9-118">`Get-PSRepository` 등록 된 리포지토리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-118">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="df4d9-119">등록 된 리포지토리가 여러 개 있는 경우 `-Repository` 매개 변수를 사용 하 여 리포지토리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-119">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="df4d9-120">예제</span><span class="sxs-lookup"><span data-stu-id="df4d9-120">EXAMPLES</span></span>

### <span data-ttu-id="df4d9-121">예제 1: 모듈 찾기 및 설치</span><span class="sxs-lookup"><span data-stu-id="df4d9-121">Example 1: Find and install a module</span></span>

<span data-ttu-id="df4d9-122">이 예제에서는 리포지토리에서 모듈을 찾아 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-122">This example finds a module in the repository and installs the module.</span></span>

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

<span data-ttu-id="df4d9-123">는 `Find-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-123">The `Find-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="df4d9-124">기본적으로 최신 버전의 모듈은 리포지토리에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-124">By default, the newest version of the module is downloaded from the repository.</span></span> <span data-ttu-id="df4d9-125">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-125">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="df4d9-126">`Install-Module` 의 모든 사용자에 대 한 모듈을 설치 `$env:ProgramFiles\WindowsPowerShell\Modules` 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-126">`Install-Module` installs the module for all users in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

### <span data-ttu-id="df4d9-127">예제 2: 이름별로 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="df4d9-127">Example 2: Install a module by name</span></span>

<span data-ttu-id="df4d9-128">이 예제에서는 최신 버전의 **PowerShellGet** 모듈이 설치 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-128">In this example, the newest version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet
```

<span data-ttu-id="df4d9-129">는 `Install-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-129">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="df4d9-130">기본적으로 최신 버전의 모듈은 리포지토리에서 다운로드 되어 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-130">By default, the newest version of the module is downloaded from the repository and installed.</span></span>

### <span data-ttu-id="df4d9-131">예제 3: 최소 버전을 사용 하 여 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="df4d9-131">Example 3: Install a module using its minimum version</span></span>

<span data-ttu-id="df4d9-132">이 예제에서는 **PowerShellGet** 모듈의 최소 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-132">In this example, the minimum version of the **PowerShellGet** module is installed.</span></span> <span data-ttu-id="df4d9-133">**MinimumVersion** 매개 변수는 설치 해야 하는 모듈의 가장 낮은 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-133">The **MinimumVersion** parameter specifies the lowest version of the module that should be installed.</span></span> <span data-ttu-id="df4d9-134">최신 버전의 모듈을 사용할 수 있는 경우 모든 사용자에 대해 해당 버전이 다운로드 되어 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-134">If a newer version of the module is available, that version is downloaded and installed for all users.</span></span>

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

<span data-ttu-id="df4d9-135">는 `Install-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-135">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="df4d9-136">**MinimumVersion** 매개 변수는 버전 **2.0.1** 을 리포지토리에서 다운로드 하 여 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-136">The **MinimumVersion** parameter specifies that version **2.0.1** is downloaded from the repository and installed.</span></span> <span data-ttu-id="df4d9-137">버전 **2.0.4 이상을** 를 사용할 수 있기 때문에 모든 사용자에 대해 해당 버전이 다운로드 되어 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-137">Because version **2.0.4** is available, that version is downloaded and installed for all users.</span></span>

### <span data-ttu-id="df4d9-138">예제 4: 모듈의 특정 버전 설치</span><span class="sxs-lookup"><span data-stu-id="df4d9-138">Example 4: Install a specific version of a module</span></span>

<span data-ttu-id="df4d9-139">이 예제에서는 특정 버전의 **PowerShellGet** 모듈이 설치 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-139">In this example, a specific version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

<span data-ttu-id="df4d9-140">는 `Install-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-140">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="df4d9-141">**RequiredVersion** 매개 변수는 버전 **2.0.0** 가 모든 사용자에 게 다운로드 및 설치 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-141">The **RequiredVersion** parameter specifies that version **2.0.0** is downloaded and installed for all users.</span></span>

### <span data-ttu-id="df4d9-142">예 5: 현재 사용자에 대해서만 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="df4d9-142">Example 5: Install a module only for the current user</span></span>

<span data-ttu-id="df4d9-143">이 예에서는 현재 사용자에 대해서만 최신 버전의 모듈을 다운로드 하 여 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-143">This example downloads and installs the newest version of a module, only for the current user.</span></span>

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

<span data-ttu-id="df4d9-144">는 `Install-Module` **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-144">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>
<span data-ttu-id="df4d9-145">`Install-Module` 최신 버전의 **PowerShellGet** 을 현재 사용자의 디렉터리에 다운로드 하 여 설치 `$home\Documents\WindowsPowerShell\Modules` 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-145">`Install-Module` downloads and installs the newest version of **PowerShellGet** into the current user's directory, `$home\Documents\WindowsPowerShell\Modules`.</span></span>

## <span data-ttu-id="df4d9-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="df4d9-146">PARAMETERS</span></span>

### <span data-ttu-id="df4d9-147">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="df4d9-147">-AcceptLicense</span></span>

<span data-ttu-id="df4d9-148">라이선스가 필요한 모듈의 경우에는 설치 중에 **Acceptlicense** 가 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-148">For modules that require a license, **AcceptLicense** automatically accepts the license agreement during installation.</span></span> <span data-ttu-id="df4d9-149">자세한 내용은 [라이선스 동의가 필요한 모듈](/powershell/scripting/gallery/concepts/module-license-acceptance)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="df4d9-149">For more information, see [Modules Requiring License Acceptance](/powershell/scripting/gallery/concepts/module-license-acceptance).</span></span>

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

### <span data-ttu-id="df4d9-150">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="df4d9-150">-AllowClobber</span></span>

<span data-ttu-id="df4d9-151">컴퓨터의 기존 명령과 관련 된 설치 충돌에 대 한 경고 메시지를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-151">Overrides warning messages about installation conflicts about existing commands on a computer.</span></span>
<span data-ttu-id="df4d9-152">모듈에 의해 설치 되는 명령과 이름이 같은 기존 명령을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-152">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>
<span data-ttu-id="df4d9-153">**AllowClobber** 및 **Force** 는 명령에 함께 사용할 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-153">**AllowClobber** and **Force** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="df4d9-154">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="df4d9-154">-AllowPrerelease</span></span>

<span data-ttu-id="df4d9-155">시험판으로 표시 된 모듈을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-155">Allows you to install a module marked as a pre-release.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="df4d9-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="df4d9-156">-Confirm</span></span>

<span data-ttu-id="df4d9-157">Cmdlet을 실행 하기 전에 확인 메시지를 표시 `Install-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-157">Prompts you for confirmation before running the `Install-Module` cmdlet.</span></span>

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

### <span data-ttu-id="df4d9-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="df4d9-158">-Credential</span></span>

<span data-ttu-id="df4d9-159">지정 된 패키지 공급자 또는 원본에 대해 모듈을 설치할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-159">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="df4d9-160">-Force</span><span class="sxs-lookup"><span data-stu-id="df4d9-160">-Force</span></span>

<span data-ttu-id="df4d9-161">모듈을 설치 하 고 모듈 설치 충돌에 대 한 경고 메시지를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-161">Installs a module and overrides warning messages about module installation conflicts.</span></span> <span data-ttu-id="df4d9-162">컴퓨터에 같은 이름의 모듈이 이미 있으면 **Force** 를 사용 하 여 여러 버전을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-162">If a module with the same name already exists on the computer, **Force** allows for multiple versions to be installed.</span></span> <span data-ttu-id="df4d9-163">이름과 버전이 같은 기존 모듈이 있으면에서 해당 버전을 **강제로** 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-163">If there is an existing module with the same name and version, **Force** overwrites that version.</span></span> <span data-ttu-id="df4d9-164">**Force** 및 **AllowClobber** 는 명령에 함께 사용할 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-164">**Force** and **AllowClobber** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="df4d9-165">-InputObject</span><span class="sxs-lookup"><span data-stu-id="df4d9-165">-InputObject</span></span>

<span data-ttu-id="df4d9-166">파이프라인 입력에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-166">Used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="df4d9-167">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="df4d9-167">-MaximumVersion</span></span>

<span data-ttu-id="df4d9-168">설치할 단일 모듈의 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-168">Specifies the maximum version of a single module to install.</span></span> <span data-ttu-id="df4d9-169">설치 된 버전은 **MaximumVersion** 보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-169">The version installed must be less than or equal to **MaximumVersion**.</span></span> <span data-ttu-id="df4d9-170">여러 모듈을 설치 하려는 경우 **MaximumVersion** 을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-170">If you want to install multiple modules, you cannot use **MaximumVersion**.</span></span> <span data-ttu-id="df4d9-171">**MaximumVersion** 및 **RequiredVersion** 은 동일한 명령에서 사용할 수 없습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-171">**MaximumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="df4d9-172">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="df4d9-172">-MinimumVersion</span></span>

<span data-ttu-id="df4d9-173">설치할 단일 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-173">Specifies the minimum version of a single module to install.</span></span> <span data-ttu-id="df4d9-174">설치 된 버전은 **MinimumVersion** 보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-174">The version installed must be greater than or equal to **MinimumVersion**.</span></span> <span data-ttu-id="df4d9-175">최신 버전의 모듈을 사용할 수 있는 경우 최신 버전이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-175">If there is a newer version of the module available, the newer version is installed.</span></span> <span data-ttu-id="df4d9-176">여러 모듈을 설치 하려는 경우 **MinimumVersion** 을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-176">If you want to install multiple modules, you cannot use **MinimumVersion**.</span></span>
<span data-ttu-id="df4d9-177">**MinimumVersion** 및 **RequiredVersion** 은 동일한 명령에서 사용할 수 없습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-177">**MinimumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="df4d9-178">-Name</span><span class="sxs-lookup"><span data-stu-id="df4d9-178">-Name</span></span>

<span data-ttu-id="df4d9-179">온라인 갤러리에서 설치할 모듈의 정확한 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-179">Specifies the exact names of modules to install from the online gallery.</span></span> <span data-ttu-id="df4d9-180">쉼표로 구분 된 모듈 이름 목록이 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-180">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="df4d9-181">모듈 이름은 리포지토리의 모듈 이름과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-181">The module name must match the module name in the repository.</span></span> <span data-ttu-id="df4d9-182">`Find-Module`를 사용 하 여 모듈 이름 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-182">Use `Find-Module` to get a list of module names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="df4d9-183">-PassThru</span><span class="sxs-lookup"><span data-stu-id="df4d9-183">-PassThru</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="df4d9-184">-프록시</span><span class="sxs-lookup"><span data-stu-id="df4d9-184">-Proxy</span></span>

<span data-ttu-id="df4d9-185">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-185">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="df4d9-186">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="df4d9-186">-ProxyCredential</span></span>

<span data-ttu-id="df4d9-187">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-187">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="df4d9-188">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="df4d9-188">-Repository</span></span>

<span data-ttu-id="df4d9-189">**리포지토리** 매개 변수를 사용 하 여 모듈을 다운로드 하 고 설치 하는 데 사용 되는 리포지토리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-189">Use the **Repository** parameter to specify which repository is used to download and install a module.</span></span> <span data-ttu-id="df4d9-190">여러 리포지토리를 등록할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-190">Used when multiple repositories are registered.</span></span> <span data-ttu-id="df4d9-191">명령에 등록 된 리포지토리의 이름을 지정 합니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-191">Specifies the name of a registered repository in the `Install-Module` command.</span></span> <span data-ttu-id="df4d9-192">리포지토리를 등록 하려면를 사용 `Register-PSRepository` 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-192">To register a repository, use `Register-PSRepository`.</span></span>
<span data-ttu-id="df4d9-193">등록 된 리포지토리를 표시 하려면를 사용 `Get-PSRepository` 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-193">To display registered repositories, use `Get-PSRepository`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="df4d9-194">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="df4d9-194">-RequiredVersion</span></span>

<span data-ttu-id="df4d9-195">설치할 단일 모듈의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-195">Specifies the exact version of a single module to install.</span></span> <span data-ttu-id="df4d9-196">지정 된 버전에 대 한 리포지토리에 일치 하는 항목이 없는 경우 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-196">If there is no match in the repository for the specified version, an error is displayed.</span></span> <span data-ttu-id="df4d9-197">여러 모듈을 설치 하려는 경우 **RequiredVersion** 을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-197">If you want to install multiple modules, you cannot use **RequiredVersion**.</span></span> <span data-ttu-id="df4d9-198">**RequiredVersion** 은 `Install-Module` **MinimumVersion** 또는 **MaximumVersion** 과 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-198">**RequiredVersion** cannot be used in the same `Install-Module` command as **MinimumVersion** or **MaximumVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="df4d9-199">-범위</span><span class="sxs-lookup"><span data-stu-id="df4d9-199">-Scope</span></span>

<span data-ttu-id="df4d9-200">모듈의 설치 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-200">Specifies the installation scope of the module.</span></span> <span data-ttu-id="df4d9-201">이 매개 변수에 허용 되는 값은 **AllUsers** 및 **CurrentUser** 입니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-201">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span>

<span data-ttu-id="df4d9-202">**AllUsers** 범위는 컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-202">The **AllUsers** scope installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\WindowsPowerShell\Modules`

<span data-ttu-id="df4d9-203">**CurrentUser** 는 컴퓨터의 현재 사용자만 액세스할 수 있는 위치에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-203">The **CurrentUser** installs modules in a location that is accessible only to the current user of the computer.</span></span> <span data-ttu-id="df4d9-204">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="df4d9-204">For example:</span></span>

`$home\Documents\WindowsPowerShell\Modules`

<span data-ttu-id="df4d9-205">**범위** 를 정의 하지 않으면 PowerShellGet 버전에 따라 기본값이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-205">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="df4d9-206">PowerShellGet 버전 2.0.0 이상에서 기본값은 **CurrentUser** 이며, 설치 시 권한 상승이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-206">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser** , which does not require elevation for install.</span></span>
- <span data-ttu-id="df4d9-207">PowerShellGet 1. x 버전에서 기본값은 **AllUsers** 이며, 설치 시 권한 상승이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-207">In PowerShellGet 1.x versions, the default is **AllUsers** , which requires elevation for install.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="df4d9-208">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="df4d9-208">-SkipPublisherCheck</span></span>

<span data-ttu-id="df4d9-209">컴퓨터에 이미 존재 하는 모듈의 최신 버전을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-209">Allows you to install a newer version of a module that already exists on your computer.</span></span> <span data-ttu-id="df4d9-210">예를 들어 신뢰할 수 있는 게시자가 기존 모듈을 디지털 서명 하지만 새 버전이 신뢰할 수 있는 게시자에 의해 디지털로 서명 되지 않은 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-210">For example, when an existing module is digitally signed by a trusted publisher but the new version is not digitally signed by a trusted publisher.</span></span>

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

### <span data-ttu-id="df4d9-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="df4d9-211">-WhatIf</span></span>

<span data-ttu-id="df4d9-212">명령이 실행 된 경우 발생 하는 상황을 보여 줍니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-212">Shows what would happen if an `Install-Module` command was run.</span></span> <span data-ttu-id="df4d9-213">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="df4d9-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="df4d9-214">CommonParameters</span></span>

<span data-ttu-id="df4d9-215">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="df4d9-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="df4d9-216">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df4d9-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="df4d9-217">입력</span><span class="sxs-lookup"><span data-stu-id="df4d9-217">INPUTS</span></span>

### <span data-ttu-id="df4d9-218">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="df4d9-218">PSRepositoryItemInfo</span></span>

<span data-ttu-id="df4d9-219">`Find-Module` 파이프라인에서로 전송할 수 있는 **PSRepositoryItemInfo** 개체를 만듭니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-219">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span>

### <span data-ttu-id="df4d9-220">System.String[]</span><span class="sxs-lookup"><span data-stu-id="df4d9-220">System.String[]</span></span>

### <span data-ttu-id="df4d9-221">System.web. PSObject []</span><span class="sxs-lookup"><span data-stu-id="df4d9-221">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="df4d9-222">System.String</span><span class="sxs-lookup"><span data-stu-id="df4d9-222">System.String</span></span>

### <span data-ttu-id="df4d9-223">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="df4d9-223">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="df4d9-224">System.Uri</span><span class="sxs-lookup"><span data-stu-id="df4d9-224">System.Uri</span></span>

## <span data-ttu-id="df4d9-225">출력</span><span class="sxs-lookup"><span data-stu-id="df4d9-225">OUTPUTS</span></span>

### <span data-ttu-id="df4d9-226">PSRepositoryItemInfo.</span><span class="sxs-lookup"><span data-stu-id="df4d9-226">Microsoft.PowerShell.Commands.PSRepositoryItemInfo</span></span>

<span data-ttu-id="df4d9-227">**PassThru** 매개 변수를 사용 하는 경우 `Install-Module` 은 모듈에 대 한 **PSRepositoryItemInfo** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-227">When using the **PassThru** parameter, `Install-Module` outputs a **PSRepositoryItemInfo** object for the module.</span></span> <span data-ttu-id="df4d9-228">이는 cmdlet에서 가져오는 것과 동일한 정보입니다 `Find-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-228">This is the same information that you get from the `Find-Module` cmdlet.</span></span>

## <span data-ttu-id="df4d9-229">참고</span><span class="sxs-lookup"><span data-stu-id="df4d9-229">NOTES</span></span>

<span data-ttu-id="df4d9-230">`Install-Module` windows 7 또는 windows 2008 R2 이상 릴리스에서 PowerShell 5.0 이상 버전에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-230">`Install-Module` runs on PowerShell 5.0 or later releases, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="df4d9-231">보안 모범 사례로, cmdlet 또는 함수를 처음 실행 하기 전에 모듈의 코드를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-231">As a security best practice, evaluate a module's code before running any cmdlets or functions for the first time.</span></span> <span data-ttu-id="df4d9-232">악성 코드가 포함 된 모듈 실행을 방지 하기 위해 설치 후 설치 된 모듈을 자동으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-232">To prevent running modules that contain malicious code, installed modules are not automatically imported after installation.</span></span>

<span data-ttu-id="df4d9-233">**이름** 매개 변수로 지정 된 모듈 이름이 리포지토리에 없으면에서 `Install-Module` 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-233">If the module name specified by the **Name** parameter does not exist in the repository, `Install-Module` returns an error.</span></span>

<span data-ttu-id="df4d9-234">여러 모듈을 설치 하려면 **Name** 매개 변수를 사용 하 고 쉼표로 구분 된 모듈 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-234">To install multiple modules, use the **Name** parameter and specify a comma-separated array of module names.</span></span> <span data-ttu-id="df4d9-235">여러 모듈 이름을 지정 하는 경우 **MinimumVersion** , **MaximumVersion** 또는 **RequiredVersion** 을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-235">If you specify multiple module names, you cannot use **MinimumVersion** , **MaximumVersion** , or **RequiredVersion**.</span></span> <span data-ttu-id="df4d9-236">`Find-Module` 파이프라인에서로 전송할 수 있는 **PSRepositoryItemInfo** 개체를 만듭니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-236">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span> <span data-ttu-id="df4d9-237">파이프라인은 단일 명령으로 설치할 여러 모듈을 지정 하는 또 다른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-237">The pipeline is another way to specify multiple modules to install in a single command.</span></span>

<span data-ttu-id="df4d9-238">기본적으로 **AllUsers** 의 범위에 대 한 모듈은에 설치 됩니다 `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-238">By default, modules for the scope of **AllUsers** are installed in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="df4d9-239">PowerShell DSC (필요한 상태 구성) 리소스를 설치할 때 기본적으로 혼동을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-239">The default prevents confusion when you install PowerShell Desired State Configuration (DSC) resources.</span></span>

<span data-ttu-id="df4d9-240">모듈 설치에 실패 하 고 `.psm1` `.psd1` 폴더 내에 같은 이름의, 또는가 없는 경우 가져올 수 없습니다 `.dll` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-240">A module installation fails and cannot be imported if it does not have a `.psm1`, `.psd1`, or `.dll` of the same name within the folder.</span></span> <span data-ttu-id="df4d9-241">**Force** 매개 변수를 사용 하 여 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-241">Use the **Force** parameter to install the module.</span></span>

<span data-ttu-id="df4d9-242">기존 모듈의 버전이 **name** 매개 변수에 지정 된 이름과 일치 하 고 **MinimumVersion** 또는 **RequiredVersion** 매개 변수를 사용 하지 않으면 `Install-Module` 자동으로 계속 되지만 모듈이 설치 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-242">If an existing module's version matches the name specified by the **Name** parameter, and the **MinimumVersion** or **RequiredVersion** parameter are not used, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="df4d9-243">기존 모듈의 버전이 **MinimumVersion** 매개 변수 값 보다 크거나 **RequiredVersion** 매개 변수 값과 같으면가 `Install-Module` 자동으로 계속 되지만 모듈을 설치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-243">If an existing module's version is greater than the value of the **MinimumVersion** parameter, or equal to the value of the **RequiredVersion** parameter, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="df4d9-244">기존 모듈이 **MinimumVersion** 또는 **RequiredVersion** 매개 변수로 지정 된 값과 일치 하지 않으면 명령에서 오류가 발생 합니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="df4d9-244">If the existing module does not match the values specified by the **MinimumVersion** or **RequiredVersion** parameters, an error occurs in the `Install-Module` command.</span></span> <span data-ttu-id="df4d9-245">예를 들어 기존에 설치 된 모듈의 버전이 **MinimumVersion** 값 보다 낮거나 **RequiredVersion** 값과 같지 않은 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-245">For example, if the version of the existing installed module is lower than the **MinimumVersion** value or not equal to the **RequiredVersion** value.</span></span>

<span data-ttu-id="df4d9-246">모듈을 설치 하면 모듈 게시자에 필요한 대로 지정 된 모든 종속 모듈도 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-246">A module installation will also install any dependent modules specified as required by the module publisher.</span></span>
<span data-ttu-id="df4d9-247">게시자는 모듈 매니페스트에서 필요한 모듈 및 해당 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4d9-247">The publisher will specify the required modules and their versions in the module manifest.</span></span>

## <span data-ttu-id="df4d9-248">관련 링크</span><span class="sxs-lookup"><span data-stu-id="df4d9-248">RELATED LINKS</span></span>

[<span data-ttu-id="df4d9-249">Find-Module</span><span class="sxs-lookup"><span data-stu-id="df4d9-249">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="df4d9-250">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="df4d9-250">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="df4d9-251">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="df4d9-251">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="df4d9-252">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="df4d9-252">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="df4d9-253">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="df4d9-253">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="df4d9-254">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="df4d9-254">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="df4d9-255">Update-Module</span><span class="sxs-lookup"><span data-stu-id="df4d9-255">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="df4d9-256">about_Module</span><span class="sxs-lookup"><span data-stu-id="df4d9-256">about_Module</span></span>](../Microsoft.PowerShell.Core/About/about_Modules.md)
