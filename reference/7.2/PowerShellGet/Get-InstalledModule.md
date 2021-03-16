---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: 33621a89f846ca277c21aaf0ad8cd788b428da33
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602469"
---
# <span data-ttu-id="b6e83-102">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="b6e83-102">Get-InstalledModule</span></span>

## <span data-ttu-id="b6e83-103">개요</span><span class="sxs-lookup"><span data-stu-id="b6e83-103">SYNOPSIS</span></span>
<span data-ttu-id="b6e83-104">PowerShellGet에 의해 설치 된 컴퓨터의 모듈 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-104">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="b6e83-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b6e83-105">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="b6e83-106">설명</span><span class="sxs-lookup"><span data-stu-id="b6e83-106">DESCRIPTION</span></span>

<span data-ttu-id="b6e83-107">`Get-InstalledModule`Cmdlet은 PowerShellGet을 사용 하 여 컴퓨터에 설치 된 PowerShell 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-107">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="b6e83-108">시스템에 설치 된 모든 모듈을 보려면 `Get-Module -ListAvailable` 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-108">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="b6e83-109">예제</span><span class="sxs-lookup"><span data-stu-id="b6e83-109">EXAMPLES</span></span>

### <span data-ttu-id="b6e83-110">예제 1: 설치 된 모든 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="b6e83-110">Example 1: Get all installed modules</span></span>

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

<span data-ttu-id="b6e83-111">이 명령은 설치 된 모든 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-111">This command gets all installed modules.</span></span>

### <span data-ttu-id="b6e83-112">예제 2: 모듈의 특정 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="b6e83-112">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="b6e83-113">이 명령은 버전 1.0에서 버전 2.0로 AzureRM 모듈의 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-113">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="b6e83-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b6e83-114">PARAMETERS</span></span>

### <span data-ttu-id="b6e83-115">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="b6e83-115">-AllowPrerelease</span></span>

<span data-ttu-id="b6e83-116">시험판으로 표시 된 결과 모듈에를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-116">Includes in the results modules marked as a prerelease.</span></span>

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

### <span data-ttu-id="b6e83-117">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="b6e83-117">-AllVersions</span></span>

<span data-ttu-id="b6e83-118">모듈의 사용 가능한 모든 버전을 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-118">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="b6e83-119">**Allversions)** 매개 변수는 **MinimumVersion**, **MaximumVersion** 또는 **RequiredVersion** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-119">You cannot use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="b6e83-120">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b6e83-120">-MaximumVersion</span></span>

<span data-ttu-id="b6e83-121">가져올 모듈의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-121">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="b6e83-122">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-122">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="b6e83-123">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b6e83-123">-MinimumVersion</span></span>

<span data-ttu-id="b6e83-124">가져올 단일 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-124">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="b6e83-125">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-125">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="b6e83-126">-Name</span><span class="sxs-lookup"><span data-stu-id="b6e83-126">-Name</span></span>

<span data-ttu-id="b6e83-127">가져올 모듈의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-127">Specifies an array of names of modules to get.</span></span>

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

### <span data-ttu-id="b6e83-128">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b6e83-128">-RequiredVersion</span></span>

<span data-ttu-id="b6e83-129">가져올 모듈의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e83-129">Specifies the exact version of a module to get.</span></span>

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

### <span data-ttu-id="b6e83-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b6e83-130">CommonParameters</span></span>

<span data-ttu-id="b6e83-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b6e83-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b6e83-132">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6e83-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b6e83-133">입력</span><span class="sxs-lookup"><span data-stu-id="b6e83-133">INPUTS</span></span>

### <span data-ttu-id="b6e83-134">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b6e83-134">System.String[]</span></span>

### <span data-ttu-id="b6e83-135">System.String</span><span class="sxs-lookup"><span data-stu-id="b6e83-135">System.String</span></span>

## <span data-ttu-id="b6e83-136">출력</span><span class="sxs-lookup"><span data-stu-id="b6e83-136">OUTPUTS</span></span>

### <span data-ttu-id="b6e83-137">PSCustomObject.</span><span class="sxs-lookup"><span data-stu-id="b6e83-137">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="b6e83-138">참고</span><span class="sxs-lookup"><span data-stu-id="b6e83-138">NOTES</span></span>

## <span data-ttu-id="b6e83-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b6e83-139">RELATED LINKS</span></span>
