---
description: 세션에 사용 되는 네임 스페이스를 지정할 수 있습니다.
Locale: en-US
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: b48cd85e200f44cdf9fdf278de78e07a918386c8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891349"
---
# <a name="about-using"></a><span data-ttu-id="5053f-103">사용 정보</span><span class="sxs-lookup"><span data-stu-id="5053f-103">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="5053f-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="5053f-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="5053f-105">세션에 사용 되는 네임 스페이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-105">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="5053f-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="5053f-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="5053f-107">문을 사용 하 여 `using` 세션에서 사용 되는 네임 스페이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-107">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="5053f-108">네임 스페이스를 추가 하면 .NET 클래스 및 멤버를 간단 하 게 사용할 수 있으며 스크립트 모듈 및 어셈블리에서 클래스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-108">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="5053f-109">`using`문은 스크립트의 다른 문 앞에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-109">The `using` statements must come before any other statements in a script.</span></span>

<span data-ttu-id="5053f-110">`using`문은 `using:` 변수에 대 한 범위 한정자와 혼동 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-110">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="5053f-111">자세한 내용은 [about_Remote_Variables](about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5053f-111">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="namespace-syntax"></a><span data-ttu-id="5053f-112">네임 스페이스 구문</span><span class="sxs-lookup"><span data-stu-id="5053f-112">Namespace syntax</span></span>

<span data-ttu-id="5053f-113">형식을 확인할 .NET 네임 스페이스를 지정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-113">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="5053f-114">네임 스페이스를 지정 하면 약식 이름으로 형식을 쉽게 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-114">Specifying a namespace makes it easier to reference types by their short names.</span></span>

## <a name="module-syntax"></a><span data-ttu-id="5053f-115">모듈 구문</span><span class="sxs-lookup"><span data-stu-id="5053f-115">Module syntax</span></span>

<span data-ttu-id="5053f-116">PowerShell 모듈에서 클래스를 로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-116">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="5053f-117">의 값은 `<module-name>` 모듈 이름, 전체 모듈 사양 또는 모듈 파일에 대 한 경로일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-117">The value of `<module-name>` can be a module name, a full module specification, or a path to a module file.</span></span>

<span data-ttu-id="5053f-118">`<module-name>`가 경로인 경우 경로는 정규화 되거나 상대적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-118">When `<module-name>` is a path, the path can be fully qualified or relative.</span></span> <span data-ttu-id="5053f-119">상대 경로는 using 문을 포함 하는 스크립트를 기준으로 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-119">A relative path is resolved relative to the script that contains the using statement.</span></span>

<span data-ttu-id="5053f-120">`<module-name>`이 이름 또는 모듈 지정 인 경우 PowerShell은 **PSModulePath** 에서 지정 된 모듈을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-120">When `<module-name>` is a name or module specification, PowerShell searches the **PSModulePath** for the specified module.</span></span>

<span data-ttu-id="5053f-121">모듈 사양은 다음과 같은 키를 포함 하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-121">A module specification is a hash table that has the following keys.</span></span>

- <span data-ttu-id="5053f-122">`ModuleName` - **필수** 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-122">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="5053f-123">`GUID` - **선택 사항** 모듈의 GUID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-123">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="5053f-124">또한 아래 세 키 중 하나를 지정 **해야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-124">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="5053f-125">이러한 키는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-125">These keys can't be used together.</span></span>
  - <span data-ttu-id="5053f-126">`ModuleVersion` -모듈의 허용 가능한 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-126">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="5053f-127">`RequiredVersion` -필요한 모듈의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-127">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="5053f-128">`MaximumVersion` -모듈의 허용 되는 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-128">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

## <a name="assembly-syntax"></a><span data-ttu-id="5053f-129">어셈블리 구문</span><span class="sxs-lookup"><span data-stu-id="5053f-129">Assembly syntax</span></span>

<span data-ttu-id="5053f-130">.NET 어셈블리에서 형식을 미리 로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-130">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
using assembly <.NET-namespace>
```

<span data-ttu-id="5053f-131">어셈블리를 로드 하면 구문 분석 시 어셈블리의 .NET 형식이 스크립트에 미리 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-131">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="5053f-132">이를 통해 미리 로드 된 어셈블리의 형식을 사용 하는 새 PowerShell 클래스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-132">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="5053f-133">Windows PowerShell 5.1에서는 경로 이름 또는 이름을 기준으로 어셈블리를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-133">In Windows PowerShell 5.1 you can load the assembly by path name or by name.</span></span> <span data-ttu-id="5053f-134">이름을 사용 하는 경우 PowerShell은 .NET GAC (전역 어셈블리 캐시)에서 연결 된 어셈블리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-134">When you use the name, PowerShell searches the .NET Global Assembly Cache (GAC) for the associated assembly.</span></span>

<span data-ttu-id="5053f-135">새 PowerShell 클래스를 만들지 않는 경우 대신 cmdlet을 사용 `Add-Type` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-135">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="5053f-136">자세한 내용은 [추가-형식](xref:Microsoft.PowerShell.Utility.Add-Type)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5053f-136">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="5053f-137">예제</span><span class="sxs-lookup"><span data-stu-id="5053f-137">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="5053f-138">예제 1-typename 확인에 대 한 네임 스페이스 추가</span><span class="sxs-lookup"><span data-stu-id="5053f-138">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="5053f-139">다음 스크립트는 "Hello World" 문자열에 대 한 암호화 해시를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-139">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="5053f-140">및에서 및의에 대 한 참조를 간소화 하는 방법을 확인 `using namespace System.Text` `using namespace System.IO` `[UnicodeEncoding]` `System.Text` `[Stream]` `[MemoryStream]` `System.IO` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-140">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

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

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="5053f-141">예제 2-스크립트 모듈에서 클래스 로드</span><span class="sxs-lookup"><span data-stu-id="5053f-141">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="5053f-142">이 예제에는 다음 클래스를 정의 하는 클래스 \ **게임** 이라는 PowerShell 스크립트 모듈이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-142">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="5053f-143">**게임 데크**</span><span class="sxs-lookup"><span data-stu-id="5053f-143">**CardGames.Deck**</span></span>
- <span data-ttu-id="5053f-144">**게임 카드**</span><span class="sxs-lookup"><span data-stu-id="5053f-144">**CardGames.Card**</span></span>

<span data-ttu-id="5053f-145">`Import-Module` 및 `#requires` 문은 모듈에서 정의한 대로 모듈 함수, 별칭 및 변수만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-145">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="5053f-146">클래스는 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-146">Classes are not imported.</span></span> <span data-ttu-id="5053f-147">이 `using module` 명령은 모듈을 가져오고 클래스 정의도 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-147">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="5053f-148">예제 3-어셈블리에서 클래스 로드</span><span class="sxs-lookup"><span data-stu-id="5053f-148">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="5053f-149">이 예제에서는 해당 클래스를 사용 하 여 새 PowerShell 클래스를 만들 수 있도록 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-149">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="5053f-150">다음 스크립트는 **Directorycontext** 클래스에서 파생 되는 새 PowerShell 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5053f-150">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

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
