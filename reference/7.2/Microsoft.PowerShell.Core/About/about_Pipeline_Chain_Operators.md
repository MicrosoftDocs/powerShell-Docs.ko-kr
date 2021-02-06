---
description: '`&&`PowerShell에서 및 연산자를 사용 하 여 파이프라인을 연결 하는 방법을 설명 합니다 `||` .'
Locale: en-US
ms.date: 09/30/2019
schema: 2.0.0
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: ece84ec061126401e53bf58112cd79a07a816e8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603311"
---
# <a name="about-pipeline-chain-operators"></a><span data-ttu-id="54940-103">파이프라인 체인 연산자 정보</span><span class="sxs-lookup"><span data-stu-id="54940-103">About Pipeline Chain Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="54940-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="54940-104">Short description</span></span>

<span data-ttu-id="54940-105">`&&`PowerShell에서 및 연산자를 사용 하 여 파이프라인을 연결 하는 방법을 설명 합니다 `||` .</span><span class="sxs-lookup"><span data-stu-id="54940-105">Describes chaining pipelines with the `&&` and `||` operators in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="54940-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="54940-106">Long description</span></span>

<span data-ttu-id="54940-107">PowerShell 7부터 PowerShell은 `&&` 및 연산자를 구현 `||` 하 여 조건부로 파이프라인을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-107">Beginning in PowerShell 7, PowerShell implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="54940-108">이러한 연산자는 PowerShell에서 *파이프라인 체인 연산자로* 알려져 있으며, bash, zsh 및 sh와 같은 POSIX 셸 [및](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) Windows 명령 셸에서의 [조건부 처리 기호](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) (cmd.exe)와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-108">These operators are known in PowerShell as *pipeline chain operators*, and are similar to [AND-OR lists](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) in POSIX shells like bash, zsh and sh, as well as [conditional processing symbols](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) in the Windows Command Shell (cmd.exe).</span></span>

<span data-ttu-id="54940-109">`&&` 연산자는 왼쪽 파이프라인이 성공한 경우 오른쪽 파이프라인을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-109">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="54940-110">반대로, `||` 연산자는 왼쪽 파이프라인이 실패한 경우 오른쪽 파이프라인을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-110">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

<span data-ttu-id="54940-111">이러한 연산자는 `$?` 및 `$LASTEXITCODE` 변수를 사용하여 파이프라인이 실패했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-111">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="54940-112">이렇게 하면 cmdlet 또는 함수뿐만 아니라 네이티브 명령과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-112">This allows you to use them with native commands and not just with cmdlets or functions.</span></span> <span data-ttu-id="54940-113">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="54940-113">For example:</span></span>

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a><span data-ttu-id="54940-114">예</span><span class="sxs-lookup"><span data-stu-id="54940-114">Examples</span></span>

#### <a name="two-successful-commands"></a><span data-ttu-id="54940-115">두 개의 성공한 명령</span><span class="sxs-lookup"><span data-stu-id="54940-115">Two successful commands</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a><span data-ttu-id="54940-116">첫 번째 명령이 실패 하 고 두 번째 명령이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-116">First command fails, causing second not to be executed</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a><span data-ttu-id="54940-117">첫 번째 명령은 성공 하므로 두 번째 명령이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-117">First command succeeds, so the second command is not executed</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a><span data-ttu-id="54940-118">첫 번째 명령이 실패 하므로 두 번째 명령이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54940-118">First command fails, so the second command is executed</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

<span data-ttu-id="54940-119">파이프라인 성공은 변수의 값으로 정의 됩니다 `$?` . PowerShell은 실행 상태에 따라 파이프라인을 실행 한 후 자동으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54940-119">Pipeline success is defined by the value of the `$?` variable, which PowerShell automatically sets after executing a pipeline based on its execution status.</span></span>
<span data-ttu-id="54940-120">즉, 파이프라인 체인 연산자의 동일성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-120">This means that pipeline chain operators have the following equivalence:</span></span>

```powershell
Test-Command '1' && Test-Command '2'
```

<span data-ttu-id="54940-121">는와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-121">works the same as</span></span>

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

<span data-ttu-id="54940-122">및</span><span class="sxs-lookup"><span data-stu-id="54940-122">and</span></span>

```powershell
Test-Command '1' || Test-Command '2'
```

<span data-ttu-id="54940-123">는와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-123">works the same as</span></span>

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a><span data-ttu-id="54940-124">파이프라인 체인에서 할당</span><span class="sxs-lookup"><span data-stu-id="54940-124">Assignment from pipeline chains</span></span>

<span data-ttu-id="54940-125">파이프라인 체인에서 변수를 할당 하면 체인에 있는 모든 파이프라인이 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54940-125">Assigning a variable from a pipeline chain takes the concatenation of all the pipelines in the chain:</span></span>

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

<span data-ttu-id="54940-126">파이프라인 체인에서 할당 하는 동안 스크립트 종료 오류가 발생 하면 할당에 성공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-126">If a script-terminating error occurs during assignment from a pipeline chain, the assignment does not succeed:</span></span>

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a><span data-ttu-id="54940-127">연산자 구문 및 우선 순위</span><span class="sxs-lookup"><span data-stu-id="54940-127">Operator syntax and precedence</span></span>

<span data-ttu-id="54940-128">예를 들어 다른 연산자와 달리 `&&` 및는 `||` 또는와 같은 식이 아니라 파이프라인에서 작동 `+` `-and` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-128">Unlike other operators, `&&` and `||` operate on pipelines, rather than on expressions like `+` or `-and`, for example.</span></span>

