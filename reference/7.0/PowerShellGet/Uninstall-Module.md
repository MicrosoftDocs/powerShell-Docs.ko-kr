---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 427f50a697186354c889e85bf080189f5ee4af9c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211353"
---
# <span data-ttu-id="e8950-103">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="e8950-103">Uninstall-Module</span></span>

## <span data-ttu-id="e8950-104">개요</span><span class="sxs-lookup"><span data-stu-id="e8950-104">SYNOPSIS</span></span>
<span data-ttu-id="e8950-105">모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-105">Uninstalls a module.</span></span>

## <span data-ttu-id="e8950-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e8950-106">SYNTAX</span></span>

### <span data-ttu-id="e8950-107">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="e8950-107">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="e8950-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="e8950-108">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e8950-109">설명</span><span class="sxs-lookup"><span data-stu-id="e8950-109">DESCRIPTION</span></span>

<span data-ttu-id="e8950-110">`Uninstall-Module`Cmdlet은 로컬 컴퓨터에서 지정 된 모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-110">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="e8950-111">다른 모듈이 종속성으로 포함 된 모듈은 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-111">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="e8950-112">예제</span><span class="sxs-lookup"><span data-stu-id="e8950-112">EXAMPLES</span></span>

### <span data-ttu-id="e8950-113">예제 1: 모듈 제거</span><span class="sxs-lookup"><span data-stu-id="e8950-113">Example 1: Uninstall a module</span></span>

<span data-ttu-id="e8950-114">이 예제에서는 모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-114">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="e8950-115">`Uninstall-Module`**Name** 매개 변수를 사용 하 여 로컬 컴퓨터에서 제거할 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-115">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="e8950-116">예제 2: 파이프라인을 사용 하 여 모듈 제거</span><span class="sxs-lookup"><span data-stu-id="e8950-116">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="e8950-117">이 예제에서는 파이프라인을 사용 하 여 모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-117">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="e8950-118">`Get-InstalledModule`**Name** 매개 변수를 사용 하 여 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-118">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="e8950-119">개체는 파이프라인에서로 전송 되 `Uninstall-Module` 고 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-119">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="e8950-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e8950-120">PARAMETERS</span></span>

### <span data-ttu-id="e8950-121">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="e8950-121">-AllowPrerelease</span></span>

<span data-ttu-id="e8950-122">시험판으로 표시 된 모듈을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-122">Allows you to uninstall a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="e8950-123">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="e8950-123">-AllVersions</span></span>

<span data-ttu-id="e8950-124">모듈의 사용 가능한 모든 버전을 포함 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-124">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="e8950-125">**Allversions)** 매개 변수는 **MinimumVersion** , **MaximumVersion** 또는 **RequiredVersion** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-125">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="e8950-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e8950-126">-Confirm</span></span>

<span data-ttu-id="e8950-127">을 실행 하기 전에 확인 메시지를 표시 `Uninstall-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-127">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="e8950-128">-Force</span><span class="sxs-lookup"><span data-stu-id="e8950-128">-Force</span></span>

<span data-ttu-id="e8950-129">`Uninstall-Module`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-129">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e8950-130">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e8950-130">-InputObject</span></span>

<span data-ttu-id="e8950-131">**PSRepositoryItemInfo** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="e8950-132">예를 들어 `Get-InstalledModule` 변수를 출력 하 고 해당 변수를 **InputObject** 인수로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-132">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="e8950-133">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e8950-133">-MaximumVersion</span></span>

<span data-ttu-id="e8950-134">제거할 모듈의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-134">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="e8950-135">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-135">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="e8950-136">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e8950-136">-MinimumVersion</span></span>

<span data-ttu-id="e8950-137">제거할 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-137">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="e8950-138">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-138">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="e8950-139">-Name</span><span class="sxs-lookup"><span data-stu-id="e8950-139">-Name</span></span>

<span data-ttu-id="e8950-140">제거할 모듈 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-140">Specifies an array of module names to uninstall.</span></span>

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

### <span data-ttu-id="e8950-141">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e8950-141">-RequiredVersion</span></span>

<span data-ttu-id="e8950-142">제거할 모듈의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-142">Specifies the exact version number of the module to uninstall.</span></span>

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

### <span data-ttu-id="e8950-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e8950-143">-WhatIf</span></span>

<span data-ttu-id="e8950-144">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Uninstall-Module` .</span><span class="sxs-lookup"><span data-stu-id="e8950-144">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="e8950-145">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8950-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="e8950-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e8950-146">CommonParameters</span></span>

<span data-ttu-id="e8950-147">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e8950-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e8950-148">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8950-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e8950-149">입력</span><span class="sxs-lookup"><span data-stu-id="e8950-149">INPUTS</span></span>

### <span data-ttu-id="e8950-150">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e8950-150">System.String[]</span></span>

### <span data-ttu-id="e8950-151">System.web. PSObject []</span><span class="sxs-lookup"><span data-stu-id="e8950-151">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="e8950-152">System.String</span><span class="sxs-lookup"><span data-stu-id="e8950-152">System.String</span></span>

## <span data-ttu-id="e8950-153">출력</span><span class="sxs-lookup"><span data-stu-id="e8950-153">OUTPUTS</span></span>

### <span data-ttu-id="e8950-154">System.Object</span><span class="sxs-lookup"><span data-stu-id="e8950-154">System.Object</span></span>

## <span data-ttu-id="e8950-155">참고</span><span class="sxs-lookup"><span data-stu-id="e8950-155">NOTES</span></span>

## <span data-ttu-id="e8950-156">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e8950-156">RELATED LINKS</span></span>

[<span data-ttu-id="e8950-157">Find-Module</span><span class="sxs-lookup"><span data-stu-id="e8950-157">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="e8950-158">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="e8950-158">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="e8950-159">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="e8950-159">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="e8950-160">Save-Module</span><span class="sxs-lookup"><span data-stu-id="e8950-160">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="e8950-161">Update-Module</span><span class="sxs-lookup"><span data-stu-id="e8950-161">Update-Module</span></span>](Update-Module.md)
