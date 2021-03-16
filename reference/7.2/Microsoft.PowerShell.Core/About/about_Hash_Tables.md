---
description: PowerShell에서 해시 테이블을 만들고 사용 하 고 정렬 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: dec2683acfa4fcf79419beea9e0840387d3d43d1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600418"
---
# <a name="about-hash-tables"></a><span data-ttu-id="c2a5c-103">해시 테이블 정보</span><span class="sxs-lookup"><span data-stu-id="c2a5c-103">About Hash Tables</span></span>

## <a name="short-description"></a><span data-ttu-id="c2a5c-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c2a5c-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="c2a5c-105">PowerShell에서 해시 테이블을 만들고 사용 하 고 정렬 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-105">Describes how to create, use, and sort hash tables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="c2a5c-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="c2a5c-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="c2a5c-107">사전 또는 결합형 배열이 라고도 하는 해시 테이블은 하나 이상의 키/값 쌍을 저장 하는 간단한 데이터 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-107">A hash table, also known as a dictionary or associative array, is a compact data structure that stores one or more key/value pairs.</span></span> <span data-ttu-id="c2a5c-108">예를 들어 해시 테이블에는 일련의 IP 주소와 컴퓨터 이름이 포함 될 수 있습니다. 여기서 IP 주소는 키 이며 컴퓨터 이름은 값 이거나 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-108">For example, a hash table might contain a series of IP addresses and computer names, where the IP addresses are the keys and the computer names are the values, or vice versa.</span></span>

<span data-ttu-id="c2a5c-109">PowerShell에서 각 해시 테이블은 해시 테이블 (System.object) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-109">In PowerShell, each hash table is a Hashtable (System.Collections.Hashtable) object.</span></span> <span data-ttu-id="c2a5c-110">PowerShell에서 해시 테이블 개체의 속성 및 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-110">You can use the properties and methods of Hashtable objects in PowerShell.</span></span>

<span data-ttu-id="c2a5c-111">PowerShell 3.0부터 [정렬 된] 특성을 사용 하 여 PowerShell에서 순서가 지정 된 사전 (OrderedDictionary)을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-111">Beginning in PowerShell 3.0, you can use the [ordered] attribute to create an ordered dictionary (System.Collections.Specialized.OrderedDictionary) in PowerShell.</span></span>

<span data-ttu-id="c2a5c-112">순서가 지정 된 사전은 키가 나열 된 순서 대로 항상 표시 된다는 점에서 해시 테이블과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-112">Ordered dictionaries differ from hash tables in that the keys always appear in the order in which you list them.</span></span> <span data-ttu-id="c2a5c-113">해시 테이블의 키 순서는 결정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-113">The order of keys in a hash table is not determined.</span></span>

<span data-ttu-id="c2a5c-114">해시 테이블의 키와 값은 .NET 개체 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-114">The keys and value in hash tables are also .NET objects.</span></span> <span data-ttu-id="c2a5c-115">가장 일반적으로 문자열이 나 정수 이지만 모든 개체 유형을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-115">They are most often strings or integers, but they can have any object type.</span></span> <span data-ttu-id="c2a5c-116">또한 키 값이 다른 해시 테이블인 중첩 된 해시 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-116">You can also create nested hash tables, in which the value of a key is another hash table.</span></span>

<span data-ttu-id="c2a5c-117">해시 테이블은 데이터를 찾고 검색 하는 데 매우 효율적 이기 때문에 자주 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-117">Hash tables are frequently used because they are very efficient for finding and retrieving data.</span></span> <span data-ttu-id="c2a5c-118">해시 테이블을 사용 하 여 목록을 저장 하 고 PowerShell에서 계산 된 속성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-118">You can use hash tables to store lists and to create calculated properties in PowerShell.</span></span> <span data-ttu-id="c2a5c-119">그리고 PowerShell에는 문자열을 해시 테이블로 변환 하는 Convertfrom-csv cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-119">And, PowerShell has a cmdlet, ConvertFrom-StringData, that converts strings to a hash table.</span></span>

### <a name="syntax"></a><span data-ttu-id="c2a5c-120">Syntax</span><span class="sxs-lookup"><span data-stu-id="c2a5c-120">Syntax</span></span>

