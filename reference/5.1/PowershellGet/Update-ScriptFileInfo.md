---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: bb36d5a1acc8331762513219e823bf91304b6b45
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215162"
---
# <span data-ttu-id="00cef-103">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="00cef-103">Update-ScriptFileInfo</span></span>

## <span data-ttu-id="00cef-104">개요</span><span class="sxs-lookup"><span data-stu-id="00cef-104">SYNOPSIS</span></span>
<span data-ttu-id="00cef-105">스크립트에 대 한 정보를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-105">Updates information for a script.</span></span>

## <span data-ttu-id="00cef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="00cef-106">SYNTAX</span></span>

### <span data-ttu-id="00cef-107">PathParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="00cef-107">PathParameterSet (Default)</span></span>

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="00cef-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="00cef-108">LiteralPathParameterSet</span></span>

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="00cef-109">설명</span><span class="sxs-lookup"><span data-stu-id="00cef-109">DESCRIPTION</span></span>

<span data-ttu-id="00cef-110">`Update-ScriptFileInfo`Cmdlet은 스크립트의 속성 값을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-110">The `Update-ScriptFileInfo` cmdlet updates a script's property values.</span></span> <span data-ttu-id="00cef-111">예를 들어 버전, 작성자 또는 설명의 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-111">For example, the values for version, author, or description.</span></span>

## <span data-ttu-id="00cef-112">예제</span><span class="sxs-lookup"><span data-stu-id="00cef-112">EXAMPLES</span></span>

### <span data-ttu-id="00cef-113">예제 1: 스크립트 파일의 버전 업데이트</span><span class="sxs-lookup"><span data-stu-id="00cef-113">Example 1: Update the version of a script file</span></span>

<span data-ttu-id="00cef-114">이 예에서는 기존 스크립트 파일을 새 속성 값으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-114">In this example, an existing script file is updated with new property values.</span></span>

<span data-ttu-id="00cef-115">스 플랫는 cmdlet에 매개 변수를 전달 하는 데 사용 됩니다 `Update-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="00cef-115">Splatting is used to pass parameters to the `Update-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="00cef-116">자세한 내용은 [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="00cef-116">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "2.0"
  Author = "bob@contoso.com"
  CompanyName = "Contoso"
  Description = "This is the updated description"
  }
Update-ScriptFileInfo @Parms -PassThru
```

```Output
<#PSScriptInfo

.VERSION 2.0

.GUID 4609f00c-e850-4d3f-9c69-3741e56e4133

.AUTHOR bob@contoso.com

.COMPANYNAME Contoso

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

.PRIVATEDATA

#>

<#

.DESCRIPTION
This is the updated description

#>
Param()
```

<span data-ttu-id="00cef-117">`$Parms`**경로** , **버전** , **작성자** , **CompanyName** 및 **설명** 에 대 한 매개 변수 값을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-117">`$Parms` stores the parameter values for **Path** , **Version** , **Author** , **CompanyName** , and **Description** .</span></span> <span data-ttu-id="00cef-118">`Update-ScriptFileInfo` 에서 매개 변수 값을 가져오고 `@Parms` 스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-118">`Update-ScriptFileInfo` gets the parameter values from `@Parms` and updates the script.</span></span> <span data-ttu-id="00cef-119">**PassThru** 매개 변수는 PowerShell 콘솔에 스크립트의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-119">The **PassThru** parameter displays the script's contents in the PowerShell console.</span></span>

## <span data-ttu-id="00cef-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="00cef-120">PARAMETERS</span></span>

### <span data-ttu-id="00cef-121">-작성자</span><span class="sxs-lookup"><span data-stu-id="00cef-121">-Author</span></span>

<span data-ttu-id="00cef-122">스크립트 작성자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-122">Specifies the script author.</span></span>

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

### <span data-ttu-id="00cef-123">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="00cef-123">-CompanyName</span></span>

<span data-ttu-id="00cef-124">스크립트를 만든 회사나 공급 업체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-124">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="00cef-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="00cef-125">-Confirm</span></span>

<span data-ttu-id="00cef-126">실행 하기 전에 확인 메시지를 표시 `Update-ScriptFileInfo` 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-126">Prompts you for confirmation before running `Update-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="00cef-127">-저작권</span><span class="sxs-lookup"><span data-stu-id="00cef-127">-Copyright</span></span>

<span data-ttu-id="00cef-128">스크립트에 대 한 저작권 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-128">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="00cef-129">-Description</span><span class="sxs-lookup"><span data-stu-id="00cef-129">-Description</span></span>

<span data-ttu-id="00cef-130">스크립트에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-130">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="00cef-131">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="00cef-131">-ExternalModuleDependencies</span></span>

<span data-ttu-id="00cef-132">외부 모듈 종속성의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-132">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="00cef-133">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="00cef-133">-ExternalScriptDependencies</span></span>

<span data-ttu-id="00cef-134">외부 스크립트 종속성의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-134">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="00cef-135">-Force</span><span class="sxs-lookup"><span data-stu-id="00cef-135">-Force</span></span>

