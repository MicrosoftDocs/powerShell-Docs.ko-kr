---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 4cf883964e1ff86487bf5abca8789af62b274c8a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214625"
---
# <span data-ttu-id="35f57-103">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="35f57-103">Move-ItemProperty</span></span>

## <span data-ttu-id="35f57-104">개요</span><span class="sxs-lookup"><span data-stu-id="35f57-104">Synopsis</span></span>
<span data-ttu-id="35f57-105">속성의 위치를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-105">Moves a property from one location to another.</span></span>

## <span data-ttu-id="35f57-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="35f57-106">SYNTAX</span></span>

### <span data-ttu-id="35f57-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="35f57-107">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="35f57-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="35f57-108">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="35f57-109">Description</span><span class="sxs-lookup"><span data-stu-id="35f57-109">Description</span></span>

<span data-ttu-id="35f57-110">`Move-ItemProperty`Cmdlet은 항목의 속성을 한 항목에서 다른 항목으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-110">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="35f57-111">예를 들어 레지스트리 키 간에 레지스트리 항목을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-111">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="35f57-112">항목 속성을 이동하면 해당 속성은 원래 위치에서 삭제되고 새 위치에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-112">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="35f57-113">예제</span><span class="sxs-lookup"><span data-stu-id="35f57-113">EXAMPLES</span></span>

### <span data-ttu-id="35f57-114">예제 1: 레지스트리 값과 해당 데이터를 다른 키로 이동</span><span class="sxs-lookup"><span data-stu-id="35f57-114">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="35f57-115">이 명령은 "MyApp" 하위 키에서 레지스트리 키의 NewApp 하위 키로 버전 레지스트리 값과 해당 데이터를 이동 `HKLM\Software\MyCompany` 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-115">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="35f57-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="35f57-116">PARAMETERS</span></span>

### <span data-ttu-id="35f57-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="35f57-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="35f57-118">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="35f57-119">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35f57-120">-Destination</span><span class="sxs-lookup"><span data-stu-id="35f57-120">-Destination</span></span>

<span data-ttu-id="35f57-121">대상 위치의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-121">Specifies the path to the destination location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35f57-122">-제외</span><span class="sxs-lookup"><span data-stu-id="35f57-122">-Exclude</span></span>

<span data-ttu-id="35f57-123">이 cmdlet이 작업에서 제외 하는 속성 또는 속성을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-123">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="35f57-124">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-124">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="35f57-125">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-125">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="35f57-126">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-126">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="35f57-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="35f57-127">-Filter</span></span>

<span data-ttu-id="35f57-128">공급자의 형식 또는 언어로 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-128">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="35f57-129">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-129">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="35f57-130">와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-130">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="35f57-131">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="35f57-132">-Force</span><span class="sxs-lookup"><span data-stu-id="35f57-132">-Force</span></span>

<span data-ttu-id="35f57-133">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="35f57-134">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-134">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="35f57-135">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35f57-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f57-136">-포함</span><span class="sxs-lookup"><span data-stu-id="35f57-136">-Include</span></span>

<span data-ttu-id="35f57-137">이 cmdlet이 작업에 포함 하는 속성 또는 속성을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-137">Specifies, as a string array, a property or property that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="35f57-138">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="35f57-139">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="35f57-140">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-140">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="35f57-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="35f57-141">-LiteralPath</span></span>

<span data-ttu-id="35f57-142">속성의 현재 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-142">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="35f57-143">**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-143">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="35f57-144">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-144">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="35f57-145">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="35f57-145">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="35f57-146">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35f57-147">-Name</span><span class="sxs-lookup"><span data-stu-id="35f57-147">-Name</span></span>

<span data-ttu-id="35f57-148">이동할 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-148">Specifies the name of the property to be moved.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35f57-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="35f57-149">-PassThru</span></span>

<span data-ttu-id="35f57-150">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-150">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="35f57-151">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="35f57-152">-Path</span><span class="sxs-lookup"><span data-stu-id="35f57-152">-Path</span></span>

<span data-ttu-id="35f57-153">속성의 현재 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-153">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="35f57-154">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-154">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="35f57-155">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="35f57-155">-UseTransaction</span></span>

<span data-ttu-id="35f57-156">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-156">Includes the command in the active transaction.</span></span>
<span data-ttu-id="35f57-157">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-157">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="35f57-158">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35f57-158">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f57-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="35f57-159">-Confirm</span></span>

<span data-ttu-id="35f57-160">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="35f57-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="35f57-161">-WhatIf</span></span>

<span data-ttu-id="35f57-162">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-162">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="35f57-163">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="35f57-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="35f57-164">CommonParameters</span></span>

<span data-ttu-id="35f57-165">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-165">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="35f57-166">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35f57-166">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="35f57-167">입력</span><span class="sxs-lookup"><span data-stu-id="35f57-167">INPUTS</span></span>

### <span data-ttu-id="35f57-168">System.String</span><span class="sxs-lookup"><span data-stu-id="35f57-168">System.String</span></span>

<span data-ttu-id="35f57-169">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-169">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="35f57-170">출력</span><span class="sxs-lookup"><span data-stu-id="35f57-170">OUTPUTS</span></span>

### <span data-ttu-id="35f57-171">없음 또는 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="35f57-171">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="35f57-172">**PassThru** 매개 변수를 사용 하는 경우이 cmdlet은 이동 된 항목 속성을 나타내는 **PSCustomObject** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-172">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span>
<span data-ttu-id="35f57-173">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-173">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="35f57-174">참고</span><span class="sxs-lookup"><span data-stu-id="35f57-174">NOTES</span></span>

<span data-ttu-id="35f57-175">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-175">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="35f57-176">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f57-176">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="35f57-177">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35f57-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="35f57-178">관련 링크</span><span class="sxs-lookup"><span data-stu-id="35f57-178">RELATED LINKS</span></span>

[<span data-ttu-id="35f57-179">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="35f57-179">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="35f57-180">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="35f57-180">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="35f57-181">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="35f57-181">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="35f57-182">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="35f57-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="35f57-183">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="35f57-183">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="35f57-184">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="35f57-184">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="35f57-185">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="35f57-185">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="35f57-186">about_Providers</span><span class="sxs-lookup"><span data-stu-id="35f57-186">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