<span data-ttu-id="c2a5c-121">해시 테이블의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-121">The syntax of a hash table is as follows:</span></span>

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="c2a5c-122">순서가 지정 된 사전의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-122">The syntax of an ordered dictionary is as follows:</span></span>

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="c2a5c-123">[정렬 된] 특성은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-123">The [ordered] attribute was introduced in PowerShell 3.0.</span></span>

### <a name="creating-hash-tables"></a><span data-ttu-id="c2a5c-124">해시 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="c2a5c-124">Creating Hash Tables</span></span>

<span data-ttu-id="c2a5c-125">해시 테이블을 만들려면 다음 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-125">To create a hash table, follow these guidelines:</span></span>

- <span data-ttu-id="c2a5c-126">@ 기호를 사용 하 여 해시 테이블을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-126">Begin the hash table with an at sign (@).</span></span>
- <span data-ttu-id="c2a5c-127">해시 테이블을 중괄호 ()로 묶습니다 {} .</span><span class="sxs-lookup"><span data-stu-id="c2a5c-127">Enclose the hash table in braces ({}).</span></span>
- <span data-ttu-id="c2a5c-128">해시 테이블의 내용에 대해 하나 이상의 키/값 쌍을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-128">Enter one or more key/value pairs for the content of the hash table.</span></span>
- <span data-ttu-id="c2a5c-129">등호 (=)를 사용 하 여 각 키를 해당 값과 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-129">Use an equal sign (=) to separate each key from its value.</span></span>
- <span data-ttu-id="c2a5c-130">세미콜론 (;)을 사용 합니다. 또는 줄 바꿈으로 키/값 쌍을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-130">Use a semicolon (;) or a line break to separate the key/value pairs.</span></span>
- <span data-ttu-id="c2a5c-131">공백을 포함 하는 키는 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-131">Key that contains spaces must be enclosed in quotation marks.</span></span> <span data-ttu-id="c2a5c-132">값은 유효한 PowerShell 식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-132">Values must be valid PowerShell expressions.</span></span> <span data-ttu-id="c2a5c-133">문자열은 공백이 포함 되지 않은 경우에도 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-133">Strings must appear in quotation marks, even if they do not include spaces.</span></span>
- <span data-ttu-id="c2a5c-134">해시 테이블을 관리 하려면 변수에 변수를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-134">To manage the hash table, save it in a variable.</span></span>
- <span data-ttu-id="c2a5c-135">변수에 순서가 지정 된 해시 테이블을 할당 하는 경우에는 [순서가 지정 된] 특성을 "@" 기호 앞에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-135">When assigning an ordered hash table to a variable, place the [ordered] attribute before the "@" symbol.</span></span> <span data-ttu-id="c2a5c-136">변수 이름 앞에 놓으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-136">If you place it before the variable name, the command fails.</span></span>

<span data-ttu-id="c2a5c-137">$Hash 값에 빈 해시 테이블을 만들려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-137">To create an empty hash table in the value of $hash, type:</span></span>

```powershell
$hash = @{}
```

<span data-ttu-id="c2a5c-138">해시 테이블을 만들 때 키 및 값을 해시 테이블에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-138">You can also add keys and values to a hash table when you create it.</span></span> <span data-ttu-id="c2a5c-139">예를 들어 다음 문은 세 개의 키가 있는 해시 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-139">For example, the following statement creates a hash table with three keys.</span></span>

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a><span data-ttu-id="c2a5c-140">정렬 된 사전 만들기</span><span class="sxs-lookup"><span data-stu-id="c2a5c-140">Creating Ordered Dictionaries</span></span>

<span data-ttu-id="c2a5c-141">OrderedDictionary 형식의 개체를 추가 하 여 정렬 된 사전을 만들 수 있지만 정렬 된 사전을 만드는 가장 쉬운 방법은 [정렬 된] 특성을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-141">You can create an ordered dictionary by adding an object of the OrderedDictionary type, but the easiest way to create an ordered dictionary is use the [Ordered] attribute.</span></span>

<span data-ttu-id="c2a5c-142">[정렬 된] 특성은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-142">The [ordered] attribute is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="c2a5c-143">"@" 기호 바로 앞에 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-143">Place the attribute immediately before the "@" symbol.</span></span>

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

