---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Script
ms.openlocfilehash: 240bd1be4cd4a54fc667fade257e07d29434274d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891459"
---
# <span data-ttu-id="db15b-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="db15b-103">Save-Script</span></span>

## <span data-ttu-id="db15b-104">개요</span><span class="sxs-lookup"><span data-stu-id="db15b-104">SYNOPSIS</span></span>
<span data-ttu-id="db15b-105">스크립트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-105">Saves a script.</span></span>

## <span data-ttu-id="db15b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="db15b-106">SYNTAX</span></span>

### <span data-ttu-id="db15b-107">NameAndPathParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="db15b-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="db15b-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="db15b-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="db15b-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="db15b-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="db15b-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="db15b-110">InputObjectAndPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="db15b-111">설명</span><span class="sxs-lookup"><span data-stu-id="db15b-111">DESCRIPTION</span></span>

<span data-ttu-id="db15b-112">`Save-Script`Cmdlet은 지정 된 스크립트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-112">The `Save-Script` cmdlet saves the specified script.</span></span>

## <span data-ttu-id="db15b-113">예제</span><span class="sxs-lookup"><span data-stu-id="db15b-113">EXAMPLES</span></span>

### <span data-ttu-id="db15b-114">예제 1: 스크립트 저장 및 스크립트 메타 데이터 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="db15b-114">Example 1: Save a script and validate the script's metadata</span></span>

<span data-ttu-id="db15b-115">이 예에서는 리포지토리의 스크립트를 로컬 컴퓨터에 저장 하 고 스크립트의 메타 데이터에 대 한 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-115">In this example, a script from a repository is saved to the local computer and the script's metadata is validated.</span></span>

```powershell
Save-Script -Name Install-VSCode -Repository PSGallery -Path C:\Test\Scripts
Test-ScriptFileInfo -Path C:\Test\Scripts\Install-VSCode.ps1
```

```Output
Version   Name              Author      Description
-------   ----              ------      -----------
1.3       Install-VSCode    Microsoft   This script can be used to easily install Visual Studio Code
```

<span data-ttu-id="db15b-116">`Save-Script`**name** 매개 변수를 사용 하 여 스크립트의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-116">`Save-Script` uses the **Name** parameter to specify the script's name.</span></span> <span data-ttu-id="db15b-117">**리포지토리** 매개 변수는 스크립트를 찾을 수 있는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-117">The **Repository** parameter specifies where to find the script.</span></span> <span data-ttu-id="db15b-118">스크립트는 **Path** 매개 변수로 지정 된 위치에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-118">The script is saved in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="db15b-119">`Test-ScriptFileInfo`**경로** 를 지정 하 고 스크립트의 메타 데이터에 대 한 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-119">`Test-ScriptFileInfo` specifies the **Path** and validates the script's metadata.</span></span>

## <span data-ttu-id="db15b-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="db15b-120">PARAMETERS</span></span>

### <span data-ttu-id="db15b-121">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="db15b-121">-AcceptLicense</span></span>

<span data-ttu-id="db15b-122">스크립트에 필요한 경우 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-122">Automatically accept the license agreement if the script requires it.</span></span>

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

### <span data-ttu-id="db15b-123">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="db15b-123">-AllowPrerelease</span></span>

<span data-ttu-id="db15b-124">시험판으로 표시 된 스크립트를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-124">Allows you to save a script marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db15b-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="db15b-125">-Confirm</span></span>

<span data-ttu-id="db15b-126">실행 하기 전에 확인 메시지를 표시 `Save-Script` 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-126">Prompts you for confirmation before running `Save-Script`.</span></span>

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

### <span data-ttu-id="db15b-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="db15b-127">-Credential</span></span>

<span data-ttu-id="db15b-128">스크립트를 저장할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-128">Specifies a user account that has permission to save a script.</span></span>

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

### <span data-ttu-id="db15b-129">-Force</span><span class="sxs-lookup"><span data-stu-id="db15b-129">-Force</span></span>

<span data-ttu-id="db15b-130">`Save-Script`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-130">Forces `Save-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="db15b-131">-InputObject</span><span class="sxs-lookup"><span data-stu-id="db15b-131">-InputObject</span></span>

<span data-ttu-id="db15b-132">**PSRepositoryItemInfo** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-132">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="db15b-133">예를 들어 `Find-Script` 변수를 출력 하 고 해당 변수를 **InputObject** 인수로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-133">For example, output `Find-Script` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="db15b-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="db15b-134">-LiteralPath</span></span>

