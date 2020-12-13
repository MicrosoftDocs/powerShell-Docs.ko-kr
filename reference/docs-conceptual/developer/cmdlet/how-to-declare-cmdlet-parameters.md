---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 매개 변수를 선언하는 방법
description: Cmdlet 매개 변수를 선언하는 방법
ms.openlocfilehash: ed53f9788c9afb142b137e08966dff33551b9d0f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667099"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="8f7dd-103">Cmdlet 매개 변수를 선언하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f7dd-103">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="8f7dd-104">이러한 예제에서는 명명 된, 위치, 필수, 선택적 및 스위치 매개 변수를 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-104">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="8f7dd-105">또한이 예제에서는 매개 변수 별칭을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-105">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="8f7dd-106">명명 된 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f7dd-106">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="8f7dd-107">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-107">Define a public property as shown in the following code.</span></span> <span data-ttu-id="8f7dd-108">매개 변수 특성을 추가 하는 경우 `Position` 특성에서 키워드를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-108">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="8f7dd-109">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-109">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="8f7dd-110">위치 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f7dd-110">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="8f7dd-111">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-111">Define a public property as shown in the following code.</span></span> <span data-ttu-id="8f7dd-112">매개 변수 특성을 추가 하는 경우 `Position` 키워드를 인수 위치로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-112">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="8f7dd-113">값 0은 첫 번째 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-113">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="8f7dd-114">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-114">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="8f7dd-115">필수 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f7dd-115">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="8f7dd-116">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-116">Define a public property as shown in the following code.</span></span> <span data-ttu-id="8f7dd-117">매개 변수 특성을 추가 하는 경우 `Mandatory` 키워드를로 설정 `true` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-117">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="8f7dd-118">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-118">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="8f7dd-119">선택적 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f7dd-119">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="8f7dd-120">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-120">Define a public property as shown in the following code.</span></span> <span data-ttu-id="8f7dd-121">매개 변수 특성을 추가 하는 경우 키워드를 생략 `Mandatory` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-121">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="8f7dd-122">스위치 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f7dd-122">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="8f7dd-123">공용 속성을 형식 [System.webserver 매개 변수로](/dotnet/api/System.Management.Automation.SwitchParameter)정의한 다음 매개 변수 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-123">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="8f7dd-124">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-124">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="8f7dd-125">별칭을 사용 하 여 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f7dd-125">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="8f7dd-126">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-126">Define a public property as shown in the following code.</span></span> <span data-ttu-id="8f7dd-127">매개 변수에 대 한 별칭을 나열 하는 별칭 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-127">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="8f7dd-128">이 예에서는 동일한 매개 변수에 대해 3 개의 별칭을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-128">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="8f7dd-129">첫 번째 별칭은 바로 가기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-129">The first alias provides a shortcut.</span></span> <span data-ttu-id="8f7dd-130">두 번째와 세 번째 별칭은 다양 한 시나리오에 사용할 수 있는 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-130">The second and third aliases provide names you can use for different scenarios.</span></span>

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="8f7dd-131">Alias 특성에 대 한 자세한 내용은 [Alias 특성 선언](./alias-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f7dd-131">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f7dd-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f7dd-132">See Also</span></span>

[<span data-ttu-id="8f7dd-133">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="8f7dd-133">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="8f7dd-134">Parameter 특성 선언</span><span class="sxs-lookup"><span data-stu-id="8f7dd-134">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="8f7dd-135">Alias 특성 선언</span><span class="sxs-lookup"><span data-stu-id="8f7dd-135">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

<span data-ttu-id="8f7dd-136">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="8f7dd-136">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
