---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: 6198964f01a4c0dc70584cdb3e5c0e13f3965934
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599579"
---
# <span data-ttu-id="e55ce-102">Group-Object</span><span class="sxs-lookup"><span data-stu-id="e55ce-102">Group-Object</span></span>

## <span data-ttu-id="e55ce-103">개요</span><span class="sxs-lookup"><span data-stu-id="e55ce-103">SYNOPSIS</span></span>
<span data-ttu-id="e55ce-104">지정한 속성에 대해 같은 값이 있는 개체를 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-104">Groups objects that contain the same value for specified properties.</span></span>

## <span data-ttu-id="e55ce-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e55ce-105">SYNTAX</span></span>

### <span data-ttu-id="e55ce-106">테이블</span><span class="sxs-lookup"><span data-stu-id="e55ce-106">HashTable</span></span>

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="e55ce-107">설명</span><span class="sxs-lookup"><span data-stu-id="e55ce-107">DESCRIPTION</span></span>

<span data-ttu-id="e55ce-108">`Group-Object`Cmdlet은 지정 된 속성의 값을 기준으로 개체를 그룹으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-108">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span>
<span data-ttu-id="e55ce-109">`Group-Object` 각 속성 값에 대해 하나의 행이 있는 테이블을 반환 하 고 해당 값을 가진 항목 수를 표시 하는 열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-109">`Group-Object` returns a table with one row for each property value and a column that displays the number of items with that value.</span></span>

<span data-ttu-id="e55ce-110">둘 이상의 속성을 지정 하는 경우 먼저 `Group-Object` 첫 번째 속성의 값을 기준으로 그룹화 한 다음 각 속성 그룹 내에서 다음 속성의 값을 기준으로 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-110">If you specify more than one property, `Group-Object` first groups them by the values of the first property, and then, within each property group, it groups by the value of the next property.</span></span>

<span data-ttu-id="e55ce-111">PowerShell 7부터는 `Group-Object` **CaseSensitive** 및 **ashashtable** 매개 변수를 결합 하 여 대/소문자를 구분 하는 해시 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-111">Beginning in PowerShell 7, `Group-Object` can combine the **CaseSensitive** and **AsHashtable** parameters to create a case-sensitive hash table.</span></span> <span data-ttu-id="e55ce-112">해시 테이블 키는 대/소문자를 구분 하는 비교를 사용 하 고 **system.object** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-112">The hash table keys use case-sensitive comparisons and output a **System.Collections.Hashtable** object.</span></span>

## <span data-ttu-id="e55ce-113">예제</span><span class="sxs-lookup"><span data-stu-id="e55ce-113">EXAMPLES</span></span>

### <span data-ttu-id="e55ce-114">예제 1: 확장명으로 파일 그룹화</span><span class="sxs-lookup"><span data-stu-id="e55ce-114">Example 1: Group files by extension</span></span>

<span data-ttu-id="e55ce-115">이 예제에서는 파일을 재귀적으로 가져와 `$PSHOME` 파일 이름 확장명 별로 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-115">This example recursively gets the files under `$PSHOME` and groups them by file name extension.</span></span> <span data-ttu-id="e55ce-116">출력은 cmdlet으로 전송 됩니다 `Sort-Object` .이 cmdlet은 지정 된 확장에 대해 발견 된 카운트 파일을 기준으로 출력을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-116">The output is sent to the `Sort-Object` cmdlet, which sorts them by the count files found for the given extension.</span></span> <span data-ttu-id="e55ce-117">빈 **이름은** 디렉터리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-117">The empty **Name** represents directories.</span></span>

<span data-ttu-id="e55ce-118">이 예제에서는 **Noelement** 매개 변수를 사용 하 여 그룹의 멤버를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-118">This example uses the **NoElement** parameter to omit the members of the group.</span></span>

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### <span data-ttu-id="e55ce-119">예제 2: 영향을 받은 것과 같은 방식으로 정수 그룹화</span><span class="sxs-lookup"><span data-stu-id="e55ce-119">Example 2: Group integers by odds and evens</span></span>

