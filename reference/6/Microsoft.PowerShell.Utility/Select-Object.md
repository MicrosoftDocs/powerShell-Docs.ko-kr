---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 11aedd0f5249153e01382132c9eeb95f0717cda3
ms.sourcegitcommit: f9ae48d026d65833b9c8ca881058dda0bbd067b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "93220089"
---
# <span data-ttu-id="17e7a-103">Select-Object</span><span class="sxs-lookup"><span data-stu-id="17e7a-103">Select-Object</span></span>

## <span data-ttu-id="17e7a-104">개요</span><span class="sxs-lookup"><span data-stu-id="17e7a-104">SYNOPSIS</span></span>
<span data-ttu-id="17e7a-105">개체 또는 개체 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-105">Selects objects or object properties.</span></span>

## <span data-ttu-id="17e7a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="17e7a-106">SYNTAX</span></span>

### <span data-ttu-id="17e7a-107">DefaultParameter (기본값)</span><span class="sxs-lookup"><span data-stu-id="17e7a-107">DefaultParameter (Default)</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### <span data-ttu-id="17e7a-108">SkipLastParameter</span><span class="sxs-lookup"><span data-stu-id="17e7a-108">SkipLastParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="17e7a-109">IndexParameter</span><span class="sxs-lookup"><span data-stu-id="17e7a-109">IndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="17e7a-110">SkipIndexParameter</span><span class="sxs-lookup"><span data-stu-id="17e7a-110">SkipIndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="17e7a-111">설명</span><span class="sxs-lookup"><span data-stu-id="17e7a-111">DESCRIPTION</span></span>

<span data-ttu-id="17e7a-112">`Select-Object`Cmdlet은 개체 또는 개체 집합의 지정 된 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-112">The `Select-Object` cmdlet selects specified properties of an object or set of objects.</span></span> <span data-ttu-id="17e7a-113">또한 고유한 개체, 지정된 수의 개체 또는 배열에서 지정된 위치에 있는 개체를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-113">It can also select unique objects, a specified number of objects, or objects in a specified position in an array.</span></span>

<span data-ttu-id="17e7a-114">컬렉션에서 개체를 선택하려면 **First** , **Last** , **Unique** , **Skip** 및 **Index** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-114">To select objects from a collection, use the **First** , **Last** , **Unique** , **Skip** , and **Index** parameters.</span></span> <span data-ttu-id="17e7a-115">개체 속성을 선택하려면 **Property** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-115">To select object properties, use the **Property** parameter.</span></span> <span data-ttu-id="17e7a-116">속성을 선택 하면에서 `Select-Object` 지정 된 속성만 있는 새 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-116">When you select properties, `Select-Object` returns new objects that have only the specified properties.</span></span>

<span data-ttu-id="17e7a-117">Windows PowerShell 3.0 이상에 `Select-Object` 는 명령에서 사용 되지 않는 개체를 만들고 처리 하지 못하게 하는 최적화 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-117">Beginning in Windows PowerShell 3.0, `Select-Object` includes an optimization feature that prevents commands from creating and processing objects that are not used.</span></span>

<span data-ttu-id="17e7a-118">명령 `Select-Object` 파이프라인에 **첫 번째** 또는 **인덱스** 매개 변수를 사용 하 여 명령을 포함 하는 경우 개체를 생성 하는 명령이 파이프라인의 명령 앞에 표시 되는 경우에도 PowerShell에서 개체를 생성 하는 명령을 중지 합니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-118">When you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated, even when the command that generates the objects appears before the `Select-Object` command in the pipeline.</span></span> <span data-ttu-id="17e7a-119">이 최적화 동작을 끄려면 **Wait** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-119">To turn off this optimizing behavior, use the **Wait** parameter.</span></span>

## <span data-ttu-id="17e7a-120">예제</span><span class="sxs-lookup"><span data-stu-id="17e7a-120">EXAMPLES</span></span>

### <span data-ttu-id="17e7a-121">예제 1: 속성으로 개체 선택</span><span class="sxs-lookup"><span data-stu-id="17e7a-121">Example 1: Select objects by property</span></span>

