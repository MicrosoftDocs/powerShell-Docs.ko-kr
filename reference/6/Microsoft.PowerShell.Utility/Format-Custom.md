---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: 28914b86c86d5c16f09c81a5dc70ed1e05123b3e
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219250"
---
# <span data-ttu-id="e0ef6-103">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="e0ef6-103">Format-Custom</span></span>

## <span data-ttu-id="e0ef6-104">개요</span><span class="sxs-lookup"><span data-stu-id="e0ef6-104">SYNOPSIS</span></span>
<span data-ttu-id="e0ef6-105">사용자 지정된 보기를 사용하여 출력 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-105">Uses a customized view to format the output.</span></span>

## <span data-ttu-id="e0ef6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e0ef6-106">SYNTAX</span></span>

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## <span data-ttu-id="e0ef6-107">설명</span><span class="sxs-lookup"><span data-stu-id="e0ef6-107">DESCRIPTION</span></span>

<span data-ttu-id="e0ef6-108">`Format-Custom`Cmdlet은 대체 보기에 정의 된 대로 명령의 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-108">The `Format-Custom` cmdlet formats the output of a command as defined in an alternate view.</span></span>
<span data-ttu-id="e0ef6-109">`Format-Custom` 는 단순히 테이블이 나 목록이 아닌 보기를 표시 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-109">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="e0ef6-110">PowerShell에 정의 된 뷰를 사용 하거나 새 파일에서 고유한 뷰를 만들고 `format.ps1xml` cmdlet을 사용 `Update-FormatData` 하 여 powershell에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-110">You can use the views defined in PowerShell, or you can create your own views in a new `format.ps1xml` file and use the `Update-FormatData` cmdlet to add them to PowerShell.</span></span>

## <span data-ttu-id="e0ef6-111">예제</span><span class="sxs-lookup"><span data-stu-id="e0ef6-111">EXAMPLES</span></span>

### <span data-ttu-id="e0ef6-112">예제 1: 사용자 지정 보기를 사용 하 여 출력 서식 지정</span><span class="sxs-lookup"><span data-stu-id="e0ef6-112">Example 1: Format output with a custom view</span></span>

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

<span data-ttu-id="e0ef6-113">이 명령은 `Start-Transcript` 사용자가 만든 사용자 지정 보기 인 MyView 보기에 정의 된 형식으로 cmdlet에 대 한 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-113">This command formats information about the `Start-Transcript` cmdlet in the format defined by the MyView view, a custom view created by the user.</span></span> <span data-ttu-id="e0ef6-114">이 명령을 성공적으로 실행 하려면 먼저 새 TYPES.PS1XML 파일을 만들고 **myview** 뷰를 정의한 다음 `Update-FormatData` 명령을 사용 하 여 Types.ps1xml 파일을 PowerShell에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-114">To run this command successfully, you must first create a new PS1XML file, define the **MyView** view, and then use the `Update-FormatData` command to add the PS1XML file to PowerShell.</span></span>

### <span data-ttu-id="e0ef6-115">예제 2: 기본 보기를 사용 하 여 출력 서식 지정</span><span class="sxs-lookup"><span data-stu-id="e0ef6-115">Example 2: Format output with the default view</span></span>

```powershell
Get-Process Winlogon | Format-Custom
```

<span data-ttu-id="e0ef6-116">이 명령은 **Winlogon** 프로세스에 대 한 정보의 형식을 다른 사용자 지정 보기로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-116">This command formats information about the **Winlogon** process in an alternate customized view.</span></span>
<span data-ttu-id="e0ef6-117">이 명령은 **View** 매개 변수를 사용 하지 않으므로는 `Format-Custom` 기본 사용자 지정 뷰를 사용 하 여 데이터의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-117">Because the command does not use the **View** parameter, `Format-Custom` uses a default custom view to format the data.</span></span>

### <span data-ttu-id="e0ef6-118">예 3: 형식 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="e0ef6-118">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="e0ef6-119">다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-119">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="e0ef6-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e0ef6-120">PARAMETERS</span></span>

