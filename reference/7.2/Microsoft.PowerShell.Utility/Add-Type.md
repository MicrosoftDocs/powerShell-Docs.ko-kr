---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: d55925b0580542459e62e60108f855508232f232
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602243"
---
# <span data-ttu-id="bd266-102">Add-Type</span><span class="sxs-lookup"><span data-stu-id="bd266-102">Add-Type</span></span>

## <span data-ttu-id="bd266-103">개요</span><span class="sxs-lookup"><span data-stu-id="bd266-103">SYNOPSIS</span></span>
<span data-ttu-id="bd266-104">PowerShell 세션에 Microsoft .NET Core 클래스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-104">Adds a Microsoft .NET Core class to a PowerShell session.</span></span>

## <span data-ttu-id="bd266-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bd266-105">SYNTAX</span></span>

### <span data-ttu-id="bd266-106">FromSource (기본값)</span><span class="sxs-lookup"><span data-stu-id="bd266-106">FromSource (Default)</span></span>

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="bd266-107">FromMember</span><span class="sxs-lookup"><span data-stu-id="bd266-107">FromMember</span></span>

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="bd266-108">FromPath</span><span class="sxs-lookup"><span data-stu-id="bd266-108">FromPath</span></span>

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="bd266-109">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="bd266-109">FromLiteralPath</span></span>

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="bd266-110">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="bd266-110">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="bd266-111">설명</span><span class="sxs-lookup"><span data-stu-id="bd266-111">DESCRIPTION</span></span>

<span data-ttu-id="bd266-112">`Add-Type`Cmdlet을 사용 하 여 PowerShell 세션에서 Microsoft .NET Core 클래스를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-112">The `Add-Type` cmdlet lets you define a Microsoft .NET Core class in your PowerShell session.</span></span> <span data-ttu-id="bd266-113">그런 다음 cmdlet을 사용 하 여 개체를 인스턴스화하고 `New-Object` .Net Core 개체를 사용 하는 것 처럼 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-113">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Core object.</span></span> <span data-ttu-id="bd266-114">`Add-Type`Powershell 프로필에 명령을 추가 하는 경우 클래스는 모든 powershell 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-114">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="bd266-115">기존 어셈블리 또는 소스 코드 파일을 지정하여 유형을 지정할 수도 있고 인라인 또는 변수에 저장된 소스 코드를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-115">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="bd266-116">메서드만 지정 하 고 `Add-Type` 클래스를 정의 하 고 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-116">You can even specify only a method and `Add-Type` defines and generates the class.</span></span> <span data-ttu-id="bd266-117">Windows에서는이 기능을 사용 하 여 PowerShell의 관리 되지 않는 함수에 대 한 플랫폼 호출 (P/Invoke)을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-117">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="bd266-118">소스 코드를 지정 하는 경우는 `Add-Type` 지정 된 소스 코드를 컴파일하고 새 .Net Core 형식이 포함 된 메모리 내 어셈블리를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-118">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Core types.</span></span>

<span data-ttu-id="bd266-119">의 매개 변수를 사용 `Add-Type` 하 여 대체 언어 및 컴파일러를 지정할 수 있습니다. c #은 기본값, 컴파일러 옵션, 어셈블리 종속성, 클래스 네임 스페이스, 형식 이름 및 결과 어셈블리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-119">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

<span data-ttu-id="bd266-120">PowerShell 7부터 `Add-Type` 같은 이름의 형식이 이미 있는 경우는 형식을 컴파일하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-120">Beginning in PowerShell 7, `Add-Type` does not compile a type if a type with the same name already exists.</span></span> <span data-ttu-id="bd266-121">또한는가 `Add-Type` `ref` 포함 된 폴더의 폴더에서 어셈블리를 찾습니다 `pwsh.dll` .</span><span class="sxs-lookup"><span data-stu-id="bd266-121">Also, `Add-Type` looks for assemblies in a `ref` folder under the folder that contains `pwsh.dll`.</span></span>

## <span data-ttu-id="bd266-122">예제</span><span class="sxs-lookup"><span data-stu-id="bd266-122">EXAMPLES</span></span>

### <span data-ttu-id="bd266-123">예제 1: 세션에 .NET 형식 추가</span><span class="sxs-lookup"><span data-stu-id="bd266-123">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="bd266-124">이 예제에서는 변수에 저장 된 소스 코드를 지정 하 여 **Basictest** 클래스를 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-124">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="bd266-125">**Basictest** 클래스는 정수를 추가 하 고, 개체를 만들고, 정수를 곱하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-125">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