<span data-ttu-id="c2a5c-144">해시 테이블을 사용 하는 것과 동일한 방식으로 순서가 지정 된 사전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-144">You can use ordered dictionaries in the same way that you use hash tables.</span></span>
<span data-ttu-id="c2a5c-145">두 유형을 모두 해시 테이블 또는 사전을 사용 하는 매개 변수 값으로 사용할 수 있습니다 (iDictionary).</span><span class="sxs-lookup"><span data-stu-id="c2a5c-145">Either type can be used as the value of parameters that take a hash table or dictionary (iDictionary).</span></span>

<span data-ttu-id="c2a5c-146">[정렬 된] 특성을 사용 하 여 해시 테이블을 변환 하거나 캐스팅할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-146">You cannot use the [ordered] attribute to convert or cast a hash table.</span></span> <span data-ttu-id="c2a5c-147">정렬 된 특성을 변수 이름 앞에 배치 하는 경우 명령이 실패 하 고 다음과 같은 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-147">If you place the ordered attribute before the variable name, the command fails with the following error message.</span></span>

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

<span data-ttu-id="c2a5c-148">식을 수정 하려면 [정렬 된] 특성을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-148">To correct the expression, move the [ordered] attribute.</span></span>

```powershell
PS C:\> $hash = [ordered]@{}
```

<span data-ttu-id="c2a5c-149">정렬 된 사전을 해시 테이블로 캐스팅할 수 있지만 변수를 지우고 새 값을 입력 하는 경우에도 정렬 된 특성을 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-149">You can cast an ordered dictionary to a hash table, but you cannot recover the ordered attribute, even if you clear the variable and enter new values.</span></span> <span data-ttu-id="c2a5c-150">순서를 다시 설정 하려면 변수를 제거 하 고 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-150">To re-establish the order, you must remove and recreate the variable.</span></span>

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a><span data-ttu-id="c2a5c-151">해시 테이블 표시</span><span class="sxs-lookup"><span data-stu-id="c2a5c-151">Displaying Hash Tables</span></span>

<span data-ttu-id="c2a5c-152">변수에 저장 된 해시 테이블을 표시 하려면 변수 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-152">To display a hash table that is saved in a variable, type the variable name.</span></span>
<span data-ttu-id="c2a5c-153">기본적으로 해시 테이블은 하나의 키 열과 값에 대 한 하나의 열이 있는 테이블로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-153">By default, a hash tables is displayed as a table with one column for keys and one for values.</span></span>

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

<span data-ttu-id="c2a5c-154">해시 테이블에는 키와 값 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-154">Hash tables have Keys and Values properties.</span></span> <span data-ttu-id="c2a5c-155">점 표기법을 사용 하 여 모든 키 또는 모든 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-155">Use dot notation to display all of the keys or all of the values.</span></span>

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

<span data-ttu-id="c2a5c-156">또한 각 키 이름은 해시 테이블의 속성 이며, 해당 값은 키-이름 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-156">Each key name is also a property of the hash table, and its value is the value of the key-name property.</span></span> <span data-ttu-id="c2a5c-157">다음 형식을 사용 하 여 속성 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-157">Use the following format to display the property values.</span></span>

```powershell
$hashtable.<key>
<value>
```

<span data-ttu-id="c2a5c-158">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="c2a5c-158">For example:</span></span>

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

<span data-ttu-id="c2a5c-159">키 이름이 HashTable 형식의 속성 이름 중 하 나와 충돌 하는 경우 `PSBase` 를 사용 하 여 해당 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-159">If the key name collides with one of the property names of the HashTable type, you can use `PSBase` to access those properties.</span></span> <span data-ttu-id="c2a5c-160">예를 들어 키 이름이이 `keys` 고 키 컬렉션을 반환 하려는 경우 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-160">For example, if the key name is `keys` and you want to return the collection of Keys, use this syntax:</span></span>

```powershell
$hashtable.PSBase.Keys
```

<span data-ttu-id="c2a5c-161">해시 테이블에는 해시 테이블의 키-값 쌍 수를 나타내는 Count 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-161">Hash tables have a Count property that indicates the number of key-value pairs in the hash table.</span></span>

```powershell
C:\PS> $hash.count
3
```