<span data-ttu-id="e55ce-120">이 예제에서는 스크립트 블록을 **Property** 매개 변수의 값으로 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-120">This example shows how to use script blocks as the value of the **Property** parameter.</span></span> <span data-ttu-id="e55ce-121">이 명령은 1에서 20 사이의 정수를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-121">This command displays the integers from 1 to 20, grouped by odds and even.</span></span>

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### <span data-ttu-id="e55ce-122">예 3: Entrytype 관련이에서 이벤트 로그 이벤트 그룹화</span><span class="sxs-lookup"><span data-stu-id="e55ce-122">Example 3: Group event log events by EntryType</span></span>

<span data-ttu-id="e55ce-123">이 예에서는 시스템 이벤트 로그에 **entrytype 관련이** 별로 그룹화 된 가장 최근의 1000 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-123">This example displays the 1,000 most recent entries in the System event log, grouped by **EntryType**.</span></span>

<span data-ttu-id="e55ce-124">출력에서 **Count** 열은 각 그룹의 항목 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-124">In the output, the **Count** column represents the number of entries in each group.</span></span> <span data-ttu-id="e55ce-125">**이름** 열은 그룹을 정의 하는 **EventType** 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-125">The **Name** column represents the **EventType** values that define a group.</span></span> <span data-ttu-id="e55ce-126">**그룹** 열은 각 그룹의 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-126">The **Group** column represents the objects in each group.</span></span>

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### <span data-ttu-id="e55ce-127">예제 4: 우선 순위 클래스 별로 프로세스 그룹화</span><span class="sxs-lookup"><span data-stu-id="e55ce-127">Example 4: Group processes by priority class</span></span>

<span data-ttu-id="e55ce-128">이 예제에서는 **Noelement** 매개 변수의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-128">This example demonstrates the effect of the **NoElement** parameter.</span></span> <span data-ttu-id="e55ce-129">이 명령은 우선 순위 클래스를 기준으로 컴퓨터의 프로세스를 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-129">These commands group the processes on the computer by priority class.</span></span>

<span data-ttu-id="e55ce-130">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 컴퓨터의 프로세스를 가져온 후 해당 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-130">The first command uses the `Get-Process` cmdlet to get the processes on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="e55ce-131">`Group-Object`프로세스의 **PriorityClass** 속성 값을 기준으로 개체를 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-131">`Group-Object`groups the objects by the value of the **PriorityClass** property of the process.</span></span>

<span data-ttu-id="e55ce-132">두 번째 예제에서는 **Noelement** 매개 변수를 사용 하 여 출력에서 그룹의 멤버를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-132">The second example uses the **NoElement** parameter to eliminate the members of the group from the output.</span></span> <span data-ttu-id="e55ce-133">결과는 **Count** 및 **Name** 속성 값만 있는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-133">The result is a table with only the **Count** and **Name** property value.</span></span>

<span data-ttu-id="e55ce-134">결과는 다음과 같은 샘플 출력에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-134">The results are shown in the following sample output.</span></span>

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### <span data-ttu-id="e55ce-135">예 5: 이름별로 프로세스 그룹화</span><span class="sxs-lookup"><span data-stu-id="e55ce-135">Example 5: Group processes by name</span></span>

<span data-ttu-id="e55ce-136">다음 예에서는 `Group-Object` 를 사용 하 여 로컬 컴퓨터에서 실행 중인 프로세스의 여러 인스턴스를 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-136">The following example uses `Group-Object` to group multiple instances of processes running on the local computer.</span></span> <span data-ttu-id="e55ce-137">`Where-Object` 둘 이상의 인스턴스가 있는 프로세스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-137">`Where-Object` displays processes with more than one instance.</span></span>

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### <span data-ttu-id="e55ce-138">예 6: 해시 테이블의 개체 그룹화</span><span class="sxs-lookup"><span data-stu-id="e55ce-138">Example 6: Group objects in a hash table</span></span>

