---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: 584e36dbb6db251906dfbf4f700ced78f1cb6830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213913"
---
# <span data-ttu-id="01ef0-103">Get-Unique</span><span class="sxs-lookup"><span data-stu-id="01ef0-103">Get-Unique</span></span>

## <span data-ttu-id="01ef0-104">개요</span><span class="sxs-lookup"><span data-stu-id="01ef0-104">SYNOPSIS</span></span>
<span data-ttu-id="01ef0-105">정렬된 목록에서 고유한 항목을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-105">Returns unique items from a sorted list.</span></span>

## <span data-ttu-id="01ef0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="01ef0-106">SYNTAX</span></span>

### <span data-ttu-id="01ef0-107">AsString (기본값)</span><span class="sxs-lookup"><span data-stu-id="01ef0-107">AsString (Default)</span></span>

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### <span data-ttu-id="01ef0-108">UniqueByType</span><span class="sxs-lookup"><span data-stu-id="01ef0-108">UniqueByType</span></span>

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## <span data-ttu-id="01ef0-109">설명</span><span class="sxs-lookup"><span data-stu-id="01ef0-109">DESCRIPTION</span></span>

<span data-ttu-id="01ef0-110">`Get-Unique`이 cmdlet은 정렬 된 목록의 각 항목을 다음 항목과 비교 하 고, 중복을 제거 하 고, 각 항목의 인스턴스를 하나만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-110">The `Get-Unique` cmdlet compares each item in a sorted list to the next item, eliminates duplicates, and returns only one instance of each item.</span></span> <span data-ttu-id="01ef0-111">cmdlet이 제대로 작동하려면 목록을 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-111">The list must be sorted for the cmdlet to work properly.</span></span>

<span data-ttu-id="01ef0-112">`Get-Unique`은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-112">`Get-Unique` is case-sensitive.</span></span> <span data-ttu-id="01ef0-113">따라서 문자의 대/소문자만 다른 문자열은 고유한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-113">As a result, strings that differ only in character casing are considered to be unique.</span></span>

## <span data-ttu-id="01ef0-114">예제</span><span class="sxs-lookup"><span data-stu-id="01ef0-114">EXAMPLES</span></span>

### <span data-ttu-id="01ef0-115">예제 1: 텍스트 파일에서 고유한 단어 가져오기</span><span class="sxs-lookup"><span data-stu-id="01ef0-115">Example 1: Get unique words in a text file</span></span>

<span data-ttu-id="01ef0-116">이러한 명령은 텍스트 파일에서 고유한 단어 수를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-116">These commands find the number of unique words in a text file.</span></span>

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

<span data-ttu-id="01ef0-117">첫 번째 명령은 File.txt 파일의 내용을 가져오고,</span><span class="sxs-lookup"><span data-stu-id="01ef0-117">The first command gets the content of the File.txt file.</span></span> <span data-ttu-id="01ef0-118">각 텍스트 줄을 소문자로 변경한 다음 공백(" ")에서 별도의 줄로 각 단어를 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-118">It converts each line of text to lowercase letters and then splits each word onto a separate line at the space (" ").</span></span> <span data-ttu-id="01ef0-119">그런 다음 결과 목록을 사전순 (기본값)으로 정렬 하 고 cmdlet을 사용 하 여 `Get-Unique` 중복 된 단어를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-119">Then, it sorts the resulting list alphabetically (the default) and uses the `Get-Unique` cmdlet to eliminate any duplicate words.</span></span> <span data-ttu-id="01ef0-120">결과는 변수에 저장 됩니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="01ef0-120">The results are stored in the `$A` variable.</span></span>

<span data-ttu-id="01ef0-121">두 번째 명령은에서 문자열 컬렉션의 **Count** 속성을 사용 하 여 `$A` 에 있는 항목 수를 확인 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="01ef0-121">The second command uses the **Count** property of the collection of strings in `$A` to determine how many items are in `$A`.</span></span>

### <span data-ttu-id="01ef0-122">예제 2: 배열에서 고유한 정수 가져오기</span><span class="sxs-lookup"><span data-stu-id="01ef0-122">Example 2: Get unique integers in an array</span></span>

<span data-ttu-id="01ef0-123">이 명령은 정수 집합의 고유한 멤버를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-123">This command finds the unique members of the set of integers.</span></span>

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

