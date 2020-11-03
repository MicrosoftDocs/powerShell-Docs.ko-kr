---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 02731fb2c45a32d947a951c6ed39c371291f71ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214826"
---
# <span data-ttu-id="bb301-103">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="bb301-103">Import-PackageProvider</span></span>

## <span data-ttu-id="bb301-104">개요</span><span class="sxs-lookup"><span data-stu-id="bb301-104">SYNOPSIS</span></span>
<span data-ttu-id="bb301-105">현재 세션에 패키지 관리 패키지 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-105">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="bb301-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb301-106">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="bb301-107">설명</span><span class="sxs-lookup"><span data-stu-id="bb301-107">DESCRIPTION</span></span>

<span data-ttu-id="bb301-108">`Import-PackageProvider`Cmdlet은 현재 세션에 패키지 공급자를 하나 이상 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-108">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="bb301-109">가져오는 공급자를 로컬 컴퓨터에 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-109">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="bb301-110">사용 가능한 공급자 목록을 가져오려면를 실행 `Get-PackageProvider -ListAvailable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-110">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="bb301-111">패키지 공급자 이름은 해당 모듈 이름과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-111">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="bb301-112">보안상의 이유로 **PackageManagement** 에는를 포함 하는 c # 기반 공급자가 필요 `provider.manifest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-112">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="bb301-113">삽입 된 공급자를 빌드하는 방법에 대 한 자세한 내용은 `provider.manifest` `.csproj` 의 프로젝트 파일을 참조 하십시오 [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .</span><span class="sxs-lookup"><span data-stu-id="bb301-113">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="bb301-114">예제</span><span class="sxs-lookup"><span data-stu-id="bb301-114">EXAMPLES</span></span>

### <span data-ttu-id="bb301-115">예 1: 로컬 컴퓨터에서 패키지 공급자 가져오기</span><span class="sxs-lookup"><span data-stu-id="bb301-115">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="bb301-116">이 명령은 로컬 컴퓨터에 설치 된 Nuget 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-116">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="bb301-117">예제 2: 패키지 공급자의 특정 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="bb301-117">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="bb301-118">이 명령은 특정 버전의 Nuget 패키지 공급자를 찾아서 설치 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-118">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="bb301-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb301-119">PARAMETERS</span></span>

### <span data-ttu-id="bb301-120">-Force</span><span class="sxs-lookup"><span data-stu-id="bb301-120">-Force</span></span>

<span data-ttu-id="bb301-121">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-121">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="bb301-122">패키지 공급자를 다시 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-122">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="bb301-123">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="bb301-123">-ForceBootstrap</span></span>

<span data-ttu-id="bb301-124">이 cmdlet이 패키지 관리 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-124">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="bb301-125">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="bb301-125">-MaximumVersion</span></span>

<span data-ttu-id="bb301-126">가져올 패키지 공급자의 최대 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-126">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="bb301-127">이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` 사용 가능한 가장 높은 버전의 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-127">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

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

### <span data-ttu-id="bb301-128">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="bb301-128">-MinimumVersion</span></span>

<span data-ttu-id="bb301-129">가져올 패키지 공급자의 최소 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-129">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="bb301-130">이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` *MaximumVersion* 매개 변수를 사용 하 여 지정 된 최대 버전을 만족 하는 패키지의 사용 가능한 가장 높은 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-130">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="bb301-131">-Name</span><span class="sxs-lookup"><span data-stu-id="bb301-131">-Name</span></span>

<span data-ttu-id="bb301-132">패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-132">Specifies one or more package provider names.</span></span> <span data-ttu-id="bb301-133">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-133">Wildcards are not permitted.</span></span>

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

### <span data-ttu-id="bb301-134">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="bb301-134">-RequiredVersion</span></span>

<span data-ttu-id="bb301-135">가져올 패키지 공급자의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-135">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="bb301-136">이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` **MaximumVersion** 매개 변수를 사용 하 여 지정 된 최대 버전을 충족 하는 사용 가능한 가장 높은 버전의 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bb301-136">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="bb301-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb301-137">CommonParameters</span></span>

<span data-ttu-id="bb301-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb301-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb301-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb301-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb301-140">입력</span><span class="sxs-lookup"><span data-stu-id="bb301-140">INPUTS</span></span>

### <span data-ttu-id="bb301-141">Install-packageprovider.</span><span class="sxs-lookup"><span data-stu-id="bb301-141">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="bb301-142">에서 반환 하는 **install-packageprovider** 개체를로 파이프 할 수 있습니다 `Get-PackageProvider` `Import-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="bb301-142">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="bb301-143">출력</span><span class="sxs-lookup"><span data-stu-id="bb301-143">OUTPUTS</span></span>

## <span data-ttu-id="bb301-144">참고</span><span class="sxs-lookup"><span data-stu-id="bb301-144">NOTES</span></span>

## <span data-ttu-id="bb301-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bb301-145">RELATED LINKS</span></span>

[<span data-ttu-id="bb301-146">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="bb301-146">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="bb301-147">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="bb301-147">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="bb301-148">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="bb301-148">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="bb301-149">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="bb301-149">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="bb301-150">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="bb301-150">Get-PackageProvider</span></span>](Get-PackageProvider.md)
