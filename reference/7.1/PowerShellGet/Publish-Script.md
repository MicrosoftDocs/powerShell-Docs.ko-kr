---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 1c333494525ed697ad04f6b500cabfb5964ec9eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217546"
---
# <span data-ttu-id="962cd-103">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="962cd-103">Publish-Script</span></span>

## <span data-ttu-id="962cd-104">개요</span><span class="sxs-lookup"><span data-stu-id="962cd-104">SYNOPSIS</span></span>
<span data-ttu-id="962cd-105">스크립트를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-105">Publishes a script.</span></span>

## <span data-ttu-id="962cd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="962cd-106">SYNTAX</span></span>

### <span data-ttu-id="962cd-107">PathParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="962cd-107">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="962cd-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="962cd-108">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="962cd-109">설명</span><span class="sxs-lookup"><span data-stu-id="962cd-109">DESCRIPTION</span></span>

<span data-ttu-id="962cd-110">`Publish-Script`Cmdlet은 지정 된 스크립트를 온라인 갤러리에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-110">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="962cd-111">예제</span><span class="sxs-lookup"><span data-stu-id="962cd-111">EXAMPLES</span></span>

### <span data-ttu-id="962cd-112">예제 1: 스크립트 파일 만들기, 콘텐츠를 추가 및 게시</span><span class="sxs-lookup"><span data-stu-id="962cd-112">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="962cd-113">`New-ScriptFileInfo`Cmdlet은 이라는 스크립트 파일을 만듭니다 `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="962cd-113">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="962cd-114">`Get-Content` 의 내용을 표시 합니다 `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="962cd-114">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="962cd-115">`Add-Content`Cmdlet은에 함수와 워크플로를 추가 `Demo-Script.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-115">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

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

<span data-ttu-id="962cd-116">`Test-ScriptFileInfo`Cmdlet은 유효성을 검사 `Demo-Script.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-116">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="962cd-117">`Publish-Script`Cmdlet은 **LocalRepo1** 리포지토리에 스크립트를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-117">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="962cd-118">마지막으로,</span><span class="sxs-lookup"><span data-stu-id="962cd-118">Finally.</span></span> <span data-ttu-id="962cd-119">`Find-Script`LocalRepo1 리포지토리에서를 검색 하는 데 사용 됩니다 `Demo-Script.ps1` . **LocalRepo1**</span><span class="sxs-lookup"><span data-stu-id="962cd-119">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="962cd-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="962cd-120">PARAMETERS</span></span>

### <span data-ttu-id="962cd-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="962cd-121">-Confirm</span></span>

<span data-ttu-id="962cd-122">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="962cd-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="962cd-123">-Credential</span></span>

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

### <span data-ttu-id="962cd-124">-Force</span><span class="sxs-lookup"><span data-stu-id="962cd-124">-Force</span></span>

<span data-ttu-id="962cd-125">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="962cd-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="962cd-126">-LiteralPath</span></span>

<span data-ttu-id="962cd-127">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-127">Specifies a path to one or more locations.</span></span> <span data-ttu-id="962cd-128">**Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-128">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="962cd-129">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-129">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="962cd-130">경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-130">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="962cd-131">작은따옴표는 Windows PowerShell이 어떤 문자도 이스케이프 시퀀스로 해석하지 않도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-131">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="962cd-132">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="962cd-132">-NuGetApiKey</span></span>

<span data-ttu-id="962cd-133">온라인 갤러리에 스크립트를 게시 하는 데 사용할 API 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-133">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="962cd-134">API 키는 온라인 갤러리에 있는 프로필의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-134">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="962cd-135">자세한 내용은 [API 키 관리](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="962cd-135">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="962cd-136">-Path</span><span class="sxs-lookup"><span data-stu-id="962cd-136">-Path</span></span>

<span data-ttu-id="962cd-137">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-137">Specifies a path to one or more locations.</span></span> <span data-ttu-id="962cd-138">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-138">Wildcards are permitted.</span></span> <span data-ttu-id="962cd-139">기본 위치는 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-139">The default location is the current directory.</span></span>

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

### <span data-ttu-id="962cd-140">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="962cd-140">-Repository</span></span>

<span data-ttu-id="962cd-141">을 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="962cd-141">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="962cd-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="962cd-142">-WhatIf</span></span>

<span data-ttu-id="962cd-143">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="962cd-144">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="962cd-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="962cd-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="962cd-145">CommonParameters</span></span>

<span data-ttu-id="962cd-146">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="962cd-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="962cd-147">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="962cd-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="962cd-148">입력</span><span class="sxs-lookup"><span data-stu-id="962cd-148">INPUTS</span></span>

### <span data-ttu-id="962cd-149">System.String</span><span class="sxs-lookup"><span data-stu-id="962cd-149">System.String</span></span>

### <span data-ttu-id="962cd-150">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="962cd-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="962cd-151">출력</span><span class="sxs-lookup"><span data-stu-id="962cd-151">OUTPUTS</span></span>

### <span data-ttu-id="962cd-152">System.Object</span><span class="sxs-lookup"><span data-stu-id="962cd-152">System.Object</span></span>

## <span data-ttu-id="962cd-153">참고</span><span class="sxs-lookup"><span data-stu-id="962cd-153">NOTES</span></span>

## <span data-ttu-id="962cd-154">관련 링크</span><span class="sxs-lookup"><span data-stu-id="962cd-154">RELATED LINKS</span></span>

[<span data-ttu-id="962cd-155">Find-Script</span><span class="sxs-lookup"><span data-stu-id="962cd-155">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="962cd-156">Install-Script</span><span class="sxs-lookup"><span data-stu-id="962cd-156">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="962cd-157">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="962cd-157">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="962cd-158">Save-Script</span><span class="sxs-lookup"><span data-stu-id="962cd-158">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="962cd-159">Update-Script</span><span class="sxs-lookup"><span data-stu-id="962cd-159">Update-Script</span></span>](Update-Script.md)

