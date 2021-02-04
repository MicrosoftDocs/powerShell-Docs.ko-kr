---
description: PowerShell에서 텍스트 파일로 출력을 리디렉션하는 방법에 대해 설명 합니다.
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 85b719b7af11cce2396e7d62fcc638007b55c834
ms.sourcegitcommit: b9826dcf402db8a2b6d3eab37edb82c6af113343
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040901"
---
# <a name="about-redirection"></a><span data-ttu-id="35f93-103">리디렉션 정보</span><span class="sxs-lookup"><span data-stu-id="35f93-103">About Redirection</span></span>

## <a name="short-description"></a><span data-ttu-id="35f93-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="35f93-104">Short description</span></span>
<span data-ttu-id="35f93-105">PowerShell에서 텍스트 파일로 출력을 리디렉션하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-105">Explains how to redirect output from PowerShell to text files.</span></span>

## <a name="long-description"></a><span data-ttu-id="35f93-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-106">Long description</span></span>

<span data-ttu-id="35f93-107">기본적으로 PowerShell은 출력을 PowerShell 호스트로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-107">By default, PowerShell sends output to the PowerShell host.</span></span> <span data-ttu-id="35f93-108">일반적으로 콘솔 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-108">Usually this is the console application.</span></span> <span data-ttu-id="35f93-109">그러나 출력을 텍스트 파일로 보낼 수 있으며, 오류 출력을 일반 출력 스트림으로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-109">However, you can direct the output to a text file, and you can redirect error output to the regular output stream.</span></span>

<span data-ttu-id="35f93-110">다음 메서드를 사용 하 여 출력을 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-110">You can use the following methods to redirect output:</span></span>

- <span data-ttu-id="35f93-111">Cmdlet을 사용 하 여 `Out-File` 명령 출력을 텍스트 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-111">Use the `Out-File` cmdlet, which sends command output to a text file.</span></span>
  <span data-ttu-id="35f93-112">일반적으로 `Out-File` `Encoding` ,, `Force` `Width` 또는 매개 변수와 같은 매개 변수를 사용 해야 하는 경우 cmdlet을 사용 `NoClobber` 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-112">Typically, you use the `Out-File` cmdlet when you need to use its parameters, such as the `Encoding`, `Force`, `Width`, or `NoClobber` parameters.</span></span>

- <span data-ttu-id="35f93-113">Cmdlet을 사용 하 여 `Tee-Object` 명령 출력을 텍스트 파일로 보내고 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-113">Use the `Tee-Object` cmdlet, which sends command output to a text file and then sends it to the pipeline.</span></span>

- <span data-ttu-id="35f93-114">PowerShell 리디렉션 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-114">Use the PowerShell redirection operators.</span></span> <span data-ttu-id="35f93-115">File 대상과 함께 리디렉션 연산자를 사용 하는 것은 추가 매개 변수 없이로 파이프 하는 것과 동일 `Out-File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-115">Using the redirection operator with a file target is functionally equivalent to piping to `Out-File` with no extra parameters.</span></span>

