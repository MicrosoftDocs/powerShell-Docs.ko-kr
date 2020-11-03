---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 5a1a53c2b312ef36c80ecfb2a771d2fee2ebea7f
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "93219889"
---
# <span data-ttu-id="f11a2-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="f11a2-103">ForEach-Object</span></span>

## <span data-ttu-id="f11a2-104">개요</span><span class="sxs-lookup"><span data-stu-id="f11a2-104">SYNOPSIS</span></span>
<span data-ttu-id="f11a2-105">입력 개체 컬렉션에 있는 각 항목에 대해 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="f11a2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f11a2-106">SYNTAX</span></span>

### <span data-ttu-id="f11a2-107">ScriptBlockSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="f11a2-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f11a2-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="f11a2-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f11a2-109">설명</span><span class="sxs-lookup"><span data-stu-id="f11a2-109">DESCRIPTION</span></span>

<span data-ttu-id="f11a2-110">`ForEach-Object`Cmdlet은 입력 개체 컬렉션의 각 항목에 대해 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-110">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="f11a2-111">입력 개체를 cmdlet으로 파이프 하거나 **InputObject** 매개 변수를 사용 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-111">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="f11a2-112">Windows PowerShell 3.0부터 명령을 생성 하는 방법에는 두 가지가 있습니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-112">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="f11a2-113">**스크립트 블록** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-113">**Script block**.</span></span> <span data-ttu-id="f11a2-114">스크립트 블록을 사용하여 작업을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-114">You can use a script block to specify the operation.</span></span> <span data-ttu-id="f11a2-115">스크립트 블록 내에서 변수를 사용 `$_` 하 여 현재 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-115">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="f11a2-116">스크립트 블록은 **Process** 매개 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-116">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="f11a2-117">스크립트 블록에는 모든 PowerShell 스크립트가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-117">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="f11a2-118">예를 들어 다음 명령은 컴퓨터에 있는 각 프로세스의 **ProcessName** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-118">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="f11a2-119">`ForEach-Object``begin` `process` `end` [about_functions](about/about_functions.md#piping-objects-to-functions)에 설명 된 대로, 및 블록을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-119">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="f11a2-120">스크립트 블록은 호출자의 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-120">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="f11a2-121">따라서 블록은 해당 범위의 변수에 액세스할 수 있으며 cmdlet이 완료 된 후 해당 범위에 유지 되는 새 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-121">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="f11a2-122">**Operation 문**.</span><span class="sxs-lookup"><span data-stu-id="f11a2-122">**Operation statement**.</span></span> <span data-ttu-id="f11a2-123">자연어와 유사한 작업 문을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-123">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="f11a2-124">작업 문을 사용하여 속성 값을 지정하거나 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-124">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="f11a2-125">작업 문은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-125">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="f11a2-126">예를 들어 다음 명령도 컴퓨터에 있는 각 프로세스의 **ProcessName** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-126">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

## <span data-ttu-id="f11a2-127">예제</span><span class="sxs-lookup"><span data-stu-id="f11a2-127">EXAMPLES</span></span>

