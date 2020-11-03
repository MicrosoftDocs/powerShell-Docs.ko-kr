---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/find-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Script
ms.openlocfilehash: dcbe4efc6c351ff404405ee469c91769f86fd0e6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215706"
---
# <span data-ttu-id="9db3b-103">Find-Script</span><span class="sxs-lookup"><span data-stu-id="9db3b-103">Find-Script</span></span>

## <span data-ttu-id="9db3b-104">개요</span><span class="sxs-lookup"><span data-stu-id="9db3b-104">SYNOPSIS</span></span>
<span data-ttu-id="9db3b-105">스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-105">Finds a script.</span></span>

## <span data-ttu-id="9db3b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9db3b-106">SYNTAX</span></span>

```
Find-Script [[-Name] <String[]>] [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-AllVersions] [-IncludeDependencies] [-Filter <String>] [-Tag <String[]>]
 [-Includes <String[]>] [-Command <String[]>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [-Credential <PSCredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="9db3b-107">설명</span><span class="sxs-lookup"><span data-stu-id="9db3b-107">DESCRIPTION</span></span>

<span data-ttu-id="9db3b-108">**찾기-스크립트** cmdlet은 등록 된 리포지토리에서 지정 된 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-108">The **Find-Script** cmdlet finds a specified script in registered repositories.</span></span>

## <span data-ttu-id="9db3b-109">예제</span><span class="sxs-lookup"><span data-stu-id="9db3b-109">EXAMPLES</span></span>

### <span data-ttu-id="9db3b-110">예제 1: 사용 가능한 모든 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-110">Example 1: Find all available scripts</span></span>

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

<span data-ttu-id="9db3b-111">이 명령은 사용 가능한 모든 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-111">This command finds all available scripts.</span></span>

### <span data-ttu-id="9db3b-112">예제 2: 이름을 기준으로 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-112">Example 2: Find a script by name</span></span>

```
PS C:\> Find-Script -Name "Start-WFContosoServer"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
```

<span data-ttu-id="9db3b-113">이 명령은 WFContosoServer 라는 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-113">This command find the script named Start-WFContosoServer.</span></span>

### <span data-ttu-id="9db3b-114">예 3: 이름, 필요한 버전 및 지정 된 리포지토리에서 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-114">Example 3: Find a script by name, required version, and from a specified repository</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo01"
```

<span data-ttu-id="9db3b-115">이 명령은 LocalRepo01 리포지토리에서 이름 및 필요한 버전으로 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-115">This command finds a script by name and required version in the LocalRepo01 repository.</span></span>

### <span data-ttu-id="9db3b-116">예제 4: 스크립트 찾기 및 출력을 목록으로 서식 지정</span><span class="sxs-lookup"><span data-stu-id="9db3b-116">Example 4: Find a script and format the output as a list</span></span>

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

<span data-ttu-id="9db3b-117">이 명령은 LocalRepo1 리포지토리에서 Required-Script2를 찾은 다음 결과 **PSRepositoryItemInfo** 개체를 Format-List cmdlet에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-117">This command finds Required-Script2 in the LocalRepo1 repository, and then passes the resulting **PSRepositoryItemInfo** object to the Format-List cmdlet.</span></span>

### <span data-ttu-id="9db3b-118">예 5: 지정 된 버전 범위에서 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-118">Example 5: Find a script in the specified version range</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -MinimumVersion 2.1 -MaximumVersion 2.5 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="9db3b-119">이 명령은 LocalRepo1 리포지토리에서 버전 2.1과 2.5 사이의 모든 버전의 RequiredScript2를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-119">This command finds all versions of RequiredScript2 between versions 2.1 and 2.5 in the LocalRepo1 respository.</span></span>

### <span data-ttu-id="9db3b-120">예제 6: 스크립트의 모든 버전 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-120">Example 6: Find all versions of a script</span></span>

