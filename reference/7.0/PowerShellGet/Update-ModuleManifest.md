---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 2ad1f5991920cecf0a5b494bde698510c1c55b94
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890807"
---
# <span data-ttu-id="af954-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="af954-103">Update-ModuleManifest</span></span>

## <span data-ttu-id="af954-104">개요</span><span class="sxs-lookup"><span data-stu-id="af954-104">SYNOPSIS</span></span>
<span data-ttu-id="af954-105">모듈 매니페스트 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-105">Updates a module manifest file.</span></span>

## <span data-ttu-id="af954-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="af954-106">SYNTAX</span></span>

### <span data-ttu-id="af954-107">모두</span><span class="sxs-lookup"><span data-stu-id="af954-107">All</span></span>

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="af954-108">설명</span><span class="sxs-lookup"><span data-stu-id="af954-108">DESCRIPTION</span></span>

<span data-ttu-id="af954-109">`Update-ModuleManifest`Cmdlet은 모듈 매니페스트 ( `.psd1` ) 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-109">The `Update-ModuleManifest` cmdlet updates a module manifest (`.psd1`) file.</span></span>

## <span data-ttu-id="af954-110">예제</span><span class="sxs-lookup"><span data-stu-id="af954-110">EXAMPLES</span></span>

### <span data-ttu-id="af954-111">예제 1: 모듈 매니페스트 업데이트</span><span class="sxs-lookup"><span data-stu-id="af954-111">Example 1: Update a module manifest</span></span>

<span data-ttu-id="af954-112">이 예에서는 기존 모듈 매니페스트 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-112">This example updates an existing module manifest file.</span></span> <span data-ttu-id="af954-113">스 플랫는 매개 변수 값을에 전달 하는 데 사용 됩니다 `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="af954-113">Splatting is used to pass parameter values to `Update-ModuleManifest`.</span></span> <span data-ttu-id="af954-114">자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af954-114">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

<span data-ttu-id="af954-115">`$Parms` 는 **Path**, **Author**, **CompanyName** 및 **저작권** 에 대 한 매개 변수 값을 저장 하는 스 플랫입니다.</span><span class="sxs-lookup"><span data-stu-id="af954-115">`$Parms` is a splat that stores the parameter values for **Path**, **Author**, **CompanyName**, and **Copyright**.</span></span> <span data-ttu-id="af954-116">`Update-ModuleManifest` 에서 매개 변수 값을 가져오고 `@Parms` 모듈 매니페스트 ( **TestManifest.psd1)** 를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-116">`Update-ModuleManifest` gets the parameter values from `@Parms` and updates the module manifest, **TestManifest.psd1**.</span></span>

## <span data-ttu-id="af954-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="af954-117">PARAMETERS</span></span>

### <span data-ttu-id="af954-118">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="af954-118">-AliasesToExport</span></span>

<span data-ttu-id="af954-119">모듈이 내보내는 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-119">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="af954-120">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="af954-120">Wildcards are permitted.</span></span>

<span data-ttu-id="af954-121">이 매개 변수를 사용 하 여 모듈에서 내보내는 별칭을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-121">Use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="af954-122">**AliasesToExport** 는 내보낸 별칭 목록에서 별칭을 제거할 수 있지만 목록에 별칭을 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-122">**AliasesToExport** can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="af954-123">-작성자</span><span class="sxs-lookup"><span data-stu-id="af954-123">-Author</span></span>

<span data-ttu-id="af954-124">모듈 작성자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-124">Specifies the module author.</span></span>

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

### <span data-ttu-id="af954-125">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="af954-125">-ClrVersion</span></span>

<span data-ttu-id="af954-126">모듈에 필요한 Microsoft .NET Framework의 CLR(공용 언어 런타임) 최소 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-126">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-127">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="af954-127">-CmdletsToExport</span></span>

<span data-ttu-id="af954-128">모듈이 내보내는 cmdlet을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-128">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="af954-129">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="af954-129">Wildcards are permitted.</span></span>

<span data-ttu-id="af954-130">이 매개 변수를 사용 하 여 모듈에서 내보내는 cmdlet을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-130">Use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="af954-131">**Cmdletstoexport** 는 내보낸 cmdlet 목록에서 cmdlet을 제거할 수 있지만 목록에 cmdlet을 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-131">**CmdletsToExport** can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="af954-132">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="af954-132">-CompanyName</span></span>

<span data-ttu-id="af954-133">모듈을 만든 회사나 공급 업체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-133">Specifies the company or vendor who created the module.</span></span>

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

### <span data-ttu-id="af954-134">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="af954-134">-CompatiblePSEditions</span></span>

