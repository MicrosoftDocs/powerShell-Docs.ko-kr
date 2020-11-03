---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 72cdbd26a909e4be33fa32f67019e4c1f02ce3de
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215177"
---
# <span data-ttu-id="c9f69-103">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="c9f69-103">Uninstall-Module</span></span>

## <span data-ttu-id="c9f69-104">개요</span><span class="sxs-lookup"><span data-stu-id="c9f69-104">SYNOPSIS</span></span>
<span data-ttu-id="c9f69-105">모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-105">Uninstalls a module.</span></span>

## <span data-ttu-id="c9f69-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c9f69-106">SYNTAX</span></span>

### <span data-ttu-id="c9f69-107">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="c9f69-107">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="c9f69-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="c9f69-108">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c9f69-109">설명</span><span class="sxs-lookup"><span data-stu-id="c9f69-109">DESCRIPTION</span></span>

<span data-ttu-id="c9f69-110">`Uninstall-Module`Cmdlet은 로컬 컴퓨터에서 지정 된 모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-110">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="c9f69-111">다른 모듈이 종속성으로 포함 된 모듈은 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-111">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="c9f69-112">예제</span><span class="sxs-lookup"><span data-stu-id="c9f69-112">EXAMPLES</span></span>

### <span data-ttu-id="c9f69-113">예제 1: 모듈 제거</span><span class="sxs-lookup"><span data-stu-id="c9f69-113">Example 1: Uninstall a module</span></span>

<span data-ttu-id="c9f69-114">이 예제에서는 모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-114">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="c9f69-115">`Uninstall-Module`**Name** 매개 변수를 사용 하 여 로컬 컴퓨터에서 제거할 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-115">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="c9f69-116">예제 2: 파이프라인을 사용 하 여 모듈 제거</span><span class="sxs-lookup"><span data-stu-id="c9f69-116">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="c9f69-117">이 예제에서는 파이프라인을 사용 하 여 모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-117">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="c9f69-118">`Get-InstalledModule`**Name** 매개 변수를 사용 하 여 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-118">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="c9f69-119">개체는 파이프라인에서로 전송 되 `Uninstall-Module` 고 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-119">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="c9f69-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c9f69-120">PARAMETERS</span></span>

### <span data-ttu-id="c9f69-121">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="c9f69-121">-AllowPrerelease</span></span>

<span data-ttu-id="c9f69-122">시험판으로 표시 된 모듈을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-122">Allows you to uninstall a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c9f69-123">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="c9f69-123">-AllVersions</span></span>

<span data-ttu-id="c9f69-124">모듈의 사용 가능한 모든 버전을 포함 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-124">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="c9f69-125">**Allversions)** 매개 변수는 **MinimumVersion** , **MaximumVersion** 또는 **RequiredVersion** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-125">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c9f69-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c9f69-126">-Confirm</span></span>

<span data-ttu-id="c9f69-127">을 실행 하기 전에 확인 메시지를 표시 `Uninstall-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-127">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="c9f69-128">-Force</span><span class="sxs-lookup"><span data-stu-id="c9f69-128">-Force</span></span>

<span data-ttu-id="c9f69-129">`Uninstall-Module`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-129">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="c9f69-130">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c9f69-130">-InputObject</span></span>

<span data-ttu-id="c9f69-131">**PSRepositoryItemInfo** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="c9f69-132">예를 들어 `Get-InstalledModule` 변수를 출력 하 고 해당 변수를 **InputObject** 인수로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-132">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c9f69-133">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="c9f69-133">-MaximumVersion</span></span>

<span data-ttu-id="c9f69-134">제거할 모듈의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-134">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="c9f69-135">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-135">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c9f69-136">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c9f69-136">-MinimumVersion</span></span>

<span data-ttu-id="c9f69-137">제거할 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-137">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="c9f69-138">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-138">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c9f69-139">-Name</span><span class="sxs-lookup"><span data-stu-id="c9f69-139">-Name</span></span>

<span data-ttu-id="c9f69-140">제거할 모듈 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-140">Specifies an array of module names to uninstall.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c9f69-141">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c9f69-141">-RequiredVersion</span></span>

<span data-ttu-id="c9f69-142">제거할 모듈의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-142">Specifies the exact version number of the module to uninstall.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c9f69-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c9f69-143">-WhatIf</span></span>

<span data-ttu-id="c9f69-144">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Uninstall-Module` .</span><span class="sxs-lookup"><span data-stu-id="c9f69-144">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="c9f69-145">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="c9f69-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c9f69-146">CommonParameters</span></span>

<span data-ttu-id="c9f69-147">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c9f69-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c9f69-148">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9f69-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c9f69-149">입력</span><span class="sxs-lookup"><span data-stu-id="c9f69-149">INPUTS</span></span>

### <span data-ttu-id="c9f69-150">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="c9f69-150">PSRepositoryItemInfo</span></span>

<span data-ttu-id="c9f69-151">`Uninstall-Module` 파이프라인에서 **PSRepositoryItemInfo** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f69-151">`Uninstall-Module` accepts **PSRepositoryItemInfo** objects from the pipeline.</span></span>

## <span data-ttu-id="c9f69-152">출력</span><span class="sxs-lookup"><span data-stu-id="c9f69-152">OUTPUTS</span></span>

## <span data-ttu-id="c9f69-153">참고</span><span class="sxs-lookup"><span data-stu-id="c9f69-153">NOTES</span></span>

## <span data-ttu-id="c9f69-154">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c9f69-154">RELATED LINKS</span></span>

[<span data-ttu-id="c9f69-155">Find-Module</span><span class="sxs-lookup"><span data-stu-id="c9f69-155">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="c9f69-156">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="c9f69-156">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="c9f69-157">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="c9f69-157">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="c9f69-158">Save-Module</span><span class="sxs-lookup"><span data-stu-id="c9f69-158">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="c9f69-159">Update-Module</span><span class="sxs-lookup"><span data-stu-id="c9f69-159">Update-Module</span></span>](Update-Module.md)
