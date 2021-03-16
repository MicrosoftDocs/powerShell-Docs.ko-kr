---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 8ede1375faa1287b70eeb49689ec7fe1bb800d55
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605504"
---
# <span data-ttu-id="3a17a-102">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="3a17a-102">Remove-TypeData</span></span>

## <span data-ttu-id="3a17a-103">개요</span><span class="sxs-lookup"><span data-stu-id="3a17a-103">Synopsis</span></span>
<span data-ttu-id="3a17a-104">현재 세션에서 확장 유형을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-104">Deletes extended types from the current session.</span></span>

## <span data-ttu-id="3a17a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a17a-105">Syntax</span></span>

### <span data-ttu-id="3a17a-106">RemoveTypeDataSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="3a17a-106">RemoveTypeDataSet (Default)</span></span>

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3a17a-107">RemoveTypeSet</span><span class="sxs-lookup"><span data-stu-id="3a17a-107">RemoveTypeSet</span></span>

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3a17a-108">RemoveFileSet</span><span class="sxs-lookup"><span data-stu-id="3a17a-108">RemoveFileSet</span></span>

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3a17a-109">설명</span><span class="sxs-lookup"><span data-stu-id="3a17a-109">DESCRIPTION</span></span>

<span data-ttu-id="3a17a-110">`Remove-TypeData`Cmdlet은 현재 세션에서 확장 유형 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-110">The `Remove-TypeData` cmdlet deletes extended type data from the current session.</span></span> <span data-ttu-id="3a17a-111">이 cmdlet은 현재 세션과 현재 세션에 만들어지는 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-111">This cmdlet affects only the current session and sessions that are created in the current session.</span></span>

<span data-ttu-id="3a17a-112">명령 및 파일에서 정의 하 여 PowerShell의 개체에 속성 및 메서드를 추가할 수 있습니다 `Update-TypeData` `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-112">You can add properties and methods to objects in PowerShell by defining them in `Update-TypeData` commands and `Types.ps1xml` files.</span></span> <span data-ttu-id="3a17a-113">`Remove-TypeData` 현재 세션에서 확장 된 속성 및 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-113">`Remove-TypeData` deletes those extended properties and methods from the current session.</span></span> <span data-ttu-id="3a17a-114">`Remove-TypeData` 는 파일을 삭제 `Types.ps1xml` 하거나 파일에서 확장 형식 정의를 삭제 하지 않습니다 `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-114">`Remove-TypeData` does not delete the `Types.ps1xml` files or delete any extended type definitions from the `Types.ps1xml` files.</span></span> <span data-ttu-id="3a17a-115">파일에 대 한 자세한 내용은 `Types.ps1xml` [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a17a-115">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span></span>

<span data-ttu-id="3a17a-116">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="3a17a-117">예</span><span class="sxs-lookup"><span data-stu-id="3a17a-117">Examples</span></span>

### <span data-ttu-id="3a17a-118">예제 1: 지정 된 형식에 대 한 형식 데이터 제거</span><span class="sxs-lookup"><span data-stu-id="3a17a-118">Example 1: Remove type data for a specified type</span></span>

<span data-ttu-id="3a17a-119">이 예에서는 파일에 의해 추가 된  형식 데이터 `Types.ps1xml` 및 cmdlet을 사용 하 여 세션에 추가 된 동적 형식 데이터를 비롯 하 여 세션에서 system.object 형식의 모든 형식 데이터를 삭제 합니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-119">This example deletes all type data for the **System.Array** type  from the session, including type data that was added by a `Types.ps1xml` file and dynamic type data that was added to the session by using the `Update-TypeData` cmdlet.</span></span>

```powershell
Remove-TypeData -TypeName System.Array
```

### <span data-ttu-id="3a17a-120">예 2: 세션에서 확장 데이터 형식 제거</span><span class="sxs-lookup"><span data-stu-id="3a17a-120">Example 2: Remove an extended data type from a session</span></span>

<span data-ttu-id="3a17a-121">이 예에서는 세션에서 확장 유형 데이터를 제거 하는 경우의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-121">This example shows the effect of removing extended type data from a session.</span></span> <span data-ttu-id="3a17a-122">첫 번째는 `Get-TypeData` **DateTime** 형식의 확장 유형 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-122">The first `Get-TypeData` gets extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="3a17a-123">출력은 PowerShell의 모든 **system.web** 개체에 **datetime** 속성이 추가 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-123">The output shows that a **DateTime** property has been added to all **System.DateTime** objects in PowerShell.</span></span> <span data-ttu-id="3a17a-124">이 `Get-Date` cmdlet은 **시스템의 DateTime** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-124">The `Get-Date` cmdlet returns a **System.DateTime** object.</span></span> <span data-ttu-id="3a17a-125">이 명령은 점 표기법을 사용 하 여를 반환 하는 **system.web** 개체의 **datetime** 속성 값을 가져옵니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-125">The command uses dot notation to get the value of the **DateTime** property of the **System.DateTime** object that `Get-Date` returns.</span></span>

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

