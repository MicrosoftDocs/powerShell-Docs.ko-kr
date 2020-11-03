---
description: 조인 연산자 (-조인)가 여러 문자열을 단일 문자열로 결합 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_join
ms.openlocfilehash: 3e5bf4363adbded29dc58facde00f6597abeb697
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222730"
---
# <a name="about-join"></a><span data-ttu-id="da61c-104">조인 정보</span><span class="sxs-lookup"><span data-stu-id="da61c-104">About join</span></span>

## <a name="short-description"></a><span data-ttu-id="da61c-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="da61c-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="da61c-106">조인 연산자 (-조인)가 여러 문자열을 단일 문자열로 결합 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-106">Describes how the join operator (-join) combines multiple strings into a single string.</span></span>

## <a name="long-description"></a><span data-ttu-id="da61c-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="da61c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="da61c-108">Join 연산자는 문자열 집합을 단일 문자열로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-108">The join operator concatenates a set of strings into a single string.</span></span> <span data-ttu-id="da61c-109">문자열은 결과 문자열에 명령에 표시 되는 순서 대로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-109">The strings are appended to the resulting string in the order that they appear in the command.</span></span>

### <a name="syntax"></a><span data-ttu-id="da61c-110">구문</span><span class="sxs-lookup"><span data-stu-id="da61c-110">Syntax</span></span>

<span data-ttu-id="da61c-111">다음 다이어그램에서는 조인 연산자의 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-111">The following diagram shows the syntax for the join operator.</span></span>

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a><span data-ttu-id="da61c-112">매개 변수</span><span class="sxs-lookup"><span data-stu-id="da61c-112">Parameters</span></span>

<span data-ttu-id="da61c-113">String []-조인할 문자열을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-113">String[] - Specifies one or more strings to be joined.</span></span>

<span data-ttu-id="da61c-114">Delimiter-연결 된 문자열 사이에 배치 되는 하나 이상의 문자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-114">Delimiter - Specifies one or more characters placed between the concatenated strings.</span></span> <span data-ttu-id="da61c-115">기본값은 구분 기호 ("")가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-115">The default is no delimiter ("").</span></span>

<span data-ttu-id="da61c-116">설명</span><span class="sxs-lookup"><span data-stu-id="da61c-116">Remarks</span></span>

<span data-ttu-id="da61c-117">단항 조인 연산자 (-join <string [] >)는 쉼표 보다 우선 순위가 높습니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-117">The unary join operator (-join <string[]>) has higher precedence than a comma.</span></span> <span data-ttu-id="da61c-118">결과적으로, 쉼표로 구분 된 문자열 목록을 단항 join 연산자에 제출 하면 첫 번째 쉼표 앞의 첫 번째 문자열만 조인 연산자에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-118">As a result, if you submit a comma-separated list of strings to the unary join operator, only the first string (before the first comma) is submitted to the join operator.</span></span>

<span data-ttu-id="da61c-119">단항 조인 연산자를 사용 하려면 문자열을 괄호로 묶거나 변수에 문자열을 저장 한 다음 조인할 변수를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-119">To use the unary join operator, enclose the strings in parentheses, or store the strings in a variable, and then submit the variable to join.</span></span>

<span data-ttu-id="da61c-120">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-120">For example:</span></span>

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a><span data-ttu-id="da61c-121">예</span><span class="sxs-lookup"><span data-stu-id="da61c-121">Examples</span></span>

<span data-ttu-id="da61c-122">다음 문은 세 개의 문자열을 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-122">The following statement joins three strings:</span></span>

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

<span data-ttu-id="da61c-123">다음 문은 공백으로 구분 된 세 개의 문자열을 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-123">The following statement joins three strings delimited by a space:</span></span>

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

<span data-ttu-id="da61c-124">다음 문에서는 여러 문자 구분 기호를 사용 하 여 세 개의 문자열을 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-124">The following statements use a multiple-character delimiter to join three strings:</span></span>

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

<span data-ttu-id="da61c-125">다음 문은 문자열의 줄을 단일 문자열로 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-125">The following statement joins the lines in a here-string into a single string.</span></span> <span data-ttu-id="da61c-126">여기에 있는 문자열은 하나의 문자열 이기 때문에 조인 하려면 여기 문자열의 줄을 분할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-126">Because a here-string is one string, the lines in the here-string must be split before they can be joined.</span></span> <span data-ttu-id="da61c-127">이 메서드를 사용 하 여 다음 문자열에 저장 된 XML 파일의 문자열을 다시 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da61c-127">You can use this method to rejoin the strings in an XML file that has been saved in a here-string:</span></span>

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a><span data-ttu-id="da61c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da61c-128">SEE ALSO</span></span>

[<span data-ttu-id="da61c-129">about_Operators</span><span class="sxs-lookup"><span data-stu-id="da61c-129">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="da61c-130">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="da61c-130">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="da61c-131">about_Split</span><span class="sxs-lookup"><span data-stu-id="da61c-131">about_Split</span></span>](about_Split.md)
