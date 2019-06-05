---
ms.date: 03/18/2019
title: FilterHashtable를 사용하여 Get-WinEvent 쿼리 만들기
ms.openlocfilehash: 2f598fceb570f189bee776b6ed572b11a6938f64
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66471024"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="33ac4-102">FilterHashtable를 사용하여 Get-WinEvent 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="33ac4-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="33ac4-103">2014년 6월 3일 자 원본 **Scripting Guy** 블로그 게시물을 읽으려면 [FilterHashTable을 사용하여 PowerShell을 통해 이벤트 로그 필터링](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33ac4-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="33ac4-104">이 문서는 원래 블로그 게시물의 일부로, `Get-WinEvent` cmdlet의 **FilterHashtable** 매개 변수를 사용하여 이벤트 로그를 필터링하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="33ac4-105">PowerShell의 `Get-WinEvent` cmdlet은 Windows 이벤트 및 진단 로그를 필터링하는 강력한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="33ac4-106">`Get-WinEvent` 쿼리가 **FilterHashtable** 매개 변수를 사용하면 성능이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="33ac4-107">대규모 이벤트 로그를 사용할 경우 개체를 파이프라인 아래로 보내 `Where-Object` 명령으로 전달하는 것은 효율적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="33ac4-108">PowerShell 6 이전에는 `Get-EventLog` cmdlet이 로그 데이터를 가져오는 또 다른 옵션으로 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="33ac4-109">예를 들어, 다음 명령은 **Microsoft-Windows-Defrag** 로그를 필터링하는 데 비효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="33ac4-110">다음 명령은 성능을 향상시키는 해시 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="33ac4-111">열거형에 관한 블로그 게시물</span><span class="sxs-lookup"><span data-stu-id="33ac4-111">Blog posts about enumeration</span></span>

<span data-ttu-id="33ac4-112">이 문서에서는 해시 테이블의 열거된 값을 사용하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="33ac4-113">열거형에 대한 자세한 내용은 **Scripting Guy** 블로그 게시물을 읽어보세요.</span><span class="sxs-lookup"><span data-stu-id="33ac4-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="33ac4-114">열거된 값을 반환하는 함수를 만들려면 [열거형 및 값](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33ac4-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="33ac4-115">자세한 내용은 [열거형에 대한 Scripting Guy 블로그 게시물 시리즈](https://devblogs.microsoft.com/scripting/?s=about+enumeration)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33ac4-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="33ac4-116">해시 테이블 키/값 쌍</span><span class="sxs-lookup"><span data-stu-id="33ac4-116">Hash table key/value pairs</span></span>

<span data-ttu-id="33ac4-117">효율적인 쿼리를 작성하려면 `Get-WinEvent` cmdlet과 **FilterHashtable** 매개 변수를 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="33ac4-118">**FilterHashtable**은 Windows 이벤트 로그에서 특정 정보를 가져오기 위한 필터로 해시 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="33ac4-119">해시 테이블은 **키/값** 쌍을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="33ac4-120">해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33ac4-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="33ac4-121">**키/값** 쌍이 같은 줄에 있으면 세미콜론으로 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="33ac4-122">각 **키/값** 쌍이 별도 줄에 있으면 세미콜론이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="33ac4-123">예를 들어, 이 문서에서는 **키/값** 쌍을 별도 줄에 배치하며 세미콜론을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="33ac4-124">이 샘플에서는 몇 가지 **FilterHashtable** 매개 변수의 **키/값** 쌍을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="33ac4-125">완료된 쿼리에는 **LogName**, **ProviderName**, **Keywords**, **ID** 및 **Level**이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="33ac4-126">허용되는 **키/값** 쌍은 다음 표에 표시되고, [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** 매개 변수에 대한 설명서에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="33ac4-127">다음 표는 키 이름, 데이터 형식, 데이터 값에 대해 와일드카드 문자가 허용되는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="33ac4-128">키 이름</span><span class="sxs-lookup"><span data-stu-id="33ac4-128">Key name</span></span>     | <span data-ttu-id="33ac4-129">값 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="33ac4-129">Value data type</span></span>    | <span data-ttu-id="33ac4-130">와일드카드 문자 허용 여부</span><span class="sxs-lookup"><span data-stu-id="33ac4-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="33ac4-131">LogName</span><span class="sxs-lookup"><span data-stu-id="33ac4-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="33ac4-132">예</span><span class="sxs-lookup"><span data-stu-id="33ac4-132">Yes</span></span> |
| <span data-ttu-id="33ac4-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="33ac4-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="33ac4-134">예</span><span class="sxs-lookup"><span data-stu-id="33ac4-134">Yes</span></span> |
| <span data-ttu-id="33ac4-135">경로</span><span class="sxs-lookup"><span data-stu-id="33ac4-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="33ac4-136">아니요</span><span class="sxs-lookup"><span data-stu-id="33ac4-136">No</span></span>  |
| <span data-ttu-id="33ac4-137">키워드</span><span class="sxs-lookup"><span data-stu-id="33ac4-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="33ac4-138">아니요</span><span class="sxs-lookup"><span data-stu-id="33ac4-138">No</span></span>  |
| <span data-ttu-id="33ac4-139">ID</span><span class="sxs-lookup"><span data-stu-id="33ac4-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="33ac4-140">아니요</span><span class="sxs-lookup"><span data-stu-id="33ac4-140">No</span></span>  |
| <span data-ttu-id="33ac4-141">수준</span><span class="sxs-lookup"><span data-stu-id="33ac4-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="33ac4-142">아니요</span><span class="sxs-lookup"><span data-stu-id="33ac4-142">No</span></span>  |
| <span data-ttu-id="33ac4-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="33ac4-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="33ac4-144">아니요</span><span class="sxs-lookup"><span data-stu-id="33ac4-144">No</span></span>  |
| <span data-ttu-id="33ac4-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="33ac4-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="33ac4-146">아니요</span><span class="sxs-lookup"><span data-stu-id="33ac4-146">No</span></span>  |
| <span data-ttu-id="33ac4-147">UserID</span><span class="sxs-lookup"><span data-stu-id="33ac4-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="33ac4-148">아니요</span><span class="sxs-lookup"><span data-stu-id="33ac4-148">No</span></span>  |
| <span data-ttu-id="33ac4-149">데이터</span><span class="sxs-lookup"><span data-stu-id="33ac4-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="33ac4-150">아니요</span><span class="sxs-lookup"><span data-stu-id="33ac4-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="33ac4-151">아니요</span><span class="sxs-lookup"><span data-stu-id="33ac4-151">No</span></span>  |

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="33ac4-152">해시 테이블을 사용하여 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="33ac4-152">Building a query with a hash table</span></span>

<span data-ttu-id="33ac4-153">결과를 확인하고 문제를 해결하려는 경우 **키/값** 쌍을 한 번에 하나씩 사용해서 해시 테이블을 작성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="33ac4-154">쿼리는 **애플리케이션** 로그에서 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="33ac4-155">해시 테이블은 `Get-WinEvent –LogName Application`과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="33ac4-156">시작하려면 `Get-WinEvent` 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="33ac4-157">**FilterHashtable** 매개 변수의 **키/값** 쌍(키: **LogName**, 값: **Application**)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="33ac4-158">**ProviderName** 키를 사용해서 해시 테이블을 계속 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="33ac4-159">**ProviderName**은 **Windows 이벤트 뷰어**의 **원본** 필드에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="33ac4-160">예를 들어, 다음 스크린샷에서 **.NET Runtime**입니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Windows 이벤트 뷰어 원본 이미지](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="33ac4-162">해시 테이블을 업데이트하고 **키/값** 쌍(키: \*\*ProviderName, 값: **.NET Runtime**)을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="33ac4-163">보관된 이벤트 로그에서 데이터를 가져오는 쿼리가 필요한 경우 **Path** 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="33ac4-164">**Path** 값은 로그 파일에 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="33ac4-165">자세한 내용은 **Scripting Guy** 블로그 게시물, [PowerShell을 사용하여 저장된 이벤트 로그에 오류가 있는지 구문 분석](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33ac4-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="33ac4-166">해시 테이블에서 열거된 값 사용</span><span class="sxs-lookup"><span data-stu-id="33ac4-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="33ac4-167">**Keywords**는 해시 테이블의 다음 키입니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="33ac4-168">**Keywords** 데이터 형식은 큰 숫자를 포함하는 `[long]` 값 형식의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="33ac4-169">다음 명령을 사용하여 `[long]`의 최대 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="33ac4-170">**Keywords** 키의 경우 PowerShell은 **Security**와 같은 문자열이 아니라 숫자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="33ac4-171">**Windows 이벤트 뷰어**는 **Keywords**를 문자열로 표시하지만 열거형 값입니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="33ac4-172">해시 테이블에서 문자열 값에 **Keywords** 키를 사용하면 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="33ac4-173">**Windows 이벤트 뷰어**를 열고 **작업** 창에서 **현재 로그 필터링**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="33ac4-174">**Keywords** 드롭다운 메뉴는 다음 스크린샷에 표시된 것처럼 사용할 수 있는 키워드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Windows 이벤트 뷰어 Keywords의 이미지입니다.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="33ac4-176">다음 명령을 사용하여 `StandardEventKeywords` 속성 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

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

<span data-ttu-id="33ac4-177">열거형 값은 **.NET Framework**에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="33ac4-178">자세한 내용은 [StandardEventKeywords 열거형](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33ac4-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="33ac4-179">**Keywords** 이름 및 열거형 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="33ac4-180">이름</span><span class="sxs-lookup"><span data-stu-id="33ac4-180">Name</span></span>             |  <span data-ttu-id="33ac4-181">Value</span><span class="sxs-lookup"><span data-stu-id="33ac4-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="33ac4-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="33ac4-182">AuditFailure</span></span>     | <span data-ttu-id="33ac4-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="33ac4-183">4503599627370496</span></span>  |
| <span data-ttu-id="33ac4-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="33ac4-184">AuditSuccess</span></span>     | <span data-ttu-id="33ac4-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="33ac4-185">9007199254740992</span></span>  |
| <span data-ttu-id="33ac4-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="33ac4-186">CorrelationHint2</span></span> | <span data-ttu-id="33ac4-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="33ac4-187">18014398509481984</span></span> |
| <span data-ttu-id="33ac4-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="33ac4-188">EventLogClassic</span></span>  | <span data-ttu-id="33ac4-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="33ac4-189">36028797018963968</span></span> |
| <span data-ttu-id="33ac4-190">Sqm</span><span class="sxs-lookup"><span data-stu-id="33ac4-190">Sqm</span></span>              | <span data-ttu-id="33ac4-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="33ac4-191">2251799813685248</span></span>  |
| <span data-ttu-id="33ac4-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="33ac4-192">WdiDiagnostic</span></span>    | <span data-ttu-id="33ac4-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="33ac4-193">1125899906842624</span></span>  |
| <span data-ttu-id="33ac4-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="33ac4-194">WdiContext</span></span>       | <span data-ttu-id="33ac4-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="33ac4-195">562949953421312</span></span>   |
| <span data-ttu-id="33ac4-196">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="33ac4-196">ResponseTime</span></span>     | <span data-ttu-id="33ac4-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="33ac4-197">281474976710656</span></span>   |
| <span data-ttu-id="33ac4-198">없음</span><span class="sxs-lookup"><span data-stu-id="33ac4-198">None</span></span>             | <span data-ttu-id="33ac4-199">0</span><span class="sxs-lookup"><span data-stu-id="33ac4-199">0</span></span>                 |

<span data-ttu-id="33ac4-200">해시 테이블을 업데이트하고 **키/값** 쌍(키: **Keywords** 및 **EventLogClassic** 열거형 값, **36028797018963968** )을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="33ac4-201">Keywords 정적 속성 값(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="33ac4-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="33ac4-202">**Keywords** 키는 열거형이지만 해시 테이블 쿼리에서 정적 속성 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="33ac4-203">반환된 문자열을 사용하는 대신, 속성 이름을 **Value__** 속성을 갖는 값으로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="33ac4-204">예를 들어, 다음 스크립트는 **Value__** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="33ac4-205">이벤트 ID 기준으로 필터링</span><span class="sxs-lookup"><span data-stu-id="33ac4-205">Filtering by Event Id</span></span>

<span data-ttu-id="33ac4-206">보다 구체적인 데이터를 가져오기 위해 쿼리 결과가 **이벤트 ID**를 기준으로 필터링됩니다. **이벤트 ID**는 해시 테이블에서 키 **ID**로 참조되고 해당 값은 특정 **이벤트 ID**입니다. **Windows 이벤트 뷰어**는 **이벤트 ID**를 표시합니다. 이 예제에서는 **이벤트 ID 1023**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="33ac4-207">해시 테이블을 업데이트하고 **키/값** 쌍(키: **ID**, 값: **1023**)을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="33ac4-208">수준 기준 필터링</span><span class="sxs-lookup"><span data-stu-id="33ac4-208">Filtering by Level</span></span>

<span data-ttu-id="33ac4-209">결과를 구체화하고 오류가 있는 이벤트만 포함하려면 **Level** 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="33ac4-210">**Windows 이벤트 뷰어**는 **Level**을 문자열 값으로 표시하지만, 열거형 값입니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="33ac4-211">해시 테이블에서 문자열 값에 **Level** 키를 사용하면 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="33ac4-212">**Level**에는 **Error**, **Warning** 또는 **Informational**과 같은 값이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="33ac4-213">다음 명령을 사용하여 `StandardEventLevel` 속성 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

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

<span data-ttu-id="33ac4-214">열거형 값은 **.NET Framework**에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="33ac4-215">자세한 내용은 [StandardEventLevel 열거형](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33ac4-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="33ac4-216">**Level** 키의 이름 및 열거형 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="33ac4-217">이름</span><span class="sxs-lookup"><span data-stu-id="33ac4-217">Name</span></span>           | <span data-ttu-id="33ac4-218">Value</span><span class="sxs-lookup"><span data-stu-id="33ac4-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="33ac4-219">Verbose</span><span class="sxs-lookup"><span data-stu-id="33ac4-219">Verbose</span></span>        |   <span data-ttu-id="33ac4-220">5</span><span class="sxs-lookup"><span data-stu-id="33ac4-220">5</span></span>   |
| <span data-ttu-id="33ac4-221">정보 제공</span><span class="sxs-lookup"><span data-stu-id="33ac4-221">Informational</span></span>  |   <span data-ttu-id="33ac4-222">4</span><span class="sxs-lookup"><span data-stu-id="33ac4-222">4</span></span>   |
| <span data-ttu-id="33ac4-223">경고</span><span class="sxs-lookup"><span data-stu-id="33ac4-223">Warning</span></span>        |   <span data-ttu-id="33ac4-224">3</span><span class="sxs-lookup"><span data-stu-id="33ac4-224">3</span></span>   |
| <span data-ttu-id="33ac4-225">오류</span><span class="sxs-lookup"><span data-stu-id="33ac4-225">Error</span></span>          |   <span data-ttu-id="33ac4-226">2</span><span class="sxs-lookup"><span data-stu-id="33ac4-226">2</span></span>   |
| <span data-ttu-id="33ac4-227">위험</span><span class="sxs-lookup"><span data-stu-id="33ac4-227">Critical</span></span>       |   <span data-ttu-id="33ac4-228">1</span><span class="sxs-lookup"><span data-stu-id="33ac4-228">1</span></span>   |
| <span data-ttu-id="33ac4-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="33ac4-229">LogAlways</span></span>      |   <span data-ttu-id="33ac4-230">0</span><span class="sxs-lookup"><span data-stu-id="33ac4-230">0</span></span>   |

<span data-ttu-id="33ac4-231">완료된 쿼리에 대한 해시 테이블은 키, **Level** 및 값, **2**를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="33ac4-232">열거형의 Level 정적 속성(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="33ac4-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="33ac4-233">**Level** 키는 열거형이지만 해시 테이블 쿼리에서 정적 속성 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="33ac4-234">반환된 문자열을 사용하는 대신, 속성 이름을 **Value__** 속성을 갖는 값으로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="33ac4-235">예를 들어, 다음 스크립트는 **Value__** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="33ac4-235">For example, the following script uses the **Value__** property.</span></span>

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