### <span data-ttu-id="f11a2-128">예제 1: 배열의 정수 나누기</span><span class="sxs-lookup"><span data-stu-id="f11a2-128">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="f11a2-129">이 예제에서는 세 개의 정수로 이루어진 배열을 사용 하 여 각 정수를 1024으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-129">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="f11a2-130">예 2: 디렉터리에 있는 모든 파일의 길이 가져오기</span><span class="sxs-lookup"><span data-stu-id="f11a2-130">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="f11a2-131">이 예에서는 PowerShell 설치 디렉터리의 파일 및 디렉터리를 처리 `$PSHOME` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-131">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="f11a2-132">개체가 디렉터리가 아닌 경우 스크립트 블록은 파일의 이름을 가져오고, **길이** 속성의 값을 1024로 나누고, 공백 ("")을 추가 하 여 다음 항목과 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-132">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="f11a2-133">이 cmdlet은 **PSISContainer** 속성을 사용 하 여 개체가 디렉터리 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-133">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="f11a2-134">예 3: 최신 시스템 이벤트에 대 한 운영</span><span class="sxs-lookup"><span data-stu-id="f11a2-134">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="f11a2-135">이 예제에서는 시스템 이벤트 로그의 최신 이벤트 1000을 텍스트 파일에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-135">This example write the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="f11a2-136">현재 시간은 이벤트를 처리 하기 전과 후에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-136">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="f11a2-137">`Get-EventLog` 시스템 이벤트 로그에서 1000 개의 최신 이벤트를 가져와 변수에 저장 합니다 `$Events` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-137">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="f11a2-138">`$Events` 가 cmdlet으로 파이프 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-138">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="f11a2-139">**Begin** 매개 변수는 현재 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-139">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="f11a2-140">그런 다음 **Process** 매개 변수는 cmdlet을 사용 하 여 `Out-File` events.txt 라는 텍스트 파일을 만들고 해당 파일에 있는 각 이벤트의 메시지 속성을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-140">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="f11a2-141">마지막으로, **End** 매개 변수는 모든 처리가 완료된 후 날짜와 시간을 표시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-141">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="f11a2-142">예제 4: 레지스트리 키 값 변경</span><span class="sxs-lookup"><span data-stu-id="f11a2-142">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="f11a2-143">이 예에서는 키 아래의 모든 하위 키에 있는 **RemotePath** 레지스트리 항목의 값을 `HKCU:\Network` 대문자 텍스트로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-143">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="f11a2-144">이 형식을 사용하여 레지스트리 항목 값의 형식이나 내용을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-144">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="f11a2-145">**Network** 키의 각 하위 키는 로그온 시 다시 연결할 매핑된 네트워크 드라이브를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-145">Each subkey in the **Network** key represents a mapped network drive that will reconnect at logon.</span></span>
<span data-ttu-id="f11a2-146">**RemotePath** 항목에는 연결된 드라이브의 UNC 경로가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-146">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="f11a2-147">예를 들어 E: 드라이브를에 매핑하면 `\\Server\Share` 의 **e** 하위 키가 `HKCU:\Network` 있으며 **e** 하위 키에 있는 **RemotePath** 레지스트리 항목의 값은입니다 `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-147">For example, if you map the E: drive to `\\Server\Share`, there will be an **E** subkey of `HKCU:\Network` and the value of the **RemotePath** registry entry in the **E** subkey is `\\Server\Share`.</span></span>

