---
title: Cmdlet 매개 변수를 선언 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 97e86a1eb715f149a8383a1a4529c00da4f0eba8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774391"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="64561-102">Cmdlet 매개 변수를 선언하는 방법</span><span class="sxs-lookup"><span data-stu-id="64561-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="64561-103">이러한 예제에서는 명명 된, 위치, 필수, 선택적 및 스위치 매개 변수를 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="64561-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="64561-104">또한이 예제에서는 매개 변수 별칭을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="64561-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="64561-105">명명 된 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="64561-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="64561-106">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="64561-107">매개 변수 특성을 추가 하는 경우 `Position` 특성에서 키워드를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="64561-108">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64561-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="64561-109">위치 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="64561-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="64561-110">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="64561-111">매개 변수 특성을 추가 하는 경우 `Position` 키워드를 인수 위치로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="64561-112">값 0은 첫 번째 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="64561-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="64561-113">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64561-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="64561-114">필수 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="64561-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="64561-115">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="64561-116">매개 변수 특성을 추가 하는 경우 `Mandatory` 키워드를로 설정 `true` 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="64561-117">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64561-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="64561-118">선택적 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="64561-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="64561-119">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="64561-120">매개 변수 특성을 추가 하는 경우 키워드를 생략 `Mandatory` 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="64561-121">스위치 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="64561-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="64561-122">공용 속성을 형식 [System.webserver 매개 변수로](/dotnet/api/System.Management.Automation.SwitchParameter)정의한 다음 매개 변수 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="64561-123">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64561-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="64561-124">별칭을 사용 하 여 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="64561-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="64561-125">다음 코드와 같이 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="64561-126">매개 변수에 대 한 별칭을 나열 하는 별칭 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="64561-127">이 예에서는 동일한 매개 변수에 대해 3 개의 별칭을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="64561-128">첫 번째 별칭은 바로 가기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="64561-129">두 번째와 세 번째 별칭은 다양 한 시나리오에 사용할 수 있는 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="64561-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="64561-130">Alias 특성에 대 한 자세한 내용은 [Alias 특성 선언](./alias-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64561-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64561-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64561-131">See Also</span></span>

[<span data-ttu-id="64561-132">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="64561-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="64561-133">Parameter 특성 선언</span><span class="sxs-lookup"><span data-stu-id="64561-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="64561-134">Alias 특성 선언</span><span class="sxs-lookup"><span data-stu-id="64561-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="64561-135">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="64561-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
