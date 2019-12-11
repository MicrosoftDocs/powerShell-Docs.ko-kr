---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 개체 정렬
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030776"
---
# <a name="sorting-objects"></a><span data-ttu-id="e78d3-103">개체 정렬</span><span class="sxs-lookup"><span data-stu-id="e78d3-103">Sorting Objects</span></span>

<span data-ttu-id="e78d3-104">`Sort-Object` cmdlet을 사용하여 표시된 데이터를 검색하기 쉽게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="e78d3-105">`Sort-Object`는 정렬 기준으로 사용할 하나 이상의 속성 이름을 선택하고 이러한 속성의 값을 기준으로 정렬된 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="e78d3-106">기본 정렬</span><span class="sxs-lookup"><span data-stu-id="e78d3-106">Basic sorting</span></span>

<span data-ttu-id="e78d3-107">현재 디렉터리의 하위 디렉터리 및 파일 나열 관련 문제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="e78d3-108">정렬 기준으로 **LastWriteTime**과 **Name**을 차례로 사용하여 정렬하려면 다음과 같이 입력하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

<span data-ttu-id="e78d3-109">또한 **Descending** 스위치 매개 변수를 지정하여 개체를 반대 순서로 정렬할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a><span data-ttu-id="e78d3-110">해시 테이블 사용</span><span class="sxs-lookup"><span data-stu-id="e78d3-110">Using hash tables</span></span>

<span data-ttu-id="e78d3-111">배열에서 해시 테이블을 사용하여 여러 가지 속성을 다양한 순서로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="e78d3-112">각 해시 테이블은 **Expression** 키를 사용하여 속성 이름을 문자열로 지정하고 **Ascending** 또는 **Descending** 키를 사용하여 `$true` 또는 `$false`를 기준으로 정렬 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="e78d3-113">**Expression** 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="e78d3-114">**Ascending** 또는 **Descending** 키는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="e78d3-115">다음 예제에서는 내림차순 **LastWriteTime** 및 오름차순 **Name**으로 개체를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

<span data-ttu-id="e78d3-116">scriptblock을 **Expression** 키로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="e78d3-117">`Sort-Object` cmdlet을 실행하면 scriptblock이 실행되고 결과가 정렬에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="e78d3-118">다음 예제에서는 **CreationTime** 및 **LastWriteTime** 사이의 시간 간격을 기준으로 개체를 내림차순으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a><span data-ttu-id="e78d3-119">팁</span><span class="sxs-lookup"><span data-stu-id="e78d3-119">Tips</span></span>

<span data-ttu-id="e78d3-120">다음과 같이 **Property** 매개 변수 이름을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="e78d3-121">또한 기본 제공 별칭 `sort`를 통해 `Sort-Object`를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="e78d3-122">정렬을 위한 해시 테이블의 키는 다음과 같이 약식으로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="e78d3-123">이 예제에서 **e**는 **Expression**을 나타내고, **d**는 **Descending**을 나타내고, **a**는 **Ascending**을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="e78d3-124">가독성을 개선하기 위해 해시 테이블을 개별 변수에 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e78d3-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