<span data-ttu-id="af954-135">모듈의 호환 되는 **pseditions가** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-135">Specifies the compatible **PSEditions** of the module.</span></span> <span data-ttu-id="af954-136">**PSEdition** 에 대 한 자세한 내용은 [호환 되는 PowerShell 버전이 있는 모듈](/powershell/scripting/gallery/concepts/module-psedition-support)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af954-136">For information about **PSEdition**, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="af954-137">-Confirm</span></span>

<span data-ttu-id="af954-138">실행 하기 전에 확인 메시지를 표시 `Update-ModuleManifest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-138">Prompts you for confirmation before running `Update-ModuleManifest`.</span></span>

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

### <span data-ttu-id="af954-139">-저작권</span><span class="sxs-lookup"><span data-stu-id="af954-139">-Copyright</span></span>

<span data-ttu-id="af954-140">모듈의 저작권 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-140">Specifies a copyright statement for the module.</span></span>

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

### <span data-ttu-id="af954-141">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="af954-141">-DefaultCommandPrefix</span></span>

<span data-ttu-id="af954-142">기본 명령 접두사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-142">Specifies the default command prefix.</span></span>

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

### <span data-ttu-id="af954-143">-Description</span><span class="sxs-lookup"><span data-stu-id="af954-143">-Description</span></span>

<span data-ttu-id="af954-144">모듈에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-144">Specifies a description of the module.</span></span>

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

### <span data-ttu-id="af954-145">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="af954-145">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="af954-146">모듈에 필요한 Microsoft .NET Framework의 최소 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-146">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-147">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="af954-147">-DscResourcesToExport</span></span>

<span data-ttu-id="af954-148">모듈에서 내보내는 DSC (Desired State Configuration) 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-148">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="af954-149">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="af954-149">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="af954-150">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="af954-150">-ExternalModuleDependencies</span></span>

<span data-ttu-id="af954-151">외부 모듈 종속성의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-151">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="af954-152">-FileList</span><span class="sxs-lookup"><span data-stu-id="af954-152">-FileList</span></span>

<span data-ttu-id="af954-153">모듈에 포함된 모든 항목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-153">Specifies all items that are included in the module.</span></span>

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

### <span data-ttu-id="af954-154">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="af954-154">-FormatsToProcess</span></span>

<span data-ttu-id="af954-155">`.ps1xml`모듈을 가져올 때 실행 되는 서식 파일 ()을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-155">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="af954-156">모듈을 가져올 때 PowerShell에서 지정 된 파일을 사용 하 여 cmdlet을 실행 합니다 `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="af954-156">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="af954-157">형식 지정 파일의 범위는 지정 되지 않기 때문에 세션의 모든 세션 상태에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af954-157">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="af954-158">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="af954-158">-FunctionsToExport</span></span>

<span data-ttu-id="af954-159">모듈이 내보내는 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-159">Specifies the functions that the module exports.</span></span> <span data-ttu-id="af954-160">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="af954-160">Wildcards are permitted.</span></span>

<span data-ttu-id="af954-161">이 매개 변수를 사용 하 여 모듈에서 내보내는 함수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-161">Use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="af954-162">**Functionstoexport** 는 내보낸 별칭 목록에서 함수를 제거할 수 있지만 목록에 함수를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-162">**FunctionsToExport** can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="af954-163">-Guid</span><span class="sxs-lookup"><span data-stu-id="af954-163">-Guid</span></span>

<span data-ttu-id="af954-164">모듈의 고유 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-164">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="af954-165">GUID를 사용하여 이름이 같은 모듈을 구별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-165">The GUID can be used to distinguish among modules with the same name.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-166">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="af954-166">-HelpInfoUri</span></span>

<span data-ttu-id="af954-167">모듈의 **HELPINFO XML** 파일의 인터넷 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-167">Specifies the internet address of the module's **HelpInfo XML** file.</span></span> <span data-ttu-id="af954-168">**Http** 또는 **https** 로 시작 하는 URI (Uniform resource Identifier)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-168">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="af954-169">**HELPINFO XML** 파일은 PowerShell 버전 3.0에 도입 된 업데이트할 수 있는 도움말 기능을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-169">The **HelpInfo XML** file supports the Updatable Help feature that was introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="af954-170">모듈의 다운로드 가능한 도움말 파일의 위치 및 지원 되는 각 로캘에 대 한 최신 도움말 파일의 버전 번호에 대 한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-170">It contains information about the location of the module's downloadable help files and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="af954-171">업데이트할 수 있는 도움말에 대 한 자세한 내용은 [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af954-171">For information about Updatable Help, see [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="af954-172">**HELPINFO XML** 파일에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af954-172">For information about the **HelpInfo XML** file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-173">-IconUri</span><span class="sxs-lookup"><span data-stu-id="af954-173">-IconUri</span></span>

