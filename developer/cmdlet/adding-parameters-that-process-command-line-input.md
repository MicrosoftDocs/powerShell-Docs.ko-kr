---
title: 명령줄 입력을 처리 하는 매개 변수 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: e010e28ec705932063bb418b260a1087fc3eef9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856009"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="a5b60-102">명령줄 입력을 처리하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="a5b60-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="a5b60-103">소스 cmdlet에 대 한 입력 중 하나는 명령줄입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="a5b60-104">이 항목에서는 매개 변수를 추가 하는 방법을 설명 합니다 **Get-proc** cmdlet (에 설명 되어 있는 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)) cmdlet 기반 명시적으로 로컬 컴퓨터에서 입력을 처리할 수 있도록 개체를 cmdlet에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="a5b60-105">합니다 **Get-proc** cmdlet 설명 여기 해당 이름을 기반으로 하는 프로세스를 검색 한 다음 명령 프롬프트에서 프로세스에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

<span data-ttu-id="a5b60-106">다음 섹션에서는이 항목은 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-106">The following sections are in this topic:</span></span>

- [<span data-ttu-id="a5b60-107">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="a5b60-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="a5b60-108">매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-108">Declaring Parameters</span></span>](#Declaring-Parameters)

- [<span data-ttu-id="a5b60-109">매개 변수 유효성 검사를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-109">Supporting Parameter Validation</span></span>](#Supporting-Parameter-Validation)

- [<span data-ttu-id="a5b60-110">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="a5b60-111">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="a5b60-111">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="a5b60-112">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="a5b60-112">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="a5b60-113">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="a5b60-113">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="a5b60-114">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a5b60-114">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="a5b60-115">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="a5b60-115">Defining the Cmdlet Class</span></span>

<span data-ttu-id="a5b60-116">Cmdlet 만드는 첫 번째 단계에는 cmdlet 및 cmdlet을 구현 하는.NET Framework 클래스의 선언을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-116">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="a5b60-117">"Get"입니다. 여기서 선택한 동사 이름 이므로이 cmdlet에 프로세스 정보 검색</span><span class="sxs-lookup"><span data-stu-id="a5b60-117">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="a5b60-118">(거의 모든 종류의 정보를 검색할 수 있는 cmdlet의 명령줄 입력을 처리할 수 있습니다.) 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-118">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="a5b60-119">에 대 한 클래스 선언을 다음은 **Get-proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a5b60-119">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="a5b60-120">이 정의 대 한 세부 정보에 제공 됩니다 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-120">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="a5b60-121">매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-121">Declaring Parameters</span></span>

<span data-ttu-id="a5b60-122">Cmdlet 매개 변수를 cmdlet에 대 한 입력을 제공 하도록 사용자를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-122">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="a5b60-123">다음 예에서 **Get-proc** 및 `Get-Member` 파이프라인된 cmdlet의 이름 및 `MemberType` 에 대 한 매개 변수는 `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a5b60-123">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="a5b60-124">매개 변수 속성이 인수 "."</span><span class="sxs-lookup"><span data-stu-id="a5b60-124">The parameter has the argument "property."</span></span>

<span data-ttu-id="a5b60-125">**PS > 가져오기-proc; `get-member` -membertype 속성**</span><span class="sxs-lookup"><span data-stu-id="a5b60-125">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="a5b60-126">Cmdlet의 매개 변수를 선언 하려면 먼저 매개 변수를 나타내는 속성을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-126">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="a5b60-127">에 **Get-proc** cmdlet을 유일한 매개 변수는 `Name`,이 경우 검색할.NET Framework 프로세스 개체의 이름을 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-127">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="a5b60-128">따라서 cmdlet 클래스 이름의 배열에 적용할 문자열 형식 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-128">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="a5b60-129">에 대 한 매개 변수 선언은 다음과 같습니다 합니다 `Name` 의 매개 변수를 **Get-proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a5b60-129">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="a5b60-130">이 속성은 Windows PowerShell 런타임에 알리기 위해 합니다 `Name` 매개 변수를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 속성 정의에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-130">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="a5b60-131">이 특성을 선언 하기 위한 기본 구문은 `[Parameter()]`합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-131">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="a5b60-132">매개 변수 해야 명시적으로 공용으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-132">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="a5b60-133">내부 공용 기본으로 표시 되지 않은 하는 Windows PowerShell 런타임에서 찾을 수 없는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-133">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="a5b60-134">이 cmdlet에 대 한 문자열의 배열을 사용 하 여 `Name` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-134">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="a5b60-135">가능한 경우 cmdlet도 정의 해야 매개 변수를 배열로 cmdlet이 둘 이상의 항목에 적용할 수 있도록이 때문에 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-135">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="a5b60-136">매개 변수 정의 기억해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="a5b60-136">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="a5b60-137">미리 정의 된 Windows PowerShell 매개 변수 이름과 데이터 형식은 cmdlet Windows PowerShell cmdlet을 사용 하 여 호환 되는지 확인 하려면 최대한 재사용 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-137">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="a5b60-138">예를 들어 미리 정의 된 모든 cmdlet을 사용 하는 경우 `Id` 매개 변수를 사용 하는 어떤 cmdlet에 관계 없이 의미를 이해 하는 매개 변수 이름 리소스에 사용자가 쉽게 식별할 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-138">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="a5b60-139">기본적으로 매개 변수 이름은 CLR (공용 언어 런타임)의 변수 이름에 사용 되는 동일한 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-139">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="a5b60-140">매개 변수 이름 지정에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수 이름은](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-140">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="a5b60-141">Windows PowerShell은 일관 된 사용자 환경을 제공 하기 위해 몇 가지 매개 변수 이름을 예약 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-141">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="a5b60-142">이러한 매개 변수 이름을 사용 하지 않는: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`를 `ErrorAction`, `ErrorVariable`를 `OutVariable`, 및 `OutBuffer`합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-142">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="a5b60-143">또한 이러한 매개 변수 이름에 대 한 다음 별칭은 예약 된: `vb`, `db`를 `ea`를 `ev`를 `ov`, 및 `ob`합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-143">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="a5b60-144">`Name` cmdlet에서 사용 하기 위해 권장 하는 간단 하 고 일반적인 매개 변수 이름이입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-144">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="a5b60-145">특정 cmdlet에 고유 하며 기억 하기 어려운 복잡 한 이름 대신 다음과 같은 매개 변수 이름을 선택 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-145">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="a5b60-146">매개 변수는 셸이 기본적으로 대/소문자를 유지 하지만 Windows PowerShell에서 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-146">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="a5b60-147">인수는 대/소문자 구분 cmdlet의 작업에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-147">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="a5b60-148">인수는 명령줄에서 지정 된 매개 변수에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-148">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="a5b60-149">다른 매개 변수 선언의 예를 참조 하세요 [Cmdlet 매개 변수](./cmdlet-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-149">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="a5b60-150">위치 또는 명명 된 매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-150">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="a5b60-151">Cmdlet을 설정 해야 각 매개 변수 중 하나로 위치 또는 명명 된 매개 변수를 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-151">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="a5b60-152">두 종류의 매개 변수 단일 인수를 부울 설정과 쉼표로 구분 된 여러 인수를 수락 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-152">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="a5b60-153">라고도 부울 매개 변수를 *전환*, 부울 설정을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-153">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="a5b60-154">스위치 매개 변수가 있는지 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-154">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="a5b60-155">권장 되는 기본값은 `false`합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-155">The recommended default is `false`.</span></span>

<span data-ttu-id="a5b60-156">샘플 **Get-proc** cmdlet을 정의 합니다 `Name` 위치 0 사용 하 여 위치 매개 변수로 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-156">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="a5b60-157">즉, 첫 번째 인수는 사용자가 명령줄에 입력이 매개 변수에 대해 자동으로 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-157">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="a5b60-158">명명 된 매개 변수를 정의 하려는 경우 사용자를 지정 해야 하는 명령줄에서 매개 변수 이름을 둡니다는 `Position` 특성 선언에서 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-158">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="a5b60-159">매개 변수 이름은, 없는 경우에 귀하에 게 가장 많이 사용 하는 매개 변수를 위치 사용자는 매개 변수 이름을 입력 하지 않아도 되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-159">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="a5b60-160">필수 또는 선택적으로 매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-160">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="a5b60-161">Cmdlet는 선택적인 또는 필수 매개 변수를 각 매개 변수를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-161">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="a5b60-162">예제의 **Get-proc** cmdlet을 합니다 `Name` 때문에 매개 변수가 선택 사항으로 정의 된는 `Mandatory` 특성 선언에서 키워드를 설정 하지.</span><span class="sxs-lookup"><span data-stu-id="a5b60-162">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="a5b60-163">매개 변수 유효성 검사를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-163">Supporting Parameter Validation</span></span>

<span data-ttu-id="a5b60-164">샘플 **Get-proc** 입력된 유효성 검사 특성을 추가 하는 cmdlet [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)를 `Name` 매개 변수 유효성 검사를 사용 하도록 설정 하는 입력이 모두 `null` 이거나 비어 있으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-164">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="a5b60-165">이 특성에는 Windows PowerShell에서 제공 하는 여러 유효성 검사 특성 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-165">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="a5b60-166">다른 유효성 검사 특성의 예제를 참조 하세요 [매개 변수 입력 유효성 검사](./validating-parameter-input.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-166">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="a5b60-167">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-167">Overriding an Input Processing Method</span></span>

<span data-ttu-id="a5b60-168">Cmdlet이 명령줄 입력을 처리 하려는 경우, 적절 한 입력 처리 메서드를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-168">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="a5b60-169">에 도입 된 기본 입력된 처리 메서드로 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-169">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="a5b60-170">**Get-proc** cmdlet 재정의 합니다 [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 처리 하는 메서드를 `Name` 사용자 또는 스크립트에서 제공 하는 매개 변수 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-170">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="a5b60-171">이 메서드는 제공 된 이름이 없는 경우 각 요청된 프로세스 이름 또는 프로세스에 대 한 모든 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-171">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="a5b60-172">있음을 [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)에 대 한 호출 [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 출력은 출력을 보내기 위한 메커니즘을 파이프라인에는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-172">Notice that in [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="a5b60-173">이 호출의 두 번째 매개 변수 `enumerateCollection`를 `true` 출력 배열을 프로세스 개체를 열거 하 고 명령줄에 한 번에 하나의 프로세스를 작성 하는 Windows PowerShell 런타임에 알리기 위해.</span><span class="sxs-lookup"><span data-stu-id="a5b60-173">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="a5b60-174">코드 예제</span><span class="sxs-lookup"><span data-stu-id="a5b60-174">Code Sample</span></span>

<span data-ttu-id="a5b60-175">전체 C# 코드 샘플을 참조 하십시오 [GetProcessSample02 샘플](./getprocesssample02-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-175">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="a5b60-176">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="a5b60-176">Defining Object Types and Formatting</span></span>

<span data-ttu-id="a5b60-177">.NET Framework 개체를 사용 하 여 cmdlet 간에 정보를 전달 하는 Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5b60-177">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="a5b60-178">따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-178">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="a5b60-179">새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-179">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="a5b60-180">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="a5b60-180">Building the Cmdlet</span></span>

<span data-ttu-id="a5b60-181">Cmdlet을 구현 하면 후 Windows PowerShell 스냅인을 사용 하 여 Windows PowerShell을 사용 하 여 등록 해야 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-181">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="a5b60-182">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-182">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="a5b60-183">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a5b60-183">Testing the Cmdlet</span></span>

<span data-ttu-id="a5b60-184">Cmdlet은 Windows PowerShell을 사용 하 여 등록 되 면 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-184">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="a5b60-185">샘플 cmdlet에 대 한 코드를 테스트 하려면 두 가지 방법으로 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-185">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="a5b60-186">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-186">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="a5b60-187">Windows PowerShell 프롬프트에서 "IEXPLORE." 라고 하는 Internet Explorer 프로세스를 나열 하려면 다음 명령을 사용합니다</span><span class="sxs-lookup"><span data-stu-id="a5b60-187">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="a5b60-188">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-188">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="a5b60-189">"OUTLOOK" 및 "NOTEPAD,"는 "IEXPLORE" 라는 Internet Explorer, Outlook 및 메모장 프로세스를 나열 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-189">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="a5b60-190">여러 프로세스의 경우 모두 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-190">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="a5b60-191">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5b60-191">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="a5b60-192">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5b60-192">See Also</span></span>

[<span data-ttu-id="a5b60-193">프로세스 파이프라인 입력 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="a5b60-193">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="a5b60-194">첫 번째 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="a5b60-194">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="a5b60-195">확장 개체 형식 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="a5b60-195">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="a5b60-196">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="a5b60-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="a5b60-197">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="a5b60-197">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="a5b60-198">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="a5b60-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)
