---
ms.date: 04/28/2020
title: PowerShell에서 실험적 기능 사용
description: 현재 사용 가능한 실험적 기능과 사용 방법을 나열합니다.
ms.openlocfilehash: 72a4309d6eeede4cd2ff7c38ce8e99ce3ace30eb
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809189"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="d12c7-103">PowerShell에서 실험적 기능 사용</span><span class="sxs-lookup"><span data-stu-id="d12c7-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="d12c7-104">PowerShell의 실험적 기능 지원에서는 PowerShell 또는 PowerShell 모듈에서 기존의 안정적인 기능과 함께 실험적 기능을 사용할 수 있는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="d12c7-105">실험적 기능은 디자인이 완성되지 않은 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="d12c7-106">사용자는 이 기능을 테스트하고 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="d12c7-107">실험적 기능이 완성되면 해당 디자인 변경 내용은 호환성이 손상되는 변경이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="d12c7-108">이로 인해 중단이 발생할 수 있으므로 실험적 기능은 프로덕션에서 사용하기에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="d12c7-109">실험적 기능은 공식적으로 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="d12c7-110">하지만 피드백과 버그 보고서는 언제나 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="d12c7-111">[GitHub 소스 리포지토리](https://github.com/PowerShell/PowerShell/issues/new/choose)에서 문제를 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="d12c7-112">이러한 기능을 사용 설정 또는 해제하는 방법은 [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d12c7-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="d12c7-113">사용 가능한 기능</span><span class="sxs-lookup"><span data-stu-id="d12c7-113">Available features</span></span>

<span data-ttu-id="d12c7-114">이 문서에서는 사용 가능한 실험적 기능과 해당 기능을 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="d12c7-115">속성</span><span class="sxs-lookup"><span data-stu-id="d12c7-115">Name</span></span>                            |   <span data-ttu-id="d12c7-116">6.2</span><span class="sxs-lookup"><span data-stu-id="d12c7-116">6.2</span></span>   |   <span data-ttu-id="d12c7-117">7.0</span><span class="sxs-lookup"><span data-stu-id="d12c7-117">7.0</span></span>   | <span data-ttu-id="d12c7-118">7.1(미리 보기)</span><span class="sxs-lookup"><span data-stu-id="d12c7-118">7.1 (preview)</span></span> |
| ---------------------------------------------------------- | :-----: | :-----: | :-----------: |
| <span data-ttu-id="d12c7-119">PSTempDrive(PS 7.0 이상에서 일반)</span><span class="sxs-lookup"><span data-stu-id="d12c7-119">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |               |
| <span data-ttu-id="d12c7-120">PSUseAbbreviationExpansion(PS 7.0 이상에서 일반)</span><span class="sxs-lookup"><span data-stu-id="d12c7-120">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |               |
| <span data-ttu-id="d12c7-121">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="d12c7-121">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; |    &check;    |
| <span data-ttu-id="d12c7-122">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="d12c7-122">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; |    &check;    |
| <span data-ttu-id="d12c7-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="d12c7-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; |    &check;    |
| <span data-ttu-id="d12c7-124">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="d12c7-124">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; |    &check;    |
| <span data-ttu-id="d12c7-125">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="d12c7-125">PSNullConditionalOperators</span></span>                                 |         | &check; |    &check;    |
| <span data-ttu-id="d12c7-126">PSUnixFileStat(Windows가 아닌 경우만 해당)</span><span class="sxs-lookup"><span data-stu-id="d12c7-126">PSUnixFileStat (non-Windows only)</span></span>                          |         | &check; |    &check;    |
| <span data-ttu-id="d12c7-127">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="d12c7-127">PSNativePSPathResolution</span></span>                                   |         |         |    &check;    |
| <span data-ttu-id="d12c7-128">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="d12c7-128">PSCultureInvariantReplaceOperator</span></span>                          |         |         |    &check;    |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="d12c7-129">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="d12c7-129">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="d12c7-130">사용자가 디버거를 연결할 때 PowerShell이 현재 위치에서 즉시 중단할지 여부를 결정할 수 있도록 `Debug-Runspace` 및 `Debug-Job` cmdlet에서 **BreakAll** 매개 변수를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-130">Enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="d12c7-131">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="d12c7-131">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="d12c7-132">**CommandNotFoundException** 다음에 유사 일치 검색을 기반으로 가능한 명령을 추천합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-132">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="d12c7-133">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="d12c7-133">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="d12c7-134">`-replace` 연산자 문의 왼쪽 피연산자가 문자열이 아닌 경우 해당 피연산자는 문자열로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-134">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="d12c7-135">이 기능을 사용하지 않도록 설정하면 `-replace` 연산자는 문화권 구분 문자열 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-135">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="d12c7-136">예를 들어 문화권이 프랑스어(fr)로 설정된 경우 값 `1.2`는 문자열 `1,2`로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-136">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="d12c7-137">이 기능을 사용하도록 설정하는 경우:</span><span class="sxs-lookup"><span data-stu-id="d12c7-137">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="d12c7-138">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="d12c7-138">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="d12c7-139">비 Windows 시스템에서 MOF 컴파일이 가능해지고 LCM 없이 `Invoke-DSCResource`를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-139">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="d12c7-140">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="d12c7-140">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="d12c7-141">이 기능은 셸에 입력한 명령을 검사합니다. 모든 명령이 간단한 파이프라인을 구성하는 암시적 원격 구현 프록시 명령인 경우 명령이 함께 일괄 처리되고 단일 원격 파이프라인으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-141">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="d12c7-142">예제:</span><span class="sxs-lookup"><span data-stu-id="d12c7-142">Example:</span></span>

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

<span data-ttu-id="d12c7-143">위에서 설명한 것처럼 일괄 처리 기능을 사용하도록 설정하면 세 개의 암시적 원격 구현 프록시 명령 `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`가 원격 세션에서 실행되고 파이프라인의 결과는 클라이언트에 반환되는 유일한 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-143">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="d12c7-144">이렇게 하면 클라이언트와 원격 세션 간에 전송되는 데이터의 양이 줄어들고 개체 직렬화 및 역직렬화도 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-144">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="d12c7-145">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="d12c7-145">PSNativePSPathResolution</span></span>

<span data-ttu-id="d12c7-146">FileSystem 공급자를 사용하는 PSDrive 경로를 네이티브 명령에 전달하는 경우 확인된 파일 경로가 네이티브 명령에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-146">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="d12c7-147">따라서 이제 `code temp:/test.txt`와 같은 명령이 정상적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-147">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="d12c7-148">또한 Windows에서 `~`로 시작하는 경로는 전체 경로로 확인되고 네이티브 명령에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-148">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="d12c7-149">두 경우 모두 해당 경로는 관련 운영 체제에 대한 디렉터리 구분 기호로 정규화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-149">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="d12c7-150">경로가 PSDrive 또는 `~`(Windows)가 아닌 경우 경로 정규화가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-150">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="d12c7-151">경로가 작은따옴표로 묶여 있으면 이를 확인하여 리터럴로 처리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-151">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="d12c7-152">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="d12c7-152">PSNullConditionalOperators</span></span>

<span data-ttu-id="d12c7-153">Null 조건부 멤버 액세스 연산자 `?.` 및 `?[]`에 대한 새 연산자를 도입합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-153">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="d12c7-154">Null 멤버 액세스 연산자는 스칼라 형식 및 배열 형식에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-154">Null member access operators can used on scalar types and array types.</span></span> <span data-ttu-id="d12c7-155">변수가 null이 아닌 경우 액세스한 멤버의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-155">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="d12c7-156">변수 값이 null이면 null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-156">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="d12c7-157">`propname` 속성에 액세스하고 `$x`가 null이 아닌 경우에만 해당 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-157">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="d12c7-158">마찬가지로 인덱서는 `$x`가 null이 아닌 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-158">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="d12c7-159">`$x`가 null이면 null이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-159">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="d12c7-160">`?.` 및 `?[]` 연산자는 멤버 액세스 연산자이며 변수 이름과 연산자 사이에 공백을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-160">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="d12c7-161">PowerShell에서는 변수 이름의 일부로 `?`를 허용하므로 변수 이름과 연산자 사이에 공백 없이 연산자를 사용하는 경우 명확성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-161">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="d12c7-162">명확성을 위해 변수는 변수 이름 주위에 `{}`를 사용해야 합니다(예: `${x?}?.propertyName` 또는 `${y}?[0]`).</span><span class="sxs-lookup"><span data-stu-id="d12c7-162">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="d12c7-163">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="d12c7-163">PSTempDrive</span></span>

<span data-ttu-id="d12c7-164">사용자의 임시 디렉터리 경로에 매핑된 `TEMP:` PSDrive를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-164">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="d12c7-165">이 기능은 실험적 단계를 벗어났으며 PowerShell 7 이상에서 주요 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-165">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="d12c7-166">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="d12c7-166">PSUnixFileStat</span></span>

<span data-ttu-id="d12c7-167">이 기능은 Unix와 비슷한 파일 목록을 사용할 수 있도록 파일 시스템 공급자의 출력에 Unix **stat** API의 데이터를 포함하는 새로운 동작을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-167">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="d12c7-168">기본 Unix 형식 시스템의 일반 식 `stat(2)` API를 포함하는 **UnixStat**라는 파일 시스템 공급자에서 새 note 속성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-168">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="d12c7-169">`Get-ChildItem`의 출력은 다음과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-169">The output from `Get-ChildItem` should look something like this:</span></span>

```powershell
PS> dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="d12c7-170">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="d12c7-170">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="d12c7-171">이 기능을 사용하면 축약된 cmdlet 및 함수에 대한 탭 완성 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-171">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="d12c7-172">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="d12c7-172">For example:</span></span>

- <span data-ttu-id="d12c7-173">`i-psdf<tab>`는 `Import-PowerShellDataFile`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-173">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="d12c7-174">`u-akvmssdr<tab>``Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`를 반환합니다</span><span class="sxs-lookup"><span data-stu-id="d12c7-174">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="d12c7-175">이는 탭 완성 기능에만 사용할 수 있으므로(대화형) `i-psdf`는 스크립트에서 유효한 cmdlet 이름이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-175">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="d12c7-176">이 기능은 실험적 단계를 벗어났으며 PowerShell 7 이상에서 주요 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="d12c7-176">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>
