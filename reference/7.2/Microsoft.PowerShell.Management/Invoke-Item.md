---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: ebb79f16447aef2dd194505d805a34353f710e69
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600637"
---
# <span data-ttu-id="5b03b-102">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="5b03b-102">Invoke-Item</span></span>

## <span data-ttu-id="5b03b-103">개요</span><span class="sxs-lookup"><span data-stu-id="5b03b-103">SYNOPSIS</span></span>
<span data-ttu-id="5b03b-104">지정된 항목에 대해 기본 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-104">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="5b03b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5b03b-105">SYNTAX</span></span>

### <span data-ttu-id="5b03b-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="5b03b-106">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5b03b-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5b03b-107">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5b03b-108">설명</span><span class="sxs-lookup"><span data-stu-id="5b03b-108">DESCRIPTION</span></span>

<span data-ttu-id="5b03b-109">`Invoke-Item`Cmdlet은 지정 된 항목에 대해 기본 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-109">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="5b03b-110">예를 들어 실행 파일을 실행하거나 문서 파일 형식과 연결된 애플리케이션에서 문서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-110">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="5b03b-111">기본 작업은 항목의 유형에 따라 다르며 데이터 액세스를 제공 하는 PowerShell 공급자에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-111">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="5b03b-112">예제</span><span class="sxs-lookup"><span data-stu-id="5b03b-112">EXAMPLES</span></span>

### <span data-ttu-id="5b03b-113">예제 1: 파일 열기</span><span class="sxs-lookup"><span data-stu-id="5b03b-113">Example 1: Open a file</span></span>

<span data-ttu-id="5b03b-114">이 명령은 Microsoft Office Word에서 "aliasApr04.doc" 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-114">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="5b03b-115">이 경우 ".doc" 파일에 대 한 기본 작업은 Word에서 열기입니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-115">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="5b03b-116">예제 2: 특정 형식의 모든 파일 열기</span><span class="sxs-lookup"><span data-stu-id="5b03b-116">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="5b03b-117">이 명령은 폴더의 모든 Microsoft Office Excel 스프레드시트를 엽니다 `C:\Documents and
Settings\Lister\My Documents` .</span><span class="sxs-lookup"><span data-stu-id="5b03b-117">This command opens all of the Microsoft Office Excel spreadsheets in the `C:\Documents and
Settings\Lister\My Documents` folder.</span></span> <span data-ttu-id="5b03b-118">각 스프레드시트는 Excel의 새 인스턴스로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-118">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="5b03b-119">이 경우 Excel에서 열기는 파일에 대 한 기본 동작입니다 `.xls` .</span><span class="sxs-lookup"><span data-stu-id="5b03b-119">In this case, opening in Excel is the default action for `.xls` files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="5b03b-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5b03b-120">PARAMETERS</span></span>

### <span data-ttu-id="5b03b-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="5b03b-121">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="5b03b-122">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-122">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="5b03b-123">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-123">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="5b03b-124">-제외</span><span class="sxs-lookup"><span data-stu-id="5b03b-124">-Exclude</span></span>

<span data-ttu-id="5b03b-125">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-125">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="5b03b-126">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-126">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5b03b-127">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-127">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="5b03b-128">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-128">Wildcard characters are permitted.</span></span> <span data-ttu-id="5b03b-129">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="5b03b-129">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5b03b-130">-Filter</span><span class="sxs-lookup"><span data-stu-id="5b03b-130">-Filter</span></span>

<span data-ttu-id="5b03b-131">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-131">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="5b03b-132">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-132">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="5b03b-133">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-133">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="5b03b-134">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-134">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="5b03b-135">-포함</span><span class="sxs-lookup"><span data-stu-id="5b03b-135">-Include</span></span>

<span data-ttu-id="5b03b-136">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="5b03b-137">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5b03b-138">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="5b03b-139">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="5b03b-140">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="5b03b-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5b03b-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5b03b-141">-LiteralPath</span></span>

<span data-ttu-id="5b03b-142">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="5b03b-143">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="5b03b-144">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="5b03b-145">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="5b03b-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="5b03b-146">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="5b03b-147">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b03b-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="5b03b-148">-Path</span><span class="sxs-lookup"><span data-stu-id="5b03b-148">-Path</span></span>

<span data-ttu-id="5b03b-149">선택된 항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-149">Specifies the path to the selected item.</span></span>
<span data-ttu-id="5b03b-150">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-150">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="5b03b-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5b03b-151">-Confirm</span></span>

<span data-ttu-id="5b03b-152">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5b03b-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5b03b-153">-WhatIf</span></span>

<span data-ttu-id="5b03b-154">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5b03b-155">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5b03b-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b03b-156">CommonParameters</span></span>

<span data-ttu-id="5b03b-157">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-157">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="5b03b-158">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b03b-158">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5b03b-159">입력</span><span class="sxs-lookup"><span data-stu-id="5b03b-159">INPUTS</span></span>

### <span data-ttu-id="5b03b-160">System.String</span><span class="sxs-lookup"><span data-stu-id="5b03b-160">System.String</span></span>

<span data-ttu-id="5b03b-161">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-161">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="5b03b-162">출력</span><span class="sxs-lookup"><span data-stu-id="5b03b-162">OUTPUTS</span></span>

### <span data-ttu-id="5b03b-163">없음</span><span class="sxs-lookup"><span data-stu-id="5b03b-163">None</span></span>

<span data-ttu-id="5b03b-164">이 명령에서 어떠한 출력도 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-164">The command does not generate any output.</span></span>
<span data-ttu-id="5b03b-165">그러나 명령이 호출하는 항목은 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-165">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="5b03b-166">참고</span><span class="sxs-lookup"><span data-stu-id="5b03b-166">NOTES</span></span>

<span data-ttu-id="5b03b-167">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="5b03b-168">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b03b-168">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="5b03b-169">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b03b-169">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="5b03b-170">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5b03b-170">RELATED LINKS</span></span>

[<span data-ttu-id="5b03b-171">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="5b03b-171">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="5b03b-172">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="5b03b-172">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="5b03b-173">Get-Item</span><span class="sxs-lookup"><span data-stu-id="5b03b-173">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="5b03b-174">Move-Item</span><span class="sxs-lookup"><span data-stu-id="5b03b-174">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="5b03b-175">New-Item</span><span class="sxs-lookup"><span data-stu-id="5b03b-175">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="5b03b-176">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="5b03b-176">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="5b03b-177">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="5b03b-177">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="5b03b-178">Set-Item</span><span class="sxs-lookup"><span data-stu-id="5b03b-178">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="5b03b-179">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5b03b-179">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