<span data-ttu-id="e55ce-139">이 예에서는 **ashashtable** 및 **asstring** 매개 변수를 사용 하 여 해시 테이블의 그룹을 키-값 쌍의 컬렉션으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-139">This example uses the **AsHashTable** and **AsString** parameters to return the groups in a hash table, as a collection of key-value pairs.</span></span>

<span data-ttu-id="e55ce-140">그 결과로 생성되는 해시 테이블에서 각 속성 값은 키이고 그룹 요소는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-140">In the resulting hash table, each property value is a key, and the group elements are the values.</span></span>
<span data-ttu-id="e55ce-141">각 키는 해시 테이블 개체의 속성이므로 점 표기법으로 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-141">Because each key is a property of the hash table object, you can use dot notation to display the values.</span></span>

<span data-ttu-id="e55ce-142">첫 번째 명령은 `Get` 세션에서 및 cmdlet을 가져오고, 동사로 그룹화 하 `Set` 고, 그룹을 해시 테이블로 반환 하 고, 해시 테이블을 변수에 저장 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="e55ce-142">The first command gets the `Get` and `Set` cmdlets in the session, groups them by verb, returns the groups as a hash table, and saves the hash table in the `$A` variable.</span></span>

<span data-ttu-id="e55ce-143">두 번째 명령은의 해시 테이블을 표시 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="e55ce-143">The second command displays the hash table in `$A`.</span></span> <span data-ttu-id="e55ce-144">`Get`Cmdlet 및 cmdlet에 대해 하나씩 두 개의 키-값 쌍이 있습니다 `Set` .</span><span class="sxs-lookup"><span data-stu-id="e55ce-144">There are two key-value pairs, one for the `Get` cmdlets and one for the `Set` cmdlets.</span></span>

