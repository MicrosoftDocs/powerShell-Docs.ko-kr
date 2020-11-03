---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: 7817384f077c58b46aed1dba552f89ac431891f0
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219305"
---
# <span data-ttu-id="ce7ff-103">Format-List</span><span class="sxs-lookup"><span data-stu-id="ce7ff-103">Format-List</span></span>

## <span data-ttu-id="ce7ff-104">개요</span><span class="sxs-lookup"><span data-stu-id="ce7ff-104">SYNOPSIS</span></span>
<span data-ttu-id="ce7ff-105">출력의 형식을 각 속성이 새 줄에 표시되는 속성 목록으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-105">Formats the output as a list of properties in which each property appears on a new line.</span></span>

## <span data-ttu-id="ce7ff-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ce7ff-106">SYNTAX</span></span>

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## <span data-ttu-id="ce7ff-107">설명</span><span class="sxs-lookup"><span data-stu-id="ce7ff-107">DESCRIPTION</span></span>

<span data-ttu-id="ce7ff-108">`Format-List`Cmdlet은 명령의 출력 형식을 각 속성이 별도의 줄에 표시 되는 속성 목록으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-108">The `Format-List` cmdlet formats the output of a command as a list of properties in which each property is displayed on a separate line.</span></span> <span data-ttu-id="ce7ff-109">`Format-List`를 사용 하 여 개체의 모든 속성 또는 선택한 속성을 목록 형식으로 표시 하 고 표시할 수 있습니다 (형식 목록 \*).</span><span class="sxs-lookup"><span data-stu-id="ce7ff-109">You can use `Format-List` to format and display all or selected properties of an object as a list (format-list \*).</span></span>

<span data-ttu-id="ce7ff-110">목록의 각 항목에 사용 가능한 공간이 테이블 보다 더 많은 경우 PowerShell은 목록에 개체의 속성을 더 많이 표시 하 고 속성 값은 잘릴 가능성이 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-110">Because more space is available for each item in a list than in a table, PowerShell displays more properties of the object in the list, and the property values are less likely to be truncated.</span></span>

## <span data-ttu-id="ce7ff-111">예제</span><span class="sxs-lookup"><span data-stu-id="ce7ff-111">EXAMPLES</span></span>

### <span data-ttu-id="ce7ff-112">예제 1: 컴퓨터 서비스 포맷</span><span class="sxs-lookup"><span data-stu-id="ce7ff-112">Example 1: Format computer services</span></span>

```powershell
Get-Service | Format-List
```

<span data-ttu-id="ce7ff-113">이 명령은 컴퓨터의 서비스에 대한 정보를 목록 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-113">This command formats information about services on the computer as a list.</span></span> <span data-ttu-id="ce7ff-114">기본적으로 서비스는 테이블 형식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-114">By default, the services are formatted as a table.</span></span> <span data-ttu-id="ce7ff-115">`Get-Service`Cmdlet은 컴퓨터의 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-115">The `Get-Service` cmdlet gets objects representing the services on the computer.</span></span> <span data-ttu-id="ce7ff-116">파이프라인 연산자 (|)가 파이프라인을 통해 결과를에 전달 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-116">The pipeline operator (|) passes the results through the pipeline to `Format-List`.</span></span>
<span data-ttu-id="ce7ff-117">그런 다음 `Format-List` 목록에서 서비스 정보의 형식을 지정 하 고 표시를 위해 기본 출력 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-117">Then, the `Format-List` command formats the service information in a list and sends it to the default output cmdlet for display.</span></span>

### <span data-ttu-id="ce7ff-118">예제 2: TYPES.PS1XML 파일 서식 지정</span><span class="sxs-lookup"><span data-stu-id="ce7ff-118">Example 2: Format PS1XML files</span></span>

<span data-ttu-id="ce7ff-119">이러한 명령은 PowerShell 디렉터리의 TYPES.PS1XML 파일에 대 한 정보를 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-119">These commands display information about the PS1XML files in the PowerShell directory as a list.</span></span>

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

<span data-ttu-id="ce7ff-120">첫 번째 명령은 파일을 나타내는 개체를 가져와 변수에 저장 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-120">The first command gets the objects representing the files and stores them in the `$A` variable.</span></span>

