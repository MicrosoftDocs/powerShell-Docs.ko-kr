---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-ItemProperty
ms.openlocfilehash: fc454095f9610e8712af18bfe1558e275324cefe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599759"
---
# <span data-ttu-id="0a68c-102">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0a68c-102">Clear-ItemProperty</span></span>

## <span data-ttu-id="0a68c-103">개요</span><span class="sxs-lookup"><span data-stu-id="0a68c-103">SYNOPSIS</span></span>
<span data-ttu-id="0a68c-104">속성의 값을 지우면 속성을 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-104">Clears the value of a property but does not delete the property.</span></span>

## <span data-ttu-id="0a68c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0a68c-105">SYNTAX</span></span>

### <span data-ttu-id="0a68c-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="0a68c-106">Path (Default)</span></span>

```
Clear-ItemProperty [-Path] <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0a68c-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0a68c-107">LiteralPath</span></span>

```
Clear-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0a68c-108">설명</span><span class="sxs-lookup"><span data-stu-id="0a68c-108">DESCRIPTION</span></span>

<span data-ttu-id="0a68c-109">`Clear-ItemProperty`Cmdlet은 속성 값을 지우므로 속성을 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-109">The `Clear-ItemProperty` cmdlet clears the value of a property, but it does not delete the property.</span></span>
<span data-ttu-id="0a68c-110">이 cmdlet을 사용하여 레지스트리 값에서 데이터를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-110">You can use this cmdlet to delete the data from a registry value.</span></span>

## <span data-ttu-id="0a68c-111">예제</span><span class="sxs-lookup"><span data-stu-id="0a68c-111">EXAMPLES</span></span>

### <span data-ttu-id="0a68c-112">예 1: 레지스트리 키의 값을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-112">Example 1: Clear the value of registry key</span></span>

<span data-ttu-id="0a68c-113">이 명령은의 "MyApp" 하위 키에서 "Options" 레지스트리 값의 데이터를 지웁니다 `HKEY_LOCAL_MACHINE\Software\MyCompany` .</span><span class="sxs-lookup"><span data-stu-id="0a68c-113">This command clears the data in the "Options" registry value in the "MyApp" subkey of `HKEY_LOCAL_MACHINE\Software\MyCompany`.</span></span>

```powershell
Clear-ItemProperty -Path "HKLM:\Software\MyCompany\MyApp" -Name "Options"
```

## <span data-ttu-id="0a68c-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0a68c-114">PARAMETERS</span></span>

### <span data-ttu-id="0a68c-115">-Credential</span><span class="sxs-lookup"><span data-stu-id="0a68c-115">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="0a68c-116">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-116">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="0a68c-117">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-117">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="0a68c-118">-제외</span><span class="sxs-lookup"><span data-stu-id="0a68c-118">-Exclude</span></span>

<span data-ttu-id="0a68c-119">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-119">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="0a68c-120">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-120">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0a68c-121">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-121">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="0a68c-122">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-122">Wildcard characters are permitted.</span></span> <span data-ttu-id="0a68c-123">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="0a68c-123">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="0a68c-124">-Filter</span><span class="sxs-lookup"><span data-stu-id="0a68c-124">-Filter</span></span>

<span data-ttu-id="0a68c-125">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-125">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="0a68c-126">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-126">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="0a68c-127">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-127">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="0a68c-128">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-128">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="0a68c-129">-Force</span><span class="sxs-lookup"><span data-stu-id="0a68c-129">-Force</span></span>

<span data-ttu-id="0a68c-130">이 cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 항목에서 속성을 삭제 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-130">Indicates that this cmdlet deletes properties from items that cannot otherwise be accessed by the user.</span></span> <span data-ttu-id="0a68c-131">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-131">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="0a68c-132">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a68c-132">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="0a68c-133">-포함</span><span class="sxs-lookup"><span data-stu-id="0a68c-133">-Include</span></span>

