---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: ff4b2dda3f12fa34fc518c6a180f3213ba873d90
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605479"
---
# <span data-ttu-id="2d140-102">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="2d140-102">Format-Custom</span></span>

## <span data-ttu-id="2d140-103">개요</span><span class="sxs-lookup"><span data-stu-id="2d140-103">SYNOPSIS</span></span>
<span data-ttu-id="2d140-104">사용자 지정된 보기를 사용하여 출력 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-104">Uses a customized view to format the output.</span></span>

## <span data-ttu-id="2d140-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2d140-105">SYNTAX</span></span>

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## <span data-ttu-id="2d140-106">설명</span><span class="sxs-lookup"><span data-stu-id="2d140-106">DESCRIPTION</span></span>

<span data-ttu-id="2d140-107">`Format-Custom`Cmdlet은 대체 보기에 정의 된 대로 명령의 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-107">The `Format-Custom` cmdlet formats the output of a command as defined in an alternate view.</span></span>
<span data-ttu-id="2d140-108">`Format-Custom` 는 단순히 테이블이 나 목록이 아닌 보기를 표시 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-108">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="2d140-109">PowerShell에 정의 된 뷰를 사용 하거나 새 파일에서 고유한 뷰를 만들고 `format.ps1xml` cmdlet을 사용 `Update-FormatData` 하 여 powershell에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-109">You can use the views defined in PowerShell, or you can create your own views in a new `format.ps1xml` file and use the `Update-FormatData` cmdlet to add them to PowerShell.</span></span>

## <span data-ttu-id="2d140-110">예제</span><span class="sxs-lookup"><span data-stu-id="2d140-110">EXAMPLES</span></span>

### <span data-ttu-id="2d140-111">예제 1: 사용자 지정 보기를 사용 하 여 출력 서식 지정</span><span class="sxs-lookup"><span data-stu-id="2d140-111">Example 1: Format output with a custom view</span></span>

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

<span data-ttu-id="2d140-112">이 명령은 `Start-Transcript` 사용자가 만든 사용자 지정 보기 인 MyView 보기에 정의 된 형식으로 cmdlet에 대 한 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-112">This command formats information about the `Start-Transcript` cmdlet in the format defined by the MyView view, a custom view created by the user.</span></span> <span data-ttu-id="2d140-113">이 명령을 성공적으로 실행 하려면 먼저 새 TYPES.PS1XML 파일을 만들고 **myview** 뷰를 정의한 다음 `Update-FormatData` 명령을 사용 하 여 Types.ps1xml 파일을 PowerShell에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-113">To run this command successfully, you must first create a new PS1XML file, define the **MyView** view, and then use the `Update-FormatData` command to add the PS1XML file to PowerShell.</span></span>

### <span data-ttu-id="2d140-114">예제 2: 기본 보기를 사용 하 여 출력 서식 지정</span><span class="sxs-lookup"><span data-stu-id="2d140-114">Example 2: Format output with the default view</span></span>

```powershell
Get-Process Winlogon | Format-Custom
```

<span data-ttu-id="2d140-115">이 명령은 **Winlogon** 프로세스에 대 한 정보의 형식을 다른 사용자 지정 보기로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-115">This command formats information about the **Winlogon** process in an alternate customized view.</span></span>
<span data-ttu-id="2d140-116">이 명령은 **View** 매개 변수를 사용 하지 않으므로는 `Format-Custom` 기본 사용자 지정 뷰를 사용 하 여 데이터의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-116">Because the command does not use the **View** parameter, `Format-Custom` uses a default custom view to format the data.</span></span>

### <span data-ttu-id="2d140-117">예 3: 형식 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="2d140-117">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="2d140-118">다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-118">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

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

## <span data-ttu-id="2d140-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2d140-119">PARAMETERS</span></span>

### <span data-ttu-id="2d140-120">-깊이</span><span class="sxs-lookup"><span data-stu-id="2d140-120">-Depth</span></span>

<span data-ttu-id="2d140-121">표시에서 열의 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-121">Specifies the number of columns in the display.</span></span>

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

### <span data-ttu-id="2d140-122">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="2d140-122">-DisplayError</span></span>

<span data-ttu-id="2d140-123">명령줄에 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-123">Displays errors at the command line.</span></span> <span data-ttu-id="2d140-124">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="2d140-124">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="2d140-125">-확장</span><span class="sxs-lookup"><span data-stu-id="2d140-125">-Expand</span></span>

<span data-ttu-id="2d140-126">컬렉션의 개체와 함께 컬렉션 개체의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-126">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="2d140-127">이 매개 변수는 **Collections** 인터페이스를 지 원하는 개체의 형식을 지정 하도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-127">This parameter is designed to format objects that support the **System.Collections.ICollection** interface.</span></span> <span data-ttu-id="2d140-128">기본값은 **Enumonly** 입니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-128">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="2d140-129">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-129">Valid values are:</span></span>

- <span data-ttu-id="2d140-130">EnumOnly: 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-130">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="2d140-131">CoreOnly: 컬렉션 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-131">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="2d140-132">Both: 컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-132">Both: Displays the properties of the collection object and the objects in the collection.</span></span>

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

### <span data-ttu-id="2d140-133">-Force</span><span class="sxs-lookup"><span data-stu-id="2d140-133">-Force</span></span>

<span data-ttu-id="2d140-134">cmdlet에 모든 오류 정보를 표시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-134">Directs the cmdlet to display all of the error information.</span></span> <span data-ttu-id="2d140-135">**Displayerror** 또는 **showerror** 매개 변수와 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-135">Use with the **DisplayError** or **ShowError** parameters.</span></span> <span data-ttu-id="2d140-136">기본적으로 오류 또는 표시 스트림에 오류 개체를 쓰는 경우 일부 오류 정보만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-136">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="2d140-137">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="2d140-137">-GroupBy</span></span>

