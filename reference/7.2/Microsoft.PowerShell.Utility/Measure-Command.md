---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 0c2346dc7177e091c0921cd4775422938305e2be
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "99599567"
---
# <span data-ttu-id="7a596-102">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="7a596-102">Measure-Command</span></span>

## <span data-ttu-id="7a596-103">개요</span><span class="sxs-lookup"><span data-stu-id="7a596-103">SYNOPSIS</span></span>
<span data-ttu-id="7a596-104">스크립트 블록 및 cmdlet을 실행하는 데 걸리는 시간을 측정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-104">Measures the time it takes to run script blocks and cmdlets.</span></span>

## <span data-ttu-id="7a596-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7a596-105">SYNTAX</span></span>

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="7a596-106">설명</span><span class="sxs-lookup"><span data-stu-id="7a596-106">DESCRIPTION</span></span>

<span data-ttu-id="7a596-107">`Measure-Command`Cmdlet은 작업 실행 시간을 지 나 스크립트 블록 또는 cmdlet을 내부적으로 실행 하 고 실행 시간을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-107">The `Measure-Command` cmdlet runs a script block or cmdlet internally, times the execution of the operation, and returns the execution time.</span></span>

> [!NOTE]
> <span data-ttu-id="7a596-108">스크립트 블록은 `Measure-Command` 자식 범위가 아니라 현재 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-108">Script blocks run by `Measure-Command` run in the current scope, not a child scope.</span></span>

## <span data-ttu-id="7a596-109">예제</span><span class="sxs-lookup"><span data-stu-id="7a596-109">EXAMPLES</span></span>

### <span data-ttu-id="7a596-110">예제 1: 명령 측정</span><span class="sxs-lookup"><span data-stu-id="7a596-110">Example 1: Measure a command</span></span>

<span data-ttu-id="7a596-111">이 예에서는 `Get-EventLog` Windows PowerShell 이벤트 로그에서 이벤트를 가져오는 명령을 실행 하는 데 걸리는 시간을 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-111">This example measures the time it takes to run a `Get-EventLog` command that gets the events in the Windows PowerShell event log.</span></span>

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### <span data-ttu-id="7a596-112">예제 2: Measure-Command에서 두 출력 비교</span><span class="sxs-lookup"><span data-stu-id="7a596-112">Example 2: Compare two outputs from Measure-Command</span></span>

<span data-ttu-id="7a596-113">첫 번째 명령은 `Get-ChildItem` **Path** 매개 변수를 사용 하 여 `.txt` `C:\Windows` 디렉터리 및 하위 디렉터리에 있는 파일만 가져오는 재귀 명령을 처리 하는 데 걸리는 시간을 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-113">The first command measures the time it takes to process a recursive `Get-ChildItem` command that uses the **Path** parameter to get only `.txt` files in the `C:\Windows` directory and its subdirectories.</span></span>

<span data-ttu-id="7a596-114">두 번째 명령은 `Get-ChildItem` 공급자별 ' 매개 변수를 사용 하는 재귀 명령을 처리 하는 데 걸리는 시간을 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-114">The second command measures the time it takes to process a recursive `Get-ChildItem` command that uses the provider-specific \` parameter.</span></span>

<span data-ttu-id="7a596-115">이러한 명령은 PowerShell 명령에서 공급자별 필터를 사용 하는 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-115">These commands show the value of using a provider-specific filter in PowerShell commands.</span></span>

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### <span data-ttu-id="7a596-116">예제 3: Measure-Command에 입력 파이핑</span><span class="sxs-lookup"><span data-stu-id="7a596-116">Example 3: Piping input to Measure-Command</span></span>

<span data-ttu-id="7a596-117">파이프 된 개체는 `Measure-Command` **Expression** 매개 변수에 전달 되는 스크립트 블록에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-117">Objects that are piped to `Measure-Command` are available to the script block that is passed to the **Expression** parameter.</span></span> <span data-ttu-id="7a596-118">스크립트 블록은 파이프라인의 각 개체에 대해 한 번씩 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-118">The script block is executed once for each object on the pipeline.</span></span>

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### <span data-ttu-id="7a596-119">예제 4: 측정 된 명령의 출력 표시</span><span class="sxs-lookup"><span data-stu-id="7a596-119">Example 4: Displaying output of measured command</span></span>

