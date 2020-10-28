---
ms.date: 09/13/2019
title: FilterHashtable를 사용하여 Get-WinEvent 쿼리 만들기
description: 이 문서에서는 Get-WinEvent의 FilterHashtable을 사용하여 Windows 이벤트 로그를 쿼리하는 방법을 설명합니다.
ms.openlocfilehash: 8e080f17436d97adda277600cd202a0e6e9283e0
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500609"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="477f3-103">FilterHashtable를 사용하여 Get-WinEvent 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="477f3-103">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="477f3-104">2014년 6월 3일 자 원본 **Scripting Guy** 블로그 게시물을 읽으려면 [FilterHashTable을 사용하여 PowerShell을 통해 이벤트 로그 필터링](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="477f3-104">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="477f3-105">이 문서는 원래 블로그 게시물의 일부로, `Get-WinEvent` cmdlet의 **FilterHashtable** 매개 변수를 사용하여 이벤트 로그를 필터링하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-105">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="477f3-106">PowerShell의 `Get-WinEvent` cmdlet은 Windows 이벤트 및 진단 로그를 필터링하는 강력한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-106">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="477f3-107">`Get-WinEvent` 쿼리가 **FilterHashtable** 매개 변수를 사용하면 성능이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-107">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="477f3-108">대규모 이벤트 로그를 사용할 경우 개체를 파이프라인 아래로 보내 `Where-Object` 명령으로 전달하는 것은 효율적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-108">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="477f3-109">PowerShell 6 이전에는 `Get-EventLog` cmdlet이 로그 데이터를 가져오는 또 다른 옵션으로 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-109">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="477f3-110">예를 들어, 다음 명령은 **Microsoft-Windows-Defrag** 로그를 필터링하는 데 비효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-110">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

<span data-ttu-id="477f3-111">다음 명령은 성능을 향상시키는 해시 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-111">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="477f3-112">열거형에 관한 블로그 게시물</span><span class="sxs-lookup"><span data-stu-id="477f3-112">Blog posts about enumeration</span></span>

<span data-ttu-id="477f3-113">이 문서에서는 해시 테이블의 열거된 값을 사용하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-113">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="477f3-114">열거형에 대한 자세한 내용은 **Scripting Guy** 블로그 게시물을 읽어보세요.</span><span class="sxs-lookup"><span data-stu-id="477f3-114">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="477f3-115">열거된 값을 반환하는 함수를 만들려면 [열거형 및 값](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="477f3-115">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="477f3-116">자세한 내용은 [열거형에 대한 Scripting Guy 블로그 게시물 시리즈](https://devblogs.microsoft.com/scripting/?s=about+enumeration)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="477f3-116">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-key-value-pairs"></a><span data-ttu-id="477f3-117">해시 테이블 키-값 쌍</span><span class="sxs-lookup"><span data-stu-id="477f3-117">Hash table key-value pairs</span></span>

<span data-ttu-id="477f3-118">효율적인 쿼리를 작성하려면 `Get-WinEvent` cmdlet과 **FilterHashtable** 매개 변수를 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-118">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="477f3-119">**FilterHashtable** 은 Windows 이벤트 로그에서 특정 정보를 가져오기 위한 필터로 해시 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-119">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="477f3-120">해시 테이블은 **키-값** 쌍을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-120">A hash table uses **key-value** pairs.</span></span> <span data-ttu-id="477f3-121">해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="477f3-121">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="477f3-122">**키-값** 쌍이 같은 줄에 있으면 세미콜론으로 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-122">If the **key-value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="477f3-123">각 **키-값** 쌍이 서로 다른 줄에 있으면 세미콜론이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-123">If each **key-value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="477f3-124">예를 들어 이 문서에서는 **키-값** 쌍을 서로 다른 줄에 배치하며 세미콜론을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-124">For example, this article places **key-value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="477f3-125">이 샘플에서는 몇 가지 **FilterHashtable** 매개 변수의 **키-값** 쌍을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-125">This sample uses several of the **FilterHashtable** parameter's **key-value** pairs.</span></span> <span data-ttu-id="477f3-126">완료된 쿼리에는 **LogName** , **ProviderName** , **Keywords** , **ID** 및 **Level** 이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-126">The completed query includes **LogName** , **ProviderName** , **Keywords** , **ID** , and **Level** .</span></span>