```
PS C:\> Find-Script -Name "Required-Script02" -AllVersions
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
1.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="9db3b-121">이 명령은 필요한 모든 버전의 Script02를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-121">This command finds all versions of Required-Script02.</span></span>

### <span data-ttu-id="9db3b-122">예 7: 스크립트 및 해당 종속성 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-122">Example 7: Find a script and its dependencies</span></span>

```
PS C:\> Find-Script -Name "Script-WithDependencies1" -IncludeDependencies -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        RequiredModule3                     Script     LocalRepo1           RequiredModule3 module
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="9db3b-123">이 명령은 스크립트와 해당 종속성을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-123">This command finds a script and its dependencies.</span></span>

### <span data-ttu-id="9db3b-124">예 8: 지정 된 태그를 사용 하 여 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-124">Example 8: Find scripts with the specified tag</span></span>

```
PS C:\> Find-Script -Tag "Tag1" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
```

<span data-ttu-id="9db3b-125">이 명령은 LocalRepo1 리포지토리에서 태그가 Tag1 인 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-125">This command finds scripts that have the tag Tag1 in the LocalRepo1 repository</span></span>

### <span data-ttu-id="9db3b-126">예 9: 지정 된 명령 이름의 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-126">Example 9: Find scripts with specified command name</span></span>

```
PS C:\> Find-Script -Command Test-FunctionFromScript_Required-Script3 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
```

<span data-ttu-id="9db3b-127">이 명령은 지정 된 명령 이름을 포함 하는 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-127">This command finds a script that contains the specified command name.</span></span>

### <span data-ttu-id="9db3b-128">예 10: 워크플로를 사용 하 여 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-128">Example 10: Find scripts with workflows</span></span>

```
PS C:\> Find-Script -Includes "Workflow" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
1.0        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
```

<span data-ttu-id="9db3b-129">이 명령은 LocalRepo1 리포지토리에서 워크플로 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-129">This command finds workflow scripts in the LocalRepo1 repository.</span></span>

### <span data-ttu-id="9db3b-130">예 11: 와일드 카드를 사용 하 여 스크립트 찾기</span><span class="sxs-lookup"><span data-stu-id="9db3b-130">Example 11: Find scripts using wildcards</span></span>

