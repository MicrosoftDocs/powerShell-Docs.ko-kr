---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 6c19d1cbc7b7e4dc37e24c466f83efae688f3cec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99604987"
---
# <span data-ttu-id="ab31d-102">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="ab31d-102">Import-PackageProvider</span></span>

## <span data-ttu-id="ab31d-103">개요</span><span class="sxs-lookup"><span data-stu-id="ab31d-103">SYNOPSIS</span></span>
<span data-ttu-id="ab31d-104">현재 세션에 패키지 관리 패키지 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-104">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="ab31d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ab31d-105">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="ab31d-106">설명</span><span class="sxs-lookup"><span data-stu-id="ab31d-106">DESCRIPTION</span></span>

<span data-ttu-id="ab31d-107">`Import-PackageProvider`Cmdlet은 현재 세션에 패키지 공급자를 하나 이상 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-107">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="ab31d-108">가져오는 공급자를 로컬 컴퓨터에 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-108">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="ab31d-109">사용 가능한 공급자 목록을 가져오려면를 실행 `Get-PackageProvider -ListAvailable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-109">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="ab31d-110">패키지 공급자 이름은 해당 모듈 이름과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-110">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="ab31d-111">보안상의 이유로 **PackageManagement** 에는를 포함 하는 c # 기반 공급자가 필요 `provider.manifest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-111">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="ab31d-112">삽입 된 공급자를 빌드하는 방법에 대 한 자세한 내용은 `provider.manifest` `.csproj` 의 프로젝트 파일을 참조 하십시오 [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .</span><span class="sxs-lookup"><span data-stu-id="ab31d-112">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="ab31d-113">예제</span><span class="sxs-lookup"><span data-stu-id="ab31d-113">EXAMPLES</span></span>

### <span data-ttu-id="ab31d-114">예 1: 로컬 컴퓨터에서 패키지 공급자 가져오기</span><span class="sxs-lookup"><span data-stu-id="ab31d-114">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="ab31d-115">이 명령은 로컬 컴퓨터에 설치 된 Nuget 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-115">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="ab31d-116">예제 2: 패키지 공급자의 특정 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="ab31d-116">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="ab31d-117">이 명령은 특정 버전의 Nuget 패키지 공급자를 찾아서 설치 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-117">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="ab31d-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ab31d-118">PARAMETERS</span></span>

### <span data-ttu-id="ab31d-119">-Force</span><span class="sxs-lookup"><span data-stu-id="ab31d-119">-Force</span></span>

<span data-ttu-id="ab31d-120">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-120">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="ab31d-121">패키지 공급자를 다시 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-121">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="ab31d-122">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="ab31d-122">-ForceBootstrap</span></span>

<span data-ttu-id="ab31d-123">이 cmdlet이 패키지 관리 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-123">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="ab31d-124">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ab31d-124">-MaximumVersion</span></span>

<span data-ttu-id="ab31d-125">가져올 패키지 공급자의 최대 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-125">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="ab31d-126">이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` 사용 가능한 가장 높은 버전의 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-126">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

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

### <span data-ttu-id="ab31d-127">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="ab31d-127">-MinimumVersion</span></span>

<span data-ttu-id="ab31d-128">가져올 패키지 공급자의 최소 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-128">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="ab31d-129">이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` *MaximumVersion* 매개 변수를 사용 하 여 지정 된 최대 버전을 만족 하는 패키지의 사용 가능한 가장 높은 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-129">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="ab31d-130">-Name</span><span class="sxs-lookup"><span data-stu-id="ab31d-130">-Name</span></span>

<span data-ttu-id="ab31d-131">패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-131">Specifies one or more package provider names.</span></span> <span data-ttu-id="ab31d-132">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-132">Wildcards are not permitted.</span></span>

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

### <span data-ttu-id="ab31d-133">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ab31d-133">-RequiredVersion</span></span>

<span data-ttu-id="ab31d-134">가져올 패키지 공급자의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-134">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="ab31d-135">이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` **MaximumVersion** 매개 변수를 사용 하 여 지정 된 최대 버전을 충족 하는 사용 가능한 가장 높은 버전의 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-135">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="ab31d-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab31d-136">CommonParameters</span></span>

<span data-ttu-id="ab31d-137">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab31d-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab31d-138">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab31d-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab31d-139">입력</span><span class="sxs-lookup"><span data-stu-id="ab31d-139">INPUTS</span></span>

### <span data-ttu-id="ab31d-140">Install-packageprovider.</span><span class="sxs-lookup"><span data-stu-id="ab31d-140">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="ab31d-141">에서 반환 하는 **install-packageprovider** 개체를로 파이프 할 수 있습니다 `Get-PackageProvider` `Import-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="ab31d-141">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="ab31d-142">출력</span><span class="sxs-lookup"><span data-stu-id="ab31d-142">OUTPUTS</span></span>

## <span data-ttu-id="ab31d-143">참고</span><span class="sxs-lookup"><span data-stu-id="ab31d-143">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab31d-144">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-144">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="ab31d-145">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-145">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="ab31d-146">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ab31d-146">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="ab31d-147">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab31d-147">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="ab31d-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ab31d-148">RELATED LINKS</span></span>

[<span data-ttu-id="ab31d-149">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="ab31d-149">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="ab31d-150">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ab31d-150">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="ab31d-151">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ab31d-151">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="ab31d-152">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ab31d-152">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="ab31d-153">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="ab31d-153">Get-PackageProvider</span></span>](Get-PackageProvider.md)