<span data-ttu-id="2d140-138">공유 속성이나 값에 따라 그룹으로 출력 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-138">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="2d140-139">출력의 식이나 속성을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="2d140-139">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="2d140-140">**GroupBy** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-140">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="2d140-141">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-141">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="2d140-142">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-142">Valid key-value pairs are:</span></span>

- <span data-ttu-id="2d140-143">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="2d140-143">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="2d140-144">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="2d140-144">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="2d140-145">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="2d140-145">FormatString - `<string>`</span></span>

<span data-ttu-id="2d140-146">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d140-146">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="2d140-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2d140-147">-InputObject</span></span>

<span data-ttu-id="2d140-148">형식을 지정할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-148">Specifies the objects to be formatted.</span></span> <span data-ttu-id="2d140-149">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="2d140-149">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="2d140-150">-속성</span><span class="sxs-lookup"><span data-stu-id="2d140-150">-Property</span></span>

<span data-ttu-id="2d140-151">표시에 나타나는 개체 속성 및 표시되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-151">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="2d140-152">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-152">Wildcards are permitted.</span></span>

<span data-ttu-id="2d140-153">이 매개 변수를 생략할 경우 표시에 나타나는 속성은 표시되는 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-153">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="2d140-154">매개 변수 이름 **속성** 은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-154">The parameter name **Property** is optional.</span></span> <span data-ttu-id="2d140-155">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-155">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="2d140-156">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-156">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="2d140-157">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-157">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="2d140-158">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-158">Valid key-value pairs are:</span></span>

- <span data-ttu-id="2d140-159">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="2d140-159">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="2d140-160">크기 `<int32>`</span><span class="sxs-lookup"><span data-stu-id="2d140-160">Depth - `<int32>`</span></span>

<span data-ttu-id="2d140-161">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d140-161">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="2d140-162">-ShowError</span><span class="sxs-lookup"><span data-stu-id="2d140-162">-ShowError</span></span>

<span data-ttu-id="2d140-163">파이프라인을 통해 오류를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-163">Sends errors through the pipeline.</span></span> <span data-ttu-id="2d140-164">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="2d140-164">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="2d140-165">-보기</span><span class="sxs-lookup"><span data-stu-id="2d140-165">-View</span></span>

<span data-ttu-id="2d140-166">대체 형식 또는 보기의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-166">Specifies the name of an alternate format or view.</span></span> <span data-ttu-id="2d140-167">이 매개 변수를 생략 하면에서 `Format-Custom` 기본 사용자 지정 뷰를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-167">If you omit this parameter, `Format-Custom` uses a default custom view.</span></span> <span data-ttu-id="2d140-168">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-168">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="2d140-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2d140-169">CommonParameters</span></span>

<span data-ttu-id="2d140-170">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2d140-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2d140-171">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d140-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2d140-172">입력</span><span class="sxs-lookup"><span data-stu-id="2d140-172">INPUTS</span></span>

### <span data-ttu-id="2d140-173">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="2d140-173">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="2d140-174">모든 개체를로 파이프 할 수 있습니다 `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="2d140-174">You can pipe any object to `Format-Custom`.</span></span>

## <span data-ttu-id="2d140-175">출력</span><span class="sxs-lookup"><span data-stu-id="2d140-175">OUTPUTS</span></span>

### <span data-ttu-id="2d140-176">Microsoft. PowerShell. Internal. Format</span><span class="sxs-lookup"><span data-stu-id="2d140-176">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="2d140-177">`Format-Custom` 표시를 나타내는 형식 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-177">`Format-Custom` returns the format objects that represent the display.</span></span>

## <span data-ttu-id="2d140-178">참고</span><span class="sxs-lookup"><span data-stu-id="2d140-178">NOTES</span></span>

<span data-ttu-id="2d140-179">`Format-Custom` 는 단순히 테이블이 나 목록이 아닌 보기를 표시 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-179">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="2d140-180">대체 테이블 뷰를 표시 하려면를 사용 `Format-Table` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-180">To display an alternate table view, use `Format-Table`.</span></span> <span data-ttu-id="2d140-181">대체 목록 보기를 표시 하려면를 사용 `Format-List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-181">To display an alternate list view, use `Format-List`.</span></span>

<span data-ttu-id="2d140-182">의 기본 제공 별칭인를 참조할 수도 있습니다 `Format-Custom` `fc` .</span><span class="sxs-lookup"><span data-stu-id="2d140-182">You can also refer to `Format-Custom` by its built-in alias, `fc`.</span></span> <span data-ttu-id="2d140-183">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d140-183">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="2d140-184">**GroupBy** 매개 변수는 개체가 정렬 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-184">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="2d140-185">를 사용 하 여 개체를 그룹화 하기 전에를 `Format-Custom` 사용 하 여 개체를 `Sort-Object` 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d140-185">Before using `Format-Custom` to group the objects, use `Sort-Object` to sort them.</span></span>

## <span data-ttu-id="2d140-186">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2d140-186">RELATED LINKS</span></span>

[<span data-ttu-id="2d140-187">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="2d140-187">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="2d140-188">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="2d140-188">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="2d140-189">Format-List</span><span class="sxs-lookup"><span data-stu-id="2d140-189">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="2d140-190">Format-Table</span><span class="sxs-lookup"><span data-stu-id="2d140-190">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="2d140-191">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="2d140-191">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="2d140-192">Get-Process</span><span class="sxs-lookup"><span data-stu-id="2d140-192">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)