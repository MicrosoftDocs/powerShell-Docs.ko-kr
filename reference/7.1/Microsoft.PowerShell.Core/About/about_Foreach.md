---
description: 항목 컬렉션의 모든 항목을 트래버스하는 데 사용할 수 있는 언어 명령을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: 87d4b78df35c8944bdd95a478be4ea0b8d6fbe49
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220913"
---
# <a name="about-foreach"></a><span data-ttu-id="7ac96-104">ForEach 정보</span><span class="sxs-lookup"><span data-stu-id="7ac96-104">About ForEach</span></span>

## <a name="short-description"></a><span data-ttu-id="7ac96-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="7ac96-105">Short description</span></span>
<span data-ttu-id="7ac96-106">항목 컬렉션의 모든 항목을 트래버스하는 데 사용할 수 있는 언어 명령을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-106">Describes a language command you can use to traverse all the items in a collection of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="7ac96-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-107">Long description</span></span>

<span data-ttu-id="7ac96-108">`Foreach`문 (루프 라고도 함)은 `Foreach` 항목 컬렉션의 일련의 값을 단계별로 실행 (반복) 하는 언어 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-108">The `Foreach` statement (also known as a `Foreach` loop) is a language construct for stepping through (iterating) a series of values in a collection of items.</span></span>

<span data-ttu-id="7ac96-109">트래버스할 가장 간단 하 고 가장 일반적인 컬렉션 형식은 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-109">The simplest and most typical type of collection to traverse is an array.</span></span>
<span data-ttu-id="7ac96-110">루프 내에서 `Foreach` 배열의 각 항목에 대해 하나 이상의 명령을 실행 하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-110">Within a `Foreach` loop, it is common to run one or more commands against each item in an array.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ac96-111">구문</span><span class="sxs-lookup"><span data-stu-id="7ac96-111">Syntax</span></span>

<span data-ttu-id="7ac96-112">다음은 구문을 보여 줍니다 `ForEach` .</span><span class="sxs-lookup"><span data-stu-id="7ac96-112">The following shows the `ForEach` syntax:</span></span>

```
foreach ($<item> in $<collection>){<statement list>}
```

<span data-ttu-id="7ac96-113">`ForEach`괄호 안에 있는 문의 부분은 변수와 반복할 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-113">The part of the `ForEach` statement enclosed in parenthesis represents a variable and a collection to iterate.</span></span> <span data-ttu-id="7ac96-114">PowerShell `$<item>` 은 루프가 실행 될 때 변수를 자동으로 만듭니다 `Foreach` .</span><span class="sxs-lookup"><span data-stu-id="7ac96-114">PowerShell creates the variable `$<item>` automatically when the `Foreach` loop runs.</span></span> <span data-ttu-id="7ac96-115">루프를 반복 하기 전에 변수는 컬렉션의 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-115">Prior to each iteration through the loop, the variable is set to a value in the collection.</span></span>
<span data-ttu-id="7ac96-116">문 뒤의 블록에는 `Foreach` `{<statement list>}` 컬렉션의 각 항목에 대해 실행할 명령 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-116">The block following a `Foreach` statement `{<statement list>}` contains a set of commands to execute against each item in a collection.</span></span>

### <a name="examples"></a><span data-ttu-id="7ac96-117">예</span><span class="sxs-lookup"><span data-stu-id="7ac96-117">Examples</span></span>

<span data-ttu-id="7ac96-118">예를 들어 `Foreach` 다음 예제의 루프는 배열의 값을 표시 합니다 `$letterArray` .</span><span class="sxs-lookup"><span data-stu-id="7ac96-118">For example, the `Foreach` loop in the following example displays the values in the `$letterArray` array.</span></span>

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

