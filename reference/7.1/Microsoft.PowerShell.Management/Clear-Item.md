---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Item
ms.openlocfilehash: b03e6a68da933dc0da6bfce92201825f70b77b19
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217609"
---
# <span data-ttu-id="da176-103">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="da176-103">Clear-Item</span></span>

## <span data-ttu-id="da176-104">개요</span><span class="sxs-lookup"><span data-stu-id="da176-104">SYNOPSIS</span></span>
<span data-ttu-id="da176-105">항목의 내용을 지우면 항목을 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-105">Clears the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="da176-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="da176-106">SYNTAX</span></span>

### <span data-ttu-id="da176-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="da176-107">Path (Default)</span></span>

```
Clear-Item [-Path] <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="da176-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="da176-108">LiteralPath</span></span>

```
Clear-Item -LiteralPath <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="da176-109">설명</span><span class="sxs-lookup"><span data-stu-id="da176-109">DESCRIPTION</span></span>

<span data-ttu-id="da176-110">`Clear-Item`Cmdlet은 항목의 내용을 지우고 항목은 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-110">The `Clear-Item` cmdlet clears the content of an item, but it does not delete the item.</span></span>
<span data-ttu-id="da176-111">예를 들어 `Clear-Item` cmdlet은 변수의 값을 삭제할 수 있지만 변수를 삭제 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-111">For example, the `Clear-Item` cmdlet can delete the value of a variable, but it does not delete the variable.</span></span> <span data-ttu-id="da176-112">지워진 항목을 나타내는 데 사용 되는 값은 각 PowerShell 공급자에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da176-112">The value that used to represent a cleared item is defined by each PowerShell provider.</span></span>
<span data-ttu-id="da176-113">이 cmdlet은와 유사 `Clear-Content` 하지만 파일 대신 별칭 및 변수에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-113">This cmdlet is similar to `Clear-Content`, but it works on aliases and variables, instead of files.</span></span>

## <span data-ttu-id="da176-114">예제</span><span class="sxs-lookup"><span data-stu-id="da176-114">EXAMPLES</span></span>

### <span data-ttu-id="da176-115">예제 1: 변수 값 지우기</span><span class="sxs-lookup"><span data-stu-id="da176-115">Example 1: Clear the value of a variable</span></span>

<span data-ttu-id="da176-116">이 명령은 이라는 변수의 값을 지웁니다 `TestVar1` .</span><span class="sxs-lookup"><span data-stu-id="da176-116">This command clears the value of the variable named `TestVar1`.</span></span>
<span data-ttu-id="da176-117">변수는 그대로 유지 되지만 유효 하지만 해당 값은로 설정 됩니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="da176-117">The variable remains and is valid, but its value is set to `$null`.</span></span>
<span data-ttu-id="da176-118">변수 이름에는 `Variable:` PowerShell 변수 공급자를 나타내는 접두사가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-118">The variable name is prefixed with `Variable:` to indicate the PowerShell Variable provider.</span></span>

<span data-ttu-id="da176-119">대체 명령은 동일한 결과를 얻기 위해 PowerShell 드라이브로 전환 하 `Variable:` 고 명령을 실행할 수 있음을 보여 줍니다 `Clear-Item` .</span><span class="sxs-lookup"><span data-stu-id="da176-119">The alternate commands show that, to get the same result, you can switch to the PowerShell `Variable:` drive and then run the `Clear-Item` command.</span></span>

```powershell
Clear-Item Variable:TestVar1
```

```
Set-Location Variable:
PS Variable:\> Clear-Item TestVar1
```

### <span data-ttu-id="da176-120">예제 2: 모든 레지스트리 항목 지우기</span><span class="sxs-lookup"><span data-stu-id="da176-120">Example 2: Clear all registry entries</span></span>

<span data-ttu-id="da176-121">이 명령은 "MyKey" 하위 키의 모든 레지스트리 항목을 지웁니다. 단, 사용자의 의도를 확인 하 라는 메시지가 표시 된 후에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da176-121">This command clears all registry entries in the "MyKey" subkey, but only after prompting you to confirm your intent.</span></span>
<span data-ttu-id="da176-122">"MyKey" 하위 키를 삭제 하거나 다른 레지스트리 키 또는 항목에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-122">It does not delete the "MyKey" subkey or affect any other registry keys or entries.</span></span>
<span data-ttu-id="da176-123">**Include** 및 **Exclude** 매개 변수를 사용하여 특정 레지스트리 키(레지스트리 항목은 해당되지 않음)를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-123">You can use the **Include** and **Exclude** parameters to identify particular registry keys, but you cannot use them to identify registry entries.</span></span>

- <span data-ttu-id="da176-124">특정 레지스트리 항목을 삭제 하려면 cmdlet을 사용 `Remove-ItemProperty` 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-124">To delete particular registry entries, use the `Remove-ItemProperty` cmdlet.</span></span>
- <span data-ttu-id="da176-125">레지스트리 항목의 값을 삭제 하려면를 사용 `Clear-ItemProperty cmdlet` 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-125">To delete the value of a registry entry, use the `Clear-ItemProperty cmdlet`.</span></span>

```powershell
Clear-Item HKLM:\Software\MyCompany\MyKey -Confirm
```

## <span data-ttu-id="da176-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="da176-126">PARAMETERS</span></span>

### <span data-ttu-id="da176-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="da176-127">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="da176-128">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-128">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="da176-129">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-129">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="da176-130">-제외</span><span class="sxs-lookup"><span data-stu-id="da176-130">-Exclude</span></span>