<span data-ttu-id="af954-174">모듈에 대 한 아이콘의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-174">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="af954-175">지정 된 아이콘은 모듈에 대 한 갤러리 웹 페이지에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af954-175">The specified icon is displayed on the gallery web page for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-176">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="af954-176">-LicenseUri</span></span>

<span data-ttu-id="af954-177">모듈에 대 한 라이선스 조건의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-177">Specifies the URL of licensing terms for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-178">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="af954-178">-ModuleList</span></span>

<span data-ttu-id="af954-179">모듈에 포함 된 모듈의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-179">Specifies an array of modules that are included in the module.</span></span>

<span data-ttu-id="af954-180">각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-180">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="af954-181">해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-181">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="af954-182">매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-182">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="af954-183">이 키는 모듈 인벤토리 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-183">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="af954-184">이 키의 값에 나열 된 모듈은 자동으로 처리 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-184">The modules that are listed in the value of this key aren't automatically processed.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-185">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="af954-185">-ModuleVersion</span></span>

<span data-ttu-id="af954-186">모듈의 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-186">Specifies the version of the module.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-187">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="af954-187">-NestedModules</span></span>

<span data-ttu-id="af954-188">`.psm1` `.dll` 모듈의 세션 상태로 가져올 스크립트 모듈 () 및 이진 모듈 ()을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-188">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="af954-189">**NestedModules** 키의 파일은 값에 나열 된 순서 대로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af954-189">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="af954-190">각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-190">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="af954-191">해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-191">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="af954-192">매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-192">You can combine strings and hash tables in the parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-193">-PackageManagementProviders</span><span class="sxs-lookup"><span data-stu-id="af954-193">-PackageManagementProviders</span></span>

<span data-ttu-id="af954-194">패키지 관리 공급자의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-194">Specifies an array of package management providers.</span></span>

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

### <span data-ttu-id="af954-195">-PassThru</span><span class="sxs-lookup"><span data-stu-id="af954-195">-PassThru</span></span>

<span data-ttu-id="af954-196">작업 중인 항목을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-196">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="af954-197">기본적으로는 `Update-ModuleManifest` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-197">By default, `Update-ModuleManifest` doesn't generate any output.</span></span>

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

### <span data-ttu-id="af954-198">-Path</span><span class="sxs-lookup"><span data-stu-id="af954-198">-Path</span></span>

<span data-ttu-id="af954-199">모듈 매니페스트의 경로와 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-199">Specifies the path and file name of the module manifest.</span></span> <span data-ttu-id="af954-200">파일 이름 확장명을 사용 하는 경로 및 파일 이름 (예:)을 입력 `.psd1` `$PSHOME\Modules\MyModule\MyModule.psd1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-200">Enter a path and file name with a `.psd1` file name extension, such as `$PSHOME\Modules\MyModule\MyModule.psd1`.</span></span>