<span data-ttu-id="7ac96-119">이 예제에서는 `$letterArray` 배열이 생성 되 고 문자열 값,, 및를 사용 하 여 초기화 됩니다 `"a"` `"b"` `"c"` `"d"` .</span><span class="sxs-lookup"><span data-stu-id="7ac96-119">In this example, the `$letterArray` array is created and initialized with the string values `"a"`, `"b"`, `"c"`, and `"d"`.</span></span> <span data-ttu-id="7ac96-120">`Foreach`문이 처음 실행 될 때 `$letter` 변수는 ()의 첫 번째 항목으로 설정 `$letterArray` `"a"` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-120">The first time the `Foreach` statement runs, it sets the `$letter` variable equal to the first item in `$letterArray` (`"a"`).</span></span> <span data-ttu-id="7ac96-121">그런 다음 cmdlet을 사용 하 여 `Write-Host` 문자 a를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-121">Then, it uses the `Write-Host` cmdlet to display the letter a.</span></span> <span data-ttu-id="7ac96-122">다음 번에 루프를 통해를로 `$letter` 설정 `"b"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-122">The next time through the loop, `$letter` is set to `"b"`, and so on.</span></span> <span data-ttu-id="7ac96-123">루프에서 `Foreach` 문자 d를 표시 한 후 PowerShell은 루프를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-123">After the `Foreach` loop displays the letter d, PowerShell exits the loop.</span></span>

<span data-ttu-id="7ac96-124">`Foreach`PowerShell 명령 프롬프트에서 명령으로 실행 하려면 전체 문이 한 줄에 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-124">The entire `Foreach` statement must appear on a single line to run it as a command at the PowerShell command prompt.</span></span> <span data-ttu-id="7ac96-125">`Foreach`대신 ps1 스크립트 파일에 명령을 추가 하는 경우 전체 문이 한 줄에 표시 되지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-125">The entire `Foreach` statement does not have to appear on a single line if you place the command in a .ps1 script file instead.</span></span>

<span data-ttu-id="7ac96-126">`Foreach` 문을 항목 컬렉션을 반환 하는 cmdlet과 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-126">`Foreach` statements can also be used together with cmdlets that return a collection of items.</span></span> <span data-ttu-id="7ac96-127">다음 예에서는 Foreach 문이 cmdlet에 의해 반환 되는 항목 목록을 단계별로 안내 합니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="7ac96-127">In the following example, the Foreach statement steps through the list of items that is returned by the `Get-ChildItem` cmdlet.</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

<span data-ttu-id="7ac96-128">문을 사용 하 여 반환 되는 결과를 제한 하 여 예제를 구체화할 수 있습니다 `If` .</span><span class="sxs-lookup"><span data-stu-id="7ac96-128">You can refine the example by using an `If` statement to limit the results that are returned.</span></span> <span data-ttu-id="7ac96-129">다음 예제에서 `Foreach` 문은 이전 예제와 동일한 반복 작업을 수행 하지만, `If` 결과를 100 kb 보다 큰 파일로 제한 하는 문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-129">In the following example, the `Foreach` statement performs the same looping operation as the previous example, but it adds an `If` statement to limit the results to files that are greater than 100 kilobytes (KB):</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

<span data-ttu-id="7ac96-130">이 예에서 `Foreach` 루프는 변수의 속성을 사용 하 여 `$file` 비교 작업을 수행 `$file.length -gt 100KB` 합니다 ().</span><span class="sxs-lookup"><span data-stu-id="7ac96-130">In this example, the `Foreach` loop uses a property of the `$file` variable to perform a comparison operation (`$file.length -gt 100KB`).</span></span> <span data-ttu-id="7ac96-131">변수는 cmdlet에서 반환 되는 `$file` 개체의 모든 속성을 포함 합니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="7ac96-131">The `$file` variable contains all the properties in the object that is returned by the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="7ac96-132">따라서 단순히 파일 이름 이상의 이름을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-132">Therefore, you can return more than just a file name.</span></span>
<span data-ttu-id="7ac96-133">다음 예제에서 PowerShell은 문 목록 내에서의 길이와 마지막 액세스 시간을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-133">In the next example, PowerShell returns the length and the last access time inside the statement list:</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
    Write-Host $file.length
    Write-Host $file.lastaccesstime
  }
}
```

<span data-ttu-id="7ac96-134">이 예에서는 문 목록에서 단일 명령을 실행 하는 것으로 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-134">In this example, you are not limited to running a single command in a statement list.</span></span>

<span data-ttu-id="7ac96-135">루프 외부에서 변수를 사용 하 `Foreach` 고 루프 내에서 변수를 증가 시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-135">You can also use a variable outside a `Foreach` loop and increment the variable inside the loop.</span></span> <span data-ttu-id="7ac96-136">다음 예제에서는 크기가 100 KB를 초과 하는 파일 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-136">The following example counts files over 100 KB in size:</span></span>

```powershell
$i = 0
foreach ($file in Get-ChildItem) {
  if ($file.length -gt 100KB) {
    Write-Host $file "file size:" ($file.length / 1024).ToString("F0") KB
    $i = $i + 1
  }
}

if ($i -ne 0) {
  Write-Host
  Write-Host $i " file(s) over 100 KB in the current directory."
}
else {
  Write-Host "No files greater than 100 KB in the current directory."
}
```

