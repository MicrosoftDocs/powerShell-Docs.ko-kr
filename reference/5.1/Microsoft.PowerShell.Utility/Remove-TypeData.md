---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 5ba104eb3183916891d9fbf560dac2ecc4a9f6b6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213737"
---
# <span data-ttu-id="fdaab-103">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="fdaab-103">Remove-TypeData</span></span>

## <span data-ttu-id="fdaab-104">개요</span><span class="sxs-lookup"><span data-stu-id="fdaab-104">Synopsis</span></span>
<span data-ttu-id="fdaab-105">현재 세션에서 확장 유형을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-105">Deletes extended types from the current session.</span></span>

## <span data-ttu-id="fdaab-106">구문</span><span class="sxs-lookup"><span data-stu-id="fdaab-106">Syntax</span></span>

### <span data-ttu-id="fdaab-107">RemoveTypeDataSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="fdaab-107">RemoveTypeDataSet (Default)</span></span>

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fdaab-108">RemoveTypeSet</span><span class="sxs-lookup"><span data-stu-id="fdaab-108">RemoveTypeSet</span></span>

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fdaab-109">RemoveFileSet</span><span class="sxs-lookup"><span data-stu-id="fdaab-109">RemoveFileSet</span></span>

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fdaab-110">설명</span><span class="sxs-lookup"><span data-stu-id="fdaab-110">DESCRIPTION</span></span>

<span data-ttu-id="fdaab-111">`Remove-TypeData`Cmdlet은 현재 세션에서 확장 유형 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-111">The `Remove-TypeData` cmdlet deletes extended type data from the current session.</span></span> <span data-ttu-id="fdaab-112">이 cmdlet은 현재 세션과 현재 세션에 만들어지는 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-112">This cmdlet affects only the current session and sessions that are created in the current session.</span></span>

<span data-ttu-id="fdaab-113">명령 및 파일에서 정의 하 여 PowerShell의 개체에 속성 및 메서드를 추가할 수 있습니다 `Update-TypeData` `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-113">You can add properties and methods to objects in PowerShell by defining them in `Update-TypeData` commands and `Types.ps1xml` files.</span></span> <span data-ttu-id="fdaab-114">`Remove-TypeData` 현재 세션에서 확장 된 속성 및 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-114">`Remove-TypeData` deletes those extended properties and methods from the current session.</span></span> <span data-ttu-id="fdaab-115">`Remove-TypeData` 는 파일을 삭제 `Types.ps1xml` 하거나 파일에서 확장 형식 정의를 삭제 하지 않습니다 `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-115">`Remove-TypeData` does not delete the `Types.ps1xml` files or delete any extended type definitions from the `Types.ps1xml` files.</span></span> <span data-ttu-id="fdaab-116">파일에 대 한 자세한 내용은 `Types.ps1xml` [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fdaab-116">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span></span>

<span data-ttu-id="fdaab-117">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="fdaab-118">예</span><span class="sxs-lookup"><span data-stu-id="fdaab-118">Examples</span></span>

### <span data-ttu-id="fdaab-119">예제 1: 지정 된 형식에 대 한 형식 데이터 제거</span><span class="sxs-lookup"><span data-stu-id="fdaab-119">Example 1: Remove type data for a specified type</span></span>

<span data-ttu-id="fdaab-120">이 예에서는 파일에 의해 추가 된 **System.Array** 형식 데이터 `Types.ps1xml` 및 cmdlet을 사용 하 여 세션에 추가 된 동적 형식 데이터를 비롯 하 여 세션에서 system.object 형식의 모든 형식 데이터를 삭제 합니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-120">This example deletes all type data for the **System.Array** type  from the session, including type data that was added by a `Types.ps1xml` file and dynamic type data that was added to the session by using the `Update-TypeData` cmdlet.</span></span>

```powershell
Remove-TypeData -TypeName System.Array
```

### <span data-ttu-id="fdaab-121">예 2: 세션에서 확장 데이터 형식 제거</span><span class="sxs-lookup"><span data-stu-id="fdaab-121">Example 2: Remove an extended data type from a session</span></span>

<span data-ttu-id="fdaab-122">이 예에서는 세션에서 확장 유형 데이터를 제거 하는 경우의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-122">This example shows the effect of removing extended type data from a session.</span></span> <span data-ttu-id="fdaab-123">첫 번째는 `Get-TypeData` **DateTime** 형식의 확장 유형 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-123">The first `Get-TypeData` gets extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="fdaab-124">출력은 PowerShell의 모든 **system.web** 개체에 **datetime** 속성이 추가 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-124">The output shows that a **DateTime** property has been added to all **System.DateTime** objects in PowerShell.</span></span> <span data-ttu-id="fdaab-125">이 `Get-Date` cmdlet은 **시스템의 DateTime** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-125">The `Get-Date` cmdlet returns a **System.DateTime** object.</span></span> <span data-ttu-id="fdaab-126">이 명령은 점 표기법을 사용 하 여를 반환 하는 **system.web** 개체의 **datetime** 속성 값을 가져옵니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-126">The command uses dot notation to get the value of the **DateTime** property of the **System.DateTime** object that `Get-Date` returns.</span></span>

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

