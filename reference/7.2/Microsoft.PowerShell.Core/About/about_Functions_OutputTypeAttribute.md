---
description: 함수가 반환하는 개체의 형식을 보고하는 특성에 대해 설명합니다.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 82f1615c4a2fe2a24f104d8e5637103dea6e5a0a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600453"
---
# <a name="about-functions-outputtypeattribute"></a><span data-ttu-id="bf12d-103">함수 OutputTypeAttribute 정보</span><span class="sxs-lookup"><span data-stu-id="bf12d-103">About Functions OutputTypeAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="bf12d-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="bf12d-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="bf12d-105">함수가 반환하는 개체의 형식을 보고하는 특성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-105">Describes an attribute that reports the type of object that the function returns.</span></span>

## <a name="long-description"></a><span data-ttu-id="bf12d-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="bf12d-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="bf12d-107">OutputType 특성은 함수가 반환 하는 .NET 형식의 개체를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-107">The OutputType attribute lists the .NET types of objects that the functions returns.</span></span> <span data-ttu-id="bf12d-108">선택적 ParameterSetName 매개 변수를 사용 하 여 각 매개 변수 집합에 대해 서로 다른 출력 형식을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-108">You can use its optional ParameterSetName parameter to list different output types for each parameter set.</span></span>

<span data-ttu-id="bf12d-109">OutputType 특성은 단순 함수와 고급 함수에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-109">The OutputType attribute is supported on simple and advanced functions.</span></span> <span data-ttu-id="bf12d-110">CmdletBinding 특성에 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-110">It is independent of the CmdletBinding attribute.</span></span>

<span data-ttu-id="bf12d-111">OutputType 특성은 cmdlet이 반환 하는 **system.object** 개체의 OutputType 속성 값을 제공 합니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="bf12d-111">The OutputType attribute provides the value of the OutputType property of the **System.Management.Automation.FunctionInfo** object that the `Get-Command` cmdlet returns.</span></span>

<span data-ttu-id="bf12d-112">OutputType 특성 값은 문서 참고일뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-112">The OutputType attribute value is only a documentation note.</span></span> <span data-ttu-id="bf12d-113">함수 코드에서 파생 되거나 실제 함수 출력과 비교 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-113">It is not derived from the function code or compared to the actual function output.</span></span> <span data-ttu-id="bf12d-114">따라서 값이 정확 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-114">As such, the value might be inaccurate.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf12d-115">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bf12d-115">SYNTAX</span></span>

<span data-ttu-id="bf12d-116">함수의 OutputType 특성에는 다음 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-116">The OutputType attribute of functions has the following syntax:</span></span>

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

<span data-ttu-id="bf12d-117">**ParameterSetName** 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-117">The **ParameterSetName** parameter is optional.</span></span>

<span data-ttu-id="bf12d-118">OutputType 특성에 여러 형식을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-118">You can list multiple types in the OutputType attribute.</span></span>

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

<span data-ttu-id="bf12d-119">**ParameterSetName** 매개 변수를 사용 하 여 서로 다른 매개 변수 집합이 다른 형식을 반환 함을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-119">You can use the **ParameterSetName** parameter to indicate that different parameter sets return different types.</span></span>

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

<span data-ttu-id="bf12d-120">문 앞에 오는 특성 목록에 OutputType 특성 문을 추가 `Param` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-120">Place the OutputType attribute statements in the attributes list that precedes the `Param` statement.</span></span>

<span data-ttu-id="bf12d-121">다음 예에서는 간단한 함수에서 OutputType 특성을 배치 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-121">The following example shows the placement of the OutputType attribute in a simple function.</span></span>

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

<span data-ttu-id="bf12d-122">다음 예에서는 고급 함수에서 OutputType 특성을 배치 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-122">The following example shows the placement of the OutputType attribute in advanced functions.</span></span>

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a><span data-ttu-id="bf12d-123">예제</span><span class="sxs-lookup"><span data-stu-id="bf12d-123">EXAMPLES</span></span>

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a><span data-ttu-id="bf12d-124">예제 1: 문자열의 OutputType을 포함 하는 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="bf12d-124">Example 1: Create a function that has the OutputType of String</span></span>

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