<span data-ttu-id="af954-201">기존 파일에 대 한 경로를 지정 하는 경우 `Update-ModuleManifest` 파일에 읽기 전용 특성이 없는 경우는 경고 없이 파일을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="af954-201">If you specify the path to an existing file, `Update-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="af954-202">매니페스트는 모듈 디렉터리에 있어야 하며 매니페스트 파일 이름은 모듈 디렉터리 이름과 동일 해야 하지만 확장명은 동일 해야 합니다 `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="af954-202">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` extension.</span></span>

<span data-ttu-id="af954-203">`$PSHOME` `$HOME` **경로** 매개 변수 값에 대 한 프롬프트에 응답 하 여 또는와 같은 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-203">You can't use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="af954-204">변수를 사용하려면 명령에 **Path** 매개 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-204">To use a variable, include the **Path** parameter in the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="af954-205">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="af954-205">-PowerShellHostName</span></span>

<span data-ttu-id="af954-206">모듈에 필요한 PowerShell 호스트 프로그램의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-206">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="af954-207">호스트 프로그램의 이름 (예: PowerShell ISE Host 또는 ConsoleHost)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-207">Enter the name of the host program, such as PowerShell ISE Host or ConsoleHost.</span></span> <span data-ttu-id="af954-208">와일드 카드는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-208">Wildcards aren't permitted.</span></span>

<span data-ttu-id="af954-209">호스트 프로그램의 이름을 찾으려면 프로그램에서을 입력 `$Host.Name` 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-209">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="af954-210">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="af954-210">-PowerShellHostVersion</span></span>

<span data-ttu-id="af954-211">모듈에서 작동 하는 PowerShell 호스트 프로그램의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-211">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="af954-212">버전 번호를 입력하세요(예: 1.1).</span><span class="sxs-lookup"><span data-stu-id="af954-212">Enter a version number, such as 1.1.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-213">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="af954-213">-PowerShellVersion</span></span>

<span data-ttu-id="af954-214">이 모듈에서 작동 하는 PowerShell의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-214">Specifies the minimum version of PowerShell that will work with this module.</span></span> <span data-ttu-id="af954-215">예를 들어이 매개 변수의 값으로 3.0, 4.0 또는 5.0을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-215">For example, you can specify 3.0, 4.0, or 5.0 as the value of this parameter.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-216">-시험판</span><span class="sxs-lookup"><span data-stu-id="af954-216">-Prerelease</span></span>

<span data-ttu-id="af954-217">모듈이 시험판 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af954-217">Indicates the module is prerelease.</span></span>

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

### <span data-ttu-id="af954-218">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="af954-218">-PrivateData</span></span>

<span data-ttu-id="af954-219">모듈을 가져올 때 모듈에 전달 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-219">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-220">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="af954-220">-ProcessorArchitecture</span></span>

<span data-ttu-id="af954-221">모듈에 필요한 프로세서 아키텍처를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-221">Specifies the processor architecture that the module requires.</span></span>

<span data-ttu-id="af954-222">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="af954-223">Amd64</span><span class="sxs-lookup"><span data-stu-id="af954-223">Amd64</span></span>
- <span data-ttu-id="af954-224">Arm</span><span class="sxs-lookup"><span data-stu-id="af954-224">Arm</span></span>
- <span data-ttu-id="af954-225">IA64</span><span class="sxs-lookup"><span data-stu-id="af954-225">IA64</span></span>
- <span data-ttu-id="af954-226">MSIL</span><span class="sxs-lookup"><span data-stu-id="af954-226">MSIL</span></span>
- <span data-ttu-id="af954-227">없음 (알 수 없음 또는 지정 되지 않음)</span><span class="sxs-lookup"><span data-stu-id="af954-227">None (unknown or unspecified)</span></span>
- <span data-ttu-id="af954-228">X86</span><span class="sxs-lookup"><span data-stu-id="af954-228">X86</span></span>

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-229">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="af954-229">-ProjectUri</span></span>

<span data-ttu-id="af954-230">이 프로젝트에 대 한 웹 페이지의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-230">Specifies the URL of a web page about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-231">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="af954-231">-ReleaseNotes</span></span>

<span data-ttu-id="af954-232">이 버전의 스크립트에 사용할 수 있는 릴리스 정보 또는 설명을 포함 하는 문자열 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-232">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="af954-233">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="af954-233">-RequiredAssemblies</span></span>

<span data-ttu-id="af954-234">`.dll`모듈에 필요한 어셈블리 () 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-234">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="af954-235">어셈블리 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-235">Enter the assembly file names.</span></span>
<span data-ttu-id="af954-236">PowerShell은 형식 또는 형식을 업데이트 하거나, 중첩 모듈을 가져오거나, **RootModule** 키 값에 지정 된 모듈 파일을 가져오기 전에 지정 된 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-236">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="af954-237">이 매개 변수를 사용 하 여 모듈에 필요한 모든 어셈블리를 지정 합니다. 어셈블리를 포함 하 여 **Formatstoprocess** 또는 **TypesToProcess** keys에 나열 된 서식 파일 또는 형식 파일을 업데이트 하기 위해 로드 해야 하는 어셈블리를 포함 하 여 해당 어셈블리가 **NestedModules** 키에 이진 모듈로도 나열 되어 있는 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="af954-237">Use this parameter to specify all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="af954-238">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="af954-238">-RequiredModules</span></span>

<span data-ttu-id="af954-239">전역 세션 상태여야 하는 모듈을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-239">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="af954-240">필수 모듈이 전역 세션 상태가 아닌 경우 PowerShell에서 해당 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="af954-240">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="af954-241">필수 모듈을 사용할 수 없는 경우 `Import-Module` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-241">If the required modules aren't available, the `Import-Module` command fails.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af954-242">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="af954-242">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="af954-243">모듈에 대 한 라이선스 동의가 필요 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-243">Specifies that a license acceptance is required for the module.</span></span>

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

### <span data-ttu-id="af954-244">-RootModule</span><span class="sxs-lookup"><span data-stu-id="af954-244">-RootModule</span></span>

<span data-ttu-id="af954-245">모듈의 기본 또는 루트 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-245">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="af954-246">스크립트 ( `.ps1` ), 스크립트 모듈 ( `.psm1` ), 모듈 매니페스트 ( `.psd1` ), 어셈블리 ( `.dll` ), cmdlet 정의 XML 파일 ( `.cdxml` ) 또는 워크플로 ( `.xaml` )의 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-246">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest (`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="af954-247">모듈을 가져오는 경우 루트 모듈 파일에서 내보낸 멤버를 호출자의 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="af954-247">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="af954-248">모듈에 매니페스트 파일이 있고 **RootModule** 키에 루트 파일이 지정 되지 않은 경우 매니페스트는 모듈의 주 파일이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af954-248">If a module has a manifest file and no root file has been specified in the **RootModule** key, the manifest becomes the primary file for the module.</span></span> <span data-ttu-id="af954-249">그리고 모듈이 매니페스트 모듈이 됩니다 (ModuleType = Manifest).</span><span class="sxs-lookup"><span data-stu-id="af954-249">And, the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="af954-250">`.psm1`매니페스트가 포함 된 모듈의 또는 파일에서 멤버를 내보내려면 `.dll` 해당 파일의 이름을 매니페스트의 **RootModule** 또는 **NestedModules** 키 값에 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-250">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="af954-251">그렇지 않으면 해당 멤버를 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-251">Otherwise, their members aren't exported.</span></span>

