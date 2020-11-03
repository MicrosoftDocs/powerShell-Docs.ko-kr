---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: 199c257633a6d85a305a5155fdb4e61debcdf322
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215994"
---
# <span data-ttu-id="ff8e3-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="ff8e3-103">Get-InstalledModule</span></span>

## <span data-ttu-id="ff8e3-104">개요</span><span class="sxs-lookup"><span data-stu-id="ff8e3-104">SYNOPSIS</span></span>
<span data-ttu-id="ff8e3-105">PowerShellGet에 의해 설치 된 컴퓨터의 모듈 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-105">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="ff8e3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ff8e3-106">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="ff8e3-107">설명</span><span class="sxs-lookup"><span data-stu-id="ff8e3-107">DESCRIPTION</span></span>

<span data-ttu-id="ff8e3-108">`Get-InstalledModule`Cmdlet은 PowerShellGet을 사용 하 여 컴퓨터에 설치 된 PowerShell 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-108">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="ff8e3-109">시스템에 설치 된 모든 모듈을 보려면 `Get-Module -ListAvailable` 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-109">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="ff8e3-110">예제</span><span class="sxs-lookup"><span data-stu-id="ff8e3-110">EXAMPLES</span></span>

### <span data-ttu-id="ff8e3-111">예제 1: 설치 된 모든 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="ff8e3-111">Example 1: Get all installed modules</span></span>

```powershell
Get-InstalledModule
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
2.0.0      PSGTEST-UploadMultipleVersionOfP... Module     GalleryINT     Module for DAC functionality
1.3.5      AzureAutomationDebug                Module     PSGallery      Module for debugging Azure Automation runbooks, emulating AA native cmdlets
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="ff8e3-112">이 명령은 설치 된 모든 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-112">This command gets all installed modules.</span></span>

### <span data-ttu-id="ff8e3-113">예제 2: 모듈의 특정 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="ff8e3-113">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="ff8e3-114">이 명령은 버전 1.0에서 버전 2.0로 AzureRM 모듈의 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-114">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="ff8e3-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ff8e3-115">PARAMETERS</span></span>

### <span data-ttu-id="ff8e3-116">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="ff8e3-116">-AllowPrerelease</span></span>

<span data-ttu-id="ff8e3-117">시험판으로 표시 된 결과 모듈에를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-117">Includes in the results modules marked as a prerelease.</span></span>

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

### <span data-ttu-id="ff8e3-118">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="ff8e3-118">-AllVersions</span></span>

<span data-ttu-id="ff8e3-119">모듈의 사용 가능한 모든 버전을 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-119">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="ff8e3-120">**Allversions)** 매개 변수는 **MinimumVersion** , **MaximumVersion** 또는 **RequiredVersion** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-120">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="ff8e3-121">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ff8e3-121">-MaximumVersion</span></span>

<span data-ttu-id="ff8e3-122">가져올 모듈의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-122">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="ff8e3-123">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-123">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ff8e3-124">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="ff8e3-124">-MinimumVersion</span></span>

<span data-ttu-id="ff8e3-125">가져올 단일 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-125">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="ff8e3-126">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-126">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ff8e3-127">-Name</span><span class="sxs-lookup"><span data-stu-id="ff8e3-127">-Name</span></span>

<span data-ttu-id="ff8e3-128">가져올 모듈의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-128">Specifies an array of names of modules to get.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ff8e3-129">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ff8e3-129">-RequiredVersion</span></span>

<span data-ttu-id="ff8e3-130">가져올 모듈의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-130">Specifies the exact version of a module to get.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ff8e3-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ff8e3-131">CommonParameters</span></span>

<span data-ttu-id="ff8e3-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ff8e3-133">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-133">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ff8e3-134">입력</span><span class="sxs-lookup"><span data-stu-id="ff8e3-134">INPUTS</span></span>

### <span data-ttu-id="ff8e3-135">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ff8e3-135">System.String[]</span></span>

### <span data-ttu-id="ff8e3-136">System.String</span><span class="sxs-lookup"><span data-stu-id="ff8e3-136">System.String</span></span>

## <span data-ttu-id="ff8e3-137">출력</span><span class="sxs-lookup"><span data-stu-id="ff8e3-137">OUTPUTS</span></span>

### <span data-ttu-id="ff8e3-138">PSCustomObject.</span><span class="sxs-lookup"><span data-stu-id="ff8e3-138">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="ff8e3-139">참고</span><span class="sxs-lookup"><span data-stu-id="ff8e3-139">NOTES</span></span>

## <span data-ttu-id="ff8e3-140">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ff8e3-140">RELATED LINKS</span></span>
