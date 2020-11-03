---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/new-scriptfileinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScriptFileInfo
ms.openlocfilehash: f416447c2c13d3dbf2d14ed5ca045164779fcbe0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211105"
---
# <span data-ttu-id="ad0e9-103">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="ad0e9-103">New-ScriptFileInfo</span></span>

## <span data-ttu-id="ad0e9-104">개요</span><span class="sxs-lookup"><span data-stu-id="ad0e9-104">SYNOPSIS</span></span>
<span data-ttu-id="ad0e9-105">메타데이터를 사용하여 스크립트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-105">Creates a script file with metadata.</span></span>

## <span data-ttu-id="ad0e9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ad0e9-106">SYNTAX</span></span>

### <span data-ttu-id="ad0e9-107">모두</span><span class="sxs-lookup"><span data-stu-id="ad0e9-107">All</span></span>

```
New-ScriptFileInfo [[-Path] <String>] [-Version <String>] [-Author <String>] -Description <String>
 [-Guid <Guid>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ad0e9-108">설명</span><span class="sxs-lookup"><span data-stu-id="ad0e9-108">DESCRIPTION</span></span>

<span data-ttu-id="ad0e9-109">`New-ScriptFileInfo`Cmdlet은 스크립트에 대 한 메타 데이터를 포함 하 여 PowerShell 스크립트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-109">The `New-ScriptFileInfo` cmdlet creates a PowerShell script file, including metadata about the script.</span></span>

<span data-ttu-id="ad0e9-110">이 예에서는 스 플랫를 사용 하 여 cmdlet에 매개 변수를 전달 `New-ScriptFileInfo` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-110">The examples use splatting to pass parameters to the `New-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="ad0e9-111">자세한 내용은 [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-111">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

## <span data-ttu-id="ad0e9-112">예제</span><span class="sxs-lookup"><span data-stu-id="ad0e9-112">EXAMPLES</span></span>

### <span data-ttu-id="ad0e9-113">예 1: 스크립트 파일을 만들고 해당 버전, 작성자 및 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-113">Example 1: Create a script file and specify its version, author, and description</span></span>

<span data-ttu-id="ad0e9-114">이 예제에서는 스크립트 파일이 만들어지고 해당 내용이 PowerShell 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-114">In this example, a script file is created and its contents are displayed in the PowerShell console.</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "1.0"
  Author = "pattif@contoso.com"
  Description = "My test script file description goes here"
  }
New-ScriptFileInfo @Parms
Get-Content -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
<#PSScriptInfo

.VERSION 1.0

.GUID 3bb10ee7-38c1-41b9-88ea-16899164fc19

.AUTHOR pattif@contoso.com

.COMPANYNAME

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
 My test script file description goes here

#>
Param()
```

<span data-ttu-id="ad0e9-115">`New-ScriptFileInfo`Cmdlet은 스 플랫를 사용 하 여 스크립트에 대 한 몇 가지 매개 변수를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-115">The `New-ScriptFileInfo` cmdlet uses splatting to configure several parameters for the script.</span></span>
<span data-ttu-id="ad0e9-116">**Path** 스크립트의 위치와 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-116">**Path** sets the location and name of the script.</span></span> <span data-ttu-id="ad0e9-117">**버전** 은 스크립트의 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-117">**Version** specifies the script's version number.</span></span> <span data-ttu-id="ad0e9-118">**Author** 는 스크립트를 만든 사람의 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-118">**Author** is the email address of the person who created the script.</span></span> <span data-ttu-id="ad0e9-119">**설명** 스크립트의 용도를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-119">**Description** explains the script's purpose.</span></span>

<span data-ttu-id="ad0e9-120">스크립트를 만든 후에는 `Get-Content` **Path** 매개 변수를 사용 하 여 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-120">After the script is created, `Get-Content` uses the **Path** parameter to locate the script.</span></span> <span data-ttu-id="ad0e9-121">스크립트의 내용이 PowerShell 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-121">The script's contents are displayed in the PowerShell console.</span></span>

### <span data-ttu-id="ad0e9-122">예제 2: 스크립트 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="ad0e9-122">Example 2: Test a script file</span></span>

<span data-ttu-id="ad0e9-123">이 예에서는 **예 1** 에서 만든 스크립트에 대 한 메타 데이터가 테스트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-123">In this example, the metadata for the script created in **Example 1** is tested.</span></span>

```powershell
Test-ScriptFileInfo -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
Version   Name                  Author               Description
-------   ----                  ------               -----------
1.0       Temp-Scriptfile       pattif@contoso.com   My test script file description goes here
```

<span data-ttu-id="ad0e9-124">`Test-ScriptFileInfo`Cmdlet은 **Path** 매개 변수를 사용 하 여 스크립트 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-124">The `Test-ScriptFileInfo` cmdlet uses the **Path** parameter to specify the script file's location.</span></span>

### <span data-ttu-id="ad0e9-125">예제 3: 모든 메타 데이터 속성을 포함 하는 스크립트 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="ad0e9-125">Example 3: Create a script file with all the metadata properties</span></span>

<span data-ttu-id="ad0e9-126">이 예제에서는 스 플랫를 사용 하 여 `New-ScriptFile.ps1` 모든 메타 데이터 속성을 포함 하는 이라는 스크립트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-126">This example uses splatting to create a script file named `New-ScriptFile.ps1` that includes all its metadata properties.</span></span> <span data-ttu-id="ad0e9-127">**Verbose** 매개 변수는 스크립트가 생성 될 때 자세한 정보 표시 출력을 표시 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-127">The **Verbose** parameter specifies that verbose output is displayed as the script is created.</span></span>

```powershell
$Parms = @{
 Path = "C:\Test\New-ScriptFile.ps1"
 Verbose = $True
 Version = "1.0"
 Author = "pattif@contoso.com"
 Description = "My new script file test"
 CompanyName = "Contoso Corporation"
 Copyright = "2019 Contoso Corporation. All rights reserved."
 ExternalModuleDependencies = "ff","bb"
 RequiredScripts = "Start-WFContosoServer", "Stop-ContosoServerScript"
 ExternalScriptDependencies = "Stop-ContosoServerScript"
 Tags = @("Tag1", "Tag2", "Tag3")
 ProjectUri = "https://contoso.com"
 LicenseUri = "https://contoso.com/License"
 IconUri = "https://contoso.com/Icon"
 PassThru = $True
 ReleaseNotes = @("Contoso script now supports the following features:",
   "Feature 1",
   "Feature 2",
   "Feature 3",
   "Feature 4",
   "Feature 5")
 RequiredModules =
   "1",
   "2",
   "RequiredModule1",
   @{ModuleName="RequiredModule2";ModuleVersion="1.0"},
   @{ModuleName="RequiredModule3";RequiredVersion="2.0"},
   "ExternalModule1"
 }
