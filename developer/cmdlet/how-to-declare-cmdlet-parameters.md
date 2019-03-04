---
title: Cmdlet 매개 변수를 선언 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: d6613889ebd2ba139ce0b3de1b8d24e4aec37d2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861399"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="0e1b1-102">Cmdlet 매개 변수를 선언하는 방법</span><span class="sxs-lookup"><span data-stu-id="0e1b1-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="0e1b1-103">이러한 예제에는 명명 된, 위치, 필수 (선택 사항)를 선언 하 고 매개 변수를 전환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="0e1b1-104">이러한 예제에는 매개 변수 별칭을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="0e1b1-105">명명된 된 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0e1b1-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="0e1b1-106">다음 코드에 표시 된 대로 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0e1b1-107">매개 변수 특성을 추가한 경우 생략 된 `Position` 특성에서 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="0e1b1-108">매개 변수 특성에 대 한 자세한 내용은 참조 하세요. [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="0e1b1-109">위치 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0e1b1-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="0e1b1-110">다음 코드에 표시 된 대로 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0e1b1-111">매개 변수 특성을 추가할 때 설정는 `Position` 키워드 인수 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="0e1b1-112">값 0은 첫 번째 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="0e1b1-113">매개 변수 특성에 대 한 자세한 내용은 참조 하세요. [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="0e1b1-114">필수 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0e1b1-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="0e1b1-115">다음 코드에 표시 된 대로 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0e1b1-116">매개 변수 특성을 추가할 때 설정 된 `Mandatory` 키워드를 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="0e1b1-117">매개 변수 특성에 대 한 자세한 내용은 참조 하세요. [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="0e1b1-118">선택적 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0e1b1-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="0e1b1-119">다음 코드에 표시 된 대로 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0e1b1-120">매개 변수 특성을 추가한 경우 생략 된 `Mandatory` 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="0e1b1-121">스위치 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0e1b1-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="0e1b1-122">형식으로 공용 속성을 정의 [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)과 다음 매개 변수 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-122">Define a public property as type [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="0e1b1-123">매개 변수 특성에 대 한 자세한 내용은 참조 하세요. [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="0e1b1-124">별칭을 사용 하 여 매개 변수를 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0e1b1-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="0e1b1-125">다음 코드에 표시 된 대로 공용 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0e1b1-126">매개 변수의 별칭을 나열 하는 별칭 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="0e1b1-127">이 예제에서는 세 가지 별칭은 동일한 매개 변수에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="0e1b1-128">첫 번째 별칭에는 바로 가기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="0e1b1-129">두 번째 및 세 번째 별칭에는 다양 한 시나리오에 사용할 수 있는 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="0e1b1-130">Alias 특성에 대 한 자세한 내용은 참조 하세요. [별칭 특성 선언은](./alias-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1b1-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0e1b1-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e1b1-131">See Also</span></span>

[<span data-ttu-id="0e1b1-132">System.Management.Automation.Switchparameter</span><span class="sxs-lookup"><span data-stu-id="0e1b1-132">System.Management.Automation.Switchparameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="0e1b1-133">매개 변수 특성 선언</span><span class="sxs-lookup"><span data-stu-id="0e1b1-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="0e1b1-134">별칭 특성 선언</span><span class="sxs-lookup"><span data-stu-id="0e1b1-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

<span data-ttu-id="0e1b1-135">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="0e1b1-135">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