<span data-ttu-id="bd266-126">`$Source`변수는 클래스에 대 한 소스 코드를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-126">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="bd266-127">형식에 라는 정적 메서드와 `Add` 비정적 메서드가 `Multiply` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-127">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="bd266-128">`Add-Type`Cmdlet은 세션에 클래스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-128">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="bd266-129">이 명령은 인라인 소스 코드를 사용 하기 때문에 **Typedefinition** 매개 변수를 사용 하 여 변수의 코드를 지정 합니다 `$Source` .</span><span class="sxs-lookup"><span data-stu-id="bd266-129">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="bd266-130">`Add` **Basictest** 클래스의 정적 메서드는 이중 콜론 문자 ()를 사용 `::` 하 여 클래스의 정적 멤버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-130">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="bd266-131">정수가 추가 되 고 합계가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-131">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="bd266-132">`New-Object`Cmdlet은 **basictest** 클래스의 인스턴스를 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-132">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="bd266-133">새 개체를 `$BasicTestObject` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-133">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="bd266-134">`$BasicTestObject` 메서드를 사용 `Multiply` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-134">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="bd266-135">정수가 곱하고 제품이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-135">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="bd266-136">예제 2: 추가 된 형식 검사</span><span class="sxs-lookup"><span data-stu-id="bd266-136">Example 2: Examine an added type</span></span>

<span data-ttu-id="bd266-137">이 예에서는 cmdlet을 사용 하 여 `Get-Member` `Add-Type` 및 `New-Object` cmdlet이 **예제 1** 에서 만든 개체를 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-137">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1**.</span></span>

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