<span data-ttu-id="c2a5c-162">해시 테이블 테이블은 배열이 아니므로 해시 테이블에 대 한 인덱스로 정수를 사용할 수 없지만 키 이름을 사용 하 여 해시 테이블로 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-162">Hash table tables are not arrays, so you cannot use an integer as an index into the hash table, but you can use a key name to index into the hash table.</span></span>
<span data-ttu-id="c2a5c-163">키가 문자열 값 이면 키 이름을 따옴표로 묶으십시오.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-163">If the key is a string value, enclose the key name in quotation marks.</span></span>

<span data-ttu-id="c2a5c-164">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="c2a5c-164">For example:</span></span>

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a><span data-ttu-id="c2a5c-165">키 및 값 추가 및 제거</span><span class="sxs-lookup"><span data-stu-id="c2a5c-165">Adding and Removing Keys and Values</span></span>

<span data-ttu-id="c2a5c-166">해시 테이블에 키 및 값을 추가 하려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-166">To add keys and values to a hash table, use the following command format.</span></span>

```powershell
$hash["<key>"] = "<value>"
```

<span data-ttu-id="c2a5c-167">예를 들어, "Now" 값을 가진 "Time" 키를 해시 테이블에 추가 하려면 다음 문 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-167">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash["Time"] = "Now"
```

<span data-ttu-id="c2a5c-168">또한 System.object 개체의 Add 메서드를 사용 하 여 해시 테이블에 키 및 값을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-168">You can also add keys and values to a hash table by using the Add method of the System.Collections.Hashtable object.</span></span> <span data-ttu-id="c2a5c-169">Add 메서드의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-169">The Add method has the following syntax:</span></span>

```powershell
Add(Key, Value)
```

<span data-ttu-id="c2a5c-170">예를 들어, "Now" 값을 가진 "Time" 키를 해시 테이블에 추가 하려면 다음 문 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-170">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash.Add("Time", "Now")
```

<span data-ttu-id="c2a5c-171">더하기 연산자 (+)를 사용 하 여 해시 테이블에 키 및 값을 추가 하 여 기존 해시 테이블에 해시 테이블을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-171">And, you can add keys and values to a hash table by using the addition operator (+) to add a hash table to an existing hash table.</span></span> <span data-ttu-id="c2a5c-172">예를 들어 다음 문은 $hash 변수의 해시 테이블에 "Now" 값을 가진 "Time" 키를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-172">For example, the following statement adds a "Time" key with a value of "Now" to the hash table in the $hash variable.</span></span>

```powershell
$hash = $hash + @{Time="Now"}
```

<span data-ttu-id="c2a5c-173">변수에 저장 된 값을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-173">You can also add values that are stored in variables.</span></span>

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

<span data-ttu-id="c2a5c-174">빼기 연산자를 사용 하 여 해시 테이블에서 키/값 쌍을 제거할 수는 없지만 Hashtable 개체의 Remove 메서드는 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-174">You cannot use a subtraction operator to remove a key/value pair from a hash table, but you can use the Remove method of the Hashtable object.</span></span> <span data-ttu-id="c2a5c-175">Remove 메서드는 키를 해당 값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-175">The Remove method takes the key as its value.</span></span>

<span data-ttu-id="c2a5c-176">Remove 메서드의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-176">The Remove method has the following syntax:</span></span>

```
Remove(Key)
```

<span data-ttu-id="c2a5c-177">예를 들어 $hash 변수 값의 해시 테이블에서 Time = Now key/value 쌍을 제거 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-177">For example, to remove the Time=Now key/value pair from the hash table in the value of the $hash variable, type:</span></span>

```powershell
$hash.Remove("Time")
```

<span data-ttu-id="c2a5c-178">Contains, Clear, Clone 및 CopyTo를 포함 하 여 PowerShell에서 해시 테이블 개체의 모든 속성 및 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-178">You can use all of the properties and methods of Hashtable objects in PowerShell, including Contains, Clear, Clone, and CopyTo.</span></span> <span data-ttu-id="c2a5c-179">해시 테이블 개체에 대 한 자세한 내용은 [system.object](/dotnet/api/system.collections.hashtable)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-179">For more information about Hashtable objects, see [System.Collections.Hashtable](/dotnet/api/system.collections.hashtable).</span></span>

