---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: d5257c334c22fb9955925e00f775635493451e71
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892868"
---
# <span data-ttu-id="795dc-103">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="795dc-103">Get-PackageSource</span></span>

## <span data-ttu-id="795dc-104">개요</span><span class="sxs-lookup"><span data-stu-id="795dc-104">SYNOPSIS</span></span>
<span data-ttu-id="795dc-105">패키지 공급자에 대해 등록 된 패키지 소스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-105">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="795dc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="795dc-106">SYNTAX</span></span>

### <span data-ttu-id="795dc-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="795dc-107">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="795dc-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="795dc-108">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="795dc-109">설명</span><span class="sxs-lookup"><span data-stu-id="795dc-109">DESCRIPTION</span></span>

<span data-ttu-id="795dc-110">`Get-PackageSource`Cmdlet은 로컬 컴퓨터의 **PackageManagement** 에 등록 된 패키지 원본 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-110">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="795dc-111">패키지 공급자를 지정 하는 경우 `Get-PackageSource` 지정 된 공급자와 연결 된 원본만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-111">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="795dc-112">그렇지 않으면이 명령은 **PackageManagement** 에 등록 된 모든 패키지 원본을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-112">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="795dc-113">예제</span><span class="sxs-lookup"><span data-stu-id="795dc-113">EXAMPLES</span></span>

### <span data-ttu-id="795dc-114">예제 1: 모든 패키지 소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="795dc-114">Example 1: Get all package sources</span></span>

<span data-ttu-id="795dc-115">`Get-PackageSource`Cmdlet은 로컬 컴퓨터의 **PackageManagement** 에 등록 된 모든 패키지 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-115">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

```powershell
Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
PSGallery            PowerShellGet    False      https://www.powershellgallery.com/api/v2
```

### <span data-ttu-id="795dc-116">예 2: 특정 공급자에 대 한 모든 패키지 원본 가져오기</span><span class="sxs-lookup"><span data-stu-id="795dc-116">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="795dc-117">이 명령은 특정 공급자에 대해 등록 된 패키지 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-117">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="795dc-118">`Get-PackageSource`**ProviderName** 매개 변수를 사용 하 여 **NuGet** 공급자에 대해 등록 된 패키지 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-118">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="795dc-119">예제 3: 패키지 공급자에서 원본 가져오기</span><span class="sxs-lookup"><span data-stu-id="795dc-119">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="795dc-120">이 명령은 패키지 공급자를 사용 하 여 패키지 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-120">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="795dc-121">`Get-PackageProvider`**name** 매개 변수를 사용 하 여 공급자 이름인 **NuGet** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-121">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="795dc-122">개체는 파이프라인에서로 전송 됩니다 `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="795dc-122">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="795dc-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="795dc-123">PARAMETERS</span></span>

### <span data-ttu-id="795dc-124">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="795dc-124">-ConfigFile</span></span>

<span data-ttu-id="795dc-125">구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-125">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="795dc-126">-Force</span><span class="sxs-lookup"><span data-stu-id="795dc-126">-Force</span></span>

<span data-ttu-id="795dc-127">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-127">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="795dc-128">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="795dc-128">-ForceBootstrap</span></span>

<span data-ttu-id="795dc-129">이 cmdlet이 **PackageManagement** 가 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-129">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="795dc-130">-Location</span><span class="sxs-lookup"><span data-stu-id="795dc-130">-Location</span></span>

<span data-ttu-id="795dc-131">패키지 관리 원본 또는 리포지토리의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-131">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="795dc-132">-Name</span><span class="sxs-lookup"><span data-stu-id="795dc-132">-Name</span></span>

<span data-ttu-id="795dc-133">패키지 관리 원본의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-133">Specifies the name of a package management source.</span></span>

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

### <span data-ttu-id="795dc-134">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="795dc-134">-PackageManagementProvider</span></span>

<span data-ttu-id="795dc-135">패키지 관리 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-135">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="795dc-136">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="795dc-136">-ProviderName</span></span>

<span data-ttu-id="795dc-137">패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-137">Specifies one or more package provider names.</span></span> <span data-ttu-id="795dc-138">여러 패키지 공급자 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-138">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="795dc-139">사용 `Get-PackageProvider` 가능한 패키지 공급자 목록을 가져오는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-139">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="795dc-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="795dc-140">-PublishLocation</span></span>

<span data-ttu-id="795dc-141">패키지 원본에 대 한 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-141">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="795dc-142">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="795dc-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="795dc-143">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-143">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="795dc-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="795dc-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="795dc-145">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-145">Specifies the script source location.</span></span>

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

### <span data-ttu-id="795dc-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="795dc-146">-SkipValidate</span></span>

<span data-ttu-id="795dc-147">패키지 원본에 대 한 자격 증명의 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-147">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="795dc-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="795dc-148">CommonParameters</span></span>

<span data-ttu-id="795dc-149">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="795dc-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="795dc-150">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="795dc-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="795dc-151">입력</span><span class="sxs-lookup"><span data-stu-id="795dc-151">INPUTS</span></span>

## <span data-ttu-id="795dc-152">출력</span><span class="sxs-lookup"><span data-stu-id="795dc-152">OUTPUTS</span></span>

### <span data-ttu-id="795dc-153">Register-packagesource []</span><span class="sxs-lookup"><span data-stu-id="795dc-153">PackageSource[]</span></span>

<span data-ttu-id="795dc-154">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-154">Specifies one or more package sources.</span></span>

## <span data-ttu-id="795dc-155">참고</span><span class="sxs-lookup"><span data-stu-id="795dc-155">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="795dc-156">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-156">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="795dc-157">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-157">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="795dc-158">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="795dc-158">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="795dc-159">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="795dc-159">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="795dc-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="795dc-160">RELATED LINKS</span></span>

[<span data-ttu-id="795dc-161">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="795dc-161">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="795dc-162">Find-Package</span><span class="sxs-lookup"><span data-stu-id="795dc-162">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="795dc-163">Get-Package</span><span class="sxs-lookup"><span data-stu-id="795dc-163">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="795dc-164">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="795dc-164">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="795dc-165">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="795dc-165">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="795dc-166">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="795dc-166">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="795dc-167">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="795dc-167">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