<span data-ttu-id="da176-131">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-131">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="da176-132">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-132">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="da176-133">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-133">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="da176-134">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-134">Wildcard characters are permitted.</span></span> <span data-ttu-id="da176-135">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="da176-135">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="da176-136">-Filter</span><span class="sxs-lookup"><span data-stu-id="da176-136">-Filter</span></span>

<span data-ttu-id="da176-137">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-137">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="da176-138">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="da176-138">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="da176-139">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-139">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="da176-140">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="da176-140">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="da176-141">-Force</span><span class="sxs-lookup"><span data-stu-id="da176-141">-Force</span></span>

<span data-ttu-id="da176-142">Cmdlet이 다른 방법으로는 변경할 수 없는 항목 (예: 읽기 전용 별칭)을 지우도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-142">Indicates that the cmdlet clears items that cannot otherwise be changed, such as read- only aliases.</span></span>
<span data-ttu-id="da176-143">그러나 상수는 지울 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-143">The cmdlet cannot clear constants.</span></span>
<span data-ttu-id="da176-144">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="da176-144">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="da176-145">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da176-145">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="da176-146">**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-146">The cmdlet cannot override security restrictions, even when the **Force** parameter is used.</span></span>

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

### <span data-ttu-id="da176-147">-포함</span><span class="sxs-lookup"><span data-stu-id="da176-147">-Include</span></span>

<span data-ttu-id="da176-148">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-148">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="da176-149">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-149">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="da176-150">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-150">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="da176-151">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-151">Wildcard characters are permitted.</span></span> <span data-ttu-id="da176-152">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="da176-152">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="da176-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="da176-153">-LiteralPath</span></span>

<span data-ttu-id="da176-154">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-154">Specifies a path to one or more locations.</span></span> <span data-ttu-id="da176-155">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da176-155">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="da176-156">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-156">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="da176-157">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="da176-157">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="da176-158">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-158">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="da176-159">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da176-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="da176-160">-Path</span><span class="sxs-lookup"><span data-stu-id="da176-160">-Path</span></span>

<span data-ttu-id="da176-161">지울 항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-161">Specifies the path to the items being cleared.</span></span>
<span data-ttu-id="da176-162">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-162">Wildcard characters are permitted.</span></span>
<span data-ttu-id="da176-163">이 매개 변수는 필수 이지만 매개 변수 이름 **경로** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="da176-163">This parameter is required, but the parameter name **Path** is optional.</span></span>

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

### <span data-ttu-id="da176-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="da176-164">-Confirm</span></span>

<span data-ttu-id="da176-165">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="da176-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="da176-166">-WhatIf</span></span>

<span data-ttu-id="da176-167">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-167">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="da176-168">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="da176-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="da176-169">CommonParameters</span></span>

<span data-ttu-id="da176-170">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-170">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="da176-171">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da176-171">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="da176-172">입력</span><span class="sxs-lookup"><span data-stu-id="da176-172">INPUTS</span></span>

### <span data-ttu-id="da176-173">System.String</span><span class="sxs-lookup"><span data-stu-id="da176-173">System.String</span></span>

<span data-ttu-id="da176-174">이 cmdlet에 경로 문자열을 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-174">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="da176-175">출력</span><span class="sxs-lookup"><span data-stu-id="da176-175">OUTPUTS</span></span>

### <span data-ttu-id="da176-176">없음</span><span class="sxs-lookup"><span data-stu-id="da176-176">None</span></span>

<span data-ttu-id="da176-177">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-177">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="da176-178">참고</span><span class="sxs-lookup"><span data-stu-id="da176-178">NOTES</span></span>

- <span data-ttu-id="da176-179">`Clear-Item`Cmdlet은 **별칭** , **환경** , **함수** , **레지스트리** 및 **변수** 공급자를 비롯 한 여러 PowerShell 공급자만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-179">The `Clear-Item` cmdlet is supported only by several PowerShell providers, including the **Alias** , **Environment** , **Function** , **Registry** , and **Variable** providers.</span></span> <span data-ttu-id="da176-180">따라서를 사용 `Clear-Item` 하 여 공급자 네임 스페이스에 있는 항목의 내용을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-180">As such, you can use `Clear-Item` to delete the content of items in the provider namespaces.</span></span> <span data-ttu-id="da176-181">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-181">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="da176-182">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da176-182">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
- <span data-ttu-id="da176-183">`Clear-Item`PowerShell FileSystem 공급자가이 cmdlet을 지원 하지 않으므로를 사용 하 여 파일의 내용을 삭제할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da176-183">You cannot use `Clear-Item` to delete the contents of a file, because the PowerShell FileSystem provider does not support this cmdlet.</span></span> <span data-ttu-id="da176-184">파일을 지우려면를 사용 `Clear-Content` 합니다.</span><span class="sxs-lookup"><span data-stu-id="da176-184">To clear files, use the `Clear-Content`.</span></span>

## <span data-ttu-id="da176-185">관련 링크</span><span class="sxs-lookup"><span data-stu-id="da176-185">RELATED LINKS</span></span>

[<span data-ttu-id="da176-186">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="da176-186">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="da176-187">Get-Item</span><span class="sxs-lookup"><span data-stu-id="da176-187">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="da176-188">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="da176-188">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="da176-189">Move-Item</span><span class="sxs-lookup"><span data-stu-id="da176-189">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="da176-190">New-Item</span><span class="sxs-lookup"><span data-stu-id="da176-190">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="da176-191">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="da176-191">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="da176-192">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="da176-192">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="da176-193">Set-Item</span><span class="sxs-lookup"><span data-stu-id="da176-193">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="da176-194">about_Providers</span><span class="sxs-lookup"><span data-stu-id="da176-194">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