<span data-ttu-id="f11a2-148">이 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` **네트워크** 키의 모든 하위 키를 가져오고 cmdlet을 사용 하 여 `Set-ItemProperty` 각 키에서 **RemotePath** 레지스트리 항목의 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-148">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="f11a2-149">명령에서 `Set-ItemProperty` 경로는 레지스트리 키의 **PSPath** 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-149">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="f11a2-150">레지스트리 항목이 아니라 레지스트리 키를 나타내는 Microsoft .NET Framework 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-150">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="f11a2-151">이 명령은 문자열 (REG_SZ) 인 **RemotePath** 값의 **ToUpper ()** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-151">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="f11a2-152">`Set-ItemProperty`는 각 키의 속성을 변경 하기 때문에 `ForEach-Object` 속성에 액세스 하려면 cmdlet이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-152">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="f11a2-153">예 5: $Null 자동 변수 사용</span><span class="sxs-lookup"><span data-stu-id="f11a2-153">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="f11a2-154">이 예에서는 `$Null` cmdlet에 자동 변수를 파이프 하는 결과를 보여 줍니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-154">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="f11a2-155">PowerShell은 null을 명시적 자리 표시자로 처리 하기 때문에 `ForEach-Object` 이 cmdlet은 `$Null` 파이프 하는 다른 개체와 마찬가지로에 대 한 값을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-155">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="f11a2-156">예제 6: 속성 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="f11a2-156">Example 6: Get property values</span></span>

<span data-ttu-id="f11a2-157">이 예에서는 cmdlet의 **MemberName** 매개 변수를 사용 하 여 설치 된 모든 PowerShell 모듈의 **Path** 속성 값을 가져옵니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-157">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="f11a2-158">두 번째 명령은 첫 번째 명령과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-158">The second command is equivalent to the first.</span></span> <span data-ttu-id="f11a2-159">`Foreach`Cmdlet의 별칭을 사용 하 `ForEach-Object` 고 **MemberName** 매개 변수 (선택 사항)의 이름을 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-159">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="f11a2-160">Cmdlet은 속성 값 `ForEach-Object` 형식을 변경 하는 **Format** cmdlet 또는 cmdlet과 달리 형식을 변경 하지 않고 값을 가져오기 때문에 속성 값을 가져오는 데 매우 유용 합니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-160">The `ForEach-Object` cmdlet is very useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="f11a2-161">예 7: 모듈 이름을 구성 요소 이름으로 분할</span><span class="sxs-lookup"><span data-stu-id="f11a2-161">Example 7: Split module names into component names</span></span>

<span data-ttu-id="f11a2-162">이 예제에서는 점으로 구분 된 두 개의 모듈 이름을 해당 구성 요소 이름으로 분할 하는 세 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-162">This examples shows three ways to split two dot-separated module names into their component names.</span></span>

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

<span data-ttu-id="f11a2-163">명령에서 문자열의 **Split** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-163">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="f11a2-164">세 명령은 서로 다른 구문을 사용하지만 동일하며 교환해서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-164">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="f11a2-165">첫 번째 명령은 스크립트 블록과 현재 개체 연산자를 포함 하는 일반적인 구문을 사용 합니다 `$_` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-165">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="f11a2-166">점 구문을 사용하여 메서드를 지정하고 괄호를 사용하여 구분 기호 인수를 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-166">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="f11a2-167">두 번째 명령은 **MemberName** 매개 변수를 사용하여 **Split** 메서드를 지정하고 **ArgumentName** 매개 변수를 사용하여 점(".")을 분할 구분 기호로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-167">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="f11a2-168">세 번째 명령은 cmdlet의 **Foreach** 별칭을 사용 하 `ForEach-Object` 고 **MemberName** 및 **argumentlist** 매개 변수의 이름을 생략 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="f11a2-168">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="f11a2-169">예 8: 두 스크립트 블록을 사용 하 여 ForEach-Object 사용</span><span class="sxs-lookup"><span data-stu-id="f11a2-169">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="f11a2-170">이 예제에서는 메서드에 액세스할 스크립트 블록 두 개를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-170">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="f11a2-171">모든 스크립트 블록은 **Process** 매개 변수에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-171">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="f11a2-172">그러나 **Begin** 및 **Process** 매개 변수에 전달 된 것 처럼 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-172">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="f11a2-173">예제 9: 두 개 이상의 스크립트 블록을 사용 하 여 ForEach-Object 사용</span><span class="sxs-lookup"><span data-stu-id="f11a2-173">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="f11a2-174">이 예제에서는 메서드에 액세스할 스크립트 블록 두 개를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-174">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="f11a2-175">모든 스크립트 블록은 **Process** 매개 변수에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-175">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="f11a2-176">그러나 **Begin** , **Process** 및 **End** 매개 변수에 전달 된 것 처럼 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-176">However, they are treated as if they had been passed to the **Begin** , **Process** , and **End** parameters.</span></span>

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
> <span data-ttu-id="f11a2-177">첫 번째 스크립트 블록은 항상 블록에 매핑되고 `begin` , 마지막 블록은 블록에 매핑되고 `end` , between의 블록은 모두 블록에 매핑됩니다 `process` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-177">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="f11a2-178">예 10: 각 파이프라인 항목에 대해 여러 스크립트 블록 실행</span><span class="sxs-lookup"><span data-stu-id="f11a2-178">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="f11a2-179">위의 예제와 같이 **Process** 매개 변수를 사용 하 여 전달 된 여러 스크립트 블록은 **Begin** 및 **End** 매개 변수에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-179">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="f11a2-180">이 매핑을 방지 하려면 **Begin** 및 **End** 매개 변수에 대 한 명시적 값을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-180">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

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

## <span data-ttu-id="f11a2-181">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f11a2-181">PARAMETERS</span></span>

### <span data-ttu-id="f11a2-182">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="f11a2-182">-ArgumentList</span></span>

<span data-ttu-id="f11a2-183">메서드 호출에 대 한 인수 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-183">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="f11a2-184">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f11a2-184">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="f11a2-185">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-185">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f11a2-186">-Begin</span><span class="sxs-lookup"><span data-stu-id="f11a2-186">-Begin</span></span>

<span data-ttu-id="f11a2-187">이 cmdlet이 입력 개체를 처리 하기 전에 실행 되는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-187">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="f11a2-188">이 스크립트 블록은 전체 파이프라인에 대해 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-188">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="f11a2-189">블록에 대 한 자세한 내용은 `begin` [about_Functions](about/about_functions.md#piping-objects-to-functions)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f11a2-189">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="f11a2-190">-끝</span><span class="sxs-lookup"><span data-stu-id="f11a2-190">-End</span></span>

<span data-ttu-id="f11a2-191">이 cmdlet이 모든 입력 개체를 처리 한 후 실행 되는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-191">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="f11a2-192">이 스크립트 블록은 전체 파이프라인에 대해 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-192">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="f11a2-193">블록에 대 한 자세한 내용은 `end` [about_Functions](about/about_functions.md#piping-objects-to-functions)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f11a2-193">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="f11a2-194">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f11a2-194">-InputObject</span></span>

<span data-ttu-id="f11a2-195">입력 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-195">Specifies the input objects.</span></span> <span data-ttu-id="f11a2-196">`ForEach-Object` 각 입력 개체에 대해 스크립트 블록 또는 작업 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-196">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="f11a2-197">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="f11a2-197">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="f11a2-198">에 **inputobject** 매개 변수를 사용 하는 경우 `ForEach-Object` 명령 결과를로 파이프 하는 대신 `ForEach-Object` **inputobject** 값은 단일 개체로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-198">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="f11a2-199">이는 값이 명령 결과인 컬렉션 (예:) 인 경우에도 마찬가지입니다 `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-199">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="f11a2-200">**InputObject** 는 배열 또는 개체 컬렉션의 개별 속성을 반환할 수 없으므로를 사용 `ForEach-Object` 하 여 정의 된 속성에 특정 값이 있는 개체의 개체 컬렉션에 대 한 작업을 수행 하는 경우 `ForEach-Object` 이 항목의 예제에 나와 있는 것 처럼 파이프라인에서를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-200">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="f11a2-201">-MemberName</span><span class="sxs-lookup"><span data-stu-id="f11a2-201">-MemberName</span></span>

