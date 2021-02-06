---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: d8410fbc2d3f29f0726f84ab151993a60ce95434
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602060"
---
# <span data-ttu-id="20620-102">Format-List</span><span class="sxs-lookup"><span data-stu-id="20620-102">Format-List</span></span>

## <span data-ttu-id="20620-103">개요</span><span class="sxs-lookup"><span data-stu-id="20620-103">SYNOPSIS</span></span>
<span data-ttu-id="20620-104">출력의 형식을 각 속성이 새 줄에 표시되는 속성 목록으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-104">Formats the output as a list of properties in which each property appears on a new line.</span></span>

## <span data-ttu-id="20620-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20620-105">SYNTAX</span></span>

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## <span data-ttu-id="20620-106">설명</span><span class="sxs-lookup"><span data-stu-id="20620-106">DESCRIPTION</span></span>

<span data-ttu-id="20620-107">`Format-List`Cmdlet은 명령의 출력 형식을 각 속성이 별도의 줄에 표시 되는 속성 목록으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-107">The `Format-List` cmdlet formats the output of a command as a list of properties in which each property is displayed on a separate line.</span></span> <span data-ttu-id="20620-108">`Format-List`를 사용 하 여 개체의 모든 속성 또는 선택한 속성을 목록 형식으로 표시 하 고 표시할 수 있습니다 (형식 목록 \*).</span><span class="sxs-lookup"><span data-stu-id="20620-108">You can use `Format-List` to format and display all or selected properties of an object as a list (format-list \*).</span></span>

<span data-ttu-id="20620-109">목록의 각 항목에 사용 가능한 공간이 테이블 보다 더 많은 경우 PowerShell은 목록에 개체의 속성을 더 많이 표시 하 고 속성 값은 잘릴 가능성이 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-109">Because more space is available for each item in a list than in a table, PowerShell displays more properties of the object in the list, and the property values are less likely to be truncated.</span></span>

## <span data-ttu-id="20620-110">예제</span><span class="sxs-lookup"><span data-stu-id="20620-110">EXAMPLES</span></span>

### <span data-ttu-id="20620-111">예제 1: 컴퓨터 서비스 포맷</span><span class="sxs-lookup"><span data-stu-id="20620-111">Example 1: Format computer services</span></span>

```powershell
Get-Service | Format-List
```

<span data-ttu-id="20620-112">이 명령은 컴퓨터의 서비스에 대한 정보를 목록 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-112">This command formats information about services on the computer as a list.</span></span> <span data-ttu-id="20620-113">기본적으로 서비스는 테이블 형식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="20620-113">By default, the services are formatted as a table.</span></span> <span data-ttu-id="20620-114">`Get-Service`Cmdlet은 컴퓨터의 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="20620-114">The `Get-Service` cmdlet gets objects representing the services on the computer.</span></span> <span data-ttu-id="20620-115">파이프라인 연산자 (|)가 파이프라인을 통해 결과를에 전달 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="20620-115">The pipeline operator (|) passes the results through the pipeline to `Format-List`.</span></span>
<span data-ttu-id="20620-116">그런 다음 `Format-List` 목록에서 서비스 정보의 형식을 지정 하 고 표시를 위해 기본 출력 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="20620-116">Then, the `Format-List` command formats the service information in a list and sends it to the default output cmdlet for display.</span></span>

### <span data-ttu-id="20620-117">예제 2: TYPES.PS1XML 파일 서식 지정</span><span class="sxs-lookup"><span data-stu-id="20620-117">Example 2: Format PS1XML files</span></span>

<span data-ttu-id="20620-118">이러한 명령은 PowerShell 디렉터리의 TYPES.PS1XML 파일에 대 한 정보를 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-118">These commands display information about the PS1XML files in the PowerShell directory as a list.</span></span>

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

<span data-ttu-id="20620-119">첫 번째 명령은 파일을 나타내는 개체를 가져와 변수에 저장 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="20620-119">The first command gets the objects representing the files and stores them in the `$A` variable.</span></span>

