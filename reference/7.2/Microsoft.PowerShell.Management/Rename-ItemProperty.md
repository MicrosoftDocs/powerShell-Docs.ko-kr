---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: 4fbd2677d6a978d4d144effe9607bceb376ad43f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602460"
---
# <span data-ttu-id="31da4-102">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31da4-102">Rename-ItemProperty</span></span>

## <span data-ttu-id="31da4-103">개요</span><span class="sxs-lookup"><span data-stu-id="31da4-103">SYNOPSIS</span></span>
<span data-ttu-id="31da4-104">항목의 속성 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-104">Renames a property of an item.</span></span>

## <span data-ttu-id="31da4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="31da4-105">SYNTAX</span></span>

### <span data-ttu-id="31da4-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="31da4-106">Path (Default)</span></span>

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="31da4-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="31da4-107">LiteralPath</span></span>

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="31da4-108">설명</span><span class="sxs-lookup"><span data-stu-id="31da4-108">DESCRIPTION</span></span>

<span data-ttu-id="31da4-109">`Rename-ItemProperty`Cmdlet은 지정 된 항목 속성의 이름을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-109">The `Rename-ItemProperty` cmdlet changes the name of a specified item property.</span></span>
<span data-ttu-id="31da4-110">속성의 값은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-110">The value of the property is not changed.</span></span>
<span data-ttu-id="31da4-111">예를 들어를 사용 `Rename-ItemProperty` 하 여 레지스트리 항목의 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-111">For example, you can use `Rename-ItemProperty` to change the name of a registry entry.</span></span>

## <span data-ttu-id="31da4-112">예제</span><span class="sxs-lookup"><span data-stu-id="31da4-112">EXAMPLES</span></span>

### <span data-ttu-id="31da4-113">예제 1: 레지스트리 항목 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="31da4-113">Example 1: Rename a registry entry</span></span>

<span data-ttu-id="31da4-114">이 명령은 키에 포함 된 구성 레지스트리 항목의 이름을 `HKEY_LOCAL_MACHINE\Software\SmpApplication` "oldconfig"로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-114">This command renames the config registry entry that is contained in the `HKEY_LOCAL_MACHINE\Software\SmpApplication` key to "oldconfig".</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## <span data-ttu-id="31da4-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="31da4-115">PARAMETERS</span></span>

### <span data-ttu-id="31da4-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="31da4-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="31da4-117">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="31da4-118">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="31da4-119">-제외</span><span class="sxs-lookup"><span data-stu-id="31da4-119">-Exclude</span></span>

<span data-ttu-id="31da4-120">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-120">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="31da4-121">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-121">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="31da4-122">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-122">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="31da4-123">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-123">Wildcard characters are permitted.</span></span> <span data-ttu-id="31da4-124">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="31da4-124">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="31da4-125">-Filter</span><span class="sxs-lookup"><span data-stu-id="31da4-125">-Filter</span></span>

<span data-ttu-id="31da4-126">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-126">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="31da4-127">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-127">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="31da4-128">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-128">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="31da4-129">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-129">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="31da4-130">-Force</span><span class="sxs-lookup"><span data-stu-id="31da4-130">-Force</span></span>

<span data-ttu-id="31da4-131">Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 개체의 속성 이름을 강제로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-131">Forces the cmdlet to rename a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="31da4-132">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-132">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="31da4-133">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31da4-133">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="31da4-134">-포함</span><span class="sxs-lookup"><span data-stu-id="31da4-134">-Include</span></span>

<span data-ttu-id="31da4-135">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="31da4-136">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="31da4-137">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="31da4-138">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="31da4-139">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="31da4-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="31da4-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="31da4-140">-LiteralPath</span></span>

<span data-ttu-id="31da4-141">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="31da4-142">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="31da4-143">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="31da4-144">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="31da4-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="31da4-145">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="31da4-146">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31da4-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="31da4-147">-Name</span><span class="sxs-lookup"><span data-stu-id="31da4-147">-Name</span></span>

<span data-ttu-id="31da4-148">이름을 바꿀 속성의 현재 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-148">Specifies the current name of the property to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="31da4-149">-NewName</span><span class="sxs-lookup"><span data-stu-id="31da4-149">-NewName</span></span>

<span data-ttu-id="31da4-150">속성의 새 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-150">Specifies the new name for the property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="31da4-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="31da4-151">-PassThru</span></span>

<span data-ttu-id="31da4-152">항목 속성을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-152">Returns an object that represents the item property.</span></span>
<span data-ttu-id="31da4-153">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="31da4-154">-Path</span><span class="sxs-lookup"><span data-stu-id="31da4-154">-Path</span></span>

<span data-ttu-id="31da4-155">이름을 바꿀 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-155">Specifies the path of the item to rename.</span></span>
<span data-ttu-id="31da4-156">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-156">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="31da4-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="31da4-157">-Confirm</span></span>

<span data-ttu-id="31da4-158">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="31da4-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="31da4-159">-WhatIf</span></span>

<span data-ttu-id="31da4-160">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="31da4-161">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="31da4-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31da4-162">CommonParameters</span></span>

<span data-ttu-id="31da4-163">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-163">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="31da4-164">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31da4-164">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="31da4-165">입력</span><span class="sxs-lookup"><span data-stu-id="31da4-165">INPUTS</span></span>

### <span data-ttu-id="31da4-166">System.String</span><span class="sxs-lookup"><span data-stu-id="31da4-166">System.String</span></span>

<span data-ttu-id="31da4-167">경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-167">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="31da4-168">출력</span><span class="sxs-lookup"><span data-stu-id="31da4-168">OUTPUTS</span></span>

### <span data-ttu-id="31da4-169">None, PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="31da4-169">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="31da4-170">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 이름이 바뀐 항목 속성을 나타내는 **PSCustomObject** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-170">This cmdlet generates a **PSCustomObject** that represents the renamed item property, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="31da4-171">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="31da4-172">참고</span><span class="sxs-lookup"><span data-stu-id="31da4-172">NOTES</span></span>

<span data-ttu-id="31da4-173">`Remove-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-173">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="31da4-174">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31da4-174">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="31da4-175">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31da4-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="31da4-176">관련 링크</span><span class="sxs-lookup"><span data-stu-id="31da4-176">RELATED LINKS</span></span>

[<span data-ttu-id="31da4-177">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31da4-177">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="31da4-178">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31da4-178">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="31da4-179">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31da4-179">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="31da4-180">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31da4-180">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="31da4-181">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31da4-181">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="31da4-182">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31da4-182">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="31da4-183">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="31da4-183">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="31da4-184">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31da4-184">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="31da4-185">about_Providers</span><span class="sxs-lookup"><span data-stu-id="31da4-185">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