<span data-ttu-id="3a17a-126">다음 cmdlet은 system.string `Get-TypeData` 형식에 대 한 모든 확장 유형  데이터를 가져온 다음 cmdlet에 파이프 하 여 `Remove-TypeData` 확장 된 유형 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-126">The next `Get-TypeData` cmdlet to get all extended type data for the **System.DateTime** type and pipes that to the `Remove-TypeData` cmdlet to delete the extended type data.</span></span> <span data-ttu-id="3a17a-127">마지막 `Get-Date` cmdlet은 **DateTime** 형식에 대 한 확장 유형 데이터를 삭제 한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-127">The last `Get-Date` cmdlet shows the effect of deleting the extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="3a17a-128">System.string 속성이 **더** 이상 존재 하지 않기 때문에 해당 값을 가져오는 명령은 아무것도 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-128">Because the **System.DateTime** property no longer exists, a command to get its value returns nothing.</span></span>

### <span data-ttu-id="3a17a-129">예제 3: 모듈에 대 한 확장 형식 제거</span><span class="sxs-lookup"><span data-stu-id="3a17a-129">Example 3: Remove extended types for modules</span></span>

<span data-ttu-id="3a17a-130">이 예에서는 모듈 개체에 대 한 모든 확장 유형 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-130">This example removes all extended type data for module objects.</span></span> <span data-ttu-id="3a17a-131">개체를로 파이프 하는 `Remove-TypeData` 경우 `Remove-TypeData` 개체 형식의 이름을 가져오고 해당 형식의 모든 개체에 대 한 모든 형식 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-131">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the name of the object type and removes all type data for all objects of that type.</span></span>

```powershell
Get-Module | Remove-TypeData
```

### <span data-ttu-id="3a17a-132">예제 4: 지정 된 모듈에서 확장 형식 제거</span><span class="sxs-lookup"><span data-stu-id="3a17a-132">Example 4: Remove extended types from specified modules</span></span>

<span data-ttu-id="3a17a-133">이 예에서는 cmdlet의 **Path** 매개 변수를 사용 하 여 `Remove-TypeData` `Types.ps1xml` **PSScheduledJob** 및 **psworkflow** 모듈에 의해 추가 되는 파일에 정의 된 확장 형식을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-133">This example uses the **Path** parameter of the `Remove-TypeData` cmdlet to remove the extended types that are defined in the `Types.ps1xml` files that are added by the **PSScheduledJob** and **PSWorkflow** modules.</span></span> <span data-ttu-id="3a17a-134">이 명령은 cmdlet을 사용 하 여 추가 된 동적 형식 데이터에는 영향을 주지 않습니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-134">This command does not affect dynamic type data that is added by using the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="3a17a-135">명령은 현재 세션으로 모듈을 가져온 경우에만 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-135">The command succeeds only when the modules have been imported into the current session.</span></span>

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

<span data-ttu-id="3a17a-136">모듈에 대 한 자세한 내용은 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a17a-136">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

### <span data-ttu-id="3a17a-137">예 5: 원격 세션에서 확장 유형 제거</span><span class="sxs-lookup"><span data-stu-id="3a17a-137">Example 5: Remove extended types from a remote session</span></span>

<span data-ttu-id="3a17a-138">이 예에서는 원격 세션에서 확장 유형을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-138">This example removes extended types from a remote session.</span></span> <span data-ttu-id="3a17a-139">이 명령은 cmdlet을 사용 하 여 `Invoke-Command` 변수에 있는 세션의 모든 CIM 형식에 대 한 확장 유형 데이터를 제거 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-139">The command uses the `Invoke-Command` cmdlet to remove extended type data for all CIM types in the sessions in the `$S` variable.</span></span>

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## <span data-ttu-id="3a17a-140">매개 변수</span><span class="sxs-lookup"><span data-stu-id="3a17a-140">Parameters</span></span>

### <span data-ttu-id="3a17a-141">-Path</span><span class="sxs-lookup"><span data-stu-id="3a17a-141">-Path</span></span>

<span data-ttu-id="3a17a-142">이 cmdlet이 세션 확장 유형 데이터에서 삭제 하는 파일의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-142">Specifies an array of files that this cmdlet deletes from the session extended type data.</span></span> <span data-ttu-id="3a17a-143">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-143">This parameter is required.</span></span>

