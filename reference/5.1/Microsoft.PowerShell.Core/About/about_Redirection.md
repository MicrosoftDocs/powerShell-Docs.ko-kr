---
description: PowerShell에서 텍스트 파일로 출력을 리디렉션하는 방법에 대해 설명 합니다.
keywords: PowerShell, cmdlet
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 59151c31857f12e3a78fd6d292a6a952c312c850
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224314"
---
# <a name="about-redirection"></a><span data-ttu-id="9cab2-104">리디렉션 정보</span><span class="sxs-lookup"><span data-stu-id="9cab2-104">About Redirection</span></span>

## <a name="short-description"></a><span data-ttu-id="9cab2-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9cab2-105">Short description</span></span>
<span data-ttu-id="9cab2-106">PowerShell에서 텍스트 파일로 출력을 리디렉션하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-106">Explains how to redirect output from PowerShell to text files.</span></span>

## <a name="long-description"></a><span data-ttu-id="9cab2-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-107">Long description</span></span>

<span data-ttu-id="9cab2-108">기본적으로 PowerShell은 출력을 PowerShell 호스트로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-108">By default, PowerShell sends output to the PowerShell host.</span></span> <span data-ttu-id="9cab2-109">일반적으로 콘솔 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-109">Usually this is the console application.</span></span> <span data-ttu-id="9cab2-110">그러나 출력을 텍스트 파일로 보낼 수 있으며, 오류 출력을 일반 출력 스트림으로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-110">However, you can direct the output to a text file, and you can redirect error output to the regular output stream.</span></span>

<span data-ttu-id="9cab2-111">다음 메서드를 사용 하 여 출력을 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-111">You can use the following methods to redirect output:</span></span>

- <span data-ttu-id="9cab2-112">Cmdlet을 사용 하 여 `Out-File` 명령 출력을 텍스트 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-112">Use the `Out-File` cmdlet, which sends command output to a text file.</span></span>
  <span data-ttu-id="9cab2-113">일반적으로 `Out-File` `Encoding` ,, `Force` `Width` 또는 매개 변수와 같은 매개 변수를 사용 해야 하는 경우 cmdlet을 사용 `NoClobber` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-113">Typically, you use the `Out-File` cmdlet when you need to use its parameters, such as the `Encoding`, `Force`, `Width`, or `NoClobber` parameters.</span></span>

- <span data-ttu-id="9cab2-114">Cmdlet을 사용 하 여 `Tee-Object` 명령 출력을 텍스트 파일로 보내고 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-114">Use the `Tee-Object` cmdlet, which sends command output to a text file and then sends it to the pipeline.</span></span>

- <span data-ttu-id="9cab2-115">PowerShell 리디렉션 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-115">Use the PowerShell redirection operators.</span></span> <span data-ttu-id="9cab2-116">File 대상과 함께 리디렉션 연산자를 사용 하는 것은 추가 매개 변수 없이로 파이프 하는 것과 동일 `Out-File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-116">Using the redirection operator with a file target is functionally equivalent to piping to `Out-File` with no extra parameters.</span></span>