<span data-ttu-id="ce7ff-121">두 번째 명령은 `Format-List` 를 사용 하 여에 저장 된 개체에 대 한 정보를 형식으로 지정 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-121">The second command uses `Format-List` to format information about objects stored in `$A`.</span></span> <span data-ttu-id="ce7ff-122">이 명령은 **InputObject** 매개 변수를 사용 하 여 변수를에 전달 `Format-List` 합니다. 그러면에서 표시를 위해 형식이 지정 된 출력을 기본 출력 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-122">This command uses the **InputObject** parameter to pass the variable to `Format-List`, which then sends the formatted output to the default output cmdlet for display.</span></span>

### <span data-ttu-id="ce7ff-123">예제 3: 이름을 기준으로 프로세스 속성 서식 지정</span><span class="sxs-lookup"><span data-stu-id="ce7ff-123">Example 3: Format process properties by name</span></span>

<span data-ttu-id="ce7ff-124">이 명령은 컴퓨터에 있는 각 프로세스의 이름, 기본 우선 순위 및 우선 순위 클래스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-124">This command displays the name, base priority, and priority class of each process on the computer.</span></span>

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

<span data-ttu-id="ce7ff-125">Cmdlet을 사용 하 여 `Get-Process` 각 프로세스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-125">It uses the `Get-Process` cmdlet to get an object representing each process.</span></span> <span data-ttu-id="ce7ff-126">파이프라인 연산자 (|)가 파이프라인을 통해 프로세스 개체를에 전달 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-126">The pipeline operator (|) passes the process objects through the pipeline to `Format-List`.</span></span> <span data-ttu-id="ce7ff-127">`Format-List` 프로세스의 형식을 지정 된 속성 목록으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-127">`Format-List` formats the processes as a list of the specified properties.</span></span> <span data-ttu-id="ce7ff-128">*속성* 매개 변수 이름은 선택 사항 이므로 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-128">The *Property* parameter name is optional, so you can omit it.</span></span>

### <span data-ttu-id="ce7ff-129">예제 4: 프로세스의 모든 속성 서식 지정</span><span class="sxs-lookup"><span data-stu-id="ce7ff-129">Example 4: Format all properties for a process</span></span>

<span data-ttu-id="ce7ff-130">이 명령은 Winlogon 프로세스의 모든 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-130">This command displays all of the properties of the Winlogon process.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="ce7ff-131">Get-Process cmdlet을 사용하여 Winlogon 프로세스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-131">It uses the Get-Process cmdlet to get an object representing the Winlogon process.</span></span> <span data-ttu-id="ce7ff-132">파이프라인 연산자 (|)가 파이프라인을 통해 Winlogon 프로세스 개체를에 전달 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-132">The pipeline operator (|) passes the Winlogon process object through the pipeline to `Format-List`.</span></span> <span data-ttu-id="ce7ff-133">이 명령은 *Property* 매개 변수를 사용 하 여 속성을 지정 하 고를 사용 하 여 \* 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-133">The command uses the *Property* parameter to specify the properties and the \* to indicate all properties.</span></span>
<span data-ttu-id="ce7ff-134">*Property* 매개 변수의 이름은 선택 사항 이므로 생략 하 고 명령을 입력할 수 있습니다 `Format-List *` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-134">Because the name of the *Property* parameter is optional, you can omit it and type the command as `Format-List *`.</span></span> <span data-ttu-id="ce7ff-135">`Format-List` 표시를 위해 결과를 기본 출력 cmdlet으로 자동으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-135">`Format-List` automatically sends the results to the default output cmdlet for display.</span></span>

### <span data-ttu-id="ce7ff-136">예 5: 형식 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="ce7ff-136">Example 5: Troubleshooting format errors</span></span>

<span data-ttu-id="ce7ff-137">다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-137">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

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

## <span data-ttu-id="ce7ff-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ce7ff-138">PARAMETERS</span></span>

### <span data-ttu-id="ce7ff-139">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="ce7ff-139">-DisplayError</span></span>

<span data-ttu-id="ce7ff-140">이 cmdlet이 명령줄에서 오류를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-140">Indicates that this cmdlet displays errors at the command line.</span></span> <span data-ttu-id="ce7ff-141">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-141">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="ce7ff-142">-확장</span><span class="sxs-lookup"><span data-stu-id="ce7ff-142">-Expand</span></span>

