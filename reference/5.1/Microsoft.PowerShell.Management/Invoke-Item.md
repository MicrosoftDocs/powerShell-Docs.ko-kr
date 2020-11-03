---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: 6aac74b9b084996377b97997ab78972cb28b0959
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215385"
---
# <span data-ttu-id="396ea-103">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="396ea-103">Invoke-Item</span></span>

## <span data-ttu-id="396ea-104">개요</span><span class="sxs-lookup"><span data-stu-id="396ea-104">SYNOPSIS</span></span>
<span data-ttu-id="396ea-105">지정된 항목에 대해 기본 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-105">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="396ea-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="396ea-106">SYNTAX</span></span>

### <span data-ttu-id="396ea-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="396ea-107">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="396ea-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="396ea-108">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="396ea-109">설명</span><span class="sxs-lookup"><span data-stu-id="396ea-109">DESCRIPTION</span></span>

<span data-ttu-id="396ea-110">`Invoke-Item`Cmdlet은 지정 된 항목에 대해 기본 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-110">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="396ea-111">예를 들어 실행 파일을 실행하거나 문서 파일 형식과 연결된 애플리케이션에서 문서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-111">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="396ea-112">기본 작업은 항목의 유형에 따라 다르며 데이터 액세스를 제공 하는 PowerShell 공급자에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-112">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="396ea-113">예제</span><span class="sxs-lookup"><span data-stu-id="396ea-113">EXAMPLES</span></span>

### <span data-ttu-id="396ea-114">예제 1: 파일 열기</span><span class="sxs-lookup"><span data-stu-id="396ea-114">Example 1: Open a file</span></span>

<span data-ttu-id="396ea-115">이 명령은 Microsoft Office Word에서 "aliasApr04.doc" 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-115">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="396ea-116">이 경우 ".doc" 파일에 대 한 기본 작업은 Word에서 열기입니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-116">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="396ea-117">예제 2: 특정 형식의 모든 파일 열기</span><span class="sxs-lookup"><span data-stu-id="396ea-117">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="396ea-118">이 명령은 "C:\Documents and Settings\Lister\My Documents" 폴더의 모든 Microsoft Office Excel 스프레드시트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-118">This command opens all of the Microsoft Office Excel spreadsheets in the "C:\Documents and Settings\Lister\My Documents" folder.</span></span>
<span data-ttu-id="396ea-119">각 스프레드시트는 Excel의 새 인스턴스로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-119">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="396ea-120">이 경우 ".xls" 파일에 대 한 기본 작업은 Excel에서 열기입니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-120">In this case, opening in Excel is the default action for ".xls" files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="396ea-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="396ea-121">PARAMETERS</span></span>

### <span data-ttu-id="396ea-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="396ea-122">-Credential</span></span>

<span data-ttu-id="396ea-123">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-123">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="396ea-124">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-124">The default is the current user.</span></span>

<span data-ttu-id="396ea-125">"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="396ea-125">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="396ea-126">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-126">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="396ea-127">이 매개 변수는 Windows PowerShell과 함께 설치된 모든 공급자에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-127">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="396ea-128">-제외</span><span class="sxs-lookup"><span data-stu-id="396ea-128">-Exclude</span></span>

<span data-ttu-id="396ea-129">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-129">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="396ea-130">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-130">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="396ea-131">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-131">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="396ea-132">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="396ea-133">-Filter</span><span class="sxs-lookup"><span data-stu-id="396ea-133">-Filter</span></span>

<span data-ttu-id="396ea-134">공급자의 형식 또는 언어로 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-134">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="396ea-135">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-135">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="396ea-136">와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-136">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="396ea-137">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-137">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="396ea-138">-포함</span><span class="sxs-lookup"><span data-stu-id="396ea-138">-Include</span></span>

<span data-ttu-id="396ea-139">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-139">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="396ea-140">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-140">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="396ea-141">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-141">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="396ea-142">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-142">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="396ea-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="396ea-143">-LiteralPath</span></span>

<span data-ttu-id="396ea-144">항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-144">Specifies a path to the item.</span></span>
<span data-ttu-id="396ea-145">**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-145">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="396ea-146">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-146">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="396ea-147">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="396ea-147">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="396ea-148">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="396ea-149">-Path</span><span class="sxs-lookup"><span data-stu-id="396ea-149">-Path</span></span>

<span data-ttu-id="396ea-150">선택된 항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-150">Specifies the path to the selected item.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="396ea-151">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="396ea-151">-UseTransaction</span></span>

<span data-ttu-id="396ea-152">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="396ea-153">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="396ea-154">자세한 내용은 about_transactions를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="396ea-154">For more information, see about_transactions.</span></span>

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

### <span data-ttu-id="396ea-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="396ea-155">-Confirm</span></span>
<span data-ttu-id="396ea-156">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="396ea-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="396ea-157">-WhatIf</span></span>

<span data-ttu-id="396ea-158">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="396ea-159">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="396ea-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="396ea-160">CommonParameters</span></span>

<span data-ttu-id="396ea-161">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-161">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="396ea-162">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="396ea-162">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="396ea-163">입력</span><span class="sxs-lookup"><span data-stu-id="396ea-163">INPUTS</span></span>

### <span data-ttu-id="396ea-164">System.String</span><span class="sxs-lookup"><span data-stu-id="396ea-164">System.String</span></span>

<span data-ttu-id="396ea-165">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-165">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="396ea-166">출력</span><span class="sxs-lookup"><span data-stu-id="396ea-166">OUTPUTS</span></span>

### <span data-ttu-id="396ea-167">없음</span><span class="sxs-lookup"><span data-stu-id="396ea-167">None</span></span>

<span data-ttu-id="396ea-168">이 명령에서 어떠한 출력도 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-168">The command does not generate any output.</span></span>
<span data-ttu-id="396ea-169">그러나 명령이 호출하는 항목은 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-169">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="396ea-170">참고</span><span class="sxs-lookup"><span data-stu-id="396ea-170">NOTES</span></span>

<span data-ttu-id="396ea-171">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-171">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="396ea-172">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="396ea-172">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="396ea-173">자세한 내용은 About_Providers를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="396ea-173">For more information, see about_Providers.</span></span>

## <span data-ttu-id="396ea-174">관련 링크</span><span class="sxs-lookup"><span data-stu-id="396ea-174">RELATED LINKS</span></span>

[<span data-ttu-id="396ea-175">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="396ea-175">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="396ea-176">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="396ea-176">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="396ea-177">Get-Item</span><span class="sxs-lookup"><span data-stu-id="396ea-177">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="396ea-178">Move-Item</span><span class="sxs-lookup"><span data-stu-id="396ea-178">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="396ea-179">New-Item</span><span class="sxs-lookup"><span data-stu-id="396ea-179">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="396ea-180">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="396ea-180">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="396ea-181">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="396ea-181">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="396ea-182">Set-Item</span><span class="sxs-lookup"><span data-stu-id="396ea-182">Set-Item</span></span>](Set-Item.md)
