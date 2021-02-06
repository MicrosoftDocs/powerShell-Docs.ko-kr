---
description: 개체 컬렉션에 대 한 스크립팅 필터를 보다 쉽고 자연 스러운 방식으로 설명 합니다.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: dbd30d566414f784e7d5eca04af716c2bf1642b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602268"
---
# <a name="about_simplified_syntax"></a><span data-ttu-id="219c7-103">about_Simplified_Syntax</span><span class="sxs-lookup"><span data-stu-id="219c7-103">about_Simplified_Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="219c7-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="219c7-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="219c7-105">개체 컬렉션에 대 한 스크립팅 필터를 보다 쉽고 자연 스러운 방식으로 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="219c7-105">Describes easier, more natural-language ways of scripting filters for collections of objects.</span></span>

## <a name="long-description"></a><span data-ttu-id="219c7-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="219c7-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="219c7-107">Windows PowerShell 3.0에 도입 된 간단한 구문을 사용 하면 스크립트 블록을 사용 하지 않고 일부 필터 명령을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="219c7-107">Simplified syntax, introduced in Windows PowerShell 3.0, lets you build some filter commands without using script blocks.</span></span> <span data-ttu-id="219c7-108">단순화 된 구문은 자연어와 거의 유사 하며, 주로 명령과 `Where-Object` `ForEach-Object` 해당 별칭 및로 파이프 하는 개체의 컬렉션에 유용 합니다 `where` `foreach` .</span><span class="sxs-lookup"><span data-stu-id="219c7-108">The simplified syntax more closely resembles natural language, and is primarily useful with collections of objects that get piped into commands `Where-Object` and `ForEach-Object` and their corresponding aliases `where` and `foreach`.</span></span>

<span data-ttu-id="219c7-109">스크립트 블록 내에서 자동 변수를 참조 하지 않고 컬렉션 (가장 일반적으로는 배열)의 멤버에 대해 메서드를 사용할 수 있습니다 `$_` .</span><span class="sxs-lookup"><span data-stu-id="219c7-109">You can use a method on the members of a collection (most commonly, an array) without referring to the automatic variable `$_` inside a script block.</span></span>

<span data-ttu-id="219c7-110">다음 두 호출을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="219c7-110">Consider the following two invocations:</span></span>

### <a name="standard-syntax"></a><span data-ttu-id="219c7-111">표준 구문</span><span class="sxs-lookup"><span data-stu-id="219c7-111">Standard Syntax</span></span>

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a><span data-ttu-id="219c7-112">단순화 된 구문</span><span class="sxs-lookup"><span data-stu-id="219c7-112">Simplified syntax</span></span>

<span data-ttu-id="219c7-113">단순화 된 구문에서 컬렉션에 있는 개체의 멤버에 대해 작동 하는 비교 연산자는 매개 변수로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="219c7-113">Under the simplified syntax, comparison operators that work on members of objects in a collection are treated as parameters.</span></span> <span data-ttu-id="219c7-114">스크립트 블록 내에서 자동 변수를 참조 하지 않고 컬렉션의 개체에 대해 메서드를 호출할 수 있습니다 `$_` .</span><span class="sxs-lookup"><span data-stu-id="219c7-114">You can invoke a method on objects in a collection without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="219c7-115">다음 두 호출을 앞의 예제와 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="219c7-115">Compare the following two invocations to those of the previous example:</span></span>

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

<span data-ttu-id="219c7-116">두 구문이 모두 작동 하는 동안 간소화 된 구문은 스크립트 블록 내의 자동 변수를 참조 하지 않고 결과를 반환 합니다 `$_` .</span><span class="sxs-lookup"><span data-stu-id="219c7-116">While both syntaxes work, the simplified syntax returns results without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="219c7-117">메서드 이름은 `GetKeyAlgorithm` 의 매개 변수로 처리 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="219c7-117">The method name `GetKeyAlgorithm` is treated as a parameter of `ForEach-Object`.</span></span>
<span data-ttu-id="219c7-118">단순한 구문은 지정 된 인수가 적용 되지 않은 항목에 대해 결과를 반환 하지 않기 때문에 두 번째 명령은 오류 없이 동일한 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="219c7-118">The second command returns the same results, but without errors, because the simplified syntax does not attempt to return results for items for which the specified argument did not apply.</span></span>

<span data-ttu-id="219c7-119">이 예제에서 속성은 `Process` `Description` 명령에 멤버 이름 매개 변수로 전달 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="219c7-119">In this example, the `Process` property `Description` is passed as the member name parameter to the `ForEach-Object` command.</span></span> <span data-ttu-id="219c7-120">결과는 활성 프로세스에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="219c7-120">The results are descriptions of active processes.</span></span>

```powershell
Get-Process | foreach Description
```

<span data-ttu-id="219c7-121">이 예제에서 메서드는 `DirectoryInfo` `GetFiles` 명령의 멤버 이름 매개 변수로 전달 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="219c7-121">In this example, the `DirectoryInfo` method `GetFiles` is passed as the member name parameter of the `ForEach-Object` command.</span></span>  
<span data-ttu-id="219c7-122">검색 패턴 매개 변수를 사용 하 여 메서드를 호출 합니다 `.*` .</span><span class="sxs-lookup"><span data-stu-id="219c7-122">The method is called with the search pattern parameter `.*`.</span></span>  
<span data-ttu-id="219c7-123">결과는 `FileInfo` 사용자 홈 디렉터리에 있는 모든 Unix 스타일의 숨김 파일에 대 한 레코드입니다.</span><span class="sxs-lookup"><span data-stu-id="219c7-123">The results are `FileInfo` records for all Unix-style hidden files in user home directories.</span></span> 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a><span data-ttu-id="219c7-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="219c7-124">SEE ALSO</span></span>

- [<span data-ttu-id="219c7-125">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="219c7-125">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="219c7-126">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="219c7-126">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="219c7-127">Where-Object</span><span class="sxs-lookup"><span data-stu-id="219c7-127">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
- [<span data-ttu-id="219c7-128">Foreach-개체</span><span class="sxs-lookup"><span data-stu-id="219c7-128">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