### <a name="object-types-in-hashtables"></a><span data-ttu-id="c2a5c-180">해시 테이블의 개체 형식</span><span class="sxs-lookup"><span data-stu-id="c2a5c-180">Object Types in HashTables</span></span>

<span data-ttu-id="c2a5c-181">해시 테이블의 키와 값은 모든 .NET 개체 유형을 포함할 수 있으며, 단일 해시 테이블에는 여러 유형의 키와 값이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-181">The keys and values in a hash table can have any .NET object type, and a single hash table can have keys and values of multiple types.</span></span>

<span data-ttu-id="c2a5c-182">다음 문은 프로세스 이름 문자열의 해시 테이블을 만들고 개체 값을 처리 한 다음 변수에 저장 합니다 `$p` .</span><span class="sxs-lookup"><span data-stu-id="c2a5c-182">The following statement creates a hash table of process name strings and process object values and saves it in the `$p` variable.</span></span>

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

<span data-ttu-id="c2a5c-183">에서 해시 테이블을 표시 `$p` 하 고 키 이름 속성을 사용 하 여 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-183">You can display the hash table in `$p` and use the key-name properties to display the values.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

<span data-ttu-id="c2a5c-184">해시 테이블의 키는 .NET 형식일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-184">The keys in a hash table can also be any .NET type.</span></span> <span data-ttu-id="c2a5c-185">다음 문은 변수의 해시 테이블에 키/값 쌍을 추가 합니다 `$p` .</span><span class="sxs-lookup"><span data-stu-id="c2a5c-185">The following statement adds a key/value pair to the hash table in the `$p` variable.</span></span> <span data-ttu-id="c2a5c-186">키는 WinRM 서비스를 나타내는 서비스 개체이 고 값은 서비스의 현재 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-186">The key is a Service object that represents the WinRM service, and the value is the current status of the service.</span></span>

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

<span data-ttu-id="c2a5c-187">해시 테이블의 다른 쌍에 사용 하는 것과 동일한 방법을 사용 하 여 새 키/값 쌍을 표시 하 고 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-187">You can display and access the new key/value pair by using the same methods that you use for other pairs in the hash table.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

<span data-ttu-id="c2a5c-188">해시 테이블의 키와 값은 해시 테이블 개체 일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-188">The keys and values in a hash table can also be Hashtable objects.</span></span> <span data-ttu-id="c2a5c-189">다음 문은 키가 문자열인 변수의 해시 테이블에 키/값 쌍을 추가 하 `$p` 고, 값은 3 개의 키/값 쌍이 있는 해시 테이블을 Hash2 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-189">The following statement adds key/value pair to the hash table in the `$p` variable in which the key is a string, Hash2, and the value is a hash table with three key/value pairs.</span></span>

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

<span data-ttu-id="c2a5c-190">동일한 메서드를 사용 하 여 새 값을 표시 하 고 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-190">You can display and access the new values by using the same methods.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a><span data-ttu-id="c2a5c-191">키 및 값 정렬</span><span class="sxs-lookup"><span data-stu-id="c2a5c-191">Sorting Keys and Values</span></span>

<span data-ttu-id="c2a5c-192">해시 테이블의 항목은 기본적으로 순서가 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-192">The items in a hash table are intrinsically unordered.</span></span> <span data-ttu-id="c2a5c-193">키/값 쌍은 표시 될 때마다 다른 순서로 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-193">The key/value pairs might appear in a different order each time that you display them.</span></span>

<span data-ttu-id="c2a5c-194">해시 테이블을 정렬할 수는 없지만, 해시 테이블의 GetEnumerator 메서드를 사용 하 여 키 및 값을 열거 한 다음 Sort-Object cmdlet을 사용 하 여 표시를 위해 열거 된 값을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-194">Although you cannot sort a hash table, you can use the GetEnumerator method of hash tables to enumerate the keys and values, and then use the Sort-Object cmdlet to sort the enumerated values for display.</span></span>

<span data-ttu-id="c2a5c-195">예를 들어 다음 명령은 변수에 있는 해시 테이블의 키와 값을 열거 한 `$p` 다음 키를 알파벳 순서로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-195">For example, the following commands enumerate the keys and values in the hash table in the `$p` variable and then sort the keys in alphabetical order.</span></span>

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