<span data-ttu-id="bd266-138">`Get-Member`Cmdlet은 세션에 추가 된 **basictest** 클래스의 형식 및 멤버를 가져옵니다 `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="bd266-138">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="bd266-139">`Get-Member`이 명령은 **system.object** 클래스에서 파생 된 **system.environment 아니라 system.runtimetype** 개체 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-139">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="bd266-140">`Get-Member` **정적** 매개 변수는 **basictest** 클래스의 정적 속성 및 메서드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-140">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="bd266-141">출력은 `Add` 메서드가 포함 되어 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-141">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="bd266-142">`Get-Member`Cmdlet은 변수에 저장 된 개체의 멤버를 가져옵니다 `$BasicTestObject` .</span><span class="sxs-lookup"><span data-stu-id="bd266-142">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="bd266-143">`$BasicTestObject` 는 `New-Object` **basictest** 클래스와 함께 cmdlet을 사용 하 여 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-143">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="bd266-144">출력에는 `$BasicTestObject` 변수의 값이 **basictest** 클래스의 인스턴스이고 라는 멤버가 포함 되어 있음을 알 수 `Multiply` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-144">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="bd266-145">예제 3: 어셈블리에서 형식 추가</span><span class="sxs-lookup"><span data-stu-id="bd266-145">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="bd266-146">이 예제에서는 어셈블리의 클래스를 `NJsonSchema.dll` 현재 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-146">This example adds the classes from the `NJsonSchema.dll` assembly to the current session.</span></span>

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

<span data-ttu-id="bd266-147">`Set-Location`**Path** 매개 변수를 사용 하 여 `$PSHOME` 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-147">`Set-Location` uses the **Path** parameter to specify the `$PSHOME` variable.</span></span> <span data-ttu-id="bd266-148">변수는 DLL 파일이 있는 PowerShell 설치 디렉터리를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-148">The variable references the PowerShell installation directory where the DLL file is located.</span></span>

<span data-ttu-id="bd266-149">`$AccType`변수는 cmdlet을 사용 하 여 만든 개체를 저장 `Add-Type` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-149">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="bd266-150">`Add-Type`**AssemblyName** 매개 변수를 사용 하 여 어셈블리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-150">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="bd266-151">별표 ( `*` ) 와일드 카드 문자를 사용 하면 이름이 나 철자를 잘 모르는 경우에도 올바른 어셈블리를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-151">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="bd266-152">**PassThru** 매개 변수는 세션에 추가 된 클래스를 나타내는 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-152">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="bd266-153">예제 4: 네이티브 Windows Api 호출</span><span class="sxs-lookup"><span data-stu-id="bd266-153">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="bd266-154">이 예제에서는 PowerShell에서 네이티브 Windows Api를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-154">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="bd266-155">`Add-Type` 플랫폼 호출 (P/Invoke) 메커니즘을 사용 하 여 PowerShell에서의 함수를 호출 `User32.dll` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-155">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="bd266-156">이 예제는 Windows 운영 체제를 실행 하는 컴퓨터 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-156">This example only works on computers running the Windows operating system.</span></span>

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

<span data-ttu-id="bd266-157">`$Signature`변수는 함수의 c # 시그니처를 저장 합니다 `ShowWindowAsync` .</span><span class="sxs-lookup"><span data-stu-id="bd266-157">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="bd266-158">결과 메서드가 PowerShell 세션에서 표시 되도록 하려면 `public` 키워드가 표준 서명에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-158">To ensure that the resulting method is visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="bd266-159">자세한 내용은 [Showwindowasync 함수](/windows/win32/api/winuser/nf-winuser-showwindowasync)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bd266-159">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="bd266-160">`$ShowWindowAsync`변수는 `Add-Type` **PassThru** 매개 변수에 의해 생성 된 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-160">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="bd266-161">`Add-Type`Cmdlet은 함수를 `ShowWindowAsync` PowerShell 세션에 정적 메서드로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-161">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="bd266-162">이 명령은 **memberdefinition** 매개 변수를 사용 하 여 변수에 저장 된 메서드 정의를 지정 합니다 `$Signature` .</span><span class="sxs-lookup"><span data-stu-id="bd266-162">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="bd266-163">이 명령은 **Name** 및 **Namespace** 매개 변수를 사용하여 클래스의 이름 및 네임스페이스를 지정하고,</span><span class="sxs-lookup"><span data-stu-id="bd266-163">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="bd266-164">**PassThru** 매개 변수는 형식을 나타내는 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-164">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="bd266-165">새 `ShowWindowAsync` 정적 메서드는 PowerShell 콘솔을 최소화 하 고 복원 하는 명령에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-165">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="bd266-166">이 메서드는 창 핸들과 창 표시 방법을 지정 하는 정수의 두 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-166">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="bd266-167">PowerShell 콘솔을 최소화 하기 위해에서는 `ShowWindowAsync` `Get-Process` 자동 변수와 함께 cmdlet을 사용 하 여 `$PID` 현재 PowerShell 세션을 호스트 하는 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-167">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="bd266-168">그런 다음 현재 프로세스의 **MainWindowHandle** 속성을 사용 하 고 값을 나타내는 값을 사용 `2` `SW_MINIMIZE` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-168">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="bd266-169">창을 복원 하기 위해는 `ShowWindowAsync` `4` 값을 나타내는 창 위치에 값을 사용 `SW_RESTORE` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-169">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="bd266-170">창을 최대화 하려면를 나타내는 값을 사용 `3` `SW_MAXIMIZE` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-170">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

## <span data-ttu-id="bd266-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd266-171">PARAMETERS</span></span>

### <span data-ttu-id="bd266-172">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="bd266-172">-AssemblyName</span></span>

<span data-ttu-id="bd266-173">해당 유형을 포함하는 어셈블리 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-173">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="bd266-174">`Add-Type` 지정 된 어셈블리의 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-174">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="bd266-175">이 매개 변수는 어셈블리 이름을 기반으로 형식을 만들 때 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-175">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="bd266-176">어셈블리의 전체 이름 또는 단순한 이름 (부분 이름이 라고도 함)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-176">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="bd266-177">어셈블리 이름에는 와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-177">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="bd266-178">단순 이름 또는 부분 이름을 입력 하면에서 `Add-Type` 전체 이름으로 확인 한 다음 전체 이름을 사용 하 여 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-178">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="bd266-179">이 매개 변수는 경로 또는 파일 이름을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-179">This parameter doesn't accept a path or a filename.</span></span> <span data-ttu-id="bd266-180">어셈블리 DLL (동적 연결 라이브러리) 파일에 대 한 경로를 입력 하려면 **path** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-180">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bd266-181">-CompilerOptions</span><span class="sxs-lookup"><span data-stu-id="bd266-181">-CompilerOptions</span></span>

<span data-ttu-id="bd266-182">소스 코드 컴파일러에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-182">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="bd266-183">이 옵션은 수정 없이 컴파일러로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-183">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="bd266-184">이 매개 변수를 사용 하면 실행 파일을 생성 하거나, 리소스를 포함 하거나, 옵션과 같은 명령줄 옵션을 설정 하도록 컴파일러에 지시할 수 있습니다 `/unsafe` .</span><span class="sxs-lookup"><span data-stu-id="bd266-184">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span>

<span data-ttu-id="bd266-185">동일한 명령에서 **CompilerOptions** 및 **referencedassemblies** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-185">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-186">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="bd266-186">-IgnoreWarnings</span></span>

<span data-ttu-id="bd266-187">컴파일러 경고를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-187">Ignores compiler warnings.</span></span> <span data-ttu-id="bd266-188">이 매개 변수를 사용 하 여 `Add-Type` 컴파일러 경고를 오류로 처리 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-188">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-189">-언어</span><span class="sxs-lookup"><span data-stu-id="bd266-189">-Language</span></span>

<span data-ttu-id="bd266-190">소스 코드에서 사용된 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-190">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="bd266-191">이 매개 변수에 허용 되는 값은 **CSharp** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-191">The acceptable value for this parameter is **CSharp**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-192">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bd266-192">-LiteralPath</span></span>

<span data-ttu-id="bd266-193">해당 유형이 포함된 소스 코드 파일 또는 어셈블리 DLL 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-193">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="bd266-194">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-194">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="bd266-195">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-195">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="bd266-196">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="bd266-196">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="bd266-197">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-197">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-198">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="bd266-198">-MemberDefinition</span></span>

<span data-ttu-id="bd266-199">클래스의 새 속성 또는 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-199">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="bd266-200">`Add-Type` 속성이 나 메서드를 지 원하는 데 필요한 템플릿 코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-200">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="bd266-201">Windows에서는이 기능을 사용 하 여 PowerShell의 관리 되지 않는 함수에 대 한 플랫폼 호출 (P/Invoke)을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-201">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-202">-Name</span><span class="sxs-lookup"><span data-stu-id="bd266-202">-Name</span></span>

<span data-ttu-id="bd266-203">만들 클래스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-203">Specifies the name of the class to create.</span></span> <span data-ttu-id="bd266-204">멤버 정의에서 유형을 생성하는 경우 이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-204">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="bd266-205">유형 이름 및 네임스페이스는 세션 내부에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-205">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="bd266-206">유형을 언로드하거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-206">You can't unload a type or change it.</span></span>
<span data-ttu-id="bd266-207">형식에 대 한 코드를 변경 하려면 이름을 변경 하거나 새 PowerShell 세션을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-207">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="bd266-208">그러지 않으면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-208">Otherwise, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-209">-Namespace</span><span class="sxs-lookup"><span data-stu-id="bd266-209">-Namespace</span></span>

<span data-ttu-id="bd266-210">유형의 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-210">Specifies a namespace for the type.</span></span>

<span data-ttu-id="bd266-211">이 매개 변수가 명령에 포함 되지 않은 경우 형식은 **Microsoft. PowerShell. AddType. AutoGeneratedTypes** 네임 스페이스에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-211">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="bd266-212">매개 변수가 명령에 빈 문자열 값 또는 값으로 포함 되어 있으면 `$Null` 해당 형식이 전역 네임 스페이스에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-212">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-213">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="bd266-213">-OutputAssembly</span></span>

<span data-ttu-id="bd266-214">어셈블리에 대한 DLL 파일을 해당 위치에 지정된 이름으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-214">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="bd266-215">선택적 경로와 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-215">Enter an optional path and filename.</span></span> <span data-ttu-id="bd266-216">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-216">Wildcard characters are permitted.</span></span> <span data-ttu-id="bd266-217">기본적으로는 `Add-Type` 메모리에만 어셈블리를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-217">By default, `Add-Type` generates the assembly only in memory.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bd266-218">-OutputType</span><span class="sxs-lookup"><span data-stu-id="bd266-218">-OutputType</span></span>

<span data-ttu-id="bd266-219">출력 어셈블리의 출력 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-219">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="bd266-220">기본적으로 출력 유형은 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-220">By default, no output type is specified.</span></span> <span data-ttu-id="bd266-221">이 매개 변수는 명령에서 출력 어셈블리를 지정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-221">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="bd266-222">값에 대 한 자세한 내용은 [Outputassemblytype 열거](/dotnet/api/microsoft.powershell.commands.outputassemblytype)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bd266-222">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="bd266-223">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-223">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bd266-224">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="bd266-224">ConsoleApplication</span></span>
- <span data-ttu-id="bd266-225">라이브러리</span><span class="sxs-lookup"><span data-stu-id="bd266-225">Library</span></span>
- <span data-ttu-id="bd266-226">Windowsapplication.zip</span><span class="sxs-lookup"><span data-stu-id="bd266-226">WindowsApplication</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd266-227">PowerShell 7.1에서 `ConsoleApplication` 및 `WindowsApplication` 은 지원 되지 않으며, **OutputType** 매개 변수에 대 한 값으로 지정 된 경우 powershell에서 종료 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-227">As of PowerShell 7.1, `ConsoleApplication` and `WindowsApplication` are not supported and PowerShell throws a terminating error if either are specified as values for the **OutputType** parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-228">-PassThru</span><span class="sxs-lookup"><span data-stu-id="bd266-228">-PassThru</span></span>

<span data-ttu-id="bd266-229">추가된 유형을 나타내는 **System.Runtime** 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-229">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="bd266-230">기본적으로이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-230">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-231">-Path</span><span class="sxs-lookup"><span data-stu-id="bd266-231">-Path</span></span>

<span data-ttu-id="bd266-232">해당 유형이 포함된 소스 코드 파일 또는 어셈블리 DLL 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-232">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="bd266-233">소스 코드 파일을 제출 하는 경우는 `Add-Type` 파일의 코드를 컴파일하고 형식의 메모리 내 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-233">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="bd266-234">**Path** 값에 지정 된 파일 확장명은를 사용 하는 컴파일러를 결정 합니다 `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="bd266-234">The file extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="bd266-235">어셈블리 파일을 제출 하는 경우는 `Add-Type` 어셈블리의 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-235">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="bd266-236">메모리 내 어셈블리 또는 전역 어셈블리 캐시를 지정하려면 **AssemblyName** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-236">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-237">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="bd266-237">-ReferencedAssemblies</span></span>

