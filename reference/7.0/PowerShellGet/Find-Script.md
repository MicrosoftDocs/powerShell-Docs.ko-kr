---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/find-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Script
ms.openlocfilehash: e07bf9ea44441f02593864789db447d9193b83ab
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892640"
---
# <span data-ttu-id="0d244-103">Find-Script</span><span class="sxs-lookup"><span data-stu-id="0d244-103">Find-Script</span></span>

## <span data-ttu-id="0d244-104">개요</span><span class="sxs-lookup"><span data-stu-id="0d244-104">SYNOPSIS</span></span>
<span data-ttu-id="0d244-105">스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-105">Finds a script.</span></span>

## <span data-ttu-id="0d244-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0d244-106">SYNTAX</span></span>

```
Find-Script [[-Name] <String[]>] [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-AllVersions] [-IncludeDependencies] [-Filter <String>] [-Tag <String[]>]
 [-Includes <String[]>] [-Command <String[]>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [-Credential <PSCredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="0d244-107">설명</span><span class="sxs-lookup"><span data-stu-id="0d244-107">DESCRIPTION</span></span>

<span data-ttu-id="0d244-108">**찾기-스크립트** cmdlet은 등록 된 리포지토리에서 지정 된 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-108">The **Find-Script** cmdlet finds a specified script in registered repositories.</span></span>

## <span data-ttu-id="0d244-109">예제</span><span class="sxs-lookup"><span data-stu-id="0d244-109">EXAMPLES</span></span>

### <span data-ttu-id="0d244-110">예제 1: 사용 가능한 모든 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-110">Example 1: Find all available scripts</span></span>

```
PS C:\> Find-Script
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
2.5        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
2.5        Fabrikam-ServerScript               Script     LocalRepo1           Description for the Fabrikam-ServerScript script
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        Script-WithDependencies2            Script     LocalRepo1           Description for the Script-WithDependencies2 script
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
2.1        Test-Script1                        Script     LocalRepo1           Test-Script1 Script example
2.0        Test-Script2                        Script     LocalRepo1           Test-Script2 Script example
1.0        TestRunbook                         Script     LocalRepo1           Contoso Script example
```

<span data-ttu-id="0d244-111">이 명령은 사용 가능한 모든 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-111">This command finds all available scripts.</span></span>

### <span data-ttu-id="0d244-112">예제 2: 이름을 기준으로 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-112">Example 2: Find a script by name</span></span>

```
PS C:\> Find-Script -Name "Start-WFContosoServer"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
```

<span data-ttu-id="0d244-113">이 명령은 WFContosoServer 라는 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-113">This command find the script named Start-WFContosoServer.</span></span>

### <span data-ttu-id="0d244-114">예 3: 이름, 필요한 버전 및 지정 된 리포지토리에서 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-114">Example 3: Find a script by name, required version, and from a specified repository</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo01"
```

<span data-ttu-id="0d244-115">이 명령은 LocalRepo01 리포지토리에서 이름 및 필요한 버전으로 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-115">This command finds a script by name and required version in the LocalRepo01 repository.</span></span>

