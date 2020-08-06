---
title: 인수 범위의 유효성을 검사 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange attribute, example
ms.openlocfilehash: b48b1b87425add51e855c48ec700c78c3ae296c1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782075"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="377ef-102">인수 범위를 확인하는 방법</span><span class="sxs-lookup"><span data-stu-id="377ef-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="377ef-103">이 예제에서는 cmdlet이 실행 되기 전에 Windows PowerShell 런타임에서 매개 변수 인수의 최소값과 최대값을 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="377ef-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="377ef-104">ValidateRange 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="377ef-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="377ef-105">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="377ef-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="377ef-106">인수 범위의 유효성을 검사 하려면</span><span class="sxs-lookup"><span data-stu-id="377ef-106">To validate an argument range</span></span>

- <span data-ttu-id="377ef-107">다음 코드와 같이 ValidateRange 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="377ef-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="377ef-108">이 예에서는 매개 변수에 대해 0에서 5 사이의 범위를 지정 합니다 `InputData` .</span><span class="sxs-lookup"><span data-stu-id="377ef-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="377ef-109">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [ValidateRange Attribute 선언](./validaterange-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="377ef-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="377ef-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="377ef-110">See Also</span></span>

[<span data-ttu-id="377ef-111">ValidateRange 특성 선언</span><span class="sxs-lookup"><span data-stu-id="377ef-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="377ef-112">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="377ef-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