New-ScriptFileInfo @Parms
```

```Output
VERBOSE: Performing the operation "Creating the 'C:\Test\New-ScriptFile.ps1'
  PowerShell Script file" on target "C:\Test\New-ScriptFile.ps1".

<#PSScriptInfo

.VERSION 1.0

.GUID 4fabe8c7-7862-45b1-a72e-1352a433b77d

.AUTHOR pattif@contoso.com

.COMPANYNAME Contoso Corporation

.COPYRIGHT 2019 Contoso Corporation. All rights reserved.

.TAGS Tag1 Tag2 Tag3

.LICENSEURI https://contoso.com/License

.PROJECTURI https://contoso.com/

.ICONURI https://contoso.com/Icon

.EXTERNALMODULEDEPENDENCIES ff,bb

.REQUIREDSCRIPTS Start-WFContosoServer,Stop-ContosoServerScript

.EXTERNALSCRIPTDEPENDENCIES Stop-ContosoServerScript

.RELEASENOTES
Contoso script now supports the following features:
Feature 1
Feature 2
Feature 3
Feature 4
Feature 5

.PRIVATEDATA

#>

#Requires -Module 1
#Requires -Module 2
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.0'}
#Requires -Module @{RequiredVersion = '2.0'; ModuleName = 'RequiredModule3'}
#Requires -Module ExternalModule1

<#

.DESCRIPTION
 My new script file test

#>
Param()
```

## <span data-ttu-id="ad0e9-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ad0e9-128">PARAMETERS</span></span>

### <span data-ttu-id="ad0e9-129">-작성자</span><span class="sxs-lookup"><span data-stu-id="ad0e9-129">-Author</span></span>

<span data-ttu-id="ad0e9-130">스크립트 작성자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-130">Specifies the script author.</span></span>

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

### <span data-ttu-id="ad0e9-131">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="ad0e9-131">-CompanyName</span></span>

<span data-ttu-id="ad0e9-132">스크립트를 만든 회사나 공급 업체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-132">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="ad0e9-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ad0e9-133">-Confirm</span></span>

<span data-ttu-id="ad0e9-134">을 실행 하기 전에 확인 메시지를 표시 `New-ScriptFileInfo` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-134">Prompts you for confirmation before running the `New-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="ad0e9-135">-저작권</span><span class="sxs-lookup"><span data-stu-id="ad0e9-135">-Copyright</span></span>

<span data-ttu-id="ad0e9-136">스크립트에 대 한 저작권 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-136">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="ad0e9-137">-Description</span><span class="sxs-lookup"><span data-stu-id="ad0e9-137">-Description</span></span>

<span data-ttu-id="ad0e9-138">스크립트에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-138">Specifies a description for the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad0e9-139">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="ad0e9-139">-ExternalModuleDependencies</span></span>

<span data-ttu-id="ad0e9-140">외부 모듈 종속성의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-140">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="ad0e9-141">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="ad0e9-141">-ExternalScriptDependencies</span></span>

