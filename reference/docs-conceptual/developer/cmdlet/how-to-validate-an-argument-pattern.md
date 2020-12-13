---
ms.date: 09/13/2016
ms.topic: reference
title: 인수 패턴 유효성을 검사하는 방법
description: 인수 패턴 유효성을 검사하는 방법
ms.openlocfilehash: ab5777c918a53c0a3900f87c52e7f14f9cb9b726
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666912"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="0a7ee-103">인수 패턴 유효성을 검사하는 방법</span><span class="sxs-lookup"><span data-stu-id="0a7ee-103">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="0a7ee-104">이 예제에서는 cmdlet이 실행 되기 전에 Windows PowerShell 런타임에서 매개 변수 인수의 문자 패턴을 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a7ee-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="0a7ee-105">ValidatePattern 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a7ee-105">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="0a7ee-106">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0a7ee-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="0a7ee-107">인수 패턴의 유효성을 검사 하려면</span><span class="sxs-lookup"><span data-stu-id="0a7ee-107">To validate an argument pattern</span></span>

- <span data-ttu-id="0a7ee-108">다음 코드와 같이 Validate 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a7ee-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="0a7ee-109">이 예에서는 네 자리의 패턴을 지정 합니다. 여기서 각 숫자의 값은 0에서 9 까지입니다.</span><span class="sxs-lookup"><span data-stu-id="0a7ee-109">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="0a7ee-110">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [ValidatePattern Attribute 선언](./validatepattern-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0a7ee-110">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0a7ee-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a7ee-111">See Also</span></span>

[<span data-ttu-id="0a7ee-112">ValidatePattern 특성 선언</span><span class="sxs-lookup"><span data-stu-id="0a7ee-112">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

<span data-ttu-id="0a7ee-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="0a7ee-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
