---
description: 메서드를 사용 하 여 PowerShell에서 개체에 대 한 작업을 수행 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_methods
ms.openlocfilehash: 39ebd876b99d77d699c5026e298acc931b501382
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388946"
---
# <a name="about-methods"></a><span data-ttu-id="9f637-104">메서드 정보</span><span class="sxs-lookup"><span data-stu-id="9f637-104">About methods</span></span>

## <a name="short-description"></a><span data-ttu-id="9f637-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9f637-105">Short description</span></span>
<span data-ttu-id="9f637-106">메서드를 사용 하 여 PowerShell에서 개체에 대 한 작업을 수행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-106">Describes how to use methods to perform actions on objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="9f637-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-107">Long description</span></span>

<span data-ttu-id="9f637-108">PowerShell은 개체를 사용 하 여 데이터 저장소의 항목 또는 컴퓨터의 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-108">PowerShell uses objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="9f637-109">예를 들어, FileInfo 개체는 파일 시스템 드라이브의 파일을 나타내고 ProcessInfo 개체는 컴퓨터의 프로세스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-109">For example, FileInfo objects represent the files in file system drives and ProcessInfo objects represent the processes on the computer.</span></span>

<span data-ttu-id="9f637-110">개체에는 개체에 대 한 데이터를 저장 하는 속성과 개체를 변경할 수 있는 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-110">Objects have properties, which store data about the object, and methods that let you change the object.</span></span>

<span data-ttu-id="9f637-111">"메서드"는 개체에서 수행할 수 있는 작업을 지정 하는 일련의 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-111">A "method" is a set of instructions that specify an action you can perform on the object.</span></span> <span data-ttu-id="9f637-112">예를 들어 개체에는 `FileInfo` `CopyTo` 개체가 나타내는 파일을 복사 하는 메서드가 포함 되어 있습니다 `FileInfo` .</span><span class="sxs-lookup"><span data-stu-id="9f637-112">For example, the `FileInfo` object includes the `CopyTo` method that copies the file that the `FileInfo` object represents.</span></span>

<span data-ttu-id="9f637-113">개체의 메서드를 가져오려면 cmdlet을 사용 합니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="9f637-113">To get the methods of any object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="9f637-114">값이 "Method" 인 **MemberType** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-114">Use its **MemberType** property with a value of "Method".</span></span> <span data-ttu-id="9f637-115">다음 명령은 개체를 처리 하는 메서드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-115">The following command gets the methods of process objects.</span></span>

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

<span data-ttu-id="9f637-116">개체의 메서드를 수행 하거나 "호출" 하려면 점 (.), 메서드 이름 및 괄호 ("()") 집합을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-116">To perform or "invoke" a method of an object, type a dot (.), the method name, and a set of parentheses "()".</span></span> <span data-ttu-id="9f637-117">메서드에 인수가 있는 경우 인수 값을 괄호 안에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-117">If the method has arguments, place the argument values inside the parentheses.</span></span> <span data-ttu-id="9f637-118">인수를 포함 하지 않는 경우에도 모든 메서드 호출에 괄호가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-118">The parentheses are required for every method call, even when there are no arguments.</span></span> <span data-ttu-id="9f637-119">메서드가 여러 인수를 사용 하는 경우 쉼표로 구분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-119">If the method takes multiple arguments, they should be separated by commas.</span></span>

<span data-ttu-id="9f637-120">예를 들어 다음 명령은 프로세스의 Kill 메서드를 호출 하 여 컴퓨터에서 메모장 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-120">For example, the following command invokes the Kill method of processes to end the Notepad process on the computer.</span></span>

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

<span data-ttu-id="9f637-121">위의 문을 결합 하 여이 예를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-121">This example can be shortened by combining the above statements.</span></span>

```powershell
(Get-Process Notepad).Kill()
```

<span data-ttu-id="9f637-122">`Get-Process`명령은 Kill 메서드를 호출 하기 전에 실행 되도록 괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-122">The `Get-Process` command is enclosed in parentheses to ensure that it runs before the Kill method is invoked.</span></span> <span data-ttu-id="9f637-123">`Kill`그런 다음 반환 된 개체에서 메서드를 호출 합니다 `Process` .</span><span class="sxs-lookup"><span data-stu-id="9f637-123">The `Kill` method is then invoked on the returned `Process` object.</span></span>

