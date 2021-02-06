---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Script
ms.openlocfilehash: 2f672cbb814b0641411bb11ffb17bd1ecef96dda
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99601041"
---
# <span data-ttu-id="aedfb-102">Save-Script</span><span class="sxs-lookup"><span data-stu-id="aedfb-102">Save-Script</span></span>

## <span data-ttu-id="aedfb-103">개요</span><span class="sxs-lookup"><span data-stu-id="aedfb-103">SYNOPSIS</span></span>
<span data-ttu-id="aedfb-104">스크립트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-104">Saves a script.</span></span>

## <span data-ttu-id="aedfb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aedfb-105">SYNTAX</span></span>

### <span data-ttu-id="aedfb-106">NameAndPathParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="aedfb-106">NameAndPathParameterSet (Default)</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aedfb-107">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="aedfb-107">NameAndLiteralPathParameterSet</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aedfb-108">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="aedfb-108">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aedfb-109">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="aedfb-109">InputObjectAndPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="aedfb-110">설명</span><span class="sxs-lookup"><span data-stu-id="aedfb-110">DESCRIPTION</span></span>

<span data-ttu-id="aedfb-111">`Save-Script`Cmdlet은 지정 된 스크립트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-111">The `Save-Script` cmdlet saves the specified script.</span></span>

## <span data-ttu-id="aedfb-112">예제</span><span class="sxs-lookup"><span data-stu-id="aedfb-112">EXAMPLES</span></span>

### <span data-ttu-id="aedfb-113">예제 1: 스크립트 저장 및 스크립트 메타 데이터 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="aedfb-113">Example 1: Save a script and validate the script's metadata</span></span>

<span data-ttu-id="aedfb-114">이 예에서는 리포지토리의 스크립트를 로컬 컴퓨터에 저장 하 고 스크립트의 메타 데이터에 대 한 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-114">In this example, a script from a repository is saved to the local computer and the script's metadata is validated.</span></span>

```powershell
Save-Script -Name Install-VSCode -Repository PSGallery -Path C:\Test\Scripts
Test-ScriptFileInfo -Path C:\Test\Scripts\Install-VSCode.ps1
```

```Output
Version   Name              Author      Description
-------   ----              ------      -----------
1.3       Install-VSCode    Microsoft   This script can be used to easily install Visual Studio Code
```

<span data-ttu-id="aedfb-115">`Save-Script`**name** 매개 변수를 사용 하 여 스크립트의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-115">`Save-Script` uses the **Name** parameter to specify the script's name.</span></span> <span data-ttu-id="aedfb-116">**리포지토리** 매개 변수는 스크립트를 찾을 수 있는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-116">The **Repository** parameter specifies where to find the script.</span></span> <span data-ttu-id="aedfb-117">스크립트는 **Path** 매개 변수로 지정 된 위치에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-117">The script is saved in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="aedfb-118">`Test-ScriptFileInfo`**경로** 를 지정 하 고 스크립트의 메타 데이터에 대 한 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-118">`Test-ScriptFileInfo` specifies the **Path** and validates the script's metadata.</span></span>

## <span data-ttu-id="aedfb-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aedfb-119">PARAMETERS</span></span>

### <span data-ttu-id="aedfb-120">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="aedfb-120">-AcceptLicense</span></span>

<span data-ttu-id="aedfb-121">스크립트에 필요한 경우 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-121">Automatically accept the license agreement if the script requires it.</span></span>

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

### <span data-ttu-id="aedfb-122">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="aedfb-122">-AllowPrerelease</span></span>

<span data-ttu-id="aedfb-123">시험판으로 표시 된 스크립트를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-123">Allows you to save a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="aedfb-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aedfb-124">-Confirm</span></span>

<span data-ttu-id="aedfb-125">실행 하기 전에 확인 메시지를 표시 `Save-Script` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-125">Prompts you for confirmation before running `Save-Script`.</span></span>

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

### <span data-ttu-id="aedfb-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="aedfb-126">-Credential</span></span>

<span data-ttu-id="aedfb-127">스크립트를 저장할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-127">Specifies a user account that has permission to save a script.</span></span>

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

### <span data-ttu-id="aedfb-128">-Force</span><span class="sxs-lookup"><span data-stu-id="aedfb-128">-Force</span></span>

<span data-ttu-id="aedfb-129">`Save-Script`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-129">Forces `Save-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="aedfb-130">-InputObject</span><span class="sxs-lookup"><span data-stu-id="aedfb-130">-InputObject</span></span>

<span data-ttu-id="aedfb-131">**PSRepositoryItemInfo** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="aedfb-132">예를 들어 `Find-Script` 변수를 출력 하 고 해당 변수를 **InputObject** 인수로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-132">For example, output `Find-Script` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="aedfb-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aedfb-133">-LiteralPath</span></span>

