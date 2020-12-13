---
ms.date: 09/13/2016
ms.topic: reference
title: 인수 개수를 확인하는 방법
description: 인수 개수를 확인하는 방법
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666946"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="32f95-103">인수 개수를 확인하는 방법</span><span class="sxs-lookup"><span data-stu-id="32f95-103">How to Validate an Argument Count</span></span>

<span data-ttu-id="32f95-104">이 예제에서는 Windows PowerShell 런타임에서 cmdlet이 실행 되기 전에 매개 변수가 허용 하는 인수 개수 (개수)를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="32f95-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="32f95-105">이 유효성 검사 규칙은 ValidateCount 특성을 선언 하 여 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="32f95-105">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="32f95-106">이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="32f95-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="32f95-107">인수 개수를 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="32f95-107">To validate an argument count</span></span>

- <span data-ttu-id="32f95-108">다음 코드와 같이 Validate 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="32f95-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="32f95-109">이 예에서는 매개 변수에서 인수를 하나 또는 3 개까지 허용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="32f95-109">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

<span data-ttu-id="32f95-110">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [Validatecount 특성 선언](./validatecount-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="32f95-110">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32f95-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32f95-111">See Also</span></span>

[<span data-ttu-id="32f95-112">ValidateCount 특성 선언</span><span class="sxs-lookup"><span data-stu-id="32f95-112">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

<span data-ttu-id="32f95-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="32f95-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