<span data-ttu-id="9f637-124">또 다른 유용한 방법은 `Replace` 문자열의 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-124">Another very useful method is the `Replace` method of strings.</span></span> <span data-ttu-id="9f637-125">`Replace`메서드는 문자열 내에서 텍스트를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-125">The `Replace` method, replaces text within a string.</span></span> <span data-ttu-id="9f637-126">아래 예제에서 점 (.)은 문자열의 끝 따옴표 바로 뒤에 배치 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-126">In the example below, the dot (.) can be placed immediately after the end quote of the string.</span></span>

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

<span data-ttu-id="9f637-127">앞의 예제와 같이 명령을 사용 하 여 가져온 개체에 대해 메서드를 호출 하거나, 변수의 개체를 사용 하거나, 개체를 생성 하는 모든 항목 (예: 인용 부호의 문자열)을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-127">As shown in the previous examples, you can invoke a method on an object that you get by using a command, an object in a variable, or anything that results in an object (like a string in quotes).</span></span>

<span data-ttu-id="9f637-128">PowerShell 4.0부터 동적 메서드 이름을 사용한 메서드 호출이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-128">Starting in PowerShell 4.0, method invocation by using dynamic method names is supported.</span></span>

### <a name="learning-about-methods"></a><span data-ttu-id="9f637-129">메서드 학습</span><span class="sxs-lookup"><span data-stu-id="9f637-129">Learning about methods</span></span>