<span data-ttu-id="bf12d-125">결과 출력 형식 속성을 보려면 cmdlet을 사용 합니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="bf12d-125">To see the resulting output type property, use the `Get-Command` cmdlet.</span></span>

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a><span data-ttu-id="bf12d-126">예제 2: 출력 특성을 사용 하 여 동적 출력 형식 표시</span><span class="sxs-lookup"><span data-stu-id="bf12d-126">Example 2: Use the Output attribute to indicate dynamic output types</span></span>

<span data-ttu-id="bf12d-127">다음 고급 함수는 OutputType 특성을 사용 하 여 함수가 함수 명령에 사용 되는 매개 변수 집합에 따라 다른 형식을 반환 함을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-127">The following advanced function uses the OutputType attribute to indicate that the function returns different types depending on the parameter set used in the function command.</span></span>

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a><span data-ttu-id="bf12d-128">예제 3: 실제 출력이 OutputType과 다를 때 표시</span><span class="sxs-lookup"><span data-stu-id="bf12d-128">Example 3: Shows when an actual output differs from the OutputType</span></span>

<span data-ttu-id="bf12d-129">다음 예에서는 출력 유형 속성 값이 잘못 된 경우에도 OutputType 특성의 값을 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-129">The following example demonstrates that the output type property value displays the value of the OutputType attribute, even when it is inaccurate.</span></span>

<span data-ttu-id="bf12d-130">`Get-Time`함수는 DateTime 개체의 짧은 시간 형식을 포함 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-130">The `Get-Time` function returns a string that contains the short form of the time in any DateTime object.</span></span> <span data-ttu-id="bf12d-131">그러나 OutputType 특성은 **system.web** 개체를 반환 한다는 것을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-131">However, the OutputType attribute reports that it returns a **System.DateTime** object.</span></span>

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

<span data-ttu-id="bf12d-132">`GetType()`메서드는 함수가 문자열을 반환 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-132">The `GetType()` method confirms that the function returns a string.</span></span>

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

<span data-ttu-id="bf12d-133">그러나 outputtype 특성에서 값을 가져오는 OutputType 속성은 함수가 **DateTime** 개체를 반환 하는지 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-133">However, the OutputType property, which gets its value from the OutputType attribute, reports that the function returns a **DateTime** object.</span></span>

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a><span data-ttu-id="bf12d-134">예제 4: 출력이 없어야 하는 함수</span><span class="sxs-lookup"><span data-stu-id="bf12d-134">Example 4: A function  that shouldn't have output</span></span>

<span data-ttu-id="bf12d-135">다음 예제에서는 및 동작을 수행 하지만 아무것도 반환 하지 않는 사용자 지정 함수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-135">The following example shows a custom function that should perform and action but not return anything.</span></span>

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a><span data-ttu-id="bf12d-136">참고</span><span class="sxs-lookup"><span data-stu-id="bf12d-136">NOTES</span></span>

<span data-ttu-id="bf12d-137">**Functioninfo** 개체의 OutputType 속성 값은 각각 Name 및 Type 속성을 가지는 **PSTypeName** 개체의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-137">The value of the OutputType property of a **FunctionInfo** object is an array of **System.Management.Automation.PSTypeName** objects, each of which have Name and Type properties.</span></span>

<span data-ttu-id="bf12d-138">각 출력 형식의 이름만 가져오려면 다음 형식의 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-138">To get only the name of each output type, use a command with the following format.</span></span>

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

<span data-ttu-id="bf12d-139">OutputType 속성의 값은 null 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-139">The value of the OutputType property can be null.</span></span> <span data-ttu-id="bf12d-140">**WMI** 개체 또는 개체의 형식이 지정 된 뷰와 같이 출력이 .net 형식이 아닌 경우 null 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf12d-140">Use a null value when the output is a not a .NET type, such as a **WMI** object or a formatted view of an object.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf12d-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf12d-141">SEE ALSO</span></span>

[<span data-ttu-id="bf12d-142">about_Functions</span><span class="sxs-lookup"><span data-stu-id="bf12d-142">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="bf12d-143">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="bf12d-143">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="bf12d-144">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="bf12d-144">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="bf12d-145">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="bf12d-145">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="bf12d-146">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="bf12d-146">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)
