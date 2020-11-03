---
description: 세션에 사용 되는 네임 스페이스를 지정할 수 있습니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: 6001f2f4495490c9f2b9dbfbeac2e1f4298febd8
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224977"
---
# <a name="about-using"></a><span data-ttu-id="c36b6-104">사용 정보</span><span class="sxs-lookup"><span data-stu-id="c36b6-104">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="c36b6-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c36b6-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="c36b6-106">세션에 사용 되는 네임 스페이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-106">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="c36b6-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="c36b6-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c36b6-108">문을 사용 하 여 `using` 세션에서 사용 되는 네임 스페이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-108">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="c36b6-109">네임 스페이스를 추가 하면 .NET 클래스 및 멤버를 간단 하 게 사용할 수 있으며 스크립트 모듈 및 어셈블리에서 클래스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-109">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="c36b6-110">`using`문은 스크립트의 다른 문 앞에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-110">The `using` statements must come before any other statements in a script.</span></span>

<span data-ttu-id="c36b6-111">`using`문은 `using:` 변수에 대 한 범위 한정자와 혼동 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-111">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="c36b6-112">자세한 내용은 [about_Remote_Variables](about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c36b6-112">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="c36b6-113">구문</span><span class="sxs-lookup"><span data-stu-id="c36b6-113">Syntax</span></span>

<span data-ttu-id="c36b6-114">형식을 확인할 .NET 네임 스페이스를 지정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-114">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="c36b6-115">PowerShell 모듈에서 클래스를 로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-115">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="c36b6-116">.NET 어셈블리에서 형식을 미리 로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-116">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
```

<span data-ttu-id="c36b6-117">네임 스페이스를 지정 하면 약식 이름으로 형식을 쉽게 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-117">Specifying a namespace makes it easier to reference types by their short names.</span></span>

<span data-ttu-id="c36b6-118">어셈블리를 로드 하면 구문 분석 시 어셈블리의 .NET 형식이 스크립트에 미리 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-118">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="c36b6-119">이를 통해 미리 로드 된 어셈블리의 형식을 사용 하는 새 PowerShell 클래스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-119">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="c36b6-120">새 PowerShell 클래스를 만들지 않는 경우 대신 cmdlet을 사용 `Add-Type` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-120">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="c36b6-121">자세한 내용은 [추가-형식](xref:Microsoft.PowerShell.Utility.Add-Type)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c36b6-121">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="c36b6-122">예</span><span class="sxs-lookup"><span data-stu-id="c36b6-122">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="c36b6-123">예제 1-typename 확인에 대 한 네임 스페이스 추가</span><span class="sxs-lookup"><span data-stu-id="c36b6-123">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="c36b6-124">다음 스크립트는 "Hello World" 문자열에 대 한 암호화 해시를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-124">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="c36b6-125">및에서 및의에 대 한 참조를 간소화 하는 방법을 확인 `using namespace System.Text` `using namespace System.IO` `[UnicodeEncoding]` `System.Text` `[Stream]` `[MemoryStream]` `System.IO` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-125">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="c36b6-126">예제 2-스크립트 모듈에서 클래스 로드</span><span class="sxs-lookup"><span data-stu-id="c36b6-126">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="c36b6-127">이 예제에는 다음 클래스를 정의 하는 클래스 \ **게임** 이라는 PowerShell 스크립트 모듈이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-127">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="c36b6-128">**게임 데크**</span><span class="sxs-lookup"><span data-stu-id="c36b6-128">**CardGames.Deck**</span></span>
- <span data-ttu-id="c36b6-129">**게임 카드**</span><span class="sxs-lookup"><span data-stu-id="c36b6-129">**CardGames.Card**</span></span>

<span data-ttu-id="c36b6-130">`Import-Module` 및 `#requires` 문은 모듈에서 정의한 대로 모듈 함수, 별칭 및 변수만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-130">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="c36b6-131">클래스는 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-131">Classes are not imported.</span></span> <span data-ttu-id="c36b6-132">이 `using module` 명령은 모듈을 가져오고 클래스 정의도 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-132">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="c36b6-133">예제 3-어셈블리에서 클래스 로드</span><span class="sxs-lookup"><span data-stu-id="c36b6-133">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="c36b6-134">이 예제에서는 해당 클래스를 사용 하 여 새 PowerShell 클래스를 만들 수 있도록 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-134">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="c36b6-135">다음 스크립트는 **Directorycontext** 클래스에서 파생 되는 새 PowerShell 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c36b6-135">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```