<span data-ttu-id="9f637-130">개체의 메서드에 대 한 정의를 찾으려면 개체 형식에 대 한 도움말 항목으로 이동 하 여 해당 메서드 페이지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-130">To find definitions of the methods of an object, go to help topic for the object type and look for its methods page.</span></span> <span data-ttu-id="9f637-131">예를 들어 다음 페이지 [에서는 개체를](/dotnet/api/system.diagnostics.process#methods)처리 하는 프로세스의 메서드를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-131">For example, the following page describes the methods of process objects [System.Diagnostics.Process](/dotnet/api/system.diagnostics.process#methods).</span></span>

<span data-ttu-id="9f637-132">메서드의 인수를 확인 하려면 PowerShell cmdlet의 구문 다이어그램과 같은 메서드 정의를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-132">To determine the arguments of a method, review the method definition, which is like the syntax diagram of a PowerShell cmdlet.</span></span>

<span data-ttu-id="9f637-133">메서드 정의에는 PowerShell cmdlet의 매개 변수 집합과 같은 하나 이상의 메서드 서명이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-133">A method definition might have one or more method signatures, which are like the parameter sets of PowerShell cmdlets.</span></span> <span data-ttu-id="9f637-134">시그니처는 메서드를 호출 하는 명령에 대 한 모든 유효한 형식을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-134">The signatures show all of the valid formats of commands to invoke the method.</span></span>

<span data-ttu-id="9f637-135">예를 `CopyTo` 들어 클래스의 메서드에는 `FileInfo` 다음과 같은 두 가지 메서드 시그니처가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-135">For example, the `CopyTo` method of the `FileInfo` class contains the following two method signatures:</span></span>

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

<span data-ttu-id="9f637-136">첫 번째 메서드 시그니처는 대상 파일 이름 및 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-136">The first method signature takes the destination file name (and a path).</span></span> <span data-ttu-id="9f637-137">다음 예제에서는 첫 번째 메서드를 사용 하 여 `CopyTo` `Final.txt` 파일을 디렉터리에 복사 `C:\Bin` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-137">The following example uses the first `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> <span data-ttu-id="9f637-138">PowerShell의 _인수_ 모드와 달리 개체 메서드는 powershell이 빌드되는 .net framework에 대 한 통과 인 _식_ 모드에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-138">Unlike PowerShell's _argument_ mode, object methods execute in _expression_ mode, which is a pass-through to the .NET framework that PowerShell is built on.</span></span> <span data-ttu-id="9f637-139">_식_ 모드에서는 **bareword** 인수 (따옴표 붙지 않은 문자열)를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-139">In _expression_ mode **bareword** arguments (unquoted strings) are not allowed.</span></span> <span data-ttu-id="9f637-140">경로를 매개 변수로 사용 하 고 경로를 인수로 사용 하는 경우 이러한 차이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-140">You can see this difference when using a the path as a parameter, versus the path as an argument.</span></span> <span data-ttu-id="9f637-141">에서 구문 분석 모드에 대해 자세히 알아볼 수 있습니다 [about_Parsing](about_Parsing.md)</span><span class="sxs-lookup"><span data-stu-id="9f637-141">You can read more about parsing modes in [about_Parsing](about_Parsing.md)</span></span>

<span data-ttu-id="9f637-142">두 번째 메서드 시그니처는 대상 파일 이름 및 대상 파일을 덮어쓸지 여부를 결정 하는 부울 값 (이미 있는 경우)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-142">The second method signature takes a destination file name and a Boolean value that determines whether the destination file should be overwritten, if it already exists.</span></span>

<span data-ttu-id="9f637-143">다음 예제에서는 두 번째 방법을 사용 하 여 `CopyTo` `Final.txt` 디렉터리에 파일을 복사 하 `C:\Bin` 고 기존 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-143">The following example uses the second `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory, and to overwrite existing files.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a><span data-ttu-id="9f637-144">스칼라 개체 및 컬렉션의 메서드</span><span class="sxs-lookup"><span data-stu-id="9f637-144">Methods of Scalar objects and Collections</span></span>

<span data-ttu-id="9f637-145">특정 형식의 한 ("스칼라") 개체의 메서드는 일반적으로 동일한 형식의 개체 컬렉션 메서드와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-145">The methods of one ("scalar") object of a particular type are often different from the methods of a collection of objects of the same type.</span></span>

<span data-ttu-id="9f637-146">예를 들어 모든 프로세스에는 `Kill` 메서드가 있지만 프로세스 컬렉션에는 Kill 메서드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-146">For example, every process has a `Kill` method, but a collection of processes does not have a Kill method.</span></span>

<span data-ttu-id="9f637-147">PowerShell 3.0부터 PowerShell은 스칼라 개체 및 컬렉션의 다른 방법으로 인해 발생 하는 스크립팅 오류를 방지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-147">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing methods of scalar objects and collections.</span></span>

<span data-ttu-id="9f637-148">컬렉션을 제출 하지만 단일 ("스칼라") 개체에만 존재 하는 메서드를 요청 하는 경우 PowerShell은 컬렉션의 모든 개체에 대해 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-148">If you submit a collection, but request a method that exists only on single ("scalar") objects, PowerShell invokes the method on every object in the collection.</span></span>

<span data-ttu-id="9f637-149">메서드가 개별 개체 및 컬렉션에 있으면 컬렉션의 메서드만 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-149">If the method exists on the individual objects and on the collection, only the collection's method is invoked.</span></span>

<span data-ttu-id="9f637-150">이 기능은 스칼라 개체 및 컬렉션의 속성에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-150">This feature also works on properties of scalar objects and collections.</span></span> <span data-ttu-id="9f637-151">자세한 내용은 [about_Properties](about_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9f637-151">For more information, see [about_Properties](about_Properties.md).</span></span>

### <a name="examples"></a><span data-ttu-id="9f637-152">예</span><span class="sxs-lookup"><span data-stu-id="9f637-152">Examples</span></span>

<span data-ttu-id="9f637-153">다음 예제에서는 개체의 컬렉션에 있는 개별 프로세스 개체의 **Kill** 메서드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-153">The following example runs the **Kill** method of individual process objects in a collection of objects.</span></span>

<span data-ttu-id="9f637-154">첫 번째 명령은 메모장 프로세스의 세 가지 인스턴스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-154">The first command starts three instances of the Notepad process.</span></span> <span data-ttu-id="9f637-155">`Get-Process` 메모장 프로세스의 세 인스턴스를 모두 가져온 다음 `$p` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-155">`Get-Process` gets all three instance of the Notepad process and saves them in the `$p` variable.</span></span>

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

<span data-ttu-id="9f637-156">다음 명령은 변수의 세 프로세스 모두에서 **Kill** 메서드를 실행 합니다 `$p` .</span><span class="sxs-lookup"><span data-stu-id="9f637-156">The next command runs the **Kill** method on all three processes in the `$p` variable.</span></span> <span data-ttu-id="9f637-157">이 명령은 프로세스 컬렉션에 메서드가 없는 경우에도 작동 `Kill` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-157">This command works even though a collection of processes does not have a `Kill` method.</span></span>

```powershell
$p.Kill()
Get-Process Notepad
```

<span data-ttu-id="9f637-158">`Get-Process`명령은 메서드가 작동 하는지 확인 합니다 `Kill` .</span><span class="sxs-lookup"><span data-stu-id="9f637-158">The `Get-Process` command confirms that the `Kill` method worked.</span></span>

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

<span data-ttu-id="9f637-159">이 예제는 cmdlet을 사용 하 여 `Foreach-Object` 컬렉션의 각 개체에 대해 메서드를 실행 하는 것과 기능적으로 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-159">This example is functionally equivalent to using the `Foreach-Object` cmdlet to run the method on each object in the collection.</span></span>

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a><span data-ttu-id="9f637-160">ForEach 및 Where 메서드</span><span class="sxs-lookup"><span data-stu-id="9f637-160">ForEach and Where methods</span></span>

<span data-ttu-id="9f637-161">PowerShell 4.0부터 메서드 구문을 사용한 컬렉션 필터링이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-161">Beginning in PowerShell 4.0, collection filtering by using a method syntax is supported.</span></span> <span data-ttu-id="9f637-162">이를 통해 컬렉션 및를 처리할 때 두 가지 새로운 메서드를 사용할 수 있습니다 `ForEach` `Where` .</span><span class="sxs-lookup"><span data-stu-id="9f637-162">This allows use of two new methods when dealing with collections `ForEach` and `Where`.</span></span>

<span data-ttu-id="9f637-163">[about_arrays](about_arrays.md)의 이 메서드에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-163">You can read more about these methods in [about_arrays](about_arrays.md)</span></span>

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a><span data-ttu-id="9f637-164">여러 오버 로드가 있는 경우 특정 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="9f637-164">Calling a specific method when multiple overloads exist</span></span>

<span data-ttu-id="9f637-165">.NET 메서드를 호출할 때 다음 시나리오를 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f637-165">Consider the following scenario when calling .NET methods.</span></span> <span data-ttu-id="9f637-166">메서드가 개체를 사용 하지만 더 구체적인 형식을 사용 하는 인터페이스를 통해 오버 로드가 있는 경우 PowerShell은 해당 인터페이스로 명시적으로 캐스팅 하지 않는 한 개체를 허용 하는 메서드를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-166">If a method takes an object but has an overload via an interface taking a more specific type, PowerShell chooses the method that accepts the object unless you explicitly cast it to that interface.</span></span>

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

<span data-ttu-id="9f637-167">이 예제에서는 `object` **Bar** 메서드의 오버 로드가 더 이상 선택 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-167">In this example the less specific `object` overload of the **Bar** method was chosen.</span></span>

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

<span data-ttu-id="9f637-168">이 예제에서는 메서드를 interface **IFoo** 로 캐스팅 하 여 **Bar** 메서드의 구체적인 오버 로드를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f637-168">In this example we cast the method to the interface **IFoo** to select the more specific overload of the **Bar** method.</span></span>

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a><span data-ttu-id="9f637-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f637-169">See Also</span></span>

[<span data-ttu-id="9f637-170">about_Objects</span><span class="sxs-lookup"><span data-stu-id="9f637-170">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="9f637-171">about_Properties</span><span class="sxs-lookup"><span data-stu-id="9f637-171">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="9f637-172">Get-Member</span><span class="sxs-lookup"><span data-stu-id="9f637-172">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