<span data-ttu-id="e55ce-145">세 번째 명령은 점 표기법을 사용 하 여 `$A.Get` 의 **Get** 키 값을 표시 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="e55ce-145">The third command uses dot notation, `$A.Get` to display the values of the **Get** key in `$A`.</span></span> <span data-ttu-id="e55ce-146">값은 **Cmdletinfo** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-146">The values are **CmdletInfo** object.</span></span> <span data-ttu-id="e55ce-147">**Asstring** 매개 변수는 그룹의 개체를 문자열로 변환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-147">The **AsString** parameter doesn't convert the objects in the groups to strings.</span></span>

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                                Version    Source
-----------     ----                                -------    ------
Cmdlet          Get-Acl                             7.0.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                           7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AppLockerFileInformation        2.0.0.0    AppLocker
Cmdlet          Get-AppLockerPolicy                 2.0.0.0    AppLocker
...
```

### <span data-ttu-id="e55ce-148">예 7: 대/소문자를 구분 하는 해시 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="e55ce-148">Example 7: Create a case-sensitive hash table</span></span>

<span data-ttu-id="e55ce-149">이 예에서는 **CaseSensitive** 와 **ashashtable** 매개 변수를 결합 하 여 대/소문자를 구분 하는 해시 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-149">This example combines the **CaseSensitive** and **AsHashTable** parameters to create a case-sensitive hash table.</span></span> <span data-ttu-id="e55ce-150">예제의 파일에는 및의 확장이 있습니다 `.txt` `.TXT` .</span><span class="sxs-lookup"><span data-stu-id="e55ce-150">The files in the example have extensions of `.txt` and `.TXT`.</span></span>

```powershell
$hash = Get-ChildItem -Path C:\Files | Group-Object -Property Extension -CaseSensitive -AsHashTable
$hash
```

```Output
Name           Value
----           -----
.TXT           {C:\Files\File7.TXT, C:\Files\File8.TXT, C:\Files\File9.TXT}
.txt           {C:\Files\file1.txt, C:\Files\file2.txt, C:\Files\file3.txt}
```

<span data-ttu-id="e55ce-151">`$hash`변수는 **system.object** 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-151">The `$hash` variable stores the **System.Collections.Hashtable** object.</span></span> <span data-ttu-id="e55ce-152">`Get-ChildItem` 디렉터리에서 파일 이름을 가져오고 `C:\Files` , 파이프라인에서 **시스템** 의 파일 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-152">`Get-ChildItem` gets the file names from the `C:\Files` directory and sends the **System.IO.FileInfo** objects down the pipeline.</span></span> <span data-ttu-id="e55ce-153">`Group-Object`**속성** 값 **확장** 을 사용 하 여 개체를 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-153">`Group-Object` groups the objects using the **Property** value **Extension**.</span></span> <span data-ttu-id="e55ce-154">**CaseSensitive** 및 **ashashtable** 매개 변수는 해시 테이블을 만들고 키는 대/소문자를 구분 하는 키와를 사용 하 여 그룹화 됩니다 `.txt` `.TXT` .</span><span class="sxs-lookup"><span data-stu-id="e55ce-154">The **CaseSensitive** and **AsHashTable** parameters create the hash table and the keys are grouped using the case-sensitive keys `.txt` and `.TXT`.</span></span>

## <span data-ttu-id="e55ce-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e55ce-155">PARAMETERS</span></span>

### <span data-ttu-id="e55ce-156">-AsHashTable</span><span class="sxs-lookup"><span data-stu-id="e55ce-156">-AsHashTable</span></span>

<span data-ttu-id="e55ce-157">이 cmdlet이 그룹을 해시 테이블로 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-157">Indicates that this cmdlet returns the group as a hash table.</span></span> <span data-ttu-id="e55ce-158">해시 테이블의 키는 개체를 그룹화하는 기준인 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-158">The keys of the hash table are the property values by which the objects are grouped.</span></span> <span data-ttu-id="e55ce-159">해시 테이블의 값은 속성 값을 포함하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-159">The values of the hash table are the objects that have that property value.</span></span>

<span data-ttu-id="e55ce-160">기본적으로 **ashashtable** 매개 변수는 각 키가 그룹화 된 개체의 인스턴스인 각 해시 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-160">By itself, the **AsHashTable** parameter returns each hash table in which each key is an instance of the grouped object.</span></span> <span data-ttu-id="e55ce-161">**Asstring** 매개 변수와 함께 사용 하는 경우 해시 테이블의 키는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-161">When used with the **AsString** parameter, the keys in the hash table are strings.</span></span>

<span data-ttu-id="e55ce-162">PowerShell 7부터 대/소문자를 구분 하는 해시 테이블을 만들려면 명령에 **CaseSensitive** 및 **ashashtable** 을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-162">Beginning in PowerShell 7, to create case-sensitive hash tables, include **CaseSensitive** and **AsHashtable** in your command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e55ce-163">-AsString</span><span class="sxs-lookup"><span data-stu-id="e55ce-163">-AsString</span></span>

<span data-ttu-id="e55ce-164">이 cmdlet이 해시 테이블 키를 문자열로 변환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-164">Indicates that this cmdlet converts the hash table keys to strings.</span></span> <span data-ttu-id="e55ce-165">기본적으로 해시 테이블 키는 그룹화된 개체의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-165">By default, the hash table keys are instances of the grouped object.</span></span> <span data-ttu-id="e55ce-166">이 매개 변수는 **Ashashtable** 매개 변수와 함께 사용 하는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-166">This parameter is valid only when used with the **AsHashTable** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e55ce-167">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="e55ce-167">-CaseSensitive</span></span>

<span data-ttu-id="e55ce-168">이 cmdlet을 통해 대/소문자를 구분 하 여 그룹화 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-168">Indicates that this cmdlet makes the grouping case-sensitive.</span></span> <span data-ttu-id="e55ce-169">이 매개 변수를 사용하지 않으면 그룹에 포함된 개체 속성 값의 대/소문자가 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-169">Without this parameter, the property values of objects in a group might have different cases.</span></span>

<span data-ttu-id="e55ce-170">PowerShell 7부터 대/소문자를 구분 하는 해시 테이블을 만들려면 명령에 **CaseSensitive** 및 **ashashtable** 을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-170">Beginning in PowerShell 7, to create case-sensitive hash tables, include **CaseSensitive** and **AsHashtable** in your command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e55ce-171">-문화권</span><span class="sxs-lookup"><span data-stu-id="e55ce-171">-Culture</span></span>

<span data-ttu-id="e55ce-172">문자열을 비교할 때 사용할 문화권을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-172">Specifies the culture to use when comparing strings.</span></span>

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

### <span data-ttu-id="e55ce-173">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e55ce-173">-InputObject</span></span>

<span data-ttu-id="e55ce-174">그룹화할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-174">Specifies the objects to group.</span></span> <span data-ttu-id="e55ce-175">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="e55ce-175">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="e55ce-176">**InputObject** 매개 변수를 사용 하 여 개체의 컬렉션을에 제출 하면는 `Group-Object` 컬렉션을 `Group-Object` 나타내는 개체 하나를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-176">When you use the **InputObject** parameter to submit a collection of objects to `Group-Object`, `Group-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="e55ce-177">따라서 해당 개체가 포함된 단일 그룹을 멤버로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-177">As a result, it creates a single group with that object as its member.</span></span>