<span data-ttu-id="fdaab-127">다음 cmdlet은 system.string `Get-TypeData` 형식에 대 한 모든 확장 유형 **System.DateTime** 데이터를 가져온 다음 cmdlet에 파이프 하 여 `Remove-TypeData` 확장 된 유형 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-127">The next `Get-TypeData` cmdlet to get all extended type data for the **System.DateTime** type and pipes that to the `Remove-TypeData` cmdlet to delete the extended type data.</span></span> <span data-ttu-id="fdaab-128">마지막 `Get-Date` cmdlet은 **DateTime** 형식에 대 한 확장 유형 데이터를 삭제 한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-128">The last `Get-Date` cmdlet shows the effect of deleting the extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="fdaab-129">System.string 속성이 **더** 이상 존재 하지 않기 때문에 해당 값을 가져오는 명령은 아무것도 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-129">Because the **System.DateTime** property no longer exists, a command to get its value returns nothing.</span></span>

### <span data-ttu-id="fdaab-130">예제 3: 모듈에 대 한 확장 형식 제거</span><span class="sxs-lookup"><span data-stu-id="fdaab-130">Example 3: Remove extended types for modules</span></span>

<span data-ttu-id="fdaab-131">이 예에서는 모듈 개체에 대 한 모든 확장 유형 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-131">This example removes all extended type data for module objects.</span></span> <span data-ttu-id="fdaab-132">개체를로 파이프 하는 `Remove-TypeData` 경우 `Remove-TypeData` 개체 형식의 이름을 가져오고 해당 형식의 모든 개체에 대 한 모든 형식 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-132">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the name of the object type and removes all type data for all objects of that type.</span></span>

```powershell
Get-Module | Remove-TypeData
```

### <span data-ttu-id="fdaab-133">예제 4: 지정 된 모듈에서 확장 형식 제거</span><span class="sxs-lookup"><span data-stu-id="fdaab-133">Example 4: Remove extended types from specified modules</span></span>

<span data-ttu-id="fdaab-134">이 예에서는 cmdlet의 **Path** 매개 변수를 사용 하 여 `Remove-TypeData` `Types.ps1xml` **PSScheduledJob** 및 **psworkflow** 모듈에 의해 추가 되는 파일에 정의 된 확장 형식을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-134">This example uses the **Path** parameter of the `Remove-TypeData` cmdlet to remove the extended types that are defined in the `Types.ps1xml` files that are added by the **PSScheduledJob** and **PSWorkflow** modules.</span></span> <span data-ttu-id="fdaab-135">이 명령은 cmdlet을 사용 하 여 추가 된 동적 형식 데이터에는 영향을 주지 않습니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-135">This command does not affect dynamic type data that is added by using the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="fdaab-136">명령은 현재 세션으로 모듈을 가져온 경우에만 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-136">The command succeeds only when the modules have been imported into the current session.</span></span>

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

<span data-ttu-id="fdaab-137">모듈에 대 한 자세한 내용은 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fdaab-137">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

### <span data-ttu-id="fdaab-138">예 5: 원격 세션에서 확장 유형 제거</span><span class="sxs-lookup"><span data-stu-id="fdaab-138">Example 5: Remove extended types from a remote session</span></span>

<span data-ttu-id="fdaab-139">이 예에서는 원격 세션에서 확장 유형을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-139">This example removes extended types from a remote session.</span></span> <span data-ttu-id="fdaab-140">이 명령은 cmdlet을 사용 하 여 `Invoke-Command` 변수에 있는 세션의 모든 CIM 형식에 대 한 확장 유형 데이터를 제거 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-140">The command uses the `Invoke-Command` cmdlet to remove extended type data for all CIM types in the sessions in the `$S` variable.</span></span>

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## <span data-ttu-id="fdaab-141">매개 변수</span><span class="sxs-lookup"><span data-stu-id="fdaab-141">Parameters</span></span>

### <span data-ttu-id="fdaab-142">-Path</span><span class="sxs-lookup"><span data-stu-id="fdaab-142">-Path</span></span>

<span data-ttu-id="fdaab-143">이 cmdlet이 세션 확장 유형 데이터에서 삭제 하는 파일의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-143">Specifies an array of files that this cmdlet deletes from the session extended type data.</span></span> <span data-ttu-id="fdaab-144">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-144">This parameter is required.</span></span>