### <span data-ttu-id="e0ef6-121">-깊이</span><span class="sxs-lookup"><span data-stu-id="e0ef6-121">-Depth</span></span>

<span data-ttu-id="e0ef6-122">표시에서 열의 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-122">Specifies the number of columns in the display.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0ef6-123">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="e0ef6-123">-DisplayError</span></span>

<span data-ttu-id="e0ef6-124">명령줄에 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-124">Displays errors at the command line.</span></span> <span data-ttu-id="e0ef6-125">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="e0ef6-125">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="e0ef6-126">-확장</span><span class="sxs-lookup"><span data-stu-id="e0ef6-126">-Expand</span></span>

<span data-ttu-id="e0ef6-127">컬렉션의 개체와 함께 컬렉션 개체의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-127">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="e0ef6-128">이 매개 변수는 **Collections** 인터페이스를 지 원하는 개체의 형식을 지정 하도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-128">This parameter is designed to format objects that support the **System.Collections.ICollection** interface.</span></span> <span data-ttu-id="e0ef6-129">기본값은 **Enumonly** 입니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-129">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="e0ef6-130">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-130">Valid values are:</span></span>

- <span data-ttu-id="e0ef6-131">EnumOnly: 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-131">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="e0ef6-132">CoreOnly: 컬렉션 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-132">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="e0ef6-133">Both: 컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-133">Both: Displays the properties of the collection object and the objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0ef6-134">-Force</span><span class="sxs-lookup"><span data-stu-id="e0ef6-134">-Force</span></span>

<span data-ttu-id="e0ef6-135">cmdlet에 모든 오류 정보를 표시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-135">Directs the cmdlet to display all of the error information.</span></span> <span data-ttu-id="e0ef6-136">**Displayerror** 또는 **showerror** 매개 변수와 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-136">Use with the **DisplayError** or **ShowError** parameters.</span></span> <span data-ttu-id="e0ef6-137">기본적으로 오류 또는 표시 스트림에 오류 개체를 쓰는 경우 일부 오류 정보만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-137">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="e0ef6-138">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="e0ef6-138">-GroupBy</span></span>

<span data-ttu-id="e0ef6-139">공유 속성이나 값에 따라 그룹으로 출력 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-139">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="e0ef6-140">출력의 식이나 속성을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-140">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="e0ef6-141">**GroupBy** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-141">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="e0ef6-142">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-142">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="e0ef6-143">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-143">Valid key-value pairs are:</span></span>

- <span data-ttu-id="e0ef6-144">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="e0ef6-144">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="e0ef6-145">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="e0ef6-145">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="e0ef6-146">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="e0ef6-146">FormatString - `<string>`</span></span>

<span data-ttu-id="e0ef6-147">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-147">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0ef6-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e0ef6-148">-InputObject</span></span>

<span data-ttu-id="e0ef6-149">형식을 지정할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-149">Specifies the objects to be formatted.</span></span> <span data-ttu-id="e0ef6-150">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-150">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e0ef6-151">-속성</span><span class="sxs-lookup"><span data-stu-id="e0ef6-151">-Property</span></span>

<span data-ttu-id="e0ef6-152">표시에 나타나는 개체 속성 및 표시되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-152">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="e0ef6-153">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-153">Wildcards are permitted.</span></span>

<span data-ttu-id="e0ef6-154">이 매개 변수를 생략할 경우 표시에 나타나는 속성은 표시되는 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-154">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="e0ef6-155">매개 변수 이름 **속성** 은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-155">The parameter name **Property** is optional.</span></span> <span data-ttu-id="e0ef6-156">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-156">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="e0ef6-157">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-157">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="e0ef6-158">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-158">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="e0ef6-159">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-159">Valid key-value pairs are:</span></span>

