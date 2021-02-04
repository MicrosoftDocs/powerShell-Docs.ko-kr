---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 1b1824db5c5c20698d551a6277890ce6c82c4e11
ms.sourcegitcommit: fb9bafd041e3615b9dc9fb77c9245581b705cd02
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725190"
---
# <span data-ttu-id="7a49e-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="7a49e-103">ForEach-Object</span></span>

## <span data-ttu-id="7a49e-104">개요</span><span class="sxs-lookup"><span data-stu-id="7a49e-104">Synopsis</span></span>
<span data-ttu-id="7a49e-105">입력 개체 컬렉션에 있는 각 항목에 대해 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="7a49e-106">구문</span><span class="sxs-lookup"><span data-stu-id="7a49e-106">Syntax</span></span>

### <span data-ttu-id="7a49e-107">ScriptBlockSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="7a49e-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7a49e-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="7a49e-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7a49e-109">ParallelParameterSet</span><span class="sxs-lookup"><span data-stu-id="7a49e-109">ParallelParameterSet</span></span>

```
ForEach-Object -Parallel <scriptblock> [-InputObject <PSObject>] [-ThrottleLimit <int>]
[-UseNewRunspace] [-TimeoutSeconds <int>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7a49e-110">설명</span><span class="sxs-lookup"><span data-stu-id="7a49e-110">Description</span></span>

<span data-ttu-id="7a49e-111">`ForEach-Object`Cmdlet은 입력 개체 컬렉션의 각 항목에 대해 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-111">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="7a49e-112">입력 개체를 cmdlet으로 파이프 하거나 **InputObject** 매개 변수를 사용 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-112">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="7a49e-113">Windows PowerShell 3.0부터 명령을 생성 하는 방법에는 두 가지가 있습니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-113">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="7a49e-114">**스크립트 블록** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-114">**Script block**.</span></span> <span data-ttu-id="7a49e-115">스크립트 블록을 사용하여 작업을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-115">You can use a script block to specify the operation.</span></span> <span data-ttu-id="7a49e-116">스크립트 블록 내에서 변수를 사용 `$_` 하 여 현재 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-116">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="7a49e-117">스크립트 블록은 **Process** 매개 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-117">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="7a49e-118">스크립트 블록에는 모든 PowerShell 스크립트가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-118">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="7a49e-119">예를 들어 다음 명령은 컴퓨터에 있는 각 프로세스의 **ProcessName** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-119">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="7a49e-120">`ForEach-Object``begin` `process` `end` [about_functions](about/about_functions.md#piping-objects-to-functions)에 설명 된 대로, 및 블록을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-120">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="7a49e-121">스크립트 블록은 호출자의 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-121">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="7a49e-122">따라서 블록은 해당 범위의 변수에 액세스할 수 있으며 cmdlet이 완료 된 후 해당 범위에 유지 되는 새 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-122">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="7a49e-123">**Operation 문**.</span><span class="sxs-lookup"><span data-stu-id="7a49e-123">**Operation statement**.</span></span> <span data-ttu-id="7a49e-124">자연어와 유사한 작업 문을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-124">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="7a49e-125">작업 문을 사용하여 속성 값을 지정하거나 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-125">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="7a49e-126">작업 문은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-126">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="7a49e-127">예를 들어 다음 명령도 컴퓨터에 있는 각 프로세스의 **ProcessName** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-127">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

- <span data-ttu-id="7a49e-128">**병렬 실행 스크립트 블록** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-128">**Parallel running script block**.</span></span> <span data-ttu-id="7a49e-129">PowerShell 7.0부터 각 스크립트 블록을 병렬로 실행 하는 세 번째 매개 변수 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-129">Beginning with PowerShell 7.0, a third parameter set is available that runs each script block in parallel.</span></span> <span data-ttu-id="7a49e-130">**ThrottleLimit** 매개 변수는 한 번에 실행 되는 병렬 스크립트의 수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-130">The **ThrottleLimit** parameter limits the number of parallel scripts running at a time.</span></span> <span data-ttu-id="7a49e-131">이전 처럼 변수를 사용 `$_` 하 여 스크립트 블록의 현재 입력 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-131">As before, use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="7a49e-132">키워드를 사용 `$using:` 하 여 실행 중인 스크립트에 변수 참조를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-132">Use the `$using:` keyword to pass variable references to the running script.</span></span>

  <span data-ttu-id="7a49e-133">PowerShell 7에서 최대 격리를 보장 하기 위해 각 루프 반복에 대 한 새 runspace가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-133">In PowerShell 7, a new runspace is created for each loop iteration to ensure maximum isolation.</span></span>
  <span data-ttu-id="7a49e-134">이는 새 runspace를 만드는 것과 비교 하 여 수행 하는 작업의 양이 적거나, 많은 작업이 많은 반복이 발생 하는 경우 성능이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-134">This can be a large performance and resource hit if the work you are doing is small compared to creating new runspaces or if there are a lot of iterations performing significant work.</span></span> <span data-ttu-id="7a49e-135">PowerShell 7.1을 기준으로 runspace 풀에서 runspace는 기본적으로 다시 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-135">As of PowerShell 7.1, runspaces from a runspace pool are reused by default.</span></span> <span data-ttu-id="7a49e-136">Runspace 풀 크기는 **ThrottleLimit** 매개 변수로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-136">The runspace pool size is specified by the **ThrottleLimit** parameter.</span></span> <span data-ttu-id="7a49e-137">기본 runspace 풀 크기는 5입니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-137">The default runspace pool size is 5.</span></span> <span data-ttu-id="7a49e-138">**UseNewRunspace** 스위치를 사용 하 여 각 반복에 대해 새 runspace를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-138">You can still create a new runspace for each iteration using the **UseNewRunspace** switch.</span></span>

  <span data-ttu-id="7a49e-139">기본적으로 병렬 scriptblocks은 병렬 작업을 시작한 호출자의 현재 작업 디렉터리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-139">By default, the parallel scriptblocks use the current working directory of the caller that started the parallel tasks.</span></span>

  <span data-ttu-id="7a49e-140">종료 되지 않는 오류는 scriptblocks를 병렬로 실행 하는 경우에 발생 하므로 cmdlet 오류 스트림에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-140">Non-terminating errors are written to the cmdlet error stream as they occur in parallel running scriptblocks.</span></span> <span data-ttu-id="7a49e-141">병렬 scriptblock 실행 순서를 확인할 수 없기 때문에 오류 스트림에 오류가 표시 되는 순서는 임의적입니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-141">Because parallel scriptblock execution order cannot be determined, the order in which errors appear in the error stream is random.</span></span> <span data-ttu-id="7a49e-142">마찬가지로, 경고, 자세한 정보 표시 또는 정보와 같은 다른 데이터 스트림에 기록 된 메시지는 해당 데이터 스트림에 확정 되지 않은 순서로 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-142">Likewise, messages written to other data streams, like warning, verbose, or information are written to those data streams in an indeterminate order.</span></span>

  <span data-ttu-id="7a49e-143">예외와 같은 종료 오류는 발생 하는 scriptblocks의 개별 병렬 인스턴스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-143">Terminating errors, such as exceptions, terminate the individual parallel instance of the scriptblocks in which they occur.</span></span> <span data-ttu-id="7a49e-144">하나의 scriptblocks에서 종료 오류가 발생 하면 cmdlet이 종료 되지 않을 수 있습니다 `Foreach-Object` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-144">A terminating error in one scriptblocks may not cause the termination of the `Foreach-Object` cmdlet.</span></span> <span data-ttu-id="7a49e-145">동시에 실행 되는 다른 scriptblocks는 종료 오류가 발생 하지 않는 한 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-145">The other scriptblocks, running in parallel, continue to run unless they also encounter a terminating error.</span></span> <span data-ttu-id="7a49e-146">종료 오류는 **FullyQualifiedErrorId** 가 인 **ErrorRecord** 으로 오류 데이터 스트림에 기록 됩니다 `PSTaskException` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-146">The terminating error is written to the error data stream as an **ErrorRecord** with a **FullyQualifiedErrorId** of `PSTaskException`.</span></span>
  <span data-ttu-id="7a49e-147">PowerShell try/catch 또는 트랩 블록을 사용 하 여 종료 오류를 종료 되지 않는 오류로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-147">Terminating errors can be converted to non-terminating errors using PowerShell try/catch or trap blocks.</span></span>

## <span data-ttu-id="7a49e-148">예제</span><span class="sxs-lookup"><span data-stu-id="7a49e-148">Examples</span></span>

### <span data-ttu-id="7a49e-149">예제 1: 배열의 정수 나누기</span><span class="sxs-lookup"><span data-stu-id="7a49e-149">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="7a49e-150">이 예제에서는 세 개의 정수로 이루어진 배열을 사용 하 여 각 정수를 1024으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-150">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="7a49e-151">예 2: 디렉터리에 있는 모든 파일의 길이 가져오기</span><span class="sxs-lookup"><span data-stu-id="7a49e-151">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="7a49e-152">이 예에서는 PowerShell 설치 디렉터리의 파일 및 디렉터리를 처리 `$PSHOME` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-152">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="7a49e-153">개체가 디렉터리가 아닌 경우 스크립트 블록은 파일의 이름을 가져오고, **길이** 속성의 값을 1024로 나누고, 공백 ("")을 추가 하 여 다음 항목과 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-153">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="7a49e-154">이 cmdlet은 **PSISContainer** 속성을 사용 하 여 개체가 디렉터리 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-154">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="7a49e-155">예 3: 최신 시스템 이벤트에 대 한 운영</span><span class="sxs-lookup"><span data-stu-id="7a49e-155">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="7a49e-156">이 예제에서는 시스템 이벤트 로그의 최신 이벤트 1000을 텍스트 파일에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-156">This example writes the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="7a49e-157">현재 시간은 이벤트를 처리 하기 전과 후에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-157">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="7a49e-158">`Get-EventLog` 시스템 이벤트 로그에서 1000 개의 최신 이벤트를 가져와 변수에 저장 합니다 `$Events` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-158">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="7a49e-159">`$Events` 가 cmdlet으로 파이프 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-159">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="7a49e-160">**Begin** 매개 변수는 현재 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-160">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="7a49e-161">그런 다음 **Process** 매개 변수는 cmdlet을 사용 하 여 `Out-File` events.txt 라는 텍스트 파일을 만들고 해당 파일에 있는 각 이벤트의 메시지 속성을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-161">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="7a49e-162">마지막으로, **End** 매개 변수는 모든 처리가 완료된 후 날짜와 시간을 표시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-162">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="7a49e-163">예제 4: 레지스트리 키 값 변경</span><span class="sxs-lookup"><span data-stu-id="7a49e-163">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="7a49e-164">이 예에서는 키 아래의 모든 하위 키에 있는 **RemotePath** 레지스트리 항목의 값을 `HKCU:\Network` 대문자 텍스트로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-164">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="7a49e-165">이 형식을 사용하여 레지스트리 항목 값의 형식이나 내용을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-165">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="7a49e-166">**네트워크** 키의 각 하위 키는 로그온 할 때 다시 연결 되는 매핑된 네트워크 드라이브를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-166">Each subkey in the **Network** key represents a mapped network drive that reconnects at sign on.</span></span> <span data-ttu-id="7a49e-167">**RemotePath** 항목에는 연결된 드라이브의 UNC 경로가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-167">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="7a49e-168">예를 들어 E: 드라이브를에 매핑하면 `\\Server\Share` **e** 하위 키가에 생성 되 `HKCU:\Network` 고 **RemotePath** 레지스트리 값이로 설정 됩니다 `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-168">For example, if you map the E: drive to `\\Server\Share`, an **E** subkey is created in `HKCU:\Network` with the **RemotePath** registry value set to `\\Server\Share`.</span></span>