<span data-ttu-id="35f93-116">스트림에 대 한 자세한 내용은 [about_Output_Streams](about_Output_Streams.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35f93-116">For more information about streams, see [about_Output_Streams](about_Output_Streams.md).</span></span>

### <a name="redirectable-output-streams"></a><span data-ttu-id="35f93-117">리디렉션할 때 출력 스트림</span><span class="sxs-lookup"><span data-stu-id="35f93-117">Redirectable output streams</span></span>

<span data-ttu-id="35f93-118">PowerShell은 다음 출력 스트림의 리디렉션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-118">PowerShell supports redirection of the following output streams.</span></span>

| <span data-ttu-id="35f93-119">스트림 #</span><span class="sxs-lookup"><span data-stu-id="35f93-119">Stream #</span></span> |      <span data-ttu-id="35f93-120">설명</span><span class="sxs-lookup"><span data-stu-id="35f93-120">Description</span></span>       | <span data-ttu-id="35f93-121">에 도입 됨</span><span class="sxs-lookup"><span data-stu-id="35f93-121">Introduced in</span></span>  |    <span data-ttu-id="35f93-122">쓰기 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35f93-122">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="35f93-123">1</span><span class="sxs-lookup"><span data-stu-id="35f93-123">1</span></span>        | <span data-ttu-id="35f93-124">**성공** 스트림</span><span class="sxs-lookup"><span data-stu-id="35f93-124">**Success** Stream</span></span>     | <span data-ttu-id="35f93-125">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="35f93-125">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="35f93-126">2</span><span class="sxs-lookup"><span data-stu-id="35f93-126">2</span></span>        | <span data-ttu-id="35f93-127">**오류** 스트림</span><span class="sxs-lookup"><span data-stu-id="35f93-127">**Error** Stream</span></span>       | <span data-ttu-id="35f93-128">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="35f93-128">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="35f93-129">3</span><span class="sxs-lookup"><span data-stu-id="35f93-129">3</span></span>        | <span data-ttu-id="35f93-130">**경고** 스트림</span><span class="sxs-lookup"><span data-stu-id="35f93-130">**Warning** Stream</span></span>     | <span data-ttu-id="35f93-131">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="35f93-131">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="35f93-132">4</span><span class="sxs-lookup"><span data-stu-id="35f93-132">4</span></span>        | <span data-ttu-id="35f93-133">**자세한 정보** 스트림</span><span class="sxs-lookup"><span data-stu-id="35f93-133">**Verbose** Stream</span></span>     | <span data-ttu-id="35f93-134">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="35f93-134">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="35f93-135">5</span><span class="sxs-lookup"><span data-stu-id="35f93-135">5</span></span>        | <span data-ttu-id="35f93-136">**디버그** 스트림</span><span class="sxs-lookup"><span data-stu-id="35f93-136">**Debug** Stream</span></span>       | <span data-ttu-id="35f93-137">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="35f93-137">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="35f93-138">6</span><span class="sxs-lookup"><span data-stu-id="35f93-138">6</span></span>        | <span data-ttu-id="35f93-139">**정보** 스트림</span><span class="sxs-lookup"><span data-stu-id="35f93-139">**Information** Stream</span></span> | <span data-ttu-id="35f93-140">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="35f93-140">PowerShell 5.0</span></span> | `Write-Information` |
| *        | <span data-ttu-id="35f93-141">모든 스트림</span><span class="sxs-lookup"><span data-stu-id="35f93-141">All Streams</span></span>            | <span data-ttu-id="35f93-142">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="35f93-142">PowerShell 3.0</span></span> |                     |

> [!NOTE]
> <span data-ttu-id="35f93-143">PowerShell에는 **진행률** 스트림도 있지만 리디렉션을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-143">There is also a **Progress** stream in PowerShell, but it does not support redirection.</span></span>

### <a name="powershell-redirection-operators"></a><span data-ttu-id="35f93-144">PowerShell 리디렉션 운영자</span><span class="sxs-lookup"><span data-stu-id="35f93-144">PowerShell redirection operators</span></span>

<span data-ttu-id="35f93-145">PowerShell 리디렉션 연산자는 다음과 같습니다. 여기서은 `n` 스트림 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-145">The PowerShell redirection operators are as follows, where `n` represents the stream number.</span></span> <span data-ttu-id="35f93-146">스트림이 지정 되지 않은 경우 **성공** 스트림 ( `1` )이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-146">The **Success** stream ( `1` ) is the default if no stream is specified.</span></span>

| <span data-ttu-id="35f93-147">연산자</span><span class="sxs-lookup"><span data-stu-id="35f93-147">Operator</span></span> |                         <span data-ttu-id="35f93-148">설명</span><span class="sxs-lookup"><span data-stu-id="35f93-148">Description</span></span>                         | <span data-ttu-id="35f93-149">Syntax</span><span class="sxs-lookup"><span data-stu-id="35f93-149">Syntax</span></span> |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | <span data-ttu-id="35f93-150">지정 된 스트림을 파일에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-150">Send specified stream to a file.</span></span>                            | `n>`   |
| `>>`     | <span data-ttu-id="35f93-151">지정 된 스트림을 파일에 **추가** 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-151">**Append** specified stream to a file.</span></span>                      | `n>>`  |
| `>&1`    | <span data-ttu-id="35f93-152">지정 된 스트림을 **성공** 스트림으로 _리디렉션합니다_ .</span><span class="sxs-lookup"><span data-stu-id="35f93-152">_Redirects_ the specified stream to the **Success** stream.</span></span> | `n>&1` |

> [!NOTE]
> <span data-ttu-id="35f93-153">일부 Unix 셸과 달리 다른 스트림은 **성공** 스트림으로만 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-153">Unlike some Unix shells, you can only redirect other streams to the **Success** stream.</span></span>

## <a name="examples"></a><span data-ttu-id="35f93-154">예제</span><span class="sxs-lookup"><span data-stu-id="35f93-154">Examples</span></span>

### <a name="example-1-redirect-errors-and-output-to-a-file"></a><span data-ttu-id="35f93-155">예제 1: 오류 및 출력을 파일로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="35f93-155">Example 1: Redirect errors and output to a file</span></span>

<span data-ttu-id="35f93-156">이 예제는 `dir` 성공 하는 한 항목 및 오류가 발생 한 항목에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-156">This example runs `dir` on one item that will succeed, and one that will error.</span></span>

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

<span data-ttu-id="35f93-157">를 사용 `2>&1` 하 여 **오류** 스트림을 **성공** 스트림으로 리디렉션하고 `>` 결과 **성공** 스트림을 라는 파일로 보냅니다. `dir.log`</span><span class="sxs-lookup"><span data-stu-id="35f93-157">It uses `2>&1` to redirect the **Error** stream to the **Success** stream, and `>` to send the resultant **Success** stream to a file called `dir.log`</span></span>

### <a name="example-2-send-all-success-stream-data-to-a-file"></a><span data-ttu-id="35f93-158">예제 2: 모든 성공 스트림 데이터를 파일로 보내기</span><span class="sxs-lookup"><span data-stu-id="35f93-158">Example 2: Send all Success stream data to a file</span></span>

<span data-ttu-id="35f93-159">이 예에서는 라는 파일에 모든 **성공** 스트림 데이터를 보냅니다 `script.log` .</span><span class="sxs-lookup"><span data-stu-id="35f93-159">This example sends all **Success** stream data to a file called `script.log`.</span></span>

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a><span data-ttu-id="35f93-160">예 3: 파일에 성공, 경고 및 오류 스트림 보내기</span><span class="sxs-lookup"><span data-stu-id="35f93-160">Example 3: Send Success, Warning, and Error streams to a file</span></span>

<span data-ttu-id="35f93-161">이 예에서는 리디렉션 연산자를 결합 하 여 원하는 결과를 얻을 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-161">This example shows how you can combine redirection operators to achieve a desired result.</span></span>

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > C:\Temp\redirection.log
```

- <span data-ttu-id="35f93-162">`3>&1`**경고** 스트림을 **성공** 스트림으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-162">`3>&1` redirects the **Warning** stream to the **Success** stream.</span></span>
- <span data-ttu-id="35f93-163">`2>&1`**오류** 스트림을 **성공** 스트림으로 리디렉션합니다 (이제 모든 **경고** 스트림 데이터를 포함).</span><span class="sxs-lookup"><span data-stu-id="35f93-163">`2>&1` redirects the **Error** stream to the **Success** stream (which also now includes all **Warning** stream data)</span></span>
- <span data-ttu-id="35f93-164">`>`**성공** 스트림 (이제 **경고** 및 **오류** 스트림 모두 `C:\temp\redirection.log` 포함)을 라는 파일로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-164">`>` redirects the **Success** stream (which now contains both **Warning** and **Error** streams) to a file called `C:\temp\redirection.log`)</span></span>

### <a name="example-4-redirect-all-streams-to-a-file"></a><span data-ttu-id="35f93-165">예제 4: 모든 스트림을 파일로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="35f93-165">Example 4: Redirect all streams to a file</span></span>

<span data-ttu-id="35f93-166">이 예제에서는 라는 스크립트의 모든 스트림 출력 `script.ps1` 을 이라는 파일로 보냅니다. `script.log`</span><span class="sxs-lookup"><span data-stu-id="35f93-166">This example sends all streams output from a script called `script.ps1` to a file called `script.log`</span></span>

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a><span data-ttu-id="35f93-167">예 5: 모든 Write-Host 및 정보 스트림 데이터 표시 안 함</span><span class="sxs-lookup"><span data-stu-id="35f93-167">Example 5: Suppress all Write-Host and Information stream data</span></span>

<span data-ttu-id="35f93-168">이 예에서는 모든 정보 스트림 데이터를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-168">This example suppresses all information stream data.</span></span> <span data-ttu-id="35f93-169">**정보** 스트림 cmdlet에 대 한 자세한 내용은 [쓰기-호스트](xref:Microsoft.PowerShell.Utility.Write-Host) 및 [쓰기 정보](xref:Microsoft.PowerShell.Utility.Write-Information) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35f93-169">To read more about **Information** stream cmdlets, see [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) and [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)</span></span>

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a><span data-ttu-id="35f93-170">예 6: 작업 기본 설정의 효과 표시</span><span class="sxs-lookup"><span data-stu-id="35f93-170">Example 6: Show the effect of Action Preferences</span></span>

<span data-ttu-id="35f93-171">작업 기본 설정 변수 및 매개 변수는 특정 스트림에 기록 되는 내용을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-171">Action Preference variables and parameters can change what gets written to a particular stream.</span></span> <span data-ttu-id="35f93-172">이 예제의 스크립트는의 값이 `$ErrorActionPreference` **오류** 스트림에 쓰여지는 항목에 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-172">The script in this example shows how the value of `$ErrorActionPreference` affects what gets written to the **Error** stream.</span></span>

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

<span data-ttu-id="35f93-173">이 스크립트를 실행 하면 `$ErrorActionPreference` 가로 설정 된 경우 메시지가 표시 됩니다 `Inquire` .</span><span class="sxs-lookup"><span data-stu-id="35f93-173">When we run this script we get prompted when `$ErrorActionPreference` is set to `Inquire`.</span></span>

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

<span data-ttu-id="35f93-174">로그 파일을 검토 하면 다음이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-174">When we examine the log file we see the following:</span></span>

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

## <a name="notes"></a><span data-ttu-id="35f93-175">참고</span><span class="sxs-lookup"><span data-stu-id="35f93-175">Notes</span></span>

<span data-ttu-id="35f93-176">데이터를 추가 하지 않는 리디렉션 연산자 ( `>` 및 `n>` )는 지정 된 파일의 현재 내용을 경고 없이 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-176">The redirection operators that do not append data (`>` and `n>`) overwrite the current contents of the specified file without warning.</span></span>

<span data-ttu-id="35f93-177">그러나 파일이 읽기 전용, 숨김 또는 시스템 파일인 경우 리디렉션이 **실패** 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-177">However, if the file is a read-only, hidden, or system file, the redirection **fails**.</span></span> <span data-ttu-id="35f93-178">추가 리디렉션 연산자 ( `>>` 및 `n>>` )는 읽기 전용 파일에 쓰지 않지만 시스템이 나 숨겨진 파일에는 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-178">The append redirection operators (`>>` and `n>>`) do not write to a read-only file, but they append content to a system or hidden file.</span></span>

<span data-ttu-id="35f93-179">콘텐츠를 읽기 전용, 숨김 또는 시스템 파일로 강제로 리디렉션할 수 있도록 하려면 cmdlet에 매개 변수를 사용 `Out-File` `Force` 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-179">To force the redirection of content to a read-only, hidden, or system file, use the `Out-File` cmdlet with its `Force` parameter.</span></span>

<span data-ttu-id="35f93-180">파일에 쓰는 경우 리디렉션 연산자는 `UTF8NoBOM` 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-180">When you are writing to files, the redirection operators use `UTF8NoBOM` encoding.</span></span> <span data-ttu-id="35f93-181">파일의 인코딩이 다른 경우 출력의 형식이 잘못 된 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-181">If the file has a different encoding, the output might not be formatted correctly.</span></span> <span data-ttu-id="35f93-182">다른 인코딩을 사용 하 여 파일에 쓰려면 `Out-File` cmdlet에 매개 변수를 사용 `Encoding` 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-182">To write to files with a different encoding, use the `Out-File` cmdlet with its `Encoding` parameter.</span></span>

### <a name="potential-confusion-with-comparison-operators"></a><span data-ttu-id="35f93-183">비교 연산자와 혼동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-183">Potential confusion with comparison operators</span></span>

<span data-ttu-id="35f93-184">`>`연산자는 [보다 큼](about_Comparison_Operators.md#-gt--ge--lt-and--le) 비교 연산자와 혼동 하지 않습니다 (종종 `>` 다른 프로그래밍 언어에서로 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="35f93-184">The `>` operator is not to be confused with the [Greater-than](about_Comparison_Operators.md#-gt--ge--lt-and--le) comparison operator (often denoted as `>` in other programming languages).</span></span>

<span data-ttu-id="35f93-185">비교 되는 개체에 따라를 사용 하는 출력은 `>` 올바른 것으로 표시 될 수 있습니다 (36가 42 보다 크지 않기 때문).</span><span class="sxs-lookup"><span data-stu-id="35f93-185">Depending on the objects being compared, the output using `>` can appear to be correct (because 36 is not greater than 42).</span></span>

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

<span data-ttu-id="35f93-186">그러나 로컬 파일 시스템에 대 한 검사를 통해 라는 파일을 기록 하는 내용을 확인할 수 있습니다 `42` `36` .</span><span class="sxs-lookup"><span data-stu-id="35f93-186">However, a check of the local filesystem can see that a file called `42` was written, with the contents `36`.</span></span>

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

<span data-ttu-id="35f93-187">역방향 비교 `<` (보다 작음)를 사용 하려고 하면 시스템 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-187">Attempting to use the reverse comparison `<` (less than), yields a system error:</span></span>

```powershell
PS> if (36 < 42) { "true" } else { "false" }
ParserError:
Line |
   1 |  if (36 < 42) { "true" } else { "false" }
     |         ~
     | The '<' operator is reserved for future use.
```

<span data-ttu-id="35f93-188">숫자 비교가 필요한 작업 인 경우에 `-lt` 는를 `-gt` 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f93-188">If numeric comparison is the required operation, `-lt` and `-gt` should be used.</span></span> <span data-ttu-id="35f93-189">자세한 내용은 `-gt` [about_Comparison_Operators](about_Comparison_Operators.md#-gt--ge--lt-and--le)의 연산자를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35f93-189">For more information, see the `-gt` operator in [about_Comparison_Operators](about_Comparison_Operators.md#-gt--ge--lt-and--le).</span></span>

## <a name="see-also"></a><span data-ttu-id="35f93-190">참조</span><span class="sxs-lookup"><span data-stu-id="35f93-190">See also</span></span>

- [<span data-ttu-id="35f93-191">Out-File</span><span class="sxs-lookup"><span data-stu-id="35f93-191">Out-File</span></span>](xref:Microsoft.PowerShell.Utility.Out-File)
- [<span data-ttu-id="35f93-192">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="35f93-192">Tee-Object</span></span>](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [<span data-ttu-id="35f93-193">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="35f93-193">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="35f93-194">Write-Error</span><span class="sxs-lookup"><span data-stu-id="35f93-194">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="35f93-195">Write-Host</span><span class="sxs-lookup"><span data-stu-id="35f93-195">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="35f93-196">Write-Information</span><span class="sxs-lookup"><span data-stu-id="35f93-196">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="35f93-197">Write-Output</span><span class="sxs-lookup"><span data-stu-id="35f93-197">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="35f93-198">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="35f93-198">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="35f93-199">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="35f93-199">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="35f93-200">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="35f93-200">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="35f93-201">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="35f93-201">about_Output_Streams</span></span>](about_Output_Streams.md)
- [<span data-ttu-id="35f93-202">about_Operators</span><span class="sxs-lookup"><span data-stu-id="35f93-202">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="35f93-203">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="35f93-203">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="35f93-204">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="35f93-204">about_Path_Syntax</span></span>](about_Path_Syntax.md)
