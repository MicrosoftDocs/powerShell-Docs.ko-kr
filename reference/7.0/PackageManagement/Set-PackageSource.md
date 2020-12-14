---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: 67a5a97c4e29556c9b93a17d25576d4bd6eaea0c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892708"
---
# <span data-ttu-id="38fc3-103">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="38fc3-103">Set-PackageSource</span></span>

## <span data-ttu-id="38fc3-104">개요</span><span class="sxs-lookup"><span data-stu-id="38fc3-104">SYNOPSIS</span></span>
<span data-ttu-id="38fc3-105">지정 된 패키지 공급자에 대 한 패키지 원본을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-105">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="38fc3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="38fc3-106">SYNTAX</span></span>

### <span data-ttu-id="38fc3-107">SourceBySearch (기본값)</span><span class="sxs-lookup"><span data-stu-id="38fc3-107">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="38fc3-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="38fc3-108">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="38fc3-109">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="38fc3-109">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="38fc3-110">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="38fc3-110">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="38fc3-111">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="38fc3-111">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="38fc3-112">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="38fc3-112">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="38fc3-113">설명</span><span class="sxs-lookup"><span data-stu-id="38fc3-113">DESCRIPTION</span></span>

<span data-ttu-id="38fc3-114">는 `Set-PackageSource` 지정 된 패키지 공급자에 대 한 패키지 소스를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-114">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="38fc3-115">패키지 원본은 항상 패키지 공급자에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-115">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="38fc3-116">예제</span><span class="sxs-lookup"><span data-stu-id="38fc3-116">EXAMPLES</span></span>

### <span data-ttu-id="38fc3-117">예제 1: 패키지 원본 변경</span><span class="sxs-lookup"><span data-stu-id="38fc3-117">Example 1: Change a package source</span></span>

<span data-ttu-id="38fc3-118">이 명령은 패키지 원본의 기존 이름을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-118">This command changes the existing name of a package source.</span></span> <span data-ttu-id="38fc3-119">원본은 **신뢰할** 수 있는 것으로 설정 되어 패키지가 설치 될 때 원본을 확인 하는 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-119">The source is set to **Trusted**, which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="38fc3-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38fc3-120">PARAMETERS</span></span>

### <span data-ttu-id="38fc3-121">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="38fc3-121">-ConfigFile</span></span>

<span data-ttu-id="38fc3-122">구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-122">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="38fc3-123">-Credential</span></span>

<span data-ttu-id="38fc3-124">패키지 공급자를 설치할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-124">Specifies a user account that has permission to install package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-125">-Force</span><span class="sxs-lookup"><span data-stu-id="38fc3-125">-Force</span></span>

<span data-ttu-id="38fc3-126">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="38fc3-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="38fc3-127">-ForceBootstrap</span></span>

<span data-ttu-id="38fc3-128">PackageManagement에서 `Set-PackageSource` 패키지  공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-128">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="38fc3-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="38fc3-129">-InputObject</span></span>

<span data-ttu-id="38fc3-130">변경 하려는 패키지를 나타내는 패키지 원본 ID 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-130">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="38fc3-131">패키지 원본 Id는 cmdlet의 결과에 포함 됩니다 `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="38fc3-131">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-132">-Location</span><span class="sxs-lookup"><span data-stu-id="38fc3-132">-Location</span></span>

<span data-ttu-id="38fc3-133">현재 패키지 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-133">Specifies the current package source location.</span></span> <span data-ttu-id="38fc3-134">값은 URI, 파일 경로 또는 패키지 공급자가 지 원하는 다른 모든 대상 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-134">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-135">-Name</span><span class="sxs-lookup"><span data-stu-id="38fc3-135">-Name</span></span>

<span data-ttu-id="38fc3-136">패키지 소스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-136">Specifies a package source's name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: SourceName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-137">-NewLocation</span><span class="sxs-lookup"><span data-stu-id="38fc3-137">-NewLocation</span></span>

<span data-ttu-id="38fc3-138">패키지 원본에 대 한 새 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-138">Specifies the new location for a package source.</span></span> <span data-ttu-id="38fc3-139">값은 URI, 파일 경로 또는 패키지 공급자가 지 원하는 다른 모든 대상 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-139">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="38fc3-140">-NewName</span><span class="sxs-lookup"><span data-stu-id="38fc3-140">-NewName</span></span>

<span data-ttu-id="38fc3-141">패키지 원본에 할당 하는 새 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-141">Specifies the new name you assign to a package source.</span></span>

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

### <span data-ttu-id="38fc3-142">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="38fc3-142">-PackageManagementProvider</span></span>

<span data-ttu-id="38fc3-143">패키지 관리 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-143">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-144">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="38fc3-144">-ProviderName</span></span>

<span data-ttu-id="38fc3-145">공급자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-145">Specifies a provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-146">-프록시</span><span class="sxs-lookup"><span data-stu-id="38fc3-146">-Proxy</span></span>

<span data-ttu-id="38fc3-147">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-147">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="38fc3-148">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="38fc3-148">-ProxyCredential</span></span>

<span data-ttu-id="38fc3-149">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-149">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="38fc3-150">-PublishLocation</span></span>

<span data-ttu-id="38fc3-151">게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-151">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="38fc3-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="38fc3-153">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-153">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="38fc3-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="38fc3-155">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-155">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="38fc3-156">-SkipValidate</span></span>

<span data-ttu-id="38fc3-157">패키지 원본에 대 한 자격 증명의 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-157">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38fc3-158">-신뢰할 수 있음</span><span class="sxs-lookup"><span data-stu-id="38fc3-158">-Trusted</span></span>

<span data-ttu-id="38fc3-159">소스가 신뢰할 수 있는 패키지 공급자 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-159">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="38fc3-160">신뢰할 수 있는 원본에서 패키지 설치를 확인 하는 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-160">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="38fc3-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="38fc3-161">-Confirm</span></span>

<span data-ttu-id="38fc3-162">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="38fc3-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="38fc3-163">-WhatIf</span></span>

<span data-ttu-id="38fc3-164">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-164">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="38fc3-165">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="38fc3-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38fc3-166">CommonParameters</span></span>

<span data-ttu-id="38fc3-167">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38fc3-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38fc3-168">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38fc3-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="38fc3-169">입력</span><span class="sxs-lookup"><span data-stu-id="38fc3-169">INPUTS</span></span>

### <span data-ttu-id="38fc3-170">`Set-PackageSource` 파이프라인 입력을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-170">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="38fc3-171">출력</span><span class="sxs-lookup"><span data-stu-id="38fc3-171">OUTPUTS</span></span>

### <span data-ttu-id="38fc3-172">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-172">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="38fc3-173">참고</span><span class="sxs-lookup"><span data-stu-id="38fc3-173">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38fc3-174">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-174">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="38fc3-175">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-175">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="38fc3-176">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="38fc3-176">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="38fc3-177">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38fc3-177">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="38fc3-178">관련 링크</span><span class="sxs-lookup"><span data-stu-id="38fc3-178">RELATED LINKS</span></span>

[<span data-ttu-id="38fc3-179">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="38fc3-179">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="38fc3-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="38fc3-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="38fc3-181">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="38fc3-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="38fc3-182">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="38fc3-182">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