<span data-ttu-id="20620-120">두 번째 명령은 `Format-List` 를 사용 하 여에 저장 된 개체에 대 한 정보를 형식으로 지정 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="20620-120">The second command uses `Format-List` to format information about objects stored in `$A`.</span></span> <span data-ttu-id="20620-121">이 명령은 **InputObject** 매개 변수를 사용 하 여 변수를에 전달 `Format-List` 합니다. 그러면에서 표시를 위해 형식이 지정 된 출력을 기본 출력 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="20620-121">This command uses the **InputObject** parameter to pass the variable to `Format-List`, which then sends the formatted output to the default output cmdlet for display.</span></span>

### <span data-ttu-id="20620-122">예제 3: 이름을 기준으로 프로세스 속성 서식 지정</span><span class="sxs-lookup"><span data-stu-id="20620-122">Example 3: Format process properties by name</span></span>

<span data-ttu-id="20620-123">이 명령은 컴퓨터에 있는 각 프로세스의 이름, 기본 우선 순위 및 우선 순위 클래스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-123">This command displays the name, base priority, and priority class of each process on the computer.</span></span>

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

<span data-ttu-id="20620-124">Cmdlet을 사용 하 여 `Get-Process` 각 프로세스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="20620-124">It uses the `Get-Process` cmdlet to get an object representing each process.</span></span> <span data-ttu-id="20620-125">파이프라인 연산자 (|)가 파이프라인을 통해 프로세스 개체를에 전달 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="20620-125">The pipeline operator (|) passes the process objects through the pipeline to `Format-List`.</span></span> <span data-ttu-id="20620-126">`Format-List` 프로세스의 형식을 지정 된 속성 목록으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-126">`Format-List` formats the processes as a list of the specified properties.</span></span> <span data-ttu-id="20620-127">*속성* 매개 변수 이름은 선택 사항 이므로 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-127">The *Property* parameter name is optional, so you can omit it.</span></span>

### <span data-ttu-id="20620-128">예제 4: 프로세스의 모든 속성 서식 지정</span><span class="sxs-lookup"><span data-stu-id="20620-128">Example 4: Format all properties for a process</span></span>

<span data-ttu-id="20620-129">이 명령은 Winlogon 프로세스의 모든 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-129">This command displays all of the properties of the Winlogon process.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="20620-130">Get-Process cmdlet을 사용하여 Winlogon 프로세스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="20620-130">It uses the Get-Process cmdlet to get an object representing the Winlogon process.</span></span> <span data-ttu-id="20620-131">파이프라인 연산자 (|)가 파이프라인을 통해 Winlogon 프로세스 개체를에 전달 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="20620-131">The pipeline operator (|) passes the Winlogon process object through the pipeline to `Format-List`.</span></span> <span data-ttu-id="20620-132">이 명령은 *Property* 매개 변수를 사용 하 여 속성을 지정 하 고를 사용 하 여 \* 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-132">The command uses the *Property* parameter to specify the properties and the \* to indicate all properties.</span></span>
<span data-ttu-id="20620-133">*Property* 매개 변수의 이름은 선택 사항 이므로 생략 하 고 명령을 입력할 수 있습니다 `Format-List *` .</span><span class="sxs-lookup"><span data-stu-id="20620-133">Because the name of the *Property* parameter is optional, you can omit it and type the command as `Format-List *`.</span></span> <span data-ttu-id="20620-134">`Format-List` 표시를 위해 결과를 기본 출력 cmdlet으로 자동으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="20620-134">`Format-List` automatically sends the results to the default output cmdlet for display.</span></span>

### <span data-ttu-id="20620-135">예 5: 형식 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="20620-135">Example 5: Troubleshooting format errors</span></span>

<span data-ttu-id="20620-136">다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20620-136">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="20620-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="20620-137">PARAMETERS</span></span>

### <span data-ttu-id="20620-138">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="20620-138">-DisplayError</span></span>

<span data-ttu-id="20620-139">이 cmdlet이 명령줄에서 오류를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="20620-139">Indicates that this cmdlet displays errors at the command line.</span></span> <span data-ttu-id="20620-140">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="20620-140">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="20620-141">-확장</span><span class="sxs-lookup"><span data-stu-id="20620-141">-Expand</span></span>

