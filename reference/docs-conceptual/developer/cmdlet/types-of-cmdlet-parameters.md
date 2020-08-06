---
title: Cmdlet 매개 변수의 유형 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e704aae6e23568be9935e228752f652929863a98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786376"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="1e3f5-102">Cmdlet 매개 변수 형식</span><span class="sxs-lookup"><span data-stu-id="1e3f5-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="1e3f5-103">이 항목에서는 cmdlet에서 선언할 수 있는 여러 가지 형식의 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="1e3f5-104">Cmdlet 매개 변수는 위치, 명명 됨, 필수, 선택적 또는 스위치 매개 변수가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="1e3f5-105">위치 및 명명 된 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1e3f5-105">Positional and Named Parameters</span></span>

<span data-ttu-id="1e3f5-106">모든 cmdlet 매개 변수는 명명 된 매개 변수 또는 위치 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="1e3f5-107">명명 된 매개 변수를 사용 하려면 cmdlet을 호출할 때 매개 변수 이름과 인수를 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="1e3f5-108">위치 매개 변수는 상대 순서로 인수를 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="1e3f5-109">그런 다음 첫 번째 명명 되지 않은 인수를 첫 번째 위치 매개 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="1e3f5-110">시스템은 두 번째 명명 되지 않은 인수를 두 번째 명명 되지 않은 매개 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="1e3f5-111">기본적으로 모든 cmdlet 매개 변수는 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="1e3f5-112">명명 된 매개 변수를 정의 하려면 `Position` 다음 매개 변수 선언에 표시 된 것 처럼 **매개 변수** 특성 선언에서 키워드를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="1e3f5-113">위치 매개 변수를 정의 하려면 `Position` 매개 변수 특성 선언에 키워드를 추가 하 고 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="1e3f5-114">다음 샘플에서 `UserName` 매개 변수는 위치가 0 인 위치 매개 변수로 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="1e3f5-115">즉, 호출의 첫 번째 인수는이 매개 변수에 자동으로 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="1e3f5-116">Cmdlet이 실행 될 때 사용자가 매개 변수 이름을 입력 하지 않아도 되도록 가장 많이 사용 되는 매개 변수를 위치 매개 변수로 선언 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="1e3f5-117">위치 및 명명 된 매개 변수는 단일 인수 또는 쉼표로 구분 된 여러 인수를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="1e3f5-118">매개 변수가 문자열 배열과 같은 컬렉션을 허용 하는 경우에만 여러 인수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="1e3f5-119">동일한 cmdlet에서 위치 및 명명 된 매개 변수를 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="1e3f5-120">이 경우 시스템은 명명 된 인수를 먼저 검색 한 다음 나머지 명명 되지 않은 인수를 위치 매개 변수에 매핑하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="1e3f5-121">다음 명령은 cmdlet의 매개 변수에 대 한 단일 인수와 여러 인수를 지정할 수 있는 여러 가지 방법을 보여 줍니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="1e3f5-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="1e3f5-122">마지막 두 샘플에서 매개 변수가 위치 매개 변수로 정의 되었으므로 **-name** 을 지정할 필요가 없습니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="1e3f5-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="1e3f5-123">필수 및 선택적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1e3f5-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="1e3f5-124">Cmdlet 매개 변수를 필수 또는 선택적 매개 변수로 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="1e3f5-125">Windows PowerShell 런타임이 cmdlet을 호출 하기 전에 필수 매개 변수를 지정 해야 합니다.  기본적으로 매개 변수는 선택 사항으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="1e3f5-126">필수 매개 변수를 정의 하려면 `Mandatory` 다음 매개 변수 선언에 표시 된 것 처럼 매개 변수 특성 선언에 키워드를 추가 하 고로 설정 `true` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="1e3f5-127">선택적 매개 변수를 정의 하려면 `Mandatory` 다음 매개 변수 선언에 표시 된 것 처럼 **매개 변수** 특성 선언에서 키워드를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="1e3f5-128">스위치 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1e3f5-128">Switch Parameters</span></span>

<span data-ttu-id="1e3f5-129">Windows PowerShell은 cmdlet [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 을 `false` 호출할 때 매개 변수가 지정 되지 않은 경우 값이 자동으로로 설정 되는 매개 변수를 정의할 수 있도록 하는 system.object를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="1e3f5-130">가능 하면 부울 매개 변수 대신 스위치 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="1e3f5-131">다음 샘플을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-131">Consider the following sample.</span></span> <span data-ttu-id="1e3f5-132">기본적으로 여러 Windows PowerShell cmdlet은 출력 개체를 파이프라인 아래로 전달 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="1e3f5-133">그러나 이러한 cmdlet에는 `PassThru` 기본 동작을 재정의 하는 스위치 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="1e3f5-134">`PassThru`이러한 cmdlet을 호출할 때 매개 변수가 지정 된 경우 cmdlet은 출력 개체를 파이프라인에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="1e3f5-135">호출에 매개 변수를 지정 하지 않은 경우 매개 변수의 기본값을 포함 해야 하는 경우 `true` 매개 변수의 의미를 반대로 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="1e3f5-136">샘플의 경우 매개 변수 특성을 부울 값으로 설정 하는 대신 `true` 속성을 [system.object](/dotnet/api/System.Management.Automation.SwitchParameter) 로 선언한 다음 매개 변수의 기본값을로 설정 `false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="1e3f5-137">스위치 매개 변수를 정의 하려면 다음 샘플과 같이 속성을 [System.object 매개 변수](/dotnet/api/System.Management.Automation.SwitchParameter) 형식으로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="1e3f5-138">매개 변수가 지정 될 때 매개 변수를 사용 하도록 하려면 입력 처리 메서드 중 하나에서 다음 구조체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3f5-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="1e3f5-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e3f5-139">See Also</span></span>

[<span data-ttu-id="1e3f5-140">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="1e3f5-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
