---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 26e32cc3d7330026bd77d33ba6574818559d1c6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212617"
---
# <span data-ttu-id="85f88-103">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="85f88-103">Uninstall-Script</span></span>

## <span data-ttu-id="85f88-104">개요</span><span class="sxs-lookup"><span data-stu-id="85f88-104">SYNOPSIS</span></span>
<span data-ttu-id="85f88-105">스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-105">Uninstalls a script.</span></span>

## <span data-ttu-id="85f88-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="85f88-106">SYNTAX</span></span>

### <span data-ttu-id="85f88-107">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="85f88-107">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="85f88-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="85f88-108">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="85f88-109">설명</span><span class="sxs-lookup"><span data-stu-id="85f88-109">DESCRIPTION</span></span>

<span data-ttu-id="85f88-110">`Uninstall-Script`Cmdlet은 로컬 컴퓨터에서 지정 된 스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-110">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="85f88-111">예제</span><span class="sxs-lookup"><span data-stu-id="85f88-111">EXAMPLES</span></span>

### <span data-ttu-id="85f88-112">예제 1: 스크립트 제거</span><span class="sxs-lookup"><span data-stu-id="85f88-112">Example 1: Uninstall a script</span></span>

<span data-ttu-id="85f88-113">이 예제에서는 스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-113">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="85f88-114">`Uninstall-Script`**Name** 매개 변수를 사용 하 여 로컬 컴퓨터에서 제거할 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-114">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="85f88-115">예제 2: 파이프라인을 사용 하 여 스크립트 제거</span><span class="sxs-lookup"><span data-stu-id="85f88-115">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="85f88-116">이 예제에서는 파이프라인을 사용 하 여 스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-116">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="85f88-117">`Get-InstalledScript`**Name** 매개 변수를 사용 하 여 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-117">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="85f88-118">개체가 파이프라인으로 전송 되 `Uninstall-Script` 고 스크립트가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-118">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="85f88-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="85f88-119">PARAMETERS</span></span>

### <span data-ttu-id="85f88-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="85f88-120">-AllowPrerelease</span></span>

<span data-ttu-id="85f88-121">시험판으로 표시 된 스크립트를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-121">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="85f88-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="85f88-122">-Confirm</span></span>

<span data-ttu-id="85f88-123">실행 하기 전에 확인 메시지를 표시 `Uninstall-Script` 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-123">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="85f88-124">-Force</span><span class="sxs-lookup"><span data-stu-id="85f88-124">-Force</span></span>

<span data-ttu-id="85f88-125">`Uninstall-Script`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-125">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="85f88-126">-InputObject</span><span class="sxs-lookup"><span data-stu-id="85f88-126">-InputObject</span></span>

<span data-ttu-id="85f88-127">**PSRepositoryItemInfo** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-127">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="85f88-128">예를 들어 `Get-InstalledScript` 변수를 출력 하 고 해당 변수를 **InputObject** 인수로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-128">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="85f88-129">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="85f88-129">-MaximumVersion</span></span>

<span data-ttu-id="85f88-130">제거할 스크립트의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-130">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="85f88-131">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-131">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="85f88-132">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="85f88-132">-MinimumVersion</span></span>

<span data-ttu-id="85f88-133">제거할 스크립트의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-133">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="85f88-134">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-134">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="85f88-135">-Name</span><span class="sxs-lookup"><span data-stu-id="85f88-135">-Name</span></span>

<span data-ttu-id="85f88-136">제거할 스크립트 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-136">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="85f88-137">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="85f88-137">-RequiredVersion</span></span>

<span data-ttu-id="85f88-138">제거할 스크립트의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-138">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="85f88-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="85f88-139">-WhatIf</span></span>

<span data-ttu-id="85f88-140">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Uninstall-Script` .</span><span class="sxs-lookup"><span data-stu-id="85f88-140">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="85f88-141">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85f88-141">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="85f88-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="85f88-142">CommonParameters</span></span>

<span data-ttu-id="85f88-143">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="85f88-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="85f88-144">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85f88-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="85f88-145">입력</span><span class="sxs-lookup"><span data-stu-id="85f88-145">INPUTS</span></span>

### <span data-ttu-id="85f88-146">System.String[]</span><span class="sxs-lookup"><span data-stu-id="85f88-146">System.String[]</span></span>

### <span data-ttu-id="85f88-147">System.web. PSObject []</span><span class="sxs-lookup"><span data-stu-id="85f88-147">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="85f88-148">System.String</span><span class="sxs-lookup"><span data-stu-id="85f88-148">System.String</span></span>

## <span data-ttu-id="85f88-149">출력</span><span class="sxs-lookup"><span data-stu-id="85f88-149">OUTPUTS</span></span>

### <span data-ttu-id="85f88-150">System.Object</span><span class="sxs-lookup"><span data-stu-id="85f88-150">System.Object</span></span>

## <span data-ttu-id="85f88-151">참고</span><span class="sxs-lookup"><span data-stu-id="85f88-151">NOTES</span></span>

## <span data-ttu-id="85f88-152">관련 링크</span><span class="sxs-lookup"><span data-stu-id="85f88-152">RELATED LINKS</span></span>

[<span data-ttu-id="85f88-153">Find-Script</span><span class="sxs-lookup"><span data-stu-id="85f88-153">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="85f88-154">Install-Script</span><span class="sxs-lookup"><span data-stu-id="85f88-154">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="85f88-155">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="85f88-155">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="85f88-156">Save-Script</span><span class="sxs-lookup"><span data-stu-id="85f88-156">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="85f88-157">Update-Script</span><span class="sxs-lookup"><span data-stu-id="85f88-157">Update-Script</span></span>](Update-Script.md)

