---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: ecae1ba3a3aea6628817bab2f09fc23e23162f03
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215985"
---
# <span data-ttu-id="6b681-103">Install-Script</span><span class="sxs-lookup"><span data-stu-id="6b681-103">Install-Script</span></span>

## <span data-ttu-id="6b681-104">개요</span><span class="sxs-lookup"><span data-stu-id="6b681-104">SYNOPSIS</span></span>
<span data-ttu-id="6b681-105">스크립트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-105">Installs a script.</span></span>

## <span data-ttu-id="6b681-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6b681-106">SYNTAX</span></span>

### <span data-ttu-id="6b681-107">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="6b681-107">NameParameterSet (Default)</span></span>

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6b681-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="6b681-108">InputObject</span></span>

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6b681-109">설명</span><span class="sxs-lookup"><span data-stu-id="6b681-109">DESCRIPTION</span></span>

<span data-ttu-id="6b681-110">`Install-Script`Cmdlet은 리포지토리에서 스크립트 페이로드를 획득 하 고 페이로드가 유효한 PowerShell 스크립트 인지 확인 하 고 스크립트 파일을 지정 된 설치 위치에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-110">The `Install-Script` cmdlet acquires a script payload from a repository, verifies that the payload is a valid PowerShell script, and copies the script file to a specified installation location.</span></span>

<span data-ttu-id="6b681-111">에 대해 작동 하는 기본 리포지토리는 `Install-Script` ,, 및 cmdlet을 통해 구성할 수 `Register-PSRepository` `Set-PSRepository` `Unregister-PSRepository` `Get-PSRepository` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-111">The default repositories `Install-Script` operates against are configurable through the `Register-PSRepository`, `Set-PSRepository`, `Unregister-PSRepository`, and `Get-PSRepository` cmdlets.</span></span> <span data-ttu-id="6b681-112">여러 리포지토리에 대해 작업 하는 경우는 `Install-Script` 오류 없이 첫 번째 리포지토리에서 지정 된 검색 조건 **(Name** , **MinimumVersion** 또는 **MaximumVersion** )과 일치 하는 첫 번째 스크립트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-112">When operating against multiple repositories, `Install-Script` installs the first script that matches the specified search criteria ( **Name** , **MinimumVersion** , or **MaximumVersion** ) from the first repository without any error.</span></span>

## <span data-ttu-id="6b681-113">예제</span><span class="sxs-lookup"><span data-stu-id="6b681-113">EXAMPLES</span></span>

### <span data-ttu-id="6b681-114">예제 1: 스크립트 찾기 및 설치</span><span class="sxs-lookup"><span data-stu-id="6b681-114">Example 1: Find a script and install it</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

<span data-ttu-id="6b681-115">첫 번째 명령은 Local1 리포지토리에서 이라는 스크립트를 찾아 `Required-Script2` 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-115">The first command finds the script named `Required-Script2` from the Local1 repository and displays the results.</span></span>

<span data-ttu-id="6b681-116">두 번째 명령은 `Required-Script2` 스크립트를 찾은 다음 파이프라인 연산자를 사용 하 여 cmdlet에 전달 하 여 `Install-Script` 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-116">The second command finds the `Required-Script2` script, and then uses the pipeline operator to pass it to the `Install-Script` cmdlet to install it.</span></span>

<span data-ttu-id="6b681-117">세 번째 명령은 cmdlet을 사용 하 여 `Get-Command` `Required-Script2` 를 가져온 다음 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-117">The third command uses the `Get-Command` cmdlet to get `Required-Script2`, and then displays the results.</span></span>

<span data-ttu-id="6b681-118">네 번째 명령은 cmdlet을 사용 하 여 `Get-InstalledScript` 결과를 가져오고 `Required-Script2` 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-118">The fourth command uses the `Get-InstalledScript` cmdlet to get `Required-Script2` and display the results.</span></span>

<span data-ttu-id="6b681-119">다섯 번째 명령은 `Required-Script2` 파이프라인 연산자를 가져와 cmdlet에 전달 하 여 `Format-List` 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-119">The fifth command gets `Required-Script2` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="6b681-120">예 2: AllUsers 범위를 사용 하 여 스크립트 설치</span><span class="sxs-lookup"><span data-stu-id="6b681-120">Example 2: Install a script with AllUsers scope</span></span>

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

<span data-ttu-id="6b681-121">첫 번째 명령은 이라는 스크립트를 설치 `Required-Script3` 하 고이를 AllUsers 범위에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-121">The first command installs the script named `Required-Script3` and assigns it AllUsers scope.</span></span>

<span data-ttu-id="6b681-122">두 번째 명령은 설치 된 스크립트를 가져오고 `Required-Script3` 해당 스크립트에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-122">The second command gets the installed script `Required-Script3` and displays information about it.</span></span>