### <span data-ttu-id="0d244-116">예제 4: 스크립트 찾기 및 출력을 목록으로 서식 지정</span><span class="sxs-lookup"><span data-stu-id="0d244-116">Example 4: Find a script and format the output as a list</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo1" | Format-List * -Force
Name                       : Required-Script2
Version                    : 2.0
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/14/2015 2:37:01 PM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {, Tag1, Tag2, Tag-Required-Script2-2.0...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : C:\MyLocalRepo
Repository                 : LocalRepo01
PackageManagementProvider  : NuGet
```

<span data-ttu-id="0d244-117">이 명령은 LocalRepo1 리포지토리에서 Required-Script2를 찾은 다음 결과 **PSRepositoryItemInfo** 개체를 Format-List cmdlet에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-117">This command finds Required-Script2 in the LocalRepo1 repository, and then passes the resulting **PSRepositoryItemInfo** object to the Format-List cmdlet.</span></span>

### <span data-ttu-id="0d244-118">예 5: 지정 된 버전 범위에서 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-118">Example 5: Find a script in the specified version range</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -MinimumVersion 2.1 -MaximumVersion 2.5 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="0d244-119">이 명령은 LocalRepo1 리포지토리에서 버전 2.1과 2.5 사이의 모든 버전의 RequiredScript2를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-119">This command finds all versions of RequiredScript2 between versions 2.1 and 2.5 in the LocalRepo1 respository.</span></span>

### <span data-ttu-id="0d244-120">예제 6: 스크립트의 모든 버전 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-120">Example 6: Find all versions of a script</span></span>

```
PS C:\> Find-Script -Name "Required-Script02" -AllVersions
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
1.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="0d244-121">이 명령은 필요한 모든 버전의 Script02를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-121">This command finds all versions of Required-Script02.</span></span>

### <span data-ttu-id="0d244-122">예 7: 스크립트 및 해당 종속성 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-122">Example 7: Find a script and its dependencies</span></span>

```
PS C:\> Find-Script -Name "Script-WithDependencies1" -IncludeDependencies -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        RequiredModule3                     Script     LocalRepo1           RequiredModule3 module
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="0d244-123">이 명령은 스크립트와 해당 종속성을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-123">This command finds a script and its dependencies.</span></span>

### <span data-ttu-id="0d244-124">예 8: 지정 된 태그를 사용 하 여 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-124">Example 8: Find scripts with the specified tag</span></span>

```
PS C:\> Find-Script -Tag "Tag1" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
```

<span data-ttu-id="0d244-125">이 명령은 LocalRepo1 리포지토리에서 태그가 Tag1 인 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-125">This command finds scripts that have the tag Tag1 in the LocalRepo1 repository</span></span>

### <span data-ttu-id="0d244-126">예 9: 지정 된 명령 이름의 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-126">Example 9: Find scripts with specified command name</span></span>

```
PS C:\> Find-Script -Command Test-FunctionFromScript_Required-Script3 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
```

<span data-ttu-id="0d244-127">이 명령은 지정 된 명령 이름을 포함 하는 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-127">This command finds a script that contains the specified command name.</span></span>

### <span data-ttu-id="0d244-128">예 10: 워크플로를 사용 하 여 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-128">Example 10: Find scripts with workflows</span></span>

```
PS C:\> Find-Script -Includes "Workflow" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
1.0        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
```

<span data-ttu-id="0d244-129">이 명령은 LocalRepo1 리포지토리에서 워크플로 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-129">This command finds workflow scripts in the LocalRepo1 repository.</span></span>

### <span data-ttu-id="0d244-130">예 11: 와일드 카드를 사용 하 여 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="0d244-130">Example 11: Find scripts using wildcards</span></span>

```
PS C:\> Find-Script -Name "Required-Script*" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="0d244-131">이 명령은 와일드 카드 문자 (\*)를 사용 하 여 필수 스크립트로 시작 하는 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-131">This command uses the wildcard character (\*) to find scripts that begin with Required-Script.</span></span>

## <span data-ttu-id="0d244-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0d244-132">PARAMETERS</span></span>

### <span data-ttu-id="0d244-133">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0d244-133">-AllowPrerelease</span></span>

<span data-ttu-id="0d244-134">시험판으로 표시 된 결과 스크립트에를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-134">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="0d244-135">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="0d244-135">-AllVersions</span></span>

<span data-ttu-id="0d244-136">이 작업에서 모든 스크립트 버전을 검색 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-136">Indicates that this operation finds all script versions.</span></span>

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

### <span data-ttu-id="0d244-137">-Command</span><span class="sxs-lookup"><span data-stu-id="0d244-137">-Command</span></span>

<span data-ttu-id="0d244-138">스크립트에서 찾을 명령의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-138">Specifies an array of commands to find in scripts.</span></span>
<span data-ttu-id="0d244-139">명령은 함수 또는 워크플로가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-139">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="0d244-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="0d244-140">-Credential</span></span>

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

### <span data-ttu-id="0d244-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="0d244-141">-Filter</span></span>

<span data-ttu-id="0d244-142">PackageManagement 공급자별 검색 구문을 기반으로 하 여 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-142">Finds scripts based on the PackageManagement provider-specific search syntax.</span></span>

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

### <span data-ttu-id="0d244-143">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="0d244-143">-IncludeDependencies</span></span>

<span data-ttu-id="0d244-144">이 작업에서 *Name* 매개 변수에 지정 된 스크립트에 종속 된 모든 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-144">Indicates that this operation gets all scripts that are dependent upon the script specified in the *Name* parameter.</span></span>

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

### <span data-ttu-id="0d244-145">-포함</span><span class="sxs-lookup"><span data-stu-id="0d244-145">-Includes</span></span>

<span data-ttu-id="0d244-146">가져올 스크립트의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-146">Specifies type of script to get.</span></span>
<span data-ttu-id="0d244-147">이 매개 변수에 사용할 수 있는 값은 함수, 워크플로입니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-147">The acceptable values for this parameter are: Function, Workflow.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Function, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0d244-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="0d244-148">-MaximumVersion</span></span>

<span data-ttu-id="0d244-149">찾을 스크립트의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-149">Specifies the maximum, or newest, version of the script to find.</span></span>
<span data-ttu-id="0d244-150">*MaximumVersion* 및 *RequiredVersion* 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-150">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="0d244-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="0d244-151">-MinimumVersion</span></span>

<span data-ttu-id="0d244-152">찾을 스크립트의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-152">Specifies the minimum version of the script to find.</span></span>
<span data-ttu-id="0d244-153">*MinimumVersion* 및 *RequiredVersion* 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-153">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="0d244-154">-Name</span><span class="sxs-lookup"><span data-stu-id="0d244-154">-Name</span></span>

<span data-ttu-id="0d244-155">찾을 스크립트의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-155">Specifies an array of names of scripts to find.</span></span>

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

### <span data-ttu-id="0d244-156">-프록시</span><span class="sxs-lookup"><span data-stu-id="0d244-156">-Proxy</span></span>

<span data-ttu-id="0d244-157">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-157">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="0d244-158">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="0d244-158">-ProxyCredential</span></span>

<span data-ttu-id="0d244-159">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-159">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="0d244-160">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="0d244-160">-Repository</span></span>

<span data-ttu-id="0d244-161">Set-psrepository를 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-161">Specifies the friendly name of a repository that has been registered by running Register-PSRepository.</span></span>

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

### <span data-ttu-id="0d244-162">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0d244-162">-RequiredVersion</span></span>

<span data-ttu-id="0d244-163">찾을 스크립트의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-163">Specifies the exact version number of the script to find.</span></span>

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

### <span data-ttu-id="0d244-164">-Tag</span><span class="sxs-lookup"><span data-stu-id="0d244-164">-Tag</span></span>

<span data-ttu-id="0d244-165">태그의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-165">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="0d244-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0d244-166">CommonParameters</span></span>

<span data-ttu-id="0d244-167">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0d244-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0d244-168">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d244-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0d244-169">입력</span><span class="sxs-lookup"><span data-stu-id="0d244-169">INPUTS</span></span>

### <span data-ttu-id="0d244-170">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0d244-170">System.String[]</span></span>

### <span data-ttu-id="0d244-171">System.String</span><span class="sxs-lookup"><span data-stu-id="0d244-171">System.String</span></span>

### <span data-ttu-id="0d244-172">System.Uri</span><span class="sxs-lookup"><span data-stu-id="0d244-172">System.Uri</span></span>

### <span data-ttu-id="0d244-173">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="0d244-173">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="0d244-174">출력</span><span class="sxs-lookup"><span data-stu-id="0d244-174">OUTPUTS</span></span>

### <span data-ttu-id="0d244-175">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="0d244-175">PSRepositoryItemInfo</span></span>

## <span data-ttu-id="0d244-176">참고</span><span class="sxs-lookup"><span data-stu-id="0d244-176">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d244-177">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-177">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="0d244-178">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-178">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="0d244-179">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d244-179">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="0d244-180">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d244-180">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="0d244-181">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0d244-181">RELATED LINKS</span></span>

[<span data-ttu-id="0d244-182">Install-Script</span><span class="sxs-lookup"><span data-stu-id="0d244-182">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="0d244-183">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="0d244-183">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="0d244-184">Save-Script</span><span class="sxs-lookup"><span data-stu-id="0d244-184">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="0d244-185">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="0d244-185">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="0d244-186">Update-Script</span><span class="sxs-lookup"><span data-stu-id="0d244-186">Update-Script</span></span>](Update-Script.md)