<span data-ttu-id="bd266-238">유형이 종속된 어셈블리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-238">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="bd266-239">기본적으로는 `Add-Type` 및를 참조 `System.dll` `System.Management.Automation.dll` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-239">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="bd266-240">이 매개 변수를 사용하여 지정하는 어셈블리는 기본 어셈블리에 추가하여 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-240">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="bd266-241">PowerShell 6부터 **Referencedassemblies** 는 기본 .net 어셈블리를 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-241">Beginning in PowerShell 6, **ReferencedAssemblies** doesn't include the default .NET assemblies.</span></span> <span data-ttu-id="bd266-242">이 매개 변수에 전달 된 값에이에 대 한 특정 참조를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-242">You must include a specific reference to them in the value passed to this parameter.</span></span>

<span data-ttu-id="bd266-243">동일한 명령에서 **CompilerOptions** 및 **referencedassemblies** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-243">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-244">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="bd266-244">-TypeDefinition</span></span>

<span data-ttu-id="bd266-245">유형 정의가 포함된 소스 코드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-245">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="bd266-246">소스 코드를 문자열 또는 here-string으로 입력하거나 소스 코드가 포함된 변수를 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="bd266-246">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="bd266-247">이러한 문자열에 대 한 자세한 내용은 [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bd266-247">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="bd266-248">유형 정의에 네임스페이스 선언을 포함하세요.</span><span class="sxs-lookup"><span data-stu-id="bd266-248">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="bd266-249">네임스페이스 선언을 누락하면 유형 이름이 다른 유형 또는 다른 유형의 바로 가기 이름과 같아져서 해당 유형을 덮어쓰는 일이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-249">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="bd266-250">예를 들어 **exception** 이라는 형식을 정의 하는 경우 exception을 위한 바로 가기로 **예외** 를 사용 하는 **스크립트는 실패** 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-250">For example, if you define a type called **Exception**, scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-251">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="bd266-251">-UsingNamespace</span></span>