<span data-ttu-id="01ef0-124">첫 번째 명령은 명령줄에서 입력 한 정수 배열을 가져와이를 cmdlet으로 파이프 하 여 `Sort-Object` 정렬 한 다음이를 파이프 하 여 중복 된 항목을 제거 합니다 `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="01ef0-124">The first command takes an array of integers typed at the command line, pipes them to the `Sort-Object` cmdlet to be sorted, and then pipes them to `Get-Unique`, which eliminates duplicate entries.</span></span>

### <span data-ttu-id="01ef0-125">예제 3: 디렉터리에서 고유 개체 형식 가져오기</span><span class="sxs-lookup"><span data-stu-id="01ef0-125">Example 3: Get unique object types in a directory</span></span>

<span data-ttu-id="01ef0-126">이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` 파일 및 디렉터리를 포함 하는 로컬 디렉터리의 콘텐츠를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-126">This command uses the `Get-ChildItem` cmdlet to retrieve the contents of the local directory, which includes files and directories.</span></span>

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

<span data-ttu-id="01ef0-127">파이프라인 연산자 (|)가 결과를 cmdlet으로 보냅니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="01ef0-127">The pipeline operator (|) sends the results to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="01ef0-128">`$_.GetType()`문은 **GetType** 메서드를 각 파일 또는 디렉터리에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-128">The `$_.GetType()` statement applies the **GetType** method to each file or directory.</span></span> <span data-ttu-id="01ef0-129">그런 다음 `Sort-Object` 유형별로 항목을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-129">Then, `Sort-Object` sorts the items by type.</span></span> <span data-ttu-id="01ef0-130">다른 파이프라인 연산자는 결과를로 보냅니다 `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="01ef0-130">Another pipeline operator sends the results to `Get-Unique`.</span></span> <span data-ttu-id="01ef0-131">**Ontype** 매개 변수는 `Get-Unique` 각 형식의 하나의 개체만 반환 하도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-131">The **OnType** parameter directs `Get-Unique` to return only one object of each type.</span></span>

### <span data-ttu-id="01ef0-132">예제 4: 고유한 프로세스 가져오기</span><span class="sxs-lookup"><span data-stu-id="01ef0-132">Example 4: Get unique processes</span></span>

<span data-ttu-id="01ef0-133">이 명령은 컴퓨터에서 실행되는 프로세스의 이름을 중복 항목을 제거하고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-133">This command gets the names of processes running on the computer with duplicates eliminated.</span></span>

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

<span data-ttu-id="01ef0-134">`Get-Process`명령은 컴퓨터의 모든 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-134">The `Get-Process` command gets all of the processes on the computer.</span></span> <span data-ttu-id="01ef0-135">파이프라인 연산자 (|)는 결과를에 전달 합니다 `Sort-Object` .이는 기본적으로 ProcessName에 의해 사전순으로 프로세스를 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-135">The pipeline operator (|) passes the result to `Sort-Object`, which, by default, sorts the processes alphabetically by ProcessName.</span></span> <span data-ttu-id="01ef0-136">결과는 cmdlet에 파이프 되어 `Select-Object` 각 개체의 ProcessName 속성 값만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-136">The results are piped to the `Select-Object` cmdlet, which selects only the values of the ProcessName property of each object.</span></span> <span data-ttu-id="01ef0-137">그런 다음 결과를로 파이프 하 여 `Get-Unique` 중복 항목을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-137">The results are then piped to `Get-Unique` to eliminate duplicates.</span></span>

<span data-ttu-id="01ef0-138">**Asstring** 매개 변수는 `Get-Unique` **ProcessName** 값을 문자열로 처리 하도록에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-138">The **AsString** parameter tells `Get-Unique` to treat the **ProcessName** values as strings.</span></span>
<span data-ttu-id="01ef0-139">이 매개 변수를 사용 하지 않으면는 `Get-Unique` **ProcessName** 값을 개체로 처리 하 고 개체의 인스턴스 하나 즉, 목록의 첫 번째 프로세스 이름만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-139">Without this parameter, `Get-Unique` treats the **ProcessName** values as objects and returns only one instance of the object, that is, the first process name in the list.</span></span>

## <span data-ttu-id="01ef0-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="01ef0-140">PARAMETERS</span></span>

### <span data-ttu-id="01ef0-141">-AsString</span><span class="sxs-lookup"><span data-stu-id="01ef0-141">-AsString</span></span>

<span data-ttu-id="01ef0-142">이 cmdlet이 데이터를 문자열로 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-142">Indicates that this cmdlet uses the data as a string.</span></span> <span data-ttu-id="01ef0-143">이 매개 변수를 사용 하지 않으면 데이터는 개체로 처리 되므로 동일한 형식의 개체 컬렉션을 파일 컬렉션과 같은에 제출할 때에는 `Get-Unique` 하나 (첫 번째)만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-143">Without this parameter, data is treated as an object, so when you submit a collection of objects of the same type to `Get-Unique`, such as a collection of files, it returns just one (the first).</span></span> <span data-ttu-id="01ef0-144">이 매개 변수를 사용하여 파일 이름과 같은 개체 속성의 고유한 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-144">You can use this parameter to find the unique values of object properties, such as the file names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01ef0-145">-InputObject</span><span class="sxs-lookup"><span data-stu-id="01ef0-145">-InputObject</span></span>

<span data-ttu-id="01ef0-146">에 대 한 입력을 지정 합니다 `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="01ef0-146">Specifies input for `Get-Unique`.</span></span> <span data-ttu-id="01ef0-147">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="01ef0-147">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="01ef0-148">이 cmdlet은 **InputObject** 를 사용 하 여 제출한 입력을 컬렉션으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-148">This cmdlet treats the input submitted by using **InputObject** as a collection.</span></span> <span data-ttu-id="01ef0-149">컬렉션의 개별 항목을 열거 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-149">it does not enumerate individual items in the collection.</span></span> <span data-ttu-id="01ef0-150">컬렉션은 단일 항목 이므로 **InputObject** 를 사용 하 여 제출한 입력은 항상 변경 되지 않은 상태로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-150">Because the collection is a single item, input submitted by using **InputObject** is always returned unchanged.</span></span>

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