<span data-ttu-id="e55ce-178">컬렉션에 있는 개체를 그룹화 하려면 개체를로 파이프 `Group-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-178">To group the objects in a collection, pipe the objects to `Group-Object`.</span></span>

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

### <span data-ttu-id="e55ce-179">-NoElement</span><span class="sxs-lookup"><span data-stu-id="e55ce-179">-NoElement</span></span>

<span data-ttu-id="e55ce-180">이 cmdlet이 결과에서 그룹의 멤버를 생략 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-180">Indicates that this cmdlet omits the members of a group from the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e55ce-181">-속성</span><span class="sxs-lookup"><span data-stu-id="e55ce-181">-Property</span></span>

<span data-ttu-id="e55ce-182">그룹화할 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-182">Specifies the properties for grouping.</span></span> <span data-ttu-id="e55ce-183">개체는 지정된 속성의 값을 기반으로 하여 그룹으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-183">The objects are arranged into groups based on the value of the specified property.</span></span>

<span data-ttu-id="e55ce-184">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-184">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="e55ce-185">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-185">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="e55ce-186">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-186">Valid key-value pairs are:</span></span>

- <span data-ttu-id="e55ce-187">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="e55ce-187">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="e55ce-188">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e55ce-188">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e55ce-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e55ce-189">CommonParameters</span></span>

<span data-ttu-id="e55ce-190">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e55ce-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e55ce-191">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e55ce-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e55ce-192">입력</span><span class="sxs-lookup"><span data-stu-id="e55ce-192">INPUTS</span></span>

### <span data-ttu-id="e55ce-193">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="e55ce-193">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e55ce-194">모든 개체를로 파이프 할 수 있습니다 `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="e55ce-194">You can pipe any object to `Group-Object`.</span></span>

## <span data-ttu-id="e55ce-195">출력</span><span class="sxs-lookup"><span data-stu-id="e55ce-195">OUTPUTS</span></span>

### <span data-ttu-id="e55ce-196">GroupInfo 또는 System.object. 해시 테이블</span><span class="sxs-lookup"><span data-stu-id="e55ce-196">Microsoft.PowerShell.Commands.GroupInfo or System.Collections.Hashtable</span></span>

<span data-ttu-id="e55ce-197">**Ashashtable** 매개 변수를 사용 하는 경우는 `Group-Object` **Hashtable** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-197">When you use the **AsHashTable** parameter, `Group-Object` returns a **Hashtable** object.</span></span>
<span data-ttu-id="e55ce-198">그렇지 않으면 **GroupInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-198">Otherwise, it returns a **GroupInfo** object.</span></span>

## <span data-ttu-id="e55ce-199">참고</span><span class="sxs-lookup"><span data-stu-id="e55ce-199">NOTES</span></span>