<span data-ttu-id="6b681-123">세 번째 명령은 `Required-Script3` 파이프라인 연산자를 가져와 cmdlet에 전달 하 여 `Format-List` 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-123">The third command gets `Required-Script3` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="6b681-124">예제 3: 스크립트 및 해당 종속성 설치</span><span class="sxs-lookup"><span data-stu-id="6b681-124">Example 3: Install a script and its dependencies</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

<span data-ttu-id="6b681-125">첫 번째 명령은 Local1 리포지토리에서 이라는 스크립트 `Script-WithDependencies2` 와 해당 종속성을 찾아 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-125">The first command finds the script named `Script-WithDependencies2` and its dependencies in the Local1 repository and displays the results.</span></span>

<span data-ttu-id="6b681-126">두 번째 명령은를 설치 `Script-WithDependencies2` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-126">The second command installs `Script-WithDependencies2`.</span></span>

<span data-ttu-id="6b681-127">세 번째 명령은 스크립트 cmdlet을 사용 하 여 `Get-InstalledScript` 설치 된 스크립트를 가져오고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-127">The third command uses the `Get-InstalledScript` script cmdlet to get installed scripts and display the results.</span></span>

<span data-ttu-id="6b681-128">네 번째 명령은 cmdlet을 사용 하 여 `Get-InstalledModule` 설치 된 모듈을 가져오고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-128">The fourth command uses the `Get-InstalledModule` cmdlet to get installed modules and display the results.</span></span>

<span data-ttu-id="6b681-129">다섯 번째 명령은 cmdlet을 사용 하 여 `Find-Script` 이름이로 시작 하 `Required-Script` 고 결과를 표시 하는 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-129">The fifth command uses the `Find-Script` cmdlet to find scripts where the name begins with `Required-Script` and display the results.</span></span>

<span data-ttu-id="6b681-130">여섯 번째 명령은 Local1 리포지토리에서 이름이로 시작 하는 스크립트를 설치 합니다 `Required-Script` .</span><span class="sxs-lookup"><span data-stu-id="6b681-130">The sixth command installs the scripts where the name begins with `Required-Script` in the Local1 repository.</span></span>

<span data-ttu-id="6b681-131">최종 명령은 설치 된 스크립트를 가져오고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-131">The final command gets installed scripts and displays the results.</span></span>

## <span data-ttu-id="6b681-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6b681-132">PARAMETERS</span></span>

### <span data-ttu-id="6b681-133">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6b681-133">-AcceptLicense</span></span>

<span data-ttu-id="6b681-134">모듈에 필요한 경우 설치 하는 동안 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-134">Automatically accept the license agreement during installation if the module requires it.</span></span>

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

### <span data-ttu-id="6b681-135">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="6b681-135">-AllowPrerelease</span></span>

<span data-ttu-id="6b681-136">시험판으로 표시 된 스크립트를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-136">Allows you to install a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="6b681-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6b681-137">-Confirm</span></span>

<span data-ttu-id="6b681-138">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6b681-139">-Credential</span><span class="sxs-lookup"><span data-stu-id="6b681-139">-Credential</span></span>

<span data-ttu-id="6b681-140">지정 된 패키지 공급자나 원본에 대 한 스크립트를 설치할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-140">Specifies a user account that has rights to install a script for a specified package provider or source.</span></span>

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

### <span data-ttu-id="6b681-141">-Force</span><span class="sxs-lookup"><span data-stu-id="6b681-141">-Force</span></span>

<span data-ttu-id="6b681-142">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="6b681-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6b681-143">-InputObject</span></span>

<span data-ttu-id="6b681-144">파이프라인 입력에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-144">Used for pipeline input.</span></span>

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

### <span data-ttu-id="6b681-145">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6b681-145">-MaximumVersion</span></span>

<span data-ttu-id="6b681-146">설치할 단일 스크립트의 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-146">Specifies the maximum version of a single scripts to install.</span></span> <span data-ttu-id="6b681-147">여러 스크립트를 설치 하려는 경우에는이 매개 변수를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-147">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="6b681-148">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-148">The **MaximumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="6b681-149">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6b681-149">-MinimumVersion</span></span>

<span data-ttu-id="6b681-150">설치할 단일 스크립트의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-150">Specifies the minimum version of a single script to install.</span></span> <span data-ttu-id="6b681-151">여러 스크립트를 설치 하려는 경우에는이 매개 변수를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-151">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="6b681-152">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-152">The **MinimumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="6b681-153">-Name</span><span class="sxs-lookup"><span data-stu-id="6b681-153">-Name</span></span>

<span data-ttu-id="6b681-154">설치할 스크립트의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-154">Specifies an array of names of scripts to install.</span></span>

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

### <span data-ttu-id="6b681-155">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="6b681-155">-NoPathUpdate</span></span>

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

### <span data-ttu-id="6b681-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="6b681-156">-PassThru</span></span>

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

### <span data-ttu-id="6b681-157">-프록시</span><span class="sxs-lookup"><span data-stu-id="6b681-157">-Proxy</span></span>