<span data-ttu-id="bd266-252">클래스에 필요한 다른 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-252">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="bd266-253">이는 c # 키워드인와 매우 비슷합니다 `Using` .</span><span class="sxs-lookup"><span data-stu-id="bd266-253">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="bd266-254">기본적으로 `Add-Type` 은 **System** 네임 스페이스를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-254">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="bd266-255">**Memberdefinition** 매개 변수를 사용 하는 경우은 `Add-Type` 기본적으로 **t e m** 네임 스페이스를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-255">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="bd266-256">**UsingNamespace** 매개 변수를 사용하여 추가한 네임스페이스는 기본 네임스페이스에 추가로 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-256">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd266-257">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd266-257">CommonParameters</span></span>

<span data-ttu-id="bd266-258">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd266-258">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd266-259">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd266-259">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd266-260">입력</span><span class="sxs-lookup"><span data-stu-id="bd266-260">INPUTS</span></span>

### <span data-ttu-id="bd266-261">없음</span><span class="sxs-lookup"><span data-stu-id="bd266-261">None</span></span>

<span data-ttu-id="bd266-262">파이프라인에서로 개체를 보낼 수 없습니다 `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="bd266-262">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="bd266-263">출력</span><span class="sxs-lookup"><span data-stu-id="bd266-263">OUTPUTS</span></span>

### <span data-ttu-id="bd266-264">없음 또는 System.object</span><span class="sxs-lookup"><span data-stu-id="bd266-264">None or System.Type</span></span>

<span data-ttu-id="bd266-265">**PassThru** 매개 변수를 사용 하는 경우는 `Add-Type` 새 형식을 나타내는 **system.object** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-265">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="bd266-266">그렇지 않으면이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-266">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="bd266-267">참고</span><span class="sxs-lookup"><span data-stu-id="bd266-267">NOTES</span></span>

<span data-ttu-id="bd266-268">추가한 유형은 현재 세션에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-268">The types that you add exist only in the current session.</span></span> <span data-ttu-id="bd266-269">모든 세션에서 형식을 사용 하려면 PowerShell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-269">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="bd266-270">프로필에 대 한 자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bd266-270">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="bd266-271">형식 이름 및 네임 스페이스는 세션 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-271">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="bd266-272">유형을 언로드하거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-272">You can't unload a type or change it.</span></span> <span data-ttu-id="bd266-273">형식에 대 한 코드를 변경 해야 하는 경우 이름을 변경 하거나 새 PowerShell 세션을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-273">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="bd266-274">그러지 않으면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-274">Otherwise, the command fails.</span></span>

<span data-ttu-id="bd266-275">Windows PowerShell (버전 5.1이 하)에서 `Add-Type` 아직 로드 되지 않은 모든 항목에 대해을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-275">In Windows PowerShell (version 5.1 and below), you need to use `Add-Type` for anything that isn't already loaded.</span></span> <span data-ttu-id="bd266-276">가장 일반적으로이는 GAC (전역 어셈블리 캐시)에 있는 어셈블리에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-276">Most commonly, this applies to assemblies found in the Global Assembly Cache (GAC).</span></span>
<span data-ttu-id="bd266-277">PowerShell 6 이상에서는 GAC가 없으므로 PowerShell에서 자체 어셈블리를 설치 `$PSHome` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-277">In PowerShell 6 and higher, there is no GAC, so PowerShell installs its own assemblies in `$PSHome`.</span></span>
<span data-ttu-id="bd266-278">이러한 어셈블리는 요청 시 자동으로 로드 되므로를 사용 하 여 로드할 필요가 없습니다 `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="bd266-278">These assemblies are automatically loaded on request, so there's no need to use `Add-Type` to load them.</span></span> <span data-ttu-id="bd266-279">그러나를 사용 하면 `Add-Type` 스크립트를 모든 버전의 PowerShell과 암시적으로 호환 되도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-279">However, using `Add-Type` is still permitted to allow scripts to be implicitly compatible with any version of PowerShell.</span></span>

<span data-ttu-id="bd266-280">GAC의 어셈블리는 경로 대신 형식 이름으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-280">Assemblies in the GAC can be loaded by type name, rather than by path.</span></span> <span data-ttu-id="bd266-281">임의 경로에서 어셈블리를 로드 하려면 `Add-Type` 이러한 어셈블리를 자동으로 로드할 수 없기 때문에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd266-281">Loading assemblies from an arbitrary path requires `Add-Type`, since those assemblies cannot not be loaded automatically.</span></span>

## <span data-ttu-id="bd266-282">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bd266-282">RELATED LINKS</span></span>

[<span data-ttu-id="bd266-283">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="bd266-283">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="bd266-284">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="bd266-284">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="bd266-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="bd266-285">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="bd266-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="bd266-286">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="bd266-287">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="bd266-287">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="bd266-288">P/Invoke(플랫폼 호출)</span><span class="sxs-lookup"><span data-stu-id="bd266-288">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="bd266-289">Where-Object</span><span class="sxs-lookup"><span data-stu-id="bd266-289">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