<span data-ttu-id="ce7ff-143">컬렉션에 있는 개체 뿐만 아니라 서식이 지정 된 컬렉션 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-143">Specifies the formatted collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="ce7ff-144">이 매개 변수는 ICollection(System.Collections) 인터페이스를 지원하는 개체의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-144">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="ce7ff-145">기본값은 EnumOnly입니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-145">The default value is EnumOnly.</span></span> <span data-ttu-id="ce7ff-146">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ce7ff-147">EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-147">EnumOnly.</span></span> <span data-ttu-id="ce7ff-148">컬렉션에 있는 개체의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-148">Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="ce7ff-149">CoreOnly.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-149">CoreOnly.</span></span> <span data-ttu-id="ce7ff-150">컬렉션 개체의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-150">Displays the properties of the collection object.</span></span>
- <span data-ttu-id="ce7ff-151">둘 다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-151">Both.</span></span> <span data-ttu-id="ce7ff-152">컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-152">Displays the properties of the collection object and the properties of objects in the collection.</span></span>

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

### <span data-ttu-id="ce7ff-153">-Force</span><span class="sxs-lookup"><span data-stu-id="ce7ff-153">-Force</span></span>

<span data-ttu-id="ce7ff-154">이 cmdlet이 모든 오류 정보를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-154">Indicates that this cmdlet displays all of the error information.</span></span> <span data-ttu-id="ce7ff-155">**Displayerror** 또는 **showerror** 매개 변수와 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-155">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="ce7ff-156">기본적으로 오류 또는 표시 스트림에 오류 개체를 쓰는 경우 일부 오류 정보만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-156">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="ce7ff-157">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="ce7ff-157">-GroupBy</span></span>

<span data-ttu-id="ce7ff-158">공유 속성이 나 값에 따라 그룹의 출력을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-158">Specifies the output in groups based on a shared property or value.</span></span> <span data-ttu-id="ce7ff-159">출력의 식이나 속성을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-159">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="ce7ff-160">**GroupBy** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-160">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="ce7ff-161">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-161">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="ce7ff-162">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-162">Valid key-value pairs are:</span></span>

- <span data-ttu-id="ce7ff-163">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="ce7ff-163">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="ce7ff-164">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="ce7ff-164">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="ce7ff-165">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="ce7ff-165">FormatString - `<string>`</span></span>

<span data-ttu-id="ce7ff-166">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-166">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="ce7ff-167">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ce7ff-167">-InputObject</span></span>

<span data-ttu-id="ce7ff-168">형식을 지정할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-168">Specifies the objects to be formatted.</span></span> <span data-ttu-id="ce7ff-169">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-169">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="ce7ff-170">-속성</span><span class="sxs-lookup"><span data-stu-id="ce7ff-170">-Property</span></span>

<span data-ttu-id="ce7ff-171">표시에 나타나는 개체 속성 및 표시되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-171">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="ce7ff-172">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-172">Wildcards are permitted.</span></span>

<span data-ttu-id="ce7ff-173">이 매개 변수를 생략할 경우 표시에 나타나는 속성은 표시되는 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-173">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="ce7ff-174">"Property" 매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-174">The parameter name "Property" is optional.</span></span> <span data-ttu-id="ce7ff-175">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-175">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="ce7ff-176">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-176">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="ce7ff-177">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-177">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="ce7ff-178">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-178">Valid key-value pairs are:</span></span>

- <span data-ttu-id="ce7ff-179">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="ce7ff-179">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="ce7ff-180">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="ce7ff-180">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="ce7ff-181">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="ce7ff-181">FormatString - `<string>`</span></span>

<span data-ttu-id="ce7ff-182">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-182">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="ce7ff-183">-ShowError</span><span class="sxs-lookup"><span data-stu-id="ce7ff-183">-ShowError</span></span>

<span data-ttu-id="ce7ff-184">Cmdlet이 파이프라인을 통해 오류를 보내도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-184">Indicates that the cmdlet sends errors through the pipeline.</span></span> <span data-ttu-id="ce7ff-185">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-185">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="ce7ff-186">-보기</span><span class="sxs-lookup"><span data-stu-id="ce7ff-186">-View</span></span>