<span data-ttu-id="db15b-135">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-135">Specifies a path to one or more locations.</span></span> <span data-ttu-id="db15b-136">**LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-136">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="db15b-137">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="db15b-138">경로에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-138">If the path includes escape characters, enclose the path within single quotation marks.</span></span> <span data-ttu-id="db15b-139">PowerShell은 작은 따옴표로 묶인 문자를 이스케이프 시퀀스로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-139">PowerShell doesn't interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="db15b-140">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="db15b-140">-MaximumVersion</span></span>

<span data-ttu-id="db15b-141">저장할 스크립트의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-141">Specifies the maximum, or newest version of the script to save.</span></span> <span data-ttu-id="db15b-142">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-142">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="db15b-143">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="db15b-143">-MinimumVersion</span></span>

<span data-ttu-id="db15b-144">저장할 스크립트의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-144">Specifies the minimum version of a script to save.</span></span> <span data-ttu-id="db15b-145">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-145">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="db15b-146">-Name</span><span class="sxs-lookup"><span data-stu-id="db15b-146">-Name</span></span>

<span data-ttu-id="db15b-147">저장할 스크립트 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-147">Specifies an array of script names to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="db15b-148">-Path</span><span class="sxs-lookup"><span data-stu-id="db15b-148">-Path</span></span>

<span data-ttu-id="db15b-149">저장 된 모듈을 저장할 로컬 컴퓨터의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-149">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="db15b-150">와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-150">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="db15b-151">-프록시</span><span class="sxs-lookup"><span data-stu-id="db15b-151">-Proxy</span></span>

<span data-ttu-id="db15b-152">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-152">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="db15b-153">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="db15b-153">-ProxyCredential</span></span>

<span data-ttu-id="db15b-154">**프록시** 매개 변수로 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-154">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="db15b-155">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="db15b-155">-Repository</span></span>

<span data-ttu-id="db15b-156">을 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="db15b-156">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="db15b-157">`Get-PSRepository`등록 된 리포지토리를 표시 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-157">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="db15b-158">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="db15b-158">-RequiredVersion</span></span>

<span data-ttu-id="db15b-159">저장할 스크립트의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-159">Specifies the exact version number of the script to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="db15b-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="db15b-160">-WhatIf</span></span>

<span data-ttu-id="db15b-161">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Save-Script` .</span><span class="sxs-lookup"><span data-stu-id="db15b-161">Shows what would happen if `Save-Script` runs.</span></span> <span data-ttu-id="db15b-162">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-162">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="db15b-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="db15b-163">CommonParameters</span></span>

<span data-ttu-id="db15b-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="db15b-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="db15b-165">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db15b-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="db15b-166">입력</span><span class="sxs-lookup"><span data-stu-id="db15b-166">INPUTS</span></span>

### <span data-ttu-id="db15b-167">System.String[]</span><span class="sxs-lookup"><span data-stu-id="db15b-167">System.String[]</span></span>

### <span data-ttu-id="db15b-168">System.web. PSObject []</span><span class="sxs-lookup"><span data-stu-id="db15b-168">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="db15b-169">System.String</span><span class="sxs-lookup"><span data-stu-id="db15b-169">System.String</span></span>

### <span data-ttu-id="db15b-170">System.Uri</span><span class="sxs-lookup"><span data-stu-id="db15b-170">System.Uri</span></span>

### <span data-ttu-id="db15b-171">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="db15b-171">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="db15b-172">출력</span><span class="sxs-lookup"><span data-stu-id="db15b-172">OUTPUTS</span></span>

### <span data-ttu-id="db15b-173">System.Object</span><span class="sxs-lookup"><span data-stu-id="db15b-173">System.Object</span></span>

## <span data-ttu-id="db15b-174">참고</span><span class="sxs-lookup"><span data-stu-id="db15b-174">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db15b-175">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-175">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="db15b-176">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-176">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="db15b-177">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="db15b-177">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="db15b-178">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db15b-178">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="db15b-179">관련 링크</span><span class="sxs-lookup"><span data-stu-id="db15b-179">RELATED LINKS</span></span>

[<span data-ttu-id="db15b-180">Find-Script</span><span class="sxs-lookup"><span data-stu-id="db15b-180">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="db15b-181">Install-Script</span><span class="sxs-lookup"><span data-stu-id="db15b-181">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="db15b-182">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="db15b-182">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="db15b-183">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="db15b-183">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="db15b-184">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="db15b-184">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="db15b-185">Update-Script</span><span class="sxs-lookup"><span data-stu-id="db15b-185">Update-Script</span></span>](Update-Script.md)