<span data-ttu-id="6b681-158">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-158">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="6b681-159">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="6b681-159">-ProxyCredential</span></span>

<span data-ttu-id="6b681-160">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-160">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="6b681-161">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="6b681-161">-Repository</span></span>

<span data-ttu-id="6b681-162">Cmdlet에 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="6b681-162">Specifies the friendly name of a repository that has been registered with the `Register-PSRepository` cmdlet.</span></span> <span data-ttu-id="6b681-163">기본값은 등록 된 모든 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-163">The default is all registered repositories.</span></span>

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

### <span data-ttu-id="6b681-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6b681-164">-RequiredVersion</span></span>

<span data-ttu-id="6b681-165">설치할 스크립트의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-165">Specifies the exact version number of the script to install.</span></span>

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

### <span data-ttu-id="6b681-166">-범위</span><span class="sxs-lookup"><span data-stu-id="6b681-166">-Scope</span></span>

<span data-ttu-id="6b681-167">스크립트의 설치 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-167">Specifies the installation scope of the script.</span></span>
<span data-ttu-id="6b681-168">유효한 값은 AllUsers 및 CurrentUser입니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-168">Valid values are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="6b681-169">AllUsers 범위를 사용 하면 컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 모듈을 설치할 수 있습니다 `$env:ProgramFiles\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="6b681-169">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, `$env:ProgramFiles\WindowsPowerShell\Scripts`.</span></span>

<span data-ttu-id="6b681-170">CurrentUser 범위를 사용 하면 모듈을에만 설치할 수 `$home\Documents\WindowsPowerShell\Scripts` 있으므로 모듈을 현재 사용자만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-170">The CurrentUser scope lets modules be installed only to `$home\Documents\WindowsPowerShell\Scripts`, so that the module is available only to the current user.</span></span>

<span data-ttu-id="6b681-171">**범위** 를 정의 하지 않으면 현재 세션에 따라 기본값이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-171">When no **Scope** is defined, the default will be set based on the current session:</span></span>

- <span data-ttu-id="6b681-172">관리자 권한 PowerShell 세션의 경우 기본 **범위** 는 AllUsers로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-172">For an elevated PowerShell session, **Scope** defaults to AllUsers;</span></span>
- <span data-ttu-id="6b681-173">[PowerShellGet 버전 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) 이상에서 관리자가 아닌 PowerShell 세션의 경우 **범위** 는 CurrentUser입니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-173">For non-elevated PowerShell sessions in [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) and above, **Scope** is CurrentUser;</span></span>
- <span data-ttu-id="6b681-174">PowerShellGet 버전 1.6.7 및 이전 버전의 관리자가 아닌 PowerShell 세션의 경우 **범위가** 정의 되지 않고 `Install-Module` 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-174">For non-elevated PowerShell sessions in PowerShellGet versions 1.6.7 and earlier, **Scope** is undefined, and `Install-Module` fails.</span></span>

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

### <span data-ttu-id="6b681-175">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6b681-175">-WhatIf</span></span>

<span data-ttu-id="6b681-176">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-176">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6b681-177">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b681-177">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6b681-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6b681-178">CommonParameters</span></span>

<span data-ttu-id="6b681-179">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6b681-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6b681-180">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b681-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6b681-181">입력</span><span class="sxs-lookup"><span data-stu-id="6b681-181">INPUTS</span></span>

### <span data-ttu-id="6b681-182">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6b681-182">System.String[]</span></span>

### <span data-ttu-id="6b681-183">System.web. PSObject []</span><span class="sxs-lookup"><span data-stu-id="6b681-183">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="6b681-184">System.String</span><span class="sxs-lookup"><span data-stu-id="6b681-184">System.String</span></span>

### <span data-ttu-id="6b681-185">System.Uri</span><span class="sxs-lookup"><span data-stu-id="6b681-185">System.Uri</span></span>

### <span data-ttu-id="6b681-186">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="6b681-186">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="6b681-187">출력</span><span class="sxs-lookup"><span data-stu-id="6b681-187">OUTPUTS</span></span>

### <span data-ttu-id="6b681-188">System.Object</span><span class="sxs-lookup"><span data-stu-id="6b681-188">System.Object</span></span>

## <span data-ttu-id="6b681-189">참고</span><span class="sxs-lookup"><span data-stu-id="6b681-189">NOTES</span></span>

## <span data-ttu-id="6b681-190">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6b681-190">RELATED LINKS</span></span>

[<span data-ttu-id="6b681-191">Find-Script</span><span class="sxs-lookup"><span data-stu-id="6b681-191">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="6b681-192">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="6b681-192">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="6b681-193">Save-Script</span><span class="sxs-lookup"><span data-stu-id="6b681-193">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="6b681-194">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="6b681-194">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="6b681-195">Update-Script</span><span class="sxs-lookup"><span data-stu-id="6b681-195">Update-Script</span></span>](Update-Script.md)
