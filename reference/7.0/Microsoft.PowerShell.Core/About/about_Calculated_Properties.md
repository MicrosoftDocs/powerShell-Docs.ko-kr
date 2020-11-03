---
description: PowerShell은 새 속성을 동적으로 추가 하 고 파이프라인에 대 한 개체 출력의 형식을 변경 하는 기능을 제공 합니다.
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 7937d4e59f2e73c8b52e9957dd143b6d48eeae57
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220754"
---
# <a name="about-calculated-properties"></a><span data-ttu-id="b2155-103">계산 된 속성 정보</span><span class="sxs-lookup"><span data-stu-id="b2155-103">About calculated properties</span></span>

## <a name="short-description"></a><span data-ttu-id="b2155-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="b2155-104">Short Description</span></span>

<span data-ttu-id="b2155-105">PowerShell은 새 속성을 동적으로 추가 하 고 파이프라인에 대 한 개체 출력의 형식을 변경 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-105">PowerShell provides the ability to dynamically add new properties and alter the formatting of objects output to the pipeline.</span></span>

## <a name="long-description"></a><span data-ttu-id="b2155-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="b2155-106">Long Description</span></span>

<span data-ttu-id="b2155-107">많은 PowerShell cmdlet이 출력 개체에 새 속성을 추가할 수 있는 매개 변수를 사용 하 여 입력 개체를 출력 개체로 변환, 집계 또는 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-107">A number of PowerShell cmdlets transform, aggregate, or process input objects into output objects using parameters that allow the addition of new properties to those output objects.</span></span> <span data-ttu-id="b2155-108">이러한 매개 변수를 사용 하 여 입력 개체의 값을 기반으로 출력 개체에서 계산 된 새 속성을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-108">These parameters can be used to generate new, calculated properties on output objects based on the values of input objects.</span></span>
<span data-ttu-id="b2155-109">계산 된 속성은 새 속성의 이름, 값을 계산 하는 식 및 선택적 형식 지정 정보를 지정 하는 키-값 쌍을 포함 하는 [해시 테이블](about_hash_tables.md) 에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-109">The calculated property is defined by a [hashtable](about_hash_tables.md) containing key-value pairs that specify the name of the new property, an expression to calculate the value, and optional formatting information.</span></span>

## <a name="supported-cmdlets"></a><span data-ttu-id="b2155-110">지원되는 cmdlet</span><span class="sxs-lookup"><span data-stu-id="b2155-110">Supported cmdlets</span></span>

<span data-ttu-id="b2155-111">다음 cmdlet은 **property** 매개 변수에 대해 계산 된 속성 값을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-111">The following cmdlets support calculated property values for the **Property** parameter.</span></span> <span data-ttu-id="b2155-112">`Format-*`또한이 cmdlet은 **GroupBy** 매개 변수에 대해 계산 된 값을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-112">The `Format-*` cmdlets also support calculated values for the **GroupBy** parameter.</span></span>

<span data-ttu-id="b2155-113">다음 목록에서는 각 cmdlet에서 지 원하는 계산 된 속성 및 키-값 쌍을 지 원하는 cmdlet을 항목별로 요약 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-113">The following list itemizes the cmdlets that support calculated properties and the key-value pairs that are supported by each cmdlet.</span></span>

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - <span data-ttu-id="b2155-114">`name`/`label` -선택 사항 (PowerShell 6.x에 추가 됨)</span><span class="sxs-lookup"><span data-stu-id="b2155-114">`name`/`label` - optional (added in PowerShell 6.x)</span></span>
  - `expression`
  - <span data-ttu-id="b2155-115">`width` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-115">`width` - optional</span></span>
  - <span data-ttu-id="b2155-116">`alignment` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-116">`alignment` - optional</span></span>

- `Format-Custom`
  - `expression`
  - <span data-ttu-id="b2155-117">`depth` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-117">`depth` - optional</span></span>

- `Format-List`
  - <span data-ttu-id="b2155-118">`name`/`label` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-118">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="b2155-119">`formatstring` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-119">`formatstring` - optional</span></span>

  <span data-ttu-id="b2155-120">이 동일한 키-값 쌍 집합은 모든 cmdlet에 대해 **GroupBy** 매개 변수에 전달 된 계산 된 속성 값에도 적용 `Format-*` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-120">This same set of key-value pairs also apply to calculated property values passed to the **GroupBy** parameter for all `Format-*` cmdlets.</span></span>