<span data-ttu-id="af954-252">PowerShell 2.0에서는이 키를 **ModuleToProcess** 라고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-252">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span>

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

### <span data-ttu-id="af954-253">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="af954-253">-ScriptsToProcess</span></span>

<span data-ttu-id="af954-254">`.ps1`모듈을 가져올 때 호출자의 세션 상태에서 실행 되는 스크립트 () 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-254">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="af954-255">로그인 스크립트를 사용하는 것처럼 이러한 스크립트를 사용하여 환경을 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-255">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="af954-256">모듈의 세션 상태에서 실행되는 스크립트를 지정하려면 **NestedModules** 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-256">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="af954-257">-태그</span><span class="sxs-lookup"><span data-stu-id="af954-257">-Tags</span></span>

<span data-ttu-id="af954-258">태그의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-258">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="af954-259">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="af954-259">-TypesToProcess</span></span>

<span data-ttu-id="af954-260">`.ps1xml`모듈을 가져올 때 실행 되는 형식 파일 ()을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-260">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="af954-261">모듈을 가져올 때 PowerShell에서 지정 된 파일을 사용 하 여 cmdlet을 실행 합니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="af954-261">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="af954-262">형식 파일은 범위가 지정 되지 않기 때문에 세션의 모든 세션 상태에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af954-262">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="af954-263">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="af954-263">-VariablesToExport</span></span>

<span data-ttu-id="af954-264">모듈이 내보내는 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-264">Specifies the variables that the module exports.</span></span> <span data-ttu-id="af954-265">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="af954-265">Wildcards are permitted.</span></span>

<span data-ttu-id="af954-266">이 매개 변수를 사용 하 여 모듈이 내보내는 변수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-266">Use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="af954-267">**VariablesToExport** 는 내보낸 변수 목록에서 변수를 제거할 수 있지만 목록에 변수를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-267">**VariablesToExport** can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="af954-268">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="af954-268">-WhatIf</span></span>

<span data-ttu-id="af954-269">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="af954-269">Shows what would happen if `Update-ModuleManifest` runs.</span></span> <span data-ttu-id="af954-270">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-270">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="af954-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="af954-271">CommonParameters</span></span>

<span data-ttu-id="af954-272">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="af954-272">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="af954-273">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af954-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="af954-274">입력</span><span class="sxs-lookup"><span data-stu-id="af954-274">INPUTS</span></span>

### <span data-ttu-id="af954-275">System.String</span><span class="sxs-lookup"><span data-stu-id="af954-275">System.String</span></span>

## <span data-ttu-id="af954-276">출력</span><span class="sxs-lookup"><span data-stu-id="af954-276">OUTPUTS</span></span>

### <span data-ttu-id="af954-277">System.Object</span><span class="sxs-lookup"><span data-stu-id="af954-277">System.Object</span></span>

## <span data-ttu-id="af954-278">참고</span><span class="sxs-lookup"><span data-stu-id="af954-278">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af954-279">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af954-279">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="af954-280">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af954-280">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="af954-281">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="af954-281">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="af954-282">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af954-282">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="af954-283">관련 링크</span><span class="sxs-lookup"><span data-stu-id="af954-283">RELATED LINKS</span></span>
