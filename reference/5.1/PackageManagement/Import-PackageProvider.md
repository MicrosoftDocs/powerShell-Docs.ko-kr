---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 1349b0c9e675e36a78f9a9d8d789ea73192d37ec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892834"
---
# <span data-ttu-id="349bd-103">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="349bd-103">Import-PackageProvider</span></span>

## <span data-ttu-id="349bd-104">개요</span><span class="sxs-lookup"><span data-stu-id="349bd-104">SYNOPSIS</span></span>
<span data-ttu-id="349bd-105">현재 세션에 패키지 관리 패키지 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-105">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="349bd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="349bd-106">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="349bd-107">설명</span><span class="sxs-lookup"><span data-stu-id="349bd-107">DESCRIPTION</span></span>

<span data-ttu-id="349bd-108">`Import-PackageProvider`Cmdlet은 현재 세션에 패키지 공급자를 하나 이상 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-108">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="349bd-109">가져오는 공급자를 로컬 컴퓨터에 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-109">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="349bd-110">사용 가능한 공급자 목록을 가져오려면를 실행 `Get-PackageProvider -ListAvailable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-110">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="349bd-111">패키지 공급자 이름은 해당 모듈 이름과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-111">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="349bd-112">보안상의 이유로 **PackageManagement** 에는를 포함 하는 c # 기반 공급자가 필요 `provider.manifest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-112">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="349bd-113">삽입 된 공급자를 빌드하는 방법에 대 한 자세한 내용은 `provider.manifest` `.csproj` 의 프로젝트 파일을 참조 하십시오 [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .</span><span class="sxs-lookup"><span data-stu-id="349bd-113">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="349bd-114">예제</span><span class="sxs-lookup"><span data-stu-id="349bd-114">EXAMPLES</span></span>

### <span data-ttu-id="349bd-115">예 1: 로컬 컴퓨터에서 패키지 공급자 가져오기</span><span class="sxs-lookup"><span data-stu-id="349bd-115">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="349bd-116">이 명령은 로컬 컴퓨터에 설치 된 Nuget 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-116">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="349bd-117">예제 2: 패키지 공급자의 특정 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="349bd-117">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="349bd-118">이 명령은 특정 버전의 Nuget 패키지 공급자를 찾아서 설치 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-118">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="349bd-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="349bd-119">PARAMETERS</span></span>

### <span data-ttu-id="349bd-120">-Force</span><span class="sxs-lookup"><span data-stu-id="349bd-120">-Force</span></span>

<span data-ttu-id="349bd-121">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-121">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="349bd-122">패키지 공급자를 다시 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-122">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="349bd-123">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="349bd-123">-ForceBootstrap</span></span>

<span data-ttu-id="349bd-124">이 cmdlet이 패키지 관리 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-124">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="349bd-125">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="349bd-125">-MaximumVersion</span></span>

<span data-ttu-id="349bd-126">가져올 패키지 공급자의 최대 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-126">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="349bd-127">이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` 사용 가능한 가장 높은 버전의 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-127">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

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

### <span data-ttu-id="349bd-128">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="349bd-128">-MinimumVersion</span></span>

<span data-ttu-id="349bd-129">가져올 패키지 공급자의 최소 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-129">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="349bd-130">이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` *MaximumVersion* 매개 변수를 사용 하 여 지정 된 최대 버전을 만족 하는 패키지의 사용 가능한 가장 높은 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-130">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="349bd-131">-Name</span><span class="sxs-lookup"><span data-stu-id="349bd-131">-Name</span></span>

<span data-ttu-id="349bd-132">패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-132">Specifies one or more package provider names.</span></span> <span data-ttu-id="349bd-133">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-133">Wildcards are not permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="349bd-134">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="349bd-134">-RequiredVersion</span></span>

<span data-ttu-id="349bd-135">가져올 패키지 공급자의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-135">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="349bd-136">이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` **MaximumVersion** 매개 변수를 사용 하 여 지정 된 최대 버전을 충족 하는 사용 가능한 가장 높은 버전의 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-136">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="349bd-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="349bd-137">CommonParameters</span></span>

<span data-ttu-id="349bd-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="349bd-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="349bd-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="349bd-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="349bd-140">입력</span><span class="sxs-lookup"><span data-stu-id="349bd-140">INPUTS</span></span>

### <span data-ttu-id="349bd-141">Install-packageprovider.</span><span class="sxs-lookup"><span data-stu-id="349bd-141">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="349bd-142">에서 반환 하는 **install-packageprovider** 개체를로 파이프 할 수 있습니다 `Get-PackageProvider` `Import-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="349bd-142">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="349bd-143">출력</span><span class="sxs-lookup"><span data-stu-id="349bd-143">OUTPUTS</span></span>

## <span data-ttu-id="349bd-144">참고</span><span class="sxs-lookup"><span data-stu-id="349bd-144">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="349bd-145">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-145">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="349bd-146">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-146">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="349bd-147">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="349bd-147">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="349bd-148">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="349bd-148">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="349bd-149">관련 링크</span><span class="sxs-lookup"><span data-stu-id="349bd-149">RELATED LINKS</span></span>

[<span data-ttu-id="349bd-150">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="349bd-150">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="349bd-151">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="349bd-151">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="349bd-152">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="349bd-152">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="349bd-153">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="349bd-153">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="349bd-154">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="349bd-154">Get-PackageProvider</span></span>](Get-PackageProvider.md)