- `Format-Table`
  - <span data-ttu-id="b2155-121">`name`/`label` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-121">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="b2155-122">`formatstring` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-122">`formatstring` - optional</span></span>
  - <span data-ttu-id="b2155-123">`width` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-123">`width` - optional</span></span>
  - <span data-ttu-id="b2155-124">`alignment` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-124">`alignment` - optional</span></span>

- `Format-Wide`
  - `expression`
  - <span data-ttu-id="b2155-125">`formatstring` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-125">`formatstring` - optional</span></span>

- `Group-Object`
  - `expression`

- `Measure-Object`
  - <span data-ttu-id="b2155-126">는 해시 테이블이 아닌 식에 대 한 스크립트 블록만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-126">Only supports a script block for the expression, not a hashtable.</span></span>
  - <span data-ttu-id="b2155-127">PowerShell 5.1 이상에서는 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-127">Not supported in PowerShell 5.1 and older.</span></span>

- `Select-Object`
  - <span data-ttu-id="b2155-128">`name`/`label` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-128">`name`/`label` - optional</span></span>
  - `expression`

- `Sort-Object`
  - `expression`
  - <span data-ttu-id="b2155-129">`ascending`/`descending` -선택 사항</span><span class="sxs-lookup"><span data-stu-id="b2155-129">`ascending`/`descending` - optional</span></span>