<span data-ttu-id="c2a5c-196">다음 명령은 동일한 절차를 사용 하 여 해시 값을 내림차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-196">The following command uses the same procedure to sort the hash values in descending order.</span></span>

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a><span data-ttu-id="c2a5c-197">해시 테이블에서 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="c2a5c-197">Creating Objects from Hash Tables</span></span>

<span data-ttu-id="c2a5c-198">PowerShell 3.0부터 속성 및 속성 값의 해시 테이블에서 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-198">Beginning in PowerShell 3.0, you can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="c2a5c-199">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-199">The syntax is as follows:</span></span>

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="c2a5c-200">이 메서드는 null 생성자, 즉 매개 변수가 없는 생성자를 포함 하는 클래스에 대해서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-200">This method works only for classes that have a null constructor, that is, a constructor that has no parameters.</span></span> <span data-ttu-id="c2a5c-201">개체 속성은 public 이어야 하며 설정 가능 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-201">The object properties must be public and settable.</span></span>

<span data-ttu-id="c2a5c-202">자세한 내용은 [about_Object_Creation](about_Object_Creation.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-202">For more information, see [about_Object_Creation](about_Object_Creation.md).</span></span>

### <a name="convertfrom-stringdata"></a><span data-ttu-id="c2a5c-203">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="c2a5c-203">ConvertFrom-StringData</span></span>

<span data-ttu-id="c2a5c-204">`ConvertFrom-StringData`Cmdlet은 키/값 쌍의 문자열 또는 문자열을 해시 테이블로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-204">The `ConvertFrom-StringData` cmdlet converts a string or a here-string of key/value pairs into a hash table.</span></span> <span data-ttu-id="c2a5c-205">`ConvertFrom-StringData`스크립트의 데이터 섹션에서 cmdlet을 안전 하 게 사용할 수 있으며이 cmdlet을 cmdlet과 함께 사용 `Import-LocalizedData` 하 여 현재 사용자의 UI (사용자 인터페이스) 문화권에 사용자 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-205">You can use the `ConvertFrom-StringData` cmdlet safely in the Data section of a script, and you can use it with the `Import-LocalizedData` cmdlet to display user messages in the user-interface (UI) culture of the current user.</span></span>

<span data-ttu-id="c2a5c-206">여기서 문자열은 해시 테이블의 값에 따옴표가 포함 된 경우에 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-206">Here-strings are especially useful when the values in the hash table include quotation marks.</span></span> <span data-ttu-id="c2a5c-207">이러한 문자열에 대 한 자세한 내용은 [about_Quoting_Rules](about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-207">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="c2a5c-208">다음 예제에서는 이전 예제에서 사용자 메시지의 여기 문자열을 만드는 방법과를 사용 하 여 `ConvertFrom-StringData` 문자열을 해시 테이블로 변환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-208">The following example shows how to create a here-string of the user messages in the previous example and how to use `ConvertFrom-StringData` to convert them from a string into a hash table.</span></span>

<span data-ttu-id="c2a5c-209">다음 명령은 키/값 쌍의 문자열을 만든 다음 \$ 문자열 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-209">The following command creates a here-string of the key/value pairs and then saves it in the \$string variable.</span></span>

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

<span data-ttu-id="c2a5c-210">이 명령은 ConvertFrom-StringData cmdlet을 사용 하 여 다음 문자열을 해시 테이블로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-210">This command uses the ConvertFrom-StringData cmdlet to convert the here-string into a hash table.</span></span>

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

<span data-ttu-id="c2a5c-211">이러한 문자열에 대 한 자세한 내용은 [about_Quoting_Rules](about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-211">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2a5c-212">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2a5c-212">SEE ALSO</span></span>

[<span data-ttu-id="c2a5c-213">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="c2a5c-213">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="c2a5c-214">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="c2a5c-214">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="c2a5c-215">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="c2a5c-215">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="c2a5c-216">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="c2a5c-216">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="c2a5c-217">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="c2a5c-217">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="c2a5c-218">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="c2a5c-218">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[<span data-ttu-id="c2a5c-219">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="c2a5c-219">System.Collections.Hashtable</span></span>](/dotnet/api/system.collections.hashtable)