<span data-ttu-id="54940-129">`&&` 및는 `||` 파이프 () `|` 또는 리디렉션 () 보다 우선 순위가 낮으므로 `>` 작업 연산자 ( `&` ), 할당 ( `=` ) 또는 세미콜론 () 보다 우선 순위가 높습니다 `;` .</span><span class="sxs-lookup"><span data-stu-id="54940-129">`&&` and `||` have a lower precedence than piping (`|`) or redirection (`>`), but a higher precedence than job operators (`&`), assignment (`=`) or semicolons (`;`).</span></span> <span data-ttu-id="54940-130">즉, 파이프라인 체인 내의 파이프라인은 개별적으로 리디렉션될 수 있으며 전체 파이프라인 체인을 backgrounded 하거나 변수에 할당 하거나 문으로 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-130">This means that pipelines within a pipeline chain can be individually redirected, and that entire pipeline chains can be backgrounded, assigned to variables, or separated as statements.</span></span>

<span data-ttu-id="54940-131">파이프라인 체인 내에서 낮은 우선 순위 구문을 사용 하려면 괄호를 사용 하는 것이 좋습니다 `(...)` .</span><span class="sxs-lookup"><span data-stu-id="54940-131">To use lower precedence syntax within a pipeline chain, consider the use of parentheses `(...)`.</span></span>
<span data-ttu-id="54940-132">마찬가지로 파이프라인 체인 내에 문을 포함 하려면 하위 식을 `$(...)` 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-132">Similarly, to embed a statement within a pipeline chain, a subexpression `$(...)` can be used.</span></span>
<span data-ttu-id="54940-133">이는 네이티브 명령과 제어 흐름을 결합 하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-133">This can be useful for combining native commands with control flow:</span></span>

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

<span data-ttu-id="54940-134">PowerShell 7을 통해 이러한 구문에 대 한 동작이 변경 되어 `$?` 괄호 또는 하위 식 내에서 명령이 성공 하거나 실패 하는 경우가 예상 대로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54940-134">As of PowerShell 7, the behaviour of these syntaxes has been changed so that `$?` is set as expected when a command succeeds or fails within parentheses or a subexpression.</span></span>

<span data-ttu-id="54940-135">PowerShell에서 대부분의 다른 연산자와 마찬가지로 `&&` 및 `||` 은 *왼쪽* 에서 그룹화 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-135">Like most other operators in PowerShell, `&&` and `||` are also *left-associative*, meaning they group from the left.</span></span> <span data-ttu-id="54940-136">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="54940-136">For example:</span></span>

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

<span data-ttu-id="54940-137">그룹화 할 위치:</span><span class="sxs-lookup"><span data-stu-id="54940-137">will group as:</span></span>

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

<span data-ttu-id="54940-138">다음과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="54940-138">being equivalent to:</span></span>

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a><span data-ttu-id="54940-139">오류 상호 작용</span><span class="sxs-lookup"><span data-stu-id="54940-139">Error interaction</span></span>

<span data-ttu-id="54940-140">파이프라인 체인 연산자에는 오류가 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-140">Pipeline chain operators do not absorb errors.</span></span> <span data-ttu-id="54940-141">파이프라인 체인의 문이 스크립트 종료 오류를 throw 하는 경우 파이프라인 체인이 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54940-141">When a statement in a pipeline chain throws a script-terminating error, the pipeline chain is terminated.</span></span>

<span data-ttu-id="54940-142">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="54940-142">For example:</span></span>

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

<span data-ttu-id="54940-143">오류가 catch 되어도 파이프라인 체인이 여전히 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54940-143">Even when the error is caught, the pipeline chain is still terminated:</span></span>

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

<span data-ttu-id="54940-144">오류가 종료 되지 않거나 파이프라인을 종료 하는 경우 파이프라인 체인은 다음 값을 준수 합니다 `$?` .</span><span class="sxs-lookup"><span data-stu-id="54940-144">If an error is non-terminating, or only terminates a pipeline, the pipeline chain continues, respecting the value of `$?`:</span></span>

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a><span data-ttu-id="54940-145">명령 대신 파이프라인 연결</span><span class="sxs-lookup"><span data-stu-id="54940-145">Chaining pipelines rather than commands</span></span>

<span data-ttu-id="54940-146">파이프라인 체인 연산자는 이름을 기준으로 하 여 단순히 명령만이 아니라 파이프라인을 연결 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-146">Pipeline chain operators, by their name, can be used to chain pipelines, rather than just commands.</span></span> <span data-ttu-id="54940-147">이는 다른 셸의 동작과 일치 하지만 *성공을* 확인 하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-147">This matches the behavior of other shells, but can make *success* harder to determine:</span></span>

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

<span data-ttu-id="54940-148">가 `Write-Output 'All done!'` `Test-NotTwo` 종료 되지 않는 오류를 생성 한 후에 실패 한 것으로 간주 되므로이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54940-148">Note that `Write-Output 'All done!'` is not executed, since `Test-NotTwo` is deemed to have failed after generating the non-terminating error.</span></span>

## <a name="see-also"></a><span data-ttu-id="54940-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54940-149">See also</span></span>

- [<span data-ttu-id="54940-150">about_Operators</span><span class="sxs-lookup"><span data-stu-id="54940-150">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="54940-151">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="54940-151">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="54940-152">about_pipelines</span><span class="sxs-lookup"><span data-stu-id="54940-152">about_pipelines</span></span>](about_pipelines.md)

