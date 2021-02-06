---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 92a14e4bd165efd4721e3802cade827744c9c056
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601266"
---
# <span data-ttu-id="f165d-102">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f165d-102">Move-ItemProperty</span></span>

## <span data-ttu-id="f165d-103">개요</span><span class="sxs-lookup"><span data-stu-id="f165d-103">Synopsis</span></span>
<span data-ttu-id="f165d-104">속성의 위치를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-104">Moves a property from one location to another.</span></span>

## <span data-ttu-id="f165d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f165d-105">SYNTAX</span></span>

### <span data-ttu-id="f165d-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="f165d-106">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f165d-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f165d-107">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f165d-108">설명</span><span class="sxs-lookup"><span data-stu-id="f165d-108">Description</span></span>

<span data-ttu-id="f165d-109">`Move-ItemProperty`Cmdlet은 항목의 속성을 한 항목에서 다른 항목으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-109">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="f165d-110">예를 들어 레지스트리 키 간에 레지스트리 항목을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-110">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="f165d-111">항목 속성을 이동하면 해당 속성은 원래 위치에서 삭제되고 새 위치에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-111">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="f165d-112">예제</span><span class="sxs-lookup"><span data-stu-id="f165d-112">EXAMPLES</span></span>

### <span data-ttu-id="f165d-113">예제 1: 레지스트리 값과 해당 데이터를 다른 키로 이동</span><span class="sxs-lookup"><span data-stu-id="f165d-113">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="f165d-114">이 명령은 "MyApp" 하위 키에서 레지스트리 키의 NewApp 하위 키로 버전 레지스트리 값과 해당 데이터를 이동 `HKLM\Software\MyCompany` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-114">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="f165d-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f165d-115">PARAMETERS</span></span>

### <span data-ttu-id="f165d-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="f165d-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="f165d-117">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="f165d-118">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="f165d-119">-Destination</span><span class="sxs-lookup"><span data-stu-id="f165d-119">-Destination</span></span>

<span data-ttu-id="f165d-120">대상 위치의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-120">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="f165d-121">-제외</span><span class="sxs-lookup"><span data-stu-id="f165d-121">-Exclude</span></span>

<span data-ttu-id="f165d-122">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-122">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="f165d-123">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-123">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f165d-124">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-124">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f165d-125">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-125">Wildcard characters are permitted.</span></span> <span data-ttu-id="f165d-126">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="f165d-126">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f165d-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="f165d-127">-Filter</span></span>

<span data-ttu-id="f165d-128">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-128">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="f165d-129">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-129">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="f165d-130">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-130">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="f165d-131">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="f165d-132">-Force</span><span class="sxs-lookup"><span data-stu-id="f165d-132">-Force</span></span>

<span data-ttu-id="f165d-133">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="f165d-134">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-134">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="f165d-135">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f165d-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="f165d-136">-포함</span><span class="sxs-lookup"><span data-stu-id="f165d-136">-Include</span></span>

<span data-ttu-id="f165d-137">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="f165d-138">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f165d-139">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="f165d-140">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="f165d-141">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="f165d-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f165d-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f165d-142">-LiteralPath</span></span>

<span data-ttu-id="f165d-143">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f165d-144">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="f165d-145">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f165d-146">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="f165d-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f165d-147">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="f165d-148">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f165d-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f165d-149">-Name</span><span class="sxs-lookup"><span data-stu-id="f165d-149">-Name</span></span>

<span data-ttu-id="f165d-150">이동할 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-150">Specifies the name of the property to be moved.</span></span>

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

### <span data-ttu-id="f165d-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f165d-151">-PassThru</span></span>

<span data-ttu-id="f165d-152">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-152">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="f165d-153">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f165d-154">-Path</span><span class="sxs-lookup"><span data-stu-id="f165d-154">-Path</span></span>

<span data-ttu-id="f165d-155">속성의 현재 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-155">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="f165d-156">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f165d-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f165d-157">-Confirm</span></span>

<span data-ttu-id="f165d-158">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f165d-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f165d-159">-WhatIf</span></span>

<span data-ttu-id="f165d-160">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f165d-161">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f165d-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f165d-162">CommonParameters</span></span>

<span data-ttu-id="f165d-163">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-163">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="f165d-164">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f165d-164">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f165d-165">입력</span><span class="sxs-lookup"><span data-stu-id="f165d-165">INPUTS</span></span>

### <span data-ttu-id="f165d-166">System.String</span><span class="sxs-lookup"><span data-stu-id="f165d-166">System.String</span></span>

<span data-ttu-id="f165d-167">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-167">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="f165d-168">출력</span><span class="sxs-lookup"><span data-stu-id="f165d-168">OUTPUTS</span></span>

### <span data-ttu-id="f165d-169">없음 또는 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="f165d-169">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="f165d-170">**PassThru** 매개 변수를 사용 하는 경우이 cmdlet은 이동 된 항목 속성을 나타내는 **PSCustomObject** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-170">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span> <span data-ttu-id="f165d-171">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f165d-172">참고</span><span class="sxs-lookup"><span data-stu-id="f165d-172">NOTES</span></span>

<span data-ttu-id="f165d-173">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-173">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f165d-174">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f165d-174">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="f165d-175">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f165d-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="f165d-176">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f165d-176">RELATED LINKS</span></span>

[<span data-ttu-id="f165d-177">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f165d-177">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="f165d-178">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f165d-178">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="f165d-179">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f165d-179">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="f165d-180">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f165d-180">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="f165d-181">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f165d-181">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="f165d-182">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f165d-182">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="f165d-183">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f165d-183">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="f165d-184">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f165d-184">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