<span data-ttu-id="7a596-120">에서 식의 출력을 표시 하려면 `Measure-Command` 파이프를로 사용할 수 있습니다 `Out-Default` .</span><span class="sxs-lookup"><span data-stu-id="7a596-120">To display output of expression in `Measure-Command` you can use a pipe to `Out-Default`.</span></span>

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### <span data-ttu-id="7a596-121">예 5: 자식 범위에서 실행 측정</span><span class="sxs-lookup"><span data-stu-id="7a596-121">Example 5: Measuring execution in a child scope</span></span>

<span data-ttu-id="7a596-122">`Measure-Command` 현재 범위에서 스크립트 블록을 실행 하므로 스크립트 블록은 현재 범위의 값을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-122">`Measure-Command` runs the script block in the current scope, so the script block can modify values in the current scope.</span></span> <span data-ttu-id="7a596-123">현재 범위를 변경 하지 않으려면 스크립트 블록을 중괄호 ()로 래핑하고 `{}` 호출 연산자 ()를 사용 `&` 하 여 자식 범위에서 블록을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-123">To avoid changes to the current scope, you must wrap the script block in braces (`{}`) and use the invocation operator (`&`) to execute the block in a child scope.</span></span>

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

<span data-ttu-id="7a596-124">호출 연산자에 대 한 자세한 내용은 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a596-124">For more information about the invocation operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span></span>

## <span data-ttu-id="7a596-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7a596-125">PARAMETERS</span></span>

### <span data-ttu-id="7a596-126">-식</span><span class="sxs-lookup"><span data-stu-id="7a596-126">-Expression</span></span>

<span data-ttu-id="7a596-127">시간이 측정되는 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-127">Specifies the expression that is being timed.</span></span> <span data-ttu-id="7a596-128">식을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="7a596-128">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a596-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7a596-129">-InputObject</span></span>

<span data-ttu-id="7a596-130">**InputObject** 매개 변수에 바인딩된 개체는 **Expression** 매개 변수에 전달 된 스크립트 블록의 선택적 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-130">Objects bound to the **InputObject** parameter are optional input for the script block passed to the **Expression** parameter.</span></span> <span data-ttu-id="7a596-131">스크립트 블록 내에서를 `$_` 사용 하 여 파이프라인의 현재 개체를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-131">Inside the script block, `$_` can be used to reference the current object in the pipeline.</span></span>

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

### <span data-ttu-id="7a596-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a596-132">CommonParameters</span></span>

<span data-ttu-id="7a596-133">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a596-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a596-134">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a596-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a596-135">입력</span><span class="sxs-lookup"><span data-stu-id="7a596-135">INPUTS</span></span>

### <span data-ttu-id="7a596-136">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="7a596-136">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7a596-137">개체를로 파이프 할 수 있습니다 `Measure-Command` .</span><span class="sxs-lookup"><span data-stu-id="7a596-137">You can pipe an object to `Measure-Command`.</span></span>

## <span data-ttu-id="7a596-138">출력</span><span class="sxs-lookup"><span data-stu-id="7a596-138">OUTPUTS</span></span>

### <span data-ttu-id="7a596-139">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="7a596-139">System.TimeSpan</span></span>

<span data-ttu-id="7a596-140">`Measure-Command` 결과를 나타내는 시간 범위 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a596-140">`Measure-Command` returns a time span object that represents the result.</span></span>

## <span data-ttu-id="7a596-141">참고</span><span class="sxs-lookup"><span data-stu-id="7a596-141">NOTES</span></span>

## <span data-ttu-id="7a596-142">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7a596-142">RELATED LINKS</span></span>

[<span data-ttu-id="7a596-143">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="7a596-143">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="7a596-144">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="7a596-144">Trace-Command</span></span>](Trace-Command.md)

