---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: fd8325f1a68755ee1b5c05719a04e71b22a7e9fd
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99601256"
---
# <span data-ttu-id="9e5fe-102">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="9e5fe-102">Get-PackageProvider</span></span>

## <span data-ttu-id="9e5fe-103">개요</span><span class="sxs-lookup"><span data-stu-id="9e5fe-103">SYNOPSIS</span></span>
<span data-ttu-id="9e5fe-104">패키지 관리에 연결 된 패키지 공급자의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-104">Returns a list of package providers that are connected to Package Management.</span></span>

## <span data-ttu-id="9e5fe-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9e5fe-105">SYNTAX</span></span>

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="9e5fe-106">설명</span><span class="sxs-lookup"><span data-stu-id="9e5fe-106">DESCRIPTION</span></span>

<span data-ttu-id="9e5fe-107">**Install-packageprovider** cmdlet은 패키지 관리에 연결 된 패키지 공급자 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-107">The **Get-PackageProvider** cmdlet returns a list of package providers that are connected to Package Management.</span></span>
<span data-ttu-id="9e5fe-108">이러한 공급자의 예로는 PSModule, NuGet 및 Chocolatey이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-108">Examples of these providers include PSModule, NuGet, and Chocolatey.</span></span>
<span data-ttu-id="9e5fe-109">하나 이상의 공급자 이름 전체 또는 일부를 기준으로 결과를 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-109">You can filter the results based on all or part of one or more provider names.</span></span>

## <span data-ttu-id="9e5fe-110">예제</span><span class="sxs-lookup"><span data-stu-id="9e5fe-110">EXAMPLES</span></span>

### <span data-ttu-id="9e5fe-111">예제 1: 현재 로드 된 패키지 공급자 모두 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e5fe-111">Example 1: Get all currently loaded package providers</span></span>

```
PS C:\> Get-PackageProvider
```

<span data-ttu-id="9e5fe-112">이 명령은 로컬 컴퓨터에 현재 로드 된 모든 패키지 공급자 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-112">This command gets a list of all the package providers that are currently loaded on the local computer.</span></span>

### <span data-ttu-id="9e5fe-113">예제 2: 사용 가능한 패키지 공급자 모두 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e5fe-113">Example 2: Get all available package providers</span></span>

```
PS C:\> Get-PackageProvider -ListAvailable
```

<span data-ttu-id="9e5fe-114">이 명령은 로컬 컴퓨터에서 사용할 수 있는 모든 패키지 공급자 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-114">This command gets a list of all package providers that are available on the local computer.</span></span>

### <span data-ttu-id="9e5fe-115">예제 3: 동적으로 패키지 공급자 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e5fe-115">Example 3: Dynamically get a package provider</span></span>

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

<span data-ttu-id="9e5fe-116">이 명령은 컴퓨터에 Chocolatey 공급자가 설치 되어 있지 않은 경우 Chocolatey 공급자를 자동으로 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-116">This command automatically installs the Chocolatey provider if your computer does not have the Chocolatey provider installed.</span></span>

## <span data-ttu-id="9e5fe-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9e5fe-117">PARAMETERS</span></span>

### <span data-ttu-id="9e5fe-118">-Force</span><span class="sxs-lookup"><span data-stu-id="9e5fe-118">-Force</span></span>

<span data-ttu-id="9e5fe-119">이 cmdlet이 강제로 적용할 수 있는이 cmdlet을 사용 하 여 다른 모든 작업을 수행 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-119">Indicates that this cmdlet forces all other actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="9e5fe-120">**Install-packageprovider** 에서 *Force* 매개 변수는 *forcebootstrap* 매개 변수와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-120">In **Get-PackageProvider**, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="9e5fe-121">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="9e5fe-121">-ForceBootstrap</span></span>

<span data-ttu-id="9e5fe-122">이 cmdlet이 패키지 관리 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-122">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="9e5fe-123">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="9e5fe-123">-ListAvailable</span></span>

<span data-ttu-id="9e5fe-124">설치 된 모든 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-124">Gets all installed providers.</span></span>
<span data-ttu-id="9e5fe-125">**Install-packageprovider** 는 **PSModulePath** 환경 변수에 나열 된 경로 및 패키지 공급자 어셈블리 폴더에 대 한 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-125">**Get-PackageProvider** gets provider in paths listed in the **PSModulePath** environment variable as well as the package provider assembly folders:</span></span>

<span data-ttu-id="9e5fe-126">**$env:P rogramFiles\PackageManagement\ProviderAssemblies \* \* \* \* $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span><span class="sxs-lookup"><span data-stu-id="9e5fe-126">**$env:ProgramFiles\PackageManagement\ProviderAssemblies\*\*\*\*$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span></span>

<span data-ttu-id="9e5fe-127">이 매개 변수를 **사용** 하지 않으면 install-packageprovider는 현재 세션에 로드 된 공급자만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-127">Without this parameter, **Get-PackageProvider** gets only the providers loaded in the current session.</span></span>

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

### <span data-ttu-id="9e5fe-128">-Name</span><span class="sxs-lookup"><span data-stu-id="9e5fe-128">-Name</span></span>

<span data-ttu-id="9e5fe-129">하나 이상의 공급자 이름 또는 일부 공급자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-129">Specifies one or more provider names, or partial provider names.</span></span>
<span data-ttu-id="9e5fe-130">여러 공급자 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-130">Separate multiple provider names with commas.</span></span>
<span data-ttu-id="9e5fe-131">이 매개 변수에 유효한 값은 패키지와 함께 설치한 공급자의 이름을 포함 합니다. PackageManagement는 **Psmodule** 및 **MSI** 공급자를 비롯 한 기본 공급자 집합과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-131">Valid values for this parameter include names of providers that you have installed with packages; PackageManagement ships with a set of default providers, including the **PSModule** and **MSI** providers.</span></span>

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

### <span data-ttu-id="9e5fe-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e5fe-132">CommonParameters</span></span>

<span data-ttu-id="9e5fe-133">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e5fe-134">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e5fe-135">입력</span><span class="sxs-lookup"><span data-stu-id="9e5fe-135">INPUTS</span></span>

## <span data-ttu-id="9e5fe-136">출력</span><span class="sxs-lookup"><span data-stu-id="9e5fe-136">OUTPUTS</span></span>

### <span data-ttu-id="9e5fe-137">Install-packageprovider []</span><span class="sxs-lookup"><span data-stu-id="9e5fe-137">PackageProvider[]</span></span>

## <span data-ttu-id="9e5fe-138">참고</span><span class="sxs-lookup"><span data-stu-id="9e5fe-138">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e5fe-139">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-139">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="9e5fe-140">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-140">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="9e5fe-141">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-141">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="9e5fe-142">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e5fe-142">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="9e5fe-143">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9e5fe-143">RELATED LINKS</span></span>

[<span data-ttu-id="9e5fe-144">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="9e5fe-144">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="9e5fe-145">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="9e5fe-145">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="9e5fe-146">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="9e5fe-146">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="9e5fe-147">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="9e5fe-147">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