<span data-ttu-id="ad0e9-142">외부 스크립트 종속성의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-142">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="ad0e9-143">-Force</span><span class="sxs-lookup"><span data-stu-id="ad0e9-143">-Force</span></span>

<span data-ttu-id="ad0e9-144">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-144">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ad0e9-145">-Guid</span><span class="sxs-lookup"><span data-stu-id="ad0e9-145">-Guid</span></span>

<span data-ttu-id="ad0e9-146">스크립트에 대 한 고유 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-146">Specifies a unique ID for the script.</span></span>

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

### <span data-ttu-id="ad0e9-147">-IconUri</span><span class="sxs-lookup"><span data-stu-id="ad0e9-147">-IconUri</span></span>

<span data-ttu-id="ad0e9-148">스크립트에 대 한 아이콘의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-148">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="ad0e9-149">지정 된 아이콘이 스크립트의 갤러리 웹 페이지에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-149">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="ad0e9-150">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="ad0e9-150">-LicenseUri</span></span>

<span data-ttu-id="ad0e9-151">라이선스 조건의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-151">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="ad0e9-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ad0e9-152">-PassThru</span></span>

<span data-ttu-id="ad0e9-153">작업 중인 항목을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-153">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="ad0e9-154">기본적으로는 `New-ScriptFileInfo` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-154">By default, `New-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="ad0e9-155">-Path</span><span class="sxs-lookup"><span data-stu-id="ad0e9-155">-Path</span></span>

<span data-ttu-id="ad0e9-156">스크립트 파일이 저장 되는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-156">Specifies the location where the script file is saved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ad0e9-157">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="ad0e9-157">-PrivateData</span></span>

<span data-ttu-id="ad0e9-158">스크립트에 대 한 개인 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-158">Specifies private data for the script.</span></span>

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

### <span data-ttu-id="ad0e9-159">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="ad0e9-159">-ProjectUri</span></span>

<span data-ttu-id="ad0e9-160">이 프로젝트에 대 한 웹 페이지의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-160">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="ad0e9-161">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="ad0e9-161">-ReleaseNotes</span></span>

<span data-ttu-id="ad0e9-162">이 버전의 스크립트 사용자가 사용할 수 있도록 하려는 릴리스 정보 또는 설명을 포함 하는 문자열 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-162">Specifies a string array that contains release notes or comments that you want available to users of this version of the script.</span></span>

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

### <span data-ttu-id="ad0e9-163">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="ad0e9-163">-RequiredModules</span></span>

<span data-ttu-id="ad0e9-164">전역 세션 상태여야 하는 모듈을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-164">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="ad0e9-165">필수 모듈이 전역 세션 상태가 아닌 경우 PowerShell에서 해당 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-165">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="ad0e9-166">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="ad0e9-166">-RequiredScripts</span></span>

<span data-ttu-id="ad0e9-167">필수 스크립트의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-167">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="ad0e9-168">-태그</span><span class="sxs-lookup"><span data-stu-id="ad0e9-168">-Tags</span></span>

<span data-ttu-id="ad0e9-169">태그의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-169">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="ad0e9-170">-Version</span><span class="sxs-lookup"><span data-stu-id="ad0e9-170">-Version</span></span>

<span data-ttu-id="ad0e9-171">스크립트의 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-171">Specifies the version of the script.</span></span>

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

### <span data-ttu-id="ad0e9-172">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ad0e9-172">-WhatIf</span></span>

<span data-ttu-id="ad0e9-173">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `New-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="ad0e9-173">Shows what would happen if `New-ScriptFileInfo` runs.</span></span> <span data-ttu-id="ad0e9-174">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-174">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ad0e9-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ad0e9-175">CommonParameters</span></span>

<span data-ttu-id="ad0e9-176">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ad0e9-177">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad0e9-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ad0e9-178">입력</span><span class="sxs-lookup"><span data-stu-id="ad0e9-178">INPUTS</span></span>

### <span data-ttu-id="ad0e9-179">System.String</span><span class="sxs-lookup"><span data-stu-id="ad0e9-179">System.String</span></span>

## <span data-ttu-id="ad0e9-180">출력</span><span class="sxs-lookup"><span data-stu-id="ad0e9-180">OUTPUTS</span></span>

### <span data-ttu-id="ad0e9-181">System.Object</span><span class="sxs-lookup"><span data-stu-id="ad0e9-181">System.Object</span></span>

## <span data-ttu-id="ad0e9-182">참고</span><span class="sxs-lookup"><span data-stu-id="ad0e9-182">NOTES</span></span>

## <span data-ttu-id="ad0e9-183">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ad0e9-183">RELATED LINKS</span></span>

[<span data-ttu-id="ad0e9-184">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="ad0e9-184">about_Splatting</span></span>](../Microsoft.Powershell.Core/About/about_splatting.md)

[<span data-ttu-id="ad0e9-185">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="ad0e9-185">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="ad0e9-186">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="ad0e9-186">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