<span data-ttu-id="7ac96-137">위의 예제에서 `$i` 변수는 루프 외부로 설정 되 `0` 고, 발견 된 각 파일에 대 한 루프 내에서 100 보다 큰 변수가 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-137">In the preceding example, the `$i` variable is set to `0` outside the loop, and the variable is incremented inside the loop for each file that is found that is larger than 100 KB.</span></span> <span data-ttu-id="7ac96-138">루프가 종료 되 면 `If` 문은의 값을 평가 하 여 `$i` 100 KB를 초과 하는 모든 파일의 수를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-138">When the loop exits, an `If` statement evaluates the value of `$i` to display a count of all the files over 100 KB.</span></span> <span data-ttu-id="7ac96-139">또는 100 KB 이상의 파일이 없다는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-139">Or, it displays a message stating that no files over 100 KB were found.</span></span>

<span data-ttu-id="7ac96-140">이전 예제에서는 파일 길이 결과의 형식을 지정 하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-140">The previous example also demonstrates how to format the file length results:</span></span>

```powershell
($file.length / 1024).ToString("F0")
```

<span data-ttu-id="7ac96-141">값은 1024로 나뉘어 결과를 바이트 대신 킬로바이트 단위로 표시 하 고 결과 값은 고정 소수점 서식 지정자를 사용 하 여 형식 지정 된 후 결과에서 10 진수 값을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-141">The value is divided by 1,024 to show the results in kilobytes rather than bytes, and the resulting value is then formatted using the fixed-point format specifier to remove any decimal values from the result.</span></span> <span data-ttu-id="7ac96-142">0을 지정 하면 형식 지정자에 소수 자릿수가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-142">The 0 makes the format specifier show no decimal places.</span></span>

<span data-ttu-id="7ac96-143">다음 예제에서 정의 된 함수는 PowerShell 스크립트 및 스크립트 모듈을 구문 분석 하 고 내에 포함 된 함수의 위치를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-143">In the following example, the function defined parses PowerShell scripts and script modules and returns the location of functions contained within.</span></span> <span data-ttu-id="7ac96-144">이 예제에서는 메서드를 사용 하는 방법 `MoveNext` (루프에서와 유사 하 게 작동 함 `skip X` `For` )과 `Current` `$foreach` foreach 스크립트 블록 내의 변수 속성을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-144">The example demonstrates how to use the `MoveNext` method (which works similarly to `skip X` on a `For` loop) and the `Current` property of the `$foreach` variable inside of a foreach script block.</span></span> <span data-ttu-id="7ac96-145">예제 함수는 여러 줄에 걸쳐 있는 함수 정의가 비정상적 이거나 일관 되지 않은 경우에도 스크립트에서 함수를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac96-145">The example function can find functions in a script even if there are unusually- or inconsistently-spaced function definitions that span multiple lines.</span></span>

<span data-ttu-id="7ac96-146">자세한 내용은 [열거자 사용](about_Automatic_Variables.md#using-enumerators)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac96-146">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators).</span></span>

```powershell
function Get-FunctionPosition {
  [CmdletBinding()]
  [OutputType('FunctionPosition')]
  param(
    [Parameter(Position = 0, Mandatory,
      ValueFromPipeline, ValueFromPipelineByPropertyName)]
    [ValidateNotNullOrEmpty()]
    [Alias('PSPath')]
    [System.String[]]
    $Path
  )

  process {
    try {
      $filesToProcess = if ($_ -is [System.IO.FileSystemInfo]) {
        $_
      } else {
        $filesToProcess = Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      foreach ($item in $filesToProcess) {
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $ast = $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors))
        if ($errors) {
          $msg = "File '{0}' has {1} parser errors." -f $item.FullName,
            $errors.Count
          Write-Warning $msg
        }
        :tokenLoop foreach ($token in $tokens) {
          if ($token.Kind -ne 'Function') {
            continue
          }
          $position = $token.Extent.StartLineNumber
          do {
            if (-not $foreach.MoveNext()) {
              break tokenLoop
            }
            $token = $foreach.Current
          } until ($token.Kind -in @('Generic', 'Identifier'))
          $functionPosition = [pscustomobject]@{
            Name       = $token.Text
            LineNumber = $position
            Path       = $item.FullName
          }
          Add-Member -InputObject $functionPosition `
            -TypeName FunctionPosition -PassThru
        }
      }
    }
    catch {
      throw
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="7ac96-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ac96-147">SEE ALSO</span></span>

[<span data-ttu-id="7ac96-148">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="7ac96-148">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="7ac96-149">about_If</span><span class="sxs-lookup"><span data-stu-id="7ac96-149">about_If</span></span>](about_If.md)

[<span data-ttu-id="7ac96-150">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="7ac96-150">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