### <span data-ttu-id="01ef0-151">-OnType</span><span class="sxs-lookup"><span data-stu-id="01ef0-151">-OnType</span></span>

<span data-ttu-id="01ef0-152">이 cmdlet은 각 형식의 하나의 개체만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-152">Indicates that this cmdlet returns only one object of each type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01ef0-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01ef0-153">CommonParameters</span></span>

<span data-ttu-id="01ef0-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="01ef0-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01ef0-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01ef0-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01ef0-156">입력</span><span class="sxs-lookup"><span data-stu-id="01ef0-156">INPUTS</span></span>

### <span data-ttu-id="01ef0-157">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="01ef0-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="01ef0-158">모든 형식의 개체를로 파이프 할 수 있습니다 `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="01ef0-158">You can pipe any type of object to `Get-Unique`.</span></span>

## <span data-ttu-id="01ef0-159">출력</span><span class="sxs-lookup"><span data-stu-id="01ef0-159">OUTPUTS</span></span>

### <span data-ttu-id="01ef0-160">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="01ef0-160">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="01ef0-161">가 반환 하는 개체의 형식은 `Get-Unique` 입력에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-161">The type of object that `Get-Unique` returns is determined by the input.</span></span>

## <span data-ttu-id="01ef0-162">참고</span><span class="sxs-lookup"><span data-stu-id="01ef0-162">NOTES</span></span>

<span data-ttu-id="01ef0-163">의 기본 제공 별칭인를 참조할 수도 있습니다 `Get-Unique` `gu` .</span><span class="sxs-lookup"><span data-stu-id="01ef0-163">You can also refer to `Get-Unique` by its built-in alias, `gu`.</span></span> <span data-ttu-id="01ef0-164">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="01ef0-164">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="01ef0-165">목록을 정렬하려면 Sort-Object를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-165">To sort a list, use Sort-Object.</span></span> <span data-ttu-id="01ef0-166">의 **unique** 매개 변수를 사용 하 여 `Sort-Object` 목록에서 고유한 항목을 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01ef0-166">You can also use the **Unique** parameter of `Sort-Object` to find the unique items in a list.</span></span>

## <span data-ttu-id="01ef0-167">관련 링크</span><span class="sxs-lookup"><span data-stu-id="01ef0-167">RELATED LINKS</span></span>

[<span data-ttu-id="01ef0-168">Select-Object</span><span class="sxs-lookup"><span data-stu-id="01ef0-168">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="01ef0-169">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="01ef0-169">Sort-Object</span></span>](Sort-Object.md)