<span data-ttu-id="e55ce-200">서식 지정 cmdlet의 **GroupBy** 매개 변수 (예: 및)를 `Format-Table` 사용 `Format-List` 하 여 개체를 그룹화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-200">You can use the **GroupBy** parameter of the formatting cmdlets, such as `Format-Table` and `Format-List`, to group objects.</span></span> <span data-ttu-id="e55ce-201">`Group-Object`각 속성 값에 대 한 행이 포함 된 단일 테이블을 만드는와는 달리, **GroupBy** 매개 변수는 속성 값이 있는 각 항목에 대 한 행이 포함 된 각 속성 값에 대 한 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-201">Unlike `Group-Object`, which creates a single table with a row for each property value, the **GroupBy** parameters create a table for each property value with a row for each item that has the property value.</span></span>

<span data-ttu-id="e55ce-202">`Group-Object` 그룹화 중인 개체가 동일한 Microsoft .NET 코어 유형인 경우를 필요로 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-202">`Group-Object` doesn't require that the objects being grouped are of the same Microsoft .NET Core type.</span></span> <span data-ttu-id="e55ce-203">다른 .NET Core 형식의 개체를 그룹화 하는 경우는 `Group-Object` 다음 규칙을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-203">When grouping objects of different .NET Core types, `Group-Object` uses the following rules:</span></span>

- <span data-ttu-id="e55ce-204">동일한 속성 이름 및 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-204">Same Property Names and Types.</span></span>

  <span data-ttu-id="e55ce-205">개체에 지정 된 이름을 가진 속성이 있고 속성 값이 동일한 .NET Core 유형인 경우 속성 값은 동일한 유형의 개체에 사용 되는 것과 동일한 규칙을 사용 하 여 그룹화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-205">If the objects have a property with the specified name, and the property values have the same .NET Core type, the property values are grouped by using the same rules that would be used for objects of the same type.</span></span>

- <span data-ttu-id="e55ce-206">동일한 속성 이름, 다른 형식</span><span class="sxs-lookup"><span data-stu-id="e55ce-206">Same Property Names, Different Types.</span></span>

  <span data-ttu-id="e55ce-207">개체에 지정 된 이름의 속성이 있지만 속성 값에 다른 개체의 .NET Core 형식이 있는 경우 `Group-Object` 는 처음 발견 되는 속성의 .Net core 형식을 해당 속성 그룹의 .Net core 형식으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-207">If the objects have a property with the specified name, but the property values have a different .NET Core type in different objects, `Group-Object` uses the .NET Core type of the first occurrence of the property as the .NET Core type for that property group.</span></span> <span data-ttu-id="e55ce-208">개체에 유형이 다른 속성이 있으면 속성 값은 해당 그룹의 유형으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-208">When an object has a property with a different type, the property value is converted to the type for that group.</span></span> <span data-ttu-id="e55ce-209">형식 변환에 실패 하면 개체가 그룹에 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-209">If the type conversion fails, the object isn't included in the group.</span></span>

- <span data-ttu-id="e55ce-210">속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-210">Missing Properties.</span></span>

  <span data-ttu-id="e55ce-211">지정 된 속성이 없는 개체는 그룹화 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-211">Objects that don't have a specified property can't be grouped.</span></span> <span data-ttu-id="e55ce-212">그룹화 되지 않은 개체는 라는 그룹의 최종 **GroupInfo** 개체 출력에 표시 `AutomationNull.Value` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e55ce-212">Objects that aren't grouped appear in the final **GroupInfo** object output in a group named `AutomationNull.Value`.</span></span>

## <span data-ttu-id="e55ce-213">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e55ce-213">RELATED LINKS</span></span>

[<span data-ttu-id="e55ce-214">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="e55ce-214">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="e55ce-215">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="e55ce-215">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="e55ce-216">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="e55ce-216">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="e55ce-217">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="e55ce-217">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="e55ce-218">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="e55ce-218">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="e55ce-219">New-Object</span><span class="sxs-lookup"><span data-stu-id="e55ce-219">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="e55ce-220">Select-Object</span><span class="sxs-lookup"><span data-stu-id="e55ce-220">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="e55ce-221">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="e55ce-221">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="e55ce-222">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="e55ce-222">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="e55ce-223">Where-Object</span><span class="sxs-lookup"><span data-stu-id="e55ce-223">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