> [!NOTE]
> <span data-ttu-id="b2155-130">의 값은 `expression` hashtable 대신 스크립트 블록이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-130">The value of the `expression` can be a script block instead of a hashtable.</span></span> <span data-ttu-id="b2155-131">자세한 내용은 [참고](#notes) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2155-131">For more information, see the [Notes](#notes) section.</span></span>

## <a name="hashtable-key-definitions"></a><span data-ttu-id="b2155-132">Hashtable 키 정의</span><span class="sxs-lookup"><span data-stu-id="b2155-132">Hashtable key definitions</span></span>

- <span data-ttu-id="b2155-133">`name`/`label` -만들려는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-133">`name`/`label` - Specifies the name of the property being created.</span></span> <span data-ttu-id="b2155-134">또는 해당 별칭 ()을 사용할 수 있습니다 `name` `label` .</span><span class="sxs-lookup"><span data-stu-id="b2155-134">You can use `name` or its alias, `label`, interchangeably.</span></span>
- <span data-ttu-id="b2155-135">`expression` -새 속성의 값을 계산 하는 데 사용 되는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-135">`expression` - A script block used to calculate the value of the new property.</span></span>
- <span data-ttu-id="b2155-136">`alignment` -열에 값이 표시 되는 방식을 정의 하는 테이블 형식 출력을 생성 하는 cmdlet에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-136">`alignment` - Used by cmdlets that produce tabular output to define how the values are displayed in a column.</span></span> <span data-ttu-id="b2155-137">값은 `'left'` , 또는 여야 합니다 `'center'` `'right'` .</span><span class="sxs-lookup"><span data-stu-id="b2155-137">The value must be `'left'`, `'center'`, or `'right'`.</span></span>
- <span data-ttu-id="b2155-138">`formatstring` -출력에 대 한 값의 형식을 지정 하는 방법을 정의 하는 형식 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-138">`formatstring` - Specifies a format string that defines how the value is formatted for output.</span></span> <span data-ttu-id="b2155-139">서식 문자열에 대 한 자세한 내용은 [.net의 서식 형식](/dotnet/standard/base-types/formatting-types)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2155-139">For more information about format strings, see [Format types in .NET](/dotnet/standard/base-types/formatting-types).</span></span>
- <span data-ttu-id="b2155-140">`width` -값이 표시 될 때 테이블의 최대 너비 열 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-140">`width` - Specifies the maximum width column in a table when the value is displayed.</span></span> <span data-ttu-id="b2155-141">값은 보다 커야 합니다 `0` .</span><span class="sxs-lookup"><span data-stu-id="b2155-141">The value must be greater than `0`.</span></span>
- <span data-ttu-id="b2155-142">`depth` -의 **depth** 매개 변수는 `Format-Custom` 모든 속성에 대 한 확장 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-142">`depth` - The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="b2155-143">키를 사용 하 여 `depth` 속성 당 확장의 깊이를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-143">The `depth` key allows you to specify the depth of expansion per property.</span></span>
- <span data-ttu-id="b2155-144">`ascending` / `descending` -하나 이상의 속성에 대 한 정렬 순서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-144">`ascending` / `descending` - Allows you to specify the order of sorting for one or more properties.</span></span> <span data-ttu-id="b2155-145">이러한 값은 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-145">These are boolean values.</span></span>

<span data-ttu-id="b2155-146">지정 된 이름 접두사가 명확 하지 않으면 해시 테이블 키의 철자를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-146">The hashtable keys need not be spelled out as long as the specified name prefix is unambiguous.</span></span> <span data-ttu-id="b2155-147">예를 들어,는 대신 사용할 수 있으며 대신 사용할 수 있습니다 `n` `Name` `e` `Expression` .</span><span class="sxs-lookup"><span data-stu-id="b2155-147">For example, `n` can be used in lieu of `Name` and `e` can be used in lieu of `Expression`.</span></span>

## <a name="examples"></a><span data-ttu-id="b2155-148">예</span><span class="sxs-lookup"><span data-stu-id="b2155-148">Examples</span></span>

### <a name="compare-object"></a><span data-ttu-id="b2155-149">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-149">Compare-Object</span></span>

<span data-ttu-id="b2155-150">계산 된 속성을 사용 하 여 입력 개체의 속성을 비교 하는 방법을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-150">With calculated properties, you can control how the properties of the input objects are compared.</span></span> <span data-ttu-id="b2155-151">이 예제에서 값을 직접 비교 하는 대신 값을 산술 연산 (2 모듈러스)의 결과와 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-151">In this example, rather than comparing the values directly, the values are compared to the result of the arithmetic operation (modulus of 2).</span></span>

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a><span data-ttu-id="b2155-152">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="b2155-152">ConvertTo-Html</span></span>

<span data-ttu-id="b2155-153">`ConvertTo-Html` 개체의 컬렉션을 HTML 테이블로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-153">`ConvertTo-Html` can convert a collection of objects to an HTML table.</span></span>
<span data-ttu-id="b2155-154">계산 된 속성을 사용 하면 테이블이 표시 되는 방식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-154">Calculated properties allow you to control how the table is presented.</span></span>

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

<span data-ttu-id="b2155-155">이 예에서는 각 별칭 지정 된 명령에 대 한 PowerShell 별칭 목록과 숫자 매개 변수를 포함 하는 HTML 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-155">This example creates an HTML table containing a list of PowerShell aliases and the number parameters for each aliased command.</span></span> <span data-ttu-id="b2155-156">**Parametercount** 열의 값이 가운데에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-156">The values of **ParameterCount** column are centered.</span></span>

### <a name="format-custom"></a><span data-ttu-id="b2155-157">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="b2155-157">Format-Custom</span></span>

<span data-ttu-id="b2155-158">`Format-Custom` 클래스 정의와 유사한 형식으로 개체의 사용자 지정 뷰를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-158">`Format-Custom` provides a custom view of an object in a format similar to a class definition.</span></span> <span data-ttu-id="b2155-159">더 복잡 한 개체는 복합 형식으로 깊게 중첩 된 멤버를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-159">More complex objects can contain members that are deeply nested with complex types.</span></span> <span data-ttu-id="b2155-160">의 **depth** 매개 변수는 `Format-Custom` 모든 속성에 대 한 확장 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-160">The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="b2155-161">키를 사용 하 여 `depth` 속성 당 확장의 깊이를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-161">The `depth` key allows you to specify the depth of expansion per property.</span></span>

<span data-ttu-id="b2155-162">이 예제에서 `depth` 키는 cmdlet에 대 한 사용자 지정 출력을 단순화 합니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="b2155-162">In this example, the `depth` key simplifies the custom output for the `Get-Date` cmdlet.</span></span> <span data-ttu-id="b2155-163">`Get-Date`**DateTime** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-163">`Get-Date` returns a **DateTime** object.</span></span> <span data-ttu-id="b2155-164">또한이 개체의 **Date** 속성은 **DateTime** 개체 이므로 개체가 중첩 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-164">The **Date** property of this object is also a **DateTime** object, so the object is nested.</span></span>

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a><span data-ttu-id="b2155-165">Format-List</span><span class="sxs-lookup"><span data-stu-id="b2155-165">Format-List</span></span>

<span data-ttu-id="b2155-166">이 예에서는 계산 된 속성을 사용 하 여 출력의 이름과 형식을 변경 `Get-ChildItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-166">In this example, we use calculated properties to change the name and format of the output from `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a><span data-ttu-id="b2155-167">Format-Table</span><span class="sxs-lookup"><span data-stu-id="b2155-167">Format-Table</span></span>

<span data-ttu-id="b2155-168">이 예제에서 계산 된 속성은 콘텐츠 형식으로 파일을 분류 하는 데 사용 되는 **형식** 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-168">In this example, the calculated property adds a **Type** property used to classify the files by the content type.</span></span>

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a><span data-ttu-id="b2155-169">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="b2155-169">Format-Wide</span></span>

<span data-ttu-id="b2155-170">`Format-Wide`Cmdlet을 사용 하면 컬렉션의 개체에 대 한 하나의 속성 값을 여러 열 목록으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-170">The `Format-Wide` cmdlet allows you to display the value of one property for objects in a collection as a multi-column list.</span></span>

<span data-ttu-id="b2155-171">이 예에서는 파일 이름 및 크기 (kb)를 광범위 한 목록으로 표시 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-171">For this example, we want to see the filename and the size (in kilobytes) as a wide listing.</span></span> <span data-ttu-id="b2155-172">`Format-Wide`에는 두 개 이상의 속성이 표시 되지 않으므로 계산 된 속성을 사용 하 여 두 속성의 값을 단일 값으로 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-172">Since `Format-Wide` does not display more than one property, we use a calculated property to combine the value of two properties into a single value.</span></span>

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a><span data-ttu-id="b2155-173">Group-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-173">Group-Object</span></span>

<span data-ttu-id="b2155-174">`Group-Object`Cmdlet은 지정 된 속성의 값을 기준으로 개체를 그룹으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-174">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span> <span data-ttu-id="b2155-175">이 예제에서 계산 된 속성은 각 콘텐츠 형식의 파일 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-175">In this example, the calculated property counts the number of files of each content type.</span></span>

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="measure-object"></a><span data-ttu-id="b2155-176">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-176">Measure-Object</span></span>

<span data-ttu-id="b2155-177">`Measure-Object`Cmdlet은 개체의 숫자 속성을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-177">The `Measure-Object` cmdlet calculates the numeric properties of objects.</span></span> <span data-ttu-id="b2155-178">이 예에서는 계산 된 속성을 사용 하 여 3으로 균등 하 게 나눌 수 있는 숫자 ( **합계** )를 1에서 10 사이에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-178">In this example, we use a calculated property to get the count ( **Sum** ) of the numbers, between 1 and 10, that are evenly divisible by 3.</span></span>

```powershell
1..10 | Measure-Object -Property {($_ % 3) -eq 0} -Sum
```

```Output
Count             : 10
Average           :
Sum               : 3
Maximum           :
Minimum           :
StandardDeviation :
Property          : ($_ % 3) -eq 0
```

> [!NOTE]
> <span data-ttu-id="b2155-179">다른 cmdlet과 달리는 `Measure-Object` 계산 된 속성에 대 한 해시 테이블을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-179">Unlike the other cmdlets, `Measure-Object` does not accept a hashtable for calculated properties.</span></span> <span data-ttu-id="b2155-180">스크립트 블록을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-180">You must use a script block.</span></span>

### <a name="select-object"></a><span data-ttu-id="b2155-181">Select-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-181">Select-Object</span></span>

<span data-ttu-id="b2155-182">계산 된 속성을 사용 하 여 cmdlet을 통해 개체 출력에 멤버를 더 추가할 수 있습니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="b2155-182">You can use calculated properties to add additional members to the objects output with the `Select-Object` cmdlet.</span></span> <span data-ttu-id="b2155-183">이 예제에서는 문자로 시작 하는 PowerShell 별칭을 나열 합니다 `C` .</span><span class="sxs-lookup"><span data-stu-id="b2155-183">In this example, we are listing the PowerShell aliases that begin with the letter `C`.</span></span> <span data-ttu-id="b2155-184">를 사용 하 여 `Select-Object` 별칭, 별칭이 매핑된 cmdlet 및 cmdlet에 대해 정의 된 매개 변수의 개수를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-184">Using `Select-Object`, we output the alias, the cmdlet it's mapped to, and a count for the number of parameters defined for the cmdlet.</span></span> <span data-ttu-id="b2155-185">계산 된 속성을 사용 하 여 **Parametercount** 속성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-185">Using a calculated property, we can create the **ParameterCount** property.</span></span>

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a><span data-ttu-id="b2155-186">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-186">Sort-Object</span></span>

<span data-ttu-id="b2155-187">계산 된 속성을 사용 하 여 속성 마다 다른 순서로 데이터를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-187">Using the calculated properties, you can sort data in different orders per property.</span></span> <span data-ttu-id="b2155-188">이 예에서는 CSV 파일의 데이터를 **날짜별** 로 오름차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-188">This example sorts data from a CSV file in ascending order by **Date**.</span></span> <span data-ttu-id="b2155-189">그러나 각 날짜 내에서 행을 **UnitsSold** 기준으로 내림차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-189">But within each date, it sorts the rows in descending order by **UnitsSold**.</span></span>

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a><span data-ttu-id="b2155-190">메모</span><span class="sxs-lookup"><span data-stu-id="b2155-190">Notes</span></span>

- <span data-ttu-id="b2155-191">식 스크립트 블록을 _directly_ `Expression` 해시 테이블의 항목으로 지정 하는 대신 인수로 직접 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-191">You may specify the expression script block _directly_ , as an argument, rather than specifying it as the `Expression` entry in a hashtable.</span></span> <span data-ttu-id="b2155-192">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="b2155-192">For example:</span></span>

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  <span data-ttu-id="b2155-193">이 예제는,, 등의 키를 통해 속성 이름을 지정 하지 않거나 지원 하지 않는 cmdlet에 편리 `Name` `Sort-Object` `Group-Object` `Measure-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-193">This example is convenient for cmdlets that do not require (or support) naming a property via the `Name` key, such as `Sort-Object`, `Group-Object`, and `Measure-Object`.</span></span>

  <span data-ttu-id="b2155-194">속성 이름 지정을 지 원하는 cmdlet의 경우 스크립트 블록은 문자열로 변환 되 고 출력에서 속성의 이름으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-194">For cmdlets that support naming the property, the script block is converted to a string and used as the name of the property in the output.</span></span>

- <span data-ttu-id="b2155-195">`Expression` 스크립트 블록은 _자식_ 범위에서 실행 됩니다. 즉, 호출자의 변수를 직접 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-195">`Expression` script blocks run in _child_ scopes, meaning that the caller's variables cannot be directly modified.</span></span>

- <span data-ttu-id="b2155-196">파이프라인 논리는 스크립트 블록의 출력에 적용 됩니다 `Expression` .</span><span class="sxs-lookup"><span data-stu-id="b2155-196">Pipeline logic is applied to the output from `Expression` script blocks.</span></span> <span data-ttu-id="b2155-197">즉, 단일 요소 배열을 출력 하면 해당 배열이 래핑 해제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-197">This means that outputting a single-element array causes that array to be unwrapped.</span></span>

- <span data-ttu-id="b2155-198">대부분의 cmdlet에서 식 스크립트 블록 내의 오류는 자동으로 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-198">For most cmdlets, errors inside expression script blocks are quietly ignored.</span></span>
  <span data-ttu-id="b2155-199">`Sort-Object`에서 문 종료 및 스크립트 종료 오류는 _출력_ 이지만 문을 종료 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2155-199">For `Sort-Object`, statement-terminating and script-terminating errors are _output_ but they do not terminate the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2155-200">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2155-200">See Also</span></span>

[<span data-ttu-id="b2155-201">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="b2155-201">about_Hash_Tables</span></span>](about_hash_tables.md)

[<span data-ttu-id="b2155-202">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-202">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="b2155-203">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="b2155-203">ConvertTo-Html</span></span>](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[<span data-ttu-id="b2155-204">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="b2155-204">Format-Custom</span></span>](xref:Microsoft.PowerShell.Utility.Format-Custom)

[<span data-ttu-id="b2155-205">Format-List</span><span class="sxs-lookup"><span data-stu-id="b2155-205">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)

[<span data-ttu-id="b2155-206">Format-Table</span><span class="sxs-lookup"><span data-stu-id="b2155-206">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="b2155-207">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="b2155-207">Format-Wide</span></span>](xref:Microsoft.PowerShell.Utility.Format-Wide)

[<span data-ttu-id="b2155-208">Group-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-208">Group-Object</span></span>](xref:Microsoft.PowerShell.Utility.Group-Object)

[<span data-ttu-id="b2155-209">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-209">Measure-Object</span></span>](xref:Microsoft.PowerShell.Utility.Measure-Object)

[<span data-ttu-id="b2155-210">Select-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-210">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="b2155-211">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="b2155-211">Sort-Object</span></span>](xref:Microsoft.PowerShell.Utility.Sort-Object)

[<span data-ttu-id="b2155-212">.NET의 형식 유형</span><span class="sxs-lookup"><span data-stu-id="b2155-212">Format types in .NET</span></span>](/dotnet/standard/base-types/formatting-types)
