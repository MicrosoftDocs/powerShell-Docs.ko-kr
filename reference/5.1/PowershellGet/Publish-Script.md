---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 6593148b493f15feb47af886681032aaf5d009e7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891093"
---
# <span data-ttu-id="d3a27-103">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="d3a27-103">Publish-Script</span></span>

## <span data-ttu-id="d3a27-104">개요</span><span class="sxs-lookup"><span data-stu-id="d3a27-104">SYNOPSIS</span></span>
<span data-ttu-id="d3a27-105">스크립트를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-105">Publishes a script.</span></span>

## <span data-ttu-id="d3a27-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d3a27-106">SYNTAX</span></span>

### <span data-ttu-id="d3a27-107">PathParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="d3a27-107">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d3a27-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="d3a27-108">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d3a27-109">설명</span><span class="sxs-lookup"><span data-stu-id="d3a27-109">DESCRIPTION</span></span>

<span data-ttu-id="d3a27-110">`Publish-Script`Cmdlet은 지정 된 스크립트를 온라인 갤러리에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-110">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="d3a27-111">예제</span><span class="sxs-lookup"><span data-stu-id="d3a27-111">EXAMPLES</span></span>

### <span data-ttu-id="d3a27-112">예제 1: 스크립트 파일 만들기, 콘텐츠를 추가 및 게시</span><span class="sxs-lookup"><span data-stu-id="d3a27-112">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="d3a27-113">`New-ScriptFileInfo`Cmdlet은 이라는 스크립트 파일을 만듭니다 `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="d3a27-113">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="d3a27-114">`Get-Content` 의 내용을 표시 합니다 `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="d3a27-114">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="d3a27-115">`Add-Content`Cmdlet은에 함수와 워크플로를 추가 `Demo-Script.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-115">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

```powershell
$newScriptInfo = @{
  Path = 'D:\ScriptSharingDemo\Demo-Script.ps1'
  Version = '1.0'
  Author = 'author@contoso.com'
  Description = "my test script file description goes here"
}
New-ScriptFileInfo @newScriptInfo
Get-Content -Path $newScriptInfo.Path
```

```Output
<#PSScriptInfo

.VERSION 1.0

.AUTHOR pattif@microsoft.com

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
#>

<#
.DESCRIPTION
 my test script file description goes here
#>
Param()
```

```powershell
Add-Content -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Value @"

Function Demo-ScriptFunction { 'Demo-ScriptFunction' }

Workflow Demo-ScriptWorkflow { 'Demo-ScriptWorkflow' }

Demo-ScriptFunction
Demo-ScriptWorkflow
"@
Test-ScriptFileInfo -Path D:\ScriptSharingDemo\Demo-Script.ps1
```

```Output
Version    Name                 Author                   Description
-------    ----                 ------                   -----------
1.0        Demo-Script          author@contoso.com       my test script file description goes here
```

```powershell
Publish-Script -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Repository LocalRepo1
Find-Script -Repository LocalRepo1 -Name "Demo-Script"
```

```Output
Version    Name                 Type       Repository    Description
-------    ----                 ----       ----------    -----------
1.0        Demo-Script          Script     LocalRepo1    my test script file description goes here
```

<span data-ttu-id="d3a27-116">`Test-ScriptFileInfo`Cmdlet은 유효성을 검사 `Demo-Script.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-116">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="d3a27-117">`Publish-Script`Cmdlet은 **LocalRepo1** 리포지토리에 스크립트를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-117">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="d3a27-118">마지막으로,</span><span class="sxs-lookup"><span data-stu-id="d3a27-118">Finally.</span></span> <span data-ttu-id="d3a27-119">`Find-Script`LocalRepo1 리포지토리에서를 검색 하는 데 사용 됩니다 `Demo-Script.ps1` . </span><span class="sxs-lookup"><span data-stu-id="d3a27-119">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="d3a27-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d3a27-120">PARAMETERS</span></span>

### <span data-ttu-id="d3a27-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="d3a27-121">-Credential</span></span>

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

### <span data-ttu-id="d3a27-122">-Force</span><span class="sxs-lookup"><span data-stu-id="d3a27-122">-Force</span></span>

<span data-ttu-id="d3a27-123">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-123">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d3a27-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d3a27-124">-LiteralPath</span></span>

<span data-ttu-id="d3a27-125">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-125">Specifies a path to one or more locations.</span></span> <span data-ttu-id="d3a27-126">**Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-126">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="d3a27-127">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-127">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="d3a27-128">경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-128">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="d3a27-129">작은따옴표는 Windows PowerShell이 어떤 문자도 이스케이프 시퀀스로 해석하지 않도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-129">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d3a27-130">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="d3a27-130">-NuGetApiKey</span></span>

<span data-ttu-id="d3a27-131">온라인 갤러리에 스크립트를 게시 하는 데 사용할 API 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-131">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="d3a27-132">API 키는 온라인 갤러리에 있는 프로필의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-132">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="d3a27-133">자세한 내용은 [API 키 관리](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3a27-133">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="d3a27-134">-Path</span><span class="sxs-lookup"><span data-stu-id="d3a27-134">-Path</span></span>

<span data-ttu-id="d3a27-135">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-135">Specifies a path to one or more locations.</span></span> <span data-ttu-id="d3a27-136">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-136">Wildcards are permitted.</span></span> <span data-ttu-id="d3a27-137">기본 위치는 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-137">The default location is the current directory.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: Named
Default value: <Current location>
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="d3a27-138">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="d3a27-138">-Repository</span></span>

<span data-ttu-id="d3a27-139">을 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="d3a27-139">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="d3a27-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d3a27-140">-Confirm</span></span>

<span data-ttu-id="d3a27-141">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d3a27-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d3a27-142">-WhatIf</span></span>

<span data-ttu-id="d3a27-143">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d3a27-144">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d3a27-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d3a27-145">CommonParameters</span></span>

<span data-ttu-id="d3a27-146">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d3a27-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d3a27-147">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3a27-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d3a27-148">입력</span><span class="sxs-lookup"><span data-stu-id="d3a27-148">INPUTS</span></span>

### <span data-ttu-id="d3a27-149">System.String</span><span class="sxs-lookup"><span data-stu-id="d3a27-149">System.String</span></span>

### <span data-ttu-id="d3a27-150">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="d3a27-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="d3a27-151">출력</span><span class="sxs-lookup"><span data-stu-id="d3a27-151">OUTPUTS</span></span>

### <span data-ttu-id="d3a27-152">System.Object</span><span class="sxs-lookup"><span data-stu-id="d3a27-152">System.Object</span></span>

## <span data-ttu-id="d3a27-153">참고</span><span class="sxs-lookup"><span data-stu-id="d3a27-153">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3a27-154">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-154">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d3a27-155">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-155">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d3a27-156">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a27-156">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d3a27-157">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3a27-157">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d3a27-158">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d3a27-158">RELATED LINKS</span></span>

[<span data-ttu-id="d3a27-159">Find-Script</span><span class="sxs-lookup"><span data-stu-id="d3a27-159">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="d3a27-160">Install-Script</span><span class="sxs-lookup"><span data-stu-id="d3a27-160">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="d3a27-161">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="d3a27-161">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="d3a27-162">Save-Script</span><span class="sxs-lookup"><span data-stu-id="d3a27-162">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="d3a27-163">Update-Script</span><span class="sxs-lookup"><span data-stu-id="d3a27-163">Update-Script</span></span>](Update-Script.md)