- <span data-ttu-id="e0ef6-160">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="e0ef6-160">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="e0ef6-161">크기 `<int32>`</span><span class="sxs-lookup"><span data-stu-id="e0ef6-161">Depth - `<int32>`</span></span>

<span data-ttu-id="e0ef6-162">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-162">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e0ef6-163">-ShowError</span><span class="sxs-lookup"><span data-stu-id="e0ef6-163">-ShowError</span></span>

<span data-ttu-id="e0ef6-164">파이프라인을 통해 오류를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-164">Sends errors through the pipeline.</span></span> <span data-ttu-id="e0ef6-165">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="e0ef6-165">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="e0ef6-166">-보기</span><span class="sxs-lookup"><span data-stu-id="e0ef6-166">-View</span></span>

<span data-ttu-id="e0ef6-167">대체 형식 또는 보기의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-167">Specifies the name of an alternate format or view.</span></span> <span data-ttu-id="e0ef6-168">이 매개 변수를 생략 하면에서 `Format-Custom` 기본 사용자 지정 뷰를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-168">If you omit this parameter, `Format-Custom` uses a default custom view.</span></span> <span data-ttu-id="e0ef6-169">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-169">You cannot use the **Property** and **View** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0ef6-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0ef6-170">CommonParameters</span></span>

<span data-ttu-id="e0ef6-171">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e0ef6-172">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e0ef6-173">입력</span><span class="sxs-lookup"><span data-stu-id="e0ef6-173">INPUTS</span></span>

### <span data-ttu-id="e0ef6-174">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="e0ef6-174">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e0ef6-175">모든 개체를로 파이프 할 수 있습니다 `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="e0ef6-175">You can pipe any object to `Format-Custom`.</span></span>

## <span data-ttu-id="e0ef6-176">출력</span><span class="sxs-lookup"><span data-stu-id="e0ef6-176">OUTPUTS</span></span>

### <span data-ttu-id="e0ef6-177">Microsoft. PowerShell. Internal. Format</span><span class="sxs-lookup"><span data-stu-id="e0ef6-177">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="e0ef6-178">`Format-Custom` 표시를 나타내는 형식 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-178">`Format-Custom` returns the format objects that represent the display.</span></span>

## <span data-ttu-id="e0ef6-179">참고</span><span class="sxs-lookup"><span data-stu-id="e0ef6-179">NOTES</span></span>

<span data-ttu-id="e0ef6-180">`Format-Custom` 는 단순히 테이블이 나 목록이 아닌 보기를 표시 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-180">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="e0ef6-181">대체 테이블 뷰를 표시 하려면를 사용 `Format-Table` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-181">To display an alternate table view, use `Format-Table`.</span></span> <span data-ttu-id="e0ef6-182">대체 목록 보기를 표시 하려면를 사용 `Format-List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-182">To display an alternate list view, use `Format-List`.</span></span>

<span data-ttu-id="e0ef6-183">의 기본 제공 별칭인를 참조할 수도 있습니다 `Format-Custom` `fc` .</span><span class="sxs-lookup"><span data-stu-id="e0ef6-183">You can also refer to `Format-Custom` by its built-in alias, `fc`.</span></span> <span data-ttu-id="e0ef6-184">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-184">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="e0ef6-185">**GroupBy** 매개 변수는 개체가 정렬 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-185">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="e0ef6-186">를 사용 하 여 개체를 그룹화 하기 전에를 `Format-Custom` 사용 하 여 개체를 `Sort-Object` 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ef6-186">Before using `Format-Custom` to group the objects, use `Sort-Object` to sort them.</span></span>

## <span data-ttu-id="e0ef6-187">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e0ef6-187">RELATED LINKS</span></span>

[<span data-ttu-id="e0ef6-188">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="e0ef6-188">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="e0ef6-189">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="e0ef6-189">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="e0ef6-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="e0ef6-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="e0ef6-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="e0ef6-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="e0ef6-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="e0ef6-192">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="e0ef6-193">Get-Process</span><span class="sxs-lookup"><span data-stu-id="e0ef6-193">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
