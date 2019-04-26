---
title: Cmdlet 매개 변수 유형의 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067198"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="ec93f-102">Cmdlet 매개 변수 형식</span><span class="sxs-lookup"><span data-stu-id="ec93f-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="ec93f-103">이 항목에서는 다양 한 cmdlet에서 선언할 수 있는 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="ec93f-104">Cmdlet 매개 변수 스위치 매개 변수 또는 위치, 명명 된, 필수 (선택 사항)을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="ec93f-105">위치 인수와 명명 된 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ec93f-105">Positional and Named Parameters</span></span>

<span data-ttu-id="ec93f-106">모든 cmdlet 매개 변수는 이름이 나 위치 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="ec93f-107">명명된 된 매개 변수는 cmdlet을 호출 하는 경우 매개 변수 이름 및 인수를 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="ec93f-108">위치 매개 변수는 상대 순서로 인수를 입력할만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="ec93f-109">그런 다음 시스템은 첫 번째 위치 매개 변수를 명명 되지 않은 첫 번째 인수를 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="ec93f-110">시스템은 두 번째 명명 되지 않은 두 번째 인수를 매핑합니다 명명 되지 않은 매개 변수를 등에입니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="ec93f-111">기본적으로 모든 cmdlet 매개 변수는 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="ec93f-112">명명된 된 매개 변수를 정의 하려면 생략 합니다 `Position` 키워드를 **매개 변수** 특성 선언에 다음 매개 변수 선언에 표시 된 대로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="ec93f-113">위치 매개 변수를 정의 하려면 추가 `Position` 매개 변수에 키워드 특성 선언 하 고 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="ec93f-114">다음 샘플에서는 `UserName` 매개 변수가 0의 위치를 사용 하 여 위치 매개 변수로 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="ec93f-115">즉, 호출의 첫 번째 인수는이 매개 변수를 자동으로 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

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
> <span data-ttu-id="ec93f-116">좋은 cmdlet 설계 위치 매개 변수로 사용자는 cmdlet를 실행할 때 매개 변수 이름을 입력 하지 않아도 되도록 가장 많이 사용 되는 매개 변수를 선언 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="ec93f-117">위치 인수와 명명 된 매개 변수는 단일 인수 또는 쉼표로 구분 된 여러 인수를 수락 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="ec93f-118">여러 인수는 매개 변수가 문자열 배열과 같은 컬렉션을 허용 하는 경우에 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="ec93f-119">동일한 cmdlet에서 위치 인수와 명명 된 매개 변수를 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="ec93f-120">시스템 명명 된 인수를 먼저 검색 하 고에 나머지 매핑하려고 명명 되지 않은 인수가 위치 매개 변수를이 예제의 경우.</span><span class="sxs-lookup"><span data-stu-id="ec93f-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="ec93f-121">다음 명령은 단일 및 여러 인수 매개 변수를 지정할 수 있는 다양 한 방법을 표시 합니다 `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ec93f-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="ec93f-122">마지막 두 샘플에서 있음을 **-이름** 때문에 지정할 필요가 없습니다를 `Name` 매개 변수를 위치 매개 변수로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="ec93f-123">필수 및 선택적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ec93f-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="ec93f-124">또한 필수 또는 선택적 매개 변수로 cmdlet 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="ec93f-125">(필수 매개 변수는 Windows PowerShell 런타임에 cmdlet을 호출 하기 전에 지정 되어야 합니다.)  기본적으로 매개 변수를 선택적으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="ec93f-126">필수 매개 변수를 정의 하려면 다음을 추가 합니다 `Mandatory` 특성 선언 하 고 설정 하는 매개 변수에 키워드 `true`다음 매개 변수 선언에 나와 있는 것 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="ec93f-127">선택적 매개 변수를 정의 하려면 생략 합니다 `Mandatory` 키워드를 **매개 변수** 특성 선언에 다음 매개 변수 선언에 표시 된 대로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="ec93f-128">스위치 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ec93f-128">Switch Parameters</span></span>

<span data-ttu-id="ec93f-129">Windows PowerShell은 제공 된 [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 값을 갖는 매개 변수를 정의할 수 있는 형식으로 자동 설정 됩니다 `false` 경우 cmdlet 매개 변수를 지정 하지 않으면 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="ec93f-130">가능 하면 부울 매개 변수 대신 스위치 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="ec93f-131">다음 샘플을 고려해보세요.</span><span class="sxs-lookup"><span data-stu-id="ec93f-131">Consider the following sample.</span></span> <span data-ttu-id="ec93f-132">기본적으로 몇 가지 Windows PowerShell cmdlet에 출력 개체를 파이프라인으로 전달 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="ec93f-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="ec93f-133">그러나 이러한 cmdlet에는 `PassThru` 기본 동작을 재정의 하는 매개 변수를 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="ec93f-134">경우는 `PassThru` 파이프라인에 출력 개체를 반환 하는 cmdlet, 이러한 cmdlet이 호출 될 때 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="ec93f-135">매개 변수가 기본 값을 가질 경우 `true` 호출에서 매개 변수를 지정 하지 않으면, 매개 변수의 의미를 반전 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="ec93f-136">샘플의 경우, 매개 변수 속성의 부울 값으로 설정 하는 대신 `true`를 속성으로 선언 된 [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 형식과 매개변수의기본값을설정합니다`false`.</span><span class="sxs-lookup"><span data-stu-id="ec93f-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="ec93f-137">스위치 매개 변수를 정의 하려면 속성으로 선언 된 [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 다음 샘플에 표시 된 것과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="ec93f-138">지정 된 경우에 매개 변수를 작업할 cmdlet 입력 처리 메서드 중 하나에서 다음 구조를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec93f-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec93f-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec93f-139">See Also</span></span>

<span data-ttu-id="ec93f-140">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="ec93f-140">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