<span data-ttu-id="7a49e-169">이 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` **네트워크** 키의 모든 하위 키를 가져오고 cmdlet을 사용 하 여 `Set-ItemProperty` 각 키에서 **RemotePath** 레지스트리 항목의 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-169">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="7a49e-170">명령에서 `Set-ItemProperty` 경로는 레지스트리 키의 **PSPath** 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-170">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="7a49e-171">레지스트리 항목이 아니라 레지스트리 키를 나타내는 Microsoft .NET Framework 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-171">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="7a49e-172">이 명령은 문자열 (REG_SZ) 인 **RemotePath** 값의 **ToUpper ()** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-172">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="7a49e-173">`Set-ItemProperty`는 각 키의 속성을 변경 하기 때문에 `ForEach-Object` 속성에 액세스 하려면 cmdlet이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-173">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="7a49e-174">예 5: $Null 자동 변수 사용</span><span class="sxs-lookup"><span data-stu-id="7a49e-174">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="7a49e-175">이 예에서는 `$Null` cmdlet에 자동 변수를 파이프 하는 결과를 보여 줍니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-175">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="7a49e-176">PowerShell은 null을 명시적 자리 표시자로 처리 하기 때문에 `ForEach-Object` 이 cmdlet은 `$Null` 파이프 하는 다른 개체와 마찬가지로에 대 한 값을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-176">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="7a49e-177">예제 6: 속성 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="7a49e-177">Example 6: Get property values</span></span>

<span data-ttu-id="7a49e-178">이 예에서는 cmdlet의 **MemberName** 매개 변수를 사용 하 여 설치 된 모든 PowerShell 모듈의 **Path** 속성 값을 가져옵니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-178">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="7a49e-179">두 번째 명령은 첫 번째 명령과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-179">The second command is equivalent to the first.</span></span> <span data-ttu-id="7a49e-180">`Foreach`Cmdlet의 별칭을 사용 하 `ForEach-Object` 고 **MemberName** 매개 변수 (선택 사항)의 이름을 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-180">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="7a49e-181">Cmdlet은 속성 값 `ForEach-Object` 형식을 변경 하는 **Format** cmdlet 또는 cmdlet과 달리 형식을 변경 하지 않고 값을 가져오기 때문에 속성 값을 가져오는 데 유용 합니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-181">The `ForEach-Object` cmdlet is useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="7a49e-182">예 7: 모듈 이름을 구성 요소 이름으로 분할</span><span class="sxs-lookup"><span data-stu-id="7a49e-182">Example 7: Split module names into component names</span></span>

<span data-ttu-id="7a49e-183">이 예제에서는 점으로 구분 된 두 개의 모듈 이름을 해당 구성 요소 이름으로 분할 하는 세 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-183">This example shows three ways to split two dot-separated module names into their component names.</span></span>

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

<span data-ttu-id="7a49e-184">명령에서 문자열의 **Split** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-184">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="7a49e-185">세 명령은 서로 다른 구문을 사용하지만 동일하며 교환해서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-185">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="7a49e-186">첫 번째 명령은 스크립트 블록과 현재 개체 연산자를 포함 하는 일반적인 구문을 사용 합니다 `$_` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-186">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="7a49e-187">점 구문을 사용하여 메서드를 지정하고 괄호를 사용하여 구분 기호 인수를 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-187">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="7a49e-188">두 번째 명령은 **MemberName** 매개 변수를 사용하여 **Split** 메서드를 지정하고 **ArgumentName** 매개 변수를 사용하여 점(".")을 분할 구분 기호로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-188">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="7a49e-189">세 번째 명령은 cmdlet의 **Foreach** 별칭을 사용 하 `ForEach-Object` 고 **MemberName** 및 **argumentlist** 매개 변수의 이름을 생략 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="7a49e-189">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="7a49e-190">예 8: 두 스크립트 블록을 사용 하 여 ForEach-Object 사용</span><span class="sxs-lookup"><span data-stu-id="7a49e-190">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="7a49e-191">이 예제에서는 메서드에 액세스할 스크립트 블록 두 개를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-191">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="7a49e-192">모든 스크립트 블록은 **Process** 매개 변수에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-192">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="7a49e-193">그러나 **Begin** 및 **Process** 매개 변수에 전달 된 것 처럼 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-193">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="7a49e-194">예제 9: 두 개 이상의 스크립트 블록을 사용 하 여 ForEach-Object 사용</span><span class="sxs-lookup"><span data-stu-id="7a49e-194">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="7a49e-195">이 예제에서는 메서드에 액세스할 스크립트 블록 두 개를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-195">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="7a49e-196">모든 스크립트 블록은 **Process** 매개 변수에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-196">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="7a49e-197">그러나 **Begin**, **Process** 및 **End** 매개 변수에 전달 된 것 처럼 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-197">However, they are treated as if they had been passed to the **Begin**, **Process**, and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> <span data-ttu-id="7a49e-198">첫 번째 스크립트 블록은 항상 블록에 매핑되고 `begin` , 마지막 블록은 블록에 매핑되고 `end` , between의 블록은 모두 블록에 매핑됩니다 `process` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-198">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="7a49e-199">예 10: 각 파이프라인 항목에 대해 여러 스크립트 블록 실행</span><span class="sxs-lookup"><span data-stu-id="7a49e-199">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="7a49e-200">위의 예제와 같이 **Process** 매개 변수를 사용 하 여 전달 된 여러 스크립트 블록은 **Begin** 및 **End** 매개 변수에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-200">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="7a49e-201">이 매핑을 방지 하려면 **Begin** 및 **End** 매개 변수에 대 한 명시적 값을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-201">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

### <span data-ttu-id="7a49e-202">예 11: 병렬 일괄 처리에서 느림 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="7a49e-202">Example 11: Run slow script in parallel batches</span></span>

<span data-ttu-id="7a49e-203">이 예에서는 문자열을 계산 하 고 1 초 동안 대기 하는 간단한 스크립트 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-203">This example runs a simple script block that evaluates a string and sleeps for one second.</span></span>

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

<span data-ttu-id="7a49e-204">**ThrottleLimit** 매개 변수 값은 4로 설정 되므로 입력이 4 개의 일괄 처리로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-204">The **ThrottleLimit** parameter value is set to 4 so that the input is processed in batches of four.</span></span>
<span data-ttu-id="7a49e-205">`$using:`키워드는 `$Message` 각 병렬 스크립트 블록에 변수를 전달 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-205">The `$using:` keyword is used to pass the `$Message` variable into each parallel script block.</span></span>

### <span data-ttu-id="7a49e-206">예 12: 병렬로 로그 항목 검색</span><span class="sxs-lookup"><span data-stu-id="7a49e-206">Example 12: Retrieve log entries in parallel</span></span>

<span data-ttu-id="7a49e-207">이 예제에서는 로컬 Windows 컴퓨터에 있는 5 개의 시스템 로그에서 5만 로그 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-207">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine.</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

<span data-ttu-id="7a49e-208">**Parallel** 매개 변수는 각 입력 로그 이름에 대해 병렬로 실행되는 스크립트 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-208">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span> <span data-ttu-id="7a49e-209">**ThrottleLimit** 매개 변수를 사용 하면 5 개의 스크립트 블록이 모두 동시에 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-209">The **ThrottleLimit** parameter ensures that all five script blocks run at the same time.</span></span>

### <span data-ttu-id="7a49e-210">예제 13: 작업으로 병렬로 실행</span><span class="sxs-lookup"><span data-stu-id="7a49e-210">Example 13: Run in parallel as a job</span></span>

<span data-ttu-id="7a49e-211">이 예제에서는 간단한 스크립트 블록을 병렬로 실행 하 여 한 번에 두 개의 백그라운드 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-211">This example runs a simple script block in parallel, creating two background jobs at a time.</span></span>

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

<span data-ttu-id="7a49e-212">`$job`변수는 출력 데이터를 수집 하 고 실행 상태를 모니터링 하는 작업 개체를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-212">the `$job` variable receives the job object that collects output data and monitors running state.</span></span>
<span data-ttu-id="7a49e-213">작업 개체는 `Receive-Job` **Wait** 스위치 매개 변수를 사용 하 여로 파이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-213">The job object is piped to `Receive-Job` with the **Wait** switch parameter.</span></span> <span data-ttu-id="7a49e-214">이 스트림은 `ForEach-Object -Parallel` **AsJob** 없이 실행 된 것 처럼 콘솔에 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-214">And this streams output to the console, just as if `ForEach-Object -Parallel` was run without **AsJob**.</span></span>

### <span data-ttu-id="7a49e-215">예제 14: 스레드로부터 안전한 변수 참조 사용</span><span class="sxs-lookup"><span data-stu-id="7a49e-215">Example 14: Using thread safe variable references</span></span>

<span data-ttu-id="7a49e-216">이 예에서는 고유 하 게 명명 된 프로세스 개체를 수집 하기 위해 스크립트 블록을 병렬로 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-216">This example invokes script blocks in parallel to collect uniquely named Process objects.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

<span data-ttu-id="7a49e-217">**ConcurrentDictionary** 개체의 단일 인스턴스는 각 스크립트 블록에 전달 되어 개체를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-217">A single instance of a **ConcurrentDictionary** object is passed to each script block to collect the objects.</span></span> <span data-ttu-id="7a49e-218">**ConcurrentDictionary** 은 스레드로부터 안전 하기 때문에 각 병렬 스크립트에 의해 안전 하 게 수정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-218">Since the **ConcurrentDictionary** is thread safe, it is safe to be modified by each parallel script.</span></span> <span data-ttu-id="7a49e-219">**System.object** 와 같은 스레드로부터 안전 하지 않은 개체는 여기에서 사용 하기에 안전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-219">A non-thread-safe object, such as **System.Collections.Generic.Dictionary**, would not be safe to use here.</span></span>

> [!NOTE]
> <span data-ttu-id="7a49e-220">이 예에서는 **병렬** 매개 변수를 매우 비효율적으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-220">This example is a very inefficient use of **Parallel** parameter.</span></span> <span data-ttu-id="7a49e-221">스크립트는 단순히 입력 개체를 동시 사전 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-221">The script simply adds the input object to a concurrent dictionary object.</span></span> <span data-ttu-id="7a49e-222">별도의 스레드에서 각 스크립트를 호출 하는 오버 헤드가 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-222">It is trivial and not worth the overhead of invoking each script in a separate thread.</span></span> <span data-ttu-id="7a49e-223">`ForEach-Object` **병렬** 스위치 없이 정상적으로 실행 하는 것이 훨씬 더 효율적이 고 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-223">Running `ForEach-Object` normally without the **Parallel** switch is much more efficient and faster.</span></span> <span data-ttu-id="7a49e-224">이 예제는 스레드 안전 변수를 사용 하는 방법을 보여 주기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-224">This example is only intended to demonstrate how to use thread safe variables.</span></span>

### <span data-ttu-id="7a49e-225">예 15: 병렬 실행으로 오류 작성</span><span class="sxs-lookup"><span data-stu-id="7a49e-225">Example 15: Writing errors with parallel execution</span></span>

<span data-ttu-id="7a49e-226">이 예제에서는 기록 된 오류의 순서가 무작위로 오류 스트림에 동시에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-226">This example writes to the error stream in parallel, where the order of written errors is random.</span></span>

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### <span data-ttu-id="7a49e-227">예 16: 병렬 실행에서 오류 종료</span><span class="sxs-lookup"><span data-stu-id="7a49e-227">Example 16: Terminating errors in parallel execution</span></span>

<span data-ttu-id="7a49e-228">이 예제에서는 하나의 병렬 실행 scriptblock에서 종료 오류를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-228">This example demonstrates a terminating error in one parallel running scriptblock.</span></span>

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

<span data-ttu-id="7a49e-229">`Output: 3` 해당 반복에 대 한 병렬 scriptblock이 종료 되었기 때문에 작성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-229">`Output: 3` is never written because the parallel scriptblock for that iteration was terminated.</span></span>

## <span data-ttu-id="7a49e-230">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7a49e-230">Parameters</span></span>

### <span data-ttu-id="7a49e-231">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="7a49e-231">-ArgumentList</span></span>

<span data-ttu-id="7a49e-232">메서드 호출에 대 한 인수 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-232">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="7a49e-233">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a49e-233">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="7a49e-234">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-234">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-235">-Begin</span><span class="sxs-lookup"><span data-stu-id="7a49e-235">-Begin</span></span>

<span data-ttu-id="7a49e-236">이 cmdlet이 입력 개체를 처리 하기 전에 실행 되는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-236">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="7a49e-237">이 스크립트 블록은 전체 파이프라인에 대해 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-237">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="7a49e-238">블록에 대 한 자세한 내용은 `begin` [about_Functions](about/about_functions.md#piping-objects-to-functions)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a49e-238">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-239">-끝</span><span class="sxs-lookup"><span data-stu-id="7a49e-239">-End</span></span>

<span data-ttu-id="7a49e-240">이 cmdlet이 모든 입력 개체를 처리 한 후 실행 되는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-240">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="7a49e-241">이 스크립트 블록은 전체 파이프라인에 대해 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-241">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="7a49e-242">블록에 대 한 자세한 내용은 `end` [about_Functions](about/about_functions.md#piping-objects-to-functions)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a49e-242">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-243">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7a49e-243">-InputObject</span></span>

<span data-ttu-id="7a49e-244">입력 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-244">Specifies the input objects.</span></span> <span data-ttu-id="7a49e-245">`ForEach-Object` 각 입력 개체에 대해 스크립트 블록 또는 작업 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-245">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="7a49e-246">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="7a49e-246">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="7a49e-247">에 **inputobject** 매개 변수를 사용 하는 경우 `ForEach-Object` 명령 결과를로 파이프 하는 대신 `ForEach-Object` **inputobject** 값은 단일 개체로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-247">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="7a49e-248">이는 값이 명령 결과인 컬렉션 (예:) 인 경우에도 마찬가지입니다 `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-248">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="7a49e-249">**InputObject** 는 배열 또는 개체 컬렉션의 개별 속성을 반환할 수 없으므로를 사용 `ForEach-Object` 하 여 정의 된 속성에 특정 값이 있는 개체의 개체 컬렉션에 대 한 작업을 수행 하는 경우 `ForEach-Object` 이 항목의 예제에 나와 있는 것 처럼 파이프라인에서를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-249">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-250">-MemberName</span><span class="sxs-lookup"><span data-stu-id="7a49e-250">-MemberName</span></span>