<span data-ttu-id="fdaab-145">하나 이상의 파일의 경로 및 파일 이름을 입력 `Types.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-145">Enter the paths and file names of one or more `Types.ps1xml` files.</span></span> <span data-ttu-id="fdaab-146">와일드카드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-146">Wildcards are not supported.</span></span> <span data-ttu-id="fdaab-147">경로를 생략할 경우 기본 위치는 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-147">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fdaab-148">-Update-typedata</span><span class="sxs-lookup"><span data-stu-id="fdaab-148">-TypeData</span></span>

<span data-ttu-id="fdaab-149">이 cmdlet이 세션에서 삭제 하는 형식 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-149">Specifies the type data that this cmdlet deletes from the session.</span></span> <span data-ttu-id="fdaab-150">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-150">This parameter is required.</span></span> <span data-ttu-id="fdaab-151">**Update-typedata** 개체 ( **Runspace** ) 또는 **update-typedata** 개체를 가져오는 명령 (예: 명령)을 포함 하는 변수를 입력 합니다. `Get-TypeData`</span><span class="sxs-lookup"><span data-stu-id="fdaab-151">Enter a variable that contains **TypeData** objects ( **System.Management.Automation.Runspaces.TypeData** ) or a command that gets **TypeData** objects, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="fdaab-152">**Update-typedata** 개체를로 파이프 할 수도 있습니다 `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-152">You can also pipe **TypeData** objects to `Remove-TypeData`.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fdaab-153">-TypeName</span><span class="sxs-lookup"><span data-stu-id="fdaab-153">-TypeName</span></span>

<span data-ttu-id="fdaab-154">이 cmdlet이 모든 확장 유형 데이터를 삭제 하는 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-154">Specifies the types that this cmdlet deletes all extended type data for.</span></span> <span data-ttu-id="fdaab-155">System 네임스페이스에 있는 유형의 경우 짧은 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-155">For types in the System namespace, enter the short name.</span></span> <span data-ttu-id="fdaab-156">그러지 않으면 전체 유형 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-156">Otherwise, the full type name is required.</span></span> <span data-ttu-id="fdaab-157">와일드카드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-157">Wildcards are not supported.</span></span>

<span data-ttu-id="fdaab-158">형식 이름을로 파이프 할 수 있습니다 `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-158">You can pipe type names to `Remove-TypeData`.</span></span> <span data-ttu-id="fdaab-159">개체를로 파이프 하는 경우 개체 `Remove-TypeData` `Remove-TypeData` 의 형식 이름을 가져오고 개체 형식에 대 한 모든 형식 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-159">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fdaab-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fdaab-160">-Confirm</span></span>

<span data-ttu-id="fdaab-161">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fdaab-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fdaab-162">-WhatIf</span></span>

<span data-ttu-id="fdaab-163">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-163">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fdaab-164">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fdaab-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fdaab-165">CommonParameters</span></span>

<span data-ttu-id="fdaab-166">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fdaab-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fdaab-167">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fdaab-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fdaab-168">입력</span><span class="sxs-lookup"><span data-stu-id="fdaab-168">Inputs</span></span>

### <span data-ttu-id="fdaab-169">Runspace. Update-typedata</span><span class="sxs-lookup"><span data-stu-id="fdaab-169">System.Management.Automation.Runspaces.TypeData</span></span>

<span data-ttu-id="fdaab-170">Cmdlet이 반환 하는 개체와 같은 **update-typedata** 개체를로 파이프 할 수 있습니다 `Get-TypeData` `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-170">You can pipe **TypeData** object, such as the ones that the `Get-TypeData` cmdlet returns, to `Remove-TypeData`.</span></span>

### <span data-ttu-id="fdaab-171">System.String</span><span class="sxs-lookup"><span data-stu-id="fdaab-171">System.String</span></span>

<span data-ttu-id="fdaab-172">형식 이름을로 파이프 할 수 있습니다 `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="fdaab-172">You can pipe the type names to `Remove-TypeData`.</span></span> <span data-ttu-id="fdaab-173">개체를로 파이프 하는 경우 개체 `Remove-TypeData` `Remove-TypeData` 의 형식 이름을 가져오고 개체 형식에 대 한 모든 형식 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-173">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

## <span data-ttu-id="fdaab-174">outputs</span><span class="sxs-lookup"><span data-stu-id="fdaab-174">Outputs</span></span>

### <span data-ttu-id="fdaab-175">없음</span><span class="sxs-lookup"><span data-stu-id="fdaab-175">None</span></span>

<span data-ttu-id="fdaab-176">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-176">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fdaab-177">메모</span><span class="sxs-lookup"><span data-stu-id="fdaab-177">Notes</span></span>

<span data-ttu-id="fdaab-178">`Remove-TypeData` 현재 세션에서 확장 유형 데이터만 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-178">`Remove-TypeData` can remove only the extended type data in the current session.</span></span> <span data-ttu-id="fdaab-179">컴퓨터에 있지만 현재 세션에 추가되지 않은 확장 유형 데이터(예: 현재 세션으로 가져오지 않은 모듈에 정의된 확장 유형)는 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fdaab-179">It cannot remove extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="fdaab-180">관련 링크</span><span class="sxs-lookup"><span data-stu-id="fdaab-180">Related links</span></span>

[<span data-ttu-id="fdaab-181">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="fdaab-181">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="fdaab-182">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="fdaab-182">Update-TypeData</span></span>](Update-TypeData.md)
