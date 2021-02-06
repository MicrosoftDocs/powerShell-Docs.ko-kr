---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/test-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ScriptFileInfo
ms.openlocfilehash: 35de1c9b7c975a68ac2f5a01c97a78eeef6d1184
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603260"
---
# <span data-ttu-id="752a1-102">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="752a1-102">Test-ScriptFileInfo</span></span>

## <span data-ttu-id="752a1-103">개요</span><span class="sxs-lookup"><span data-stu-id="752a1-103">SYNOPSIS</span></span>
<span data-ttu-id="752a1-104">스크립트에 대 한 주석 블록의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-104">Validates a comment block for a script.</span></span>

## <span data-ttu-id="752a1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="752a1-105">SYNTAX</span></span>

### <span data-ttu-id="752a1-106">PathParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="752a1-106">PathParameterSet (Default)</span></span>

```
Test-ScriptFileInfo [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="752a1-107">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="752a1-107">LiteralPathParameterSet</span></span>

```
Test-ScriptFileInfo -LiteralPath <String> [<CommonParameters>]
```

## <span data-ttu-id="752a1-108">설명</span><span class="sxs-lookup"><span data-stu-id="752a1-108">DESCRIPTION</span></span>

<span data-ttu-id="752a1-109">**New-scriptfileinfo** cmdlet은 Publish-Script cmdlet을 사용 하 여 게시 될 스크립트의 시작 부분에 있는 주석 블록의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-109">The **Test-ScriptFileInfo** cmdlet validates the comment block at the beginning of a script that will be published with the Publish-Script cmdlet.</span></span>
<span data-ttu-id="752a1-110">주석 블록에 오류가 있는 경우이 cmdlet은 오류가 발생 한 위치 또는 수정 방법에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-110">If the comment block has an error, this cmdlet returns information about where the error is located or how to correct it.</span></span>

## <span data-ttu-id="752a1-111">예제</span><span class="sxs-lookup"><span data-stu-id="752a1-111">EXAMPLES</span></span>

### <span data-ttu-id="752a1-112">예제 1: 스크립트 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="752a1-112">Example 1: Test a script file</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "C:\temp\temp_scripts\New-ScriptFile.ps1"
Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        New-ScriptFile            pattif               my new script file test
```

<span data-ttu-id="752a1-113">이 명령은 New-ScriptFile.ps1 스크립트 파일을 테스트 하 고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-113">This command tests the New-ScriptFile.ps1 script file and displays the results.</span></span>
<span data-ttu-id="752a1-114">스크립트 파일에 유효한 메타 데이터가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-114">The script file includes valid metadata.</span></span>

### <span data-ttu-id="752a1-115">예제 2: 모든 메타 데이터 속성에 대 한 값이 있는 스크립트 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="752a1-115">Example 2: Test a script file that has values for all metadata properties</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Test-Runbook.ps1" | Format-List *
Name                       : Test-Runbook
Path                       : D:\code\Test-Runbook.ps1
ScriptBase                 : D:\code
ReleaseNotes               : {contoso script now supports following features, Feature 1, Feature 2, Feature 3...}
Version                    : 1.0
Guid                       : eb246b19-17da-4392-8c89-7c280f69ad0e
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
Tags                       : {Tag1, Tag2, Tag3}
LicenseUri                 : https://contoso.com/License
ProjectUri                 : https://contoso.com/
IconUri                    : https://contoso.com/MyScriptIcon
ExternalModuleDependencies : ExternalModule1
RequiredScripts            : {Start-WFContosoServer, Stop-ContosoServerScript}
ExternalScriptDependencies : Stop-ContosoServerScript
Description                : Contoso Script example
RequiredModules            : {RequiredModule1, @{ ModuleName = 'RequiredModule2'; ModuleVersion = '1.0' }, @{ ModuleName = 'RequiredModule3'; RequiredVersion = '2.0' }, ExternalModule1}
ExportedCommands           : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-Workflow...}
ExportedFunctions          : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-AdvPSCmdlet}
ExportedWorkflows          : My-Workflow
```

<span data-ttu-id="752a1-116">이 명령은 Test-Runbook.ps1 스크립트 파일을 테스트 하 고 파이프라인 연산자를 사용 하 여 결과를 Format-List cmdlet에 전달 하 여 결과의 서식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-116">This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.</span></span>

### <span data-ttu-id="752a1-117">예제 3: 메타 데이터가 없는 스크립트 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="752a1-117">Example 3: Test a script file that has no metadata</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Hello-World.ps1"
Test-ScriptFileInfo : Script 'D:\code\Hello-World.ps1' is missing required metadata properties. Verify that the script file has Version, Description
and Author properties. You can use the Update-ScriptFileInfo or New-ScriptFileInfo cmdlet to add or update the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo D:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidArgument: (D:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException

+ FullyQualifiedErrorId : MissingRequiredPSScriptInfoProperties,Test-ScriptFile
```

<span data-ttu-id="752a1-118">이 명령은 연결 된 메타 데이터가 없는 Hello-World.ps1 스크립트 파일을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-118">This command tests the script file Hello-World.ps1, which has no metadata associated with it.</span></span>

## <span data-ttu-id="752a1-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="752a1-119">PARAMETERS</span></span>

### <span data-ttu-id="752a1-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="752a1-120">-LiteralPath</span></span>

<span data-ttu-id="752a1-121">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-121">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="752a1-122">*Path* 매개 변수와 달리 *LiteralPath* 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-122">Unlike the *Path* parameter, the value of the *LiteralPath* parameter is used exactly as it is entered.</span></span>
<span data-ttu-id="752a1-123">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-123">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="752a1-124">경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-124">If the path includes escape characters, enclose them in single quotation marks.</span></span>
<span data-ttu-id="752a1-125">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-125">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="752a1-126">-Path</span><span class="sxs-lookup"><span data-stu-id="752a1-126">-Path</span></span>

<span data-ttu-id="752a1-127">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-127">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="752a1-128">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-128">Wildcards are permitted.</span></span>
<span data-ttu-id="752a1-129">기본 위치는 현재 디렉터리(.)입니다.</span><span class="sxs-lookup"><span data-stu-id="752a1-129">The default location is the current directory (.).</span></span>

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

### <span data-ttu-id="752a1-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="752a1-130">CommonParameters</span></span>

<span data-ttu-id="752a1-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="752a1-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="752a1-132">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="752a1-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="752a1-133">입력</span><span class="sxs-lookup"><span data-stu-id="752a1-133">INPUTS</span></span>

### <span data-ttu-id="752a1-134">System.String</span><span class="sxs-lookup"><span data-stu-id="752a1-134">System.String</span></span>

## <span data-ttu-id="752a1-135">출력</span><span class="sxs-lookup"><span data-stu-id="752a1-135">OUTPUTS</span></span>

### <span data-ttu-id="752a1-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="752a1-136">System.Object</span></span>

## <span data-ttu-id="752a1-137">참고</span><span class="sxs-lookup"><span data-stu-id="752a1-137">NOTES</span></span>

## <span data-ttu-id="752a1-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="752a1-138">RELATED LINKS</span></span>

[<span data-ttu-id="752a1-139">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="752a1-139">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="752a1-140">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="752a1-140">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="752a1-141">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="752a1-141">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)