<span data-ttu-id="7a49e-251">가져올 속성이나 호출할 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-251">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="7a49e-252">와일드 카드 문자를 사용할 수 있지만 결과 문자열이 고유한 값으로 확인 되는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-252">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="7a49e-253">예를 들어를 실행 하 `Get-Process | ForEach -MemberName *Name` 는 경우 와일드 카드 패턴은 두 개 이상의 멤버와 일치 하므로 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-253">For example, if you run `Get-Process | ForEach -MemberName *Name`, the wildcard pattern matches more than one member causing the command to fail.</span></span>

<span data-ttu-id="7a49e-254">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-254">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7a49e-255">-Process</span><span class="sxs-lookup"><span data-stu-id="7a49e-255">-Process</span></span>

<span data-ttu-id="7a49e-256">각 입력 개체에 대해 수행되는 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-256">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="7a49e-257">이 스크립트 블록은 파이프라인의 모든 개체에 대해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-257">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="7a49e-258">블록에 대 한 자세한 내용은 `process` [about_Functions](about/about_functions.md#piping-objects-to-functions)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a49e-258">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="7a49e-259">**프로세스** 매개 변수에 여러 스크립트 블록을 제공 하는 경우 첫 번째 스크립트 블록은 항상 블록에 매핑됩니다 `begin` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-259">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="7a49e-260">두 개의 스크립트 블록만 있는 경우 두 번째 블록은 블록에 매핑됩니다 `process` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-260">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="7a49e-261">스크립트 블록이 3 개 이상 있는 경우 첫 번째 스크립트 블록은 항상 블록에 매핑되고 `begin` , 마지막 블록은 블록에 매핑되고, `end` 사이에 있는 블록은 모두 블록에 매핑됩니다 `process` .</span><span class="sxs-lookup"><span data-stu-id="7a49e-261">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-262">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="7a49e-262">-RemainingScripts</span></span>

<span data-ttu-id="7a49e-263">**Process** 매개 변수에서 사용 하지 않는 모든 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-263">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="7a49e-264">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-264">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-265">-Parallel</span><span class="sxs-lookup"><span data-stu-id="7a49e-265">-Parallel</span></span>

<span data-ttu-id="7a49e-266">입력 개체의 병렬 처리에 사용할 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-266">Specifies the script block to be used for parallel processing of input objects.</span></span> <span data-ttu-id="7a49e-267">작업을 설명하는 스크립트 블록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-267">Enter a script block that describes the operation.</span></span>

<span data-ttu-id="7a49e-268">이 매개 변수는 PowerShell 7.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-268">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-269">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="7a49e-269">-ThrottleLimit</span></span>

<span data-ttu-id="7a49e-270">병렬로 스크립트 블록 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-270">Specifies the number of script blocks that in parallel.</span></span> <span data-ttu-id="7a49e-271">입력 개체는 실행 중인 스크립트 블록 수가 **ThrottleLimit** 아래로 떨어질 때까지 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-271">Input objects are blocked until the running script block count falls below the **ThrottleLimit**.</span></span> <span data-ttu-id="7a49e-272">기본값은 `5`입니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-272">The default value is `5`.</span></span>

<span data-ttu-id="7a49e-273">이 매개 변수는 PowerShell 7.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-273">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-274">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="7a49e-274">-TimeoutSeconds</span></span>

<span data-ttu-id="7a49e-275">모든 입력이 병렬로 처리 될 때까지 대기 하는 시간 (초)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-275">Specifies the number of seconds to wait for all input to be processed in parallel.</span></span> <span data-ttu-id="7a49e-276">지정 된 제한 시간 후에는 실행 중인 모든 스크립트가 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-276">After the specified timeout time, all running scripts are stopped.</span></span> <span data-ttu-id="7a49e-277">그리고 처리할 나머지 모든 입력 개체는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-277">And any remaining input objects to be processed are ignored.</span></span> <span data-ttu-id="7a49e-278">의 기본값 `0` 은 시간 제한을 사용 하지 않도록 설정 하 고 `ForEach-Object -Parallel` 무기한 실행 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-278">Default value of `0` disables the timeout, and `ForEach-Object -Parallel` can run indefinitely.</span></span> <span data-ttu-id="7a49e-279">명령줄에서 <kbd>Ctrl</kbd> + <kbd>C</kbd> 를 입력 하면 실행 중인 `ForEach-Object -Parallel` 명령이 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-279">Typing <kbd>Ctrl</kbd>+<kbd>C</kbd> at the command line stops a running `ForEach-Object -Parallel` command.</span></span> <span data-ttu-id="7a49e-280">이 매개 변수는 **AsJob** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-280">This parameter cannot be used along with the **AsJob** parameter.</span></span>

<span data-ttu-id="7a49e-281">이 매개 변수는 PowerShell 7.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-281">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-282">-UseNewRunspace</span><span class="sxs-lookup"><span data-stu-id="7a49e-282">-UseNewRunspace</span></span>

<span data-ttu-id="7a49e-283">병렬 호출이 runspace 풀에서 runspace를 다시 사용 하는 대신 모든 루프 반복에 대해 새 runspace를 만들도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-283">Causes the parallel invocation to create a new runspace for every loop iteration instead of reusing runspaces from the runspace pool.</span></span>

<span data-ttu-id="7a49e-284">이 매개 변수는 PowerShell 7.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-284">This parameter was introduced in PowerShell 7.1</span></span>

```yml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-285">-AsJob</span><span class="sxs-lookup"><span data-stu-id="7a49e-285">-AsJob</span></span>

<span data-ttu-id="7a49e-286">병렬 호출이 PowerShell 작업으로 실행 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-286">Causes the parallel invocation to run as a PowerShell job.</span></span> <span data-ttu-id="7a49e-287">실행 중인 스크립트 블록에서 출력 하는 대신 단일 작업 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-287">A single job object is returned instead of output from the running script blocks.</span></span> <span data-ttu-id="7a49e-288">작업 개체에는를 실행 하는 각 병렬 스크립트 블록에 대 한 자식 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-288">The job object contains child jobs for each parallel script block that runs.</span></span> <span data-ttu-id="7a49e-289">작업 개체는 모든 PowerShell 작업 cmdlet에서 실행 상태를 모니터링 하 고 데이터를 검색 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-289">The job object can be used by all PowerShell job cmdlets, to monitor running state and retrieve data.</span></span>

<span data-ttu-id="7a49e-290">이 매개 변수는 PowerShell 7.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-290">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-291">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7a49e-291">-Confirm</span></span>

<span data-ttu-id="7a49e-292">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-292">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-293">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7a49e-293">-WhatIf</span></span>

<span data-ttu-id="7a49e-294">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-294">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="7a49e-295">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-295">The cmdlet is not run.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a49e-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a49e-296">CommonParameters</span></span>

<span data-ttu-id="7a49e-297">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a49e-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a49e-298">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a49e-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a49e-299">입력</span><span class="sxs-lookup"><span data-stu-id="7a49e-299">Inputs</span></span>

### <span data-ttu-id="7a49e-300">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="7a49e-300">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7a49e-301">모든 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-301">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="7a49e-302">출력</span><span class="sxs-lookup"><span data-stu-id="7a49e-302">Outputs</span></span>

### <span data-ttu-id="7a49e-303">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="7a49e-303">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7a49e-304">이 cmdlet은 입력에 의해 결정 되는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-304">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="7a49e-305">참고</span><span class="sxs-lookup"><span data-stu-id="7a49e-305">Notes</span></span>

- <span data-ttu-id="7a49e-306">이 cmdlet은 foreach 문과 `ForEach-Object` 매우  유사 하 게 작동 합니다. 단, **foreach** 문에는 입력을 파이프 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-306">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="7a49e-307">**Foreach** 문에 대 한 자세한 내용은 [about_Foreach](./About/about_Foreach.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a49e-307">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="7a49e-308">PowerShell 4.0부터 `Where` `ForEach` 컬렉션과 함께 사용 하기 위해 메서드가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-308">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="7a49e-309">이러한 새 메서드에 대 한 자세한 내용은 여기를 참조 하세요 [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="7a49e-309">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

- <span data-ttu-id="7a49e-310">`ForEach-Object -Parallel`매개 변수 집합은 PowerShell의 내부 API를 사용 하 여 각 스크립트 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-310">The `ForEach-Object -Parallel` parameter set uses PowerShell's internal API to run each script block.</span></span> <span data-ttu-id="7a49e-311">이는 `ForEach-Object` 순차적 처리를 통해 정상적으로 실행 하는 것 보다 훨씬 더 많은 오버 헤드가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-311">This is significantly more overhead than running `ForEach-Object` normally with sequential processing.</span></span> <span data-ttu-id="7a49e-312">병렬로 실행 하는 오버 헤드가 스크립트 블록에서 수행 하는 작업에 비해 작은 경우 **병렬** 를 사용 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-312">It is important to use **Parallel** where the overhead of running in parallel is small compared to work the script block performs.</span></span> <span data-ttu-id="7a49e-313">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-313">For example:</span></span>

  - <span data-ttu-id="7a49e-314">다중 코어 컴퓨터에서 계산 집약적인 스크립트</span><span class="sxs-lookup"><span data-stu-id="7a49e-314">Compute intensive scripts on multi-core machines</span></span>
  - <span data-ttu-id="7a49e-315">결과를 기다리거나 파일 작업을 수행 하는 데 시간을 소비 하는 스크립트</span><span class="sxs-lookup"><span data-stu-id="7a49e-315">Scripts that spend time waiting for results or doing file operations</span></span>

  <span data-ttu-id="7a49e-316">**Parallel** 매개 변수를 사용 하면 스크립트가 평소 보다 훨씬 느리게 실행 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-316">Using the **Parallel** parameter can cause scripts to run much slower than normal.</span></span> <span data-ttu-id="7a49e-317">특히 병렬 스크립트가 trivial 인 경우</span><span class="sxs-lookup"><span data-stu-id="7a49e-317">Especially if the parallel scripts are trivial.</span></span> <span data-ttu-id="7a49e-318">**병렬** 로 실험 하 여 유용할 수 있는 위치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-318">Experiment with **Parallel** to discover where it can be beneficial.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="7a49e-319">`ForEach-Object -Parallel`매개 변수 집합은 별도의 프로세스 스레드에서 스크립트 블록을 병렬로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-319">The `ForEach-Object -Parallel` parameter set runs script blocks in parallel on separate process threads.</span></span> <span data-ttu-id="7a49e-320">`$using:`키워드를 사용 하면 cmdlet 호출 스레드에서 실행 중인 각 스크립트 블록 스레드로 변수 참조를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-320">The `$using:` keyword allows passing variable references from the cmdlet invocation thread to each running script block thread.</span></span> <span data-ttu-id="7a49e-321">스크립트 블록은 다른 스레드에서 실행 되므로 참조로 전달 되는 개체 변수를 안전 하 게 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-321">Since the script blocks run in different threads, the object variables passed by reference must be used safely.</span></span> <span data-ttu-id="7a49e-322">일반적으로 변경 되지 않는 참조 된 개체를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a49e-322">Generally it is safe to read from referenced objects that don't change.</span></span> <span data-ttu-id="7a49e-323">하지만 개체 상태를 수정 하는 경우에는 .Net **system.object** 와 같은 스레드로부터 안전한 개체를 사용 해야 합니다 (예 11 참조).</span><span class="sxs-lookup"><span data-stu-id="7a49e-323">But if the object state is being modified then you must used thread safe objects, such as .Net **System.Collection.Concurrent** types (See Example 11).</span></span>

## <span data-ttu-id="7a49e-324">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7a49e-324">Related links</span></span>

[<span data-ttu-id="7a49e-325">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="7a49e-325">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="7a49e-326">Where-Object</span><span class="sxs-lookup"><span data-stu-id="7a49e-326">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="7a49e-327">Group-Object</span><span class="sxs-lookup"><span data-stu-id="7a49e-327">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="7a49e-328">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="7a49e-328">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="7a49e-329">New-Object</span><span class="sxs-lookup"><span data-stu-id="7a49e-329">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="7a49e-330">Select-Object</span><span class="sxs-lookup"><span data-stu-id="7a49e-330">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="7a49e-331">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="7a49e-331">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="7a49e-332">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="7a49e-332">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
