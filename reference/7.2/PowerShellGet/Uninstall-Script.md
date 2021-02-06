---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 2cd8b51e1d4ef11a0a5f9e3542ff89e094854d8c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600446"
---
# <span data-ttu-id="dd7af-102">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="dd7af-102">Uninstall-Script</span></span>

## <span data-ttu-id="dd7af-103">개요</span><span class="sxs-lookup"><span data-stu-id="dd7af-103">SYNOPSIS</span></span>
<span data-ttu-id="dd7af-104">스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-104">Uninstalls a script.</span></span>

## <span data-ttu-id="dd7af-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dd7af-105">SYNTAX</span></span>

### <span data-ttu-id="dd7af-106">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="dd7af-106">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dd7af-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="dd7af-107">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dd7af-108">설명</span><span class="sxs-lookup"><span data-stu-id="dd7af-108">DESCRIPTION</span></span>

<span data-ttu-id="dd7af-109">`Uninstall-Script`Cmdlet은 로컬 컴퓨터에서 지정 된 스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-109">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="dd7af-110">예제</span><span class="sxs-lookup"><span data-stu-id="dd7af-110">EXAMPLES</span></span>

### <span data-ttu-id="dd7af-111">예제 1: 스크립트 제거</span><span class="sxs-lookup"><span data-stu-id="dd7af-111">Example 1: Uninstall a script</span></span>

<span data-ttu-id="dd7af-112">이 예제에서는 스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-112">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="dd7af-113">`Uninstall-Script`**Name** 매개 변수를 사용 하 여 로컬 컴퓨터에서 제거할 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-113">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="dd7af-114">예제 2: 파이프라인을 사용 하 여 스크립트 제거</span><span class="sxs-lookup"><span data-stu-id="dd7af-114">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="dd7af-115">이 예제에서는 파이프라인을 사용 하 여 스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-115">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="dd7af-116">`Get-InstalledScript`**Name** 매개 변수를 사용 하 여 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-116">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="dd7af-117">개체가 파이프라인으로 전송 되 `Uninstall-Script` 고 스크립트가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-117">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="dd7af-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dd7af-118">PARAMETERS</span></span>

### <span data-ttu-id="dd7af-119">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="dd7af-119">-AllowPrerelease</span></span>

<span data-ttu-id="dd7af-120">시험판으로 표시 된 스크립트를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-120">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="dd7af-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dd7af-121">-Confirm</span></span>

<span data-ttu-id="dd7af-122">실행 하기 전에 확인 메시지를 표시 `Uninstall-Script` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-122">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="dd7af-123">-Force</span><span class="sxs-lookup"><span data-stu-id="dd7af-123">-Force</span></span>

<span data-ttu-id="dd7af-124">`Uninstall-Script`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-124">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="dd7af-125">-InputObject</span><span class="sxs-lookup"><span data-stu-id="dd7af-125">-InputObject</span></span>

<span data-ttu-id="dd7af-126">**PSRepositoryItemInfo** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-126">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="dd7af-127">예를 들어 `Get-InstalledScript` 변수를 출력 하 고 해당 변수를 **InputObject** 인수로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-127">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="dd7af-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="dd7af-128">-MaximumVersion</span></span>

<span data-ttu-id="dd7af-129">제거할 스크립트의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-129">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="dd7af-130">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="dd7af-131">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="dd7af-131">-MinimumVersion</span></span>

<span data-ttu-id="dd7af-132">제거할 스크립트의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-132">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="dd7af-133">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-133">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="dd7af-134">-Name</span><span class="sxs-lookup"><span data-stu-id="dd7af-134">-Name</span></span>

<span data-ttu-id="dd7af-135">제거할 스크립트 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-135">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="dd7af-136">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="dd7af-136">-RequiredVersion</span></span>

<span data-ttu-id="dd7af-137">제거할 스크립트의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-137">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="dd7af-138">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dd7af-138">-WhatIf</span></span>

<span data-ttu-id="dd7af-139">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Uninstall-Script` .</span><span class="sxs-lookup"><span data-stu-id="dd7af-139">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="dd7af-140">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd7af-140">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="dd7af-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dd7af-141">CommonParameters</span></span>

<span data-ttu-id="dd7af-142">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dd7af-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dd7af-143">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd7af-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dd7af-144">입력</span><span class="sxs-lookup"><span data-stu-id="dd7af-144">INPUTS</span></span>

### <span data-ttu-id="dd7af-145">System.String[]</span><span class="sxs-lookup"><span data-stu-id="dd7af-145">System.String[]</span></span>

### <span data-ttu-id="dd7af-146">System.web. PSObject []</span><span class="sxs-lookup"><span data-stu-id="dd7af-146">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="dd7af-147">System.String</span><span class="sxs-lookup"><span data-stu-id="dd7af-147">System.String</span></span>

## <span data-ttu-id="dd7af-148">출력</span><span class="sxs-lookup"><span data-stu-id="dd7af-148">OUTPUTS</span></span>

### <span data-ttu-id="dd7af-149">System.Object</span><span class="sxs-lookup"><span data-stu-id="dd7af-149">System.Object</span></span>

## <span data-ttu-id="dd7af-150">참고</span><span class="sxs-lookup"><span data-stu-id="dd7af-150">NOTES</span></span>

## <span data-ttu-id="dd7af-151">관련 링크</span><span class="sxs-lookup"><span data-stu-id="dd7af-151">RELATED LINKS</span></span>

[<span data-ttu-id="dd7af-152">Find-Script</span><span class="sxs-lookup"><span data-stu-id="dd7af-152">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="dd7af-153">Install-Script</span><span class="sxs-lookup"><span data-stu-id="dd7af-153">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="dd7af-154">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="dd7af-154">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="dd7af-155">Save-Script</span><span class="sxs-lookup"><span data-stu-id="dd7af-155">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="dd7af-156">Update-Script</span><span class="sxs-lookup"><span data-stu-id="dd7af-156">Update-Script</span></span>](Update-Script.md)

