---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/register-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PackageSource
ms.openlocfilehash: 76b3bd49f81f42cc80f4127f4b549acddcd1d906
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99601856"
---
# <span data-ttu-id="d3f8a-102">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d3f8a-102">Register-PackageSource</span></span>

## <span data-ttu-id="d3f8a-103">개요</span><span class="sxs-lookup"><span data-stu-id="d3f8a-103">SYNOPSIS</span></span>
<span data-ttu-id="d3f8a-104">지정 된 패키지 공급자에 대 한 패키지 소스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-104">Adds a package source for a specified package provider.</span></span>

## <span data-ttu-id="d3f8a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d3f8a-105">SYNTAX</span></span>

### <span data-ttu-id="d3f8a-106">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="d3f8a-106">SourceBySearch</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="d3f8a-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="d3f8a-107">NuGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="d3f8a-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d3f8a-108">PowerShellGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="d3f8a-109">설명</span><span class="sxs-lookup"><span data-stu-id="d3f8a-109">DESCRIPTION</span></span>

<span data-ttu-id="d3f8a-110">`Register-PackageSource`Cmdlet은 지정 된 패키지 공급자에 대 한 패키지 소스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-110">The `Register-PackageSource` cmdlet adds a package source for a specified package provider.</span></span> <span data-ttu-id="d3f8a-111">패키지 원본은 항상 패키지 공급자에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-111">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="d3f8a-112">패키지 공급자가 패키지 원본을 추가 하거나 교체할 수 없는 경우 공급자는 오류 메시지를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-112">If the package provider cannot add or replace a package source, the provider generates an error message.</span></span>

## <span data-ttu-id="d3f8a-113">예제</span><span class="sxs-lookup"><span data-stu-id="d3f8a-113">EXAMPLES</span></span>

### <span data-ttu-id="d3f8a-114">예제 1: NuGet 공급자에 대 한 패키지 소스 등록</span><span class="sxs-lookup"><span data-stu-id="d3f8a-114">Example 1: Register a package source for the NuGet provider</span></span>

<span data-ttu-id="d3f8a-115">이 명령은 **NuGet** 공급자의 웹 기반 위치인 패키지 소스를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-115">This command registers a package source, a web-based location for the **NuGet** provider.</span></span> <span data-ttu-id="d3f8a-116">기본적으로 원본은 신뢰할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-116">By default, sources aren't trusted.</span></span> <span data-ttu-id="d3f8a-117">패키지를 설치 하기 전에 원본을 신뢰할 수 있는지 확인 하는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-117">You are prompted to confirm the source is trusted before packages are installed.</span></span> <span data-ttu-id="d3f8a-118">기본값을 재정의 하려면 `-Trusted` 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-118">To override the default, use the `-Trusted` parameter.</span></span>

```powershell
Register-PackageSource -Name MyNuGet -Location https://www.nuget.org/api/v2 -ProviderName NuGet
```

```Output
Name          ProviderName     IsTrusted  Location
----          ------------     ---------  --------
MyNuGet       NuGet            False      https://www.nuget.org/api/v2
```

## <span data-ttu-id="d3f8a-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d3f8a-119">PARAMETERS</span></span>

### <span data-ttu-id="d3f8a-120">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="d3f8a-120">-ConfigFile</span></span>

<span data-ttu-id="d3f8a-121">구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-121">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d3f8a-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="d3f8a-122">-Credential</span></span>

<span data-ttu-id="d3f8a-123">인증 된 위치에 액세스할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-123">Specifies a user account that has permission to access the authenticated location.</span></span>

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

### <span data-ttu-id="d3f8a-124">-Force</span><span class="sxs-lookup"><span data-stu-id="d3f8a-124">-Force</span></span>

<span data-ttu-id="d3f8a-125">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d3f8a-126">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d3f8a-126">-ForceBootstrap</span></span>

<span data-ttu-id="d3f8a-127">이 cmdlet이 패키지 공급자를 자동으로 설치 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-127">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="d3f8a-128">-Location</span><span class="sxs-lookup"><span data-stu-id="d3f8a-128">-Location</span></span>

<span data-ttu-id="d3f8a-129">패키지 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-129">Specifies the package source location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d3f8a-130">-Name</span><span class="sxs-lookup"><span data-stu-id="d3f8a-130">-Name</span></span>

<span data-ttu-id="d3f8a-131">등록할 패키지 원본의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-131">Specifies the name of the package source to register.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d3f8a-132">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="d3f8a-132">-PackageManagementProvider</span></span>

<span data-ttu-id="d3f8a-133">패키지 관리 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-133">Specifies the Package Management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d3f8a-134">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="d3f8a-134">-ProviderName</span></span>

<span data-ttu-id="d3f8a-135">패키지 공급자의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-135">Specifies the package provider's name.</span></span>

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

### <span data-ttu-id="d3f8a-136">-프록시</span><span class="sxs-lookup"><span data-stu-id="d3f8a-136">-Proxy</span></span>

<span data-ttu-id="d3f8a-137">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-137">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="d3f8a-138">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="d3f8a-138">-ProxyCredential</span></span>

<span data-ttu-id="d3f8a-139">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-139">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="d3f8a-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="d3f8a-140">-PublishLocation</span></span>

<span data-ttu-id="d3f8a-141">게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-141">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d3f8a-142">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="d3f8a-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="d3f8a-143">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-143">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d3f8a-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="d3f8a-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="d3f8a-145">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-145">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d3f8a-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="d3f8a-146">-SkipValidate</span></span>

<span data-ttu-id="d3f8a-147">패키지 원본에 대 한 자격 증명의 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-147">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d3f8a-148">-신뢰할 수 있음</span><span class="sxs-lookup"><span data-stu-id="d3f8a-148">-Trusted</span></span>

<span data-ttu-id="d3f8a-149">패키지 원본을 신뢰할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-149">Indicates that the package source is trusted.</span></span>

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

### <span data-ttu-id="d3f8a-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d3f8a-150">-Confirm</span></span>

<span data-ttu-id="d3f8a-151">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d3f8a-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d3f8a-152">-WhatIf</span></span>

<span data-ttu-id="d3f8a-153">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-153">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d3f8a-154">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d3f8a-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d3f8a-155">CommonParameters</span></span>

<span data-ttu-id="d3f8a-156">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d3f8a-157">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d3f8a-158">입력</span><span class="sxs-lookup"><span data-stu-id="d3f8a-158">INPUTS</span></span>

## <span data-ttu-id="d3f8a-159">출력</span><span class="sxs-lookup"><span data-stu-id="d3f8a-159">OUTPUTS</span></span>

## <span data-ttu-id="d3f8a-160">참고</span><span class="sxs-lookup"><span data-stu-id="d3f8a-160">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3f8a-161">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-161">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d3f8a-162">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-162">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d3f8a-163">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-163">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d3f8a-164">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3f8a-164">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d3f8a-165">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d3f8a-165">RELATED LINKS</span></span>

[<span data-ttu-id="d3f8a-166">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d3f8a-166">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d3f8a-167">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d3f8a-167">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="d3f8a-168">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d3f8a-168">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="d3f8a-169">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d3f8a-169">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