<span data-ttu-id="ce7ff-187">대체 목록 형식 또는 보기의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-187">Specifies the name of an alternate list format or view.</span></span> <span data-ttu-id="ce7ff-188">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-188">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="ce7ff-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ce7ff-189">CommonParameters</span></span>

<span data-ttu-id="ce7ff-190">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ce7ff-191">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ce7ff-192">입력</span><span class="sxs-lookup"><span data-stu-id="ce7ff-192">INPUTS</span></span>

### <span data-ttu-id="ce7ff-193">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="ce7ff-193">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="ce7ff-194">모든 개체를로 파이프 할 수 있습니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-194">You can pipe any object to `Format-List`.</span></span>

## <span data-ttu-id="ce7ff-195">출력</span><span class="sxs-lookup"><span data-stu-id="ce7ff-195">OUTPUTS</span></span>

### <span data-ttu-id="ce7ff-196">Microsoft. PowerShell. Internal. Format</span><span class="sxs-lookup"><span data-stu-id="ce7ff-196">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="ce7ff-197">`Format-List` 목록을 나타내는 형식 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-197">`Format-List` returns the format objects that represent the list.</span></span>

## <span data-ttu-id="ce7ff-198">참고</span><span class="sxs-lookup"><span data-stu-id="ce7ff-198">NOTES</span></span>

<span data-ttu-id="ce7ff-199">기본 제공 별칭인 FL로 Format-List을 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-199">You can also refer to Format-List by its built-in alias, FL.</span></span> <span data-ttu-id="ce7ff-200">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-200">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="ce7ff-201">와 같은 형식 cmdlet은 `Format-List` 표시할 데이터를 정렬 하지만 표시 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-201">The format cmdlets, such as `Format-List`, arrange the data to be displayed but do not display it.</span></span>
<span data-ttu-id="ce7ff-202">데이터는 PowerShell의 출력 기능 및 Out 동사 (Out cmdlet)를 포함 하는 cmdlet (예: 또는)에 의해 표시 됩니다 `Out-Host` `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="ce7ff-202">The data is displayed by the output features of PowerShell and by the cmdlets that contain the Out verb (the Out cmdlets), such as `Out-Host` or `Out-File`.</span></span>

<span data-ttu-id="ce7ff-203">Format cmdlet을 사용 하지 않는 경우 PowerShell은 표시 하는 각 개체에 대해 기본 형식을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-203">If you do not use a format cmdlet, PowerShell applies that default format for each object that it displays.</span></span>

<span data-ttu-id="ce7ff-204">**GroupBy** 매개 변수는 개체가 정렬 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-204">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="ce7ff-205">를 사용 하 여 개체를 그룹화 하기 전에 Sort-Object `Format-List` 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-205">Use Sort-Object before using `Format-List` to group the objects.</span></span>

<span data-ttu-id="ce7ff-206">**View** 매개 변수를 사용 하 여 테이블에 대 한 대체 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-206">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="ce7ff-207">PowerShell 디렉터리의 파일에 정의 된 뷰를 사용 `*.format.PS1XML` 하거나 새 types.ps1xml 파일에서 고유한 뷰를 만들고 Update-FormatData cmdlet을 사용 하 여 powershell에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-207">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the Update-FormatData cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="ce7ff-208">**View** 매개 변수의 대체 보기는 목록 형식을 사용 해야 합니다. 그렇지 않으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-208">The alternate view for the **View** parameter must use the list format, otherwise, the command fails.</span></span> <span data-ttu-id="ce7ff-209">대체 뷰가 테이블인 경우를 사용 `Format-Table` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-209">If the alternate view is a table, use `Format-Table`.</span></span> <span data-ttu-id="ce7ff-210">대체 뷰가 목록이 나 테이블이 아닌 경우를 사용 `Format-Custom` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce7ff-210">If the alternate view is not a list or a table, use `Format-Custom`.</span></span>

## <span data-ttu-id="ce7ff-211">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ce7ff-211">RELATED LINKS</span></span>

[<span data-ttu-id="ce7ff-212">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="ce7ff-212">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="ce7ff-213">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="ce7ff-213">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="ce7ff-214">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="ce7ff-214">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="ce7ff-215">Format-Table</span><span class="sxs-lookup"><span data-stu-id="ce7ff-215">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="ce7ff-216">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="ce7ff-216">Format-Wide</span></span>](Format-Wide.md)