<span data-ttu-id="aedfb-134">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-134">Specifies a path to one or more locations.</span></span> <span data-ttu-id="aedfb-135">**LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-135">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="aedfb-136">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-136">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="aedfb-137">경로에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-137">If the path includes escape characters, enclose the path within single quotation marks.</span></span> <span data-ttu-id="aedfb-138">PowerShell은 작은 따옴표로 묶인 문자를 이스케이프 시퀀스로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-138">PowerShell doesn't interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

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

### <span data-ttu-id="aedfb-139">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="aedfb-139">-MaximumVersion</span></span>

<span data-ttu-id="aedfb-140">저장할 스크립트의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-140">Specifies the maximum, or newest version of the script to save.</span></span> <span data-ttu-id="aedfb-141">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-141">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="aedfb-142">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="aedfb-142">-MinimumVersion</span></span>

<span data-ttu-id="aedfb-143">저장할 스크립트의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-143">Specifies the minimum version of a script to save.</span></span> <span data-ttu-id="aedfb-144">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-144">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="aedfb-145">-Name</span><span class="sxs-lookup"><span data-stu-id="aedfb-145">-Name</span></span>

<span data-ttu-id="aedfb-146">저장할 스크립트 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-146">Specifies an array of script names to save.</span></span>

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

### <span data-ttu-id="aedfb-147">-Path</span><span class="sxs-lookup"><span data-stu-id="aedfb-147">-Path</span></span>

<span data-ttu-id="aedfb-148">저장 된 모듈을 저장할 로컬 컴퓨터의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-148">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="aedfb-149">와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-149">Accepts wildcard characters.</span></span>

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

### <span data-ttu-id="aedfb-150">-프록시</span><span class="sxs-lookup"><span data-stu-id="aedfb-150">-Proxy</span></span>

<span data-ttu-id="aedfb-151">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-151">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="aedfb-152">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="aedfb-152">-ProxyCredential</span></span>

<span data-ttu-id="aedfb-153">**프록시** 매개 변수로 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-153">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="aedfb-154">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="aedfb-154">-Repository</span></span>

<span data-ttu-id="aedfb-155">을 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="aedfb-155">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="aedfb-156">`Get-PSRepository`등록 된 리포지토리를 표시 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-156">Use `Get-PSRepository` to display registered repositories.</span></span>

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

### <span data-ttu-id="aedfb-157">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="aedfb-157">-RequiredVersion</span></span>

<span data-ttu-id="aedfb-158">저장할 스크립트의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-158">Specifies the exact version number of the script to save.</span></span>

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

### <span data-ttu-id="aedfb-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aedfb-159">-WhatIf</span></span>

<span data-ttu-id="aedfb-160">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Save-Script` .</span><span class="sxs-lookup"><span data-stu-id="aedfb-160">Shows what would happen if `Save-Script` runs.</span></span> <span data-ttu-id="aedfb-161">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-161">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="aedfb-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aedfb-162">CommonParameters</span></span>

<span data-ttu-id="aedfb-163">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aedfb-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aedfb-164">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aedfb-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aedfb-165">입력</span><span class="sxs-lookup"><span data-stu-id="aedfb-165">INPUTS</span></span>

### <span data-ttu-id="aedfb-166">System.String[]</span><span class="sxs-lookup"><span data-stu-id="aedfb-166">System.String[]</span></span>

### <span data-ttu-id="aedfb-167">System.web. PSObject []</span><span class="sxs-lookup"><span data-stu-id="aedfb-167">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="aedfb-168">System.String</span><span class="sxs-lookup"><span data-stu-id="aedfb-168">System.String</span></span>

### <span data-ttu-id="aedfb-169">System.Uri</span><span class="sxs-lookup"><span data-stu-id="aedfb-169">System.Uri</span></span>

### <span data-ttu-id="aedfb-170">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="aedfb-170">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="aedfb-171">출력</span><span class="sxs-lookup"><span data-stu-id="aedfb-171">OUTPUTS</span></span>

### <span data-ttu-id="aedfb-172">System.Object</span><span class="sxs-lookup"><span data-stu-id="aedfb-172">System.Object</span></span>

## <span data-ttu-id="aedfb-173">참고</span><span class="sxs-lookup"><span data-stu-id="aedfb-173">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aedfb-174">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-174">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="aedfb-175">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-175">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="aedfb-176">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aedfb-176">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="aedfb-177">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aedfb-177">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="aedfb-178">관련 링크</span><span class="sxs-lookup"><span data-stu-id="aedfb-178">RELATED LINKS</span></span>

[<span data-ttu-id="aedfb-179">Find-Script</span><span class="sxs-lookup"><span data-stu-id="aedfb-179">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="aedfb-180">Install-Script</span><span class="sxs-lookup"><span data-stu-id="aedfb-180">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="aedfb-181">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="aedfb-181">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="aedfb-182">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="aedfb-182">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="aedfb-183">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="aedfb-183">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="aedfb-184">Update-Script</span><span class="sxs-lookup"><span data-stu-id="aedfb-184">Update-Script</span></span>](Update-Script.md)