<span data-ttu-id="477f3-127">허용되는 **키-값** 쌍은 다음 표에 표시되며 [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** 매개 변수에 대한 설명서에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-127">The accepted **key-value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="477f3-128">다음 표는 키 이름, 데이터 형식, 데이터 값에 대해 와일드카드 문자가 허용되는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-128">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

|    <span data-ttu-id="477f3-129">키 이름</span><span class="sxs-lookup"><span data-stu-id="477f3-129">Key name</span></span>    | <span data-ttu-id="477f3-130">값 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="477f3-130">Value data type</span></span> | <span data-ttu-id="477f3-131">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="477f3-131">Accepts wildcard characters?</span></span> |
| -------------- | --------------- | ---------------------------- |
| <span data-ttu-id="477f3-132">LogName</span><span class="sxs-lookup"><span data-stu-id="477f3-132">LogName</span></span>        | `<String[]>`    | <span data-ttu-id="477f3-133">예</span><span class="sxs-lookup"><span data-stu-id="477f3-133">Yes</span></span>                          |
| <span data-ttu-id="477f3-134">ProviderName</span><span class="sxs-lookup"><span data-stu-id="477f3-134">ProviderName</span></span>   | `<String[]>`    | <span data-ttu-id="477f3-135">예</span><span class="sxs-lookup"><span data-stu-id="477f3-135">Yes</span></span>                          |
| <span data-ttu-id="477f3-136">경로</span><span class="sxs-lookup"><span data-stu-id="477f3-136">Path</span></span>           | `<String[]>`    | <span data-ttu-id="477f3-137">예</span><span class="sxs-lookup"><span data-stu-id="477f3-137">No</span></span>                           |
| <span data-ttu-id="477f3-138">키워드</span><span class="sxs-lookup"><span data-stu-id="477f3-138">Keywords</span></span>       | `<Long[]>`      | <span data-ttu-id="477f3-139">예</span><span class="sxs-lookup"><span data-stu-id="477f3-139">No</span></span>                           |
| <span data-ttu-id="477f3-140">ID</span><span class="sxs-lookup"><span data-stu-id="477f3-140">ID</span></span>             | `<Int32[]>`     | <span data-ttu-id="477f3-141">예</span><span class="sxs-lookup"><span data-stu-id="477f3-141">No</span></span>                           |
| <span data-ttu-id="477f3-142">Level</span><span class="sxs-lookup"><span data-stu-id="477f3-142">Level</span></span>          | `<Int32[]>`     | <span data-ttu-id="477f3-143">예</span><span class="sxs-lookup"><span data-stu-id="477f3-143">No</span></span>                           |
| <span data-ttu-id="477f3-144">StartTime</span><span class="sxs-lookup"><span data-stu-id="477f3-144">StartTime</span></span>      | `<DateTime>`    | <span data-ttu-id="477f3-145">예</span><span class="sxs-lookup"><span data-stu-id="477f3-145">No</span></span>                           |
| <span data-ttu-id="477f3-146">EndTime</span><span class="sxs-lookup"><span data-stu-id="477f3-146">EndTime</span></span>        | `<DateTime>`    | <span data-ttu-id="477f3-147">예</span><span class="sxs-lookup"><span data-stu-id="477f3-147">No</span></span>                           |
| <span data-ttu-id="477f3-148">UserID</span><span class="sxs-lookup"><span data-stu-id="477f3-148">UserID</span></span>         | `<SID>`         | <span data-ttu-id="477f3-149">예</span><span class="sxs-lookup"><span data-stu-id="477f3-149">No</span></span>                           |
| <span data-ttu-id="477f3-150">데이터</span><span class="sxs-lookup"><span data-stu-id="477f3-150">Data</span></span>           | `<String[]>`    | <span data-ttu-id="477f3-151">예</span><span class="sxs-lookup"><span data-stu-id="477f3-151">No</span></span>                           |
| `<named-data>` | `<String[]>`    | <span data-ttu-id="477f3-152">예</span><span class="sxs-lookup"><span data-stu-id="477f3-152">No</span></span>                           |

<span data-ttu-id="477f3-153">`<named-data>` 키는 명명된 이벤트 데이터 필드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-153">The `<named-data>` key represents a named event data field.</span></span> <span data-ttu-id="477f3-154">예를 들어, Perflib 이벤트 1008은 다음 이벤트 데이터를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-154">For example, the Perflib event 1008 can contain the following event data:</span></span>

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

<span data-ttu-id="477f3-155">이러한 이벤트를 다음 명령을 사용하여 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-155">You can query for these events using the following command:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> <span data-ttu-id="477f3-156">`<named-data>`를 쿼리할 수 있는 기능이 PowerShell 6에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-156">The ability to query for `<named-data>` was added in PowerShell 6.</span></span>

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="477f3-157">해시 테이블을 사용하여 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="477f3-157">Building a query with a hash table</span></span>

<span data-ttu-id="477f3-158">결과를 확인하고 문제를 해결하려는 경우 **키-값** 쌍을 한 번에 하나씩 사용해서 해시 테이블을 빌드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-158">To verify results and troubleshoot problems, it helps to build the hash table one **key-value** pair at a time.</span></span> <span data-ttu-id="477f3-159">쿼리는 **애플리케이션** 로그에서 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-159">The query gets data from the **Application** log.</span></span> <span data-ttu-id="477f3-160">해시 테이블은 `Get-WinEvent –LogName Application`과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-160">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="477f3-161">시작하려면 `Get-WinEvent` 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-161">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="477f3-162">**FilterHashtable** 매개 변수의 **키-값** 쌍(키: **LogName** , 값: **Application** )을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-162">Use the **FilterHashtable** parameter's **key-value** pair with the key, **LogName** , and the value, **Application** .</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="477f3-163">**ProviderName** 키를 사용해서 해시 테이블을 계속 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-163">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="477f3-164">**ProviderName** 은 **Windows 이벤트 뷰어** 의 **원본** 필드에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-164">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer** .</span></span> <span data-ttu-id="477f3-165">예를 들어, 다음 스크린샷에서 **.NET Runtime** 입니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-165">For example, **.NET Runtime** in the following screenshot:</span></span>

![Windows 이벤트 뷰어 원본 이미지](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="477f3-167">해시 테이블을 업데이트하고 **키-값** 쌍(키: **ProviderName** , 값: **NET Runtime** )을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-167">Update the hash table and include the **key-value** pair with the key, **ProviderName** , and the value, **.NET Runtime** .</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="477f3-168">보관된 이벤트 로그에서 데이터를 가져오는 쿼리가 필요한 경우 **Path** 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-168">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="477f3-169">**Path** 값은 로그 파일에 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-169">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="477f3-170">자세한 내용은 **Scripting Guy** 블로그 게시물, [PowerShell을 사용하여 저장된 이벤트 로그에 오류가 있는지 구문 분석](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="477f3-170">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="477f3-171">해시 테이블에서 열거된 값 사용</span><span class="sxs-lookup"><span data-stu-id="477f3-171">Using enumerated values in a hash table</span></span>

<span data-ttu-id="477f3-172">**Keywords** 는 해시 테이블의 다음 키입니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-172">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="477f3-173">**Keywords** 데이터 형식은 큰 숫자를 포함하는 `[long]` 값 형식의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-173">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="477f3-174">다음 명령을 사용하여 `[long]`의 최대 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-174">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="477f3-175">**Keywords** 키의 경우 PowerShell은 **Security** 와 같은 문자열이 아니라 숫자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-175">For the **Keywords** key, PowerShell uses a number, not a string such as **Security** .</span></span> <span data-ttu-id="477f3-176">**Windows 이벤트 뷰어** 는 **Keywords** 를 문자열로 표시하지만 열거형 값입니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-176">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="477f3-177">해시 테이블에서 문자열 값에 **Keywords** 키를 사용하면 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-177">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="477f3-178">**Windows 이벤트 뷰어** 를 열고 **작업** 창에서 **현재 로그 필터링** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-178">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log** .</span></span>
<span data-ttu-id="477f3-179">**Keywords** 드롭다운 메뉴는 다음 스크린샷에 표시된 것처럼 사용할 수 있는 키워드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-179">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Windows 이벤트 뷰어 키워드 이미지](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="477f3-181">다음 명령을 사용하여 `StandardEventKeywords` 속성 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-181">Use the following command to display the `StandardEventKeywords` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

<span data-ttu-id="477f3-182">열거형 값은 **.NET Framework** 에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-182">The enumerated values are documented in the **.NET Framework** .</span></span> <span data-ttu-id="477f3-183">자세한 내용은 [StandardEventKeywords 열거형](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="477f3-183">For more information, see [StandardEventKeywords Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords).</span></span>

<span data-ttu-id="477f3-184">**Keywords** 이름 및 열거형 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-184">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="477f3-185">속성</span><span class="sxs-lookup"><span data-stu-id="477f3-185">Name</span></span>             |  <span data-ttu-id="477f3-186">값</span><span class="sxs-lookup"><span data-stu-id="477f3-186">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="477f3-187">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="477f3-187">AuditFailure</span></span>     | <span data-ttu-id="477f3-188">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="477f3-188">4503599627370496</span></span>  |
| <span data-ttu-id="477f3-189">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="477f3-189">AuditSuccess</span></span>     | <span data-ttu-id="477f3-190">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="477f3-190">9007199254740992</span></span>  |
| <span data-ttu-id="477f3-191">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="477f3-191">CorrelationHint2</span></span> | <span data-ttu-id="477f3-192">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="477f3-192">18014398509481984</span></span> |
| <span data-ttu-id="477f3-193">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="477f3-193">EventLogClassic</span></span>  | <span data-ttu-id="477f3-194">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="477f3-194">36028797018963968</span></span> |
| <span data-ttu-id="477f3-195">Sqm</span><span class="sxs-lookup"><span data-stu-id="477f3-195">Sqm</span></span>              | <span data-ttu-id="477f3-196">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="477f3-196">2251799813685248</span></span>  |
| <span data-ttu-id="477f3-197">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="477f3-197">WdiDiagnostic</span></span>    | <span data-ttu-id="477f3-198">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="477f3-198">1125899906842624</span></span>  |
| <span data-ttu-id="477f3-199">WdiContext</span><span class="sxs-lookup"><span data-stu-id="477f3-199">WdiContext</span></span>       | <span data-ttu-id="477f3-200">562949953421312</span><span class="sxs-lookup"><span data-stu-id="477f3-200">562949953421312</span></span>   |
| <span data-ttu-id="477f3-201">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="477f3-201">ResponseTime</span></span>     | <span data-ttu-id="477f3-202">281474976710656</span><span class="sxs-lookup"><span data-stu-id="477f3-202">281474976710656</span></span>   |
| <span data-ttu-id="477f3-203">None</span><span class="sxs-lookup"><span data-stu-id="477f3-203">None</span></span>             | <span data-ttu-id="477f3-204">0</span><span class="sxs-lookup"><span data-stu-id="477f3-204">0</span></span>                 |

<span data-ttu-id="477f3-205">해시 테이블을 업데이트하고 **키-값** 쌍(키: **Keywords** 및 **EventLogClassic** 열거형 값, **36028797018963968** )을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-205">Update the hash table and include the **key-value** pair with the key, **Keywords** , and the **EventLogClassic** enumeration value, **36028797018963968** .</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="477f3-206">Keywords 정적 속성 값(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="477f3-206">Keywords static property value (optional)</span></span>

<span data-ttu-id="477f3-207">**Keywords** 키는 열거형이지만 해시 테이블 쿼리에서 정적 속성 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-207">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="477f3-208">반환된 문자열을 사용하는 대신, 속성 이름을 **Value__** 속성을 갖는 값으로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-208">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="477f3-209">예를 들어, 다음 스크립트는 **Value__** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-209">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="477f3-210">이벤트 ID 기준으로 필터링</span><span class="sxs-lookup"><span data-stu-id="477f3-210">Filtering by Event Id</span></span>

<span data-ttu-id="477f3-211">보다 구체적인 데이터를 가져오기 위해 쿼리 결과가 **이벤트 ID** 를 기준으로 필터링됩니다. **이벤트 ID** 는 해시 테이블에서 키 **ID** 로 참조되고 해당 값은 특정 **이벤트 ID** 입니다. **Windows 이벤트 뷰어** 는 **이벤트 ID** 를 표시합니다. 이 예제에서는 **이벤트 ID 1023** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-211">To get more specific data, the query's results are filtered by **Event Id** . The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id** . The **Windows Event Viewer** displays the **Event Id** . This example uses **Event Id 1023** .</span></span>

<span data-ttu-id="477f3-212">해시 테이블을 업데이트하고 **키-값** 쌍(키: **ID** , 값: **1023** )을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-212">Update the hash table and include the **key-value** pair with the key, **ID** and the value, **1023** .</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="477f3-213">수준 기준 필터링</span><span class="sxs-lookup"><span data-stu-id="477f3-213">Filtering by Level</span></span>

<span data-ttu-id="477f3-214">결과를 구체화하고 오류가 있는 이벤트만 포함하려면 **Level** 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-214">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="477f3-215">**Windows 이벤트 뷰어** 는 **Level** 을 문자열 값으로 표시하지만, 열거형 값입니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-215">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="477f3-216">해시 테이블에서 문자열 값에 **Level** 키를 사용하면 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-216">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="477f3-217">**Level** 에는 **Error** , **Warning** 또는 **Informational** 과 같은 값이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-217">**Level** has values such as **Error** , **Warning** , or **Informational** .</span></span> <span data-ttu-id="477f3-218">다음 명령을 사용하여 `StandardEventLevel` 속성 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-218">Use the following command to display the `StandardEventLevel` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

<span data-ttu-id="477f3-219">열거형 값은 **.NET Framework** 에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-219">The enumerated values are documented in the **.NET Framework** .</span></span> <span data-ttu-id="477f3-220">자세한 내용은 [StandardEventLevel 열거형](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="477f3-220">For more information, see [StandardEventLevel Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel).</span></span>

<span data-ttu-id="477f3-221">**Level** 키의 이름 및 열거형 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-221">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="477f3-222">속성</span><span class="sxs-lookup"><span data-stu-id="477f3-222">Name</span></span>           | <span data-ttu-id="477f3-223">값</span><span class="sxs-lookup"><span data-stu-id="477f3-223">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="477f3-224">자세히</span><span class="sxs-lookup"><span data-stu-id="477f3-224">Verbose</span></span>        |   <span data-ttu-id="477f3-225">5</span><span class="sxs-lookup"><span data-stu-id="477f3-225">5</span></span>   |
| <span data-ttu-id="477f3-226">정보 제공</span><span class="sxs-lookup"><span data-stu-id="477f3-226">Informational</span></span>  |   <span data-ttu-id="477f3-227">4</span><span class="sxs-lookup"><span data-stu-id="477f3-227">4</span></span>   |
| <span data-ttu-id="477f3-228">Warning</span><span class="sxs-lookup"><span data-stu-id="477f3-228">Warning</span></span>        |   <span data-ttu-id="477f3-229">3</span><span class="sxs-lookup"><span data-stu-id="477f3-229">3</span></span>   |
| <span data-ttu-id="477f3-230">Error</span><span class="sxs-lookup"><span data-stu-id="477f3-230">Error</span></span>          |   <span data-ttu-id="477f3-231">2</span><span class="sxs-lookup"><span data-stu-id="477f3-231">2</span></span>   |
| <span data-ttu-id="477f3-232">위험</span><span class="sxs-lookup"><span data-stu-id="477f3-232">Critical</span></span>       |   <span data-ttu-id="477f3-233">1</span><span class="sxs-lookup"><span data-stu-id="477f3-233">1</span></span>   |
| <span data-ttu-id="477f3-234">LogAlways</span><span class="sxs-lookup"><span data-stu-id="477f3-234">LogAlways</span></span>      |   <span data-ttu-id="477f3-235">0</span><span class="sxs-lookup"><span data-stu-id="477f3-235">0</span></span>   |

<span data-ttu-id="477f3-236">완료된 쿼리에 대한 해시 테이블은 키, **Level** 및 값, **2** 를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-236">The hash table for the completed query includes the key, **Level** , and the value, **2** .</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="477f3-237">열거형의 Level 정적 속성(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="477f3-237">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="477f3-238">**Level** 키는 열거형이지만 해시 테이블 쿼리에서 정적 속성 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-238">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="477f3-239">반환된 문자열을 사용하는 대신, 속성 이름을 **Value__** 속성을 갖는 값으로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-239">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="477f3-240">예를 들어, 다음 스크립트는 **Value__** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="477f3-240">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```