```
PS C:\> Find-Script -Name "Required-Script*" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="9db3b-131">이 명령은 와일드 카드 문자 (\*)를 사용 하 여 필수 스크립트로 시작 하는 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-131">This command uses the wildcard character (\*) to find scripts that begin with Required-Script.</span></span>

## <span data-ttu-id="9db3b-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9db3b-132">PARAMETERS</span></span>

### <span data-ttu-id="9db3b-133">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="9db3b-133">-AllowPrerelease</span></span>

<span data-ttu-id="9db3b-134">시험판으로 표시 된 결과 스크립트에를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-134">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="9db3b-135">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="9db3b-135">-AllVersions</span></span>

<span data-ttu-id="9db3b-136">이 작업에서 모든 스크립트 버전을 검색 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-136">Indicates that this operation finds all script versions.</span></span>

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

### <span data-ttu-id="9db3b-137">-Command</span><span class="sxs-lookup"><span data-stu-id="9db3b-137">-Command</span></span>

<span data-ttu-id="9db3b-138">스크립트에서 찾을 명령의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-138">Specifies an array of commands to find in scripts.</span></span>
<span data-ttu-id="9db3b-139">명령은 함수 또는 워크플로가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-139">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="9db3b-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="9db3b-140">-Credential</span></span>

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

### <span data-ttu-id="9db3b-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="9db3b-141">-Filter</span></span>

<span data-ttu-id="9db3b-142">PackageManagement 공급자별 검색 구문을 기반으로 하 여 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-142">Finds scripts based on the PackageManagement provider-specific search syntax.</span></span>

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

### <span data-ttu-id="9db3b-143">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="9db3b-143">-IncludeDependencies</span></span>

<span data-ttu-id="9db3b-144">이 작업에서 *Name* 매개 변수에 지정 된 스크립트에 종속 된 모든 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-144">Indicates that this operation gets all scripts that are dependent upon the script specified in the *Name* parameter.</span></span>

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

### <span data-ttu-id="9db3b-145">-포함</span><span class="sxs-lookup"><span data-stu-id="9db3b-145">-Includes</span></span>

<span data-ttu-id="9db3b-146">가져올 스크립트의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-146">Specifies type of script to get.</span></span>
<span data-ttu-id="9db3b-147">이 매개 변수에 사용할 수 있는 값은 함수, 워크플로입니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-147">The acceptable values for this parameter are: Function, Workflow.</span></span>

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

### <span data-ttu-id="9db3b-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9db3b-148">-MaximumVersion</span></span>

<span data-ttu-id="9db3b-149">찾을 스크립트의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-149">Specifies the maximum, or newest, version of the script to find.</span></span>
<span data-ttu-id="9db3b-150">*MaximumVersion* 및 *RequiredVersion* 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-150">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="9db3b-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9db3b-151">-MinimumVersion</span></span>

<span data-ttu-id="9db3b-152">찾을 스크립트의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-152">Specifies the minimum version of the script to find.</span></span>
<span data-ttu-id="9db3b-153">*MinimumVersion* 및 *RequiredVersion* 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-153">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="9db3b-154">-Name</span><span class="sxs-lookup"><span data-stu-id="9db3b-154">-Name</span></span>

<span data-ttu-id="9db3b-155">찾을 스크립트의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-155">Specifies an array of names of scripts to find.</span></span>

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

### <span data-ttu-id="9db3b-156">-프록시</span><span class="sxs-lookup"><span data-stu-id="9db3b-156">-Proxy</span></span>

<span data-ttu-id="9db3b-157">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-157">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="9db3b-158">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="9db3b-158">-ProxyCredential</span></span>

<span data-ttu-id="9db3b-159">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-159">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="9db3b-160">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="9db3b-160">-Repository</span></span>

<span data-ttu-id="9db3b-161">Set-psrepository를 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-161">Specifies the friendly name of a repository that has been registered by running Register-PSRepository.</span></span>

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

### <span data-ttu-id="9db3b-162">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9db3b-162">-RequiredVersion</span></span>

<span data-ttu-id="9db3b-163">찾을 스크립트의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-163">Specifies the exact version number of the script to find.</span></span>

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

### <span data-ttu-id="9db3b-164">-Tag</span><span class="sxs-lookup"><span data-stu-id="9db3b-164">-Tag</span></span>

<span data-ttu-id="9db3b-165">태그의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3b-165">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="9db3b-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9db3b-166">CommonParameters</span></span>

<span data-ttu-id="9db3b-167">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9db3b-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9db3b-168">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9db3b-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9db3b-169">입력</span><span class="sxs-lookup"><span data-stu-id="9db3b-169">INPUTS</span></span>

### <span data-ttu-id="9db3b-170">System.String[]</span><span class="sxs-lookup"><span data-stu-id="9db3b-170">System.String[]</span></span>

### <span data-ttu-id="9db3b-171">System.String</span><span class="sxs-lookup"><span data-stu-id="9db3b-171">System.String</span></span>

### <span data-ttu-id="9db3b-172">System.Uri</span><span class="sxs-lookup"><span data-stu-id="9db3b-172">System.Uri</span></span>

### <span data-ttu-id="9db3b-173">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="9db3b-173">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="9db3b-174">출력</span><span class="sxs-lookup"><span data-stu-id="9db3b-174">OUTPUTS</span></span>

### <span data-ttu-id="9db3b-175">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="9db3b-175">PSRepositoryItemInfo</span></span>

## <span data-ttu-id="9db3b-176">참고</span><span class="sxs-lookup"><span data-stu-id="9db3b-176">NOTES</span></span>

## <span data-ttu-id="9db3b-177">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9db3b-177">RELATED LINKS</span></span>

[<span data-ttu-id="9db3b-178">Install-Script</span><span class="sxs-lookup"><span data-stu-id="9db3b-178">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="9db3b-179">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="9db3b-179">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="9db3b-180">Save-Script</span><span class="sxs-lookup"><span data-stu-id="9db3b-180">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="9db3b-181">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="9db3b-181">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="9db3b-182">Update-Script</span><span class="sxs-lookup"><span data-stu-id="9db3b-182">Update-Script</span></span>](Update-Script.md)