<span data-ttu-id="3a17a-144">하나 이상의 파일의 경로 및 파일 이름을 입력 `Types.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-144">Enter the paths and file names of one or more `Types.ps1xml` files.</span></span> <span data-ttu-id="3a17a-145">와일드카드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-145">Wildcards are not supported.</span></span> <span data-ttu-id="3a17a-146">경로를 생략할 경우 기본 위치는 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-146">If you omit the path, the default location is the current directory.</span></span>

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

### <span data-ttu-id="3a17a-147">-Update-typedata</span><span class="sxs-lookup"><span data-stu-id="3a17a-147">-TypeData</span></span>

<span data-ttu-id="3a17a-148">이 cmdlet이 세션에서 삭제 하는 형식 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-148">Specifies the type data that this cmdlet deletes from the session.</span></span> <span data-ttu-id="3a17a-149">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-149">This parameter is required.</span></span> <span data-ttu-id="3a17a-150">**Update-typedata** 개체 (**Runspace**) 또는 **update-typedata** 개체를 가져오는 명령 (예: 명령)을 포함 하는 변수를 입력 합니다. `Get-TypeData`</span><span class="sxs-lookup"><span data-stu-id="3a17a-150">Enter a variable that contains **TypeData** objects (**System.Management.Automation.Runspaces.TypeData**) or a command that gets **TypeData** objects, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="3a17a-151">**Update-typedata** 개체를로 파이프 할 수도 있습니다 `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-151">You can also pipe **TypeData** objects to `Remove-TypeData`.</span></span>

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

### <span data-ttu-id="3a17a-152">-TypeName</span><span class="sxs-lookup"><span data-stu-id="3a17a-152">-TypeName</span></span>

<span data-ttu-id="3a17a-153">이 cmdlet이 모든 확장 유형 데이터를 삭제 하는 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-153">Specifies the types that this cmdlet deletes all extended type data for.</span></span> <span data-ttu-id="3a17a-154">System 네임스페이스에 있는 유형의 경우 짧은 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-154">For types in the System namespace, enter the short name.</span></span> <span data-ttu-id="3a17a-155">그러지 않으면 전체 유형 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-155">Otherwise, the full type name is required.</span></span> <span data-ttu-id="3a17a-156">와일드카드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-156">Wildcards are not supported.</span></span>

<span data-ttu-id="3a17a-157">형식 이름을로 파이프 할 수 있습니다 `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-157">You can pipe type names to `Remove-TypeData`.</span></span> <span data-ttu-id="3a17a-158">개체를로 파이프 하는 경우 개체 `Remove-TypeData` `Remove-TypeData` 의 형식 이름을 가져오고 개체 형식에 대 한 모든 형식 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-158">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

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

### <span data-ttu-id="3a17a-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3a17a-159">-Confirm</span></span>

<span data-ttu-id="3a17a-160">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3a17a-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3a17a-161">-WhatIf</span></span>

<span data-ttu-id="3a17a-162">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-162">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3a17a-163">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3a17a-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3a17a-164">CommonParameters</span></span>

<span data-ttu-id="3a17a-165">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3a17a-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3a17a-166">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a17a-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3a17a-167">입력</span><span class="sxs-lookup"><span data-stu-id="3a17a-167">Inputs</span></span>

### <span data-ttu-id="3a17a-168">Runspace. Update-typedata</span><span class="sxs-lookup"><span data-stu-id="3a17a-168">System.Management.Automation.Runspaces.TypeData</span></span>

<span data-ttu-id="3a17a-169">Cmdlet이 반환 하는 개체와 같은 **update-typedata** 개체를로 파이프 할 수 있습니다 `Get-TypeData` `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-169">You can pipe **TypeData** object, such as the ones that the `Get-TypeData` cmdlet returns, to `Remove-TypeData`.</span></span>

### <span data-ttu-id="3a17a-170">System.String</span><span class="sxs-lookup"><span data-stu-id="3a17a-170">System.String</span></span>

<span data-ttu-id="3a17a-171">형식 이름을로 파이프 할 수 있습니다 `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="3a17a-171">You can pipe the type names to `Remove-TypeData`.</span></span> <span data-ttu-id="3a17a-172">개체를로 파이프 하는 경우 개체 `Remove-TypeData` `Remove-TypeData` 의 형식 이름을 가져오고 개체 형식에 대 한 모든 형식 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-172">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

## <span data-ttu-id="3a17a-173">출력</span><span class="sxs-lookup"><span data-stu-id="3a17a-173">Outputs</span></span>

### <span data-ttu-id="3a17a-174">없음</span><span class="sxs-lookup"><span data-stu-id="3a17a-174">None</span></span>

<span data-ttu-id="3a17a-175">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-175">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3a17a-176">참고</span><span class="sxs-lookup"><span data-stu-id="3a17a-176">Notes</span></span>

<span data-ttu-id="3a17a-177">`Remove-TypeData` 현재 세션에서 확장 유형 데이터만 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-177">`Remove-TypeData` can remove only the extended type data in the current session.</span></span> <span data-ttu-id="3a17a-178">컴퓨터에 있지만 현재 세션에 추가되지 않은 확장 유형 데이터(예: 현재 세션으로 가져오지 않은 모듈에 정의된 확장 유형)는 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a17a-178">It cannot remove extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="3a17a-179">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3a17a-179">Related links</span></span>

[<span data-ttu-id="3a17a-180">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="3a17a-180">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="3a17a-181">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="3a17a-181">Update-TypeData</span></span>](Update-TypeData.md)