<span data-ttu-id="00cef-136">`Update-ScriptFileInfo`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-136">Forces `Update-ScriptFileInfo` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="00cef-137">-Guid</span><span class="sxs-lookup"><span data-stu-id="00cef-137">-Guid</span></span>

<span data-ttu-id="00cef-138">스크립트에 대 한 고유 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-138">Specifies a unique ID for a script.</span></span>

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

### <span data-ttu-id="00cef-139">-IconUri</span><span class="sxs-lookup"><span data-stu-id="00cef-139">-IconUri</span></span>

<span data-ttu-id="00cef-140">스크립트에 대 한 아이콘의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-140">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="00cef-141">지정 된 아이콘이 스크립트의 갤러리 웹 페이지에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-141">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="00cef-142">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="00cef-142">-LicenseUri</span></span>

<span data-ttu-id="00cef-143">라이선스 조건의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-143">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="00cef-144">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="00cef-144">-LiteralPath</span></span>

<span data-ttu-id="00cef-145">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-145">Specifies a path to one or more locations.</span></span> <span data-ttu-id="00cef-146">**LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-146">The **LiteralPath** parameter's value is used exactly as it's entered.</span></span> <span data-ttu-id="00cef-147">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-147">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="00cef-148">경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-148">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="00cef-149">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-149">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="00cef-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="00cef-150">-PassThru</span></span>

<span data-ttu-id="00cef-151">작업 중인 항목을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-151">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="00cef-152">기본적으로는 `Update-ScriptFileInfo` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-152">By default, `Update-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="00cef-153">-Path</span><span class="sxs-lookup"><span data-stu-id="00cef-153">-Path</span></span>

<span data-ttu-id="00cef-154">스크립트 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-154">Specifies the script file's location.</span></span> <span data-ttu-id="00cef-155">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-155">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="00cef-156">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="00cef-156">-PrivateData</span></span>

<span data-ttu-id="00cef-157">스크립트에 대 한 개인 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-157">Specifies the private data for the script.</span></span>

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

### <span data-ttu-id="00cef-158">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="00cef-158">-ProjectUri</span></span>

<span data-ttu-id="00cef-159">이 프로젝트에 대 한 웹 페이지의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-159">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="00cef-160">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="00cef-160">-ReleaseNotes</span></span>

<span data-ttu-id="00cef-161">이 버전의 스크립트에 사용할 수 있는 릴리스 정보 또는 설명을 포함 하는 문자열 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-161">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="00cef-162">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="00cef-162">-RequiredModules</span></span>

<span data-ttu-id="00cef-163">전역 세션 상태여야 하는 모듈을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-163">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="00cef-164">필수 모듈이 전역 세션 상태가 아닌 경우 PowerShell에서 해당 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-164">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="00cef-165">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="00cef-165">-RequiredScripts</span></span>

<span data-ttu-id="00cef-166">필수 스크립트의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-166">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="00cef-167">-태그</span><span class="sxs-lookup"><span data-stu-id="00cef-167">-Tags</span></span>

<span data-ttu-id="00cef-168">태그의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-168">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="00cef-169">-Version</span><span class="sxs-lookup"><span data-stu-id="00cef-169">-Version</span></span>

<span data-ttu-id="00cef-170">스크립트의 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-170">Specifies the script's version.</span></span>

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

### <span data-ttu-id="00cef-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="00cef-171">-WhatIf</span></span>

<span data-ttu-id="00cef-172">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Update-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="00cef-172">Shows what would happen if `Update-ScriptFileInfo` runs.</span></span> <span data-ttu-id="00cef-173">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-173">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="00cef-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="00cef-174">CommonParameters</span></span>

<span data-ttu-id="00cef-175">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="00cef-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="00cef-176">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00cef-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="00cef-177">입력</span><span class="sxs-lookup"><span data-stu-id="00cef-177">INPUTS</span></span>

## <span data-ttu-id="00cef-178">출력</span><span class="sxs-lookup"><span data-stu-id="00cef-178">OUTPUTS</span></span>

## <span data-ttu-id="00cef-179">참고</span><span class="sxs-lookup"><span data-stu-id="00cef-179">NOTES</span></span>

<span data-ttu-id="00cef-180">Cmdlet을 사용 `Test-ScriptFileInfo` 하 여 스크립트 메타 데이터의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-180">Use the `Test-ScriptFileInfo` cmdlet to validate a script's metadata.</span></span> <span data-ttu-id="00cef-181">스크립트에는 버전, GUID, 설명 및 만든이에 대 한 값이 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00cef-181">Scripts must include values for version, GUID, description, and author.</span></span>

## <span data-ttu-id="00cef-182">관련 링크</span><span class="sxs-lookup"><span data-stu-id="00cef-182">RELATED LINKS</span></span>

[<span data-ttu-id="00cef-183">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="00cef-183">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="00cef-184">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="00cef-184">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