<span data-ttu-id="0a68c-134">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-134">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="0a68c-135">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-135">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0a68c-136">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-136">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="0a68c-137">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-137">Wildcard characters are permitted.</span></span> <span data-ttu-id="0a68c-138">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="0a68c-138">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="0a68c-139">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0a68c-139">-LiteralPath</span></span>

<span data-ttu-id="0a68c-140">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-140">Specifies a path to one or more locations.</span></span> <span data-ttu-id="0a68c-141">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-141">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="0a68c-142">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-142">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0a68c-143">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="0a68c-143">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0a68c-144">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-144">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="0a68c-145">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0a68c-145">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="0a68c-146">-Name</span><span class="sxs-lookup"><span data-stu-id="0a68c-146">-Name</span></span>

<span data-ttu-id="0a68c-147">지울 속성의 이름(예: 레지스트리 값의 이름)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-147">Specifies the name of the property to be cleared, such as the name of a registry value.</span></span>
<span data-ttu-id="0a68c-148">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-148">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="0a68c-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0a68c-149">-PassThru</span></span>

<span data-ttu-id="0a68c-150">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-150">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="0a68c-151">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="0a68c-152">-Path</span><span class="sxs-lookup"><span data-stu-id="0a68c-152">-Path</span></span>

<span data-ttu-id="0a68c-153">지울 속성의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-153">Specifies the path to the property being cleared.</span></span>
<span data-ttu-id="0a68c-154">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-154">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="0a68c-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0a68c-155">-Confirm</span></span>

<span data-ttu-id="0a68c-156">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0a68c-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0a68c-157">-WhatIf</span></span>

<span data-ttu-id="0a68c-158">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0a68c-159">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0a68c-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0a68c-160">CommonParameters</span></span>

<span data-ttu-id="0a68c-161">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-161">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="0a68c-162">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a68c-162">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0a68c-163">입력</span><span class="sxs-lookup"><span data-stu-id="0a68c-163">INPUTS</span></span>

### <span data-ttu-id="0a68c-164">System.String</span><span class="sxs-lookup"><span data-stu-id="0a68c-164">System.String</span></span>

<span data-ttu-id="0a68c-165">이 cmdlet에 경로 문자열을 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-165">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="0a68c-166">출력</span><span class="sxs-lookup"><span data-stu-id="0a68c-166">OUTPUTS</span></span>

### <span data-ttu-id="0a68c-167">없음 또는 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="0a68c-167">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="0a68c-168">**PassThru** 매개 변수를 사용 하는 경우는 `Clear-ItemProperty` 지운 항목 속성을 나타내는 **PSCustomObject** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-168">When you use the **PassThru** parameter, `Clear-ItemProperty` generates a **PSCustomObject** object that represents the cleared item property.</span></span> <span data-ttu-id="0a68c-169">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-169">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0a68c-170">참고</span><span class="sxs-lookup"><span data-stu-id="0a68c-170">NOTES</span></span>

- <span data-ttu-id="0a68c-171">`Clear-ItemProperty`를 사용 하 여 값을 삭제 하지 않고 레지스트리 값의 데이터를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-171">You can use `Clear-ItemProperty` to delete the data in registry values without deleting the value.</span></span>
  <span data-ttu-id="0a68c-172">값의 데이터 유형이 Binary 또는 DWORD인 경우 데이터를 지우면 값은 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-172">If the data type of the value is Binary or DWORD, clearing the data sets the value to zero.</span></span>
  <span data-ttu-id="0a68c-173">그러지 않으면 값은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-173">Otherwise, the value is empty.</span></span>
- <span data-ttu-id="0a68c-174">`Clear-ItemProperty`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-174">The `Clear-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="0a68c-175">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a68c-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="0a68c-176">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a68c-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="0a68c-177">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0a68c-177">RELATED LINKS</span></span>

[<span data-ttu-id="0a68c-178">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0a68c-178">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="0a68c-179">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0a68c-179">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="0a68c-180">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0a68c-180">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="0a68c-181">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0a68c-181">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="0a68c-182">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0a68c-182">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="0a68c-183">about_Providers</span><span class="sxs-lookup"><span data-stu-id="0a68c-183">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