<span data-ttu-id="20620-142">컬렉션에 있는 개체 뿐만 아니라 서식이 지정 된 컬렉션 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-142">Specifies the formatted collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="20620-143">이 매개 변수는 ICollection(System.Collections) 인터페이스를 지원하는 개체의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-143">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="20620-144">기본값은 EnumOnly입니다.</span><span class="sxs-lookup"><span data-stu-id="20620-144">The default value is EnumOnly.</span></span> <span data-ttu-id="20620-145">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="20620-146">EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="20620-146">EnumOnly.</span></span> <span data-ttu-id="20620-147">컬렉션에 있는 개체의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-147">Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="20620-148">CoreOnly.</span><span class="sxs-lookup"><span data-stu-id="20620-148">CoreOnly.</span></span> <span data-ttu-id="20620-149">컬렉션 개체의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-149">Displays the properties of the collection object.</span></span>
- <span data-ttu-id="20620-150">둘 다.</span><span class="sxs-lookup"><span data-stu-id="20620-150">Both.</span></span> <span data-ttu-id="20620-151">컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-151">Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20620-152">-Force</span><span class="sxs-lookup"><span data-stu-id="20620-152">-Force</span></span>

<span data-ttu-id="20620-153">이 cmdlet이 모든 오류 정보를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="20620-153">Indicates that this cmdlet displays all of the error information.</span></span> <span data-ttu-id="20620-154">**Displayerror** 또는 **showerror** 매개 변수와 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-154">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="20620-155">기본적으로 오류 또는 표시 스트림에 오류 개체를 쓰는 경우 일부 오류 정보만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20620-155">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="20620-156">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="20620-156">-GroupBy</span></span>

<span data-ttu-id="20620-157">공유 속성이 나 값에 따라 그룹의 출력을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-157">Specifies the output in groups based on a shared property or value.</span></span> <span data-ttu-id="20620-158">출력의 식이나 속성을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="20620-158">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="20620-159">**GroupBy** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-159">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="20620-160">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-160">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="20620-161">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-161">Valid key-value pairs are:</span></span>

- <span data-ttu-id="20620-162">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="20620-162">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="20620-163">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="20620-163">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="20620-164">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="20620-164">FormatString - `<string>`</span></span>

<span data-ttu-id="20620-165">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20620-165">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="20620-166">-InputObject</span><span class="sxs-lookup"><span data-stu-id="20620-166">-InputObject</span></span>

<span data-ttu-id="20620-167">형식을 지정할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-167">Specifies the objects to be formatted.</span></span> <span data-ttu-id="20620-168">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="20620-168">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="20620-169">-속성</span><span class="sxs-lookup"><span data-stu-id="20620-169">-Property</span></span>

<span data-ttu-id="20620-170">표시에 나타나는 개체 속성 및 표시되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-170">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="20620-171">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="20620-171">Wildcards are permitted.</span></span>

<span data-ttu-id="20620-172">이 매개 변수를 생략할 경우 표시에 나타나는 속성은 표시되는 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="20620-172">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="20620-173">"Property" 매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="20620-173">The parameter name "Property" is optional.</span></span> <span data-ttu-id="20620-174">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-174">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="20620-175">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-175">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="20620-176">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-176">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="20620-177">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-177">Valid key-value pairs are:</span></span>

- <span data-ttu-id="20620-178">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="20620-178">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="20620-179">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="20620-179">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="20620-180">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="20620-180">FormatString - `<string>`</span></span>

<span data-ttu-id="20620-181">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20620-181">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="20620-182">-ShowError</span><span class="sxs-lookup"><span data-stu-id="20620-182">-ShowError</span></span>

<span data-ttu-id="20620-183">Cmdlet이 파이프라인을 통해 오류를 보내도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-183">Indicates that the cmdlet sends errors through the pipeline.</span></span> <span data-ttu-id="20620-184">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="20620-184">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="20620-185">-보기</span><span class="sxs-lookup"><span data-stu-id="20620-185">-View</span></span>

