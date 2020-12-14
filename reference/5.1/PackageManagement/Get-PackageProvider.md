---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: 66a6bfeda557894e224753018ff9087de9887cc7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892853"
---
# <span data-ttu-id="4f0df-103">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="4f0df-103">Get-PackageProvider</span></span>

## <span data-ttu-id="4f0df-104">개요</span><span class="sxs-lookup"><span data-stu-id="4f0df-104">SYNOPSIS</span></span>
<span data-ttu-id="4f0df-105">패키지 관리에 연결 된 패키지 공급자의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-105">Returns a list of package providers that are connected to Package Management.</span></span>

## <span data-ttu-id="4f0df-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f0df-106">SYNTAX</span></span>

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="4f0df-107">설명</span><span class="sxs-lookup"><span data-stu-id="4f0df-107">DESCRIPTION</span></span>
<span data-ttu-id="4f0df-108">**Install-packageprovider** cmdlet은 패키지 관리에 연결 된 패키지 공급자 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-108">The **Get-PackageProvider** cmdlet returns a list of package providers that are connected to Package Management.</span></span>
<span data-ttu-id="4f0df-109">이러한 공급자의 예로는 PSModule, NuGet 및 Chocolatey이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-109">Examples of these providers include PSModule, NuGet, and Chocolatey.</span></span>
<span data-ttu-id="4f0df-110">하나 이상의 공급자 이름 전체 또는 일부를 기준으로 결과를 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-110">You can filter the results based on all or part of one or more provider names.</span></span>

## <span data-ttu-id="4f0df-111">예제</span><span class="sxs-lookup"><span data-stu-id="4f0df-111">EXAMPLES</span></span>

### <span data-ttu-id="4f0df-112">예제 1: 현재 로드 된 패키지 공급자 모두 가져오기</span><span class="sxs-lookup"><span data-stu-id="4f0df-112">Example 1: Get all currently loaded package providers</span></span>

```
PS C:\> Get-PackageProvider
```

<span data-ttu-id="4f0df-113">이 명령은 로컬 컴퓨터에 현재 로드 된 모든 패키지 공급자 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-113">This command gets a list of all the package providers that are currently loaded on the local computer.</span></span>

### <span data-ttu-id="4f0df-114">예제 2: 사용 가능한 패키지 공급자 모두 가져오기</span><span class="sxs-lookup"><span data-stu-id="4f0df-114">Example 2: Get all available package providers</span></span>

```
PS C:\> Get-PackageProvider -ListAvailable
```

<span data-ttu-id="4f0df-115">이 명령은 로컬 컴퓨터에서 사용할 수 있는 모든 패키지 공급자 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-115">This command gets a list of all package providers that are available on the local computer.</span></span>

### <span data-ttu-id="4f0df-116">예제 3: 동적으로 패키지 공급자 가져오기</span><span class="sxs-lookup"><span data-stu-id="4f0df-116">Example 3: Dynamically get a package provider</span></span>

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

<span data-ttu-id="4f0df-117">이 명령은 컴퓨터에 Chocolatey 공급자가 설치 되어 있지 않은 경우 Chocolatey 공급자를 자동으로 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-117">This command automatically installs the Chocolatey provider if your computer does not have the Chocolatey provider installed.</span></span>

## <span data-ttu-id="4f0df-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f0df-118">PARAMETERS</span></span>

### <span data-ttu-id="4f0df-119">-Force</span><span class="sxs-lookup"><span data-stu-id="4f0df-119">-Force</span></span>
<span data-ttu-id="4f0df-120">이 cmdlet이 강제로 적용할 수 있는이 cmdlet을 사용 하 여 다른 모든 작업을 수행 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-120">Indicates that this cmdlet forces all other actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="4f0df-121">**Install-packageprovider** 에서 *Force* 매개 변수는 *forcebootstrap* 매개 변수와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-121">In **Get-PackageProvider**, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="4f0df-122">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="4f0df-122">-ForceBootstrap</span></span>
<span data-ttu-id="4f0df-123">이 cmdlet이 패키지 관리 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-123">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="4f0df-124">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="4f0df-124">-ListAvailable</span></span>
<span data-ttu-id="4f0df-125">설치 된 모든 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-125">Gets all installed providers.</span></span>
<span data-ttu-id="4f0df-126">**Install-packageprovider** 는 **PSModulePath** 환경 변수에 나열 된 경로 및 패키지 공급자 어셈블리 폴더에 대 한 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-126">**Get-PackageProvider** gets provider in paths listed in the **PSModulePath** environment variable as well as the package provider assembly folders:</span></span>

<span data-ttu-id="4f0df-127">**$env:P rogramFiles\PackageManagement\ProviderAssemblies \* \* \* \* $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span><span class="sxs-lookup"><span data-stu-id="4f0df-127">**$env:ProgramFiles\PackageManagement\ProviderAssemblies\*\*\*\*$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span></span>

<span data-ttu-id="4f0df-128">이 매개 변수를 **사용** 하지 않으면 install-packageprovider는 현재 세션에 로드 된 공급자만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-128">Without this parameter, **Get-PackageProvider** gets only the providers loaded in the current session.</span></span>

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

### <span data-ttu-id="4f0df-129">-Name</span><span class="sxs-lookup"><span data-stu-id="4f0df-129">-Name</span></span>
<span data-ttu-id="4f0df-130">하나 이상의 공급자 이름 또는 일부 공급자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-130">Specifies one or more provider names, or partial provider names.</span></span>
<span data-ttu-id="4f0df-131">여러 공급자 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-131">Separate multiple provider names with commas.</span></span>
<span data-ttu-id="4f0df-132">이 매개 변수에 유효한 값은 패키지와 함께 설치한 공급자의 이름을 포함 합니다. PackageManagement는 **Psmodule** 및 **MSI** 공급자를 비롯 한 기본 공급자 집합과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-132">Valid values for this parameter include names of providers that you have installed with packages; PackageManagement ships with a set of default providers, including the **PSModule** and **MSI** providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f0df-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f0df-133">CommonParameters</span></span>
<span data-ttu-id="4f0df-134">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f0df-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f0df-135">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4f0df-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f0df-136">입력</span><span class="sxs-lookup"><span data-stu-id="4f0df-136">INPUTS</span></span>

## <span data-ttu-id="4f0df-137">출력</span><span class="sxs-lookup"><span data-stu-id="4f0df-137">OUTPUTS</span></span>

### <span data-ttu-id="4f0df-138">Install-packageprovider []</span><span class="sxs-lookup"><span data-stu-id="4f0df-138">PackageProvider[]</span></span>

## <span data-ttu-id="4f0df-139">참고</span><span class="sxs-lookup"><span data-stu-id="4f0df-139">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4f0df-140">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-140">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="4f0df-141">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-141">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="4f0df-142">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f0df-142">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="4f0df-143">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f0df-143">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="4f0df-144">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4f0df-144">RELATED LINKS</span></span>

[<span data-ttu-id="4f0df-145">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="4f0df-145">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="4f0df-146">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4f0df-146">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="4f0df-147">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4f0df-147">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="4f0df-148">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4f0df-148">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