<span data-ttu-id="17e7a-122">이 예에서는 process 개체의 **이름** , **ID** 및 **WS** (작업 집합) 속성이 있는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-122">This example creates objects that have the **Name** , **ID** , and working set ( **WS** ) properties of process objects.</span></span>

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### <span data-ttu-id="17e7a-123">예제 2: 속성으로 개체 선택 및 결과 서식 지정</span><span class="sxs-lookup"><span data-stu-id="17e7a-123">Example 2: Select objects by property and format the results</span></span>

<span data-ttu-id="17e7a-124">이 예에서는 컴퓨터의 프로세스에서 사용 하는 모듈에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-124">This example gets information about the modules used by the processes on the computer.</span></span> <span data-ttu-id="17e7a-125">Cmdlet을 사용 하 여 `Get-Process` 컴퓨터의 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-125">It uses `Get-Process` cmdlet to get the process on the computer.</span></span>

<span data-ttu-id="17e7a-126">Cmdlet을 사용 하 여에 `Select-Object` `[System.Diagnostics.ProcessModule]` 의해 출력 되는 각 인스턴스의 **Modules** 속성에 포함 된 인스턴스의 배열을 출력 `System.Diagnostics.Process` `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-126">It uses the `Select-Object` cmdlet to output an array of `[System.Diagnostics.ProcessModule]` instances as contained in the **Modules** property of each `System.Diagnostics.Process` instance output by `Get-Process`.</span></span>

<span data-ttu-id="17e7a-127">Cmdlet의 **Property** 매개 변수는 `Select-Object` 프로세스 이름을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-127">The **Property** parameter of the `Select-Object` cmdlet selects the process names.</span></span> <span data-ttu-id="17e7a-128">`ProcessName`모든 인스턴스에 대 한 **참고 속성** 을 추가 하 `[System.Diagnostics.ProcessModule]` 고 현재 프로세스의 **ProcessName** 속성 값으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-128">This adds a `ProcessName` **NoteProperty** to every `[System.Diagnostics.ProcessModule]` instance and populates it with the value of current process's **ProcessName** property.</span></span>

<span data-ttu-id="17e7a-129">마지막으로 `Format-List` cmdlet은 각 프로세스의 이름과 모듈을 목록에 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-129">Finally, `Format-List` cmdlet is used to display the name and modules of each process in a list.</span></span>

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### <span data-ttu-id="17e7a-130">예제 3: 메모리를 가장 많이 사용 하는 프로세스 선택</span><span class="sxs-lookup"><span data-stu-id="17e7a-130">Example 3: Select processes using the most memory</span></span>

<span data-ttu-id="17e7a-131">이 예제에서는 메모리를 가장 많이 사용 하는 5 개의 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-131">This example gets the five processes that are using the most memory.</span></span> <span data-ttu-id="17e7a-132">`Get-Process`Cmdlet은 컴퓨터의 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-132">The `Get-Process` cmdlet gets the processes on the computer.</span></span> <span data-ttu-id="17e7a-133">`Sort-Object`Cmdlet은 메모리 (작업 집합) 사용에 따라 프로세스를 정렬 하 고, `Select-Object` cmdlet은 개체의 결과 배열에서 마지막 5 개의 멤버만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-133">The `Sort-Object` cmdlet sorts the processes according to memory (working set) usage, and the `Select-Object` cmdlet selects only the last five members of the resulting array of objects.</span></span>

<span data-ttu-id="17e7a-134">는 **Wait** `Sort-Object` `Sort-Object` 모든 개체를 처리 한 다음 컬렉션을 반환 하기 때문에 cmdlet을 포함 하는 명령에는 Wait 매개 변수가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-134">The **Wait** parameter is not required in commands that include the `Sort-Object` cmdlet because `Sort-Object` processes all objects and then returns a collection.</span></span> <span data-ttu-id="17e7a-135">`Select-Object`최적화는 개체를 처리 하는 동안 개별적으로 반환 하는 명령에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-135">The `Select-Object` optimization is available only for commands that return objects individually as they are processed.</span></span>

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### <span data-ttu-id="17e7a-136">예제 4: 배열에서 고유한 문자 선택</span><span class="sxs-lookup"><span data-stu-id="17e7a-136">Example 4: Select unique characters from an array</span></span>

<span data-ttu-id="17e7a-137">이 예제에서는의 **unique** 매개 변수를 사용 하 여 `Select-Object` 문자 배열에서 고유한 문자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-137">This example uses the **Unique** parameter of `Select-Object` to get unique characters from an array of characters.</span></span>

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### <span data-ttu-id="17e7a-138">예 5: 이벤트 로그에서 최신 이벤트 및 가장 오래 된 이벤트 선택</span><span class="sxs-lookup"><span data-stu-id="17e7a-138">Example 5: Select newest and oldest events in the event log</span></span>

<span data-ttu-id="17e7a-139">이 예제에서는 Windows PowerShell 이벤트 로그에서 첫 번째 (최신) 및 마지막 (가장 오래 된) 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-139">This example gets the first (newest) and last (oldest) events in the Windows PowerShell event log.</span></span>

<span data-ttu-id="17e7a-140">`Get-EventLog` Windows PowerShell 로그의 모든 이벤트를 가져와 `$a` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-140">`Get-EventLog` gets all events in the Windows PowerShell log and saves them in the `$a` variable.</span></span>
<span data-ttu-id="17e7a-141">그런 다음 `$a` 가 cmdlet으로 파이프 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-141">Then, `$a` is piped to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="17e7a-142">이 `Select-Object` 명령은 **Index** 매개 변수를 사용 하 여 변수의 이벤트 배열에서 이벤트를 선택 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-142">The `Select-Object` command uses the **Index** parameter to select events from the array of events in the `$a` variable.</span></span> <span data-ttu-id="17e7a-143">첫 번째 이벤트의 인덱스는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-143">The index of the first event is 0.</span></span> <span data-ttu-id="17e7a-144">마지막 이벤트의 인덱스는의 항목 수에서 1을 뺀 값입니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-144">The index of the last event is the number of items in `$a` minus 1.</span></span>

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### <span data-ttu-id="17e7a-145">예제 6: 첫 번째 개체를 제외한 모든 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-145">Example 6: Select all but the first object</span></span>

<span data-ttu-id="17e7a-146">이 예제에서는 첫 번째 항목을 제외 하 고 Servers.txt 파일에 나열 된 각 컴퓨터에 새 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-146">This example creates a new PSSession on each of the computers listed in the Servers.txt files, except for the first one.</span></span>

<span data-ttu-id="17e7a-147">`Select-Object` 컴퓨터 이름 목록에서 첫 번째 컴퓨터를 제외한 모든 컴퓨터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-147">`Select-Object` selects all but the first computer in a list of computer names.</span></span> <span data-ttu-id="17e7a-148">결과 컴퓨터 목록은 cmdlet의 **ComputerName** 매개 변수 값으로 설정 됩니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-148">The resulting list of computers is set as the value of the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### <span data-ttu-id="17e7a-149">예 7: 파일 이름 바꾸기 및 검토할 몇 가지 선택</span><span class="sxs-lookup"><span data-stu-id="17e7a-149">Example 7: Rename files and select several to review</span></span>

<span data-ttu-id="17e7a-150">이 예에서는 읽기 전용 특성이 있는 텍스트 파일의 기본 이름에 "-ro" 접미사를 추가한 다음 사용자가 결과 샘플을 볼 수 있도록 처음 다섯 개 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-150">This example adds a "-ro" suffix to the base names of text files that have the read-only attribute and then displays the first five files so the user can see a sample of the effect.</span></span>

<span data-ttu-id="17e7a-151">`Get-ChildItem`**ReadOnly** 동적 매개 변수를 사용 하 여 읽기 전용 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-151">`Get-ChildItem` uses the **ReadOnly** dynamic parameter to get read-only files.</span></span> <span data-ttu-id="17e7a-152">결과 파일은 cmdlet으로 파이프 되어 `Rename-Item` 파일의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-152">The resulting files are piped to the `Rename-Item` cmdlet, which renames the file.</span></span> <span data-ttu-id="17e7a-153">의 **Passthru** 매개 변수를 사용 하 여 `Rename-Item` 이름을 바꾼 파일을 cmdlet으로 보냅니다 `Select-Object` .이 cmdlet은 표시를 위해 처음 5 개를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-153">It uses the **Passthru** parameter of `Rename-Item` to send the renamed files to the `Select-Object` cmdlet, which selects the first 5 for display.</span></span>

<span data-ttu-id="17e7a-154">의 **Wait** 매개 변수는 `Select-Object` `Get-ChildItem` 처음 5 개의 읽기 전용 텍스트 파일을 가져온 후 PowerShell에서 cmdlet을 중지 하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-154">The **Wait** parameter of `Select-Object` prevents PowerShell from stopping the `Get-ChildItem` cmdlet after it gets the first five read-only text files.</span></span> <span data-ttu-id="17e7a-155">이 매개 변수를 사용하지 않으면 처음 다섯 개 읽기 전용 파일만 이름이 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-155">Without this parameter, only the first five read-only files would be renamed.</span></span>

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### <span data-ttu-id="17e7a-156">예 8:-ExpandProperty 매개 변수를 복잡 하 게 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-156">Example 8: Demonstrate the intricacies of the -ExpandProperty parameter</span></span>

<span data-ttu-id="17e7a-157">이 예에서는 **ExpandProperty** 매개 변수를 복잡 하 게 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-157">This example demonstrates the intricacies of the **ExpandProperty** parameter.</span></span>

<span data-ttu-id="17e7a-158">생성 된 출력은 인스턴스의 배열입니다 `[System.Int32]` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-158">Note that the output generated was an array of `[System.Int32]` instances.</span></span> <span data-ttu-id="17e7a-159">인스턴스는 **출력 뷰의** 표준 서식 지정 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-159">The instances conform to standard formatting rules of the **Output View**.</span></span> <span data-ttu-id="17e7a-160">이는 *확장* 된 속성에 대해 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-160">This is true for any *Expanded* properties.</span></span> <span data-ttu-id="17e7a-161">출력 된 개체에 특정 표준 형식이 있으면 확장 된 속성이 표시 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-161">If the outputted objects have a specific standard format, the expanded property might not be visible.</span></span>

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### <span data-ttu-id="17e7a-162">예제 9: 개체에 대 한 사용자 지정 속성 만들기</span><span class="sxs-lookup"><span data-stu-id="17e7a-162">Example 9: Create custom properties on objects</span></span>

<span data-ttu-id="17e7a-163">다음 예제에서는를 사용 하 여 `Select-Object` 사용자 지정 속성을 개체에 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-163">The following example demonstrates using `Select-Object` to add a custom property to any object.</span></span>
<span data-ttu-id="17e7a-164">존재 하지 않는 속성 이름을 지정 하면 `Select-Object` 는 전달 된 각 개체에 대해 해당 속성을 **참고 속성** 으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-164">When you specify a property name that does not exist, `Select-Object` creates that property as a **NoteProperty** on each object passed.</span></span>

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### <span data-ttu-id="17e7a-165">예 10: 각 InputObject에 대해 계산 된 속성 만들기</span><span class="sxs-lookup"><span data-stu-id="17e7a-165">Example 10: Create calculated properties for each InputObject</span></span>

<span data-ttu-id="17e7a-166">이 예제에서는를 사용 하 여 `Select-Object` 계산 된 속성을 입력에 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-166">This example demonstrates using `Select-Object` to add calculated properties to your input.</span></span> <span data-ttu-id="17e7a-167">**ScriptBlock** 을 **Property** 매개 변수에 전달 하면가 `Select-Object` 전달 된 각 개체에 대해 식을 평가 하 고 결과를 출력에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-167">Passing a **ScriptBlock** to the **Property** parameter causes `Select-Object` to evaluate the expression on each object passed and add the results to the output.</span></span> <span data-ttu-id="17e7a-168">**ScriptBlock** 내에서 변수를 사용 하 여 `$_` 파이프라인의 현재 개체를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-168">Within the **ScriptBlock** , you can use the `$_` variable to reference the current object in the pipeline.</span></span>

<span data-ttu-id="17e7a-169">기본적으로에서는 `Select-Object` **ScriptBlock** 문자열을 속성 이름으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-169">By default, `Select-Object` will use the **ScriptBlock** string as the name of the property.</span></span> <span data-ttu-id="17e7a-170">**Hashtable** 을 사용 하 여 각 개체에 추가 된 사용자 지정 속성으로 **ScriptBlock** 의 출력에 레이블을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-170">Using a **Hashtable** , you can label the output of your **ScriptBlock** as a custom property added to each object.</span></span> <span data-ttu-id="17e7a-171">에 전달 된 각 개체에 여러 계산 된 속성을 추가할 수 있습니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-171">You can add multiple calculated properties to each object passed to `Select-Object`.</span></span>

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## <span data-ttu-id="17e7a-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="17e7a-172">PARAMETERS</span></span>

### <span data-ttu-id="17e7a-173">-ExcludeProperty</span><span class="sxs-lookup"><span data-stu-id="17e7a-173">-ExcludeProperty</span></span>

<span data-ttu-id="17e7a-174">이 cmdlet이 작업에서 제외 하는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-174">Specifies the properties that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="17e7a-175">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-175">Wildcards are permitted.</span></span>

<span data-ttu-id="17e7a-176">PowerShell 6부터 **Excludeproperty** 의 **속성** 매개 변수를 더 이상 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-176">Beginning in PowerShell 6, it is no longer required to include the **Property** parameter for **ExcludeProperty** to work.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="17e7a-177">-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="17e7a-177">-ExpandProperty</span></span>

<span data-ttu-id="17e7a-178">선택할 속성을 지정하고 해당 속성을 확장하려고 시도해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-178">Specifies a property to select, and indicates that an attempt should be made to expand that property.</span></span>

- <span data-ttu-id="17e7a-179">지정 된 속성이 배열인 경우 배열의 각 값이 출력에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-179">If the specified property is an array, each value of the array is included in the output.</span></span>
- <span data-ttu-id="17e7a-180">지정 된 속성이 개체 이면 모든 **InputObject** 에 대해 개체 속성이 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-180">If the specified property is an object, the objects properties are expanded for every **InputObject**</span></span>

<span data-ttu-id="17e7a-181">두 경우 모두 출력 되는 개체의 **형식은** 확장 된 속성의 **형식과** 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-181">In either case, the **Type** of objects output will match the **Type** of the expanded property.</span></span>

<span data-ttu-id="17e7a-182">**Property** 매개 변수가 지정 된 경우는 `Select-Object` 모든 출력 된 개체에 대해 선택한 각 속성을 **메모 속성** 으로 추가 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-182">If the **Property** parameter is specified, `Select-Object` will attempt to add each selected property as a **NoteProperty** to every outputted object.</span></span>

> [!WARNING]
> <span data-ttu-id="17e7a-183">다음 오류가 표시 되는 경우: Select: 속성은 이미 존재 하기 때문에 처리할 수 없습니다 `<PropertyName>` . 다음을 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="17e7a-183">If you receive the error: Select : Property cannot be processed because property `<PropertyName>` already exists, consider the following.</span></span>
> <span data-ttu-id="17e7a-184">를 사용 하는 `-ExpandProperty` 경우 `Select-Object` 기존 속성을 바꿀 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-184">Note that when using `-ExpandProperty`, `Select-Object` can not replace an existing property.</span></span>
> <span data-ttu-id="17e7a-185">이것은 다음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-185">This means:</span></span>
>
> - <span data-ttu-id="17e7a-186">확장 된 개체에 같은 이름의 속성이 있는 경우 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-186">If the expanded object has a property of the same name, an error will occur.</span></span>
> - <span data-ttu-id="17e7a-187">*선택한* 개체에 *확장* 된 개체 속성과 같은 이름의 속성이 있는 경우 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-187">If the *Selected* object has a property of the same name as an *Expanded* objects property, an error will occur.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17e7a-188">-첫 번째</span><span class="sxs-lookup"><span data-stu-id="17e7a-188">-First</span></span>

<span data-ttu-id="17e7a-189">입력 개체 배열의 시작에서 선택할 개체 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-189">Specifies the number of objects to select from the beginning of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17e7a-190">-인덱스</span><span class="sxs-lookup"><span data-stu-id="17e7a-190">-Index</span></span>

<span data-ttu-id="17e7a-191">인덱스 값을 기준으로 배열에서 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-191">Selects objects from an array based on their index values.</span></span> <span data-ttu-id="17e7a-192">인덱스를 쉼표로 구분된 목록으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-192">Enter the indexes in a comma-separated list.</span></span> <span data-ttu-id="17e7a-193">배열의 인덱스는 0에서 시작하는데 여기서 0은 첫 번째 값을 나타내고 (n-1)은 마지막 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-193">Indexes in an array begin with 0, where 0 represents the first value and (n-1) represents the last value.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17e7a-194">-InputObject</span><span class="sxs-lookup"><span data-stu-id="17e7a-194">-InputObject</span></span>

<span data-ttu-id="17e7a-195">파이프라인을 통해 cmdlet에 보낼 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-195">Specifies objects to send to the cmdlet through the pipeline.</span></span> <span data-ttu-id="17e7a-196">이 매개 변수를 사용 하 여 개체를에 연결할 수 있습니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-196">This parameter enables you to pipe objects to `Select-Object`.</span></span>

<span data-ttu-id="17e7a-197">개체를 **inputobject** 매개 변수에 전달 하는 경우 파이프라인을 사용 하는 대신는 `Select-Object` 값이 컬렉션인 경우에도 **inputobject** 를 단일 개체로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-197">When you pass objects to the **InputObject** parameter, instead of using the pipeline, `Select-Object` treats the **InputObject** as a single object, even if the value is a collection.</span></span> <span data-ttu-id="17e7a-198">로 컬렉션을 전달할 때 파이프라인을 사용 하는 것이 좋습니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-198">It is recommended that you use the pipeline when passing collections to `Select-Object`.</span></span>

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

### <span data-ttu-id="17e7a-199">-마지막</span><span class="sxs-lookup"><span data-stu-id="17e7a-199">-Last</span></span>

<span data-ttu-id="17e7a-200">입력 개체 배열의 끝에서 선택할 개체 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-200">Specifies the number of objects to select from the end of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17e7a-201">-속성</span><span class="sxs-lookup"><span data-stu-id="17e7a-201">-Property</span></span>

<span data-ttu-id="17e7a-202">선택할 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-202">Specifies the properties to select.</span></span> <span data-ttu-id="17e7a-203">이러한 속성은 output 개체에 **메모 속성** 멤버로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-203">These properties are added as **NoteProperty** members to the output objects.</span></span> <span data-ttu-id="17e7a-204">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-204">Wildcards are permitted.</span></span>

<span data-ttu-id="17e7a-205">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-205">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="17e7a-206">계산된 속성을 만들려면 해시 테이블을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="17e7a-206">To create a calculated, property, use a hash table.</span></span>

<span data-ttu-id="17e7a-207">유효한 키는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-207">Valid keys are:</span></span>

- <span data-ttu-id="17e7a-208">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="17e7a-208">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="17e7a-209">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="17e7a-209">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="17e7a-210">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17e7a-210">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="17e7a-211">-Skip</span><span class="sxs-lookup"><span data-stu-id="17e7a-211">-Skip</span></span>

<span data-ttu-id="17e7a-212">지정된 개수의 항목을 선택하지 않고 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-212">Skips (does not select) the specified number of items.</span></span> <span data-ttu-id="17e7a-213">**Skip** 매개 변수는 기본적으로 개체 목록 또는 배열의 처음부터 계산 하지만, 명령에서 **마지막** 매개 변수를 사용 하는 경우 목록 또는 배열의 끝부터 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-213">By default, the **Skip** parameter counts from the beginning of the array or list of objects, but if the command uses the **Last** parameter, it counts from the end of the list or array.</span></span>

<span data-ttu-id="17e7a-214">0에서 계산을 시작하는 **Index** 매개 변수와 달리 **Skip** 매개 변수는 1에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-214">Unlike the **Index** parameter, which starts counting at 0, the **Skip** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17e7a-215">-SkipLast</span><span class="sxs-lookup"><span data-stu-id="17e7a-215">-SkipLast</span></span>

<span data-ttu-id="17e7a-216">목록 또는 배열의 끝부터 지정 된 수의 항목을 건너뜁니다 (선택 하지 않음).</span><span class="sxs-lookup"><span data-stu-id="17e7a-216">Skips (does not select) the specified number of items from the end of the list or array.</span></span> <span data-ttu-id="17e7a-217">는 **마지막** 매개 변수와 함께 **Skip** 을 사용 하는 것과 동일한 방식으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-217">Works in the same way as using **Skip** together with **Last** parameter.</span></span>

<span data-ttu-id="17e7a-218">0에서 계산을 시작 하는 **인덱스** 매개 변수와 달리 **SkipLast** 매개 변수는 1부터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-218">Unlike the **Index** parameter, which starts counting at 0, the **SkipLast** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17e7a-219">-고유</span><span class="sxs-lookup"><span data-stu-id="17e7a-219">-Unique</span></span>

<span data-ttu-id="17e7a-220">입력 개체의 하위 집합 속성과 값이 동일한 경우 하위 집합의 멤버 하나만 선택되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-220">Specifies that if a subset of the input objects has identical properties and values, only a single member of the subset will be selected.</span></span>

<span data-ttu-id="17e7a-221">이 매개 변수는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-221">This parameter is case-sensitive.</span></span> <span data-ttu-id="17e7a-222">따라서 문자의 대/소문자만 다른 문자열은 고유한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-222">As a result, strings that differ only in character casing are considered to be unique.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17e7a-223">-Wait</span><span class="sxs-lookup"><span data-stu-id="17e7a-223">-Wait</span></span>

<span data-ttu-id="17e7a-224">Cmdlet이 최적화를 해제 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-224">Indicates that the cmdlet turns off optimization.</span></span> <span data-ttu-id="17e7a-225">PowerShell은 명령 파이프라인에 나타나는 순서 대로 명령을 실행 하 고 모든 개체를 생성할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-225">PowerShell runs commands in the order that they appear in the command pipeline and lets them generate all objects.</span></span> <span data-ttu-id="17e7a-226">기본적으로 명령 `Select-Object` 파이프라인에 **첫 번째** 또는 **인덱스** 매개 변수를 사용 하 여 명령을 포함 하는 경우 PowerShell은 선택한 개체 수가 생성 되는 즉시 개체를 생성 하는 명령을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-226">By default, if you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated.</span></span>

<span data-ttu-id="17e7a-227">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17e7a-228">-SkipIndex</span><span class="sxs-lookup"><span data-stu-id="17e7a-228">-SkipIndex</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17e7a-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="17e7a-229">CommonParameters</span></span>

<span data-ttu-id="17e7a-230">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="17e7a-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="17e7a-231">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17e7a-231">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="17e7a-232">입력</span><span class="sxs-lookup"><span data-stu-id="17e7a-232">INPUTS</span></span>

### <span data-ttu-id="17e7a-233">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="17e7a-233">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="17e7a-234">모든 개체를로 파이프 할 수 있습니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-234">You can pipe any object to `Select-Object`.</span></span>

## <span data-ttu-id="17e7a-235">출력</span><span class="sxs-lookup"><span data-stu-id="17e7a-235">OUTPUTS</span></span>

### <span data-ttu-id="17e7a-236">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="17e7a-236">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="17e7a-237">참고</span><span class="sxs-lookup"><span data-stu-id="17e7a-237">NOTES</span></span>

- <span data-ttu-id="17e7a-238">또한 `Select-Object` 해당 기본 제공 별칭인에서 cmdlet을 참조할 수 있습니다 `select` .</span><span class="sxs-lookup"><span data-stu-id="17e7a-238">You can also refer to the `Select-Object` cmdlet by its built-in alias, `select`.</span></span> <span data-ttu-id="17e7a-239">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17e7a-239">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

- <span data-ttu-id="17e7a-240">의 최적화 기능은 `Select-Object` 개체를 처리할 때 파이프라인에 개체를 쓰는 명령에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-240">The optimization feature of `Select-Object` is available only for commands that write objects to the pipeline as they are processed.</span></span> <span data-ttu-id="17e7a-241">처리된 개체를 버퍼링하고 컬렉션으로 작성하는 명령에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-241">It has no effect on commands that buffer processed objects and write them as a collection.</span></span> <span data-ttu-id="17e7a-242">개체를 즉시 기록하는 것이 cmdlet 설계 모범 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="17e7a-242">Writing objects immediately is a cmdlet design best practice.</span></span> <span data-ttu-id="17e7a-243">자세한 내용은 [강력한 개발 지침](/powershell/scripting/developer/windows-powershell)에서 _파이프라인에 단일 레코드 쓰기_ 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17e7a-243">For more information, see _Write Single Records to the Pipeline_ in [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/windows-powershell).</span></span>

## <span data-ttu-id="17e7a-244">관련 링크</span><span class="sxs-lookup"><span data-stu-id="17e7a-244">RELATED LINKS</span></span>

[<span data-ttu-id="17e7a-245">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="17e7a-245">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="17e7a-246">Group-Object</span><span class="sxs-lookup"><span data-stu-id="17e7a-246">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="17e7a-247">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="17e7a-247">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="17e7a-248">Where-Object</span><span class="sxs-lookup"><span data-stu-id="17e7a-248">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