<span data-ttu-id="9cab2-117">스트림에 대 한 자세한 내용은 [about_Output_Streams](about_Output_Streams.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9cab2-117">For more information about streams, see [about_Output_Streams](about_Output_Streams.md).</span></span>

### <a name="redirectable-output-streams"></a><span data-ttu-id="9cab2-118">리디렉션할 때 출력 스트림</span><span class="sxs-lookup"><span data-stu-id="9cab2-118">Redirectable output streams</span></span>

<span data-ttu-id="9cab2-119">PowerShell은 다음 출력 스트림의 리디렉션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-119">PowerShell supports redirection of the following output streams.</span></span>

| <span data-ttu-id="9cab2-120">스트림 #</span><span class="sxs-lookup"><span data-stu-id="9cab2-120">Stream #</span></span> |      <span data-ttu-id="9cab2-121">Description</span><span class="sxs-lookup"><span data-stu-id="9cab2-121">Description</span></span>       | <span data-ttu-id="9cab2-122">에 도입 됨</span><span class="sxs-lookup"><span data-stu-id="9cab2-122">Introduced in</span></span>  |    <span data-ttu-id="9cab2-123">쓰기 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9cab2-123">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="9cab2-124">1</span><span class="sxs-lookup"><span data-stu-id="9cab2-124">1</span></span>        | <span data-ttu-id="9cab2-125">**성공** 스트림</span><span class="sxs-lookup"><span data-stu-id="9cab2-125">**Success** Stream</span></span>     | <span data-ttu-id="9cab2-126">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="9cab2-126">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="9cab2-127">2</span><span class="sxs-lookup"><span data-stu-id="9cab2-127">2</span></span>        | <span data-ttu-id="9cab2-128">**오류** 스트림</span><span class="sxs-lookup"><span data-stu-id="9cab2-128">**Error** Stream</span></span>       | <span data-ttu-id="9cab2-129">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="9cab2-129">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="9cab2-130">3</span><span class="sxs-lookup"><span data-stu-id="9cab2-130">3</span></span>        | <span data-ttu-id="9cab2-131">**경고** 스트림</span><span class="sxs-lookup"><span data-stu-id="9cab2-131">**Warning** Stream</span></span>     | <span data-ttu-id="9cab2-132">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="9cab2-132">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="9cab2-133">4</span><span class="sxs-lookup"><span data-stu-id="9cab2-133">4</span></span>        | <span data-ttu-id="9cab2-134">**자세한 정보** 스트림</span><span class="sxs-lookup"><span data-stu-id="9cab2-134">**Verbose** Stream</span></span>     | <span data-ttu-id="9cab2-135">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="9cab2-135">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="9cab2-136">5</span><span class="sxs-lookup"><span data-stu-id="9cab2-136">5</span></span>        | <span data-ttu-id="9cab2-137">**디버그** 스트림</span><span class="sxs-lookup"><span data-stu-id="9cab2-137">**Debug** Stream</span></span>       | <span data-ttu-id="9cab2-138">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="9cab2-138">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="9cab2-139">6</span><span class="sxs-lookup"><span data-stu-id="9cab2-139">6</span></span>        | <span data-ttu-id="9cab2-140">**정보** 스트림</span><span class="sxs-lookup"><span data-stu-id="9cab2-140">**Information** Stream</span></span> | <span data-ttu-id="9cab2-141">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9cab2-141">PowerShell 5.0</span></span> | `Write-Information` |
| *        | <span data-ttu-id="9cab2-142">모든 스트림</span><span class="sxs-lookup"><span data-stu-id="9cab2-142">All Streams</span></span>            | <span data-ttu-id="9cab2-143">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="9cab2-143">PowerShell 3.0</span></span> |                     |

> [!NOTE]
> <span data-ttu-id="9cab2-144">PowerShell에는 **진행률** 스트림도 있지만 리디렉션을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-144">There is also a **Progress** stream in PowerShell, but it does not support redirection.</span></span>

### <a name="powershell-redirection-operators"></a><span data-ttu-id="9cab2-145">PowerShell 리디렉션 운영자</span><span class="sxs-lookup"><span data-stu-id="9cab2-145">PowerShell redirection operators</span></span>

<span data-ttu-id="9cab2-146">PowerShell 리디렉션 연산자는 다음과 같습니다. 여기서은 `n` 스트림 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-146">The PowerShell redirection operators are as follows, where `n` represents the stream number.</span></span> <span data-ttu-id="9cab2-147">스트림이 지정 되지 않은 경우 **성공** 스트림 ( `1` )이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-147">The **Success** stream ( `1` ) is the default if no stream is specified.</span></span>

| <span data-ttu-id="9cab2-148">연산자</span><span class="sxs-lookup"><span data-stu-id="9cab2-148">Operator</span></span> |                         <span data-ttu-id="9cab2-149">Description</span><span class="sxs-lookup"><span data-stu-id="9cab2-149">Description</span></span>                         | <span data-ttu-id="9cab2-150">구문</span><span class="sxs-lookup"><span data-stu-id="9cab2-150">Syntax</span></span> |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | <span data-ttu-id="9cab2-151">지정 된 스트림을 파일에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-151">Send specified stream to a file.</span></span>                            | `n>`   |
| `>>`     | <span data-ttu-id="9cab2-152">지정 된 스트림을 파일에 **추가** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-152">**Append** specified stream to a file.</span></span>                      | `n>>`  |
| `>&1`    | <span data-ttu-id="9cab2-153">지정 된 스트림을 **성공** 스트림으로 _리디렉션합니다_ .</span><span class="sxs-lookup"><span data-stu-id="9cab2-153">_Redirects_ the specified stream to the **Success** stream.</span></span> | `n>&1` |

> [!NOTE]
> <span data-ttu-id="9cab2-154">일부 Unix 셸과 달리 다른 스트림은 **성공** 스트림으로만 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-154">Unlike some Unix shells, you can only redirect other streams to the **Success** stream.</span></span>

## <a name="examples"></a><span data-ttu-id="9cab2-155">예</span><span class="sxs-lookup"><span data-stu-id="9cab2-155">Examples</span></span>

### <a name="example-1-redirect-errors-and-output-to-a-file"></a><span data-ttu-id="9cab2-156">예제 1: 오류 및 출력을 파일로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="9cab2-156">Example 1: Redirect errors and output to a file</span></span>

<span data-ttu-id="9cab2-157">이 예제는 `dir` 성공 하는 한 항목 및 오류가 발생 한 항목에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-157">This example runs `dir` on one item that will succeed, and one that will error.</span></span>

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

<span data-ttu-id="9cab2-158">를 사용 `2>&1` 하 여 **오류** 스트림을 **성공** 스트림으로 리디렉션하고 `>` 결과 **성공** 스트림을 라는 파일로 보냅니다. `dir.log`</span><span class="sxs-lookup"><span data-stu-id="9cab2-158">It uses `2>&1` to redirect the **Error** stream to the **Success** stream, and `>` to send the resultant **Success** stream to a file called `dir.log`</span></span>

### <a name="example-2-send-all-success-stream-data-to-a-file"></a><span data-ttu-id="9cab2-159">예제 2: 모든 성공 스트림 데이터를 파일로 보내기</span><span class="sxs-lookup"><span data-stu-id="9cab2-159">Example 2: Send all Success stream data to a file</span></span>

<span data-ttu-id="9cab2-160">이 예에서는 라는 파일에 모든 **성공** 스트림 데이터를 보냅니다 `script.log` .</span><span class="sxs-lookup"><span data-stu-id="9cab2-160">This example sends all **Success** stream data to a file called `script.log`.</span></span>

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a><span data-ttu-id="9cab2-161">예 3: 파일에 성공, 경고 및 오류 스트림 보내기</span><span class="sxs-lookup"><span data-stu-id="9cab2-161">Example 3: Send Success, Warning, and Error streams to a file</span></span>

<span data-ttu-id="9cab2-162">이 예에서는 리디렉션 연산자를 결합 하 여 원하는 결과를 얻을 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-162">This example shows how you can combine redirection operators to achieve a desired result.</span></span>

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > P:\Temp\redirection.log
```

- <span data-ttu-id="9cab2-163">`3>&1`**경고** 스트림을 **성공** 스트림으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-163">`3>&1` redirects the **Warning** stream to the **Success** stream.</span></span>
- <span data-ttu-id="9cab2-164">`2>&1`**오류** 스트림을 **성공** 스트림으로 리디렉션합니다 (이제 모든 **경고** 스트림 데이터를 포함).</span><span class="sxs-lookup"><span data-stu-id="9cab2-164">`2>&1` redirects the **Error** stream to the **Success** stream (which also now includes all **Warning** stream data)</span></span>
- <span data-ttu-id="9cab2-165">`>`**성공** 스트림 (이제 **경고** 및 **오류** 스트림 모두 `C:\temp\redirection.log` 포함)을 라는 파일로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-165">`>` redirects the **Success** stream (which now contains both **Warning** and **Error** streams) to a file called `C:\temp\redirection.log`)</span></span>

### <a name="example-4-redirect-all-streams-to-a-file"></a><span data-ttu-id="9cab2-166">예제 4: 모든 스트림을 파일로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="9cab2-166">Example 4: Redirect all streams to a file</span></span>

<span data-ttu-id="9cab2-167">이 예제에서는 라는 스크립트의 모든 스트림 출력 `script.ps1` 을 이라는 파일로 보냅니다. `script.log`</span><span class="sxs-lookup"><span data-stu-id="9cab2-167">This example sends all streams output from a script called `script.ps1` to a file called `script.log`</span></span>

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a><span data-ttu-id="9cab2-168">예 5: 모든 Write-Host 및 정보 스트림 데이터 표시 안 함</span><span class="sxs-lookup"><span data-stu-id="9cab2-168">Example 5: Suppress all Write-Host and Information stream data</span></span>

<span data-ttu-id="9cab2-169">이 예에서는 모든 정보 스트림 데이터를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-169">This example suppresses all information stream data.</span></span> <span data-ttu-id="9cab2-170">**정보** 스트림 cmdlet에 대 한 자세한 내용은 [쓰기-호스트](xref:Microsoft.PowerShell.Utility.Write-Host) 및 [쓰기 정보](xref:Microsoft.PowerShell.Utility.Write-Information) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9cab2-170">To read more about **Information** stream cmdlets, see [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) and [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)</span></span>

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a><span data-ttu-id="9cab2-171">예 6: 작업 기본 설정의 효과 표시</span><span class="sxs-lookup"><span data-stu-id="9cab2-171">Example 6: Show the effect of Action Preferences</span></span>

<span data-ttu-id="9cab2-172">작업 기본 설정 변수 및 매개 변수는 특정 스트림에 기록 되는 내용을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-172">Action Preference variables and parameters can change what gets written to a particular stream.</span></span> <span data-ttu-id="9cab2-173">이 예제의 스크립트는의 값이 `$ErrorActionPreference` **오류** 스트림에 쓰여지는 항목에 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-173">The script in this example shows how the value of `$ErrorActionPreference` affects what gets written to the **Error** stream.</span></span>

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

<span data-ttu-id="9cab2-174">이 스크립트를 실행 하면 `$ErrorActionPreference` 가로 설정 된 경우 메시지가 표시 됩니다 `Inquire` .</span><span class="sxs-lookup"><span data-stu-id="9cab2-174">When we run this script we get prompted when `$ErrorActionPreference` is set to `Inquire`.</span></span>

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

<span data-ttu-id="9cab2-175">로그 파일을 검토 하면 다음이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-175">When we examine the log file we see the following:</span></span>

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a><span data-ttu-id="9cab2-176">메모</span><span class="sxs-lookup"><span data-stu-id="9cab2-176">Notes</span></span>

<span data-ttu-id="9cab2-177">데이터를 추가 하지 않는 리디렉션 연산자 ( `>` 및 `n>` )는 지정 된 파일의 현재 내용을 경고 없이 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-177">The redirection operators that do not append data (`>` and `n>`) overwrite the current contents of the specified file without warning.</span></span>

<span data-ttu-id="9cab2-178">그러나 파일이 읽기 전용, 숨김 또는 시스템 파일인 경우 리디렉션이 **실패** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-178">However, if the file is a read-only, hidden, or system file, the redirection **fails**.</span></span> <span data-ttu-id="9cab2-179">추가 리디렉션 연산자 ( `>>` 및 `n>>` )는 읽기 전용 파일에 쓰지 않지만 시스템이 나 숨겨진 파일에는 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-179">The append redirection operators (`>>` and `n>>`) do not write to a read-only file, but they append content to a system or hidden file.</span></span>

<span data-ttu-id="9cab2-180">콘텐츠를 읽기 전용, 숨김 또는 시스템 파일로 강제로 리디렉션할 수 있도록 하려면 cmdlet에 매개 변수를 사용 `Out-File` `Force` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-180">To force the redirection of content to a read-only, hidden, or system file, use the `Out-File` cmdlet with its `Force` parameter.</span></span>

<span data-ttu-id="9cab2-181">파일에 쓰는 경우 리디렉션 연산자는 `UTF8NoBOM` 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-181">When you are writing to files, the redirection operators use `UTF8NoBOM` encoding.</span></span> <span data-ttu-id="9cab2-182">파일의 인코딩이 다른 경우 출력의 형식이 잘못 된 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-182">If the file has a different encoding, the output might not be formatted correctly.</span></span> <span data-ttu-id="9cab2-183">다른 인코딩을 사용 하 여 파일에 쓰려면 `Out-File` cmdlet에 매개 변수를 사용 `Encoding` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-183">To write to files with a different encoding, use the `Out-File` cmdlet with its `Encoding` parameter.</span></span>

### <a name="potential-confusion-with-comparison-operators"></a><span data-ttu-id="9cab2-184">비교 연산자와 혼동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-184">Potential confusion with comparison operators</span></span>

<span data-ttu-id="9cab2-185">`>`연산자는 [보다 큼](about_Comparison_Operators.md#-gt) 비교 연산자와 혼동 하지 않습니다 (종종 `>` 다른 프로그래밍 언어에서로 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="9cab2-185">The `>` operator is not to be confused with the [Greater-than](about_Comparison_Operators.md#-gt) comparison operator (often denoted as `>` in other programming languages).</span></span>

<span data-ttu-id="9cab2-186">비교 되는 개체에 따라를 사용 하는 출력은 `>` 올바른 것으로 표시 될 수 있습니다 (36가 42 보다 크지 않기 때문).</span><span class="sxs-lookup"><span data-stu-id="9cab2-186">Depending on the objects being compared, the output using `>` can appear to be correct (because 36 is not greater than 42).</span></span>

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

<span data-ttu-id="9cab2-187">그러나 로컬 파일 시스템에 대 한 검사를 통해 라는 파일을 기록 하는 내용을 확인할 수 있습니다 `42` `36` .</span><span class="sxs-lookup"><span data-stu-id="9cab2-187">However, a check of the local filesystem can see that a file called `42` was written, with the contents `36`.</span></span>

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

<span data-ttu-id="9cab2-188">역방향 비교 `<` (보다 작음)를 사용 하려고 하면 시스템 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-188">Attempting to use the reverse comparison `<` (less than), yields a system error:</span></span>

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : RedirectionNotSupported
```

<span data-ttu-id="9cab2-189">숫자 비교가 필요한 작업 인 경우에 `-lt` 는를 `-gt` 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cab2-189">If numeric comparison is the required operation, `-lt` and `-gt` should be used.</span></span> <span data-ttu-id="9cab2-190">참조: [ `-gt` 비교 연산자](about_Comparison_Operators.md#-gt)</span><span class="sxs-lookup"><span data-stu-id="9cab2-190">See: [`-gt` Comparison Operator](about_Comparison_Operators.md#-gt)</span></span>

## <a name="see-also"></a><span data-ttu-id="9cab2-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9cab2-191">See also</span></span>

- [<span data-ttu-id="9cab2-192">Out-File</span><span class="sxs-lookup"><span data-stu-id="9cab2-192">Out-File</span></span>](xref:Microsoft.PowerShell.Utility.Out-File)
- [<span data-ttu-id="9cab2-193">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="9cab2-193">Tee-Object</span></span>](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [<span data-ttu-id="9cab2-194">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="9cab2-194">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="9cab2-195">쓰기 오류</span><span class="sxs-lookup"><span data-stu-id="9cab2-195">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="9cab2-196">Write-Host</span><span class="sxs-lookup"><span data-stu-id="9cab2-196">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="9cab2-197">Write-Information</span><span class="sxs-lookup"><span data-stu-id="9cab2-197">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="9cab2-198">Write-Output</span><span class="sxs-lookup"><span data-stu-id="9cab2-198">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="9cab2-199">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="9cab2-199">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="9cab2-200">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="9cab2-200">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="9cab2-201">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="9cab2-201">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="9cab2-202">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="9cab2-202">about_Output_Streams</span></span>](about_Output_Streams.md)
- [<span data-ttu-id="9cab2-203">about_Operators</span><span class="sxs-lookup"><span data-stu-id="9cab2-203">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="9cab2-204">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="9cab2-204">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="9cab2-205">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="9cab2-205">about_Path_Syntax</span></span>](about_Path_Syntax.md)