<span data-ttu-id="f11a2-202">가져올 속성이나 호출할 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-202">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="f11a2-203">와일드 카드 문자를 사용할 수 있지만 결과 문자열이 고유한 값으로 확인 되는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-203">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="f11a2-204">예를 들어를 실행 하는 경우 `Get-Process | ForEach -MemberName *Name` **ProcessName** 및 **Name** 속성과 같이 문자열 이름을 포함 하는 이름으로 두 개 이상의 멤버가 있으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-204">If, for example, you run `Get-Process | ForEach -MemberName *Name`, and more than one member exists with a name that contains the string Name, such as the **ProcessName** and **Name** properties, the command fails.</span></span>

<span data-ttu-id="f11a2-205">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f11a2-206">-Process</span><span class="sxs-lookup"><span data-stu-id="f11a2-206">-Process</span></span>

<span data-ttu-id="f11a2-207">각 입력 개체에 대해 수행되는 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-207">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="f11a2-208">이 스크립트 블록은 파이프라인의 모든 개체에 대해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-208">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="f11a2-209">블록에 대 한 자세한 내용은 `process` [about_Functions](about/about_functions.md#piping-objects-to-functions)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f11a2-209">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="f11a2-210">**프로세스** 매개 변수에 여러 스크립트 블록을 제공 하는 경우 첫 번째 스크립트 블록은 항상 블록에 매핑됩니다 `begin` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-210">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="f11a2-211">두 개의 스크립트 블록만 있는 경우 두 번째 블록은 블록에 매핑됩니다 `process` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-211">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="f11a2-212">스크립트 블록이 3 개 이상 있는 경우 첫 번째 스크립트 블록은 항상 블록에 매핑되고 `begin` , 마지막 블록은 블록에 매핑되고, `end` 사이에 있는 블록은 모두 블록에 매핑됩니다 `process` .</span><span class="sxs-lookup"><span data-stu-id="f11a2-212">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

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

### <span data-ttu-id="f11a2-213">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="f11a2-213">-RemainingScripts</span></span>

<span data-ttu-id="f11a2-214">**Process** 매개 변수에서 사용 하지 않는 모든 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-214">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="f11a2-215">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f11a2-216">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f11a2-216">-Confirm</span></span>

<span data-ttu-id="f11a2-217">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-217">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f11a2-218">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f11a2-218">-WhatIf</span></span>

<span data-ttu-id="f11a2-219">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-219">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f11a2-220">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-220">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f11a2-221">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f11a2-221">CommonParameters</span></span>

<span data-ttu-id="f11a2-222">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f11a2-222">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f11a2-223">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f11a2-223">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f11a2-224">입력</span><span class="sxs-lookup"><span data-stu-id="f11a2-224">INPUTS</span></span>

### <span data-ttu-id="f11a2-225">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="f11a2-225">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f11a2-226">모든 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-226">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="f11a2-227">출력</span><span class="sxs-lookup"><span data-stu-id="f11a2-227">OUTPUTS</span></span>

### <span data-ttu-id="f11a2-228">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="f11a2-228">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f11a2-229">이 cmdlet은 입력에 의해 결정 되는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-229">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="f11a2-230">참고</span><span class="sxs-lookup"><span data-stu-id="f11a2-230">NOTES</span></span>

- <span data-ttu-id="f11a2-231">이 cmdlet은 foreach 문과 `ForEach-Object` 매우 **Foreach** 유사 하 게 작동 합니다. 단, **foreach** 문에는 입력을 파이프 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-231">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="f11a2-232">**Foreach** 문에 대 한 자세한 내용은 [about_Foreach](./About/about_Foreach.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f11a2-232">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="f11a2-233">PowerShell 4.0부터 `Where` `ForEach` 컬렉션과 함께 사용 하기 위해 메서드가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f11a2-233">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="f11a2-234">이러한 새 메서드에 대 한 자세한 내용은 여기를 참조 하세요 [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="f11a2-234">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="f11a2-235">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f11a2-235">RELATED LINKS</span></span>

[<span data-ttu-id="f11a2-236">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="f11a2-236">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="f11a2-237">Where-Object</span><span class="sxs-lookup"><span data-stu-id="f11a2-237">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="f11a2-238">Group-Object</span><span class="sxs-lookup"><span data-stu-id="f11a2-238">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="f11a2-239">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="f11a2-239">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="f11a2-240">New-Object</span><span class="sxs-lookup"><span data-stu-id="f11a2-240">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="f11a2-241">Select-Object</span><span class="sxs-lookup"><span data-stu-id="f11a2-241">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="f11a2-242">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="f11a2-242">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="f11a2-243">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="f11a2-243">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
