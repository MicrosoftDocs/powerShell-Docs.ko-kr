---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 8b91c5b950e0e16c4ce0821ee2f96b830dab1fc2
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99605482"
---
# <span data-ttu-id="a793c-102">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a793c-102">Get-PackageSource</span></span>

## <span data-ttu-id="a793c-103">개요</span><span class="sxs-lookup"><span data-stu-id="a793c-103">SYNOPSIS</span></span>
<span data-ttu-id="a793c-104">패키지 공급자에 대해 등록 된 패키지 소스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-104">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="a793c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a793c-105">SYNTAX</span></span>

### <span data-ttu-id="a793c-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="a793c-106">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="a793c-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a793c-107">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="a793c-108">설명</span><span class="sxs-lookup"><span data-stu-id="a793c-108">DESCRIPTION</span></span>

<span data-ttu-id="a793c-109">`Get-PackageSource`Cmdlet은 로컬 컴퓨터의 **PackageManagement** 에 등록 된 패키지 원본 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-109">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="a793c-110">패키지 공급자를 지정 하는 경우 `Get-PackageSource` 지정 된 공급자와 연결 된 원본만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-110">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="a793c-111">그렇지 않으면이 명령은 **PackageManagement** 에 등록 된 모든 패키지 원본을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-111">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="a793c-112">예제</span><span class="sxs-lookup"><span data-stu-id="a793c-112">EXAMPLES</span></span>

### <span data-ttu-id="a793c-113">예제 1: 모든 패키지 소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="a793c-113">Example 1: Get all package sources</span></span>

<span data-ttu-id="a793c-114">`Get-PackageSource`Cmdlet은 로컬 컴퓨터의 **PackageManagement** 에 등록 된 모든 패키지 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-114">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

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

### <span data-ttu-id="a793c-115">예 2: 특정 공급자에 대 한 모든 패키지 원본 가져오기</span><span class="sxs-lookup"><span data-stu-id="a793c-115">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="a793c-116">이 명령은 특정 공급자에 대해 등록 된 패키지 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-116">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="a793c-117">`Get-PackageSource`**ProviderName** 매개 변수를 사용 하 여 **NuGet** 공급자에 대해 등록 된 패키지 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-117">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="a793c-118">예제 3: 패키지 공급자에서 원본 가져오기</span><span class="sxs-lookup"><span data-stu-id="a793c-118">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="a793c-119">이 명령은 패키지 공급자를 사용 하 여 패키지 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-119">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="a793c-120">`Get-PackageProvider`**name** 매개 변수를 사용 하 여 공급자 이름인 **NuGet** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-120">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="a793c-121">개체는 파이프라인에서로 전송 됩니다 `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="a793c-121">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="a793c-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a793c-122">PARAMETERS</span></span>

### <span data-ttu-id="a793c-123">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="a793c-123">-ConfigFile</span></span>

<span data-ttu-id="a793c-124">구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-124">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="a793c-125">-Force</span><span class="sxs-lookup"><span data-stu-id="a793c-125">-Force</span></span>

<span data-ttu-id="a793c-126">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="a793c-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="a793c-127">-ForceBootstrap</span></span>

<span data-ttu-id="a793c-128">이 cmdlet이 **PackageManagement** 가 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-128">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="a793c-129">-Location</span><span class="sxs-lookup"><span data-stu-id="a793c-129">-Location</span></span>

<span data-ttu-id="a793c-130">패키지 관리 원본 또는 리포지토리의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-130">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="a793c-131">-Name</span><span class="sxs-lookup"><span data-stu-id="a793c-131">-Name</span></span>

<span data-ttu-id="a793c-132">패키지 관리 원본의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-132">Specifies the name of a package management source.</span></span>

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

### <span data-ttu-id="a793c-133">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="a793c-133">-PackageManagementProvider</span></span>

<span data-ttu-id="a793c-134">패키지 관리 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-134">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="a793c-135">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="a793c-135">-ProviderName</span></span>

<span data-ttu-id="a793c-136">패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-136">Specifies one or more package provider names.</span></span> <span data-ttu-id="a793c-137">여러 패키지 공급자 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-137">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="a793c-138">사용 `Get-PackageProvider` 가능한 패키지 공급자 목록을 가져오는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-138">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="a793c-139">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="a793c-139">-PublishLocation</span></span>

<span data-ttu-id="a793c-140">패키지 원본에 대 한 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-140">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="a793c-141">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="a793c-141">-ScriptPublishLocation</span></span>

<span data-ttu-id="a793c-142">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-142">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="a793c-143">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="a793c-143">-ScriptSourceLocation</span></span>

<span data-ttu-id="a793c-144">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-144">Specifies the script source location.</span></span>

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

### <span data-ttu-id="a793c-145">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="a793c-145">-SkipValidate</span></span>

<span data-ttu-id="a793c-146">패키지 원본에 대 한 자격 증명의 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-146">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="a793c-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a793c-147">CommonParameters</span></span>

<span data-ttu-id="a793c-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a793c-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a793c-149">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a793c-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a793c-150">입력</span><span class="sxs-lookup"><span data-stu-id="a793c-150">INPUTS</span></span>

## <span data-ttu-id="a793c-151">출력</span><span class="sxs-lookup"><span data-stu-id="a793c-151">OUTPUTS</span></span>

### <span data-ttu-id="a793c-152">Register-packagesource []</span><span class="sxs-lookup"><span data-stu-id="a793c-152">PackageSource[]</span></span>

<span data-ttu-id="a793c-153">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-153">Specifies one or more package sources.</span></span>

## <span data-ttu-id="a793c-154">참고</span><span class="sxs-lookup"><span data-stu-id="a793c-154">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a793c-155">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-155">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a793c-156">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-156">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a793c-157">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a793c-157">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a793c-158">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a793c-158">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="a793c-159">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a793c-159">RELATED LINKS</span></span>

[<span data-ttu-id="a793c-160">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="a793c-160">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="a793c-161">Find-Package</span><span class="sxs-lookup"><span data-stu-id="a793c-161">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="a793c-162">Get-Package</span><span class="sxs-lookup"><span data-stu-id="a793c-162">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="a793c-163">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a793c-163">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="a793c-164">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a793c-164">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="a793c-165">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a793c-165">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="a793c-166">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a793c-166">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
