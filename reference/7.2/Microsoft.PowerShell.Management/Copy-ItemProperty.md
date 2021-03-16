---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-ItemProperty
ms.openlocfilehash: d6dd6d21d7c0022e8ca1ea7dbd8e1cab8a680de6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599758"
---
# <span data-ttu-id="8b1d9-102">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8b1d9-102">Copy-ItemProperty</span></span>

## <span data-ttu-id="8b1d9-103">개요</span><span class="sxs-lookup"><span data-stu-id="8b1d9-103">SYNOPSIS</span></span>
<span data-ttu-id="8b1d9-104">지정된 위치에서 다른 위치로 속성 및 값을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-104">Copies a property and value from a specified location to another location.</span></span>

## <span data-ttu-id="8b1d9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b1d9-105">SYNTAX</span></span>

### <span data-ttu-id="8b1d9-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="8b1d9-106">Path (Default)</span></span>

```
Copy-ItemProperty [-Path] <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8b1d9-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8b1d9-107">LiteralPath</span></span>

```
Copy-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8b1d9-108">설명</span><span class="sxs-lookup"><span data-stu-id="8b1d9-108">DESCRIPTION</span></span>

<span data-ttu-id="8b1d9-109">`Copy-ItemProperty`Cmdlet은 지정 된 위치에서 다른 위치로 속성 및 값을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-109">The `Copy-ItemProperty` cmdlet copies a property and value from a specified location to another location.</span></span>
<span data-ttu-id="8b1d9-110">예를 들어이 cmdlet을 사용 하 여 한 레지스트리 키에서 다른 레지스트리 키로 하나 이상의 레지스트리 항목을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-110">For instance, you can use this cmdlet to copy one or more registry entries from one registry key to another registry key.</span></span>

## <span data-ttu-id="8b1d9-111">예제</span><span class="sxs-lookup"><span data-stu-id="8b1d9-111">EXAMPLES</span></span>

### <span data-ttu-id="8b1d9-112">예제 1: 레지스트리 키에서 다른 레지스트리 키로 속성 복사</span><span class="sxs-lookup"><span data-stu-id="8b1d9-112">Example 1: Copy a property from a registry key to another registry key</span></span>

<span data-ttu-id="8b1d9-113">이 명령은 "MyApplication" 레지스트리 키에서 "T.myproperty" 라는 속성을 "MyApplicationRev2" 레지스트리 키에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-113">This command copies the property named "MyProperty" from the "MyApplication" registry key to the "MyApplicationRev2" registry key.</span></span>

```powershell
Copy-ItemProperty -Path "MyApplication" -Destination "HKLM:\Software\MyApplicationRev2" -Name "MyProperty"
```

## <span data-ttu-id="8b1d9-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b1d9-114">PARAMETERS</span></span>

### <span data-ttu-id="8b1d9-115">-Credential</span><span class="sxs-lookup"><span data-stu-id="8b1d9-115">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="8b1d9-116">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-116">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="8b1d9-117">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-117">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="8b1d9-118">-Destination</span><span class="sxs-lookup"><span data-stu-id="8b1d9-118">-Destination</span></span>

<span data-ttu-id="8b1d9-119">대상 위치의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-119">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="8b1d9-120">-제외</span><span class="sxs-lookup"><span data-stu-id="8b1d9-120">-Exclude</span></span>

<span data-ttu-id="8b1d9-121">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-121">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="8b1d9-122">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-122">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8b1d9-123">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-123">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="8b1d9-124">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-124">Wildcard characters are permitted.</span></span> <span data-ttu-id="8b1d9-125">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="8b1d9-125">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="8b1d9-126">-Filter</span><span class="sxs-lookup"><span data-stu-id="8b1d9-126">-Filter</span></span>

<span data-ttu-id="8b1d9-127">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-127">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="8b1d9-128">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-128">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="8b1d9-129">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-129">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="8b1d9-130">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-130">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="8b1d9-131">-Force</span><span class="sxs-lookup"><span data-stu-id="8b1d9-131">-Force</span></span>

<span data-ttu-id="8b1d9-132">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-132">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="8b1d9-133">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-133">Implementation varies from provider to provider.</span></span>

<span data-ttu-id="8b1d9-134">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-134">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="8b1d9-135">-포함</span><span class="sxs-lookup"><span data-stu-id="8b1d9-135">-Include</span></span>

<span data-ttu-id="8b1d9-136">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="8b1d9-137">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8b1d9-138">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="8b1d9-139">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="8b1d9-140">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="8b1d9-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="8b1d9-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8b1d9-141">-LiteralPath</span></span>

<span data-ttu-id="8b1d9-142">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="8b1d9-143">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="8b1d9-144">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="8b1d9-145">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="8b1d9-146">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="8b1d9-147">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="8b1d9-148">-Name</span><span class="sxs-lookup"><span data-stu-id="8b1d9-148">-Name</span></span>

<span data-ttu-id="8b1d9-149">복사할 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-149">Specifies the name of the property to be copied.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8b1d9-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8b1d9-150">-PassThru</span></span>

<span data-ttu-id="8b1d9-151">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="8b1d9-152">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8b1d9-153">-Path</span><span class="sxs-lookup"><span data-stu-id="8b1d9-153">-Path</span></span>

<span data-ttu-id="8b1d9-154">복사할 속성의 경로를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-154">Specifies, as a string array, the path to the property to be copied.</span></span>
<span data-ttu-id="8b1d9-155">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-155">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8b1d9-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8b1d9-156">-Confirm</span></span>

<span data-ttu-id="8b1d9-157">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8b1d9-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8b1d9-158">-WhatIf</span></span>

<span data-ttu-id="8b1d9-159">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8b1d9-160">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8b1d9-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b1d9-161">CommonParameters</span></span>

<span data-ttu-id="8b1d9-162">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-162">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="8b1d9-163">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-163">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8b1d9-164">입력</span><span class="sxs-lookup"><span data-stu-id="8b1d9-164">INPUTS</span></span>

### <span data-ttu-id="8b1d9-165">System.String</span><span class="sxs-lookup"><span data-stu-id="8b1d9-165">System.String</span></span>

<span data-ttu-id="8b1d9-166">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-166">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="8b1d9-167">출력</span><span class="sxs-lookup"><span data-stu-id="8b1d9-167">OUTPUTS</span></span>

### <span data-ttu-id="8b1d9-168">없음 또는 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="8b1d9-168">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="8b1d9-169">**Passthru** 매개 변수를 사용 하는 경우이 cmdlet은 복사 된 항목 속성을 나타내는 **PsCustomObject** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-169">When you use the **Passthru** parameter, this cmdlet generates a **PsCustomObject** representing the copied item property.</span></span> <span data-ttu-id="8b1d9-170">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-170">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8b1d9-171">참고</span><span class="sxs-lookup"><span data-stu-id="8b1d9-171">NOTES</span></span>

<span data-ttu-id="8b1d9-172">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-172">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="8b1d9-173">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-173">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="8b1d9-174">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b1d9-174">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="8b1d9-175">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8b1d9-175">RELATED LINKS</span></span>

[<span data-ttu-id="8b1d9-176">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8b1d9-176">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="8b1d9-177">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8b1d9-177">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="8b1d9-178">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8b1d9-178">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="8b1d9-179">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8b1d9-179">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="8b1d9-180">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8b1d9-180">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="8b1d9-181">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8b1d9-181">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="8b1d9-182">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="8b1d9-182">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="8b1d9-183">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8b1d9-183">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