<span data-ttu-id="20620-186">대체 목록 형식 또는 보기의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-186">Specifies the name of an alternate list format or view.</span></span> <span data-ttu-id="20620-187">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-187">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="20620-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20620-188">CommonParameters</span></span>

<span data-ttu-id="20620-189">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20620-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20620-190">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20620-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20620-191">입력</span><span class="sxs-lookup"><span data-stu-id="20620-191">INPUTS</span></span>

### <span data-ttu-id="20620-192">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="20620-192">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="20620-193">모든 개체를로 파이프 할 수 있습니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="20620-193">You can pipe any object to `Format-List`.</span></span>

## <span data-ttu-id="20620-194">출력</span><span class="sxs-lookup"><span data-stu-id="20620-194">OUTPUTS</span></span>

### <span data-ttu-id="20620-195">Microsoft. PowerShell. Internal. Format</span><span class="sxs-lookup"><span data-stu-id="20620-195">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="20620-196">`Format-List` 목록을 나타내는 형식 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-196">`Format-List` returns the format objects that represent the list.</span></span>

## <span data-ttu-id="20620-197">참고</span><span class="sxs-lookup"><span data-stu-id="20620-197">NOTES</span></span>

<span data-ttu-id="20620-198">기본 제공 별칭인 FL로 Format-List을 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-198">You can also refer to Format-List by its built-in alias, FL.</span></span> <span data-ttu-id="20620-199">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20620-199">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="20620-200">와 같은 형식 cmdlet은 `Format-List` 표시할 데이터를 정렬 하지만 표시 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-200">The format cmdlets, such as `Format-List`, arrange the data to be displayed but do not display it.</span></span>
<span data-ttu-id="20620-201">데이터는 PowerShell의 출력 기능 및 Out 동사 (Out cmdlet)를 포함 하는 cmdlet (예: 또는)에 의해 표시 됩니다 `Out-Host` `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="20620-201">The data is displayed by the output features of PowerShell and by the cmdlets that contain the Out verb (the Out cmdlets), such as `Out-Host` or `Out-File`.</span></span>

<span data-ttu-id="20620-202">Format cmdlet을 사용 하지 않는 경우 PowerShell은 표시 하는 각 개체에 대해 기본 형식을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-202">If you do not use a format cmdlet, PowerShell applies that default format for each object that it displays.</span></span>

<span data-ttu-id="20620-203">**GroupBy** 매개 변수는 개체가 정렬 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-203">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="20620-204">를 사용 하 여 개체를 그룹화 하기 전에 Sort-Object `Format-List` 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-204">Use Sort-Object before using `Format-List` to group the objects.</span></span>

<span data-ttu-id="20620-205">**View** 매개 변수를 사용 하 여 테이블에 대 한 대체 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-205">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="20620-206">PowerShell 디렉터리의 파일에 정의 된 뷰를 사용 `*.format.PS1XML` 하거나 새 types.ps1xml 파일에서 고유한 뷰를 만들고 Update-FormatData cmdlet을 사용 하 여 powershell에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20620-206">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the Update-FormatData cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="20620-207">**View** 매개 변수의 대체 보기는 목록 형식을 사용 해야 합니다. 그렇지 않으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-207">The alternate view for the **View** parameter must use the list format, otherwise, the command fails.</span></span> <span data-ttu-id="20620-208">대체 뷰가 테이블인 경우를 사용 `Format-Table` 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-208">If the alternate view is a table, use `Format-Table`.</span></span> <span data-ttu-id="20620-209">대체 뷰가 목록이 나 테이블이 아닌 경우를 사용 `Format-Custom` 합니다.</span><span class="sxs-lookup"><span data-stu-id="20620-209">If the alternate view is not a list or a table, use `Format-Custom`.</span></span>

## <span data-ttu-id="20620-210">관련 링크</span><span class="sxs-lookup"><span data-stu-id="20620-210">RELATED LINKS</span></span>

[<span data-ttu-id="20620-211">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="20620-211">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="20620-212">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="20620-212">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="20620-213">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="20620-213">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="20620-214">Format-Table</span><span class="sxs-lookup"><span data-stu-id="20620-214">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="20620-215">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="20620-215">Format-Wide</span></span>](Format-Wide.md)
